---
title: Uç Nokta için Microsoft Defender'de API Gezgini
ms.reviewer: ''
description: API Gezgini'ni kullanarak api sorguları oluşturun ve yapın, kullanılabilir API'ler için istekler test edin ve gönderin
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
ms.openlocfilehash: 5d3d81f878e201cd00e7286bd045caa5fb3e1625
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486805"
---
# <a name="api-explorer"></a>API Gezgini

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender API Gezgini, çeşitli Uç Nokta için Defender API'lerini etkileşimli olarak keşfetmenize yardımcı olan bir araçtır.

API Gezgini, kullanılabilir uç nokta için Defender API uç noktaları için API sorguları oluşturma ve yapma, test etme ve istek göndermeyi kolaylaştırır. Kullanıcı arabirimi aracılığıyla henüz kullanılamayabilecek eylemleri yapmak veya verileri bulmak için API Gezgini'ni kullanın.

Araç, uygulama geliştirme sırasında kullanışlıdır. Kullanıcı erişim ayarlarınıza saygı duyan API sorguları gerçekleştirmenize olanak sağlayarak erişim belirteçleri oluşturma gereksinimini azaltır.

Ayrıca aracı kullanarak örnek sorgular galerisini keşfedebilir, sonuç kodu örneklerini kopyalayabilir ve hata ayıklama bilgileri oluşturabilirsiniz.

API Gezgini ile şunları yapabilirsiniz:

- Herhangi bir yöntem için istekleri çalıştırın ve yanıtları gerçek zamanlı olarak görün.
- API örneklerine hızla göz atın ve hangi parametreleri desteklediklerini öğrenin.
- API çağrılarını kolayca yapın; yönetim portalı oturum açma işleminin ötesinde kimlik doğrulaması yapmanız gerekmez.

## <a name="access-api-explorer"></a>Access API Gezgini

Sol gezinti menüsünden **İş Ortakları & API'leri** \> **[API Gezgini'ni](https://security.microsoft.com/interoperability/api-explorer)** seçin.

## <a name="supported-apis"></a>Desteklenen API'ler

API Gezgini, Uç Nokta için Defender tarafından sunulan tüm API'leri destekler.

Desteklenen API'lerin listesi [API'ler belgelerinde](apis-intro.md) bulunabilir.

## <a name="get-started-with-the-api-explorer"></a>API Gezgini'ni kullanmaya başlama

1. Sol bölmede kullanabileceğiniz örnek isteklerin listesi vardır.
2. Bağlantıları izleyin ve **Sorguyu çalıştır'a** tıklayın.

Örneklerden bazıları URL'de bir parametre belirtmeyi gerektirebilir, örneğin, {machine- ID}.

## <a name="faq"></a>SSS

**API Gezgini'ni kullanmak için bir API belirtecim olması gerekiyor mu?** <br>
API'ye erişmek için kimlik bilgileri gerekmez. API Gezgini, her istekte bulunurken Uç Nokta için Defender yönetim portalı belirtecini kullanır.

Oturum açmış kullanıcı kimlik doğrulaması kimlik bilgileri, API Gezgini'nin sizin adınıza verilere erişim yetkisine sahip olduğunu doğrulamak için kullanılır.

Belirli API istekleri RBAC ayrıcalıklarınıza göre sınırlıdır. Örneğin, "Gösterge gönder" isteği, güvenlik yöneticisi rolüyle sınırlıdır.
