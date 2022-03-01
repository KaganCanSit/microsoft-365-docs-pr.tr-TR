---
title: SIEM araçlarınızı el ile Microsoft 365 Defender
description: REST API'sini kullanmayı ve algılamaları almak ve çekmek için desteklenen güvenlik bilgileri ile olay yönetim araçlarını yapılandırmayı öğrenin.
keywords: siem, güvenlik bilgileri ve olay yönetim araçları, splunk, arcsight, özel göstergeler, rest api, uyarı tanımları, güvenlik güvenliği göstergeleri yapılandırma
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 210705bd3392e4aeeadd815ed8c1840e772f6ad9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005491"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>SIEM araçlarınızı el ile Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Güvenlik Microsoft 365 Defender ve olay yönetimi (SIEM) araçlarını kullanarak olay olaylarını ve akış verilerini çekme

> [!NOTE]
>
> - [Microsoft 365 Defender olaylar](incident-queue.md) ilişkili uyarılardan ve bunların kanıtlarından oluşan koleksiyonlardan oluşur.
> - [Microsoft 365 Defender API'si](streaming-api.md) akışlarını, olay Microsoft 365 Defender hub'lara veya Azure depolama hesaplarına akış olarak sunar.

Microsoft 365 Defender, bilgisayarınıza yüklenmiş belirli SIEM çözümünü veya bağlayıcıyı temsil eden kayıtlı bir AAD uygulaması için OAuth 2.0 kimlik doğrulama protokolünü kullanarak Azure Active Directory'te kurumsal kiracıdan bilgi alan güvenlik bilgileri ve olay yönetimi AAD (SIEM) araçlarını destekler ortamını da s belirttiysiniz. 

Daha fazla bilgi için bkz.:

- [Microsoft 365 Defender API'ler lisansı ve kullanım koşulları](api-terms.md)
- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [Hello Dünya örneği](api-hello-world.md)
- [Uygulama bağlamıyla erişim elde](api-create-app-web.md)

Güvenlik bilgilerini almak için iki birincil model vardır: 

1.  Azure'Microsoft 365 Defender REST API'si ile ilgili olayları ve bunların içerdiği uyarıları kabul. 

2.  Azure Olay Hub'ları veya Azure Veri Kaynağı hesapları aracılığıyla etkinlik Depolama. 

Microsoft 365 Defender, şu anda aşağıdaki SIEM çözümü tümleştirmelerini destekle almaktadır: 

- [Olaylardan olay rest API'siniesting](#ingesting-incidents-from-the-incidents-rest-api)
- [Olay Hub'ı aracılığıyla etkinlik verileri akışıyla ilgili bilgi](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Olaylardan olay rest API'siniesting

### <a name="incident-schema"></a>Olay şeması
Meta verilerin içerdiği uyarı Microsoft 365 Defender kanıt varlıkları da dahil olmak üzere olay özellikleri hakkında daha fazla bilgi için bkz. [Şema eşlemesi](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Splunk Microsoft 365 Defender Eklentiyi kullanma:

- Splunk'un Ortak Bilgi Modeli'ne (CIM) eşlenen aşağıdaki ürünlerden uyarılar içeren olayları almak:

  - Microsoft 365 Defender
  - Uç Nokta için Microsoft Defender
  - Kimlik ve Kimlik Koruması Azure Active Directory Microsoft Defender
  - Bulut Uygulamaları için Microsoft Defender

- Splunk'un Microsoft 365 Defender olayları güncelleştirme

- Uç Nokta uyarıları için Ingesting Defender (Uç Nokta Azure uç noktası için Defender'dan) ve bu uyarıları güncelleştirme

Splunk için Microsoft 365 Defender daha fazla bilgi için bkz. [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Olaylarda ArcSight Microsoft 365 Defender için yeni SmartConnector ve bunları Ortak Etkinlik Çerçevesine (CEF) eşler.

Yeni ArcSight SmartConnector For ArcSight SmartConnector hakkında daha fazla bilgi Microsoft 365 Defender [bkz. ArcSight Ürün Belgeleri](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector, Uç Nokta için Microsoft Defender için önceki FlexConnector'un yerini almaktadır.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Etkinlik Hub'ları aracılığıyla etkinlik verileri akışı

İlk olarak, etkinlik hub'lar veya Azure AAD Hesabınıza etkinlik akışı Depolama gerekir. Daha fazla bilgi için bkz. [Akış API'si](../defender/streaming-api.md).

Akış API'si tarafından desteklenen olay türleri hakkında daha fazla bilgi için bkz. [Desteklenen akış olay türleri](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk
Azure Etkinlik Hub'larından etkinlikler eklemek üzere Microsoft Bulut Hizmetleri için Splunk Eklentilerini kullanın.  


Microsoft Bulut Hizmetleri için Splunk Eklentisi hakkında daha fazla bilgi için bkz. [splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Microsoft 365 Defender ürünlerinden etkinlik verisi akışına izin veren [Microsoft 365 Defender Akış API'sini](streaming-api.md) çağıran yeni IBM QRadar Microsoft 365 Defender Cihaz Desteği Modülü'Microsoft 365 Defender kullanın. Desteklenen olay türleri hakkında daha fazla bilgi için bkz. [Desteklenen olay türleri](supported-event-types.md).
