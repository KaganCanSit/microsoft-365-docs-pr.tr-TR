---
title: Uç Nokta için Microsoft Defender’da güvenlik duvarı raporlama oturumu düzenleyin
description: Microsoft 365 Defender portalında güvenlik duvarı raporlamayı barındırın ve görüntüleyin.
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
ms.openlocfilehash: 33eff726609db3d7f2d07f4a5bcf4955536c086c
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647293"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender’da güvenlik duvarı raporlama oturumu düzenleyin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Genel yönetici veya güvenlik yöneticisiyseniz artık güvenlik duvarı raporlamasını [Microsoft 365 Defender portalında](https://security.microsoft.com) barındırabilirsiniz. Bu özellik, Windows 10, Windows 11, Windows Server 2019'u ve Windows Server 2022 güvenlik duvarı raporlamasını merkezi bir konumdan görüntülemenizi sağlar.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Windows 10 veya Windows 11 ya da Windows Server 2019 veya Windows Server 2022 çalıştırıyor olmanız gerekir.
- Cihazları Uç Nokta için Microsoft Defender hizmetine eklemek için [buraya](onboard-configure.md) bakın.
- <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalın</a> verileri almaya başlaması için Gelişmiş Güvenlik ile Windows Defender Güvenlik Duvarı için **Denetim Olaylarını** etkinleştirmeniz gerekir:
  - [Denetim Filtreleme Platformu Paket Bırakma](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Filtre Platformu Bağlantısını Denetle](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- grup ilkesi Nesne Düzenleyicisi, Yerel Güvenlik İlkesi veya auditpol.exe komutlarını kullanarak bu olayları etkinleştirin. Daha fazla bilgi için [buraya](/windows/win32/fwp/auditing-and-logging) bakın.
  - İki PowerShell komutu şunlardır:
    - **auditpol /set /subcategory:"Platform Paket Bırakmasını Filtreleme" /failure:enable**
    - **auditpol /set /subcategory:"Platform Bağlantısını Filtreleme" /failure:enable**
```powershell
param (
    [switch]$remediate
)
try {

    $categories = "Filtering Platform Packet Drop,Filtering Platform Connection"
    $current = auditpol /get /subcategory:"$($categories)" /r | ConvertFrom-Csv    
    if ($current."Inclusion Setting" -ne "failure") {
        if ($remediate.IsPresent) {
            Write-Host "Remediating. No Auditing Enabled. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})"
            $output = auditpol /set /subcategory:"$($categories)" /failure:enable
            if($output -eq "The command was successfully executed.") {
                Write-Host "$($output)"
                exit 0
            }
            else {
                Write-Host "$($output)"
                exit 1
            }
        }
        else {
            Write-Host "Remediation Needed. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})."
            exit 1
        }
    }

}
catch {
    throw $_
} 
```

## <a name="the-process"></a>İşlem

> [!NOTE]
> Yukarıdaki bölümde yer alan yönergeleri izlediğinizden ve cihazlarınızı erken önizleme katılımı için düzgün yapılandırdığından emin olun.

- Olayları etkinleştirdikten sonra Microsoft 365 Defender verileri izlemeye başlar.
  - Uzak IP, Uzak Bağlantı Noktası, Yerel Bağlantı Noktası, Yerel IP, Bilgisayar Adı, Gelen ve giden bağlantılar arasında işlem.
- Yöneticiler artık Windows ana bilgisayar güvenlik duvarı etkinliğini [burada](https://security.microsoft.com/firewall) görebilir.
  - Power BI kullanarak Windows Defender Güvenlik Duvarı etkinliklerini izlemek için [Özel Raporlama betiğini](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) indirerek ek raporlama kolaylaştırılabilir.
  - Verilerin yansıtılabilmesi 12 saat kadar sürebilir.

## <a name="supported-scenarios"></a>Desteklenen senaryolar

Ring0 Preview sırasında aşağıdaki senaryolar desteklenir.

### <a name="firewall-reporting"></a>Güvenlik duvarı raporlama

Güvenlik duvarı rapor sayfalarının birkaç örneği aşağıda verilmiştir. Burada gelen, giden ve uygulama etkinliğinin özetini bulabilirsiniz. Bu sayfaya doğrudan adresine giderek <https://security.microsoft.com/firewall>erişebilirsiniz.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="Konak güvenlik duvarı raporlama sayfası" lightbox="\images\host-firewall-reporting-page.png":::

Bu raporlara Güvenlik **Duvarı Engellenen Gelen Bağlantılar** kartının en altında bulunan **RaporlarGüvenlik** >  **RaporuCihazlar** >  (bölüm) bölümüne giderek de erişilebilir.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>"Bağlantısı engellenen bilgisayarlar"dan cihaza

Kartlar etkileşimli nesneleri destekler. Yeni bir sekmede Microsoft 365 Defender portalını başlatacak ve sizi doğrudan **Cihaz Zaman Çizelgesi** sekmesine götürecek cihaz adına tıklayarak bir cihazın etkinliğinde detaya gidebilirsiniz.

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="Bağlantısı engellenen bilgisayarlar sayfası" lightbox="\images\firewall-reporting-blocked-connection.png":::

Artık **Zaman Çizelgesi** sekmesini seçebilirsiniz. Bu sekme, size bu cihazla ilişkili olayların listesini verir.

Görüntüleme bölmesinin sağ üst köşesindeki **Filtreler** düğmesine tıkladıktan sonra istediğiniz olay türünü seçin. Bu durumda **Güvenlik duvarı olayları'nı** seçtiğinizde bölme Güvenlik duvarı olayları olarak filtrelenir.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="Filtreler düğmesi" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Gelişmiş avcılık (önizleme yenilemesi) detayına gitme

Güvenlik duvarı raporları, Gelişmiş **Avcılığı Aç** düğmesine tıklayarak doğrudan karttan **Gelişmiş Avcılık'a** detaya gitme desteği verir. Sorgu önceden doldurulur.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="Gelişmiş avcılığı aç düğmesi" lightbox="\images\firewall-reporting-advanced-hunting.png":::

Sorgu artık yürütülebilir ve son 30 güne ait tüm ilgili Güvenlik Duvarı olayları incelenebilir.

Ek raporlama veya özel değişiklikler için sorgu daha fazla analiz için Power BI aktarılabilir. Özel raporlama, Power BI kullanarak Windows Defender Güvenlik Duvarı etkinliklerini izlemek için [Özel Raporlama betiğini](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) indirerek kolaylaştırılabilir.
