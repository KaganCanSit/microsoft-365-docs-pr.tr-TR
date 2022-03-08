---
title: Microsoft Uyumluluk Yöneticisi'nde geliştirme eylemleriyle çalışma
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
description: Microsoft Uyumluluk Yöneticisi'nde geliştirme eylemleriyle çalışarak denetimleri uygulama ve test etmeyi öğrenin. Çalışma atayın, belgeleri depo edin ve raporları dışarı aktarın.
ms.openlocfilehash: 33b1de7dfc116cc1403d0e3619dfbec2f0853be3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319469"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde geliştirme eylemleriyle çalışma

**Bu makalede:** Bu makalede, geliştirme eylemleriyle **uyumluluk iş akışınızı** yönetme işlemleri açıklanmıştır. Uygulama ve test **için geliştirme eylemleri** atamayı, güncelleştirmeleri **yönetmeyi ve** raporları dışarı aktarmayı **öğrenin**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Geliştirme eylemleriyle uyumluluk iş akışlarını yönetme

Uyumluluk etkinliklerinizi merkezi olarak geliştirme eylemleri gerçekleştirin. Her geliştirme eylemi, veri koruma düzenlemelerine ve standartlara uyum içinde çalışmanıza yardımcı olacak ayrıntılı uygulama kılavuzu sağlar. Eylemler, uygulama ve test çalışması gerçekleştirmek için kuruluşta kullanıcılara atanabilir. Ayrıca belgeleri, notları depolar ve eylem içindeki durum güncelleştirmelerini de kayda alabilirsiniz.

Geliştirme eylemlerinizin hepsi geliştirme eylemleri sayfasında listelenir. Geliştirme eylemlerinizi görüntüleme [hakkında daha fazla bilgi öğrenin](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Geliştirme eylemleri ayrıntıları sayfası

Her geliştirme eyleminin geçerli durumunu, ilgili standartları ve mevzuat gereksinimlerini ve önerilen uygulama kılavuzlarını gösteren bir ayrıntılar sayfası vardır. [Teknik eylemler](compliance-score-calculation.md#technical-and-non-technical-actions) , sizi **uygulama için** uygun çözüme alan Şimdi başlat bağlantısını içerir. Geliştirme eyleminin ayrıntılar sayfasına doğrudan uygulama ve test belgeleri ebilirsiniz.

Geliştirme eyleminin ayrıntılar sayfasını görüntülemek için:

1. Geliştirme eylemleri sayfanıza gidin.
2. Hedeflenen geliştirme işleminizin ayrıntılarını sayfasını açan satırı seçin.

Ekranın sağ üst köşesindeki yukarı veya aşağı oku seçerek, listede sonraki veya önceki geliştirme eylemlerini kolayca görebilirsiniz. Geliştirme eylemleri sayfasında listenizi filtreledıysanız, yukarı veya aşağı hareket etmek, bu filtrelenmiş listede sizi bir sonraki öğeye kadar ilerlemenizi sağlar.

> [!TIP]
> Farklı geliştirme eylemleri türleri [hakkında daha fazla bilgi edinmek ve bu noktaların uyumluluk puanınıza](compliance-score-calculation.md#action-types-and-points) nasıl puan verilip faktörlü olduğunu öğrenin.

## <a name="assign-improvement-actions"></a>Geliştirme eylemleri atama

Geliştirme eylemi üzerinde uygulama çalışmasına başlamak için, bu işlemi kendiniz yapar veya başka bir kullanıcıya atabilirsiniz. Atanan kişi:

- İş ilkesi sahibi
- Bir IT uygulayıcısı
- Görevi gerçekleştirme sorumluluğu olan başka bir çalışan

Uygun yetkiliyi tanım verdiktan sonra, bu atamanın çalışması için yeterli Uyumluluk [Yöneticisi rolüne](compliance-manager-setup.md#set-user-permissions-and-assign-roles) sahip olduğundan emin olun. Ardından geliştirme eylemlerini atamak için aşağıdaki adımları izleyin:

1. Geliştirme eylemleri ayrıntıları sayfasında, ekranın sol **tarafından Eylem** ata'ya tıklayın.

2. **Kullanıcıya ata bölmesi**, Önerilen kişiler **kullanıcı** listesini gösterir. Listeden bir kullanıcı seçebilirsiniz veya atamak istediğiniz kişinin e-posta adresini yazın.

3. **Ata'ya seçin**. Atanan kullanıcı, geliştirme eyleminin ona atandığıyla ilgili bir e-posta alır ve geliştirme eyleminin doğrudan bağlantısını alır.

> [!NOTE]
> ABD Kamu Community (GCC) Yüksek ve Savunma Bölümü (DoD) müşterileri geliştirme eylemleri atandığı zaman e-posta alamaz.

Ardından atanan kullanıcı önerilen eylemleri gerçekleştirabilir.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Tek bir kullanıcıya birden çok geliştirme eylemi atama

Aşağıdaki adımları kullanarak bir kullanıcıya birden çok geliştirme eylemi atabilirsiniz:

1. Geliştirme eylemleri sayfanıza gidin.
2. Geliştirme eyleminin adının sol tarafından bir alan seçin. Bu eylemi seçtiğinizi belirten yuvarlak bir onay simgesi görünür. Atamak istediğiniz tüm eylemleri kontrol edin.
3. Geliştirme **eylemleri tablosunda,** Kullanıcıya ata bağlantısını seçin.
4. Bir açılır pencere görüntülenir. Ata **alanında** , eylemleri atamak istediğiniz kişinin adını yazmaya başlayın. Önerilen kişiler listesinden de seçim seçebilirsiniz.
5. Ata alanını ata **ata'nın** adıyla doldurmak için Ata'ya **seçin**.
6. Yeni atanan kişi, atadığınız eylemler için listelenmiş olarak Geliştirme eylemleri sayfanız gösterilir.

## <a name="change-implementation-details"></a>Uygulama ayrıntılarını değiştirme

Her geliştirme eylemi için uygulama durumunu ve tarihini kaydedebilirsiniz ve şirket içinde başvuruya yönelik notlar ekleyebilirsiniz. Bu alanlar, yalnızca atanan kişi tarafından değil, düzenleme izinlerine sahip olan herhangi bir kullanıcı tarafından düzenlenebilir.

Geliştirme eyleminin durumunu düzenlemek için, ayrıntılar **sayfasında Uygulama ayrıntılarını düzenle'yi** seçin. Kullanılabilir alanlar ve durum seçenekleri aşağıdadır:

- **Uygulama durumu**
  - **Uygulanmadı**: eylem henüz uygulanmadı
  - **Uygulanan**: uygulanan eylem
  - **Alternatif uygulama**: Diğer üçüncü taraf araçlarını kullandıysanız veya Microsoft önerilerine dahil olmayan başka eylemler yaptıysanız bu seçeneği belirleyin
  - **Planlı**: uygulama için eylem planlandı
  - **Kapsam dışında**: eylem, organizasyonuyla ilgili değil ve puanınıza katkıda bulun
- **Uygulama tarihi**: Uygulama durumu "uygulama" veya "alternatif uygulama" olduğunda seçmek için kullanılabilir
- **Uygulama notları**: Uygulamanıza yönelik notlar için metin alanı.

Not alanlarında karakter sınırı yoktur. Geliştirme eylemleri ayrıntıları sayfasından notlarınızı kolayca görüntüley ve düzenley için, notları kısa tutmanız önerilir.

Gruplar arasında ortak eylemler eşitlenir. Aynı grupta yer alan iki farklı değerlendirme sizin yönetilen geliştirme eylemlerini paylaştığında, bir eylemin uygulama ayrıntılarında veya durumunda yapılan tüm güncelleştirmeler, gruptaki diğer tüm değerlendirmelerde aynı eylemle otomatik olarak eşitlenir. Bu eşitleme, tek bir geliştirme eylemi uygulamana ve birden fazla düzenlemeye ilişkin çeşitli gereksinimleri karşılamaya olanak sağlar.

## <a name="change-test-status"></a>Test durumunu değiştirme

Test **bölümünde** , geliştirme eyleminizin test durumunu, test tarihini ve varsa notları görüntüebilirsiniz. Bu alanların içeriği, Düzenleme izinleri olan herhangi **bir kullanıcı tarafından Test** ayrıntılarını düzenle altında değiştirilebilir.

Kullanılabilir alanlar şunlardır:

- **Test durumu**: Uygulama durumu "uygulama" veya "alternatif uygulama" olduğunda seçmek için kullanılabilir. Seçenekler şunlardır:
  - **Değerlendir edilmedi**: eylem sınanmamıştır
  - **Kabul** edildi: uygulama, bir değerlendiren tarafından doğrulandı
  - **Düşük risk başarısız**: test başarısız oldu, düşük risk
  - **Orta risk başarısız**: test başarısız, orta risk
  - **Yüksek risk başarısız**: test başarısız oldu, yüksek risk
  - **Kapsam dışında**: eylem değerlendirme kapsamı dışındadır ve puanınıza katkı sağlamaz
- **Test tarihi**: Tarihi seçmek için takvim açılır menüsünde geçiş yapmak
- **Notları test etme** **ve Ek notlar**: dahili başvuru için notlar için metin alanları

### <a name="update-testing-source"></a>Test kaynağını güncelleştirme

Uyumluluk Yöneticisi size geliştirme eylemlerini test etmek için seçenekler sağlar. Her **geliştirme eyleminin** Genel Bakış bölümünde, Kaynak Test  Alanında eylemin nasıl test etmek istediğinize ilişkin tercihleri seçen bir açılan menü vardır **: El** **ile, Otomatik** ve **Üst**. Aşağıda, her test yöntemiyle ilgili ayrıntıları öğrenin.

#### <a name="manual-testing-source"></a>El ile test kaynağı
El ile test etmek için ayarlanmış geliştirme eylemleri, el ile test ve uygulama eylemleridir. Gerekli uygulama ve test durumu durumlarını ayarlayın ve Belgeler sekmesine tüm kanıt dosyalarını **yükleyin** . Bazı eylemlerde, geliştirme eylemlerini test etmek için kullanılabilen tek yöntem bu yöntemdir.

#### <a name="automatic-testing-source"></a>Otomatik test kaynağı
Bir uygulama eylemi Uyumluluk Yöneticisi tarafından otomatik olarak test edilecek şekilde uygunsa, kaynak test **etmek için otomatik** seçeneğini oradanız. Uyumluluk Yöneticisi, Microsoft Güvenli Puanı'nın da izler olduğu tamamlayıcı eylemlerin yanı sıra, Microsoft 365 ortamınıza ayarladınız diğer uyumluluk çözümlerinden gelen sinyalleri algılar. Test **sekmesindeki** Test mantığı alanı, eylemin uyumluluk puanınızı geçmesi ve bu puandan puan kazan olması için başka bir çözümde ne tür bir ilke veya yapılandırma gerektir olduğunu gösterir.

Sinyaller bir geliştirme eyleminin başarıyla uygulandığını gösteriyorsa, bu eylem için uygun puanları otomatik olarak alırsınız ve bu da ilgili denetimlerin ve değerlendirmelerin puanlarını dengeler. Sürekli değerlendirmenin uyumluluk [puanınızı nasıl etkileyeceğini öğrenin](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

 Tüm uygun geliştirme eylemleri için otomatik sınama varsayılan olarak açıktır. Bu ayarları yalnızca belirli geliştirme eylemlerini otomatik olarak test etmek için ayarlayabilir veya tüm eylemler için otomatik sınamayı kapatabilirsiniz. Otomatik testin nasıl çalıştığını ve ayarlarınızı otomatik test ayarlama konusundan [daha fazla bilgi edinebilirsiniz](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Üst sınama kaynağı

Geliştirme **eyleminin** test kaynağı olarak Üst'i seçerseniz, eyleminizin bağlanacak başka bir eylemi seçersiniz. Etkin olan eyleminiz, "ebeveyn" olarak atamanız eyleme "çocuğunuz" olur. Geliştirme eylemi için bir üst bilgi alt öğesi atamayı, bu eylemin üst eylemin uygulama ve test ayrıntılarını yapısı olur. Üst eylemin durumu her değişiklikte, çocuğun durumu bu değişiklikleri devralır. Alt eylem, Belgeler sekmesinde bulunan ve üst eyleme  ait olan tüm kanıtı kabul eder. Bu eylem, alt eylemin Belgeler'inde daha önce var olan verileri geçersiz **kıldı**.

> [!NOTE]
> Üst öğenin test kaynağı **olması** , eylemin Uyumluluk Yöneticisi tarafından otomatik olarak test edilmiş olduğu anlamına gelmez. Örneğin, üst eylemin test kaynağı el ile **olursa, alt** eylem kuruluş tarafından el ile yapılan bir test ve uygulama olan üst eylemin durumunu alır.

Üst test kaynağını ayarlamak için aşağıdaki adımları izleyin:

- Geliştirme işlemi ayrıntıları sayfasında Genel Bakış **bölümünü** bulun.
- Kaynak Test **Başlığı altında** , açılan **menüden** Üst'i seçin.
- Üst öğe **ata'ya seçin**.
- Üst **geliştirme eylemi ata** uç burada, listede üst olarak atamak istediğiniz geliştirme eylemlerini bulun veya üst yakın olan arama çubuğuna eylemin adını girin. Amaçlanan eyleminizi tanımsanız, üzerine gelin ve eylem adının sol tarafından görüntülenen onay kutusunu seçin, sonra da Kaydet'i **seçin**.

Eyleminizin ayrıntılar sayfasına dönersiniz. Genel **Bakış bölümündeki** Test **Kaynağı'nın** altında üst eylem olarak belirledik yeni eylem Üst eylem **altında listelenir**.

## <a name="review-standards-and-regulations"></a>Standartları ve düzenlemeleri gözden geçirme

Standartlar **ve düzenlemeler bölümü** , geliştirme eyleminize ilişkin, arama edilebilir ve filtrelenebilir bir standartlar ve düzenlemeler listesi sağlar. Bunlar ilgili denetim, denetim **kimliği**, **denetim ailesi ve** **ilgili düzenleme** ile bunları **22/2/2003'lerde** karşılarına çıkana kadar onları görüntüde bulundurabilirsiniz.

## <a name="perform-work-and-store-documentation"></a>İş ve depolama belgelerini gerçekleştirme

Uygulama ve test etme ile ilgili dosyaları ve notları doğrudan Belgeler bölümüne **yükleyebilirsiniz** . Bu ortam, uyumluluk standartlarını ve düzenlemelerini karşılamaya yardımcı olacak denetimlerin memnuniyetini göstermenıza yardımcı olan güvenli ve merkezi bir depodur. Salt okunur erişimi olan tüm kullanıcılar bu bölümdeki içeriği okuyabilir. Dosyaları yalnızca düzenleme hakları olan kullanıcılar karşıya yükleyebilir ve indirebilir.

#### <a name="uploaded-documents"></a>Karşıya yüklenen belgeler

- Uygun **dosyaları karşıya yüklemek** için Belgeleri yönet'i seçin.
- Belgeleri yönet açılır bölmesi açıldığında Belge **ekle'yi** seçin ve sonra da sisteminiz içinde dosyanızı seçin. Kabul edilen dosya türleri:
  - Belgeler (.doc, .xls, .ppt, .txt, .pdf)
  - Resimler (.jpg, .png)
  - Video (.mkv)
  - Sıkıştırılmış dosyalar (.zip, .rar)
- Dosyanız bölmede çözümlenirken Kapat'ı **seçin;** bu işlem dosya ekini otomatik olarak kaydeder. Ardından, Karşıya yüklenen belgeler'in altında listelenen **dosyayı görüyorsunuz**.
- Belgeyi indirmek veya silmek için, belge **listesinin altındaki** Belgeleri yönet'i seçin. Uçarak çıkış bölmesinde belge satırına seçerek vurgulayın ve ardından İndir veya **Sil'i** **seçin**.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Tamamlanma için değerlendirene geliştirme işlemi atama

Çalışma tamamlandıktan, testi yürütdikten ve kanıtı karşıya yükledikten sonra, bir sonraki adım geliştirme eylemını doğrulama için bir değerlendirene atamaktır. Değerlendiren, çalışmaları doğrular, belgeleri inceler ve uygun test durumunu seçer.

**Test durumu "Geçti" olarak ayarlanırsa**, eylem tamamlanır ve elde edilen puanlar, elde edilen en yüksek puanları gösterir. Bundan sonra puanlar, genel uyumluluk puanınıza sayılır.

**Test durumu "Başarısız" olarak ayarlanırsa**, eylem gereksinimleri karşılamıyorsa ve değerlendiren kişi, ek çalışma için uygun kullanıcıya geri atamaktadır.

## <a name="accepting-updates-to-improvement-actions"></a>Geliştirme eylemleri için güncelleştirmeleri kabul etme

Geliştirme işlemi için bir güncelleştirme mevcut olduğunda, adının yanında bir bildirim alırsınız. Güncelleştirmeyi kabul etmek veya daha sonra ertelemek için bu işlemi erteleyebilirsiniz.

#### <a name="what-causes-an-update"></a>Güncelleştirmeye neden olan nedir?

Puanlama, otomasyon veya kapsam ile ilgili değişiklikler olduğunda güncelleştirme gerçekleşir. Değişiklikler, mevzuat değişikliklerine dayalı iyileştirme eylemleri için yeni kılavuzlar veya ürün değişiklikleri nedeniyle olabilir. Yalnızca kuruluşlarınız tarafından yönetilen geliştirme eylemleri güncelleştirme bildirimleri alır.

#### <a name="where-youll-see-assessment-update-notifications"></a>Değerlendirme güncelleştirme bildirimlerini göreceğiniz yer

Geliştirme eylemi güncelleştirildiğinde geliştirme eylemleri sayfasında ve ilgili değerlendirmelerin ayrıntılar  sayfasında geliştirme adının yanında Bekleyen güncelleştirme etiketini görebilirsiniz.

Geliştirme eyleminin ayrıntılar sayfasına gidin ve değişikliklerle ilgili ayrıntıları gözden geçirmek, güncelleştirmeyi kabul etmek veya ertelemek için üst başlıkta yer alan Güncelleştirmeyi gözden geçir düğmesini seçin.

#### <a name="review-update-to-accept-or-defer"></a>Kabul etmek veya ertelemek için güncelleştirmeyi gözden geçirme

Geliştirme eylemi **ayrıntıları sayfasından** Güncelleştirmeyi gözden geçir'i seçdikten sonra, ekrannizin sağ tarafında bir açılır bölme görüntülenir. Uç nokta bölmesi, güncelleştirmeyle ilgili olarak, puanı ve kapsamı etkileyen değerlendirmeler ve değişiklikler gibi önemli ayrıntıları sağlar.

Geliştirme **eyleminin tüm** değişikliklerini kabul etmek için Güncelleştirmeyi kabul et'i seçin. **Kabul edilen değişiklikler kalıcıdır**.

> [!NOTE]
> Bir eyleme yönelik güncelleştirmeyi kabul etmek, bu eylemin diğer tüm sürümlerine veya örneklerinin güncelleştirmelerini de kabul edersiniz. Güncelleştirmeler, teknik işlemler için kiracı genelinde yalıtır ve teknik olmayan eylemler için grup genelinde yalıtır.

**İptal'i** seçmeniz, geliştirme eylemine uygulanmaz. Ancak siz güncelleştirmeyi kabul edene kadar **Bekleyen güncelleştirme** bildirimini görmeye devam edersiniz.

**Neden güncelleştirmeleri kabul etmenizi öneririz?**

Güncelleştirmeleri kabul etmek, çözümleri kullanma konusunda en güncel kılavuza sahip olmasını sağlar ve sertifikanın gereksinimlerini karşılamanıza yardımcı olacak uygun geliştirme eylemleri gerçekleştirebilir.

**Güncelleştirmeyi ertelemek istemeniz nedeni**

Geliştirme eylemini içeren bir değerlendirmeyi tamamlamanın ortasındaysanız, güncelleştirmeyi kabul edene kadar üzerinde çalışmanız bittiğinden emin olmak iyi olabilir. Gözden geçirme güncelleştirmesi çıkış bölmesinde İptal'i **seçerek** güncelleştirmeyi daha sonra ertelemeniz gerekir.

#### <a name="accept-all-updates-at-once"></a>Tüm güncelleştirmeleri bir kerede kabul etme

Birden çok güncelleştirmeniz varsa ve bunların hepsini bir defada kabul etmek için iyileştirme eylemleri tablonizin en üstünde Tüm güncelleştirmeleri kabul et bağlantısını seçin. Güncelleştirilecek eylem sayısını listeen bir çıkış bölmesi görüntülenir. Tüm **güncelleştirmeleri uygulamak için** Güncelleştirmeleri kabul et düğmesini seçin.

Geliştirme eylemleri sayfanıza geri dönüp sayfanın üst kısmında güncelleştirmelerin tamamlanması için sayfayı yenilemenizi isteyen bir ileti görebilirsiniz.

## <a name="set-up-alerts-for-improvement-action-changes"></a>Geliştirme eylemi değişiklikleri için uyarıları ayarlama

Uygulama veya test durumunda yapılan değişiklik ya da puanda artış veya düşüş gibi iyileştirme eylemlerinin oluştuğu durumlarda sizi hemen bilgilendirecek uyarılar kurabilirsiniz. Bu tür değişikliklerle ilgili hızlı bildirimler almak, olası uyumluluk risklerini takip etmeye yardımcı olabilir. Uyarıları [ayarlamayı öğrenmek için Uyumluluk Yöneticisi uyarılarını](compliance-manager-alert-policies.md) ve uyarı ilkelerini ziyaret edin.

## <a name="export-a-report"></a>Raporu dışarı aktarma

Ekranın **sol** üst köşesindeki Dışarı Aktar'ı seçerek tüm iyileştirme eylemlerinizi ve iyileştirme eylemleri sayfasında gösterilen filtre kategorilerini içeren bir Excel çalışma sayfasını indirin.