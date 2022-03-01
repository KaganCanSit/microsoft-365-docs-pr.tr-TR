---
title: Uç Nokta için Microsoft Defender'da API Gezgini
ms.reviewer: ''
description: API sorguları oluşturmak ve yapmak, mevcut API'ler için istekler sınamak ve göndermek için API Gezgini'ni kullanın
keywords: api, explorer, send, request, get, post,
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6e7d0e5927a85f2f3952221c294fe2387c268546
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996479"
---
# <a name="api-explorer"></a>API Gezgini

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta API Için Microsoft Defender Gezgini, çeşitli Uç Nokta API'leri için Defender'ı etkileşimli olarak incelemenizi sağlar.

API Gezgini, Uç Nokta API uç noktası için kullanılabilir Herhangi bir Defender için API sorguları oluşturmasını ve göndermesini, testsini ve göndermesini kolaylaştırır. Api Gezgini'ni kullanarak kullanıcı arabirimi üzerinden henüz mevcut olamay eylemleri gerçekleştirin veya verileri bulun.

Araç, uygulama geliştirme sırasında yararlıdır. Kullanıcı erişim ayarlarınıza saygılı API sorguları gerçekleştirmenize olanak sağlar ve erişim belirteçleri oluşturma ihtiyacını azalttır.

Bu aracı ayrıca örnek sorgular galerisini incelemek, sonuç kodu örneklerini kopyalamak ve hata ayıklama bilgileri oluşturmak için de kullanabilirsiniz.

API Gezgini'ni kullanarak şunları kullanabilirsiniz:

- Herhangi bir yöntem için istekleri çalıştırma ve yanıtları gerçek zamanlı olarak görme
- API örneklerine hızla göz atarak bunların hangi parametreleri destekle ilgili olduğunu öğrenin
- API çağrılarını kolaylıkla yapma; yönetim portalı oturum açma dışında kimlik doğrulamasına gerek yok

## <a name="access-api-explorer"></a>Access API Gezgini

Sol gezinti menüsünden API Api Gezgini **'& İş Ortakları'ı** \> **seçin**.

## <a name="supported-apis"></a>Desteklenen API'ler

API Gezgini, Uç Nokta için Defender tarafından sunulan tüm API'leri destekler.

Desteklenen API'ler listesi API'ler [belgelerinde mevcuttur](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>API Gezgini ile çalışmaya başlama

1. Sol bölmede, kullanabileceğiniz örnek isteklerin listesi vardır.
2. Bağlantıları izleyin ve Sorguyu **çalıştır'a tıklayın**.

Örneklerin bazıları URL'de bir parametre belirtmeyi gerekli kılıyor olabilir, örneğin, {machine- ID}.

## <a name="faq"></a>SSS

**API Gezgini'ni kullanmak için bir API belirtecine sahip ihtiyacım var mı?** <br>
API'ye erişmek için kimlik bilgileri gerekli değildir. API Gezgini, bir istekte her zaman Uç nokta yönetim portalı belirteci için Defender'ı kullanır.

Oturum açan kullanıcı kimlik doğrulaması kimlik bilgileri API Gezgini'nin sizin adınıza verilere erişim yetkisine sahip olduğunu doğrulamak için kullanılır.

Belirli API istekleri RBAC ayrıcalıklarınıza göre sınırlıdır. Örneğin, "Gönder göstergesi" isteği güvenlik yöneticisi rolüyle sınırlıdır.
