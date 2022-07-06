---
title: eBulma'da işleri yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: eBulma (Premium) işleri, çeşitli eBulma (Premium) görevlerini gerçekleştirmeyle ilgili uzun süre çalışan işlemlerin durumunu izlemenize yardımcı olur.
ms.openlocfilehash: 9be48325e3103e8f4e349c32cc559db36e42a05e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639742"
---
# <a name="manage-jobs-in-ediscovery-premium"></a>eBulma'da işleri yönetme (Premium)

Microsoft Purview eKeşif(Premium) içindeki bir servis talebinin **İşler** sekmesinde izlenen işlerin (genellikle uzun süre çalışan işlemlerdir) listesi aşağıdadır. Bu işler, servis taleplerini kullanırken ve yönetirken kullanıcı eylemleri tarafından tetiklenir.

|İş türü|Açıklama|
|---|---|
|Gözden geçirme kümesine veri ekleme|Kullanıcı bir gözden geçirme kümesine koleksiyon ekler. Bu iş iki alt işten oluşur: <ul><li>**Dışarı Aktar** - Koleksiyondaki öğelerin listesi oluşturulur.</li><li>**Alma & Dizin Oluşturma** - Koleksiyondaki arama sorgusuyla eşleşen öğeler bir Azure Depolama konumuna kopyalanır ( *alma* adlı bir işlemde) ve ardından Azure Depolama konumundaki öğeler yeniden dizine alınır. Bu yeni dizin, veri kümesindeki öğeleri sorgularken ve analiz ederken kullanılır.</li><ul> <p> Daha fazla bilgi için bkz. [Gözden geçirme kümesine arama sonuçları ekleme](add-data-to-review-set.md).|
|Başka bir gözden geçirme kümesine veri ekleme|Kullanıcı, bir gözden geçirme kümesindeki belgeleri aynı durumda farklı bir gözden geçirme kümesine ekler. Daha fazla bilgi için bkz. [Başka bir gözden geçirme kümesinden bir gözden geçirme kümesine veri ekleme](add-data-to-review-set-from-another-review-set.md).|
|Gözden geçirme kümesine Microsoft 365 dışı veriler ekleme|Kullanıcı, Microsoft 365 dışı verileri bir gözden geçirme kümesine yükler. Bu işlem sırasında veriler de dizine eklenir. Örneğin, şirket içi dosya sunucusundan veya istemci bilgisayardan gelen dosyalar bir gözden geçirme kümesine yüklenir. Daha fazla bilgi için bkz [. Microsoft 365 dışı verileri gözden geçirme kümesine yükleme](load-non-office-365-data-into-a-review-set.md).|
|Gözden geçirme kümesine düzeltilmiş veriler ekleme|İşleme hataları olan veriler düzeltilir ve bir gözden geçirme kümesine geri yüklenir. Daha fazla bilgi için bkz.: <ul><li>[Verileri işlerken hata düzeltme](error-remediation-when-processing-data-in-advanced-ediscovery.md)</li><li>[Tek öğede hata düzeltme](single-item-error-remediation.md)</li></ul>|
|Yük kümelerini karşılaştırma|Kullanıcı, bir gözden geçirme kümesindeki farklı yük kümeleri arasındaki farklara bakar. Yük kümesi, bir gözden geçirme kümesine veri ekleme örneğidir. Örneğin, aynı gözden geçirme kümesine iki farklı aramanın sonuçlarını eklerseniz her biri bir yük kümesini temsil eder.|
|Konuşma yeniden yapılandırma|Kullanıcı arama sonuçlarını bir konuşma gözden geçirme kümesine eklediğinde, Microsoft Teams gibi hizmetlerdeki anlık ileti *konuşmaları (yazışmalı konuşmalar* olarak da adlandırılır) PDF dosyasında yeniden oluşturulur. Bu iş, kullanıcı eylem > Bir gözden geçirme kümesinde **konuşma PDF'leri oluştur'a** tıkladığında da tetikleniyor. Daha fazla bilgi için bkz. [eBulma(Premium)'da konuşmaları gözden geçirme](conversation-review-sets.md).
|Redakte edilmiş belgeleri PDF'ye dönüştürme|Bir kullanıcı bir gözden geçirme kümesindeki bir belgeye not ekledikten ve bir bölümünü yeniden dağıttıktan sonra, redakte edilmiş belgeyi PDF dosyasına dönüştürmeyi seçebilir. Bu, belge sunu için dışarı aktarılırsa, yeniden dağıtılan bölümün görünür olmamasını sağlar. Daha fazla bilgi için bkz. [Belgeleri gözden geçirme kümesinde görüntüleme](view-documents-in-review-set.md).|
|Arama sonuçlarını tahmin etme|Kullanıcı bir taslak koleksiyonu oluşturup çalıştırdıktan veya yeniden çalıştırdıktan sonra, arama aracı arama sorgusuyla eşleşen öğeler için dizinde arama yaparak aramanın tüm öğelerinin sayısını ve toplam boyutunu ve aranan veri kaynaklarının sayısını içeren bir tahmin hazırlar.  Daha fazla bilgi için bkz. [Servis talebi için veri toplama](collecting-data-for-ediscovery.md).|
|Verileri dışarı aktarma için hazırlama|Kullanıcı, belgeleri gözden geçirme kümesinden dışarı aktarır. Dışarı aktarma işlemi tamamlandığında, dışarı aktarılan verileri yerel bir bilgisayara indirebilirler. Daha fazla bilgi için bkz. [Büyük/küçük harf verilerini dışarı aktarma](exporting-data-ediscover20.md).|
|Hata çözümlemeye hazırlanma|Kullanıcı bir dosyayı seçip bir servis talebinin **İşleme** sekmesindeki Hata görünümünde yeni bir hata düzeltmesi oluşturduğunda, işlemin ilk adımı işleme hatasına sahip dosyayı Microsoft bulutunda bir Azure Depolama konumuna yüklemektir. Bu iş, karşıya yükleme işleminin ilerleme durumunu izler. Hata düzeltme iş akışı hakkında daha fazla bilgi için bkz. [Verileri işlerken hata düzeltme](error-remediation-when-processing-data-in-advanced-ediscovery.md).|
|Arama önizlemesi hazırlanıyor|Kullanıcı yeni bir taslak koleksiyonu oluşturup çalıştırdıktan (veya var olan bir taslak koleksiyonu yeniden çalıştırdıktan) sonra, arama aracı önizlemesi kullanılabilecek örnek bir öğe alt kümesi (arama sorgusuyla eşleşen) hazırlar. Arama sonuçlarının önizlemesi, aramanın verimliliğini belirlemenize yardımcı olur.  Daha fazla bilgi için bkz. [Servis talebi için veri toplama](collecting-data-for-ediscovery.md#view-search-results-and-statistics).|
|Koruyucu verilerini yeniden dizine alma|Bir servis talebine bir koruyucu eklediğinizde, koruyucunun seçili veri kaynaklarında kısmen dizine alınan tüm öğeler *Gelişmiş dizin oluşturma* adlı bir işlem tarafından yeniden dizinlenir. Bu iş, bir servis talebinin **İşleme** sekmesinde **Dizini güncelleştir'e** tıkladığınızda ve koruyucu özellikleri açılır sayfasında belirli bir koruyucu için dizini güncelleştirdiğinizde de tetikler. Daha fazla bilgi için bkz. [Koruyucu verilerin gelişmiş dizin oluşturması](indexing-custodian-data.md).
|Analiz çalıştırma|Kullanıcı, bir gözden geçirme kümesindeki verileri neredeyse yinelenen algılama, e-posta iş parçacığı analizi ve tema analizi gibi eBulma (Premium) analiz araçlarını çalıştırarak analiz eder. Daha fazla bilgi için bkz [. Gözden geçirme kümesindeki verileri analiz etme](analyzing-data-in-review-set.md).|
|Belgeleri etiketleme|Bu iş, bir kullanıcı bir gözden geçirme kümesindeki belgeleri gözden geçirirken **Etiketleme panelinde Etiketleme** **işini başlat'a** tıkladığında tetikleniyor. Bir kullanıcı, gözden geçirme kümesindeki belgeleri etiketleyip belgeyi görüntüleme panelinde toplu olarak seçtikten sonra bu işi başlatabilir. Daha fazla bilgi için bkz. [Gözden geçirme kümesindeki belgeleri etiketleme](tagging-documents.md).|

## <a name="job-status"></a>İş durumu

Aşağıdaki tabloda işler için farklı durum durumları açıklanmaktadır.

|Durum|Açıklama|
|---|---|
|Gönderilmektedir|Yeni bir iş oluşturuldu.  İşin gönderildiği tarih ve saat **İşler** sekmesindeki **Oluşturuldu** sütununda görüntülenir.|
|Gönderim başarısız oldu|İş gönderimi başarısız oldu.  İşi tetikleyen eylemi yeniden çalıştırmayı denemelisiniz.|
|Devam ediyor|İş devam ediyor, işin ilerleme durumunu **İşler** sekmesinden izleyebilirsiniz.|
|Başarılı|İş başarıyla tamamlandı. İşin tamamlandığı tarih ve saat **İşler** sekmesindeki **Tamamlandı** sütununda görüntülenir.|
|Kısmen başarılı|İş başarılı oldu. Bu durum genellikle, iş bazı koruyucu veri kaynaklarında kısmen dizine alınmış veri ( *dizinlenmemiş veriler* olarak da adlandırılır) bulamadığında döndürülür.|
|Başarısız|İş başarısız oldu.  İşi tetikleyen eylemi yeniden çalıştırmayı denemelisiniz. İş ikinci kez başarısız olursa, Microsoft Desteği başvurmanızı ve işten destek bilgilerini sağlamanızı öneririz.|
