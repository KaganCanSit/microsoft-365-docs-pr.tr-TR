---
title: eBulma olaylarında 10 ayrı tutan rapor oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/11/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: eBulma servis örnekleriyle ilişkilendirilmiş tüm esnalar hakkında bilgi içeren bir rapor oluşturma hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 953b2aaa1b133d79b82f17e5f75603947cc5d6d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988106"
---
# <a name="create-a-report-on-holds-in-ediscovery-cases"></a>eBulma olaylarında 10 ayrı tutan rapor oluşturma

Bu makaledeki betik, eBulma yöneticilerinin ve eBulma yöneticilerinin, Office 365 veya Microsoft 365'daki uyumluluk merkezinde eBulma servisleriyle ilişkilendirilmiş tüm beklemelerle ilgili bilgileri içeren bir rapor oluşturmalarını sağlar. Raporda, bir tutma durumunda yer alan dosyanın adı, beklemede tutulan içerik konumları ve tutmanın sorgu tabanlı olup olmadığı gibi bilgiler yer almaktadır. Hiçbir mızrı olmayan durumlar varsa, betik, var olan durumlar listesi olan ek bir rapor sağlar.

Rapora [dahil edilen](#more-information) bilgilerin ayrıntılı açıklaması için Daha fazla bilgi bölümüne bakın.

## <a name="admin-requirements-and-script-information"></a>Yönetici gereksinimleri ve betik bilgileri

- Organizasyonlu tüm eBulma davaları hakkında rapor oluşturmak için, kuruluşta eBulma Yöneticisi olmak gerekir. eBulma Yöneticisiysiniz, rapor yalnızca eriş erişiminiz olan vakalar hakkında bilgi içerir. eBulma izinleri hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

- Bu makaledeki betikte çok az hata işleme vardır. Temel amacı, kurumuz tarafından eBulma davaları ile ilişkili tığlar hakkında hızlıca rapor oluşturmaktır.

- Bu konu başlığı altında verilen örnek betikler, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenemmektedir. Örnek betikler hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiklerin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>1. Adım: Bağlan ve Uyumluluk & PowerShell'e geçin

İlk adım, güvenlik ve uyumluluk & PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz. Güvenlik [Bağlan Uyumluluk Merkezi PowerShell& e geçin](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>2. Adım: eBulma durumleriyle ilişkilendirilmiş 12. adım: Betiği çalıştırarak eBulma durumlarını bildirme

Güvenlik ve Uyumluluk Merkezi PowerShell& e bağlandıktan sonra, bir sonraki adım, kurumdaki eBulma örnekleri hakkında bilgi toplayan betiği oluşturmak ve çalıştırmaktır.

1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, CaseHoldsReport.ps1.

   ```powershell
   #script begin
   " "
   write-host "***********************************************"
   write-host "   Security & Compliance Center   " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "        eDiscovery cases - Holds report         " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "***********************************************"
   " "
   #prompt users to specify a path to store the output files
   $time=get-date
   $Path = Read-Host 'Enter a file path to save the report to a .csv file'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casestatus,
   [datetime]$casecreatedtime,
   [string]$casemembers,
   [datetime]$caseClosedDateTime,
   [string]$caseclosedby,
   [string]$holdname,
   [String]$Holdenabled,
   [string]$holdcreatedby,
   [string]$holdlastmodifiedby,
   [string]$ExchangeLocation,
   [string]$sharePointlocation,
   [string]$ContentMatchQuery,
   [datetime]$holdcreatedtime,
   [datetime]$holdchangedtime
   )
   $addRow = New-Object PSObject
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case name" -Value $casename
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case status" -Value $casestatus
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case members" -Value $casemembers
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case created time" -Value $casecreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed time" -Value $caseClosedDateTime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed by" -Value $caseclosedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold name" -Value $holdname
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold enabled" -Value $Holdenabled
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created by" -Value $holdcreatedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold last changed by" -Value $holdlastmodifiedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Exchange locations" -Value  $ExchangeLocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "SharePoint locations" -Value $sharePointlocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold query" -Value $ContentMatchQuery
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created time (UTC)" -Value $holdcreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold changed time (UTC)" -Value $holdchangedtime
   $allholdreport = $addRow | Select-Object "Case name","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }

   " "
   Write-host "Script complete! Report files saved to this folder: '$Path'"
   " "
   #script end
   ```

2. 1. Windows PowerShell açılan Yeni Oturumda, betiği kaydeden klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Betik, raporu kaydetmek için bir hedef klasör girmenizi sağlar.

4. Raporu kaydetmek istediğiniz klasörün tam yol adını yazın ve Enter tuşuna **basın**.

   > [!TIP]
   > Raporu betiğin bulunduğu klasöre kaydetmek için, hedef klasör istendiğinde bir nokta (".") yazın. Raporu betiğin bulunduğu klasördeki bir alt klasöre kaydetmek için, alt klasörün adını yazmanız gerekir.

   Betik, tüm eBulma davaları hakkında kuruluş bilgilerini toplamaya başlar. Betik çalışırken rapor dosyasına erişin. Betik tamamlandıktan sonra, son oturumda onay Windows PowerShell görüntülenir. Bu ileti görüntülendikten sonra, 4. Adımda belirttiğiniz klasördeki rapora erişebilirsiniz. Raporun dosya adıdır `CaseHoldsReport<DateTimeStamp>.csv`.

   Bunun yanı sıra, betik 2013'lerde 1500'den fazla özel durum raporu bulundurarak rapor oluşturur. Bu raporun dosya adıdır `CaseswithNoHolds<DateTimeStamp>.csv`.

   Bu betiği çalıştırma örneği CaseHoldsReport.ps1.

   ![Betiği çalıştırdikten sonra CaseHoldsReport.ps1.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Daha fazla bilgi

Olay, bu makaledeki betiği çalıştırarak oluşturulan ve her tutma hakkında aşağıdaki bilgileri içerir. Daha önce de belirtildiği gibi, bir eBulma Yöneticisi olarak, kurumda tüm esnat bilgilerini iade etmek için bir eBulma Yöneticisi olmak gerekir. Servis servis servis adayları hakkında daha fazla bilgi için bkz. [eBulma servis örnekleri](./get-started-core-ediscovery.md).

- Tutma adı ve ile ilişkilendirilmiş eBulma dava adı.

- eBulma olaylarının etkin veya kapalı olup olmadığı.

- Tutmanın etkin veya devre dışı bırakılabilir olup olmadığı.

- Tutma ile ilişkilendirilmiş eBulma davalarının üyeleri. Vaka üyeleri, atandığı eBulma izinlerine bağlı olarak vakayı  görüntülemek veya yönetmek için bu izinleri ister.

- Vakanın oluşturulmuş olduğu saat ve tarih.

- Bir dava kapatılırsa kapatılan kişi, kapatılan kişi ile kapatılan saat ve tarihtir.

- Posta Exchange ve SharePoint konumlarını tutmadan önce kullanabilirsiniz.

- Tutma, sorgu tabanlı bir söz dizimidir.

- Tutmanın saat ve tarihi, oluşturulduğunda bu tarihi oluşturan kişidir.

- Tutmanın en son değiştir değiştirme saati ve tarihi ve bunu değiştiren kişi.