---
title: Microsoft 365'de otomatik bir araştırmanın sonuçlarını Microsoft 365
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
description: Çalışma değerlendirmesinde otomatik bir soruşturma Microsoft 365 sonra, sonuçları ve önemli bulguları görüntüabilirsiniz.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 54b9389d323c1e775b50bf63beaa33b0c4b0cae6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314091"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Bir ekipte otomatik bir soruşturmanın ayrıntıları ve Microsoft 365

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Office 365 [için](office-365-air.md) [Microsoft Defender'da](defender-for-office-365.md) otomatik soruşturma Office 365, bu soruşturmayla ilgili ayrıntılar otomatik soruşturma işlemi sırasında ve sonrasında kullanılabilir. Gerekli izinlere sahipsiniz, bu ayrıntıları portalda Microsoft 365 Defender. Araştırma ayrıntıları size güncel durumu ve bekleyen eylemleri onaylama olanağı sağlar.

> [!TIP]
> Microsoft 365 Defender portalında yeni, birleşik soruşturma Microsoft 365 Defender göz atın. Daha fazla bilgi edinmek için bkz [. (Yenİ!) Birleşik araştırma sayfası](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>İnceleme durumu

Araştırma durumu, çözümlemenin ve eylemlerin ilerleme durumunu gösterir. Araştırma çalıştırıldığı için durum, tehditlerin bulunıp buluna olmadığını ve eylemlerin onaylanıp onaylanmayacaklarını belirtecek şekilde değişir.

<br>

****

|Durum|Açıklama|
|---|---|
|**Başlıyor**|Araştırma tetiklenir ve çalışmaya başlamayı bekler.|
|**Çalışıyor**|İnceleme süreci başlamış ve devam etmektedir. Bu durum bekleyen eylemler [onaylanırsa da](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) ortaya çıkar.|
|**Tehdit Bulunamadı**|Araştırma tamamlandı ve herhangi bir tehdit (kullanıcı hesabı, e-posta iletisi, URL veya dosya) tanımlandı. <p> **İpucu**: Kaçırdığınız bir şey (hatalı negatif bir durum gibi) varsa, [Threat Explorer'ı kullanarak eyleme geçebilirsiniz](threat-explorer.md).|
|**Tehdit Bulundu**|Otomatik araştırma sorunları buldu, ancak bu sorunları çözmeye yönelik belirli bir düzeltme eylemi yok. <p> Tehdit **Bulundu durumu** , herhangi bir tür kullanıcı etkinliği tanımlandı ancak temizleme eylemleri kullanılamaz durumda olabilir. Örnek olarak aşağıdaki kullanıcı etkinliklerinden herhangi biri yer almaktadır: <ul><li>Veri [kaybı önleme](../../compliance/dlp-learn-about-dlp.md) olayı</li><li>E-posta gönderme anormalliği</li><li>Kötü amaçlı yazılım gönderildi</li><li>Gönderilen kimlik avı</li></ul> <p> Araştırmada düzeltmek için kötü amaçlı URL, dosya veya e-posta iletileri bulunamadı ve düzeltme amaçlı hiçbir posta kutusu etkinliği (iletme kuralları veya temsilci seçme gibi) bulunamıyor. <p> **İpucu**: Bir şeyin kaçırıldığına şüpheleniyorsanız (hatalı negatif bir durum gibi), Tehdit Gezgini'ni kullanarak araştırma ve [işlem](threat-explorer.md)|
|**Sistem tarafından Sonlandırıldı**|Araştırma durduruldu. Bir araştırma birkaç nedenle durabiliyor: <ul><li>Araştırmanın bekleyen eylemlerinin süresi doldu. Bir hafta için onay bekliyor sonra bekleyen eylemler zaman akışı</li><li>Çok fazla eylem var. Örneğin, kötü amaçlı URL'leri tıklatan çok fazla kullanıcı varsa, araştırmanın tüm çözümleyicileri çalıştırma becerisini aşarak araştırmanın durdurulmasını</li></ul> <p> **İpucu**: Eylemler gerçekleştirmeden önce bir soruşturma durdurulsa tehdit bulmak ve adresleri bulmak [için Threat Explorer'ı](threat-explorer.md) kullanmayı deneyin.|
|**Bekleyen Eylem**|Araştırma kötü amaçlı e-posta, kötü amaçlı URL veya riskli posta kutusu ayarı gibi bir tehdit ve onay bekliyor olan tehdide yönelik bir [düzeltme eylemi buldu](air-review-approve-pending-completed-actions.md). <p> İlgili **eyleme** yönelik herhangi bir tehdit bulunursa Bekleyen Eylem durumu tetiklenir. Ancak, bir araştırma çalıştırıldığı sürece bekleyen eylemler listesi artabilir. Diğer öğelerin hala tamamlanmayı beklemede olup olduğunu görmek için araştırma ayrıntılarını görüntüleme.|
|**Düzeltildi**|Araştırma tamamlandı ve tüm düzeltme eylemleri onaylandı (tamamen düzeltildi olarak not edildi). <p> **NOT**: Onaylanan düzeltme eylemlerinin, eylemlerin gerçekleştirlsini engelleyen hatalar olabilir. Düzeltme eylemlerinin başarıyla tamamlandıktan bağımsız olarak, soruşturma durumu değişmez. Araştırma ayrıntılarını görüntüleme.|
|**Kısmen Düzeltildi**|İnceleme sonucunda düzeltme eylemleri ve bazıları onaylandı ve tamamlandı. Diğer eylemler hala [beklemede.](air-review-approve-pending-completed-actions.md)|
|**Başarısız**|En az bir araştırma çözümleyicisi düzgün tamamlanamaya neden olan bir sorun ile gitti. <p> **NOT** Düzeltme eylemleri onaylandıktan sonra bir soruşturma başarısız olursa, düzeltme eylemleri yine de başarılı olabilir. Araştırma ayrıntılarını görüntüleme.|
|**Azaltma tarafından Sıraya Alınanlar**|Bir araştırma kuyruğa alındı. Diğer soruşturmalar tamamlandıktan sonra kuyruğa alınan soruşturmalar başlar. Azaltma, düşük hizmet performansını önlemeye yardımcı olur.  <p> **İpucu**: Bekleyen eylemler, kaç yeni araştırmanın çalıştırıla birlikte çalıştırılana kadar sınırlandırabilirsiniz. Bekleyen eylemleri [onaylayın (veya reddedin](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)).|
|**Azaltma ile Sonlandırıldı**|Araştırma fazla uzun süre kuyrukta tutulsa, durur. <p> **İpucu**: Threat [Explorer'dan bir araştırma başlatabilirsiniz](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|
|

## <a name="view-details-of-an-investigation"></a>Araştırmanın ayrıntılarını görüntüleme

1. Erişim portalına Microsoft 365 Defender (<https://security.microsoft.com> ) ve oturum açın.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.
3. Beklemede **veya Geçmiş** **sekmelerinde** bir eylem seçin. Açılır bölmesi açılır.
4. Açılır bölmede Araştırma sayfasını **aç'ı seçin**. 
5. Araştırma hakkında daha fazla bilgi edinmek için çeşitli sekmeleri kullanın.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Bir soruşturmayla ilgili uyarının ayrıntılarını görüntüleme

Belirli türde uyarılar, ekip içinde otomatik soruşturmayı Microsoft 365. Daha fazla bilgi edinmek için [bkz. Otomatik soruşturmaları tetikleyen uyarı ilkeleri](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Erişim portalına Microsoft 365 Defender (<https://security.microsoft.com> ) ve oturum açın.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.
3. Beklemede **veya Geçmiş** **sekmelerinde** bir eylem seçin. Açılır bölmesi açılır.
4. Açılır bölmede Araştırma sayfasını **aç'ı seçin**.
5. Bu **araştırmayla** ilişkili tüm uyarıların listesini görüntülemek için Uyarılar sekmesini seçin.
6. Açılır bölmesini açmak için listeden bir öğe seçin. Orada, uyarı hakkında daha fazla bilgi görüntüebilirsiniz.

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları unutmayın

- E-posta sayıları araştırmanın zamanında hesaplanır ve araştırma açılırken (temel alınan bir sorguya bağlı olarak) bazı sayımlar yeniden hesaplanır.

- E-posta sekmesindeki e-posta kümeleri için gösterilen  e-posta sayıları ve küme oluşturmada gösterilen e-posta miktarı değeri, araştırma zamanında hesaplanır ve değişmez.

- E-posta kümesi açılır iletisinde E-posta sekmesinin altında gösterilen e-posta sayısı ve Gezgin'de gösterilen e-posta iletilerinin sayısı, incelemenin ilk çözümlemesinde alınan e-posta iletilerini yansıttır.

  Dolayısıyla, özgün miktarı 10 e-posta iletilerini gösteren bir e-posta kümesi, inceleme çözümleme aşamasıyla yönetici incelemeyi inceleme aşaması arasında geldiğinde toplam 15 e-posta listesi gösteriyor. Benzer biçimde, Office 365 için Microsoft Defender'daki veriler denemeler için yedi gün sonra ve ücretli lisanslar için 30 gün sonra sona erer, bu nedenle eski soruşturmalar da Explorer sorgularının gösterdiğinden daha yüksek sayı göstermeye başlayabilir.

  Hem geçmiş sayısını hem de geçerli sayımların farklı görünümlerde göstermesi, e-postanın araştırma zamanında etkisini ve düzeltme çalıştırıldığı zamana kadar geçerli etkiyi göstermek için  yapılır.

- E-posta bağlamında, incelemenin bir parçası olarak anormal bir tehdit yüzeyi görebilirler. Ses düzeyi anormalliği, önceki zaman çerçeveleri ile karşılaştırıldığında araştırma olay süresi çevresinde benzer e-posta iletisinde bir depo olduğunu gösterir. E-posta trafiğinde bazı özelliklerle birlikte depo (örneğin, konu ve gönderen etki alanı, gövde benzerlikleri ve gönderen IP'leri), e-posta kampanyalarının veya saldırılarının başlangıcı normaldir. Bununla birlikte, toplu, istenmeyen posta ve yasal e-posta kampanyaları bu özellikleri yaygın olarak paylaşır.

- Toplu iş hacmi olası bir tehdittir ve buna göre kötü amaçlı yazılım veya kimlik avı tehditlerine karşı karşı daha az ciddi olabilir ve bu durum virüsten koruma motorları, detonasyonu veya kötü amaçlı itibarı kullanılarak tanımlanan tehditlere karşı daha az açık olabilir.

- Her eylemi onaylamanız zorunda değildir. Önerilen eylemi kabul etmiyorsanız veya organizasyonunız belirli eylem türlerini seç etmiyorsa, eylemleri reddetmeyi veya yok sayarak hiçbir işlem yapmaya devam  etme'yi seçebilirsiniz.

- Tüm eylemlerin onaylanması ve/veya reddedilen kısmın onaylanması, soruşturmanın tamamen kapanmasını sağlar (durum düzeltilir), bazı eylemler eksik kalırken, soruşturma durumunda kısmen düzeltilen durum değişir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bekleyen eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
