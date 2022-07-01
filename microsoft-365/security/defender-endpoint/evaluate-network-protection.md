---
title: Ağ korumasını değerlendirin
description: Koruduğu yaygın senaryoları test ederek ağ korumasının nasıl çalıştığını görün.
keywords: Ağ koruması, açıklardan yararlanmalar, kötü amaçlı web sitesi, ip, etki alanı, etki alanları, değerlendirme, test, tanıtım
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 2826c623437760d86aad54e4aa36900bdad68082
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603956"
---
# <a name="evaluate-network-protection"></a>Ağ korumasını değerlendirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Ağ koruması](network-protection.md) , çalışanların İnternet'te kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içeriğe ev sahipliği yapabilen tehlikeli etki alanlarına erişmek için herhangi bir uygulama kullanmasını önlemeye yardımcı olur.

Bu makale, özelliği etkinleştirerek ve bir test sitesine yönlendirerek ağ korumasını değerlendirmenize yardımcı olur. Bu değerlendirme makalesindeki siteler kötü amaçlı değildir. Bunlar, kötü amaçlıymış gibi davranan özel olarak oluşturulmuş web siteleridir. Site, bir kullanıcı kötü amaçlı bir siteyi veya etki alanını ziyaret ederse gerçekleşecek davranışı yineler.

> [!TIP]
> Diğer koruma özelliklerinin nasıl çalıştığını görmek için [demo.wd.microsoft.com'daki](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Microsoft Defender tanıtım senaryoları web sitesini de ziyaret edebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="enable-network-protection-in-audit-mode"></a>Denetim modunda ağ korumasını etkinleştirme

Hangi IP adreslerinin ve etki alanlarının engellendiğini görmek için denetim modunda ağ korumasını etkinleştirin. Bunun iş kolu uygulamalarını etkilemediğinden emin olabilir veya blokların ne sıklıkta oluştuğu hakkında fikir edinebilirsiniz.

1. Başlat menüsüne **powershell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin
2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>(Sahte) kötü amaçlı etki alanını ziyaret edin

1. Internet Explorer, Google Chrome veya istediğiniz başka bir tarayıcıyı açın.

2. [https://smartscreentestratings2.net](https://smartscreentestratings2.net) adımına gidin.

    Ağ bağlantısına izin verilir ve bir test iletisi görüntülenir.
    
    :::image type="content" source="images/np-notif.png" alt-text="Bağlantı engelleme bildirimi" lightbox="images/np-notif.png":::

> [!NOTE]
> Bir site ağ koruması tarafından engellenmiş olsa bile ağ bağlantıları başarılı olabilir. Daha fazla bilgi edinmek için bkz [. Ağ koruması ve TCP üç yönlü el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Windows Olay Görüntüleyicisi'de ağ koruma olaylarını gözden geçirme

Engellenmiş olabilecek uygulamaları gözden geçirmek için Olay Görüntüleyicisi açın ve Microsoft-Windows-Windows Defender/İşletim günlüğünde Olay Kimliği 1125'i filtreleyin. Aşağıdaki tabloda tüm ağ koruma olayları listelenir.

| Olay Kimliği | Sağla/Kaynak | Açıklama |
|---|---|---|
| 5007 | Windows Defender (Operasyonel) | Ayarlar değiştirildiğinde gerçekleşen olay |
| 1125 | Windows Defender (Operasyonel) | Ağ bağlantısı denetlendiğinde gerçekleşen olay |
| 1126 | Windows Defender (Operasyonel) | Ağ bağlantısı engellendiğinde gerçekleşen olay |

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruması](network-protection.md)

- [Ağ koruması ve TCP üç yönlü el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Ağ korumasını etkinleştirme](enable-network-protection.md)

- [Ağ koruması sorunlarını giderme](troubleshoot-np.md)
