---
title: İş için Microsoft Defender'da (önizleme) düzeltme eylemlerini gözden geçirme
description: İşlem merkezinde otomatik olarak alınan veya onay bekleyen düzeltmeleri görüntüleme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f1128b5fd9c27845bebbd4b6a0b45f93c5f3e0c6
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016702"
---
# <a name="review-remediation-actions-in-the-action-center"></a>İşlem merkezinde düzeltme eylemlerini gözden geçirme

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
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

İş için Microsoft Defender (önizleme) çeşitli düzeltme eylemleri içerir. Bu eylemler, el ile yanıt eylemlerini, otomatik soruşturmayı takip eden eylemleri ve canlı yanıt eylemlerini içerir.

Aşağıdaki tabloda, kullanılabilir düzeltme eylemleri listele:

| Kaynak  | Eylemler  |
|---------|---------|
| [Otomatik soruşturmalar](../defender-endpoint/automated-investigations.md)      | - Dosyayı karantinaya alın <br/>- Kayıt defteri anahtarını kaldırma <br/>- Süreci kill <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma        |
| [El ile yanıt eylemleri](../defender-endpoint/respond-machine-alerts.md)   | - Virüsten koruma taraması çalıştırma <br/>- Cihazı yalıt <br/>- Durdurma ve karantina <br/>- Dosyayı engellemek veya dosyaya izin vermek için bir gösterge ekleyin       |
| [Canlı yanıt](../defender-endpoint/live-response.md)   | - Bilgi toplama <br/>- Dosyayı çözümleme <br/>- Betik çalıştırma <br/>- Çözümleme için Microsoft'a şüpheli bir varlık gönderin <br/>- Dosyayı düzeltme <br/>- Tehditlere karşı önceden önlem almak         |

## <a name="next-steps"></a>Sonraki adımlar

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İş için Microsoft Defender'da cihazları yönetme (önizleme)](mdb-manage-devices.md)