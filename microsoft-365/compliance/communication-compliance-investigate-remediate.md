---
title: İletişim uyumluluğu uyarılarını araştırma ve çözümleme
description: Microsoft Purview'da iletişim uyumluluk uyarılarını araştırın ve düzeltin.
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 7f1afe62dcb7dabf55b48985354653b9418d0561
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971637"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>İletişim uyumluluğu uyarılarını araştırma ve çözümleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

İletişim uyumluluk ilkelerinizi yapılandırdıktan sonra, ilke koşullarınızla eşleşen ileti sorunları için Microsoft Purview uyumluluk portalında uyarılar almaya başlarsınız. Uyarı sorunlarını araştırmak ve düzeltmek için buradaki iş akışı yönergelerini izleyin.

## <a name="investigate-alerts"></a>Uyarıları araştırın

İlkeleriniz tarafından algılanan sorunları araştırmanın ilk adımı, Microsoft Purview uyumluluk portalındaki iletişim uyumluluğu uyarılarını gözden geçirmektir. Uyarı gruplandırma şeklini görüntülemeyi tercih ettiğinize bağlı olarak, uyarıları hızlı bir şekilde araştırmanıza yardımcı olmak için iletişim uyumluluk çözümü alanında birkaç alan vardır:

- **İletişim uyumluluk ilkesi sayfası**: Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) oturum açtığınızda, iletişim uyumluluk İlkesi sayfasını görüntülemek için **İletişim uyumluluğu'na** tıklayın. Bu sayfada, Microsoft 365 kuruluşunuz için yapılandırılmış iletişim uyumluluk ilkeleri ve önerilen ilke şablonlarının bağlantıları görüntülenir. Listelenen her ilke gözden geçirilmesi gereken uyarıların sayısını, yükseltilen ve çözümlenen öğelerin sayısını, ilkenin durumunu ve son ilke taramasının tarih ve saatini içerir. İlke seçildiğinde, ilkeyle eşleşmeler için tüm bekleyen uyarılar görüntülenir, ilke ayrıntıları sayfasını başlatmak ve düzeltme eylemlerini başlatmak için belirli bir uyarı seçin.
- Uyarılar: İlke **eşleşmelerine** göre gruplandırılmış son 30 günlük uyarıları görüntülemek için **İletişim uyumluluğuAlerts** >  bölümüne gidin. Bu görünüm, önem derecesine göre en çok uyarı oluşturan iletişim uyumluluk ilkelerini hızla görmenizi sağlar. Düzeltme eylemlerini başlatmak için uyarıyla ilişkili ilkeyi seçerek **İlke ayrıntıları** sayfasını başlatın. **İlke ayrıntıları** sayfasından **Genel Bakış** sayfasındaki etkinliklerin özetini gözden geçirebilir, **Bekleyen** sayfasındaki uyarı iletilerini gözden geçirebilir ve üzerinde işlem yapabilir veya **Çözümlenenler** sayfasındaki kapalı uyarıların geçmişini gözden geçirebilirsiniz.
- **Raporlar**: İletişim uyumluluğu Rapor pencere öğelerini görüntülemek için **İletişim** **uyumluluğuReports'a** >  gidin. Her pencere öğesi, ilke eşleşmeleri ve düzeltme eylemleri hakkında daha ayrıntılı içgörülere erişim de dahil olmak üzere iletişim uyumluluk etkinliklerine ve durumlarına genel bir bakış sağlar.

### <a name="using-filters"></a>Filtreleri kullanma

Sonraki adım, uyarıları araştırmanızı kolaylaştırmak için iletileri sıralamaktır. İletişim uyumluluğu, **İlke ayrıntıları** sayfasından, ilke eşleşmeleriyle iletileri hızla araştırmanıza ve gözden geçirmenize yardımcı olmak için çeşitli ileti alanları için çok düzeyli filtrelemeyi destekler. Her yapılandırılmış ilke için bekleyen ve çözümlenen öğeler için filtreleme kullanılabilir. Bir ilke için filtre sorgularını yapılandırabilir veya özel ve varsayılan filtre sorgularını her bir ilkede kullanılmak üzere yapılandırıp kaydedebilirsiniz. Bir filtre için alanları yapılandırdıktan sonra, belirli filtre değerleri için yapılandırabileceğiniz uyarı iletisi kuyruğunun en üstünde görüntülenen filtre alanlarını görürsünüz.

Tarih filtresi için, olayların tarih ve saati Eşgüdümlü Evrensel Saat (UTC) içinde listelenir. Görünümler için iletileri filtrelerken, istekte bulunan kullanıcının yerel tarih/saatinin UTC'ye dönüştürülmesi temelinde sonuçları belirler. Örneğin, ABD Pasifik Yaz Saati (PDT) içindeki bir kullanıcı 30.08.2021 ile 31.08.2021 saat 00:00 arasında bir raporu filtrelerse, rapor 30.08.2021 07:00 UTC ile 31.08.2021 07:00 UTC arası iletileri içerir. Saat 00:00'da filtreleme yaparken aynı kullanıcı ABD Doğu Yaz Saati'nde (EDT) bulunuyorsa, rapor 30.08.2021 04:00 UTC ile 31.08.2021 04:00 UTC arası iletileri içerir.

#### <a name="filter-details"></a>Filtre ayrıntıları

İletişim uyumluluğu filtreleri, daha hızlı araştırma ve düzeltme eylemleri için uyarı iletilerini filtrelemenize ve sıralamanıza olanak sağlar. Filtreleme, her ilke için **Bekleyen** ve **Çözümlenen** sekmelerinde kullanılabilir. Bir filtreyi veya filtre kümesini kaydedilmiş bir filtre sorgusu olarak kaydetmek için bir veya daha fazla değerin filtre seçimi olarak yapılandırılması gerekir.

Aşağıdaki tabloda filtre ayrıntıları özetlenmiştir:

|**Filtre**|**Ayrıntılar**|
|:-----|:-----|
| **Tarih** | İletinin kuruluşunuzdaki bir kullanıcı tarafından gönderildiği veya alındığı tarih. Tek bir güne filtre uygulamak için, sonuçları istediğiniz günle başlayan ve sonraki günle biten bir tarih aralığı seçin. Örneğin, 20/9/2020 için sonuçları filtrelemek istiyorsanız, 20/9/2020-9/21/2020 filtre tarih aralığını seçersiniz.|
| **Dosya sınıfı** | İleti türüne göre iletinin sınıfı( *ileti* veya *ek*). |
| **Eki var** | İletideki ek iletişim durumu. |
| **Item sınıfı** | İleti türü, e-posta, Microsoft Team sohbeti, Bloomberg vb. temelinde iletinin kaynağı. Yaygın Öğe Türleri ve İleti Sınıfları hakkında daha fazla bilgi için bkz. [Öğe Türleri ve İleti Sınıfları](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Alıcı etki alanları** | İletinin gönderildiği etki alanı. Bu etki alanı normalde varsayılan olarak Microsoft 365 abonelik etki alanınızdır. |
| **Alıcı** | İletinin gönderildiği kullanıcı. |
| **Gönderen** | İletiyi gönderen kişi. |
| **Gönderen etki alanı** | İletiyi gönderen etki alanı. |
| **Boyutu** | İletinin KB cinsinden boyutu. |
| **Konu/Başlık** | İleti konusu veya sohbet başlığı. |
| **Etiketler** | İletiye atanan etiketler *(Sorgulanabilir*, *Uyumlu* veya *Uyumsuz*). |
| **Dil** | İletideki metnin algılanan dili. İleti, ileti metninin büyük bölümünün diline göre sınıflandırılır. Örneğin, hem Almanca hem de İtalyanca metin içeren ancak metnin büyük bölümü Almanca olan bir ileti için ileti Almanca (DE) olarak sınıflandırılır. Aşağıdaki diller desteklenir: Çince (Basitleştirilmiş - ZH), İngilizce (EN), Fransızca (FR), Almanca (DE), İtalyanca (BT), Japonca (JP), Portekizce (PT) ve İspanyolca (ES). Örneğin, Almanca ve İtalyanca olarak sınıflandırılan iletileri filtrelemek için Dil filtresi arama kutusuna 'DE,IT' (2 basamaklı dil kodları) yazın. İletinin algılanan dil sınıflandırmasını görüntülemek için bir ileti seçin, İleti ayrıntılarını görüntüle'yi seçin ve E-posta AlgılandıDil alanına gidin. |
| **İlerletilen** | İleti yükseltme eyleminin bir parçası olarak dahil edilen kişinin kullanıcı adı. |
| **Sınıflandırıcı** | İletiye uygulanan yerleşik ve özel sınıflandırıcıların adı. Bazı örnekler *arasında Hedefli Taciz*, *Küfür*, *Tehdit* ve daha fazlası yer alır.

#### <a name="to-configure-a-filter"></a>Filtre yapılandırmak için

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) oturum açın.

2. Microsoft Purview uyumluluk portalında **İletişim uyumluluğu'na** gidin.

3. **İlkeler** sekmesini seçin ve araştırmak üzere bir ilke seçin, **İlke** sayfasını açmak için çift tıklayın.

4. **İlke** sayfasında, filtrelemeye yönelik öğeleri görüntülemek için **Beklemede** veya **Çözümlendi** sekmesini seçin.

5. **Filtreler** denetimini seçerek **Filtreler** ayrıntıları sayfasını açın.

6. Bu uyarılar için filtreleri etkinleştirmek için bir veya daha fazla onay kutusu seçin. *Tarih*, *Gönderen*, *Konu/Başlık*, *Sınıflandırıcılar*, *Dil* ve daha birçok filtre arasından seçim yapabilirsiniz.

7. Seçilen filtreyi varsayılan filtre olarak kaydetmek istiyorsanız **Varsayılan olarak kaydet'i** seçin. Bu filtreyi kaydedilmiş bir filtre olarak kullanmak istiyorsanız **Bitti'yi** seçin.

8. Seçili filtreleri filtre sorgusu olarak kaydetmek isterseniz, en az bir filtre değeri yapılandırdıktan sonra **sorgu denetimini kaydet'i** seçin. Filtre sorgusu için bir ad girin ve **Kaydet'i** seçin. Bu filtre yalnızca bu ilke için kullanılabilir ve **Filtreler** ayrıntıları sayfasının **Kayıtlı filtre sorguları** bölümünde listelenir.

    ![İletişim uyumluluk filtresi ayrıntı denetimleri.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Yakın ve tam yinelenen analizi kullanma

İletişim uyumluluk ilkeleri, ek yapılandırma adımları olmadan iletinin yakın ve tam yinelemelerini otomatik olarak tarar ve önceden gruplandırılır. Bu görünüm, benzer iletiler üzerinde tek tek veya grup olarak hızlı bir şekilde işlem yapmanızı sağlayarak gözden geçirenlerin ileti araştırma yükünü azaltır. Yinelemeler algılandıkçe, Düzeltme eylemi araç çubuğunda **Yakın Yinelemeler** ve/veya **Tam Yinelemeler** denetimleri görüntülenir. Yakın veya tam yinelemeler bulunamazsa bu görünüm kullanılamaz.

#### <a name="to-remediate-duplicates"></a>Yinelenenleri düzeltmek için

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) oturum açın.

2. Microsoft Purview uyumluluk portalında **İletişim uyumluluğu'na** gidin.

3. **İlkeler** sekmesini seçin ve araştırmak üzere bir ilke seçin, **İlke** sayfasını açmak için çift tıklayın.

4. yinelenen iletileri görüntülemek için **İlke** sayfasında **Bekleyen** veya **Çözümlendi** sekmesini seçin.

5. Yineleme ayrıntıları sayfasını açmak için **Yakın Yinelemeler** veya **Tam Yinelemeler** denetimlerini seçin.

6. Bu iletiler için düzeltme eylemi denetimleri için bir veya daha fazla ileti seçin.

7. Eylemi varsayılan filtre olarak seçili yinelenen **iletilere** uygulamak için **Çözümle**, **Bildir**, Yükselt veya **İndir'i** seçin.

8. İletilerde düzeltme eylemlerini tamamladıktan sonra **Kapat'ı** seçin.

    ![İletişim uyumluluğu denetimleri tam olarak yineler.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Uyarıları düzeltme

Uyarıları veya yapılandırdığınız filtrelemeyi gözden geçirmeye nereden başlarsanız başlayın, sonraki adım uyarıyı düzeltmek için eyleme geçmektir. **İlke** veya **Uyarılar** sayfalarında aşağıdaki iş akışını kullanarak uyarı düzeltmenizi başlatın.

### <a name="step-1-examine-the-message-basics"></a>1. Adım: İletinin temellerini inceleme

 Bazen kaynaktan veya konudan bir iletinin hemen düzeltilebileceği açıktır. İletinin sahte veya yanlış bir şekilde bir ilkeyle eşleştirilmiş olması ve yanlış sınıflandırılmış olarak çözümlenmesi gerekebilir. Yanlış sınıflandırılmış içeriği Microsoft ile paylaşmak, uyarıyı hemen çözümlemek ve bekleyen uyarı kuyruğundan kaldırmak için Yanlış **sınıflandırılmış olarak raporla** denetimini seçin. Kaynak veya gönderen bilgilerinden, iletinin bu durumlarda nasıl yönlendirilmesi veya işlenmesi gerektiğini zaten biliyor olabilirsiniz. Geçerli iletilere etiket atamak veya belirlenen gözden geçirene ileti göndermek için **Etiket olarak** veya **Yükseltme** denetimlerini kullanmayı göz önünde bulundurun.

![İletişim uyumluluğu düzeltme denetimleri.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>2. Adım: İleti ayrıntılarını inceleme

İletinin temellerini gözden geçirdikten sonra, ayrıntıları incelemek ve diğer düzeltme eylemlerini belirlemek için bir ileti açmanın zamanı geldi. İleti üst bilgisinin ve gövde bilgilerinin tamamını görüntülemek için bir ileti seçin. Uygun eylem seyrini belirlemenize yardımcı olmak için çeşitli farklı seçenekler ve görünümler mevcuttur:

- **Ekler**: Bu seçenek, ilke koşullarıyla eşleşen Modern ekleri incelemenize olanak tanır. Modern ekler içeriği metin olarak ayıklanır ve bir ilke için Bekleyen uyarılar panosunda görüntülenebilir. Daha fazla bilgi için bkz [. İletişim uyumluluğu özelliği başvurusu](/microsoft-365/compliance/communication-compliance-channels).
- **Kaynak**: Bu görünüm, web tabanlı mesajlaşma platformlarının çoğunda yaygın olarak görülen standart ileti görünümüdür. Üst bilgi normal stilde biçimlendirilir ve ileti gövdesi, imbedded grafik dosyalarını ve sözcük kaydırılan metni destekler. İlke için [optik karakter tanıma (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) etkinleştirildiyse, ilke koşulluyla eşleşen yazdırılmış veya el yazısı metin içeren görüntüler, bu görünümdeki ilişkili ileti için alt öğe olarak görüntülenir.
- **Düz metin**: Metin görünümü, iletinin satır numaralı yalnızca metin görünümünü görüntüler ve hassas bilgi türü terimleri veya ilişkili iletişim uyumluluk ilkesinde eşleşen anahtar sözcükler için iletilerde ve eklerde anahtar sözcük vurgulama içerir. Anahtar sözcük vurgulama, uzun iletileri ve ekleri ilgilendiğiniz alan için hızla taramanıza yardımcı olabilir. Bazı durumlarda, vurgulanan metin yalnızca ilke koşullarıyla eşleşen iletiler için eklerde olabilir. Anahtar sözcük vurgulama, bir ilkeye atanan yerleşik sınıflandırıcılar tarafından tanımlanan terimler için desteklenmez. Katıştırılmış dosyalar görüntülenmez ve bu görünümün satır numaralandırması, birden çok gözden geçiren arasında ilgili ayrıntılara başvurmak için yararlıdır.
- **Konuşma (önizleme)**: Microsoft Teams sohbet iletileri için bu görünüm, gözden geçirenlerin etkinliği konuşma bağlamında görüntülemesine yardımcı olmak için bir uyarı iletisinden önce ve sonra en fazla beş ileti görüntüler. Bu bağlam, gözden geçirenlerin iletileri hızla değerlendirmesine ve daha bilinçli ileti çözümleme kararları vermesine yardımcı olur. Konuşmalara gerçek zamanlı ileti eklemeleri, Teams'da bulunan tüm satır içi resimler, emojiler ve çıkartmalar da dahil olmak üzere görüntülenir. İletilere resim veya metin dosyası ekleri görüntülenmez. Düzenlenen iletiler veya konuşma penceresinden silinmiş iletiler için bildirimler otomatik olarak görüntülenir. İleti çözümlendiğinde, ilişkili konuşma iletileri çözümlenen iletiyle birlikte korunmaz. Konuşma iletileri, uyarı iletisi tanımlandıktan sonra 60 güne kadar kullanılabilir.
- **Kullanıcı geçmişi**: Kullanıcı geçmişi görünümü, iletiyi gönderen kullanıcı için herhangi bir iletişim uyumluluk ilkesi tarafından oluşturulan diğer tüm uyarıları görüntüler.
- **Desen algılandı bildirimi**: Zaman içinde birçok taciz ve zorbalık eylemi ve aynı davranışın örneklerinin bir kullanıcı tarafından yeniden yinelenmesi gerekir. *Desen algılandı* bildirimi uyarı ayrıntılarında görüntülenir ve uyarıya dikkat çekmektedir. Desenlerin algılanması ilke başına temel alınır ve gönderen tarafından aynı alıcıya en az iki ileti gönderildiğinde son 30 gün içindeki davranışı değerlendirir. Araştırmacılar ve gözden geçirenler, uyarıyı uygun şekilde değerlendirmek üzere yinelenen davranışı belirlemek için bu bildirimi kullanabilir.
- **Çeviri**: Bu görünüm, uyarı iletisi metnini her gözden geçiren için Microsoft 365 aboneliğindeki *Görüntülenen dil* ayarında yapılandırılan dile otomatik olarak dönüştürür. *Çeviri* görünümü, çok dilli kullanıcıları olan kuruluşlara yönelik araştırma desteğini genişletmeye yardımcı olur ve iletişim uyumluluğu gözden geçirme sürecinin dışında ek çeviri hizmetleri gereksinimini ortadan kaldırır. Microsoft çeviri hizmetleri kullanılarak *Çeviri* görünümü gerektiğinde açılıp kapatılabilir ve çok çeşitli dilleri destekler. Desteklenen dillerin tam listesi için bkz. [Microsoft Çeviri Dilleri](https://www.microsoft.com/translator/business/languages/). *Çeviri Dil Listesi'nde listelenen diller* *Çeviri* görünümünde desteklenir.

### <a name="step-3-decide-on-a-remediation-action"></a>3. Adım: Düzeltme eylemine karar verme

Uyarının iletisinin ayrıntılarını gözden geçirdiyseniz, birkaç düzeltme eylemi seçebilirsiniz:

- **Çözümle**: **Çözümle** denetiminin seçilmesi, iletiyi **Bekleyen uyarılar** kuyruğundan hemen kaldırır ve ileti üzerinde başka bir işlem yapılamaz. **Çözümle'yi** seçerek uyarıyı daha fazla sınıflandırma yapmadan kapattınız. Çözümlenen tüm iletiler **Çözümlendi** sekmesinde görüntülenir.
- **Yanlış sınıflandırılmış olarak raporla**: İletiyi her zaman ileti gözden geçirme iş akışı sırasında herhangi bir noktada yanlış sınıflandırılmış olarak çözümleyebilirsiniz. Yanlış sınıflandırılmış, uyarının eyleme dönüştürülemez olduğunu veya uyarının uyarı işlemi ve eğitilebilir sınıflandırıcılar tarafından yanlış oluşturulduğunu gösterir. Öğeyi yanlış sınıflandırılmış olarak çözümlemek, eğitilebilir sınıflandırıcıların geliştirilmesine yardımcı olmak için ileti içeriğini, ekleri ve ileti konusunu (meta veriler dahil) Microsoft'a gönderir. Microsoft'a gönderilen veriler, kuruluşunuzdaki kullanıcıları tanımlayacak veya tanımlamak için kullanılabilecek bilgiler içermez. İletide başka eylemler gerçekleştirilemez ve yanlış sınıflandırılmış tüm iletiler **Çözümlendi** sekmesinde görüntülenir.
- **Power Automate (önizleme):** Uyarı iletisi için işlem görevlerini otomatikleştirmek için Power Automate akışı kullanın. Varsayılan olarak, iletişim uyumluluğu, gözden geçirenlerin ileti uyarılarına sahip kullanıcılar için bildirim işlemini otomatikleştirmek için kullanabileceği *bir iletişim uyumluluğu uyarı akışı şablonuna sahip olduğunda bildirim yöneticisini* içerir. İletişim uyumluluğunda Power Automate akışları oluşturma ve yönetme hakkında daha fazla bilgi için bu makalenin **5. Adım: Power Automate akışlarını göz önünde bulundurun** bölümüne bakın.
- **Etiket olarak**: İletiyi *uyumlu*, *uyumsuz* veya kuruluşunuzun ilkeleri ve standartlarıyla ilgili olarak *sorgulanabilir* olarak etiketleyin. Etiketleri ve etiketleme açıklamalarını eklemek, yükseltmeler için veya diğer iç gözden geçirme işlemlerinin bir parçası olarak ilke uyarılarını mikro filtrelemenize yardımcı olur. Etiketleme tamamlandıktan sonra, iletiyi bekleyen gözden geçirme kuyruğundan taşımak için çözmeyi de seçebilirsiniz.
- **Bildirim**: **Uyarıya** özel bir bildirim şablonu atamak ve kullanıcıya uyarı bildirimi göndermek için Bildirim denetimini kullanabilirsiniz. **İletişim uyumluluk ayarları** alanında yapılandırılan uygun bildirim şablonunu seçin ve iletiyi gönderen kullanıcıya e-postayla anımsatıcı **gönder'i** seçerek sorunu çözün.
- **Yükseltme**: **Yükseltme** denetimini kullanarak, kuruluşunuzda başka kimlerin iletiyi gözden geçirmesi gerektiğini seçebilirsiniz. İleti uyarısının ek gözden geçirilmesini isteyen bir e-posta bildirimi göndermek için iletişim uyumluluk ilkesinde yapılandırılan gözden geçirenler listesinden seçim yapın. Seçilen gözden geçiren, doğrudan gözden geçirilecek öğelere gitmek için e-posta bildirimindeki bir bağlantıyı kullanabilir.
- **Araştırma için yükseltme**: **Araştırma için Yükseltme** denetimini kullanarak, tek veya birden çok ileti için yeni bir [eBulma (Premium) olayı](overview-ediscovery-20.md) oluşturabilirsiniz. Yeni servis talebi için bir ad ve notlar sağlayacaksınız ve ilkeyle eşleşen iletiyi gönderen kullanıcı otomatik olarak servis talebi koruyucu olarak atanır. Olayı yönetmek için ek izinlere ihtiyacınız yoktur. Servis talebi oluşturma, ileti için çözümlenmiyor veya yeni bir etiket oluşturmuyor. Düzeltme işlemi sırasında eBulma (Premium) olayı oluştururken toplam 100 ileti seçebilirsiniz. İletişim uyumluluğu tarafından izlenen tüm iletişim kanallarındaki iletiler desteklenir. Örneğin, bir kullanıcı için yeni bir eBulma (Premium) servis talebi açtığınızda 50 Microsoft Teams sohbet, 25 Exchange Online e-posta iletisi ve 25 Yammer iletisi seçebilirsiniz.
- **Teams'da iletiyi kaldırma**: **Teams denetimindeki İletiyi kaldır'ı** kullanarak, Microsoft Teams kanallardan ve 1:1 ve grup sohbetlerinden gelen uyarılarda tanımlanan uygunsuz iletileri ve içeriği engelleyebilirsiniz. Kaldırılan iletiler ve içerik, engellendiğini ve görünümden kaldırılması için geçerli olan ilkeyi açıklayan bir ilke ipucuyla değiştirilir. İlgili ilke ve gözden geçirme işlemi hakkında daha fazla bilgi edinmek için alıcılara ilke ipucunda bir bağlantı sağlanır. Gönderen, engellenen ileti ve içerik için bir ilke ipucu alır, ancak engellenen iletinin ayrıntılarını ve kaldırmayla ilgili bağlam için içeriği gözden geçirebilir.

    ![Microsoft Teams bir iletiyi kaldırın.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>4. Adım: İleti ayrıntılarının iletişim uyumluluğu dışında arşivlenip arşivlenmemesi gerektiğini belirleme

İletileri ayrı bir depolama çözümünde arşivlemeniz gerekiyorsa ileti ayrıntıları dışarı aktarılabilir veya indirilebilir. **İndir** denetiminin seçilmesi, seçilen iletileri otomatik olarak Microsoft 365 dışında depolama alanına kaydedilebilen bir .ZIP dosyasına ekler.

### <a name="step-5-consider-power-automate-flows"></a>5. Adım: Akışları Power Automate göz önünde bulundurun

[Microsoft Power Automate](/power-automate/getting-started), uygulamalar ve hizmetler genelinde eylemleri otomatik hale getiren bir iş akışı hizmetidir. Şablonlardan gelen veya el ile oluşturulan akışları kullanarak, bu uygulama ve hizmetlerle ilişkili ortak görevleri otomatikleştirebilirsiniz. İletişim uyumluluğu için Power Automate akışlarını etkinleştirdiğinizde, uyarılar ve kullanıcılar için önemli görevleri otomatikleştirebilirsiniz. kullanıcılar iletişim uyumluluk uyarılarına ve diğer uygulamalara sahip olduğunda yöneticileri bilgilendirmek için Power Automate akışları yapılandırabilirsiniz.

İletişim uyumluluğu içeren Microsoft 365 abonelikleri olan müşterilerin önerilen varsayılan iletişim uyumluluğu Power Automate şablonunu kullanmak için ek Power Automate lisanslarına ihtiyacı yoktur. Varsayılan şablon, kuruluşunuzu destekleyecek ve temel iletişim uyumluluk senaryolarını kapsayacak şekilde özelleştirilebilir. Bu şablonlardaki premium Power Automate özelliklerini kullanmayı, Microsoft Purview bağlayıcısını kullanarak özel bir şablon oluşturmayı veya Microsoft Purview'daki diğer uyumluluk alanları için Power Automate şablonları kullanmayı seçerseniz ek Power Automate lisanslarına ihtiyacınız olabilir.

> [!IMPORTANT]
> Power Automate akışlarını test ederken ek lisans doğrulaması istemleri mi alıyorsunuz? Kuruluşunuz henüz bu önizleme özelliği için hizmet güncelleştirmeleri almamış olabilir. Güncelleştirmeler dağıtılıyor ve iletişim uyumluluğu içeren Microsoft 365 abonelikleri olan tüm kuruluşların 30 Ekim 2020'ye kadar önerilen Power Automate şablonlarından oluşturulan akışlar için lisans desteğine sahip olması gerekir.

![İletişim uyumluluğu Power Automate.](../media/communication-compliance-power-automate.png)

Aşağıdaki Power Automate şablonu, müşterilere iletişim uyumluluk uyarıları için işlem otomasyonunu desteklemek üzere sağlanır:

- **Kullanıcının iletişim uyumluluk uyarısı olduğunda yöneticiye bildirme: Bir kullanıcı iletişim uyumluluk uyarısına** sahip olduğunda bazı kuruluşların anında yönetim bildirimine sahip olması gerekebilir. Bu akış yapılandırılıp seçildiğinde, servis talebi kullanıcısının yöneticisine tüm uyarılar hakkında aşağıdaki bilgileri içeren bir e-posta iletisi gönderilir:
  - Uyarı için geçerli ilke
  - Uyarının tarih/saati
  - Uyarının önem derecesi düzeyi

#### <a name="create-a-power-automate-flow"></a>Power Automate akışı oluşturma

Önerilen varsayılan şablondan Power Automate akışı oluşturmak için, doğrudan bir uyarıda çalışırken **Otomatikleştirme** denetimindeki **Power Automate akışlarını yönet** seçeneğini kullanacaksınız. Power Automate **akışlarını yönet ile Power Automate akışı** oluşturmak için en az bir iletişim uyumluluk rol grubunun üyesi olmanız gerekir.

Varsayılan şablondan Power Automate akışı oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **İletişim** **uyumluluğuİlkeler'e** >  gidin ve gözden geçirmek istediğiniz uyarıyı içeren ilkeyi seçin.
2. İlkeden **Bekleyen** sekmesini seçin ve bekleyen bir uyarı seçin.
3. Uyarı eylemi **menüsünden Power Automate** seçin.
4. **Power Automate** sayfasında, sayfadaki **İletişim uyumluluk şablonları** bölümünden varsayılan bir şablon seçin.
5. Akış, akış için gereken ekli bağlantıları listeler ve bağlantı durumlarının kullanılabilir olup olmadığını görüntüler. Gerekirse, kullanılabilir olarak görüntülenmemiş bağlantıları güncelleştirin. **Devam'ı** seçin.
6. Varsayılan olarak, önerilen akışlar önerilen iletişim uyumluluğuyla önceden yapılandırılır ve akış için atanan görevi tamamlamak için gereken hizmet verileri alanlarını Microsoft 365. Gerekirse Gelişmiş **seçenekleri göster** denetimini kullanarak ve akış bileşeni için kullanılabilir özellikleri yapılandırarak akış bileşenlerini özelleştirin.
7. Gerekirse **, Yeni adım** düğmesini seçerek akışa ek adımlar ekleyin. Çoğu durumda, önerilen varsayılan şablonlar için bu değişiklik gerekli olmamalıdır.
8. Akışı daha sonra yapılandırmak üzere kaydetmek için **Taslağı kaydet'i** veya akışın yapılandırmasını tamamlamak için **Kaydet'i** seçin.
9. Power Automate akışı sayfasına dönmek için **Kapat'ı** seçin. Yeni şablon **Akışlarım** sekmesinde akış olarak listelenir ve iletişim uyumluluk uyarılarıyla çalışırken akışı oluşturan kullanıcının Power Automate denetiminden otomatik olarak kullanılabilir.

#### <a name="share-a-power-automate-flow"></a>Power Automate akışı paylaşma

Varsayılan olarak, bir kullanıcı tarafından oluşturulan Power Automate akışları yalnızca o kullanıcı tarafından kullanılabilir. Diğer iletişim uyumluluğu kullanıcılarının bir akışa erişmesi ve akış kullanması için akışın akış oluşturucusu tarafından paylaşılması gerekir. Akışı paylaşmak için doğrudan bir uyarıda çalışırken **Power Automate** denetimini kullanacaksınız.

bir Power Automate akışını paylaşmak için en az bir iletişim uyumluluk rol grubunun üyesi olmanız gerekir.
Power Automate akışını paylaşmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **İletişim** **uyumluluğuİlkeler'e** >  gidin ve gözden geçirmek istediğiniz uyarıyı içeren ilkeyi seçin.
2. İlkeden **Bekleyen** sekmesini seçin ve bekleyen bir uyarı seçin.
3. Uyarı eylemi **menüsünden Power Automate** seçin.
4. **Power Automate akışları** sayfasında **Akışlarım** veya **Ekip akışları** sekmesini seçin.
5. Paylaşacak akışı seçin ve ardından akış seçenekleri menüsünden **Paylaş'ı** seçin.
6. Akış paylaşımı sayfasında, akışın sahibi olarak eklemek istediğiniz kullanıcı veya grubun adını girin.
7. **Bağlantı Kullanıldı** iletişim kutusunda **Tamam'ı** seçerek eklenen kullanıcı veya grubun akışa tam erişimi olacağını kabul edin.

#### <a name="edit-a-power-automate-flow"></a>Power Automate akışını düzenleme

Bir akışı düzenlemeniz gerekiyorsa, doğrudan bir uyarıda çalışırken **Power Automate** denetimini kullanırsınız. Power Automate akışını düzenlemek için en az bir iletişim uyumluluk rol grubunun üyesi olmanız gerekir.

Power Automate akışını düzenlemek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **İletişim** **uyumluluğuİlkeler'e** >  gidin ve gözden geçirmek istediğiniz uyarıyı içeren ilkeyi seçin.
2. İlkeden **Bekleyen** sekmesini seçin ve bekleyen bir uyarı seçin.
3. Uyarı eylemi **menüsünden Power Automate** seçin.
4. **Power Automate akışları** sayfasında düzenlemek için akışı seçin. Akış denetimi menüsünde **Düzenle'yi** seçin.
5. Bir akış bileşeni ayarını değiştirmek için **üç nokta** >  **Ayarlar** veya bir akış bileşenini silmek için **üç** >  **noktaDele** seçeneğini belirleyin.
6. Akışı düzenlemeyi tamamlamak için **Kaydet'i** ve ardından **Kapat'ı** seçin.

#### <a name="delete-a-power-automate-flow"></a>Power Automate akışını silme

Bir akışı silmeniz gerekiyorsa, doğrudan bir uyarıda çalışırken **Power Automate** denetimini kullanırsınız. Power Automate akışını silmek için en az bir iletişim uyumluluk rol grubunun üyesi olmanız gerekir.

Power Automate akışını silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **İletişim** **uyumluluğuİlkeler'e** >  gidin ve gözden geçirmek istediğiniz uyarıyı içeren ilkeyi seçin.
2. İlkeden **Bekleyen** sekmesini seçin ve bekleyen bir uyarı seçin.
3. Uyarı eylemi **menüsünden Power Automate** seçin.
4. **Power Automate akışlar** sayfasında silinecek akışı seçin. Akış denetimi menüsünde **Sil'i** seçin.
5. Silme onayı iletişim kutusunda Akışı kaldırmak için **Sil'i** seçin veya silme eyleminden çıkmak için **İptal'i** seçin.

### <a name="step-6-consider-creating-notice-templates"></a>6. Adım: Bildirim şablonları oluşturmayı göz önünde bulundurun

Kullanıcılara sorun çözme işleminin bir parçası olarak ilke eşleşmeleri için bir e-posta anımsatıcı bildirimi göndermek istiyorsanız bildirim şablonları oluşturabilirsiniz. Bildirimler yalnızca düzeltme için belirli bir uyarıyı oluşturan ilke eşleşmesiyle ilişkili kullanıcı e-posta adresine gönderilebilir. Düzeltme iş akışının bir parçası olarak bir ilke ihlaline uygulanacak bir bildirim şablonu seçerken, şablonda tanımlanan alan değerlerini kabul etmeyi veya gerektiğinde alanların üzerine yazmayı seçebilirsiniz.

Bildirimler şablonları, **İletişim uyumluluk ayarları** alanında aşağıdaki ileti alanlarını tanımlayabileceğiniz özel e-posta şablonlarıdır:

|**Alan**|**Gerekli**| **Ayrıntılar** |
|:-----|:-----|:-----|
|**Şablon adı** | Evet | Düzeltme sırasında bildirim iş akışında seçeceğiniz bildirim şablonunun kolay adı, metin karakterlerini destekler. |
| **Gönderen adresi** | Evet | Aboneliğiniz için Active Directory'den seçilen ilke eşleşmesiyle kullanıcıya ileti gönderen bir veya daha fazla kullanıcı veya grubun adresi. |
| **BILGI ve Gizli adresleri** | Hayır | aboneliğiniz için Active Directory'den seçilen ilke eşleşmesinin bildirilmesi için isteğe bağlı kullanıcılar veya gruplar. |
| **Konu** | Evet | İletinin konu satırında görünen bilgiler metin karakterlerini destekler. |
| **İleti gövdesi** | Evet | İleti gövdesinde görünen bilgiler metin veya HTML değerlerini destekler. |

### <a name="html-for-notices"></a>Bildirimler için HTML

Bildirimler için basit bir metin tabanlı e-posta iletisinden daha fazlasını oluşturmak isterseniz, bildirim şablonunun ileti gövdesi alanında HTML kullanarak daha ayrıntılı bir ileti oluşturabilirsiniz. Aşağıdaki örnek, temel HTML tabanlı e-posta bildirim şablonu için ileti gövdesi biçimini sağlar:

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

> [!NOTE]
> İletişim uyumluluk bildirim şablonlarındaki HTML href özniteliği uygulaması şu anda URL başvuruları için çift tırnak işaretleri yerine yalnızca tek tırnak işaretlerini destekler.

## <a name="unresolve-messages-preview"></a>İletileri çözme (önizleme)

İletiler çözümlendiğinde **Bekleyen sekme** görünümünden kaldırılır ve **Çözümlenen** sekme görünümünde görüntülenir. Araştırma ve düzeltme eylemleri *Çözümlenmiş* görünümündeki iletiler için kullanılamaz. Ancak, yanlışlıkla çözümlenen veya ilk çözümden sonra daha fazla araştırma gerektiren bir ileti üzerinde ek işlem yapmanız gereken örnekler olabilir. Çözümlenmemiş komut özelliğini kullanarak Bir veya daha fazla iletiyi *Çözümlenmiş* görünümünden *Beklemede* görünümüne geri taşıyabilirsiniz.

İletileri çözümlemek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki *İletişim Uyumluluk Analisti* veya *İletişim Uyumluluğu Araştırmacısı* rol gruplarına atanmış bir kullanıcının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) oturum açın.
2. Microsoft Purview uyumluluk portalında **İletişim uyumluluğu'na** gidin.
3. **İlkeler** sekmesini seçin ve ardından çözümlenen uyarı iletisini içeren bir ilke seçin, **İlke** sayfasını açmak için çift tıklayın.
4. **İlke** sayfasında **Çözümlendi** sekmesini seçin.
5. **Çözümlendi** sekmesinde, *Beklemede'ye* geri dönmek için bir veya daha fazla ileti seçin.
6. Komut çubuğunda **Çözümle'yi** seçin.
7. **Öğeyi çözümle** bölmesinde, çözümlenmemiş eyleme uygulanabilir açıklamaları ekleyin ve **Kaydet'i** seçerek öğeyi *Beklemede'ye* geri taşıyın.
8. Seçili öğelerin görüntülendiğini doğrulamak için **Beklemede** sekmesini seçin.
