---
title: Uç Nokta için Microsoft Defender'da ana bilgisayar güvenlik duvarı bildirimi
description: Portalda güvenlik duvarı raporlamayı ana Microsoft 365 Defender görüntüleme.
keywords: windows defender, güvenlik duvarı
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: b5aaad7363b42e18a0ca21e4d56d118218cec1a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019042"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da ana bilgisayar güvenlik duvarı bildirimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Yöneticiyseniz, artık güvenlik duvarı bildirimini portalında [Microsoft 365 Defender.](https://security.microsoft.com) Bu özellik merkezi bir konumdan Windows 10, Windows 11, Windows Server 2019 ve Windows Server 2022 güvenlik duvarı raporlamalarını görüntülemeye olanak sağlar.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Windows 10, Windows 11 veya Windows Server 2019 ya da Windows Server 2022 çalıştırlısınız.
- Cihazları Uç Nokta için Microsoft Defender hizmetine ekleme için buraya [bakın](onboard-configure.md).
- Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalının</a> verileri almaya başlaması için, Gelişmiş Güvenlik Duvarı'nı **Windows Defender** Denetim Olayları'nı etkinleştirmeniz gerekir:
  - [Denetim Filtreleme Platform Paketi Bırakma](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Denetim Filtreleme Platform Bağlantısı](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Grup İlkesi Nesne Düzenleyicisi, Yerel Güvenlik İlkesi veya İlke komutlarını kullanarak bu auditpol.exe etkinleştirin. Daha fazla bilgi için buraya [bakın](/windows/win32/fwp/auditing-and-logging).
  - İki PowerShell komutu vardır:
    - **auditpol /set /subcategory:"Platform PaketTeleni Filtreleme" /failure:enable**
    - **auditpol /set /subcategory:"Platform Bağlantısına Filtre Uygulama" /failure:enable**

## <a name="the-process"></a>İşlem

> [!NOTE]
> Yukarıdaki bölümde verilen yönergeleri izlemiş ve ön izleme katılımı için cihazlarınızı düzgün şekilde yapılandırmış olun.

- Olayları etkinleştirdikten sonra, Microsoft 365 Defender verileri izlemeye başlar.
  - Uzak IP, Uzak Bağlantı Noktası, Yerel Bağlantı Noktası, Yerel IP, Bilgisayar Adı, Gelen ve giden bağlantılarla ilgili süreç.
- Yöneticiler artık burada güvenlik Windows güvenlik duvarı etkinliğini [görebilir](https://security.microsoft.com/firewall).
  - Daha fazla raporlama, Güvenlik Duvarı kullanılarak güvenlik duvarı etkinliklerini izlemek üzere Windows Defender Raporlama betiği indirerek Power BI.[](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)
  - Verilerin yansıtması 12 saat kadar sürebilir.

## <a name="supported-scenarios"></a>Desteklenen senaryolar

Aşağıdaki senaryolar Ring0 Preview sırasında de desteklenen bir durumdadır.

### <a name="firewall-reporting"></a>Güvenlik duvarı raporlaması

Aşağıda güvenlik duvarı rapor sayfalarının birkaç örneği verilmiştir. Burada, gelen, giden ve uygulama etkinliğinin özetini bulabilirsiniz. Bu sayfaya doğrudan, 'a gidip erişebilirsiniz <https://security.microsoft.com/firewall>.

> [!div class="mx-imgBorder"]
> ![Ana bilgisayar güvenlik duvarı raporlama sayfası.](\images\host-firewall-reporting-page.png)

Bu raporlara, Güvenlik Duvarı Engellenen Gelen Bağlantılar kartının alt kısmında bulunan **ReportsSecurity** >  **ReportDevices** >  (bölüm) **bağlantısına gidip** de erişilebilir.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>"Engellenen bağlantı olan bilgisayarlar" cihazdan

Kartlar etkileşimli nesneleri destekler. Yeni bir sekmede Microsoft 365 Defender portalını başlatan ve sizi doğrudan Cihaz Zaman Çizelgesi sekmesine götüren cihaz adına tıklayarak, cihazın etkinliğinde **detaya girebilirsiniz**.

> [!div class="mx-imgBorder"]
> ![Bağlantısı engellenen bilgisayarlar.](\images\firewall-reporting-blocked-connection.png)

Artık, size o **cihazla** ilişkili olayların listesini verecek Olan Zaman Çizelgesi sekmesini seçebilirsiniz.

Görüntüleme bölmesinin **sağ** üst köşesindeki Filtreler düğmesine tık olduktan sonra, istediğiniz etkinlik türünü seçin. Bu durumda, Güvenlik Duvarı **olayları'nı** seçin; bölme Güvenlik Duvarı olayları olarak filtrelenmiş olur.

> [!div class="mx-imgBorder"]
> ![Filtreler düğmesi.](\images\firewall-reporting-filters-button.png)

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Gelişmiş avda detaya gitme (önizleme yenileme)

Güvenlik duvarı raporları, Gelişmiş av düğmesini aç düğmesine tıklayarak **karttan doğrudan** Gelişmiş **Uzmlara açmayı** destekler. Sorgu önceden doldurulur.

> [!div class="mx-imgBorder"]
> ![Gelişmiş av düğmesini açın.](\images\firewall-reporting-advanced-hunting.png)

Sorgu şimdi yürütülebilirsiniz ve son 30 gün içinde ilgili tüm Güvenlik Duvarı olayları araştırabilirsiniz.

Ek raporlama veya özel değişiklikler için sorgu daha fazla çözümleme yapmak üzere Power BI başka bir Power BI aktarabilirsiniz. Özel raporlama, Güvenlik Duvarı kullanılarak güvenlik duvarı etkinliklerini [](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) izlemek üzere Windows Defender Raporlama betiği indirerek Power BI.
