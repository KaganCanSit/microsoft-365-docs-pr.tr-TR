---
title: Ağ korumasını değerlendirme
description: Ağ korumasının koruma altında olduğu yaygın senaryoları testarak nasıl çalıştığını bakın.
keywords: Ağ koruması, exploits, kötü amaçlı web sitesi, ip, etki alanı, etki alanları, değerlendirme, test, tanıtım
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
- m365solution-scenario
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: c43fdfe746575837e8e5c8f36992f5fa6e2fec96
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679510"
---
# <a name="evaluate-network-protection"></a>Ağ korumasını değerlendirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Ağ koruması,](network-protection.md) çalışanların İnternet'de kimlik avı dolandırıcılığı, açıklardan yararlanan ve diğer zararlı içerikleri barındıran tehlikeli etki alanlarına erişmek için herhangi bir uygulamayı kullanmalarını engellemeye yardımcı olur.

Bu makale, özelliği etkinleştirerek ve size bir test sitesine yönlendirerek ağ korumasını değerlendirmeye yardımcı olur. Bu değerlendirme makalesinde yer alan siteler kötü amaçlı değildir. Bunlar kötü amaçlı olması gereken özel olarak oluşturulmuş web siteleridir. Kullanıcı kötü amaçlı bir siteyi veya etki alanını ziyaret ettiyse, site bu davranışı yineler.

> [!TIP]
> Diğer koruma özelliklerinin nasıl olduğunu görmek için Microsoft Defender tanıtım senaryoları web [sitesini demo.wd.microsoft.com'de](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) de ziyaret edebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="enable-network-protection-in-audit-mode"></a>Denetim modunda ağ korumasını etkinleştirme

Hangi IP adreslerinin ve etki alanlarının engellenmiş olacağını görmek için denetim modunda ağ korumasını etkinleştirin. Bunun iş hattı uygulamalarını etkilemey olduğundan emin olabilir veya engellemelerin ne sıklıkta oluştuğuna dair fikir edinebilirsiniz.

1. **PowerShell yazın ve** Başlat menüsü sağ tıklayın ve **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin.**
2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Kötü amaçlı (sahte) bir etki alanını ziyaret edin

1. Internet Explorer, Google Chrome veya tercihiniz herhangi bir tarayıcıyı açın.

2. [https://smartscreentestratings2.net](https://smartscreentestratings2.net) adımına gidin.

    Ağ bağlantısına izin verilir ve bir test iletisi görüntülenir.
    
    ![Bağlantı engellendi ifadesinin yer alan örnek bildirim: Bu ağ bağlantısının Windows Güvenliği yöneticiniz tarafından engellenmiş. IT yardım masanıza ulaşın.](images/np-notif.png)

> [!NOTE]
> Bir site ağ koruması tarafından engellenmiş olsa bile ağ bağlantıları başarılı olabilir. Daha fazla bilgi edinmek için [bkz. Ağ koruması ve TCP üç yol el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Olay Görüntüleyicisi'nde ağ Windows olaylarını gözden geçirme

Engellenmiş olan uygulamaları gözden geçirmek için Olay Görüntüleyicisi'ni açın ve Microsoft-Windows-Windows Defender/Operational günlüğünde Olay Kimliği 1125'i filtrelenin. Aşağıdaki tabloda tüm ağ koruma olayları listele.

| Olay Kimliği | Sağla/Kaynak | Açıklama |
|---|---|---|
| 5007 | Windows Defender (İşlem) | Ayarların değiştir olduğu olay |
| 1125 | Windows Defender (İşlem) | Ağ bağlantısı denetlenen olay |
| 1126 | Windows Defender (İşlem) | Ağ bağlantısı engellenmiş durumdayken olay |

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruması](network-protection.md)

- [Ağ koruması ve TCP üç yol el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Ağ korumasını etkinleştirme](enable-network-protection.md)

- [Ağ koruması sorunlarını giderme](troubleshoot-np.md)
