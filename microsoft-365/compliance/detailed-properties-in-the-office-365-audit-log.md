---
title: Denetim günlüğünde ayrıntılı özellikler
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Bu makalede, bir denetim günlüğü kaydına ilişkin sonuçları dışarı aktararak ek Office 365 açıklamaları yer almaktadır.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1293cdda6ae99fc64b331b7e10cf827c62504456
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2022
ms.locfileid: "63016304"
---
# <a name="detailed-properties-in-the-audit-log"></a>Denetim günlüğünde ayrıntılı özellikler

Denetim günlüğü aramalarının sonuçlarını dışarı aktaran Microsoft 365 uyumluluk merkezi, arama ölçütlerinize uyan tüm sonuçları indirme seçeneğiniz vardır. Bunu yapmak için Denetim günlüğü **araması sayfasında** \> Sonuçları **dışarı aktar** Tüm sonuçları **indir'i** seçin. Daha fazla bilgi için bkz[. Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)
  
 Denetim günlüğü aramasında elde etmek istediğiniz tüm sonuçları dışarı aktarsanız bile, birleşik denetim günlüğünden gelen ham veriler yerel bilgisayarınıza indirilen virgülle ayrılmış değer (CSV) dosyasına kopyalanır. Bu dosya, Denetim Verileri adlı sütunda yer alan her denetim kaydından ek **bilgiler içerir**. Bu sütun denetim günlüğü kaydından birden çok özellik için çok değerli bir özellik içerir. Özelliğin **her biri: Bu** çok değerli özellikte yer alan değer çiftleri virgülle ayrılmıştır. 
  
Aşağıdaki tabloda, birden çok özellikli **AuditData** sütununda bulunan özellikler (olayın oluştuğu hizmete bağlı olarak) açık bulunmaktadır. Bu **Office 365 içeren grup hizmeti**, özelliği içeren hizmeti ve etkinlik türünü (kullanıcı veya yönetici) gösterir. Bu özellikler veya özellikler hakkında bu konuda listelenmiyor olmasıyla ilgili daha ayrıntılı bilgi için bkz. [Yönetim Etkinliği API Şeması](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Denetim Verileri sütununu birden çok sütuna bölmek için Excel'te Power Query'de JSON dönüştürme özelliğini kullanabilirsiniz; böylece her özelliğin kendi sütunu olur. Bu özellik, bu özelliklerden birini veya birden fazlasını sıralama ve filtrelemenizi sağlar. Bunun nasıl olduğunu öğrenmek için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md). 
  
|**Özellik**|**Açıklama**|**Microsoft 365 özelliği olan bir hizmet**|
|:-----|:-----|:-----|
|Actor|Eylemi gerçekleştirilen kullanıcı veya hizmet hesabı.|Azure Active Directory|
|AddOnName|Bir ekipte eklenen, kaldırılan veya güncelleştirilen eklentinin adı. E-posta veya Microsoft Teams bot, bağlayıcı veya sekme gibi eklenti tuşuna basın.|Microsoft Teams|
|AddOnType|Ekipte eklenen, kaldırılan veya güncelleştirilen eklentinin türü. Aşağıdaki değerler eklenti türünü gösterir.  <br/> **1** - Robotu gösterir.<br/> **2** - Bağlayıcıyı gösterir.<br/> **3** - Bir sekmeyi gösterir.|Microsoft Teams|
|AzureActiveDirectoryEventType|Olay türü Azure Active Directory. Olay türü aşağıdaki değerlerle belirtilmiştir.  <br/> **0** - Hesap oturum açma olayı gösterir.<br/> **1** - Azure uygulaması güvenlik olaylarını gösterir.|Azure Active Directory|
|ChannelGuid|Bir kanala Microsoft Teams. Kanalın bulunduğu ekip, **TeamName** ve **TeamGuid özellikleri tarafından** tanımlanır.|Microsoft Teams|
|ChannelName|Bir kanalın Microsoft Teams. Kanalın bulunduğu ekip, **TeamName** ve **TeamGuid özellikleri tarafından** tanımlanır.|Microsoft Teams|
|İstemci|Oturum açma olayında kullanılan istemci cihazı, cihaz işletim sistemi ve cihaz tarayıcısı (örneğin, Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|İşlem gerçekleştirmek için kullanılan e-posta istemcisi hakkında bilgi (örneğin, tarayıcı sürümü, Outlook sürümü ve mobil cihaz bilgileri)|Exchange kutusu etkinliği)|
|ClientIP|Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi, IPv4 veya IPv6 adres biçiminde görüntülenir.<br/><br/> Bazı hizmetlerde, bu özellikte görüntülenen değer etkinliği yapan kişi tarafından kullanılan cihazın IP adresi değil, kullanıcı adına hizmeti çağıran güvenilen bir uygulamanın IP adresi (örneğin, Web üzerinde Office uygulamaları) olabilir. <br/><br/>Ayrıca, ilgili etkinlikler için yönetici etkinliği (veya sistem hesabı tarafından gerçekleştirilen etkinlik) Azure Active Directory IP adresi günlüğe kaydedilmez ve ClientIP özelliğinin değeri yer almaktadır`null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Kullanıcının etkinliği gerçekleştirilen Eşgüdümli Evrensel Saat (UTC) tarihi ve saati.|Tümü|
|DestinationFileExtension|Kopyalanan veya taşınan dosyanın dosya uzantısı. Bu özellik yalnızca FileCopied ve FileMoved kullanıcı etkinlikleri için görüntülenir.|SharePoint|
|DestinationFileName|Kopyalanan veya taşınan dosyanın adı. Bu özellik yalnızca FileCopied ve FileMoved eylemleri için görüntülenir.|SharePoint|
|DestinationRelativeUrl|Dosyanın kopya bulunduğu veya taşındığı hedef klasörün URL'si. **SiteURL**, **DestinationRelativeURL** ve **DestinationFileName** özelliği için değerlerin bileşimi, kopyalanan dosyanın tam yol adı olan **ObjectID** özelliğiyle aynı değerdir. Bu özellik yalnızca FileCopied ve FileMoved kullanıcı etkinlikleri için görüntülenir.|SharePoint|
|EventSource|Bir olayın başka bir dosyada olduğunu SharePoint. Olası değerler En **SharePoint** **ObjectModel'dir**.|SharePoint|
|ExternalAccess|Yönetici Exchange için, cmdlet'in kuruluşta bir kullanıcı tarafından mı, Microsoft veri merkezi personeli veya veri merkezi hizmet hesabı tarafından mı, yoksa yönetici temsilcisi tarafından mı çalıştırıldı olduğunu belirtir. **False değeri**, cmdlet'in kurumdan biri tarafından çalıştırıldı olduğunu gösterir. True **değeri,** cmdlet'in veri merkezi personeli, veri merkezi hizmet hesabı veya yönetici temsilcisi tarafından çalıştır olmadığını gösterir.  <br/> Daha Exchange posta kutusu etkinliği için, posta kutusuna kuruluş dışındaki bir kullanıcı tarafından erişip erişil olmadığını belirtir.|Exchange|
|ExtendedProperties|Bir etkinlik için genişletilmiş Azure Active Directory.|Azure Active Directory|
|Kimlik|Rapor girdisi kimliği. Kimlik, rapor girdisini benzersiz olarak tanımlar.|Tümü|
|InternalLogonType|İç kullanım için ayrılmıştır.|Exchange kutusu etkinliği)|
|ItemType|Erişilen veya değiştirilen nesnenin türü. Olası değerler **şunlardır: File**, **Folder**, **Web**, **Site**, **Tenant** ve **DocumentLibrary**.|SharePoint|
|LoginStatus|Olası oturum açma hatalarını tanımlar.|Azure Active Directory|
|LogonType|Posta kutusu erişiminin türü. Aşağıdaki değerler, posta kutusuna erişen kullanıcının türünü gösterir.  <br/><br/> **0** - Posta kutusu sahibini gösterir.<br/> **1** - Yöneticiyi gösterir.<br/> **2** - Temsilciyi gösterir. <br/>**3** - Microsoft veri merkezinde aktarım hizmetini gösterir.<br/> **4** - Microsoft veri merkezinde bir hizmet hesabını gösterir. <br/>**6** - Yönetici temsilcisini gösterir.|Exchange kutusu etkinliği)|
|MailboxGuid|Erişilen Exchange kutusunun GUID'si.|Exchange kutusu etkinliği)|
|MailboxOwnerUPN|Erişilen posta kutusunun sahibi olan kişinin e-posta adresi.|Exchange kutusu etkinliği)|
|Üyeler|Ekipte eklenen veya kaldırılan kullanıcıları listeler. Aşağıdaki değerler kullanıcıya atanan Rol türünü gösterir.  <br/><br/> **1** - Sahip rolünü gösterir.<br/> **2** - Üye rolünü gösterir.<br/> **3** - Konuk rolünü gösterir. <br/><br/>Members özelliği, hem kuruluşun adını hem de üyenin e-posta adresini içerir.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Özellik, site veya site koleksiyonu yönetici grubu üyesi olarak bir kullanıcı ekleme gibi yönetici olaylarının bir özelliğidir. Özellik, değiştirilen özelliğin adını (örneğin, Site Yöneticisi grubu), değiştirilen özelliğin yeni değerini (site yöneticisi olarak eklenen kullanıcı gibi) ve değiştirilen nesnenin önceki değerini içerir.|Tüm (yönetici etkinliği)|
|ObjectId|Yönetici Exchange günlüğü kaydı için, cmdlet tarafından değiştirilen nesnenin adı.  <br/> Daha SharePoint için, kullanıcı tarafından erişilen dosya veya klasörün tam URL yol adı.  <br/> Azure AD etkinliği için, değiştirilen kullanıcı hesabının adı.|Tümü|
|Operation|Kullanıcı veya yönetici etkinliğinin adı. Bu özelliğin değeri Etkinlikler açılan listesinde seçilmiş olan **değere** karşılık geldi. Tüm **etkinlikler için sonuçları göster seçildiyse** , rapora tüm hizmetlere yönelik tüm kullanıcı ve yönetici etkinliklerine yönelik girişler yer almaktadır. Denetim günlüğüne kaydedilen işlemlerin/etkinliklerin açıklaması için, Denetim günlüğünde arama kaydında Denetlenen etkinlikler  [sekmesine Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> Yönetici Exchange için bu özellik, çalıştırıldı olan cmdlet'in adını tanımlar.|Tümü|
|OrganizationId|Kuruluş için GUID.|Tümü|
|Yol|Erişilen iletinin bulunduğu posta kutusu klasörünün adı. Bu özellik, bir iletinin oluşturulmuş veya kopyalanan/taşındığı klasörü de tanımlar.|Exchange kutusu etkinliği)|
|Parametreler|Yönetici Exchange için, Operation özelliğinde tanımlanan cmdlet'te kullanılan tüm parametrelerin adı ve değeri.|Exchange (yönetici etkinliği)|
|RecordType|Kayıt tarafından gösterilen işlem türü. Bu özellik, işlemi tetikleyen hizmeti veya özelliği gösterir. Kayıt türlerinin listesi ve buna karşılık gelen ENUM değeri (denetim kaydındaki **RecordType** özelliğinde görüntülenen değer) için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Eylemin (Operation özelliğinde belirtilen eylem) **başarılı olup** olmadığını gösterir.  <br/> Yönetici Exchange için değer True (**başarılı**) veya **False (başarısız**) olur.|Tümü  <br/>|
|SecurityComplianceCenterEventType|Etkinliğin, en son etkinlik Microsoft 365 uyumluluk merkezi gösterir. Bu özellik için tüm uyumluluk merkezi etkinliklerinin **değeri 0** olur.|Güvenlik & Uyumluluk Merkezi|
|SharingType|Kaynağın paylaşılıyor olduğu kullanıcıya atanmış olan paylaşım izinlerinin türü. Bu kullanıcı **UserSharedWith özelliğinde** tanımlanır.|SharePoint|
|Site|Kullanıcı tarafından erişilen dosya veya klasörün bulunduğu sitenin GUID'si.|SharePoint|
|SiteUrl|Kullanıcı tarafından erişilen dosya veya klasörün bulunduğu sitenin URL'si.|SharePoint|
|SourceFileExtension|Kullanıcı tarafından erişilen dosyanın dosya uzantısı. Erişilen nesne bir klasörse bu özellik boş bırakılır.|SharePoint|
|SourceFileName|Kullanıcı tarafından erişilen dosya veya klasörün adı.|SharePoint|
|SourceRelativeUrl|Kullanıcı tarafından erişilen dosyayı içeren klasörün URL'si. **SiteURL**, **SourceRelativeURL** ve **SourceFileName** özelliği için değerlerin bileşimi, kullanıcı tarafından erişilen dosyanın tam yol adı olan **ObjectID** özelliğinin değeriyle aynıdır.|SharePoint|
|Konu|Erişilen iletinin konu satırı.|Exchange kutusu etkinliği)|
|TabType| Ekipte eklenen, kaldırılan veya güncelleştirilen sekmenin türü. Bu özelliğin olası değerleri:  <br/><br/> **Excel sabitle** - Excel sekmesi.  <br/> **Uzantı** - Tüm birinci taraf ve üçüncü taraf uygulamaları; örneğin, Sınıf Programı, VSTS ve Formlar gibi.  <br/> **Notlar** - OneNote sekmesi.  <br/> **Pdfpin** - PDF sekmesi.  <br/> **Powerbi** - Power BI sekmesi.  <br/> **Powerpointpin** - PowerPoint sekmesi.  <br/> **Sharepointfiles** - SharePoint sekmesi.  <br/> **Web sayfası** - Sabitlenmiş web sitesi sekmesi.  <br/> **Wiki sekmesi** - Wiki sekmesi.  <br/> **Wordpin** - Word sekmesi.|Microsoft Teams|
|Hedef|Üzerinde eylemin ( **Operation** özelliğinde tanımlanan eylem) gerçekleştir olduğu kullanıcı. Örneğin, konuk kullanıcı bir Ekip'e SharePoint Microsoft Ekibi'ne eklenirse, bu kullanıcı bu özellikte listelenir.|Azure Active Directory|
|TeamGuid|Aynı ekipte yer alan bir Microsoft Teams.|Microsoft Teams|
|TeamName|Aynı dosyada yer alan bir ekibin Microsoft Teams.|Microsoft Teams|
|UserAgent|Kullanıcının tarayıcısı hakkında bilgiler. Bu bilgiler tarayıcı tarafından sağlanır.|SharePoint|
|UserDomain|Eylemi gerçekleştiren kullanıcının (Actor) kiracı kuruluşu hakkında kimlik bilgileri.|Azure Active Directory|
|UserId|Kaydın günlüğe kaydedilmiş olmasıyla sonuç veren eylemi ( **Operation** özelliğinde belirtilen eylem) gerçekleştiren kullanıcı. Sistem hesapları (SHAREPOINT\system veya NT AUTHORITY\SYSTEM gibi) tarafından gerçekleştirilen etkinliğin denetim kayıtları da denetim günlüğüne dahil edilir. UserId özelliği için başka bir ortak değer app@sharepoint. Bu, etkinliği gerçekleştiren "kullanıcının" kullanıcı, yönetici veya hizmet adına kuruluş genelinde eylemler (SharePoint sitesinde veya SharePoint OneDrive hesabında arama yapmak gibi) gerçekleştirmek için SharePoint'de gerekli izinlere sahip bir uygulama olduğunu gösterir. <br/><br/>Daha fazla bilgi için bkz.:<br/> [Denetim kayıtlarında\@ appsharepoint kullanıcısı](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> veya <br/>[Posta kutusu denetim Exchange için sistem hesapları](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Tümü|
|UserKey|UserID özelliğinde tanımlanan kullanıcının alternatif kimliği. Örneğin, bu özellik aynı bölgede yer alan kullanıcılar tarafından gerçekleştirilen olaylar için Passport benzersiz kimliğiyle (PUID) SharePoint. Bu özellik, başka hizmetlerde oluşan olaylar ve sistem hesapları tarafından gerçekleştirilen olaylar için **UserID** özelliğiyle aynı değeri de belirtebilirsiniz.|Tümü|
|UserSharedWith|Bir kaynağın paylaşıldı olduğu kullanıcı. **Operation** özelliğinin değeri SharingSet ise, bu özellik **dahil edilir**. Bu kullanıcı, rapordaki **Paylaşılan sütununda** da listelenir.|SharePoint|
|UserType|İşlemleri gerçekleştirilen kullanıcının türü. Kullanıcı türü aşağıdaki değerlerle belirtilmiştir. <br/> <br/> **0** - Normal bir kullanıcı. <br/>**2** - Bir iş Microsoft 365 yöneticisi.<sup> 1</sup> <br/>**3** - Microsoft veri merkezi yöneticisi veya veri merkezi sistem hesabı. <br/>**4** - Sistem hesabı. <br/>**5** - Uygulama. <br/>**6** - Hizmet sorumlusu.<br/>**7** - Özel ilke.<br/>**8** - Sistem ilkesi.|Tümü|
|Sürüm|Günlüğe kaydedilen etkinliğin ( **Operation** özelliği tarafından tanımlanan etkinlik) sürüm numarasını gösterir.|Tümü|
|workload|Etkinliğin Microsoft 365 hizmetidir.|Tümü|
||||

> [!NOTE]
><sup>1</sup> Azure Active Directory ilgili olaylar için, yöneticinin değeri denetim kaydında kullanılmaz. Yöneticiler tarafından gerçekleştirilen etkinliklerin denetim kayıtları, normal bir kullanıcının (örneğin, **UserType: 0**) etkinliği gerçekleştirileni gösterir. **UserID özelliği**, etkinliği gerçekleştiren kişiyi (normal kullanıcı veya yönetici) gösterir.
