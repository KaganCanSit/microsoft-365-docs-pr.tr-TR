---
title: Kuruluşunuzun cihazlarını İş için Microsoft Defender ekleme
description: Kuruluşunuzun cihazlarını İş için Microsoft Defender ekleme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a03d79da004dab7a68e691c6c2a8ac21ac2b7501
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318192"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Kayıtlı cihazları İş için Microsoft Defender ekleme

Cihazları kaydettiğinize göre, yeni nesil koruma (virüsten koruma, kötü amaçlı yazılımdan koruma ve bulut tabanlı koruma), güvenlik duvarı koruması, web içeriği filtreleme ve daha fazlasını uygulamak için cihazları İş için Microsoft Defender eklemelisiniz. 

Cihazları eklemek için çeşitli seçenekler arasından seçim yapabilirsiniz:

- [zaten Microsoft Endpoint Manager kayıtlı Windows cihazlar için otomatik ekleme kullanma](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Windows ve macOS cihazları eklemek için yerel betik kullanma](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Cihazları (Windows](#use-microsoft-endpoint-manager-to-enroll-devices), macOS, iOS ve Android) kaydetmek ve ardından bu cihazlara İş için Defender ilkelerini uygulamak için Endpoint Manager kullanın

Bu makale şunları da içerir:

- [Windows cihazda algılama testi çalıştırma](#run-a-detection-test-on-a-windows-device)

- [Cihazları aşamalı olarak ekleme](#onboard-devices-gradually)

- Bir [cihaz](#offboard-a-device) değiştirilirse veya biri kuruluştan ayrılırsa cihazı çıkarma

> [!IMPORTANT]
> Bir sorun oluşursa ve ekleme işleminiz başarısız olursa sorun [giderme İş için Microsoft Defender](../security/defender-business/mdb-troubleshooting.yml) bakın.

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>zaten Microsoft Endpoint Manager kayıtlı Windows cihazlar için otomatik ekleme kullanma

Otomatik ekleme seçeneği yalnızca Windows cihazlar için geçerlidir. Aşağıdaki koşullar karşılanırsa otomatik ekleme kullanılabilir:

- Kuruluşunuz, İş için Defender'ı (Microsoft 365 İş Ekstra) almadan önce Microsoft Intune'da zaten Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi (MDM) kullanıyordu  müşteriler zaten Microsoft Intune).

- Endpoint Manager kayıtlı Windows cihazınız zaten var.

Windows cihazlar zaten Endpoint Manager kayıtlıysa, siz İş için Defender'ı ayarlama ve yapılandırma sürecindeyken İş için Defender bu cihazları algılar. Windows cihazlarınızın tümü veya bazıları için otomatik ekleme kullanmak isteyip istemediğiniz sorulur. Tüm Windows cihazları aynı anda ekleyebilir veya başlamak için belirli cihazları seçip daha sonra daha fazla cihaz ekleyebilirsiniz.

> [!TIP]
> "Tüm cihazlar kaydedildi" seçeneğini belirlemenizi öneririz. Bu şekilde, Windows cihazlar daha sonra Endpoint Manager kaydedildiğinde otomatik olarak İş için Defender'a eklenir.
Otomatik ekleme hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender ayarlamak için sihirbazı kullanma](../security/defender-business/mdb-use-wizard.md) konusundaki 2. Adım.

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Windows ve macOS cihazları eklemek için yerel betik kullanma

Windows ve Mac cihazlarını eklemek için yerel bir betik kullanabilirsiniz. Bir cihazda ekleme betiğini çalıştırdığınızda, Azure Active Directory ile bir güven oluşturur (bu güven yoksa), cihazı Microsoft Endpoint Manager kaydeder (henüz kaydedilmemişse) ve ardından cihazı İş için Defender'a ekler. Bu yöntem, İş için Defender'a cihaz ekleme için kullanışlıdır. Aynı anda en fazla 10 cihaz ekleyebilirsiniz.

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** >  **Endpoints'i** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

3. **Windows 10, 11** veya **macOS** gibi bir işletim sistemi seçin ve ardından **Dağıtım yöntemi** bölümünde **Yerel betik'i** seçin. 

4. **Ekleme paketini indir'i** seçin. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz. (**macOS** seçtiyseniz **Yükleme paketini indir'i** de seçip çıkarılabilir cihazınıza kaydedin.)

5. Aşağıdaki kılavuzu kullanın:

   - Windows cihazlar: [Yerel betik kullanarak Windows cihazları ekleme](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - macOS cihazlar: [macOS'da Uç Nokta için Microsoft Defender için el ile dağıtım](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Cihazları kaydetmek için Microsoft Endpoint Manager kullanma

Bir cihazı kaydetmek için, cihazı kendiniz kaydedin veya kullanıcılarınızın şirket portalında oturum açmasını ve gerekli uygulamaları kaydedip yüklemesini sağlayın. 

İş için Defender'ı almadan önce zaten Endpoint Manager (Microsoft Intune ve Mobil Cihaz Yönetimi dahil) kullanıyorsanız, kuruluşunuzun cihazlarını eklemek için Endpoint Manager kullanmaya devam edebilirsiniz. Endpoint Manager ile iOS ve Android cihazları dahil olmak üzere bilgisayarları, tabletleri ve telefonları ekleyebilirsiniz.

Bkz[. Microsoft Intune'da cihaz kaydı](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Windows cihazda algılama testi çalıştırma

Windows cihazları İş için Defender'a ekledikten sonra, her şeyin düzgün çalıştığından emin olmak için Windows bir cihazda algılama testi çalıştırabilirsiniz.

1. Windows cihazında bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ni açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştırıldıktan sonra Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa algılama testi tamamlandı olarak işaretlenir ve yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yaklaşık on dakika içinde yeni bir uyarı görünür.

## <a name="onboard-devices-gradually"></a>Cihazları aşamalı olarak ekleme

Cihazları *aşamalı cihaz ekleme* olarak adlandırdığımız aşamalara eklemeyi tercih ediyorsanız şu adımları izleyin: 

1. Eklemek istediğiniz bir cihaz kümesini belirleyin.

2. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

3. Gezinti bölmesinde **Ayarlar** >  **Endpoints'i** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

4. bir işletim sistemi (**Windows 10 ve 11 gibi)** seçin ve ardından bir ekleme yöntemi (**Yerel betik** gibi) seçin. Seçtiğiniz yöntem için sağlanan yönergeleri izleyin.

5. Eklemek istediğiniz her cihaz kümesi için bu işlemi yineleyin. 

> [!TIP]
> Cihazları her eklediğinizde aynı ekleme paketini kullanmanız gerekmez. Örneğin, bazı cihazları eklemek için yerel bir betik kullanabilir ve daha sonra daha fazla cihaz eklemek için başka bir yöntem seçebilirsiniz.

## <a name="offboard-a-device"></a>Cihazı çıkarma

Bir cihazı boşaltmak istiyorsanız aşağıdaki yordamlardan birini kullanın:

1. Gezinti bölmesinde **Ayarlar** ve ardından **Uç Noktalar'ı** seçin.

1. **Cihaz yönetimi'nin** altında **Çıkarma'yı** seçin.

1. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından **Cihazı kullanıma alma** altında Dağıtım **yöntemi** bölümünde **Yerel betik'i** seçin. 

1. Onay ekranında bilgileri gözden geçirin ve ardından devam etmek için **İndir'i** seçin.

1. **Çıkarma paketini indir'i** seçin. Çıkarma paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

1. Betiği, gemiden çıkarmak istediğiniz her cihazda çalıştırın. Bu görevle ilgili yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:   

   - Windows cihazlar: [Yerel betik kullanarak Windows cihazları](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) çıkarma
   
   - macOS cihazlar: [macOS'de kaldırma](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Cihazı kullanıma almak, cihazların İş için Defender'a veri göndermeyi durdurmasına neden olur. Ancak, çıkarmadan önce alınan veriler altı (6) aya kadar saklanır.

## <a name="next-objective"></a>Sonraki hedef

[Windows cihazlarınız için korumayı ayarlayın](m365bp-protection-settings-for-windows-10-devices.md).
