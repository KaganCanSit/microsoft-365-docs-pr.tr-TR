---
title: Bulut Uygulamaları için Microsoft Defender tümleştirmeye genel bakış
ms.reviewer: ''
description: Uç Nokta için Microsoft Defender, tüm bulut uygulaması ağ etkinliklerini ileterek Bulut Uygulamaları için Defender ile tümleştirilmiştir.
keywords: bulut, uygulama, ağ, görünürlük, kullanım
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d3cf5259aeb070175d5d2a4a95154974c6cd4d56
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021592"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>Uç Nokta için Defender'da Bulut Uygulamaları için Microsoft Defender'a genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bulut Uygulamaları için Microsoft Defender, bulut uygulamalarına erişimi denetlemenizi ve bu uygulamalara erişimi sınırlandırmanıza olanak sağlarken bulutta depolanan verilerde uyumluluk gereksinimlerini de zorlayarak bulut uygulamaları ve hizmetlerinin görünürlüğünü sağlayan kapsamlı bir çözümdür. Daha fazla bilgi için bkz. [Bulut Uygulamaları için Defender](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> Bu özellik, 1809 veya [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) 11 sürümünü çalıştıran Windows 10 çalıştıran cihazlarda E5 Windows ile kullanılabilir.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>Bulut Uygulamaları tümleştirmesi için Uç Nokta ve Defender için Microsoft Defender

Bulut Uygulamaları için Defender bulma, bulut trafiği günlüklerinin kurumsal güvenlik duvarından ve ara sunuculardan bu günlüklere ilet  özeldir. Uç Nokta için Microsoft Defender, tüm bulut uygulaması ağ etkinlikleri toplayarak ve ileterek Bulut Uygulamaları için Defender ile tümleştirerek, bulut uygulama kullanımına benzersiz görünürlük sağlar. İzleme işlevselliği cihazda yerleşik olarak yer alınarak ağ etkinliğinin tam kapsamda yer alan bir özelliğidir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

Tümleştirme, mevcut Bulut Uygulamaları için Defender'ı bulma konusunda aşağıdaki önemli geliştirmeleri sağlar:

- Her yerde kullanılabilir - Ağ etkinliği doğrudan uç noktadan toplanmış olduğu için, cihazın olduğu her yerde, şirket ağına açık veya kapalı olarak kullanılabilir çünkü artık kurumsal güvenlik duvarı veya ara sunuculardan yönlendiren trafik bağlı değildir.

- Hazır çalışır, yapılandırma gerekmez - Bulut trafiği günlüklerinin Bulut Uygulamaları için Defender'a ilet olması için güvenlik duvarı ve ara sunucu yapılandırması gerekir. Uç Nokta için Defender ve Bulut Uygulamaları için Defender tümleştirmesi ile yapılandırma gerekmez. Bu ayarı Microsoft 365 Defender ve artık devam edebilirsiniz.

- Cihaz bağlamı - Bulut trafiğinde cihaz bağlamı eksik. Uç nokta ağ etkinliği için Defender, cihaz bağlamında (bulut uygulamasına erişilen cihaz) raporlandığı için, ağ etkinliğini kimin (kullanıcı) gerçekleştireceğiyle birlikte tam olarak nerede gerçekleştir olduğunu (cihaz) anlıyoruz.

Bulut bulma hakkında daha fazla bilgi için bkz [. Bulunan uygulamalarla çalışma](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>İlgili konu

- [Bulut Uygulamaları tümleştirmesi için Microsoft Defender'ı yapılandırma](microsoft-cloud-app-security-config.md)
