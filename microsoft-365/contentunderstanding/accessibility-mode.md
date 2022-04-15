---
title: SharePoint Syntex'de erişilebilirlik modu
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: SharePoint Syntex modellerini eğitirken ve modellerle çalışırken erişilebilirlik özellikleri modunu kullanmayı öğrenin.
ms.openlocfilehash: 567abb862af27457c1eb9395e32bf68d98446887
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882340"
---
# <a name="accessibility-mode-in-sharepoint-syntex"></a>SharePoint Syntex'de erişilebilirlik modu

[SharePoint Syntex'da](index.md) kullanıcılar örnek belgelerle çalışırken model eğitiminin (etiket, eğit, test) tüm aşamalarında erişilebilirlik modunu açabilir. Erişilebilirlik modunu kullanmak, görme bozukluğu olan kullanıcıların belge görüntüleyicisinde gezinirken ve öğeleri etiketlediklerinde klavye erişilebilirliğini kolaylaştırmalarına yardımcı olabilir.

Bu, kullanıcıların klavyelerini kullanarak belge görüntüleyicisindeki metinlerde gezinmelerine ve yalnızca seçili değerlerin değil, aynı zamanda eylemlerin (seçili metinden etiketleme veya kaldırma gibi) anlatımını veya siz modeli ek örnek belgelerle eğitirken tahmin edilen etiket değerlerini duymalarına yardımcı olur. 


![Erişilebilirlik modu.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Gereksinimler

Anlatımın sesini duymak için, Windows 10 sisteminizdeki [Ekran Okuyucusu](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) ayarlarınızda Ekran Okuyucusu Uygulamasını açtığınızdan emin olun.

![Ekran Okuyucusu'nu açın.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Klavye kullanıcıları için etiketleme

Erişilebilirlik modunu kullanan klavye kullanıcıları için, görüntüleyicideki örnek bir belgede metin etiketlediyseniz aşağıdaki tuşları kullanabilirsiniz:

- Sekme: Sizi ileri taşır ve sonraki sözcüğü seçer.
- Sekme + Shift: Sizi geriye taşır ve önceki sözcüğü seçer.
- Enter: Seçili sözcükten bir etiketi etiketle veya kaldırır.
- Sağ ok: Seçili sözcükteki tek tek karakterler arasında ilerlemenizi sağlar.
- Sol ok: Seçili sözcükteki tek tek karakterler arasında geriye doğru hareket eder.

> [!NOTE]
> Tek bir etiket için birden çok sözcüğü etiketlediyseniz, her sözcüğü etiketlemeniz gerekir.


## <a name="narration"></a>Anlatım

Erişilebilirlik modunu kullanan Ekran Okuyucusu kullanıcıları için, klavye kullanıcıları için açıklanan klavye gezintisinin aynısını kullanarak görüntüleyicideki örnek belgeyi gözden geçirin.

Örnek belgeler ve etiket dizesi değerleri arasında gezinirken Ekran Okuyucusu kullanıcıya aşağıdaki ses istemlerini verir:

- Belge görüntüleyicisinde gezinmek için klavyeyi kullandığınızda Ekran Okuyucusu sesi seçili dizeyi belirtir.
- Seçili dizede Ekran Okuyucusu sesi, siz seçerken sol veya sağ ok tuşlarını kullanarak dizedeki her karakteri belirtir.
- Etiketlenmiş bir dize seçerseniz Ekran Okuyucusu değeri belirtir ve ardından "etiketlenir".  Örneğin, etiket değeri "Contoso" ise , "Costoso etiketli" durumunu belirtir. 
- Eğitim sekmesinde, belge görüntüleyicisinde yalnızca tahmin edilen bir dize seçerseniz Ekran Okuyucusu sesi değeri belirtir ve ardından "tahmin edilir". Bu durum, eğitim dosyada kullanıcı tarafından etiketlenen değerle eşleşmeyen bir değeri tahmin ettiğinde oluşur.
- Eğitim sekmesinde, belge görüntüleyicisinde etiketlenmiş ve tahmin edilmiş bir dize seçerseniz Ekran Okuyucusu sesi değeri belirtir ve ardından "etiketlenir ve tahmin edilir". Eğitim başarılı olduğunda ve tahmin edilen değerle kullanıcı etiketi arasında bir eşleşme olduğunda bu durum oluşur.

Bir dize etiketlendikten veya görüntüleyicide bir etiket kaldırıldıktan sonra Ekran Okuyucusu sesi, çıkmadan önce değişikliklerinizi kaydetmeniz için sizi uyarır.

## <a name="see-also"></a>Ayrıca bkz.

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Sınıflandırıcı oluşturma](create-a-classifier.md)










 


  
  



