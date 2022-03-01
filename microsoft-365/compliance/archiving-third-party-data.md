---
title: Aynı dosyada üçüncü taraf verilerini içeri aktarma ve arşivlemek için veri bağlayıcılarını Microsoft 365
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
description: Sosyal medya platformları, anlık ileti platformları ve belge işbirliği platformlarından gelen üçüncü taraf verilerini kendi posta kutularına aktarmayı ve Microsoft 365 öğrenin.
ms.openlocfilehash: 06833acd3ea29e30d8789fbb05e0a081309c7f2b
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2022
ms.locfileid: "63016312"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Üçüncü taraf verileri için bağlayıcılar hakkında bilgi

Microsoft 365 yöneticilerin Microsoft dışı, üçüncü taraf verileri sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından gelen posta kutularına, Microsoft 365 posta kutularına içeri aktarmalarını ve arşivlemelerini sağlar. Üçüncü taraf verilerini Microsoft 365'ta içeri aktararak arşivlemek için veri bağlayıcıları kullanmanın başlıca faydalarından biri, verileri içeri aktardikten Microsoft 365 uyumluluk çözümleri uygulayabilirsiniz. Bu, kuruluşta yer alan Microsoft olmayan verilerin kuruluşu etkileyen yasal düzenlemelere ve standartlara uygun olmasını sağlamaya yardımcı olur.

Üçüncü taraf verilerini içeri aktarma ve arşivlemek için veri bağlayıcıları oluşturmanın ve verileri başka bir öğeye aktardikten sonra bunlara uyumluluk çözümleri uygulama örneklerini gösteren bu etkileşimli Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Üçüncü taraf veri bağlayıcıları

The Microsoft 365 uyumluluk merkezi provides native third-party data connectors from Microsoft to import data sources, such as LinkedIn, Instant Bloomberg, and Twitter and data connectors that support the Insider risk management solution. Microsoft, bu veri bağlayıcılarına ek olarak, son veri bağlantılarında daha birçok üçüncü bölüm veri bağlayıcısı sağlamak için aşağıdaki Microsoft 365 uyumluluk merkezi. Kuruluş, dosyada karşılık gelen bir veri bağlayıcısı oluşturmadan önce bu iş ortaklarıyla birlikte arşiv hizmetini Microsoft 365 uyumluluk merkezi.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Sonraki bölümlerde listelenen üçüncü taraf verileri (İk verileri ve Microsoft 365 Insider risk yönetimi çözümü için kullanılan fiziksel garanti verileri dışında) kullanıcı posta kutularına aktarılır. Üçüncü Microsoft 365 destekleyen uyumluluk çözümleri, verilerin depolandığı kullanıcı posta kutusuna uygulanır.

### <a name="microsoft-data-connectors"></a>Microsoft veri bağlayıcıları

Aşağıdaki tabloda, ana tabloda kullanılabilen yerel üçüncü taraf veri bağlayıcıları Microsoft 365 uyumluluk merkezi. Tabloda ayrıca, üçüncü taraf verilerini içeri aktardıktan ve arşivledikten sonra uygulayabilecek uyumluluk çözümleri de özetlenir Microsoft 365. Her uyumluluk [çözümünün daha ayrıntılı](#overview-of-compliance-solutions-that-support-third-party-data) açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için, Üçüncü taraf verileri destekleyen uyumluluk çözümlerine genel bakış bölümüne bakın.

Bu veri türüne **bağlayıcı oluşturmaya ilişkin** adım adım yönergelere gitmek için Üçüncü taraf veri sütunundaki bağlantıya tıklayın.

|Üçüncü taraf verileri  |Mahkeme tutma|eKbulma  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |Insider risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Bloomberg Message](archive-bloomberg-message-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||
|[Destan EHR sağlık hizmetleri](import-epic-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Genel EHR sağlık hizmetleri](import-healthcare-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[İnsan kaynakları (İk)](import-hr-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[ICE Sohbeti](archive-icechat-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Fiziksel bajman](import-physical-badging-data.md) ||||||![Onay işareti](../media/checkmark.png)|
|[Slack eKovery](archive-slack-data-microsoft.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Veritas veri bağlayıcıları

Bu bölümdeki tabloda, Veritas ile ortak olarak bulunan üçüncü taraf veri bağlayıcıları listeleni. Tabloda ayrıca, üçüncü taraf verileri içeri aktardikten ve burada arşivledikten sonra bu verilere uygulayabilecek uyumluluk çözümleri de Microsoft 365. Her uyumluluk [çözümünün daha ayrıntılı](#overview-of-compliance-solutions-that-support-third-party-data) açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için, Üçüncü taraf verileri destekleyen uyumluluk çözümlerine genel bakış bölümüne bakın.

Üçüncü taraf verilerini Microsoft 365'de arşivlemeden önce, veritas ile birlikte çalışarak kuruluş için arşivleme hizmetini (*Birleştirme1* olarak adlandırılan) ayarlayabilirsiniz. Daha fazla bilgi için, Üçüncü taraf veri sütunundaki bağlantıya tıklayarak bu veri türüne ilişkin bağlayıcıyı oluşturmaya ilişkin adım adım yönergelere bakın.

|Üçüncü taraf verileri  |Mahkeme tutma|eKbulma  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |Insider risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[MS SQL'da Cisco Cisco Cisco SQL](archive-ciscojabberonmssql-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Cisco Cisco Ciscober on Oracle](archive-ciscojabberonoracle-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[PostgreSQL'de Cisco Cisco Cisco Cisco Cisco](archive-ciscojabberonpostgresql-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[FX Bağlan](archive-fxconnect-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[MS SQL Veritabanı](archive-mssqldatabaseimporter-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Özet](archive-pivot-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters Ilgilenme](archive-reutersdealing-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters E ilgili](archive-reuterseikon-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Salesforce SohbetTeri](archive-salesforcechatter-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Skype Kurumsal](archive-skypeforbusiness-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Slack eKovery](archive-slack-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Burya](archive-symphony-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Metinle ayrılmış](archive-text-delimited-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Web sayfaları](archive-webpagecapture-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Facebook'tan iş yeri](archive-workplacefromfacebook-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Ödemebroker](archive-yieldbroker-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|||
|[Toplantıları Yakınlaştırma](archive-zoommeetings-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>TeleMessage veri bağlayıcıları

Bu bölümdeki tabloda, TeleMessage ile ortak olarak bulunan üçüncü taraf veri bağlayıcıları liste almaktadır. Tabloda ayrıca, üçüncü taraf verileri içeri aktardikten ve burada arşivledikten sonra bu verilere uygulayabilecek uyumluluk çözümleri de Microsoft 365. Her uyumluluk [çözümünün daha ayrıntılı](#overview-of-compliance-solutions-that-support-third-party-data) açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için, Üçüncü taraf verileri destekleyen uyumluluk çözümlerine genel bakış bölümüne bakın.

Microsoft 365'de üçüncü taraf verilerini arşivleymeden önce, telemessage ile birlikte çalışarak, bu verileri kuruluşlarınız için arşivleme hizmetini ayarlayabilirsiniz. Daha fazla bilgi için, Üçüncü taraf veri sütunundaki bağlantıya tıklayarak bu veri türüne ilişkin bağlayıcıyı oluşturmaya ilişkin adım adım yönergelere bakın.

TeleMessage veri bağlayıcıları ABD Kamu GCC ve Microsoft 365 ortamlarda da kullanılabilir. Daha fazla bilgi için, [bu makalenin ABD Kamu bulutunda veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

|Üçüncü taraf verileri  |Mahkeme tutma|eKbulma  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |Insider risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bell Network](archive-bell-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Enterprise Numarası](archive-enterprise-number-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[O2 Network](archive-o2-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Rogers Network](archive-rogers-network-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Sinyal](archive-signal-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[2010](archive-telegram-archiver-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[TELUS Network](archive-telus-network-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>17a-4 veri bağlayıcıları

Bu bölümdeki tabloda, 17a-4 LLC ile ortak olarak bulunan üçüncü taraf veri bağlayıcıları liste almaktadır. Tabloda ayrıca, üçüncü taraf verileri içeri aktardikten ve burada arşivledikten sonra bu verilere uygulayabilecek uyumluluk çözümleri de Microsoft 365. Her uyumluluk [çözümünün daha ayrıntılı](#overview-of-compliance-solutions-that-support-third-party-data) açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için, Üçüncü taraf verileri destekleyen uyumluluk çözümlerine genel bakış bölümüne bakın.

Microsoft 365'ta üçüncü taraf verilerini arşivlemeden önce, 17a-4 LLC ile birlikte çalışarak bu hizmet için arşivleme hizmetini (*DataParser* olarak adlandırılan) ayarlayabilirsiniz. Daha fazla bilgi için, Üçüncü taraf veri sütunundaki bağlantıya tıklayarak bu veri türüne ilişkin bağlayıcıyı oluşturmaya ilişkin adım adım yönergelere bakın.

17a-4 veri bağlayıcıları, ABD Kamu GCC ve Microsoft 365 ortamlarda da kullanılabilir. Daha fazla bilgi için, [bu makalenin ABD Kamu bulutunda veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

|Üçüncü taraf verileri  |Mahkeme tutma|eKbulma  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |Insider risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Cisco Cisco Ciscober](archive-17a-4-cisco-jabber-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bilgi Kümesi](archive-17a-4-factset-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Dondur](archive-17a-4-fuze-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[FX Bağlan](archive-17a-4-fxconnect-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[ICE Sohbeti](archive-17a-4-ice-im-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[LivePerson Konuşma Bulutu](archive-17a-4-liveperson-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Sessiz](archive-17a-4-quip-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Refinitiv Evitn Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
[Skype Kurumsal Sunucu](archive-17a-4-skype-for-business-server-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Bolluk](archive-17a-4-slack-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Burya](archive-17a-4-symphony-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
|[Yakınlaştırma](archive-17a-4-zoom-data.md)    |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>CellTrust veri bağlayıcıları

Bu bölümdeki tabloda, CellTrust ile ortak olarak bulunan üçüncü taraf veri bağlayıcısı liste bulunmaktadır. Tabloda ayrıca, üçüncü taraf verileri içeri aktardikten ve burada arşivledikten sonra bu verilere uygulayabilecek uyumluluk çözümleri de Microsoft 365. Her uyumluluk [çözümünün daha ayrıntılı](#overview-of-compliance-solutions-that-support-third-party-data) açıklaması ve üçüncü taraf verilerini nasıl desteklediği hakkında daha ayrıntılı bilgi için, Üçüncü taraf verileri destekleyen uyumluluk çözümlerine genel bakış bölümüne bakın.

Microsoft 365'da üçüncü taraf verilerini arşivleymeden önce, bu kuruluşun arşivleme hizmetini (*CellTrust SL2* olarak adlandırılan) ayarlamak için CellTrust ile birlikte çalışmanız gerekir. Daha fazla bilgi için, Üçüncü taraf veri sütunundaki bağlantıya tıklayarak CellTrust SL2 bağlayıcısı oluşturmaya ilişkin adım adım yönergelere bakın.

|Üçüncü taraf verileri  |Mahkeme tutma|eKbulma  |Bekletme ayarları  |Kayıt yönetimi  |İletişim uyumluluğu  |Insider risk yönetimi  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)||
||||||||

CellTrust SL2 veri bağlayıcısı, ABD Kamu GCC ve Microsoft 365 ortamlarda da kullanılabilir. Daha fazla bilgi için, [bu makalenin ABD Kamu bulutunda veri bağlayıcıları](#data-connectors-in-the-us-government-cloud) bölümüne bakın.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Üçüncü taraf verilerini destekleyen uyumluluk çözümlerine genel bakış

Aşağıdaki bölümlerde, uyumluluk çözümlerinin uyumluluk Microsoft 365 tabloda listelenen üçüncü taraf verilerini yönetmenize yardımcı olacak bazı şeyler açıklanmaktadır.

### <a name="litigation-hold"></a>Mahkeme tutma

Üçüncü taraf [verilerini tutmak için kullanıcı](create-a-litigation-hold.md) posta kutusu üzerinde Mahkeme var. Bir hold (zaman tabanlı tutma olarak da *adlandırılan) bir* tutma süresi belirtebilirsiniz; böylece silinen ve değiştirilen üçüncü taraf verileri belirli bir süre boyunca korunur ve sonra posta kutusundan kalıcı olarak silinir. Ya da içeriği süresiz (sonsuz tutma olarak anılır *) veya* Mahkeme tutma kaldırılana kadar tutabilirsiniz.

### <a name="ediscovery"></a>eKbulma

Bu çalışma sayfalarındaki üç birincil eKöden Microsoft 365 İçerik arama, Çekirdek eKbulma ve Advanced eDiscovery.

- **[İçerik arama.](content-search.md)** İçerik arama aracını kullanarak, içe aktarılmış olan üçüncü taraf verileri için posta kutularını arayabilirsiniz. Arama sonuçlarını daraltmak ve arama sonuçlarını dışarı aktarmak için arama sorgularını ve koşulları kullanabilirsiniz.

- **[Çekirdek eKbulma](get-started-core-ediscovery.md).** Bu araç, büyük/küçük harf verilerine kimlerin eriş erişeni denetlemenizi, kullanıcı posta kutularını veya arama ölçütleriyle eşleşen posta kutusu içeriğini yerinde tutmanızı sağlayan temel arama ve dışarı aktarma işlevlerini temelden oluşturmanıza olanak sağlar. Başka bir ifadeyle, kullanıcı posta kutularına aktarılmış olan üçüncü taraf verilerine eBulma yerinde tutabilirsiniz.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** Bu güçlü araç, bir vakaya koruyucular eklemenize, özel kişi verilerini tutmanıza ve sonra da custo bir üçüncü taraf verilerini gözden geçirerek (temalar ve yinelenen algılama gibi) daha fazla çözümleme yapmak için Core eKover'ın olay işlevselliğini genişlettir. Üçüncü taraf verilerini gözden geçirme kümesine yükledikten sonra, onu sorgular ve dar bir sonuç kümesine filtreleyesiniz.

   Hem Çekirdek eBulma hem de Advanced eDiscovery, üçüncü taraf verilerini, kurumla ilgili yasal veya iç soruşturmaları ile ilgili olarak yönetmenize izin sağlar.

### <a name="retention-settings"></a>Bekletme ayarları

Bekletme süresinin sona [erdikten sonra](retention.md) üçüncü taraf verilerini (ve diğer posta kutusu içeriğini) korumak ve silmek için kullanıcı posta kutularına bekletme ilkesi uygulayabilirsiniz. Ayrıca, belirli bir yaşa sahip üçüncü taraf verilerini silmek için bekletme ilkelerini kullanabilir veya üçüncü taraf [](disposition.md) verilerin bekletme süresi dolduğunda bir saklama gözden geçirmeyi tetiklemek için bekletme etiketlerini kullanabilirsiniz.

### <a name="records-management"></a>Kayıt yönetimi

Kayıt [yönetimi özelliği](records-management.md), Microsoft 365 üçüncü taraf verilerini kayıt olarak bildirebilirsiniz. Bu, kullanıcıların posta kutularına üçüncü taraf verilerini kayıt olarak işaret eden bir bekletme etiketi uygulayan kullanıcılar tarafından el ile yapılabilir. Ya da üçüncü taraf verilerinde hassas bilgileri, anahtar sözcükleri veya içerik türlerini tanımarak bekletme etiketlerini otomatik olarak uygulayabilirsiniz.

### <a name="communication-compliance"></a>İletişim uyumluluğu

İletişim [uyumluluğunu kullanarak,](communication-compliance.md) üçüncü taraf verilerini inceleyen ve bu verilerin kurumnizin veri standartlarına uygun olduğundan emin olun. Bunu, kuruluşta uygunsuz iletileri tespit eder, yakalayarak ve düzeltme eylemleri gerçekleştirerek gerçekleştirebilirsiniz. Örneğin rahatsız edici dil, hassas bilgiler ve yasal düzenlemelere uyum için içeri aktardıkları üçüncü taraf verilerini izleyebilirsiniz.

### <a name="insider-risk-management"></a>Insider risk yönetimi

Seçmeli İk verileri gibi üçüncü taraf verilerden gelen sinyaller, [Insider risk](insider-risk-management.md) yönetimi çözümü tarafından, kuruluş içindeki riskli etkinlikleri algılamanıza, araştırmanıza ve buna göre eyleme izin vererek iç riskleri en aza indirmek için kullanılabilir. Örneğin İk veri bağlayıcısı tarafından alınan veriler, ayrılan çalışanların veri hırsızlığını algılamaya yardımcı olmak için risk göstergeleri olarak kullanılır.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Üçüncü taraf verilerini aramak için eBulma araçlarını kullanma

Veri bağlayıcılarını kullanarak kullanıcı posta kutularına üçüncü taraf verilerini aktardıktan ve arşivledikten sonra, Microsoft 365 taraf verilerini aramak için eBulma araçlarını kullanabilirsiniz. Ayrıca, üçüncü taraf verilerini korumak için, Core eDiscovery ve Advanced eDiscovery durumlarla ilişkilendirilmiş sorgu tabanlı korumalar oluşturmak için eBulma araçları da oluşturabilirsiniz. eBulma araçları hakkında daha fazla bilgi için bkz. [EBulma çözümleri ve Microsoft 365](ediscovery.md).

Veri bağlayıcısı kullanarak kullanıcı posta kutularına aktarılmış herhangi bir üçüncü taraf veri türünü aramak (veya yerinde tutmak) için, aşağıdaki arama sorgusunu kullanabilirsiniz. Arama kapsamını kullanıcı posta kutularının kapsamında olduğundan emin olun.

```powershell
kind:externaldata
```

Bu sorguyu Anahtar Sözcükler **kutusunda** İçerik araması, Çekirdek eBulma durumuyla ilişkilendirilmiş bir arama veya bir çalışma Advanced eDiscovery.

![Üçüncü taraf verilerini aramak için sorgu.](..\media\SearchThirdPartyData1.png)

Arama kapsamını üçüncü taraf `kind:externaldata` verileriyle daraltmak için de property:value pair özelliğini kullanabilirsiniz. Örneğin, alınan öğenin Konu özelliğinde *contoso* sözcüğü geçen herhangi bir üçüncü taraf veri kaynağından alınan öğeleri aramak için  Anahtar Sözcükler kutusunda aşağıdaki **sorguyu** kullanın:

```powershell
subject:contoso AND kind:externaldata
```

Alternatif olarak, aynı sorguyu **yapılandırmak için İleti** tür koşullarını kullanabilirsiniz.

![Üçüncü taraf verilerine göre aramaları daraltmak için İleti tür koşullarını kullanın.](..\media\SearchThirdPartyData2.png)

Arşivlenmiş belirli bir üçüncü taraf veri türünü aramak için, arama sorgusunda **itemclass** mailbox özelliğini kullanın. Aşağıdaki özellik:değer biçimini kullanın:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Üçüncü taraf veri bağlayıcısı tarafından alınan her öğe, üçüncü taraf veri türüne karşılık gelen bir değerle **itemclass** özelliğini içerir. Örneğin, contoso sözcüğü içeren Facebook *verilerini aramak için*, alınan öğenin **Konu** özelliğinde aşağıdaki sorguyu kullanın:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Burada, farklı türlerde **üçüncü taraf verileri** için öğe sınıfı değerleri için birkaç örnek verilmiştir.

| **Üçüncü taraf veri türü** | **Itemclass özelliğinin değeri**   |
|---------------------------|-------------------------------------|
| Bloomberg Message         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Özet                     | ipm.externaldata.pivot*            |
| WhatsApp Arşivleyicisi         | ipm.externaldata.whatsapparchiver* |
|||

*Itemclass özelliğinin değerleri* büyük/harfe duyarlı değildir. Genelde, üçüncü taraf veri türünün adını (boşluksuz) ve ardından joker karakter ( * ) karakteri kullanın.

eBulma arama sorguları oluşturma hakkında daha fazla bilgi için bkz. eBulma için anahtar [sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutunda veri bağlayıcıları

Bazı veri bağlayıcıları ABD Kamu bulutunda kullanılabilir. Aşağıdaki bölümlerde, üçüncü taraf veri bağlayıcılarını destekleyen belirli kamu ortamları belirtilmiştir. ABD Kamu bulutları hakkında daha fazla bilgi için ABD [Microsoft 365'ne bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>ABD Kamu bulutunda (önizleme) Veritas veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |GCC Yüksek  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| Evet | Hayır | Hayır |
|MS SQL'da Cisco Cisco Cisco SQL| Evet | Hayır | Hayır |
|Cisco Cisco Ciscober on Oracle| Evet | Hayır | Hayır |
|PostgreSQL'de Cisco Cisco Cisco Cisco Cisco| Evet | Hayır | Hayır |
|EML| Evet | Hayır | Hayır |
|FX Bağlan| Evet | Hayır | Hayır |
|Jive| Evet | Hayır | Hayır |
|MS SQL Veritabanı| Evet | Hayır | Hayır |
|Özet| Evet | Hayır | Hayır |
|Redtail Speak| Evet | Hayır | Hayır |
|Reuters Ilgilenme| Evet | Hayır | Hayır |
|Reuters E ilgili| Evet | Hayır | Hayır |
|Reuters FX| Evet | Hayır | Hayır |
|RingCentral| Evet | Hayır | Hayır |
|Salesforce SohbetTeri| Evet | Hayır | Hayır |
|ServiceNow| Evet | Hayır | Hayır |
|Skype Kurumsal| Evet | Hayır | Hayır |
|Slack eKovery| Evet | Hayır | Hayır |
|Burya| Evet | Hayır | Hayır |
|Metinle ayrılmış| Evet | Hayır | Hayır |
|Twitter| Evet | Hayır | Hayır |
|Webex Teams| Evet | Hayır | Hayır |
|Web sayfaları| Evet | Hayır | Hayır |
|Facebook'tan iş yeri| Evet | Hayır | Hayır |
|XIP| Evet | Hayır | Hayır |
|XSLT/XML| Evet | Hayır | Hayır |
|Ödemebroker| Evet | Hayır | Hayır |
|YouTube| Hayır | Hayır | Hayır |
|Toplantıları Yakınlaştırma| Evet | Hayır | Hayır |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>US Government bulutunda TeleMessage veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |GCC Yüksek  |DoD  |
|:---------|:---------|:---------|:---------|
|Android Arşivleyici | Evet | Hayır | Hayır |
|AT&T SMS/MMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Zil SMS/MMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Enterprise Sayı Arşivleyicisi | Evet | Hayır | Hayır |
|O2 SMS ve Voice Network Arşivleyicisi | Evet         | Hayır | Hayır |
|Rogers Network Archiver | Evet         | Hayır | Hayır |
|Sinyal Arşivleyicisi | Evet | Hayır | Hayır |
|Arşivleyici | Evet | Hayır | Hayır |
|TELUS SMS Ağ Arşivleyicisi | Evet | Hayır | Hayır |
|Verizon SMS/MMS Network Archiver | Evet | Hayır | Hayır |
|WeChat Arşivleyicisi | Evet | Hayır | Hayır |
|WhatsApp Arşivleyicisi | Evet | Hayır | Hayır |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutuna 17a-4 veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |GCC Yüksek  |DoD  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Evet | Hayır | Hayır |
|Bloomberg DataParser  | Evet | Hayır | Hayır |
|Cisco Cisco Ciscober DataParser  | Evet | Hayır | Hayır |
|Cisco Webex DataParser  | Evet | Hayır | Hayır |
|FactSet DataParser  | Evet | Hayır | Hayır |
|DataParser'ı dondurma  | Evet | Hayır | Hayır |
|FX Bağlan DataParser  | Evet | Hayır | Hayır |
|ICE DataParser  | Evet | Hayır | Hayır |
|InvestEdge DataParser  | Evet | Hayır | Hayır |
|LivePerson Conversational Cloud DataParser  | Evet | Hayır | Hayır |
|Quip DataParser  | Evet | Hayır | Hayır |
|Refinitiv Evitn Messenger DataParser  | Evet | Hayır | Hayır |
|ServiceNow DataParser  | Evet | Hayır | Hayır |
|Skype Kurumsal Sunucu Parser | Evet | Hayır | Hayır |
|Slack DataParser | Evet | Hayır | Hayır |
|SQL Parser  | Evet | Hayır | Hayır |
|Symphony DataParser | Evet | Hayır | Hayır |
|Zoom DataParser | Evet | Hayır | Hayır |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>ABD Kamu bulutuna CellTrust veri bağlayıcıları

|Veri bağlayıcısı  |GCC  |GCC Yüksek  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Evet | Hayır | Hayır |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Üçüncü taraf verilerini arşivlemek için bir Microsoft iş ortağıyla çalışma

Üçüncü taraf verilerini içeri aktarma ve arşivlemek için bir diğer seçenek de, kuruluş bir Microsoft İş Ortağı ile çalışmaktır. Üçüncü taraf bir veri türü Microsoft uyumluluk merkezinde kullanılabilen veri bağlayıcıları tarafından desteklenmiyorsa, üçüncü taraf veri kaynağından düzenli olarak öğe ayıklayacak şekilde yapılandırılan özel bir bağlayıcı sağlayılan bir iş ortağıyla çalışabilirsiniz ve sonra da üçüncü taraf API'yle Microsoft buluta bağlanın ve bu öğeleri Microsoft 365'a aktarın. İş ortağı bağlayıcısı ayrıca, üçüncü taraf veri kaynağında yer alan bir öğenin içeriğini e-posta iletisine dönüştürür ve sonra bu içeriği Microsoft 365.

Birlikte çalışabilirsiniz iş ortaklarının listesi ve bu yöntemin adım adım süreci için bkz. İş ortağıyla birlikte çalışarak üçüncü taraf verilerini [Microsoft 365.](work-with-partner-to-archive-third-party-data.md)
