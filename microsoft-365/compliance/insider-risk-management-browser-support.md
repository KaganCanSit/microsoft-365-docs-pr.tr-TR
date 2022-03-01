---
title: Insider risk yönetimi tarayıcı sinyali algılama hakkında bilgi ve yapılandırma
description: Tarayıcıda Insider risk yönetimi tarayıcı sinyali algılaması hakkında Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: c3cb9e432f3ea94f88c63cfad928ba577471b420
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015330"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Insider risk yönetimi tarayıcı sinyali algılama hakkında bilgi ve yapılandırma

Web tarayıcıları çoğunlukla kullanıcılar tarafından kuruluş içindeki hassas ve hassas olmayan dosyalara erişmek için kullanılır. Insider risk yönetimi, Microsoft Edge [Ve Google Chrome](https://www.google.com/chrome) tarayıcılarında görüntülen tüm yürütülebilir olmayan dosyalar için tarayıcı sızıntısını algılama ve bu [](https://www.microsoft.com/edge) işaret üzerinde işlem görüntülemenize olanak sağlar. Bu sinyallerle, analistler ve tahminler bu tarayıcıları kullanırken kapsam dışı ilke kullanıcıları tarafından aşağıdaki etkinliklerden herhangi biri gerçekleştir geldiğinde hızlı bir şekilde harekete geçebilirsiniz:

- Kişisel bulut depolama alanına kopyalanan dosyalar
- Yerel cihazlara veya ağ cihazlarına yazdırılan dosyalar
- Ağ paylaşımına aktarılan veya kopyalanan dosyalar
- USB cihazlarına kopyalanan dosyalar

Bu olaylar için sinyaller, Microsoft Edge özellikleri kullanılarak ve *Microsoft* Uyumluluk Uzantısı eklentisi kullanılarak algılanır. Google Chrome'da müşteriler sinyal algılama *için Microsoft Uyumluluk Uzantısını* kullanır.

Aşağıdaki tabloda, her tarayıcı için algılanan etkinlikler ve uzantı desteği özetlenmiştir:

| **Algılanan etkinlikler**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Kişisel bulut depolama alanına kopyalanan dosyalar         | Yerel             | Uzantı         |
| Yerel cihazlara veya ağ cihazlarına yazdırılan dosyalar      | Yerel             | Uzantı         |
| Ağ paylaşımına aktarılan veya kopyalanan dosyalar | Uzantı          | Uzantı         |
| USB cihazlarına kopyalanan dosyalar                    | Uzantı          | Uzantı         |

## <a name="common-requirements"></a>Yaygın gereksinimler

Microsoft Edge eklentisini veya Google Chrome uzantısını yüklemeden önce müşterilerin, kapsam ilkesi kullanıcılarının cihazları aşağıdaki gereksinimleri karşılaya olduğundan emin olmak gerekir:

- Sinyal Windows 10 desteği için en son x64 derlemesi Windows 10 x64 derleme 1809'un kullanılması önerilir. Tarayıcı sinyali algılama şu anda bu konu dışı cihazlarda Windows desteklenmiyor.
- [Insider risk Microsoft 365](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) ile geçerli abonelik.
- Cihazlar Uyumluluk [portalına](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) Microsoft 365 gerekir.

Belirli tarayıcı yapılandırma gereksinimleri için, bu makalenin Microsoft Edge ve Google Chrome'un en son bölümlerine bakın.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Daha fazla bilgi için tarayıcı sinyali algılamayı Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge tarayıcı gereksinimleri

- Yaygın gereksinimleri karşılama
- Microsoft Edge x64, 91.0.864.41 veya daha yüksek sürümü
- *Microsoft Uyumluluk Uzantısı* eklentisi sürüm 1.0.0.44 veya üzerinde
- Edge.exe izin verilmeyen bir tarayıcı olarak yapılandırılmadı

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>1. Seçenek: Temel kurulum (Edge ile test etmek için önerilir)

Tarayıcı sinyali algılamayı test etmek için, bu seçeneği kullanarak tarayıcınızdaki her cihaz için tek bir makine selfhost yapılandırabilirsiniz.

Temel kurulum seçeneği için aşağıdaki adımları tamamlayın:

1. Microsoft Uyumluluk [Uzantısına gidin](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Uzantıyı yükleyin.

### <a name="option-2-intune-setup-for-edge"></a>2. Seçenek: Edge için Intune kurulumu

Intune kullanarak kuruluş uzantısını ve gereksinimlerini yapılandırmak için bu seçeneği kullanın.

Intune kurulum seçeneği için aşağıdaki adımları tamamlayın:

1. Yönetici izinlerini kullanarak [Microsoft Endpoint Manager Yönetim Merkezi'nde](https://endpoint.microsoft.com) oturum açın.
2. Yapılandırma **Profilleri'ne gidin**.
3. Profil **Oluştur'a tıklayın**.
4. Platform **olarak Windows 10'ı** seçin.
5. Profil **türü olarak Yönetim** *Şablonları'nın ardından Oluştur'a* **tıklayın.**
6. Sekme **Ayarlar** seçin.
7. Edge **Sürüm 77 ve sonraki bir sürümünü seçin.**
8. Uzantılarla **ilgili tüm** ayarlara genel bir bakış için Uzantılar'da arama yapın.
9. Hangi **uzantıların sessiz yük yükl dahili olduğunu kontrol etmek ayarını seçin.**
10. **Etkin'i seçin.**
11. İstendiğinde uzantı kimliğini ekleyin: *lcmcgbabdcbngcbcfabdncmoppkaj parola***.**
12. **Tamam'ı seçin.**

### <a name="option-3-group-policy-setup-for-edge"></a>3. Seçenek: Edge için Grup İlkesi kurulumu

Grup İlkesi'yi kullanarak kuruluş genelinde uzantıları ve gereksinimleri yapılandırmak için bu seçeneği kullanın.

Grup İlkesi kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: En son Microsoft Edge Yönetim Şablonu (.admx) dosyasını içeri aktarın.**

Cihazlar Grup İlkeleri kullanılarak yönetilebilir olmalıdır ve [Microsoft Edge](https://www.microsoft.com/edge/business/download) Yönetim Şablonlarının Grup İlkesi Merkezi Deposu'na aktarılmış olması gerekir. Daha fazla bilgi için bkz[.](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Merkezi Grup İlkesi Yönetim Şablonları için Merkezi Mağaza oluşturma ve Windows.

**2. Adım: *Microsoft Uyumluluk Uzantısı* eklentiyi Zorla Yükleme *listesine* ekleyin.**

Uzantıyı eklemek için aşağıdaki adımları tamamlayın:

1. Grup İlkesi **Yönetim Düzenleyicisi'nde**, Kuruluş Biriminize (OU) gidin.
2. Aşağıdaki yolu genişletin **Bilgisayar/Kullanıcı yapılandırması** **İlkeleri** \> \> **Yönetim şablonları** \> **Klasik yönetim şablonları** \> **Microsoft Edge** \> **genişletin**. Bu yol, kuruluşun yapılandırmasına bağlı olarak değişebilir.
3. Hangi **uzantıların sessizce yük yükl dahili olduğunu yapılandır'ı seçin.**
4. Sağ tıklayın ve Düzenle'yi **seçin**.
5. Etkin radyo **düğmesini** kontrol edin.
6. **Göster'i seçin**.
7. Değer **için** şu girdiyi ekleyin: *lcmcgbabdcbngcbcfabdncmoppkajajaj;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. **Tamam'ı ve** ardından Uygula'ya **tıklayın**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Google Chrome için tarayıcı sinyali algılamayı yapılandırma

Google Chrome için Insider risk yönetimi tarayıcı sinyali algılama desteği, Microsoft Uyumluluk Uzantısı *aracılığıyla etkinleştirilir*. Bu uzantı Chrome'da Uç Nokta DLP'lerini de destekler. Uç Nokta DLP desteği hakkında daha fazla bilgi için bkz [. Microsoft Uyumluluk Uzantısıyla (önizleme) çalışmaya başlama](/microsoft-365/compliance/dlp-chrome-get-started).

### <a name="google-chrome-browser-requirements"></a>Google Chrome tarayıcı gereksinimleri

- Yaygın gereksinimleri karşılama
- Google Chrome x64'ün en son sürümü
- *Microsoft Uyumluluk Uzantısı* sürüm 2.0.0.183 veya üzerinde
- Chrome.exe izin verilmeyen bir tarayıcı olarak yapılandırılmadı

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>1. Seçenek: Temel kurulum (Chrome ile test etmek için önerilir)

Tarayıcı sinyali algılamayı test etmek için, bu seçeneği kullanarak tarayıcınızdaki her cihaz için tek bir makine selfhost yapılandırabilirsiniz.

Temel kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: PowerShell ile gerekli Kayıt Defteri anahtarlarını etkinleştirme**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Bu kayıt defteri anahtarları, uzantının düzgün işlevselliğini sağlamak için gereklidir. Herhangi bir sinyali test etmek için önce bu kayıt defteri anahtarlarını etkinleştirmeniz gerekir.*

**2. Adım: *Microsoft Uyumluluk Uzantısını yükleme***

1. Microsoft Uyumluluk [Uzantısına gidin](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Uzantıyı yükleyin.

### <a name="option-2-intune-setup-for-chrome"></a>2. Seçenek: Chrome için Intune kurulumu

Intune kullanarak kuruluş uzantısını ve gereksinimlerini yapılandırmak için bu seçeneği kullanın.

Intune kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: Intune ile gerekli Kayıt Defteri anahtarını etkinleştirme**

1. Aşağıdaki PowerShell betiğini çalıştırın:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Microsoft Endpoint Manager [Yönetim Merkezi'nde oturum açma](https://endpoint.microsoft.com).
3. Cihazlar **Betikleri'ne** \> **gidin** ve Ekle'yi **seçin.**
4. Sorularak oluşturulan betiğin bulunduğu konuma gidin.
5. Aşağıdaki ayarları seçin:

    - Oturum açma kimlik bilgilerini kullanarak bu betiği çalıştırın: *Evet*
    - Betik imzasını zorunlu kılın denetimi: *Hayır*
    - Betiği 64 bit PowerShell Ana Bilgisayarı'ta *çalıştırma: Evet*

6. Uygun cihaz gruplarını seçin ve ilkeyi uygulama.

**2. Adım: Intune Force Yüklemesi'yi yapılandırma**

Microsoft DLP Chrome uzantısını yüklü uzantılar listesine eklemeden önce, Intune yönetimine yönelik Chrome Yönetim Şablonu (.admx) dosyasını yüklemeniz gerekir. Adım adım kılavuz için bkz. Daha fazla [bilgi için Chrome Tarayıcısını Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Yönetim Şablonu dosyasını yükledikten sonra, aşağıdaki adımları tamamlayın:

1. Microsoft Endpoint Manager [Yönetim Merkezi'nde oturum açma](https://endpoint.microsoft.com).
2. Yapılandırma **Profilleri'ne gidin**.
3. Profil **Oluştur'a tıklayın**.
4. Platform **olarak Windows 10'ı** *seçin*.
5. Profil **türü** olarak *Özel'i* seçin.
6. Sekme **Ayarlar** seçin.
7. **Ekle'yi seçin.**
8. Aşağıdaki ilke bilgilerini girin:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Veri türü: *Dize*
    - Değer: *\<enabled/\>\<data id=”ExtensionInstallForcelistDesc” value=”1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx″/\>*

9. **Oluştur**’u seçin.

### <a name="option-3-group-policy-setup-for-chrome"></a>3. Seçenek: Chrome için Grup İlkesi kurulumu

Grup İlkesi'yi kullanarak kuruluş genelinde uzantıları ve gereksinimleri yapılandırmak için bu seçeneği kullanın.

Grup İlkesi kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: Chrome Yönetim Şablonu dosyasını içeri aktarma**

Cihazlarınız Grup İlkesi kullanılarak yönetilebilir olmalı ve tüm [Chrome](https://chromeenterprise.google/browser/download/) Yönetim Şablonları Merkezi Grup İlkesi'ne aktarılabilir. Daha fazla bilgi için bkz[.](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Merkezi Grup İlkesi Yönetim Şablonları için Merkezi Mağaza oluşturma ve Windows.

**2. Adım: PowerShell ile gerekli Kayıt Defteri anahtarını etkinleştirme**

1. Aşağıdaki içeriği kullanarak bir PowerShell betiği oluşturun:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Grup İlkesi **Yönetim Konsolu'nu açın** ve kuruluş biriminize (OU) gidin.
3. Sağ tıklayın ve Bu etki alanında **GPO oluştur'u seçin ve burada bağlantı oluşturun**. İstendiğinde, bu Grup İlkesi Nesnesine (GPO) açıklayıcı bir ad attayın. Örneğin, *DLP Chrome Immediate PowerShell Betiği*.
4. GPO'yı oluşturdukta sağ tıklayın ve Düzenle'yi **seçin**. Bu seçim sizi Grup İlkesi Nesnesine alır.
5. Bilgisayar yapılandırması **Tercihler Denetim** \> **masası ayarları** \> **Zamanlanmış** **görevler'e**\> gidin.
6. Zamanlanmış Görevler'in altındaki boş alana **sağ tıklayın ve** Yeni Anlık Görev (**en az** \> **7 Windows seçin).**
7. Görev Adı ve *Açıklaması* *girin*.
8. Acil görevi çalıştırmak için ilgili hesabı seçin. Örneğin, *NT Yetkili*.
9. En yüksek **ayrıcalıklarla çalıştır'ı seçin**.
10. Varsayılan ilkeyi Windows 10.
11. Eylemler sekmesinde **Program** **başlat'ı seçin**.
12. 1. Adımda oluşturulan programın/betiğin **yolunu girin**.
13. **Uygula'ya seçin**.

**3. Adım: Zorla Yükleme listesine Chrome uzantısını ekleme**

1. Grup İlkesi **Yönetim Düzenleyicisi'nde**, kuruluş biriminize (OU) gidin.
2. Aşağıdaki yolu genişletin **Bilgisayar/Kullanıcı yapılandırması** **İlkeleri** \> \> **Yönetim şablonları** \> **Klasik yönetim şablonları** \> **Google** \> **Google Chrome** \> Uzantıları. Bu yol, kuruluşun yapılandırmasına bağlı olarak değişebilir.
3. Yüklü **uzantılara zorla listesini yapılandır'ı seçin**.
4. Sağ tıklayın ve Düzenle'yi **seçin**.
5. Etkin radyo **düğmesini** seçin.
6. **Göster'i seçin**.
7. Değer **için** şu girdiyi ekleyin: *echcggldkblholpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. **Tamam'ı ve** ardından Uygula'ya **tıklayın**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Insider risk yönetimi tarayıcı sinyali algılamalarını test edin ve doğrulayın

1. Cihaz göstergelerinin etkin olduğu bir Insider risk yönetimi ilkesi oluşturun.
2. Kişisel bulut depolama alanına kopyalanan dosyaların sinyal algılamasını test etmek için desteklenen bir cihaz veya cihazda aşağıdaki Windows tamamlayın:

    - Sinyal algılama için yapılandırmış Microsoft OneDrive tarayıcı türüyle bir dosya paylaşım web sitesi (Microsoft OneDrive, Google Drive, vb.) açın.
    - Tarayıcıyla, yürütülebilir olmayan bir dosyayı web sitesine yükleyin.
3. Yerel veya ağ cihazlarına yazdırılan dosyalar, ağ paylaşımına aktarılan veya kopyalanan dosyalar ve USB cihazlarına kopyalanan dosyalar için sinyal algılamayı test etmek için desteklenen bir cihazla aşağıdaki Windows tamamlayın:

    - Yürütülebilir olmayan bir dosyayı doğrudan tarayıcıda açın. Dosyanın, web sayfası yerine görüntülemek için doğrudan Dosya Gezgini aracılığıyla açılması veya yeni bir tarayıcı sekmesinde açılması gerekir.
    - Dosyayı yazdırabilirsiniz.
    - Dosyayı bir USB cihazına kaydedin.
    - Dosyayı bir ağ sürücüsüne kaydedin.
  
4. İlk Insider risk yönetimi ilkeniz oluşturulduktan sonra, yaklaşık 24 saat sonra etkinlik göstergelerinden uyarılar almaya başlarsınız. Test edilen [etkinlikler için](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) Insider risk yönetimi uyarıları için Uyarılar panosuna göz atabilirsiniz.
