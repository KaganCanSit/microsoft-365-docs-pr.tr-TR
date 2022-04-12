---
title: JAMF Pro (önizleme) kullanarak macOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: JAMF Pro (önizleme) kullanarak macOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma hakkında bilgi edinin
ms.openlocfilehash: 44e57e482c08b486563200010671b5c79329f7b2
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783831"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>JAMF Pro (önizleme) kullanarak macOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma

MacOS cihazlarını Uç nokta veri kaybını önleme gibi Microsoft 365 uyumluluk çözümlerine eklemek için JAMF Pro kullanabilirsiniz.

> [!IMPORTANT]
> macOS ***cihazlarınıza dağıtılmış*** Pertahanan Microsoft untuk Titik Akhir (MDE) yoksa bu yordamı kullanın

**Şunlar için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızın JAMF pro aracılığıyla yönetildiğinden ve JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) Bağlan veya Intune aracılığıyla bir kimlikle (Azure AD'ye katılmış UPN) ilişkilendirildiğinden emin olun.
- macOS cihazlarınıza v95+ Edge tarayıcısını yükleme

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>JAMF Pro kullanarak cihazları Microsoft 365 Uyumluluk çözümlerine ekleme

1. Bu yordam için bu dosyalara ihtiyacınız olacaktır.

|Için gereken dosya|Kaynak|
|---|---|
|Paket ekleme|Uyumluluk portalı **Ekleme paketinden** indirildi, dosya adı *DeviceComplianceOnboarding.plist*|
|Erişilebilir -lik|[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi|[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Ağ filtresi| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Sistem uzantıları|[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE tercihi|[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|MAU tercihi|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Yükleme paketi|uyumluluk portalından indirildi **Yükleme paketi**, dosya adı *\*wdav.pkg*\*|

> [!TIP]
> *.mobileconfig* dosyalarını tek tek veya aşağıdakileri içeren [tek bir birleştirilmiş dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
>
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Bu dosyalardan herhangi biri güncelleştirildiyse, birleştirilmiş dosyayı veya tek tek güncelleştirilmiş dosyayı tek tek indirmeniz gerekir.

MacOS cihazını Uyumluluk çözümlerine ekleme işlemi çok aşamalı bir işlemdir.

### <a name="get-the-device-onboarding-package"></a>Cihaz ekleme paketini alma

1. **Uyumluluk merkezinde** **Ayarlar** >  **Cihaz Ekleme'yi** açın ve **Ekleme'yi** seçin.

1. **Ekleme işlemini başlatmak için işletim sistemini seçin** **için macOS'u** seçin

1. **Dağıtım yöntemi** için **Mobil Cihaz Yönetimi/Microsoft Intune'ı** seçin

1. **Ekleme paketini indir'i** seçin

1. Cihaz ekleme paketinin içeriğini ayıklayın. JAMF klasöründe *DeviceComplainceOnboarding.plist* dosyasını görmeniz gerekir.

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Ekleme paketi için jamf Pro yapılandırma profili oluşturma

1. JAMF Pro'de yeni bir yapılandırma profili oluşturun. [JAMF Pro yöneticileri kılavuzuna](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) bakın. Şu değerleri kullanın:
    - Ad: `MDATP onboarding for macOS`
    - Açıklama: `MDATP EDR onboarding for macOS`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

2. JAMF Pro konsolunda **Uygulama & Özel ayarları >** **karşıya yükle'yi** seçin ve **ardından ekleyin**. Şu değeri kullanın:
    - Tercih Etki Alanı: `com.microsoft.wdav.atp`

3. **Karşıya yükle'yi** seçin ve **DeviceComplianceOnboarding.plist** ekleme dosyasını seçin.

4. **Kapsam** sekmesini seçin.

5. Hedef bilgisayarları seçin.

6. **Kaydet**'i seçin.

7. **Done** düğmesini seçin.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>JAMF PRO konsolunu kullanarak Tercih etki alanını yapılandırma

> [!IMPORTANT]
> Tercih Etki Alanı değeri olarak ***com.microsoft.wdav** _ kullanmalısınız. Pertahanan Microsoft untuk Titik Akhir yönetilen ayarlarını yüklemek için bu adı ve _ *_com.microsoft.wdav.ext_** kullanır.

1. JAMF Pro'de yeni bir yapılandırma profili oluşturun. [JAMF Pro yöneticileri kılavuzuna](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) bakın. Şu değerleri kullanın:
    - Ad: `MDATP MDAV configuration settings`
    - Açıklama: Bunu boş bırakın
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. **Uygulama & Özel Ayarlar** sekmesinde **Dış Uygulamalar'ı** seçin, **Ekle'yi** seçin ve tercih etki alanı için **Özel Şema'yı** seçin. Şu değeri kullanın:
    - Tercih etki alanı: `com.microsoft.wdav`

1. **Şema Ekle'yi** seçin ve *schema.json* dosyasını karşıya yüklemek için **Upload**.

1. **Kaydet**'i seçin.

1. **Tercih Etki Alanı Özellikleri'nin** altında bu ayarları seçin
    - Özellik
        - Sistem Uzantılarını Kullanma: `enabled` - Catalina'da ağ uzantıları için gereklidir
        - Veri Kaybı Önleme'yi kullanma: `enabled`
    - Pasif mod > virüsten koruma altyapısı: `true|false`. Yalnızca DLP dağıtıyorsanız kullanın `true`. DLP ve Pertahanan Microsoft untuk Titik Akhir (MDE) dağıtırken değer kullanın `false` veya atayın.

1. **Kapsam** sekmesini seçin.

1. Bu yapılandırma profilinin dağıtılacağı grupları seçin.

1. **Kaydet**'i seçin.

### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Microsoft AutoUpdate (MAU) için yapılandırma profili oluşturma ve dağıtma

1. **com.microsoft.autoupdate2.plist** dosyasını kullanarak jamf Pro yapılandırma dosyası oluşturun. [JAMF Pro yöneticileri kılavuzuna](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) bakın. Şu değerleri kullanın:
    - Ad: `MDATP MDAV MAU settings`
    - Açıklama: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. **Uygulama & Özel Ayarlar** **Upload** ve **Ekle'yi** seçin.

1. **Tercihler Etki Alanı** alanına girin `com.microsoft.autoupdate2` ve **ardından Upload'ı** seçin.

1. **com.microsoft.autoupdate2.plist** dosyasını seçin.

1. **Kaydet**'i seçin.

1. **Kapsam** sekmesini seçin.

1. Hedef bilgisayarları seçin.

1. **Kaydet**'i seçin.

1. **Done** düğmesini seçin.

### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Tam disk erişimi verme için yapılandırma profili oluşturma ve dağıtma

1. **fulldisk.mobileconfig** dosyasını kullanın.

1. **fulldisk.mobileconfig** dosyasını JAMF'ye Upload. [JAMF Pro kullanarak Özel Yapılandırma Profilleri Dağıtma](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html) bölümüne bakın.

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Sistem uzantıları için yapılandırma profili oluşturma ve dağıtma

1. [JAMF Pro yöneticileri kılavuzundaki yordamları kullanarak bir JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) yapılandırma dosyası oluşturun. Şu değerleri kullanın:
    - Ad: `MDATP MDAV System Extensions`
    - Açıklama: `MDATP system extensions`
    - Kategori: `none`
    - Dağıtım yöntemi: `install automatically`
    - Düzey: `computer level`

1. **Sistem uzantıları** profilinde şu değerleri girin:
    - Görünen Ad: `Microsoft Corp. System Extensions`
    - Sistem Uzantısı Türleri: `Allowed System Extensions`
    - Ekip Tanımlayıcısı: `UBF8T346G9`
    - İzin Verilen Sistem Uzantıları: `com.microsoft.wdav.epsext`, ve `com.microsoft.wdav.netext`

1. **Kapsam** sekmesini seçin.

1. Hedef bilgisayarları seçin.

1. **Kaydet**'i seçin.

1. **Done** düğmesini seçin.

### <a name="configure-network-extension"></a>Ağ uzantısını yapılandırma

1. GitHub'dan indirdiğiniz **netfilter.mobileconfig** dosyasını kullanın.

2. [Jamf Pro kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF'ye Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>DLP'ye erişilebilirlik erişimi verme

1. GitHub'den indirdiğiniz **accessibility.mobileconfig** dosyasını kullanın.

2. [Jamf Pro kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF'ye Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Yükleme paketini alma

1. **Uyumluluk merkezinde** **Ayarlar** >  **Cihaz Ekleme'yi** açın ve **Ekleme'yi** seçin.

1. **Ekleme işlemini başlatmak için işletim sistemini seçin** **için macOS'u** seçin

1. **Dağıtım yöntemi** için **Mobil Cihaz Yönetimi/Microsoft Intune'ı** seçin

1. **Yükleme paketini indir'i** seçin. Bu size *wdav.pkg* dosyasını verir.

### <a name="deploy-the-installation-package"></a>Yükleme paketini dağıtma

1. Dosyayı kaydettiğiniz `wdav.pkg` yere gidin.

1. JAMF Pro panosunu açın.

1. Bilgisayarınızı seçin ve üstteki dişliye tıklayın, ardından **Bilgisayar Yönetimi'ni** seçin.

1. **Paketler'de** **+Yeni'yi** seçin. Şu ayrıntıları girin:
    - Görünen Ad: .pkg dosyasını seçtiğinizde sıfırlanacağı için boş bırakın.
    - Kategori: Hiçbiri (varsayılan)
    - Dosya adı: Dosyayı seçin, bu durumda `wdav.pkg` dosyayı seçin.

1. **Aç'ı** seçin. Ayarlamak:
    - **Görünen Ad**: `Microsoft Endpoint Technology`
    - **Bildirim Dosyası**: gerekli değil
    - **Seçenekler sekmesi**: Varsayılan değerleri değiştirmeyin
    - **Sınırlamalar sekmesi**: varsayılan değerleri bırakın

1. **Kaydet**'i seçin. Bu işlem paketi JAMF Pro yükler.

1. **İlkeler** sayfasını açın.

1. Yeni bir ilke oluşturmak için **+Yeni'yi** seçin.

1. Bu değerleri girin
    - **Görünen ad**: `MDATP Onboarding200329 v100.86.92 or later`

1. **Yinelenen İade Et'i** seçin.

1. **Kaydet**'i seçin.

1. **PaketlerYapılandırma'yı** >  seçin.

1. **Ekle**'yi seçin.

1. **Kaydet**'i seçin.

1. **Kapsam** sekmesini seçin.

1. Hedef bilgisayarları seçin.

1. **Ekle**'yi seçin.

1. **Self servis'i** seçin.

1. **Done** düğmesini seçin.

### <a name="check-the-macos-device"></a>macOS cihazını denetleme

1. macOS cihazını yeniden başlatın.

1. Sistem **TercihleriProfiller'i** >  açın.

1. Şunu görmeniz gerekir:
    - Accessiblity
    - Tam Disk Erişimi
    - MAU
    - MDATP Ekleme
    - MDE Tercihleri
    - Yönetim profili
    - Ağ filtresi
    - Sistem uzantısı profili

## <a name="offboard-macos-devices-using-jamf-pro"></a>JAMF Pro kullanarak macOS cihazlarını çıkarma

1. Uygulamayı kaldırma (MDE kullanmıyorsa)
    1. Bkz. JAMF Pro Docs - Paket Dağıtımı - [JAMF Pro yöneticileri kılavuzuJamf](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro Yönetici Kılavuzu

1. macOS cihazını yeniden başlatma - Bazı uygulamalar yeniden başlatılana kadar yazdırma işlevselliğini kaybedebilir

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.
