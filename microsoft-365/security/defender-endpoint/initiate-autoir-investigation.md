---
title: Araştırma API'sini Başlat
description: Bir cihazda araştırma başlatmak için bu API'yi kullanın.
keywords: api'ler, grafik api'leri, desteklenen api'ler, araştırma
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
ms.openlocfilehash: efffd6bdb0ab6db5b17a8d6beab09a0d84f5ff6c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012852"
---
# <a name="start-investigation-api"></a>Araştırma API'sini Başlat

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Bir cihazda otomatik araştırma başlatma.

Daha [fazla bilgi için bkz. Otomatik soruşturmalara](automated-investigations.md) genel bakış.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, saatte 50 çağrıdır.

## <a name="requirements-for-air"></a>AIR gereksinimleri

Kuruluşta Uç Nokta için Defender olmalıdır (bkz. Uç Nokta [için Microsoft Defender için en düşük gereksinimler](minimum-requirements.md).

Şu anda, AIR yalnızca aşağıdaki işletim sistemi sürümlerini destekler:

- Windows Server 2019
- Windows Server 2022
- Windows 10, sürüm 1709 ([KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) ile birlikte işletim sistemi derlemesi 16299.1085) veya sonraki sürümler
- Windows 10, sürüm 1803 ([KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464) ile birlikte işletim sistemi derlemesi 17134.704) veya sonraki sürümler
- Windows 10, sürüm [1803 veya](/windows/release-information/status-windows-10-1809-and-windows-server-2019) sonrası
- Windows 11

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alert.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Alert.ReadWrite|'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Etkin düzeltme eylemleri' (Daha fazla bilgi için bkz [.](user-roles.md) Rol oluşturma ve yönetme)
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.security.microsoft.com/api/machines/{id}/startInvestigation
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
Açıklama ekleme|Dize|Eylemle ilişkilendirmek için açıklama. **Gerekli**.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 201 - Yanıt kodu [ve](investigation.md) Araştırma oluşturuldu hata kodunu döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```https
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/startInvestigation
```

```json
{
  "Comment": "Test investigation"
}
```
