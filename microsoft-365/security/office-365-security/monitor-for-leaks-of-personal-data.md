---
title: Kişisel verilerin sızıntılarını izleme
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MET150
description: Kişisel veri sızıntılarını izlemek için kullanabileceğiniz üç araç hakkında bilgi edinin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b16e96e85d6ee154912535ecf0bac4ac5ba6fac
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947769"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Kişisel verilerin sızıntılarını izleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Kişisel verilerin kullanımını ve taşınmasını izlemek için kullanılabilecek birçok araç vardır. Bu konuda, iyi çalışan üç araç açıklanmaktadır.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image1.png" alt-text="Kişisel verilerin kullanımını ve taşınmasını izlemeye ilişkin araçlar" lightbox="../../media/Monitor-for-leaks-of-personal-data-image1.png":::

Çizimde:

- SharePoint Online, OneDrive İş ve aktarımdaki e-postada kişisel verileri izlemek için Microsoft Purview veri kaybı önleme raporlarıyla başlayın. Bu raporlar, kişisel verileri izlemek için en yüksek ayrıntı düzeyini sağlar. Ancak bu raporlar Office 365'deki tüm hizmetleri içermez.

- Ardından, hizmetler genelinde etkinliği izlemek için uyarı ilkelerini ve denetim günlüğünü kullanın. Bir olayı araştırmak için sürekli izleme ayarlayın veya denetim günlüğünde arama yapın. Denetim günlüğü hizmetler arasında çalışır: Sway, Power BI, eBulma, Dynamics 365, Power Automate, Microsoft Teams, Yönetici etkinliği, OneDrive İş, SharePoint Online, aktarımdaki postalar ve bekleyen posta kutuları. Skype konuşmalar bekleyen posta kutularına eklenir.

- Son olarak, diğer SaaS sağlayıcılarında hassas verilerle dosyaları izlemek için Microsoft Defender for Cloud Apps kullanın. Yakında hassas bilgi türlerini ve birleşik etiketleri Azure Information Protection ve Bulut için Defender Uygulamaları ile Office kullanabilme özelliği sunulacaktır. Tüm SaaS uygulamalarınıza veya belirli uygulamalarınıza (Box gibi) uygulanan ilkeler ayarlayabilirsiniz. Bulut için Defender Uygulamalar, e-postaya eklenmiş dosyalar da dahil olmak üzere Exchange Online dosyaları bulmaz.

## <a name="data-loss-prevention-reports"></a>Veri kaybı önleme raporları

Veri kaybı önleme (DLP) ilkelerinizi oluşturduktan sonra, bunların istediğiniz gibi çalıştığını ve uyumlu kalmanıza yardımcı olduğunu doğrulamak istersiniz. Office 365'daki DLP raporlarıyla DLP ilkesi eşleşmelerinin, geçersiz kılmaların veya hatalı pozitiflerin sayısını hızla görüntüleyebilir; bunların zaman içinde eğiliminin artıp artmadığını görebilir, raporu farklı şekillerde filtreleyebilir ve grafikteki bir çizgide bir nokta seçerek daha fazla ayrıntı görüntüleyebilirsiniz.

DLP raporlarını kullanarak aşağıdakileri yapabilirsiniz:

- Belirli zaman aralıklarına odaklanın ve ani artışların ve eğilimlerin nedenlerini anlayın.
- Kuruluşunuzun DLP ilkelerini ihlal eden iş süreçlerini keşfedin.
- DLP ilkelerinin iş üzerindeki etkisini anlayın.
- İlkeyi geçersiz kılarak veya hatalı pozitif bir rapor bildirerek bir ilke ipucunu çözümlediklerinde kullanıcılar tarafından gönderilen gerekçeleri görüntüleyin.
- Belirli bir DLP ilkesine yönelik eşleşmeleri göstererek uyumluluğu doğrulayın.
- Ayrıntılar bölmesinde DLP ilkelerinizle eşleşen hassas verilere sahip dosyaların listesini görüntüleyin.

Ayrıca, DLP raporlarınızı test modunda çalıştırırken DLP ilkelerinize ince ayar yapmak için de kullanabilirsiniz.

DLP raporları Microsoft Purview uyumluluk portalındadır. **DLP ilkesi eşleşmelerini**, **DLP olaylarını ve DLP** **hatalı pozitif sonuçları ve geçersiz kılma** raporlarını bulmak için **Raporlar** \> **Kuruluş verileri** bölümüne gidin.

Daha fazla bilgi için bkz. [Veri kaybı önleme raporlarını görüntüleme](../../compliance/view-the-dlp-reports.md).

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image2.png" alt-text="DLP ilkesi eşleşmelerini gösteren rapor" lightbox="../../media/Monitor-for-leaks-of-personal-data-image2.png":::

## <a name="audit-log-and-alert-policies"></a>Denetim günlüğü ve uyarı ilkeleri

Denetim günlüğü Exchange Online, SharePoint Online, OneDrive İş, Azure Active Directory, Microsoft Teams, Power BI, Sway ve diğer hizmetlerden olayları içerir.

Microsoft 365 Defender portalı ve Microsoft Purview uyumluluk portalı, denetim günlüğünü izlemek ve raporlamak için iki yol sağlar:

- Uyarı ilkelerini ayarlama, uyarıları görüntüleme ve eğilimleri izleme—Microsoft 365 Defender portalında veya Microsoft Purview uyumluluk portalında uyarı ilkesini ve uyarı panosu araçlarını kullanın.
- Doğrudan denetim günlüğünde arama yapın: Belirtilen tarih aralığındaki tüm olayları arayın. Ya da, eylemi gerçekleştiren kullanıcı, eylem veya hedef nesne gibi belirli ölçütlere göre sonuçları filtreleyebilirsiniz.

Bilgi uyumluluğu ve güvenlik ekipleri, hizmetler genelinde hem son kullanıcılar hem de yöneticiler tarafından gerçekleştirilen etkinlikleri proaktif olarak gözden geçirmek için bu araçları kullanabilir. Otomatik uyarılar, belirli site koleksiyonlarında belirli etkinlikler gerçekleştiğinde (örneğin, GDPR ile ilgili bilgiler içerdiği bilinen sitelerden içerik paylaşıldığında) e-posta bildirimleri gönderecek şekilde yapılandırılabilir. Bu, bu ekiplerin kurumsal güvenlik ilkelerine uyulmasını sağlamak veya ek eğitim sağlamak için kullanıcılarla birlikte izlemesine olanak tanır.

Bilgi güvenliği ekipleri, şüpheli veri ihlallerini araştırmak ve hem kök nedenini hem de ihlalin kapsamını belirlemek için denetim günlüğünde arama yapabilir. Bu yerleşik özellik, GDPR'nin 33. ve 34. maddesine uyumluluğu kolaylaştırır. Bu, GDPR denetim yetkilisine ve belirli bir zaman aralığında veri ihlalinin veri sahiplerine bildirim sağlanmasını gerektirir. Denetim günlüğü girdileri hizmet içinde yalnızca 90 gün boyunca tutulur; genellikle önerilir ve birçok kuruluş bu günlüklerin daha uzun süre saklanmasını gerektirir.

Microsoft Yönetim Etkinliği API'sini kullanarak Birleşik Denetim Günlüklerine abone olan ve günlük girdilerini gerektiği gibi depolayan ve gelişmiş panolar ve uyarılar sağlayan çözümler sağlanır. Örnek olarak [Microsoft Operations Management Suite (OMS) gösteriliyor](/azure/operations-management-suite/oms-solution-office-365).

Uyarı ilkeleri ve denetim günlüğünde arama yapma hakkında daha fazla bilgi:

- [Microsoft 365 uyarı ilkeleri](../../compliance/alert-policies.md)
- [Office 365'de kullanıcı ve yönetici etkinliği için denetim günlüğünde arama](../../compliance/search-the-audit-log-in-security-and-compliance.md) yapma (giriş)
- [Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md)
- [Denetim günlüğünde arama yapma](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (cmdlet)
- [Denetim günlüğündeki ayrıntılı özellikler](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

Microsoft Defender for Cloud Apps, ağlarınızda kullanılan diğer SaaS uygulamalarını ve bu uygulamalara gönderilen ve bu uygulamalardan gönderilen hassas verileri keşfetmenize yardımcı olur.

Microsoft Defender for Cloud Apps, bulut uygulamalarınız için derin görünürlük, ayrıntılı denetimler ve gelişmiş tehdit koruması sağlayan kapsamlı bir hizmettir. Ağınızdaki 15.000'den fazla bulut uygulamasını tüm cihazlardan tanımlar ve risk puanlaması ile sürekli risk değerlendirmesi ve analiz sağlar. Aracı gerekmez: Bulut kullanımı ve gölge BT için tam görünürlük ve bağlam sağlamak için güvenlik duvarlarınızdan ve proxy'lerinizden bilgi toplanır.

Bulut ortamınızı daha iyi anlamak için Bulut için Defender Uygulamaları araştırma özelliği, tasdikli ve yönetilen uygulamalar için tüm etkinlikler, dosyalar ve hesaplar hakkında derin görünürlük sağlar. Dosya düzeyinde ayrıntılı bilgi edinebilir ve verilerin bulut uygulamalarında nereye ulaştığını keşfedebilirsiniz.

Örnekler için aşağıdaki çizimde GDPR'ye yardımcı olabilecek iki Bulut için Defender Uygulama ilkesi gösterilmektedir.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image3.png" alt-text="Bulut için Defender Uygulamaları ilkeleri" lightbox="../../media/Monitor-for-leaks-of-personal-data-image3.png":::

Seçtiğiniz önceden tanımlanmış PII özniteliğine veya özel ifadeye sahip dosyalar seçtiğiniz SaaS uygulamalarından kuruluş dışında paylaşıldığında ilk ilke uyarır.

İkinci ilke, yönetilmeyen herhangi bir cihaza dosya indirmeyi engeller. Aranacak dosyaların içindeki öznitelikleri ve ilkenin uygulanmasını istediğiniz SaaS uygulamalarını seçersiniz.

Bu öznitelik türleri yakında Bulut için Defender Uygulamalarına sunulacaktır:

- Hassas bilgi türleri
- Microsoft 365 ve Azure Information Protection genelinde birleşik etiketler

### <a name="defender-for-cloud-apps-dashboard"></a>Bulut için Defender Uygulamaları panosu

henüz Bulut için Defender Uygulamaları kullanmaya başlamadıysanız, başlatarak başlayın. Bulut için Defender Uygulamalarına erişmek için: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Bulut için Defender Uygulamaları kullanmaya başlarken veya etiketleri atamadan önce "Azure Information Protection sınıflandırma etiketleri için dosyaları otomatik olarak tara" özelliğini (Genel ayarlarda) etkinleştirdiğinizden emin olun. Kurulumdan sonra, Bulut için Defender Uygulamalar değiştirilene kadar mevcut dosyaları yeniden taramaz.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image4.png" alt-text="Uyarılar hakkındaki bilgileri gösteren pano" lightbox="../../media/Monitor-for-leaks-of-personal-data-image4.png":::

Daha fazla bilgi:

- [Bulut için Defender Uygulamaları Dağıtma](/cloud-app-security/getting-started-with-cloud-app-security)
- [Microsoft Defender for Cloud Apps hakkında daha fazla bilgi](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Microsoft Defender for Cloud Apps ara sunucusunu kullanarak hassas bilgilerin indirilmelerini engelleme](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Kişisel verilerin paylaşımını algılamak için örnek dosya ve etkinlik ilkeleri

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>PII içeren dosyaların paylaşımını algılama — Kredi kartı numarası

Onaylanan bir bulut uygulamasından kredi kartı numarası içeren bir dosya paylaşıldığında uyarır.

|Denetim|Ayarlar|
|---|---|
|İlke türü|Dosya ilkesi|
|İlke şablonu|Şablon yok|
|İlke önem derecesi|Yüksek|
|Kategori|DLP|
|Filtre ayarları|Erişim düzeyi = Genel (İnternet), Genel, Dış <p> Uygulama = \<select apps\> (izlemeyi belirli SaaS uygulamalarıyla sınırlamak istiyorsanız bu ayarı kullanın)|
|Uygulama:|Tüm dosyalar, tüm sahipler|
|İçerik denetimi|Mevcut ifadeyle eşleşen dosyaları içerir: Tüm ülkeler: Finans: Kredi kartı numarası <p> İlgili bağlam gerektirmez: işaretlenmemiş (bu ayar hem anahtar sözcüklerle hem de regex ile eşleşecektir) <p> En az 1 eşleşmesi olan dosyaları içerir <p> İhlalin son 4 karakterinin maskesini kaldırın: işaretli|
|Uyarılar|Eşleşen her dosya için bir uyarı oluşturun: işaretli <p> Günlük uyarı sınırı: 1000 <p> E-posta olarak bir uyarı seçin: işaretli <p> Son: infosec@contoso.com|
|İdare|Microsoft OneDrive İş <p> Özel yap: Dış Kullanıcıları Kaldır'ı işaretleyin <p> Diğer tüm ayarlar: işaretlenmemiş <p> Microsoft Office SharePoint Online <p> Özel yap: Dış Kullanıcıları Kaldır'ı işaretleyin <p> Diğer tüm ayarlar: işaretlenmemiş|

Benzer ilkeler:

- PII içeren Dosyaların paylaşımını algılama - E-posta Adresi
- PII içeren Dosyaların paylaşımını algılama - Pasaport Numarası

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Box veya OneDrive İş'da Müşteri veya İk Verilerini Algılama

Müşteri Verileri veya İk Verileri olarak etiketlenmiş bir dosya OneDrive İş veya Box'a yüklendiğinde uyarır.

Notlar:

- Kutu izleme, API Bağlayıcı SDK'sı kullanılarak bir bağlayıcının yapılandırılmasını gerektirir.
- Bu ilke, şu anda özel önizlemede olan özellikler gerektirir.

|Denetim|Ayarlar|
|---|---|
|İlke türü|Etkinlik ilkesi|
|İlke şablonu|Şablon yok|
|İlke önem derecesi|Yüksek|
|Kategori|Paylaşım Denetimi|
|Üzerinde işlem yapma|Tek etkinlik|
|Filtre ayarları|Etkinlik türü = Upload Dosyası <p> Uygulama = Microsoft OneDrive İş ve Kutu <p> Sınıflandırma Etiketi (şu anda özel önizlemede): Azure Information Protection = Müşteri Verileri, İnsan Kaynakları—Maaş Verileri, İnsan Kaynakları—Çalışan Verileri|
|Uyarılar|Uyarı oluşturma: işaretli <p> Günlük uyarı sınırı: 1000 <p> E-posta olarak bir uyarı seçin: işaretli <p> Son: infosec@contoso.com|
|İdare|Tüm uygulamalar <p> Kullanıcıyı karantinaya alma: check <p> Diğer tüm ayarlar: işaretlenmemiş <p> Office 365 <p> Kullanıcıyı karantinaya alma: check <p> Diğer tüm ayarlar: işaretlenmemiş|

Benzer ilkeler:

- Müşteri verilerinin veya İk Verilerinin büyük indirmelerini algılama— Müşteri verilerini veya İk verilerini içeren çok sayıda dosyanın kısa bir süre içinde tek bir kullanıcı tarafından indirildiği algılandığında uyarı verir.
- Müşteri ve İk Verilerinin Paylaşımını Algılama— Müşteri veya İk Verilerini içeren dosyalar paylaşıldığında uyarı.
