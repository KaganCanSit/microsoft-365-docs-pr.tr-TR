---
title: Raporlama ve ileti izleme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, Güvenlik Koruması (EOP) yöneticileri tarafından kullanılabilen raporlar Microsoft Exchange Online sorun giderme araçları hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d4f0289054baec0e5bcedf4e9e3d434ab51ef92b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986512"
---
# <a name="reporting-and-message-trace-in-eop"></a>EOP'de raporlama ve ileti izleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu olan Exchange Online kuruluşlarında, EOP, genel durumu ve durumunu belirlemenize yardımcı olacak birçok farklı rapor sunar. Belirli olayları (örneğin, hedeflenen alıcılarına gelmeyen bir ileti) ve denetim raporlarını uyumluluk gereksinimlerine yardımcı olacak sorunları gidermenize yardımcı olacak araçlar da vardır.

## <a name="usage-reports"></a>Kullanım raporları

- **Microsoft 365 grupları etkinliği**: Oluşturulan ve kullanılan grup Microsoft 365 sayısı hakkında bilgileri görüntüleme. Daha fazla bilgi için bkz [Microsoft 365 Yönetim merkezinde Raporlar - Gruplarda Microsoft 365.](../../admin/activity-reports/office-365-groups.md)
- **E-posta** etkinliği: Tüm kuruluşta ve belirli kullanıcılar tarafından gönderilen, alınan ve okunan ileti sayısıyla ilgili bilgileri görüntüleme. Daha fazla bilgi için bkz[. Microsoft 365 Merkezi'nde Raporlar - E-posta etkinliği](../../admin/activity-reports/email-activity.md).
- **E-posta** uygulaması kullanımı: Kullanılan e-posta uygulamaları hakkında bilgileri görüntüleme. Bu, her uygulama için toplam bağlantı sayısını ve bağlanan Outlook sürümlerini içerir. Daha fazla bilgi için bkz[. Microsoft 365 Merkezi'nde Raporlar - E-posta uygulamaları kullanımı](../../admin/activity-reports/email-apps-usage.md).
- **Posta kutusu** kullanımı: Posta kutuları için kullanılan depolama, kota tüketimi, öğe sayısı ve son etkinlik (gönderme veya okuma etkinliği) hakkında bilgileri görüntüleme. Daha fazla bilgi için bkz[. Microsoft 365 Merkezi'nde Raporlar - Posta Kutusu kullanımı](../../admin/activity-reports/mailbox-usage.md).

## <a name="security-reports-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında güvenlik raporları

Bu iyileştirilmiş raporlar, özet bilgileri ve daha fazla ayrıntı için detaya gitme olanağı içeren EOP yöneticileri için etkileşimli bir raporlama deneyimi sağlar.

- **Office 365 için Defender**: Kasa için Microsoft Defender'ın bir parçası olan bağlantılar Kasa Ekleri hakkında Office 365. Daha fazla bilgi için bkz[. Office 365 portalında raporları görüntülemek Microsoft 365 Defender.](view-reports-for-mdo.md)
- **EOP**: Kötü amaçlı yazılım algılamaları, kimlik e-postası, istenmeyen posta algılamaları ve kuruluştan gelen ve bu posta akışı ile ilgili bilgileri görüntüleme. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalında e-posta Microsoft 365 Defender görüntüleme](view-email-security-reports.md).

## <a name="mail-flow-insights-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde & öngörüleri

Daha fazla bilgi için, [Güvenlik ve Uyumluluk Merkezi'nde Posta & bilgilerine bakın](mail-flow-insights-v2.md).

## <a name="custom-reports-using-microsoft-graph"></a>Microsoft Graph kullanan özel raporlar

Yönetim merkezinde, Microsoft Graph kullanarak, programlı olarak kullanılabilen raporlar Graph. Daha fazla bilgi için bkz[. Microsoft Graph Ve Microsoft Office 365](/graph/overview) [raporlarıyla çalışmaya genel bakış Graph](/graph/api/resources/report).

## <a name="message-trace"></a>İleti izleme

EOP üzerinden seyahat eden e-posta iletilerini takip eder. Bir e-posta iletisi hizmet tarafından alınmıştır, reddedilmiş, ertelenmiştir veya teslim edilir. Ayrıca, son durumuna ulaşmadan önce ileti üzerinde hangi eylemlerin gerçekleştirildiklerini de gösterir.

Bu bilgileri kullanıcınizin sorularını etkili bir şekilde yanıtlamak, posta akışı sorunlarını gidermek, ilke değişikliklerini doğrulamak ve yardım için teknik destek ile iletişim kurma ihtiyacını gidermek için kullanabilirsiniz.

Bkz[. Portalda ileti Microsoft 365 Defender.](message-trace-scc.md)

## <a name="audit-logging"></a>Denetim günlüğü

Yöneticiler tarafından yapılan belirli değişiklikleri izler. Bu raporlar yapılandırma sorunlarını gidermenize veya güvenlik veya uyumlulukla ilgili sorunların nedenini bu sorunlara yardımcı olabilir. Daha [fazla bilgi için bkz. Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>Veri kullanılabilirliğini ve gecikme süresini raporlama ve ileti izleme

Aşağıdaki tabloda EOP raporlama ve ileti izleme verileri ne zaman ve ne kadar süreyle kullanılabilir olduğu açık almaktadır.

<br>

****

|Rapor türü|Kullanılabilir veriler (geriye dönüp bak)|Gecikme süresi|
|---|---|---|
|Posta koruması özet raporları|90 gün|İleti verileri toplama işlemi büyük ölçüde 24-48 saat içinde tamamlanır. Bazı küçük artımlı toplu değişiklikler en çok 5 gün olabilir.|
|Posta koruması ayrıntı raporları|90 gün|7 saatten az olan ayrıntılı veriler için verilerin 24 saat içinde görünmesi gerekir, ancak 48 saate kadar tamamlanamayabilirsiniz. Bazı küçük artımlı değişiklikler en çok 5 gün olabilir. <p> 7 günlükten daha eski iletilerin ayrıntılı raporlarını görüntülemek için, sonuçlar birkaç saat sürebilir.|
|İleti izleme verileri|90 gün|7 günlükten az olan iletiler için bir ileti izleme çalıştırsanız, iletilerin 5-30 dakika içinde görünmesi gerekir.<p> 7 günlükten daha eski iletiler için bir ileti izleme çalıştırsanız, sonuçlar birkaç saat kadar sürebilir.|
|

> [!NOTE]
> Hem yönetim merkezi hem de uzak PowerShell üzerinden veri kullanılabilirliği ve gecikme süresi aynı olur.
