---
title: SIEM araçlarınızı Microsoft 365 Defender ile tümleştirin
description: REST API'yi kullanmayı ve algılamaları almak ve çekmek için desteklenen güvenlik bilgilerini ve olay yönetimi araçlarını yapılandırmayı öğrenin.
keywords: siem, güvenlik bilgileri ve olay yönetimi araçlarını yapılandırma, splunk, arcsight, özel göstergeler, rest API, uyarı tanımları, risk göstergeleri
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
ms.openlocfilehash: 3e2772fd458c60e48f78c0d4b816cdac8ca25940
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530329"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>SIEM araçlarınızı Microsoft 365 Defender ile tümleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanarak olayları ve akış olay verilerini Microsoft 365 Defender çekme

> [!NOTE]
>
> - [Microsoft 365 Defender Olaylar](incident-queue.md), bağıntılı uyarı koleksiyonlarından ve bunların kanıtlarından oluşur.
> - [Microsoft 365 Defender Akış API'si](streaming-api.md), olay verilerini Microsoft 365 Defender'dan olay hub'larına veya Azure depolama hesaplarına akışla bildirir.

Microsoft 365 Defender, ortamınızda yüklü olan belirli bir SIEM çözümünü veya bağlayıcısını temsil eden kayıtlı bir AAD uygulaması için OAuth 2.0 kimlik doğrulama protokolü kullanılarak Azure Active Directory'de (AAD) kurumsal kiracınızdan bilgi alan güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını destekler. 

Daha fazla bilgi için bkz.:

- [Microsoft 365 Defender API'ler lisansı ve kullanım koşulları](api-terms.md)
- [Microsoft 365 Defender API'lerine erişme](api-access.md)
- [Merhaba Dünya örneği](api-hello-world.md)
- [Uygulama bağlamıyla erişim alın](api-create-app-web.md)

Güvenlik bilgilerini almak için iki birincil model vardır: 

1.  Azure'daki bir REST API'den Microsoft 365 Defender olayları ve bunların içerdiği uyarıları alma. 

2.  Akış olayı verilerini Azure Event Hubs veya Azure Depolama Hesapları aracılığıyla alma. 

Microsoft 365 Defender şu anda aşağıdaki SIEM çözüm tümleştirmelerini destekler: 

- [Olaylar REST API'sinden olayları alma](#ingesting-incidents-from-the-incidents-rest-api)
- [Olay Hub'ı aracılığıyla akış olay verilerini alma](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Olaylar REST API'sinden olayları alma

### <a name="incident-schema"></a>Olay şeması
İçerilen uyarı ve kanıt varlıkları meta verileri de dahil olmak üzere Microsoft 365 Defender olay özellikleri hakkında daha fazla bilgi için bkz. [Şema eşleme](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Microsoft Security için aşağıdakileri destekleyen yeni, tam olarak desteklenen Splunk Eklentisini kullanma:

- Splunk'un Ortak Bilgi Modeli'ne (CIM) eşlenen aşağıdaki ürünlerden gelen uyarıları içeren olayları alma:

  - Microsoft 365 Defender
  - Uç Nokta için Microsoft Defender
  - Kimlik için Microsoft Defender ve Azure Active Directory Kimlik Koruması
  - Bulut Uygulamaları için Microsoft Defender

- Uç Nokta için Defender uyarılarını alma (Uç Nokta için Defender'ın Azure uç noktasından) ve bu uyarıları güncelleştirme

- Microsoft 365 Defender Olayları ve/veya Uç Nokta için Microsoft Defender Uyarılarını güncelleştirme desteği ve ilgili panolar Splunk için Microsoft 365 Uygulaması'na taşındı. 

Daha fazla bilgi için:

- Microsoft Güvenliği için Splunk Eklentisi, bkz. [Splunkbase'de Microsoft Güvenlik Eklentisi](https://splunkbase.splunk.com/app/6207/#/overview)

- Splunk için Microsoft 365 Uygulaması, bkz. [Splunkbase üzerinde Microsoft 365 Uygulaması](https://splunkbase.splunk.com/app/3786/)

### <a name="micro-focus-arcsight"></a>Mikro Odak ArcSight

Microsoft 365 Defender için yeni SmartConnector olayları ArcSight'a alıyor ve bunları Common Event Framework (CEF) ile eşler.

Microsoft 365 Defender için yeni ArcSight SmartConnector hakkında daha fazla bilgi için bkz. [ArcSight Ürün Belgeleri](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector, kullanım dışı bırakılan Uç Nokta için Microsoft Defender için önceki FlexConnector'ın yerini alır.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Event Hubs aracılığıyla akış olayı verilerini alma

öncelikle olayları AAD kiracınızdan Event Hubs veya Azure Depolama Hesabınıza akışla aktarmanız gerekir. Daha fazla bilgi için bkz [. Akış API'si](../defender/streaming-api.md).

Akış API'sinin desteklediği olay türleri hakkında daha fazla bilgi için bkz. [Desteklenen akış olay türleri](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk

olayları Azure Event Hubs almak için Microsoft Cloud Services için Splunk Eklentisini kullanın.  

Microsoft Cloud Services için Splunk Eklentisi hakkında daha fazla bilgi için bkz. [Splunkbase'de Microsoft Cloud Services Eklentisi](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Event Hubs veya Azure Depolama Hesabı aracılığıyla Microsoft 365 Defender ürünlerden akış olay verilerinin alımına olanak tanıyan [Microsoft 365 Defender Akış API'sini](streaming-api.md) çağıran yeni IBM QRadar Microsoft 365 Defender Cihaz Destek Modülü'ni (DSM) kullanın. Desteklenen olay türleri hakkında daha fazla bilgi için bkz [. Desteklenen olay türleri](supported-event-types.md).
