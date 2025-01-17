---
title: Uç Nokta için Microsoft Defender Denetim Yazıcı Koruması
description: Uç Nokta için Microsoft Defender Denetim Yazıcı Koruması, kişilerin şirket dışı yazıcılar veya onaysız USB yazıcıları aracılığıyla yazdırmasını engeller.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: dansimp
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 9a700cd57b7843625f40289b43acd0e7a7eda45a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466685"
---
# <a name="device-control-printer-protection"></a>Cihaz Denetimi Yazıcı Koruması

**Geçerli olduğu yer:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender Denetim Yazıcı Koruması, kişilerin şirket dışı yazıcılar veya onaysız USB yazıcıları aracılığıyla yazdırmasını engeller.

## <a name="licensing"></a>Lisanslama

Yazıcı Koruma'ya başlamadan önce Yazıcı Koruması [aboneliğinizi Microsoft 365 gerekir](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Yazıcı Koruma'ya erişmek ve bu korumayı kullanmak için, aşağıdakilere sahip olmak gerekir:

- Microsoft 365 E3/ilke dağıtımı için özellik
- Microsoft 365 E5 raporu

## <a name="permission"></a>İzin

Intune'ta ilke dağıtımı için, oMA-URI aracılığıyla ilkenin dağıtımı için, hesabın cihaz yapılandırma profilleri oluşturma, düzenleme, güncelleştirme veya silme izinleri olması gerekir. Bu izinlerle özel roller oluşturabilir veya yerleşik rollerden herhangi birini kullanabilirsiniz:

- İlke ve profil Yöneticisi rolü.
- Cihaz Yapılandırması profilleri için Rapor Oluştur/Düzenle/Güncelleştir/Oku/Sil/Görüntüle izinleri açıkken özel bir rol de kullanabilirsiniz
- Veya Genel yönetici

Cihaz yapılandırma raporlarını görmek için, hesabın rapor görüntüleme izinlerine sahip olması gerekir. Bu izinlerle özel roller oluşturabilir veya yerleşik rolleri kullanabilirsiniz:

- Genel güvenlik yöneticisi
- Güvenlik yöneticisi
- Güvenlik Okuyucu

## <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Bu gereksinimleri karşılamak Windows 10, Windows 11 Koruma'nın dağıtımında planlanlan her yazıcı veya cihaz için uygun olduğundan emin olun.

1. Aşağıdaki Windows Güncelleştirmeler yüklenir.
    - 1809 için Windows: [KB5003217 Windows Update yükleme](https://support.microsoft.com/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46)
    - 1909 Windows için: [KB5003212 Windows Update yükleme](https://support.microsoft.com/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - Windows 2004 veya sonraki bir yıl için

2. İlkeyi grup ilkesi aracılığıyla dağıtmayı planlıyorsanız, cihazın Uç Nokta için Microsoft Defender'e dahil olması gerekir; ilkeyi Microsoft Endpoint Manager aracılığıyla dağıtmayı planlıyorsanız cihaz, Microsoft Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>Cihaz Denetimi Yazıcı Koruması İlkesini Dağıtma

İlkeyi, E-posta grup ilkesi Posta Intune.

<br>

****

|Başlık|Açıklama|CSP Desteği | GPO Desteği | Kullanıcı Tabanlı Destek | Makine Tabanlı Destek |
|---|---|:---:|:---:|:---:|:---:|
|**Cihaz Denetimi Yazdırma Kısıtlamalarını Etkinleştir**|Şirket dışında bir yazıcı kullanarak kişilerin yazdırmalarını engelleme|Evet|Evet|Evet|Evet|
|**Onaylandı USB bağlantılı yazdırma cihazlarının listesi**\*|Belirli BIR USB yazıcıya izin ver|Evet|Evet|Evet|Evet|
|

\* Bu ilke Cihaz denetimi Yazdırma **Kısıtlamalarını Etkinleştir ile birlikte kullanılmalıdır**.

## <a name="deploy-policy-via-intune"></a>Posta yoluyla ilkeyi Intune

Daha Intune, şu anda Cihaz Denetimi Yazıcı Koruması yalnızca OMA-URI'yi destekler.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-intune"></a>Senaryo 1: Kişilerin şirket dışından herhangi bir yazıcı kullanarak yazdırmalarını engellemek için Intune

- Makine üzerinden ilke uygulama:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl`

- Kullanıcıya ilke uygulama:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser`

AŞAĞıDAKI gibi CSP destek dizesi `<enabled/>`:

:::image type="content" source="../../media/customeditrow.png" alt-text="Özel sayfası" lightbox="../../media/customeditrow.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-intune"></a>Senaryo 2: Onaylandı olarak onaylanmış BELIRLI USB yazıcılarına klavye Intune

- Makine üzerinden ilke uygulama:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices`

- Kullanıcıya ilke uygulama:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser`

'ApprovedUsbPrintDevices' özelliği aracılığıyla onaylanmış USB yazıcılara sahip CSP destek dizesi, örnek `<enabled><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`:

:::image type="content" source="../../media/editrow.png" alt-text="Satır Düzenle bölmesi" lightbox="../../media/editrow.png":::

## <a name="deploy-policy-via-group-policy"></a>İlkeyi Posta yoluyla grup ilkesi

Cihaz bağlı değilse, Intune aracılığıyla ilkeyi dağıt grup ilkesi abilirsiniz.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-group-policy"></a>Senaryo 1: Kişilerin şirket dışından herhangi bir yazıcı kullanarak yazdırmalarını engellemek için grup ilkesi

- Makine üzerinden ilke uygulama:

  Bilgisayar Yapılandırması \> Yönetim Şablonları Yazıcısı \> : Cihaz denetimi Yazdırma Kısıtlamalarını Etkinleştirme

- Kullanıcıya ilke uygulama:

  Kullanıcı Yapılandırması \> Yönetim Şablonları Denetim Masası \> \> Yazıcılar: Cihaz denetimi Yazdırma Kısıtlamalarını Etkinleştirme

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="Cihaz Denetimi Yazdırma Kısıtlamalarını Etkinleştir bölmesi" lightbox="../../media/enable-device-ctrl-printing-restrictions.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-group-policy"></a>Senaryo 2: Onaylandır'ı kullanarak belirli onaylanmış USB yazıcılarına grup ilkesi

- Makine üzerinden ilke uygulama:

  Bilgisayar Yapılandırması \> Yönetim Şablonları Yazıcısı \> : Onaylanan USB bağlantılı yazdırma cihazlarının listesi

- Kullanıcıya ilke uygulama:

  Kullanıcı Yapılandırması \> Yönetim Şablonları Denetim Masası \> \> Yazıcılar: Onaylanan USB bağlantılı yazdırma cihazlarının listesi

:::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="Onaylanmış USB bağlantılı yazdırma cihazlarının listesi" lightbox="../../media/list-of-approved-connected-print-devices.png":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>Portalda Cihaz Denetimi Yazıcı Koruması Uç Nokta için Microsoft Defender görüntüleme

Yazdırma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender yukarıdaki</a> Cihaz Denetim Yazıcı Koruması ilkesi tarafından engellenen yazdırmayı gösterir.

```kusto
DeviceEvents
| where ActionType == 'PrintJobBlocked'
| extend parsed=parse_json(AdditionalFields)
| extend PrintedFile=tostring(parsed.JobOrDocumentName)
| extend PrintPortName=tostring(parsed.PortName)
| extend PrinterName=tostring(parsed.PrinterName)
| extend Policy=tostring(parsed.RestrictionReason) 
| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName, Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields
| order by Timestamp desc
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="gelişmiş av" lightbox="../../media/device-control-advanced-hunting.png":::

 PnP olayına, kuruluşta kullanılan USB yazıcıyı bulmak için kullanabilirsiniz:

```kusto
//find the USB Printer VID/PID
DeviceEvents
| where ActionType == "PnpDeviceConnected"
| extend parsed=parse_json(AdditionalFields)
| extend DeviceDescription = tostring(parsed.DeviceDescription) 
| extend PrinterDeviceId = tostring(parsed.DeviceId) 
| extend VID_PID_Array = split(split(PrinterDeviceId, "\\")[1], "&")
| extend VID_PID = replace_string(strcat(VID_PID_Array[0], '/', VID_PID_Array[1]), 'VID_', '')
| extend VID_PID = replace_string(VID_PID, 'PID_', '')
| extend ClassId = tostring(parsed.ClassId) 
| extend VendorIds = tostring(parsed.VendorIds) 
| where DeviceDescription == 'USB Printing Support'
| project Timestamp , DeviceId, DeviceName, ActionType, DeviceDescription, VID_PID, ClassId, PrinterDeviceId, VendorIds, parsed
| order by Timestamp desc
```

 :::image type="content" source="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png" alt-text="Gelişmiş Av sayfası" lightbox="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png":::
