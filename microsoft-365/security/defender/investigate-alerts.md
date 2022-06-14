---
title: Microsoft 365 Defender'da uyarıları araştırma
description: Cihazlar, kullanıcılar ve posta kutuları arasında görülen uyarıları araştırın.
keywords: olaylar, uyarılar, araştırma, analiz etme, yanıt, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: b80bbb747ab9a0aefebaa4dd5721370ba56a3890
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057725"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Microsoft 365 Defender'da uyarıları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

>[!Note]
>Bu makalede Microsoft 365 Defender'deki güvenlik uyarıları açıklanmaktadır. Ancak, kullanıcılar Microsoft 365 belirli etkinlikler gerçekleştirdiğinde kendinize veya diğer yöneticilere e-posta bildirimleri göndermek için etkinlik uyarılarını kullanabilirsiniz. Daha fazla bilgi için bkz. [Etkinlik uyarıları oluşturma - Microsoft Purview | Microsoft Docs](../../compliance/create-activity-alerts.md).

Uyarılar tüm olayların temelini oluşturur ve ortamınızda kötü amaçlı veya şüpheli olayların oluştuğuna işaret eder. Uyarılar genellikle daha geniş kapsamlı bir saldırının parçasıdır ve bir olay hakkında ipuçları sağlar.

Microsoft 365 Defender'da, ilgili uyarılar [olayları](incidents-overview.md) oluşturmak için bir araya toplanır. Olaylar her zaman bir saldırının daha geniş bağlamını sağlar, ancak daha derin analiz gerektiğinde uyarıları analiz etmek değerli olabilir.

**Uyarılar kuyruğu** geçerli uyarı kümesini gösterir. Microsoft 365 Defender [portalının](https://go.microsoft.com/fwlink/p/?linkid=2077139) hızlı başlatılması sırasında **Olaylar & uyarılar > Uyarılar'dan uyarılar** kuyruğuna ulaşabilirsiniz.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Microsoft 365 Defender portalındaki Uyarılar bölümü" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender ve Microsoft 365 Defender gibi farklı Microsoft güvenlik çözümlerinden uyarılar burada görünür.

Varsayılan olarak, Microsoft 365 Defender portalındaki uyarılar kuyruğu son 30 güne ait yeni ve devam eden uyarıları görüntüler. En son uyarı listenin en üstündedir, böylece önce siz görebilirsiniz. 

Varsayılan uyarılar kuyruğundan **Filtre'yi** seçerek bir **Filtre** bölmesi görebilirsiniz. Bu bölmeden uyarıların bir alt kümesini belirtebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Microsoft 365 Defender portalındaki Filtreler bölümü." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

Uyarıları şu ölçütlere göre filtreleyebilirsiniz:

- Önem derecesi
- Durum
- Hizmet kaynakları
- Varlıklar (etkilenen varlıklar)
- Otomatik araştırma durumu

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Office 365 için Defender uyarıları için gerekli roller

Office 365 için Microsoft Defender uyarılarına erişmek için aşağıdaki rollerden birine sahip olmanız gerekir:

- Azure Active Directory (Azure AD) genel roller için:

   - Genel yönetici

   - Güvenlik yöneticisi

   - Güvenlik İşleci

   - Genel Okuyucu

   - Güvenlik Okuyucusu

- Office 365 Güvenlik & Uyumluluk Rol Grupları

   - Uyumluluk Yöneticisi

   - Kuruluş Yönetimi 

- [Özel bir rol](custom-roles.md)

## <a name="analyze-an-alert"></a>Uyarıyı analiz etme

Ana uyarı sayfasını görmek için uyarının adını seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Microsoft 365 Defender portalında uyarının ayrıntıları" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

Uyarıyı **yönet** **bölmesinden Ana uyarı sayfasını aç** eylemini de seçebilirsiniz.

Uyarı sayfası şu bölümlerden oluşur: 

- Bu uyarıyla ilgili olayların ve uyarıların kronolojik sırada zinciri olan uyarı hikayesi
- Özet ayrıntıları

Uyarı sayfası boyunca, uyarıyı başka bir olaya bağlama gibi kullanılabilir eylemleri görmek için herhangi bir varlığın yanındaki üç noktayı (**...**) seçebilirsiniz. Kullanılabilir eylemlerin listesi uyarı türüne bağlıdır.

### <a name="alert-sources"></a>Uyarı kaynakları

Microsoft 365 Defender uyarılar Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender gibi çözümlerden gelebilir Microsoft Defender for Cloud Apps ve Microsoft Defender for Cloud Apps için uygulama idare eklentisi. Uyarıda önceden eklenmiş karakterler içeren uyarılar fark edebilirsiniz. Aşağıdaki tabloda uyarının ekli karakterine göre uyarı kaynaklarının eşlemesini anlamanıza yardımcı olacak yönergeler sağlanmaktadır.

> [!NOTE]
> - Önceden eklenen GUID'ler yalnızca birleşik uyarılar kuyruğu, birleşik uyarılar sayfası, birleşik araştırma ve birleştirilmiş olay gibi birleşik deneyimlere özeldir.
> - Ekli karakter uyarının GUID değerini değiştirmez. GUID'de yapılan tek değişiklik, önceden eklenen bileşendir.

| Uyarı kaynağı | Ekli karakter |
| :---|:--- |
| Office 365 için Microsoft Defender | `fa{GUID}` <br> Örnek: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Uç Nokta için Microsoft Defender | `da` veya `ed` özel algılama uyarıları için <br> |
| Kimlik için Microsoft Defender | `aa{GUID}` <br> Örnek: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Bulut Uygulamaları için Microsoft Defender |`ca{GUID}` <br> Örnek: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Etkilenen varlıkları analiz etme

**Gerçekleştirilen eylemler** bölümünde posta kutuları, cihazlar ve bu uyarıdan etkilenen kullanıcılar gibi etkilenen varlıkların listesi bulunur. 

ayrıca **, Microsoft 365 Defender portalında İşlem merkezinin** **Geçmiş** sekmesini görüntülemek için **İşlem merkezinde** görüntüle'yi de seçebilirsiniz. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Uyarı yazısında uyarının rolünü izleme

Uyarı hikayesi, bir işlem ağacı görünümünde uyarıyla ilgili tüm varlıkları veya varlıkları görüntüler. Başlıktaki uyarı, seçtiğiniz uyarının sayfasına ilk kez girdiğinizde odakta olan uyarıdır. Uyarı hikayesindeki varlıklar genişletilebilir ve tıklanabilir. Ek bilgiler sağlar ve uyarı sayfası bağlamında işlem yapmanıza olanak tanıyarak yanıtınızı hızlandırırlar. 

> [!NOTE]
> Uyarı hikayesi bölümünde birden fazla uyarı bulunabilir ve seçtiğiniz uyarıdan önce veya sonra aynı yürütme ağacıyla ilgili ek uyarılar görüntülenir.

### <a name="view-more-alert-information-on-the-details-page"></a>Ayrıntılar sayfasında daha fazla uyarı bilgisi görüntüleyin

Ayrıntılar sayfası, seçili uyarının ayrıntılarını ve bununla ilgili ayrıntıları ve eylemleri gösterir. Uyarı yazısında etkilenen varlıklardan veya varlıklardan herhangi birini seçerseniz, ayrıntılar sayfası seçili nesne için bağlamsal bilgiler ve eylemler sağlayacak şekilde değişir.

İlgilendiğiniz bir varlığı seçtikten sonra ayrıntılar sayfası seçili varlık türüyle ilgili bilgileri, kullanılabilir olduğunda geçmiş bilgileri ve doğrudan uyarı sayfasından bu varlık üzerinde eylem gerçekleştirme seçeneklerini görüntüleyecek şekilde değişir.

## <a name="manage-alerts"></a>Uyarıları yönetin

Uyarıyı yönetmek için uyarı sayfasının özet ayrıntıları bölümünde Uyarıyı **yönet'i** seçin. Tek bir uyarı için **Uyarıyı yönet** bölmesinin bir örneği aşağıda verilmiştır.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Microsoft 365 Defender portalındaki Uyarıyı yönet bölümü" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

**Uyarıyı yönet** bölmesi şunları görüntülemenize veya belirtmenize olanak tanır:

- Uyarı durumu (Yeni, Çözüldü, Sürüyor).
- Uyarıya atanan kullanıcı hesabı.
- Uyarının sınıflandırması:

   - **Ayarlanmadı** (varsayılan).

   - Bir tehdit türüyle **gerçek pozitif**. Gerçek bir tehdidi doğru şekilde gösteren uyarılar için bu sınıflandırmayı kullanın. Tehdit türünü belirtmek, güvenlik ekibinizin tehdit desenlerini görmesine ve kuruluşunuzu onlardan korumak için harekete geçilmesine yardımcı olur.

   - Bir etkinlik türüyle **bilgilendirici, beklenen** etkinlik. Güvenlik testlerine, kırmızı ekip etkinliğine ve güvenilen uygulama ve kullanıcılardan beklenen olağan dışı davranışlara yönelik uyarıları sınıflandırmak için bu kategorideki seçenekleri kullanın.

   - Kötü amaçlı etkinlik olmadığında bile oluşturulan uyarı türleri için **hatalı pozitif**. Uyarıları hatalı pozitif olarak sınıflandırmak Microsoft 365 Defender algılama kalitesini artırmaya yardımcı olur.

- Uyarıyla ilgili bir açıklama.

> [!NOTE]
> Etiketleri kullanarak uyarıları yönetmenin bir yolu. Office 365 için Microsoft Defender etiketleme özelliği artımlı olarak kullanıma sunulmuştur ve şu anda önizleme aşamasındadır. <br>
> Şu anda değiştirilen etiket adları yalnızca *güncelleştirmeden sonra* oluşturulan uyarılara uygulanır. Değişiklik öncesinde oluşturulan uyarılar güncelleştirilmiş etiket adını yansıtmaz. 

*Belirli bir uyarıya benzer bir uyarı kümesini yönetmek için* uyarı sayfasının özet ayrıntıları bölümündeki **INSIGHT** kutusunda **Benzer uyarıları görüntüle'yi** seçin.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Microsoft 365 Defender portalında uyarıyı yönetme":::

**Uyarıları yönet** bölmesinden, tüm ilgili uyarıları aynı anda sınıflandırabilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Microsoft 365 Defender portalında ilgili uyarıları yönetme":::

Benzer uyarılar geçmişte zaten sınıflandırıldıysa, diğer uyarıların nasıl çözüldüğünü öğrenmek için Microsoft 365 Defender önerileri kullanarak zaman kazanabilirsiniz. Özet ayrıntıları **bölümünden Öneriler'ı** seçin.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Uyarı önerileri seçme örneği":::

**Öneriler** sekmesi araştırma, düzeltme ve önleme için sonraki adım eylemler ve öneriler sağlar. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Uyarı önerileri örneği":::

## <a name="resolve-an-alert"></a>Uyarıyı çözme

Bir uyarıyı çözümlemeyi tamamladıktan ve çözümlenebildiğiniz zaman, uyarı veya benzer uyarılar için **Uyarıyı yönet** bölmesine gidin ve durumu **Çözüldü** olarak işaretleyin ve ardından bir tehdit **türü,** **Bilgilendirici,** etkinlik türüyle beklenen etkinlik veya **Hatalı pozitif** olarak sınıflandırın.

Uyarıları sınıflandırmak Microsoft 365 Defender algılama kalitesini artırmaya yardımcı olur.

## <a name="use-power-automate-to-triage-alerts"></a>Uyarıları önceliklendirmek için Power Automate kullanma

Modern güvenlik operasyonları (SecOps) ekiplerinin etkili bir şekilde çalışması için otomasyon gerekir. SecOps ekipleri, gerçek tehditleri avlamaya ve araştırmaya odaklanmak için Power Automate kullanarak uyarı listesini önceliklendirmek ve tehdit olmayanları ortadan kaldırır.  

### <a name="criteria-for-resolving-alerts"></a>Uyarıları çözümleme ölçütleri

- Kullanıcının İşyeri Dışında iletisi açık

- Kullanıcı yüksek riskli olarak etiketlenmemiş

Her ikisi de doğruysa, SecOps uyarıyı geçerli seyahat olarak işaretler ve çözer. Uyarı çözümlendikten sonra Microsoft Teams bir bildirim gönderilir.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps Bağlan Power Automate

Otomasyonu oluşturmak için, Power Automate Microsoft Defender for Cloud Apps bağlayabilmeniz için bir API belirteci gerekir.

1. **Ayarlar'e** tıklayın, **Güvenlik uzantıları'nı** seçin ve ardından **API belirteçleri** sekmesinde **Belirteç ekle'ye** tıklayın.

2. Belirteciniz için bir ad girin ve **Oluştur'a** tıklayın. Daha sonra ihtiyacınız olacak şekilde belirteci kaydedin.

### <a name="create-an-automated-flow"></a>Otomatik akış oluşturma

Otomasyonun sorunsuz bir iş akışı oluşturmak için verimli bir şekilde nasıl çalıştığını ve Power Automate Bulut için Defender Uygulamalarına nasıl bağlanacağını öğrenmek için bu kısa videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn]

## <a name="next-steps"></a>Sonraki adımlar

İşlem içi olaylar için gerektiğinde [araştırmanıza](investigate-incidents.md) devam edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları yönetin](manage-incidents.md)
- [Olayları araştırın](investigate-incidents.md)
- [Veri kaybı olaylarını araştırma](investigate-dlp.md)