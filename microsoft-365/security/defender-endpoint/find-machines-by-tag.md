---
title: Etiket API'sini kullanarak cihazları bulma
description: Specifc etiketi içeren tüm cihazları bulma
keywords: api'ler, desteklenen api'ler, get, device, find, find device, by tag, tag
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
ms.openlocfilehash: 93363ba9cb6252a32406c0c29dfb7d757d2f411d
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996579"
---
# <a name="find-devices-by-tag-api"></a>Etiket API'sini kullanarak cihazları bulma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Makine [etikete](machine.md) [göre bulun](machine-tags.md).

`startswith` sorgusu da desteklene.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Machine.Read.All|'Tüm makine profillerini oku'
Uygulama|Machine.ReadWrite.All|'Tüm makine bilgilerini okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Machine.Read|'Makine bilgilerini oku'
Temsilcili (iş veya okul hesabı)|Machine.ReadWrite|'Makine bilgilerini okuma ve yazma'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Yanıt yalnızca kullanıcının cihaz grubu ayarlarına göre erişim iznine sahip olduğu cihazları içerir (Daha fazla bilgi için bkz. Cihaz [grupları oluşturma](machine-groups.md) ve yönetme)
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)
> - Yanıt yalnızca kullanıcının cihaz grubu ayarlarına göre erişim iznine sahip olduğu cihazları içerir (Daha fazla bilgi için bkz. Cihaz [grupları oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/findbytag?tag={tag}&useStartsWithFilter={true/false}
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-uri-parameters"></a>URI parametreleri isteği

Name|Tür|Açıklama
:---|:---|:---
etiket|Dize|Etiket adı. **Gerekli**.
useStartsWithFilter|Boole|True olarak ayar olduğunda, arama sorguda verilen etiketle başlayan etiket adına sahip tüm cihazları bulur. Varsayılan değer yanlış'tır. **İsteğe bağlı**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa - Yanıt gövdesinde makinelerin listesiyle 200 Tamam.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/machines/findbytag?tag=testTag&useStartsWithFilter=true
```
