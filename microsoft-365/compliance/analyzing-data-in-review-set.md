---
title: eBulma'da bir gözden geçirme kümesindeki verileri analiz etme (Premium)
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
description: Microsoft Purview eKeşif (Premium) servis talebini analiz ederken belge kümelerini düzenlemek için kullanılabilecek araçlar hakkında bilgi edinin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 822c21c05b865bdf1208f7679eaff9ea35b10a9e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634841"
---
# <a name="analyze-data-in-a-review-set-in-ediscovery-premium"></a>eBulma'da bir gözden geçirme kümesindeki verileri analiz etme (Premium)

Toplanan belgelerin sayısı büyük olduğunda, hepsini gözden geçirmek zor olabilir. Microsoft Purview eKeşif (Premium), bilgi kaybı olmadan gözden geçirilecek belgelerin hacmini azaltmak ve belgeleri tutarlı bir şekilde düzenlemenize yardımcı olmak için belgeleri analiz etmek için çeşitli araçlar sağlar. Bu özellikler hakkında daha fazla bilgi edinmek için bkz:

- [Yakın eş kopya algılama](near-duplicate-detection-in-advanced-ediscovery.md)

- [E-posta yazışması](email-threading-in-advanced-ediscovery.md)

- [Temalar](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Gözden geçirme kümesi için analiz çalıştırma

Gözden geçirme kümesindeki verileri analiz etmek için:

1. Servis talebiniz için analiz ayarlarını yapılandırın. Daha fazla bilgi için bkz. [Arama ve analiz ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Analiz etmek istediğiniz gözden geçirme kümesini açın.

3. **Analiz** > **Belgeyi çalıştır & e-posta analizi'ne** tıklayın.

   ![Analiz açılan listesinden Belgeyi çalıştır & e-posta analizi'ni seçin](..\media\RunAnalytics1.png)

Analizin ilerleme durumunu servis talebinin **İşler** sekmesinden de kontrol edebilirsiniz.

 Analiz tamamlandıktan sonra analiz raporunu görüntüleyebilir, çözümleme çıktıları üzerinde inceleme kümenizde sorgular çalıştırabilirsiniz (bkz. [Gözden geçirme kümenizdeki sorgular](review-set-search.md) ve belirli bir belgenin ilgili belgelerine bakın (bkz. [Gözden geçirme kümesindeki verileri gözden geçirme](reviewing-data-in-review-set.md).

## <a name="using-the-for-review-filter-query"></a>Gözden Geçirmek için filtre sorgusunu kullanma

Gözden geçirme kümesi için analiz çalıştırdıktan sonra, gözden geçirmenizi filtreleyerek önemsiz, yinelenen veya kapsayıcı olmayan öğeleri dışlayan otomatik olarak oluşturulmuş bir filtre sorgusu ( *Gözden Geçirme için* olarak adlandırılır) kullanabilirsiniz. Bu size yalnızca inceleme kümesindeki temsili, benzersiz ve kapsayıcı öğeleri bırakır.

**Gözden Geçirme için** filtre sorgusunu bir gözden geçirme kümesine uygulamak için **Kayıtlı filtre sorguları** açılan listesini ve ardından **Gözden Geçirmek için OtomatikGen] öğesini seçin\[**.

![Kaydedilen filtre sorguları açılan listesinden Gözden Geçir İçin'i seçin](..\media\ForReviewFilterQuery1.png)

**Gözden Geçirmek için** filtre sorgusunun söz dizimi aşağıdadır:

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

Aşağıdaki listede, filtre sorgusunun sonucu, siz gözden geçirme kümesine uygulandıktan sonra hangi içeriğin görüntülendiğine ilişkin olarak açıklanmaktadır.

- **E-posta.** **Inclusive** veya **InclusiveMinus** olarak işaretlenmiş öğeleri görüntüler. Kapsayıcı öğe, e-posta yazışmasında son iletidir. E-posta yazışmasında önceki tüm içeriği içerir. Dahil eksi, e-posta yazışmasında belirli iletiyle ilişkilendirilmiş bir veya daha fazla ek içerir. Gözden geçiren, e-posta yazışmasında hangi belirli iletilerin ilişkili ekleri olduğunu belirlemek için dahil eksi değerini kullanabilir.

- **Ekler**. Aynı E-posta Kümesindeki yinelenen ekleri filtreler. Yalnızca e-posta yazışmasında benzersiz olan ekler görüntülenir.

- **Belgeler ve diğer**. Yinelenen belgeleri filtreler. Yalnızca gözden geçirme kümesinde benzersiz olan belgeler görüntülenir.

- **Teams konuşmaları**. Gözden geçirme kümesindeki tüm Teams (ve Yammer) konuşmaları görüntülenir.

Kapsayıcı türler ve belge benzersizliği hakkında daha fazla bilgi için bkz. [eBulma'da e-posta iş parçacığı oluşturma (Premium)](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> eBulma'da (Premium) [yeni durum biçiminin](advanced-ediscovery-new-case-format.md) genel önizlemesi sırasında **Gözden Geçir için** filtre sorgusu, 4 Kasım 2021'den önce oluşturulan gözden geçirme kümeleri (büyük harf biçimini kullanan durumlarda) için Teams veya Yammer konuşmalarını döndürmedi. Bu sorun çözüldü. Başka bir deyişle **, Gözden Geçir için** sorgusunu büyük harf biçimini kullanan bir inceleme kümesine yeniden uygulamanız durumunda, tüm Teams veya Yammer konuşmaları dahil edildiğinden filtre sorgusuyla eşleşen daha fazla öğe görüntülenebilir.

## <a name="analytics-report"></a>Analiz raporu

Bir gözden geçirme kümesinin analiz raporunu görüntülemek için:

1. Gözden geçirme kümesini açın.

2. **Analiz Raporları göster'e** >  tıklayın.

**Analiz** raporu, analizden yedi bileşen içerir:

- **Hedef popülasyon:** Gözden geçirme kümesinde bulunan e-posta iletilerinin, eklerin ve gevşek belgelerin sayısı.

- **Belgeler (ekler hariç):** Özet olan gevşek belgelerin sayısı, bir özetin benzersiz ve benzer yinelemeleri veya başka bir belgenin tam yinelemesi.

- **Emails:** Kapsayıcı, kapsayıcı kopya, kapsayıcı eksi veya yukarıdakilerin hiçbiri olarak işaretlenen e-posta iletilerinin sayısı.

- **Ekleri:** Gözden geçirme kümesindeki başka bir e-posta ekinin benzersiz veya yinelenen e-posta eki sayısı.

- **Belgeleri dosya türüne göre numaralandırma:** Dosya uzantısıyla tanımlanan dosya sayısı.

- **Kaynağa göre belgeler:** İçeriğin özgün veri kaynağına göre özeti.

- **İşleme göre toplanan belgeler:** Küme işlemlerini gözden geçirerek içeriğin özeti. 
