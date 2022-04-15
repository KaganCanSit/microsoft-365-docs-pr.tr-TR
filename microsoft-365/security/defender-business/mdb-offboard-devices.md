---
title: cihazı İş için Microsoft Defender'dan çıkarma
description: İş için Microsoft Defender'den cihaz kaldırma hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f702cb51e87777f0ac0e18e7caa794977df9c3dd
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862942"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>cihazı İş için Microsoft Defender'dan çıkarma

Bir cihazı boşaltmak istiyorsanız aşağıdaki yordamlardan birini kullanın:

- [Windows cihazı çıkarma](#offboard-a-windows-device)
- [macOS bilgisayarı çıkarma](#offboard-a-macos-computer)

## <a name="offboard-a-windows-device"></a>Windows cihazı çıkarma

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** ve ardından **Uç Noktalar'ı** seçin.

3. **Cihaz yönetimi'nin** altında **Çıkarma'yı** seçin.

4. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından **Cihazı kullanıma alma** altında Dağıtım **yöntemi** bölümünde **Yerel betik'i** seçin. 

5. Onay ekranında bilgileri gözden geçirin ve ardından devam etmek için **İndir'i** seçin.

6. **Çıkarma paketini indir'i** seçin. Çıkarma paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

7. Betiği, gemiden çıkarmak istediğiniz her cihazda çalıştırın.

## <a name="offboard-a-macos-computer"></a>macOS bilgisayarı çıkarma

1. **BulucuUygulamalar'a** >  gidin. 

2. İş için Microsoft Defender sağ tıklayın ve ardından **Çöp Kutusuna Taşı'yı** seçin. <br/><br/>--- veya --- <br/><br/> Şu komutu kullanın: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Cihazı kullanıma almak, cihazların İş için Defender'a veri göndermeyi durdurmasına neden olur. Ancak, çıkarmadan önce alınan veriler altı (6) aya kadar saklanır.

## <a name="next-steps"></a>Sonraki adımlar

