---
title: İşlem merkezinde eylemleri görüntüleme ve yönetme
description: Düzeltme eylemlerini görüntülemek ve yönetmek için İşlem merkezini kullanma
keywords: action, center, autoair, automated, investigation, response, düzeltme
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
ms.openlocfilehash: 775781a5df9149ae99f1a051303f5d55c23f1bab
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323241"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>İşlem merkezinde eylemleri görüntüleme ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Yeni E-Microsoft 365 Defender tehdit koruması özellikleri bazı düzeltme eylemlerine neden olabilir. İşte birkaç örnek:

- [Otomatik soruşturmalar,](m365d-autoir.md) otomatik olarak yapılan düzeltme eylemlerine neden olabilir veya sizin onayınızı bekler.
- Virüsten koruma, kötü amaçlı yazılımdan koruma ve diğer tehdit koruması özellikleri dosya, URL veya işlemi engelleme ya da karantinaya alınacak yapı gönderme gibi düzeltme eylemlerine neden olabilir.
- Güvenlik işlemleri ekipleriniz, gelişmiş arama sırasında ya da uyarıları veya olayları araştırırken [](advanced-hunting-overview.md) olduğu gibi düzeltme işlemlerini [el](investigate-alerts.md) [ile gerçekleştirebilir](investigate-incidents.md).

> [!NOTE]
> Düzeltme [eylemlerini onaylamak veya](m365d-action-center.md#required-permissions-for-action-center-tasks) reddetmek için uygun izinlere sahip olmak gerekir. Daha fazla bilgi için, [önkoşullara bakın](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>İşlem merkezinde bekleyen eylemleri gözden geçirme

Otomatik soruşturmaların zamanında devam etmelerini ve tamamlaymalarını mümkün olan en kısa zamanda onaylamanız (veya reddetmeniz) önemlidir. 

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender ve</a> oturum açın. 

2. Gezinti bölmesinde İşlem **merkezi'ni seçin**. 

3. İşlem merkezi'nde, **Bekleyen** sekmesinde, listeden bir öğe seçin. Açılır bölmesi açılır. İşte bir örnek.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Bir eylemi onaylama veya reddetme örneği." lightbox="../../media/air-actioncenter-itemselected.png":::

4. Uçarak çıkış bölmesinde bilgileri gözden geçirin ve sonra aşağıdaki adımlardan birini uygulayın:
   - Araştırma **hakkında daha fazla ayrıntı** görüntülemek için Araştırma sayfasını aç'ı seçin.
   - Bekleyen **bir eylemi** başlatmak için Onayla'ya seçin.
   - Bekleyen **bir eylemin** askıya alınmasını önlemek için Reddet'i seçin.
   - Gelişmiş **ava gitmek** için Avına [git'i seçin](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Tamamlanmış eylemleri geri alma

Bir cihaz veya dosyanın bir tehdit olmadığını belirlediysanız, yapılan düzeltme eylemlerini geri alabilirsiniz (bu eylemlerin otomatik olarak veya el ile gerçekleştirileme). İşlem merkezi'nin Geçmiş **sekmesinde** , aşağıdaki eylemlerden herhangi birini geri alabilirsiniz:  

| Eylem kaynağı | Desteklenen Eylemler |
|:---|:---|
| - Otomatik araştırma <br/>- Microsoft Defender Virüsten Koruma <br/>- El ile yanıt eylemleri | - Cihazı yalıt <br/>- Kod yürütmeyi kısıtla <br/>- Dosyayı karantinaya alın <br/>- Kayıt defteri anahtarını kaldırma <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma |

### <a name="undo-one-remediation-action"></a>Bir düzeltme eylemlerini geri alma

1. İşlem merkezi'ne ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açma.

2. Geçmiş **sekmesinde** , geri almak istediğiniz eylemi seçin.

3. Ekranın sağ tarafındaki bölmede Geri Al'ı **seçin**.

### <a name="undo-multiple-remediation-actions"></a>Birden çok düzeltme eylemlerini geri alma

1. İşlem merkezi'ne gidin ( vehttps://security.microsoft.com/action-center) oturum açma.

2. Geçmiş **sekmesinde** , geri almak istediğiniz eylemleri seçin. Aynı Eylem türüne sahip öğeleri seçmeye emin olun. Açılır bölme açılır.

3. Uçarak çıkış bölmesinde Geri Al'ı **seçin**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Dosyayı birden çok cihaz genelinde karantinadan kaldırmak için 

1. İşlem merkezi'ne ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açma.

2. Geçmiş **sekmesinde** , Dosyayı Karantina eylem türüne **sahip bir** dosyayı seçin.

3. Ekranın sağ tarafındaki bölmede, Bu dosyanın **daha fazla X** örneği için uygula'ya tıklayın ve sonra da Geri Al'ı **seçin**.

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik bir incelemenin ayrıntılarını ve sonuçlarını görüntüleme](m365d-autoir-results.md)
- [Hatalı pozitif veya yanlış negatifleri ele](m365d-autoir-report-false-positives-negatives.md)
