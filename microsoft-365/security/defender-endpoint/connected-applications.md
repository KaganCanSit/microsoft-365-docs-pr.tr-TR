---
title: Uç Nokta için Microsoft Defender'daki bağlı uygulamalar
ms.reviewer: ''
description: Standart OAuth 2.0 protokolünü kullanan ve Uç nokta API'leri için Microsoft Defender ile kullanmak üzere belirteçler sağlayan bağlı iş ortağı uygulamalarını görüntüye alın.
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
ms.openlocfilehash: 4dd630dd2b35c2fedc0340cd873ff065b2685b41
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996503"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'daki bağlı uygulamalar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Bağlı uygulamalar API'leri kullanarak Uç nokta platformu için Defender ile tümleştirilmiştir.

Uygulamalar, uç nokta API'leri için Microsoft Defender'da kimlik doğrulaması yapmak ve belirteç sağlamak için standart OAuth 2.0 protokolünü kullanır. Buna ek Azure Active Directory, uygulama (Azure AD) uygulamaları kiracı yöneticilerinin hangi API'lere ilgili uygulama kullanılarak erişilemediklerini açıkça denetlemelerine olanak sağlar.

API'leri [bağlantılı uygulamayla](/microsoft-365/security/defender-endpoint/apis-intro) kullanmak için bu adımları izlemeniz gerekir.

Sol gezinti menüsünden Bağlı **uygulamalar'da API'leri &** İş Ortakları (Uç **noktalar altında)** > **seçin**.

## <a name="view-connected-application-details"></a>Bağlı uygulama ayrıntılarını görüntüleme

Bağlı uygulamalar sayfası, kurumda Uç Nokta için Microsoft Defender'a bağlı Azure AD uygulamaları hakkında bilgi sağlar. Bağlı uygulamaların kullanımını gözden geçirabilirsiniz: son görülme, son 24 saat içinde istek sayısı ve son 30 gün içinde eğilim isteği.

![Bağlı uygulamaların resmi.](images/connected-apps.png)
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Bağlı uygulamayı düzenleme, yeniden yapılandırma veya silme

Uygulama **ayarlarını aç bağlantısı** , Azure portalda ilgili Azure AD uygulama yönetimi sayfasını açar. Azure portaldan izinleri yönetebilir, yeniden yapılandırabilirsiniz veya bağlı uygulamaları silebilirsiniz.
