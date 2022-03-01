---
title: Virüsten koruma tarama API'sini çalıştırma
description: Cihazda virüsten koruma taraması çalıştırmayla ilgili çağrılar oluşturmak için bu API'yi kullanın.
keywords: api'ler, grafik api'leri, desteklenen api'ler, cihazı yalıtımtan kaldırma
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3208ff32c2adda051b79fea684af915a909dd062
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016510"
---
# <a name="run-antivirus-scan-api"></a>Virüsten koruma tarama API'sini çalıştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Bir Microsoft Defender Virüsten Koruma taramayı başlatma.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Bu eylem, 11. Windows 10 sürüm 1709 ve sonraki sürümler Windows kullanılabilir.
> - Etkin Microsoft Defender Virüsten Koruma virüsten koruma çözümü olsa da, diğer virüsten koruma çözümleriyle birlikte bir Microsoft Defender Virüsten Koruma (Microsoft Defender AV) taraması da çalıştırabilirsiniz. Microsoft Defender Virüsten Koruma Edilgen modunda olabilir. Daha fazla bilgi için uyumluluk [Microsoft Defender Virüsten Koruma bakın](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Makine.Tarama|'Makine tara'
Temsilcili (iş veya okul hesabı)|Makine.Tarama|'Makine tara'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Etkin düzeltme eylemleri' (Daha fazla bilgi için bkz [.](user-roles.md) Rol oluşturma ve yönetme)
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/runAntiVirusScan
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|dize|application/json

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
:---|:---|:---
Açıklama ekleme|Dize|Eylemle ilişkilendirmek için açıklama. **Gerekli**.
ScanType|Dize|Tarama türünü tanımlar. **Gerekli**.

**ScanType** , gerçekleştirmek istediğiniz tarama türünü kontrol eder ve aşağıdakilerden biri olabilir:

- **Hızlı**: Cihazda hızlı tarama gerçekleştirme
- **Tam**: Cihazda tam tarama gerçekleştirme

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 201, Yanıt kodu ve _MakineAction_ nesnesi oluşturuldu hata kodunu döndürür.

Aynı cihaz için virüsten koruma taraması çalıştırmak üzere birden çok API çağrısı gönderiyorsanız, "Eylem zaten devam ediyor" iletisiyle "bekleyen makine eylemi" veya HTTP 400'ü döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runAntiVirusScan 
```

```json
{
  "Comment": "Check machine for viruses due to alert 3212",
  "ScanType": "Full"
}
```
