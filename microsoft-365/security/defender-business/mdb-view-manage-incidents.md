---
title: İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)
description: Uyarıları yönetmeyi, & yönetmeyi, cihazları yönetmeyi ve düzeltme eylemlerini gözden geçirmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 01/06/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 7b637b729cce02f00aa035571504266452e3bcd4
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027516"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Tehdit algılandığında ve uyarılar tetiklendiğinden, olaylar oluşturulur. Kuruluş güvenlik ekibi portalda olayları 2013'Microsoft 365 Defender yönetebilir.

**Bu makale şunları içerir**:

- [Olaylarınızı ve uyarılarınızı izleme](#monitor-your-incidents--alerts)
- [Önem derecesine dikkat](#alert-severity)
- [Sonraki adımlar](#next-steps)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="monitor-your-incidents--alerts"></a>Olaylarınızı veya & izleme

1. Gezinti Microsoft 365 Defender ()[https://security.microsoft.com](https://security.microsoft.com) içinde **Olaylar'ı seçin**. Oluşturulan tüm olaylar sayfada listelenir.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Olaylar listesinin ekran görüntüsü":::

2. Uyarı hakkında daha fazla bilgi edinmek istediğiniz açılır pencereyi açmak için bir uyarı seçin. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Açılır uygulama açık olarak seçilen olayın ekran görüntüsü":::

3. Açılır bölmede uyarı başlığını görebilir, etkilenen varlıkların listesini (uç noktalar veya kullanıcı hesapları gibi) ekleyebilirsiniz, kullanılabilir eylemler gerçekleştirabilir ve daha fazla bilgi görüntülemek, hatta seçili uyarının ayrıntılar sayfasını açmak için bağlantıları kullanabilirsiniz. 

> [!TIP]
> İş için Microsoft Defender (önizleme), önerilen eylemleri sunarak algılanan tehditlere karşı size yardımcı olacak şekilde tasarlanmıştır. Uyarıyı görüntülediğiniz zaman, gerçekleştirilecek önerilen eylemlerin ne olduğunu bakın. Ayrıca, yalnızca tehdit önem düzeyine göre değil, aynı zamanda kuruluş için risk düzeyine de göre belirlenen uyarı önem derecesine de dikkatin. 

## <a name="alert-severity"></a>Önem derecesine dikkat

Bu Microsoft Defender Virüsten Koruma bir uyarı önem derecesi, algılanan bir tehdidin (kötü amaçlı yazılım) mutlak önem düzeyine ve tek bir uç nokta için olası risklere (virüs bulaşmışsa) dayalı olarak bir uyarı önem düzeyi atar.
İş için Microsoft Defender (önizleme), algılanan davranışın önem düzeyine, bir uç nokta (cihaz) için gerçek riske ve daha önemlisi, kuruluş için olası riske dayalı bir uyarı önem düzeyi atar. Aşağıdaki tabloda birkaç örnek listele: <br/><br/>

| Senaryo | Önem derecesine dikkat | Neden |
|:---|:---|:---|
| Microsoft Defender Virüsten Koruma bir hasar algılamadan önce tehdide son verir. | Bilgilendirme | Herhangi bir hasar yapılmadan önce tehdit durduruldu. |
| Microsoft Defender Virüsten Koruma içinde yürütülen kötü amaçlı yazılımı algılar. Kötü amaçlı yazılım durduruldu ve düzeltildi. | Düşük | Tek bir uç noktada bazı zararlar olsa da, kötü amaçlı yazılım artık organizasyonunız için bir tehdit oluşturmaz. |
| Yürüten kötü amaçlı yazılım Microsoft Defender İş (önizleme) tarafından algılanır. Kötü amaçlı yazılım neredeyse hemen engellenir. | Orta veya Yüksek | Kötü amaçlı yazılım, tek tek uç noktalar ve sizin için tehdit oluşturuyor. |
| Şüpheli davranış algılanır, ancak henüz hiçbir düzeltme eylemi gerçekleştir alınmaz. | Düşük, Orta veya Yüksek | Önem derecesi, davranışın kuruluş için tehdit oluşturduğu dereceye bağlıdır. |

## <a name="next-steps"></a>Sonraki adımlar

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [Microsoft Defender İş'te cihaz ilkelerini görüntüleme veya düzenleme (önizleme)](mdb-view-edit-policies.md)