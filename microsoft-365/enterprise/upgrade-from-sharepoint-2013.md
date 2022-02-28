---
title: SharePoint 2013'den yükseltme
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: sharepoint-server-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: SharePoint Server 2013 ve SharePoint Foundation 2013'den yükseltme yapmak için bilgi ve kaynakları bulun. Her ikisi için de destek 11 Nisan 2023'te sona erer.
ms.openlocfilehash: 05f545b67d60d6bcc45587049e49a5f5c1f6d654
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2021
ms.locfileid: "62990619"
---
# <a name="upgrading-from-sharepoint-2013"></a>SharePoint 2013'den yükseltme

Hem Microsoft SharePoint Server 2013'te hem de SharePoint Foundation 2013'te destek **11 Nisan 2023'te sona erecek**. Bu makale, var olan SharePoint Server verilerinizi Microsoft 365'te SharePoint Online'a geçirmenize veya şirket içi SharePoint 2013 ortamınızı yükseltmenize yardımcı olacak kaynaklar sağlar. Bu makalenin kalan bölümü için, SharePoint 2013'ü hem SharePoint Server 2013'e hem de SharePoint Foundation 2013'e başvurmak için kullan kullan aynı şekildedir.

## <a name="what-is-end-of-support"></a>Destek *sonu nedir*?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Destek sonu tarihini tamamlanın, ürün çalışmayı durdurmaz, ancak Microsoft artık şunları sağlar:

- Ortaya çıkabilir sorunlar için teknik destek.

- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.

- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Bu, ürün için başka güncelleştirme, yama veya düzeltme (güvenlik yamaları/düzeltmeleri de dahil) olmayacaktır. Microsoft Desteği, destek çalışmalarını tümüyle daha yeni sürümlere kaydıracak.

> [!NOTE]
> Yazılım yaşam döngüsü normalde ilk sürümden gelen temel destek beş yıl devam eder ve potansiyel olarak 5 yıla kadar uzatılmış destek daha uzun olur. [Microsoft çözüm sağlayıcıları](https://go.microsoft.com/fwlink/?linkid=841249) yazılımın sonraki sürümüne yükseltmenizi veya her ikisini birden (veya birden) Microsoft 365 yardımcı olabilir. Kritik temel teknolojiler için, özellikle de Microsoft SQL Server ile birlikte kullanmakta olduğunuz teknolojilerin destek sonu tarihlerini bildiğinizden emin SharePoint. Daha fazla bilgi için bkz. [Sabit Yaşam Döngüsü İlkesi](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Devam et'i planla

[SharePoint Server 2013](/lifecycle/products/sharepoint-server-2013) ve [SharePoint Foundation 2013 için Ürün Yaşam Döngüsü sitesinde destek SharePoint tarihleri kontrol edin](/lifecycle/products/sharepoint-foundation-2013). Yükseltmelerinizi veya geçişlerinizi bu tarihleri unutmayın. Ürününüz listelenen *tarihte çalışmayı durdurmayacak* . Ancak, yükleme işleminize bu tarihten sonra yama olmayacak olması nedeniyle ürünün sonraki sürümüne sorunsuz bir geçiş planlamak istemeniz gerekir. Aşağıdaki tabloda sizin için kullanılabilir seçenekler listelenmiştir.

|Destek ürünü sonu|İyi|Daha iyi|En iyi|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|SharePoint Server 2016 veya 2019'a yükseltme|SharePoint Server Subscription Edition'a yükseltme|SharePoint'de Microsoft 365'e Microsoft 365

## <a name="whats-next"></a>Sırada ne var?

Microsoft 365'daki en SharePoint, zeka ve güvenlik çözümlerinden yararlanmak için Microsoft 365'te diğer iş birliği ve Microsoft 365. Özelliklere sahip modern Microsoft 365 çekici, esnek ve performansa uygun şekilde tasarlanmıştır.

Şirket içi SharePoint dağıtımına devam etmek zorundaysanız, Microsoft 365'te kullanmak için mümkün olduğu kadar fazla SharePoint işlevini geçirmenizi sağlayacak SharePoint bir dağıtım öneririz. Karma [SharePoint hakkında](/sharepoint/hybrid/hybrid) bilgi edinmek ve planlamak için bkz. Karma uygulama.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>SharePoint'de Microsoft 365'e Microsoft 365

SharePoint Geçiş Aracı'nı (SPMT) kullanarak, sitelerinizi ve içeriğinizi başka bir SharePoint Microsoft 365. Kapsamlı bir içerik kitaplığımız var ve bu kitaplık, ön planda planlamanıza, geçiş işlemini gerçekleştirmenize ve karşınıza gelebilir tüm sorunları gidermenize yardımcı olabilir. [Geçiş Aracı'SharePoint genel bakış](/sharepointmigration/introducing-the-sharepoint-migration-tool) iyi bir başlangıçtır.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>SharePoint Server Subscription Edition'a yükseltme

SharePoint 2013'den Subscription Edition'a doğrudan yükseltecek yol olmasına rağmen, bu yine de ikinci en iyi seçenektir. Bunun birincil nedeni, SharePoint Server Subscription Edition'ın, ileriye doğru SharePoint Server'ın yeni ana sürümlerini sürüme ihtiyacı ortadan kaldıran bir sürekli güncelleştirme modeli tanıtmaktır.

Subscription Edition'a yükseltmek için, SharePoint Server 2016 veya 2019'i çalıştırmanız gerekir. ayrıca SharePoint 2013 ile 2019 arasında doğrudan yol da SharePoint, sizin için en iyi seçenek önce 2016'ya yükseltmek ve sonra da Subscription Edition'a yükseltmektir. Subscription Edition yükseltmeniz hakkında daha fazla bilgi edinmek ve bu sürümü planlamak için aşağıdaki bağlantılara bakın:

- [SharePoint Server 2016'ya yükseltme](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [SharePoint Server Subscription Edition'a yükseltme](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

Şirket içi SharePoint dağıtımını sürdürmeniz gerekse bile, SharePoint'te modern işbirliği deneyimlerinden, güvenlik ve uyumluluk özelliklerinden yararlanmaya başlamak için sitelerinizi veya içeriğinizin bölümlerini [Microsoft 365'e](/sharepoint/hybrid/hybrid) geçirmenizi Microsoft 365 öneririz.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>SharePoint Server 2016 veya 2019'a yükseltme

Şirket içi SharePoint 2013 desteği sona erer ve dağıtımınızı sürdürmeyi planlıyorsanız, SharePoint Server 2016 ve 2019 SharePoint platformlar da desteklenen platformlardır. Ancak her **iki sürüm de 14 Temmuz 2026'da destek sonuna ulaşacak**. Başka bir ifadeyle, 2013 destek tarihini sona erdikten sonra 3 yıl içinde başka bir yükseltme planlamanız gerekir. Her iki ürün için de destek yaşam döngüsü sayfaları:

- [SharePoint Server 2016 destek yaşam döngüsü tarihleri](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 yaşam döngüsü tarihlerini öğrenin](/lifecycle/products/sharepoint-server-2019)

Daha fazla bilgi edinmek ve yükseltmenizi planlamak için aşağıdaki makalelere bakın:

- [SharePoint Server 2016'ya yükseltme](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Yükseltme SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

Şirket içi SharePoint dağıtımını sürdürmeniz gerekse bile, SharePoint'te modern işbirliği deneyimlerinden, güvenlik ve uyumluluk özelliklerinden yararlanmaya başlamak için sitelerinizi veya içeriğinizin bölümlerini [Microsoft 365'e](/sharepoint/hybrid/hybrid) geçirmenizi Microsoft 365 öneririz.  
