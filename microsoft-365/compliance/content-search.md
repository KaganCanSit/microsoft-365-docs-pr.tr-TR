---
title: arama sonuçlarında İçerik araması oluşturma ve Microsoft 365 uyumluluk merkezi
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Uyumluluk merkezinde İçerik arama eBulma aracını kullanarak farklı Uyumluluk Hizmetleri'nde içerik Microsoft 365 kullanın.
ms.openlocfilehash: 68270466625cc5f9b76359ae7697536956c727aa
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021465"
---
# <a name="create-a-content-search"></a>İçerik araması oluşturma

Kuruluşta e-posta, belgeler ve anlık ileti konuşmaları Microsoft 365 uyumluluk merkezi yerinde içerik aramak için, İçerik arama eBulma aracını kullanabilirsiniz. Bu bulut tabanlı veri kaynaklarında içerik aramak için bu Microsoft 365 kullanın:
  
- Exchange Online kutularını geri alın

- SharePoint Online siteleri ve OneDrive İş hesapları

- Microsoft Teams

- Microsoft 365 Grupları

- Yammer Grupları

Siz bir arama çalıştırdikten sonra, içerik konumlarının sayısı ve tahmini arama sonucu sayısı arama uç sayfası üzerinde görüntülenir. Arama sorgusuyla en fazla öğeye sahip içerik konumları gibi istatistikleri hızla görüntüebilirsiniz. Bir arama çalıştırdikten sonra, sonuçların önizlemesini  önizler veya bunları yerel bir bilgisayara aktarabilirsiniz.

## <a name="before-you-run-a-search"></a>Arama çalıştırmadan önce

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi'ta</a> İçerik arama aracına erişmek için (aramaları çalıştırmak, sonuçları önizlemek ve sonuçları dışarı aktarmak için), bir yönetici, uyumluluk görevlisi veya eBulma Yöneticisi, kuruluşta eBulma Yöneticisi rol grubunun bir üyesi Microsoft 365 uyumluluk merkezi. Daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md).

- Karma Exchange dağıtımda, şirket içi posta kutularında arama yapmak için İçerik arama aracını kullanamalısınız. Aracı yalnızca bulut tabanlı posta kutularda arama yapmak için kullanabilirsiniz.

## <a name="create-and-run-a-search"></a>Arama oluşturma ve çalıştırma
  
1. <https://compliance.microsoft.com> Uygun izinlerin atandığı hesabın kimlik bilgilerini kullanarak gidip oturum açın.

2. Gezinti bölmesinin sol bölmesinde Microsoft 365 uyumluluk merkezi **arama'ya tıklayın**.

3. İçerik arama **sayfasında Yeni** **arama'ya tıklayın**.

4. Arama için bir ad yazın ve aramanızı tanımlamanıza yardımcı olacak isteğe bağlı bir açıklama yazın. Arama adı, kurum içinde benzersiz olmalıdır.

5. Konumlar  sayfasında, arama yapmak istediğiniz içerik konumlarını seçin. Posta kutularında, sitelerde ve ortak klasörlerde arama bulabilirsiniz.

    ![Yerinde tutacak içerik konumlarını seçin.](../media/ContentSearchLocations.png)
  
   1. **Exchange kutularını ayarlama**: Düğmeyi Açık olarak **ayarlayın** ve ardından posta kutularını yerinde tutmak için Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın. Ayrıca, Microsoft Ekibi ile ilişkilendirilmiş posta kutusunda (kanal iletileri için), Grup'Office 365 ve Grup Yammer de arayabilirsiniz. Posta kutularında depolanan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint:** Sitelerin ve hesapların yerinde basılı SharePoint belirtmek  için iki durum OneDrive  lu düğmeyi Açık SharePoint Siteleri seç'e tıklayın. Yerinde tutmak istediğiniz her sitenin URL'sini yazın. Ayrıca, bir Microsoft Team, SharePoint Veya Grup için sitenin URL'sini Office 365 da Yammer.
  
   3. **Exchange klasörleri ayarlama**: Exchange Online klasörünüzdeki tüm ortak klasörleri tutmak  için iki durumlu düğmeyi Açık olarak ayarlayın. Belirli ortak klasörlerin 9'da 9'da 11'inin 11'ini seçesiniz. Ortak klasörlerde  basılı tutmak istemiyorsanız iki durumlu düğmeyi kapalı bırakın.
  
   4. Şirket içi kullanıcıların içeriklerini aramak Teams bu onay kutusunu seçili durumda tut. Örneğin, kuruluşta Exchange posta kutularında arama yaptıysanız ve bu onay kutusu seçiliyse, şirket içi kullanıcıların Teams sohbet verilerini depolamak için kullanılan bulut tabanlı depolama alanı arama kapsamına dahil edilir. Daha fazla bilgi için [bkz. Teams kullanıcıların sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Arama **koşullarınızı tanımlayın sayfasında** bir anahtar sözcük sorgusu yazın ve gerekirse arama sorgusuna koşullar ekleyin.

   ![Arama sorgusunu yapılandırabilirsiniz.](../media/ContentSearchQuery.png)

   1. Gönderilen ve alınan tarihler gibi anahtar sözcükleri, ileti özelliklerini ya da dosya adları veya belgenin son değiştir olduğu tarih gibi belge özelliklerini belirtin. VE, YADA, NOT ve NEAR gibi Boole işleci kullanan daha **karmaşık** **sorgular** **kullanabilirsiniz**. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında yer alan tüm içerik arama sonuçlarına dahil edilir. Daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

   2. Alternatif olarak, Anahtar sözcük listesini **göster onay kutusuna** tıklar ve her satıra bir anahtar sözcük yazın. Bunu yaparsanız, her satırdaki anahtar sözcükler, oluşturulan arama sorgusunda **OR** işlecine benzeyen mantıksal bir işleçle (**c:s**) bağlantılıdır.

      Anahtar sözcük listesini neden kullanasınız? Her anahtar sözcükle kaç öğenin eş olduğunu göstermek için istatistikler eldeebilirsiniz. Bu, hangi anahtar sözcüklerin en etkili (ve en az) olduğunu hızla tanımlamanıza yardımcı olabilir. Satırda bir anahtar sözcük tümceciği de (parantez içinde) kullanabilirsiniz. Anahtar sözcük listesi ve arama istatistikleri hakkında daha fazla bilgi için bkz [. Aramalar için anahtar sözcük istatistiklerini al](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için, anahtar sözcük listesinde en çok 20 satırla sınırlandırabilirsiniz.

   3. Bir arama daraltmak ve daha daraltılmış bir sonuç kümesi geri dönmek için arama koşulları  eklersiniz. Her koşul, oluşturulan ve siz arama başlatmak üzere çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) VE işlecine benzer bir mantıksal işleç (**c:c**) tarafından **mantıksal olarak** bağlanır. Bu, öğelerin sonuçlara hem anahtar sözcük sorgusunu hem de bir veya daha fazla durumu karşılaması gereken anlamına gelir. Koşullar, sonuçlarınızı daraltmanıza böyle yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için bkz. [Arama koşulları](keyword-queries-and-search-conditions.md#search-conditions).

7. Arama ayarlarını gözden geçirebilirsiniz (ve gerekirse düzenleyin) ve ardından başlamak için aramanızı gönderin.
  
Bu içerik aramalarına yeniden erişmek veya İçerik arama sayfasında listelenen diğer içerik aramalarına **erişmek için,** arama'yı seçin ve Aç'a **tıklayın**.

## <a name="next-steps"></a>Sonraki adımlar

İçerik araması oluşturduk ve çalıştırdikten sonra gerçekleştirmeniz gereken sonraki adımların listesi burada ve ve şekildedir.

- [Arama sonuçlarını önizleme](preview-ediscovery-search-results.md)

- [Arama sonuçları istatistiklerini görüntüleme](view-keyword-statistics-for-content-search.md)

- [Arama sonuçlarını dışarı aktarma](export-search-results.md)

- [Arama raporunu dışarı aktarma](export-a-content-search-report.md)

## <a name="more-information"></a>Daha fazla bilgi

Farklı hizmetlerde içerik arama gibi İçerik arama hakkında daha fazla bilgi Microsoft 365, İçerik arama için [özellik başvurusu'ne bakın](content-search-reference.md).
