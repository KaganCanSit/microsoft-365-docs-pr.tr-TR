---
title: Uç Nokta için Microsoft Defender'da IoT tümleştirmesi için Microsoft Defender'ı etkinleştirme
description: MDE'nin dağıtınmamış olduğu ağ alanlarında IoT/OT cihazlarına odaklanan görünürlük kazanmak için IoT için Microsoft Defender tümleştirmesini etkinleştirme
keywords: siem bağlayıcısı, siem, bağlayıcı, güvenlik bilgileri ve olayları etkinleştirme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 70d8586cb8f8babcdc709a67632f32103e9420ce
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996614"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>IoT tümleştirmesi için Microsoft Defender'ı etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Uç Nokta için Microsoft Defender artık IoT için Microsoft Defender ile tümleştirildi. Bu tümleştirme, IoT için Microsoft Defender tarafından sağlanan aracısız izleme özellikleriyle cihaz bulma yeteneklerinizi genişlettir. Bu, İnternet Protokolü (VoIP) cihazları, yazıcılar ve kameralar gibi, IT ağlarına bağlı kurumsal IoT cihazlarının güvenliğini sağlar. Kuruluşların tüm IoT ve Operasyon Teknolojisi (OT) altyapılarının güvenliğini sağlayan tek bir tümleşik çözümden yararlanmalarını sağlar. Daha fazla bilgi için bkz[. IoT Enterprise korumayı koruma](/azure/defender-for-iot/organizations/overview-eiot).

Bu tümleştirme etkinleştirildiğinde, Uç Nokta için Microsoft Defender ağ bağlantısında IoT cihazlarının yerini belirlemeye ve güvenlik altına almaya yardımcı olmak için daha fazla görünürlük sağlar. IoT için Microsoft Defender veya Uç Nokta için Microsoft Defender tarafından bulunan IoT cihazları her iki portalda da otomatik olarak eşitlenir. Bu size, tüm OT/IoT envanterini, diğer IT cihazlarınız (iş istasyonları, sunucular ve mobil cihazlar) ile birlikte tek bir birleşik görünümde sunar.

IoT için Microsoft Defender ayrıca, ek bir veri kaynağı sağlayan, dağıtılabilir bir ağ algılayıcısı içerir. Tümleştirmenizin bir parçası olarak ağ algılayıcısı ayarlama, özellikle Uç nokta algılayıcıları için Microsoft Defender'ın mevcut olmadığını ve çalışanların bilgilere uzaktan eriştikleri ağ kesimleri için, IoT ve OT cihazlarınızı en eksiksiz şekilde görüntülemenizi sağlar.

## <a name="prerequisites"></a>Önkoşullar

IoT için Microsoft Defender'ı etkinleştirmek için kullanıcının aşağıdaki rollere sahip olması gerekir:

- Kiracı Genel Yöneticisi'Azure Active Directory
- IoT tümleştirmesi için Microsoft Defender'da kullanılacak Azure aboneliğinin Güvenlik Yöneticisi

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>IoT için Microsoft Defender tümleştirmesini etkinleştirme

1. Portalın  gezinti bölmesinde, [https://security.microsoft.com](https://security.microsoft.com/) IoT için **Ayarlar** \> \> **Microsoft Defender'ı seçin**.

    ![IoT tümleştirme kurulumunun resmi.](images/enable-defender-for-iot.png)

2. **Kiracınız için geçerli** abonelikler açılan listesinden bir Azure aboneliği seçin Azure Active Directory Kaydet'i **seçin**.

## <a name="set-up-a-network-sensor"></a>Ağ algılayıcısı ayarlama

Bir Azure aboneliği seçiliyken bir ağ algılayıcısı  eklemeniz gerekir.

Ağ algılayıcısı eklemek için, Ağ **algılayıcılarını ayarlayın altından** **IoT bağlantısı için Microsoft Defender'ı** seçin. Bu sizi Azure portalda Yerleşik algılayıcı kurulum sürecine getirir. Daha fazla bilgi için bkz [. Azure portalda IoT için Defender ile algılayıcıları yönetme](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud).

## <a name="turn-off-subscription-integration"></a>Abonelik tümleştirmeyi kapatma

Portalda IoT için Microsoft Defender ayarları sayfasından Azure aboneliği tümleştirmesini kapatabilirsiniz [https://security.microsoft.com](https://security.microsoft.com/) . Aboneliği kapattıktan sonra, uç nokta cihaz envanteri için Microsoft Defender'da IoT için Microsoft Defender tarafından keşfedilen IoT cihazlarını artık görmeyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz keşfine genel bakış](configure-device-discovery.md)
- [Cihaz bulma hakkında SSS](device-discovery-faq.md)
