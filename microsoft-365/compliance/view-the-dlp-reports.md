---
title: Veri kaybını önleme raporlarını görüntüleme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/7/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: DLP ilkesi eşleşmelerinin, geçersiz Office 365 veya hatalı pozitif sonuç sayısını görüntülemek ve zamanla yukarı veya aşağı eğilim olup olmadığını görmek için DLP raporlarını Office 365'de kullanın.
ms.openlocfilehash: cbf03a4d981d4b37bd22db8fa08c728b77318ddf
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018814"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Veri kaybını önleme raporlarını görüntüleme

Veri kaybı önleme (DLP) ilkelerinizi oluşturdukktan sonra, bunların istediğiniz gibi çalıştığını doğrulamak ve uyumlu kalmanıza yardımcı olmak istiyor olursunuz. Güvenlik Uyumluluk Merkezi'nde DLP raporlarıyla &amp; şunları hızla görüntüabilirsiniz:
  
- **DLP ilkesi eşleşmeleri** Bu rapor, zaman içinde DLP ilkesi eşleşmelerinin sayısını gösterir. Raporu tarihe, konuma, ilkeye veya eyleme göre filtreleebilirsiniz. Bu raporu kullanarak şunları kullanabilirsiniz: 
    
  - DLP ilkelerinizi test modunda çalıştıracak şekilde ayarlama veya geliştirme. İçerikle eşleşmeye yönelik belirli bir kuralı görüntüebilirsiniz.
    
  - Belirli zaman dönemleri üzerinde odaklanın ve depolar ile eğilimlerin nedenlerini an edin.
    
  - Kuruluş DLP ilkelerini ihlal eden iş işlemlerini keşfedin.
    
  - DLP ilkelerinin ticari etkisini anlamak için, içeriğe hangi eylemlerin uygulandığını görebilirsiniz.
    
  - Belirli bir DLP ilkesine uyumluluğu doğrulamak için, o ilkeyle ilgili eşleşmeleri gösterin.
    
  - En çok kullanan kullanıcıların listesini görüntüleme ve kuruluşunda olaylara katkıda bulunan kullanıcıları yineleme.
    
  - En önemli hassas bilgi türlerinin listesini görüntüleme.
    
- **DLP olayları** Bu raporda, ilke eşleşmeleri raporu gibi zaman içinde yapılan eşleşmeleri de gösterir. Bununla birlikte, ilke eşleşmeleri raporu kural düzeyinde eşleşmeleri gösterir; Örneğin, bir e-posta üç farklı kuralla eş kullandı ise, ilke raporu üç farklı satır öğelerini gösterir. Buna karşılık, olaylar raporu bir öğe düzeyinde eşleşmeleri gösterir; Örneğin, bir e-posta üç farklı kuralla eşlenirse, olay raporu bu içerik parçası için tek bir satır öğesi gösterir. 
    
  Rapor sayıları farklı bir araya toplanmış olduğundan, ilke raporu belirli kurallarla eşleşmeleri tanımlamak ve DLP ilkeleri içinde ince ayar yapmak için daha iyidir. Olaylar raporu, DLP ilkeleriniz için sorunlu belirli içerik parçalarını tanımlamak için daha iyidir.
    
- **DLP'de hatalı pozitif sonuçlar ve geçersiz kılmalar** DLP ilkeniz kullanıcıların bunu geçersiz kılacağına veya hatalı pozitif sonuç bildirse bile, bu raporda bu tür örneklerin zaman içinde sayısı yer almaktadır. Raporu tarihe, konuma veya ilkeye göre filtreleebilirsiniz. Bu raporu kullanarak şunları kullanabilirsiniz: 
    
  - Çok fazla sayıda hatalı pozitif sonuça neden olan ilkelere görerek DLP ilkelerinizi ayarlama veya geliştirme.
    
  - İlkeyi geçersiz karak bir ilke ipucu çözümleyene kadar kullanıcılar tarafından gönderilen gerekçeleri görüntüleme.
    
  - Çok fazla sayıda kullanıcı geçersiz kılmaya neden olarak DLP ilkelerinin geçerli iş süreçleriyle çakışması olduğunu keşfedin.
    
Tüm DLP raporları, en son dört aylık zaman dönemine göre verileri gösterebilir. En son verilerin raporlarda görünmesi 24 saat kadar sürebilir.
  
Bu raporları, Güvenlik Uyumluluk Merkezi Raporlar **Panosu'nde** \> &amp; \> **bulabilirsiniz**.
  
![DLP ilkesi raporla eşleri.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)
  
## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Kullanıcı tarafından geçersiz kılma için gönderilen gerekçeyi görüntüleme

DLP ilkeniz kullanıcıların bunu geçersiz k kullanmasını sağlarsa, ilke ipucunda kullanıcılar tarafından gönderilen metni görüntülemek için hatalı pozitif sonuç ve geçersiz kılma raporunu kullanabilirsiniz.
  
![DLP'nin hatalı pozitif ve geçersiz k olduğu ayrıntılarında gerekçelendirme alanı.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)
  
## <a name="take-action-on-insights-and-recommendations"></a>Öngörüler ve öneriler üzerinde eylemde bulun

Raporlar içgörüler ve öneriler gösterebilir; burada kırmızı uyarı simgesine tıklar ve olası sorunlar hakkında ayrıntılı bilgi edinebilirsiniz ve olası düzeltmeler yapmak için bu simgeyi tıklatın.
  
![Ayrıntıları ve gerçekleştirilen işlemleri görmek için bir içgörüler simgesine tıklayın.](../media/51782036-7299-4960-8175-75c2b1637159.png)
  
## <a name="permissions-for-dlp-reports"></a>DLP raporları için izinler

Güvenlik ve Uyumluluk Merkezi'& DLP raporlarını görüntülemek için size şu atamalar atanabilir:

- **Yönetim merkezinde** Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange rolü</a>. Varsayılan olarak bu rol, yönetim merkezinde Kuruluş Yönetimi ve Güvenlik Okuyucusu rol Exchange atanır.

- **Güvenlik ve Uyumluluk Merkezi'nde Yalnızca** Görüntülemeye & rolü. Varsayılan olarak, bu rol Güvenlik ve Uyumluluk Merkezi'nde Uyumluluk Yöneticisi, Kuruluş Yönetimi, Güvenlik Yöneticisi ve Güvenlik Okuyucusu rol & atanır.

- **Yönetim merkezinde Yalnızca** Görüntülemeli <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Alıcılar Exchange.</a> Varsayılan olarak, bu rol Uyumluluk Yönetimi, Kuruluş Yönetimi ve View-Only Yönetim Merkezi'nde Kuruluş Yönetimi rol Exchange atanır.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>DLP raporları için cmdlet'leri bulma

Güvenlik Uyumluluk Merkezi cmdlet'lerinin çoğunu kullanmak &amp; için:
  
1. [Bağlan'e &amp; Uzak PowerShell kullanılarak Uyumluluk Merkezi](/powershell/exchange/connect-to-scc-powershell)
    
2. Bu Güvenlik Uyumluluk [Merkezi &amp; cmdlet'lerini kullanın](/powershell/exchange/exchange-online-powershell)
    
Bununla birlikte, DLP raporlarının farklı verilerden, Office 365 genelinden veri Exchange Online. Bu nedenle, DLP raporları için cmdlet'ler Powershell'de Exchange Online Uyumluluk Merkezi Powershell'de &amp; kullanılamaz. Bu nedenle, DLP raporlarında cmdlet'leri kullanmak için şunları gerekir:
  
1. [Uzak PowerShell'i kullanarak Exchange Online'a bağlanma](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. DLP raporları için şu cmdlet'lerden herhangi birini kullanın:
    
      - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
    
      - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
