---
title: Uç Nokta için Microsoft Defender API’lere erişin
ms.reviewer: ''
description: api'leri kullanarak iş akışlarını otomatikleştirmeyi ve Uç Nokta için Microsoft Defender özelliklerine göre yenilik yapmayı öğrenin
keywords: apis, api, wdatp, open API, uç nokta api için microsoft defender, microsoft defender atp, genel API, desteklenen API'ler, uyarılar, cihaz, kullanıcı, etki alanı, ip, dosya, gelişmiş tehdit avcılığı, sorgu
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3638357d2c1440604858fabfa42e5df32569aed3
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172255"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Uç Nokta için Microsoft Defender API’lere erişin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler iş akışlarını otomatikleştirmenize ve Uç Nokta için Defender özelliklerine göre yenilik yapmanızı sağlar. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Uç Nokta için Defender API'lerine hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Genel olarak, API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:

- [AAD uygulaması](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp) oluşturma
- Bu uygulamayı kullanarak erişim belirteci alma
- Uç Nokta için Defender API'sine erişmek için belirteci kullanma

**Uygulama Bağlamı** veya **Kullanıcı Bağlamı** ile Uç Nokta için Defender API'lerine erişebilirsiniz.

- **Uygulama Bağlamı: (Önerilen)**

  Oturum açmış bir kullanıcı olmadan çalışan uygulamalar tarafından kullanılır. örneğin, arka plan hizmetleri veya daemon'lar olarak çalışan uygulamalar.

  Uygulama bağlamıyla Uç Nokta için Defender API'sine erişmek için izlenmesi gereken adımlar:

  1. bir AAD Web Uygulaması oluşturun.
  2. Uygulamaya istenen izni atayın, örneğin, 'Uyarıları Okuma', 'Makineleri Yalıtma'.
  3. Bu Uygulama için bir anahtar oluşturun.
  4. Anahtarıyla uygulamayı kullanarak belirteç alın.
  5. Uç Nokta için Microsoft Defender API'sine erişmek için belirteci kullanma

     Daha fazla bilgi için bkz. [Uygulama bağlamıyla erişim alma](exposed-apis-create-app-webapp.md).

- **Kullanıcı Bağlamı:**

  API'de kullanıcı adına eylemler gerçekleştirmek için kullanılır.

  Kullanıcı bağlamıyla Uç Nokta için Defender API'sine erişmek için atılması gereken adımlar:

  1. Yerel Uygulama AAD oluşturun.
  2. İstenen izni uygulamaya atayın; örneğin 'Uyarıları Okuma', 'Makineleri Yalıtma' vb.
  3. Kullanıcı kimlik bilgileriyle uygulamayı kullanarak belirteç alın.
  4. Uç Nokta için Microsoft Defender API'sine erişmek için belirteci kullanma

     Daha fazla bilgi için bkz. [Kullanıcı bağlamıyla erişim alma](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>İlgili konular

- [api'leri Uç Nokta için Microsoft Defender](exposed-apis-list.md)
- [Uygulama bağlamı ile Uç Nokta için Microsoft Defender erişme](exposed-apis-create-app-webapp.md)
- [Kullanıcı bağlamıyla Uç Nokta için Microsoft Defender erişme](exposed-apis-create-app-nativeapp.md)
