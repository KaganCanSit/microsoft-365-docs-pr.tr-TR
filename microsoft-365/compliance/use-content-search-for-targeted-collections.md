---
title: Hedeflenen koleksiyonlar için İçerik aramasını kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
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
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Belirli bir posta kutusu veya site klasöründeki öğeleri arayan hedefli bir koleksiyon gerçekleştirmek için Microsoft Purview uyumluluk portalındaki İçerik arama özelliğini kullanın.
ms.openlocfilehash: 224da8e651599d1d007684a069b0dbb9d30a6119
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015550"
---
# <a name="use-content-search-for-targeted-collections"></a>Hedeflenen koleksiyonlar için İçerik aramasını kullanma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalındaki İçerik arama aracı, kullanıcı arabiriminde Exchange posta kutularındaki veya SharePoint ve OneDrive İş sitelerdeki belirli klasörleri aramak için doğrudan bir yol sağlamaz. Ancak, gerçek arama sorgusu söz dizimindeki siteler için e-posta veya yol (DocumentLink) özelliği için klasör kimliği özelliğini belirterek belirli klasörlerde ( *hedeflenen koleksiyon* olarak adlandırılır) arama yapmak mümkündür. Hedeflenen bir koleksiyonu gerçekleştirmek için İçerik Arama'yı kullanmak, büyük/küçük harfe veya ayrıcalıklı öğelere yanıt veren öğelerin belirli bir posta kutusunda veya site klasöründe bulunduğundan emin olduğunuzda kullanışlıdır. Posta kutusu klasörlerinin klasör kimliğini veya bir SharePoint ve OneDrive İş sitesindeki klasörlerin yolunu (DocumentLink) almak için bu makaledeki betiği kullanabilirsiniz. Ardından, klasörde bulunan öğeleri döndürmek için bir arama sorgusundaki klasör kimliğini veya yolunu kullanabilirsiniz.

> [!NOTE]
> SharePoint veya OneDrive İş sitedeki bir klasörde bulunan içeriği döndürmek için, bu konudaki betik Path özelliği yerine DocumentLink yönetilen özelliğini kullanır. DocumentLink özelliği, bir klasördeki tüm içeriği döndüreceği için Path özelliğinden daha sağlamdır, Path özelliği ise bazı medya dosyalarını döndürmez.

## <a name="before-you-run-a-targeted-collection"></a>Hedeflenen bir koleksiyonu çalıştırmadan önce

- 1. Adımda betiği çalıştırmak için uyumluluk portalında eBulma Yöneticisi rol grubunun üyesi olmanız gerekir. Daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

- Ayrıca, Exchange Online kuruluşunuzda Posta Alıcıları rolüne de atanmış olmanız gerekir. Betikte bulunan **Get-MailboxFolderStatistics** cmdlet'ini çalıştırmak için bu gereklidir. Varsayılan olarak, Posta Alıcıları rolü Exchange Online'deki Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır. Exchange Online izin atama hakkında daha fazla bilgi için bkz. [Rol grubu üyelerini yönetme](/exchange/manage-role-group-members-exchange-2013-help). Ayrıca özel bir rol grubu oluşturabilir, buna Posta Alıcıları rolünü atayabilir ve ardından 1. Adımda betiği çalıştırması gereken üyeleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [Rol gruplarını yönetme](/Exchange/permissions-exo/role-groups).

- Bu makaledeki betik modern kimlik doğrulamasını destekler. Microsoft 365 veya Microsoft 365 GCC bir kuruluşsanız betiği olduğu gibi kullanabilirsiniz. Office 365 Almanya kuruluşu, Microsoft 365 GCC High kuruluşu veya Microsoft 365 DoD kuruluşuysanız, betiği başarıyla çalıştırmak için düzenlemeniz gerekir. Özellikle, Exchange Online PowerShell'e bağlanmak için satırı `Connect-ExchangeOnline` düzenlemeniz ve *ExchangeEnvironmentName* parametresini (ve kuruluşunuzun türü için uygun değeri) kullanmanız gerekir.  Ayrıca, Güvenlik & Uyumluluğu PowerShell'e bağlanmak için satırı `Connect-IPPSSession` düzenlemeniz ve *ConnectionUri* ve *AzureADAuthorizationEndpointUri* parametrelerini (ve kuruluşunuzun türü için uygun değerleri) kullanmanız gerekir. Daha fazla bilgi için [PowerShell'i Exchange Online ve Güvenlik &](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) [Uyumluluğu PowerShell'e Bağlan için Bağlan örneklerine](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa) bakın.

- Betiği her çalıştırdığınızda yeni bir uzak PowerShell oturumu oluşturulur. Bu, kullanabileceğiniz tüm uzak PowerShell oturumlarını kullanabileceğiniz anlamına gelir. Bunun olmasını önlemek için, etkin uzak PowerShell oturumlarınızın bağlantısını kesmek için aşağıdaki komutları çalıştırın.

  ```powershell
  Get-PSSession | Remove-PSSession; Disconnect-ExchangeOnline
  ```

    Daha fazla bilgi için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Betik en az hata işleme içerir. Betiğin birincil amacı, hedeflenen bir koleksiyonu gerçekleştirmek için İçerik Arama'nın arama sorgusu söz diziminde kullanılabilecek posta kutusu klasör kimliklerinin veya site yollarının listesini hızla görüntülemektir.

- Bu konuda sağlanan örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>1. Adım: Posta kutusu veya site için klasörlerin listesini almak için betiği çalıştırın

Bu ilk adımda çalıştırdığınız betik, posta kutusu klasörlerinin veya SharePoint ve OneDrive İş klasörlerin listesini ve her klasörün ilgili klasör kimliğini veya yolunu döndürür. Bu betiği çalıştırdığınızda sizden aşağıdaki bilgileri ister.

- **E-posta adresi veya site URL'si**: posta kutusu klasörlerinin ve klasör kimliklerinin listesini Exchange için koruyucunun e-posta adresini yazın. Veya bir SharePoint sitesinin URL'sini veya belirtilen sitenin yollarının listesini döndürmek için OneDrive İş bir sitenin URL'sini yazın. İşte birkaç örnek:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive İş**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Kullanıcı kimlik bilgileriniz**: Betik, modern kimlik doğrulaması kullanarak Exchange Online PowerShell'e veya Güvenlik & Uyumluluk PowerShell'e bağlanmak için kimlik bilgilerinizi kullanır. Daha önce açıklandığı gibi, bu betiği başarıyla çalıştırmak için size uygun izinler atanmalıdır.

Posta kutusu klasörlerinin veya site belge bağlantısı (yol) adlarının listesini görüntülemek için:

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the compliance portal.            #
   # The script will then:                                            #
   #    * If an email address is supplied: list the folders for the target mailbox.            #
   #    * If a SharePoint or OneDrive for Business site is supplied: list the documentlinks (folder paths) #
   #    * for the site.                                                                                    #
   #    * In both cases, the script supplies the correct search properties (folderid: or documentlink:)    #
   #      appended to the folder ID or documentlink to use in a Content Search.                #
   # Notes:                                                #
   #    * For SharePoint and OneDrive for Business, the paths are searched recursively; this means the     #
   #      the current folder and all sub-folders are searched.                        #
   #    * For Exchange, only the specified folder will be searched; this means sub-folders in the folder    #
   #      will not be searched.  To search sub-folders, you need to use the specify the folder ID for    #
   #      each sub-folder that you want to search.                                #
   #    * For Exchange, only folders in the user's primary mailbox will be returned by the script.        #
   #########################################################################################################
   # Collect the target email address or SharePoint Url
   $addressOrSite = Read-Host "Enter an email address or a URL for a SharePoint or OneDrive for Business site"
   # Authenticate with Exchange Online and the compliance portal (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline -ShowBanner:$false -CommandName Get-MailboxFolderStatistics
      }
      $folderQueries = @()
      $folderStatistics = Get-MailboxFolderStatistics $emailAddress
      foreach ($folderStatistic in $folderStatistics)
      {
          $folderId = $folderStatistic.FolderId;
          $folderPath = $folderStatistic.FolderPath;
          $encoding= [System.Text.Encoding]::GetEncoding("us-ascii")
          $nibbler= $encoding.GetBytes("0123456789ABCDEF");
          $folderIdBytes = [Convert]::FromBase64String($folderId);
          $indexIdBytes = New-Object byte[] 48;
          $indexIdIdx=0;
          $folderIdBytes | select -skip 23 -First 24 | %{$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -shr 4];$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -band 0xF]}
          $folderQuery = "folderid:$($encoding.GetString($indexIdBytes))";
          $folderStat = New-Object PSObject
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderPath -Value $folderPath
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderQuery -Value $folderQuery
          $folderQueries += $folderStat
      }
      Write-Host "-----Exchange Folders-----"
      $folderQueries |ft
   }
   elseif ($addressOrSite.IndexOf("http") -ige 0)
   {
      $searchName = "SPFoldersSearch"
      $searchActionName = "SPFoldersSearch_Preview"
      # List the folders for the SharePoint or OneDrive for Business Site
      $siteUrl = $addressOrSite
      # Connect to Security & Compliance PowerShell
      if (!$SccSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-IPPSSession
      }
      # Clean-up, if the script was aborted, the search we created might not have been deleted.  Try to do so now.
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
      # Create a Content Search against the SharePoint Site or OneDrive for Business site and only search for folders; wait for the search to complete
      $complianceSearch = New-ComplianceSearch -Name $searchName -ContentMatchQuery "contenttype:folder" -SharePointLocation $siteUrl
      Start-ComplianceSearch $searchName
      do{
          Write-host "Waiting for search to complete..."
          Start-Sleep -s 5
          $complianceSearch = Get-ComplianceSearch $searchName
      }while ($complianceSearch.Status -ne 'Completed')
      if ($complianceSearch.Items -gt 0)
      {
          # Create a Compliance Search Action and wait for it to complete. The folders will be listed in the .Results parameter
          $complianceSearchAction = New-ComplianceSearchAction -SearchName $searchName -Preview
          do
          {
              Write-host "Waiting for search action to complete..."
              Start-Sleep -s 5
              $complianceSearchAction = Get-ComplianceSearchAction $searchActionName
          }while ($complianceSearchAction.Status -ne 'Completed')
          # Get the results and print out the folders
          $results = $complianceSearchAction.Results
          $matches = Select-String "Data Link:.+[,}]" -Input $results -AllMatches
          foreach ($match in $matches.Matches)
          {
              $rawUrl = $match.Value
              $rawUrl = $rawUrl -replace "Data Link: " -replace "," -replace "}"
              Write-Host "DocumentLink:""$rawUrl"""
          }
      }
      else
      {
          Write-Host "No folders were found for $siteUrl"
      }
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
   }
   else
   {
      Write-Error "Couldn't recognize $addressOrSite as an email address or a site URL"
   }
   ```

2. Yerel bilgisayarınızda Windows PowerShell açın ve betiği kaydettiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Betiğin sizden sorduğunu bilgileri girin.

    Betik, belirtilen kullanıcı için posta kutusu klasörlerinin veya site klasörlerinin listesini görüntüler. Klasör kimliğini veya belge bağlantısı adını kopyalayıp 2. Adımda bir arama sorgusuna yapıştırabilmek için bu pencereyi açık bırakın.

    > [!TIP]
    > Bilgisayar ekranında klasörlerin listesini görüntülemek yerine, betiğin çıkışını bir metin dosyasına yeniden yönlendirebilirsiniz. Bu dosya, betiğin bulunduğu klasöre kaydedilir. Örneğin, betik çıkışını bir metin dosyasına yeniden yönlendirmek için 3. Adım'da aşağıdaki komutu çalıştırın:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Ardından, bir arama sorgusunda kullanmak üzere dosyadan klasör kimliğini veya belge bağlantısını kopyalayabilirsiniz.

### <a name="script-output-for-mailbox-folders"></a>Posta kutusu klasörleri için betik çıkışı

Posta kutusu klasör kimliklerini alıyorsanız, betik Exchange Online PowerShell'e bağlanır, **Get-MailboxFolderStatisics** cmdlet'ini çalıştırır ve ardından belirtilen posta kutusundan klasörlerin listesini görüntüler. Posta kutusundaki her klasör için betik, **KlasörYolu** sütunundaki klasörün adını ve **FolderQuery** sütununda klasör kimliğini görüntüler. Ayrıca, betik klasör kimliğine **folderId** (posta kutusu özelliğinin adıdır) ön ekini ekler. **folderid** özelliği aranabilir bir özellik olduğundan, bu klasörü aramak için 2. Adım'daki bir arama sorgusunda kullanacaksınız`folderid:<folderid>`. 

> [!IMPORTANT]
> Bu makaledeki betik, **Get-MailboxFolderStatistics** tarafından döndürülen 64 karakterlik klasör kimliği değerlerini arama için dizine alınan 48 karakterlik biçime dönüştüren kodlama mantığını içerir. Klasör kimliğini almak için PowerShell'de **Get-MailboxFolderStatistics** cmdlet'ini çalıştırırsanız (bu makaledeki betiği çalıştırmak yerine), bu klasör kimliği değerini kullanan bir arama sorgusu başarısız olur. İçerik Aramasında kullanılabilecek doğru biçimlendirilmiş klasör kimliklerini almak için betiği çalıştırmanız gerekir.

Posta kutusu klasörleri için betik tarafından döndürülen çıktının bir örneği aşağıda verilmiştır.

![Betik tarafından döndürülen posta kutusu klasörleri ve klasör kimlikleri listesi örneği.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

2. Adım'daki örnek, kullanıcının Kurtarılabilir Öğeler klasöründeki Temizlemeler alt klasöründe arama yapmak için kullanılan sorguyu gösterir.

### <a name="script-output-for-site-folders"></a>Site klasörleri için betik çıkışı

**documentlink** özelliğinin yolunu SharePoint veya OneDrive İş sitelerden alıyorsanız, betik Güvenlik & Uyumluluğu PowerShell'e bağlanır, sitede klasörler için arama yapılan yeni bir İçerik Araması oluşturur ve ardından belirtilen sitede bulunan klasörlerin listesini görüntüler. Betik her klasörün adını görüntüler ve **belge bağlantısının** ön ekini klasör URL'sine ekler. **Documentlink** özelliği aranabilir bir özellik olduğundan, bu klasörde arama yapmak için 2. Adım'daki bir arama sorgusunda property:value çiftini kullanacaksınız`documentlink:<path>`. Betik en fazla 100 site klasörü görüntüler. 100'den fazla site klasörü varsa, en yeni klasörler görüntülenir.

Aşağıda, site klasörleri için betik tarafından döndürülen çıktının bir örneği verilmiştır.

![Betik tarafından döndürülen site klasörleri için belge bağlantısı adlarının listesi örneği.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>2. Adım: Hedeflenen koleksiyonu gerçekleştirmek için klasör kimliği veya belge bağlantısı kullanma

Belirli bir kullanıcının klasör kimliklerinin veya belge bağlantılarının listesini toplamak üzere betiği çalıştırdıktan sonra, uyumluluk portalına gidip belirli bir klasörde arama yapmak üzere yeni bir İçerik Araması oluşturmak için sonraki adım. İçerik Arama anahtar sözcüğü kutusunda yapılandırdığınız arama sorgusunda veya `documentlink:<path>` property:value çiftini kullanacaksınız `folderid:<folderid>` (veya **New-ComplianceSearch** cmdlet'ini kullanıyorsanız *ContentMatchQuery* parametresinin değeri olarak). veya `documentlink` özelliğini diğer arama parametreleri veya arama koşullarıyla birleştirebilirsiniz`folderid`. Sorguya  `folderid` yalnızca veya  `documentlink` özelliğini eklerseniz, arama belirtilen klasörde bulunan tüm öğeleri döndürür.

1. <https://compliance.microsoft.com> 1. Adımda betiği çalıştırmak için kullandığınız hesabı ve kimlik bilgilerini kullanarak gidin ve oturum açın.

2. Uyumluluk merkezinin sol bölmesinde **Tüm** > **İçerik aramasını** göster'e ve ardından **Yeni arama'ya** tıklayın.

3. **Anahtar Sözcükler** kutusuna, 1. Adım'da betik tarafından döndürülen veya `documentlink:<path>/*` değerini yapıştırın`folderid:<folderid>`.

    Örneğin, aşağıdaki ekran görüntüsündeki sorgu kullanıcının Kurtarılabilir Öğeler klasöründeki Temizlemeler alt klasöründeki herhangi bir öğeyi arar (Temizleme alt klasörünün `folderid` özelliği 1. Adım'daki ekran görüntüsünde gösterilir):

    ![folderid veya documentlink dosyasını arama sorgusunun anahtar sözcük kutusuna yapıştırın.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > documentlink aramaları, sondaki  `asterisk '/*'`bir öğesinin kullanılmasını gerektirir.  

4. **Konumlar'ın** altında **Belirli konumlar'ı** seçin ve **değiştir'e** tıklayın.

5. Posta kutusu klasöründe mi yoksa site klasöründe mi arama yaptığınıza bağlı olarak aşağıdakilerden birini yapın:

    - **E-posta Exchange** yanında **Kullanıcıları, grupları veya ekipleri seç'e** tıklayın ve ardından 1. Adımda betiği çalıştırdığınızda belirttiğiniz posta kutusunu ekleyin.

      Veya

    - **siteleri SharePoint** yanında **Siteleri seç'e** tıklayın ve ardından 1. Adımda betiği çalıştırdığınızda belirttiğiniz site URL'sini ekleyin.

6. Arama yapmak için içerik konumunu kaydettikten sonra **Kaydet'e tıklayın & çalıştırın**, İçerik Araması için bir ad yazın ve hedeflenen koleksiyon aramasını başlatmak için **Kaydet'e** tıklayın.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Hedeflenen koleksiyonlar için arama sorguları örnekleri

Aşağıda, hedeflenen bir koleksiyonu gerçekleştirmek için bir arama sorgusunda ve `documentlink` özelliklerini kullanmaya `folderid` ilişkin bazı örnekler verilmiştir. Yer tutucular yer kazanmak için ve `documentlink:<path>` için `folderid:<folderid>` kullanılır.

- Bu örnekte üç farklı posta kutusu klasörü aranmaktadır. Kullanıcının Kurtarılabilir Öğeler klasöründeki gizli klasörlerde arama yapmak için benzer sorgu söz dizimini kullanabilirsiniz.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- Bu örnekte, posta kutusu klasöründe tam tümcecik içeren öğeler aranmaktadır.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- Bu örnek, bir site klasöründe (ve tüm alt klasörlerde) başlıkta "NDA" harflerini içeren belgeleri arar.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- Bu örnekte, bir tarih aralığında değiştirilmiş belgeler için site klasöründe (ve herhangi bir alt klasörde) arama yapılmıştır.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Daha fazla bilgi

Hedeflenen koleksiyonları gerçekleştirmek için bu makaledeki betiği kullanırken aşağıdakileri göz önünde bulundurun.

- Betik, sonuçlardan hiçbir klasörü kaldırmaz. Bu nedenle, sonuçlarda listelenen bazı klasörler, sistem tarafından oluşturulan içerik içerdiğinden veya posta kutusu öğelerini değil yalnızca alt klasörler içerdiğinden, arama yapılamayabilir (veya sıfır öğe döndürebilir).

- Bu betik yalnızca kullanıcının birincil posta kutusu için klasör bilgilerini döndürür. Kullanıcının arşiv posta kutusunda klasörler hakkında bilgi döndürmez. Kullanıcının arşiv posta kutusunda klasörler hakkında bilgi döndürmek için betiği düzenleyebilirsiniz. Bunu yapmak için satırı `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` olarak `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` değiştirin ve ardından düzenlenen betiği kaydedip çalıştırın. Bu değişiklik, kullanıcının arşiv posta kutusunda klasörler ve alt klasörler için klasör kimliklerini döndürür. Arşiv posta kutusunun tamamında arama yapmak için, tüm klasör kimliği özelliği:değer çiftlerini arama sorgusundaki bir `OR` işleçle bağlayabilirsiniz.

- Posta kutusu klasörlerinde arama yaparken yalnızca belirtilen klasör (özelliğiyle `folderid` tanımlanır) aranacak; alt klasörler aranmayacak. Alt klasörleri aramak için, aramak istediğiniz alt klasörün klasör kimliğini kullanmanız gerekir.

- Site klasörlerinde arama yaparken, klasör (özelliğiyle `documentlink` tanımlanır) ve tüm alt klasörler aranacaktır.

- Arama sorgusunda yalnızca özelliğini belirttiğiniz `folderid` bir aramanın sonuçlarını dışarı aktarırken, "Tanınmayan biçime sahip olanlar hariç tüm öğeler şifrelenir veya başka nedenlerle dizine eklenmedi", ilk dışarı aktarma seçeneğini belirleyebilirsiniz. Klasör kimliği her zaman dizine alınacağından, klasördeki tüm öğeler dizin oluşturma durumlarına bakılmaksızın her zaman dışarı aktarılır.
