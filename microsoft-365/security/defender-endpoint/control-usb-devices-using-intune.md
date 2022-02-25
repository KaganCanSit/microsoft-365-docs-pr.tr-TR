---
title: Intune (Usb cihazları ve diğer çıkarılabilir medyalar) kullanılarak USB cihazları ve diğer çıkarılabilir medyalar nasıl Windows 10
description: Intune ayarlarını, USB cihazları gibi çıkarılabilir bir depolama alanına yönelik tehditleri azaltacak şekilde yapılandırabilirsiniz.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.author: dansimp
author: dansimp
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.technology: mde
ROBOTS: NOINDEX
ms.openlocfilehash: 6ad51065ca4e919fe51cc4a2d5f4b0d53bc474b1
ms.sourcegitcommit: 1ef30b82d97bd998149235dc69d3c0e450e95285
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2021
ms.locfileid: "62959921"
---
# <a name="how-to-control-usb-devices-and-other-removable-media-using-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'ı kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme

**Geçerli olduğu yer: Uç** [Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2069559)

Microsoft çıkarılabilir medyanın güvenliğini sağlamak için katmanlı bir yaklaşım önerisinde ve Uç Nokta için Microsoft Defender, yetkisiz çevre birimlerinin cihazlarınıza zarar vermesini engellemeye yardımcı olmak için birden çok izleme ve denetim özelliği sunar:[](https://aka.ms/devicecontrolblog)

1. [Uç nokta gelişmiş av için Microsoft Defender'da çevre birimleri için bağlantı etkinliklerini keşfedin ve oynatin](#discover-plug-and-play-connected-events). Şüpheli kullanım etkinliğini tanımlama veya araştırma.

2. Çıkarılabilir cihazlara izin vermek veya engellemek ve tehditleri önlemek için yapılandırabilirsiniz.
    1. [USB cihaz kimliklerini kullanarak çıkarılabilir](#allow-or-block-removable-devices) disklere yazma erişimini reddetmek ve cihazları onaylamak veya reddetmek için, parçalı yapılandırmaya dayalı olarak çıkarılabilir cihazlara izin verme veya engelleme. Cihaz yükleme ayarlarını, bir kullanıcı veya grup Kullanıcı (Azure AD) kullanıcı Azure Active Directory cihaza göre esnek ilke ataması.

    2. [Şunları etkinleştirerek çıkarılabilir depolama cihazlarının](#prevent-threats-from-removable-storage) çıkarılabilir depolama alanıyla tehditlere neden olan tehditlerini önle:
        - Microsoft Defender Virüsten Koruma kötü amaçlı yazılım için çıkarılabilir depolama alanını taramak için gerçek zamanlı koruma (RTP) sağlar.
        - SALDıRı SURFACE Azaltma (ASR) USB kuralı, USB'den çalıştırilen güvenilmeyen ve imzalanmamış işlemleri engelleyebilir.
        - DMA saldırılarını azaltmak için Direct Memory Access (DMA) koruma ayarları (Kernel DMA Protection for İrtila ve bir kullanıcı oturum kapatana kadar DMA'yı engelleme dahil).

3. [Çıkarılabilir cihazların kullanımını bu](#create-customized-alerts-and-response-actions) yükleme ve oynatma olaylarına veya özel algılama kurallarıyla Uç Nokta için Diğer Microsoft Defender olaylarına göre izlemek için özelleştirilmiş uyarılar ve [yanıt eylemleri oluşturun](/microsoft-365/security/defender-endpoint/custom-detection-rules).

4. [Her çevre birimi](#respond-to-threats) tarafından bildirilen özelliklere göre çevre birimlerinin tehditlerine gerçek zamanlı olarak yanıt verin.

> [!NOTE]
> Bu tehdit azaltma önlemleri, kötü amaçlı yazılımların ortamınıza girileni önlemeye yardımcı olur. Kurumsal verileri ortamından ayrılmaya karşı korumak için, veri kaybı önleme ölçülerini de yapılandırabilirsiniz. Örneğin Windows 10 cihaz üzerinde [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md) ve [Windows](/windows/security/information-protection/create-wip-policy-using-intune-azure.md) Bilgi Koruması'yı yapılandırabilirsiniz. Bu koruma, kişisel bir cihazda depolansa bile şirket verilerini şifreler veya çıkarılabilir disklere yazma erişimini reddetmek için [Depolama/RemovableDenyWriteAccess CSP'yi](/windows/client-management/mdm/policy-csp-storage#storage-removablediskdenywriteaccess) kullanır. Buna ek olarak, Uç Nokta için Microsoft Defender'ı ve Azure [Information Protection'ı kullanarak](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview) Windows cihazlarında (takılan USB cihazları da dahil) dosyaları sınıflandırabilirsiniz ve koruyabilirsiniz.

## <a name="discover-plug-and-play-connected-events"></a>Bağlantılı etkinlikleri keşfetme ve oynatma

Şüpheli kullanım etkinliğini tanımlamak veya dahili soruşturmalar gerçekleştirmek için Uç nokta gelişmiş avı için Microsoft Defender'da bağlantı etkinliklerini  bakarak oynatabilirsiniz.
Uç nokta gelişmiş av sorguları için Defender örnekleri için bkz. Uç nokta arama sorguları için [Microsoft Defender GitHub.](https://github.com/Microsoft/WindowsDefenderATP-Hunting-Queries)

Gelişmiş Power BI için Kullanabileceğiniz Uç Nokta için Microsoft Defender'da örnek arama raporu şablonları vardır. Cihaz denetimi için de dahil olmak üzere bu örnek şablonlarla, Gelişmiş avlamanın gücünü cihaza Power BI. Daha [fazla GitHub için Power BI deposuna](https://github.com/microsoft/MDATP-PowerBI-Templates) bakın. Veri [tümleştirmesi hakkında daha fazla bilgi Power BI](/microsoft-365/security/defender-endpoint/api-power-bi) için bkz. Power BI oluşturma.

## <a name="allow-or-block-removable-devices"></a>Çıkarılabilir cihazlara izin verme veya engelleme
Aşağıdaki tabloda, Uç Nokta için Microsoft Defender'ın parçalı yapılandırmaya dayalı olarak çıkarılabilir cihazlara izin verme veya engelleme yolları açık almaktadır.

<br>

****

|Denetim|Açıklama|
|---|---|
|[USB sürücülerini ve diğer çevre birimlerini kısıtlama](#restrict-usb-drives-and-other-peripherals)|Kullanıcıların yalnızca yetkili/yetkisiz cihaz veya cihaz türleri listesinde bulunan USB sürücülerini ve diğer çevre birimlerini yüklemesine izin ve önleyebilirsiniz.|
|[Çıkarılabilir depolamanın yüklemesini ve kullanımını engelleme](#block-installation-and-usage-of-removable-storage)|Çıkarılabilir depolama alanını yükleyesiniz veya kullanamazlar.|
|[Özellikle onaylanmış çevre birimlerinin yüklenmesine ve kullanımına izin ver](#allow-installation-and-usage-of-specifically-approved-peripherals)|Yalnızca üretici yazılımında belirli özellikleri raporan onaylı çevre birimlerini yükleyebilir ve kullanabilirsiniz.|
|[Özellikle yasak olan çevre birimlerinin yüklemesini engelleme](#prevent-installation-of-specifically-prohibited-peripherals)|Kendi üretici yazılımında belirli özellikleri raporan yasaklı çevre birimlerini yük yüklemeniz veya kullanmanız yasaktır.|
|[Eşleşen cihaz örneği kimlikleriyle özel olarak onaylanmış çevre birimlerinin yüklenmesine ve kullanımına izin verme](#allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids)|Yalnızca bu cihaz örneği kimliklerinin herhangi birini kullanan onaylı çevre birimlerini yükleyebilir ve kullanabilirsiniz.|
|[Eşleşen cihaz örneği kimlikleriyle özellikle yasaklanan çevre birimlerinin kurulumu ve kullanımını engelleme](#prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids)|Bu cihaz örneği kimlikleri ile eşleşmesi yasaklanan çevre birimlerini yükamaz veya kullanamazsiniz.|
|[Alan kullanan hizmetleri Bluetooth](#limit-services-that-use-bluetooth)|Bu hizmeti kullanabileceğiniz hizmetleri Bluetooth.|
|

### <a name="restrict-usb-drives-and-other-peripherals"></a>USB sürücülerini ve diğer çevre birimlerini kısıtlama

Kötü amaçlı yazılım bulaşmalarını veya veri kaybını önlemek için, kuruluş USB sürücülerini ve diğer çevre birimlerini kısıtlar. Aşağıdaki tabloda, Uç Nokta için Microsoft Defender'ın USB sürücülerinin ve diğer çevre birimlerinin yüklenmesi ve kullanımını engellemeye yardımcı olduğu yollar açık almaktadır.

<br>

****

|Denetim|Açıklama
|---|---|
|[USB sürücülerinin ve diğer çevre birimlerinin yüklenmesine ve kullanımına izin verme](#allow-installation-and-usage-of-usb-drives-and-other-peripherals)|Kullanıcıların yalnızca yetkili cihazlar veya cihaz türleri listesinde bulunan USB sürücülerini ve diğer çevre birimlerini yüklemesine izin verme|
|[USB sürücülerinin ve diğer çevre birimlerinin yüklemesini ve kullanımını engelleme](#prevent-installation-and-usage-of-usb-drives-and-other-peripherals)|Kullanıcıların yetkisiz cihazlar ve cihaz türleri listesinde bulunan USB sürücülerini ve diğer çevre birimlerini yüklemesini engelleme|
|

Yukarıdaki denetimlerin hepsi Intune Yönetim Şablonları [aracılığıyla ayarlanır](/intune/administrative-templates-windows). İlgili ilkeler burada Intune Yönetici Şablonları'nın içinde yer almaktadır:

![Yönetici Şablonları listesinin ekran görüntüsü.](images/admintemplates.png)

> [!NOTE]
> Intune kullanarak, Azure AD kullanıcı ve/veya cihaz gruplarına cihaz yapılandırma ilkeleri uygulayabilirsiniz.
Yukarıdaki ilkeler Cihaz Yükleme [CSP ayarları ve Cihaz Yükleme GPOS'ları](/windows/client-management/mdm/policy-csp-deviceinstallation) [aracılığıyla da ayarlanabilirsiniz](/previous-versions/dotnet/articles/bb530324(v=msdn.10)).
>
> Üretimde uygulamadan önce, önce pilot bir kullanıcı ve cihaz grubuyla bu ayarları test edin ve geliştirin.
USB cihazlarını denetleme hakkında daha fazla bilgi için bkz. Uç nokta [için Microsoft Defender blogu](https://www.microsoft.com/security/blog/2018/12/19/windows-defender-atp-has-protections-for-usb-and-removable-devices/).

#### <a name="allow-installation-and-usage-of-usb-drives-and-other-peripherals"></a>USB sürücülerinin ve diğer çevre birimlerinin yüklenmesine ve kullanımına izin verme

USB sürücülerin ve diğer çevre birimlerinin yüklenmesine ve kullanımına izin vermenin bir yolu, her şeye izin vererek başlamaktır. Daha sonra, izin verilebilir USB sürücülerini ve diğer çevre birimlerini azaltmaya başlayabilirsiniz.

> [!NOTE]
> Yetkisiz bir USB çevre birimi, USB özelliklerini kullanan üretici yazılımına sahip olduğundan, yalnızca onaylı USB çevre birimlerine izin vermenizi ve bu çevre birimlerine erişecek kullanıcıları sınırlamanizi öneririz.

1. Enable **Prevent installation of devices not described by other policy settings to** all users.
2. Tüm **cihaz kurulum sınıfları için bu cihaz kurulum sınıflarına uygun sürücüleri kullanarak cihazların** [yüklenmesine izin ver'i etkinleştirin](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

İlkeyi zaten yüklü olan cihazlara uygulamak için, bu ayarın geçerli olduğu önleme ilkelerini kullanın.

Cihaz yüklemesine izin ver ilkesi yapılandırılamazken, tüm üst özniteliklere de izin ver gerekir. Cihaz Yöneticisi'ni açarak ve bağlantıyı görüntüerek cihazın ebeveynlerini görüntüebilirsiniz.

![Cihazlara göre bağlantı.](images/devicesbyconnection.png)

Bu örnekte, şu sınıfların ekli olması gerekir: HID, Klavye ve {36fc9e60-c465-11cf-8056-444553540000}. Daha [fazla bilgi için Bkz. Microsoft tarafından sağlanan USB](/windows-hardware/drivers/usbcon/supported-usb-classes) sürücüleri.

![Cihaz ana bilgisayar denetleyicisi.](images/devicehostcontroller.jpg)

Belirli cihazlarla kısıtlamak için, sınırlamak istediğiniz çevre biriminin cihaz kurulum sınıfını kaldırın. Ardından, eklemek istediğiniz cihaz kimliğini ekleyin. Cihaz Kimliği, cihazın satıcı kimliği ve ürün kimliği değerlerini temel alarak hazırlar. Cihaz kimliği biçimleri hakkında bilgi için bkz [. Standart USB Tanımlayıcıları](/windows-hardware/drivers/install/standard-usb-identifiers).

Cihaz kimliklerini bulmak için bkz [. Cihaz kimliğini bulma](#look-up-device-id).

Örneğin:

1. Sınıf USBDevice'i Bu cihaz **kurulumuyla eşleşmesi sürücüleri kullanarak cihazların yüklenmesine izin ver bağlantısından kaldırın**.
2. Bu cihaz kimlikleri ile eşleşmesi **gereken cihazın yüklenmesine izin ver girişsine izin vermek için cihaz kimliğini ekleyin**.

#### <a name="prevent-installation-and-usage-of-usb-drives-and-other-peripherals"></a>USB sürücülerinin ve diğer çevre birimlerinin yüklemesini ve kullanımını engelleme

Bir cihaz sınıfının veya belirli cihazların yüklenmesine engel olmak için, cihaz yüklemesini engelleme ilkelerini kullanabilirsiniz:

1. Bu **cihaz kimlikleri ile eşleşmesi cihazlar yüklemesini engelle'yi etkinleştirin** ve bu cihazları listeye ekleyin.
2. Bu **cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların kurulumunu engelle'yi etkinleştirin**.

> [!NOTE]
> Cihaz yüklemesine izin verme ilkeleri, cihaz yüklemesine izin verme ilkelerine göre önceliklidir.

Bu **cihaz kimliklerinden herhangi biri ile** eşleşmeye sahip cihazların yüklemeyi engelleme ilkesi, Cihaz yüklemesi Windows cihazların listesini belirtmenize olanak tanır.

Şu cihaz kimliklerinin herhangi birini eşleyen cihazlar yüklemesini engellemek için:

1. [Yüklemesini engellemek](#look-up-device-id) istediğiniz Windows cihaz kimliğine bakın.

   ![Satıcıyı veya ürün kimliğini ara.](images/lookup-vendor-product-id.png)

2. Bu **cihaz kimlikleri ile eşleşmesi cihazlar yüklemesini engelle'yi etkinleştirin** ve satıcıyı veya ürün kimliklerini listeye ekleyin.

    ![Listeyi engellemek için satıcı kimliği ekleyin.](images/add-vendor-id-to-prevent-list.png)

#### <a name="look-up-device-id"></a>Cihaz kimliğini ara

Cihaz kimliğine bakmak için Cihaz Yöneticisi'ni kullanabilirsiniz.

1. Cihaz Yöneticisi'ni açın.
2. **Görüntüle'ye** tıklayın ve Cihazlar **bağlantı ile'yi seçin**.
3. Ağaç hakkında, cihaza sağ tıklayın ve Özellikler'i **seçin**.
4. Seçili cihazın iletişim kutusunda Ayrıntılar **sekmesine tıklayın** .
5. Özellik açılan **listesine** tıklayın ve Donanım **Kimlikleri'ne tıklayın**.
6. En üst kimlik değerine sağ tıklayın ve Kopyala'yı **seçin**.

Cihaz Kimliği biçimleri hakkında bilgi için bkz [. Standart USB Tanımlayıcıları](/windows-hardware/drivers/install/standard-usb-identifiers).

Satıcı kimlikleri hakkında bilgi için [bkz. USB üyeleri](https://www.usb.org/members).

PowerShell kullanarak bir cihaz satıcı kimliğini veya ürün kimliğini (cihaz kimliğinin bir parçası olan) arama örneği aşağıda vemektedir:

```powershell
Get-WMIObject -Class Win32_DiskDrive | Select-Object -Property *
```

Bu **cihaz kurulumu sınıfları ile uyumlu sürücüleri** kullanan cihazların yüklemeyi engelleme ilkesi, cihaz kurulum sınıflarını belirtmenize ve bu Windows engellenebilir.

Belirli cihaz sınıflarının yüklemesini önlemek için:

1. Sistem Tanımlı Cihaz Kurulumu Sınıfları Satıcılara Uygun [olarak, cihaz kurulum sınıfının GUID'lerini bulun](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

2. Bu **cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların yüklemesini engelle'yi** etkinleştirin ve sınıf GUID'sini listeye ekleyin.

    > [!div class="mx-imgBorder"]
    > ![Listeyi engellemek için cihaz kurulum sınıfı ekleyin.](images/Add-device-setup-class-to-prevent-list.png)

### <a name="block-installation-and-usage-of-removable-storage"></a>Çıkarılabilir depolamanın yüklemesini ve kullanımını engelleme

1. [Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com/) oturum açın.

2. Cihazlar **Yapılandırma Profilleri** \> **Profil** **Oluştur'a**\> tıklayın.

    > [!div class="mx-imgBorder"]
    > ![Cihaz yapılandırma profili oluşturun.](images/create-device-configuration-profile.png)

3. Aşağıdaki ayarları kullanın:
   - Ad: Profil için bir ad yazın
   - Açıklama: Açıklama yazın
   - Platform: Windows 10 ve üzeri
   - Profil türü: Cihaz kısıtlamaları

   > [!div class="mx-imgBorder"]
   > ![Profil oluştur'a tıklayın.](images/create-profile.png)

4. Genel **Yapılandır'a** \> **tıklayın**.

5. Çıkarılabilir **depolama alanı ve** **USB bağlantısı (yalnızca mobil) için Engelle'yi** **seçin**. **Çıkarılabilir depolama alanı** USB sürücüleri içerir, **ANCAK USB bağlantısı (** yalnızca mobil) USB şarj etme özelliğine dahil değildir, ancak yalnızca mobil cihazlardaki diğer USB bağlantılarını içerir.

   ![Genel ayarlar'a tıklayın.](images/general-settings.png)

6. Genel **ayarlar ve** Cihaz **kısıtlamaları'na** kapatmak **için Tamam'a tıklayın**.

7. Profili **kaydetmek için** Oluştur'a tıklayın.

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals"></a>Özellikle onaylanmış çevre birimlerinin yüklenmesine ve kullanımına izin ver

Kurulmalarına izin verilen çevre birimleri kendi donanım kimlikleriyle [belirtilebilir](/windows-hardware/drivers/install/device-identification-strings). Sık kullanılan tanımlayıcı yapılarının listesi için bkz. [Cihaz Tanımlayıcı Biçimleri](/windows-hardware/drivers/install/device-identifier-formats). Blokları ve cihazların beklenenlere izin olduğundan emin olmak için, bunu öncesinde yapılandırmayı test edin. İdeal olarak donanımın çeşitli örneklerini test etmektir. Örneğin, yalnızca bir TANE yerine birden çok USB anahtarını test etmek.

Belirli cihaz kimliklerinin yüklenmesine izin veren bir SyncML örneği için bkz. [DeviceInstallation/AllowInstallationOfMatchingDeviceIDS CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceids). Belirli cihaz sınıflarına izin vermek için bkz [. DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses).
Belirli cihazların yüklenmesine izin verme özelliği [, DeviceInstallation/PreventInstallationOfDevicesNotDescribedByOtherPolicySettings'i de etkinleştirmeyi gerektirir](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofdevicesnotdescribedbyotherpolicysettings).

### <a name="prevent-installation-of-specifically-prohibited-peripherals"></a>Özellikle yasak olan çevre birimlerinin yüklemesini engelleme

Uç Nokta için Microsoft Defender, şu seçeneklerden birini kullanarak yasak çevre birimlerinin yüklenmesi ve kullanımını engeller:

- [Yönetim Şablonları,](/intune/administrative-templates-windows) eşleşen donanım kimliğine veya kurulum sınıfına sahip tüm aygıtı engelleyebilir.
- [Intune'da özel](/windows/client-management/mdm/policy-csp-deviceinstallation) bir profille Cihaz Yükleme CSP ayarları. Belirli cihaz [kimliklerinin yüklenmesine veya belirli cihaz](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) [sınıflarının yüklenmesine engel olabilirsiniz](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdevicesetupclasses).

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids"></a>Eşleşen cihaz örneği kimlikleriyle özel olarak onaylanmış çevre birimlerinin yüklenmesine ve kullanımına izin verme

Yüklemesine izin verilen çevre birimleri kendi cihaz örnek [kimlikleri ile belirtilebilir](/windows-hardware/drivers/install/device-instance-ids). Cihazların beklenenlere izin olduğundan emin olmak için, yapılandırmayı yuvarlamadan önce test edin. İdeal olarak donanımın çeşitli örneklerini test etmektir. Örneğin, yalnızca bir TANE yerine birden çok USB anahtarını test etmek.

[DeviceInstallation/AllowInstallationOfMatchingDeviceInstanceIDS](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceinstanceids) ilke ayarını yapılandırarak, eşleşen cihaz örneği kimlikleriyle onaylı çevre birimlerinin yüklenmesine ve kullanımına izin veebilirsiniz.

### <a name="prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids"></a>Eşleşen cihaz örneği kimlikleriyle özellikle yasaklanan çevre birimlerinin kurulumu ve kullanımını engelleme

Yüklemesi yasak olan çevre birimleri cihaz örnek [kimlikleri ile belirtilebilir](/windows-hardware/drivers/install/device-instance-ids). Cihazların beklenenlere izin olduğundan emin olmak için, yapılandırmayı yuvarlamadan önce test edin. İdeal olarak donanımın çeşitli örneklerini test etmektir. Örneğin, yalnızca bir TANE yerine birden çok USB anahtarını test etmek.

[DeviceInstallation/PreventInstallationOfMatchingDeviceInstanceIDS](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceinstanceids) ilke ayarını yapılandırarak, eşleşen cihaz örneği kimlikleriyle yasak çevre birimlerinin yüklenmesine engel olabilirsiniz.

### <a name="limit-services-that-use-bluetooth"></a>Alan kullanan hizmetleri Bluetooth

Intune kullanarak, "izin verilen hizmetler" Bluetooth [kullanabileceğiniz Bluetooth sınırlandırabilirsiniz](/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide). "İzin verilen hizmetler" Bluetooth varsayılan durumu, her şeye izin ver anlamına gelir.  Bir hizmet eklenmiştir ve bu izin verilenler listesine eklenir. Müşteri Klavyeler ve Fareler değerlerini ekliyorsa ve dosya aktarım GUID'lerini ekleyene kadar dosya aktarımı engellenmiş olabilir.

> [!div class="mx-imgBorder"]
> ![ayarlar Bluetooth ekran görüntüsü.](images/bluetooth.png)

## <a name="prevent-threats-from-removable-storage"></a>Çıkarılabilir depolama alanına yönelik tehditleri önleme

Çıkarılabilir depolama cihazlarında, kuruluşa ek güvenlik riski olabilir. Uç Nokta için Microsoft Defender çıkarılabilir depolama aygıtlarda kötü amaçlı dosyaları tanımlamaya ve engellemeye yardımcı olabilir.

Uç Nokta için Microsoft Defender ayrıca, harici tehditleri önlemek için USB çevre birimlerinin cihazlarda kullanılmaktadır. Bunu yapmak için USB çevre birimleri tarafından bildirilen özellikleri kullanarak cihaza yüklerinin olup olmadığını ve kullanılap kullanılamaylarını belirler.

CIHAZ yükleme ilkelerini, örneğin telefonlar gibi bağlı cihazları kullanarak USB cihazlarını veya diğer cihaz sınıflarını engellemeye devam edebilirsiniz.

> [!NOTE]
> Organizasyona büyük dağıtım öncesinde her zaman pilot bir kullanıcı ve cihaz grubuyla bu ayarları test edin ve geliştirin.

Aşağıdaki tabloda, Uç Nokta için Microsoft Defender'ın çıkarılabilir depolama alanına yönelik tehditlere karşı nasıl yardımcı olduğu açık almaktadır.

USB cihazlarını denetleme hakkında daha fazla bilgi için bkz. Uç nokta [için Microsoft Defender blogu](https://aka.ms/devicecontrolblog).

<br>

****

|Denetim|Açıklama|
|---|---|
|[Taramayı Microsoft Defender Virüsten Koruma etkinleştirme](#enable-microsoft-defender-antivirus-scanning)|Gerçek Microsoft Defender Virüsten Koruma tarama veya zamanlanmış taramalar için taramayı etkinleştirin.|
|[USB çevre birimleri üzerinde güvenilmeyen ve imzalanmamış işlemleri engelleme](#block-untrusted-and-unsigned-processes-on-usb-peripherals)|Imzalanmamış veya güvenilmeyen USB dosyalarını engelin.|
|[Doğrudan Bellek Erişimi (DMA) saldırılarına karşı koruma](#protect-against-direct-memory-access-dma-attacks)|DMA saldırılarına karşı korumak için ayarları yapılandırabilirsiniz.|
|

> [!NOTE]
> Yetkisiz bir USB çevre birimi, USB özelliklerini kullanan üretici yazılımına sahip olduğundan, yalnızca onaylı USB çevre birimlerine izin vermenizi ve bu çevre birimlerine erişecek kullanıcıları sınırlamanizi öneririz.

### <a name="enable-microsoft-defender-antivirus-scanning"></a>Taramayı Microsoft Defender Virüsten Koruma Etkinleştirme

Çıkarılabilir depolama alanını tek tek [Microsoft Defender Virüsten Koruma, gerçek](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) zamanlı korumayı etkinleştirmeyi veya taramalar için çıkarılabilir sürücüleri taramalar için zamanlamayı ve yapılandırmayı gerektirir.

- Gerçek zamanlı koruma etkinleştirilirse, dosyalara erişilmeden ve yürütülmeden önce taranır. Tarama kapsamı, USB sürücüleri gibi takılan çıkarılabilir cihazlar da dahil olmak üzere tüm dosyaları içerir. İsterseniz, USB sürücü takılı olduktan sonra özel bir tarama yapmak için bir [PowerShell](/samples/browse/?redirectedfrom=TechNet-Gallery) betiği çalıştırabilirsiniz, böylece Microsoft Defender Virüsten Koruma çıkarılabilir bir cihaz takılı olarak tüm dosyaları çıkarılabilir bir cihaza taramaya başlar. Bununla birlikte, özellikle de büyük depolama cihazlarında, gelişmiş tarama performansı için gerçek zamanlı korumayı etkinleştirmenizi öneririz.

- Zamanlanmış taramalar kullanılıyorsa, tam tarama sırasında çıkarılabilir cihazı taramak için DisableRemovableDriveScanning ayarını devre dışı bırakmanız (varsayılan olarak etkindir) gerekir. Çıkarılabilir cihazlar, DisableRemovableDriveScanning ayarına bakılmaksızın, hızlı veya özel bir tarama sırasında taranır.

> [!NOTE]
> Tarama için gerçek zamanlı izleme özelliğini etkinleştirmenizi öneririz. Intune'da, Gerçek zamanlı izleme için Windows 10'yi  \>  \> Yapılandırma'da **Microsoft Defender Virüsten Koruma** \> **izlemeyi etkinleştirebilirsiniz**.

<!-- Need to build out point in the preceding note.
-->

### <a name="block-untrusted-and-unsigned-processes-on-usb-peripherals"></a>USB çevre birimleri üzerinde güvenilmeyen ve imzalanmamış işlemleri engelleme

Son kullanıcılar, kötü amaçlı yazılımdan etkilenen çıkarılabilir cihazları takabilir.
Bulaşmaları önlemek için, şirket imzalanmamış veya güvenilmeyen USB dosyalarını engelleyebilir.
Alternatif olarak şirketler, USB çevre birimi üzerinde yürüten [](/microsoft-365/security/defender-endpoint/attack-surface-reduction) güvenilmeyen ve imzalanmamış işlemlerin etkinliğini izlemek için saldırı yüzeyini azaltma kurallarının denetim özelliğiden de faydalanabilirsiniz.
Bu işlem, USB'den **çalıştırarak** yalnızca Engelle veya Denetle'ye (sırasıyla) güvenilmeyen ve  **imzalanmamış işlemler ayar** kullanarak yapılabilir.
Bu kuralla, yöneticiler SD kartları da dahil olmak üzere USB çıkarılabilir sürücülerden çalıştırılabilen imzalanmamış veya güvenilmeyen yürütülebilir dosyaları önleyen veya denetlemeye yarayabilirsiniz.
Etkilenen dosya türleri yürütülebilir dosyalar (.exe, .dll veya .scr gibi) ve PowerShell (.ps), VisualBasic (.vbs) veya JavaScript (.js) dosyaları gibi betik dosyalarını içerir.

Bu ayarlar gerçek [zamanlı korumayı etkinleştirmeyi gerektirir](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).

1. Oturum [açma Microsoft Endpoint Manager.](https://endpoint.microsoft.com/)

2. **Cihazlar'a** \> **Windows** \> **İlkeleri Profil** **Oluştur'a**\> tıklayın.

    ![Cihaz yapılandırma profili oluşturun.](images/create-device-configuration-profile.png)

3. Aşağıdaki ayarları kullanın:
   - Platform: Windows 10 ve üzeri
   - Profil türü: Cihaz kısıtlamaları

   > [!div class="mx-imgBorder"]
   > ![Uç nokta koruma profili oluşturma.](images/create-endpoint-protection-profile.png)

4. **Oluştur'a tıklayın**.

5. **USB'den gelen imzasız ve güvenilmeyen işlemler için Engelle'yi** **seçin**.

   ![Güvenilmeyen işlemleri engelin.](images/block-untrusted-processes.png)

6. Ayarları **ve** Cihaz kısıtlamalarını kapatmak için **Tamam'a tıklayın**.

### <a name="protect-against-direct-memory-access-dma-attacks"></a>Doğrudan Bellek Erişimi (DMA) saldırılarına karşı koruma

DMA saldırıları, bir PC'de yer alan hassas bilgilerin açıklanmasına, hatta saldırganların kilit ekranından atlanmasına veya bilgisayarları uzaktan kontrol sınasına olanak veren kötü amaçlı yazılım eklemelerinin açıklanmasına neden olabilir. Aşağıdaki ayarlar DMA saldırılarını önlemeye yardımcı olur:

1. Microsoft, Windows 10 1803 sürümünden başarak, Oğuz bağlantı noktaları üzerinden DMA saldırılarına karşı yerel koruma sağlamak için [Kernel DMA Koruması'yı](/windows/security/information-protection/kernel-dma-protection-for-thunderbolt.md) sunmaktadır. Kernel DMA Protection for Tüm Sistem üreticileri tarafından etkinleştirilir ve kullanıcılar tarafından açamaz veya kapatamaz.

   1809 Windows 10 başarak, [DMA Guard CSP'yi yapılandırarak Kernel DMA Protection düzeyini ayarlayabilirsiniz](/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy). Bu, cihaz belleği yalıtımnı desteklemeen çevre birimleri için ek bir denetimdir (DMA yeniden kırpma olarak da bilinir). Bellek yalıtım, işletim sistemi tarafından bir cihazın izin verilmeyen I/O veya bellek erişimini çevre birimi (bellek korumalı alan) tarafından engellemek için cihazın I/O Bellek Yönetim Birimi'den (IOMMU) yararlanan bir özelliktir. Başka bir deyişle, işletim sistemi çevre birimine belirli bir bellek aralığı atar. Çevre birimi atanmış aralığın dışında bir belleğe okumaya/yazmaya çalışırsa, işletim sistemi tarafından engeller.

   Cihaz belleği yalıtımnı destekleyen çevre birimleri her zaman birbirine bağlı olabilir. Ancak kullanıcı oturum a girişine izin verdikten sonra engellenemeyecek, izin verilmiyor veya izin verilmiyor çevre birimleri (varsayılan).

2. Kernel Windows 10 korumasını desteklemeen sistemlerde şunları şunları yapabiliriz:

   - [Kullanıcı oturum aya kadar DMA'yı engelleme](/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)
   - [Bağlantı noktası üzerinden tüm bağlantıları engelleme (USB cihazları dahil)](https://support.microsoft.com/help/2516445/blocking-the-sbp-2-driver-and-thunderbolt-controllers-to-reduce-1394-d)

## <a name="create-customized-alerts-and-response-actions"></a>Özelleştirilmiş uyarılar ve yanıt eylemleri oluşturma

WDATP Bağlayıcısı ve özel algılama kurallarıyla özel uyarılar ve yanıt eylemleri oluşturabilirsiniz:

**Wdatp Bağlayıcısı yanıt Eylemleri:**

**Araştır:** Soruşturmaları başlatıp araştırma paketini toplayın ve bir makinesi yalıtmak.

USB **cihazlarda** tehdit tarama.

**Önceden tanımlanmış bir küme dışında** makinede tüm uygulamaların yürütülmesini kısıtlama

MDATP bağlayıcısı, Outlook, Teams, Slack vb. dahil 200'den fazla önceden tanımlanmış bağlayıcıdan biridir. Özel bağlayıcılar oluşturabilirsiniz.

- [WDATP Bağlayıcısı Yanıt Eylemleri hakkında daha fazla bilgi](/connectors/wdatp/)

**Özel Algılama Kuralları Yanıt Eylemi:**

Hem makine hem de dosya düzeyi eylemleri uygulanabilir.

- [Özel Algılama Kuralları Yanıt Eylemleri hakkında daha fazla bilgi](/microsoft-365/security/defender-endpoint/custom-detection-rules)

Cihaz denetimi ile ilgili önceden arama olayları ve özel uyarı oluşturma hakkında örnekler hakkında bilgi için bkz. Gelişmiş arama güncelleştirmeleri [: USB olayları, makine](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/Advanced-hunting-updates-USB-events-machine-level-actions-and/ba-p/824152) düzeyinde eylemler ve şema değişiklikleri.

## <a name="respond-to-threats"></a>Tehditlere yanıt verme

Uç Nokta Özel Algılama Kuralları için Microsoft Defender'la özel uyarılar [ve otomatik yanıt eylemleri oluşturabilirsiniz](/microsoft-365/security/defender-endpoint/custom-detection-rules). Özel algılama içindeki yanıt eylemleri, hem makine hem de dosya düzeyi eylemlerini içerir. Ayrıca, Uç nokta için Microsoft Defender bağlayıcısı ile birlikte [Power Apps ve Flow](https://powerapps.microsoft.com/) [kullanarak uyarılar ve otomatik yanıt eylemleri de oluşturabilirsiniz](/connectors/wdatp/).[](https://flow.microsoft.com/) Bağlayıcı, soruşturma, tehdit tarama ve çalışan uygulamaları kısıtlama eylemleri destekler. Bu, Outlook, Teams, Slack ve daha fazlası dahil 200'den fazla önceden tanımlanmış bağlayıcıdan biridir. Özel bağlayıcılar da oluşturabilirsiniz. [Bağlayıcılar hakkında daha](/connectors/) fazla bilgi edinmek için bkz. Bağlayıcılar.

Örneğin iki yaklaşımdan birini kullanarak, USB cihazı Microsoft Defender Virüsten Koruma makineye takılanda otomatik olarak çalıştırabilirsiniz.

## <a name="related-topics"></a>İlgili konular

- [E-posta için gerçek zamanlı korumayı Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)
- [Defender/AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)
- [İlke/DeviceInstallation CSP](/windows/client-management/mdm/policy-csp-deviceinstallation)
- [Çıkarılabilir bir cihazda özel tarama işlemi gerçekleştirme](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Cihaz Denetimi Power BI raporlama şablonu](https://github.com/microsoft/MDATP-PowerBI-Templates)
- [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md)
- [Windows Koruma](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure.md)
