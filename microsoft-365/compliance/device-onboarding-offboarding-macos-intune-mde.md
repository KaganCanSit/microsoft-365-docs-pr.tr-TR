---
title: Uç Nokta için Microsoft Defender müşterileri için Microsoft Intune kullanarak macOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkarma
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
description: MDE müşterileri için Microsoft Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma hakkında bilgi edinin
ms.openlocfilehash: 3e6947483a4d3320b61211edeb0f9fdc3e31095d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623041"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers"></a>macOS cihazlarının Uç Nokta için Microsoft Defender müşterileri için Intune kullanarak Uyumluluk çözümlerine katılımı ve çıkarılması

> [!IMPORTANT]
> macOS cihazlarınıza Uç Nokta için Microsoft Defender (MDE) ***dağıttıysanız*** bu yordamı kullanın

**Şunlar için geçerlidir:**

- MDE'yi macOS cihazlarına dağıtan müşteriler.
- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)


## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızın Intune eklenip Şirket Portalı](/mem/intune/fundamentals/deployment-guide-platform-macos) [uygulamasına](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) kaydedildiğinden emin olun. 
- [Microsoft Endpoint Manager merkezine](https://endpoint.microsoft.com/#home) erişiminiz olduğundan emin olun
- Bu, macOS sürüm Catalina 10.15 ve üzerini destekler
- macOS cihazlarınıza v95+ Edge tarayıcısını yükleme 

## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Microsoft Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme

Zaten MDE dağıtılmışsa macOS cihazını Uyumluluk çözümlerine eklemek için bu adımları kullanın.

1. Bu yordam için bu dosyalara ihtiyacınız olacaktır.

|için gereken dosya |Kaynak |
|---------|---------|
|Erişilebilir -lik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> *.mobileconfig* dosyalarını tek tek veya aşağıdakileri içeren [tek bir birleştirilmiş dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Bu dosyalardan herhangi biri güncelleştirildiyse, birleştirilmiş dosyayı veya tek tek güncelleştirilmiş dosyayı tek tek indirmeniz gerekir.

### <a name="create-system-configuration-profiles"></a>Sistem yapılandırma profilleri oluşturma

1. **Microsoft Endpoint Manager merkezi** > **Cihazlar** > **Yapılandırma profillerini** açın.

1. Seçin: **Profil oluştur**. 

1. Seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'u** seçin

1. Bu örnekteki *AccessibilityformacOS* gibi bir profil adı seçin. **İleri**'yi seçin.

1. Yapılandırma profili dosyası olarak 1. adımda indirdiğiniz **accessibility.mobileconfig** dosyasını seçin.

1. **İleri'yi** seçin

1. **Atamalar** sekmesinde, bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve **İleri'yi** seçin.

1. Ayarlarınızı gözden geçirin ve **oluştur'u** seçerek yapılandırmayı dağıtın.

1. **Cihaz** > **Yapılandırma profillerini** açın, oluşturduğunuz profilleri orada görmeniz gerekir.

1. **Yapılandırma profilleri** sayfasında, az önce oluşturduğunuz profili seçin, bu örnekte *ErişilebilirlikformacOS* ve cihaz listesini ve yapılandırma profilinin dağıtım durumunu görmek için **Cihaz durumu'nu** seçin.

### <a name="update-configuration-profiles"></a>Yapılandırma profillerini güncelleştirme

1. Var olan tam disk erişim profilini **fulldisk.mobileconfig** dosyasıyla güncelleştirin.

1. Mevcut MDE tercihleri profilini bu değerlerle güncelleştirin
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Intune kullanarak macOS cihazlarını çıkarma

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

1. **Microsoft Endpoint Manager merkezinde** **Cihazlar** > **Yapılandırma profillerini** açın, oluşturduğunuz profilleri orada görmeniz gerekir.

2. **Yapılandırma profilleri** sayfasında MDE tercihleri profilini seçin.

1. Şu ayarları kaldırın:
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **Kaydet'i seçin**.
