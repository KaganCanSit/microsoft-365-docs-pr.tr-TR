---
title: eBulma'da iş akışını Teams (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: eBulma'da (Premium) Microsoft Teams içeriği korumayı, toplamayı, gözden geçirmeyi ve dışarı aktarmayı öğrenin.
ms.openlocfilehash: 043cfb070c008b4c58e48df40dfbb069ca859edd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972397"
---
# <a name="ediscovery-premium-workflow-for-content-in-microsoft-teams"></a>Microsoft Teams içeriği için eBulma (Premium) iş akışı

Bu makalede, Microsoft Teams içeriğini korumak, toplamak, gözden geçirmek ve dışarı aktarmak için Microsoft Purview eKeşif 'i (Premium) kullanmaya yönelik kapsamlı yordamlar, yönergeler ve en iyi yöntemler kümesi sağlanır. Bu makalenin amacı, eBulma iş akışınızı Teams içerik için iyileştirmenize yardımcı olmaktır.

eBulma (Premium) kullanarak toplayabileceğiniz ve işleyebileceğiniz beş Teams içerik kategorisi vardır:

- **Teams 1:1 sohbetleri**. İki kişi arasındaki Teams konuşmada paylaşılan sohbet iletileri, gönderiler ve ekler.  Teams 1:1 sohbetleri *konuşma olarak da* adlandırılır.

- **Grup sohbetlerini Teams**. Üç veya daha fazla kişi arasındaki Teams konuşmada paylaşılan sohbet iletileri, gönderiler ve ekler. *1:N* sohbetleri veya *grup konuşmaları* olarak da adlandırılır.

- **Teams kanalları**. Standart bir Teams kanalında paylaşılan sohbet iletileri, gönderiler, yanıtlar ve ekler.

- **Özel kanallar**. Özel bir Teams kanalında paylaşılan ileti gönderileri, yanıtlar ve ekler.

- **Paylaşılan kanallar**. Paylaşılan bir Teams kanalında paylaşılan ileti gönderileri, yanıtlar ve ekler.

## <a name="where-teams-content-is-stored"></a>Teams içeriğinin depolandığı yer

eBulma'da (Premium) Teams içeriği yönetmenin önkoşullarından biri, eBulma'da (Premium) toplayabileceğiniz, işleyebileceğiniz ve gözden geçirebileceğiniz Teams içeriğinin türünü ve bu içeriğin Microsoft 365 nerede depolandığını anlamaktır. Aşağıdaki tabloda Teams içerik türü ve bunların depolandığı yer listeleniyor.

|&nbsp;|Sohbet iletilerinin ve gönderilerinin konumu|Dosyaların ve eklerin konumu|
|---|---|---|
|Teams 1:1 sohbetleri|1:1 sohbetlerindeki iletiler, tüm sohbet katılımcılarının Exchange Online posta kutusunda depolanır.|1:1 sohbetinde paylaşılan dosyalar, dosyayı paylaşan kişinin OneDrive İş hesabında depolanır.|
|Grup sohbetlerini Teams|Grup sohbetlerindeki iletiler, tüm sohbet katılımcılarının Exchange Online posta kutusunda depolanır.|Grup sohbetlerinde paylaşılan dosyalar, dosyayı paylaşan kişinin OneDrive İş hesabında depolanır.|
|kanalları Teams|Tüm kanal iletileri ve gönderileri, ekiple ilişkilendirilmiş Exchange Online posta kutusunda depolanır.|Kanalda paylaşılan dosyalar, ekiple ilişkilendirilmiş SharePoint Online sitesinde depolanır.|
|Özel kanallar|Özel kanalda gönderilen iletiler, özel kanalın tüm üyelerinin Exchange Online posta kutularında depolanır.|Özel kanalda paylaşılan dosyalar, özel kanalla ilişkilendirilmiş ayrılmış bir SharePoint Online sitesinde depolanır.|
|Paylaşılan kanallar|Paylaşılan kanalda gönderilen iletiler, paylaşılan kanalla ilişkilendirilmiş bir sistem posta kutusunda depolanır. <sup>1</sup>|Paylaşılan kanalda paylaşılan dosyalar, paylaşılan kanalla ilişkilendirilmiş ayrılmış bir SharePoint Çevrimiçi sitesinde depolanır.|

> [!NOTE]
> <sup>1</sup> Paylaşılan bir kanalda gönderilen iletileri aramak (ve korumak) için üst Ekip için Exchange Online posta kutusunu aramanız veya belirtmeniz gerekir.

## <a name="create-a-case-for-teams-content"></a>Teams içerik için servis talebi oluşturma

eBulma'da (Premium) Teams içeriği yönetmenin ilk adımı, Teams içeriği yönetmek için iyileştirilmiş yeni servis talebi biçimini kullanarak bir servis talebi oluşturmaktır. Teams içerik için yeni büyük/küçük harf biçimini kullanmanın avantajları şunlardır:

- Aynı konuşmada yanıt veren öğeler içeren ek iletilerin otomatik olarak toplandığı ve gözden geçirme kümelerine eklendiği konuşma yazışması desteği.

- Teams sohbet konuşmaları otomatik olarak gözden geçirme kümelerine HTML transkript dosyası olarak eklenir. Konuşmalarda paylaşılan bulut ekleri de gözden geçirme kümesine eklenir. Bu, yanıt veren öğelerle konuşmalara bağlam sağlamaya ve sohbet tabanlı içerik tarafından üretilen toplam öğe sayısını azaltmaya yardımcı olur.

- Gözden geçirme kümelerine 1 TB'a kadar olan koleksiyonlar eklenebilir ve bu da büyük miktarlarda Teams içeriği toplamanıza olanak sağlar.

Artan büyük/küçük harf sınırları hakkında daha fazla bilgi için bkz. [eBulma'da yeni servis talebi biçimini kullanma (Premium)](advanced-ediscovery-new-case-format.md).

Servis talebi oluşturmak için:

1. <https://compliance.microsoft.com> adresine gidin ve oturum açın.

2. Microsoft Purview uyumluluk portalının sol gezinti bölmesinde **gelişmiş > eBulma'ya** tıklayın.

3. **eBulma (Premium)** sayfasında **Servis Talepleri** sekmesine ve ardından **Servis talebi oluştur'a** tıklayın.

   **Yeni eBulma servis talebi** açılır sayfası görüntülenir. **Olay biçimi** bölümü, yeni büyük/küçük harf biçimini kullanarak servis talebi oluşturma seçeneği sağlar.

   ![Yeni eBulma servis talebi sayfasındaki büyük harf seçeneği.](..\media\AeDNewCaseFormat1.png)

4. Olayı adlandırdıktan sonra **, Yeni** seçeneğini belirleyin ve ardından Büyük/küçük harf oluşturmak için **Kaydet'e** tıklayın.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Teams koruyucu veri kaynakları ekleme ve Teams içeriği koruma  

Sonraki adım, araştırmanızdaki veri koruyucuları olan kullanıcıları belirlemek ve bunları ve içerik konumlarını önceki bölümde oluşturduğunuz davaya koruyucu olarak eklemektir. Koruyucu eklediğinizde, posta kutularını ve OneDrive hesabını koruyucu veri kaynakları olarak belirtebilirsiniz. Ayrıca Teams içerik konumlarını koruyucu veri kaynakları olarak belirterek bu konumları araştırmanız sırasında içeriği korumak üzere yasal saklamaya hızlıca yerleştirebilirsiniz. Ayrıca içerik toplamayı ve bir gözden geçirme kümesine eklemeyi de kolaylaştırır.

Bir olaya koruyucu eklemek ve koruyucu veri kaynaklarını korumak için:

1. Önceki bölümde oluşturduğunuz eBulma (Premium) olayına gidin ve **Veri kaynakları'na** tıklayın.

2. **Veri kaynakları** sayfasında **Veri kaynağı** >  **ekleYeni koruyucu ekle'ye** tıklayın.

3. **Yeni koruyucu** sihirbazında, kullanıcı adının veya diğer adının ilk bölümünü yazarak bir veya daha fazla kullanıcıyı servis talebine koruyucu olarak ekleyin. Doğru kişiyi buldukta adını seçerek listeye ekleyin.  

4. Koruyucuyla otomatik olarak ilişkilendirilen birincil veri kaynaklarını görüntülemek ve koruyucuyla ilişkilendirilecek diğer konumları seçmek için her koruyucuyu genişletin.

   ![Koruyucu veri kaynakları.](..\media\TeamsCustodialDataLocations1.png)

5. Teams içerik için koruyucu veri kaynakları eklemek için bu yönergeleri izleyin. Veri konumu eklemek için **Düzenle'ye** tıklayın.

   - **Posta kutuları**. Koruyucunun posta kutusu varsayılan olarak seçilidir. 1:1 sohbetleri, grup sohbetlerini ve özel kanal sohbetlerini koruyucu veriler olarak eklemek (ve korumak) için bunu seçili tutun.

   - **OneDrive'lar**. Koruyucunun OneDrive hesabı varsayılan olarak seçilidir. 1:1 sohbetlerinde ve grup sohbetlerinde paylaşılan dosyaları koruyucu veriler olarak eklemek (ve korumak) için bunu seçili tutun.

   - **SharePoint**. Bir kanalda paylaşılan dosyaların koruyucu veriler olarak eklenmesi (ve korunması) için, koruyucunun üyesi olduğu herhangi bir özel veya paylaşılan kanalla ilişkilendirilmiş SharePoint sitesini ekleyin. **Düzenle'ye** tıklayın ve özel veya paylaşılan bir kanalla ilişkilendirilmiş SharePoint sitesinin URL'sini ekleyin. Kullanıcının üyesi olduğu özel ve paylaşılan kanalları nasıl bulacağınızı öğrenmek için bkz. [Özel ve paylaşılan kanalları bulma](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

   - **Teams**. Koruyucunun üyesi olduğu ekipleri, tüm kanal iletilerini ve bir Teams kanalına paylaşılan tüm dosyaları gözetim verileri olarak eklemek (ve korumak) için ekleyin. Bu, koruyucunun üyesi olduğu paylaşılan bir kanalın üst ekibi için posta kutusu eklemeyi içerir. **Düzenle'ye** tıkladığınızda, koruyucunun üyesi olduğu her ekiple ilişkili posta kutusu ve site listede görüntülenir. Koruyucuyla ilişkilendirmek istediğiniz ekipleri seçin. Her ekip için ilgili posta kutusunu ve siteyi seçmeniz gerekir.

   > [!NOTE]
   > Ayrıca, koruyucuların üyesi Teams posta kutusunu ve sitesini koruyucu veri konumu olarak ekleyebilirsiniz. Bunu yapmak için **Exchange** ve **SharePoint** yanındaki **Düzenle'ye** tıklayıp ekiple ilişkili posta kutusunu ve siteyi eklersiniz.

6. Koruyucuları ekledikten ve koruyucu veri kaynaklarını yapılandırdıktan sonra, **Tutma ayarları** sayfasını görüntülemek için **İleri'ye** tıklayın.

   Koruyucuların listesi görüntülenir ve **Ayrı Tut** sütunundaki onay kutusu varsayılan olarak seçilidir. Bu, her bir koruyucuyla ilişkilendirdiğiniz veri kaynaklarına bir ayrı tutma uygulanacağını gösteriyordu. Bu verileri korumak için bu onay kutularını seçili bırakın.

7. **Saklama ayarları** sayfasında, koruyucu ayarlarını gözden geçirmek için **İleri'ye** tıklayın. Servis talebine koruyucuları eklemek için **Gönder'e** tıklayın.

eBulma (Premium) durumunda veri kaynaklarını ekleme ve koruma hakkında daha fazla bilgi için bkz:

- [eBulma (Premium) olayına koruyucu ekleme](add-custodians-to-case.md)

- [eBulma (Premium) olayına gözetimsiz veri kaynakları ekleme](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Teams içerik toplama ve gözden geçirme kümesine ekleme

Olaya koruyucuları ekledikten ve koruyucu veri kaynaklarında içeriği korudikten sonra, iş akışının bir sonraki adımı araştırmanızla ilgili Teams içeriği aramak ve daha fazla inceleme ve analiz için bir gözden geçirme kümesine eklemektir. Exchange e-posta ve SharePoint'daki belgeler gibi diğer Microsoft 365 hizmetlerden içerikle birlikte Teams içerik toplamak normal olsa da, bu bölüm özellikle bir koleksiyonda Teams içerik toplamaya odaklanır. Gözden geçirme kümesine eklemek için Teams olmayan içerik toplayan ek koleksiyonlar oluşturabilirsiniz.

Bir servis talebi için Teams içerik topladığınızda, iş akışında iki adım vardır:

1. **Taslak koleksiyon oluşturma**.  İlk adım, arama ölçütlerinizle eşleşen öğelerin tahmini olan bir *taslak koleksiyonu* oluşturmaktır. Bulunan öğelerin toplam sayısı ve boyutu, bulundukları farklı veri kaynakları ve arama sorgusuyla ilgili istatistikler gibi arama sorgusuyla eşleşen sonuçlar hakkındaki bilgileri görüntüleyebilirsiniz. Koleksiyon tarafından döndürülen öğelerin bir örneğini de önizleyebilirsiniz. Bu istatistikleri kullanarak arama sorgusunu değiştirebilir ve taslak koleksiyonu gerektiği kadar yeniden çalıştırarak, olayınızla ilgili içeriği topladığınıza memnun kalana kadar sonuçları daraltabilirsiniz.

2. **Taslak koleksiyonu gözden geçirme kümesine işleme**. Taslak koleksiyonun sonuçlarından memnun olduktan sonra, koleksiyonu bir gözden geçirme kümesine işleyebilirsiniz. Bir taslak koleksiyonu işlediğiniz zaman, koleksiyon tarafından döndürülen öğeler gözden geçirme, analiz ve dışarı aktarma için bir gözden geçirme kümesine eklenir.

Ayrıca, bir taslak koleksiyonu çalıştırmama ve koleksiyonu oluşturup çalıştırdığınızda koleksiyon sonuçlarını doğrudan bir gözden geçirme kümesine ekleme seçeneğiniz vardır.

Teams içerik koleksiyonu oluşturmak için:

1. Önceki bölümde koruyucuları eklediğiniz eBulma (Premium) olayına gidin ve **Koleksiyonlar'a** tıklayın.

2. **Koleksiyonlar** sayfasında Yeni **koleksiyonStandard koleksiyonu'nu** >  seçin.

3. Koleksiyon için bir ad (gerekli) ve açıklama (isteğe bağlı) yazın.

4. **Koruyucu veri kaynakları** sayfasında, olaya eklediğiniz **koruyucuları seçmek için Koruyucuları seç'e** tıklayın.

   Olay koruyucularının listesi, **Koruyucuları seçin** açılır sayfasında görüntülenir.

5. Bir veya daha fazla koruyucu seçin ve **ekle'ye** tıklayın.

   Koleksiyona belirli koruyucular ekledikten sonra, her koruyucu için belirli veri kaynaklarının listesi görüntülenir. Bunlar, olaya koruyucu eklerken yapılandırdığınız veri kaynaklarıdır. Tüm koruyucu veri kaynakları varsayılan olarak seçilir. Bu, bir koruyucuyla ilişkilendirdiğiniz tüm Teams veya kanalları içerir.

   Teams içerik toplarken aşağıdakilerin yapılması önerilir:

   - Koruyucuların OneDrive hesaplarını koleksiyon kapsamından kaldırın (her koruyucu için **Koruyucunun OneDrive** sütunundaki onay kutusunun seçimini kaldırarak). Bu, 1:1 sohbetlerine ve grup sohbetlerine eklenmiş yinelenen dosyaların toplanmasını engeller. Taslak koleksiyonu gözden geçirme kümesine kaydettiğinizde, koleksiyonda bulunan her konuşmadan bulut ekleri otomatik olarak toplanır. Bu yöntem kullanılarak (koleksiyonun bir parçası olarak OneDrive hesapları aramak yerine), 1:1'e eklenen dosyalar ve grup sohbetleri paylaşıldıkları konuşmada gruplandırılır.

   - Özel veya paylaşılan kanallarda paylaşılan dosyaları içeren SharePoint sitelerini kaldırmak için **Ek site** sütunundaki onay kutusunun seçimini kaldırın. Bunun yapılması, özel veya paylaşılan kanal konuşmalarına eklenmiş yinelenen dosyaların toplanmasını ortadan kaldırır çünkü bu bulut ekleri taslak koleksiyonu işlediğinizde gözden geçirme kümesine otomatik olarak eklenir ve paylaşıldıkları konuşmalarda gruplandırılır.

6. Daha önce Teams içeriği koruyucu veri kaynakları olarak ekleme adımlarını izlediyseniz, bu adımı atlayabilir ve **İleri'yi** seçebilirsiniz. Aksi takdirde, **Gözetimsiz veri kaynakları** sihirbazı sayfasında, koleksiyonda arama yapmak için büyük/küçük harfe eklemiş olabileceğiniz Teams içerik içeren gözetimsiz veri kaynaklarını seçebilirsiniz.

7. Daha önce Teams içeriği koruyucu veri kaynakları olarak ekleme adımlarını izlediyseniz, bu adımı atlayabilir ve **İleri'yi** seçebilirsiniz. Aksi takdirde, **Ek konumlar** sihirbazı sayfasında, koleksiyonda arama yapmak için başka veri kaynakları ekleyebilirsiniz. Örneğin, bir ekip için posta kutusunu ve siteyi, gözetim veya gözetim dışı veri kaynağı olarak eklenmemiş bir ekip için ekleyebilirsiniz. Aksi takdirde **İleri'yi** seçin ve bu adımı atlayın.

8. **Koşullar** sihirbazı sayfasında, arama sorgusunu önceki sihirbaz sayfalarında belirttiğiniz veri kaynaklarından Teams içerik toplayacak şekilde yapılandırın. Koleksiyonun kapsamını daraltmak için çeşitli anahtar sözcükler ve arama koşulları kullanabilirsiniz. Daha fazla bilgi için bkz. [Koleksiyonlar için arama sorguları oluşturma](building-search-queries.md).

   Teams sohbet konuşmalarının (1:1, grup ve kanal sohbetleri dahil) en kapsamlı koleksiyonunu sağlamaya yardımcı olmak için **Tür** koşulunu kullanın ve **Anlık iletiler** seçeneğini belirleyin. Ayrıca, koleksiyonun kapsamını araştırmanızla ilgili öğelere daraltmak için bir tarih aralığı veya birkaç anahtar sözcük de eklemenizi öneririz. **Tür** ve **Tarih** seçeneklerini kullanan örnek sorgunun ekran görüntüsü aşağıda verilmiştir:

   ![Teams içerik toplamak için sorgu.](..\media\TeamsConditionsQueryType.png)

9. **Taslağı kaydet veya topla** sihirbazı sayfasında, taslak koleksiyonu oluşturmak mı yoksa koleksiyonu gözden geçirme kümesine işlemek mi istediğinize bağlı olarak aşağıdakilerden birini yapın.

   ![Taslak koleksiyonu veya işleme koleksiyonunu kaydedin.](..\media\TeamsDraftCommitCollection.png)

   1. **Koleksiyonu taslak olarak kaydedin**. Taslak koleksiyon oluşturmak için bu seçeneği belirleyin. Daha önce açıklandığı gibi taslak koleksiyon, koleksiyon sonuçlarını gözden geçirme kümesine eklemez. Koleksiyon kapsamındaki veri kaynakları için arama sorgusuyla eşleşen arama sonuçlarının tahminini döndürür. Bu size [koleksiyon istatistiklerini ve raporlarını [(collection-statistics-reports.md)] görüntüleme ve taslak koleksiyonu düzenleme ve yeniden çalıştırma fırsatı verir. Taslak koleksiyonun sonucundan memnun olduğunuzda, bunu bir gözden geçirme kümesine işleyebilirsiniz. Daha fazla bilgi için bkz. [Taslak koleksiyonu oluşturma](create-draft-collection.md).

   2. **Öğeleri toplayın ve bir gözden geçirme kümesine ekleyin**. Koleksiyonu çalıştırmak ve sonuçları gözden geçirme kümesine eklemek için bu seçeneği belirleyin. Koleksiyonu yeni veya mevcut bir gözden geçirme kümesine ekleyebilirsiniz. Bağlamsal Teams konuşma iletilerini (*konuşma yazışması* olarak da adlandırılır) toplama ve bulut eklerini toplama seçenekleri varsayılan olarak seçilidir ve seçilemez. Bu seçenekler, Teams içerik için servis talebini ilk oluşturduğunuzda kullandığınız yeni büyük/küçük harf biçimi nedeniyle otomatik olarak uygulanır. Koleksiyonları bir gözden geçirme kümesine işleme hakkında daha fazla bilgi için bkz. Taslak [koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md).

10. Koleksiyonu yapılandırmayı tamamladıktan sonra, taslak koleksiyon oluşturmak veya öğeleri toplamak için koleksiyonu gönderin ve bunları bir gözden geçirme kümesine ekleyin.

   Koleksiyonu gözden geçirme kümesine ekleme işlemi tamamlandığında **Koleksiyonlar** sekmesinde koleksiyonun durum değeri **Kabul Edilen** olarak ayarlanır.

## <a name="review-teams-content-in-a-review-set"></a>Gözden geçirme kümesindeki Teams içeriği gözden geçirme

bir gözden geçirme kümesine Teams içerik koleksiyonları ekledikten sonra, sonraki adım içeriği araştırmanızla ilgisi için gözden geçirmek ve gerekirse iptal etmektir. Teams içeriği gözden geçirmenin önemli önkoşullarından biri, eBulma'nın (Premium) bir gözden geçirme kümesine eklerken sohbet konuşmalarını ve eklerini Teams nasıl işlediğini anlamaktır. Teams içeriğinin işlenmesi aşağıdaki üç şeye neden olur:

- **[Gruplandırma](#grouping)**. konuşmaların Teams iletilerin, gönderilerin ve yanıtların birlikte gruplandırılıp gözden geçirme kümesinde sunulması. Ayrıca sohbet konuşmalarındaki eklerin ayıklanması ve konuşma içinde gruplanması da buna dahildir.

- **[Transkript konuşma yazışması](#transcript-conversation-threading)**. eBulma (Premium), toplama ölçütleriyle eşleşen öğelerle ilgili bağlam sağlamak için bir konuşmadan hangi ek içeriğin toplandığını nasıl belirler?

- **[Yinelenenleri kaldırma](#deduplication-of-teams-content)**. eBulma (Premium) yinelenen Teams içeriğini nasıl işler?

- **[Meta veriler](#metadata-for-teams-content)**. eBulma'nın (Premium) toplanıp bir gözden geçirme kümesine eklendikten sonra Teams içeriğe eklediği meta veri özellikleri.

Gruplandırma, konuşma yazışması oluşturma, yinelenenleri kaldırma ve Teams meta verilerini anlamak, Teams içeriğinin gözden geçirilmesini ve analizini iyileştirmenize yardımcı olur. Bu bölümde, [bir inceleme kümesindeki Teams içeriği görüntülemeye yönelik ipuçları da bulunur](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Grup -landırma

Teams sohbet konuşmalarındaki içerik bir gözden geçirme kümesine eklendiğinde, konuşmalardan gelen iletiler, gönderiler ve yanıtlar HTML transkript dosyalarında toplanır. Tek bir sohbet konuşması birden çok transkript dosyası içerebilir. Bu transkript dosyalarının önemli bir işlevi, Teams içeriği tek tek (veya ayrı) iletiler olarak değil sürekli konuşmalar olarak sunmaktır. Bu, önceki adımda koleksiyonlarınızın arama ölçütleriyle eşleşen öğeler için bağlam sağlamaya ve gözden geçirme kümesinde toplanan öğe sayısını azaltmaya yardımcı olur. Transkriptler ve ilişkili öğeler *aileye* veya *konuşmaya* göre gruplandırılabilir. Aynı ailedeki öğeler **FamilyId** meta veri özelliği için aynı değere sahip olacaktır. Aynı konuşmadaki öğeler **, ConversationId** meta veri özelliği için aynı değere sahip olur.

Aşağıdaki tabloda, farklı türlerdeki Teams sohbet içeriğinin aile ve konuşmaya göre nasıl gruplandırıldığı açıklanmaktadır.

|İçerik türünü Teams|Aileye göre gruplandır|Konuşmaya göre gruplandırma|
|---|---|---|
|Teams 1:1 ve grup sohbetleri|Bir transkript ve tüm ekleri ve ayıklanan öğeler aynı **FamilyId değerini** paylaşır. Her transkript benzersiz bir **FamilyId'ye** sahiptir.|Aynı konuşmadaki tüm transkript dosyaları ve bunların aile öğeleri aynı **ConversationId değerini** paylaşır. Bu, aşağıdaki öğeleri içerir: <ul><li>Aynı **ConversationId'yi** paylaşan tüm transkriptlerin ayıklanan tüm öğeleri ve ekleri.</li><li>Aynı sohbet konuşması için tüm transkriptler</li><li>Her transkriptin tüm koruyucu kopyaları</li><li>Aynı sohbet konuşmasından sonraki koleksiyonlardan dökümler</li></ul> <br/> Teams 1:1 ve grup sohbeti konuşmaları için, her biri konuşma içinde farklı bir zaman dilimine karşılık gelen birden çok transkript dosyanız olabilir. Bu transkript dosyaları aynı katılımcılarla aynı konuşmadan geldiği için aynı **ConversationId** değerini paylaşır.|
|Standart, özel ve paylaşılan kanal sohbetleri|Her gönderi ve tüm yanıtlar ve ekler kendi transkriptine kaydedilir. Bu transkript ve tüm ekleri ve ayıklanan öğeler aynı **FamilyId değerini** paylaşır.|Her gönderinin ve eklerinin ve ayıklanan öğelerin benzersiz bir **ConversationId değeri** vardır. Aynı gönderiden sonraki koleksiyonlar veya yeni yanıtlar varsa, bu koleksiyonlardan elde edilen değişim transkriptleri de aynı **ConversationId'ye** sahip olur.|

Aile veya konuşmaya göre gruplandırılmış Teams içeriği görüntülemek için gözden geçirme kümesinin komut çubuğundaki **Grup** denetimini kullanın.

![Komut çubuğunda grup denetimi.](..\media\TeamsGroupControl.png)

- Aileye göre gruplandırılmış Teams içeriği görüntülemek için Aile **eklerini** gruplandır'ı seçin. Her transkript dosyası, gözden geçirme kümesi öğeleri listesindeki bir satırda görüntülenir. Ekler öğenin altına iç içe yerleştirilmiştir.

- Konuşmaya göre gruplandırılmış Teams içeriği görüntülemek için **Grup Teams veya Yammer konuşmaları** seçin. Her konuşma, gözden geçirme kümesi öğeleri listesindeki bir satırda görüntülenir. Transkript dosyaları ve ekleri üst düzey konuşmanın altında iç içe yerleştirilmiştir.

> [!NOTE]
> Bulut ekleri, göründükleri konuşmalarla gruplandırılır. Bu gruplandırma, dosyanın eklendiği iletinin transkript dosyasıyla aynı **FamilyId** değeri ve iletinin göründüğü konuşmayla aynı **ConversationId** değeri atanarak gerçekleştirilir. Bu, farklı konuşmalara eklenmiş bulut eklerinin birden çok kopyasının gözden geçirme kümesine eklenebileceği anlamına gelir.

#### <a name="viewing-transcript-files-for-conversations"></a>Konuşmalar için transkript dosyalarını görüntüleme

Transkript dosyalarını bir gözden geçirme kümesinde görüntülerken, iletilerden bazıları mor renkle vurgulanır. Vurgulanan iletiler, görüntülemekte olduğunuz transkriptin hangi koruyucu kopyasına bağlıdır. Örneğin, User4 ile User2 arasındaki 1:1 sohbetinde, User4 tarafından gönderilen iletiler, User4'ün posta kutusundan toplanan dökümü görüntülediğinizde mor renkle vurgulanır. Kullanıcı2'nin aynı konuşmanın dökümünü görüntülediğinizde, User2 tarafından gönderilen iletiler mor renkle vurgulanır. Bu vurgulama davranışı, kullanıcının gönderilerinin Teams istemcisinde mor renkle vurgulandığı aynı Teams istemci deneyimini temel alır.

Aşağıdaki ekran görüntüleri, Teams istemcisindeki konuşmanın bir örneğini ve inceleme kümesindeki aynı konuşmanın transkript dosyasını gösterir. Döküm dosyasındaki mor vurgulama, transkriptin User2'nin posta kutusundan toplandığını gösterir.

##### <a name="conversation-in-teams-client"></a>Teams istemcisinde konuşma

![Gözden geçirme kümesindeki transkript dosyasında gösterilen konuşma.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Transkript dosyasında konuşma

![Teams istemcisinde gösterilen konuşmanın aynısı.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Transkript konuşma yazışması oluşturma

eBulma'daki (Premium) yeni olay biçimindeki konuşma yazışma işlevselliği, araştırmanızla ilgili olabilecek öğelerle ilgili bağlamsal içeriği belirlemenize yardımcı olur. Bu özellik, koleksiyon sırasında arama sorgusuyla eşleşen öğelerden önce gelen ve izleyen sohbet iletilerini içeren ayrı konuşma görünümleri oluşturur. Bu özellik, Microsoft Teams'da sohbet konuşmalarını (*yazışmalı konuşmalar* olarak adlandırılır) verimli ve hızlı bir şekilde gözden geçirmenizi sağlar. Daha önce açıklandığı gibi, eBulma (Premium) bir gözden geçirme kümesine Teams içerik eklediğinde sohbet konuşmaları HTML transkript dosyalarında yeniden oluşturulur.

eBulma (Premium) tarafından öğelerle ilgili bağlam sağlayan ek iletiler ve yanıt döküm dosyalarını eklemek için kullanılan mantık, Teams içerik toplarken kullandığınız koleksiyon sorgusuyla (*duyarlı öğeler* olarak adlandırılır) eşleşmektedir. Farklı iş parçacığı oluşturma davranışları, yanıt veren öğeleri toplamak için kullanılan sohbet türlerini ve arama sorgusunu temel alır. İki yaygın koleksiyon senaryosu vardır:

- Anahtar sözcükler ve property:value çiftleri gibi arama parametrelerini kullanan sorgular

- Yalnızca tarih aralıklarını kullanan sorgular

|İçerik türünü Teams|Arama parametrelerine sahip sorgular|Tarih aralıklarına sahip sorgular|
|---|---|---|
|Teams 1:1 ve grup sohbetleri|Duyarlı öğelerden 12 saat önce ve 12 saat sonra gönderilen iletiler, duyarlı öğeyle tek bir transkript dosyasında gruplandırılır.|24 saatlik bir zaman penceresindeki iletiler tek bir transkript dosyasında gruplandırılır.|
|Standart, özel ve paylaşılan Teams kanal sohbetleri|Duyarlı öğeler ve karşılık gelen tüm yanıtları içeren her gönderi tek bir transkript dosyasında gruplandırılır.|Duyarlı öğeler ve karşılık gelen tüm yanıtları içeren her gönderi tek bir transkript dosyasında gruplandırılır.|

### <a name="deduplication-of-teams-content"></a>Teams içeriğinin yinelenenlerini kaldırma

Aşağıdaki listede, bir gözden geçirme kümesinde Teams içerik toplanırken yinelenenleri kaldırma (ve yinelenenleri kaldırma) davranışı açıklanmaktadır.

- Gözden geçirme kümesine eklenen her transkript dosyası, veri konumlarında depolanan içeriğe bire bir eşleme olmalıdır. Başka bir deyişle, eBulma (Premium) gözden geçirme kümesine zaten eklenmiş Teams içeriği toplamaz. Bir sohbet iletisi zaten bir gözden geçirme kümesinde toplanıyorsa, eBulma (Premium) sonraki koleksiyonlarda aynı veri konumundan aynı iletiyi gözden geçirme kümesine eklemez.

- 1:1 ve grup sohbetleri için, iletilerin kopyaları her konuşma katılımcısının posta kutusunda depolanır. Farklı katılımcıların posta kutularında bulunan aynı konuşmanın kopyaları farklı meta verilerle toplanır. Sonuç olarak, konuşmanın her örneği benzersiz olarak değerlendirilir ve ayrı transkript dosyalarında gözden geçirme kümesine getirilir. Bu nedenle, 1:1 veya grup sohbetinin tüm katılımcıları bir durumda koruyucu olarak eklenirse ve bir koleksiyonun kapsamına dahil edilirse, her transkriptin kopyaları (aynı koruma için) gözden geçirme kümesine eklenir ve aynı **ConversationId** ile birlikte gruplandırılır. Bu kopyaların her biri ilgili bir koruyucu ile ilişkilendirilir. **İpucu**: Gözden geçirme kümesi listesindeki **Koruyucu** sütunu, ilgili transkript dosyasının koruyucusunu tanımlar.

- Aynı konuşmadaki sonraki öğe koleksiyonlarında, yalnızca daha önce toplanmamış olan delta içeriği gözden geçirme kümesine eklenir ve aynı konuşmadan daha önce toplanan transkriptlerle gruplandırılır (aynı **ConversationId** paylaşılarak). Bu davranışa bir örnek aşağıda verilmişti:

   1. Toplama A, Kullanıcı1 ile Kullanıcı2 arasındaki konuşmadaki iletileri toplar ve gözden geçirme kümesine ekler.

   2. B Koleksiyonu aynı konuşmadaki iletileri toplar, ancak A Koleksiyonu çalıştırıldığından bu yana Kullanıcı1 ile Kullanıcı2 arasında yeni iletiler vardır.

   3. Gözden geçirme kümesine yalnızca Koleksiyon B'deki yeni iletiler eklenir. Bu iletiler ayrı bir transkript dosyasına eklenir, ancak yeni transkript, Collection A'dan alınan transkriptlerle aynı **ConversationId** ile gruplandırılır.

   Bu davranış, tüm Teams sohbet türleri için geçerlidir.

### <a name="metadata-for-teams-content"></a>Teams içeriği için meta veriler

Binlerce veya milyonlarca öğe içeren büyük inceleme kümelerinde, incelemenizin kapsamını Teams içerikle daraltmak zor olabilir. gözden geçirmenize Teams içeriğe odaklanmanıza yardımcı olmak için, Teams içeriğe özgü meta veri özellikleri vardır. Gözden geçirme listesindeki sütunları düzenlemek ve Teams içeriğinin gözden geçirilmesini iyileştirmek için [filtreleri ve sorguları yapılandırmak](review-set-search.md) için bu özellikleri kullanabilirsiniz. Bu meta veri özellikleri, dışarı aktarma sonrasında veya üçüncü taraf eBulma araçlarında içeriği düzenlemenize ve görüntülemenize yardımcı olmak için eBulma'dan (Premium) Teams içeriği dışarı aktardığınızda da eklenir.

Aşağıdaki tabloda, Teams içerik için meta veri özellikleri açıklanmaktadır.

|Meta veri özelliği|Açıklama|
|---|---|
|ContainsEditedMessage|Transkript dosyasının düzenlenmiş ileti içerip içermediğini gösterir. Transkript dosyası görüntülenirken düzenlenen iletiler tanımlanır.|
|ConversationId|Öğenin ilişkili olduğu konuşmayı tanımlayan bir GUID. Aynı konuşmadaki transkript dosyaları ve ekleri bu özellik için aynı değere sahiptir.|
|Konuşma adı|Transkript dosyasının veya ekin ilişkili olduğu konuşmanın adı. Teams 1:1 ve grup sohbetleri için bu özelliğin değeri, konuşmanın tüm katılımcılarının UPN'sinin birleştirilmiş olmasıdır. Örneğin, `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams kanal (standart, özel ve paylaşılan) sohbetleri konuşma adı için şu biçimi kullanır: `<Team name>,<Channel name>`. Örneğin, `eDiscovery vNext, General`.|
|ConversationType|Ekip sohbetinin türünü gösterir. Teams 1:1 ve grup sohbetleri için bu özelliğin değeri şeklindedir`Group`. Standart, özel ve paylaşılan kanal sohbetleri için değeri şeklindedir `Channel`.|
|Tarih|Transkript dosyasındaki ilk iletinin zaman damgası.|
|FamilyId|Sohbet konuşması için transkript dosyasını tanımlayan guid. Ekler, bu özellik için dosyanın eklendiği iletiyi içeren transkript dosyasıyla aynı değere sahip olur.|
|FileClass|Bu içerik türünü gösterir. Teams sohbetlerdeki öğeler değerine `Conversation`sahiptir. Buna karşılık, Exchange e-posta iletileri değerine `Email`sahiptir.|
|MessageKind|İleti türü özelliği. Teams içerik değerine `microsoftteams , im`sahiptir.|
|Alıcı|Transkript konuşmasının içinde ileti alan tüm kullanıcıların listesi.|
|TeamsChannelName|Transkripti Teams kanal adı.|

Diğer eBulma (Premium) meta veri özelliklerinin açıklamaları için bkz. [eBulma'da (Premium) meta veri alanlarını belgeleme](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="export-teams-content"></a>Teams içeriğini dışarı aktarma

Bir gözden geçirme kümesindeki içeriği gözden geçirip Teams sonra, araştırmanıza yanıt veren içerik içeren transkript dosyalarını dışarı aktarabilirsiniz. Teams içerik için belirli bir dışarı aktarma ayarı yoktur. Her transkript dosyası bir HTML ileti dosyası olarak dışarı aktarılır. Bu dosya, tek tek sohbet iletileri için tüm meta verileri içeren gizli CDATA etiketlerini de içerir. önceki bölümde açıklanan meta veri özellikleri, Teams içerik dışarı aktarıldığında eklenir.  

Her transkript dosyasına yük dosyasında başvurulur ve yükleme dosyasındaki Export_native_path alanındaki göreli yol kullanılarak bulunabilir. Transkript dosyaları kök dışarı aktarma klasöründeki Konuşmalar klasöründe bulunur.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>bir gözden geçirme kümesinde Teams içeriği görüntülemek için İpuçları

Bir inceleme kümesinde Teams içeriği görüntülemeye yönelik bazı ipuçları ve en iyi yöntemler aşağıdadır.

- Teams içeriğinin gözden geçirilmesini iyileştirmek üzere sütun eklemek ve düzenlemek için komut çubuğundaki Sütunları **özelleştir** denetimini kullanın.

  ![Sütunları eklemek, kaldırmak ve düzenlemek için Sütunu düzenle açılır sayfasını kullanın.](..\media\EditReviewSetColumns.png)

   Teams içerik için yararlı olan sütunları ekleyebilir ve kaldırabilirsiniz. Sütunların sırasını, **sütunu düzenle** açılır sayfasında sürükleyip bırakarak da sıralayabilirsiniz. Ayrıca, sıraladığınız sütun için benzer değerlere sahip Teams içeriği gruplandırmak için sütunları sıralayabilirsiniz.

- Teams içeriği gözden geçirmenize yardımcı olacak yararlı sütunlar **arasında Koruyucu**, **Alıcılar** ve **Dosya türü** veya **İleti türü bulunur**.

- Teams içeriği hızla görüntülemek için Teams ilgili özellikler için [filtreleri](review-set-search.md) kullanın. Önceki bölümde açıklanan meta veri özelliklerinin çoğu için filtreler vardır.

## <a name="deleting-teams-chat-messages"></a>Teams sohbet iletilerini silme

Gizli veya kötü amaçlı bilgiler içeren içerik Teams sohbet iletileri aracılığıyla yayınlandığında veri taşması olaylarına yanıt vermek için eBulma (Premium) ve Microsoft Graph Gezgini'ni kullanabilirsiniz. Kuruluşunuzdaki yöneticiler Microsoft Teams sohbet iletilerini arayabilir ve silebilir. Bu, Teams sohbet iletilerindeki hassas bilgileri veya uygunsuz içeriği kaldırmanıza yardımcı olabilir. Daha fazla bilgi için bkz[. Teams sohbet iletilerini arama ve temizleme](search-and-delete-Teams-chat-messages.md).

## <a name="reference-guide"></a>Başvuru kılavuzu

Microsoft Teams için eBulma (Premium) kullanımına yönelik hızlı başvuru kılavuzu aşağıda verilmiştir. Bu kılavuz, Microsoft Teams içeriğini korumak, toplamak, gözden geçirmek ve dışarı aktarmak için eKeşif (Premium) kullanma anahtar noktalarını özetler.

![Microsoft Teams için eBulma (Premium) kullanma başvuru kılavuzunun küçük resmi.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[PDF dosyası olarak indirme](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
