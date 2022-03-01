---
title: REST API'si Microsoft 365 Defender Hello World
description: Uygulama oluşturma ve mobil API'lere erişmek için belirteç Microsoft 365 Defender öğrenin
keywords: uygulama, belirteç, erişim, aad, uygulama, uygulama kaydı, powershell, betik, genel yönetici, izin, microsoft 365 defender
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
ms.openlocfilehash: 1c83a64c3bf1e721ea54b526c0db0c5d7c403fba
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010757"
---
# <a name="hello-world-for-microsoft-365-defender-rest-api"></a>REST API'si Microsoft 365 Defender Hello World

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="get-incidents-using-a-simple-powershell-script"></a>Basit bir PowerShell betiği kullanarak olayları al

Bu projenin tamamlanması 5 - 10 dakika kadar sürer. Bu kez tahmin, uygulamayı kaydetmeyi ve PowerShell örnek betiğinden kodu uygulamayı içerir.

### <a name="register-an-app-in-azure-active-directory"></a>E-postada bir uygulamayı Azure Active Directory

1. Genel yönetici [rolüne](https://portal.azure.com) sahip bir kullanıcı olarak **Azure'da oturum** açın.

2. **Azure Active Directory** >  **App kayıtlarıne** **gidinYeni** >  kayıt.

   ![Kayıt Microsoft Azure gezinti görüntüsü.](../../media/atp-azure-new-app2.png)

3. Kayıt formunda, başvuru için bir ad seçin ve sonra Kaydol'a **tıklayın**. Yönlendirme URI'sini seçmek isteğe bağlıdır. Bu örneği tamamlamak için buna ihtiyacınız olmayacak.

4. Uygulama sayfanız üzerinde **API permissionsAdd** >  **permissionAPIs my organization** >  uses >, **Microsoft Threat Protection yazın** ve **Microsoft Threat Protection'ı seçin**. Artık uygulama erişim izni Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Tehdit* Koruması bu güncelleştirmelerin eski Microsoft 365 Defender, özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlamalı.
   ![API izin seçimi resmi.](../../media/apis-in-my-org-tab.PNG)

   - Uygulama **izinleriIncident.Read.All'i seçin ve İzin** **ekle'yi seçin**. > 

   ![API erişimi ve API seçimi görüntüsü.](../../media/request-api-permissions.PNG)

5. Yönetici **izni ver'i seçin**. Her izin ekleyseniz, geçerlik için **Yönetici izni ver'i** seçmeniz gerekir.

    ![İzin ver'in resmi.](../../media/grant-consent.PNG)

6. Uygulamaya bir gizli ekleyin. **Sertifikalar gizli & seçin**, gizli belgeye bir açıklama ekleyin ve ekle'yi **seçin**.

    > [!TIP]
    > Ekle'yi **seçin** ve **oluşturulan gizli değeri kopyalayın**. Siz ayrılarak gizli değeri geri ala zamanlarız.

    ![Uygulama anahtarı oluşturma resmi.](../../media/webapp-create-key2.png)

7. Uygulama kimliğinizi ve kiracı kimliğini güvenli bir yere kaydedin. Bunlar, uygulama sayfanıza **genel bakış** altında listelenir.

   ![Oluşturulan uygulama kimliğinin resmi.](../../media/app-and-tenant-ids.png)

### <a name="get-a-token-using-the-app-and-use-the-token-to-access-the-api"></a>Uygulamayı kullanarak bir belirteç alın ve API'ye erişmek için belirteci kullanın

Belirteçleri kullanma hakkında Azure Active Directory için [Azure AD öğreticisi'ne bakın](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Bu tanıtım uygulamasındaki örnek, test amacıyla gizli değerinizi yapıştırmanızı teşvik etmese de, üretimde çalışan bir  uygulamada gizli kodları asla zor kodlamanız gerekir. Üçüncü bir taraf kaynaklara erişmek için sizin sırrınızı kullanabilir. Azure Anahtar Kasasını kullanarak uygulamanın sırlarını güvende [tutmanıza yardımcı olabilirsiniz](/azure/key-vault/general/about-keys-secrets-certificates). Uygulamanızı nasıl koruyabilirsiniz gibi pratik bir örnek için bkz. Azure Anahtar Kasası [ile sunucu uygulamalarınız için gizli uygulamaları yönetme](/learn/modules/manage-secrets-with-azure-key-vault/).

1. Aşağıdaki betiği kopyalayıp sık kullanılan metin düzenleyicinize yapıştırın. Farklı kaydet **Get-Token.ps1**. Kodu PowerShell ISE'de olduğu gibi de çalıştırabilirsiniz, ancak bir sonraki bölümde olay getirme betiğini kullanırken yeniden çalıştırmamız gerek olduğundan kodu kaydetmeniz gerekir.

    Bu betik bir belirteç oluşturur ve bu belirteç adı altındaki çalışma klasörüne *Latest-token.txt.*

    ```PowerShell
    # This script gets the app context token and saves it to a file named "Latest-token.txt" under the current directory.
    # Paste in your tenant ID, client ID and app secret (App key).

    $tenantId = '' # Paste your directory (tenant) ID here
    $clientId = '' # Paste your application (client) ID here
    $appSecret = '' # # Paste your own app secret here to test, then store it in a safe place!

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

#### <a name="validate-the-token"></a>Belirteci doğrulama

1. Kodu çözmek için, alınan [belirteci kopyalayıp JWT'ye](https://jwt.ms) yapıştırın.
1. *JWT,* *JSON Web Belirteci'nin açılımıdır*. Kod çözme belirteci, bir dizi JSON tarafından biçimlendirilmiş öğe veya talep içerir. Kod çözme *belirteci* içinde talep ettiği rollerin istenen izinleri içerdiğindan emin olun.

    Aşağıdaki resimde, ile ve izinleri olan bir uygulamada alınan kod çözme belirteci ```Incidents.Read.All``````Incidents.ReadWrite.All``````AdvancedHunting.Read.All``` gösterebilirsiniz:

    ![Resim jwt.ms.](../../media/api-jwt-ms.png)

### <a name="get-a-list-of-recent-incidents"></a>Son olayları listele

Aşağıdaki betik **API'yeGet-Token.ps1** aşağıdaki komut dosyasını kullanır. Ardından, son 48 saat içinde güncelleştirilen olayları listesi alınır ve listeyi JSON dosyası olarak kaydeder.

> [!IMPORTANT]
> Bu betiği, kaydetmek istediğiniz klasöre **Get-Token.ps1**.

```PowerShell
# This script returns incidents last updated within the past 48 hours.

$token = ./Get-Token.ps1

# Get incidents from the past 48 hours.
# The script may appear to fail if you don't have any incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# This URL contains the type of query and the time filter we created above.
# Note that `$filter` does not refer to a local variable in our script --
# it's actually an OData operator and part of the API's syntax.
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the webrequest headers
$headers = @{
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the request and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results.
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get a string containing the execution time. We concatenate that string to the name 
# of the output file to avoid overwriting the file on consecutive runs of the script.
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"

Out-File -FilePath $outputJsonPath -InputObject $incidents
```

Hepsi bu kadar! Başarıyla tamamladık:

- Bir uygulama oluşturulur ve kaydedilir.
- Bu uygulama için uyarıları okuma izni verildi.
- API'ye bağlı.
- Son 48 saat içinde güncellenen olayları geri dönmek için bir PowerShell betiği kullanıldı.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [Kullanıcı olmadan e-Microsoft 365 Defender için uygulama oluşturma](api-create-app-web.md)
- [Kullanıcı adına API Microsoft 365 Defender erişmek için uygulama oluşturma](api-create-app-user-context.md)
- [Api'lere çok kiracılı iş ortağı erişimi Microsoft 365 Defender oluşturma](api-partner-access.md)
- [Azure Anahtar Kasası ile sunucu uygulamalarınıza olan sırlarınızı yönetin](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Kullanıcı oturum açma ve API erişimi için OAuth 2.0 Yetkilendirme](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)