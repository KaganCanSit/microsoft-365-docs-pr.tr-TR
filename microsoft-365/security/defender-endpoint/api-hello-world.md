---
title: Uç Nokta API'si için Microsoft Defender için Hello World
ms.reviewer: ''
description: Uç Nokta API için Microsoft Defender'a 'Merhaba dünya' tarzı bir API çağrısı oluşturun.
keywords: api'ler, desteklenen api'ler, gelişmiş av, sorgu, microsoft defender atp, uç nokta için Microsoft Defender
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
ms.openlocfilehash: 55d01dfe6d0b6fd69bf32016b1b5dd585827e168
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997123"
---
# <a name="microsoft-defender-for-endpoint-api---hello-world"></a>Uç Nokta API için Microsoft Defender - Hello World

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)


>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="get-alerts-using-a-simple-powershell-script"></a>Basit bir PowerShell betiği kullanarak Uyarılar'ı kullanma

### <a name="how-long-it-takes-to-go-through-this-example"></a>Bu örneği üzerinden geçen süre ne kadar sürer?

İki adımda yapılması yalnızca 5 dakika sürer:

- Uygulama kaydı
- Örnekleri kullanın: yalnızca kısa bir PowerShell betiğinin kopyalayıp yapıştır gerektirir

### <a name="do-i-need-a-permission-to-connect"></a>Bağlanmak için izin gerekiyor mu?

Uygulama kayıt aşamasında, genel yönetici rolüne sahip Azure Active Directory  Azure AD) kiracınız olması gerekir.

### <a name="step-1---create-an-app-in-azure-active-directory"></a>1. Adım - Aynı Uygulamada Azure Active Directory

1. [Genel yönetici kullanıcınız ile Azure'da](https://portal.azure.com) **oturum** açın.

2.  \> Azure Active Directory **App kayıtları Yeni kayıt'a** \> **gidin**.

   :::image type="content" alt-text="Kayıt Microsoft Azure gezinti görüntüsü." source="images/atp-azure-new-app2.png" lightbox="images/atp-azure-new-app2.png":::

3. Kayıt formunda, başvuru için bir ad seçin ve Kaydol'a **tıklayın**.

4. Uygulamanın Uç Nokta için Defender'a erişmesine ve 'Tüm uyarıları **okuma' izni atamasına izin** ver:

   - Uygulama sayfanız üzerinde **API** \>  \> İzinleri Ekle Kuruluşumda kullanan izin API'leri'ne **tıklayın > WindowsDefenderATP** yazın ve **WindowsDefenderATP'ye tıklayın**.

     > [!NOTE]
     > WindowsDefenderATP özgün listede görünmez. Görünmesini görmek için metin kutusuna adını yazmaya başlamalı.

     :::image type="content" alt-text="API erişimi ve API seçimi1 resmi." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Uygulama **izinleri** **Uyarısı.Oku.Tüm** \> Gün > İzin **ekle'ye tıklayın**.

     :::image type="content" alt-text="API erişimi ve API seçimi2 resmi." source="images/application-permissions.png" lightbox="images/application-permissions.png":::

     > [!IMPORTANT]
     > İlgili izinleri seçmeniz gerekir. 'Tüm Uyarıları Oku' yalnızca bir örnektir!

     Örneğin:

     - Gelişmiş [sorguları çalıştırmak için "](run-advanced-query-api.md)Gelişmiş sorguları çalıştırma" iznini seçin.
     - Bir [makine yalıtmak](isolate-machine.md) için "Makine ayırma" iznini seçin.
     - Hangi izinlere ihtiyacınız olduğunu belirlemek için lütfen çağrı **yapmakla** ilgilendiğiniz API'deki İzinler bölümüne bakın.

5. İzin **ver'e tıklayın**.

   > [!NOTE]
   > Her izin ekley tıklaymanız ve yeni **iznin** yürürlüğe girecek olması için İzin ver'e tıklamanız gerekir.

   ![İzin ver'in resmi.](images/grant-consent.png)

6. Uygulamaya bir gizli ekleyin.

    **Sertifikalar gizli & tıklayın**, gizli gizli için açıklama ekleyin ve Ekle'ye **tıklayın**.

    > [!IMPORTANT]
    > Ekle'ye **tıklayıp oluşturulan gizli değeri kopyalayın**. İşten ayrıldıktan sonra geri ala zaman kazanaaasiniz!

    ![Uygulama anahtarı oluşturma resmi.](images/webapp-create-key2.png)

7. Uygulama kimliğinizi ve kiracı kimliğinizi bir yere yazın.

   Uygulama sayfanız üzerinde Genel **Bakış'a** gidin ve şunları kopyalayın:

   ![Oluşturulan uygulama kimliğinin resmi.](images/app-and-tenant-ids.png)

Bitti! Bir uygulamayı başarıyla kaydettiysiniz!

### <a name="step-2---get-a-token-using-the-app-and-use-this-token-to-access-the-api"></a>2. Adım - Uygulamayı kullanarak bir belirteç alın ve API'ye erişmek için bu belirteci kullanın.

- Aşağıdaki betiği PowerShell ISE'ye veya bir metin düzenleyicisine kopyalayın ve **farklıGet-Token.ps1.**
- Bu betiği çalıştırarak bir belirteç oluşturulur ve bunu çalışma klasörüne dosya adı **Latest-token.txt**.

   ```powershell
   # That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
   # Paste below your Tenant ID, App ID and App Secret (App key).

   $tenantId = '' ### Paste your tenant ID here
   $appId = '' ### Paste your Application ID here
   $appSecret = '' ### Paste your Application secret here

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

- Sanity Check:
  - Betiği çalıştırın.
  - Tarayıcınızda şu gidin: <https://jwt.ms/>.
  - Belirteci kopyalayın (dosyanın Latest-token.txt).
  - Üst kutuya yapıştırma.
  - "Roller" bölümünü bakın. _Alert.Read.All rolünü_ bulun.

  :::image type="content" alt-text="Resim jwt.ms." source="images/api-jwt-ms.png" lightbox="images/api-jwt-ms.png":::

### <a name="lets-get-the-alerts"></a>Uyarıları al!

- Aşağıdaki betik API' **Get-Token.ps1** içinGet-Token.ps1'i kullanır ve son 48 saatlik Uyarıları alır.
- Bu betiği, önceki betiği kaydetmek istediğiniz **klasöreGet-Token.ps1**.
- Betik, betiklerle aynı klasörde yer alan verilerle birlikte iki dosya (json ve csv) oluşturur.

  ```powershell
  # Returns Alerts created in the past 48 hours.

  $token = ./Get-Token.ps1       #run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-Token.ps1

  # Get Alert from the last 48 hours. Make sure you have alerts in that time frame.
  $dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

  # The URL contains the type of query and the time filter we create above
  # Read more about other query options and filters at   Https://TBD- add the documentation link
  $url = "https://api.securitycenter.microsoft.com/api/alerts?`$filter=alertCreationTime ge $dateTime"

  # Set the WebRequest headers
  $headers = @{
      'Content-Type' = 'application/json'
      Accept = 'application/json'
      Authorization = "Bearer $token"
  }

  # Send the webrequest and get the results.
  $response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

  # Extract the alerts from the results.
  $alerts =  ($response | ConvertFrom-Json).value | ConvertTo-Json

  # Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
  $dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

  # Save the result as json and as csv
  $outputJsonPath = "./Latest Alerts $dateTimeForFileName.json"
  $outputCsvPath = "./Latest Alerts $dateTimeForFileName.csv"

  Out-File -FilePath $outputJsonPath -InputObject $alerts
  ($alerts | ConvertFrom-Json) | Export-CSV $outputCsvPath -NoTypeInformation
  ```

Hepsi bu kadar! Başarıyla tamamladık:

- Oluşturma, kayıt ve uygulama
- Bu uygulama için uyarıları okuma izni verildi
- API'ye bağlandı
- Son 48 saat içinde oluşturulan uyarıları geri dönmek için bir PowerShell betiği kullanıldı

## <a name="related-topic"></a>İlgili konu

- [Uç Nokta API'leri için Microsoft Defender](exposed-apis-list.md)
- [Uygulama bağlamında Uç Nokta için Access Microsoft Defender](exposed-apis-create-app-webapp.md)
- [Kullanıcı bağlamında Uç Nokta için Access Microsoft Defender](exposed-apis-create-app-nativeapp.md)
