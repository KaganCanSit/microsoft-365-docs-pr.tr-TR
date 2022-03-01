---
title: Kullanıcı olmadan Uç Nokta için Microsoft Defender'a erişmek için Uygulama oluşturma
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
ms.openlocfilehash: 2705eb4e3010a06c707ad071a907da90dc0ec1fc
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998175"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Uç Nokta API'leri için Microsoft Defender üzerinden iş ortağı erişimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, müşterileriniz adına Uç Azure Active Directory için Microsoft Defender'a programlı erişim elde etmek için nasıl Bir Azure Active Directory (Azure AD) uygulaması oluştur oluşturmanız anlatmaktadır.

Uç Nokta için Microsoft Defender, veri ve eylemlerinin büyük bir fazlasını bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, çalışma akışlarını otomatikleştirmenize ve Uç nokta özellikleri için Microsoft Defender'a dayalı yenilikler yapmaya yardımcı olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- Çok **kiracılı** bir Azure AD uygulaması oluşturun.
- İhtiyaçları olan Uç nokta kaynakları için Defender'a erişmek için müşteri yöneticiniz tarafından yetki (izin) alın.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- Belirteci, Uç Nokta API'si için Microsoft Defender'a erişmek üzere kullanın.

Aşağıdaki adımlar, Azure AD uygulaması oluşturma, Uç Nokta için Microsoft Defender için Microsoft Defender'a erişim belirteci elde edin ve belirteci doğrulama hakkında size yol sunar.

## <a name="create-the-multi-tenant-app"></a>Çok kiracılı uygulamayı oluşturma

1. Genel Yönetici rolüne [sahip bir](https://portal.azure.com) kullanıcıyla Azure **kiracısında oturum** açın.

2.  \> Azure Active Directory **App kayıtları Yeni kayıt'a** \> **gidin**.

   ![Kayıt Microsoft Azure gezinti görüntüsü.](images/atp-azure-new-app2.png)

3. Kayıt formunda:

   - Uygulamanız için bir ad seçin.

   - Desteklenen hesap türleri - herhangi bir kuruluş dizininde yer alan hesaplar.

   - Yeniden yönlendirme URI'sini - tür: Web, URI: https://portal.azure.com

   ![İş ortağı Microsoft Azure kaydı görüntüsü.](images/atp-api-new-app-partner.png)

4. Uygulamanın Uç Nokta için Microsoft Defender'a erişmesine ve tümleştirmeyi tamamlamak için gereken en az izin kümesiyle bunu atamasına izin verin.

   - Uygulama sayfanız üzerinde **API** \>  \> İzinleri Ekle İzin API'leri Kuruluşumda şu API'leri kullanır> **WindowsDefenderATP** yazın ve **WindowsDefenderATP'de öğesini seçin**.

   - **Not**: *WindowsDefenderATP* özgün listede görünmüyor. Görünmesini görmek için metin kutusuna adını yazmaya başlayabilirsiniz.

     ![izin ekleyin.](images/add-permission.png)

### <a name="request-api-permissions"></a>API izinleri isteği

Hangi izinlere ihtiyacınız olduğunu belirlemek için **aramakla** ilgilendiğiniz API'deki İzinler bölümünü gözden geçirebilirsiniz. Örneğin:

- Gelişmiş [sorguları çalıştırmak için '](run-advanced-query-api.md)Gelişmiş sorguları çalıştırma' iznini seçin
- Cihazı [yalıtmak](isolate-machine.md) için "Makine ayırma" iznini seçin

Aşağıdaki örnekte 'Tüm uyarıları **okuma' iznini kullanılacaktır** :

1. Uygulama **izinleri** **Alert.Read.All** \> > **Ekle'yi seçin**

   ![izinlerini seçin.](images/application-permissions.png)

2. İzin **ver'i seçin**

   - **Not**: Her izin eklemeye devam etmek için yeni **izin** ver'i seçmeniz gerekir.

   ![İzin ver'in resmi.](images/grant-consent.png)

3. Uygulamaya bir gizli ekleyin.

   - **Sertifikalar gizli & seçin**, gizliye açıklama ekleyin ve Ekle'yi **seçin**.

    **Önemli**: Ekle'ye **tıklayıp oluşturulan gizli değeri kopyalayın**. İşten ayrıldıktan sonra geri ala zaman kazanaaasiniz!

    ![Uygulama anahtarı oluşturma resmi.](images/webapp-create-key2.png)

4. Uygulama kimliğinizi bir yere yazın:

   - Uygulama sayfanız üzerinde Genel **Bakış'a** gidin ve aşağıdaki bilgileri kopyalayın:

   ![Oluşturulan uygulama kimliğinin resmi.](images/app-id.png)

5. Uygulamayı müşterinizin kiracısına ekleyin.

   Başvurunun, kullanmayı uygun olduğu her müşteri kiracısı içinde onaylanması gerekir. Bunun nedeni, uygulamanın müşteri adına Uç Nokta için Microsoft Defender uygulamasıyla etkileşim kurmasıdır.

   Müşterinizin **kiracısına Genel** Yönetici izni olan bir kullanıcının izin bağlantısını seçmesi ve başvurularınızı onaylaması gerekir.

   İzin bağlantısı formun bir bağlantısıdır:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Burada 00000000-0000-0000-00000000000 Yerine Uygulama Kimliği'niz gerekir

   İzin bağlantısına tık olduktan sonra, müşterinin kiracısı Genel Yöneticisi ile oturum açın ve uygulamayı kabul edin.

   ![İzin görüntüsü.](images/app-consent-partner.png)

   Buna ek olarak, müşteriden kiracı kimliğini istemeniz ve belirteci alırken daha sonra kullanmak üzere kaydetmeniz gerekir.

6. **Bitti!** Bir uygulamayı başarıyla kaydettiysiniz! Belirteç edinme ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token-example"></a>Erişim belirteci örneği alın

**Not:** Müşteriniz adına erişim belirteci almak için, müşterinin kiracı kimliğini aşağıdaki belirteç alımında kullanın.

Belirteç hakkında daha fazla AAD için [öğreticiye AAD bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>PowerShell'i kullanma

```powershell
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

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
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### <a name="using-c"></a>C'yi kullanma #

> Aşağıdaki kod Nuget Microsoft.IdentityModel.Clients.ActiveDirectory ile test edilmiştir

- Yeni bir Konsol Uygulaması oluşturma
- [Microsoft.IdentityModel.Clients.ActiveDirectory'NuGet yükleme](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- Aşağıdakini kullanarak ekleyin:

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- Uygulamanıza aşağıdaki kodu kopyalayın/yapıştırın (üç değişkeni güncelleştirmeyi unutmayın: `tenantId`, ve `appId``appSecret`)

    ```console
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

### <a name="using-python"></a>Python'ı kullanma

Python kullanarak [belirteç al'a başvuru](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Kıvrık'ı kullanma

> [!NOTE]
> Aşağıdaki yordam(Bilgisayarınızda Windows için Kıvrık'ın zaten yüklü olması gerekir)

- Komut penceresini açma
- Azure CLIENT_ID kimliğine kimlik ayarlama
- Azure CLIENT_SECRET sırrınızı ayarlama
- Varsayılan TENANT_ID uç nokta için Microsoft Defender uygulamasına erişmek isteyen müşterinin Azure kiracı kimliğine ayarlama
- Aşağıdaki komutu çalıştırın:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Formun yanıtını alırsiniz:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Belirteci doğrulama

Doğru belirtece sahip olup olmadığınız emin olmak için Sanity check:

- Kodunu çözmek için önceki adımda edinilen belirteci [JWT'ye](https://jwt.ms) kopyalama/yapıştırma
- İstenen izinlerle bir 'roller' talebi alasınız
- Aşağıdaki ekran görüntüsünde, Uç Nokta için Microsoft Defender'a birden çok izni olan bir Uygulamadan alınan kod çözme belirteci görebilirsiniz:
- "Kimlik" talebi, belirtecin ait olduğu kiracı kimliğidir.

![Belirteç doğrulama resmi.](images/webapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Belirteci, Uç Nokta API'si için Microsoft Defender'a erişmek için kullanma

- Kullanmak istediğiniz API'yi seçin, daha fazla bilgi için bkz. Uç Nokta [API'leri için desteklenen Microsoft Defender](exposed-apis-list.md)
- "Taşıyıcı {token}" adresine göndermek istediğiniz Http isteğinde Yetkilendirme üst bilgilerini ayarlayın (Taşıyıcı, Yetkilendirme düzenidir)
- Belirtecin son kullanma süresi 1 saattir (aynı belirteçe sahip birden fazla istek gönderabilirsiniz)

- C# kullanarak uyarı listesini almak için istek **gönderme örneği**

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
