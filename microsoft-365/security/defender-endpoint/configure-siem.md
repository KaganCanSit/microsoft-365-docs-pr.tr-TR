---
title: SIEM araçlarınızı el ile Uç Nokta için Microsoft Defender
description: Olayları ve uyarıları nasıl estersiniz ve SIEM araçlarını tümleştirin.
keywords: siem, güvenlik bilgileri ve olay yönetim araçları, splunk, arcsight, özel göstergeler, rest api, uyarı tanımları, güvenlik güvenliği göstergeleri yapılandırma
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ed88048b506ecfcddb8394667e7d800927fc1d83
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634921"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>SIEM araçlarınızı el ile Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanarak uyarı uyarısı

> [!NOTE]
>
> [Uç Nokta için Microsoft Defender Uyarısı](alerts.md), cihazda meydana gelen bir veya birden çok şüpheli veya kötü amaçlı olaydan ve bu olaylarla ilgili ayrıntılardan oluşur. Uyarı Uç Nokta için Microsoft Defender API'si, uyarı tüketimi için en son API'dir ve her uyarı için ayrıntılı bir kanıt listesi içerir. Daha fazla bilgi için bkz [. Uyarı yöntemleri ve özellikleri](alerts.md) ve [Liste uyarıları](get-alerts.md).

Uç Nokta için Microsoft Defender, kaydedilmiş bir kiracı için OAuth 2.0 kimlik doğrulama protokolünü kullanarak Azure Active Directory'te (AAD) kurumsal kiracıdan bilgi alan güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını AAD  ortamınıza yüklenmiş belirli SIEM çözümünü veya bağlayıcıyı temsil eden uygulama.

Daha fazla bilgi için bkz.:

- [Uç Nokta için Microsoft Defender API'ler lisansı ve kullanım koşulları](api-terms-of-use.md) 
- [Uç Nokta için Microsoft Defender API’lere erişin](apis-intro.md)
- [Merhaba Dünya örnek (Azure Active Directory'de uygulamanın nasıl kayded Azure Active Directory](api-hello-world.md)
- [Uygulama bağlamıyla erişim alın](exposed-apis-create-app-webapp.md)


Uç Nokta için Microsoft Defender şu anda aşağıdaki SIEM çözümü tümleştirmelerini destekle almaktadır: 

- [İlk ve son olaylardan olayları ve Microsoft 365 Defender ve REST API'lerini Uç Nokta için Microsoft Defender ve uyarıları](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [En çok Uç Nokta için Microsoft Defender akışı API'sinde Microsoft 365 Defender akışı api'sini kullanma](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>İlk ve son olaylardan olayları ve Microsoft 365 Defender ve REST API'lerini Uç Nokta için Microsoft Defender ve uyarıları

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>İlk ve son olaylardan Microsoft 365 Defender REST API'si

Olay API'si hakkında Microsoft 365 Defender için bkz. [olay yöntemleri ve özellikleri](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Alan uyarılarından uyarı Uç Nokta için Microsoft Defender REST API'si

En iyi uyarı API'si Uç Nokta için Microsoft Defender için bkz[. Uyarı yöntemleri ve özellikleri](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender ile SIEM aracı tümleştirmesi

### <a name="splunk"></a>Splunk

Splunk Microsoft 365 Defender Eklentiyi kullanma:

- Uyarı Uç Nokta için Microsoft Defender.
- Splunk'Uç Nokta için Microsoft Defender gelen uyarıları güncelleştirme

Splunk için Microsoft 365 Defender daha fazla bilgi için bkz. [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Uç Nokta için Microsoft Defender'tan ArcSight'a tüm Microsoft 365 Defender ürünlerinden uyarı içeren ve bunları Common Event Framework'e (CEF) eşlerken içeren yeni Microsoft 365 Defender olayları için SmartConnector.

Yeni ArcSight SmartConnector For ArcSight SmartConnector hakkında daha fazla bilgi Microsoft 365 Defender [bkz. ArcSight Ürün belgeleri](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector, aynı zaman için önceki FlexConnector'ın Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>MICROSOFT 365 DEFENDER'i de içeren IBM QRadar tümleştirmesi, Uç Nokta için Microsoft Defender aşağıdaki çağrıları alan yeni Microsoft 365 Defender Cihaz Desteği Modülü (DSM) tarafından desteklemektedir[. Microsoft 365 Defender dahil olmak üzere Microsoft 365 Defender](../defender/streaming-api.md) ürünlerinden etkinlik verileri akışına izin veren akış API'si Uç Nokta için Microsoft Defender. Yeni QRadar ürün türleri hakkında daha fazla bilgi Microsoft 365 Defender IÇIN [IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender) Ürün Belgelerine bakın ve Akış API'si desteklenen olay türleri hakkında daha fazla bilgi için bkz. Desteklenen [olay türleri](../defender/supported-event-types.md).

Yeni müşteriler artık önceki QRadar Microsoft Defender ATP Cihaz Desteği Modülü (DSM) kullanılarak ekli olarak sunulmaktadır ve mevcut müşterilerin tüm Microsoft 365 Defender ürünleriyle tek tümleştirme noktası olarak yeni Microsoft 365 Defender DSM'yi benimsemeleri teşvik edilecektir.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>En çok Uç Nokta için Microsoft Defender akışı API'sinde Microsoft 365 Defender akışı api'sini kullanma

Microsoft 365 Defender verilerini akış olarak kullanabilirsiniz, bu akışta Uç Nokta için Microsoft Defender Microsoft Defender ürünlerine karşı uyarılar ve diğer olaylar yer almaktadır. Bu olaylar bir Azure Depolama Hesabına veya Azure Event Hubs. Etkinlik hub'ları aracılığıyla tümleştirme modeli şu anda Splunk ve IBM QRadar tarafından destek almaktadır.

Daha fazla bilgi için bkz[. SIEM Microsoft 365 Defender tümleştirmeyi tümleştirme](../defender/configure-siem-defender.md).
