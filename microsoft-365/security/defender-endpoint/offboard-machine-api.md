---
title: Offboard makine API'si
description: Uç nokta için Microsoft Defender'dan bir cihazın çıkarı için API kullanmayı öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, soruşturma paketi toplama
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
ms.openlocfilehash: 1279f7271abbd4086c946492e95daa52962dbae5
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014324"
---
# <a name="offboard-machine-api"></a>Offboard makine API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Uç Nokta için Defender'dan offboard cihazı.

## <a name="limitations"></a>Sınırlamalar

- Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Bu API, Windows 11, Windows 10, sürüm 1703 ve sonraki sürümler ya da Windows Server 2019 ve sonraki sürümler için de desteklenen bir API'tir.
>
> Bu API, MacOS veya Linux cihazlarda desteklenmiyor.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. [Uç Nokta API'leri için Defender Kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Makine.Offboard|'Offboard makinesi'
Temsilcili (iş veya okul hesabı)|Makine.Offboard|'Offboard makinesi'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının 'Genel Yönetici' AD rolüne ihtiyacı var
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

Makine kimliği, cihazı seçinca URL'de bulunabilir. Genel olarak, URL'de bulunanın 40 basamaklı alfasayısal sayıdır.

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
---|---|---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
---|---|---
Açıklama ekleme|Dize|Eylemle ilişkilendirmek için açıklama. **Gerekli**.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 201 - Yanıt kodu [ve Makine](machineaction.md) Eylemi oluşturuldu hata kodunu döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
