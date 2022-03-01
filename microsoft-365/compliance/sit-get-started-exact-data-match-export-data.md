---
title: Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8253ff73d53100c986a2bd8580830703c9f4b363
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015251"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma


Hassas veri tablosu, hassas verileri tanımlamak için belgelerinize içerik karşılaştıracak değerlerin satırlarını içeren bir metin dosyasıdır. Bu değerler, içerikte tespit etmek ve üzerinde koruyucu işlemler yapmak istediğiniz, metin formunda kişisel kimliği ortaya çıkarabilecek bilgiler, ürün kayıtları veya diğer hassas veriler olabilir.

Veriler desteklenen biçimlerden biri içinde dışarı aktarıldıktan sonra, EDM şeması oluşturma işlemine devam edebilirsiniz.

## <a name="defining-your-edm-sensitive-type"></a>EDM Duyarlı türlerinizi tanımlama

EDM hassas türlerinizi tanımlarken, en kritik kararlardan biri hangi alanların birincil alanlar olacağını belirlemedir. Birincil alanların algılanabilir bir düzeni izlemesi ve EDM şemanız içinde aranabilir alanlar (sütunlar) olarak tanımlanmış olması gerekir. İkincil alanların, birincil alanlarla çevresindeki tüm metinle karşılaştırıldığından bu alanları hiçbir desenle izlemesi gerekmektedir.

Birincil alan olarak hangi sütunları kullanmalısınız? karar vermede size yardımcı olması için bu kuralları kullanın:

- Hassas veri tablodaki bir alanla eşleşen tek bir değerin varlığını temel alarak hassas verileri algılamanız gerekirse, onu çevreleyen diğer hassas veriler ne olursa olsun, bu sütunun bir EDM türü için birincil öğe olarak tanımlanmış olması gerekir. 
- Hassas veri tablomdaki farklı alanların birden çok bileşimi içerikte algılanırsa, bu tür bileşimlerin çoğunda ortak olan sütunları tanımlayabilir ve bunları birincil öğeler ve diğer alanların bileşimleri olarak ikincil öğeler olarak belirleyebilirsiniz.
- Birincil alan olarak kullanmak istediğiniz bir sütun herhangi bir metin dizesi gibi algılanabilir bir düzenden sonra geliyorsa veya büyük miktarda belge veya e-postanın herhangi bir yerde mevcut olan algılanabilir düzenleri izliyorsa, birincil öğeler olarak daha iyi yapılandırılmış başka sütunları seçmeyi deneyin.

Örneğin, `full name`sütunlara , , `date of birth``account number``Social Security Number`ve hatta adlar ve lastekler, algılamak istediğiniz farklı veri bileşimlerinin ortak olan sütunları olsa bile, bu tür dizeler kolayca tanınmayı sağlayacak düzenlere uymaz ve hassas bir bilgi türü olarak tanımlamak zor olabilir. Bunun nedeni, bazı adların büyük harfle başlanmazken iki, üç veya daha fazla sözcükle oluşturulmuş olması ve hatta sayı veya başka alfabetik olmayan karakterler içermesidir. Doğum tarihi daha kolay belirlenebilir, ancak her e-postada ve çoğu belgede en az bir tarih yer alamayacak olması bu nedenle iyi bir aday da değildir. Sosyal güvenlik numaraları ve hesap numaraları, birincil alan olarak kullanmak üzere uygun adaylardır.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Hassas verileri .csv, .tsv veya boruyla ayrılmış biçimde kaydetme

1. Kullanmak istediğiniz hassas bilgileri tanımlayabilirsiniz. Verileri Veri Kaynağı gibi bir Microsoft Excel dışarı aktarın ve dosyayı bir metin dosyasına kaydedin. Dosya, virgülle ayrılmış .csv), .tsv (sekmeyle ayrılmış değerler) veya boruyla ayrılmış (|) biçiminde kaydedilebilir. Veri değerlerinizi sokak adresleri gibi virgüllerle birlikte bulunduğu durumlarda .tsv biçimi önerilir.
Veri dosyası en çok şunları içerebilir:
   - 100 milyon satıra kadar hassas veri satırı
   - Veri kaynağı başına en çok 32 sütun (alan)
   - Aranabilir olarak işaretlenmiş en çok 5 sütun (alan)

2. .csv veya .tsv dosyasındaki hassas verileri, ilk satırda EDM tabanlı sınıflandırma için kullanılan alanların adlarını içeren şekilde yapılandırabilirsiniz. Dosyanıza "ssn", "doğum tarihi", "ad", "soyadı" gibi alan adlarınız olabilir. Sütun üst bilgisi adları boşluk veya alt çizgi içerebilir. Örneğin, bu makalede .csv dosyanın adı *PatientRecords.csv* ve bu dosyanın sütunları *PatientID*, *MRN, LastName*, *FirstName*, *SSN* gibi daha fazlasını içerir.

3. Hassas veri alanlarının biçimine dikkat olun. Özel olarak, içeriğinde virgül bulunan alanlar (örneğin, "Seattle,WA" değerini içeren açık adres) bu alanlar, .csv biçimi seçildiğinde ayrıştırılarak iki ayrı alan olarak ayrıştırılamaz. Bunu önlemek için, .tsv biçimini kullanın veya hassas veri tablosunda değerleri içeren virgül çift tırnak içine alın. Değerler içeren virgül de boşluk içeriyorsa, ilgili biçimle eşleşen özel bir SIT oluşturmanız gerekir. Örneğin, içinde virgüller ve boşluklar olan çok sözcüklü dizeyi algılayan bir SIT.

## <a name="next-step"></a>Sonraki adım

- [Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Ayrıca bkz.

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
