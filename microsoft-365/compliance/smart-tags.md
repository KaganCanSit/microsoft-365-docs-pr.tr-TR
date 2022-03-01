---
title: Smart Tags'i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Akıllı etiketler, bir olayda içeriği gözden geçirerek makine öğrenme özelliklerini Advanced eDiscovery sağlar. Avukat-istemci ayrıcalık modeli gibi makine öğrenme algılama modellerinin sonuçlarını görüntülemek için akıllı etiket gruplarını kullanın.
ms.openlocfilehash: 80c946da943e4880dbd82ea6b34d238b80030b4c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015193"
---
# <a name="set-up-smart-tags-in-advanced-ediscovery"></a>Smart Tags'i Advanced eDiscovery

Makine öğrenimi (ML) özellikleri Advanced eDiscovery bir gözden geçirme kümesinde büyük/küçük harf belgelerini gözden geçirerek karar sürecini daha verimli bir hale getirir. Akıllı etiketler, kullanıcı özelliklerini kararların ML getirmenin bir yolutur: gözden geçirme sırasında belgeleri etiketleme. Bir akıllı etiket grubu  oluşturmanın ardından, akıllı etiket grubuyla ilişkilendirilmiş ML modelin sonucunda alınan kararlar, etiket grubunda etiketlerle satır içinde görüntülenir. Bu, belirli ML gözden geçirerek elde etmek için sonuçların bilgileri satır içinde görmenizi sağlar.

## <a name="how-to-set-up-a-smart-tag-group"></a>Akıllı etiket grubu ayarlama

1. Gözden geçirme kümesinde Gözden geçirme kümesi **yönet'e ve sonra da** Etiketleri **yönet'e tıklayın**.

2. Etiket **grubu ekle'ye tıklayın** ve Akıllı etiket **grubu ekle'yi seçin**.

3. Etiket ML ilişkilendirmek istediğiniz veri modeli seçin.
    
   Bu, bir etiket grubu ve *N* alt etiketleri oluşturur; burada *N* , modelin olası çıkışlarının sayısıdır. Örneğin, [avukat-istemci ayrıcalık algılama modelinin iki](attorney-privilege-detection.md) olası çıktısı vardır: 

   - **Pozitif** – İstemci ayrıcalığı içeriği bulunan belgeleri etiketlemek için kullanın.
   
   - **Negatif** – Avukat veya istemci ayrıcalığı içeriği olmayan belgeleri etiketlemek için kullanın.
    
    Bu modeli seçin, gözden geçirme kümesi için iki alt etiketi olan bir etiket grubu (Pozitif adlı bir alt  etiket ve diğeri **negatif adlı)** oluşturulur. Bu örnekte, her çocuk etiketi avukatlık ayrıcalık algılama modelinin olası çıktılarından birini ifade eder.

4. İsteğe bağlı olarak, etiket grubunu ve alt etiketleri yeniden adlandırabilirsiniz. Örneğin, Pozitif etiketini Ayrıcalıklı olarak **ve Negatif** etiketini **de** **Ayrıcalıklı değil olarak** **yeniden adlandırabilirsiniz**.

## <a name="how-to-use-smart-tags"></a>Akıllı etiketleri kullanma

Bir belgeyi gözden geçirerek, uygun alt etiketin yanında modelin sonuçları görüntülenir. Örneğin, avukat-istemci ayrıcalık algılama için bir akıllı etiket grubunuz varsa ve muhtemelen ayrıcalıklı olabilecek bir belgeyi gözden geçirersiniz, sonuç olarak uygun etiketin yanında sonuçlanması için neden görüntülenir. Etiketin otomatik olarak belgeye uygulanmadı olduğunu unutmayın. Gözden geçiren belgeyi etiketleme konusunda karar verdi.
