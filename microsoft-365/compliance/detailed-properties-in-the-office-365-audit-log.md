---
title: Denetim günlüğündeki ayrıntılı özellikler
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: Bu makalede, bir Office 365 denetim günlüğü kaydının sonuçlarını dışarı aktarırken eklenen ek özelliklerin açıklamaları sağlanır.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66928de026e95fbbb02f1a3e7d0efd3da0766afd
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623285"
---
# <a name="detailed-properties-in-the-audit-log"></a>Denetim günlüğündeki ayrıntılı özellikler

denetim günlüğü aramasının sonuçlarını Microsoft Purview uyumluluk portalı dışarı aktardığınızda, arama ölçütlerinize uyan tüm sonuçları indirme seçeneğiniz vardır. Bunu yapmak için Sonuçları \> **dışarı aktar** **Denetim günlüğü arama** sayfasında **Tüm sonuçları indir'i** seçin. Daha fazla bilgi için bkz [. Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.
  
 Bir denetim günlüğü araması için tüm sonuçları dışarı aktardığınızda, birleşik denetim günlüğündeki ham veriler yerel bilgisayarınıza indirilen virgülle ayrılmış değer (CSV) dosyasına kopyalanır. Bu dosya **, AuditData** adlı bir sütundaki her denetim kaydından ek bilgiler içerir. Bu sütun, denetim günlüğü kaydından birden çok özellik için çok değerli bir özellik içerir. **Özelliğin** her biri: bu çok değerli özellikteki değer çiftleri virgülle ayrılır. 
  
Aşağıdaki tabloda, çok özellikli **AuditData** sütununa dahil edilen özellikler (bir olayın gerçekleştiği hizmete bağlı olarak) açıklanmaktadır. **Bu özellik sütununa sahip Office 365 hizmeti**, özelliği içeren hizmet ve etkinlik türünü (kullanıcı veya yönetici) gösterir. Bu özellikler veya bu konuda listelenmeyecek özellikler hakkında daha ayrıntılı bilgi için bkz. [Yönetim Etkinliği API Şeması](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Excel'de Power Query JSON dönüştürme özelliğini kullanarak **AuditData** sütununu birden çok sütuna bölerek her özelliğin kendi sütununa sahip olmasını sağlayabilirsiniz. Bu, bu özelliklerden birini veya daha fazlasını sıralamanıza ve filtrelemenize olanak tanır. Bunun nasıl yapılacağını öğrenmek için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md). 
  
|**Özellik**|**Açıklama**|**Bu özelliğe sahip Microsoft 365 hizmeti**|
|:-----|:-----|:-----|
|Aktör|Eylemi gerçekleştiren kullanıcı veya hizmet hesabı.|Azure Active Directory|
|AddOnName|Ekipte eklenen, kaldırılan veya güncelleştirilen bir eklentinin adı. Microsoft Teams'deki eklentilerin türü bir bot, bağlayıcı veya sekmedir.|Microsoft Teams|
|AddOnType|Ekipte eklenen, kaldırılan veya güncelleştirilen bir eklentinin türü. Aşağıdaki değerler eklentinin türünü gösterir.  <br/> **1** - Botu gösterir.<br/> **2** - Bağlayıcıyı gösterir.<br/> **3** - Sekmeyi gösterir.|Microsoft Teams|
|AzureActiveDirectoryEventType|Azure Active Directory olayının türü. Aşağıdaki değerler olayın türünü gösterir.  <br/> **0** - Hesap oturum açma olayını gösterir.<br/> **1** - Azure uygulama güvenliği olayını gösterir.|Azure Active Directory|
|ChannelGuid|Microsoft Teams kanalının kimliği. Kanalın bulunduğu ekip **TeamName** ve **TeamGuid** özellikleriyle tanımlanır.|Microsoft Teams|
|Channelname|Microsoft Teams kanalının adı. Kanalın bulunduğu ekip **TeamName** ve **TeamGuid** özellikleriyle tanımlanır.|Microsoft Teams|
|İstemci|İstemci cihazı, cihaz işletim sistemi ve oturum açma olayı için kullanılan cihaz tarayıcısı (örneğin, Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|tarayıcı sürümü, Outlook sürümü ve mobil cihaz bilgileri gibi işlemi gerçekleştirmek için kullanılan e-posta istemcisi hakkında bilgiler|Exchange (posta kutusu etkinliği)|
|ClientIP|Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi IPv4 veya IPv6 adres biçiminde görüntülenir.<br/><br/> Bazı hizmetler için, bu özellikte görüntülenen değer, etkinliği gerçekleştiren kişinin kullandığı cihazın IP adresi değil, kullanıcı adına hizmete çağrı yapan güvenilir bir uygulamanın IP adresi (örneğin, Web üzerinde Office uygulamalar) olabilir. <br/><br/>Ayrıca, Azure Active Directory ile ilgili olaylar için yönetici etkinliği (veya bir sistem hesabı tarafından gerçekleştirilen etkinlik) için IP adresi günlüğe kaydedilmez ve ClientIP özelliğinin değeri olur `null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Kullanıcının etkinliği gerçekleştirdiği Eşgüdümlü Evrensel Saat (UTC) içindeki tarih ve saat.|Tümü|
|DestinationFileExtension|Kopyalanan veya taşınan bir dosyanın dosya uzantısı. Bu özellik yalnızca FileCopied ve FileMoved kullanıcı etkinlikleri için görüntülenir.|SharePoint|
|Destinationfilename|Dosyanın adı kopyalanır veya taşınır. Bu özellik yalnızca FileCopied ve FileMoved eylemleri için görüntülenir.|SharePoint|
|DestinationRelativeUrl|Bir dosyanın kopyalandığı veya taşındığı hedef klasörün URL'si. **SiteURL**, **DestinationRelativeURL** ve **DestinationFileName** özelliğinin değerlerinin birleşimi, kopyalanan dosyanın tam yol adı olan **ObjectID** özelliğinin değeriyle aynıdır. Bu özellik yalnızca FileCopied ve FileMoved kullanıcı etkinlikleri için görüntülenir.|SharePoint|
|EventSource|SharePoint'te bir olayın gerçekleştiğini tanımlar. Olası değerler **SharePoint** ve **ObjectModel'dır**.|SharePoint|
|ExternalAccess|Exchange yönetici etkinliği için, cmdlet'in kuruluşunuzdaki bir kullanıcı, Microsoft veri merkezi personeli veya veri merkezi hizmet hesabı ya da temsilci yönetici tarafından çalıştırılıp çalıştırılmadığını belirtir. **False** değeri, cmdlet'in kuruluşunuzdaki biri tarafından çalıştırıldığını gösterir. **True** değeri, cmdlet'in veri merkezi personeli, veri merkezi hizmet hesabı veya yönetici temsilcisi tarafından çalıştırıldığını gösterir.  <br/> Exchange posta kutusu etkinliği için, posta kutusuna kuruluşunuzun dışındaki bir kullanıcı tarafından erişilip erişilemediğini belirtir.|Exchange|
|ExtendedProperties|Azure Active Directory olayının genişletilmiş özellikleri.|Azure Active Directory|
|Kimlik|Rapor girdisinin kimliği. Kimlik, rapor girdisini benzersiz olarak tanımlar.|Tümü|
|InternalLogonType|dahili kullanım için ayrılmıştır.|Exchange (posta kutusu etkinliği)|
|Itemtype|Erişilen veya değiştirilen nesnenin türü. Olası değerler **Dosya**, **Klasör**, **Web**, **Site**, **Kiracı** ve **DocumentLibrary'yi** içerir.|SharePoint|
|Loginstatus|Oluşmuş olabilecek oturum açma hatalarını tanımlar.|Azure Active Directory|
|LogonType|Posta kutusu erişiminin türü. Aşağıdaki değerler, posta kutusuna erişen kullanıcının türünü gösterir.  <br/><br/> **0** - Posta kutusu sahibini gösterir.<br/> **1** - Bir yöneticiyi gösterir.<br/> **2** - Bir temsilciyi gösterir. <br/>**3** - Microsoft veri merkezinde taşıma hizmetini gösterir.<br/> **4** - Microsoft veri merkezinde bir hizmet hesabını gösterir. <br/>**6** - Yönetici temsilcisini gösterir.|Exchange (posta kutusu etkinliği)|
|MailboxGuid|Erişilen posta kutusunun Exchange GUID'i.|Exchange (posta kutusu etkinliği)|
|MailboxOwnerUPN|Erişilen posta kutusunun sahibi olan kişinin e-posta adresi.|Exchange (posta kutusu etkinliği)|
|Üyeler|Takıma eklenen veya takımdan kaldırılan kullanıcıları listeler. Aşağıdaki değerler kullanıcıya atanan Rol türünü gösterir.  <br/><br/> **1** - Sahip rolünü gösterir.<br/> **2** - Üye rolünü gösterir.<br/> **3** - Konuk rolünü gösterir. <br/><br/>Members özelliği, kuruluşunuzun adını ve üyenin e-posta adresini de içerir.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Bu özellik, bir kullanıcıyı bir sitenin veya site koleksiyonu yönetici grubunun üyesi olarak ekleme gibi yönetici olayları için dahil edilir. özelliği değiştirilen özelliğin adını (örneğin, Site Yönetici grubu) değiştirilen özelliğin yeni değerini (site yöneticisi olarak eklenen kullanıcı ve değiştirilen nesnenin önceki değeri gibi) içerir.|Tümü (yönetici etkinliği)|
|Objectıd|Exchange yöneticisi denetim günlüğü için, cmdlet'i tarafından değiştirilen nesnenin adı.  <br/> SharePoint etkinliği için, bir kullanıcı tarafından erişilen dosyanın veya klasörün tam URL yolu adı.  <br/> Azure AD etkinliği için, değiştirilen kullanıcı hesabının adı.|Tümü|
|Işlem|Kullanıcı veya yönetici etkinliğinin adı. Bu özelliğin değeri **, Etkinlikler** açılan listesinde seçilen değere karşılık gelir. **Tüm etkinlikler için sonuçları göster** seçiliyse, rapor tüm hizmetlere yönelik tüm kullanıcı ve yönetici etkinliklerine yönelik girdiler ekler. Denetim günlüğüne kaydedilen işlemlerin/etkinliklerin açıklaması için, [Office 365 Denetim günlüğünde arama'nın](search-the-audit-log-in-security-and-compliance.md) **Denetlenen etkinlikler** sekmesine bakın.  <br/> Exchange yönetici etkinliği için bu özellik, çalıştırılan cmdlet'in adını tanımlar.|Tümü|
|OrganizationId|Kuruluşunuzun GUID değeri.|Tümü|
|Yol|Erişilen iletinin bulunduğu posta kutusu klasörünün adı. Bu özellik, içinde iletinin oluşturulduğu veya kopyalandığı/taşındığı klasörü de tanımlar.|Exchange (posta kutusu etkinliği)|
|Parametre|Exchange yönetici etkinliği için, Operation özelliğinde tanımlanan cmdlet ile kullanılan tüm parametrelerin adı ve değeri.|Exchange (yönetici etkinliği)|
|Kayıt Türü|Kayıt tarafından belirtilen işlem türü. Bu özellik, işlemin tetiklediği hizmeti veya özelliği gösterir. Kayıt türlerinin listesi ve buna karşılık gelen ENUM değeri (bir denetim kaydındaki **RecordType** özelliğinde görüntülenen değerdir) için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Eylemin ( **Operation** özelliğinde belirtilen) başarılı olup olmadığını gösterir.  <br/> Exchange yönetici etkinliği için değer **True** (başarılı) veya **False** (başarısız) olur.|Tümü  <br/>|
|SecurityComplianceCenterEventType|Etkinliğin bir uyumluluk portalı olayı olduğunu gösterir. Tüm uyumluluk merkezi etkinlikleri bu özellik için **0** değerine sahip olacaktır.|Güvenlik & Uyumluluk Merkezi|
|SharingType|Kaynağın paylaşıldığı kullanıcıya atanan paylaşım izinlerinin türü. Bu kullanıcı **UserSharedWith** özelliğinde tanımlanır.|SharePoint|
|Site|Kullanıcı tarafından erişilen dosya veya klasörün bulunduğu sitenin GUID'i.|SharePoint|
|Siteurl|Kullanıcı tarafından erişilen dosya veya klasörün bulunduğu sitenin URL'si.|SharePoint|
|SourceFileExtension|Kullanıcı tarafından erişilen dosyanın dosya uzantısı. Erişilen nesne bir klasörse bu özellik boş olur.|SharePoint|
|Sourcefilename|Kullanıcı tarafından erişilen dosya veya klasörün adı.|SharePoint|
|SourceRelativeUrl|Kullanıcı tarafından erişilen dosyayı içeren klasörün URL'si. **SiteURL**, **SourceRelativeURL** ve **SourceFileName** özelliğinin değerlerinin birleşimi, kullanıcı tarafından erişilen dosyanın tam yol adı olan **ObjectID** özelliğinin değeriyle aynıdır.|SharePoint|
|Konu|Erişilen iletinin konu satırı.|Exchange (posta kutusu etkinliği)|
|TabType| Ekipte eklenen, kaldırılan veya güncelleştirilen sekme türü. Bu özelliğin olası değerleri şunlardır:  <br/><br/> **Excel pin** - Excel sekmesi.  <br/> **Uzantı** - Tüm birinci taraf ve üçüncü taraf uygulamaları; Sınıf Zamanlaması, VSTS ve Formlar gibi.  <br/> **Notlar** - OneNote sekmesi.  <br/> **Pdfpin** - PDF sekmesi.  <br/> **Powerbi** - Power BI sekmesi.  <br/> **Powerpointpin** - PowerPoint sekmesi.  <br/> **Sharepointfiles** - SharePoint sekmesi.  <br/> **Web sayfası** - Sabitlenmiş bir web sitesi sekmesi.  <br/> **Wiki-sekmesi** - Wiki sekmesi.  <br/> **Wordpin** - Word sekmesi.|Microsoft Teams|
|Hedef|Eylemin ( **Operation** özelliğinde tanımlanan) gerçekleştirildiği kullanıcı. Örneğin, SharePoint'e veya Microsoft Ekibi'ne bir konuk kullanıcı eklenirse, bu kullanıcı bu özellikte listelenir.|Azure Active Directory|
|TeamGuid|Microsoft Teams'de bir ekibin kimliği.|Microsoft Teams|
|TeamName|Microsoft Teams'deki bir ekibin adı.|Microsoft Teams|
|Useragent|Kullanıcının tarayıcısı hakkında bilgi. Bu bilgiler tarayıcı tarafından sağlanır.|SharePoint|
|UserDomain|Eylemi gerçekleştiren kullanıcının (aktör) kiracı kuruluşu hakkında kimlik bilgileri.|Azure Active Directory|
|Userıd|Kaydın günlüğe kaydedilmesiyle sonuçlanan eylemi gerçekleştiren kullanıcı ( **Operation** özelliğinde belirtilir). Sistem hesapları (SHAREPOINT\system veya NT AUTHORITY\SYSTEM gibi) tarafından gerçekleştirilen etkinliğin denetim kayıtları da denetim günlüğüne eklenir. UserId özelliği için bir diğer yaygın değer de app@sharepoint. Bu, etkinliği gerçekleştiren "kullanıcının" sharepoint'te kullanıcı, yönetici veya hizmet adına kuruluş genelinde eylemler (SharePoint sitesinde veya OneDrive hesabında arama yapma gibi) gerçekleştirmek için gerekli izinlere sahip bir uygulama olduğunu gösterir. <br/><br/>Daha fazla bilgi için bkz.:<br/> [Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> veya <br/>[Exchange posta kutusu denetim kayıtlarındaki sistem hesapları](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Tümü|
|UserKey|**UserID** özelliğinde tanımlanan kullanıcı için alternatif bir kimlik. Örneğin, bu özellik SharePoint'te kullanıcılar tarafından gerçekleştirilen olaylar için pasaport benzersiz kimliği (PUID) ile doldurulur. Bu özellik, sistem hesapları tarafından gerçekleştirilen diğer hizmetlerde ve olaylarda gerçekleşen olaylar için **UserID** özelliğiyle aynı değeri de belirtebilir.|Tümü|
|UserSharedWith|Kaynağın paylaşıldığı kullanıcı. **Operation** özelliğinin değeri **SharingSet** ise bu özellik eklenir. Bu kullanıcı, rapordaki **Paylaşılan** sütununda da listelenir.|SharePoint|
|Usertype|İşlemi gerçekleştiren kullanıcının türü. Aşağıdaki değerler kullanıcı türünü gösterir. <br/> <br/> **0** - Normal bir kullanıcı. <br/>**2** - Microsoft 365 kuruluşunuzda bir yönetici. <sup>1</sup> <br/>**3** - Microsoft veri merkezi yöneticisi veya veri merkezi sistem hesabı. <br/>**4** - Bir sistem hesabı. <br/>**5** - Bir uygulama. <br/>**6** - Hizmet sorumlusu.<br/>**7** - Özel bir ilke.<br/>**8** - Sistem ilkesi.|Tümü|
|Sürüm|Günlüğe kaydedilen etkinliğin sürüm numarasını ( **Operation** özelliğiyle tanımlanır) gösterir.|Tümü|
|Iş yük -ünü|Etkinliğin gerçekleştiği Microsoft 365 hizmeti.|Tümü|
||||

> [!NOTE]
><sup>1</sup> Azure Active Directory ile ilgili olaylar için yöneticinin değeri denetim kaydında kullanılmaz. Yöneticiler tarafından gerçekleştirilen etkinliklerin denetim kayıtları, etkinliği normal bir kullanıcının (örneğin, **UserType: 0**) gerçekleştirdiğini gösterir. **UserID** özelliği, etkinliği gerçekleştiren kişiyi (normal kullanıcı veya yönetici) tanımlar.
