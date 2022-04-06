---
title: Kuruluş cihazlarınızı İş için Microsoft Defender'a ekleme
description: Kuruluş cihazlarınızı İş için Microsoft Defender'a ekleme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 44015c7cf568b968a4910433faa7700d550586fb
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705622"
---
# <a name="onboard-managed-devices-to-microsoft-defender-for-business"></a>Yönetilen cihazları İş için Microsoft Defender'a ekleme

Yeni nesil koruma (virüsten koruma, kötü amaçlı yazılımdan koruma ve bulut teslimi koruma), güvenlik duvarı koruması, web içeriği filtreleme ve daha fazlası ile korumak için cihazları İş için Microsoft Defender'a yükleyin. 

Cihazları onboard yapmak için çeşitli seçeneklerden birini seçebilirsiniz:

- [Microsoft Endpoint Manager'a önceden kaydolan Windows cihazlar için otomatik Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)
- [Kullanıcıları ve macOS cihazlarına Windows betik kullanarak ekleme](#use-a-local-script-to-onboard-windows-and-macos-devices)
- [Cihazları Endpoint Manager (Windows](#use-microsoft-endpoint-manager-to-enroll-devices), macOS, iOS ve Android) kaydetmek için Endpoint Manager'i kullanın ve ardından bu cihazlara İş için Defender ilkeleri uygulama

Bu makale şunları da içerir:

- [Windows cihazında algılama Windows çalıştırma](#run-a-detection-test-on-a-windows-device)
- [Cihazları aşamalı olarak ekleme](#onboard-devices-gradually)
- [Bir cihaz değiştirilirse veya bir](#offboard-a-device) kişi kuruluştan ayrılırsa cihaz çıkardan çıkar

> [!IMPORTANT]
> Bir sorun olursa ve ekleme işleminiz başarısız olursa bkz. [İş için Microsoft Defender sorun giderme](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'a önceden kaydolan Windows cihazlar için otomatik Microsoft Endpoint Manager

Otomatik ekleme seçeneği yalnızca Windows için geçerlidir. Otomatik ekleme, siz İş için Defender'ı edinmeden önce Microsoft Intune'te Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi'Windows kullanıyorsa ve zaten Windows cihazlarınız varsa kullanılabilir Endpoint Manager. 

cihaz Windows zaten Endpoint Manager, siz İş için Defender'ı ayarlama ve yapılandırma sürecindeyken, İş için Defender bu cihazları algılar. Windows cihazlarının hepsi veya bazısı için otomatik ekleme özelliğini kullanmak Windows soruldu. Tüm cihaz ve Windows bir kerede ekleyebilir veya başlangıç yapmak üzere belirli cihazlar seçin ve daha sonra daha fazla cihaz ekleyin.

Otomatik ekleme hakkında daha fazla bilgi edinmek için, İşletmeler için Microsoft Defender'ı ayarlamak için sihirbazı kullanma makalesinde 2 [. Adım'a bakın](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Kullanıcıları ve macOS cihazlarına Windows betik kullanarak ekleme

Kullanıcıları ve macOS cihazlarına yerel Windows betik kullanabilirsiniz. Ekleme betiğini bir cihazda çalıştırsanız, Azure Active Directory ile bir güven oluşturur (bu güven henüz yoksa), cihazı Microsoft Endpoint Manager'e (henüz kayıtlı değilse) kaydederek cihazı İş için Defender'a verir. 

Bu yöntemle bir defada en fazla 10 cihaz abilirsiniz.

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

3. **Windows 10 11** gibi bir işletim sistemi seçin ve ardından Cihaz ekleme'nin altındaki **Dağıtım** yöntemi bölümünde Yerel **betik'i seçin**. 

4. Ekleme **paketini indir'i seçin**. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

5. Aşağıdaki makalelerde yer alan yönergeleri izleyin:

   - Windows cihazlar: [Yerel Windows kullanarak cihazları ekleme](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)
   - macOS cihazları: [macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Cihazları Microsoft Endpoint Manager için mobil cihaz kullanma

zaten Endpoint Manager kullanıyorsanız (Microsoft Intune ve Mobil Cihaz Yönetimi dahil), Endpoint Manager'ı kullanarak kuruluş cihazlarını eklemeye devam edebilirsiniz. Uygulama Endpoint Manager iOS ve Android cihazları dahil olmak üzere bilgisayarları, tabletleri ve telefonları dahil edin.

Kuruluşta Android cihazları kullanıyorsa, bu yöntemi kullanın.

Bkz[. Microsoft Intune'de cihaz kaydı](/mem/intune/enrollment/device-enrollment).


## <a name="run-a-detection-test-on-a-windows-device"></a>Windows cihazında Windows çalıştırma

Windows Için Defender'Windows cihazları işe başladıktan sonra, her şeyin düzgün olduğundan emin olmak için Windows bir algılama testi çalıştırabilirsiniz.

1. Windows bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ne açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştır edildikten sonra, Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa, algılama testi tamamlandı olarak işaretlenir ve yaklaşık 10 dakika içinde yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yeni bir uyarı görüntülenir.

## <a name="onboard-devices-gradually"></a>Cihazları aşamalı olarak ekleme

Cihazları aşamalı cihaz ekleme olarak çağırdiğimiz aşamalı cihaz ekleme *aşamalarını tercih ediyorsanız* şu adımları izleyin: 

1. Ekleme için bir cihaz kümesi belirleme.

2. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

3. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

4. Bir işletim sistemi (örneğin, **Windows 10 11)** seçin ve sonra bir ekleme yöntemi (Yerel betik gibi **) seçin**. Seçtiğiniz yöntem için sağlanan yönergeleri izleyin.

5. Eklemek istediğiniz her cihaz kümesi için bu işlemi yinelayın. 

> [!TIP]
> Cihazları her eklemeye aynı ekleme paketini kullanmak zorunda değildir. Örneğin, bazı cihazları yerel betik kullanarak kullanabilir ve daha sonra daha fazla cihaza sahip olmak için başka bir yöntem seçebilirsiniz.

## <a name="offboard-a-device"></a>Cihaz çıkartan

Bir cihazla çıkarılacak şekilde yer almak için şu adımları izleyin:

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde, Gezinti **Bölmesi'Ayarlar** uç **noktalar'ı seçin**.

3. Cihaz **yönetimi'nin** altında **Çıkar'ı seçin**.

4. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından Cihaz çıkar'ın altındaki Dağıtım yöntemi bölümünde Yerel **betik'i seçin**. 

5. Onay ekranında bilgileri gözden geçirin ve devam etmek için **İndir'i** seçin.

6. İndirme **paketi'ne tıklayın**. Çıkarılabilir paketi çıkarılabilir bir sürücüye kaydetmenizi öneririz.

7. Betiği, çıkaracakları her cihaza çalıştırın. Bu görevle ilgili yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:   

   - Windows için: [Yerel Windows kullanarak çıkar çıkar](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - macOS cihazları: [macOS'ta kaldırma](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Bir cihaz çıkar bırak bırak bırak, cihazların Verileri İş için Defender'a göndermesini durdurur. Bununla birlikte, karalama öncesinde alınan veriler altı (6) aya kadar korunur.

## <a name="next-steps"></a>Sonraki adımlar

[Düzeltme eylemlerini gözden Microsoft 365 İş Ekstra](m365bp-review-remediation-actions-devices.md)