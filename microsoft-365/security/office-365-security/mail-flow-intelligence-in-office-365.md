---
title: Posta akış zekası
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: troubleshooting
ms.custom: ''
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c29f75e5-c16e-409e-a123-430691e38276
description: Yöneticiler, bağlayıcıları (posta akış zekası olarak da bilinir) kullanarak ileti teslimi ile ilişkili hata kodlarını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2536120dfc336145ec9fdba1db34a8da1f56c1b4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681006"
---
# <a name="mail-flow-intelligence-in-eop"></a>EOP'de posta akışı zekası

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu olan Exchange Online kuruluşlarda, normalde EOP'den e-posta iletilerini şirket içi e-posta ortamınıza yönlendiren bir bağlayıcı kullanırsınız. İletileri iş ortağı kuruluşundan iş ortağı bir Microsoft 365 için de kullanabilirsiniz. Microsoft 365 bu iletileri bağlayıcı üzerinden teslim edeyene kadar teslim e-posta göndere Microsoft 365. Microsoft 365 24 saat boyunca her iletinin teslimi yeniden denenecek. 24 saat sonra kuyruğa alınan iletinin süresi dolar ve ileti özgün gönderene teslim edil iletisi (NDR veya geri dönen ileti olarak da bilinir) içinde döndürülür.

Microsoft 365 bir bağlayıcı kullanarak bir ileti teslimi başarısız olduğunda hata verir. En yaygın hatalar ve çözümleri bu makalede açıklanmıştır. Bağlayıcılar aracılığıyla gönderilen teslim edilemeyen iletiler için toplu olarak kuyruğa alma ve bildirim hataları, posta akış _zekası olarak bilinir_.

## <a name="error-code-450-44312-dns-query-failed"></a>Hata kodu: 450 4.4.312 DNS sorgusu başarısız oldu

Normalde, bu hata Microsoft 365 bağlayıcıda belirtilen akıllı ana bilgisayara bağlanmayı denemesi ancak akıllı ana bilgisayarının IP adreslerini bulmak için DNS sorgusunun başarısız olduğu anlamına gelir. Bu hatanın olası nedenleri:

- Etki alanınıza ilişkin DNS barındırma hizmette (etki alanınız için yetkili ad sunucularının bakımını yapan taraf) bir sorun vardır.

- Etki alanınız kısa süre önce sona erdi, dolayısıyla MX kaydı alınamıyor.

- Etki alanınıza ilişkin MX kaydı yakın zamanda değişmiştir ve DNS sunucuları daha önce etki alanınız için DNS bilgilerini önbelleğe alınmış olarak hala vardır.

### <a name="how-do-i-fix-error-code-450-44312"></a>Hata kodu 450 4.4.312'i nasıl düzeltebilirim?

- Etki alanınız ile ilgili sorunu tanımlamak ve gidermek için DNS barındırma hizmetiniz ile birlikte çalışabilirsiniz.

- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu düzeltmek için iş ortağınıza başvurun.

## <a name="error-code-450-44315-connection-timed-out"></a>Hata kodu: 450 4.4.315 Bağlantı zamanlandı

Normalde, bu Microsoft 365 e-posta sunucusunun hedef e-posta sunucusuna bağlanamay olduğu anlamına gelir. Hata ayrıntıları sorunu açıklar. Örneğin:

- Şirket içi e-posta sunucunuz yok.

- Bağlayıcının akıllı ana bilgisayar ayarlarında bir hata var, dolayısıyla Microsoft 365 IP adresine bağlanmaya çalışıyor.

### <a name="how-do-i-fix-error-code-450-44315"></a>Hata kodu 450 4.4.315'i nasıl düzeltirim?

- Sizin için hangi senaryonun geçerli olduğunu bulun ve gerekli düzeltmeleri yapın. Örneğin, posta akışı düzgün çalışıyorsa ve bağlayıcı ayarlarını değiştirmemişsanız, sunucunun aşağıda olup olmadığını veya ağ altyapıda herhangi bir değişiklik olup olmadığını görmek için şirket içi e-posta ortamınızı denetlemeniz gerekir (örneğin, İnternet servis sağlayıcıları değiştirdiniz, dolayısıyla artık farklı IP adresleriniz var).

- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu düzeltmek için iş ortağınıza başvurun.

## <a name="error-code-450-44316-connection-refused"></a>Hata kodu: 450 4.4.316 Bağlantı reddedildi

Normalde, bu hata Microsoft 365 e-posta sunucusuna bağlanmaya çalışıldı hatasıyla karşılaştığınız anlamına gelir. Bu hatanın olası bir nedeni güvenlik duvarının IP adreslerinden gelen bağlantıları Microsoft 365 olmasıdır. Şirket içi e-posta sisteminizi Microsoft 365-posta ortamınıza tamamen geçirmeniz ve kapatmanız, tasarımdan da bir hata olabilir.

### <a name="how-do-i-fix-error-code-450-44316"></a>Hata kodu 450 4.4.316'da nasıl düzeltebilirim?

- Şirket içi ortamınıza posta kutularınız varsa, TCP bağlantı noktası 25'te yer alan Microsoft 365 IP adreslerinden şirket içi e-posta sunucularına bağlantılara izin vermek için güvenlik duvarı ayarlarınızı değiştirmeniz gerekir. IP adreslerinin nasıl Microsoft 365 için bkz. MICROSOFT 365 [ve IP adresi aralıkları](../../enterprise/urls-and-ip-address-ranges.md).

- Şirket içi ortamınıza başka ileti teslimi gerektirsinse, Uyarıda Şimdi  düzelt'e tıklayın; böylece Microsoft 365 iletileri geçersiz alıcılara hemen reddedebilir. Bu, normal ileti teslimini etkileyabilecek geçersiz alıcılar için kuruluş kotasını aşma riskini azaltır. Sorunu kendiniz çözmek için aşağıdaki yönergeleri de kullanabilirsiniz:

  - Exchange yönetim merkezinde, şirket içi e-posta ortamınıza e-posta teslim Microsoft 365 devre dışı bırak veya sil:

    1. Aşağıdaki EAC'de, <https://admin.exchange.microsoft.com>Posta akışı **Bağlayıcıları'ne** \> **gidin**. Doğrudan Bağlayıcılar **sayfasına gitmek için** kullanın <https://admin.exchange.microsoft.com/#/connectors>.

    2. from value **Office 365 ve** **To** değeri Your **organization's email server ile bağlayıcıyı** seçin ve aşağıdaki adımlardan birini uygulayın:
       - Kaldır Simgesini Sil'e tıklayarak **bağlayıcıyı** ![silin.](../../media/adf01106-cc79-475c-8673-065371c1897b.gif)
       - Düzenle simgesini tıklatarak bağlayıcıyı **devre dışı** ![bırakabilirsiniz.](../../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) ve **Aç'ın temizlerini temizleme**.

  - Şirket içi e-Microsoft 365 ortamıyla ilişkilendirilmiş etki alanında kabul edilen etki alanını İç Geçişten **Yetkili'ye değiştirebilirsiniz**. Yönergeler için bkz. [Etki alanlarında kabul edilen etki Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

  **Not**: Normalde, bu değişikliklerin etkili olmak için 30 dakika ile bir saat arasında sürer. Bir saat sonra, hatayı artık alma almay postasını doğrulayın.

- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu çözmek için iş ortağınıza başvurun.

## <a name="error-code-450-44317-cannot-connect-to-remote-server"></a>Hata kodu: 450 4.4.317 Uzak sunucuya bağlanamıyor

Normalde, bu hata Microsoft 365 e-posta sunucusuna bağlı olduğu, ancak sunucunun hemen bir hatayla yanıt verdi olduğu veya bağlantı gereksinimlerini karşılamıyor olduğu anlamına gelir. Hata ayrıntıları sorunu açıklar. Örneğin:

- Hedef e-posta sunucusu "Hizmet kullanılamıyor" hatasıyla yanıt verdi ve bu da sunucunun Şu adresle iletişimi sürdüre olmadığını Microsoft 365.
- Bağlayıcı TLS gerektirecek şekilde yapılandırılmıştır, ancak hedef e-posta sunucusu TLS'yi desteklemez.

### <a name="how-do-i-fix-error-code-450-44317"></a>Hata kodu 450 4.4.317'i nasıl düzeltebilirim?

- Şirket içi e-posta sunucular ve bağlayıcıda TLS ayarlarını ve sertifikalarını doğrulayın.
- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu çözmek için iş ortağınıza başvurun.

## <a name="error-code-450-44318-connection-was-closed-abruptly"></a>Hata kodu: 450 4.4.318 Bağlantısı ani bir şekilde kapatıldı

Normalde, bu hata Microsoft 365 şirket içi e-posta ortamınız ile iletişim kurmakta güçlük veya sorun olduğu anlamına gelir; dolayısıyla bağlantı atıldı. Bu hatanın olası nedenleri:

- Güvenlik duvarınız SMTP paket kabul kurallarını kullanıyor ve bu kurallar düzgün çalışmıyor.
- Şirket içi e-posta sunucunuz düzgün çalışmıyor (örneğin, hizmet kilitleniyor, kilitleniyor veya düşük sistem kaynakları); bu da sunucunun zaman kapanmasına ve sunucuyla bağlantının kapanmasına neden Microsoft 365.
- Şirket içi ortamınız ile şirket içi ortamınız arasında ağ Microsoft 365.

### <a name="how-do-i-fix-error-code-450-44318"></a>Hata kodu 450 4.4.318'i nasıl düzeltebilirim?

- Sizin için hangi senaryonun geçerli olduğunu bulun ve gerekli düzeltmeleri yapın.
- Sorun, şirket içi ortamınız ile şirket içi ortamınız arasındaki ağ sorun Microsoft 365, sorunu gidermek için ağ ekibiyle iletişime geçin.
- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu çözmek için iş ortağınıza başvurun.

## <a name="error-code-450-47320-certificate-validation-failed"></a>Hata kodu: 450 4.7.320 Sertifika doğrulaması başarısız

Normalde, bu hata Microsoft 365 hedef e-posta sunucusunun sertifikasını doğrulamaya çalışırken bir hatayla karşılaştığınız anlamına gelir. Hata ayrıntıları hatayı açıklar. Örneğin:

- Sertifikanın süresi doldu
- Sertifika konusu eşleşmeyenleri
- Sertifika artık geçerli değil

### <a name="how-do-i-fix-error-code-450-47320"></a>Hata kodu 450 4.7.320'i nasıl düzeltebilirim?

- Bekleyen iletilerin teslim Microsoft 365 için bağlayıcının sertifikasını veya Microsoft 365 düzeltin.
- Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu çözmek için iş ortağınıza başvurun.

## <a name="other-error-codes"></a>Diğer hata kodları

Microsoft 365 şirket içi veya iş ortağı e-posta sunucunuza ileti teslim etmekte zor oluyor. Hatada **Hedef sunucu** bilgilerini kullanarak ortamınıza sorunu incelemek veya yapılandırma hatası varsa bağlayıcıyı değiştirmek için kullanın.

Hata iş ortağı kuruluştansa (örneğin, üçüncü taraf bulut hizmeti sağlayıcısı), sorunu çözmek için iş ortağınıza başvurun.
