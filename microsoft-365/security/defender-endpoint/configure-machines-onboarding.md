---
title: Uç nokta için Microsoft Defender'a cihaz ekleme
description: Intune tarafından yönetilen cihazlarla Uç Nokta için Microsoft Defender'a ekleme ve ekleme oranını artırmayı takip edin.
keywords: onboard, Intune yönetimi, Uç Nokta için Microsoft Defender, Microsoft Defender, Windows Defender, yapılandırma yönetimi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ef0f461bef452336052018a26970bad94400fa71
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997545"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'a cihaz ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Her bir cihaz ek bir algılayıcı (uç noktada algılama ve yanıtlama EDR) algılayıcısı ekler ve ağ üzerindeki ihlal etkinliklerinin görünürlüğünü artırır. Kullanıma alma, ayrıca bir cihazın zayıf bileşenlerin yanı sıra güvenlik yapılandırma sorunları için de denetlenebilir ve saldırılar sırasında kritik düzeltme eylemleri al sağlar.

Cihazların kullanıcı kullanıcılarını izlemeden ve yönetmeden önce:

- [Cihazlarınızı Intune yönetimine kaydetme](configure-machines.md#enroll-devices-to-intune-management)
- [Gerekli izinlere sahip olduğundan emin olun](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Korumasız cihazları keşfetme ve izleme

Ekleme **kartı**, uç nokta için Defender for Endpoint'a yerleşik olarak bulunan Windows cihazlarının sayısını Intune tarafından yönetilen cihaz sayısıyla karşılaştırarak ekleme hızınıza ilişkin üst düzey bir Windows sunar.

![Cihaz yapılandırma yönetimi Ekleme kartı.](images/secconmgmt_onboarding_card.png)

*Intune tarafından yönetilen cihaz sayısına göre yerleşik cihazları gösteren Windows kart*

> [!NOTE]
> Configuration Manager kullandınız, ekleme betiği veya Intune profillerini kullanmayan diğer ekleme yöntemleri, veri ayrımları ile karşılaşabilirsiniz. Bu tutarsızlıkları çözmek için, Uç nokta ekleme için Defender için karşılık gelen bir Intune yapılandırma profili oluşturun ve bu profili cihazlarınıza attayın.

## <a name="onboard-more-devices-with-intune-profiles"></a>Intune profilleriyle daha fazla cihaz ekleme

Uç nokta için Defender, cihaz eklemeye ve [cihaz Windows sağlar](onboard-configure.md). Bununla birlikte Intune tarafından yönetilen cihazlarda, Cihazları seçmek ve bu cihazları hizmete etkili bir şekilde eklemek için Uç nokta algılayıcısı için Defender'ı rahatça dağıtmak için Intune profillerinden faydalanabilirsiniz.

**Intune'da** profil oluşturmak **ve atamak için**, Ekleme kartından Daha fazla cihaz edin'i seçin. Bu bağlantı sizi Intune'daki cihaz uyumluluğu sayfasına alır ve bu, ekleme durumunuzla benzer bir genel bakış sağlar.

![Intune cihaz yönetimi sayfasındaki Uç nokta cihaz uyumluluğu için Microsoft Defender.](images/secconmgmt_onboarding_1deviceconfprofile.png)

*Intune cihaz yönetiminde Uç nokta cihaz uyumluluk sayfası için Microsoft Defender*

> [!TIP]
> Alternatif olarak, Tüm hizmetler ve **Intune > Microsoft Defender ATP'den** Microsoft Azure [portalında](https://portal.azure.com/) Uç nokta ekleme uyumluluğu için Defender> a > gidin.

> [!NOTE]
> En güncel cihaz verilerini görüntülemek için ATP algılayıcısı olmayan cihazlar **listesi'ne tıklayın**.

Cihaz uyumluluk sayfasında, uç nokta algılayıcısı için Defender'ın dağıtımı için özel olarak bir yapılandırma profili oluşturun ve bu profili almak istediğiniz cihazlara attayin. Bunu yapmak için şunları da yapabiliriz:

- **ATP algılayıcısı öğesini önceden tanımlanmış bir cihaz yapılandırma profiliyle** başlayacak şekilde yapılandırmak için Cihaz yapılandırma profili oluştur'ı seçin.
- Sıfırdan cihaz yapılandırma profilini oluşturun.

Daha fazla bilgi için [, Cihazları Uç Nokta için Defender'a almak için Intune cihaz yapılandırma profillerini kullanma hakkında bilgi edinebilirsiniz](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
- [Uç nokta güvenlik temeli için Defender'a uyumluluğu artırma](configure-machines-security-baseline.md)
- [ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme](configure-machines-asr.md)
