---
title: Uyumlulukla ilgili Microsoft 365.
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Uyumluluk merkezine yeni çözümler eklemek, geri bildirimleriniz temel alınarak mevcut özellikleri güncelleştirmek veya yeni ve güncelleştirilmiş belgeler çıkarmak olabilir; Microsoft 365 sürekli değişen uyumluluk ortamını takip içinde kalmanıza yardımcı olur. Bu ay neler olduğunu takipte bulun.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 15a97fc419bc6e4264f3c3cd0bbe389b79e5c2f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326979"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Uyumlulukla ilgili Microsoft 365.

[Microsoft 365 uyumluluk merkezi'a](microsoft-365-compliance-center.md) yeni çözümler eklemek, Microsoft 365 uyumluluk merkezi geri bildirimleriniz temel alınarak mevcut özellikleri güncelleştirmek veya yeni ve güncelleştirilmiş belgeler çıkarmak olabilir; Microsoft 365, sürekli değişen uyumluluk ortamını takip içinde kalmanıza yardımcı olur. Uyumluluk uyumluluğu ile ilgili bugün hangi Microsoft 365 bakın.

> [!NOTE]
> Bazı uyumluluk özellikleri müşterilerimize farklı hızlarda sunulmaktadır. Henüz bir özelliği görmüyorsanız kendinizi hedefli sürüme [eklemeyi deneyin](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Diğer yönetim merkezlerinde neler olduğunu merak ediyor musunuz? Şu makalelere göz at:
>
> - [2010'daki Microsoft 365 yönetim merkezi](/office365/admin/whats-new-in-preview)
> - [Yönetim merkezinde SharePoint.](/sharepoint/what-s-new-in-admin-center)
> - [Microsoft 365 Defender'daki Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Ayrıca, [Microsoft 365,](https://www.microsoft.com/microsoft-365/roadmap) piyasaya Microsoft 365, geliştirme aşamasında olan, iptal edilen veya daha önce yayımlanan özellikler hakkında bilgi edinmek için Yol Haritası'Microsoft 365 ziyaret edin.

## <a name="february-2022"></a>Şubat 2022

### <a name="ediscovery"></a>eKbulma

- [Advanced eDiscovery'ta](advanced-ediscovery-communications-library.md) özel iş iletişim şablonlarını yönetme - eBulma yöneticileri artık kuruluşta herhangi bir durumda kullanılmaktadır ve özel Advanced eDiscovery şablonları oluşturabilir.
- [Advanced eDiscovery'te](advanced-ediscovery-issuing-officers.md) sorumluları yönetme - eBulma yöneticileri, kuruluşta herhangi bir dava halinde özel kişi iletişimlerine atanabilir, Advanced eDiscovery sorumluların listesini ekleyebilir.

### <a name="information-governance-and-records-management"></a>Bilgi yönetimi ve kayıt yönetimi

- [Bekletme ilkeleri ve](retention.md#adaptive-or-static-policy-scopes-for-retention) bekletme etiketi ilkeleri için uyarlanabilir kapsamlar artık genel olarak kullanılabilir (GA). Uyarlanabilir bir [](retention-settings.md#to-configure-an-adaptive-scope) kapsam yapılandırma yönergeleri, artık SharePoint site kapsamları hakkında daha fazla bilgi içerir: Özel site özelliklerini kullanmak için blog gönderisi başvurusu ve gelişmiş sorgu oluşturucusıyla belirli site türlerini eklemek veya dışarıda tutmak için SiteTemplate site özelliğini kullanma.
- [Bilgi Yönetimi](retention.md#policy-lookup) çözümünde ilke araması artık genel olarak kullanılabilir (GA.
- Kullanıcıların [Get-PnPTenant ve Set-PnPTenant'tan](/powershell/module/sharepoint-pnp/get-pnptenant) AllowFilesWithKeepLabelToDeletedSPO ve AllowFilesWithKeepLabelToBeDeletedODB kullanarak SharePoint ve OneDrive'daki etiketli öğeleri silmesine olanak sağlayan kayıt yönetimi ayarının PowerShell []( /powershell/module/sharepoint-pnp/set-pnptenant)alternatifi.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Yeni kılavuz Office bilgisayarlar için Azure Information Protection (AIP) birleşik etiketleme istemcisini kullanıyorsanız, Office uygulamaları için [AIP eklentisinde MIP](sensitivity-labels-aip.md) yerleşik etiketlemeyi neden Windows gerekir. Bu sayfada, bu uygulamaların yeni özel önizlemesi hakkında Office vardır.
- Otomatik etiketleme [ilkeleri için yeni ayarlar](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - E-posta için her zaman eşlenmiş bir duyarlılık etiketi uygulama ve kuruluş dışından alınan e-postaya şifreleme uygulama için ek ayarlar.
  - Belirli örnekler (kullanıcılar, gruplar, siteler) için dışlamalar, yeni Dışarıda Bırakıldı seçeneği dahil edilenler için varsayılan olarak belirtilmiş olduğunda **desteklemektedir**. 
- Şimdi önizlemede: En düşük sürümlere sahipken mobil cihazlar ([](sensitivity-labels-coauthoring.md)iOS ve Android) birlikte yazma desteği sağlar ve bu önizlemeyi kabul edin.
- Varsayılan paylaşım bağlantı türünü ayarlama desteği belge ve çalışma sayfalarındaki tek tek SharePoint OneDrive. Daha fazla bilgi için, aynı adres ve sitelerde site ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak üzere duyarlılık SharePoint [OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams yönetim merkezi artık kapsayıcı etiketlerini (Gruplar grubu siteleri kapsamındaki duyarlılık etiketleri) & destekliyor.

## <a name="january-2022"></a>Ocak 2022

### <a name="microsoft-information-governance"></a>Microsoft Bilgi Yönetimi

- [Microsoft 365'ta](manage-information-governance.md) yapılandırılan çözümlerle ilgili bilgileri daha kolay bulmanıza yardımcı olmak için, önemli ölçüde düzeltilmiş ve yeniden yapılandırılmıştır: Microsoft 365 uyumluluk merkezi Veri Bağlayıcıları, Bilgi Yönetimi ve Kayıt Yönetimi. Bu düzeltmenin bir parçası olarak, belgeler bilgi yönetimi ve kayıt yönetimi arasındaki saklama senaryolarına daha net bir fark sağlar.
- [Yeniden yapılandırmayı desteklemek için](information-governance.md) yeni, bilgi idaresi hakkında bilgi edinebilirsiniz.
- [Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md) - yeni, "Bekletmeye başlarken" yerine geçmektedir. Bu makale, bekletme de içinde olmak üzere tüm bilgi yönetimi özelliklerine ilişkin başlarken adımlarını içerir.
- [Bekletme ilkeleriniz için özel durumlar için bekletme](create-retention-labels-information-governance.md) etiketleri oluşturun; kayıt yönetimi yerine bilgi yönetimi için bekletme etiketlerinin kullanımına yönelik yeni, tanımlanan senaryo.
- [Yeni olan ve yeniden yapılandırılmayı](archive-mailboxes.md) destekleyecek arşiv posta kutuları hakkında bilgi edinmek için daha önce Arşiv posta kutularını etkinleştirme'de yer alan kavramsal bilgileri içerir.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Gizlilik yönetimi artık Microsoft Priva](/privacy/priva/priva-overview) oldu; ürün ve çözümlerini yeniden satın almak için güncelleştirilir: Priva Gizlilik Risk Yönetimi ve Priva Konu Hakları İstekleri.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Yeni [MIP rol grupları ve rolleri için destek, şu anda](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels) önizlemede.
- Otomatik [etiketleme ilkeleri](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) için yeni izleme özellikleri.
- Şimdi de yayınlanacak: Geçerli Kanal'daki (Önizleme) mevcut belgeler için varsayılan etiket ve doğru metinler için Web üzerinde Office.
- 2202+ sürümüyle Temmuz Semi-Annual Enterprise Kanalı için duyurululdu: Yeni sürüm için birlikte yazma ve Outlook.

## <a name="december-2021"></a>Aralık 2021

### <a name="compliance-and-service-assurance"></a>Uyumluluk ve hizmet güvencesi

- [Azure, Dynamics 365 ve Windows GDPR](/compliance/regulatory/gdpr-breach-notification) kapsamında ihlal bildirimi - müşterilerin güvenlik ve gizlilik bildirimlerini almak için Bulut için Defender gibi bir ödeme hizmeti kullanmaları gerek olmadığını açık bir şekilde açıklamak üzere güncelleştirilir

### <a name="ediscovery"></a>eKbulma

- [Advanced eDiscovery iş akışını güncelleştirme - Microsoft Teams'de](teams-workflow-in-advanced-ediscovery.md#reference-guide) içerik yönetimine yardımcı olacak yeni indirilebilir hızlı başvuru kılavuzuyla Teams iş Advanced eDiscovery

### <a name="information-governance"></a>Bilgi yönetimi

- [Uyumluluk merkezinde arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) - arşiv posta kutuları için yeni tanılama aracı hakkında bölüm eklendi
- [Ağ karşıya yükleme kullanarak kuruluş PST dosyalarını diğer kuruluşlara](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) aktarın - PST içeri Microsoft 365 artık AzCopy v10'i destekliyor
- [Etkin olmayan posta kutusunu geri yükleme](restore-an-inactive-mailbox.md) - öncelikle etkin olmayan posta kutusunun LegacyExchangeDN'ini hedef posta kutusuna ekleyerek etkin olmayan posta kutusunu geri yüklemek için düzeltilmiş yordam

### <a name="information-protection"></a>Bilgi koruması

- [MIP çözümünü dağıtma](information-protection-solution.md) - MIP'yi (MIP) dağıtmak için ön simgeli bir yol haritası arayan Microsoft Bilgi Koruması adım adım kılavuz

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi

- Bekletme [ilkelerinin etkililiği ne kadar sürer? ile ilgili yeni kılavuz](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Yeni kiracı ayarları ayarlandı: Kayıt olarak işaretlenmiş ve kilitli olan SharePoint etiketli öğelerin düzenlenmesini ve kullanıcıların kayıt olarak işaretlenmiş öğelerin kilidini açmasını önlemeye yönelik kayıt yönetimi ayarı

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Zorunlu etiketleme ve varsayılan etiket Power BI artık genel kullanıma açıktır (GA)

## <a name="november-2021"></a>Kasım 2021

### <a name="compliance-manager"></a>Uyumluluk Yöneticisi

Yeni içerik güncelleştirmeleri [Microsoft Uyumluluk Yöneticisi'nin tüm yeniliklerine bakabilirsiniz](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Cihaz Ekleme

Cihaz ekleme için aşağıdaki makaleler eklenmiştir:

- [MacOS cihazlarını mobil cihazlara Microsoft 365 genel bakış (önizleme)](device-onboarding-macos-overview.md)
- [Intune (önizleme) kullanarak MacOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma](device-onboarding-offboarding-macos-intune.md)
- [Uç nokta müşterileri için Microsoft Defender'ı kullanarak MacOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkararak kullanma (önizleme)](device-onboarding-offboarding-macos-intune-mde.md)
- [JAMF uyumluluk çözümleri kullanarak macOS cihazlarını Microsoft 365 kullanma ve çıkararak uyumluluk çözümlerine (Pro)](device-onboarding-offboarding-macos-jamfpro.md)
- [Uç nokta müşterileri için Microsoft Defender 'da JAMF Pro kullanarak MacOS cihazlarını ekleme ve çıkararak Uyumluluk çözümlerine ekleme (önizleme)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eKbulma

- [Yeni büyük/küçük harf biçimini Advanced eDiscovery](advanced-ediscovery-new-case-format.md) kullanılabilirlik durumuna çıkar ve "büyük harf biçimi" olarak yeniden adlandırılmıştır

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- Rolling out: Whether labeled items in SharePoint and OneDrive kullanıcılar tarafından silinebilir. Daha önce, içeriği korumak üzere yapılandırılan ve öğeleri kayıt olarak işaretlemeen bekletme etiketleri, kullanıcıların bu eyleme izin verilmiyorken SharePoint'te etiketli içeriği silmeden OneDrive. Daha fazla bilgi için bkz[. SharePoint ve OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Hassas Bilgi Türleri

Aşağıdaki yeni makaleler eklendi:

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md)
- [Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma](sit-get-started-exact-data-match-export-data.md)
- [Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma](sit-get-started-exact-data-match-create-schema.md)
- [Hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı tablosuna karma sağlama ve yükleme](sit-get-started-exact-data-match-hash-upload.md)
- [Hassas bilgi türü/kural paketiyle tam olarak eşleşmesi için veri oluşturma](sit-get-started-exact-data-match-create-rule-package.md)
- [Hassas bilgi türüyle tam olarak eşan bir veri sınaması](sit-get-started-exact-data-match-test.md)
- [Tam veri eşleşme şemanızı yönetme](sit-use-exact-data-manage-schema.md)
- [Hassas bilgi kaynağı tablo dosyanızı yenileme](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri
- [Azure Purview etiketlerinin kapsam adı artık](/azure/purview/create-sensitivity-label) "Şemalı veri varlıkları" olarak gösterilmektedir.

## <a name="october-2021"></a>Ekim 2021

### <a name="app-governance"></a>Uygulama yönetimi

- [Bulut Uygulamaları için Defender'ın uygulama yönetimi eklentileri genel kullanılabilirlik için yayınlandı](/cloud-app-security/app-governance-manage-app-governance). Uygulama yönetimi belgeleri, Bulut Uygulamaları için Defender belgelerine katılmaya taşındı.

### <a name="compliance--service-assurance"></a>Uyumluluk & hizmet güvencesi

- [Hizmet güvencesi](/compliance) - Sertifikalar ve uygulanabilirlik ifadeleri için üç aylık olarak içerik güncelleştirmelerini gözden geçirme) Veri merkezi varlık yönetimi
  - Veri merkezi mimarisi ve altyapısı
  - Veri merkezi iş sürekliliği ve olağanüstü durum kurtarma
  - Veri merkezi koruma korumaları
  - Veri merkezi fiziksel erişim güvenliği
  - Microsoft 365 SDL uyumluluk programı
  - Microsoft 365 mühendisi erişim denetimi
  - MS Cloud için risk değerlendirmesi kılavuzu

### <a name="data-loss-prevention"></a>Veri Kaybını Önleme

- [MacOS desteği ve gelişmiş sınıflandırma için](endpoint-dlp-learn-about.md) Veri Kaybı Önleme'nin güncelleştirilmiş olduğunu öğrenin; tüm desteklenen dosya türlerinde etkinliği denetlenmek üzere özel bir DLP ilkesi oluşturmak üzere güncelleştirilmiştir.
- [Gelişmiş sınıflandırma için Microsoft 365 MacOS desteği](endpoint-dlp-getting-started.md) ve gelişmiş sınıflandırma için uç nokta veri kaybı önleme güncelleştirildi.
- [MacOS desteği ve gelişmiş sınıflandırma için](endpoint-dlp-using.md) Uç nokta veri kaybı önleme özellikleri güncelleştirildi.
- [Veri Kaybı Önleme ilke ipuçları başvurusu](dlp-policy-tips-reference.md) macOS desteği ve gelişmiş sınıflandırma için güncelleştirildi.
- [macOS cihazlarını MacOS desteği Microsoft 365 sınıflandırma için güncelleştirilmiş](device-onboarding-macos-overview.md) yeni (önizleme) bölüme alın.
- Ekleme cihazları için aşağıdaki yeni sayfalar eklendi:
  - [Intune (önizleme) kullanarak MacOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma](device-onboarding-offboarding-macos-intune.md)
  - [Uç nokta müşterileri için Microsoft Defender'ı kullanarak MacOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkararak kullanma (önizleme)](device-onboarding-offboarding-macos-intune-mde.md)
  - [JAMF uyumluluk çözümleri kullanarak macOS cihazlarını Microsoft 365 kullanma ve çıkararak uyumluluk çözümlerine (Pro)](device-onboarding-offboarding-macos-jamfpro.md)
  - [Uç nokta müşterileri için Microsoft Defender 'da JAMF Pro kullanarak MacOS cihazlarını ekleme ve çıkararak Uyumluluk çözümlerine ekleme (önizleme)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eKbulma

- [bulut](advanced-ediscovery-cloud-attachments.md) eklerini Advanced eDiscovery'te toplayın Bulut eklerinin en son sürümünü toplamanın yanı sıra bir e-posta iletisinde veya Teams sohbet konuşmalarında paylaşılan sürümü de toplayabilirsiniz; bulut eklerine otomatik olarak bekletme etiketi uygulama özelliğiyle paylaşılan sürümün toplanması mümkün olur.
- SharePoint sitesinde [Advanced eDiscovery depolanan](advanced-ediscovery-historical-versions.md) tüm belgelerin sürümlerini arama için dizine alan yeni işlevlerle geçmiş sürümleri ayarlayın. Bu, bir koleksiyon sorgusuyla eşleşmeye sahip içerik içeren belge sürümlerinin arama sonuçlarında döndürül olduğu anlamına gelir.

### <a name="encryption"></a>Şifreleme

- [Bire bir arama aramalarında 4'e uç şifreleme Microsoft Teams kullanın (Genel önizleme)](/microsoftteams/teams-end-to-end-encryption) Genel önizleme için yeni içerik.

### <a name="information-governance"></a>Bilgi yönetimi

- [DestanSı EHR](import-epic-data.md) denetim verileri yeni bağlayıcısı içeri aktaracak bir bağlayıcı ayarlamak, Insider risk yönetimi için yeni genel hasta verisi yanlış kullanım senaryosunu desteklemek için, Bilgileri Elektronik Sağlık kayıtları sisteminden içeri aktarmanız için bir bağlayıcı ayarlayın.
- [Sağlık EHR](import-healthcare-data.md) denetim verilerini içeri aktarmayı sağlayan bir bağlayıcı ayarlayın yeni bağlayıcı, insider risk yönetimi için yeni genel hasta verilerini yanlış kullanım senaryosunu desteklemek için bir elektronik sağlık kayıt sisteminden verileri içeri aktarmanıza olanak sağlar.

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- [Uyarlanabilir ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) bekletme ilkeleri ve bekletme etiketi ilkeleri için önizlemede yayınlanır.
- Artık otomatik olarak [duyarlılık etiketine dayalı bir bekletme etiketi uygulayabilirsiniz](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- Dosya Planı'nın yeni bir içeri [aktarma işlemi var](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [Bekletme ilkeleri ve bekletme etiketi ilkeleri](retention-settings.md) için genel ayarlar: Uyarlanabilir kapsamları ve hem bekletme ilkeleri hem de bekletme etiketi ilkeleriyle ilgili diğer ayarları yapılandırma hakkında ayrıntılı bilgi için yeni makale.

### <a name="sensitive-information-types"></a>Hassas Bilgi Türleri

- [Adlandırılmış varlıklar için yeni içerikler hakkında bilgi edinmek (](named-entities-learn.md) önizleme)
- [Adlandırılmış varlıkları kullanırken, veri kaybı önleme ilkeleri (önizleme)](named-entities-use.md) yeni içeriğinde adlandırılmış varlıkları kullanın.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- [Varsayılan etiketler ve varsayılan](mip-easy-trials.md) ilkeler uygun müşterilere sunulmaktadır.

## <a name="september-2021"></a>Eylül 2021

### <a name="app-governance"></a>Uygulama yönetimi

- [Akıcı uygulama yönetiminin başlama bilgileri, değiştirilmiş](app-governance-get-started.md) bir iş akışına sahiptir ve genel önizleme için yeni bağlantılar ekler
- [Yeni algılama uyarıları tanımı eklendi](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) (güncelleştirildi; koleksiyon uyarıları için yeni tanım eklendi)

### <a name="auditing"></a>Denetim

- [Bir kuruluşta denetim durumunda yapılan](turn-audit-log-search-on-or-off.md) değişikliklerin kendileri tarafından denetlenma hakkında yeni bir bölüm eklenmiştir ve denetimi açma veya kapatma; bu, denetimin açık veya kapalı olduğu durumda denetim kayıtlarının günlüğe kaydedileceğini anlamına gelir; bu denetim kayıtlarını Exchange denetim günlüğünde arama

### <a name="communication-compliance"></a>İletişim uyumluluğu

- [SIEM çözümleriyle iletişim uyumluluğu tümleştirmesi için SIEM](communication-compliance-siem.md) çözümleriyle iletişim uyumluluğu kılavuzu)

### <a name="compliance-offerings"></a>Uyumluluk teklifleri

- [Multi-Tier Cloud Security (MTCS)](/compliance/regulatory/offering-mtcs-singapore) Dynamics 365 kapsamı için Singapur güncelleştirmeleri için standart
- [Ödeme Kartı Sektörü (PCI)](/compliance/regulatory/offering-pci-dss) SharePoint Online kapsamı için Veri Güvenliği Standart (DSS) güncelleştirmeleri
- [ABD Bölüm 508](/compliance/regulatory/offering-section-508-vpats) yeni istemci yazılım kılavuzu
- [Web İçeriği Erişilebilirlik Yönergeleri](/compliance/regulatory/offering-wcag-2-1) yeni istemci yazılımı kılavuzu

### <a name="compliance--service-assurance"></a>Uyumluluk & hizmet güvencesi

- [Hizmet güvencesi](/compliance/) , uygunluk sertifikaları ve deyimleri için içerik güncelleştirmelerini üç aylık olarak gözden geçirme
  - Veri yataklı cihaz cihazı cihazıyla ilgili bilgi
  - DDOS saldırıları

### <a name="data-connectors"></a>Veri bağlayıcıları

- [](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) CellTrust ve 17a-4 LLC'den Microsoft 365 veri bağlayıcılarında üçüncü taraf verileri arşivleme, artık ABD Kamu GCC kuruluşlarında kullanılabilir
- [YouTube verilerini arşivlemek için bir bağlayıcı ayarlamak,](archive-youtube-data.md) genel önizlemede bu özellik için yeni kılavuz sağlar.

### <a name="ediscovery"></a>eKbulma

- İçerik arama, Çekirdek eK bulma ve Advanced eDiscovery'ta arama sorguları oluşturmanın yeni bir yolunun arama sorgularını genel önizlemesini oluşturmak için [KQL](ediscovery-kql-editor.md) düzenleyicisini kullanın; KQL düzenleyicisi desteklenen aranabilir özellikler ve koşullar için otomatik tamamlama sağlar ve standart özellikler ve koşullar için desteklenen değer listelerini görüntüler; KQL düzenleyicisi ayrıca arama sorgularında olası hataların düzeltmeleri için hata algılama ve öneriler de sağlar

### <a name="information-barriers"></a>Bilgi engelleri

- [Bilgi engelleri modları için yeni](information-barriers-policies.md#step-6-information-barriers-modes) önizleme özelliği ile bilgi engellerini çalışmaya başlama
- [Bilgi engelleri modları Microsoft Teams](/microsoftteams/information-barriers-in-teams) önizleme özelliği ile bilgi engelleri
- [Bilgi engelleri modları OneDrive](/onedrive/information-barriers) önizleme özelliği ile bilgi engelleri
- [Bilgi engelleri modları SharePoint Online](/sharepoint/information-barriers) yeni önizleme özelliği ile bilgi engelleri

### <a name="insider-risk-management"></a>Insider risk yönetimi

- [Önerilen eylemleri almaya başlamaya için Insider risk](insider-risk-management-configure.md#recommended-actions-preview) yönetimi yeni önizleme özelliği ile çalışmaya başlama
- [Insider risk etkinliklerini araştırma](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) yeni "Insider risk uyarı kuyruğunızı yönetme konusunda yardım al" kılavuzu bölümü
- [Insider risk yönetimi ayarlarını yeni Yönetici](insider-risk-management-settings.md#admin-notifications) bildirimleri ayarları önizleme özelliği ile çalışmaya başlama

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- [Çok aşamalı disposition review is](disposition.md) now available generally (GA), with new [auditing events](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). Çok aşamalı disposition gözden geçirmesi, bekletme etiketi için art arda en çok beş disposition gözden geçirme aşaması belirtmenize olanak sağlar ve gözden geçirenler diğer kullanıcıları disposition gözden geçirme aşamasına ekleyebilir. E-posta bildirimlerini ve anımsatıcıları da özelleştirebilirsiniz.
- Bekletme ilkeleri için [Teams kanallar artık](create-retention-policies.md#retention-policy-for-teams-locations) genel olarak kullanılabilir (GA).

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri
- [Birlikte yazma](sensitivity-labels-coauthoring.md) ve Otomatik Kaydetme artık genel olarak Windows (Güncel Kanal veya Aylık Enterprise Kanalından) ve macOS'ta (en düşük 16.51 sürümü) Windows 2107'nin en düşük sürümü) için kullanıma sunulmaktadır.
- Yerleşik etiketlerin Office için uygulamanın kullanımı: Varsayılan etiket ayarı artık hem var olan belgeleri hem de yeni belgeleri destekler. Bu davranış değişikliği, Azure Information Protection birleşik etiketleme istemcisinde eşlik sağlar. Uygulama başına ve en düşük sürümler için uygulama başına uygulama sürümü hakkında daha fazla [](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) bilgi için Word, Excel özellikleri tablosuna PowerPoint.
- Kapsayıcı etiketleri artık [PowerShell gelişmiş ayarlarını kullanarak varsayılan paylaşım bağlantısı ayarlarını destekliyor](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings).
- Yerleşik [etiketleme için](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) minimum desteklenen sürümleri listeleen özellikler tablolarında artık Geçerli Kanal, Aylık Kanal ve Enterprise Kanalı için sürümler Semi-Annual Enterprise vardır.
