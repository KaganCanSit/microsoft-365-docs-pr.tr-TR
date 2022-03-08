---
title: Cihaz durumu raporu
description: Cihaz durumunu açıklar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: be685d39bbda3b96f689c13a3bc3485c011f1ec8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319887"
---
# <a name="device-status-report"></a>Cihaz durumu raporu

Bu rapor tüm kayıtlı cihazlarınızı durumunu toparak Microsoft Yönetilen Masaüstü hizmetini kullanımınızı gösterir.

Cihazları, son 28 gün içinde yaptıkları etkinliklere ve cihazı güncel tutma yeteneğimize göre kategorilere ayırıyoruz.

En kısa sürede Güncelleştir Windows güncelleştirilecek bir cihaz için:

- İnternet'e bağlı olun.
- Hazırda bekleme moduna geç değil.
- En az altı saat duraklatılmış değil, bunlardan ikisi sürekli olmalı.

Bu gereksinimleri karşılamayan bir cihaz güncelleştirilebilir. Bu cihazlar güncelleştirilme olasılığı en yüksek olana sahip olur.

:::image type="content" source="../../media/mmd-device-status.png" alt-text="Sol üst köşede cihaz etkinliği durumunun grafitini gösteren rapor, sağ üstteki filtreleri ve raporu oluşturmak için bir düğmeyi ve altta ayrıntılar tablosu gösteren rapor":::

## <a name="device-status-labels"></a>Cihaz durum etiketleri

Cihaz durumunu aşağıdaki etiketleri kullanarak bildirebilirsiniz:

| Cihaz durum etiketi | Açıklama |
| ------ | ------ |
| Kullanıcı için hazır | Hizmetimize başarıyla kaydedilmiş ve kullanıcıya verilmeye hazır cihazlar.|
| Etkin | Kullanılan cihazlar. <ul><li>En son güvenlik güncelleştirmesi sürümü için etkinlik ölçütlerine (altı saat, iki sürekli) karşılaştılar.</li> <li>Son beş günde en Microsoft Intune bir kez iade ettik.</li></ul> |
| Eşitlendi | Son 28 gün içinde kullanılan ve Intune ile iade yapılan cihazlar.
| Eşit değil | Son 28 gündür Intune ile birlikte kullanılmaya devam ediyor ancak iade ettirilen cihazlar. |
| Diğer | Etiket, genellikle cihaz kaydı sırasında meydana gelen çeşitli hata durumlarını bir araya döndürür. Daha fazla bilgi için bkz. [Cihaz kaydı sorunlarını giderme](../get-started/manual-registration.md#troubleshooting-device-registration). |
