---
title: Gözden geçirme kümesine arama sonuçları ekleme
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
ms.custom:
- seo-marvel-apr2020
description: EBulma (Premium) servis talebi gözden geçirme kümesine arama sonuçlarını veya bu arama sonuçlarının örneklerini eklemeyi öğrenin.
ms.openlocfilehash: 48371521edef225b63b6b06170dc422881122034
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640952"
---
# <a name="add-search-results-to-a-review-set"></a>Gözden geçirme kümesine arama sonuçları ekleme

Bir aramanın sonuçlarından memnun olduğunuzda ve bu arama sonuçlarını gözden geçirmeye ve analiz etmeye hazır olduğunuzda, bunları servis talebindeki bir gözden geçirme kümesine ekleyebilirsiniz. Özgün verilerin gözden geçirme kümesine kopyalanması ayrıca tema algılama, neredeyse yinelenen algılama ve e-posta iş parçacığı tanımlama gibi gelişmiş analiz araçları sağlayarak inceleme ve analiz sürecini kolaylaştırır. Ayrıca, Microsoft 365 dışındaki veri kaynaklarından bir gözden geçirme kümesine veri ekleyebilirsiniz, böylece bu verileri Microsoft 365'ten topladığınız verilere ek olarak gözden geçirebilirsiniz.

Bir aramanın sonuçlarını gözden geçirme kümesine eklediğinizde (bir servis talebindeki inceleme kümeleri **Gözden geçirme kümeleri** sekmesinde listelenir), aşağıdaki işlemler gerçekleşir:

- Arama yeniden çalıştırılır. Bu, gözden geçirme kümesine kopyalanan gerçek arama sonuçlarının, arama son çalıştırıldığında döndürülen tahmini sonuçlardan farklı olabileceği anlamına gelir.

- Arama sonuçlarındaki tüm öğeler canlı hizmetlerdeki özgün veri kaynağından kopyalanır ve Microsoft bulutunda güvenli bir Azure Depolama konumuna kopyalanır.

- Tüm öğeler (içerik ve meta veriler dahil) yeniden dizinlenir, böylece olay verilerinin gözden geçirilmesi sırasında gözden geçirme kümesindeki tüm veriler tamamen aranabilir. Verilerin yeniden dizine alınması, olay araştırması sırasında gözden geçirme kümesindeki verileri aradığınızda kapsamlı ve hızlı aramalara neden olur.

- [Microsoft şifreleme teknolojisiyle](encryption.md) şifrelenmiş ve arama sonuçlarında döndürülen bir e-posta iletisine eklenmiş bir dosyanın şifresi, e-posta iletisi ve ekli dosya gözden geçirme kümesine eklendiğinde çözülür. Şifresi çözülen dosyayı gözden geçirip gözden geçirme kümesinde sorgulayabilirsiniz. Gözden geçirme kümesine şifresi çözülmüş e-posta ekleri eklemek için RMS Şifre Çözme rolüne atanmış olmanız gerekir. Daha fazla bilgi için bkz[. Microsoft Purview eKeşif araçlarda şifre çözme](ediscovery-decryption.md).

Gözden geçirme kümesine veri eklemek için **, Aramalar** sekmesinde bir aramaya tıklayın ve ardından açılır sayfada **gözden geçirmek için Sonuç ekle'ye** tıklayın.

Mevcut bir gözden geçirme kümesine ekleyebilir veya yeni bir gözden geçirme kümesi oluşturabilirsiniz.  Yeni bir gözden geçirme kümesine ekliyorsanız, açılır sayfayı görüntülemek için adı belirtin ve **Ekle'ye** tıklayın.

![Bir gözden geçirme kümesi seçin ve koleksiyon seçeneklerini yapılandırın.](../media/AeD_AddToReviewSet.png)

Gözden geçirme kümesine veri eklemek uzun süren bir işlemdir. Bu işlem, Microsoft 365'teki özgün veri kaynaklarından (örneğin, posta kutularından ve sitelerden) öğeleri toplamayı, Bunları Azure Depolama konumuna kopyalamayı (bu kopyalama işlemine *alım* olarak da adlandırılır) ve sonra öğeleri yeniden dizine yüklemeyi içerir. **İlerleme durumunu İşler** sekmesinde veya **Aramalar** sekmesinde, **Kümeyi gözden geçirmek için eklenen veriler** sütunundaki durumu izleyerek izleyebilirsiniz. Gözden geçirme kümesi işleme tamamlandıktan sonra, inceleme kümesindeki verileri filtreleme, gözden geçirme, etiketleme ve dışarı aktarma işlemini başlatmak için olaydaki **Gözden geçirme kümeleri** sekmesine tıklayın ve ardından gözden geçirme kümesine tıklayın.

## <a name="define-options-to-scope-your-collection-for-review"></a>Koleksiyonunuzun kapsamını gözden geçirmek için tanımlama seçenekleri

Bir aramanın içeriğini var olan veya yeni bir gözden geçirme kümesine eklediğinizde, inceleme için içeriğin nasıl toplanacağına ilişkin aşağıdaki seçeneklere sahipsiniz:

- **SharePoint'ten sürümleri dahil et (beta):** Bu seçeneği, koleksiyonun sürüm sınırları ve arama parametrelerine göre bir SharePoint belgesinin tüm sürümlerinin toplanmasını etkinleştirmek için kullanın. Bu seçeneğin belirtilmesi, gözden geçirme kümesine eklenen öğelerin boyutunu önemli ölçüde artırır.

- **Konuşma alma seçenekleri: Gözden** geçirme kümesine eklenen öğeler, içeriği ileri geri konuşma bağlamında gözden geçirmeye yardımcı olmak üzere yazışma konuşmaları için etkinleştirilir. Daha fazla bilgi için bkz. [eBulma(Premium)'da konuşmaları gözden geçirme](conversation-review-sets.md).

- **Modern ekler için almayı etkinleştir**: Daha fazla inceleme için modern ekleri veya bağlı dosyaları koleksiyona eklemek için bu seçeneği kullanın. Modern eklerle ilgili aranabilir özellikler hakkında daha fazla bilgi için bkz. [eBulma'da (Premium) belge meta veri alanları](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Gözden geçirme kümesine örnek ekleme

Tümünü bir gözden geçirme kümesine eklemeden önce bir aramanın sonuçlarını daha kapsamlı bir şekilde doğrulamak istiyorsanız, her şeyi eklemek yerine bir gözden geçirme kümesine arama sonuçlarının bir örneğini ekleyebilirsiniz.

Gözden geçirme kümesine örnek eklemek için **, Aramalar** sekmesinde bir aramaya tıklayın ve açılır sayfada **Örnek'e** tıklayın. **Örnekleme parametreleri** sayfasında aşağıdaki seçeneklerden birini belirleyin:

- **Güvenilirlik düzeyi %** ve **Güvenilirlik aralığı %** - Gözden geçirme kümesine eklenen öğeler, ayarladığınız istatistiksel parametreler tarafından belirlenir. Sonuçları örnekleme sırasında genellikle bir güvenilirlik düzeyi ve aralık kullanıyorsanız, bunları açılan kutularda belirtin. Aksi takdirde varsayılan ayarları kullanın.

- **Rastgele örnek %** - Gözden geçirme kümesine eklenen öğeler, arama tarafından döndürülen toplam öğe sayısının belirtilen yüzdesinin rastgele seçilmesini temel alır.

Önceki seçeneklerden birini seçip yapılandırdıktan sonra, örneği eklemek için bir gözden geçirme kümesi seçin ve **gönder'e** tıklayın. Yeniden, **İşler** sekmesinde veya **Aramalar** sekmesinde, **Kümeyi gözden geçirmek için eklenen veriler** sütunundaki durumu izleyerek ilerleme durumunu izleyebilirsiniz.

## <a name="optical-character-recognition"></a>Optik karakter tanıma

Bir gözden geçirme kümesine arama sonuçları eklediğinizde, eBulma(Premium) içindeki optik karakter tanıma (OCR) işlevi görüntülerdeki metinleri otomatik olarak ayıklar ve bir gözden geçirme kümesine eklenen verileri içeren görüntü metnini içerir. Ayıklanan metni, gözden geçirme kümesindeki seçili görüntü dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Bu sayede görüntülerdeki metinler üzerinde daha fazla inceleme ve analiz gerçekleştirebilirsiniz. OCR gevşek dosyalar, e-posta ekleri ve ekli görüntüler için desteklenir. OCR için desteklenen görüntü dosyası biçimlerinin listesi için bkz. [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md#image).

eBulma'da (Premium) oluşturduğunuz her servis talebi için OCR işlevselliğini etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [Arama ve analiz ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
