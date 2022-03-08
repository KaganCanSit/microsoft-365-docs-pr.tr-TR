---
title: İş için Microsoft Defender'da düzeltme eylemlerini gözden geçirme
description: İşlem merkezinde otomatik olarak alınan veya onay bekleyen düzeltmeleri görüntüleme
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
ms.openlocfilehash: 5a0fed3ebdb3c7b7275425c24288efab293d6a6d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322961"
---
# <a name="review-remediation-actions-in-the-action-center"></a>İşlem merkezinde düzeltme eylemlerini gözden geçirme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Tehdit algılandığında düzeltme eylemleri ortaya çıktı. Belirli tehdide ve güvenlik ayarlarınızın nasıl yapılandırılana bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca onay üzerine gerçek olabilir. Düzeltme eylemlerine örnek olarak, dosyayı karantinaya gönderme, bir işlemi çalıştırmayı durdurma ve zamanlanmış görevi kaldırma işlemleri örnek olarak verilmiştir. Tüm düzeltme eylemleri İşlem merkezinde iz izdedir.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="İşlem merkezi ekran görüntüsü":::

**Bu makalede şu açıklanmıştır**:

- [İşlem merkezini kullanma](#how-to-use-the-action-center)

- [Düzeltme eylemleri](#remediation-actions)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="how-to-use-the-action-center"></a>İşlem merkezini kullanma

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.

3. Bekleyen eylemleri **görüntülemek** ve onaylamak (veya reddetmek) için Beklemede sekmesini seçin. Bu tür eylemler virüsten koruma/kötü amaçlı yazılımlardan koruma, otomatik soruşturmalar, el ile yanıt etkinlikleri veya canlı yanıt oturumlarından oluşabilir.

4. Tamamlanmış **eylemlerin** listesini görüntülemek için Geçmiş sekmesini seçin. 

## <a name="remediation-actions"></a>Düzeltme eylemleri

İş için Microsoft Defender çeşitli düzeltme eylemleri içerir. Bu eylemler, el ile yanıt eylemlerini, otomatik soruşturmayı takip eden eylemleri ve canlı yanıt eylemlerini içerir.

Aşağıdaki tabloda, kullanılabilir düzeltme eylemleri listele:

| Kaynak  | Eylemler  |
|---------|---------|
| [Otomatik soruşturmalar](../defender-endpoint/automated-investigations.md)      | - Dosyayı karantinaya alın <br/>- Kayıt defteri anahtarını kaldırma <br/>- Süreci kill <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma        |
| [El ile yanıt eylemleri](../defender-endpoint/respond-machine-alerts.md)   | - Virüsten koruma taraması çalıştırma <br/>- Cihazı yalıt <br/>- Durdurma ve karantina <br/>- Dosyayı engellemek veya dosyaya izin vermek için bir gösterge ekleyin       |
| [Canlı yanıt](../defender-endpoint/live-response.md)   | - Bilgi toplama <br/>- Dosyayı çözümleme <br/>- Betik çalıştırma <br/>- Çözümleme için Microsoft'a şüpheli bir varlık gönderin <br/>- Dosyayı düzeltme <br/>- Tehditlere karşı önceden önlem almak         |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md)