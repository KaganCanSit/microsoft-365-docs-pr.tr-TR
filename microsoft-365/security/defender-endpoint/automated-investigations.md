---
title: Tehditleri araştırmak ve düzeltmek için otomatik soruşturmaları kullanma
description: Uç Nokta için Microsoft Defender'da otomatik araştırma akışını anlama.
keywords: otomatik, araştırma, algılama, Uç Nokta için Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 11/24/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: 31b2a7b41c26bdba22e6f364e517471e31e9115c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313027"
---
# <a name="overview-of-automated-investigations"></a>Otomatik soruşturmalara genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Nasıl çalıştığını görmek mi istiyor musunuz? Aşağıdaki videoyu izleyin:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Otomatik soruşturmada kullanılan teknoloji çeşitli denetim algoritmalarını kullanır ve güvenlik analistleri tarafından kullanılan süreçleri temel kullanır. AIR özellikleri uyarıları inceleyen ve ihlalleri çözmek için hemen harekete geçecek şekilde tasarlanmıştır. AIR özellikleri uyarı hacmini önemli ölçüde azaltır ve güvenlik işlemlerinin daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak verir. Bekleyen veya tamamlanan tüm düzeltme eylemleri İşlem merkezinde [izlanır](auto-investigation-action-center.md). İşlem merkezinde bekleyen eylemler onaylanır (veya reddedilir) ve gerekirse tamamlanmış eylemler geri alınabilirsiniz.

Bu makalede AIR'ye genel bir bakış ve sonraki adımlarla ek kaynakların bağlantıları yer sağlar.

> [!TIP]
> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Otomatik soruşturma nasıl başlatılır

Bir uyarı tetiklendiğinde veya güvenlik işleci araştırmayı başlattığında otomatik bir araştırma başlayabilir.

<br>

****

|Durum|Ne olur?|
|---|---|
|Uyarı tetiklenir|Genelde, bir uyarı tetiklendiğinde ve [bir olay](review-alerts.md) oluşturulduğunda otomatik [bir araştırma](view-incidents-queue.md) başlatılır. Örneğin, kötü amaçlı bir dosyanın bir cihazda yer alan bir dosya olduğunu varsayalım. Bu dosya algılandığında bir uyarı tetiklenir ve olay oluşturulur. Cihazda otomatik bir soruşturma işlemi başlar. Diğer cihazlarda aynı dosya nedeniyle diğer uyarılar da oluşturulsa, bunlar ilişkili olaya ve otomatik soruşturmaya eklenir.|
|El ile araştırma başlatıldı|Güvenlik işlemleri takımınız tarafından otomatik bir araştırma el ile başlatılabilir. Örneğin, bir güvenlik operatörünün cihaz listesini gözden geçirerek cihazın yüksek risk düzeyine sahip olduğunu fark olduğunu varsayalım. Güvenlik işleci listeden cihazı seçerek açılır öğesini açabilir ve ardından Otomatik Araştırmayı **Başlat'ı seçebilirsiniz**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Otomatik araştırmanın kapsamını genişletme

Araştırma devam ederken, cihazdan oluşturulan diğer tüm uyarılar, bu araştırma tamamlanana kadar devam eden otomatik bir soruşturmaya eklenir. Buna ek olarak, diğer cihazlarda da aynı tehdit görülürse, bu cihazlar araştırmaya eklenir.

Başka bir cihazdacrim bir varlık görülürse, otomatik araştırma işlemi kapsamı bu cihazı içerecek şekilde genişletmiş olur ve bu cihazda genel bir güvenlik çalışma kitabı başlatılır. Bu genişletme işlemi sırasında aynı varlığa bağlı 10 veya daha fazla cihaz bulunursa, bu genişletme eylemi bir onay gerektirir ve Bekleyen eylemler **sekmesinde** görünür.

## <a name="how-threats-are-remediated"></a>Tehditlerin düzeltmesi

Uyarılar tetiklendiğinde ve otomatik bir soruşturma çalıştırıldığı için araştırılan her kanıt parçası için bir karar oluşturulur. Kararların karşılanması şunları sağlar:

- *Kötü Amaçlı*;
- *Şüpheli*; veya
- *Tehdit bulunamadı*.

Kararlara ulaşıldığı için otomatik soruşturmalar bir veya birden çok düzeltme eylemine neden olabilir. Düzeltme eylemlerine örnek olarak, dosyayı karantinaya gönderme, hizmeti durdurma, zamanlanmış görevi kaldırma ve daha fazlası dahildir. Daha fazla bilgi edinmek için [bkz. Düzeltme eylemleri](manage-auto-investigation.md#remediation-actions).

Düzeltme eylemleri, [hem](automation-levels.md) sizin için hem de diğer güvenlik ayarlarının yanı sıra, sizin için otomasyon kümesi düzeyine bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca güvenlik işlemleri ekibinin onayı üzerine gerçekleştirebilirsiniz. Otomatik düzeltmeyi etkileyebilecek ek güvenlik ayarları arasında istenmeyen [olabilecek uygulamalara (](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) PUA) karşı koruma da vardır.

Bekleyen veya tamamlanan tüm düzeltme eylemleri İşlem merkezinde [izlanır](auto-investigation-action-center.md). Gerekirse, güvenlik işlemleri ekipleriniz bir düzeltme eylemini geri alabilir. Daha fazla bilgi edinmek için [bkz. Otomatik bir soruşturmadan sonra düzeltme eylemlerini gözden geçirme ve onaylama](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Microsoft 365 Defender portalında yeni, birleşik soruşturma Microsoft 365 Defender göz atın. Daha fazla bilgi edinmek için bkz [. (Yenİ!) Birleşik araştırma sayfası](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>AIR gereksinimleri

Kuruluşta Uç Nokta için Defender olmalıdır (Bkz. Uç Nokta [için Microsoft Defender için en düşük gereksinimler](minimum-requirements.md)).

> [!NOTE]
> Otomatik araştırma ve yanıt, pasif Microsoft Defender Virüsten Koruma etkin modda çalıştırıldığı için otomatik araştırma ve yanıt gerektirir. Otomatik Microsoft Defender Virüsten Koruma devre dışı bırakılır veya kaldırılırsa, Otomatik Araştırma ve Yanıt düzgün çalışmaz.

Şu anda, AIR yalnızca aşağıdaki işletim sistemi sürümlerini destekler:

- Windows Server 2012 R2 (Önizleme)
- Windows Server 2016 (Önizleme)
- Windows Server 2019
- Windows Server 2022
- Windows 10, sürüm 1709 ([KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) ile birlikte işletim sistemi derlemesi 16299.1085) veya sonraki sürümler
- Windows 10, sürüm 1803 ([KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464) ile birlikte işletim sistemi derlemesi 17134.704) veya sonraki sürümler
- Windows 10, sürüm [1803 veya](/windows/release-information/status-windows-10-1809-and-windows-server-2019) sonrası
- Windows 11

## <a name="next-steps"></a>Sonraki adımlar

- [Otomasyon düzeyleri hakkında daha fazla bilgi](automation-levels.md)
- [Etkileşimli kılavuza bakın: Uç Nokta için Microsoft Defender'la tehditleri araştırma ve düzeltme](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Uç Nokta için Microsoft Defender'da otomatik araştırma ve düzeltme özelliklerini yapılandırma](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [PUA koruması](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Office 365 için Microsoft Defender'da otomatik araştırma ve Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Otomatik araştırma ve yanıt Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
