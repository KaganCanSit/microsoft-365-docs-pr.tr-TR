---
title: Uç Nokta için Microsoft Defender Denetimi Çıkarılabilir Depolama Koruması Depolama a bakın
description: Kullanıcı veya makine ya da her ikisinin de yetkisiz çıkarılabilir depolama medyasını kullanmalarını önlemeye yardımcı olan 'özellikleri anlama
keywords: çıkarılabilir depolama medyası
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
ms.openlocfilehash: 5913df59cb12d2f4d2d9dbec9c426bbf71769848
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569545"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Uç Nokta için Microsoft Defender Denetimi Çıkarılabilir Depolama Koruması Depolama a bakın


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Birden çok cihazda çıkarılabilir depolama alanı koruması Uç Nokta için Microsoft Defender kullanıcıların, uç noktaların veya her ikisinin de yetkisiz çıkarılabilir depolama medyasını kullanmalarını önler.

## <a name="protection-policies"></a>Koruma ilkeleri

### <a name="removable-storage-access-control"></a>Çıkarılabilir depolama alanı erişim denetimi

**Özellikler**

- *Denetim* Çıkarılabilir depolamada dışlamayla veya dışlama olmadan çeşitli cihaz özelliklerine bağlı olarak Okuma veya Yazma veya Yürütme erişimi.
- *Engelleme* Okuma veya Yazma veya Dışlama olmadan erişim - Çeşitli cihaz özelliklerine göre belirli bir cihaza izin verme.

**Windows 10 ve Windows 11 ayrıntılarına bakın**:

- Cihaz düzeyinde kullanıcı düzeyinde uygulanır. veya her ikisini birden. Yalnızca belirli bir makinede belirli bir çıkarılabilir depolama alanına Okuma/Yazma/Yürütme erişimi gerçekleştiren belirli kişilerin erişmesine izin verme.
- MEM OMA-URI ve GPO desteği.
- 'Cihaz [Özellikleri' listelenmiştir](#device-properties).
- Çıkarılabilir depolama Windows için bkz[. Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md).

**Desteklenen Platform** - Windows 10, Windows 11

**macOS destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış olan tüm kullanıcılar için geçerlidir.
- macOS'a özgü bilgiler için bkz. [macOS için cihaz denetimi](mac-device-control-overview.md).

**Desteklenen platform** - macOS Catalina 10.15.4+ (sistem uzantıları etkin durumdadır)


### <a name="device-installation"></a>Cihaz yüklemesi

**Özellikler -** Çeşitli cihaz özelliklerine göre yükleme işlemini dışlamayla veya dışlama olmadan engelin.

**Windows 10 ve Windows 11 ayrıntılarına bakın**:

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış olan tüm kullanıcılar için geçerlidir.
- Nesne Microsoft Endpoint Manager nesne grup ilkesi destekler.
- 'Cihaz [Özellikleri' listelenmiştir](#device-properties).
- Usb cihazları ve diğer Windows medyayı denetleme hakkında daha fazla bilgi için bkz. [USB cihazlarını ve diğer çıkarılabilir medyayı Uç Nokta için Microsoft Defender](control-usb-devices-using-intune.md).

**Desteklenen Platform** - Windows 10, Windows 11

**macOS destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Aynı ilke oturum açmış olan tüm kullanıcılar için geçerlidir
- macOS'a özgü bilgiler için bkz. [macOS için cihaz denetimi](mac-device-control-overview.md).

**Desteklenen platform** - macOS Catalina 10.15.4+ (sistem uzantıları etkin durumdadır) veya sonrası

### <a name="endpoint-dlp-removable-storage"></a>Uç nokta DLP Çıkarılabilir depolama alanı

**Özellikler** - Kullanıcının bir öğeyi veya bilgileri çıkarılabilir bir medyaya veya USB cihazına kopyalamasını denetleme, uyarma veya engelleme.

**Açıklama** - Bu bağlantı hakkında daha fazla Windows bkz [. Uç nokta veri Microsoft 365 önleme hakkında bilgi.](../../compliance/endpoint-dlp-learn-about.md)

**Desteklenen Platform** - Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Özellikler**:

- BitLocker korumalı olmayan çıkarılabilir sürücülere yazılabilen verileri engelin.
- Kuruluşun sahip olduğu bir bilgisayarda şifrelenmediği sürece çıkarılabilir sürücülere erişimi engelleme

**Açıklama** - BitLocker - Sabit Windows fazla bilgi için bkz. [BitLocker - Çıkarılabilir Sürücü Ayarlar](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Desteklenen Platform** - Windows 10, Windows 11

## <a name="device-properties"></a>Cihaz özellikleri

Uç Nokta için Microsoft Defender Denetimi Çıkarılabilir Çıkarılabilir Depolama Koruması, çıkarılabilir depolama erişimini aşağıdaki tabloda açıklanan özelliklere göre kısıtlamanıza olanak sağlar:

<br/><br/>

|Özellik Adı|Geçerli İlkeler|İşletim Sistemleri için geçerlidir|Açıklama|
|---|---|---|---|
|Cihaz Sınıfı|[USB cihazlarını ve diğer çıkarılabilir medyayı KONTROL etmek için USB Uç Nokta için Microsoft Defender](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz. [cihaz kurulum sınıfı](/windows-hardware/drivers/install/overview-of-device-setup-classes). Aşağıdaki iki bağlantı Cihaz Kurulumu Sınıflarının tam listesini sağlar. 'Sistem Kullanımı' sınıfları çoğunlukla fabrikaya ait bir bilgisayar/makineyle gelen cihazlara başvururken, "Satıcı" sınıfları daha çok var olan bir bilgisayara/makineye bağlanıyor olabilir: Satıcılara Kullanılabilen Sistem Tanımlı Cihaz Kurulumu Sınıfları [- Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) sürücüleri ve Sistem Kullanımı [- Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use) sürücüleri için Ayrılmış Sistem Tanımlı Cihaz Kurulumu Sınıfları. **Not**: Cihaz Yüklemesi yalnızca Çıkarılabilir depolama alanı değil tüm cihazlara uygulanabilir.|
|Birincil Kimlik|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows|Birincil kimlik çıkarılabilir depolama alanını, CD/DVD'yi ve Taşınabilir Windows/WPD'yi içerir.|
|Cihaz Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md); <p> [USB cihazlarını ve diğer çıkarılabilir medyayı KONTROL etmek için USB Uç Nokta için Microsoft Defender](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz [. Standart USB Tanımlayıcıları](/windows-hardware/drivers/install/standard-usb-identifiers), örneğin, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Donanım Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md) <p> [USB cihazlarını ve diğer çıkarılabilir medyayı KONTROL etmek için USB Uç Nokta için Microsoft Defender](control-usb-devices-using-intune.md)|Windows|Sistemde USBSTOR\DiskGeneric_Flash_Disk___8.07 gibi bir dize tanımlanır; **Not**: Donanım kimliği benzersiz değildir; farklı cihazlar aynı değeri paylaşabilir.|
|Örnek Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md) <p> Cihaz Yüklemesi|Windows|Dize, sistem içinde cihazı benzersiz olarak tanımlar; örneğin, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611 veya&0|
|Kolay Ad|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows|Cihaza bağlı bir dize, örneğin Genel Flash Disk USB Cihazı|
|Satıcı Kimliği / Ürün Kimliği|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows <p> macOS|Satıcı Kimliği, USB komitenin satıcıya atadığınız dört basamaklı satıcı kodudur. Ürün Kimliği, satıcının cihaza atadığınız dört basamaklı ürün kodudur; Destek joker karakteri.|
|Seri NumarasıKimlik|[Çıkarılabilir depolama Access Control](device-control-removable-storage-access-control.md)|Windows <p> macOS |Örneğin, `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
