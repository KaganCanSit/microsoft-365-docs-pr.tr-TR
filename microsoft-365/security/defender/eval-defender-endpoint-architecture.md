---
title: Uç nokta mimarisi gereksinimleri ve önemli kavramlar için Microsoft Defender'ı gözden geçirin
description: Microsoft 365 Defender Uç Nokta için Microsoft Defender'a yönelik teknik diyagram, deneme laboratuvarınızı veya pilot ortamınızı oluşturmadan önce Microsoft 365'de kimliği anlamanıza yardımcı olur.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: b1381e7c2be2224818c72fb8e269ad65ffcacfc8
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755020"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Uç nokta mimarisi gereksinimleri ve önemli kavramlar için Microsoft Defender'ı gözden geçirin

**Geçerli olduğu durum:** Microsoft 365 Defender

Bu makale, Uç nokta ortamı için Microsoft Defender değerlendirmesini ayarlama sürecinde size yol sunar.

Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-endpoint-overview.md).

Uç Nokta için Microsoft Defender'ı etkinleştirmeden önce mimariyi anlıyoruz ve gereksinimleri karşılaya hazır olduğundan emin olun.

## <a name="understand-the-architecture"></a>Mimariyi anlama

Aşağıdaki diyagramda, Uç nokta mimarisi ve tümleştirmeleri için Microsoft Defender'ın gösterildiği yer almaktadır. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="Defender değerlendirme ortamına güvenlik Office Microsoft Defender ekleme adımları" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

Aşağıdaki tabloda çizim açık gösterilmiştir.

Çağrıdan çıkma | Açıklama
:---|:---|
1 | Cihazlar, desteklenen yönetim araçlarından biri aracılığıyla on-boarded olarak kullanılır. 
2 | Üzerine kurulu cihazlar Uç nokta sinyali verileri için Microsoft Defender'ı sağlar ve yanıtlar.
3 | Yönetilen cihazlar başka bir cihaza katılmış ve/veya Azure Active Directory.
4 | Etki alanına katılmış Windows cihazlar, etki alanı Azure Active Directory kullanılarak Azure Active Directory Bağlan.
5 | Uç Nokta uyarıları, soruşturmalar ve yanıtlar için Microsoft Defender en son Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Önemli kavramları anlama

Aşağıdaki tabloda, Uç Nokta için Microsoft Defender'ı değerlendirirken, yapılandırarak ve dağıtırken anlamanız gereken önemli kavramlar tanımlandı: 

Kavram | Açıklama | Daha fazla bilgi
:---|:---|:---|
Yönetim Portalı | Microsoft 365 Defender kalıcı tehdit etkinlikleri veya veri ihlalleri uyarılarını izlemek ve yardımcı olmak için portalda oturum açın. | [Uç nokta portalı için Microsoft Defender'a genel bakış](/microsoft-365/security/defender-endpoint/portal-overview)
Saldırı Yüzeyini Azaltma | Organizasyon un siber tehditlere ve saldırılara açık olduğu yerleri en aza indirerek saldırı yerlerinizi azaltmaya yardımcı olur. | [Saldırı yüzeyini azaltmaya genel bakış](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
Uç Nokta Algılama ve Yanıt | Uç nokta algılama ve yanıt özellikleri, gerçek zamanlı olarak yakın olan ve işlemlebilir gelişmiş saldırı algılamaları sağlar. | [Yeni özelliklere uç noktada algılama ve yanıtlama genel bakış](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
Davranış Engelleme ve Engelleme | Davranışsal engelleme ve engelleme özellikleri, tehdit yürütmeye başlamış olsalar bile, davranışlarına ve işlem ağaçlarına dayalı olarak tehditleri belirlemeye ve durdurmaya yardımcı olabilir. | [Davranışsal engelleme ve kapsama](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
Otomatik Araştırma ve Yanıt | Otomatik araştırma, güvenlik analistleri tarafından kullanılan ve uyarıları inceleyen ve ihlalleri çözmek için hemen harekete geçecek şekilde tasarlanmış süreçlere dayalı çeşitli denetim algoritmalarını kullanır. | [Tehditleri araştırmak ve düzeltmek için otomatik soruşturmaları kullanma](/microsoft-365/security/defender-endpoint/automated-investigations)
Gelişmiş Av | Gelişmiş av, 30 günlük ham verileri incelemenize olanak sağlayan sorgu tabanlı bir tehdit arama aracıdır. Böylece tehdit göstergelerini ve varlıkları bulmak için ağ etkinlikleri önceden inceebilirsiniz. | [Gelişmiş ava genel bakış](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Threat Analytics | Tehdit analizleri, en ilgili tehditleri kapsayan, uzman Microsoft güvenlik araştırmacısı'nın bir dizi raporuyla hazırlar. | [Ortaya çıkan tehditleri izleyin ve yanıtlayın](/microsoft-365/security/defender-endpoint/threat-analytics)


Uç Nokta için Microsoft Defender'da bulunan özellikler hakkında daha ayrıntılı bilgi için bkz [. Uç Nokta için Microsoft Defender nedir](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>SIEM tümleştirmesi

Kuruluş genelindeki güvenlik olaylarını daha kapsamlı olarak çözümlemek ve etkili ve anında yanıt için çalışma kitapları oluşturmak için Uç Nokta için Microsoft Defender'ı Microsoft Sentinel ile tümleştirebilirsiniz. 

Uç Nokta için Microsoft Defender diğer Güvenlik Bilgileri ve Olay Yönetimi (SIEM) çözümleriyle de tümleştirebilirsiniz. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender'da SIEM tümleştirmesini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Sonraki adımlar
[Değerlendirmeyi etkinleştirin](eval-defender-endpoint-enable-eval.md)

Uç Nokta için [Microsoft Defender'ı Değerlendir'e genel bakış](eval-defender-endpoint-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
