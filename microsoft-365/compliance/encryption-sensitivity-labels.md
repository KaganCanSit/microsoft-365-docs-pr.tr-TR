---
title: Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Erişimi ve kullanımı kısıtlaarak verilerinizi koruyan şifreleme için duyarlılık etiketlerini yapılandırabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2e337ef74975bd761de89b4aaae03379344efeed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311907"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Duyarlılık etiketi  oluşturduktan sonra, etiketin uygulanacak içeriklere erişimini kısıtabilirsiniz. Örneğin, bir duyarlılık etiketinin şifreleme ayarlarıyla içeriği koruyarak şunları yapabilirsiniz:

- Yalnızca kuruluş içindeki kullanıcılar gizli bir belgeyi veya e-postayı açabilir.
- Yalnızca pazarlama departmanında yer alan kullanıcılar promosyon duyurusu belgesini veya e-postasını düzenleyebilir ve yazdırabilirsiniz; öte yandan, organizasyonu kullanan diğer tüm kullanıcılar bu belgeyi yalnızca okuyabilir.
- Kullanıcılar, şirket içi bir yeniden düzenlemeyle ilgili haberleri içeren e-postayı iletamaz veya bilgileri kopyaamaz.
- İş ortaklarına gönderilen geçerli fiyat listesi, belirtilen tarihten sonra açılamıyor.

Belge veya e-posta şifrelenirken içeriğe erişim kısıtlanır; böylelikle:

- Şifreleri yalnızca etiketin şifreleme ayarları tarafından yetkilendirilmiş kullanıcılar tarafından çözülebilirsiniz.
- Dosya yeniden adlandırılmış olsa bile, nerede olursa olsun, kuruluş içinde veya dışında şifrelenmiş olarak kalır.
- Hem rest rest (örneğin, bir OneDrive hesabında) hem de iletili olarak (örneğin, İnternet'e çapraz geçişte e-posta) şifrelenir.

Son olarak, yönetici olarak şifreleme uygulamak üzere bir duyarlılık etiketi yapılandırıldığında şunların için birini seçebilirsiniz:

- **Bu etiketle** hangi kullanıcıların hangi içeriğe sahip olduğunu tam olarak belirlemek için şimdi izinleri attayabilirsiniz.
- **Kullanıcıların, etiketi içeriğe** uygulayabilecekleri izinler atamasına izin verin. Bu şekilde, organizasyon durumdaki kişilerin işbirliği yapmaları ve çalışmalarını yapmaları için ihtiyaçları bazı esneklikler de olabilir.

Şifreleme ayarları, dosya sayfasında [bir duyarlılık Microsoft 365 uyumluluk merkezi](create-sensitivity-labels.md). Eski portalı, Güvenlik ve Uyumluluk Merkezi'& de kullanabilirsiniz.

## <a name="understand-how-the-encryption-works"></a>Şifrelemenin nasıl çalıştığını anlama

Şifreleme, Azure Information Protection'dan Azure Rights Management hizmetini (Azure RMS) kullanır. Bu koruma çözümü şifreleme, kimlik ve yetkilendirme ilkelerini kullanır. Daha fazla bilgi edinmek için Azure [Information Protection belgelerinden Azure Hak](/azure/information-protection/what-is-azure-rms) Yönetimi nedir? belgesine bakın. 

Bu şifreleme çözümünü kullanırken, süper kullanıcı  özelliği yetkili kişilerin ve hizmetlerin, kurum için şifrelenmiş verileri her zaman okumalarını ve inceleymesini sağlar. Gerekirse şifreleme kaldırılabilir veya değiştirilebilir. Daha fazla bilgi için bkz. [Azure Information Protection ve keşif hizmetleri veya veri kurtarma için süper kullanıcıları yapılandırma](/azure/information-protection/configure-super-users).

## <a name="important-prerequisites"></a>Önemli önkoşullar

Şifrelemeyi kullanamadan önce bazı yapılandırma görevlerini gerçekleştirmeniz gerekir. Şifreleme ayarlarını yapılandırıldığında, bu önkoşulların karşılanmış olduğunu doğrulamak için denetim olmaz.

- Azure Information Protection'dan korumayı etkinleştirme
    
    Duyarlılık etiketlerinin şifreleme uygulayması için, Azure Information Protection'dan alınan koruma hizmetinin (Azure Rights Management) kiracınız için etkinleştirilmesi gerekir. Daha yeni kiracılarda, bu varsayılan ayardır, ancak hizmeti el ile etkinleştirmeniz gerekebilir. Daha fazla bilgi için bkz [. Azure Information Protection'dan koruma hizmetini etkinleştirme](/azure/information-protection/activate-service).

- Ağ gereksinimlerini denetleme
    
    Güvenlik duvarları gibi ağ cihazlarınız üzerinde bazı değişiklikler yapmak zorundayabilirsiniz. Ayrıntılar için Azure Information Protection [belgelerinden Güvenlik duvarları](/azure/information-protection/requirements#firewalls-and-network-infrastructure) ve ağ altyapısına bakın.

- Azure Information Protection Exchange'yi yapılandırma
    
    Exchange e-postalarını şifrelemek için kullanıcıların Azure Information Protection'da etiketler uygulayamadan önce Outlook yapılandırılması gerekir. Bununla birlikte, Exchange Azure Information Protection için yapılandırılana kadar, güvenlik özellikleriyle birlikte Azure Hak Yönetimi korumasını kullanma Exchange.
    
    Örneğin, kullanıcılar cep telefonlarında veya Web üzerinde Outlook'da şifrelenmiş e-postaları görüntüleyememektedir, arama için şifrelenmiş e-postalar dizine Exchange Online hakların korunması için DLP'yi yapılandıramazsınız. 
    
    Bu ek Exchange destekleyene emin olmak için, aşağıdakilere bakın:
    
    - Daha Exchange Online için şu yönergelere bakın[: Exchange Online: IRM Yapılandırması](/azure/information-protection/configure-office365#exchangeonline-irm-configuration).
    - Şirket Exchange için, RMS bağlayıcısı dağıtmalı ve [Exchange yapılandırmanız gerekir](/azure/information-protection/deploy-rms-connector). 

## <a name="how-to-configure-a-label-for-encryption"></a>Şifreleme için etiket yapılandırma

1. Duyarlılık etiketi oluşturmak veya [düzenlemek için genel](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) yönergeleri izleyin ve etiketin **kapsamına göre & e-postalarla** dosyalar'ın seçili olduğundan emin olun: 
    
    ![Dosyalar ve e-postalar için duyarlılık etiketi kapsamı seçenekleri.](../media/filesandemails-scope-options-sensitivity-label.png)

2. Ardından, Dosyalar ve **e-postalar için koruma ayarlarını seçin** sayfasında Dosyaları ve e-postaları **şifrele'yi seçmeyi seçin.**
    
    ![Dosyalar ve e-postalar için duyarlılık etiketleri koruma seçenekleri.](../media/protection-options-sensitivity-label.png)

4.  Şifreleme **sayfasında** aşağıdaki seçeneklerden birini belirleyin:
    
    - **Dosya şifrelenirse şifrelemeyi kaldır**: Bu seçenek yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından destekler. Bu seçeneği belirterek yerleşik etiketlemeyi kullanmayı tercih ediyorsanız, etiket uygulamalarda görüntülenmeyebilirsiniz veya herhangi bir şifreleme değişikliği yapmayabilirsiniz.
        
        Bu senaryo hakkında daha fazla bilgi için, Bir etiket uygulandığında var olan [şifrelemeye ne olur? bölümüne](#what-happens-to-existing-encryption-when-a-labels-applied) bakın. Bu ayarın, kullanıcıların yeterli izinlere sahip değilken uygulayamayabilecek bir duyarlılık etiketine neden olabileceğini anlamanız önemlidir.
    
    - **Şifreleme ayarlarını yapılandırma**: Şifrelemeyi ayarlar ve şunları görünür hale gelir:
        
        ![Şifreleme için duyarlılık etiketi seçenekleri.](../media/encrytion-options-sensitivity-label.png)
        
        Bu ayarlara ilişkin yönergeler, şifreleme ayarlarını [yapılandırma bölümünde](#configure-encryption-settings) yer almaktadır.

### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Bir etiket uygulandığında mevcut şifrelemeye ne olur?

Şifrelenmemiş içeriğe bir duyarlılık etiketi uygulanırsa, seçebilirsiniz şifreleme seçeneklerinin sonucu açıklayıcı olur. Örneğin, Dosyaları ve e-postaları **şifrele'yi seçmemişsanız**, içerik şifrelenmemiş olarak kalır.

Bununla birlikte, içerik zaten şifrelenmiş olabilir. Örneğin, başka bir kullanıcı şunları uygulanmış olabilir:

- Bir etiket tarafından istendiğinde kullanıcı tanımlı izinlerin, Azure Information Protection istemcisinin özel izinlerinin ve bir belgenin içinde Sınırlı **Erişim** belge korumasının yer Office uygulaması.
- İçeriği etiketten bağımsız olarak şifrelenen bir Azure Hak Yönetimi koruma şablonu. Bu kategori, hak korumasını kullanarak şifreleme uygulayan posta akışı kurallarını içerir.
- Yönetici tarafından atanan izinlere sahip şifrelemeyi uygulanan etiket.

Aşağıdaki tablo, bir duyarlılık etiketi bu içeriğe uygulandığında var olan şifrelemeye ne olacağını tanımlar:

| | Şifreleme: Seçili değil | Şifreleme: Yapılandırıldı | Şifreleme: Kaldırma <sup>\*</sup> |
|:-----|:-----|:-----|:-----|
|**Kullanıcı tarafından belirtilen izinler**|Özgün şifreleme korunur|Yeni etiket şifrelemesi uygulanır|Özgün şifreleme kaldırıldı|
|**Koruma şablonu**|Özgün şifreleme korunur|Yeni etiket şifrelemesi uygulanır|Özgün şifreleme kaldırıldı|
|**Yönetici tanımlı izinlere sahip etiket**|Özgün şifreleme kaldırıldı|Yeni etiket şifrelemesi uygulanır|Özgün şifreleme kaldırıldı|

**Dipnot:**

<sup>\*</sup> Yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenen

Yeni etiket şifrelemenin uygulandığı veya özgün şifrelemenin kaldırıldığı durumlarda, bu durum ancak etiketi uygulama kullanıcısında bu eylemi destekleyen bir kullanım hakkı veya rolü olduğunda gerçekleşir:

- Kullanım [sağ Dışarı](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Aktar veya Tam Denetim.
- Hak Yönetimi konusunda [yönetici veya Hak Yönetimi sahibi ya da](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) süper [kullanıcı rolü](/azure/information-protection/configure-super-users).

Kullanıcının bu hak ve rollerden biri yoksa, etiket uygulanamaz ve böylelikle özgün şifreleme korunur. Kullanıcı aşağıdaki iletiyi görür: **Duyarlılık etiketinde bu değişikliği yapma izniniz yok. Lütfen içerik sahibine ulaşın.**

Örneğin, e-posta iletisine İletin'i iletme'ye uygulanan kişi, e-postanın Hak Yönetimi sahibi olduğundan, şifrelemeyi değiştirmek veya kaldırmak için iş parçacığını yeniden etiketl olabilir. Ancak süper kullanıcılar dışında, bu e-postanın alıcıları gerekli kullanım haklarına sahip değilkleriyle bu e-postayı yeniden etiketleyemmektedir.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Şifreli e-posta iletileri için e-posta ekleri

E-posta iletisi herhangi bir yöntem tarafından şifrelenirken, şifrelenmemiş tüm belgeler Office e-postaya eklenen tüm belgeler otomatik olarak aynı şifreleme ayarlarını devralabilir.

Zaten şifrelenmiş olan ve ek olarak eklenen belgeler her zaman özgün şifrelemelerini korur.

## <a name="configure-encryption-settings"></a>Şifreleme ayarlarını yapılandırma

Duyarlılık etiketi **oluşturmak veya düzenlemek için** **Şifreleme** sayfasında Şifreleme ayarlarını yapılandır'ı seçerseniz, aşağıdaki seçeneklerden birini belirleyin:

- **Şimdi izinleri atarak** tam olarak hangi kullanıcıların etiket uygulanmış olan içeriğe hangi izinleri ataytayabilirsiniz. Daha fazla bilgi için bir sonraki İzinleri şimdi [atama bölümüne bakın](#assign-permissions-now).
- **Kullanıcılarınız etiketi içeriğe** uygulayana kadar kullanıcıların izinler atamasına izin verin. Bu seçenekle, organizasyonu ziyaret etmek istediğiniz kişilerin işbirliği yapmaları ve çalışmalarını yapmaları için ihtiyaçları olacak bir esneklik sabilirsiniz. Daha fazla bilgi için Bu [sayfada Kullanıcıların izin atamasına izin](#let-users-assign-permissions) verme bölümüne bakın.

Örneğin, en hassas içeriğinize uygulanacak olan Çok Gizli adlı  bir duyarlılık etiketiniz varsa, bu içerik üzerinde ne tür izinlere sahip olduğuna şimdi karar vermek istiyor olabilirsiniz.

Alternatif olarak, İş Sözleşmeleri adlı bir duyarlılık etiketiniz varsa ve iş akışında kişilerinin bu içerik üzerinde özel olarak birlikte çalışmalarını gerektiriyorsa, kullanıcılarınızı etiket atadığınız zaman kimlerin izinlere sahip olduğuna karar vermelerine izin vermek istiyorabilirsiniz. Bu esneklik hem kullanıcılarının üretkenliğine yardımcı olur hem de yöneticilerinizin belirli senaryolara yönelik olarak güncelleştirilme veya yeni duyarlılık etiketleri oluşturma isteklerini azaltır.

şimdi izin atamayı veya kullanıcıların izin atamasına izin ver'i seçme:

![Kullanıcı veya yönetici tanımlı izin ekleme seçeneği.](../media/sensitivity-label-user-or-admin-defined-permissions.png)

## <a name="assign-permissions-now"></a>İzinleri şimdi ata

Bu etiketin uygulandığı e-postaya veya belgelere kimlerin eriş erişeni kontrol etmek için aşağıdaki seçenekleri kullanın. Şunları yapabilirsiniz:

- **Etiketli içeriğe erişimin belirli bir** tarihte veya etiket uygulandıktan belirli sayıda gün sonra sona erer. Bu sürenin ardından, kullanıcılar etiketli öğeyi açabilecektir. Bir tarih belirtirsanız, geçerli saat diliminde o tarihin üzerinde etkin bir gece yarısı olur. (Önbelleğe alma mekanizmaları nedeniyle bazı e-posta istemcilerinin süre dolmayı zorunlu hale gösterip son kullanma tarihini geçmiş e-postaları göstereylenene dikkat edin.)

- **Etiket uygulandıktan** sonra hiçbir zaman, her zaman veya belirli sayıda gün boyunca çevrimdışı erişime izin verme. Çevrimdışı erişimi hiçbir zaman veya gün sayısıyla kısıtlarsanız, eşiklere ulaşıldıysa kullanıcıların yeniden kimlik doğrulaması ve erişimleri günlüğe kaydedilir. Daha fazla bilgi için, Hak Yönetimi kullanım lisansının bir sonraki bölümüne bakın.

Ayarlar şifreli içerik için erişim denetimine erişim izni:

![Ayarlar tanımlı izinler için izinler.](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

### <a name="rights-management-use-license-for-offline-access"></a>Çevrimdışı erişim için Hak Yönetimi kullanım lisansı

Kullanıcı, Azure Rights Management hizmetinin şifrelemesi ile korunan bir belgeyi veya e-postayı açtığında, kullanıcıya bu içerik için bir Azure Hak Yönetimi kullanım lisansı velenir. Bu kullanım lisansı, kullanıcının belge veya e-postayla ilgili kullanım haklarını ve içeriği şifrelemek için kullanılan şifreleme anahtarını içeren bir sertifikadır. Ayrıca kullanım lisansı, ayarlanmışsa bir son kullanma tarihi ve kullanım lisansının ne kadar süreyle geçerli olduğunu da içerir.

Son kullanma tarihi ayarlanamıyorsa, kiracı için varsayılan kullanım lisansı geçerlilik süresi 30 gündür. Kullanım lisansı süresi boyunca, kullanıcının kimliği yeniden doğrulanmaz veya içerik için yeniden doğrulanmaz. Bu işlem, kullanıcının korumalı belgeyi veya e-postayı İnternet bağlantısı olmadan açmaya devam ettiğine olanak sağlar. Kullanım lisansı geçerlilik süresi sona erdiğinde, kullanıcının korumalı belgeye veya e-postaya bir sonraki erişdiğinde, kullanıcının yeniden kimlik doğrulaması ve yeniden yetkilendirmesi gerekir.

Yeniden kimlik doğrulamasına ek olarak, şifreleme ayarları ve kullanıcı grubu üyeliği de yeniden değerlendirebilirsiniz. Bu, şifreleme ayarlarında veya grup üyeliğinde içeriğe son erişilmelerinden sonra gelen değişiklikler olduğunda, kullanıcıların aynı belge veya e-posta için farklı erişim sonuçları elde e-postası ile karşınıza çıka kolayca erişemelerini sağlar.

Varsayılan 30 günlük ayarın nasıl değiştiri olduğunu öğrenmek için bkz. [Hak Yönetimi kullanım lisansı](/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Belirli kullanıcılara veya gruplara izin atama

Belirli kullanıcılara izinler ve böylelikle yalnızca o kişilerin etiketli içerikle etkileşimde bulunarak etkileşimde bulunabilirsiniz:

1. İlk olarak, etiketli içeriğe izin atanacak kullanıcıları veya grupları ekleyin.

2. Ardından, etiketli içerik için bu kullanıcıların hangi izinlere sahip olması gerektiğini seçin.

İzinleri atama:

![Kullanıcılara izin atama seçenekleri.](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Kullanıcı veya grup ekleme

İzinleri atarken şunları seçebilirsiniz:

- Herkes, kuruluşta (tüm kiracı üyeleri). Bu ayar konuk hesaplarını dışlar.

- Kimliği doğrulanmış tüm kullanıcılar. Bu ayarı seçmeden önce [gereksinimlerini ve sınırlamalarını](#requirements-and-limitations-for-add-any-authenticated-users) anlıyoruz.

- Azure AD'de belirli kullanıcı veya e-posta etkin güvenlik Microsoft 365, dağıtım grubu veya [Microsoft 365 grubu (Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601) grubu) olabilir. Grup Microsoft 365 statik veya dinamik [üyelikleri olabilir](/azure/active-directory/users-groups-roles/groups-create-rule). bu grup türü Azure AD ile eşitlenmedi ve e-posta etkin olmayan bir güvenlik grubu kullanamaylarından dolayı [Exchange'tan](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups) dinamik dağıtım grubu kullanamayabilirsiniz.
    
    Bu seçenek için desteklenen belirtilen bir grup içinde, şifrelenmiş içeriği açmadan önce [](/azure/information-protection/prepare#azure-information-protection-requirements-for-user-accounts) her kullanıcının kimliği Azure Information Protection hizmeti tarafından tek tek doğrulanır.

- Herhangi bir e-posta adresi veya etki alanı. Bu seçeneği, başka bir kuruluşta Azure AD kullanan tüm kullanıcıları belirtmek için o kuruluştan herhangi bir etki alanı adı girerek belirtin. Bu seçeneği, sosyal sağlayıcılar için ad, etki alanı adı veya posta **gmail.com hotmail.com girerek** **outlook.com**. 

    > [!NOTE]
    > Azure AD kullanan bir kuruluşa yönelik bir etki alanı belirtirsanız, erişimi belirli bir etki alanına kısıtlayamabilirsiniz. Bunun yerine, Azure AD'de tüm doğrulanmış etki alanları, belirttiğiniz etki alanı adının sahibi olan kiracıya otomatik olarak eklenir.

Kuruluşta tüm kullanıcıları ve grupları seçerseniz veya dizine göz atsanız, kullanıcıların veya grupların bir e-posta adresi olmalıdır.

En iyi uygulama olarak, kullanıcıları değil grupları kullanın. Bu strateji yapılandırmanızı daha basit tutar.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>"Kimliği doğrulanmış kullanıcıları ekleme" gereksinimleri ve sınırlamaları

Bu ayar, bir yandan içeriği şifrelerken diğer yandan içeriği şifrelerken ve içeriği nasıl kullanılasını (izinler) ve erişilebilirliği (süre dolması ve çevrimdışı erişim) kısıtlama seçenekleri sağlarken, kimlerin içeriği şifreley içeriğe eriş ulaşamaz olacağını kısıtlamaz. Ancak, şifrelenmiş içeriği açılan uygulamanın kimlik doğrulamasının kullanılasını desteklemesi gerekir. Bu nedenle, Google gibi federasyon sosyal sağlayıcıları ve tek kullanımlı geçiş kodu kimlik doğrulaması yalnızca e-postada ve bu hizmette yalnızca sizin Exchange Online. Microsoft hesapları, diğer uygulamalarla Office 365 [Azure Information Protection görüntüleyicisi ile kullanılabilir](https://portal.azurerms.com/#/download).

> [!NOTE]
> duyarlılık etiketleri SharePoint ve OneDrive dosyaları için duyarlılık etiketleri etkinleştirildiğinde[, bu ayarı Azure AD B2 Office B](/sharepoint/sharepoint-azureb2b-integration-preview) ile SharePoint ve SharePoint tümleştirmesinde [OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Kimliği doğrulanmış herhangi bir kullanıcı ayarı için bazı tipik senaryolar:

- İçeriği kimin görüntülemesi önemli değildir, ancak nasıl kullanıla birlikte kısıtlayalın. Örneğin, içeriğin düzenlenemez, kopyalanır veya yazdırılmaz.
- İçeriklere kimlerin eriş erişeni kısıtlamanız gerek değildir, ancak içeriği kimlerin açtığını onaylayabilirsiniz.
- İçeriğin ilerlerken ve iletilirken şifreleniyor olması gerekir, ancak erişim denetimleri gerektirmez.

#### <a name="choose-permissions"></a>İzinleri seçin

Bu kullanıcılara veya gruplara izin vermek istediğiniz izinleri seçerseniz:

- Kaynak [veya Gözden Geçiren gibi](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) önceden tanımlı bir hak grubuyla önceden Co-Author düzeyi.
- Bir veya birden çok kullanım hakkı seçtiğiniz özel izinler.

Uygun izinleri seçmenize yardımcı olacak daha fazla bilgi için bkz. [Kullanım hakları ve açıklamaları](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Önceden ayarlanmış veya özel izinleri seçme seçenekleri.](../media/Sensitivity-Choose-permissions-settings.png)

Aynı etiketin farklı kullanıcılara farklı izinler verey olduğunu unutmayın. Örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi, tek bir etiket bazı kullanıcıları Gözden Geçiren veya Ortak Yazar olarak başka bir kullanıcı atayabilirsiniz.

Bunu yapmak için kullanıcıları veya grupları ekleyin, onlara izin verin ve bu ayarları kaydedin. Ardından, kullanıcıları ekleyerek ve onlara izinler ataarak ayarları her zaman kaydederek bu adımları yinelayın. Farklı kullanıcılar için farklı izinler tanımlamak üzere bu yapılandırmayı gerektiğinde yinelersiniz.

![Farklı izinleri olan farklı kullanıcılar.](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>Hak Yönetimi konusunda (kullanıcı duyarlılık etiketini uygulamalı) her zaman Tam Denetim'e sahip olur

Duyarlılık etiketinin şifrelemesi, Azure Information Protection'dan Azure Rights Management hizmetini kullanır. Kullanıcı şifreleme kullanarak belgeyi veya e-postayı korumak için bir duyarlılık etiketi uygularsa, bu kullanıcı bu içerik için Hak Yönetimi'nin vericisi olur.

Hak Yönetimi ile ilgili olarak, belge veya e-posta üzerinde her zaman Tam Denetim izinleri ve ayrıca:

- Şifreleme ayarlarının son kullanma tarihi varsa, Hak Yönetimi ile ilgili olarak, ilgili tarihten sonra da belgeyi veya e-postayı açabilir ve düzenleyebilir.
- Hak Yönetimi ile ilgili olarak, belgeye veya e-postaya her zaman çevrimdışı olarak erişebilirsiniz.
- Hak Yönetimi ile ilgili olarak, belge iptal edildikten sonra da açabilirsiniz.

Daha fazla bilgi için bkz [. Hak Yönetimi sahibi ve Hak Yönetimi sahibi](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

### <a name="double-key-encryption"></a>Çift Anahtar Şifrelemesi

> [!NOTE]
> Bu özellik şu anda yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenmiş durumdadır.

Bu seçeneği yalnızca Çift Anahtar Şifreleme hizmetini yapılandırdıktan ve bu etiketin uygulandığı dosyalar için bu çift anahtar şifrelemeyi kullanmalıdır.

Daha fazla bilgi, önkoşullar ve yapılandırma yönergeleri için bkz. [Çift Anahtar Şifrelemesi (DKE)](double-key-encryption.md).

## <a name="let-users-assign-permissions"></a>Kullanıcıların izin atamasına izin ver

> [!IMPORTANT]
> Etiket istemcilerinin hepsi, kullanıcıların kendi izinlerini atamasına izin verilen tüm seçenekleri desteklemez. Daha fazla bilgi edinmek için bu bölümü kullanın.

Aşağıdaki seçenekleri kullanarak, kullanıcıların içeriğe el ile bir duyarlılık etiketi uygulamalarına izinler atamalarına izin veebilirsiniz:

- Bu Outlook, kullanıcı "İleri iletme" seçeneğiyle eşdeğer kısıtlamaları veya Seçili alıcıları [](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) [için](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails) Yalnızca şifrele seçeneğini kullanabilir.
    
    The Do Not Forward option is supported by all email clients that supporty labels. Bununla birlikte, Duyarlılık **etiketiyle** Yalnızca Şifrele seçeneğinin uygulanması, Azure Information Protection birleşik etiketleme istemcisi tarafından değil, yalnızca yerleşik etiketleme tarafından desteklenen yeni bir sürümdir. Bu özelliği desteklemeen e-posta istemcileri için etiket görünmez.
    
    Yerleşik etiketleme kullanan Outlook uygulamalarının duyarlılık etiketiyle birlikte Encrypt-Only seçeneğinin uygulanmasına destek olan minimum sürümlerini kontrol etmek için Outlook'un özellikler tablosu ve [Kullanıcıların](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-outlook) izin atamasına izin ver **: - Encrypt-Only** satırı kullanın.

- Word, PowerPoint ve Excel'de, bir kullanıcıdan belirli kullanıcılar, gruplar veya kuruluşlar için kendi izinlerini seçmesi istenir.

    Bu seçenek Azure Information Protection birleşik etiketleme istemcisi ve yerleşik etiketleme kullanan bazı uygulamalar tarafından destekler. Bu özelliği desteklemeen uygulamalarda etiket kullanıcılar tarafından görülmeyebilir veya tutarlılık için görünür ancak kullanıcılara bir açıklama iletisiyle uygulanameyebilir.
    
    Yerleşik etiketleme kullanan uygulamaları kontrol etmek için bu seçeneği destekleyen [Word, Excel](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) ve PowerPoint özellikler tablosu ile kullanıcıların izin atamasına izin ver **: -** Kullanıcılara sor satırlarını kullanın.

Seçenekler desteklenmişken, kullanıcıların duyarlılık etiketini ne zaman göreceğini belirlemek için aşağıdaki tabloyu kullanın:

|Ayar |Etiket, Outlook'de görünür|Word, Excel, PowerPoint'de görünen PowerPoint|
|:-----|:-----|:-----|:-----|
|**Daha Outlook'te, İleri Veya İleri'ye Encrypt-Only seçeneğiyle kısıtlamaları zorunlu Encrypt-Only yapma**|Evet |Hayır |
|**Word, PowerPoint ve Excel'de kullanıcılardan izinleri belirtmelerini istenir**|Hayır |Evet|

Her iki ayar da seçildiğinde, etiket hem Word'de hem de Outlook, Excel ve PowerPoint.

Kullanıcıların izin atamalarını sağlayan bir duyarlılık etiketi kullanıcılar tarafından içeriğe el ile uygulanmalıdır; otomatik olarak uygulanamayacak veya önerilen etiket olarak kullanılamaz.

Kullanıcıya atanan izinleri yapılandırma:

![Kullanıcı tanımlı izinler için şifreleme ayarları.](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>Outlook kısıtlamalarını

Daha Outlook'de, kullanıcı bir iletiye izinler atamalarına olanak sağlayan bir duyarlılık etiketi uygularsa, İletiyle seçeneğini veya Yalnızca  **Şifrele'yi seçebilirsiniz**. Kullanıcı iletinin en üstünde etiket adını ve açıklamasını görebilir ve bu da içeriğin korunmaktadır olduğunu gösterir. Word, PowerPoint ve Excel'den farklı olarak (sonraki bölüme [bakın),](#word-powerpoint-and-excel-permissions) kullanıcılardan belirli izinleri seçmeleri istenz.

![metinde iletiye uygulanan duyarlılık Outlook.](../media/sensitivity-label-outlook-protection-applied.png)

E-postaya bu seçeneklerden biri uygulandığında, e-posta şifrelenir ve alıcıların kimlik doğrulaması gerekir. Ardından, alıcıların kullanım hakları otomatik olarak kısıtlanır:

- **Gönderme:** Alıcılar e-postayı iletamaz, yazdıramaz veya kopyalayıp samaz. Örneğin, Outlook istemcisinde İleri düğmesi kullanılamaz, Farklı Kaydet ve Yazdır menü seçenekleri kullanılamaz ve Yeni, Bilgi veya Gizli kutularına alıcı ekamaz veya bu seçenekleri değiştiremezsiniz.
    
    Bu seçeneğin nasıl olduğu hakkında daha fazla bilgi için bkz. [E-postalar için seçeneği iletme](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails).

- **Yalnızca Şifrele**: Alıcılar Farklı Kaydet, Dışarı Aktar ve Tam Denetim dışında tüm kullanım haklarına sahip olur. Kullanım haklarının bu bileşimi, alıcıların korumayı kaldıramazları dışında hiçbir kısıtlaması olmadığını gösterir. Örneğin, alıcı e-postadan kopyalayıp yazdırarak iletebilirsiniz.
    
    Bu seçeneğin nasıl olduğu hakkında daha fazla bilgi için bkz [. E-postalar için yalnızca şifrele seçeneği](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails).

Şifrelenmemiş Office e-postaya eklenmiş belgeler aynı kısıtlamaları otomatik olarak devralabilir. Bu belgelere uygulanan kullanım hakları, İçeriği Düzenleme, Düzenleme'yi içerir. Kaydet; Görüntüleme, Açma, Okuma; ve Makrolara İzin Ver'i tıklatın. Kullanıcı ek için farklı kullanım hakları istiyorsa veya ek, bu devralınan korumayı destekleyen bir Office belgesi yoksa, kullanıcının e-postaya eklemeden önce dosyayı şifrelemesi gerekir.

### <a name="word-powerpoint-and-excel-permissions"></a>Word, PowerPoint ve Excel izinlerini değiştirme

Word, PowerPoint ve Excel'da, kullanıcı belgeye izin atamalarına olanak sağlayan bir duyarlılık etiketi uygularsa, şifreleme uygulandığında kullanıcı ve izin tercihlerini belirtmeleri istenir.

Örneğin, birlikte yazma etkinleştirilmediği sürece Azure Information Protection birleşik etiketleme [istemcisini kullanan](sensitivity-labels-coauthoring.md) kullanıcılar şunları şunları olabilir:

- Görüntüleyici (Yalnızca Görüntüleme izni ataan) veya Görünüm, Düzenleme, Kopyalama ve Yazdırma Co-Author izinlerini ataan izin düzeyini seçin.
- Kullanıcıları, grupları veya kuruluşları seçin. Bu, hem kuruluş içindeki hem de dışındaki kişiler içerebilir.
- Son kullanma tarihi ayarlayın; bundan sonra seçilen kullanıcılar içeriğe erişemayacaktır. Daha fazla bilgi için yukarıdaki Çevrimdışı erişim için [Hak Yönetimi kullanım lisansı bölümüne bakın](#rights-management-use-license-for-offline-access).

![Kullanıcıya özel izinlerle koruma seçenekleri.](../media/sensitivity-aip-custom-permissions-dialog.png)

Yerleşik etiketleme için ve birlikte yazma etkinleştirildiğinde Azure Information Protection birleşik etiketleme istemcisi [için, kullanıcılar](sensitivity-labels-coauthoring.md) aşağıdakini seçtikleri gibi aynı iletişim kutusunu görebilirler:

- Windows: **InfoProtect** **>'de** >  Dosya **sekmesiRestrict** >  Erişimi  > **Kısıtlanmış Erişimi**

- macOS: **Gözden Geçir** sekmesi > **ProtectionPermissionsRestricted** >  >  **Access**

> [!TIP]
> Birlikte yazma etkinleştirilmeden önce kullanıcılar Azure Information Protection birleşik etiketleme istemcisiyle özel izinler yapılandırmayı biliyorsa [, izin](sensitivity-labels-coauthoring.md) düzeylerini tek tek kullanım haklarıyla eşlemeyi gözden geçirmeyi yararlı bulabilirsiniz: İzin düzeylerine dahil edilen [haklar](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

## <a name="example-configurations-for-the-encryption-settings"></a>Şifreleme ayarları için örnek yapılandırmalar

Aşağıdaki her örnekte, Şifreleme ayarlarını yapılandır seçildiğinde **şifreleme** **sayfasından yapılandırmayı** yapın:

![Duyarlılık etiketi sihirbazında Şifrelemeyi uygula seçeneği.](../media/apply-encryption-option.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-an-encrypted-email-to-a-gmail-account"></a>Örnek 1: Gmail hesabına şifreli bir e-posta göndermek için 'İleri'ye iletme' etiketinin uygulandığı etiket

Bu etiket yalnızca Outlook ve Web üzerinde Outlook olarak görüntülenir ve Exchange Online. Gmail hesabı (veya kuruluş dışındaki başka herhangi bir e-posta hesabı) kullanan kullanıcılara şifreli bir e-posta göndermeleri gereken kullanıcılardan bu etiketi seçmelerini sorun.

Kullanıcılarınız, Son kutusuna Gmail e-posta **adresini** yazın.  Ardından etiketi seçerler ve E-postaya otomatik olarak Iletme seçeneği eklenir. Sonuçta, alıcıların Farklı Kaydet seçeneğini kullanarak e-postayı ilete almaları, yazdırmalarına, kopyalamalarına veya posta kutularının dışında **kaydetmelerine neden** olur.

1. Şifreleme sayfasında **: İzinleri** şimdi ata **veya kullanıcıların karar vermesine** izin ve ver? için, Kullanıcıların etiketi uygulayabilecekleri **izinleri atamasına izin ver'i seçin**.

2. Onay kutusunu seçin: **Outlook iletme seçeneğiyle eşdeğer kısıtlamaları zorunlu kılın.**

3. Seçiliyse, onay kutusunu temizleyin: **Word'de, PowerPoint ve Excel izinlerini belirtmelerini isten.**

4. **Sonraki'yi** seçin ve yapılandırmayı tamamlama.

### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization"></a>Örnek 2: Başka bir kuruluşta tüm kullanıcılar için salt okunur izni kısıtlayan etiket

Bu etiket çok hassas belgeleri salt okunur olarak paylaşmak için uygundur ve bu belgeleri görüntülemek için her zaman İnternet bağlantısı gerekir.

Bu etiket e-postalar için uygun değil.

1. Şifreleme sayfasında **: İzinleri** şimdi ata **veya kullanıcıların karar vermesine izin ve ver? için İzinleri** şimdi **ata'ya tıklayın**.

2. Çevrimdışı **erişime izin ver için Hiçbir** **zaman'ı seçin**.

3. İzinleri **ata'ya tıklayın**.

4. İzinleri **ata bölmesinde Belirli** e-posta **adreslerini veya etki alanlarını ekle'yi seçin**.

5. Metin kutusuna, diğer kuruluştan bir etki alanının adını girin; **örneğin, fabrikam.com**. Ardından **Ekle'yi seçin**.

6. İzinleri **seç'i seçin**.

7. İzinleri **seçin bölmesinde** açılan kutuyu seçin, Görüntüleyici'yi **seçin ve** sonra da Kaydet'i **seçin**.

8. İzinleri Ata **bölmesine dönüp** Kaydet'i **seçin**.

9. Şifreleme sayfasında **Sonraki'yi** **seçin ve** yapılandırmayı tamamlayın.

### <a name="example-3-add-external-users-to-an-existing-label-that-encrypts-content"></a>Örnek 3: var olan içeriği şifreen bir etikete dış kullanıcılar ekleme

Ekley istediğiniz yeni kullanıcılar, daha önce bu etiketle korunmuş olan belgeleri ve e-postaları açabilir. Bu kullanıcılara vermekte olduğu izinler, var olan kullanıcıların sahip olduğu izinlerden farklı olabilir.

1. Şifreleme sayfasında **: İzinleri** şimdi **ata veya kullanıcıların karar vermesine izin ver? şimdi** izinleri **ata'nın seçili olduğundan** emin olun.

2. İzinleri **ata'ya tıklayın**.

3. İzinleri **ata bölmesinde Belirli** e-posta **adreslerini veya etki alanlarını ekle'yi seçin**.

4. Metin kutusuna, eklemek istediğiniz ilk kullanıcının (veya grubun) e-posta adresini girin ve Ekle'yi **seçin**.

5. İzinleri **seç'i seçin**.

6. İzinleri **seçin bölmesinde** , bu kullanıcı (veya grup) için izinleri seçin ve sonra da Kaydet'i **seçin**.

7. İzinleri Ata **bölmesine** dönerek, bu etikete eklemek istediğiniz her kullanıcı (veya grup) için 3 ile 6 arasında olan adımları yinelayın. Ardından **Kaydet'e tıklayın**.

8. Şifreleme sayfasında **Sonraki'yi** **seçin ve** yapılandırmayı tamamlayın.

### <a name="example-4-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Örnek 4: İçeriği şifrelayan ancak içeriğe kimlerin eriş erişeni kısıtlayan etiket

Bu yapılandırmada, e-postayı veya belgeyi şifrelemek için kullanıcıları, grupları veya etki alanlarını belirtmenize gerek yok avantajı vardır. İçerik şifrelenir ve yine de kullanım haklarını, son kullanma tarihini ve çevrimdışı erişimi belirtebilirsiniz.

Bu yapılandırmayı yalnızca korumalı belgeyi veya e-postayı açacak kullanıcıları kısıtlamak zorunda olmadığınız zaman kullanın. [Bu ayar hakkında daha fazla bilgi](#requirements-and-limitations-for-add-any-authenticated-users)

1. Şifreleme sayfasında **: İzinleri** şimdi **ata veya kullanıcıların karar vermesine izin ver? şimdi** izinleri **ata'nın seçili olduğundan** emin olun.

2. Kullanıcı içeriğine **erişimin süresi dolsa ve Gerektiğinde çevrimdışı** **erişime izin ver ayarlarını** yapılandırabilirsiniz.

3. İzinleri **ata'ya tıklayın**.

4. İzinleri **ata bölmesinde** Kimliği doğrulanmış kullanıcıları **ekle'yi seçin**.

    Kullanıcılar **ve gruplar için**, Kimliği doğrulanmış **kullanıcıların otomatik olarak ekli olduğunu** görüyorsunuz. Bu değeri değiştiremezsiniz, yalnızca silemezsiniz ve bu durumda Kimliği doğrulanmış kullanıcı ekleme **seçimi iptal** edilir.

5. İzinleri **seç'i seçin**.

6. İzinleri **seçin** bölmesindeki açılan kutuyu seçin, istediğiniz izinleri seçin ve sonra da Kaydet'i **seçin**.

7. İzinleri Ata **bölmesine dönüp** Kaydet'i **seçin**.

8. Şifreleme sayfasında **Sonraki'yi** **seçin ve** yapılandırmayı tamamlayın.

## <a name="considerations-for-encrypted-content"></a>Şifreli içerikle ilgili dikkate alınacak noktalar

En hassas belgelerinizi ve e-postalarınızı şifrelemek, yalnızca yetkili kişilerin bu verilere erişmesini sağlamaya yardımcı olur. Bununla birlikte, dikkate alınması gereken bazı noktalar vardır:

- Bu dosya ve klasörlerin dosyaları [için Office etiketleri SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

  - Arama, eBulma ve Delve şifreli dosyalar için çalışmaz.
  - DLP ilkeleri, bu şifreli dosyaların meta verileri için çalışır (bekletme etiketi bilgileri dahil) ancak bu dosyaların içeriğine (dosyaların içindeki kredi kartı numaraları gibi) yönelik değildir.
  - Kullanıcılar şifreli dosyaları e-posta iletileriyle Web üzerinde Office. SharePoint ve OneDrive'te Office dosyalarının duyarlılık etiketleri etkinleştirildiğinde, kullanıcılar Web üzerinde Office'i kullanarak şifrelenmiş dosyaları açabilir ve bu sınırlamalar şirket içi bir anahtarla uygulanan şifrelemeyi ("kendi anahtarınızı [](sensitivity-labels-sharepoint-onedrive-files.md#limitations) tutma" veya HYOK [olarak bilinir](#double-key-encryption)), çift anahtar şifrelemesi içerir ve duyarlılık etiketinden bağımsız olarak uygulanmış olan şifrelemeyi içerir.

- Şifrelenmiş belgeleri kurum dışından kişilerle paylaşıyorsanız konuk hesapları oluşturmanız ve Koşullu Erişim ilkelerini değiştirmeniz gerekir. Daha fazla bilgi için bkz [. Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Yetkili kullanıcılar Office uygulamalarına şifrelenmiş belgeleri açtıklarında, uygulamalarının üst kısmında sarı ileti çubuğunda etiket adını ve açıklamasını görebilirler. Şifreleme izinleri kuruluş dışındaki kullanıcılara genişletilende, belge açıldığında bu ileti çubuğunda görünür olacak etiket adlarını ve açıklamalarını dikkatle gözden geçirin.

- Birden çok kullanıcının şifreli bir dosyayı aynı anda düzenlemesi için, hepsinin Web için Office kullanıyor olması veya duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma özelliğini etkinleştirmiş olması gerekir ve tüm kullanıcıların bu özelliği destekleyen [Office](sensitivity-labels-coauthoring.md#prerequisites) uygulamaları vardır.[](sensitivity-labels-coauthoring.md) Durum böyle değilse ve dosya zaten açıksa:

  - Office uygulamalarında (Windows, Mac, Android ve iOS), kullanıcılar Kullanımda Dosyası iletisiyle birlikte dosyayı kullanıma alan  kişinin adını görüyor. Daha sonra salt okunur bir kopyayı  görüntülemelerini, dosyanın bir kopyasını kaydedlayıp düzenlemelerini ve dosya kullanılabilir olduğunda bildirim almalarını sağlarlar.
  - Web için Office'de, kullanıcılar belgeyi diğer kullanıcılarla birlikte düzenleyemediklerini ifadean bir hata iletisi görüyorlar. Böylece Okuma Görünümünde **Aç'ı da açabilirler**.

- iOS [ve](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) Android için Office Uygulamaları'nın Otomatik Kaydetme işlevselliği, şifrelenmiş dosyalar için devre dışı bırakılır. Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma işlevini etkinleştirmediyseniz, Windows ve Mac'te şifrelenmiş dosyalar için de bu [işlevsellik devre dışı bırakılır](sensitivity-labels-coauthoring.md). Kullanıcılar, Otomatik Kaydetme özelliğinin açılabilir olması için önce dosyanın kaldırılması gereken kısıtlı izinlere sahip olduğunu haber verilen bir ileti görüyor.

- Şifreli dosyaların farklı uygulamalarda (Office, Mac, Android Windows iOS) açılması daha uzun sürebilir.

- Şifreleme uygulanan bir etiket, Office uygulaması belge SharePoint kullanıma alınmışken bir SharePoint kullanılarak eklenirse ve kullanıcı kullanıma [](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de)almayı atsa, belge etiketli ve şifrelenmiş olarak kalır.

- Duyarlılık [etiketleriyle](sensitivity-labels-coauthoring.md) şifrelenmiş dosyalar için birlikte yazma özelliği etkinleştirmediyseniz, şifrelenmiş dosyalar için aşağıdaki eylemler Office uygulamaları (Windows, Mac, Android ve iOS) tarafından desteklenmez ve kullanıcılar bir sorun olduğunu içeren bir hata iletisi görüntüler. Bununla SharePoint işlevleri alternatif olarak kullanılabilir:

  - Önceki sürümlerin kopyalarını görüntüleme, geri yükleme ve kaydetme. Alternatif olarak, liste veya kitaplık için sürüm Web üzerinde Office etkinleştirerek yapılandırsanız da [kullanıcılar bu eylemleri gerçekleştirebilirsiniz](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37).
  - Dosyaların adını veya konumunu değiştirme. Alternatif olarak, kullanıcılar aynı [belge kitaplığında yer alan bir dosya, klasör veya bağlantıyı yeniden](https://support.microsoft.com/office/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185) SharePoint.

Duyarlılık etiketiyle şifrelenen dosyalar için en iyi işbirliği deneyimi için SharePoint, [SharePoint](sensitivity-labels-sharepoint-onedrive-files.md) ve OneDrive'daki Office etiketleri Web için Office.



## <a name="next-steps"></a>Sonraki adımlar

Etiketli ve şifrelenmiş belgelerinizi kuruluş dışındaki kişiler ile paylaşmanız mı gerekiyor?  Bkz [. Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
