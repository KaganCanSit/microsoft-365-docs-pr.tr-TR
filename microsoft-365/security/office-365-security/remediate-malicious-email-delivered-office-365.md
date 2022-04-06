---
title: Bir dosyada teslim edilen kötü amaçlı e-postaları Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Tehdit düzeltmesi
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 49cd5f532f41fd05090592136e28ca2462a9efd6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681182"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Posta ile teslim edilen kötü amaçlı e-postaları Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

Düzeltme, bir tehditle karşı önceden planlanmış bir eyleme karşı almak anlamına gelir. Bilgisayarınıza gönderilen kötü amaçlı e-postalar sistem tarafından, sıfır saatlik otomatik temizleme (ZAP) yoluyla veya gelen kutusu taşıma, gereksiz'e taşıma, silinmiş öğelere taşıma, yumuşak silme veya sabit silme gibi düzeltme eylemleri aracılığıyla güvenlik ekipleri tarafından temizlenebilir *.* Microsoft Defender for Office 365 Plan 2/E5, güvenlik ekiplerinin elle ve otomatik soruşturma yoluyla e-posta ve işbirliği işlevselliğiyle tehditleri düzeltmesini sağlar.

> [!NOTE]
> Kötü amaçlı e-postaları düzeltmek için güvenlik ekiplerine Arama *ve* Temizleme rolü atanabilir. Rol ataması, [portalda izinler Microsoft 365 Defender yapılır](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Yöneticiler e-postalarda gerekli işlemleri gerçekleştirebilirsiniz, ancak bu eylemlerin onaylanması için, Microsoft 365 Defender portalında  E-posta & işbirliği izinlerine atanmış Ara ve Temizle  rolüne sahip olması gerekir. Rol *gruplarından biri için* Ara ve temizleme" rolü ekli olmadan, eylemi yürütüleyem olmaz.

## <a name="manual-and-automated-remediation"></a>El ile ve otomatik düzeltme

*El ile* arama, güvenlik ekipleri Explorer'daki arama ve filtreleme özelliklerini kullanarak tehdit tanımlıyorsa ortaya çıkar. El ile düzeltme, siz düzeltmesi gereken bir dizi e-posta tanım bastıktan *sonra herhangi bir* e-posta *görünümünde (Kötü* Amaçlı Yazılım, Kimlik Avı veya Tüm e-postalar *)* tetiklenir.

> [!div class="mx-imgBorder"]
> [![Tehdit Gezgini'Office 365 tarihe göre el ile avlama.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Güvenlik ekipleri çeşitli yollarla e-postaları seçmek için Explorer'ı kullanabilir:

- El ile e-postaları seçin: Çeşitli görünümlerde filtreleri kullanın. Düzeltmek için en fazla 100 e-posta seçin.

- Sorgu seçimi: Üstteki Hepsini seç düğmesini kullanarak tüm **sorguyu** seçin. Aynı sorgu, işlem merkezi posta gönderimi ayrıntılarında da gösterilir.

- Dışlamayla sorgu seçimi: Bazen güvenlik işlemleri ekipleri, bir sorgunun tamamını seçerek ve belirli e-postaları sorgudan el ile dışlayarak e-postaları düzeltmek ister. Yönetici bunu yapmak için, YöneticiNin her şeyi seç **onay kutusunu** kullanabilir ve e-postaları el ile dışarıda tutmak için sayfayı aşağı kaydırın. Sorgu en çok 1.000 e-posta tutabilir. En fazla dışlama sayısı 100'tir.

E-postalar Gezgin aracılığıyla seçildikten sonra, doğrudan bir işlemle veya bir eylem için e-postaları sıraya alarak düzeltmeye başlayabilirsiniz:

- Doğrudan onay: Uygun izinlere sahip güvenlik personeli tarafından Gelen Kutusu'na taşıma, gereksiz'e *taşıma, silinmiş* öğelere  *taşıma, yumuşak* silme veya kalıcı silme gibi eylemler seçildiğinde ve düzeltmenin sonraki adımları izlendikten sonra, düzeltme süreci seçili eylemi yürütmeye başlar. Geçici bir çıkış, düzeltmenin devam ediyor olduğunu gösterir.

- İki adımlı onay: Uygun izinleri olmayan veya eylemi yürütmek için beklemesi gereken yöneticiler "düzeltmeye ekle" eylemi gerçekleştirebilirsiniz. Bu durumda, hedefli e-postalar bir düzeltme kapsayıcısı eklenir. Düzeltme yürütülmeden önce onay gerekir.

**Otomatik araştırma ve yanıt eylemleri** , uyarılar veya Explorer'daki güvenlik işlemleri ekipleri tarafından tetiklenir. Bunlar, güvenlik işlemleri ekibi tarafından onaylanması gereken önerilen düzeltme eylemlerini içerebilir. Bu eylemler, otomatik **araştırmanın** Eylem sekmesine dahil edilir.

> [!div class="mx-imgBorder"]
> [!["Zapped" sayfasında kötü amaçlı yazılımla posta, Zap yürütme zamanlarını gösteriyor.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Gezgin'de oluşturulmuş tüm düzeltmeler (doğrudan onay veya iki adımlı onay) ve otomatik soruşturmalardan gelen onaylanmış eylemler İşlem Merkezi'nde görüntülenir. Bunlara, İşlem Merkezini Gözden Geçir'in altındaki sol **gezinti panelinden** \> **erişin**.

> [!div class="mx-imgBorder"]
> [![Tarihe ve önem derecesine göre tehdit listesiyle işlem merkezi.](../../media/tp-RemediationArticle4.png)](../../media/tp-RemediationArticle4.png#lightbox)

İşlem Merkezi son 30 gün için tüm düzeltme eylemlerini gösterir. Explorer aracılığıyla  alınan eylemler, düzeltme oluşturulduğunda güvenlik işlemleri ekibinin sağladığı adla listelenir. Otomatik soruşturmalar aracılığıyla  alınan eylemlerin başlığı, incelemeyi tetikleyen ilgili uyarıyla başlar (örneğin, "Zap e-posta kümesi... )."

Ad, oluşturma tarihi, açıklama, tehdit önem derecesi ve durum gibi ayrıntıları görüntülemek için herhangi bir düzeltme öğesini açın. Aşağıdaki iki sekmeyi de gösterir.

- **Posta gönderimi** sekmesi: Threat Explorer aracılığıyla gönderilen e-posta sayısını veya düzelti yapılacak otomatik soruşturmaları görüntüler. Bu e-postalar eyleme değiştirilebilir veya işlem edilemez.

  > [!div class="mx-imgBorder"]
  > [![İşlemlenebilir ve işlem için değiştirilebilir tehditlere sahip işlem merkezidir.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

  - **İşlem Edilebilir**: Aşağıdaki bulut posta kutusu konumlarında yer alan e-postalar üzerinde eyleme edilebilir ve taşınabilir:
    - Gelen Kutusu
    - Gereksiz
    - Klasör silindi
    - Yumuşak silinmiş klasör

      > [!NOTE]
      > Şu anda, yalnızca posta kutusuna erişimi olan bir kullanıcı silinmiş bir klasörden öğeleri kurtarabilirsiniz.

  - **İşlem edilemez**: Aşağıdaki konumlarda yer alan e-postalar düzeltme eylemleriyle eylem gerçekleştirilemez veya taşınamaz:
    - Karantina
    - Sabit silinmiş klasör
    - Şirket içi/dış
    - Başarısız/bırakılan

  Şüpheli iletiler düzeltilebilir veya düzeltilemez olarak kategorilere ayrılmıştır. Çoğu durumda, düzeltilebilir ve düzeltilemez iletiler, gönderilen toplam iletilerden eşittir. Ancak nadir durumlarda bu doğru olmaz. Bu durum, sistem gecikmeleri, zaman aşımı veya süresi dolmuş iletiler nedeniyle olabilir. İletilerin süresi, kurum için Explorer bekletme süresine bağlı olarak sona erer.

  Kuruluşun Explorer bekletme süresi sona e-postadan sonra eski iletileri düzeltmezken, sayı tutarsızlıkları gördüğünüzde öğeleri yeniden denemeniz tavsiye edilir. Sistem gecikmeleri için düzeltme güncelleştirmeleri genellikle birkaç saat içinde yenilenir.

  Kuruluşun Gezgin'de e-postayı bekletme süresi 30 gündür ve 29-30 gün geriye e-postaları düzeltıyorsanız, posta gönderim sayıları her zaman bir şey eklemez. E-postalar bekletme süresi zaten taşınmaya başlamış olabilir.

  Düzeltmeler bir süre "Sürüyor" durumuna takılmışsa, bunun nedeni sistem gecikmeleri olabilir. Düzeltmek birkaç saat sürebilir. Sistem gecikmeleri nedeniyle düzeltmenin başında bazı e-postalar sorguya dahil e-postalarda yer alamamayya neden olabileceği için, posta gönderim sayılarında farklılıklarla bakabilirsiniz. Bu gibi durumlarda düzeltmeyi yeniden denemek iyi bir fikirdir.

  > [!NOTE]
  > En iyi sonuç için, düzeltmenin 50.000 veya daha az toplu olarak yapılması gerekir.

  Düzeltme sırasında yalnızca düzeltilebilir e-postalar üzerinde eyleme geçilebilir. Düzeltilemez e-postalar, bulut posta kutularında depolandığı Office 365 e-posta sistemi tarafından düzeltilemez.

  Yöneticiler gerekirse karantinada bulunan e-postalar üzerinde eylem gerçekleştirebilir, ancak el ile temizlanmazsa bu e-postaların karantina süresi dolar. Varsayılan olarak, kötü amaçlı içerik nedeniyle e-postalara kullanıcılar tarafından erişilemez ve dolayısıyla güvenlik personeli karantinada tehditlerden kurtulmak için herhangi bir işlem yapmak zorunda değildir. E-postalar şirket içinde veya dışında olursa, şüpheli e-postayla bağlantı kurmak için kullanıcıyla bağlantı kurabilirsiniz. Ya da yöneticiler kaldırma için ayrı e-posta sunucusu/güvenlik araçları kullanabilir. Bu e-postalar, Explorer'da *teslim konumu = önceden gelen dış filtre* uygulanarak belirlenebilirsiniz. Başarısız veya bırakılan e-postalar veya kullanıcılar tarafından erişilamayan e-postalar için, azaltmak istediğiniz e-posta olmaz çünkü bu postalar posta kutusuna ulaşmaz.

  Aşağıdaki resimde bir gönderimin İşlem Merkezi'nde nasıl göründüğünü gösterir. Düzeltme birden çok gönderim içerebilir. Birden çok eylem tek bir otomatik soruşturma aracılığıyla onaylanırsa, her e-posta veya e-posta kümesi eylemi, farklı bir gönderimle aynı düzeltmede görünür.

  > [!div class="mx-imgBorder"]
  > [![ZAP e-posta kümesi uçma paneli.](../../media/tp-RemediationArticle6.png)](../../media/tp-RemediationArticle6.png#lightbox)

  Bu düzeltmenin ayrıntılarını( sorgu seçme yoluyla otomatik soruşturmalar veya Explorer tetiklendiğinde) ve düzeltmenin başlangıç ve bitiş saatleri gibi ayrıntıları göstermek için bir posta gönderme öğesi seçin. Ayrıca, düzeltme için gönderilen iletilerin listesini de görüntüler. İletiler Gezgin bekletme süresinden çıktıklarından, iletiler bu listeden kaybolur. Listede düzeltilebilir tek tek iletiler de görüntülenir.

- **Eylem günlükleri**: Bu sekmede, onay tarihi, eylemi, eylemi, durumu ve sayımları onay eden yönetici gibi düzeltmiş iletiler görüntülenir.

  Durum şöyle olabilir:

  - **Başlatıldı**: Düzeltme tetiklenir.
    - **Sıraya Alınan**: Düzeltme, e-postaların azaltılması için sıraya alınan bir kuyruktadır.
    - **Sürüyor**: Azaltma devam ediyor.
    - **Tamamlandı**: Düzeltilebilir tüm e-postaların azaltması başarıyla veya bazı hatalarla tamamlanır.
    - **Başarısız**: Hiçbir düzeltme başarılı olmadı.

  Yalnızca düzeltilebilir e-postalar üzerinde eyleme geçilebilir ve her e-postanın temizleme işlemi başarılı veya başarısız olarak gösterilir. Toplam düzeltilebilir e-postalardan, başarılı ve başarısız azaltmaları bildiriliyor.

  - **Başarı**: Düzeltilebilir e-postalar üzerinde istenen eylem başarıyla tamamlandı. Örneğin: Yönetici posta kutularından e-postaları kaldırmak ister, bu nedenle yönetici e-postaları geçici olarak silme eylemsini gerçekleştirin. Eylem  alındıktan sonra özgün klasörde düzeltilebilir bir e-posta bulunamazsa, durum başarılı olarak görünür.

  - **Hata**: Düzeltilebilir e-postalarda istenen eylem başarısız oldu. Örneğin: Yönetici posta kutularından e-postaları kaldırmak ister, bu nedenle yönetici e-postaları geçici olarak silme eylemsini gerçekleştirin. Eylem alındıktan sonra posta kutusunda düzeltilebilir bir e-posta bulunursa, durum başarısız olarak gösterir.
  
  - **Zaten hedefte**: İstenen eylem e-postada zaten ildi VEYA e-posta hedef konumda zaten var. Örneğin: İlk gün Gezgin aracılığıyla yönetici tarafından e-posta yumuşak olarak silinmiştir. Daha sonra benzer e-postalar 2. günde de ortaya çıktı ve bu e-postalar yönetici tarafından tekrar yumuşak silinir. Yönetici, bu e-postaları seçerken son olarak, zaten yumuşak silinmiş olan ilk günden bazı e-postalar seçiyor. Artık bu e-postalar bir daha üzerinde eyleme geçilecek, çünkü hedef konumda var olan e-postalar hiçbir eyleme alınmamış olarak sadece "hedefte" olarak gösterilecek.

  - **Yeni**: *Eylem Günlüğü'ne* Hedef sütunda Zaten var olan bir sütun eklenmiştir. Bu özellik, postanın daha önce düzeltilmişse sinyal göndermek için Threat Explorer'daki en son teslim konumunu kullanır. *Zaten hedefte* olan ileti sayısı, güvenlik ekiplerinin yine de ele alınması gereken toplam ileti sayısını anlamalarına yardımcı olur.

Eylemler yalnızca Tehdit Gezgini'nin Gelen Kutusu, Gereksiz, Silinmiş ve Yumuşak Silinmiş klasörleri'nde iletiler üzerinde gerçek dışı ekleyebilirsiniz. Burada, yeni sütunun nasıl çalıştığının bir örneği ve ve bir örneği ve bir örnek ve sonra açık ve açık bir şekilde Gelen *Kutusu'ta* var olan iletide yumuşak silme eylemi musunuz? Ardından ileti ilkelere göre iş olur. Bir sonraki yumuşak silme işlemi gerçekleştirilecekse, bu ileti "Zaten hedefte" sütunu altında görüntülenir ve bu iletinin yeniden ele alınması gerekmiyor sinyalini verir.

Düzeltme ayrıntılarını görüntülemek için eylem günlüğünde herhangi bir öğeyi seçin. Ayrıntılarda "başarılı" veya "posta kutusunda bulunamadı" ifadeleri varsa, bu öğe posta kutusundan zaten kaldırılmıştır. Düzeltme sırasında bazen sistem hatası olabilir. Böyle durumlarda, düzeltme eylemlerini yeniden denemek iyi bir fikirdir.

Büyük toplu e-postaları düzeltme durumunda, Posta Gönderimi yoluyla düzeltme için gönderilen iletileri ve Eylem Günlükleri aracılığıyla düzeltmiş iletileri dışarı aktarın. Dışarı aktarma sınırı 100.000 kayıt olarak artırıldı.

Düzeltme, tehditleri azaltmak, şüpheli e-postaları adreslerine karşıtlık sağlar ve kuruluşun güvenliğini korumanıza yardımcı olur.
