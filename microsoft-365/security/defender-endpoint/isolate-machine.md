---
title: Makine API'sini yalıt
description: Uç Nokta için Microsoft Defender'da bir cihazın dış ağa erişimini ayırmak için Makine API'sini yalıtmak hakkında bilgi edinin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, cihazı yalıtmak
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
ms.openlocfilehash: 52063135280d9e91ca531546b4ae03cf5b42ccbf
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996505"
---
# <a name="isolate-machine-api"></a>Makine API'sini yalıt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Bir cihazı dış ağa erişimini yalıtır.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Tam yalıtım, 11. Windows 10 sürüm 1703 ve Windows cihazlar için kullanılabilir.
> - Seçmeli yalıtım; 11. Windows 10, sürüm 1709 veya sonraki sürümlerde ve Windows kullanılabilir.
> - Bir cihazı yorumlarken yalnızca belirli işlemlere ve hedeflere izin verilir. Bu nedenle, tam VPN hedeflerinin arkasındaki cihazlar cihaz yalıtılmış halde uç nokta için Microsoft Defender bulut hizmetine ulaşamayabilecektir. Uç Nokta için Microsoft Defender ve bulut tabanlı korumayla ilgili Microsoft Defender Virüsten Koruma bir VPN kullanılması önerilir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Makine.Yalıt|'Makine yalıt'
Temsilcili (iş veya okul hesabı)|Makine.Yalıt|'Makine yalıt'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Etkin düzeltme eylemleri' (Daha fazla bilgi için bkz [.](user-roles.md) Rol oluşturma ve yönetme)
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
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
IsolationType|Dize|Yalıtma türü. İzin verilen değerler: 'Dolu' veya 'Seçmeli'.

**IsolationType** , gerçekleştirmek için yalıtım türünü kontrol eder ve aşağıdakilerden biri olabilir:

- Tam: Tam yalıtım
- Seçmeli: Yalnızca sınırlı uygulama kümelerinin ağa erişimini kısıtlama (daha ayrıntılı bilgi [için bkz. Cihazları ağdan](respond-machine-alerts.md#isolate-devices-from-the-network) ayırma)

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 201 - Yanıt kodu [ve Makine](machineaction.md) Eylemi oluşturuldu hata kodunu döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- Cihazı yalıtma tarafından serbest bırakmak için bkz. [Cihazı yalıtımtan ayırmayı bırakma](unisolate-machine.md).
