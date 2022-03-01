---
title: SIEM araçlarınızı Uç Nokta için Microsoft Defender ile tümleştirin
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
ms.openlocfilehash: 4c0462bcfae77677fca05132aaf0895b897bf788
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010731"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>SIEM araçlarınızı Uç Nokta için Microsoft Defender ile tümleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanarak uyarı uyarısı

> [!NOTE]
>
> [Uç Nokta Uyarısı için Microsoft Defender](alerts.md) , cihazda meydana gelen bir veya birden çok şüpheli veya kötü amaçlı olaydan ve onların ilgili ayrıntılarından oluşur. Uç Nokta Uyarı API'si için Microsoft Defender uyarı tüketimi için en son API'dir ve her uyarı için ayrıntılı bir kanıt listesi içerir. Daha fazla bilgi için bkz [. Uyarı yöntemleri ve özellikleri](alerts.md) ve [Liste uyarıları](get-alerts.md).

Uç Nokta için Microsoft Defender, ortamınıza yüklenmiş belirli SIEM çözümünü veya bağlayıcıyı temsil eden kayıtlı bir AAD uygulaması için OAuth 2.0 kimlik doğrulama protokolünü kullanarak Azure Active Directory'te kurumsal kiracıdan bilgi alan güvenlik bilgileri ve olay yönetimi AAD (SIEM) araçlarını destekler.

Daha fazla bilgi için bkz.:

- [Uç Nokta API'leri için Microsoft Defender lisansı ve kullanım koşulları](api-terms-of-use.md) 
- [Uç Nokta API'leri için Microsoft Defender'a erişme](apis-intro.md)
- [Hello Dünya örneği (Azure Active Directory'de bir uygulamanın nasıl kayded Azure Active Directory)](api-hello-world.md)
- [Uygulama bağlamıyla erişim elde](exposed-apis-create-app-webapp.md)


Uç Nokta için Microsoft Defender şu anda aşağıdaki SIEM çözümü tümleştirmelerini destekle almaktadır: 

- [Siteden olay ve uyarı Microsoft 365 Defender Uç nokta olayları ve REST API'leri için Microsoft Defender'ı uyarın](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Microsoft 365 Defender akışı API'sinde Uç nokta olayları için Microsoft Defender'ı kullanma](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Siteden olay ve uyarı Microsoft 365 Defender Uç nokta olayları ve REST API'leri için Microsoft Defender'ı uyarın

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>İlk ve son olaylardan Microsoft 365 Defender REST API'si

Olay API'si hakkında Microsoft 365 Defender için bkz. [olay yöntemleri ve özellikleri](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Uç nokta uyarıları REST API'si için Microsoft Defender'dan uyarı uyarısı

Uç nokta uyarıları API'si için Microsoft Defender hakkında daha fazla bilgi için bkz [. Uyarı yöntemleri ve özellikleri](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender ile SIEM aracı tümleştirmesi

### <a name="splunk"></a>Splunk

Splunk Microsoft 365 Defender Eklentiyi kullanma:

- Uç Nokta uyarıları için Microsoft Defender'ı satın alın
- Splunk'tan Uç Nokta için Microsoft Defender'da uyarıları güncelleştirme

Splunk için Microsoft 365 Defender daha fazla bilgi için bkz. [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Yeni Microsoft 365 Defender için SmartConnector, Uç Nokta için Microsoft Defender dahil olmak üzere tüm Microsoft 365 Defender ürünlerinden gelen uyarıları içeren olayları ArcSight'a alır ve bunları Common Event Framework'e (CEF) eşler.

Yeni ArcSight SmartConnector For ArcSight SmartConnector hakkında daha fazla bilgi Microsoft 365 Defender [bkz. ArcSight Ürün belgeleri](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector, aynı zaman için önceki FlexConnector'ın Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>Uç nokta için Microsoft Defender'ı içeren Microsoft 365 Defender ile IBM QRadar tümleştirmesi artık etkinlik verisi akışına izin veren [Microsoft 365 Defender Streaming API'sini](../defender/streaming-api.md) (DSM) çağıran yeni Microsoft 365 Defender Cihaz Desteği Modülü (DSM) tarafından destek almaktadır Microsoft 365 Defender için Microsoft Defender da dahil olmak üzere tüm ürünleri içerir. Yeni QRadar ürün türleri hakkında daha fazla bilgi Microsoft 365 Defender IÇIN [IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender) Ürün Belgelerine bakın ve Akış API'si desteklenen olay türleri hakkında daha fazla bilgi için bkz. Desteklenen [olay türleri](../defender/supported-event-types.md).

Yeni müşteriler artık önceki QRadar Microsoft Defender ATP Cihaz Desteği Modülü (DSM) kullanılarak ekli olarak sunulmaktadır ve mevcut müşterilerin tüm Microsoft 365 Defender ürünleriyle tek tümleştirme noktası olarak yeni Microsoft 365 Defender DSM'yi benimsemeleri teşvik edilecektir.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Microsoft 365 Defender akışı API'sinde Uç nokta olayları için Microsoft Defender'ı kullanma

Microsoft 365 Defender akış verileri, Uç Nokta için Microsoft Defender ve diğer Microsoft Defender ürünlerinin uyarılarını ve diğer olayları içerir. Bu olaylar bir Azure Depolama Hesabına veya Azure Olay Hub'ları'nına akışla yayın olabilir. Etkinlik hub'ları aracılığıyla tümleştirme modeli şu anda Splunk ve IBM QRadar tarafından destek almaktadır.

Daha fazla bilgi için bkz[. SIEM Microsoft 365 Defender tümleştirmeyi tümleştirme](../defender/configure-siem-defender.md).
