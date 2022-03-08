---
title: Microsoft Yönetilen Masaüstü teknolojileri
description: Bu makalede, Microsoft Yönetilen Masaüstü'nde kullanılan teknolojiler ve uygulamalar listelemektedir.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 302666c6b29d2cffd4db641509f14ba616cfd459
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314973"
---
# <a name="microsoft-managed-desktop-technologies"></a>Microsoft Yönetilen Masaüstü teknolojileri

Bu makalede, Microsoft Yönetilen Masaüstü'nde kullanılan teknolojiler ve uygulamalar listelemektedir.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Kurumsal Microsoft Yönetilen Masaüstü kullanıcıları için lisans gereklidir. Hizmetin lisans gereksinimleri hakkında daha fazla bilgi için bkz. Microsoft Yönetilen Masaüstü [için önkoşullar](../get-ready/prerequisites.md).

Bu makalede, gerekli lisanslara dahil edilen bileşenler Enterprise ve hizmetin Microsoft Yönetilen Masaüstü cihazlarıyla her bileşeni nasıl kullandığı özetlenmiştir. Her alan için belirli roller ve sorumluluklar Microsoft Yönetilen Masaüstü belgelerinde ayrıntılı olarak açıklanmıştır.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 E5

| Ürün | Bilgi |
| ----- | ----- |
| Kurumlar için Microsoft 365 Uygulamaları (64 bit) | Aşağıdaki Office uygulamaları cihazla birlikte gönderilir:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>Access</li><li>Skype Kurumsal</li><li>OneNote</li></ul><br>Microsoft Microsoft Project 64 bit tam Visio sürümleri dahil değildir. Bununla birlikte, bu uygulamaların yüklenmesi Microsoft 365 Uygulamaları Enterprise sürümüne bağlı olduğu için, Microsoft Yönetilen Masaüstü bu uygulamaları lisanslı kullanıcılara dağıtmak için kullanabileceğiniz varsayılan Microsoft Intune dağıtımları ve güvenlik grupları oluşturdu. Daha fazla bilgi için bkz[. Microsoft Microsoft Project Masaüstü cihazlarına Microsoft Visio Yükleme](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory Oturum Açma özelliği, oturum açmada ilk kez oturum alıkan kullanıcılar için OneDrive.<br><br>Masaüstü, Belge ve Resimler klasörleri için bilinen Klasör Yeniden Yönlendirmesi dahildir. Bu klasörler Microsoft Yönetilen Masaüstü tarafından etkinleştirilir ve yapılandırılır. |
| Store Uygulamaları | Microsoft Sway Power BI diğer e-posta hizmetleri cihazla birlikte sevk edilir. Bu uygulamalar tüm uygulamalardan indirilebilir Microsoft Store. |
| Win32 Uygulamaları | Teams cihazla birlikte gönderilmiyor, ancak Microsoft Tarafından Yönetilen Masaüstü cihazları için Microsoft tarafından paketli ve sağlanmıştır. Azure Information Protection Client cihazla birlikte gönderilir, ancak dağıtım için paketli olarak sebilirsiniz. |
| Web Uygulamaları | Aşağıdaki web uygulamaları cihazla birlikte sevk edilir: <ul><li>Yammer</li><li>Office tarayıcıda yeniden kullanma</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planner</li></ul> <br>Kullanıcılar bir tarayıcıyla bu uygulamaların web sürümüne erişim sağlar. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise için Microsoft Defender ile E5 veya E3

IT yöneticilerinizin aşağıdaki ayarları yapılandırmalarını öneririz.

> [!NOTE]
> Bu ayarlar Microsoft Yönetilen Masaüstü kapsamında dahil değildir veya yönetilmiyor.

| Ürün | Bilgi |
| ----- | ----- |
| Windows Hello Kurumsal | Microsoft Yönetilen Masaüstü Windows Hello güçlü iki faktörlü kimlik doğrulamasıyla parolaları değiştirmek için Kurumsal'a uygulamanız gerekir. Daha fazla bilgi için bkz[. Windows Hello İş'e bakın](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Uygulama Sanallaştırma | Intune Win32 uygulama yönetim istemcisini kullanarak Uygulama Sanallaştırma (App-V) paketleri dağıtabilirsiniz. Daha fazla bilgi için bkz. [Uygulama Sanallaştırma](/windows/application-management/app-v/appv-technical-reference). |
| Microsoft 365 kaybı önlemeyi engelleme | Hassas olmaya Microsoft 365 üzerinde gerçekleştirmiş olduğunuz eylemleri izlemek ve bu öğelerin özel olarak paylaşımını önlemeye yardımcı olmak için, veri kaybı önleme işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için bkz[. Microsoft 365 önleme.](../../compliance/endpoint-dlp-learn-about.md) |

Microsoft Yönetilen Masaüstü'ne dahil edilen ve yönetilen özellikler:

| Ürün | Bilgi |
| ----- | ----- |
| BitLocker Sürücü Şifrelemesi | BitLocker Sürücü Şifrelemesi, tüm sistem sürücülerini şifrelemek için kullanılır. Daha fazla bilgi için bkz. [BitLocker Sürücü Şifrelemesi](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Başlangıçta sistem bütünlüğünü korur ve sistem bütünlüğünün gerçekten korunarak geçerli olduğunu doğrular. Daha fazla bilgi için [system guard Windows Defender bakın](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender credential Guard, yalnızca ayrıcalıklı sistem yazılımının bu bilgilere erişmesi için sanallaştırma tabanlı güvenliği kullanarak gizli bilgileri yalıtır. Daha fazla bilgi için [system guard Windows Defender bakın](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Uç Nokta için Microsoft Defender - Uç Nokta Algılama ve Yanıt | Microsoft Yönetilen Masaüstü Güvenlik İşlemleri uyarılara yanıt verir ve Uç Nokta Algılama ve Yanıt'ı kullanarak tehditleri düzeltmek için harekete geçmektedir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Uç Nokta Algılama ve Yanıt](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Uç Nokta için Microsoft Defender - Tehdit Uzmanları | Microsoft Yönetilen Masaüstü, Tehdit Uzmanları içgörüleri ve verileriyle hedefli saldırı bildirimleriyle tümleştirilmiştir. Bu hizmet etkinleştirilmeden önce ek izin sağlanız gerekir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Tehdit Uzmanları](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Uç Nokta için Microsoft Defender - Tehdit ve Güvenlik Açığı Yönetimi | Microsoft Yönetilen Masaüstü hizmet planında gelecekte kullanmak için gereklidir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Tehdit ve Güvenlik Açığı Yönetimi](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Uç Nokta için Microsoft Defender - Saldırı Yüzeyini Azaltma | Saldırganlar tarafından sıklıkla kötüye sınanan riskli yazılım davranışlarını hedefler. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Saldırı Yüzeyini Azaltma](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Uç Nokta için Microsoft Defender - Exploit Protection | Cihazlara bulaştırmak için açıkları kullanan kötü amaçlı yazılımlara karşı koruma sağlar ve işletim sistemi işlemleriyle uygulamalarına otomatik olarak açık kullanımı azaltma tekniklerini uygulayarak yayılır. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Uç Nokta için Microsoft Defender - Ağ Koruması | Düşük itibarlı kaynaklara Microsoft Defender SmartScreen tüm giden HTTP ve HTTPS trafiğini engellemek için, bağlantının kapsamını genişleter. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender - Ağ Koruması](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Microsoft Defender Tamper Protection | Windows Koruma, virüsten koruma gibi güvenlik ayarlarının değiştirilmesini önlemek için kullanılır. Daha fazla bilgi için bkz [. Microsoft Defender Tamper Protection](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Microsoft Defender Virüsten Koruma tabanlı, heuristic ve gerçek zamanlı virüsten koruma yazılımı | Kötü amaçlı yazılım olarak algı edilemedi dosya ve süreç tehditlerini taramak için her zaman açık. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma tabanlı, heuristic ve gerçek zamanlı virüsten koruma.](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) |
| Microsoft Defender Virüsten Koruma Teslim Edilen Koruma | Yeni ve yeni ortaya çıkan tehditlere karşı dinamik, anında ve otomatik koruma sağlar. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma Koruma'ya bakın](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Uç Nokta için Microsoft Defender - "İlk görüşte engelle" | Şüpheli veya bilinmeyen bir dosya algılayana kadar Windows kötü amaçlı yazılımları algılama ve engellemeyi sağlar. Daha fazla bilgi için bkz. [İlk görüşte Uç Nokta için Microsoft Defender - Blok](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| Microsoft Defender Virüsten Koruma İstenmeyen Olabilecek Uygulamalar | Makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemenize veya en kötü durumda beklenmedik veya istenmeyen başka yazılımlar yüklemenize neden olan uygulamaları engellemek için kullanılır. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma İstenmeyen Uygulamalar'a bakın](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| Windows Defender Güvenlik Duvarı | Cihaz için ana bilgisayar tabanlı iki yol yönelik ağ trafiği filtrelemesi Windows Defender Güvenlik Duvarı, yerel cihaza veya yerel cihaza gelen yetkisiz ağ trafiğini engeller. Daha fazla bilgi için bkz. [Gelişmiş Windows Defender Güvenlik Duvarı'nı yapılandırma](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| Kullanıcı Hesabı Denetimi | Kullanıcı Hesabı Denetimi, bir görev veya eylem yönetici hesap türüne erişim gerektirdiğinde Güvenli Masaüstü'ne geçiş sağlar. Microsoft Yönetilen Masaüstü kullanıcılarına kayıt sırasında Standart kullanıcı erişimi atanır. Daha fazla bilgi için bkz. [Kullanıcı Hesabı Denetimi](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Ürün | Bilgi |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | MDM cihazlarını yönetmek Enterprise Mobility + Security E3 tüm özellikleri kullanabilirsiniz.<br><br>Azure Active Directory Premium P2'i Microsoft Yönetilen Masaüstü ile isteğe bağlı bir özellik olarak kullanabilirsiniz. |
| Bulut Uygulamaları için Microsoft Defender | Bu isteğe bağlı özelliği Microsoft Yönetilen Masaüstü ile kullanabilirsiniz.
| Azure Information Protection P2  | Bu isteğe bağlı özelliği Microsoft Yönetilen Masaüstü ile kullanabilirsiniz.
