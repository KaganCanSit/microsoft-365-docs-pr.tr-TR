---
title: Aynı adreste dış e-posta iletmeyi yapılandırma ve Microsoft 365.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2021
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Bu makale dış e-posta iletme, Otomatik iletme, 5.7.520 Erişim Engellendi iletileri, dış iletmeyi devre dışı bırakma, 'Yöneticiniz dış iletmeyi devre dışı bıraktı' iletilerini ve giden istenmeyen posta önleme ilkesi gibi konuları kapsar.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 228bb4402fd67ba8e56dd84b270c64977667ff2d
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401028"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>E-postalarda otomatik dış e-posta iletmeyi Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yönetici olarak, şirket gereksinimleriniz olabilir ve bu iletileri dış alıcılara (kuruluş dışından alıcılar) otomatik olarak iletilen iletileri kısıtlar veya kontrol eder. E-posta iletme kullanışlı olabilir, ancak bilgilerin olası açıklanması nedeniyle güvenlik riski de ortaya atabilirsiniz. Saldırganlar bu bilgileri kuruluşa veya iş ortaklarına saldırı yapmak için kullanabilir.

Aşağıdaki otomatik iletme türleri şu bağlantılarda Microsoft 365:

- Kullanıcılar, iletileri [otomatik olarak dış](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) gönderenlere (bilerek veya güvenliği tehlikeye atılmış bir hesabın sonucu olarak) iletecek Gelen Kutusu kurallarını yapılandırabilirsiniz.
- Yöneticiler, iletileri dış [alıcılara otomatik olarak](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) ilet üzere posta kutusu iletmeyi ( _SMTP_ iletme olarak da bilinir) yapılandırabilirsiniz. Yönetici yalnızca iletileri iletmeyi veya iletili iletilerin kopyalarını posta kutusunda tutmayı seçebilir.

> [!NOTE]
> Şirket içi e-posta sistemlerinden Microsoft 365 ile otomatik iletme özelliğine sahip kullanıcılar, yaklaşan güncelleştirmede bulut posta kutularıyla aynı ilke denetimlerine tabi olur. Bu güncelleştirme İleti Merkezi gönderisi üzerinden iletecek.

Dış alıcılara otomatik iletmeyi kontrol etmek için giden istenmeyen posta filtresi ilkelerini kullanabilirsiniz. Üç ayar kullanılabilir:

- **Otomatik - Sistem denetimli**: Bu, varsayılan ayardır. Bu ayar artık Kapalı ile **aynıdır**. Bu ayar ilk ilk ilk geldiğinde Açık ayarıyla **eşdeğerdir**. Zamanla, varsayılan olarak güvenli ilkeleri [sayesinde](secure-by-default.md) bu ayar tüm müşteriler için aşamalı olarak **Kapalı** olarak değiştirildi. Daha fazla bilgi için bu [blog gönderisi'ne bakın](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888). 
- **Açık**: Otomatik dış iletmeye izin verilir ve kısıtlanmaz.
- **Kapalı**: Otomatik dış iletme devre dışı bırakılır ve gönderene teslim edileme raporu (NDR veya geri dönen ileti olarak da bilinir) gönderilir.

Bu ayarları yapılandırma yönergeleri için bkz. [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - Otomatik iletmeyi devre dışı bırakmak, iletileri dış adreslere yönlendiren tüm Gelen Kutusu kurallarını (kullanıcılar) veya posta kutusu iletmeyi (yöneticiler) devre dışı bıraktır.
>
> - İletilerin iç kullanıcılar arasında otomatik olarak iletiliyor olması giden istenmeyen posta filtresi ilkelerinde yer alan ayarlardan etkilenmez.


## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Giden istenmeyen posta filtresi ilke ayarları diğer otomatik e-posta iletme denetimleriyle nasıl çalışır?

Yönetici olarak, otomatik e-posta iletmeye izin vermek veya engellemek için önceden başka denetimler yapılandırmış olabilirsiniz. Örneğin:

- [Dış etki alanlarının](/exchange/mail-flow-best-practices/remote-domains/remote-domains) birlarına veya tamamlarına otomatik e-posta iletmeye izin vermek veya engellemek için uzak etki alanları.
- Dış alıcılara otomatik olarak iletilen [iletileri Exchange](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) ve engellemek için posta akış kurallarında (aktarım kuralları olarak da bilinir) yer alan koşullar ve eylemler.

Bir ayar dış iletmeye izin verirken, başka bir ayar dış iletmeyi engellerken, blok normalde kazanır. Aşağıdaki tabloda örnekler açıklanmıştır:

<br>

****

|Senaryo|Sonuç|
|---|---|
|<ul><li>Uzak etki alanı ayarlarını otomatik iletmeye izin verecek şekilde yapılandırabilirsiniz.</li><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme seçeneği Kapalı olarak **ayarlanır**.</li></ul>|etkilenen etki alanlarındaki alıcılara otomatik olarak iletilene iletiler engellenir.|
|<ul><li>Uzak etki alanı ayarlarını otomatik iletmeye izin verecek şekilde yapılandırabilirsiniz.</li><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme seçeneği Otomatik **- Sistem denetimli olarak ayarlanır**.</li></ul>|etkilenen etki alanlarındaki alıcılara otomatik olarak iletilene iletiler engellenir. <p> Daha önce açıklandığı gibi **Otomatik - Sistem** tarafından denetlenen açık ayarı **kullanılır, ancak** tüm kuruluşlarda ayar zaman içinde **Kapalı** olarak değiştirilmiştir. <p> Netlik sağlamak için, giden istenmeyen posta filtresi ilkenizi Açık veya **Kapalı olarak yapılandırmanız** **gerekir**.|
|<ul><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme seçeneği On olarak **ayarlanır**</li><li>Posta akış kurallarını veya uzak etki alanlarını, otomatik olarak iletili e-postaları engellemek için kullanırsınız.</li></ul>|Etkilenen alıcılara otomatik olarak iletilen iletiler posta akış kuralları veya uzak etki alanları tarafından engellenir.|
|

Bu davranışı (örneğin), giden istenmeyen posta filtresi ilkelerinde otomatik iletmeye izin vermek için kullanabilirsiniz, ancak uzak etki alanlarını kullanıcıların iletileri ilet kullanabileceği dış etki alanlarını kontrol etmek için kullanabilirsiniz.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Otomatik olarak iletien kullanıcıları bulma

Bulut tabanlı hesaplar için Otomatik iletili iletiler raporunda, dış alıcılara otomatik olarak [ileti](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) gönderen kullanıcılar hakkında bilgi edinebilirsiniz. Şirket içi e-posta sisteminden Microsoft 365 aracılığıyla otomatik olarak ileti alan şirket içi kullanıcılar için, bu kullanıcıları izlemek için bir posta akış kuralı oluşturmanız gerekir. Posta akış kuralı oluşturma yönergeleri için bkz. [EAC kullanarak posta akış kuralı oluşturma](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Aşağıdaki bilgiler, yönetim merkezinde (EAC) posta Exchange oluşturmak için gereklidir:

- **Şu koşulu (koşul)** uygula: **İleti üst bilgisi bu** \> **metin düzenleri ile eş görünür**. Bu seçeneği görmek için Diğer **seçenekler'e** tıklamak zorunda olabileceğiniz unutmayın.
  - **Üst bilgi adı**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Üst bilgi değeri**: `.`

  Koşul şöyle görünür: **'X-MS-Exchange-Inbox-Rules-Loop'** üst bilgisi **'.'**

  Bu koşul, üst bilgi için herhangi bir değerle eşler.

- (İsteğe bağlı) **Aşağıdakini yapın** (eylem): İsteğe bağlı bir eylem yapılandırarak. Örneğin, üst bilgi adı  \> **X-İletili** olarak ve Doğru değeriyle **ileti üst** bilgisini ayarlamak için İleti özelliklerini değiştirme eylemini **kullanabilirsiniz**. Ancak, bir eylemi yapılandırmak gerekmez.
- Bu **rupisi önem düzeyi için Düşük****, Orta** veya Yüksek **değerine** **ayarlayın**. Bu ayar, iletmeyi sağlayan [Exchange için Aktarım](view-email-security-reports.md#exchange-transport-rule-report) Kuralı raporunu kullanmana olanak sağlar.

![İletili iletileri tanımlamak için EAC'de posta akışı kuralı özellikleri.](../../media/mail-flow-rule-for-forwarded-messages.png)

## <a name="blocked-email-forwarding-messages"></a>İletileri iletirken engellenen e-posta

İleti otomatik olarak iletildi olarak algılandığında ve giden istenmeyen posta filtresi [](configure-the-outbound-spam-policy.md) bu etkinliği engellerse,  ileti aşağıdaki bilgileri içeren bir NDR'de gönderene döndürülür:

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
