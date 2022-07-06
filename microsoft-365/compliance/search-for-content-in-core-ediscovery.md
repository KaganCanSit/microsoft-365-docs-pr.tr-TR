---
title: eBulma (Standart) durumunda içerik arama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: eBulma (Standart) olayıyla ilgili olabilecek içeriği arayın.
ms.openlocfilehash: 1c51475602e3a0807932501325e12d93a89fcba3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638135"
---
# <a name="search-for-content-in-a-ediscovery-standard-case"></a>eBulma (Standart) durumunda içerik arama

bir Microsoft Purview eKeşif (Standart) servis talebi oluşturulduktan ve servis talebiyle ilgili kişiler beklemeye alındıktan sonra, servis talebiyle ilgili içerik için bir veya daha fazla arama oluşturabilir ve çalıştırabilirsiniz. eBulma (Standart) servis talebiyle ilişkili aramalar, Microsoft Purview uyumluluk portalı **İçerik arama** sayfasında listelenmez. Bu aramalar, aramaların ilişkili olduğu eBulma (Standart) servis talebinin Aramalar **sayfasında listelenir** . Bu aynı zamanda bir servis talebiyle ilişkili aramalara yalnızca servis talebi üyeleri tarafından erişilebileceği anlamına gelir.

eBulma (Standart) araması oluşturmak için:
  
1. <https://compliance.microsoft.com> Adresine gidin ve uygun eBulma izinlerine atanmış ve servis talebinin bir üyesi olan kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Tümünü göster'e** tıklayın ve ardından **eBulma > Çekirdeği'ne** tıklayın.

3. **eBulma (Standart)** sayfasında, ilişkili arama oluşturmak istediğiniz servis talebini seçin ve ardından **Büyük/küçük harf aç'a** tıklayın.

4. Servis talebinin **Giriş** sayfasında **, Aramalar** sekmesine ve ardından **Yeni arama'ya** tıklayın.

   ![eBulma (Standart) arama araması oluşturmak için Yeni arama'ya tıklayın.](../media/CoreeDiscoverySearch1.png)

5. **Yeni arama** sihirbazında, arama için bir ad ve aramayı tanımlamaya yardımcı olacak isteğe bağlı bir açıklama yazın. Aramanın adı kuruluşunuzda benzersiz olmalıdır.

6. **Konumlar** sayfasında, aramak istediğiniz içerik konumlarını seçin. Posta kutuları, siteler ve ortak klasörlerde arama yapabilirsiniz.

    ![Ayrı tutulacak içerik konumlarını seçin.](../media/ContentSearchLocations.png)
  
   1. **Exchange posta kutuları: İki** durumlu düğmeyi **Açık** olarak ayarlayın ve ardından Beklemeye alınan posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri seçin'e** tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın (grup üyelerinin posta kutularına ayrı tutma yerleştirmek için). Microsoft Ekibi (kanal iletileri için), Office 365 Grubu ve Yammer Grubu ile ilişkili posta kutusunda da arama yapabilirsiniz. Posta kutularında depolanan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint siteleri**: İki durumlu düğmeyi **Açık** olarak ayarlayın ve ardından **Site seç'e** tıklayarak SharePoint sitelerini ve OneDrive hesaplarını beklemeye alacak şekilde belirtin. Beklemeye almak istediğiniz her sitenin URL'sini yazın. Microsoft Ekibi, Office 365 Grubu veya Yammer Grubu için SharePoint sitesinin URL'sini de ekleyebilirsiniz.
  
   3. **Ortak klasörleri değiştirme: Tüm ortak klasörleri** Exchange Online kuruluşunuzda beklemeye almak için iki durumlu düğmeyi **Açık** olarak ayarlayın. Beklemeye almak için belirli ortak klasörleri seçemezsiniz. Ortak klasörleri bekletmek istemiyorsanız iki durumlu düğmeyi kapalı bırakın.
  
   4. Şirket içi kullanıcılar için Teams içeriği aramak için bu onay kutusunu seçili tutun. Örneğin, kuruluştaki tüm Exchange posta kutularında arama yaparsanız ve bu onay kutusu seçiliyse, şirket içi kullanıcılar için Teams sohbet verilerini depolamak için kullanılan bulut tabanlı depolama alanı arama kapsamına eklenir. Daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

7. **Arama koşullarınızı tanımlayın** sayfasında bir anahtar sözcük sorgusu yazın ve gerekirse arama sorgusuna koşullar ekleyin.

   ![Arama sorgusunu yapılandırın.](../media/ContentSearchQuery.png)

   1. Anahtar sözcükleri, gönderilen ve alınan tarihler gibi ileti özelliklerini veya dosya adları veya belgenin son değiştirildiği tarih gibi belge özelliklerini belirtin. **AND**, **OR**, **NOT** ve **NEAR** gibi boole işleci kullanan daha karmaşık sorgular kullanabilirsiniz. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik arama sonuçlarına eklenir. Daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

   2. Alternatif olarak, **Anahtar sözcük listesini göster** onay kutusuna tıklayabilir ve her satıra bir anahtar sözcük yazabilirsiniz. Bunu yaparsanız, her satırdaki anahtar sözcükler, oluşturulan arama sorgusundaki **OR** işlecine benzer bir mantıksal işleç (**c:s**) ile bağlanır.

      Anahtar sözcük listesini neden kullanmalısınız? Her anahtar sözcükle eşleşen öğe sayısını gösteren istatistikler alabilirsiniz. Bu, hangi anahtar sözcüklerin en (ve en az) etkili olduğunu hızla belirlemenize yardımcı olabilir. Satır içinde bir anahtar sözcük tümceciği (parantez içinde) de kullanabilirsiniz. Anahtar sözcük listesi ve arama istatistikleri hakkında daha fazla bilgi için bkz. [Aramalar için anahtar sözcük istatistiklerini alma](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için anahtar sözcük listesinde en fazla 20 satırla sınırlısınız.

   3. Bir aramayı daraltmak ve daha iyileştirilmiş bir sonuç kümesi döndürmek için arama koşulları ekleyebilirsiniz. Her koşul, aramayı başlattığınızda oluşturulan ve çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul, **and** işlecine benzer bir mantıksal işleç (**c:c**) tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin sonuçlara dahil edilmesi için hem anahtar sözcük sorgusunu hem de bir veya daha fazla koşulu karşılaması gerektiğini gösterir. Koşulların sonuçlarınızı daraltmanıza bu şekilde yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için bkz [. Arama koşulları](keyword-queries-and-search-conditions.md#search-conditions).

8. Arama ayarlarını gözden geçirin (ve gerekirse düzenleyin) ve ardından başlatmak için aramayı gönderin.

Arama tamamlandıktan sonra arama sonuçlarının önizlemesini görebilirsiniz. Gerekirse, oluşturduğunuz aramayı görüntülemek için **Aramalar** sayfasında **Yenile'ye** tıklayın.

## <a name="more-information-about-searching-content-locations"></a>İçerik konumlarını arama hakkında daha fazla bilgi

- Aranacak posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri seçin'e** tıkladığınızda, görüntülenen posta kutusu seçicisi boş olur. Bu, performansı geliştirmek için tasarım gereğidir. Bu listeye alıcı eklemek için **Kullanıcı, grup veya ekip seç'e** tıklayın, arama kutusuna bir ad (en az üç karakter) yazın, adın yanındaki onay kutusunu seçin ve **seç'e** tıklayın.

- Etkin olmayan posta kutuları, Microsoft Teams, Yammer Grupları, Office 365 Grupları ve dağıtım gruplarını aranacak posta kutuları listesine ekleyebilirsiniz. Dinamik dağıtım grupları desteklenmez. Microsoft Teams, Yammer Grupları veya Office 365 Grupları eklerseniz, grup veya ekip posta kutusu aranır; grup üyelerinin posta kutuları aranz.

- Aramaya site eklemek için iki durumlu düğmeyi açın ve **ardından Site seç'e** tıklayın. Aramak istediğiniz her sitenin URL'sini yazın. Microsoft Ekibi, Yammer Grubu veya Office 365 Grubu için SharePoint sitesinin URL'sini de ekleyebilirsiniz.
