---
title: Uç Nokta için Microsoft Defender'de bağlı uygulamalar
ms.reviewer: ''
description: Kimlik doğrulaması yapmak için standart OAuth 2.Uç Nokta için Microsoft Defender 0 protokolünü kullanan bağlantılı iş ortağı uygulamalarını 2.
keywords: partners, uygulamalar, üçüncü taraf, bağlantılar, sentinelone, lookout, bitdefender, corrata, morphisec, paloalto, ziften, daha iyi mobil
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
ms.openlocfilehash: 9e15103f4366d0717af9cec44d516b4b16a7160a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475575"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'de bağlı uygulamalar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Bağlı uygulamalar API'leri kullanarak Uç nokta platformu için Defender ile tümleştirilmiştir.

Uygulamalar, kimlik doğrulaması yapmak ve API'lerle kullanım için belirteç sağlamak için standart OAuth 2.0 Uç Nokta için Microsoft Defender kullanır. Buna ek Azure Active Directory, uygulama (Azure AD) uygulamaları kiracı yöneticilerinin hangi API'lere ilgili uygulama kullanılarak erişilemediklerini açıkça denetlemelerine olanak sağlar.

API'leri [bağlantılı uygulamayla](/microsoft-365/security/defender-endpoint/apis-intro) kullanmak için bu adımları izlemeniz gerekir.

Sol gezinti menüsünden Bağlı **uygulamalar'da API'leri &** İş Ortakları (Uç **noktalar altında)** > **seçin**.

## <a name="view-connected-application-details"></a>Bağlı uygulama ayrıntılarını görüntüleme

Bağlı uygulamalar sayfası, belirli uygulamalara bağlı ve Uç Nokta için Microsoft Defender Azure AD uygulamaları hakkında bilgi sağlar. Bağlı uygulamaların kullanımını gözden geçirabilirsiniz: son görülme, son 24 saat içinde istek sayısı ve son 30 gün içinde eğilim isteği.

:::image type="content" source="images/connected-apps.png" alt-text="Bağlı uygulamalar" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Bağlı uygulamayı düzenleme, yeniden yapılandırma veya silme

Uygulama **ayarlarını aç** bağlantısı, ilgili Azure AD uygulama yönetimi sayfasını uygulama sayfasında Azure portal. Aşağıdaki Azure portal, bağlı uygulamaları yönetebilir, yeniden yapılandırabilirsiniz veya silebilirsiniz.
