---
title: Microsoft Purview'daki yenilikler
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
description: Uyumluluk merkezine yeni çözümler eklemek, mevcut özellikleri geri bildiriminize göre güncelleştirmek veya yeni ve güncelleştirilmiş belgeler kullanıma sunarken Microsoft 365 sürekli değişen uyumluluk ortamını takip etme konusunda size yardımcı olur. Bu ay neler yaptığımıza bakın.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b5f231abfbfe943f0b2ab0cf33a14267f0940820
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972485"
---
# <a name="whats-new-in-microsoft-purview"></a>Microsoft Purview'daki yenilikler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Microsoft Purview uyumluluk portalına](microsoft-365-compliance-center.md) yeni çözümler eklemek, mevcut özellikleri geri bildiriminize göre güncelleştirmek veya yeni ve güncelleştirilmiş belgeleri kullanıma sunan Microsoft 365, sürekli değişen uyumluluk ortamını takip etme konusunda size yardımcı olur. Bugün Microsoft Purview'daki yeniliklere göz atmak için aşağıya göz atın.

> [!NOTE]
> Bazı uyumluluk özellikleri müşterilerimiz için farklı hızlarda kullanıma sunulur. Henüz bir özellik görmüyorsanız, [kendinizi hedeflenen sürüme](/office365/admin/manage/release-options-in-office-365) eklemeyi deneyin.

> [!TIP]
> Diğer yönetim merkezlerinde neler olduğuyla ilgileniyor musunuz? Şu makalelere göz atın:
>
> - [Microsoft 365 yönetim merkezi'deki yenilikler](/office365/admin/whats-new-in-preview)
> - [SharePoint yönetim merkezindeki yenilikler](/sharepoint/what-s-new-in-admin-center)
> - [Microsoft 365 Defender'daki yenilikler](../security/defender/whats-new.md)
>
> Ayrıca başlatılan, kullanıma sunulan, geliştirilen, iptal edilen veya daha önce yayımlanan Microsoft 365 özellikler hakkında bilgi edinmek için [Microsoft 365 Yol Haritası'nı](https://www.microsoft.com/microsoft-365/roadmap) ziyaret edin.

## <a name="april-2022"></a>Nisan 2022

### <a name="changes-to-product-names"></a>Ürün adlarına yapılan değişiklikler

Günümüzün merkezi olmayan, veri açısından zengin çalışma alanının zorluklarını karşılamak için, tüm veri varlığınızı anlamanıza, yönetmenize ve korumanıza yardımcı olan kapsamlı bir çözüm kümesi olan [Microsoft Purview'u](https://aka.ms/microsoftpurview) kullanıma sunuyoruz. Bu yeni marka ailesi, eski Microsoft Purview Veri Haritası'nın özelliklerini ve müşterilerin zaten güvendiği Microsoft 365 uyumluluk portföyünü bir araya getirerek kuruluşunuz için birleşik veri idaresi ve risk yönetimi sağlar.

| **Eski Ad** | **Yeni Ad** | **Açıklama** |
|:----------------|:-------------|:----------------|
| gelişmiş denetim Microsoft 365 <br><br> Microsoft 365 Temel Denetimi | Microsoft Purview Denetimi (Premium) <br><br> Microsoft Purview Denetimi (Standart)| Denetim çözümleri, kuruluşların güvenlik olaylarına, adli araştırmalara, iç araştırmalara ve uyumluluk yükümlülüklerine etkili bir şekilde yanıt vermelerine yardımcı olmak için tümleşik bir çözüm sağlar. Daha fazla bilgi için bkz. [Microsoft Purview Gelişmiş Denetim (Premium)](advanced-audit.md) ve [Microsoft Purview Gelişmiş Denetim (Standart)](set-up-basic-audit.md). |
| Microsoft 365 İletişim Uyumluluğu | Microsoft Purview İletişim Uyumluluğu | İletişim Uyumluluğu, şirket iletişim kanalları ve ilke ihlallerini hızla algılamanıza, yakalamanıza ve düzeltme eylemleri gerçekleştirmenize yardımcı olarak riskleri en aza indirmenize yardımcı olur. Daha fazla bilgi edinmek için bkz. [Microsoft Purview İletişim Uyumluluğu](communication-compliance-solution-overview.md). |
| Microsoft Uyumluluk Yöneticisi | Microsoft Purview Uyumluluk Yöneticisi | Uyumluluk Yöneticisi, veri koruma risklerinizin envanterini almaktan denetimleri uygulama, düzenlemeler ve sertifikalarla güncel kalma ve denetçilere raporlama gibi karmaşıklıkları yönetmeye kadar uyumluluk yolculuğunuz boyunca size yardımcı olabilir. Daha fazla bilgi için bkz. [Microsoft Purview Uyumluluk Yöneticisi](compliance-manager.md). |
| müşteri anahtarını Microsoft 365 | Microsoft Purview Müşteri Anahtarı | Müşteri Anahtarı, yetkisiz sistemler veya personel tarafından verilerin görüntülenmesine karşı ek koruma sağlar ve Microsoft veri merkezlerinde BitLocker disk şifrelemesini tamamlar. Daha fazla bilgi için bkz. [Microsoft Purview Müşteri Anahtarı](customer-key-overview.md). |
| Office 365 Müşteri Kasası | Microsoft Purview Müşteri Kasası | Müşteri Kasası, Microsoft'un açık onayınız olmadan hizmet işlemleri yapmak için içeriğinize erişememesini sağlar. Müşteri Kasası sizi Microsoft'un yalnızca yetkili isteklerin içeriğinize erişim izni vermek için kullandığı onay iş akışı sürecine getirir. Daha fazla bilgi için bkz. [Microsoft Purview Müşteri Kasası](customer-lockbox-requests.md). |
| Veri Kaybı Önleme | Microsoft Purview Veri Kaybı Önleme | DLP, kullanıcıların verileri sahip olmaması gereken kişilerle uygunsuz bir şekilde paylaşmasını engelleyerek hassas verilerin korunmasına ve riskin azaltılmasına yardımcı olur. Daha fazla bilgi için bkz. [Microsoft Purview Veri Kaybı Önleme](dlp-learn-about-dlp.md). |
| Microsoft 365 için Çift Anahtar şifrelemesi | Microsoft Purview Çift Anahtar Şifrelemesi | Çift Anahtar Şifrelemesi (DKE), korumalı içeriğe erişmek için iki anahtarı birlikte kullanır. Microsoft bir anahtarı Microsoft Azure depolar ve siz diğer anahtarı tutarsınız. Daha fazla bilgi edinmek için bkz. [Microsoft Purview Çift Anahtar Şifrelemesi](double-key-encryption.md) |
| Microsoft 365 Bilgi Engelleri | Microsoft Purview Bilgi Engelleri | Bilgi Engelleri, iç bilgileri korumak için kuruluşunuz içindeki belirli kişiler arasındaki iletişimi ve işbirliğini kısıtlayan bir çözümdür. Daha fazla bilgi için bkz. [Microsoft Purview Bilgi Engelleri](information-barriers-solution-overview.md). |
| Microsoft Bilgi Koruması | Microsoft Purview Information Protection | Bilgi koruması, hassas bilgileri nerede yaşarsa yaşasın veya nereye giderse gitsin keşfetmenize, sınıflandırmanıza ve korumanıza yardımcı olur. Daha fazla bilgi için bkz. [Microsoft Purview Information Protection](information-protection.md). |
| Microsoft Bilgi İdaresi | Microsoft Purview Veri Yaşam Döngüsü Yönetimi | Veri yaşam döngüsü yönetimi, saklamanız ve silmeniz gereken içeriği saklamanız için araçlar ve özellikler sağlar. Daha fazla bilgi için bkz. [Microsoft Purview Veri Yaşam Döngüsü Yönetimi](data-lifecycle-management.md). |
| insider Risk Management'ı Microsoft 365 | Microsoft Purview Insider Risk Management | Insider risk yönetimi, riskli kullanıcı etkinliklerini hızla tanımlamanıza, önceliklendirmenize ve harekete geçirmenize yardımcı olmak için hizmetin ve üçüncü taraf göstergelerin tamamını kullanır. Daha fazla bilgi için bkz. [Microsoft Purview Insider Risk Management](insider-risk-management.md). |
| Office 365 İleti Şifrelemesi | Microsoft Purview İleti Şifrelemesi | İleti Şifreleme ile kuruluşunuz, kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri gönderebilir ve alabilir. Daha fazla bilgi için bkz. [Microsoft Purview İleti Şifrelemesi](ome.md). |
| Microsoft 365'da Ayrıcalıklı Erişim Yönetimi | Microsoft Purview Privileged Access Management | Privileged Access Management, kuruluşunuzun ihlallere karşı korunmasına yardımcı olur ve hassas verilere veya kritik yapılandırma ayarlarına erişimi sınırlayarak uyumluluk en iyi yöntemlerini karşılamaya yardımcı olur. Daha fazla bilgi için bkz. [Microsoft Purview Privileged Access Management](privileged-access-management-solution-overview.md). |
| Microsoft veri bağlayıcıları | Microsoft Purview veri bağlayıcıları | Microsoft 365, yöneticilerin Microsoft dışı üçüncü taraf verileri sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından Microsoft 365 kuruluşunuzdaki posta kutularına aktarmak ve arşivlemek için veri bağlayıcılarını kullanmasına olanak tanır. Daha fazla bilgi için bkz. [Microsoft Purview veri bağlayıcıları](compliance-extensibility.md). |
| Microsoft 365 Gelişmiş eKeşif <br><br> Microsoft 365 Core eKeşif | Microsoft Purview eKeşif (Premium) <br><br> Microsoft Purview eKeşif (Standart) | Elektronik bulma veya eBulma, yasal davalarda kanıt olarak kullanılabilecek elektronik bilgileri tanımlama ve teslim etme işlemidir. Daha fazla bilgi için bkz. [Microsoft Purview eKeşif (Premium)](overview-ediscovery-20.md) ve [Microsoft Purview eKeşif (Standart)](get-started-core-ediscovery.md). |
| Microsoft 365 uyumluluk merkezi | Microsoft Purview uyumluluk portalı | Microsoft 365 E5 Uyumluluk paketindeki çözümlere ve çözüm kataloğuna erişmek için yönetici portalı. Daha fazla bilgi için bkz. [Microsoft Purview uyumluluk portalı](microsoft-365-compliance-center.md). |

## <a name="february-2022"></a>Şubat 2022

### <a name="ediscovery"></a>Ediscovery

- [eKeşif 'te (Premium) koruyucu iletişim şablonlarını yönetme](advanced-ediscovery-communications-library.md) - eKeşif yöneticileri artık kuruluştaki herhangi bir eBulma (Premium) durumunda kullanılabilecek koruyucu iletişim şablonları oluşturabilir.
- [eKeşif 'te (Premium) veren memurları yönetme](advanced-ediscovery-issuing-officers.md) - eKeşif yöneticileri, kuruluştaki herhangi bir eBulma (Premium) durumunda koruyucu iletişimlere atanabilecek veren memurların listesini ekleyebilir.

### <a name="data-lifecycle-management-and-records-management"></a>Veri yaşam döngüsü yönetimi ve kayıt yönetimi

- Bekletme ilkeleri ve bekletme etiketi ilkeleri için [uyarlamalı kapsamlar](retention.md#adaptive-or-static-policy-scopes-for-retention) artık genel kullanıma sunuldu (GA). [Uyarlamalı kapsamı yapılandırma](retention-settings.md#to-configure-an-adaptive-scope) yönergeleri artık SharePoint site kapsamları için daha fazla bilgi içerir: Özel site özelliklerini kullanmaya yönelik blog gönderisi başvurusu ve gelişmiş sorgu oluşturucusuyla belirli site türlerini dahil etmek veya hariç tutmak için SiteTemplate site özelliğini kullanma.
- Veri yaşam döngüsü yönetimi çözümünde [ilke araması](retention.md#policy-lookup) genel kullanıma sunuldu (GA).
- Kullanıcıların [Get-PnPTenant ve Set-PnPTenant'tan](/powershell/module/sharepoint-pnp/get-pnptenant) AllowFilesWithKeepLabelToBeDeletedSPO ve AllowFilesWithKeepLabelToBeDeletedODB kullanarak SharePoint ve OneDrive etiketli öğeleri silmesine olanak tanıyan kayıt yönetimi ayarına powershell alternatifi.[]( /powershell/module/sharepoint-pnp/set-pnptenant)

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Yeni kılavuz Windows bilgisayarlar için Azure Information Protection (AIP) birleşik etiketleme istemcisini kullanıyorsanız [neden Office uygulamaları için AIP eklentisi yerine yerleşik etiketlemeyi seçin](sensitivity-labels-aip.md)? Bu sayfa, Office uygulamaları için yeni özel önizleme hakkında bilgi içerir.
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) için yeni ayarlar:
  - E-postanın her zaman eşleşen bir duyarlılık etiketi uygulamayı ve kuruluş dışından alınan e-postaya şifreleme uygulamayı desteklemeye yönelik ek ayarlar.
  - Belirli örnekler (kullanıcılar, gruplar, siteler) için dışlamalar, **Dahil** Edilenler için varsayılan **Tümü** seçimi belirtildiğinde yeni **Dışlanan** seçeneği kullanılarak desteklenir.
- Önizleme aşamasında: Mobil cihazlar (iOS ve Android), en düşük sürümlere sahip olduğunuzda ve bu önizlemeyi kabul ettiğinizde [birlikte yazmayı](sensitivity-labels-coauthoring.md) destekler.
- Varsayılan paylaşım bağlantı türünü ayarlama desteği, SharePoint ve OneDrive tek tek belgelere genişletilir. Daha fazla bilgi için, [SharePoint ve OneDrive'da siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanma]( sensitivity-labels-default-sharing-link.md) makalesine bakın.
- Teams yönetim merkezi artık kapsayıcı etiketlerini (Gruplar & siteleri kapsamına sahip duyarlılık etiketleri) destekliyor.

## <a name="january-2022"></a>Ocak 2022

### <a name="microsoft-purview-data-lifecycle-management"></a>Microsoft Purview Veri Yaşam Döngüsü Yönetimi

- Microsoft Purview uyumluluk portalında yapılandırdığınız çözümlerle ilgili bilgileri daha kolay bulmanıza yardımcı olmak için eski adıyla Microsoft Information Governance olan belgeler önemli ölçüde gözden geçirilmiş ve yeniden yapılandırılmıştır: Veri Bağlayıcıları, Veri Yaşam Döngüsü Yönetimi ve Kayıt Yönetimi. Bu düzeltmenin bir parçası olarak, belgelerde veri yaşam döngüsü yönetimi ile kayıt yönetimi arasındaki saklama senaryoları için daha net bir ayrım sağlanır.
- Yeniden yapılandırmayı desteklemek için [yeni veri yaşam döngüsü yönetimi hakkında bilgi edinin](data-lifecycle-management.md).
- [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md) - "Kullanmaya başlayın saklama ile" değiştirmek için bu makale saklamayı içeren tüm veri yaşam döngüsü yönetimi özelliklerine yönelik başlangıç adımlarını içerir.
- [Bekletme ilkelerinizin özel durumları için bekletme etiketleri oluşturun](create-retention-labels-data-lifecycle-management.md) . Kayıt yönetimi yerine veri yaşam döngüsü yönetimi için bekletme etiketlerini kullanmaya yönelik yeni, tanımlanmış bir senaryo.
- [Arşiv posta kutuları hakkında bilgi edinin](archive-mailboxes.md) - yeni, yeniden yapılandırmayı desteklemek için daha önce "Arşiv posta kutularını etkinleştirme" makalesinde yer alan kavramsal bilgileri içerir.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Gizlilik yönetimi artık Microsoft Priva'dır](/privacy/priva/priva-overview) - ürünü ve çözümlerini, Priva Gizlilik Risk Yönetimi ve Priva Konu Hakları İsteklerini yeniden üretecek şekilde güncelleştirildi.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Artık önizleme aşamasında olan yeni [rol grupları ve rolleri](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels) için destek.
- Otomatik etiketleme ilkeleri için yeni [izleme özellikleri](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) .
- Şimdi kullanıma sunuldu: Geçerli Kanaldaki (Önizleme) mevcut belgeler için varsayılan etiket ve Web üzerinde Office için gerekçe metni.
- Temmuz Semi-Annual Enterprise Kanalı için sürüm 2202+ ile duyuruldu: Outlook için birlikte yazma ve denetim.

## <a name="december-2021"></a>Aralık 2021

### <a name="compliance-and-service-assurance"></a>Uyumluluk ve hizmet güvencesi

- [GDPR kapsamında Azure, Dynamics 365 ve Windows ihlal bildirimi](/compliance/regulatory/gdpr-breach-notification) - müşterilerin güvenlik ve gizlilik bildirimleri almak için Bulut için Defender gibi bir ödeme hizmeti kullanmasına gerek olmadığını netleştirmek için güncelleştirildi

### <a name="ediscovery"></a>Ediscovery

- [Microsoft Teams içeriği için eBulma (Premium) iş akışı](teams-workflow-in-advanced-ediscovery.md#reference-guide) - eBulma'da (Premium) Teams içeriği yönetmeye yönelik yeni bir indirilebilir hızlı başvuru kılavuzuyla güncelleştirildi

### <a name="data-lifecycle-management"></a>Veri yaşam döngüsü yönetimi

- [Uyumluluk merkezinde arşiv posta kutularını etkinleştirme - arşiv posta kutuları](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) için yeni tanılama aracı hakkında bölüm eklendi
- [Kuruluşunuzun PST dosyalarını Microsoft 365 içeri aktarmak için ağ karşıya yükleme özelliğini kullanın](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) - PST içeri aktarma artık AzCopy v10'ı destekliyor
- [Etkin olmayan posta kutusunu geri yükleme](restore-an-inactive-mailbox.md) - önce etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusuna ekleyerek etkin olmayan posta kutusunu geri yüklemek için düzeltilmiş yordam

### <a name="information-protection"></a>Bilgi koruması

- [Microsoft Purview ile bilgi koruma çözümü dağıtma - Microsoft Purview'u](information-protection-solution.md) dağıtmak için açıklayıcı bir yol haritası arayan müşteriler için yeni adım adım yönergeler Information Protection

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi

- [Bekletme ilkelerinin geçerli olması ne kadar sürer](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)? için yeni kılavuz
- Yeni kiracı ayarları dağıtılıyor: Kayıt olarak işaretlenen ve kilitlenen etiketli SharePoint öğelerinin özelliklerini düzenlemeyi engelleyen kayıt yönetimi ayarı ve kullanıcıların kayıt olarak işaretlenmiş öğelerin kilidini açmasını engelleyen diğer ayarlar

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- Zorunlu etiketleme ve Power BI için varsayılan etiket genel kullanıma sunuldu (GA)

## <a name="november-2021"></a>Kasım 2021

### <a name="compliance-manager"></a>Uyumluluk Yöneticisi

Yeni içerik güncelleştirmeleri [Microsoft Purview Uyumluluk Yöneticisi'ndeki yenilikler](compliance-manager-whats-new.md) bölümünde görüntülenebilir.

### <a name="device-onboarding"></a>Cihaz Ekleme

Cihaz ekleme için aşağıdaki makaleler eklendi:

- [macOS cihazlarının Microsoft 365'e katılımına genel bakış (önizleme)](device-onboarding-macos-overview.md)
- [Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma (önizleme)](device-onboarding-offboarding-macos-intune.md)
- [macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için Intune kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)](device-onboarding-offboarding-macos-intune-mde.md)
- [JAMF Pro (önizleme) kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma](device-onboarding-offboarding-macos-jamfpro.md)
- [macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>Ediscovery

- [Yeni servis talebi biçimini eBulma (Premium) içinde kullan](advanced-ediscovery-new-case-format.md) Yeni servis talebi biçimi genel kullanıma sunuldu ve "büyük harf biçimi" olarak yeniden adlandırıldı

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- Kullanıma sunulma: SharePoint ve OneDrive etiketli öğelerin kullanıcılar tarafından silinip silinemeyeceğini denetleyebilen yeni kayıt yönetimi ayarları. Daha önce, içeriği korumak için yapılandırılmış ve öğeleri kayıt olarak işaretlememiş olan bekletme etiketleri, kullanıcıların OneDrive'da bu eyleme izin verildiğinde SharePoint etiketli içeriği silmesini engelliyordu. Daha fazla bilgi için bkz. [SharePoint ve OneDrive için bekletme nasıl çalışır](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)?

### <a name="sensitive-information-types"></a>Hassas Bilgi Türleri

Aşağıdaki yeni makaleler eklendi:

- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri için kaynak verilerini dışa aktarma](sit-get-started-exact-data-match-export-data.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma](sit-get-started-exact-data-match-create-schema.md)
- [Tam veri eşleşmeli hassas bilgi türleri için hassas bilgi kaynak tablosu karması oluşturma ve karşıya yükleme](sit-get-started-exact-data-match-hash-upload.md)
- [Tam veri eşleşmesi hassas bilgi türü/kural paketi oluşturma](sit-get-started-exact-data-match-create-rule-package.md)
- [Tam veri eşleşmesi hassas bilgi türünü test etme](sit-get-started-exact-data-match-test.md)
- [Tam veri eşleşme şemanızı yönetme](sit-use-exact-data-manage-schema.md)
- [Hassas bilgi kaynak tablosu dosyanızı yenileme](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri
- [Microsoft Purview Veri Haritası etiketlerinin](/azure/purview/create-sensitivity-label) kapsam adı artık "Şemalaştırılmış veri varlıkları" olarak belirlenmiştir.

## <a name="october-2021"></a>Ekim 2021

### <a name="app-governance"></a>Uygulama idaresi

- [Bulut için Defender Uygulamaları için uygulama idaresi eklentisi genel kullanıma sunuldu](/cloud-app-security/app-governance-manage-app-governance). Uygulama idaresi belgeleri, Bulut için Defender Uygulamaları belgelerine katılmak üzere taşındı.

### <a name="compliance--service-assurance"></a>Uyumluluk & hizmet güvencesi

- [Hizmet güvencesi](/compliance) - Sertifikalar ve uygulanabilirlik bildirimleri için içerik güncelleştirmelerini üç ayda bir gözden geçirme) Veri merkezi varlık yönetimi
  - Veri merkezi mimarisi ve altyapısı
  - Veri merkezi iş sürekliliği ve olağanüstü durum kurtarma
  - Veri merkezi ortam korumaları
  - Veri merkezi fiziksel erişim güvenliği
  - SDL uyumluluk programını Microsoft 365
  - Microsoft 365 hizmet mühendisi erişim denetimi
  - MS Cloud için risk değerlendirme kılavuzu

### <a name="data-loss-prevention"></a>Veri Kaybı Önleme

- [Microsoft Purview Veri Kaybı Önleme'nin](endpoint-dlp-learn-about.md) macOS desteği ve gelişmiş sınıflandırma için güncelleştirildiğini öğrenin; desteklenen tüm dosya türleri için etkinliği denetlemek üzere özel bir DLP ilkesi oluşturmak için güncelleştirildi.
- [Microsoft 365 Endpoint veri kaybı önleme ile Kullanmaya başlayın](endpoint-dlp-getting-started.md) macOS desteği ve gelişmiş sınıflandırma için güncelleştirildi.
- [Uç nokta veri kaybı önlemenin kullanılması](endpoint-dlp-using.md) macOS desteği ve gelişmiş sınıflandırma için güncelleştirildi.
- [Veri Kaybı Önleme ilkesi ipuçları başvurusu](dlp-policy-tips-reference.md) macOS desteği ve gelişmiş sınıflandırma için güncelleştirildi.
- [macOS cihazlarını Microsoft 365(önizleme) içine ekleme](device-onboarding-macos-overview.md), macOS desteği ve gelişmiş sınıflandırma için güncelleştirildi.
- Cihaz ekleme için aşağıdaki yeni sayfalar eklendi:
  - [Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma (önizleme)](device-onboarding-offboarding-macos-intune.md)
  - [macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için Intune kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)](device-onboarding-offboarding-macos-intune-mde.md)
  - [JAMF Pro (önizleme) kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma](device-onboarding-offboarding-macos-jamfpro.md)
  - [macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>Ediscovery

- [Bulut eklerini eBulma'da (Premium)](advanced-ediscovery-cloud-attachments.md) toplamaya ek olarak, bir bulut ekinin en son sürümünü toplamanın yanı sıra, bir e-posta iletisinde veya sohbet konuşmasında paylaşılan sürümü toplayabilir veya sohbet konuşması Teams; paylaşılan sürümü toplamak, bulut eklerine otomatik olarak bekletme etiketi uygulama özelliğiyle mümkün hale getirilebilir.
- [eBulma (Premium) içinde,](advanced-ediscovery-historical-versions.md) arama için bir SharePoint sitesinde depolanan belgelerin tüm sürümlerini dizinleyen yeni işlevlerde geçmiş sürümleri ayarlayın; bu, koleksiyon sorgusuyla eşleşen içerik içeren belge sürümlerinin arama sonuçlarında döndürüldiği anlamına gelir.

### <a name="encryption"></a>Şifreleme

- [Bire bir Microsoft Teams çağrıları için uçtan uca şifrelemeyi kullanın (Genel önizleme) Genel önizleme](/microsoftteams/teams-end-to-end-encryption) için yeni içerik.

### <a name="data-lifecycle-management"></a>Veri yaşam döngüsü yönetimi

- [Epic EHR denetim verilerini içeri aktarmak için bir bağlayıcı ayarlayın](import-epic-data.md) yeni bağlayıcı, şirket içi risk yönetimi için yeni genel hasta verilerini kötüye kullanma senaryolarını desteklemek üzere Epic elektronik sağlık kayıtları sisteminden verileri içeri aktarmanıza olanak tanır.
- [Sağlık ehr denetim verilerini içeri aktarmak için bir bağlayıcı ayarlayın](import-healthcare-data.md) yeni bağlayıcı, şirket içi risk yönetimi için yeni genel hasta verilerini kötüye kullanma senaryolarını desteklemek üzere elektronik sağlık kayıt sisteminden verileri içeri aktarmanıza olanak tanır.

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- [Uyarlamalı ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) , bekletme ilkeleri ve bekletme etiketi ilkeleri için önizlemede yayınlanır.
- Artık [duyarlılık etiketine göre otomatik olarak bir bekletme etiketi uygulayabilirsiniz](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- Dosya Planı'nın yeni bir [içeri aktarma işlemi](file-plan-manager.md#import-retention-labels-into-your-file-plan) var.
- [Bekletme ilkeleri ve bekletme etiketi ilkeleri için genel ayarlar: Hem bekletme ilkeleri hem de bekletme etiketi ilkelerinde](retention-settings.md) uyarlamalı kapsamları ve diğer ayarları yapılandırma hakkında ayrıntılı bilgi için yeni makale.

### <a name="sensitive-information-types"></a>Hassas Bilgi Türleri

- [Adlandırılmış varlıklar için adlandırılmış varlıklar (önizleme) yeni içeriği hakkında bilgi edinin](named-entities-learn.md) .
- [Adlandırılmış varlıkları kullanırken veri kaybı önleme ilkelerinizde adlandırılmış varlıkları kullanın (önizleme)](named-entities-use.md) yeni içerik.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

- [Varsayılan etiketler ve varsayılan ilkeler](mip-easy-trials.md) uygun müşterilere dağıtılır.

## <a name="september-2021"></a>Eylül 2021

### <a name="app-governance"></a>Uygulama idaresi

- [Kolaylaştırılmış uygulama idaresi kullanmaya başlama bilgileri](app-governance-get-started.md) , iş akışını değiştirdi ve genel önizleme kaydına yeni bağlantılar ekledi
- [Yeni algılama uyarıları tanımı](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) eklendi (güncelleştirildi; koleksiyon uyarıları için yeni tanım eklendi)

### <a name="auditing"></a>Denetim

- Bir kuruluştaki denetim durumundaki değişikliklerin kendilerinin nasıl denetleniyor olduğuna ilişkin yeni bölüm eklenmiş denetimi [açma veya kapatma](turn-audit-log-search-on-or-off.md); bu, denetim açık veya kapalı olduğunda denetim kayıtlarının günlüğe kaydedildiğini gösterir; Exchange yönetici denetim günlüğünde bu denetim kayıtlarını arayabilirsiniz

### <a name="communication-compliance"></a>İletişim uyumluluğu

- [SIEM çözümleriyle iletişim uyumluluğu](communication-compliance-siem.md) tümleştirmesi için SIEM çözümleriyle iletişim uyumluluğu kılavuzu)

### <a name="compliance-offerings"></a>Uyumluluk teklifleri

- [Çok Katmanlı Bulut Güvenliği (MTCS)](/compliance/regulatory/offering-mtcs-singapore) Dynamics 365 kapsamı için Singapur için standart güncelleştirmeler
- [Ödeme Kartı Sektörü (PCI)](/compliance/regulatory/offering-pci-dss) SharePoint Çevrimiçi kapsamı için Veri Güvenliği Standardı (DSS) güncelleştirmeleri
- [ABD Bölüm 508](/compliance/regulatory/offering-section-508-vpats) yeni istemci yazılımı kılavuzu
- [Web İçeriği Erişilebilirlik Yönergeleri](/compliance/regulatory/offering-wcag-2-1) yeni istemci yazılımı kılavuzu

### <a name="compliance--service-assurance"></a>Uyumluluk & hizmet güvencesi

- [Hizmet güvencesi](/compliance/) , uygulanabilirlik sertifikaları ve deyimleri için içerik güncelleştirmelerini üç ayda bir gözden geçirme
  - Veri taşıyan cihaz yok etme
  - DDOS saldırıları

### <a name="data-connectors"></a>Veri bağlayıcıları

- CellTrust ve 17a-4 LLC'den [üçüncü taraf verileri Microsoft 365](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) veri bağlayıcılarında arşivleme artık ABD Kamu bulutundaki GCC kuruluşlarda kullanılabilir
- [YouTube verilerini arşivleme amacıyla bir bağlayıcı ayarlamak](archive-youtube-data.md) , genel önizlemede bu özellik için yeni yönergeler sağlar.

### <a name="ediscovery"></a>Ediscovery

- İçerik arama, eBulma (Standart) ve eBulma (Premium) içinde arama sorguları oluşturmanın yeni bir yolunun arama sorguları genel önizlemesini oluşturmak için KQL [düzenleyicisini kullanın](ediscovery-kql-editor.md); KQL düzenleyicisi, desteklenen aranabilir özellikler ve koşullar için otomatik uyumluluk sağlar ve standart özellikler ve koşullar için desteklenen değerlerin listesini görüntüler; KQL  düzenleyici ayrıca hata algılama ve arama sorgularındaki olası hataların düzeltmeleri için öneriler sağlar

### <a name="information-barriers"></a>Bilgi engelleri

- [Bilgi engelleri ile Kullanmaya başlayın bilgi engelleri](information-barriers-policies.md#step-6-information-barriers-modes) modları için yeni önizleme özelliği
- [Bilgi engelleri modları için yeni Microsoft Teams](/microsoftteams/information-barriers-in-teams) önizleme özelliği ile bilgi engelleri
- [Bilgi engelleri](/onedrive/information-barriers) modları için yeni OneDrive önizleme özelliği ile bilgi engelleri
- [Bilgi engelleri modları için SharePoint Çevrimiçi](/sharepoint/information-barriers) yeni önizleme özelliği ile bilgi engelleri

### <a name="insider-risk-management"></a>İçeriden risk yönetimi

- Önerilen eylemleri kullanmaya başlamak için [insider risk yönetimi yeni önizleme özelliğiyle Kullanmaya başlayın](insider-risk-management-configure.md#recommended-actions-preview)
- [Insider risk etkinliklerini araştırma yeni 'Insider](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) risk uyarı kuyruğunuzu yönetme konusunda yardım alın' kılavuzu bölümü
- [insider risk yönetimi ayarları yeni Yönetici bildirimleri ayarları önizleme özelliğiyle Kullanmaya başlayın](insider-risk-management-settings.md#admin-notifications)

### <a name="retention-and-records-management"></a>Bekletme ve kayıt yönetimi
- Yeni [denetim olaylarıyla](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) [birlikte çok aşamalı değerlendirme gözden geçirmesi](disposition.md) genel kullanıma sunuldu (GA). Çok aşamalı değerlendirme gözden geçirmesi, bekletme etiketi için ardışık beş ayrı değerlendirme aşaması belirtmenize olanak tanır ve gözden geçirenler başka kullanıcıları değerlendirme aşamalarına ekleyebilir. E-posta bildirimlerini ve anımsatıcılarını da özelleştirebilirsiniz.
- [Teams bekletme ilkeleri](create-retention-policies.md#retention-policy-for-teams-locations) için özel kanallar artık genel kullanıma sunuldu (GA).

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri
- [Birlikte yazma ve Otomatik Kaydetme](sensitivity-labels-coauthoring.md) artık Windows (Geçerli Kanaldan veya Aylık Enterprise Kanalından en düşük 2107 sürümü) ve macOS (en az 16,51 sürümü) için genel kullanıma sunuldu (GA).
- Yerleşik etiketler kullanan Office uygulamalar için kullanıma sunulma: Varsayılan etiket ayarı artık mevcut belgelerin yanı sıra yeni belgeleri de destekler. Davranıştaki bu değişiklik, Azure Information Protection birleşik etiketleme istemcisiyle eşlik sağlar. Uygulama başına dağıtım ve en düşük sürümler hakkında daha fazla bilgi için Word, Excel ve PowerPoint [için yetenekler tablosuna](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) bakın.
- Kapsayıcı etiketleri artık [PowerShell gelişmiş ayarlarını kullanarak varsayılan paylaşım bağlantısı ayarlarını](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings) destekliyor.
- Yerleşik etiketleme için desteklenen en düşük sürümleri listeleyen [özellik tablolarında](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) artık Geçerli Kanal, Aylık Enterprise Kanalı ve Semi-Annual Enterprise Kanalı sürümleri vardır.
