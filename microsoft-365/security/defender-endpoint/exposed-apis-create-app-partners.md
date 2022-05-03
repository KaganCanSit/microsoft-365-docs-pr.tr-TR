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
ms.openlocfilehash: fde2cc894fb989628f9e2e0d9d7297bdb3c9e9da
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172403"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Uç Nokta için Microsoft Defender API'leri aracılığıyla iş ortağı erişimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, müşterileriniz adına Uç Nokta için Microsoft Defender program aracılığıyla erişim elde etmek için bir Azure Active Directory (Azure AD) uygulamasının nasıl oluşturulacağı açıklanır.

Uç Nokta için Microsoft Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler, iş akışlarını otomatikleştirmenize ve Uç Nokta için Microsoft Defender özelliklerine göre yenilik oluşturmanıza yardımcı olur. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:

- **Çok kiracılı** bir Azure AD uygulaması oluşturun.
- Uygulamanızın ihtiyaç duyduğu Uç Nokta için Defender kaynaklarına erişmesi için müşteri yöneticinizden yetki (onay) alın.
- Bu uygulamayı kullanarak erişim belirteci alın.
- Uç Nokta için Microsoft Defender API'ye erişmek için belirteci kullanın.

Aşağıdaki adımlar bir Azure AD uygulaması oluşturma, Uç Nokta için Microsoft Defender için erişim belirteci alma ve belirteci doğrulama konusunda size yol gösterir.

## <a name="create-the-multi-tenant-app"></a>Çok kiracılı uygulamayı oluşturma

1. **Genel Yönetici** rolüne sahip kullanıcıyla [Azure kiracınızda](https://portal.azure.com) oturum açın.

2. **yeni kayıt Uygulama kayıtları Azure Active Directory** \>  \> gidin.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Uygulama kaydı bölmesine gezinti" lightbox="images/atp-azure-new-app2.png":::

3. Kayıt formunda:

   - Uygulamanız için bir ad seçin.

   - Desteklenen hesap türleri - herhangi bir kuruluş dizinindeki hesaplar.

   - Yeniden yönlendirme URI'si - tür: Web, URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Microsoft Azure iş ortağı uygulama kaydı sayfası" lightbox="images/atp-api-new-app-partner.png":::

4. Uygulamanızın Uç Nokta için Microsoft Defender erişmesine izin verin ve tümleştirmeyi tamamlamak için gereken en düşük izin kümesiyle uygulamayı atayın.

   - Uygulama sayfanızda **API İzinleri** **Kuruluşumun kullandığı** **izin** \> API'leri \> ekle'yi seçin > **WindowsDefenderATP** yazın ve **WindowsDefenderATP'yi** seçin.

   - **Not**: *WindowsDefenderATP* özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlayın.

     :::image type="content" source="images/add-permission.png" alt-text="İzin ekle seçeneği" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>API izinleri isteme

Hangi izne ihtiyacınız olduğunu belirlemek için çağırmak istediğiniz API'deki **İzinler** bölümünü gözden geçirin. Örneğin:

- [Gelişmiş sorguları çalıştırmak](run-advanced-query-api.md) için 'Gelişmiş sorgu çalıştır' iznini seçin
- [Cihazı yalıtmak](isolate-machine.md) için 'Makineyi yalıt' iznini seçin

Aşağıdaki örnekte **'Tüm uyarıları oku'** iznini kullanacağız:

1. **Uygulama izinleri** \> **Alert.Read.All** > **İzin ekle'yi** seçin

   :::image type="content" source="images/application-permissions.png" alt-text="İzin eklemeye izin veren seçenek" lightbox="images/application-permissions.png":::

2. **İzin ver'i** seçin

   - **Not**: İzin eklediğinizde, yeni iznin geçerli olması için **Onay ver'i** seçmeniz gerekir.

   :::image type="content" source="images/grant-consent.png" alt-text="Onay verilmesine izin veren seçenek" lightbox="images/grant-consent.png":::

3. Uygulamaya gizli dizi ekleyin.

   - **Sertifikalar & gizli diziler'i** seçin, gizli diziye açıklama ekleyin ve **Ekle'yi** seçin.

    **Önemli**: Ekle'ye tıkladıktan sonra **oluşturulan gizli dizi değerini kopyalayın**. Gittikten sonra geri alamazsınız!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Uygulama oluşturma anahtarı" lightbox="images/webapp-create-key2.png":::

4. Uygulama kimliğinizi not edin:

   - Uygulama sayfanızda **Genel Bakış'a** gidin ve aşağıdaki bilgileri kopyalayın:

     :::image type="content" source="images/app-id.png" alt-text="Oluşturma uygulamasının kimliği" lightbox="images/app-id.png":::

5. Uygulamayı müşterinizin kiracısına ekleyin.

   Uygulamanızı kullanmak istediğiniz her müşteri kiracısında onaylanması gerekir. Bunun nedeni uygulamanızın müşteriniz adına Uç Nokta için Microsoft Defender uygulamayla etkileşim kurmasıdır.

   Müşterinizin kiracısından **Genel Yöneticiye** sahip bir kullanıcının onay bağlantısını seçip uygulamanızı onaylaması gerekir.

   Onay bağlantısı şu biçimdedir:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Burada 000000000-0000-0000-0000-0000000000000000 yerine Uygulama Kimliğiniz kullanılmalıdır

   Onay bağlantısına tıkladıktan sonra müşterinin kiracısının Genel Yöneticisi ile oturum açın ve uygulamayı onaylayın.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Kabul Et düğmesi" lightbox="images/app-consent-partner.png":::

   Ayrıca, müşterinizden kiracı kimliğini istemeniz ve belirteci alırken gelecekte kullanmak üzere kaydetmeniz gerekir.

6. **Bitti!** Bir uygulamayı başarıyla kaydettiniz! Belirteç alma ve doğrulama için aşağıdaki örneklere bakın.

## <a name="get-an-access-token-example"></a>Erişim belirteci örneği alma

**Not:** Müşteriniz adına erişim belirteci almak için aşağıdaki belirteç alımlarında müşterinin kiracı kimliğini kullanın.

AAD belirteci hakkında daha fazla bilgi için bkz. [AAD öğreticisi](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>PowerShell kullanma

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

### <a name="using-c"></a>C kullanma #

> Aşağıdaki kod Nuget Microsoft.IdentityModel.Clients.ActiveDirectory ile test edilmiştir

- Yeni konsol uygulaması oluşturma
- [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet yükleme
- Kullanarak aşağıdakini ekleyin

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- Uygulamanıza aşağıdaki kodu kopyalayın/yapıştırın (üç değişkeni güncelleştirmeyi unutmayın: `tenantId`, `appId`ve `appSecret`)

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

### <a name="using-python"></a>Python kullanma

[Python kullanarak belirteç alma](run-advanced-query-sample-python.md#get-token) bölümüne bakın

### <a name="using-curl"></a>Curl kullanma

> [!NOTE]
> Windows için Curl'in bilgisayarınızda zaten yüklü olduğu varsayılan aşağıdaki yordam

- Komut penceresi açma
- azure uygulama kimliğinize CLIENT_ID ayarlama
- azure uygulama gizli dizinize CLIENT_SECRET ayarlama
- TENANT_ID, uygulamanızı kullanarak Uç Nokta için Microsoft Defender uygulamasına erişmek isteyen müşterinin Azure kiracı kimliğine ayarlayın
- Aşağıdaki komutu çalıştırın:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Formun yanıtını alırsınız:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Belirteci doğrulama

Doğru belirteci kullandığınızdan emin olmak için akıl sağlığı denetimi:

- Kodunu çözmek için önceki adımda aldığınız belirteci [JWT'ye](https://jwt.ms) kopyalayın/yapıştırın
- İstenen izinlerle 'roller' talebi aldığınızdan doğrulama
- Aşağıdaki ekran görüntüsünde, Uç Nokta için Microsoft Defender için birden çok izne sahip bir Uygulamadan alınan kodu çözülen belirteci görebilirsiniz:
- "tid" talebi, belirtecin ait olduğu kiracı kimliğidir.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Belirteç doğrulama sayfası" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uç Nokta için Microsoft Defender API'ye erişmek için belirteci kullanma

- Kullanmak istediğiniz API'yi seçin. Daha fazla bilgi için bkz[. Desteklenen Uç Nokta için Microsoft Defender API'leri](exposed-apis-list.md)
- "Taşıyıcı {token}" adresine gönderdiğiniz Http isteğinde Yetkilendirme üst bilgisini ayarlayın (Taşıyıcı, Yetkilendirme şemasıdır)
- Belirtecin Süre sonu süresi 1 saattir (aynı belirteçle birden fazla istek gönderebilirsiniz)

- **C# kullanarak** uyarıların listesini almak için istek gönderme örneği

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
