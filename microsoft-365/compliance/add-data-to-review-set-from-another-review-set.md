---
title: Bir gözden geçirme kümesinden diğerine veri ekleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Microsoft Purview eKeşif (Premium) durumunda bir gözden geçirme kümesinden belgeleri seçmeyi ve başka bir kümede ayrı ayrı çalışmayı öğrenin.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 599af9e2060497738076cd702e9e3dd31f5db06d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094151"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Başka bir gözden geçirme kümesinden bir gözden geçirme kümesine veri ekleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bazı durumlarda, bir gözden geçirme kümesinden belge seçmek ve başka bir gözden geçirme kümesinde ayrı ayrı çalışmak gerekebilir. Bu, özellikle bir gözden geçirme kümesindeki içeriği dolandırdıysanız ve verilerin alt kümesinde analiz çalıştırmak istiyorsanız kullanışlıdır.

Bir gözden geçirme kümesinden diğerine içerik eklemek için bu makaledeki iş akışını izleyin.

## <a name="create-a-review-set"></a>Gözden geçirme kümesi oluşturma

Başlamadan önce, verileri eklemek için bir gözden geçirme kümesi oluşturmanız gerekir.  Servis talebinin **Gözden geçirme kümeleri** sekmesine yeni bir gözden geçirme kümesi eklenebilir. Daha fazla bilgi için bkz. [Gözden geçirme kümesi oluşturma](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>1. Adım: Başka bir gözden geçirme kümesine eklenecek içeriği tanımlama

Kaynak gözden geçirme kümesindeki belirli belgeleri seçerek veya gözden geçirme kümesi sorgusu tarafından döndürülen tüm öğeleri seçerek bir gözden geçirme kümesinden diğerine içerik ekleyebilirsiniz. Seçili öğeleri ekliyorsanız, öğeleri seçin, **Eylem'i** ve ardından **Başka bir gözden geçirme kümesine ekle'yi** seçin.

![Eylem menüsünde başka bir gözden geçirme kümesine ekleyin.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>2. Adım: Başka bir gözden geçirme kümesine ekleme seçeneklerini belirtme

**Başka bir gözden geçirme kümesine ekle seçenekleri** açılır sayfasında, öğeleri eklemek istediğiniz gözden geçirme kümesini seçin. **Tüm arama sonuçlarının** mı yoksa **Seçili öğelerin** mi ekleneceğini seçin.  **Ek bilgiler** , öğelerdeki tüm meta verileri dahil etme ve belgeler yeni gözden geçirme kümesine eklendiğinde kaynak gözden geçirme kümesinden etiketlerin dahil edilip edilmeyeceğini ( **Etiketler** onay kutusunu seçerek) sağlar.  

![Başka bir gözden geçirme kümesine veri ekleme seçenekleri.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

**Tamam'a** tıkladıktan sonra, içeriği başka bir gözden geçirme kümesine eklemek için yeni bir iş (**başka bir gözden geçirme kümesine veri ekleme** adlı) oluşturulur. **İşler** sekmesine gidip bu işin ilerleme durumunu izleyebilirsiniz. Daha fazla bilgi için bkz. [İşleri yönetme](managing-jobs-ediscovery20.md).
