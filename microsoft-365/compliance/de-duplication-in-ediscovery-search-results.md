---
title: eBulma arama sonuçlarında yinelenenleri kaldırma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/21/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5af334b6-a15d-4f73-97f8-1423457d9f6b
ms.custom:
- seo-marvel-apr2020
description: E-posta iletisinin yalnızca bir kopyasının dışarı aktarılabilmesi için yinelenen eBulma arama sonuçlarını nasıl ortadan kaldıracağınızı öğrenin.
ms.openlocfilehash: 1632f0179479d7a2e283f0ebcf3fdab06751cdc7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992248"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>eBulma arama sonuçlarında yinelenenleri kaldırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, eBulma arama sonuçlarının yinelenenleri kaldırma işleminin nasıl çalıştığı ve yinelenenleri kaldırma algoritmasının sınırlamaları açıklanmaktadır.
  
eBulma aramasının sonuçlarını dışarı aktarmak için eBulma araçlarını kullanırken, dışarı aktarılan sonuçların yinelenenlerini kaldırma seçeneğiniz vardır. Bu ne anlama geliyor? Yinelenenleri kaldırmayı etkinleştirdiğinizde (varsayılan olarak, yinelenenleri kaldırma etkinleştirilmez), aranan posta kutularında aynı iletinin birden çok örneği bulunsa bile e-posta iletisinin yalnızca bir kopyası dışarı aktarılır. Yinelenenleri kaldırma, arama sonuçları dışarı aktarıldıktan sonra gözden geçirmeniz ve çözümlemeniz gereken öğe sayısını azaltarak zaman kazanmanıza yardımcı olur. Ancak yinelenenleri kaldırma işleminin nasıl çalıştığını anlamak ve dışarı aktarma işlemi sırasında benzersiz bir öğenin yineleme olarak işaretlenmesine neden olabilecek algoritma sınırlamaları olduğunu bilmeniz önemlidir.
  
## <a name="how-duplicate-messages-are-identified"></a>Yinelenen iletiler nasıl tanımlanır?

eBulma araçları, bir iletinin yinelenen olup olmadığını belirlemek için aşağıdaki e-posta özelliklerinin bir bileşimini kullanır:
  
- **InternetMessageId** - Bu özellik, belirli bir iletinin belirli bir sürümüne başvuran genel olarak benzersiz bir tanımlayıcı olan e-posta iletisinin İnternet ileti tanımlayıcısını belirtir. Bu kimlik, gönderenin e-posta istemci programı veya iletiyi gönderen ana bilgisayar e-posta sistemi tarafından oluşturulur. Bir kişi birden fazla alıcıya ileti gönderirse, İnternet ileti kimliği iletinin her örneği için aynı olur. Özgün iletide yapılan sonraki düzeltmeler farklı bir ileti tanımlayıcısı alır. 

- **ConversationTopic** - Bu özellik, iletinin konuşma yazışmasının konusunu belirtir. **ConversationTopic** özelliğinin değeri, konuşmanın genel konusunu açıklayan dizedir. Konuşma, ilk iletiden ve ilk iletiye yanıt olarak gönderilen tüm iletilerden oluşur. Aynı konuşmadaki iletiler **ConversationTopic** özelliği için aynı değere sahiptir. Bu özelliğin değeri genellikle konuşmayı oluşturan ilk iletideki Konu satırıdır. 

- **BodyTagInfo** - Bu bir iç Exchange deposu özelliğidir. Bu özelliğin değeri, iletinin gövdesindeki çeşitli öznitelikler denetlenerek hesaplanır. Bu özellik, iletilerin gövdesindeki farkları tanımlamak için kullanılır. 

eBulma dışarı aktarma işlemi sırasında, arama ölçütleriyle eşleşen her ileti için bu üç özellik karşılaştırılır. bu özellikler iki (veya daha fazla) ileti için aynıysa, bu iletilerin yinelenenleri olduğu belirlenir ve sonuçta yinelenenleri kaldırma etkinleştirildiğinde iletinin yalnızca bir kopyası dışarı aktarılır. Dışarı aktarılan ileti "kaynak öğe" olarak bilinir. Yinelenen iletiler hakkındaki bilgiler **,** dışarı aktarılan arama sonuçlarına dahil edilen **Results.csvveManifest.xml** raporlarına eklenir. **Results.csv** dosyasında, **Öğeye Çoğalt** sütununda bir değer bulunarak yinelenen bir ileti tanımlanır. Bu sütundaki değer, dışarı aktarılan iletinin **Öğe Kimliği** sütunundaki değerle eşleşir. 
  
Aşağıdaki grafiklerde, arama sonuçlarıyla birlikte dışarı aktarılan **Results.csv** ve **Manifest.xml** raporlarında yinelenen iletilerin nasıl görüntülendiği gösterilir. Bu raporlar, daha önce açıklanan ve yinelenenleri kaldırma algoritmasında kullanılan e-posta özelliklerini içermez. Bunun yerine, raporlar Exchange deposu tarafından öğelere atanan **Öğe Kimliği** özelliğini içerir. 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv raporu (Excel görüntülenir)
  
![Results.csv raporundaki yinelenen öğeler hakkındaki bilgileri görüntüleme.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml raporu (Excel görüntülenir)
  
![Manifest.xml raporundaki yinelenen öğeler hakkındaki bilgileri görüntüleme.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
Ayrıca, yinelenen iletilerdeki diğer özellikler dışarı aktarma raporlarına eklenir. Bu, yinelenen iletinin bulunduğu posta kutusunu, iletinin bir dağıtım grubuna gönderilip gönderilmediğini ve iletinin Bilgi veya Gizli olup olmadığını başka bir kullanıcıya içerir.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Yinelenenleri kaldırma algoritmasının sınırlamaları

Yinelenenleri kaldırma algoritmasının, benzersiz öğelerin yinelenen öğeler olarak işaretlenmesine neden olabilecek bazı bilinen sınırlamaları vardır. İsteğe bağlı yinelenenleri kaldırma özelliğini kullanıp kullanmamaya karar verebilmeniz için bu sınırlamaları anlamanız önemlidir.
  
Yinelenenleri kaldırma özelliğinin bir iletiyi yanlışlıkla yineleme olarak tanımlayıp dışarı aktarmaması (ancak yine de dışarı aktarma raporlarında yineleme olarak nitelemesi) bir durum vardır. Bunlar, kullanıcının düzenlediği ancak göndermediği iletilerdir. Örneğin, bir kullanıcının Outlook'da bir iletiyi seçtiğini, iletinin içeriğini kopyalayıp yeni bir iletiye yapıştırır olduğunu varsayalım. Ardından kullanıcı, bir eki kaldırarak veya ekleyerek ya da konu satırını veya gövdeyi değiştirerek kopyalardan birini değiştirir. Bu iki ileti bir eBulma aramasının sorgusuyla eşleşiyorsa, arama sonuçları dışarı aktarıldığında yinelenenleri kaldırma etkinleştirildiğinde iletilerden yalnızca biri dışarı aktarılır. Bu nedenle, özgün ileti veya kopyalanan ileti değiştirilmiş olsa da, düzeltilen iletilerden hiçbiri gönderilmemiştir ve bu nedenle **InternetMessageId**, **ConversationTopic** ve **BodyTagInfo** özelliklerinin değerleri güncelleştirilmez. Ancak daha önce açıklandığı gibi, her iki ileti de dışarı aktarma raporlarında listelenir 
  
Bir posta kutusunun Dava Tutma veya In-Place Ayrı Tutma'da olması durumunda olduğu gibi, YazmaDa Kopyala sayfa koruma özelliği etkinleştirildiğinde de benzersiz iletiler yinelenen olarak işaretlenebilir. YazmaDa Kopyala özelliği, özgün öğeye yapılan düzeltme kaydedilmeden önce özgün iletiyi kopyalar (ve kullanıcının Kurtarılabilir Öğeler klasörünün Sürümler klasörüne kaydeder). Bu durumda, düzeltilen kopya ve özgün ileti (Kurtarılabilir Öğeler klasöründe) yinelenen iletiler olarak kabul edilebilir ve bu nedenle bunlardan yalnızca biri dışarı aktarılabilir.
  
> [!IMPORTANT]
> Yinelenenleri kaldırma algoritmasının sınırlamaları arama sonuçlarınızın kalitesini etkileyebilirse, öğeleri dışarı aktarırken yinelenenleri kaldırmayı etkinleştirmemelisiniz. Bu bölümde açıklanan durumların arama sonuçlarınızda bir faktör olma olasılığı düşükse ve yinelenen öğe olma olasılığı en yüksek olan öğe sayısını azaltmak istiyorsanız, yinelenenleri kaldırmayı etkinleştirmeyi düşünmelisiniz. 
  
## <a name="more-information"></a>Daha fazla bilgi

- Bu makaledeki bilgiler, aşağıdaki eBulma araçlarından birini kullanarak arama sonuçlarını dışarı aktarırken geçerlidir:

  - Office 365'daki uyumluluk merkezinde içerik arama

  - Exchange Online'da eBulma'In-Place

  - SharePoint Online'da eBulma Merkezi

- Arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz:

  - [İçerik Arama'yı Dışarı Aktar](export-search-results.md)

  - [İçerik Arama raporunu dışarı aktarma](export-a-content-search-report.md)

  - [eBulma arama sonuçlarını pst dosyasına In-Place dışarı aktarma](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - [eBulma Merkezi'nde içeriği dışarı aktarma ve rapor oluşturma](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
