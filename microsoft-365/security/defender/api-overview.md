---
title: Microsoft 365 Defender API'lerine genel bakış
description: Microsoft 365 Defender'deki kullanılabilir API'ler hakkında bilgi edinin
keywords: api, apis, genel bakış, olay, olaylar, tehdit avcılığı, microsoft 365 defender
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
ms.openlocfilehash: c2a340c2ad147e32082a50e326a2e0c7e11718c2
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739615"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Microsoft 365 Defender API'lerine genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Microsoft 365 Defender, tümleştirmeye hazır bir platformun üzerine kurulmuştur.

Paylaşılan olay ve gelişmiş tehdit avcılığı tablolarını temel alan iş akışlarını otomatikleştirmek için Microsoft 365 Defender API'lerini kullanın.

- **[Birleştirilmiş olaylar kuyruğu](api-incident.md)** - Tam saldırı kapsamını ve etkilenen tüm varlıkları olay API'sinin altında birlikte gruplandırarak kritik öneme odaklanın.

- **[Ürün arası tehdit avcılığı](api-advanced-hunting.md)** - Güvenlik ekibinizin kurumsal bilgilerinden yararlanarak, birden çok koruma ürününde toplanan ham verileri ele geçirme amacıyla kendi özel sorgularınızı oluşturun.

- **[Olay akışı API'si](streaming-api.md)** - Gerçek zamanlı olayları ve uyarıları gerçekleşen tek bir veri akışında gönderin.

Bu Microsoft 365 Defender özgü API'lerle birlikte, diğer güvenlik ürünlerimizin her biri benzersiz özelliklerinden yararlanmanıza yardımcı olmak için [ek API'leri](api-articles.md) kullanıma sunar.

> [!NOTE]
> Birleşik portala geçiş, Uç Nokta için Microsoft Defender API'leri temel alan PowerBi panolarını etkilememelidir. Etkileşimli portal geçişi ne olursa olsun mevcut API'lerle çalışmaya devam edebilirsiniz.

İş akışlarını otomatikleştirmek ve uygulamaları tümleştirmek için Microsoft 365 Defender nasıl kullanabileceğinizi öğrenmek için bu kısa videoyu izleyin.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M?rel=0]

## <a name="learn-more"></a>Daha fazla bilgi

| **API'lere erişmeyi anlama** |
|-|
| [API kotaları ve lisanslama hakkında bilgi edinin](api-terms.md) |
| [Microsoft 365 Defender API'lerine erişme](api-access.md) |
| **Uygulama oluşturma** |
| ['Merhaba dünya' uygulaması oluşturma](api-hello-world.md) |
| [Kullanıcı adına Microsoft 365 Defender API'lere erişmek için uygulama oluşturma](api-create-app-user-context.md) |
| [Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-web.md) |
| [Microsoft 365 Defender API'lere çok kiracılı iş ortağı erişimine sahip bir uygulama oluşturma](api-partner-access.md) |
| **Uygulamalarınızın sorunlarını giderme ve bakımını sağlama** |
| [API hata kodlarını anlama](api-error-codes.md) |
| [Azure Key Vault ile uygulamalarınızdaki gizli dizileri yönetme](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Kullanıcı oturum açma için OAuth 2.0 yetkilendirmesi uygulama](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
