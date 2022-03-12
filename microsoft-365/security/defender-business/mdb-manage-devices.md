---
title: İş için Microsoft Defender'da cihazları yönetme
description: İş için Microsoft Defender'da cihazları yönetmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f229574461e4aa11efc8595270c0a92dcb91add2
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449197"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da cihazları yönetme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender'da cihazları aşağıdaki gibi yönetebilirsiniz:

- [Risk düzeyini, pozlama düzeyini ve](#view-the-list-of-onboarded-devices) sağlık durumunu görmek için, yerleşik cihazların listesini görüntüleme

- [Tehdit algılamaları olan](#take-action-on-a-device-that-has-threat-detections) bir cihazda eyleme geç

- [İş için Defender'a bir cihaz ekleme](#onboard-a-device)  

- [İş için Defender'dan bir cihaz çıkartan](#offboard-a-device)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="view-the-list-of-onboarded-devices"></a>Eklenen cihazların listesini görüntüleme

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Cihaz stoku ekran görüntüsü":::

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde Cihaz **envanteri'ni seçin**.

3. Bir cihazı seçerek çıkış panelini açın. Bu panelden, cihazın durumu hakkında daha fazla bilgi edinebilirsiniz ve harekete geçebilirsiniz. 

   Henüz hiç cihaz listelenmiyorsa cihazları İş için [Microsoft Defender'a ekleme](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Tehdit algılamaları olan bir cihazda eyleme geç

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Ayrıntıları ve eylemlerin mevcut olduğu seçili cihazın ekran görüntüsü":::

1. Mobil Microsoft 365 Defender () gezinti [https://security.microsoft.com](https://security.microsoft.com) bölmesinde Cihaz **envanteri'ni seçin**. 

2. Açılır panelini açmak için bir cihaz seçin ve görüntülenen bilgileri gözden geçirin.

3. Eylemler menüsünü açmak için üç **noktayı (...**) seçin. 

4. Virüsten koruma taraması çalıştırma **veya Otomatik Araştırmayı** **Başlatma gibi bir eylem seçin**. 

## <a name="onboard-a-device"></a>Bir cihaz ekleme

Bkz [. Cihazları İş için Microsoft Defender'a ekleme](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Cihaz çıkartan

Bkz [. Cihaz çıkarma](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [Cihaz grupları oluşturma veya düzenleme](mdb-create-edit-device-groups.md)