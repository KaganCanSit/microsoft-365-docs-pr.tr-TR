---
title: ABD Microsoft 365 Defender müşterileri için müşteri adayları
description: ABD Kamu Microsoft 365 Defender gereksinimleri ve yetenekleri hakkında bilgi
keywords: kamu, gcc, yüksek, gereksinimler, özellikler, defender, Microsoft 365 Defender, xdr, dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 3e8f6e523a5483de99beb0af7d01ab96951b7a3e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996052"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>ABD Microsoft 365 Defender müşterileri için müşteri adayları

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender ABD Kamu Ortamı'nın yerleşik ABD Kamu müşterileri için, Azure Ticari'de yer alan ABD Microsoft 365 Defender temel alınan teknolojileri kullanır.

Bu teklif GCC, GCC High ve DoD müşterilerine sunulmaktadır ve ticari sürümle aynı engelleme, algılama, soruşturma ve düzeltmelerden temel alındı. Bununla birlikte, bu teklifin özelliklerinde bazı farklılıklar vardır.

> [!NOTE]
> Bulut Uygulamaları için Defender GCC Uç Nokta için Defender veya Ticari Olarak Kimlik için Defender kullanan bir müşteriyebilirsiniz, bu hizmetleri GCC sürümlerine uygun olacak şekilde Microsoft 365 Defender GCC.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Microsoft 365 Defender IÇIN MICROSOFT KAMU MÜŞTERILERI için aşağıdaki Microsoft toplu lisans tekliflerinden birini gerektirir:

### <a name="desktop-licensing"></a>Masaüstü lisansı

<br />

****

|GCC|GCC Yüksek|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 High için GCC.|MICROSOFT 365 için G5|
|Microsoft 365 G5 Güvenlik GCC|Microsoft 365 G5 Security for GCC High|Microsoft 365 DOD için G5 Güvenliği|
|Enterprise Mobility + Security G5 GCC|Enterprise Mobility + Security Yüksek için E5 GCC|dod Enterprise Mobility + Security E5|
|Office 365 G5 GCC|Office 365 E5 High için GCC.|DOD Office 365 E5 için iş|
|Bulut Uygulamaları için Microsoft Defender GCC|GCC High için Bulut Uygulamaları için Microsoft Defender|DOD için Bulut Uygulamaları için Microsoft Defender|
|Uç Nokta için Microsoft Defender - GCC|GCC High uç noktası için Microsoft Defender|DOD için Uç Nokta için Microsoft Defender|
|Kimlik için Microsoft Defender - GCC|GCC High için Identity için Microsoft Defender|DOD için Kimlik için Microsoft Defender|
|Office 365 için Microsoft Defender (Plan 2) GCC|GCC High için Office 365 için Microsoft Defender (Plan 2)|DOD için Office 365 Microsoft Defender (Plan 2)|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise yüksek için E5 GCC|dod Windows 10 Enterprise E5|
|

### <a name="server-licensing"></a>Sunucu lisansı

<br />

****

|GCC|GCC Yüksek|DoD|
|---|---|---|
|Endpoint Server 2010 için Microsoft Defender GCC|GCC High için Endpoint Server için Microsoft Defender|DOD için Uç Nokta Sunucusu için Microsoft Defender|
|Sunucular için Microsoft Defender|Sunucular için Microsoft Defender - Kamu|Sunucular için Microsoft Defender - Kamu|
|

## <a name="portal-urls"></a>Portal URL'leri

Aşağıda, ABD Kamu Microsoft 365 Defender portal URL'leri veleri ve):

<br />

****

|Müşteri türü|Portal URL'si|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC Yüksek|Rolling out|
|DoD|Rolling out|
|
> [!NOTE]
> GCC müşterisiysiniz ve Uç nokta ticari sürümü için Microsoft Defender'dan GCC'e taşıma sürecindeysanız, https://transition.security.microsoft.com Uç nokta ticari verileri için Microsoft Defender'ınıza erişmek için kullanın.

## <a name="api"></a>API

[API](api-overview.md) belgelerinde listelenen genel URL yerine, aşağıdaki URL'leri kullanasınız:

<br />

****

|Uç nokta türü|GCC|GCC High & DoD|
|---|---|---|
|Oturum açma|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Microsoft 365 Defender API'si|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Ticari özellik eşlik

Microsoft 365 Defender ABD Kamu müşterileri için yapılan ticari tekliflerle ilgili olarak tam olarak uygun olmayan müşterilere yönelik bir tekliftir. TÜM ticari özellikleri ve işlevleri ABD Kamu müşterilerine sunmakla birlikte, henüz mevcut olmayan bazı özellikleri vurgulamak için çalışıyoruz.

Bunlar bilinen boşluklardır:

<br />

****

|Özellik adı|GCC|GCC Yüksek|DoD|
|---|:---:|:---:|:---:|
|Tümleştirmeler: Microsoft Sentinel (Ham & Olaylar)|![Evet](../defender-endpoint/images/svg/check-yes.svg)|![Evet](../defender-endpoint/images/svg/check-yes.svg) Özel önizlemede|![Evet](../defender-endpoint/images/svg/check-yes.svg) Özel önizlemede|
|Microsoft Tehdit Uzmanları|![Hayır](../defender-endpoint/images/svg/check-no.svg) Mühendislik iş günlüğünde|![Hayır](../defender-endpoint/images/svg/check-no.svg) Mühendislik iş günlüğünde|![Hayır](../defender-endpoint/images/svg/check-no.svg) Mühendislik iş günlüğünde|

## <a name="more-details"></a>Diğer ayrıntılar

Daha fazla bilgi için US Gov sayfalarını tek tek iş yükleri ile birlikte ziyaret edin:
- [Bulut Uygulamaları için Microsoft Defender](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Kimlik için Microsoft Defender](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/gov).
