---
title: Düzeltme eylemleri Microsoft 365 Defender
description: Yeni ekiplerde otomatik soruşturmaları takip etmek için düzeltme eylemlerine genel Microsoft 365 Defender
keywords: otomatik, araştırma, uyarı, tetikleyici, eylem, düzeltme
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
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: c922213a262fdc9c61d6f79d0205e6ead96fd44a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326439"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Düzeltme eylemleri Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

E-postada otomatik bir Microsoft 365 Defender sırasında ve sonrasında, kötü amaçlı veya şüpheli öğelere yönelik düzeltme eylemleri tanımlanır. Bazı düzeltme eylemleri cihazlara uygulanır ve bu işlem uç nokta olarak da adlandırılır. E-posta içeriği üzerinde diğer düzeltme eylemleri  alınır. Düzeltme eylemleri gerçekleştirdikten, onaylandıktan veya reddedildikten sonra otomatik soruşturmalar tamamlanır.

> [!IMPORTANT]
> Düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi alınıp alınmayacak, otomasyon düzeylerinin nasıl olduğu gibi bazı ayarlara bağlıdır. Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:
> - [Ekip içinde otomatik araştırma ve yanıt yeteneklerinizi Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Cihazlara yönelik tehdit nasıl düzeltildi](../defender-endpoint/automated-investigations.md)
> - [E-posta üzerinde tehdit ve düzeltme eylemleri & işbirliği içeriğine yöneliktir](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Aşağıdaki tabloda, çalışma sayfalarında şu anda desteklenen düzeltme eylemleri Microsoft 365 Defender. 

|Cihaz (uç nokta) düzeltme eylemleri  |E-posta düzeltme eylemleri  |
|:---------|:---------|
|- Soruşturma paketini topla <br/>- Cihazı yalıt (bu işlem geri alın alabilir)<br/>- Offboard makinesi <br/>- Sürüm kodu yürütme <br/>- Karantinadan çıkar <br/>- örnek istek <br/>- Kod yürütmeyi kısıtla (bu eylem geri alınabilir) <br/>- Virüsten koruma taraması çalıştırma <br/>- Durdurma ve karantina      |- URL'yi engelle (tıklama zamanı)<br/>- E-posta iletilerini veya kümelerini yumuşak silme<br/>- E-postayı karantinaya alın<br/>- E-posta eklerini karantinaya alın<br/>- Dış posta iletmeyi kapatma          |

Beklemede veya zaten tamamlandıktan sonra düzeltme eylemleri İşlem merkezinde [22/2002'de 20223'te 2013'te 265 gün 25 gün 25 gün 25 gün 25 gün 25 gün olarak 2](m365d-action-center.md)

## <a name="remediation-actions-that-follow-automated-investigations"></a>Otomatik soruşturmaları takip etmek için düzeltme eylemleri

Otomatik bir araştırma tamamlandığında, dahil olan her kanıt için bir karara varıldı. Karara bağlı olarak düzeltme eylemleri tanımlanır. Bazı durumlarda düzeltme eylemleri otomatik olarak yapılır; başka durumlarda da düzeltme eylemleri onay bekliyor olabilir. Tüm bunlar, otomatik [araştırmanın ve yanıtın nasıl yapılandırıldığına bağlıdır](m365d-configure-auto-investigation-response.md).

Aşağıdaki tabloda olası karar ve sonuçlar listelemektedir:

| Karar    | Etkilenen varlıklar    | Sonuçlar|
|------|------|------|
| Kötü Amaçlı    | Cihazlar (uç noktalar)    | Düzeltme eylemleri otomatik olarak alınır (kuruluş cihaz gruplarının Tam olarak ayar olduğu [](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) varsayılarak **tehditleri otomatik olarak düzeltin**)|
| Kötü Amaçlı    | E-posta içeriği (URL'ler veya ekler) | Önerilen düzeltme eylemleri onay bekliyor|
| Şüpheli    | Cihazlar veya e-posta içeriği | Önerilen düzeltme eylemleri onay bekliyor|
| Tehdit bulunamadı    | Cihazlar veya e-posta içeriği    | Düzeltme eylemi gerekmez|


## <a name="remediation-actions-that-are-taken-manually"></a>El ile yapılan düzeltme eylemleri

Otomatik soruşturmaları takip etmeye yönelik düzeltme eylemlerine ek olarak, güvenlik işlemleri ekibinin bazı düzeltme işlemlerini el ile de gerçekleştirebilir. Bunlar şunlardır:

- Cihaz yalıtlığı veya dosya karantinası gibi el ile cihaz eylemi
- El ile e-posta eylemi, örneğin e-posta iletilerini geçici silme 
- [Cihazlarda veya e-postada](../defender-endpoint/advanced-hunting-overview.md) gelişmiş av eylemi
- [E-postayı](../office-365-security/threat-explorer.md) gereksiz e-postaya taşıma, geçici silme veya e-postayı zor silme gibi e-posta içeriği üzerinde Gezgin eylemi
- Dosyayı [silme](/windows/security/threat-protection/microsoft-defender-atp/live-response) , işlemi durdurma ve zamanlanmış görevi kaldırma gibi el ile canlı yanıt eylemi
- Bir cihazı yalıtma, virüsten koruma taraması çalıştırma ve dosya hakkında bilgi alma gibi Uç Nokta API'leri için [Microsoft Defender](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) ile canlı yanıt eylemi

## <a name="next-steps"></a>Sonraki adımlar

- [İşlem merkezini ziyaret edin](m365d-action-center.md)
- [Düzeltme eylemlerini görüntüleme ve yönetme](m365d-autoir-actions.md)
- [Hatalı pozitif veya yanlış negatifleri ele](m365d-autoir-report-false-positives-negatives.md)
