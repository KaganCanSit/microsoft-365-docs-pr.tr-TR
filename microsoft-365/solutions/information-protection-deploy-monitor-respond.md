---
title: Kuruluşta veri gizliliği olaylarını izleme ve yanıtlama
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Kişisel veri olaylarını izlemek ve yanıtlamak için denetim ve uyarı ilkelerini ve veri konusu isteklerini kullanın.
ms.openlocfilehash: 74efff60bb8e0ad6f170b57c86e384d3b689eee1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988581"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Kuruluşta veri gizliliği olaylarını izleme ve yanıtlama

Microsoft 365 ilgili özellikleri faaliyete ettiyken, organizasyonda veri gizliliği olaylarını izlemenize, araştırmanıza ve yanıtlamanıza yardımcı olacak yeni özelliklerden de kullanılabilir. Mevzuat gövdelerine uyumluluğu göstermek için bunların her biri için süreçler, yordamlar ve diğer belgelerin olması da önemli olabilir.

Şunlar dahildir: 

- Denetim ve uyarı ilkeleri
- Veri konusu istekleri (içerik arama ve eBulma dahil)
- Ek yatırım araçları ve raporlama

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>İzleme ve yanıt araçlarının kullanımını etkileyen veri gizliliği düzenlemeleri

Aşağıda, bilgi idaresi denetimleriyle ilgili olacak veri gizliliği düzenlemelerinin örnek bir listesi ve ve vemektedir:

- LGPD Makale 46
- LGPD Makale 48
- GDPR Makalesi (5)(1)(f)
- GDPR Makalesi (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Daha fazla bilgi için bkz [. Veri gizliliği risklerini değerlendirme ve hassas bilgileri belirleme](information-protection-deploy-assess.md).

Veri gizliliği yönetmelikleri genel olarak aşağıdakilerin izlenmesi ve yanıtını içerir:

- Kişisel verilerin depolaması, paylaşımı ve işlanmasıyla ilgili etkinlikleri denetleme, uyarı ve raporlama
- Bir veri konusu isteğini (DSR) yanıtlayabilme ve bazı durumlarda bu isteklere uyması için yatırım ve diğer idari önlemleri gerçekleştirebilme.

Ayrıca, organizasyonunız diğer uyumluluk ihtiyaçları veya iş nedenleriyle başka amaçlara yönelik izleme ve yanıt etkinlikleri gerçekleştirmek de ister. Veri gizliliği için izleme ve yanıt düzeni oluşturma, genel izleme ve yanıt planlama, uygulama ve yönetiminin bir parçası olarak yapılabilir.

Veri gizliliği düzenlemelerine uygun olarak Microsoft 365 ve yanıt düzenini düzenlemeye başlamanıza yardımcı olmak için, bu makalede Microsoft 365 gibi soruları yanıtlamak için yararlı özellikler listelemektedir: 

- Farklı veri türleri ve kaynakları için hangi tür günlük izleme, yatırım ve raporlama teknikleri vardır?
- Veri konusu isteklerini (DSR) işlemek için gerekli mekanizmalar ve anonimleştirme, yeniden işleme ve silme gibi tüm düzeltme eylemleri.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde Denetim ve Uyarı İlkeleri

Denetim, gelişmiş denetim ve uyarı ilkelerini ayarlamaya yönelik şu makalelere bakın:

- [Birleşik denetim](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Posta kutusu denetimi](../compliance/enable-mailbox-auditing.md)
- [Gelişmiş denetim](../compliance/advanced-audit.md)
- [Uyarı ilkeleri](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>GDPR ve CCPA için veri konusu istekleri

[GdpR ve CCPA için Veri](/compliance/regulatory/gdpr-dsr-Office365) Konusu İstekleri'ne bakarak Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Microsoft Stream'de silinen kullanıcıları yönetme

Microsoft Stream için, kullanıcı Azure Active Directory'den (Azure AD) silindiğinde, bu noktadan önce paylaşılan bir Stream videosuyla ilişkilendirilmişse e-posta adresi videoyla ilişkilendirilmiş olarak kalır. Kaldırmak [için bkz. Silinen kullanıcıları Microsoft Stream'den](/stream/managing-deleted-users) yönetme.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Insider risk yönetimi bir yatırım aracı olarak

[Microsoft 365'da Insider risk](../compliance/insider-risk-management.md) yönetimi, Microsoft Uyumluluk yönetim merkezinin bir özelliğidir ve organizasyonu risk altında olan etkinlikleri algılamanıza, araştırmanıza ve bu etkinliklere yönelik işlemde önlem alamanıza olanak sağlayarak dahili riski en aza indirmenize yardımcı olur.