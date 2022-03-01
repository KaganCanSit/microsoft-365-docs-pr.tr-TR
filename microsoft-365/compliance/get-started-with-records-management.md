---
title: Kayıt yönetimiyle çalışmaya Microsoft 365
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
description: Yasal, ticari veya mevzuat Microsoft 365 yüksek değerli içerikleri yöneten ancak nereden başlayacağından emin değil misiniz? Başlamaya yönelik bazı pratik kılavuzu okuyun.
ms.openlocfilehash: ba23aed20cbef05272bc33306df5fc1eebc6cb3f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010838"
---
# <a name="get-started-with-records-management"></a>Kayıt yönetimiyle çalışmaya başlama

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Microsoft 365'da kayıt yönetimi çözümü kullanarak yasal, ticari veya yasal düzenlemelere yönelik yüksek değerli içeriğini yönetmeye başlamaya hazır mısınız? Kullanmaya başlama için aşağıdaki kılavuzu kullanın:

1. **Bekletme ve silme** işlemlerinin Microsoft 365 anlayın ve belgeleri ve e-postaları öğe düzeyinde yöneten bekletme etiketlerini tamamlayıcı şekilde bekletme ilkeleri kullanmak zorunda olup olmadığılarınızı belirleme: Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi [edinin](retention.md)
    
    Gerekirse, iş [yükleri genelinde verilerin](create-retention-policies.md) temel yönetimi için bekletme Microsoft 365 oluşturun.
    
2. **Kayıt yönetimi çözümünü anlama ve** belgeler ve e-postalar kayıt olarak bildirilen eylemlere izin vermek veya bunu engellemek için bekletme etiketlerinin nasıl kullanılabiliyor: [Kayıt yönetimi hakkında bilgi edinin](records-management.md)

3. **Bekletme ve** silme ayarları ile eylemleri için dosya planınızı oluşturun ve varsa var olan bir planı içeri aktararak öğelerin kayıt olarak işaretlenirken ne zaman yeni bekletme etiketleri oluşturması gerektiğini seçin: Bekletme etiketlerini oluşturmak ve yönetmek için dosya planı [kullanma](file-plan-manager.md)

4. **Bekletme etiketlerinizi yayımlayın ve uygulama**. Bekletme etiketleri, birden çok ilkede değiştirilebilir ve kullanıcı iş akışlarıyla birleştirilebilirler:

    - [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)
    - [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)

Bu adımlardan **bağımsız olarak,** sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından veri içeren üçüncü taraf verilerini içeri ve arşivlemek için bağlayıcıları kullanın. Bu veriler çevrimiçi posta kutularına aktarıldıklarında, yalnızca Microsoft 365 Uyumluluk'tan kayıt yönetimini değil, iletişim uyumluluğu, insider risk yönetimi ve eKbulma gibi diğer uyumluluk çözümlerini de destekler. Daha fazla bilgi için bkz[. Üçüncü taraf verilerine ilişkin bağlayıcılar hakkında bilgi.](archiving-third-party-data.md)

## <a name="subscription-and-licensing-requirements"></a>Abonelik ve lisans gereksinimleri

Birkaç farklı abonelik kayıt yönetimini ve kullanıcıların lisans gereksinimlerini kullandığınız özelliklere göre destekler.

Uyumluluk özelliklerinden yararlanmak için kullanıcılarınızı lisanslama Microsoft 365 görmek için, güvenlik Microsoft 365 uyumluluğu için lisanslama & [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Kayıt yönetimi için, özellik [düzeyi lisans gereksinimleri için](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) Kayıt Yönetimi bölümüne ve ilgili PDF indirmesine bakın.

## <a name="permissions"></a>İzinler

Kayıt yönetiminden sorumlu olan uyumluluk ekibimizin üyelerinin kayıt ekibi üzerinde izinleri <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>. Varsayılan olarak, kiracı yöneticisinin (genel yönetici) bu konuma erişimi vardır ve uyumluluk görevlilerine ve diğer kullanıcılara, tüm kiracı yöneticisinin izinlerini vermeden erişim izni vetir. Sınırlı bir yönetim için izinler vermek üzere, kullanıcıları Kayıt Yönetimi yönetici rolü grubuna eklemenizi öneririz. Bu grup, incelemeyi inceleme ve doğrulama da içinde olmak üzere kayıt yönetimiyle ilgili tüm [özelliklere izinler sağlar](disposition.md).

Salt okunur bir rol için, yeni bir rol grubu oluşturabilir ve bu gruba Yalnızca **Görüntüleme Kayıt Yönetimi** rolünü eklersiniz.

Kullanıcıları varsayılan rollere ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için [bkz. Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca kayıtları bildiren bekletme etiketleri oluşturmak, yapılandırmak ve uygulamak ve yok olmak üzere yönetmek için gereklidir. Bu etiketleri yapılandıran kişinin içeriğe erişmesi gerekli değildir.

## <a name="common-scenarios"></a>Yaygın senaryolar

İş gereksinimlerinizi kayıt yönetimi tarafından desteklenen senaryolara eşlemenize yardımcı olmak için aşağıdaki tabloyu kullanın.

> [!TIP]
> Belirli bir endüstri düzenlemelerine uymamız mı gerekiyor? [Düzenlemeye özgü rehberlik için bilgi idaresi ve kayıt yönetimiyle](retention-regulatory-requirements.md) ilgili mevzuat gereksinimlerini kontrol edin.

|Yapmak istiyorum...|Belgeler|
|----------------|---------------|
|Kayıt bildir |[Bekletme etiketlerini kullanarak kayıtları bildir](declare-records.md)|
|Kaydı güncelleştirme |[SharePoint veya başka bir sürümde depolanan kayıtları güncelleştirmek OneDrive](record-versioning.md)|
|Yöneticilerin ve kullanıcıların belgeler ve e-postalar için tutma ve silme eylemlerini el ile uygulamalarına izin verme: <br />- SharePoint <br />- OneDrive <br />- Outlook ve Web üzerinde Outlook|[Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)|
|Site yöneticilerinin bir kitaplık, klasör veya belge kümesinde yer alan tüm içerik için varsayılan SharePoint eylemleri ayarlamasına ve silmesine izin verme|[Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)|
|Kullanıcıların, e-posta kurallarını kullanarak e-postalarda tutma ve silme eylemlerini otomatik Outlook verme|[Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)|
|Yöneticilerin, belge anlama modeli için gerekli koruma ve silme eylemlerini uygulamalarına izin verme, böylelikle bu eylemlerin belge kitaplığında tanımlanan belgelere otomatik SharePoint sağlar|[Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)|
|Belgeleri ve e-postaları tutma ve silme eylemlerini otomatik olarak uygulama |[İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)|
|Bekletme dönemini, bir olay oluştuğunda başlatma:  <br />- Çalışanlar kuruluşdan ayrılmayı sağlar <br />- Sözleşmeler sona erer <br />- Kullanım ömrü sonu| [Bir olay oluştuğunda bekletmeyi başlatma](event-driven-retention.md)|
|Yasal düzenleme gereksinimlerini karşılamaya veya yönetici yöneticilerini korumaya yardımcı olmak için ilkelerde yapılan değişiklikleri kısıtlama| [Bekletme ilkelerine ve bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Saklama Kilidi'i kullanma](retention-preservation-lock.md)
|Farklı belge türlerinde yaşam döngüsünü SharePoint| [Başka bir veritabanında depolanan belgelerin yaşam döngüsünü yönetmek için bekletme SharePoint](auto-apply-retention-labels-scenario.md)|
|Bekletme süresi sonunda içerik silinmeden önce, gözden birinin incelemesini ve onaylamasını emin olun|[İncelemeleri incelemeyi inceleme](disposition.md#disposition-reviews) |
|Bekletme döneminin sonunda kalıcı olarak silinen içerik için saklama kanıtı sağlama|[Kayıtların yok olarak kaydın yokğları](disposition.md#disposition-of-records) |
| Öğelerin nasıl ve nerede tutma ve silme ayarlarının uygulandığını izleme | [Bekletme etiketlerini izleme](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

Temel veri idaresi için bekletme ilkeleri kullanıyorsanız, bunlar normalde kullanıcı etkileşimi olmadan arka planda çalışmadan çalışır. Sonuç olarak, kullanıcılar için çok az belgeye ihtiyaçları olur. Kullanıcılara bekletme Teams bekletme ilkeleriyle ilgili iletilerine bağlantı içeren bir bağlantıyla [silindiğinde Teams hakkında bilgi sağlar](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Buna göre, bekletme etiketlerinin Microsoft 365 uygulamalarınızda kullanıcı arabirimi iletişim durumu söz konusu olduğundan, bu etiketlerin üretim ağınıza dağıtılmasından önce son kullanıcılar ve yardım masanız için kılavuz sağlamak istediğinizden emin olun. Kullanıcıların SharePoint ve OneDrive'da bekletme etiketleri uygulamanıza yardımcı olmak ve düzenleme için kayıtların kilidini açma hakkında bilgi için bkz. SharePoint veya [OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Bununla birlikte, en etkili son kullanıcı belgeleri, seçtiğiniz bekletme etiketi adları ve yapılandırmaları için size yol gösterici yönergeler ve yönergeler olarak sağlanmıştır. Kullanıcılarınızı eğitmenize yardımcı olmak için kullanabileceğiniz aşağıdaki sayfaya ve indirmelere bakın: [Bekletme Etiketleri için Son Kullanıcı Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
