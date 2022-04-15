---
title: İş için Microsoft Defender'de cihazları yönetme
description: İş için Microsoft Defender'de cihazları yönetmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 453cce2c52902116bc3eaa71f5e6c998ab4164a1
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862840"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de cihazları yönetme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

İş için Microsoft Defender cihazları aşağıdaki gibi yönetebilirsiniz:

- Risk düzeylerini, maruz kalma düzeylerini ve sistem durumunu görmek için [eklenen cihazların listesini görüntüleme](#view-the-list-of-onboarded-devices)
- Tehdit algılamaları olan [bir cihazda işlem gerçekleştirme](#take-action-on-a-device-that-has-threat-detections)
- [İş için Defender'a cihaz ekleme](#onboard-a-device)  
- [İş için Defender'dan cihaz çıkarma](#offboard-a-device)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="view-the-list-of-onboarded-devices"></a>Eklenen cihazların listesini görüntüleme

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Cihaz envanterinin ekran görüntüsü":::

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Cihaz envanteri'ni** seçin.

3. Durumu hakkında daha fazla bilgi edinebileceğiniz ve eylem gerçekleştirebileceğiniz açılır panelini açmak için bir cihaz seçin. 

   Henüz listelenen herhangi bir cihazınız yoksa cihazları [İş için Microsoft Defender](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Tehdit algılamaları olan bir cihazda işlem gerçekleştirme

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Ayrıntıları ve eylemleri içeren seçili bir cihazın ekran görüntüsü":::

1. Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) gezinti bölmesinde **Cihaz envanteri'ni** seçin. 

2. Açılır panelini açmak için bir cihaz seçin ve görüntülenen bilgileri gözden geçirin.

3. Eylemler menüsünü açmak için üç noktayı (**...**) seçin. 

4. **Virüsten koruma taraması çalıştır** veya **Otomatik Araştırma Başlat** gibi bir eylem seçin. 

## <a name="onboard-a-device"></a>Cihaz ekleme

Bkz[. cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Cihazı çıkarma

Bkz. [Cihazı çıkarma](mdb-offboard-devices.md).

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)
- [Cihaz gruplarını oluşturma veya düzenleme](mdb-create-edit-device-groups.md)