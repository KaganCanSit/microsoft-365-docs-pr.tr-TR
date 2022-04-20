---
title: Tehdit Gezgini'nde görünümler ve gerçek zamanlı algılamalar
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365 Defender portalında tehditleri araştırmak ve yanıtlamak için Tehdit Gezgini'ni ve gerçek zamanlı algılama raporunu kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ccc26bef5209dd297df0b3008b841edb56cdd160
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971164"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Tehdit Gezgini'nde görünümler ve gerçek zamanlı algılamalar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

:::image type="content" source="../../media/explorer.png" alt-text="Tehdit Gezgini sayfası" lightbox="../../media/explorer.png":::

[Tehdit Gezgini](threat-explorer.md) (ve gerçek zamanlı algılamalar raporu), Güvenlik operasyonları ekiplerinin Microsoft 365 Defender portalındaki tehditleri araştırmasına ve yanıtlamasına yardımcı olan güçlü ve neredeyse gerçek zamanlı bir araçtır. Explorer (ve gerçek zamanlı algılamalar raporu), e-postada ve Office 365'deki dosyalarda şüpheli kötü amaçlı yazılım ve kimlik avı ile ilgili bilgilerin yanı sıra kuruluşunuza yönelik diğer güvenlik tehditleri ve riskleri görüntüler.

- Office 365 Plan 2 [için Microsoft Defender'larınız](defender-for-office-365.md) varsa Gezgin'iniz vardır.
- Office 365 Plan 1 için Microsoft Defender'larınız varsa gerçek zamanlı algılamalarınız vardır.

Explorer'ı (veya gerçek zamanlı algılama raporunu) ilk kez açtığınızda, varsayılan görünüm son 7 güne ilişkin e-posta kötü amaçlı yazılım algılamalarını gösterir. Bu rapor, Kasa Bağlantıları tarafından algılanan kötü amaçlı URL'ler ve [Kasa Ekleri](safe-links.md) tarafından algılanan kötü amaçlı dosyalar gibi Office 365 [algılamaları](safe-attachments.md) için Microsoft Defender'ı da gösterebilir. Bu rapor son 30 güne ilişkin verileri gösterecek şekilde değiştirilebilir (Office 365 P2 ücretli aboneliği için Microsoft Defender ile). Deneme abonelikleri yalnızca son yedi güne ilişkin verileri içerir.

|Abonelik|Yardımcı programı|Veri Günleri|
|---|---|---|
|Office 365 için Microsoft Defender P1 deneme sürümü|Gerçek zamanlı algılamalar|7|
|Office 365 P1 için Microsoft Defender ücretli|Gerçek zamanlı algılamalar|30|
|Office 365 P1 için Microsoft Defender Office 365 P2 deneme sürümü için ücretli test Defender|Tehdit Gezgini|7|
|Office 365 için Microsoft Defender P2 deneme sürümü|Tehdit Gezgini|7|
|Office 365 P2 için Microsoft Defender ücretli|Tehdit Gezgini|30|

> [!NOTE]
> Yakında Gezgin (ve Gerçek zamanlı algılamalar) veri saklama ve deneme kiracıları için arama sınırını 7 günden 30 güne uzatacağız. Bu değişiklik, 70544 no'lu yol haritası öğesinin bir parçası olarak izleniyor ve şu anda bir dağıtım aşamasında.

Görüntülenecek bilgileri değiştirmek için **Görünüm** menüsünü kullanın. Araç ipuçları, hangi görünümü kullanacağınızı belirlemenize yardımcı olur.

:::image type="content" source="../../media/all-email.png" alt-text="Tehdit Gezgini Görünümü menüsü" lightbox="../../media/all-email.png":::

Bir görünüm seçtikten sonra filtreler uygulayabilir ve daha fazla analiz gerçekleştirmek için sorgular ayarlayabilirsiniz. Aşağıdaki bölümlerde Gezgin'de (veya gerçek zamanlı algılamalarda) bulunan çeşitli görünümlere kısa bir genel bakış sağlanır.

## <a name="email--malware"></a>E-posta > Kötü Amaçlı Yazılım

Bu raporu görüntülemek için Gezgin'de (veya gerçek zamanlı algılamalarda) **E-posta** \> **Kötü Amaçlı Yazılımını** **Görüntüle'yi** \> seçin. Bu görünüm, kötü amaçlı yazılım içerdiği belirlenen e-posta iletileri hakkındaki bilgileri gösterir.

:::image type="content" source="../../media/detection-technology.png" alt-text="Kötü amaçlı yazılım olarak tanımlanan e-posta hakkındaki verileri görüntüleme" lightbox="../../media/detection-technology.png":::

Görüntüleme seçenekleri listenizi açmak için **Gönderen'e** tıklayın. Gönderene, alıcılara, gönderen etki alanına, konuya, algılama teknolojisine, koruma durumuna ve daha fazlasına göre verileri görüntülemek için bu listeyi kullanın.

Örneğin, algılanan e-posta iletilerinde hangi eylemlerin gerçekleştirildiğini görmek için **listeden Koruma durumu'nu** seçin. Bir seçenek belirleyin ve ardından Yenile düğmesine tıklayarak bu filtreyi raporunuz için uygulayın.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Tehdit Gezgini için Tehdit Koruması Durumu seçenekleri" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Grafiğin altında belirli iletiler hakkında daha fazla ayrıntı görüntüleyin. Listeden bir öğe seçtiğinizde, seçtiğiniz öğe hakkında daha fazla bilgi edinebileceğiniz bir açılır bölme açılır.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Açılır öğe açılan Tehdit Gezgini" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>E-posta > Kimlik Avı

Bu raporu görüntülemek için Gezgin'de (veya gerçek zamanlı algılamalarda) **E-posta** \> **Kimlik** **Avı'nı Görüntüle'yi** \> seçin. Bu görünüm, kimlik avı girişimi olarak tanımlanan e-posta iletilerini gösterir.

:::image type="content" source="../../media/phish.png" alt-text="Kimlik avı girişimleri olarak tanımlanan e-posta hakkındaki verileri görüntüleme" lightbox="../../media/phish.png":::

Görüntüleme seçenekleri listenizi açmak için **Gönderen'e** tıklayın. Gönderene, alıcılara, gönderen etki alanına, gönderen IP'sine, URL etki alanına göre verileri görüntülemek, karara ve daha fazlasına göre verileri görüntülemek için bu listeyi kullanın.

Örneğin, kişiler kimlik avı girişimi olarak tanımlanan URL'lere tıkladığında hangi eylemlerin gerçekleştirildiğini görmek için **listeden Karara tıklayın'ı** seçin, bir veya daha fazla seçeneği belirleyin ve ardından Yenile düğmesine tıklayın.

:::image type="content" source="../../media/click-verdict.png" alt-text="Kimlik Avı raporu için Tıklama kararı seçenekleri" lightbox="../../media/click-verdict.png":::

Grafiğin altında belirli iletiler, URL tıklamaları, URL'ler ve e-posta kaynağı hakkında daha fazla ayrıntı görüntüleyin.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="E-posta iletilerinde kimlik avı olarak algılanan URL'ler" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Listede algılanan URL gibi bir öğeyi seçtiğinizde, seçtiğiniz öğe hakkında daha fazla bilgi edinebileceğiniz bir açılır bölme açılır.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Algılanan URL ile ilgili ayrıntılar" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>E-posta > Gönderimleri

Bu raporu görüntülemek için Gezgin'de (veya gerçek zamanlı algılamalarda) **E-posta** \> **Gönderimlerini** **Görüntüle'yi** \> seçin. Bu görünüm, kullanıcıların gereksiz olarak değil gereksiz olarak bildirdiği e-postayı veya kimlik avı e-postasını gösterir.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="Kullanıcılar tarafından bildirilen E-posta iletileri" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Görüntüleme seçenekleri listenizi açmak için **Gönderen'e** tıklayın. Gönderene, alıcılara, rapor türüne (kullanıcının e-postanın gereksiz, gereksiz veya kimlik avı değil gereksiz olduğunu belirlemesi) ve daha fazlasına göre bilgileri görüntülemek için bu listeyi kullanın.

Örneğin, kimlik avı girişimi olarak bildirilen e-posta iletileriyle ilgili bilgileri görüntülemek için **Gönderen** \> **Raporu türü'ne** tıklayın, **Kimlik Avı'nı** seçin ve ardından Yenile düğmesine tıklayın.

![Rapor Türü filtresi için kimlik avı seçildi.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Grafiğin altında konu satırı, gönderenin IP adresi, iletiyi gereksiz değil gereksiz veya kimlik avı olarak bildiren kullanıcı gibi belirli e-posta iletileri hakkında daha fazla ayrıntı görüntüleyin.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="Kimlik avı girişimi olarak bildirilen iletiler" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Ek ayrıntıları görüntülemek için listeden bir öğe seçin.

## <a name="email--all-email"></a>E-posta > Tüm e-postalar

Bu raporu görüntülemek için Gezgin'de **Tüm E-postaları Görüntüle'yi** \>  \> seçin. Bu görünümler, kimlik avı veya kötü amaçlı yazılım nedeniyle kötü amaçlı olarak tanımlanan e-postalar ve kötü amaçlı olmayan tüm postalar (normal e-posta, istenmeyen posta ve toplu posta) dahil olmak üzere e-posta etkinliğinin genel görünümünü gösterir.

> [!NOTE]
> **Görüntülenecek çok fazla veri** var hatasını alırsanız filtre ekleyin ve gerekirse görüntülemekte olduğunuz tarih aralığını daraltın.

Filtre uygulamak için **Gönderen'i** seçin, listeden bir öğe seçin ve yenile düğmesine tıklayın. Örneğimizde filtre olarak **Algılama teknolojisini** kullandık (çeşitli seçenekler mevcuttur). Gönderen, gönderenin etki alanı, alıcılar, konu, ek dosya adı, kötü amaçlı yazılım ailesi, koruma durumu (Office 365 tehdit koruma özellikleriniz ve ilkeleriniz tarafından gerçekleştirilen eylemler), algılama teknolojisi (kötü amaçlı yazılımın nasıl algılandığı) ve daha fazlasına göre bilgileri görüntüleyin.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Algılama teknolojisine göre algılanan e-posta hakkındaki verileri görüntüleme" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Grafiğin altında konu satırı, alıcı, gönderen, durum vb. gibi belirli e-posta iletileri hakkında daha fazla ayrıntı görüntüleyin.

## <a name="content--malware"></a>İçerik > Kötü Amaçlı Yazılım

Bu raporu görüntülemek için Gezgin'de (veya gerçek zamanlı algılamalarda) **İçerik** \> **Kötü Amaçlı Yazılımını** **Görüntüle'yi** \> seçin. Bu görünümde, [SharePoint Online, OneDrive İş ve Microsoft Teams Office 365 için Microsoft Defender](mdo-for-spo-odb-and-teams.md) tarafından kötü amaçlı olarak tanımlanan dosyalar gösterilir.

Kötü amaçlı yazılım ailesine, algılama teknolojisine (kötü amaçlı yazılımın nasıl algılandığı) ve iş yüküne (OneDrive, SharePoint veya Teams) göre bilgileri görüntüleyin.

:::image type="content" source="../../media/malware-family.png" alt-text="Algılanan kötü amaçlı yazılım hakkındaki verileri görüntüleme" lightbox="../../media/malware-family.png":::

Grafiğin altında, ek dosya adı, iş yükü, dosya boyutu, dosyayı en son kimin değiştirdiği ve daha fazlası gibi belirli dosyalar hakkında daha fazla ayrıntı görüntüleyin.

## <a name="click-to-filter-capabilities"></a>Tıkla-filtre özellikleri

Gezgin (ve gerçek zamanlı algılamalar) ile bir tıklamayla filtre uygulayabilirsiniz. Göstergedeki bir öğeye tıklar ve bu öğe rapor için bir filtre olur. Örneğin, Gezgin'de Kötü Amaçlı Yazılım görünümüne baktığımızı varsayalım:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Güvenlik & Uyumluluk portalındaki Gezgin sayfası" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Bu grafikte **ATP Patlama'ya tıklanması** aşağıdaki gibi bir görünüme neden olur:

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="Gezgin yalnızca Office 365 için Defender'ı gösterecek şekilde filtrelendi." lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

Bu görünümde, Kasa [Ekleri](safe-attachments.md) tarafından patlatılan dosyalara yönelik verileri inceliyoruz. Grafiğin altında, ekleri Kasa Ekler tarafından algılanan belirli e-posta iletileriyle ilgili ayrıntıları görebiliriz.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="Algılanan ekleri olan e-posta iletileriyle ilgili belirli ayrıntılar" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

Bir veya daha fazla öğe seçildiğinde, seçilen öğeler için seçilecek çeşitli seçenekler sunan **Eylemler** menüsü etkinleştirilir.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Eylemler menüsünü etkinleştiren bir öğe seçme işlemi" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

Tek bir tıklamayla filtreleme ve belirli ayrıntılara gitme özelliği, tehditleri araştırma konusunda size çok zaman kazandırabilir.

## <a name="queries-and-filters"></a>Sorgular ve filtreler

Explorer (gerçek zamanlı algılamalar raporunun yanı sıra), en çok hedeflenen kullanıcılar, en iyi kötü amaçlı yazılım aileleri, algılama teknolojisi ve daha fazlası gibi ayrıntılarda detaya gitmenizi sağlayan çeşitli güçlü filtrelere ve sorgulama özelliklerine sahiptir. Her rapor türü, verileri görüntülemek ve araştırmak için çeşitli yollar sunar.

> [!IMPORTANT]
> Gezgin(veya gerçek zamanlı algılamalar) için sorgu çubuğunda yıldız işareti veya soru işareti gibi joker karakterler kullanmayın. **Konu alanında** e-posta iletileri için arama yaptığınızda, Gezgin (veya gerçek zamanlı algılamalar) kısmi eşleştirme gerçekleştirir ve joker karakter aramasına benzer sonuçlar verir.
