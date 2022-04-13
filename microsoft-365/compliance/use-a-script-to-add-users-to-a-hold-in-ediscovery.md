---
title: Core eBulma örneğinde bir ayrı tutmaya kullanıcı eklemek için betik kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: bad352ff-d5d2-45d8-ac2a-6cb832f10e73
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Microsoft 365 uyumluluk merkezi bir eBulma olayıyla ilişkili yeni bir ayrı tutmaya posta kutuları & OneDrive İş siteleri eklemek için bir betik çalıştırmayı öğrenin.
ms.openlocfilehash: 10a605b422178e5006d8a027a697ca6745f82b98
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824498"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Core eBulma örneğinde bir ayrı tutmaya kullanıcı eklemek için betik kullanma

Güvenlik & Uyumluluk Merkezi PowerShell, eBulma servis taleplerini oluşturma ve yönetmeyle ilgili zaman alan görevleri otomatikleştirmenize olanak sağlayan cmdlet'ler sağlar. Şu anda Microsoft 365 uyumluluk merkezi Core eKescovery dosyasını kullanarak çok sayıda koruyucu içerik konumunu beklemeye almak zaman alır ve hazırlık yapılır. Örneğin, ayrı tutma oluşturmadan önce, ayrı tutmaya yerleştirmek istediğiniz her OneDrive İş sitesinin URL'sini toplamanız gerekir. Ardından, beklemeye almak istediğiniz her kullanıcı için posta kutusunu ve OneDrive İş sitesini ayrı tutmaya eklemeniz gerekir. Bu işlemi otomatikleştirmek için bu makaledeki betiği kullanabilirsiniz.
  
Betik, kuruluşunuzun Sitem etki alanının adını ister (örneğin, URL'dehttps://contoso-my.sharepoint.com), `contoso` var olan bir eBulma servis talebinin adı, servis talebiyle ilişkili yeni ayrı tutmanın adı, beklemeye almak istediğiniz kullanıcıların e-posta adreslerinin listesi ve sorgu tabanlı ayrı tutma oluşturmak istiyorsanız kullanmak üzere bir arama sorgusu. Betik daha sonra listedeki her kullanıcı için OneDrive İş sitesinin URL'sini alır, yeni ayrı tutmayı oluşturur ve ardından listedeki her kullanıcı için posta kutusunu ve OneDrive İş sitesini ayrı tutmaya ekler. Betik ayrıca yeni ayrı tutma hakkında bilgi içeren günlük dosyaları da oluşturur.
  
Bunun gerçekleşmesi için adımlar şunlardır:
  
[1. Adım: SharePoint Online Management Shell'i yükleme](#step-1-install-the-sharepoint-online-management-shell)
  
[2. Adım: Kullanıcıların listesini oluşturma](#step-2-generate-a-list-of-users)
  
[3. Adım: Betiği çalıştırarak ayrı tutma oluşturma ve kullanıcı ekleme](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Ayrı tutmaya kullanıcı eklemeden önce

- 3. Adımda betiği çalıştırmak için Microsoft 365 uyumluluk merkezi eBulma Yöneticisi rol grubunun üyesi ve SharePoint Online yöneticisi olmanız gerekir. Daha fazla bilgi için bkz[. Office 365 Güvenlik & Uyumluluk Merkezi'nde eBulma izinleri atama](assign-ediscovery-permissions.md).

- Microsoft 365 uyumluluk merkezi Core eBulma olayıyla ilişkili bir ayrı tutmaya en fazla 1.000 posta kutusu ve 100 site eklenebilir. Beklemeye almak istediğiniz her kullanıcının bir OneDrive İş sitesi olduğunu varsayarsak, bu makaledeki betiği kullanarak ayrı tutmaya en fazla 100 kullanıcı ekleyebilirsiniz.

- 2. Adımda oluşturduğunuz kullanıcıların listesini ve 3. Adım'daki betiği aynı klasöre kaydettiğinizden emin olun. Bu, betiği çalıştırmayı kolaylaştırır.

- Betik, kullanıcıların listesini mevcut bir servis talebiyle ilişkili yeni bir ayrı tutmaya ekler. Betiği çalıştırmadan önce ayrı tutma işlemini ilişkilendirmek istediğiniz durumun oluşturulduğundan emin olun.

- Bu makaledeki betik, Güvenlik & Uyumluluk Merkezi PowerShell ve SharePoint Çevrimiçi Yönetim Kabuğu'na bağlanırken modern kimlik doğrulamasını destekler. Microsoft 365 veya Microsoft 365 GCC bir kuruluşsanız betiği olduğu gibi kullanabilirsiniz. Office 365 Almanya kuruluşu, Microsoft 365 GCC High kuruluşu veya Microsoft 365 DoD kuruluşuysanız, betiği başarıyla çalıştırmak için düzenlemeniz gerekir. Özellikle, Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmak için satırı `Connect-IPPSSession` düzenlemeniz ve *ConnectionUri* ve *AzureADAuthorizationEndpointUri* parametrelerini (ve kuruluşunuzun türü için uygun değerleri) kullanmanız gerekir. Daha fazla bilgi için [bkz. Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa) örnekleri.

- Betiğin Güvenlik & Uyumluluk Merkezi PowerShell ve SharePoint Online Management Shell bağlantısı otomatik olarak kesilir.

- Betik en az hata işleme içerir. Birincil amacı, her kullanıcının posta kutusunu ve OneDrive İş sitesini hızlı ve kolay bir şekilde beklemeye almaktır.

- Bu konuda sağlanan örnek betikler, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betikler, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiklerin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>1. Adım: SharePoint Online Management Shell'i yükleme

İlk adım, yerel bilgisayarınızda yüklü değilse SharePoint Çevrimiçi Yönetim Kabuğu'nun yüklenmesidir. Bu yordamda kabuğu kullanmanız gerekmez, ancak 3. Adımda çalıştırdığınız betiğin gerektirdiği önkoşulları içerdiğinden bunu yüklemeniz gerekir. Bu önkoşullar, betiğin OneDrive İş sitelerinin URL'lerini almak için SharePoint Online ile iletişim kurmasına olanak sağlar.
  
[SharePoint Çevrimiçi Yönetim Kabuğu Windows PowerShell ortamını ayarlama'ya](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) gidin ve SharePoint Online Management Shell'i yerel bilgisayarınıza yüklemek için 1. ve 2. Adım'ı gerçekleştirin.

## <a name="step-2-generate-a-list-of-users"></a>2. Adım: Kullanıcıların listesini oluşturma

3. Adım'daki betik, eBulma olayıyla ilişkili bir ayrı tutma oluşturur ve bir kullanıcı listesinin posta kutularını ve OneDrive İş sitelerini ayrı tutmaya ekler. E-posta adreslerini bir metin dosyasına yazabilir veya Windows PowerShell'da bir komut çalıştırarak e-posta adreslerinin listesini alabilir ve bir dosyaya kaydedebilirsiniz (betiği 3. Adımda kaydedebileceğiniz klasörde bulunur).
  
Kuruluşunuzdaki tüm kullanıcıların e-posta adreslerinin listesini almak ve HoldUsers.txt adlı bir metin dosyasına kaydetmek için bir PowerShell komutu (Exchange Online kuruluşunuza bağlı uzak PowerShell kullanarak çalıştırılır).
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Bu komutu çalıştırdıktan sonra, metin dosyasını açın ve özellik adını içeren üst bilgiyi kaldırın. `PrimarySmtpAddress` Ardından, 3. Adımda oluşturacağınız ayrı tutmaya eklemek istediğiniz kullanıcılar dışındaki tüm e-posta adreslerini kaldırın. E-posta adresleri listesinden önce veya sonra boş satır olmadığından emin olun.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>3. Adım: Betiği çalıştırarak ayrı tutma oluşturma ve kullanıcı ekleme

Bu adımda betiği çalıştırdığınızda sizden aşağıdaki bilgileri isteyecektir. Betiği çalıştırmadan önce bu bilgilerin hazır olduğundan emin olun.
  
- **Kullanıcı kimlik bilgileriniz:** Betik, PowerShell ile Güvenlik & Uyumluluk Merkezi'ne bağlanmak için kimlik bilgilerinizi kullanır. Kullanıcı listesinin OneDrive İş URL'lerini almak üzere SharePoint Online'a erişmek için de bu kimlik bilgilerini kullanır.

- **SharePoint etki alanınızın adı:** Betik, <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezine</a> bağlanabilmesi için bu adı girmenizi ister. Ayrıca kuruluşunuzdaki OneDrive URL'leri için etki alanı adını kullanır. Örneğin, yönetim merkezinizin `https://contoso-admin.sharepoint.com` URL'si ve OneDrive URL'si ise`https://contoso-my.sharepoint.com`, betik sizden etki alanı adınızı isterse girersiniz`contoso`.

- **Servis talebinin adı:** Mevcut bir servis talebinin adı. Betik, bu servis talebiyle ilişkili yeni bir ayrı tutma oluşturur.

- **Ayrı tutmanın adı:** Betiği tutma adı oluşturulur ve belirtilen servis talebiyle ilişkilendirilecektir.

- **Sorgu tabanlı ayrı tutma için arama sorgusu:** Yalnızca belirtilen arama ölçütlerini karşılayan içeriğin beklemeye alınabilmesi için sorgu tabanlı bir ayrı tutma oluşturabilirsiniz. Tüm içeriği beklemeye almak için, arama sorgusu istendiğinde **Enter tuşuna** basmanız gerekir.

- **Ayrı tutmayı açma veya açmama:** Betiğin oluşturulduktan sonra ayrı tutma özelliğini açmasını sağlayabilir veya betiğin etkinleştirmeden ayrı tutma oluşturmasını sağlayabilirsiniz. Betiği ayrı tutmada açmadıysanız, Microsoft 365 uyumluluk merkezi daha sonra veya aşağıdaki PowerShell komutlarını çalıştırarak açabilirsiniz:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Kullanıcı listesini içeren metin dosyasının** adı - 2. Adım'da yer alan ve ayrı tutmaya eklenecek kullanıcıların listesini içeren metin dosyasının adı. Bu dosya betikle aynı klasörde yer alıyorsa, dosyanın adını yazmanız (örneğin, HoldUsers.txt). Metin dosyası başka bir klasördeyse, dosyanın tam yol adını yazın.

Betiğin sizden soracağı bilgileri topladıktan sonra, son adım betiği çalıştırarak yeni ayrı tutma oluşturmak ve kullanıcılar eklemektir.
  
1. dosya adı soneki `.ps1`kullanarak aşağıdaki metni Windows PowerShell betik dosyasına kaydedin. Örneğin, `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   Core eDiscovery cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
write-host "***********************************************"
" "
# Connect to SCC PowerShell using modern authentication
if (!$SccSession)
{
  Import-Module ExchangeOnlineManagement
  Connect-IPPSSession
}

# Get the organization's domain name. We use this to create the SharePoint admin URL and root URL for OneDrive for Business.
""
$mySiteDomain = Read-Host "Enter the domain name for your SharePoint organization. We use this name to connect to SharePoint admin center and for the OneDrive URLs in your organization. For example, 'contoso' in 'https://contoso-admin.sharepoint.com' and 'https://contoso-my.sharepoint.com'"
""

# Connect to PnP Online using modern authentication
Import-Module PnP.PowerShell
Connect-PnPOnline -Url https://$mySiteDomain-admin.sharepoint.com -UseWebLogin

# Load the SharePoint assemblies from the SharePoint Online Management Shell
# To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
{
    $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
    $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
    $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
    if (!$SharePointClient)
    {
        Write-Error "The SharePoint Online Management Shell isn't installed. Please install it from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then re-run this script."
        return;
    }
}

# Get other required information
do{
$casename = Read-Host "Enter the name of the case"
$caseexists = (get-compliancecase -identity "$casename" -erroraction SilentlyContinue).isvalid
if($caseexists -ne 'True')
{""
write-host "A case named '$casename' doesn't exist. Please specify the name of an existing case, or create a new case and then re-run the script." -foregroundColor Yellow
""}
}While($caseexists -ne 'True')
""
do{
$holdName = Read-Host "Enter the name of the new hold"
$holdexists=(get-caseholdpolicy -identity "$holdname" -case "$casename" -erroraction SilentlyContinue).isvalid
if($holdexists -eq 'True')
{""
write-host "A hold named '$holdname' already exists. Please specify a new hold name." -foregroundColor Yellow
""}
}While($holdexists -eq 'True')
""
$holdQuery = Read-Host "Enter a search query to create a query-based hold, or press Enter to hold all content"
""
$holdstatus = read-host "Do you want the hold enabled after it's created? (Yes/No)"
do{
""
$inputfile = read-host "Enter the name of the text file that contains the email addresses of the users to add to the hold"
""
$fileexists = test-path -path $inputfile
if($fileexists -ne 'True'){write-host "$inputfile doesn't exist. Please enter a valid file name." -foregroundcolor Yellow}
}while($fileexists -ne 'True')
#Import the list of addresses from the txt file.  Trim any excess spaces and make sure all addresses 
    #in the list are unique.
  [array]$emailAddresses = Get-Content $inputfile -ErrorAction SilentlyContinue | where {$_.trim() -ne ""}  | foreach{ $_.Trim() }
  [int]$dupl = $emailAddresses.count
  [array]$emailAddresses = $emailAddresses | select-object -unique
  $dupl -= $emailAddresses.count
#Validate email addresses so the hold creation does not run in to an error.
if($emailaddresses.count -gt 0){
write-host ($emailAddresses).count "addresses were found in the text file. There were $dupl duplicate entries in the file." -foregroundColor Yellow
""
Write-host "Validating the email addresses. Please wait..." -foregroundColor Yellow
""
$finallist =@()
foreach($emailAddress in $emailAddresses)
{
if((get-recipient $emailaddress -erroraction SilentlyContinue).isvalid -eq 'True')
{$finallist += $emailaddress}
else {"Unable to find the user $emailaddress"
[array]$excludedlist += $emailaddress}
}
""
#Find user's OneDrive account URL using email address
Write-Host "Getting the URL for each user's OneDrive for Business site." -foregroundColor Yellow 
""
$AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
$mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
$urls = @()
foreach($emailAddress in $finallist)
{
try
{
$url=Get-PnPUserProfileProperty -Account $emailAddress | Select PersonalUrl
$urls += $url.PersonalUrl
       Write-Host "- $emailAddress => $url"
       [array]$ODadded += $url.PersonalUrl
       }catch { 
 Write-Warning "Could not locate OneDrive for $emailAddress"
 [array]$ODExluded += $emailAddress
 Continue }
}
$urls | FL
if(($finallist.count -gt 0) -or ($urls.count -gt 0)){
""
Write-Host "Creating the hold named $holdname. Please wait..." -foregroundColor Yellow
if(($holdstatus -eq "Y") -or ($holdstatus -eq  "y") -or ($holdstatus -eq "yes") -or ($holdstatus -eq "YES")){
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $True | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery | out-null
}
else{
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $false | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery -disabled $false | out-null
}
""
}
else {"No valid locations were identified. Therefore, the hold wasn't created."}
#write log files (if needed)
$newhold=Get-CaseHoldPolicy -Identity "$holdname" -Case "$casename" -erroraction SilentlyContinue
$newholdrule=Get-CaseHoldRule -Identity "$holdName" -erroraction SilentlyContinue
if(($ODAdded.count -gt 0) -or ($ODExluded.count -gt 0) -or ($finallist.count -gt 0) -or ($excludedlist.count -gt 0) -or ($newhold.isvalid -eq 'True') -or ($newholdrule.isvalid -eq 'True'))
{
Write-Host "Generating output files..." -foregroundColor Yellow
if($ODAdded.count -gt 0){
"OneDrive Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.SharePointLocation.name | add-content .\LocationsOnHold.txt}
if($ODExluded.count -gt 0){ 
"Users without OneDrive locations" | add-content .\LocationsNotOnHold.txt
"================================" | add-content .\LocationsNotOnHold.txt
$ODExluded | add-content .\LocationsNotOnHold.txt}
if($finallist.count -gt 0){
" " | add-content .\LocationsOnHold.txt
"Exchange Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.ExchangeLocation.name | add-content .\LocationsOnHold.txt}
if($excludedlist.count -gt 0){
" "| add-content .\LocationsNotOnHold.txt
"Mailboxes not added to the hold" | add-content .\LocationsNotOnHold.txt
"===============================" | add-content .\LocationsNotOnHold.txt
$excludedlist | add-content .\LocationsNotOnHold.txt}
$FormatEnumerationLimit=-1
if($newhold.isvalid -eq 'True'){$newhold|fl >.\GetCaseHoldPolicy.txt}
if($newholdrule.isvalid -eq 'True'){$newholdrule|Fl >.\GetCaseHoldRule.txt}
}
}
else {"The hold wasn't created because no valid entries were found in the text file."}
""
#Disconnect from SCC PowerShell and PnPOnline

Write-host "Disconnecting from SCC PowerShell and PnP Online" -foregroundColor Yellow
Get-PSSession | Remove-PSSession
Disconnect-PnPOnline

Write-host "Script complete!" -foregroundColor Yellow
""
#script end
```

2. Yerel bilgisayarınızda Windows PowerShell açın ve betiği kaydettiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Betiğin sizden sorduğunu bilgileri girin.

   Betik, Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanır ve eBulma durumunda yeni ayrı tutma oluşturur ve listedeki kullanıcılar için posta kutularını ve OneDrive İş ekler. Yeni ayrı tutma işlemini görüntülemek için Microsoft 365 uyumluluk merkezi **eBulma** sayfasında servis talebine gidebilirsiniz.

Betiğin çalışması tamamlandıktan sonra aşağıdaki günlük dosyalarını oluşturur ve betiğin bulunduğu klasöre kaydeder.
  
- **LocationsOnHold.txt:** Betiğin başarıyla beklemeye aldığı posta kutularının ve OneDrive İş sitelerinin listesini içerir.

- **LocationsNotOnHold.txt:** Betiğin beklemeye almadığı posta kutularının ve OneDrive İş sitelerin listesini içerir. Kullanıcının posta kutusu varsa ancak OneDrive İş sitesi yoksa, kullanıcı beklemeye alınmamış OneDrive İş siteleri listesine eklenir.

- **GetCaseHoldPolicy.txt:** Yeni ayrı tutma oluşturulduktan sonra betiğin çalıştırıldığı yeni ayrı tutma için **Get-CaseHoldPolicy** cmdlet'inin çıkışını içerir. Bu cmdlet tarafından döndürülen bilgiler, posta kutuları ve OneDrive İş siteleri ayrı tutmanın etkinleştirilip etkinleştirilmediğini ve devre dışı bırakılıp bırakılmadığını içeren kullanıcıların listesini içerir. 

- **GetCaseHoldRule.txt:** Yeni ayrı tutma oluşturulduktan sonra betiğin çalıştırıldığı yeni ayrı tutma için **Get-CaseHoldRule** cmdlet'inin çıkışını içerir. Bu cmdlet tarafından döndürülen bilgiler, sorgu tabanlı ayrı tutma oluşturmak için betiği kullandıysanız arama sorgusunu içerir.
