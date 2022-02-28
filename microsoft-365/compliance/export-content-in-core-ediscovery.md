---
title: Core eBulma durumundan içerik dışarı aktarma ve indirme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom: admindeeplinkCOMPLIANCE
description: Bu makalede, Core eKovery durumundan içerik dışarı ve Microsoft 365.
ms.openlocfilehash: 1d998a4b1eb540a1d96afc3acd3518d0c604a7e9
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990604"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>Core eKovery durumundan içerik dışarı aktarma

Core eKovery durumuyla ilişkilendirilmiş bir arama başarıyla çalıştırıldıktan sonra, arama sonuçlarını dışarı aktarın. Arama sonuçlarını dışarı aktarsanız da, posta kutusu öğeleri PST dosyalarına veya tek tek iletiler olarak indirilir. Site ve sitelerden içerik SharePoint OneDrive İş, yerel Office belge ve diğer belgelerin kopyaları dışarı aktarıldı. Dışarı Results.csv öğe hakkında bilgi içeren bir bildirim dosyası ve her arama sonucu hakkında bilgi içeren bir bildirim dosyası (XML biçiminde) de dışarı aktarıldı.
  
## <a name="export-search-results"></a>Arama sonuçlarını dışarı aktarma

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> ve uygun eBulma izinleri atanmış olan kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın.

2. Gezinti bölmesinin sol bölmesinde, **Microsoft 365 uyumluluk merkezi'i** seçin ve sonra **da eKbulma Puanı'ı** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**seçin**</a>.

3. **Core eDiscovery sayfasında**, ayrı tutma için oluşturmak istediğiniz vakanın adını tıklatın.

4. Vakanın  Giriş sayfasında Aramalar **sekmesine** tıklayın.

5. Açılır **sayfanın en** altındaki Eylemler menüsünde Sonuçları dışarı aktar'a **tıklayın**.

   ![Eylemler menüsünde sonuçları dışarı aktar seçeneği.](../media/ActionMenuExportResults.png)

   Core eKovery durumuyla ilişkilendirilmiş bir aramanın sonuçlarını dışarı aktarma iş akışı, İçerik arama sayfasındaki arama sonuçlarını dışarı **aktarmayla aynıdır** . Adım adım yönergeler için bkz. İçerik [arama sonuçlarını dışarı aktarma](export-search-results.md).

   > [!NOTE]
   > Arama sonuçlarını dışarı aktarsanız bile, aynı iletinin birden çok örneği arama yapılan posta kutularında bulunsa bile e-posta iletisi yalnızca bir kopyasının dışarı aktarılması için de-yinelemeyi etkinleştirme seçeneğiniz vardır. Yinelemeyi de-yineleme ve yinelenen öğelerin nasıl tanım olduğu hakkında daha fazla bilgi için bkz. [eBulma arama sonuçlarında yinelemeyi geri bulma](de-duplication-in-ediscovery-search-results.md).

   Dışarı aktarmayı başladıktan sonra arama sonuçları indirmeye hazır olur ve bu da Microsoft tarafından sağlanan bir Azure bulut Depolama bir konuma aktarıldıları anlamına gelir.
  
6. Dışarı **aktarma işlerinin** listesini görüntülemek için Durum'ta Dışarı Aktarmalar sekmesine tıklayın.
  
   ![Core eDiscovery durumundaki Dışarı Aktar sekmesinde işleri dışarı aktarın.](../media/CoreeDiscoveryExport.png)

   Oluşturduğunuz dışarı aktarma **işinin gösterirken** dışarı aktarma işleri listesini güncelleştirmek için Yenile'ye tıklamanız gerekir. Dışarı aktarma işleri, arama adının sonuna eklenen **adla _Export** aramayla aynıdır.

7. Dışarı aktarma sayfasında durum bilgilerini görüntülemek için oluşturduğunuz dışarı aktarma işini tıklatın. Bu bilgiler, Azure Veri Merkezi'ne aktarılan öğelerin Depolama içerir.

8. Tüm öğeler aktarıldıktan sonra, arama **sonuçlarını yerel** bilgisayarınıza indirmek için Sonuçları indir'e tıklayın. Arama sonuçlarını indirme hakkında daha fazla bilgi için İçerik arama sonuçlarını dışarı aktarma'daki 2[. Adım'a bakın](export-search-results.md#step-2-download-the-search-results).

> [!NOTE]
> Dışarı aktarılan arama sonuçlarının, siz dışarı aktarma işini oluşturduktan sonra 14 gün içinde indirilmiş olması gerekir.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Vakadan aramaları dışarı aktarma hakkında daha fazla bilgi

- Arama sonuçlarını dışarı aktararak dahil edilen dosyaları dışarı aktarma hakkında daha fazla bilgi için bkz [. İçerik arama raporunu dışarı aktarma](export-a-content-search-report.md#whats-included-in-the-report).

- Dışarı aktarmayı yeniden başlattıktan sonra, dışarı aktarma işinin yapılan arama sorgularında yapılan değişiklikler alınan arama sonuçlarını etkilemez. Dışarı aktarmayı yeniden başlattıktan sonra, dışarı aktarma işi oluşturulduğunda çalıştırılan aynı birleşik arama sorgusu işi yeniden çalıştırılacaktır.

- Ayrıca, dışarı aktarmayı yeniden başlattıktan sonra Azure Arama konumuna kopyalanan arama Depolama sonuçların üzerine yazılacaktır. Önceki kopyalanan sonuçlar indiril kullanılamaz.
