---
title: İstenmeyen posta, istenmeyen posta olmayan ve kimlik avı iletilerini Microsoft'a bildirme
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
description: Yöneticiler, iyi ve kötü iletileri ve dosyaları analiz için Microsoft'a bildirmenin farklı yolları hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d2ddd9c0d96355af1ccdbb40cdd5c7542d9852c1
ms.sourcegitcommit: 58ec09f1fd66af9717dc2743585d06d358ec7360
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2022
ms.locfileid: "65144729"
---
# <a name="report-messages-and-files-to-microsoft"></a>İletileri ve dosyaları Microsoft'a bildirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, hem kullanıcıların hem de yöneticilerin e-posta iletilerini ve dosyalarını Microsoft'a raporlamak için birkaç farklı yöntemi vardır.

|Yöntem|Açıklama|
|---|---|
|[Şüpheli istenmeyen postaları, kimlik avı, URL'leri ve dosyaları Microsoft'a göndermek için Gönderimler portalını kullanın](admin-submission.md)|Exchange Online posta kutuları olan kuruluşlardaki yöneticiler için önerilen raporlama yöntemi (tek başına EOP'de kullanılamaz).|
|[Rapor İletisini veya Rapor Kimlik Avı eklentilerini etkinleştirme](enable-the-report-message-add-in.md)|Outlook ve Web üzerinde Outlook (eski adıyla Outlook Web App) ile çalışır. <br/><br/> Aboneliğinize bağlı olarak, kullanıcıların eklentilerle bildirdiği iletiler [Yönetici Gönderimleri portalında](admin-submission.md), [Otomatik araştırma ve yanıt (AIR) sonuçlarında](air-view-investigation-results.md), [Kullanıcı tarafından bildirilen iletiler raporunda](view-email-security-reports.md#user-reported-messages-report) ve [Gezgin'de](threat-explorer-views.md#email--submissions) kullanılabilir. <br/><br/> Bildirilen iletileri, belirttiğiniz bir posta kutusuna kopyalanacak veya yeniden yönlendirilecek şekilde yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı gönderim ilkeleri](user-submission.md).
|[Outlook'ta yanlış pozitifleri ve yanlış negatifleri bildirme](report-false-positives-and-false-negatives.md)|Rapor İletisi özelliğini kullanarak hatalı pozitif sonuçları (engellenmiş veya gereksiz klasöre gönderilmiş iyi e-posta) ve hatalı negatifleri (gelen kutusuna teslim edilen istenmeyen e-posta veya kimlik avı) Exchange Online Protection (EOP) adresine gönderin.|
|[Kullanıcıların Microsoft'a ne bildirdiğini görmek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Kullanıcılar analiz için Microsoft'a ileti bildirdiğinde size bildirimde bulunmanızı sağlayan bir posta akışı kuralı (taşıma kuralı olarak da bilinir) oluşturmayı öğrenin.|
|[Kötü amaçlı yazılımları ve kötü amaçlı olmayan yazılımları analiz için Microsoft'a gönderme](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Ekleri ve diğer dosyaları göndermek için Microsoft Güvenlik Zekası sitesini kullanın.|

> [!NOTE]
> Bir e-posta varlığını Microsoft'a bildirdiğinizde, sürekli algoritma incelemelerimize dahil etmek için e-postayla ilişkili her şeyin bir kopyasını oluştururuz. Bu kopya e-posta içeriğini, e-posta üst bilgilerini ve e-posta yönlendirmeyle ilgili verileri içerir. İletideki ekler de eklenir.
>
> Microsoft, geri bildiriminizi kuruluşunuzun daha önce açıklanan tüm bilgileri analiz etmemize ve ileti hijyen algoritmalarına ince ayar yapmak için çalışmamıza izni olarak değerlendirmektedir. Gönderinizi bize sağladıktan en fazla 30 gün sonra silene kadar mesajınızı ABD'deki güvenli denetimli veri merkezlerimizde tutarız. Microsoft'taki personel gönderdiğiniz iletiyi ve ekleri okuyabilir ve bu, normalde Office 365 e-posta için izin verilmez. Ancak, e-postanız sizinle Microsoft arasında gizli olarak kabul edilir ve bu inceleme işlemi için e-postayı veya eklerini okuması için gönderiminizi başka bir tarafa sağlarız.
