---
title: Microsoft 365 uyumluluğu genişletilebilirliği
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
description: Üçüncü taraf veri bağlayıcıları ve Microsoft Microsoft 365 API'leri kullanarak uyumluluk çözümlerini genişletmeyi Graph öğrenin.
ms.openlocfilehash: 1127064394e5b4873adb046e2b0540b361064c9d
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019529"
---
# <a name="microsoft-365-compliance-and-microsoft-priva-extensibility"></a>Microsoft 365 Uyumluluğu ve Microsoft Priva genişletilebilirliği

Microsoft 365 çözümlerini kontrol etmek, kuruluşların uyumluluk risklerini akıllı bir şekilde değerlendirmesine, hassas verileri yönetmelerine ve korumalarına ve mevzuat gereksinimlerine etkin bir şekilde yanıt vermelerine yardımcı olur. Microsoft 365 uyumluluk, zengin genişletilebilirlik senaryolarıdır ve kuruluşların uyumluluk çözümlerini uyarlamalarına, genişletmelerine, tümleştirlerine, hızlandırmalarına ve desteklemelerine olanak sağlar.

Uyumluluk genişletilebilirliği için iki önemli yapı bloğu vardır:

- **Veri bağlayıcıları**. Microsoft'a bağlı olmayan verileri içeri aktarmayı ve arşivlemeyi kullanarak, Microsoft 365 taraf verilerine koruma ve yönetim özelliklerini uygulayabilirsiniz.

- **API'ler**. Uyumluluk özelliklerine programlı Microsoft 365 olanak sağlar.

## <a name="data-connectors"></a>Veri bağlayıcıları

Microsoft, web sitesinde yapılandırılan üçüncü taraf veri bağlayıcıları Microsoft 365 uyumluluk merkezi. Microsoft tarafından sağlanan veri bağlayıcılarının listesi için bkz. [Üçüncü taraf veri bağlayıcıları](archiving-third-party-data.md#third-party-data-connectors) tablosu. Üçüncü taraf veri bağlayıcıları tablosunda ayrıca, Microsoft 365'ta verileri içeri aktardıktan ve arşivledikten sonra üçüncü taraf verilerine uygulayabilecek uyumluluk çözümleri ve her bağlayıcının adım adım yönergelerinin bağlantıları da özetlenir.

Veri bağlayıcılarını arşivleme hakkında Microsoft 365 için bkz[. Üçüncü taraf verilerini arşivleme](archiving-third-party-data.md). Üçüncü taraf bir veri türü Microsoft 365 uyumluluk merkezi bağlayıcıları tarafından desteklenmiyorsa, size özel bir bağlayıcı sağlayacak bir iş ortağıyla çalışabilirsiniz. Bu yöntemle çalışabilirsiniz iş ortaklarının listesi ve adım adım süreç için bkz. Üçüncü taraf verilerini arşivlemek için [iş ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Veri bağlayıcıları için önkoşullar

Dosyada kullanılabilen çoğu veri bağlayıcısı Microsoft 365 uyumluluk merkezi üçüncü taraf verilerini içeri aktarmayı ve arşivlemek için, üçüncü taraf veri kaynağında yapılandırma görevlerini hazırlamanız ve gerçekleştirmeniz gerekir. Bu önkoşullar, her bir üçüncü taraf veri bağlayıcısı için ayrıntılı olarak belgelanmıştır.

Microsoft'un iş ortaklarından biri tarafından sağlanan Microsoft 365 uyumluluk merkezi bağlayıcıları için bağlayıcı dağıtmadan önce, kuruluşla iş ilişkisine gerek vardır.

Üçüncü taraf veri bağlayıcıları için lisans gereksinimleri için, güvenlik ve uyumlulukla ilgili lisanslama Microsoft 365 "Veri bağlayıcıları" [& bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>API'ler

Microsoft 365 ve Microsoft Priva API'leri Microsoft Bilgi Koruması SDK, Microsoft Graph API ve Office 365 Yönetim Etkinliği API'sinde kullanılabilir. Bazı uyumluluk API'leri, Microsoft 365 müşterilerinin, bağımsız yazılım satıcılarının, sistem entegratıcılarının ve yönetilen güvenlik hizmet sağlayıcılarının yüksek değerli güvenlik ve uyumluluk çözümleri oluşturmalarına olanak sağlayan yeni bir güvenlik ve uyumluluk API'leri kümesi içinde yer almaktadır.

Api'lere erişim hakkında daha fazla Graph için Bkz. [Microsoft API'lerine Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Microsoft Graph istekleri için API'ler

Dünya çerçevesinde bazı gizlilik düzenlemelerine uygun olarak, kişiler şirketlerin topladığı kişisel verileri incelemeye veya yönetmeye yönelik isteklerde  edilebilir. Bu istekler, Microsoft Priva Konu Hakları *İstekleri* çözümü kapsamındaki konu hakları istekleri olarak adlandırılır. Konu hakları istekleri, veri konusu *istekleri (* DSR) veya veri konusu erişim *istekleri (* DSAR) olarak da adlandırılır. Microsoft Graph hakları istekleriyle ilgili API'ler, geliştiricilerin konuyla ilgili Microsoft 365 isteklerini daha geniş gizlilik ekosistemi ile tümleştirebiliyor. Bu API tabanlı genişletilebilirlik, kuruluşların hem Microsoft'u hem de Microsoft olmayan ortamları kapsayan tüm veri mülkları genelinde konu hak isteklerine tek bir biçimde yanıt vermelerine olanak tanır. Bu özellik aynı zamanda ölçeğin otomasyonunu kullanmada ve kuruluşların el ile yapılan süreçlere bel bağlı kalmadan sektör düzenlemelerini daha verimli bir şekilde karşılamalarına da yardımcı olur.

Daha fazla bilgi edinmek için [Bkz. Microsoft Graph talebiyle ilgili API'leri arama](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Bilgi Koruması (MIP) SDK

MIP SDK, güvenlik ve uyumluluk merkezlerinden gelen Microsoft 365 ve koruma hizmetlerini üçüncü taraf uygulamalarına ve hizmetlerine sunar. Geliştiriciler, etiketler ve dosyalara koruma uygulamak için yerel destek oluşturmak üzere SDK'yı kullanabilir. Geliştiriciler, belirli etiketler algılandığında hangi eylemlerin gerçekleştirileceklerini ve MIP şifreli bilgiler üzerinde nedenlerini belirler.

Üst düzey MIP SDK kullanım örnekleri şunlardır:

- Dışarı aktarma dosyalarına sınıflandırma etiketleri ekan bir iş hattı uygulaması.

- MIP etiketlemesi için yerel destek sağlayan bir CAD/CAM tasarım uygulaması.

- Azure Information Protection ile verileri şifrelten bir bulut erişimi güvenlik aracısı veya veri kaybı önleme çözümü.

MIP SDK, önkoşullar, ek senaryolar ve örnekler hakkında daha fazla bilgi edinmek için bkz. [MIP SDK'ye Genel Bakış](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Graph DLP için Microsoft Teams API'si

[Veri kaybı önleme (DLP)](dlp-microsoft-teams.md) özellikleri, özellikle kuruluşların uzak Microsoft Teams fazla işi olduğu için bu kuruluşlarda yaygın olarak kullanılır. Kısa bir [süre önce, Microsoft Çevrimiçi](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) Graph Bildirim API'sinde genel olarak kullanılabilir olduğunu Teams. Bu API, geliştiricilerin gerçek zamanlı olarak iletileri Microsoft Teams dlp senaryoları uygulayan ve ardından hem müşteriler hem de iş ortakları için DLP senaryoları uygulayan uygulamalar oluşturmasını sağlar. Buna ek olarak, Microsoft Graph Yama API'si bu tür iletilere DLP eylemleri Teams sağlar.

Bu iki API, Teams DLP için Microsoft Graph API'sini oluşturur. Örnek uygulamayı kullanarak çalışmaya [başlamaya çalışabilirsiniz](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Mesajlaşma web belgelerinde Microsoft Teams daha fazla bilgi için belgelere [bakın](/graph/api/subscription-post-subscriptions).

DLP'ye yönelik lisans Teams için bkz[. Güvenlik Microsoft 365 uyumluluğu için lisans & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>eK Graph için Microsoft Graph API'si (önizleme)

[Advanced eDiscovery](overview-ediscovery-20.md) ile, kuruluşlar yaşadığı yeri veri keşfeder ve akıllı makine öğrenme ve çözümleme özellikleriyle daha uç uç eKbulma iş akışlarını yönetebilir ve verileri ilgili kümeye düşürebilirsiniz; tüm bunlar Microsoft 365 ve uyumluluk sınırının içinde kalır.

Graph API'leri Advanced eDiscovery durumlar oluşturmak ve yönetmek, kümeleri gözden geçirmek ve küme sorgularını ölçeklenebilir ve yinelenebilir bir şekilde gözden geçirmek için kullanılabilir. Bu, müşterilerin ve iş ortaklarının durum oluşturma, özel durumlar oluşturma ve koruyucularla yasal düretileri yönetme gibi ortak ve yinelenen işlemleri otomatikleştirmek için uygulamalar ve iş akışları oluşturmalarına olanak sağlar.

eKbulma için Graph API'lerinin ilk kümesi genel önizlemede kullanılabilir. Takvim yılı sonuna kadar daha fazla özellik eklemeyi planlıyoruz. Bu API'ler ve diğer güncelleştirmeler hakkında daha fazla bilgi Advanced eDiscovery bu [bloga bakın](https://aka.ms/Ignite2020AeDAA).

Advanced eDiscovery ve API lisans gereksinimleri için, güvenlik ve uyumluluk için lisanslama kılavuzunda yer alan "eKbul [Microsoft 365" & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API'si Teams Dışarı Aktarma

Enterprise Için Bilgi Arşivleme (EIA), Microsoft Teams gereksinimleri çözmelerine olanak sağlarken müşterilerimiz için önemli bir senaryodur. Microsoft Teams'ta içeriği arşivlemeye yerleşik yeteneklerimizin yanı sıra, müşteriler ve iş ortakları artık özel uygulama ve tümleştirme senaryolarını çözmek için Teams Dışarı Aktarma API'lerini de kullanabilir. Dışarı Teams API'leri, her bir ileti ve ileti eklerinin toplu olarak dışarı aktarmalarını (uygulama başına/kiracı başına saniye başına 200 Teams) destekler. Silinen iletilere, silindikten sonra 30 gün içerisinde API tarafından da erişilebilir. Bu API'leri dışarı Teams hakkında daha fazla bilgi ve bunları uygulamalarınız içinde nasıl kullanabileceğiniz hakkında daha fazla bilgi için bkz. Dışarı Aktarma [API'leri Microsoft Teams dışarı aktarma](/microsoftteams/export-teams-content).

Dışarı Aktarma API'lerinin kullanımına yönelik lisans Teams için, güvenlik Microsoft 365 uyumluluğu için lisanslama & [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Microsoft Graph Bağlayıcı API'leri (önizleme)

Microsoft [Graph bağlayıcıları](/microsoftsearch/connectors-overview) ile, kuruluşlar üçüncü taraf verileri dizine adi olarak işaretlerini Microsoft Arama olabilir. Bu özellik, hem üretkenlik uygulamalarında hem de daha geniş bir Microsoft Microsoft 365 arama özelliği olan içerik kaynağı türlerini genişletiyor. Üçüncü taraf verileri şirket içinde veya genel ya da özel bulutlarda barındırabilirsiniz. Bu Advanced eDiscovery, bağlı uygulamalar için yerleşik uyumluluk değerinin geliştirici Microsoft 365 etkinleştir istiyoruz. Bu, kullanıcıları sorunsuz uyumluluk deneyimleriyle güçlendirmek için Microsoft 365 mobil Microsoft 365 tümleştirmesine olanak sağlar. Microsoft Graph Bağlayıcı API'lerini uygulamalar görünümünüze dahil etmeyi öğrenmek için bkz. Microsoft Web Sitesinde bağlantı oluşturma[, güncelleştirme ve Graph](/graph/connecting-external-content-connectors-api-overview).
