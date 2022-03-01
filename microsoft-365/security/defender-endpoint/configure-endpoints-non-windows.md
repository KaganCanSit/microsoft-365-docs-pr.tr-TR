---
title: Uç nokta Windows için Microsoft Defender'a cihaz olmayan cihazları ekleme
description: Uç nokta Windows için Microsoft Defender'a algılayıcı verileri gönder gönderecek şekilde, uyumlu olmayan cihazları yapılandırın.
keywords: Windows olmayan cihazları ekleme, macos, linux, cihaz yönetimi, Uç nokta cihazları için Microsoft Defender'ı yapılandırma
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4573e7002454e9e72648df42352104abaa4c22d6
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019443"
---
# <a name="onboard-non-windows-devices"></a>Windows olmayan cihazları ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformlar**
- macOS
- Linux

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

Uç Nokta için Defender, platformlar arasında Windows olmayan platformlar için merkezi bir Windows deneyimi sağlar. Bu ağ üzerinde desteklenen çeşitli işletim sistemlerinin (OS) uyarılarını Microsoft 365 Defender ve kuruluş ağın daha iyi korunmasını sebilirsiniz.

Tümleştirmenin çalışması için Uç Nokta için Defender ile uyumlu tam Linux dağıtımlarını ve macOS sürümlerini bilebilirsiniz. Daha fazla bilgi için bkz.:

- [Linux'ta Uç Nokta için Microsoft Defender sistem gereksinimleri](microsoft-defender-endpoint-linux.md#system-requirements)
- [macOS'ta Uç Nokta için Microsoft Defender sistem gereksinimleri](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Windows olmayan cihazlara ekleme

Cihaz olmayan cihazları işe almak için aşağıdaki Windows gerekir:

1. Tercih ettiğiniz ekleme yöntemini seçin:

   - macOS cihazlarda, Uç Nokta için Microsoft Defender aracılığıyla veya bir üçüncü taraf çözümü aracılığıyla eklemeye seçebilirsiniz. Daha fazla bilgi için bkz. [Mac'te Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac).

   - Üçüncü taraf tümleştirme Windows cihazlar için Cihaz olmayan **cihazları Windows cihazlarla birlikte kullanın'ı seçin**.
    1. Gezinti bölmesinde İş Ortakları ve **API'ler İş Ortağı Uygulamaları'ni** \> **seçin** . Üçüncü taraf çözümün listelenmiş olduğundan emin olun.
    2. İş **Ortağı Uygulamaları sayfasında**, iş ortağı olmayan cihazlarınızı destekleyen Windows seçin.
    3. İş **ortağının** sayfasını açmak için Görüntüle'ye tıklayın. Sayfada sağlanan yönergeleri izleyin.
    4. Bir hesap oluşturduktan veya iş ortağı çözümüne abone olduktan sonra, kurumuzda bir kiracı Genel Yöneticiden iş ortağı uygulamasından izin isteğini kabul etmelerini istenen bir aşamaya sahip olasınız. İzin isteğini dikkatle okuarak, isteğin gereken hizmetle uyumlu olduğundan emin olun.

2. Üçüncü taraf çözümün yönergelerini izleyerek bir algılama testi çalıştırın.

## <a name="offboard-non-windows-devices"></a>Kapalı alan olmayan Windows cihazlar

macOS ve Linux cihazları için, Uç Nokta için Microsoft Defender ile çıkartan seçeneğiyle çıkarabilirsiniz. Gezinti bölmesinde, **Çıkar'Ayarlar** \> **Seçin** \> **İşletim Sistemi'ni seçerek çıkar işlemini başlatın**.

Ayrıca üçüncü taraf tümleştirmesini devre dışı Windows olmayan cihazlarla çıkarabilirsiniz. Üçüncü taraf çözümlerini tümleştirerek Windows olmayan [platformlara sahip cihazların kapsama alanı etkinleştirin](https://security.microsoft.com/interoperability/partners).

## <a name="related-topics"></a>İlgili konular
- [Cihaz Windows ekleme](configure-endpoints.md)
- [Sunucuları ekleme](configure-server-endpoints.md)
- [Ara sunucu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [Uç nokta ekleme sorunları için Microsoft Defender sorunlarını giderme](troubleshoot-onboarding.md)
