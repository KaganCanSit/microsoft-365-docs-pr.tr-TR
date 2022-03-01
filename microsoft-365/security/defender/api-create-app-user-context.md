---
title: Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma
description: Kullanıcı adına KULLANıCı Microsoft 365 Defender API'lere erişmeyi öğrenin.
keywords: access, kullanıcı, api, uygulama, kullanıcı, erişim belirteci, belirteç adına,
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
ms.openlocfilehash: 88b1bc6c46296e3694ef53ae733955a1491b21c7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010730"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Bu sayfada, tek bir kullanıcı adına postanıza programlı erişim Microsoft 365 Defender uygulamanın nasıl oluşturularak oluşturul oluşturul diğer bir adı vardır.

Microsoft 365 Defender'a tanımlı bir kullanıcı olmadan (örneğin, bir arka plan uygulaması veya daemon yazıyorsanız) programlı erişime ihtiyacınız varsa, bkz. Kullanıcı olmadan Microsoft 365 Defender için uygulama [oluşturma](api-create-app-web.md). Birden çok kiracıya erişim sağlamanız gerekirse (örneğin, büyük bir kuruluşa veya bir grup müşteriye hizmet veriyorsanız) bkz. API'lere iş ortağı [erişimiyle Microsoft 365 Defender oluşturma](api-partner-access.md). Ne tür erişime ihtiyacınız olduğundan emin değilsanız, bkz. [Başlama](api-access.md).

Microsoft 365 Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler iş akışlarını otomatikleştirmenize ve Microsoft 365 Defender özelliklerini kullanmanıza yardımcı olur. Bu API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, şu API'leri kullanmak için aşağıdaki adımları benimsersiniz:

- Bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- API'ye erişmek için Microsoft 365 Defender kullanın.

Bu makalede şunların nasıl olduğu açıklanmıştır:

- Azure AD uygulaması oluşturma
- Erişmek için bir erişim belirteci Microsoft 365 Defender
- Belirteci doğrulama

> [!NOTE]
> Kullanıcı adına Microsoft 365 Defender API'sine erişirken doğru uygulama izinlerine ve kullanıcı izinlerine ihtiyacınız vardır.

> [!TIP]
> Portalda bir eylemi gerçekleştirme izniniz varsa, API'de eylemi gerçekleştirme izniniz vardır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. Genel Yönetici [rolüne](https://portal.azure.com) sahip bir kullanıcı olarak **Azure'da oturum** açın.

2. **Azure Active Directory** >  **App kayıtlarıne** **gidinYeni** >  kayıt.

   ![Kayıt Microsoft Azure gezinti görüntüsü.](../../media/atp-azure-new-app2.png)

3. Formda, uygulamanız için bir ad seçin ve yönlendirme URI'si için aşağıdaki bilgileri girin, sonra da Kaydol'a **tıklayın**.

   ![Uygulama oluştur penceresinin resmi.](../../media/nativeapp-create2.PNG)

   - **Uygulama türü:** Genel istemci
   - **Yeniden yönlendirme URI'si:** https://portal.azure.com

4. Uygulama sayfanız üzerinde **API permissionsAdd** >  **permissionAPIs my organization** >  uses >, **Microsoft Threat Protection yazın** ve **Microsoft Threat Protection'ı seçin**. Artık uygulama erişim izni Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Tehdit* Koruması bu güncelleştirmelerin eski Microsoft 365 Defender, özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlamalı.

   ![API izin seçimi resmi.](../../media/apis-in-my-org-tab.PNG)

   - **Temsilcili izinler'i seçin**. Senaryon için uygun izinleri seçin (örneğin **Olay.Okuma) ve** ardından İzin **ekle'yi seçin**.

   ![API erişimi ve API seçimi görüntüsü.](../../media/request-api-permissions-delegated.PNG)

    > [!NOTE]
    > Senaryo için uygun izinleri seçmeniz gerekir. *Tüm olayları okuma,* yalnızca bir örnektir. Hangi izinlere ihtiyacınız olduğunu belirlemek için lütfen çağrı **yapmak istediğiniz** API'deki İzinler bölümüne bakın.
    >
    > Örneğin, gelişmiş [sorguları çalıştırmak için](api-advanced-hunting.md) 'Gelişmiş sorguları çalıştır' iznini seçin; bir [cihazı yalıtmak](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) için "Makine ayırma" iznini seçin.

5. Yönetici **izni ver'i seçin**. Her izin ekleyseniz, geçerlik için **Yönetici izni ver'i** seçmeniz gerekir.

   ![İzin ver'in resmi.](../../media/grant-consent-delegated.PNG)

6. Uygulama kimliğinizi ve kiracı kimliğini güvenli bir yere kaydedin. Bunlar, uygulama sayfanıza **genel bakış** altında listelenir.

   ![Oluşturulan uygulama kimliğinin resmi.](../../media/app-and-tenant-ids.png)

## <a name="get-an-access-token"></a>Erişim belirteci alın

Belirteçleri kullanma hakkında Azure Active Directory için [Azure AD öğreticisi'ne bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-using-powershell"></a>PowerShell kullanarak erişim belirteci alın

```PowerShell
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps } # Install the ADAL.PS package in case it's not already present

$tenantId = '' # Paste your directory (tenant) ID here.
$clientId = '' # Paste your application (client) ID here.
$redirectUri = '' # Paste your app's redirection URI

$authority = "https://login.windows.net/$tenantId"
$resourceUrl = 'https://api.security.microsoft.com'

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip

$response.AccessToken
```

## <a name="validate-the-token"></a>Belirteci doğrulama

1. Belirteci kopyalayıp [kodu çözmek için JWT'ye](https://jwt.ms) yapıştırın.
1. Kod çözme *belirteci* içinde talep ettiği rollerin istenen izinleri içerdiğindan emin olun.

Aşağıdaki resimde, ile ve izinleri olan bir uygulamada alınan kod çözme belirteci ```Incidents.Read.All``````Incidents.ReadWrite.All``````AdvancedHunting.Read.All``` gösterebilirsiniz:

![Belirteç doğrulama resmi.](../../media/webapp-decoded-token.png)

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Microsoft 365 Defender API'sinde erişmek için belirteci kullanın

1. Kullanmak istediğiniz API'yi (olaylar veya gelişmiş avlar) seçin. Daha fazla bilgi için bkz[. Desteklenen Microsoft 365 Defender API'ler](api-supported.md).
2. Göndermektesiniz olan http isteğinde, `"Bearer" <token>`yetkilendirme üst bilginizi *, yetkilendirme* düzeninin taşıyıcı ve doğrulanmış belirtecin olduğu belirteç  olarak ayarlayın.
3. Belirteç, bir saat içinde sona erer. Bu süre boyunca aynı belirteçle birden çok istek gönderabilirsiniz.

Aşağıdaki örnekte, C# kullanan olayları listesi almak için istek **göndermenin nasıl olduğu görüntülenir**.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- ['Merhaba dünya' uygulaması oluşturma](api-hello-world.md)
- [Kullanıcı olmadan e-Microsoft 365 Defender için uygulama oluşturma](api-create-app-web.md)
- [Api'lere çok kiracılı iş ortağı erişimi Microsoft 365 Defender oluşturma](api-partner-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 yetkilendirme](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
