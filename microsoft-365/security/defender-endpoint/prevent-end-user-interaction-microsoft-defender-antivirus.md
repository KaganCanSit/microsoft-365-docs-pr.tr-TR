---
title: Microsoft Defender Virüsten Koruma arabirimini gizleme
description: Windows Güvenliği uygulamasında virüs ve tehdit koruması kutucuğunu gizleyebilirsiniz.
keywords: ui lockdown, headless mode, hide app, hide settings, hide interface
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
ms.openlocfilehash: 26a792a753b0855a12cd994256cef93a64a5a159
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469239"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Kullanıcıların kullanıcı arabirimini görmelerini veya Microsoft Defender Virüsten Koruma engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

uç noktalarda grup ilkesi arabirimini görmelerini engellemek için Microsoft Defender Virüsten Koruma kullanabilirsiniz. Ayrıca, bunları taramaları duraklatmalarını da önleysiniz.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Microsoft Defender Virüsten Koruma arabirimini gizleme

Windows 10 sürüm 1703'te arabirimin gizlenması, Microsoft Defender Virüsten Koruma bildirimlerini gizler ve Virüs & tehdit koruması kutucuğunun Windows Güvenliği uygulamasında görünmesini önler.

Ayar Etkin olarak **ayarlanmışken**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Kalkan Windows Güvenliği ve virüs ve tehdit koruması bölümleri olmayan alan" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Ayar Devre Dışı veya **yapılandırılmamış** olarak ayarlanmışsa:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Kalkan Windows Güvenliği ve tehdit koruması bölümleriyle birlikte alan" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Arabirimin gizlenilmesi, kullanıcı Microsoft Defender Virüsten Koruma uç noktada bu bildirimlerin görünmesini de engelleyebilirsiniz. Uç Nokta için Microsoft Defender bildirimleri yine görünür. Ayrıca, uç [noktalarda görünen bildirimleri tek tek yapılandırarak](configure-notifications-microsoft-defender-antivirus.md) da

Bu ayar, Windows 10 arabiriminin önceki Windows Defender gizlenecek. Kullanıcı bu uygulamayı açmaya çalışırsa, "Sistem yöneticiniz bu uygulamaya erişimi kısıtladı" diyen bir uyarı alır.

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Başsız mod 1703'Windows 10 daha önceki sürümlerde etkinleştirildiğinde uyarı iletisi" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Microsoft Defender AV grup ilkesi kullanıcılarından gizlemek için kullanıcı arabirimini kullanma

1. Grup ilkesi yönetim makinenizin Yönetim [Konsolu'nu grup ilkesi](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), yapılandırmak istediğiniz Grup ilkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Yönetim **Grup ilkesi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. İstemci arabiriminde bileşenleri **Windows için > Microsoft Defender Virüsten Koruma > genişletin**.

5. Başsız kullanıcı arabirimi **modunu etkinleştir ayarına çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. **Tamam**'a tıklayın.

Kullanıcıların [pc'lerinde korumayı değiştirmesini önlemeye](configure-local-policy-overrides-microsoft-defender-antivirus.md) yönelik diğer seçenekler için bkz. Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme.

## <a name="prevent-users-from-pausing-a-scan"></a>Kullanıcıların taramayı duraklatmalarını engelleme

Kullanıcıların taramaları duraklatmasını önebilirsiniz, bu da zamanlanmış veya isteğe bağlı taramaların kullanıcılar tarafından kesintiye uğramamasını sağlamak için yararlı olabilir.

> [!NOTE]
> Bu ayar diğer iş Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Kullanıcıların grup ilkesi duraklatmalarını önlemek için Hızlı Erişim'i kullanma

1. Grup ilkesi yönetim makinenizin Yönetim [Konsolu'nu grup ilkesi](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), yapılandırmak istediğiniz Grup ilkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Yönetim **Grup ilkesi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. Tarama için bileşenleri **Windows için** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

5. Kullanıcıların taramayı **duraklatmalarına izin ver ayarına çift** tıklayın ve seçeneği Devre Dışı olarak **ayarlayın**. **Tamam**'a tıklayın.

## <a name="related-articles"></a>İlgili makaleler

- [Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)
- [Kullanıcı profiliyle son kullanıcı etkileşimi Microsoft Defender Virüsten Koruma](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
