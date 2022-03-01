---
title: Gönderme veya Güncelleştirme Göstergesi API'si
description: Uç Nokta için Microsoft Defender'da Yeni Bir Gösterge varlıkını göndermek veya güncelleştirmek için Gönderme veya Güncelleştirme Göstergesi API'sini nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'si, desteklenen api'ler, gönder, ti, gösterge, güncelleştirme
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
ms.openlocfilehash: a3fc1a0ce2f7d02ad8ed6804b99621f78fb859d3
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010814"
---
# <a name="submit-or-update-indicator-api"></a>Gönderme veya Güncelleştirme Göstergesi API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Submits or Updates new [Indicator](ti-indicator.md) entity.

IP'ler için CIDR'ye dikkatilemez.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.
2. Kiracı başına 15.000 etkin gösterge sınırı vardır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Ti.ReadWrite|'Okuma ve yazma Göstergeleri'
Uygulama|Ti.ReadWrite.All|'Tüm Göstergeleri okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Ti.ReadWrite|'Okuma ve yazma Göstergeleri'

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
:---|:---|:---
indicatorValue|Dize|Gösterge varlık [kimliği](ti-indicator.md) . **Gerekli**
indicatorType|Enum|Göstergenin türü. Olası değerler şöyledir: "FileSha1", "FileMd5", "CertificateThumbprint", "FileSha256", "IpAddress", "DomainName" ve "Url". **Gerekli**
eylem|Enum|Gösterge kuruluşta keşfedilecekse, alınacak eylem. Olası değerler şöyledir: "Uyarı", "Uyar", "Engelle", "Denetim, "BlockAndRemediate", "AlertAndBlock" ve "İzin Verildi". **Gerekli**. "Denetim" ile bir eylem oluşturulurken "GenerateAlert" parametresi "TRUE" olarak ayar olmalıdır.
uygulama|Dize|Göstergeyle ilişkili uygulama. Bu alan yalnızca yeni göstergeler için çalışır. Var olan bir göstergenin değerini güncelleştirmez. **İsteğe bağlı**
başlık|Dize|Gösterge uyarısı başlığı. **Gerekli**
açıklama|Dize|Göstergenin açıklaması. **Gerekli**
expirationTime|DateTimeOffset|Göstergenin sona erme zamanıdır. **İsteğe bağlı**
önem derecesi|Enum|Göstergenin önem derecesidir. Olası değerler şöyledir: "Bilgilendirme", "Düşük", "Orta" ve "Yüksek". **İsteğe bağlı**
recommendedActions|Dize|TI göstergesi uyarısı önerilen eylemler. **İsteğe bağlı**
rbacGroupNames|Dize|Göstergenin uygulanabilecek RBAC grup adlarının virgülle ayrılmış listesi. **İsteğe bağlı**
generateAlert|Enum|**Uyarı** oluşturma gerekirse Doğru, bu **gösterge** bir uyarı oluşturmazsa False.
## <a name="response"></a>Yanıt

- Başarılı olursa, bu yöntem yanıt gövdesinde 200 - Tamam yanıt kodu ve oluşturulan / güncelleştirilmiş Gösterge varlığı döndürür.[](ti-indicator.md)
- Başarılı değilse: Bu yöntem 400 - Kötü İstek olarak geri döner. Hatalı istek genellikle yanlış gövdeyi gösterir.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

```json
{
    "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
    "indicatorType": "FileSha1",
    "title": "test",
    "application": "demo-test",
    "expirationTime": "2020-12-12T00:00:00Z",
    "action": "AlertAndBlock",
    "severity": "Informational",
    "description": "test",
    "recommendedActions": "nothing",
    "rbacGroupNames": ["group1", "group2"]
}
```

## <a name="related-topic"></a>İlgili konu

- [Göstergeleri yönetme](manage-indicators.md)
