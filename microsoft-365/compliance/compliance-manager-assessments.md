---
title: Microsoft Uyumluluk Yöneticisi'nde değerlendirmeleri oluşturma ve yönetme
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
description: Microsoft Uyumluluk Yöneticisi'nde, organizasyonunız için önemli olan yasal düzenlemeler ve sertifikalara ilişkin gereksinimleri karşılamanıza yardımcı olacak değerlendirmeler sağlayın.
ms.openlocfilehash: 950178b638b020e9d44301db3a335c73bbb55311
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016645"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde değerlendirmeleri oluşturma ve yönetme

**Bu makalede:** Değerlendirmeler oluşturarak ve yöneterek, kuruluş için Uyumluluk Yöneticisi'ni nasıl **özelleştirebileceğinizi öğrenin**. Bu makalede değerlendirmeleri oluşturma, bunları gruplar halinde **düzenleme, denetimlerle** **çalışma, güncelleştirmeleri** kabul etme ve değerlendirme raporlarını dışarı aktarma gibi makalelerde size yol **gösterir**.

## <a name="introduction-to-assessments"></a>Değerlendirmelere giriş

Uyumluluk Yöneticisi, organizasyonunıza uygun endüstri ve bölgesel düzenlemelere uygunluğunızı değerlendiren değerlendirmeler oluşturmanıza yardımcı olur. Değerlendirmeler, gerekli denetimleri, geliştirme eylemlerini ve uygun olduğunda değerlendirmeyi tamamlamak için Microsoft eylemlerini içeren değerlendirme şablonları çerçevesi üzerine temel alınarak hazırlar. Organizasyon için en uygun değerlendirmeleri ayarlama, uyumluluk risklerinizi sınırlandıracak ilkeler ve işlem yordamları uygulamanıza yardımcı olabilir.

Tüm değerlendirmeleriniz Uyumluluk Yöneticisi'nin değerlendirmeler sekmesinde listelenir. Değerlendirmelerinizi görüntüleme [ve durum durumlarını yorumlama hakkında daha fazla bilgi edinmek için](compliance-manager-setup.md#assessments-page):

> [!IMPORTANT]
> Değerlendirme oluşturmak için organizasyonda kullanılabilen şablonlar lisans sözleşmenize bağlıdır. [Lisans ayrıntılarını gözden geçirebilirsiniz](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="data-protection-baseline-default-assessment"></a>Veri Koruma Temeli varsayılan değerlendirme

Çalışmaya başlamanız için, Microsoft Uyumluluk **Yöneticisi'nde** veri koruma temeli Microsoft 365 **değerlendirmesini sağlar**. Bu temel değerlendirme, veri koruma ve genel veri idaresi için temel düzenlemeler ve standartlar için bir dizi denetim içerir. Bu taban çizgisi öncelikle NIST CSF (Ulusal Standartlar ve Teknoloji Enstitüsü Cybersecurity Framework) ve ISO (Standartlaştırma için Uluslararası Kuruluş) ile FedRAMP (Federal Risk ve Yetkilendirme Yönetim Programı) ve GDPR (Avrupa Birliği Genel Veri Koruma Yönetmeliği) kaynaklarından gelen öğeleri çizmektedir.

Bu değerlendirme, Uyumluluk Yöneticisi'ne ilk gelirken diğer değerlendirmeleri yapılandırmadan önce ilk uyumluluk puanınızı hesaplamak için kullanılır. Uyumluluk Yöneticisi veri çözümlerinden başlangıç Microsoft 365 toplar. Kuruluşlarının önemli veri koruma standartları ve yasal düzenlemelere göre nasıl performans gösterirken bir bakışta bakarak gerçekleştirmesi önerilen geliştirme işlemlerine bakabilirsiniz.

Uyumluluk Yöneticisi, siz kendi değerlendirmelerinizi, sizin özel  ihtiyaçlarını karşılarken ve yönetirken daha yararlı hale gelir.

## <a name="understand-groups-before-creating-assessments"></a>Değerlendirme oluşturmadan önce grupları anlama

Değerlendirme  oluşturmak için, bunu bir gruba atamalısiniz. Gruplar, yıl veya düzenlemeye göre ya da kuruluş bölmelerine veya coğrafi bölümlere göre sizin için mantıksal bir düzende değerlendirmelerinizi düzenlemenize olanak sağlayan kapsayıcılardır. İşte bu nedenle değerlendirmeleri oluşturmadan önce bir gruplama stratejisi planlamanızı öneririz.

Aşağıda iki gruba ve onun temel değerlendirmelerine örnekler verilmiştir:

- **FFIEC IS değerlendirme 2020**
  - FFIEC IS
- **Veri güvenliği ve gizlilik değerlendirmeleri**
  - ISO 27001:2013
  - ISO 27018:2014

Bir grup veya grup içindeki farklı değerlendirmeler geliştirme eylemlerini paylaşabilir. Geliştirme eylemleri, kiracınıza eşlenen teknik çözümler içinde yaptığınız, iki faktörlü kimlik doğrulamasını açma gibi değişiklikler veya yeni bir iş yeri ilkesi olduğu gibi sistem dışında gerçekleştir yaptığınız teknik olmayan işlemler olabilir. Teknik geliştirme eylemlerini ayrıntılı olarak veya durum bilgisinde yapılan tüm güncelleştirmeler, tüm gruplarda değerlendirmeler tarafından alır. Teknik olmayan geliştirme işlemi güncelleştirmeleri, bunları uygulayan grup içindeki değerlendirmeler tarafından tanınır. Bu sayede tek bir geliştirme eylemi gerçekleştirebilirsiniz ve aynı anda çeşitli gereksinimleri karşılarsiniz.

### <a name="create-a-group"></a>Grup oluşturma

Yeni değerlendirme oluştururken bir grup da oluşturabilirsiniz. Gruplar tek başına varlıklar olarak oluşturulamıyor.

### <a name="what-to-know-when-working-with-groups"></a>Gruplarla çalışırken neleri bilmek gerekir?

- Bir grup en az bir değerlendirme içerebilir.
- Grup adları, kurum içinde benzersiz olmalıdır.
- Grupların güvenlik özellikleri yok. Tüm izinler değerlendirmelerle ilişkilendirildi.
- Bir gruba değerlendirme eklenin ardından, gruplama değiştirilemez.
- Var olan bir gruba yeni bir değerlendirme eklersiniz, bu gruptaki değerlendirmelerden genel bilgiler yeni değerlendirmeye kopyalanır.
- Aynı grup içindeki farklı değerlendirmelerde bulunan ilgili değerlendirme denetimleri tamamlandığında otomatik olarak güncelleştirmesi yapılır.
- Gruplar aynı sertifika veya düzenleme için değerlendirmeler içerebilir, ancak her grup belirli bir ürün-sertifika çifti için yalnızca bir değerlendirme içerebilir. Örneğin, bir grup, HER IKI DEĞERLENDIRME ve NIST CSF Office 365 değerlendirmeleri içerer. Bir grup, aynı ürün için birden çok değerlendirme içerebilir, ancak her bir ürün için ilgili sertifika veya düzenleme farklı olabilir.
- Değerlendirmenin silinmesi, bu değerlendirmeyle grup arasındaki ilişkiyi bozar.
- Gruplar el ile silinemez.

## <a name="understand-templates-before-creating-assessments"></a>Değerlendirme oluşturmadan önce şablonları anlama

Değerlendirme şablonları, farklı gizlilik düzenlemelerine ve standartlara ilişkin sertifikalara dayalı olarak değerlendirmelere ilişkin denetimleri ve eylem önerilerini içerir. Kuruluşun kullanılabilir şablonları, lisans sözleşmenizin bir parçası olarak dahil edilen bir veya daha fazla şablonu ve satın aldığınız diğer premium şablonları içerebilir.

İster dahil olun, ister premium olsun her şablon iki sürümde yer almaktadır: biri Microsoft 365 (veya kullanılabilir diğer Microsoft ürünleriyle) kullanım için ve diğeri de kullanabileceğiniz diğer ürünleri değerlendirmek için uyarlanmış evrensel sürüm. Değerlendirmek istediğiniz ürün için uygun şablon türünü seçebilirsiniz.

Şablonlar hakkında daha fazla bilgi edinmek için değerlendirme [şablonlarıyla çalışma'ya bakın](compliance-manager-templates.md).

## <a name="create-assessments"></a>Değerlendirmeler oluşturma

> [!NOTE]
> Değerlendirmeleri yalnızca Genel Yönetici, Uyumluluk Yöneticisi Yönetimi veya Uyumluluk Yöneticisi Değerlendiren rolüne sahip olan kullanıcılar oluşturabilir ve değiştirebilir. Roller ve izinler [hakkında daha fazla bilgi edinmek için](compliance-manager-setup.md#set-user-permissions-and-assign-roles):

Başlamadan önce, bunu hangi gruba atay o gruba atay tamamlaydığınızdan emin olun veya bu değerlendirme için yeni bir grup oluşturmak üzere hazır olun. Gruplar ve [değerlendirmeler hakkında ayrıntıları okuyun](#understand-groups-before-creating-assessments).

Değerlendirme oluşturmak için, kılavuzlu bir işlem kullanarak bir şablon seçer ve ilişkili ürünü belirlemezsiniz. Değerlendirmeler **sayfanız** üzerinde, tüm değerlendirmeleri aynı anda hem tanımlamanıza hem de hızla ayarlaymanıza yardımcı olan Önerilen Değerlendirmeleri Ekle'den başlamanızı öneririz. Değerlendirme ekle'yi seçerek değerlendirmeleri tek tek **de kurabilirsiniz**. Değerlendirmeler etmeye başlamak için aşağıdaki adımları izleyin.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Kuruluş türünüz için önerilere dayalı değerlendirmeler oluşturma

Uyumluluk Yöneticisi, hangi değerlendirmelerin sizin için en uygun olacağını belirt olabilir. Kuruluşun endüstri ve konumları hakkında temel bilgiler sağlarken, 300'den fazla şablondan bulunan kitaplığımızda hangi şablonların kullanıla birlikte kullanılması önerilir. Birden çok değerlendirmenin hızlı kurulumu için önerilen şablonlar arasından bir kerede seçim yapmanız gerekir. 

Önerilerimizi temel alarak bir veya daha fazla değerlendirme oluşturmak için, Değerlendirmeler  sayfanıza Önerilen Değerlendirmeler **Ekle'yi** seçin ve şu adımları izleyin:
   - Organizasyonlarınızı tanımlamak için bir veya daha fazla endüstri seçin ve sonra da Sonraki'yi **seçin.**
   - Kuruluş konumu için bir veya daha fazla bölge seçin ve ardından Sonraki'yi **seçin**
   - Değerlendirme **seçin ekranında**, organizasyonunız için geçerli olduğunu düşünüyoruz değerlendirmelerin  listesini görmek için Önerilen şablonlar'ın yanındaki açılan oku seçin. Değerlendirme oluşturmak için kullanmak istediğiniz şablonların yanındaki kutuları işaretleyin ve sonra Sonraki'yi **seçin**.
   - Son seçimlerinizi gözden geçirerek yeni **değerlendirmelerinizi oluşturmak için Önerilen** Değerlendirmeleri Ekle'yi seçin.

#### <a name="create-an-assessment-using-a-guided-process"></a>Rehberli bir işlemi kullanarak değerlendirme oluşturma

1. Değerlendirmeler **sayfanız için** Değerlendirme **ekle'yi seçin**. Bu sizi değerlendirme oluşturma sihirbazına getirir.

2. Temel şablon **ekranında** Şablon **seç'i seçerek** değerlendirmenize uygun şablonu seçin.

3. Uçarak çıkış bölmesinde, değerlendirmeyi temel alan düzenleme veya sertifika için şablonu seçin. Dahil edilen ve premium kategorilere ayrılmış şablonların listesi ([ayrıntılara bakın](compliance-manager-templates.md#template-availability-and-licensing)). Uç **uç bölmenin** üst kısmında bulunan Etkinleştirilmiş/Lisanslı şablonlar sayaçları, toplam kullanılabilir veya kuruluş içinde kullanmak üzere kaç şablon kullanabileceğinizi gösterir (daha fazla [bilgi alın](compliance-manager-templates.md#active-and-inactive-templates).) Seçtiğiniz şablonun yanındaki radyo düğmesini seçin ve sonra da Kaydet'i **seçin**. Temel şablon ekranınıza **dönersiniz ve burada** şablon ayrıntılarını gözden geçirebilirsiniz ve sonra Sonraki'yi seçerek devam **edin**.

4. **Ürün, ad ve grup:** Değerlendirmenizi tanımlamak için bu özellikleri ayarlayın, değerlendirecek ürünü seçin ve bir gruba attayabilirsiniz.

    - **Ürün**: Değerlendirmenizin uygulamak istediğiniz ürünü seçin. Microsoft şablonu kullanıyorsanız (örneğin, iş Microsoft 365 şablonu) bu alan sizin için uygun ürünü belirtecek şekilde doldurulur ve değiştirilemez. Evrensel şablon kullanıyorsanız, bu değerlendirmeyi yeni bir ürün için mi yoksa Uyumluluk Yöneticisi'nde önceden tanımmış olduğunuz özel bir ürün için mi oluşturuyorsanız seçin. Yeni bir ürün seçerseniz, adını girin. Evrensel bir şablon kullanırken önceden tanımlanmış bir Microsoft ürünü seçeyleylene kadar, bunu seçeyyebilirsiniz.
    - **Değerlendirme adı**: Değerlendirme adı alanına değerlendirmeniz **için bir ad** girin. Değerlendirme adları, grupların içinde benzersiz olmalıdır. Değerlendirmenizin adı herhangi bir gruptaki başka bir değerlendirmenin adıyla eş eşleşense, farklı bir ad oluşturmanızı isteyen bir hata alırsınız.
    - **Grup**: Değerlendirmenizi gruba atama. Şunları da s kaydettiysiniz:
        - Mevcut **grubu zaten oluşturduğunuz** bir gruba atamak için Varolan grubu kullan'ı seçin; veya
        - Yeni **grup oluşturmak ve** bu değerlendirmeyi bu gruba atamak için Yeni grup oluştur'a seçin:
            - Grubunuz için bir ad belirleyin ve radyo düğmesinin altındaki alana girin.
            - Uygun **kutuları seçerek var olan bir** gruptan (uygulama ve test ayrıntıları ve belgeler gibi) veri kopyaabilirsiniz.

    Bitirdikten sonra, Sonraki'yi **seçin**.

5. **Gözden geçir ve bitir:** Seçimlerinizi gözden geçirin ve gerekli düzenlemeleri yapın. Hazır olduğunuz zaman Değerlendirme **oluştur'a seçin**.

Sonraki ekran değerlendirmenin oluşturulmuş olduğunu onaylar. **Bitti'yi** seçerek yeni değerlendirmenizin ayrıntılar sayfasına gidin.

Değerlendirme oluştur'a **tıklayın öğesinin** ardından **Değerlendirme başarısız oldu** ekranını görüyorsanız, değerlendirmenizi yeniden **oluşturmak için Yeniden** dene'yi seçin.

Değerlendirmenin ayrıntılar sayfasının sağ üst köşesindeki Adı düzenle düğmesini seçerek, oluşturduklardan  sonra [değerlendirmenizin adını değiştirebilirsiniz](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Değerlendirme ilerlemesini ve denetimlerini izleme

Her değerlendirmenin, değerlendirmeyi tamamlamayla ilgili ilerlemenizi tek bakışta görmek için bir ayrıntı sayfası vardır. Bu sayfada, denetimleri tamamlama ilerleme durumunuz ve bu denetimler içindeki önemli geliştirme eylemlerinin test durumu görüntülenir.

### <a name="overview-tab"></a>Genel Bakış sekmesi

Genel bakış sekmesi, değerlendirmeyi tamamlamaya yönelik yüzdenizi gösteren bir grafik içerir. Bu grafik, sahip olduğu eylemlerden puanların dökümünü ve Microsoft'un sahip olduğu eylemlerden puanları içerir; böylece değerlendirmeyi tamamlamak için daha kaç puana ihtiyacınız olduğunu görebilirsiniz.

Değerlendirmedeki denetimler için önemli geliştirme eylemleri, puan kazanmak için olası en büyük etkiyi sırasıyla listelenmiştir. İlişkili grafikte, nelerin test edilmiş ve nelerin yapılması gerektiğini hızla ölçebilirsiniz ve böylece geliştirme eylemlerinizin toplanan test durumu ayrıntıları gösterilir.

Tek tek geliştirme eylemlerine erişmek için **Denetimler sekmesini** veya Geliştirme **eylemleriniz sekmesini ziyaret** edin.

### <a name="controls-tab"></a>Denetimler sekmesi

Denetimler sekmesinde, değerlendirmeyle eşlenen her denetim için ayrıntılı bilgiler görüntülenir. Denetim **durumu çözümleme grafiği** ailelere göre denetimlerin durumunu gösterir, böylece hangi denetim gruplamalarının dikkat çekmesi gerektir olduğunu bir bakışta görebilirsiniz.

Grafiğin altında yer alan tablo, değerlendirme içindeki her denetimle ilgili ayrıntılı bilgileri listeler. Denetimler, denetim ailesine göre gruplandı. Içerdiği tek tek denetimleri ortaya çıkarmak için her bir aile adını genişletin. Her denetim için listelenen bilgiler şunları içerir:

- **Denetim başlığı**
- **Durum**: Denetim içindeki geliştirme eylemlerinin test durumunu gösterir 
    - **Geçildi** - tüm iyileştirme eylemlerinin "geçti" durumu vardır veya en az bir tane geçirildi ve geri kalanı "kapsamın dışında"
    -  **Başarısız** - en az bir geliştirme eyleminin "başarısız" durumu vardır
    - **Yok** - tüm geliştirme eylemleri sınanmamıştır
    - **Kapsam dışında -** bu değerlendirme için tüm geliştirme eylemleri kapsam dışında
    - **Sürüyor** - geliştirme eylemlerinin durumu yukarıda listelenenlerden farklı bir durumla birliktedir ve bu durum "sürüyor", "kısmi kredi" veya "algılanmadı" olabilir
- **Denetim Kimliği**: denetimin ilgili düzenleme, standart veya ilke ile atanan kimlik numarası
- **Elde edilen** puanlar: eylemleri tamamlayarak kazanılan puan sayısı, elde edilebilir toplam puanın dışında 
- **Eylemleriniz**: yapılacak toplam eylem sayısının dışında tamamlanan eylemlerinizin sayısı
- **Microsoft eylemleri**: Microsoft tarafından tamamlanan eylem sayısı

Bir denetimin ayrıntılarını görüntülemek için, denetimi tablodaki satırından seçin. Denetim ayrıntıları sayfasında, bu denetim içindeki eylemlerin test durumunu gösteren bir grafik gösterilir. Grafiğin altındaki tabloda bu denetim için önemli geliştirme eylemleri gösterilir.

Geliştirme eyleminin ayrıntılar sayfasında detaya inme için listeden bir geliştirme eylemi seçin. Ayrıntılar sayfasında test durumu ve uygulama notları görüntülenir ve önerilen çözüme ekleyebilirsiniz.

### <a name="your-improvement-actions-tab"></a>Geliştirme eylemleriniz sekmesi

Geliştirme eylemlerinizin sekmesi, değerlendirmede kurum tarafından yönetilen tüm denetimleri listeler. Durum çubuğu, nelerin test edilmiş ve nelerin yine de yapılması gerektiğini hızlı bir şekilde ölçmek için değerlendirmedeki geliştirme eylemlerinizin toplanan test durumunu ayrıntılarıyla ayrıntılarıyla gösterir. Çubuğun altında geliştirme eylemlerinin ve önemli ayrıntıların tam listesi vardır: test durumu, potansiyel ve kazanılan puan sayısı, ilişkili yasal düzenlemeler ve standartlar, uygulanabilir çözüm, eylem türü ve aileyi kontrol edin. Eylemlerin uyumluluk [puanınıza nasıl katkıda bulunmakla ilgili daha fazla bilgi edinin](compliance-score-calculation.md#action-types-and-points).

Ayrıntıları sayfasını görüntülemek için bir geliştirme eylemi seçin ve **önlem almak için** çözümü açmak için Şimdi başlat bağlantısını seçin.

### <a name="microsoft-actions-tab"></a>Microsoft eylemler sekmesi

Microsoft ürünlerini destekleyen şablonlara dayalı değerlendirmeler için Microsoft eylemleri sekmesi görüntülenir. Değerlendirmede, Microsoft tarafından yönetilen tüm eylemler liste içerir. Liste, test durumu, genel uyumluluk puanınıza katkıda bulunan puanlar, ilişkili yasal düzenlemeler ve standartlar, uygulanabilir çözüm, eylem türü ve aileyi kontrol gibi önemli eylem ayrıntılarını gösterir. Ayrıntıları sayfasını görüntülemek için bir geliştirme eylemi seçin.

Denetimlerin ve [geliştirme eylemlerinin nasıl izlen yaptıkları ve puanlandıkları hakkında daha fazla bilgi edinmek için:](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Değerlendirme güncelleştirmelerini kabul etme

Değerlendirme için bir güncelleştirme kullanılabilir olduğunda, bir bildirim alır ve güncelleştirmeyi kabul etme veya daha sonra erteleme seçeneğiniz olur.

### <a name="what-causes-an-update"></a>Güncelleştirmeye neden olan nedir?

Değerlendirme güncelleştirmesi, puanlamayı etkileyen temel şablon değişiklikleri olduğunda oluşur. Değişiklikler, denetim eşlemesini veya mevzuat değişikliklerine veya ürün değişikliklerine dayalı olarak diğer kılavuzu ayarlamayı içeriyor olabilir. Değerlendirme güncelleştirmeleri, (örneğin, özel bir şablonun yanı sıra Microsoft'tan da değiştirildiğinde [) sizin](compliance-manager-templates-modify.md) organizasyondan kaynakleştirilebilir.

Microsoft uzattıktan sonra bir Uyumluluk Yöneticisi şablonunu güncellerse, değerlendirmeniz bu güncelleştirmeleri kabul ettiyken devralacak. Değerlendirmeniz, genişletilen değerlendirmeye uygulanan ek öznitelikleri korur.

Kendi özel değerlendirmeleri Microsoft'tan hiçbir şablon güncelleştirmesi almaz. Özel değerlendirmeler geliştirme eylem güncelleştirmeleri alsa da, değerlendirmelerle geliştirme eylemleri arasındaki eşlemeyi denetlemeye ilişkin tüm Microsoft güncelleştirmeleri özel şablonlara uygulanamaz.

> [!NOTE]
> Değerlendirmelerde yapılan güncelleştirmeler yalnızca grup düzeyinde geçerlidir. Aynı şablonda iki farklı grupta yer alan iki değerlendirmeniz varsa, her değerlendirmede bekleyen bir güncelleştirme bildirimi olur ve ilgili gruptaki her değerlendirmeye ilişkin güncelleştirmeyi ayrı ayrı kabul etmek gerekir.

#### <a name="where-youll-see-assessment-update-notifications"></a>Değerlendirme güncelleştirme bildirimlerini göreceğiniz yer

Değerlendirme ayrıntıları sayfasında, değerlendirmenin **yanında bir güncelleştirmeyle** birlikte Bekleyen güncelleştirme etiketi de görüntülenir. Ayrıntılar sayfasına almak için bu değerlendirmeyi seçin.

Değerlendirme ayrıntıları sayfasının üst kısmında yer alan bir ileti, bu değerlendirme için bir güncelleştirme sağ olduğunu gösterir. Belirli değişiklikleri **gözden geçirmek ve** güncelleştirmeyi kabul etmek veya ertelemek için başlıkta Güncelleştirmeyi gözden geçir düğmesini seçin.

Değerlendirme ayrıntıları sayfasında ayrıca, yanında Bekleyen güncelleştirme etiketi olan **geliştirme** eylemleri de listelenmiş olabilir. Bu güncelleştirmeler geliştirme eylemlerinin kendi özel değişikliklerine yöneliktir ve ayrı olarak kabul edilmelidir. Daha [fazla bilgi edinmek için Geliştirme eylemleri için Güncelleştirmeleri kabul](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) etme sitesini ziyaret edin.

#### <a name="review-update-to-accept-or-defer"></a>Kabul etmek veya ertelemek için güncelleştirmeyi gözden geçirme

Değerlendirme ayrıntıları **sayfasından Güncelleştirmeyi** gözden geçir'i seçdikten sonra, ekrannizin sağ tarafında bir açılır bölme görüntülenir. Uç nokta bölmesi, aşağıdaki bekleyen güncelleştirmeyle ilgili önemli ayrıntıları sağlar:

- Şablon başlığı
- Güncelleştirmenin kaynağı (Microsoft, sizin veya belirli bir kullanıcı)
- Güncelleştirmenin oluşturulma tarihi
- Güncelleştirmeyi açıklayan genel bakış
- Uyumluluk puanınıza etkisini, değerlendirmenin tamamlanmasına yönelik ilerleme durumu ve iyileştirme eylemleriyle denetimlerine yönelik belirli değişiklik sayısı gibi değişikliklerle ilgili belirli ayrıntılar.

Güncelleştirilmiş **şablon bağlantısı seçerek**, Excel güncelleştirmelerin bulunduğu şablonun sürümüne uygun denetim verilerini içeren bir Excel dosyası indir olur. Geçerli şablon **bağlantısı seçilse** bile, değişiklikler olmadan var olan şablonun dosyası indirilir.

Güncelleştirmeyi kabul etmek ve değerlendirmeniz üzerinde değişiklik yapmak için Güncelleştirmeyi kabul **et'i seçin**. Kabul edilen değişiklikler kalıcıdır.

**İptal'i** seçersiniz, güncelleştirme değerlendirmeye uygulanmaz. Ancak siz güncelleştirmeyi kabul edene kadar **Bekleyen güncelleştirme** bildirimini görmeye devam edersiniz.

**Neden güncelleştirmeleri kabul etmenizi öneririz?**

Güncelleştirmeleri kabul etmek, çözümleri kullanma konusunda en güncel kılavuza sahip olmasını sağlar ve sertifikanın gereksinimlerini karşılamanıza yardımcı olacak uygun geliştirme eylemleri gerçekleştirebilir.

**Güncelleştirmeyi ertelemek istemeniz nedeni**

Değerlendirmeyi tamamlamanın ortasındaysanız, denetim eşlemesini kesintiye neden olacak değerlendirmeye ilişkin bir güncelleştirmeyi kabul etmek için önce değerlendirme üzerinde çalışmanız bittiğinden emin olmak iyi bir yol olabilir. Gözden geçirme güncelleştirmesi çıkış bölmesinde İptal'i **seçerek** güncelleştirmeyi daha sonra ertelemeniz gerekir.

## <a name="export-an-assessment-report"></a>Değerlendirme raporunu dışarı aktarma

Değerlendirmeyi, kurumuzla ilgili uyumluluk Excel için veya dış denetçiler ve düzenleyiciler için bir uyumluluk dosyasına aktarabilirsiniz. Değerlendirme ayrıntıları sayfanız üzerinde, **sayfanın üst** kısmında rapor oluştur düğmesini seçin. Bu düğmeyi Excel paylaşabilirsiniz.

Rapor, dışarı aktarmanın tarih ve saatine ilişkin değerlendirmenin anlık görüntüsüdir. Uygulama durumu, test tarihi ve test sonuçları dahil olmak üzere hem sizin hem de Microsoft tarafından yönetilen denetimlerin ayrıntılarını içerir.

## <a name="delete-an-assessment"></a>Değerlendirmeyi silme

Değerlendirmenin silinmesi, değerlendirmeleri sayfanıza bu değerlendirmeyi listeden kaldırır. Değerlendirmeleri silmeyle ilgili şu önemli noktaları unutmayın:

- **Değerlendirmeyi silmek kalıcı bir değerdir; geri alayam.** Aynı değerlendirmeyi yeniden kullanmak için, yeniden oluşturmanız gerekir.
- Değerlendirmedeki geliştirme eylemleri başka bir değerlendirmede görünmüyorsa, değerlendirme silindiğinde bunlar silinir.
- Değerlendirmeyi [kalıcı olarak silmezken](#export-an-assessment-report) önce bu değerlendirmenin raporunu dışarı aktarmayı öneririz.

Değerlendirmeyi silmek için aşağıdaki adımları izleyin:

1. Değerlendirmeler **sayfanız** , silmek istediğiniz değerlendirmeyi seçerek o değerlendirmenin ayrıntılar sayfasını açın.

2. **Ekrannizin sağ** üst köşesindeki Değerlendirmeyi sil'i seçin.

3. Değerlendirmeyi kalıcı olarak silmek istediğinizi onaylamanızı isteyen bir pencere görüntülenir. **Pencereyi kapatmak için** Değerlendirmeyi sil'i seçin. Değerlendirmenizin Uyumluluk Yöneticisi'den silindikten sonra bir onay penceresi görüntülenir.

> [!NOTE]
> Tüm değerlendirmelerinizi silemezsiniz. Kuruluşların Uyumluluk Yöneticisi'nin düzgün çalışması için en az bir değerlendirmeye ihtiyacı vardır. Silmek istediğiniz değerlendirme tek değerlendirme ise, diğer değerlendirmeyi silmeden önce başka bir değerlendirme ekleyin.
