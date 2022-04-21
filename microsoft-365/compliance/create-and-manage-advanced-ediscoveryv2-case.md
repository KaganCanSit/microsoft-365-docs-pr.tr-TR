---
title: Microsoft 365'de eBulma (Premium) servis taleplerini oluşturma ve yönetme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/08/2022
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
description: Bu makalede, Microsoft Purview eKeşif (Premium) servis taleplerinin nasıl oluşturulacağı ve yönetildiği açıklanır. İlk adım bir servis talebi oluşturmak ve eBulma (Premium) özelliklerini ve işlevselliğini kullanmaya başlamaktır.
ms.openlocfilehash: 294a07c2f43559943482c3e17c98289f41dff7bc
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999288"
---
# <a name="create-and-manage-an-ediscovery-premium-case"></a>eBulma (Premium) olayı oluşturma ve yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eBulma 'yı (Premium) ayarladıktan ve kuruluşunuzdaki [eBulma yöneticilerine servis taleplerini yönetecek izinler atadıktan](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) sonra, sonraki adım bir servis talebi oluşturmak ve yönetmektir.

Bu makalede ayrıca, yasal bir olay veya diğer araştırma türleri için eKeşif (Premium) iş akışını yönetmek üzere kullanım örneklerine üst düzey bir genel bakış sağlanır.

## <a name="create-a-case"></a>Servis talebi oluşturma

Servis talebi oluşturmak ve üye eklemek için aşağıdaki adımları tamamlayın. Servis talebini oluşturan kullanıcı otomatik olarak üye olarak eklenir. Servis talebi üyeleri Olaya Microsoft Purview uyumluluk portalından erişebilir ve eBulma (Premium) görevlerini gerçekleştirebilir.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalına</a> gidin ve eBulma izinleri atanmış kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın. Kuruluş Yönetimi rol grubunun üyeleri de eBulma (Premium) servis talepleri oluşturabilir.

2. Uyumluluk portalının sol gezinti bölmesinde **Tümünü göster'e** tıklayın ve **sonra eBulmaGeldi'yi** >  seçin ve ardından <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">**Servis Talepleri** sekmesini</a> seçin.

3. **Servis talebi oluştur'u** seçin.

4. **Yeni eBulma servis talebi** açılır sayfasında, servis talebine bir ad verin (gerekli) ve ardından isteğe bağlı bir servis talebi numarası ve açıklama yazın. Servis talebi adı kuruluşunuzda benzersiz olmalıdır.

5. Servis talebini oluşturmak için **Kaydet'e** tıklayın.

   Yeni servis talebi oluşturulur ve yeni servis talebindeki **Ayarlar** sekmesi görüntülenir.

6. Ayarlar **sekmesindeki** **Access & izinleri** kutucuğunda **Seç'e** tıklayın.

7. **Bu olayı yönet** açılır sayfasındaki **Üyeleri yönet'in** altında **, olaya** üye eklemek için Ekle'ye tıklayın.

8. Kişi listesinde, servis talebine eklemek istediğiniz kişilerin adlarının yanındaki onay kutusunu seçin. Daha önce açıklandığı gibi, servis talebine eklediğiniz kişilere uygun eBulma izinlerinin atandığından emin olun.

9. Olaya üye olarak eklenecek kişileri seçtikten sonra **Ekle'ye** tıklayın.

10. **Yeni servis talebi** üyeleri listesini kaydetmek için Bu olayı yönet açılır sayfasında **Kaydet'e** tıklayın.

11. Servis talebi giriş sayfasına gitmek için **Giriş** sekmesine tıklayın.

## <a name="manage-the-workflow"></a>İş akışını yönetme

eBulma (Premium) kullanmaya başlamanız için [yaygın eBulma uygulamalarıyla](advanced-ediscovery-edrm.md) uyumlu temel bir iş akışı aşağıdadır. Bu adımların her birinde, keşfedebileceğiniz bazı genişletilmiş eBulma (Premium) işlevlerini de vurgulayacağız.

![eBulma (Premium) iş akışı.](../media/AeDWorkflow.png)

1. **[Olaya koruyucular](add-custodians-to-case.md) ve [gözetimsiz veri kaynakları](non-custodial-data-sources.md) ekleyin**. Olay oluşturduktan sonraki ilk adım, koruyucu eklemektir. *Koruyucu*, olayla ilgili olabilecek bir belgenin veya elektronik dosyanın yönetim denetimine sahip bir kişidir. Ayrıca, belirli bir kullanıcıyla ilişkilendirilmeyen ancak servis talebiyle ilgili olabilecek veri kaynakları ekleyebilirsiniz.

   Bir olaya koruyucu eklerken gerçekleşen (veya yapabileceğiniz) bazı şeyler şunlardır:

   - Koruyucunun Exchange posta kutusunda, OneDrive hesabındaki ve koruyucunun üyesi olduğu Microsoft Teams veya Yammer gruplarındaki veriler, olayda koruma verileri olarak "işaretlenebilir".
  
   - Koruyucu verileri yeniden dizine alınır ( *Gelişmiş dizin oluşturma* adlı bir işlem tarafından). Bu, sonraki adımda aramayı iyileştirmeye yardımcı olur.
  
   - Koruyucu verileri ayrı tutabilirsiniz. Bu, araştırma sırasında olayla ilgili olabilecek verileri korur.
  
   - Diğer veri kaynaklarını bir koruyucuyla ilişkilendirebilirsiniz (örneğin, bir SharePoint sitesini veya Microsoft 365 Grubunu bir koruyucuyla ilişkilendirebilirsiniz), böylece bu veriler aynı koruyucunun posta kutusu veya OneDrive hesabındaki veriler gibi yeniden dizine eklenebilir, beklemeye alınıp aranabilir.

   - eBulma(Premium) içindeki [iletişim iş akışını](managing-custodian-communications.md) kullanarak koruyuculara yasal saklama bildirimi gönderebilirsiniz.

2. **[Veri kaynaklarından ilgili içeriği toplayın](create-draft-collection.md)**. Bir servis talebine koruyucular ve gözetimsiz veri kaynakları ekledikten sonra, bu veri kaynaklarında olayla ilgili olabilecek içerikleri aramak için yerleşik koleksiyonlar aracını kullanın. Büyük olasılıkla servis talebiyle ilgili olan verilerle arama sonuçları döndüren [arama sorguları oluşturmak](building-search-queries.md) için anahtar sözcükleri, özellikleri ve koşulları kullanırsınız. Şunları da yapabilirsiniz:

   - Sonuçları daraltmak için bir koleksiyonu daraltmanıza yardımcı olabilecek koleksiyon [istatistiklerini](collection-statistics-reports.md) görüntüleyin.

   - İlgili verilerin bulunup bulunmadığını hızla doğrulamak için koleksiyonun bir örneğini önizleme.

   - Sorguyu düzeltin ve koleksiyonu yeniden çalıştırın.

3. **[Koleksiyonu bir gözden geçirme kümesine işleme](commit-draft-collection.md)**. Bir aramanın istenen verileri döndürdüğünü yapılandırıp doğruladıktan sonra, sonraki adım arama sonuçlarını bir gözden geçirme kümesine eklemektir. Bir gözden geçirme kümesine veri eklediğinizde, öğeler özgün konumlarından güvenli bir Azure Depolama konumuna kopyalanır. Veriler, gözden geçirme kümesindeki öğeleri gözden geçirirken ve çözümlerken kapsamlı ve hızlı aramalar için iyileştirmek üzere yeniden dizine eklenir. Ayrıca, [gözden geçirme kümesine Office 365 olmayan veriler de ekleyebilirsiniz](load-non-office-365-data-into-a-review-set.md).

   Ayrıca, veri ekleyebileceğiniz ve konuşma gözden geçirme kümesi olarak adlandırılan özel bir *gözden geçirme kümesi de vardır*. Bu tür inceleme kümeleri, Microsoft Teams'dakiler gibi yazışma yazışmalarını yeniden derlemek, gözden geçirmek ve dışarı aktarmak için konuşma yeniden yapılandırma özellikleri sağlar. Daha fazla bilgi için bkz. [eBulma'da (Premium) konuşmaları gözden geçirme](conversation-review-sets.md).

4. **Bir gözden geçirme kümesindeki verileri gözden geçirin ve analiz edin**. Veriler bir gözden geçirme kümesinde olduğuna göre, veri kümesini araştırdığınız servis talebiyle en alakalı duruma düşürmek amacıyla büyük/küçük harf verilerini görüntülemek ve analiz etmek için çok çeşitli araçlar ve özellikler kullanabilirsiniz. Bu işlem sırasında kullanabileceğiniz bazı araç ve özelliklerin listesi aşağıdadır.

   - [Belgeleri görüntüleme](view-documents-in-review-set.md). Bu, her belgenin meta verilerini bir gözden geçirme kümesinde görüntülemeyi ve belgeyi yerel sürümünde veya metin sürümünde görüntülemeyi içerir.

   - [Sorgular ve filtreler oluşturun](review-set-search.md). Çeşitli arama ölçütlerini kullanarak arama sorguları oluşturursunuz (servis talebi verilerini büyük/küçük harfe en uygun değere daha fazla daraltmak ve silmek için tüm [dosya meta veri özelliklerini](document-metadata-fields-in-advanced-ediscovery.md) arama özelliği dahil). Ayrıca, bu sonuçları daha da daraltmak için bir arama sorgusunun sonuçlarına hızlı bir şekilde başka koşullar uygulamak için gözden geçirme kümesi filtrelerini de kullanabilirsiniz. 

   - [Etiket oluşturma ve kullanma](tagging-documents.md). Bir gözden geçirme kümesindeki belgelere etiket uygulayarak hangilerinin yanıt veren (veya büyük/küçük harfe yanıt vermeyen) olduğunu belirleyebilir ve ardından etiketli belgeleri dahil etmek veya hariç tutmak için arama sorguları oluştururken bu etiketleri kullanabilirsiniz. Ayrıca hangi belgeleri dışarı aktarabileceğinizi belirlemek için etiketleme yapabilirsiniz.

   - [Belgelere not ekleme ve belgeleri yeniden düzenleme](view-documents-in-review-set.md#annotate-view). Bir incelemede ek açıklama aracını kullanarak belgelere açıklama ekleyebilir ve belgelerdeki içeriği iş ürünü olarak yeniden düzenleyebilirsiniz. Belgenin kaydedilmemiş yerel sürümünü dışarı aktarma riskini azaltmak için inceleme sırasında açıklamalı veya yeniden düzenlenen bir belgenin PDF sürümünü oluşturuyoruz.

   - [Büyük/küçük harf verilerini analiz etme](analyzing-data-in-review-set.md). eBulma (Premium) içindeki analiz işlevselliği güçlüdür. Gözden geçirme kümesindeki veriler üzerinde analiz çalıştırdıktan sonra, gözden geçirmeniz gereken belge hacmini azaltmaya yardımcı olabilecek neredeyse yinelenen algılama, e-posta yazışması ve temalar gibi analizler yaparız. Ayrıca, analiz çalıştırmanın sonucunu özetleyen bir Analiz raporları da oluştururuz. Daha önce açıklandığı gibi, analiz çalıştırmak [ayrıca avukat-istemci ayrıcalık algılama modelini](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model) çalıştırır.

5. **Servis talebi verilerini dışarı aktarma ve indirme**. Olay verilerini topladıktan, gözden geçirdikten ve analiz ettikten sonra son adım, eBulma (Premium) dışında dış gözden geçirme veya araştırma ekibi dışındaki kişiler tarafından gözden geçirme amacıyla dışarı aktarmaktır. Verileri dışarı aktarmak iki adımlı bir işlemdir. İlk adım, verileri gözden geçirme kümesinden [dışarı aktarmak](export-documents-from-review-set.md) ve farklı bir Azure Depolama konumuna kopyalamaktır (Microsoft tarafından sağlanan veya kuruluşunuz tarafından yönetilen bir konum). Ardından verileri yerel bir bilgisayara [indirmek](download-export-jobs.md) için Azure Depolama Gezgini kullanırsınız. Dışarı aktarılan veri dosyalarına ek olarak, dışarı aktarma paketinin içeriği bir dışarı aktarma raporu, bir özet raporu ve bir hata raporu da içerir.

## <a name="ediscovery-premium-architecture"></a>eBulma (Premium) mimarisi

Burada eBulma (Premium) uçtan uca iş akışını tek coğrafi bir ortamda ve çok coğrafi bir ortamda ve [Elektronik Bulma Başvuru Modeli](overview-ediscovery-20.md#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model) ile uyumlu uçtan uca veri akışını gösteren bir mimari diyagramı yer alır.

[![Model posteri: Microsoft 365'de eBulma (Premium) Mimarisi.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Resim olarak görüntüle](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[PDF dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Visio dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
