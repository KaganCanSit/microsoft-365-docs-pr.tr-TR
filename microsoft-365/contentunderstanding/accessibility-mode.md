---
title: Erişilebilirlik modu'SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: Eğitim ve çalışma zamanlarında eğitim ve çalışma modelleriyle çalışırken erişilebilirlik özellikleri modunu SharePoint Syntex.
ms.openlocfilehash: 09fd16259a44a2aa4d1b82dca49fffa76065690b
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419065"
---
# <a name="accessibility-mode-in-sharepoint-syntex"></a>Erişilebilirlik modu'SharePoint Syntex

Diğer [SharePoint Syntex](index.md), kullanıcılar örnek belgelerle çalışırken tüm model eğitimi aşamalarında (etiket, eğit, test) erişilebilirlik modunu açabilirsiniz. Erişilebilirlik modunu kullanmak, görme zoru olan kullanıcıların, belge görüntüleyicisinde gezinen ve öğeleri etiketleyene kadar daha kolay klavye erişilebilirliğine sahip olmasına yardımcı olabilir.

Bu, kullanıcıların klavyelerini kullanarak belge görüntüleyicisinde metin içinde gezinmelerine ve yalnızca seçili değerlerin değil, aynı zamanda seçili metinden etiket kullanımının veya tahmini etiket değerlerinin anlatımını dinlemek için, modeli ek örnek belgelerle eğitmelerine yardımcı olur. 


![Erişilebilirlik modu'dur.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Gereksinimler

Anlatım sesini duymak için ekran okuyucusu ayarlarınıza bağlı olarak Ekran Okuyucusu [](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) uygulamasını Windows 10.

![Ekran Okuyucusu'mu açma.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Klavye kullanıcıları için etiketleme

Erişilebilirlik modunu kullanan klavye kullanıcıları için, görüntüleyicide örnek bir belgede metin etiketliyebilirsiniz, aşağıdaki tuşları kullanabilirsiniz:

- Sekme: Sizi ileri taşır ve bir sonraki sözcüğü seçer.
- Sekme + Shift: Sizi geriye taşır ve önceki sözcüğü seçer.
- Enter: Seçili sözcükten bir etiket kaldırır veya etiket kaldırır.
- Sağ ok: Seçili bir sözcükte tek tek karakterler arasında ilerlersiniz.
- Sol ok: Seçili bir sözcükte tek tek karakterler arasında geriye doğru ilerlersiniz.

> [!NOTE]
> Tek bir etiket için birden çok sözcük etiketliysiniz, her sözcüğü etiketlemelisiniz.


## <a name="narration"></a>Anlatım

Erişilebilirlik modunu kullanan Ekran Okuyucusu kullanıcıları için, klavye kullanıcılarının görüntüleyicide örnek belgede gezinmeleri için açıklanan klavye gezintisini kullanın.

Örnek belgelerde ve etiket dizesi değerleri arasında gezinken Ekran Okuyucusu kullanıcıya aşağıdaki ses istemlerini verir:

- Belge görüntüleyicisi arasında gezinmek için klavyeyi kullanırsanız, Ekran Okuyucusu sesi seçilen dizeyi gösterir.
- Seçili bir dizede, siz sol veya sağ ok tuşlarını kullanarak seçtiğiniz zaman Ekran Okuyucusu sesi dizedeki her karakterin durumunu gösterir.
- Etiketlenmiş bir dizeyi alırsanız, Ekran Okuyucusu değeri ve "etiketli" olarak okur.  Örneğin, etiket değeri "Contoso" ise, "Maliyetoso etiketli" olur. 
- Eğitim sekmesinde, belge görüntüleyicisinde yalnızca öngörülen bir dizeyi seçersiniz, Ekran Okuyucusu sesi değeri ve "tahmin edilen" durumuna döndürür. Bu durum, eğitim dosyada kullanıcı tarafından etiketlenmiş olan değerle eşleşmez.
- Eğitim sekmesinde, belge görüntüleyicisinde etiketlenmiş ve öngörülen bir dize seçersiniz, Ekran Okuyucusu sesi değeri belirtir ve ardından "etiketli ve tahmini" olur. Bu durum, eğitim başarılı olduğunda ve öngörülen değerle kullanıcı etiketi arasında bir eşleşme olduğunda ortaya çıkar.

Görüntüleyicide bir dize etiketli veya bir etiket kaldırıldıktan sonra, Ekran Okuyucusu siz çıkmadan önce değişikliklerinizi kaydetmeniz için sizi uyaracak.

## <a name="see-also"></a>Ayrıca Bkz

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Sınıflandırıcı oluşturma](create-a-classifier.md)










 


  
  



