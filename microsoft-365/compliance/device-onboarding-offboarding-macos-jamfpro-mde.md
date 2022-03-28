---
title: macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)
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
description: Uç nokta müşterileri için Microsoft Defender 'ı (önizleme) kullanarak mac Microsoft 365 OS cihazlarını JAMF Pro Uyumluluk çözümlerine ekleme ve çıkararak kullanma hakkında bilgi edinin
ms.openlocfilehash: f260d901f8f02c2c02007b2cc0d49ab9ee57dafd
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716331"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması (önizleme)

MacOS cihazlarını uyumluluk çözümlerine Pro IÇIN JAMF Microsoft 365 kullanabilirsiniz.

> [!IMPORTANT]
> MacOS ***cihazlarınıza Uç Nokta*** için Microsoft Defender (MDE) dağıttıysanız bu yordamı kullanın

**Aşağıdakiler için geçerlidir:**

- MacOS cihazlarına MDE dağıtan müşteriler.
- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızı JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) aracılığıyla yönettikten ve JAMF hizmeti veya Intune aracılığıyla bir kimlikle (Azure AD'ye katılmış UPN) ilişkilendirilmiş Bağlan emin olun.
- v95+ Edge tarayıcısını macOS cihazlarınıza yükleme

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>JAMF uyumluluk Microsoft 365 kullanarak cihazları Uyumluluk çözümlerine Pro

Bir macOS cihazı Uyumluluk çözümlerine ekleme, çok aşamalı bir işlemdir.

### <a name="download-the-configuration-files"></a>Yapılandırma dosyalarını indirme

1. Bu yordam için bu dosyalara ihtiyacınız vardır.

|için gereken dosya |kaynak |
|---------|---------|
|erişilebilirlik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[full ssd.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|MDE tercihi |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> *.mobileconfig dosyalarını tek tek* veya içeren tek [bir birleşik dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - full ssd.mobileconfig
>
>Bu tek tek dosyalardan herhangi biri güncelleştirilmişse, birleştirilmiş dosyayı ya da tek tek güncelleştirilmiş dosyayı yeniden indirmeniz gerekir.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>JAMF PRO konsolunu kullanarak mevcut MDE Tercihi etki alanı profilini güncelleştirme

1. İndirdiğiniz schema.xml **schema.json dosyasıyla** en son profili güncelleştirin.

1. **MDE Tercih Etki Alanı Özellikleri'nin** altında bu ayarları seçin
    - Özellikler 
        - Sistem Uzantılarını Kullanma: `enabled` - Catalina'da ağ uzantıları için gereklidir
        - Veri kaybını önlemeyi kullanma: `enabled`

1. Kapsam **sekmesini** seçin.

1. Bu yapılandırma profilinin dağıtımı için grupları seçin.

1. **Kaydet**'i seçin. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Tam disk erişimi ver için yapılandırma profilini güncelleştirme

1. mevcut tam disk erişimi profilini **full pie.mobileconfig dosyasıyla güncelleştirin** .

1. Upload **. mobileconfig dosyasını** JAMF'e kaydedin. [JAMF dosyası kullanarak Özel Yapılandırma Profillerini Dağıtma Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>DLP'ye erişilebilirlik erişimi ver

1. Daha önce indirdiğiniz accessibility.mobileconfig dosyasını kullanın.

1. Upload Yapılandırma Profillerini Jamf kullanarak Dağıtma konusunda [açıklandığı gibi JAMF'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>macOS cihazına bakın 

1. macOS cihazı yeniden başlatın.

1. Sistem **TercihleriProfiles'i** >  **açın**.

1. Şunları görüyor gerekir:
    - Erişilebilirlik
    - Tam Disk Erişimi
    - Kernel Extension Profile
    - MAU
    - MDATP Ekleme
    - MDE Tercihleri
    - Yönetim profili
    - Ağ filtresi
    - Bildirimler
    - Sistem uzantısı profili

## <a name="offboard-macos-devices-using-jamf-pro"></a>JAMF bağlantı cihazları kullanan offboard macOS Pro

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

MacOS cihazından çıkarılacak adımları izleyin

 1. **MDE Tercihi Etki Alanı Özellikleri altında**, bu ayarların değerlerini kaldırın
    - Özellikler 
        - Sistem Uzantılarını Kullanma
        - Veri Kaybını Önlemeyi Kullanma

1. **Kaydet**'i seçin.
