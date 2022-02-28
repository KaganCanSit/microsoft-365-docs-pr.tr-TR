---
title: Microsoft 365 Merkezinde Rapor Raporları - Microsoft 365 Uygulamaları kullanımı
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: Raporlar panosunda Microsoft 365 Uygulamaları Raporları panosu kullanarak kullanım Microsoft 365 hakkında bilgi Microsoft 365 yönetim merkezi.
ms.openlocfilehash: 5418ea32129a667d198eee7a14e005450105a3ca
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990585"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Microsoft 365 Merkezinde Rapor Raporları - Microsoft 365 Uygulamaları kullanımı

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.

 Örneğin, Microsoft 365 Uygulamaları uygulamaları kullanma lisansı olan her kullanıcının etkinliğini anlamak için uygulamalar genelindeki etkinliklerine ve platformlar arasında bunların nasıl kullanıldıklarına bakabilirsiniz.
 
 > [!NOTE]
 > Paylaşılan bilgisayar etkinleştirmeleri bu rapora dahil değildir.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Microsoft 365 Uygulamaları kullanım raporuna nasıl edinebilirsiniz?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, Etkin kullanıcılar - Diğer **kullanıcılar sayfasındaki** Daha fazla görüntüle düğmesine Microsoft 365 Uygulamaları tıklayın.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Microsoft 365 Uygulamaları raporunu yorumlama

Kullanıcılar ve Platform grafiklerine bakarak Microsoft 365 Uygulamaları etkinliklerini **görüntüebilirsiniz**.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Uygulamaları raporu.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

|Öğe|Açıklama|
 |:-----|:-----|
 |1. <br/> |Yeni **Microsoft 365 Uygulamaları raporu**, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için 2012'de 2013'te 2013'ü 2013'e kadar görüntüleyebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir. <br/> |
 |2. <br/> |Her raporda yer alan veriler genellikle son iki günü kapsar. Her altı günde bir, veri kalitesini sağlamak için raporu küçük güncelleştirmelerle yenileziz. <br/> |
 |3. <br/> |Kullanıcılar **görünümü** her uygulama için etkin kullanıcı sayısına (Outlook, Word, Excel, PowerPoint, OneNote ve diğer Teams. "Etkin kullanıcılar", bu uygulamalar içinde bilerek yapılan tüm eylemleri gerçekleştiren kullanıcılardır. <br/> |
 |4. <br/> |**Platformlar** görünümü her platform (Platformlar, Mac, Web ve Mobil Windows tüm uygulamalar genelinde etkin kullanıcıların eğilimini gösterir. <br/> |
 |5.<br/>|Kullanıcılar **grafiğinde** , Y ekseni ilgili uygulama için benzersiz etkin kullanıcıların sayısıdır.  **Platformschart'ta**  Y ekseni, ilgili platform için benzersiz kullanıcıların sayısıdır. Her iki grafikte de X ekseni, bir uygulamanın belli bir platformda kullanılan tarihtir.<br/>|
 6.<br/>|Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtrenin ekleyebilirsiniz. Örneğin, Kullanıcılar grafiğinde  Outlook ilgili bilgileri görmek için Outlook, Word, Excel, PowerPoint, OneDrive veya Teams'i seçin. Bu seçim değiştir değiştir değiştiriken, altındaki kılavuz tablosunda yer alan bilgiler değişmez.|
 |7.<br/>|Tablo, kullanıcı başına verilerin dökümünü gösterir. Tablodaki sütunları ekleyebilir veya kaldırabilirsiniz.  <br/><br/>**Kullanıcı** adı, etkinlik gerçekleştirilen kullanıcının e-posta adresidir Microsoft Apps.<br><br/>**Son etkinleştirme tarihi (UTC),** kullanıcının paylaşılan bilgisayarda Microsoft 365 Uygulamaları aboneliğini etkinleştirdikten sonra uygulamayı kendi hesabıyla başlatır olduğu en son tarihtir. <br/><br/>**Son etkinlik tarihi (UTC),** kullanıcı tarafından bilerek gerçekleştirilen son etkinlik tarihidir. Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.<br/><br/>Diğer sütunlar, seçilen dönemde kullanıcının o platformda (Microsoft 365 Uygulamaları içinde) etkin olup olduğunu gösterir. |
 |8.<br/>|Raporda **sütun eklemek veya** kaldırmak için Sütunları seç simgesini seçin.|
 |9.<br/>|Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit toplama, sıralama ve filtreleme gibi işlemlerde size olanak sağlar. 100'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtre uygulama. 100'den fazla kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.|
