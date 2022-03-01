---
title: eBulma için Gizli ve genişletilmiş dağıtım grubu alıcılarını koruma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: In-Place Saklama, Mahkeme Tutma ve Microsoft 365 bekletme ilkeleri, mevzuat uyumluluğu ve eKbulma gereksinimlerini karşılamak için posta kutusu içeriğini korumanızı sağlar.
ms.openlocfilehash: c157f2fb0b74e679bf1252b6f24208b77a657d8c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034252"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>eBulma için Gizli ve genişletilmiş dağıtım grubu alıcılarını koruma
  
Mahkeme bekletmeleri, eBulma bekletmeleri ve [Microsoft 365](./retention.md) bekletme ilkeleri (Microsoft 365 uyumluluk merkezi'de oluşturulmuş), mevzuat uyumluluğu ve eKbulma gereksinimlerini karşılamak için posta kutusu içeriğini saklamanızı sağlar. bir iletinin Gönder ve Bilgi alanlarında doğrudan adreslenen alıcılar hakkında bilgiler varsayılan olarak tüm iletilere dahil edilir. Ancak, kuruluş bir iletinin tüm alıcıları hakkında ayrıntıları arayabilme ve yeniden üretebilme yeteneğine sahip olabilir. Bu şunları içerir:
  
- **İletinin Gizli alanı kullanılarak adreslenen alıcılar:** Gizli alıcılar iletide, gönderenin posta kutusunda depolanır ancak alıcılara teslim edilen iletinin üst bilgilerine dahil değildir. 
    
- **Genişletilmiş dağıtım grubu alıcıları:** İletiyi alan alıcılar, iletinin adresli olduğu bir dağıtım grubunun üyeleri olduğundan (Kime, Bilgi veya Gizli alanlarında). 
    
Exchange Online ve Exchange Server 2013 (Toplu Güncelleştirme 7 ve sonraki sürümler) için, Gizli ve genişletilmiş dağıtım grubu alıcıları hakkında bilgiler korunur. Çalışma sayfalarında bir eBulma aracı kullanarak bu bilgileri Microsoft 365 uyumluluk merkezi. 
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Gizli alıcılar ve genişletilmiş dağıtım grubu alıcıları nasıl korunur

Daha önce de belirtildiği gibi, Gizli alıcılar hakkında bilgiler gönderenin posta kutusunda iletiyle birlikte depolanır. Bu bilgiler dizine alındı ve eBulma aramaları ve 1. 
  
Genişletilmiş dağıtım grubu alıcıları hakkında bilgiler, posta kutusunu Yerinde Tutma veya Mahkeme In-Place iletiyle birlikte depolanır. Bu Office 365, posta kutusuna bir saklama Microsoft 365 ilke uygulandığında da bu bilgiler depolanır. Dağıtım grubu üyeliği, iletinin gönderildiği sırada belirlenir. İletiyle birlikte depolanan genişletilmiş alıcılar listesi, ileti gönderildikten sonra grubun üyeliğinde yapılan değişikliklerden etkilenmez. 
  
| Bilgi: | Depolandığı yer... | Varsayılan olarak depolanıyor mu? | Erişilebilir durumda... |
|:-----|:-----|:-----|:-----|
|Son ve Bilgi alıcıları  <br/> |Gönderen ve alıcıların posta kutularında ileti özellikleri.  <br/> |Evet  <br/> |Gönderen, alıcılar ve uyumluluk yetkililerini  <br/> |
|Gizli alıcılar  <br/> |Gönderenin posta kutusunda İleti özelliği.  <br/> |Evet  <br/> |Gönderen ve uyumluluk görevlileri  <br/> |
|Genişletilmiş dağıtım grubu alıcıları  <br/> |Gönderenin posta kutusunda ileti özellikleri.  <br/> |Hayır. Genişletilmiş dağıtım grubu alıcı bilgileri, posta kutusu Bekletme veya Mahkeme In-Place veya bir saklama ilkesine atandıktan sonra Microsoft 365 depolanır.  <br/> |Uyumluluk görevlileri  <br/> |
   
## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Gizli ve genişletilmiş dağıtım grubu alıcısına gönderilen iletileri arama

Alıcıya gönderilen iletiler aranken eBulma arama sonuçları artık alıcının üyesi olduğu bir dağıtım grubuna gönderilen iletileri de içerir. Aşağıdaki tabloda, Gizli ve genişletilmiş dağıtım grubu alıcılarına gönderilen iletilerin eKbulma aramalarında döndürül olduğu senaryolar gösterir.
  
Senaryo 1: Can, en son US-Sales grubuna üyedir. Bu tabloda, Ahmet bir dağıtım grubu aracılığıyla doğrudan veya dolaylı olarak Can'a ileti gönderdiği zaman eBulma arama sonuçları gösterir.
  
| Ahmet'in posta kutusunda gönderilen iletileri arayabilirsiniz... | İleti şu şekilde gönderilir: | Sonuçlar ileti içerir mi? |
|:-----|:-----|:-----|
|To:John  <br/> |John on TO  <br/> |Evet  <br/> |
|To:John  <br/> |US-Sales tonları  <br/> |Evet  <br/> |
|To:US-Sales  <br/> |US-Sales tonları  <br/> |Evet  <br/> |
|Bilgi:Can  <br/> |Bilgide Can  <br/> |Evet  <br/> |
|Bilgi:Can  <br/> |US-Sales bilgide bilgi  <br/> |Evet  <br/> |
|Bilgi:ABD-Satış  <br/> |US-Sales bilgide bilgi  <br/> |Evet  <br/> |
   
Senaryo 2: Ahmet Can (To/Bilgi) ve Jak (Gizli) e-postalarını doğrudan veya dolaylı olarak bir dağıtım grubu aracılığıyla gönderir. Aşağıdaki tabloda eBulma arama sonuçları gösterilmiştir.
  
| Arama | Gönderilen iletiler için... | Sonuçlar ileti içerir mi? | Notlar |
|:-----|:-----|:-----|:-----|
|Ahmet'in posta kutusu  <br/> |To/Cc:John  <br/> |Evet  <br/> |Jack'in Gizli olarak ekli olduğuna dair bir gösterge sunar.  <br/> |
|Ahmet'in posta kutusu  <br/> |Gizli:Jack  <br/> |Evet  <br/> |Jack'in Gizli olarak ekli olduğuna dair bir gösterge sunar.  <br/> |
|Ahmet'in posta kutusu  <br/> |Gizli:Jack (dağıtım grubu aracılığıyla)  <br/> |Evet  <br/> |İletinin gönderildiği zaman genişletilmiş Gizli dağıtım grubunun üyeleri, eBulma arama önizlemesinde, dışarı aktarmada ve günlüklerde görünür durumdadır.  <br/> |
|John'un posta kutusu  <br/> |To/Cc:John  <br/> |Evet  <br/> |Gizli alıcıların göstergesi yok.  <br/> |
|John'un posta kutusu  <br/> |Gizli:Jack (doğrudan veya dağıtım grubu aracılığıyla)  <br/> |Hayır  <br/> |Gizli bilgiler alıcılara teslim edilen iletide depolanmaz. Gönderenin posta kutusunda aramanız gerekir.  <br/> |
|Jack'in posta kutusu  <br/> |To/Cc:John (doğrudan veya dağıtım grubu aracılığıyla)  <br/> |Evet  <br/> |Tüm alıcılara teslim edilen iletiye To/Cc bilgileri dahil edilir.  <br/> |
|Jack'in posta kutusu  <br/> |Gizli:Jack (doğrudan veya dağıtım grubu aracılığıyla)  <br/> |Hayır  <br/> |Gizli bilgiler alıcılara teslim edilen iletide depolanmaz. Gönderenin posta kutusunda aramanız gerekir.  <br/> |
   
## <a name="frequently-asked-questions"></a>Sık sorulan sorular

 **Q. Gizli alıcı bilgileri ne zaman ve nerede depolanır?**
  
C. Gizli alıcı bilgileri, gönderenin posta kutusunda özgün iletide varsayılan olarak korunur. Gizli alıcı bir dağıtım grubu ise, dağıtım grubu üyeliği yalnızca gönderenin posta kutusunun saklamada olduğu veya bir saklama ilkesine atandığı Microsoft 365 genişletilir.
  
 **Q. Genişletilmiş dağıtım grubu alıcıları listesi ne zaman ve nerede depolanır?**
  
C. Grup üyeliği, ileti gönderildiği sırada genişletilir. Genişletilmiş dağıtım grubu üyeleri listesi, gönderenin posta kutusunda özgün iletide depolanır. Gönderenin posta kutusu saklama, In-Place saklama veya bir saklama ilkesine Microsoft 365 gerekir.
  
 **Q. To/Bilgi alıcıları Gizli olarak hangi alıcıların gizli olduğunu görebilir mi?**
  
C. Hayır. Bu bilgiler ileti üst bilgilerine dahil değildir ve Gönderen/Bilgi alıcılarında görünmez. Gönderen, posta kutusunda depolanan özgün iletide depolanan Gizli alanını görebilir. Uyumluluk görevlileri, gönderenin posta kutusunu ararken bu bilgileri görebilir.
  
 **Q. Genişletilmiş dağıtım grubu alıcılarının her zaman korunmasını nasıl s alanım?**
  
C. Genişletilmiş dağıtım grubu üyelerinin her zaman bir iletiyle korunmasını sağlamak [için, Tüm](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) posta kutularını yerinde saklama veya bekletme ilkesi oluşturmak Microsoft 365 oluşturun. 
  
 **Q. Hangi grup türleri destektedir?**
  
C. Dağıtım grupları, posta etkin güvenlik grupları ve dinamik dağıtım grupları de desteklenir. 
  
 **Q. İletide genişletilmiş ve depolanan dağıtım grubu alıcılarının sayısında bir sınırlama var mı?**
  
C. Bir dağıtım grubunun en çok 10.000 üyesi korunur.
  
 **Q. İç içe dağıtım grupları destek var mı?**
  
C. Evet, iç içe dağıtım gruplarının 25 düzeyi genişletilir.
  
 **Q. Gizli ve genişletilmiş dağıtım grubu alıcı bilgileri nerede görünür?**
  
C. eBulma araması yaparken Gizli ve genişletilmiş dağıtım grubu alıcı bilgileri Uyumluluk görevlileri tarafından görülebilir. Gizli ve genişletilmiş dağıtım grubu alıcıları, Bulma posta kutusuna kopyalanan veya bir PST dosyasına ve arama sonuçlarına dahil edilen eBulma günlüğüne aktarılmış arama sonuçlarına dahil edilir. Gizli alıcı bilgileri arama önizlemesinde de kullanılabilir.
  
 **Q. Bir dağıtım grubunun üyesi kuruluşun genel adres listesinden (GAL) gizlenirse ne olur?**
  
C. Herhangi bir etkisi yoktur. Alıcılar GAL'den gizlenmişse, yine de genişletilmiş dağıtım grubunun alıcılar listesine dahil edilirler.