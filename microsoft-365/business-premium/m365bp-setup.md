---
title: Ayarlama Microsoft 365 İş Ekstra
description: E-Microsoft 365 İş Ekstra'i ayarlamayı Microsoft 365 İş Ekstra
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b6f187f93e8a135bfb67c78509553d2963b011b
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705642"
---
# <a name="set-up-microsoft-365-business-premium"></a>Ayarlama Microsoft 365 İş Ekstra

Bu ayarları yapılandırmak ve yapılandırmak için çeşitli seçenekleriniz Microsoft 365 İş Ekstra. Şunları yapabilirsiniz:

- [Temel kurulum ve yapılandırma için rehberli kurulum deneyimi kullanma](#guided-process-for-basic-setup)
- [İş ortağı, örneğin bir Microsoft Bulut Çözümü Sağlayıcısı (CSP) ile çalışma](#work-with-a-microsoft-partner)
- [Kurulum işlemiyle el ile çalışma](#manual-setup-and-configuration)


Bu makaleyi kılavuz olarak kullanın.

## <a name="guided-process-for-basic-setup"></a>Temel kurulum için rehberli işlem

Microsoft 365 İş Ekstra kurulum için yönlendiren bir işlem içerir. Bu görevler arasında özel bir etki alanına bağlanma, kullanıcı ekleme, lisans atama, Outlook cihazlarına yükleme, veri koruma ayarlarını gözden geçirme ve mobil uygulama koruma ilkesi uygulama görevleri yer almaktadır. 

Rehberli kurulumun nasıl çalıştığını görmek için aşağıdaki videoyu izleyin: <br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

Rehberli kurulumu tamamlandıktan sonra, güvenlik ve uyumluluk yeteneklerinizin düzgün bir şekilde ayarlandıktan ve uygulandığıktan emin olmak için tamamlamanız gereken ek adımlar vardır. Söz konusu adımlar şunlardır:

- [Cihaz Windows güvenliğini sağlama](m365bp-secure-windows-devices.md)
- [Uygulama Microsoft 365 dağıtma](../admin/setup/install-applications.md)
- [Yeni İş için Defender yeteneklerinizi ayarlama ve yapılandırma](../security/defender-business/mdb-setup-configuration.md)

[Rehberli kurulum işlemi ile Kurulum sayfası arasındaki farklar hakkında daha fazla bilgi edinebilirsiniz](../admin/setup/o365-setup-wizard-and-setup-page.md).

> [!TIP]
> E-tablo ayarlarını ve yapılandırma hakkında daha fazla ayrıntı için aşağıdaki Microsoft 365 İş Ekstra.


## <a name="work-with-a-microsoft-partner"></a>Bir Microsoft iş ortağıyla çalışma

Microsoft'un teklif satışı için yetkili çözüm sağlayıcılarının listesi vardır ve bu sağlayıcılar da Microsoft 365 İş Ekstra. 

Bölgenize çözüm sağlayıcısı bulmak için aşağıdaki adımları izleyin:

1. **Microsoft Çözüm Sağlayıcıları sayfasına** () gidin [https://www.microsoft.com/solution-providers](https://www.microsoft.com/solution-providers).
 
2. Arama kutusunda, konum ve şirket boyutunu doldurun. 

3. Ürün **, hizmet, beceri, endüstri ara kutusuna ,** ve ardından `Microsoft 365`Git'i **seçin**.

4. Sonuç listesini gözden geçirme. Uzmanlıkları ve sağ yaptıkları hizmetler hakkında daha fazla bilgi edinmek için bir sağlayıcı seçin.

Ayrıca bkz [. İş ortağınızı veya satıcınızı bulma](../admin/manage/find-your-partner-or-reseller.md).

## <a name="manual-setup-and-configuration"></a>El ile kurulum ve yapılandırma

Kurulum ve yapılandırma işleminizi el ile tamamlamayı tercih ediyorsanız, kılavuz olarak aşağıdaki tabloyu kullanın:

| Aşama  | Görev  | Daha fazla bilgi edinmek için kaynaklar  |
|---------|---------|---------|
| **Planlama**     | Kurulum ve yapılandırma işleminizi planlama  | [Microsoft 365 Kurumsal kurulumlarınızı planlama](../admin/setup/plan-your-setup.md)   |
|  | Gereksinimleri gözden geçirme | [Microsoft 365 İş Ekstra gereksinimleri](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:overviewtab) |
| **Temel kurulum**     | Özel alan adı gibi özel `rob@contoso.com` bir Microsoft 365 | [Postanıza etki Microsoft 365](../admin/setup/add-domain.md) |
|      | Posta'da kullanıcı ekleme ve lisans Microsoft 365      | [Kullanıcıları ekleme ve lisansları aynı anda atama](../admin/add-users/add-users.md)        |
|  | Aşağıdakiler gibi belirli işlevleri gerçekleştirecek kullanıcılara yönetici rolleri attayabilirsiniz: <br/>- Özellikleri yönetme<br/>- Kullanıcı hesaplarını yönetme<br/>- Cihazları yönetme<br/>- Kuruluş güvenlik ve uyumluluk bilgilerini görüntüleme veya yönetme | [Yönetici rolleri hakkında bilgi](../admin/add-users/about-admin-roles.md) <br/><br/> [Yönetici rollerini atama](../admin/add-users/assign-admin-roles.md)  |
|  | Sözcük Microsoft 365 Uygulamaları (Word, Excel, PowerPoint gibi) yükleme | [Office uygulamalarını yükleme](../admin/setup/install-applications.md) |
| **Kuruluş güvenliğini sağlama** | Microsoft 365 aboneliğinizin güvenliğini sağlamak için son 10 Microsoft 365 bakın |  [kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Başka bir e-postada oturum aken herkesin ek bir doğrulama yöntemi Microsoft 365 | [Çok faktörlü kimlik doğrulamasını ayarlama](../admin/security-and-compliance/set-up-multi-factor-authentication.md) | 
| **E-postayı ve içeriği koruma** |  Kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarına ve diğer kimlik avı saldırılarına karşı korunmak için gelişmiş kimlik avı korumasını ayarlama | [E-postanızı kimlik avı saldırılarından koruma](../admin/security-and-compliance/secure-your-business-data.md) |
|   | E-Kasa kötü amaçlı e-posta eklerinden korumak için Ekleri Ayarlama | [Dosya Ekleriyle kötü amaçlı eklere ve Kasa koruma](../admin/security-and-compliance/secure-your-business-data.md) |
|  | E-Kasa iletilerde ve diğer belgelerde kötü amaçlı web sitelerine (URL) karşı korumak için Office ayarlama | [Bağlantı Kasa ayarlama](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Hassas bilgilerin paylaşılmalarını önlemek için veri kaybı önleme ilkelerini ayarlama | [Uyumluluk özelliklerini ayarlama](../admin/security-and-compliance/set-up-compliance.md) |
| **Cihazları yönetme ve koruma** | Kuruluş cihazlarının güvenliğini Windows sağlama | [Mobil Windows güvenliğini sağlama](m365bp-secure-windows-devices.md) <br/><br/>[Cihazlar için uygulama koruma ayarlarını Windows 10 düzenleme](../admin/devices/protection-settings-for-windows-10-devices.md) |
|   | Mobil Microsoft 365 uygulamaların güvenliğini sağlama | [Android veya iOS cihazlara yönelik uygulama koruma ayarlarını belirleme](../admin/devices/app-protection-settings-for-android-and-ios.md) |
|  | İş için Microsoft Defender'ı ayarlama (kiracınız için uygun olduğunda) | [İş için Microsoft Defender'a genel bakış](../security/defender-business/mdb-overview.md)<br/><br/>[İş için Defender'ı ayarlamak için sihirbazı kullanma](../security/defender-business/mdb-use-wizard.md) |
| **Dosya depolama ve içeriğigrat** | Dosya depolamayı ayarlama ve paylaşımın kurum için nasıl çalışması | [Dosya depolamayı ve dosya paylaşımını Microsoft 365](../admin/setup/set-up-file-storage-and-sharing.md) |
| | E-postayı ve kişileri içeri aktarma veya geçirme | [E-postayı ve kişileri başka bir Microsoft 365](../admin/setup/migrate-email-and-contacts-admin.md) |
|  | Herkesin erişmesi gereken şirket dosyalarını taşıma SharePoint (SharePoint çoğunlukla dosya paylaşımı veya ağ sürücüsü kullanımının yerini almaktadır) | [Dosyaları başka bir yere SharePoint](../admin/setup/files-to-sharepoint.md) |
|  | Kişisel iş dosyaları veya hassas iş dosyaları gibi mevcut iş dosyalarınızı başka bir OneDrive | [Dosyaları başka bir yere OneDrive](../admin/setup/files-to-onedrive.md) |
| **Eğitim yöneticileri ve güvenlik ekipleriniz** | Yönetim merkezini kullanmayı öğrenin | [Genel bakış Microsoft 365 yönetim merkezi](../admin/admin-overview/admin-center-overview.md) |
|  | Bu yöneticiler için ücretsiz eğitim Microsoft 365 kitaplığını kullanma | [Yönetici eğitimi video kitaplığı](../admin/admin-video-library.yml)  |
|  | Microsoft 365 Defender portalını kullanmayı öğrenin ([https://security.microsoft.com](https://security.microsoft.com)) | [Microsoft 365 Defender portalını kullanmaya başlama](../security/defender-business/mdb-get-started.md) |

> [!TIP]
> Yardıma mı ihtiyacınız var? Daha fazla yardım [için İş Yardımı'Microsoft 365](https://support.microsoft.com/en-us/office/business-assist-for-microsoft-365-37deb8fe-61cc-4cf9-9ad1-1c8d93475070)

## <a name="see-also"></a>Ayrıca bkz.

- [İş için Microsoft Defender'a genel bakış](../security/defender-business/mdb-overview.md) (artık Microsoft 365 İş Ekstra!)

- [İş abonelikleri ve faturalama belgeleri](../commerce/index.yml)

- [Genel bakış Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md) (Microsoft CSP'ler için)

- [kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](../admin/security-and-compliance/secure-your-business-data.md)
