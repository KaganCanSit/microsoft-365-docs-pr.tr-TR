---
title: E Exchange Online bağlantılarının güvenliğini sağlamak için Aktarım Katmanı Güvenliği'nin (TLS) kullanımı
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/08/2021
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: E-Exchange Online güvenli Microsoft 365 Aktarım Katmanı Güvenliği (TLS) ve İletme Gizliliğini (FS) nasıl kullanabileceğinizi ve nasıl kullanabileceğinizi öğrenin. Ayrıca Microsoft tarafından verilen sertifika hakkında daha fazla bilgi Exchange Online.
ms.openlocfilehash: 1caf4a8425f4a8e7c340e8a52d785027e99a1618
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998284"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>E Exchange Online bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?

E-Exchange Online güvenli Microsoft 365 Aktarım Katmanı Güvenliği (TLS) ve İletme Gizliliğini (FS) nasıl kullanabileceğinizi ve nasıl kullanabileceğinizi öğrenin. Ayrıca, Microsoft tarafından güvenlik için verilen sertifika hakkında Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>TLS'de temel Microsoft 365 ve Exchange Online

TLS'den önce gelen Aktarım Katmanı Güvenliği (TLS) ve SSL, bilgisayarlar arasındaki bağlantıyı şifrelemek için güvenlik sertifikaları kullanarak ağ üzerinden iletişimi güvenli hale gelen şifreleme protokolleridir. TLS, Güvenli Yuva Katmanı'nın (SSL) yerine kullanılır ve genellikle SSL 3.1 olarak adlandırılır. Exchange Online, Exchange sunucularıyla Exchange sunucuları ile şirket içi Exchange sunucuları veya alıcılarının posta sunucuları gibi diğer sunucular arasındaki bağlantıları şifrelemek için TLS kullanır. Bağlantı şifrelenirken, bu bağlantı üzerinden gönderilen tüm veriler şifreli kanal aracılığıyla gönderilir. Bununla birlikte, TLS şifreli bir bağlantı üzerinden gönderilmiş bir iletiyi iletirsiniz, bu iletinin şifrelenmiş olması gerekmez. TLS iletiyi şifrelemez, yalnızca bağlantıyı şifrelemez.
  
İletiyi şifrelemek istemiyorsanız, ileti içeriğini şifrelenen bir şifreleme teknolojisi kullanın. Örneğin, İleti Şifrelemesi'Office S/MIME kullanabilirsiniz. [E-posta şifreleme hakkında bilgi Office 365](email-encryption.md) ve [Office 365 İleti Şifrelemesi (OME)](ome.md) içinde e-posta şifrelemesi Office 365.
  
TLS'yi, Microsoft ile şirket içi kuruluş arasında veya iş ortağı gibi başka bir kuruluş arasında yazışmaların güvenli bir kanalını ayarlamak istediğiniz durumlarda kullanın. Exchange Online e-postanızı güvence altına almak için her zaman TLS kullanmayı denemenize rağmen karşı taraf TLS güvenliği sunmasa da bunu yapmak zorunda değildir. Bağlayıcıları kullanarak şirket içi sunucularınıza veya önemli iş ortaklarına tüm postayı nasıl güvenli hale gönderebilirsiniz hakkında bilgi almak için okumaya *devam edin*.

Müşterilerimize en iyi sınıf şifrelemeyi sağlamak için Microsoft, [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) ve Office 365 GCC'de Aktarım Katmanı Güvenliği (TLS) sürüm 1.0 ve 1.1'i [kullanımdan Office 365 GCC](tls-1-2-in-office-365-gcc.md). Ancak, TLS olmadan şifrelenmemiş SMTP bağlantısını kullanmaya devam edersiniz. Şifreleme olmadan e-posta iletimini önerilmez.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>EXCHANGE ONLINE, diğer müşteriler arasında TLS Exchange Online i nasıl kullanır?

Exchange Online her zaman veri merkezlerimizde TLS 1.2 Exchange Online diğer veri sunucularına olan bağlantıları şifreler. İletiyi, kurum içindeki bir alıcıya gönderirken, Exchange Online TLS kullanılarak otomatik olarak şifreli bir bağlantı üzerinden gönderilir. Exchange Online ayrıca, İletme Güvenliği kullanılarak güvenliği sağlanacak TLS kullanarak şifrelenmiş bağlantılar üzerinden diğer müşterilere de e-posta gönderir.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Dış Microsoft 365, güvenilir iş ortakları arasında Microsoft 365 TLS'yi nasıl kullanır?

Varsayılan olarak, Exchange Online *her zaman fırsat fırsatlarını kullanır*. Fırsatçı TLS, Exchange Online bağlantıları her zaman en güvenli TLS sürümüyle şifrelemeye çalıştığından, sonra da TLS şifreleme listesinde aşağı doğru ilerler ve her iki tarafta da anlaşılacak bir şifreleme bulana kadar çalışır. Bu alıcıya Exchange Online güvenli bağlantılar kullanmalarını sağlayacak şekilde yapılandırmadıysanız, alıcı kuruluş TLS şifrelemeyi desteklemiyorsa ileti varsayılan olarak şifreleme olmadan gönderilir. Fırsat TLS, çoğu işletme için yeterlidir. Ancak tıp, bankacılık veya kamu kuruluşları gibi uyumluluk gereksinimleri olan işletmeler için, Exchange Online'yi gerekli olacak şekilde yapılandırarak veya TLS'yi zorlarsiniz. Yönergeler için bkz. [Kendi adres mektuplarında bağlayıcıları kullanarak posta Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
TlS'yi organizasyonla güvenilir bir iş ortağı kuruluş arasında yapılandırmaya karar Exchange Online, güvenilir iletişim kanalları oluşturmak için zorunlu *TLS'yi* kullanabilirsiniz. Zorunlu TLS, iş ortağı kuruluşlarının size posta Exchange Online sertifikayla kimlik doğrulaması yapmalarını gerektirir. İş ortağının kendi sertifikalarını yönetmesi gerekir. Exchange Online e-posta sağlayıcısına gelmeden önce yetkisiz erişimden gönderirken iletileri korumak için bağlayıcıları kullanır. Posta akışını yapılandırmak için bağlayıcıları kullanma hakkında bilgi için bkz. Kendi adres mektuplarında [bağlayıcıları kullanarak posta Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>TLS ve karma Exchange Server dağıtımları

Karma bir Exchange dağıtımı yönetiyorsanız, posta kutuları yalnızca Exchange'te olan alıcılara posta göndermek için güvenlik sertifikası kullanarak şirket içi Exchange sunucunuzda kimlik Office 365 doğrulaması yapılması Microsoft 365. Sonuç olarak, şirket içi güvenlik sertifikalarınızı ve sunucularınızı yönetmek için kendi güvenlik Exchange gerekir. Ayrıca, bu sunucu sertifikalarını güvenli bir şekilde depolamanız ve korumanız gerekir. Karma dağıtımlarda sertifikaları yönetme hakkında daha fazla bilgi için bkz. [Karma dağıtımlar için sertifika gereksinimleri](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Office 365'de zorlanan TLS Exchange Online nasıl ayarlanır Office 365

Diğer Exchange Online, gönderilen ve alınan tüm e-postalarınızı güvenlik altına almak amacıyla zorlanan TLS'nin çalışması için, TLS gerektiren birden çok bağlayıcıyı ayarlaym gerekir. Kullanıcı posta kutularına gönderilen iletiler için bir bağlayıcıya ve kullanıcı posta kutularından gönderilen iletiler için de başka bir bağlayıcıya ihtiyacınız vardır. Bu bağlayıcıları, Exchange yönetim merkezinde Office 365. Yönergeler için bkz. [Kendi adres mektuplarında bağlayıcıları kullanarak posta Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>İletişim için TLS sertifika Exchange Online

Kullanıcı tarafından kullanılan sertifika Exchange Online aşağıdaki tabloda açıklanmıştır. İş ortağınız e-posta sunucusunda zorlamalı TLS ayarıyorsa, bu bilgiyi onlara sağlaymanız gerekir. Güvenlik nedenleriyle, sertifikalarımız zaman zaman değişir. Geçerli sertifika 24 Eylül 2020'den itibaren geçerlidir.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Geçerli sertifika bilgileri 24 Eylül 2020'den itibaren geçerli
  
| Öznitelik | Değer |
|:-----|:-----|
|Sertifika yetkilisi kök issuer|DigiCert CA – 1|
|Sertifika adı|mail.protection.outlook.com|
|Kuruluş|Microsoft Corporation|
|Kuruluş birimi|www.digicert.com|
|Sertifika anahtar gücü|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>TLS, sertifikalar ve sertifikalar hakkında daha fazla bilgi Microsoft 365 sertifika indirme ve indirme

[Microsoft 365 zincirleri ve sertifika indirmelerini yükleme](encryption-office-365-certificate-chains.md)

[Microsoft 365 şifreleme zincirleri ve sertifika indirmeleri - DOD ve GCC High](encryption-office-365-certificate-chains-itar.md)

Desteklenen şifreleme paketlerinin listesi için bkz. Şifreleme [hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md).
  
[İş ortağı kuruluşla güvenli posta akışı için bağlayıcıları ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Gelişmiş e-posta güvenliğine sahip bağlayıcılar](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Şifreleme Microsoft 365](encryption.md)
