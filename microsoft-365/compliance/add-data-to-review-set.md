---
title: Gözden geçirme kümesine arama sonuçları ekleme
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
ms.custom:
- seo-marvel-apr2020
description: Büyük/harf gözden geçirme kümesine arama sonuçlarının veya bu arama sonuçlarının Advanced eDiscovery örnekleri ek olduğunu öğrenin.
ms.openlocfilehash: bce0301e7045eeb0dd5c42f8a119d56649120a11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973852"
---
# <a name="add-search-results-to-a-review-set"></a>Gözden geçirme kümesine arama sonuçları ekleme

Bir aramanın sonuçlarından memnunsanız ve bu arama sonuçlarını gözden geçirmeye ve çözümlemeye hazırsanız, bunları durumdaki bir gözden geçirme kümesine  eklersiniz. Orijinal verilerin gözden geçirme kümesine kopyalanması, tema algılama, yakın yineleme algılama ve e-posta dizisini tanımlama gibi gelişmiş analiz araçları sağlayarak gözden geçirme ve çözümleme işlemlerini kolaylaştırır. Ayrıca, gözden geçirme kümesine Microsoft 365 olmayan veri kaynaklarından veriler de ekleyebilir, böylelikle bu verileri gözden geçirebilirsiniz ve böylece bu verileri Microsoft 365.

Bir aramanın sonuçlarını gözden geçirme kümesine eklerken (bir olayda gözden geçirme kümeleri Gözden Geçir kümeleri sekmesinde listelenir),  aşağıdaki şeyler gerçekleşir:

- Arama yeniden çalıştırın. Bu, gözden geçirme kümesine kopyalanan gerçek arama sonuçlarının, arama en son çalıştırılamazken döndürülen tahmini sonuçlardan farklı olduğu anlamına gelir.

- Arama sonuçlarıdaki tüm öğeler canlı hizmetlerdeki özgün veri kaynağından kopyalanır ve Microsoft bulutunda güvenli bir Azure Depolama konuma kopyalanır.

- Gözden geçirme kümesinde yer alan tüm verilerin olay verilerini gözden geçirme sırasında tamamen aranabilir durumda olacak şekilde, tüm öğeler (içerik ve meta veriler dahil) yeniden dizilir. Olay incelemesi sırasında gözden geçirme kümesinde verilerde arama sırasında, veri sonuçlarını kapsamlı ve hızlı aramalarda yeniden dizine alma.

- [Microsoft](encryption.md) şifreleme teknolojisiyle şifrelenmiş bir dosyadır ve e-posta iletisi ve ekli dosya gözden geçirme kümesine ekli olduğunda, arama sonuçlarında döndürülen e-posta iletisine eklenir. Gözden geçirme kümesinde şifresi çözülmüş dosyayı gözden geçirebilirsiniz ve sorgularsiniz. Gözden geçirme kümesine şifre çözülmüş e-posta ekleri eklemek için RMS Şifre Çözme rolüne atanmışsınız. Daha fazla bilgi için bkz[. eK bulma Microsoft 365 Şifre Çözme.](ediscovery-decryption.md)

Gözden geçirme kümesine veri eklemek için, Aramalar sekmesinde bir aramaya tıklayın  ve sonra açılır sayfada gözden geçirmek **için Sonuç** ekle'ye tıklayın.

Var olan bir gözden geçirme kümesine ekleyebilir veya yeni bir gözden geçirme kümesi oluşturabilirsiniz.  Yeni bir gözden geçirme kümesine ekleniyorsa, adı belirtin ve ardından  Ekle'ye tıklarsanız, görünen sayfayı görüntüler.

![Gözden geçirme kümesi seçin ve koleksiyon seçeneklerini yapılandırabilirsiniz.](../media/AeD_AddToReviewSet.png)

Gözden geçirme kümesine veri ekleme, uzun süredir çalışan bir işlemdir. Bu işlem, öğeleri Microsoft 365'daki özgün veri kaynaklarından (örneğin, posta kutularından ve sitelerden) toplamayı, azure Depolama konuma (bu kopyalama işlemi aynı zamanda *ingestion* olarak da denir) kopyalamayı ve sonra öğelerin yeniden sunucularını yeniden depolamayı içerir. küme sütununu gözden **geçirmek için eklendi** sütunundaki durumu izlemek için, İşlerin sekmesinde veya Aramalar **sekmesinde ilerleme durumunu izleyebilirsiniz**. Gözden geçirme kümesi işleme tamamlandıktan sonra, olayda Gözden  Geçir kümeleri sekmesine tıklayın ve sonra da gözden geçirme kümesinde verileri filtreleme, gözden geçirme, etiketleme ve dışarı aktarma işlemini başlatmak için gözden geçirme kümesine tıklayın.

## <a name="define-options-to-scope-your-collection-for-review"></a>Koleksiyonun kapsamını gözden geçirme için tanımlama

Var olan veya yeni bir gözden geçirme kümesine aramanın içeriğini eklerken, gözden geçirme için içeriği toplamak için aşağıdaki seçenekleri kullanabilirsiniz:

- **SharePoint sürümlerini dahil edin (beta)**: Koleksiyonun sürüm sınırları ve arama parametrelerine göre bir SharePoint belgesinin tüm sürümlerinin koleksiyonunu etkinleştirmek için bu seçeneği kullanın. Bu seçeneğin seçimi, gözden geçirme kümesine eklenen öğelerin boyutunu önemli ölçüde artırır.

- **Konuşma alma seçenekleri**: Gözden geçirme kümesine eklenen öğeler, ileri ve geri konuşma bağlamında içeriği gözden geçirmeye yardımcı olmak için zincir konuşmalar için etkinleştirilir. Daha fazla bilgi için bkz[. Advanced eDiscovery](conversation-review-sets.md).

- **Modern ekler için alma seçeneğini etkinleştirin**: Daha fazla gözden geçirmek üzere modern ekleri veya bağlı dosyaları koleksiyona eklemek için bu seçeneği kullanın. Modern eklerle ilgili aranabilir özellikler hakkında daha fazla bilgi için bkz. Modern [eklerin belge meta Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Gözden geçirme kümesine örnek ekleme

Tüm arama sonuçlarını gözden geçirme kümesine eklemeden önce daha kapsamlı bir şekilde doğrulamak için, her şeyi eklemek yerine arama sonuçlarından bir örnek olarak gözden geçirme kümesine  eklersiniz.

Gözden geçirme kümesine örnek eklemek için, Aramalar sekmesinde bir aramaya **tıklayın** ve açılır sayfada **Örnek'e** tıklayın. Örnekleme **parametreleri sayfasında** aşağıdaki seçeneklerden birini belirleyin:

- **Güven düzeyi %** **ve Güven aralığı %** - Gözden geçirme kümesine eklenen öğeler, ayar istediğiniz istatistiksel parametrelerle belirlenir. Sonuçları örneklemek için normalde bir güven düzeyi ve aralık kullanıyorsanız, bunları açılan kutularda belirtin. Aksi takdirde, varsayılan ayarları kullanın.

- **Rastgele örnek %** - Gözden geçirme kümesine eklenen öğelerde, arama tarafından döndürülen toplam öğe sayısının belirtilen yüzdesinin rastgele seçimi temel alınarak belirlenmektedir.

Önceki seçeneklerden birini seçtikten ve yapılandırdikten sonra, örneği eklemek için bir gözden geçirme kümesi seçin ve gönder'e **tıklayın**. Yine, İşlerin ilerleme durumunu, İş sekmesinde  veya Aramalar sekmesindeki Kümeyi gözden geçirmek için eklenmiş veri **sütunundaki durumu izleyebilirsiniz**.

## <a name="optical-character-recognition"></a>Optik karakter tanıma

Bir gözden geçirme kümesine arama sonuçları eklerken, Advanced eDiscovery'daki optik karakter tanıma (OCR) işlevselliği resimlerden metinleri otomatik olarak ayıklar ve resim metnini gözden geçirme kümesine eklenen verilerle birlikte ekler. Ayıklanan metni gözden geçirme kümesinde, seçili resim dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Bu, resimlerde metin üzerinde daha fazla gözden geçirme ve çözümleme yürütmenizi sağlar. OCR kayıp dosyalar, e-posta ekleri ve ekli resimler için destekler. OCR tarafından desteklenen resim dosyası biçimlerinin listesi için bkz. OCR'de [desteklenen dosya Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Bu dosyalarda kendi 2013 olaylarında OCR işlevini etkinleştirmeniz Advanced eDiscovery. Daha fazla bilgi için bkz [. Arama ve çözümleme ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
