---
title: Denetim günlüğünü aramak için PowerShell betiği kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Denetim günlüğünde arama yapmak için Exchange Online'da Search-UnifiedAuditLog cmdlet'ini çalıştıran bir PowerShell betiği kullanın. Bu betik, her çalıştırdığınızda büyük bir denetim kayıtları kümesi döndürecek şekilde iyileştirilmiştir. Betik, bu kayıtları Excel'da Power Query kullanarak görüntüleyebileceğiniz veya dönüştürebileceğiniz bir CSV dosyasına aktarır.
ms.openlocfilehash: 8799f1a4ddf2ef7dd536ccb3e6e70a4b731b4cd6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100863"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Denetim günlüğünü aramak için PowerShell betiği kullanma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Güvenlik, uyumluluk ve denetim, günümüzün dünyasında BT yöneticileri için en önemli öncelik haline gelmiştir. Microsoft 365, kuruluşların güvenlik, uyumluluk ve denetimi yönetmesine yardımcı olan çeşitli yerleşik özelliklere sahiptir. Özellikle, birleşik denetim günlüğü güvenlik olaylarını ve uyumluluk sorunlarını araştırmanıza yardımcı olabilir. Aşağıdaki yöntemleri kullanarak denetim günlüklerini alabilirsiniz:

- [Office 365 Yönetim Etkinliği API'si](/office/office-365-management-api/office-365-management-activity-api-reference)

- Microsoft Purview uyumluluk portalındaki [denetim günlüğü arama aracı](search-the-audit-log-in-security-and-compliance.md)

- Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'i

Denetim günlüklerini düzenli olarak almanız gerekiyorsa, büyük kuruluşlara sürekli olarak milyonlarca denetim kaydını almaları için ölçeklenebilirlik ve performans sağlayabilen Office 365 Yönetim Etkinliği API'sini kullanan bir çözüm düşünmelisiniz. Uyumluluk portalında denetim günlüğü arama aracını kullanmak, daha kısa zaman aralığında gerçekleşen belirli işlemlerin denetim kayıtlarını hızla bulmanın iyi bir yoludur. Denetim günlüğü arama aracında, özellikle de büyük kuruluşlar için daha uzun zaman aralıkları kullanmak, kolayca yönetmek veya dışarı aktarmak için çok fazla kayıt döndürebilir.

Özellikle büyük kuruluşlardaki daha uzun tarih aralıkları için belirli bir araştırma veya olay için denetim verilerini el ile almanız gereken durumlar olduğunda, **Search-UnifiedAuditLog** cmdlet'ini kullanmak en iyi seçenek olabilir. Bu makale, 50.000 denetim kaydını alabilen (cmdlet'i her çalıştırdığınızda) cmdlet'ini kullanan ve bunları gözden geçirmenize yardımcı olmak için Excel'deki Power Query kullanarak biçimlendirebileceğiniz bir CSV dosyasına aktaran bir PowerShell betiği içerir. Bu makaledeki betiğin kullanılması, büyük denetim günlüğü aramalarının hizmette zaman aşımına neden olma olasılığını da en aza indirir.

## <a name="before-you-run-the-script"></a>Betiği çalıştırmadan önce

- Denetim kayıtlarını döndürmek için betiğin başarıyla kullanılabilmesi için kuruluşunuz için denetim günlüğünün etkinleştirilmesi gerekir. Denetim günlüğü, Microsoft 365 ve Office 365 kurumsal kuruluşlar için varsayılan olarak açıktır. Kuruluşunuzda denetim günlüğü aramasının açık olduğunu doğrulamak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  **UnifiedAuditLogIngestionEnabled** özelliğinin değeri`True`, denetim günlüğü aramasının açık olduğunu gösterir.

- Betiği başarıyla çalıştırmak için Exchange Online'da View-Only Denetim Günlükleri veya Denetim Günlükleri rolüne atanmış olmanız gerekir. Varsayılan olarak, bu roller <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezindeki</a> İzinler sayfasındaki Uyumluluk Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Daha fazla bilgi için Uyumluluk merkezinde denetim günlüğünde arama yapma bölümündeki " [Denetim günlüğünde](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log) arama yapma gereksinimleri" bölümüne bakın.

- Betiğin tamamlanması uzun sürebilir. Çalıştırmanın ne kadar süreceği, denetim kayıtlarını almak için betiği yapılandırdığınız tarih aralığına ve aralığın boyutuna bağlıdır. Daha büyük tarih aralıkları ve daha küçük aralıklar uzun çalışma süresine neden olur. Tarih aralığı ve aralıklar hakkında daha fazla bilgi için 2. Adım'daki tabloya bakın.

- Bu makalede sağlanan örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiğin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiğin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-connect-to-exchange-online-powershell"></a>1. Adım: PowerShell'i Exchange Online için Bağlan

İlk adım, Exchange Online PowerShell'e bağlanmaktır. Modern kimlik doğrulaması kullanarak veya çok faktörlü kimlik doğrulaması (MFA) ile bağlanabilirsiniz. Adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>2. Adım: Denetim kayıtlarını almak için betiği değiştirme ve çalıştırma

Exchange Online PowerShell'e bağlandıktan sonra, sonraki adım denetim verilerini almak için betiği oluşturmak, değiştirmek ve çalıştırmaktır. Denetim günlüğü arama betiğindeki ilk yedi satır, aramanızı yapılandırmak için değiştirebileceğiniz aşağıdaki değişkenleri içerir. Bu değişkenlerin açıklaması için 2. adımdaki tabloya bakın.

1. .ps1 dosya adı son ekini kullanarak aşağıdaki metni Windows PowerShell betiğine kaydedin. Örneğin, SearchAuditLog.ps1.

   ```powershell
   #Modify the values for the following variables to configure the audit log search.
   $logFile = "d:\AuditLogSearch\AuditLogSearchLog.txt"
   $outputFile = "d:\AuditLogSearch\AuditLogRecords.csv"
   [DateTime]$start = [DateTime]::UtcNow.AddDays(-1)
   [DateTime]$end = [DateTime]::UtcNow
   $record = "AzureActiveDirectory"
   $resultSize = 5000
   $intervalMinutes = 60
   
   #Start script
   [DateTime]$currentStart = $start
   [DateTime]$currentEnd = $start
   
   Function Write-LogFile ([String]$Message)
   {
       $final = [DateTime]::Now.ToUniversalTime().ToString("s") + ":" + $Message
       $final | Out-File $logFile -Append
   }
   
   Write-LogFile "BEGIN: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize."
   Write-Host "Retrieving audit records for the date range between $($start) and $($end), RecordType=$record, ResultsSize=$resultSize"
   
   $totalCount = 0
   while ($true)
   {
       $currentEnd = $currentStart.AddMinutes($intervalMinutes)
       if ($currentEnd -gt $end)
       {
           $currentEnd = $end
       }
   
       if ($currentStart -eq $currentEnd)
       {
           break
       }
   
       $sessionID = [Guid]::NewGuid().ToString() + "_" +  "ExtractLogs" + (Get-Date).ToString("yyyyMMddHHmmssfff")
       Write-LogFile "INFO: Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       Write-Host "Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       $currentCount = 0
   
       $sw = [Diagnostics.StopWatch]::StartNew()
       do
       {
           $results = Search-UnifiedAuditLog -StartDate $currentStart -EndDate $currentEnd -RecordType $record -SessionId $sessionID -SessionCommand ReturnLargeSet -ResultSize $resultSize
   
           if (($results | Measure-Object).Count -ne 0)
           {
               $results | export-csv -Path $outputFile -Append -NoTypeInformation
   
               $currentTotal = $results[0].ResultCount
               $totalCount += $results.Count
               $currentCount += $results.Count
               Write-LogFile "INFO: Retrieved $($currentCount) audit records out of the total $($currentTotal)"
   
               if ($currentTotal -eq $results[$results.Count - 1].ResultIndex)
               {
                   $message = "INFO: Successfully retrieved $($currentTotal) audit records for the current time range. Moving on!"
                   Write-LogFile $message
                   Write-Host "Successfully retrieved $($currentTotal) audit records for the current time range. Moving on to the next interval." -foregroundColor Yellow
                   ""
                   break
               }
           }
       }
       while (($results | Measure-Object).Count -ne 0)
   
       $currentStart = $currentEnd
   }
   
   Write-LogFile "END: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize, total count: $totalCount."
   Write-Host "Script complete! Finished retrieving audit records for the date range between $($start) and $($end). Total count: $totalCount" -foregroundColor Green
   ```

2. Arama ölçütlerini yapılandırmak için aşağıdaki tabloda listelenen değişkenleri değiştirin. Betik bu değişkenler için örnek değerler içerir, ancak bunları (aksi belirtilmedikçe) özel gereksinimlerinizi karşılayacak şekilde değiştirmeniz gerekir.

   <br>

   ****

   |Değişken|Örnek değer|Açıklama|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Betik tarafından gerçekleştirilen denetim günlüğü aramasının ilerleme durumu hakkında bilgi içeren günlük dosyasının adını ve konumunu belirtir. Betik, günlük dosyasına UTC zaman damgaları yazar.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Betik tarafından döndürülen denetim kayıtlarını içeren CSV dosyasının adını ve konumunu belirtir.|
   |`[DateTime]$start` Ve `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Denetim günlüğü araması için tarih aralığını belirtir. Betik, belirtilen tarih aralığında gerçekleşen denetim etkinliklerinin kayıtlarını döndürür. Örneğin, Ocak 2021'de gerçekleştirilen etkinlikleri döndürmek için başlangıç tarihi ve bitiş tarihi `"2021-01-01"` `"2021-01-31"` kullanabilirsiniz (değerleri çift tırnak işaretiyle çevrelediğinizden emin olun) Betikteki örnek değer, önceki 24 saat içinde gerçekleştirilen etkinliklerin kayıtlarını döndürür. Değere bir zaman damgası eklemezseniz, varsayılan zaman damgası belirtilen tarihte 12:00 (gece yarısı) olur.|
   |`$record`|"AzureActiveDirectory"|Aranacak denetim etkinliklerinin ( *işlemler* olarak da adlandırılır) kayıt türünü belirtir. Bu özellik, bir etkinliğin tetiklediği hizmeti veya özelliği gösterir. Bu değişken için kullanabileceğiniz kayıt türlerinin listesi için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Kayıt türü adını veya ENUM değerini kullanabilirsiniz. <br/><br/>**Ipucu:** Tüm kayıt türlerinin denetim kayıtlarını döndürmek için değerini `$null` kullanın (çift tırnak işaretleri olmadan).|
   |`$resultSize`|5000|**Search-UnifiedAuditLog** cmdlet'i betik tarafından her çağrıldığında döndürülen sonuç sayısını belirtir (*sonuç kümesi* olarak adlandırılır). 5.000 değeri, cmdlet tarafından desteklenen en büyük değerdir. Bu değeri olduğu gibi bırakın.|
   |`$intervalMinutes`|60|Döndürülen 5000 kayıt sınırını aşmaya yardımcı olmak için, bu değişken belirttiğiniz veri aralığını alır ve daha küçük zaman aralıklarına dilimler. Artık tarih aralığının tamamı değil her aralık, komutun 5000 kayıt çıkış sınırına tabidir. Tarih aralığındaki 60 dakikalık aralık başına varsayılan 5000 kayıt değeri çoğu kuruluş için yeterli olmalıdır. Ancak, betik şunu belirten bir hata döndürürse, `maximum results limitation reached`zaman aralığını azaltın (örneğin, 30 dakika, hatta 15 dakika) ve betiği yeniden çalıştırın.|
   ||||

   Önceki tabloda listelenen değişkenlerin çoğu **Search-UnifiedAuditLog** cmdlet'inin parametrelerine karşılık gelir. Bu parametreler hakkında daha fazla bilgi için bkz [. Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Yerel bilgisayarınızda Windows PowerShell açın ve değiştirilen betiği kaydettiğiniz klasöre gidin.

4. Betiği Exchange Online PowerShell'de çalıştırın; örneğin:

   ```powershell
   .\SearchAuditLog.ps1
   ```

Betik, çalışırken ilerleme iletilerini görüntüler. Betiğin çalışması tamamlandıktan sonra, denetim kayıtlarını içeren günlük dosyasını ve CSV dosyasını oluşturur ve ve değişkenleri tarafından tanımlanan klasörlere `$logFile` `$outputFile` kaydeder.

> [!IMPORTANT]
> Betikte cmdlet'i her çalıştırdığınızda döndürülen denetim kaydı sayısı üst sınırı 50.000'dir. Bu betiği çalıştırırsanız ve 50.000 sonuç döndürürse, tarih aralığında gerçekleşen etkinliklerin denetim kayıtlarının dahil edilmemiş olması olasıdır. Böyle bir durumda, tarih aralığını daha küçük sürelere bölmenizi ve ardından her tarih aralığı için betiği yeniden çalıştırmanızı öneririz. Örneğin, 90 günlük bir tarih aralığı 50.000 sonuç döndürürse betiği, tarih aralığındaki ilk 45 gün için bir kez ve ardından sonraki 45 gün boyunca olmak üzere iki kez yeniden çalıştırabilirsiniz.

## <a name="step-3-format-and-view-the-audit-records"></a>3. Adım: Denetim kayıtlarını biçimlendirme ve görüntüleme

Betiği çalıştırdıktan ve denetim kayıtlarını bir CSV dosyasına aktardıktan sonra, denetim kayıtlarını gözden geçirmeyi ve çözümlemeyi kolaylaştırmak için CSV'yi biçimlendirmek isteyebilirsiniz. Bunu gerçekleştirmenin bir yolu, **AuditData** sütunundaki JSON nesnesindeki her özelliği kendi sütununa bölmek için Excel Power Query JSON dönüştürme özelliğidir. Adım adım yönergeler için, denetim günlüğü kayıtlarını dışarı aktarma[, yapılandırma ve görüntüleme](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor) başlığı altındaki "2. Adım: Power Query Düzenleyicisi kullanarak dışarı aktarılan denetim günlüğünü biçimlendirme" bölümüne bakın.
