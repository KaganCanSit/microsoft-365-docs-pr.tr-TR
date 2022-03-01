---
title: API'lere Microsoft 365 Defender genel bakış
description: Microsoft 365 Defender'daki kullanılabilir API'ler hakkında bilgi Microsoft 365 Defender
keywords: api, api'ler, genel bakış, olay, olay, tehdit avı, Microsoft 365 Defender
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
ms.openlocfilehash: ec4a497fd0ee428fbc664ae064ec95f74fcdce85
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010754"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>API'lere Microsoft 365 Defender genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Microsoft 365 Defender, tümleştirmeye hazır bir platform üzerine üzerine yerleşik olarakdır.

Paylaşılan olay Microsoft 365 Defender gelişmiş av tablolarına dayalı iş akışlarını otomatikleştirmek için gelişmiş API'leri kullanın.

- **[Birleştirilmiş olay sırası](api-incident.md)** - Tam saldırı kapsamını ve etkilenen varlıkları olay API'si altında birlikte gruplamayla kritik öneme odaklanın.

- **[Ürünler arası tehdit](api-advanced-hunting.md)** avı - Birden çok koruma ürünü arasında toplanan ham verileri elelamak için kendi özel sorgularınızı oluşturarak güvenlik ekibinin kurumsal bilgilerinden faydalanın.

- **[Olay akışı API'si](streaming-api.md)** - Gerçek zamanlı olayları ve uyarıları, meydana gelen tek bir veri akışında gönderebilirsiniz.

Bu özel Microsoft 365 Defender API'lerle birlikte, diğer güvenlik ürünlerimizin her biri, benzersiz yeteneklerinin avantajından yararlanmanıza yardımcı olmak için ek API'ler de sağlıyor.[](api-articles.md)

> [!NOTE]
> Birleşik portala geçiş, Uç Nokta API'leri için Microsoft Defender'ı temel alan PowerBi panolarını etkilemez. Etkileşimli portal geçişi ne olursa olsun, var olan API'lerle çalışmaya devam edebilirsiniz.

## <a name="learn-more"></a>Daha fazla bilgi

| **API'lere nasıl erişileni anlama** |
|-|
| [API kotaları ve lisanslama hakkında bilgi edinin](api-terms.md) |
| [Api'lere Microsoft 365 Defender erişme](api-access.md) |
| **Uygulama oluşturma** |
| ['Merhaba dünya' uygulaması oluşturma](api-hello-world.md) |
| [Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-user-context.md) |
| [Kullanıcı olmadan e-Microsoft 365 Defender için uygulama oluşturma](api-create-app-web.md) |
| [Api'lere çok kiracılı iş ortağı erişimi Microsoft 365 Defender oluşturma](api-partner-access.md) |
| **Sorun giderme ve uygulamalarınızı koruma** |
| [API hata kodlarını anlama](api-error-codes.md) |
| [Azure Anahtar Kasası ile uygulamalarınız için sırlarınızı yönetin](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Kullanıcı oturum açma için OAuth 2.0 yetkilendirmesi uygulama](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
