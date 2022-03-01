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
description: İçerik arama, Core eKbulma ve Diğer İçerik aramalarında eKbulma arama sorgularını yapılandırmak için KQL düzenleyicisini Advanced eDiscovery.
ms.openlocfilehash: 6c553a20116eba478961b606f30fa7af8c4c322e
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996610"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Arama sorguları oluşturmak için KQL düzenleyicisini kullanma

eBulma araçları arama özelliğinde yeni KQ Microsoft 365 L sorgu deneyimi, İçerik arama, Çekirdek eKbulma ve Başka bir adla arama sorguları  oluştururken geri bildirim ve Advanced eDiscovery. Düzenleyiciye sorgular yazarak, desteklenen arama özelliği ve koşulları için otomatik tamamlama sağlar ve standart özellikler ve koşullar için desteklenen değer listeleri sağlar. Örneğin, sorguda e-posta `kind` özelliğini belirtirsiniz, düzenleyici seçebilirsiniz desteklenen değerlerin listesini gösterir. KQL düzenleyicisi, aramanızı çalıştırmadan önce düzeltebilirsiniz ve olası sorgu hatalarını gerçek zamanlı olarak görüntüler. En güzeli de, standart koşul oluşturucusunu kullanarak anahtar sözcükleri ve koşul kartlarını kullanarak sorguları el ile oluşturmak zorunda kalmadan, karmaşık sorguları doğrudan düzenleyiciye yapıştırabilirsiniz.
  
KQL düzenleyicisini kullanmanın önemli avantajları:

- Rehberlik sağlar ve sıfırdan arama sorguları oluşturmanıza yardımcı olur.

- Uzun ve karmaşık sorguları doğrudan düzenleyiciye yapıştırmak için olanak sağlar. Örneğin, karşıt avukattan karmaşık bir sorgu alırsanız, koşul oluşturucusunu kullanmak yerine bunu KQL düzenleyicisine yapıştırabilirsiniz.

- Olası hataları hızla tanımlar ve sorunları çözmeyle ilgili ipuçları görüntüler.

KQL düzenleyicisi, Core eKovery ve Advanced eDiscovery'de sorgu tabanlı 122-1000

## <a name="displaying-the-kql-editor"></a>KQL düzenleyicisini görüntüleme

eBulma araması seniz veya düzenleyseniz, KQL düzenleyicisini görüntüleme ve kullanma seçeneği arama veya koleksiyonlar sihirbazının Koşullar sayfasında  bulunur.

### <a name="kql-editor-in-content-search-and-core-ediscovery"></a>İçerik arama ve Çekirdek eKbulma'da KQL düzenleyicisi

![İçerik arama ve Çekirdek eKbulma'da KQL düzenleyicisi](../media/KQLEditorCore.png)

### <a name="kql-editor-in-advanced-ediscovery"></a>Advanced eDiscovery'de KQL düzenleyicisi

![Advanced eDiscovery'de KQL düzenleyicisi](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>KQL düzenleyicisini kullanma

Aşağıdaki bölümlerde, KQL düzenleyicisinin öneriler gösterme ve olası hataları algılama örnekleri yer almaktadır.

### <a name="autocompletion-of-search-properties-and-operators"></a>Arama özelliklerinin ve işleçlerinin otomatik tamamlama

KQL düzenleyicisinde bir arama sorgusu yazmaya baş baş günü, düzenleyici seçerek, desteklenen arama özelliklerinin (özellik kısıtlamaları olarak da *adlandırılan) otomatik* tamamlama önerilerini görüntüler. Bu iki karakterle başlayan desteklenen özelliklerin listesini görüntülemek için en az iki karakter yazmalı. Örneğin, aşağıdaki ekran görüntüsü ile başlayan önerilen arama özelliklerini gösterir `Se`.

![KQL düzenleyicisi desteklenen özellikler önerir](../media/KQLEditorAutoCompleteProperties.png)

Ayrıca, düzenleyici tam özellik adı yazmanız için desteklenen işleçlerin ( `:`, ve `=` `<>`) bir listesini de önerir. Örneğin, aşağıdaki ekran görüntüsünde özellik için önerilen işleçler `Date` gösterilmektedir.

![KQL düzenleyicisi işleçler önerir](../media/KQLEditorOperatorSuggestions.png)

Desteklenen arama özellikleri ve işleçleri hakkında daha fazla bilgi için bkz. [eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Özellik değeri önerileri

KQL düzenleyicisi bazı özelliklerin olası değerleri için öneriler sağlar. Örneğin, aşağıdaki ekran görüntüsü özellik için önerilen değerleri `Kind` gösterir.

![KQL düzenleyicisi bazı özellikler için değerler önerir](../media/KQLEditorValueSuggestions.png)

Düzenleyici, , ve gibi e-posta alıcısı özelliklerini yazarak kullanıcı listesini de (UPN biçiminde`From``To``Recipients`) önerir.`Participants`

![KQL düzenleyicisi, alıcı e-posta özellikleri için kullanıcılara önerir](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Olası hataları algılama

KQL düzenleyicisi arama sorgularında olası hataları algılar ve hatayı çözmenize yardımcı olmak için hatanın neden olduğu konusunda bir ipucu sağlar. Düzenleyici, bir özelliğin ilgili bir işlemi veya değeri yoksa olası bir hatayı da gösterir. Sorguda olası hatalar kırmızı metinle vurgulanır ve Olası hatalar açılan bölümünde hatanın açıklamaları **ve olası** düzeltmeleri görüntülenir. Örneğin, aşağıdaki sorguyu KQL düzenleyicisine yapıştırdıysanız, dört olası hata algılanır.

![KQL düzenleyicisi hata algılama](../media/KQLEditorErrorDetection.png)

Bu durumda, sorguyu gidermek ve düzeltmek için olası hata ipuçlarını kullanabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

- Koşul oluşturucusu ile KQL düzenleyicisi arasında geçişabilirsiniz. Örneğin, Anahtar Sözcükler kutusunu ve birden çok koşul kartlarını kullanarak bir sorguyu yapılandırmak için koşul oluşturucusunu kullanırsanız, sonuçta elde edilen sorguyu KQL düzenleyicisinde görüntüebilirsiniz. Bununla birlikte, KQL düzenleyicisinde karmaşık bir sorgu (anahtar sözcükler ve koşullarla) oluşturursanız, sonuçta elde edilen sorgu yalnızca koşul oluşturucussinde görüntülendiğinde Anahtar Sözcükler kutusunda görüntülenir.

- KQL düzenleyicisine karmaşık bir sorgu yapıştırıyorsanız, düzenleyici olası hataları algılar ve hataları çözmek için olası çözümler önerir.
