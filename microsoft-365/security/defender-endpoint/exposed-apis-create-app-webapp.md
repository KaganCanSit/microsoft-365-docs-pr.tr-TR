---
title: Kullanıcı olmadan Uç Nokta için Microsoft Defender erişmek için uygulama oluşturma
ms.reviewer: ''
description: Kullanıcı olmadan Uç Nokta için Microsoft Defender program aracılığıyla erişim elde etmek için bir web uygulaması tasarlamayı öğrenin.
keywords: apis, graph api, desteklenen API'ler, aktör, uyarılar, cihaz, kullanıcı, etki alanı, ip, dosya, gelişmiş avcılık, sorgu
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
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4a0387eac18152599cfd08ba75893f3eae248431
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102624"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Kullanıcı olmadan Uç Nokta için Microsoft Defender erişmek için uygulama oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, kullanıcı olmadan Uç Nokta için Defender'a programlı erişim elde etmek için bir uygulamanın nasıl oluşturulacağı açıklanır. Kullanıcı adına Uç Nokta için Defender'a programlı erişime ihtiyacınız varsa bkz. [Kullanıcı bağlamıyla erişim alma](exposed-apis-create-app-nativeapp.md). Hangi erişime ihtiyacınız olduğundan emin değilseniz bkz. [Kullanmaya başlayın](apis-intro.md).

Uç Nokta için Microsoft Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler iş akışlarını otomatikleştirmenize ve Uç Nokta için Defender özelliklerine göre yenilik yapmaya yardımcı olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:
- bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak erişim belirteci alın.
- Uç Nokta için Defender API'sine erişmek için belirteci kullanın.

Bu makalede bir Azure AD uygulaması oluşturma, Uç Nokta için Microsoft Defender erişim belirteci alma ve belirteci doğrulama açıklanmaktadır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. **Genel Yönetici** rolüne sahip bir kullanıcıyla [Azure'da](https://portal.azure.com) oturum açın.

2. **yeni kayıt Uygulama kayıtları Azure Active Directory** \>  \> gidin. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Uygulama kaydı bölmesi" lightbox="images/atp-azure-new-app2.png":::

3. Kayıt formunda, uygulamanız için bir ad seçin ve ardından **Kaydet'i** seçin.

4. Uygulamanızın Uç Nokta için Defender'a erişmesini ve **'Tüm uyarıları okuma'** izni atamasını sağlamak için uygulama sayfanızda **API İzinleri** **Kuruluşumun** > kullandığı izin \> **API'leri** \> ekle'yi seçin, **WindowsDefenderATP** yazın ve ardından **WindowsDefenderATP'yi** seçin.

   > [!NOTE]
   > *WindowsDefenderATP* özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlayın.

   :::image type="content" source="images/add-permission.png" alt-text="API izinleri bölmesi" lightbox="images/add-permission.png":::

   **Uygulama izinleri** \> **Alert.Read.All** öğesini ve ardından **İzin ekle'yi** seçin.

   :::image type="content" source="images/application-permissions.png" alt-text="Uygulama izin bilgileri bölmesi" lightbox="images/application-permissions.png":::

     İlgili izinleri seçmeniz gerekir. 'Tüm Uyarıları Oku' yalnızca bir örnektir. Örneğin:

     - [Gelişmiş sorguları çalıştırmak](run-advanced-query-api.md) için 'Gelişmiş sorguları çalıştırma' iznini seçin.
     - [Bir cihazı yalıtmak](isolate-machine.md) için 'Makineyi yalıtma' iznini seçin.
     - Hangi izne ihtiyacınız olduğunu belirlemek için çağırmak istediğiniz API'nin **İzinler** bölümüne bakın.

5. **İzin ver'i** seçin.

     > [!NOTE]
     > Her izin eklediğinizde, yeni iznin geçerli olması için **Onay ver'i** seçmeniz gerekir.

    :::image type="content" source="images/grant-consent.png" alt-text="İzin ver sayfası" lightbox="images/grant-consent.png":::

6. Uygulamaya gizli dizi eklemek için **Sertifikalar & gizli dizileri** seçin, gizli diziye bir açıklama ekleyin ve ardından **Ekle'yi** seçin.

    > [!NOTE]
    > **Ekle'yi** seçtikten sonra **oluşturulan gizli dizi değerini kopyala'yı** seçin. Ayrıldıktan sonra bu değeri alamazsınız.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="Uygulama oluştur seçeneği" lightbox="images/webapp-create-key2.png":::

7. Uygulama kimliğinizi ve kiracı kimliğinizi not edin. Uygulama sayfanızda **Genel Bakış'a** gidin ve aşağıdakileri kopyalayın.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Oluşturulan uygulama ve kiracı kimlikleri" lightbox="images/app-and-tenant-ids.png":::

8. **Yalnızca Uç Nokta için Microsoft Defender İş Ortakları için**. Uygulamanızı çok kiracılı olacak şekilde ayarlayın (onaydan sonra tüm kiracılarda kullanılabilir). Bu, üçüncü taraf uygulamalar için **gereklidir** (örneğin, birden çok müşterinin kiracısında çalıştırılması amaçlanan bir uygulama oluşturursanız). Yalnızca kiracınızda çalıştırmak istediğiniz bir hizmet oluşturursanız (örneğin, kendi kullanımınız için yalnızca kendi verilerinizle etkileşim kuracak bir uygulama oluşturursanız) bu **gerekli değildir** . Uygulamanızı çok kiracılı olarak ayarlamak için:

    - **Kimlik Doğrulaması'na** gidin ve **Yeniden Yönlendirme URI'sini** ekleyin`https://portal.azure.com`.

    - Sayfanın alt kısmındaki **Desteklenen hesap türleri'nin** altında, çok kiracılı uygulamanız için **herhangi bir kuruluş dizini uygulamasındaki hesaplar** onayını seçin.

    Uygulamanızı kullanmak istediğiniz her kiracıda onaylanması gerekir. Bunun nedeni, uygulamanızın müşteriniz adına Uç Nokta için Defender ile etkileşim kurmasıdır.

    Sizin (veya üçüncü taraf bir uygulama yazıyorsanız müşterinizin) onay bağlantısını seçip uygulamanızı onaylamanız gerekir. Onay, Active Directory'de yönetici ayrıcalıklarına sahip bir kullanıcıyla yapılmalıdır.

    Onay bağlantısı aşağıdaki gibi oluşturulur: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Burada 000000000-0000-0000-0000-0000000000000000 yerine uygulama kimliğiniz eklenir.


**Bitti!** Bir uygulamayı başarıyla kaydettiniz! Belirteç alma ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token"></a>Erişim belirteci alma

Azure AD belirteçleri hakkında daha fazla bilgi için [Azure AD öğreticisine](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds) bakın.

### <a name="use-powershell"></a>PowerShell kullanma

```powershell
# This script acquires the App Context Token and stores it in the variable $token for later use in the script.
# Paste your Tenant ID, App ID, and App Secret (App key) into the indicated quotes below.

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
$token
```

### <a name="use-c"></a>C# kullanın:

Aşağıdaki kod NuGet Microsoft.Identity.Client 3.19.8 ile test edilmiştir.

> [!IMPORTANT]
> [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) NuGet paketi ve Azure AD Kimlik Doğrulama Kitaplığı (ADAL) kullanım dışı bırakıldı. 30 Haziran 2020'den bu yana yeni özellik eklenmemiş.   Yükseltmenizi kesinlikle öneririz. Diğer ayrıntılar için [geçiş kılavuzuna](/azure/active-directory/develop/msal-migration) bakın.

1. Yeni bir konsol uygulaması oluşturun.
1. [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/) NuGet yükleyin.
1. Aşağıdakileri ekleyin:

    ```csharp
    using Microsoft.Identity.Client;
    ```

1. Aşağıdaki kodu kopyalayıp uygulamanıza yapıştırın (üç değişkeni güncelleştirmeyi unutmayın: ```tenantId, appId, appSecret```):

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 
    const string authority = https://login.microsoftonline.com;
    const string audience = https://api.securitycenter.microsoft.com;

    IConfidentialClientApplication myApp = ConfidentialClientApplicationBuilder.Create(appId).WithClientSecret(appSecret).WithAuthority($"{authority}/{tenantId}").Build();

    List<string> scopes = new List<string>() { $"{audience}/.default" };

    AuthenticationResult authResult = myApp.AcquireTokenForClient(scopes).ExecuteAsync().GetAwaiter().GetResult();

    string token = authResult.AccessToken;
    ```
### <a name="use-python"></a>Python kullanma

Bkz. [Python kullanarak belirteç alma](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Curl kullanma

> [!NOTE]
> Aşağıdaki yordamda, Windows için Curl'un bilgisayarınızda zaten yüklü olduğu varsayılır.

1. Bir komut istemi açın ve CLIENT_ID Azure uygulama kimliğiniz olarak ayarlayın.
1. CLIENT_SECRET Azure uygulama gizli dizinize ayarlayın.
1. Uç Nokta için Defender'a erişmek için uygulamanızı kullanmak isteyen müşterinin Azure kiracı kimliğine TENANT_ID ayarlayın.
1. Aşağıdaki komutu çalıştırın:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Aşağıdaki biçimde bir yanıt alırsınız:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Belirteci doğrulama

Doğru belirteci aldığınızdan emin olun:

1. Kodunu çözmek için önceki adımda aldığınız belirteci kopyalayıp [JWT'ye](https://jwt.ms) yapıştırın.

1. İstenen izinlere sahip bir 'roller' talebi aldığınızdan doğrulayın.

   Aşağıdaki görüntüde, Uç Nokta için Microsoft Defender rollerinin tümüne izinlere sahip bir uygulamadan alınan kodu çözülen belirteci görebilirsiniz:

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="Belirteç ayrıntıları bölümü" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uç Nokta için Microsoft Defender API'ye erişmek için belirteci kullanma

1. Kullanmak istediğiniz API'yi seçin. Daha fazla bilgi için bkz [. Uç Nokta API'leri için Desteklenen Defender](exposed-apis-list.md).
1. "Taşıyıcı {token}" adresine gönderdiğiniz http isteğinde yetkilendirme üst bilgisini ayarlayın (Taşıyıcı, yetkilendirme şemasıdır).
1. Belirtecin süre sonu bir saattir. Aynı belirteçle birden fazla istek gönderebilirsiniz.

Aşağıda **, C# kullanarak** uyarıların listesini almak için istek gönderme örneği verilmiştir:

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen Uç Nokta için Microsoft Defender API'leri](exposed-apis-list.md)
- [Kullanıcı adına erişim Uç Nokta için Microsoft Defender](exposed-apis-create-app-nativeapp.md)
