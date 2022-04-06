---
title: Destek sonu yazılım ve yazılım sürümlerini planlama
description: Artık desteklenen ve güvenlik güncelleştirmeleri al almayan yazılım ve yazılım sürümlerini keşfedin ve plan edin.
keywords: Tehdit ve Güvenlik Açığı Yönetimi, Uç Nokta için Microsoft Defender tvm güvenlik önerisi, siber güvenlik önerisi, işlemli güvenlik önerisi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3997e2cb372a2cbbbdb0d8e9b51c5b57bd38c7aa
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476697"
---
# <a name="plan-for-end-of-support-software-and-software-versions-with-threat-and-vulnerability-management"></a>Destek sonu yazılım ve yazılım sürümlerini destek sürümleriyle birlikte Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Yazılım veya yazılım sürümleri için de destek sonu (EOS) olarak bilinen destek sonu (EOS), artık destek almayacakları veya hizmet almayacakları ve güvenlik güncelleştirmeleri almayacakları anlamına gelir. Desteği sona ermiştir ve yazılım veya yazılım sürümlerini kullanırsınız ve bu, kurum açısından güvenlik açıkları, yasal ve finansal risklere karşı açık olur.

Güvenlik ve IT Yöneticilerinin birlikte çalışması ve kuruluşun yazılım envanterinin en iyi sonuç, uyumluluk ve sağlıklı bir ağ ekosistemi için yapılandırılması çok önemlidir. Artık destek sonu ve güncelleştirme sürümlerine ulaşmış olan uygulamaları kaldırma veya değiştirme seçeneklerini incelemeleri gerekir. Destek tarihlerinin sonundan önce bir plan **oluşturmak** ve uygulamak en iyisidir.

> [!NOTE]
> Destek sonu özelliği şu anda yalnızca bu ürünleri Windows sunulmaktadır.

## <a name="find-software-or-software-versions-that-are-no-longer-supported"></a>Artık desteklenen yazılım veya yazılım sürümlerini bulma

1. Seçenekler Tehdit ve Güvenlik Açığı Yönetimi, Güvenlik [**önerileri'ne gidin**](tvm-security-recommendation.md).
2. Filtreler **paneline** gidin ve etiketler bölümüne bakın. EOS etiket seçenekleriden birini veya birden fazlasını seçin. Sonra **Uygula'ya.**

   :::image type="content" source="images/tvm-eos-tag.png" alt-text="EOS yazılımı, EOS sürümleri ve Yaklaşan EOS sürümleri" lightbox="images/tvm-eos-tag.png":::

3. Sona eren destek sona ermiştir, destek sona erer yazılım sürümleri veya yaklaşan destek sonu ile sürümler ile ilgili önerilerin bir listesini burada bulunmaktadır. Bu etiketler yazılım envanteri [sayfasında da](tvm-software-inventory.md) görünür.

   :::image type="content" source="images/tvm-eos-tags-column.png" alt-text="The Öneriler with EOS tag" lightbox="images/tvm-eos-tags-column.png":::

## <a name="list-of-versions-and-dates"></a>Sürümler ve tarihler listesi

Destek sonuna ulaşan ya da kısa süre içinde sona eren ya da desteklenen sürümlerin listesini görüntülemek ve bu tarihleri görmek için aşağıdaki adımları izleyin:

1. Desteğin sonuna ulaşan veya yakın zamanda destek sonuna gelecek sürümlerin yazılım için güvenlik önerisi uç iletisinde bir ileti görüntülenir.

   :::image type="content" source="images/eos-upcoming-eos.png" alt-text="Sürüm dağıtım bağlantısı" lightbox="images/eos-upcoming-eos.png":::

2. Yazılım **detaya** gitme sayfasına gitmek için sürüm dağıtım bağlantısını seçin. Burada, etiketlerin destek sonu veya yaklaşan destek sonu olarak tanımları için filtrelenmiş sürümler listesi görebilirler.

   :::image type="content" source="images/software-drilldown-eos.png" alt-text="Destek yazılımının sonunun ayrıntılarının yer alan yazılım detaya gitme sayfası" lightbox="images/software-drilldown-eos.png":::

3. Tablodaki sürümlerden birini seçerek açın. Örneğin, sürüm 10.0.18362.1. Destek sonunun bitiş tarihiyle birlikte bir çıkış görünür.

   :::image type="content" source="images/version-eos-date.png" alt-text="Destek sonunun tarihi görüntülenir" lightbox="images/version-eos-date.png":::

Destek sonu durumlarından dolayı hangi yazılım ve yazılım sürümlerinin zayıf olduğunu belirleyip belirlemenin ardından, bunları kurumdan güncelleştirme veya kaldırma arasında karar verebilirsiniz. Bunun yapmak, kuruluşlarının güvenlik açıklarına ve gelişmiş kalıcı tehditlere maruz kalmalarını azaltır.

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Yazılım envanteri](tvm-software-inventory.md)
