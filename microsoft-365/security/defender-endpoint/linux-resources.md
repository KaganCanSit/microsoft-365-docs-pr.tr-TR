---
title: Linux kaynakları üzerinde Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender kaynaklarını açıklar. Bunun nasıl kaldıracağız, tanılama günlüklerinin nasıl topla ilgili olduğu, CLI komutları ve ürünle ilgili bilinen sorunlar da buna dahil.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, yükleme, dağıtma, kaldırma, ssible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: a32c8c91350218da619de18e0b1b398a93bf7fda
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312684"
---
# <a name="resources"></a>Kaynaklar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Tanılama bilgilerini toplama

Bir sorunu yeniden üreteceksanız, önce günlüğe kaydetme düzeyini artırabilir, sistemi bir süre için çalıştırın ve sonra günlük düzeyini varsayılan değere geri yüklenin.

1. Günlüğe kaydetme düzeyini artırma:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Sorunu yeniden üretin.

3. Defender for Endpoint'ın günlüklerini back up için aşağıdaki komutu çalıştırın. Dosyalar bir arşivinde .zip.

   ```bash
   sudo mdatp diagnostic create
   ```

    Bu komut, işlem başarılı olduktan sonra yedek dosya yolunu da yazdırır:

   ```Output
   Diagnostic file created: <path to file>
   ```

4. Günlüğe kaydetme düzeyini geri yükleme:

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

Yükleme sırasında bir hata oluşursa, yükleyici yalnızca genel bir hata verir.

Ayrıntılı günlük 'a kaydedilir `/var/log/microsoft/mdatp/install.log`.
Yükleme sırasında sorun edersiniz, nedenini tanılamaya yardımcı olmak için bu dosyayı bize gönderin.

## <a name="uninstall"></a>Kaldır

Linux'ta Uç Nokta için Defender'ı kaldırmanın çeşitli yolları vardır. Yalı gibi bir yapılandırma aracı kullanıyorsanız, yapılandırma aracı için paket kaldırma yönergelerini izleyin.

### <a name="manual-uninstallation"></a>El ile kaldırma

- `sudo yum remove mdatp` RHEL ve çeşitlemeler için (CentOS ve Oracle Linux).
- `sudo zypper remove mdatp` SLES ve çeşitlemeler için.
- `sudo apt-get purge mdatp` Ubuntu ve Debian sistemleri için.

## <a name="configure-from-the-command-line"></a>Komut satırına göre yapılandırma

Ürün ayarlarını denetleme ve isteğe bağlı taramaları tetikleme gibi önemli görevler komut satırına göre yapılabilir.

### <a name="global-options"></a>Genel seçenekler

Varsayılan olarak, komut satırı aracı sonucun çıkışını insanlar tarafından okunabilir biçimde verir. Buna ek olarak, araç sonuçların JSON olarak çıkışını da destekler ve bu, otomasyon senaryolarında kullanışlı olur. Çıkışı JSON olarak değiştirmek için aşağıdaki komutlardan `--output json` herhangi birini seçin.

### <a name="supported-commands"></a>Desteklenen komutlar

Aşağıdaki tabloda, en yaygın senaryolardan bazılarının komutları listeledir. Desteklenen `mdatp help` komutların tam listesini görüntülemek için Terminal'den çalıştırın.

<br>

****

|Grup|Senaryo|Komut|
|---|---|---|
|Yapılandırma|Gerçek zamanlı korumayı açma/kapatma|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Yapılandırma|Davranış izlemeyi açma/kapatma|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Yapılandırma|Bulut korumasını açma/kapatma|`mdatp config cloud --value [enabled\|disabled]`|
|Yapılandırma|Ürün tanılamayı açma/kapatma|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Yapılandırma|Otomatik örnek gönderimi açma/kapatma|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Yapılandırma|AV pasif modunu açma/kapatma|`mdatp config passive-mode --value [enabled\|disabled]`|
|Yapılandırma|Dosya uzantısı için virüsten koruma dışlama ekleme/kaldırma|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Yapılandırma|Dosya için virüsten koruma dışlama ekleme/kaldırma|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Yapılandırma|Dizin için virüsten koruma dışlama ekleme/kaldırma|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Yapılandırma|İşlem için virüsten koruma dışlama ekleme/kaldırma|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Yapılandırma|Tüm virüsten koruma dışlamalarını listele|`mdatp exclusion list`|
|Yapılandırma|İzin verilenler listesine tehdit adı ekleme|`mdatp threat allowed add --name [threat-name]`|
|Yapılandırma|Tehdit adını izin verilenler listesinden kaldırma|`mdatp threat allowed remove --name [threat-name]`|
|Yapılandırma|İzin verilen tüm tehdit adlarını listele|`mdatp threat allowed list`|
|Yapılandırma|PUA korumasını açma|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Yapılandırma|PUA korumasını kapatma|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Yapılandırma|PUA koruması için denetim modunu açma|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Yapılandırma|Isteğe bağlı taramalar için paralellik derecesini yapılandırma|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Yapılandırma|Güvenlik zekası güncelleştirmeleri sonrasında taramaları açma/kapatma|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Yapılandırma|Arşiv taramayı açma/kapatma (yalnızca isteğe bağlı taramalar)|`mdatp config scan-archives --value [enabled/disabled]`|
|Tanılama|Günlük düzeyini değiştirme|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Tanılama|Tanılama günlükleri oluşturma|`mdatp diagnostic create --path [directory]`|
|Hizmet Durumu|Ürünün durumunu denetleme|`mdatp health`|
|Koruma|Yolu tarama|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Koruma|Hızlı tarama yapma|`mdatp scan quick`|
|Koruma|Tam tarama yapma|`mdatp scan full`|
|Koruma|Sürekli isteğe bağlı taramayı iptal etme|`mdatp scan cancel`|
|Koruma|Güvenlik zekası güncelleştirmesi talep edin|`mdatp definitions update`|
|Koruma geçmişi|Tam koruma geçmişini yazdırma|`mdatp threat list`|
|Koruma geçmişi|Tehdit ayrıntılarını al|`mdatp threat get --id [threat-id]`|
|Karantina yönetimi|Tüm karantinaya alınmış dosyaları listele|`mdatp threat quarantine list`|
|Karantina yönetimi|Tüm dosyaları karantinadan kaldırma|`mdatp threat quarantine remove-all`|
|Karantina yönetimi|Karantina için tehdit olarak algılanan bir dosyayı ekleme|`mdatp threat quarantine add --id [threat-id]`|
|Karantina yönetimi|Tehdit olarak algılanan dosyayı karantinadan kaldırma|`mdatp threat quarantine remove --id [threat-id]`|
|Karantina yönetimi|Dosyayı karantinadan geri yükleme|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|Uç Nokta Algılama ve Yanıt|Erken önizlemeyi ayarlama (kullanılmayan)|`mdatp edr early-preview [enable|disable]`|
|Uç Nokta Algılama ve Yanıt|Grup kimliğini ayarlama|`mdatp edr group-ids --group-id [group-id]`|
|Uç Nokta Algılama ve Yanıt|Yalnızca desteklenen etiket ayarlama `GROUP` / kaldırma|`mdatp edr tag set --name GROUP --value [tag]`|
|Uç Nokta Algılama ve Yanıt|Liste dışlamaları (kök)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
