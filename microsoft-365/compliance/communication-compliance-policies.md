---
title: İletişim uyumluluğu ilkeleri
description: İletişim uyumluluk ilkeleri hakkında daha fazla bilgi edinin.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: ab3b274ee07b343528c9b25f36dccc86d18e7ef8
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635009"
---
# <a name="communication-compliance-policies"></a>İletişim uyumluluğu ilkeleri

## <a name="policies"></a>İlkeler

> [!IMPORTANT]
> İletişim uyumluluk ilkeleri oluşturmak ve yönetmek için PowerShell kullanımı desteklenemektedir. Bu ilkeleri oluşturmak ve yönetmek için, uyumluluk çözümünde ilke yönetim [Microsoft 365 kullanmalıdır](https://compliance.microsoft.com/supervisoryreview).

Kuruluşta yer alan tüm Microsoft 365 için iletişim uyumluluk Microsoft 365 uyumluluk merkezi. İletişim uyumluluk ilkeleri, hangi iletişimlerin ve kullanıcıların kuruluş içinde gözden geçir kanunlarına tabi olduğunu tanımlar, iletişimin karşılaması gereken özel koşulları tanımlar ve kimin incelemeler yapması gerektiğini belirtir. İletişim Uyumluluğu Yöneticisi *rolüne* atanan kullanıcılar ilkeler ayarlar ve bu rolün atandığı herkes, ilgili iletişim sayfasında İletişim uyumluluğu sayfasına  ve genel ayarlara Microsoft 365 uyumluluk merkezi. Gerekirse, ilkede yapılan değişikliklerin geçmişini, gözden geçirmeyi bekleyen uyarıların, geçen öğelerin ve çözümlenen öğelerin durumunu da içeren bir .csv (virgülle ayrılmış değerler) dosyasına aktarabilirsiniz. İlkeler yeniden adlandırılamaz ve artık gerek kalmadiğinde silinebilir.

## <a name="policy-templates"></a>İlke şablonları

İlke şablonları, genel uyumluluk senaryolarına yönelik ilkeler oluşturmak için kullanabileceğiniz, önceden tanımlanmış ilke ayarlarıdır. Bu şablonların her biri, koşullar ve kapsam olarak farklılık gösterir ve tüm şablonlar aynı tarama sinyali türlerini kullanır. Aşağıdaki ilke şablonlarından birini seçebilirsiniz:

|**Alan**|**İlke Şablonu**|**Ayrıntılar**|
|:-----|:-----|:-----|
| **Uygunsuz metin** | Uygunsuz metni algılama | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Yüzdeyi gözden geçirme: %100 <br> - Koşullar: Tehdit, Tehdit, Tehdit ve Taciz sınıflandırıcıları |
| **Uygunsuz resimler** | Uygunsuz resimleri algılama | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Yüzdeyi gözden geçirme: %100 <br> - Koşullar: Yetişkin ve Racy resim sınıflandırıcıları |
| **Hassas bilgiler** | Hassas bilgileri izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Yüzdeyi gözden geçirme: %10 <br> - Koşullar: Hassas bilgiler, ilk gelen içerik desenleri ve türleri, özel sözlük seçeneği, 1 MB'den büyük ekler |
| **Mevzuat uyumluluğu** | Yasal düzenlemelere uyumluluğu izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden <br> - Yüzdeyi gözden geçirme: %10 <br> - Koşullar: özel sözlük seçeneği, 1 MB'den büyük ekler |
| **İlgi çakışması** | İlgi çakışması izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: İç <br> - Yüzdeyi gözden geçirme: %100 <br> - Koşullar: Yok |

İletişimler, ilkelerin oluşturulduktan sonra her 24 saatte bir taranır. Örneğin, saat 11:00'de uygunsuz bir içerik ilkesi oluşturmanıza göre, ilke her 24 saatte bir 11:00'de iletişim uyumluluk sinyallerini toplar. bir ilkenin düzenlenmesi bu sefer değişmez. İlkenin son tarama tarihi ve saati görüntülemek için İlke *sayfasındaki Son ilke* tarama **sütununa** gidin. Yeni bir ilke oluşturdukta, ilk ilke tarama tarihi ve saati 24 saate kadar sürebilir. Son taramanın tarihi ve saati, yerel sistem saat dilimine dönüştürülür.

## <a name="pause-a-policy-preview"></a>İlkeyi duraklatma (önizleme)

İletişim uyumluluğu ilkesi oluşturduktan sonra, gerekirse ilke geçici olarak duraklatılmış olabilir. İlkeyi duraklatma, ilke eşleşmelerini test etmek veya gidermek ya da ilke koşullarını en iyi duruma etmek için kullanılabilir. Bu koşullarda bir ilkeyi silmek yerine, ilke duraklatıldığı için var olan ilke uyarıları ve devam eden araştırma ve incelemelere yönelik iletiler de korunur. İlkeyi duraklatmak, ilkenin duraklatılmış olduğu süre için ilkede tanımlanmış tüm kullanıcı iletisi koşulları için inceleme ve uyarı oluşturmasını önler. Bir ilkeyi duraklatmak veya yeniden başlatmak için, kullanıcıların İletişim Uyumluluğu Yöneticisi *rol grubunun bir üyesi olması* gerekir.

Bir ilkeyi duraklatmak için İlke sayfasına **gidin** , bir ilke seçin ve ardından Eylemler araç **çubuğundan İlkeyi** duraklat'ı seçin. **İlkeyi duraklat** bölmesinde, Duraklat'ı seçerek ilkeyi duraklatmak istediğiniz **onaylayın**. Bazı durumlarda, bir ilkenin duraklatılmış durumda olması 24 saate kadar sürebilir. İlke duraklatıldıktan sonra, ilkeyle eşleşen iletilere karşı uyarılar oluşturulmaz. Bununla birlikte, ilke duraklatma öncesinde oluşturulan uyarılarla ilişkilendirilmiş iletiler araştırma, gözden geçirme ve düzeltme için kullanılabilir olarak kalır.

Duraklatılmış ilkeler için ilke durumu birkaç durum gösteriyor olabilir:

- **Etkin**: İlke etkin
- **Duraklatıldı**: İlke tümüyle duraklatıldı.
- **Duraklatma**: İlke duraklatma sürecindedir.
- **Devam etme**: Devam etme sürecindeki ilke.
- **Devam sırasında hatayla** karşılaşıldı: İlke devam ediyorken bir hatayla karşılaşıldı. Hata yığın izlemesi için, farenizi İlke *sayfasındaki* Durum sütunundaki Devamlama durumu hatası'nın üzerine gelin.
- **Duraklatma hatası**: İlke duraklatıldı. Hata yığın izlemesi için, farenizi *İlke sayfasındaki* Durum sütununda duraklatma durumundaki Hata'nın üzerine gelin.

Bir ilkeyi devam ettirin, **İlke sayfasına gidin** , bir ilke seçin ve sonra da eylemler araç **çubuğundan İlkeyi** sürdür'e tıklayın. **İlkeyi sürdür** bölmesinde, Sürdür'e seçerek ilkeyi devam ettirerek devam etmek istediğiniz **onaylayın**. Bazı durumlarda, bir ilkenin sürdürül olması 24 saate kadar sürebilir. İlke devam edildiktan sonra, ilkeyle eşleşen iletilere yönelik uyarılar oluşturulur ve araştırma, inceleme ve düzeltme için kullanılabilir.

## <a name="copy-a-policy-preview"></a>İlkeyi kopyalama (önizleme)

Var olan iletişim uyumluluk ilkelerine sahip kuruluşlarda, var olan bir ilkeden yeni ilke oluştururken yararlı olacak senaryolar olabilir. İlkeyi kopyalama, var olan bir ilkenin, kapsam içinde tüm kullanıcılar, atanmış gözden geçirenler ve tüm ilke koşulları dahil olmak üzere tam bir yinelemesini oluşturur. Bazı senaryolar şunlar olabilir:

- **İlke depolama sınırına ulaşıldı**: Etkin iletişim uyumluluk ilkelerinin ileti depolama sınırları vardır. Bir ilkenin depolama sınırına ulaşıldığında, ilke otomatik olarak devre dışı bırakılır. Devre dışı bırakılan ilkenin kapsa ettiği uygunsuz iletileri algılamaya, yakalamaya ve bu iletilere eylemde çalışmaya devam olması gereken kuruluşlar, hemen aynı yapılandırmaya sahip yeni bir ilke oluşturabilir.
- **Farklı kullanıcı grupları için** uygunsuz iletileri algılama ve gözden geçirme: Bazı kuruluşlar aynı yapılandırmaya sahip birden çok ilke oluşturmayı tercih eder, ancak her ilke için farklı kapsamda kullanıcılar ve farklı gözden geçirenler içerebilir.
- **Küçük değişiklikleri olan benzer ilkeler**: Karmaşık yapılandırma veya koşulları olan ilkeler için, benzer bir ilkeden yeni ilke oluşturmak zaman tasarrufu sağlar.

Bir ilkeyi kopyalamak için, kullanıcıların İletişim Uyumluluğu veya İletişim *Uyumluluğu* Yöneticisi *rol gruplarının bir üyesi olması* gerekir. Var olan bir ilkeden yeni bir ilke oluşturulduktan sonra, yeni ilke yapılandırmasına uyan iletilerin görünümü 24 saat kadar sürebilir.

Bir ilkeyi kopyalamak ve yeni ilke oluşturmak için, aşağıdaki adımları tamamlayın:

1. Kopyalamak istediğiniz ilkeyi seçin.
2. Komut **çubuğunda İlkeyi** kopyala komut çubuğu düğmesini seçin veya ilkenin eylem **menüsünden** İlkeyi kopyala'ya tıklayın.
3. **İlkeyi kopyala** bölmesinde, İlke adı alanında ilke için varsayılan adı kabul **veya ilkeyi** yeniden adlandırabilirsiniz. Yeni ilkenin ilke adı, var olan etkin veya devre dışı bırakılmış ilkeyle aynı olabilir. Açıklama **alanını gereken** şekilde tamamlama.
4. İlkeyi daha fazla özelleştirmeye ihtiyacınız yoksa, işlemi tamamlamak için **İlkeyi kopyala'ya** seçin. Yeni ilkenin yapılandırmasını güncelleştirmeniz gerekirse İlkeyi **özelleştir'i seçin**. Bu, yeni ilkeyi güncelleştirmenize ve özelleştirmenize yardımcı olmak için ilke sihirbazını başlatır.

## <a name="user-reported-messages-policy"></a>Kullanıcı tarafından bildirilen ileti ilkesi

Kuruluşta uygunsuz iletileri algılamak ve düzeltmek için katmanlı bir savunmanın parçası olarak, kullanıcı tarafından bildirilen iletilerle iletişim uyumluluk ilkelerine destek Microsoft Teams. Bu özellik, güvenli ve uyumlu bir çalışma ortamını teşvik etmeye yardımcı olmak için, organizasyonduki kullanıcıları taciz veya tehdit dili, yetişkin içeriğini paylaşma ve hassas veya gizli bilgileri paylaşma gibi uygunsuz iletileri kendi kendine bildirme konusunda güçlendirmektedir.

Teams yönetim merkezinde varsayılan olarak etkinleştirilen [Teams](/microsoftteams/manage-teams-in-modern-portal) iletileri için Bir sorun bildir  seçeneği, kuruluşta yer alan kullanıcıların ilkeye yönelik iletişim uyumluluğu gözden geçirenleri tarafından gözden geçirilleri için uygunsuz iletiler göndermelerine olanak sağlar. Bu iletiler, kanallarda, gruplarda ve özel sohbetlerde ileti Teams destekleyen varsayılan sistem ilkesi tarafından de destekler.

![İletişim uyumluluğu Sorun bildirebilirsiniz.](../media/communication-compliance-report-a-concern-full-menu.png)

Kullanıcı gözden geçirme için Teams bir sohbet iletisi gönderse, ileti Kullanıcı tarafından bildirilen ileti ilkesine kopyalanır. Bildirilen iletiler başlangıçta tüm sohbet üyeleri tarafından görünür kalır ve sohbet üyelerine veya ileti göndericiye kanal, özel veya grup sohbetine ileti bildirilmesine yönelik herhangi bir bildirim yoktur. Kullanıcı aynı iletiyi birden çok kez raporamaz ve ilke inceleme işlemi sırasında ileti sohbet oturumuna dahil olan tüm kullanıcılar tarafından görülebilir. 

Gözden geçirme işlemi sırasında, iletişim uyumluluğu gözden geçirenler iletide, iletiyi [](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) sohbetten kaldırmak da dahil olmak üzere tüm standart Teams gerçekleştirebilirsiniz. İletilerin nasıl düzeltilmesine bağlı olarak, ileti gönderen ve alıcılar inceleme sonrasında sohbetlerde Teams iletileri görebilir[](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams).

![İletişim uyumluluğu kullanıcı tarafından bildirilen iletiler ilkesi.](../media/communication-compliance-user-reported-messages-policy.png)

Kullanıcı sohbetlerden gelen Teams, Kullanıcı tarafından bildirilen ileti ilkesi tarafından işlenen tek iletidir ve ilkeye atanan gözden geçirenler değiştirilebilir. Diğer tüm ilke özellikleri düzenlenemez. İlke oluşturulduğunda, ilkeye atanan ilk gözden geçirenler, İletişim Uyumluluğu Yöneticileri rol grubunun (en az  bir kullanıcıyla doldurulduğunda) tüm üyeleri veya kuruluşun Genel Yönetici rol grubunun tüm üyeleridir. İlke oluşturucusu, İletişim Uyumluluğu Yöneticileri rol grubundan  (en az bir kullanıcıyla doldurulduğunda) rastgele seçilen bir kullanıcı veya kuruluşun Genel Yönetici rol grubundan rastgele seçilen *bir kullanıcıdır*.  

Yöneticilerin, özel gözden geçirenleri hemen bu ilkeye sizin için uygun şekilde ataması gerekir. Bu, Uyumluluk Görevlisi, Risk Görevlisi veya İnsan Kaynakları departmanınız üyeleri gibi gözden geçirenleri içerebilir. Kullanıcı tarafından bildirilen iletiler olarak gönderilen sohbet iletilerinin gözden geçirenlerini özelleştirmek için, aşağıdaki adımları tamamlayın:

1. Kendi [Microsoft 365 uyumluluk merkezi yönetici](https://compliance.microsoft.com/) hesabının kimlik bilgilerini kullanarak oturum Microsoft 365 açın.
2. aşağıdaki Microsoft 365 uyumluluk merkezi **uyumluluğu'ne gidin**.
3. İlke **sekmesinde** Kullanıcı tarafından bildirilen *iletiler ilkeyi seçin ve* sonra da Düzenle'yi **seçin**.
4. Kullanıcı tarafından **bildirilen iletileri izle bölmesinde** , ilke için gözden geçirenleri attayın. Gözden geçirenlerin, posta kutuları posta kutusunda barındırılan Exchange Online. Gözden geçirenler bir ilkeye ekli olduğunda, otomatik olarak ilkeye atamayı haber veren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını veren bir e-posta iletisi alırlar.
5. **Kaydet**'i seçin.

Kullanıcıların Önemli bir Teams bildir seçeneğiyle iletileri raporlamasını devre dışı bırakmak *için, Kullanıcı* Yönetim Merkezi'nde Son kullanıcı [raporlama seçeneğini Teams devre dışı bırak.](/microsoftteams/manage-teams-in-modern-portal)

## <a name="storage-limit-notification-preview"></a>Depolama sınırı bildirimi (önizleme)

Her iletişim uyumluluk ilkesi 100 GB veya 1 milyon ileti (hangisi önce ulaşsa) bir depolama sınırı boyutuna sahiptir. İlke bu sınırlara yaklaştıkça, bildirim e-postaları otomatik olarak İletişim Uyumluluğu veya *İletişim Uyumluluğu Yöneticisi* rol gruplarına atanan *kullanıcılara* gönderilir. Depolama boyutu veya ileti sayısı sınırın %80, 90 ve yüzde 95'ine ulaştığında bildirimler iletisi gönderilir. İlke sınırına ulaşıldığında, ilke otomatik olarak devre dışı bırakılır ve ilke uyarı iletilerini işlemeyi durdurur.

>[!IMPORTANT]
>Depolama ve ileti sınırlarına ulaştığınız için bir ilke devre dışı bırakıldı ise, devre dışı bırakılan ilkenin nasıl yönet bırakılacaklarını değerlendirin. İlkeyi silerseniz tüm iletiler, ilişkili ekler ve ileti uyarıları kalıcı olarak silinir. Bu öğeleri gelecekte kullanmak üzere korumanız gerekirse, devre dışı bırakılan ilkeyi silmeyin.

Depolama ve ileti sınırlarına yaklaşan ilkeleri yönetmek için, kapsamın sürekliliğini korumak üzere ilkenin bir kopyasını alma veya geçerli ilke depolama boyutuyla ileti sayılarını en aza indirmeye yardımcı olacak aşağıdaki eylemleri gerçekleştirin:

- İlkeye atanan kullanıcı sayısını azaltmayı göz önünde bulundurabilirsiniz. Kullanıcıların ilkeden kaldırılması veya farklı kullanıcı grupları için farklı ilkeler oluşturulması ilke boyutunun ve toplam iletilerinin büyümeyi yavaşlatmanıza yardımcı olabilir.
- Hatalı pozitif uyarılar için ilkeyi inceleme. Sık karşılaşılan hatalı pozitif uyarıları yoksaymak için ilke koşullarına özel durumlar veya değişiklikler eklemeyi göz önünde bulundurabilirsiniz.
- Bir ilke depolama veya ileti sınırlarına ulaştı ve devre dışı bırakıldısa, aynı koşulları ve kullanıcıları algılayıp önlem almaya devam etmek için ilkenin bir kopyasını hazır hale getirebilirsiniz.

## <a name="policy-settings"></a>İlke ayarları

### <a name="users"></a>Kullanıcılar

İletişim uyumluluğu ilkesinde **Tüm kullanıcılar'ı** veya belirli kullanıcıları tanımlamayı seçebilirsiniz. Tüm **kullanıcılar'ın** seçimi, ilkeyi tüm kullanıcılara ve herhangi bir kullanıcının üye olarak dahil olduğu tüm gruplara uygular. Belirli kullanıcıların tanımlanması, ilkeyi tanımlı kullanıcılara ve tanımlı kullanıcıların üye olarak dahil olduğu tüm gruplara uygular.

### <a name="direction"></a>Yön

Varsayılan olarak **Yön koşulu** görüntülenir ve kaldırılamaz. Bir ilkede iletişim yönü ayarları tek tek veya birlikte seçilir:

- **Gelen**: İlkede denetleme yapılan **diğer** kullanıcılar dahil olmak üzere dış ve iç gönderenlerden denetleme yapılan kullanıcılara gönderilen iletişimi algılar.
- **Giden**: Denetim altında olan kullanıcılardan dış **ve** iç alıcılara gönderilen iletişimi algılar ve ilkede denetleme yapılan diğer kullanıcılar da buna dahil olur.
- **İç**: İlkede **denetleme** yapılan kullanıcılar veya gruplar arasındaki iletişimi algılar.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

İletişim uyumluluk ilkeniz kapsamında hassas bilgi türlerini dahil olma seçeneğiniz vardır. Hassas bilgi türleri, kredi kartı numaralarını, banka hesap numaralarını, pasaport numaralarını ve daha fazlasını tanımlamanıza ve korumanıza yardımcı olan önceden tanımlanmış veya özel veri türleridir. Veri kaybını [önleme hakkında bilgi](dlp-learn-about-dlp.md) vermenin bir parçası olarak, hassas bilgi yapılandırmasında hassas içeriği tanımlamanıza ve bayraklamanıza yardımcı olması için desenler, karakter yakınlığı, güven düzeyleri ve hatta özel veri türleri kullanılabilir. Varsayılan hassas bilgi türleri şöyledir:

- Finansal
- Sağlık ve sağlık
- Gizlilik
- Özel bilgi türü

> [!IMPORTANT]
> SITS'lerin en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Hassas bilgi ayrıntıları ve varsayılan türlerde bulunan desenler hakkında daha fazla bilgi edinmek için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Özel anahtar sözcük sözlükleri

Organizasyonunıza veya sektörünize özel anahtar sözcüklerin basit yönetimini sağlamak için özel anahtar sözcük sözlükleri (veya anahtar sözcükleri) yapılandırabilirsiniz. Anahtar sözcük sözlükleri, sözlükte en fazla 100 KB terim (sıkıştırma sonrası) destekler ve her dili destekler. Sıkıştırma sonrasında kiracı sınırı da 100 KB'dir. Gerekirse, tek bir ilkeye birden çok özel anahtar sözcük sözlüğü uygulayabilir veya her ilke için tek bir anahtar sözcük sözlüğü kullanabilirsiniz. Bu sözlükler bir iletişim uyumluluk ilkesinde atanır ve bir dosyadan (.csv veya .txt listesi gibi) ya da Uyumluluk Merkezi'nde İçeri Aktarabilirsiniz listesinden [kaynaklandı](create-a-keyword-dictionary.md). Organizasyonunıza ve ilkelerinize özgü terimleri veya dilleri desteklemeniz gereken özel sözlükler kullanın.

### <a name="classifiers"></a>Sınıflayıcılar

Yerleşik olarak eğitilebilir ve genel sınıflayıcılar, farklı türlerde uyumluluk sorunları için kuruluş genelinde gönderilen veya alınan iletileri tüm iletişim kanallarına tarar. Sınıflayıcılar, iletilerde taciz önleme ilkelerini ihlal olasılığı bulunan iletilerde dil belirlemek için yapay zeka ve anahtar sözcüklerin bir bileşimini kullanır. Yerleşik sınıflayıcılar şu anda çeşitli dillerde ileti anahtar sözcüğü kimliğini desteklemektedir:

- Çince (Basitleştirilmiş)
- English
- French
- German
- Italian
- Japanese
- Portekizce
- Spanish

Aşağıdaki dil ve içerik türleri için terimler, resimler ve duyguları için iletişimin yerleşik eğitim ve genel sınıflandırıcı tarama iletişimi:

- **Yetişkinlere yönelik** resimler: Cinsel olan doğada açık olan resimleri tarar.
- **Virüs**: Açık bir ayırt etmek için taramalar ve diğer topluluklara göre Afrika Amerika/Siyah topluluklarına karşı özellikle ayrımcı dillere duyarlıdır.
- **Gory resimleri**: Şiddet ve gore gösteren görüntüleri tarar.
- **Küfür:** Çoğu kişiyi dikkat dışı eden küfür ifadelerini tarar.
- **Racy resimleri**: Cinsel olan ama yetişkinlere yönelik olduğu kabul edildi resimlerden daha az açık içerik içeren resimleri tarar.
- **Hedeflenen taciz**: Yarış, renk, din ve ulusal kökenle ilgili kişiyi hedef alan rahatsız edici davranış tarar.
- **Tehdit**: Tehditlere karşı, bir kişi ya da mülkiyete şiddet veya fiziksel zarar vermek için tehditler tarar.

*Adult,* *Racy* ve *Gory image classifiers* scan files in .jpeg, .png, .gif, and gory .bmp. Resim dosyalarının boyutu 4 megabayttan (MB) küçük olmalı ve resmin değerlendirmeye uygun olması için resimlerin boyutları 50x50 pikselden büyük ve 50 kilobayttan (KB) büyük olmalıdır. E-posta iletilerini, kanallarını ve Exchange Online sohbetleri göndermek Microsoft Teams resim kimliği desteklemektedir.

Yerleşik eğitilebilir ve genel sınıflayıcılar, bu alanlar genelinde terimlerin veya resimlerin çok kapsamlı bir listesini sağlamaz. Ayrıca, dil ve kültürel standartlar sürekli değişir ve bu gerçeklerin ışığı altında, Microsoft kendi takdirine bağlı olarak sınıflayıcıları güncelleştirme hakkını sahiptir. Sınıflayıcılar bu alanları izlemede kuruma yardımcı olabilir, ancak sınıflayıcılar, bu tür dili veya görüntüleri izleme veya değerlendirme için yalnızca kuruluş izinlerini sağlamak üzere hazır değildir. Microsoft'u değil de, bu alanlarda dilleri ve resimleri izleme, tarama ve engellemeyle ilgili tüm kararlardan (yerel gizlilik ve diğer geçerli yasalarla uyumluluk dahil) sorumlu tutulamaz. Microsoft dağıtım ve kullanımdan önce hukuk danışmanını teşvik ediyor.

> [!NOTE]
> Sınıflayıcıları kullanan ilkeler, altı veya daha büyük bir sözcük sayısına sahip iletileri inceler ve değerlendirir. Altı sözcükten az sözcük içeren iletiler, sınıflayıcılar kullanılarak ilkelerde değerlendirilmez. Uygunsuz içeriği içeren kısa iletileri tanımlamak ve bu iletilere önlem almak için, bu içerik türünün iletişim uyumluluk ilkelerini izlemek için özel bir anahtar sözcük sözlüğü eklemenizi öneririz.

Aynı sınıfta eğitilebilir sınıflayıcılar hakkında Microsoft 365 için bkz[. Eğitilebilir sınıflayıcılarla çalışmaya başlama](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Optik karakter tanıma (OCR)

Yazılı veya el yazısıyla yazılmış metinleri kuruluş içinde uygunsuz olan resimlerden taramak ve tanımlamak için yerleşik veya özel iletişim uyumluluk ilkelerini yapılandırabilirsiniz. Tümleşik [Azure Bilişsel](/azure/cognitive-services/computer-vision/overview-ocr) Hizmetleri ve resimlerde metinleri belirlemek için optik tarama desteği, analistlerin ve tahminlere, öncelikli olarak metin dışı iletişimlerde uygunsuz davranışların kaçırıl olduğu örnekleri algılamaya ve bu örnekler üzerinde işlemde yardımcı olur.

Şablonlardan, özel ilkelerden gelen yeni ilkelerde optik karakter tanımayı (OCR) etkinleştirebilirsiniz veya ekli resimleri ve ekleri işleme desteğini genişletmek için var olan ilkeleri güncelleştirebilirsiniz. bir ilke şablonundan oluşturulan bir ilkede etkinleştirildiğinde, e-postaya eklenen veya eklenen resimlerde ve sohbet iletilerinde otomatik Microsoft Teams destekler. Belge dosyalarına eklenmiş resimler için OCR tarama özelliği desteklenmiyor. Özel ilkeler için, OCR taramasının seçimini etkinleştirmek üzere ilkede anahtar sözcüklerle, yerleşik sınıflayıcılarla veya hassas bilgi türleriyle ilişkilendirilmiş bir veya birden çok koşullu ayarın yapılandırılması gerekir.

Aşağıdaki görüntü biçimlerinden 50 KB - 4 MB arasında olan resimler taranır ve işlenir:

- .jpg/.jpeg (ortak fotoğraf uzmanları grubu)
- .png (taşınabilir ağ grafikleri)
- .bmp (bit eşlem)
- .tiff (etiket resmi dosya biçimi)
- .pdf (taşınabilir belge biçimi)

> [!NOTE]
> Ekli ve ekli resim .pdf tarama ve ayıklama şu anda yalnızca e-posta iletisinde desteklene.

OCR etkin ilkeler için bekleyen uyarılar incelendiğinde, ilke koşullarına tanımlanan ve ona uygun resimler ilişkili uyarılar için alt öğe olarak görüntülenir. Tanımlanan metni özgün iletiyle bağlam içinde değerlendirmek için özgün resmi görüntüebilirsiniz. Algılanan resimlerin uyarılarla birlikte kullanılabilir olması 48 saat kadar sürebilir.

### <a name="conditional-settings"></a>Koşullu ayarlar
<a name="ConditionalSettings"> </a>

İlke için seçtiğiniz koşullar, hem e-postanın hem de üçüncü taraf kaynaklarının (Instant Bloomberg'te olduğu gibi) iletişimler için geçerlidir.

Aşağıdaki tabloda her koşul hakkında daha fazla açıklama ve bilgi ve açıklama yer alır.

|**Koşul**|**Bu koşul nasıl olur?**|
|:-----|:-----|
| **İçerik bu sınıflayıcılardan herhangi birini eşler** | Sınıflandırıcılar iletiye ekli olduğunda veya iletiye dışlandıklarında ilkeye uygulanır. Bazı sınıflayıcılar kiracınız içinde önceden tanımlanmıştır ve özel sınıflayıcıların bu koşul için kullanılabilir duruma gelmeden önce ayrı olarak yapılandırılmaları gerekir. İlkede tek bir sınıflandırıcı bir koşul olarak tanımlanabilir. Sınıflayıcıları yapılandırma hakkında daha fazla bilgi için bkz[. Eğitilebilir sınıflandırıcılar (önizleme) hakkında bilgi.](classifier-learn-about.md) |
| **İçerik, bu hassas bilgi türlerinden herhangi birini içerir** | Hassas bilgi türleri bir iletiye ekli olduğunda veya iletiye dahil edilirken ilkeye uygulanır. Bazı sınıflayıcılar kiracınız içinde önceden tanımlanmıştır ve özel sınıflayıcılar ayrı olarak veya koşul atama işleminin bir parçası olarak ya da tek tek ya da bir parçası olarak ya da önceden tanımlanabilir. Seçtiğiniz her hassas bilgi türü ayrı ayrı uygulanır ve ilkenin iletiye uygulanması için bu hassas bilgi türlerinden yalnızca biri geçerli olması gerekir. Özel hassas bilgi türleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türleri hakkında bilgi.](sensitive-information-type-learn-about.md) |
| **İleti bu etki alanlarından herhangi biri tarafından alınmıştır**  <br><br> **İleti bu etki alanlarından herhangi biri tarafından alınamaz** | Alınan iletilere belirli etki alanlarını veya e-posta adreslerini eklemek veya dışarıda tutmak için ilkeyi uygulama. Her etki alanını veya e-posta adresini girin ve birden çok etki alanını veya e-posta adresini virgülle birbirinden ayırabilirsiniz. Girilen her etki alanı veya e-posta adresi ayrı olarak uygulanır; ilkenin iletiye uygulanması için tek bir etki alanı veya e-posta adresi gerekir. <br><br> Belirli bir etki alanındaki tüm e-postaları taramak istiyor ama gözden geçirmesi gerek iletileri (bültenler, duyurular, başka) dışarıda tutmak istemiyorsanız, e-posta adresini (örneğin "newsletter@contoso.com") dışlamak için bu etki alanlarından hiçbir ileti alınmayacak koşullarından bir İletiyi yapılandırmanız gerekir. |
| **İleti bu etki alanlarından herhangi birini**  <br><br> **İleti bu etki alanlarından hiçbir'e gönderilmez** | Gönderilen iletilere belirli etki alanlarını eklemek veya hariç tutmak için ilkeyi uygulama. Her etki alanını girin ve birden çok etki alanını virgülle birbirinden ayırabilirsiniz. Her etki alanı ayrı uygulanır, ilkenin iletiye uygulanması için tek bir etki alanının uygulanması gerekir. <br><br> belirli iki etki alanına gönderilen tüm e-postaları dışarıda tutmak için İleti'yi bu etki alanları  koşulundan hiçbirsine ('contoso.com,wingtiptoys.com' örneğinde olduğu gibi) göndermeyecek şekilde yapılandırabilirsiniz. |
| **İleti, bu etiketlerden herhangi biri ile sınıflandırılır**  <br><br> **İleti, bu etiketlerin hiçbirleriyle sınıflandırılmamıştır** | Belirli bekletme etiketleri iletiye ekli olduğunda veya iletiye dışlandıklarında ilkeyi uygulamak için. Bekletme etiketlerinin ayrı olarak yapılandırılması gerekir ve bu koşul kapsamında yapılandırılmış etiketler seçilir. Seçtiğiniz her etiket ayrı olarak uygulanır (ilkenin iletiye uygulanması için bu etiketlerden yalnızca biri uygulanmalıdır). Bekletme etiketleri hakkında daha fazla bilgi için bkz. Bekletme [ilkeleri ve bekletme etiketleri hakkında bilgi.](retention.md)|
| **İleti bu sözcüklerden herhangi birini içeriyor**  <br><br> **İletide bu sözcüklerden hiçbiri yok** | Belirli sözcükler veya tümcecikler iletiye ekli veya dışlanmışken ilkeyi uygulamak için, her sözcüğü virgülle ayrılmış olarak girin. İki sözcük veya daha fazla sözcük içeren tümcecikler için, ifadenin etrafında tırnak işareti kullanın. Her sözcük veya tümcecik ayrı olarak uygulanır (ilkenin iletiye uygulanması için yalnızca bir sözcük geçerli olması gerekir). Sözcük veya tümcecik girme hakkında daha fazla bilgi için, sonraki E-posta veya eklerle sözcük [ve tümcecikleri eşleştirme bölümüne bakın](communication-compliance-policies.md#Matchwords).|
| **Ek, bu sözcüklerden herhangi birini içerir**  <br><br> **Ekte bu sözcüklerden hiçbiri yok** | Belirli sözcükler veya tümcecikler bir ileti eke (örneğin bir Word belgesi) eke ekli veya dışlanmış durumdayken ilkeyi uygulamak için, virgülle ayrılmış her sözcüğü girin. İki sözcük veya daha fazla sözcük içeren tümcecikler için, ifadenin etrafında tırnak işareti kullanın. Her sözcük veya tümcecik ayrı olarak uygulanır (eke uygulanması için ilkeye yalnızca bir sözcük uygulanması gerekir). Sözcük veya tümcecik girme hakkında daha fazla bilgi için, sonraki E-posta veya eklerle sözcük [ve tümcecikleri eşleştirme bölümüne bakın](communication-compliance-policies.md#Matchwords).|
| **Ek, bu dosya türlerinden herhangi biridir**  <br><br> **Ek, bu dosya türlerinden hiçbiri değil** | Belirli türde ekleri içeren veya dışarıda tutmak istediğiniz denetleme iletişimleri için, dosya uzantılarını (örneğin, .exe veya .pdf). Birden çok dosya uzantısını dahil etmek veya hariç tutmak için, virgülle ayrılmış dosya türlerini girin (.exe *,.pdf,.zip*). İlkenin geçerli olması için yalnızca bir ek uzantısının eşleşmesi gerekir.|
| **İleti boyutu**  <br><br> **İleti boyutu büyük değil** | Belirli bir boyuta bağlı olarak iletileri gözden geçirmek için, bu koşulları kullanarak bir iletinin gözden geçirnmeden önce en büyük veya en küçük boyut belirtebilirsiniz. Örneğin, İleti **boyutunun** \> **1,0 MB'den** büyük olduğunu belirtirsiniz, 1,01 MB ve daha büyük olan tüm iletiler gözden geçirebilirsiniz. Bu koşul için bayt, kilobayt, megabayt veya gigabayt seçebilirsiniz.|
| **Ek,**  <br><br> **Ek büyük değil** | İletileri eklerinin boyutuna göre gözden geçirmek için, ekin iletiden ve eklerinin gözden geçirilmeden önce en fazla veya en küçük boyutta olacağını belirtin. Örneğin, Ek'in  \> **2,0 MB'den** büyük olduğunu belirtirsiniz, ekleri 2,01 MB ve üzerinde olan tüm iletiler gözden geçirebilirsiniz. Bu koşul için bayt, kilobayt, megabayt veya gigabayt seçebilirsiniz.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>E-posta veya eklerle eşleşen sözcükler ve tümcecikler
<a name="Matchwords"> </a>

Girer ve virgülle birbirinden ayırarak her sözcük ayrı uygulanır (e-postaya veya eke uygulamak için ilke koşuluna yalnızca bir sözcük ek gerekir). Örneğin, İleti bu sözcüklerden herhangi birini ve "gizli **", "** gizli" ve "insider alım satım" anahtar sözcüklerini virgülle ayırarak (yalniz, gizli,"insider alım satım") içeren koşulu kullanelim. İlke, "ornek", "gizli" ya da "insider ticaret" tümceciklerini içeren tüm iletilere uygulanır. Bu ilke koşulun geçerli olması için, bu sözcük ve tümceciklerden yalnızca biri gerçekleşir. İletide veya ekte yer alan sözcüklerin giriş ile tam olarak eşleşmesi gerekir.

> [!IMPORTANT]
>
> Özel sözlük dosyasını içeri aktarıyorsanız, her sözcük veya tümceciğin satır başı ve ayrı satırla birbirinden ayrılmış olması gerekir. Örneğin:
>
> *2010* <br>
> *Gizli* <br>
> *insider alım satım*

Aynı anahtar sözcükleri hem e-posta iletilerini hem de ekleri taramak için[](create-a-keyword-dictionary.md), iletilerde taramak istediğiniz terimler için özel bir anahtar sözcük sözlüğü oluşturun. Bu ilke yapılandırması, e-posta iletisinde VEYA e-posta ekte **görünen** tanımlı anahtar sözcükleri tanımlar. İletilerde ve eklerde terimleri tanımlamak için standart koşullu ilke *ayarlarını kullanmak (* İleti bu sözcüklerden herhangi birini içerir ve Ek bu sözcüklerden herhangi birini *içerir) hem* iletide hem de ekte  yer alan koşulların mevcut olması gerekir.

#### <a name="enter-multiple-conditions"></a>Birden çok koşullar girin

Birden çok koşullar girerseniz, Microsoft 365 uyumluluk ilkesi'nin iletişim öğelerine ne zaman uygulanabileceklerini belirlemek için tüm koşulları birlikte kullanır. Birden çok kural ayarsanız, özel durum girmedikçe ilkenin geçerli olması için tüm koşulların karşı şartlarının karşı olması gerekir. Örneğin, bir ileti "ticari" sözcüğü içeriyorsa ve 2 MB'den büyükse, geçerli bir ilkeye ihtiyacınız vardır. Bununla birlikte, iletide "Contoso mali onaylandı" sözcükleri de varsa, ilke geçerli değildir. Bu örnekte, üç koşullar aşağıdaki gibi tanımlanır:

- **İleti, "ticari" anahtar sözcüğüyle** birlikte bu sözcüklerden herhangi birini içerir
- **İleti boyutu** 2 MB değeriyle daha büyük
- **İleti, "Contoso mali ekibi** tarafından onaylandı" anahtar sözcükleriyle birlikte bu sözcüklerden hiçbirini içeriyor

### <a name="review-percentage"></a>Yüzdeyi gözden geçir

Gözden geçir edilecek içerik miktarını azaltmak için, iletişim uyumluluk ilkesi tarafından yönetilen tüm iletişimlerin yüzdesini belirtebilirsiniz. Seçilen ilke koşullarına uygun içeriğin toplam yüzdesinden gerçek zamanlı rastgele bir içerik örneği seçilir. Gözden geçirenlerin tüm öğeleri gözden geçirmesini sağlamak için, iletişim uyumluluk **ilkesinde %100** yapılandırabilirsiniz.

## <a name="alert-policies"></a>Uyarı ilkeleri

Bir ilke yapılandırıldığında, otomatik olarak buna karşılık gelen bir uyarı ilkesi oluşturulur ve ilkede tanımlanan koşullarla uyan iletiler için uyarılar oluşturulur. İlke oluşturduktan sonra etkinlik göstergelerinden uyarı almaya başlamak 24 saat kadar sürebilir. Varsayılan olarak, tüm ilke eşleşmeleri uyarı tetikleyicisine ilişkili uyarı ilkesinde bir önem düzeyi orta düzeyde atanır. İlişkili uyarı ilkesinde toplama tetikleyici eşik düzeyi karşılandıktan sonra, iletişim uyumluluk ilkesi için uyarılar oluşturulur. İlke koşullarına uygun iletilerin sayısına bakılmaksızın, her 24 saatte bir, uyarılar için tek bir e-posta bildirimi gönderilir. Örneğin, Contoso'da uygun olmayan bir içerik ilkesi etkindir ve 1 Ocak'ta altı uyarı oluşturan 100 ilke eşleşmesi vardır. 1 Ocak sonunda altı uyarı için tek bir e-posta bildirimi gönderilir.

İletişim uyumluluğu ilkeleri için, aşağıdaki uyarı ilkesi değerleri varsayılan olarak yapılandırılır:

|**Uyarı ilkesi tetikleyicisi**|**Varsayılan değer**|
|:-----|:-----|
| Toplama | Basit toplama |
| Eşik | Varsayılan: 4 etkinlik <br> En az: 3 etkinlik <br> En fazla: 2.147.483.647 etkinlik |
| Pencere | Varsayılan: 60 dakika <br> En az: 60 dakika <br> En fazla: 10.000 dakika |

> [!NOTE]
> Etkinlikler için uyarı ilkesi tetikleyici ayarları, iletişim uyumluluk ilkeleri için en az 3 veya daha yüksek değeri destekler.

Etkinlik sayısı, etkinlikler için dönem ve uyarı ilkeleri sayfasındaki uyarı ilkeleri sayfasındaki belirli kullanıcılar için tetikler için varsayılan ayarları Microsoft 365 uyumluluk merkezi.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Uyarı ilkesi için önem düzeyini değiştirme

Belirli bir iletişim uyumluluk ilkesi için uyarı ilkesine atanan önem düzeyini değiştirmek için aşağıdaki adımları tamamlayın:

1. Kendi [Microsoft 365 uyumluluk merkezi yönetici](https://compliance.microsoft.com) hesabının kimlik bilgilerini kullanarak oturum Microsoft 365 açın.

2. Aşağıdaki Microsoft 365 uyumluluk merkezi İlkeler'e **gidin**.

3. **İlkeler Office 365** **Uyarı ilkeleri sayfasını** açmak için İlkeler **sayfasında uyarıyı seçin**.

4. Güncelleştirmek istediğiniz iletişim uyumluluk ilkesi onay kutusunu seçin ve sonra İlkeyi **düzenle'yi seçin**.

5. Açıklama **sekmesinde,** ilke uyarı düzeyini **yapılandırmak için** Önem Derecesi açılan listesinden seçim yapın.

6. Yeni **önem** düzeyi ilkeye uygulamak için Kaydet'i seçin.

7. Uyarı **ilkesi** ayrıntıları sayfasından çıkmak için Kapat'ı seçin.
