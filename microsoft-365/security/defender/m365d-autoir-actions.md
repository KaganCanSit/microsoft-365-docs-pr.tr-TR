---
title: İşlem merkezinde eylemleri görüntüleme ve yönetme
description: düzeltme eylemlerini görüntülemek ve yönetmek için İşlem merkezini kullanma
keywords: işlem, merkez, otomatik hava aracı, otomatik, araştırma, yanıt, düzeltme
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 43c48081a86e33cd918bc4de8f01859bc1107583
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666844"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>İşlem merkezinde eylemleri görüntüleme ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender'deki tehdit koruma özellikleri belirli düzeltme eylemlerine neden olabilir. İşte birkaç örnek:

- [Otomatik araştırmalar](m365d-autoir.md) , otomatik olarak gerçekleştirilen veya onayınızı bekleyen düzeltme eylemlerine neden olabilir.
- Virüsten koruma, kötü amaçlı yazılımdan koruma ve diğer tehdit koruması özellikleri bir dosyayı, URL'yi veya işlemi engelleme veya karantinaya bir yapıt gönderme gibi düzeltme eylemlerine neden olabilir.
- Güvenlik operasyonları ekibiniz, [gelişmiş tehdit avcılığı](advanced-hunting-overview.md) sırasında veya uyarıları veya olayları araştırırken olduğu gibi düzeltme [eylemlerini](investigate-alerts.md) el ile gerçekleştirebilir[](investigate-incidents.md).

> [!NOTE]
> Düzeltme eylemlerini onaylamak veya reddetmek için [uygun izinlere](m365d-action-center.md#required-permissions-for-action-center-tasks) sahip olmanız gerekir. Daha fazla bilgi için [önkoşullara](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender) bakın.

## <a name="review-pending-actions-in-the-action-center"></a>İşlem merkezinde bekleyen eylemleri gözden geçirme

Otomatik araştırmalarınızın zamanında devam edebilmesi ve tamamlayabilmesi için bekleyen eylemleri en kısa sürede onaylamanız (veya reddetmeniz) önemlidir. 

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın. 

2. Gezinti bölmesinde **İşlem merkezi'ni** seçin. 

3. İşlem merkezindeki **Beklemede** sekmesinde listeden bir öğe seçin. Açılır pencere bölmesi açılır. İşte bir örnek.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Eylemi onaylama veya reddetme seçenekleri" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Açılır pencere bölmesindeki bilgileri gözden geçirin ve aşağıdaki adımlardan birini uygulayın:
   - Araştırma hakkında daha fazla ayrıntı görüntülemek için **Araştırma sayfasını aç'ı** seçin.
   - Bekleyen bir eylem başlatmak için **Onayla'yı** seçin.
   - Bekleyen bir eylemin gerçekleştirilmesini önlemek için **Reddet'i** seçin.
   - [Gelişmiş avcılığa](advanced-hunting-overview.md) gitmek için **Avlanmaya git'i** seçin. 

## <a name="undo-completed-actions"></a>Tamamlanan eylemleri geri alma

Bir cihazın veya dosyanın bir tehdit olmadığını belirlediyseniz, bu eylemlerin otomatik olarak veya el ile gerçekleştirilip gerçekleştirilmediğine bakılmaksızın, gerçekleştirilen düzeltme eylemlerini geri alabilirsiniz. İşlem merkezindeki **Geçmiş** sekmesinde aşağıdaki eylemlerden herhangi birini geri alabilirsiniz:  

| Eylem kaynağı | Desteklenen Eylemler |
|:---|:---|
| - Otomatik araştırma <br/>- Microsoft Defender Virüsten Koruma <br/>- El ile yanıt eylemleri | - Cihazı yalıtma <br/>- Kod yürütmeyi kısıtlama <br/>- Dosyayı karantinaya al <br/>- Kayıt defteri anahtarını kaldırma <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma |

### <a name="undo-one-remediation-action"></a>Bir düzeltme eylemini geri alma

1. İşlem merkezine ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açın.

2. **Geçmiş** sekmesinde, geri almak istediğiniz eylemi seçin.

3. Ekranın sağ tarafındaki bölmede **Geri Al'ı** seçin.

### <a name="undo-multiple-remediation-actions"></a>Birden çok düzeltme eylemini geri alma

1. İşlem merkezine gidin (https://security.microsoft.com/action-center) ve oturum açın.

2. **Geçmiş** sekmesinde, geri almak istediğiniz eylemleri seçin. Aynı Eylem türüne sahip öğeleri seçtiğinizden emin olun. Açılır pencere bölmesi açılır.

3. Açılır bölmede **Geri Al'ı** seçin.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Bir dosyayı birden çok cihazda karantinadan kaldırmak için 

1. İşlem merkezine ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açın.

2. **Geçmiş** sekmesinde **, Karantina** dosyası Eylem türüne sahip bir dosya seçin.

3. Ekranın sağ tarafındaki bölmede **Bu dosyanın X daha fazla örneğine uygula'yı** ve ardından **Geri Al'ı** seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik araştırmanın ayrıntılarını ve sonuçlarını görüntüleme](m365d-autoir-results.md)
- [Hatalı pozitif sonuçları veya hatalı negatifleri ele alın](m365d-autoir-report-false-positives-negatives.md)
