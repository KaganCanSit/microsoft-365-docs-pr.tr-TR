---
title: İçerik Aramalarını oluşturma, raporlama ve silme
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
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: Güvenlik & Uyumluluk Merkezi PowerShell kullanarak arama oluşturma ve raporları çalıştırma gibi İçerik Arama görevlerini otomatikleştirmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8ef806b9be55b8c39ad26f477d35eb076b22c16b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099289"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Birden çok İçerik Araması oluşturma, raporlama ve silme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

 Bulma aramalarını hızla oluşturmak ve raporlamak, temel alınan veriler ve aramalarınızın zenginliği ve kalitesi hakkında bilgi edinmeye çalışırken eBulma ve araştırmalarda genellikle önemli bir adımdır. Bunu yapmanıza yardımcı olmak için Güvenlik & Uyumluluk Merkezi PowerShell, zaman alan İçerik Arama görevlerini otomatikleştirmek için bir dizi cmdlet sunar. Bu betikler, bir dizi arama oluşturmak için hızlı ve kolay bir yol sağlar ve ardından söz konusu veri miktarını belirlemenize yardımcı olabilecek tahmini arama sonuçlarının raporlarını çalıştırır. Betikleri, her birinin ürettiği sonuçları karşılaştırmak üzere aramaların farklı sürümlerini oluşturmak için de kullanabilirsiniz. Bu betikler, verilerinizi hızlı ve verimli bir şekilde tanımlamanıza ve iptal etmenize yardımcı olabilir.

## <a name="before-you-create-a-content-search"></a>İçerik Araması oluşturmadan önce

- Bu konuda açıklanan betikleri çalıştırmak için Microsoft Purview uyumluluk portalında eBulma Yöneticisi rol grubunun üyesi olmanız gerekir.

- 1. Adımda CSV dosyasına ekleyebileceğiniz, kuruluşunuzdaki OneDrive İş sitelerinin URL'lerinin listesini toplamak için bkz. [Kuruluşunuzdaki tüm OneDrive konumlarının listesini oluşturma](/onedrive/list-onedrive-urls).

- Bu konuda oluşturduğunuz tüm dosyaları aynı klasöre kaydettiğinizden emin olun. Bu, betikleri çalıştırmayı kolaylaştırır.

- Betikler en az hata işleme içerir. Birincil amacı, birden çok İçerik Aramasını hızla oluşturmak, raporlamak ve silmektir.

- Bu konuda sağlanan örnek betikler, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betikler, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiklerin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>1. Adım: Çalıştırmak istediğiniz aramalar hakkında bilgi içeren bir CSV dosyası oluşturma

Bu adımda oluşturduğunuz virgülle ayrılmış değer (CSV) dosyası, aramak isteyen her kullanıcı için bir satır içerir. Kullanıcının Exchange Online posta kutusunda (etkinse arşiv posta kutusunu içerir) ve OneDrive İş sitesinde arama yapabilirsiniz. Ya da yalnızca posta kutusunda veya OneDrive İş sitesinde arama yapabilirsiniz. SharePoint Online kuruluşunuzdaki herhangi bir sitede de arama yapabilirsiniz. 3. Adımda çalıştırdığınız betik, CSV dosyasındaki her satır için ayrı bir arama oluşturur.

1. Not Defteri'ni kullanarak aşağıdaki metni kopyalayıp .txt dosyasına yapıştırın. Bu dosyayı yerel bilgisayarınızdaki bir klasöre kaydedin. Diğer betikleri de bu klasöre kaydedeceksiniz.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Dosyanın ilk satırı veya üst bilgi satırı, yeni İçerik Aramaları oluşturmak için **New-ComplianceSearch** cmdlet'i (3. Adımdaki betikte) tarafından kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılır. Üst bilgi satırında boşluk olmadığından emin olun. Üst bilgi satırının altındaki her satır, her arama için parametre değerlerini temsil eder. CSV dosyasındaki yer tutucu verileri gerçek verilerinizle değiştirerek değiştirmeyi unutmayın.

2. .txt dosyasını Excel açın ve sonra dosyayı her aramayla ilgili bilgilerle düzenlemek için aşağıdaki tabloda yer alan bilgileri kullanın.

   ****

   |Parametre|Açıklama|
   |---|---|
   |`ExchangeLocation`|Kullanıcının posta kutusunun SMTP adresi.|
   |`SharePointLocation`|Kullanıcının OneDrive İş sitesinin URL'si veya kuruluşunuzdaki herhangi bir sitenin URL'si. OneDrive İş sitelerin URL'si için şu biçimi kullanın: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. Örneğin,  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|Aramanın arama sorgusu. Arama sorgusu oluşturma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).|
   |`StartDate`|E-posta için, iletinin alıcı tarafından alındığı veya gönderen tarafından gönderildiği tarih. SharePoint veya OneDrive İş sitelerdeki belgeler için, belgenin son değiştirilme tarihi veya sonrasındaki tarih.|
   |`EndDate`|E-posta için, iletinin kullanıcı tarafından gönderilen bir tarafından gönderildiği veya gönderilmeden önceki tarih. SharePoint veya OneDrive İş sitelerdeki belgeler için, belgenin son değiştirilme tarihi veya öncesinde tarih.|
   |

3. Excel dosyasını CSV dosyası olarak yerel bilgisayarınızdaki bir klasöre kaydedin. 3. Adımda oluşturduğunuz betik, aramaları oluşturmak için bu CSV dosyasındaki bilgileri kullanır.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>2. Adım: Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan

Sonraki adım, kuruluşunuz için Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz[. Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>3. Adım: Aramaları oluşturmak ve başlatmak için betiği çalıştırın

Bu adımdaki betik, 1. Adımda oluşturduğunuz CSV dosyasındaki her satır için ayrı bir İçerik Araması oluşturur. Bu betiği çalıştırdığınızda sizden iki değer istenir:

- **Arama Grubu Kimliği** - Bu ad, CSV dosyasından oluşturulan aramaları düzenlemek için kolay bir yol sağlar. Oluşturulan her arama, Arama Grubu Kimliği ile adlandırılır ve arama adının sonuna bir sayı eklenir. Örneğin, Arama Grubu Kimliği için **ContosoCase** girerseniz, aramalar **ContosoCase_1, ContosoCase_2**, **ContosoCase_3** vb. olarak adlandırılır.  Yazdığınız adın büyük/küçük harfe duyarlı olduğunu unutmayın. 4. Adım ve 5. Adım'da Arama Grubu Kimliğini kullandığınızda, bunu oluştururken kullandığınız servis talebinin aynısını kullanmanız gerekir.

- **CSV dosyası** - 1. Adımda oluşturduğunuz CSV dosyasının adı. Tam dosya adını kullanmayı eklediğinizden emin olun, .csv dosya uzantısını ekleyin; örneğin,  `ContosoCase.csv`.

Betiği çalıştırmak için:

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `CreateSearches.ps1`. Dosyayı, diğer dosyaları kaydettiğiniz klasöre kaydedin.

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

2. Windows PowerShell önceki adımda betiği kaydettiğiniz klasöre gidin ve ardından betiği çalıştırın; örneğin:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. **Arama Grubu Kimliği** isteminde bir arama grubu adı yazın ve **Enter tuşuna** basın; örneğin, `ContosoCase`. Bu adın büyük/küçük harfe duyarlı olduğunu unutmayın, bu nedenle sonraki adımlarda aynı şekilde yazmanız gerekir.

4. **Kaynak CSV dosyası** isteminde, .csv dosya uzantısı da dahil olmak üzere CSV dosyasının adını yazın; örneğin, `ContosoCase.csv`.

5. Betiği çalıştırmaya devam etmek için **Enter tuşuna** basın.

   Betik, arama oluşturma ve çalıştırma işleminin ilerleme durumunu görüntüler. Betik tamamlandığında istemine döner.

   ![Birden çok uyumluluk araması oluşturmak için betiği çalıştırmanın örnek çıktısı.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>4. Adım: Arama tahminlerini raporlamak için betiği çalıştırın

Aramaları oluşturduktan sonra, sonraki adım, 3. Adımda oluşturulan her arama için arama isabet sayısıyla ilgili basit bir rapor görüntüleyen bir betik çalıştırmaktır. Rapor ayrıca her arama için sonuçların boyutunu ve toplam isabet sayısını ve tüm aramaların toplam boyutunu içerir. Raporlama betiğini çalıştırdığınızda, raporu bir CSV dosyasına kaydetmek istiyorsanız Arama Grubu Kimliği ve CSV dosya adı istenir.

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `SearchReport.ps1`. Dosyayı, diğer dosyaları kaydettiğiniz klasöre kaydedin.

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

2. Windows PowerShell önceki adımda betiği kaydettiğiniz klasöre gidin ve ardından betiği çalıştırın; örneğin:

   ```Powershell
   .\SearchReport.ps1
   ```

3. **Arama Grubu Kimliği** isteminde bir arama grubu adı yazın ve **Enter tuşuna** basın; örneğin`ContosoCase`, . Bu adın büyük/küçük harfe duyarlı olduğunu unutmayın, bu nedenle 3. Adımda betiği çalıştırdığınız gibi yazmanız gerekir.

4. **Raporu csv dosyasına kaydetmek için dosya yolu (raporu görüntülemek için boş bırakın)** isteminde, raporu csv dosyasına kaydetmek istiyorsanız tam dosya adı yolunun (.csv dosya uzantısı dahil) bir dosya adı yazın. .csv dosya uzantısı da dahil olmak üzere CSV dosyasının adı. Örneğin, geçerli dizine kaydetmek için yazabilir  `ContosoCaseReport.csv` veya farklı bir klasöre kaydetmek için yazabilirsiniz  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` . Ayrıca, raporu görüntülemek için istemi boş bırakabilirsiniz ancak bir dosyaya kaydedemezsiniz.

5. **Enter tuşuna** basın.

   Betik, arama oluşturma ve çalıştırma işleminin ilerleme durumunu görüntüler. Betik tamamlandığında rapor görüntülenir.

   ![Arama grubunun tahminlerini görüntülemek için arama raporunu çalıştırın.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Aynı posta kutusu veya site, arama grubundaki birden fazla aramada içerik konumu olarak belirtilirse, rapordaki toplam sonuç tahmini (hem öğe sayısı hem de toplam boyut için) aynı öğelerin sonuçlarını içerebilir. Bunun nedeni, arama grubundaki farklı aramalar için sorguyla eşleşiyorsa aynı e-posta iletisinin veya belgenin birden çok kez sayılmasıdır.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>5. Adım: Aramaları silmek için betiği çalıştırın

Çok fazla arama oluşturduğunuz için bu son betik, 3. Adımda oluşturduğunuz aramaları hızlı bir şekilde silmenizi kolaylaştırır. Diğer betiklerde olduğu gibi, bu komut da arama grubu kimliğini girmenizi ister. Bu betiği çalıştırdığınızda, arama adında Arama Grubu Kimliği olan tüm aramalar silinir.

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `DeleteSearches.ps1`. Dosyayı, diğer dosyaları kaydettiğiniz klasöre kaydedin.

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

2. Windows PowerShell önceki adımda betiği kaydettiğiniz klasöre gidin ve ardından betiği çalıştırın; örneğin:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. **Arama Grubu Kimliği** isteminde, silmek istediğiniz aramalar için bir arama grubu adı yazın ve enter **tuşuna** basın; örneğin, `ContosoCase`. Bu adın büyük/küçük harfe duyarlı olduğunu unutmayın, bu nedenle 3. Adımda betiği çalıştırdığınız gibi yazmanız gerekir.

   Betik, silinen her aramanın adını görüntüler.

   ![Arama grubundaki aramaları silmek için betiği çalıştırın.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
