---
title: Otomatik araştırma ve yanıt Çalışma'da Office 365 için Microsoft Defender
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
description: Otomatik araştırma ve yanıt yeteneklerinin çalışma ve çalışma Office 365 için Microsoft Defender
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7173d45fed25fe1d0d1e93dbcc259046c1f221cd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474277"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Otomatik araştırma ve yanıt Çalışma'da Office 365 için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik uyarıları tetiklendiğinden, güvenlik işlemleri ekibinin bu uyarılara göz atarak kurumlarınızı korumak için gerekli adımları atmış olur. Bazen, güvenlik işlemleri ekipleri tetiklenen uyarı ses düzeyine boğulmuş gibi hissederler. Bu konudaki otomatik araştırma ve yanıt (AIR) Office 365 için Microsoft Defender yardımcı olabilir.

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
- Sinyal, sinyal gibi diğer platformlarla [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Herhangi bir kullanıcının şüpheli e-posta iletilerine gelen kötü amaçlı bağlantılara tıklamış olup olmadığını belirleme.
- Kullanıcılar tarafından bildirilen benzer ileti Exchange Online Protection başka ileti [olup](defender-for-office-365.md) Office 365 için Microsoft Defender için [EOP ve (EOP](exchange-online-protection-overview.md)) genelinde denetim yapılır.
- Bir kullanıcının güvenliği ihlal edilmiş olup olduğunu görmek için bir denetim yapılır. Bu denetim, ilgili kullanıcı Office 365 [etkinliklerini Microsoft Defender for Cloud Apps](/cloud-app-security) ilgili Azure Active Directory ilgili tüm veri kaynak ve [](/azure/active-directory)kaynak Azure Active Directory sinyallerden yararlanıyor.

Av aşamasında riskler ve tehditler çeşitli av adımlarına atanır.

Düzeltme, çalışma kitabının son aşamasıdır. Bu aşamada, inceleme ve av aşamaları temel alınarak düzeltme adımları  alınır.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Örnek: Güvenlik yöneticisi Threat Explorer'dan gelen bir soruşturmayı tetikler

Bir uyarı tarafından tetiklenen otomatik soruşturmalara ek olarak, kuruluş güvenlik işlemleri ekibi Tehdit Gezgini'nde bir görünümden otomatik bir soruşturma da [tetikler](threat-explorer.md).  Bu araştırma aynı zamanda bir uyarı oluşturur ve böylece Microsoft 365 Defender ve dış SIEM araçları bu araştırmanın tetik tetikle olduğunu görebilir.

Örneğin, Gezgin'de Kötü Amaçlı Yazılım **görünümünü kullanmakta** olduğunu varsayalım. Grafiğin altındaki sekmeleri kullanarak E-posta sekmesini **seçin** . Listeden bir veya daha fazla öğe seçmeniz, **+ Eylemler** düğmesini etkinleştirir.

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Seçili iletilerin yer olduğu Gezgin" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::


Eylemler menüsünü **kullanarak** Araştırmayı tetikle'yi **seçebilirsiniz**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Seçili iletiler için Eylemler menüsü" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

Uyarı tarafından tetiklenen çalışma kitaplarına benzer şekilde, Explorer'da bir görünümden tetiklenen otomatik soruşturmalar bir kök araştırma, tehditleri belirleme ve birbiriyle ilişkisine yönelik adımlar ve bu tehditleri azaltmak için önerilen eylemler içerir.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Örnek: Güvenlik işlemleri ekibi, AIR'yi SIEM'leriyle Office 365 Yönetim Etkinliği API'si ile tümleştirmektedir

Hava Durumu özellikleri Office 365 için Microsoft Defender güvenlik [& tehditlerini](air-view-investigation-results.md) izlemek ve adreslerine yönelik olarak kullanabileceği raporlar ve ayrıntılar içerir. Ancak AIR özelliklerini diğer çözümlerle de tümleştirin. Örnek olarak güvenlik bilgileri ve olay yönetimi (SIEM) sistemi, olay yönetim sistemi veya özel raporlama çözümü örnek olarak verilmiştir. Bu tür tümleştirmeler, Office 365 [Yönetim Etkinliği API'si kullanılarak yapılabilir](/office/office-365-management-api/office-365-management-activity-api-reference).

Örneğin, yakın zamanda bir kuruluş, güvenlik işlemleri ekibi tarafından zaten AIR tarafından işlenen kullanıcı tarafından bildirilen kimlik avı uyarılarını görüntülemesi için bir yol ayarlamış. Çözümü, ilgili uyarıları kuruluşun SIEM sunucusuyla ve olay yönetimi sistemiyle tümleştirin. Çözüm, güvenlik işlemleri ekibinin zaman ve çabalarını gerçek tehditlere odaklanması için hatalı pozitif sonuç sayısını büyük ölçüde azaltır. Bu özel çözüm hakkında daha fazla bilgi edinmek için teknik destek [Community bloguna bakın: Teknik Destek ile SOC'nizin Office 365 için Microsoft Defender ve O365 Yönetim API'sinin etkisini artırma](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Sonraki adımlar

- [Kullanmaya başlayın AIR kullanarak kullanma](office-365-air.md)
- [Bekleyen veya tamamlanmış düzeltme eylemlerini görüntüleme](air-review-approve-pending-completed-actions.md)
