---
title: Mobil cihazların mobil cihazlar tarafından nasıl güncelleştiriliyor Microsoft Defender Virüsten Koruma
description: Dizüstü bilgisayarlar gibi mobil cihazların güvenlik güncelleştirmeleri ile nasıl güncelleştirileceklerini Microsoft Defender Virüsten Koruma yönetin.
keywords: güncelleştirmeler, koruma, güncelleştirmeleri zamanlama, pil, mobil cihaz, dizüstü bilgisayar, not defteri, kabul, microsoft update, wsus, geçersiz kılma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 3fc6d5a8b8fa7889f65f21111b3af82e124516b4
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997528"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Performansın güncelleştirmeler tarafından etkilenmey olduğundan emin olmak için mobil cihazlar ve VM'ler daha fazla yapılandırma gerektirir.

Bu cihazlar için yararlı iki ayar vardır:

- WSUS bağlantısı olmayan mobil bilgisayarlarda Microsoft Update'e katılma
- Pil gücüyle çalıştırmaya yönelik Güvenlik zekası güncelleştirmelerini engelleme

Aşağıdaki makaleler şu durumlarda da yararlı olabilir:
- [Zamanlanmış ve yakalama taramalarını yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Sanal masaüstü Microsoft Defender Virüsten Koruma (VDI) ortamında dağıtım kılavuzu](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>WSUS bağlantısı olmayan mobil bilgisayarlarda Microsoft Update'e katılma

Microsoft Update'i kullanarak, kurumsal ağa Microsoft Defender Virüsten Koruma veya WSUS bağlantısına sahip değilken mobil cihazlarda güvenlik zekası kullanımını güncel tutabilirsiniz.

Bu, WSUS'u Microsoft Update'i geçersiz k olacak şekilde ayarlasanız bile, cihazlara koruma güncelleştirmelerinin (Microsoft Update yoluyla) teslim edile aç olduğu anlamına gelir.

Mobil cihazda Microsoft Update'e katılmayı aşağıdaki yöntemlerden birini kullanarak kabul edebilirsiniz:

- Ayarı Grup İlkesi ile değiştirme.
- VBScript kullanarak bir betik oluşturun ve ardından bunu ağ bilgisayarınıza her bilgisayarda çalıştırın.
- Otomatik Menü menüsünden, ağ bilgisayarınızdan her **Ayarlar** seçin.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Microsoft Update'e katılmayı kabul etmek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'i** **ve ardından Yönetim şablonları'ı seçin**.

4. İmza **Güncelleştirmeleri'Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin**.

5. **Microsoft Update güvenlik zekası güncelleştirmelerine izin ver seçeneğini Etkin** **olarak ayarlayın ve** ardından Tamam'ı **seçin**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Microsoft Update'e katılmayı kabul etmek için VBScript kullanma

1. VBScript oluşturmak için MSDN'de [Microsoft Update'i Kabul Edin](/windows/win32/wua_sdk/opt-in-to-microsoft-update) makalesinde verilen yönergeleri kullanın.

2. Ağ ağınız içinde oluşturduğunuz her bilgisayarda oluşturduğunuz VBScript'i çalıştırın.

### <a name="manually-opt-in-to-microsoft-update"></a>Microsoft Update'e el ile katılma

1. Kabul **etmek Windows bilgisayarda** **& güncelleştirme** ve güvenlik ayarlarını güncelleştirme'de Güncelleştir'i açın.

2. Gelişmiş **seçenekler'i** seçin.

3. Güncelleştirme tarihime diğer **Microsoft ürünlerinin güncelleştirmelerini de ver onay kutusunu Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Pil gücüyle çalıştırmaya yönelik Güvenlik zekası güncelleştirmelerini engelleme

Bir bilgisayarı Microsoft Defender Virüsten Koruma bir güç kaynağına bağlı olduğunda koruma güncelleştirmelerini indirmek için yapılandırabilirsiniz.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Pil gücüyle ilgili güvenlik zekası güncelleştirmelerini engellemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesini seçin ve düzenlemek üzere açın.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'i** **ve ardından Yönetim şablonları'ı seçin**.

4. İmza Güncelleştirmeleri'Windows **bileşenleri Microsoft Defender Virüsten Koruma** \>  \> ağacı genişletin ve Pil gücüyle çalışan güvenlik zekası güncelleştirmelerine izin ver'i Devre **dışı olarak** **ayarlayın**. Sonra **Tamam**’ı seçin.

Bu eylem, bilgisayar pil gücün olduğunda koruma güncelleştirmelerinin indir indirebilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

- [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [E-posta Microsoft Defender Virüsten Koruma güncelleştirme ve Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)