---
title: Insider risk yönetimiyle çalışmaya başlama
description: Kuruluş içinde insider risk yönetimini yapılandırma.
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: e21d2904ec2afdcd57b69267f99af6a0726dca56
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314637"
---
# <a name="get-started-with-insider-risk-management"></a>Insider risk yönetimiyle çalışmaya başlama

Insider risk yönetimi ilkelerini kullanarak riskli etkinlikleri ve yönetim araçlarını kullanarak, kuruluşta risk uyarıları üzerinde eylem gerçekleştirin. Önkoşulları ayarlamak ve insider risk yönetimi ilkesi yapılandırmak için aşağıdaki adımları tamamlayın.

> [!IMPORTANT]
> En Microsoft 365 insider risk yönetimi çözümü, müşterilerin kullanıcı düzeyinde iç yönetimi kolaylaştırmanıza yardımcı olacak bir kiracı düzeyi seçeneği sunar. Kiracı düzeyi yöneticileri, kuruluş üyelerine bu çözüme erişim sağlamak için izinler kurabilirsiniz ve olası riskli etkinliklerin kullanıcı düzeyinde tanımlanmasını destekleyebilecek ilgili verileri içeri aktaracak şekilde Microsoft 365 uyumluluk merkezi'te veri bağlayıcıları kurabilirsiniz. Müşteriler, bireysel kullanıcının davranışı, karakteri ve performansıyla ilgili olarak, yönetici tarafından hesaplanabilir ve kuruluş içinde başka kullanıcılar tarafından kullanılabilir. Ayrıca müşteriler, bireysel kullanıcının davranışı, karakteri veya performansıyla ilgili olarak yalnızca Insider risk yönetim hizmetinin içgörülerine güvenmekle değil, tamamen farklı bir çalışma yürütmeleri gerektiğini de kabul eder. Tek tek kullanıcı kimlikleriyle ve düzeltme eylemleriyle ilgili yasalar da dahil olmak üzere, Microsoft 365 Insider risk yönetim hizmetini ve ilgili tüm geçerli yasalara uygun özellik veya hizmeti kullanmak müşterilere aittir.

Insider risk ilkelerinin, kuruluşta riski yönetmenize nasıl yardımcı olduğu hakkında daha fazla bilgi için bkz. [Insider risk yönetimi (Insider risk yönetimi Microsoft 365](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonelikler ve lisanslar

Insider risk yönetimine başlamadan önce, yeni aboneliğinizi [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) eklentileri doğrulamanız gerekir. Insider risk yönetimine erişmek ve bu riski kullanmak için, organizasyon aşağıdaki aboneliklerden veya eklentilerden biri gerekir:

- Microsoft 365 E5/A5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/G3 aboneliği + Microsoft 365 E5/A5/G5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/G3 aboneliği + Microsoft 365 E5/A5/G5 Insider Risk Yönetimi eklentisi
- Office 365 E3 + Enterprise Mobil Kullanım ve Güvenlik E3 + Microsoft 365 E5 Uyumluluk eklenti

Insider risk yönetimi ilkelerine dahil olan kullanıcılara yukarıdaki lisanslardan biri atanmalıdır.

> [!IMPORTANT]
> Insider risk yönetimi, şu anda Azure hizmet bağımlılıkları tarafından desteklenen coğrafi bölgelerde ve ülkelerde barındırılan kiracılarda kullanılabilir. Insider risk yönetiminin organizasyonunız için destek olduğunu doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

Mevcut bir Microsoft 365 Kurumsal E5 planınız yoksa ve insider risk yönetimini denemek için mevcut aboneliğinize [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) ekleyebilir veya Microsoft 365 Kurumsal E5 deneme sürümüne kaydolabilirsiniz.[](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="recommended-actions-preview"></a>Önerilen eylemler (önizleme)

Önerilen eylemler, kuruluşa hızlı bir şekilde başlamanıza ve insider risk yönetimi yeteneklerine en iyi şekilde sahip olmak için yardımcı olabilir. Genel Bakış **sayfasında yer** alan önerilen eylemler, ilkeleri yapılandırma ve dağıtma ve ilke eşleşmelerinden uyarı oluşturan kullanıcı eylemleri için soruşturma eylemlerine yönelik işlemlerde size yol bu konuda yol yardımcı olur.

![Insider risk yönetimi önerilen eylemler.](../media/insider-risk-recommended-actions.png)

Insider risk yönetimi yapılandırmanıza başlamanıza veya en üst düzeye çıkarmanıza yardımcı olmak için aşağıdaki öneriler kullanılabilir:

- **Denetimi açma**: Açık olduğunda, kuruluşta kullanıcı ve yönetici etkinliği denetim günlüğüne Microsoft 365 kaydedilir. Insider risk ilkeleri ve çözümlemeleri, risk etkinliklerini algılamak için bu günlüğü kullanır.
- **Kullanıcı risk yönetimi için izinler** al: Insider risk yönetimi özelliklerine erişim düzeyiniz, size atanan rol grubuna bağlıdır. Önerilen eylemlere erişmek ve onları yapılandırmak için, kullanıcıların *Insider Risk Yönetimi* veya *Insider Risk Yönetimi Yöneticileri rol gruplarına atanmaları* gerekir.
- **İlke göstergelerini** seçin: Göstergeler temelde algılamak ve araştırmak istediğiniz kullanıcı etkinlikleridir. Birkaç farklı konumda ve hizmette etkinliği izlemek Microsoft 365 göstergeler seçebilirsiniz.
- **Olası insider risklerini tarama**: Kuruluşta yaşanacak olası insider risklerini bulmak için bir analiz taraması çalıştırın. Sonuçları değerlendirdikten sonra, ayarlamak için önerilen ilkeleri gözden geçirin.
- **Başkalarına izin atama**: Insider risk özelliklerini yönetmekle sorumlu ek ekip üyeleri varsa, bunları uygun rol gruplarına atamanız gerekir.
- **İlk ilkenizi** oluşturma: Olası riskli etkinliklere yönelik uyarılar almak için, algılamak ve araştırmak istediğiniz kullanıcı etkinliklerini tanımlayan, önceden tanımlanmış şablonlara dayalı ilkeler ayarlamelisiniz.
- **Etkinliği not edilen kullanıcıları** gözden geçirme: Kullanıcılar panosu,  uyarı oluşturmak için etkinliğin eşiği karşı edip olmadığına bakılmaksızın, etkinliğine şu anda risk puanları atanmış olan kullanıcıları görüntülemeye olanak sağlar.
- **Uyarıları gözden geçirme**: Kullanıcı için bir tetikleyici olayı gerçekleşirse, ilkeler algılanan etkinliğe risk puanları atamaya başlar. Risk puanı bir ilkenin eşiklerini karşılarsa, bu kullanıcı için puanlandır olunan tüm etkinliklerin ayrıntılı dökümünü içeren bir uyarıyla karşılaşın.
- **Vakayı araştırma**: Olası Insider risklerini tanımlamak için daha fazla araştırma gerektiğinde durumlar uyarılardan el ile oluşturulur. Her olay tek bir kullanıcıya yöneliktir ve kullanıcı için mevcut bir vakaya veya yeni bir vakaya birden çok uyarı eklenebilir.

Bu deneyime dahil edilen önerilen her eylemin dört özniteliği vardır:

- **Eylem**: Önerilen eylemin adı ve açıklaması.
- **Durum**: Önerilen eylemin durumu. Değerler *Başlamadı*, *Sürüyor, Daha* *sonrası için kaydedildi veya* *Tamamlandı*.
- **Gerekli veya isteğe** bağlı: Insider risk yönetimi özelliklerinin beklenen şekilde çalışması için önerilen eylemin gerekli veya isteğe bağlı olması.
- **Tahmini tamamlama süresi**: Önerilen eylemi dakikalar içinde tamamlama tahmin edilen süre.

Insider risk yönetimini yapılandırmaya başlamaya başlama için listeden bir öneri seçin. Önerilen her eylem, gereksinimleri, neler beklemeniz gerekenler ve özelliğin kuruluş içinde yapılandırılma etkisini de içinde olmak üzere, öneriye yönelik gerekli etkinliklerde size yol sunar.   Önerilen her eylem, yapılandırıldığında otomatik olarak tamamlandı olarak işaretlenir veya yapılandırıldığında eylemi tamamlandı olarak el ile seçmeniz gerekir.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>1. Adım (gerekli): Insider risk yönetimi için izinleri etkinleştirme

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdikten sonra, rol grubu izinlerin kuruluş genelinde atanan kullanıcılara uygulamak 30 dakika kadar sürebilir.

Insider risk yönetimi özelliklerini yapılandırmak için kullanılan altı rol grubu vardır. **Insider risk yönetimini** Microsoft 365 uyumluluk merkezi menü seçeneği olarak kullanılabilir yapmak ve bu yapılandırma adımlarını devam etmek için, aşağıdaki rollerden veya rol gruplarından biri size atanmış olması gerekir:

- Azure Active Directory [*Yönetici rolü*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*Uyumluluk Yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolü
- Microsoft 365 uyumluluk merkezi [*Yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- Microsoft 365 uyumluluk merkezi [*Yöneticisi rol*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) grubu
- *Insider Risk Yönetimi* rol grubu
- *Insider Risk Yönetimi Yönetici* rol grubu

Insider risk yönetimi ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı Insider risk yönetimi özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Insider risk yönetimi özelliklerinin farklı alanlarını yönetmek için, belirli rol gruplarına farklı uyumluluk sorumluluklarına sahip kullanıcılar atama seçeneğiniz vardır. Ya da belirlenen yöneticiler, analistler, tahminler ve görüntüleyiciler için tüm kullanıcı hesaplarını Insider Risk Management rol grubuna atamaya karar veabilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun şekilde tek bir rol grubu veya birden çok rol grubu kullanın.

Insider risk yönetimiyle çalışırken, bu rol grubu seçenekleri ve çözüm eylemleri arasında seçim yapabilirsiniz:

|**Eylemler**|**Insider Risk Yönetimi**|**Insider Risk Yönetimi Yöneticisi**|**İçeriden Risk Yönetimi Analistleri**|**İçeriden Risk Yönetimi Araştırmacıları**|**Insider Risk Yönetimi Denetçileri**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| İlkeleri ve ayarları yapılandırma | Evet | Evet | Hayır | Hayır | Hayır |
| Access analiz içgörüleri | Evet | Evet | Evet | Hayır | Hayır |
| Access & araştırma uyarıları | Evet | Hayır | Evet | Evet | Hayır |
| Vakaları & Access araştıracak | Evet | Hayır | Evet | Evet | Hayır |
| Access & Gezgini'ni görüntüde görüntüleme | Evet | Hayır | Hayır | Evet | Hayır |
| Bildirim şablonlarını yapılandırma | Evet | Hayır | Evet | Evet | Hayır |
| Denetim & görüntüleme | Evet | Hayır | Hayır | Hayır | Evet |

>[!IMPORTANT]
>*Insider Risk Yönetimi veya Insider Risk Yönetimi* Yöneticisi rol gruplarında (seçtiğiniz seçen bağlı olarak) her zaman en az bir kullanıcınız olduğundan emin olun; böylelikle, insider risk yönetimi yapılandırmanız belirli kullanıcılar kuruluş içinden ayrılırsa "sıfır yönetici" senaryosuna girilamaz.

Aşağıdaki rollerin üyeleri kullanıcıları Insider risk yönetimi rol gruplarına ata atayar ve *Insider Risk Management Admin* rol grubuna dahil edilenlerle aynı çözüm izinlerine sahip olabilir:

- Azure Active Directory *Yönetici*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft 365 uyumluluk merkezi *Yönetimi*
- Microsoft 365 uyumluluk merkezi *Uyumluluk Yöneticisi*

> [!NOTE]
> Bu rol grupları şu anda etkin bir Privileged Identity Management desteklenmiyor. PIM hakkında daha fazla bilgi edinmek için bkz. [PiM'de Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Insider risk yönetimi rol grubuna kullanıcı ekleme

Kullanıcıları Insider risk yönetimi rol grubuna eklemek için aşağıdaki adımları tamamlayın:

1. Kendi [Microsoft 365 uyumluluk merkezi yönetici](https://compliance.microsoft.com) hesabının kimlik bilgilerini kullanarak oturum Microsoft 365 açın.

2. Güvenlik Uyumluluk Merkezi'nde &amp; İzinler'e **gidin**. Aynı dosyada rolleri görüntülemek ve yönetmek için Office 365.

3. Kullanıcıları eklemek istediğiniz insider risk yönetimi rol grubunu seçin ve sonra da Rol grubunu **düzenle'yi seçin**.

4. Sol **gezinti bölmesinde Üye** seç'i, ardından Düzenle'yi **seçin**.

5. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcıların onay kutusunu seçin.

6. **Ekle'yi** ve ardından **Bitti'yi seçin**.

7. Kullanıcıları **rol** grubuna eklemek için Kaydet'i seçin. Adımları **tamamlamak** için Kapat'ı seçin.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>2. Adım (gerekli): Denetim Microsoft 365 etkinleştirme

Insider risk yönetimi, Microsoft 365 ve çözümleme öngörülerinde tanımlanan kullanıcı içgörüleri ve etkinlikleri için denetim günlüklerini kullanır. Denetim Microsoft 365, kurum içindeki tüm etkinliklerin özetidir ve insider risk yönetimi ilkeleri ilke içgörüleri oluşturmak için bu etkinlikleri kullanabilir.

Bu kuruluşlarda denetim Microsoft 365 varsayılan olarak etkinleştirilir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmıştır. If auditing is disabled for your organization, it might be because another administrator has turned it. Bu adımı tamamlarken denetimi yeniden açmanın bir sorun olduğunu doğrulamanızı öneririz.

Denetimi açma adım adım yönergeler için bkz. [Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açmak için denetim günlüğünün hazır olduğunu ve birkaç saat içinde hazırlık tamamlandıktan sonra arama çalıştırabilirsiniz iletisi görüntülenir. Bu eylemi yalnızca bir kez yapmak gerekir. Denetim günlüğünü kullanma hakkında daha fazla Microsoft 365 için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>3. Adım (isteğe bağlı): Insider risk analizi içgörülerini etkinleştirme ve görüntüleme

Insider risk yönetimi analizi, insider risk ilkelerini yapılandırmadan, organizasyonda olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşa daha yüksek kullanıcı riski olan olası alanları belirlemede yardımcı olabilir ve yapılandırmayı göz önünde bulundurarak göz önünde bulundurarak, insider risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Bu değerlendirme, ek lisanslama veya var olan ilkelerin gelecekteki iyileştirmesi ile ilgili ihtiyaçları belirlemenize de yardımcı olabilir. İncelemelerin rapor olarak gözden geçirilmeden önce analiz tarama sonuçları 48 saat kadar sürebilir. Analiz içgörüleri hakkında daha fazla bilgi edinmek için [Insider risk](insider-risk-management-settings.md#analytics) yönetimi ayarları: Analizler hakkında daha fazla bilgi edinmek ve analizlerin olası insider risklerini daha hızlı şekilde belirlemeye yardımcı olup hızla işlemde size yardımcı olan [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) videosunu inceleyin.

Insider risk Analytics'i etkinleştirmek için *Insider Risk Yönetimi'ne*, *Insider Risk Yönetimi* Yöneticisi'ne veya Microsoft 365 *Genel yönetici rol grubuna üye* olmak gerekir.

Insider risk analizini etkinleştirmek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin**.
2. **Insider risk** yönetimine **genel bakış sekmesinde, kuruluş kartınızda insider** risklerini tara seçeneğinde Taramayı **çalıştır'ı** seçin. Bu eylem, kurum için analiz taramasını kullanır. Ayrıca, **Insider risk** >  ayarlarına giderek ve Kiracınız **kullanıcı etkinliğini tarayın özelliğini** etkinleştirerek olası Insider risklerini tanım kullanarak, organizasyonda taramayı açabilirsiniz.
3. Analiz ayrıntıları **bölmesinde Taramayı** **çalıştır'ı seçerek, kurum için taramayı başlatabilirsiniz**. İncelemelerin rapor olarak gözden geçirilmeden önce analiz tarama sonuçları 48 saat kadar sürebilir.

Çözümleme içgörülerini gözden geçirdikten sonra insider risk ilkelerini seçin ve kuruluşun insider risk azaltma stratejisini en iyi şekilde karşılayacak ilişkili önkoşulları yapılandırın.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>4. Adım (önerilen): İlkeler için önkoşulları yapılandırma

Insider risk yönetimi ilkelerinin çoğu, ilgili etkinlik uyarıları oluşturmak üzere ilke göstergeleri için yapılandırılması gereken önkoşullara sahip olur. Organizasyonunız için yapılandırmayı plan kullandığınız ilkelere bağlı olarak uygun önkoşulları yapılandırma.

### <a name="configure-microsoft-365-hr-connector"></a>İk Microsoft 365 yapılandırma

Insider risk yönetimi, üçüncü taraf risk yönetimi ve insan kaynakları platformlarından içeri aktarılmış kullanıcı ve günlük verilerini içeri aktarmayı destekler. Microsoft 365 İnsan Kaynakları (İk) veri bağlayıcısı, kullanıcı sonlandırma tarihleri, son çalışma tarihleri, performans geliştirme planı bildirimleri, performans gözden geçirme eylemleri ve iş düzeyi değişiklik durumu gibi CSV dosyalarından insan kaynakları verilerini çekmenizi sağlar. Bu veriler Insider risk yönetimi ilkelerde uyarı göstergelerinin kurum içinde yapılandırılması için önemli bir özelliktir. Organizasyonunız için birden fazla İk bağlayıcısı yapılandırıyorsanız, Insider risk yönetimi tüm İk bağlayıcılarından göstergeleri otomatik olarak çeker.

Aşağıdaki Microsoft 365 ilke şablonları kullanırken İk bağlayıcısı gereklidir:

- Göz korkutucu kullanıcıların veri sızıntıları
- Ayrılan kullanıcı veri hırsızlığı
- Genel hasta verileri yanlış kullanımı
- Ayrılan kullanıcılarla güvenlik ilkesi ihlalleri
- Korkutucu kullanıcıların güvenlik ilkesi ihlalleri

Organizasyon için [İk bağlayıcısını](import-hr-data.md) yapılandırmaya yönelik adım adım kılavuz bilgiler için İk verisi içeri aktaracak Microsoft 365 ayarlama makalesine bakın. İk bağlayıcısını yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

### <a name="configure--a-healthcare-specific-data-connector"></a>Sağlıkla ilgili veri bağlayıcısı yapılandırma

Insider risk yönetimi, üçüncü taraflardan mevcut elektronik tıbbi kayıt (EMR) sistemlerinde kullanıcı ve günlük verilerini içeri aktarmayı destekler. Microsoft Healthcare ve Destansı veri bağlayıcıları, uygun olmayan hasta kaydı erişimi, şüpheli hacim etkinlikleri ve düzenleme ve dışarı aktarma etkinlikleri dahil, CSV dosyalarıyla etkinlik verilerini EMR sisteminize çekmenize olanak sağlar. Bu veriler Insider risk yönetimi ilkelerde uyarı göstergelerinin kurum içinde yapılandırılması için önemli bir özelliktir.

Organizasyonunız için birden çok Sağlık veya Destansı bağlayıcısı yapılandırıyorsanız, Insider risk yönetimi tüm Sağlık ve Destan konnektörlerinden etkinlik ve etkinliklerin sinyallerini otomatik olarak destekler.
Aşağıdaki Microsoft 365 ilke şablonları kullanırken Sağlık veya Destansı bağlayıcısı gerekir:

- Genel hasta verileri yanlış kullanımı

Sağlık [verilerini içeri](import-healthcare-data.md) aktaracak bağlayıcı ayarlama veya [Destan EHR](import-epic-data.md) verilerini içeri aktarma için bağlayıcı ayarlama makalesine bakın ve organizasyonu için sağlıkla ilgili bağlayıcıyı adım adım yapılandırma kılavuzuna bakın. Bağlayıcıyı yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Veri Kaybı Önleme (DLP) ilkelerini yapılandırma

Insider risk yönetimi, Yüksek önem düzeyi DLP uyarıları için hassas bilgilerin istenmeyen taraflara bilerek veya yanlışlıkla maruz kalma durumunu belirlemeye yardımcı olmak için DLP ilkelerini kullanmayı destekler. Herhangi bir Veri sızıntı şablonuyla Insider risk yönetimi ilkesi yapılandırdığınız  zaman, bu tür uyarılar için ilkeye belirli bir DLP ilkesi atama seçeneğiniz vardır.

DLP ilkeleri, hassas bilgiler için yüksek öneme sahip DLP uyarıları için Insider risk yönetiminde kullanıcıların risk puanlamasını etkinleştirmesine yardımcı olur ve kuruluşta tam risk yönetimi kapsamı yapılandırmanın önemli bir parçasıdır. Insider risk yönetimi ve DLP ilkesi tümleştirmesi ve planlamada dikkate alınacak noktalar hakkında daha fazla bilgi için [bkz. Insider risk yönetimi ilkeleri](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Şunları tamamlamış olun:
>
>- Beklediğiniz ilke kapsamını ortaya almak için hem DLP hem de Insider risk yönetimi ilkeleri kapsamındaki kullanıcıları an anlar ve düzgün yapılandırmış olursunuz.
>- Bu **şablonlarla kullanılan** Insider risk yönetimi için DLP ilkesinde Olay raporları ayarının Yüksek önem düzeyi uyarıları için yapılandırıldığından  emin olun. Insider risk yönetimi uyarıları, Düşük veya Orta olarak ayarlanmış Olay raporları alanıyla DLP ilkelerinden *oluşturulmaz*. 

Aşağıdaki ilke şablonları kullanırken DLP ilkesi isteğe bağlıdır:

- Genel veri sızıntıları
- Öncelikli kullanıcıların veri sızıntıları

DLP [ilkelerini yapılandırmayla ilgili adım](create-test-tune-dlp-policy.md) adım kılavuz için DLP ilkesi oluşturma, test ve ayarlama makalesine bakın. DLP ilkesi yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

### <a name="configure-priority-user-groups"></a>Öncelik kullanıcı gruplarını yapılandırma

Insider risk yönetimi, kritik konumlara, yüksek veri düzeylerine ve ağ erişimine sahip olan kullanıcılar için kimlik benzersiz risk etkinliklerine yardımcı olacak ilkelere öncelik kullanıcı grupları atama desteği içerir. Öncelik kullanıcı grubu oluşturma ve kullanıcıları gruba atama, bu kullanıcıların sunduğu benzersiz durumlara yardım kapsamı ilkelerine yardımcı olur.

Aşağıdaki ilke şablonları kullanırken bir öncelik kullanıcı grubu gerekir:

- Öncelikli kullanıcıların güvenlik ilkesi ihlalleri
- Öncelikli kullanıcıların veri sızıntıları

Öncelik kullanıcı [grubu oluşturma adım adım kılavuzluk için Insider risk](insider-risk-management-settings.md#priority-user-groups-preview) yönetimi ayarları ile çalışmaya başlama makalesine bakın. Öncelik kullanıcı grubunu yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

### <a name="configure-physical-badging-connector-optional"></a>Fiziksel bağlantı bağlayıcısı yapılandırma (isteğe bağlı)

Insider risk yönetimi, fiziksel denetim ve erişim platformlarından kullanıcı ve günlük verilerini içeri aktarmayı destekler. Fiziksel bağlantı bağlayıcısı, JSON dosyalarından kullanıcı kimlikleri, erişim noktası kimlikleri, erişim zamanı ve tarihleri ve erişim durumu gibi erişim verilerini çekmene olanak sağlar. Bu veriler Insider risk yönetimi ilkelerde uyarı göstergelerinin kurum içinde yapılandırılması için önemli bir özelliktir. Organizasyonunız için birden çok Fiziksel sertifika bağlayıcısı yapılandırıyorsanız, Insider risk yönetimi tüm Fiziksel bağlantı bağlayıcılarından göstergeleri otomatik olarak çeker. Tüm Insider risk ilkesi şablonlarını kullanırken Fiziksel belgeleme bağlayıcısı eklerinden gelen bilgiler diğer insider risk sinyallerini tamamlar.

> [!IMPORTANT]
> Insider risk yönetimi ilkelerinin fiziksel kontrol ve erişim platformlardan etkinlik verileriyle ayrılan ve sonlandırılan kullanıcılarla ilgili sinyal verilerini kullanması ve bu verileri birbiriyle bağlantılı olarak birbiriyle bağlantılı kılabilir olması için, İk bağlayıcısını Microsoft 365 yapılandırmanız gerekir. Microsoft 365 HR bağlayıcısını etkinleştirmeden Fiziksel badging bağlayıcısını etkinleştirirsanız, insider risk yönetimi ilkeleri yalnızca organizasyonlu kullanıcılar için yetkisiz fiziksel erişim için olayları işlemeye devamir.

Takımınız için Fiziksel sertifika [ayarlama bağlayıcısı](import-physical-badging-data.md) yapılandırmayla ilgili adım adım kılavuz bilgileri için, Fiziksel badging verilerini içeri aktaracak şekilde bağlayıcı ayarlama makalesine bakın. Bağlayıcıyı yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Uç Nokta için Microsoft Defender'ı yapılandırma (isteğe bağlı)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) , kurumsal ağların gelişmiş tehditleri engellemesini, algılamasını, araştırmasını ve yanıtlamasını önlemeye yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Organizasyonda güvenlik ihlallerinin daha iyi görünürlüğünü artırmak için, Insider risk yönetimi güvenlik ihlal ilkesi şablonlarından oluşturulan ilkelerde kullanılan etkinlikler için Uç nokta uyarıları için Defender'ı içeri aktararak ve filtresini gerçekleştirebilirsiniz.

Güvenlik ihlal ilkeleri oluşturmanız gerekirse, güvenlik ihlal uyarılarını içeri aktarması için Defender Güvenlik Merkezi'nde Insider risk yönetimi tümleştirmesi için kuruluşta Uç Nokta için Microsoft Defender for Endpoint'ı etkinleştirmeniz ve Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Gereksinimler hakkında daha fazla bilgi için, Uç nokta [için Microsoft Defender'a ilişkin en düşük gereksinimler makalesine](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) bakın.

Insider risk [yönetimi tümleştirmesi için Uç Nokta için Defender'ı](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) yapılandırmayla ilgili adım adım kılavuzlar için, Uç nokta için Defender'daki gelişmiş özellikleri yapılandırma makalesine bakın. Uç Nokta için Microsoft Defender'ı yapılandırdıktan sonra bu yapılandırma adımlarına geri dönebilirsiniz.

## <a name="step-5-required-configure-insider-risk-settings"></a>5. Adım (gerekli): Insider risk ayarlarını yapılandırma

[Insider risk ayarları](insider-risk-management-settings.md) , ilke oluştururken seçtiğiniz şablondan bağımsız olarak tüm Insider risk yönetimi ilkeleri için geçerlidir. Ayarlar, tüm **Insider risk yönetimi** sekmelerinin en üstünde yer alan Insider risk ayarları denetimi kullanılarak yapılandırılır. Bu ayarlar gizliliği, göstergeleri, pencereleri izlemeyi ve akıllı algılamaları kontrol eder.

İlkeyi yapılandırmadan önce aşağıdaki Insider risk ayarlarını tanımlayın:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve herhangi bir sayfanın sağ üst köşesinden **Insider risk** ayarları'ı seçin.
2. Gizlilik **sayfasında** , ilke uyarılarının kullanıcı adlarını görüntülemek için bir gizlilik ayarı seçin.
3. Göstergeler **sayfasında** , tüm insider risk ilkelerine uygulamak istediğiniz uyarı göstergelerini seçin.

    > [!IMPORTANT]
    > İlkeleriniz içinde tanımlanan riskli etkinlikle ilgili uyarılar almak için bir veya birden çok gösterge seçmeniz gerekir. Bu durumda, göstergeler Ayarlar yapılandırılmazsa Insider risk ilkesinde göstergeler seçilemez.

4. İlke **zaman çerçeveleri** sayfasında, bir insider [](insider-risk-management-settings.md#policy-timeframes) risk ilkesine uygun eşleşmeyi tetikleyen kullanıcı için geçerli olacak ilke zaman çerçevelerini seçin.
5. Akıllı **algılamalar sayfasında** , Insider risk ilkeleri için aşağıdaki ayarları yapılandırabilirsiniz:
    - [Dosya türü dışlamaları](insider-risk-management-settings.md#file-type-exclusions)
    - [Alışılmış dışı etkinlikler için puanı artırmak için günlük en az etkinlik sayısı](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Ses düzeyi uyarısı](insider-risk-management-settings.md#alert-volume)
    - [Uç nokta uyarısı durumu için Microsoft Defender](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Etki alanı ayarları](insider-risk-management-settings.md#domains)
6. Uyarıları dışarı **aktar sayfasında**, gerekirse Veri Yönetimi API'lerini kullanarak Insider risk Office 365 bilgilerini dışarı aktarmayı etkinleştirin.
7. Öncelik kullanıcı **grupları sayfasında** , bir öncelik kullanıcı grubu oluşturun ve 3. Adım'da oluşturulmazsa **kullanıcıları ekleyin**.
8. Giriş **Power Automate,** insider risk akışı şablonlarından bir akış yapılandırabilirsiniz veya yeni akış oluşturabilirsiniz. Adım adım [kılavuz için Insider risk yönetimi ayarları ile](insider-risk-management-settings.md#power-automate-flows-preview) çalışmaya başlama makalesine bakın.
9. Öncelik varlıkları **sayfasında, fiziksel** denetim ve fiziksel sertifika bağlayıcısı tarafından alınan erişim platformunu kullanarak öncelik varlıklarını yapılandırabilirsiniz. Adım adım [kılavuz için Insider risk yönetimi ayarları ile](insider-risk-management-settings.md#priority-physical-assets-preview) çalışmaya başlama makalesine bakın.
10. Ekipler **Microsoft Teams**, olay ve Microsoft Teams işbirliği için otomatik olarak ekip oluşturmak üzere Insider risk yönetimiyle tümleştirmeyi etkinleştirin. Adım adım [kılavuz için Insider risk yönetimi ayarları ile](insider-risk-management-settings.md#microsoft-teams-preview) çalışmaya başlama makalesine bakın.
11. **Insider** risk ilkeleriniz için bu ayarları etkinleştirmek için Kaydet'i seçin.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>6. Adım (gerekli): Insider risk yönetimi ilkesi oluşturma

Insider risk yönetimi ilkeleri atanmış kullanıcıları içerir ve uyarılar için hangi tür risk göstergeleri yapılandırıldığından emin olun. Etkinliklerin uyarıları tetiklemesi için, önce bir ilkenin yapılandırılması gerekir. Yeni Insider risk yönetimi ilkeleri oluşturmak için ilke sihirbazını kullanın.

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** İlkeler **sekmesini** seçin.
2. **İlke oluştur'a** seçerek ilke sihirbazını açın.
3. İlke **şablonu sayfasında** , bir ilke kategorisi seçin ve sonra da yeni ilkenin şablonunu seçin. Bu şablonlar algılamak ve araştırmak istediğiniz risk etkinliklerini tanımlayan koşullar ve göstergelerden tasarlanmıştır. Bu ilke şablonunun ihtiyaçlarınıza uyduğunu onaylamak için, şablon önkoşullarını, olayları tetikleyen ve algılanan etkinlikleri gözden geçirebilirsiniz.

    > [!IMPORTANT]
    > Bazı ilke şablonlarının, ilgili uyarıları oluşturmak üzere ilke için yapılandırılması gereken önkoşulları vardır. Geçerli ilke önkoşullarını yapılandırmadıysanız, yukarıdaki **4. Adıma** bakın.

4. Devam etmek **için Sonraki'yi** seçin.
5. Ad **ve açıklama sayfasında** aşağıdaki alanları doldurun:
    - **Ad (gerekli)**: İlke için kolay bir ad girin. İlke oluşturulduktan sonra bu ad değiştirilemez.
    - **Açıklama (isteğe bağlı)**: İlke için bir açıklama girin.

6. Devam etmek **için Sonraki'yi** seçin.
7. Kullanıcılar ve **gruplar sayfasında**, İlkeye  dahil edilecek kullanıcıları veya grupları tanımlamak  veya öncelikli kullanıcı tabanlı bir şablon seçtiyseniz belirli kullanıcıları ve grupları dahil edin'i veya Belirli kullanıcıları ve grupları dahil edin'i seçin; Öncelik kullanıcı **grupları ekle veya düzenle'yi seçin**. **İlkenin risk puanlarını** atamaya başlamak için Tüm kullanıcılar ve grupları dahil etmek üzere, Kuruluşta tüm kullanıcılar ve grupların olaylarını tetikleyen olayları tetikle'yi seçin. Belirli kullanıcılar **ve gruplar dahil öğesini seçerek** , ilkeye hangi kullanıcı ve grupların atan lisanslarını tanımlayabilirsiniz. Konuk kullanıcı hesapları destek desteklemez.
8. Devam etmek **için Sonraki'yi** seçin.
9. **Önceliklendirmek için içerik** sayfasında, öncelikleri belirlemek için kaynakları atabilirsiniz (gerekirse), bu kaynaklar için yüksek önem düzeyi uyarısı oluşturma ihtimali artar. Aşağıdaki seçeneklerden birini seçin:

    - **Site, duyarlılık SharePoint ve/veya hassas bilgi türlerini öncelik içeriği olarak belirtmek istiyorum**. Bu seçeneğin belirleyin, sihirbazda ayrıntılı sayfaları etkinleştirerek bu kanalları yapılandırabilirsiniz.
    - **Şu anda öncelik içeriğini belirtmek istemiyorum (ilke oluşturulduktan sonra bunu yapmaya devam edeceksiniz)**. Bu seçeneğin seçimi, sihirbazda kanal ayrıntı sayfalarını atlar.

10. Devam etmek **için Sonraki'yi** seçin.

11. Bir önceki adımda SharePoint siteleri **,** duyarlılık etiketleri ve/veya hassas bilgi türlerini öncelik içeriği olarak belirtmek istiyorum'i seçtiysanız, *SharePoint* sitelerinin, Hassas bilgi türlerinin ve Duyarlılık etiketlerinin ayrıntı sayfalarını *görüyorsunuz*.  İlkede öncelikleri belirlemek üzere SharePoint, hassas bilgi türlerini ve duyarlılık etiketlerini tanımlamak için bu ayrıntı sayfalarını kullanın.

    - **SharePoint ekle**: SharePoint **sitesi** ekle'yi, SharePoint erişiminiz olan ve önceliklerini belirlemek istediğiniz siteleri seçin. Örneğin, *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Hassas bilgi türü**: **Hassas bilgi türü ekle'yi** seçin ve önceliklerini belirlemek istediğiniz duyarlılık türlerini seçin. Örneğin, *"ABD Banka Hesap Numarası" ve* *"Kredi Kartı Numarası"*.
    - **Duyarlılık etiketleri**: Duyarlılık **etiketi ekle'yi** seçin ve önceliklerini belirlemek istediğiniz etiketleri seçin. Örneğin, *"Gizli"* ve *"Gizli"*.

    >[!NOTE]
    >İlkeyi yapılandıran ve öncelik Share Point sitelerini seçen kullanıcılar SharePoint erişim iznine sahip olduğu siteleri de işaretlerinin seçnayebilirsiniz. SharePoint siteleri geçerli kullanıcı tarafından ilkede seçim için kullanılamıyorsa, gerekli izinlere sahip olan başka bir kullanıcı daha ilkenin sitelerini daha sonra seçerek sitelere erişmesi veya geçerli kullanıcıya gerekli sitelere erişim verilmesi gerekir.

12. Devam etmek **için Sonraki'yi** seçin.
13. Önceliğe sahip kullanıcı şablonlarının Genel veri sızıntıları veya  Veri sızıntıları seçeneklerini seçtiyseniz, özel tetikleyen olaylar ve ilke göstergeleri için  bu ilkenin tetikleyicileri sayfasında seçenekleri görebilirsiniz. Etkinlik puanlama için kullanıcıları ilke kapsamında bir araya getiren olayları tetikleyen bir DLP ilkesi veya göstergeleri seçme seçeneğiniz vardır. Kullanıcı veri kaybı önleme **(DLP)** politikasını tetikleyen bir olay seçeneğiyle eşlerse, bu insider risk yönetimi ilkesi için DLP İlkesinin tetikleyici göstergelerini etkinleştirmek için DLP ilkesi açılan listesinden bir DLP ilkesi seçmeniz gerekir. Kullanıcı, olay **tetikleyen bir exfiltration** etkinliği gerçekleştirir seçeneğini etkinleştirirseniz, olayı tetikleyen ilke için listelenen göstergelerden birini veya birden fazlasını seçmeniz gerekir.
    >[!IMPORTANT]
    >Listelenen bir göstergeyi seçemiyorsanız, bunun nedeni bunun nedeni kuruluş için etkin değilleridir. İlkeyi seçerek atamak için, **Insider risk** >  >  yönetimi veyaPolicy göstergeleri Ayarlar **göstergeleri etkinleştirin**.

    Diğer ilke şablonlarını seçtiyseniz, özel tetikleyici olayları desteklenmiyor. Olayları tetikleyen yerleşik ilke geçerli olur ve ilke özniteliklerini tanımlamadan 23. Adıma devam edersiniz.

14. Devam etmek **için Sonraki'yi** seçin.
15. Öncelik kullanıcı şablonları tarafından Genel veri  sızıntıları veya Veri sızıntıları seçtiysanız ve Kullanıcı bir kullanım etkinliği ve ilişkili göstergeler gerçekleştirirse **, seçtiğiniz** göstergeyi tetikleyen gösterge için özel veya varsayılan eşikler seçebilirsiniz. Tetikleyen **olaylar için Varsayılan eşikleri kullan (Önerilen)** **veya Özel eşikleri kullan'ı seçin**.
16. Devam etmek **için Sonraki'yi** seçin.
17. Tetikleyici **olayları için özel** eşikleri kullan'ı seçtiysanız, 13. Adımda seçtiğiniz her olay göstergesi için uygun düzeyi seçerek istenen etkinlik uyarıları düzeyini üretin.
18. Devam etmek **için Sonraki'yi** seçin.
19. İlke **göstergeleri sayfasında**, **Insider risk**[](insider-risk-management-settings.md#indicators) **ayarlarıIndicators** sayfasında tanımlandığı gibi tanımlandığı  >  göstergeleri görebilirsiniz. İlkeye uygulamak istediğiniz göstergeleri seçin.

    > [!IMPORTANT]
    > Bu sayfada göstergeler seçilenene kadar, tüm ilkeler için etkinleştirmek istediğiniz göstergeleri seçmeniz gerekir. Sihirbazda Göstergeleri **aç düğmesini** kullanabilir veya **Insider risk** >  yönetimi **Ayarlar** >  **Policy göstergeleri sayfasında göstergeleri seçin**.

    En az bir Cihaz göstergesi *seçtiysiniz Office* **risk puanı uygun** şekilde seçin. Risk puanı sadece seçilen göstergeler için geçerlidir.
    Veri hırsızlığı veya Veri sızıntıları  ilke şablonunu seçtiyseniz, ilkeye uygulamak için bir veya birden  çok Sıralı algılama yöntemi ve Kümülatif sızıntı **algılama** yöntemi seçin.

20. Devam etmek **için Sonraki'yi** seçin.
21. Varsayılan veya **özel gösterge eşiklerini** kullanmaya karar verin sayfasında, seçtiğiniz ilke göstergeleri için özel veya varsayılan eşikleri seçin. Tüm **göstergeler için varsayılan eşikleri kullan'ı veya** **seçili ilke göstergeleri için** özel eşikleri belirtin'i seçin. Özel eşikleri belirtin'i seçtiyseniz, her ilke göstergesi için istenen etkinlik uyarı düzeyini oluşturmak üzere uygun düzeyi seçin.
22. Devam etmek **için Sonraki'yi** seçin.
23. Gözden **Geçir sayfasında** , ilke için seçtiğiniz ayarları ve seçimlerinizi önerileri veya uyarıları gözden geçirebilirsiniz. **İlke değerlerini** değiştirmek için Düzenle'yi seçin veya **ilkeyi oluşturmak ve** etkinleştirmek için Gönder'i seçin.

## <a name="next-steps"></a>Sonraki adımlar

İlk Insider risk yönetimi ilkenizi oluşturmak için bu adımları tamamlandıktan sonra, yaklaşık 24 saat sonra etkinlik göstergelerinden uyarı almaya başlarsınız. Bu makalenin 4. Adım'daki veya Yeni bir Insider risk ilkesi oluşturma konusunda yer alan adımları kullanarak [ek ilkeleri gerektiğinde yapılandırabilirsiniz](insider-risk-management-policies.md#create-a-new-policy).

Insider risk uyarılarını ve Uyarılar panosu hakkında daha fazla **bilgi** edinmek için bkz. [Insider risk yönetimi etkinlikleri](insider-risk-management-activities.md#alert-dashboard).
