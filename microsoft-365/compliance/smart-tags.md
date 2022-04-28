---
title: eBulma'da akıllı etiketleri ayarlama (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ROBOTS: NOINDEX, NOFOLLOW
description: Akıllı etiketler, eBulma (Premium) durumundaki içeriği gözden geçirirken makine öğrenmesi özelliklerini uygulamanızı sağlar. Avukat-istemci ayrıcalık modeli gibi makine öğrenmesi algılama modellerinin sonuçlarını görüntülemek için akıllı etiket gruplarını kullanın.
ms.openlocfilehash: e9b791d632ea6a1a84472ac5ad00b4a45fea294d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095520"
---
# <a name="set-up-smart-tags-in-ediscovery-premium"></a>eBulma'da akıllı etiketleri ayarlama (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif (Premium) içindeki makine öğrenmesi (ML) özellikleri, inceleme kümesindeki servis talebi belgelerini gözden geçirirken karar sürecini daha verimli hale getirmenize yardımcı olabilir. Akıllı etiketler, ML özelliklerini kararların kaydedildiği yere getirmenin bir yoludur: gözden geçirme sırasında belgeler etiketlenirken. Akıllı etiket grubu oluşturduğunuzda, akıllı etiket grubuyla ilişkilendirdiğiniz ML modelinin sonucu olan kararlar etiket grubundaki etiketlerle aynı hizada görüntülenir. Bu, belirli belgeleri gözden geçirirken ML sonuç bilgilerini satır içinde görmenize yardımcı olur.

## <a name="how-to-set-up-a-smart-tag-group"></a>Akıllı etiket grubu ayarlama

1. Gözden geçirme kümesinde **Gözden geçirme kümesini yönet'e** ve ardından **Etiketleri yönet'e** tıklayın.

2. **Etiket grubu ekle'ye** tıklayın ve **akıllı etiket grubu ekle'yi** seçin.

3. Etiket grubuyla ilişkilendirmek istediğiniz ML modelini seçin.
    
   Bu, bir etiket grubu ve *N* alt etiketleri oluşturur; burada *N* , modelin olası çıkışlarının sayısıdır. Örneğin [, avukat-istemci ayrıcalık algılama modelinin](attorney-privilege-detection.md) iki olası çıkışı vardır: 

   - **Pozitif** : Avukat-müşteri ayrıcalıklı içeriği içeren belgeleri etiketlemek için kullanın.
   
   - **Negatif** : Avukat-müşteri ayrıcalıklı içeriği içermeyen belgeleri etiketlemek için kullanın.
    
    Bu modeli seçerseniz, gözden geçirme kümesi için iki alt etiketli bir etiket grubu (biri **Pozitif** , diğeri **Negatif** adlı) oluşturulur. Bu örnekte, her alt etiket, avukat-istemci ayrıcalık algılama modelindeki olası çıkışlardan birine karşılık gelir.

4. İsteğe bağlı olarak, etiket grubunu ve alt etiketleri yeniden adlandırabilirsiniz. Örneğin, **Positive** etiketini **Privileged** olarak, **Negative** etiketini ise **Ayrıcalıklı değil** olarak yeniden adlandırabilirsiniz.

## <a name="how-to-use-smart-tags"></a>Akıllı etiketleri kullanma

Belge gözden geçirilirken modelin sonuçları uygun alt etiketin yanında görüntülenir. Örneğin, avukat-istemci ayrıcalık algılama için bir akıllı etiket grubunuz varsa ve potansiyel olarak ayrıcalıklı bir belgeyi gözden geçirirseniz, bu sonucun nedeni uygun etiketin yanında görüntülenir. Etiketin belgeye otomatik olarak uygulanmadığını unutmayın. Gözden geçiren, belgeyi etiketleme konusunda karar verir.
