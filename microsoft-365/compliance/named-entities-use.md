---
title: DLP ilkelerinde adlandırılmış varlıkları kullanma
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
ms.openlocfilehash: 108b21e7c5a6708a01a712dcd44788f489df0e73
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971593"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>Veri kaybı önleme ilkelerinizde adlandırılmış varlıkları kullanma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kullanmaya başlamadan önce [Adlandırılmış varlıklar hakkında bilgi edinin](named-entities-learn.md) bölümüne bakın.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

Tam lisanslama ayrıntıları için [hizmet açıklamasına](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer) bakın.

### <a name="permissions"></a>İzinler

Veri kaybı önleme (DLP) ilkelerini oluşturmak ve düzenlemek için kullandığınız hesabın **DLP Uyumluluk Yönetimi** rol izinlerine sahip olması gerekir. Daha fazla bilgi için bkz[. Kullanıcılara Office 365 Uyumluluk Merkezi'ne erişim verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Desteklenen konumlar

Bu konumlardaki hassas öğeleri algılamak ve korumak için adlandırılmış varlık SID'lerini ve gelişmiş ilkeleri kullanabilirsiniz:

- siteleri SharePoint
- hesapları OneDrive
- Sohbet ve kanal iletilerini Teams
- Cihazlar (Windows 10 ve 11 uç nokta cihazı)
- posta kutularını Exchange

Adlandırılmış varlık SID'leri ve gelişmiş ilkeler şunlar için desteklenmez:

- Şirket içi depolar
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Gelişmiş ilkeler oluşturma ve düzenleme

DLP ilkesi oluşturmak veya düzenlemek için [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md) içindeki yordamları kullanın.

## <a name="workloads-and-services-that-support-named-entities"></a>Adlandırılmış varlıkları destekleyen iş yükleri ve hizmetler

- **Microsoft 365 eBulma**, Substrate hizmetlerinde adlandırılmış varlıkların kullanımını destekler.
- **Microsoft Defender for Cloud Apps**, Bulut için Defender uygulamaları portalındaki Bulut için Defender Uygulamaları ilkelerinde adlandırılmış varlıkların kullanımını destekler.
- **Insider Risk Management** , Substrate hizmetlerinde adlandırılmış varlıkların kullanımını destekler.
- **Kayıt Yönetimi** , adlandırılmış varlıkların kullanımını destekler.
- **Hassas Bilgi Türleriyle Tam Veri Eşleşmesi** , adlandırılmış varlıkların kullanımını destekler.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Birleşik DLP

|İş Yükü/Hizmetler  |Adlandırılmış Varlıklar için Destek  |
|---------|---------|
|win32 istemcileri ilke ipucunu Office    |Desteklenmiyor  |
|WAC istemcileri ilke ipucunu Office    |Destekleniyor         |
|OWA ilke ipucu     |Desteklenmiyor         |
|İlke ipucu Outlook     |Desteklenmiyor |
|Uç noktalar (Windows 10 ve 11 cihaz)     |Destekleniyor  |
|Exchange Taşıma kuralları     |Destekleniyor |
|Bekleyen verileri OneDrive İş     |Destekleniyor         |
|bekleyen çevrimiçi verileri SharePoint     |Destekleniyor         |
|Bekleyen verileri Teams     |Destekleniyor         |
|Bekleyen e-posta iletileri verileri     |Gizlilik Hizmeti Planı ile kiracılar için desteklenir         |
|Bulut Uygulamaları için Microsoft Defender     |Desteklenen         |

### <a name="autolabeling"></a>Otomatik etiketleme

|İş Yükü/Hizmetler |Adlandırılmış Varlıklar için Destek  |
|---------|---------|
|Win32 istemcilerini çevrimdışı Office   |Desteklenir, kullanıcı etiketi seçip el ile uygulamalıdır |
|Çevrimiçi Office Win32 istemcileri çevrimiçi|Eski güvenilirlik şemasıyla desteklenir |
|çevrimiçi Outlook   |Eski güvenilirlik şemasıyla desteklenir  |
|WAC istemci Office     |Destekleniyor |
|OWA     |Destekleniyor |
|Exchange taşıma     |Destekleniyor |
|Bekleyen verileri OneDrive İş     |Destekleniyor |
|bekleyen çevrimiçi verileri SharePoint|Destekleniyor|
|Azure Information Protection (AIP) tarayıcısı|desteklenmiyor|

## <a name="known-issues"></a>Bilinen sorunlar

|Sorun  |Etki  |
|---------|---------|
|DLP İlkesi ipuçları (OWA, Outlook Office Win32 istemcileri)     |   Varlık koşuluna sahip ilke ipuçları "eşleşme yok" ile sonuçlanır      |
| Kişi adı için Asya dili desteği (Çince, Japonca, Korece)    | Kişi adı için yalnızca Latin tabanlı karakter kümesi için desteklenen adlandırılmış varlıklar (yani kanji desteklenmez)        |
|Şirket içi depolar    | İş yükü olarak desteklenmez|
|Power BI (önizleme) | Desteklenmiyor

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="best-practices-for-using-named-entity-sits"></a>Adlandırılmış varlık SID'lerini kullanmak için en iyi yöntemler

Adlandırılmış varlık SIT kullanan bir ilke oluştururken veya düzenlerken kullanabileceğiniz bazı uygulamalar aşağıda verilmiştir.

- Elektronik tablodaki verileri ararken düşük örnek sayılarını (üç-beş) kullanın ve bu veriler için SIT'in gerektirdiği anahtar sözcük yalnızca sütun üst bilgisindedir. Örneğin, ABD Sosyal Güvenlik numaralarını aradığınızı ve anahtar sözcüğün `Social Security Number` yalnızca sütun başlığında olduğunu varsayalım. Değerler (doğrulayıcı kanıt) aşağıdaki hücrelerde olduğundan, yalnızca ilk birkaç örneğin algılanacak anahtar sözcükle yeterince yakın olması olasıdır.  

- ABD Sosyal Güvenlik numaralarını bulmanıza yardımcı olması için Tüm Tam Adlar gibi adlandırılmış bir SIT varlığı kullanıyorsanız, 10 veya 50 gibi daha büyük örnek sayılarını kullanın. Ardından hem kişi adları hem de SSN'ler birlikte algılandığında gerçek pozitifler elde etme olasılığınız artar.

- Adlandırılmış varlık SID'lerinin doğruluğunu test etmek için [Otomatik etiketleme simülasyonlarını](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) kullanabilirsiniz. İlkeyle eşleşen öğeleri görmek için adlandırılmış varlık SIT kullanarak bir simülasyon çalıştırın. Bu bilgilerle, özel ilkelerinizdeki veya gelişmiş şablon koşullarındaki örnek sayılarını ve güvenilirlik düzeylerini ayarlayarak doğruluğu ayarlayabilirsiniz. Üretimde adlandırılmış varlıkları içeren bir DLP veya otomatik etiketleme ilkesi dağıtmadan önce simülasyonları doğruluk istediğiniz yere gelene kadar yineleyebilirsiniz. Akışa genel bir bakış aşağıdadır:

1. Simülasyon modunda test etmek istediğiniz SIT veya SIP'ler bileşimini (özel veya kopyalanmış ve düzenlenmiş) tanımlayın.
1. Otomatik etiketleme ilkesi Exchange, SharePoint sitelerde veya OneDrive hesaplarında eşleşme bulduğunda uygulanacak bir duyarlılık etiketi belirleyin veya oluşturun.
1. 1. adımdaki SIT'i kullanan ve DLP ilkenizde kullanılacak Koşullar ve Özel Durumlar ile duyarlılık otomatik etiketleme ilkesi oluşturma
1. İlke benzetimi çalıştırma
1. Sonuçları görüntüleme
1. Hatalı pozitif sonuçları azaltmak için SIT veya ilke ile örnek sayısı ve güvenilirlik düzeylerini ayarlayın.
1. İstediğiniz doğruluk sonuçlarını elde edene kadar tekrarlayın.


## <a name="for-further-information"></a>Daha fazla bilgi için
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Adlandırılmış varlıklar hakkında bilgi edinin](named-entities-learn.md).
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
