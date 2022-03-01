---
title: Dağıtım ve güncelleştirme kanalı örnek yapılandırmaları
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: Örnek kuruluşlar kanal kullanarak nasıl dağıtım ve güncelleştirmeler sağlar.
ms.openlocfilehash: 4e4ebfef9c505f3a6ac27726da9b1f6e5ebb932a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019535"
---
# <a name="deployment-and-update-channel-example-configurations"></a>Dağıtım ve güncelleştirme kanalı örnek yapılandırmaları

Windows 10 ve Microsoft 365 Uygulamaları kanalların hangi güncelleştirmeleri kullanacağı, kuruluşun türüne ve yeni özellik ve özellikleri dağıtmak ve kullanmak istediğiniz geliştirme döngüsünün hangi aşamasında olduğunu seçme. Yayın öncesi sürüm ve üretim kanallarını ihtiyaçlarınıza en uygun şekilde bulun.

## <a name="pre-release-channels"></a>Yayın öncesi sürüm kanalları

<br>

****

|Müşteri/Kanal Teklifi|Windows 10|Microsoft 365 Uygulamaları için Enterprise (Windows 10)|
|:-------|:-------|:-----|
|Üst düzeyde teknik kullanıcılar ve geliştiriciler için doğru. <p> Geliştirme döngüsünün en erken sırasında en yeni kodun yer alan en son derlemelere ilk erişenler olmak. <p> Kaba kenarlar ve bazı instability olur.|Geliştirme|Yok|
|Henüz geliştirme aşamasında olan daha güvenilir derlemeler isteyen erken benimseyenler ve IT Profesyonelleri için doğru. <p> Sırada neler olduğunu görebilir ve yeni özellikleri doğrulamaya yardımcı olur.|Beta Kanalı|Beta Kanalı|
|Yaklaşan sürümlere erken erişim isteyenlerin en doğru sürümü. <p> Şirketlerin geniş dağıtım öncesinde gelecek sürümlere önizlemesi ve geçerliliği. <p> Bunlar destekledir.|Sürüm Önizlemesi|Güncel Kanal (Önizleme) <p> Semi-Annual Enterprise Kanalı (Önizleme)|
|

## <a name="production-channels-for-broad-deployment"></a>Geniş dağıtım için üretim kanalları

Örnek kuruluş için dağıtım **aşamaları ve** grupları adım adım görmek için Örnek sütunundaki bağlantıya tıklayın.

<br>

****

|Müşteri/Kanal Teklifi|Windows 10|Microsoft 365 Uygulamaları için Enterprise (Windows 10)|Örnek|
|:-------|:-------|:-----|:-------|
|Hazır olduğunda en son sürümler isteyen müşteriler için doğru.|Semi-Annual Kanalı|[Güncel Kanal](/deployoffice/overview-update-channels#current-channel-overview)|[En son sürümler](deploy-update-channels-examples-rapid-deploy.md)|
|En son sürümü daha öngörülebilirlik ile isteyen kuruluşlar için doğru.|Semi-Annual Kanalı|[Aylık Enterprise Kanalı](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview)||
|Her güncelleştirmeden önce kapsamlı BIR IT testi ihtiyacı olan kuruluşlar için doğru.|Semi-Annual Kanalı|[Yarı Yıllık Enterprise Kanalı](/deployoffice/overview-update-channels#semi-annual-enterprise-channel-overview)||
|

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)