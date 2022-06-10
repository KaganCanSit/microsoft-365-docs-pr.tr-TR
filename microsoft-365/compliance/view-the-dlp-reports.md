---
title: Veri kaybı önleme raporlarını görüntüleme
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
description: DLP ilkesi eşleşmelerinin, geçersiz kılmalarının veya hatalı pozitiflerin sayısını görüntülemek ve zaman içinde eğilimin artıp artmadığını görmek için Office 365'daki DLP raporlarını kullanın.
ms.openlocfilehash: b264a0e0b76397be99d7586ac793dac501b6672e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011642"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Veri kaybı önleme raporlarını görüntüleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview veri kaybı önleme (DLP) ilkelerinizi oluşturduktan sonra, bunların istediğiniz gibi çalıştığını ve uyumlu kalmanıza yardımcı olduğunu doğrulamanız gerekir. Microsoft Purview uyumluluk portalındaki DLP raporlarıyla şunları hızla görüntüleyebilirsiniz:

- **DLP ilkesi eşleşmeleri** Bu rapor, DLP ilkesi eşleşmelerinin zaman içindeki sayısını gösterir. Raporu tarihe, konuma, ilkeye veya eyleme göre filtreleyebilirsiniz. Bu raporu aşağıdakiler için kullanabilirsiniz:

  - DLP ilkelerinizi test modunda çalıştırırken ayarlayın veya geliştirin. İçerikle eşleşen belirli kuralı görüntüleyebilirsiniz.

  - Belirli zaman aralıklarına odaklanın ve ani artışların ve eğilimlerin nedenlerini anlayın.

  - Kuruluşunuzun DLP ilkelerini ihlal eden iş süreçlerini keşfedin.

  - İçeriğe hangi eylemlerin uygulandığını görerek DLP ilkelerinin iş üzerindeki etkisini anlayın.

  - Belirli bir DLP ilkesine yönelik eşleşmeleri göstererek uyumluluğu doğrulayın.

  - En çok kullanılan kullanıcıların listesini görüntüleyin ve kuruluşunuzdaki olaylara katkıda bulunan kullanıcıları yineleyin.

  - Kuruluşunuzdaki en önemli hassas bilgi türlerinin listesini görüntüleyin.

- **DLP olayları** Bu rapor, ilkenin raporla eşleşmesi gibi zaman içindeki ilke eşleşmelerini de gösterir. Ancak, ilke eşleşmeleri raporu kural düzeyinde eşleşmeleri gösterir; örneğin, bir e-posta üç farklı kuralla eşleşirse, ilke eşleşmeleri raporu üç farklı satır öğesi gösterir. Buna karşılık, olaylar raporu eşleşmeleri öğe düzeyinde gösterir; örneğin, bir e-posta üç farklı kuralla eşleşiyorsa, olaylar raporu söz diziminin tek satırlık bir öğesini gösterir.

  Rapor sayıları farklı toplandığından, ilke raporu eşleştirir, belirli kurallarla eşleşmeleri tanımlamak ve DLP ilkelerinin ince ayarını yapmak için daha iyidir. Olaylar raporu, DLP ilkeleriniz için sorunlu olan belirli içerik parçalarını tanımlamak için daha iyidir.

- **DLP hatalı pozitifler ve geçersiz kılmalar** DLP ilkeniz kullanıcıların bu ilkeyi geçersiz kılmasına veya hatalı pozitif rapor vermesine izin veriyorsa, bu rapor zaman içinde bu tür örneklerin sayısını gösterir. Raporu tarihe, konuma veya ilkeye göre filtreleyebilirsiniz. Bu raporu aşağıdakiler için kullanabilirsiniz:

  - Hangi ilkelerin yüksek sayıda hatalı pozitif sonuç doğuracağını görerek DLP ilkelerinizi ayarlayın veya geliştirin.

  - İlkeyi geçersiz kılarak bir ilke ipucunu çözümlediklerinde kullanıcılar tarafından gönderilen gerekçeleri görüntüleyin.

  - DLP ilkelerinin geçerli iş süreçleriyle çakıştığı yeri bulmak için çok fazla sayıda kullanıcı geçersiz kılma işlemine neden olur.

Tüm DLP raporları en son dört aylık zaman aralığındaki verileri gösterebilir. En son verilerin raporlarda görünmesi 24 saat kadar sürebilir.

Bu raporları Microsoft Purview uyumluluk portalı \> **Raporlar** \> **Panosu'nda** bulabilirsiniz.

![DLP ilkesi raporla eşleşir.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)

## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Geçersiz kılma için kullanıcı tarafından gönderilen gerekçeyi görüntüleme

DLP ilkeniz kullanıcıların bu ilkeyi geçersiz kılmasına izin veriyorsa, ilke ipucunda kullanıcılar tarafından gönderilen metni görüntülemek için hatalı pozitif ve geçersiz kılma raporunu kullanabilirsiniz.

![DLP hatalı pozitif ve geçersiz kılma raporunun ayrıntılarında yaslama alanı.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)

## <a name="take-action-on-insights-and-recommendations"></a>İçgörüler ve öneriler üzerinde eyleme geçme

Raporlar, olası sorunlarla ilgili ayrıntıları görmek ve olası düzeltme işlemleri yapmak için kırmızı uyarı simgesine tıklayabileceğiniz içgörüler ve öneriler gösterebilir.

![Bir içgörü simgesine tıklayarak yapılması gereken ayrıntıları ve eylemleri görebilirsiniz.](../media/51782036-7299-4960-8175-75c2b1637159.png)

## <a name="permissions-for-dlp-reports"></a>DLP raporları için izinler

Güvenlik & Uyumluluk Merkezi'nde DLP raporlarını görüntülemek için aşağıdakilere atanmış olmanız gerekir:

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> **Güvenlik Okuyucusu** rolü. Varsayılan olarak, bu rol Exchange yönetim merkezindeki Kuruluş Yönetimi ve Güvenlik Okuyucusu rol gruplarına atanır.

- Güvenlik & Uyumluluk Merkezi'nde **Yalnızca DLP Uyumluluk Yönetimi rolünü görüntüleyin**. Varsayılan olarak, bu rol Güvenlik & Uyumluluk Merkezi'ndeki Uyumluluk Yöneticisi, Kuruluş Yönetimi, Güvenlik Yöneticisi ve Güvenlik Okuyucusu rol gruplarına atanır.

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> **Yalnızca Alıcıları Görüntüle** rolü. Varsayılan olarak, bu rol Exchange yönetim merkezindeki Uyumluluk Yönetimi, Kuruluş Yönetimi ve View-Only Kuruluş Yönetimi rol gruplarına atanır.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>DLP raporları için cmdlet'leri bulma

DLP raporlama cmdlet'lerini kullanmak için şu adımları uygulayın:

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell)

2. Şu cmdlet'leri kullanın:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
   - [Get-DlpSiDetectionsReport](/powershell/module/exchange/get-dlpsidetectionsreport)

Ancak DLP raporlarının Exchange Online dahil olmak üzere Microsoft 365 genelinden veri çekmesi gerekir. Bu nedenle, DLP raporları için aşağıdaki cmdlet'ler Exchange Online PowerShell'de kullanılabilir. Bu DLP raporları için cmdlet'leri kullanmak için şu adımları uygulayın:

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell)

2. Şu cmdlet'leri kullanın:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-MailDetailDlpPolicyReport](/powershell/module/exchange/get-maildetaildlppolicyreport)
