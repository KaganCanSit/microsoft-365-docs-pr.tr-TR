---
title: Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın
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
description: Kuruluşunuzun verilerini yönetmeye başlamaya hazırsınız, ancak nereden başlayacağınızdan emin değil misiniz? Başlamak için bazı açıklayıcı yönergeleri okuyun.
ms.openlocfilehash: c5b9e931e2ab822a4d888b775de9fb8fa2acb13b
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972375"
---
# <a name="get-started-with-data-lifecycle-management"></a>Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Tutmanız gereken içeriği koruyarak ve tutmadığınız içeriği silerek kuruluşunuzun verilerini yönetmeye başlamaya hazır mısınız? Başlamak için Microsoft Purview Veri Yaşam Döngüsü Yönetimi (eski adıyla Microsoft Information Governance) için aşağıdaki kılavuzu kullanın:

1. **Bekletme ve silmenin Microsoft 365 nasıl çalıştığını anlayın** ve ardından bekletme ilkesi gerektiren iş yüklerini ve özel durumlar için bekletme etiketleri oluşturmanız gerekip gerekmediğini belirleyin: [Bekletme hakkında bilgi edinin](retention.md)
    
    > [!NOTE]
    > İş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri yönetmeniz gerekiyorsa: Veri yaşam döngüsü [yönetimi yerine kayıt yönetimiyle](records-management.md) bekletme etiketlerini kullanın.

2. Belirlediğiniz iş yükleri için **bekletme ilkeleri oluşturma**, kuruluş ilkelerinizin veya sektör düzenlemelerinizin gerektirdiği saklama ayarlarını ve eylemleri belirtme: [Bekletme ilkeleri oluşturma](create-retention-policies.md)
    
    Gerekirse, [özel durumlarınız için bekletme etiketleri oluşturun ve uygulayın](create-retention-labels-information-governance.md).

3. Kullanıcılara ek posta kutusu depolama alanı sağlamak için posta **kutusu arşivlemeyi etkinleştirme**: [Microsoft Purview uyumluluk portalında arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md)
    
    Arşiv posta kutularını desteklemek için gerekirse:
    
    - 100 GB'tan fazla depolama alanı gerektiren posta kutuları için [otomatik genişletme arşivlemeyi etkinleştirin](enable-autoexpanding-archiving.md).
    
    - E-postaların kullanıcının birincil posta kutusundan otomatik olarak arşiv posta kutusuna nasıl taşınacağını özelleştirmeniz gerekiyorsa veya posta kutusunun tamamı yerine belirli klasörler için bekletme ve silme ayarlarını belirtmeniz gerekiyorsa, [mesajlaşma kayıtları yönetiminden (MRM) elde tutma ilkesiyle bekletme etiketlerini](set-up-an-archive-and-deletion-policy-for-mailboxes.md) kullanın.

4. Çalışanlar kuruluştan ayrıldıktan sonra posta kutusu içeriğini koruyan **etkin olmayan posta kutularını anlama ve yönetme**: [Etkin olmayan posta kutuları hakkında bilgi edinin](inactive-mailboxes-in-office-365.md)

5. Yönetmek istediğiniz verileri içeren PST dosyalarınız varsa: Pst dosyalarını ağ yükleme veya sürücü gönderimini kullanarak **çevrimiçi posta kutularına aktarma** : [Kuruluşunuzun PST dosyalarını içeri aktarma hakkında bilgi edinin](importing-pst-files-to-office-365.md)

## <a name="subscription-and-licensing-requirements"></a>Abonelik ve lisans gereksinimleri

Bir dizi farklı abonelik, veri yaşam döngüsü yönetimi özelliklerini destekler.

Kullanıcılarınızın Microsoft Purview özelliklerinden yararlanması için lisanslama seçeneklerini görmek [için güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzuna](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) bakın. Bu sayfada listelenen özellikler için özellik düzeyi lisanslama gereksinimleri için [Microsoft Purview Veri Yaşam Döngüsü Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management) bölümüne ve ilgili [PDF indirme](https://go.microsoft.com/fwlink/?linkid=2139145) bölümüne bakın.

## <a name="permissions"></a>İzinler

Microsoft 365 saklamayı yönetecek roller ve rol grupları hakkında bilgi için aşağıdaki bölüme bakın.

Arşivleme, etkin olmayan posta kutuları ve içeri aktarma için posta kutularını yönetme izinleri için, bunlar genellikle Posta Alıcıları rolü gibi Exchange izinleri gerektirir. Varsayılan olarak, bu rol Alıcı Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Her yönetim görevi için tam izin gereksinimi için yönetici yönergelerine eşlik eden belgelere bakın.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri için izinler

Bekletme ilkeleri ve bekletme etiketleri oluşturacak ve yönetecek uyumluluk ekibinizin üyelerinin <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalında</a> izinlere sahip olması gerekir. Varsayılan olarak, kiracı yöneticisinin (genel yönetici) bu konuma erişimi vardır ve uyumluluk görevlilerine ve diğer kişilere kiracı yöneticisinin tüm izinlerini vermeden erişim verebilir. Bu sınırlı yönetim için izinler vermek için, kullanıcıları **Uyumluluk Yöneticisi** yönetici rol grubuna eklemenizi öneririz.

Alternatif olarak, bu varsayılan rolü kullanmak için yeni bir rol grubu oluşturabilir ve **Bekletme Yönetimi** rolünü bu gruba ekleyebilirsiniz. Salt okunur bir rol için **Yalnızca Görüntüleme Bekletme Yönetimi'ni** kullanın. 

Varsayılan rollere kullanıcı ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için bkz. [Microsoft Purview uyumluluk portalında İzinler](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca bekletme ilkeleri ve bekletme etiketleri oluşturmak, yapılandırmak ve uygulamak için gereklidir. Bu ilkeleri ve etiketleri yapılandıran kişinin içeriğe erişmesi gerekmez.

## <a name="common-scenarios"></a>Yaygın senaryolar

İş gereksinimlerinizi veri yaşam döngüsü yönetimi için en yaygın senaryolarla eşlemenize yardımcı olması için aşağıdaki tabloyu kullanın.

|Yapmak istiyorum...|Belge|
|----------------|---------------|
|Microsoft 365 hizmetleri için verileri verimli bir şekilde saklama veya silme: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Microsoft 365 Grupları <br />- Teams <br />- Yammer <br />- Skype Kurumsal |[Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)|
|Kullanıcılara ek posta kutusu depolama alanı sağlama |[Microsoft Purview uyumluluk portalında arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md)|
|Çalışanlar kuruluştan ayrıldıktan sonra posta kutusu verilerini saklama |[Etkin olmayan posta kutuları oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md)|
|PST dosyalarından posta kutusu verilerini Upload |[PST dosyalarını içe aktarmak için ağ yüklemesini kullanma](use-network-upload-to-import-pst-files.md)|


Tek tek öğelerin veri yönetimini gerektiren bir senaryonuz varsa, [kayıt yönetimi için yaygın senaryolara](get-started-with-records-management.md#common-scenarios) bakın. 

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

Microsoft 365 saklamayı desteklemek için son kullanıcı belgeleri hakkında bilgi için aşağıdaki bölüme bakın.

Posta kutusu yönetimini destekleyen veri yaşam döngüsü yönetimi özellikleri (arşivleme, etkin olmayan posta kutuları ve içeri aktarma) genellikle son kullanıcı belgeleri gerektirmez.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Saklama ve silme için son kullanıcı belgeleri

Bekletme ilkelerinin çoğu kullanıcı etkileşimi olmadan arka planda göze çarpmadan çalışır ve bu nedenle kullanıcılar için çok az belge gerekir. Teams için bekletme ilkeleri, iletileri silindiğinde kullanıcıları [bekletme ilkeleri hakkında Teams](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b) bir bağlantıyla bilgilendirebilir.

Ancak bekletme ilkelerine bekletme etiketleri eklerseniz, bu etiketlerin Microsoft 365 uygulamalarında bir kullanıcı arabirimi varlığı vardır. Bu etiketleri üretim ağınıza dağıtmadan önce, son kullanıcılar ve yardım masanız için bilgi ve yönergeler sağladığınızdan emin olun. Kullanıcıların SharePoint ve OneDrive bekletme etiketlerini uygulamasına yardımcı olmak için bkz. [SharePoint veya OneDrive dosyalara bekletme etiketleri uygulama](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

En etkili son kullanıcı belgeleri her zaman seçtiğiniz bekletme etiketi adları ve yapılandırmaları için sağladığınız özelleştirilmiş yönergeler ve yönergeler olacaktır. Kullanıcılarınızı eğitmek için kullanabileceğiniz şu sayfaya ve indirmelere bakın: [Bekletme Etiketleri için Son Kullanıcı Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

