---
title: Microsoft 365'te dış e-posta iletmeyi yapılandırma ve denetleme.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2021
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
- adminvideo
description: Bu makale dış e-posta iletme, Otomatik iletme, 5.7.520 Erişim Reddedildi iletileri, dış iletmeyi devre dışı bırakma, 'Yöneticiniz dış iletmeyi devre dışı bırakmış' iletileri ve giden istenmeyen posta önleme ilkesi gibi konuları kapsar.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c10433cd858ebe160ac4a38cfee78b57d39b80df
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487158"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Microsoft 365'te otomatik dış e-posta iletmeyi denetleme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yönetici olarak, otomatik olarak iletilen iletileri dış alıcılara (kuruluşunuzun dışındaki alıcılar) kısıtlamak veya denetlemek için şirket gereksinimleriniz olabilir. E-posta iletme yararlı olabilir, ancak bilgilerin olası açığa çıkması nedeniyle güvenlik riski de oluşturabilir. Saldırganlar bu bilgileri kuruluşunuza veya iş ortaklarınıza saldırmak için kullanabilir.

Aşağıdaki otomatik iletme türleri Microsoft 365'te kullanılabilir:

- Kullanıcılar, gelen [kutusu kurallarını](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) iletileri otomatik olarak dış gönderenlere iletecek şekilde yapılandırabilir (kasıtlı olarak veya güvenliği aşılmış bir hesabın sonucu olarak).
- Yöneticiler, iletileri otomatik olarak dış alıcılara iletmek için [posta kutusu iletmeyi](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) ( _SMTP iletme_ olarak da bilinir) yapılandırabilir. Yönetici, iletileri iletmeyi veya iletilen iletilerin kopyalarını posta kutusunda tutmayı seçebilir.

> [!NOTE]
> Şirket içi e-posta sistemlerinden Microsoft 365 aracılığıyla otomatik iletme özelliğine sahip kullanıcılar, gelecek bir güncelleştirmede bulut posta kutularıyla aynı ilke denetimlerine tabi olacak. Bu güncelleştirme İleti Merkezi gönderisi aracılığıyla iletilecektir.

Dış alıcılara otomatik iletmeyi denetlemek için giden istenmeyen posta filtresi ilkelerini kullanabilirsiniz. Üç ayar mevcuttur:

- **Otomatik - Sistem denetimi**: Bu varsayılan ayardır. Bu ayar artık **Kapalı** ayarıyla aynıdır. Bu ayar ilk kullanıma sunulduğunda **Açık** ayarına eşdeğerdi. Zaman içinde, [varsayılan olarak güvenli](secure-by-default.md) ilkeleri sayesinde bu ayar tüm müşteriler için aşamalı olarak **Kapalı** olarak değiştirildi. Daha fazla bilgi için [bu blog gönderisini inceleyin](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888).
- **Açık**: Otomatik dış iletmeye izin verilir ve kısıtlanmaz.
- **Kapalı**: Otomatik dış iletme devre dışı bırakılır ve gönderene teslim edilmedi raporu (NDR veya geri dönen ileti olarak da bilinir) neden olur.

Bu ayarları yapılandırma yönergeleri için bkz. [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - Otomatik iletmeyi devre dışı bırakmak, iletileri dış adreslere yönlendiren gelen kutusu kurallarını (kullanıcılar) veya posta kutusu iletmeyi (yöneticiler) devre dışı bırakır.
> - İletilerin iç kullanıcılar arasında otomatik olarak iletilmesi, giden istenmeyen posta filtresi ilkelerindeki ayarlardan etkilenmez.

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Giden istenmeyen posta filtresi ilke ayarları diğer otomatik e-posta iletme denetimleriyle nasıl çalışır?

Yönetici olarak, otomatik e-posta iletmeye izin verecek veya bunları engelleyecek başka denetimler yapılandırmış olabilirsiniz. Örneğin:

- [Dış etki alanlarının](/exchange/mail-flow-best-practices/remote-domains/remote-domains) bir kısmına veya tümüne otomatik e-posta iletmeye izin vermek veya bunları engellemek için uzak etki alanları.
- Dış alıcılara otomatik olarak iletilen iletileri algılamak ve engellemek için Exchange [posta akışı kurallarındaki](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) koşullar ve eylemler (aktarım kuralları olarak da bilinir).

Bir ayar dış iletmeye izin verdiğinde, ancak başka bir ayar dış iletmeyi engellediğinde, blok genellikle kazanır. Örnekler aşağıdaki tabloda açıklanmıştır:

|Senaryo|Sonuç|
|---|---|
|<ul><li>Uzak etki alanı ayarlarını otomatik iletmeye izin verecek şekilde yapılandırabilirsiniz.</li><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme **Kapalı** olarak ayarlanır.</li></ul>|Etkilenen etki alanlarındaki alıcılara otomatik olarak iletilen iletiler engellenir.|
|<ul><li>Uzak etki alanı ayarlarını otomatik iletmeye izin verecek şekilde yapılandırabilirsiniz.</li><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme **, Otomatik - Sistem denetiminde** olarak ayarlanır.</li></ul>|Etkilenen etki alanlarındaki alıcılara otomatik olarak iletilen iletiler engellenir. <p> Daha önce açıklandığı gibi **, Otomatik - Sistem denetimi** **Açık** olarak kullanılıyordu, ancak ayar zaman içinde tüm kuruluşlarda **Kapalı** olarak değiştirildi. <p> Mutlak netlik için, giden istenmeyen posta filtresi ilkenizi **Açık** veya **Kapalı** olarak yapılandırmanız gerekir.|
|<ul><li>Giden istenmeyen posta filtresi ilkesinde otomatik iletme **Açık** olarak ayarlandı</li><li>Otomatik olarak iletilen e-postayı engellemek için posta akışı kurallarını veya uzak etki alanlarını kullanırsınız.</li></ul>|Etkilenen alıcılara otomatik olarak iletilen iletiler, posta akışı kuralları veya uzak etki alanları tarafından engellenir.|

Bu davranışı (örneğin), giden istenmeyen posta filtresi ilkelerinde otomatik iletmeye izin vermek için kullanabilirsiniz, ancak uzak etki alanlarını kullanarak kullanıcıların iletileri iletebileceği dış etki alanlarını denetleyebilirsiniz.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Otomatik olarak iletilen kullanıcıları bulma

Bulut tabanlı hesaplar için [otomatik olarak iletilen iletiler raporunda](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) , iletileri dış alıcılara otomatik olarak iletilen kullanıcılar hakkındaki bilgileri görebilirsiniz. Microsoft 365 aracılığıyla şirket içi e-posta sisteminden otomatik olarak iletilen şirket içi kullanıcılar için, bu kullanıcıları izlemek için bir posta akışı kuralı oluşturmanız gerekir. Posta akışı kuralı oluşturma yönergeleri için bkz. [Posta akışı kuralı oluşturmak için EAC'yi kullanma](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Exchange yönetim merkezinde (EAC) posta akışı kuralı oluşturmak için aşağıdaki bilgiler gereklidir:

- (koşul): **İleti üst bilgisi** \> **bu metin desenleri ile eşleşiyorsa** **bu kuralı uygulayın**. Bu seçeneği görmek için **Diğer seçenekler'e** tıklamanız gerekebileceğini unutmayın.
  - **Üst bilgi adı**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Üst bilgi değeri**: `.`

  Koşul şöyle görünür: **'X-MS-Exchange-Inbox-Rules-Loop'** üst bilgisi **'.'**

  Bu koşul, üst bilgi için herhangi bir değerle eşleşecektir.

- (İsteğe bağlı) **Aşağıdakileri yapın** (eylem): İsteğe bağlı bir eylem yapılandırabilirsiniz. Örneğin, **İleti özelliklerini** \> değiştir eylemini kullanarak, üst bilgi adı **X-Forwarded** ve **True** değeriyle **bir ileti üst bilgisi ayarlayabilirsiniz**. Ancak, bir eylemi yapılandırmak gerekli değildir.
- **Önem derecesi düzeyiyle Bu değeri Denetle'yi** **Düşük**, **Orta** veya **Yüksek** değerine ayarlayın. Bu ayar, iletilen kullanıcıların ayrıntılarını almak için [Exchange aktarım kuralı raporunu](view-email-security-reports.md#exchange-transport-rule-report) kullanmanıza olanak tanır.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="İletilen iletileri tanımlama kuralı için EAC'deki Posta akışı kuralı özellikleri" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::

## <a name="blocked-email-forwarding-messages"></a>Engellenen e-posta iletme iletileri

Otomatik olarak iletilen bir ileti algılandığında ve [giden istenmeyen posta filtresi](configure-the-outbound-spam-policy.md) ilkesi bu etkinliği *engellediğinde* , ileti aşağıdaki bilgileri içeren bir NDR'de gönderene döndürülür:

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
