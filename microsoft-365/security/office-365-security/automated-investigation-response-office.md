---
title: Microsoft Defender for Office 365'da otomatik soruşturma ve yanıt nasıl Office 365
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: otomatik olay yanıtı, araştırma, düzeltme, tehdit koruması
ms.date: 01/29/2021
description: İş için Microsoft Defender'da otomatik araştırma ve yanıt yeteneklerinin nasıl Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f515567eca50f99e654df15ddc0b69eb186ba89a
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63008900"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365'da otomatik soruşturma ve yanıt nasıl Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik uyarıları tetiklendiğinden, güvenlik işlemleri ekibinin bu uyarılara göz atarak kurumlarınızı korumak için gerekli adımları atmış olur. Bazen, güvenlik işlemleri ekipleri tetiklenen uyarı ses düzeyine boğulmuş gibi hissederler. Çalışma için Microsoft Defender'daki otomatik araştırma ve yanıt (AIR) Office 365 yardımcı olabilir.

AIR, güvenlik işlemleri ekibimizin daha verimli ve etkili bir şekilde çalışmasına olanak sağlar. AIR özellikleri, bugün var olan iyi bilinen tehditlere yanıt olarak otomatik soruşturma süreçleri içerir. Uygun düzeltme eylemleri onay bekliyor, bu da güvenlik işlemleri ekibimizin algılanan tehditlere yanıt vermesini sağlar.

Bu makalede AIR'nin çeşitli örneklerde nasıl çalıştığını bulabilirsiniz. AIR kullanmaya başlamaya hazırsanız, bkz. Tehditleri [otomatik olarak araştırma ve yanıtlama](office-365-air.md).

- [Örnek 1: Kullanıcı tarafından bildirilen bir kimlik avı iletisi araştırma playbook'larını başlatma](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Örnek 2: Güvenlik yöneticisi Threat Explorer'dan gelen bir soruşturmayı tetikler](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Örnek 3: Güvenlik işlemleri ekibi AIR'yi SIEM'leriyle Office 365 Yönetim Etkinliği API'si ile tümleştirmektedir](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Örnek: Kullanıcı tarafından bildirilen bir kimlik avı iletisi bir araştırma playbook'ını başlatıyor

Organizasyonumdan bir kullanıcının kimlik avı girişimi olduğunu düşünüyor olduğu bir e-posta aldığını varsayalım. Bu tür iletileri raporla eğitimini alan kullanıcı, çözümleme için [](enable-the-report-message-add-in.md) Rapor İletisi eklentiyi veya Rapor [](enable-the-report-phish-add-in.md) Kimlik Avı eklentilerini kullanarak bu eklentiyi Microsoft'a gönderir. Gönderi sisteminize de gönderilir ve Gönderiler görünümünde Gezgin'de görünür (eski  adı Kullanıcı tarafından **bildirilen görünüm).** Buna ek olarak, kullanıcı tarafından bildirilen ileti artık sistem tabanlı bilgisel uyarıyı tetikler ve araştırma playbook'larını otomatik olarak başlatılır.

Kök araştırma aşamasında, e-postanın çeşitli yönleri değerlendirilir. Bu özellikler şunlardır:

- Bunun ne tür bir tehdit olabileceğini belirleme;
- Who gönderme;
- E-postanın gönderildiği yer (gönderme altyapısı);
- E-postanın diğer örneklerinin teslim veya engellenmiş olup olmadığı;
- Analistlerimizin değerlendirmesini;
- E-postanın bilinen herhangi bir kampanyayla ilişkilendirilip ilişkilendirilmediği;
- ve daha fazlasını.

Kök araştırma tamamlandıktan sonra, oynatma defteri özgün e-postada ve ilişkili varlıklarda işlem yapmak için önerilen eylemlerin listesini sağlar.

Ardından, çeşitli tehdit soruşturmaları ve arama adımları yürütülür:

- Benzer e-posta iletileri, e-posta kümesi aramaları yoluyla tanımlanır.
- Sinyal, Uç Nokta için [Microsoft Defender gibi diğer platformlarla paylaşılır](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Herhangi bir kullanıcının şüpheli e-posta iletilerine gelen kötü amaçlı bağlantılara tıklamış olup olmadığını belirleme.
- Kullanıcılar tarafından bildirilen benzer Exchange Online Protection başka ileti olup Office 365 için [EOP (EOP](exchange-online-protection-overview.md) ve Office 365 [için Microsoft Defender](defender-for-office-365.md)) üzerinden bir denetim yapılır.
- Bir kullanıcının güvenliği ihlal edilmiş olup olduğunu görmek için bir denetim yapılır. Bu denetim tüm ilgili kullanıcı etkinliklerini Office 365 uyumlu Office 365 Bulut Uygulamaları için [Microsoft Defender](/cloud-app-security) ve Azure Active Directory tabanlı [](/azure/active-directory)sinyallerden yararlanıyor.

Av aşamasında riskler ve tehditler çeşitli av adımlarına atanır.

Düzeltme, çalışma kitabının son aşamasıdır. Bu aşamada, inceleme ve av aşamaları temel alınarak düzeltme adımları  alınır.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Örnek: Güvenlik yöneticisi Threat Explorer'dan gelen bir soruşturmayı tetikler

Bir uyarı tarafından tetiklenen otomatik soruşturmalara ek olarak, kuruluş güvenlik işlemleri ekibi Tehdit Gezgini'nde bir görünümden otomatik bir soruşturma da [tetikler](threat-explorer.md).  Bu araştırma aynı zamanda bir uyarı oluşturur ve böylece Microsoft 365 Defender ve dış SIEM araçları bu araştırmanın tetik tetikle olduğunu görebilir.

Örneğin, Gezgin'de Kötü Amaçlı Yazılım **görünümünü kullanmakta** olduğunu varsayalım. Grafiğin altındaki sekmeleri kullanarak E-posta sekmesini **seçin** . Listeden bir veya daha fazla öğe seçmeniz, **+ Eylemler** düğmesini etkinleştirir.

![Seçili iletilerle birlikte Gezgin.](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

Eylemler menüsünü **kullanarak** Araştırmayı tetikle'yi **seçebilirsiniz**.

![Seçili iletiler için Eylemler menüsü.](../../media/explorer-malwareview-selectedemails-actions.jpg)

Uyarı tarafından tetiklenen çalışma kitaplarına benzer şekilde, Explorer'da bir görünümden tetiklenen otomatik soruşturmalar bir kök araştırma, tehditleri belirleme ve birbiriyle ilişkisine yönelik adımlar ve bu tehditleri azaltmak için önerilen eylemler içerir.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Örnek: Güvenlik işlemleri ekibi, AIR'yi SIEM'leriyle Office 365 Yönetim Etkinliği API'si ile tümleştirmektedir

Hava Durumu özellikleri, güvenlik Office 365 ekiplerin tehditleri izlemek [&](air-view-investigation-results.md) için kullanabileceği raporlar ve ayrıntılar içerir. Ancak AIR özelliklerini diğer çözümlerle de tümleştirin. Örnek olarak güvenlik bilgileri ve olay yönetimi (SIEM) sistemi, olay yönetim sistemi veya özel raporlama çözümü örnek olarak verilmiştir. Bu tür tümleştirmeler, Office 365 [Yönetim Etkinliği API'si kullanılarak yapılabilir](/office/office-365-management-api/office-365-management-activity-api-reference).

Örneğin, yakın zamanda bir kuruluş, güvenlik işlemleri ekibi tarafından zaten AIR tarafından işlenen kullanıcı tarafından bildirilen kimlik avı uyarılarını görüntülemesi için bir yol ayarlamış. Çözümü, ilgili uyarıları kuruluşun SIEM sunucusuyla ve olay yönetimi sistemiyle tümleştirin. Çözüm, güvenlik işlemleri ekibinin zaman ve çabalarını gerçek tehditlere odaklanması için hatalı pozitif sonuç sayısını büyük ölçüde azaltır. Bu özel çözüm hakkında daha fazla bilgi edinmek için bkz. Teknik Community [blogu: Microsoft Defender ile SOC'nizin Office 365 ve O365 Yönetim API'sinin etkisini geliştirme](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Sonraki adımlar

- [AIR kullanmaya başlama](office-365-air.md)
- [Bekleyen veya tamamlanmış düzeltme eylemlerini görüntüleme](air-review-approve-pending-completed-actions.md)
