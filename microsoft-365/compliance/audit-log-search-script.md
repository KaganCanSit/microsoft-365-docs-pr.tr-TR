---
title: Denetim günlüğünde arama yapmak için PowerShell betiği kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Denetim günlüğünde arama yapmak için Search-UnifiedAuditLog cmdlet'ini Exchange Online bir PowerShell betiği kullanın. Bu betik, her çalıştırışta büyük bir denetim kayıtları kümesi geri dönecek şekilde en iyi duruma getirildi. Betik, bu kayıtları bir CSV dosyasına dışarı aktarır ve bu dosyayı Power Query kullanarak görüntü veya Excel.
ms.openlocfilehash: 60f78f5a5eebeaa90f01b4b251d917f178c06ae9
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012876"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Denetim günlüğünde arama yapmak için PowerShell betiği kullanma

Günümüzdeki IT yöneticileri için güvenlik, uyumluluk ve denetim en öncelikli hale geldi. Microsoft 365, kuruluşların güvenlik, uyumluluk ve denetimi yönetmelerine yardımcı olacak çeşitli yerleşik özelliklere sahip olabilir. Özel olarak, birleşik denetim günlüğü güvenlik olaylarını ve uyumluluk sorunlarını araştırmanıza yardımcı olabilir. Aşağıdaki yöntemleri kullanarak denetim günlüklerini geri alın:

- [Office 365 Yönetimi Etkinlik API'si](/office/office-365-management-api/office-365-management-activity-api-reference)

- Denetim [günlüğü arama aracı](search-the-audit-log-in-security-and-compliance.md) Microsoft 365 uyumluluk merkezi

- Exchange Online [PowerShell'de Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'i

Denetim günlüklerini düzenli aralıklarla geri almak zorundaysanız, büyük kuruluşlara sürekli milyonlarca denetim kaydı almak için ölçeklenebilirlik ve performans sağlayabilse de, Office 365 Yönetim Etkinliği API'sini kullanan bir çözüm göz önünde bulundurabilirsiniz. Zaman aralığındaki denetim günlüğü arama Microsoft 365 uyumluluk merkezi, daha kısa bir süre içinde oluşan belirli işlemlerin denetim kayıtlarını hızla bulmak için iyi bir yol sağlar. Özellikle büyük kuruluşlar için denetim günlüğü arama aracında daha uzun süre aralıklarının kullanımı, kolayca yönetilemeyecek veya dışarı aktarılameyecek kadar çok kayıt verebilir.

Belirli bir araştırma veya olay için denetim verilerini el ile almanızı istediğiniz durumlar olduğunda, özellikle de büyük kuruluşlarda daha uzun tarih aralıkları için en iyi seçenek **Search-UnifiedAuditLog** cmdlet'ini kullanmak olabilir. Bu makalede, cmdlet'i kullanan bir PowerShell betiği vardır ve bu betik 50.000 denetim kaydına (cmdlet'i her çalıştırsanız) alabilir ve sonra da bunları Excel'te Power Query kullanarak biçimlendirebilir ve gözden geçirmenize yardımcı olabilir. Bu makaledeki betiği kullanmak, hizmette büyük denetim günlüğü aramalarına zaman çıkma riskini de en aza indirmektedir.

## <a name="before-you-run-the-script"></a>Betiği çalıştırmadan önce

- Denetim kayıtlarının geri dönmesi için betiğin başarılı bir şekilde kullan kullanışta olması için, denetim günlüğünün etkinleştirilmesi gerekir. Denetim günlüğü, kurumsal kuruluşlar tarafından denetlenen Microsoft 365 Office 365 açıktır. Kuruluşunız için denetim günlüğü aramalarının açık olduğunu doğrulamak için, Exchange Online PowerShell'de çalıştırabilirsiniz:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  `True` **UnifiedAuditLogIngestionEnabled** özelliğinin değeri, denetim günlüğü aramasında izinlerin açık olduğunu gösterir.

- Betiği başarılı bir şekilde View-Only için Exchange Online Günlükleri veya Denetim Günlükleri rolüne atanmış olmak gerekir. Varsayılan olarak, bu roller yönetim merkezinin İzinler sayfasında yer alan Uyumluluk Yönetimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. Daha fazla bilgi için, Uyumluluk merkezinde denetim günlüğünde arama yapın bölümündeki "Denetim [günlüğünde arama yapmak için gereksinimler" bölümüne bakın](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- Betiğin tamamlanması uzun sürebilir. Ne kadar süreyle çalıştırıldığında, tarih aralığı ve betiği denetim kayıtlarını almak için yapılandırılan aralığın boyutuna bağlıdır. Daha büyük tarih aralıkları ve daha küçük aralıklar uzun çalışma süresine neden olur. Tarih aralığı ve aralıklar hakkında daha fazla bilgi için 2. Adımdaki tabloya bakın.

- Bu makalede sağlanan örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiğin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiğin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgileri kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-connect-to-exchange-online-powershell"></a>1. Adım: Bağlan PowerShell Exchange Online e geri

İlk adım, Exchange Online PowerShell'e bağlanmaktir. Modern kimlik doğrulamayı kullanarak veya Çok Faktörlü Kimlik Doğrulaması (MFA) ile bağlanın. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>2. Adım: Denetim kayıtlarını almak için betiği değiştirme ve çalıştırma

Exchange Online PowerShell'e bağlandıktan sonra, sonraki adım denetim verilerini almak için betiği oluşturmak, değiştirmek ve çalıştırmaktır. Denetim günlüğü arama betiğinde ilk yedi satır, aramanızı yapılandırmak için değiştirerek değiştirerek, aşağıdaki değişkenleri içerir. Bu değişkenlerin açıklaması için 2. adımdaki tabloya bakın.

1. Dosya adı son eklerini kullanarak Windows PowerShell betiğine aşağıdaki metni .ps1. Örneğin, SearchAuditLog.ps1.

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

2. Arama ölçütlerini yapılandırmak için aşağıdaki tabloda listelenen değişkenleri değiştirebilirsiniz. Betik, bu değişkenler için örnek değerler içerir, ancak özel gereksinimlerinizi karşılamak için bunları değiştirebilirsiniz (aksi belirtilmedikçe).

   <br>

   ****

   |Değişken|Örnek değer|Açıklama|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Betik tarafından gerçekleştirilen denetim günlüğü aramanın ilerleme durumu hakkında bilgi içeren günlük dosyasının adını ve konumunu belirtir. Betik, günlük dosyasına UTC zaman damgası yazar.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Betik tarafından döndürülen denetim kayıtlarını içeren CSV dosyasının adını ve konumunu belirtir.|
   |`[DateTime]$start` ve `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Denetim günlüğü araması için tarih aralığını belirtir. Betik, belirtilen tarih aralığında  meydana gelen denetim etkinliklerinin kayıtlarını döner. Örneğin, Ocak 2021'de gerçekleştirilen etkinlikleri geri almak için başlangıç tarihi ve bitiş tarihi kullanabilirsiniz (değerleri çift tırnak içine almanız gerekir) betik dosyasındaki örnek değer, `"2021-01-01"` `"2021-01-31"` önceki 24 saat içinde gerçekleştirilen etkinliklerin kayıtlarını döndürür. Değere bir zaman damgası belirtilmezse, varsayılan zaman damgası belirtilen tarihte saat 12:00'dır.|
   |`$record`|"AzureActiveDirectory"|Aramanın denetim etkinliklerinin (işlem de denir) *kayıt* türünü belirtir. Bu özellik, etkinliğin tetiklendiğinde tetiklenen hizmeti veya özelliği gösterir. Bu değişken için kullanabileceğiniz kayıt türlerinin listesi için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Kayıt türü adını veya ENUM değerini kullanabilirsiniz. <br/><br/>**İpucu:** Tüm kayıt türlerinin denetim kayıtlarını geri almak için, değeri kullanın `$null` (çift tırnak işaretleri olmadan).|
   |`$resultSize`|5000|**Search-UnifiedAuditLog** cmdlet'i betik tarafından her çağrılsında döndürülen sonuç *sayısını (sonuç kümesi denir) belirtir*. 5.000 değeri, cmdlet tarafından desteklenen en büyük değerdir. Bu değeri olduğu gibi bırakın.|
   |`$intervalMinutes`|60|Döndürülen 5000 kayıt sınırını aşmanıza yardımcı olması için, bu değişken belirttiğiniz veri aralığını alır ve daha küçük zaman aralıkları halinde dilimler. Artık, tarih aralığının tamamı değil her aralık, komutun 5000 kayıt çıkış sınırına tabi olur. Tarih aralığı içindeki 60 dakikalık aralık başına 5000 kayıt varsayılan değeri çoğu kuruluş için yeterli olacaktır. Ancak betik, zaman aralığını (örneğin, `maximum results limitation reached`30 dakika veya 15 dakikaya kadar) azaltarak betiği yeniden çalıştırma hatasını döndürür.|
   ||||

   Önceki tabloda listelenen değişkenlerin çoğu **Search-UnifiedAuditLog cmdlet'inin** parametrelerine karşılık geldi. Bu parametreler hakkında daha fazla bilgi için bkz. [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Yerel bilgisayarınızda, Windows PowerShell'i açın ve değiştirilen betiği kaydeden klasöre gidin.

4. Betiği Exchange Online PowerShell'de çalıştırın; örneğin:

   ```powershell
   .\SearchAuditLog.ps1
   ```

Betik, çalışırken ilerleme durumu iletilerini görüntüler. Betiğin çalıştırması bittiğinde, denetim kayıtlarını içeren günlük dosyasını ve CSV dosyasını oluşturur ve bunları değişkenler ve değişkenler tarafından tanımlanan klasörlere `$logFile` `$outputFile` kaydeder.

> [!IMPORTANT]
> Betikte cmdlet'i her çalıştırışta döndürülen denetim kayıtlarının üst sınırı 50.000'dir. Bu betiği çalıştırarak 50.000 sonuç döndürürse, büyük olasılıkla tarih aralığı içinde 40.000'den fazla sonuç döndüren etkinliklere yönelik denetim kayıtları dahil değildir. Bu durumda, tarih aralığını daha küçük sürelere bölmenizi ve ardından her tarih aralığı için betiği yeniden çalıştırmanız önerilir. Örneğin, 90 günlük bir tarih aralığı 50.000 sonuç döndürürse, betiği iki kez, tarih aralığındaki ilk 45 gün için bir kez yeniden çalıştırarak sonraki 45 gün boyunca tekrar çalıştırarak devam  olabilir.

## <a name="step-3-format-and-view-the-audit-records"></a>3. Adım: Denetim kayıtlarını biçimlendirme ve görüntüleme

Betiği çalıştırarak denetim kayıtlarını BIR CSV dosyasına aktardıktan sonra, denetim kayıtlarının gözden geçirmesini ve çözümlemesini kolaylaştırmak için CSV'nin biçimini biçimlendirmek iyi olabilir. Bunu yapmak için bir yol, denetim verileri sütunundaki JSON nesnesinde yer alan her özelliği kendi sütununa bölmek için Excel'daki Power Query JSON dönüştürme özelliğidir. Adım adım yönergeler için, Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme'nin "2. Adım: Power Query Düzenleyicisi'ni kullanarak dışarı aktarılan denetim günlüğünü [biçimlendirme" makalesinde yer alan](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor) ".
