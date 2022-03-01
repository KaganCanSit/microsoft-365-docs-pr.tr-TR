---
title: Kullanıcı olmadan Uç Nokta için Microsoft Defender'a erişmek için uygulama oluşturma
ms.reviewer: ''
description: Kullanıcı olmadan Uç Nokta için Microsoft Defender'a programlı erişim elde etmek için web uygulaması tasarlamayı öğrenin.
keywords: api'ler, grafik api'si, desteklenen api'ler, Actor, alerts, device, kullanıcı, etki alanı, ip, dosya, gelişmiş av, sorgu
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
ms.openlocfilehash: e32f05792b4658c7d7b42f78e88d989dfb134a78
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997129"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Kullanıcı olmadan Uç Nokta için Microsoft Defender'a erişmek için uygulama oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, kullanıcı olmadan Uç Nokta için Defender'a programlı erişim elde etmek için nasıl uygulama oluşturularak oluşturul olduğu açıkmektedir. Kullanıcı adına Uç Nokta için Defender'a programlı erişime ihtiyacınız varsa bkz [. Kullanıcı bağlamıyla erişim elde görme](exposed-apis-create-app-nativeapp.md). Hangi erişime ihtiyacınız olduğundan emin değilsanız, bkz [. Başlama](apis-intro.md).

Uç Nokta için Microsoft Defender, veri ve eylemlerinin büyük bir fazlasını bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, çalışma akışlarını otomatikleştirmenize ve Uç nokta özellikleri için Defender'a dayalı yenilikler yapmaya yardımcı olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:
- Bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- Belirteci, Uç Nokta API için Defender'a erişmek üzere kullanın.

Bu makalede Azure AD uygulaması oluşturma, Uç Nokta için Microsoft Defender'a erişim belirteci elde edin ve belirteci doğrulama açıklanmıştır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. [Genel Yönetici rolüne](https://portal.azure.com) sahip bir kullanıcıyla **Azure'da oturum** açın.

2.  \> Azure Active Directory **App kayıtları Yeni kayıt'a** \> **gidin**. 

    :::image type="content" alt-text="Kayıt Microsoft Azure gezinti görüntüsü." source="images/atp-azure-new-app2.png" lightbox="images/atp-azure-new-app2.png":::

3. Kayıt formunda, başvuru için bir ad seçin ve sonra Kaydol'a **tıklayın**.

4. Uygulamanın Uç Nokta için **Defender'a** erişmesini ve bunu "Tüm uyarıları okuma" iznini atamasını sağlamak için, uygulama sayfanıza **API** \>  \> İzinleri Ekle kuruluşumda > kullanan izin API'leri ekleyin'i seçin, **WindowsDefenderATP yazın** ve **ardından WindowsDefenderATP'yi** seçin.

   > [!NOTE]
   > *WindowsDefenderATP* özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlayabilirsiniz.

   :::image type="content" alt-text="izin ekleyin." source="images/add-permission.png" lightbox="images/add-permission.png":::

   Uygulama **izinleri** **Alert.Read.All'yi**\> seçin ve sonra İzin **ekle'yi seçin**.

   :::image type="content" alt-text="izin ve kullanılamaz." source="images/application-permissions.png" lightbox="images/application-permissions.png":::

     İlgili izinleri seçmeniz gerekir. 'Tüm Uyarıları Oku' yalnızca bir örnektir. Örneğin:

     - Gelişmiş [sorguları çalıştırmak için](run-advanced-query-api.md) 'Gelişmiş sorguları çalıştırma' iznini seçin.
     - Cihazı [yalıtmak](isolate-machine.md) için "Cihazı ayırma" iznini seçin.
     - Hangi izinlere ihtiyacınız olduğunu belirlemek için **api'de** aramakla ilgilendiğiniz İzinler bölümüne bakın.

5. İzin **ver'i seçin**.

     > [!NOTE]
     > Her izin ekley7yyken, yeni **iznin geçerliksı** için İzin ver'i seçmeniz gerekir.

    ![İzinleri verin.](images/grant-consent.png)

6. Uygulamaya bir sır eklemek için Sertifikalar gizli **& seçin**, gizli belgeye bir açıklama ekleyin ve ekle'yi **seçin**.

    > [!NOTE]
    > Ekle'yi **seçin** ve **oluşturulan gizli değeri kopyalayın**. Bu değeri, siz ayrıldıktan sonra geri alalam.

    ![Uygulama anahtarı oluşturma resmi.](images/webapp-create-key2.png)

7. Uygulama kimliğinizi ve kiracı kimliğinizi bir yere yazın. Uygulama sayfanız üzerinde Genel **Bakış'a gidin** ve aşağıdaki kopyayı kopyalayın.

   :::image type="content" alt-text="Oluşturulan uygulama kimliğinin resmi." source="images/app-and-tenant-ids.png" lightbox="images/app-and-tenant-ids.png":::

8. **Yalnızca Uç Nokta İş Ortakları için Microsoft Defender için**. Uygulamanızı çok kiracılı olacak şekilde ayarlayın (izin sonrasında tüm kiracılarda kullanılabilir). Bu **,** üçüncü taraf uygulamalar için gereklidir (örneğin, birden çok müşteri kiracısinde çalıştıracak şekilde tasarlanmış bir uygulama sanız). Yalnızca **kiracıda** çalıştırmak istediğiniz bir hizmet oluşturmanız (örneğin, kendi kullanımınız için yalnızca kendi verilerinizle etkileşimde bulunacak bir uygulama sanız) bu gerekli değildir. Uygulamalarınızı çok kiracılı olacak şekilde ayarlamak için:

    - Kimlik **Doğrulaması'ne** gidin ve Yeniden `https://portal.azure.com` Yönlendirme **URI'si olarak ekleyin**.

    - Sayfanın en altında, Desteklenen hesap türleri **altında**, Çok kiracılı uygulamanız için herhangi bir kuruluş **dizininde** bulunan hesaplar'ı seçin.

    Başvurunun, kullanmayı uygun olduğu her kiracıda onaylanması gerekir. Bunun nedeni, uygulamanın müşteri adına Uç Nokta için Defender ile etkileşim kurmasıdır.

    Sizin (veya üçüncü taraf bir uygulama yazıyorsanız müşterinizin) izin bağlantısını seçmeniz ve uygulamanızı onaylamanız gerekir. İzin, Active Directory'de yönetici ayrıcalıklarına sahip bir kullanıcıyla yapılabilir.

    İzin bağlantısı aşağıdaki gibi oluşturulur: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Burada 00000000-0000-0000-00000000000 yerine uygulama kimliğinizi girin.


**Bitti!** Bir uygulamayı başarıyla kaydettiysiniz! Belirteç edinme ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token"></a>Erişim belirteci alın

Azure AD belirteçleri hakkında daha fazla bilgi için [Azure AD öğreticisi'ne bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

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
```

### <a name="use-c"></a>Use C#:

Aşağıdaki kod Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8 NuGet ile test edilmiştir.

1. Yeni bir konsol uygulaması oluşturun.
1. [Microsoft.IdentityModel NuGet Clients.ActiveDirectory'i yükleyin](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Şunları ekleyin:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Uygulamanıza aşağıdaki kodu kopyalayıp yapıştırın (üç değişkeni güncelleştirmeyi unutmayın: ```tenantId, appId, appSecret```):

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.microsoftonline.com";
    const string wdatpResourceId = "https://api.securitycenter.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```


### <a name="use-python"></a>Python'i kullanma

Bkz [. Python kullanarak belirteç almak](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Kıvrık'i kullanın

> [!NOTE]
> Aşağıdaki yordamda, bilgisayarınızda Windows için Kıvrık Kıvrık'ın zaten yüklü olduğu varsayıldı.

1. Bir komut istemi açın ve CLIENT_ID Azure uygulama kimliğinize ayarlayın.
1. Azure CLIENT_SECRET sırrınızı ayarlayın.
1. Diğer TENANT_ID uç nokta için Defender'a erişmek üzere uygulamanızı kullanmak isteyen müşterinin Azure kiracı kimliğine ayarlayın.
1. Aşağıdaki komutu çalıştırın:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Aşağıdaki formda bir yanıt alırsiniz:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Belirteci doğrulama

Doğru belirteci almak için:

1. Bir önceki adımda sahip olduğunuz belirteci kopyalayıp [çözmek için JWT'ye](https://jwt.ms) yapıştırın.

1. İstenen izinlerle bir 'roller' talebi alanın.

   Aşağıdaki resimde, uç nokta rolleri için tüm Microsoft Defender izinleri olan bir uygulamada alınan kod çözme belirteci gösterebilirsiniz:

   :::image type="content" alt-text="Belirteç doğrulama resmi." source="images/webapp-decoded-token.png" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Belirteci, Uç Nokta API'si için Microsoft Defender'a erişmek için kullanma

1. Kullanmak istediğiniz API'yi seçin. Daha fazla bilgi için bkz [. Uç Nokta API'leri için Desteklenen Defender](exposed-apis-list.md).
1. "Taşıyıcı {token}" adresine göndermek istediğiniz http isteğinde yetkilendirme üst bilgilerini ayarlayın (Taşıyıcı, yetkilendirme düzenidir).
1. Belirtecin son kullanma süresi bir saattir. Aynı belirteçle birden çok istek göndersiniz.

Aşağıda, C# kullanarak uyarıların listesini almak için bir istek **gönderme örneği ve almaktadır:**

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>Ayrıca bkz.
- [Uç Nokta API'leri için desteklenen Microsoft Defender](exposed-apis-list.md)
- [Kullanıcı adına Uç Nokta için Microsoft Defender'a Erişme](exposed-apis-create-app-nativeapp.md)
