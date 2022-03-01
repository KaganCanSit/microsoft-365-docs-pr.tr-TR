---
title: Kullanıcıyla ilgili makine API'sini edinin
description: Uç Nokta için Microsoft Defender'da kullanıcı kimliğiyle ilgili cihaz koleksiyonunu almak için Kullanıcıyla ilgili makineler al API'sini kullanmayı öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, kullanıcı, kullanıcı ile ilgili uyarılar
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
ms.openlocfilehash: 5dd8cbd36fdac4aa3d0661a9b418a30ec2bae44f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996034"
---
# <a name="get-user-related-machines-api"></a>Kullanıcıyla ilgili makine API'sini edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması
Verilen bir kullanıcı kimliğiyle ilgili cihaz koleksiyonunu verir.

## <a name="limitations"></a>Sınırlamalar

Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama |Machine.Read.All|'Tüm makine profillerini oku'
Uygulama |Machine.ReadWrite.All |'Tüm makine bilgilerini okuma ve yazma'
Temsilcili (iş veya okul hesabı) | Machine.Read | 'Makine bilgilerini oku'
Temsilcili (iş veya okul hesabı) | Machine.ReadWrite | 'Makine bilgilerini okuma ve yazma'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle'. Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md)
> - Yanıt, cihaz grubu ayarlarına göre yalnızca kullanıcının eriş erişeliklerini içerecektir. Daha fazla bilgi için bkz [. Cihaz grupları oluşturma ve yönetme](machine-groups.md).

## <a name="http-request"></a>HTTP isteği

```http
GET /api/users/{id}/machines
```

**Kimlik, tam UPN'değildir; yalnızca kullanıcı adıdır. (örneğin, /api/users/user1/machines user1@contoso.com makinelerini almak için)**

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve kullanıcı varsa - Gövdede makine varlıklarının listesiyle 200 Tamam.[](machine.md) Kullanıcı yoksa - boş bir kümeyle 200 Tamam.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/machines
```
