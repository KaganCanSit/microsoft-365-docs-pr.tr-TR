---
title: Microsoft 365'da üçüncü taraf verileri içeri aktarmak ve arşivlemek için veri bağlayıcılarını kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Posta kutularını Microsoft 365 için sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından üçüncü taraf verileri içeri aktarmayı ve arşivlemeyi öğrenin.
ms.openlocfilehash: 0588ab242f2d198c486b7ce0318939e204076421
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934961"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Üçüncü taraf verileri için bağlayıcılar hakkında daha fazla bilgi edinme

Microsoft 365, yöneticilerin Microsoft dışı üçüncü taraf verileri sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından Microsoft 365 kuruluşunuzdaki posta kutularına aktarmak ve arşivlemek için veri bağlayıcılarını kullanmasına olanak tanır. Microsoft 365'da üçüncü taraf verileri içeri aktarmak ve arşivleme amacıyla veri bağlayıcılarını kullanmanın birincil avantajlarından biri, içeri aktarıldıktan sonra verilere çeşitli Microsoft Purview çözümleri uygulayabilmenizdir. Bu, kuruluşunuzun Microsoft dışı verilerinin kuruluşunuzu etkileyen düzenlemelere ve standartlara uygun olduğundan emin olmanıza yardımcı olur.

Üçüncü taraf verileri içeri aktarmak ve arşivleme amacıyla veri bağlayıcıları oluşturmayı ve Microsoft 365'a aktarıldıktan sonra verilere uyumluluk çözümleri uygulama örneklerini gösteren bu etkileşimli kılavuzu izleyin.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Üçüncü taraf veri bağlayıcıları

Microsoft Purview uyumluluk portalı LinkedIn, Instant Bloomberg ve Twitter gibi çeşitli veri kaynaklarından verileri içeri aktarmak için Microsoft'tan yerel üçüncü taraf veri bağlayıcıları ve Insider risk yönetimi çözümünü destekleyen veri bağlayıcıları sağlar. Microsoft, bu veri bağlayıcılarına ek olarak, uyumluluk portalında daha birçok üçüncü bölüm veri bağlayıcısı sağlamak için aşağıdaki iş ortaklarıyla birlikte çalışır. Kuruluşunuz, uyumluluk portalında ilgili veri bağlayıcısını oluşturmadan önce arşivleme hizmetini ayarlamak için bu iş ortaklarıyla birlikte çalışır.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Sonraki bölümlerde listelenen üçüncü taraf verileri (İk verileri ve Microsoft 365 Insider risk yönetimi çözümü için kullanılan fiziksel badging verileri hariç) kullanıcı posta kutularına aktarılır. Üçüncü taraf verilerini destekleyen Microsoft Purview çözümleri, verilerin depolandığı kullanıcı posta kutusuna uygulanır.

### <a name="microsoft-data-connectors"></a>Microsoft veri bağlayıcıları

Aşağıdaki tabloda, uyumluluk portalında kullanılabilen yerel üçüncü taraf veri bağlayıcıları listelemektedir. Tabloda, üçüncü taraf verileri Microsoft 365 içeri aktardıktan ve arşivledikten sonra uygulayabileceğiniz uyumluluk çözümleri de özetlenebilir. Her uyumluluk çözümünün daha ayrıntılı açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için [Üçüncü taraf verilerini destekleyen](#overview-of-compliance-solutions-that-support-third-party-data) uyumluluk çözümlerine genel bakış bölümüne bakın.

Bu veri türü için bağlayıcı oluşturmaya yönelik adım adım yönergelere gitmek için **Üçüncü taraf veri** sütunundaki bağlantıya tıklayın.

|Üçüncü taraf verileri  |Dava tutma|Ediscovery  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |İçeriden risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Bloomberg Message](archive-bloomberg-message-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||
|[Epic EHR sağlık hizmetleri](import-epic-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Genel EHR sağlık hizmetleri](import-healthcare-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[İnsan kaynakları (İk)](import-hr-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[ICE Chat](archive-icechat-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Fiziksel badging](import-physical-badging-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[Slack eKeşif](archive-slack-data-microsoft.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Veritas veri bağlayıcıları

Bu bölümdeki tabloda, Veritas ile ortaklaşa sağlanan üçüncü taraf veri bağlayıcıları listelenir. Tabloda ayrıca üçüncü taraf verileri içeri aktardıktan ve Microsoft 365 arşivledikten sonra uygulayabileceğiniz uyumluluk çözümleri de özetlenebilir. Her uyumluluk çözümünün daha ayrıntılı açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için [Üçüncü taraf verilerini destekleyen](#overview-of-compliance-solutions-that-support-third-party-data) uyumluluk çözümlerine genel bakış bölümüne bakın.

Microsoft 365'da üçüncü taraf verilerini arşivlemeden önce, kuruluşunuz için arşivleme hizmetini (*Birleştir1* olarak adlandırılır) ayarlamak için Veritas ile çalışmanız gerekir. Daha fazla bilgi için **, üçüncü taraf veri** sütunundaki bağlantıya tıklayarak ilgili veri türü için bağlayıcı oluşturmaya yönelik adım adım yönergelere gidin.

|Üçüncü taraf verileri  |Dava tutma|Ediscovery  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |İçeriden risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[MS SQL üzerinde Cisco Jabber](archive-ciscojabberonmssql-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Oracle üzerinde Cisco Jabber](archive-ciscojabberonoracle-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[PostgreSQL üzerinde Cisco Jabber](archive-ciscojabberonpostgresql-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[FX Connect](archive-fxconnect-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[MS SQL Veritabanı](archive-mssqldatabaseimporter-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters Dealing](archive-reutersdealing-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Salesforce Chatter](archive-salesforcechatter-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Skype Kurumsal](archive-skypeforbusiness-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Slack eKeşif](archive-slack-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Symphony](archive-symphony-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Metinle ayrılmış](archive-text-delimited-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Web sayfaları](archive-webpagecapture-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Facebook Workplace](archive-workplacefromfacebook-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Zoom Meetings](archive-zoommeetings-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>TeleMessage veri bağlayıcıları

Bu bölümdeki tabloda, TeleMessage ile ortaklaşa sağlanan üçüncü taraf veri bağlayıcıları listelenir. Tabloda ayrıca üçüncü taraf verileri içeri aktardıktan ve Microsoft 365 arşivledikten sonra uygulayabileceğiniz uyumluluk çözümleri de özetlenebilir. Her uyumluluk çözümünün daha ayrıntılı açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için [Üçüncü taraf verilerini destekleyen](#overview-of-compliance-solutions-that-support-third-party-data) uyumluluk çözümlerine genel bakış bölümüne bakın.

üçüncü taraf verileri Microsoft 365 arşivlemeden önce, kuruluşunuz için arşivleme hizmetini ayarlamak için TeleMessage ile çalışmanız gerekir. Daha fazla bilgi için **, üçüncü taraf veri** sütunundaki bağlantıya tıklayarak ilgili veri türü için bağlayıcı oluşturmaya yönelik adım adım yönergelere gidin.

TeleMessage veri bağlayıcıları, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda da kullanılabilir. Daha fazla bilgi için bu makalenin [ABD Kamu bulutundaki Veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

|Üçüncü taraf verileri  |Dava tutma|Ediscovery  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |İçeriden risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[AT&T Ağı](archive-att-network-archiver-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bell Network](archive-bell-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Enterprise Numarası](archive-enterprise-number-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[O2 Ağ](archive-o2-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Rogers Network](archive-rogers-network-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Sinyal](archive-signal-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Telgraf](archive-telegram-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[TELUS Network](archive-telus-network-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Whatsapp](archive-whatsapp-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>17a-4 veri bağlayıcıları

Bu bölümdeki tabloda, 17a-4 LLC ortaklığıyla sağlanan üçüncü taraf veri bağlayıcıları listelenir. Tabloda ayrıca üçüncü taraf verileri içeri aktardıktan ve Microsoft 365 arşivledikten sonra uygulayabileceğiniz uyumluluk çözümleri de özetlenebilir. Her uyumluluk çözümünün daha ayrıntılı açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için [Üçüncü taraf verilerini destekleyen](#overview-of-compliance-solutions-that-support-third-party-data) uyumluluk çözümlerine genel bakış bölümüne bakın.

üçüncü taraf verilerini Microsoft 365 arşivlemeden önce, kuruluşunuz için arşivleme hizmetini (*DataParser* olarak adlandırılır) ayarlamak için 17a-4 LLC ile çalışmanız gerekir. Daha fazla bilgi için **, üçüncü taraf veri** sütunundaki bağlantıya tıklayarak ilgili veri türü için bağlayıcı oluşturmaya yönelik adım adım yönergelere gidin.

17a-4 veri bağlayıcıları, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda da kullanılabilir. Daha fazla bilgi için bu makalenin [ABD Kamu bulutundaki Veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

|Üçüncü taraf verileri  |Dava tutma|Ediscovery  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |İçeriden risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Blackberry](archive-17a-4-blackberry-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[FX Connect](archive-17a-4-fxconnect-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[ICE Chat](archive-17a-4-ice-im-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[LivePerson Konuşma Bulutu](archive-17a-4-liveperson-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Espri](archive-17a-4-quip-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
[Skype Kurumsal Sunucu](archive-17a-4-skype-for-business-server-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bol -luk](archive-17a-4-slack-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Zoom](archive-17a-4-zoom-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>CellTrust veri bağlayıcıları

Bu bölümdeki tabloda, CellTrust ile ortaklaşa sağlanan üçüncü taraf veri bağlayıcısı listelenir. Tabloda ayrıca üçüncü taraf verileri içeri aktardıktan ve Microsoft 365 arşivledikten sonra uygulayabileceğiniz uyumluluk çözümleri de özetlenebilir. Her uyumluluk çözümünün daha ayrıntılı açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için [Üçüncü taraf verilerini destekleyen](#overview-of-compliance-solutions-that-support-third-party-data) uyumluluk çözümlerine genel bakış bölümüne bakın.

Microsoft 365'da üçüncü taraf verileri arşivlemeden önce, kuruluşunuz için arşivleme hizmetini (*CellTrust SL2* olarak adlandırılır) ayarlamak için CellTrust ile çalışmanız gerekir. Daha fazla bilgi için **, Üçüncü taraf veri** sütunundaki bağlantıya tıklayarak CellTrust SL2 bağlayıcısı oluşturmaya yönelik adım adım yönergelere gidin.

|Üçüncü taraf verileri  |Dava tutma|Ediscovery  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |İçeriden risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

CellTrust SL2 veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda da kullanılabilir. Daha fazla bilgi için bu makalenin [ABD Kamu bulutundaki Veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Üçüncü taraf verilerini destekleyen uyumluluk çözümlerine genel bakış

Aşağıdaki bölümlerde, Microsoft Purview çözümlerinin önceki tabloda listelenen üçüncü taraf verilerini yönetmenize yardımcı olabilecek bazı şeyler açıklanmaktadır.

### <a name="litigation-hold"></a>Dava tutma

Üçüncü taraf verilerini korumak için bir kullanıcı posta kutusuna Dava [bekletmesi](create-a-litigation-hold.md) yerleştirirsiniz. Ayrı tutma oluşturduğunuzda, silinen ve değiştirilen üçüncü taraf verilerin belirli bir süre boyunca saklanması ve ardından posta kutusundan kalıcı olarak silinmesi için bir *ayrı tutma süresi (zamana bağlı saklama* olarak da adlandırılır) belirtebilirsiniz. Ya da içeriği süresiz olarak ( *sonsuz ayrı tutma* olarak adlandırılır) veya Dava ayrılığı kaldırılana kadar saklayabilirsiniz.

### <a name="ediscovery"></a>Ediscovery

Microsoft 365'deki üç birincil eBulma aracı İçerik arama, Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) araçlarıdır.

- **[İçerik araması](content-search.md).** İçeri aktardığınız üçüncü taraf verileri için posta kutularını aramak için içerik arama aracını kullanabilirsiniz. Arama sonuçlarınızı daraltmak ve arama sonuçlarını dışarı aktarmak için arama sorgularını ve koşullarını kullanabilirsiniz.

- **[eBulma (Standart)](get-started-core-ediscovery.md).** Bu araç, servis talebi verilerine kimlerin erişebileceğini denetlemenize, kullanıcı posta kutularına veya arama ölçütleriyle eşleşen posta kutusu içeriğine ayrı tutmanıza olanak tanıyan servis talepleri oluşturmanıza olanak tanıyarak temel arama ve dışarı aktarma işlevselliğini temel alır. Bu, kullanıcı posta kutularına aktarılan üçüncü taraf verilerine eBulma ayrılığı yerleştirebileceğiniz anlamına gelir.

- **[eBulma (Premium)](overview-ediscovery-20.md).** Bu güçlü araç, bir olaya koruyucu eklemenizi, koruyucu verilerini beklemeye almanızı ve ardından temalar ve yinelenen algılama gibi daha fazla analiz için bir koruyucunun üçüncü taraf verilerini gözden geçirmenize izin vererek eBulma (Standart) işlevini genişletir. Üçüncü taraf verileri bir gözden geçirme kümesine yükledikten sonra sorgulayabilir ve dar bir sonuç kümesine filtreleyebilirsiniz.

   Hem eBulma (Standart) hem de eBulma (Premium), kuruluşunuzun yasal veya iç soruşturmalarıyla ilgili olabilecek üçüncü taraf verileri yönetmenize olanak sağlar.

### <a name="retention-settings"></a>Bekletme ayarları

Saklama süresi dolduktan sonra üçüncü taraf verileri (ve diğer posta kutusu içeriğini) saklamak ve silmek için kullanıcı posta kutularına bekletme [ilkesi](retention.md) uygulayabilirsiniz. Ayrıca, belirli bir yaştaki üçüncü taraf verilerini silmek için bekletme ilkelerini kullanabilir veya üçüncü taraf verilerinin saklama süresi dolduğunda [bir değerlendirme gözden geçirmesini tetikleme amacıyla bekletme etiketlerini kullanabilirsiniz](disposition.md) .

### <a name="records-management"></a>Kayıt yönetimi

Microsoft 365'daki [kayıt yönetimi](records-management.md) özelliği, üçüncü taraf verilerini kayıt olarak bildirmenizi sağlar. Bu, posta kutularındaki üçüncü taraf verilerini kayıt olarak işaretleyen bir bekletme etiketi uygulayan kullanıcılar tarafından el ile yapılabilir. Ya da üçüncü taraf verilerindeki hassas bilgileri, anahtar sözcükleri veya içerik türlerini tanımlayarak bekletme etiketlerini otomatik olarak uygulayabilirsiniz.

### <a name="communication-compliance"></a>İletişim uyumluluğu

Kuruluşunuzun veri standartlarıyla uyumlu olduğundan emin olmak için üçüncü taraf verileri incelemek için [İletişim uyumluluğunu](communication-compliance.md) kullanabilirsiniz. Bunu, kuruluşunuzdaki uygunsuz iletileri algılayarak, yakalayarak ve düzeltme eylemleri gerçekleştirerek yapabilirsiniz. Örneğin, rahatsız edici dil, hassas bilgiler ve mevzuat uyumluluğu için içeri aktardığınız üçüncü taraf verilerini izleyebilirsiniz.

### <a name="insider-risk-management"></a>İçeriden risk yönetimi

Seçmeli İk verileri gibi üçüncü taraf verilerden gelen sinyaller, [Insider risk yönetimi](insider-risk-management.md) çözümü tarafından kuruluşunuzdaki riskli etkinlikleri algılamanıza, araştırmanıza ve işlem yapmanıza izin vererek iç riskleri en aza indirmek için kullanılabilir. Örneğin, İk veri bağlayıcısı tarafından içeri aktarılan veriler, ayrılan çalışan verilerinin çalınması algılamaya yardımcı olmak için risk göstergeleri olarak kullanılır.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Üçüncü taraf verileri aramak için eBulma araçlarını kullanma

Kullanıcı posta kutularında üçüncü taraf verileri içeri aktarmak ve arşivlemek için veri bağlayıcılarını kullandıktan sonra, üçüncü taraf verileri aramak için Microsoft 365 eBulma araçlarını kullanabilirsiniz. Üçüncü taraf verileri korumak için eBulma (Standart) ve eBulma (Premium) durumlarıyla ilişkili sorgu tabanlı tutmalar oluşturmak için eBulma araçlarını da kullanabilirsiniz. eBulma araçları hakkında daha fazla bilgi için bkz. [Microsoft 365'de eBulma çözümleri](ediscovery.md).

Veri bağlayıcısı kullanarak kullanıcı posta kutularına aktardığınız herhangi bir üçüncü taraf veri türünü aramak (veya ayrı tutmak) için aşağıdaki arama sorgusunu kullanabilirsiniz. Aramanın kapsamını kullanıcı posta kutularına göre daraltmaya özen gösterin.

```powershell
kind:externaldata
```

İçerik araması, eBulma (Standart) olayıyla ilişkilendirilmiş bir arama veya eBulma (Premium) içindeki bir koleksiyon için Anahtar **Sözcükler** kutusunda bu sorguyu kullanabilirsiniz.

![Üçüncü taraf verileri aramak için sorgu.](..\media\SearchThirdPartyData1.png)

Arama kapsamını üçüncü taraf verileriyle `kind:externaldata` daraltmak için property:value çiftini de kullanabilirsiniz. Örneğin, içeri aktarılan öğenin **Subject** özelliğinde *contoso* sözcüğünü içeren herhangi bir üçüncü taraf veri kaynağından içeri aktarılan öğeleri aramak için **Anahtar Sözcükler** kutusunda aşağıdaki sorguyu kullanın:

```powershell
subject:contoso AND kind:externaldata
```

Alternatif olarak, aynı sorguyu yapılandırmak için **İleti türü** koşulunu kullanabilirsiniz.

![Aramaları üçüncü taraf verileriyle sınırlandırmak için İleti türü koşulunu kullanın.](..\media\SearchThirdPartyData2.png)

Belirli bir arşivlenmiş üçüncü taraf veri türünü aramak için, arama sorgusunda **itemclass** posta kutusu özelliğini kullanın. Aşağıdaki özelliği kullanın:değer biçimi:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Üçüncü taraf veri bağlayıcısı tarafından içeri aktarılan her öğe, üçüncü taraf veri türüne karşılık gelen bir değere sahip **itemclass** özelliğini içerir. Örneğin, içeri aktarılan öğenin **Subject** özelliğinde *contoso* sözcüğünü içeren Facebook verilerini aramak için aşağıdaki sorguyu kullanın:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Burada, farklı üçüncü taraf veri türleri için **itemclass** değerlerine birkaç örnek verilmiştir.

| **Üçüncü taraf veri türü** | **itemclass özelliğinin değeri**   |
|---------------------------|-------------------------------------|
| Bloomberg Message         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| WhatsApp Arşivleyicisi         | ipm.externaldata.whatsapparchiver* |
|||

*itemclass* özelliğinin değerleri büyük/küçük harfe duyarlı değildir. Genel olarak, üçüncü taraf veri türünün adını (boşluk olmadan) ve ardından joker karakter ( * ) karakteri kullanın.

eBulma arama sorguları oluşturma hakkında daha fazla bilgi için bkz. [eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutundaki veri bağlayıcıları

Bazı veri bağlayıcıları ABD Kamu bulutunda kullanılabilir. Aşağıdaki bölümlerde, üçüncü taraf veri bağlayıcılarını destekleyen belirli kamu ortamları gösterilir. ABD Kamu bulutları hakkında daha fazla bilgi için bkz. [US Government Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>ABD Kamu bulutundaki Veritas veri bağlayıcıları (önizleme)

|Veri bağlayıcısı  |GCC  |yüksek GCC  |Dod  |
|:---------|:---------|:---------|:---------|
|CellTrust| Evet | Hayır | Hayır |
|MS SQL üzerinde Cisco Jabber| Evet | Hayır | Hayır |
|Oracle üzerinde Cisco Jabber| Evet | Hayır | Hayır |
|PostgreSQL üzerinde Cisco Jabber| Evet | Hayır | Hayır |
|EML| Evet | Hayır | Hayır |
|FX Connect| Evet | Hayır | Hayır |
|Jive| Evet | Hayır | Hayır |
|MS SQL Veritabanı| Evet | Hayır | Hayır |
|Pivot| Evet | Hayır | Hayır |
|Redtail Speak| Evet | Hayır | Hayır |
|Reuters Dealing| Evet | Hayır | Hayır |
|Reuters Eikon| Evet | Hayır | Hayır |
|Reuters FX| Evet | Hayır | Hayır |
|RingCentral| Evet | Hayır | Hayır |
|Salesforce Chatter| Evet | Hayır | Hayır |
|ServiceNow| Evet | Hayır | Hayır |
|Skype Kurumsal| Evet | Hayır | Hayır |
|Slack eKeşif| Evet | Hayır | Hayır |
|Symphony| Evet | Hayır | Hayır |
|Metinle ayrılmış| Evet | Hayır | Hayır |
|Twitter| Evet | Hayır | Hayır |
|Webex Teams| Evet | Hayır | Hayır |
|Web sayfaları| Evet | Hayır | Hayır |
|Facebook Workplace| Evet | Hayır | Hayır |
|XIP| Evet | Hayır | Hayır |
|XSLT/XML| Evet | Hayır | Hayır |
|Yieldbroker| Evet | Hayır | Hayır |
|YouTube| Hayır | Hayır | Hayır |
|Zoom Meetings| Evet | Hayır | Hayır |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutunda TeleMessage veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |yüksek GCC  |Dod  |
|:---------|:---------|:---------|:---------|
|Android Arşivleyici | Evet | Hayır | Hayır |
|AT&T SMS/MMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Bell SMS/MMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Kurumsal Numara Arşivleyicisi | Evet | Hayır | Hayır |
|O2 SMS ve Ses Ağı Arşivleyicisi | Evet         | Hayır | Hayır |
|Rogers Ağ Arşivleyicisi | Evet         | Hayır | Hayır |
|Signal Arşivleyicisi | Evet | Hayır | Hayır |
|Telegram Arşivleyicisi | Evet | Hayır | Hayır |
|TELUS SMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Verizon SMS/MMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|WeChat Arşivleyicisi | Evet | Hayır | Hayır |
|WhatsApp Arşivleyicisi | Evet | Hayır | Hayır |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutunda 17a-4 veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |yüksek GCC  |Dod  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Evet | Hayır | Hayır |
|Bloomberg DataParser  | Evet | Hayır | Hayır |
|Cisco Jabber DataParser  | Evet | Hayır | Hayır |
|Cisco Webex DataParser  | Evet | Hayır | Hayır |
|FactSet DataParser  | Evet | Hayır | Hayır |
|Fuze DataParser  | Evet | Hayır | Hayır |
|FX Connect DataParser  | Evet | Hayır | Hayır |
|ICE DataParser  | Evet | Hayır | Hayır |
|InvestEdge DataParser  | Evet | Hayır | Hayır |
|LivePerson Conversational Cloud DataParser  | Evet | Hayır | Hayır |
|Quip DataParser  | Evet | Hayır | Hayır |
|Refinitiv Eikon Messenger DataParser  | Evet | Hayır | Hayır |
|ServiceNow DataParser  | Evet | Hayır | Hayır |
|Skype Kurumsal Sunucu DataParser | Evet | Hayır | Hayır |
|Slack DataParser | Evet | Hayır | Hayır |
|SQL DataParser  | Evet | Hayır | Hayır |
|Symphony DataParser | Evet | Hayır | Hayır |
|Zoom DataParser | Evet | Hayır | Hayır |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutunda CellTrust veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |yüksek GCC  |Dod  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Evet | Hayır | Hayır |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Üçüncü taraf verileri arşivlemek için bir Microsoft iş ortağıyla çalışma

Üçüncü taraf verileri içeri aktarma ve arşivleme için bir diğer seçenek de kuruluşunuzun bir Microsoft İş Ortağı ile çalışmasıdır. Üçüncü taraf veri türü Microsoft uyumluluk merkezinde bulunan veri bağlayıcıları tarafından desteklenmiyorsa, üçüncü taraf veri kaynağındaki öğeleri düzenli olarak ayıklayacak şekilde yapılandırılacak özel bir bağlayıcı sağlayabilecek ve ardından üçüncü taraf BIR API ile Microsoft buluta bağlanıp bu öğeleri Microsoft 365 aktarabilecek bir iş ortağıyla çalışabilirsiniz. İş ortağı bağlayıcısı ayrıca bir öğenin içeriğini üçüncü taraf veri kaynağından bir e-posta iletisine dönüştürür ve ardından Microsoft 365 bir posta kutusuna aktarır.

Birlikte çalışabileceğiniz iş ortaklarının listesi ve bu yöntemin adım adım işlemi için bkz. [Microsoft 365'da üçüncü taraf verileri arşivlemek için bir iş ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md).
