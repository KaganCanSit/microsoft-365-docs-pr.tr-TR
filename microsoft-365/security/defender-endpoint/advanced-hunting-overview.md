---
title: Uç nokta için Microsoft Defender'da gelişmiş ava genel bakış
description: Ağ 365'te tehdit ve zayıflığı olan sorgular oluşturmak üzere Uç Nokta için Microsoft Defender'da tehdit özellikleri kullanın
keywords: gelişmiş av, tehdit avı, siber tehdit avı, mdatp, microsoft defender atp, uç nokta için Microsoft Defender, wdatp, arama, sorgu, telemetri, özel algılamalar, şema, kusto, saat dilimi, UTC
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2e1b6a5bb77dc757861a5d7f56d8a4380c6fc6c1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997602"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>Gelişmiş avla tehditlere karşı önceden arama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Gelişmiş av, 30 günlük ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit arama aracıdır. Tehdit göstergelerini ve varlıklarını bulmak için ağ'daki olayları önceden inceebilirsiniz. Verilere esnek erişim, hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış arama sağlar.

Gelişmiş avlara hızlı bir genel bakış için bu videoyu ve hızlı bir başlangıç yapmaya yardımcı olacak kısa bir öğreticiyi izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

Aynı tehdit arama sorgularını kullanarak özel algılama kuralları oluşturabilirsiniz. Bu kurallar ihlal şüphesi olan etkinlikleri, hatalı yapılandırılmış makineleri ve diğer bulguları denetlemek ve sonra bu kurallara yanıt vermek için otomatik olarak çalışır.

> [!TIP]
> Gelişmiş [av için Microsoft 365 Defender Uç nokta](/microsoft-365/security/defender/advanced-hunting-overview) için Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender'dan gelen verileri kullanarak tehdit avına kullanın. [Aç'Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

Uç nokta için Microsoft Defender'dan gelişmiş av iş akışlarınızı Gelişmiş av sorgularını Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender'e taşıma [hakkında daha fazla bilgi edinmek için.](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde)

## <a name="get-started-with-advanced-hunting"></a>Gelişmiş avla çalışmaya başlama

Gelişmiş av bilginizi yukarıya çıkmak için aşağıdaki adımları izleyin.

Gelişmiş avla hızlı bir şekilde gidip gitmek için birkaç adım atmanizi öneririz.

<br>

****

|Learning hedefi|Açıklama|Kaynak|
|---|---|---|
|**Dili öğrenin**|Gelişmiş av, aynı söz [dizimi ve işleçleri](/azure/kusto/query/) destekleyen Bire bir sorgu diline bağlıdır. İlk sorguyu çalıştırarak sorgu dilini öğrenmeye başlayabilirsiniz.|[Sorgu diline genel bakış](advanced-hunting-query-language.md)|
|**Sorgu sonuçlarını kullanmayı öğrenin**|Grafikler ve sonuçlarınızı görüntülemenin veya dışarı aktarmanın çeşitli yollarını öğrenin. Sorguları hızlı bir şekilde incelemeyi ve daha zengin bilgiler elde etmek için detaya gitme olanağını keşfedin.|[Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)|
|**Şemayı anlama**|Şemadaki tabloları ve bunların sütunlarını daha iyi ve üst düzey bir şekilde anlayabilirsiniz. Sorgularınızı hazırlarken verilerin nerede araması gerektir olduğunu öğrenin.|[Şema başvurusu](advanced-hunting-schema-reference.md)|
|**Önceden tanımlanmış sorguları kullanma**|Farklı tehdit arama senaryolarını kapsayan önceden tanımlanmış sorgu koleksiyonlarını keşfedin.|[Paylaşılan sorgular](advanced-hunting-shared-queries.md)|
|**Sorguları en iyi duruma getirme ve hataları işleme**|Verimli ve hatasız sorgular oluşturma hakkında bilgi.|[Sorgu en iyi yöntemleri](advanced-hunting-best-practices.md) <p> [Hataları işleme](advanced-hunting-errors.md)|
|**En eksiksiz kapsamı elde**|Organizasyonunıza daha iyi veri kapsamı sağlamak için denetim ayarlarını kullanın.|[Gelişmiş arama kapsamı genişletme](advanced-hunting-extend-data.md)|
|**Hızlı bir araştırma çalıştırma**|Şüpheli etkinlikleri araştırmak için hızla gelişmiş bir arama sorgusu çalıştırın.|[Hareket avı ile varlık veya etkinlik bilgilerini *hızla avına çıktılar*](advanced-hunting-go-hunt.md)|
|**Tehdit ve tehditlere karşı koruma**|Dosyaları paylaşarak, uygulama yürütmeyi kısıtlaarak ve diğer eylemlerle saldırılara yanıt verin|[Gelişmiş arama sorgusu sonuçları üzerinde eyleme geç](advanced-hunting-take-action.md)|
|**Özel algılama kuralları oluşturma**|Uyarıları tetiklemek ve otomatik olarak yanıt eylemleri yapmak için gelişmiş arama sorgularını nasıl kullanabileceğiniz hakkında bilgi.|[Özel algılamalara genel bakış](overview-custom-detections.md) <p> [Özel algılama kuralları](custom-detection-rules.md)|
|

## <a name="data-freshness-and-update-frequency"></a>Veri tazeliği ve güncelleştirme sıklığı

Gelişmiş av verileri, her biri farklı bir birleştirilmiş, iki ayrı tür altında kategorilere ayırabilirsiniz.

- **Olay veya etkinlik verileri**: Uyarılar, güvenlik olayları, sistem olayları ve rutin değerlendirmeler ile ilgili tabloları doldurmak için kullanılır. Gelişmiş av, bu verileri toplayan algılayıcıların uç nokta için Defender'a iletmesi hemen ardından alır.
- **Varlık verileri**: Tablolar, kullanıcılar ve cihazlar hakkında birleştirilmiş bilgilerle birlikte kullanılır. Bu veriler hem görece statik veri kaynaklarından hem de Active Directory girdileri ve olay günlükleri gibi dinamik kaynaklardan gelir. Yeni veriler sağlamak için, tablolar her 15 dakikada bir tüm yeni bilgilerle güncelleştirilir ve tam doldurulmaması gereken satırlar ekler. Her 24 saatte bir, veriler bir bir konuşarak her varlıkla ilgili en son, en kapsamlı veri kümesi içeren bir kayıt ekler.

## <a name="time-zone"></a>Saat dilimi

Gelişmiş avda saat bilgileri şu anda UTC saat diliminde.

## <a name="related-topics"></a>İlgili konular

- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Şemayı anlama](advanced-hunting-schema-reference.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](overview-custom-detections.md)
- [Depolama genel bakış](/azure/storage/common/storage-account-overview)
- [Azure Etkinlik Hub'ları — Büyük bir veri akışı platformu ve etkinlik alımı hizmeti](/azure/event-hubs/event-hubs-about)
