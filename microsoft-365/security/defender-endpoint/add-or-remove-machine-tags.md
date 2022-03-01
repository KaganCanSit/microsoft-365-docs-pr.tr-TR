---
title: Makine Etiketleri API'si Ekleme veya Kaldırma
description: Uç Nokta için Microsoft Defender'da makineye etiket eklemek veya kaldırmak için Makine etiketleri API'sini Ekle veya Kaldır'ı kullanmayı öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, etiketler, makine etiketleri
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
ms.openlocfilehash: 2ec34011d00e77c5e32f58567a0b705cf7c0dc1c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996527"
---
# <a name="add-or-remove-machine-tags-api"></a>Makine Etiketleri API'si Ekleme veya Kaldırma

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender ](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender ](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Belirli bir Makineye etiket ekler veya [etiketi kaldırır](machine.md).

## <a name="limitations"></a>Sınırlamalar

1. Yapılandırılmış bekletme sürenize göre en son görülen makinelerde gönderi yayınlarız.

2. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. [Uç Nokta API'leri için Defender Kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Machine.ReadWrite.All|'Tüm makine bilgilerini okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Machine.ReadWrite|'Makine bilgilerini okuma ve yazma'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Güvenlik ayarını yönet'. Daha fazla bilgi için ( [Daha fazla bilgi için bkz. Rol](user-roles.md) oluşturma ve yönetme)
> - Kullanıcının makine grubu ayarlarına göre makineye erişimi olması gerekir (Daha fazla bilgi için bkz [. Makine gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/tags
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
Değer|Dize|Etiket adı. **Gerekli**.
Eylem|Enum|Ekle veya Kaldır'ı seçin. İzin verilen değerler: 'Ekle' veya 'Kaldır'. **Gerekli**.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 200 - Tamam yanıt kodunu ve güncelleştirilmiş Makine'i döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

Burada, makine etiketi ekleyen bir istek örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/tags
```

```json
{
  "Value" : "test Tag 2",
  "Action": "Add"
}
```

- Makine etiketini kaldırmak için, isteğin gövdesinde 'Ekle' yerine Eylem'i 'Kaldır' olarak ayarlayın.
