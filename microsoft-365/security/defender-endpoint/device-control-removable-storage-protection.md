---
title: Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Koruması
description: Kullanıcının veya makinenin ya da her ikisinin de yetkisiz çıkarılabilir depolama medyası kullanmasını önlemeye yardımcı olan 'özellikleri anlama
keywords: çıkarılabilir depolama ortamı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5210530bb9102436e66667a0482aa09d941e26f9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939421"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Koruması


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Uç Nokta için Microsoft Defender'de cihaz denetimi çıkarılabilir depolama koruması, kullanıcıların, uç noktaların veya her ikisinin de yetkisiz çıkarılabilir depolama medyası kullanmasını engeller.

## <a name="protection-policies"></a>Koruma ilkeleri

### <a name="removable-storage-access-control"></a>Çıkarılabilir depolama birimi erişim denetimi

**Yetenek -lerini**

- *Denetim* Dışlama ile veya hariç tutmadan çeşitli cihaz özelliklerine göre çıkarılabilir depolama birimine okuma veya yazma veya yürütme erişimi.
- *Önle* Okuma veya Yazma veya Dışlama olmadan erişim yürütme - Çeşitli cihaz özelliklerine göre belirli bir cihaza izin verin.

**Windows 10 ve Windows 11 destek ayrıntıları**:

- Cihaz düzeyinde, kullanıcı düzeyinde uygulanır. veya her ikisini birden. Yalnızca belirli bir makinedeki belirli çıkarılabilir depolama birimine Okuma/Yazma/Yürütme erişimi gerçekleştiren belirli kişilere izin verin.
- MEM OMA-URI ve GPO desteği.
- Listelendiği gibi '[Cihaz Özellikleri](#device-properties)' desteklenir.
- Windows özelliği için bkz[. Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md).

**Desteklenen Platform** - Windows 10, Windows 11

**macOS destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış tüm kullanıcılar için de geçerlidir.
- macOS'a özgü bilgiler için bkz. [macOS için cihaz denetimi](mac-device-control-overview.md).

**Desteklenen platform** - macOS Catalina 10.15.4+ (sistem uzantıları etkin)


### <a name="device-installation"></a>Cihaz yüklemesi

**Özellikler** - Çeşitli cihaz özelliklerine göre dışlama ile veya dışlama olmadan yüklemeyi engelleyin.

**Windows 10 ve Windows 11 destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış tüm kullanıcılar için de geçerlidir.
- nesneleri Microsoft Endpoint Manager ve grup ilkesi destekler.
- Listelendiği gibi '[Cihaz Özellikleri](#device-properties)' desteklenir.
- Windows hakkında daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender kullanarak USB cihazlarını ve diğer çıkarılabilir medyaları denetleme](control-usb-devices-using-intune.md).

**Desteklenen Platform** - Windows 10, Windows 11

**macOS destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Oturum açan tüm kullanıcılar için aynı ilke geçerlidir
- macOS'a özgü bilgiler için bkz. [macOS için cihaz denetimi](mac-device-control-overview.md).

**Desteklenen platform** - macOS Catalina 10.15.4+ (sistem uzantıları etkinleştirilmiş) veya üzeri

### <a name="endpoint-dlp-removable-storage"></a>Uç Nokta DLP Çıkarılabilir depolama alanı

**Özellikler** - Kullanıcının bir öğeyi veya bilgiyi çıkarılabilir medyaya veya USB cihazına kopyalamasını denetleyin, uyarın veya engelleyin.

**Açıklama** - Windows hakkında daha fazla bilgi için bkz [. Uç nokta veri kaybını önleme hakkında bilgi edinin](../../compliance/endpoint-dlp-learn-about.md).

**Desteklenen Platform** - Windows 10, Windows 11

### <a name="bitlocker"></a>Bitlocker

**Özellikler**:

- BitLocker korumalı olmayan çıkarılabilir sürücülere yazılacak verileri engelleyin.
- Kuruluşunuza ait bir bilgisayarda şifrelenmedikleri sürece çıkarılabilir sürücülere erişimi engelleme

**Açıklama** - Windows hakkında daha fazla bilgi için bkz. [BitLocker - Çıkarılabilir Sürücü Ayarlar](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Desteklenen Platform** - Windows 10, Windows 11

## <a name="device-properties"></a>Cihaz özellikleri

Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Koruması, çıkarılabilir depolama birimi erişimini aşağıdaki tabloda açıklanan özelliklere göre kısıtlamanıza olanak tanır:

<br/><br/>

|Özellik Adı|Geçerli İlkeler|İşletim Sistemleri için geçerlidir|Açıklama|
|---|---|---|---|
|Cihaz Sınıfı|[Uç Nokta için Microsoft Defender kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz. [cihaz kurulum sınıfı](/windows-hardware/drivers/install/overview-of-device-setup-classes). Aşağıdaki iki bağlantı, Cihaz Kurulum Sınıflarının tam listesini sağlar. 'Sistem Kullanımı' sınıfları çoğunlukla fabrikadan bir bilgisayar/makineyle birlikte gelen cihazlara, 'Satıcı' sınıfları ise çoğunlukla mevcut bir bilgisayara/makineye bağlanabilen cihazlara başvurur: [Satıcılar tarafından Kullanılabilen Sistem Tanımlı Cihaz Kurulum Sınıfları - Windows sürücüleri](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) ve [Sistem Kullanımı için Ayrılmış Sistem Tanımlı Cihaz Kurulum Sınıfları - Windows sürücüleri](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Not**: Cihaz Yüklemesi yalnızca Çıkarılabilir depolama birimine değil tüm cihazlara da uygulanabilir.|
|Birincil Kimlik|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows|Birincil Kimlik çıkarılabilir depolama alanı ve CD/DVD ile Taşınabilir Cihaz/WPD Windows içerir.|
|Cihaz Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md); <p> [Uç Nokta için Microsoft Defender kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz. [Standart USB Tanımlayıcıları](/windows-hardware/drivers/install/standard-usb-identifiers), örneğin, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Donanım Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md) <p> [Uç Nokta için Microsoft Defender kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Sistemdeki cihazı tanımlayan bir dize, örneğin USBSTOR\DiskGeneric_Flash_Disk___8.07; **Not**: Donanım Kimliği benzersiz değildir; farklı cihazlar aynı değeri paylaşabilir.|
|Örnek Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md) <p> Cihaz Yüklemesi|Windows|Dize, sistemdeki cihazı benzersiz olarak tanımlar, örneğin USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Kolay Ad|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows|Cihaza bağlı bir dize, örneğin, Genel Flash Disk USB Cihazı|
|Satıcı Kimliği / Ürün Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows <p> macOS|Satıcı Kimliği, USB komitesinin satıcıya atadığını dört basamaklı satıcı kodudur. Ürün Kimliği, satıcının cihaza atadığını dört basamaklı ürün kodudur; Joker karakteri destekleyin.|
|Seri Numarası Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows <p> macOS |Örneğin, `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
