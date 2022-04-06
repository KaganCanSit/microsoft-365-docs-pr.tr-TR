---
title: SIEM araçlarınızı Uç Nokta için Microsoft Defender ile tümleştirme
description: Olayları ve uyarıları almayı ve SIEM araçlarını tümleştirmeyi öğrenin.
keywords: siem, güvenlik bilgileri ve olay yönetimi araçlarını yapılandırma, splunk, arcsight, özel göstergeler, rest API, uyarı tanımları, risk göstergeleri
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
ms.openlocfilehash: d679ac0d01a7e922e49b72b574a43e6f684179f9
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664512"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>SIEM araçlarınızı Uç Nokta için Microsoft Defender ile tümleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanarak uyarıları alma

> [!NOTE]
>
> [Uç Nokta için Microsoft Defender Uyarısı](alerts.md), cihazda gerçekleşen bir veya daha fazla şüpheli veya kötü amaçlı olaydan ve bunların ilgili ayrıntılarından oluşur. Uç Nokta için Microsoft Defender Uyarı API'si, uyarı tüketimi için en son API'dir ve her uyarı için ilgili kanıtların ayrıntılı bir listesini içerir. Daha fazla bilgi için bkz [. Uyarı yöntemleri ve özellikleri ve](alerts.md) [Liste uyarıları](get-alerts.md).

Uç Nokta için Microsoft Defender, kayıtlı bir AAD için OAuth 2.0 kimlik doğrulama protokolunu kullanarak Azure Active Directory 'da (AAD) kurumsal kiracınızdan bilgi alan güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını destekler AAD  ortamınızda yüklü olan belirli SIEM çözümünü veya bağlayıcısını temsil eden uygulama.

Daha fazla bilgi için bkz.:

- [api lisansını ve kullanım koşullarını Uç Nokta için Microsoft Defender](api-terms-of-use.md) 
- [Uç Nokta için Microsoft Defender API’lere erişin](apis-intro.md)
- [Merhaba Dünya örnek (bir uygulamanın Azure Active Directory'ye nasıl kaydedildiği açıklanır)](api-hello-world.md)
- [Uygulama bağlamıyla erişim alın](exposed-apis-create-app-webapp.md)


Uç Nokta için Microsoft Defender şu anda aşağıdaki SIEM çözüm tümleştirmelerini destekler: 

- [Microsoft 365 Defender ve Uç Nokta için Microsoft Defender olaylarından ve uyarılardan olay ve uyarı alma REST API'leri](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Microsoft 365 Defender olay akış API'sinden Uç Nokta için Microsoft Defender olayları alma](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Microsoft 365 Defender ve Uç Nokta için Microsoft Defender olaylarından ve uyarılardan olay ve uyarı alma REST API'leri

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Microsoft 365 Defender olayları REST API'sinden olayları alma

Microsoft 365 Defender olayları API'si hakkında daha fazla bilgi için bkz. [olay yöntemleri ve özellikleri](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Uç Nokta için Microsoft Defender uyarıları REST API'sinden uyarıları alma

Uç Nokta için Microsoft Defender uyarıları API'si hakkında daha fazla bilgi için bkz. [uyarı yöntemleri ve özellikleri](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender ile SIEM aracı tümleştirmesi

### <a name="splunk"></a>Splunk

Splunk için aşağıdakileri destekleyen Microsoft 365 Defender Eklentisini kullanma:

- Uç Nokta için Microsoft Defender uyarıları alma
- Splunk içinden Uç Nokta için Microsoft Defender uyarıları güncelleştirme

Splunk için Microsoft 365 Defender Eklentisi hakkında daha fazla bilgi için bkz. [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Mikro Odak ArcSight

Microsoft 365 Defender için yeni SmartConnector, Uç Nokta için Microsoft Defender dahil olmak üzere tüm Microsoft 365 Defender ürünlerden gelen uyarıları içeren olayları ArcSight'a aktarır ve bunları Ortak Olay Çerçevesi (CEF) ile eşler.

Microsoft 365 Defender için yeni ArcSight SmartConnector hakkında daha fazla bilgi için [ArcSight Ürün belgelerine bakın](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector, Microsoft 365 Defender için önceki FlexConnector'ın yerini alır.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>Uç Nokta için Microsoft Defender içeren IBM QRadar Microsoft 365 Defender tümleştirmesi Microsoft 365 Defender [artık Uç Nokta için Microsoft Defender](../defender/streaming-api.md) dahil olmak üzere Microsoft 365 Defender ürünlerden akış olayı verilerinin alımına olanak tanıyan Microsoft 365 Defender Akış API'si. Yeni QRadar Microsoft 365 Defender DSM hakkında daha fazla bilgi için bkz. [IBM QRadar Ürün Belgeleri](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender) ve Akış API'sinin desteklediği olay türleri hakkında daha fazla bilgi için bkz[. Desteklenen olay türleri](../defender/supported-event-types.md).

Yeni müşteriler artık önceki QRadar Microsoft Defender ATP Cihaz Destek Modülü (DSM) kullanılarak eklenmemektedir ve mevcut müşterilerin tüm Microsoft 365 Defender ürünleriyle tek tümleştirme noktası olarak yeni Microsoft 365 Defender DSM'yi benimsemeleri teşvik edilir.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Microsoft 365 Defender olay akış API'sinden Uç Nokta için Microsoft Defender olayları alma

Microsoft 365 Defender akış olayı verileri, Uç Nokta için Microsoft Defender ve diğer Microsoft Defender ürünlerinden gelen uyarıları ve diğer olayları içerir. Bu olaylar bir Azure Depolama Hesabına veya Azure Event Hubs aktarılabilir. Event Hubs aracılığıyla tümleştirme modeli şu anda Splunk ve IBM QRadar tarafından desteklenmektedir.

Daha fazla bilgi için bkz. [Microsoft 365 Defender SIEM tümleştirmesi](../defender/configure-siem-defender.md).
