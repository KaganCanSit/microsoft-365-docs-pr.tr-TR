---
title: Yanıtla birlikte olay Microsoft 365 Defender
description: Mobil portalda cihazlar, kullanıcılar ve posta kutuları genelinde görülen Microsoft 365 Defender araştırabilirsiniz.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
- MET150
ms.technology: m365d
ms.openlocfilehash: ac908a03aad2ccbe203877250a84185cb6c8da16
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015543"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Yanıtla birlikte olay Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).
>

Microsoft 365 Defender'daki bir olay, bir saldırının hikayesini ifade etmek için birbiriyle ilişkili uyarılar ve ilişkili veriler koleksiyonudur. 

Microsoft 365 ve uygulamalar, şüpheli veya kötü amaçlı bir etkinlik algılayana kadar uyarılar oluşturabilir. Tek tek uyarılar tamamlanmış veya devam eden bir saldırı hakkında değerli ipuçları sağlar. Öte yandan, saldırılar genellikle cihazlar, kullanıcılar ve posta kutuları gibi farklı varlık türlerine karşı çeşitli teknikler kullanır. Sonuç, kiracınız içinde birden çok varlık için birden çok uyarıdır. 

Tek tek uyarıları bir saldırı hakkında fikir edinmek için bir araya toplamak zor ve zaman alıcı olduğundan, Microsoft 365 Defender uyarıları ve ilgili bilgilerini otomatik olarak bir olayda bir araya toplar.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Nasıl Microsoft 365 Defender varlıklardan gelen olayları bir olayla nasıl ilişkili olduğunu gösterir." lightbox="../../media/incidents-overview/incidents.png":::

Bu kısa ve son dakika olaylarını genel Microsoft 365 Defender (4 dakika) izleyin.

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

İlgili uyarıları bir olayda gruplama, saldırının kapsamlı bir görünümünü sağlar. Örneğin, şunları görüyoruz:

- Saldırının başladığı yer.
- Hangi taktikler kullanılmış?
- Saldırının kiracınıza ne kadar gittiğini.
- Saldırının kapsamı (kaç cihaz, kullanıcı ve posta kutusu etkilendi olduğu gibi). 
- Saldırıyla ilişkili tüm veriler.

[Etkinleştirilirse](m365d-enable.md), Microsoft 365 Defender ve yapay [zeka aracılığıyla](m365d-autoir.md) uyarıları otomatik olarak inceler ve çözebilir. Ayrıca, saldırıyı çözmek için ek düzeltme adımları da gerçekleştirebilirsiniz. 

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Portalda olaylar ve Microsoft 365 Defender uyarılar

Olayları, & **portalının hızlı > başlatmada Olaylardan** ve Olaylar'dan <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender yönetirsiniz</a>. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Portalda Olay Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Olay adı seçerek olayın özeti görüntülenir ve sekmelere ek bilgilerle birlikte erişim sağlar. İşte bir örnek.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Portalda bir olay için Özet Microsoft 365 Defender örneği" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Bir olayın ek sekmeleri:

- Uyarılar 

  Olayla ilgili tüm uyarılar ve onların bilgileri.

- Cihazlar

  Olayın parçası veya ilgili olduğu belirlenen tüm cihazlar.

- Kullanıcılar

  Olayın bir parçası veya ilgili olduğu belirlenen tüm kullanıcılar.

- Posta Kutuları

  Olayın parçası veya ilgili olduğu belirlenen tüm posta kutuları.

- İncelemeler

  Olayda [uyarılar tarafından](m365d-autoir.md) tetiklenen tüm otomatik soruşturmalar.

- Kanıt ve Yanıt

  Olayın uyarılarında desteklenen tüm olaylar ve şüpheli varlıklar.

- Graph (Önizleme)

  Saldırının parçası olan farklı şüpheli varlıkları kullanıcılar, cihazlar ve posta kutuları gibi ilişkili varlıklarıyla bağlayan saldırının görsel bir gösterimi.

İşte bir olayla verileri arasındaki ilişki ve portalda bir olayın sekmeleri Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Bir olayın ve bu olayın verileriyle portal portalında bir olayın sekmeleri Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>İş Akışları için örnek olay Microsoft 365 Defender

Burada, Microsoft 365 Defender portalıyla iş akışında yer alan olayları Microsoft 365 için örnek Microsoft 365 Defender ve açık bir iş akışı vardır.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Microsoft 365 için olay yanıtı iş akışı Microsoft 365." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

Sürekli olarak, en yüksek öncelikli olayları analiz ve çözüm için olay sırasına tanıyın ve onları yanıt için hazırlayın. Bu, şunların bir bileşimidir:

- [En yüksek](incident-queue.md) öncelikli olayları, olay sırasına filtre uygulama ve sıralama yoluyla belirlemek için öncelik belirleme.
- [Başlıklarını](manage-incidents.md) değiştirerek, bunları bir analiste ataarak, etiketler ve açıklamalar ekleyerek olayları yönetme.

Kendi olay yanıtı iş akışınız için şu adımları göz önünde bulundurabilirsiniz:

1. Her olay için bir saldırı [ve uyarı soruşturması ve çözümlemesi başlayacaktır](investigate-incidents.md):
 
   1. Olayın kapsamını ve önem derecesini anlamak ve Özet ve Güvenlik (Önizleme) sekmelerinde hangi varlıkların etkilendiğini **anlamak Graph** görünümüne bakın.

   1. uyarılar sekmesiyle kaynaklarını, kapsamını ve önem derecesini anlamak için uyarıları **çözümlemeye** başlayabilirsiniz.

   1. Gerektiğinde, Cihazlar, Kullanıcılar ve Posta Kutuları sekmeleriyle etkilenen **cihazlar, kullanıcılar** ve posta kutuları **hakkında bilgi** toplayın.

   1. İncelemeler Microsoft 365 Defender [uyarıların otomatik olarak çözüme kavuşturularak](m365d-autoir.md) nasıl **çözülmüş olduğunu** görebilirsiniz.
   
   1. Gerekirse, Kanıt ve Yanıt sekmesiyle daha fazla bilgi için olayın veri **kümesinde yer alan bilgileri** kullanın.

2. Çözümlemeniz sonrasında veya çözümlemeniz sırasında, saldırı üzerindeki ek etkiyi azaltmak ve güvenlik tehditini ortadan kaldırmayı gerçekleştirmek için etkiyi gerçekleştirin.

3. Mümkün olduğunca, kiracı kaynaklarınızı olaydan önce içinde olduğu durumlara geri yükleyerek saldırıdan kurtarin.

4. [Olayı](manage-incidents.md#resolve-an-incident) çözerek olay sonrası öğrenmenin zamanlarını şu şekilde öğrenin:

   - Saldırının türünü ve etkisini anlıyoruz.
   - Tehdit Analiz'de [ve güvenlik](threat-analytics.md) topluluğunda güvenlik saldırı eğilimi için saldırıyı araştırnın.
   - Olayı çözmek için kullanılan iş akışını geri çağırabilir ve standart iş akışlarınızı, süreçlerinizi, ilkelerinizi ve çalışma kitaplarınızı gereken şekilde güncelleştirebilirsiniz.
   - Güvenlik yapılandırmanıza gereken değişikliklerin gerekli olup olmadığını belirler ve bunları gerçekleştirin.

Güvenlik çözümlemesinde yeniysiniz, ek bilgi almak [](incidents-overview.md) ve örnek bir olayın üzerinden geçerek ilk olayınıza yanıt verme giriş bilgilerine bakın.

Microsoft ürünleri genelinde olay yanıtı hakkında daha fazla bilgi için bu [makaleye bakın](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Güvenlik önlemleri için örnek güvenlik Microsoft 365 Defender

Burada, güvenlik işlemleri için örnek bir (SecOps) Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Güvenlik işlemleri için örnek Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Günlük görevler şunlar olabilir:

- [Olayları](manage-incidents.md) yönetme
- İşlem Merkezinde [otomatik araştırma ve yanıt (AIR)](m365d-action-center.md) eylemlerini gözden geçirme
- En son Threat [Analytics'i gözden geçirme](threat-analytics.md)
- [Olayları](investigate-incidents.md) yanıtla

Aylık görevler şunlardan bazıları olabilir:

- AIR ayarlarını [gözden geçirme](m365d-configure-auto-investigation-response.md)
- Güvenlik [Puanını ve](microsoft-secure-score-improvement-actions.md) Tehdit [Güvenlik &'i gözden geçirme](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- IT güvenlik yönetimi zincirinize bildirme

Üç aylık görevler, Güvenlik Görevlisi (CISO) için bir rapor ve güvenlik sonuçları özetleri içerebilir.

Yıllık görevler, personelinizi, sistemlerinizi ve süreçlerinizi test etmek için önemli bir olay ya da ihlal çalışması gerçekleştirmeyi içerebilir. 

Süreçleri, ilkeleri ve güvenlik yapılandırmalarını güncelleştirmek veya geliştirmek için günlük, aylık, üç aylık ve yıllık görevler kullanılabilir.

Daha [ fazla Microsoft 365 Defender için bkz. Güvenliğinizi güvenlik işlemleriyle](integrate-microsoft-365-defender-secops.md) tümleştirme.

### <a name="secops-resources-across-microsoft-products"></a>Microsoft ürünleri genelinde SecOps kaynakları

Microsoft ürünleri genelinde SecOps hakkında daha fazla bilgi için şu kaynaklara bakın:

- [Özellikler](/security/compass/security-operations-capabilities)
- [En iyi yöntemler](/security/compass/security-operations)
- [Videolar ve slaytlar](/security/compass/security-operations-videos-and-decks)


## <a name="get-incident-notifications-by-email"></a>E-postayla olay bildirimlerini alın

Yeni olaylar veya Microsoft 365 Defender güncelleştirmeleri içeren bir e-posta ile personelinizi bilgilendiren ekipler oluşturabilirsiniz. Şu temel bildirim bildirimlerini alırsınız:

- Olay önem derecesi.
- Cihaz grubu.
- Yalnızca olay başına ilk güncelleştirmede.

E-posta bildiriminde olay adı, önem derecesi ve kategoriler gibi olayla ilgili önemli ayrıntılar ve diğerleri yer alır. Ayrıca doğrudan olayın üzerine gidip çözümlemenizi hemen başlatabilirsiniz. Daha fazla bilgi için bkz [. Olayları araştırma](investigate-incidents.md).

E-posta bildirimlerine alıcı ekleyebilir veya alıcıları kaldırabilirsiniz. Yeni alıcılar eklendikten sonra olaylar hakkında bilgi alır. 

>[!NOTE]
>E-posta **bildirimi ayarlarını yapılandırmak için** Güvenlik ayarlarını yönetme iznine sahip olmak gerekir. Temel izin yönetimini kullanmayı seçtiyseniz, Güvenlik Yöneticisi veya Genel Yönetici rolüne sahip kullanıcılar e-posta bildirimlerini yapılandırabilirsiniz. <br> <br>
Benzer şekilde, kuruluşta rol tabanlı erişim denetimi (RBAC) kullanıyorsa, yalnızca yönetmenize izin verilen cihaz gruplarına göre bildirim oluşturabilir, düzenleyebilir, silebilir ve alabilirsiniz.

### <a name="create-a-rule-for-email-notifications"></a>E-posta bildirimleri için kural oluşturma

Yeni bir kural oluşturmak ve e-posta bildirimi ayarlarını özelleştirmek için bu adımları izleyin.

1. Gezinti bölmesinde, Olay **e-Ayarlar > Microsoft 365 Defender > e-posta bildirimlerini seçin**.
2. Öğe **ekle'yi seçin**.
3. Temel **Bilgiler sayfasında** , kural adını ve açıklamasını yazın ve Ardından Sonraki'yi **seçin**.
4. Bildirim **ayarları sayfasında** şunları yapılandırabilirsiniz:
    - **Uyarı önem derecesi** - Olay bildirimini tetikleyen uyarı önem derecelerini seçin. Örneğin, yalnızca yüksek önem derecesine sahip olaylar hakkında bilgi sahibi olmak için Yüksek'i **seçin**.
    - **Cihaz grubu kapsamı** - Tüm cihaz gruplarını belirtebilirsiniz veya kiracınız için cihaz grupları listesinden seçim edebilirsiniz.
    - **Her olay için yalnızca ilk kez bildir** - Yalnızca diğer seçimlerinizi eşleşen ilk uyarıda bildirim almak için bildirim almak için seçin. Daha sonra, olayla ilgili güncelleştirmeler veya uyarılar ek bildirim göndermez.
    - **E-postaya kuruluş adını dahil** edin - Kuruluş adının e-posta bildiriminde görünmesini istediğinizi seçin.
    - **Kiracıya özgü portal bağlantısını ekle** - Belirli bir kiracıya erişim için e-posta bildiriminde kiracı kimliğiyle bir bağlantı eklemek Microsoft 365 seçin.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Olay e-posta bildirimleri için bildirim ayarları." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. **İleri**'yi seçin. Alıcılar **sayfasında** , olay bildirimlerini alacak e-posta adreslerini ekleyin. Her yeni **e-posta** adresini yazdikten sonra Ekle'yi seçin. Bildirimleri test etmek ve alıcıların bunları gelen kutularında almalarını sağlamak için Test **e-postası gönder'i seçin**. 
6. **İleri**'yi seçin. Kuralı gözden **geçir sayfasında** , kuralın ayarlarını gözden geçirin ve Kural **oluştur'a tıklayın**. Alıcılar ayarlara göre e-posta aracılığıyla olay bildirimleri almaya başlar.

Var olan bir kuralı düzenlemek için, kural listesinden kuralı seçin. Kural adının olduğu bölmede, **Kuralı düzenle'yi** seçin ve Temel **Bilgiler, Bildirim** ayarları ve **Alıcılar** sayfalarında **değişikliklerinizi** yapın.

Bir kuralı silmek için kural listesinden seçin. Kural adının olduğu bölmede Sil'i **seçin**.


## <a name="training-for-security-analysts"></a>Güvenlik analistleri için eğitim

Microsoft Learn'un bu öğrenme modülünü kullanarak olayları ve uyarıları Microsoft 365 Defender nasıl kullanabileceğinizi öğrenin.

|Eğitim:|Olayları araştırarak Microsoft 365 Defender|
|---|---|
|![En iyi eğitim Microsoft 365 Defender olayları araştırabilirsiniz.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender çok hizmetten gelen tehdit verilerini birleştirir ve AI'yi kullanarak bunları olay ve uyarılarda bir araya kullanır. Sonraki yanıt ve çözüm için bir olayla onun yönetimi arasındaki zamanı en aza indirmeyi öğrenin. <p> 27 dak. - 6 Birim |

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Sonraki adımlar

Güvenlik ekibinizin deneyim düzeyine veya rolüne bağlı olarak listelenen adımları kullanın.

### <a name="experience-level"></a>Deneyim düzeyi

Güvenlik çözümlemesi ve olay yanıtı deneyimi düzeyiniz için bu tabloyu izleyin.

| Düzey | Adımlar |
|:-------|:-----|
| **Yeni** | <ol><li> Örnek bir [saldırıyla](first-incident-overview.md) Microsoft 365 Defender portalında tipik bir çözümleme, düzeltme ve olay sonrası inceleme sürecinde rehberli bir tur için İlk olayınızı yanıtlama kılavuzuna bakın. </li><li> Önem düzeyine ve diğer [etmenlere göre hangi olaylara](incident-queue.md) önceliklendirmeleri gerektiğini bakın. </li><li> [Olay yönetimi](manage-incidents.md) iş akışınıza dayalı olarak yeniden başlatma, atama, sınıflama ve etiketlerle açıklamalar ekleme gibi olayları yönetin.</li></ol> |
| **Deneyimli** | <ol><li> İlk portalın Olaylar sayfasından **, olay** kuyruğuyla Microsoft 365 Defender. Buradan: </li> <ul><li> Önem düzeyine ve diğer [etmenlere göre hangi olaylara](incident-queue.md) önceliklendirmeleri gerektiğini bakın. </li><li> [Olay yönetimi](manage-incidents.md) iş akışınıza dayalı olarak yeniden başlatma, atama, sınıflama ve etiketlerle açıklamalar ekleme gibi olayları yönetin. </li><li> [Olaylarda](investigate-incidents.md) soruşturmalar gerçekleştirin. </li></ul> </li><li> Tehdit analizi ile ortaya çıkan tehditleri takip edin [ve yanıt verin](threat-analytics.md). </li><li>  Gelişmiş tehdit avıyla tehditlere [karşı önceden arama.](advanced-hunting-overview.md) </li><li> Kimlik avı [, parola parola parolaları](/security/compass/incident-response-playbooks) ve uygulama izni izni saldırılarına yönelik ayrıntılı kılavuzlar için bu olay yanıt çalışma kitaplarına bakın. </li></ol> |


### <a name="security-team-role"></a>Güvenlik ekibi rolü

Bu tabloyu, güvenlik ekibi rolünüz temel alarak izleyin.

| Rol | Adımlar |
|:-------|:-----|
| Olay yanıtlayan (Katman 1) | İlk portalın Olaylar sayfasından **, olay** kuyruğuyla Microsoft 365 Defender. Buradan: <ul><li> Önem düzeyine ve diğer [etmenlere göre hangi olaylara](incident-queue.md) önceliklendirmeleri gerektiğini bakın. </li><li> [Olay yönetimi](manage-incidents.md) iş akışınıza dayalı olarak yeniden başlatma, atama, sınıflama ve etiketlerle açıklamalar ekleme gibi olayları yönetin. </li></ul> |
| Güvenlik analisti veya analist (Katman 2) | <ol><li> İlk [portalın](investigate-incidents.md) Olaylar **sayfasından** olay incelemeleri Microsoft 365 Defender. </li><li> Kimlik avı [, parola parola parolaları](/security/compass/incident-response-playbooks) ve uygulama izni izni saldırılarına yönelik ayrıntılı kılavuzlar için bu olay yanıt çalışma kitaplarına bakın. </li></ol> |
| Gelişmiş güvenlik analisti veya tehdit analisti (Katman 3) | <ol><li>İlk [portalın](investigate-incidents.md) Olaylar **sayfasından** olay incelemeleri Microsoft 365 Defender. </li><li> Tehdit analizi ile ortaya çıkan tehditleri takip edin [ve yanıt verin](threat-analytics.md). </li><li> Gelişmiş tehdit avıyla tehditlere [karşı önceden arama.](advanced-hunting-overview.md) </li><li> Kimlik avı [, parola parola parolaları](/security/compass/incident-response-playbooks) ve uygulama izni izni saldırılarına yönelik ayrıntılı kılavuzlar için bu olay yanıt çalışma kitaplarına bakın. |
| SOC manager | Güvenlik İşlemleri [Merkezi'Microsoft 365 Defender (SOC) bu uygulamaları nasıl tümleştirin?](integrate-microsoft-365-defender-secops.md) |

