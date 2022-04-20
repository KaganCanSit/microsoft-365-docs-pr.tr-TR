---
title: Microsoft 365 kiracınız için fidye yazılımı koruması dağıtın
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
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
keywords: fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, HumOR, gasp saldırısı, fidye yazılımı saldırısı, şifreleme, kriptoviroloji, sıfır güven
description: Microsoft 365 kaynaklarınızı fidye yazılımı saldırılarına karşı koruma adımlarını atın.
ms.openlocfilehash: fde24132341512d76467284cb2f9c9b11b7d88cc
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943249"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Microsoft 365 kiracınız için fidye yazılımı koruması dağıtın

Fidye yazılımı, dosyaları ve klasörleri yok eden veya şifreleyen ve kritik verilere erişimi engelleyen bir tür gasp saldırısıdır. Ticari fidye yazılımı genellikle cihazlara bulaşan ve yalnızca kötü amaçlı yazılım düzeltmesi gerektiren bir virüs gibi yayılır. İnsan tarafından çalıştırılan fidye yazılımı, bir kuruluşun şirket içine veya bulut BT altyapısına sızan, ayrıcalıklarını yükselten ve kritik verilere fidye yazılımı dağıtan siber suçluların etkin bir saldırısının sonucudur.

Saldırı tamamlandıktan sonra, saldırgan silinen dosyalar, şifrelenmiş dosyalar için şifre çözme anahtarları veya gizli verileri karanlık web'e veya genel İnternet'e bırakmama sözü karşılığında kurbanlardan para ister. İnsan tarafından çalıştırılan fidye yazılımı, endüstriyel üretim için gerekli olanlar gibi kritik makineleri veya süreçleri kapatmak, fidye ödenene ve hasar düzeltilene kadar normal iş operasyonlarını durmaya getirmek veya kuruluş zararı kendileri düzeltmek için de kullanılabilir.

İnsan tarafından işletilen bir fidye yazılımı saldırısı, her büyüklükteki işletmeler için yıkıcı olabilir ve temizlenmesi zor olabilir ve gelecekteki saldırılara karşı koruma sağlamak için tam saldırgan çıkarma gerektirir. Ticari fidye yazılımlarının aksine, insan tarafından çalıştırılan fidye yazılımı ilk fidye isteğinden sonra işletme işlemlerini tehdit etmeye devam edebilir.

>[!Note]
>bir Microsoft 365 kiracısına yönelik fidye yazılımı saldırısı, saldırganın bir kiracı için geçerli kullanıcı hesabı kimlik bilgilerine sahip olduğunu ve kullanıcı hesabına izin verilen tüm dosya ve kaynaklara erişimi olduğunu varsayar. Geçerli kullanıcı hesabı kimlik bilgileri olmayan bir saldırganın bekleyen verilerin şifresini çözmesi Microsoft 365 varsayılan ve gelişmiş şifreleme ile şifrelenir. Daha fazla bilgi için bkz [. Şifreleme ve anahtar yönetimine genel bakış](/compliance/assurance/assurance-encryption). 
>

Microsoft ürünleri genelinde fidye yazılımı koruması hakkında daha fazla bilgi için bu [ek fidye yazılımı kaynaklarına](#additional-ransomware-resources) bakın.

## <a name="security-in-the-cloud-is-a-partnership"></a>Bulutta güvenlik bir iş ortaklığıdır

Microsoft bulut hizmetlerinizin güvenliği, sizinle Microsoft arasındaki bir ortaklıktır:

- Microsoft bulut hizmetleri, güven ve güvenlik temeli üzerine kurulmuştur. Microsoft, verilerinizi ve uygulamalarınızı korumanıza yardımcı olacak güvenlik denetimleri ve özellikleri sağlar.
- Verilerinize ve kimliklerinize ve bunları koruma sorumluluğuna, şirket içi kaynaklarınızın güvenliğine ve denetlediğiniz bulut bileşenlerinin güvenliğine sahip olursunuz.

Bu özellikleri ve sorumlulukları birleştirerek fidye yazılımı saldırısına karşı en iyi korumayı sağlayabiliriz.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Microsoft 365 ile sağlanan fidye yazılımı azaltma ve kurtarma özellikleri

bir Microsoft 365 kiracıya sızan bir fidye yazılımı saldırganı, kuruluşunuzu fidye için şu şekilde tutabilir:

- Dosyaları veya e-postayı silme
- Dosyaları şifreleme yerinde
- Kiracınızın dışına dosya kopyalama (veri sızdırma)

Ancak Microsoft 365 çevrimiçi hizmetler, müşteri verilerini fidye yazılımı saldırılarına karşı korumak için birçok yerleşik özelliğe ve denetime sahiptir. Aşağıdaki bölümlerde bir özet sağlanır. Microsoft'un [Microsoft 365'da müşteri verilerini, Kötü amaçlı yazılım ve fidye yazılımı korumasını](/compliance/assurance/assurance-malware-and-ransomware-protection) nasıl koruduğu hakkında daha fazla bilgi için.

>[!Note]
>bir Microsoft 365 kiracısına yönelik fidye yazılımı saldırısı, saldırganın bir kiracı için geçerli kullanıcı hesabı kimlik bilgilerine sahip olduğunu ve kullanıcı hesabına izin verilen tüm dosya ve kaynaklara erişimi olduğunu varsayar. Geçerli kullanıcı hesabı kimlik bilgileri olmayan bir saldırganın bekleyen verilerin şifresini çözmesi Microsoft 365 varsayılan ve gelişmiş şifreleme ile şifrelenir. Daha fazla bilgi için bkz [. Şifreleme ve anahtar yönetimine genel bakış](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Dosyaları veya e-postayı silme

SharePoint ve OneDrive İş dosyaları şunlarla korunur:

- Sürüm 

   Microsoft 365 varsayılan olarak bir dosyanın en az 500 sürümünü korur ve daha fazlasını korumak için yapılandırılabilir. 

   Güvenlik ve yardım masası personelinizin yükünü en aza indirmek için kullanıcılarınızı [dosyaların önceki sürümlerini geri yükleme konusunda eğitin](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Geri dönüşüm kutusu

   Fidye yazılımı dosyanın yeni bir şifrelenmiş kopyasını oluşturur ve eski dosyayı silerse, müşterilerin geri dönüşüm kutusundan geri yüklemek için 93 günü vardır. 93 gün sonra, Microsoft'un verileri hala kurtarabileceği 14 günlük bir süre vardır. 
  
   Güvenlik ve yardım masası personelinizin yükünü en aza indirmek için kullanıcılarınızı [geri dönüşüm kutusundan dosyaları geri yükleme konusunda eğitin](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Dosyaları Geri Yükleme](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   SharePoint ve OneDrive için, yöneticilerin ve son kullanıcıların son 30 gün içinde herhangi bir noktadan dosyaları geri yüklemesine olanak tanıyan eksiksiz bir self servis kurtarma çözümü.

   Güvenlik ve BT yardım masası personelinizin yükünü en aza indirmek için kullanıcılarınızı [Dosyalar Geri Yükleme](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15) konusunda eğitin.


OneDrive ve SharePoint dosyaları için, toplu bir saldırıyla çarpılırsanız Microsoft 14 güne kadar önceki bir noktaya geri dönebilir.

E-posta şu şekilde korunur:

- Yanlışlıkla veya kötü amaçlı erken silme işleminden sonra bir posta kutusunda öğeleri kurtarabileceğiniz [tek öğe kurtarma](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) ve posta kutusu saklama. Varsayılan olarak 14 gün içinde silinen ve 30 güne kadar yapılandırılabilen posta iletilerini geri alabilirsiniz.

- [Bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) , yapılandırılan saklama süresi boyunca e-postanın sabit kopyalarını saklamanıza olanak sağlar.

### <a name="encrypting-files-in-place"></a>Dosyaları şifreleme yerinde

Daha önce açıklandığı gibi, SharePoint ve OneDrive İş dosyaları aşağıdakilerle kötü amaçlı şifrelemeye karşı korunur:

- Sürüm
- Geri dönüşüm kutusu
- Koruma Bekletme kitaplığı

Ek ayrıntılar için bkz[. Microsoft 365'de veri bozulmasıyla ilgilenme](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kiracınızın dışına dosya kopyalama 

Fidye yazılımı saldırganlarının kiracınızın dışındaki dosyaları kopyalamasını şu yöntemle engelleyebilirsiniz:

- [Microsoft Purview Veri Kaybı Önleme (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) ilkeleri

    Aşağıdakileri içeren verilerin riskli, yanlışlıkla veya uygunsuz paylaşımını algılama, uyarma ve engelleme:

    - Bölgesel gizlilik düzenlemelerine uyum için kişisel olarak tanımlayıcı bilgiler (PII) gibi kişisel bilgiler.

    - Duyarlılık etiketlerine dayalı gizli kuruluş bilgileri.

- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)

    Dosyalar gibi hassas bilgilerin indirilmelerini engelleyin. 

    Ayrıca Bulut için Defender [Uygulamaları Koşullu Erişim Uygulama Denetimi](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) için oturum ilkelerini kullanarak kullanıcıyla uygulama arasındaki bilgi akışını gerçek zamanlı olarak izleyebilirsiniz.

## <a name="whats-in-this-solution"></a>Bu çözümde neler var?

Bu çözüm, fidye yazılımı saldırganlarının Microsoft 365 kiracınızdaki kritik verileri kullanma ve kuruluşunuzu fidye için tutma becerisini en aza indirmek için Microsoft 365 koruma ve azaltma özellikleri, yapılandırmaları ve devam eden işlemlerin dağıtımında size yol gösterir.

![Microsoft 365 ile fidye yazılımlarına karşı koruma adımları](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

Bu çözümdeki adımlar şunlardır:

1. [Güvenlik temel hatlarını yapılandırın](ransomware-protection-microsoft-365-security-baselines.md)
2. [Saldırı algılama ve yanıt dağıtın](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Kimlikleri koruyun](ransomware-protection-microsoft-365-identities.md)
4. [Cihazları koruyun](ransomware-protection-microsoft-365-devices.md)
5. [Bilgileri koruma](ransomware-protection-microsoft-365-information.md)

Microsoft 365 kiracınız için dağıtılan çözümün beş adımı aşağıdadır.

![Microsoft 365 kiracı için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

Bu çözüm[, Sıfır Güven](/security/zero-trust/) ilkelerini kullanır: 

- **Açıkça doğrula:** Kullanılabilir tüm veri noktalarına göre her zaman kimlik doğrulaması ve yetkilendirme.
- **En az ayrıcalık erişimi kullanın:** Tam Zamanında ve Yeterli Erişim (JIT/JEA), risk tabanlı uyarlamalı ilkeler ve veri koruması ile kullanıcı erişimini sınırlayın.
- **İhlal olduğunu varsay:** Patlama yarıçapı ve segment erişimini en aza indirin. Uçtan uca şifrelemeyi doğrulayın ve görünürlük elde etmek, tehdit algılamayı yönlendirmek ve savunmaları geliştirmek için analizi kullanın.

Bir kuruluşun güvenlik duvarının arkasındaki her şeye güvenen geleneksel intranet erişiminin aksine, Sıfır Güven her oturum açma ve erişimi kuruluş güvenlik duvarının arkasında veya İnternet'te olduğu gibi denetimsiz bir ağdan geliyormuş gibi davranır. Sıfır Güven ağ, altyapı, kimlikler, uç noktalar, uygulamalar ve veriler için koruma gerektirir.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 özellikleri ve özellikleri

Microsoft 365 kiracınızı fidye yazılımı saldırılarına karşı korumak için çözümdeki bu adımlara yönelik bu Microsoft 365 özelliklerini ve özelliklerini kullanın.

### <a name="1-security-baseline"></a>1. Güvenlik temeli

| Yetenek veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Güvenlik Puanı |  bir Microsoft 365 kiracısının güvenlik duruşunu ölçer. | Güvenlik yapılandırmanızı değerlendirin ve iyileştirmeler önerin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Saldırı yüzeyini azaltma kuralları | Çeşitli yapılandırma ayarlarını kullanarak kuruluşunuzun siber saldırılara karşı güvenlik açığını azaltır. | Şüpheli etkinlikleri ve güvenlik açığı olan içeriği engelleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| E-posta ayarlarını Exchange |  Kuruluşunuzun güvenlik açığını e-posta tabanlı bir saldırıyla azaltan hizmetlere olanak tanır. | Kimlik avı ve diğer e-posta tabanlı saldırılar aracılığıyla kiracınıza ilk erişimi engelleyin.  | Microsoft 365 E3 veya Microsoft 365 E5 |
| Enterprise ayarları için Microsoft Windows, Microsoft Edge ve Microsoft 365 Uygulamaları | Yaygın olarak bilinen ve iyi test edilmiş endüstri standardı güvenlik yapılandırmaları sağlar. | Enterprise için Windows, Edge ve Microsoft 365 Uygulamaları üzerinden saldırıları önleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Algılama ve yanıt

| Yetenek veya özellik | Açıklama | Algılamaya ve yanıtlamaya yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Sinyalleri birleştirir ve özellikleri tek bir çözümde düzenler. <br><br> Güvenlik uzmanlarının tehdit sinyallerini birleştirmesini ve bir tehdidin tam kapsamını ve etkisini belirlemesini sağlar. <br><br> Saldırıyı önleme veya durdurma eylemlerini otomatikleştirir ve etkilenen posta kutularını, uç noktaları ve kullanıcı kimliklerini kendi kendine iyileştirir. | Saldırıları oluşturan birleşik uyarılar ve veriler olan olaylar. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
| Kimlik için Microsoft Defender |  Bulut tabanlı bir güvenlik arabirimi aracılığıyla kuruluşunuza yönlendirilen gelişmiş tehditleri, güvenliği aşılmış kimlikleri ve kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırır şirket içi Active Directory Domain Services (AD DS) sinyallerinizi kullanır. | AD DS hesapları için kimlik bilgisi güvenliğinin aşılmasına neden olur. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
| Office 365 için Microsoft Defender | Kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya konan kötü amaçlı tehditlere karşı korur. <br><br> Kötü amaçlı yazılımlara, kimlik avına, kimlik sahtekarlığına ve diğer saldırı türlerine karşı koruma sağlar. | Kimlik avı saldırıları. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
| Uç Nokta için Microsoft Defender | Uç noktalar (cihazlar) genelindeki gelişmiş tehditleri algılamayı ve yanıtlamayı etkinleştirir. | Kötü amaçlı yazılım yükleme ve cihaz güvenliğinin aşılmasına neden olur. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
| Azure Active Directory (Azure AD) Kimlik Koruması | Kimlik tabanlı riskleri algılamayı ve düzeltmeyi ve bu risklerin araştırılması işlemini otomatikleştirir. | Azure AD hesapları ve ayrıcalık yükseltmesi için kimlik bilgisi güvenliğinin aşılması. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
| Bulut Uygulamaları için Defender | Tüm Microsoft ve üçüncü taraf bulut hizmetlerinizde bulma, araştırma ve idare için bir bulut erişim güvenlik aracısı. | Yanal hareket ve veri sızdırma. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
|

### <a name="3-identities"></a>3. Kimlikler

| Yetenek veya özellik | Açıklama | Önlemeye yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
|Azure AD Parola Koruması | Ortak bir listeden ve özel girdilerden parolaları engelleyin. | Bulut veya şirket içi kullanıcı hesabı parola belirleme. |Microsoft 365 E3 veya Microsoft 365 E5|
|Koşullu Erişim ile zorunlu kılınan MFA | Koşullu Erişim ilkeleriyle kullanıcı oturum açma özelliklerinin temelinde MFA gerektirme. | Kimlik bilgisi güvenliğinin aşılmasına ve erişime. | Microsoft 365 E3 veya Microsoft 365 E5|
|Risk tabanlı Koşullu Erişim ile zorunlu kılınan MFA | Azure AD Kimlik koruması ile kullanıcı oturum açma riskine bağlı olarak MFA gerektirme. |Kimlik bilgisi güvenliğinin aşılmasına ve erişime. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3|
|

### <a name="4-devices"></a>4. Cihazlar

Cihaz ve uygulama yönetimi için:

| Yetenek veya özellik | Açıklama | Önlemeye yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Cihazları ve üzerinde çalışan uygulamaları yönetin.  | Cihaz veya uygulama güvenliğinin aşılmasına ve erişime. | Microsoft 365 E3 veya E5 |
|  |  |  |  |

Windows 11 veya 10 cihaz için:

| Yetenek veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Microsoft Defender Güvenlik Duvarı | Konak tabanlı bir güvenlik duvarı sağlar.  | Gelen ve istenmeyen ağ trafiğinden gelen saldırıları önleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Defender Virüsten Koruma | Makine öğrenmesi, büyük veri analizi, derinlemesine tehdit direnci araştırması ve Microsoft bulut altyapısını kullanarak cihazların (uç noktalar) kötü amaçlı yazılımdan korumasını sağlar. | Kötü amaçlı yazılımların yüklenmesini ve çalıştırılmasını önleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Kimlik avına veya kötü amaçlı yazılım web sitelerine ve uygulamalarına ve kötü amaçlı olabilecek dosyaların indirilmesine karşı koruma sağlar. | Siteleri, indirmeleri, uygulamaları ve dosyaları denetlerken engelleyin veya uyarın. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Uç Nokta için Microsoft Defender | Cihazlar (uç noktalar) genelindeki gelişmiş tehditleri önlemeye, algılamaya, araştırmaya ve yanıtlamaya yardımcı olur. | Ağ üzerinde oynanmaya karşı koruma sağlayın. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
|  |  |  |  |

### <a name="5-information"></a>5. Bilgi

| Yetenek veya özellik | Açıklama | Yardımcı olur... | Lisanslama |
|:-------|:-----|:-------|:-------|
| Denetimli klasör erişimi | Uygulamaları bilinen, güvenilen uygulamalar listesine karşı denetleyerek verilerinizi korur. | Dosyaların fidye yazılımı tarafından değiştirilmesini veya şifrelenmesini önleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Microsoft Purview Information Protection | Fidye için kullanılabilir bilgilere duyarlılık etiketlerinin uygulanmasını sağlar | Dosyadan çıkarılmış bilgilerin kullanımını önleme. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Veri kaybı önleme (DLP) | Hassas verileri korur ve kullanıcıların uygunsuz bir şekilde paylaşmasını engelleyerek riski azaltır. | Veri sızdırmayı önleyin. | Microsoft 365 E3 veya Microsoft 365 E5 |
| Bulut Uygulamaları için Defender | Bulma, araştırma ve idare için bir bulut erişimi güvenlik aracısı. | Yanal hareketi algılayın ve veri sızdırmayı önleyin. | Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3 |
|

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar ve değişiklik yönetimi üzerindeki etkisi

Microsoft 365 kiracınız için ek güvenlik özellikleri dağıtmak ve gereksinimleri ve güvenlik ilkelerini uygulamak kullanıcılarınızı etkileyebilir. 

Örneğin, kullanıcıların kuruluştaki tüm kullanıcılar için daha kolay bir ekip oluşturmak yerine üye olarak kullanıcı hesaplarının listesiyle belirli kullanımlar için yeni ekipler oluşturmasını gerektiren yeni bir güvenlik ilkesi uygulayabilirsiniz. Bu, fidye yazılımı saldırganlarının güvenliği aşılmış kullanıcı hesabı için kullanılamayan ekipleri keşfetmesini ve sonraki saldırıda bu ekibin kaynaklarını hedeflemesini önlemeye yardımcı olabilir.

Bu temel çözüm, gerekli değişiklik yönetimini gerçekleştirebilmeniz için yeni yapılandırmaların veya önerilen güvenlik ilkelerinin kullanıcılarınızı ne zaman etkileyebileceğini belirler.

## <a name="next-steps"></a>Sonraki adımlar

Microsoft 365 kiracınız için kapsamlı koruma dağıtmak için şu adımları kullanın:

1. [Güvenlik temel hatlarını yapılandırın](ransomware-protection-microsoft-365-security-baselines.md)
2. [Saldırı algılama ve yanıt dağıtın](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Kimlikleri koruyun](ransomware-protection-microsoft-365-identities.md)
4. [Cihazları koruyun](ransomware-protection-microsoft-365-devices.md)
5. [Bilgileri koruma](ransomware-protection-microsoft-365-information.md)

[![Microsoft 365 ile fidye yazılımı koruması için 1. Adım](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Ek fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Artan fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog gönderisi 20 Temmuz 2021'de
- [İnsan tarafından çalıştırılan fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımı ve gaspa karşı hızla koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (bkz. sayfa 10-19)
- [Fidye yazılımı: Microsoft 365 Defender portalında sürekli ve sürekli tehdit tehdit](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) analizi raporu
- Microsoft'un Algılama ve Yanıt Ekibi (DART) fidye yazılımı [yaklaşımı ve en iyi yöntemler](/security/compass/incident-response-playbook-dart-ransomware-approach) ve [örnek olay incelemesi](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımı saldırısından kurtarma](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Kötü amaçlı yazılım ve fidye yazılımı koruması](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Windows 10 bilgisayarınızı fidye yazılımlarından koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- Microsoft 365 Defender portalında [fidye yazılımı için tehdit analizi raporları](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag)

Microsoft 365 Defender:

- [Gelişmiş avcılık ile fidye yazılımı bulma](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Fidye Yazılımı Saldırısı için Azure Defenses](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı koruma sağlamak için yedekleme ve geri yükleme planı](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Backup ile fidye yazılımlarından korunmaya yardımcı olun](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 dakikalık video)
- [Sistemik kimlik güvenliğinin aşılmasından kurtarma](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok aşamalı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fusion Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Bulut için Defender Uygulamalarında anomali algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önleme ve kurtarma için 3 adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (DART) fidye yazılımı olay araştırmalarını nasıl yürüttüğüne ilişkin temel adımlar.

- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayarak dayanıklı hale gelme: Bölüm 4— Mevcut tehditlerde gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  **Fidye yazılımı** bölümüne bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırıların saldırı zinciri analizlerini içerir.

- [Fidye yazılımı yanıtı— ödeme yapmak için mi yoksa ödememek için mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro fidye yazılımı saldırısına şeffaflıkla yanıt veriyor (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
