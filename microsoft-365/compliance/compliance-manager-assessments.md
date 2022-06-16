---
title: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme oluşturma ve yönetme
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
description: Kuruluşunuz için önemli olan düzenlemelerin ve sertifikaların gereksinimlerini karşılamanıza yardımcı olmak için Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirmeler oluşturun.
ms.openlocfilehash: cb2d90bf8dfbdcb2ec2ca534d1659a19d27998bc
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115751"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde değerlendirme oluşturma ve yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makalede:** **Değerlendirmeler** oluşturup yöneterek Kuruluşunuz için Uyumluluk Yöneticisi'nin nasıl özelleştirileceği hakkında bilgi edinin. Bu makalede değerlendirme oluşturma, bunları **gruplar** halinde düzenleme, **denetimlerle** çalışma, **güncelleştirmeleri** kabul etme ve değerlendirme **raporlarını** dışarı aktarma konusunda size yol gösterilir.

## <a name="introduction-to-assessments"></a>Değerlendirmelere giriş

Uyumluluk Yöneticisi, kuruluşunuz için geçerli olan sektör ve bölgesel düzenlemelere uyumluluğunuzu değerlendiren değerlendirmeler oluşturmanıza yardımcı olur. Değerlendirmeler, değerlendirmeyi tamamlamak için gerekli denetimleri, iyileştirme eylemlerini ve uygun olduğunda Microsoft eylemlerini içeren değerlendirme şablonları çerçevesine göre oluşturulur. Kuruluşunuz için en uygun değerlendirmeleri ayarlamak, uyumluluk riskinizi sınırlamak için ilkeleri ve operasyonel yordamları uygulamanıza yardımcı olabilir.

Tüm değerlendirmeleriniz Uyumluluk Yöneticisi'nin değerlendirmeler sekmesinde listelenir. [Değerlendirmelerinizin görünümünü filtreleme ve durum durumlarını yorumlama](compliance-manager-setup.md#assessments-page) hakkında daha fazla bilgi edinin.

> [!IMPORTANT]
> Değerlendirme oluşturmak için kuruluşunuzun kullanabileceği şablonlar lisans sözleşmenize bağlıdır. [Lisanslama ayrıntılarını gözden geçirin](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="data-protection-baseline-default-assessment"></a>Veri Koruma Temeli varsayılan değerlendirmesi

Microsoft, çalışmaya başlamanız için **Microsoft 365 veri koruma temeli** için Uyumluluk Yöneticisi'nde **varsayılan** bir değerlendirme sağlar. Bu temel değerlendirme, veri koruma ve genel veri idaresi için temel düzenlemelere ve standartlara yönelik bir dizi denetime sahiptir. Bu temel öncelikle NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) ve ISO (International Organization for Standardization) ile FedRAMP (Federal Risk ve Authorization Management Program) ve GDPR (Avrupa Birliği Genel Veri Koruma Yönetmeliği) öğelerini kullanır.

Bu değerlendirme, diğer değerlendirmeleri yapılandırmadan önce Uyumluluk Yöneticisi'ne ilk kez geldiğinizde ilk uyumluluk puanınızı hesaplamak için kullanılır. Uyumluluk Yöneticisi, Microsoft 365 çözümlerinizden ilk sinyalleri toplar. Kuruluşunuzun temel veri koruma standartlarına ve düzenlemelerine göre nasıl performans sergilediğini bir bakışta göreceksiniz ve gerçekleştirilecek önerilen iyileştirme eylemlerine göz atacaksınız.

Uyumluluk Yöneticisi, kuruluşunuzun özel gereksinimlerini karşılamak için kendi değerlendirmelerinizi oluşturup yönetdiğinizde daha yararlı hale gelir.

## <a name="understand-groups-before-creating-assessments"></a>Değerlendirme oluşturmadan önce grupları anlama

Değerlendirme oluşturduğunuzda, bunu bir gruba atamanız gerekir. Gruplar, değerlendirmeleri yıl veya düzenleme gibi sizin için mantıklı bir şekilde ya da kuruluşunuzun bölümlerine veya coğrafyalarına göre düzenlemenize olanak sağlayan kapsayıcılardır. Bu nedenle, değerlendirmeleri oluşturmadan önce bir gruplandırma stratejisi planlamanızı öneririz.

Aşağıda iki gruba ve bunların temel alınan değerlendirmelerine örnekler verilmiştir:

- **FFIEC IS değerlendirmesi 2020**
  - FFIEC IS
- **Veri güvenliği ve gizlilik değerlendirmeleri**
  - ISO 27001:2013
  - ISO 27018:2014

Bir grup veya grup içindeki farklı değerlendirmeler geliştirme eylemlerini paylaşabilir. İyileştirme eylemleri, iki öğeli kimlik doğrulamasını açma gibi kiracınıza eşlenen teknik çözümlerde veya yeni bir çalışma alanı ilkesi oluşturmak gibi sistem dışında gerçekleştirdiğiniz teknik olmayan eylemlerde yaptığınız değişiklikler olabilir. Teknik geliştirme eyleminde yaptığınız ayrıntılar veya durum güncelleştirmeleri tüm gruplar genelindeki değerlendirmeler tarafından alınır. Teknik olmayan geliştirme eylem güncelleştirmeleri, bunları uyguladığınız gruptaki değerlendirmeler tarafından tanınır. Bu, tek bir iyileştirme eylemi uygulamanıza ve aynı anda çeşitli gereksinimleri karşılamanıza olanak tanır.

### <a name="create-a-group"></a>Grup oluşturma

Yeni bir değerlendirme oluştururken grup oluşturabilirsiniz. Gruplar tek başına varlıklar olarak oluşturulamaz.

### <a name="what-to-know-when-working-with-groups"></a>Gruplarla çalışırken bilinmesi gerekenler

- Bir grup en az bir değerlendirme içermelidir.
- Grup adları kuruluşunuz içinde benzersiz olmalıdır.
- Grupların güvenlik özellikleri yoktur. Tüm izinler değerlendirmelerle ilişkilendirilir.
- Bir gruba değerlendirme eklediğinizde gruplandırma değiştirilemez.
- Mevcut bir gruba yeni bir değerlendirme eklerseniz, bu gruptaki değerlendirmelerden elde edilen genel bilgiler yeni değerlendirmeye kopyalanır.
- Aynı grup içindeki farklı değerlendirmelerdeki ilgili değerlendirme denetimleri tamamlandığında otomatik olarak güncelleştirilir.
- Gruplar aynı sertifikasyon veya düzenleme için değerlendirmeler içerebilir, ancak her grup belirli bir ürün sertifikası çifti için yalnızca bir değerlendirme içerebilir. Örneğin, bir grup Office 365 ve NIST CSF için iki değerlendirme içeremez. Bir grup, aynı ürün için birden çok değerlendirme içerebilir ancak her biri için karşılık gelen sertifikasyon veya düzenleme farklıysa.
- Değerlendirmenin silinmesi, bu değerlendirmeyle grup arasındaki ilişkiyi bozar.
- Gruplar silinemez.

## <a name="understand-templates-before-creating-assessments"></a>Değerlendirme oluşturmadan önce şablonları anlama

Değerlendirme şablonları, farklı gizlilik düzenlemelerine ve standartlarına yönelik sertifikasyonlara dayalı olarak değerlendirmeler için denetimler ve eylem önerileri içerir. Kuruluşunuz lisans sözleşmenize bağlı olarak en az bir ve muhtemelen daha fazla **dahil** edilen şablonla başlar. Kuruluşunuz ek **premium** şablonlar da satın alabilir.

Her şablon iki sürümde bulunur: biri Microsoft 365 (veya kullanılabilir diğer Microsoft ürünleri) ile kullanım için ve kullandığınız diğer ürünleri değerlendirmek için uyarlanabilir evrensel bir sürüm. Değerlendirmek istediğiniz ürün için uygun şablon türünü seçebilirsiniz.

Şablonlar hakkında daha fazla ayrıntı için [Bkz. Uyumluluk Yöneticisi'nde değerlendirme şablonları hakkında bilgi edinin](compliance-manager-templates.md).

## <a name="create-assessments"></a>Değerlendirme oluşturma

> [!NOTE]
> Değerlendirmeleri yalnızca Genel Yönetici, Uyumluluk Yöneticisi Yönetimi veya Uyumluluk Yöneticisi Değerlendiricisi rolüne sahip kullanıcılar oluşturabilir ve değiştirebilir. [Roller ve izinler](compliance-manager-setup.md#set-user-permissions-and-assign-roles) hakkında daha fazla bilgi edinin.

Başlamadan önce, hangi gruba atayabileceğinizi bildiğinizden veya bu değerlendirme için yeni bir grup oluşturmaya hazır olduğunuzdan emin olun. [Gruplar ve değerlendirmeler](#understand-groups-before-creating-assessments) hakkındaki ayrıntıları okuyun.

Değerlendirme oluşturmak için bir şablon seçmek ve ilişkili ürünü seçmek için kılavuzlu bir işlem kullanacaksınız. **Değerlendirmeler** sayfanızda, kuruluşunuz için en uygun değerlendirmeleri tek seferde tanımlamanıza ve hızlı bir şekilde ayarlamanıza yardımcı olan **Önerilen Değerlendirmeler Ekle** ile başlamanızı öneririz. Değerlendirme **ekle'yi** seçerek de değerlendirmeleri birer birer ayarlayabilirsiniz. Değerlendirme oluşturmaya başlamak için aşağıdaki adımları izleyin.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Kuruluş türünüz için önerilere dayalı değerlendirmeler oluşturma

Uyumluluk Yöneticisi hangi değerlendirmelerin kuruluşunuzla en ilgili olabileceğini gösterebilir. Kuruluşunuzun sektörü ve konumları hakkında temel bilgiler sağladığınızda, 300'den fazla şablondan oluşan kitaplığımızdan hangi şablonların kullanılacağını öneririz. Tek seferde birden çok değerlendirmenin hızlı kurulumu için önerilen şablonlar arasından seçim yapmanız yeterlidir.

Önerilerimize göre bir veya daha fazla değerlendirme oluşturmak için Değerlendirmeler **sayfanızdan** **Önerilen Değerlendirmeleri Ekle'yi** seçin ve şu adımları izleyin:

- Kuruluşunuzu tanımlayan bir veya daha fazla sektör seçin ve ardından **İleri'yi** seçin
- Kuruluşunuzun konumu için bir veya daha fazla bölge seçin ve ardından **İleri'yi** seçin
- Değerlendirme **seç** ekranında, Kuruluşunuz için geçerli olduğunu düşündüğümüz değerlendirmelerin listesini görmek için **Önerilen şablonlar'ın** yanındaki açılan oku seçin. Değerlendirme oluşturmak için kullanmak istediğiniz şablonların yanındaki kutuları işaretleyin ve **İleri'yi** seçin.
- Yeni değerlendirmelerinizi oluşturmak için son seçimlerinizi gözden geçirin ve **Önerilen Değerlendirmeler Ekle'yi** seçin.

#### <a name="create-an-assessment-using-a-guided-process"></a>Kılavuzlu işlem kullanarak değerlendirme oluşturma

1. **Değerlendirmeler** sayfanızdan **Değerlendirme ekle'yi** seçin. Bu sizi değerlendirme oluşturma sihirbazına yerleştirir.

2. **Temel şablon** ekranında **Şablon seç'i** seçerek değerlendirmenize yönelik şablonu seçin.

3. Açılır bölmede değerlendirmenin temel aldığı düzenleme veya sertifikasyon şablonunu seçin. Dahil edilen ve premium kategorilere ayrılmış şablonların listesi ([ayrıntıları alın](compliance-manager-templates.md#template-availability-and-licensing)). Açılır pencere bölmesinin en üstündeki **Etkinleştirilmiş/Lisanslı şablonlar** sayacı, kullandığınız şablonların kullanılabilir toplam sayıdan veya kuruluşunuzun kullanabileceği toplam sayıdan nasıl yararlanabileceğini gösterir ([daha fazla bilgi edinin](compliance-manager-templates.md#active-and-inactive-templates).) Seçtiğiniz şablonun yanındaki radyo düğmesini ve ardından **Kaydet'i** seçin. Şablon ayrıntılarını gözden geçirebileceğiniz **Temel şablon** ekranınıza dönecek ve **ardından İleri'yi** seçerek devam edebilirsiniz.

4. **Ürün, ad ve grup:** Değerlendirmenizi tanımlamak, hangi ürünü değerlendireceğini seçmek ve bir gruba atamak için bu özellikleri ayarlayın.

    - **Ürün**: Değerlendirmenizin uygulanmasını istediğiniz ürünü seçin. Microsoft 365 için tasarlanmış bir Şablon gibi bir Microsoft şablonu kullanıyorsanız, uygun ürünü belirtmeniz için bu alan doldurulur ve değiştirilemez. Evrensel bir şablon kullanıyorsanız, bu değerlendirmeyi yeni bir ürün için mi yoksa Uyumluluk Yöneticisi'nde önceden tanımlamış olduğunuz özel bir ürün için mi oluşturduğunuzu seçin. Yeni bir ürün seçerseniz adını girin. Evrensel şablon kullanırken önceden tanımlanmış bir Microsoft ürünü seçemeyeceğinizi unutmayın.
    - **Değerlendirme adı**: **Değerlendirme adı** alanına değerlendirmeniz için bir ad girin. Değerlendirme adları gruplar içinde benzersiz olmalıdır. Değerlendirmenizin adı belirli bir gruptaki başka bir değerlendirmenin adıyla eşleşiyorsa farklı bir ad oluşturmanızı isteyen bir hata alırsınız.
    - **Grup**: Değerlendirmenizi bir gruba atayın. Aşağıdakilerden birini yapabilirsiniz:
        - Zaten oluşturduğunuz **bir gruba atamak için Var olan grubu kullan'ı** seçin; Veya
        - **Yeni grup oluştur'u** seçerek yeni bir grup oluşturun ve bu değerlendirmeyi ona atayın:
            - Grubunuz için bir ad belirleyin ve radyo düğmesinin altındaki alana girin.
            - Uygulama ve test ayrıntıları ve belgeleri gibi **mevcut bir gruptaki verileri**, uygun kutuları seçerek kopyalayabilirsiniz.

    İşiniz bittiğinde **İleri'yi** seçin.

5. **Gözden geçir ve bitir:** Seçimlerinizi gözden geçirin ve gerekli düzenlemeleri yapın. Hazır olduğunuzda **Değerlendirme oluştur'u** seçin.

Sonraki ekranda değerlendirmenin oluşturulduğu onaylanır. **Bitti'yi** seçtiğinizde yeni değerlendirmenizin ayrıntılar sayfasına yönlendirilirsiniz.

Değerlendirme **oluştur'u** seçtikten sonra Değerlendirme **başarısız oldu** ekranını görürseniz değerlendirmenizi yeniden oluşturmak için **Yeniden deneyin'i** seçin.

Değerlendirmenizi oluşturduktan sonra, değerlendirmenin ayrıntılar sayfasının sağ üst köşesindeki **Adı düzenle** düğmesini seçerek [değerlendirmenizin](#monitor-assessment-progress-and-controls) adını değiştirebilirsiniz.

## <a name="monitor-assessment-progress-and-controls"></a>Değerlendirme ilerleme durumunu ve denetimlerini izleme

Her değerlendirmenin, değerlendirmeyi tamamlamadaki ilerlemenizi bir bakışta gösteren bir ayrıntılar sayfası vardır. Sayfada denetimleri tamamlamadaki ilerleme durumunuz ve bu denetimlerdeki önemli iyileştirme eylemlerinin test durumu gösterilir.

### <a name="overview-tab"></a>Genel Bakış sekmesi

Genel bakış sekmesi, değerlendirmenin tamamlanmasına yönelik yüzdenizi gösteren bir grafik içerir. Bu grafik, sahip olduğunuz eylemlerden ve Microsoft'un sahip olduğu eylemlerden alınan noktaların dökümünü içerir, böylece değerlendirmeyi tamamlamak için kaç puana daha ihtiyacınız olduğunu görebilirsiniz.

Değerlendirmedeki denetimler için önemli iyileştirme eylemleri, puan kazanmak için en büyük olası etki sırasına göre listelenir. İlişkili grafik, test edilenleri ve hala yapılması gerekenleri hızla ölçebilmeniz için iyileştirme eylemlerinizin toplu test durumunu ayrıntılarıyla açıklar.

Tek tek iyileştirme eylemlerine erişmek için **Denetimler** sekmesini veya **Geliştirme eylemleriniz** sekmesini ziyaret edin.

### <a name="controls-tab"></a>Denetimler sekmesi

Denetimler sekmesinde, değerlendirmeye eşlenen her denetim için ayrıntılı bilgiler görüntülenir. **Denetim durumu döküm** grafiği, aileye göre denetimlerin durumunu gösterir, böylece hangi denetim gruplarına dikkat etmeniz gerektiğini bir bakışta görebilirsiniz.

Grafiğin altında, bir tabloda değerlendirmedeki her denetimle ilgili ayrıntılı bilgiler listelenir. Denetimler, denetim ailesine göre gruplandırılır. Her aile adını genişleterek içerdiği denetimleri tek tek ortaya çıkar. Her denetim için listelenen bilgiler şunları içerir:

- **Denetim başlığı**
- **Durum**: Denetim içindeki iyileştirme eylemlerinin test durumunu yansıtır
  - **Başarılı -** tüm geliştirme eylemlerinin "başarılı" bir test durumu vardır veya en az biri geçirilir ve geri kalanı "kapsam dışı" olur
  - **Başarısız** - en az bir geliştirme eyleminin "başarısız" test durumu var
  - **Hiçbiri** - tüm iyileştirme eylemleri test edilmedi
  - **Kapsam dışında** - tüm iyileştirme eylemleri bu değerlendirmenin kapsamı dışında
  - **Devam ediyor** - geliştirme eylemlerinin yukarıda listelenenlerden farklı bir durumu vardır ve bu durum "devam ediyor", "kısmi kredi" veya "algılanmamış" olabilir
- **Denetim Kimliği**: denetimin ilgili düzenleme, standart veya ilke tarafından atanan kimlik numarası
- **Elde edilen puanlar**: Toplam ulaşılabilir puan sayısı dışında eylemleri tamamlayarak kazanılan puan sayısı
- **Eylemleriniz**: Gerçekleştirilecek toplam eylem sayısı dışında tamamlanan eylemlerinizin sayısı
- **Microsoft eylemleri**: Microsoft tarafından tamamlanan eylemlerin sayısı

Denetimin ayrıntılarını görüntülemek için tablodaki satırından bu denetimi seçin. Denetim ayrıntıları sayfasında, denetim içindeki eylemlerin test durumunu gösteren bir grafik gösterilir. Grafiğin altındaki tabloda bu denetim için önemli iyileştirme eylemleri gösterilir.

İyileştirme eyleminin ayrıntılar sayfasında detaya gitmek için listeden bir iyileştirme eylemi seçin. Ayrıntılar sayfasında test durumu ve uygulama notları gösterilir ve önerilen çözüme başlatılır.

### <a name="your-improvement-actions-tab"></a>Geliştirme eylemleri sekmeniz

geliştirme eylemlerinizin sekmesi, değerlendirmedeki kuruluşunuz tarafından yönetilen tüm denetimleri listeler. Durum çubuğu değerlendirmedeki iyileştirme eylemlerinizin toplam test durumunu ayrıntılı olarak açıklar, böylece test edilenleri ve hala yapılması gerekenleri hızla ölçebilirsiniz. Çubuğun altında iyileştirme eylemlerinin ve önemli ayrıntıların tam listesi yer alır: test durumu, potansiyel ve kazanılmış puan sayısı, ilişkili düzenlemeler ve standartlar, geçerli çözüm, eylem türü ve denetim ailesi. [Eylemlerin uyumluluk puanınıza nasıl katkıda bulunduğu](compliance-score-calculation.md#action-types-and-points) hakkında daha fazla bilgi edinin.

Ayrıntılarını görüntülemek için bir iyileştirme eylemi seçin ve işlem yapmak üzere çözümü açmak için **Şimdi başlat** bağlantısını seçin.

### <a name="microsoft-actions-tab"></a>Microsoft eylemler sekmesi

Microsoft ürünlerini destekleyen şablonlara dayalı değerlendirmeler için Microsoft eylemleri sekmesi görüntülenir. Değerlendirmedeki Microsoft tarafından yönetilen tüm eylemleri listeler. Listede test durumu, genel uyumluluk puanınıza katkıda bulunan puanlar, ilgili düzenlemeler ve standartlar, geçerli çözüm, eylem türü ve denetim ailesi gibi önemli eylem ayrıntıları gösterilir. Ayrıntılar sayfasını görüntülemek için bir iyileştirme eylemi seçin.

[Denetimlerin ve iyileştirme eylemlerinin nasıl izlendiği ve puanlandığı](compliance-score-calculation.md) hakkında daha fazla bilgi edinin.

## <a name="accept-updates-to-assessments"></a>Değerlendirme güncelleştirmelerini kabul etme

Değerlendirme için bir güncelleştirme kullanılabilir olduğunda bir bildirim görürsünüz ve güncelleştirmeyi kabul etme veya daha sonra erteleme seçeneğine sahip olursunuz.

Güncelleştirmeler, Microsoft 365 ile kullanılmak üzere tasarlanmış olanlar gibi Microsoft şablonlarını temel alan değerlendirmeler için kullanılabilir. Kuruluşunuz diğer ürünleri değerlendirmek için evrensel şablonlar kullanıyorsa devralma desteklenmiyor olabilir. Daha fazla bilgi için bkz. [Değerlendirme şablonlarını genişletme](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Güncelleştirmeye neden olan nedenler

Puanlamayı etkileyen temel şablon değişiklikleri olduğunda değerlendirme güncelleştirmesi gerçekleşir. Değişiklikler, denetim eşlemesini ayarlamayı veya mevzuat değişikliklerine veya ürün değişikliklerine göre diğer yönergeleri içerebilir. Değerlendirme güncelleştirmeleri kuruluşunuzdan ( [örneğin, özel bir şablon değiştirildiğinde](compliance-manager-templates-modify.md)) ve Microsoft'tan kaynaklanabilir.

Microsoft, uzattığınız bir Uyumluluk Yöneticisi şablonunu güncelleştirirse, değerlendirmeniz bu güncelleştirmeleri kabul ettikten sonra devralır. Değerlendirmeniz, bunu genişlettiğinizde değerlendirmeye uyguladığınız ek öznitelikleri korur.

Oluşturduğunuz özel değerlendirmeler Microsoft'tan şablon güncelleştirmesi almaz. Özel değerlendirmeler geliştirme eylem güncelleştirmeleri alabilir, ancak değerlendirmeler ve iyileştirme eylemleri arasındaki eşlemeyi denetlemek için yapılan microsoft güncelleştirmeleri özel şablonlar için geçerli değildir.

> [!NOTE]
> Değerlendirme güncelleştirmeleri yalnızca grup düzeyinde geçerlidir. İki farklı grupta bulunan aynı şablondan oluşturulmuş iki değerlendirmeniz varsa, her değerlendirmenin bekleyen bir güncelleştirme bildirimi olur ve ilgili gruptaki her değerlendirmeye yönelik güncelleştirmeyi tek tek kabul etmeniz gerekir.

#### <a name="where-youll-see-assessment-update-notifications"></a>Değerlendirme güncelleştirme bildirimlerini nerede görürsünüz?

Değerlendirme ayrıntıları sayfasında, değerlendirmenin yanında bir **güncelleştirme içeren Bekleyen güncelleştirme** etiketi de gösterilir. Ayrıntılar sayfasına ulaşmak için bu değerlendirmeyi seçin.

Değerlendirme ayrıntıları sayfasının üst kısmına yakın bir ileti, söz konusu değerlendirme için bir güncelleştirmenin kullanılabilir olduğunu gösterir. Belirli değişiklikleri gözden geçirmek ve güncelleştirmeyi kabul etmek veya ertelemek için başlıktaki güncelleştirmeyi **gözden geçir** düğmesini seçin.

Değerlendirme ayrıntıları sayfasında, yanında **Bekleyen güncelleştirme** etiketi bulunan iyileştirme eylemleri de listelenebilir. Bu güncelleştirmeler, iyileştirme eylemlerinin kendisinde yapılan belirli değişikliklere yöneliktir ve ayrı olarak kabul edilmesi gerekir. Daha fazla bilgi edinmek [için iyileştirme eylemlerine güncelleştirmeleri kabul etme](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) sayfasını ziyaret edin.

#### <a name="review-update-to-accept-or-defer"></a>Kabul etmek veya ertelemek için güncelleştirmeyi gözden geçirin

Değerlendirme ayrıntıları sayfasında **güncelleştirmeyi gözden geçir'i** seçtikten sonra ekranınızın sağ tarafında bir açılır pencere bölmesi görüntülenir. Açılır pencere bölmesi, bekleyen güncelleştirme hakkında aşağıdaki önemli ayrıntıları sağlar:

- Şablon başlığı
- Güncelleştirmenin kaynağı (Microsoft, kuruluşunuz veya belirli bir kullanıcı)
- Güncelleştirmenin oluşturulduğu tarih
- Güncelleştirmeyi açıklayan bir genel bakış
- Uyumluluk puanınıza etkisi, değerlendirmenin tamamlanmasına yönelik ilerleme miktarı ve iyileştirme eylemleri ve denetimlerindeki belirli değişiklik sayısı gibi değişikliklerle ilgili belirli ayrıntılar.

**Güncelleştirilmiş şablon** bağlantısı seçildiğinde, bekleyen güncelleştirmelerle şablonun sürümü için denetim verilerini içeren bir Excel dosyası indirilir. **Geçerli şablon** bağlantısı seçildiğinde, değişiklikler olmadan mevcut şablonun bir dosyası indirilir.

Güncelleştirmeyi kabul etmek ve değerlendirmenizde değişiklik yapmak için **Güncelleştirmeyi kabul et'i** seçin. Kabul edilen değişiklikler kalıcıdır.

**İptal'i** seçerseniz güncelleştirme değerlendirmeye uygulanmaz. Ancak, güncelleştirmeyi kabul edene kadar **Bekleyen güncelleştirme** bildirimini görmeye devam edersiniz.

**Güncelleştirmeleri kabul etmenizi neden öneririz?**

Güncelleştirmeleri kabul etmek, elinizdeki sertifikasyon gereksinimlerini karşılamanıza yardımcı olmak için çözümleri kullanma ve uygun iyileştirme eylemleri gerçekleştirme konusunda en güncel rehberliğe sahip olduğunuzdan emin olmanıza yardımcı olur.

**Bir güncelleştirmeyi neden ertelemek isteyebilirsiniz?**

Değerlendirmeyi tamamlamanın ortasındaysanız, denetim eşlemesini kesintiye uğratabilecek bir değerlendirme güncelleştirmesini kabul etmeden önce üzerinde çalışmayı tamamladığınızdan emin olmak isteyebilirsiniz. Gözden geçirme güncelleştirmesi açılır bölmesinde **İptal'i** seçerek güncelleştirmeyi daha sonra erteleyebilirsiniz.

## <a name="export-an-assessment-report"></a>Değerlendirme raporunu dışarı aktarma

Kuruluşunuzdaki uyumluluk paydaşları veya dış denetçiler ve düzenleyiciler için değerlendirmeyi bir Excel dosyasına aktarabilirsiniz. Değerlendirme ayrıntıları sayfanızda, sayfanın üst kısmındaki **Rapor oluştur** düğmesini seçin. Bu düğme, kaydedip paylaşabileceğiniz bir Excel dosyası oluşturur.

Rapor, dışarı aktarmanın tarih ve saati itibarıyla değerlendirmenin anlık görüntüsüdür. Uygulama durumu, test tarihi ve test sonuçları dahil olmak üzere hem sizin hem de Microsoft tarafından yönetilen denetimlerin ayrıntılarını içerir.

## <a name="delete-an-assessment"></a>Değerlendirmeyi silme

Değerlendirmeyi silmek, değerlendirmeler sayfanızdaki listeden kaldırır. Değerlendirmeleri silmeyle ilgili şu önemli noktalara dikkat edin:

- **Değerlendirmenin silinmesi kalıcıdır; Geri alamazsınız.** Aynı değerlendirmeyi yeniden kullanmak istiyorsanız yeniden oluşturmanız gerekir.
- Değerlendirmedeki iyileştirme eylemleri başka bir değerlendirmede görünmüyorsa, değerlendirme silindiğinde silinir.
- Değerlendirme raporunu kalıcı olarak silmeden önce [dışarı aktarmanızı](#export-an-assessment-report) öneririz.

Değerlendirmeyi silmek için aşağıdaki adımları izleyin:

1. **Değerlendirmeler** sayfanızdan silmek istediğiniz değerlendirmeyi seçerek değerlendirmenin ayrıntılar sayfasını açın.

2. Ekranınızın sağ üst köşesinde değerlendirmeyi **sil'i** seçin.

3. Değerlendirmeyi kalıcı olarak silmek istediğinizi onaylamanızı isteyen bir pencere görüntülenir. Pencereyi kapatmak için **Değerlendirmeyi sil'i** seçin. Değerlendirmenizin Uyumluluk Yöneticisi'nden silindiğini belirten bir onay penceresi alırsınız.

> [!NOTE]
> Tüm değerlendirmelerinizi silemezsiniz. Uyumluluk Yöneticisi'nin düzgün çalışması için kuruluşların en az bir değerlendirmeye ihtiyacı vardır. Silmek istediğiniz değerlendirme tek değerlendirmeyse, diğer değerlendirmeyi silmeden önce başka bir değerlendirme ekleyin.
