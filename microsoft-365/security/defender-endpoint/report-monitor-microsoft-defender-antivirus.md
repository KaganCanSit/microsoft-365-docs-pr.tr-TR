---
title: Microsoft Defender Virüsten Koruma korumayı izleme ve raporlama
description: Raporları kullanmak ve PowerShell ve WMI ile Microsoft Defender AV'yi izlemek için Configuration Manager veya güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanın.
keywords: siem, monitor, report, Microsoft Defender AV
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: b6593784b0df1109eb7729b3df91ef467d30c4bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788424"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Defender Virüsten Koruma’yı raporlayın

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016 yerleşik olarak bulunur. Microsoft Defender Virüsten Koruma, Pertahanan Microsoft untuk Titik Akhir'da yeni nesil korumanızdır. Yeni nesil koruma, cihazlarınızı e-posta, uygulamalar, bulut ve web'de virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerinden korumaya yardımcı olur.

Microsoft Defender Virüsten Koruma ile koruma durumunu ve uyarılarını gözden geçirmek için çeşitli seçenekleriniz vardır. Microsoft Defender Virüsten Koruma izlemek veya [e-posta uyarıları oluşturmak](/configmgr/protect/deploy-use/endpoint-configure-alerts) için [Microsoft Endpoint Manager](/configmgr/protect/deploy-use/monitor-endpoint-protection) kullanabilirsiniz. Ya da [Microsoft Intune](/intune/introduction-intune) kullanarak korumayı izleyebilirsiniz.

Üçüncü taraf güvenlik bilgileriniz ve olay yönetimi (SIEM) sunucunuz varsa, [Windows Defender istemci olaylarını](/windows/win32/events/windows-events) da kullanabilirsiniz.

Windows olaylar, Güvenlik Hesap Yöneticisi (SAM) olayları ([Windows 10 için geliştirilmiş](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), [Güvenlik denetimi](/windows/device-security/auditing/security-auditing-overview) konusuna da bakın) ve [Windows Defender olayları](troubleshoot-microsoft-defender-antivirus.md) da dahil olmak üzere çeşitli güvenlik olay kaynaklarından oluşur.

Bu olaylar [Windows olay toplayıcısı](/windows/win32/wec/windows-event-collector) kullanılarak merkezi olarak toplanabilir. SIEM sunucuları genellikle Windows olayları için bağlayıcılara sahiptir ve SIEM sunucunuzdaki tüm güvenlik olaylarını ilişkilendirmenize olanak sağlar.

[Log Analytics'teki Kötü Amaçlı Yazılım Değerlendirmesi çözümünü kullanarak kötü amaçlı yazılım olaylarını da izleyebilirsiniz](/azure/log-analytics/log-analytics-malware).

PowerShell, WMI veya Microsoft Azure durumunu izlemek veya belirlemek için [bkz. (Dağıtım, yönetim ve raporlama seçenekleri tablosu)](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)
