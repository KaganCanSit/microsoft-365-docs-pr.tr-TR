---
title: Microsoft 365'da kayıt yönetimiyle Kullanmaya başlayın
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Yasal, iş veya mevzuat yükümlülükleri için yüksek değerli içeriği yöneten ancak nereden başlayacağınıza emin olmayan Microsoft 365 için kayıt yönetimi çözümüne mi ihtiyacınız var? Başlamak için bazı pratik kılavuzları okuyun.
ms.openlocfilehash: bbba24a2627c6040873da8d01185e4e6bdfdbfc8
ms.sourcegitcommit: 265a4fb38258e9428a1ecdd162dbf9afe93eb11b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2022
ms.locfileid: "65268759"
---
# <a name="get-started-with-records-management"></a>Kayıt yönetimini kullanmaya başlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Microsoft 365'de kayıt yönetimi çözümünü kullanarak kuruluşunuzun yasal, iş veya mevzuat yükümlülükleri için yüksek değerli içeriğini yönetmeye başlamaya hazır mısınız? Başlamak için aşağıdaki kılavuzu kullanın:

1. **Bekletme ve silmenin Microsoft 365 nasıl çalıştığını anlayın** ve belge ve e-postaları öğe düzeyinde yöneten bekletme etiketlerini desteklemek için bekletme ilkelerini kullanmanız gerekip gerekmediğini belirleyin: [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md)
    
    Gerekirse, Microsoft 365 iş yükleri genelinde verilerin temel idaresi için [bekletme ilkeleri oluşturun](create-retention-policies.md).
    
2. **Kayıt yönetimi çözümünü** ve belgeler ve e-postalar kayıt olarak bildirildiğinde eylemlere izin vermek veya bunları engellemek için bekletme etiketlerinin nasıl kullanılabileceğini anlama: [Kayıt yönetimi hakkında bilgi edinin](records-management.md)

3. **Bekletme ve silme ayarları ve eylemleri için dosya planınızı oluşturma ve** varsa mevcut bir planı içeri aktararak öğelerin kayıt olarak işaretlenmesi gerektiğinde veya yeni bekletme etiketleri oluşturarak: [Bekletme etiketleri oluşturmak ve yönetmek için dosya planını kullanma](file-plan-manager.md)

4. **Bekletme etiketlerinizi yayımlayın ve uygulayın**. Bekletme etiketleri, birden çok ilkede kullanılabilen ve kullanıcı iş akışlarına dahil edilebilen yeniden kullanılabilir yapı taşlarıdır:

    - [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
    - [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements"></a>Abonelik ve lisans gereksinimleri

Bir dizi farklı abonelik kayıt yönetimini destekler ve kullanıcıların lisans gereksinimleri kullandığınız özelliklere bağlıdır.

Kullanıcılarınızın Microsoft Purview özelliklerinden yararlanması için lisanslama seçeneklerini görmek [için güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzuna](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) bakın. Kayıt yönetimi için, özellik düzeyinde lisanslama gereksinimleri için [Microsoft Purview Kayıt Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management) bölümüne ve ilgili PDF indirme bölümüne bakın.

## <a name="permissions"></a>İzinler

Kayıt yönetiminden sorumlu uyumluluk ekibinizin üyelerinin <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalında</a> izinlere sahip olması gerekir. Varsayılan olarak, kiracı yöneticisinin (genel yönetici) bu konuma erişimi vardır ve uyumluluk görevlilerine ve diğer kişilere kiracı yöneticisinin tüm izinlerini vermeden erişim verebilir. Bu sınırlı yönetime izin vermek için, kullanıcıları **Kayıt Yönetimi** yönetici rol grubuna eklemenizi öneririz. Bu grup, [edat gözden geçirme ve doğrulama](disposition.md) da dahil olmak üzere kayıt yönetimiyle ilgili tüm özellikler için izinler verir.

Salt okunur bir rol için yeni bir rol grubu oluşturabilir ve bu gruba **Yalnızca Görüntüleme Kayıt Yönetimi** rolünü ekleyebilirsiniz.

Varsayılan rollere kullanıcı ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için bkz. [Microsoft Purview uyumluluk portalında İzinler](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca kayıtları bildiren ve değerlendirmeyi yöneten bekletme etiketleri oluşturmak, yapılandırmak ve uygulamak için gereklidir. Bu etiketleri yapılandıran kişinin içeriğe erişmesi gerekmez.

## <a name="common-scenarios"></a>Yaygın senaryolar

İş gereksinimlerinizi kayıt yönetimi tarafından desteklenen senaryolarla eşlemenize yardımcı olması için aşağıdaki tabloyu kullanın.

> [!TIP]
> Belirli bir endüstri düzenlemesine uymanız mı gerekiyor? [Düzenlemeye özgü yönergeler için veri yaşam döngüsü yönetimi ve kayıt yönetimi için Mevzuat gereksinimlerini](retention-regulatory-requirements.md) denetleyin.

|Yapmak istiyorum...|Belge|
|----------------|---------------|
|Kayıt bildirme |[Saklama etiketleri kullanarak kayıtları beyan etme](declare-records.md)|
|Kaydı güncelleştirme |[SharePoint veya OneDrive depolanan kayıtları güncelleştirmek için kayıt sürümü oluşturma özelliğini kullanma](record-versioning.md)|
|Yöneticilerin ve kullanıcıların belgeler ve e-postalar için saklama ve silme eylemlerini el ile uygulamasına izin verin: <br />- SharePoint <br />- OneDrive <br />- Outlook ve Web üzerinde Outlook|[Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)|
|Site yöneticilerinin bir SharePoint kitaplığı, klasörü veya belge kümesindeki tüm içerik için varsayılan saklama ve silme eylemlerini ayarlamasına izin ver|[Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)|
|Kullanıcıların Outlook kurallarını kullanarak e-postalara saklama ve silme eylemlerini otomatik olarak uygulamasına izin verme|[Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)|
|Yöneticilerin belge anlama modeline saklama ve silme eylemleri uygulamasına izin verin; böylece bunlar SharePoint kitaplığındaki tanımlanan belgelere otomatik olarak uygulanır|[Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)|
|Belgelere ve e-postalara saklama ve silme eylemlerini otomatik olarak uygulama |[İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)|
|Bir olay gerçekleştiğinde bekletme süresini başlatın, örneğin:  <br />- Çalışanlar kuruluştan ayrılır <br />- Sözleşmelerin süresi doluyor <br />- Ürün ömrünün sonu| [Bir olay meydana geldiğinde saklamayı başlatma](event-driven-retention.md)|
|Mevzuat gereksinimlerini karşılamaya veya dolandırıcı yöneticilere karşı koruma sağlamaya yardımcı olmak için ilkelerdeki değişiklikleri kısıtlama| [Saklama ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma](retention-preservation-lock.md)
|SharePoint'da farklı belge türlerinin yaşam döngüsünü yönetme| [SharePoint'de depolanan belgelerin yaşam döngüsünü yönetmek için bekletme etiketlerini kullanma](auto-apply-retention-labels-scenario.md)|
|Kişisel verileri içeren içeriğin depolandığına veya çok uzun süre dokunulmadığını belirten bir uyarı alırsam dosyaya bekletme etiketi uygulama| [Gizlilik Risk Yönetimi'nde uyarıları araştırma ve düzeltme](/privacy/priva/risk-management-alerts)|
|Saklama süresinin sonunda içerik silinmeden önce birinin gözden geçirmesini ve onaylamasını sağlama|[Değerlendirme değerlendirmeleri](disposition.md#disposition-reviews) |
|Saklama süresinin sonunda kalıcı olarak silinen içerik için edat kanıtına sahip olmak|[Kayıtların konumu](disposition.md#disposition-of-records) |
| Öğeleri saklama ve silme ayarlarının nasıl ve nerede uygulandığını izleme | [Bekletme etiketlerini izleme](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

Temel veri idaresi için bekletme ilkeleri kullanıyorsanız, bunlar genellikle kullanıcı etkileşimi olmadan arka planda göze çarpmadan çalışır. Sonuç olarak kullanıcılar için çok az belgeye ihtiyaç duyarlar. Teams için bekletme ilkeleri, iletileri silindiğinde kullanıcıları [bekletme ilkeleri hakkında Teams](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b) bir bağlantıyla bilgilendirebilir.

Buna karşılık, bekletme etiketlerinin Microsoft 365 uygulamalarda bir kullanıcı arabirimi varlığı vardır, bu nedenle bu etiketler üretim ağınıza dağıtılmadan önce son kullanıcılar ve yardım masanız için rehberlik sağladığınızdan emin olun. Kullanıcıların SharePoint ve OneDrive bekletme etiketleri uygulamasına yardımcı olmak ve düzenleme için kayıtların kilidini açma hakkında bilgi edinmek için bkz. [SharePoint veya OneDrive dosyalara bekletme etiketleri uygulama](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Ancak, en etkili son kullanıcı belgeleri, seçtiğiniz bekletme etiketi adları ve yapılandırmaları için sağladığınız özelleştirilmiş yönergeler ve yönergeler olacaktır. Kullanıcılarınızı eğitmek için kullanabileceğiniz şu sayfaya ve indirmelere bakın: [Bekletme Etiketleri için Son Kullanıcı Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
