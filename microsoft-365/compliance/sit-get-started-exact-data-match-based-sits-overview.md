---
title: Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas bilgi türlerine göre tam veri eşleşmesi oluşturmaya başlama.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75650484368b6ccbaf6f6d39aeead133403f5b8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526284"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama

Veri eşleşmesi (EDM) tabanlı hassas bilgi türünü (SIT) oluşturmak ve tam olarak kullanılabilir yapmak, çok aşamalı bir işlemdir. Bunlar veri kaybı önleme ilkelerinde, eBulma ve bazı içerik yönetim görevlerinde kullanılabilir Bu makalede, iş akışı ana hatlarıyla ve aşamalardan her biri için yordamların bağlantıları ana hatlarıyla açıklanmıştır

## <a name="before-you-begin"></a>Başlamadan önce

Bu makalelerde kavramlara ve terminolojiye kendinizi tanıma:

- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Bu makalede açıklanan görevleri gerçekleştirmek için genel yönetici, Exchange Online veya uyumluluk yöneticisi ya da genel yönetici gerekir. DLP izinleri hakkında daha fazla bilgi edinmek için İzinler'e [bakın](data-loss-prevention-policies.md#permissions).

Tam lisans [bilgileri için veri kaybı](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) önleme hizmet açıklamasına bakın

## <a name="portal-links-for-your-subscription"></a>Aboneliğiniz için portal bağlantıları

|Portal|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender portalı|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft 365 Uyumluluk Merkezi|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Bir bakışta iş akışı

![tam veri eşleşmesi iş akışı aşamaları](..\media\swimlane_edm_process.png)


|Aşama|Gerekenler|
|---|---|
|[Aşama 1: Temel alınan hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- Hassas verilere erişimi okuma|
|[Aşama 2: Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Sihirbazda hassas bilgi türü sihirbazına Microsoft 365 yönetim merkezi </br>- Güvenlik Microsoft 365 yönetim merkezi [Uyumluluğu PowerShell aracılığıyla & erişim](/powershell/exchange/connect-to-scc-powershell) |
|[Aşama 3: Hassas bilgi türleriyle tam olarak eşleşmesi için karma sağlama ve hassas bilgi kaynağı tablosuna yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- Özel güvenlik grubu ve kullanıcı hesabı </br>- **Karma ve tek bir bilgisayardan karşıya yükleme**: doğrudan İnternet erişimi olan bir bilgisayara yerel yönetici erişimi ve EDM Yönetici Upload barındırma </br>- **Karma** ve ayrı bilgisayarlardan karşıya yükleme: doğrudan internet erişimi olan bir bilgisayara yerel yönetici erişimi ve EDM Upload Aracısı'nın yük yük farklı bir bilgisayara ve EDM Upload Aracısı'nın barındır yer alan güvenli bir bilgisayara yerel yönetici erişimini barındırarak hassas bilgi kaynağı tablolarını karma hale </br>- Hassas bilgi kaynağı tablo dosyasına okuma erişimi </br> şema dosyası |
|[Aşama 4: Hassas bilgi türü/kural paketiyle tam olarak eşan veriler oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Uyumluluk Merkezi'Microsoft 365 erişim |
|[Hassas bilgi türüyle tam olarak eşan bir veri sınaması](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Uyumluluk Merkezi'Microsoft 365 erişim

## <a name="see-also"></a>Ayrıca bkz.

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
