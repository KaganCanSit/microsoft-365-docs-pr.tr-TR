---
title: Linux'ta Uç Nokta için Microsoft Defender ile ilgili eksik olay veya uyarı sorunlarını giderme
description: Linux'ta Uç Nokta için Microsoft Defender'da eksik olay veya uyarı sorunlarını giderin.
keywords: microsoft, defender, Endpoint için Microsoft Defender, Linux, etkinlikler
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5a17f94e3d26c08c0f6e0ca358778a65189cf6a5
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011887"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender ile ilgili eksik olay veya uyarı sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, portalda eksik etkinlikleri veya uyarıları azaltmak için bazı <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">genel Microsoft 365 Defender sağlar</a>.

Uç **Nokta için Microsoft Defender** bir cihaza düzgün bir şekilde yüklendikten sonra portalda bir cihaz sayfası oluşturulur. Cihaz sayfasındaki veya gelişmiş av sayfasındaki zaman çizelgesi sekmesinde tüm kayıtlı etkinlikleri gözden geçirebilirsiniz. Bu bölümde, bazı veya tüm beklenen olayların eksik olması durumu giderilir.
Örneğin, tüm _CreatedFile olayları_ eksikse.

## <a name="missing-network-and-login-events"></a>Eksik ağ ve oturum açma olayları

Ağ ve oturum açma etkinliğini izlemek için `audit` Linux'tan kullanılan Uç Nokta için Microsoft Defender.

1. Denetim çerçevesinin çalıştığından emin olun.

    ```bash
    service auditd status
    ```

    beklenen çıkış:

    ```output
    ● auditd.service - Security Auditing Service
    Loaded: loaded (/usr/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2020-12-21 10:48:02 IST; 2 weeks 0 days ago
        Docs: man:auditd(8)
            https://github.com/linux-audit/audit-documentation
    Process: 16689 ExecStartPost=/sbin/augenrules --load (code=exited, status=1/FAILURE)
    Process: 16665 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Main PID: 16666 (auditd)
        Tasks: 25
    CGroup: /system.slice/auditd.service
            ├─16666 /sbin/auditd
            ├─16668 /sbin/audispd
            ├─16670 /usr/sbin/sedispatch
            └─16671 /opt/microsoft/mdatp/sbin/mdatp_audisp_plugin -d
    ```

2. Durduruldu `auditd` olarak işaretlenmişse, başlat'a.

    ```bash
    service auditd start
    ```

**SLES sistemlerinde** , SYSCALL denetimi `auditd` varsayılan olarak devre dışı bırakılabilir ve eksik olaylardan sorumlu olabilir.

1. SYSCALL denetiminin devre dışı olmadığını doğrulamak için, geçerli denetim kurallarını listele:

    ```bash
    sudo auditctl -l
    ```

    Aşağıdaki satır varsa, belirli SYSCALL'leri izlemek için Uç Nokta için Microsoft Defender'ı etkinleştirmek için satırı kaldırın veya düzenleyin.

    ```output
    -a task, never
    ```

    denetim kuralları 'da bulunur `/etc/audit/rules.d/audit.rules`.

## <a name="missing-file-events"></a>Eksik dosya olayları

Dosya olayları çerçeveyle `fanotify` toplanır. Bazı dosya olaylarında veya bunların tüm durumlarda eksikse, `fanotify` cihazda etkin olduğundan ve dosya sisteminin destekildiğinden [emin olun](microsoft-defender-endpoint-linux.md#system-requirements).

Makinede dosyasistemlerini şu şekilde listele:

```bash
df -Th
```
