---
title: Otomatik araştırma ve düzeltmede otomasyon düzeyleri
description: Otomasyon düzeylerine ve Uç Nokta için Microsoft Defender nasıl çalıştıklarına genel bakış elde edin
keywords: otomatik, araştırma, düzey, Uç Nokta için Microsoft Defender
ms.prod: m365-security
ms.technology: mde
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
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: e36bcdd5851b64ec035eaf8e4e3961c14df5c535
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535834"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Otomatik araştırma ve düzeltme özelliklerindeki otomasyon düzeyleri

**Şunlar için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/mdb-overview.md)

İş için Microsoft Defender otomatik araştırma ve düzeltme (AIR) özellikleri önceden yapılandırılmıştır ve yapılandırılamaz. Uç Nokta için Microsoft Defender'de AIR'i çeşitli otomasyon düzeylerinden birine yapılandırabilirsiniz. Otomasyon düzeyiniz, AIR araştırmalarından sonraki düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi gerçekleştirildiğini etkiler.

- *Tam otomasyon* (önerilen), kötü amaçlı olduğu belirlenen yapıtlarda düzeltme eylemlerinin otomatik olarak gerçekleştirildiği anlamına gelir. (*İş için Defender'da tam otomasyon varsayılan olarak ayarlanır*.)
- *Yarı otomasyon* , bazı düzeltme eylemlerinin otomatik olarak gerçekleştirildiği, ancak diğer düzeltme eylemlerinin gerçekleştirilmeden önce onay beklediği anlamına gelir. (Otomasyon [düzeyleri'ndeki tabloya](#levels-of-automation) bakın.)
- Bekleyen veya tamamlanan tüm düzeltme eylemleri İşlem Merkezi'nde ([https://security.microsoft.com](https://security.microsoft.com) ) izlenir.

> [!TIP]
> En iyi sonuçlar için [, AIR'i yapılandırırken](configure-automated-investigations-remediation.md) tam otomasyon kullanmanızı öneririz. Geçen yıl toplanan ve analiz edilen veriler, tam otomasyon kullanan müşterilerin daha düşük otomasyon düzeylerini kullanan müşterilere kıyasla %40 daha yüksek güvenilirlikli kötü amaçlı yazılım örneklerinin kaldırıldığını gösteriyor. Tam otomasyon, stratejik girişimlerinize daha fazla odaklanmak için güvenlik operasyonları kaynaklarınızın serbestleştirilmesine yardımcı olabilir.

## <a name="levels-of-automation"></a>Otomasyon düzeyleri

|Otomasyon düzeyi|Açıklama|
|---|---|
|**Tam - tehditleri otomatik olarak düzeltme** <br> ( *tam otomasyon* olarak da adlandırılır)|Tam otomasyon ile düzeltme eylemleri otomatik olarak gerçekleştirilir. Gerçekleştirilen tüm düzeltme eylemleri **Geçmiş** sekmesindeki [İşlem Merkezi'nde](auto-investigation-action-center.md) görüntülenebilir. Gerekirse, bir düzeltme eylemi geri alınabilir. <p> **_Tam otomasyon önerilir_* ve 16 Ağustos 2020 tarihinde veya sonrasında oluşturulan uç nokta için Defender'a sahip kiracılar için varsayılan olarak seçilidir ve henüz cihaz grubu tanımlanmamıştır.*<p>*İş için Defender'da tam otomasyon varsayılan olarak ayarlanır.*|
|**Yarı - herhangi bir düzeltme için onay gerektir** <br> ( *yarı otomasyon* olarak da adlandırılır)|Bu yarı otomasyon düzeyiyle, *herhangi bir* düzeltme eylemi için onay gerekir. Bu tür bekleyen eylemler [İşlem Merkezi'nde](auto-investigation-action-center.md)**, Beklemede** sekmesinde görüntülenebilir ve onaylanabilir. <p> *Bu yarı otomasyon düzeyi, 16 Ağustos 2020'den önce Uç Nokta için Microsoft Defender ile oluşturulan ve hiçbir cihaz grubu tanımlanmamış kiracılar için varsayılan olarak seçilir.*|
|**Yarı - çekirdek klasörlerin düzeltilmesi için onay gerektir** <br> (aynı zamanda bir *tür yarı otomasyon*)|Bu yarı otomasyon düzeyiyle, çekirdek klasörlerdeki dosyalarda veya yürütülebilir dosyalarda gereken düzeltme eylemleri için onay gerekir. Çekirdek klasörler, **Windows** (`\windows\*` gibi) işletim sistemi dizinlerini içerir. <p> Düzeltme eylemleri, diğer (çekirdek olmayan) klasörlerdeki dosyalarda veya yürütülebilir dosyalarda otomatik olarak yapılabilir. <p> Çekirdek klasörlerdeki dosyalar veya yürütülebilir dosyalar için bekleyen eylemler [İşlem Merkezi'nde](auto-investigation-action-center.md) **Beklemede** sekmesinde görüntülenebilir ve onaylanabilir. <p> Diğer klasörlerdeki dosyalarda veya yürütülebilir dosyalarda gerçekleştirilen eylemler [İşlem Merkezi'nde](auto-investigation-action-center.md)**, Geçmiş** sekmesinde görüntülenebilir.|
|**Yarı - geçici olmayan klasörlerin düzeltilmesi için onay gerektir** <br> (aynı zamanda bir *tür yarı otomasyon*)|Bu yarı otomasyon düzeyiyle, geçici klasörlerde *olmayan* dosyalarda veya yürütülebilir dosyalarda gerekli olan düzeltme eylemleri için onay gerekir. <p> Geçici klasörler aşağıdaki örnekleri içerebilir: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Düzeltme eylemleri, geçici klasörlerdeki dosyalarda veya yürütülebilir dosyalarda otomatik olarak yapılabilir. <p> Geçici klasörlerde bulunmayan dosyalar veya yürütülebilir dosyalar için bekleyen eylemler [İşlem Merkezi'nde](auto-investigation-action-center.md)**, Beklemede** sekmesinde görüntülenebilir ve onaylanabilir. <p> Geçici klasörlerdeki dosyalar veya yürütülebilir dosyalar üzerinde gerçekleştirilen eylemler [İşlem Merkezi'nde](auto-investigation-action-center.md) **Geçmiş** sekmesinde görüntülenebilir ve onaylanabilir.|
|**Otomatik yanıt yok** <br> ( *otomasyon yok* olarak da adlandırılır)|Otomasyon olmadan, otomatik araştırma kuruluşunuzun cihazlarında çalışmaz. Sonuç olarak, otomatik araştırma sonucunda hiçbir düzeltme eylemi gerçekleştirilmedi veya beklemede değil. Ancak, virüsten koruma ve yeni nesil koruma özelliklerinizin nasıl yapılandırıldığına bağlı olarak, [istenmeyebilecek uygulamalardan koruma](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) gibi diğer tehdit koruma özellikleri etkin olabilir. <p> *Kuruluşunuzun cihazlarının güvenlik duruşunu azalttığı için ***otomasyon* yok seçeneğinin kullanılması önerilmez**. [Otomasyon düzeyinizi tam otomasyona (veya en azından yarı otomasyona) ayarlamayı göz önünde bulundurun](/microsoft-365/security/defender-endpoint/machine-groups).|

## <a name="important-points-about-automation-levels"></a>Otomasyon düzeyleri hakkında önemli noktalar

- Tam otomasyonun güvenilir, verimli ve güvenli olduğu kanıtlanmıştır ve tüm müşteriler için önerilir. Tam otomasyon, stratejik girişimlerinize daha fazla odaklanabilmeleri için kritik güvenlik kaynaklarınızı serbesttir.

- Uç Nokta için Defender ile yeni kiracılar (16 Ağustos 2020 veya sonrasında oluşturulan kiracıları içerir) varsayılan olarak tam otomasyona ayarlanır.

- [İş için Defender](../defender-business/compare-mdb-m365-plans.md) varsayılan olarak tam otomasyonu kullanır. İş için Defender, cihaz gruplarını İş için Defender ile aynı şekilde kullanmaz. Bu nedenle, tam otomasyon açık ve İş için Defender'daki tüm cihazlara uygulanır.

- Güvenlik ekibiniz bir otomasyon düzeyine sahip cihaz grupları tanımladıysa, bu ayarlar dağıtılan yeni varsayılan ayarlar tarafından değiştirilmez.

- Varsayılan otomasyon ayarlarınızı koruyabilir veya kuruluş gereksinimlerinize göre değiştirebilirsiniz. Ayarlarınızı değiştirmek için [otomasyon düzeyinizi ayarlayın](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Defender'da otomatik araştırma ve düzeltme özelliklerini yapılandırma](configure-automated-investigations-remediation.md)
- [İşlem Merkezi'ni ziyaret edin](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
