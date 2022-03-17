---
title: İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak
description: Tehdit algılandığında, bu tehditlere yanıt vermek ve onları azaltmak için eylem gerçekleştirabilirsiniz.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f57774f993c0044878655713202d6835a2a69173
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525297"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Bu Microsoft 365 Defender portalı, güvenlik ekibimizin algılanan tehditlere yanıt vermelerini ve bu tehditleri azaltmak için olanak sağlar. Bu makalede, İş için Defender'ı nasıl kullanabileceğiniz örnek olarak açıklanmıştır.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="view-detected-threats"></a>Algılanan tehditleri görüntüleme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Giriş sayfasındaki bildirim kartları. Kartlar, size kaç tehdit algılandığından ve kaç kullanıcı hesabının, uç noktaların (cihazların) ve diğer varlıkların etkilendiğini bir bakışta gösterir. Aşağıdaki resim, gördüğünüz kartlara bir örnektir:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Microsoft 365 Defender portalında kartların ekran görüntüsü":::

3. Daha fazla bilgi görüntülemek ve işlem yapmak için karttan bir düğme veya bağlantı seçin. Örnek olarak, Risk **kartında yer** alan Cihazlar düğmesi, Ayrıntıları **görüntüle düğmesi** içerir. Bu düğmeyi seçmek, aşağıdaki **resimde gösterildiği gibi** bizi Cihaz envanteri sayfasına alır:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Cihaz stoku ekran görüntüsü":::

   Cihaz **envanteri sayfasında** , şirket cihazlarının yanı sıra risk düzeyi ve pozlama düzeyi de listeleyebilirsiniz.

4. Cihaz gibi bir öğeyi seçin. Açılır bölme açılır ve aşağıdaki resimde gösterildiği gibi, bu öğe için oluşturulan uyarılar ve olaylar hakkında daha fazla bilgi görüntüler:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Seçili bir cihaz için uçarak çıkış bölmesinin ekran görüntüsü":::

5. Uçarak çıkışta, görüntülenen bilgileri görüntüleme. Aşağıdaki resimde gösterildiği gibi kullanılabilir eylemleri listeleyen bir menü açmak için üç noktayı (...) seçin: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Seçili cihaz için kullanılabilir eylemlerin ekran görüntüsü":::

6. Kullanılabilir bir eylemi seçin. Örneğin, Virüsten koruma taraması **çalıştır'ı seçebilirsiniz** ve Microsoft Defender Virüsten Koruma hızlı tarama başlatmak için bu işlemi başlatabilirsiniz. Öte ya da cihazda otomatik **bir soruşturmayı tetiklemek** için Otomatik Araştırma Başlat'ı da seçebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)