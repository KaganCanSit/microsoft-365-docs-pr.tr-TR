---
title: DLP ilkelerinde duyarlılık etiketlerini koşul olarak kullanma
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
description: DLP ilkelerinde koşul olarak duyarlılık etiketlerini kullanabileceğiniz hizmetler ve öğe türleri hakkında bilgi edinin
ms.openlocfilehash: 55803a2c354890264f99753af2aa6337cf49182a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632409"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>DLP ilkelerinde duyarlılık etiketlerini koşul olarak kullanma

[Duyarlılık etiketlerini](sensitivity-labels.md) şu konumlar için DLP ilkelerinde koşul olarak kullanabilirsiniz:

- E-posta iletilerini Exchange Online
- SharePoint Online
- siteleri OneDrive İş
- cihazları Windows 10

Duyarlılık etiketleri **İçerik içerir** listesinde bir seçenek olarak görünür.

> [!div class="mx-imgBorder"]
> ![duyarlılık etiketi bir koşul olarak.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> DLP ilkesini uygulamak için bir konum olarak **Teams sohbetini ve kanal iletilerini** seçtiyseniz, koşul olarak **Duyarlılık Etiketleri** kullanılamaz.


## <a name="supported-items-scenarios-and-policy-tips"></a>Desteklenen öğeler, senaryolar ve ilke ipuçları

Duyarlılık etiketlerini bu öğelerde ve bu senaryolarda koşul olarak kullanabilirsiniz.

### <a name="supported-items"></a>Desteklenen öğeler

|Hizmet  |Öğe türü  |İlke ipucu için kullanılabilir  |Uygulanabilir  |
|---------|---------|---------|---------|
|Exchange    |e-posta iletisi         |Evet         |Evet         |
|Exchange    |e-posta eki         |No         |Evet , *         |
|SharePoint Online     |SharePoint Online'daki öğeler         |Evet         |Evet         |
|OneDrive İş     |Bileşen         |Evet         |Evet         |
|Teams     |Ekipler ve kanal iletileri         |geçerli değil         |geçerli değil         |
|Teams     |Ekleri         |Evet **         |Evet **         |
|cihazları Windows 10     |Bileşen         |Evet         |Evet         |
|MCAS (önizleme) |Bileşen         |Evet         |Evet         |

\* Duyarlılık etiketli e-posta eklerinin DLP algılaması yalnızca Open XML tabanlı Office dosya türleri için desteklenir.

\** Teams'de 1:1 sohbet veya kanal üzerinden gönderilen ekler otomatik olarak OneDrive İş ve SharePoint'e yüklenir. Dolayısıyla SharePoint Online veya OneDrive İş DLP ilkenize konum olarak dahil edilirse, Teams'de gönderilen etiketli ekler bu koşulun kapsamına otomatik olarak eklenir. DLP ilkesinde konum olarak Teams'in seçilmesi gerekmez.

> [!NOTE]
> DLP'nin SharePoint ve OneDrive İş'teki duyarlılık etiketlerini algılama özelliği sınırlıdır. Daha fazla bilgi için bkz [. SharePoint ve OneDrive'da Office dosyaları için duyarlılık etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Desteklenen senaryolar

- DLP Yönetici, koşul olarak bir veya daha fazla duyarlılık etiketi eklemeyi seçtiğinde kiracıdaki tüm duyarlılık etiketlerinin listesini görebilir.

- Duyarlılık etiketlerini koşul olarak kullanmak, yukarıdaki destek matrisinde belirtildiği gibi tüm iş yüklerinde desteklenir.

- DLP ilkesi ipuçları, bir koşul olarak duyarlılık etiketi içeren DLP ilkeleri için iş yüklerinde (Outlook Win32 hariç) gösterilmeye devam eder.

- Duyarlılık etiketleri, bir koşul olarak duyarlılık etiketine sahip bir DLP ilkesi eşleştirilirse olay raporu e-postasının bir parçası olarak da görünür.

- Duyarlılık etiketi ayrıntıları, bir koşul olarak duyarlılık etiketi içeren bir DLP ilkesi eşleşmesi için DLP kuralı eşleştirme denetim günlüğünde de gösterilir.


### <a name="support-policy-tips"></a>Destek ilkesi ipuçları


|Iş yük -ünü  |desteklenen/desteklenmeyen ilke ipuçları  |
|---------|---------|
|OWA |    Desteklenen     |
|Outlook Win 32    |  desteklenmiyor       |
|SharePoint   |   Desteklenen      |
|OneDrive İş    |    Desteklenen     |
|uç nokta cihazları   |  desteklenmiyor       |
