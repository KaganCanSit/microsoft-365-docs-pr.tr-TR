---
title: Insider risk yönetimi tarayıcısı sinyal algılama hakkında bilgi edinin ve yapılandırın
description: Microsoft 365'de insider risk yönetimi tarayıcısı sinyal algılama hakkında bilgi edinin
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
ms.openlocfilehash: e904c4576081cd459ca905a56e3dd6cec5b1af31
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758739"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Insider risk yönetimi tarayıcısı sinyal algılama hakkında bilgi edinin ve yapılandırın

Web tarayıcıları genellikle kullanıcılar tarafından bir kuruluştaki hem hassas hem de hassas olmayan dosyalara erişmek için kullanılır. Insider risk yönetimi, kuruluşunuzun [Microsoft Edge](https://www.microsoft.com/edge) ve [Google Chrome](https://www.google.com/chrome) tarayıcılarında görüntülenen tüm yürütülebilir olmayan dosyalar için tarayıcı sızdırma sinyallerini algılamasına ve bu sinyaller üzerinde işlem yapmasına olanak tanır. Bu sinyallerle, analistler ve araştırmacılar bu tarayıcıları kullanırken kapsam içi ilke kullanıcıları tarafından aşağıdaki etkinliklerden herhangi biri gerçekleştirildiğinde hızla harekete geçebilir:

- Kişisel bulut depolama alanına kopyalanan dosyalar
- Yerel veya ağ cihazlarına yazdırılan dosyalar
- Ağ paylaşımına aktarılan veya kopyalanan dosyalar
- USB cihazlarına kopyalanan dosyalar

Bu olaylara yönelik sinyaller, yerleşik tarayıcı özellikleri ve *Microsoft Uyumluluk Uzantısı* eklentisi kullanılarak Microsoft Edge algılanmıştır. Google Chrome'da müşteriler sinyal algılama için *Microsoft Uyumluluk Uzantısı'nı* kullanır.

Aşağıdaki tabloda, her tarayıcı için algılanan etkinlikler ve uzantı desteği özetlenmiştir:

| **Algılanan etkinlikler**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Kişisel bulut depolama alanına kopyalanan dosyalar         | Yerel             | Uzantısı         |
| Yerel veya ağ cihazlarına yazdırılan dosyalar      | Yerel             | Uzantısı         |
| Ağ paylaşımına aktarılan veya kopyalanan dosyalar | Uzantısı          | Uzantısı         |
| USB cihazlarına kopyalanan dosyalar                    | Uzantısı          | Uzantısı         |

## <a name="common-requirements"></a>Yaygın gereksinimler

Microsoft Edge eklentisini veya Google Chrome uzantısını yüklemeden önce müşterilerin kapsam içi ilke kullanıcıları için cihazların aşağıdaki gereksinimleri karşıladığından emin olması gerekir:

- Sinyal algılama desteği için en son Windows 10 x64 derlemesi önerilir, en az Windows 10 x64 derleme 1809. Tarayıcı sinyali algılama şu anda Windows olmayan cihazlarda desteklenmiyor.
- Insider risk yönetimi desteğine sahip geçerli [Microsoft 365 aboneliği](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing).
- Cihazların Microsoft 365 Uyumluluk portalına [eklenmelidir](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices).

Belirli tarayıcı yapılandırma gereksinimleri için bu makalenin devamında yer alan Microsoft Edge ve Google Chrome bölümlerine bakın.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Microsoft Edge için tarayıcı sinyali algılamayı yapılandırma

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge tarayıcı gereksinimleri

- Ortak gereksinimleri karşılama
- Microsoft Edge x64, 91.0.864.41 veya üzeri
- *Microsoft Uyumluluk Uzantısı* eklentisi sürüm 1.0.0.44 veya üzeri
- Edge.exe, izin verilmeyen bir tarayıcı olarak yapılandırılmadı

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Seçenek 1: Temel kurulum (Edge ile test için önerilir)

Tarayıcı sinyal algılamayı test ederken kuruluşunuzdaki her cihaz için tek makineli selfhost yapılandırmak için bu seçeneği kullanın.

Temel kurulum seçeneği için aşağıdaki adımları tamamlayın:

1. [Microsoft Uyumluluk Uzantısı'na](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo) gidin.
2. Uzantıyı yükleyin.

### <a name="option-2-intune-setup-for-edge"></a>2. Seçenek: Edge için Intune kurulumu

Intune kullanarak kuruluşunuz için uzantıyı ve gereksinimleri yapılandırmak için bu seçeneği kullanın.

Intune kurulum seçeneği için aşağıdaki adımları tamamlayın:

1. Yönetici izinlerini kullanarak [Microsoft Endpoint Manager Yönetim Merkezi'nde](https://endpoint.microsoft.com) oturum açın.
2. **Yapılandırma Profilleri'ne** gidin.
3. **Profil Oluştur'u** seçin.
4. Platform olarak **Windows 10** seçin.
5. *Profil türü* olarak **Yönetim Şablonları'nı** ve **ardından Oluştur'u seçin.**
6. **Ayarlar** sekmesini seçin.
7. **Edge Sürüm 77 ve üzeri'ne tıklayın.**
8. Uzantılarla ilgili tüm ayarlara genel bakış sağlayan **Uzantılar'ı** arayın.
9. **Hangi uzantıların sessizce yükleneceğini denetle** ayarını seçin.
10. **Etkin'i seçin.**
11. İstendiğinde uzantı kimliğini ekleyin: *lcmcgbabdcbngcbcfabdncmoppkajglo**.**
12. **Tamam'ı seçin.**

### <a name="option-3-group-policy-setup-for-edge"></a>3. Seçenek: Edge için grup ilkesi kurulumu

grup ilkesi kullanarak uzantıyı ve gereksinimleri kuruluş genelinde yapılandırmak için bu seçeneği kullanın.

grup ilkesi kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: En son Microsoft Edge Yönetim Şablonu (.admx) dosyasını içeri aktarın.**

Cihazların Grup İlkeleri kullanılarak yönetilebilir olması ve tüm [Microsoft Edge Yönetim Şablonlarının](https://www.microsoft.com/edge/business/download) grup ilkesi Central Store'a aktarılması gerekir. Daha fazla bilgi için bkz. [Windows'da grup ilkesi Yönetim Şablonları için Merkezi Mağaza'yı oluşturma ve yönetme](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**2. Adım: *Microsoft Uyumluluk Uzantısı* eklentisini *Yüklemeye Zorla* listesine ekleyin.**

Uzantıyı eklemek için aşağıdaki adımları tamamlayın:

1. **grup ilkesi Yönetim Düzenleyicisi'nde** Kuruluş Biriminize (OU) gidin.
2. **Aşağıdaki yolu Genişletin Bilgisayar/Kullanıcı yapılandırma** \> **İlkeleri** \> **Yönetim şablonları** \> **Klasik yönetim şablonları** \> **Microsoft Edge** \> **Uzantılar**. Bu yol, kuruluşunuzun yapılandırmasına bağlı olarak değişebilir.
3. **Hangi uzantıların sessizce yükleneceğini yapılandır'ı seçin.**
4. Sağ tıklayın ve **Düzenle'yi** seçin.
5. **Etkin** radyo düğmesini denetleyin.
6. **Göster'i** seçin.
7. **Değer** için şu girdiyi ekleyin: *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. **Tamam'ı** ve **ardından Uygula'yı** seçin.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Google Chrome için tarayıcı sinyali algılamayı yapılandırma

Google Chrome için Insider risk yönetimi tarayıcısı sinyal algılama desteği *Microsoft Uyumluluk Uzantısı* aracılığıyla etkinleştirilir. Bu uzantı, Chrome'da Endpoint DLP'i de destekler. Uç Nokta DLP desteği hakkında daha fazla bilgi için bkz. [Microsoft Uyumluluk Uzantısı (önizleme) ile Kullanmaya başlayın](/microsoft-365/compliance/dlp-chrome-get-started).

### <a name="google-chrome-browser-requirements"></a>Google Chrome tarayıcı gereksinimleri

- Yaygın gereksinimleri karşılama
- Google Chrome x64'ün en son sürümü
- *Microsoft Uyumluluk Uzantısı* sürüm 2.0.0.183 veya üzeri
- Chrome.exe, izin verilmeyen bir tarayıcı olarak yapılandırılmadı

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>1. Seçenek: Temel kurulum (Chrome ile test için önerilir)

Tarayıcı sinyal algılamayı test ederken kuruluşunuzdaki her cihaz için tek makineli selfhost yapılandırmak için bu seçeneği kullanın.

Temel kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: PowerShell ile gerekli Kayıt Defteri anahtarlarını etkinleştirme**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Uzantının düzgün işlevselliğini sağlamak için bu kayıt defteri anahtarları gereklidir. Sinyalleri test etmeden önce bu kayıt defteri anahtarlarını etkinleştirmeniz gerekir.*

**2. Adım: *Microsoft Uyumluluk Uzantısını* Yükleme**

1. [Microsoft Uyumluluk Uzantısı'na](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco) gidin.
2. Uzantıyı yükleyin.

### <a name="option-2-intune-setup-for-chrome"></a>Seçenek 2: Chrome için Intune kurulumu

Intune kullanarak kuruluşunuz için uzantıyı ve gereksinimleri yapılandırmak için bu seçeneği kullanın.

Intune kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: gerekli Kayıt Defteri anahtarını Intune ile etkinleştirme**

1. Aşağıdaki PowerShell betiğini çalıştırın:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. [Microsoft Endpoint Manager Yönetim Merkezi'nde](https://endpoint.microsoft.com) oturum açın.
3. **Cihaz** \> **Betikleri'ne** gidin ve **Ekle'yi seçin.**
4. İstendiğinde oluşturulan betiğin konumuna göz atın.
5. Aşağıdaki ayarları seçin:

    - Oturum açmış kimlik bilgilerini kullanarak bu betiği çalıştırın: *Evet*
    - Betik imzası denetimini zorunlu kılma: *Hayır*
    - Betiği 64 bit PowerShell Ana Bilgisayarında çalıştır: *Evet*

6. Uygun cihaz gruplarını seçin ve ilkeyi uygulayın.

**2. Adım: Yüklemeye Zorlama Intune Yapılandırma**

Microsoft DLP Chrome uzantısını zorla yüklenen uzantılar listesine eklemeden önce, Intune yönetimi için Chrome Yönetim Şablonu (.admx) dosyasını yüklemeniz gerekir. Adım adım yönergeler için bkz. [chrome tarayıcısını Microsoft Intune ile yönetme](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Yönetim Şablonu dosyasını yükledikten sonra aşağıdaki adımları tamamlayın:

1. [Microsoft Endpoint Manager Yönetim Merkezi'nde](https://endpoint.microsoft.com) oturum açın.
2. **Yapılandırma Profilleri'ne** gidin.
3. **Profil Oluştur'u** seçin.
4. *Platform* olarak **Windows 10'ı** seçin.
5. *Profil* türü olarak **Özel'i** seçin.
6. **Ayarlar** sekmesini seçin.
7. **Ekle'yi seçin.**
8. Aşağıdaki ilke bilgilerini girin:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Veri türü: *Dize*
    - Değer: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. **Oluştur**’u seçin.

### <a name="option-3-group-policy-setup-for-chrome"></a>3. Seçenek: Chrome için grup ilkesi kurulumu

grup ilkesi kullanarak uzantıyı ve gereksinimleri kuruluş genelinde yapılandırmak için bu seçeneği kullanın.

grup ilkesi kurulum seçeneği için aşağıdaki adımları tamamlayın:

**1. Adım: Chrome Yönetim Şablonu dosyasını içeri aktarma**

Cihazlarınız grup ilkesi kullanılarak yönetilebilir olmalıdır ve tüm [Chrome Yönetim Şablonlarının](https://chromeenterprise.google/browser/download/) grup ilkesi Central Store'a aktarılması gerekir. Daha fazla bilgi için bkz. [Windows'da grup ilkesi Yönetim Şablonları için Merkezi Mağaza'yı oluşturma ve yönetme](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**2. Adım: PowerShell ile gerekli Kayıt Defteri anahtarını etkinleştirme**

1. Aşağıdaki içeriklere sahip bir PowerShell betiği oluşturun:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. **grup ilkesi Yönetim Konsolu'nu** açın ve kuruluş biriminize (OU) gidin.
3. Sağ tıklayıp **Bu etki alanında GPO oluştur'u seçin ve buraya bağlayın**. İstendiğinde, bu grup ilkesi Nesnesine (GPO) açıklayıcı bir ad atayın. Örneğin, *DLP Chrome Anında PowerShell Betiği*.
4. GPO'yı oluşturduktan sonra sağ tıklayın ve **Düzenle'yi** seçin. Bu seçim sizi grup ilkesi Nesnesine götürür.
5. **Bilgisayar yapılandırması** \> **Tercihler** \> **Denetim masası ayarları** \> **Zamanlanmış görevler'e** gidin.
6. **Zamanlanmış Görevler'in** altındaki boş alana sağ tıklayın ve **Yeni** \> **Anında Görev 'i (en az Windows 7) seçin.**
7. Görev *Adı* ve *Açıklaması* girin.
8. Anında görevi çalıştırmak için ilgili hesabı seçin. Örneğin *, NT Yetkilisi*.
9. **En yüksek ayrıcalıklarla çalıştır'ı** seçin.
10. İlkeyi Windows 10 için yapılandırın.
11. **Eylemler** sekmesinde **Program başlat'ı** seçin.
12. **1. Adımda** oluşturulan programın/betiğin yolunu girin.
13. **Uygula'yı** seçin.

**3. Adım: Chrome uzantısını Yüklemeye Zorla listesine ekleme**

1. **grup ilkesi Yönetim Düzenleyicisi'nde** kuruluş biriminize (OU) gidin.
2. Aşağıdaki yolu genişletin **Bilgisayar/Kullanıcı yapılandırma** \> **İlkeleri** \> **Yönetim şablonları** \> **Klasik yönetim şablonları** \> **Google** \> **Google Chrome** \> **Uzantıları**. Bu yol, kuruluşunuzun yapılandırmasına bağlı olarak değişebilir.
3. **Zorla yüklenen uzantıların listesini yapılandır'ı** seçin.
4. Sağ tıklayın ve **Düzenle'yi** seçin.
5. **Etkin** radyo düğmesini seçin.
6. **Göster'i** seçin.
7. **Değer** için şu girdiyi ekleyin: *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. **Tamam'ı** ve **ardından Uygula'yı** seçin.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Insider risk yönetimi tarayıcısı sinyal algılamalarını test edin ve doğrulayın

1. Cihaz göstergeleri etkinleştirilmiş bir insider risk yönetimi ilkesi oluşturun.
2. Kişisel bulut depolama alanına kopyalanan dosyaların sinyal algılamasını test etmek için desteklenen bir Windows cihazından aşağıdaki adımları tamamlayın:

    - Sinyal algılama için yapılandırdığınız tarayıcı türüyle bir dosya paylaşım web sitesini (Microsoft OneDrive, Google Drive vb.) açın.
    - Tarayıcı ile web sitesine yürütülebilir olmayan bir dosya yükleyin.
3. Yerel veya ağ cihazlarına yazdırılan dosyalar, bir ağ paylaşımına aktarılan veya kopyalanan dosyalar ve USB cihazlarına kopyalanan dosyalar için sinyal algılamayı test etmek için desteklenen bir Windows cihazından aşağıdaki adımları tamamlayın:

    - Yürütülemeyen bir dosyayı doğrudan tarayıcıda açın. Dosya doğrudan Dosya Gezgini aracılığıyla açılmalı veya web sayfası yerine yeni bir tarayıcı sekmesinde açılmalıdır.
    - Dosyayı yazdırın.
    - Dosyayı bir USB cihazına kaydedin.
    - Dosyayı bir ağ sürücüsüne kaydedin.
  
4. İlk insider risk yönetimi ilkeniz oluşturulduktan sonra, yaklaşık 24 saat sonra etkinlik göstergelerinden uyarılar almaya başlarsınız. Test edilen etkinlikler için içeriden risk yönetimi uyarıları için [Uyarılar panosuna](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) bakın.
