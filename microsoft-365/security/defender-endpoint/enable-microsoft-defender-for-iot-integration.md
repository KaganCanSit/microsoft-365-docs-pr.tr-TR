---
title: Uç Nokta için Microsoft Defender'da IoT tümleştirmesi için Microsoft Defender'ı Uç Nokta için Microsoft Defender
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
ms.openlocfilehash: 00b7a7abbf6c9fcb9395723e5e62ef0e89b2114a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470537"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>IoT tümleştirmesi için Microsoft Defender'ı etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Uç Nokta için Microsoft Defender artık IoT için Microsoft Defender ile tümleştirildi. Bu tümleştirme, IoT için Microsoft Defender tarafından sağlanan aracısız izleme özellikleriyle cihaz bulma yeteneklerinizi genişlettir. Bu, İnternet Protokolü (VoIP) cihazları, yazıcılar ve kameralar gibi, IT ağlarına bağlı kurumsal IoT cihazlarının güvenliğini sağlar. Kuruluşların tüm IoT ve Operasyon Teknolojisi (OT) altyapılarının güvenliğini sağlayan tek bir tümleşik çözümden yararlanmalarını sağlar. Daha fazla bilgi için bkz[. IoT Enterprise korumayı koruma](/azure/defender-for-iot/organizations/overview-eiot).

Bu tümleştirme etkinleştirildiğinde, Uç Nokta için Microsoft Defender IoT cihazlarının yerini belirlemeye ve güvenlik altına almaya yardımcı olmak için daha fazla görünürlük sağlar. IoT için Microsoft Defender tarafından bulunan IoT cihazları veya Uç Nokta için Microsoft Defender her iki portalda da otomatik olarak eşitlenir. Bu size, tüm OT/IoT envanterini, diğer IT cihazlarınız (iş istasyonları, sunucular ve mobil cihazlar) ile birlikte tek bir birleşik görünümde sunar.

IoT için Microsoft Defender ayrıca, ek bir veri kaynağı sağlayan, dağıtılabilir bir ağ algılayıcısı içerir. Tümleştirmenizin bir parçası olarak ağ algılayıcısı ayarlama, özellikle de Uç Nokta için Microsoft Defender algılayıcıların mevcut olmadığını ve çalışanların bilgilere uzaktan eriştikleri ağ kesimleri için, IoT ve OT cihazlarınızı en eksiksiz şekilde görüntülemenizi sağlar.

## <a name="prerequisites"></a>Önkoşullar

IoT için Microsoft Defender'ı etkinleştirmek için kullanıcının aşağıdaki rollere sahip olması gerekir:

- Kiracı Genel Yöneticisi'Azure Active Directory
- IoT tümleştirmesi için Microsoft Defender'da kullanılacak Azure aboneliğinin Güvenlik Yöneticisi

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>IoT için Microsoft Defender tümleştirmesini etkinleştirme

1. Portalın  gezinti bölmesinde, [https://security.microsoft.com](https://security.microsoft.com/) IoT için **Ayarlar** \> \> **Microsoft Defender'ı seçin**.

   :::image type="content" source="images/enable-defender-for-iot.png" alt-text="IoT tümleştirme kurulumu" lightbox="images/enable-defender-for-iot.png":::

2. **Kiracınız için geçerli** abonelikler açılan listesinden bir Azure aboneliği seçin Azure Active Directory Kaydet'i **seçin**.

## <a name="set-up-a-network-sensor"></a>Ağ algılayıcısı ayarlama

Bir Azure aboneliği seçiliyken bir ağ algılayıcısı  eklemeniz gerekir.

Ağ algılayıcısı eklemek için, Ağ **algılayıcılarını ayarlayın altından** **IoT bağlantısı için Microsoft Defender'ı** seçin. Bu, sizi yerleşik algılayıcı kurulum sürecinden Azure portal. Daha fazla bilgi için bkz[. Kamerada IoT için Defender ile algılayıcıları Azure portal](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud).

## <a name="turn-off-subscription-integration"></a>Abonelik tümleştirmeyi kapatma

Portalda IoT için Microsoft Defender ayarları sayfasından Azure aboneliği tümleştirmesini kapatabilirsiniz [https://security.microsoft.com](https://security.microsoft.com/) . Aboneliğinizi kapattıktan sonra, mobil cihaz envanteri içinde IoT için Microsoft Defender tarafından keşfedilen IoT Uç Nokta için Microsoft Defender göremeyeceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz keşfine genel bakış](configure-device-discovery.md)
- [Cihaz bulma hakkında SSS](device-discovery-faq.md)
