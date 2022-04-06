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
ms.openlocfilehash: 1f9706a92cf07f23656e6865fe69f11b04d58544
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680530"
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

![Güvenlik Panosu - Tehdit Yönetimi Özeti widget'ı.](../../media/SecDash-ThreatMgmtSummary.png)

Tehdit Yönetimi Özeti'ne bakarak göreceğiniz bilgiler aboneliğinizin içeriğine bağlıdır. Aşağıdaki tabloda, bu tabloyla ilgili olarak hangi bilgilerin Office 365 E3 Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Kötü amaçlı yazılım iletileri engellendi<br>Kimlik avı iletileri engellendi<br>Kullanıcılar tarafından bildirilen iletiler<br><br><br><br>|Kötü amaçlı yazılım iletileri engellendi<br>Kimlik avı iletileri engellendi<br>Kullanıcılar tarafından bildirilen iletiler<br>Sıfır gün kötü amaçlı yazılım engellendi<br>Algılanan gelişmiş kimlik avı iletileri<br>Engellenen kötü amaçlı URL'ler|

Tehdit Yönetimi Özeti widget'ini görüntülemek veya bu widget'a erişmek için, güvenlik raporlarında Defender'ı Office 365 gerekir. Daha fazla bilgi edinmek için bkz. Raporlar [için Defender'ı görüntülemek Office 365 gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Tehdit Koruması Durumu

Tehdit Koruması Durumu widget'ı, kimlik avının ve kötü amaçlı yazılımların eğilim ve ayrıntılı görünümüyle tehdit korumasının etkili olduğunu gösterir.

![Tehdit koruması durumu pencere öğesi.](../../media/tpswidget.png)

Ayrıntılar, Microsoft 365 aboneliğinizin Microsoft Defender Exchange Online Protection(EOP) [](exchange-online-protection-overview.md) ekli veya bu uygulama olmadan da dahil [Office 365](defender-for-office-365.md).

|Aboneliğiniz şunları da içerirse...|Bu ayrıntıları göreceğiz|
|---|---|
|EOP, ancak windows için Microsoft Defender'Office 365|EOP tarafından algılanan ve engellenen kötü amaçlı e-posta.<p> Tehdit [Koruması Durumu raporuna (EOP) bakın](view-email-security-reports.md#threat-protection-status-report).|
|Office 365 için Microsoft Defender|EOP ve Office 365 için Defender tarafından algılanan ve engellenen kötü amaçlı içerik ve kötü amaçlı Office 365 <p> Kötü amaçlı yazılımdan koruma altyapısı tarafından engellenen benzersiz [e-posta](zero-hour-auto-purge.md) iletilerinin sayısı, sıfır saatlik otomatik temizleme ve Office 365 özellikleri için Defender (Kasa Bağlantıları, [Kasa](safe-links.md) Ekleri ve [Office 365 için Defender'da](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) Kimlik avından [](safe-attachments.md)koruma). <p> Tehdit [koruması durum raporuna bakın](view-reports-for-mdo.md#threat-protection-status-report).|

Tehdit Koruması Durumu widget'sini görüntülemek veya bu widget'a erişmek için, güvenlik raporlarında Defender'ı Office 365 gerekir. Daha fazla bilgi edinmek için bkz[. Yeni raporlar için Defender'ı görüntülemek Office 365 gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Genel Haftalık Tehdit Algılamaları

Genel Haftalık Tehdit Algılamaları widget'ı son yedi (7) gün içinde e-posta iletilerinde kaç tehdit algılan olduğunu gösterir.

![Genel Haftalık Tehdit Algılamaları widget'ı.](../../media/globalweeklythreatdetections.png)

Ölçümler aşağıdaki tabloda açıklandığı gibi hesaplanır:

|Metrik|Nasıl hesaplanır?|
|---|---|
|Taranan iletiler|Alıcı sayısıyla çarpımlı taranan e-posta iletilerinin sayısı|
|Tehditler durduruldu|Kötü amaçlı yazılım içeren ve alıcı sayısıyla çarpıldı olarak tanımlanan e-posta iletilerinin sayısı|
|Office 365 [için Defender tarafından Office 365](defender-for-office-365.md)|Office 365 için Defender ile engellenen e-posta iletilerinin alıcı sayısıyla çarpımını|
|Teslimden sonra kaldırıldı|Sıfır saatlik otomatik temizleme [(ZAP)](zero-hour-auto-purge.md) ile alıcı sayısıyla çarpılmış iletilerin sayısı|

## <a name="malware"></a>Kötü amaçlı yazılım

Kötü amaçlı yazılım pencere öğeleri, son yedi (7) gün içinde kötü amaçlı yazılım eğilimleri ve kötü amaçlı yazılım ailesi türleriyle ilgili ayrıntıları gösterir.

![Kötü amaçlı yazılım eğilimleri ve aile türleri.](../../media/malwarewidgetatpe5.png)

## <a name="insights"></a>Analizler

Analizler surface tuşu sorunlarının yanı sıra dikkate almaniz gereken öneriler ve eylemler de bunlardır.

![Akıllı içgörüler.](../../media/smartinsights.png)

Örneğin, bazı kullanıcılar gereksiz posta seçeneklerini devre dışı bırakıldıklarından kimlik avı e-posta iletilerinin teslim ediliyor olduğunu görüyorsunuz. Öngörülerin nasıl çalışması hakkında daha fazla bilgi edinmek için Güvenlik [ve Uyumluluk Merkezi'nde raporlar & bakın](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Tehdit soruşturması ve yanıt

If your subscription includes [Microsoft Defender for Office 365 Plan 2, your Security Dashboard](office-365-ti.md) has a section that includes advanced threat investigation and response tools. Bu araçlar, [otomatik araştırma ve yanıt özelliklerini içerir](automated-investigation-response-office.md). Güvenliği tehlikeye atılmış kullanıcı hesaplarını hızla ele alama gibi senaryolarda [otomatik araştırma ve yanıt yararlı olabilir](address-compromised-users-quickly.md).

Daha fazla bilgi edinmek için, çalışma [sayfalarındaki Otomatik araştırma ve yanıtı (AIR) kullanmaya Office 365](office-365-air.md).

## <a name="trends"></a>Eğilimler

Güvenlik Panosunun alt kısmında, e-posta **akışı eğilimlerini** özetleyen bir Eğilimler bölümü vardır. Raporlar istenmeyen posta, kötü amaçlı yazılım, kimlik avı girişimleri ve iyi e-posta olarak kategorilere ayrılmış e-postalar hakkında bilgi sağlar. Raporda daha ayrıntılı bilgi görüntülemek için bir kutucuğu tıklatın.

![Eğilimler bölümünde, kuruluşun e-posta akışı eğilimleri özetlenmiştir.](../../media/trends.png)

Ayrıca, kuruluşun aboneliği [Office 365 Plan 2 için Defender'ı](office-365-ti.md) da dahil ediyorsa, bu bölümde güvenlik ekibimizin yüksek öncelikli güvenlik  uyarılarını görüntülemesine ve bu uyarılara yönelik işlemde işlem görüntülemesine ve bu uyarılara yönelik işlemde yer almalarına olanak sağlayan bir Son tehdit yönetimi uyarıları raporunuz da olur.

Gönderilmiş ve Alınan E-posta widget'larını görüntülemek veya bu widget'a erişmek için, bir veya daha fazla rapor için Defender'ı Office 365 gerekir. Daha fazla bilgi edinmek için bkz. Raporlar [için Defender'ı görüntülemek Office 365 gereklidir?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

Son Tehdit Yönetimi Uyarıları widget'larını görüntülemek veya bu pencereye erişmek için, uyarıları görüntüleme izinlerine sahip olmak gerekir. Daha fazla bilgi edinmek için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>İlgili makaleler

[Güvenlik ve Uyumluluk Merkezi'nde e-& raporları görüntüleme](view-email-security-reports.md)

[Microsoft Defender for Office 365](view-reports-for-mdo.md)

[Office 365 için Defender](defender-for-office-365.md)

[Office 365 soruşturma ve yanıt](office-365-ti.md)
