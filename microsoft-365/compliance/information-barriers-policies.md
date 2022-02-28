---
title: Bilgi engellerini çalışmaya başlama
description: Bilgi engelleriyle çalışmaya nasıl başlay ola öğrenin.
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
ms.openlocfilehash: 1a9b6a4000b6d96fa8fe60b3abc60ff01676073e
ms.sourcegitcommit: 7b83e2605895fee5c73cd1d01f4cd16e1457a69f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "62990628"
---
# <a name="get-started-with-information-barriers"></a>Bilgi engellerini çalışmaya başlama

Bilgi engelleriyle, kullanıcıların belirli kesimlerinin birbirleriyle iletişim kurmasını önleyen veya belirli kesimlerin yalnızca diğer bazı kesimlerle iletişim kurmasına olanak verecek ilkeler tanımlayabilirsiniz. Bilgi engeli ilkeleri, kurum gerek ilgili endüstri standartları ve düzenlemelerine uyumluluğunu korumanıza ve olası ilgi çakışmalarını önlemenize yardımcı olabilir. Daha fazla bilgi için bkz [. Bilgi engelleri hakkında bilgi öğrenme](information-barriers.md).

Bu makalede, bilgi engeli ilkelerinin nasıl yapılandırıldığından emin olun. Çeşitli adımlar söz konusu olduğundan, bilgi engeli ilkelerini yapılandırmaya başlamadan önce tüm süreci gözden geçirmeyi unutmayın.

> [!TIP]
> Bu makale, bilgi [engeli ilkelerinizi](#example-scenario-contosos-departments-segments-and-policies) planlamanıza ve tanımlamanıza yardımcı olacak örnek bir senaryo içerir.

## <a name="concepts"></a>Kavramlar

Bilgi engeli olan ilkeler tanımladığınız zaman, kullanıcı hesabı öznitelikleri, kesimler, 'blok' ve/veya 'izin ver' ilkeleri ve ilke uygulamasıyla çalışırsınız.

- Kullanıcı hesabı öznitelikleri Azure Active Directory Exchange Online. Bu öznitelikler bölüm, iş unvanı, konum, ekip adı ve diğer iş profili ayrıntılarını içerebilir.
- Kesimler, seçilen kullanıcı hesabı özniteliği kullanılarak Microsoft 365 uyumluluk merkezi kullanıcı **kümesidir**. (Desteklenen [özniteliklerin listesine bakın](information-barriers-attributes.md).)
- Bilgi engeli ilkeleri iletişim sınırlarını veya kısıtlamalarını belirler. Bilgi engeli ilkelerini tanımlarken, iki tür ilkeden birini seçersiniz:
  - *İlkeleri* engelle, bir segmentin başka bir segmentle iletişim kurmasını önle.
  - *İlkelere* izin ver, bir segmentin yalnızca belirli diğer kesimlerle iletişim kurmasına olanak sağlar.
- İlke uygulaması, tüm bilgi engeli ilkeleri tanımlandığı ve bunları kuruluş içinde uygulamaya hazır hale geldikten sonra yapılır.

## <a name="configuration-at-a-glance"></a>Bir bakışta yapılandırma

| **Adımlar** | **Nelerin dahil olduğu** |
|:------|:----------------|
| **1. Adım**: [Önkoşulların karşı olduğundan emin olun](#step-1-make-sure-prerequisites-are-met) | - Gerekli lisanslara ve [izinlere sahip olduğunu doğrulayın](information-barriers.md#required-licenses-and-permissions)<br/>- Dizininizin kullanıcıları bölümleme için veri de dahil olduğunu doğrulama<br/>- Arama için kapsamı olan dizin aramalarını Microsoft Teams<br/>- Denetim günlüğünün açık olduğundan emin olun<br/>- Adres defteri Exchange ilgili ilkelerin var olduğundan emin olun<br/>- PowerShell kullanma (örnekler verilmiştir)<br/>- E-postanın kullanımı için Microsoft Teams izni sağlama (adımlar dahildir) |
| **2. Adım**: [Kuruluşta kullanıcıları kesimlere göre bölümleme](#step-2-segment-users-in-your-organization) | - Hangi ilkelerin gerektiğini belirleme<br/>- Tanımlamak üzere bir kesimler listesi yapma<br/>- Hangi özniteliklerin kullanılamayacaklarını belirleme<br/>- İlke filtreleri açısından kesimleri tanımlayın |
| **3. Adım**: [Bilgi engeli ilkelerini tanımlama](#step-3-define-information-barrier-policies) | - İlkelerinizi tanımlayın (henüz geçerli değildir)<br/>- İki tür (engelle veya izin ver) seçin |
| **4. Adım**: [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies) | - İlkeleri etkin durum olarak ayarlama<br/>- İlke uygulamasını çalıştırın<br/>- İlke durumunu görüntüleme |
| **5. Adım**: [Web ve SharePoint (isteğe bağlı) OneDrive engellerini yapılandırma](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - İletişim ve eğitim için SharePoint engellerini OneDrive |
| **6. Adım**: [Bilgi engelleri modları (isteğe bağlı)](#step-6-information-barriers-modes) | - Uygunsa bilgi engeli modlarını güncelleştirin |

## <a name="step-1-make-sure-prerequisites-are-met"></a>1. Adım: Önkoşulların karşı olduğundan emin olun

Gerekli lisanslara [ve izinlere ek olarak](information-barriers.md#required-licenses-and-permissions), bilgi engellerini yapılandırmadan önce aşağıdaki gereksinimlerin karşı gerektiğinden emin olun:

- **Dizin verileri**: Kuruluş yapının dizin verilerine yansıyan olduğundan emin olun. Bu eylemi yapmak için, grup üyeliği, bölüm adı vb. kullanıcı hesabı özniteliklerinin Grup Üyeliği (veya Bölüm Adı) içinde Azure Active Directory doğru doldurulduğundan Exchange Online. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
  - [Bilgi engeli ilkeleri için öznitelikler](information-barriers-attributes.md)
  - [Profili kullanarak kullanıcının profil bilgilerini ekleme veya Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Kullanıcı hesabı özelliklerini Office 365 PowerShell ile yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Kapsamı olan dizin araması**: Kuruluşta ilk bilgi engeli politikasını tanımlamadan önce, belirli bir dizin arama kapsamını belirlemeli ve [Microsoft Teams.](/MicrosoftTeams/teams-scoped-directory-search) Bilgi engeli ilkelerini ayarlamadan veya tanımlamadan önce, kapsamlı dizin arama özelliğini etkinleştirdikten sonra en az 24 saat bekleyin.

- **Exchange Online engeller**: Bilgi engeli ilkelerinin çalışması için, hedef kullanıcılara bir lisans Exchange Online gerekir.

- **Denetim günlüğünün etkinleştirildiğinden** emin olun: İlke uygulamasının durumuna bakmak için, denetim günlüğünün açık olması gerekir. Bu kuruluşlarda denetim Microsoft 365 varsayılan olarak etkinleştirilir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmıştır. If auditing is disabled for your organization, it might be because another administrator has turned it. Bu adımı tamamlarken denetimi yeniden açmanın bir sorun olduğunu doğrulamanızı öneririz. Daha fazla bilgi için [bkz. Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md).

- **Adres defteri ilkeleri yok**: Bilgi engeli ilkelerini tanımlamadan ve uygulamadan önce, adres defteri Exchange ilkelerinin uygulamay olduğundan emin olun. Bilgi engelleri adres defteri ilkelerine dayalıdır, ancak iki tür ilke uyumlu değildir. Bu tür ilkeleriniz varsa, önce adres defteri [ilkelerinizi kaldırmayı unutmayın](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Bilgi engeli ilkeleri etkinleştirildikten ve hiyerarşik adres defteri etkinleştirildikten sonra, bilgi engeli segmentinde yer görmeyen tüm kullanıcılar Exchange online'da [](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) hiyerarşik adres kitabını görebilir.****

- **PowerShell kullanmayı yönetme**: Şu anda, bilgi engeli ilkeleri Güvenlik ve Uyumluluk Merkezi PowerShell& tanımlanır ve yönetilir. Bu makalede birkaç örnek sağlanmıştır, ancak PowerShell cmdlet'leri ve parametreleri hakkında bilgi sahibi olmak gerekir. Ayrıca, PowerShell modülü Azure Active Directory gerekir.
  - [Bağlan ve Uyumluluk & PowerShell'e](/powershell/exchange/connect-to-scc-powershell)
  - [Graph Azure Active Directory PowerShell'i Graph](/powershell/azure/active-directory/install-adv2)

- Microsoft Teams'te bilgi engellerini yönetici onayı: **IB** ilkeleriniz olduğunda, IB uyumlu olmayan kullanıcıları Gruplar'dan (örneğin, gruplara dayalı Teams kanal) kaldırabilirler. Bu yapılandırma, kuruma ilişkin ilkelerin ve yasal düzenlemelere uygun olmaya yardımcı olur. Bilgi engeli ilkelerinin kaynak kodda beklendiği gibi çalışması için aşağıdaki Microsoft Teams.

   1. [Önkoşul: Azure Active Directory için PowerShell'i Graph](/powershell/azure/active-directory/install-adv2).

   1. Aşağıdaki PowerShell cmdlet'lerini çalıştırın:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. İstendiğinde, iş veya okul hesabınızla oturum açın ve Office 365.

   1. İstenen **izinler iletişim kutusunda** bilgileri gözden geçirin ve kabul et'i **seçin**. Uygulama tarafından istenen izinler aşağıda verilmiştir.

      > [!div class="mx-imgBorder"]
      > ![resmine tıklayın.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Tüm önkoşullar karşılandığı zaman, sonraki adıma geçin.

> [!TIP]
> Planınızı hazırlamanıza yardımcı olmak için, bu makalede örnek bir senaryo yer almaktadır. [Contoso'nun bölümlerine, kesimlerine ve ilkelerine bakın](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>2. Adım: Kuruluşta kullanıcıları kesimlere göre bölümleme

Bu adımda, hangi bilgi engeli ilkelerinin gerekli olduğunu belirler, segmentlerinizi tanımlamak için bir kesimler listesi oluşturur ve sonra da kesimlerinizi tanımlarsınız.

### <a name="determine-what-policies-are-needed"></a>Hangi ilkelerin gerektiğini belirleme

Yasal düzenlemeler ve endüstri düzenlemelerini göz önünde bulundurarak, organizasyon içinde bilgi engeli ilkelerine ihtiyaç olacak gruplar kimler? Liste yapma. Başka bir grupla iletişim kurmasını engelleyen gruplar var mı? Yalnızca bir veya iki grupla iletişim kurmasına izin verilen gruplar var mı? İki gruptan birini ait olarak ihtiyacınız olan ilkeleri düşünmelisiniz:

- "Engelle" ilkeleri, bir grubun başka bir grupla iletişim kurmasını engelleme.
- "İzin Ver" ilkeleri, bir grubun yalnızca belirli belirli gruplarla iletişim kurmasına olanak sağlar.

İlk grup ve ilke listeniz olduğunda, ihtiyacınız olacak kesimleri belirlemek için devam edin.

### <a name="identify-segments"></a>Kesimleri belirleme

İlkeler listenizin yanı sıra, organizasyonunız için kesimlerin listesini de hazır olun. Bilgi engeli ilkelerine dahil olacak kullanıcılar bir segmente dahil olmalıdır. Bir kullanıcı yalnızca bir segmentte olabilirken segmentlerinizi dikkatle plan edin. Her segmente tek bir bilgi engeli ilkesi uygulanabilir.

> [!IMPORTANT]
> Bir kullanıcı yalnızca tek bir segmentte olabilir.

Kuruluş dizin verilerinde kesimler tanımlamak için hangi öznitelikleri kullanabileceğinizi belirler. *Department, MemberOf* *veya* desteklenen özniteliklerden herhangi birini kullanabilirsiniz. Kullanıcılar için seçenilen öznitelikte değerlerin olduğundan emin olun. [Bilgi engelleri için desteklenen özniteliklerin listesine bakın](information-barriers-attributes.md).

> [!IMPORTANT]
> **Sonraki bölüme başlamadan önce dizin verilerinizde, kesimleri tanımlamak için kullanabileceğiniz özniteliklere ilgili değerler olduğundan emin olun**. Dizin verilerinizde kullanmak istediğiniz özniteliklerin değerleri yoksa, bilgi engelleriyle devammeden önce kullanıcı hesaplarının bu bilgileri içerecek şekilde güncelleştirilmiş olması gerekir. Bu konuda yardım almak için aşağıdaki kaynaklara bakın:<br/>- [Kullanıcı hesabı özelliklerini Office 365 PowerShell ile yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Profili kullanarak kullanıcının profil bilgilerini ekleme veya Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>PowerShell kullanarak kesimleri tanımlama

Kesimlerin tanımlanması kullanıcıları etkilemez; yalnızca bilgi engeli ilkelerinin tanımlanmayacak ve sonra uygulanacak aşamayı ayarlar.

1. Kullanmak istediğiniz öznitelike karşılık gelen **UserGroupFilter** parametresiyle **New-OrganizationSegment** cmdlet'ini kullanın.[](information-barriers-attributes.md)

    | Söz dizimi | Örnek |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Bu örnekte, İk adlı bir *segment, Department* *özniteliğinde bir* değer olan *İk kullanılarak tanımlanır* . **Cmdlet'in -eq** bölümü "eşittir" anlamına gelir. (Alternatif olarak, - **ne kullanarak** "eşittir değil" anlamına da kullanabilirsiniz. Bkz [. Segment tanımlarında "eşittir" ve "eşit değil" kullanma](#using-equals-and-not-equals-in-segment-definitions).) |

    Her cmdlet'i çalıştırdikten sonra, yeni segmentle ilgili ayrıntıların bir listesini görüyor olması gerekir. Ayrıntılar, segmentin türünü ve bunu oluşturan veya en son değiştireni, daha sonra böyle devam eden bilgileri içerir. 

2. Tanımlamak istediğiniz her segment için bu işlemi yinelayın.

    > [!IMPORTANT]
    > **Kesimlerin çakışmay olduğundan emin olun**. Bilgi engellerinden etkilenen her kullanıcı, bir (ve yalnızca bir) segmente ait olmalı. Hiçbir kullanıcı iki veya daha fazla kesime ait olması gerekir. (Örnek [: Bu makaledeki Contoso'nun tanımlı](#contosos-defined-segments) kesimleri'ne bakın.)

Segmentlerinizi tanımdikten sonra, bilgi engeli ilkelerini [tanımlamaya devam edin](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Segment tanımlarında "eşittir" ve "eşittir değil" kullanma

Aşağıdaki örnekte, "Bölüm eşittir İk" gibi bir segment tanımlarız. 

| Örnek | Not |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Bu örnekte, segment **tanımında -eq** olarak ifade edilmiştir ve "eşittir" parametresi vardır. |

Ayrıca, aşağıdaki tabloda gösterildiği gibi ,ne olarak gösterilen "eşit değil" parametresi kullanarak kesimler tanımlayabilirsiniz:

| Söz dizimi | Örnek |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | Bu örnekte, SatışLar *bölümünde yer alan* herkesi içeren Satış Değil adlı bir segment tanımla *kullandık*. **Cmdlet'in -** ne bölümü "eşit değil" anlamına gelir. |

"Eşittir" veya "eşittir" kullanarak kesimler tanımlamaya ek olarak, hem "eşittir" hem de "eşit değil" parametrelerini kullanarak da bir segment tanımlayabilirsiniz. Mantıksal VE ve OR işleçlerini kullanarak karmaşık *grup filtreleri* *de tanımlayabilirsiniz* .

| Söz dizimi | Örnek |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | Bu örnekte, yerel olarak bulunan ve konumları Geçici olarak listelenmiyor kişilerini içeren *LocalFTE* adlı bir segment *tanımladik*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| Bu örnekte, *Segment1* adlı bir segment tanımladır ve bu segmente üye değil group1@contoso.com üyesi olan group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | Bu örnekte, *Segment2* adlı bir segment tanımladır ve bu segmente üye değil group2@contoso.com üyesi olan group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| Bu örnekte, *Segment1and2* adlı bir segment tanımladık ve bu segmente üye group1@contoso.com group2@contoso.com hem de group3@contoso.com. |

> [!TIP]
> Mümkünse "-eq" veya "-ne" içeren segment tanımlarını kullanın. Karmaşık segment tanımlarını tanımlamamaya deneyin.

## <a name="step-3-define-information-barrier-policies"></a>3. Adım: Bilgi engeli ilkelerini tanımlama

Belirli kesimler arasındaki iletişimi engellemeye mi yoksa iletişimi belirli kesimlere göre mi sınırlandırma ihtiyacınız olduğunu belirler. İdeal olarak, kuruma yönelik olarak yasal gereksinimlerle ve endüstri gereksinimleriyle uyumlu olduğundan emin olmak için en az sayıda ilkeyi kullanacağız.

Kullanıcı segmentleri listeniz ve tanımlamak istediğiniz bilgi engeli ilkeleri listeniz ile bir senaryo seçin ve ardından adımları izleyin.

- [1. Senaryo: Kesimler arasındaki iletişimi engelleme](#scenario-1-block-communications-between-segments)
- [Senaryo 2: Bir segmentin yalnızca başka bir segmentle iletişim kurmasına izin verme](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **İlkeleri tanımlarken bir segmente birden çok ilke atamadığınızdan emin olun**. Örneğin, Satış adlı bir segment için tek bir ilke *tanımlarsanız*, Satışlar için ek bir ilke *tanımlamayın*.<p> Ayrıca, bilgi engeli ilkelerini tanımlarken, bu ilkeleri uygulamaya hazır olana kadar devre dışı durumuna ayarladığınızdan emin olun. İlkeleri tanımlama (veya düzenleme), bu ilkeler etkin durum olarak ayarlanıncaya ve sonra uygulanmadan kullanıcıları etkilemez.

(Bu [makaledeki Örnek: Contoso'nun bilgi engeli](#contosos-information-barrier-policies) ilkelerine bakın.)

### <a name="scenario-1-block-communications-between-segments"></a>1. Senaryo: Kesimler arasındaki iletişimi engelleme

Kesimlerin birbirleriyle iletişim kurmalarını engellemek için iki ilke tanımlarsınız: her yön için bir ilke. Her ilke yalnızca tek bir yolla iletişimi engeller.

Örneğin, Segment A ile Segment B arasındaki iletişimi engellemek istediğiniz varsayalım. Bu durumda, Segment A'nın Segment B ile iletişim kurmasını önleyen bir ilke tanımlar, ardından da Segment B'nin Segment A ile iletişim kurmasını önlemek için ikinci bir ilke tanımlarsanız.

1. İlk engelleme ilkenizi tanımlamak için **, New-InformationBarrierPolicy** cmdlet'ini **SegmentsBlocked parametresiyle** kullanın.

    | Söz dizimi | Örnek |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Bu örnekte, Satış adlı bir segment için *Satış-Araştırma* adlı bir ilke *tanımladık*. Etkin ve uygulandığında, bu ilke Satış ekibini olan kişilerin *Araştırma adlı bir* bölümdeki insanlarla iletişim kurmasını *engellemeyi sağlar*. |

2. İkinci engelleme segmentini tanımlamak için **, New-InformationBarrierPolicy** cmdlet'ini **segmentsBlocked** parametresiyle yeniden kullanın; bu kez kesimler ters çevrildi.

    | Örnek | Not |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | Bu örnekte, Araştırma'nın Satışlarla iletişim *kurmasını önlemek için Araştırma-Satış* *adlı* bir ilke *tanımladık*. |

3. Aşağıdaki eylemlerden biri ile devam edin:

   - (Gerekirse) [Bir segmentin yalnızca başka bir segmentle iletişim kurmasına olanak sağlayan bir ilke tanımlama](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Tüm ilkeleriniz tanımlandığı zaman) [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Senaryo 2: Bir segmentin yalnızca başka bir segmentle iletişim kurmasına izin verme

1. Bir segmentin yalnızca bir kesimle başka bir segmentle iletişim kurmasına izin vermek için **, New-InformationBarrierPolicy** cmdlet'ini **SegmentsAllowed parametresiyle** kullanın.

    | Söz dizimi | Örnek |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> Bu örnekte, Üretim adlı bir segment için *Üretim-İk* adlı bir ilke *tanımladık*. Etkin ve uygulandığında, bu ilke Üretim'de *çalışan* kişilerin yalnızca İk adlı bir segmentte yer alan kullanıcılarla iletişim kurmasına olanak *sağlar*. (Bu durumda, *Üretim* İk'nın bir parçası değil kullanıcılarla iletişim *kuramaz*.) |

    **Gerekirse, aşağıdaki örnekte gösterildiği gibi, bu cmdlet ile birden çok kesim belirtebilirsiniz.**

    | Söz dizimi | Örnek |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> Bu örnekte, Araştırma kesiminin yalnızca İk ve Üretim ile  iletişim kurmasını sağlayan *bir ilke* *tanımladık*. |

    Belirli kesimlerin yalnızca diğer belirli kesimlerle iletişim kurmasına izin vermek üzere tanımlamak istediğiniz her ilke için bu adımı yinele.

2. Aşağıdaki eylemlerden biri ile devam edin:

   - (Gerekirse) [Kesimler arasındaki iletişimi engellemek için ilke tanımlama](#scenario-1-block-communications-between-segments) 
   - (Tüm ilkeleriniz tanımlandığı zaman) [Bilgi engeli ilkelerini uygulama](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>4. Adım: Bilgi engeli ilkelerini uygulama

Bilgi engeli ilkelerini, siz etkin durum durumuna ayarlamadan ve ardından ilkeleri uygulamadan önce geçerli olmaz.

1. Tanımlanmış **ilkelerin listesini görmek için Get-InformationBarrierPolicy** cmdlet'ini kullanın. Her ilkenin durumunu ve kimliğini (GUID) notun.

    Söz dizimi: `Get-InformationBarrierPolicy`

2. Bir ilkeyi etkin durum olarak ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini **Identity** parametresiyle ve State parametresi **de Etkin** olarak **ayarlanır**. 

    | Söz dizimi | Örnek |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> Bu örnekte, guid *43c37853-ea10-4b90-a23d-ab8c93772471* olan bir bilgi engeli ilkesi ayarladık. |

    Bu adımı her ilkeye uygun şekilde yinelayın.

3. Bilgi engeli ilkelerinizi etkin durum için ayarlamayı bitirdikten sonra, Güvenlik ve Uyumluluk Merkezi'nde **Start-InformationBarrierPoliciesApplication** cmdlet'ini & kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication`

    çalıştırdikten sonra `Start-InformationBarrierPoliciesApplication`, sistemin ilkeleri uygulamaya başlaması için 30 dakika kadar bekleyin. Sistem, kullanıcıya göre ilkeler uygular. Sistem, saatte yaklaşık 5.000 kullanıcı hesabını işler.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Kullanıcı hesaplarının, kesimlerin, ilkelerin veya ilke uygulamasının durumunu görüntüleme

PowerShell ile, aşağıdaki tabloda listelenen gibi kullanıcı hesaplarının, kesimlerin, ilkelerin ve ilke uygulamasının durumunu görüntüebilirsiniz.

| Bu bilgileri görüntülemek için | Bu eylemi benim 1 |
|:---------------|:----------|
| Kullanıcı hesapları | **Identity parametreleriyle Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın. <p> Söz dizimi: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her bir kişiyi benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. <p> Örnek: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Bu örnekte, Office 365'de iki kullanıcı hesabına başvururuz: *İbrhan için ayses* *ve* *Alex* *için alexw*. <p> (Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Bu cmdlet, öznitelik değerleri ve uygulanan herhangi bir bilgi engeli ilkeleri gibi kullanıcılarla ilgili bilgileri döndürür.|
| Kesimler | **Get-OrganizationSegment** cmdlet'ini kullanın.<p> Söz dizimi: `Get-OrganizationSegment` <p> Bu cmdlet, organizasyonunız için tanımlanmış tüm kesimlerin listesini görüntüler. |
| Bilgi engeli ilkeleri | **Get-InformationBarrierPolicy** cmdlet'ini kullanın. <p> Söz dizimi: `Get-InformationBarrierPolicy` <p> Bu cmdlet, tanımlanmış bilgi engeli ilkelerinin listesini ve bunların durumunu görüntüler. |
| En yeni bilgi engeli ilke uygulaması | **Get-InformationBarrierPoliciesApplicationStatus** cmdlet'ini kullanın. <p> Söz dizimi: `Get-InformationBarrierPoliciesApplicationStatus`<p> Bu cmdlet, ilke uygulamasının tamamlandıktan, başarısız veya devam eden bir durumla ilgili bilgileri görüntüler. |
| Tüm bilgi engeli ilke uygulamaları|Kullanım `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Bu cmdlet, ilke uygulamasının tamamlandıktan, başarısız veya devam eden bir durumla ilgili bilgileri görüntüler.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>İlkeleri kaldırmam veya değiştirmem gerekirse ne olur?

Bilgi engeli ilkelerinizi yönetmenize yardımcı olacak kaynaklara mevcuttur.

- Bilgi engelleriyle ilgili bir sorun olursa bilgi [engellerini giderme'ye bakın](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- İlkelerin uygulanmalarını durdurmak için bkz. [İlke uygulamasını durdurma](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Bilgi engeli ilkesi kaldırmak için bkz [. İlkeyi kaldırma](information-barriers-edit-segments-policies.md#remove-a-policy).
- Kesimlerde veya ilkelerde değişiklik yapmak için bkz. [Bilgi engeli ilkelerini düzenleme (veya kaldırma](information-barriers-edit-segments-policies.md)).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>5. Adım: İletişim ve eğitim SharePoint engellerini OneDrive

Bu hizmetlere ve hizmetlere SharePoint OneDrive engellerini yapılandırıyorsanız, bu hizmetlerle ilgili bilgi engellerini etkinleştirmeniz gerekir. Ayrıca, bu hizmetler için bilgi engellerini yapılandırıyorsanız, bu hizmetler için bilgi engellerini etkinleştirmeniz Microsoft Teams. Yeni Microsoft Teams ekip oluşturulduğunda, otomatik olarak SharePoint bir site oluşturulur ve dosyalar deneyimi Microsoft Teams ekiple ilişkilendirilz. Bu sitede ve dosyalarda varsayılan olarak bilgi engeli SharePoint ilkelerine bağlı değildir.

E-SharePoint OneDrive engellerini etkinleştirmek için, Bu makaledeki Bilgi engellerini kullanma makalesinde [SharePoint](/sharepoint/information-barriers) izleyin.

## <a name="step-6-information-barriers-modes"></a>6. Adım: Bilgi engelleri modları

Modlar, kaynağın IB moduna bağlı olarak bir kaynak Microsoft 365, paylaşımı ve üyeliği güçlendirmeye yardımcı olabilir. Modlar Grup, Microsoft 365, Microsoft Teams, OneDrive ve SharePoint etkinleştirilmiş durumdadır ve yeni veya var olan IB yapılandırmanız içinde otomatik olarak etkinleştirilir.

Aşağıdaki IB modları, kaynaklarda Microsoft 365 destekler:

| **Mod** | **Açıklama** | **Örnek** |
|:-----|:------------|:--------|
| **Aç** | Kaynakla ilişkilendirilmiş herhangi bir IB Microsoft 365 yok. Herkes kaynağın üyesi olmak için davet edilemez. | Organizasyonunız için piknik etkinliği için oluşturulmuş bir ekip sitesi. |
| **Owner Moderated (önizleme)** | Kaynakta yer alan Microsoft 365 IB ilkesi, kaynak sahibinin IB ilkesinden belirlenir. Kaynak sahipleri, IB ilkelerine göre herhangi bir kullanıcıyı kaynağa davet etmelerini sağlar. Bu mod, şirketin sahibi tarafından denetlenen uyumlu olmayan segment kullanıcıları arasında işbirliğine izin vermek istediği zaman yararlıdır. IB ilkesi başına yalnızca kaynak sahibi yeni üyeler ekleyebilir. | İk Başkan Yardımcısı Satış ve Araştırma temsilcileriyle işbirliği yapmak istiyor. Aynı siteye SharePoint Satış ve Araştırma segmenti kullanıcılarını eklemek için IB  modu Sahibi Ile ayarlanmış yeni bir müşteri merkezi sitesi. Kaynağa uygun üyelerin eklendiknden emin olmak, sahibin sorumluluğundadır. |
| **Örtülü** | Kaynakta yer alan IB Microsoft 365 bölümleri, kaynak üyeleri IB ilkesinden devralınan bir ilkedir. Sahibi, kaynağın var olan üyeleriyle uyumlu olduğu sürece üyeleri ekleyebilir. Bu, varsayılan IB modudur ve Microsoft Teams. | Satış segmenti kullanıcısı, Microsoft Teams uyumlu kesimlerle işbirliği yapmak üzere bir ekip oluşturur. |
| **Belirtik** | Kaynakla ilişkilendirilmiş Microsoft 365 BB ilkesi, kaynakla ilişkilendirilmiş olan kesimlere göredir. Kaynak sahibi veya SharePoint yöneticinin kaynak üzerinde kesimleri yönetme özelliği vardır.  | Yalnızca Satış segmenti üyeleri için, Satış segmentini siteyle bağimlı olarak birlikte kullanmaları için oluşturulmuş bir site.   |

Bilgi engeli modları ve bunların hizmetler genelinde nasıl yapılandırıldıları hakkında daha fazla bilgi için, aşağıdaki makalelere bakın:

- [Bilgi engelleri modları ve Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Bilgi engelleri modları ve OneDrive](/onedrive/information-barriers)
- [Bilgi engelleri modları ve SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Örnek senaryo: Contoso'nun bölümleri, kesimleri ve ilkeleri

Kuruluşun kesimleri ve ilkeleri tanımlama yaklaşımının nasıl olduğunu görmek için aşağıdaki örnek senaryoyu göz önünde bulundurabilirsiniz.

### <a name="contosos-departments-and-plan"></a>Contoso'nun departmanları ve planı

Contoso'da beş bölüm vardır: İk, Satış, Pazarlama, Araştırma ve Üretim. Endüstri düzenlemelerine uygun kalmak için, bazı departmanların kişileriyle aşağıdaki tabloda belirtilen şekilde başka departmanlarla iletişim kurmaları gerekir:

| Segment | Konuşarak | Konuşamaz |
|:----------|:--------------|:-----------------|
| İk | Herkes | (kısıtlama yok) |
| Satış | İk, Pazarlama, üretim | Araştırma |
| Pazarlama | Herkes | (kısıtlama yok) |
| Araştırma | İk, Pazarlama, üretim | Satış |
| İmalat | İk, Pazarlama | İk veya Pazarlama dışında herkes |

Bu yapı için, Contoso'nun planı üç bilgi engeli ilkeleri içerir:

1. Satış'ın Araştırma ile iletişim kurmasını engellemek için tasarlanmış bir ilke (ve Araştırma'nın Satışlarla iletişim kurmasını engellemek için başka bir ilke).

2. Üretim'in yalnızca İk ve Pazarlama ile iletişim kurmasını sağlayacak şekilde tasarlanmış bir ilke.

Bu senaryoda, İk veya Pazarlama için ilkeler tanımlamanız gerekmez.

### <a name="contosos-defined-segments"></a>Contoso'nun tanımlanmış kesimleri

Contoso, kesimleri tanımlamak için Azure Active Directory Department özniteliğini aşağıdaki gibi kullanır:

| Bölüm | Segment Tanımı |
|:-------------|:---------------------|
| İk | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Satış | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Pazarlama | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Araştırma | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| İmalat | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Tanımlı kesimlerle, Contoso ilkeler tanımlamaya devam eder.

### <a name="contosos-information-barrier-policies"></a>Contoso'nun bilgi engeli ilkeleri

Contoso, aşağıdaki tabloda açıklandığı gibi üç ilke tanımlar:

| İlke | İlke Tanımı |
|:---------|:--------------------|
| **İlke 1: Satışların Araştırma ile iletişim kurmasını engelleme** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Bu örnekte, bilgi engeli ilkesi *Satış-Araştırma olarak adlandırılan bir ilkedir*. Bu ilke etkin ve uygulandığında, Satış segmentinde yer alan kullanıcıların Araştırma segmentinde yer alan kullanıcılarla iletişim kurmasını engellemeye yardımcı olur. Bu ilke tek yol ilkedir; Araştırma'nın Satışlarla iletişim kurmasını engellemez. Bunun için, İlke 2 gereklidir. |
| **İlke 2: Araştırmanın Satışlarla iletişim kurmasını engelleme** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> Bu örnekte, bilgi engeli ilkesi *Araştırma-Satış olarak adlandırılan bir ilkedir*. Bu ilke etkin ve uygulandığında, Araştırma segmentinde yer alan kullanıcıların Satış segmentinde yer alan kullanıcılarla iletişim kurmasını engellemeye yardımcı olur. |
| **İlke 3: Üretim'in yalnızca İk ve Pazarlama ile iletişim kurmasına izin verme** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> Bu durumda, bilgi engeli ilkesi *Üretim-İkPazarlama olarak adlandırılan bir ilkedir*. Bu ilke etkin ve uygulandığında, Üretim yalnızca İk ve Pazarlama ile iletişim kurabilir. İk ve Pazarlama diğer kesimlerle iletişim kurma kısıtlaması değildir. |

Kesimler ve ilkeler tanımlandığı için, Contoso **başlangıç-informationBarrierPoliciesApplication** cmdlet'ini çalıştırarak ilkeleri uygular.

Cmdlet bitir olduğunda, Contoso yasal ve endüstri gereksinimleriyle uyumludur.

## <a name="resources"></a>Kaynaklar

- [Bilgi engellerine genel bir bakış elde edin](information-barriers.md)
- [Bu konuda bilgi engelleri hakkında daha fazla Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'daki bilgi engelleri hakkında daha fazla bilgi](/sharepoint/information-barriers)
- [Bu konuda bilgi engelleri hakkında daha fazla OneDrive](/onedrive/information-barriers)
