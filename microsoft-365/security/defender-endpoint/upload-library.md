---
title: Dosyaları canlı yanıt kitaplığına Upload
description: Canlı yanıt kitaplığına dosya yüklemeyi öğrenin.
keywords: api'ler, graf api'leri, desteklenen API'ler, kitaplığa yükleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 8e0bc9ca78a7e0baad7c07e73790215618aff9ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873749"
---
#  <a name="upload-files-to-the-live-response-library"></a>Dosyaları canlı yanıt kitaplığına Upload  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Dosyayı canlı yanıt kitaplığına Upload.

## <a name="limitations"></a>Sınırlamalar

1.  Dosya boyutu üst sınırı 20 MB'tır.

2.  Bu API için hız sınırlamaları dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi için bkz. [Kullanmaya başlayın](apis-intro.md).


| İzin türü                    | Izni     | İzin görünen adı        |
|------------------------------------|----------------|--------------------------------|
| Uygulama                        | Library.Manage | Canlı yanıt kitaplığını yönetme |
| Temsilci (iş veya okul hesabı) | Library.Manage | Canlı yanıt kitaplığını yönetme |

## <a name="http-request"></a>HTTP isteği

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>İstek üst bilgileri

|  Name   |    Tür    |       Açıklama                         |
|-----------------|--------|--------------------------------|
| Yetkilendirme   | Dize | \<token>Taşıyıcı. Gerekli.      |
| İçerik Türü    | Dize | multipart/form-data. Gerekli. |

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde aşağıdaki parametreleri içeren bir form-data nesnesi sağlayın:

| Parametre         |     Tür         |       Açıklama                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Dosya                  | Dosya içeriği | Canlı yanıt kitaplığına yüklenecek dosya. Gerekli |
| Açıklama           | Dize       | Dosyanın açıklaması.                                  |
| ParametersDescription | Dize       | (İsteğe bağlı) Betiğin çalışması için gereken parametreler. Varsayılan değer boş bir dizedir.                |
| OverrideIfExists      | Boole      | (İsteğe bağlı) Zaten varsa dosyanın geçersiz kılınıp geçersiz kılınmayacağı. Varsayılan değer boş bir dizedir.          |



## <a name="response"></a>Yanıt

-   Başarılı olursa, bu yöntem 200 - Tamam yanıt kodunu ve yanıt gövdesinde karşıya yüklenen canlı yanıt kitaplığı varlığını döndürür.

-   Başarılı olmazsa: Bu yöntem 400 - Hatalı İstek döndürür.  
    Hatalı istek genellikle yanlış gövdeyi gösterir.

## <a name="example"></a>Örnek

Istek

Curl kullanan isteğin bir örneği aşağıda verilmiştir.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>İlgili konu

-  [Canlı yanıt çalıştır](run-live-response.md) 