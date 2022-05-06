---
title: İletişim uyumluluk ilkeleri
description: İletişim uyumluluk ilkeleri hakkında daha fazla bilgi edinin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, iletişim uyumluluğu
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
ms.openlocfilehash: 8418683577ffe3bf63fe7fe3bf4aff2ef55007f5
ms.sourcegitcommit: c33af120921d3c4fb5c362dac3e74f0ab3d1e58d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2022
ms.locfileid: "65249641"
---
# <a name="communication-compliance-policies"></a>İletişim uyumluluk ilkeleri

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="policies"></a>İlkeler

> [!IMPORTANT]
> İletişim uyumluluk ilkeleri oluşturmak ve yönetmek için PowerShell'in kullanılması desteklenmez. Bu ilkeleri oluşturmak ve yönetmek için [, iletişim uyumluluk çözümünde](https://compliance.microsoft.com/supervisoryreview) ilke yönetimi denetimlerini kullanmanız gerekir.

Microsoft Purview uyumluluk portalında Microsoft 365 kuruluşlar için iletişim uyumluluk ilkeleri oluşturursunuz. İletişim uyumluluk ilkeleri, kuruluşunuzda hangi iletişimlerin ve kullanıcıların gözden geçirileceğini tanımlar, iletişimlerin hangi özel koşulları karşılaması gerektiğini tanımlar ve kimin inceleme yapacağını belirtir. *İletişim Uyumluluğu Yöneticisi* rolüne atanan kullanıcılar ilkeleri ayarlayabilir ve bu role atanmış olan herkes Microsoft Purview uyumluluk portalında **İletişim uyumluluğu** sayfasına ve genel ayarlara erişebilir. Gerekirse, bir ilkedeki değişikliklerin geçmişini gözden geçirmeyi bekleyen uyarıların, yükseltilmiş öğelerin ve çözümlenen öğelerin durumunu da içeren bir .csv (virgülle ayrılmış değerler) dosyasına aktarabilirsiniz. İlkeler yeniden adlandırılamaz ve artık gerekli olmadığında silinebilir.

## <a name="policy-templates"></a>İlke şablonları

İlke şablonları, yaygın uyumluluk senaryolarına yönelik ilkeleri hızla oluşturmak için kullanabileceğiniz önceden tanımlanmış ilke ayarlarıdır. Bu şablonların her birinin koşulları ve kapsamı farklıdır ve tüm şablonlar aynı tür tarama sinyallerini kullanır. Aşağıdaki ilke şablonları arasından seçim yapabilirsiniz:

|**Alan**|**İlke Şablonu**|**Ayrıntılar**|
|:-----|:-----|:-----|
| **Uygunsuz metin** | Uygunsuz metni algılama | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Gözden Geçirme Yüzdesi: %100 <br> - Koşullar: Tehdit, Ayrımcılık ve Hedefli taciz sınıflandırıcıları |
| **Uygunsuz görüntüler** | Uygunsuz görüntüleri algılama | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Gözden Geçirme Yüzdesi: %100 <br> - Koşullar: Yetişkin ve Müstehcen görüntü sınıflandırıcıları |
| **Hassas bilgiler** | Hassas bilgileri izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden, İç <br> - Gözden Geçirme Yüzdesi: %10 <br> - Koşullar: Hassas bilgiler, kullanıma uygun olmayan içerik desenleri ve türleri, özel sözlük seçeneği, 1 MB'tan büyük ekler |
| **Mevzuat uyumluluğu** | Mevzuat uyumluluğunu izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: Gelen, Giden <br> - Gözden Geçirme Yüzdesi: %10 <br> - Koşullar: özel sözlük seçeneği, 1 MB'tan büyük ekler |
| **Çıkar çatışması** | çıkar çatışmasını izleme | - Konumlar: Exchange Online, Microsoft Teams, Yammer, Skype Kurumsal <br> - Yön: dahili <br> - Gözden Geçirme Yüzdesi: %100 <br> - Koşullar: Yok |

İletişimler, ilkelerin oluşturulduğu zamandan itibaren her 24 saatte bir taranır. Örneğin, saat 11:00'de uygunsuz bir içerik ilkesi oluşturursanız, ilke her 24 saatte bir 11:00'de iletişim uyumluluk sinyallerini toplar. İlkeyi düzenlemek bu kez değişmez. İlkenin son tarama tarihini ve saatini görüntülemek için İlke **sayfasındaki** *Son ilke tarama* sütununa gidin. Yeni bir ilke oluşturduktan sonra, ilk ilke tarama tarihini ve saatini görüntülemek 24 saat kadar sürebilir. Son taramanın tarihi ve saati yerel sisteminizin saat dilimine dönüştürülür.

## <a name="pause-a-policy-preview"></a>İlkeyi duraklatma (önizleme)

İletişim uyumluluk ilkesi oluşturduktan sonra, gerekirse ilke geçici olarak duraklatılabilir. İlkeyi duraklatma, ilke eşleşmelerini test etmek veya sorun gidermek ya da ilke koşullarını iyileştirmek için kullanılabilir. Bu durumlarda bir ilkeyi silmek yerine, bir ilkenin duraklatılması, devam eden araştırma ve incelemeler için mevcut ilke uyarılarını ve iletilerini de korur. İlkenin duraklatılması, ilkenin duraklatıldığı süre boyunca ilkede tanımlanan tüm kullanıcı iletisi koşulları için inceleme ve uyarı oluşturmayı engeller. Bir ilkeyi duraklatmak veya yeniden başlatmak için kullanıcıların *İletişim Uyumluluğu Yöneticisi* rol grubunun üyesi olması gerekir.

İlkeyi duraklatmak için **İlke** sayfasına gidin, bir ilke seçin ve ardından eylemler araç **çubuğundan İlkeyi duraklat'ı** seçin. **İlkeyi duraklat** bölmesinde Duraklat'ı seçerek ilkeyi duraklatmak istediğinizi **onaylayın**. Bazı durumlarda, bir ilkenin duraklatılması 24 saat kadar sürebilir. İlke duraklatıldıktan sonra, ilkeyle eşleşen iletiler için uyarılar oluşturulmaz. Ancak, ilke duraklatmadan önce oluşturulan uyarılarla ilişkili iletiler araştırma, gözden geçirme ve düzeltme için kullanılabilir durumda kalır.

Duraklatılan ilkelerin ilke durumu birkaç durumu gösterebilir:

- **Etkin**: İlke etkin
- **Duraklatıldı**: İlke tamamen duraklatıldı.
- **Duraklatma**: İlke duraklatılıyor.
- **Sürdürme**: Sürdürülme sürecindeki ilke.
- **Devam ederken hata**: İlke devam ederken bir hatayla karşılaşıldı. Hata yığını izlemesi için, farenizi İlke sayfasındaki Durum sütunundaki Devam *etme* durumunda hata'nın üzerine getirin.
- **Duraklatma hatası**: İlke duraklatılırken bir hatayla karşılaşıldı. Hata yığını izlemesi için, farenizi İlke sayfasındaki Durum sütunundaki *Duraklatma durumundaki hatanın* üzerine getirin.

bir ilkeyi sürdürmek için **İlke** sayfasına gidin, bir ilke seçin ve eylemler araç **çubuğundan İlkeyi sürdür'ü** seçin. İlkeyi **sürdür bölmesinde Sürdür'ü** seçerek ilkeyi sürdürmek istediğinizi onaylayın **.** Bazı durumlarda, bir ilkenin sürdürül etmesi 24 saat kadar sürebilir. İlke sürdürüldükten sonra, ilkeyle eşleşen iletiler için uyarılar oluşturulur ve araştırma, gözden geçirme ve düzeltme için kullanılabilir.

## <a name="copy-a-policy-preview"></a>İlke kopyalama (önizleme)

mevcut iletişim uyumluluk ilkelerine sahip kuruluşlar için, mevcut bir ilkeden yeni ilke oluşturmanın yararlı olabileceği senaryolar olabilir. İlkenin kopyalanması, tüm kapsam içi kullanıcılar, atanan tüm gözden geçirenler ve tüm ilke koşulları dahil olmak üzere mevcut ilkenin tam bir kopyasını oluşturur. Bazı senaryolar şunları içerebilir:

- **İlke depolama sınırına ulaşıldı**: Etkin iletişim uyumluluk ilkelerinin ileti depolama sınırları vardır. bir ilkenin depolama sınırına ulaşıldığında, ilke otomatik olarak devre dışı bırakılır. Devre dışı bırakılan ilke kapsamındaki uygunsuz iletileri algılamaya, yakalamaya ve üzerinde işlem yapmaya devam etmesi gereken kuruluşlar hızla aynı yapılandırmaya sahip yeni bir ilke oluşturabilir.
- **Farklı kullanıcı grupları için uygunsuz iletileri algılama ve gözden geçirme**: Bazı kuruluşlar aynı yapılandırmaya sahip birden çok ilke oluşturmayı tercih edebilir, ancak her ilke için farklı kapsam içi kullanıcılar ve farklı gözden geçirenler içerebilir.
- **Küçük değişikliklerle benzer ilkeler**: Karmaşık yapılandırmaları veya koşulları olan ilkeler için, benzer bir ilkeden yeni ilke oluşturmak zaman kazandırabilir.

Bir ilkeyi kopyalamak için kullanıcıların *İletişim Uyumluluğu* veya *İletişim Uyumluluğu Yöneticisi* rol gruplarının üyesi olması gerekir. Mevcut bir ilkeden yeni bir ilke oluşturulduktan sonra, yeni ilke yapılandırmasıyla eşleşen iletilerin görüntülenmesi 24 saat kadar sürebilir.

İlkeyi kopyalamak ve yeni bir ilke oluşturmak için aşağıdaki adımları tamamlayın:

1. Kopyalamak istediğiniz ilkeyi seçin.
2. Komut çubuğunda **İlkeyi kopyala** komut çubuğu düğmesini seçin veya **ilkenin eylem menüsünde İlkeyi kopyala'yı** seçin.
3. **İlkeyi kopyala** bölmesinde, **İlke** adı alanında ilkenin varsayılan adını kabul edebilir veya ilkeyi yeniden adlandırabilirsiniz. Yeni ilkenin ilke adı, mevcut etkin veya devre dışı bırakılmış ilkeyle aynı olamaz. **Açıklama** alanını gerektiği gibi tamamlayın.
4. İlkeyi daha fazla özelleştirmeniz gerekmiyorsa, işlemi tamamlamak için **İlkeyi kopyala'yı** seçin. Yeni ilkenin yapılandırmasını güncelleştirmeniz gerekiyorsa İlkeyi **özelleştir'i** seçin. Bu, yeni ilkeyi güncelleştirmenize ve özelleştirmenize yardımcı olmak için ilke sihirbazını başlatır.

## <a name="user-reported-messages-policy"></a>Kullanıcı tarafından bildirilen iletiler ilkesi

>[!NOTE]
>Kullanıcı tarafından bildirilen iletiler, Mayıs 2022'den itibaren [iletişim uyumluluğu](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) ve Microsoft Teams lisansına sahip kuruluşlarda kullanıma sunulmaya başlayacaktır. Bu özellik 31 Ağustos 2022'ye kadar tüm lisanslı kuruluşlar için kullanılabilir olmalıdır.

Kuruluşunuzdaki uygunsuz iletileri algılamak ve düzeltmek için katmanlı bir savunmanın parçası olarak, Microsoft Teams kullanıcı tarafından bildirilen iletilere iletişim uyumluluk ilkelerini tamamlayabilirsiniz. Bu özellik, kuruluşunuzdaki kullanıcılara güvenli ve uyumlu bir çalışma ortamı sağlamaya yardımcı olmak için taciz veya tehdit dili, yetişkin içeriğinin paylaşımı ve hassas veya gizli bilgilerin paylaşılması gibi uygunsuz iletileri kendi kendine bildirme gücü sağlar.

[Teams yönetim merkezinde](/microsoftteams/manage-teams-in-modern-portal) varsayılan olarak etkinleştirilen Teams iletilerde *Sorun* bildir seçeneği, kuruluşunuzdaki kullanıcıların ilke için iletişim uyumluluğu gözden geçirenleri tarafından gözden geçirebilmek üzere uygunsuz iletiler göndermesine olanak tanır. Bu iletiler, Teams kanallarda, gruplarda ve özel sohbetlerde iletileri raporlamayı destekleyen varsayılan bir sistem ilkesi tarafından desteklenir.

![İletişim uyumluluğu Bir sorun bildirin.](../media/communication-compliance-report-a-concern-full-menu.png)

Kullanıcı gözden geçirmek üzere Teams sohbet iletisi gönderdiğinde, ileti Kullanıcı tarafından bildirilen ileti ilkesine kopyalanır. Bildirilen iletiler başlangıçta tüm sohbet üyeleri tarafından görünür durumda kalır ve sohbet üyelerine veya gönderene kanal, özel veya grup sohbetlerinde bir iletinin bildirildiğine dair bir bildirim yoktur. Kullanıcı aynı iletiyi birden çok kez raporlayamaz ve ilke gözden geçirme işlemi sırasında ileti sohbet oturumuna dahil olan tüm kullanıcılar tarafından görünür durumda kalır. 

gözden geçirme işlemi sırasında, iletişim uyumluluğu gözden geçirenler iletideki iletiyi Teams sohbetten kaldırma da dahil olmak üzere tüm standart [düzeltme eylemlerini](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) gerçekleştirebilir. İletilerin nasıl düzeltileceğine bağlı olarak, ileti gönderen ve alıcılar gözden geçirmeden sonra Teams sohbetlerde farklı [bildirim iletileri](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) görür.

![İletişim uyumluluğu kullanıcı tarafından bildirilen iletiler ilkesi.](../media/communication-compliance-user-reported-messages-policy.png)

Teams sohbetlerden gelen kullanıcı tarafından bildirilen iletiler, Kullanıcı tarafından bildirilen ileti ilkesi tarafından işlenen tek iletilerdir ve yalnızca ilke için atanan gözden geçirenler değiştirilebilir. Diğer tüm ilke özellikleri düzenlenemez. İlke oluşturulduğunda, ilkeye atanan ilk gözden geçirenlerin tümü *İletişim Uyumluluğu Yöneticileri* rol grubunun (en az bir kullanıcıyla doldurulmuşsa) veya kuruluşunuzun *Genel Yönetici* rol grubunun tüm üyeleridir. İlkeyi oluşturan, *İletişim Uyumluluğu Yöneticileri* rol grubundan (en az bir kullanıcıyla doldurulmuşsa) rastgele seçilen bir kullanıcı veya kuruluşunuzun *Genel Yönetici* rol grubundan rastgele seçilen bir kullanıcıdır.  

Yöneticiler, kuruluşunuza uygun şekilde bu ilkeye hemen özel gözden geçirenler atamalıdır. Bu, Uyumluluk Yetkiliniz, Risk Sorumlunuz veya İnsan Kaynakları departmanınızın üyeleri gibi gözden geçirenleri içerebilir. Gözden geçirenleri kullanıcı tarafından bildirilen iletiler olarak gönderilen sohbet iletileri için özelleştirmek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com/) oturum açın.
2. Uyumluluk portalında **İletişim uyumluluğu'na** gidin.
3. **İlke** sekmesinde *Kullanıcı tarafından bildirilen iletiler* ilkesini ve **düzenle'yi** seçin.
4. **Kullanıcı tarafından bildirilen iletileri izleme** bölmesinde, ilke için gözden geçirenleri atayın. Gözden geçirenlerin Exchange Online üzerinde barındırılan posta kutuları olmalıdır. Gözden geçirenler bir ilkeye eklendiğinde, ilkeye atamayı bildiren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını sağlayan bir e-posta iletisini otomatik olarak alır.
5. **Kaydet**'i seçin.

*Sorun bildir* seçeneği varsayılan olarak etkindir ve [Teams Yönetim Merkezi'ndeki Teams](/microsoftteams/manage-teams-in-modern-portal) mesajlaşma ilkeleri aracılığıyla denetlenebilir. Özel ilke oluşturup atamadığınız sürece kuruluşunuzdaki kullanıcılar genel ilkeyi otomatik olarak alır. Genel ilkedeki ayarları düzenleyin veya Sorun bildir seçeneğini açmak veya kapatmak için *bir* veya daha fazla özel ilke oluşturup atayın. Daha fazla bilgi için bkz. [Teams'de mesajlaşma ilkelerini yönetme](/microsoftteams/messaging-policies-in-teams).  

>[!IMPORTANT]
>Teams Yönetim Merkezi'nde **Son kullanıcı raporlama** seçeneğini açmak veya kapatmak için PowerShell kullanıyorsanız, [Microsoft Teams cmdlet'leri modülü sürüm 4.2.0](/MicrosoftTeams/teams-powershell-release-notes) veya üzerini kullanmanız gerekir.

## <a name="storage-limit-notification-preview"></a>Depolama sınırı bildirimi (önizleme)

Her iletişim uyumluluk ilkesinin depolama sınırı boyutu 100 GB veya 1 milyon iletidir (hangisi önce ulaşılırsa). İlke bu sınırlara yaklaştıkça, bildirim e-postaları *İletişim Uyumluluğu* veya *İletişim Uyumluluğu Yöneticisi* rol gruplarına atanan kullanıcılara otomatik olarak gönderilir. Depolama boyutu veya ileti sayısı sınırın yüzde 80, 90 ve yüzde 95'ine ulaştığında bildirim iletileri gönderilir. İlke sınırına ulaşıldığında, ilke otomatik olarak devre dışı bırakılır ve ilke uyarılar için iletileri işlemeyi durdurur.

>[!IMPORTANT]
>Depolama ve ileti sınırlarına ulaşılması nedeniyle bir ilke devre dışı bırakılırsa, devre dışı bırakılan ilkenin nasıl yönetileceğini değerlendirmeyi unutmayın. İlkeyi silerseniz tüm iletiler, ilişkili ekler ve ileti uyarıları kalıcı olarak silinir. Gelecekte kullanmak üzere bu öğelerin bakımını yapmanız gerekiyorsa devre dışı bırakılan ilkeyi silmeyin.

Depolama ve ileti sınırlarına yaklaşan ilkeleri yönetmek için, kapsam sürekliliğini korumak için ilkenin bir kopyasını oluşturmayı veya geçerli ilke depolama boyutunu ve ileti sayılarını en aza indirmeye yardımcı olmak için aşağıdaki eylemleri gerçekleştirmeyi göz önünde bulundurun:

- İlkeye atanan kullanıcı sayısını azaltmayı göz önünde bulundurun. Kullanıcıları ilkeden kaldırmak veya farklı kullanıcı grupları için farklı ilkeler oluşturmak, ilke boyutunun ve toplam iletilerin büyümesini yavaşlatma konusunda yardımcı olabilir.
- Aşırı hatalı pozitif uyarılar için ilkeyi inceleyin. Yaygın hatalı pozitif uyarıları yoksaymak için ilke koşullarına özel durumlar veya değişiklikler eklemeyi göz önünde bulundurun.
- Bir ilke depolama veya ileti sınırlarına ulaştıysa ve devre dışı bırakıldıysa, aynı koşulları ve kullanıcıları algılamaya ve eyleme almaya devam etmek için ilkenin bir kopyasını alın.

## <a name="policy-settings"></a>İlke ayarları

### <a name="users"></a>Kullanıcılar

**Tüm kullanıcılar'ı** veya bir iletişim uyumluluk ilkesinde belirli kullanıcıları tanımlamayı seçebilirsiniz. **Tüm kullanıcılar'ın** seçilmesi, ilkeyi tüm kullanıcılara ve herhangi bir kullanıcının üye olarak dahil olduğu tüm gruplara uygular. Belirli kullanıcıları tanımlamak, ilkeyi tanımlı kullanıcılara ve tanımlı kullanıcıların üye olarak dahil olduğu tüm gruplara uygular.

### <a name="direction"></a>Yön

Varsayılan olarak **Direction koşulu** görüntülenir ve kaldırılamaz. İlkedeki iletişim yönü ayarları tek tek veya birlikte seçilir:

- **Gelen**: **İlkedeki** diğer denetimli kullanıcılar da dahil olmak üzere dış ve iç gönderenlerden denetimli kullanıcılara gönderilen iletişimleri algılar.
- **Giden**: Denetimli **kullanıcılardan** ilkedeki diğer denetimli kullanıcılar da dahil olmak üzere dış ve iç alıcılara gönderilen iletişimleri algılar.
- **İç**: İlkedeki denetimli kullanıcılar veya gruplar **arasındaki** iletişimi algılar.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

hassas bilgi türlerini iletişim uyumluluk ilkenizin bir parçası olarak dahil edebilirsiniz. Hassas bilgi türleri kredi kartı numaralarını, banka hesap numaralarını, pasaport numaralarını ve daha fazlasını tanımlamaya ve korumaya yardımcı olabilecek önceden tanımlanmış veya özel veri türleridir. [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinme'nin](dlp-learn-about-dlp.md) bir parçası olarak, hassas bilgi yapılandırması hassas olabilecek içeriği tanımlamaya ve işaretlemeye yardımcı olmak için desenleri, karakter yakınlığı, güvenilirlik düzeylerini ve hatta özel veri türlerini kullanabilir. Varsayılan hassas bilgi türleri şunlardır:

- Finansal
- Tıbbi ve sağlık
- Gizlilik
- Özel bilgi türü

> [!IMPORTANT]
> SID'lerin, en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Hassas bilgi ayrıntıları ve varsayılan türlerde yer alan desenler hakkında daha fazla bilgi edinmek için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Özel anahtar sözcük sözlükleri

Kuruluşunuza veya sektörünüze özgü anahtar sözcüklerin basit yönetimini sağlamak için özel anahtar sözcük sözlüklerini (veya sözcük sözcüklerini) yapılandırın. Anahtar sözcük sözlükleri sözlükte 100 KB'a kadar terimleri (sıkıştırma sonrası) destekler ve herhangi bir dili destekler. Sıkıştırmadan sonra kiracı sınırı da 100 KB'tır. Gerekirse, tek bir ilkeye birden çok özel anahtar sözcük sözlükleri uygulayabilir veya ilke başına tek bir anahtar sözcük sözlüğüne sahip olabilirsiniz. Bu sözlükler bir iletişim uyumluluk ilkesinde atanır ve bir dosyadan (.csv veya .txt listesi gibi) veya [Uyumluluk merkezinde İçeri Aktarabileceğiniz bir listeden](create-a-keyword-dictionary.md) kaynaklanabilir. Kuruluşunuza ve ilkelerinize özgü terimleri veya dilleri desteklemeniz gerektiğinde özel sözlükleri kullanın.

### <a name="classifiers"></a>Sınıflandırıcı

Yerleşik eğitilebilir ve genel sınıflandırıcılar, farklı uyumluluk sorunları için kuruluşunuzdaki tüm iletişim kanallarında gönderilen veya alınan iletileri tarar. Sınıflandırıcılar, tehdit önleme ilkelerini ihlal etme olasılığı olan iletilerdeki dili tanımlamak için yapay zeka ve anahtar sözcüklerin bir bileşimini kullanır. Yerleşik sınıflandırıcılar şu anda çeşitli dillerde ileti anahtar sözcüğü tanımlamayı desteklemektedir:

- Arapça
- Çince (Basitleştirilmiş)
- Çince (Geleneksel)
- Dutch
- English
- French
- German
- Italian
- Korean
- Japanese
- Portekizce
- Spanish

İletişim uyumluluğu yerleşik eğitilebilir ve genel sınıflandırıcılar, aşağıdaki dil ve içerik türleri için terimler, resimler ve yaklaşımlar için iletişimleri tarar:

- **Yetişkinlere yönelik görüntüler**: Doğası gereği cinsel içerikli görüntüler için taramalar.
- **Ayrımcılık**: Açık ayrımcı dili tarar ve diğer topluluklarla karşılaştırıldığında Afrikalı Amerikalı/Siyah topluluklara karşı ayrımcı dile karşı özellikle hassastır.
- **Gory görüntüleri**: Şiddet ve vahşeti gösteren görüntüler için taramalar.
- **Küfür**: Çoğu insanı utandıran küfür içeren ifadeler tarar.
- **Müstehcen görüntüler**: Doğası gereği cinsel açıdan öneride bulunan ancak Yetişkinlere yönelik olarak kabul edilen görüntülerden daha az açık içerik içeren görüntüler için taramalar.
- **Hedeflenen taciz**: Irk, renk, din, ulusal kökenle ilgili insanları hedef alan saldırgan davranış taramaları.
- **Tehdit**: Bir kişiye veya mülke yönelik şiddet veya fiziksel zarar verme tehditlerini tarar.

*Adult*, *Racy* ve *Gory* görüntü sınıflandırıcıları dosyaları .jpeg, .png, .gif ve .bmp biçimlerinde tarar. Görüntü dosyalarının boyutu 4 megabayttan (MB) küçük olmalı ve görüntünün değerlendirmeye uygun olması için görüntülerin boyutları 50x50 pikselden büyük ve 50 kilobayttan (KB) büyük olmalıdır. Görüntü tanımlama, Exchange Online e-posta iletileri ve Microsoft Teams kanalları ve sohbetler için desteklenir.

Yerleşik eğitilebilir ve genel sınıflandırıcılar, bu alanlardaki terimlerin veya görüntülerin kapsamlı bir listesini sağlamaz. Ayrıca, dil ve kültürel standartlar sürekli olarak değişir ve bu gerçekler ışığında Microsoft, sınıflandırıcıları kendi takdirine bağlı olarak güncelleştirme hakkını saklı tutar. Sınıflandırıcılar kuruluşunuza bu alanları izleme konusunda yardımcı olabilir ancak sınıflandırıcılar, kuruluşunuzun bu tür dil veya görüntüleri izleme veya ele alma için tek araçlarını sağlamayı amaçlamamaktadır. Yerel gizlilik ve diğer geçerli yasalar dahil olmak üzere, bu alanlardaki izleme, tarama ve engelleme dili ve görüntüleriyle ilgili tüm kararlardan Microsoft değil kuruluşunuz sorumludur. Microsoft, dağıtım ve kullanımdan önce hukuk müşaviri ile danışmayı teşvik eder.

> [!NOTE]
> Sınıflandırıcıları kullanan ilkeler, altı veya daha büyük sözcük sayısına sahip iletileri inceler ve değerlendirir. Altıdan az sözcük içeren iletiler sınıflandırıcılar kullanılarak ilkelerde değerlendirilmez. Uygunsuz içerik içeren daha kısa iletileri tanımlamak ve üzerinde işlem yapmak için, bu içerik türünü izleyen iletişim uyumluluk ilkelerine özel bir anahtar sözcük sözlüğü eklemenizi öneririz.

Eğitilebilir sınıflandırıcılar hakkında bilgi için bkz. [Eğitilebilir sınıflandırıcıları kullanmaya başlama](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Optik karakter tanıma (OCR)

Kuruluşunuzda uygunsuz olabilecek resimlerdeki yazdırılmış veya el yazısı metinleri taramak ve tanımlamak için yerleşik veya özel iletişim uyumluluk ilkelerini yapılandırın. Görüntülerdeki metinleri tanımlamaya yönelik tümleşik [Azure Bilişsel Hizmetler ve optik tarama desteği](/azure/cognitive-services/computer-vision/overview-ocr) , analistlerin ve araştırmacıların öncelikle metinsel olmayan iletişimlerde uygunsuz davranışlar olup olmadığını algılamalarına ve bu örnekler üzerinde işlem yapmalarına yardımcı olur.

Şablonlardan, özel ilkelerden yeni ilkelerde optik karakter tanımayı (OCR) etkinleştirebilir veya ekli görüntüleri ve ekleri işleme desteğini genişletmek için mevcut ilkeleri güncelleştirebilirsiniz. İlke şablonundan oluşturulan bir ilkede etkinleştirildiğinde, e-posta ve Microsoft Teams sohbet iletilerine eklenmiş veya eklenmiş görüntüler için otomatik tarama desteklenir. Belge dosyalarına eklenmiş görüntüler için OCR taraması desteklenmez. Özel ilkeler için, OCR tarama seçimini etkinleştirmek için ilkede anahtar sözcükler, yerleşik sınıflandırıcılar veya hassas bilgi türleriyle ilişkili bir veya daha fazla koşullu ayar yapılandırılmalıdır.

Aşağıdaki görüntü biçimlerinde 50 KB ile 4 MB arasındaki görüntüler taranır ve işlenir:

- .jpg/.jpeg (ortak fotoğraf uzmanları grubu)
- .png (taşınabilir ağ grafikleri)
- .bmp (bit eşlem)
- .tiff (etiket görüntüsü dosya biçimi)
- .pdf (taşınabilir belge biçimi)

> [!NOTE]
> Ekli ve ekli .pdf görüntüleri için tarama ve ayıklama şu anda yalnızca e-posta iletileri için desteklenmektedir.

OCR etkin ilkeler için bekleyen uyarılar gözden geçirilirken, ilke koşullarıyla tanımlanan ve eşleşen görüntüler ilişkili uyarılar için alt öğe olarak görüntülenir. Tanımlanan metni özgün iletiyle bağlamda değerlendirmek için özgün görüntüyü görüntüleyebilirsiniz. Algılanan görüntülerin uyarılarla kullanılabilir olması 48 saat kadar sürebilir.

### <a name="conditional-settings"></a>Koşullu ayarlar
<a name="ConditionalSettings"> </a>

İlke için seçtiğiniz koşullar, hem e-posta hem de kuruluşunuzdaki üçüncü taraf kaynaklardan (Instant Bloomberg gibi) gelen iletişimler için geçerlidir.

Aşağıdaki tabloda her koşul hakkında daha fazla bilgi ve bulabilirsiniz.

|**Durum**|**Bu koşulu kullanma**|
|:-----|:-----|
| **İçerik bu sınıflandırıcılardan herhangi biri ile eşleşir** | İletiye sınıflandırıcılar eklendiğinde veya dışlandığında ilkeye uygulayın. Bazı sınıflandırıcılar kiracınızda önceden tanımlanmıştır ve özel sınıflandırıcıların bu koşul için kullanılabilir hale gelmeden önce ayrı olarak yapılandırılması gerekir. Bir ilkede koşul olarak yalnızca bir sınıflandırıcı tanımlanabilir. Sınıflandırıcıları yapılandırma hakkında daha fazla bilgi için bkz. [Eğitilebilir sınıflandırıcılar (önizleme) hakkında bilgi edinin](classifier-learn-about.md). |
| **İçerik bu hassas bilgi türlerinden herhangi birini içerir** | İletiye herhangi bir hassas bilgi türü eklendiğinde veya dışlandığında ilkeye uygulayın. Bazı sınıflandırıcılar kiracınızda önceden tanımlanmıştır ve özel sınıflandırıcılar ayrı olarak veya koşul atama işleminin bir parçası olarak yapılandırılabilir. Seçtiğiniz her hassas bilgi türü ayrı ayrı uygulanır ve ilkenin iletiye uygulanması için bu hassas bilgi türlerinden yalnızca birinin geçerli olması gerekir. Özel hassas bilgi türleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md). |
| **İleti bu etki alanlarından herhangi birinden alınır**  <br><br> **İleti bu etki alanlarının hiçbirinden alınmaz** | Alınan iletilere belirli etki alanlarını veya e-posta adreslerini dahil etmek veya dışlamak için ilkeyi uygulayın. Her etki alanını veya e-posta adresini girin ve birden çok etki alanını veya e-posta adresini virgülle ayırın. Girilen her etki alanı veya e-posta adresi ayrı ayrı uygulanır, ilkenin iletiye uygulanması için yalnızca bir etki alanı veya e-posta adresi uygulanmalıdır. <br><br> Belirli bir etki alanındaki tüm e-postaları taramak, ancak gözden geçirilmesi gerekmeyen iletileri (bültenler, duyurular vb.) dışlamak istiyorsanız, e-posta adresini dışlayan **bu etki alanları koşulundan bir İleti alınmaz** (örneğin "newsletter@contoso.com") yapılandırmanız gerekir. |
| **İleti bu etki alanlarından herhangi birine gönderilir**  <br><br> **İleti bu etki alanlarından hiçbirine gönderilmez** | Gönderilen iletilere belirli etki alanlarını dahil etmek veya dışlamak için ilkeyi uygulayın. Her etki alanını girin ve birden çok etki alanını virgülle ayırın. Her etki alanı ayrı ayrı uygulanır, ilkenin iletiye uygulanması için yalnızca bir etki alanı uygulanmalıdır. <br><br> belirli iki etki alanına gönderilen tüm e-postaları dışlamak istiyorsanız, **İletinin bu etki alanları koşulundan hiçbirine gönderilmemesini iki etki alanıyla** (örneğin, 'contoso.com,wingtiptoys.com') yapılandırabilirsiniz. |
| **İleti bu etiketlerden herhangi biriyle sınıflandırılır**  <br><br> **İleti bu etiketlerden herhangi biriyle sınıflandırılmadı** | İletiye belirli bekletme etiketleri eklendiğinde veya hariç tutulduğunda ilkeyi uygulamak için. Bekletme etiketleri ayrı olarak yapılandırılmalıdır ve bu koşulun bir parçası olarak yapılandırılmış etiketler seçilir. Seçtiğiniz her etiket ayrı ayrı uygulanır (ilkenin iletiye uygulanması için bu etiketlerden yalnızca birinin geçerli olması gerekir). Bekletme etiketleri hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).|
| **İleti bu sözcüklerden herhangi birini içerir**  <br><br> **İleti bu sözcüklerden hiçbirini içermiyor** | İletiye belirli sözcükler veya tümcecikler eklendiğinde veya hariç tutulduğunda ilkeyi uygulamak için, her sözcüğü virgülle ayırarak girin. İki veya daha fazla sözcüğün tümcecikleri için, tümceciği tırnak içine alın. Girdiğiniz her sözcük veya tümcecik ayrı ayrı uygulanır (ilkenin iletiye uygulanması için yalnızca bir sözcük geçerli olmalıdır). Sözcük veya tümcecik girme hakkında daha fazla bilgi için, [e-postalarla veya eklerle sözcükleri ve tümcecikleri eşleştirme](communication-compliance-policies.md#Matchwords) bölümüne bakın.|
| **Ek bu sözcüklerden herhangi birini içerir**  <br><br> **Ek bu sözcüklerden hiçbirini içermiyor** | İleti ekine (word belgesi gibi) belirli sözcükler veya tümcecikler eklendiğinde veya dışlandığında ilkeyi uygulamak için, her sözcüğü virgülle ayırarak girin. İki veya daha fazla sözcüğün tümcecikleri için, tümceciği tırnak içine alın. Girdiğiniz her sözcük veya tümcecik ayrı ayrı uygulanır (ilkenin eke uygulanması için yalnızca bir sözcük geçerli olmalıdır). Sözcük veya tümcecik girme hakkında daha fazla bilgi için, [e-postalarla veya eklerle sözcükleri ve tümcecikleri eşleştirme](communication-compliance-policies.md#Matchwords) bölümüne bakın.|
| **Ek bu dosya türlerinden herhangi biridir**  <br><br> **Ek bu dosya türlerinden hiçbiri değildir** | Belirli ek türlerini içeren veya dışlayan iletişimleri denetlemek için dosya uzantılarını (.exe veya .pdf gibi) girin. Birden çok dosya uzantısını dahil etmek veya hariç tutmak istiyorsanız, virgülle ayrılmış dosya türlerini girin (örnek *.exe,.pdf,.zip*). İlkenin uygulanması için yalnızca bir ek uzantısı eşleşmelidir.|
| **İleti boyutu şundan büyük**  <br><br> **İleti boyutu şundan büyük değil:** | İletileri belirli bir boyuta göre gözden geçirmek için, bir iletinin gözden geçirilmeden önce olabileceği en büyük veya en düşük boyutu belirtmek için bu koşulları kullanın. Örneğin, **İleti boyutunun** **1,0 MB'tan**\> büyük olduğunu belirtirseniz, 1,01 MB ve daha büyük olan tüm iletiler gözden geçirilir. Bu koşul için bayt, kilobayt, megabayt veya gigabayt seçebilirsiniz.|
| **Ek,**  <br><br> **Ek şundan büyük değil:** | İletileri eklerinin boyutuna göre gözden geçirmek için, ileti ve ekleri gözden geçirilmeden önce bir ekin olabileceği en büyük veya en düşük boyutu belirtin. Örneğin, **Ekin 2,0 MB'tan**\> **büyük olduğunu** belirtirseniz, ekleri 2,01 MB ve üzeri olan tüm iletiler gözden geçirilir. Bu koşul için bayt, kilobayt, megabayt veya gigabayt seçebilirsiniz.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Sözcükleri ve tümcecikleri e-postalarla veya eklerle eşleştirme
<a name="Matchwords"> </a>

Girdiğiniz ve virgülle ayırdığınız her sözcük ayrı ayrı uygulanır (ilke koşulunun e-postaya veya eke uygulanması için yalnızca bir sözcük geçerli olmalıdır). Örneğin, **Message bu sözcüklerden herhangi birini ve** "banker", "gizli" ve "insider trading" anahtar sözcüklerini virgülle ayırarak (banker, gizli, "insider trading") koşulunu kullanalım. İlke "bankacı", "gizli" veya "insider trading" ifadesini içeren tüm iletiler için geçerlidir. Bu ilke koşulunun uygulanabilmesi için bu sözcüklerden veya tümceciklerden yalnızca biri gerçekleşmelidir. İletideki veya ekteki sözcükler girdiğiniz sözcüklerle tam olarak eşleşmelidir.

> [!IMPORTANT]
>
> Özel sözlük dosyası içeri aktarılırken, her sözcük veya tümcecik bir satır başıyla ve ayrı bir satırda ayrılmalıdır. Örneğin:
>
> *Bankacı* <br>
> *Gizli* <br>
> *insider trading*

Aynı anahtar sözcükler için hem e-posta iletilerini hem de ekleri taramak için, iletilerde taramak istediğiniz terimler için [özel bir anahtar sözcük sözlüğü](create-a-keyword-dictionary.md) oluşturun. Bu ilke yapılandırması, e-posta iletisinde **VEYA** e-posta ekinde görünen tanımlı anahtar sözcükleri tanımlar. İletilerdeki ve eklerdeki terimleri tanımlamak için standart koşullu ilke ayarlarını (*İleti bu sözcüklerden herhangi birini içerir* ve *Ek bu sözcüklerden herhangi birini içerir*) kullanmak, koşulların hem iletide **hem de** ekte bulunmasını gerektirir.

#### <a name="enter-multiple-conditions"></a>Birden çok koşul girin

Birden çok koşul girerseniz, Microsoft 365 iletişim uyumluluk ilkesinin iletişim öğelerine ne zaman uygulanacağını belirlemek için tüm koşulları birlikte kullanır. Birden çok koşul ayarladığınızda, özel durum girmediğiniz sürece ilkenin uygulanması için tüm koşulların karşılanması gerekir. Örneğin, bir ileti "ticaret" sözcüğünü içeriyorsa ve 2 MB'tan büyükse geçerli olan bir ilkeye ihtiyacınız vardır. Ancak iletide "Contoso finansal tarafından onaylandı" sözcükleri de varsa ilke geçerli olmamalıdır. Bu örnekte, üç koşul aşağıdaki gibi tanımlanabilir:

- İleti, "trade" anahtar sözcüğünü içeren **bu sözcüklerden herhangi birini içerir**
- **İleti boyutu** 2 MB değeriyle büyüktür
- İleti, "Contoso finansal ekibi tarafından onaylandı" anahtar sözcükleriyle **birlikte bu sözcüklerin hiçbirini içermiyor**

### <a name="review-percentage"></a>Gözden geçirme yüzdesi

Gözden geçirilmesi gereken içerik miktarını azaltmak istiyorsanız, iletişim uyumluluk ilkesi tarafından yönetilen tüm iletişimlerin yüzdesini belirtebilirsiniz. Seçilen ilke koşullarıyla eşleşen içeriğin toplam yüzdesi arasından gerçek zamanlı, rastgele bir içerik örneği seçilir. Gözden geçirenlerin tüm öğeleri gözden geçirmesini istiyorsanız, iletişim uyumluluk ilkesinde **%100'ünü** yapılandırabilirsiniz.

## <a name="alert-policies"></a>Uyarı ilkeleri

Bir ilkeyi yapılandırdıktan sonra, ilgili uyarı ilkesi otomatik olarak oluşturulur ve ilkede tanımlanan koşullarla eşleşen iletiler için uyarılar oluşturulur. İlke oluşturulduktan sonra etkinlik göstergelerinden uyarıların alınması 24 saat kadar sürebilir. Varsayılan olarak, tüm ilke eşleşmeleri uyarı tetikleyicilerine ilişkili uyarı ilkesinde bir orta önem düzeyi atanır. İlişkili uyarı ilkesinde toplama tetikleyicisi eşik düzeyi karşılandığında, bir iletişim uyumluluk ilkesi için uyarılar oluşturulur. İlke koşullarıyla eşleşen tek tek iletilerin sayısına bakılmaksızın, uyarılar için her 24 saatte bir tek bir e-posta bildirimi gönderilir. Örneğin, Contoso'nun uygunsuz bir içerik ilkesi etkindir ve 1 Ocak'ta altı uyarı oluşturan 100 ilke eşleşmesi vardır. Altı uyarı için tek bir e-posta bildirimi 1 Ocak'ın sonunda gönderilir.

İletişim uyumluluk ilkeleri için aşağıdaki uyarı ilkesi değerleri varsayılan olarak yapılandırılır:

|**Uyarı ilkesi tetikleyicisi**|**Varsayılan değer**|
|:-----|:-----|
| Toplama | Basit toplama |
| Eşik | Varsayılan: 4 etkinlik <br> Minimum: 3 etkinlik <br> Maksimum: 2.147.483.647 etkinlik |
| Pencere | Varsayılan: 60 dakika <br> En az: 60 dakika <br> Maksimum: 10.000 dakika |

> [!NOTE]
> Etkinlikler için uyarı ilkesi eşik tetikleyici ayarları, iletişim uyumluluk ilkeleri için en az 3 veya daha yüksek bir değeri destekler.

Microsoft Purview uyumluluk portalındaki **Uyarı ilkeleri** sayfasında, uyarı ilkelerindeki etkinlik sayısı, etkinlikler dönemi ve belirli kullanıcılar için tetikleyiciler için varsayılan ayarları değiştirebilirsiniz.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Uyarı ilkesinin önem düzeyini değiştirme

Belirli bir iletişim uyumluluk ilkesi için uyarı ilkesinde atanan önem düzeyini değiştirmek istiyorsanız aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) oturum açın.

2. Microsoft Purview uyumluluk portalında **İlkeler'e** gidin.

3. **uyarılar ilkeleri** sayfasını açmak için **İlkeler** sayfasında **Office 365 uyarıyı** seçin.

4. Güncelleştirmek istediğiniz iletişim uyumluluk ilkesinin onay kutusunu ve ardından **İlkeyi düzenle'yi** seçin.

5. **İlke** uyarı düzeyini yapılandırmak için Açıklama sekmesinde **Önem Derecesi** açılan listesini seçin.

6. İlkeye yeni önem derecesi düzeyini uygulamak için **Kaydet'i** seçin.

7. Uyarı ilkesi ayrıntıları sayfasından çıkmak için **Kapat'ı** seçin.
