---
title: Genel Bakış - Gelişmiş avcılık
description: Microsoft 365'daki gelişmiş tehdit avcılığı sorguları ve ağınızdaki tehditleri ve zayıf noktaları proaktif olarak bulmak için bunları nasıl kullanacağınızı öğrenin
keywords: gelişmiş avcılık, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 1ee8d8fbd3b1a56f83106ffaf6be937fa984c272
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731449"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Microsoft 365 Defender'da gelişmiş arama ile tehditleri proaktif olarak avlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş avcılık, 30 güne kadar ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit avcılığı aracıdır. Tehdit göstergelerini ve varlıkları bulmak için ağınızdaki olayları proaktif olarak inceleyebilirsiniz. Verilere esnek erişim, hem bilinen hem de olası tehditler için kısıtlanmamış avcılık sağlar.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Özel algılama kuralları oluşturmak için aynı tehdit avcılığı sorgularını kullanabilirsiniz. Bu kurallar, şüpheli ihlal etkinliğini, yanlış yapılandırılmış makineleri ve diğer bulguları denetlemek ve yanıtlamak için otomatik olarak çalıştırılır.

Bu özellik[, Uç Nokta için Microsoft Defender'daki gelişmiş avcılık](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) özelliklerine benzer ve aşağıdakilerden daha geniş bir veri kümesini denetleyebilen sorguları destekler:

- Uç Nokta için Microsoft Defender
- Office 365 için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Kimlik için Microsoft Defender

Gelişmiş avcılığı kullanmak için [Microsoft 365 Defender açın](m365d-enable.md).

Microsoft Defender for Cloud Apps verilerde gelişmiş avlanma hakkında daha fazla bilgi için [videoya](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa) bakın. 

## <a name="get-started-with-advanced-hunting"></a>Gelişmiş avcılık ile Kullanmaya başlayın

Gelişmiş avlanmaya hızlı bir şekilde başlamak için birkaç adımdan geçmenizi öneririz.

| Learning hedefi | Açıklama | Kaynak |
|--|--|--|
| **Dili öğrenme** | Gelişmiş avcılık, aynı söz dizimini ve işleçleri destekleyen [Kusto sorgu dilini](/azure/kusto/query/) temel alır. İlk sorgunuzu çalıştırarak sorgu dilini öğrenmeye başlayın. | [Sorgu diline genel bakış](advanced-hunting-query-language.md) |
| **Sorgu sonuçlarını kullanmayı öğrenin** | Grafikler ve sonuçlarınızı görüntülemek veya dışarı aktarmak için kullanabileceğiniz çeşitli yollar hakkında bilgi edinin. Sorguları hızlı bir şekilde ayarlamayı, daha zengin bilgi almak için detaya gitmeyi ve yanıt eylemleri gerçekleştirmeyi keşfedin. | - [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)<br /> - [Sorgu sonuçlarında eylem gerçekleştirme](advanced-hunting-take-action.md) |
| **Şemayı anlayın** | Şemadaki tablolar ve sütunları hakkında iyi ve üst düzey bir anlayış elde edin. Sorgularınızı oluştururken verileri nerede arayacağınızı öğrenin. | - [Şema başvurusu](advanced-hunting-schema-tables.md) <br />- [Uç Nokta için Microsoft Defender geçiş](advanced-hunting-migrate-from-mde.md) |
| **Uzman ipuçları ve örnekler alın** | Microsoft uzmanlarının kılavuzlarıyla ücretsiz olarak eğitin. Farklı tehdit avcılığı senaryolarını kapsayan önceden tanımlanmış sorgu koleksiyonlarını keşfedin. | - [Uzman eğitimi alma](advanced-hunting-expert-training.md) <br />- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md) <br />- [Git avla](advanced-hunting-go-hunt.md) <br />- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında tehditleri avlama](advanced-hunting-query-emails-devices.md) |
| **Sorguları iyileştirme ve hataları işleme** | Verimli ve hatasız sorgular oluşturmayı öğrenin. | - [En iyi sorgu yöntemleri](advanced-hunting-best-practices.md)<br />- [Hataları işleme](advanced-hunting-errors.md) |
| **Özel algılama kuralları oluşturma** | Uyarıları tetikleme ve yanıt eylemlerini otomatik olarak gerçekleştirme amacıyla gelişmiş tehdit avcılığı sorgularını nasıl kullanabileceğinizi anlayın. | - [Özel algılamalara genel bakış](custom-detections-overview.md) <br />- [Özel algılama kuralları](custom-detection-rules.md) |

## <a name="get-access"></a>Erişim alma
Gelişmiş avcılık veya diğer [Microsoft 365 Defender](microsoft-365-defender.md) özelliklerini kullanmak için Azure Active Directory uygun bir role sahip olmanız gerekir. [Gelişmiş avcılık için gerekli roller ve izinler hakkında bilgi edinin](custom-roles.md).

Ayrıca, uç nokta verilerine erişiminiz Uç Nokta için Microsoft Defender rol tabanlı erişim denetimi (RBAC) ayarları tarafından belirlenir. [Microsoft 365 Defender erişimini yönetme hakkında bilgi edinin](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Veri güncelliği ve güncelleştirme sıklığı
Gelişmiş tehdit avcılığı verileri, her biri farklı şekilde birleştirilmiş iki ayrı türe kategorilere ayırılabilir.

- **Olay veya etkinlik verileri**; uyarılar, güvenlik olayları, sistem olayları ve rutin değerlendirmeler hakkındaki tabloları doldurur. Gelişmiş avcılık, bu verileri toplayan algılayıcılar tarafından ilgili bulut hizmetlerine başarıyla iletildikten hemen sonra alır. Örneğin, iş istasyonlarındaki veya etki alanı denetleyicilerindeki iyi durumdaki algılayıcılardan gelen olay verilerini, Uç Nokta için Microsoft Defender ve Kimlik için Microsoft Defender kullanıma sunulduktan hemen sonra sorgulayabilirsiniz.
- **Varlık verileri**; tabloları kullanıcılar ve cihazlar hakkındaki bilgilerle doldurur. Bu veriler hem görece statik veri kaynaklarından hem de Active Directory girişleri ve olay günlükleri gibi dinamik kaynaklardan gelir. Yeni veriler sağlamak için, tablolar her 15 dakikada bir yeni bilgilerle güncelleştirilir ve tam olarak doldurulmayabilecek satırlar eklenir. Her 24 saatte bir veriler birleştirerek her varlıkla ilgili en son ve en kapsamlı veri kümesini içeren bir kayıt eklenir.

## <a name="time-zone"></a>Saat dilimi
Gelişmiş avcılıkta saat bilgileri UTC saat dilimindedir.

## <a name="related-topics"></a>İlgili konular
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Uzman eğitimi alın](advanced-hunting-expert-training.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](custom-detections-overview.md)
