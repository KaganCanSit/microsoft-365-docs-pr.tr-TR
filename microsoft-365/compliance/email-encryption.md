---
title: Microsoft 365'te e-posta şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: c0d87cbe-6d65-4c03-88ad-5216ea5564e8
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Microsoft Purview İleti Şifrelemesi, S/MIME, Bilgi Hakları Yönetimi (IRM) gibi Microsoft 365 şifreleme seçeneklerini karşılaştırın ve Aktarım Katmanı Güvenliği (TLS) hakkında bilgi edinin.
ms.openlocfilehash: a5541c9a1478d1eb1add40a5aecb7439d1442e1b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624255"
---
# <a name="email-encryption"></a>E-posta şifreleme

Bu makalede Microsoft Purview İleti Şifrelemesi, S/MIME, Bilgi Hakları Yönetimi (IRM) dahil olmak üzere Microsoft 365'teki şifreleme seçenekleri karşılaştırılarak Aktarım Katmanı Güvenliği (TLS) tanıtıldı.
  
Microsoft 365, e-posta güvenliği için iş gereksinimlerinizi karşılamanıza yardımcı olmak için birden çok şifreleme seçeneği sunar. Bu makalede e-postayı Office 365 şifrelemenin üç yolu verilmiştir. Office 365'daki tüm güvenlik özellikleri hakkında daha fazla bilgi edinmek istiyorsanız [Office 365 Güven Merkezi'ni ziyaret edin](https://go.microsoft.com/fwlink/p/?LinkID=282470). Bu makalede, Office 365'da e-postanın güvenliğini sağlamaya yardımcı olmak için Microsoft 365 yöneticilerinin kullanabileceği üç şifreleme türü tanıtilmektedir:
  
- Microsoft Purview İleti Şifrelemesi.

- Güvenli/Çok Amaçlı İnternet Posta Uzantıları (S/MIME).

- Bilgi Hakları Yönetimi (IRM).

## <a name="how-microsoft-365-uses-email-encryption"></a>Microsoft 365 e-posta şifrelemesini nasıl kullanır?

Şifreleme, bilgilerin kodlandığı ve yalnızca yetkili bir alıcının bilgilerin kodunu çözebileceği ve kullanabileceği işlemdir. Microsoft 365 şifrelemeyi iki şekilde kullanır: hizmette ve müşteri denetimi olarak. Hizmette şifreleme varsayılan olarak Microsoft 365'te kullanılır; hiçbir şeyi yapılandırmanız gerekmez. Örneğin, Microsoft 365 iki sunucu arasındaki bağlantıyı veya oturumu şifrelemek için Aktarım Katmanı Güvenliği'ni (TLS) kullanır. 
  
E-posta şifrelemesi genellikle şu şekilde çalışır:
  
- İleti, gönderenin makinesinde veya ileti aktarımdayken merkezi bir sunucu tarafından şifrelenir veya düz metinden okunamaz şifreleme metnine dönüştürülür.

- İletinin kesilmesi durumunda okunmasını engellemek için ileti aktarım sırasında şifre metninde kalır.

- İleti alıcı tarafından alındıktan sonra, ileti iki yoldan biriyle okunabilir düz metne dönüştürülür:

  - Alıcının makinesi iletinin şifresini çözmek için bir anahtar kullanır veya

  - Merkezi sunucu, alıcının kimliğini doğruladıktan sonra iletinin şifresini alıcı adına çözer.

Microsoft 365'in, Microsoft 365 içindeki kuruluşlar veya Microsoft 365 dışındaki güvenilir bir iş ortağı arasında olduğu gibi sunucular arasındaki iletişimi nasıl güvenli hale getireceği hakkında daha fazla bilgi için bkz. [Exchange Online, Office 365'da e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır](exchange-online-uses-tls-to-secure-email-connections.md)?
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Office 365'de kullanılabilen e-posta şifreleme seçeneklerini karşılaştırma

|E-posta şifreleme teknolojisi|![OME'nin açıklandığı kavramsal resim.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![IRM'nin açıklandığı kavramsal resim](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![SMIME'i açıklayan kavramsal resim](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Nedir o?|İleti şifrelemesi, hedef e-posta adresinden (Gmail, Yahoo! ) bağımsız olarak kuruluşunuzun içindeki veya dışındaki kişilere şifrelenmiş e-posta göndermenizi sağlayan, Azure Rights Management (Azure RMS) üzerinde oluşturulmuş bir hizmettir Posta, Outlook.com vb.). <br/> Yönetici olarak, şifreleme koşullarını tanımlayan aktarım kuralları ayarlayabilirsiniz. Kullanıcı bir kuralla eşleşen bir ileti gönderdiğinde şifreleme otomatik olarak uygulanır. <br/> Şifrelenmiş iletileri görüntülemek için alıcılar tek seferlik geçiş kodu alabilir, Microsoft hesabıyla oturum açabilir veya Office 365 ile ilişkilendirilmiş bir iş veya okul hesabıyla oturum açabilir. Alıcılar şifrelenmiş yanıtlar da gönderebilir. Şifrelenmiş iletileri görüntülemek veya şifrelenmiş yanıtlar göndermek için Microsoft 365 aboneliği gerekmez.|IRM, e-posta iletilerine kullanım kısıtlamaları da uygulayan bir şifreleme çözümüdür. Hassas bilgilerin yetkisiz kişiler tarafından yazdırılmasını, iletilmesini veya kopyalanmasını önlemeye yardımcı olur. <br/> Microsoft 365'teki IRM özellikleri Azure Rights Management 'ı (Azure RMS) kullanır.|S/MIME, bir iletiyi hem şifrelemenize hem de dijital olarak imzalamanıza olanak tanıyan sertifika tabanlı bir şifreleme çözümüdür. İleti şifrelemesi, yalnızca hedeflenen alıcının iletiyi açıp okuyabilmesine yardımcı olur. Dijital imza, alıcının gönderenin kimliğini doğrulamasına yardımcı olur. <br/> Hem dijital imzalar hem de ileti şifrelemesi, dijital imzaları doğrulamak ve iletileri şifrelemek veya şifresini çözmek için anahtarları içeren benzersiz dijital sertifikaların kullanılmasıyla mümkün hale getirilir. <br/> S/MIME kullanmak için, her alıcı için dosyada ortak anahtarlar olmalıdır. Alıcıların kendi özel anahtarlarını korumaları gerekir ve bu anahtarların güvenli kalması gerekir. Alıcının özel anahtarları tehlikeye girerse, alıcının yeni bir özel anahtar alması ve ortak anahtarları tüm olası gönderenlere yeniden dağıtması gerekir.|
|Ne işe yarıyor?|OME: <br/> İç veya dış alıcılara gönderilen iletileri şifreler. <br/>  Kullanıcıların Outlook.com, Yahoo! dahil olmak üzere herhangi bir e-posta adresine şifreli iletiler göndermesine izin verir Posta ve Gmail. <br/>  Yönetici olarak e-posta görüntüleme portalını kuruluşunuzun markasını yansıtacak şekilde özelleştirmenize olanak tanır. <br/> Microsoft anahtarları güvenli bir şekilde yönetir ve depolar, bu nedenle bunu yapmak zorunda değilsiniz. <br/> Şifrelenmiş ileti (HTML eki olarak gönderilir) tarayıcıda açılabilmesi sürece özel istemci tarafı yazılımı gerekmez.|IRM: <br/> E-posta iletileri ve ekleri için çevrimiçi ve çevrimdışı koruma sağlamak için şifreleme ve kullanım kısıtlamalarını kullanır. <br/> Yönetici olarak, ileti seçmek için IRM'yi otomatik olarak uygulamak için aktarım kuralları veya Outlook koruma kuralları ayarlama olanağı sağlar. <br/> Kullanıcıların Şablonları Outlook'ta veya Web üzerinde Outlook (eski adıyla Outlook Web App) el ile uygulamasına olanak tanır.|S/MIME, dijital imzalarla gönderen kimlik doğrulamasını ve şifreleme ile ileti gizliliğini adresler.|
|Ne işe yarmıyor?|OME, iletilere kullanım kısıtlamaları uygulamanıza izin vermez. Örneğin, bir alıcının şifreli iletiyi iletmesini veya yazdırmasını durdurmak için bunu kullanamazsınız.|Bazı uygulamalar tüm cihazlarda IRM e-postalarını desteklemeyebilir. Bunlar ve IRM e-postasını destekleyen diğer ürünler hakkında daha fazla bilgi için bkz. [İstemci cihazı özellikleri](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME, şifrelenmiş iletilerin kötü amaçlı yazılım, istenmeyen posta veya ilkeler için taranmasına izin vermez.|
|Öneriler ve örnek senaryolar|İster tüketici ister diğer işletmeler olsun, kuruluşunuzun dışındaki kişilere hassas iş bilgileri göndermek istediğinizde OME kullanmanızı öneririz. Örneğin:  <br/>  Müşterilere kredi kartı ekstreleri gönderen bir banka çalışanı  <br/>  Doktor muayenehanesi hastaya tıbbi kayıtlar gönderiyor  <br/>  Gizli yasal bilgileri başka bir avukata gönderen bir avukat|Şifrelemenin yanı sıra kullanım kısıtlamalarını uygulamak istediğinizde IRM kullanmanızı öneririz. Örneğin:  <br/>  Ekibine yeni bir ürünle ilgili gizli ayrıntılar gönderen bir yönetici "İletme" seçeneğini uygular.  <br/>  Bir yöneticinin, Office 365 kullanan bir iş ortağının ekini içeren ve hem e-postanın hem de ekin korunmasını gerektiren bir teklif teklifini başka bir şirketle paylaşması gerekir.|Kuruluşunuz veya alıcının kuruluşu gerçek eşler arası şifreleme gerektirdiğinde S/MIME kullanmanızı öneririz.  <br/>  S/MIME en yaygın olarak aşağıdaki senaryolarda kullanılır:  <br/>  Diğer devlet kurumlarıyla iletişim kurarak kamu kurumları  <br/>  Bir kamu kuruluşuyla iletişim kurarak bir işletme|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Microsoft 365 aboneliğim için hangi şifreleme seçenekleri kullanılabilir?

Microsoft 365 aboneliğinizin e-posta şifreleme seçenekleri hakkında bilgi için [Exchange Online hizmet açıklamasına](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) bakın. Burada, aşağıdaki şifreleme özellikleri hakkında bilgi bulabilirsiniz:
  
- Hem IRM özellikleri hem de Microsoft Purview İleti Şifrelemesi dahil olmak üzere Azure RMS

- S/MIME

- TLS

- Bekleyen verilerin şifrelenmesi (BitLocker aracılığıyla)

Üçüncü taraf şifreleme araçlarını Microsoft 365 ile de kullanabilirsiniz; örneğin, PGP (Oldukça İyi Gizlilik). Microsoft 365 PGP/MIME'yi desteklemez ve PGP/Inline'ı yalnızca PGP ile şifrelenmiş e-posta gönderip almak için kullanabilirsiniz.

## <a name="what-about-encryption-for-data-at-rest"></a>Bekleyen veriler için şifreleme ne olacak?

"Bekleyen veriler", etkin olarak aktarımda olmayan verileri ifade eder. Microsoft 365'te bekleyen e-posta verileri BitLocker Sürücü Şifrelemesi kullanılarak şifrelenir. BitLocker, yetkisiz erişime karşı gelişmiş koruma sağlamak için Microsoft veri merkezlerindeki sabit sürücüleri şifreler. Daha fazla bilgi için bkz. [BitLocker'a Genel Bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>E-posta şifreleme seçenekleri hakkında daha fazla bilgi

Bu makaledeki e-posta şifreleme seçenekleri ve TLS hakkında daha fazla bilgi için şu makalelere bakın:
  
**Microsoft Purview İleti Şifrelemesi**
  
[İleti şifreleme](ome.md)
  
**IRM**
  
[Exchange Online'de Bilgi Hakları Yönetimi](./information-rights-management-in-exchange-online.md)
  
[Azure Rights Management nedir?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[İleti imzalama ve şifreleme için S/MIME](/Exchange/policy-and-compliance/smime/smime)
  
[S/MIME'i anlama](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Ortak Anahtar Şifrelemesi'ni anlama](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Bağlayıcıları kullanarak özel posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
