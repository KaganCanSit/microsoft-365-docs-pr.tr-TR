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
ms.openlocfilehash: d54d8ecf2d0c365168ae636cbe85ef1da9cfb6b1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998066"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Kullanıcıların kullanıcı arabirimini görmelerini veya Microsoft Defender Virüsten Koruma engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç noktaları kullanan kullanıcıların kullanıcı arabirimini görmelerini engellemek için Grup İlkesi Microsoft Defender Virüsten Koruma kullanabilirsiniz. Ayrıca, bunları taramaları duraklatmalarını da önleysiniz.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Microsoft Defender Virüsten Koruma arabirimini gizleme

Windows 10 sürüm 1703'te arabirimin gizlenması, Microsoft Defender Virüsten Koruma bildirimlerini gizler ve Virüs & tehdit koruması kutucuğunun Windows Güvenliği uygulamasında görünmesini önler.

Ayar Etkin olarak **ayarlanmışken**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Kalkan simgesi Windows Güvenliği virüs ve tehdit koruması bölümleri olmayan görüntülerin ekran görüntüsü.":::

Ayar Devre Dışı veya **yapılandırılmamış** olarak ayarlanmışsa:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Kalkan simgesi Windows Güvenliği tehdit koruması bölümlerinin ekran görüntüsü.":::

> [!NOTE]
> Arabirimin gizlenilmesi, kullanıcı Microsoft Defender Virüsten Koruma uç noktada bu bildirimlerin görünmesini de engelleyebilirsiniz. Uç nokta bildirimleri için Microsoft Defender yine görünür. Ayrıca, uç [noktalarda görünen bildirimleri tek tek yapılandırarak](configure-notifications-microsoft-defender-antivirus.md) da

Bu ayar, Windows 10 arabiriminin önceki Windows Defender gizlenecek. Kullanıcı bu uygulamayı açmaya çalışırsa, "Sistem yöneticiniz bu uygulamaya erişimi kısıtladı" diyen bir uyarı alır.

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="1703'den önceki sürümlerde, Windows 10 modunda etkin olan uyarı iletisi":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Microsoft Defender AV arabirimini kullanıcılardan gizlemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. İstemci arabiriminde bileşenleri **Windows için > Microsoft Defender Virüsten Koruma > genişletin**.

5. Başsız kullanıcı arabirimi **modunu etkinleştir ayarına çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. **Tamam**'a tıklayın.

Kullanıcıların [pc'lerinde korumayı değiştirmesini önlemeye](configure-local-policy-overrides-microsoft-defender-antivirus.md) yönelik diğer seçenekler için bkz. Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme.

## <a name="prevent-users-from-pausing-a-scan"></a>Kullanıcıların taramayı duraklatmalarını engelleme

Kullanıcıların taramaları duraklatmasını önebilirsiniz, bu da zamanlanmış veya isteğe bağlı taramaların kullanıcılar tarafından kesintiye uğramamasını sağlamak için yararlı olabilir.

> [!NOTE]
> Bu ayar diğer iş Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Kullanıcıların taramayı duraklatmalarını engellemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. Tarama için bileşenleri **Windows için** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

5. Kullanıcıların taramayı **duraklatmalarına izin ver ayarına çift** tıklayın ve seçeneği Devre Dışı olarak **ayarlayın**. **Tamam**'a tıklayın.

## <a name="related-articles"></a>İlgili makaleler

- [Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)
- [Kullanıcı profiliyle son kullanıcı etkileşimi Microsoft Defender Virüsten Koruma](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
