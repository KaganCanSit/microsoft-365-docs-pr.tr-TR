---
title: otomatik araştırmanın sonuçlarını Microsoft 365
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, düzeltme, eylemler
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365'da otomatik bir araştırma sırasında ve sonrasında sonuçları ve önemli bulguları görüntüleyebilirsiniz.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b99573f73d5b53b6ea0e8d0cd1e44b539fa47db9
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649087"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Microsoft 365'da otomatik araştırmanın ayrıntıları ve sonuçları

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

[Office 365 için Microsoft Defender'de otomatik bir araştırma](office-365-air.md) gerçekleştiğinde, otomatik araştırma işlemi sırasında ve sonrasında bu araştırmayla ilgili ayrıntılar sağlanır.[](defender-for-office-365.md) Gerekli izinlere sahipseniz bu ayrıntıları Microsoft 365 Defender portalında görüntüleyebilirsiniz. Araştırma ayrıntıları size güncel durumu ve bekleyen eylemleri onaylama olanağı sağlar.

> [!TIP]
> Microsoft 365 Defender portalındaki yeni, birleşik araştırma sayfasına göz atın. Daha fazla bilgi edinmek için bkz. [(YENİ!) Birleşik araştırma sayfası](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>Araştırma durumu

Araştırma durumu, analizin ve eylemlerin ilerleme durumunu gösterir. Araştırma çalıştırılırken durum, tehditlerin bulunup bulunmadığını ve eylemlerin onaylanıp onaylanmadığını gösterecek şekilde değişir.

|Durum|Açıklama|
|---|---|
|**Başlıyor**|Araştırma tetiklendi ve çalışmaya başlamayı bekliyor.|
|**Çalışan**|Araştırma süreci başlamıştır ve devam etmektedir. Bu durum [, bekleyen eylemler](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) onaylandığında da oluşur.|
|**Tehdit Bulunamadı**|Araştırma tamamlandı ve hiçbir tehdit (kullanıcı hesabı, e-posta iletisi, URL veya dosya) belirlendi. <p> **İpucu**: Bir şeyin eksik olduğundan şüpheleniyorsanız (hatalı negatif gibi), [Tehdit Gezgini'ne](threat-explorer.md) kullanarak işlem yapabilirsiniz.|
|**Bulunan Tehditler**|Otomatik araştırma sorunları buldu, ancak bu sorunları çözmek için belirli bir düzeltme eylemi yok. <p> **Tehdit bulundu** durumu, bir tür kullanıcı etkinliği tanımlandığında ancak kullanılabilir temizleme eylemi olmadığında oluşabilir. Örnek olarak aşağıdaki kullanıcı etkinliklerinden herhangi biri verilebilir: <ul><li>[Veri kaybı önleme](../../compliance/dlp-learn-about-dlp.md) olayı</li><li>Anomali gönderen bir e-posta</li><li>Gönderilen kötü amaçlı yazılım</li><li>Gönderilen kimlik avı</li></ul> <p> Araştırmada düzeltilmesi gereken kötü amaçlı URL' ler, dosyalar veya e-posta iletileri bulunamadı ve iletme kurallarını veya temsilci seçmeyi kapatma gibi düzeltilmesi gereken bir posta kutusu etkinliği bulunamadı. <p> **İpucu**: Bir şeyin kaçırıldığından şüpheleniyorsanız (hatalı negatif gibi), [Tehdit Gezgini'ne](threat-explorer.md) kullanarak araştırma yapabilir ve işlem yapabilirsiniz|
|**Sistem Tarafından Sonlandırıldı**|Soruşturma durduruldu. Araştırma birkaç nedenden dolayı durdurulabilir: <ul><li>Araştırmanın bekleyen eylemlerinin süresi doldu. Bir hafta boyunca onay beklendikten sonra bekleyen eylemler zaman aşımına uğradı</li><li>Çok fazla eylem var. Örneğin, kötü amaçlı URL'lere tıklayan çok fazla kullanıcı varsa, araştırmanın tüm çözümleyicileri çalıştırma becerisini aşabilir, böylece araştırma durdurulabilir</li></ul> <p> **İpucu**: Bir araştırma eylemler gerçekleştirilmeden önce durursa tehditleri bulmak ve ele almak için [Tehdit Gezgini'ne](threat-explorer.md) kullanmayı deneyin.|
|**Bekleyen Eylem**|Araştırmada kötü amaçlı e-posta, kötü amaçlı URL veya riskli posta kutusu ayarı gibi bir tehdit ve bu tehdidi düzeltmeye yönelik bir eylem [onay bekliyor](air-review-approve-pending-completed-actions.md). <p> Karşılık gelen eylem içeren herhangi bir tehdit bulunduğunda **Bekleyen Eylem** durumu tetikleniyor. Ancak, bir araştırma çalıştırıldığında bekleyen eylemlerin listesi artabilir. Diğer öğelerin hala tamamlanmasının beklenip beklenmediğini görmek için araştırma ayrıntılarını görüntüleyin.|
|**Düzeltilmiş**|Araştırma tamamlandı ve tüm düzeltme eylemleri onaylandı (tamamen düzeltildiği kaydedildi). <p> **NOT**: Onaylanan düzeltme eylemleri, eylemlerin gerçekleştirilmesini engelleyen hatalara neden olabilir. Düzeltme eylemlerinin başarıyla tamamlanıp tamamlanmadığına bakılmaksızın, araştırma durumu değişmez. Araştırma ayrıntılarını görüntüleyin.|
|**Kısmen Düzeltilmiş**|Araştırma, düzeltme eylemleriyle sonuçlandı ve bazıları onaylandı ve tamamlandı. Diğer eylemler hala [beklemede](air-review-approve-pending-completed-actions.md).|
|**Başarısız**|En az bir araştırma çözümleyicisi düzgün tamamlanamadı bir sorunla karşılaştı. <p> **NOT** Düzeltme eylemleri onaylandıktan sonra bir araştırma başarısız olursa, düzeltme eylemleri yine de başarılı olmuş olabilir. Araştırma ayrıntılarını görüntüleyin.|
|**Azaltma Tarafından Kuyruğa Alındı**|Bir soruşturma kuyrukta tutuluyor. Diğer araştırmalar tamamlandığında kuyruğa alınmış araştırma başlar. Azaltma, düşük hizmet performansını önlemeye yardımcı olur.  <p> **İpucu**: Bekleyen eylemler kaç yeni araştırmanın çalışabileceğini sınırlayabilir. [Bekleyen eylemleri onaylamayı (veya reddetmeyi)](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) unutmayın.|
|**Azaltma Ile Sonlandırıldı**|Bir araştırma kuyrukta çok uzun süre tutulursa durdurulur. <p> **İpucu**: [Tehdit Gezgini'nden bir araştırma başlatabilirsiniz](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|

## <a name="view-details-of-an-investigation"></a>Araştırmanın ayrıntılarını görüntüleme

1. Microsoft 365 Defender portalına (<https://security.microsoft.com>) gidin ve oturum açın.
2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.
3. **Beklemede** veya **Geçmiş** sekmelerinde bir eylem seçin. Açılır pencere bölmesi açılır.
4. Açılır bölmede **Araştırma sayfasını aç'ı** seçin. 
5. Araştırma hakkında daha fazla bilgi edinmek için çeşitli sekmeleri kullanın.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Araştırmayla ilgili uyarıyla ilgili ayrıntıları görüntüleme

Bazı uyarı türleri, Microsoft 365 otomatik araştırmayı tetikler. Daha fazla bilgi edinmek için bkz. [Otomatik araştırma tetikleyen uyarı ilkeleri](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Microsoft 365 Defender portalına (<https://security.microsoft.com>) gidin ve oturum açın.
2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.
3. **Beklemede** veya **Geçmiş** sekmelerinde bir eylem seçin. Açılır pencere bölmesi açılır.
4. Açılır bölmede **Araştırma sayfasını aç'ı** seçin.
5. Bu araştırmayla ilişkili tüm uyarıların listesini görüntülemek için **Uyarılar** sekmesini seçin.
6. Açılan bölmeyi açmak için listeden bir öğe seçin. Burada uyarı hakkında daha fazla bilgi görüntüleyebilirsiniz.

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları göz önünde bulundurun

- E-posta sayıları araştırma sırasında hesaplanır ve araştırma açılır öğelerini açtığınızda (temel alınan sorguya göre) bazı sayılar yeniden hesaplanır.

- E-posta sekmesindeki e-posta kümeleri için gösterilen **e-posta** sayısı ve küme açılır öğesinde gösterilen e-posta miktarı değeri araştırma sırasında hesaplanır ve değişmez.

- E-posta kümesi açılır öğesinin **E-posta** sekmesinin en altında gösterilen e-posta sayısı ve Gezgin'de gösterilen e-posta iletilerinin sayısı, araştırmanın ilk analizinden sonra alınan e-posta iletilerini yansıtır.

  Bu nedenle, özgün 10 e-posta iletisi miktarını gösteren bir e-posta kümesi, araştırma analizi aşaması arasında beş e-posta iletisi daha geldiğinde ve yönetici araştırmayı gözden geçirirken toplam 15 e-posta listesi gösterir. Benzer şekilde, Office 365 için Microsoft Defender Plan 2'deki verilerin süresi denemeler için yedi gün sonra ve ücretli lisanslar için 30 gün sonra dolduğundan, eski araştırmalarda Gezgin sorgularının gösterdiğinden daha yüksek sayımlar gösterilmeye başlanabilir.

  Hem geçmiş hem de geçerli sayıların farklı görünümlerde gösterilmesi, araştırma sırasındaki e-posta etkisini ve düzeltme çalıştırana kadar geçerli etkiyi göstermek için yapılır.

- E-posta bağlamında, araştırmanın bir parçası olarak bir birim anomali tehdit yüzeyi görebilirsiniz. Birim anomalisi, önceki zaman çerçevelerine kıyasla araştırma olayı süresi boyunca benzer e-posta iletilerinde ani artış olduğunu gösterir. E-posta trafiğinde belirli özelliklerle (örneğin, konu ve gönderen etki alanı, gövde benzerliği ve gönderen IP'si) ani bir artış, e-posta kampanyalarının veya saldırılarının başlangıcının tipik bir örneğidir. Ancak toplu, istenmeyen posta ve meşru e-posta kampanyaları genellikle bu özellikleri paylaşır.

- Birim anomalileri olası bir tehdidi temsil eder ve buna göre virüsten koruma motorları, patlama veya kötü amaçlı itibar kullanılarak tanımlanan kötü amaçlı yazılım veya kimlik avı tehditlerine kıyasla daha az ciddi olabilir.

- Her eylemi onaylamanız gerekmez. Önerilen eylemi kabul etmiyorsanız veya kuruluşunuz belirli eylem türlerini seçmiyorsa, **Eylemleri reddet'i** seçebilir veya yalnızca bunları yoksayabilir ve hiçbir işlem gerçekleştiremezsiniz.

- Tüm eylemlerin onaylanması ve/veya reddedilmesi, araştırmanın tamamen kapanmasına (durum düzeltilir) olanak tanırken, bazı eylemlerin tamamlanmamış olması, araştırma durumunun kısmen düzeltilmiş duruma dönüşmesine neden olur.

## <a name="next-steps"></a>Sonraki adımlar

- [Bekleyen eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
