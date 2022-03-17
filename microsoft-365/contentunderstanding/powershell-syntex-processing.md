---
title: Belge anlama modeliyle işlem yapmak isteği için PowerShell kullanma
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Belge anlama modeliyle iş yapmayı talep etmek için PowerShell SharePoint Syntex kullanmayı öğrenin.
ms.openlocfilehash: 8f66a0cc5e59ad2ccb6b92d98cfaee8ce84470f2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526452"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>Belge anlama modeliyle işlem yapmak isteği için PowerShell kullanma

> [!IMPORTANT]
> En SharePoint Syntex PowerShell cmdlet'leri ve diğer tüm PnP bileşenleri, bunlar için destek sağlayan etkin bir topluluk tarafından desteklenen açık kaynak araçlarıdır. Resmi Microsoft destek kanallarından açık kaynak araç desteği için SLA yoktur.

Belge anlama modelleri, yeni karşıya yüklenen dosyaları kitaplı kitaplılara işler. Ayrıca kullanıcı arabiriminde el ile işlem yapmak da mümkündür. Bununla birlikte, PowerShell aracılığıyla işlemeyi tetiklemenin daha verimli olduğu senaryolar olabilir.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>Daha önce sınıflandırılmış tüm öğelerin işlemini talep

Kitaplıkta daha önce sınıflandırılmış olan tüm öğeler için şu komutu kullanarak işleme isteğinde bulunmaktadır:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

Daha düşük öncelikli işleme için, kiracınız bulunduğu iş saatleri dışında iş için dosyaları sıraya alan -OffPeak parametresini kullanmayı da göz önünde bulundurabilirsiniz. Daha [fazla ayrıntı için bkz. Request-PnPSyntexClassifyAndExtract](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) .

## <a name="request-processing-of-all-items-in-a-library"></a>Kitaplıkta tüm öğelerin işlemesini talep edin

Daha önce sınıflandırılmış olsalar bile kitaplıkta tüm dosyaların işlemesini talep edin. Bir modeli güncelleştirilmiş veya kitaplı kitaplara başka bir model eklenmişse, bu yararlı olabilir.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> -Force seçeneğini 5000'den fazla öğeyle kullanmak tepe işlemeyi otomatik olarak etkinleştirir.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Bir özele dayalı olarak tüm öğelerin işlemesi isteği

İşlemeyi kitaplıkta belirli bir öğe alt kümesiyle sınırlandır etmek için, betik kullanarak belirli bir dosya grubunu seçin. Aşağıdaki örnekte, betik bir alanın seçili ve bir alan değerine göre filtre uygulamana izin verir. [Get-PnPListItem kullanılarak daha karmaşık sorgular tamamlandıktan sonra](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"
$list = Get-PnPList -Identity "Documents"
# Set the field name to filter items by
$fieldName = "Vendor"
# Set the field value to filter by
$fieldFilter = "Fabrikam"

$listItems = (Get-PnPListItem -List $list -fields $fieldName).fieldValues
$targetItems = $listItems | Where-Object -Property Provider -EQ -Value $fieldFilter

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
foreach ($listItem in $targetItems) {
    Request-PnPSyntexClassifyAndExtract -FileUrl $listItem.FileRef -Batch $classifyBatch
}

# Execute batch
Invoke-PnPBatch -Batch $batch
```

## <a name="request-processing-of-specific-files"></a>Belirli dosyaların işlemesi isteği

Belirli dosyalar için işlemenin de istenen bir işlem olması gerekir.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

Dosya modeline göre dosya toplu işlemi de destekler:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx" -Batch $batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/relecloud contract.docx" -Batch $batch

# Execute batch
Invoke-PnPBatch -Batch $batch
```
