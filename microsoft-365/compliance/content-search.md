---
title: Microsoft Purview uyumluluk portalı İçerik araması oluşturma ve çalıştırma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Farklı Microsoft 365 hizmetlerindeki içeriği aramak için uyumluluk merkezindeki İçerik arama eBulma aracını kullanın.
ms.openlocfilehash: 3c5e4191c34db9d31ce54494f2677e75f3cae3bf
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632629"
---
# <a name="create-a-content-search"></a>İçerik araması oluşturma

Kuruluşunuzda e-posta, belgeler ve anlık ileti konuşmaları gibi yerinde içerik aramak için Microsoft Purview uyumluluk portalı İçerik arama eBulma aracını kullanabilirsiniz. Bu bulut tabanlı Microsoft 365 veri kaynaklarında içerik aramak için bu aracı kullanın:
  
- posta kutularını Exchange Online

- SharePoint Online siteleri ve OneDrive İş hesapları

- Microsoft Teams

- Microsoft 365 Grupları

- Yammer Grupları

Bir arama çalıştırdıktan sonra, arama açılır sayfasında içerik konumlarının sayısı ve tahmini arama sonuçları sayısı görüntülenir. Arama sorgusuyla eşleşen en çok öğeye sahip içerik konumları gibi istatistikleri hızla görüntüleyebilirsiniz. Bir arama çalıştırdıktan sonra sonuçların önizlemesini görebilir veya yerel bir bilgisayara aktarabilirsiniz.

## <a name="before-you-run-a-search"></a>Arama çalıştırmadan önce

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalında</a> İçerik arama aracına erişmek için (aramaları çalıştırmak ve sonuçları önizlemek ve sonuçları dışarı aktarmak için), yönetici, uyumluluk yetkilisi veya eBulma yöneticisinin uyumluluk portalındaki eBulma Yöneticisi rol grubunun üyesi olması gerekir. Daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

- Exchange karma dağıtımında, şirket içi posta kutularında e-postaları aramak için İçerik arama aracını kullanamazsınız. Aracı yalnızca bulut tabanlı posta kutularını aramak için kullanabilirsiniz.

- Exchange karma dağıtımında, şirket içi posta kutularında Teams sohbet verilerini arayabilirsiniz. Daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verileri](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

## <a name="create-and-run-a-search"></a>Arama oluşturma ve çalıştırma
  
1. <https://compliance.microsoft.com> Adresine gidin ve uygun izinlere atanmış bir hesabın kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **İçerik araması'na** tıklayın.

3. **İçerik arama** sayfasında **Yeni arama'ya** tıklayın.

4. Aramayı tanımlamaya yardımcı olan isteğe bağlı bir açıklama olan arama için bir ad yazın. Aramanın adı kuruluşunuzda benzersiz olmalıdır.

5. **Konumlar** sayfasında, aramak istediğiniz içerik konumlarını seçin. Posta kutuları, siteler ve ortak klasörlerde arama yapabilirsiniz.

    ![Ayrı tutulacak içerik konumlarını seçin.](../media/ContentSearchLocations.png)
  
   1. **Exchange posta kutuları: İki** durumlu düğmeyi **Açık** olarak ayarlayın ve ardından Beklemeye alınan posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri seçin'e** tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın. Microsoft Ekibi (kanal iletileri için), Office 365 Grubu ve Yammer Grubu ile ilişkili posta kutusunda da arama yapabilirsiniz. Posta kutularında depolanan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint siteleri**: İki durumlu düğmeyi **Açık** olarak ayarlayın ve ardından **Site seç'e** tıklayarak SharePoint sitelerini ve OneDrive hesaplarını beklemeye alacak şekilde belirtin. Beklemeye almak istediğiniz her sitenin URL'sini yazın. Microsoft Ekibi, Office 365 Grubu veya Yammer Grubu için SharePoint sitesinin URL'sini de ekleyebilirsiniz.
  
   3. **Ortak klasörleri değiştirme: Tüm ortak klasörleri** Exchange Online kuruluşunuzda beklemeye almak için iki durumlu düğmeyi **Açık** olarak ayarlayın. Beklemeye almak için belirli ortak klasörleri seçemezsiniz. Ortak klasörleri bekletmek istemiyorsanız iki durumlu düğmeyi kapalı bırakın.
  
   4. Şirket içi kullanıcılar için Teams içeriği aramak için bu onay kutusunu seçili tutun. Örneğin, kuruluştaki tüm Exchange posta kutularında arama yaparsanız ve bu onay kutusu seçiliyse, şirket içi kullanıcılar için Teams sohbet verilerini depolamak için kullanılan bulut tabanlı depolama alanı arama kapsamına eklenir. Daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

6. **Arama koşullarınızı tanımlayın** sayfasında bir anahtar sözcük sorgusu yazın ve gerekirse arama sorgusuna koşullar ekleyin.

   ![Arama sorgusunu yapılandırın.](../media/ContentSearchQuery.png)

   1. Anahtar sözcükleri, gönderilen ve alınan tarihler gibi ileti özelliklerini veya dosya adları veya belgenin son değiştirildiği tarih gibi belge özelliklerini belirtin. **AND**, **OR**, **NOT** ve **NEAR** gibi boole işleci kullanan daha karmaşık sorgular kullanabilirsiniz. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik arama sonuçlarına eklenir. Daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

   2. Alternatif olarak, **Anahtar sözcük listesini göster** onay kutusuna tıklayabilir ve her satıra bir anahtar sözcük yazabilirsiniz. Bunu yaparsanız, her satırdaki anahtar sözcükler, oluşturulan arama sorgusundaki **OR** işlecine benzer bir mantıksal işleç (**c:s**) ile bağlanır.

      Anahtar sözcük listesini neden kullanmalısınız? Her anahtar sözcükle eşleşen öğe sayısını gösteren istatistikler alabilirsiniz. Bu, hangi anahtar sözcüklerin en (ve en az) etkili olduğunu hızla belirlemenize yardımcı olabilir. Satır içinde bir anahtar sözcük tümceciği (parantez içinde) de kullanabilirsiniz. Anahtar sözcük listesi ve arama istatistikleri hakkında daha fazla bilgi için bkz. [Aramalar için anahtar sözcük istatistiklerini alma](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için anahtar sözcük listesinde en fazla 20 satırla sınırlısınız.

   3. Bir aramayı daraltmak ve daha iyileştirilmiş bir sonuç kümesi döndürmek için arama koşulları ekleyebilirsiniz. Her koşul, aramayı başlattığınızda oluşturulan ve çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul, **and** işlecine benzer bir mantıksal işleç (**c:c**) tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin sonuçlara dahil edilmesi için hem anahtar sözcük sorgusunu hem de bir veya daha fazla koşulu karşılaması gerektiğini gösterir. Koşulların sonuçlarınızı daraltmanıza bu şekilde yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için bkz [. Arama koşulları](keyword-queries-and-search-conditions.md#search-conditions).

7. Arama ayarlarını gözden geçirin (ve gerekirse düzenleyin) ve ardından başlatmak için aramayı gönderin.
  
Bu içerik aramasına yeniden erişmek veya **İçerik arama** sayfasında listelenen diğer içerik aramalarına erişmek için aramayı seçin ve **aç'a** tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

İçerik araması oluşturup çalıştırdıktan sonra gerçekleştirilecek sonraki adımların listesi aşağıdadır.

- [Arama sonuçlarını önizleme](preview-ediscovery-search-results.md)

- [Arama sonuçları için istatistikleri görüntüleme](view-keyword-statistics-for-content-search.md)

- [Arama sonuçlarını dışarı aktarma](export-search-results.md)

- [Bir arama raporunu dışa aktarma](export-a-content-search-report.md)

## <a name="more-information"></a>Daha fazla bilgi

farklı Microsoft 365 hizmetlerinde içerik arama gibi İçerik arama hakkında daha fazla bilgi için bkz. [İçerik araması için özellik başvurusu](content-search-reference.md).
