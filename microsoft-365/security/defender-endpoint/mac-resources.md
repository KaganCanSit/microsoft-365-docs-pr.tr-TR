---
title: Mac'te Uç Nokta için Microsoft Defender Kaynakları
description: Mac'te Uç Nokta için Microsoft Defender kaynakları; kaldırma, tanılama günlüklerini, CLI komutlarını ve ürünle ilgili bilinen sorunları toplama gibi kaynaklar.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5c8580e1bc0869f28da1b23a813bba9d2f3c612e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012010"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender kaynakları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>Tanılama bilgilerini toplama

Bir sorunu yeniden üretecek, günlüğe kaydetme düzeyini artırabilir, sistemi bir süre için çalıştırabilir ve günlük düzeyini varsayılan değere geri yükleyebilirsiniz.

1. Günlüğe kaydetme düzeyini artırma:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Sorunu yeniden üretin

3. Uç `sudo mdatp diagnostic create` nokta günlükleri için Microsoft Defender'ı çalıştırmak. Dosyalar bir arşivde .zip. Bu komut, işlem başarılı olduktan sonra yedek dosya yolunu da yazdırır.

   > [!TIP]
   > Varsayılan olarak, tanılama günlükleri için kaydedilir `/Library/Application Support/Microsoft/Defender/wdavdiag/`. Tanı günlüklerinin kayded olduğu dizini değiştirmek için, istediğiniz `--path [directory]` dizinle değiştirerek aşağıdaki `[directory]` komuta geçin.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. Günlüğe kaydetme düzeyini geri yükleme:

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>Günlüğe kaydetme yükleme sorunları

Yükleme sırasında bir hata oluşursa, yükleyici yalnızca genel bir hata verir.

Ayrıntılı günlük 'a kaydedilir `/Library/Logs/Microsoft/mdatp/install.log`. Yükleme sırasında sorun edersiniz, nedenini tanılamaya yardımcı olmak için bu dosyayı bize gönderin.

## <a name="uninstalling"></a>Kaldırma

macOS'ta Uç Nokta için Microsoft Defender'ı kaldırmanın çeşitli yolları vardır. Merkezi olarak yönetilen kaldırma işlemi JAMF'de mevcutken, bu uygulamanın henüz merkezi olarak Microsoft Intune.

### <a name="interactive-uninstallation"></a>Etkileşimli kaldırma

- **Finder >'ı açın**. Uç Nokta ve **Çöp Kutusuna Taşı > Microsoft Defender'a sağ tıklayın**.

### <a name="supported-output-types"></a>Desteklenen çıktı türleri

Tablo ve JSON biçimi çıkış türlerini destekler. Her komut için varsayılan bir çıkış davranışı vardır. Şu komutları kullanarak, çıkışı tercih ettiğiniz çıkış biçiminde değiştirebilirsiniz:

`-output json`

`-output table`

### <a name="from-the-command-line"></a>Komut satırından

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>Komut satırına göre yapılandırma

Ürün ayarlarını denetleme ve isteğe bağlı taramaları tetikleme gibi önemli görevler komut satırına yapılabilir:

|Grup|Senaryo|Komut|
|---|---|---|
|Yapılandırma|Gerçek zamanlı korumayı açma/kapatma|`mdatp config real-time-protection --value [enabled/disabled]`|
|Yapılandırma|Bulut korumasını açma/kapatma|`mdatp config cloud --value [enabled/disabled]`|
|Yapılandırma|Ürün tanılamayı açma/kapatma|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|Yapılandırma|Otomatik örnek gönderimi açma/kapatma|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|Yapılandırma|İzin verilenler listesine tehdit adı ekleme|`mdatp threat allowed add --name [threat-name]`|
|Yapılandırma|Tehdit adını izin verilenler listesinden kaldırma|`mdatp threat allowed remove --name [threat-name]`|
|Yapılandırma|İzin verilen tüm tehdit adlarını listele|`mdatp threat allowed list`|
|Yapılandırma|PUA korumasını açma|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|Yapılandırma|PUA korumasını kapatma|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|Yapılandırma|PUA koruması için denetim modunu açma|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|Yapılandırma|Virüsten koruma pasif modunu açma/kapatma|`mdatp config passive-mode --value [enabled/disabled]`|
|Yapılandırma|Isteğe bağlı taramalar için paralellik derecesini yapılandırma|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Yapılandırma|Güvenlik zekası güncelleştirmeleri sonrasında taramaları açma/kapatma|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Yapılandırma|Arşiv taramayı açma/kapatma (yalnızca isteğe bağlı taramalar)|`mdatp config scan-archives --value [enabled/disabled]`|
|Tanılama|Günlük düzeyini değiştirme|`mdatp log level set --level [error/warning/info/verbose]`|
|Tanılama|Tanılama günlükleri oluşturma|`mdatp diagnostic create --path [directory]`|
|Hizmet Durumu|Ürünün durumunu denetleme|`mdatp health`|
|Hizmet Durumu|Spefic ürün özniteliğini denetleme|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|Koruma|Yolu tarama|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Koruma|Hızlı tarama yapma|`mdatp scan quick`|
|Koruma|Tam tarama yapma|`mdatp scan full`|
|Koruma|Sürekli isteğe bağlı taramayı iptal etme|`mdatp scan cancel`|
|Koruma|Güvenlik zekası güncelleştirmesi talep edin|`mdatp definitions update`|
|EDR|Set/Remove etiketi, yalnızca GROUP desteği|`mdatp edr tag set --name GROUP --value [name]`|
|EDR|Grup etiketini cihazdan kaldırma|`mdatp edr tag remove --tag-name [name]`|
|EDR|Grup Kimliği Ekleme|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>Otomatik tamamlama nasıl etkinleştirilen?

Bash'ta otomatik tamamlama özelliğini etkinleştirmek için aşağıdaki komutu çalıştırın ve Terminal oturumunu yeniden başlatın:

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

Zsh ile otomatik tamamlamayı etkinleştirmek için:

- Aygıtınızda otomatik tamamlama özelliğinin etkinleştirildiğinden emin olun:

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- Önceki komut herhangi bir çıkış üretemese, aşağıdaki komutu kullanarak otomatik tamamlama özelliğini etkinleştirebilirsiniz:

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- macOS'ta Uç Nokta için Microsoft Defender otomatik tamamlama özelliğini etkinleştirmek ve Terminal oturumunu yeniden başlatmak için aşağıdaki komutları çalıştırın:

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>Uç nokta karantina dizini için Client Microsoft Defender

`/Library/Application Support/Microsoft/Defender/quarantine/` tarafından karantinaya alınmış dosyaları içerir `mdatp`. Dosyalar, tehdit izlemeKimli'den sonra adlandırılmıştır. Geçerli izlemekimleri ile birlikte gösterilir `mdatp threat list`.

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Uç nokta portalı bilgileri için Microsoft Defender

[EDR için microsoft](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801) defender özellikleri artık MacOS için Microsoft Defender blog'a geldi; Uç Nokta Güvenlik Merkezi için Microsoft Defender'da neler beklediğiniz hakkında ayrıntılı bilgiler bulabilirsiniz.
