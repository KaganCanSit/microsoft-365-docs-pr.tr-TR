---
title: eBulma (Standart) servis talebine ait içeriği dışarı aktarma ve indirme
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
description: Microsoft 365'da eBulma (Standart) durumundan içerik dışarı aktarmayı ve indirmeyi açıklar.
ms.openlocfilehash: 2a63d22c8b4cb20e2c0f1317a8496e1cf517b2da
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995458"
---
# <a name="export-content-from-a-ediscovery-standard-case"></a>eBulma (Standart) durumundan içeriği dışarı aktarma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif (Standart) olayıyla ilişkilendirilmiş bir arama başarıyla çalıştırıldıktan sonra, arama sonuçlarını dışarı aktarabilirsiniz. Arama sonuçlarını dışarı aktardığınızda, posta kutusu öğeleri PST dosyalarına veya tek tek iletiler olarak indirilir. SharePoint ve OneDrive İş sitelerdeki içeriği dışarı aktardığınızda, yerel Office belgelerin ve diğer belgelerin kopyaları dışarı aktarılır. Dışarı aktarılan her öğe hakkında bilgi içeren bir Results.csv dosyası ve her arama sonucu hakkında bilgi içeren bir bildirim dosyası (XML biçiminde) de dışarı aktarılır.
  
## <a name="export-search-results"></a>Arama sonuçlarını dışarı aktarma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalına</a> gidin ve uygun eBulma izinlerine atanmış kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Tümünü göster'i** ve ardından **eBulma Çekirdeği'ni** >  seçin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. **eBulma (Standart)** sayfasında, ayrı tutmayı oluşturmak istediğiniz servis talebinin adına tıklayın.

4. Servis talebi için **Giriş** sayfasında **Aramalar** sekmesine tıklayın.

5. Açılır sayfanın alt kısmındaki **Eylemler** menüsünde **Sonuçları dışarı aktar'a** tıklayın.

   ![Eylemler menüsünde sonuçları dışarı aktar seçeneği.](../media/ActionMenuExportResults.png)

   eBulma (Standart) olayıyla ilişkili bir aramanın sonuçlarını dışarı aktarmak için kullanılan iş akışı, **İçerik arama** sayfasındaki arama sonuçlarını dışarı aktarmakla aynıdır. Adım adım yönergeler için bkz. [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md).

   > [!NOTE]
   > Arama sonuçlarını dışarı aktardığınızda, arama yapılan posta kutularında aynı iletinin birden çok örneği bulunsa bile e-posta iletisinin yalnızca bir kopyasının dışarı aktarılabilmesi için yinelenenleri kaldırmayı etkinleştirme seçeneğiniz vardır. Yinelenenleri kaldırma ve yinelenen öğeleri tanımlama hakkında daha fazla bilgi için bkz. [eBulma arama sonuçlarında](de-duplication-in-ediscovery-search-results.md) yinelenenleri kaldırma.

   Dışarı aktarma işlemine başladıktan sonra, arama sonuçları indirilmeye hazırlanır ve bu da Microsoft bulutunda Microsoft tarafından sağlanan bir Azure Depolama konumuna aktarıldığı anlamına gelir.
  
6. Dışarı aktarma işlerinin listesini görüntülemek için büyük/küçük harfe göre Dışarı **Aktarmalar** sekmesine tıklayın.
  
   ![eBulma (Standart) durumundaki Dışarı Aktar sekmesindeki dışarı aktarma işleri.](../media/CoreeDiscoveryExport.png)

   Dışarı aktarma işlerinin listesini oluşturduğunuz dışarı aktarma işini gösterecek şekilde güncelleştirmek için **Yenile'ye** tıklamanız gerekebilir. Dışarı aktarma işlerinin adı, arama adına **eklenmiş _Export** karşılık gelen aramayla aynı ada sahiptir.

7. Açılır sayfada durum bilgilerini görüntülemek için oluşturduğunuz dışarı aktarma işine tıklayın. Bu bilgiler, Azure Depolama konumuna aktarılan öğelerin yüzdesini içerir.

8. Tüm öğeler aktarıldıktan sonra sonuçları **indir'e** tıklayarak arama sonuçlarını yerel bilgisayarınıza indirin. Arama sonuçlarını indirme hakkında daha fazla bilgi için bkz. [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md#step-2-download-the-search-results) bölümündeki 2. Adım

> [!NOTE]
> Dışarı aktarılan arama sonuçları, dışarı aktarma işini oluşturduktan sonraki 14 gün içinde indirilmelidir.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Bir servis talebi aramalarını dışarı aktarma hakkında daha fazla bilgi

- Arama sonuçlarını dışarı aktarırken dahil edilen dışarı aktarma dosyaları hakkında daha fazla bilgi için bkz. [İçerik arama raporunu dışarı aktarma](export-a-content-search-report.md#whats-included-in-the-report).

- Dışarı aktarmayı yeniden başlatırsanız, dışarı aktarma işini oluşturan arama sorgularına yapılan değişiklikler alınan arama sonuçlarını etkilemez. Dışarı aktarmayı yeniden başlattığınızda, dışarı aktarma işi oluşturulduğunda çalıştırılan birleşik arama sorgusu işi yeniden çalıştırılır.

- Ayrıca dışarı aktarmayı yeniden başlatırsanız, Azure Depolama konumuna kopyalanan arama sonuçları önceki sonuçların üzerine yazar. Kopyalanan önceki sonuçlar indirilmeyecek.
