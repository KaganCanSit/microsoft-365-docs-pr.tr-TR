---
title: DLP ilkelerde duyarlılık etiketlerini koşullar olarak kullanma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: DLP ilkelerinde duyarlılık etiketlerini koşullar olarak kullanabileceğiniz hizmetler ve öğe türleri hakkında bilgi
ms.openlocfilehash: 1117471e38b430f1d7289c6aae76994ac5acd494
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015173"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>DLP ilkelerde duyarlılık etiketlerini koşullar olarak kullanma

Duyarlılık [etiketlerini bu konumlar](sensitivity-labels.md) için DLP ilkeleri içinde bir koşul olarak kullanabilirsiniz:

- Exchange Online-posta iletilerini gönderme
- SharePoint Online
- OneDrive İş siteleri
- Windows 10 cihazları

Duyarlılık etiketleri İçerik içeriği listesinde bir **seçenek olarak** görünür.

> [!div class="mx-imgBorder"]
> ![duyarlılık etiketini bir koşul olarak kullanın.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **Bir koşul olarak** Duyarlılık Etiketleri, DLP İlkesi'nin Teams üzere sohbet  ve kanal iletilerini bir konum olarak seçtiyseniz kullanılamaz.


## <a name="supported-items-scenarios-and-policy-tips"></a>Desteklenen öğeler, senaryolar ve ilke ipuçları

Duyarlılık etiketlerini bu öğelerde ve bu senaryolarda koşullar olarak kullanabilirsiniz.

### <a name="supported-items"></a>Desteklenen öğeler

|Hizmet  |Öğe türü  |İlke ipucu için kullanılabilir  |Zorunlu  |
|---------|---------|---------|---------|
|Exchange    |e-posta iletisi         |evet         |evet         |
|Exchange    |e-posta eki         |hayır         |evet *         |
|SharePoint Online     |SharePoint Online'da öğeler         |evet         |evet         |
|OneDrive İş     |öğeler         |evet         |evet         |
|Teams     |Teams ve kanal iletileri gönderme         |uygulanamaz         |uygulanamaz         |
|Teams     |ekler         |evet **         |evet **         |
|Windows 10 cihazları     |öğeler         |evet         |evet         |
|MCAS (önizleme) |öğeler         |evet         |evet         |

\*DLP ile etiketli e-posta eklerinin duyarlılık algılanması yalnızca Office dosya türlerinde kullanılabilir.

\** Bire bir sohbet Teams kanallarında gönderilen ekler otomatik olarak bire bir sohbet veya kanallarda OneDrive İş SharePoint. Dolayısıyla SharePoint Online veya OneDrive İş DLP ilkenize konum olarak eklenirse, Teams'de gönderilen etiketli ekler otomatik olarak bu koşulun kapsamına dahil edilir. Teams olarak seçilenlerin DLP ilkesinde seçilmiş olması gerekir.

> [!NOTE]
> DLP'nin kurumsal ve kurumsal ağ etiketlerini SharePoint OneDrive duyarlılık etiketlerini algılama özelliği sınırlıdır. Daha fazla bilgi için bkz[. Dosya ve klasörlerin Office için duyarlılık SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Desteklenen senaryolar

- DLP Yöneticisi, bir veya daha fazla duyarlılık etiketine koşul olarak eklemeyi seçtiklerinden kiracının tüm duyarlılık etiketlerinin listesini görebilir.

- Duyarlılık etiketlerinin koşul olarak kullanımı, yukarıdaki destek matrisinde belirtildiği gibi tüm iş yükleri genelinde de desteklemektedir.

- DLP ilkesi ipuçları, duyarlılık etiketi içeren DLP ilkeleri için iş yükleri genelinde (Outlook Win32 hariç) gösterilmeye devam eder.

- Duyarlılık etiketleri, bir koşul olarak duyarlılık etiketine sahip bir DLP ilkesi eşlenmişse olay raporu e-postasında da görünür.

- Duyarlılık etiketi ayrıntıları, duyarlılık etiketi içeren bir DLP ilkesi eşleşmesi için DLP kuralı denetim günlüğünde de bir koşul olarak gösterilecektir.


### <a name="support-policy-tips"></a>Destek ilkesi ipuçları


|workload  |Desteklenen/desteklenmiyor ilke ipuçları  |
|---------|---------|
|OWA |    destek     |
|Outlook Win 32    |  desteklenmiyor       |
|SharePoint   |   destek      |
|OneDrive İş    |    destek     |
|uç nokta cihazları   |  desteklenmiyor       |
