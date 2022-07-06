---
title: eBulma tutma raporu oluşturmak için betik kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 05/10/2022
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
description: eBulma servis talepleri ile ilişkili tüm ayrı tutmalar hakkında bilgi içeren bir rapor oluşturmayı öğrenin.
ms.openlocfilehash: 9820eba0e29a510a1881a9349f63c7e2d9650728
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625489"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>eBulma durumlarında ayrı tutmalar hakkında rapor oluşturmak için betik kullanma

Bu makaledeki betik, eBulma yöneticilerinin ve eBulma yöneticilerinin Microsoft Purview uyumluluk portalı eBulma (Standart) ve eBulma (Premium) durumlarıyla ilişkili tüm tutmalar hakkında bilgi içeren bir rapor oluşturmasına olanak tanır. Rapor, ayrı tutmanın ilişkilendirildiği servis talebinin adı, ayrı tutmaya yerleştirilen içerik konumları ve ayrı tutmanın sorgu tabanlı olup olmadığı gibi bilgileri içerir. Ayrı tutması olmayan durumlar varsa betik, ayrı tutma olmayan servis taleplerinin listesini içeren ek bir rapor oluşturur.

Rapora dahil edilen bilgilerin ayrıntılı açıklaması için [Daha fazla bilgi](#more-information) bölümüne bakın.

## <a name="admin-requirements-and-script-information"></a>Yönetici gereksinimleri ve betik bilgileri

- Kuruluşunuzdaki tüm eBulma durumlarına ilişkin bir rapor oluşturmak için, kuruluşunuzda eBulma Yöneticisi olmanız gerekir. eBulma Yöneticisiyseniz, rapor yalnızca erişebileceğiniz servis talepleri hakkında bilgi içerir. eBulma izinleri hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

- Bu makaledeki betikte en az hata işleme vardır. Birincil amaç, kuruluşunuzdaki eBulma servis talepleri ile ilişkili tutmalar hakkında hızla rapor oluşturmaktır.

- Bu konuda sağlanan örnek betikler, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betikler, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiklerin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-connect-to-security--compliance-powershell"></a>1. Adım: Güvenlik & Uyumluluğu PowerShell'e bağlanma

İlk adım, kuruluşunuz için Güvenlik & Uyumluluk PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz [. Güvenlik & Uyumluluk PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>2. Adım: eBulma servis talepleri ile ilişkili ayrı tutmaları raporlamak için betiği çalıştırın

Güvenlik & Uyumluluğu PowerShell'e bağlandıktan sonra, bir sonraki adım kuruluşunuzdaki eBulma servis talepleri hakkında bilgi toplayan betiği oluşturmak ve çalıştırmaktır.

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, CaseHoldsReport.ps1.

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
   $Path = Read-Host 'Enter a folder path to save the report to a .csv file (filename is created automatically)'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casetype,
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
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case type" -Value $casetype
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
   $allholdreport = $addRow | Select-Object "Case name","Case type","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Standard) cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Premium) cases and holds..."
   " "
   $edc =Get-ComplianceCase -CaseType Advanced -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus -casetype $cc.casetype $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
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

2. 1. Adımda açılan Windows PowerShell oturumunda, betiği kaydettiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Betik, raporun kaydedileceği hedef klasörü ister.

4. Raporu kaydetmek için klasörün tam yol adını yazın ve **Enter tuşuna** basın.

   > [!TIP]
   > Raporu betiğin bulunduğu klasöre kaydetmek için hedef klasör istendiğinde nokta (".") yazın. Raporu betiğin bulunduğu klasördeki bir alt klasöre kaydetmek için alt klasörün adını yazması gerekir.

   Betik, kuruluşunuzdaki tüm eBulma olayları hakkında bilgi toplamaya başlar. Betik çalışırken rapor dosyasına erişemezsiniz. Betik tamamlandıktan sonra, Windows PowerShell oturumunda bir onay iletisi görüntülenir. Bu ileti görüntülendikten sonra, rapora 4. Adımda belirttiğiniz klasörden erişebilirsiniz. Raporun dosya adı şeklindedir `CaseHoldsReport<DateTimeStamp>.csv`.

   Ayrıca betik, ayrı tutması olmayan servis taleplerinin listesini içeren bir rapor da oluşturur. Bu raporun dosya adı şeklindedir `CaseswithNoHolds<DateTimeStamp>.csv`.

   aşağıda CaseHoldsReport.ps1 betiğini çalıştırma örneği verilmiştır.

   ![CaseHoldsReport.ps1 betiğini çalıştırdıktan sonra çıkış.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Daha fazla bilgi

Servis talebi, bu makaledeki betiği çalıştırdığınızda oluşturulan raporu tutar ve her ayrı tutma hakkında aşağıdaki bilgileri içerir. Daha önce açıklandığı gibi, kuruluşunuzdaki tüm tutmalar için bilgi döndürmek için eBulma Yöneticisi olmanız gerekir. Servis talebi tutmaları hakkında daha fazla bilgi için bkz. [eBulma durumları](./get-started-core-ediscovery.md).

- Ayrı tutmanın adı ve ayrı tutmanın ilişkili olduğu eBulma servis talebinin adı.

- Ayrı tutmanın eBulma (Standart) veya eBulma (Premium) servis talebiyle ilişkili olup olmadığı.

- eBulma servis talebinin etkin veya kapalı olup olmadığı.

- Ayrı tutmanın etkinleştirilip etkinleştirilmediği veya devre dışı bırakılıp bırakılmadığı.

- Ayrı tutmanın ilişkili olduğu eBulma servis talebinin üyeleri. Servis talebi üyeleri, atanmış oldukları eBulma izinlerine bağlı olarak bir servis talebini görüntüleyebilir veya yönetebilir.

- Servis talebinin oluşturulduğu saat ve tarih.

- Bir servis talebi kapatılırsa, kapatılan kişi ve kapatıldığı saat ve tarih.

- Exchange posta kutuları ve SharePoint site konumları ayrı tutulmaktadır.

- Ayrı tutma sorgu tabanlıysa, sorgu söz dizimi.

- Ayrı tutmanın oluşturulduğu saat ve tarih ve bunu oluşturan kişi.

- Ayrı tutmanın son değiştirildiği saat ve tarih ve değiştiren kişi.
