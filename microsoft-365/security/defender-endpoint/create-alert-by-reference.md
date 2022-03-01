---
title: Olay API'si için uyarı oluşturma
description: Uç nokta için Microsoft Defender'da Olay hakkında yeni bir Uyarı oluşturmak için Uyarı API'si oluştur'u nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alert, information, id
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
ms.openlocfilehash: cc28ea9082e7afbb6f623e325a48119de393f075
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996626"
---
# <a name="create-alert-api"></a>Uyarı API'si oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API açıklaması

[Olay'ın](alerts.md) üstünde yeni Uyarı **oluşturur**.

- **Uyarı oluşturma işlemi için Uç** Nokta Olayı için Microsoft Defender gereklidir.
- İstekte Olay'dan üç parametre belirtebilirsiniz: **Olay Zamanı**, **Makine Kimliği** ve **Rapor Kimliği**. Aşağıdaki örneğine bakın.
- Gelişmiş Av API'sinde veya Portalda bulunan bir etkinliği kullanabilirsiniz.
- Aynı Cihazda Başlığı aynı olan bir açık uyarı varsa, yeni oluşturulan uyarı bu uyarıyla birleştirilir.
- API aracılığıyla oluşturulan uyarılarda otomatik olarak bir araştırma başlatılır.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları dakikada 15 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü | İzin | İzin görünen adı
:---|:---|:---
Uygulama | Alert.ReadWrite.All | 'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı) | Alert.ReadWrite | 'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Uyarı soruşturması' (Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md) )
> - Kullanıcının, cihaz grubu ayarlarına göre uyarıyla ilişkilendirilmiş cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz grupları [oluşturma ve yönetme](machine-groups.md)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.
İçerik Türü | Dize | application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki değerleri sağlar (hepsi gereklidir):

Özellik | Tür | Açıklama
:---|:---|:---
eventTime | DateTime(UTC) | Gelişmiş avdan elde edilen dize olarak etkinliğin tam zamanı. Örneğin,  ```2018-08-03T16:45:21.7115183Z``` **Gerekli**.
reportId | Dize | Gelişmiş avdan elde edilen etkinliğin raporki. **Gerekli**.
machineId | Dize | Olayın tanım olduğu cihazın kimliği. **Gerekli**.
önem derecesi | Dize | Uyarının önem derecesi. Özellik değerleri şöyledir: 'Düşük', 'Orta' ve 'Yüksek'. **Gerekli**.
başlık | Dize | Uyarının başlığı. **Gerekli**.
açıklama | Dize | Uyarının açıklaması. **Gerekli**.
recommendedAction| Dize | Güvenlik görevlisinin uyarıyı incelerken bu eylemi at ihtiyacı vardır. **Gerekli**.
kategori| Dize | Uyarının kategorisi. Özellik değerleri şöyledir: "General", "CommandAndControl", "Collection", "CredentialAccess", "DefenseEvasion", "Discovery", "Exfiltration", "Exploit", "Execution", "InitialAccess", "LateralMovement", "Malware", "Persistence", "AyrıcalıkEscalation", "Fidye Yazılımı", "SuspiciousActivity" **Gerekli**.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem 200 Tamam'ı ve yanıt [gövdesine](alerts.md) yeni bir uyarı nesnesini döndürür. Belirtilen özelliklerle ilgili olay (_reportId_, _eventTime_ ve _machineId_) bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

```json
{
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "severity": "Low",
    "title": "example",
    "description": "example alert",
    "recommendedAction": "nothing",
    "eventTime": "2018-08-03T16:45:21.7115183Z",
    "reportId": "20776",
    "category": "Exploit"
}
```
