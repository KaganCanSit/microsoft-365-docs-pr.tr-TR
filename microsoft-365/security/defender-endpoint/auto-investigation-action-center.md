---
title: Düzeltme eylemlerini görmek için İşlem merkezini ziyaret edin
description: Otomatik araştırmanın ardından ayrıntıları ve sonuçları görüntülemek için işlem merkezini kullanma
keywords: eylem, merkez, otomatikleştirme, otomatik, araştırma, yanıt, düzeltme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.technology: mde
ms.openlocfilehash: 6a2cc5d4315c5dd64a852c74176272061789b1ba
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535414"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Düzeltme eylemlerini görmek için İşlem merkezini ziyaret edin

Otomatik bir araştırma sırasında ve sonrasında tehdit algılamaları için düzeltme eylemleri tanımlanır. Belirli bir tehdide ve kuruluşunuz için [otomatik araştırma ve düzeltme özelliklerinin nasıl yapılandırıldığına](configure-automated-investigations-remediation.md) bağlı olarak, bazı düzeltme eylemleri otomatik olarak yapılır ve diğerleri onay gerektirir. Kuruluşunuzun güvenlik operasyonları ekibinin bir parçasıysanız İşlem **merkezinde** bekleyen ve tamamlanan [düzeltme eylemlerini](manage-auto-investigation.md#remediation-actions) görüntüleyebilirsiniz.

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/mdb-overview.md)

## <a name="the-unified-action-center"></a>Birleşik İşlem merkezi

Kısa süre önce İşlem merkezi güncelleştirildi. Artık birleşik bir İşlem merkezi deneyimine sahipsiniz. İşlem merkezinize erişmek için adresine gidin [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ve oturum açın.

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Microsoft 365 Defender portalındaki İşlem merkezi sayfası" lightbox="images/mde-action-center-unified.png":::

### <a name="whats-changed"></a>Ne değişti?

Aşağıdaki tablo, yeni, birleşik İşlem merkezini önceki İşlem merkeziyle karşılaştırır.

|Yeni, birleşik İşlem merkezi  |Önceki İşlem merkezi  |
|---------|---------|
|Tek bir konumdaki cihazlar ve e-postalar için bekleyen ve tamamlanan eylemleri listeler <br/>([Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) artı [Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/office-365-atp))|Cihazlar için bekleyen ve tamamlanan eylemleri listeler <br/> (yalnızca [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md))   |
|Şu konumda bulunur:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Şu konumda bulunur:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **İşlem merkezi'ni** seçin. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Microsoft 365 Defender portalında İşlem Merkezi'ne gezinti bölmesi" lightbox="images/action-center-nav-new.png"::: | Microsoft 365 Defender portalında **Otomatik araştırmalarAction** >  **merkezi'ni** seçin. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Microsoft 365 Defender portalında İşlem Merkezi'ne gezinti bölmesinin eski bir sürümü" lightbox="images/action-center-nav-old.png":::  |

Birleşik İşlem merkezi, Uç Nokta için Defender ve Office 365 için Defender genelinde düzeltme eylemlerini bir araya getirir. Tüm düzeltme eylemleri için ortak bir dil tanımlar ve birleşik bir araştırma deneyimi sağlar.

Uygun izinlere ve aşağıdaki aboneliklerden birine veya daha fazlasına sahipseniz birleşik İşlem merkezini kullanabilirsiniz:

- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)
- [Uç Nokta için Defender](microsoft-defender-endpoint.md)
- [Office 365 için Defender](/microsoft-365/security/office-365-security/office-365-atp)
- [İş için Defender](../defender-business/mdb-overview.md)

## <a name="using-the-action-center"></a>İşlem merkezini kullanma

Geliştirilmiş Microsoft 365 Defender portalında birleşik İşlem merkezine ulaşmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın.

2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.

3. **Bekleyen eylemler** ve **Geçmiş** sekmelerini kullanın. Aşağıdaki tabloda, her sekmede görecekleri özetlemektedir:

   |Sekme|Açıklama|
   |---|---|
   |**Bekleyen**|Dikkat gerektiren eylemlerin listesini görüntüler. Eylemleri birer birer onaylayabilir veya reddedebilir ya da aynı eylem türüne sahipse ( **Karantina dosyası** gibi) birden çok eylem seçebilirsiniz. <p> **İpucu**: Otomatik araştırmalarınızın zamanında tamamlayabilmesi için bekleyen eylemleri en kısa sürede [gözden geçirip onayladığınızdan (veya reddettiğinizden)](manage-auto-investigation.md) emin olun.|
   |**Geçmiş**|Aşağıdakiler gibi gerçekleştirilen eylemler için bir denetim günlüğü görevi görür: <ul><li>Otomatik araştırmalar sonucunda gerçekleştirilen düzeltme eylemleri</li><li>Güvenlik operasyonları ekibiniz tarafından onaylanan düzeltme eylemleri</li><li>Canlı Yanıt oturumları sırasında uygulanan çalıştırılan komutlar ve düzeltme eylemleri</li><li>Microsoft Defender Virüsten Koruma tehdit koruması özellikleri tarafından gerçekleştirilen düzeltme eylemleri</li></ul> <p> Belirli eylemleri geri almak için bir yol sağlar (bkz. [Tamamlanan eylemleri geri alma](manage-auto-investigation.md#undo-completed-actions)).|

4. İşlem merkezindeki verileri özelleştirmek, sıralamak, filtrelemek ve dışarı aktarmak için aşağıdaki adımlardan birini veya daha fazlasını uygulayın:

   :::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Sütunlar ve filtreler içeren İşlem merkezi" lightbox="images/new-action-center-columnsfilters.png":::

   - Öğeleri artan veya azalan düzende sıralamak için bir sütun başlığı seçin.
   - Geçen gün, hafta, 30 gün veya 6 aya ait verileri görüntülemek için zaman aralığı filtresini kullanın.
   - Görüntülemek istediğiniz sütunları seçin.
   - Her veri sayfasına eklenecek öğe sayısını belirtin.
   - Yalnızca görmek istediğiniz öğeleri görüntülemek için filtreleri kullanın.
   - Sonuçları bir .csv dosyasına aktarmak için **Dışarı Aktar'ı** seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Düzeltme eylemlerini görüntüleyin ve yönetin](manage-auto-investigation.md)
- [Etkileşimli kılavuza bakın: Uç Nokta için Microsoft Defender ile tehditleri araştırma ve düzeltme](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın](defender-endpoint-false-positives-negatives.md)
- [Küçük ve orta ölçekli işletmeler için Microsoft 365 planlarındaki güvenlik özelliklerini karşılaştırma](../defender-business/compare-mdb-m365-plans.md)
