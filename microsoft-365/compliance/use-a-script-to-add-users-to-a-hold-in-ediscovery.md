---
title: Core eKovery durumunda kullanıcıları tik olarak tutmak için betik kullanma
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
description: Bir betiği çalıştırarak sitelerde yer alan posta kutularını & OneDrive İş bir eBulma durumuyla ilişkilendirilmiş yeni bir tutma durumuna nasıl Microsoft 365 uyumluluk merkezi.
ms.openlocfilehash: fd11ccb6c262cd0e31a65d2a1f95d5dbcd92869c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314567"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Core eKovery durumunda kullanıcıları tik olarak tutmak için betik kullanma

Güvenlik & Uyumluluk Merkezi PowerShell, eBulma olaylarını oluşturma ve yönetmeyle ilgili zaman alıcı görevleri otomatikleştirmenize izin veren cmdlet'ler sağlar. Şu anda, çok fazla sayıda özel kişi içerik konumu Microsoft 365 uyumluluk merkezi durumda Çekirdek eKbulma durumu kullanmak zaman ve hazırlık aşamasındadır. Örneğin, yerinde tutma oluşturmadan önce, yerinde OneDrive İş her sitenin URL'sini toplamalı. Ardından yerinde tutmak istediğiniz her kullanıcı için, o kullanıcının posta kutusunu ve posta kutusunu OneDrive İş yerinde tutmanız gerekir. Bu işlemi otomatikleştirmek için bu makaledeki betiği kullanabilirsiniz.
  
Betik size, kuruluş sitem etki alanının adını ( `contoso` örneğin, URL'de https://contoso-my.sharepoint.com), var olan eBulma davanın adını, davayla ilişkilendirilmiş yeni tutmanın adını, yerinde tutmak istediğiniz kullanıcıların e-posta adreslerinin listesini ve sorgu tabanlı bir tutma oluşturmak istediğiniz bir arama sorgusunu) ister. Ardından betik, OneDrive İş sitesinin URL'sini alır, yeni tutma oluşturur ve ardından listeden her kullanıcının posta kutusunu OneDrive İş kutusunu ve OneDrive İş sitesini yerinde tutma olarak ekler. Betik, yeni tutma hakkında bilgi içeren günlük dosyalarını da üretir.
  
Bunu yapmak için gereken adımlar:
  
[1. Adım: SharePoint Online Yönetim Kabuğu'nu yükleme](#step-1-install-the-sharepoint-online-management-shell)
  
[2. Adım: Kullanıcı listesi oluşturma](#step-2-generate-a-list-of-users)
  
[3. Adım: Betiği çalıştırarak  tutma ve kullanıcıları ekleme](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Kullanıcıları  basılı tutmadan önce

- 3. Adımda betiği çalıştırmak için Microsoft 365 uyumluluk merkezi'de eBulma Yöneticisi rol grubunun bir üyesi SharePoint ve SharePoint Online yöneticisi olun. Daha fazla bilgi için bkz. Uyumluluk Merkezi'nde [eBulma izinleri Office 365 Güvenlik & atama](assign-ediscovery-permissions.md).

- Bir eBulma durumuyla ilişkilendirilmiş bir eBulma olaylarına en çok 1.000 posta kutusu ve 100 site Microsoft 365 uyumluluk merkezi. Yerinde yerinde tutmak istediğiniz her kullanıcının bir OneDrive İş sitesi olduğunu varsayarak, bu makaledeki betiği kullanarak 100 kullanıcıdan en fazla 100'lerini yerinde tutabilirsiniz.

- 2. Adımda oluştursunu kullanıcıların listesini ve 3. Adım'daki betiği de aynı klasöre kaydetmeye dikkat edin. Bu, betiği çalıştırmayı kolaylaştırır.

- Betik, kullanıcıların listesini var olan bir vakayla ilişkilendirilmiş yeni bir tutma durumuna ekler. Betiği çalıştırmadan önce, tutmak istediğiniz durumla ilişkilendirmek istediğiniz durumların oluşturulmuş olduğundan emin olun.

- Bu makaledeki betik, Güvenlik ve Uyumluluk Merkezi PowerShell'e & Çevrimiçi Yönetim Kabuğu'SharePoint destekler. Betiği olduğu gibi, bir çalışan veya Microsoft 365 Microsoft 365 GCC kullanabilirsiniz. Office 365 Germany kuruluşu, Microsoft 365 GCC Yüksek kuruluşu veya Microsoft 365 DoD kuruluşu isanız betiği düzenlemek ve başarılı bir şekilde çalıştırmak için gerekir. Özel olarak, `Connect-IPPSSession` Güvenlik ve Uyumluluk Merkezi PowerShell'e bağlanmak için satırı düzenlemeli ve *ConnectionUri* ile *AzureADAuthorizationEndpointUri* parametrelerini (ve kuruluş türünüz için uygun değerleri) & gerekir. Daha fazla bilgi için Güvenlik ve Uyumluluk [Bağlan PowerShell'& örneklere bakın](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Betiğin Güvenlik ve Uyumluluk Merkezi PowerShell& ve Çevrimiçi Yönetim Kabuğu SharePoint bağlantısı otomatik olarak kesilir.

- Betik en az hata işlemeyi içerir. Bunun birincil amacı, posta kutusunu ve kullanıcı OneDrive İş siteyi hızlı ve kolay bir şekilde yerinde tutmaktır.

- Bu konu başlığı altında verilen örnek betikler, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenemmektedir. Örnek betikler hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiklerin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>1. Adım: SharePoint Online Yönetim Kabuğu'nu yükleme

İlk adım, yerel bilgisayarınızda SharePoint Çevrimiçi Yönetim Kabuğu'nun yüklü olmasıdır. Bu yordamda kabuk kullanmak zorunda değilsiniz, ancak 3. Adımda çalıştıracakları betik için gerekli önkulları içerdiği için onu yüklemeniz gerekir. Bu önkoşullar betiğin SharePoint Online ile iletişim kurmasına olanak OneDrive İş sağlar.
  
[SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) Yönetim Kabuğu'Windows PowerShell ortamını ayarlama'ya gidin ve yerel bilgisayarınıza SharePoint Çevrimiçi Yönetim Kabuğu'SharePoint 1. Adımı ve 2. Adımı gerçekleştirin.

## <a name="step-2-generate-a-list-of-users"></a>2. Adım: Kullanıcı listesi oluşturma

3. Adım'daki betik, bir eBulma durumuyla ilişkilendirilmiş bir tutma durumu oluşturmanın yanı sıra posta kutularını ve kullanıcı listesinin OneDrive İş sitelerini de tutma için ekler. Metin dosyasına yalnızca e-posta adreslerini yazarak veya Windows PowerShell'te bir komut çalıştırarak e-posta adreslerinin listesini alın ve bunları bir dosyaya kaydedin (betiği 3. Adımda kaydeden aynı klasörde bulunur).
  
İşte bir PowerShell komutu (Exchange Online kuruluşuyla bağlantılı uzak PowerShell kullanarak çalıştırarak), kurumdaki tüm kullanıcıların e-posta adreslerinin listesini almak ve bunu HoldUsers.txt adlı bir metin dosyasına kaydetmek için kullanabilirsiniz.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Bu komutu çalıştırdikten sonra, metin dosyasını açın ve özellik adını içeren üstbilgiyi kaldırın,  `PrimarySmtpAddress`. Ardından, 3. Adımda oluştury istediğiniz kullanıcıların e-posta adreslerini kaldırın. E-posta adresleri listesinden önce veya sonra boş satırlar olmadığını kontrol edin.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>3. Adım: Betiği çalıştırarak  tutma ve kullanıcıları ekleme

Bu adımda betiği çalıştırınca, sizden aşağıdaki bilgileri istenir. Betiği çalıştırmadan önce bu bilgilerin hazır olduğundan emin olun.
  
- **Kullanıcı kimlik bilgileriniz:** Betik, PowerShell ile Güvenlik ve Uyumluluk Merkezi'ne & kimlik bilgilerinizi kullanır. Ayrıca, kullanıcı listesi için SharePoint Online'a erişmek OneDrive İş bu kimlik bilgilerini kullanır.

- **SharePoint etki SharePoint adı:** Betik, yönetim merkezinden bağlana kadar bu <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">adı SharePoint istiyor</a>. Ayrıca, kuruluş url'leri OneDrive alanı adını kullanır. Örneğin, yönetim merkezinizin URL'si `https://contoso-admin.sharepoint.com` ve yönetim merkezinin URL'si OneDrive `https://contoso-my.sharepoint.com``contoso` ise, betik sizden etki alanı adınızı isteminde geldiğinde siz de girersiniz.

- **Vakanın adı:** Var olan bir vakanın adı. Betik, bu vakayla ilişkilendirilmiş yeni bir tutma oluşturacak.

- **Tutma adı:** Betiğin basılı tutma adı, belirtilen vakayı oluşturabilir ve bu vakayla ilişkilendirilecek.

- **Sorgu tabanlı bir tutma sorgusu:** Sorgu tabanlı bir tutma oluşturabilir ve böylelikle yalnızca belirtilen arama ölçütlerine uyan içeriğin yerine basılı tutabilirsiniz. Tüm içeriği yerinde tutmak için, arama sorgusu girmeniz istendiğinde **Enter** tuşuna basmanız gerekir.

- **Tutmayı açma veya açmama:** Betiğin oluşturulduktan sonra 12 saat içinde etkinleştirilmesini veya betiğin etkinleştirilmeden  hold oluşturması s olabilir. Betiği basılı tutmanız yoksa, daha sonra Microsoft 365 uyumluluk merkezi veya aşağıdaki PowerShell komutlarını çalıştırarak açabilirsiniz:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Kullanıcı listesini içeren metin dosyasının adı** - 2. Adım'da yer alan ve tutma için ekleyebilirsiniz kullanıcı listesini içeren metin dosyasının adı. Bu dosya betikle aynı klasörde yer alıyorsa, yalnızca dosyanın adını yazmanız (örneğin, TamamHoldUsers.txt. Metin dosyası başka bir klasörde yer alan dosyanın tam yol adını yazın.

Betiğin sizden istenecek bilgileri topladığı zaman, son adım betiği çalıştırarak yeni  hold'i oluşturmak ve kullanıcı eklemektir.
  
1. dosya adı son eksini kullanarak Windows PowerShell betik dosyasına aşağıdaki metni kaydedin`.ps1`. Örneğin, `AddUsersToHold.ps1`.

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

2. Yerel bilgisayarınızda, Windows PowerShell açın ve betiği kaydedttiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Betiğin sizden istendiğinde bilgileri girin.

   Betik, Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanır, eBulma durumunda yeni tutma oluşturur ve posta kutularını ve posta kutularını OneDrive İş kullanıcıların listesini ekler. eBulma sayfasındaki **vakaya gidip** yeni Microsoft 365 uyumluluk merkezi görebilirsiniz.

Betiğin çalıştırması bittiğinde, aşağıdaki günlük dosyalarını oluşturur ve bunları betiğin bulunduğu klasöre kaydeder.
  
- **LocationsOnHold.txt:** Betiğin başarıyla beklemede OneDrive İş posta kutularının ve sitelerinin listesini içerir.

- **LocationsNotOnHold.txt:** Betiğin yerinde OneDrive İş posta kutularının ve diğer sitelerin listesini içerir. Kullanıcının bir posta kutusu varsa ancak OneDrive İş sitesi yoksa, kullanıcı yerinde OneDrive İş site listesine dahil edilir.

- **GetCaseHoldPolicy.txt:** Betiğin yeni tutma oluşturdukten sonra çalıştırıldı olan yeni tutma için **Get-CaseHoldPolicy** cmdlet'inin çıktısını içerir. Bu cmdlet'in döndürülen bilgilerinde, posta kutuları ve posta kutuları OneDrive İş sitelerine yerleştirildiğinde ve tutmanın etkinleştirildiğinde veya devre dışı bırakılmıştır. 

- **GetCaseHoldRule.txt:** **Get-CaseHoldRule** cmdlet'inin, betiğin yeni tutma oluşturdukten sonra çalıştırıldı olan yeni tutma çıktısını içerir. Bu cmdlet tarafından döndürülen bilgiler, sorgu tabanlı bir tutma oluşturmak için betiği kullandıysanız arama sorgusunu içerir.
