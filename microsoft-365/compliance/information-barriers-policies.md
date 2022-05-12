---
title: Bilgi engellerini kullanmaya başlama
description: Microsoft Purview'da bilgi engellerini kullanmaya başlamayı öğrenin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, bilgi engelleri
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ef2c8c5c4dfdbb1598c8f6edc5344da9351b6ad7
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363302"
---
# <a name="get-started-with-information-barriers"></a>Bilgi engellerini kullanmaya başlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, kuruluşunuzda bilgi engeli (IB) ilkelerinin nasıl yapılandırıldığı açıklanır. Birkaç adım söz konusu olduğundan, IB ilkelerini yapılandırmaya başlamadan önce sürecin tamamını gözden geçirmeyi unutmayın.

IB ilkelerini tanımlamak, doğrulamak veya düzenlemek için [PowerShell cmdlet'lerini](/powershell/exchange/scc-powershell) biliyor olmanız gerekir. Bu makalede Çeşitli PowerShell cmdlet'leri örnekleri sağlasak da, kuruluşunuz için diğer ayrıntıları (parametre değerleri gibi) bilmeniz gerekir.

IB senaryoları ve özellikleri hakkında daha fazla bilgi için bkz. [Bilgi engelleri hakkında bilgi edinin](information-barriers.md).

> [!TIP]
> Planınızı hazırlamanıza yardımcı olmak için bu makalede [örnek bir senaryo](#example-scenario-contosos-departments-segments-and-policies) yer alır.

## <a name="required-subscriptions-and-permissions"></a>Gerekli abonelikler ve izinler

IB'yi kullanmaya başlamadan önce Microsoft 365 aboneliğinizi ve tüm eklentileri onaylamanız gerekir. IB'ye erişmek ve bunları kullanmak için kuruluşunuzun aşağıdaki aboneliklerden veya eklentilerden birine sahip olması gerekir:

- Microsoft 365 E5/A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 E5/A5/A3/A1 aboneliği (ücretli veya deneme sürümü)
- Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz)
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Insider Risk Management eklentisi

Daha fazla bilgi için bkz[. güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

[IB ilkelerini yönetmek](information-barriers-policies.md) için aşağıdaki rollerden birine atanmış olmanız gerekir:

- Genel yönetici Microsoft 365
- Genel yönetici Office 365
- Uyumluluk yöneticisi
- IB Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için bkz. [Office 365 Güvenlik & Uyumluluk Merkezi'ndeki İzinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="configuration-concepts"></a>Yapılandırma kavramları

IB için ilkeler tanımladığınızda, çeşitli nesneler ve kavramlarla çalışacaksınız.

- **Kullanıcı hesabı öznitelikleri** Azure Active Directory (veya Exchange Online) içinde tanımlanır. Bu öznitelikler departman, iş unvanı, konum, ekip adı ve diğer iş profili ayrıntılarını içerebilir.
- **Segmentler**, seçilen **kullanıcı hesabı özniteliği kullanılarak Microsoft Purview uyumluluk portalı tanımlanan kullanıcı kümeleridir**. Ayrıntılar için [IB tarafından desteklenen özniteliklerin](information-barriers-attributes.md) listesine bakın.
- **IB olmayan kullanıcıların ve grupların görünürlüğü**. IB dışı kullanıcılar ve gruplar, IB segmentlerinin ve ilkelerinin dışında tutulan kullanıcılar ve gruplardır. IB ilkelerinin türüne bağlı olarak (engelle veya izin ver), bu kullanıcıların ve grubun davranışı Microsoft Teams, SharePoint, OneDrive ve genel adres listenizde farklılık gösterir. *İzin verme* ilkelerinde tanımlanan kullanıcılar için, IB dışı gruplar ve kullanıcılar IB segmentlerine ve ilkelerine dahil olan kullanıcılara görünmez. *Blok* ilkelerinde tanımlanan kullanıcılar için, IB dışı gruplar ve kullanıcılar IB segmentlerine ve ilkelerine dahil olan kullanıcılar tarafından görülebilir.
- **Grup desteği**. Şu anda IB'de yalnızca Modern Gruplar desteklenmektedir ve Dağıtım Listeleri/Güvenlik Grupları IB dışı gruplar olarak değerlendirilir.
- **Gizli/devre dışı bırakılmış kullanıcı hesapları**. Kuruluşunuzdaki gizli/devre dışı bırakılmış hesaplar için, kullanıcı hesapları gizlendiğinde veya devre dışı bırakıldığında *HiddenFromAddressListEnabled* parametresi otomatik olarak *True* olarak ayarlanır. IB özellikli kuruluşlarda bu hesapların diğer tüm kullanıcı hesaplarıyla iletişim kurması engellenir. Microsoft Teams'de, bu hesaplar dahil tüm sohbetler kilitlenir veya kullanıcılar konuşmalardan otomatik olarak kaldırılır.
- **IB ilkeleri** , iletişim sınırlarını veya kısıtlamalarını belirler. Bilgi engeli ilkeleri tanımladığınızda, iki tür ilke arasından seçim yapabilirsiniz:
  - *İlkeleri engelleme* , bir kesimin başka bir kesimle iletişim kurmasını engeller.
  - *İlkelere izin ver* , bir segmentin yalnızca belirli diğer segmentlerle iletişim kurmasına izin verir.

    > [!NOTE]
    > **İzin verme** ilkeleri için, IB dışı gruplar ve kullanıcılar IB segmentlerine ve ilkelerine dahil edilen kullanıcılara görünmez. IB dışı grupların ve kullanıcıların IB segmentlerine ve ilkelerine dahil edilen kullanıcılara görünür olması gerekiyorsa **, engelleme** ilkelerini kullanmanız gerekir.

- *İlke uygulaması* tüm IB ilkeleri tanımlandıktan sonra yapılır ve bunları kuruluşunuzda uygulamaya hazır olursunuz.

## <a name="configuration-at-a-glance"></a>Bir bakışta yapılandırma

| **Adımlar** | **Nelerin dahil olduğu** |
|:------|:----------------|
| **1. Adım**: [Önkoşulların karşılandığından emin olun](#step-1-make-sure-prerequisites-are-met) | - Gerekli aboneliklere ve izinlere sahip olduğunuzu doğrulayın <br/>- Dizininizin kullanıcıları segmentlere ayırmaya yönelik veriler içerdiğini doğrulayın<br/>- [Microsoft Teams için ada göre aramayı](/microsoftteams/teams-scoped-directory-search) etkinleştirme<br/>- Denetim günlüğünün açık olduğundan emin olun<br/>- Exchange adres defteri ilkelerinin uygulanmadığından emin olun<br/>- PowerShell kullanma (örnekler sağlanır)<br/>- Microsoft Teams için yönetici onayı sağlayın (adımlar dahildir) |
| **2. Adım**: [Kuruluşunuzdaki kullanıcıları segmentlere ayırma](#step-2-segment-users-in-your-organization) | - Hangi ilkelerin gerekli olduğunu belirleme<br/>- Tanımlayacak segmentlerin listesini oluşturma<br/>- Hangi özniteliklerin kullanılacağını belirleme<br/>- İlke filtreleri açısından segmentleri tanımlama |
| **3. Adım**: [Bilgi engeli ilkelerini tanımlama](#step-3-define-information-barrier-policies) | - İlkelerinizi tanımlayın (henüz geçerli değildir)<br/>- İki tür arasından seçim yapın (engelle veya izin ver) |
| **4. Adım**: [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies) | - İlkeleri etkin duruma ayarlama<br/>- İlke uygulamasını çalıştırma<br/>- İlke durumunu görüntüleme |
| **5. Adım**: [SharePoint ve OneDrive ile ilgili bilgi engelleri için yapılandırma (isteğe bağlı)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - IB'yi SharePoint ve OneDrive için yapılandırma |
| **6. Adım**: [Bilgi engelleri modları (isteğe bağlı)](#step-6-information-barriers-modes) | - Varsa IB modlarını güncelleştirme |

## <a name="step-1-make-sure-prerequisites-are-met"></a>1. Adım: Önkoşulların karşılandığından emin olun

Gerekli aboneliklere ve izinlere ek olarak, IB'yi yapılandırmadan önce aşağıdaki gereksinimlerin karşılandığından emin olun:

- **Dizin verileri**: Kuruluşunuzun yapısının dizin verilerine yansıtıldığından emin olun. Bu eylemi gerçekleştirmek için kullanıcı hesabı özniteliklerinin (grup üyeliği, departman adı vb.) Azure Active Directory (veya Exchange Online) içinde doğru dolduruldığından emin olun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
  - [Bilgi engeli ilkeleri öznitelikleri](information-barriers-attributes.md)
  - [Azure Active Directory kullanarak kullanıcının profil bilgilerini ekleme veya güncelleştirme](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Office 365 PowerShell ile kullanıcı hesabı özelliklerini yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Kapsamlı dizin araması**: Kuruluşunuzun ilk IB ilkesini tanımlamadan önce, [Microsoft Teams'de kapsamlı dizin aramasını etkinleştirmeniz](/MicrosoftTeams/teams-scoped-directory-search) gerekir. IB ilkelerini ayarlamadan veya tanımlamadan önce kapsamlı dizin aramasını etkinleştirdikten sonra en az 24 saat bekleyin.

- **Denetim günlüğünün etkin olduğunu doğrulayın**: IB ilke uygulamasının durumunu aramak için denetim günlüğünün açık olması gerekir. Denetim, Microsoft 365 kuruluşlar için varsayılan olarak etkindir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmış olabilir. Kuruluşunuzda denetim devre dışı bırakıldıysa, bunun nedeni başka bir yöneticinin kapatması olabilir. Bu adımı tamamlarken denetimi yeniden açmanın uygun olduğunu onaylamanızı öneririz. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md).

- **Mevcut Exchange Online adres defteri ilkelerini kaldırma**: IB ilkelerini tanımlayıp uygulamadan önce, kuruluşunuzdaki tüm Exchange Online adres defteri ilkelerini kaldırmanız gerekir. IB ilkeleri adres defteri ilkelerini temel alır ve mevcut ABP ilkeleri IB tarafından oluşturulan ABP'lerle uyumlu değildir. Mevcut adres defteri ilkelerinizi kaldırmak için bkz. [Exchange Online'da adres defteri ilkesini kaldırma](/exchange/address-books/address-book-policies/remove-an-address-book-policy). IB ilkeleri ve Exchange Online hakkında daha fazla bilgi için bkz. [Bilgi engelleri ve Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **PowerShell kullanarak yönetme**: Şu anda IB ilkeleri Güvenlik & Uyumluluk Merkezi PowerShell'de tanımlanmış ve yönetilmektedir. Bu makalede çeşitli örnekler sağlansa da PowerShell cmdlet'leri ve parametreleri hakkında bilgi sahibi olmanız gerekir. Azure Active Directory PowerShell modülüne de ihtiyacınız olacaktır.
  - [Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell)
  - [Graph için Azure Active Directory PowerShell'i yükleme](/powershell/azure/active-directory/install-adv2)

- **Microsoft Teams'de IB için yönetici onayı**: IB ilkeleriniz geçerli olduğunda, IB uyumsuz uyumluluk kullanıcılarını Gruplar'dan kaldırabilirler (örneğin, grupları temel alan Teams kanalları). Bu yapılandırma, kuruluşunuzun ilkeler ve düzenlemeler ile uyumlu kalmasını sağlamaya yardımcı olur. IB ilkelerinin Microsoft Teams beklendiği gibi çalışmasını sağlamak için aşağıdaki yordamı kullanın.

   1. Önkoşul: [Graph için Azure Active Directory PowerShell'i yükleyin](/powershell/azure/active-directory/install-adv2).

   1. Aşağıdaki PowerShell cmdlet'lerini çalıştırın:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. İstendiğinde, Office 365 için iş veya okul hesabınızı kullanarak oturum açın.

   1. **İstenen izinler** iletişim kutusunda bilgileri gözden geçirin ve **kabul et'i** seçin. Uygulama tarafından istenen izinler aşağıda verilmiştir.

      > [!div class="mx-imgBorder"]
      > ![Görüntü.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Tüm önkoşullar karşılandığında sonraki adıma geçin.

## <a name="step-2-segment-users-in-your-organization"></a>2. Adım: Kuruluşunuzdaki kullanıcıları segmentlere ayırma

Bu adım sırasında hangi IB ilkelerinin gerekli olduğunu belirler, tanımlayacak segmentlerin listesini oluşturur ve ardından segmentlerinizi tanımlarsınız.

### <a name="determine-what-policies-are-needed"></a>Hangi ilkelerin gerekli olduğunu belirleme

Kuruluşunuzun gereksinimlerini göz önünde bulundurarak, kuruluşunuzda IB ilkelerine ihtiyacı olacak grupları belirleyin. Kendinize aşağıdaki soruları sorun:

- Kuruluşunuzdaki gruplar ve kullanıcılar arasında iletişim ve işbirliği kısıtlaması gerektiren iç, yasal veya sektör düzenlemeleri var mı?
- Başka bir kullanıcı grubuyla iletişim kurması engellenmesi gereken gruplar veya kullanıcılar var mı?
- Yalnızca bir veya iki kullanıcı grubuyla iletişim kurmasına izin verilmesi gereken gruplar veya kullanıcılar var mı?

İhtiyacınız olan ilkeleri iki türden birine ait olarak düşünün:

- *İlkeleri engelleme* , bir grubun başka bir grupla iletişim kurmasını engeller.
- *İlkelere izin ver* , bir grubun yalnızca belirli gruplarla iletişim kurmasına izin verir.

Gerekli grupların ve ilkelerin ilk listesine sahip olduğunuzda, IB ilkeleri için ihtiyacınız olan segmentleri tanımlamaya devam edin.

### <a name="identify-segments"></a>Segmentleri tanımlama

İlk ilke listenize ek olarak, kuruluşunuz için segmentlerin listesini oluşturun. IB ilkelerine dahil edilecek kullanıcılar bir segmente ait olmalıdır. Kullanıcı yalnızca bir segmentte olabileceği için segmentlerinizi dikkatli bir şekilde planlayın. Her segmentte yalnızca bir IB ilkesi uygulanabilir.

> [!IMPORTANT]
> Kullanıcı yalnızca bir segmentte olabilir.

Kuruluşunuzun dizin verilerinde segmentleri tanımlamak için hangi öznitelikleri kullanacağınızı belirleyin. *Department*, *MemberOf* veya desteklenen IB özniteliklerinden herhangi birini kullanabilirsiniz. Kullanıcılar için seçtiğiniz öznitelikte değerler olduğundan emin olun. Daha fazla bilgi için bkz. [IB için desteklenen öznitelikler](information-barriers-attributes.md).

> [!IMPORTANT]
> **Sonraki bölüme geçmeden önce dizin verilerinizin, segmentleri tanımlamak için kullanabileceğiniz öznitelik değerlerine sahip olduğundan emin olun**. Dizin verilerinizin kullanmak istediğiniz öznitelikler için değerleri yoksa, IB'yi yapılandırmaya devam etmeden önce kullanıcı hesaplarının bu bilgileri içerecek şekilde güncelleştirilmesi gerekir. Bu konuda yardım almak için aşağıdaki kaynaklara bakın:<br/>- [Office 365 PowerShell ile kullanıcı hesabı özelliklerini yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Azure Active Directory kullanarak kullanıcının profil bilgilerini ekleme veya güncelleştirme](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>PowerShell kullanarak segmentleri tanımlama

Sonraki görev, kuruluşunuz için segmentleri tanımlamaktır. Segmentleri tanımlamak kullanıcıları etkilemez, yalnızca IB ilkelerinin tanımlanıp uygulanacağı aşamayı ayarlar.

1. Kullanmak istediğiniz [özniteliğe](information-barriers-attributes.md) karşılık gelen **UserGroupFilter** parametresiyle **New-OrganizationSegment** cmdlet'ini kullanın.

    | Sözdizimi | Örnek |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Bu örnekte, *departman* özniteliğindeki bir değer olan *İk* kullanılarak *İk* adlı bir kesim tanımlanmıştır. Cmdlet'in **-eq** bölümü "eşittir" anlamına gelir. (Alternatif olarak, "eşit değil" anlamına gelen **-ne** kullanabilirsiniz. Bkz [. Segment tanımlarında "eşittir" ve "eşit değil" kullanma](#using-equals-and-not-equals-in-segment-definitions).) |

    Her cmdlet'i çalıştırdıktan sonra yeni segmentle ilgili ayrıntıların listesini görmeniz gerekir. Ayrıntılar arasında segmentin türü, kimin oluşturduğu veya en son değiştirildiği vb. yer alır. 

2. Tanımlamak istediğiniz her segment için bu işlemi yineleyin.

    > [!IMPORTANT]
    > **Segmentlerinizin çakışmadığından emin olun**. IB ilkelerinden etkilenecek her kullanıcı bir (ve yalnızca bir) kesime ait olmalıdır. Hiçbir kullanıcı iki veya daha fazla kesime ait olmamalıdır. Örnek senaryo için bu makaledeki [Örnek: Contoso'nun tanımlı kesimleri](#contosos-defined-segments) konusuna bakın.

Segmentlerinizi tanımladıktan sonra [3. Adım: Bilgi engeli ilkelerini tanımlama](#step-3-define-information-barrier-policies) bölümüne geçin.

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Segment tanımlarında "equals" ve "not equals" kullanma

Aşağıdaki örnekte, "Departman İk'ya eşittir" şeklinde bir segment tanımlıyoruz. 

| Örnek | Not |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Bu örnekte segment tanımının **-eq** olarak belirtilen bir "equals" parametresi içerdiğine dikkat edin. |

Segmentleri, aşağıdaki tabloda gösterildiği gibi **-ne** olarak belirtilen bir "eşit değil" parametresi kullanarak da tanımlayabilirsiniz:

| Sözdizimi | Örnek |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | Bu örnekte *Satış'ta olmayan* herkesi içeren *NotSales* adlı bir segment tanımladık. Cmdlet'in **-ne** kısmı "eşit değil" anlamına gelir. |

"eşittir" veya "eşit değil" kullanarak segment tanımlamaya ek olarak, "eşittir" ve "eşit değil" parametrelerini kullanarak bir segment tanımlayabilirsiniz. Mantıksal *AND* ve *OR* işleçlerini kullanarak karmaşık grup filtreleri de tanımlayabilirsiniz.

| Sözdizimi | Örnek |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | Bu örnekte, yerel olarak bulunan ve konumları *Geçici* olarak listelenmeyen kullanıcıları içeren *LocalFTE* adlı bir segment tanımladık. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| Bu örnekte, group3@contoso.com üyesi değil group1@contoso.com üyesi olan kullanıcıları içeren *Segment1* adlı bir segment tanımladık. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | Bu örnekte, group2@contoso.com üyesi olan ve group3@contoso.com üyesi olmayan kullanıcıları içeren *Segment2* adlı bir segment tanımladık. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| Bu örnekte, group1@contoso.com ve group2@contoso.com kullanıcıları içeren ve group3@contoso.com üyesi olmayan *Segment1and2* adlı bir segment tanımladık. |

> [!TIP]
> Mümkünse, "-eq" veya "-ne" içeren segment tanımlarını kullanın. Karmaşık segment tanımları tanımlamamaya çalışın.

## <a name="step-3-define-information-barrier-policies"></a>3. Adım: Bilgi engeli ilkelerini tanımlama

Belirli segmentler arasındaki iletişimi engellemeniz mi yoksa iletişimleri belirli segmentlerle sınırlamanız mı gerektiğini belirleyin. İdeal olarak, kuruluşunuzun iç, yasal ve sektör gereksinimleriyle uyumlu olduğundan emin olmak için en az IB ilkesi sayısını kullanırsınız.

> [!TIP]
> Kullanıcı deneyimi tutarlılığı için mümkünse çoğu senaryo için Engelleme ilkelerini kullanmanızı öneririz.

Kullanıcı segmentleri listeniz ve tanımlamak istediğiniz IB ilkeleriyle bir senaryo seçin ve adımları izleyin.

- [Senaryo 1: Segmentler arasındaki iletişimi engelleme](#scenario-1-block-communications-between-segments)
- [Senaryo 2: Bir segmentin yalnızca bir diğer segmentle iletişim kurmasına izin verme](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **İlkeleri tanımlarken bir segmente birden fazla ilke atamadığınızdan emin olun**. Örneğin, *Satış* adlı bir segment için bir ilke tanımlarsanız, *Sales* için ek bir ilke tanımlamayın.<p> Ayrıca, IB ilkelerini tanımlarken, uygulamaya hazır olana kadar bu ilkeleri devre dışı durumuna ayarladığınızdan emin olun. İlkelerin tanımlanması (veya düzenlenmesi) bu ilkeler etkin duruma ayarlanıp sonra uygulanana kadar kullanıcıları etkilemez.

### <a name="scenario-1-block-communications-between-segments"></a>Senaryo 1: Segmentler arasındaki iletişimi engelleme

Segmentlerin birbiriyle iletişim kurmasını engellemek istediğinizde iki ilke tanımlarsınız: her yön için bir ilke. Her ilke iletişimi yalnızca bir yönde engeller.

Örneğin, Segment A ile Segment B arasındaki iletişimi engellemek istediğinizi varsayalım. Bu durumda, Segment A'nın Segment B ile iletişim kurmasını engelleyen bir ilke tanımlarsınız ve ardından B Segmenti'nin A Segmenti ile iletişim kurmasını önlemek için ikinci bir ilke tanımlarsınız.

1. İlk engelleme ilkenizi tanımlamak için **SegmentsBlocked** parametresiyle **New-InformationBarrierPolicy** cmdlet'ini kullanın.

    | Sözdizimi | Örnek |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Bu örnekte Sales adlı bir segment için *Sales-Research* *adlı bir* ilke tanımladık. Etkin ve uygulandığında, bu ilke *Satış'taki* kullanıcıların *Araştırma* adlı segmentteki kullanıcılarla iletişim kurmasını engeller. |

2. İkinci engelleme segmentinizi tanımlamak için, **SegmentlerBlocked** parametresiyle **New-InformationBarrierPolicy** cmdlet'ini yeniden kullanın; bu kez segmentler ters çevrildi.

    | Örnek | Not |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | Bu örnekte, Research'in *Satış* ile iletişim kurmasını önlemek için *Research-Sales* adlı bir ilke tanımladık. |

3. Aşağıdaki eylemlerden birine geçin:

   - (Gerekirse) [Bir segmentin yalnızca bir diğer segmentle iletişim kurmasına izin veren bir ilke tanımlama](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Tüm ilkeleriniz tanımlandıktan sonra) [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Senaryo 2: Bir segmentin yalnızca bir diğer segmentle iletişim kurmasına izin verme

Bir segmentin yalnızca bir diğer segmentle iletişim kurmasına izin vermek istediğinizde, bu segment için yalnızca bir ilke tanımlarsınız. İletişimde olan segment için benzer bir yönlü ilke gerekmez (çünkü varsayılan olarak herkesle iletişim kurabilir ve işbirliği yapabilir).

1. Bir segmentin yalnızca bir diğer segmentle iletişim kurmasına izin vermek için, **SegmentlerAllowed** parametresiyle **New-InformationBarrierPolicy** cmdlet'ini kullanın.

    | Sözdizimi | Örnek |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> Bu örnekte, Manufacturing adlı bir segment için *Manufacturing-HR* *adlı bir* ilke tanımladık. Etkin ve uygulandığında, bu ilke *Üretim'deki* kullanıcıların yalnızca *İk* adlı segmentteki kullanıcılarla iletişim kurmasına olanak tanır. Bu durumda *Üretim* , *İk'nın* parçası olmayan kullanıcılarla iletişim kuramaz. |

    **Gerekirse, aşağıdaki örnekte gösterildiği gibi bu cmdlet ile birden çok kesim belirtebilirsiniz.**

    | Sözdizimi | Örnek |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> Bu örnekte *, Araştırma* segmentinin yalnızca *İk* ve *Üretim* ile iletişim kurmasını sağlayan bir ilke tanımladık. |

    Belirli segmentlerin yalnızca belirli belirli segmentlerle iletişim kurmasına izin vermek için tanımlamak istediğiniz her ilke için bu adımı yineleyin.

2. Aşağıdaki eylemlerden birine geçin:

   - (Gerekirse) [Segmentler arasındaki iletişimi engellemek için bir ilke tanımlama](#scenario-1-block-communications-between-segments) 
   - (Tüm ilkeleriniz tanımlandıktan sonra) [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>4. Adım: Bilgi engeli ilkelerini uygulama

IB ilkeleri etkin duruma ayarlayıp ilkeleri uygulayana kadar geçerli olmaz.

1. Tanımlanmış ilkelerin listesini görmek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın. Her ilkenin durumunu ve kimliğini (GUID) not edin.

    Sözdizimi: `Get-InformationBarrierPolicy`

2. bir ilkeyi etkin duruma ayarlamak için, **Bir Identity** parametresiyle **Set-InformationBarrierPolicy** cmdlet'ini ve **State parametresini Etkin** olarak ayarlayın. 

    | Sözdizimi | Örnek |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> Bu örnekte GUID *43c37853-ea10-4b90-a23d-ab8c93772471* olan bir IB ilkesini etkin duruma ayarlayacağız. |

    Bu adımı her ilke için uygun şekilde yineleyin.

3. IB ilkelerinizi etkin duruma ayarlamayı bitirdiğinizde, Güvenlik & Uyumluluk Merkezi PowerShell'de **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Sözdizimi: `Start-InformationBarrierPoliciesApplication`

    komutunu çalıştırdıktan `Start-InformationBarrierPoliciesApplication`sonra, sistemin ilkeleri uygulamaya başlaması için 30 dakika bekleyin. Sistem, ilkeler kullanıcı tarafından kullanıcı tarafından uygulanır. Sistem saatte yaklaşık 5.000 kullanıcı hesabını işler.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Kullanıcı hesaplarının, kesimlerinin, ilkelerin veya ilke uygulamasının durumunu görüntüleme

PowerShell ile aşağıdaki tabloda listelendiği gibi kullanıcı hesaplarının, segmentlerin, ilkelerin ve ilke uygulamasının durumunu görüntüleyebilirsiniz.

| Bu bilgileri görüntülemek için | Bu eylemi gerçekleştirin |
|:---------------|:----------|
| Kullanıcı hesapları | Kimlik parametreleriyle **Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın. <p> Sözdizimi: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her kullanıcıyı benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. <p> Örnek: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Bu örnekte, Office 365'de iki kullanıcı hesabına başvuracağız: *Megan* için *meganb* ve *Alex* için *alexw*. <p> (Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Bu cmdlet, kullanıcılar hakkında öznitelik değerleri ve uygulanan tüm bilgi engeli ilkeleri gibi bilgileri döndürür.|
| Segment | **Get-OrganizationSegment** cmdlet'ini kullanın.<p> Sözdizimi: `Get-OrganizationSegment` <p> Bu cmdlet, kuruluşunuz için tanımlanan tüm segmentlerin listesini görüntüler. |
| Bilgi engeli ilkeleri | **Get-InformationBarrierPolicy** cmdlet'ini kullanın. <p> Sözdizimi: `Get-InformationBarrierPolicy` <p> Bu cmdlet, tanımlanan bilgi engeli ilkelerinin listesini ve bunların durumunu görüntüler. |
| En son bilgi engeli ilkesi uygulaması | **Get-InformationBarrierPoliciesApplicationStatus** cmdlet'ini kullanın. <p> Sözdizimi: `Get-InformationBarrierPoliciesApplicationStatus`<p> Bu cmdlet, ilke uygulamasının tamamlanıp tamamlanmadığı, başarısız olup olmadığı veya devam edip etmediğiyle ilgili bilgileri görüntüler. |
| Tüm bilgi engeli ilkesi uygulamaları|Kullanın `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Bu cmdlet, ilke uygulamasının tamamlanıp tamamlanmadığı, başarısız olup olmadığı veya devam edip etmediğiyle ilgili bilgileri görüntüler.|

### <a name="what-if-i-need-to-remove-or-change-policies"></a>İlkeleri kaldırmam veya değiştirmem gerekirse ne olur?

IB ilkelerinizi yönetmenize yardımcı olacak kaynaklar sağlanır.

- IB ilkelerini düzenlemek, durdurmak veya kaldırmak için bkz. [Bilgi engeli ilkelerini yönetme](information-barriers-edit-segments-policies.md).
- IB'de bir sorun olursa bkz [. Bilgi engelleriyle ilgili sorunları giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>5. Adım: SharePoint ve OneDrive ile ilgili bilgi engelleri için yapılandırma

IB'yi SharePoint ve OneDrive için yapılandırıyorsanız, bu hizmetlerde IB'yi etkinleştirmeniz gerekir. IB'yi Microsoft Teams için yapılandırıyorsanız bu hizmetlerde IB'yi de etkinleştirmeniz gerekir. Microsoft Teams ekipte bir ekip oluşturulduğunda, otomatik olarak bir SharePoint sitesi oluşturulur ve dosya deneyimi için Microsoft Teams ile ilişkilendirilir. IB ilkeleri bu yeni SharePoint sitesinde ve dosyalarında varsayılan olarak kabul edilmez.

SharePoint ve OneDrive IB'yi etkinleştirmek için SharePoint [bilgi engellerini kullanma](/sharepoint/information-barriers) makalesindeki yönergeleri ve adımları izleyin.

## <a name="step-6-information-barriers-modes"></a>6. Adım: Bilgi engelleri modları

Modlar, kaynağın IB moduna göre Microsoft 365 kaynağın erişimini, paylaşımını ve üyeliğini güçlendirmeye yardımcı olabilir. Modlar Microsoft 365 Grupları, Microsoft Teams, OneDrive ve SharePoint sitelerinde desteklenir ve yeni veya mevcut IB yapılandırmanızda otomatik olarak etkinleştirilir.

Aşağıdaki IB modları Microsoft 365 kaynaklarda desteklenir:

| **Mod** | **Açıklama** | **Örnek** |
|:-----|:------------|:--------|
| **Açık** | Microsoft 365 kaynağıyla ilişkilendirilmiş IB ilkeleri veya kesimleri yoktur. Herkes kaynağın üyesi olmaya davet edilebilir. | Kuruluşunuz için piknik etkinliği için oluşturulmuş bir ekip sitesi. |
| **Sahip Denetimli (önizleme)** | Microsoft 365 kaynağının IB ilkesi, kaynak sahibinin IB ilkesinden belirlenir. Kaynak sahipleri, IB ilkelerine göre herhangi bir kullanıcıyı kaynağa davet edebilir. Şirketiniz, sahibi tarafından denetlenen uyumsuz segment kullanıcıları arasında işbirliğine izin vermek istediğinde bu mod kullanışlıdır. IB ilkesine göre yalnızca kaynak sahibi yeni üyeler ekleyebilir. | İk Başkan Yardımcısı, Satış ve Araştırma VM'leri ile işbirliği yapmak istiyor. Hem Satış hem de Araştırma segmenti kullanıcılarını aynı siteye eklemek için IB modu *Sahip Moded* ile ayarlanan yeni bir SharePoint sitesi. Kaynağa uygun üyelerin eklendiğinden emin olmak sahibin sorumluluğundadır. |
| **Örtülü** | Microsoft 365 kaynağının IB ilkesi veya kesimleri, kaynak üyeleri IB ilkesinden devralınır. Sahibi, kaynağın mevcut üyeleriyle uyumlu olduğu sürece üye ekleyebilir. Bu, Microsoft Teams için varsayılan IB modudur. | Satış segmenti kullanıcısı, kuruluştaki diğer uyumlu segmentlerle işbirliği yapmak için bir Microsoft Teams ekibi oluşturur. |
| **Açık** | Microsoft 365 kaynağının IB ilkesi, kaynakla ilişkili segmentlere göredir. Kaynak sahibi veya SharePoint yöneticisi, kaynak üzerindeki segmentleri yönetebilir.  | Yalnızca Satış segmenti üyelerinin, Satış segmentini siteyle ilişkilendirerek işbirliği yapmaları için oluşturulmuş bir site.   |

IB modları ve hizmetler arasında nasıl yapılandırıldıkları hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Bilgi engeli modları ve Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Bilgi engelleri modları ve OneDrive](/onedrive/information-barriers)
- [Bilgi engelleri modları ve SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Örnek senaryo: Contoso'nun bölümleri, kesimleri ve ilkeleri

Bir kuruluşun segmentleri ve ilkeleri tanımlamaya nasıl yaklaşabileceğini görmek için aşağıdaki örnek senaryoyu göz önünde bulundurun.

### <a name="contosos-departments-and-plan"></a>Contoso'nun bölümleri ve planı

Contoso'nun beş bölümü vardır: *İk*, *Satış*, *Pazarlama*, *Araştırma* ve *Üretim*. Sektör düzenlemeleriyle uyumlu kalmak için, bazı departmanlardaki kullanıcıların aşağıdaki tabloda listelendiği gibi diğer departmanlarla iletişim kurmaması gerekir:

| Segment | ile iletişim kurabilir | ile iletişim kuramıyorum |
|:----------|:--------------|:-----------------|
| HR | Herkes | (kısıtlama yok) |
| Satış | İk, Pazarlama, Üretim | Araştırma |
| Pazarlama | Herkes | (kısıtlama yok) |
| Araştırma | İk, Pazarlama, Üretim | Satış |
| Üretim | İk, Pazarlama | İk veya Pazarlama dışında herkes |

Bu yapı için Contoso'nun planı üç IB ilkesi içerir:

1. Satışların Araştırma ile iletişim kurmasını önlemek için tasarlanmış bir IB ilkesi
2. Araştırma'nın Satış ile iletişim kurmasını engelleyen başka bir IB ilkesi.
3. İmalat'ın yalnızca İk ve Pazarlama ile iletişim kurmasını sağlamak için tasarlanmış bir IB ilkesi.

Bu senaryo için *İk* veya *Pazarlama* için IB ilkeleri tanımlamak gerekmez.

### <a name="contosos-defined-segments"></a>Contoso'nun tanımlı kesimleri

Contoso, segmentleri tanımlamak için Azure Active Directory'deki Department özniteliğini aşağıdaki gibi kullanır:

| Bölüm | Segment Tanımı |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Satış | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Pazarlama | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Araştırma | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Üretim | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Segmentler tanımlandığında Contoso, IB ilkelerini tanımlamaya devam eder.

### <a name="contosos-information-barrier-policies"></a>Contoso'nun bilgi engeli ilkeleri

Contoso, aşağıdaki tabloda açıklandığı gibi üç IB ilkesi tanımlar:

| Ilkesi | İlke Tanımı |
|:---------|:--------------------|
| **İlke 1: Satışların Araştırma ile iletişim kurmasını engelleme** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Bu örnekte, bilgi engeli ilkesi *Sales-Research* olarak adlandırılır. Bu ilke etkin ve uygulandığında, Satış segmentindeki kullanıcıların Araştırma segmentindeki kullanıcılarla iletişim kurmasını önlemeye yardımcı olur. Bu ilke tek yönlü bir ilkedir; Araştırma'nın Satış ile iletişim kurmasını engellemez. Bunun için İlke 2 gereklidir. |
| **İlke 2: Araştırmanın Satış ile iletişim kurmasını engelleme** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> Bu örnekte, bilgi engeli ilkesi *Research-Sales* olarak adlandırılır. Bu ilke etkin ve uygulandığında, Araştırma segmentindeki kullanıcıların Satış segmentindeki kullanıcılarla iletişim kurmasını önlemeye yardımcı olur. |
| **İlke 3: Üretimin yalnızca İk ve Pazarlama ile iletişim kurmasına izin ver** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> Bu durumda, IB ilkesi *Manufacturing-HRMarketing* olarak adlandırılır. Bu ilke etkin ve uygulandığında, Üretim yalnızca İk ve Pazarlama ile iletişim kurabilir. İk ve Pazarlama'nın diğer segmentlerle iletişim kurması kısıtlanmaz. |

Segmentler ve ilkeler tanımlandığında Contoso, **Start-InformationBarrierPoliciesApplication** cmdlet'ini çalıştırarak ilkeleri uygular.

Cmdlet tamamlandığında Contoso, sektör gereksinimleriyle uyumludur.

## <a name="resources"></a>Kaynaklar

- [Bilgi engelleri hakkında daha fazla bilgi edinme](information-barriers.md)
- [Microsoft Teams bilgi engelleri hakkında daha fazla bilgi edinin](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'da bilgi engelleri hakkında daha fazla bilgi edinin](/sharepoint/information-barriers)
- [OneDrive bilgi engelleri hakkında daha fazla bilgi edinin](/onedrive/information-barriers)
