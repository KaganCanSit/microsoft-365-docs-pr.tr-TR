---
title: Microsoft Defender Virüsten Koruma arabirimini gizleme
description: Windows Güvenliği uygulamasında virüs ve tehdit koruması kutucuğunu gizleyebilirsiniz.
keywords: ui kilitleme, başsız mod, uygulamayı gizleme, ayarları gizleme, arabirimi gizleme
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
ms.openlocfilehash: fdd212efd50d55bbcdae80275f5d2ca8a97cdeb3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787676"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Kullanıcıların Microsoft Defender Virüsten Koruma kullanıcı arabirimini görmesini veya bu arabirimle etkileşim kurmasını engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Uç noktalardaki kullanıcıların Microsoft Defender Virüsten Koruma arabirimini görmesini önlemek için grup ilkesi kullanabilirsiniz. Taramaları duraklatmalarını da engelleyebilirsiniz.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Microsoft Defender Virüsten Koruma arabirimini gizleme

Windows 10, sürüm 1703'te arabirimi gizlemek Microsoft Defender Virüsten Koruma bildirimlerini gizler ve Virüs & tehdit koruması kutucuğunun Windows Güvenliği uygulamasında görünmesini engeller.

Ayar **Etkin** olarak ayarlandığında:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Kalkan simgesi ve virüs ve tehdit koruması bölümleri olmadan Windows Güvenliği" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Ayar **Devre dışı** veya yapılandırılmamış olarak ayarlandığında:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Kalkan simgesi ve tehdit koruması bölümleri içeren Windows Güvenliği" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Arabirimi gizlemek, Microsoft Defender Virüsten Koruma bildirimlerinin uç noktada görünmesini de engeller. Pertahanan Microsoft untuk Titik Akhir bildirimler görünmeye devam eder. [Ayrıca uç noktalarda görünen bildirimleri tek tek yapılandırabilirsiniz](configure-notifications-microsoft-defender-antivirus.md)

Windows 10 önceki sürümlerinde, ayar Windows Defender istemci arabirimini gizler. Kullanıcı uygulamayı açmayı denerse, "Sistem yöneticiniz bu uygulamaya erişimi kısıtlamıştır" şeklinde bir uyarı alır.

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="1703'ten önceki Windows 10 sürümlerde başsız mod etkinleştirildiğinde uyarı iletisi" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Microsoft Defender AV arabirimini kullanıcılardan gizlemek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** tıklatın.

4. **İstemci arabirimi > Microsoft Defender Virüsten Koruma > bileşenleri Windows** için ağacı genişletin.

5. **Başsız UI modunu etkinleştir** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Tamam**'a tıklayın.

Kullanıcıların bilgisayarlarında korumayı değiştirmesini engelleme hakkında daha fazla seçenek için bkz. Kullanıcıların [ilke ayarlarını yerel olarak](configure-local-policy-overrides-microsoft-defender-antivirus.md) değiştirmesini engelleme.

## <a name="prevent-users-from-pausing-a-scan"></a>Kullanıcıların taramayı duraklatmasını engelleme

Kullanıcıların taramaları duraklatmasını engelleyebilirsiniz. Bu, zamanlanmış veya isteğe bağlı taramaların kullanıcılar tarafından kesintiye uğramamasını sağlamak için yararlı olabilir.

> [!NOTE]
> Bu ayar Windows 10 desteklenmez.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Kullanıcıların taramayı duraklatmasını önlemek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** tıklatın.

4. **Tarama** **Microsoft Defender Virüsten Koruma bileşenleri** \>  \> Windows için ağacı genişletin.

5. **Kullanıcıların taramayı duraklatmasına izin ver ayarına** çift tıklayın ve seçeneği **Devre Dışı** olarak ayarlayın. **Tamam**'a tıklayın.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Uç noktalarda görünen bildirimleri yapılandırın](configure-notifications-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma ile son kullanıcı etkileşimlerini yapılandırma](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
