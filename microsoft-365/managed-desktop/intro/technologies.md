---
title: Microsoft Managed Desktop teknolojileri
description: Bu makalede, Microsoft Managed Desktop'de kullanılan teknolojiler ve uygulamalar listelenir.
keywords: Microsoft Managed Desktop, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d7a7b6889451d83aaa6c2b53c1dce6ed035f9916
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945637"
---
# <a name="microsoft-managed-desktop-technologies"></a>Microsoft Managed Desktop teknolojileri

Bu makalede, Microsoft Managed Desktop'de kullanılan teknolojiler ve uygulamalar listelenir.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

tüm Microsoft Managed Desktop kullanıcıları için Microsoft 365 Kurumsal lisanslama gereklidir. Hizmetin lisans gereksinimleri hakkında daha fazla bilgi için bkz. [Microsoft Managed Desktop önkoşulları](../get-ready/prerequisites.md).

Bu makalede, gerekli Enterprise lisanslarına dahil edilen bileşenler ve hizmetin her bileşeni Microsoft Managed Desktop cihazlarla nasıl kullandığı özetlenmektedir. Her bir alan için belirli roller ve sorumluluklar Microsoft Managed Desktop belgelerde ayrıntılı olarak açıklanmıştır.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 veya E5

| Ürün | Bilgi |
| ----- | ----- |
| Kurumlar için Microsoft 365 Uygulamaları (64 bit) | Aşağıdaki Office uygulamaları cihazla birlikte gönderilir:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>Access</li><li>Skype Kurumsal</li><li>OneNote</li></ul><br>Microsoft Project ve Microsoft Visio 64 bit tam sürümleri dahil değildir. Ancak, bu uygulamaların yüklenmesi Enterprise yükleme Microsoft 365 Uygulamaları bağlı olduğundan, Microsoft Managed Desktop bu uygulamaları dağıtmak için kullanabileceğiniz varsayılan Microsoft Intune dağıtımları ve güvenlik grupları oluşturdunuz lisanslı kullanıcılar. Daha fazla bilgi için bkz[. Microsoft Managed Desktop cihazlara Microsoft Project veya Microsoft Visio yükleme](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory Çoklu Oturum Açma, kullanıcılar OneDrive ilk kez oturum açtıklarında etkinleştirilir.<br><br>Masaüstü, Belge ve Resimler klasörleri için Bilinen Klasör Yeniden Yönlendirmesi eklenmiştir. Bu klasörler Microsoft Managed Desktop tarafından etkinleştirilir ve yapılandırılır. |
| Uygulamaları Depolama | Microsoft Sway ve Power BI cihazla birlikte gönderilmez. Bu uygulamalar Microsoft Store'den indirilebilir. |
| Win32 Uygulamaları | Teams cihazla birlikte gönderilmez, ancak Microsoft Managed Desktop cihazlar için Microsoft tarafından paketlenip sağlanır. Azure Information Protection İstemcisi cihazla birlikte gönderilmez, ancak bu istemciyi dağıtım için paketleyebilirsiniz. |
| Web Uygulamaları | Aşağıdaki web uygulamaları cihazla birlikte gönderilmez: <ul><li>Yammer</li><li>Tarayıcıda Office</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planner</li></ul> <br>Kullanıcılar bu uygulamaların web sürümüne tarayıcıyla erişebilir. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender ile E5 veya E3 Windows 10 Enterprise

BT yöneticilerinizin aşağıdaki ayarları yapılandırmalarını öneririz.

> [!NOTE]
> Bu ayarlar Microsoft Managed Desktop bir parçası olarak dahil değildir veya yönetilmiyor.

| Ürün | Bilgi |
| ----- | ----- |
| İş İçin Windows Hello | parolaları Microsoft Managed Desktop cihazlar için güçlü iki faktörlü kimlik doğrulamasıyla değiştirmek için İş İçin Windows Hello uygulamanız gerekir. Daha fazla bilgi için bkz. [İş İçin Windows Hello](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Uygulama Sanallaştırma | Intune Win32 uygulama yönetimi istemcisini kullanarak Uygulama Sanallaştırma (App-V) paketlerini dağıtabilirsiniz. Daha fazla bilgi için bkz. [Uygulama Sanallaştırma](/windows/application-management/app-v/appv-technical-reference). |
| Microsoft Purview veri kaybı önleme | Hassas olduğunu belirlediğiniz öğelerde gerçekleştirilen eylemleri izlemek ve bu öğelerin yanlışlıkla paylaşılmasını önlemeye yardımcı olmak için veri kaybı önleme uygulamanız gerekir. Daha fazla bilgi için bkz. [veri kaybı önleme](../../compliance/endpoint-dlp-learn-about.md). |

Microsoft Managed Desktop kapsamında dahil edilen ve yönetilen özellikler:

| Ürün | Bilgi |
| ----- | ----- |
| BitLocker Sürücü Şifrelemesi | BitLocker Sürücü Şifrelemesi tüm sistem sürücülerini şifrelemek için kullanılır. Daha fazla bilgi için bkz. [BitLocker Sürücü Şifrelemesi](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Başlangıçta sistemin bütünlüğünü korur ve sistem bütünlüğünün gerçekten korunduğunu doğrular. Daha fazla bilgi için bkz. [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender Credential Guard, gizli dizileri yalnızca ayrıcalıklı sistem yazılımlarının erişebilmesi için yalıtmak için Sanallaştırma tabanlı güvenlik kullanır. Daha fazla bilgi için bkz. [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Uç Nokta için Microsoft Defender - Uç Nokta Algılama ve Yanıt | Microsoft Managed Desktop Güvenlik İşlemleri uyarılara yanıt verir ve Uç Nokta Algılama ve Yanıt kullanarak tehditleri düzeltmek için eylemde bulunur. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Uç Nokta Algılama ve Yanıt](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Uç Nokta için Microsoft Defender - Tehdit Uzmanları | Microsoft Managed Desktop, hedeflenen saldırı bildirimleri aracılığıyla Tehdit Uzmanları içgörüleri ve verileriyle tümleşir. Bu hizmet etkinleştirilmeden önce ek onay vermeniz gerekir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Tehdit Uzmanları](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Uç Nokta için Microsoft Defender - Tehdit ve Güvenlik Açığı Yönetimi | Microsoft Managed Desktop hizmet planında gelecekte kullanmak için gereklidir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Tehdit ve Güvenlik Açığı Yönetimi](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Uç Nokta için Microsoft Defender - Saldırı Yüzeyini Azaltma | Saldırganlar tarafından sıklıkla kötüye kullanılabilecek riskli yazılım davranışlarını hedefler. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Saldırı Yüzeyini Azaltma](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Uç Nokta için Microsoft Defender - Exploit Protection | Cihazlara bulaşmak için kötüye kullanım kullanan kötü amaçlı yazılımlara karşı koruma sağlar ve işletim sistemi süreçlerine ve uygulamalarına açıklardan yararlanma azaltma tekniklerini otomatik olarak uygulayarak yayılır. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Uç Nokta için Microsoft Defender - Ağ Koruması | Düşük saygınlık kaynaklarına bağlanmaya çalışan tüm giden HTTP ve HTTPS trafiğini engellemek için Microsoft Defender SmartScreen kapsamını genişletir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Ağ Koruması](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Microsoft Defender Kurcalama Koruması | Windows Kurcalama Koruması, virüsten koruma gibi güvenlik ayarlarının değiştirilmesini önlemek için kullanılır. Daha fazla bilgi için bkz. [Microsoft Defender Kurcalama Koruması](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Microsoft Defender Virüsten Koruma Davranış tabanlı, buluşsal ve gerçek zamanlı virüsten koruma | Kötü amaçlı yazılım olarak algılanmayabilecek dosya ve işlem tehditlerini taramak için her zaman açık. Daha fazla bilgi için bkz. [davranış tabanlı, buluşsal ve gerçek zamanlı virüsten koruma Microsoft Defender Virüsten Koruma](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| Microsoft Defender Virüsten Koruma Bulut Tabanlı Koruma | Yeni ve yeni ortaya çıkan tehditlere karşı neredeyse anında ve otomatik olarak dinamik koruma sağlar. Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma Cloud-delivered Protection](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Uç Nokta için Microsoft Defender - "İlk görüşte engelle" | Windows şüpheli veya bilinmeyen bir dosya algıladığında yeni kötü amaçlı yazılımların algılanması ve engellenmesi sağlar. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - İlk bakışta engelle](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| İstenmeyebilecek Uygulamaları Microsoft Defender Virüsten Koruma | Makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya en kötü ihtimalle beklenmeyen veya istenmeyen olabilecek diğer yazılımları yüklemesine neden olabilecek uygulamaları engellemek için kullanılır. Daha fazla bilgi için bkz. [İstenmeyebilecek Uygulamalar Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| Gelişmiş Güvenlik özellikli Windows Defender Güvenlik Duvarı | Bir cihaz için konak tabanlı, iki yönlü ağ trafiği filtreleme Windows Defender Güvenlik Duvarı, yerel cihaza gelen veya giden yetkisiz ağ trafiğini engeller. Daha fazla bilgi için bkz[. Gelişmiş Güvenlik özellikli güvenlik duvarı Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| Kullanıcı Hesabı Denetimi | Kullanıcı Hesabı Denetimi, bir görev veya eylem yönetici hesabı türü erişim gerektirdiğinde Güvenli Masaüstü'ne geçer. Microsoft Managed Desktop kullanıcılara kayıt sırasında Standart kullanıcı erişimi atanır. Daha fazla bilgi için bkz. [Kullanıcı Hesabı Denetimi](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Ürün | Bilgi |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | MDM cihazlarını yönetmek için Enterprise Mobility + Security E3 tüm özelliklerini kullanabilirsiniz.<br><br>Microsoft Managed Desktop ile isteğe bağlı bir özellik olarak Azure Active Directory Premium P2 kullanabilirsiniz. |
| Bulut Uygulamaları için Microsoft Defender | bu isteğe bağlı özelliği Microsoft Managed Desktop ile kullanabilirsiniz.
| Azure Information Protection P2  | bu isteğe bağlı özelliği Microsoft Managed Desktop ile kullanabilirsiniz.
