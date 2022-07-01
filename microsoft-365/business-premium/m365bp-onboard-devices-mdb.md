---
title: Kuruluşunuzun cihazlarını İş için Microsoft Defender ekleme
description: Kuruluşunuzun cihazlarını İş için Microsoft Defender ekleme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 70be4a5b7991d038dd1e34c00778de6bb3a67b84
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573979"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Kayıtlı cihazları İş için Microsoft Defender ekleme

Microsoft 365 İş Ekstra küçük ve orta ölçekli işletmeler için bir uç nokta güvenlik çözümü olan İş için Microsoft Defender içerir. İş için Defender, şirketinizin cihazları için yeni nesil koruma (virüsten koruma, kötü amaçlı yazılımdan koruma ve bulut tabanlı koruma), güvenlik duvarı koruması, web içeriği filtreleme ve daha fazlasını sağlar. Cihazları eklediğinizde koruma uygulanır. 

Cihazları eklemek için çeşitli seçenekler arasından seçim yapabilirsiniz:

- [Microsoft Intune kayıtlı Windows cihazları için otomatik ekleme](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune)
- [Windows ve macOS cihazlarını İş için Defender'a eklemek için yerel bir betik](#use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business)
- Mobil cihazlar (Windows, macOS, iOS ve Android) [dahil olmak üzere cihazları kaydetmek için Intune](#use-intune-to-enroll-devices) ve ardından bu cihazlara İş için Defender ilkelerini uygulama

Bu makale şunları da içerir:

- [Windows cihazında algılama testi çalıştırma](#run-a-detection-test-on-a-windows-device)
- [Cihazları aşamalı olarak ekleme](#onboard-devices-gradually)
- Bir [cihaz](#offboard-a-device) değiştirilirse veya biri kuruluştan ayrılırsa cihazı çıkarma

> [!IMPORTANT]
> Bir sorun oluşursa ve ekleme işleminiz başarısız olursa sorun [giderme İş için Microsoft Defender](../security/defender-business/mdb-troubleshooting.yml) bakın.

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune"></a>Zaten Intune kayıtlı Windows cihazları için otomatik ekleme kullanma

Bu cihazlar zaten Intune kayıtlıysa Windows cihazlarını İş için Defender'a otomatik olarak ekleyebilirsiniz. İş için Defender, Intune kayıtlı Windows istemci cihazlarını algılar ve bu cihazların otomatik olarak eklenip eklenmeyeceğini seçmenizi ister. Daha sonra İş için Defender'daki güvenlik ilkeleri ve ayarları bu cihazlara uygulanır. Bu işlemi *otomatik ekleme* olarak adlandırıyoruz. Otomatik ekleme seçeneğinin yalnızca Windows cihazları için geçerli olduğunu unutmayın. Aşağıdaki koşullar karşılanırsa otomatik ekleme kullanılabilir:

- Kuruluşunuz, İş için Defender'ı (Microsoft 365 İş Ekstra müşterileri zaten Microsoft 365 İş Ekstra) almadan önce Intune'da Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi (MDM) kullanıyormuş Microsoft Intune).
- Intune kayıtlı Windows cihazlarınız zaten var.

> [!TIP]
> Otomatik ekleme kullanmanız istendiğinde "tüm cihazlar kaydedildi" seçeneğini belirlemenizi öneririz. Bu şekilde, Windows cihazları daha sonra Intune kaydedildiğinde otomatik olarak İş için Defender'a eklenir.

Otomatik ekleme hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender ayarlamak için sihirbazı kullanma](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business"></a>Windows ve macOS cihazlarını İş için Defender'a eklemek için yerel betik kullanma

Windows ve Mac cihazlarını eklemek için yerel bir betik kullanabilirsiniz. Ekleme betiğini bir cihazda çalıştırdığınızda, Azure Active Directory ile bir güven oluşturur (bu güven yoksa), cihazı Intune kaydeder (henüz kaydedilmediyse) ve ardından cihazı İş için Defender'a ekler. Yerel betiği kullanarak aynı anda en fazla 10 cihaz ekleyebilirsiniz.

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** > **Uç Noktaları'nı** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

3. **Windows 10 ve 11** veya **macOS** gibi bir işletim sistemi seçin ve ardından **Dağıtım yöntemi** bölümünde **Yerel betik'i** seçin. 

4. **Ekleme paketini indir'i** seçin. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz. ( **macOS'yi** seçtiyseniz **yükleme paketini indir'i** de seçin ve çıkarılabilir cihazınıza kaydedin.)

5. Aşağıdaki kılavuzu kullanın:

   - Windows cihazları: [Yerel betik kullanarak Windows cihazları ekleme](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)
   - macOS cihazları: [macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-intune-to-enroll-devices"></a>Cihazları kaydetmek için Intune kullanma

Bir cihazı kaydetmek için, cihazı kendiniz kaydedin veya kullanıcılarınızın şirket portalında oturum açmasını ve gerekli uygulamaları kaydedip yüklemesini sağlayın. 

İş için Defender'ı almadan önce zaten Intune veya Mobil Cihaz Yönetimi kullanıyorsanız kuruluşunuzun cihazlarını eklemek için Intune kullanmaya devam edebilirsiniz. Intune kullanarak, iOS ve Android cihazlar dahil olmak üzere bilgisayarları, tabletleri ve telefonları ekleyebilirsiniz.

Bkz[. Microsoft Intune'da cihaz kaydı](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Windows cihazında algılama testi çalıştırma

Windows cihazlarını İş için Defender'a ekledikten sonra, her şeyin düzgün çalıştığından emin olmak için bir Windows cihazında algılama testi çalıştırabilirsiniz.

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

3. Gezinti bölmesinde **Ayarlar** > **Uç Noktaları'nı** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

4. bir işletim sistemi (**Windows 10 ve 11 gibi)** seçin ve ardından bir ekleme yöntemi (**Yerel betik** gibi) seçin. Seçtiğiniz yöntem için sağlanan yönergeleri izleyin.

5. Eklemek istediğiniz her cihaz kümesi için bu işlemi yineleyin. 

> [!TIP]
> Cihazları her eklediğinizde aynı ekleme paketini kullanmanız gerekmez. Örneğin, bazı cihazları eklemek için yerel bir betik kullanabilir ve daha sonra daha fazla cihaz eklemek için başka bir yöntem seçebilirsiniz.

## <a name="offboard-a-device"></a>Cihazı çıkarma

Bir cihazı boşaltmak istiyorsanız aşağıdaki yordamlardan birini kullanın:

1. Gezinti bölmesinde **Ayarlar'ı** ve ardından **Uç Noktalar'ı** seçin.

2. **Cihaz yönetimi'nin** altında **Çıkarma'yı** seçin.

3. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından **Cihazı kullanıma alma** altında Dağıtım **yöntemi** bölümünde **Yerel betik'i** seçin. 

4. Onay ekranında bilgileri gözden geçirin ve ardından devam etmek için **İndir'i** seçin.

5. **Çıkarma paketini indir'i** seçin. Çıkarma paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

6. Betiği, gemiden çıkarmak istediğiniz her cihazda çalıştırın. Bu görevle ilgili yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:   

   - Windows cihazları: [Yerel betik kullanarak Windows cihazlarını](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) çıkarma 
   - macOS cihazları: [macOS'ta kaldırma](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Cihazı kullanıma almak, cihazların İş için Defender'a veri göndermeyi durdurmasına neden olur. Ancak, çıkarmadan önce alınan veriler altı (6) aya kadar saklanır.

## <a name="next-objective"></a>Sonraki hedef

[Windows cihazlarınız için korumayı ayarlayın](m365bp-protection-settings-for-windows-10-devices.md).
