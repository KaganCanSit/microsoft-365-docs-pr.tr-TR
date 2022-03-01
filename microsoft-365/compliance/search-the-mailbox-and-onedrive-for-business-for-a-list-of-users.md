---
title: İçerik Arama & OneDrive İş kullanıcıların listesini bulmak için posta kutusu arama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/3/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 5f4f8206-2d6a-4cb2-bbc6-7a0698703cc0
description: Posta kutularında ve sitelerde bir grup kullanıcı için arama yapmak OneDrive İş İçerik Arama ve betik kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2fdf749511cc859c0aec2ea947c3a53cb800cf8c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996999"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Posta kutusunda arama yapmak ve OneDrive İş kullanıcı listesi aramak için İçerik Arama'ya tıklayın

Güvenlik & Uyumluluk Merkezi PowerShell, zaman alıcı eKbulma ile ilgili görevleri otomatikleştirmenize izin veren bir dizi cmdlet sağlar. Şu anda, çok fazla sayıda özel Microsoft 365 uyumluluk merkezi konumlarında arama yapmak için İçerik araması oluşturmak zaman ve hazırlık alır. Arama oluşturmadan önce, her sitenin URL'sini OneDrive İş sonra her posta kutusunu ve posta kutusunu OneDrive İş aramanıza eklemeniz gerekir. Gelecek sürümlerde, bu daha kolay olacaktır Microsoft 365 uyumluluk merkezi. O zamana kadar, bu işlemi otomatikleştirmek için bu makaledeki betiği kullanabilirsiniz. Bu betik size, kuruluş sitem etki alanının (örneğin, URL'de `https://contoso-my.sharepoint.com`**contoso**), kullanıcı e-posta adreslerinin listesini, yeni İçerik Arama adını ve kullanmak üzere arama sorgusunu girmenizi sağlar. Betik, OneDrive İş her kullanıcı için ayrı bir URL alır ve ardından, sağlamakta olduğu arama sorgusunu kullanarak posta kutusunda ve OneDrive İş sitesinde aramaların yer alan İçerik Arama'sini oluşturur ve başlatır.
  
## <a name="permissions-and-script-information"></a>İzinler ve betik bilgileri

- 3. Adımda betiği çalıştırmak için Microsoft 365 uyumluluk merkezi Online'da eBulma Yöneticisi rol grubunun bir üyesi ve SharePoint Online genel yöneticisi olun.

- 2. Adımda oluştursunu kullanıcıların listesini ve 3. Adım'daki betiği de aynı klasöre kaydetmeye dikkat edin. Bu, betiği çalıştırmayı kolaylaştırır.

- Betik en az hata işlemeyi içerir. Bunun birincil amacı, posta kutusunda hızlı ve kolay bir şekilde arama yapmak OneDrive İş kullanıcının kendi sitesinde arama yapmaktır.

- Bu konu başlığı altında verilen örnek betikler, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenemmektedir. Örnek betikler hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiklerin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>1. Adım: SharePoint Online Yönetim Kabuğu'nu yükleme

İlk adım, SharePoint Shell'i yüklemektir. Bu yordamda kabuk kullanmak zorunda değilsiniz, ancak 3. Adımda çalıştıracakları betik için gerekli önkulları içerdiği için onu yüklemeniz gerekir. Bu önkoşullar betiğin SharePoint Online ile iletişim kurmasına olanak OneDrive İş sağlar.
  
SharePoint Online Yönetim Kabuğu ortamını ayarlama [Windows PowerShell gidin](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) ve SharePoint Online Management Shell'i yüklemek için 1. Adım'SharePoint adımlarını gerçekleştirin.
  
## <a name="step-2-generate-a-list-of-users"></a>2. Adım: Kullanıcı listesi oluşturma

3. Adım'daki betik, posta kutularında arama yapmak ve kullanıcı OneDrive hesapları aramak için İçerik Arama'ya eklenir. Metin dosyasına yalnızca e-posta adreslerini yazarak veya Windows PowerShell'te bir komut çalıştırarak e-posta adreslerinin listesini alın ve bunları bir dosyaya kaydedin (betiği 3. Adımda kaydeden aynı klasörde bulunur).
  
İşte Exchange Online tüm kullanıcılar için e-posta adreslerinin listesini almak ve bunu adlı bir metin dosyasına kaydetmek için çalıştırabilirsiniz[.](/powershell/exchange/connect-to-exchange-online-powershell) `Users.txt` 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Bu komutu çalıştırdikten sonra, dosyayı açmayı ve özellik adını içeren üstbilgiyi kaldırmayı unutmayın. `PrimarySmtpAddress` Metin dosyası yalnızca e-posta adreslerinin listesini içermeli ve başka hiçbir şey içermeli. E-posta adresleri listesinden önce veya sonra boş satırlar olmadığını kontrol edin.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>3. Adım: Betiği çalıştırarak arama oluşturma ve başlatma

Bu adımda betiği çalıştırınca, sizden aşağıdaki bilgileri istenir. Betiği çalıştırmadan önce bu bilgilerin hazır olduğundan emin olun.
  
- **Kullanıcı kimlik bilgileriniz** - Betik, SharePoint Online'a erişmek, OneDrive İş URL'leri almak ve Güvenlik ve Uyumluluk Merkezi PowerShell'& bağlanmak için kimlik bilgilerinizi kullanır. 
    
- **Sitem etki alanı adı** - Sitem etki alanı, tüm sitelere sahip olan OneDrive İş alanıdır. Örneğin, Sitem etki alanının **https://contoso-my.sharepoint.com** URL'si , ise,  `contoso` betik sizden Sitem etki alanı adınızı isteminde geldiğinde siz de girmeniz gerekir. 
    
- **2. Adımdan gelen metin** dosyasının yol adı - 2. Adımda oluşturduğunuz metin dosyasının yol adı. Metin dosyası ve betik aynı klasörde yer alıyorsa, metin dosyasının adını girin. Aksi takdirde, metin dosyasının tam yol adını girin. 
    
- **İçerik Arama adı** - Betik tarafından oluşturulacak İçerik Arama'nın adı. 
    
- **Arama sorgusu** - İçerik Arama ile kullanılacak arama sorgusu oluşturulur ve çalıştırılan sorgudur. Arama sorguları hakkında daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).


**Betiği çalıştırmak için:**
    
1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `SearchEXOOD4B.ps1`. Dosyayı, 2. Adım'da kullanıcı listesini kaydett istediğiniz klasöre kaydedin.
    
  ```powershell
  # This PowerShell script will prompt you for the following information:
  #    * Your user credentials 
  #    * The name of your organization's MySite domain                                              
  #    * The pathname for the text file that contains a list of user email addresses
  #    * The name of the Content Search that will be created
  #    * The search query string
  # The script will then:
  #    * Find the OneDrive for Business site for each user in the text file
  #    * Create and start a Content Search using the above information
  # Get user credentials
  if (!$credentials)
  {
      $credentials = Get-Credential
  }
  # Get the user's MySite domain name.  We use this to create the admin URL and root URL for OneDrive for Business
  $mySiteDomain = Read-Host "What is your organization's MySite domain?  For example,  'contoso' for 'https://contoso-my.sharepoint.com'"
  $AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
  $mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
  # Get other required information
  $inputfile = read-host "Enter the file name of the text file that contains the email addresses for the users you want to search"
  $searchName = Read-Host "Enter the name for the new search"
  $searchQuery = Read-Host "Enter the search query you want to use"
  $emailAddresses = Get-Content $inputfile | where {$_ -ne ""}  | foreach{ $_.Trim() }
  # Connect to Security & Compliance Center PowerShell
  if (!$s -or !$a)
  {
      Import-Module ExchangeOnlineManagement
      Connect-IPPSSession
  }
  
  # Load the SharePoint assemblies from the SharePoint Online Management Shell
  # To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
  if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
  {
      $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
      $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
      $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
      if (!$SharePointClient)
      {
          Write-Error "SharePoint Online Management Shell isn't installed, please install from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then run this script again"
          return;
      }
  }
  if (!$spCreds)
  {
      $spCreds = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($credentials.UserName, $credentials.Password)
  }
  # Add the path of the User Profile Service to the SPO admin URL, then create a new webservice proxy to access it
  $proxyaddr = "$AdminUrl/_vti_bin/UserProfileService.asmx?wsdl"
  $UserProfileService= New-WebServiceProxy -Uri $proxyaddr -UseDefaultCredential False
  $UserProfileService.Credentials = $credentials
  # Take care of auth cookies
  $strAuthCookie = $spCreds.GetAuthenticationCookie($AdminUrl)
  $uri = New-Object System.Uri($AdminUrl)
  $container = New-Object System.Net.CookieContainer
  $container.SetCookies($uri, $strAuthCookie)
  $UserProfileService.CookieContainer = $container
  Write-Host "Getting each user's OneDrive for Business URL"
  $urls = @()
  foreach($emailAddress in $emailAddresses)
  {
      try
      {
          $prop = $UserProfileService.GetUserProfileByName("i:0#.f|membership|$emailAddress") | Where-Object { $_.Name -eq "PersonalSpace" } 
          $url = $prop.values[0].value
          $furl = $mySiteUrlRoot + $url
          $urls += $furl
          Write-Host "-$emailAddress => $furl"
      }
      catch
      {
          Write-Warning "Could not locate OneDrive for $emailAddress"
      }
  }
  Write-Host "Creating and starting the search"
  $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $emailAddresses -SharePointLocation $urls -ContentMatchQuery $searchQuery
  # Finally, start the search and then display the status
  if($search)
  {
      Start-ComplianceSearch $search.Name
      Get-ComplianceSearch $search.Name
  }
  
  ```

2. Dosyayı Windows PowerShell betiğinizi kaydeden klasöre ve 2. Adım'dan kullanıcıların listesine gidin.
    
3. Betiği başlatma; örneğin:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Kimlik bilgileriniz istendiğinde e-posta adresinizi ve parolanızı girin, ardından Tamam'a **tıklayın**. 
    
5. Betik tarafından istendiğinde aşağıdaki bilgileri girin. Her bilgi parçasını yazın ve Enter tuşuna **basın**.
    
    - Sitem etki alanının adı. 
    
    - Kullanıcı listesini içeren metin dosyasının yol adı.
    
    - İçerik Arama için bir ad.
    
    - Arama sorgusu (içerik konumlarında yer alan tüm öğeleri geri dönmek için bu boş bırakın).
    
    Betik, her sitenin URL'lerini OneDrive İş sonra da arama oluşturur ve başlatır. Arama istatistiklerini ve sonuçlarını görüntülemek için Güvenlik & Uyumluluk Merkezi PowerShell'de **Get-ComplianceSearch** cmdlet'ini çalıştırabilirsiniz veya Microsoft 365 uyumluluk merkezi'de İçerik arama sayfasına gidip aramayla ilgili bilgileri görüntüleyebilirsiniz.
