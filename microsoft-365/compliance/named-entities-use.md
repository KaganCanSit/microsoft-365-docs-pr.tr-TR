---
title: Veri kaybı önleme ilkelerinize adlandırılmış varlıkları kullanma (önizleme)
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
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Veri kaybı önleme ilkelerinize adlandırılmış varlıklardan yararlanmak için bu yordamları kullanın
ms.openlocfilehash: f3dac4efa1b0cf84971ac4d07f78144b438d1161
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010041"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Veri kaybı önleme ilkelerinize adlandırılmış varlıkları kullanma (önizleme)

> [!IMPORTANT]
> Adlandırılmış varlıklar özelliği sunulmaktadır ve sizin için kullanılabilir olduğunda kiracıda görünür. İçerik gezgininde ve veri kaybı önleme (DLP) ilkesi yazma akışında bunları kontrol edin. 

Kullanmaya başlamadan [önce adlandırılmış varlıklar (önizleme)](named-entities-learn.md) hakkında bilgi edinmek için bu makaleyi okuyun.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Bu aboneliklerden birini

- Bilgi Koruması ve Yönetimi
- Microsoft 365 E5 Uyumluluk
- Office 365 E5
- Microsoft 365 E5

Tam lisans ayrıntıları için, hizmet [açıklamasına bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>İzinler

Veri kaybı önleme (DLP) ilkelerini oluşturmak ve düzenlemek için kullanıyorsanız, **DLP Uyumluluk Yönetimi rol izinlerine sahip** olmalıdır. Daha fazla bilgi için bkz[. Kullanıcılara Uyumluluk Merkezi'Office 365 erişme izni verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Desteklenen konumlar

Şu konumlarda önemli öğeleri algılamak ve korumak için adlandırılmış varlık SITS'leri ve gelişmiş ilkeleri kullanabilirsiniz:

- SharePoint siteleri
- OneDrive hesapları
- Teams ve kanal iletilerini gönderme
- Cihazlar (Windows 10 uç nokta cihazları)

Adlandırılmış varlık SITS'leri ve gelişmiş ilkeler şular için destek desteklemez:


- Şirket içi depolar
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Gelişmiş ilkeleri oluşturma ve düzenleme

DLP ilkesi oluşturmak veya düzenlemek için, [DLP ilkesi oluşturma, sınama ve ayarlama'daki yordamları kullanın](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Adlandırılmış varlıkları destekleyen iş yükleri ve hizmetler


- **Microsoft 3655 eKbulma** , Altstrate hizmetlerde adlandırılmış varlıkların kullanımını destekler.
- **Bulut Uygulamaları için Microsoft Defender** , Bulut Uygulamaları için Defender ilkelerde adlandırılmış varlıkların kullanımını destekler.
- **Insider Risk Yönetimi** , Alt Kuruluş hizmetlerde adlandırılmış varlıkların kullanımını destekler.
- **İletişim Uyumluluğu**, diğer kuruluşta adlandırılmış varlıkların aktarım Exchange kalan verilerin kullanımını desteklemez.
- **Microsoft Bilgi Yönetimi** (MIG), diğer bir çok aktarım kuralında ve veri yerinde çalışma Exchange adlandırılmış varlıkların kullanımını desteklemez.
 
### <a name="unified-dlp"></a>Birleşik DLP

|workload/services  |Adlandırılmış Varlıklar için Genel Önizleme Desteği  |
|---------|---------|
|Office Win32 istemcileri ilke ipucu    |desteklenmiyor  |
|Office WAC istemcileri ilke ipucu    |destek         |
|OWA ilke ipucu     |desteklenmiyor         |
|Outlook ilkesi ipucu     |desteklenmiyor |
|Uç noktalar (Windows 10 cihazlar)     |destek  |
|Exchange Aktarım kuralları     |desteklenmiyor |
|OneDrive İş kalan verileri geri toplama     |destek         |
|SharePoint Online'da veriler geri alın     |destek         |
|Teams kalan verileri geri toplama     |destek         |
|E-posta iletileri için geri kalan veriler     |desteklenmiyor         |
|Bulut Uygulamaları için Microsoft Defender     |destek         |

### <a name="autolabeling"></a>Otomatik etiket

|workload/services |Adlandırılmış Varlıklar için Genel Önizleme Desteği  |
|---------|---------|
|Office Win32 istemcilerini çevrimdışı olarak geri getirme   |desteklenmişsa kullanıcının etiket seçmesi ve el ile başvurması gerekir |
|Çevrimiçi Office Win32 istemcileri|Eski güven düzeni ile desteklenen |
|Outlook çevrimiçi   |Eski güven düzeni ile desteklenen  |
|Office WAC istemcisi     |destek |
|OWA     |destek |
|Exchange aktarım     |desteklenmiyor |
|OneDrive İş kalan verileri geri toplama     |destek |
|SharePoint Online'da veriler geri alın|destek|
|Azure Information Protection (AIP) tarayıcı|desteklenmiyor|

## <a name="known-issues"></a>Bilinen sorunlar

|Sorun  |Etki  |
|---------|---------|
|DLP İlkesi ipuçları (OWA, Outlook, Office Win32 istemcileri)     |   Varlık koşuluyla ilgili ilke ipuçları "eşleşme yok" sonucu      |
| Kişi adı için Asya dili desteği (Çince, Japonca, Korece)    | Kişi adı için yalnızca Latin tabanlı karakter kümesinde desteklenen adlandırılmış varlıklar (başka bir ifadeyle kanji desteklenmiyor)        |
|Şirket içi depolar    | İş yükü olarak desteklenmiyor|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Daha fazla bilgi için
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Adlandırılmış varlıklar (önizleme) hakkında bilgi öğrenin](named-entities-learn.md).
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
