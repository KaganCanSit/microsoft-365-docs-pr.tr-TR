---
title: Kullanıcı olmadan e-Uç Nokta için Microsoft Defender erişmek için Uygulama oluşturma
ms.reviewer: ''
description: Kullanıcı olmadan web uygulamasına programlı erişim elde etmek için web Uç Nokta için Microsoft Defender tasarlamayı öğrenin.
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
ms.openlocfilehash: 454d385c66a0019ba6059a2b8038907dd630b443
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469877"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>API'ler aracılığıyla Uç Nokta için Microsoft Defender iş ortağı erişimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, müşterileriniz adına Azure Active Directory programlı erişim elde etmek için Uç Nokta için Microsoft Defender (Azure AD) uygulaması oluşturma hakkında bilgi bulabilirsiniz.

Uç Nokta için Microsoft Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, çalışma akışlarını otomatikleştirmenize ve farklı özelliklere Uç Nokta için Microsoft Defender yardımcı olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- Çok **kiracılı** bir Azure AD uygulaması oluşturun.
- İhtiyaçları olan Uç nokta kaynakları için Defender'a erişmek için müşteri yöneticiniz tarafından yetki (izin) alın.
- Bu uygulamayı kullanarak bir erişim belirteci alın.
- API'ye erişmek için Uç Nokta için Microsoft Defender kullanın.

Aşağıdaki adımlar, Azure AD uygulaması oluşturma, belirteç oluşturmak ve belirteç doğrulamak için bir erişim belirteci Uç Nokta için Microsoft Defender için size yol sağlar.

## <a name="create-the-multi-tenant-app"></a>Çok kiracılı uygulamayı oluşturma

1. Genel Yönetici rolüne [sahip bir](https://portal.azure.com) kullanıcıyla Azure **kiracısında oturum** açın.

2. Yeni kayıt **Azure Active Directory** \> **Uygulama kayıtları** \> **gidin**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Uygulama kayıt bölmesine gezinti" lightbox="images/atp-azure-new-app2.png":::

3. Kayıt formunda:

   - Uygulamanız için bir ad seçin.

   - Desteklenen hesap türleri - herhangi bir kuruluş dizininde yer alan hesaplar.

   - Yeniden yönlendirme URI'sini - tür: Web, URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="İş Microsoft Azure başvuru kayıt sayfası" lightbox="images/atp-api-new-app-partner.png":::

4. Uygulamanıza erişim izni Uç Nokta için Microsoft Defender ve tümleştirmeyi tamamlamak için gereken en düşük izin kümesiyle bunu attayabilirsiniz.

   - Uygulama sayfanız üzerinde **API** \>  \> İzinleri Ekle İzin API'leri Kuruluşumda şu API'leri kullanır> **WindowsDefenderATP** yazın ve **WindowsDefenderATP'de öğesini seçin**.

   - **Not**: *WindowsDefenderATP* özgün listede görünmüyor. Görünmesini görmek için metin kutusuna adını yazmaya başlayabilirsiniz.

     :::image type="content" source="images/add-permission.png" alt-text="İzin ekle seçeneği" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>API izinleri isteği

Hangi izinlere ihtiyacınız olduğunu belirlemek için **aramakla** ilgilendiğiniz API'deki İzinler bölümünü gözden geçirebilirsiniz. Örneğin:

- Gelişmiş [sorguları çalıştırmak için '](run-advanced-query-api.md)Gelişmiş sorguları çalıştırma' iznini seçin
- Cihazı [yalıtmak](isolate-machine.md) için "Makine ayırma" iznini seçin

Aşağıdaki örnekte 'Tüm uyarıları **okuma' iznini kullanılacaktır** :

1. Uygulama **izinleri** **Alert.Read.All** \> > **Ekle'yi seçin**

   :::image type="content" source="images/application-permissions.png" alt-text="İzin eklemeye izin veren seçenek" lightbox="images/application-permissions.png":::

2. İzin **ver'i seçin**

   - **Not**: Her izin eklemeye devam etmek için yeni **izin** ver'i seçmeniz gerekir.

   :::image type="content" source="images/grant-consent.png" alt-text="İzin verilmesine izin veren seçenek" lightbox="images/grant-consent.png":::

3. Uygulamaya bir gizli ekleyin.

   - **Sertifikalar gizli & seçin**, gizliye açıklama ekleyin ve Ekle'yi **seçin**.

    **Önemli**: Ekle'ye **tıklayıp oluşturulan gizli değeri kopyalayın**. İşten ayrıldıktan sonra geri ala zaman kazanaaasiniz!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Uygulama oluştur anahtarı" lightbox="images/webapp-create-key2.png":::

4. Uygulama kimliğinizi bir yere yazın:

   - Uygulama sayfanız üzerinde Genel **Bakış'a** gidin ve aşağıdaki bilgileri kopyalayın:

     :::image type="content" source="images/app-id.png" alt-text="Uygulamanın kimliğini oluşturma" lightbox="images/app-id.png":::

5. Uygulamayı müşterinizin kiracısına ekleyin.

   Başvurunun, kullanmayı uygun olduğu her müşteri kiracısı içinde onaylanması gerekir. Bunun nedeni, uygulamanın müşteri adına Uç Nokta için Microsoft Defender uygulamayla etkileşim kurmasıdır.

   Müşterinizin **kiracısına Genel** Yönetici izni olan bir kullanıcının izin bağlantısını seçmesi ve başvurularınızı onaylaması gerekir.

   İzin bağlantısı formun bir bağlantısıdır:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Burada 00000000-0000-0000-00000000000 Yerine Uygulama Kimliği'niz gerekir

   İzin bağlantısına tık olduktan sonra, müşterinin kiracısı Genel Yöneticisi ile oturum açın ve uygulamayı kabul edin.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Kabul Et düğmesi" lightbox="images/app-consent-partner.png":::

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
- Müşteri TENANT_ID erişmek için başvurularınızı kullanmak isteyen müşterinin Azure kiracı kimliğine Uç Nokta için Microsoft Defender ayarlayın
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
- Aşağıdaki ekran görüntüsünde, kod çözme izni birden çok izine sahip bir Uygulamadan alınan kod çözme belirteci Uç Nokta için Microsoft Defender:
- "Kimlik" talebi, belirtecin ait olduğu kiracı kimliğidir.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Belirteç doğrulama sayfası" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>API'ye erişmek için Uç Nokta için Microsoft Defender kullanma

- Kullanmak istediğiniz API'yi seçin, daha fazla bilgi için desteklenen [API'ler Uç Nokta için Microsoft Defender bakın](exposed-apis-list.md)
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

- [Desteklenen Uç Nokta için Microsoft Defender API'ler](exposed-apis-list.md)
- [Kullanıcı Uç Nokta için Microsoft Defender adına erişim bilgilerine erişme](exposed-apis-create-app-nativeapp.md)
