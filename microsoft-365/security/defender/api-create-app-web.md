---
title: Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturma
description: Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturmayı öğrenin.
keywords: uygulama, erişim, api, oluşturma
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
ms.openlocfilehash: 1fb5e5087d03842832e89a3982826df1e94b857c
ms.sourcegitcommit: 265a4fb38258e9428a1ecdd162dbf9afe93eb11b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2022
ms.locfileid: "65268847"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Bu sayfada, tanımlı bir kullanıcı olmadan Microsoft 365 Defender programlı erişim elde etmek için bir uygulamanın nasıl oluşturulacağı açıklanır( örneğin, bir daemon veya arka plan hizmeti oluşturuyorsanız).

Bir veya daha fazla kullanıcı adına Microsoft 365 Defender program aracılığıyla erişmeniz gerekiyorsa bkz. [Kullanıcı adına Microsoft 365 Defender API'lere erişmek için uygulama oluşturma](api-create-app-user-context.md) ve [Microsoft 365 Defender API'lere iş ortağı erişimiyle uygulama oluşturma](api-partner-access.md). Hangi tür erişime ihtiyacınız olduğundan emin değilseniz bkz. [Kullanmaya başlayın](api-access.md).

Microsoft 365 Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler iş akışlarını otomatikleştirmenize ve Microsoft 365 Defender özelliklerinden yararlanmanıza yardımcı olur. Bu API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, bu API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:

- bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak erişim belirteci alın.
- Microsoft 365 Defender API'sine erişmek için belirteci kullanın.

Bu makalede şunların nasıl yapılacağını açıklar:

- Azure AD uygulaması oluşturma
- Microsoft 365 Defender erişim belirteci alma
- Belirteci doğrulayın.

## <a name="create-an-app"></a>Uygulama oluşturma

1. **Azure'da Genel Yönetici** rolüyle kullanıcı olarak oturum açın.[](https://portal.azure.com)

2. **Azure Active Directory** >  **Uygulama kayıtları** >  **Yeni kayıt'a** gidin.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Microsoft 365 Defender portalındaki Yeni kayıt sekmesi" lightbox="../../media/atp-azure-new-app2.png":::

3. Formda, uygulamanız için bir ad seçin ve ardından **Kaydet'i** seçin.

4. Uygulama sayfanızda **API İzinleri** **EkleGerekli** **izinlerGereklilikler** >  >  kuruluşum > kullanıyor'u seçin, **Microsoft Tehdit Koruması** yazın ve **Microsoft Tehdit Koruması'yı** seçin. Uygulamanız artık Microsoft 365 Defender erişebilir.

   > [!TIP]
   > *Microsoft Tehdit Koruması*, Microsoft 365 Defender için eski bir addır ve özgün listede görünmez. Görünmesini sağlamak için metin kutusuna adını yazmaya başlamanız gerekir.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Microsoft 365 Defender portalında kuruluşun API'leri kullanım sekmesi" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. **Uygulama izinleri'ne tıklayın**. Senaryonuz için ilgili izinleri seçin (örneğin, **Incident.Read.All**) ve ardından **İzin ekle'yi** seçin.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Microsoft 365 Defender portalındaki uygulama izin bölmesi" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Senaryonuz için ilgili izinleri seçmeniz gerekir. *Tüm olayları okuma* yalnızca bir örnektir. Hangi izne ihtiyacınız olduğunu belirlemek için lütfen çağırmak istediğiniz API'nin **İzinler** bölümüne bakın.
    >
    > Örneğin, [gelişmiş sorgular çalıştırmak](api-advanced-hunting.md) için 'Gelişmiş sorguları çalıştırma' iznini seçin; [cihazı yalıtmak](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) için 'Makineyi yalıt' iznini seçin.

6. **Yönetici onayı ver'i** seçin. Her izin eklediğinizde, geçerli olması için **Yönetici onayı ver'i** seçmeniz gerekir.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Microsoft 365 Defender portalında onay vermeyle ilgili bölme" lightbox="../../media/grant-consent.PNG":::

7. Uygulamaya gizli dizi eklemek için **Sertifikalar & gizli dizileri** seçin, gizli diziye bir açıklama ekleyin ve **ardından Ekle'yi** seçin.

    > [!TIP]
    > **Ekle'yi** seçtikten sonra **oluşturulan gizli dizi değerini kopyala'yı** seçin. Ayrıldıktan sonra gizli dizi değerini alamazsınız.

    :::image type="content" source="../../media/defender-endpoint/webapp-create-key2.png" alt-text="Microsoft 365 Defender portalındaki uygulama oluştur bölmesi" lightbox="../../media/defender-endpoint/webapp-create-key2.png":::

8. Uygulama kimliğinizi ve kiracı kimliğinizi güvenli bir yere kaydedin. Bunlar uygulama sayfanızda **Genel Bakış** altında listelenir.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Microsoft 365 Defender portalındaki Genel Bakış bölmesi" lightbox="../../media/app-and-tenant-ids.png":::

9. **Yalnızca Microsoft 365 Defender İş Ortakları** için: Microsoft 365 Defender API'leri aracılığıyla iş ortağı erişimi için [bu yönergeleri izleyin](./api-partner-access.md), uygulamanızı çok kiracılı olarak ayarlayın; böylece yönetici onayı aldıktan sonra tüm kiracılarda kullanılabilir. Üçüncü taraf uygulamalar için iş ortağı erişimi **gereklidir** ; örneğin, birden çok müşterinin kiracısında çalıştırılması amaçlanan bir uygulama oluşturursanız. Yalnızca kendi kullanımınız için yalnızca kendi verilerinizle etkileşime geçebilecek bir uygulama gibi, yalnızca kiracınızda çalıştırmak istediğiniz bir hizmet oluşturursanız **gerekli değildir** . Uygulamanızı çok kiracılı olarak ayarlamak için:

    - **Kimlik Doğrulaması'na** gidin ve **Yeniden Yönlendirme URI'sini** ekleyinhttps://portal.azure.com.

    - Sayfanın alt kısmındaki **Desteklenen hesap türleri'nin** altında, çok kiracılı uygulamanız için **herhangi bir kuruluş dizini uygulamasındaki hesaplar** onayını seçin.

    Uygulamanız kullanıcılarınız adına Microsoft 365 Defender ile etkileşime geçtiğinden, kullanmak istediğiniz her kiracı için onaylanması gerekir.

    Her kiracının Active Directory genel yöneticisinin onay bağlantısını seçip uygulamanızı onaylaması gerekir.

    Onay bağlantısı aşağıdaki yapıya sahiptir:

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    Basamaklar `00000000-0000-0000-0000-000000000000` Uygulama Kimliğiniz ile değiştirilmelidir.  

**Bitti!** Bir uygulamayı başarıyla kaydettiniz! Belirteç alma ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token"></a>Erişim belirteci alma

Azure Active Directory belirteçleri hakkında daha fazla bilgi için [Azure AD öğreticisine](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds) bakın.

> [!IMPORTANT]
> Bu bölümdeki örnekler gizli dizi değerlerini test amacıyla yapıştırmanızı teşvik etse de, üretimde çalışan bir uygulamaya **gizli dizileri hiçbir zaman sabit kodlamamalısınız** . Üçüncü bir taraf, kaynaklara erişmek için gizli dizinizi kullanabilir. [Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates) kullanarak uygulamanızın gizli dizilerini güvende tutmaya yardımcı olabilirsiniz. Uygulamanızı nasıl koruyabileceğinize ilişkin pratik bir örnek için bkz. [Azure Key Vault ile sunucu uygulamalarınızda gizli dizileri yönetme](/learn/modules/manage-secrets-with-azure-key-vault/).

### <a name="get-an-access-token-using-powershell"></a>PowerShell kullanarak erişim belirteci alma

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

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

### <a name="get-an-access-token-using-c"></a>C kullanarak erişim belirteci alma\#

> [!NOTE]
> Aşağıdaki kod Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8 ile test edilmiştir.

> [!IMPORTANT]
> [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) NuGet paketi ve Azure AD Kimlik Doğrulama Kitaplığı (ADAL) kullanım dışı bırakıldı. 30 Haziran 2020'den bu yana yeni özellik eklenmemiş.   Yükseltmenizi kesinlikle öneririz. Diğer ayrıntılar için [geçiş kılavuzuna](/azure/active-directory/develop/msal-migration) bakın.

1. Yeni bir konsol uygulaması oluşturun.

1. [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet yükleyin.

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

### <a name="get-an-access-token-using-python"></a>Python kullanarak erişim belirteci alma

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

### <a name="get-an-access-token-using-curl"></a>Curl kullanarak erişim belirteci alma

> [!NOTE]
> Curl, Windows 10, sürüm 1803 ve sonraki sürümlerde önceden yüklenmiştir. Windows diğer sürümleri için aracı doğrudan [resmi curl web sitesinden](https://curl.haxx.se/windows/) indirin ve yükleyin.

1. Bir komut istemi açın ve CLIENT_ID Azure uygulama kimliğiniz olarak ayarlayın.

1. CLIENT_SECRET Azure uygulama gizli dizinize ayarlayın.

1. Microsoft 365 Defender erişmek için uygulamanızı kullanmak isteyen müşterinin Azure kiracı kimliğine TENANT_ID ayarlayın.

1. Aşağıdaki komutu çalıştırın:

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   Başarılı bir yanıt şöyle görünür:

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>Belirteci doğrulama

1. Kodu çözmek için belirteci kopyalayıp [JSON web belirteci doğrulayıcı web sitesine (JWT)](https://jwt.ms) yapıştırın.

1. Kodu çözülen belirteç içindeki *rol* talebi için istenen izinlerin bulunduğundan emin olun.

   Aşağıdaki görüntüde, , `Incidents.ReadWrite.All`ve `AdvancedHunting.Read.All` izinleriyle `Incidents.Read.All`bir uygulamadan alınan kodu çözülen belirteci görebilirsiniz:

   :::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Microsoft 365 Defender portalındaki Kod Çözme belirteci bölmesi" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Microsoft 365 Defender API'sine erişmek için belirteci kullanma

1. Kullanmak istediğiniz API'yi (olaylar veya gelişmiş avcılık) seçin. Daha fazla bilgi için bkz[. Desteklenen Microsoft 365 Defender API'leri](api-supported.md).

2. Göndermek üzere olduğunuz http isteğinde, yetkilendirme üst bilgisini `"Bearer" <token>`olarak ayarlayın, *taşıyıcı* yetkilendirme şeması ve *belirteç* doğrulanmış belirtecinizdir.

3. Belirtecin süresi bir saat içinde dolar. Bu süre boyunca aynı belirteçle birden fazla istek gönderebilirsiniz.

Aşağıdaki örnekte **, C# kullanarak** olayların listesini almak için istek gönderme işlemleri gösterilmektedir.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Microsoft 365 Defender API'lerine erişme](api-access.md)
- ['Hello world' uygulaması oluşturma](api-hello-world.md)
- [Kullanıcı adına Microsoft 365 Defender API'lere erişmek için uygulama oluşturma](api-create-app-user-context.md)
- [Microsoft 365 Defender API'lere çok kiracılı iş ortağı erişimine sahip bir uygulama oluşturma](api-partner-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Azure Key Vault ile sunucu uygulamalarınızdaki gizli dizileri yönetme](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 yetkilendirmesi](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
