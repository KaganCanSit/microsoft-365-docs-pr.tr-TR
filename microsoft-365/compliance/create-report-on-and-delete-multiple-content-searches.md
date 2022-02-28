---
title: Birden çok İçerik Araması oluşturma, bu aramaları bildirme ve silme
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
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: Güvenlik ve Uyumluluk Merkezi PowerShell kullanarak arama oluşturma ve rapor çalıştırma gibi İçerik Arama & otomatikleştirmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 602997114c46a68be13182a504d0b123e98d2be2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985568"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Birden çok İçerik Araması oluşturma, bu aramaları bildirme ve silme

 Bulma aramalarını hızla oluşturmak ve raporlamak, çoğunlukla temel alınan veriler ve aramaların zenginliği ve kalitesi hakkında bilgi edinmeye çalışırken eBulma ve soruşturmalarda önemli bir adımdır. Bunu yapmaya yardımcı olmak için, Güvenlik & Uyumluluk Merkezi PowerShell zaman alan İçerik Arama görevlerini otomatikleştirmek için bir dizi cmdlet sunar. Bu betikler, bir dizi arama oluşturmak ve ardından söz konusu verilerin miktarını belirlemenize yardımcı olacak tahmini arama sonuçlarının raporlarını çalıştırmak için hızlı ve kolay bir yol sağlar. Betikleri, her birinin ürettiği sonuçları karşılaştırmak üzere farklı arama sürümleri oluşturmak için de kullanabilirsiniz. Bu betikler, verilerinizi hızlı ve verimli bir şekilde tanımlamanıza ve kullanmanıza yardımcı olabilir.

## <a name="before-you-create-a-content-search"></a>İçerik Arama oluşturmadan önce

- Bu konuda açıklanan betikleri çalıştırmak için, Microsoft 365 uyumluluk merkezi Yöneticisi'nin eBulma Yöneticisi rol grubunun üyesi olun.

- 1. Adımda CSV dosyasına ek olarak, OneDrive İş sitelerinin URL'lerinin listesini toplamak için bkz. OneDrive [konumlarının listesini oluşturma](/onedrive/list-onedrive-urls).

- Bu konu başlığında, bu konu başlığında oluşturan tüm dosyaları aynı klasöre kaydetmeye emin olun. Bu, betikleri çalıştırmayı kolaylaştırır.

- Betikler en az hata işlemeyi içerir. Bunun birincil amacı, birden çok İçerik Aramalarını hızla oluşturmak, bu aramaları rapor etmek ve silmektir.

- Bu konu başlığı altında verilen örnek betikler, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenemmektedir. Örnek betikler hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiklerin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>1. Adım: Çalıştırmak istediğiniz aramalara ilişkin bilgileri içeren bir CSV dosyası oluşturun

Bu adımda oluştursanız da virgülle ayrılmış değer (CSV) dosyası, arama yapmak isteyen her kullanıcı için bir satır içerir. Kullanıcının posta kutusu (etkinse Exchange Online arşiv posta kutusunu da içerir) ve kullanıcının posta kutusu arama OneDrive İş. Ya da yalnızca posta kutusunda veya posta kutusunda OneDrive İş de arayabilirsiniz. Ayrıca, SharePoint Online SharePoint arayabilirsiniz. 3. Adımda çalıştırdınız betik, CSV dosyasındaki her satır için ayrı bir arama oluşturacak.

1. Aşağıdaki metni kopyalayıp Not Defteri'ni kullanarak .txt bir dosyaya yapıştırın. Bu dosyayı yerel bilgisayarınızdan bir klasöre kaydedin. Diğer betikleri de bu klasöre kaydetebilirsiniz.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Dosyanın ilk satırı veya üst bilgi satırı, yeni İçerik Aramaları oluşturmak için **Yeni** Uyumluluk Arama cmdlet'i tarafından (3. adımdaki betikte) kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılmıştır. Üst bilgi satırda boşluk olmadığını unutmayın. Üst bilgi satırın altındaki her satır, her aramanın parametre değerlerini temsil eder. CSV dosyasındaki yer tutucu verilerini gerçek verilerinizle değiştir mutlaka.

2. .txt dosyanızı Excel ve her aramayla ilgili bilgilerle birlikte dosyayı düzenlemek için aşağıdaki tabloda yer alan bilgileri kullanın.

   ****

   |Parametre|Açıklama|
   |---|---|
   |`ExchangeLocation`|Kullanıcının posta kutusunun SMTP adresi.|
   |`SharePointLocation`|Kullanıcının web sitesinin URL'si OneDrive İş sitenin URL'si veya kuruluşta herhangi bir sitenin URL'si. Site sitelerinin URL'OneDrive İş şu biçimi kullanın: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. Örneğin,  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|Arama için arama sorgusu. Arama sorgusu oluşturma hakkında daha fazla bilgi için bkz. [Anahtar sözcük sorguları ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).|
   |`StartDate`|E-posta için, iletinin alıcı tarafından veya gönderen tarafından gönderildiği tarihtir. Site veya site SharePoint OneDrive İş belgeler için, belgenin son değiştirilme tarihi veya sonrası.|
   |`EndDate`|E-posta için, kullanıcı tarafından gönderilen iletinin gönderilme tarihi veya öncesi. Site site SharePoint veya OneDrive İş belgeler için, belgenin son değiştirilme tarihi veya önceki tarihi.|
   |

3. Dosya Excel CSV dosyası olarak yerel bilgisayarınızdan bir klasöre kaydedin. 3. Adımda oluşturmuştuk betik, aramaları oluşturmak için bu CSV dosyasındaki bilgileri kullanır.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>2. Adım: Bağlan ve Uyumluluk & PowerShell'e geçin

Sonraki adım, sizin için Güvenlik ve Uyumluluk & PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz. Güvenlik [Bağlan Uyumluluk Merkezi PowerShell& e geçin](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>3. Adım: Betiği çalıştırarak aramaları oluşturun ve çalıştırın

Bu adımdaki betik, 1. Adımda oluşturduğunuz CSV dosyasındaki her satır için ayrı bir İçerik Arama oluşturacak. Bu betiği çalıştırarak iki değer girmeniz istenir:

- **Arama Grubu Kimliği** - Bu ad, CSV dosyasından oluşturulan aramaları düzenlemenin kolay bir yolunu sağlar. Oluşturulan her arama, Arama Grubu Kimliği ile adlandırılmıştır ve arama adına bir numara eklenir. Örneğin, Arama Grubu Kimliği olarak **ContosoCase** girersiniz, aramalar grup adı **ContosoCase_1****, ContosoCase_2** ContosoCase_3 gibi adlar alır.  Yazım adının büyük/harfe duyarlı olduğunu unutmayın. 4. ve 5. Adım'da Grup Arama kimliğini kullanırken, grubu oluşturulduğunda kullanmak için grupla aynı vakayı kullan gerekir.

- **CSV dosyası** - 1. Adımda oluşturduğunuz CSV dosyasının adı. Tam dosya adını kullanmayı, dosya uzantısını ve dosya .csv emin olun; örneğin,  `ContosoCase.csv`.

Betiği çalıştırmak için:

1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `CreateSearches.ps1`. Dosyayı, diğer dosyaları kendi kaydett ili aynı klasöre kaydedin.

   ```Powershell
   # Get the Search Group ID and the location of the CSV input file
   $searchGroup = Read-Host 'Search Group ID'
   $csvFile = Read-Host 'Source CSV file'

   # Do a quick check to make sure our group name will not collide with other searches
   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    $searchName = $searchGroup +'_' + $searchCounter
    $search = Get-ComplianceSearch $searchName -EA SilentlyContinue
    if ($search)
    {
       Write-Error "The Search Group ID conflicts with existing searches.  Please choose a search group name and restart the script."
       return
    }
    $searchCounter++
   }

   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    # Create the query
    $query = $_.ContentMatchQuery
    if(($_.StartDate -or $_.EndDate))
    {
          # Add the appropriate date restrictions.  NOTE: Using the Date condition property here because it works across Exchange, SharePoint, and OneDrive for Business.
          # For Exchange, the Date condition property maps to the Sent and Received dates; for SharePoint and OneDrive for Business, it maps to Created and Modified dates.
          if($query)
          {
              $query += " AND"
          }
          $query += " ("
          if($_.StartDate)
          {
              $query += "Date >= " + $_.StartDate
          }
          if($_.EndDate)
          {
              if($_.StartDate)
              {
                  $query += " AND "
              }
              $query += "Date <= " + $_.EndDate
          }
          $query += ")"
    }

     # -ExchangeLocation can't be set to an empty string, set to null if there's no location.
     $exchangeLocation = $null
     if ( $_.ExchangeLocation)
     {
           $exchangeLocation = $_.ExchangeLocation
     }

    # Create and run the search
    $searchName = $searchGroup +'_' + $searchCounter
    Write-Host "Creating and running search: " $searchName -NoNewline
    $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $exchangeLocation -SharePointLocation $_.SharePointLocation -ContentMatchQuery $query

    # Start and wait for each search to complete
    Start-ComplianceSearch $search.Name
    while ((Get-ComplianceSearch $search.Name).Status -ne "Completed")
    {
       Write-Host " ." -NoNewline
       Start-Sleep -s 3
    }
    Write-Host ""

    $searchCounter++
   }
   ```

2. Bunu Windows PowerShell, önceki adımda betiği kaydeden klasöre gidin ve sonra betiği çalıştırın; örneğin:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. Grup **Kimliğini Ara istemine** bir arama grubu adı yazın ve Enter tuşuna **basın**; örneğin,  `ContosoCase`. Bu adın büyük/harfe duyarlı olduğunu unutmayın, bu nedenle sonraki adımlarda da aynı şekilde yazmamız gerekir.

4. Kaynak **CSV dosya istemine** , en son dosya uzantısını içeren CSV .csv yazın; örneğin,  `ContosoCase.csv`.

5. **Betiği çalıştırmaya** devam etmek için Enter tuşuna basın.

   Betikte, aramaları oluşturma ve çalıştırma ilerleme durumu görüntülenir. Betik tamamlandığında komut istemine döner.

   ![Betiği çalıştırmadan çeşitli uyumluluk aramaları oluşturmak için örnek çıktı.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>4. Adım: Arama tahminlerini rapor etmek için betiği çalıştırın

Aramaları oluşturduktan sonraki adım, 3. Adımda oluşturulan her aramanın arama isabet sayısını gösteren basit bir rapor görüntüleyen bir betik çalıştırmaktır. Ayrıca rapor, her arama için sonuç boyutunu ve tüm aramaların toplam isabet sayısını ve toplam boyutunu da içerir. Raporlama betiğinizi çalıştırsanız, raporu CSV dosyasına kaydetmek için Grup Ara kimliği ve CSV dosya adı istenir.

1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `SearchReport.ps1`. Dosyayı, diğer dosyaları kendi kaydett ili aynı klasöre kaydedin.

   ```Powershell
   $searchGroup = Read-Host 'Search Group ID'
   $outputFile = Read-Host 'Enter a file name or file path to save the report to a .csv file. Leave blank to only display the report'
   $searches = Get-ComplianceSearch | ?{$_.Name -clike $searchGroup + "_*"}
   $allSearchStats = @()
   foreach ($partialObj in $searches)
   {
      $search = Get-ComplianceSearch $partialObj.Name
      $sizeMB = [System.Math]::Round($search.Size / 1MB, 2)
      $searchStatus = $search.Status
      if($search.Errors)
      {
          $searchStatus = "Failed"
      }elseif($search.NumFailedSources -gt 0)
      {
          $searchStatus = "Failed Sources"
      }
      $searchStats = New-Object PSObject
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Name -Value $search.Name
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name ContentMatchQuery -Value $search.ContentMatchQuery
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Status -Value $searchStatus
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Items -Value $search.Items
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size" -Value $search.Size
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size(MB)" -Value $sizeMB
      $allSearchStats += $searchStats
   }
   # Calculate the totals
   $allItems = ($allSearchStats | Measure-Object Items -Sum).Sum
   # Convert the total size to MB and round to the nearst 100th
   $allSize = ($allSearchStats | Measure-Object 'Size' -Sum).Sum
   $allSizeMB = [System.Math]::Round($allSize  / 1MB, 2)
   # Get the total successful searches and total of all searches
   $allSuccessCount = ($allSearchStats |?{$_.Status -eq "Completed"}).Count
   $allCount = $allSearchStats.Count
   $allStatus = [string]$allSuccessCount + " of " + [string]$allCount
   # Totals Row
   $totalSearchStats = New-Object PSObject
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Name -Value "Total"
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Status -Value $allStatus
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Items -Value $allItems
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name "Size(MB)" -Value $allSizeMB
   $allSearchStats += $totalSearchStats
   # Just get the columns we're interested in showing
   $allSearchStatsPrime = $allSearchStats | Select-Object Name, Status, Items, "Size(MB)", ContentMatchQuery
   # Print the results to the screen
   $allSearchStatsPrime |ft -AutoSize -Wrap
   # Save the results to a CSV file
   if ($outputFile)
   {
      $allSearchStatsPrime | Export-Csv -Path $outputFile -NoTypeInformation
   }
   ```

2. Bunu Windows PowerShell, önceki adımda betiği kaydeden klasöre gidin ve sonra betiği çalıştırın; örneğin:

   ```Powershell
   .\SearchReport.ps1
   ```

3. Grup **Kimliğini Ara istemine** bir arama grubu adı yazın ve Enter tuşuna **basın**;  `ContosoCase`örneğin. Bu adın büyük/harfe duyarlı olduğunu unutmayın, bu nedenle 3. Adımda betiği son çalıştırmada olduğu gibi yazmanız gerekir.

4. Raporu CSV dosyasına kaydetmek için Dosya yolu (yalnızca raporu görüntülemek için boş bırakın **)** istemine, raporu CSV dosyasına kaydetmek için tam dosya adı yolunun (.csv dosya uzantısıyla birlikte) dosya adını yazın. CSV dosyasının adı, dosya uzantısı .csv. Örneğin, geçerli dizine  `ContosoCaseReport.csv` kaydetmek için yazarak veya başka bir klasöre  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` kaydetmek için yazabilirsiniz. Ayrıca, raporu görüntülemek için istemi boş bırakabilirsiniz ancak bir dosyaya kaydedeebilirsiniz.

5. **Enter tuşuna basın**.

   Betikte, aramaları oluşturma ve çalıştırma ilerleme durumu görüntülenir. Betik tamamlandığında rapor görüntülenir.

   ![Arama grubunun tahminlerini görüntülemek için arama raporunu çalıştırın.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Bir arama grubunda birden fazla aramada aynı posta kutusu veya site bir içerik konumu olarak belirtilirse, rapordaki toplam sonuç tahmini (hem öğe sayısı hem de toplam boyut için) aynı öğelerin sonuçlarını içerebilir. Çünkü aynı e-posta iletisi veya belge, arama grubunda farklı aramalar için sorguyla eş kullandıktan sonra birden çok kez sayılır.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>5. Adım: Aramaları silmek için betiği çalıştırma

Çok fazla arama oluşturuyor olabileceğiniz için, bu son betik yalnızca 3. Adımda oluşturduğunuz aramaları hızla silmeyi kolaylaştırır. Diğer betiklerde olduğu gibi, bu da sizden Grup Kimliğini Aramanızı da sağlar. Bu betiği çalıştırarak, arama adı altında Grup Ara kimliğiyle yapılan tüm aramalar silinir.

1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `DeleteSearches.ps1`. Dosyayı, diğer dosyaları kendi kaydett ili aynı klasöre kaydedin.

   ```Powershell
   # Delete all searches in a search group
   $searchGroup = Read-Host 'Search Group ID'
   Get-ComplianceSearch |
      ForEach-Object{
      # If the name matches the search group name pattern (case sensitive), delete the search
      if ($_.Name -cmatch $searchGroup + "_\d+")
      {
          Write-Host "Deleting search: " $_.Name
          Remove-ComplianceSearch $_.Name -Confirm:$false
      }
   }
   ```

2. Bunu Windows PowerShell, önceki adımda betiği kaydeden klasöre gidin ve sonra betiği çalıştırın; örneğin:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. Grup **Kimliğini Ara istemine** , silmek istediğiniz aramalar için bir arama grubu adı yazın ve Enter tuşuna **basın**; örneğin,  `ContosoCase`. Bu adın büyük/harfe duyarlı olduğunu unutmayın, bu nedenle 3. Adımda betiği son çalıştırmada olduğu gibi yazmanız gerekir.

   Betikte silinen her aramanın adı görüntülenir.

   ![Arama grubunda aramaları silmek için betiği çalıştırın.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
