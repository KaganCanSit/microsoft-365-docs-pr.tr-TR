---
title: API'Uç Nokta için Microsoft Defender kullanma
ms.reviewer: ''
description: Kullanıcı olmadan yerel Windows program erişimi elde etmek için yerel Uç Nokta için Microsoft Defender tasarlamayı öğrenin.
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
ms.openlocfilehash: 752e08d3fddb28b7d30122281009e54fc235b129
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471219"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>API'Uç Nokta için Microsoft Defender kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, bir kullanıcı adına Uç Nokta için Defender'a programlı erişim elde etmek için nasıl uygulama oluşturularak oluşturul olduğu açıkmektedir.

Kullanıcı olmadan programlı erişime Uç Nokta için Microsoft Defender, Access'e başvuru Uç Nokta için Microsoft Defender [bağlamsal olarak bağlama bakın](exposed-apis-create-app-webapp.md).

Hangi erişime ihtiyacınız olduğundan emin değilsanız, Giriş [sayfasını okuyun](apis-intro.md).

Uç Nokta için Microsoft Defender çok büyük bir veri ve eylemlerini bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, çalışma akışlarını otomatik hale Uç Nokta için Microsoft Defender olanak sağlar. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için [bkz. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genelde API'leri kullanmak için aşağıdaki adımları atabilirsiniz:

- AAD oluşturma
- Bu uygulamayı kullanarak bir erişim belirteci alın
- Belirteci, Uç Nokta API'si için Defender'a erişmek üzere kullanma

Bu sayfada, bir AAD uygulamanın nasıl oluşturularak, belirteci doğrulamak ve Uç Nokta için Microsoft Defender için bir erişim belirteci elde etmek nasıl açıklanır.

> [!NOTE]
> Kullanıcı adına Uç Nokta için Microsoft Defender API'sine erişirken doğru Uygulama iznine ve kullanıcı iznine ihtiyacınız vardır.
> E-posta hesaplarıyla ilgili kullanıcı izinlerini Uç Nokta için Microsoft Defender, bkz[. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).

> [!TIP]
> Portalda bir eylemi gerçekleştirme izniniz varsa, API'de eylemi gerçekleştirme izniniz vardır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. [Genel Yönetici rolüne](https://portal.azure.com) sahip bir kullanıcı hesabıyla **Azure'da oturum** açın.

2. Yeni kayıt **Azure Active Directory** \> **Uygulama kayıtları** \> **gidin**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Uygulama kayıtları portalında Microsoft Azure sayfası" lightbox="images/atp-azure-new-app2.png":::

3. Uygulama **kaydettir sayfası** görüntülendiğinde, uygulamanın kayıt bilgilerini girin:
   - **Ad** - Uygulama kullanıcıları için görüntülenecek anlamlı bir uygulama adı girin.
   - **Desteklenen hesap türleri** - Uygulamanın desteklemesi istediğiniz hesapları seçin.

     <br>

     |Desteklenen hesap türleri|Açıklama|
     |---|---|
     |**Yalnızca bu kuruluş dizininde hesaplar**|İş hattı (LOB) uygulaması inşa bunlar için bu seçeneği belirtin. Uygulamayı dizine kaydetmezseniz, bu seçenek kullanılamaz. <p> Bu seçenek, Azure AD'ye yalnızca tek kiracılı olarak eşler. <p> Uygulamayı dizin dışında kaydetmedikçe bu varsayılan seçenektir. Uygulamanın dizin dışında kayıtlı olduğu durumlarda, varsayılan değer Azure AD çok kiracılı ve kişisel Microsoft hesaplarıdır.|
     |**Herhangi bir kuruluş dizininde hesaplar**|Tüm iş ve eğitim müşterilerini hedeflemek için bu seçeneği belirleyin. <p> Bu seçenek, bir Azure AD'ye yalnızca birden çok kiracılı olarak eşler. <p> Uygulamayı yalnızca tek kiracılı Azure AD olarak kaydettiysanız, Azure AD çok kiracılı olacak şekilde güncelleştirip Kimlik Doğrulama blade'i aracılığıyla tek **kiracıya geri dönebilirsiniz** .|
     |**Herhangi bir kuruluş dizininde ve kişisel Microsoft hesaplarında bulunan hesaplar**|En geniş müşteri kitlesi için bu seçeneği belirleyin. <p> Bu seçenek, Azure AD çok kiracılı ve kişisel Microsoft hesaplarıyla eşler. <p> Uygulamayı Azure AD çok kiracılı ve kişisel Microsoft hesapları olarak kaydettiyebilirsiniz, kullanıcı arabiriminde bunu değiştiremezsiniz. Bunun yerine, desteklenen hesap türlerini değiştirmek için uygulama bildirim düzenleyicisini kullanabilirsiniz.|

   - **Yeniden yönlendirme URI'si (** isteğe bağlı) - Web veya Genel istemci (mobil  & masaüstü **)** ve sonra uygulamanın yeniden yönlendirme URL'sini (veya yanıt URL'sini) girin.

     - Web uygulamaları için, uygulamanın temel URL'sini girin. Örneğin, `http://localhost:31544` yerel makinede çalışan bir web uygulamasının URL'si olabilir. Kullanıcılar bu URL'yi kullanarak bir web istemci uygulamasında oturum adı.

     - Genel istemci uygulamalarında, belirteç yanıtlarını geri almak için Azure AD tarafından kullanılan URI'yi sağlar. Uygulamanıza özgü bir değer girin, örneğin `myapp://auth`.

     Web uygulamalarına veya yerel uygulamalara yönelik belirli örnekler görmek için hızlı [başlangıçlarımızı kontrol edin](/azure/active-directory/develop/#quickstarts).

     Bitirdikten sonra **Kaydol'a tıklayın**.

4. Uygulamanıza erişim izni Uç Nokta için Microsoft Defender ve 'Okuma uyarıları' izni attayabilirsiniz:

   - Uygulama sayfanız üzerinde **API** \>  \> İzinleri Ekle İzin API'leri Kuruluşumda şu API'leri kullanır> **WindowsDefenderATP** yazın ve **WindowsDefenderATP'de öğesini seçin**.

     > [!NOTE]
     > *WindowsDefenderATP* özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlayabilirsiniz.

     :::image type="content" alt-text="izin ekleyin." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Temsilci **İzinleri Uyarı'ya** \> **tıklayın.İzin** **>'ı seçin**.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Uygulama türü ve izin bölmeleri" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Uygun izinleri seçin. Okuma uyarıları yalnızca bir örnektir.

     Örneğin:

     - Gelişmiş [sorguları çalıştırmak için Gelişmiş](run-advanced-query-api.md) sorguları **çalıştırma iznini** seçin.
     - Cihazı [yalıtmak için](isolate-machine.md) Makine **iznini yalıt öğesini** seçin.
     - Hangi izinlere ihtiyacınız olduğunu belirlemek için **çağrı yapmakla** ilgilendiğiniz API'deki İzinler bölümünü görüntüebilirsiniz.

   - İzin **ver'i seçin**.

      > [!NOTE]
      > Her izin ekley irden sonra **geçerlik için İzin** Ver'i seçmeniz gerekir.

      :::image type="content" source="images/grant-consent.png" alt-text="Genel yönetici izin seçeneği" lightbox="images/grant-consent.png":::

5. Uygulama kimliğinizi ve kiracı kimliğinizi bir yere yazın.

    Uygulama sayfanız üzerinde Genel **Bakış'a** gidin ve aşağıdaki bilgileri kopyalayın:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Oluşturulan uygulama kimliği"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Erişim belirteci alın

Bu belirteçleri kullanma hakkında AAD azure [ad öğreticisi'ne bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>C'yi kullanma\#

- Uygulamanıza aşağıdaki sınıfı kopyalayıp yapıştırın.
- Belirteç **almak için AcquireUserTokenAsync** yöntemini uygulama kimliğiniz, kiracı kimliğiniz, kullanıcı adınız ve parolanız ile kullanın.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Belirteci doğrulama

Doğru belirtece sahip olduğunu doğrulayın:

- Kodunu çözmek için [önceki adımda edinilen belirteci JWT'ye](https://jwt.ms) kopyalayıp yapıştırın.
- İstenen uygulama izinleri ile bir 'scp' talebi alasınız.
- Aşağıdaki ekran görüntüsünde, öğreticide, uygulamada alınan kod çözme belirteci görebilirsiniz:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Belirteç doğrulama sayfası" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>API'ye erişmek için Uç Nokta için Microsoft Defender kullanma

- Kullanmak istediğiniz API'yi seçin - [Desteklenen API'Uç Nokta için Microsoft Defender seçin](exposed-apis-list.md).
- "Taşıyıcı {token}" adresine göndermek istediğiniz HTTP isteğinde Yetkilendirme üst bilgisini ayarlayın (Taşıyıcı, Yetkilendirme düzenidir).
- Belirtecin son kullanma süresi 1 saattir (aynı belirteçe sahip birden fazla istek gönderabilirsiniz).

- C# kullanarak uyarıların listesini almak için istek **gönderme örneği**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Microsoft Defender API'leri](exposed-apis-list.md)
- [Uygulama Uç Nokta için Microsoft Defender ile Access 2013](exposed-apis-create-app-webapp.md)
