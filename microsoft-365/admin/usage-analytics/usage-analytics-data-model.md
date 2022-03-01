---
title: Microsoft 365 kullanım analizi veri modeli
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 08c5307c-4a6b-4761-8410-a6c96725760f
description: "Kullanım analizinin BIR API'ye nasıl bağlanarak çeşitli veri hizmetleriyle ilgili aylık kullanım Microsoft 365 öğrenin.  "
ms.openlocfilehash: 013fdd75063ad8ad2489ebe43c9091f05f94c14c
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027535"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Microsoft 365 kullanım analizi veri modeli

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Microsoft 365 kullanım analizi tablolarına yönelik veriler

Microsoft 365 çözümleme, çok boyutlu bir veri modelini ortaya çıkarırken bir API'ye bağlanır. Veri oluşturmak Microsoft 365 kullanım analizini kullanan API'ler, genel kullanıma açık çeşitli API'lerden Graph kaynaktır. Tek başına Microsoft 365 kullanım analizi API'lerinin işlevi genel olarak kullanılamaz.
  
> [!NOTE]
> Daha fazla bilgi için bkz[. Microsoft Microsoft 365 raporlarında çalışma Graph](/graph/api/resources/report). 
  
Bu API, çeşitli veri hizmetlerini aylık kullanım eğilimi hakkında bilgi Microsoft 365 sağlar. API'ler tarafından tam olarak hangi verilerin döndürüldüğünü görmek için aşağıdaki bölümde yer alan tabloya başvurun.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Microsoft 365 Raporlama API'si tarafından döndürülen veri tabloları

|**Tablo adı**|**Tablodaki bilgiler**|**Tarih aralığı**|
|:-----|:-----|:-----|
|Kiracı Ürün Kullanımı  <br/> |Etkinleştirilmiş, etkin kullanıcıların, aydan aya korunur kullanıcıların, ilk kez kullananların ve kümülatif etkin kullanıcıların aylık toplamlarını içerir.  <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı Ürün Etkinliği  <br/> |Ürünler içindeki çeşitli etkinlikler için aylık toplam etkinlikleri ve etkin kullanıcı sayısını içerir.  <br/> Bu veri tablosunda döndürülen ürün etkinlikleri hakkında bilgi edinmek için bkz. [etkin kullanıcı tanımı](active-user-in-usage-reports.md).      <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı Office Lisansları  <br/> |Kullanıcılara atanan Microsoft Office aboneliklerinin sayısı hakkında veri içerir  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Posta Kutusu Kullanımı  <br/> |Toplam posta kutusu sayısı ve depolamanın nasıl kullanıldıkları için kullanıcının posta kutusuyla ilgili verileri içerir.  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı İstemci Kullanımı  <br/> |Exchange Online, Skype Kurumsal ve Yammer'a bağlanmak için etkin olarak belirli istemcileri/cihazları kullanan kullanıcı sayısı hakkındaki verileri içerir.  <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı SharePoint Online Kullanımı  <br/> |SharePoint siteleri hakkında, Takım veya Gruplar sitelerini kapsayan toplam site sayısı, sitedeki belge sayısı, etkinlik türüne göre dosya sayısı ve kullanılan depolama alanı gibi verileri içerir.  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı OneDrive İş Kullanımı  <br/> |OneDrive hesaplarıyla ilgili olarak hesap sayısı, OneDrive'lardaki belge sayısı, kullanılan depolama alanı, etkinlik türüne göre dosya sayısı gibi verileri içerir.  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Microsoft 365 Grupları Kullanımı  <br/> |Posta Kutusu, Microsoft 365 Kutusu ve Posta Kutusu gibi Grup kullanımı SharePoint verileri Yammer.  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Office Etkinleştirmesi  <br/> |Office aboneliği etkinleştirme sayısı, cihaz (Android/iOS/Mac/PC) başına etkinleştirme sayısı, hizmet planı (örneğin, Kurumlar için Microsoft 365 Uygulamaları, Visio, Project) başına etkinleştirme sayısı hakkında Project.  <br/> |Geçerli kısmi ay dahil olacak şekilde kayan 12 aylık bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kullanıcı Durumu  <br/> |Kullanıcı görünen adı, kullanıcıya atanan ürünler, konum, bölüm, unvan, şirket dahil olmak üzere kullanıcılarla ilgili meta veriler içerir. Bu veriler, son tam ay içinde lisans atanan kullanıcılarla ilgilidir. Her kullanıcı bir kullanıcı kimliğiyle benzersiz olarak temsil edildi.  <br/> |Bu veriler, son tam ay içinde bir lisans atanmış kullanıcılarla ilgilidir.  <br/> |
|Kullanıcı Etkinliği  <br/> |Lisanslı kullanıcılar tarafından gerçekleştirilen etkinlikler hakkında kullanıcı başına düzeyinde bilgiler içerir.  <br/> Bu veri tablosunda döndürülen ürün etkinlikleri hakkında bilgi edinmek için bkz. [etkin kullanıcı tanımı](active-user-in-usage-reports.md).      <br/> |Bu veriler, son tam ay içinde hizmetlerin herhangi birinde etkinlik gerçekleştirmiş kullanıcılarla ilgilidir.  <br/> |
   
Her veri tablosuyla ilgili ayrıntılı bilgi görüntülemek için aşağıdaki bölümleri genişletin.
  
### <a name="data-table---user-state"></a>Veri tablosu - Kullanıcı Durumu

Bu tablo, son tam ay içinde lisans atanmış tüm kullanıcılar için kullanıcı düzeyi ayrıntıları sağlar. Azure Active Directory'den veri alır.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|UserId  <br/> |Bir kullanıcıyı temsil eden ve veri kümesi içindeki diğer veri tablolarına katılmayı sağlayan benzersiz kullanıcı kimliği.  <br/> |
|Timeframe  <br/> |Bu tablonun hangi aya ait verileri içerdiğini gösteren değer.  <br/> |
|UPN  <br/> |Diğer dış veri kaynaklarıyla birleştirebilmek amacıyla kullanıcıyı benzersiz olarak tanımlayan kullanıcı asıl adı.  <br/> |
|DisplayName  <br/> |Kullanıcının görünen adı.  <br/> |
|IDType  <br/> |Kimlik türü, kullanıcı Yammer kimliğini kullanarak bağlanan bir Yammer kullanıcı ise 1 olarak, Yammer Kimliği'Yammer bağlanıyorsa 0 olarak Microsoft 365 ayarlanır.  <br/> Değer, bu kullanıcının Yammer kimliğiyle değil de Yammer kimliğiyle bağlandığını temsil Microsoft 365.  <br/> |
|HasLicenseEXO  <br/> |Kullanıcıya bir lisans atanmışsa ve kullanıcıya Exchange ayın son günü etkinse true olarak ayarlanır.  <br/> |
|HasLicenseODB  <br/> |Kullanıcıya bir lisans atanmışsa ve kullanıcıya OneDrive İş ayın son günü etkinse true olarak ayarlanır.  <br/> |
|HasLicenseSPO  <br/> |Kullanıcıya bir lisans atanmışsa ve SharePoint Online kullanımı ayın son günü etkinleştirildiyse true olarak ayarlanır.  <br/> |
|HasLicenseYAM  <br/> |Kullanıcıya bir lisans atanmışsa ve kullanıcıya Yammer ayın son günü true olarak ayarlanır.  <br/> |
|HasLicenseSFB  <br/> |Kullanıcıya bir lisans atanmışsa ve kullanıcıya Skype ayın son günü Kurumsal'ın kullanımı etkinleştirilmişse true olarak ayarlanır.  <br/> |
|HasLicenseTeams  <br/> |Kullanıcıya bir lisans atanmışsa ve kullanıcıya Microsoft Teams true olarak ayarlanır.  <br/> |
|Şirket  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen şirket verileri.  <br/> |
|Bölüm  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen bölüm verileri.  <br/> |
|LocationCity  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen şehir verileri.  <br/> |
|LocationCountry  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen ülke verileri.  <br/> |
|LocationState  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen eyalet verileri.  <br/> |
|LocationOffice  <br/> |Kullanıcının ofisi.  <br/> |
|Başlık  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen unvan verileri.  <br/> |
|Silindi  <br/> |Kullanıcı ilgili son tam ay içinde Microsoft 365 doğru olarak silinmişse.  <br/> |
|DeletedDate  <br/> |Kullanıcının dosyadan silindikten sonra Microsoft 365.  <br/> |
|YAM_State  <br/> |Kullanıcının sistem sistemi Yammer, etkin, silinmiş veya askıya alınmış olabilir.  <br/> |
|YAM_ActivationDate  <br/> |Kullanıcının Yammer'da etkin durumuna geçtiği tarih.  <br/> |
|YAM_DeletionDate  <br/> |Kullanıcının Yammer'da silinmiş durumuna geçtiği tarih.  <br/> |
|YAM_SuspensionDate  <br/> |Kullanıcının Yammer'da askıya alınmış durumuna geçtiği tarih.  <br/> |
   
### <a name="data-table---user-activity"></a>Veri tablosu - Kullanıcı Etkinliği

Bu tablo, önceki ay içinde hizmetlerin herhangi birinde etkinlik gerçekleştirmiş her bir kullanıcıyla ilgili veriler içerir.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|UserID  <br/> |Bir kullanıcıyı temsil eden ve veri kümesi içindeki diğer veri tablolarına katılmayı sağlayan benzersiz kullanıcı kimliği.  <br/> |
|IDType  <br/> |Kimlik türü, kullanıcı Yammer kimliğini kullanarak bağlanan bir Yammer kullanıcı ise 1 olarak, Yammer Kimliği'Yammer bağlanıyorsa 0 olarak Microsoft 365 ayarlanır.  <br/> Değer, bu kullanıcının Yammer kimliğiyle değil de Yammer kimliğiyle bağlandığını temsil Microsoft 365.  <br/> |
|Timeframe  <br/> |Bu tablonun hangi aya ait verileri temsil ettiğini gösteren değer.  <br/> |
|EXO_EmailSent  <br/> |Gönderilen e-posta sayısı.  <br/> |
|EXO_EmailReceived  <br/> |Alınan e-posta sayısı.  <br/> |
|EXO_EmailRead  <br/> |Kullanıcının gerçekleştirilen etkinlik okuma sayısı, zaten okunan veya daha önce alınan bir e-postayı birden çok kez okuyor olabilir.  <br/> |
|EXO_AppointmentCreated  <br/> |Oluşturulan randevu sayısı.  <br/> |
|EXO_MeetingAccepted  <br/> |Kabul edilen toplantı sayısı.  <br/> |
|EXO_MeetingCancelled  <br/> |İptal edilen toplantı sayısı.  <br/> |
|EXO_MeetingDeclined  <br/> |Reddedilen toplantı sayısı.  <br/> |
|EXO_MeetingSent  <br/> |Gönderilen toplantı sayısı.  <br/> |
|ODB_FileViewedModified  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabında etkileşim gerçekleştirdiği (örneğin, oluşturduğu, güncelleştirdiği, sildiği, görüntülediği veya indirdiği) dosya sayısı.  <br/> |
|ODB_FileSynched  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabında eşitlediği dosya sayısı.  <br/> |
|ODB_FileSharedInternally  <br/> |Bu kullanıcının herhangi bir şirket içinde veya grup OneDrive İş kullanıcılarla (dış kullanıcılar da dahil) paylaştığı dosya sayısı.  <br/> |
|ODB_FileSharedExternally  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabından şirket dışında paylaştığı dosya sayısı.  <br/> |
|ODB_AccessedByOwner  <br/> |Kullanıcının kendi etki alanı içinde bulunan ve etkileşim  ettiği site OneDrive İş.  <br/> |
|ODB_AccessedByOthers  <br/> |Bu kullanıcının başka bir kullanıcının hesabı üzerinde bulunan ve etkileşim  ettiği site OneDrive İş.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Bu kullanıcının herhangi bir grup sitesinde etkileşim edte olduğu dosya sayısı.  <br/> |
|SPO_GroupFileSynched  <br/> |Bu kullanıcının herhangi bir grup sitesinde eşitlediği dosya sayısı.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Kuruluş içindeki kullanıcılarla veya gruplarda bulunan kullanıcılarla (dış kullanıcılar da dahil) paylaşılan dosyaların sayısı.  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Bu kullanıcının herhangi bir grup sitesinden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Kullanıcının sahip olduğu bir grup sitesinde bulunan ve etkileşim  ettiği site sayısı.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Başka bir kullanıcıya ait bir grup sitesinde bulunan ve kullanıcının etkileşim  ettiği site sayısı.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Herhangi bir sitede bulunan ve bu kullanıcının etkileşim gerçekleştirdiği dosya sayısı.  <br/> |
|SPO_OtherFileSynched  <br/> |Bu kullanıcının herhangi bir siteden eşitlediği dosya sayısı.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Bu kullanıcının herhangi bir siteden şirket içinde veya gruplarda yer alan kullanıcılarla (dış kullanıcılar da dahil olabilir) paylaştığı dosya sayısı. <br/> |
|SPO_OtherFileSharedExternally  <br/> |Bu kullanıcının herhangi bir siteden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Kullanıcının sahip olduğu diğer sitede bulunan ve etkileşim gerçekleştirdiği site sayısı.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Başka bir kullanıcıya ait bir sitede bulunan ve kullanıcının etkileşim gerçekleştirdiği site sayısı.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Herhangi bir ekip sitesinde bulunan ve bu kullanıcının etkileşim gerçekleştirdiği dosya sayısı.  <br/> |
|SPO_TeamFileSynched  <br/> |Bu kullanıcının herhangi bir ekip sitesinden eşitlediği dosya sayısı.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Bu kullanıcının herhangi bir ekip sitesinden şirket içinde paylaştığı veya grup içindeki kullanıcılarla (dış kullanıcılar da dahil olabilir) paylaştığı dosya sayısı.  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Bu kullanıcının herhangi bir ekip sitesinden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Kullanıcının sahip olduğu bir ekip sitesinde bulunan ve etkileşim  ettiği site sayısı.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Başka bir kullanıcıya ait bir ekip sitesinde bulunan ve kullanıcının etkileşim  ettiği site sayısı.  <br/> |
|Teams_ChatMessages  <br/> |Gönderilen sohbet iletisi sayısı.  <br/> |
|Teams_ChannelMessage  <br/> |Kanallara gönderilen ileti sayısı.  <br/> |
|Teams_CallParticipate  <br/> |Kullanıcının katıldığı çağrı sayısı.  <br/> |
|Teams_MeetingParticipate  <br/> |Kullanıcının katıldığı toplantı sayısı.  <br/> |
|Teams_HasOtherAction  <br/> |Kullanıcı Microsoft Teams'de diğer eylemler gerçekleştirdiğinde Boole değeri.  <br/> |
|YAM_MessagePost  <br/> |Bu Yammer gönderilen ileti sayısı.  <br/> |
|YAM_MessageLiked  <br/> |Bu kullanıcının Yammer beğendiğini ileti sayısı.  <br/> |
|YAM_MessageRead  <br/> |Bu Yammer okuduğu ileti sayısı.  <br/> |
|SFB_P2PSummary  <br/> |Bu kullanıcının katıldığı eşler arası oturum sayısı.  <br/> |
|SFB_ConfOrgSummary  <br/> |Bu kullanıcının düzenlediği konferans oturumu sayısı.  <br/> |
|SFB_ConfPartSummary  <br/> |Bu kullanıcının katıldığı konferans oturumu sayısı.  <br/> |

> [!NOTE]
> Teams_HasOtherAction, kullanıcının etkin kabul ettiği ancak Sohbet İletileri, 1:1 çağrıları, Kanal İletileri, Toplam Toplantılar ve Düzenlenen Toplantılar için sıfır değeri olduğu anlamına gelir.
   
### <a name="data-table---tenant-product-usage"></a>Veri tablosu - Kiracı Ürün Kullanımı

Bu tablo, proje kapsamındaki her ürün için etkinleştirme, etkin, geri dönme ve ilk kez kullananlara aydan aya benimseme Microsoft 365. En Microsoft 365 değerleri, ürünlerin herhangi bir'inde etkin kullanımı temsil eder.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Ürün  <br/> |Kullanım bilgileri özetlenen ürünlerin adı. Microsoft 365 sütunundaki değer, ürünlerin herhangi bir etkinliği temsil eder  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
|EnabledUsers  <br/> |Ürünü zaman çerçevesi değeri olarak kullanmak için etkinleştirilen kullanıcı sayısı; ayın bir bölümünde etkinleştirilmişse, bunlar yine de sayılır.  <br/> |
|ActiveUsers  <br/> |Zaman çerçevesi değeri için üründe bilinçli olarak etkinlik gerçekleştirilen kullanıcı sayısı.  <br/> Bir kullanıcı üründeki temel etkinliklerden birini gerçekleştirdiyse, ilgili ayda ürün için etkin olarak sayılır. Temel etkinlikler **Kiracı Ürün Etkinliği** tablosunda sağlanmıştır.  <br/> |
|CumulativeActiveUsers  <br/> |Bir ürünü kullanacak şekilde etkinleştirilmiş ve yeni kullanım sisteminde veri toplama işlemi başladığından beri zaman çerçevesi ayına kadar ürünü kullanmış olan kullanıcı sayısı.  <br/> |
|MoMReturningUsers  <br/> |Zaman çerçevesi ayında etkin olan ve bir önceki ay da etkin olmuş kullanıcı sayısı.  <br/> |
|FirstTimeUsers  <br/> |Yeni kullanım sisteminde veri toplama işlemi başladığından beri ilk kez zaman çerçevesinde etkin olmuş kullanıcı sayısı.  <br/> Bir kullanıcının bu yeni raporlama sisteminde veri toplama işlemi başladığından beri ilk kez etkinlik gerçekleştirdiğini algılarsak, bu kullanıcı ilgili ay için ilk kez kullananlar arasında sayılır. İlk kez alan bir kullanıcı olarak kabul edildiklerinde, bu kullanıcının etkinlikleri arasında büyük bir boşluk olsa bile bu kullanıcı bir daha ilk kez gelen kullanıcı olarak saymaz.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Veri tablosu - Kiracı Ürün Etkinliği

Bu tablo, ürünler içindeki çeşitli etkinlikler için aylık toplam etkinlik ve etkin kullanıcı sayısı sağlar.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Zaman Çerçevesi  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
|Ürün  <br/> |Kullanım verileri kullanılabilen Microsoft 365 ürünün adı.  <br/> |
|Etkinlik  <br/> |Bir üründe, ürünün etkin olarak kullanıldığını göstermek için kullanılan etkinliğin adı.  <br/> |
|ActivityCount  <br/> |Bu, tüm etkin kullanıcıları kapsayacak şekilde üründe gerçekleştirilen her etkinlik için sayılan toplam etkinlik sayısıdır.  <br/> **Not:** SharePoint Online ve OneDrive İş etkinlikleri için bu değer, kullanıcıların etkileşim gerçekleştirdiği farklı belge sayısını temsil eder.  <br/> |
|ActiveUserCount  <br/> |Ürün içinde etkinliği gerçekleştiren kullanıcı sayısı.  <br/> |
|TotalDurationInMinute  <br/> |Tüm etkin kullanıcıları kapsayacak şekilde, geçerli bir Skype Kurumsal etkinliğinde ses veya görüntü oturumu kullanımının dakika cinsinden süresi.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Veri tablosu - Kiracı Posta Kutusu Kullanımı

Bu tablo, kullanıcı posta kutusu olan tüm lisanslı Exchange Online özet verilerinden oluşur. Tüm kullanıcı posta kutularının ay sonu durumunu içerir. Bu tablodaki veriler, birden çok ayın toplamını içermez. Bu tablodaki son aya ait veriler, en son durumu temsil eder.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|TotalMailboxes  <br/> |Yeni abonelik için kullanıcı Microsoft 365 kutusu sayısı.  <br/> |
|IssueWarningQuota  <br/> |Tüm kullanıcıların posta kutularına uyarı vermeyle ilgili toplam kota.  <br/> |
|ProhibitSendQuota  <br/> |Tüm kullanıcı posta kutularında gönderimi yasaklamak için toplam kota.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Tüm kullanıcı posta kutularında gönderim ve alımı yasaklamak için toplam kota.  <br/> |
|TotalItemBytes  <br/> |Tüm kullanıcı posta kutularında bayt cinsinden toplam kullanılan depolama alanı miktarı.  <br/> |
|MailboxesNoWarning  <br/> |Depolama alanı uyarı sınırı altında kalan kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesIssueWarning  <br/> |Depolama alanı kotasıyla ilgili uyarı gönderilen kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesExceedSendQuota  <br/> |Gönderme kotasını aşan kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesExceedSendReceiveQuota  <br/> |Gönderme/alma kotasını aşan kullanıcı posta kutusu sayısı.  <br/> |
|DeletedMailboxes  <br/> |Zaman çerçevesi içinde silinen kullanıcı posta kutusu sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Veri tablosu - Kiracı İstemci Kullanımı

Bu tablo, kullanıcıların Exchange Online, veritabanı ve veri kaynağına bağlanmak için Exchange Online Skype Kurumsal özet Yammer. Bu tablo, henüz SharePoint Online ve OneDrive İş için istemci kullanım verilerini içermez.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Ürün  <br/> |İstemci kullanım verilerini Microsoft 365 bilgileri için ürün adı.  <br/> |
|ClientId  <br/> |Ürüne bağlanmak için kullanılan her cihazın adı.  <br/> |
|UserCount  <br/> |Her ürün için istemcilerin her birini kullanan kullanıcı sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Veri tablosu - Kiracı SharePoint Online Kullanımı

Bu tablo, bir Çevrimiçi sitenin kullanımı veya etkinliğiyle ilgili aydan aya SharePoint verilerden oluşur. Bu yalnızca Ekip Siteleri ve Grup sitelerini kapsar. SharePoint Online sitelerinin ay sonu durumu bu sütunda temsil edildi. Örneğin, bir kullanıcı beş belge oluşturdu, toplam depolama için 10 MB kullandı, sonra bazı dosyaları sildi ve dosyalar için ay sonu durumuna beş MB depolama alanı kullanan yedi dosya eklendi.  bu tabloda temsil edilen değer ay sonu durumudur. Bu tablo yinelenen toplama sayısını önlemek için gizlenmiştir ve iki başvuru tablosu oluşturmak için kaynak olarak kullanılır.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|SiteType  <br/> |Site türü değeri (tümü/ekip/grup) (tümü ifadesi, bu 2 site türünden herhangi birini temsil eder).  <br/> |
|TotalSites  <br/> |Zaman çerçevesi sonunda mevcut olan site sayısı.  <br/> |
|DocumentCount  <br/> |Zaman çerçevesi sonunda sitede mevcut olan toplam belge sayısı.  <br/> |
|Diplansed  <br/> |Zaman çerçevesi sonunda tüm sitelerde kullanılan toplam depolama alanı.  <br/> |
|ActivityType  <br/> |Çeşitli dosya etkinliği türlerini (tümü/etkin dosyalar/ DIŞ/İÇ paylaşılan dosyalar/eşitlenen dosyalar) kaydeden site sayısı.  <br/> Gerçekleştirilen dosya etkinliklerini temsil eder.  <br/> |
|SitesWithOwnerActivities  <br/> |Site sahibinin kendi sitelerinde belirli bir dosya etkinliği gerçekleştirdiği etkin site sayısı. Site sahibini PowerShell komutu **get-sposite'dan edinebilirsiniz**. Bu, siteden sorumlu olan kişidir.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Sitelerde site sahibi dışındaki kullanıcıların belirli bir dosya etkinliği gerçekleştirdiği etkin sitelerin ilgili aya ait toplam sayısı. Site sahibini PowerShell komutu **get-sposite'dan edinebilirsiniz**. Bu, siteden sorumlu olan kişidir. <br/> |
|ActivityTotalSites  <br/> |Zaman çerçevesi içinde etkinlik kaydeden site sayısı. Bir sitede zaman çerçevesinin başlarında etkinlik gerçekleşmiş ve zaman çerçevesinin sonuna kadar site silinmişse bu site yine de ilgili zaman çerçevesi için toplam etkin site sayısına dahil edilir.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Veri tablosu - Kiracı OneDrive Kullanımı

Bu tablo, OneDrive hesaplarıyla ilgili olarak hesap sayısı, OneDrive hesaplarındaki belge sayısı, kullanılan depolama alanı, etkinlik türüne göre dosya sayısı gibi veriler sağlar. OneDrive İş hesaplarının ay sonu durumu bu tabloda temsil edilir. Örneğin, bir kullanıcı 10 MB depolama alanı kullanan bir Beş belge oluşturdu ve ay sonunda Beş MB depolama alanı kullanan yedi dosya olacak şekilde birkaç dosya sildi ve başka dosyalar eklediyse, ay sonu değeri ay sonunda bu tabloda temsil edildi.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|SiteType  <br/> |Değer "OneDrive"dır.  <br/> |
|TotalSites  <br/> |Zaman çerçevesinin sonunda mevcut olan OneDrive İş hesabı sayısı.  <br/> |
|DocumentCount  <br/> |Zaman çerçevesi sonunda tüm OneDrive İş hesaplarında mevcut olan toplam belge sayısı  <br/> |
|Diplansed  <br/> |Zaman çerçevesi sonunda tüm OneDrive kullanılan toplam depolama alanı.  <br/> |
|ActivityType  <br/> |Çeşitli dosya etkinliği türlerini (tümü/etkin dosyalar/ DIŞ/İÇ paylaşılan dosyalar/eşitlenen dosyalar) kaydeden hesap sayısı.  <br/> Tümü ifadesi, gerçekleştirilen dosya etkinliklerinden herhangi birini temsil eder  <br/> |
|SitesWithOwnerActivities  <br/> |Hesap sahibinin kendi hesabında belirli bir dosya etkinliği gerçekleştirdiği etkin OneDrive İş hesabı sayısı.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Dosya etkinliğinin hesap sahibi dışındaki kullanıcılar tarafından gerçekleştirildiği OneDrive İş hesabı sayısı.  <br/> |
|ActivityTotalSites  <br/> |Zaman çerçevesi boyunca herhangi bir etkinlik kaydeden OneDrive İş hesabı sayısı. Bir OneDrive İş hesabında zaman çerçevesinin başlarında etkinlik gerçekleşmiş ve zaman çerçevesinin sonuna kadar hesap silinmişse bu hesap yine de ilgili zaman çerçevesi için toplam etkin OneDrive İş hesabı sayısına dahil edilir.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Veri tablosu - Kiracı Microsoft 365 Grupları Kullanımı

Bu tablo, grupların kuruluş Microsoft 365 nasıl kullanıldıkları hakkında veri sağlar.
  
****

|**Sütun adı**|**Sütun Açıklaması**|
|:-----|:-----|
|Zaman Çerçevesi  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
|GroupType  <br/> |Grup türü (özel/genel/tüm).  <br/> |
|TotalGroups  <br/> |Her grup türündeki grup sayısı.  <br/> |
|ActiveGroups  <br/> |Etkin grup sayısı.  <br/> |
|MBX_TotalGroups  <br/> |Posta kutusu gruplarının sayısı.  <br/> |
|MBX_ActiveGroups  <br/> |Etkin posta kutusu gruplarının sayısı.  <br/> |
|MBX_TotalActivities  <br/> |Posta kutusu etkinliklerinin sayısı.  <br/> |
|MBX_TotalItems  <br/> |Posta kutusu öğelerinin sayısı.  <br/> |
|MBX_StorageUsed  <br/> |Kullanılan posta kutusu depolama alanı miktarı.  <br/> |
|SPO_TotalGroups  <br/> |SharePoint gruplarının sayısı.  <br/> |
|SPO_ActiveGroups  <br/> |Etkin SharePoint gruplarının sayısı.  <br/> |
|SPO_FileAccessedActiveGroups  <br/> |Dosya SharePoint etkinliklere sahip grup sayısı.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Dosya SharePoint etkinlikleri olan grup sayısı.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Paylaşılan SharePoint veya gruplarla (dış kullanıcılar da dahil olabilir) sahip grup sayısı.  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Dosyaların şirket dışında paylaşıldığı etkinliklere sahip SharePoint gruplarının sayısı.  <br/> |
|SPO_TotalActivities  <br/> |SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileAccessedActivities  <br/> |Dosya erişimli SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileSyncedActivities  <br/> |Dosya eşitlemeli SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Dosya SharePoint etkinliklerinin şirket içinde veya gruplarla (dış üyeler de dahil olabilir) sayısı.  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Dosyaların şirket dışında paylaşıldığı SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_TotalFiles  <br/> |SharePoint dosyalarının sayısı.  <br/> |
|SPO_ActiveFiles  <br/> |Etkin SharePoint dosyalarının sayısı.  <br/> |
|SPO_StorageUsed  <br/> |Kullanılan SharePoint depolama alanı miktarı.  <br/> |
|YAM_TotalGroups  <br/> |Yammer gruplarının sayısı.  <br/> |
|YAM_ActiveGroups  <br/> |Etkin Yammer gruplarının sayısı.  <br/> |
|YAM_LikedActiveGroups  <br/> |Beğenme etkinliklerinin olduğu Yammer gruplarının sayısı.  <br/> |
|YAM_PostedActiveGroups  <br/> |Gönderme etkinliklerinin olduğu Yammer gruplarının sayısı.  <br/> |
|YAM_ReadActiveGroups  <br/> |Okuma etkinliklerinin olduğu Yammer gruplarının sayısı.  <br/> |
|YAM_TotalActivities  <br/> |Yammer etkinliklerinin sayısı.  <br/> |
|YAM_LikedActivities  <br/> |Yammer beğenme etkinliklerinin sayısı.  <br/> |
|YAM_PostedActivties  <br/> |Yammer gönderme etkinliklerinin sayısı.  <br/> |
|YAM_ReadActivites  <br/> |Yammer okuma etkinliklerinin sayısı.  <br/> |

### <a name="data-table---tenant-office-licenses"></a>Veri tablosu - Kiracı Office Lisansları

Bu tablo, kullanıcılara lisans ataması hakkında aydan aya özet veriler sağlar. 
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|LicenseName  <br/> |Lisansın adı.  <br/> |
|AssignedCount  <br/> |Atanmış lisans sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Veri tablosu - Kiracı Office Etkinleştirmesi

Tablo, tüm hizmet planları genelinde Office etkinleştirme sayısı hakkında veri sağlar; örneğin, Microsoft 365 Uygulamaları, Visio veya Project. Cihaz (Android/iOS/Mac/PC) başına etkinleştirme sayısı hakkında da veri sağlar.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|ServicePlanName  <br/> |Alttaki sütunlarda gösterildiği gibi, cihazlara göre hizmet planı adı değerlerinin ve sayılarının listesi.  <br/> |
|TotalEnabled  <br/> |Zaman çerçevesinin sonuna kadar hizmet planı adı başına etkinleştirilen kullanıcı sayısı.  <br/> |
|TotalActivatedUsers  <br/> |Zaman çerçevesinin sonuna kadar her bir hizmet planını etkinleştiren kullanıcı sayısı.  <br/> |
|AndroidCount  <br/> |Zaman çerçevesinin sonuna kadar Android cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|iOSCount  <br/> |Zaman çerçevesinin sonuna kadar iOS cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|MacCount  <br/> |Zaman çerçevesinin sonuna kadar Mac cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|PcCount  <br/> |Zaman çerçevesinin sonuna kadar PC cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|WinRtCount  <br/> |Zaman çerçevesinin sonuna kadar Windows Mobile cihazı için hizmet planı başına etkinleştirme sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
