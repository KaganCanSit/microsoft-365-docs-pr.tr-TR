---
title: Bir gözden geçirme kümesinde verileri çözümlemek için Advanced eDiscovery
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
description: Bir olay çözümlemek için belge kümelerini düzenlemek için Advanced eDiscovery öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 829e6e6441403cf5a934e81a1a437f65d2de3db3
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62974115"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Bir gözden geçirme kümesinde verileri çözümlemek için Advanced eDiscovery

Toplanan belge sayısı büyük olduğunda, hepsini gözden geçirmek zor olabilir. Advanced eDiscovery, herhangi bir kayıp olmadan gözden geçir projesinde yer alan ve belgeleri uygun bir şekilde düzenlemenize yardımcı olmak için, belgeleri çözümlemeye yönelik bir dizi araç sağlar. Bu özellikler hakkında daha fazla bilgi edinmek için bkz:

- [Yinelenen algılamaya yakın](near-duplicate-detection-in-advanced-ediscovery.md)

- [E-posta dizileri](email-threading-in-advanced-ediscovery.md)

- [Temalar](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Gözden geçirme kümesi için çözümleme çalıştırma

Gözden geçirme kümesinde verileri çözümlemek için:

1. Vakanız için çözümleme ayarlarını yapılandırma. Daha fazla bilgi için bkz [. Arama ve çözümleme ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Çözümlemek istediğiniz gözden geçirme kümesi açın.

3. **AnalizE-posta** >  **analizi için & çalıştır'a tıklayın**.

   ![Analiz açılan listesinden & e-posta analizi için belgeyi çalıştır'ı seçin](..\media\RunAnalytics1.png)

Çözümlemenin ilerlemesini, olayla ilgili **İş** sekmesinden görebilirsiniz.

 Çözümleme tamamlandıktan sonra çözümleme raporunu ekleyebilirsiniz, inceleme kümeniz içinde çözümleme çıktıları üzerinde sorgu çalıştırabilirsiniz (bkz. Gözden geçirme kümenizin içindeki [](review-set-search.md)sorgular ve verili belgenin ilgili belgelerine bakın (bkz. Gözden geçirme kümesinde verileri gözden [geçirme](reviewing-data-in-review-set.md)).

## <a name="using-the-for-review-filter-query"></a>Gözden Geçirme için filtre sorgusunu kullanma

Gözden geçirme kümesiyle ilgili çözümlemeleri çalıştırdikten sonra, otomatik olarak oluşturulan ve gözden geçirme için adlandırılan, immaterial, yinelenen veya dahil olmayan öğeleri dışarıda tutmak için incelemenizi filtreleyen bir filtre sorgusu kullanabilirsiniz. Bu sizi yalnızca gözden geçirme kümesinde temsili, benzersiz ve kapsayıcı öğelerle bırakır.

Gözden Geçirme için **filtre sorgusunu** gözden geçirme kümesine uygulamak için, **Kaydedilmiş** **\[** filtre sorguları açılan listesini seçin ve sonra da Gözden Geçirme için OtomatikGen] seçeneğini seçin.

![Kaydedilmiş filtre sorguları açılan listesinde Gözden Geçirme için seçin](..\media\ForReviewFilterQuery1.png)

İşte Gözden Geçirme için filtre **sorgusunun söz** dizimi:

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

Aşağıdaki listede, filtre sorgusunun sonucu, gözden geçirme kümesine uygulayan içeriği açısından açıklar.

- **E-posta.** Kapsayıcı veya KapsayıcıMinus **olarak** işaretlenmiş **öğeleri görüntüler**. Kapsayıcı bir öğe, e-posta ileti dizisinde yer alan son iletidir. E-posta dizisinde önceki tüm içeriği içerir. Kapsayıcı eksi e-posta ileti dizisinde belirli bir iletiyle ilişkilendirilmiş bir veya daha fazla ek içerir. Gözden geçirenler, e-posta ileti dizisinde hangi iletilerin ilişkili ekleri olduğunu belirlemek için kapsayıcı eksi değerini kullanabilir.

- **Ekler**. Aynı E-posta Kümesi'nin yinelenen eklerini filtreler. Yalnızca e-posta ileti dizisinde benzersiz olan ekler görüntülenir.

- **Belgeler ve diğer belgeler**. Yinelenen belgeleri filtreler. Yalnızca gözden geçirme kümesinde benzersiz olan belgeler görüntülenir.

- **Teams konuşmalar**. Gözden Teams tüm konuşmalar (Yammer) konuşmalar görüntülenir.

Kapsayıcı türler ve belge benzersizliği hakkında daha fazla bilgi için bkz. [E-posta dizileri Advanced eDiscovery](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> Advanced eDiscovery'ta yeni büyük[](advanced-ediscovery-new-case-format.md)/küçük harf biçiminin genel önizlemesi sırasında, Gözden  Geçirme için filtre sorgusu 4 Kasım 2021'den önce oluşturulan gözden geçirme kümeleri için Teams veya Yammer konuşmalarını (büyük harf biçiminin olduğu durumlarda) geri dönüp bakmdı. Bu sorun çözüldü. Başka bir ifadeyle, Gözden Geçirme için  sorguyu büyük harf biçimini kullanan bir gözden geçirme kümesine yeniden kullanırsanız, tüm yeni veya küçük harf konuşmaları dahil Teams veya Yammer filtre sorgusuyla eşanlı öğeler görüntülenebilir.

## <a name="analytics-report"></a>Analiz raporu

Gözden geçirme kümesine yönelik çözümleme raporunu görüntülemek için:

1. Gözden geçirme kümesi açın.

2. **Analiz Gösterisi** **raporları'ne** >  tıklayın.

Analiz **raporunun** , çözümlemeden gelen yedi bileşeni vardır:

- **Hedef popülasyon:** Gözden geçirme kümesinde bulunan e-posta iletilerinin, eklerin ve eksik belgelerin sayısı.

- **Belgeler (ekler hariç):** Özet olan, bir özetin yakın yinelemesi veya başka bir belgenin tam kopyası olan serbest belge sayısı.

- **E-postalar:** Kapsayıcı, kapsayıcı kopya, dahil eksi veya yukarıdakilerin hiçbiri olarak işaretlenen e-posta iletilerinin sayısı.

- **Ekler:** Gözden geçirme kümesinde, başka bir e-posta ekin benzersiz veya yinelenen e-posta eklerinin sayısı.

- **Belgeleri dosya türüne göre numarala:** Dosya uzantısıyla tanımlanan dosya sayısı.

- **Belgeler kaynak:** özgün veri kaynağına göre içeriğin özeti.

- **süreç tarafından toplanan belgeler:** Gözden geçirme kümesi süreçlerine göre içeriğin özeti. 
