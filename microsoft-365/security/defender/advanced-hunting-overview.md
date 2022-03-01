---
title: Genel Bakış - Gelişmiş av
description: Ağ bağlantılarında gelişmiş Microsoft 365 sorgular ve ağda tehdit ve zayıflığı önceden bulmak için nasıl kullanabileceğiniz hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto
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
ms.openlocfilehash: 03f99f6b883a46e0a7c87d6cbdb2abb8f5552a31
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010868"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>E-Microsoft 365 Defender'de gelişmiş avla tehditlere karşı önceden Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).
>

Gelişmiş av, 30 günlük ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit arama aracıdır. Tehdit göstergelerini ve varlıklarını bulmak için ağ'daki olayları önceden inceebilirsiniz. Verilere esnek erişim, hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış arama sağlar.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Aynı tehdit arama sorgularını kullanarak özel algılama kuralları oluşturabilirsiniz. Bu kurallar ihlal şüphesi olan etkinlikleri, hatalı yapılandırılmış makineleri ve diğer bulguları denetlemek ve sonra bu kurallara yanıt vermek için otomatik olarak çalışır.

Bu özellik, Uç Nokta için [Microsoft Defender'da gelişmiş avlamaya](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) benzer ve daha geniş bir veri kümesinden gelen sorguları destekler:

- Uç Nokta için Microsoft Defender
- Office 365 için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Kimlik için Microsoft Defender

Gelişmiş avı kullanmak için[, arama Microsoft 365 Defender](m365d-enable.md).

Bulut Uygulamaları için Microsoft Defender'da gelişmiş av verileriyle ilgili daha fazla bilgi için [videoya bakın](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Gelişmiş avla çalışmaya başlama

Gelişmiş avlamaya hızlı bir şekilde başlamak için birkaç adımdan başlamayı öneririz.

| Learning hedefi | Açıklama | Kaynak |
|--|--|--|
| **Dili öğrenin** | Gelişmiş av, aynı söz [dizimi ve işleçleri](/azure/kusto/query/) destekleyen Bire bir sorgu diline bağlıdır. İlk sorguyu çalıştırarak sorgu dilini öğrenmeye başlayabilirsiniz. | [Sorgu diline genel bakış](advanced-hunting-query-language.md) |
| **Sorgu sonuçlarını kullanmayı öğrenin** | Grafikler ve sonuçlarınızı görüntülemenin veya dışarı aktarmanın çeşitli yollarını öğrenin. Sorguları hızlı bir şekilde incelemeyi, daha zengin bilgiler elde etmek için detaya gitme ve yanıt eylemlerine yanıt alma hakkında bilgi edinebilirsiniz. | - [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)<br /> - [Sorgu sonuçları üzerinde eylemde bulundur](advanced-hunting-take-action.md) |
| **Şemayı anlama** | Şemadaki tabloları ve bunların sütunlarını daha iyi ve üst düzey bir şekilde anlayabilirsiniz. Sorgularınızı hazırlarken verilerin nerede araması gerektir olduğunu öğrenin. | - [Şema başvurusu](advanced-hunting-schema-tables.md) <br />- [Uç Nokta için Microsoft Defender'dan Geçiş](advanced-hunting-migrate-from-mde.md) |
| **Uzman ipuçları ve örneklerine bakın** | Microsoft uzmanlarından gelen kılavuzlarla ücretsiz eğitim alın. Farklı tehdit arama senaryolarını kapsayan önceden tanımlanmış sorgu koleksiyonlarını keşfedin. | - [Uzman eğitimi al](advanced-hunting-expert-training.md) <br />- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md) <br />- [Hemen iş avına çık](advanced-hunting-go-hunt.md) <br />- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında tehdit avı](advanced-hunting-query-emails-devices.md) |
| **Sorguları en iyi duruma getirme ve hataları işleme** | Verimli ve hatasız sorgular oluşturma hakkında bilgi. | - [Sorgu en iyi yöntemleri](advanced-hunting-best-practices.md)<br />- [Hataları işleme](advanced-hunting-errors.md) |
| **Özel algılama kuralları oluşturma** | Uyarıları tetiklemek ve otomatik olarak yanıt eylemleri yapmak için gelişmiş arama sorgularını nasıl kullanabileceğiniz hakkında bilgi. | - [Özel algılamalara genel bakış](custom-detections-overview.md) <br />- [Özel algılama kuralları](custom-detection-rules.md) |

## <a name="get-access"></a>Erişim elde
Gelişmiş av veya [diğer Microsoft 365 Defender kullanmak](microsoft-365-defender.md) için bu özellik için uygun bir Azure Active Directory. [Gelişmiş av için gerekli roller ve izinler hakkında bilgi okuyun](custom-roles.md).

Ayrıca, uç nokta verilerine erişiminiz, Uç Nokta için Microsoft Defender'daki rol tabanlı erişim denetimi (RBAC) ayarlarıyla belirlenir. [E-postanıza erişimi yönetme Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Veri tazeliği ve güncelleştirme sıklığı
Gelişmiş av verileri, her biri farklı bir birleştirilmiş, iki ayrı tür altında kategorilere ayırabilirsiniz.

- **Olay veya etkinlik verileri**; uyarılar, güvenlik olayları, sistem olayları ve rutin değerlendirmeler ile ilgili tabloları doldurmak için kullanılır. Gelişmiş av, algılayıcıların bunları başarılı bir şekilde ilgili bulut hizmetine iletir ve algılayıcıların hemen hemen ardından bu verileri alır. Örneğin, iş istasyonu veya etki alanı denetleyicilerinde sağlıklı algılayıcılardan gelen olay verilerini, Uç Nokta için Microsoft Defender ve Identity için Microsoft Defender'da sağ yapıldıktan hemen sonra sorguabilirsiniz.
- **Varlık verileri**— tabloları kullanıcılar ve cihazlar hakkında bilgilerle doldurmak için kullanılır. Bu veriler hem görece statik veri kaynaklarından hem de Active Directory girdileri ve olay günlükleri gibi dinamik kaynaklardan gelir. Yeni veriler sağlamak için, tablolar her 15 dakikada bir tüm yeni bilgilerle güncelleştirilir ve tam doldurulmaması gereken satırlar ekler. Her 24 saatte bir, veriler bir bir konuşarak her varlıkla ilgili en son, en kapsamlı veri kümesi içeren bir kayıt ekler.

## <a name="time-zone"></a>Saat dilimi
Gelişmiş avda saat bilgileri UTC saat dilimindedir.

## <a name="related-topics"></a>İlgili konular
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Uzman eğitimi al](advanced-hunting-expert-training.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](custom-detections-overview.md)
