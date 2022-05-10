---
title: Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama
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
description: Kullanmaya başlayın tam veri oluşturma, temel hassas bilgi türleriyle eşleşsin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 592a4c7342af9ffe5c18d0d25b99b12cd1b3e212
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294679"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tam olarak veri eşleşmesi (EDM) tabanlı hassas bilgi türü (SIT) oluşturmak ve kullanıma sunulması çok fazlı bir işlemdir. Microsoft Purview veri kaybı önleme ilkeleri, eBulma ve belirli içerik idaresi görevlerinde kullanılabilirler Bu makalede iş akışı özetlenir ve aşamaların her birine yönelik yordamlara bağlantılar açıklanır

## <a name="before-you-begin"></a>Başlamadan önce

Bu makalelerdeki kavramlar ve terimler hakkında bilgi edinin:

- [Hassas bilgi türleri hakkında daha fazla bilgi edinme](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="supported-regions"></a>Desteklenen bölgeler

Tam veri eşleşmesi şu bölgelerde kullanılabilir:

- Asya Pasifik
- Avustralya
- Brezilya
- Kanada
- Avrupa
- Fransa
- Almanya
- Hindistan
- Japonya
- Kore
- Norveç
- South Africa
- İsviçre
- Birleşik Arap Emirlikleri
- Birleşik Krallık
- Amerika Birleşik Devletleri
- ABD DoD
- ABD GCC
- ABD GCCH

Kiracınızın bekleyen verileri barındırdığı bölgeyi bulmak için [Microsoft 365 müşteri verilerinizin depolandığı yer](../enterprise/o365-data-locations.md) başlığındaki yordamları izleyebilir ve aynı makaledeki veri merkezi şehir konumlarına başvurabilirsiniz.

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Bu makalede açıklanan görevleri gerçekleştirmek için genel yönetici, uyumluluk yöneticisi veya Exchange Online yöneticisi olmanız gerekir. DLP izinleri hakkında daha fazla bilgi edinmek için bkz. [İzinler](data-loss-prevention-policies.md#permissions).

Tam lisans bilgileri için [veri kaybı önleme hizmeti açıklamasına](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) bakın

## <a name="portal-links-for-your-subscription"></a>Aboneliğiniz için portal bağlantıları

|Portal|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender portalı|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft Purview uyumluluk portalı|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Bir bakışta iş akışı

![tam veri eşleme iş akışı aşamaları](..\media\swimlane_edm_process.png)


|Aşama|Gerekenler|
|---|---|
|[1. Aşama: Tam veri eşleşmesi için kaynak verileri dışarı aktarma tabanlı hassas bilgi türü](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- Hassas verilere okuma erişimi|
|[2. Aşama: Tam veri eşleştirme tabanlı hassas bilgi türleri için şema oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Microsoft 365 yönetim merkezi hassas bilgi türü sihirbazına erişim </br>- [Güvenlik & Uyumluluğu PowerShell aracılığıyla Microsoft 365 yönetim merkezi](/powershell/exchange/connect-to-scc-powershell) erişimi |
|[3. Aşama: Hassas bilgi türleriyle tam eşleşmesi için hassas bilgi kaynağı tablosunu karma ve karşıya yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- Özel güvenlik grubu ve kullanıcı hesabı </br>- **Karma ve bir bilgisayardan karşıya yükleme**: Doğrudan İnternet erişimi olan bir bilgisayara yerel yönetici erişimi ve EDM Upload Aracısı'nı barındırma </br>- **Karma ve ayrı bilgisayarlardan karşıya yükleme**: Doğrudan İnternet erişimi olan bir bilgisayara yerel yönetici erişimi ve hassas bilgi kaynağı tablosunu karma hale getirmek için EDM Upload Aracısı'nı barındırmak üzere güvenli bir bilgisayara yükleme ve yerel yönetici erişimi için EDM Upload Aracısı'nı barındırma </br>- Hassas bilgi kaynağı tablo dosyasına okuma erişimi </br> şema dosyası |
|[4. Aşama: Hassas bilgi türü/kural paketiyle tam olarak eşleşen veriler oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Microsoft Purview uyumluluk portalına erişim |
|[Tam veri eşleşmesi hassas bilgi türünü test etme](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Microsoft Purview uyumluluk portalına erişim

## <a name="see-also"></a>Ayrıca bkz.

- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri için kaynak verilerini dışa aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
