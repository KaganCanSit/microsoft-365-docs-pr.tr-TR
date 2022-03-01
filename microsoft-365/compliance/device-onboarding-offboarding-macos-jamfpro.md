---
title: JAMF uyumluluk çözümleri kullanarak macOS cihazlarını Microsoft 365 kullanma ve çıkararak uyumluluk çözümlerine (Pro)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: JAMF uyumluluk çözümleri (önizleme) kullanarak macOS cihazlarını macOS Microsoft 365 ekleme ve kaldırmayı Pro öğrenin
ms.openlocfilehash: 2399dd901b9c31c3cd824e35bd4db844610125c5
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "63014119"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>JAMF uyumluluk çözümleri kullanarak macOS cihazlarını Microsoft 365 kullanma ve çıkararak uyumluluk çözümlerine (Pro)

MacOS cihazlarını, Uç Pro kaybı önleme gibi uyumluluk çözümlerine Microsoft 365 JAMF hizmeti kullanabilirsiniz.

> [!IMPORTANT]
> MacOS cihazlarınıza ***dağıtılmış*** Uç Nokta için Microsoft Defender (MDE) yoksa bu yordamı kullanın

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızı Azure AD'ye katıldığından emin olun](https://docs.jamf.com/10.30.0/jamf-pro/administrator-guide/Azure_AD_Integration.html)
- [macOS cihazlarınızı JAMF pro aracılığıyla yönetebilirsiniz](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- v95+ Edge tarayıcısını macOS cihazlarınıza yükleme 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>JAMF uyumluluk Microsoft 365 kullanarak cihazları Uyumluluk çözümlerine Pro

1. Bu yordam için bu dosyalara ihtiyacınız vardır.

|Için gereken dosya |Kaynak |
|---------|---------|
|Ekleme paketi    |Uyumluluk portalı Ekleme **paketinden indirilen** *DeviceComplianceOnboarding.plist dosya adı* |
|erişilebilirlik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[full ssd.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Ağ filtresi| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Sistem uzantıları |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE tercihi     |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|MAU tercihi|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Yükleme paketi     |uyumluluk portalı Yükleme **paketinden indirilen** *wdav.pkg\* dosya adı*\* |

> [!TIP]
> *.mobileconfig dosyalarını tek tek* veya içeren tek [bir birleşik dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - full ssd.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Bu tek tek dosyalardan herhangi biri güncelleştirilmişse, birleştirilmiş dosyayı ya da tek tek güncelleştirilmiş dosyayı yeniden indirmeniz gerekir.

Bir macOS cihazı Uyumluluk çözümlerine ekleme çok aşamalı bir işlemdir.

### <a name="get-the-device-onboarding-package"></a>Cihaz ekleme paketini al

1. Uyumluluk **merkezi'nde**, **Ayarlar** >  **Device Ekleme'yi açın ve** **Ekleme'yi seçin**.
 
1. ekleme **işlemini başlatmak için işletim sistemini seçin için** **macOS'u seçin**
 
1. Dağıtım **yöntemi olarak Mobil** Cihaz **Yönetimi/Cihaz Yönetimi'Microsoft Intune**
 
1. Ekleme **paketini indir'i seçin**
 
1. Cihaz ekleme paketinin içeriğini ayıkla. JAMF klasöründe *DeviceComplainceOnboarding.plist dosyasını görüyor* olun.

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Ekleme paketi için Pro bir JAMF yapılandırma profili oluşturma

1. JAMF çalışmalarında yeni bir yapılandırma profili Pro. [JAMF yöneticileri Pro bakın](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Şu değerleri kullanın:
    - Ad: `MDATP onboarding for macOS`
    - Açıklama: `MDATP EDR onboarding for macOS`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

2. JAMF uygulama Pro Uygulama > **Özel &, karşıya** **yükle'yi seçin ve** **ekle'yi seçin**. Şu değeri kullanın:
    - Tercih Etki Alanı: `com.microsoft.wdav.atp`

3. Karşıya **yükle'yi** seçin ve cihaz ekleme dosyasını **DeviceComplianceOnboarding.plist seçin**.

4. Kapsam **sekmesini** seçin.

5. Hedef bilgisayarları seçin.

6. **Kaydet**'i seçin.

7. **Done** düğmesini seçin.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>JAMF PRO konsolunu kullanarak Tercih etki alanını yapılandırma

> [!IMPORTANT]
> Tercih Etki Alanı değeri olarak ***com.microsoft.wdav** _ kullanabilirsiniz. Uç Nokta için Microsoft Defender yönetilen ayarlarını yüklemek için bu adı ve _ *_com.microsoft.wdav.ext_** kullanır.

1. JAMF çalışmalarında yeni bir yapılandırma profili Pro. [JAMF yöneticileri Pro bakın](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Şu değerleri kullanın:
    - Ad: `MDATP MDAV configuration settings`
    - Açıklama: Bunu boş bırakın
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. Uygulama Ayarları **özel & Dış uygulamalar Ayarlar**, Ekle'yi seçin ve tercih etki **alanı için** Özel  Şema'ya tıklayın. Şu değeri kullanın:
    - Tercih etki alanı: `com.microsoft.wdav`

1. Şema.json **Upload** için Şema Ekle'yi seçin ve sonra da *Şema.json dosyasını* karşıya yükleyin.

1. **Kaydet**'i seçin.

1. Tercih **Etki Alanı Özellikleri'nin altında** bu ayarları seçin
    - Özellikler 
        - Sistem Uzantılarını Kullanma: `enabled` - Catalina'da ağ uzantıları için gereklidir
        - Veri kaybını önlemeyi kullanma: `enabled`
    - Virüsten koruma > Edilgen modu: `true|false`. Yalnızca `true`DLP dağıtımında kullanın. DLP `false` ve Uç Nokta için Microsoft Defender'ın (MDE) dağıtımında değer kullanın veya bu değeri attayın.

1. Kapsam **sekmesini** seçin.

1. Bu yapılandırma profilinin dağıtımı için grupları seçin.

1. **Kaydet**'i seçin. 


### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Microsoft AutoUpdate (MAU) için yapılandırma profili oluşturma ve dağıtma

1. **com.microsoft.autoupdate2.plist** Pro bir JAMF dosyası oluşturun. [JAMF yöneticileri Pro bakın](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Şu değerleri kullanın:
    - Ad: `MDATP MDAV MAU settings`
    - Açıklama: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. Uygulama **Tercihleri& Özel Ayarlar** **Ekle'Upload'yi** **seçin**.

1. **Tercihler Etki Alanı alanına** girin `com.microsoft.autoupdate2` ve Tamam'ı **Upload**.

1. **com.microsoft.autoupdate2.plist dosyasını** seçin.

1. **Kaydet**'i seçin.

1. Kapsam **sekmesini** seçin.

1. Hedef bilgisayarları seçin.

1. **Kaydet**'i seçin.

1. **Done** düğmesini seçin.


### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Tam disk erişimi ver için yapılandırma profili oluşturma ve dağıtma

1. **full yapılandırılması.mobileconfig dosyasını** kullanın.

1. Upload **. mobileconfig dosyasını** JAMF'e kaydedin. [JAMF dosyası kullanarak Özel Yapılandırma Profillerini Dağıtma Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Sistem uzantıları için yapılandırma profili oluşturma ve dağıtma

1. JAMF ve Pro kılavuzunda yer alan yordamları kullanarak [bir JAMF Pro dosyası oluşturun](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Şu değerleri kullanın:
    - Ad: `MDATP MDAV System Extensions`
    - Açıklama: `MDATP system extensions`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. Sistem **uzantıları profiline** şu değerleri girin:
    - Görünen Ad: `Microsoft Corp. System Extensions`
    - Sistem Uzantısı Türleri: `Allowed System Extensions`
    - Ekip Tanımlayıcısı: `UBF8T346G9`
    - İzin Verilen Sistem Uzantıları: `com.microsoft.wdav.epsext`ve `com.microsoft.wdav.netext`

1. Kapsam **sekmesini** seçin.

1. Hedef bilgisayarları seçin.

1. **Kaydet**'i seçin.

1. **Done** düğmesini seçin.

### <a name="configure-network-extension"></a>Ağ uzantısını yapılandırma

1.  Bu **dosyadan indirdiğiniz netfilter.mobileconfig** GitHub.

2.  Upload Yapılandırma Profillerini Jamf kullanarak Dağıtma konusunda [açıklandığı gibi JAMF'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>DLP'ye erişilebilirlik erişimi ver

1. Dosyadan **indirdiğiniz accessibility.mobileconfig** GitHub.

2.  Upload Yapılandırma Profillerini Jamf kullanarak Dağıtma konusunda [açıklandığı gibi JAMF'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Yükleme paketini al

1. Uyumluluk **merkezi'nde**, **Ayarlar** >  **Device Ekleme'yi açın ve** **Ekleme'yi seçin**.
 
1. ekleme **işlemini başlatmak için işletim sistemini seçin için** **macOS'u seçin**
 
1. Dağıtım **yöntemi olarak Mobil** Cihaz **Yönetimi/Cihaz Yönetimi'Microsoft Intune**
 
1. Yükleme paketini **indir'i seçin**. Bu, *wdav.pkg dosyasını size* verecek.


### <a name="deploy-the-installation-package"></a>Yükleme paketini dağıtma

1. Dosyayı kayıtlı olduğu yere `wdav.pkg` gidin.

1. JAMF Pro açın.

1. Bilgisayarınızı seçin ve üst dişliye tıklayın, ardından Bilgisayar **Yönetimi'ne tıklayın**.

1. **Paketler'de** **+Yeni'yi seçin**. Şu ayrıntıları girin:
    - Görünen Ad: Boş bırakın çünkü .pkg dosyasını seçtiğiniz zaman sıfırlanır.
    - Kategori: Yok (varsayılan)
    - Dosyaadı: Bu durumda dosyayı `wdav.pkg` seçin.

1. **Aç'ı seçin**. Ayarla:
    - **Görünen Ad**: `Microsoft Endpoint Technology`
    - **Bildirim Dosyası**: Gerekli değil
    - **Seçenekler sekmesi**: varsayılan değerleri bırakma
    - **Sınırlamalar sekmesi**: varsayılan değerleri bırakın

1. **Kaydet**'i seçin. Bu, paketi JAMF dosyalarına Pro.

1. **İlkeler sayfasını** açın.

1. Yeni **bir ilke oluşturmak için +** Yeni'yi seçin.

1. Bu değerleri girin
    - **Görünen ad**: `MDATP Onboarding200329 v100.86.92 or later`

1. Yinelenen **Iade'yi seçin**.

1. **Kaydet**'i seçin.

1. **PackagesConfigure'ı** >  **seçin**.

1. **Ekle**'yi seçin.

1. **Kaydet**'i seçin. 

1. Kapsam **sekmesini** seçin.

1. Hedef bilgisayarları seçin.

1. **Ekle**'yi seçin.

1. Self **servis'i seçin**.

1. **Done** düğmesini seçin.

### <a name="check-the-macos-device"></a>macOS cihazına bakın 

1. macOS cihazı yeniden başlatın.

1. Sistem **TercihleriProfiles'i** >  **açın**.

1. Şunları görüyor gerekir:
    - Erişilebilirlik
    - Tam Disk Erişimi
    - MAU
    - MDATP Ekleme
    - MDE Tercihleri
    - Yönetim profili
    - Ağ filtresi
    - Sistem uzantısı profili

## <a name="offboard-macos-devices-using-jamf-pro"></a>JAMF bağlantı cihazları kullanan offboard macOS Pro

1. Uygulamayı kaldırma (MDE kullan
    1. Bkz. JAMF Pro Belgeleri - Paket Dağıtımı - [JAMF Pro yöneticileri kılavuzuJamf](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro Kılavuzu

1. macOS cihazı yeniden başlatın. Bazı uygulamalar yeniden başlatana kadar yazdırma işlevselliğini kaybedebilir

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.
