---
title: Web'de yasal Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: eBulma olaylarını, Microsoft 365 uyumluluk merkezi araştırmalarını yönetmek için eBulma olaylarını kullanın.
ms.openlocfilehash: fc4e89645ef1912c33ab89ec190c87dc9c8a8965
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985167"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Web'de yasal Microsoft 365

Kuruluşların, belirli yöneticilerin veya kuruluş dahili diğer çalışanların katıldığı bir davaya yanıt vermek için birçok nedeni vardır. Bu, kişiler tarafından günlük iş görevlerinde kullanılan e-postada, belgelerde, anlık ileti konuşmalarında ve diğer içerik konumlarında bulunan daha fazla soruşturmaya özgü bilgiyi hızla bulmayı ve korumayı da içeriyor olabilir. Güvenlik ve uyumluluk merkezinde eBulma olay araçları kullanarak bu ve benzer birçok etkinlik gerçekleştirebilirsiniz.
  
**Microsoft'un eBulma soruşturmalarını nasıl yöneteceklerini mi bilmek istiyor musunuz?** Burada, şirket [içi eKbulma](https://go.microsoft.com/fwlink/?linkid=852161) iş akışımızı yönetmek için aynı arama ve soruşturma araçlarını nasıl kullanabileceğimizi açıklayan teknik bir teknik inceleme ve belgemizi indirebilirsiniz.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>eBulma davaları ile yasal soruşturmaları yönetme

eBulma servis servis servis adayları, organizasyonda eBulma olaylarını kimlerin oluşturay, kimlere erişil erişeni ve yönetileni denetlemenizi sağlar. Üyeleri eklemek ve gerçekleştirecekleri işlem türlerini kontrol etmek için vakaları kullanın, bir davayla ilgili içerik konumlarına yerinde bekleyin ve davanıza yanıt olarak hazır olacak içerik için yerinde arama yapmak için İçerik Arama aracını kullanın. Böylece, dış gözden geçirenler tarafından daha fazla araştırma için bu sonuçları dışarı aktararak indirebilirsiniz.
  
- [eBulma iş akışınızı yönetmek için](./get-started-core-ediscovery.md) , kurumuz tarafından yapılması gereken her yasal soruşturma için eBulma davaları oluşturma ve kullanma.

- [Organizasyonda eBulma servis](assign-ediscovery-permissions.md) durumlarını kimlerin oluşturayanı ve yönetileni kontrol etmek için eBulma izinleri attayabilirsiniz.

- [eBulma yöneticilerinin](set-up-compliance-boundaries.md) arayabilirsiniz kullanıcı içerik konumlarını kontrol etmek için uyumluluk sınırlarını ayarlayın.

- [İçeriğinizi](search-for-content.md) kuruluş içinde arama.

### <a name="use-scripts-for-advanced-scenarios"></a>Gelişmiş senaryolar için betik kullanma

İçerik arama senaryolarıyla ilgili betiklerin listelenmiş olduğu önceki bölümde olduğu gibi, eBulma olaylarını yönetmenize yardımcı olmak için bazı Güvenlik & ve Uyumluluk Merkezi PowerShell betikleri oluşturduk.
  
- [Kuruluşta eBulma davaları](create-a-report-on-holds-in-ediscovery-cases.md) ile ilişkilendirilmiş tüm tutmalarla ilgili bilgileri içeren bir eBulma tutma raporu oluşturun.

- [eBulma tutma OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) posta kutuları ve posta kutuları ekleme ve kullanıcı listesi için konum ekleme.
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>Microsoft 365'de en son Advanced eDiscovery ile yasal Microsoft 365

Bu Advanced eDiscovery çözüm Microsoft 365, çalışma sayfalarındaki mevcut eKbulma ve çözümleme özelliklerini Office 365. *Advanced eDiscovery* adlı bu yeni çözüm, kuruluşun iç ve dış araştırmalarına yanıt veren içerikleri korumak, toplamak, gözden geçirmek, çözümlemek ve dışarı aktarmaya yönelik uç-uç iş akışı sağlar. Ayrıca, hukuk ekiplerinin bir olaya dahil olan koruyucularla iletişim kurmak için yasal tutma bildirimi iş akışının tamamını yönetmesini sağlar.

Advanced eDiscovery e-postanız için E5 aboneliği Microsoft 365 veya Office 365 gerekir. Lisanslama hakkında daha fazla bilgi için bkz. [Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Burada, iş akışında yerleşik iş akışına hızlı bir genel Advanced eDiscovery. Daha fazla bilgi için bkz[. İş Advanced eDiscovery yönetme](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow).

- [Bir vaka oluşturun](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) .

- [Koruyucuları bir](managing-custodians.md) vakaya ekp posta kutularına içerik bulundurarak, OneDrive hesabını yasal olarak tutarken Microsoft Teams üyesi olduklarını belirterek yönetin.

- [Yasal tutma](managing-custodian-communications.md) bildirim sürecini otomatik olarak yapılandırarak koruyucularla iletişimi yönetin.

- [Araştırmanız için etkili](processing-data-for-case.md) bir şekilde veri toplayabilirsiniz, dizin koruyucu verileri ve dizin oluşturma hatalarını düzeltin.

- [Olayla](collecting-data-for-ediscovery.md) ilgili verileri toplayın ve daha [fazla araştırma yapmak için gözden geçirme](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) kümesine ekleyin.

- [Gözden](view-documents-in-review-set.md) geçirme [kümesinde](review-set-search.md) belgeleri, sorgu [verilerini](tagging-documents.md) ve etiket öğelerini görüntüleme.

- [Gelişmiş analiz araçlarıyla](analyzing-data-in-review-set.md) örnek olay verilerini çözümlenin.

- [Dava verilerini, dava danışmanının](exporting-data-ediscover20.md) incelemesi için dışarı aktarın.

- [İş yerlerinde uzun süreli](managing-jobs-ediscovery20.md) Advanced eDiscovery.