---
title: E-posta şifrelemesi Microsoft 365
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
description: Aktarım Microsoft 365 (OME), S/MIME, Bilgi Hakları Yönetimi (IRM) gibi veri şifreleme seçeneklerini Office 365 İleti Şifrelemesi ve Aktarım Katmanı Güvenliği (TLS) hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 1d6ad4f595652b39ff6e984afe096272a7920c4d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973746"
---
# <a name="email-encryption"></a>E-posta şifreleme

Bu makalede, Microsoft 365 (OME), S/MIME, Bilgi Hakları Yönetimi (IRM) gibi Office 365 İleti Şifrelemesi şifreleme seçenekleri karşılaştırılıyor ve Aktarım Katmanı Güvenliği (TLS) sunulmaktadır.
  
Microsoft 365, e-posta güvenliğiyle ilgili iş ihtiyaçlarını karşılamanıza yardımcı olmak için birden çok şifreleme seçeneği sunar. Bu makalede, e-postayı e-posta şifrelemenin üç yolu Office 365. Bu özelliğin tüm güvenlik özellikleri hakkında daha fazla bilgi edinmek Office 365 Güven [Merkezi'Office 365 ziyaret edin](https://go.microsoft.com/fwlink/p/?LinkID=282470). Bu makalede, e-postayı güvenlik altına almak için Microsoft 365 yöneticilerine üç şifreleme türü Office 365:
  
- Office Şifrelemesi (OME) sağlar.

- Güvenli/Çok Amaçlı İnternet Posta Uzantıları (S/MIME).

- Bilgi Hakları Yönetimi (IRM).

## <a name="how-microsoft-365-uses-email-encryption"></a>E-Microsoft 365 nasıl e-posta şifrelemesi kullanır?

Şifreleme, yalnızca yetkili bir alıcının bilgileri çözemesi ve tüketmesi için bilgilerin kodlanması işlemidir. Microsoft 365 iki şekilde şifreleme kullanır: hizmette ve müşteri denetiminde. Hizmette, şifreleme Microsoft 365 olarak kullanılır; herhangi bir şey yapılandırmanız da zorunda değildir. Örneğin, Microsoft 365 iki sunucu arasındaki bağlantıyı veya oturumu şifrelemek için Aktarım Katmanı Güvenliği (TLS) kullanır. 
  
E-posta şifreleme normalde şöyle çalışır:
  
- İleti, gönderenin makinesi veya iletilirken merkezi bir sunucu tarafından şifrelenir veya düz metinden okunamaz şifreleme metnine dönüşür.

- İletinin kesişme durumunda okunmalarını korumak için iletilirken şifreleme metninde kalır.

- İleti alıcı tarafından alındıktan sonra, ileti iki şekilden birini kullanarak okunabilir düz metne döner:

  - Alıcının makinesi iletinin şifresini çözmek için bir anahtar kullanır veya

  - Merkezi bir sunucu, alıcının kimliğini doğruladikten sonra, alıcı adına iletinin şifresini çözebilir.

Microsoft 365'ın sunucular arasında, Microsoft 365'de yer alan kuruluşlar veya Microsoft 365 dışındaki güvenilen bir iş ortağı arasında ve sunucular arasında iletişimin nasıl güvenli olduğu hakkında daha fazla bilgi için bkz. [Microsoft 365'Exchange Online  TS'yi kullanarak e-posta bağlantılarının güvenliğini Office 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>E-posta şifreleme seçeneklerini karşılaştırma Office 365

|E-posta şifreleme teknolojisi|![OME'nin tanımları için kavramsal çizim.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![IRM'nin tanım olduğu kavramsal çizim](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![SMIME'yi açıklayan kavramsal çizim](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Nedir o?|Office 365 İleti Şifrelemesi (OME), hedef e-posta adresine (Gmail, Yahoo! Mail, Outlook.com vb.). <br/> Yönetici olarak, şifreleme koşullarını tanımlayan aktarım kuralları kurarak bu kuralları kullanabilirsiniz. Kullanıcı kuralla eşleşen bir ileti gönderdiğide, şifreleme otomatik olarak uygulanır. <br/> Şifreli iletileri görüntülemek için alıcılar tek seferlik geçiş koduna sahip olabilir, Microsoft hesabıyla oturum ya da alıcıyla ilişkilendirilmiş iş veya okul hesabıyla oturum Office 365. Alıcılar da şifreli yanıtlar gönderebilir. Şifreli iletileri görüntülemek veya Microsoft 365 yanıt göndermek için kullanıcı aboneliğine ihtiyaçları değildir.|IRM, e-posta iletilerine kullanım kısıtlamaları da uygulanan bir şifreleme çözümüdür. Bu, hassas bilgilerin yetkisiz kişiler tarafından yazdırılmaz, iletilme veya kopyanması için önlemeye yardımcı olur. <br/> Azure Hak Yönetimi'Microsoft 365 (Azure RMS) kullanımıyla ilgili IRM özellikleri.|S/MIME, iletiyi hem şifreleme hem de dijital olarak imzalamanızı sağlayan sertifika tabanlı bir şifreleme çözümüdür. İleti şifrelemesi, yalnızca hedeflenen alıcının iletiyi açıp okuyabilmelerini sağlamaya yardımcı olur. Dijital imza, alıcının gönderenin kimliğini doğrulamasını sağlar. <br/> Hem dijital imzalar hem de ileti şifreleme, dijital imzaları doğrulamak ve iletileri şifrelemek veya şifrelerini çözmek için gereken anahtarları içeren benzersiz dijital sertifikaların kullanımı yoluyla mümkün olur. <br/> S/MIME kullanmak için, her alıcının ortak anahtarlarını dosyada bulundurabilirsiniz. Alıcıların güvenli kalması için kendi özel anahtarlarını korumaları gerekir. Alıcının özel anahtarları tehlikeye atılmışsa, alıcının yeni bir özel anahtara sahip olması ve ortak anahtarları tüm olası gönderenlere yeniden dağıtmış olması gerekir.|
|Ne işe geliyor?|OME: <br/> İç veya dış alıcılara gönderilen iletileri şifreler. <br/>  Kullanıcıların Outlook.com, Yahoo! gibi herhangi bir e-posta adresine şifrelenmiş ileti göndermesini sağlar Mail ve Gmail. <br/>  Bir yönetici olarak e-posta görüntüleme portalını, kurum markasını yansıtacak şekilde özelleştirmenizi sağlar. <br/> Microsoft anahtarları güvenli bir şekilde yönetir ve depolar, böylece sizin bunu yapmak zorunda değildir. <br/> Şifreli ileti (HTML eki olarak gönderilir) tarayıcıda açılabilir olduğu sürece özel bir istemci tarafı yazılımı gerekmez.|IRM: <br/> E-posta iletileri ve ekleri için çevrimiçi ve çevrimdışı koruma sağlamak üzere şifreleme ve kullanım kısıtlamalarını kullanır. <br/> Yönetici olarak size, iletileri seçmek için IRM'yi otomatik olarak uygulamak için aktarım Outlook aktarım kurallarını ayarlama veya koruma kurallarını ayarlama olanağı verir. <br/> Kullanıcıların şablon ve dosya (eski adı Outlook Web üzerinde Outlook) içinde el ile şablon uygulamalarını Outlook Web App.|S/MIME, dijital imzalarla gönderen kimlik doğrulamasını ve şifreleme ile ileti gizliliğini ele alır.|
|Peki bu neleri yapar?|OME, iletilere kullanım kısıtlamaları uygulamana izin vermez. Örneğin, alıcının şifreli bir iletiyi iletmesini veya yazdırmasini durdurmak için onu kullanasınız.|Bazı uygulamalar tüm cihazlarda IRM e-postalarını desteklemeyebilirsiniz. IRM e-postasını destekleyen bu ürünler ve diğer ürünler hakkında daha fazla bilgi için bkz [. İstemci cihazı özellikleri](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME, şifreli iletilerin kötü amaçlı yazılım, istenmeyen posta veya ilkeler için taran olmasına izin vermez.|
|Öneriler senaryolar ve örnek senaryolar|İster tüketiciler ister diğer işletmeler olsun, kuruluş dışındaki kişiler için hassas iş bilgileri göndermek istediğiniz zaman OME'nin kullanılması önerilir. Örneğin:  <br/>  Müşterilere kredi kartı deyimleri gönderen bir banka çalışanı  <br/>  Hastanın tıbbi kayıtlarını gönderen bir doktor muayene muayenesi  <br/>  Başka bir avukata gizli yasal bilgileri gönderen bir avukat|Kullanım kısıtlamaları ve şifreleme uygulamak istediğiniz zaman IRM'i öneririz. Örneğin:  <br/>  Ekibine yeni ürünle ilgili gizli bilgiler gönderen bir yönetici "İteleyim" seçeneğini uygular.  <br/>  Yöneticinin, Office 365 kullanan bir iş ortağının ekını içeren ve hem e-postanın hem de ekin korunmasını gerektiren başka bir şirketle teklif teklifi paylaşması gerekiyor.|S/MIME'nin, kurum veya alıcının kuruluşuna gerçek eşler arası şifreleme gerektirdiği zaman kullanılması önerilir.  <br/>  S/MIME en çok aşağıdaki senaryolarda kullanılır:  <br/>  Kamu kuruluşları diğer kamu kuruluşlarıyla iletişim kurar  <br/>  Kamu kurumuyla iletişim halinde bir işletme|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Microsoft 365 aboneliğim için hangi Microsoft 365 kullanılabilir?

Yeni aboneliğinizin e-posta şifreleme seçenekleri hakkında Microsoft 365 için bkz[. Exchange Online açıklama.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) Burada, aşağıdaki şifreleme özellikleri hakkında bilgi bulabilirsiniz:
  
- Hem IRM özellikleri hem de OME dahil olmak üzere Azure RMS

- S/MIME

- TLS

- Beklemede verilerin şifreleniyor (BitLocker yoluyla)

Ayrıca, üçüncü taraf şifreleme araçlarını, ÖRNEĞIN PGP (Oldukça İyi Gizlilik) Microsoft 365, üçüncü taraf şifreleme araçlarını da kullanabilirsiniz. Microsoft 365 PGP/MIME'yi desteklemez ve PGP şifreli e-postaları göndermek ve almak için yalnızca PGP/Inline kullanabilirsiniz.

## <a name="what-about-encryption-for-data-at-rest"></a>Beklemede veriler için şifreleme ne olacak?

"Geri kalan veriler", etkin bir şekilde geçişte olmayan verileri ifade eder. Daha Microsoft 365 e-posta verileri BitLocker Sürücü Şifrelemesi kullanılarak şifrelenir. BitLocker, yetkisiz erişime karşı gelişmiş koruma sağlamak için Microsoft veri merkezlerinde sabit sürücüleri şifreler. Daha fazla bilgi edinmek için bkz. [BitLocker'a Genel Bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>E-posta şifreleme seçenekleri hakkında daha fazla bilgi

Bu makalede hem e-posta şifreleme seçenekleri hem de TLS hakkında daha fazla bilgi için şu makalelere bakın:
  
**OME**
  
[Office 365 İleti Şifrelemesi (OME)](ome.md)
  
**IRM**
  
[Exchange Online'de Bilgi Hakları Yönetimi](./information-rights-management-in-exchange-online.md)
  
[Azure Hak Yönetimi nedir?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[İleti imzalama ve şifreleme için S/MIME](/Exchange/policy-and-compliance/smime/smime)
  
[S/MIME'i anlama](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Ortak Anahtar Şifrelemeyi Anlama](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Bağlayıcıları kullanarak özel posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
