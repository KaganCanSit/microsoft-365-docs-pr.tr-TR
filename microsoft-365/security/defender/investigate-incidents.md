---
title: E-Microsoft 365 Defender'de olayları araştır
description: Cihazlar, kullanıcılar ve posta kutularıyla ilgili olayları araştırabilirsiniz.
keywords: olay, olaylar, çözümleme, yanıt, makineler, cihazlar, kullanıcılar, kimlikler, posta, e-posta, posta kutusu, araştırma, grafik, kanıt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 776680db7b2666cc964f82e88cd6af9e6bab7558
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500265"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>E-Microsoft 365 Defender'de olayları araştır

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Microsoft 365 Defender tüm ilgili uyarıları, varlıkları, soruşturmaları ve kanıtları cihazlarınız, kullanıcılarınız ve posta kutularınız genelinde bir olayda bir araya toplar ve size bir saldırının tüm ekmeklerini kapsamlı bir şekilde incelemenizi sağlar.

Bir olayda, anızı etkileyen uyarıları analiz eder, bunların ne anlama gelen olduğunu anlar ve kanıtları harmanlarsınız, böylece etkili bir düzeltme planı saptabilirsiniz.

## <a name="initial-investigation"></a>İlk araştırma

Ayrıntılara atlamadan önce, olayın özelliklerine ve özetine göz atabilirsiniz.

Onay işareti sütunundan olayı seçerek başlayabilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Portalda bir olayı Microsoft 365 Defender seçme" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Bunu bildiğinizde, olay hakkında önem derecesi, atandığı kişi ve [MITRE ATT&trade;](https://attack.mitre.org/)&gibi önemli bilgilerle birlikte bir özet bölmesi açılır. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Portalda bir olayın özet ayrıntılarını görüntüleyen Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

Buradan Olay sayfasını **aç'ı seçin**. Bu, daha fazla özet bilgi ve uyarılar, cihazlar, kullanıcılar, soruşturmalar ve kanıt için sekmeler bu olayın ana sayfasını açar.

Ayrıca, bir olayın ana sayfasını, olay sırasından olay adını seçerek de açabilirsiniz.

## <a name="summary"></a>Özet

Özet **sayfası** , olayla ilgili olarak dikkat çekmek istediğiniz en önemli şeylerden bir anlık görüntü bakış sağlar.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Portalda bir olayın özet Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Bilgiler bu bölümlerde düzenlenmiştir.

| Bölüm | Açıklama |
|:-------|:-----|
| Uyarılar ve kategoriler | Kill zincirine karşı saldırının ne kadar gelişmiş olduğunu görsel ve sayısal olarak görüntüler. Diğer Microsoft güvenlik ürünleri gibi, Microsoft 365 Defender de [MITRE ATT&CK çerçevesine göre&trade;](https://attack.mitre.org/) hizalanır. Uyarılar zaman çizelgesi uyarıların hangi sırayla ve her biri için durumlarıyla adını kronolojik sırada gösterir. |
| Kapsam |  Etkilenen cihazların, kullanıcıların ve posta kutularının sayısını görüntüler ve varlıkları risk düzeyi ve soruşturma önceliğini sırasıyla listeler. |
| Kanıt | Olaydan etkilenen varlıkların sayısını görüntüler. |
| Olay bilgileri | Olayın etiketler, durum ve önem düzeyi gibi özelliklerini görüntüler. |
|||

Olayın **göreli önemini** değerlendirmek ve ilişkili uyarılara ve etkileyen varlıklara hızla erişmek için Özet sayfasını kullanın.

## <a name="alerts"></a>Uyarılar

Uyarılar **sekmesinde** , olayla ilgili uyarılar için uyarı kuyruğunı ve onlar hakkında aşağıdakiler gibi diğer bilgileri görüntüleyebilirsiniz:

- Önem Derecesi.
- Uyarıya katılan varlıklar.
- Uyarıların (Kimlik için Microsoft Defender, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Bulut için Defender ve uygulamanın kaynağı yönetim eklenti)'yi seçin.
- Birbirine bağlı bağlantının nedeni.

İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Microsoft 365 Defender portalında bir olay için Uyarılar bölmesi" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Varsayılan olarak, uyarıları kronolojik olarak sıralanan bu şekilde, saldırının zamanla nasıl oynandı olduğunu görebilirsiniz. Bir olay içinde bir uyarı Microsoft 365 Defender, genel olayın bağlamına özgü uyarı bilgilerini görüntüler. 

Uyarının olaylarını, diğer tetiklenen uyarıların geçerli uyarıya neden olduğunu ve saldırıdan etkilenen tüm varlıkları ve etkinlikleri (cihazlar, dosyalar, kullanıcılar ve posta kutuları dahil) görebilirsiniz.

İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Portalda bulunan bir olayda uyarı Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Olay uyarı sayfasında şu bölümler vardır:

- Uyarı anlatısı, şunları içerir:

   - Ne oldu

   - 2007'de

   - İlgili etkinlikler

- Sağ bölmede uyarı özellikleri (durum, ayrıntılar, açıklama ve diğerleri)

Her uyarı, Uyarı anlatı bölümündeki listelenen alt **kısımlara sahip** olmaz.

Araştırma uyarılarında uyarı kuyruğu ve uyarı sayfalarının nasıl [kullanıldığını öğrenin](investigate-alerts.md).

## <a name="devices"></a>Cihazlar

Cihazlar **sekmesi** olayla ilgili tüm cihazları listeler. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Mobil portalda bir olayın Cihazlar Microsoft 365 Defender sayfası" lightbox="../../media/investigate-incidents/incident-devices.png":::

Cihazın ayrıntılarını, dizin verilerini, etkin uyarıları ve oturum açmış kullanıcıları görmek için cihazın onay işaretini seçin. Uç nokta cihaz envanteri için Defender'da cihaz ayrıntılarını görmek için cihazın adını seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Ürün sayfasında Cihaz stoku seçeneğiyle ilgili Uç Nokta için Microsoft Defender." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

Cihaz sayfasında, cihaz hakkında tüm uyarıları, zaman çizelgesi ve güvenlik önerileri gibi ek bilgiler topleyebilirsiniz. Örneğin, Zaman Çizelgesi sekmesinde  makine zaman çizelgesinde ilerleyerek, makinede gözlemlenen tüm olayları ve davranışları, uyarılarla kesişen kronolojik sırayla görüntüleyebilirsiniz.

> [!TIP]
> Bir cihaz sayfasında isteğe bağlı taramalar da edebilirsiniz. Mobil Microsoft 365 Defender Uç noktalar ve **Cihaz > seçin**. Uyarıları olan bir cihaz seçin ve virüsten koruma taraması çalıştırın. Virüsten koruma taramaları gibi eylemler izde gelir ve Cihaz **envanteri sayfasında** görünür. Daha fazla bilgi edinmek için bkz [. Cihazlarda Defender Virüsten Koruma taraması çalıştırma](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Kullanıcılar

Kullanıcılar **sekmesi** , olayın parçası veya ilgili olduğu belirlenen tüm kullanıcıları listeler. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Portalda Kullanıcılar Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Kullanıcı hesabı tehditi, maruz kalma ve kişi bilgileriyle ilgili ayrıntıları görmek için kullanıcının onay işaretini seçin. Ek kullanıcı hesabı ayrıntılarını görmek için kullanıcı adını seçin.

Kullanıcıları araştırma içinde ek kullanıcı bilgilerini görüntülemeyi ve bir olayın kullanıcılarını [yönetmeyi öğrenin](investigate-users.md).


## <a name="mailboxes"></a>Posta Kutuları

Posta **Kutuları** sekmesi, olayın parçası veya ilgili olduğu belirlenen tüm posta kutularını listeler. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Portalda bir olayın Posta Kutuları Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Etkin uyarıların listesini görmek için posta kutusunun onay işaretini seçebilirsiniz. Posta kutunuza ilişkin Gezgin sayfasında ek posta kutusu ayrıntılarını görmek için posta kutusu adını Office 365 için Defender.

## <a name="investigations"></a>İncelemeler

Araştırma **sekmesi** , bu olayda [uyarılar tarafından](m365d-autoir.md) tetiklenen tüm otomatik soruşturmaları listeler. Otomatik soruşturmalar, otomatik araştırmalarınızı Uç Nokta için Defender'da çalıştıracak şekilde nasıl yapılandırıldığına bağlı olarak, düzeltme eylemleri gerçekleştirecek veya eylemlerin analist onayı için Office 365 için Defender.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Portalda yer alan bir olay için Microsoft 365 Defender sayfası" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Araştırma ve düzeltme durumu hakkında tam bilgi için araştırmanın ayrıntılar sayfasına gitmek için araştırmayı seçin. Araştırma kapsamında onay için bekleyen herhangi bir eylem varsa, bunlar Bekleyen eylemler **geçmişi sekmesinde** görüntülenir. Olay düzeltmesi kapsamında eylemde bulundur.

Ayrıca, şunları gösteren **bir Araştırma** grafiği sekmesi de vardır:

- Uyarıların, organizasyonda etkilenen varlıklarla bağlantısı.
- Hangi varlıklar hangi uyarılarla ve saldırının hikayenin bir parçası olduğuyla bağlantılıdır.
- Olayla ilgili uyarılar.

Araştırma grafiği, saldırının parçası olan farklı şüpheli varlıkları kullanıcılar, cihazlar ve posta kutuları gibi ilgili varlıklarla bağlayarak saldırının tam kapsamını anlamanıza yardımcı olur. 

Daha fazla bilgi için bkz[. Otomatik araştırma ve Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Kanıt ve Yanıt

Kanıt **ve Yanıt** sekmesi, olayda uyarılarda desteklenen tüm olayları ve şüpheli varlıkları gösterir. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Microsoft 365 Defender portalında bir olay için Microsoft 365 Defender sayfası" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender, uyarılarda olayların tüm desteklenen olaylarını ve şüpheli varlıklarını otomatik olarak inceler ve önemli e-postalar, dosyalar, işlemler, hizmetler, IP Adresleri ve daha fazlası hakkında bilgi sağlar. Bu, olayda olası tehditleri hızla algılamanıza ve engellemeye yardımcı olur.

Çözümlenen varlıkların her biri karar (Kötü Amaçlı, Şüpheli, Temiz) ve düzeltme durumuyla işaretlenir. Bu, olayın tamamının düzeltme durumunu ve sonraki adımların neler olacağını anlamanıza yardımcı olur.

## <a name="graph-preview"></a>Graph (Önizleme)

Bu **Graph** saldırının tüm kapsamını, saldırının zaman içinde ağınıza nasıl yayılacaklarını, nereden başlatacaklarını ve saldırgan nereye gittiğini gösterir. Saldırının parçası olan farklı şüpheli varlıkları, kullanıcılar, cihazlar ve posta kutuları gibi ilişkili varlıklarıyla birbirine bağlar. 

**Graph sekmesinde** şunları yapın:

1. Saldırının kronolojisini anlamak için uyarıları ve düğümleri zaman içinde grafikte oynatabilirsiniz.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Sayfa üzerinde uyarıların ve düğümlerin Graph.":::
 

2. Varlık bölmesini açın ve varlık ayrıntılarını gözden geçirmenizi ve dosya silme ya da cihazı yalıtma gibi düzeltme eylemlerine ilişkin işlem görüntülemenizi sağlar.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Microsoft 365 Defender portalında Graph sayfasındaki varlık bölmesi" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. İlgili olduğu varlık temel alarak uyarıları vurgulayın.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="Sayfa üzerinde uyarı Graph vurgusu" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Sonraki adımlar

Gerekirse:

- [Bir olayın uyarılarını araştırma](investigate-alerts.md)
- [Olay kullanıcılarını araştırma](investigate-users.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olaylara öncelik belirleyin](incident-queue.md)
- [Olayları yönetin](manage-incidents.md)
