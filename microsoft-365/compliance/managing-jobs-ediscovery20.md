---
title: İş yerlerinde işleri Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Advanced eDiscovery işleri, çeşitli görev gerçekleştirmeyle ilgili uzun vadeli süreçlerin durumunu izlemenizi Advanced eDiscovery olur.
ms.openlocfilehash: 484f492ea56f6e75d3f5144dd41128c2cedfc914
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027536"
---
# <a name="manage-jobs-in-advanced-ediscovery"></a>İş yerlerinde işleri Advanced eDiscovery

burada, İş ve İş'te bir vakanın İş sekmesinde izlenen işlerin (genellikle uzun çalışan süreçler) listesi  Advanced eDiscovery. Bu işler, vakaları kullanırken ve yöneterek kullanıcı eylemleri tarafından tetiklenir.

| İş türü           | Açıklama     |
| :----------------- | :----------     |
|Gözden geçirme kümesine veri ekleme | Kullanıcı gözden geçirme kümesine koleksiyon ekler. Bu iş iki alt işden oluşur: </br>• **Dışarı** Aktar - Koleksiyondaki öğelerin listesi oluşturulur. </br>• **Ingestion & Dizin** oluşturma - Koleksiyondaki ve arama sorgusuyla eşleşmesi gereken öğeler Azure Depolama konuma (*ingestion* olarak adlandırılan bir işlemde) kopyalanır ve sonra Azure Depolama'nin bulunduğu konumdaki öğeler yeniden dizine alır. Bu yeni dizin, veri kümesinde öğeleri sorgular ve çözümlerken kullanılır. </br></br>Daha fazla bilgi için bkz [. Gözden geçirme kümesine arama sonuçları ekleme](add-data-to-review-set.md). |
|Başka bir gözden geçirme kümesine veri ekleme | Kullanıcı bir gözden geçirme kümesinden belgeleri aynı durumda farklı bir gözden geçirme kümesine ekler. Daha fazla bilgi için bkz [. Başka bir gözden geçirme kümesinden gözden geçirme kümesine veri ekleme](add-data-to-review-set-from-another-review-set.md).|
|Gözden geçirme Microsoft 365 olmayan veriler ekleme | Kullanıcı, gözden geçirme kümesine Microsoft 365 olmayan verileri karşıya yükler. Bu işlem sırasında veriler de dizine alındı. Örneğin, şirket içi dosya sunucusundan veya istemci bilgisayardan gelen dosyalar gözden geçirme kümesine karşıya yüklenen dosyalar. Daha fazla bilgi için [bkz. Gözden Microsoft 365 olmayan verileri yükleme](load-non-office-365-data-into-a-review-set.md).| 
|Gözden geçirme kümesine düzeltilen veri ekleme | İşleme hatalarının olduğu veriler düzeltildi ve gözden geçirme kümesine geri yüklenir. Daha fazla bilgi için bkz.:</br>• [Verileri işleme sırasında hata düzeltmesi](error-remediation-when-processing-data-in-advanced-ediscovery.md)</br>• [Tek öğe hatası düzeltmesi](single-item-error-remediation.md)| 
|Yükleme kümelerini karşılaştırma | Kullanıcı, gözden geçirme kümesinde farklı yükleme kümeleri arasındaki farklara bakarak değerlendirmede bulundu. Yükleme kümesi, gözden geçirme kümesine veri eklemenin bir örneğidir. Örneğin, aynı gözden geçirme kümesine iki farklı aramanın sonuçlarını eklersiniz, her biri bir yükleme kümesi temsil ediyor olabilir. |
|Konuşma sohbeti|Kullanıcı bir aramanın sonuçlarını konuşma gözden geçirme kümesine ekle olduğunda, Microsoft Teams gibi hizmetlerde yer alan anlık ileti konuşmaları (zincir konuşmalar olarak da *adlandırılan) PDF* dosyasında yeniden vardır. Kullanıcı bir gözden geçirme kümesinde Konuşma PDF'leri **oluşturma'ya >'e** tıkladığında da bu iş tetiklenir. Daha fazla bilgi için bkz[. Advanced eDiscovery](conversation-review-sets.md).
|Kırmızı işlemli belgeleri PDF'ye dönüştürme|Kullanıcı gözden geçirme kümesinde belgeye ek açıklama ek eklemesi ve belgenin bir bölümünü yeniden işlemden geçirmesi sonrasında, kırmızı işlem yapılan belgeyi PDF dosyasına dönüştürmeyi seçebilir. Bu işlem, belge sunu için dışarı aktarıldı mı yoksa kırmızı işlemle kalan kısmın görünmez olacağını sağlar. Daha fazla bilgi için bkz [. Gözden geçirme kümesinde belgeleri görüntüleme](view-documents-in-review-set.md). |
|Arama sonuçlarını tahmin | Kullanıcı bir taslak koleksiyonu oluşturduğunda ve çalıştırdığı zaman, arama aracı dizinde arama sorgusuna uygun öğeleri arar ve aramaya göre tüm öğelerin sayısını ve toplam boyutunu ve aranan veri kaynaklarının sayısını içeren bir tahmin hazırlar.  Daha fazla bilgi için bkz [. Vaka için veri toplama](collecting-data-for-ediscovery.md). | 
|Verileri dışarı aktarma için hazırlama | Kullanıcı gözden geçirme kümesinden belgeleri dışarı aktarıyor. Dışarı aktarma işlemi tamamlandığında, dışarı aktarilen verileri yerel bir bilgisayara indirebilirler. Daha fazla bilgi için bkz. [Vaka verilerini dışarı aktarma](exporting-data-ediscover20.md). | 
|Hata çözümüne hazırlanma |Kullanıcı bir dosyayı seçer ve bir vakanın İşleme sekmesindeki Hata görünümünde yeni bir hata düzeltmesi oluşturduğunda,  işleme hatası olan dosyayı Microsoft bulut üzerinde bir Azure Depolama konuma yüklemektir. Bu iş, karşıya yükleme işleminin ilerlemesini izler. Hata düzeltme iş akışı hakkında daha fazla bilgi için bkz [. Verileri işleme sırasında hata düzeltme](error-remediation-when-processing-data-in-advanced-ediscovery.md). | 
|Arama önizlemesi hazırlanıyor | Kullanıcı yeni bir taslak koleksiyonu oluşturduğunda (veya var olan bir taslak koleksiyonunu yeniden çalıştırdikten) sonra, arama aracı önizlemede 2013'e kadar olan öğelerin örnek bir alt kümesini (arama sorgusuyla eşler) hazırlar. Arama sonuçlarının önizlemesi, aramanın ne kadar etkili olduğunu belirlemenize yardımcı olur.  Daha fazla bilgi için bkz [. Vaka için veri toplama](collecting-data-for-ediscovery.md#view-search-results-and-statistics). | 
|Custo cust data yeniden dizin oluşturma | Bir vakaya bir custo custo custo bir işlemle yeniden dizine alınan tüm öğeler, Gelişmiş dizin oluşturma adı verilen bir işlemle yeniden *dizine seçilir*. Bu iş ayrıca, bir vakanın İşleme sekmesinde  Dizini güncelleştir'e  ve custo custout sayfasında belirli bir custo custout sayfasında dizin güncelleştirmeniz durumunda da tetiklenir. Daha fazla bilgi için bkz [. Koruyucu verileri gelişmiş dizin oluşturma](indexing-custodian-data.md).
|Çalışan analiz | Bir kullanıcı yakın yinelenen algılama, e-posta Advanced eDiscovery çözümlemesi ve temalar çözümlemesi gibi çözümleme araçlarını çalıştırarak bir gözden geçirme kümesinde verileri analiz eder. Daha fazla bilgi için bkz [. Gözden geçirme kümesinde verileri çözümleme](analyzing-data-in-review-set.md). | 
|Belgeleri etiketleme | Kullanıcı bir gözden geçirme kümesinde belgeleri gözden geçirerek Etiketleme panelinde İş etiketlemeye  başla'ya tıkladığında bu iş tetiklenir. Kullanıcı bir gözden geçirme kümesinde belgeleri etiketledikten ve belgeyi görüntüle panelinde toplu olarak seçerek bu işe başlayabilir. Daha fazla bilgi için bkz [. Belgeleri gözden geçirme kümesinde etiketleme](tagging-documents.md). | 
|||

## <a name="job-status"></a>İş durumu

Aşağıdaki tabloda, işlerin farklı durumları açıklandı.

| Durum           | Açıklama     |
| :----------------- | :----------     |
| Gönderildi | Yeni bir iş oluşturuldu.  İş gönderilen tarih ve saat, İşlerin **sekmesindeki Oluşturuldu** **sütununda görüntülenir** . |
| Gönderim başarısız oldu | İş gönderimi başarısız oldu.  Işi tetikleyen eylemi yeniden çalıştırmayı denemelisiniz. |
| Devam ediyor | İş devam ediyor. İşlerin ilerleme durumunu, İş sekmesinden **izleyebilirsiniz** . |
| Başarılı | İş başarıyla tamamlanmıştır. İşlerin tamamlandıktan sonra, işler sekmesinin **Tamamlandı sütununda** tarih ve **saat** görüntülenir. |
| Kısmen başarılı | İş başarılı oldu. Bu durum genellikle, işin bazı özel veri kaynaklarında kısmen dizine alınan verileri (dizine eksiz veriler olarak da *denir)* bulmamış olduğunda verilir.  |
| Başarısız | İş başarısız oldu.  Işi tetikleyen eylemi yeniden çalıştırmayı denemelisiniz. İş ikinci kez başarısız olursa, Microsoft Desteği'ne başvurarak işte destek bilgilerini sağlamanız önerilir. |
|||
