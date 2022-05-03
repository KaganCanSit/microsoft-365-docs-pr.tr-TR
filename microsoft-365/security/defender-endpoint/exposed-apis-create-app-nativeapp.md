---
title: Uç Nokta için Microsoft Defender API'lerini kullanma
ms.reviewer: ''
description: Kullanıcı olmadan Uç Nokta için Microsoft Defender program aracılığıyla erişim elde etmek için yerel bir Windows uygulaması tasarlamayı öğrenin.
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
ms.openlocfilehash: aec4c7bdc0da76a6a52a8b8f19d89b8b54f3df9f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173478"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Uç Nokta için Microsoft Defender API'lerini kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu sayfada, kullanıcı adına Uç Nokta için Defender'a programlı erişim elde etmek için bir uygulamanın nasıl oluşturulacağı açıklanır.

Kullanıcı olmadan Uç Nokta için Microsoft Defender programlı erişime ihtiyacınız varsa, [uygulama bağlamı ile Erişim Uç Nokta için Microsoft Defender'ne](exposed-apis-create-app-webapp.md) bakın.

Hangi erişime ihtiyacınız olduğundan emin değilseniz [Giriş sayfasını](apis-intro.md) okuyun.

Uç Nokta için Microsoft Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler, iş akışlarını otomatikleştirmenize ve Uç Nokta için Microsoft Defender özelliklerine göre yenilik yapmanızı sağlar. API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:

- AAD uygulaması oluşturma
- Bu uygulamayı kullanarak erişim belirteci alma
- Uç Nokta için Defender API'sine erişmek için belirteci kullanma

Bu sayfada AAD uygulaması oluşturma, Uç Nokta için Microsoft Defender için erişim belirteci alma ve belirteci doğrulama açıklanmaktadır.

> [!NOTE]
> Kullanıcı adına Uç Nokta için Microsoft Defender API'sine erişirken doğru Uygulama iznine ve kullanıcı iznine ihtiyacınız olacaktır.
> Uç Nokta için Microsoft Defender kullanıcı izinlerini tanımıyorsanız bkz. [Rol tabanlı erişim denetimini kullanarak portal erişimini yönetme](rbac.md).

> [!TIP]
> Portalda eylem gerçekleştirme izniniz varsa, eylemi API'de gerçekleştirme izniniz vardır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. **Genel Yönetici** rolüne sahip bir kullanıcı hesabıyla [Azure'da](https://portal.azure.com) oturum açın.

2. **yeni kayıt Uygulama kayıtları Azure Active Directory** \>  \> gidin.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Microsoft Azure portalındaki Uygulama kayıtları sayfası" lightbox="images/atp-azure-new-app2.png":::

3. **Uygulamayı kaydet** sayfası görüntülendiğinde, uygulamanızın kayıt bilgilerini girin:
   - **Ad** - Uygulamanın kullanıcılarına görüntülenecek anlamlı bir uygulama adı girin.
   - **Desteklenen hesap türleri** - Uygulamanızın hangi hesapları desteklemesini istediğinizi seçin.

     <br>

     |Desteklenen hesap türleri|Açıklama|
     |---|---|
     |**Yalnızca bu kuruluş dizinindeki hesaplar**|İş kolu (LOB) uygulaması oluşturuyorsanız bu seçeneği belirleyin. Uygulamayı bir dizine kaydetmiyorsanız bu seçenek kullanılamaz. <p> Bu seçenek yalnızca tek kiracılı Azure AD eşlenir. <p> Uygulamayı bir dizinin dışına kaydetmediğiniz sürece bu varsayılan seçenektir. Uygulamanın bir dizin dışında kayıtlı olduğu durumlarda, varsayılan olarak çok kiracılı ve kişisel Microsoft hesapları Azure AD.|
     |**Herhangi bir kuruluş dizinindeki hesaplar**|Tüm iş ve eğitim müşterilerini hedeflemek istiyorsanız bu seçeneği belirleyin. <p> Bu seçenek yalnızca çok kiracılı Azure AD eşlenir. <p> Uygulamayı yalnızca tek kiracılı Azure AD olarak kaydettiyseniz, çok kiracılı Azure AD olacak şekilde güncelleştirebilir ve **Kimlik Doğrulama** dikey penceresi aracılığıyla tek kiracıya dönebilirsiniz.|
     |**Herhangi bir kuruluş dizinindeki hesaplar ve kişisel Microsoft hesapları**|En geniş müşteri kümesini hedeflemek için bu seçeneği belirleyin. <p> Bu seçenek, çok kiracılı ve kişisel Azure AD Microsoft hesaplarıyla eşlenir. <p> Uygulamayı çok kiracılı ve kişisel Azure AD Microsoft hesapları olarak kaydettiyseniz, bunu kullanıcı arabiriminde değiştiremezsiniz. Bunun yerine, desteklenen hesap türlerini değiştirmek için uygulama bildirim düzenleyicisini kullanmanız gerekir.|

   - **Yeniden yönlendirme URI'si (isteğe bağlı)** - Oluşturduğunuz uygulama türünü, **Web** veya **Genel istemciyi (mobil & masaüstü)** seçin ve ardından uygulamanız için yeniden yönlendirme URI'sini (veya yanıt URL'sini) girin.

     - Web uygulamaları için uygulamanızın temel URL'sini sağlayın. Örneğin, `http://localhost:31544` yerel makinenizde çalışan bir web uygulamasının URL'si olabilir. Kullanıcılar bir web istemcisi uygulamasında oturum açmak için bu URL'yi kullanır.

     - Genel istemci uygulamaları için, belirteç yanıtlarını döndürmek için Azure AD tarafından kullanılan URI'yi sağlayın. Uygulamanıza `myapp://auth`özgü gibi bir değer girin.

     Web uygulamalarına veya yerel uygulamalara yönelik belirli örnekleri görmek için [hızlı başlangıçlarımıza](/azure/active-directory/develop/#quickstarts) göz atın.

     İşiniz bittiğinde **Kaydet'i** seçin.

4. Uygulamanızın Uç Nokta için Microsoft Defender erişmesine izin verin ve 'Uyarıları okuma' izni atayın:

   - Uygulama sayfanızda **API İzinleri** **Kuruluşumun kullandığı** **izin** \> API'leri \> ekle'yi seçin > **WindowsDefenderATP** yazın ve **WindowsDefenderATP'yi** seçin.

     > [!NOTE]
     > *WindowsDefenderATP* özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlayın.

     :::image type="content" alt-text="izin ekleyin." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - **Temsilci izinleri** \> **Uyarısı'nı seçin.Okuma** > **İzin ekle'yi** seçin.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Uygulama türü ve izin bölmeleri" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > İlgili izinleri seçin. Uyarıları okuma yalnızca bir örnektir.

     Örneğin:

     - [Gelişmiş sorgular çalıştırmak](run-advanced-query-api.md) için **Gelişmiş sorgu çalıştırma** izni'ne tıklayın.
     - [Cihazı yalıtmak](isolate-machine.md) için **Makine iznini yalıt'ı** seçin.
     - Hangi izne ihtiyacınız olduğunu belirlemek için çağırmak istediğiniz API'deki **İzinler** bölümünü görüntüleyin.

   - **İzin ver'i** seçin.

      > [!NOTE]
      > İzin eklediğinizde, yeni iznin geçerli olması için **İzin ver'i** seçmeniz gerekir.

      :::image type="content" source="images/grant-consent.png" alt-text="Genel yönetici onayı seçeneği" lightbox="images/grant-consent.png":::

5. Uygulama kimliğinizi ve kiracı kimliğinizi not edin.

    Uygulama sayfanızda **Genel Bakış'a** gidin ve aşağıdaki bilgileri kopyalayın:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Oluşturulan uygulama kimliği"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Erişim belirteci alma

AAD belirteçleri hakkında daha fazla bilgi için Azure AD [öğreticiye](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds) bakın.

### <a name="using-c"></a>C kullanma\#

- Uygulamanızda aşağıdaki sınıfı kopyalayın/yapıştırın.
- Belirteç almak için uygulama kimliğiniz, kiracı kimliğiniz, kullanıcı adınız ve parolanızla **AcquireUserTokenAsync** yöntemini kullanın.

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

Doğru belirteci kullandığınızdan emin olmak için doğrulayın:

- Kodunu çözmek için önceki adımda aldığınız belirteci [JWT'ye](https://jwt.ms) kopyalayın/yapıştırın.
- İstenen uygulama izinleriyle bir 'scp' talebi aldığınızdan doğrulayın.
- Aşağıdaki ekran görüntüsünde, öğreticide uygulamadan alınan kodu çözülen bir belirteci görebilirsiniz:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Belirteç doğrulama sayfası" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uç Nokta için Microsoft Defender API'ye erişmek için belirteci kullanma

- Kullanmak istediğiniz API'yi seçin - [Desteklenen Uç Nokta için Microsoft Defender API'leri](exposed-apis-list.md).
- Gönderdiğiniz HTTP isteğinde Yetkilendirme üst bilgisini "Taşıyıcı {token}" olarak ayarlayın (Taşıyıcı, Yetkilendirme şemasıdır).
- Belirtecin Sona erme süresi 1 saattir (aynı belirteçle birden fazla istek gönderebilirsiniz).

- **C# kullanarak** uyarıların listesini almak için istek gönderme örneği:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [api'leri Uç Nokta için Microsoft Defender](exposed-apis-list.md)
- [Uygulama bağlamı ile Uç Nokta için Microsoft Defender erişme](exposed-apis-create-app-webapp.md)
