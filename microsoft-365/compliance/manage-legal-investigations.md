---
title: Microsoft 365 yasal araştırmalarını yönetme
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
description: Kuruluşunuzun yasal araştırmasını yönetmek için Microsoft Purview uyumluluk portalında eBulma servis taleplerini kullanın.
ms.openlocfilehash: 28dead35cce2102cfd826fa1505cdd620e4a1b25
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999795"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Microsoft 365 yasal araştırmalarını yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşlar, kuruluşunuzdaki belirli yöneticilerin veya diğer çalışanların yer aldığı bir yasal davaya yanıt vermek için birçok nedene sahiptir. Bu, kişilerin günlük iş görevlerinde kullandıkları e-posta, belgeler, anlık ileti konuşmaları ve diğer içerik konumlarındaki araştırmaya özgü bilgileri hızla bulmayı ve saklamayı içerebilir. Güvenlik ve uyumluluk merkezindeki eKeşif servis talebi araçlarını kullanarak bunları ve diğer birçok benzer etkinliği gerçekleştirebilirsiniz.
  
**Microsoft'un eBulma araştırmalarını nasıl yönettiğini öğrenmek ister misiniz?** burada, iç eBulma iş akışımızı yönetmek için aynı arama ve araştırma araçlarını nasıl kullandığımızı açıklayan [bir teknik inceleme](https://go.microsoft.com/fwlink/?linkid=852161) indirebilirsiniz.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>eBulma davalarıyla yasal incelemeleri yönetme

eBulma durumları, kuruluşunuzda eBulma servis taleplerini kimlerin oluşturabileceğini, erişebileceğini ve yönetebileceğini denetlemenize olanak sağlar. Üyeleri eklemek ve gerçekleştirebilecekleri eylem türlerini denetlemek, yasal bir olayla ilgili içerik konumlarında beklemeye almak ve servis talebinize yanıt veren içerik için beklemedeki konumlarda arama yapmak için İçerik Arama aracını kullanmak için örnekleri kullanın. Ardından, dış gözden geçirenler tarafından daha fazla araştırma için bu sonuçları dışarı aktarabilir ve indirebilirsiniz.
  
- Kuruluşunuzun gerçekleştirmesi gereken her yasal araştırma için eBulma davaları oluşturup kullanarak eBulma [iş akışınızı yönetin](./get-started-core-ediscovery.md).

- Kuruluşunuzda eBulma servis taleplerini kimlerin oluşturup yönetebileceğini denetlemek için eBulma [izinleri atayın](assign-ediscovery-permissions.md).

- eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını denetlemek için [uyumluluk sınırları ayarlayın](set-up-compliance-boundaries.md).

- Kuruluşunuzdaki [içeriği arayın](search-for-content.md).

### <a name="use-scripts-for-advanced-scenarios"></a>Gelişmiş senaryolar için betikleri kullanma

İçerik arama senaryoları için betikleri listeleyen önceki bölümde olduğu gibi, eBulma servis taleplerini yönetmenize yardımcı olmak için bazı Güvenlik & Uyumluluk Merkezi PowerShell betikleri de oluşturduk.
  
- Kuruluşunuzdaki eBulma servis talepleri ile ilişkili tüm tutmalar hakkında bilgi içeren bir eBulma [bekletme raporu oluşturun](create-a-report-on-holds-in-ediscovery-cases.md).

- eBulma ayrı tutmasına kullanıcı listesi için [posta kutuları ve OneDrive konumları ekleyin](use-a-script-to-add-users-to-a-hold-in-ediscovery.md).
  
## <a name="manage-legal-investigations-with-the-ediscovery-premium-solution-in-microsoft-365"></a>Microsoft 365'da eKeşif (Premium) çözümüyle yasal araştırmaları yönetme

Microsoft 365'deki Microsoft Purview eKeşif (Premium) çözümü, Office 365'deki mevcut eBulma ve analiz özelliklerini temel alır. *eBulma (Premium)* olarak adlandırılan bu yeni çözüm, kuruluşunuzun iç ve dış araştırmalarına yanıt veren içeriği korumak, toplamak, gözden geçirmek, analiz etmek ve dışarı aktarmak için uçtan uca bir iş akışı sağlar. Ayrıca, yasal ekiplerin bir olaya dahil olan koruyucularla iletişim kurmak için yasal tutma bildirimi iş akışının tamamını yönetmesine olanak tanır.

eBulma (Premium), Microsoft 365 veya Office 365 kuruluşunuz için bir E5 aboneliği gerektirir. Lisanslama hakkında daha fazla bilgi için bkz. [eBulma ayarlama (Premium)](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Aşağıda eBulma'daki (Premium) yerleşik iş akışına hızlı bir genel bakış verilmiştir. Daha fazla bilgi için bkz. [eBulma (Premium) iş akışını yönetme](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow).

- Başlamak için [bir servis talebi oluşturun](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case).

- [Bir](managing-custodians.md) servis talebine ekleyerek ve posta kutularına, OneDrive hesabına ve üyesi oldukları Microsoft Teams içerik üzerinde yasal bir saklama yerleştirerek koruyucuları yönetin.

- Yasal tutma bildirim sürecini otomatikleştirerek koruyucularla [iletişimleri yönetin](managing-custodian-communications.md).

- [Araştırmalarınız](processing-data-for-case.md) için verileri etkili bir şekilde toplayabilmeniz için dizin koruyucu verilerini dizine alın ve dizin oluşturma hatalarını düzeltin.

- Bir olay için [veri toplayın](collecting-data-for-ediscovery.md) ve daha fazla araştırma için [bir inceleme kümesine ekleyin](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set).

- [Gözden](view-documents-in-review-set.md) geçirme kümesindeki belgeleri, [sorgu](review-set-search.md) verilerini ve [etiket](tagging-documents.md) öğelerini görüntüleyin.

- Gelişmiş analiz araçlarıyla [olay verilerini analiz](analyzing-data-in-review-set.md) etme.

- Dış danışmana göre inceleme için [olay verilerini dışarı aktarın](exporting-data-ediscover20.md).

- eBulma'da (Premium) [uzun süre çalışan işleri yönetin](managing-jobs-ediscovery20.md).