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
description: Portalda tehditlere yönelik araştırma yapmak ve onları yanıtlamak için Tehdit Gezgini'ni ve gerçek zamanlı algılamalar raporunu nasıl Microsoft 365 Defender öğrenin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d21773694e1dc9472a9a8ac566c8eaacc00fcab8
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682867"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Tehdit Gezgini'nde görünümler ve gerçek zamanlı algılamalar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


![Threat Explorer.](../../media/explorer.png)

[Tehdit Gezgini](threat-explorer.md) (ve gerçek zamanlı algılamalar raporu), Güvenlik İşlemleri ekiplerinin portalda tehditlerini araştırmalarına ve yanıtlamalarına yardımcı olmak için güçlü, yakın gerçek zamanlı Microsoft 365 Defender aracıdır. Gezgin (ve gerçek zamanlı algılamalar raporu), Office 365'te e-postada ve dosyalarda kötü amaçlı yazılım şüpheleri ve kimlik avı şüpheleri ile ilgili bilgilerin yanı sıra, diğer güvenlik tehditlerini ve riskleri de görüntüler.

- Plan 2 için [Microsoft Defender Office 365](defender-for-office-365.md) varsa Explorer'a sahipsinizdir.
- Plan 1 için Microsoft Defender Office 365 varsa, gerçek zamanlı algılamanız olur.

Gezgin'i (veya gerçek zamanlı algılamalar raporunu) ilk kez açarsanız, varsayılan görünüm son 7 gün için e-posta kötü amaçlı yazılım algılamalarını gösterir. Ayrıca bu rapor, Kasa Bağlantıları tarafından algılanan kötü amaçlı URL'ler ve Ekler tarafından algılanan kötü amaçlı dosyalar gibi Office 365 [](safe-links.md)algılamaları için Microsoft Defender [Kasa gösterebilir](safe-attachments.md). Bu rapor, (ücretli P2 aboneliği için Microsoft Defender ile) son 30 gün Office 365 değiştirilebilir. Deneme abonelikleri yalnızca son yedi gün için veri içerir.

|Abonelik|Yardımcı Program|Veri Günleri|
|---|---|---|
|Office 365 P1 denemesi için Microsoft Defender|Gerçek zamanlı algılamalar|7|
|Ücretli Office 365 P1 için Microsoft Defender|Gerçek zamanlı algılamalar|30|
|Office 365 P2 denemesi için ücretli P1 testi Defender için Microsoft Defender Office 365|Tehdit Gezgini|7|
|Office 365 P2 denemesi için Microsoft Defender|Tehdit Gezgini|7|
|ücretli Office 365 P2 için Microsoft Defender|Tehdit Gezgini|30|

> [!NOTE]
> Yakında Gezgini (ve Gerçek zamanlı algılamalar) veri bekletme süresini ve deneme kiracıları için arama sınırını 7 ile 30 gün arasında genişleteceğiz. Bu değişiklik, yol haritası öğesi no. 70544'in bir parçası olarak izlenmektedir ve şu anda bir aşamalı olarak üzerindedir.

Görüntülenen **bilgileri** değiştirmek için Görünüm menüsünü kullanın. Araç bilgileri, hangi görünümün kullanılamayacaklarını belirlemenize yardımcı olur.

![Threat Explorer View menüsü.](../../media/all-email.png)

Görünümü seçtikten sonra, daha fazla çözümleme yapmak için filtreler uygulayabilir ve sorgular oluşturabilirsiniz. Aşağıdaki bölümlerde, Gezgin'de bulunan çeşitli görünümlere (veya gerçek zamanlı algılamalara) ilişkin kısa bir genel bakış sağlanmaktadır.

## <a name="email--malware"></a>E-posta > Kötü Amaçlı Yazılım

Bu raporu görüntülemek için, Gezgin'de (veya gerçek zamanlı algılamalar) E-posta Kötü Amaçlı Yazılımlarını **Görüntüle'yi** \>  \> seçin. Bu görünüm, kötü amaçlı yazılım içeren olarak tanımlanan e-posta iletileri hakkında bilgileri gösterir.

![Kötü amaçlı yazılım olarak tanımlanan e-postayla ilgili verileri görüntüleme.](../../media/detection-technology.png)

Görüntüleme **seçenekleri listenizi** açmak için Gönderen'e tıklayın. Gönderene, alıcılara, gönderen etki alanına, konuya, algılama teknolojisine, koruma durumuna ve diğer verilere göre verileri görüntülemek için bu listeyi kullanın.

Örneğin, algılanan e-posta iletileri üzerinde hangi eylemlerin gerçekleştir olduğunu görmek için, **listede Koruma durumu'seçin** . Bir seçenek belirtin ve ardından bu filtreyi raporunuza uygulamak için Yenile düğmesine tıklayın.

![Tehdit Gezgini için Tehdit Koruması Durumu seçenekleri.](../../media/ThreatExplorerProtectionStatusOptions.png)

Grafiğin altında, belirli iletiler hakkında daha fazla ayrıntı görüntüleyebilirsiniz. Listeden bir öğe seçildiğinde, seçtiğiniz öğe hakkında daha fazla bilgi edinmek için bir açılır bölme açılır.

![Açılan açılır gezgin ile Tehdit Gezgini.](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>E-> Kimlik Avı

Bu raporu görüntülemek için, Gezgin'de (veya gerçek zamanlı algılamalar) E-posta Kimlik **Avını Görüntüle'yi** \>  \> **seçin**. Bu görünüm, kimlik avı girişimleri olarak tanımlanan e-posta iletilerini gösterir.

![Kimlik avı girişimleri olarak tanımlanan e-postayla ilgili verileri görüntüleme.](../../media/phish.png)

Görüntüleme **seçenekleri listenizi** açmak için Gönderen'e tıklayın. Gönderene, alıcılara, gönderen etki alanına, gönderen IP'sına, URL etki alanına göre verileri görüntülemek için bu listeyi kullanın, karara tıklayın ve daha fazlası.

Örneğin, kimlik avı girişimleri olarak tanımlanan URL'lere tıklanmasıyla hangi eylemlerin gerçekleştirildiklerine bakın, listede karara  tıklayın, bir veya birden çok seçenek belirleyin ve sonra Yenile düğmesine tıklayın.

![Kimlik Avı raporu için karar seçeneklerini tıklatın.](../../media/click-verdict.png)

Grafiğin altında belirli iletiler, URL tıklamaları, URL'ler ve e-posta kaynağı hakkında daha fazla ayrıntı görüntüleyebilirsiniz.

![E-posta iletisinde kimlik avı olarak algılanan URL'ler.](../../media/ThreatExplorerEmailPhishURLs.png)

Listeden bir öğe, örneğin algılanan bir URL'yi seçtiğiniz zaman, seçtiğiniz öğe hakkında daha fazla bilgi edinebilirsiniz açılır.

![Algılanan URL hakkında ayrıntılar.](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>E-> Göndermeleri

Bu raporu görüntülemek için, Gezgin'de (veya gerçek zamanlı algılamalar) E-posta **Gönderimlerini** **Görüntüle'yi** \> \> **seçin**. Bu görünüm, kullanıcıların gereksiz değil, kimlik avı e-postası olarak bildir ettiği e-postaları gösterir.

![Kullanıcılar tarafından bildirilen e-posta iletileri.](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

Görüntüleme **seçenekleri listenizi** açmak için Gönderen'e tıklayın. Gönderenlere, alıcılara, rapor türüne (kullanıcının e-postanın gereksiz değil, kimlik avı değil, gereksiz olduğunu belirlemesi) ve daha pek çok bilgiye göre bilgileri görüntülemek için bu listeyi kullanın.

Örneğin, kimlik avı girişimleri olarak bildirilen e-posta iletileriyle ilgili bilgileri görüntülemek için Gönderen Raporu  türü'ne **tıklayın,**\> Kimlik Avı'ı seçin ve sonra Yenile düğmesine tıklayın.

![Rapor Türü filtresi için seçilen kimlik avı.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Grafiğin altında, konu satırı, gönderenin IP adresi, iletiyi gereksiz değil veya kimlik avı olarak bildiren kullanıcı gibi belirli e-posta iletileri hakkında daha fazla ayrıntı görüntülenir.

![Kimlik avı girişimleri olarak bildirilen iletiler.](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

Ek ayrıntıları görüntülemek için listeden bir öğe seçin.

## <a name="email--all-email"></a>Tüm e> te e-posta adresi

Bu raporu görüntülemek için Gezgin'de Tüm E-postayı **Görüntüle'yi** \>  \> **seçin**. Bu görünümler, kimlik avı veya kötü amaçlı yazılımdan dolayı kötü amaçlı olarak tanımlanan e-postalar ve kötü amaçlı olmayan tüm postalar (normal e-posta, istenmeyen posta ve toplu posta) dahil olmak üzere, e-posta etkinliğinin hepsi açık bir görünümünü gösterir.

> [!NOTE]
> Görüntü için çok fazla veri **var** hatasını alırsanız, filtre ekleyin ve gerekirse görüntülemekte olduğu tarih aralığını daraltabilirsiniz.

Filtre uygulamak için **Gönderen'i** seçin, listeden bir öğe seçin ve ardından Yenile düğmesine tıklayın. Örneğimizde Algılama teknolojisini **filtre olarak** kullandık (çeşitli seçenekler mevcut). Gönderene, gönderenin etki alanına göre, alıcılara, konuya, ek dosya adı, kötü amaçlı yazılım ailesi, koruma durumu (Office 365'ta tehdit koruması özellikleri ve ilkeleriniz tarafından  alınan eylemler), algılama teknolojisi (kötü amaçlı yazılımın nasıl algılandı) ve daha birçok bilgiye göre bilgileri görüntüleme.

![Algılama teknolojisiyle algılanan e-postayla ilgili verileri görüntüleme.](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

Grafiğin altında, konu satırı, alıcı, gönderen, durum gibi belirli e-posta iletileri hakkında daha fazla ayrıntı görüntüleyebilirsiniz.

## <a name="content--malware"></a>İçerik > Kötü Amaçlı Yazılım

Bu raporu görüntülemek için, Gezgin'de (veya gerçek zamanlı algılamalar) İçeriği Kötü Amaçlı Yazılımı **Görüntüle'yi** \>  \> **seçin**. Bu görünümde, [SharePoint Online, OneDrive İş](mdo-for-spo-odb-and-teams.md) ve diğer programlarda Microsoft Defender tarafından Office 365 kötü amaçlı olarak tanımlanan Microsoft Teams.

Bilgileri kötü amaçlı yazılım ailesi, algılama teknolojisi (kötü amaçlı yazılımın nasıl algılandı) ve iş yüküne (kötü amaçlı yazılım, OneDrive, SharePoint veya başka bir Teams.

![Algılanan kötü amaçlı yazılımla ilgili verileri görüntüleme.](../../media/malware-family.png)

Grafiğin altında, ek dosya adı, iş yükü, dosya boyutu, dosyayı son değiştiren kişi gibi belirli dosyalar hakkında daha fazla ayrıntı ve daha fazlasını görüntüleyebilirsiniz.

## <a name="click-to-filter-capabilities"></a>Tıkla-filtre özellikleri

Gezgin (ve gerçek zamanlı algılamalar) ile, bir tıklamayla filtre uygulayabilirsiniz. Göstergede bir öğeye tıklayın; bu öğe rapora filtre olur. Örneğin, Gezgin'de Kötü Amaçlı Yazılım görünümüne bak we'miz olduğunu varsayalım:

![Tehdit yönetimi Gezgini'ne \> gidin.](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Bu **grafikte ATP'nin** Detonasyonu tıklat tıklat sonunda şöyle bir görünüm elde olur:

![Explorer, Bu Detonation sonuçları için yalnızca Defender Office 365 görüntüleniyor.](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

Bu görünümde, artık Ekleri Olan Kullanıcı Ekleri tarafından Kasa [görünüyor](safe-attachments.md). Grafiğin altında, Ekleri Olan E-posta Ekleri ile algılanan belirli e-posta iletileri Kasa görebiliriz.

![Algılanan ekleri olan e-posta iletileri hakkında belirli ayrıntılar.](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

Bir veya birden çok öğe seçildiğinde, **seçilen** öğeler için seçilecek çeşitli seçenekler sunan Eylemler menüsü etkindir.

![Bir öğe seçerek Eylemler menüsünü etkinleştirir.](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

Bir tıklamayla filtre uygulama ve belirli ayrıntılara git özelliği, tehditleri araştırmada size çok zaman yardımcı olabilir.

## <a name="queries-and-filters"></a>Sorgular ve filtreler

Explorer'da (gerçek zamanlı algılamalar raporunun yanı sıra), en çok hedefli kullanıcılar, en iyi kötü amaçlı yazılım aileleri, algılama teknolojisi ve daha fazlası gibi ayrıntılarda detaya gitmelerine olanak sağlayan çeşitli güçlü filtreler ve sorgulama özellikleri vardır. Her tür rapor, verileri görüntülemek ve keşfetmek için çeşitli yollar sunar.

> [!IMPORTANT]
> Gezgin'in sorgu çubuğunda yıldız veya soru işareti gibi joker karakterler (veya gerçek zamanlı algılamalar) kullanmayın. Konu alanında e-posta  iletilerini aratırsanız, Gezgin (veya gerçek zamanlı algılamalar) kısmi eşleştirme ve verim sonuçlarını, joker karakterlerle benzer sonuçlar verir.
