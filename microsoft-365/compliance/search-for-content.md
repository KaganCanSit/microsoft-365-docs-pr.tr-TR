---
title: İçerik için arama yapma
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
description: Exchange posta kutularında e-postayı, SharePoint sitelerdeki ve OneDrive konumlarındaki belgeleri ve Skype Kurumsal'deki anlık ileti konuşmalarını hızla bulmak için Microsoft Purview uyumluluk portalındaki İçerik arama eBulma aracını kullanın.
ms.openlocfilehash: b339d2f4ebe738407c42eda86f18a5167af03921
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941951"
---
# <a name="search-for-content-using-the-content-search-tool"></a>İçerik arama aracını kullanarak içerik arama

Exchange posta kutularında e-postayı, SharePoint sitelerdeki ve OneDrive konumlardaki belgeleri ve Skype Kurumsal anlık ileti konuşmalarını hızla bulmak için Microsoft Purview uyumluluk portalındaki İçerik arama aracını kullanın. Microsoft Teams ve Microsoft 365 Grupları gibi işbirliği araçlarında e-posta, belge ve anlık ileti konuşmalarını aramak için içerik arama aracını kullanabilirsiniz.
  
## <a name="search-for-content"></a>İçerik için arama yapma

İlk adım, arama yapılacak içerik konumlarını seçmek için İçerik arama aracını kullanmaya başlamak ve belirli öğeleri aramak için bir anahtar sözcük sorgusu yapılandırmaktır. Ya da sorguyu boş bırakıp hedef konumlardaki tüm öğeleri döndürebilirsiniz.
  
- İçerik araması [oluşturma ve çalıştırma](content-search.md)

- [Arama sorgularını oluşturma ve](keyword-queries-and-search-conditions.md) aramanızı daraltmak için koşulları kullanma

- İçerik araması için [özellik başvurusu](content-search-reference.md)

- EBulma yöneticisinin kuruluşunuzdaki posta kutularının veya sitelerin yalnızca alt kümesini aramasını sağlayan [arama izinleri filtrelemesini yapılandırın](permissions-filtering-for-content-search.md)

- Microsoft 365'da şirket içi kullanıcılar için [bulut tabanlı posta kutularında arama](search-cloud-based-mailboxes-for-on-premises-users.md)

- Arama sonuçlarının [anahtar sözcük istatistiklerini görüntüleyin](view-keyword-statistics-for-content-search.md) ve gerekirse sorguyu daraltın

- Kuruluşunuzun Microsoft 365 aktardığı [üçüncü taraf verilerini arama](use-content-search-to-search-third-party-data-that-was-imported.md)

- [Gizli alıcıları](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) aramanız için koruyun

## <a name="perform-actions-on-content-you-find"></a>Bulduğunuz içerik üzerinde eylemler gerçekleştirme

Bir aramayı çalıştırdıktan ve gerektiği gibi daraltdıktan sonra, sonraki adım arama tarafından döndürülen sonuçlarla bir şeyler yapmaktır. Sonuçları yerel bilgisayarınıza aktarabilir ve indirebilirsiniz veya kuruluşunuza yönelik bir e-posta saldırısı söz konusu olduğunda, kullanıcı posta kutularından arama sonuçlarını silebilirsiniz.
  
- [İçerik aramasının sonuçlarını dışarı aktarma](export-search-results.md) ve bunları yerel bilgisayarınıza indirme

- Virüs içeren iletiler, tehlikeli ekler veya kimlik avı [iletileri gibi e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md)

- İçerik aramasının sonuçlarıyla ilgili [raporu](export-a-content-search-report.md) gerçek sonuçları dışarı aktarmadan dışarı aktarma

## <a name="learn-more-about-content-search"></a>İçerik arama hakkında daha fazla bilgi edinin

İçerik aramanın kullanımı kolaydır, ancak aynı zamanda güçlü bir araçtır. Sahne arkası, çok şey oluyor. Ne kadar çok bilgi edinip davranışını ve sınırlamalarını anlarsanız, kuruluşunuzun arama ve araştırma gereksinimleri için o kadar başarılı olursunuz. Şu konularda bilgi edinin:
  
- [bir](limits-for-content-search.md) kerede çalıştırabileceğiniz arama sayısı üst sınırı ve tek bir aramaya ekleyebileceğiniz en fazla içerik konumu sayısı gibi içerik arama sınırları

- [Tahmini ve gerçek arama sonuçları ile arama sonuçlarını](differences-between-estimated-and-actual-ediscovery-search-results.md) dışarı aktarıp indirdiğinizde aralarında farklılıklar olmasının nedenleri

- [Exchange ve SharePoint kısmen dizinlenmiş öğeler](partially-indexed-items-in-content-search.md) ve arama sonuçlarını dışarı aktarıp indirirken bunları dahil etme veya dışlama

- [Kısmen dizine alınan öğeleri araştırma](investigating-partially-indexed-items-in-ediscovery.md) ve kuruluşunuzun bunlara maruz kalmasını belirleme

- [Arama sonuçları olan e-posta](de-duplication-in-ediscovery-search-results.md) iletilerini dışarı aktarırken etkinleştirebileceğiniz arama sonuçlarında yinelenenleri kaldırma

## <a name="use-scripts-for-advanced-scenarios"></a>Gelişmiş senaryolar için betikleri kullanma

Bazen daha gelişmiş, karmaşık ve yinelenen içerik arama görevleri gerçekleştirmeniz gerekir. Bu gibi durumlarda, Güvenlik & Uyumluluk Merkezi PowerShell'de komutları kullanmak daha kolay ve daha hızlıdır. Bunu kolaylaştırmaya yardımcı olmak için, içerik aramayla ilgili karmaşık görevleri tamamlamanıza yardımcı olacak bir dizi Güvenlik & Uyumluluk Merkezi PowerShell betikleri oluşturduk.

- Bir servis talebine yanıt veren öğelerin söz konusu klasörde bulunduğundan emin olduğunuzda [belirli posta kutusu ve site klasörlerinde](use-content-search-for-targeted-collections.md) (*hedeflenen* koleksiyon olarak adlandırılır) arama yapın

- Kullanıcı listesi için [posta kutusunda ve OneDrive konumunda arama](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md)

- Arama verilerini hızlı ve verimli bir şekilde tanımlamak [ve silmek için birden çok arama oluşturma, raporlama ve silme](create-report-on-and-delete-multiple-content-searches.md)

- [bir içerik aramasını kopyalayıp aynı içerik](clone-a-content-search.md) konumlarında çalıştırılacak farklı anahtar sözcük arama sorgularının sonuçlarını hızla karşılaştırın; veya yeni arama oluştururken çok sayıda içerik konumunu yeniden girmek zorunda kalmadan zaman kazanmak için betiği kullanın
