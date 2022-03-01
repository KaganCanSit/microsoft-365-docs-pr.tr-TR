---
title: Teams'da iş akışı Advanced eDiscovery
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
description: Aynı siteden içeriği korumayı, toplamayı, gözden geçirmeyi ve Microsoft Teams hakkında Advanced eDiscovery.
ms.openlocfilehash: 27f3ada633f7af37b657e59cce64ef1c8e102177
ms.sourcegitcommit: b71a8fdda2746f18fde2c94d188be89f9cab45f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2021
ms.locfileid: "63019118"
---
# <a name="advanced-ediscovery-workflow-for-content-in-microsoft-teams"></a>Advanced eDiscovery için iş akışını Microsoft Teams

Bu makalede, verileri korumak, toplamak, gözden geçirmek ve bu içerikten içerik dışarı Advanced eDiscovery için kapsamlı bir yordamlar, yönergeler ve en iyi Microsoft Teams. Bu makalenin amacı, eBulma iş akışınızı daha iyi bir içerik için Teams etmektir.

İçerik toplama ve işleme için Teams bir içerik kategorisi vardır ve bu kategorileri Advanced eDiscovery:

- **Teams bir sohbetler.** bir konuşmada paylaşılan sohbet iletileri, gönderiler ve Teams iki kişi arasında.  Teams bir sohbetler, konuşma olarak da *çağrılır*.

- **Teams sohbetleri seçin**. Üç veya daha fazla kişi arasında bir konuşmada paylaşılan sohbet Teams gönderileri ve ekler. Ayrıca *1:N sohbetler* veya *grup konuşmaları olarak da adlandırılan*.

- **Teams seçin**. Bir kanalda paylaşılan sohbet iletileri, gönderiler, yanıtlar ve Teams.

- **Özel Teams kanallarını seçin**. Özel bir kanalda paylaşılan ileti gönderileri, yanıtlar ve Teams.

## <a name="where-teams-content-is-stored"></a>İçerik Teams depolandığı yer

Advanced eDiscovery'Teams içeriklerini yönetmenin önkoşulları, Advanced eDiscovery'te toplayabilirsiniz, iş bulundurabilir ve gözden geçirebilirsiniz Teams içeriğinin türünü ve bu içeriğin Microsoft 365. Aşağıdaki tabloda, Teams türü ve her biri nerede depolandığı listeledir.

||Sohbet iletilerinin ve gönderilerinin konumu  |Dosya ve eklerin konumu |
|:---------|:---------|:---------|
|Teams bire bir sohbetler     |Bire bir sohbetlerde yer alan mesajlar, tüm sohbet Exchange Online posta kutusunda saklanır. |Bire bir sohbette paylaşılan dosyalar, dosyayı OneDrive İş kişinin hesaplarında depolanır. |
|Teams sohbetleri grup sohbetleri     |Grup sohbetleri'nin iletileri tüm sohbet Exchange Online posta kutusunda saklanır. |Grup sohbetlerde paylaşılan dosyalar, OneDrive İş paylaşan kişinin hesaplarında depolanır. |
|Teams kanalların     |Tüm kanal iletileri ve gönderileri, ekiple Exchange Online posta kutusunda depolanır.|Kanalda paylaşılan dosyalar, ekiple ilişkilendirilmiş SharePoint Online sitesinde depolanır.           |
|Özel Teams kanalları     |Özel kanalda gönderilen iletiler, Exchange Online tüm üyelerinin posta kutularında depolanır.|Özel kanalda paylaşılan dosyalar, özel kanalla ilişkilendirilmiş SharePoint Bir Çevrimiçi Site'de depolanır.|
||||

## <a name="create-a-case-for-teams-content"></a>İçerik oluşturmak için Teams oluşturma

Advanced eDiscovery'da Teams için ilk adım, içerik yönetimi için iyileştirilmiş yeni vaka biçimini kullanarak vaka Teams oluşturmaktır. dosya içeriği için yeni vaka biçimini kullanmanın avantajları Teams vardır:

- Aynı konuşmada yanıt veren öğeler içeren ek iletilerin otomatik olarak toplanıyor ve gözden geçirme kümelerine ekli olduğu konuşma dizileri desteği.

- Teams sohbet konuşmaları, kümeleri gözden geçirmek için otomatik olarak HTML döküm dosyası olarak eklenir. Konuşmalarda paylaşılan bulut ekleri de gözden geçirme kümesine eklenir. Bu, yanıt veren öğeleri olan konuşmalara bağlam sağlar ve sohbet tabanlı içerikle üretilen toplam öğe sayısını azaltmaya yardımcı olur.

- Gözden geçirme kümelerine 1 TB'a kadar olan koleksiyonlar eklenebilir ve bu da bir olayda büyük miktarda Teams içeriği toplamana ve toplamaya izin vermenizi sağlar.

Artan büyük/büyük harf sınırları hakkında daha fazla bilgi için bkz[. Büyük/yeni harf Advanced eDiscovery](advanced-ediscovery-new-case-format.md).

Vaka oluşturmak için:

1. Gidin ve <https://compliance.microsoft.com> oturum açma.

2. Gezinti bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi **eBulma'ya > tıklayın**.

3. Olay **Advanced eDiscovery** Vakalar sekmesine **tıklayın ve** sonra da Vaka **oluştur'a tıklayın**.

   Yeni **eBulma olay sayfası** görüntülenir. Büyük **/küçük harf** biçimi bölümünde, yeni büyük/küçük harf biçimini kullanarak büyük/küçük harf oluşturma seçeneği vardır.

   ![Yeni eBulma olay sayfasındaki büyük harf seçeneği.](..\media\AeDNewCaseFormat1.png)

4. Vakayı adlandırdikten sonra Yeni **seçeneğini belirleyin** ve ardından Kaydet'e **tıkerek** vakayı oluşturun.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Özel Teams kaynakları ekleme ve özel Teams koruma  

Sonraki adım, araştırmanız kapsamında veri koruyucu olan kullanıcıları tanımlamak ve bunları ve bunların içerik konumlarını önceki bölümde oluşturduğunuz vakaya koruyucu olarak eklemektir. Koruyucular eklerken, onların posta kutusunu ve özel OneDrive kaynaklarını belirtebilirsiniz. Ayrıca, araştırmanız Teams korunması için bu konumları hızla yasal tutmaları için özel içerik konumlarını koruyucu veri kaynağı olarak belirtebilirsiniz. Ayrıca, içeriği toplamayı ve gözden geçirme kümesine eklemenizi de kolaylaştırır.

Bir vakaya koruyucular eklemek ve özel veri kaynaklarını korumak için:

1. Önceki bölümde Advanced eDiscovery büyük/yeni olay durumuna gidin ve ardından Veri **kaynakları'ne tıklayın**.

2. Veri kaynakları **sayfasında Veri** kaynağı **ekleYeni** >  **koruyucular ekle'ye tıklayın**.

3. **Yeni koruyucu sihirbazında**, kullanıcı adının veya diğer adının ilk bölümünü yazarak vakaya bir veya birden çok koruyucu ekleyin. Doğru kişiyi buktan sonra listeye eklemek için adını seçin.  

4. Custo custo bir belgeyle otomatik olarak ilişkilendirilmiş birincil veri kaynaklarını görüntülemek ve custo custo custo ötele ilişkilendirmek için başka konumlar seçmek için genişletin.

   ![Custo bir veri kaynakları.](..\media\TeamsCustodialDataLocations1.png)

5. Daha fazla içeriğe özel veri kaynakları eklemek için bu Teams izleyin. Veri **konumu** eklemek için Düzenle'ye tıklayın.

   - **Posta Kutuları**. Custo bir posta kutusu varsayılan olarak seçilidir. Özel veri olarak bire bir sohbetler, grup sohbetleri ve özel kanal sohbetleri eklemek (ve korumak) için bu seçeneği seçili durumda tutabilirsiniz.

   - **OneDrives**. Custohal'in OneDrive hesabı varsayılan olarak seçilidir. Bire bir sohbetlerde ve grup sohbetlarında paylaşılan dosyaları özel veriler olarak eklemek (ve korumak) için bu seçeneği seçili durumda tutabilirsiniz.

   - **SharePoint**. Özel SharePoint herhangi bir özel kanalla ilişkilendirilmiş olan kullanıcı sitesini ekleyin. Custo ortak dosyalar özel kanalda paylaşılan dosyaları özel veriler olarak eklemek (ve korumak) için bir üyedir. **Düzenle'ye** tıklayın ve özel bir kanalla SharePoint sitenin URL'sini ekleyin. Bir kullanıcının üyesi olduğu özel kanalların nasıl bulunacağı hakkında bilgi edinmek için bkz. [Özel kanalların eBulma](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels).

   - **Teams**. Custo ortaklarının üyesi olduğu ekipleri, özel veriler olarak ekleyebilir (ve) tüm kanal iletileriyle bir kanalda paylaşılan tüm Teams ekleyin. **Düzenle'ye tıklarken**, koruyucu ekibin her bir ekibiyle ilişkilendirilmiş posta kutusu ve site bir üye olarak görüntülenir. Özel dosyayla ilişkilendirmek istediğiniz ekipleri seçin. Her ekip için hem ilgili posta kutusunu hem de siteyi seçmeniz gerekir.

   > [!NOTE]
   > Ayrıca, koruyucuların bir koruyucu veri Teams üyesi olmayan posta kutusunu ve posta kutusunun sitesini de  eklersiniz. Bunu yapmak için, **Ekle ve** **Düzenle'Exchange** **SharePoint posta** kutusu ve site ilişkilendirmeyi ekiple ilişkilendirme'yi ekleyerek bunu yapar.

6. Özel kişi ekdikten ve özel veri kaynaklarını yapılandırdikten sonra, **Tutma ayarları sayfasını** görüntülemek için **Sonraki'ne** tıklayın.

   Koruyucuların listesi görüntülenir ve Tut sütunundaki **onay kutusu** varsayılan olarak seçilidir. Bu, her custo custo ve ardından bir veri kaynağına yerleştiril olacağını belirtti. Bu verileri korumak için bu onay kutularını seçili bırakın.

7. Tutma ayarları **sayfasında,** koruyucu ayarları **gözden geçirmek** için Sonraki'ne tıklayın. **Vakaya** koruyucuları eklemek için Gönder'e tıklayın.

Bir olayda veri kaynaklarını ekleme ve koruma hakkında daha fazla bilgi Advanced eDiscovery bkz:

- [Bir vakaya koruyucular ekleme Advanced eDiscovery ekleme](add-custodians-to-case.md)

- [Özel durum durumuna özel olmayan veri Advanced eDiscovery ekleme](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>İçerik Teams toplama ve gözden geçirme kümesine ekleme

Vakaya koruyucular ekledikten ve custo bir veri kaynağında içeriği korurken, iş akışının bir sonraki adımı araştırmanız ile ilgili Teams içeriğini aramak ve daha fazla gözden geçirme ve çözümleme yapmak için bir gözden geçirme kümesine eklemektir. Exchange'ta e-posta ve SharePoint'ta belgeler gibi diğer Microsoft 365 hizmetlerinden içerikle birlikte Teams içeriği toplamak normal bir durum olsa da, bu bölüm özellikle koleksiyonda Teams içeriği toplamaya odaklanır. Gözden geçirme kümesine eklemek istediğiniz içeriği Teams başka koleksiyonlar da oluşturabilirsiniz.

Olay için Teams toplayabilirsiniz, iş akışında iki adım vardır:

1. **Taslak koleksiyonu oluşturun**.  İlk adım, arama *ölçütlerinize uyan* öğelerin tahmini bir taslak koleksiyonu oluşturmaktır. Arama sorgusuyla eşleşmeye neden olan sonuçlar hakkında, bulunan öğelerin toplam sayısı, boyutu, bunların bulunduğu farklı veri kaynakları ve arama sorgusuyla ilgili istatistikler gibi bilgileri görüntüebilirsiniz. Koleksiyon tarafından döndürülen öğelerden bir örneğinin önizlemesini de görüntüebilirsiniz. Bu istatistikleri kullanarak, arama sorgusunu değiştirebilir ve taslak koleksiyonunu, davanıza uygun içeriği toplarkenn memnun olana kadar sonuçları daraltmak için gereken sayıda çalıştırabilirsiniz.

2. **Taslak koleksiyonunu gözden geçirme kümesine kaydetme**. Taslak koleksiyonunun sonuçlarından memnun olduktan sonra, koleksiyonu bir gözden geçirme kümesine işlersiniz. Taslak koleksiyonu işlerken, koleksiyon tarafından döndürülen öğeler gözden geçirme, çözümleme ve dışarı aktarma için bir gözden geçirme kümesine eklenir.

Ayrıca, bir taslak koleksiyonu çalıştırmama ve koleksiyonu 2013 veya 2013/2013'lerde bir gözden geçirme kümesine doğrudan ekleme seçeneğiniz vardır.

İçerik koleksiyonu oluşturmak için Teams:

1. Önceki bölümde Advanced eDiscovery koruyucuları ekley istediğiniz durum durumuna gidin ve **Koleksiyonlar'a tıklayın**.

2. Koleksiyonlar **sayfasında New** **collectionStandard** >  **collection'ı seçin**.

3. Koleksiyon için bir ad (gerekli) ve açıklama (isteğe bağlı) yazın.

4. Özel veri **kaynakları sayfasında, eklileri** seç'e tıklayın ve vakaya eklileri seçin.

   Koruyucular listesi Select **custodians** flyout sayfasında görüntülenir.

5. Bir veya daha fazla koruyucu seçin ve Ekle'ye **tıklayın**.

   Koleksiyona belirli koruyucular eklemenizden sonra, her özel kişi için belirli veri kaynaklarının listesi görüntülenir. Bunlar, özel durumuna custo bir eklenmiştir. Tüm koruyucu veri kaynakları varsayılan olarak seçilidir. Bu, Teams ve özel kanallarla ilişkilendirilmiş olan iletişim kanallarını içerir.

   daha fazla içerik toplarken aşağıdaki Teams öneririz:

   - Koruyucuların OneDrive veli hesaplarını koleksiyon kapsamından kaldırın (**Her custo OneDrive custo yassı** sütunundaki onay kutusunun işaretini kaldırın). Bu, bire bir sohbetlere ve grup sohbetlere eklenmiş yinelenen dosya koleksiyonunun önüne geçmek için kullanılır. Bulut ekleri, taslak koleksiyonunu gözden geçirme kümesine işlerken koleksiyonda bulunan her konuşmadan otomatik olarak toplanır. Bu yöntem kullanılarak (koleksiyonun bir OneDrive bir parçası olarak bu hesaplarda arama yapmak yerine), 1:1'e eklenen dosyalar ve grup sohbetleri, paylaşıldıkları konuşmada grupılır.

   - Özel kanallarda paylaşılan dosyaların **bulunduğu sitenin SharePoint** siteyi kaldırmak için Ek site sütunundaki onay kutusunun işaretini kaldırın. Bunu yapmak, özel kanal konuşmalarına eklenmiş yinelenen dosyaları toplamayı ortadan kaldırmaz, çünkü taslak koleksiyonunu işlerken ve paylaşılan konuşmalarda gruplanan konuşmalarda gruplanan özel kanal konuşmalarına ekli bulut ekleri otomatik olarak gözden geçirme kümesine eklenir.

6. Daha önce koruyucu veri kaynakları olarak Teams adımlarını izlediysanız, bu adımı atlayıp İleri'yi **seçin**. Aksi takdirde, Özel  olmayan veri kaynakları sihirbaz sayfasında, koleksiyonda arama yapmak için vakaya eklemış olduğunuz Teams özel olmayan veri kaynaklarını seçebilirsiniz.

7. Daha önce koruyucu veri kaynakları olarak Teams adımlarını izlediysanız, bu adımı atlayıp İleri'yi **seçin**. Aksi takdirde, **Ek konumlar** sihirbazı sayfasında koleksiyonda arama yapmak için başka veri kaynakları eklersiniz. Örneğin, özel veya özel olmayan veri kaynağı olarak ekilmeyen bir ekibin posta kutusunu ve sitesini  eklersiniz. Aksi takdirde **İleri'yi seçin** ve bu adımı at edin.

8. Koşullar sihirbazı **sayfasında**, önceki sihirbaz sayfalarında belirttiğiniz veri Teams içeriği toplamak için arama sorgusunu yapılandırabilirsiniz. Koleksiyonun kapsamını daraltmak için çeşitli anahtar sözcükler ve arama koşulları kullanabilirsiniz. Daha fazla bilgi için bkz [. Koleksiyonlar için arama sorguları oluşturma](building-search-queries.md).

   En kapsamlı Teams sohbet konuşmalarını (1:1, grup, kanal ve özel sohbetler dahil) en kapsamlı koleksiyonunun sağlanmasına yardımcı olmak için **Tür** koşulu kullanın ve Anlık iletiler **seçeneğini** belirleyin. Ayrıca koleksiyonun kapsamını araştırmanız ile ilgili öğelere daraltmak için bir tarih aralığı veya birkaç anahtar sözcük de dahil öneririz. Tür ve Tarih seçeneklerini kullanan örnek bir sorgunun **ekran** **görüntüsü:**

   ![İçerik toplama sorgusu Teams.](..\media\TeamsConditionsQueryType.png)

9. Taslak **kaydetme veya toplama** sihirbazı sayfasında, taslak koleksiyonu oluşturmak veya koleksiyonu gözden geçirme kümesine işlemek istediğinize bağlı olarak, birini yapın.

   ![Taslak koleksiyonunu kaydedin veya koleksiyonu kaydedin.](..\media\TeamsDraftCommitCollection.png)

   1. **Koleksiyonu taslak olarak kaydedin**. Taslak koleksiyonu oluşturmak için bu seçeneği belirtin. Daha önce de belirtildiği gibi, taslak koleksiyonları gözden geçirme kümesine koleksiyon sonuçlarını eklemez. Arama sonuçlarının, koleksiyon kapsamındaki veri kaynaklarıyla ilgili arama sorgusuyla eşleşmesi için bir tahmin döndürür. Bu size, [koleksiyon istatistiklerini ve raporlarını[(koleksiyon-istatistik-reports.md)] görüntüleme ve taslak koleksiyonunu düzenleme ve yeniden çalıştırma fırsatı verir. Bir taslak koleksiyonunun sonucundan memnunsanız, bunu bir gözden geçirme kümesine de işlersiniz. Daha fazla bilgi için bkz [. Taslak koleksiyonu oluşturma](create-draft-collection.md).

   2. **Öğeleri toplayın ve gözden geçirme kümesine ekleyin**. Koleksiyonu çalıştırmak ve sonra da sonuçları gözden geçirme kümesine eklemek için bu seçeneği belirtin. Koleksiyonu yeni veya var olan bir gözden geçirme kümesine  eklersiniz. Konuşma iletilerinin (konuşma *Teams) ve* bulut eklerini toplama ile ilgili bağlamsal bilgileri toplama seçenekleri varsayılan olarak seçilidir ve seçilmez. Bu seçenekler otomatik olarak uygulanır. Bu seçenekler, içeriğinizi ilk kez oluşturulduğunda kullanılan yeni büyük/yeni Teams uygulanır. Koleksiyonları gözden geçirme kümesine kaydetme hakkında daha fazla bilgi için bkz. [Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md).

10. Koleksiyonu yapılandırmayı bitirdikten sonra, koleksiyonu göndererek bir taslak koleksiyonu oluşturun veya öğeleri toplayın ve bunları gözden geçirme kümesine ekleyin.

   Koleksiyonu gözden geçirme kümesine ekleme işlemi tamamlandığında, Koleksiyonlar sekmesinde koleksiyonun durum değeri Kabul Edilen olarak **ayarlanır**.

## <a name="review-teams-content-in-a-review-set"></a>Gözden Teams gözden geçirme kümesinde içeriği gözden geçirme

Gözden geçirme kümesine Teams içerik koleksiyonları eklemenizden sonra, bir sonraki adım içeriği araştırmanıza uygun olacak şekilde gözden geçirmek ve gerekirse bu içeriği kararttır etmektir. İçerik içeriklerini gözden geçirmek Teams önemli bir önkoşul, Advanced eDiscovery konuşmalarını ve eklerini gözden geçirme kümesine eklerken sohbet Teams işlemlerinin nasıl işle ilgili olduğunu anlamaktır. İçerik içeriğinin Teams işlemi sonucunda aşağıdaki üç sonuç elde olur:

- **[Gruplama](#grouping)**. Konuşmaların yanıtlarını, gönderilerini ve Teams birlikte gruplandırıldı ve gözden geçirme kümesinde sunuldu. Bu, sohbet görüşmesinde ayıklanan ve grup sohbeti içinde bulunan ekleri de içerir.

- **[Döküm konuşma yazışması](#transcript-conversation-threading)**. Nasıl Advanced eDiscovery koleksiyon ölçütlerine uyan öğelerle ilgili bağlam sağlamak üzere bir konuşmadan hangi ek içeriklerin top toplan bilgilerine karar verir.

- **[Deduplication](#deduplication-of-teams-content)**. Yinelenen Advanced eDiscovery içeriği nasıl Teams işleyeni.

- **[Meta Veri.](#metadata-for-teams-content)** Toplanmış ve Advanced eDiscovery gözden Teams içeriği bu içeriğe ekleyen meta veri özellikleri.

Meta verileri gruplama, konuşma dizisini, Teams kaldırmayı anlamanız, içeriğin gözden Teams yardımcı olacaktır. Bu bölümde ayrıca, [gözden geçirme kümesinde Teams görüntülemeye yönelik ipuçları da yer almaktadır](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Gruplama

Konuşmalardan içerik Teams gözden geçirme kümesine ekli olduğunda, iletiler, gönderiler ve konuşmalardan gelen yanıtlar HTML döküm dosyalarında bir araya toplanır. Tek bir sohbet konuşmada birden fazla döküm dosyası olabilir. Bu döküm dosyalarının önemli bir işlevi, metin Teams tek tek iletiler olarak değil sürekli konuşmalar olarak sunmaktır. Bu, önceki adımda koleksiyonlarınızı arama ölçütlerine uyan öğeler için bağlam sağlar ve gözden geçirme kümesinde toplanan öğe sayısını azaltır. Dökümler ve ilişkili öğeler aile veya konuşmaya *göre* *gruplandı.* FamilyId meta veri özelliği için aynı ailedeki öğelerin **değeri** aynı olur. Aynı konuşmadaki öğeler, ConversationId meta veri özelliği **için aynı değere** sahip olur.

Aşağıdaki tabloda, farklı türlerde sohbet içeriğinin Teams ve konuşmaya göre nasıl gruplu olduğu açıklandı.

| Teams türü|Aileye göre grupla  |Konuşmaya göre grupla  |
|:---------|:---------|:---------|
|Teams bire bir sohbetler ve grup sohbetleri   | Bir döküm ve tüm ekleri ve ayıklanan öğeler aynı **FamilyId'i paylaşır**. Her dökümün benzersiz bir **FamilyId'si var**. |Aynı konuşma içindeki tüm döküm dosyaları ve aile öğeleri aynı **ConversationId'i paylaşır**. Bu, aşağıdaki öğeleri içerir:<br/><br/>  - Aynı ConversationId'yi paylaşan tüm dökümlerin tüm ayıklanan öğeleri **ve ekleri**. <br/> - Aynı sohbet görüşmesinin tüm dökümleri<br/> - Her dökümün tüm koruyucu kopyaları<br/> - Aynı sohbet görüşmelerinden sonraki koleksiyonlardan dökümler <br/><br/>  Bire Teams sohbetleri ve grup sohbeti konuşmalarını takip etmek için, her biri konuşma içinde farklı bir zaman dilimine karşılık gelen birden fazla döküm dosyamız olabilir. Bu döküm dosyaları aynı katılımcılarla aynı konuşmadan geldiklerinden, aynı **ConversationId'leri paylaşırlar**.|
|Teams ve özel kanal sohbetleri    | Her gönderiyle tüm yanıtlar ve ekler kendi döküm metnine kaydedilir. Bu döküm ve tüm ekleri ve ayıklanan öğeler aynı **FamilyId'i paylaşır**.         |Her gönderinin ve ekleri ile ayıklanan öğelerin benzersiz bir **ConversationId'si vardır**. Aynı gönderiden sonraki koleksiyonlar veya yeni yanıtlar varsa, bu koleksiyonların sonucunda elde edilen delta dökümleri de **aynı ConversationId'ye sahip olur**.|
||||

Aile veya **konuşmaya** göre gruplu içeriği görüntülemek için, incelemenin Teams çubuğundaki Grup denetimi'ne tıklayın.

![Komut çubuğunda grup denetimi.](..\media\TeamsGroupControl.png)

- Aile **eklerini grupla'ya** Teams göre grupla içeriğini görüntülemek için Aile eklerini grupla'ya tıklayın. Her döküm dosyası gözden geçirme kümesi öğeleri listesinde bir satırda görüntülenir. Ekler öğenin altına iç içe geçmiştir.

- İçeriği **konuşmaya Teams için Yammer Teams veya konuşmaları** yeniden Teams sohbeti seçin. Her konuşma, gözden geçirme kümesi öğeleri listesinde bir satırda görüntülenir. Döküm dosyaları ve ekleri en üst düzey konuşmanın altında iç içe geçmiştir.

> [!NOTE]
> Bulut ekleri, içinde görünen konuşmalarla gruptur. Bu gruplama, dosyanın ekli olduğu iletinin döküm dosyası olarak **aynı FamilyId** ve iletide görünen konuşmayla aynı **ConversationId** atanarak işler. Bu, bulut eklerinin birden çok kopyasının, farklı konuşmalara eklenmişse gözden geçirme kümesine ekleneceği anlamına gelir.

#### <a name="viewing-transcript-files-for-conversations"></a>Konuşmalar için döküm dosyalarını görüntüleme

Gözden geçirme kümesinde transkript dosyalarını görüntülerken, bazı iletiler mor renkle vurgulanır. Vurgulanan iletiler, görüntülemekte olduğunu dökümün hangi özel kopyasına bağlı olarak olduğunu bağlıdır. Örneğin, Kullanıcı4 ile Kullanıcı2 arasındaki bire bir sohbette, User4'in posta kutusunda toplanan döküme bakarak User4 tarafından gönderilen iletiler mor renkle vurgulanır. User2'nin aynı konuşmanın döküm metnine bakarak, Kullanıcı2 tarafından gönderilen iletiler mor renkle vurgulanır. Bu vurgulama davranışı, kullanıcının Teams istemcide mor renkle vurgulanan aynı istemci deneyimine Teams dayalıdır.

Aşağıdaki ekran görüntüleri gözden geçirme kümesinde Teams istemcisinde konuşmanın bir örneğini ve aynı konuşmanın döküm dosyasını gösterir. Döküm dosyasındaki mor vurgu, döküm dosyasının Kullanıcı2'nin posta kutusundan toplanmış olduğunu gösterir.

##### <a name="conversation-in-teams-client"></a>Teams istemcisinde konuşma

![Gözden geçirme kümesinde döküm dosyasında gösterilen konuşma.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Döküm dosyasındaki konuşma

![İstemcide gösterilen konuşmanın Teams.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Döküm konuşma yazışması

Advanced eDiscovery'daki yeni vaka biçimindeki konuşma dizileri işlevselliği, araştırmanıza uygun olacak öğelerle ilgili bağlamsal içeriği tanımlamanıza yardımcı olur. Bu özellik, önünde ve öğeleri takip eden sohbet iletilerinin koleksiyon sırasındaki arama sorgusuyla eşleşmesi için ayrı konuşma görünümleri oluşturur. Bu özellik, aynı programda tüm sohbet konuşmalarını (zincir konuşmalar olarak adlandırılan) verimli *bir şekilde ve* hızlı bir şekilde inceleme Microsoft Teams. Daha önce de açıklaması gibi, konuşmalar gözden geçirme kümesine içerik Advanced eDiscovery HTML döküm dosyalarında yeniden Teams yeniden vardır.

Advanced eDiscovery tarafından öğelerle ilgili bağlam sağlayan ek iletileri ve yanıtların döküm dosyalarını eklemek için kullanılan mantık, bu içeriği toplarken kullanılan toplama sorgusuyla (yanıt veren *öğeler olarak adlandırılan*) Teams ve hazırlar. Farklı iş parçacığı oluşturma davranışları sohbet türlerine ve yanıt veren öğeleri toplamak için kullanılan arama sorgusuna dayalıdır. İki yaygın koleksiyon senaryosu vardır:

- Anahtar sözcükler ve özellik:değer çiftleri gibi arama parametrelerini kullanan sorgular

- Yalnızca tarih aralıklarını kullanan sorgular

| Teams türü|Arama parametreleriyle sorgular  |Tarih aralıkları ile sorgular  |
|:---------|:---------|:---------|
|Teams bire bir sohbetler ve grup sohbetleri   |Yanıt veren öğelerden 12 saat önce ve 12 saat sonra gönderilen iletiler, tek bir döküm dosyasında yanıt veren öğeyle birlikte gruptur.   |24 saatlik bir pencerede gelen iletiler, tek bir döküm dosyasında grup İlkesini içerir.|
|Teams ve özel kanal sohbetleri    |Yanıt veren öğeleri ve buna karşılık gelen tüm yanıtları içeren her gönderi, tek bir döküm dosyasında gruplandırılır. |Yanıt veren öğeleri ve buna karşılık gelen tüm yanıtları içeren her gönderi, tek bir döküm dosyasında gruplandırılır.|
||||

### <a name="deduplication-of-teams-content"></a>İçerik Teams kaldırma

Aşağıdaki listede, gözden geçirme kümesi içinde içerik toplarken Teams kaldırma (ve yineleme) davranışı açık almaktadır.

- Gözden geçirme kümesine eklenen her döküm dosyasının, veri konumlarında depolanan içeriğe bire bir eşlemesi gerekir. Bu Advanced eDiscovery, gözden geçirme kümesine Teams herhangi bir içerik toplamaz. Bir sohbet iletisi zaten gözden geçirme kümesinde toplanmışsa, Advanced eDiscovery aynı veri konumdan aynı iletiyi sonraki koleksiyonlarda yer alan gözden geçirme kümesine eklemez.

- Bire bir ve grup sohbetleri için iletilerin kopyaları her konuşma katılımcılarının posta kutusunda depolanır. Farklı katılımcıların posta kutularında var olan aynı konuşmanın kopyaları, farklı meta verilerle toplanır. Sonuç olarak, konuşmanın her bir örneği benzersiz olarak kabul edilir ve ayrı döküm dosyalarında gözden geçir kümesine getiriler. Dolayısıyla bire bir sohbetin veya grup sohbetlerinin tüm katılımcıları bir vakaya koruyucu olarak eklenir ve bir koleksiyonun kapsamına dahil edilirse, her dökümün kopyaları (aynı olay için) gözden geçirme kümesine eklenir ve aynı **ConversationId** ile birlikte gruplanır. Bu kopyaların her biri, karşılık gelen bir custo ortak ile ilişkilendirildi. **İpucu**: Gözden **geçirme kümesi listesinde Custo belirli** bir sütun, karşılık gelen döküm dosyasının custo custo bir tanımlar.

- Aynı konuşmadan sonraki öğeler koleksiyonunda, aynı konuşmadan daha önce toplanan metin dökümleriyle birlikte gözden geçirme kümesine ve gruplara (aynı **ConversationId** paylaşarak) yalnızca daha önce toplamamış olan delta içeriği eklenir. İşte bu davranışa bir örnek:

   1. Koleksiyon A, Kullanıcı1 ile Kullanıcı2 arasındaki bir konuşmada iletileri toplar ve gözden geçirme kümesi ekler.

   2. Koleksiyon B aynı konuşmadan ileti toplar, ancak Koleksiyon A çalıştırlır ve Kullanıcı1 ile Kullanıcı2 arasında yeni iletiler vardır.

   3. Gözden geçirme kümesine yalnızca B Koleksiyonu'daki yeni iletiler eklenir. Bu iletiler ayrı bir döküm dosyasına eklenir, ancak yeni döküm, A Koleksiyonu'nda aynı ConversationId tarafından yer alan dökümlerle **birlikte grupludur**.

   Bu davranış, sohbeti takip eden tüm Teams geçerlidir.

### <a name="metadata-for-teams-content"></a>Teams içeriği için meta veriler

Binlerce veya milyonlarca öğeyle büyük gözden geçirme kümelerde, içeriği daraltmak için gözden geçirmenizin kapsamını Teams zor olabilir. Gözden geçirmenize yardımcı olmak için Teams içeriğinizin içeriğine özel meta veri Teams vardır. Bu özellikleri kullanarak gözden geçirme listesinde sütunları düzenleyebilir ve filtreleri ve sorguları yapılandırarak[](review-set-search.md), bu içeriğin gözden Teams kullanabilirsiniz. Dışarı aktarma sonrası veya üçüncü taraf eKbulma araçlarında yer alan Teams verileri Advanced eDiscovery düzenlemenize ve görüntülemenize yardımcı olmak için, bu meta veri özellikleri de bu meta veri özellikleriyle birlikte yer almaktadır.

Aşağıdaki tabloda, bu içeriklerin meta veri Teams açık almaktadır.

|Meta Veri özelliği  |Açıklama  |
|:---------|:---------|
|containsEditedMessage      | Döküm dosyasının düzenlenmiş bir ileti içerdiğini gösterir. Düzenlenmiş iletiler, döküm dosyasını görüntülerken tanımlanır.|
|ConversationId|Öğenin ilişkilendirilen konuşmayı tanımlayan GUID. Bu özellik için aynı konuşmadan metin döküm dosyaları ve ekler aynı değere sahip olur.|
|Konuşma adı     | Döküm dosyasının veya ekin ilişkilendiril olduğu konuşmanın adı. Grup Teams bire bir sohbetler ve grup sohbetleri yapmak için bu özelliğin değeri, konuşmanın tüm katılımcılarının UPN'dir. Örneğin, `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams ve özel kanal sohbetleri görüşme adı için aşağıdaki biçimi kullanır: `<Team name>,<Channel name>`.Örneğin, `eDiscovery vNext, General`.          |
|ConversationType     | Ekip sohbeti türünü gösterir. Bire Teams sohbetler ve grup sohbetleri için bu özelliğin değeri şöyledir`Group`: . Kanal Teams özel kanal sohbetleri için değer: `Channel`.|
|Tarih | Döküm dosyasındaki ilk iletinin zaman damgasıdır.|
|FamilyId|Sohbet konuşmalarının döküm dosyasını tanımlayan GUID. Ekler, bu özellik için dosyanın ekli olduğu iletiyi içeren döküm dosyasıyla aynı değere sahip olur.|
|FileClass     |Bu tür bir içeriği gösterir. Sohbetlerde Teams değeri vardır`Conversation`. Buna karşılık, Exchange-posta iletilerinin değeri vardır`Email`.|          |
|MessageKind     | İletinin tür özelliği. Teams değeri vardır`microsoftteams , im`. |
|Alıcılar     | Döküm konuşması içinde ileti alan tüm kullanıcıların listesi.|
|TeamsChannelName     | Metin Teams adını veya dökümün özel kanal adını girin.|
|||

Meta veri özellikleriyle ilgili diğer Advanced eDiscovery için bkz. Meta [veri alanlarında belge Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="export-teams-content"></a>İçerik Teams aktarma

Gözden geçirme kümesinde içeriği gözden geçirdikten Teams olduktan sonra, incelemenize yanıt veren içeriğin yer alan döküm dosyalarını dışarı aktarabilirsiniz. İçerik türü için belirli bir dışarı Teams yok. Her döküm dosyası HTML ileti dosyası olarak dışarı aktarıldı. Bu dosya, tek tek sohbet iletileri için tüm meta verileri içeren gizli CDATA etiketleri de içerir. Önceki bölümde ele edilen meta veri özellikleri, içerik Teams dahil edilir.  

Yükleme dosyasında her döküm dosyasına başvurur ve yükleme dosyasındaki Export_native_path yolu kullanarak yer almaktadır. Döküm dosyaları Konuşmalar klasöründeki kök dışarı aktarma klasöründe bulunur.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>İpuçları gözden Teams görüntüleme deneyimi

Burada, gözden geçirme kümesinde içeriği Teams için bazı ipuçları ve en iyi yöntemler ve yer vardır.

- İçerik **içeriğinin gözden** geçirmesini iyileştirmek üzere sütunları eklemek ve düzenlemek için komut çubuğundaki Sütunları özelleştir Teams kullanın.

  ![Sütunları eklemek, kaldırmak ve düzenlemek için Sütun uçunu düzenle sayfasını kullanın.](..\media\EditReviewSetColumns.png)

   İçerik eklemek ve kaldırmak için yararlı olan sütunları Teams kaldırabilirsiniz. Ayrıca, Sütunları düzenleme sayfası içinde sürükleyip bırakarak da **sütunların sırasını** sıralayabilirsiniz. Ayrıca, sıralamada sütunlarda benzer Teams içeriği gruplandıran sütunlara göre de sıralayabilirsiniz.

- Custo veya **Recipients**, file type Teams Message **type gibi** içeriklerini gözden geçirmenizi yardımcı **olacak** **yararlı sütunlar**.

- belirli [bir](review-set-search.md) içeriği Teams için ilgili özellikler için Teams kullanın. Önceki bölümde açıklanan meta veri özelliklerinin çoğu için filtreler vardır.

## <a name="reference-guide"></a>Başvuru kılavuzu

İşte, bu kılavuzda Advanced eDiscovery kullanma Microsoft Teams. Bu kılavuz, verileri korumak, toplamak, gözden Advanced eDiscovery kaynak içeriklerini korumak, gözden geçirmek ve dışarı aktarmada Microsoft Teams.

![Microsoft Teams için Advanced eDiscovery kullanma başvuru kılavuzuna Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[PDF dosyası olarak indirme](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
