---
title: Veri kaybı önleme hakkında daha fazla bilgi edinme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Microsoft Purview veri kaybı önleme ilkelerini ve araçlarını kullanarak hassas bilgilerinizi korumayı öğrenin ve DLP yaşam döngüsünde bir tura katılın.
ms.openlocfilehash: aa32eba1111f4a119652ba88b59062581bb6cc4b
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231802"
---
# <a name="learn-about-data-loss-prevention"></a>Veri kaybı önleme hakkında daha fazla bilgi edinme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşların denetimi altında finansal veriler, özel veriler, kredi kartı numaraları, sağlık kayıtları veya sosyal güvenlik numaraları gibi hassas bilgiler bulunur. Bu hassas verilerin korunmasına ve riskin azaltılmasına yardımcı olmak için, kullanıcılarının bunları sahip olmaması gereken kişilerle uygunsuz bir şekilde paylaşmasını önlemek için bir yönteme ihtiyaçları vardır. Bu uygulamaya veri kaybı önleme (DLP) adı verilir.

Microsoft Purview'da, DLP ilkelerini tanımlayıp uygulayarak veri kaybı önleme uygularsınız. DLP ilkesiyle hassas öğeleri tanımlayabilir, izleyebilir ve otomatik olarak koruyabilirsiniz:

- Teams, Exchange, SharePoint ve OneDrive gibi hizmetleri Microsoft 365
- Word, Excel ve PowerPoint gibi uygulamaları Office
- Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) uç noktaları
- Microsoft dışı bulut uygulamaları
- şirket içi dosya paylaşımları ve şirket içi SharePoint.

DLP, hassas öğeleri yalnızca basit bir metin taramasıyla değil, derin içerik analizini kullanarak algılar. İçerik, normal ifadelerin değerlendirilmesi, iç işlev doğrulaması ve birincil veri eşleşmesine yakın ikincil veri eşleşmeleri tarafından anahtar sözcüklerle yapılan birincil veri eşleşmeleri için analiz edilir. Bunun ötesinde DLP, DLP ilkelerinizle eşleşen içeriği algılamak için makine öğrenmesi algoritmalarını ve diğer yöntemleri de kullanır.

## <a name="dlp-is-part-of-the-larger-microsoft-purview-offering"></a>DLP, daha büyük Microsoft Purview teklifinin bir parçasıdır

DLP, hassas öğelerinizi yaşadıkları veya seyahat ettikleri her yerde korumaya yardımcı olmak için kullanacağınız Microsoft Purview araçlarından yalnızca biridir. Microsoft Purview araçları kümesindeki diğer araçları, bunların nasıl birbiriyle ilişkilendirildiklerini ve birlikte nasıl daha iyi çalıştıklarını anlamanız gerekir.  Bilgi koruma işlemi hakkında daha fazla bilgi edinmek için [bkz. Microsoft Purview araçları](protect-information.md) .

## <a name="protective-actions-of-dlp-policies"></a>DLP ilkelerinin koruyucu eylemleri

DLP ilkeleri, kullanıcıların bekleyen hassas öğelere, aktarım sırasındaki hassas öğelere veya kullanımdaki hassas öğelere karşı yaptıkları etkinlikleri izleme ve koruyucu eylemler gerçekleştirme yöntemidir. Örneğin, bir kullanıcı hassas bir öğeyi onaylanmamış bir konuma kopyalama veya bir ilkede belirtilen e-posta veya diğer koşullarda tıbbi bilgileri paylaşma gibi yasaklanmış bir eylem gerçekleştirmeye çalıştığında DLP şunları yapabilir:

- kullanıcıya hassas bir öğeyi uygunsuz bir şekilde paylaşmaya çalıştığı konusunda uyaran bir açılır ilke ipucu göster
- paylaşımı engelleyin ve bir ilke ipucu aracılığıyla kullanıcının engellemeyi geçersiz kılıp kullanıcıların gerekçesini yakalamasına izin verin
- geçersiz kılma seçeneği olmadan paylaşımı engelleme
- bekleyen veriler için hassas öğeler kilitlenebilir ve güvenli bir karantina konumuna taşınabilir
- Teams sohbet için hassas bilgiler görüntülenmez

Tüm DLP izlenen etkinlikleri varsayılan olarak [Microsoft 365 Denetim günlüğüne](search-the-audit-log-in-security-and-compliance.md) kaydedilir ve [Etkinlik gezginine](data-classification-activity-explorer.md) yönlendirilir. Kullanıcı bir DLP ilkesinin ölçütlerini karşılayan bir eylem gerçekleştirdiğinde ve uyarıları yapılandırdığınızda [DLP, DLP uyarı yönetimi panosunda uyarılar](dlp-configure-view-alerts-policies.md) sağlar.

## <a name="dlp-lifecycle"></a>DLP yaşam döngüsü

Bir DLP uygulaması genellikle bu ana aşamaları izler.

- [DLP Planı](#plan-for-dlp)
- [DLP için hazırlanma](#prepare-for-dlp)
- [İlkelerinizi üretim ortamında dağıtma](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>DLP Planı

DLP izleme ve koruma, kullanıcıların her gün kullandığı uygulamalarda yereldir. Bu, kullanıcılarınız veri kaybı önleme düşünme ve uygulamalarına alışkın olmasa bile kuruluşunuzun hassas öğelerini riskli etkinliklerden korumaya yardımcı olur. Kuruluşunuz ve kullanıcılarınız veri kaybı önleme uygulamalarına yeni başlıyorsa DLP'nin benimsenmesi, iş süreçlerinizde bir değişiklik yapılmasını gerektirebilir ve kullanıcılarınız için bir kültür değişikliği olacaktır. Ancak, doğru planlama, test ve ayarlama ile DLP ilkeleriniz hassas öğelerinizi korurken olası iş süreci kesintilerini de en aza indirir.

**DLP için teknoloji planlaması**

Teknoloji olarak DLP'nin bekleyen verilerinizi, kullanımdaki verileri ve Microsoft 365 hizmetleri, Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) cihazları, şirket içi dosya paylaşımları ve şirket içi SharePoint genelinde hareket halindeki verileri izleyip koruyabileceğini unutmayın. Farklı konumlar, izlemek ve korumak istediğiniz veri türü ve ilke eşleşmesi gerçekleştiğinde gerçekleştirilecek eylemler için planlama etkileri vardır.

**DLP için iş süreçleri planlaması**

DLP ilkeleri, hassas bilgilerin e-posta yoluyla uygunsuz şekilde paylaşılması gibi yasaklanmış etkinlikleri engelleyebilir. DLP ilkelerinizi planladığınızda hassas öğelerinize dokunan iş süreçlerini tanımlamanız gerekir. İş süreci sahipleri, izin verilmesi gereken uygun kullanıcı davranışlarını ve korunması gereken uygunsuz kullanıcı davranışlarını belirlemenize yardımcı olabilir. İlkelerinizi planlamalı ve test modunda dağıtmalısınız ve daha kısıtlayıcı modlarda uygulamadan önce [etkinlik gezgini](data-classification-activity-explorer.md) aracılığıyla etkilerini değerlendirmelisiniz.

**DLP için kuruluş kültürü planlaması**

Başarılı bir DLP uygulaması, kullanıcılarınızın iyi planlanmış ve ayarlanmış ilkelerde olduğu kadar veri kaybı önleme uygulamalarına da eğitilmesine ve buna alıştırılmalarına bağlıdır. Kullanıcılarınız yoğun bir şekilde dahil olduğundan, onlar için de eğitim planlamayı unutmayın. İlke zorlamayı test modundan daha kısıtlayıcı modlara değiştirmeden önce kullanıcılarınızla farkındalık sağlamak için ilke ipuçlarını stratejik olarak kullanabilirsiniz.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>DLP için hazırlanma

Bekleyen verilere, kullanımdaki verilere ve konumlardaki hareket halindeki verilere DLP ilkeleri uygulayabilirsiniz, örneğin:

- e-postayı Exchange Online
- çevrimiçi siteleri SharePoint
- hesapları OneDrive
- Sohbet ve kanal iletilerini Teams
- Microsoft Cloud App Security
- Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) cihazlar
- Şirket içi depolar
- PowerBI siteleri

Her birinin farklı önkoşulları vardır. Çevrimiçi Exchange gibi bazı konumlardaki hassas öğeler, yalnızca kendileri için geçerli olan bir ilke yapılandırılarak DLP şemsiyesi altına getirilebilir. Şirket içi dosya depoları gibi diğerleri için Azure Information Protection (AIP) tarayıcısının dağıtımı gerekir. Ortamınızı hazırlamanız, taslak ilkeleri kodlamanız ve engelleme eylemlerini etkinleştirmeden önce bunları kapsamlı bir şekilde test etmeniz gerekir.

### <a name="deploy-your-policies-in-production"></a>İlkelerinizi üretim ortamında dağıtma

#### <a name="design-your-policies"></a>İlkelerinizi tasarlama

İlk olarak denetim hedeflerinizi ve bunların ilgili iş yüklerine nasıl uygulanacağını belirleyin. Hedeflerinizi barındıran bir ilke taslağı hazırlar. Tek seferde tek bir iş yüküyle veya tüm iş yükleriyle başlayabilirsiniz. Bunun henüz bir etkisi yoktur.

#### <a name="implement-policy-in-test-mode"></a>İlkeyi test modunda uygulama

Denetimleri test modunda bir DLP ilkesiyle uygulayarak etkilerini değerlendirin. İlkeyi test modundaki tüm iş yüklerine uygulayarak sonuçların tamamını elde edebilirsiniz, ancak gerekirse tek bir iş yüküyle başlayabilirsiniz.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Sonuçları izleme ve ilkede ince ayar yapma

Test modundayken ilkenin sonuçlarını izleyin ve denetim hedeflerinize uygun olacak şekilde ince ayar yaparken geçerli kullanıcı iş akışlarını ve üretkenliğini olumsuz veya yanlışlıkla etkilemediğinizden emin olun. Aşağıda ince ayar yapabileceğiniz bazı örnekler verilmiştir:

- kapsam içinde veya dışında olan konumları ve kişileri/yerleri ayarlama
- bir öğenin ve öğeyle yapılan işlemin ilkeyle eşleşip eşleşmediğini belirlemek için kullanılan koşulları ve özel durumları ayarlama
- hassas bilgi tanımı/tanımları
- eylemler
- kısıtlama düzeyi
- yeni denetimler ekleme
- yeni kişi ekleme
- yeni kısıtlanmış uygulamalar ekleme
- yeni kısıtlanmış siteler ekleme

#### <a name="enable-the-control-and-tune-your-policies"></a>Denetimi etkinleştirme ve ilkelerinizi ayarlama

İlke tüm hedeflerinizi karşıladıktan sonra açın. İlke uygulamasının sonuçlarını izlemeye devam edin ve gerektiğinde ayarlayın. 

> [!NOTE]
> Genel olarak, ilkeler açıldıktan yaklaşık bir saat sonra etkinleşir.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>DLP ilkesi yapılandırmasına genel bakış

DLP ilkelerinizi oluşturma ve yapılandırma konusunda esnekliğe sahipsiniz. Önceden tanımlanmış bir şablondan başlayıp yalnızca birkaç tıklamayla bir ilke oluşturabilir veya sıfırdan kendi ilkenizi tasarlayabilirsiniz. Hangisini seçerseniz seçin, tüm DLP ilkeleri sizden aynı bilgileri gerektirir.

1. **İzlemek istediğiniz öğeyi seçin** - DLP, kullanmaya başlamanıza veya özel bir ilke oluşturmanıza yardımcı olmak için önceden tanımlanmış birçok ilke şablonuyla birlikte gelir.
    - Önceden tanımlanmış bir ilke şablonu: Finansal veriler, Tıbbi veriler ve sağlık verileri, Çeşitli ülkeler ve bölgeler için gizlilik verileri.
    - Kullanılabilir hassas bilgi türlerini, bekletme etiketlerini ve duyarlılık etiketlerini kullanan özel bir ilke.
2. **İzlemek istediğiniz yeri seçin** - DLP'nin hassas bilgiler için izlemesini istediğiniz bir veya daha fazla konum seçersiniz. Şunu izleyebilirsiniz:

Konum | include/exclude by|
|---------|---------|
|e-postayı Exchange| dağıtım grupları|
|siteleri SharePoint |Site |
|hesapları OneDrive |hesaplar veya dağıtım grupları |
|Sohbet ve kanal iletilerini Teams |hesap veya dağıtım grubu |
|Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) cihazlar |kullanıcı veya grup |
|Microsoft Cloud App Security |Örnek |
|Şirket içi depolar| depo dosyası yolu|

3. **Bir ilkenin bir öğeye uygulanması için eşleşmesi gereken koşulları seçin** - Önceden yapılandırılmış koşulları kabul edebilir veya özel koşullar tanımlayabilirsiniz. Bazı örnekler şunlardır:

- öğe, belirli bir bağlamda kullanılan belirli bir tür hassas bilgi içerir. Örneğin, kuruluşunuzun dışındaki alıcıya e-postayla 95 sosyal güvenlik numarası gönderilir.
- öğe belirtilen duyarlılık etiketine sahip
- hassas bilgiler içeren öğe şirket içinde veya dışında paylaşılır

4. **İlke koşulları karşılandığında yapılması gereken eylemi seçin** - Eylemler, etkinliğin gerçekleştiği konuma bağlıdır.  Bazı örnekler şunlardır:

- SharePoint/Exchange/OneDrive: Kuruluş formunuzun dışındaki kişilerin içeriğe erişmesini engelleyin. Kullanıcıya bir ipucu gösterin ve DLP ilkesi tarafından yasaklanan bir eylemde bulunduğunu belirten bir e-posta bildirimi gönderin.
- sohbet ve kanal Teams: Hassas bilgilerin sohbette veya kanalda paylaşılmasını engelleyin
- Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) Cihazlar: Hassas bir öğeyi kaldırılabilir bir USB cihazına kopyalamayı denetleme veya kısıtlama
- Office Uygulamaları: Kullanıcıya riskli bir davranış sergilediğini bildiren ve engelleme veya engellemeye rağmen geçersiz kılmaya izin veren bir açılır pencere gösterin.
- Şirket içi dosya paylaşımları: Dosyayı depolandığı konumdan karantina klasörüne taşıma

> [!NOTE]
> Koşullar ve yapılması gereken eylemler Kural adlı bir nesnede tanımlanır.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft Purview center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Uyumluluk Merkezi'nde bir DLP ilkesi oluşturduktan sonra, bu ilke merkezi bir ilke deposunda depolanır ve ardından aşağıdakiler gibi çeşitli içerik kaynaklarıyla eşitlenir:

- Exchange Online ve oradan Web üzerinde Outlook ve Outlook.
- siteleri OneDrive İş.
- çevrimiçi siteleri SharePoint.
- masaüstü programlarını (Excel, PowerPoint ve Word) Office.
- kanalları ve sohbet iletilerini Microsoft Teams.

İlke doğru konumlara eşitlendikten sonra içeriği değerlendirmeye ve eylemleri zorlamaya başlar.

## <a name="viewing-policy-application-results"></a>İlke uygulaması sonuçlarını görüntüleme

DLP, Microsoft Purview'da izleme, ilke eşleşmeleri ve eylemleri ile kullanıcı etkinliklerine kadar çok miktarda bilgi bildirir. İlkelerinizi ayarlamak ve hassas öğeler üzerinde gerçekleştirilen eylemleri önceliklendirmek için bu bilgileri kullanmanız ve üzerinde işlem yapmanız gerekir. Telemetri önce [Microsoft Purview uyumluluk portalı Denetim Günlükleri'ne](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-portal) gider, işlenir ve farklı raporlama araçlarına gider. Her raporlama aracının farklı bir amacı vardır.

### <a name="dlp-alerts-dashboard"></a>DLP Uyarıları Panosu

DLP hassas bir öğe üzerinde eylem gerçekleştirirken, yapılandırılabilir bir uyarı aracılığıyla bu eylem hakkında bildirim alabilirsiniz. Uyumluluk merkezi, bu uyarıları elemeniz için bir posta kutusuna yığmak yerine [DLP Uyarıları Yönetim Panosu'nda](dlp-configure-view-alerts-policies.md) kullanılabilir hale getirir. Uyarıları yapılandırmak, gözden geçirmek, önceliklendirmek ve DLP Uyarılarının çözünürlüğünü izlemek için DLP Uyarıları panosunu kullanın. burada, Windows 10 cihazlardan ilke eşleşmeleri ve etkinlikleri tarafından oluşturulan uyarılara bir örnek verilmiştir.

> [!div class="mx-imgBorder"]
> ![Uyarı bilgileri.](../media/Alert-info-1.png)

Aynı panoda zengin meta verilerle ilişkili olayın ayrıntılarını da görüntüleyebilirsiniz

> [!div class="mx-imgBorder"]
> ![olay bilgileri.](../media/Event-info-1.png)

### <a name="reports"></a>Raporlar

[DLP raporları](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) zaman içindeki geniş eğilimleri gösterir ve aşağıdakilere ilişkin belirli içgörüler sunar:

- **DLP İlkesi Zaman içinde eşleşir** ve tarih aralığına, konuma, ilkeye veya eyleme göre filtre uygular
- **DLP olay eşleşmeleri** de zaman içindeki eşleşmeleri gösterir, ancak ilke kuralları yerine öğeler üzerinde özetler.
- **DLP hatalı pozitifler ve geçersiz kılmalar** , hatalı pozitiflerin sayısını ve yapılandırıldıysa kullanıcı geçersiz kılmalarının yanı sıra kullanıcı gerekçesini gösterir.

### <a name="dlp-activity-explorer"></a>DLP Etkinlik Gezgini

DLP sayfasındaki Etkinlik gezgini sekmesinde *, Etkinlik filtresi DLPRuleMatch* için önceden ayarlanmıştır. Hassas bilgiler içeren veya hangi etiketlerin değiştirildiği, dosyaların değiştirildiği ve bir kuralla eşleştirildiği gibi etiketler uygulanmış içerikle ilgili etkinliği gözden geçirmek için bu aracı kullanın.

![DLPRuleMatch kapsamlı etkinlik gezgininin ekran görüntüsü.](../media/dlp-activity-explorer.png)

Daha fazla bilgi için bkz. [Etkinlik gezginiyle Kullanmaya başlayın](data-classification-activity-explorer.md)

Microsoft Purview DLP hakkında daha fazla bilgi edinmek için bkz:

- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](endpoint-dlp-learn-about.md)
- [Microsoft Teams'teki varsayılan veri kaybı önleme ilkesi hakkında daha fazla bilgi edinme (önizleme)](dlp-teams-default-policy.md)
- [Şirket içi tarayıcıda veri kaybını önleme hakkında bilgi edinme](dlp-on-premises-scanner-learn.md)
- [Microsoft Uyumluluk Uzantısı hakkında daha fazla bilgi edinme](dlp-chrome-learn-about.md)
- [Veri kaybı önleme Uyarılar panosu hakkında daha fazla bilgi edinme](dlp-alerts-dashboard-learn.md)

Veri gizliliği düzenlemelerine uymak için veri kaybı önlemeyi kullanmayı öğrenmek için bkz. [Microsoft Purview (aka.ms/m365dataprivacy) ile veri gizliliği düzenlemeleri için bilgi koruması dağıtma](../solutions/information-protection-deploy.md)  .

## <a name="licensing-and-subscriptions"></a>Lisanslama ve Abonelikler

DLP'yi destekleyen aboneliklerle ilgili ayrıntılar [için Information Protection lisanslama gereksinimlerine](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) bakın.
