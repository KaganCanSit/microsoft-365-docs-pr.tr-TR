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
description: Örnek kuruluşların kanalları kullanarak dağıtma ve güncelleştirme şekli.
ms.openlocfilehash: 4616d424c49a1348d374fa01d705e0483822eb90
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823992"
---
# <a name="deployment-and-update-channel-example-configurations"></a>Dağıtım ve güncelleştirme kanalı örnek yapılandırmaları

Windows 10 ve Microsoft 365 Uygulamaları için hangi güncelleştirme kanallarını kullanacağınızı seçmek, kuruluşunuzun türüne ve yeni özellikleri ve özellikleri dağıtmak ve kullanmak istediğiniz geliştirme döngüsüne bağlı olabilir. Gereksinimlerinize en uygun yayın öncesi ve üretim kanallarını bulun.

## <a name="pre-release-channels"></a>Yayın öncesi kanallar

|Müşteri/Kanal Teklifi|Windows 10|Enterprise için Microsoft 365 Uygulamaları (Windows 10)|
|---|---|---|
|Son derece teknik kullanıcılar ve geliştiriciler için doğru. <br/><br/> Geliştirme döngüsünün en erken bölümlerinde en yeni kodla en son derlemelere ilk erişen olun. <br/><br/> Pürüzlü kenarlar ve biraz dengesizlik olacaktır.|Geliştirme|Yok|
|Henüz geliştirme aşamasında olan daha güvenilir derlemeler isteyen erken benimseyenler ve BT Uzmanları için uygundur. <br/><br/> Sırada neler olacağını görün ve yeni özellikleri doğrulamaya yardımcı olun.|Beta Kanalı|Beta Kanalı|
|Yaklaşan sürümlere erken erişim isteyenler için doğru. <br/><br/> Burada şirketler, geniş dağıtımdan önce gelecek sürümlerin önizlemesini ve doğrulamasını sağlar. <br/><br/> Bunlar desteklenir.|Sürüm Önizlemesi|Geçerli Kanal (Önizleme) <br/><br/> Semi-Annual Enterprise Kanalı (Önizleme)|

## <a name="production-channels-for-broad-deployment"></a>Geniş dağıtım için üretim kanalları

Örnek bir kuruluşun dağıtım aşamalarında ve gruplarında adım adım ilerleyebilmek için **Örnek** sütunundaki bağlantıya tıklayın.

|Müşteri/Kanal Teklifi|Windows 10|Enterprise için Microsoft 365 Uygulamaları (Windows 10)|Örnek|
|---|---|---|---|
|Hazır oldukları anda en son sürümleri isteyen müşteriler için uygundur.|Semi-Annual Kanalı|[Geçerli Kanal](/deployoffice/overview-update-channels#current-channel-overview)|[En son sürümler](deploy-update-channels-examples-rapid-deploy.md)|
|En son sürümün daha öngörülebilir olmasını isteyen kuruluşlar için doğru seçenek.|Semi-Annual Kanalı|[Aylık Enterprise Kanalı](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview)||
|Her güncelleştirmeden önce kapsamlı BT testi ihtiyacı olan kuruluşlar için doğru.|Semi-Annual Kanalı|[Altı Aylık Enterprise Kanalı](/deployoffice/overview-update-channels#semi-annual-enterprise-channel-overview)||

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)