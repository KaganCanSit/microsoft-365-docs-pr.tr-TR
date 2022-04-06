---
title: Güvenlik panosuna genel bakış
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Tehdit Koruması Durumu'Office 365 gözden geçirmek ve güvenlik uyarılarını görüntülemek ve bu uyarılara yönelik eylemde kullanmak için yeni Güvenlik Panosu'Office 365 kullanın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4bc9d813732c4c67531aeb47a673111d62bbf417
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475751"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'& panosu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Temel işlevler ve Güvenlik panosunun açılması

Güvenlik ve & Merkezi, <https://protection.office.com> kuruluş veri korumasını ve uyumluluğu yönetmeye olanak sağlar. Gerekli izinlere sahip olduğunu varsayarak, Güvenlik Panosu Tehdit Koruması Durumunu incelemenizin yanı sıra güvenlik uyarılarını görüntülemenizi ve bu uyarılar üzerinde işlemnizi de sağlar.

Genel bir bakış için videoyu izleyin ve daha fazla bilgi edinmek için bu makaleyi okuyun.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

Güvenlik Panosu, aşağıda açıklandığı gibi, kuruluş aboneliğinin içeriğine bağlı olarak Tehdit Yönetimi Özeti, Tehdit Koruması Durumu, Genel Haftalık Tehdit Algılamaları, Kötü Amaçlı Yazılım ve daha fazlası gibi çeşitli widget'ları içerir.

Güvenlik ve Uyumluluk Merkezi'nde Güvenlik & görüntülemek için Tehdit yönetimi **Panosu'ne** \> **gidin**. Doğrudan Güvenlik panosuna gitmek için kullanın <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> Güvenlik Panosu'mu görüntülemek için genel yönetici, güvenlik yöneticisi veya güvenlik okuyucusu olmak gerekir. Bazı pencere öğelerini görüntülemek için ek izinler gerekir. Daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'nde& ne](permissions-in-the-security-and-compliance-center.md) bakın.

## <a name="threat-management-summary"></a>Tehdit Yönetimi Özeti

Tehdit Yönetimi Özeti widget'i, son yedi (7) gün boyunca kuruluşlarının tehditlerden nasıl korunarak korunarak korunma durumuyla ilgili bir bakışta size bilgi sağlar.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="Güvenlik Panosu - Tehdit Yönetimi Özeti widget'ı" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

Tehdit Yönetimi Özeti'ne bakarak göreceğiniz bilgiler aboneliğinizin içeriğine bağlıdır. Aşağıdaki tabloda, bu tabloyla ilgili olarak hangi bilgilerin Office 365 E3 Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Kötü amaçlı yazılım iletileri engellendi<br>Kimlik avı iletileri engellendi<br>Kullanıcılar tarafından bildirilen iletiler<br><br><br><br>|Kötü amaçlı yazılım iletileri engellendi<br>Kimlik avı iletileri engellendi<br>Kullanıcılar tarafından bildirilen iletiler<br>Sıfır gün kötü amaçlı yazılım engellendi<br>Algılanan gelişmiş kimlik avı iletileri<br>Engellenen kötü amaçlı URL'ler|

Tehdit Yönetimi Özeti widget'ini görüntülemek veya bu pencereye erişmek için, tehdit raporlarını görüntüleme Office 365 için Defender gerekir. Daha fazla bilgi edinmek için bkz[. Raporları görüntülemek için Office 365 için Defender gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="threat-protection-status"></a>Tehdit Koruması Durumu

Tehdit Koruması Durumu widget'ı, kimlik avının ve kötü amaçlı yazılımların eğilim ve ayrıntılı görünümüyle tehdit korumasının etkili olduğunu gösterir.

:::image type="content" source="../../media/tpswidget.png" alt-text="Tehdit koruması durumu widget'ı" lightbox="../../media/tpswidget.png":::

Ayrıntılar, Microsoft 365 aboneliğinizin Exchange Online Protection [de dahil olup](exchange-online-protection-overview.md) [Office 365 için Microsoft Defender.](defender-for-office-365.md)

|Aboneliğiniz şunları da içerirse...|Bu ayrıntıları göreceğiz|
|---|---|
|EOP'de var, ancak Office 365 için Microsoft Defender|EOP tarafından algılanan ve engellenen kötü amaçlı e-posta.<p> Tehdit [Koruması Durumu raporuna (EOP) bakın](view-email-security-reports.md#threat-protection-status-report).|
|Office 365 için Microsoft Defender|EOP ve EOP tarafından algılanan ve engellenen kötü amaçlı içerik ve kötü amaçlı Office 365 için Defender <p> Kötü amaçlı yazılımdan koruma altyapısı tarafından engellenen benzersiz [e-posta](zero-hour-auto-purge.md) iletilerinin sayısı, sıfır saatlik otomatik temizleme ve Office 365 için Defender özellikleri ([Kasa](safe-links.md) Bağlantıları, [Kasa](safe-attachments.md) Ekleri ve [Office 365 için Defender'te](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) kimlik avı önleme dahil). <p> Tehdit [koruması durum raporuna bakın](view-reports-for-mdo.md#threat-protection-status-report).|

Tehdit Koruması Durumu widget'sını görüntülemek veya bu pencereye erişmek için, tehdit raporlarını görüntüleme Office 365 için Defender gerekir. Daha fazla bilgi edinmek için bkz[. Raporları görüntülemek için Office 365 için Defender gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Genel Haftalık Tehdit Algılamaları

Genel Haftalık Tehdit Algılamaları widget'ı son yedi (7) gün içinde e-posta iletilerinde kaç tehdit algılan olduğunu gösterir.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="Genel Haftalık Tehdit Algılamaları widget'ı" lightbox="../../media/globalweeklythreatdetections.png":::

Ölçümler aşağıdaki tabloda açıklandığı gibi hesaplanır:

|Metrik|Nasıl hesaplanır?|
|---|---|
|Taranan iletiler|Alıcı sayısıyla çarpımlı taranan e-posta iletilerinin sayısı|
|Tehditler durduruldu|Kötü amaçlı yazılım içeren ve alıcı sayısıyla çarpıldı olarak tanımlanan e-posta iletilerinin sayısı|
|Engellenmiş [Office 365 için Defender](defender-for-office-365.md)|İletinin alıcı sayısıyla çarpılarak Office 365 için Defender-posta iletilerinin sayısı|
|Teslimden sonra kaldırıldı|Sıfır saatlik otomatik temizleme [(ZAP)](zero-hour-auto-purge.md) ile alıcı sayısıyla çarpılmış iletilerin sayısı|

## <a name="malware"></a>Kötü amaçlı yazılım

Kötü amaçlı yazılım pencere öğeleri, son yedi (7) gün içinde kötü amaçlı yazılım eğilimleri ve kötü amaçlı yazılım ailesi türleriyle ilgili ayrıntıları gösterir.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="Kötü amaçlı yazılım eğilimleri ve aile türleri" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Analizler

Analizler surface tuşu sorunlarının yanı sıra dikkate almaniz gereken öneriler ve eylemler de bunlardır.

:::image type="content" source="../../media/smartinsights.png" alt-text="Akıllı içgörüler" lightbox="../../media/smartinsights.png":::

Örneğin, bazı kullanıcılar gereksiz posta seçeneklerini devre dışı bırakıldıklarından kimlik avı e-posta iletilerinin teslim ediliyor olduğunu görüyorsunuz. Öngörülerin nasıl çalışması hakkında daha fazla bilgi edinmek için Güvenlik [ve Uyumluluk Merkezi'nde raporlar & bakın](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Tehdit soruşturması ve yanıt

Kuruluş aboneliğiniz Plan [2'Office 365 için Microsoft Defender da dahilse](office-365-ti.md), Güvenlik Pano'kısmında gelişmiş tehdit soruşturması ve yanıt araçlarını içeren bir bölüm vardır. Bu araçlar, [otomatik araştırma ve yanıt özelliklerini içerir](automated-investigation-response-office.md). Güvenliği tehlikeye atılmış kullanıcı hesaplarını hızla ele alama gibi senaryolarda [otomatik araştırma ve yanıt yararlı olabilir](address-compromised-users-quickly.md).

Daha fazla bilgi edinmek için bkz[. Kullanmaya başlayın araştırma ve yanıt (AIR) kullanma hakkında daha fazla Office 365](office-365-air.md).

## <a name="trends"></a>Eğilimler

Güvenlik Panosunun alt kısmında, e-posta **akışı eğilimlerini** özetleyen bir Eğilimler bölümü vardır. Raporlar istenmeyen posta, kötü amaçlı yazılım, kimlik avı girişimleri ve iyi e-posta olarak kategorilere ayrılmış e-postalar hakkında bilgi sağlar. Raporda daha ayrıntılı bilgi görüntülemek için bir kutucuğu tıklatın.

:::image type="content" source="../../media/trends.png" alt-text="Kuruluşun e-posta akışı eğilimlerini özetleyen Eğilimler bölümü" lightbox="../../media/trends.png":::

Ayrıca, kuruluş aboneliğiniz [Office 365 için Defender Plan 2'ye](office-365-ti.md) sahipse, bu bölümde güvenlik ekibimizin yüksek öncelikli güvenlik uyarılarını görüntülemesine ve bu uyarılara yönelik işlemde yer almalarına olanak sağlayan bir Son tehdit yönetimi uyarıları raporunuz da olur.

Gönderilmiş ve Alınan E-posta widget'larını görüntülemek veya widget'lara erişmek için, tüm raporları görüntüleme Office 365 için Defender gerekir. Daha fazla bilgi edinmek için bkz[. Raporları görüntülemek için Office 365 için Defender gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

Son Tehdit Yönetimi Uyarıları widget'larını görüntülemek veya bu pencereye erişmek için, uyarıları görüntüleme izinlerine sahip olmak gerekir. Daha fazla bilgi edinmek için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>İlgili makaleler

[Güvenlik ve Uyumluluk Merkezi'nde e-& raporları görüntüleme](view-email-security-reports.md)

[Raporlar için raporları Office 365 için Microsoft Defender](view-reports-for-mdo.md)

[Office 365 için Defender](defender-for-office-365.md)

[Office 365 soruşturma ve yanıt](office-365-ti.md)
