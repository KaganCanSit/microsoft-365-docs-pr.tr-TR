---
title: Düzeltme eylemlerini görmek için İşlem merkezini ziyaret edin
description: Otomatik bir soruşturmanın ardından ayrıntıları ve sonuçları görüntülemek için işlem merkezini kullanın
keywords: eylem, orta, otomatik, otomatik, araştırma, yanıt, düzeltme
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
ms.date: 01/28/2021
ms.technology: mde
ms.openlocfilehash: 3cd45506601202a4a1bd5a400eeb51a0e07cecc0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473045"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Düzeltme eylemlerini görmek için İşlem merkezini ziyaret edin

Otomatik bir soruşturma sırasında ve sonrasında tehdit algılamaları için düzeltme eylemleri tanımlanır. Belirli tehdide [ve Uç Nokta için Microsoft Defender](/windows/security/threat-protection) yapılandırmalarına bağlı olarak, bazı düzeltme eylemleri otomatik olarak yapılır ve bazıları için onay gerekir. Kuruluş güvenlik işlemleri ekibinin bir parçasıysanız, İşlem merkezinde bekleyen ve tamamlanmış düzeltme [eylemlerini](manage-auto-investigation.md#remediation-actions) **görüntüabilirsiniz**.


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(Yenİ!) Birleşik İşlem merkezi


Yeni, birleşik bir İşlem merkezini ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) duyurmaktan mutluluk mutluyuz!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Microsoft 365 Defender portalında İşlem merkezi sayfası" lightbox="images/mde-action-center-unified.png":::

Aşağıdaki tabloda yeni, birleştirilmiş İşlem merkezi önceki İşlem merkeziyle karşılaştırıldı.

|Yeni, birleşik İşlem merkezi  |Önceki İşlem merkezi  |
|---------|---------|
|Cihazlar ve e-posta için bekleyen ve tamamlanmış eylemleri tek bir konumda listeler <br/>([Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) artı [Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/office-365-atp))|Cihazlar için bekleyen ve tamamlanmış eylemleri listeler <br/> ([Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md))   |
|Şu konumda bulunur:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Şu konumda bulunur:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında İşlem</a> **merkezi'ne seçin**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Microsoft 365 Defender portalında İşlem Merkezi'ne gezinti bölmesi" lightbox="images/action-center-nav-new.png"::: | Microsoft 365 Defender portalında Otomatik **soruşturmalarAction** **merkezi'ne** >  seçin. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Gezinti bölmesinin daha eski bir sürümü, uygulama portalında bulunan İşlem Microsoft 365 Defender." lightbox="images/action-center-nav-old.png":::  |

Birleşik İşlem Merkezi, Uç Nokta ve Diğer Eylemler için Defender genelinde düzeltme eylemlerini Office 365 için Defender. Tüm düzeltme eylemleri için ortak bir dil tanımlar ve birleşik bir araştırma deneyimi sağlar.

Uygun izinlere ve aşağıdaki aboneliklerden bir veya birden fazlasına sahipsanız, birleşik İşlem Merkezini kullanabilirsiniz:

- [Uç Nokta için Defender](microsoft-defender-endpoint.md)
- [Office 365 için Defender](/microsoft-365/security/office-365-security/office-365-atp)
- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [Gereksinimler](/microsoft-365/security/mtp/prerequisites).

## <a name="using-the-action-center"></a>İşlem merkezini kullanma

Geliştirilmiş iş merkezi portalında birleştirilmiş İşlem merkezine Microsoft 365 Defender için:

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.

İşlem merkezini ziyaret edinca iki sekme görüntülenir: **Bekleyen eylemler ve** **Geçmiş**. Aşağıdaki tabloda her sekmede neler göreceğiniz özetlenmiştir:

|Sekme|Açıklama|
|---|---|
|**Beklemede**|Dikkat gerektiren eylemlerin listesini görüntüler. Eylemleri tek tek onaylar veya reddedebilirsiniz ya da aynı türde bir eyleme (Dosyayı karantina gibi) sahip olan birden çok **eylemi de kullanabilirsiniz**. <p> **İpucu**: Otomatik [soruşturmaların zamanında tamamlanması](manage-auto-investigation.md) için bekleyen eylemleri en kısa zamanda gözden geçirmeyi ve onaylamayı (veya reddetmeyi) emin olun.|
|**Geçmiş**|Yapılan işlemler için denetim günlüğü olarak görev sağlar: <ul><li>Otomatik soruşturmalar sonucunda  alınan düzeltme eylemleri</li><li>Güvenlik işlemleri ekibinin onayını alan düzeltme eylemleri</li><li>Canlı Yanıt oturumları sırasında uygulanan çalıştıran ve düzeltme eylemleri olan komutlar</li><li>Bir yıl içinde tehdit koruması özellikleri tarafından  alınan düzeltme Microsoft Defender Virüsten Koruma</li></ul> <p> Bazı eylemleri geri almak için bir yol sağlar (bkz. [Tamamlanmış eylemleri geri alma](manage-auto-investigation.md#undo-completed-actions)).|

İşlem merkezinde verileri özelleştirilebilir, sıra koruma, filtreleme ve dışarı aktarabilirsiniz.

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Sütunlar ve filtreler içeren İşlem merkezi" lightbox="images/new-action-center-columnsfilters.png":::

- Öğeleri artan veya azalan düzende sıralamak için bir sütun başlığı seçin.
- Son gün, hafta, 30 gün veya 6 aya yönelik verileri görüntülemek için zaman süresi filtresini kullanın.
- Görüntülemek istediğiniz sütunları seçin.
- Her veri sayfasına kaç öğe ek gerektirmezseniz.
- Yalnızca görmek istediğiniz öğeleri görüntülemek için filtreleri kullanın.
- Sonuçları **bir .csv** dışarı aktar'ı seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Düzeltme eylemlerini görüntüleme ve onaylama](manage-auto-investigation.md)
- [Etkileşimli kılavuza bakın: Tehdit tehditlerini araştırma ve düzeltme Uç Nokta için Microsoft Defender](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın](defender-endpoint-false-positives-negatives.md)
