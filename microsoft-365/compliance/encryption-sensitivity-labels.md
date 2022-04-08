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
description: Erişimi ve kullanımı kısıtlayarak verilerinizi koruyan şifreleme için duyarlılık etiketlerini yapılandırın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0ec60e573d5c05c4a30e74f235ffae5983de03dc
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705418"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Şifreleme uygulamak için hassasiyet etiketleri kullanarak içeriğe erişimi kısıtlama

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Duyarlılık etiketi oluşturduğunuzda, etiketin uygulanacağı içeriğe erişimi kısıtlayabilirsiniz. Örneğin, bir duyarlılık etiketinin şifreleme ayarlarıyla içeriği koruyarak şunları yapabilirsiniz:

- Gizli bir belgeyi veya e-postayı yalnızca kuruluşunuzdaki kullanıcılar açabilir.
- Yalnızca pazarlama departmanındaki kullanıcılar promosyon duyurusu belgesini veya e-postasını düzenleyebilir ve yazdırabilirken, kuruluşunuzdaki diğer tüm kullanıcılar bunu yalnızca okuyabilir.
- Kullanıcılar bir e-postayı iletemez veya dahili yeniden düzenleme hakkındaki haberleri içeren bilgileri kopyalayamaz.
- İş ortaklarına gönderilen geçerli fiyat listesi belirtilen tarihten sonra açılamaz.

Bir belge veya e-posta şifrelendiğinde içeriğe erişim kısıtlanır ve böylece:

- Yalnızca etiketin şifreleme ayarları tarafından yetkilendirilmiş kullanıcılar tarafından şifresi çözülebilir.
- Dosyanın adı yeniden adlandırılmış olsa bile kuruluşunuzun içinde veya dışında nerede olursa olsun şifrelenmiş olarak kalır.
- Hem bekleme durumunda (örneğin, bir OneDrive hesabında) hem de aktarım sırasında (örneğin, İnternet'ten geçen e-posta) şifrelenir.

Son olarak, bir yönetici olarak, şifreleme uygulamak için bir duyarlılık etiketi yapılandırdığınızda şunları seçebilirsiniz:

- **İzinleri şimdi atayın**, böylece hangi kullanıcıların bu etikete sahip içerik için hangi izinleri tam olarak aldığını belirleyebilirsiniz.
- Etiketi içeriğe uygulayan **kullanıcıların izin atamasına izin verin**. Bu şekilde, kuruluşunuzdaki kişilere işbirliği yapmak ve işlerini yapmak için ihtiyaç duyabilecekleri esneklik sağlayabilirsiniz.

Şifreleme ayarları, Microsoft 365 uyumluluk merkezi [bir duyarlılık etiketi oluşturduğunuzda](create-sensitivity-labels.md) kullanılabilir. Ayrıca eski portal olan Güvenlik & Uyumluluk Merkezi'ni de kullanabilirsiniz.

## <a name="understand-how-the-encryption-works"></a>Şifrelemenin nasıl çalıştığını anlama

Şifreleme, Azure Information Protection Azure Rights Management hizmetini (Azure RMS) kullanır. Bu koruma çözümü şifreleme, kimlik ve yetkilendirme ilkelerini kullanır. Daha fazla bilgi edinmek için Azure Information Protection belgelerinden Azure [Rights Management nedir?](/azure/information-protection/what-is-azure-rms) konusuna bakın. 

Bu şifreleme çözümünü kullandığınızda **süper kullanıcı** özelliği, yetkili kişilerin ve hizmetlerin kuruluşunuz için şifrelenmiş verileri her zaman okuyup inceleyebilmesini sağlar. Gerekirse şifreleme kaldırılabilir veya değiştirilebilir. Daha fazla bilgi için bkz[. Azure Information Protection ve bulma hizmetleri veya veri kurtarma için süper kullanıcıları yapılandırma](/azure/information-protection/configure-super-users).

## <a name="important-prerequisites"></a>Önemli önkoşullar

Şifrelemeyi kullanabilmeniz için bazı yapılandırma görevleri gerçekleştirmeniz gerekebilir. Şifreleme ayarlarını yapılandırdığınızda, bu önkoşulların karşılanıp karşılanmadığını doğrulama denetimi yoktur.

- Azure Information Protection korumasını etkinleştirme
    
    Duyarlılık etiketlerinin şifreleme uygulaması için Azure Information Protection'den koruma hizmetinin (Azure Rights Management) kiracınız için etkinleştirilmesi gerekir. Daha yeni kiracılarda bu varsayılan ayardır, ancak hizmeti el ile etkinleştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Azure Information Protection'den koruma hizmetini etkinleştirme](/azure/information-protection/activate-service).

- Ağ gereksinimlerini denetleme
    
    Ağ cihazlarınızda güvenlik duvarları gibi bazı değişiklikler yapmanız gerekebilir. Ayrıntılar için Azure Information Protection belgelerindeki [Güvenlik duvarları ve ağ altyapısı](/azure/information-protection/requirements#firewalls-and-network-infrastructure) bölümüne bakın.

- Azure Information Protection için Exchange yapılandırma
    
    kullanıcıların e-postalarını şifrelemek için Outlook etiket uygulayabilmesi için Exchange Azure Information Protection için yapılandırılması gerekmez. Ancak Exchange Azure Information Protection için yapılandırılana kadar azure rights management korumasını Exchange ile kullanma işlevinin tamamını elde edersiniz.
    
    Örneğin, kullanıcılar cep telefonlarında veya Web üzerinde Outlook ile şifrelenmiş e-postaları görüntüleyemez, şifrelenmiş e-postalar arama için dizine eklenemez ve Rights Management koruması için Exchange Online DLP'yi yapılandıramazsınız. 
    
    Exchange bu ek senaryoları desteklediğinden emin olmak için aşağıdakilere bakın:
    
    - Exchange Online için [Exchange Online: IRM Yapılandırması](/azure/information-protection/configure-office365#exchangeonline-irm-configuration) yönergelerine bakın.
    - Şirket içi Exchange için [RMS bağlayıcısını dağıtmanız ve Exchange sunucularınızı yapılandırmanız](/azure/information-protection/deploy-rms-connector) gerekir. 

## <a name="how-to-configure-a-label-for-encryption"></a>Şifreleme için etiket yapılandırma

1. [Duyarlılık etiketi oluşturmak veya düzenlemek](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) için genel yönergeleri izleyin ve etiketin kapsamı için **Dosyalar & e-postalarının** seçildiğinden emin olun: 
    
    ![Dosyalar ve e-postalar için duyarlılık etiketi kapsam seçenekleri.](../media/filesandemails-scope-options-sensitivity-label.png)

2. Ardından, **Dosyalar ve e-postalar için koruma ayarlarını seçin sayfasında Dosyaları ve e-postaları** **şifrele'yi** seçtiğinizden emin olun
    
    ![Dosyalar ve e-postalar için duyarlılık etiketi koruma seçenekleri.](../media/protection-options-sensitivity-label.png)

4.  **Şifreleme** sayfasında aşağıdaki seçeneklerden birini belirleyin:
    
    - **Dosya şifrelenmişse şifrelemeyi kaldırın**: Bu seçenek yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenir. Bu seçeneği belirlediğinizde ve yerleşik etiketleme kullandığınızda, etiket uygulamalarda görüntülenmeyebilir veya görüntülenip şifreleme değişikliği yapılmayabilir.
        
        Bu senaryo hakkında daha fazla bilgi [için bir etiket uygulandığında mevcut şifrelemeye ne olur](#what-happens-to-existing-encryption-when-a-labels-applied) bölümüne bakın. Bu ayarın kullanıcıların yeterli izinleri olmadığında uygulayamayacakları bir duyarlılık etiketine neden olabileceğini anlamak önemlidir.
    
    - **Şifreleme ayarlarını yapılandırma**: Şifrelemeyi açar ve şifreleme ayarlarını görünür hale getirir:
        
        ![Şifreleme için duyarlılık etiketi seçenekleri.](../media/encrytion-options-sensitivity-label.png)
        
        Bu ayarların yönergeleri aşağıdaki [Şifreleme ayarlarını yapılandırma](#configure-encryption-settings) bölümündedir.

### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Bir etiket uygulandığında mevcut şifrelemeye ne olur?

Şifrelenmemiş içeriğe duyarlılık etiketi uygulanırsa, seçebileceğiniz şifreleme seçeneklerinin sonucu açıklayıcıdır. Örneğin, **Dosyaları ve e-postaları şifrele'yi** seçmediyseniz içerik şifrelenmemiş olarak kalır.

Ancak içerik zaten şifrelenmiş olabilir. Örneğin, başka bir kullanıcı uygulamış olabilir:

- Bir etiket tarafından istendiğinde kullanıcı tanımlı izinleri, Azure Information Protection istemcisinin özel izinlerini ve bir Office uygulaması içinden **Kısıtlı Erişim** belge korumasını içeren kendi izinleri.
- İçeriği bir etiketten bağımsız olarak şifreleyen bir Azure Rights Management koruma şablonu. Bu kategori, hak korumasını kullanarak şifreleme uygulayan posta akışı kurallarını içerir.
- Yönetici tarafından atanan izinlerle şifreleme uygulayan bir etiket.

Aşağıdaki tabloda, söz konusu içeriğe duyarlılık etiketi uygulandığında var olan şifrelemeye ne olacağı tanımlanmıştır:

| | Şifreleme: Seçili değil | Şifreleme: Yapılandırıldı | Şifreleme: Kaldır <sup>\*</sup> |
|:-----|:-----|:-----|:-----|
|**Kullanıcı tarafından belirtilen izinler**|Özgün şifreleme korunur|Yeni etiket şifrelemesi uygulandı|Özgün şifreleme kaldırıldı|
|**Koruma şablonu**|Özgün şifreleme korunur|Yeni etiket şifrelemesi uygulandı|Özgün şifreleme kaldırıldı|
|**Yönetici tanımlı izinlerle etiket**|Özgün şifreleme kaldırıldı|Yeni etiket şifrelemesi uygulandı|Özgün şifreleme kaldırıldı|

**Dipnot:**

<sup>\*</sup>Yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenir

Yeni etiket şifrelemesinin uygulandığı veya özgün şifrelemenin kaldırıldığı durumlarda, bu durum yalnızca etiketi uygulayan kullanıcının bu eylemi destekleyen bir kullanım hakkı veya rolü varsa gerçekleşir:

- [Kullanım hakkı](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Dışarı Aktarma veya Tam Denetim.
- [Rights Management verenin veya Rights Management sahibinin](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) veya [süper kullanıcının](/azure/information-protection/configure-super-users) rolü.

Kullanıcı bu haklardan veya rollerden birine sahip değilse etiket uygulanamaz ve bu nedenle özgün şifreleme korunur. Kullanıcı şu iletiyi görür: **Duyarlılık etiketinde bu değişikliği yapma izniniz yok. Lütfen içerik sahibine başvurun.**

Örneğin, bir e-posta iletisine İletme'yi uygulayan kişi, e-postanın Rights Management sahibi olduğundan, iş parçacığını şifrelemeyi değiştirmek veya kaldırmak için yeniden etiketleyebilir. Ancak süper kullanıcılar dışında, bu e-postanın alıcıları gerekli kullanım haklarına sahip olmadıkları için e-postayı yeniden etiketleyemez.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Şifrelenmiş e-posta iletileri için e-posta ekleri

Bir e-posta iletisi herhangi bir yöntemle şifrelendiğinde, e-postaya eklenen şifrelenmemiş Office belgeleri otomatik olarak aynı şifreleme ayarlarını devralır.

Zaten şifrelenmiş olan ve ek olarak eklenen belgeler her zaman özgün şifrelemelerini korur.

## <a name="configure-encryption-settings"></a>Şifreleme ayarlarını yapılandırma

Duyarlılık etiketi oluşturmak veya düzenlemek için **Şifreleme** sayfasında **Şifreleme ayarlarını yapılandır'ı** seçtiğinizde aşağıdaki seçeneklerden birini belirleyin:

- **Şimdi izinleri atayın**, böylece etiketin uygulandığı içeriğe hangi kullanıcıların hangi izinleri alabileceğini tam olarak belirleyebilirsiniz. Daha fazla bilgi için şimdi [izin atama](#assign-permissions-now) bölümüne bakın.
- Kullanıcılarınız etiketi içeriğe uyguladığında kullanıcıların **izin atamasına izin verin**. Bu seçenekle, kuruluşunuzdaki kişilere işbirliği yapmak ve işlerini yapmak için ihtiyaç duyabilecekleri esneklik sağlayabilirsiniz. Daha fazla bilgi için bu sayfadaki [Kullanıcıların izin atamasına izin verme](#let-users-assign-permissions) bölümüne bakın.

Örneğin, en hassas içeriğinize uygulanacak **Son Derece Gizli** adlı bir duyarlılık etiketiniz varsa, bu içeriğe kimlerin ne tür izinler alacağına şimdi karar vermek isteyebilirsiniz.

Alternatif olarak, **İş Sözleşmeleri** adlı bir duyarlılık etiketiniz varsa ve kuruluşunuzun iş akışı, kişilerinizin bu içerik üzerinde geçici olarak farklı kişilerle işbirliği yapmalarını gerektiriyorsa, kullanıcılarınızın etiketi atadığında kimlerin izin alacağına karar vermelerine izin vermek isteyebilirsiniz. Bu esneklik hem kullanıcılarınızın üretkenliğine yardımcı olur hem de yöneticilerinizin belirli senaryoları ele almak için yeni duyarlılık etiketlerini güncelleştirme veya oluşturma isteklerini azaltır.

İzinlerin şimdi atanıp atanmayacağını veya kullanıcıların izin atamasına izin verilip verilmeyeceğini seçme:

![Kullanıcı veya yönetici tanımlı izinleri ekleme seçeneği.](../media/sensitivity-label-user-or-admin-defined-permissions.png)

## <a name="assign-permissions-now"></a>İzinleri şimdi atayın

Bu etiketin uygulandığı e-postaya veya belgelere kimlerin erişebileceğini denetlemek için aşağıdaki seçenekleri kullanın. Şunları yapabilirsiniz:

- **Etiketli içeriğe erişimin süresinin belirli** bir tarihte veya etiket uygulandıktan sonraki belirli bir gün sayısından sonra dolmasına izin verin. Bu süreden sonra kullanıcılar etiketli öğeyi açamayacak. Bir tarih belirtirseniz, geçerli saat diliminizdeki bu tarihte gece yarısı geçerli olur. (Bazı e-posta istemcilerinin önbelleğe alma mekanizmaları nedeniyle sona erme tarihini geçen e-postaları göstermeyebileceğini unutmayın.)

- Etiket uygulandıktan sonra hiçbir zaman, her zaman veya belirli bir sayıda gün boyunca **çevrimdışı erişime izin verme**. Çevrimdışı erişimi hiçbir zaman veya birkaç günle kısıtlarsanız, bu eşiğe ulaşıldığında kullanıcıların yeniden kimlik doğrulaması yapılması ve erişimlerinin günlüğe kaydedilmesi gerekir. Daha fazla bilgi için Rights Management kullanım lisansının sonraki bölümüne bakın.

Şifrelenmiş içerik için erişim denetimi için Ayarlar:

![Yönetici tanımlı izinler için Ayarlar.](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

### <a name="rights-management-use-license-for-offline-access"></a>Rights Management çevrimdışı erişim için lisans kullanma

Kullanıcı, Azure Rights Management hizmetinden şifrelemeyle korunan bir belgeyi veya e-postayı açtığında, kullanıcıya söz konusu içerik için bir Azure Rights Management kullanım lisansı verilir. Bu kullanım lisansı, kullanıcının belge veya e-posta için kullanım haklarını ve içeriği şifrelemek için kullanılan şifreleme anahtarını içeren bir sertifikadır. Kullanım lisansı, bu ayarlıysa ve kullanım lisansının ne kadar süreyle geçerli olduğunu içeren bir sona erme tarihi de içerir.

Son kullanma tarihi ayarlanmamışsa, kiracı için varsayılan kullanım lisansı geçerlilik süresi 30 gündür. Kullanım lisansı süresi boyunca, kullanıcı içerik için yeniden kimlik doğrulaması veya yeniden kimlik doğrulaması yapılmaz. Bu işlem, kullanıcının korumalı belgeyi veya e-postayı internet bağlantısı olmadan açmaya devam etmesine olanak tanır. Kullanım lisansı geçerlilik süresi dolduğunda, kullanıcı korumalı belgeye veya e-postaya bir sonraki eriştiğinde, kullanıcının yeniden kimlik doğrulaması ve yeniden yetkilendirmesi gerekir.

Yeniden kimlik doğrulamasına ek olarak, şifreleme ayarları ve kullanıcı grubu üyeliği yeniden değerlendirilir. Başka bir deyişle, şifreleme ayarlarında veya grup üyeliğinde içeriğe son erişimlerinden itibaren değişiklikler varsa, kullanıcılar aynı belge veya e-posta için farklı erişim sonuçlarıyla karşılaşabilir.

Varsayılan 30 günlük ayarı değiştirmeyi öğrenmek için bkz. [Rights Management kullanım lisansı](/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Belirli kullanıcılara veya gruplara izin atama

Belirli kişilere yalnızca etiketlenmiş içerikle etkileşim kurabilmeleri için izin vekleyebilirsiniz:

1. İlk olarak, etiketlenmiş içeriğe izinler atanacak kullanıcıları veya grupları ekleyin.

2. Ardından, bu kullanıcıların etiketlenmiş içerik için sahip olması gereken izinleri seçin.

İzinler atanıyor:

![Kullanıcılara izin atama seçenekleri.](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Kullanıcı veya grup ekleme

İzinleri atadığınızda şunları seçebilirsiniz:

- Kuruluşunuzdaki herkes (tüm kiracı üyeleri). Bu ayar konuk hesaplarını dışlar.

- Kimliği doğrulanmış kullanıcılar. Seçmeden önce bu ayarın [gereksinimlerini ve sınırlamalarını](#requirements-and-limitations-for-add-any-authenticated-users) anladığınızdan emin olun.

- Azure AD'de belirli bir kullanıcı veya e-posta özellikli güvenlik grubu, dağıtım grubu veya Microsoft 365 [grubu (eski adıyla Office 365 grup](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)). Microsoft 365 grubunun statik veya [dinamik üyeliği](/azure/active-directory/users-groups-roles/groups-create-rule) olabilir. Bu grup türü Azure AD ile eşitlenmediğinden ve e-posta etkin olmayan bir güvenlik grubu kullanamadığınızdan [Exchange dinamik dağıtım](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups) grubunu kullanamadığınızı unutmayın.
    
    Posta kişilerini içeren grupları kuruluşunuzun dışındaki birden çok kişiye erişim vermek için kullanışlı bir yöntem olarak belirtebilirsiniz ancak şu anda bu yapılandırmayla ilgili bilinen bir sorun vardır. Daha fazla bilgi için bkz [. Gruplardaki posta kişilerinin şifrelenmiş içeriğe aralıklı erişimi vardır](/office365/troubleshoot/sensitivity-labels/mail-contacts-lose-access-encrypted-content).

- Herhangi bir e-posta adresi veya etki alanı. Bu seçeneği, başka bir kuruluştaki Azure AD kullanan tüm kullanıcıları belirtmek için bu kuruluştan herhangi bir etki alanı adı girerek kullanın. Bu seçeneği sosyal sağlayıcılar için **gmail.com, hotmail.com** **veya** **outlook.com** gibi etki alanı adlarını girerek de kullanabilirsiniz.

    > [!NOTE]
    > Azure AD kullanan bir kuruluştan etki alanı belirtirseniz, ilgili etki alanına erişimi kısıtlayamazsınız. Bunun yerine, Azure AD'deki tüm doğrulanmış etki alanları, belirttiğiniz etki alanı adının sahibi olan kiracıya otomatik olarak eklenir.

Kuruluşunuzdaki tüm kullanıcıları ve grupları seçtiğinizde veya dizine göz attığınızda, kullanıcıların veya grupların bir e-posta adresi olmalıdır.

En iyi uygulama olarak, kullanıcılar yerine grupları kullanın. Bu strateji yapılandırmanızı daha basit tutar.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>"Kimliği doğrulanmış kullanıcı ekle" için gereksinimler ve sınırlamalar

Bu ayar, etiketin şifrelediği içeriğe kimlerin erişebileceğini kısıtlamaz, içeriği şifrelemeye devam eder ve içeriğin nasıl kullanılabileceğini (izinler) ve erişilebileceğini (süre sonu ve çevrimdışı erişim) kısıtlama seçenekleri sunar. Ancak şifrelenmiş içeriği açan uygulamanın kullanılan kimlik doğrulamasını destekleyebilmesi gerekir. Bu nedenle, Google gibi federasyon sosyal sağlayıcıları ve tek seferlik geçiş kodu kimlik doğrulaması yalnızca e-posta için ve yalnızca Exchange Online kullandığınızda çalışır. Microsoft hesapları Office 365 uygulamaları ve [Azure Information Protection görüntüleyicisi](https://portal.azurerms.com/#/download) ile kullanılabilir.

> [!NOTE]
> Duyarlılık etiketleri SharePoint ve OneDrive Office [dosyaları için etkinleştirildiğinde bu ayarı SharePoint ve Azure](sensitivity-labels-sharepoint-onedrive-files.md) [AD B2B ile OneDrive tümleştirmesi ile](/sharepoint/sharepoint-azureb2b-integration-preview) kullanmayı göz önünde bulundurun.

Kimliği doğrulanmış kullanıcılar ayarı için bazı tipik senaryolar:

- İçeriği kimlerin görüntülediğinden rahatsız olmazsınız, ancak içeriği kullanma biçimini kısıtlamak istersiniz. Örneğin, içeriğin düzenlenmesini, kopyalanmasını veya yazdırılmasını istemezsiniz.
- İçeriğe erişenleri kısıtlamanız gerekmez, ancak içeriği kimin açtığını onaylamak istiyorsunuz.
- İçeriğin bekleyen ve aktarım sırasında şifrelenmesi gerekir, ancak erişim denetimleri gerektirmez.

#### <a name="choose-permissions"></a>İzinleri seçme

Bu kullanıcılar veya gruplar için hangi izinlere izin verileceğini seçtiğinizde şunlardan birini seçebilirsiniz:

- Co-Author veya Gözden Geçiren gibi önceden ayarlanmış bir hak grubuna sahip [önceden tanımlanmış izin düzeyi](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) .
- Bir veya daha fazla kullanım hakkı seçtiğiniz özel izinler.

Uygun izinleri seçmenize yardımcı olacak daha fazla bilgi için bkz [. Kullanım hakları ve açıklamaları](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Önceden ayarlanmış veya özel izinleri seçme seçenekleri.](../media/Sensitivity-Choose-permissions-settings.png)

Aynı etiketin farklı kullanıcılara farklı izinler verebileceğini unutmayın. Örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi, tek bir etiket bazı kullanıcıları Gözden Geçiren ve farklı bir kullanıcıyı Ortak Yazar olarak atayabilir.

Bunu yapmak için kullanıcıları veya grupları ekleyin, izinler atayın ve bu ayarları kaydedin. Ardından bu adımları yineleyin, kullanıcıları ekleyin ve onlara izinler atayın ve ayarları her seferinde kaydedin. Farklı kullanıcılar için farklı izinler tanımlamak için bu yapılandırmayı gerektiği sıklıkta yineleyebilirsiniz.

![Farklı izinlere sahip farklı kullanıcılar.](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>Rights Management veren (duyarlılık etiketini uygulayan kullanıcı) her zaman Tam Denetime sahiptir

Duyarlılık etiketi için şifreleme, Azure Information Protection Azure Rights Management hizmetini kullanır. Kullanıcı şifreleme kullanarak bir belgeyi veya e-postayı korumak için duyarlılık etiketi uyguladığında, bu kullanıcı söz konusu içerik için Rights Management vereni olur.

Rights Management verene her zaman belge veya e-posta için Tam Denetim izinleri verilir ve buna ek olarak:

- Şifreleme ayarları bir sona erme tarihi içerirse, Rights Management veren belgeyi veya e-postayı bu tarihten sonra da açabilir ve düzenleyebilir.
- Rights Management veren her zaman çevrimdışı olarak belgeye veya e-postaya erişebilir.
- Rights Management veren, iptal edilen bir belgeyi açmaya devam edebilir.

Daha fazla bilgi için bkz. [Rights Management veren ve Rights Management sahibi](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

### <a name="double-key-encryption"></a>Çift Anahtarlı Şifreleme

> [!NOTE]
> Bu özellik şu anda yalnızca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenmektedir.

Bu seçeneği yalnızca Çift Anahtar Şifrelemesi hizmetini yapılandırdıktan ve bu etiketin uygulanacağı dosyalar için bu çift anahtar şifrelemesini kullanmanız gerektiğinde belirtin. Etiket yapılandırılıp kaydedildikten sonra düzenleyemezsiniz.

Daha fazla bilgi, önkoşullar ve yapılandırma yönergeleri için bkz. [Çift Anahtar Şifrelemesi (DKE)](double-key-encryption.md).

## <a name="let-users-assign-permissions"></a>Kullanıcıların izin atamasına izin ver

> [!IMPORTANT]
> Etiketleme istemcilerinin tümü, kullanıcıların kendi izinlerini atamasına izin veren tüm seçenekleri desteklemez. Daha fazla bilgi edinmek için bu bölümü kullanın.

Kullanıcıların içeriğe el ile duyarlılık etiketi uyguladığında izin atamasına izin vermek için aşağıdaki seçenekleri kullanabilirsiniz:

- Outlook'da kullanıcı, seçtiği alıcılar için [İletme](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) seçeneğine veya [Yalnızca şifrele seçeneğine](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails) eşdeğer kısıtlamalar seçebilir.
    
    İletme seçeneği duyarlılık etiketlerini destekleyen tüm e-posta istemcileri tarafından desteklenir. Ancak Duyarlılık etiketiyle **Yalnızca Şifrele** seçeneğinin uygulanması, Azure Information Protection birleşik etiketleme istemcisi tarafından değil yalnızca yerleşik etiketleme ile desteklenen daha yeni bir sürümdür. Bu özelliği desteklemeyen e-posta istemcileri için etiket görünmez.
    
    Encrypt-Only seçeneğinin duyarlılık etiketiyle uygulanmasını desteklemek üzere yerleşik etiketleme kullanan Outlook uygulamalarının en düşük sürümlerini denetlemek [için, Outlook için yetenekler tablosunu](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-outlook) ve **Kullanıcıların izin atamasına izin ver: - Yalnızca Şifrele** satırını kullanın.

- Word, PowerPoint ve Excel'da bir kullanıcıdan belirli kullanıcılar, gruplar veya kuruluşlar için kendi izinlerini seçmesi istenir.

    Bu seçenek, Azure Information Protection birleşik etiketleme istemcisi ve yerleşik etiketleme kullanan bazı uygulamalar tarafından desteklenir. Bu özelliği desteklemeyen uygulamalar için etiket kullanıcılar için görünmez veya tutarlılık açısından görünür ancak kullanıcılara açıklama iletisiyle uygulanamaz.
    
    Yerleşik etiketleme kullanan uygulamaların bu seçeneği desteklediğini denetlemek [için Word, Excel ve PowerPoint için capabilities tablosunu](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) ve **Kullanıcıların izin atamasına izin ver: - Kullanıcılara sor** satırını kullanın.

Seçenekler desteklendiğinde, kullanıcıların duyarlılık etiketini ne zaman göreceğini belirlemek için aşağıdaki tabloyu kullanın:

|Ayar |Outlook'de görünen etiket|Word, Excel PowerPoint'de görünen etiket|
|:-----|:-----|:-----|:-----|
|**Outlook'da İletme veya Encrypt-Only seçeneğiyle kısıtlamaları zorunlu kılın**|Evet |Hayır |
|**Word'de, PowerPoint ve Excel, kullanıcılardan izinleri belirtmelerini iste**|Hayır |Evet|

Her iki ayar da seçildiğinde etiket hem Outlook hem de Word, Excel ve PowerPoint görünür.

Kullanıcıların içeriğe izin atamasına olanak tanıyan bir duyarlılık etiketi, kullanıcılar tarafından içeriğe el ile uygulanmalıdır; otomatik olarak uygulanamaz veya önerilen etiket olarak kullanılamaz.

Kullanıcı tarafından atanan izinleri yapılandırma:

![Kullanıcı tanımlı izinler için şifreleme ayarları.](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>Outlook kısıtlamaları

Outlook'da, kullanıcı bir iletiye izin atamasına izin veren bir duyarlılık etiketi uyguladığında **İletme seçeneğini** veya **Yalnızca Şifrele'yi** seçebilirsiniz. Kullanıcı, iletinin üst kısmında içeriğin korunduğunu gösteren etiket adını ve açıklamasını görür. Word, PowerPoint ve Excel([sonraki bölüme](#word-powerpoint-and-excel-permissions) bakın) aksine, kullanıcılardan belirli izinleri seçmeleri istenmez.

![Outlook'da iletiye uygulanan duyarlılık etiketi.](../media/sensitivity-label-outlook-protection-applied.png)

Bu seçeneklerden herhangi biri bir e-postaya uygulandığında, e-posta şifrelenir ve alıcıların kimliğinin doğrulanması gerekir. Ardından alıcıların kullanım hakları otomatik olarak kısıtlanır:

- **İletme**: Alıcılar e-postayı iletemez, yazdıramaz veya kopyalayamaz. Örneğin, Outlook istemcisinde İlet düğmesi kullanılamaz, Farklı Kaydet ve Yazdır menü seçenekleri kullanılamaz ve Kime, Bilgi veya Gizli kutularına alıcı ekleyemez veya değiştiremezsiniz.
    
    Bu seçeneğin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [E-postalar için İletme seçeneği](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails).

- **Yalnızca Şifrele**: Alıcılar Farklı Kaydet, Dışarı Aktar ve Tam Denetim dışında tüm kullanım haklarına sahiptir. Bu kullanım hakları birleşimi, alıcıların korumayı kaldıramayacakları dışında hiçbir kısıtlaması olmadığı anlamına gelir. Örneğin, bir alıcı e-postadan kopyalayabilir, yazdırabilir ve iletebilir.
    
    Bu seçeneğin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [E-postalar için yalnızca şifreleme seçeneği](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails).

E-postaya eklenen şifrelenmemiş Office belgeleri otomatik olarak aynı kısıtlamaları devralır. İletme için, bu belgelere uygulanan kullanım hakları İçeriği Düzenle, Düzenle; Kaydet; Görüntüle, Aç, Oku; ve Makrolara İzin Ver'i seçin. Kullanıcı bir ek için farklı kullanım hakları istiyorsa veya ek bu devralınan korumayı destekleyen Office bir belge değilse, kullanıcının dosyayı e-postaya eklemeden önce şifrelemesi gerekir.

### <a name="word-powerpoint-and-excel-permissions"></a>Word, PowerPoint ve Excel izinleri

Word'de, PowerPoint ve Excel, bir kullanıcı belgeye izin atamasına olanak tanıyan bir duyarlılık etiketi uyguladığında, şifreleme uygulandığında kullanıcı ve izin seçimini belirtmesi istenir.

Örneğin, [birlikte yazma etkinleştirilmediği](sensitivity-labels-coauthoring.md) sürece Azure Information Protection birleşik etiketleme istemcisiyle kullanıcılar şunları yapabilir:

- Görüntüleyici (Yalnızca Görüntüleme izni atayan) veya Co-Author (Görünüm, Düzenleme, Kopyalama ve Yazdırma izinleri atayan) gibi bir izin düzeyi seçin.
- Kullanıcıları, grupları veya kuruluşları seçin. Bu, kuruluşunuzun içindeki veya dışındaki kişileri içerebilir.
- Seçili kullanıcıların içeriğe erişemeyeceği bir sona erme tarihi ayarlayın. Daha fazla bilgi için, yukarıdaki [Rights Management çevrimdışı erişim için lisans kullanma](#rights-management-use-license-for-offline-access) bölümüne bakın.

![Kullanıcının özel izinlerle koruma seçenekleri.](../media/sensitivity-aip-custom-permissions-dialog.png)

Yerleşik etiketleme ve [birlikte yazma etkinleştirildiğinde](sensitivity-labels-coauthoring.md) Azure Information Protection birleşik etiketleme istemcisi için, kullanıcılar aşağıdakileri seçmiş gibi aynı iletişim kutusunu görür:

- Windows: **Dosya** sekmesi > **InfoProtect** >  **DocumentRestrict** >  **AccessRestricted Access** > 

- macOS: **ProtectionPermissionsRestricted** >  >  **Access** > **Gözden Geçir** sekmesi

> [!TIP]
> Kullanıcılar [birlikte yazma etkinleştirilmeden](sensitivity-labels-coauthoring.md) önce Azure Information Protection birleşik etiketleme istemcisiyle özel izinler yapılandırma konusunda bilgi sahibiyse, izin düzeylerinin bireysel kullanım haklarıyla eşlemesini gözden geçirmeyi yararlı bulabilirsiniz: [İzin düzeylerine dahil edilen haklar](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

## <a name="example-configurations-for-the-encryption-settings"></a>Şifreleme ayarları için örnek yapılandırmalar

Aşağıdaki her örnek için Şifreleme **ayarlarını yapılandır** seçildiğinde **Şifreleme** sayfasından yapılandırmayı yapın:

![Duyarlılık etiketi sihirbazında şifreleme seçeneğini uygulayın.](../media/apply-encryption-option.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-an-encrypted-email-to-a-gmail-account"></a>Örnek 1: Gmail hesabına şifreli e-posta göndermek için İletme'yi uygulayan etiket

Bu etiket yalnızca Outlook ve Web üzerinde Outlook görüntülenir ve Exchange Online kullanmanız gerekir. Kullanıcılara Gmail hesabı (veya kuruluşunuzun dışındaki başka bir e-posta hesabı) kullanan kişilere şifreli bir e-posta göndermeleri gerektiğinde bu etiketi seçmelerini bildirin.

Kullanıcılarınız **, Gmail** e-posta adresini To kutusuna yazar.  Ardından etiketi seçer ve İletme seçeneği otomatik olarak e-postaya eklenir. Sonuç olarak, alıcılar e-postayı iletemez, yazdıramaz, kopyalayamaz veya **Farklı Kaydet** seçeneğini kullanarak e-postayı posta kutularının dışına kaydedemez.

1. **Şifreleme** sayfasında: **İzinleri şimdi ata veya kullanıcıların karar vermesine izin ver?** için **Kullanıcıların etiketi uygularken izin atamasına izin ver'i** seçin.

2. Onay kutusunu seçin: **Outlook,İletme seçeneğine eşdeğer kısıtlamaları zorunlu kılın**.

3. Seçiliyse, onay kutusunu temizleyin: **Word'de, PowerPoint ve Excel, kullanıcılardan izinleri belirtmelerini iste**.

4. **İleri'yi** seçin ve yapılandırmayı tamamlayın.

### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization"></a>Örnek 2: Salt okunur izni başka bir kuruluştaki tüm kullanıcılarla kısıtlayan etiket

Bu etiket, çok hassas belgeleri salt okunur olarak paylaşmak için uygundur ve belgelerin görüntülenmesi için her zaman bir İnternet bağlantısı gerekir.

Bu etiket e-postalar için uygun değildir.

1. **Şifreleme** sayfasında: **İzinleri şimdi ata veya kullanıcıların karar vermesine izin ver?** **için İzinleri şimdi ata'yı** seçin.

2. **Çevrimdışı erişime izin ver** için **Hiçbir zaman'ı** seçin.

3. **İzin ata'yı** seçin.

4. **İzinleri ata** bölmesinde **Belirli e-posta adresleri veya etki alanları ekle'yi** seçin.

5. Metin kutusuna, diğer kuruluştan bir etki alanının adını (örneğin, **fabrikam.com**) girin. Ardından **Ekle'yi** seçin.

6. **İzinleri seçin'i** seçin.

7. **İzinleri seçin** bölmesinde açılan kutuyu seçin, **Görüntüleyici'yi** ve ardından **Kaydet'i** seçin.

8. **İzin Ata** bölmesine geri dönüp **Kaydet'i** seçin.

9. **Şifreleme** sayfasında **İleri'yi** seçin ve yapılandırmayı tamamlayın.

### <a name="example-3-add-external-users-to-an-existing-label-that-encrypts-content"></a>Örnek 3: İçeriği şifreleyen mevcut bir etikete dış kullanıcılar ekleme

Eklediğiniz yeni kullanıcılar, bu etiketle zaten korunan belgeleri ve e-postaları açabilir. Bu kullanıcılara verebileceğiniz izinler, mevcut kullanıcıların sahip olduğu izinlerden farklı olabilir.

1. **Şifreleme** sayfasında: **İzinleri şimdi ata veya kullanıcıların karar vermesine izin ver?** **için İzinleri şimdi ata'nın** seçili olduğundan emin olun.

2. **İzin ata'yı** seçin.

3. **İzinleri ata** bölmesinde **Belirli e-posta adresleri veya etki alanları ekle'yi** seçin.

4. Metin kutusuna, eklenecek ilk kullanıcının (veya grubun) e-posta adresini girin ve **Ekle'yi** seçin.

5. **İzinleri seçin'i** seçin.

6. **İzinleri seçin** bölmesinde, bu kullanıcının (veya grubun) izinlerini seçin ve ardından **Kaydet'i** seçin.

7. **İzinLeri Ata** bölmesine geri dönüp, bu etikete eklemek istediğiniz her kullanıcı (veya grup) için 3 ile 6 arasındaki adımları yineleyin. Ardından **Kaydet'e** tıklayın.

8. **Şifreleme** sayfasında **İleri'yi** seçin ve yapılandırmayı tamamlayın.

### <a name="example-4-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Örnek 4: İçeriği şifreleyen ancak kimlerin erişebileceğini kısıtlamayan etiket

Bu yapılandırma, e-postayı veya belgeyi şifrelemek için kullanıcıları, grupları veya etki alanlarını belirtmeniz gerekmeyen bir avantaja sahiptir. İçerik yine şifrelenir ve yine de kullanım haklarını, süre sonu tarihini ve çevrimdışı erişimi belirtebilirsiniz.

Bu yapılandırmayı yalnızca korumalı belgeyi veya e-postayı kimlerin açabileceğini kısıtlamanız gerekmediğinde kullanın. [Bu ayar hakkında daha fazla bilgi](#requirements-and-limitations-for-add-any-authenticated-users)

1. **Şifreleme** sayfasında: **İzinleri şimdi ata veya kullanıcıların karar vermesine izin ver?** **için İzinleri şimdi ata'nın** seçili olduğundan emin olun.

2. **kullanıcıya içeriğe erişimin süresi dolacak** ve **Çevrimdışı erişime izin ver** ayarlarını gerektiği gibi yapılandırın.

3. **İzin ata'yı** seçin.

4. **İzinleri ata** bölmesinde **Kimliği doğrulanmış kullanıcılar ekle'yi** seçin.

    **Kullanıcılar ve gruplar** için **kimliği doğrulanmış kullanıcıların** otomatik olarak eklendiğini görürsünüz. Bu değeri değiştiremezsiniz, yalnızca silebilirsiniz; bu da **Kimliği doğrulanmış kullanıcı ekle** seçimini iptal eder.

5. **İzinleri seçin'i** seçin.

6. **İzinleri seçin** bölmesinde açılan kutuyu seçin, istediğiniz izinleri seçin ve ardından **Kaydet'i** seçin.

7. **İzin Ata** bölmesine geri dönüp **Kaydet'i** seçin.

8. **Şifreleme** sayfasında **İleri'yi** seçin ve yapılandırmayı tamamlayın.

## <a name="considerations-for-encrypted-content"></a>Şifrelenmiş içerikle ilgili dikkat edilmesi gerekenler

En hassas belgelerinizi ve e-postalarınızı şifrelemek, bu verilere yalnızca yetkili kişilerin erişebilmesini sağlamaya yardımcı olur. Ancak dikkat edilmesi gereken bazı noktalar vardır:

- Kuruluşunuz SharePoint [ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirmediyse](sensitivity-labels-sharepoint-onedrive-files.md):

  - Arama, eBulma ve Delve şifrelenmiş dosyalar için çalışmaz.
  - DLP ilkeleri, bu şifrelenmiş dosyaların meta verileri (bekletme etiketi bilgileri dahil) için çalışır, ancak bu dosyaların içeriği (dosyalar içindeki kredi kartı numaraları gibi) için çalışmaz.
  - Kullanıcılar Web üzerinde Office kullanarak şifrelenmiş dosyaları açamaz. SharePoint ve OneDrive Office dosyaları için duyarlılık etiketleri etkinleştirildiğinde, kullanıcılar şifrelenmiş dosyaları açmak için Web üzerinde Office kullanabilir ve şirket içi anahtarla ("kendi anahtarını tut" veya HYOK olarak bilinir) uygulanan şifrelemeyi içeren bazı [sınırlamalar](sensitivity-labels-sharepoint-onedrive-files.md#limitations), [çift anahtarlı şifreleme](#double-key-encryption) ve duyarlılık etiketinden bağımsız olarak uygulanan şifreleme.

- Şifrelenmiş belgeleri kuruluşunuzun dışındaki kişilerle paylaşıyorsanız konuk hesapları oluşturmanız ve Koşullu Erişim ilkelerini değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Yetkili kullanıcılar şifrelenmiş belgeleri Office uygulamalarında açtıklarında, uygulamalarının üst kısmındaki sarı ileti çubuğunda etiket adını ve açıklamasını görürler. Şifreleme izinleri kuruluşunuzun dışındaki kişilere yayıldığında, belge açıldığında bu ileti çubuğunda görünür olacak etiket adlarını ve açıklamalarını dikkatle gözden geçirin.

- Birden çok kullanıcının şifrelenmiş bir dosyayı aynı anda düzenlemesi için hepsinin Web için Office kullanıyor olması veya [duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirmiş](sensitivity-labels-coauthoring.md) olmanız ve tüm kullanıcıların [bu özelliği destekleyen Office uygulamaları](sensitivity-labels-coauthoring.md#prerequisites) olması gerekir. Böyle bir durum söz konusu değilse ve dosya zaten açıksa:

  - Office uygulamalarında (Windows, Mac, Android ve iOS), kullanıcılar dosyayı kullanıma alan kişinin adını içeren Bir **Kullanımda Dosya** iletisi görür. Daha sonra salt okunur bir kopya görüntüleyebilir veya dosyanın bir kopyasını kaydedip düzenleyebilir ve dosya kullanılabilir olduğunda bildirim alabilirler.
  - Web için Office'da kullanıcılar belgeyi diğer kişilerle düzenleyemediklerine ilişkin bir hata iletisi görür. Daha sonra **Okuma Görünümünde Aç'ı** seçebilirler.

- iOS ve Android için Office uygulamalarında [Otomatik Kaydet](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) işlevi şifrelenmiş dosyalar için devre dışı bırakılır. [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirmediyseniz](sensitivity-labels-coauthoring.md), Windows ve Mac'te şifrelenmiş dosyalar için de bu işlev devre dışı bırakılır. Kullanıcılar, Otomatik Kaydetme'nin açılabilmesi için dosyanın kaldırılması gereken kısıtlı izinlere sahip olduğunu belirten bir ileti görür.

- Şifrelenmiş dosyaların Office uygulamalarında (Windows, Mac, Android ve iOS) açılması daha uzun sürebilir.

- Belge SharePoint kullanıma alındığında bir Office uygulaması kullanılarak şifreleme uygulayan bir etiket eklenirse ve kullanıcı kullanıma almayı atarsa, belge etiketli ve şifrelenmiş olarak kalır.[](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de)

- [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirmediğiniz](sensitivity-labels-coauthoring.md) sürece, şifrelenmiş dosyalar için aşağıdaki eylemler Office uygulamalarda (Windows, Mac, Android ve iOS) desteklenmez ve kullanıcılar bir sorun oluştuğuna ilişkin bir hata iletisi görür. Ancak SharePoint işlevselliği alternatif olarak kullanılabilir:

  - Önceki sürümlerin kopyalarını görüntüleyin, geri yükleyin ve kaydedin. Alternatif olarak, kullanıcılar bir [liste veya kitaplık için sürüm oluşturmayı etkinleştirip yapılandırdığınızda](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37) Web üzerinde Office kullanarak bu eylemleri gerçekleştirebilir.
  - Dosyaların adını veya konumunu değiştirin. Alternatif olarak, kullanıcılar SharePoint [belge kitaplığındaki bir dosyayı, klasörü veya bağlantıyı yeniden adlandırabilir](https://support.microsoft.com/office/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185).

Duyarlılık etiketiyle şifrelenen dosyalar için en iyi işbirliği deneyimi [için, SharePoint, OneDrive ve Web için Office Office dosyaları için duyarlılık etiketlerini](sensitivity-labels-sharepoint-onedrive-files.md) kullanmanızı öneririz.



## <a name="next-steps"></a>Sonraki adımlar

Etiketli ve şifrelenmiş belgelerinizi kuruluşunuzun dışındaki kişilerle paylaşmanız mı gerekiyor?  Bkz. [Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
