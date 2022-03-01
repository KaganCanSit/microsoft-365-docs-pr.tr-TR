---
title: Uç nokta müşterileri için Microsoft Defender 'ı kullanarak macOS cihazlarını Microsoft Intune Uyumluluk çözümlerine ekleme ve çıkararak kullanma (önizleme)
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
description: MDE müşterileri için Microsoft Intune (önizleme) kullanarak macOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve kaldırmayı öğrenin
ms.openlocfilehash: 0486c08734e049a82550c1fb596b0e3d789126b8
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "63014118"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview"></a>Uç nokta müşterileri için Microsoft Defender'ı kullanarak MacOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkararak kullanma (önizleme)

> [!IMPORTANT]
> MacOS ***cihazlarınıza Uç Nokta*** için Microsoft Defender (MDE) dağıttıysanız bu yordamı kullanın

**Aşağıdakiler için geçerlidir:**

- MacOS cihazlarına MDE dağıtan müşteriler.
- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızı Intune'a ekli olduğundan ve cihazlarında Mobil](/mem/intune/fundamentals/deployment-guide-platform-macos) Şirket Portalı [olun](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Merkezin Erişim Merkezi'ne Microsoft Endpoint Manager [emin olun](https://endpoint.microsoft.com/#home)
- Bu, macOS catalina 10.15 ve daha yüksek sürümünü destekler
- v95+ Edge tarayıcısını macOS cihazlarınıza yükleme 

## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>MacOS cihazlarını Uyumluluk çözümleri Microsoft 365 uyumluluk çözümlerine Microsoft Intune

Bir macOS cihazı için MDE zaten dağıtılmışsa Uyumluluk çözümlerine bu adımları izleyin.

1. Bu yordam için bu dosyalara ihtiyacınız vardır.

|için gereken dosya |kaynak |
|---------|---------|
|erişilebilirlik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[full ssd.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> *.mobileconfig dosyalarını tek tek* veya içeren tek [bir birleşik dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - full ssd.mobileconfig
> 
>
>Bu tek tek dosyalardan herhangi biri güncelleştirilmişse, birleştirilmiş dosyayı ya da tek tek güncelleştirilmiş dosyayı yeniden indirmeniz gerekir.

### <a name="create-system-configuration-profiles"></a>Sistem yapılandırma profilleri oluşturma

1. Microsoft Endpoint Manager **centerDevicesConfiguration** >  >  **profillerini açın**.

1. Seçin: **Profil oluştur**. 

1. Şunları seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'a**

1. Profil için, bu örnekteki *AccessibilityformacOS gibi bir* ad seçin. **İleri**'yi seçin.

1. Yapılandırma profili dosyası olarak 1. adımda indirdiğiniz **accessibility.mobileconfig** dosyasını seçin.

1. Sonraki'yi **seçin**

1. Atamalar **sekmesinde,** bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve Sonraki'yi **seçin**.

1. Ayarlarınızı gözden geçirebilirsiniz ve **yapılandırmayı dağıtmak için** Oluştur'a tıklayın.

1. Cihazları **Yapılandırma** >  **profillerini açın**, oluşturduğunuz profilleri burada görüyor olun.

1. Yapılandırma **profilleri sayfasında**, bu örnekte *AccessibilityformacOS'ta* yeni oluşturduğunuz profili seçin ve cihazların listesini ve yapılandırma profilinin dağıtım  durumunu görmek için Cihaz durumu'u seçin.

### <a name="update-configuration-profiles"></a>Yapılandırma profillerini güncelleştirme

1. mevcut tam disk erişimi profilini **full pie.mobileconfig dosyasıyla güncelleştirin** .

1. Genişletilebilir MDE tercihleri profilini bu değerlerle güncelleştirme
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Intune kullanan offboard macOS cihazları

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

1. **Merkezin Microsoft Endpoint Manager** **DevicesConfiguration** >  profillerini açın, oluşturduğunuz profilleri burada görüyor olun.

2. Yapılandırma **profilleri sayfasında** MDE tercihleri profilini seçin.

1. Bu ayarları kaldırın:
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **Kaydet'i tıklatın**.