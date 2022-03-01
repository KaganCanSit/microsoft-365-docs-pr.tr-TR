---
title: Kimlik avı koruması
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender'daki kimlik avı koruma özellikleri hakkında bilgi Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81cd2870ff3471fbd535415229b3ced20bba1fbf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999010"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Microsoft 365'ta kimlik avı koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Kimlik avı* , güvenli veya güvenilir gönderenlerden gelen iletilerde hassas bilgileri çalmaya çalışan bir e-posta saldırısıdır. Belirli kimlik avı kategorileri vardır. Örneğin:

- **Kimlik avı** , hedefli alıcılara özel olarak uyarlanmış odaklanmış ve özelleştirilmiş içerik kullanır (normalde, alıcılar üzerinde saldırgan tarafından uzlaştırmanın ardından).

- **Whaling** en yüksek etkiyi elde için kuruluş içindeki yöneticilere veya diğer yüksek değerli hedeflere yönlendirildi.

- **İş e-posta güvenliği (BEC),** alıcıları ödemelerini onaylamaya, fon aktarmaya veya müşteri verilerini ortaya çıkarmak için sahte güvenilir gönderenler (finans görevlileri, müşteriler, güvenilir iş ortakları, vb.) kullanır. Daha fazla bilgi edinmek için [bu videoyu izleyin](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Verilerinizi** şifrelenen ve şifresini çözmek için ödeme taleplenen fidye yazılımları neredeyse her zaman kimlik avı iletisinde ortaya çıkar. Kimlik avı koruması şifreli dosyaların şifresini çözmenıza yardımcı olmaz, ancak fidye yazılımı kampanyasıyla ilişkilendirilmiş ilk kimlik avı iletilerini algılamaya yardımcı olabilir. Fidye yazılımı saldırılarından kurtarma hakkında daha fazla bilgi için bkz. Fidye yazılımı [saldırılarından fidye yazılımından Microsoft 365](recover-from-ransomware.md).

Giderek büyüyen bir saldırı karmaşıklığıyla, gelişmiş kimlik avı iletilerini eğitimli kullanıcıların belirlemesi bile zordur. Neyse ki, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender'ın ek özellikleri yardımcı olabilir.

## <a name="anti-phishing-protection-in-eop"></a>EOP'de kimlik avı korumasını koruma

EOP (başka bir Microsoft 365, Microsoft Defender Office 365 olmayan kuruluşlar), organizasyonlarınızı kimlik avı tehditlerine karşı korumaya yardımcı olacak özellikler içerir:

- **Kimliği doğrulanmadı** bilgisi: Dış ve iç etki alanlarından gelen iletilerde kimliği doğrulandı olarak algılanan gönderenleri gözden geçirmek ve bu algılanan gönderenlere el ile izin vermek veya engellemek için bilgi ifadeli ifade içgörülerini kullanın. Daha fazla bilgi için bkz [. EOP'de Spoof Intelligence içgörü](learn-about-spoof-intelligence.md).

- **EOP'de** kimlik avı önleme ilkeleri: Kimlik avı kimliğini açma veya kapatma, kimlik doğrulaması olmayan gönderen kimliğini Outlook veya kapatın ve sahte e-postayla engellenen gönderenler için eylemi belirtin. Daha fazla bilgi için bkz. [EOP'de kimlik avı koruma ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

- Kiracı İzin Ver/Engelleme Listesi'ne yer alan kimliği doğruya sahip gönderenlere izin verme veya engelleme: Bilgi bloğu içgörüsinde kararı geçersiz kıl kılıca, kimliği doğruya sahip gönderen, yalnızca Kiracı İzin Ver **/** Engelleme Listesi'nin Gizli Bilgi sekmesinde görüntülenen bir el ile izin verilen veya engellenen giriş haline gelir. Ayrıca, e-posta gönderenlere yönelik girişlere izin verme veya engellemeyi ayrıca, bu kişi kimliğin kimliği doğrulandığından önce el ile oluşturabilir veya engelleyebilirsiniz. Daha fazla bilgi için bkz [. EOP'de Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).

- **Örtülü** e-posta kimlik doğrulaması: EOP, sahte gönderenleri belirlemeye yardımcı olmak için gelen e-posta ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC](use-dmarc-to-validate-email.md) ) için gönderen itibarı, gönderen geçmişi, alıcı geçmişi, davranış çözümlemesi ve diğer gelişmiş tekniklerle gelen e-postayı denetler. Daha fazla bilgi için bkz. [E-posta kimlik doğrulaması Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Windows için Microsoft Defender'da ek kimlik avı koruması Office 365

Çevrimiçi için Microsoft Defender Office 365 daha gelişmiş kimlik avı önleme özellikleri içerir:

- **Office 365 için Microsoft Defender'da** kimlik avı koruma ilkeleri: Belirli ileti gönderenleri ve gönderen etki alanları için kimliğe bürünme koruma ayarlarını, posta kutusu zekası ayarlarını ve ayarlanabilir gelişmiş kimlik avı eşiklerini yapılandırma. Daha fazla bilgi için bkz[. Kimlik avı için Microsoft Defender'da kimlik avı Office 365](configure-mdo-anti-phishing-policies.md). EOP'de kimlik avı önleme ilkeleri ile Office 365 için Defender'da kimlik avı ilkeleri arasındaki farklar hakkında daha fazla bilgi için bkz. [Microsoft 365.](set-up-anti-phishing-policies.md)
- **Kampanya Görünümleri**: Makine öğrenimi ve diğer heuristler, hizmetin ve kuruluşun tamamı için eşgüdümli kimlik avı saldırılarına katılan iletileri tespit ve analiz eder. Daha fazla bilgi için bkz. [For Microsoft Defender'da Kampanya görünümleri Office 365](campaigns.md).
- **Saldırı benzetimi** eğitimi: Yöneticiler sahte kimlik avı iletileri oluşturabilir ve bunları eğitim aracı olarak iç kullanıcılara gönderebilir. Daha fazla bilgi için bkz [. Kimlik avı saldırısının benzetimini yapmak](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Diğer kimlik avı önleme kaynakları

- Son kullanıcılar için: [Kendinizi kimlik avı düzenlerinden ve diğer çevrimiçi sahtekarlık biçimlerinden koruyun](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Kimlik Microsoft 365 kimlik avını önlemek için From adresini nasıl doğrular](how-office-365-validates-the-from-address.md)?
