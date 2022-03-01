---
title: Yazılım kiracınız için fidye yazılımı Microsoft 365 dağıtın
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
- m365solution-overview
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: Yazılım kaynaklarınızı fidye yazılımlarına Microsoft 365 için koruma adımlarını takip edin.
ms.openlocfilehash: 634888ac603be17265733c4443a69495015296d7
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015351"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Yazılım kiracınız için fidye yazılımı Microsoft 365 dağıtın

Fidye yazılımları, dosya ve klasörleri yok eden veya şifreleyen ve kritik verilere erişimi engelleyen bir tür ekserz saldırıdır. Ürünler fidye yazılımı genellikle cihazlara bulaşacak bir virüs gibi yayılır ve yalnızca kötü amaçlı yazılım düzeltmesi gerektirir. İnsan tarafından işletilen fidye yazılımları, bir kuruluşun şirket içi veya bulut IT altyapısını tehdit ediyor, ayrıcalıklarını yükselten ve fidye yazılımlarını kritik verilere dağıtan siber suçlular tarafından etkin bir saldırının sonucudur.

Saldırı tamamlandıktan sonra bir saldırgan, silinmiş dosyalar için exchange'den, şifreli dosyalar için şifre çözme anahtarlarının ya da hassas verileri koyu web'e veya genel İnternet'e açıklamama taa yakını talep eder. İnsan tarafından işletilen fidye yazılımları, endüstri üretimi için gerekenler gibi kritik makine ve süreçleri kapatmak, giderilene ve zarar düzeltilene kadar normal iş işlemlerini durdurmak için de kullanılabilir. Kuruluş, zararları kendi düzeltmelerini sağlar.

İnsan tarafından işletilen bir fidye yazılımı saldırısı, her boyuttaki işletmeler için zararlı olabilir ve temizlemesi zordur ve gelecekteki saldırılara karşı korumak için tam ileri geri evik gerekli olabilir. Ürünlere yönelik fidye yazılımlarının aksine, insanlar tarafından işletilen fidye yazılımları ilk başlatma isteği sonrasında işletmelerle tehdit etmeye devam edebilir.

>[!Note]
>Bir kiracıya fidye yazılımı saldırısı Microsoft 365 saldırgan, bir kiracı için geçerli kullanıcı hesabı kimlik bilgilerine sahip olduğunu ve kullanıcı hesabına izin verilen tüm dosya ve kaynaklara erişimi olduğunu varsayıyor. Geçerli kullanıcı hesabı kimlik bilgileri olmayan bir saldırgan, geri kalan ve varsayılan ve gelişmiş şifreleme ile şifrelenmiş verilerin şifresini Microsoft 365 gerekir. Daha fazla bilgi için bkz. [Şifreleme ve anahtar yönetimine genel bakış](/compliance/assurance/assurance-encryption). 
>

Microsoft ürünleri genelinde fidye yazılımı koruması hakkında daha fazla bilgi için bu ek fidye [yazılımı kaynaklarına bakın](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>Buluttaki güvenlik bir ortaklıktır

Microsoft bulut hizmetlerinizin güvenliği, siz ve Microsoft arasındaki bir ortaklıktır:

- Microsoft bulut hizmetleri güven ve güvenlik temel üzerine kurulur. Microsoft, verilerinizi ve uygulamalarınızı korumanıza yardımcı olmak için güvenlik denetimleri ve özellikler sağlar.
- Verilerinizi ve kimliklerinizi ve bunları koruma sorumluluğunuz, şirket içi kaynaklarınızı koruma ve sizin denetiminiz olan bulut bileşenlerinin güvenliği sizin sorumluluğumdadır.

Bu özellikleri ve sorumlulukları birleştirerek fidye yazılımı saldırılarına karşı en iyi korumayı sağlaruz.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Yazılımla birlikte sağlanan fidye yazılımı azaltma ve Microsoft 365

Bir fidye yazılımı yazılımı, bir Microsoft 365 tarafından organizasyonlarınızı şu kişi tarafından tutmanıza neden olabilir:

- Dosyaları veya e-postaları silme
- Dosyaları yerinde şifreleme
- Dosyaları kiracının dışına kopyalama (veri dışarı yükleme)

Bununla birlikte Microsoft 365 çevrimiçi hizmetlerin, müşteri verilerini fidye yazılımı saldırılarından korumaya yönelik birçok yerleşik özellik ve denetimi vardır. Aşağıdaki bölümlerde bir özet sağlanmıştır. Microsoft'un müşteri verilerini, yazılım yazılımlarını ve fidye yazılımlarını nasıl koruma [hakkında daha fazla Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection).

>[!Note]
>Bir kiracıya fidye yazılımı saldırısı Microsoft 365 saldırgan, bir kiracı için geçerli kullanıcı hesabı kimlik bilgilerine sahip olduğunu ve kullanıcı hesabına izin verilen tüm dosya ve kaynaklara erişimi olduğunu varsayıyor. Geçerli kullanıcı hesabı kimlik bilgileri olmayan bir saldırgan, geri kalan ve varsayılan ve gelişmiş şifreleme ile şifrelenmiş verilerin şifresini Microsoft 365 gerekir. Daha fazla bilgi için bkz. [Şifreleme ve anahtar yönetimine genel bakış](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Dosyaları veya e-postaları silme

E-SharePoint OneDrive İş dosyalar şu şekilde korunur:

- Sürüm 

   Microsoft 365 varsayılan olarak dosyanın en az 500 sürümünü korur ve daha fazlasını korumak üzere yalıtabilirsiniz. 

   Güvenliğiniz ve yardım masası üzerindeki yükü en aza indirmek için, kullanıcılarınıza dosyaların önceki sürümlerini nasıl geri [yükleyecekleri hakkında eğitin](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Geri dönüşüm kutusu

   Fidye yazılımları dosyanın yeni şifreli bir kopyasını oluşturur ve eski dosyayı silerse, müşterilerin geri dönüşüm kutusunu geri yüklemek için 93 günü vardır. 93 günün ardından, Microsoft'un yine de verileri kurtar olduğu 14 günlük bir pencere vardır. 
  
   Güvenliğinizin ve yardım masası personelinizin yükünü en aza indirmek için, kullanıcılarınızı geri dönüşüm kutusu'nda dosyaları nasıl [geri yükleyecekleri hakkında eğitin](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Dosyaları Geri Yükleme](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   Son 30 gün içinde yöneticilerin ve son SharePoint kullanıcıların dosyaları herhangi bir noktada geri yüklemelerini sağlayan, SharePoint ve OneDrive için tam bir self servis kurtarma çözümü.

   Güvenliğinize ve IT yardım masasına yükü en aza indirmek için, kullanıcılarınızı Dosyaları Geri [Yükleme'ye eğitin](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).


Toplu OneDrive SharePoint fazla dosya için Microsoft bir toplu saldırıyla olursanız 14 gün içinde önceki bir noktaya geri dönebilirsiniz.

E-posta şunları sağlar:

- [Yanlışlıkla veya kötü](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) amaçlı silme işlemiyle posta kutusu öğelerini kurtarabilirsiniz ve bu şekilde tek öğe kurtarma ve posta kutusu bekletme. Varsayılan olarak 14 gün içinde silinen posta iletilerini 30 gün'e kadar yapılandırılabilir olarak geri alabilirsiniz.

- [Bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) , yapılandırılmış bekletme süresi boyunca e-postanın değişmez kopyalarını tutmanızı sağlar.

### <a name="encrypting-files-in-place"></a>Dosyaları yerinde şifreleme

Daha önce açıklandığı gibi, SharePoint ve OneDrive İş dosyaları aşağıdakiler ile kötü amaçlı şifrelemeye karşı korunur:

- Sürüm
- Geri dönüşüm kutusu
- Saklama kitaplığı

Ek ayrıntılar için bkz[. Verileri bozulmaya karşı Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kiracının dışına dosya kopyalama 

Bir fidye yazılımı yazılımına aşağıdakiler ile kiracının dışından dosya kopyalamasını önlebilirsiniz:

- [Veri Kaybı Önleme (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) ilkeleri

    Şunları içeren verileri algıla, uyarma ve engelleme, istemeden veya uygunsuz veri paylaşımı:

    - Bölgesel gizlilik düzenlemelerine uyumluluk için kişisel bilgiler (PII) gibi kişisel bilgiler.

    - Duyarlılık etiketlerine dayalı gizli kuruluş bilgileri.

- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)

    Dosyalar gibi hassas bilgilerin indirilmelerini engelin. 

    Ayrıca, bir kullanıcıyla uygulama arasındaki bilgi akışını [gerçek zamanlı olarak](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) izlemek için Bulut Uygulamaları için Defender Koşullu Erişim Uygulama Denetimi'nin oturum ilkelerini de kullanabilirsiniz.

## <a name="whats-in-this-solution"></a>Bu çözümde neler var?

Bu çözüm, fidye yazılımı saldırganlarının Microsoft 365 kiracısı içinde kritik verileri kullanma ve organizasyonlarınızı bir süre basılı tutma olanağını en aza indirmek için, Microsoft 365 koruma ve risk azaltma özelliklerinin, yapılandırmalarının ve devam eden işlemlerin dağıtımında size yol gösterir.

![Yazılımla fidye yazılımlarına karşı korunma Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

Bu çözümde adımlar şöyledir:

1. [Güvenlik taban çizgilerini yapılandırma](ransomware-protection-microsoft-365-security-baselines.md)
2. [Saldırı algılamayı ve yanıtı dağıtın](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Kimlikleri koruma](ransomware-protection-microsoft-365-identities.md)
4. [Cihazları koruma](ransomware-protection-microsoft-365-devices.md)
5. [Bilgileri koruma](ransomware-protection-microsoft-365-information.md)

Kiracınız için dağıtılan çözümün beş adımı Microsoft 365.

![Bir kiracı için fidye yazılımı Microsoft 365 koruma](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

Bu çözümde Sıfır Güven [İlkeleri temelleri ve kullanımı:](/security/zero-trust/) 

- **Açık bir şekilde doğrulama:** Her zaman kullanılabilir tüm veri noktalarına göre kimlik doğrulama ve yetkilendirme.
- **En az ayrıcalık erişimini kullanın:** Kullanıcı erişimini Just-In-Time ve Just-Enough-Access (JIT/JEA), risk tabanlı uyarlanabilir ilkeler ve veri koruması ile sınırlandırın.
- **İhlal varsayalım:** Yarıçap yarıçapını ve segment erişimini en aza indirgeyin. Ender şifrelemeyi doğrulayın ve görünürlük elde etmek, tehdit algılamayı geliştirmek ve savunmayı geliştirmek için çözümlemeleri kullanın.

Kuruluşun güvenlik duvarının arkasında bulunan her şeye güvenen alışılmış intranet erişiminden farklı olarak, Sıfır Güven her oturum açma ve erişime, kuruluş güvenlik duvarının arkasında ya da İnternet'te bulunan denetimsiz bir ağdan geliyor gibi davranır. Sıfır Güven ağ, altyapı, kimlikler, uç noktalar, uygulamalar ve veriler için koruma gerektirir.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 özellikleri ve özellikleri hakkında

Kiracınızı fidye Microsoft 365 saldırılarından korumak için çözümün bu Microsoft 365 bu özellikleri ve özelliklerini kullanın.

### <a name="1-security-baseline"></a>1. Güvenlik temeli

| Özellik veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Güvenli Puan |  Bir kiracının güvenlik Microsoft 365 ölçür. | Güvenlik yapılandırmanızı değerlendirin ve geliştirmeler önerir. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Saldırı yüzeyini azaltma kuralları | Çeşitli yapılandırma ayarları kullanarak kuruluş güvenlik açığını siber saldırılara karşı azaltır. | Şüpheli etkinliği ve korumasız içeriği engelin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Exchange-posta ayarlarını değiştirme |  E-posta tabanlı bir saldırıya karşı organizasyon güvenlik açığını azaltan hizmetlere olanak sağlar. | Kimlik avı ve diğer e-posta tabanlı saldırılar aracılığıyla kiracınıza ilk erişimi engelin.  | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Windows, Microsoft Edge ve Microsoft 365 Uygulamaları ayarları için Enterprise sağlar | Geniş bir şekilde bilinen ve iyi sınanmış endüstri standardı güvenlik yapılandırmaları sağlar. | Güvenlik için Windows, Edge ve Microsoft 365 Uygulamaları aracılığıyla Enterprise. | Microsoft 365 E3 veya Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Algılama ve yanıt

| Özellik veya özellik | Açıklama | Algılamaya ve yanıtlamaya yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Sinyal ve ek özellikler özelliklerini tek bir çözümde birleştirir. <br><br> Güvenlik uzmanlarının tehdit sinyallerini bir araya getirdir ve bir tehdidin tam kapsamını ve etkisini belirler. <br><br> Saldırıyı ve etkilenen kendi kendine etkilenen posta kutularını, uç noktaları ve kullanıcı kimliklerini önlemeye veya durdurmaya yönelik eylemleri otomatikleştirir. | Birleştirilmiş uyarılar ve saldırıyı neden olan veriler olan olaylar. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
| Kimlik için Microsoft Defender |  Bulut tabanlı bir güvenlik arabirimi aracılığıyla, şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) sinyallerini kullanarak, gelişmiş tehditleri, güvenliği tehlikeye kimlikleri ve kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırın. | AD DS hesapları için kimlik bilgilerinin güvenliği tehlikeye atabilirsiniz. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
| Office 365 için Microsoft Defender | E-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. <br><br> Kötü amaçlı yazılımlara, kimlik avına, kimlik sahtelerine ve diğer saldırı türlerine karşı koruma sağlar. | Kimlik avı saldırıları. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
| Uç Nokta için Microsoft Defender | Uç noktalar (cihazlar) genelinde gelişmiş tehditleri algılamayı ve buna yanıt verir. | Kötü amaçlı yazılım yüklemesi ve cihaz güvenliği tehlikeye atabilirsiniz. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
| Azure Active Directory (Azure AD) Kimlik Koruması | Kimlik tabanlı riskleri algılamayı ve düzeltmeyi, bu riskleri incelemeyi otomatik haleler. | Azure AD hesapları ve ayrıcalık yükseltmesi için kimlik bilgilerinin güvenliği güvenliği. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
| Bulut Uygulamaları için Defender | Tüm Microsoft ve üçüncü taraf bulut hizmetleriniz genelinde keşif, araştırma ve yönetim için bulut erişimi güvenlik aracısı. | Eşkenar hareket ve veri sızıntıları. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
|

### <a name="3-identities"></a>3. Kimlikler

| Özellik veya özellik | Açıklama | Önlemeye yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
|Azure AD Parola Koruması | Ortak bir listeden ve özel girişlerden parolaları engelin. | Bulut veya şirket içi kullanıcı hesabı parola belirlemesi. |Microsoft 365 E3 veya Microsoft 365 E5|
|Koşullu Erişim ile zorunlu kılınan MFA | Koşullu Erişim ilkeleriyle kullanıcı oturum açma özelliklerinin temel alarak MFA gerektirme. | Kimlik bilgilerinin güvenliği ve erişimin güvenliği tehlikeye at. | Microsoft 365 E3 veya Microsoft 365 E5|
|Risk tabanlı Koşullu Erişim ile zorunlu kılınan MFA | Azure AD Identity koruması ile kullanıcı oturum açma riski temel alarak MFA gerektirme. |Kimlik bilgilerinin güvenliği ve erişimin güvenliği tehlikeye at. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme|
|

### <a name="4-devices"></a>4. Cihazlar

Cihaz ve uygulama yönetimi için:

| Özellik veya özellik | Açıklama | Önlemeye yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Cihazları ve bu cihazlarda çalıştıran uygulamaları yönetin.  | Cihazın veya uygulamanın güvenliği ve erişimi tehlikeye atabilirsiniz. | Microsoft 365 E3 E5 |
|  |  |  |  |

11 Windows 10 cihaz için:

| Özellik veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Defender Güvenlik Duvarı | Ana bilgisayar tabanlı bir güvenlik duvarı sağlar.  | Gelen, talep edilmemiş ağ trafiğine karşı saldırılar engelin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Defender Virüsten Koruma | Makine öğrenimi, büyük veri çözümlemesi, derinlemesine tehdit direnci araştırması ve Microsoft bulut altyapısını kullanarak cihazlara (uç noktalar) kötü amaçlı yazılımdan koruma sağlar. | Kötü amaçlı yazılım yüklemesini ve çalıştırmayı engelin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Kimlik avına veya kötü amaçlı yazılım web sitelerine ve uygulamalara karşı koruma sağlar ve olası kötü amaçlı dosyaların indir indirebilirsiniz. | Siteleri, indirmeleri, uygulamaları ve dosyaları kontrol etmeye yönelik engelleme veya uyarıda bulunabilirsiniz. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Uç Nokta için Microsoft Defender | Cihazlar (uç noktalar) genelinde gelişmiş tehditleri önlemeye, algılamaya, araştırmaya ve yanıtlamaya yardımcı olur. | Ağ üzerinde oynanmaya karşı koruma. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
|  |  |  |  |

### <a name="5-information"></a>5. Bilgiler

| Özellik veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Denetimli klasör erişimi | Uygulamaları bilinen, güvenilen uygulamalar listesine karşı kontrol ederek verilerinizi korur. | Fidye yazılımları tarafından dosyaların değiştirilmesini veya şifrelenmelerini önle. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Bilgi Koruması | Duyarlılık etiketlerinin özelliği yüksek olan bilgilere uygulanıyor | Exfiltrated bilgisinin kullanımını engelin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Veri kaybı önleme (DLP) | Hassas verileri korur ve kullanıcıların uygunsuz şekilde paylaşmasını engelerek riski azaltır. | Veri sızıntısını önleme. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Bulut Uygulamaları için Defender | Bulma, araştırma ve yönetim için bulut erişimi güvenlik aracısı. | Eşkenar hareketi algıla ve veri sızıntısını önle. | Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik ekleme |
|

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar üzerindeki etkisi ve değişiklik yönetimi

Kiracınız için ek güvenlik özellikleri dağıtmak, gereksinimleri ve güvenlik Microsoft 365 uygulamak kullanıcılarınızı etkileyenin. 

Örneğin, kuruluşta tüm kullanıcılar için daha kolay bir ekip oluşturmak yerine, kullanıcı hesaplarının listesini üye olarak kullanan belirli kullanımlar için kullanıcıların yeni ekipler oluşturmalarını gerektiren yeni bir güvenlik ilkesi benimseyebilirsiniz. Bu, bir fidye yazılımı saldırganların güvenliği tehlikeye atılmış kullanıcı hesabında yer alan ekipleri keşfetmesini ve sonraki saldırıda o ekibin kaynaklarını hedefley keşfetmesini önlemeye yardımcı olabilir.

Bu temel çözüm, yeni yapılandırmaların veya önerilen güvenlik ilkelerinin kullanıcılarınızı ne zaman etkiley olduğunu belirleyecek ve böylelikle gerekli değişiklik yönetimini gerçekleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Kiracınıza kapsamlı bir koruma dağıtmak için bu Microsoft 365 kullanın:

1. [Güvenlik taban çizgilerini yapılandırma](ransomware-protection-microsoft-365-security-baselines.md)
2. [Saldırı algılamayı ve yanıtı dağıtın](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Kimlikleri koruma](ransomware-protection-microsoft-365-identities.md)
4. [Cihazları koruma](ransomware-protection-microsoft-365-devices.md)
5. [Bilgileri koruma](ransomware-protection-microsoft-365-information.md)

[![Yazılımla fidye yazılımına karşı 1. Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Ek fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Giderek büyüyen fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/) olan Microsoft 20 Temmuz 2021'de Sorunlar blog gönderisi
- [İnsan tarafından işletilen fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımlarına ve ekstörlere karşı hızlı bir şekilde koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (sayfa 10-19'a bakın)
- [Fidye yazılımı: Microsoft 365 Defender portalında periveive](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) ve sürekli tehdit Microsoft 365 Defender raporu
- Microsoft'un Algılama ve Yanıt Ekibi (ATL) fidye yazılımı [yaklaşımı, en iyi yöntemler ve](/security/compass/incident-response-playbook-dart-ransomware-approach) örnek [olay inceleme](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımı saldırılarından kurtar](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Kötü amaçlı yazılım ve fidye yazılımına karşı koruma](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Bilgisayarınızın Windows 10 fidye yazılımlarından koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Yazılım portalında fidye yazılımı](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) için tehdit Microsoft 365 Defender raporları

Microsoft 365 Defender:

- [Gelişmiş avla fidye yazılımı bulun](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Fidye Yazılımı Saldırısını Azure Savunma](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı korunmak için planı yedekleme ve geri yükleme](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Yedekleme ile fidye yazılımlarından korunmaya](https://www.youtube.com/watch?v=VhLOr2_1MCg) yardımcı olun (26 dakikalık video)
- [Sistemsel kimlik güvenliğinden ödün verme](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok amaçlı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fidye Yazılımı Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Bulut Uygulamaları için Microsoft Defender:

-  [Bulut Uygulamaları için Defender'da anormal algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önlemeye ve fidye yazılımlarından korunmaya yönelik 3 adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından işletilen fidye yazılımlarla mücadeleye yardımcı bir kılavuz: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (YERMİ) fidye yazılımı olayı soruşturmalarını nasıl yönetecekleri ile ilgili önemli adımlar.

- [İnsan tarafından işletilen fidye yazılımıyla mücadeleye kılavuz: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayan giderek daha iyi hale geliyor: Bölüm 4: mevcut tehditlerle gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Fidye yazılımı **bölümüne** bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırılar için saldırı zinciri çözümlemeleri içerir.

- [Fidye yazılımına yanıt— ödeme yapmak veya ödeme yapmak değil mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk 365 Fidye yazılımı saldırılarına saydamlık saldırısıyla yanıt verdi (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
