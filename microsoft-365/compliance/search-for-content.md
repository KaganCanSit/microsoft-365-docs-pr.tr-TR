---
title: İçerik arama
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
description: Exchange posta kutularına, SharePoint sitelerinde ve OneDrive konumlarında bulunan belgelere ve Skype Kurumsal'te anlık ileti konuşmalarına hızla e-posta bulmak için Microsoft 365 uyumluluk merkezi'te İçerik arama eBulma aracını kullanın.
ms.openlocfilehash: 21e07f09c21bbf0196b6ba113b82ec3030aada32
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028424"
---
# <a name="search-for-content-using-the-content-search-tool"></a>İçerik arama aracını kullanarak içerik arama

Microsoft 365 uyumluluk merkezi posta kutularında, SharePoint sitelerinde ve Exchange OneDrive konumlarında e-postayı, Skype Kurumsal'te anlık ileti konuşmalarını hızlı bir şekilde bulmak için Skype Kurumsal. İçerik arama aracını kullanarak, Grup Sohbetleri ve Grupları Birleştirme gibi işbirliği araçlarında e-postaları, belgeleri ve anlık Microsoft Teams Microsoft 365 kullanabilirsiniz.
  
## <a name="search-for-content"></a>İçerik arama

İlk adım, İçerik arama aracını kullanarak arama yapmak üzere içerik konumları seçmek ve anahtar sözcük sorgusunu belirli öğeleri aramak üzere yapılandırmaktır. Ya da sorguyu boş bırakarak hedef konumlarda yer alan tüm öğeleri geri getirebilirsiniz.
  
- [İçerik araması](content-search.md) oluşturma ve çalıştırma

- [Aramanızı daraltmak için arama sorguları](keyword-queries-and-search-conditions.md) oluşturma ve koşulları kullanma

- [İçerik arama](content-search-reference.md) için özellik başvurusu

- [eBulma yöneticisinin yalnızca](permissions-filtering-for-content-search.md) kuruluşta yer alan posta kutularının veya sitelerin alt kümesinde arama yapılayacak şekilde arama izinleri filtrelemeyi yapılandırma

- [Microsoft 365'da bulut](search-cloud-based-mailboxes-for-on-premises-users.md) tabanlı posta kutularında şirket içi kullanıcıları Microsoft 365

- [Arama sonuçlarının anahtar](view-keyword-statistics-for-content-search.md) sözcük istatistiklerini görüntüleme ve gerekirse sorguyu geliştirme

- [Kuruluş tarafından başka bir kuruluşa](use-content-search-to-search-third-party-data-that-was-imported.md) aktarılmış üçüncü taraf verilerini Microsoft 365

- [Gizli alıcıları koruyarak](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) onları arama

## <a name="perform-actions-on-content-you-find"></a>Bu içerik üzerinde eylem gerçekleştirme

Bir arama çalıştırdikten ve gereken şekilde daralt olduktan sonra, bir sonraki adım arama tarafından döndürülen sonuçlarla bir şeyler yapmaktır. Sonuçları yerel bilgisayarınıza aktararak indirebilir veya bir e-posta saldırısı durumunda kullanıcı posta kutularından aramanın sonuçlarını silebilirsiniz.
  
- [İçerik aramanın sonuçlarını dışarı aktarma](export-search-results.md) ve bunları yerel bilgisayarınıza indirme

- [Virüs, tehlikeli ekler veya](search-for-and-delete-messages-in-your-organization.md) kimlik avı iletileri gibi e-posta iletilerini arama ve silme

- [Gerçek sonuçları dışarı](export-a-content-search-report.md) aktarmadan içerik arama sonuçlarının raporunu dışarı aktarma

## <a name="learn-more-about-content-search"></a>İçerik arama hakkında daha fazla bilgi

İçerik arama kolayca kullanılabilir, ancak aynı zamanda güçlü bir araçtır. Sahne arkası, çok fazla iş var. Bu konuda ne kadar fazla bilgi edinlir ve davranışını ve sınırlamalarını ne kadar iyi anlarsanız, arama ve soruşturma ihtiyaçlarını o kadar başarılı bir şekilde kullanabilirsiniz. Bilgi:
  
- [Bir defada](limits-for-content-search.md) çalıştırabilirsiniz arama sayısı üst sınırı ve tek bir aramada dahil etmek istediğiniz en fazla içerik konumu gibi içerik arama sınırları

- [Arama sonuçlarını dışarı ve indirirken](differences-between-estimated-and-actual-ediscovery-search-results.md) tahmin edilen ve gerçek arama sonuçları ile bu sonuçlar arasında farklılık olabilir

- [Arama sonuçlarını dışarı ve indirirken Exchange SharePoint](partially-indexed-items-in-content-search.md) ve bunları dahil etmek veya dışarıda tutmak için dizine alan kısmen dizine alındı

- [Kısmen dizine alan öğeleri](investigating-partially-indexed-items-in-ediscovery.md) araştırma ve onlara maruz kalma sürenizi belirleme

- [Aramanın sonuçları olan e-posta](de-duplication-in-ediscovery-search-results.md) iletilerini dışarı aktarsanız da etkinleştirebilirsiniz, arama sonuçlarında yinelemeyi geri alın

## <a name="use-scripts-for-advanced-scenarios"></a>Gelişmiş senaryolar için betik kullanma

Bazen daha gelişmiş, karmaşık ve yinelenen içerik arama görevlerini gerçekleştirmeniz gerekir. Böyle durumlarda, Güvenlik ve Uyumluluk Merkezi PowerShell'de komutları kullanmak & ve daha hızlı olur. Bunu kolaylaştıracak şekilde, içerik aramayla ilgili karmaşık görevleri tamamlamanıza yardımcı & Güvenlik Merkezi PowerShell betikleri oluşturduk.

- [Bir vakaya yanıt veren](use-content-search-for-targeted-collections.md) öğelerin bu klasörde yer geldiğinden emin olarak, belirli posta kutusu ve site klasörlerini (hedefli koleksiyon olarak adlandırılan) arama 

- [Posta kutusunda arama OneDrive kullanıcı](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) listesi arama

- [Arama verilerini hızlı ve verimli bir şekilde tanımlamak](create-report-on-and-delete-multiple-content-searches.md) ve kullanmak için birden çok arama oluşturma, rapor oluşturma ve silme

- [İçerik aramalarını klonlar](clone-a-content-search.md) ve aynı içerik konumlarında çalıştırlanan farklı anahtar sözcük arama sorgularının sonuçlarını hızlı bir şekilde karşılaştırın; veya betiği kullanarak yeni arama 3-4
