---
title: Temel Hareketlilik ve Güvenlik ile Intune arasında seçim
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
description: Temel Hareketlilik ve Güvenlik, mobil kullanım Microsoft 365 dir.
ms.openlocfilehash: 0a461bc7462300bb2b27b5d027c2b4d4582b7d14
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973712"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Temel Hareketlilik ve Güvenlik veya Intune arasında seçim

[Microsoft Intune](/mem/intune/), belirli Microsoft 365 planlarına dahil edilen tek başına bir üründür; temel mobil kullanım ve güvenlik ise Microsoft 365 dir.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Temel Hareketlilik ve Güvenlik ve Intune kullanılabilirliği

Hem Basic Mobility hem Security hem de Intune, aşağıdaki tabloda açıklanan çeşitli planlara dahildir.

| Plan | Temel Hareketlilik ve Güvenlik | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Uygulamaları|Evet|Hayır|
|Microsoft 365 İş Temel|Evet|Hayır|
|Microsoft 365 Business Standard|Evet|Hayır|
|Office 365 E1 |Evet|Hayır|
|Office 365 E3 |Evet|Hayır|
|Office 365 E5 |Evet|Hayır|
|Microsoft 365 Business Premium |Evet|Evet|
|Microsoft 365 Firstline 3 |Evet|Evet|
|Microsoft 365 Kurumsal E3 |Evet|Evet|
|Microsoft 365 Kurumsal E5 |Evet|Evet|
|Microsoft 365 Eğitim A1 |Evet|Evet|
|Microsoft 365 Eğitim A3 |Evet|Evet|
|Microsoft 365 Eğitim A5 |Evet|Evet|
|Microsoft Intune |Hayır|Evet|
|Enterprise Mobility & Security E3 |Hayır|Evet|
|Enterprise Mobility & Security E5 |Hayır|Evet|

> [!NOTE]
> Zaten Mobil Kullanım ve Güvenlik kullanıyorsanız Temel Mobil Kullanım ve Güvenlik'i Microsoft Intune.

 Ayrıntılar için platform hizmet [Microsoft 365 ve Office 365 bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Özelliklerde farklılıklar

Microsoft Intune Yerleşik Temel Mobil Kullanım ve Güvenlik özelliği, hem kuruluş içinde mobil cihazları yönetmenize hem de aşağıdaki tabloda açıklanan özelliklerde önemli farklılıklar vardır.

> [!NOTE]
> Kullanıcıları ve onların mobil cihazlarını yönetmek için önce Temel Mobil Kullanım ve Güvenlik'i ayarp ardından yeni bir Microsoft 365 İş Standart Intune ve Temel Mobil Kullanım ve *Güvenlik Microsoft Intune*. Bu, Temel Mobil Kullanım ve Güvenlik'i veya daha zengin özellikteki Intune çözümünü seçmenizi sağlar. Intune özelliklerini etkinleştirmek için Intune lisansı attaynın.

| Özellik alanı | Öne çıkan özellikler | Temel Hareketlilik ve Güvenlik | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Cihaz türleri|Farklı işletim sistemi platformlarını ve önemli yönetim modu değişkenlerini yönetme. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Cihaz uyumluluğu|Cihaz düzeyi PIN kilidi ve jailbreak algılama gibi güvenlik ilkelerini ayarlayın ve yönetin. |Android 9 ve sonraki cihazlarda sınırlamalar. [Ayrıntılara bakın](capabilities.md). |Evet|
|Cihaz uyumluluğuna dayalı koşullu erişim |Uyumlu olmayan cihazların şirket e-postalarına ve verilerine buluttan erişmesini engelin. |Bu sayfalarda Windows 10.<br/>Exchange Online, SharePoint Online ve Outlook.Outlook. |Evet |
|Cihaz yapılandırması  |Cihaz ayarlarını yapılandırma (örneğin kamerayı devre dışı bırakma)|Sınırlı ayar kümesi.|Evet|
|E-posta profilleri  |Cihazda yerel bir e-posta profili sağlama. |Evet|Evet|
|WiFi profilleri |Cihazda yerel bir WiFi profili sayın. |Hayır|Evet|
|VPN profilleri |Cihazda yerel bir VPN profili sağlama. |Hayır|Evet|
|Mobil uygulama yönetimi  |İç iş hattı uygulamalarınızı ve uygulama mağazalarından kullanıcılarınıza dağıtın. |Hayır|Evet|
|Mobil uygulama koruması  |Kullanıcılarınızı, bilinen Office mobil ve iş alanı uygulamalarını kullanarak şirket bilgilerine güvenli bir şekilde erişmelerini sağlarken kopyalama, kesme, yapıştırma ve kaydetme gibi eylemleri yalnızca şirket verileri için onaylanmış olarak yönetilen uygulamalarla kısıtlamaya yardımcı olarak verilerin güvenliğini sağlama. Cihazlar Temel Hareketlilik ve Güvenlik'e kaydolmamış olsa bile çalışır. Bkz. MAM ilkelerini kullanarak uygulama verilerini koruma. |Hayır|Evet|
|Yönetilen tarayıcı  |Edge uygulamasını kullanarak daha güvenli web'de gezinmeyi etkinleştirin. |Hayır|Evet|
|Sıfır dokunmatik kayıt programları (AutoPilot) |Şirkete ait çok sayıda cihazı kaydederek kullanıcı kurulumunu basitleştirin. |Hayır|Evet|
|||

Önceki tabloda listelenen özelliklere ek olarak, Temel Mobil Kullanım ve Güvenlik ile Intune'da İnternet üzerinden cihazlara komut gönderen bir dizi uzak eylem vardır. Örneğin, kişisel Office olduğu yerde bırakarak (Office uygulamalarını çalışanın cihazından temizleme) veya cihazı fabrika ayarlarına sıfırlama (tam temizleme) sırasında çalışanın cihazından Office verilerini kaldırabilirsiniz.

Temel Mobil Kullanım ve Güvenlik uzaktan eylemleri kullanımdan kullanım, temizleme ve tam temizleme eylemlerini içerir. Temel Hareketlilik ve Güvenlik eylemleri hakkında daha fazla bilgi için bkz. [Temel Hareketlilik ve Güvenlik özellikleri](capabilities.md).

Intune'da aşağıdaki eylem kümelerini kullanabilirsiniz:

-   AutoPilot sıfırlama (Windows açık)
-  [Bitlocker tuşu döndürme](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)  (Windows bir şekilde)
-  [Cihazı temizleme, kullanımdan kaldırma veya el ile kaydı kaldırmayı kullanma](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [Etkinleştirme yerini devre dışı bırakma](/mem/intune/remote-actions/device-activation-lock-disable)  (yalnızca iOS)
-  [Yeni başlangıç](/mem/intune/remote-actions/device-fresh-start)  (Windows)
- [Tam tarama](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  (Windows 10 bir kez)
- [Cihazı bulma](/mem/intune/remote-actions/device-locate)  (yalnızca iOS)
- [Kayıp modu](/mem/intune/remote-actions/device-lost-mode)  (yalnızca iOS)- [Hızlı tarama](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10)
- [Android için uzaktan denetim](/mem/intune/remote-actions/teamviewer-support)
- [Uzaktan kilitleme](/mem/intune/remote-actions/device-remote-lock)
- [Cihazı yeniden adlandır](/mem/intune/remote-actions/device-rename)
-  [Geçiş kodunu sıfırla](/mem/intune/remote-actions/device-passcode-reset) [Yeniden başlatma](/mem/intune/remote-actions/device-restart)  (Windows başlatma)
-  Akıllı Windows Defender Güncelleştirme (yalnızca Windows)
-  Windows 10 PIN sıfırlama (yalnızca Windows)
-  [Özel bildirim gönderme](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  (Android, iOS, iPad işletim sistemi)
-  [Cihazı eşitle](/mem/intune/remote-actions/device-sync)

Intune eylemleri hakkında daha fazla bilgi için bkz[. Microsoft Intune bakın](/mem/intune/).
