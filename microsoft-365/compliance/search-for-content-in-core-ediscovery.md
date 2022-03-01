---
title: Temel bir eBulma durumunda içerik arama
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
description: Çekirdek eBulma durumuyla ilgili olabilir içeriği arama.
ms.openlocfilehash: 57ea95458df568de3687e1b0d38a70991b09a850
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021461"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Core eKovery durumunda içerik arama

Temel bir eBulma durumu oluşturulduktan ve bu durumda ilgi alan kişiler ayrı tutularak, olayla ilgili bir veya birden çok içerik için arama oluşturabilir ve çalıştırabilirsiniz. Çekirdek eBulma durumuyla ilişkili aramalar, çalışma **sayfasındaki İçerik arama** Microsoft 365 uyumluluk merkezi. Bu aramalar, aramaların **ilişkilendirilen** Çekirdek eKbulma durumundaki Aramalar sayfasında listelenir. Bu aynı zamanda, bir vakayla ilişkilendirilmiş aramalara yalnızca vaka üyeleri tarafından erişil onun anlamına gelir.

Çekirdek eBulma araması oluşturmak için:
  
1. <https://compliance.microsoft.com> Uygun eBulma izinleri atanmış olan ve davanın bir üyesi olan kullanıcı hesabının kimlik bilgilerini kullanarak gidin ve oturum açın.

2. Bölmenin sol gezinti bölmesinde, **Microsoft 365 uyumluluk merkezi'e** tıklayın ve sonra **da Çekirdek'te eBulma > tıklayın**.

3. Core **eDiscovery sayfasında** , ilişkili arama oluşturmak istediğiniz vakayı seçin ve ardından Vakayı **aç'a tıklayın**.

4. Vakanın **Giriş** sayfasında Aramalar sekmesine **ve ardından Yeni** **arama'ya tıklayın**.

   ![Çekirdek eBulma arama araması oluşturmak için Yeni arama'ya tıklayın.](../media/CoreeDiscoverySearch1.png)

5. Yeni **arama sihirbazında** , arama için bir ad ve arama tanımlamaya yardımcı olacak isteğe bağlı bir açıklama yazın. Arama adı, kurum içinde benzersiz olmalıdır.

6. Konumlar  sayfasında, arama yapmak istediğiniz içerik konumlarını seçin. Posta kutularında, sitelerde ve ortak klasörlerde arama bulabilirsiniz.

    ![Yerinde tutacak içerik konumlarını seçin.](../media/ContentSearchLocations.png)
  
   1. **Exchange kutularını ayarlama**: Düğmeyi Açık olarak **ayarlayın** ve ardından posta kutularını yerinde tutmak için Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını (grup üyelerinin posta kutularını yerinde tutmak için) yerinde tutmak için arama kutusunu kullanın. Ayrıca, Microsoft Ekibi ile ilişkilendirilmiş posta kutusunda (kanal iletileri için), Grup'Office 365 ve Grup Yammer de arayabilirsiniz. Posta kutularında depolanan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint:** Sitelerin ve hesapların yerinde basılı SharePoint belirtmek  için iki durum OneDrive  lu düğmeyi Açık SharePoint Siteleri seç'e tıklayın. Yerinde tutmak istediğiniz her sitenin URL'sini yazın. Ayrıca, bir Microsoft Team, SharePoint Veya Grup için sitenin URL'sini Office 365 da Yammer.
  
   3. **Exchange klasörleri ayarlama**: Exchange Online klasörünüzdeki tüm ortak klasörleri tutmak  için iki durumlu düğmeyi Açık olarak ayarlayın. Belirli ortak klasörlerin 9'da 9'da 11'inin 11'ini seçesiniz. Ortak klasörlerde  basılı tutmak istemiyorsanız iki durumlu düğmeyi kapalı bırakın.
  
   4. Şirket içi kullanıcıların içeriklerini aramak Teams bu onay kutusunu seçili durumda tut. Örneğin, kuruluşta Exchange posta kutularında arama yaptıysanız ve bu onay kutusu seçiliyse, şirket içi kullanıcıların Teams sohbet verilerini depolamak için kullanılan bulut tabanlı depolama alanı arama kapsamına dahil edilir. Daha fazla bilgi için [bkz. Teams kullanıcıların sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

7. Arama **koşullarınızı tanımlayın sayfasında** bir anahtar sözcük sorgusu yazın ve gerekirse arama sorgusuna koşullar ekleyin.

   ![Arama sorgusunu yapılandırabilirsiniz.](../media/ContentSearchQuery.png)

   1. Gönderilen ve alınan tarihler gibi anahtar sözcükleri, ileti özelliklerini ya da dosya adları veya belgenin son değiştir olduğu tarih gibi belge özelliklerini belirtin. VE, YADA, NOT ve NEAR gibi Boole işleci kullanan daha **karmaşık** **sorgular** **kullanabilirsiniz**. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında yer alan tüm içerik arama sonuçlarına dahil edilir. Daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

   2. Alternatif olarak, Anahtar sözcük listesini **göster onay kutusuna** tıklar ve her satıra bir anahtar sözcük yazın. Bunu yaparsanız, her satırdaki anahtar sözcükler, oluşturulan arama sorgusunda **OR** işlecine benzeyen mantıksal bir işleçle (**c:s**) bağlantılıdır.

      Anahtar sözcük listesini neden kullanasınız? Her anahtar sözcükle kaç öğenin eş olduğunu göstermek için istatistikler eldeebilirsiniz. Bu, hangi anahtar sözcüklerin en etkili (ve en az) olduğunu hızla tanımlamanıza yardımcı olabilir. Satırda bir anahtar sözcük tümceciği de (parantez içinde) kullanabilirsiniz. Anahtar sözcük listesi ve arama istatistikleri hakkında daha fazla bilgi için bkz [. Aramalar için anahtar sözcük istatistiklerini al](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için, anahtar sözcük listesinde en çok 20 satırla sınırlandırabilirsiniz.

   3. Bir arama daraltmak ve daha daraltılmış bir sonuç kümesi geri dönmek için arama koşulları  eklersiniz. Her koşul, oluşturulan ve siz arama başlatmak üzere çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) VE işlecine benzer bir mantıksal işleç (**c:c**) tarafından **mantıksal olarak** bağlanır. Bu, öğelerin sonuçlara hem anahtar sözcük sorgusunu hem de bir veya daha fazla durumu karşılaması gereken anlamına gelir. Koşullar, sonuçlarınızı daraltmanıza böyle yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için bkz. [Arama koşulları](keyword-queries-and-search-conditions.md#search-conditions).

8. Arama ayarlarını gözden geçirebilirsiniz (ve gerekirse düzenleyin) ve ardından başlamak için aramanızı gönderin.

Arama tamamlandıktan sonra, arama sonuçlarının önizlemesini görüntü görebilirsiniz. Gerekirse, oluşturduğunuz **aramanın** **görüntülenmesi için** Aramalar sayfasında Yenile'ye tıklayın.

## <a name="more-information-about-searching-content-locations"></a>İçerik konumlarını arama hakkında daha fazla bilgi

- Aranecek posta **kutularını belirtmek için Kullanıcıları,** grupları veya ekipleri seç'e tıklarken görüntülenen posta kutusu seçici boş olur. Bu, performansı geliştirmek için tasarımdandır. Bu listeye alıcı eklemek için Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın, arama kutusuna bir ad yazın (en az üç karakter uzunluğunda) ve adın yanındaki onay kutusunu seçin ve ardından Seç'e **tıklayın**.

- Etkin olmayan posta kutularını, posta Microsoft Teams, Yammer Grupları, Office 365 Grupları ve dağıtım gruplarını aray yer alan posta kutuları listesine ekleyebilirsiniz. Dinamik dağıtım grupları destek desteklemez. Grup Microsoft Teams, Yammer Gruplar veya Office 365 eklersanız, grup veya ekip posta kutusunda arama olur; grup üyelerinin posta kutularında arama yoktur.

- Aramaya site eklemek için, iki durumlu düğmeyi açıp Siteleri **seç'e tıklayın**. Aramak istediğiniz her sitenin URL'sini yazın. Ayrıca bir Microsoft Team, SharePoint Grubu veya Yammer Grubu için sitenin URL'sini Office 365.
