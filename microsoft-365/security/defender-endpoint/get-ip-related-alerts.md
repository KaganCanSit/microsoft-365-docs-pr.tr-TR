---
title: IP ile ilgili uyarılar API'sini al
description: Uç Nokta için Microsoft Defender'ı kullanarak verilen IP adresiyle ilgili uyarı koleksiyonunu alma
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, ip, ilgili, uyarılar
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
ms.openlocfilehash: b46e67a6fe2d30a4b6480b88ea3a40f842227669
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997173"
---
# <a name="get-ip-related-alerts-api"></a>IP ile ilgili uyarılar API'sini al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması
Verilen IP adresiyle ilgili uyarı koleksiyonunu sağlar.


## <a name="limitations"></a>Sınırlamalar
1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.


## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. [Uç Nokta API'leri için Defender Kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alert.Read.All|'Tüm uyarıları oku'
Uygulama|Alert.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı) | Alert.Read | 'Uyarıları oku'
Temsilcili (iş veya okul hesabı) | Alert.ReadWrite | 'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)
> - Yanıt, cihaz grubu ayarlarına göre kullanıcının erişimi olan cihazlarla ilişkilendirilmiş uyarıları içerir (daha fazla bilgi için bkz. Cihaz grupları [](machine-groups.md) oluşturma ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET /api/ips/{ip}/alerts
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve IP varsa - Gövdede uyarı varlıklarının listesiyle 200 Tamam.[](alerts.md) IP adresi bilinmiyorsa ancak geçerli değilse boş bir küme döner.
IP adresi geçersizse HTTP 400 olarak döner.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/alerts
```
