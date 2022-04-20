---
title: Microsoft Purview genişletilebilirliği
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Üçüncü taraf veri bağlayıcılarını ve Microsoft Graph API'lerini kullanarak Microsoft Purview çözümlerini genişletme hakkında bilgi edinin.
ms.openlocfilehash: e61cd2dfa8121a0925cc89fd5373569d9697936a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942765"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Microsoft Purview ve Microsoft Priva genişletilebilirliği

Microsoft Purview çözümleri kuruluşların uyumluluk risklerini akıllı bir şekilde değerlendirmesine, hassas verileri yönetmesine ve korumasına ve mevzuat gereksinimlerine etkili bir şekilde yanıt vermesine yardımcı olur. Microsoft Purview, genişletilebilirlik senaryoları açısından zengindir ve kuruluşların uyumluluk çözümlerini uyarlamasına, genişletmesine, tümleştirmesine, hızlandırmasına ve desteklemesine olanak tanır.

Uyumluluk genişletilebilirliği için iki temel yapı taşları vardır:

- **Veri bağlayıcıları**. Üçüncü taraf verilere Microsoft 365 koruma ve idare özellikleri uygulayabilmek için Microsoft dışı verileri içeri aktarmak ve arşivlemek için kullanın.

- **API'ler**. Microsoft Purview özelliklerine program aracılığıyla erişim sağlar.

## <a name="data-connectors"></a>Veri bağlayıcıları

Microsoft, Microsoft Purview uyumluluk portalında yapılandırılabilir üçüncü taraf veri bağlayıcıları sağlar. Microsoft tarafından sağlanan veri bağlayıcılarının listesi için [Üçüncü taraf veri bağlayıcıları tablosuna](archiving-third-party-data.md#third-party-data-connectors) bakın. Üçüncü taraf veri bağlayıcıları tablosu, verileri Microsoft 365 içeri aktarıp arşivledikten sonra üçüncü taraf verilerine uygulayabileceğiniz uyumluluk çözümlerini ve her bağlayıcı için adım adım yönergelerin bağlantılarını da özetler.

Microsoft 365 veri bağlayıcıları hakkında daha fazla bilgi edinmek için bkz. [Üçüncü taraf verileri arşivleme](archiving-third-party-data.md). Uyumluluk portalında bulunan veri bağlayıcıları üçüncü taraf veri türü desteklenmiyorsa, size özel bağlayıcı sağlayabilen bir iş ortağıyla çalışabilirsiniz. Birlikte çalışabileceğiniz iş ortaklarının listesi ve bu yöntemin adım adım işlemi için bkz. [Üçüncü taraf verilerini arşivlemek için bir iş ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Veri bağlayıcıları için önkoşullar

Üçüncü taraf verileri içeri aktarmak ve arşivlemek için uyumluluk portalında kullanılabilen veri bağlayıcılarının çoğu, yapılandırma görevlerini üçüncü taraf veri kaynağında hazırlamanızı ve gerçekleştirmenizi gerektirir. Bu önkoşullar, her üçüncü taraf veri bağlayıcısı için ayrıntılı olarak belgelenmiştir.

Microsoft'un iş ortaklarından biri tarafından sağlanan uyumluluk portalındaki veri bağlayıcıları için, bağlayıcı dağıtabilmeniz için önce kuruluşunuzun iş ortağıyla bir iş ilişkisine sahip olması gerekir.

Üçüncü taraf veri bağlayıcıları için yönergeler ve gereksinimler için [güvenlik & uyumluluğu için Microsoft 365 kılavuzun "Veri bağlayıcıları" bölümüne bakın - Hizmet Açıklamaları | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>Apı 'leri

Microsoft Purview ve Microsoft Priva API'leri Microsoft Bilgi Koruması SDK, Microsoft Graph API ve Office 365 Yönetim Etkinliği API'sinde kullanılabilir. Bazı uyumluluk API'leri, Microsoft 365 müşterileri, bağımsız yazılım satıcıları, sistem tümleştiricileri ve yönetilen güvenlik hizmeti sağlayıcıları için geliştiricilerin yüksek değerli güvenlik ve uyumluluk çözümleri oluşturmasını sağlayan yeni bir güvenlik ve uyumluluk API'leri kümesinin parçasıdır.

Graph API'lere erişme hakkında daha fazla bilgi edinmek için bkz. [Microsoft Graph genel bakış](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Konu hakları istekleri için Microsoft Graph API'leri

Dünyanın dört bir yanındaki belirli gizlilik düzenlemelerine uygun olarak, bireyler şirketlerin kendileriyle ilgili olarak topladığı kişisel verileri gözden geçirmek veya yönetmek için istekte bulunabilir. Bu istekler, Microsoft Priva Konu Hakları *İstekleri çözümünde konu hakları istekleri* olarak adlandırılır. Konu hakları istekleri, *veri sahibi istekleri* (DSR) veya *veri sahibi erişim istekleri* (DSAR) olarak da adlandırılır. Konu hakları isteklerine yönelik Microsoft Graph API'leri, geliştiricilerin Microsoft 365 ilgili konu hakları isteklerini daha geniş bir gizlilik ekosistemiyle tümleştirmesine olanak tanır. Bu API tabanlı genişletilebilirlik, kuruluşların hem Microsoft hem de Microsoft dışı ortamları kapsayan veri varlıklarının tamamında konu hakları isteklerine birleşik bir şekilde yanıt vermelerini sağlar. Bu özellik, büyük ölçekte otomasyona da yardımcı olur ve kuruluşların el ile gerçekleştirilen süreçlere bağlı kalmadan sektör düzenlemelerini daha verimli bir şekilde karşılamalarına yardımcı olur.

Daha fazla bilgi edinmek için bkz. [Konu hakları isteği için Microsoft Graph API'leri](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Bilgi Koruması (MIP) SDK

MIP SDK, Microsoft 365 güvenlik ve uyumluluk merkezlerinden üçüncü taraf uygulama ve hizmetlere etiketleme ve koruma hizmetlerini kullanıma sunar. Geliştiriciler, dosyalara etiket ve koruma uygulamak için yerel destek oluşturmak için SDK'yı kullanabilir. Geliştiriciler, belirli etiketler algılandığında hangi eylemlerin gerçekleştirileceğini ve MIP ile şifrelenmiş bilgilerin nedenini belirleyebilir.

Üst düzey MIP SDK kullanım örnekleri şunlardır:

- Dışarı aktarma işlemindeki dosyalara sınıflandırma etiketleri uygulayan bir iş kolu uygulaması.

- Duyarlılık etiketleri için yerel destek sağlayan bir CAD/CAM tasarım uygulaması.

- Azure Information Protection ile verileri şifreleyebilen bir bulut erişim güvenlik aracısı veya veri kaybı önleme çözümü.

MIP SDK'sı, önkoşullar, ek senaryolar ve örnekler hakkında daha fazla bilgi edinmek için bkz. [MIP SDK'sına Genel Bakış](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Teams DLP için Microsoft Graph API

[Veri kaybı önleme (DLP)](dlp-microsoft-teams.md) özellikleri, özellikle kuruluşlar uzaktan çalışmaya geçiş yapmışken Microsoft Teams yaygın olarak kullanılır. Kısa süre önce Teams'daki iletiler için Microsoft Graph Değişiklik Bildirimi API'sinin [genel kullanıma sunulduğu duyuruldu](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/). Bu API, geliştiricilerin Microsoft Teams iletileri neredeyse gerçek zamanlı olarak dinleyebilen uygulamalar oluşturmasına ve ardından hem müşteriler hem de iş ortakları için DLP senaryoları uygulamasına olanak tanır. Ayrıca Microsoft Graph Patch API'si, Teams iletilere DLP eylemleri uygulamanıza olanak tanır.

Bu iki API, Teams DLP için Microsoft Graph API oluşturur. [Örnek uygulamayı](https://github.com/microsoftgraph/aspnetcore-webhooks-sample) deneyerek çalışmaya başlayabilirsiniz. Microsoft Teams mesajlaşma web kancaları hakkında daha fazla bilgi için [belgelere bakın](/graph/api/subscription-post-subscriptions).

Teams DLP için lisans gereksinimleri için bkz. [güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>eBulma için Microsoft Graph API (önizleme)

[eBulma (Premium)](overview-ediscovery-20.md) ile kuruluşlar, verileri bulunduğu yerde bulabilir ve verileri ilgili kümeye düşürmeye yönelik akıllı makine öğrenmesi ve analiz özellikleriyle uçtan uca eBulma iş akışlarını yönetebilir ve tüm bunlar Microsoft 365 güvenlik ve uyumluluk sınırı içinde kalır.

eBulma (Premium) için Graph API'leri, örnekleri oluşturmak ve yönetmek, kümeleri gözden geçirmek ve küme sorgularını ölçeklenebilir ve yinelenebilir bir şekilde gözden geçirmek için kullanılabilir. Bu, müşterilerin ve iş ortaklarının vaka oluşturma, koruyucuları ve yasal tutmaları yönetme gibi yaygın ve tekrarlanan süreçleri otomatikleştirmek için uygulamalar ve iş akışları oluşturmasına olanak tanır.

eBulma için ilk Graph API'leri genel önizlemede kullanılabilir. Takvim yılının sonuna kadar daha fazla özellik eklemeyi planlıyoruz. Bu API'ler ve eBulma (Premium) güncelleştirmeleri hakkında daha fazla bilgi edinmek için bu [bloga](https://aka.ms/Ignite2020AeDAA) bakın.

eBulma (Premium) ve API için lisans gereksinimleri için [güvenlik & uyumluluğu için lisanslama kılavuzunun Microsoft 365 "eBulma](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery)" bölümüne bakın.

### <a name="microsoft-graph-api-for-teams-export"></a>Teams Dışarı Aktarma için Microsoft Graph API

Microsoft Teams için Enterprise Bilgi Arşivleme (ÇED), mevzuat gereksinimlerini çözmelerine olanak sağladığı için müşterilerimiz için önemli bir senaryodur. müşteriler ve iş ortakları, Microsoft Teams içeriği arşivleme için yerleşik özelliklerimize ek olarak özel uygulama ve tümleştirme senaryolarını çözmek için Teams Dışarı Aktarma API'lerini de kullanabilir. Teams Dışarı Aktarma API'leri, Teams iletilerin ve ileti eklerinin toplu dışarı aktarmasını (saniyede/uygulama/kiracı başına en fazla 200 istek) destekler. Silinen iletilere, silindikten sonra 30 güne kadar API tarafından da erişilebilir. Bu Teams Dışarı Aktarma API'leri ve bunları uygulamalarınızda kullanma hakkında daha fazla bilgi için bkz. Microsoft Teams Dışarı [Aktarma API'leriyle içeriği dışarı aktarma](/microsoftteams/export-teams-content).

Teams Dışarı Aktarma API'lerinin kullanımına yönelik lisans gereksinimleri için bkz. [güvenlik & uyumluluğu için lisanslama kılavuzu Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Microsoft Graph Bağlayıcı API'leri (önizleme)

[Microsoft Graph bağlayıcıları](/microsoftsearch/connectors-overview) sayesinde kuruluşlar üçüncü taraf verileri Microsoft Arama sonuçlarda görünecek şekilde dizine alabilir. Bu özellik, Microsoft 365 üretkenlik uygulamalarınızda ve daha geniş Microsoft ekosisteminde aranabilen içerik kaynağı türlerini genişletir. Üçüncü taraf verileri şirket içinde veya genel veya özel bulutlarda barındırılabilir. eBulma (Premium) ile başlayarak bağlı Microsoft 365 uygulamaların yerleşik uyumluluk değerinin geliştirici önizlemesini etkinleştiriyoruz. Bu, kullanıcıları sorunsuz uyumluluk deneyimleri ile güçlendirmek için Microsoft 365 ekosistemiyle tümleştirilmiş uygulamalar için uyumluluk sağlar. Microsoft Graph Bağlayıcı API'lerini uygulamalar görünümünüzde birleştirme hakkında daha fazla bilgi edinmek için bkz. [Microsoft Graph bağlantıları oluşturma, güncelleştirme ve silme](/graph/connecting-external-content-connectors-api-overview).
