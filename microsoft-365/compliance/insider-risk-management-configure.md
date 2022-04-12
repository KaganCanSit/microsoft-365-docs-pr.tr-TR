---
title: İçeriden risk yönetimini kullanmaya başlama
description: Kuruluşunuzda insider risk yönetimini yapılandırın.
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
ms.openlocfilehash: ca858aaf10c453a3fa333288fd5e44c62d20cb08
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783919"
---
# <a name="get-started-with-insider-risk-management"></a>İçeriden risk yönetimini kullanmaya başlama

Kuruluşunuzdaki risk uyarılarına göre hareket etmek üzere riskli etkinlikleri ve yönetim araçlarını belirlemek için insider risk yönetimi ilkelerini kullanın. Önkoşulları ayarlamak ve bir iç risk yönetimi ilkesi yapılandırmak için aşağıdaki adımları tamamlayın.

> [!IMPORTANT]
> Microsoft 365 insider risk yönetimi çözümü, müşterilerin kullanıcı düzeyinde iç idareyi kolaylaştırmalarına yardımcı olmak için kiracı düzeyinde bir seçenek sağlar. Kiracı düzeyi yöneticileri, kuruluşunuzun üyeleri için bu çözüme erişim sağlamak üzere izinler ayarlayabilir ve riskli olabilecek etkinliklerin kullanıcı düzeyinde tanımlanmasını desteklemek üzere ilgili verileri içeri aktarmak için Microsoft 365 uyumluluk merkezi veri bağlayıcıları ayarlayabilir. Müşteriler bireysel kullanıcının davranışı, karakteri veya performansıyla ilgili içgörülerin yönetici tarafından hesaplanıp kuruluştaki diğer kişilerin kullanımına sunulabileceğini kabul eder. Ayrıca müşteriler, yalnızca iç risk yönetimi hizmetinden alınan içgörülere güvenmek yerine, bireysel kullanıcının çalışmayla ilgili davranışı, karakteri veya performansıyla ilgili kendi tam araştırmalarını yürütmeleri gerektiğini kabul eder. Müşteriler, Microsoft 365 insider risk yönetimi hizmetini ve ilgili tüm özellik veya hizmetleri bireysel kullanıcı belirleme ve düzeltme eylemleriyle ilgili yasalar da dahil olmak üzere tüm geçerli yasalara uygun olarak kullanmakla sorumludur.

Insider risk ilkelerinin kuruluşunuzdaki riski yönetmenize nasıl yardımcı olabileceği hakkında daha fazla bilgi için bkz. [Microsoft 365'de Insider risk yönetimi](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonelikler ve lisanslama

Insider risk yönetimine başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ve tüm eklentileri onaylamanız gerekir. Insider risk yönetimine erişmek ve kullanmak için kuruluşunuzun aşağıdaki aboneliklerden veya eklentilerden birine sahip olması gerekir:

- Microsoft 365 E5/A5/F5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/F3/G3 aboneliği + Microsoft 365 E5/A5/F5/G5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/F3/G3 aboneliği + Microsoft 365 E5/A5/F5/G5 Insider Risk Yönetimi eklentisi
- Office 365 E3 aboneliği + Enterprise Mobility ve Security E3 + Microsoft 365 E5 Uyumluluk eklentisi

Insider risk yönetimi ilkelerine dahil olan kullanıcılara yukarıdaki lisanslardan biri atanmalıdır.

> [!IMPORTANT]
> Insider risk yönetimi şu anda coğrafi bölgelerde barındırılan kiracılarda ve Azure hizmet bağımlılıkları tarafından desteklenen ülkelerde kullanılabilir. Kuruluşunuzda insider risk yönetiminin desteklendiğini doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

Mevcut bir Microsoft 365 Enterprise E5 planınız yoksa ve şirket içi risk yönetimini denemek istiyorsanız, mevcut aboneliğinize [Microsoft 365 ekleyebilir](/office365/admin/try-or-buy-microsoft-365) veya E5 Microsoft 365 Enterprise [deneme sürümüne kaydolabilirsiniz](https://www.microsoft.com/microsoft-365/enterprise).

## <a name="recommended-actions-preview"></a>Önerilen eylemler (önizleme)

Önerilen eylemler, kuruluşunuzun insider risk yönetimiyle hızla çalışmaya başlamanıza yardımcı olabilir. **Genel Bakış** sayfasına eklenen önerilen eylemler, ilkeleri yapılandırma ve dağıtma adımlarında size yol gösterir.

![Insider risk yönetimi önerilen eylemler.](../media/insider-risk-recommended-actions.png)

Insider risk yönetimi yapılandırmanızı kullanmaya başlamanıza veya en üst düzeye çıkarmanıza yardımcı olmak için aşağıdaki öneriler sağlanır:

- **Denetimi açma**: Açık olduğunda, kuruluşunuzdaki kullanıcı ve yönetici etkinliği Microsoft 365 denetim günlüğüne kaydedilir. Insider risk ilkeleri ve analiz taramaları, risk etkinliklerini algılamak için bu günlüğü kullanır.
- **Kullanıcı risk yönetimi izinlerini alma**: Insider risk yönetimi özelliklerine sahip olduğunuz erişim düzeyi, hangi rol grubuna atandığınıza bağlıdır. Önerilen eylemlere erişmek ve bu eylemleri yapılandırmak için kullanıcıların *Insider Risk Management veya Insider Risk Management* *Admins* rol gruplarına atanması gerekir.
- **İlke göstergelerini seçme**: Göstergeler temelde algılamak ve araştırmak istediğiniz kullanıcı etkinlikleridir. Çeşitli Microsoft 365 konum ve hizmetlerde etkinliği izlemek için göstergeleri seçebilirsiniz.
- **Olası insider risklerini tarama**: Kuruluşunuzda ortaya çıkabilecek olası insider risklerini keşfetmek için bir analiz taraması çalıştırın. Sonuçları değerlendirdikten sonra, ayarlamak için önerilen ilkeleri gözden geçirin.
- **Başkalarına izin atama**: İç risk özelliklerini yönetmekten sorumlu olacak ek ekip üyeleri varsa, bunları uygun rol gruplarına atamanız gerekir.
- **İlk ilkenizi oluşturma**: Riskli olabilecek etkinliklerle ilgili uyarılar almak için algılamak ve araştırmak istediğiniz kullanıcı etkinliklerini tanımlayan önceden tanımlanmış şablonları temel alan ilkeler ayarlamanız gerekir.

Bu deneyime dahil edilen önerilen her eylemin dört özniteliği vardır:

- **Eylem**: Önerilen eylemin adı ve açıklaması.
- **Durum**: Önerilen eylemin durumu. Değerler *Başlatılmaz*, *Devam Ediyor*, *Daha sonra için kaydedilir* veya *Tamamlandı* olur.
- **Gerekli veya isteğe bağlı**: Insider risk yönetimi özelliklerinin beklendiği gibi çalışması için önerilen eylemin gerekli mi yoksa isteğe bağlı mı olduğu.
- **Tahmini tamamlanma süresi**: Önerilen eylemin dakika cinsinden tamamlanması için tahmini süre.

Insider risk yönetimini yapılandırmaya başlamak için listeden bir öneri seçin. Önerilen her eylem, gereksinimler, beklenecekler ve özelliğin kuruluşunuzdaki yapılandırmasının etkisi de dahil olmak üzere öneri için gerekli etkinliklerde size yol gösterir.   Önerilen her eylem yapılandırıldığında otomatik olarak tamamlandı olarak işaretlenir veya yapılandırıldığında eylemi tamamlandı olarak el ile seçmeniz gerekir.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>1. Adım (gerekli): Insider risk yönetimi için izinleri etkinleştirme

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdıktan sonra, rol grubu izinlerinin kuruluşunuz genelinde atanan kullanıcılara uygulanması 30 dakika kadar sürebilir.

Insider risk yönetimi özelliklerini yapılandırmak için kullanılan altı rol grubu vardır. **Insider risk yönetimini** Microsoft 365 uyumluluk merkezi menü seçeneği olarak kullanılabilir hale getirmek ve bu yapılandırma adımlarına devam etmek için aşağıdaki rol veya rol gruplarından birine atanmalısınız:

- Genel [*Yönetici*](/azure/active-directory/roles/permissions-reference#global-administrator) rolünü Azure Active Directory
- [*uyumluluk yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolünü Azure Active Directory
- [*Microsoft 365 uyumluluk merkezi Kuruluş Yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- [*uyumluluk yöneticisi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubunu Microsoft 365 uyumluluk merkezi
- *Insider Risk Yönetimi* rol grubu
- *Insider Risk Management Yönetici* rol grubu

Insider risk yönetimi ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı iç risk yönetimi özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Şirket içi risk yönetimi özelliklerinin farklı alanlarını yönetmek için farklı uyumluluk sorumluluklarına sahip kullanıcıları belirli rol gruplarına atama seçeneğiniz vardır. Ya da belirlenen yöneticiler, analistler, araştırmacılar ve izleyiciler için tüm kullanıcı hesaplarını Insider Risk Management rol grubuna atamaya karar vekleyebilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun tek bir rol grubu veya birden çok rol grubu kullanın.

Insider risk yönetimiyle çalışırken bu rol grubu seçenekleri ve çözüm eylemleri arasından seçim yapacaksınız:

|Eylem|Insider Risk Management|Insider Risk Management Yöneticisi|İçeriden Risk Yönetimi Analistleri|İçeriden Risk Yönetimi Araştırmacıları|Insider Risk Management Denetçileri|
|---|---|---|---|---|---|
|İlkeleri ve ayarları yapılandırma|Evet|Evet|Hayır|Hayır|Hayır|
|Analiz içgörülerine erişme|Evet|Evet|Evet|Hayır|Hayır|
|Erişim & uyarıları araştırma|Evet|Hayır|Evet|Evet|Hayır|
|Olayları araştırmak & erişim|Evet|Hayır|Evet|Evet|Hayır|
|access & İçerik Gezgini'ni görüntüleyin|Evet|Hayır|Hayır|Evet|Hayır|
|Bildirim şablonlarını yapılandırma|Evet|Hayır|Evet|Evet|Hayır|
|Denetim günlüklerini görüntüleme & dışarı aktarma|Evet|Hayır|Hayır|Hayır|Evet|

> [!IMPORTANT]
> *Insider Risk Management* veya *Insider Risk Management Yönetici* rol gruplarında (seçtiğiniz seçeneğe bağlı olarak) her zaman en az bir kullanıcınız olduğundan emin olun. Böylece, kuruluşunuzdan belirli kullanıcılar ayrıldığında insider risk yönetimi yapılandırmanız 'sıfır yönetici' senaryosuna girmez.

Aşağıdaki rollerin üyeleri kullanıcıları insider risk yönetimi rol gruplarına atayabilir ve *Insider Risk Management Yönetici* rol grubuna dahil olan çözüm izinlerine sahip olabilir:

- Azure Active Directory *Genel Yöneticisi*
- *Azure Active Directory Uyumluluk Yöneticisi*
- Microsoft 365 uyumluluk merkezi *Kuruluş Yönetimi*
- Microsoft 365 uyumluluk merkezi *Uyumluluk Yöneticisi*

> [!NOTE]
> Bu rol grupları şu anda Privileged Identity Management (PIM) üzerinde desteklenmemektedir. PIM hakkında daha fazla bilgi edinmek için bkz. [Privileged Identity Management'de Azure AD rolleri atama](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Insider risk yönetimi rol grubuna kullanıcı ekleme

Insider risk yönetimi rol grubuna kullanıcı eklemek için aşağıdaki adımları tamamlayın:

1. [Microsoft 365](https://compliance.microsoft.com) kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak Microsoft 365 uyumluluk merkezi oturum açın.

2. Güvenlik &amp; Uyumluluk Merkezi'nde **İzinler'e** gidin. Office 365 rolleri görüntülemek ve yönetmek için bağlantıyı seçin.

3. Kullanıcıları eklemek istediğiniz insider risk yönetimi rol grubunu seçin ve ardından **Rol grubunu düzenle'yi** seçin.

4. Sol gezinti **bölmesinden Üyeleri seç'i** ve ardından **Düzenle'yi** seçin.

5. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.

6. **Ekle'yi** ve ardından **Bitti'yi** seçin.

7. Kullanıcıları rol grubuna eklemek için **Kaydet'i** seçin. Adımları tamamlamak için **Kapat'ı** seçin.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>2. Adım (gerekli): Microsoft 365 denetim günlüğünü etkinleştirme

Insider risk yönetimi, kullanıcı içgörüleri ve ilkeler ve analiz içgörülerinde tanımlanan etkinlikler için Microsoft 365 denetim günlüklerini kullanır. Microsoft 365 denetim günlükleri kuruluşunuzdaki tüm etkinliklerin özetidir ve iç risk yönetimi ilkeleri ilke içgörüleri oluşturmak için bu etkinlikleri kullanabilir.

Denetim, Microsoft 365 kuruluşlar için varsayılan olarak etkindir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmış olabilir. Kuruluşunuzda denetim devre dışı bırakıldıysa, bunun nedeni başka bir yöneticinin kapatması olabilir. Bu adımı tamamlarken denetimi yeniden açmanın uygun olduğunu onaylamanızı öneririz.

Denetimi açmak için adım adım yönergeler için bkz. [Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açtıktan sonra, denetim günlüğünün hazırlandığını ve hazırlık tamamlandıktan birkaç saat sonra bir arama çalıştırabileceğinizi belirten bir ileti görüntülenir. Bu eylemi yalnızca bir kez yapmanız gerekir. Microsoft 365 denetim günlüğünü kullanma hakkında daha fazla bilgi için bkz[. Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>3. Adım (isteğe bağlı): Insider risk analizi içgörülerini etkinleştirme ve görüntüleme

Insider risk yönetimi analizi, herhangi bir insider risk ilkesi yapılandırmadan kuruluşunuzdaki olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşunuzun daha yüksek kullanıcı riski olan olası alanları belirlemesine yardımcı olabilir ve yapılandırmayı düşünebileceğiniz iç risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Bu değerlendirme, mevcut ilkelerin ek lisanslama veya gelecekteki iyileştirme gereksinimlerini belirlemenize de yardımcı olabilir. Analiz tarama sonuçlarının, içgörülerin gözden geçirilebilir raporlar olarak kullanılabilir hale gelmesi 48 saat kadar sürebilir. Analiz içgörüleri hakkında daha fazla bilgi edinmek için [Insider risk yönetimi ayarları: Analiz'e](insider-risk-management-settings.md#analytics) bakın ve insider risklerinin tanımlanmasını hızlandırmaya ve hızla harekete geçmenize nasıl yardımcı olabileceğini anlamak için [Insider Risk Yönetimi Analizi videosunu](https://www.youtube.com/watch?v=5c0P5MCXNXk) inceleyin.

Insider risk Analytics'i etkinleştirmek için *Insider Risk Management, Insider Risk Management* *Yöneticisi* veya Microsoft 365 *Genel yönetici* rol grubunun üyesi olmanız gerekir.

Insider risk analizini etkinleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin.
2. Insider risk yönetimine **Genel Bakış** sekmesinde **, Kuruluşunuzdaki insider risklerini tara** kartında **Tarama çalıştır'ı** seçin. Bu eylem, kuruluşunuz için analiz taramasını açar. Ayrıca **Insider risk** **ayarlarıAnalytics'e** >  giderek ve **olası insider risklerini belirlemek için Kiracınızın kullanıcı etkinliğini tara seçeneğini etkinleştirerek de kuruluşunuzda taramayı** açabilirsiniz.
3. **Analiz ayrıntıları** bölmesinde **Taramayı çalıştır'ı seçerek kuruluşunuz için taramayı başlatın**. Analiz tarama sonuçlarının, içgörülerin gözden geçirilebilir raporlar olarak kullanılabilir hale gelmesi 48 saat kadar sürebilir.

Analiz içgörülerini gözden geçirdikten sonra insider risk ilkelerini seçin ve kuruluşunuzun insider risk azaltma stratejisine en uygun önkoşulları yapılandırın.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>4. Adım (önerilen): İlkeler için önkoşulları yapılandırma

Çoğu insider risk yönetimi ilkesinin, ilgili etkinlik uyarıları oluşturmak için ilke göstergeleri için yapılandırılması gereken önkoşulları vardır. Kuruluşunuz için yapılandırmayı planladığınız ilkelere bağlı olarak uygun önkoşulları yapılandırın.

### <a name="configure-microsoft-365-hr-connector"></a>İk bağlayıcısı Microsoft 365 yapılandırma

Insider risk yönetimi, üçüncü taraf risk yönetimi ve insan kaynakları platformlarından içeri aktarılan kullanıcı ve günlük verilerinin içeri aktarılmasını destekler. Microsoft 365 İnsan Kaynakları (İk) veri bağlayıcısı, csv dosyalarından kullanıcı sonlandırma tarihleri, son çalışma tarihleri, performans geliştirme planı bildirimleri, performans gözden geçirme eylemleri ve iş düzeyi değişiklik durumu gibi insan kaynakları verilerini çekmenizi sağlar. Bu veriler, şirket içi risk yönetimi ilkelerinde uyarı göstergelerini yönlendirmeye yardımcı olur ve kuruluşunuzda tam risk yönetimi kapsamını yapılandırmanın önemli bir parçasıdır. Kuruluşunuz için birden fazla İk bağlayıcısı yapılandırıyorsanız, insider risk yönetimi tüm İk bağlayıcılarından göstergeleri otomatik olarak çeker.

aşağıdaki ilke şablonları kullanılırken Microsoft 365 İk bağlayıcısı gereklidir:

- Bozuk kullanıcılar tarafından veri sızıntıları
- Kullanıcı verilerinin çalınmasından ayrılma
- Genel hasta verilerini kötüye kullanma
- Ayrılan kullanıcıların güvenlik ilkesi ihlalleri
- Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri

kuruluşunuz [için Microsoft 365 İk bağlayıcısını](import-hr-data.md) yapılandırmaya yönelik adım adım yönergeler için İk verilerini içeri aktarmak için bağlayıcı ayarlama makalesine bakın. İk bağlayıcısını yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

### <a name="configure--a-healthcare-specific-data-connector"></a>Sağlık hizmetleriyle ilgili veri bağlayıcısı yapılandırma

Insider risk yönetimi, mevcut elektronik tıbbi kayıt (EMR) sistemlerinde üçüncü taraflardan içeri aktarılan kullanıcı ve günlük verilerinin içeri aktarılmasını destekler. Microsoft Healthcare ve Epic veri bağlayıcıları, uygunsuz hasta kaydı erişimi, şüpheli toplu etkinlikler ve düzenleme ve dışarı aktarma etkinlikleri dahil olmak üzere CSV dosyalarıyla EMR sisteminizden etkinlik verilerini çekmenize olanak sağlar. Bu veriler, şirket içi risk yönetimi ilkelerinde uyarı göstergelerini yönlendirmeye yardımcı olur ve kuruluşunuzda tam risk yönetimi kapsamını yapılandırmanın önemli bir parçasıdır.

Kuruluşunuz için birden fazla Healthcare veya Epic bağlayıcısı yapılandırıyorsanız, insider risk yönetimi tüm Healthcare ve Epic bağlayıcılarından gelen etkinlik ve etkinlik sinyallerini otomatik olarak destekler.
Aşağıdaki ilke şablonları kullanılırken Microsoft 365 Healthcare veya Epic bağlayıcısı gereklidir:

- Genel hasta verilerini kötüye kullanma

Kuruluşunuza yönelik [bir sağlık hizmeti bağlayıcısını](import-healthcare-data.md) yapılandırmaya yönelik adım adım yönergeler için [Sağlık verilerini içeri aktarmak için bağlayıcı ayarlama veya Epic EHR verilerini içeri aktarmak için bağlayıcı ayarlama](import-epic-data.md) makalesine bakın. Bağlayıcıyı yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Veri Kaybı Önleme (DLP) ilkelerini yapılandırma

Insider risk yönetimi, yüksek önem düzeyi DLP uyarıları için hassas bilgilerin istenmeyen taraflara kasıtlı veya yanlışlıkla maruz kalmasını belirlemeye yardımcı olmak için DLP ilkelerinin kullanılmasını destekler. **Veri sızıntısı** şablonlarından herhangi biriyle bir iç risk yönetimi ilkesi yapılandırırken, bu tür uyarılar için ilkeye belirli bir DLP ilkesi atama seçeneğiniz vardır.

DLP ilkeleri, hassas bilgiler için yüksek önem dereceli DLP uyarıları için kullanıcıların şirket içi risk yönetiminde risk puanlama özelliğini etkinleştirmelerine yardımcı olur ve kuruluşunuzda tam risk yönetimi kapsamını yapılandırmanın önemli bir parçasıdır. Insider risk yönetimi ve DLP ilkesi tümleştirmesi ve planlama konuları hakkında daha fazla bilgi için bkz. [Insider risk yönetimi ilkeleri](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Aşağıdakileri tamamladığınızdan emin olun:
>
> - Beklediğiniz ilke kapsamını oluşturmak için hem DLP hem de iç risk yönetimi ilkelerindeki kapsam içi kullanıcıları anlar ve uygun şekilde yapılandırabilirsiniz.
> - Bu şablonlarla kullanılan iç risk yönetimi için DLP ilkesindeki **Olay raporları** ayarının *Yüksek* önem düzeyi uyarıları için yapılandırıldığından emin olun. Insider risk yönetimi uyarıları, **Olay raporları** alanı *Düşük* veya *Orta* olarak ayarlanmış DLP ilkelerinden oluşturulmaz.

Aşağıdaki ilke şablonları kullanılırken bir DLP ilkesi isteğe bağlıdır:

- Genel veri sızıntıları
- Öncelikli kullanıcılara göre veri sızıntıları

Kuruluşunuz için DLP ilkelerini yapılandırmaya yönelik adım adım yönergeler için [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md) makalesine bakın. Bir DLP ilkesi yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

### <a name="configure-priority-user-groups"></a>Öncelikli kullanıcı gruplarını yapılandırma

Insider risk yönetimi, kritik konumları, yüksek veri düzeyleri ve ağ erişimi veya geçmişteki risk davranışı geçmişi olan kullanıcılar için benzersiz risk etkinliklerini tanımlamaya yardımcı olmak için ilkelere öncelikli kullanıcı grupları atama desteği içerir. Öncelikli bir kullanıcı grubu oluşturma ve kullanıcıları grup yardım kapsamı ilkelerine bu kullanıcıların sunduğu benzersiz koşullara atama.

Aşağıdaki ilke şablonları kullanılırken öncelikli bir kullanıcı grubu gereklidir:

- Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri
- Öncelikli kullanıcılara göre veri sızıntıları

Öncelikli bir kullanıcı grubu oluşturmak için adım adım yönergeler için [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#priority-user-groups-preview) makalesine bakın. Öncelikli bir kullanıcı grubu yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

### <a name="configure-physical-badging-connector-optional"></a>Fiziksel badging bağlayıcısı yapılandırma (isteğe bağlı)

Insider risk yönetimi, fiziksel denetim ve erişim platformlarından kullanıcı ve günlük verilerini içeri aktarmayı destekler. Fiziksel bağlantı bağlayıcısı, kullanıcı kimlikleri, erişim noktası kimlikleri, erişim saati ve tarihleri ve erişim durumu gibi JSON dosyalarından erişim verilerini çekmenizi sağlar. Bu veriler, şirket içi risk yönetimi ilkelerinde uyarı göstergelerini yönlendirmeye yardımcı olur ve kuruluşunuzda tam risk yönetimi kapsamını yapılandırmanın önemli bir parçasıdır. Kuruluşunuz için birden fazla Fiziksel badging bağlayıcısı yapılandırırsanız, insider risk yönetimi tüm Fiziksel bağlantı bağlayıcılarından göstergeleri otomatik olarak çeker. Fiziksel badging bağlayıcısından alınan bilgiler, tüm insider risk ilkesi şablonları kullanılırken diğer iç risk sinyallerini destekler.

> [!IMPORTANT]
> Şirket içi risk yönetimi ilkelerinin, ayrılan ve sonlandırılan kullanıcılarla ilgili sinyal verilerini fiziksel denetim ve erişim platformlarınızdan gelen olay verileriyle ilişkilendirmesi için, Microsoft 365 İk bağlayıcısını da yapılandırmanız gerekir. Microsoft 365 İk bağlayıcısını etkinleştirmeden Fiziksel bağlantı bağlayıcısını etkinleştirirseniz, insider risk yönetimi ilkeleri yalnızca kuruluşunuzdaki kullanıcılar için yetkisiz fiziksel erişim olaylarını işler.

Kuruluşunuz için Fiziksel badging bağlayıcısını yapılandırmaya yönelik adım adım yönergeler için Bkz. [Fiziksel badging verilerini içeri aktarmak](import-physical-badging-data.md) için bağlayıcı ayarlama makalesi. Bağlayıcıyı yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Pertahanan Microsoft untuk Titik Akhir yapılandırma (isteğe bağlı)

[Pertahanan Microsoft untuk Titik Akhir](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), kurumsal ağların gelişmiş tehditleri engellemesine, algılamasına, araştırmasına ve yanıtlamasına yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Kuruluşunuzdaki güvenlik ihlallerini daha iyi görmek için, insider risk yönetimi güvenlik ihlali ilke şablonlarından oluşturulan ilkelerde kullanılan etkinlikler için Uç Nokta için Defender uyarılarını içeri aktarabilir ve filtreleyebilirsiniz.

Güvenlik ihlali ilkeleri oluşturursanız, kuruluşunuzda Pertahanan Microsoft untuk Titik Akhir yapılandırmanız ve güvenlik ihlali uyarılarını içeri aktarmak için Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Gereksinimler hakkında daha fazla bilgi [için Pertahanan Microsoft untuk Titik Akhir için en düşük gereksinimler](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) makalesine bakın.

[Uç Nokta için Defender'ı](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) insider risk yönetimi tümleştirmesi için yapılandırmaya yönelik adım adım yönergeler için Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma makalesine bakın. Pertahanan Microsoft untuk Titik Akhir yapılandırdıktan sonra bu yapılandırma adımlarına dönün.

## <a name="step-5-required-configure-insider-risk-settings"></a>5. Adım (gerekli): Insider risk ayarlarını yapılandırma

[Insider risk ayarları](insider-risk-management-settings.md) , ilke oluştururken seçtiğiniz şablondan bağımsız olarak tüm insider risk yönetimi ilkeleri için geçerlidir. Ayarlar, tüm **insider risk** yönetimi sekmelerinin en üstünde bulunan Insider risk ayarları denetimi kullanılarak yapılandırılır. Bu ayarlar gizliliği, göstergeleri, izleme pencerelerini ve akıllı algılamaları denetler.

İlkeyi yapılandırmadan önce aşağıdaki insider risk ayarlarını tanımlayın:

1. [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve herhangi bir sayfanın sağ üst köşesinden **Insider risk ayarları'nı** seçin.
2. **Gizlilik** sayfasında, ilke uyarıları için kullanıcı adlarını görüntülemek için bir gizlilik ayarı seçin.
3. **Göstergeler** sayfasında, tüm insider risk ilkelerine uygulamak istediğiniz uyarı göstergelerini seçin.

    > [!IMPORTANT]
    > İlkelerinizde tanımlanan riskli etkinliklere yönelik uyarılar almak için bir veya daha fazla gösterge seçmelisiniz. Göstergeler Ayarlar yapılandırılmamışsa, iç risk ilkelerinde göstergeler seçilemez.

4. **İlke zaman çerçeveleri** sayfasında, bir kullanıcı bir iç risk ilkesi için eşleşme tetiklediğinde etkin olacak [ilke zaman çerçevelerini](insider-risk-management-settings.md#policy-timeframes) seçin.
5. **Akıllı algılamalar** sayfasında, insider risk ilkeleri için aşağıdaki ayarları yapılandırın:
    - [Dosya türü dışlamaları](insider-risk-management-settings.md#file-type-exclusions)
    - [Olağan dışı etkinlikler için puanı artırmak için en az günlük etkinlik sayısı](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Uyarı ses düzeyi](insider-risk-management-settings.md#alert-volume)
    - [Uyarı durumunu Pertahanan Microsoft untuk Titik Akhir](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Etki alanı ayarları](insider-risk-management-settings.md#domains)
6. **Uyarıları dışarı aktar** sayfasında, gerekirse Office 365 Yönetimi API'lerini kullanarak insider risk uyarısı bilgilerinin dışarı aktarılabilmesini sağlayın.
7. **Öncelik kullanıcı grupları** sayfasında, bir öncelik kullanıcı grubu oluşturun ve **3. Adımda** oluşturulmadıysa kullanıcıları ekleyin.
8. **Power Automate akışları** sayfasında, insider risk akışı şablonlarından bir akış yapılandırın veya yeni bir akış oluşturun. Adım adım yönergeler için [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#power-automate-flows-preview) makalesine bakın.
9. **Öncelik varlıkları sayfasında**, fiziksel denetiminizdeki verileri kullanmak için öncelik varlıklarını yapılandırın ve Fiziksel bağlantı bağlayıcısı tarafından içeri aktarılan erişim platformuna erişin. Adım adım yönergeler için [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#priority-physical-assets-preview) makalesine bakın.
10. **Microsoft Teams** sayfasında, servis talebi veya kullanıcı işbirliği için otomatik olarak bir ekip oluşturmak için insider risk yönetimiyle Microsoft Teams tümleştirmeyi etkinleştirin. Adım adım yönergeler için [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#microsoft-teams-preview) makalesine bakın.
11. Insider risk ilkelerinizde bu ayarları etkinleştirmek için **Kaydet'i** seçin.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>6. Adım (gerekli): Insider risk yönetimi ilkesi oluşturma

Insider risk yönetimi ilkeleri atanmış kullanıcıları içerir ve uyarılar için hangi tür risk göstergelerinin yapılandırıldığını tanımlar. Etkinliklerin uyarıları tetikleyebilmesi için önce bir ilkenin yapılandırılması gerekir. Yeni insider risk yönetimi ilkeleri oluşturmak için ilke sihirbazını kullanın.

1. [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke sihirbazını açmak için İlke **oluştur'u** seçin.
3. **İlke şablonu** sayfasında bir ilke kategorisi seçin ve ardından yeni ilkenin şablonunu seçin. Bu şablonlar, algılamak ve araştırmak istediğiniz risk etkinliklerini tanımlayan koşullar ve göstergelerden oluşur. Bu ilke şablonunun gereksinimlerinize uygun olduğunu onaylamak için şablon önkoşullarını, tetikleyici olayları ve algılanan etkinlikleri gözden geçirin.

    > [!IMPORTANT]
    > Bazı ilke şablonlarının, ilgili uyarıları oluşturmak üzere ilke için yapılandırılması gereken önkoşulları vardır. Geçerli ilke önkoşullarını yapılandırmadıysanız yukarıdaki **4. adıma** bakın.

4. Devam etmek için **İleri'yi** seçin.
5. **Ad ve açıklama** sayfasında aşağıdaki alanları doldurun:
    - **Ad (gerekli):** İlke için kolay bir ad girin. İlke oluşturulduktan sonra bu ad değiştirilemez.
    - **Açıklama (isteğe bağlı)**: İlke için bir açıklama girin.

6. Devam etmek için **İleri'yi** seçin.
7. **Kullanıcılar ve gruplar** sayfasında, İlkeye hangi kullanıcıların veya grupların dahil olduğunu tanımlamak için **Tüm kullanıcıları ve grupları ekle'yi** veya **Belirli kullanıcıları ve grupları ekle'yi** seçin ya da öncelikli kullanıcılara dayalı bir şablon seçtiyseniz; **Öncelikli kullanıcı grupları ekle veya düzenle'yi** seçin. **Tüm kullanıcıları ve grupları dahil et'i** seçtiğinizde, ilke için risk puanları atamaya başlamak için kuruluşunuzdaki tüm kullanıcılar ve gruplar için tetikleme olayları aranacaktır. **Belirli kullanıcıları ve grupları dahil et'i** seçtiğinizde ilkeye atanacak kullanıcıları ve grupları tanımlayabilirsiniz. Konuk kullanıcı hesapları desteklenmez.
8. Devam etmek için **İleri'yi** seçin.
9. **Öncelik sırasına alınacak içerik** sayfasında, öncelik sırasına göre kaynakları atayabilir (gerekirse) bu kaynaklar için yüksek önem derecesi uyarısı oluşturma olasılığını artırabilirsiniz. Aşağıdaki seçeneklerden birini seçin:

    - **Öncelik içeriği olarak SharePoint siteleri, duyarlılık etiketlerini ve/veya hassas bilgi türlerini belirtmek istiyorum**. Bu seçeneğin seçilmesi, sihirbazdaki ayrıntılı sayfaların bu kanalları yapılandırmasına olanak tanır.
    - **Şu anda öncelik içeriğini belirtmek istemiyorum (ilke oluşturulduktan sonra bunu yapabilirsiniz)**. Bu seçeneğin seçilmesi, sihirbazdaki kanal ayrıntı sayfalarını atlar.

10. Devam etmek için **İleri'yi** seçin.

11. Önceki adımda **öncelik içeriği olarak SharePoint siteleri, duyarlılık etiketlerini ve/veya hassas bilgi türlerini belirtmek istiyorum** seçeneğini belirlediyseniz, *SharePoint sitelerin* ayrıntı sayfalarını, *Hassas bilgi türlerini* ve *Duyarlılık etiketlerini* görürsünüz. İlkeye öncelik vermek üzere SharePoint, hassas bilgi türlerini ve duyarlılık etiketlerini tanımlamak için bu ayrıntı sayfalarını kullanın.

    - **siteleri SharePoint**: **SharePoint site ekle'yi** seçin ve erişiminiz olan ve önceliklendirmek istediğiniz SharePoint siteleri seçin. Örneğin, *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Hassas bilgi türü**: **Hassas bilgi türü ekle'yi** seçin ve önceliklendirmek istediğiniz duyarlılık türlerini seçin. Örneğin, *"ABD Banka Hesap Numarası"* ve *"Kredi Kartı Numarası"*.
    - **Duyarlılık etiketleri**: **Duyarlılık etiketi ekle'yi** seçin ve önceliklendirmek istediğiniz etiketleri seçin. Örneğin, *"Gizli"* ve *"Gizli"*.

    > [!NOTE]
    > İlkeyi yapılandıran ve öncelikli Paylaşım Noktası sitelerini seçen kullanıcılar, erişim iznine sahip oldukları siteleri SharePoint seçebilir. İlkede geçerli kullanıcı tarafından SharePoint siteler seçilemiyorsa, gerekli izinlere sahip başka bir kullanıcı ilkenin sitelerini daha sonra seçebilir veya geçerli kullanıcıya gerekli sitelere erişim izni verilmelidir.

12. Devam etmek için **İleri'yi** seçin.
13. *Öncelikli kullanıcılara göre* *Genel veri sızıntıları* veya Veri sızıntıları şablonlarını seçtiyseniz, özel tetikleyici olayları ve ilke göstergeleri için Bu ilkenin **tetikleyicileri** sayfasında seçenekleri görürsünüz. Etkinlik puanlaması için ilkeye atanan kullanıcıları kapsama alanlara getiren olayları tetikleme için bir DLP ilkesi veya gösterge seçme seçeneğiniz vardır. **Kullanıcı bir veri kaybı önleme (DLP) ilkesi tetikleme olayıyla eşleşir** seçeneğini belirlerseniz, bu iç risk yönetimi ilkesi için DLP İlkesi için tetikleyici göstergelerini etkinleştirmek üzere DLP ilkesi açılan listesinden bir DLP ilkesi seçmeniz gerekir. **Kullanıcı bir sızdırma etkinliği tetikleme olayı gerçekleştirir** seçeneğini belirlerseniz, ilke tetikleyici olayı için listelenen göstergelerden birini veya daha fazlasını seçmeniz gerekir.

    > [!IMPORTANT]
    > Listelenen bir göstergeyi seçemiyorsanız bunun nedeni, bunların kuruluşunuz için etkinleştirilmemiş olmasıdır. İlkeyi seçip atamaya uygun hale getirmek için **Insider risk yönetimi** >  **Ayarlar** >  **İlke göstergeleri'nde göstergeleri** etkinleştirin.

    Diğer ilke şablonlarını seçtiyseniz özel tetikleyici olayları desteklenmez. Olayları tetikleyen yerleşik ilke uygulanır ve ilke öznitelikleri tanımlamadan 23. Adıma devam edersiniz.

14. Devam etmek için **İleri'yi** seçin.
15. Öncelikli kullanıcılara göre *Genel veri sızıntıları* veya *Veri sızıntıları şablonlarını* seçtiyseniz ve **Kullanıcı bir sızdırma etkinliği ve ilişkili göstergeler gerçekleştirir'i** seçtiyseniz, seçtiğiniz olayları tetikleyen gösterge için özel veya varsayılan eşikleri seçebilirsiniz. Tetikleyici olaylar için **Varsayılan eşikleri kullan (Önerilen)** veya **Özel eşikleri kullan'ı** seçin.
16. Devam etmek için **İleri'yi** seçin.
17. **Tetikleyici olaylar için özel eşikleri kullan'ı** seçtiyseniz, 13. Adımda seçtiğiniz her tetikleyici olay göstergesi için istenen etkinlik uyarısı düzeyini oluşturmak için uygun düzeyi seçin.
18. Devam etmek için **İleri'yi** seçin.
19. **İlke göstergeleri** [](insider-risk-management-settings.md#indicators) sayfasında **, Insider risk** **ayarlarıIndicators** >  sayfasında kullanılabilir olarak tanımladığınız göstergeleri görürsünüz. İlkeye uygulamak istediğiniz göstergeleri seçin.

    > [!IMPORTANT]
    > Bu sayfadaki göstergeler seçilemiyorsa, tüm ilkeler için etkinleştirmek istediğiniz göstergeleri seçmeniz gerekir. Sihirbazdaki **Göstergeleri aç** düğmesini kullanabilir veya **Insider risk yönetimi** >  **Ayarlar** >  **İlke göstergeleri sayfasında göstergeleri** seçebilirsiniz.

    En az bir *Office* veya *Cihaz* göstergesi seçtiyseniz **, risk puanı güçlendiricilerini** uygun şekilde seçin. Risk puanı güçlendiricileri yalnızca seçili göstergeler için geçerlidir.
    *Veri hırsızlığı* veya *Veri sızıntıları* ilke şablonu seçtiyseniz, ilkeye uygulanacak bir veya daha fazla **Sıra algılama** yöntemi ve **bir Kümülatif sızdırma algılama** yöntemi seçin.

20. Devam etmek için **İleri'yi** seçin.
21. **Varsayılan veya özel gösterge eşiklerini kullanmaya karar ver** sayfasında, seçtiğiniz ilke göstergeleri için özel veya varsayılan eşikleri seçin. **Tüm göstergeler için varsayılan eşikleri kullan'ı** veya Seçili ilke göstergeleri için **özel eşikler belirtin'i** seçin. Özel eşikleri belirtin'i seçtiyseniz, her ilke göstergesi için istenen etkinlik uyarı düzeyini oluşturmak için uygun düzeyi seçin.
22. Devam etmek için **İleri'yi** seçin.
23. **Gözden Geçir** sayfasında, ilke için seçtiğiniz ayarları ve seçimleriniz için önerileri veya uyarıları gözden geçirin. İlke değerlerinden herhangi birini değiştirmek için **Düzenle'yi** veya ilkeyi oluşturup etkinleştirmek için **Gönder'i** seçin.

## <a name="next-steps"></a>Sonraki adımlar

İlk insider risk yönetimi ilkenizi oluşturmak için bu adımları tamamladıktan sonra, yaklaşık 24 saat sonra etkinlik göstergelerinden uyarılar almaya başlayacaksınız. Bu makalenin 4. Adımındaki yönergeleri veya [Yeni bir insider risk ilkesi oluşturma](insider-risk-management-policies.md#create-a-new-policy) bölümündeki adımları kullanarak ek ilkeleri gerektiği gibi yapılandırın.

Insider risk uyarılarını ve **Uyarılar panosunu** araştırma hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi etkinlikleri](insider-risk-management-activities.md#alert-dashboard).
