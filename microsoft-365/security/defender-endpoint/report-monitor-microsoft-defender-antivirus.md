---
title: Korumayı izleme ve Microsoft Defender Virüsten Koruma bildirme
description: Raporları kullanmak için Configuration Manager'ı veya güvenlik bilgileri ve olay yönetimi (SIEM) araçlarını kullanın ve Microsoft Defender AV'yi PowerShell ve WMI ile takip edin.
keywords: siem, monitör, rapor, Microsoft Defender AV
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
ms.openlocfilehash: 8d801daed1ae9884d10d6a4eec7059096333ec6f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997491"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Raporla ilgili Microsoft Defender Virüsten Koruma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma; Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016. Microsoft Defender Virüsten Koruma, Uç Nokta için Microsoft Defender'daki yeni nesil korumanızdır. Yeni nesil koruma, cihazlarınızı e-posta, uygulamalar, bulut ve web üzerinde virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerine karşı korumaya yardımcı olur.

Bu Microsoft Defender Virüsten Koruma, koruma durumunu ve uyarıları gözden geçirmek için çeşitli seçenekleriniz vardır. E-posta Microsoft Endpoint Manager [veya e-Microsoft Defender Virüsten Koruma](/configmgr/protect/deploy-use/monitor-endpoint-protection) [için E-posta Uyarıları'nın kullanımını izleyebilirsiniz](/configmgr/protect/deploy-use/endpoint-configure-alerts). Ya da korumayı, [güvenlik Microsoft Intune.](/intune/introduction-intune)

Üçüncü taraf güvenlik bilgileri ve olay yönetimi (SIEM) sunucunuz varsa, bu sunucuyu veya istemci [olaylarını Windows Defender edinebilirsiniz](/windows/win32/events/windows-events).

Windows olayları, Güvenlik Hesabı Yöneticisi (SAM) olayları ([Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511) için geliştirilmiş), Güvenlik denetim konusu da dahil olmak üzere çeşitli güvenlik [olayı kaynaklarından](troubleshoot-microsoft-defender-antivirus.md) oluşur ve Windows Defender [](/windows/device-security/auditing/security-auditing-overview) içerir.

Bu olaylar, en son olay toplayıcısı kullanılarak [Windows bir araya toplanabilir](/windows/win32/wec/windows-event-collector). SIEM sunucularında sık sık SIEM sunucunuzda güvenlik olaylarını Windows için bağlayıcılar vardır.

Ayrıca, [Log Analytics'te Kötü Amaçlı Yazılım Değerlendirmesi çözümünü kullanarak kötü amaçlı yazılım olaylarını izleyebilirsiniz](/azure/log-analytics/log-analytics-malware).

PowerShell, WMI veya MICROSOFT AZURE ile durumu izlemek veya belirlemek için [bkz. (Dağıtım, yönetim ve raporlama seçenekleri tablosu).](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
