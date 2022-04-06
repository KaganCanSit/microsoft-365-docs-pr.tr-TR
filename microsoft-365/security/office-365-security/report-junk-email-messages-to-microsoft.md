---
title: İstenmeyen, istenmeyen posta olmayan ve kimlik avı iletilerini Microsoft'a bildirme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Yöneticiler iyi ve kötü iletileri ve dosyaları çözümlemek için Microsoft'a bildirmenin farklı yollarını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7818b15d97d8d7ee33005927ff899e9f5ff5a06
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682735"
---
# <a name="report-messages-and-files-to-microsoft"></a>İletileri ve dosyaları Microsoft'a bildirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu Exchange Online kuruluşlarda, hem kullanıcılar hem de yöneticiler e-posta iletilerini ve dosyalarını Microsoft'a raporlamak için birkaç farklı yöntemi vardır.

|Yöntem|Açıklama|
|---|---|
|[Gönderimler portalını kullanarak şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyaları Microsoft'a gönderme](admin-submission.md)|Posta kutusu olmayan kuruluşlarda yöneticiler için önerilen raporlama Exchange Online (tek başına EOP'de kullanılamaz).|
|[Rapor İletisi'yi veya Rapor Kimlik Avı eklentilerini etkinleştirme](enable-the-report-message-add-in.md)|Standart ve Outlook Web üzerinde Outlook (eski adıyla Outlook Web App). <p> Aboneliğinize bağlı olarak, kullanıcılar tarafından eklentilerle birlikte bildirilen iletiler Yönetici Gönderimleri [portalı](admin-submission.md), Otomatik araştırma ve yanıt [(AIR)](air-view-investigation-results.md) sonuçları, Kullanıcı tarafından bildirilen iletiler raporu ve [Gezgin'de kullanılabilir](threat-explorer-views.md#email--submissions).[](view-email-security-reports.md#user-reported-messages-report) <p> Bildirilen iletileri, belirttiğiniz bir posta kutusuna kopyalanan veya yeniden yönlendiriliyor olacak şekilde yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Kullanıcı gönderimleri ilkeleri](user-submission.md).
|[Negatif sonuçlarda hatalı pozitif ve yanlış negatif Outlook](report-false-positives-and-false-negatives.md)|Rapor İletisi özelliğini kullanarak hatalı pozitif (engellenen veya gereksiz e-postaya gönderilmiş olan iyi bir e-posta) ve hatalı negatifleri (gelen kutunuza teslim edilen istenmeyen e-posta veya kimlik avı) Exchange Online Protection (EOP) gönderin.|
|[Kullanıcıların Microsoft'a ne bildirimini görmek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Kullanıcılar iletileri çözümleme için Microsoft'a bildirecek bir posta akışı kuralı (aktarım kuralı olarak da bilinir) oluşturma hakkında bilgi alabilirsiniz.|
|[Çözümleme için Microsoft'a kötü amaçlı yazılım ve kötü amaçlı yazılım olmayan yazılımlar gönderme](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Ekleri Microsoft Güvenlik Zekası diğer dosyaları göndermek için Dosya Ekle sitesini kullanın.|

> [!NOTE]
> Microsoft'a gönderilen gönderimlerden veriler Kuzey Office 365 veri merkezlerinde uyumluluk sınırının içinde yer alıyor. Filtreler'in daha etkili olması için, mühendislik ekibi analistleri verileri gözden geçirr. Gönderi, filtreleri iyileştirmeye yardımcı olmak için geri bildirim olarak kabul edilir ve 30 gün süreyle tutulur. Ardından silinir.
