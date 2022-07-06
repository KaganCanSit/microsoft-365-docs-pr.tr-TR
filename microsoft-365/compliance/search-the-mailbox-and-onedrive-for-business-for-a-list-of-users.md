---
title: Posta kutusu & OneDrive İş sitesindeki kullanıcıların listesi için İçerik Arama'yı kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Bu makaledeki İçerik Arama'yı ve betiği kullanarak posta kutularında ve OneDrive İş sitelerinde bir kullanıcı grubu arayın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 02ee9790d35eca411a9e27607a7e99ca962ddf05
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629177"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Kullanıcı listesi için posta kutusu ve OneDrive İş sitesinde arama yapmak için İçerik Arama'yı kullanma

Güvenlik & Uyumluluğu PowerShell, zaman alan eBulma ile ilgili görevleri otomatikleştirmenize olanak sağlayan bir dizi cmdlet sağlar. Şu anda, çok sayıda koruyucu içerik konumunu aramak için Microsoft Purview uyumluluk portalı bir İçerik araması oluşturmak zaman ve hazırlık ister. Arama oluşturmadan önce, her OneDrive İş sitenin URL'sini toplamanız ve ardından her posta kutusunu ve OneDrive İş siteyi aramaya eklemeniz gerekir. Gelecek sürümlerde, uyumluluk portalında bunu yapmak daha kolay olacaktır. O zamana kadar, bu işlemi otomatikleştirmek için bu makaledeki betiği kullanabilirsiniz. Bu betik, kuruluşunuzun Sitem etki alanının adını (örneğin, URL'deki `https://contoso-my.sharepoint.com`**contoso** ), kullanıcı e-posta adreslerinin listesini, yeni İçerik Aramasının adını ve kullanılacak arama sorgusunu ister. Betik, listedeki her kullanıcı için OneDrive İş URL'sini alır ve ardından, sağladığınız arama sorgusunu kullanarak posta kutusunda arama yapıp listedeki her kullanıcı için siteyi OneDrive İş bir İçerik Araması oluşturur ve başlatır.

## <a name="permissions-and-script-information"></a>İzinler ve betik bilgileri

- 3. Adımda betiği çalıştırmak için uyumluluk portalında eBulma Yöneticisi rol grubunun üyesi ve SharePoint Online genel yöneticisi olmanız gerekir.

- 2. Adımda oluşturduğunuz kullanıcıların listesini ve 3. Adım'daki betiği aynı klasöre kaydettiğinizden emin olun. Bu, betiği çalıştırmayı kolaylaştırır.

- Betik en az hata işleme içerir. Birincil amacı, her kullanıcının posta kutusunu ve OneDrive İş sitesini hızlı ve kolay bir şekilde aramaktır.

- Bu konuda sağlanan örnek betikler, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betikler, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiklerin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>1. Adım: SharePoint Online Yönetim Kabuğu'nı yükleme

İlk adım, SharePoint Online Yönetim Kabuğu'na yüklemektir. Bu yordamda kabuğu kullanmanız gerekmez, ancak 3. Adımda çalıştırdığınız betiğin gerektirdiği önkoşulları içerdiğinden bunu yüklemeniz gerekir. Bu önkoşullar, betiğin sharepoint online ile iletişim kurarak OneDrive İş sitelerinin URL'lerini almasına olanak sağlar.

[SharePoint Online Yönetim Kabuğu ortamını ayarlama'ya gidin ve SharePoint Online Yönetim Kabuğu'nı](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) yüklemek için 1. ve 2. Adım'ı gerçekleştirin.

## <a name="step-2-generate-a-list-of-users"></a>2. Adım: Kullanıcıların listesini oluşturma

3. Adım'daki betik, posta kutularında ve OneDrive hesaplarında kullanıcı listesi aramak için bir İçerik Araması oluşturur. E-posta adreslerini bir metin dosyasına yazabilir veya PowerShell'de bir komut çalıştırarak e-posta adreslerinin listesini alabilir ve bir dosyaya kaydedebilirsiniz (betiği 3. Adımda kaydedebileceğiniz klasörde bulunur).

Burada, kuruluşunuzdaki tüm kullanıcıların e-posta adreslerinin listesini almak ve adlı `Users.txt`bir metin dosyasına kaydetmek üzere çalıştırabileceğiniz bir [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) komutu verilmiştir.

```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Bu komutu çalıştırdıktan sonra dosyayı açtığınızdan ve özellik adını içeren üst bilgiyi kaldırdığınızdan emin olun. `PrimarySmtpAddress` Metin dosyası yalnızca e-posta adreslerinin listesini içermeli ve başka bir şey içermemelidir. E-posta adresleri listesinden önce veya sonra boş satır olmadığından emin olun.

## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>3. Adım: Aramayı oluşturmak ve başlatmak için betiği çalıştırın

Bu adımda betiği çalıştırdığınızda sizden aşağıdaki bilgileri isteyecektir. Betiği çalıştırmadan önce bu bilgilerin hazır olduğundan emin olun.

- **Kullanıcı kimlik bilgileriniz** - Betik, OneDrive İş URL'lerini almak ve Güvenlik & Uyumluluğu PowerShell'e bağlanmak üzere SharePoint Online'a erişmek için kimlik bilgilerinizi kullanır.

- **Sitem etki alanınızın adı** - Sitem etki alanı, kuruluşunuzdaki tüm OneDrive İş sitelerini içeren etki alanıdır. Örneğin, Sitem etki alanınızın URL'si ise **https://contoso-my.sharepoint.com**, betik sitem etki alanınızın adını istediğinizde girersiniz  `contoso` .

- **2. Adımdaki metin dosyasının yol adı - 2** . Adımda oluşturduğunuz metin dosyasının yol adı. Metin dosyası ve betik aynı klasörde yer alıyorsa, metin dosyasının adını girin. Aksi takdirde, metin dosyasının tam yol adını girin.

- **İçerik Aramasının Adı** - Betik tarafından oluşturulacak İçerik Aramasının adı.

- **Arama sorgusu** - İçerik Arama ile kullanılacak arama sorgusu oluşturulur ve çalıştırılır. Arama sorguları hakkında daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

**Betiği çalıştırmak için:**

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `SearchEXOOD4B.ps1`. Dosyayı, 2. Adımda kullanıcı listesini kaydettiğiniz klasöre kaydedin.

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
   # Connect to Security & Compliance PowerShell
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

2. Windows PowerShell açın ve betiği kaydettiğiniz klasöre ve 2. Adım'dan kullanıcı listesine gidin.

3. Betiği başlatın; örneğin:

    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Kimlik bilgileriniz istendiğinde, e-posta adresinizi ve parolanızı girin ve **tamam'a** tıklayın.

5. Betik tarafından istendiğinde aşağıdaki bilgileri girin. Her bilgi parçasını yazın ve **Enter tuşuna** basın.

    - Sitem etki alanınızın adı.

    - Kullanıcı listesini içeren metin dosyasının yol adı.

    - İçerik Arama için bir ad.

    - Arama sorgusu (içerik konumlarındaki tüm öğeleri döndürmek için bu boş bırakın).

    Betik her OneDrive İş sitenin URL'lerini alır ve ardından aramayı oluşturur ve başlatır. Arama istatistiklerini ve sonuçlarını görüntülemek için Güvenlik & Uyumluluk PowerShell'de **Get-ComplianceSearch** cmdlet'ini çalıştırabilir veya arama hakkındaki bilgileri görüntülemek için uyumluluk portalındaki **İçerik arama** sayfasına gidebilirsiniz.
