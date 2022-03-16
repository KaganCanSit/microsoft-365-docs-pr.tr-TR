---
title: İş için Microsoft Defender'da olayları görüntüleme ve yönetme
description: Uyarıları yönetmeyi, & yönetmeyi, cihazları yönetmeyi ve düzeltme eylemlerini gözden geçirmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2e6edf09c781302c61e44a82e9f2d21c5ab2bc15
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63513026"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da olayları görüntüleme ve yönetme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Tehdit algılandığında ve uyarılar tetiklendiğinden, olaylar oluşturulur. Şirketinizin güvenlik ekibi portalında olayları 2013 Microsoft 365 Defender yönetebilir.

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
> İş için Microsoft Defender, önerilen eylemleri önererek algılanan tehditlere karşı size yardımcı olacak şekilde tasarlanmıştır. Uyarıyı görüntülediğiniz zaman, gerçekleştirilecek önerilen eylemlerin ne olduğunu bakın. Ayrıca, yalnızca tehdit önem düzeyine göre değil, aynı zamanda şirketinize yönelik risk düzeyine göre de belirlenen uyarı önem derecesine de dikkatin. 

## <a name="alert-severity"></a>Önem derecesine dikkat

Bu Microsoft Defender Virüsten Koruma bir uyarı önem derecesi, algılanan bir tehdidin (kötü amaçlı yazılım) mutlak önem düzeyine ve tek bir uç nokta için olası risklere (virüs bulaşmışsa) dayalı olarak bir uyarı önem düzeyi atar.
İş için Microsoft Defender, algılanan davranışın önem düzeyine, uç nokta (cihaz) için gerçek riske ve daha önemlisi, şirketinize olası risklere dayalı bir uyarı önem düzeyi atar. Aşağıdaki tabloda birkaç örnek listele: <br/><br/>

| Senaryo | Önem derecesine dikkat | Neden |
|:---|:---|:---|
| Microsoft Defender Virüsten Koruma bir hasar algılamadan önce tehdide son verir. | Bilgilendirme | Herhangi bir hasar yapılmadan önce tehdit durduruldu. |
| Microsoft Defender Virüsten Koruma içinde yürütülen kötü amaçlı yazılım algılayan bir yazılım algılayan bir yazılımdır. Kötü amaçlı yazılım durduruldu ve düzeltildi. | Düşük | Tek bir uç noktada bazı zararlar olsa da, kötü amaçlı yazılım artık şirketiniz için tehdit oluşturmaz. |
| Yürüten kötü amaçlı yazılım, İş için Microsoft Defender tarafından algılanır. Kötü amaçlı yazılım neredeyse hemen engellenir. | Orta veya Yüksek | Kötü amaçlı yazılım, tek tek uç noktalar ve sizin şirketiniz için tehdit oluşturur. |
| Şüpheli davranış algılanır, ancak henüz hiçbir düzeltme eylemi gerçekleştir alınmaz. | Düşük, Orta veya Yüksek | Önem derecesi, davranışın şirketiniz için tehdit oluşturduğu dereceye bağlıdır. |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [Microsoft Defender İş'te cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)