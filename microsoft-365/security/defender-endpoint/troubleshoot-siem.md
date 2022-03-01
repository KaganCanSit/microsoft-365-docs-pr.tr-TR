---
title: Uç nokta için Microsoft Defender'da SIEM aracı tümleştirme sorunlarını giderme
description: Uç Nokta için Microsoft Defender ile SIEM araçlarını kullanırken ortaya çıkabilecek sorunları giderin.
keywords: sorun giderme, siem, istemci sırrı, gizli
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: b6ed0342183734d9b4feb1c20a6c4059b77e64d6
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010795"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>SIEM aracı tümleştirme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

SIEM araçlarınızı algılamaları alırken sorunları gidermeniz gerekiyor olabilir.

Bu sayfada, karşılaşabilirsiniz sorunları gidermeye ilişkin ayrıntılı adımlar yer sağlar.

## <a name="learn-how-to-get-a-new-client-secret"></a>Yeni bir istemci sırrı elde etmeyi öğrenin

İstemci gizlinizin süresi dolsa veya SIEM araç uygulamasını etkinleştirmişken sağlanan kopyayı yanlış yaptıysanız, yeni bir gizliye ihtiyacınız vardır.

1. [Azure yönetim portalında oturum açın](https://portal.azure.com).

2. **Azure Active Directory**’yi seçin.

3. Kiracınızı seçin.

4. Uygulama **kayıtları'ne tıklayın**. Ardından uygulamalar listesinde uygulamayı seçin.

5. **Sertifikalar ve &'ı** seçin, Yeni İstemci Sırrı'nın üzerine tıklayın, ardından bir açıklama girin ve geçerlilik süresini belirtin.

6. **Kaydet**'e tıklayın. Anahtar değeri görüntülenir.

7. Değeri kopyalayın ve güvenli bir yere kaydedin.

## <a name="error-when-getting-a-refresh-access-token"></a>Yenileme erişimi belirteci alma hatası

Tehdit zekası API'si veya SIEM araçlarını kullanırken yenileme belirteci almaya çalışırken bir hatayla karşılaşırsanız, Azure Active Directory'te ilgili uygulama için yanıt URL'si eklemeniz gerekir.

1. [Azure yönetim portalında oturum açın](https://ms.portal.azure.com).

2. **Azure Active Directory**’yi seçin.

3. Kiracınızı seçin.

4. Uygulama **Kayıtları'ne tıklayın**. Ardından uygulamalar listesinde uygulamayı seçin.

5. Aşağıdaki URL'yi ekleyin:
   - Avrupa Birliği için: `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - Birleşik Krallık için: `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - Amerika Birleşik Devletleri için:  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback`.

6. **Kaydet**'e tıklayın.

## <a name="error-while-enabling-the-siem-connector-application"></a>SIEM bağlayıcı uygulamasını etkinleştirme hatası

SIEM bağlayıcı uygulamasını etkinleştirmeye çalışırken bir hatayla karşılaşırsanız tarayıcınızın açılır pencere engelleyicisi ayarlarını kontrol edin. Özelliği etkinleştirirken yeni pencerenin açılmasını engelliyor olabilir.

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshootsiem-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [SIEM araçlarınıza algılamaları çekme](configure-siem.md)

