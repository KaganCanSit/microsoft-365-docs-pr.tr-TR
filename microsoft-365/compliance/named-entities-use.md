---
title: Veri kaybı önleme ilkelerinizde adlandırılmış varlıkları kullanma (önizleme)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Veri kaybı önleme ilkelerinizdeki adlandırılmış varlıklardan yararlanmak için bu yordamları kullanın
ms.openlocfilehash: 9b3a8899ef4b64c682289e29df19648a00d4f048
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665172"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Veri kaybı önleme ilkelerinizde adlandırılmış varlıkları kullanma (önizleme)

> [!IMPORTANT]
> Adlandırılmış varlıklar özelliği kullanıma sunuluyor ve kiracınız kullanılabilir olduğunda kiracınızda görünür. Bunları içerik gezgininde ve veri kaybı önleme (DLP) ilkesi yazma akışında denetleyin. 

Kullanmaya başlamadan önce [Adlandırılmış varlıklar hakkında bilgi edinin (önizleme)](named-entities-learn.md) bölümüne bakın.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

Bu aboneliklerden birine sahip olmanız gerekir

- Information Protection ve İdare
- Microsoft 365 E5 Uyumluluk
- Office 365 E5
- Microsoft 365 E5

Tam lisanslama ayrıntıları için [hizmet açıklamasına](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer) bakın.

### <a name="permissions"></a>İzinler

Veri kaybı önleme (DLP) ilkelerini oluşturmak ve düzenlemek için kullandığınız hesabın **DLP Uyumluluk Yönetimi** rol izinlerine sahip olması gerekir. Daha fazla bilgi için bkz[. Kullanıcılara Office 365 Uyumluluk Merkezi'ne erişim verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Desteklenen konumlar

Bu konumlardaki hassas öğeleri algılamak ve korumak için adlandırılmış varlık SID'lerini ve gelişmiş ilkeleri kullanabilirsiniz:

- siteleri SharePoint
- hesapları OneDrive
- Sohbet ve kanal iletilerini Teams
- Cihazlar (Windows 10 uç nokta cihazları)

Adlandırılmış varlık SID'leri ve gelişmiş ilkeler şunlar için desteklenmez:


- Şirket içi depolar
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Gelişmiş ilkeler oluşturma ve düzenleme

DLP ilkesi oluşturmak veya düzenlemek için [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md) içindeki yordamları kullanın.

## <a name="workloads-and-services-that-support-named-entities"></a>Adlandırılmış varlıkları destekleyen iş yükleri ve hizmetler


- **Microsoft 3655 eBulma** , Substrate hizmetlerinde adlandırılmış varlıkların kullanımını destekler.
- **Microsoft Defender for Cloud Apps**, Bulut için Defender Uygulamaları ilkelerinde adlandırılmış varlıkların kullanımını destekler.
- **Insider Risk Management** , Substrate hizmetlerinde adlandırılmış varlıkların kullanımını destekler.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Birleşik DLP

|İş Yükü/Hizmetler  |Adlandırılmış Varlıklar için Genel Önizleme Desteği  |
|---------|---------|
|win32 istemcileri ilke ipucunu Office    |desteklenmiyor  |
|WAC istemcileri ilke ipucunu Office    |Desteklenen         |
|OWA ilke ipucu     |desteklenmiyor         |
|İlke ipucu Outlook     |desteklenmiyor |
|Uç noktalar (Windows 10 cihazlar)     |Desteklenen  |
|Exchange Taşıma kuralları     |desteklenmiyor |
|Bekleyen verileri OneDrive İş     |Desteklenen         |
|bekleyen çevrimiçi verileri SharePoint     |Desteklenen         |
|Bekleyen verileri Teams     |Desteklenen         |
|Bekleyen e-posta iletileri verileri     |desteklenmiyor         |
|Bulut Uygulamaları için Microsoft Defender     |Desteklenen         |

### <a name="autolabeling"></a>Otomatik etiketleme

|İş Yükü/Hizmetler |Adlandırılmış Varlıklar için Genel Önizleme Desteği  |
|---------|---------|
|Win32 istemcilerini çevrimdışı Office   |destekleniyorsa, kullanıcı etiketi seçip el ile uygulamalıdır |
|Çevrimiçi Office Win32 istemcileri çevrimiçi|eski güvenilirlik şemasıyla desteklenir |
|çevrimiçi Outlook   |eski güvenilirlik şemasıyla desteklenir  |
|WAC istemci Office     |Desteklenen |
|OWA     |Desteklenen |
|Exchange taşıma     |desteklenmiyor |
|Bekleyen verileri OneDrive İş     |Desteklenen |
|bekleyen çevrimiçi verileri SharePoint|Desteklenen|
|Azure Information Protection (AIP) tarayıcısı|desteklenmiyor|

## <a name="known-issues"></a>Bilinen sorunlar

|Sorun  |Etki  |
|---------|---------|
|DLP İlkesi ipuçları (OWA, Outlook Office Win32 istemcileri)     |   Varlık koşuluna sahip ilke ipuçları "eşleşme yok" ile sonuçlanır      |
| Kişi adı için Asya dili desteği (Çince, Japonca, Korece)    | Kişi adı için yalnızca Latin tabanlı karakter kümesi için desteklenen adlandırılmış varlıklar (yani kanji desteklenmez)        |
|Şirket içi depolar    | İş yükü olarak desteklenmez|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Daha fazla bilgi için
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Adlandırılmış varlıklar (önizleme) hakkında bilgi edinin](named-entities-learn.md).
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
