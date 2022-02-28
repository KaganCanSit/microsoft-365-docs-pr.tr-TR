---
title: Power Automate'i Power Automate
description: Power Automate hakkında bilgi Microsoft 365 Defender bunları kullanma hakkında bilgi.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, secops
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a707de259897080f8e726aed70618ea6505bdea6
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989980"
---
# <a name="use-power-automate-in-microsoft-365-defender"></a>Power Automate'ta Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).
>

Modern güvenlik işlemlerinin (SecOps) ekiplerinin etkin bir şekilde çalışması için otomasyona ihtiyacı olur. SecOps ekipleri, gerçek tehditlere karşı aramalara ve gerçek tehditlere karşı Power Automate için uyarı listesinin öncelerini kaldırmak ve tehdit olmayanları ortadan kaldırmak için bu uyarıları kullanır.  

## <a name="criteria-for-resolving-alerts"></a>Uyarıları çözümleme ölçütleri

- Kullanıcı Ofis dışında iletisi açık

- Kullanıcı yüksek risk olarak etiketlenmiş değil

Her ikisi de doğruysa, SecOps uyarıyı yasal bir seyahat olarak işaretler ve sorunu çözer. Bu uyarı çözümlendikten Microsoft Teams bu alan alanla birlikte bir bildirim postalanmıştır. 

## <a name="connect-power-automate-to-microsoft-cloud-app-security"></a>Bağlan Power Automate'Microsoft Cloud App Security

Otomasyonu oluşturmak için, Power Automate'a (MCAS) bağlanamadan önce bir API Microsoft Cloud App Security belirteci gerekir. 

1. Ekle **Ayarlar** e tıklayın, **Güvenlik uzantıları'yı** seçin ve ARDıNDAN API **belirteçleri** sekmesinde Belirteç **ekle'ye** tıklayın. 

2. Belirtecniz için bir ad girin ve oluştur'a **tıklayın**. Belirteci daha sonra ihtiyacınız olacak şekilde kaydedin.

## <a name="create-an-automated-flow"></a>Otomatik akış oluşturma

Adım adım ayrıntılı işlem için buradaki videoya [bakın](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn). 

Bu videoda ayrıca, power automate to MCAS'a nasıl bağlanın olduğu da açık almaktadır. 

## <a name="related-information"></a>İlgili bilgiler

- [Power Automate ile Microsoft Cloud App Security](/cloud-app-security/flow-integration)

- [Microsoft Power Automate belgeleri](/power-automate)
