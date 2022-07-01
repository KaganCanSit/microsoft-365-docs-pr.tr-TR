---
title: Microsoft Purview Uyumluluk Yöneticisi'nde iyileştirme eylemleriyle çalışma
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Uyumluluk Yöneticisi'nde iyileştirme eylemleriyle çalışarak denetimleri uygulamayı ve test etmeyi öğrenin. İş, depolama belgeleri ve dışarı aktarma raporları atayın.
ms.openlocfilehash: ed52b6e9b3f6c817430383beebcb57f9c4dcf613
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574288"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde iyileştirme eylemleriyle çalışma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makalede:** Bu makalede **, geliştirme eylemleriyle uyumluluk iş akışınızı yönetme** adımları açıklanmaktadır. Uygulama ve test için **iyileştirme eylemleri atamayı** , **güncelleştirmeleri yönetmeyi** ve **raporları** dışarı aktarmayı öğrenin.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>İyileştirme eylemleriyle uyumluluk iş akışlarını yönetme

geliştirme eylemleri, uyumluluk etkinliklerinizi merkezileştirir. Her iyileştirme eylemi, veri koruma düzenlemeleri ve standartlarıyla uyumlu olmanıza yardımcı olmak için ayrıntılı uygulama yönergeleri sağlar. Uygulama ve test çalışmalarını gerçekleştirmek için kuruluşunuzdaki kullanıcılara eylemler atanabilir. Eylem içinde belge, not ve kayıt durumu güncelleştirmelerini de depolayabilirsiniz.

Tüm iyileştirme eylemleriniz, iyileştirme eylemleri sayfasında listelenir. [geliştirme eylemlerinizi görüntüleme](compliance-manager-setup.md#improvement-actions-page) hakkında daha fazla bilgi edinin.

## <a name="improvement-actions-details-page"></a>İyileştirme eylemleri ayrıntıları sayfası

Her geliştirme eyleminin geçerli durumunu, ilgili standartları ve mevzuat gereksinimlerini ve önerilen uygulama kılavuzunu gösteren bir ayrıntılar sayfası vardır. [Teknik eylemler](compliance-score-calculation.md#technical-and-non-technical-actions) , sizi uygulama için uygun çözüme götüren bir **Şimdi başlat** bağlantısı içerir. Uygulama ve test belgelerini doğrudan geliştirme eyleminin ayrıntılar sayfasına ekleyebilirsiniz.

İyileştirme eyleminin ayrıntılar sayfasını görüntülemek için:

1. geliştirme eylemleri sayfanıza gidin.
2. Hedeflenen geliştirme eyleminizin satırını seçerek ayrıntılar sayfasını açın.

Ekranın sağ üst köşesindeki yukarı veya aşağı oku seçerek listedeki sonraki veya önceki geliştirme eylemini kolayca görüntüleyebilirsiniz. İyileştirme eylemleri sayfasında listenizi filtrelediyseniz, yukarı veya aşağı hareket etmek sizi filtrelenen listede bir sonraki öğeye götürür.

> [!TIP]
> Farklı [geliştirme eylemleri türleri ve puanların nasıl ödüllendirilip](compliance-score-calculation.md#action-types-and-points) uyumluluk puanınıza hesaba katılmış olduğu hakkında daha fazla bilgi edinin.

## <a name="assign-improvement-actions"></a>İyileştirme eylemleri atama

Bir geliştirme eylemi üzerinde uygulama çalışmasını başlatmak için, işi kendiniz yapabilir veya başka bir kullanıcıya atayabilirsiniz. Atanan kişi şu olabilir:

- İş ilkesi sahibi
- BT uygulayıcısı
- Görevi gerçekleştirme sorumluluğu olan başka bir çalışan

Uygun atananı tanımladıktan sonra, işi gerçekleştirmek için yeterli [bir Uyumluluk Yöneticisi rolüne](compliance-manager-setup.md#set-user-permissions-and-assign-roles) sahip olduğundan emin olun. Ardından iyileştirme eylemini atamak için aşağıdaki adımları izleyin:

1. İyileştirme eylemleri ayrıntıları sayfasında ekranın sol tarafındaki **Eylem ata'yı** seçin.

2. **Kullanıcıya ata** açılır penceresi, **Önerilen kişiler** kullanıcı listesini gösterir. Listeden kullanıcıyı seçebilir veya atamak istediğiniz kişinin e-posta adresini yazabilirsiniz.

3. **Ata'yı** seçin. Atanan kullanıcı, iyileştirme eyleminin kendisine atandığını açıklayan bir e-posta alır ve iyileştirme eylemine doğrudan bağlantı sağlar.

> [!NOTE]
> ABD Kamu Topluluğu (GCC) Yüksek ve Savunma Bakanlığı (DoD) müşterileri, iyileştirme eylemleri atandığında e-posta almaz.

Atanan kullanıcı daha sonra önerilen eylemleri gerçekleştirebilir.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Tek bir kullanıcıya birden çok geliştirme eylemi atama

Aşağıdaki adımları izleyerek bir kullanıcıya birden çok geliştirme eylemi atayabilirsiniz:

1. İyileştirme eylemleri sayfanıza gidin.
2. İyileştirme eyleminin adının solundaki alanı seçin. Bu eylemi seçtiğinizi gösteren bir yuvarlak onay simgesi görüntülenir. Atamak istediğiniz tüm eylemleri denetleyin.
3. İyileştirme eylemleri tablosunun üst kısmındaki **Kullanıcıya ata** bağlantısını seçin.
4. Bir açılır pencere görüntülenir. **Ata** alanında, eylemleri atamak istediğiniz kişinin adını yazmaya başlayın. Önerilen kişiler listesinden de seçim yapabilirsiniz.
5. **Ata** alanını atananın adıyla doldurduktan sonra **Ata'yı** seçin.
6. Ardından, yeni atadığınız eylemler için yeni atananın listelendiği İyileştirme eylemleri sayfanızı görürsünüz.

## <a name="change-implementation-details"></a>Uygulama ayrıntılarını değiştirme

Her geliştirme eylemi için uygulama durumunu ve tarihini kaydedebilir ve iç başvuru için notlar ekleyebilirsiniz. Bu alanlar yalnızca atanan kişi tarafından değil, düzenleme izinleri olan herhangi bir kullanıcı tarafından düzenlenebilir.

İyileştirme eyleminin durumunu düzenlemek için ayrıntılar sayfasında **Uygulama ayrıntılarını düzenle'yi** seçin. Kullanılabilir alanlar ve durum seçenekleri aşağıdadır:

- **Uygulama durumu**
  - **Uygulanmadı**: eylem henüz uygulanmadı
  - **Kısmen uygulandı**: Otomatik olarak test edilen eylemler için eylem kısmen uygulanır (ne geçer ne de başarısız olur) ve kısmi puan alır
  - **Uygulandı**: eylem uygulandı
  - **Alternatif uygulama**: Diğer üçüncü taraf araçları kullandıysanız veya Microsoft önerilerine dahil olmayan başka eylemler gerçekleştirdiyseniz bu seçeneği belirleyin
  - **Planlı**: Eylem uygulama için planlandı
  - **Kapsam dışı**: eylem kuruluşunuzla ilgili değildir ve puanınıza katkıda bulunmaz
- **Uygulama tarihi**: Uygulama durumunun "uygulandığı" veya "alternatif uygulama" olduğunu seçmek için kullanılabilir
- **Uygulama notları**: uygulamanızla ilgili notlar için metin alanı.

Not alanlarında karakter sınırı yoktur. İyileştirme eylemleri ayrıntıları sayfasında kolayca görüntüleyebilmeniz ve düzenleyebilmeniz için notları kısa tutmanızı öneririz.

Ortak eylemler gruplar arasında eşitlenir. Aynı gruptaki iki farklı değerlendirme, sizin tarafınızdan yönetilen iyileştirme eylemlerini paylaştığında, bir eylemin uygulama ayrıntılarında veya durumunda yaptığınız tüm güncelleştirmeler, gruptaki diğer tüm değerlendirmelerde otomatik olarak aynı eylemle eşitlenir. Bu eşitleme, tek bir iyileştirme eylemi uygulamanıza ve birden çok düzenlemede çeşitli gereksinimleri karşılamanıza olanak tanır.

## <a name="change-test-status"></a>Test durumunu değiştirme

**Test** bölümünde geliştirme eyleminizin test durumunu, test tarihini ve notları görüntüleyebilirsiniz. Düzenleme izinlerine sahip bir kullanıcı **, Test** sekmesinde içeriği düzenlemek için **Test ayrıntılarını düzenle'yi** seçebilir.

#### <a name="testing-status-fields"></a>Test durumu alanları

**Test durumu**
 
İyileştirme eyleminin uygulama durumu "uygulandı" veya "alternatif uygulama" olduğunda test durumunu düzenleyebilirsiniz.

[El ile test edilen eylemler için test](#manual-testing-source) durumları:
  - **Hiçbiri**: Eylem üzerinde hiçbir çalışma başlatılmadı
  - **Değerlendirilmedi**: eylem test edilmedi
  - **Geçti**: Uygulama bir değerlendirici tarafından doğrulandı
  - **Başarısız düşük risk**: test başarısız, düşük riskli
  - **Başarısız orta risk**: test başarısız, orta riskli
  - **Başarısız yüksek risk**: test başarısız oldu, yüksek risk
  - **Kapsam dışı**: Eylem değerlendirmenin kapsamı dışındadır ve puanınıza katkıda bulunmaz
  - **Devam ediyor**: Test devam ediyor
  - **Düzeltildi**: tbd

[Otomatik olarak test edilen eylemler](#automatic-testing-source), **İyileştirme eylemleri** sayfasındaki **Test durumu** sütununda aşağıdaki durumlardan birini de gösterebilir:
   - **Algılanacak:** test durumunu gösteren sinyaller bekleniyor
  - **Algılanamadı**: test durumu algılanamadı; otomatik olarak yeniden denetlenecek
  - **Kısmen test edildi**: eylem kısmen test edildi;  ne geçer ne de başarısız olur

> [!NOTE]
> Otomatik olarak test edilen iyileştirme eylemleri için test durumu ve test notları el ile düzenlenemez. Uyumluluk Yöneticisi bu alanları sizin için güncelleştirir.

**Test tarihi**

Test tarihini seçmek için takvim açılır penceresinde geçiş yapın.

**Test notları** ve **Ek notlar**

Bu serbest metin alanlarına kendi iç başvurunuzun notlarını girin.

**Test geçmişi**

Test geçmişi, iyileştirme eylemi için tüm test durumu değişikliklerinin indirilmiş bir raporunu sağlar.

#### <a name="exporting-testing-history"></a>Test geçmişini dışarı aktarma
İyileştirme eylemi için test durumundaki tüm değişikliklerin geçmişini gösteren bir raporu dışarı aktarabilirsiniz. Bu raporlar özellikle [otomatik olarak test edilen eylemlerdeki](#automatic-testing-source) ilerleme durumunu izlemek için yararlıdır, çünkü bu tür eylemler kiracınızın verilerine göre düzenli olarak veya sık sık güncelleştirilir.

İyileştirme eyleminin ayrıntılar sayfasında **Test** sekmesini seçin. **Test geçmişi'nin** altında **Test geçmişini dışarı aktar** düğmesini seçin. Rapor bir Excel dosyası olarak indirilir.

## <a name="update-testing-source"></a>Test kaynağını güncelleştirme

Uyumluluk Yöneticisi, iyileştirme eylemlerini test etme seçenekleri sağlar. Her geliştirme eyleminin **Genel Bakış** bölümünde, **Test Kaynağı** alanında eylemin nasıl test edilmesi gerektiğini seçebileceğiniz bir açılan menü vardır: **El ile**, **Otomatik** ve **Üst**. Her test yöntemiyle ilgili ayrıntıları aşağıda bulabilirsiniz.

#### <a name="manual-testing-source"></a>El ile test kaynağı
El ile test için ayarlanan iyileştirme eylemleri, el ile test ettiğiniz ve uyguladığınız eylemlerdir. Gerekli uygulama ve test durumu durumlarını ayarlar ve tüm kanıt dosyalarını **Belgeler** sekmesine yüklersiniz. Bazı eylemlerde, iyileştirme eylemlerini test etme için tek kullanılabilir yöntem budur.

#### <a name="automatic-testing-source"></a>Otomatik test kaynağı
Bazı iyileştirme eylemleri, Uyumluluk Yöneticisi tarafından otomatik olarak test edilebilir. Hangi iyileştirme eylemlerinin otomatik olarak test edilebileceği ve test edilemeyecekleri [hakkında ayrıntılı bilgi edinin](compliance-manager-improvement-actions.md#update-testing-source).

Otomatik olarak test edilebilen iyileştirme eylemleri için, test kaynağı için **Otomatik** seçeneğini görürsünüz. Uyumluluk Yöneticisi, Microsoft 365 ortamınızda ayarladığınız diğer uyumluluk çözümlerinden gelen sinyallerin yanı sıra Microsoft Güvenli Puan'ın da izlediği tüm tamamlayıcı eylemleri algılar. Test sekmesindeki **Test mantığı** alanı, eylemin uyumluluk puanınıza doğru puan geçirmesi ve puan kazanması için başka bir çözümde ne tür bir ilke veya yapılandırma gerektiğini gösterir.

Sinyaller bir iyileştirme eyleminin başarıyla uygulandığını gösterdiğinde, ilgili denetim ve değerlendirmelerin puanlarını dikkate alacak şekilde bu eylem için uygun puanları otomatik olarak alırsınız. [Sürekli değerlendirmenin uyumluluk puanınızı nasıl etkilediği](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls) hakkında daha fazla bilgi edinin.

 Tüm uygun iyileştirme eylemleri için otomatik test varsayılan olarak açıktır. Bu ayarları yalnızca belirli iyileştirme eylemlerini otomatik olarak test etmek için ayarlayabilir veya tüm eylemler için otomatik testi kapatabilirsiniz. Otomatik testin nasıl çalıştığı ve ayarlarınızın nasıl ayarlanacağı hakkında daha fazla bilgi için [bkz. Otomatik testi ayarlama](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Üst test kaynağı

İyileştirme eylemi için test kaynağı olarak **Üst öğesini** seçtiğinizde, eyleminizin bağlanacağı başka bir eylem seçersiniz. Etkin eyleminiz, "üst" olarak belirlediğiniz eylemin "alt öğesi" olur. İyileştirme eylemi için bir üst öğe belirlediğinizde, bu eylem üst eylemin uygulama ve test ayrıntılarına göre değişir. Üst eylemin durumu her değiştiğinde, çocuğun durumu bu değişiklikleri devralır. Alt eylem, **belgeler sekmesindeki** üst eyleme ait tüm kanıtları da kabul eder ve bu da alt eylemin **Belgelerinde** daha önce var olan tüm verileri geçersiz kılabilir.

> [!NOTE]
> **Ebeveyn'in** test kaynağına sahip olmak, eylemin Uyumluluk Yöneticisi tarafından otomatik olarak test olduğu anlamına gelmez. Örneğin, üst eylemin test kaynağı **el ile** ise, alt eylem üst eylemin durumunu (kuruluş tarafından el ile test ve uygulama) gerçekleştirir.

Bir üst test kaynağı ayarlamak için aşağıdaki adımları izleyin:

- İyileştirme eylemi ayrıntıları sayfasında **Genel Bakış** bölümünü bulun.
- **Test Kaynağı** üst bilgisinin altında, açılan menüden **Üst** öğesini seçin.
- **Üst öğe ata'yı** seçin.
- **Üst geliştirme eylemi ata** açılır bölmesinde, listeden üst öğe olarak atamak istediğiniz iyileştirme eylemini bulun veya üstteki arama çubuğuna eylemin adını girin. Hedeflenen eyleminizi belirlediğinizde, üzerine geldiğinizde eylem adının solunda görünen onay kutusunu seçin ve ardından **Kaydet'i** seçin.

Eyleminizin ayrıntılar sayfasına geri dönersiniz. **Genel Bakış** bölümündeki **Test Kaynağı'nın** altında, üst eylem olarak belirttiğiniz yeni **eylem Üst eylem** altında listelenir.

## <a name="review-standards-and-regulations"></a>Standartları ve düzenlemeleri gözden geçirme

**Standartlar ve düzenlemeler** bölümü, iyileştirme eyleminizle ilişkili standartların ve düzenlemelerin aranabilir ve filtrelenebilir bir listesini sağlar. Bunlar ilgili **denetim**, **denetim kimliği, denetim** **ailesi** ve ilgili **düzenleme** tarafından görüntülenebilir.

## <a name="perform-work-and-store-documentation"></a>İş ve mağaza belgeleri gerçekleştirme

Uygulama ve test çalışmalarıyla ilgili dosyaları ve **notları doğrudan Belgeler** bölümüne yükleyebilirsiniz. Bu ortam, uyumluluk standartlarını ve düzenlemelerini karşılamak için denetimlerin memnuniyetini göstermenize yardımcı olan güvenli, merkezi bir depodur. Salt okunur erişimi olan tüm kullanıcılar bu bölümdeki içeriği okuyabilir. Yalnızca düzenleme haklarına sahip kullanıcılar dosyaları karşıya yükleyebilir ve indirebilir.

#### <a name="uploaded-documents"></a>Karşıya yüklenen belgeler

- İlgili dosyaları karşıya yüklemek için **Belgeleri yönet'i** seçin.
- Belgeleri yönetme açılır penceresi açıldığında **Belge ekle'yi** ve ardından sisteminizden dosyanızı seçin. Kabul edilen dosya türleri:
  - Belgeler (.doc, .xls, .ppt, .txt, .pdf)
  - Görüntüler (.jpg, .png)
  - Video (.mkv)
  - Sıkıştırılmış dosyalar (.zip, .rar)
- Dosyanız bölmede çözümlenince, dosya ekini otomatik olarak kaydeden **Kapat'ı** seçin. Ardından karşıya **yüklenen belgelerin** altında listelenen dosyayı görürsünüz.
- Belgeyi indirmek veya silmek için, belge listesinin altından **Belgeleri yönet'i** seçin. Açılır bölmede belge satırını seçerek vurgulayın ve ardından **İndir** veya **Sil'i** seçin.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Tamamlama için değerlendiriciye geliştirme eylemi atama

Çalışmayı tamamladıktan, test gerçekleştirdikten ve kanıt yükledikten sonra, bir sonraki adım geliştirme eylemini doğrulama için bir değerlendiriciye atamaktır. Değerlendirici, çalışmayı doğrular ve belgeleri inceler ve uygun test durumunu seçer.

**Test durumu "Başarılı" olarak ayarlanırsa**: eylem tamamlanır ve elde edilen puanlar elde edilen en yüksek puanı gösterir. Puanlar daha sonra genel uyumluluk puanınıza göre sayılır.

**Test durumu "Başarısız" olarak ayarlanırsa**: eylem gereksinimleri karşılamaz ve değerlendirici bunu ek çalışma için uygun kullanıcıya geri atayabilir.

## <a name="accepting-updates-to-improvement-actions"></a>İyileştirme eylemlerine yönelik güncelleştirmeleri kabul etme

İyileştirme eylemi için kullanılabilecek bir güncelleştirme olduğunda, adının yanında bir bildirim görürsünüz. Güncelleştirmeyi kabul edebilir veya daha sonra erteleyebilirsiniz.

#### <a name="what-causes-an-update"></a>Güncelleştirmeye neden olan nedenler

Puanlama, otomasyon veya kapsamla ilgili değişiklikler olduğunda bir güncelleştirme gerçekleşir. Değişiklikler, mevzuat değişikliklerine dayalı iyileştirme eylemlerine yönelik yeni yönergeler içerebilir veya bunun nedeni ürün değişiklikleri olabilir. Yalnızca kuruluşunuz tarafından yönetilen iyileştirme eylemleri güncelleştirme bildirimleri alır.

#### <a name="where-youll-see-assessment-update-notifications"></a>Değerlendirme güncelleştirme bildirimlerini nerede görürsünüz?

Bir iyileştirme eylemi güncelleştirildiğinde, iyileştirme eylemleri sayfasında ve ilgili değerlendirmelerinin ayrıntılar sayfasında adının yanında **Bekleyen güncelleştirme** etiketi görürsünüz.

İyileştirme eyleminin ayrıntılar sayfasına gidin ve üst başlıktaki **güncelleştirmeyi gözden geçir** düğmesini seçerek değişikliklerle ilgili ayrıntıları gözden geçirin ve güncelleştirmeyi kabul edin veya erteleyin.

#### <a name="review-update-to-accept-or-defer"></a>Kabul etmek veya ertelemek için güncelleştirmeyi gözden geçirin

İyileştirme eylemi ayrıntıları sayfasında **güncelleştirmeyi gözden geçir'i** seçtikten sonra, ekranınızın sağ tarafında bir açılır pencere bölmesi görüntülenir. Açılır pencere bölmesinde, etkilenen değerlendirmeler ve puan ile kapsamdaki değişiklikler gibi güncelleştirmeyle ilgili önemli ayrıntılar sağlanır.

İyileştirme eylemindeki tüm değişiklikleri kabul etmek için **Güncelleştirmeyi kabul et'i** seçin. **Kabul edilen değişiklikler kalıcıdır**.

> [!NOTE]
> Bir eylem güncelleştirmesini kabul ettiğinizde, bu eylemin diğer sürümlerine veya örneklerine yönelik güncelleştirmeleri de kabul edebilirsiniz. Güncelleştirmeler, teknik eylemler için kiracı genelinde yayılır ve teknik olmayan eylemler için grup genelinde yayılır.

**İptal'i** seçerseniz, güncelleştirme iyileştirme eylemine uygulanmaz. Ancak, güncelleştirmeyi kabul edene kadar **Bekleyen güncelleştirme** bildirimini görmeye devam edersiniz.

**Güncelleştirmeleri kabul etmenizi neden öneririz?**

Güncelleştirmeleri kabul etmek, elinizdeki sertifikasyon gereksinimlerini karşılamanıza yardımcı olmak için çözümleri kullanma ve uygun iyileştirme eylemleri gerçekleştirme konusunda en güncel rehberliğe sahip olduğunuzdan emin olmanıza yardımcı olur.

**Bir güncelleştirmeyi neden ertelemek isteyebilirsiniz?**

İyileştirme eylemini içeren bir değerlendirmeyi tamamlamanın ortasındaysanız, güncelleştirmeyi kabul etmeden önce üzerinde çalışmayı tamamladığınızdan emin olmak isteyebilirsiniz. Gözden geçirme güncelleştirmesi açılır bölmesinde **İptal'i** seçerek güncelleştirmeyi daha sonra erteleyebilirsiniz.

#### <a name="accept-all-updates-at-once"></a>Tüm güncelleştirmeleri aynı anda kabul etme

Birden çok güncelleştirmeniz varsa ve hepsini tek seferde kabul etmek istiyorsanız, geliştirme eylemleri tablonuzun üst kısmındaki **Tüm güncelleştirmeleri kabul et** bağlantısını seçin. Güncelleştirilecek eylem sayısını listeleyen bir açılır pencere bölmesi görüntülenir. Tüm **güncelleştirmeleri uygulamak için Güncelleştirmeleri kabul et** düğmesini seçin.

İyileştirme eylemleri sayfanıza döndüğünüzde, sayfanın üst kısmında güncelleştirmelerin tamamlanması için sayfayı yenilemenizi isteyen bir ileti görebilirsiniz.

## <a name="set-up-alerts-for-improvement-action-changes"></a>geliştirme eylemi değişiklikleri için uyarıları ayarlama

Uygulama veya test durumunda değişiklik ya da puan artışı veya düşüş gibi iyileştirme eylemlerinde belirli değişiklikler gerçekleştiğinde sizi hemen bilgilendirecek uyarılar ayarlayabilirsiniz. Bu tür değişikliklerle ilgili hızlı bildirimler almak, olası uyumluluk risklerini takip etme konusunda size yardımcı olabilir. Uyarıları ayarlamayı öğrenmek için [Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri](compliance-manager-alert-policies.md) sayfasını ziyaret edin.

## <a name="export-a-report"></a>Raporu dışarı aktarma

Tüm iyileştirme eylemlerinizi ve iyileştirme eylemleri sayfasında gösterilen filtre kategorilerini içeren bir Excel çalışma sayfasını indirmek için ekranınızın sol üst köşesindeki **Dışarı Aktar'ı** seçin.
