---
title: Uç Nokta için Microsoft Defender ile IoT için Microsoft Defender'a ekleme
description: IoT cihazlarına odaklanan görünürlük ve güvenlik değerlendirmeleri elde etmek için IoT için Microsoft Defender'a ekleyin.
keywords: siem bağlayıcısını, siem'i, bağlayıcıyı, güvenlik bilgilerini ve olayları etkinleştirme
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
ms.openlocfilehash: a70b61ff9a27b10e66b6f4537751790eaabc59af
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617292"
---
# <a name="onboard-with-microsoft-defender-for-iot"></a>IoT için Microsoft Defender ile ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Uç Nokta için Microsoft Defender artık IoT için Microsoft Defender ile sorunsuz bir şekilde tümleştirildi. Bu tümleştirme, IoT için Defender tarafından sağlanan aracısız izleme özellikleriyle cihaz bulma özelliklerinizi genişletir. Bu, İnternet Üzerinden Ses Protokolü (VoIP) cihazları, yazıcılar ve kameralar gibi BT ağlarına bağlı kurumsal IoT cihazlarının güvenliğini sağlamaya yardımcı olur. Kuruluşların tüm IoT ve Operasyonel Teknoloji (OT) altyapılarının güvenliğini sağlayan tek bir tümleşik çözümden yararlanmasına olanak tanır. Daha fazla bilgi için bkz [. Kurumsal IoT ağ koruması](/azure/defender-for-iot/organizations/overview-eiot).

IoT için Defender planı tanımlayıp Kurumsal IoT ağ algılayıcısı ayarladıktan sonra cihaz verileri otomatik olarak hem Uç Nokta için Defender hem de IoT için Defender portallarına akışla aktarmaya başlar. 

IoT için Defender tümleştirmesi ağınızdaki IoT cihazlarını bulmanıza, tanımlamanıza ve güvenliğini sağlamaya yardımcı olmak için daha fazla görünürlük sağlar. Bu, BT cihazlarınızın (iş istasyonları, sunucular ve mobil) yanı sıra tam OT/IoT envanterinizin tek bir birleşik görünümünü sağlar.

IoT için Defender'a eklenen müşterilerin ioT cihazları için güvenlik açığı değerlendirmeleri ve yanlış yapılandırmalar için güvenlik önerileri de vardır.

## <a name="prerequisites"></a>Önkoşullar

Uç Nokta için Defender tümleştirmenizin ayarlarını değiştirmek için kullanıcının aşağıdaki rollere sahip olması gerekir:

- Azure Active Directory'de Kiracı Genel Yöneticisi
- IoT için Microsoft Defender tümleştirmesi için kullanılacak Azure aboneliğinin Güvenlik Yöneticisi

## <a name="onboard-a-defender-for-iot-plan"></a>IoT için Defender planı ekleme

1. Portalın gezinti bölmesinde [https://security.microsoft.com](https://security.microsoft.com/) **Ayarlar** \> **Cihaz bulma** \> **Kurumsal IoT'yi** seçin.

1. Planınız için aşağıdaki seçenekleri belirleyin:

   - Azure Active Directory kiracınızda plan eklemek istediğiniz kullanılabilir abonelikler listesinden Azure aboneliğini seçin.

   - Aylık veya yıllık taahhüt ya da deneme sürümü olmak üzere bir fiyatlandırma planı seçin. IoT için Microsoft Defender, değerlendirme amacıyla ilk 1.000 taahhüt edilen cihaz için 30 günlük ücretsiz deneme sunar.

      Daha fazla bilgi [için IoT için Microsoft Defender fiyatlandırma sayfasına](https://azure.microsoft.com/pricing/details/iot-defender/) bakın.
   
   - İzlemek istediğiniz kaydedilmiş cihaz sayısını seçin. Bir deneme sürümü seçtiyseniz, varsayılan olarak 1000 cihazınız olduğundan bu bölüm görünmez.

## <a name="set-up-a-network-sensor"></a>Ağ algılayıcısı ayarlama

Ağ algılayıcısı ayarlamak için Azure aboneliğinizin, Kurumsal IoT cihazları eklenmiş bir IoT için Defender planına sahip olması gerekir. Daha fazla bilgi için bkz. [IoT için Defender'ı kullanmaya başlama](/azure/defender-for-iot/organizations/getting-started).

Ağ algılayıcısı eklemek için **Ağ algılayıcılarını ayarlama** altında **IoT için Microsoft Defender** bağlantısını seçin. Bu sizi Azure portal algılayıcı kurulum işlemine getirir. Daha fazla bilgi için bkz. [Kurumsal IoT'yi kullanmaya başlama](/azure/defender-for-iot/organizations/tutorial-getting-started-eiot-sensor).

## <a name="managing-your-iot-devices"></a>IoT cihazlarınızı yönetme

[ioT cihazlarınızı Microsoft 365 Defender portalında](https://security.microsoft.com/) görüntülemek ve yönetmek için **Uç Noktalar** gezinti menüsünden **Cihaz envanterine** gidin ve **IoT cihazları** sekmesini seçin.

IoT için Defender'da cihazları görüntüleme hakkında bilgi için bkz. [IoT cihazlarınızı kuruluşlar için cihaz envanteriyle yönetme](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations).


## <a name="view-devices-alerts-recommendations-and-vulnerabilities"></a>Cihazları, uyarıları, önerileri ve güvenlik açıklarını görüntüleme

Planınızı tanımladıktan ve bir ağ algılayıcısı ayarladıktan sonra aşağıdaki konumlarda algılanan verileri ve güvenlik değerlendirmelerini görüntüleyin:

- Uç Nokta için Defender'da veya IoT için Defender'da cihaz verilerini görüntüleme
- Uç Nokta için Defender'da uyarıları, önerileri ve güvenlik açıklarını görüntüleme

Daha fazla bilgi [için Bkz. IoT için Defender fiyatlandırma sayfası](https://azure.microsoft.com/pricing/details/iot-defender/). 

## <a name="cancel-your-defender-for-iot-plan"></a>IoT için Defender planınızı iptal etme

IoT için Defender planınızı portaldaki Uç Nokta için Defender ayarları sayfasından [https://security.microsoft.com](https://security.microsoft.com/) iptal edebilirsiniz. Planınızı iptal ettikten sonra tümleştirme durdurulur ve artık Uç Nokta için Defender'da güvenlik değerlendirmesi değeri alamaz veya IoT için Defender'da yeni cihazları algılamazsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz keşfine genel bakış](configure-device-discovery.md)
- [Cihaz keşfi hakkında SSS](device-discovery-faq.md)
