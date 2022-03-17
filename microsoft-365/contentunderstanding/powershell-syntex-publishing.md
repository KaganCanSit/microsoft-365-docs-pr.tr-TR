---
title: PowerShell ile belgeyi anlama modellerini yayımlama
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
description: PowerShell ile modelleri anlayan SharePoint Syntex belge yayımlamayı öğrenin.
ms.openlocfilehash: 5169e5ea5839cd5c341baa2477fd82281f5e5d76
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526492"
---
# <a name="publish-document-understanding-models-with-powershell"></a>PowerShell ile belgeyi anlama modellerini yayımlama

> [!IMPORTANT]
> En SharePoint Syntex PowerShell cmdlet'leri ve diğer tüm PnP bileşenleri, bunlar için destek sağlayan etkin bir topluluk tarafından desteklenen açık kaynak araçlarıdır. Resmi Microsoft destek kanallarından açık kaynak araç desteği için SLA yoktur.

SharePoint Syntex, genellikle kiracınız genelinde belge kitaplıklarına dağıtılır. Bu, içerik merkezi sitesi kullanılarak da yapılabilir, ancak bu, bu makalede de [açıklanan PnP PowerShell](https://pnp.github.io/powershell/) kullanılarak da yapılabilir.

## <a name="listing-the-available-models-in-a-content-center"></a>İçerik merkezinde kullanılabilir modelleri listeleme

Geçerli içerik merkezi sitesine eklenen modellere genel bir SharePoint Syntex için [Get-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html) cmdlet'ini kullanın:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>Kitaplı kitaplı kitaplara model uygulama

Kitaplık bir modeli uygulamak için [Publish-PnPSyntexModel cmdlet'ini](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) kullanın:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>Modelin nerede kullanılır olduğunu anlama

Modeli birçok kitaplara dağıttıktan sonra, modelinizi kullanarak kitaplıklar listesini gözden geçirmek iyi olabilir. Bu, [Get-PnPSyntexModelPublication cmdlet'i](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) kullanılarak yapılabilir:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>Bir modeli kitaplıktan kaldırma

Bir modeli kitaplıktan kaldırma işlemi, uygulamayla aynı düzeni izler ve [Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) cmdlet'i etkileşimli olarak veya birden çok eylem toplu işlemi olarak yapılabilir.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>Modelleri toplu olarak uygulama

Birden çok kitaplıkta birden çok model yayımlamak için modelleri ve hedef konumları listelayan bir giriş CSV dosyası oluşturun:

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

Bu CSV dosyası, listelenen modelleri uygun kitaplıklarda yayımlayan bir betikte giriş olarak kullanılabilir. Aşağıdaki örnekte, isteklerin verimliliğini artırmak için toplu işlem kullanılır.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourSite"
$targetsCSV = "./Publish-SyntexModelBulk.csv"

Connect-PnPOnline -url $contentCenterURL

$targetLibraries = Import-Csv -Path $targetsCSV

$batch = New-PnPBatch

foreach ($target in $targetLibraries) {
    Publish-PnPSyntexModel -Model $target.ModelName -TargetSiteUrl $target.TargetSiteUrl -TargetWebServerRelativeUrl $target.TargetWebServerRelativeUrl -TargetLibraryServerRelativeUrl $target.TargetLibraryServerRelativeUrl -Batch $batch
}

Invoke-PnPBatch -Batch $batch
```
