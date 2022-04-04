---
title: Cihaz ekleme ve Uç Nokta için Microsoft Defender
description: Kontrol etmek ve Intune oranını artırmak için Uç Nokta için Microsoft Defender cihazlarla işe alımları takip edin.
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
ms.openlocfilehash: 6caaddc208e6f73de0f49ff6d419c335848ae439
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466333"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Cihaz ekleme ve Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Her bir cihaz ek bir algılayıcı (uç noktada algılama ve yanıtlama EDR) algılayıcısı ekler ve ağ üzerindeki ihlal etkinliklerinin görünürlüğünü artırır. Kullanıma alma, ayrıca bir cihazın zayıf bileşenlerin yanı sıra güvenlik yapılandırma sorunları için de denetlenebilir ve saldırılar sırasında kritik düzeltme eylemleri al sağlar.

Cihazların kullanıcı kullanıcılarını izlemeden ve yönetmeden önce:

- [Cihazlarınızı okul yönetimine Intune kaydetme](configure-machines.md#enroll-devices-to-intune-management)
- [Gerekli izinlere sahip olduğundan emin olun](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Korumasız cihazları keşfetme ve izleme

Ekleme **kartı**, uç nokta için Defender for Endpoint'a yerleşik olarak bulunan Windows cihazlarının sayısını Intune yönetilen cihaz sayısıyla karşılaştırarak ekleme hızınıza ilişkin üst düzey bir Windows sunar.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Cihaz yapılandırma yönetimi Ekleme kartı" lightbox="images/secconmgmt_onboarding_card.png":::

*Cihaz tarafından yönetilen cihazların toplam sayısıyla Intune cihazları gösteren Windows kart*

> [!NOTE]
> Kullanıcı profili Configuration Manager ekleme betiği veya diğer ekleme yöntemlerini kullandıysanız, Intune tutarsızlıklarla karşılaşabilirsiniz. Bu tutarsızlıkları çözmek için, Uç nokta ekleme Intune Defender için ilgili bir profil oluşturun ve bu profili cihazlarınıza attayın.

## <a name="onboard-more-devices-with-intune-profiles"></a>Farklı profillere sahip daha Intune cihaz ekleme

Uç nokta için Defender, cihaz eklemeye ve [cihaz Windows sağlar](onboard-configure.md). Öte Intune yönetilen cihazlar için, Intune'den faydalanarak cihazları seçmek ve bu cihazları hizmete etkili bir şekilde eklemek için Uç nokta algılayıcısı için Defender'ı rahatça dağıtabilirsiniz.

Kullanıcı profili **oluşturmak ve bu** cihaza **profil atamak için**, Ekleme kartından Daha fazla cihaz Intune. Bu bağlantı sizi, başlangıç sayfasında cihaz uyumluluğu Intune alır ve bu da ekleme durumunuzla benzer bir genel bakış sağlar.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Cihaz Uç Nokta için Microsoft Defender yönetiminin en iyi Intune sayfası" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Uç Nokta için Microsoft Defender yönetimi hakkında daha fazla bilgi Intune uyumluluk sayfasını açın*

> [!TIP]
> Alternatif olarak, Tüm hizmetler ve Cihaz Uyumluluğu ve **Microsoft Defender ATP'den** [Microsoft Azure portalında](https://portal.azure.com/) Uç nokta ekleme uyumluluğu için Defender> Intune > Defender> sayfasına gidin.

> [!NOTE]
> En güncel cihaz verilerini görüntülemek için ATP algılayıcısı olmayan cihazlar **listesi'ne tıklayın**.

Cihaz uyumluluk sayfasında, uç nokta algılayıcısı için Defender'ın dağıtımı için özel olarak bir yapılandırma profili oluşturun ve bu profili almak istediğiniz cihazlara attayin. Bunu yapmak için şunları da yapabiliriz:

- **ATP algılayıcısı öğesini önceden tanımlanmış bir cihaz yapılandırma profiliyle** başlayacak şekilde yapılandırmak için Cihaz yapılandırma profili oluştur'ı seçin.
- Sıfırdan cihaz yapılandırma profilini oluşturun.

Daha fazla bilgi için[, Uç nokta için Defender Intune a cihaz yapılandırma profillerini ekleme hakkında bilgi edinebilirsiniz](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
- [Uç nokta güvenlik temeli için Defender'a uyumluluğu artırma](configure-machines-security-baseline.md)
- [ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme](configure-machines-asr.md)
