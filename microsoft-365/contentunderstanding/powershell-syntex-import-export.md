---
title: PowerShell ile modelleri anlamak için belgeyi dışarı ve içeri aktarma
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
ms.localizationpriority: normal
description: PowerShell'de modelleri anlamak için belgeyi dışarı ve içeri aktarmayı ve SharePoint Syntex.
ms.openlocfilehash: 6751a66d713ada8c06445d8bfd0efdb5c3ac2fad
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "63014116"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>PowerShell ile modelleri anlamak için belgeyi dışarı ve içeri aktarma

> [!IMPORTANT]
> En SharePoint Syntex PowerShell cmdlet'leri ve diğer tüm PnP bileşenleri, bunlar için destek sağlayan etkin bir topluluk tarafından desteklenen açık kaynak araçlarıdır. Resmi Microsoft destek kanallarından açık kaynak araç desteği için SLA yoktur.

SharePoint Syntex PnP şablonları olarak dışarı aktararak içerik merkezleri veya kiracılar arasında yeniden kullanımı etkinleştirebilirsiniz.

## <a name="export-all-models-in-a-content-center"></a>İçerik merkezinde tüm modelleri dışarı aktarma

İçerik merkezinde bulunan tüm modelleri tek bir PnP şablonuna dışarı aktarma için aşağıdaki [PnP PowerShell](https://pnp.github.io/powershell/) cmdlet'lerini kullanın:

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Belirli modelleri dışarı aktarma

İçerik merkezinden PnP şablonuna belirli modelleri dışarı aktarma için, aşağıdaki [PnP PowerShell](https://pnp.github.io/powershell/) cmdlet'lerini kullanın:

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

extract.json dışarı aktarmak istediğiniz modelleri tanımlar ve modele göre ad veya kimlikle belirtmek ve isteğe bağlı olarak eğitim verilerini ayıklamak için yapılandırmaya izin verir.

### <a name="example---specify-model-by-name"></a>Örnek - Modeli adına göre belirtin

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "name": "Sample - benefits change notice.classifier"
            }
        ]
    }
}
```

### <a name="example---specify-model-by-id"></a>Örnek - Modele Göre Kimlik Belirtme

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "id": 3,
                "excludeTrainingData": true
            }
        ]
    }
}
```

"includeTrainingData" özelliğini dahil etmek yoksa, varsayılan davranış şunları eklemektir.

> [!NOTE]
> Bir modelin hedef içerik merkezine aktarılabilir olması için eğitim verileri gereklidir.

## <a name="import-models-to-a-content-center"></a>Modelleri içerik merkezine aktarma
PnP şablonlarına dışarı aktarılan modelleri anlama belgesi, herhangi bir kiracının içerik merkezine aktarıldı. Dışarı aktarmada eğitim verileri varsa, model bir kez aktarıldıktan sonra düzenlenebilir.

Bir modeli içeri aktarma işlemi için aşağıdaki komutları kullanın:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
