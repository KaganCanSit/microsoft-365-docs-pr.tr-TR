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
ms.openlocfilehash: 7c300a6d66ae67d481b61a0a35101a0472031266
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327693"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Düzeltme eylemlerini görmek için İşlem merkezini ziyaret edin

Otomatik bir soruşturma sırasında ve sonrasında tehdit algılamaları için düzeltme eylemleri tanımlanır. Belirli tehdit ve Uç Nokta için [Microsoft Defender'ın](/windows/security/threat-protection) sizin için nasıl yapılandırıldıklarına bağlı olarak, bazı düzeltme eylemleri otomatik olarak yapılır ve bazıları için onay gerekir. Kuruluş güvenlik işlemleri ekibinin bir parçasıysanız, İşlem merkezinde bekleyen ve tamamlanmış düzeltme [eylemlerini](manage-auto-investigation.md#remediation-actions) **görüntüabilirsiniz**.


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(Yenİ!) Birleşik İşlem merkezi


Yeni, birleşik bir İşlem merkezini ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) duyurmaktan mutluluk mutluyuz!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Web portalı'Microsoft 365 Defender merkezi.":::

Aşağıdaki tabloda yeni, birleştirilmiş İşlem merkezi önceki İşlem merkeziyle karşılaştırıldı.

|Yeni, birleşik İşlem merkezi  |Önceki İşlem merkezi  |
|---------|---------|
|Cihazlar ve e-posta için bekleyen ve tamamlanmış eylemleri tek bir konumda listeler <br/>([Endpoint için Microsoft Defender ile](microsoft-defender-endpoint.md) Office 365 [için Microsoft Defender](/microsoft-365/security/office-365-security/office-365-atp))|Cihazlar için bekleyen ve tamamlanmış eylemleri listeler <br/> ([Yalnızca uç nokta için Microsoft Defender](microsoft-defender-endpoint.md) )   |
|Şu konumda bulunur:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Şu konumda bulunur:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında İşlem</a> **merkezi'ne seçin**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Microsoft 365 Defender portalında İşlem Merkezi'ne Microsoft 365 Defender."::: | Microsoft 365 Defender portalında Otomatik **soruşturmalarAction** **merkezi'ne** >  seçin. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Portaldan İşlem merkezine Microsoft 365 Defender.":::  |

Birleşik İşlem Merkezi, diğer eylemler için Uç Nokta için Defender ve Defender genelinde düzeltme Office 365. Tüm düzeltme eylemleri için ortak bir dil tanımlar ve birleşik bir araştırma deneyimi sağlar.

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

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="İşlem merkezinde sütunlar ve filtreler.":::

- Öğeleri artan veya azalan düzende sıralamak için bir sütun başlığı seçin.
- Son gün, hafta, 30 gün veya 6 aya yönelik verileri görüntülemek için zaman süresi filtresini kullanın.
- Görüntülemek istediğiniz sütunları seçin.
- Her veri sayfasına kaç öğe ek gerektirmezseniz.
- Yalnızca görmek istediğiniz öğeleri görüntülemek için filtreleri kullanın.
- Sonuçları **bir .csv** dışarı aktar'ı seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Düzeltme eylemlerini görüntüleme ve onaylama](manage-auto-investigation.md)
- [Etkileşimli kılavuza bakın: Uç Nokta için Microsoft Defender'la tehditleri araştırma ve düzeltme](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)
