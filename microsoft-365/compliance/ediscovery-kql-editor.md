---
title: Arama sorguları oluşturmak için KQL düzenleyicisini kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
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
description: İçerik arama, eBulma (Standart) ve eBulma (Premium) içinde eBulma arama sorgularını yapılandırmak için KQL düzenleyicisini kullanabilirsiniz.
ms.openlocfilehash: f1339b064c736d19bb428f812429cf0620cb3f53
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949971"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Arama sorguları oluşturmak için KQL düzenleyicisini kullanma

Microsoft 365 eBulma araçları aramasında yeni KQL sorgu deneyimi, İçerik arama, Microsoft Purview eBulma (Standart) ve eBulma (Premium) içinde arama sorguları oluştururken geri bildirim ve rehberlik sağlar. Düzenleyiciye sorgu yazdığınızda, desteklenen aranabilir özellikler ve koşullar için otomatik tamamlama sağlar ve standart özellikler ve koşullar için desteklenen değerlerin listelerini sağlar. Örneğin, sorgunuzda e-posta özelliğini belirtirseniz `kind` düzenleyici, seçebileceğiniz desteklenen değerlerin listesini sunar. KQL düzenleyicisi, aramayı çalıştırmadan önce düzeltebileceğiniz olası sorgu hatalarını gerçek zamanlı olarak da görüntüler. En iyisi, standart koşul oluşturucusunda anahtar sözcükler ve koşullar kartlarını kullanarak sorguları el ile oluşturmak zorunda kalmadan karmaşık sorguları doğrudan düzenleyiciye yapıştırabilirsiniz.
  
KQL düzenleyicisini kullanmanın başlıca avantajları şunlardır:

- Rehberlik sağlar ve sıfırdan arama sorguları oluşturmanıza yardımcı olur.

- Uzun ve karmaşık sorguları doğrudan düzenleyiciye hızlı bir şekilde yapıştırmanızı sağlar. Örneğin, karşı danışmandan karmaşık bir sorgu alırsanız, koşul oluşturucusunu kullanmak yerine bunu KQL düzenleyicisine yapıştırabilirsiniz.

- Olası hataları hızla tanımlar ve sorunların nasıl çözüleceğini gösteren ipuçları görüntüler.

KQL düzenleyicisi, eBulma (Standart) ve eBulma (Premium) içinde sorgu tabanlı tutmalar oluşturduğunuzda da kullanılabilir.

## <a name="displaying-the-kql-editor"></a>KQL düzenleyicisini görüntüleme

Bir eBulma araması oluşturduğunuzda veya düzenlediğinizde, KQL düzenleyicisini görüntüleme ve kullanma seçeneği, arama veya koleksiyonlar sihirbazının **Koşullar** sayfasında bulunur.

### <a name="kql-editor-in-content-search-and-ediscovery-standard"></a>İçerik arama ve eBulma'da KQL düzenleyicisi (Standart)

![İçerik arama ve eBulma'da KQL düzenleyicisi (Standart)](../media/KQLEditorCore.png)

### <a name="kql-editor-in-ediscovery-premium"></a>eBulma'da KQL düzenleyicisi (Premium)

![eBulma'da KQL düzenleyicisi (Premium)](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>KQL düzenleyicisini kullanma

Aşağıdaki bölümlerde, KQL düzenleyicisinin nasıl öneriler sağladığına ve olası hataları nasıl algılayabileceklerine ilişkin örnekler gösterilir.

### <a name="autocompletion-of-search-properties-and-operators"></a>Arama özelliklerini ve işleçlerini otomatik olarak tamamlama

KQL düzenleyicisine bir arama sorgusu yazmaya başladığınızda, düzenleyici seçebileceğiniz desteklenen arama özelliklerinin (*özellik kısıtlamaları* olarak da adlandırılır) önerilen otomatik tamamlamasını görüntüler. Bu iki karakterle başlayan desteklenen özelliklerin listesini görüntülemek için en az iki karakter yazmanız gerekir. Örneğin, aşağıdaki ekran görüntüsü ile `Se`başlayan önerilen arama özelliklerini gösterir.

![KQL düzenleyicisi desteklenen özellikler önerir](../media/KQLEditorAutoCompleteProperties.png)

Ayrıca düzenleyici, tam bir özellik adı yazdığınızda desteklenen işleçlerin (, ve `<>`gibi`:``=`) listesini de sağlar. Örneğin, aşağıdaki ekran görüntüsü özelliği için `Date` önerilen işleçleri gösterir.

![KQL düzenleyicisi işleçler önerir](../media/KQLEditorOperatorSuggestions.png)

Desteklenen arama özellikleri ve işleçleri hakkında daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Özellik değeri önerileri

KQL düzenleyicisi bazı özelliklerin olası değerleri için öneriler sağlar. Örneğin, aşağıdaki ekran görüntüsü özelliği için `Kind` önerilen değerleri gösterir.

![KQL düzenleyicisi bazı özellikler için değerler önerir](../media/KQLEditorValueSuggestions.png)

Düzenleyici ayrıca, , `To``Recipients` ve `Participants`gibi `From`e-posta alıcısı özelliklerini yazdığınızda kullanıcıların listesini (UPN biçiminde) önerir.

![KQL düzenleyicisi, kullanıcılara alıcı e-posta özellikleri önerir](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Olası hataları algılama

KQL düzenleyicisi, arama sorgularındaki olası hataları algılar ve hatayı çözmenize yardımcı olmak için hataya neyin neden olduğuna ilişkin bir ipucu sağlar. Düzenleyici ayrıca bir özelliğin karşılık gelen bir işlemi veya değeri olmadığında olası bir hatayı gösterir. Sorgudaki olası hatalar kırmızı metinle vurgulanır ve **olası hatalar** açılan bölümünde hatanın açıklamaları ve olası düzeltmeleri görüntülenir. Örneğin, aşağıdaki sorguyu KQL düzenleyicisine yapıştırdıysanız dört olası hata algılanır.

![KQL düzenleyicisi hata algılama](../media/KQLEditorErrorDetection.png)

Bu durumda, olası hata ipuçlarını kullanarak sorgu sorunlarını giderebilir ve düzeltebilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

- Koşul oluşturucu ile KQL düzenleyicisi arasında geçiş yapabilirsiniz. Örneğin, Anahtar Sözcükler kutusunu ve birden çok koşul kartını kullanarak sorgu yapılandırmak için koşul oluşturucusunu kullanırsanız, sonuçta elde edilen sorguyu KQL düzenleyicisinde görüntüleyebilirsiniz. Ancak, KQL düzenleyicisinde karmaşık bir sorgu (anahtar sözcükler ve koşullarla) oluşturursanız, sonuçta elde edilen sorgu yalnızca koşul oluşturucusunda görüntülediğinizde Anahtar Sözcükler kutusunda görüntülenir.

- karmaşık bir sorguyu KQL düzenleyicisine yapıştırırsanız, düzenleyici olası hataları algılar ve hataları çözmek için olası çözümler önerir.
