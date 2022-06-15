---
title: Kullanıcı adına Microsoft 365 Defender API'lere erişmek için uygulama oluşturma
description: Kullanıcı adına Microsoft 365 Defender API'lere erişmeyi öğrenin.
keywords: kullanıcı, api, uygulama, kullanıcı, erişim belirteci, belirteç adına erişim,
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
ms.openlocfilehash: 41f2763d73bbb9ed0b7ae32dce431cb2c1a4d71f
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102602"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Kullanıcı adına Microsoft 365 Defender API'lere erişmek için uygulama oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Bu sayfada, tek bir kullanıcı adına Microsoft 365 Defender program aracılığıyla erişim elde etmek için bir uygulamanın nasıl oluşturulacağı açıklanmaktadır.

Tanımlı bir kullanıcı olmadan Microsoft 365 Defender program aracılığıyla erişmeniz gerekiyorsa (örneğin, bir arka plan uygulaması veya daemon yazıyorsanız), bkz. [Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-web.md). Birden çok kiracıya erişim sağlamanız gerekiyorsa (örneğin, büyük bir kuruluşa veya bir müşteri grubuna hizmet veriyorsanız) bkz. [Microsoft 365 Defender API'lere iş ortağı erişimi olan bir uygulama oluşturma](api-partner-access.md). Hangi tür erişime ihtiyacınız olduğundan emin değilseniz bkz. [Kullanmaya başlayın](api-access.md).

Microsoft 365 Defender, bir dizi programlı API aracılığıyla verilerinin ve eylemlerinin büyük bir kısmını kullanıma sunar. Bu API'ler iş akışlarını otomatikleştirmenize ve Microsoft 365 Defender özelliklerinden yararlanmanıza yardımcı olur. Bu API erişimi için OAuth2.0 kimlik doğrulaması gerekir. Daha fazla bilgi için bkz[. OAuth 2.0 Yetkilendirme Kodu Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Genel olarak, bu API'leri kullanmak için aşağıdaki adımları uygulamanız gerekir:

- bir Azure Active Directory (Azure AD) uygulaması oluşturun.
- Bu uygulamayı kullanarak erişim belirteci alın.
- Microsoft 365 Defender API'sine erişmek için belirteci kullanın.

Bu makalede şunların nasıl yapılacağını açıklar:

- Azure AD uygulaması oluşturma
- Microsoft 365 Defender erişim belirteci alma
- Belirteci doğrulama

> [!NOTE]
> Kullanıcı adına Microsoft 365 Defender API'sine erişirken doğru uygulama izinlerine ve kullanıcı izinlerine ihtiyacınız olacaktır.

> [!TIP]
> Portalda eylem gerçekleştirme izniniz varsa, eylemi API'de gerçekleştirme izniniz vardır.

## <a name="create-an-app"></a>Uygulama oluşturma

1. **Azure'da Genel Yönetici** rolüyle kullanıcı olarak oturum açın.[](https://portal.azure.com)

2. **Azure Active Directory** >  **Uygulama kayıtları** >  **Yeni kayıt'a** gidin.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Azure portal Yönet bölmesindeki Yeni kayıt seçeneği" lightbox="../../media/atp-azure-new-app2.png":::

3. Formda, uygulamanız için bir ad seçin ve yeniden yönlendirme URI'sine ilişkin aşağıdaki bilgileri girin, ardından **Kaydet'i** seçin.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Azure portal uygulama kaydı bölmesi" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Uygulama türü:** Genel istemci
   - **Yeniden yönlendirme URI'si:** https://portal.azure.com

4. Uygulama sayfanızda **API İzinleri** Kuruluşumun > kullandığı izin  > **API'leri** >  **ekle'yi** seçin, **Microsoft Tehdit Koruması** yazın ve **Microsoft Tehdit Koruması'yı** seçin. Uygulamanız artık Microsoft 365 Defender erişebilir.

   > [!TIP]
   > *Microsoft Tehdit Koruması*, Microsoft 365 Defender için eski bir addır ve özgün listede görünmez. Görünmesini sağlamak için metin kutusuna adını yazmaya başlamanız gerekir.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Microsoft 365 Defender portalında kuruluşunuzun API'leri bölmesi" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - **Temsilci izinleri'ni** seçin. Senaryonuz için uygun izinleri seçin (örneğin **Incident.Read**) ve ardından **İzin ekle'yi** seçin.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Microsoft 365 Defender portalındaki Temsilci izinleri bölmesi" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Senaryonuz için ilgili izinleri seçmeniz gerekir. *Tüm olayları okuma* yalnızca bir örnektir. Hangi izne ihtiyacınız olduğunu belirlemek için lütfen çağırmak istediğiniz API'nin **İzinler** bölümüne bakın.
    >
    > Örneğin, [gelişmiş sorgular çalıştırmak](api-advanced-hunting.md) için 'Gelişmiş sorguları çalıştırma' iznini seçin; [cihazı yalıtmak](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) için 'Makineyi yalıt' iznini seçin.

5. **Yönetici onayı ver'i** seçin. Her izin eklediğinizde, geçerli olması için **Yönetici onayı ver'i** seçmeniz gerekir.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Microsoft 365 Defender portalında yönetici onayı verme bölmesi" lightbox="../../media/grant-consent-delegated.PNG":::

6. Uygulama kimliğinizi ve kiracı kimliğinizi güvenli bir yere kaydedin. Bunlar uygulama sayfanızda **Genel Bakış** altında listelenir.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Microsoft 365 Defender portalındaki Genel Bakış bölmesi" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Erişim belirteci alma

Azure Active Directory belirteçleri hakkında daha fazla bilgi için [Azure AD öğreticisine](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds) bakın.

### <a name="get-an-access-token-on-behalf-of-a-user-using-powershell"></a>PowerShell kullanarak kullanıcı adına erişim belirteci alma

Temsilci izinlerine sahip erişim belirteçleri almak için MSAL.PS kitaplığını kullanın. Kullanıcı adına erişim belirteci almak için aşağıdaki komutları çalıştırın:

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```
## <a name="validate-the-token"></a>Belirteci doğrulama

1. Kodunu çözmek için belirteci kopyalayıp [JWT'ye](https://jwt.ms) yapıştırın.
2. Kodu çözülen belirteç içindeki *rol* talebi için istenen izinlerin bulunduğundan emin olun.

Aşağıdaki görüntüde, , ```Incidents.ReadWrite.All```ve ```AdvancedHunting.Read.All``` izinleriyle ```Incidents.Read.All```bir uygulamadan alınan kodu çözülen belirteci görebilirsiniz:

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Microsoft 365 Defender portalındaki Kod Çözme Belirteci bölmesindeki izinler bölümü" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Microsoft 365 Defender API'sine erişmek için belirteci kullanma

1. Kullanmak istediğiniz API'yi (olaylar veya gelişmiş avcılık) seçin. Daha fazla bilgi için bkz[. Desteklenen Microsoft 365 Defender API'leri](api-supported.md).
2. Göndermek üzere olduğunuz http isteğinde yetkilendirme üst bilgisini `"Bearer" <token>`olarak ayarlayın, *taşıyıcı* yetkilendirme şeması ve *belirteç* doğrulanmış belirtecinizdir.
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
- ['Merhaba dünya' uygulaması oluşturma](api-hello-world.md)
- [Kullanıcı olmadan Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-web.md)
- [Microsoft 365 Defender API'lere çok kiracılı iş ortağı erişimine sahip bir uygulama oluşturma](api-partner-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 yetkilendirmesi](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
