---
title: MSSP müşteri kiracısı uyarılarını getirme
description: Müşteri kiracılarından uyarı alma hakkında bilgi alın
keywords: yönetilen güvenlik hizmeti sağlayıcısı, mssp, yapılandırma, tümleştirme
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: e2ac36689f9f41badb2f4216198d8818e568778b
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010813"
---
# <a name="fetch-alerts-from-mssp-customer-tenant"></a>MSSP müşteri kiracısı uyarılarını getirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!NOTE]
> Bu eylem MSSP tarafından  alınır.

Uyarıları getirmenin iki yolu vardır:

- SIEM yöntemini kullanma
- API'leri kullanma

## <a name="fetch-alerts-into-your-siem"></a>SIEM'inize uyarı alma

SIEM sisteminize uyarı getirmek için aşağıdaki adımları atılması gerekir:

- 1. Adım: Üçüncü taraf uygulaması oluşturma
- 2. Adım: Müşterinizin kiracısına erişim ve yenileme belirteçleri alın
- 3. Adım: Uygulamanıza izin Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>1. Adım: Azure Active Directory (Azure AD) uygulamasında uygulama oluşturma

Bir uygulama oluşturmanız ve müşterinizin kiracıdan uyarı alma Microsoft 365 Defender gerekir.

1. [Azure AD portalında oturum açın](https://aad.portal.azure.com/).

2. Uygulama **Azure Active Directory** \> **seçin**.

3. Yeni **kayıt'a tıklayın**.

4. Aşağıdaki değerleri belirtin:

    - Ad: \<Tenant_name\> SIEM MSSP Bağlayıcısı (Tenant_name kiracı görünen adıyla değiştirin)

    - Desteklenen hesap türleri: Yalnızca bu kuruluş dizininde yer alan hesap
    - Yeniden yönlendirme URI'si: Web'i seçin `https://<domain_name>/SiemMsspConnector`ve yazın (<domain_name> kiracı adıyla değiştirin)

5. **Kaydol'a tıklayın**. Uygulama, sahibi olduğunuz uygulamalar listesinde görüntülenir.

6. Uygulamayı seçin ve genel bakış'a **tıklayın**.

7. Uygulama **(istemci) kimliği alanından değeri** güvenli bir yere kopyalayın; bir sonraki adımda buna ihtiyacınız olacak.

8. Yeni **& panelinde Sertifika** gizlileri'ni seçin.

9. Yeni istemci **sırrı'ya tıklayın**.

    - Açıklama: Anahtar için bir açıklama girin.
    - Son kullanma tarihi: **1 yıl içinde'yi seçin**

10. **Ekle'ye** tıklayın, istemci sırrı değerini güvenli bir yere kopyalayın; bir sonraki adımda buna ihtiyacınız olacak.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>2. Adım: Müşterinizin kiracısına erişim ve yenileme belirteçleri alın

Bu bölüm, belirteçleri müşterinizin kiracıdan almak için PowerShell betiği kullanma hakkında size yol sağlar. Bu betik, OAuth Authorization Code kod dosyası kullanılarak erişim ve yenileme belirteçlerine erişmek ve belirteçleri yenilemek için önceki Flow.

Kimlik bilgilerinizi verdikten sonra, uygulamanın müşterinin kiracısına sağlanması için uygulamaya izin verebilirsiniz.

1. Yeni bir klasör oluşturun ve bunu şu şekilde isim edin: `MsspTokensAcquisition`.

2. [LoginBrowser.psm1 modülünü indirin](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) ve klasöre `MsspTokensAcquisition` kaydedin.

    > [!NOTE]
    > Satır 30'da, ile `authorzationUrl` değiştirin `authorizationUrl`.

3. Aşağıdaki içeriği içeren bir dosya oluşturun ve bu dosyayı adla `MsspTokensAcquisition.ps1` klasöre kaydedin:

    ```powershell
    param (
        [Parameter(Mandatory=$true)][string]$clientId,
        [Parameter(Mandatory=$true)][string]$secret,
        [Parameter(Mandatory=$true)][string]$tenantId
    )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

    # Load our Login Browser Function
    Import-Module .\LoginBrowser.psm1

    # Configuration parameters
    $login = "https://login.microsoftonline.com"
    $redirectUri = "https://SiemMsspConnector"
    $resourceId = "https://graph.windows.net"

    Write-Host 'Prompt the user for his credentials, to get an authorization code'
    $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                        $login, $tenantId, $clientId, $redirectUri, $resourceId)
    Write-Host "authorzationUrl: $authorizationUrl"

    # Fake a proper endpoint for the Redirect URI
    $code = LoginBrowser $authorizationUrl $redirectUri

    # Acquire token using the authorization code

    $Body = @{
        grant_type = 'authorization_code'
        client_id = $clientId
        code = $code
        redirect_uri = $redirectUri
        resource = $resourceId
        client_secret = $secret
    }

    $tokenEndpoint = "$login/$tenantId/oauth2/token?"
    $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
    $token = $Response.access_token
    $refreshToken= $Response.refresh_token

    Write-Host " ----------------------------------- TOKEN ---------------------------------- "
    Write-Host $token

    Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
    Write-Host $refreshToken
    ```
4. Klasörde yükseltilmiş bir PowerShell komut istemini `MsspTokensAcquisition` açın.

5. Aşağıdaki konumu çalıştırın: `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. Aşağıdaki komutları girin: `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - Önceki \<client_id\> adımda **sahip olduğunuz Uygulama (istemci)** kimliğiyle değiştirin.
    - Önceki \<app_key\> adımda **oluşturduğunuz İstemci** Sırrı ile değiştirin.
    - Müşterinizin \<customer_tenant_id\> Kiracı Kimliği ile **değiştirin**.

7. Kimlik bilgilerinizi ve onay bilgilerinizi sağlamanız istenir. Sayfa yönlendirmesini yoksayın.

8. PowerShell penceresinde bir erişim belirteci ve yenileme belirteci alırsınız. SIEM bağlayıcınızı yapılandırmak için yenileme belirtecini kaydedin.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>3. Adım: Uygulamanıza izin Microsoft 365 Defender

Bu uygulamada oluşturduğunuz uygulamaya izin Microsoft 365 Defender.

Uygulamaya izin vermek için **Portal sistemi ayarlarını yönetme** izninizin olmasına gerek vardır. Aksi takdirde, müşteriden sizin için uygulamaya izin vermelerini isteğiniz gerekir.

1. Şu yere `https://security.microsoft.com?tid=<customer_tenant_id>` gidin ( \<customer_tenant_id\> müşterinin kiracı kimliğiyle değiştirin).

2. Uç **Ayarlar** \> **API'leri** \>  \> **SIEM'ye tıklayın**.

3. **MSSP sekmesini** seçin.

4. İlk adımda **Uygulama Kimliğini** ve Kiracı **Kimliği'nizi girin**.

5. Uygulamayı **yetkilendir'e tıklayın**.

Artık SIEM'niz için ilgili yapılandırma dosyasını indirebilir ve MICROSOFT 365 DEFENDER API'nize bağlanabilirsiniz. Daha fazla bilgi için bkz [. SIEM araçlarınıza uyarı çekme](configure-siem.md).

- ArcSight yapılandırma dosyası / Splunk Kimlik Doğrulama Özellikleri dosyasında, gizli değeri ayarerek uygulama anahtarınızı el ile yazın.
- Portalda bir yenileme belirteci almak yerine, betiği bir yenileme belirteci almak (veya başka bir şekilde almak) için önceki adımdan kullanın.

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>API'leri kullanarak MSSP müşteri kiracısına uyarılar getirme

REST API kullanarak uyarıları getirme hakkında bilgi için bkz. [MSSP müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Portala MSSP erişimi ver](grant-mssp-access.md)
- [MSSP müşteri portalına erişme](access-mssp-portal.md)
- [Uyarı bildirimlerini yapılandırma](configure-mssp-notifications.md)
