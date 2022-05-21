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
description: "Kullanım analizinin bir API'ye nasıl bağlanıp çeşitli Microsoft 365 hizmetlerinin aylık kullanım eğilimini sağladığını öğrenin.  "
ms.openlocfilehash: 05b8a6d9a69cc6347b4d2cdcfbdeaa26bd479cbd
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620992"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Microsoft 365 kullanım analizi veri modeli

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Microsoft 365 kullanım analizi tablolarına yönelik veriler

Microsoft 365 kullanım analizi, çok boyutlu bir veri modelini kullanıma sunan bir API'ye bağlanır. Microsoft 365 kullanım analizinin verilerini oluşturmak için kullandığı API'ler çeşitli, genel kullanıma açık Graph API'lerdendir. Microsoft 365 kullanım analizi API'sinin işlevi genel olarak kullanılamaz.
  
> [!NOTE]
> Daha fazla bilgi için bkz[. Microsoft Graph'da Microsoft 365 kullanım raporlarıyla çalışma](/graph/api/resources/report). 
  
Bu API, çeşitli Microsoft 365 hizmetlerinin aylık kullanım eğilimi hakkında bilgi sağlar. API'ler tarafından tam olarak hangi verilerin döndürüldüğünü görmek için aşağıdaki bölümde yer alan tabloya başvurun.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Microsoft 365 Raporlama API'sinin döndürdiği veri tabloları

|**Tablo adı**|**Tablodaki bilgiler**|**Tarih aralığı**|
|:-----|:-----|:-----|
|Kiracı Ürün Kullanımı  <br/> |Etkin, etkin kullanıcıların aylık toplamlarını, bir aydan fazla tutulan kullanıcıları, ilk kez kullanan kullanıcıları ve toplu etkin kullanıcıları içerir.  <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı Ürün Etkinliği  <br/> |Ürünlerdeki çeşitli etkinlikler için aylık etkinlik toplamlarını ve etkin kullanıcı sayısını içerir.  <br/> Bu veri tablosunda döndürülen ürün etkinlikleri hakkında bilgi edinmek için bkz. [etkin kullanıcı tanımı](active-user-in-usage-reports.md).      <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı Office Lisansları  <br/> |Kullanıcılara atanan Microsoft Office aboneliklerinin sayısı hakkında veri içerir  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Posta Kutusu Kullanımı  <br/> |Toplam posta kutusu sayısı ve depolamanın nasıl kullanıldığı için kullanıcının posta kutusu hakkındaki verileri içerir.  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı İstemci Kullanımı  <br/> |Exchange Online, Skype Kurumsal ve Yammer'a bağlanmak için etkin olarak belirli istemcileri/cihazları kullanan kullanıcı sayısı hakkındaki verileri içerir.  <br/> |İçinde bulunulan kısmi ay dahil olacak şekilde sürekli kayan 12 aylık bir dönem için aylık toplanan verileri içerir.  <br/> |
|Kiracı SharePoint Online Kullanımı  <br/> |SharePoint siteleri hakkında, Takım veya Gruplar sitelerini kapsayan toplam site sayısı, sitedeki belge sayısı, etkinlik türüne göre dosya sayısı ve kullanılan depolama alanı gibi verileri içerir.  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı OneDrive İş Kullanımı  <br/> |OneDrive hesaplarıyla ilgili olarak hesap sayısı, OneDrive'lardaki belge sayısı, kullanılan depolama alanı, etkinlik türüne göre dosya sayısı gibi verileri içerir.  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Microsoft 365 Grupları Kullanımı  <br/> |Posta Kutusu, SharePoint ve Yammer gibi Microsoft 365 Grupları kullanımıyla ilgili verileri içerir.  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kiracı Office Etkinleştirmesi  <br/> |Office abonelik etkinleştirme sayısı, cihaz başına etkinleştirme sayısı (Android/iOS/Mac/PC), hizmet planına göre etkinleştirmeler (Kurumlar için Microsoft 365 Uygulamaları, Visio, Project gibi) hakkındaki verileri içerir.  <br/> |Geçerli kısmi ay dahil olmak üzere 12 aylık sıralı bir dönem için ay sonu durum verilerini içerir.  <br/> |
|Kullanıcı Durumu  <br/> |Kullanıcı görünen adı, kullanıcıya atanan ürünler, konum, bölüm, unvan, şirket dahil olmak üzere kullanıcılarla ilgili meta veriler içerir. Bu veriler, son tam ay içinde lisans atanmış kullanıcılarla ilgilidir. Her kullanıcı benzersiz olarak bir kullanıcı kimliğiyle temsil edilir.  <br/> |Bu veriler, son tam ay içinde bir lisans atanmış kullanıcılarla ilgilidir.  <br/> |
|Kullanıcı Etkinliği  <br/> |Lisanslı kullanıcılar tarafından gerçekleştirilen etkinlikler hakkında kullanıcı başına düzeyinde bilgiler içerir.  <br/> Bu veri tablosunda döndürülen ürün etkinlikleri hakkında bilgi edinmek için bkz. [etkin kullanıcı tanımı](active-user-in-usage-reports.md).      <br/> |Bu veriler, son tam ay içinde hizmetlerin herhangi birinde etkinlik gerçekleştirmiş kullanıcılarla ilgilidir.  <br/> |
   
Her veri tablosuyla ilgili ayrıntılı bilgi görüntülemek için aşağıdaki bölümleri genişletin.
  
### <a name="data-table---user-state"></a>Veri tablosu - Kullanıcı Durumu

Bu tablo, son tam ay içinde kendilerine lisans atanmış olan tüm kullanıcılar için kullanıcı düzeyi ayrıntıları sağlar. Azure Active Directory'den veri alır.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Userıd  <br/> |Kullanıcıyı temsil eden ve veri kümesindeki diğer veri tablolarıyla birleştirmeyi etkinleştiren benzersiz kullanıcı kimliği.  <br/> |
|Timeframe  <br/> |Bu tablonun hangi aya ait verileri içerdiğini gösteren değer.  <br/> |
|UPN  <br/> |Diğer dış veri kaynaklarıyla birleştirebilmek amacıyla kullanıcıyı benzersiz olarak tanımlayan kullanıcı asıl adı.  <br/> |
|Displayname  <br/> |Kullanıcının görünen adı.  <br/> |
|IDType  <br/> |Kullanıcı Yammer kimliğini kullanarak bağlanan Yammer bir kullanıcıysa kimlik türü 1 veya Microsoft 365 kimliğini kullanarak Yammer bağlanıyorsa 0 olarak ayarlanır.  <br/> Değer, bu kullanıcının Microsoft 365 kimliğiyle değil Yammer kimliğiyle Yammer bağlandığını göstermek için 1'dir  <br/> |
|HasLicenseEXO  <br/> |Kullanıcıya bir lisans atandıysa ve ayın son gününde Exchange kullanmak üzere etkinleştirildiyse true olarak ayarlayın.  <br/> |
|HasLicenseODB  <br/> |Kullanıcıya bir lisans atandıysa ve ayın son gününde OneDrive İş kullanmak üzere etkinleştirildiyse true olarak ayarlayın.  <br/> |
|HasLicenseSPO  <br/> |Kullanıcıya bir lisans atandıysa ve ayın son gününde SharePoint Online'ı kullanacak şekilde etkinleştirildiyse true olarak ayarlayın.  <br/> |
|HasLicenseYAM  <br/> |Kullanıcıya bir lisans atandıysa ve ayın son gününde Yammer kullanmak üzere etkinleştirildiyse true olarak ayarlayın.  <br/> |
|HasLicenseSFB  <br/> |Kullanıcıya bir lisans atandıysa ve ayın son gününde İş İçin Skype kullanmak üzere etkinleştirildiyse true olarak ayarlayın.  <br/> |
|HasLicenseTeams  <br/> |Kullanıcıya bir lisans atanırsa true olarak ayarlayın ve ayın son gününde Microsoft Teams kullanımını etkinleştirin.  <br/> |
|Şirket  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen şirket verileri.  <br/> |
|Bölüm  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen bölüm verileri.  <br/> |
|LocationCity  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen şehir verileri.  <br/> |
|LocationCountry  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen ülke verileri.  <br/> |
|LocationState  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen eyalet verileri.  <br/> |
|KonumOffice  <br/> |Kullanıcının ofisi.  <br/> |
|Başlık  <br/> |Bu kullanıcı için Azure Active Directory'de temsil edilen unvan verileri.  <br/> |
|Silindi  <br/> |Kullanıcı son tam ay içinde Microsoft 365 silindiyse True.  <br/> |
|SilinmişTarih  <br/> |Kullanıcının Microsoft 365 silindiği tarih.  <br/> |
|YAM_State  <br/> |Yammer sistemindeki kullanıcının durumları etkin, silinmiş veya askıya alınmış olabilir.  <br/> |
|YAM_ActivationDate  <br/> |Kullanıcının Yammer'da etkin durumuna geçtiği tarih.  <br/> |
|YAM_DeletionDate  <br/> |Kullanıcının Yammer'da silinmiş durumuna geçtiği tarih.  <br/> |
|YAM_SuspensionDate  <br/> |Kullanıcının Yammer'da askıya alınmış durumuna geçtiği tarih.  <br/> |
   
### <a name="data-table---user-activity"></a>Veri tablosu - Kullanıcı Etkinliği

Bu tablo, önceki ay içinde hizmetlerin herhangi birinde etkinlik gerçekleştirmiş her bir kullanıcıyla ilgili veriler içerir.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Userıd  <br/> |Kullanıcıyı temsil eden ve veri kümesindeki diğer veri tablolarıyla birleştirmeyi etkinleştiren benzersiz kullanıcı kimliği.  <br/> |
|IDType  <br/> |Kullanıcı Yammer kimliğini kullanarak bağlanan Yammer bir kullanıcıysa kimlik türü 1 veya Microsoft 365 kimliğini kullanarak Yammer bağlanıyorsa 0 olarak ayarlanır.  <br/> Değer, bu kullanıcının Microsoft 365 kimliğiyle değil Yammer kimliğiyle Yammer bağlandığını göstermek için 1'dir  <br/> |
|Timeframe  <br/> |Bu tablonun hangi aya ait verileri temsil ettiğini gösteren değer.  <br/> |
|EXO_EmailSent  <br/> |Gönderilen e-posta sayısı.  <br/> |
|EXO_EmailReceived  <br/> |Alınan e-posta sayısı.  <br/> |
|EXO_EmailRead  <br/> |Kullanıcının gerçekleştirdiği e-posta okuma etkinliğinin sayısı, zaten okunmuş bir e-postayı veya daha önce alınan bir e-postayı birden çok kez okumak olabilir.  <br/> |
|EXO_AppointmentCreated  <br/> |Oluşturulan randevu sayısı.  <br/> |
|EXO_MeetingAccepted  <br/> |Kabul edilen toplantı sayısı.  <br/> |
|EXO_MeetingCancelled  <br/> |İptal edilen toplantı sayısı.  <br/> |
|EXO_MeetingDeclined  <br/> |Reddedilen toplantı sayısı.  <br/> |
|EXO_MeetingSent  <br/> |Gönderilen toplantı sayısı.  <br/> |
|ODB_FileViewedModified  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabında etkileşim gerçekleştirdiği (örneğin, oluşturduğu, güncelleştirdiği, sildiği, görüntülediği veya indirdiği) dosya sayısı.  <br/> |
|ODB_FileSynched  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabında eşitlediği dosya sayısı.  <br/> |
|ODB_FileSharedInternally  <br/> |Bu kullanıcının herhangi bir OneDrive İş veya gruplar içindeki kullanıcılarla (dış kullanıcıları içerebilecek) dahili olarak paylaştığı dosya sayısı.  <br/> |
|ODB_FileSharedExternally  <br/> |Bu kullanıcının herhangi bir OneDrive İş hesabından şirket dışında paylaştığı dosya sayısı.  <br/> |
|ODB_AccessedByOwner  <br/> |Kullanıcının kendi OneDrive İş bulunan etkileşimde bulunduğu site sayısı.  <br/> |
|ODB_AccessedByOthers  <br/> |Bu kullanıcının etkileşimde bulunduğu ve başka bir kullanıcının OneDrive İş bulunan site sayısı.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Bu kullanıcının herhangi bir grup sitesinde etkileşimde olduğu dosya sayısı.  <br/> |
|SPO_GroupFileSynched  <br/> |Bu kullanıcının herhangi bir grup sitesinde eşitlediği dosya sayısı.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Kuruluştaki kullanıcılarla veya gruplar içindeki kullanıcılarla (dış kullanıcıları içerebilecek) paylaşılan dosyaların sayısı.  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Bu kullanıcının herhangi bir grup sitesinden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Kullanıcının sahip olduğu bir grup sitesinde bulunan etkileşimde bulunduğu site sayısı.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Kullanıcının etkileşimde bulunduğu ve başka bir kullanıcının sahip olduğu bir grup sitesinde bulunan site sayısı.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Herhangi bir sitede bulunan ve bu kullanıcının etkileşim gerçekleştirdiği dosya sayısı.  <br/> |
|SPO_OtherFileSynched  <br/> |Bu kullanıcının herhangi bir siteden eşitlediği dosya sayısı.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Bu kullanıcının başka bir siteden veya gruplar içindeki kullanıcılarla (dış kullanıcılar içerebilecek) dahili olarak paylaştığı dosya sayısı. <br/> |
|SPO_OtherFileSharedExternally  <br/> |Bu kullanıcının herhangi bir siteden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Kullanıcının sahip olduğu diğer sitede bulunan ve etkileşim gerçekleştirdiği site sayısı.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Başka bir kullanıcıya ait bir sitede bulunan ve kullanıcının etkileşim gerçekleştirdiği site sayısı.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Herhangi bir ekip sitesinde bulunan ve bu kullanıcının etkileşim gerçekleştirdiği dosya sayısı.  <br/> |
|SPO_TeamFileSynched  <br/> |Bu kullanıcının herhangi bir ekip sitesinden eşitlediği dosya sayısı.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Bu kullanıcının herhangi bir ekip sitesinden veya gruplar içindeki kullanıcılarla (dış kullanıcılar içerebilecek) dahili olarak paylaştığı dosya sayısı.  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Bu kullanıcının herhangi bir ekip sitesinden şirket dışında paylaştığı dosya sayısı.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Kullanıcının sahip olduğu bir ekip sitesinde bulunan etkileşimde bulunduğu site sayısı.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Kullanıcının etkileşimde bulunduğu ve başka bir kullanıcının sahip olduğu bir ekip sitesinde bulunan site sayısı.  <br/> |
|Teams_ChatMessages  <br/> |Gönderilen sohbet iletisi sayısı.  <br/> |
|Teams_ChannelMessage  <br/> |Kanallara gönderilen ileti sayısı.  <br/> |
|Teams_CallParticipate  <br/> |Kullanıcının katıldığı çağrı sayısı.  <br/> |
|Teams_MeetingParticipate  <br/> |Kullanıcının katıldığı toplantı sayısı.  <br/> |
|Teams_HasOtherAction  <br/> |Kullanıcı Microsoft Teams'de diğer eylemler gerçekleştirdiğinde Boole değeri.  <br/> |
|YAM_MessagePost  <br/> |Bu kullanıcının yayınladığı Yammer ileti sayısı.  <br/> |
|YAM_MessageLiked  <br/> |Bu kullanıcının beğendiği Yammer ileti sayısı.  <br/> |
|YAM_MessageRead  <br/> |Bu kullanıcının okuduğu Yammer ileti sayısı.  <br/> |
|SFB_P2PSummary  <br/> |Bu kullanıcının katıldığı eşler arası oturum sayısı.  <br/> |
|SFB_ConfOrgSummary  <br/> |Bu kullanıcının düzenlediği konferans oturumu sayısı.  <br/> |
|SFB_ConfPartSummary  <br/> |Bu kullanıcının katıldığı konferans oturumu sayısı.  <br/> |

> [!NOTE]
> Teams_HasOtherAction, kullanıcının etkin olarak kabul edildiği ancak Sohbet İletileri, 1:1 aramalar, Kanal İletileri, Toplam Toplantılar ve Düzenlenen Toplantılar için sıfır değere sahip olduğu anlamına gelir.
   
### <a name="data-table---tenant-product-usage"></a>Veri tablosu - Kiracı Ürün Kullanımı

Bu tablo, Microsoft 365 içindeki her ürün için etkinleştirme, etkin, geri dönen ve ilk kez kullananlar açısından aylık benimseme verileri sağlar. Microsoft 365 değerleri, ürünlerden herhangi birinde etkin kullanımı temsil eder.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Ürün  <br/> |Kullanım bilgileri özetlenen ürünlerin adı. Ürün sütunundaki Microsoft 365 değeri, ürünlerin herhangi birindeki etkinliği temsil eder  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
|EnabledUsers  <br/> |Bir kullanıcı ayın bir bölümü için etkinleştirildiyse, zaman çerçevesi değeri için ürünü kullanmak üzere etkinleştirilen kullanıcı sayısı yine de sayılır.  <br/> |
|ActiveUsers  <br/> |Üründe zaman çerçevesi değeri için kasıtlı bir etkinlik gerçekleştiren kullanıcı sayısı.  <br/> Bir kullanıcı üründeki temel etkinliklerden birini gerçekleştirdiyse, ilgili ayda ürün için etkin olarak sayılır. Temel etkinlikler **Kiracı Ürün Etkinliği** tablosunda sağlanmıştır.  <br/> |
|KümülatifActiveUsers  <br/> |Bir ürünü kullanacak şekilde etkinleştirilmiş ve yeni kullanım sisteminde veri toplama işlemi başladığından beri zaman çerçevesi ayına kadar ürünü kullanmış olan kullanıcı sayısı.  <br/> |
|MoMReturningUsers  <br/> |Zaman çerçevesi ayında etkin olan ve bir önceki ay da etkin olmuş kullanıcı sayısı.  <br/> |
|FirstTimeUsers  <br/> |Yeni kullanım sisteminde veri toplama işlemi başladığından beri ilk kez zaman çerçevesinde etkin olmuş kullanıcı sayısı.  <br/> Bir kullanıcının bu yeni raporlama sisteminde veri toplama işlemi başladığından beri ilk kez etkinlik gerçekleştirdiğini algılarsak, bu kullanıcı ilgili ay için ilk kez kullananlar arasında sayılır. İlk kez kullanıcı olarak sayıldığında, bu kullanıcının etkinliğinde büyük bir boşluk olsa bile, bir daha asla ilk kez kullanan kullanıcı olarak sayılmaz  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Veri tablosu - Kiracı Ürün Etkinliği

Bu tablo, ürünlerdeki çeşitli etkinlikler için aylık etkinlik toplamları ve etkin kullanıcı sayısı sağlar.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Zaman Çerçevesi  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
|Ürün  <br/> |Kullanım verilerinin kullanılabildiği Microsoft 365 ürünün adı.  <br/> |
|Etkinlik  <br/> |Bir üründe, ürünün etkin olarak kullanıldığını göstermek için kullanılan etkinliğin adı.  <br/> |
|ActivityCount  <br/> |Bu, tüm etkin kullanıcıları kapsayacak şekilde üründe gerçekleştirilen her etkinlik için sayılan toplam etkinlik sayısıdır.  <br/> **Not:** SharePoint Online ve OneDrive İş etkinlikleri için bu değer, kullanıcıların etkileşim gerçekleştirdiği farklı belge sayısını temsil eder.  <br/> |
|ActiveUserCount  <br/> |Ürün içinde etkinliği gerçekleştiren kullanıcı sayısı.  <br/> |
|TotalDurationInMinute  <br/> |Tüm etkin kullanıcıları kapsayacak şekilde, geçerli bir Skype Kurumsal etkinliğinde ses veya görüntü oturumu kullanımının dakika cinsinden süresi.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Veri tablosu - Kiracı Posta Kutusu Kullanımı

Bu tablo, kullanıcı posta kutusu olan tüm lisanslı Exchange Online kullanıcıların özet verilerinden oluşur. Tüm kullanıcı posta kutularının ay sonu durumunu içerir. Bu tablodaki veriler birden çok ay boyunca eklenmemiş. Bu tablodaki son aya ait veriler, en son durumu temsil eder.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|TotalMailboxes  <br/> |Microsoft 365 aboneliği için kullanıcı posta kutularının sayısı.  <br/> |
|IssueWarningQuota  <br/> |Tüm kullanıcıların posta kutuları arasında uyarı verme kotası.  <br/> |
|ProhibitSendQuota  <br/> |Tüm kullanıcı posta kutularında gönderimi yasaklamak için toplam kota.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Tüm kullanıcı posta kutularında gönderim ve alımı yasaklamak için toplam kota.  <br/> |
|TotalItemBytes  <br/> |Tüm kullanıcı posta kutularında bayt cinsinden toplam kullanılan depolama alanı miktarı.  <br/> |
|Posta KutularıNoWarning  <br/> |Depolama alanı uyarı sınırı altında kalan kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesIssueWarning  <br/> |Depolama alanı kotasıyla ilgili uyarı gönderilen kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesExceedSendQuota  <br/> |Gönderme kotasını aşan kullanıcı posta kutusu sayısı.  <br/> |
|MailboxesExceedSendReceiveQuota  <br/> |Gönderme/alma kotasını aşan kullanıcı posta kutularının sayısı.  <br/> |
|DeletedMailboxes  <br/> |Zaman çerçevesi içinde silinen kullanıcı posta kutusu sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Veri tablosu - Kiracı İstemci Kullanımı

Bu tablo, kullanıcıların Exchange Online, Skype Kurumsal ve Yammer bağlanmak için kullandığı istemciler hakkında aylık özet verileri sağlar. Bu tabloda henüz SharePoint Online ve OneDrive İş için istemci kullanım verileri yoktur.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Ürün  <br/> |İstemci kullanım verilerinin kullanılabildiği Microsoft 365 ürünün adı.  <br/> |
|Clientıd  <br/> |Ürüne bağlanmak için kullanılan her cihazın adı.  <br/> |
|UserCount  <br/> |Her ürün için istemcilerin her birini kullanan kullanıcı sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Veri tablosu - Kiracı SharePoint Online Kullanımı

Bu tablo, SharePoint Online sitelerinin kullanımı veya etkinliği hakkında aylık özet verilerden oluşur. Bu yalnızca Ekip Siteleri ve Grup sitelerini kapsar. SharePoint Online sitelerinin ay sonu durumu bu sütunda gösterilir; örneğin, bir kullanıcı beş belge oluşturup toplam depolama için 10 MB kullandıysa ve ardından bazı dosyaları silip daha fazla dosya eklediğinde, dosyalar için ay sonunda beş MB depolama alanı kullanan toplam yedi dosya olur.  bu tabloda gösterilen değerinin ay sonu durumudur. Bu tablo, toplamaların yinelenen sayısını önlemek için gizlenir ve iki başvuru tablosu oluşturmak için kaynak olarak kullanılır.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Site Türü  <br/> |Site türü değeri (tümü/ekip/grup) (tümü ifadesi, bu 2 site türünden herhangi birini temsil eder).  <br/> |
|TotalSites  <br/> |Zaman çerçevesi sonunda mevcut olan site sayısı.  <br/> |
|DocumentCount  <br/> |Zaman çerçevesi sonunda sitede mevcut olan toplam belge sayısı.  <br/> |
|Diplansed  <br/> |Zaman çerçevesi sonunda tüm sitelerde kullanılan toplam depolama alanı.  <br/> |
|ActivityType  <br/> |Çeşitli dosya etkinliği türlerini (tümü/etkin dosyalar/ DIŞ/İÇ paylaşılan dosyalar/eşitlenen dosyalar) kaydeden site sayısı.  <br/> Gerçekleştirilen dosya etkinliklerinden herhangi birini temsil eder.  <br/> |
|SitesWithOwnerActivities  <br/> |Site sahibinin kendi sitelerinde belirli bir dosya etkinliği gerçekleştirdiği etkin site sayısı. Site sahibini PowerShell komutu **get-sposite'den** alabilirsiniz. Bu, siteden sorumlu kişidir.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Sitelerde site sahibi dışındaki kullanıcıların belirli bir dosya etkinliği gerçekleştirdiği etkin sitelerin ilgili aya ait toplam sayısı. Site sahibini PowerShell komutu **get-sposite'den** alabilirsiniz. Bu, siteden sorumlu kişidir. <br/> |
|ActivityTotalSites  <br/> |Zaman çerçevesi içinde etkinlik kaydeden site sayısı. Bir sitede zaman çerçevesinin başlarında etkinlik gerçekleşmiş ve zaman çerçevesinin sonuna kadar site silinmişse bu site yine de ilgili zaman çerçevesi için toplam etkin site sayısına dahil edilir.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Veri tablosu - Kiracı OneDrive Kullanımı

Bu tablo, OneDrive hesaplarıyla ilgili olarak hesap sayısı, OneDrive hesaplarındaki belge sayısı, kullanılan depolama alanı, etkinlik türüne göre dosya sayısı gibi veriler sağlar. OneDrive İş hesaplarının ay sonu durumu bu tabloda temsil edilir. Örneğin, bir kullanıcı 10 MB depolama alanı kullanan bir Beş belge oluşturup birkaç dosyayı silip daha fazla dosya eklediyse, ayın sonunda Beş MB depolama alanı kullanan yedi dosyaya sahip olur ve ayın sonunda ay sonu değeri bu tabloda gösterilir.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|Site Türü  <br/> |Değer "OneDrive"dır.  <br/> |
|TotalSites  <br/> |Zaman çerçevesinin sonunda mevcut olan OneDrive İş hesabı sayısı.  <br/> |
|DocumentCount  <br/> |Zaman çerçevesi sonunda tüm OneDrive İş hesaplarında mevcut olan toplam belge sayısı  <br/> |
|Diplansed  <br/> |Zaman çerçevesinin sonunda tüm OneDrive hesabında kullanılan toplam depolama alanı.  <br/> |
|ActivityType  <br/> |Çeşitli dosya etkinliği türlerini (tümü/etkin dosyalar/ DIŞ/İÇ paylaşılan dosyalar/eşitlenen dosyalar) kaydeden hesap sayısı.  <br/> Tümü ifadesi, gerçekleştirilen dosya etkinliklerinden herhangi birini temsil eder  <br/> |
|SitesWithOwnerActivities  <br/> |Hesap sahibinin kendi hesabında belirli bir dosya etkinliği gerçekleştirdiği etkin OneDrive İş hesabı sayısı.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Dosya etkinliğinin hesap sahibi dışındaki kullanıcılar tarafından gerçekleştirildiği OneDrive İş hesabı sayısı.  <br/> |
|ActivityTotalSites  <br/> |Zaman çerçevesi boyunca herhangi bir etkinlik kaydeden OneDrive İş hesabı sayısı. Bir OneDrive İş hesabında zaman çerçevesinin başlarında etkinlik gerçekleşmiş ve zaman çerçevesinin sonuna kadar hesap silinmişse bu hesap yine de ilgili zaman çerçevesi için toplam etkin OneDrive İş hesabı sayısına dahil edilir.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Veri tablosu - Kiracı Microsoft 365 Grupları Kullanımı

Bu tabloda kuruluş genelinde Microsoft 365 Grupları nasıl kullanıldığına ilişkin veriler sağlanır.
  
****

|**Sütun adı**|**Sütun Açıklaması**|
|:-----|:-----|
|Süre  <br/> |Ay değeri. İçinde bulunulan kısmi ay dahil son 12 ay için ürün başına her ay ayrı bir satırda verilir.  <br/> |
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
|SPO_FileAccessedActiveGroups  <br/> |Dosya erişimli etkinlikleri olan SharePoint gruplarının sayısı.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Dosya eşitlenmiş etkinlikleri olan SharePoint gruplarının sayısı.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Şirket içinde veya gruplarla (dış kullanıcıları içerebilecek) paylaşılan etkinliklere sahip SharePoint gruplarının sayısı.  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Dosyaların şirket dışında paylaşıldığı etkinliklere sahip SharePoint gruplarının sayısı.  <br/> |
|SPO_TotalActivities  <br/> |SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileAccessedActivities  <br/> |Dosya erişimli SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileSyncedActivities  <br/> |Dosya eşitlemeli SharePoint etkinliklerinin sayısı.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Dahili olarak veya gruplarla (dış üyeleri içerebilen) dosya paylaşılan etkinliklerinin SharePoint sayısı.  <br/> |
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

Bu tablo, kullanıcılar için lisans ataması hakkında aylık özet verileri sağlar. 
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|LicenseName  <br/> |Lisansın adı.  <br/> |
|AssignedCount  <br/> |Atanan lisans sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Ay değeri.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Veri tablosu - Kiracı Office Etkinleştirmesi

Tabloda, hizmet planlarında Office abonelik etkinleştirmelerinin sayısıyla ilgili veriler (örneğin, kuruluşlar için Microsoft 365 Uygulamaları, Visio Project) sağlanır. Cihaz (Android/iOS/Mac/PC) başına etkinleştirme sayısı hakkında da veri sağlar.
  
|**Sütun adı**|**Sütun açıklaması**|
|:-----|:-----|
|ServicePlanName  <br/> |Alttaki sütunlarda gösterildiği gibi, cihazlara göre hizmet planı adı değerlerinin ve sayılarının listesi.  <br/> |
|ToplamEnabled  <br/> |Zaman çerçevesinin sonuna kadar hizmet planı adı başına etkinleştirilen kullanıcı sayısı.  <br/> |
|TotalActivatedUsers  <br/> |Zaman çerçevesinin sonuna kadar her bir hizmet planını etkinleştiren kullanıcı sayısı.  <br/> |
|AndroidCount  <br/> |Zaman çerçevesinin sonuna kadar Android cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|iOSCount  <br/> |Zaman çerçevesinin sonuna kadar iOS cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|MacCount  <br/> |Zaman çerçevesinin sonuna kadar Mac cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|PcCount  <br/> |Zaman çerçevesinin sonuna kadar PC cihaz için hizmet planı başına etkinleştirme sayısı.  <br/> |
|WinRtCount  <br/> |Zaman çerçevesinin sonuna kadar Windows Mobile cihazı için hizmet planı başına etkinleştirme sayısı.  <br/> |
|Zaman Çerçevesi  <br/> |Bu sütunda tarih değeri yer alır. Takvim tablosu için çoğa bir ilişkisi olarak kullanılır.  <br/> |
|İçerik Tarihi  <br/> |Zaman çerçevesi geçerli ayı gösteriyorsa, bu değer geçerli ayda en son hangi tarihe ait veriler olduğunu gösterir.  <br/> Zaman çerçevesi önceki ayı gösteriyorsa, bu değer zaman çerçevesi ayının son tarihini gösterir.  <br/> |
