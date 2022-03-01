---
title: Uç Nokta Cihaz Denetimi Çıkarılabilir Cihaz Koruma için Microsoft Defender Depolama Koruma
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
ms.openlocfilehash: cc1c2a5fc05b795c0fc69ebc8a3b50dbf556960b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998179"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Uç Nokta Cihaz Denetimi Çıkarılabilir Cihaz Koruma için Microsoft Defender Depolama Koruma


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Uç Nokta için Microsoft Defender'da cihaz denetimi çıkarılabilir depolama koruması kullanıcıların, uç noktaların veya her ikisinin de yetkisiz çıkarılabilir depolama medyasını kullanmalarını engelleme.

## <a name="protection-policies"></a>Koruma ilkeleri

### <a name="removable-storage-access-control"></a>Çıkarılabilir depolama alanı erişim denetimi

**Özellikler**

- *Denetim* Çıkarılabilir depolamada dışlamayla veya dışlama olmadan çeşitli cihaz özelliklerine bağlı olarak Okuma veya Yazma veya Yürütme erişimi.
- *Engelleme* Okuma veya Yazma veya Dışlama olmadan erişim - Çeşitli cihaz özelliklerine göre belirli bir cihaza izin verme.

**Windows 10 ve Windows 11 destek ayrıntıları:**

- Cihaz düzeyinde kullanıcı düzeyinde uygulanır. veya her ikisini birden. Yalnızca belirli bir makinede belirli bir çıkarılabilir depolama alanına Okuma/Yazma/Yürütme erişimi gerçekleştiren belirli kişilerin erişmesine izin verme.
- MEM OMA-URI ve GPO desteği.
- 'Cihaz [Özellikleri' listelenmiştir](#device-properties).
- Çıkarılabilir depolama alanı Windows için bkz[. Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md).

**Desteklenen Platform** - Windows 10, Windows 11

**macOS destek ayrıntıları**:

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış olan tüm kullanıcılar için geçerlidir.
- macOS'a özgü bilgiler için bkz. [macOS için cihaz denetimi](mac-device-control-overview.md).

**Desteklenen platform** - macOS Catalina 10.15.4+ (sistem uzantıları etkin durumdadır)


### <a name="device-installation"></a>Cihaz yüklemesi

**Özellikler -** Çeşitli cihaz özelliklerine göre yükleme işlemini dışlamayla veya dışlama olmadan engelin.

**Windows 10 ve Windows 11 destek ayrıntıları:**

- Cihaz düzeyinde uygulanır: Aynı ilke, oturum açmış olan tüm kullanıcılar için geçerlidir.
- Nesne Microsoft Endpoint Manager İlkesi Nesnelerini destekler.
- 'Cihaz [Özellikleri' listelenmiştir](#device-properties).
- Usb cihazları ve diğer çıkarılabilir Windows hakkında daha fazla bilgi için bkz. Uç Nokta için [Microsoft Defender'ı kullanarak USB cihazları ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md).

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

Uç Nokta Cihaz Denetimi Için Microsoft Defender Çıkarılabilir Depolama Koruması, çıkarılabilir depolama erişimini aşağıdaki tabloda açıklanan özelliklere göre kısıtlamanıza olanak sağlar:

<br/><br/>

|Özellik Adı|Geçerli İlkeler|İşletim Sistemleri için geçerlidir|Açıklama|
|---|---|---|---|
|Cihaz Sınıfı|[Uç Nokta için Microsoft Defender'ı kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz. [cihaz kurulum sınıfı](/windows-hardware/drivers/install/overview-of-device-setup-classes). Aşağıdaki iki bağlantı Cihaz Kurulumu Sınıflarının tam listesini sağlar. 'Sistem Kullanımı' sınıfları çoğunlukla fabrikaya ait bir bilgisayar/makineyle gelen cihazlara başvururken, "Satıcı" sınıfları daha çok var olan bir bilgisayara/makineye bağlanıyor olabilir: Satıcılara Kullanılabilen Sistem Tanımlı Cihaz Kurulumu Sınıfları [- Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) sürücüleri ve Sistem Kullanımı [- Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use) sürücüleri için Ayrılmış Sistem Tanımlı Cihaz Kurulumu Sınıfları. **Not**: Cihaz Yüklemesi yalnızca Çıkarılabilir depolama alanı değil tüm cihazlara uygulanabilir.|
|Birincil Kimlik|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md)|Windows|Birincil kimlik çıkarılabilir depolama alanını, CD/DVD'yi ve Taşınabilir Windows/WPD'yi içerir.|
|Cihaz Kimliği|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md); <p> [Uç Nokta için Microsoft Defender'ı kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Cihaz Kimliği biçimleri hakkında bilgi için bkz [. Standart USB Tanımlayıcıları](/windows-hardware/drivers/install/standard-usb-identifiers), örneğin, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Donanım Kimliği|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md) <p> [Uç Nokta için Microsoft Defender'ı kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md)|Windows|Sistemde USBSTOR\DiskGeneric_Flash_Disk___8.07 gibi bir dize tanımlanır; **Not**: Donanım kimliği benzersiz değildir; farklı cihazlar aynı değeri paylaşabilir.|
|Örnek Kimliği|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md) <p> Cihaz Yüklemesi|Windows|Dize, sistem içinde cihazı benzersiz olarak tanımlar; örneğin, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611 veya&0|
|Kolay Ad|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md)|Windows|Cihaza bağlı bir dize, örneğin Genel Flash Disk USB Cihazı|
|Satıcı Kimliği / Ürün Kimliği|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md)|Windows <p> macOS|Satıcı Kimliği, USB komitenin satıcıya atadığınız dört basamaklı satıcı kodudur. Ürün Kimliği, satıcının cihaza atadığınız dört basamaklı ürün kodudur; Destek joker karakteri.|
|Seri NumarasıKimlik|[Çıkarılabilir depolama alanı Erişim Denetimi](device-control-removable-storage-access-control.md)|Windows <p> macOS |Örneğin, <SerialNumberId>002324B534BCB431B000058A</SerialNumberId>|
