---
title: Tam veri eşleşmesine dayalı hassas bilgi türleri için kaynak verilerini dışa aktarma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 913870afeef443c5b346172099b0cd47db13e52e
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760701"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Tam veri eşleşmesine dayalı hassas bilgi türleri için kaynak verilerini dışa aktarma


Hassas veri tablosu, hassas verileri tanımlamak için belgelerinizdeki içeriği karşılaştıracağınız değer satırları içeren bir metin dosyasıdır. Bu değerler, içerikte algılamak ve üzerinde koruyucu eylemler yapmak istediğiniz, kişisel bilgiler, ürün kayıtları veya metin biçimindeki diğer hassas veriler olabilir.

Veriler desteklenen biçimlerden birinde dışarı aktarıldıktan sonra EDM şeması oluşturmaya devam edebilirsiniz.

## <a name="defining-your-edm-sensitive-type"></a>EDM Hassas türünüzü tanımlama

EDM hassas türünüzü tanımlarken en kritik kararlardan biri hangi alanların birincil alanlar olacağıdır. Birincil alanların algılanabilir bir deseni izlemesi ve EDM şemanızda aranabilir alanlar (sütunlar) olarak tanımlanması gerekir. Birincil alanlarla eşleşen tüm metinlerle karşılaştırılacağından, ikincil alanların herhangi bir deseni izlemesi gerekmez.

Birincil alan olarak hangi sütunları kullanmanız gerektiğine karar vermenize yardımcı olması için bu kuralları kullanın:

- Hassas veri tablonuzdaki bir alanla eşleşen tek bir değerin bulunmasına bağlı olarak hassas verileri algılamanız gerekiyorsa, çevresindeki diğer hassas verilerin varlığından bağımsız olarak, bu sütunun bir EDM türü için birincil öğe olarak tanımlanması gerekir. 
- Hassas veri tablonuzdaki farklı alanların birden çok bileşiminin içerikte algılanması gerekiyorsa, bu tür birleşimlerin çoğunda ortak olan sütunları belirleyin ve bunları birincil öğeler ve diğer alanların birleşimleri olarak ikincil öğeler olarak belirleyin.
- Birincil alan olarak kullanmak istediğiniz bir sütun herhangi bir metin dizesi gibi algılanabilir bir deseni izlemiyorsa veya belge veya e-postaların büyük bir yüzdesinin herhangi bir yerinde bulunan algılanabilir desenleri takip etmiyorsa, birincil öğeler olarak diğer daha iyi yapılandırılmış sütunları seçmeyi deneyin.

Örneğin, , , `date of birth``account number`ve sütunlarınız `full name`varsa, adınız ve `Social Security Number`soyadlarınız algılamak istediğiniz farklı veri birleşimlerinde ortak olacak sütunlar olsa bile, bu tür dizeler kolayca tanımlanabilir desenleri izlemez ve hassas bir bilgi türü olarak tanımlanması zor olabilir. Bunun nedeni, bazı adların büyük harfle bile başlayamayabilir, iki, üç veya daha fazla sözcük tarafından biçimlendirilmeleri ve hatta sayı veya alfabetik olmayan karakterler içermeleridir. Doğum tarihi daha kolay belirlenebilir, ancak her e-posta ve çoğu belge en az bir tarih içereceğinden iyi bir aday değildir. Sosyal güvenlik numaraları ve hesap numaraları birincil alan olarak kullanmak için iyi adaylardır.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Hassas verileri .csv, .tsv veya kanalla ayrılmış biçimde kaydetme

1. Kullanmak istediğiniz hassas bilgileri belirleyin. Verileri Microsoft Excel gibi bir uygulamaya aktarın ve dosyayı bir metin dosyasına kaydedin. Dosya .csv (virgülle ayrılmış değerler), .tsv (sekmeyle ayrılmış değerler) veya dikey çizgiyle ayrılmış (|) biçiminde kaydedilebilir. Veri değerlerinizin sokak adresleri gibi virgül içerebileceği durumlarda .tsv biçimi önerilir.
Veri dosyası en fazla şunları içerebilir:
   - 100 milyon satıra kadar hassas veri
   - Veri kaynağı başına en fazla 32 sütun (alan)
   - Aranabilir olarak işaretlenmiş en fazla 5 sütun (alan)

2. .csv veya .tsv dosyasındaki hassas verileri, ilk satırda EDM tabanlı sınıflandırma için kullanılan alanların adlarının yer aldığı şekilde yapılandırın. Dosyanızda "ssn", "birthdate", "firstname", "lastname" gibi alan adları olabilir. Sütun başlığı adları boşluk veya alt çizgi içeremez. Örneğin, bu makalede kullandığımız örnek .csv dosyası *PatientRecords.csv* olarak adlandırılır ve sütunları *PatientID*, *MRN*, *LastName, FirstName*, *SSN* ve daha fazlasını içerir. 

3. Hassas veri alanlarının biçimine dikkat edin. Özellikle, içeriğinde virgül içerebilen alanlar( örneğin, "Seattle,WA" değerini içeren bir sokak adresi, .csv biçimi seçiliyse ayrıştırıldığında iki ayrı alan olarak ayrıştırılır. Bunu önlemek için .tsv biçimini kullanın veya hassas veri tablosunda değerleri içeren virgülleri çift tırnak içine alın. Değer içeren virgül de boşluk içeriyorsa, karşılık gelen biçimle eşleşen özel bir SIT oluşturmanız gerekir. Örneğin, içinde virgül ve boşluk bulunan çok sözcüklü dizeyi algılayan bir SIT.

## <a name="next-step"></a>Sonraki adım

- [Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Ayrıca bkz.

- [Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
