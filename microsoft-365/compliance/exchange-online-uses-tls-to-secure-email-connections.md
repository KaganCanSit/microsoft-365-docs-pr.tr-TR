---
title: Exchange Online, e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?
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
description: Exchange Online ve Microsoft 365'in e-posta iletişimlerinin güvenliğini sağlamak için Aktarım Katmanı Güvenliği (TLS) ve İletme Gizliliği 'ni (FS) nasıl kullandığını öğrenin. Ayrıca Exchange Online için Microsoft tarafından verilen sertifika hakkında da bilgi edinin.
ms.openlocfilehash: 93f71e38e3063aeec0c423dbfea25ac463a3e46f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641570"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Exchange Online, e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?

Exchange Online ve Microsoft 365'in e-posta iletişimlerinin güvenliğini sağlamak için Aktarım Katmanı Güvenliği (TLS) ve İletme Gizliliği 'ni (FS) nasıl kullandığını öğrenin. Ayrıca, Exchange Online için Microsoft tarafından verilen sertifika hakkında bilgi sağlar.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Microsoft 365 ve Exchange Online için TLS temel bilgileri

AKTARıM Katmanı Güvenliği (TLS) ve TLS'den önce gelen SSL, bilgisayarlar arasındaki bağlantıyı şifrelemek için güvenlik sertifikaları kullanarak ağ üzerinden iletişimi güvenli hale getiren şifreleme protokolleridir. TLS, Güvenli Yuva Katmanı'nın (SSL) yerini alır ve genellikle SSL 3.1 olarak adlandırılır. Exchange Online, Exchange sunucuları arasındaki bağlantıları ve Exchange sunucuları ile şirket içi Exchange sunucularınız veya alıcılarınızın posta sunucuları gibi diğer sunucular arasındaki bağlantıları şifrelemek için TLS kullanır. Bağlantı şifrelendiğinde, bu bağlantı üzerinden gönderilen tüm veriler şifrelenmiş kanal üzerinden gönderilir. Ancak, TLS ile şifrelenmiş bir bağlantı üzerinden gönderilen bir iletiyi iletirseniz, bu ileti mutlaka şifrelenmez. TLS iletiyi şifrelemez, yalnızca bağlantıyı şifreler.
  
İletiyi şifrelemek istiyorsanız, ileti içeriğini şifreleyen bir şifreleme teknolojisi kullanın. Örneğin, Microsoft Purview İleti Şifrelemesi veya S/MIME kullanabilirsiniz. Office 365 ileti [şifrelemesi](ome.md) hakkında bilgi için bkz. [Office 365'de e-posta](email-encryption.md) şifrelemesi ve İleti şifrelemesi.
  
Microsoft ile şirket içi kuruluşunuz veya iş ortağı gibi başka bir kuruluş arasında güvenli bir yazışma kanalı ayarlamak istediğiniz durumlarda TLS'yi kullanın. Exchange Online her zaman e-postanızın güvenliğini sağlamak için önce TLS'yi kullanmayı dener, ancak diğer taraf TLS güvenliği sağlamazsa kullanamaz. *Bağlayıcıları* kullanarak şirket içi sunucularınıza veya önemli iş ortaklarınıza gelen tüm postaların güvenliğini nasıl sağlayabileceğinizi öğrenmek için okumaya devam edin.

Microsoft, müşterilerimize sınıfının en iyisi şifrelemeyi sağlamak için Office 365 ve [Office 365 GCC'de](tls-1-2-in-office-365-gcc.md) Aktarım Katmanı Güvenliği (TLS) 1.0 ve 1.1 sürümlerini kullanım dışı bırakmıştır.[](tls-1.0-and-1.1-deprecation-for-office-365.md) Ancak, şifrelenmemiş smtp bağlantısını tls olmadan kullanmaya devam edebilirsiniz. Şifreleme olmadan e-posta iletimini önermeyiz.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Exchange Online Exchange Online müşterileri arasında TLS'i nasıl kullanır?

Exchange Online sunucuları her zaman TLS 1.2 ile veri merkezlerimizdeki diğer Exchange Online sunuculara bağlantıları şifreler. Kuruluşunuzdaki bir alıcıya ileti gönderdiğinizde, Exchange Online tls kullanarak iletiyi otomatik olarak şifrelenmiş bir bağlantı üzerinden gönderir. Exchange Online ayrıca, İletme Gizliliği kullanılarak güvenliği sağlanan TLS kullanarak şifrelenmiş bağlantılar üzerinden diğer müşterilere gönderdiğiniz e-postaları da gönderir.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Microsoft 365, Microsoft 365 ile dış, güvenilir iş ortakları arasında TLS'yi nasıl kullanır?

Varsayılan olarak, Exchange Online her zaman *fırsatçı TLS* kullanır. Fırsatçı TLS, Exchange Online bağlantıları her zaman önce TLS'nin en güvenli sürümüyle şifrelemeye çalıştığı, ardından her iki tarafın da kabul ettiği bir şifre bulana kadar TLS şifreleri listesinde aşağı doğru çalıştığı anlamına gelir. alıcıya gönderilen iletilerin güvenli bağlantılar kullanmasını sağlamak için Exchange Online yapılandırmadıysanız, alıcı kuruluş TLS şifrelemesini desteklemiyorsa ileti varsayılan olarak şifreleme olmadan gönderilir. Fırsatçı TLS çoğu işletme için yeterlidir. Bununla birlikte, tıbbi, bankacılık veya kamu kuruluşları gibi uyumluluk gereksinimleri olan işletmeler için Exchange Online TLS'yi zorunlu kılması veya zorunlu kılması için yapılandırabilirsiniz. Yönergeler için bkz[. Office 365'da bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Kuruluşunuzla güvenilir bir iş ortağı kuruluş arasında TLS yapılandırmaya karar verirseniz, Exchange Online *zorlanmış TLS* kullanarak güvenilir iletişim kanalları oluşturabilirsiniz. Zorlamalı TLS, iş ortağı kuruluşunuzun size posta göndermek için bir güvenlik sertifikasıyla Exchange Online kimliğini doğrulamasını gerektirir. İş ortağınızın kendi sertifikalarını yönetmesi gerekir. Exchange Online, gönderdiğiniz iletileri alıcının e-posta sağlayıcısına ulaşmadan önce yetkisiz erişimden korumak için bağlayıcıları kullanır. Posta akışını yapılandırmak için bağlayıcıları kullanma hakkında bilgi için bkz[. Office 365'da bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>TLS ve karma Exchange Server dağıtımları

Karma Exchange dağıtımını yönetiyorsanız, posta kutuları yalnızca Office 365 olan alıcılara posta göndermek için şirket içi Exchange sunucunuzun bir güvenlik sertifikası kullanarak Microsoft 365'te kimlik doğrulaması yapması gerekir. Sonuç olarak, şirket içi Exchange sunucularınız için kendi güvenlik sertifikalarınızı yönetmeniz gerekir. Ayrıca bu sunucu sertifikalarını güvenli bir şekilde depolamanız ve korumanız gerekir. Karma dağıtımlarda sertifikaları yönetme hakkında daha fazla bilgi için bkz. [Karma dağıtımlar için sertifika gereksinimleri](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Office 365'de Exchange Online için zorunlu TLS ayarlama

Exchange Online müşterileri için, gönderilen ve alınan tüm e-postalarınızın güvenliğini sağlamak için TLS'nin çalışmasını zorunlu hale getirmek için TLS gerektiren birden fazla bağlayıcı ayarlamanız gerekir. Kullanıcı posta kutularına gönderilen iletiler için bir bağlayıcı ve kullanıcı posta kutularından gönderilen iletiler için başka bir bağlayıcı gerekir. Bu bağlayıcıları Office 365'deki Exchange yönetim merkezinde oluşturun. Yönergeler için bkz[. Office 365'da bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>Exchange Online için TLS sertifika bilgileri

Exchange Online tarafından kullanılan sertifika bilgileri aşağıdaki tabloda açıklanmıştır. İş ortağınız e-posta sunucusunda zorunlu TLS ayarlanıyorsa, bu bilgileri onlara sağlamanız gerekir. Güvenlik nedeniyle sertifikalarımız zaman zaman değişir. Geçerli sertifika 24 Eylül 2020'den itibaren geçerlidir.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>24 Eylül 2020'den itibaren geçerli sertifika bilgileri
  
| Öznitelik | Değer |
|:-----|:-----|
|Sertifika yetkilisi kök veren|DigiCert CA - 1|
|Sertifika adı|mail.protection.outlook.com|
|Organizasyon|Microsoft Corporation|
|Kuruluş birimi|www.digicert.com|
|Sertifika anahtarı gücü|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>TLS, sertifikalar ve Microsoft 365 hakkında daha fazla bilgi edinin ve sertifikaları indirin

[Microsoft 365 şifreleme zincirleri ve sertifika indirmeleri](encryption-office-365-certificate-chains.md)

[Microsoft 365 şifreleme zincirleri ve sertifika indirmeleri - DOD ve GCC High](encryption-office-365-certificate-chains-itar.md)

Desteklenen şifreleme paketlerinin listesi için bkz. [Şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md).
  
[İş ortağı kuruluşuyla güvenli posta akışı için bağlayıcıları ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Gelişmiş e-posta güvenliğine sahip bağlayıcılar](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Microsoft 365'te şifreleme](encryption.md)
