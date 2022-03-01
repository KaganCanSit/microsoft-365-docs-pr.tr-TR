---
title: Web'de bilgi yönetimiyle çalışmaya Microsoft 365
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
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Kuruluşun verilerini yönetmeye başlamaya hazır mısınız, ancak nereden başlayacağınıza emin değil misiniz? Başlamaya yönelik bazı önkser kılavuzu okuyun.
ms.openlocfilehash: 5b30dc870389c06bd006a056127439f1ec18ac65
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010833"
---
# <a name="get-started-with-information-governance"></a>Bilgi yönetimiyle çalışmaya başlama

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Tutmanız gereken içeriği saklayarak ve sizin olmadığınız içeriği silerek, kuruluş verilerinizi yönetmeye başlamaya hazır mısınız? Kullanmaya başlama için aşağıdaki kılavuzu kullanın:

1. **Bekletme ve silme** işlemlerinin Microsoft 365 çalıştığını anlama ve bekletme ilkesine gerek olan iş yüklerini ve özel durumlar için bekletme etiketleri oluşturmanız gerekip gerekip gerek olmadığını belirleme: Bekletme [hakkında bilgi öğrenin](retention.md)
    
    > [!NOTE]
    > İşletmeler, yasal veya yasal düzenlemelere yönelik kayıt tutma gereksinimleri için yaşam döngüsü yönetimine ihtiyacınız varsa: Bilgi yönetimi yerine kayıt yönetimiyle bekletme [](records-management.md) etiketlerini kullanın.

2. **Tanım döneminiz** iş yükleri için bekletme ilkeleri oluşturun ve bekletme ayarlarını ve kuruluş ilkeleriniz veya endüstri yasal düzenlemeleri için gereken eylemleri [belirtin: Bekletme ilkeleri oluşturma](create-retention-policies.md)
    
    Gerekirse, özel [durumlar için bekletme etiketleri oluşturun ve bu etiketleri kullanın](create-retention-labels-information-governance.md).

3. **Kullanıcılara ek posta kutusu** depolama alanı sağlamak için posta kutusu arşivlemeyi etkinleştirme: [Uyumluluk merkezinde arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md)
    
    Arşiv posta kutularını desteklemek için gerekirse:
    
    - 100 [GB'den](enable-autoexpanding-archiving.md) fazla depolama alanı olan posta kutuları için otomatik genişleyen arşivlemeyi etkinleştirin.
    
    - E-postaların kullanıcının birincil posta kutusundan arşiv posta kutusuna otomatik olarak taşınmalarını özelleştirmeniz veya posta kutusunun tamamı yerine belirli klasörler için bekletme ve silme ayarlarını belirtmeniz gerekirse, bekletme etiketlerini ileti kayıt yönetiminden [(MRM)](set-up-an-archive-and-deletion-policy-for-mailboxes.md) bir bekletme ilkesiyle kullanın.

4. **Çalışanlar kuruluşdan ayrıldıktan sonra posta kutusu** içeriğini koruyarak etkin olmayan posta kutularını anlama ve yönetme: Etkin olmayan [posta kutuları hakkında bilgi alın](inactive-mailboxes-in-office-365.md)

5. Geçerlik istediğiniz verileri içeren PST dosyalarınız varsa: Ağ karşıya yükleme veya sürücü gönderimini kullanarak **PST** dosyalarını çevrimiçi posta kutularına aktarma: Kuruluş PST dosyalarını içeri aktarma [hakkında bilgi alın](importing-pst-files-to-office-365.md)

Bu adımlardan **bağımsız olarak,** sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından veri içeren üçüncü taraf verilerini içeri ve arşivlemek için bağlayıcıları kullanın. Bu veriler çevrimiçi posta kutularına aktarıldı mı? Yalnızca Microsoft 365 Uyumluluğu'dan bilgi yönetimini değil, iletişim uyumluluğu, insider risk yönetimi ve eKbulma gibi diğer uyumluluk çözümlerini de destekler. Daha fazla bilgi için bkz[. Üçüncü taraf verilerine ilişkin bağlayıcılar hakkında bilgi.](archiving-third-party-data.md)

## <a name="subscription-and-licensing-requirements"></a>Abonelik ve lisans gereksinimleri

Birkaç farklı abonelik bilgi idaresi özelliklerini destekler.

Uyumluluk özelliklerinden yararlanmak için kullanıcılarınızı lisanslama Microsoft 365 görmek için, güvenlik Microsoft 365 uyumluluğu için lisanslama & [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Bu sayfada listelenen özellikler için, özellik düzeyi lisans gereksinimleri [için](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) Bilgi Yönetimi bölümüne ve ilgili [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) indirmesine bakın.

## <a name="permissions"></a>İzinler

Bekletmeyi yönetmeye yardımcı olacak roller ve rol grupları hakkında bilgi Microsoft 365 bakın.

Posta kutularını arşivleme, etkin olmayan posta kutuları ve içeri aktarma için yönetme izinleri için, bunlar normalde Exchange Alıcıları rolü gibi izinler gerektirir. Varsayılan olarak, bu rol Alıcı Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Her yönetim görevi için tam izin gereksinimi için, yönetici yönergeleriyle birlikte gelen belgelere bakın.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri izinleri

Bekletme ilkelerini ve bekletme etiketlerini oluşturacak ve yönetecek uyumluluk ekibimizin üyeleri, bu uyumluluk <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi.</a> Varsayılan olarak, kiracı yöneticisinin (genel yönetici) bu konuma erişimi vardır ve uyumluluk görevlilerine ve diğer kullanıcılara, tüm kiracı yöneticisinin izinlerini vermeden erişim izni vetir. Bu sınırlı yönetim için izinler vermek için kullanıcıları Uyumluluk Yöneticisi yönetici **rol grubuna eklemenizi** öneririz.

Alternatif olarak, bu varsayılan rolü kullanarak yeni bir rol grubu oluşturabilir ve Bekletme Yönetimi **rolünü bu** gruba eklersiniz. Salt okunur bir rol için, Yalnızca **Görüntüleme Bekletme Yönetimi'ne tıklayın**. 

Kullanıcıları varsayılan rollere ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için [bkz. Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca bekletme ilkeleri ve bekletme etiketleri oluşturmak, yapılandırmak ve uygulamak için gereklidir. Bu ilkeleri ve etiketleri yapılandıran kişinin içeriğe erişimi olması gerekli değildir.

## <a name="common-scenarios"></a>Yaygın senaryolar

İş gereksinimlerinizi bilgi yönetimi için en yaygın senaryolara eşlemenize yardımcı olacak aşağıdaki tabloyu kullanın.

|Yapmak istiyorum...|Belgeler|
|----------------|---------------|
|E-posta hizmetleri için verileri verimli Microsoft 365 silme: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Microsoft 365 Grupları <br />- Teams <br />- Yammer <br />- Skype Kurumsal |[Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)|
|Kullanıcılara ek posta kutusu depolama alanı sağlama |[Uyumluluk merkezinde arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md)|
|Çalışanlar kuruluşdan ayrıldıktan sonra posta kutusu verilerini koruma |[Etkin olmayan posta kutuları oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md)|
|Upload kutusu verilerini PST dosyalarından içeri aktarma |[PST dosyalarını içeri aktarma için ağ karşıya yükleme kullanma](use-network-upload-to-import-pst-files.md)|


Tek tek öğeler için yaşam döngüsü yönetimi gerektiren bir senaryo varsa, kayıt [yönetimi için yaygın senaryolara bakın](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

Son kullanıcı belgeleri hakkında bilgi almak ve bekletmeyi desteklemek için Microsoft 365 bakın.

Posta kutusu yönetimini (arşivleme, etkin olmayan posta kutuları ve içeri aktarma) destekleyen bilgi yönetimi özellikleri normalde son kullanıcı belgeleri gerektirmez.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Bekletme ve silme için son kullanıcı belgeleri

Bekletme ilkelerinin çoğu, kullanıcı etkileşimi olmadan arka planda çalışmaz ve bu nedenle kullanıcılar için çok az belgeye ihtiyacınız olur. Kullanıcılara bekletme Teams bekletme ilkeleriyle ilgili iletilerine bağlantı içeren bir bağlantıyla [silindiğinde Teams hakkında bilgi sağlar](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Bununla birlikte, bekletme ilkelerini bekletme etiketleriyle tamamlarsanız, bu etiketlerin kullanıcı arabirimi iletişim Microsoft 365 olur. Bu etiketleri üretim ağınıza dağıtmadan önce, son kullanıcılar ve yardım masanız için bilgi ve yönergeler sağlamak istediğinizden emin olun. Kullanıcıların bekletme etiketlerini SharePoint ve OneDrive için bkz. SharePoint veya [OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

En etkili son kullanıcı belgeleri her zaman, seçtiğiniz bekletme etiketi adları ve yapılandırmaları için size yol gösterici yönergeler ve yönergeler olarak sağlanmıştır. Kullanıcılarınızı eğitmenize yardımcı olmak için kullanabileceğiniz aşağıdaki sayfaya ve indirmelere bakın: [Bekletme Etiketleri için Son Kullanıcı Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

