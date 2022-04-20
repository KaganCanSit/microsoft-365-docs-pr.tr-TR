---
title: Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak macOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkarma
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
description: Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma hakkında bilgi edinin
ms.openlocfilehash: ba2ff7723e54451ace46823fafb5323dcb35069e
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953393"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers"></a>Uç Nokta için Microsoft Defender müşterileri için JAMF Pro kullanarak macOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkarma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

MACOS cihazlarını Microsoft Purview çözümlerine eklemek için JAMF Pro kullanabilirsiniz.

> [!IMPORTANT]
> macOS cihazlarınıza Uç Nokta için Microsoft Defender (MDE) ***dağıttıysanız*** bu yordamı kullanın

**Şunlar için geçerlidir:**

- MDE'yi macOS cihazlarına dağıtan müşteriler.
- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)


## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızın JAMF pro aracılığıyla yönetildiğinden ve JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) Bağlan veya Intune aracılığıyla bir kimlikle (Azure AD'ye katılmış UPN) ilişkilendirildiğinden emin olun.
- macOS cihazlarınıza v95+ Edge tarayıcısını yükleme

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>JAMF Pro kullanarak cihazları Microsoft Purview çözümlerine ekleme

MacOS cihazını Uyumluluk çözümlerine ekleme çok aşamalı bir işlemdir.

### <a name="download-the-configuration-files"></a>Yapılandırma dosyalarını indirme

1. Bu yordam için bu dosyalara ihtiyacınız olacaktır.

|için gereken dosya |Kaynak |
|---------|---------|
|Erişilebilir -lik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|MDE tercihi |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> *.mobileconfig* dosyalarını tek tek veya aşağıdakileri içeren [tek bir birleştirilmiş dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Bu dosyalardan herhangi biri güncelleştirildiyse, birleştirilmiş dosyayı veya tek tek güncelleştirilmiş dosyayı tek tek indirmeniz gerekir.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>JAMF PRO konsolunu kullanarak mevcut MDE Tercihi etki alanı profilini güncelleştirme

1. schema.xml profilini indirdiğiniz **schema.json** dosyasıyla güncelleştirin.

1. **MDE Tercih Etki Alanı Özellikleri'nin** altında bu ayarları seçin
    - Özellik 
        - Sistem Uzantılarını Kullanma: `enabled` - Catalina'da ağ uzantıları için gereklidir
        - Veri Kaybı Önleme'yi kullanma: `enabled`

1. **Kapsam** sekmesini seçin.

1. Bu yapılandırma profilinin dağıtılacağı grupları seçin.

1. **Kaydet**'i seçin. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Tam disk erişimi ver için yapılandırma profilini güncelleştirme

1. Var olan tam disk erişim profilini **fulldisk.mobileconfig** dosyasıyla güncelleştirin.

1. **fulldisk.mobileconfig** dosyasını JAMF'ye Upload. [JAMF Pro kullanarak Özel Yapılandırma Profilleri Dağıtma](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html) bölümüne bakın.

### <a name="grant-accessibility-access-to-dlp"></a>DLP'ye erişilebilirlik erişimi verme

1. Daha önce indirdiğiniz accessibility.mobileconfig dosyasını kullanın.

1. [Jamf Pro kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF'ye Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>macOS cihazını denetleme 

1. macOS cihazını yeniden başlatın.

1. Sistem **TercihleriProfiller'i** >  açın.

1. Şunu görmeniz gerekir:
    - Accessiblity
    - Tam Disk Erişimi
    - Çekirdek Uzantısı Profili
    - MAU
    - MDATP Ekleme
    - MDE Tercihleri
    - Yönetim profili
    - Ağ filtresi
    - Bildirim
    - Sistem uzantısı profili

## <a name="offboard-macos-devices-using-jamf-pro"></a>JAMF Pro kullanarak macOS cihazlarını çıkarma

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

MacOS cihazını çıkarmak için şu adımları izleyin

 1. **MDE Tercihi Etki Alanı Özellikleri** altında bu ayarların değerlerini kaldırın
    - Özellik 
        - Sistem Uzantılarını Kullanma
        - Veri Kaybı Önleme'yi kullanma

1. **Kaydet**'i seçin.
