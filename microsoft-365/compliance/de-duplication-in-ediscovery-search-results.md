---
title: eBulma arama sonuçlarında de-duplication
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
description: E-posta iletisine yalnızca bir kopyasının dışarı aktarılmış şekilde yinelenen eBulma arama sonuçlarının nasıl ortadan kaldırılacaklarını öğrenin.
ms.openlocfilehash: d09a0e09166928627be01d623963146cfd416bd2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032486"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>eBulma arama sonuçlarında de-duplication

Bu makalede, eBulma arama sonuçlarının yeniden çoğaltılması nasıl çalışır ve yineleme de-yineleme algoritmasının sınırlamaları açıklanmıştır.
  
eBulma aramalarının sonuçlarını dışarı aktarmaya ilişkin eBulma araçları kullanırken, dışarı aktarılmış sonuçları yineleme seçeneğiniz vardır. Bu ne anlama geliyor? Yinelemeyi de etkinleştirdiyseniz (yinelemeyi de-yineleme varsayılan olarak etkin değildir), aynı iletinin birden çok örneği arama yapılan posta kutularında bulunsa bile, e-posta iletisi yalnızca bir kopya dışarı aktarıldı. Yinelemeyi geri almak, arama sonuçları dışarı aktarıldıktan sonra gözden geçirmenız ve çözümlemek zorunda olduğunuz öğe sayısını azaltarak zaman kazanmak için size yardımcı olur. Ancak yinelemenin nasıl çalıştığını anlamak ve dışarı aktarma işlemi sırasında benzersiz bir öğenin yinelenen öğe olarak işaretlenirken algoritmada bazı sınırlamalar olduğunu unutmayın.
  
## <a name="how-duplicate-messages-are-identified"></a>Yinelenen iletiler nasıl tanımlanır?

eBulma araçları, bir iletinin yinelenen bir ileti olup olmadığını belirlemek için aşağıdaki e-posta özelliklerinin bir bileşimini kullanır:
  
- **InternetMessageId** - Bu özellik, belirli bir iletinin belirli bir sürümüne başvuran genel benzersiz bir tanımlayıcı olan e-posta iletisi internet iletisi tanımlayıcısını belirtir. Bu kimlik, iletiyi gönderen gönderenin e-posta istemci programı veya ana bilgisayar e-posta sistemi tarafından oluşturulur. Bir kişi birden çok alıcıya ileti gönderirse, İnternet ileti kimliği iletinin her örneğinde aynı olur. Özgün iletide daha sonra yapılan düzeltmeler farklı bir ileti tanımlayıcısı alır. 

- **ConversationTopic** - Bu özellik, bir iletinin konuşma dizisinde konuyu belirtir. **ConversationTopic özelliğinin** değeri, konuşmanın bir bütün olarak konusunu açıklayan dizedir. Konuşma bir ilk iletiden ve ilk ileti yanıtta gönderilen tüm iletilerden oluşur. KonuşmaTopic özelliği için aynı konuşma içindeki **iletilerin değeri** aynıdır. Bu özelliğin değeri normalde konuşmayı kabul eden ilk iletiden Konu satırıdır. 

- **BodyTagInfo** - Bu, bir depolama Exchange özelliktir. Bu özelliğin değeri, iletinin gövdesinde çeşitli öznitelikler denetlenerek hesaplanır. Bu özellik, iletilerin gövdesi arasındaki farkları tanımlamak için kullanılır. 

eBulma dışarı aktarma işlemi sırasında, bu üç özellik arama ölçütleriyle eşleşen her ileti için karşılaştırıldı. Bu özellikler iki (veya daha fazla) iletide aynı olursa, bu iletilerin yineli olduğu belirlenir ve de-duplication etkinleştirildiğinde iletinin yalnızca bir kopyasının dışarı aktarılmasıyla ilgili sonuç elde edilen sonuçtır. Dışarı aktarıldı iletisi, "kaynak öğe" olarak bilinir. Yinelenen iletiler hakkında bilgiler, dışarı **Results.csv** ve **Manifest.xml** raporlarında yer almaktadır. Yeni **Results.csv** , Öğeye Çoğalt sütununda bir değer bulunarak **yinelenen ileti tanımlanır** . Bu sütundaki değer, dışarı aktarıldı iletinin **Öğe** Kimliği sütunundaki değerle eşler. 
  
Aşağıdaki grafikte yinelenen iletilerin, arama **sonuçlarıyla dışarıResults.csv** veManifest.xmlraporlarda **** nasıl görüntüleniyor olduğu gösterilir. Bu raporlar, daha önce açıklanan ve yinelemeyi de-yineleme algoritmasında kullanılan e-posta özelliklerini içermez. Bunun yerine raporlar, **raporlarda**, depolama tarafından öğelere atanan Öğe Exchange vardır. 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv raporu (Excel)
  
![Rapordaki yinelenen öğeler hakkında bilgileri Results.csv görüntüleme.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml raporu (Excel)
  
![Rapordaki yinelenen öğeler hakkında bilgileri Manifest.xml görüntüleme.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
Ayrıca, yinelenen iletilerin diğer özellikleri de dışarı aktarma raporlarına dahil edilir. Bu, yinelenen iletinin bulunduğu posta kutusunu, iletinin bir dağıtım grubuna gönderip gönderilmedi ve iletinin Başka bir kullanıcıya bilgi mi yoksa Gizli mi olduğunu da içerir.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Yineleme de-yineleme algoritmasının sınırlamaları

Yineleme de-yineleme algoritmasının, benzersiz öğelerin yinelenen öğeler olarak işaretlenirken işaretlenirken neden olabileceği bilinen bazı sınırlamalar vardır. İsteğe bağlı yineleme özelliğinin kullanılamayup kullanılamayup kullanılamaya karar ver için, bu sınırlamaları anlamanız önemlidir.
  
Yinelemeyi geri gönderme özelliğinin bir iletiyi yinelenen ileti olarak yanlışlıkla belirlemesi ve dışarı aktarmama (ancak yine de dışarı aktarma raporlarında yinelenen ileti olarak tanımlamaya devam) neden olduğu bir durum vardır. Bunlar kullanıcının düzende yer alan ancak göndermesi olmayan iletilerdir. Örneğin, bir kullanıcının bu örnekte bir iletiyi Outlook, iletinin içeriğini kopyalayıp yeni bir iletiye yapıştırıyor olabilir. Sonra kullanıcı bir eki kaldırarak veya ekleyerek ya da konu satırı veya gövdesinin kendisini değiştirerek kopyalardan birini değiştirir. Bu iki ileti eBulma aramasında yapılan sorguyla eş kopyalandı ise, arama sonuçları dışarı aktarıldında de-duplication etkinleştirildiğinde iletilerden yalnızca biri dışarı aktarıldı. Dolayısıyla, özgün ileti veya kopyalanan ileti değiştirilmiş olsa bile, düzeltilmiş iletilerden hiçbiri gönderilmemiştir ve dolayısıyla **InternetMessageId**, **ConversationTopic** ve **BodyTagInfo** özelliklerinin değerleri güncelleştirilmedi. Ancak daha önce de belirtildiği gibi, her iki ileti de dışarı aktarma raporlarında listelenir 
  
Posta kutusunun Mahkeme Tutma veya Tutma durumunda olması durumunda olduğu gibi, Kopya Yaz sayfa koruma özelliği etkinleştirildiğinde de benzersiz iletiler yinelenen iletiler In-Place. Üzerine Yazma Kopyala özelliği, özgün öğeye düzeltme kaydedilemeden önce özgün iletiyi kopyalar (ve kullanıcının Kurtarılabilir Öğeler klasörünün Sürümler klasörüne kaydeder). Bu durumda, düzeltilmiş kopya ve özgün ileti (Kurtarılabilir Öğeler klasöründe) yinelenen iletiler olarak kabul edilebilir ve dolayısıyla bunlardan yalnızca biri dışarı aktarılabilir.
  
> [!IMPORTANT]
> Yineleme algoritmasının sınırlamaları arama sonuçlarınızı kalitesini etkiliyorsa, öğeleri dışarı aktarmada yinelemeyi etkinleştirmeniz gerekir. Bu bölümde açıklanan durumlar arama sonuçlarınızı çok sık etkileyen bir durum değil ve yineleme olasılığı en çok olan öğe sayısını azaltmak istiyorsanız, yinelemeyi de etkinleştirmeyi göz önünde bulundurabilirsiniz. 
  
## <a name="more-information"></a>Daha fazla bilgi

- Bu makaledeki bilgiler, aşağıdaki eBulma araçlarından birini kullanarak arama sonuçlarını dışarı aktaracak şekilde geçerlidir:

  - Office 365'daki uyumluluk merkezinde içerik Office 365

  - In-Place'te eBulma Exchange Online

  - SharePoint Online'da eBulma Merkezi

- Arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz:

  - [İçerik Arama Dışarı Aktarma](export-search-results.md)

  - [İçerik Arama raporunu dışarı aktarma](export-a-content-search-report.md)

  - [eK In-Place arama sonuçlarını bir PST dosyasına aktarma](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)

  - [eBulma Merkezi'nde içeriği dışarı aktarma ve rapor oluşturma](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
