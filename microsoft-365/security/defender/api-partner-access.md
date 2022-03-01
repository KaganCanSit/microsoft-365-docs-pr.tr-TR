---
title: API'ler aracılığıyla Microsoft 365 Defender iş ortağı erişimi
description: Kullanıcılarınız adına e-postanıza programlı erişim Microsoft 365 Defender bir uygulamanın nasıl oluşturul öğrenin.
keywords: iş ortağı, erişim, api, çok kiracı, izin, erişim belirteci, uygulama
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
ms.openlocfilehash: 8a80245f4e94ee6f5f413154cf9b6d2ea318f5e4
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010752"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>API'lere iş ortağı erişimi Microsoft 365 Defender oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Bu sayfada, birden çok Azure Active Directory genelinde kullanıcılar adına programlı olarak erişim Microsoft 365 Defender bir Microsoft 365 Defender uygulamasının nasıl oluşturulladığı açıkmektedir. Çok kiracılı uygulamalar, büyük kullanıcı gruplarına hizmet etmek için kullanışlıdır.

Tek bir kullanıcı adına Microsoft 365 Defender programlı erişime ihtiyacınız varsa bkz. Kullanıcı adına API'lere erişmek Microsoft 365 Defender [uygulama oluşturma](api-create-app-user-context.md). Açıkça tanımlanmış bir kullanıcı olmadan (örneğin, bir arka plan uygulaması veya daemon yazıyorsanız) erişime ihtiyacınız varsa, bkz. Kullanıcı olmadan belirli bir Microsoft 365 Defender için [uygulama oluşturma](api-create-app-web.md). Ne tür erişime ihtiyacınız olduğundan emin değilsanız, bkz. [Başlama](api-access.md).

Microsoft 365 Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler iş akışlarını otomatikleştirmenize ve Microsoft 365 Defender özelliklerini kullanmanıza yardımcı olur. Bu API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, şu API'leri kullanmak için aşağıdaki adımları benimsersiniz:

- Bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- API'ye erişmek için Microsoft 365 Defender kullanın.

Bu uygulama çok kiracılı olduğu için, kullanıcıları adına her [kiracıdan yönetici](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) izni de gerekir.

Bu makalede şunların nasıl olduğu açıklanmıştır:

- Çok **kiracılı** Azure AD uygulaması oluşturma
- İhtiyaçları olan kullanıcı veya kaynaklara erişmek için kullanıcı yöneticinizden Microsoft 365 Defender izni alın.
- Erişmek için bir erişim belirteci Microsoft 365 Defender
- Belirteci doğrulama

Microsoft 365 Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, çalışma akışlarını otomatik hale Microsoft 365 Defender olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- Çok **kiracılı** bir Azure AD uygulaması oluşturun.
- Uygulamanın ihtiyaç olduğu kaynak ve kaynaklara erişmesi için kullanıcı yöneticiniz tarafından Microsoft 365 Defender (izin) alın.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- API'ye erişmek için Microsoft 365 Defender kullanın.

Çok kiracılı Bir Azure AD uygulaması oluşturma, belirteç oluşturmak ve belirteci doğrulamak için erişim belirteci elde Microsoft 365 Defender aşağıdaki adımlar size yol sunar.

## <a name="create-the-multi-tenant-app"></a>Çok kiracılı uygulamayı oluşturma

1. Genel Yönetici [rolüne](https://portal.azure.com) sahip bir kullanıcı olarak **Azure'da oturum** açın.

2. **Azure Active Directory** >  **App kayıtlarıne** **gidinYeni** >  kayıt.

   ![Kayıt Microsoft Azure gezinti görüntüsü.](../../media/atp-azure-new-app2.png)

3. Kayıt formunda:

   - Uygulamanız için bir ad seçin.
   - Desteklenen **hesap türlerinden Herhangi** bir kuruluş **dizininde (Herhangi bir Azure AD dizini) - Çok Amaçlı Hesaplar'ı seçin**.
   - Yeniden yönlendirme **URI'sini** doldurun. Web yazın **ve** yeniden yönlendirme URI'sini olarak ver **https://portal.azure.com**.

   Formu doldurmayı bitirdikten sonra, Kaydettir'i **seçin**.

   ![Uygulama kaydını oluşturma formunun resmi.](../..//media/atp-api-new-app-partner.png)

4. Uygulama sayfanız üzerinde **API permissionsAdd** >  **permissionAPIs my organization** >  uses >, **Microsoft Threat Protection yazın** ve **Microsoft Threat Protection'ı seçin**. Artık uygulama erişim izni Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Tehdit* Koruması bu güncelleştirmelerin eski Microsoft 365 Defender, özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlamalı.

   ![API izin seçimi resmi.](../../media/apis-in-my-org-tab.PNG)

5. Uygulama **izinleri'ne tıklayın**. Senaryonuz için uygun izinleri seçin (örneğin, **Olay.Okuma.All**) ve ardından İzin **ekle'yi seçin**.

   ![API erişimi ve API seçimi görüntüsü.](../../media/request-api-permissions.PNG)

    > [!NOTE]
    > Senaryo için uygun izinleri seçmeniz gerekir. *Tüm olayları okuma,* yalnızca bir örnektir. Hangi izinlere ihtiyacınız olduğunu belirlemek için lütfen çağrı **yapmak istediğiniz** API'deki İzinler bölümüne bakın.
    >
    > Örneğin, gelişmiş [sorguları çalıştırmak için](api-advanced-hunting.md) 'Gelişmiş sorguları çalıştır' iznini seçin; bir [cihazı yalıtmak](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) için "Makine ayırma" iznini seçin.

6. Yönetici **izni ver'i seçin**. Her izin ekleyseniz, geçerlik için **Yönetici izni ver'i** seçmeniz gerekir.

    ![İzin ver'in resmi.](../../media/grant-consent.PNG)

7. Uygulamaya bir sır eklemek için Sertifikalar gizli **& seçin**, gizli için bir açıklama ekleyin ve Ekle'yi **seçin**.

    > [!TIP]
    > Ekle'yi **seçin** ve **oluşturulan gizli değeri kopyalayın**. Siz ayrılarak gizli değeri geri ala zamanlarız.

    ![Uygulama anahtarı oluşturma resmi.](../../media/webapp-create-key2.png)

8. Uygulama kimliğinizi ve kiracı kimliğini güvenli bir yere kaydedin. Bunlar, uygulama sayfanıza **genel bakış** altında listelenir.

   ![Oluşturulan uygulama kimliğinin resmi.](../../media/app-and-tenant-ids.png)

9. Uygulamayı kullanıcı kiracınıza ekleyin.

   Uygulamanız kullanıcılarınız adına Microsoft 365 Defender kiracılarla etkileşime sahip olduğu için, uygulamayı kullanmayı uygun olan her kiracı için onaylanması gerekir.

   **Kullanıcınıza göre** bir Genel Yöneticinin izin bağlantısını görüntülemesi ve başvurularınızı onaylaması gerekir.

   İzin bağlantısı formun bir bağlantısıdır:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Basamaklar `00000000-0000-0000-0000-000000000000` , Uygulama Kimliği'niz ile değiştir değiştir değiştir olmalıdır.

   İzin bağlantısına tık olduktan sonra, kullanıcının kiracısı Genel Yöneticisi ile oturum açın ve uygulamayı kabul edin.

   ![İzin görüntüsü.](../../media/app-consent-partner.png)

   Ayrıca, kullanıcıdan kiracı kimliğini de istemeniz gerekir. Kiracı kimliği, erişim belirteçlerini almak için kullanılan tanımlayıcılardan biridir.

- **Bitti!** Bir uygulamayı başarıyla kaydettiysiniz!
- Belirteç edinme ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token"></a>Erişim belirteci alın

Azure AD belirteçleri hakkında daha fazla bilgi için [Azure AD öğreticisi'ne bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Bu bölümdeki örnekler, test amacıyla gizli değerler yapıştırmayı teşvik etmese de, üretimde çalışan bir  uygulamada asla gizli kodların yapıştırımama gerekir. Üçüncü bir taraf kaynaklara erişmek için sizin sırrınızı kullanabilir. Azure Anahtar Kasasını kullanarak uygulamanın sırlarını güvende [tutmanıza yardımcı olabilirsiniz](/azure/key-vault/general/about-keys-secrets-certificates). Uygulamanızı nasıl koruyabilirsiniz gibi pratik bir örnek için bkz. Azure Anahtar Kasası [ile sunucu uygulamalarınız için gizli uygulamaları yönetme](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> Aşağıdaki örneklerde, betiğin çalıştığını test etmek için kullanıcının kiracı kimliğini kullanın.

### <a name="get-an-access-token-using-powershell"></a>PowerShell kullanarak erişim belirteci alın

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place!

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"

$authBody = [Ordered] @{
    resource = $resourceAppIdUri
    client_id = $clientId
    client_secret = $appSecret
    grant_type = 'client_credentials'
}

$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token

Out-File -FilePath "./Latest-token.txt" -InputObject $token

return $token
```

### <a name="get-an-access-token-using-c"></a>C kullanarak bir erişim belirteci alın\#

> [!NOTE]
> Aşağıdaki kod Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8 ile test edilmiştir.

1. Yeni bir konsol uygulaması oluşturun.
1. [Microsoft.IdentityModel NuGet Clients.ActiveDirectory'i yükleyin](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Aşağıdaki satırı ekleyin:

    ```C#
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Aşağıdaki kodu kopyalayıp uygulamanıza yapıştırın (üç değişkeni güncelleştirmeyi unutmayın: `tenantId`, `clientId`, `appSecret`):

    ```C#
    string tenantId = ""; // Paste your directory (tenant) ID here
    string clientId = ""; // Paste your application (client) ID here
    string appSecret = ""; // Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(clientId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```

### <a name="get-an-access-token-using-python"></a>Python kullanarak bir erişim belirteci alın

```Python
import json
import urllib.request
import urllib.parse

tenantId = '' # Paste your directory (tenant) ID here
clientId = '' # Paste your application (client) ID here
appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.security.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : clientId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

### <a name="get-an-access-token-using-curl"></a>Kıvrık kullanarak bir erişim belirteci alın

> [!NOTE]
> Kıvrık, 1803 Windows 10 ve sonraki sürümlere önceden yüklenmiş olarak gelecektir. Uygulamanın diğer sürümleri Windows resmi kıvrık web sitesinden [aracı indirip yükleyin](https://curl.haxx.se/windows/).

1. Bir komut istemi açın ve CLIENT_ID Azure uygulama kimliğinize ayarlayın.
1. Azure CLIENT_SECRET sırrınızı ayarlayın.
1. Kiracı TENANT_ID için uygulamanızı kullanmak isteyen kullanıcının Azure kiracı kimliğine varsayılan Microsoft 365 Defender.
1. Aşağıdaki komutu çalıştırın:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Başarılı bir yanıt şöyle olacaktır:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Belirteci doğrulama

1. Belirteci kopyalayıp çözmek için [JSON web belirteci geçerli web sitesi JWT'ye](https://jwt.ms) yapıştırın.
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
- [Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-user-context.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Azure Anahtar Kasası ile sunucu uygulamalarınıza olan sırlarınızı yönetin](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 yetkilendirme](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
