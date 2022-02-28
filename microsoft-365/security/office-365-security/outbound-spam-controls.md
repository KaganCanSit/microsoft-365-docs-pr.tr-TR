---
title: Giden istenmeyen posta koruması
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) Exchange Online Protection giden istenmeyen posta denetimleri hakkında bilgi edinebilirsiniz ve toplu posta göndermeniz gerekirse ne yapmak gerekir?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 26be514584a8fb2f8c024c0f4db208018d951868
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988141"
---
# <a name="outbound-spam-protection-in-eop"></a>EOP'de giden istenmeyen posta koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu Exchange Online kuruluşlarda, giden istenmeyen postayı çok ciddiye alıyoruz. Bir müşteri kuruluşundan bilerek veya bilerek istenmeyen posta gönderse bile, bu eylem hizmetin tamamının itibarını düşürebilir ve diğer müşterilerin e-posta teslimlerini etkileyebilir.

Bu makalede, giden istenmeyen postaları önlemeye yardımcı olmak için tasarlanmış denetimler ve bildirimler ve toplu posta göndermeniz gerekirse ne yapabilirim?

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Yöneticilerin giden istenmeyen postaları kontrol etmek için neler yapabilirim?

- Yerleşik bildirimleri kullanma: Kullanıcı, hizmet veya giden istenmeyen posta ilkelerinin gönderme sınırlarını [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) aşar ve [](configure-the-outbound-spam-policy.md) e-posta göndermeyle kısıtlanmışsa, Kullanıcı'nın e-posta göndermeyle  kısıtladığı varsayılan uyarı ilkesi **TenantAdmins** (**Genel** yöneticiler) grubunun üyelerine **e-posta** bildirimleri gönderir. Bu bildirimleri başka kimlerin aldığını yapılandırmak için bkz [. Kısıtlanmış kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Ayrıca, E-posta gönderme sınırı  aşıldı ve Şüpheli e-posta gönderme desenleri **, TenantAdmins** (**Genel** yöneticiler) grubunun üyelerine e-posta bildirimi gönder algılandı adlı varsayılan uyarı ilkeleri. Uyarı ilkeleri hakkında daha fazla bilgi için bkz[. İlke ve Microsoft 365](../../compliance/alert-policies.md).

- Üçüncü taraf e-posta sağlayıcılarından gelen istenmeyen posta şikayetlerini gözden geçirme: Outlook.com, Yahoo ve AOL gibi birçok **e-posta** hizmeti, hizmetlerinde olan bir kullanıcının Microsoft 365'tan gelen bir e-postayı istenmeyen posta olarak işaretlerse ileti bir geri bildirim döngüsü sağlar ve gözden geçirilmek üzere bize geri gönderilir. Outlook.com için gönderen desteği hakkında daha fazla bilgi edinmek için, adresine gidin<https://sendersupport.olc.protection.outlook.com/pm/services.aspx>.

## <a name="how-eop-controls-outbound-spam"></a>EOP giden istenmeyen postayı nasıl kontrol eder?

- **Giden e-posta trafiğinin ayrımı**: Hizmet aracılığıyla gönderilen her giden ileti istenmeyen posta için taranır. İletinin istenmeyen posta olduğu belirlenirse, yüksek riskli teslim havuzu adlı, daha az saygın bir IP adres havuzundan _teslim edilir_. Daha fazla bilgi için bkz [. Giden iletiler için yüksek riskli teslim havuzu](high-risk-delivery-pool-for-outbound-messages.md).

- **Kaynak IP adresi itibarımızı izleme**: Microsoft 365 üçüncü taraf IP engelleme listelerini kontrol ediyor. Giden e-posta için kullanmamız IP adreslerinden herhangi biri bu listelerde görünürse bir uyarı oluşturulur. Bu izleme istenmeyen posta, itibarımızın bozulmasına neden olduğunda hızla tepki vermemizi sağlar. Uyarı  oluşturulsa bile IP adreslerimizin engellenenler listesinden nasıl kaldırıla (listelenmemiş) olduğunu ana hatlarıyla ileten iç belgelerimiz vardır.

- <sup>\*</sup>Çok fazla istenmeyen posta gönderen hesapları devre dışı bırak: Giden istenmeyen postayı yüksek riskli teslim havuzuna alı olsak da, bir hesabın (çoğunlukla, güvenliği tehlikeye atılmış bir hesap) süresiz olarak istenmeyen posta göndermesine izin ve vermiyoruz. İstenmeyen posta gönderen hesapları belirli bir sınırı aştıklarından, bu hesapların e-posta göndermesi engellenir. Tek tek kullanıcılar ve kiracının tamamı için farklı eşikler vardır.

- <sup>\*</sup>Çok fazla hızlı e-posta gönderen hesapları devre dışı **bırakma:** İstenmeyen posta olarak işaretlenen iletileri arama sınırlamalarına ek olarak, giden iletilerde istenmeyen posta filtreleme kararlarından bağımsız olarak genel giden ileti sınırına ulaşıldıklarında hesapları engellayan sınırlar da vardır. Güvenliği tehlikeye atılmış bir hesap, istenmeyen posta filtresi tarafından kaçırılan sıfır gün (önceden tanınmayan) istenmeyen posta gönderebilir. İstenmeyen posta kampanyası ile yasal bir toplu posta kampanyası belirlemek zor olduğundan, bu sınırlar olası hasarları en aza indirmeye yardımcı olur.

<sup>\*</sup> İstenmeyen posta gönderenlerin sistemi oyunla sınırlamayacak şekilde tam olarak sınırları duyurmamız gerekmez ve bu nedenle gerektiğinde sınırları artırabilir veya azaltabilirsiniz. Sınırlar, ortalama bir işletme kullanıcısını aşmasını önleyen ve spammer tarafından oluşan zararları içermeye yardımcı olacak kadar düşüktür.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Öneriler EOP aracılığıyla toplu posta göndermek isteyen müşterilere özel e-posta gönderme

Büyük miktarda e-posta göndermek isteyen müşteriler arasında dengeyi sağlamak ve hizmeti güvenliği tehlikeye atılmış hesaplardan ve toplu e-posta gönderenlerden kötü alıcı edinme uygulamalarıyla korumak zordur. Üçüncü taraf IP Microsoft 365 bir e-posta kaynağına inen bir e-posta kaynağının maliyeti, çok fazla e-posta gönderen bir kullanıcının engellenmesinden daha büyüktür.

Hizmet [Açıklaması'Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) açıklandığı gibi, toplu e-posta göndermek için EOP kullanmak hizmetin desteklenen bir kullanımı değildir ve yalnızca "en iyi çabayı" temel alan bir şekilde izin verilir. Toplu e-posta göndermek isteyen müşteriler için aşağıdaki çözümleri öneririz:

- **Şirket içi e-posta sunucuları aracılığıyla toplu e-posta gönderme**: Müşteriler toplu postalar için kendi e-posta altyapılarını korumalarını sağlar.

- **Üçüncü taraf toplu e-posta sağlayıcısı kullanma**: Toplu posta göndermek için kullanabileceğiniz birkaç üçüncü taraf toplu e-posta çözümü sağlayıcısı vardır. Bu şirketlerin, iyi e-posta gönderme uygulamalarından emin olmak için müşterilerle birlikte çalışma konusunda yoğun bir ilgileri var.

Mesajlaşma, Mobil, Kötü Amaçlı Yazılımdan Korunma Çalışma Grubu (MAAWG) üyelik listesi'nde yayımlar <https://www.maawg.org/about/roster>. Bu listede birçok toplu e-posta sağlayıcısı vardır ve bunlardan sorumlu İnternet karnesi olduğu bilinmektedir.
