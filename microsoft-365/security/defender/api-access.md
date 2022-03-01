---
title: Api'lere Microsoft 365 Defender erişme
description: Api'lere nasıl Microsoft 365 Defender öğrenin
keywords: access, api'ler, uygulama bağlamı, kullanıcı bağlamı, aad uygulaması, erişim belirteci
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a8406c0ec27c238615b25f60b988efbb50a8d7d7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014212"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Api'lere Microsoft 365 Defender erişme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Microsoft 365 Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, iş akışlarını otomatikleştirmenize ve Microsoft 365 Defender özelliklerini tam olarak kullanmanıza yardımcı olur.

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- Azure Active Directory oluşturma
- Bu uygulamayı kullanarak bir erişim belirteci alın
- Microsoft 365 Defender API'sinde erişmek için belirteci kullanın

> [!NOTE]
> API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Bu adımları gerçekleştirin ve sonra, belirli bir bağlam kullanarak Microsoft 365 Defender API'ye erişmeye hazır oluruz.

## <a name="application-context-recommended"></a>Uygulama bağlamı (Önerilen)

Arka plan hizmetleri veya daemons gibi oturumsız kullanıcı sunumları olmadan çalıştıran uygulamalar için bu bağlamı kullanın.

1. Azure Active Directory web uygulaması oluşturun.
2. Uygulamaya istediğiniz izinleri atabilirsiniz.
3. Uygulama için bir anahtar oluşturun.
4. Uygulama ve anahtarını kullanarak bir güvenlik belirteci alın.
5. Microsoft 365 Defender API'lerine erişmek için belirteci kullanın.

Daha fazla bilgi için bkz **[. Kullanıcı olmadan postanıza Microsoft 365 Defender için uygulama oluşturma](api-create-app-web.md)**.

## <a name="user-context"></a>Kullanıcı bağlamı

Tek bir kullanıcı adına eylemler gerçekleştirmek için bu bağlamı kullanın.

1. Yerel bir Azure Active Directory oluşturun.
2. uygulamaya istediğiniz izni attayabilirsiniz.
3. Uygulamanın kullanıcı kimlik bilgilerini kullanarak bir güvenlik belirteci alın.
4. Microsoft 365 Defender API'lerine erişmek için belirteci kullanın.

Daha fazla bilgi için **[bkz. Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-user-context.md)**.

## <a name="partner-context"></a>İş ortağı bağlamı

Birden çok kiracı genelinde birçok kullanıcıya uygulama sağlamak için bu [bağlamı kullanın](/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Çok Azure Active Directory bir uygulama oluşturun.
2. uygulamaya istediğiniz izni attayabilirsiniz.
3. Her [kiracıdan](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) uygulama için yönetici izni alın.
4. Müşterinin kiracı kimliğine göre kullanıcı kimlik bilgilerini kullanarak bir güvenlik belirteci alın.
5. Microsoft 365 Defender API'lerine erişmek için belirteci kullanın.

Daha fazla bilgi için bkz **[. API'lere iş ortağı erişimi Microsoft 365 Defender oluşturma](api-partner-access.md)**.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 yetkilendirme](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Azure Anahtar Kasası ile sunucu uygulamalarınıza olan sırlarınızı yönetin](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Api'lere erişen bir 'Merhaba dünya' Microsoft 365 oluşturun](api-hello-world.md)
