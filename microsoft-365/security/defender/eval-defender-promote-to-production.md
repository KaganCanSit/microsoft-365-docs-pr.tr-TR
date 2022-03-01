---
title: Değerlendirme ortamınızı Microsoft 365 Defender üretim ortamına tanıtma
description: Bu makaleyi, Bulut Uygulamaları için MDI, MDO, MDE ve Defender evallarını Microsoft 365 Defender veya M365D'de canlı ortamınıza tanıtmak için kullanın.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e4b852ef7f252033a67e6aa3f1f8183400c18bdb
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034406"
---
# <a name="promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Değerlendirme ortamınızı Microsoft 365 Defender üretime tanıtma

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Değerlendirme ortamınızı Microsoft 365 Defender için önce gerekli lisansı satın alın. Ev ortamı oluşturma [ve Ücretsiz denemeyi başlat'ı](eval-create-eval-environment.md) Office 365 E5 lisansı satın alma'daki adımları izleyin.

Ardından, tüm ek yapılandırmaları tamamlanın ve tam üretime ulaşana kadar pilot gruplarınızı genişletin.

## <a name="microsoft-defender-for-identity"></a>Kimlik için Microsoft Defender

Kimlik için Defender herhangi bir ek yapılandırma gerektirmez. Gerekli lisansları satın aldığınızdan ve algılayıcıyı tüm Active Directory etki alanı denetleyicilerinize ve Active Directory Federasyon Hizmetleri (AD FS) sunucularına yüklemiş olmalısınız.

## <a name="microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender

MDO'yu başarıyla değerlendirdikten veya bu testlerden sonra, bu tüm üretim ortamınıza yükselt olabilir.

1. Gerekli lisansları satın alın ve sağlanması ve üretim kullanıcılarınıza ataması.
2. Önerilen temel ilke yapılandırmalarını (Standart veya Katı) üretim e-posta etki alanınıza veya belirli kullanıcı gruplarına karşı yeniden çalıştırın.
3. İsteğe bağlı olarak, üretim e-posta etki alanınıza veya kullanıcı gruplarınıza karşı tüm özel MDO ilkelerini oluşturun ve yapılandırabilirsiniz.  Bununla birlikte, atanan temel ilkelerinin her zaman özel ilkelere göre öncelikli olduğunu unutmayın.
4. Doğrudan EOP'ye çözümlemek için, üretim e-posta etki alanınıza genel MX kaydını güncelleştirin.
5. Üçüncü taraf SMTP ağ geçitlerini devre dışı bırakın ve bu geçişle ilişkilendirilmiş EXO bağlayıcılarını devre dışı bırakın veya silin.

## <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

Uç nokta değerlendirme ortamı için Microsoft Defender'ı pilotdan üretime teşvik etmek için, desteklenen araç ve yöntemlerden herhangi birini kullanarak hizmete daha fazla [uç nokta eklemeniz gerekir](../defender-endpoint/onboard-configure.md).

Uç nokta için Microsoft Defender'a daha fazla cihaz eklemeye yardımcı olmak için aşağıdaki genel yönergeleri kullanın.

1. Cihazın en düşük gereksinimleri karşı çalıştığını [doğrulayın](../defender-endpoint/minimum-requirements.md).
2. Cihaza bağlı olarak, Uç nokta için Defender portalının ekleme bölümünde sağlanan yapılandırma adımlarını izleyin.
3. Cihazlarınız için uygun yönetim aracını ve dağıtım yöntemini kullanın.
4. Cihazların düzgün bir şekilde işe alındıklarını ve hizmete rapor edildiklerini doğrulamak için bir algılama testi çalıştırın.

## <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

Bulut Uygulamaları için Microsoft Defender ek yapılandırma gerektirmez. Gerekli lisansları satın aldığınızdan emin olun. Belirli kullanıcı gruplarının dağıtımının kapsamını kullandıysanız, üretim ölçeğine ulaşana kadar bu grupların kapsamını artırabilirsiniz.
