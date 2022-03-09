---
title: Hedeflenen koleksiyonlar için İçerik arama kullanma
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
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Belirli bir posta kutusu Microsoft 365 uyumluluk merkezi site klasöründe öğe araması yapacak bir hedefli koleksiyon gerçekleştirmek için, hedefli koleksiyondaki İçerik aramalarını kullanın.
ms.openlocfilehash: a72984e3d4363dfd5d89e6167621dd65c9d57653
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63406029"
---
# <a name="use-content-search-for-targeted-collections"></a>Hedeflenen koleksiyonlar için İçerik arama kullanma

Kullanıcı arabiriminde İçerik Microsoft 365 uyumluluk merkezi aracı, kullanıcı arabiriminde doğrudan Exchange kutuları veya klasörlerin veya sitelerde SharePoint OneDrive İş sağlamaz. Bununla birlikte, asıl arama sorgusu söz dizimsinde siteler için e-posta veya yol (DocumentLink *) özelliğini* belirterek belirli klasörlerde (hedefli koleksiyon olarak adlandırılan) arama yapmak mümkündür. İçerik Arama'nın, bir vakaya veya ayrıcalıklı öğelere yanıt veren öğelere belirli bir posta kutusu veya site klasöründe yer geldiğinden eminsanız, bu yararlı olur. Bu makaledeki betiği kullanarak posta kutusu klasörlerinin klasör kimliğini veya SharePoint ve sitedeki klasörlerin yolunu (DocumentLink) OneDrive İş edinebilirsiniz. Daha sonra, klasörde yer alan öğeleri geri dönmek için arama sorgusunda klasör kimliğini veya yolu kullanabilirsiniz.

> [!NOTE]
> SharePoint veya OneDrive İş sitedeki bir klasörde yer alan içeriği geri almak için, bu konu başlığı altında yer alan betikte Yol özelliği yerine DocumentLink yönetilen özelliği kullanılır. DocumentLink özelliği Yol özelliğinden daha güçlüdür, çünkü bir klasördeki tüm içeriği dönecektir, ancak Yol özelliği bazı medya dosyalarını geri dönmez.

## <a name="before-you-run-a-targeted-collection"></a>Hedefli koleksiyonu çalıştırmadan önce

- 1. Adımda betiği çalıştıracak şekilde, eBulma Yöneticisi rol Microsoft 365 uyumluluk merkezi üyesi olmak gerekir. Daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md).

- Ayrıca, aynı zamanda Exchange Online kurumda Posta Alıcıları rolüne Exchange Online gerekir. Bu, betikte bulunan **Get-MailboxFolderStatistics** cmdlet'ini çalıştırmak için gereklidir. Varsayılan olarak, Posta Alıcıları rolü aynı grupta Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına Exchange Online. Belirli bir grupta izin atama hakkında daha fazla Exchange Online için bkz[. Rol grubu üyelerini yönetme](/exchange/manage-role-group-members-exchange-2013-help). Ayrıca özel bir rol grubu oluşturabilir, bu gruba Posta Alıcıları rolü atayabilirsiniz ve ardından betiği çalıştırması gereken üyeleri 1. Adımda  eklersiniz. Daha fazla bilgi için bkz. [Rol gruplarını yönetme](/Exchange/permissions-exo/role-groups).

- Bu makaledeki betik, modern kimlik doğrulamayı destekler. Betiği olduğu gibi, bir çalışan veya Microsoft 365 Microsoft 365 GCC kullanabilirsiniz. Office 365 Germany kuruluşu, Microsoft 365 GCC Yüksek kuruluşu veya Microsoft 365 DoD kuruluşu isanız betiği düzenlemek ve başarılı bir şekilde çalıştırmak için gerekir. Özel olarak, `Connect-ExchangeOnline` Exchange Online PowerShell'e bağlanmak için satırı düzenlemeniz ve *ExchangeEnvironmentName* parametresini (ve kuruluş türünüz için uygun değeri) Exchange Online.  Ayrıca, Güvenlik ve Uyumluluk Merkezi PowerShell'e bağlanmak için satırı düzenlemeli ve `Connect-IPPSSession` *ConnectionUri* ile *AzureADAuthorizationEndpointUri* parametrelerini (ve kuruluş türünüz için uygun değerleri) & gerekir. Daha fazla bilgi için [PowerShell'i Bağlan ve PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) uyumluluk [Bağlan için & örneklere bakın](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Betiği her çalıştırabilirsiniz, yeni bir uzak PowerShell oturumu oluşturulur. Bu, kullanabileceğiniz tüm uzak PowerShell oturumlarını kullanabileceğiniz anlamına gelir. Bunun önüne geçmek için, aşağıdaki komutu çalıştırarak etkin uzak PowerShell oturumlarınızı kesin.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Daha fazla bilgi için bkz[. Bağlan PowerShell Exchange Online e geri Exchange Online.](/powershell/exchange/connect-to-exchange-online-powershell)

- Betik en az hata işlemeyi içerir. Betiğin birincil amacı, hedefli koleksiyonu gerçekleştirmek için İçerik Arama'nın arama sorgusu söz dizimsinde  gerektirilen posta kutusu klasör kimliklerinin veya site yollarının listesini hızla görüntülemektir.

- Bu konu başlığı altında verilen örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>1. Adım: Posta kutusu veya site klasörlerinin listesini almak için betiği çalıştırın

Bu ilk adımda çalıştırdınız betik, posta kutusu klasörlerinin veya posta kutusu klasörlerinin ya da klasörlerin SharePoint OneDrive İş ve her klasörün ilgili klasör kimliğini veya yolunu dönecektir. Bu betiği çalıştırarak aşağıdaki bilgileri girmeniz istenir.

- **E-posta adresi veya site URL'si**: Posta kutusu klasörleri ve klasör kimliklerinin listesini Exchange için custo bir e-posta adresi yazın. Ya da belirtilen sitenin yollarının listesini SharePoint için OneDrive İş sitenin URL'sini yazın. İşte birkaç örnek:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive İş**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Kullanıcı kimlik bilgileriniz**: Betik, modern kimlik doğrulamayı kullanarak PowerShell veya Güvenlik & Merkezi PowerShell'e bağlanmak Exchange Online kimlik bilgilerinizi kullanır. Daha önce de belirtildiği gibi, bu betiği başarılı bir şekilde çalıştırmak için uygun izinlerin atan atanmış olması gerekir.

Posta kutusu klasörlerinin veya site belge bağlantısı (yol) adlarının listesini görüntülemek için:

1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the Microsoft 365 compliance center.            #
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
   # Authenticate with Exchange Online and the Microsoft 365 compliance center (Exchange Online Protection - EOP)
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
      # Connect to Security & Compliance Center PowerShell
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

2. Yerel bilgisayarınızda, Windows PowerShell açın ve betiği kaydedttiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Betiğin sizden istendiğinde bilgileri girin.

    Betikte, belirtilen kullanıcı için posta kutusu klasörlerinin veya site klasörlerinin listesi görüntülenir. Klasör kimliğini veya belge bağlantısı adını kopyalayıp 2. Adım'daki arama sorgusuna yapıştırmak için bu pencereyi açık bırakın.

    > [!TIP]
    > Bilgisayar ekranında klasörlerin listesini görüntülemek yerine, betiğin çıktısını bir metin dosyasına yeniden yönlendirebilirsiniz. Bu dosya, betiğin bulunduğu klasöre kaydedilir. Örneğin, betik çıkışını bir metin dosyasına yönlendirmek için, 3. Adım'da şu komutu çalıştırın:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Ardından, arama sorgusunda kullanmak üzere dosyadan klasör kimliğini veya belge bağlantısını kopyaabilirsiniz.

### <a name="script-output-for-mailbox-folders"></a>Posta kutusu klasörleri için betik çıkışı

Posta kutusu klasör kimliklerini alıyorsanız, betik Exchange Online PowerShell'e bağlanır, **Get-MailboxFolderStatisics** cmdlet'ini çalıştırır ve ardından belirtilen posta kutusundan klasörlerin listesini görüntüler. Posta kutusudaki her klasör için, betikte **FolderPath** sütununda klasörün adı ve **FolderQuery** sütununda klasör kimliği görüntülenir. Buna ek olarak, betik **klasör kimliğine folderId** ön eklerini (posta kutusu özelliğinin adıdır) ekler. **folderid özelliği aranabilir** bir özellik olduğundan, 2. Adım'daki `folderid:<folderid>` bir arama sorgusunda bu klasörde arama yapmak için kullanırsınız. 

> [!IMPORTANT]
> Bu makaledeki betik, **Get-MailboxFolderStatistics** tarafından döndürülen 64 karakterli klasör Kimlik değerlerini arama için dizine alınmış olan 48 karakterlik biçime dönüştüren kodlama mantığı içerir. Bir klasör kimliği almak için (bu makalede betiği çalıştırmak yerine) PowerShell'de **Get-MailboxFolderStatistics** cmdlet'ini çalıştırmanız gerekirse, o klasör Kimliği değerini kullanan bir arama sorgusu başarısız olur. İçerik Arama'da  kullanılan doğru biçimlendirilmiş klasör kimliklerini almak için betiği çalıştırmanız gerekir.

Burada, posta kutusu klasörleri betiği tarafından döndürülen çıktının bir örneği ve almaktadır.

![Betik tarafından döndürülen posta kutusu klasörleri ve klasör kimlikleri listesi örneği.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

2. Adım'daki örnekte, kullanıcının Kurtarılabilir Öğeler klasöründe Temizlenebilir alt klasöründe arama yapmak için kullanılan sorgu görünür.

### <a name="script-output-for-site-folders"></a>Site klasörleri için betik çıkışı

SharePoint veya OneDrive İş sitelerinden **documentlink** özelliğinin yolunu alıyorsanız, betik Güvenlik & Uyumluluk PowerShell'e bağlanır, sitede klasörler için arama yapılan yeni bir İçerik Araması oluşturur ve belirtilen sitede bulunan klasörlerin listesini görüntüler. Betikte her klasörün adı görüntülenir ve klasör URL'sinde **belge bağlantısının** ön eki bulunur. Documentlink **özelliği** aranabilir bir özellik olduğundan, 2. Adım'daki `documentlink:<path>` bir arama sorgusunda bu klasörde arama yapmak için property:value pair kullanırsınız. Betikte en çok 100 site klasörü görüntülenir. 100'den fazla site klasörü varsa, en yeni klasörler görüntülenir.

Burada, site klasörleri betiği tarafından döndürülen çıktının bir örneği ve almaktadır.

![Betik tarafından döndürülen site klasörleri için belge bağlantısı adları listesi örneği.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>2. Adım: Hedefli koleksiyon gerçekleştirmek için klasör kimliği veya belge bağlantısı kullanma

Betiği çalıştırarak belirli bir kullanıcının klasör kimliklerinin veya belge bağlantılarının listesini toplayan bir sonraki adım, Microsoft 365 uyumluluk merkezi'e gidip belirli bir klasörde aramak için yeni İçerik Arama oluşturun. İçerik Arama `folderid:<folderid>` anahtar sözcüğü kutusunda yapılandırılan arama sorgusunda veya `documentlink:<path>` özelliği:değer çiftini (veya **New-ComplianceSearch** cmdlet'ini kullanıyorsanız *ContentMatchQuery* parametresinin değeri olarak) kullanırsınız. Veya özelliğini diğer  `folderid` arama parametreleriyle  `documentlink` veya arama koşullarıyla birleştirabilirsiniz. Veya özelliğini yalnızca sorguya  `folderid`  `documentlink` dahil ettiysanız, arama belirtilen klasörde bulunan tüm öğeleri geri döner.

1. <https://compliance.microsoft.com> 1. Adımda betiği çalıştırmak için kullanılan hesap ve kimlik bilgilerini kullanarak gidip oturum açın.

2. Uyumluluk merkezinin sol bölmesinde **AllContent** aramalarını **göster'e** >  tıklayın ve sonra da Yeni **arama'ya tıklayın**.

3. Anahtar sözcükler **kutusuna** , `folderid:<folderid>` 1. Adım'da  `documentlink:<path>/*` betik tarafından döndürülen veya değeri yapıştırın.

    Örneğin, aşağıdaki ekran görüntüsünde yer alan sorgu kullanıcının Kurtarılabilir Öğeler klasöründeki Temizlenebilir alt klasördeki herhangi bir öğeyi aratır ( `folderid` Temizlenebilir alt klasörünün özelliğinin değeri, 1. Adımdaki ekran görüntüsünde gösterilir):

    ![Klasörki veya belge bağlantısını arama sorgusunun anahtar sözcük kutusuna yapıştırın.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > documentlink aramaları bir sonda kullanımını gerektirir  `asterisk '/*'`.  

4. **Konumlar'ın** altında Belirli **konumlar'ı seçin ve** Değiştir'e **tıklayın**.

5. Posta kutusu klasöründe veya site klasöründe arama yapmasanıza bağlı olarak, aşağıdan birini yapın:

    - **E-Exchange öğesinin** yanında Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın ve ardından 1. Adımda betiği çalıştırarak belirttiğiniz posta kutusunu ekleyin.

      Veya

    - Site ekle **SharePoint nin** yanında Siteleri seç'e  tıklayın ve ardından 1. Adımda betiği çalıştırarak belirttiğiniz site URL'sini ekleyin.

6. aranacak içerik konumunu kaydetmek için Kaydet **'& çalıştır'a** tıklayın, İçerik Arama için bir ad yazın ve ardından Kaydet'e tıklarsanız  hedefli koleksiyon araması başlatabilirsiniz.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Hedefli koleksiyonlar için arama sorguları örnekleri

Burada, hedefli koleksiyonu gerçekleştirmek için  `folderid`  `documentlink` bir arama sorgusunda özellikleri kullanmayla ilgili bazı örnekler verilmiştir. Yer tutucular yer kazanmak  `folderid:<folderid>` ve  `documentlink:<path>` yer kazanmak için kullanılır.

- Bu örnekte, üç farklı posta kutusu klasörü arar. Kullanıcının Kurtarılabilir Öğeler klasöründeki gizli klasörlerde arama yapmak için de benzer sorgu söz dizimi kullanabilirsiniz.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- Bu örnek, bir posta kutusu klasöründe tam bir tümcecik içeren öğeleri arar.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- Bu örnek, bir site klasöründe (ve tüm alt klasörlerde) başlıkta "NDA" harflerini içeren belgeleri arar.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- Bu örnek, bir tarih aralığında değiştirilmiş olan belgeleri site klasöründe (ve herhangi bir alt klasörde) arar.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Daha fazla bilgi

Hedefli koleksiyonları gerçekleştirmek için bu makaledeki betiği kullanırken aşağıdaki şeyleri unutmayın.

- Betik sonuçlardan hiçbir klasörü kaldırmaz. Dolayısıyla sonuçlarda listelenen bazı klasörler, sistem tarafından oluşturulan içerik içermesi veya posta kutusu öğeleri değil yalnızca alt klasörler içermesi nedeniyle aranamaz (veya sıfır öğe geri dönebilir) olabilir.

- Bu betik yalnızca kullanıcının birincil posta kutusunun klasör bilgilerini döndürür. Kullanıcının arşiv posta kutusunda yer alan klasörlerle ilgili bilgileri geri dönmez. Kullanıcının arşiv posta kutusunda klasörlerle ilgili bilgileri geri almak için betiği düzenleyebilirsiniz. Bunu yapmak için, satırı olarak değiştirin `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` ve sonra düzenlenmiş betiği kaydedin ve çalıştırın. Bu değişiklik, kullanıcının arşiv posta kutusunda klasörlerin ve alt klasörlerin klasör kimliklerini geri dönecektir. Arşiv posta kutusunun tamamnda arama yapmak için, bir arama sorgusunda tüm klasör kimliği özelliği:değer çiftlerini bir işleçle `OR` b bağlanabilirsiniz.

- Posta kutusu klasörlerini ararken, yalnızca belirtilen klasörde ( `folderid` özelliğiyle tanımlanan klasör) arama olur; alt klasörlerde arama olmayacaktır. Alt klasörlerde arama yapmak için, aramak istediğiniz alt klasörün klasör kimliğini kullansanız gerekir.

- Site klasörlerini ararken, klasörde (özelliğiyle `documentlink` tanımlanan klasör) ve tüm alt klasörlerde arama olur.

- `folderid` Özelliği yalnızca arama sorgusunda belirttiğiniz bir aramanın sonuçlarını dışarı aktararak ilk dışarı aktarma seçeneğini "Tanınmayan biçime sahip olanlar, şifrelenmiş veya başka nedenlerle dizine almamış olanlar hariç olmak üzere tüm öğeler" seçebilirsiniz. Klasör kimliği her zaman dizine alındıklarından bağımsız olarak klasördeki tüm öğeler her zaman dizin oluşturma durumundan bağımsız olarak dışarı aktarıldı.
