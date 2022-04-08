---
title: Temel Mobilite ve Güvenlik ile Intune arasında seçim yapma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Temel Mobilite ve Güvenlik, Microsoft 365 planlarının bir parçasıdır.
ms.openlocfilehash: 0c1c61181d7e8bd5eb0ee000e29285c32a454692
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713855"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Temel Mobilite ve Güvenlik veya Intune arasında seçim yapma

[Microsoft Intune](/mem/intune/), belirli Microsoft 365 planlarıyla birlikte sunulan tek başına bir üründür, Basic Mobility ve Security ise Microsoft 365 planlarının bir parçasıdır.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Temel Mobilite ve Güvenlik ve Intune Kullanılabilirliği

Temel Mobilite ve Güvenlik ve Intune, aşağıdaki tabloda açıklanan çeşitli planlara dahil edilmiştir.

| Plan | Temel Hareketlilik ve Güvenlik | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Uygulamaları|Evet|Hayır|
|Microsoft 365 Küçük İşletme|Evet|Hayır|
|Microsoft 365 Business Standard|Evet|Hayır|
|Office 365 E1 |Evet|Hayır|
|Office 365 E3 |Evet|Hayır|
|Office 365 E5 |Evet|Hayır|
|Microsoft 365 Business Premium |Evet|Evet|
|Microsoft 365 İlk Satır 3 |Evet|Evet|
|Microsoft 365 Kurumsal E3 |Evet|Evet|
|Microsoft 365 Kurumsal E5 |Evet|Evet|
|A1 Microsoft 365 Eğitim |Evet|Evet|
|Microsoft 365 Eğitim A3 |Evet|Evet|
|Microsoft 365 Eğitim A5 |Evet|Evet|
|Microsoft Intune |Hayır|Evet|
|Enterprise Mobility & Security E3 |Hayır|Evet|
|Enterprise Mobility & Security E5 |Hayır|Evet|

> [!NOTE]
> Zaten Microsoft Intune kullanıyorsanız Temel Mobilite ve Güvenlik'i kullanmaya başlayamazsınız.

 Ayrıntılar için bkz. [Microsoft 365 ve Office 365 platform hizmeti açıklamaları](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Özelliklerdeki farklılıklar

Microsoft Intune ve yerleşik Temel Mobilite ve Güvenlik, kuruluşunuzdaki mobil cihazları yönetme olanağı sağlar, ancak aşağıdaki tabloda açıklanan özelliklerde önemli farklılıklar vardır.

> [!NOTE]
> Önce *Basic Mobility ve Security'yi ayarlayıp ardından Microsoft Intune ekleyerek kullanıcıları ve* mobil cihazlarını aynı Microsoft 365 İş Standart kuruluşunda hem Intune hem de Temel Mobilite ve Güvenlik kullanarak yönetebilirsiniz. Bu, Temel Mobilite ve Güvenlik'i veya daha zengin özelliklere Intune çözümü seçmenize olanak tanır. Intune özelliklerini etkinleştirmek için bir Intune lisansı atayın.

| Özellik alanı | Öne çıkan özellikler | Temel Hareketlilik ve Güvenlik | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Cihaz türleri|Farklı işletim sistemi platformlarını ve ana yönetim modu değişkenlerini yönetme. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad işletim sistemi|
|Cihaz uyumluluğu|Cihaz düzeyinde PIN kilidi ve jailbreak algılama gibi güvenlik ilkelerini ayarlayın ve yönetin. |Android cihazlarda sınırlamalar. [Ayrıntılara](capabilities.md) bakın. |Evet|
|Cihaz uyumluluğuna göre koşullu erişim |Uyumsuz cihazların buluttan şirket e-postalarına ve verilerine erişmesini önleyin. |Windows 10 desteklenmez.<br/>Exchange Online, SharePoint Online ve Outlook erişimi denetlemeyle sınırlıdır. |Evet |
|Cihaz yapılandırması  |Cihaz ayarlarını yapılandırma (örneğin, kamerayı devre dışı bırakma)|Sınırlı ayar kümesi.|Evet|
|E-posta profilleri  |Cihazda yerel bir e-posta profili sağlayın. |Evet|Evet|
|WiFi profilleri |Cihazda yerel bir WiFi profili sağlayın. |Hayır|Evet|
|VPN profilleri |Cihazda yerel bir VPN profili sağlayın. |Hayır|Evet|
|Mobil uygulama yönetimi  |dahili iş kolu uygulamalarınızı ve uygulama mağazalarından kullanıcılara dağıtın. |Hayır|Evet|
|Mobil uygulama koruması  |Kullanıcılarınızın bildikleri Office mobil ve iş kolu uygulamalarını kullanarak şirket bilgilerine güvenli bir şekilde erişmesini sağlarken kopyalama, kesme, yapıştırma ve farklı kaydetme gibi eylemlerin yalnızca şirket verileri için onaylanan uygulamalarla kısıtlanmasını sağlayarak verilerin güvenliğini sağlayın. Cihazlar Basic Mobility ve Security'ye kayıtlı olmasa bile çalışır. Bkz. MAM ilkelerini kullanarak uygulama verilerini koruma. |Hayır|Evet|
|Yönetilen tarayıcı  |Edge uygulamasını kullanarak daha güvenli web'e gözatmayı etkinleştirin. |Hayır|Evet|
|Sıfır dokunma kayıt programı (AutoPilot) |Şirkete ait çok sayıda cihazı kaydederken kullanıcı kurulumunu basitleştirin. |Hayır|Evet|

Yukarıdaki tabloda listelenen özelliklere ek olarak, Basic Mobility ve Security ve Intune her ikisi de İnternet üzerinden cihazlara komut gönderen bir dizi uzak eylem içerir. Örneğin, kişisel verileri yerinde bırakırken çalışanın cihazından Office verileri kaldırabilir (devre dışı bırakabilir), bir çalışanın cihazından Office uygulamaları kaldırabilir (temizleme) veya cihazı fabrika ayarlarına sıfırlayabilirsiniz (tam silme).

Temel Mobilite ve Güvenlik uzaktan eylemleri devre dışı bırakma, silme ve tam silme işlemlerini içerir. Temel Mobilite ve Güvenlik eylemleri hakkında daha fazla bilgi için bkz. [Temel Mobilite ve Güvenlik özellikleri](capabilities.md).

Intune ile aşağıdaki eylemlere sahipsiniz:

- [Otomatik pilot sıfırlama](/mem/autopilot/windows-autopilot-reset) (yalnızca Windows)
- [Bitlocker anahtar kurtarma](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6)  (yalnızca Windows)
- [Cihazı silme, devre dışı bırakma veya el ile kaydını kaldırmayı kullanma](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [Etkinleştirme kilidini](/mem/intune/remote-actions/device-activation-lock-disable)  devre dışı bırakma (yalnızca iOS)
- [Yeni başlangıç](/mem/intune/remote-actions/device-fresh-start)  (yalnızca Windows)
- [Tam tarama](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  (yalnızca Windows 10)
- [Cihazı](/mem/intune/remote-actions/device-locate)  bulma (yalnızca iOS)
- [Kayıp modu](/mem/intune/remote-actions/device-lost-mode)  (yalnızca iOS)- [Hızlı tarama](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (yalnızca Windows 10)
- [Android için uzaktan denetim](/mem/intune/remote-actions/teamviewer-support)
- [Uzaktan kilitleme](/mem/intune/remote-actions/device-remote-lock)
- [Cihazı yeniden adlandırma](/mem/intune/remote-actions/device-rename)
- [Geçiş kodunu sıfırlama](/mem/intune/remote-actions/device-passcode-reset) [Yeniden Başlatma](/mem/intune/remote-actions/device-restart)  (yalnızca Windows)
- [güncelleştirme Windows Defender Güvenlik Bilgileri](https://www.microsoft.com/en-us/wdsi/defenderupdates) (yalnızca Windows)
- [PIN sıfırlamayı Windows 10](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (yalnızca Windows)
- [Özel bildirimler](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  gönderme (Android, iOS, iPad işletim sistemi)
- [Cihazı eşitleme](/mem/intune/remote-actions/device-sync)

Intune eylemleri hakkında daha fazla bilgi [için Microsoft Intune belgelerine bakın](/mem/intune/).
