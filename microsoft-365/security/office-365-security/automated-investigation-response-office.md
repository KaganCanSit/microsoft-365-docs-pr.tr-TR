---
title: Office 365 için Microsoft Defender'da otomatik araştırma ve yanıt nasıl çalışır?
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
description: Office 365 için Microsoft Defender'da otomatik araştırma ve yanıt özelliklerinin nasıl çalıştığını görün
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78dc31c055f563f0f9f03bcf12642296459de491
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974245"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da otomatik araştırma ve yanıt nasıl çalışır?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik uyarıları tetiklendiğinde, bu uyarıları incelemek ve kuruluşunuzu korumak için adımlar atmak güvenlik operasyonları ekibinize bağlı olur. Bazı durumlarda, güvenlik operasyonları ekipleri tetiklenen uyarıların hacminden bunalmış gibi hissedebilir. Office 365 için Microsoft Defender'daki otomatik araştırma ve yanıt (AIR) özellikleri yardımcı olabilir.

AIR, güvenlik operasyonları ekibinizin daha verimli ve etkili bir şekilde çalışmasını sağlar. AIR özellikleri, günümüzde mevcut olan iyi bilinen tehditlere yanıt olarak otomatik araştırma süreçlerini içerir. Uygun düzeltme eylemleri onay bekler ve güvenlik operasyonları ekibinizin algılanan tehditlere yanıt vermesini sağlar.

Bu makalede, AIR'in çeşitli örneklerle nasıl çalıştığı açıklanmaktadır. AIR kullanmaya başlamaya hazır olduğunuzda bkz. [Tehditleri otomatik olarak araştırma ve yanıtlama](office-365-air.md).

- [Örnek 1: Kullanıcı tarafından bildirilen kimlik avı iletisi bir araştırma playbook'u başlatır](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Örnek 2: Güvenlik yöneticisi Tehdit Gezgini'nden bir araştırma tetikler](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Örnek 3: Güvenlik operasyonları ekibi, Office 365 Yönetim Etkinliği API'sini kullanarak AIR'i SIEM ile tümleştirir](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Örnek: Kullanıcı tarafından bildirilen kimlik avı iletisi bir araştırma playbook'u başlatır

Kuruluşunuzdaki bir kullanıcının kimlik avı girişimi olduğunu düşündüğü bir e-posta aldığını varsayalım. Bu tür iletileri raporlamak üzere eğitilen kullanıcı, analiz için [Microsoft'a göndermek için Rapor İletisi eklentisini](enable-the-report-message-add-in.md) veya [Rapor Kimlik Avı eklentisini](enable-the-report-phish-add-in.md) kullanır. Gönderim sisteminize de gönderilir ve Gezgin'de **Gönderimler** görünümünde (eski **adıyla Kullanıcı tarafından bildirilen** görünüm) görünür. Ayrıca, kullanıcı tarafından bildirilen ileti artık araştırma playbook'unu otomatik olarak başlatan sistem tabanlı bir bilgilendirme uyarısı tetikler.

Kök araştırma aşamasında, e-postanın çeşitli yönleri değerlendirilir. Bu özellikler şunlardır:

- Ne tür bir tehdit olabileceğine ilişkin bir belirleme;
- Who gönderdi;
- E-postanın gönderildiği yer (altyapı gönderme);
- E-postanın diğer örneklerinin teslim edilip edilmediği;
- Analistlerimizden bir değerlendirme;
- E-postanın bilinen kampanyalarla ilişkilendirilmiş olup olmadığı;
- ve daha fazlasını yapın.

Kök araştırma tamamlandıktan sonra playbook, özgün e-posta ve onunla ilişkili varlıklar üzerinde yapılması önerilen eylemlerin listesini sağlar.

Ardından çeşitli tehdit araştırması ve tehdit avcılığı adımları yürütülür:

- Benzer e-posta iletileri, e-posta kümesi aramaları aracılığıyla tanımlanır.
- Sinyal, [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) gibi diğer platformlarla paylaşılır.
- Şüpheli e-posta iletilerinde herhangi bir kullanıcının kötü amaçlı bağlantılara tıklayıp tıklamadığına ilişkin bir belirleme yapılır.
- Exchange Online Protection ([EOP](exchange-online-protection-overview.md) ve ([Office 365 için Microsoft Defender](defender-for-office-365.md)' da kullanıcılar tarafından bildirilen başka benzer iletiler olup olmadığını görmek için bir denetim yapılır.
- Kullanıcının gizliliğinin tehlikeye atılıp aşılmadığını görmek için bir denetim yapılır. Bu denetim, Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) ve [Azure Active Directory](/azure/active-directory) genelindeki sinyallerden yararlanarak ilgili kullanıcı etkinliği anomalilerini ilişkilendirir.

Tehdit avcılığı aşamasında çeşitli avlanma adımlarına riskler ve tehditler atanır.

Düzeltme, playbook'un son aşamasıdır. Bu aşamada, araştırma ve avcılık aşamalarına göre düzeltme adımları atılır.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Örnek: Güvenlik yöneticisi Tehdit Gezgini'nden bir araştırma tetikler

Bir uyarı tarafından tetiklenen otomatik araştırmalara ek olarak, kuruluşunuzun güvenlik operasyonları ekibi [Tehdit Gezgini'ndeki](threat-explorer.md) bir görünümden otomatik bir araştırma tetikleyebilir. Bu araştırma bir uyarı da oluşturur, böylece Microsoft 365 Defender olaylar ve dış SIEM araçları bu araştırmanın tetiklendiğini görebilir.

Örneğin, Gezgin'de **Kötü Amaçlı Yazılım** görünümünü kullandığınızı varsayalım. Grafiğin altındaki sekmeleri kullanarak **E-posta** sekmesini seçersiniz. Listeden bir veya daha fazla öğe seçerseniz **+ Eylemler** düğmesi etkinleştirilir.

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Seçili iletileri içeren Gezgin" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::

**Eylemler** menüsünü kullanarak **Araştırmayı tetikle'yi** seçebilirsiniz.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Seçili iletiler için Eylemler menüsü" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

Bir uyarı tarafından tetiklenen playbook'lara benzer şekilde, Explorer'daki bir görünümden tetiklenen otomatik araştırmalarda kök araştırma, tehditleri tanımlama ve ilişkilendirme adımları ve bu tehditleri azaltmak için önerilen eylemler bulunur.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Örnek: Güvenlik operasyonları ekibi, Office 365 Yönetim Etkinliği API'sini kullanarak AIR'i SIEM ile tümleştirir

Office 365 için Microsoft Defender'daki AIR özellikleri, güvenlik operasyonları ekiplerinin tehditleri izlemek ve ele almak için kullanabileceği [raporlar & ayrıntıları](air-view-investigation-results.md) içerir. Ancak AIR özelliklerini diğer çözümlerle de tümleştirebilirsiniz. Örnek olarak güvenlik bilgileri ve olay yönetimi (SIEM) sistemi, servis talebi yönetim sistemi veya özel raporlama çözümü verilebilir. Bu tür tümleştirmeler [Office 365 Yönetim Etkinliği API'sini](/office/office-365-management-api/office-365-management-activity-api-reference) kullanarak yapılabilir.

Örneğin kısa süre önce bir kuruluş, güvenlik operasyonları ekibine AIR tarafından önceden işlenmiş kullanıcı tarafından bildirilen kimlik avı uyarılarını görüntülemesi için bir yol ayarladı. Çözümü, ilgili uyarıları kuruluşun SIEM sunucusu ve olay yönetim sistemiyle tümleştirir. Çözüm, hatalı pozitif sonuçların sayısını büyük ölçüde azaltır, böylece güvenlik operasyonları ekibi zamanlarını ve çabalarını gerçek tehditlere odaklayabilir. Bu özel çözüm hakkında daha fazla bilgi edinmek [için teknik Community blogu: Office 365 için Microsoft Defender ve O365 Yönetim API'siyle SOC'nizin Verimliliğini Artırma makalesine](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185) bakın.

## <a name="next-steps"></a>Sonraki adımlar

- [AIR kullanarak Kullanmaya başlayın](office-365-air.md)
- [Bekleyen veya tamamlanan düzeltme eylemlerini görüntüleme](air-review-approve-pending-completed-actions.md)
