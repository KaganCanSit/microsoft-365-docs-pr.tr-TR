---
title: Veri kaybını önleme hakkında bilgi
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
description: Veri kaybı önleme ilkelerini ve araçlarını kullanarak hassas Microsoft 365 korumayı öğrenin ve DLP yaşam döngüsü boyunca bir tur atabilirsiniz.
ms.openlocfilehash: f64fa30ed0f2eddae03a14451c55f95c9e4249a3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317689"
---
# <a name="learn-about-data-loss-prevention"></a>Veri kaybını önleme hakkında bilgi

Kuruluşların denetimi altında mali veriler, özel veriler, kredi kartı numaraları, sağlık kayıtları veya sosyal güvenlik numaraları gibi hassas bilgiler vardır. Bu hassas verilerin korunmasına ve riskin azaltılmasına yardımcı olmak için, kullanıcılarının bu verileri uygunsuz bir şekilde kullanmaması gereken kullanıcılarla paylaşmasını önlemenin bir yolu gerekir. Bu uygulama, veri kaybını önleme (DLP) olarak adlandırılan uygulamadır.

Daha Microsoft 365, DLP ilkeleri tanımlayarak ve uygulayarak veri kaybı önleme uygularsiniz. DLP ilkesiyle, hassas öğeleri şu öğeler arasında tanımlayabilir, izleyebilir ve otomatik olarak koruyabilirsiniz:

- Microsoft 365, Teams, Exchange, SharePoint ve hizmet OneDrive
- Office, word, Excel ve PowerPoint
- Windows 10, Windows macOS (Catalina 10.15 ve daha yüksek) uç noktaları
- Microsoft dışı bulut uygulamaları
- şirket içi dosya paylaşımları ve şirket içi paylaşımlar SharePoint.

Microsoft 365, yalnızca basit bir metin taramasıyla değil, derin içerik çözümlemesi kullanarak hassas öğeleri algılar. İçerik, birincil veri eşleşmelerinin anahtar sözcüklerle eşleşmesi için, normal ifadelerin de değerlendirilmesi, iç işlev doğrulaması ve birincil veri eşleşmesine yakın olan ikincil veri eşleşmeleri tarafından analiz edilir. DLP'nin ötesinde, DLP ilkelerinize uygun içeriği saptamak için makine öğrenme algoritmalarını ve diğer yöntemleri de kullanır.

## <a name="dlp-is-part-of-the-larger-microsoft-365-compliance-offering"></a>DLP, en büyük Uyumluluk Microsoft 365 bir parçasıdır

Microsoft 365 DLP, hassas öğelerinizi nerede yaşansa veya seyahat ederse koruyun korumaya yardımcı olmak için Microsoft 365 Uyumluluk araçlarından yalnızca biridir. Uyumluluk araçları kümesinde yer alan diğer Microsoft 365 anlamalı, bunların birbiriyle nasıl ilişkili olduğunu ve birlikte daha iyi çalışmalısınız.  Bilgi Microsoft 365 [hakkında daha fazla bilgi](protect-information.md) edinmek için bkz. Uyumluluk araçlarını kullanma.

## <a name="protective-actions-of-dlp-policies"></a>DLP ilkelerinin koruyucu eylemleri

Microsoft 365 DLP ilkeleri, kullanıcıların rest'te hassas öğeler, geçişte hassas öğeler veya kullanımdaki hassas öğeler üzerinde gerçekleştir yaptıkları etkinlikleri izleme ve koruyucu işlemler uygulama yoludur. Örneğin, kullanıcı bir hassas öğeyi başvurul olmayan bir konuma kopyalamak ya da bir ilkeye göre ya da başka koşullar altında tıbbi bilgileri paylaşmak gibi yasaklanan bir eylemde bulunduğu zaman, DLP şunları şunları yerine hazırlar:

- kullanıcıya hassas bir öğeyi uygunsuz bir şekilde paylaşmaya çalıştığı konusunda uyaran bir açılır ilke ipucu göster
- paylaşımı engeller ve bir ilke ipucu aracılığıyla kullanıcının engellemeyi geçersiz k olmasına ve kullanıcıların gerekçesini yakalamasına olanak sağlar
- geçersiz kılma seçeneği olmadan paylaşımı engelleme
- Geri alınan veriler için, hassas öğeler kilitlenir ve güvenli karantina yerine taşınır
- sohbet Teams için hassas bilgiler görüntülenmez

Tüm DLP izlenen etkinlikleri, varsayılan olarak [Microsoft 365 günlüğüne](search-the-audit-log-in-security-and-compliance.md) kaydedilir ve Etkinlik gezginine [yönlendirilebilir](data-classification-activity-explorer.md). Kullanıcı bir DLP ilkesi ölçütlerine uyan bir eylem gerçekleştirir ve uyarılarınız yapılandırıldığında, DLP uyarı yönetim panosunda [uyarılar sağlar](dlp-configure-view-alerts-policies.md).

## <a name="dlp-lifecycle"></a>DLP yaşam döngüsü

Bir DLP uygulaması normalde bu önemli aşamaları izler.

- [DLP için planlama](#plan-for-dlp)
- [DLP için hazırlanma](#prepare-for-dlp)
- [Üretimde ilkelerinizi dağıtma](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>DLP için planlama

Microsoft 365 DLP izleme ve koruma, kullanıcıların her gün kullanan uygulamalarda yereldir. Bu, kullanıcılarınızı veri kaybı önleme düşünme ve uygulamalara izin vermemiş olsa bile, kuruluşlarının hassas öğelerini riskli etkinliklerden korumaya yardımcı olur. Organizasyonunız ve kullanıcılarınız veri kaybı önleme uygulamalarında yeniyse, DLP'nin benimsenmesi iş süreçleriniz için bir değişiklik gerektirmeye neden olabilir ve kullanıcılarınız için bir kültür vardiyası olacak. Ancak, düzgün planlama, test etme ve ayarlama işlemleriyle DLP ilkeleriniz hassas öğelerinizi korur ve bu sırada olası iş süreci kesintiye neden olur.

**DLP için teknoloji planlaması**

DLP'nin bir teknoloji olarak, geri kalan verilerinizi, Microsoft 365 hizmetleri, Windows 10, Windows 11 ve macOS (Catalina 10.15 ve daha yüksek) cihazları, şirket içi dosya paylaşımları ve şirket içi dosya paylaşımları ile şirket içi veri paylaşımlarını izley başka bir SharePoint. Farklı konumlar, izlemek ve korumak istediğiniz verilerin türü ve ilke eşleşmesi olduğunda  alınması gereken eylemleri planlamanın bir anlamı vardır.

**DLP için iş süreçleri planlama**

DLP ilkeleri hassas bilgilerin e-postayla uygunsuz olarak paylaş olması gibi yasaklanan etkinlikleri engelleyebilir. DLP ilkelerinizi planlarken, hassas öğelerinize değen iş işlemlerini tanımlamanız gerekir. İş süreci sahipleri izin verilen uygun kullanıcı davranışlarını ve korunması gereken uygunsuz kullanıcı davranışlarını tanımlamanıza yardımcı olabilir. İlkelerinizi planlamalı, test modunda dağıtmalı ve daha kısıtlayıcı modlarda uygulamadan [](data-classification-activity-explorer.md) önce, etkisini etkinlik gezgini aracılığıyla değerlendirmelisiniz.

**DLP için kuruluş kültürü planlaması**

Başarılı bir DLP uygulaması, iyi planlanmış ve iyi ayarlanmış ilkelerde olduğu gibi, kullanıcılarınızı eğitime almaya ve veri kaybı önleme uygulamalarına da uyum olmaya çok bağlıdır. Kullanıcılarınız yoğun bir şekilde bu işe dahil olduğundan, eğitimleri de planlayın. İlkeyi test modundan daha kısıtlayıcı modlara değiştirmeden önce, kullanıcılarınızı tanımaya yönelik ilke ipuçlarını stratejik olarak kullanabilirsiniz.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for Microsoft 365 data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>DLP için hazırlanma

DLP ilkelerini, kullanımdan kalan verilere ve konumlarda hareket halindeki verilere uygulayabilirsiniz. Örneğin:

- Exchange Online-postayı gönderme
- SharePoint Online siteleri
- OneDrive hesapları
- Teams ve kanal iletilerini gönderme
- Microsoft Cloud App Security
- Windows 10, Windows 11 ve macOS (Catalina 10.15 ve daha yüksek) cihazlar
- Şirket içi depolar
- PowerBI siteleri

Her birinin farklı önkulları vardır. Çevrimiçi çalışma gibi bazı konumlarda Exchange hassas öğeler, yalnızca onlara uygulanan bir ilke yapılandırarak DLP'nin şemsiye altına getirebilirsiniz. Şirket içi dosya depoları gibi diğer kullanıcılarınsa Azure Information Protection (AIP) tarayıcılarının dağıtımı gerekir. Engel eylemleri etkinleştirmeden önce ortamınızı hazırlamanız, taslak ilkeleri kodlamanız ve bunları kapsamlı olarak testniz gerekir.

### <a name="deploy-your-policies-in-production"></a>Üretimde ilkelerinizi dağıtma

#### <a name="design-your-policies"></a>İlkelerinizi tasarlama

Denetim hedeflerinizi tanımlayarak ve bunların ilgili her iş yükü genelinde nasıl uygulanacaklarını tanımlayarak başlayabilirsiniz. Hedeflerinizi kabartmak için bir ilkenin taslağını taslağını taslağını. Bir defada veya tüm iş yükleri genelinde tek bir iş yüküyle çalışmaya başlamanın hiçbir etkisi yoktur.

#### <a name="implement-policy-in-test-mode"></a>Test modunda ilke uygulama

Denetimleri test modunda bir DLP ilkesiyle gerçekleştirerek denetimlerin etkisini değerlendirin. İlkeyi test modunda tüm iş yüklerinin ilkesine uygulayabilir, böylelikle tüm sonuçları elde etmiş olursunuz, ancak gerekirse tek bir iş yüküyle başlayabilirsiniz.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Sonuçları izleme ve ilkenin ince ayarını

Test modundayken, ilkenin sonuçlarını takip edin ve denetim hedeflerinize uygun şekilde ince ayar yaparken, geçerli kullanıcı iş akışlarını ve üretkenliği olumsuzlamamanızı veya istemeden etkilerken, ilkenin sonuçlarını kontrol hedeflerinize uygun olacak şekilde geliştirin. Ince ayar yapmak için bazı örnekleri aşağıda verilmiştir:

- kapsam dışında olan konumları ve yerleri ve yerleri ayarlama
- öğenin ve bu öğeyle ne yapılması olduğunu belirlemek için kullanılan koşulları ve özel durumları ayarlama
- hassas bilgi tanımları
- eylemler
- kısıtlama düzeyi
- yeni denetim ekleme
- yeni kişi ekleme
- yeni kısıtlanmış uygulamalar ekleme
- yeni kısıtlanmış siteler ekleme

#### <a name="enable-the-control-and-tune-your-policies"></a>Denetimi etkinleştirme ve ilkelerinizi ayarlama

İlke tüm hedeflerinize uygunsa, ilkeyi açma. İlke uygulamasının sonuçlarını izlemeye ve gerektiğinde ayarlamaları yapmaya devam edin. 

> [!NOTE]
> Genelde ilkeler, açık olduktan yaklaşık bir saat sonra yürürlüğe girecektir.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>DLP ilkesi yapılandırmasına genel bakış

DLP ilkelerinizi oluşturma ve yapılandırma konusunda esnekliğe sahipsiniz. Önceden tanımlanmış bir şablondan başlayabilir ve yalnızca birkaç tıklamayla bir ilke oluşturabilir veya en baştan başarak kendi ilkenizi tasarlayın. Hangi bilgileri seçerseniz seçin, tüm DLP ilkeleri için aynı bilgiler gerekir.

1. **İzlemek istediğiniz şeyi** seçin. Microsoft 365 veya özel bir ilke oluşturmanıza yardımcı olmak için önceden tanımlanmış birçok ilke şablonuyla birlikte gelir.
    - Önceden tanımlanmış bir ilke şablonu: Finansal veriler, Tıbbi ve sağlık verileri, çeşitli ülkeler ve bölgeler için gizlilik verileri.
    - Kullanılabilir hassas bilgi türlerini, bekletme etiketlerini ve duyarlılık etiketlerini kullanan özel bir ilke.
2. **İzlemek istediğiniz yeri seçin** - DLP'nin hassas bilgileri izlemesi için izlemesi istediğiniz bir veya birden çok konumu seçersiniz. Şunları izleyebilirsiniz:

konum | include/exclude by|
|---------|---------|
|Exchange-posta gönderme| dağıtım grupları|
|SharePoint siteleri |siteler |
|OneDrive hesapları |hesaplar veya dağıtım grupları |
|Teams ve kanal iletilerini gönderme |hesap veya dağıtım grubu |
|Windows 10, Windows 11 ve macOS (Catalina 10.15 ve daha yüksek) cihazlar |kullanıcı veya grup |
|Microsoft Cloud App Security |örnek |
|Şirket içi depolar| depo dosyası yolu|

3. **Öğeye uygulanacak ilke için eşleşmesi** gereken koşulları seçin - Önceden yapılandırılmış koşulları kabul veya özel koşullar tanımlayabilirsiniz. Bazı örnekler:

- Öğe, belirli bir bağlamda kullanılan belirli bir hassas bilgi türü içeriyor. Örneğin, 95 sosyal güvenlik numarası e-postayla kuruluş dışındaki alıcıya gönderilir.
- öğenin belirli bir duyarlılık etiketi var
- Hassas bilgilerle birlikte öğe şirket içinde veya dışında paylaşılır

4. **İlke koşullarına uygun olduğunda gerçekleştirecek** eylemi seçin - Eylemler, etkinliğin gerçekleştir olduğu konuma bağlıdır.  Bazı örnekler:

- SharePoint/Exchange/OneDrive: Kuruluş formunun dışında olan kişilerin içeriğe erişimini engelin. Kullanıcıya bir ipucu göster ve DLP ilkesi tarafından yasaklanan bir eylemde olduklarını haber içeren bir e-posta bildirimi gönderin.
- Teams Sohbet ve Kanal: Sohbette veya kanalda hassas bilgilerin paylaşılmalarını engelleme
- Windows 10, Windows 11 ve macOS (Catalina 10.15 ve daha yüksek) Cihazlar: Hassas öğeyi kaldırılabilir bir USB cihazına kopyalamayı denetleme veya kısıtlama
- Office: Kullanıcıya riskli bir davranışla ilgilerini olduğunu ve engellemeyi veya engellemeyi, ancak geçersiz kılmaya izin vermelerini bildiren bir açılır pencere gösterir.
- Şirket içi dosya paylaşımları: Dosyayı depolandığı yerden karantina klasörüne taşıma

> [!NOTE]
> Eylemler ve koşullar Kural adı verilen bir nesnede tanımlanır.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft 365 Compliance center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Uyumluluk Merkezi'nde bir DLP ilkesi oluşturduklarından sonra, bu ilke merkezi bir ilke deposuna depolanır ve sonra aşağıdakiler gibi çeşitli içerik kaynaklarıyla eşitlenen:

- Exchange Online ve buradan da Web üzerinde Outlook ve Outlook.
- OneDrive İş sitelerini ziyaret edin.
- SharePoint Online siteleri.
- Office programlarını (Excel, PowerPoint Ve Word) kullanın.
- Microsoft Teams ve sohbet iletilerini gönderme.

İlke doğru konumlara eşitledikten sonra, içeriği değerlendirmeye ve eylemleri uygulamaya başlar.

## <a name="viewing-policy-application-results"></a>İlke uygulama sonuçlarını görüntüleme

DLP, izleme, ilke eşleşmeleri, eylemler Microsoft 365 kullanıcı etkinliklerine kadar birçok bilgiyi, bu bilgilere büyük ölçüde raporlar. Hassas öğeler üzerinde  alınan ilkelerinizi ve triyatiğinizi ayarlamak için bu bilgileri tüketmelisiniz ve buna göre eylemde bulundurabilirsiniz. Telemetri, önce Uyumluluk [Microsoft 365 Denetim](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-center) Günlükleri'ne gider, işlenir ve farklı raporlama araçlarına doğru ilerler. Her raporlama aracının farklı bir amacı vardır.

### <a name="dlp-alerts-dashboard"></a>DLP Uyarıları Panosu

DLP hassas bir öğe üzerinde bir eylemde olduğunda, bu eylem hakkında yapılandırılabilir bir uyarıyla size bildirilebilir. Bu uyarıların sizin için bir posta kutusuna yığ satınalması yerine, Uyumluluk Merkezi [bunları DLP Uyarıları Yönetim Panosunda kullanılabilir olarak sağlar](dlp-configure-view-alerts-policies.md). DLP Uyarıları panosunda uyarıları yapılandırma, gözden geçirme, değerlendirme ve DLP Uyarılarının çözümlerini izleme. Burada, cihazlarından ilke eşleşmeleri ve etkinlikleri tarafından oluşturulan uyarılara Windows 10 ve ve almaktadır.

> [!div class="mx-imgBorder"]
> ![Uyarı bilgileri.](../media/Alert-info-1.png)

Ayrıca, aynı panoda zengin meta verilerle ilişkilendirilmiş olayın ayrıntılarını da görüntüleyebilirsiniz

> [!div class="mx-imgBorder"]
> ![olay bilgilerine bakın.](../media/Event-info-1.png)

### <a name="reports"></a>Raporlar

[DLP raporları zaman içinde](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) geniş eğilimler gösterir ve aşağıdakiler hakkında belirli içgörüler sağlar:

- **DLP İlkesi Zamanla eşler** ve tarih aralığına, konuma, ilkeye veya eyleme göre filtre uygulama
- **DLP olayı eşleşmeleri** de zaman içinde eşleşmeleri gösterir, ancak ilke kuralları yerine öğelere özetler.
- **DLP'de hatalı pozitif** sonuçlar ve geçersiz kılmalar, hatalı pozitiflerin sayısını ve yapılandırıldığında, kullanıcı yaslama ile birlikte geçersiz kılmaları gösterir.

### <a name="dlp-activity-explorer"></a>DLP Etkinlik Gezgini

DLP sayfasındaki Etkinlik gezgini sekmesinde, *DLPRuleMatch için etkinlik filtresi önceden ayarlanmıştır*. Hassas bilgiler içeren veya etiketlerin değiştiril, dosyalar değiştirildi ve kuralla eşleşmesi gibi etiketlerin uygulandığı içerikle ilgili etkinliği gözden geçirmek için bu aracı kullanın.

![DLPRuleMatch kapsamındaki etkinlik gezgininin ekran görüntüsü.](../media/dlp-activity-explorer.png)

Daha fazla bilgi için bkz [. Etkinlik gezginiyle çalışmaya başlama](data-classification-activity-explorer.md)

DLP'nin nasıl Microsoft 365 için bkz:

- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [E-postada (önizleme) varsayılan veri Microsoft Teams ilkesi hakkında bilgi](dlp-teams-default-policy.md)
- [Şirket içi Microsoft 365 önleme (önizleme) özelliği hakkında bilgi](dlp-on-premises-scanner-learn.md)
- [Microsoft Uyumluluk Uzantısı (önizleme) hakkında bilgi](dlp-chrome-learn-about.md)
- [Veri kaybı önleme Uyarılar panosu hakkında bilgi](dlp-alerts-dashboard-learn.md)

Veri gizliliği düzenlemeleri ile uyumlu olmak üzere veri kaybı önlemenin nasıl kullanılamayacaklarını öğrenmek için bkz. Gizlilik düzenlemelerine uygun olarak bilgi [Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy.

## <a name="licensing-and-subscriptions"></a>Lisans ve Abonelikler

[DLP'nin destek olduğu abonelikler hakkında ayrıntılı](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) bilgi için Bilgi Koruması lisans gereksinimlerine bakın.
