---
title: Otomatik araştırma ve düzeltme için otomasyon düzeyleri
description: Otomasyon düzeylerine ve bunların Uç Nokta için Microsoft Defender'da nasıl çalışmalarına genel bir bakış elde olun
keywords: otomatik, araştırma, düzey, Uç Nokta için Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.date: 10/22/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: f4baefadc2fe08b7fe909a135228278c8a696f14
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014078"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Otomatik araştırma ve düzeltme özelliklerinde otomasyon düzeyleri

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender'daki otomatik araştırma ve düzeltme (AIR) özellikleri, çeşitli otomasyon düzeylerinden biri için yaslayabilir. Otomasyon düzeyiniz, AIR soruşturmalarını takip eden düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi alınıp alınmayacaklarını etkiler.

- *Tam otomasyon* (önerilir), kötü amaçlı olduğu belirlenen yapıtlarda düzeltme eylemlerinin otomatik olarak gerçekleştirilmez.
- *Yarı otomasyon,* bazı düzeltme eylemlerinin otomatik olarak gerçekleştirilir, ancak diğer düzeltme eylemleri işlemlerden önce onayı bekler. (Otomasyon düzeyleri tablosunda [tabloya bakın](#levels-of-automation).)
- Bekleyen veya tamamlanan tüm düzeltme eylemleri İşlem Merkezi'nde () izlanır[https://security.microsoft.com](https://security.microsoft.com).

> [!TIP]
> En iyi sonuçları elde etmek için AIR'yi yapılandırken tam [otomasyonu kullanmalarını öneririz](configure-automated-investigations-remediation.md). Geçen yıl boyunca toplanan ve çözüm alınan veriler, tam otomasyon kullanan müşterilerin, düşük otomasyon düzeyleri kullanan müşterilere göre %40 daha yüksek güven düzeyi kötü amaçlı yazılım örnekleri kaldırılmış olduğunu gösterir. Tam otomasyon, güvenlik işlemleri kaynaklarınızı serbest bırakarak stratejik girişimlerinize daha fazla odaklanmanıza yardımcı olabilir.

## <a name="levels-of-automation"></a>Otomasyon düzeyleri

Aşağıdaki tabloda her otomasyon düzeyi ve bunların nasıl çalıştığını açıkmektedir.

<br>

****

|Otomasyon düzeyi|Açıklama|
|---|---|
|**Tam - tehditleri otomatik olarak düzeltme** <br> (tam otomasyon olarak *da adlandırılır*)|Tam otomasyonla, düzeltme eylemleri otomatik olarak gerçekleştirilir. Yapılan tüm düzeltme eylemleri, Geçmiş [sekmesindeki İşlem Merkezi'nde](auto-investigation-action-center.md) **görüntülenir** . Gerekirse, bir düzeltme eylemi geri alın alabilir. <p> *16 *_Ağustos_* 2020 veya sonrasında uç nokta için Microsoft Defender ile oluşturulan ve henüz cihaz grubu tanımlanmamış kiracılar için, tam otomasyon önerilir ve varsayılan olarak seçilir.*|
|**Yarı - herhangi bir düzeltme için onay gerektir** <br> (yarı otomasyon *olarak da adlandırılır*)|Bu yarı otomasyon düzeyiyle, her düzeltme işlemi *için* onay gereklidir. Bu beklemedeki eylemler, İşlem Merkezi'nin [Beklemede sekmesinde](auto-investigation-action-center.md) 2013'te **karşılanmaz ve onaylandıktan sonra da** onaylanır. <p> *Bu yarı otomasyon düzeyi, hiçbir cihaz grubu tanımlanmamış, Uç Nokta için Microsoft Defender ile 16 Ağustos 2020'den önce oluşturulan kiracılar için varsayılan olarak seçilir.*|
|**Yarı - temel klasörlerin düzeltmesi için onay gerektir** <br> (ayrıca bir yarı *otomasyon türü)*|Bu yarı otomasyon düzeyiyle, temel klasörlerdeki dosyalar veya yürütülebilir dosyalar için gereken tüm düzeltme eylemleri için onay gereklidir. Temel klasörler, dizin dosyaları () gibi işletim sistemi **Windows**.`\windows\*` <p> Düzeltme eylemleri, başka (çekirdek olmayan) klasörlerdeki dosyalar veya yürütülebilir dosyalar üzerinde otomatik olarak çalıştırılabilir. <p> Çekirdek klasörlerdeki dosya veya yürütülebilir dosyalar için bekleyen eylemler, İşlem Merkezi'nin Beklemede [](auto-investigation-action-center.md)sekmesinde çalıştırılabilir ve **onaylanır**. <p> Diğer klasörlerdeki dosyalar veya yürütülebilir dosyalar üzerinde alınan eylemler, [İşlem Merkezi'nin Geçmiş](auto-investigation-action-center.md) **sekmesinde çalıştırılabilir.**|
|**Yarı - geçici olmayan klasörlerin düzeltmesi için onay gerekiyor** <br> (ayrıca bir yarı *otomasyon türü)*|Bu düzeyde yarı otomasyonla, geçici klasörlerde olmayan dosyalar veya yürütülebilir dosyalar için gereken tüm düzeltme eylemleri için onay gereklidir. <p> Geçici klasörler aşağıdaki örnekleri içerebilir: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Düzeltme eylemleri, geçici klasörlerdeki dosyalar veya yürütülebilir dosyalar üzerinde otomatik olarak çalıştırılabilir. <p> Geçici klasörlerde yer alan dosyalar veya yürütülebilir dosyalar için bekleyen eylemler İşlem Merkezi'nde [Bekleyen sekmesinde](auto-investigation-action-center.md) çalıştırılabilir ve **onaylanır** . <p> Geçici klasörlerdeki dosyalar veya yürütülebilir dosyalar üzerinde alınan eylemler, İşlem Merkezi'nin [Geçmiş](auto-investigation-action-center.md) sekmesinde çalıştırılabilir ve **onaylanır** .|
|**Otomatik yanıt yok** <br> (Otomasyon yok olarak *da adlandırılır*)|Otomasyon yoksa, otomatik soruşturmalar kuruluşun cihazlarında çalıştırlanmaz. Sonuç olarak, otomatik soruşturma sonucunda hiçbir düzeltme eylemi gerçekleştir alınmaz veya beklemede olmaz. Ancak, virüsten koruma ve yeni nesil koruma özelliklerinin nasıl yapılandırıldıklarından bağlı [olarak, istenmeyen](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) olabilecek uygulamalardan koruma gibi diğer tehdit koruması özellikleri etkili olabilir. <p> ***Otomasyon *yok seçeneğinin* kullanılması önerilmez**, çünkü bu seçenek, kuruluş cihazlarında güvenlik riskini azaltır. [Tam otomasyon (veya en azından yarı otomasyon) için otomasyon düzeyinizi ayarlamayı göz önünde bulundurabilirsiniz](/microsoft-365/security/defender-endpoint/machine-groups).|
|

## <a name="important-points-about-automation-levels"></a>Otomasyon düzeyleri hakkında önemli noktalar

- Tam otomasyonun güvenilir, verimli ve güvenli olduğu kanıtlandı ve tüm müşteriler için önerilir. Tam otomasyon kritik güvenlik kaynaklarınızı serbest bırakarak stratejik girişimlerinize daha fazla odaklanmalarını sağlar.

- Yeni kiracılar (16 Ağustos 2020 veya sonrasında oluşturulan kiracıları içerir) ile Uç Nokta için Microsoft Defender varsayılan olarak tam otomasyona ayarlanır.

- Güvenlik ekibinin tanımlı cihaz grupları otomasyon düzeyine sahipse, bu ayarlar, yeni varsayılan ayarlar tarafından yuvarlanan tarafından değişmez.

- Varsayılan otomasyon ayarlarınızı saklayabilirsiniz veya bunları kuruluş ihtiyaçlarına göre değiştirebilirsiniz. Ayarlarınızı değiştirmek için otomasyon [düzeyinizi ayarlayın](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Microsoft Defender'da otomatik araştırma ve düzeltme özelliklerini yapılandırma](configure-automated-investigations-remediation.md)
- [İşlem Merkezi'ne ziyaret edin](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
