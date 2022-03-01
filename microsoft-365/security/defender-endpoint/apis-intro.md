---
title: Uç Nokta API'leri için Microsoft Defender'a erişme
ms.reviewer: ''
description: Uç nokta özellikleri için Microsoft Defender'a dayalı olarak iş akışlarını otomatikleştirmek ve yenilikler yapmak için API'leri nasıl kullanabileceğinizi öğrenin
keywords: apis, api, wdatp, open api, uç nokta api için microsoft defender, microsoft defender atp, genel api, desteklenen api'ler, uyarılar, cihaz, kullanıcı, etki alanı, ip, dosya, gelişmiş av, sorgu
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
ms.openlocfilehash: a73df39c6d26bdfd44a7f4f629e148e7f0afabb2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997155"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Uç Nokta API'leri için Microsoft Defender'a erişme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender, veri ve eylemlerinin büyük bir fazlasını bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, iş akışlarını otomatikleştirmenize ve Uç nokta özellikleri için Defender'a dayalı yenilikler yapmaya olanak sağlar. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Uç nokta API'leri için Defender'a hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- AAD [oluşturma](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Bu uygulamayı kullanarak bir erişim belirteci alın
- Belirteci, Uç Nokta API'si için Defender'a erişmek üzere kullanma

Uygulama Bağlamı veya Kullanıcı Bağlamı ile Uç Nokta API **için Defender'a** **erişebilirsiniz**.

- **Uygulama Bağlamı: (Önerilen)**

  Oturum alıkan bir kullanıcı sunuma gerek kalmadan çalıştıran uygulamalar tarafından kullanılır. örneğin, arka plan hizmetleri veya daemons olarak çalıştıran uygulamalar.

  Uygulama bağlamında Uç Nokta API için Defender'a erişmek için alınması gereken adımlar:

  1. Web Uygulaması AAD oluşturun.
  2. İstenen izni uygulamaya attayabilirsiniz; örneğin, 'Okuma Uyarıları', 'Yalıtmak Makineleri'.
  3. Bu Uygulama için bir anahtar oluşturun.
  4. Uygulamayı anahtarıyla kullanarak belirteç alın.
  5. Belirteci, Uç Nokta API'si için Microsoft Defender'a erişmek için kullanma

     Daha fazla bilgi için bkz [. Uygulama bağlamıyla erişim elde edin](exposed-apis-create-app-webapp.md).

- **Kullanıcı Bağlamı:**

  Kullanıcı adına API'de eylemler gerçekleştirmek için kullanılır.

  Kullanıcı bağlamında Uç Nokta API'si için Defender'a erişmek için atılması gereken adımlar:

  1. Yerel AAD bir uygulama oluşturun.
  2. Uygulamaya istediğiniz izni atayın; örneğin 'Okuma Uyarıları', 'Yalıtmak Makineleri' vb.
  3. Uygulamayı kullanıcı kimlik bilgileriyle kullanarak belirteç alın.
  4. Belirteci, Uç Nokta API'si için Microsoft Defender'a erişmek için kullanma

     Daha fazla bilgi için bkz [. Kullanıcı bağlamıyla erişim elde edin](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta API'leri için Microsoft Defender](exposed-apis-list.md)
- [Uygulama bağlamında Uç Nokta için Access Microsoft Defender](exposed-apis-create-app-webapp.md)
- [Kullanıcı bağlamında Uç Nokta için Access Microsoft Defender](exposed-apis-create-app-nativeapp.md)
