---
title: Python için Test Temel SDK'si
description: Python için Test Bankası'nın SDK'ini anlamayla ilgili ayrıntılar
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: article
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 9a4f64afbf02853ccb68098995c0f05baf2c9b01
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988761"
---
# <a name="test-base-sdk-for-python"></a>Python için Test Temel SDK'si

## <a name="overview"></a>Genel bakış
Test Temel SDK'si, Azure test temel kaynağıyla etkileşim kurmak için kullanılabilir. (Örneğin, uygulama paketinizi yönetin, paket oluştur, paketi düzenle ve paketi sil dahil)

SDK ile alınabilirsiniz test özeti ve Çözümleme Sonucu şunlardır: scriptExecution, güvenilirlik, memoryUtilization, cpuUtilization, memoryRegression, cpuRegression.

Test Temel SDK'si ile, test tabanını CI/CD ardışık düzeninde tümleştirebilirsiniz.

## <a name="client-library"></a>İstemci Kitaplığı

Boru ile test temel paketini yükleyin.

~~~
pip install  Microsoft.Testbase
~~~
 
## <a name="example"></a>Örnek
