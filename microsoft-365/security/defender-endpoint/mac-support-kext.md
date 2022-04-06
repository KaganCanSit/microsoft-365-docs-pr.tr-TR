---
title: macOS'ta çekirdek Uç Nokta için Microsoft Defender sorunlarını giderme
description: macOS'ta çekirdek uzantısıyla Uç Nokta için Microsoft Defender sorunları giderin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, kernel, extension
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 72d1aab8be071b5f4ec66988b35655571625b409
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477291"
---
# <a name="troubleshoot-kernel-extension-issues-in-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta çekirdek Uç Nokta için Microsoft Defender sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [macOS Uç Nokta için Microsoft Defender üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu makalede, macOS'ta çekirdek uzantısının bir parçası olarak yüklenmiş olan çekirdek uzantısıyla ilgili Uç Nokta için Microsoft Defender bilgiler sağlanmıştır.

macOS High Sierra'dan (10.13) başlayarak, macOS tüm çekirdek uzantılarının cihazda çalışmasına izin verilmeden önce açıkça onaylanmasını gerektirir.

macOS'ta çekirdek uzantısını dağıtım/yükleme sırasında onaylamadısanız Uç Nokta için Microsoft Defender, uygulama bunu etkinleştirmenizi istenecek bir başlık görüntüler:

:::image type="content" source="images/mdatp-32-main-app-fix.png" alt-text="RTP devre dışı" lightbox="images/mdatp-32-main-app-fix.png":::

'i de çalıştırarak da çalıştırarak,```mdatp health``` Gerçek zamanlı koruma etkinleştirildiğinde ancak kullanılabilir olmadığını raporlar. Bu, çekirdek uzantısının aygıtınızda çalıştıracak şekilde onaylan olmadığını gösterir.

```bash
mdatp health
```
```Output
...
real_time_protection_enabled                : false
real_time_protection_available              : true
...
```

Aşağıdaki bölümlerde, macOS üzerinde office 365'i dağıtırken kullandığınız yönteme bağlı olarak bu sorunu Uç Nokta için Microsoft Defender ve ve bilgi sağlanmıştır.

## <a name="managed-deployment"></a>Yönetilen dağıtım

Ürünü dağıtmak için kullanılan yönetim aracına karşılık gelen yönergelere bakın:

- [JAMF tabanlı dağıtım](mac-install-with-jamf.md)
- [Microsoft Intune tabanlı dağıtım](mac-install-with-intune.md#create-system-configuration-profiles)

## <a name="manual-deployment"></a>El ile dağıtım

Ürün yüklendikten sonra 30 dakikadan kısa bir süre geçtiyse,  \> "Microsoft Corporation" geliştiricilerin sistem yazılımlarına izin ver ifadesinin bulunduğu Sistem Tercihleri Güvenlik  & Gizliliği'ne gidin.

Bu istem görmüyorsanız, 30 veya daha fazla dakika geçmiş ve çekirdek uzantısının aygıtınızda çalıştıracak şekilde onaylanmadı olduğu anlamına gelir:

:::image type="content" source="images/mdatp-33-securityprivacysettings-noprompt.png" alt-text="Bilgi isteminin süresi dolduktan sonra güvenlik ve gizlilik penceresi" lightbox="images/mdatp-33-securityprivacysettings-noprompt.png":::

Bu durumda, onay akışını yeniden tetiklemek için aşağıdaki adımları gerçekleştirmeniz gerekir.

1. Terminal'de sürücüyü yükleyin. Çekirdek uzantısının cihazda çalıştırıldı olarak onaylanmadı olması nedeniyle aşağıdaki işlem başarısız olur. Bununla birlikte, onay akışını yeniden tetikler.

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    ```Output
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Diagnostics for /Library/Extensions/wdavkext.kext:
    ```

2. **Menüden Sistem Tercihleri** \> **güvenlik & Gizlilik'i** açın. (Açıksa, önce kapatın.)

3. **Geliştiricilerin** sistem yazılımlarına "Microsoft Corporation" izin ver

4. Terminal'de sürücüyü yeniden yükleyin. Bu kez işlem başarılı olacaktır:

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    Başlık, Defender uygulamasından kaybolacak ve ```mdatp health``` artık hem etkinleştirildiğinde hem de kullanılabilir durumda olduğu bildirilmelidir:

    ```bash
    mdatp health
    ```

    ```Output
    ...
    real_time_protection_enabled                : true
    real_time_protection_available              : true
    ...
    ```
