---
title: Başka durumlarda Advanced eDiscovery ve yönetme Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Bu makalede, yeni olay oluşturma ve Advanced eDiscovery açıklanmıştır. İlk adım, olay oluşturmak ve dosya özelliklerini ve Advanced eDiscovery kullanmaya başlamaktır.
ms.openlocfilehash: f647421dcaba3d50f1cb8b7a6b1e58a792f23403
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999075"
---
# <a name="create-and-manage-an-advanced-ediscovery-case"></a>Olay oluşturma ve Advanced eDiscovery yönetme

E-Advanced eDiscovery ayardikten ve davaları yönetecek olan kuruluş [eBulma](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) yöneticilerine izinler atadikten sonra, bir sonraki adım vakayı oluşturmak ve yönetmektir.

Bu makalede ayrıca, bir dava veya diğer soruşturma türlerinde yer alan Advanced eDiscovery iş akışını yönetmek için vakaları kullanmaya yönelik üst düzey bir genel bakış da ve almaktadır.

## <a name="create-a-case"></a>Vaka oluşturma

Vaka oluşturmak ve üye eklemek için aşağıdaki adımları tamamlayın. Vakayı oluşturan kullanıcı otomatik olarak üye olarak eklenir. Olay üyeleri olayla ilgili bilgilere Microsoft 365 uyumluluk merkezi ve Advanced eDiscovery gerçekleştirebilir.

1. eK <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> izinleri atanmış olan kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın. Kuruluş Yönetimi rol grubunun üyeleri de herhangi bir olay Advanced eDiscovery oluşturabilir.

2. Gezinti bölmesinin sol Microsoft 365 uyumluluk merkezi'ne **tıklayın,** **ardından eBulmaAdvanced'i** >  seçin ve ardından Durumlar <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">**sekmesini** seçin</a>.

3. Vaka **oluştur'a seçin**.

4. Yeni **eBulma büyük/küçük** harf çıkış sayfasında, büyük/küçük harfe bir ad (gerekli) ekleyin ve sonra isteğe bağlı bir büyük/küçük harf numarası ve açıklama yazın. Olay adı, kurum içinde benzersiz olmalıdır.

5. **Vakayı oluşturmak** için Kaydet'e tıklayın.

   Yeni vaka oluşturulur **ve Ayarlar büyük**/harf sekmesinde görüntülenir.

6. Yeni Sekme **& Access izinler** **kutucu Ayarlar** Seç'e **tıklayın**.

7. Bu **vakayı yönet uç** sayfasında, Üyeleri **yönet'in altında**, vakaya üye **eklemek** için Ekle'ye tıklayın.

8. Kişi listesinde, vakaya eklemek istediğiniz kişilerin adlarının yanındaki onay kutusunu seçin. Daha önce de belirtildiği gibi, vakaya ekley istediğiniz kişilerin uygun eBulma izinlerine atanmış olduğundan emin olun.

9. Vakanın üyesi olarak eklemek istediğiniz kişiyi seçtikten sonra Ekle'ye **tıklayın**.

10. Bu **vakayı yönet uç** sayfasında **Kaydet'e** tıklar ve vaka üyelerinin yeni listesini kaydedebilirsiniz.

11. Vaka **giriş sayfasına** gitmek için Giriş sekmesine tıklayın.

## <a name="manage-the-workflow"></a>İş akışını yönetme

E-postanızı kullanmaya Advanced eDiscovery için, yaygın eBulma uygulamalarıyla uyumlu [temel bir iş akışı ve burada açık bir iş akışı vardır](advanced-ediscovery-edrm.md). Bu adımların her biri, keşfedebilirsiniz bazı genişletilmiş Advanced eDiscovery de vurgulaacağız.

![Advanced eDiscovery iş akışı.](../media/AeDWorkflow.png)

1. **[Vakaya koruyucular](add-custodians-to-case.md) [ve özel olmayan veri](non-custodial-data-sources.md) kaynakları ekleyin**. Vaka oluşturdukktan sonra ilk adım koruyucu eklemektir. *Koruyucu, olayla* ilgili olması gereken bir belgenin veya elektronik dosyanın yönetimsel denetimine sahip olan kişidir. Buna ek olarak, belirli bir kullanıcıyla ilişkili olmayan ancak olayla ilgili olan veri kaynakları  eklersiniz.

   Bir vakaya koruyucular eklerken aşağıdakiler olur:

   - Custo custo custo her Exchange posta kutusunda, OneDrive hesabında ve custo bir üyesi olduğu tüm Microsoft Teams veya Yammer gruplarında veriler bu durumda "özel veri" olarak "işaretlenir".
  
   - Custo bir veri yeniden dizine alır (Gelişmiş dizin oluşturma adı verilen *bir işlem tarafından*). Bu, bir sonraki adımda aramanızı en iyi duruma getirmeye yardımcı olur.
  
   - Custo cust Bu, araştırma sırasında olayla ilgili olabilir verileri korur.
  
   - Diğer veri kaynaklarını bir özel dosyayla (örneğin, bir SharePoint sitesi veya Microsoft 365 Grubunu bir custo OneDrive custo veya account'daki veriler gibi yeniden yerleştirilsin, yerleştirilsin ve aransın) ile ilişkilendirmeniz gerekir.

   - Özel çalışanlara yasal [tutma](managing-custodian-communications.md) bildirimi Advanced eDiscovery iletişim iş akışını kullanabilirsiniz.

2. **[Veri kaynaklarından ilgili içeriği toplayın](create-draft-collection.md)**. Bir vakaya koruyucular ve özel olmayan veri kaynakları ekledikten sonra, bu veri kaynaklarında olayla ilgili olabilir içerik aramak için yerleşik koleksiyonlar aracını kullanın. Arama sonuçlarını, büyük olasılıkla [olayla ilgili olan](building-search-queries.md) verilerle birlikte geri dönen arama sorguları oluşturmak için anahtar sözcükler, özellikler ve koşullar kullanırsınız. Şunları da yapabilirsiniz:

   - Sonuçları [daraltmak için](collection-statistics-reports.md) koleksiyonu daraltmanıza yardımcı olacak koleksiyon istatistiklerini görüntüleme.

   - Uygun verilerin bulunıp buluna olmadığını hızlı bir şekilde doğrulamak için koleksiyonun bir örneğini önizle.

   - Sorguyu düzeltin ve koleksiyonu yeniden çalıştırabilirsiniz.

3. **[Koleksiyonu gözden geçirme kümesine kaydetme](commit-draft-collection.md)**. Bir aramanın istenen verileri döndür yönelik olduğunu yapılandırdıktan ve doğruladıktan sonra, bir sonraki adım arama sonuçlarını gözden geçirme kümesine eklemektir. Gözden geçirme kümesine veri eklerken, öğeler özgün konumlarından güvenli bir Azure Depolama Alanı'Depolama kopyalanır. Gözden geçirme kümesinde öğeleri gözden geçirme ve çözümlemeye yönelik kapsamlı ve hızlı aramalar için veriler yeniden dizine alındı. Buna ek olarak, [gözden geçirme kümesine Office 365 olmayan veriler de ebilirsiniz](load-non-office-365-data-into-a-review-set.md).

   Ayrıca, konuşma gözden geçirme kümesi olarak adlandırılan, veri ek adında, özel bir gözden geçirme *kümesi de içerir*. Bu tür incelemeler, konuşmaların yeniden yapılandırılmasını, gözden geçirmesini ve dışarı aktarması için konuşma becerileri Microsoft Teams. Daha fazla bilgi için bkz[. Advanced eDiscovery](conversation-review-sets.md).

4. **Gözden geçirme kümesinde verileri gözden geçirme ve çözümleme**. Artık veriler bir gözden geçirme kümesinde olduğu için, veri kümesini araştıran durumla en ilgili olayla ilgili olarak azaltmayı amaç edinerek olay verilerini görüntülemek ve çözümlemek için çok çeşitli araç ve yetenekleri kullanabilirsiniz. Burada, bu işlem sırasında kullanabileceğiniz bazı araç ve becerilerin listesi ve ve listeyi kullanabilirsiniz.

   - [Belgeleri görüntüleme](view-documents-in-review-set.md). Bu, her belgenin meta verilerini gözden geçirme kümesinde görüntülemeyi ve belgeyi yerel sürümünde veya metin sürümünde görüntülemeyi içerir.

   - [Sorgu ve filtre oluşturma](review-set-search.md). Çeşitli arama ölçütlerini kullanarak arama sorguları oluşturabilirsiniz (tüm dosya meta verileri özelliklerinde [](document-metadata-fields-in-advanced-ediscovery.md) arama yapma özelliği de içinde olmak üzere, olay verilerini olayla en ilgili olanla daha fazla daraltır ve daraltabilirsiniz). Bu sonuçları daha da geliştirmek için, arama sorgusunun sonuçlarına hızla başka koşullar uygulamak için de gözden geçirme kümesi filtrelerini kullanabilirsiniz. 

   - [Etiketleri oluşturun ve kullanın](tagging-documents.md). Hangi etiketlerin yanıt vereni (veya yanıtsız olduğunu) tanımlamak için bir gözden geçirme kümesinde belgelere etiketler uygulayabilir ve ardından etiketlenmiş belgeleri eklemek veya dışarıda tutmak için arama sorguları oluştururken bu etiketleri kullanabilirsiniz. Ayrıca, hangi belgelerin dışarı aktarılamayacaklarını belirlemek için etiketleme de abilirsiniz.

   - [Belgelere ek açıklama veya belgeyi yeniden açıklama.](view-documents-in-review-set.md#annotate-view) Bir gözden geçirmede belgelere ek açıklama eklemek ve belgelerde içeriği iş ürünü olarak yeniden işlem yapmak için ek açıklama aracını kullanabilirsiniz. Belgenin tam olarak olmayan yerel sürümünü dışarı aktarma riskini azaltmak için, inceleme sırasında açıklamalı veya tam olarak ek açıklamalı bir belgenin PDF sürümünü oluşturtük.

   - [Vaka verilerini çözümle](analyzing-data-in-review-set.md). Bu Advanced eDiscovery çözümleme işlevselliği güçlü bir işlevdir. Gözden geçirme kümesinde veriler üzerinde çözümlemeler çalıştırdikten sonra, incelemeniz gereken belge hacmini azaltmaya yardımcı olacak, yakın yineleme algılama, e-posta dizileri ve temalar gibi çözümlemeler gerçekleştiriz. Ayrıca, çalışan analizlerin sonucu özetleyen bir Analiz raporları da oluşturuz. Daha önce de açıklanması gibi, çözümlemelerde [avukatlık ayrıcalık algılama modeli de çalıştırıldı](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Vaka verilerini dışarı aktarma ve indirme**. Veri toplama, gözden geçirme ve çözümlemenin son adımı, verileri dış inceleme için Advanced eDiscovery gözden geçirmek veya araştırma ekibinin dışından kişiler tarafından gözden geçirmektir. Verileri dışarı aktarma, iki adımlı bir işlemdir. İlk adım, gözden geçirme [](export-documents-from-review-set.md) kümesi dışında olan verileri dışarı aktararak farklı bir Azure Depolama Depolama (Microsoft tarafından sağlanan veya sizin yönetilen bir konum) kopyalamaktır. Ardından, Azure Depolama Gezgini [yerel bir](download-export-jobs.md) bilgisayara indirmek için bu uygulamayı kullanırsınız. Dışarı aktarıldı veri dosyalarına ek olarak, dışarı aktarma paketinin içinde de dışarı aktarma raporu, özet rapor ve hata raporu yer alır.

## <a name="advanced-ediscovery-architecture"></a>Advanced eDiscovery mimarisi

Burada, Advanced eDiscovery uç-uç iş akışını tek coğrafi ortamda ve çok coğrafi bir ortamda gösteren bir mimari diyagramı ve Elektronik Bulma Başvuru Modeli ile uyumlu uç uç veri akışını gösteren bir mimari diyagramı ve [bulunmaktadır.](overview-ediscovery-20.md#advanced-ediscovery-alignment-with-the-electronic-discovery-reference-model)

[![Model posteri: Advanced eDiscovery Mimari'ye Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Resim olarak görüntüleme](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[PDF dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Visio dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
