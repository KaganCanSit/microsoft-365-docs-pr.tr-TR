---
title: Grup hizmetleri etkileşimleri
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Grup hizmetleri etkileşimleri
ms.openlocfilehash: 226c1588c0275c3349d0fd996dd68f5748f11cd6
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005420"
---
# <a name="groups-services-interactions"></a>Grup hizmetleri etkileşimleri

Microsoft 365 Grupları, son kullanıcılara bağlı bir deneyim sunmak için Microsoft 365 platformu içindeki çeşitli hizmetler ve iş yükleri için ortak bir doku sağlar. Temel olarak, şunları Microsoft 365 bir grup vardır:

- Üyeliği yönetmek için bir yol (Azure AD)
- Mesajlaşma ve konuşmalar için bir yer (posta kutusu, Exchange kutusu, Microsoft Teams veya Yammer)
- Dosyaların depolandığı yer (SharePoint)
- Zamanlama için bir takvim (Exchange)
- Notları yakalamak için not defteri (OneNote)

Grup oluşturma noktasında birkaç başka kaynak da sağlanmaz, ancak hizmetten ilk kez erişilene kadar görünmezler:

- Grup görevlerini yönetmek için bir alan (Planner)
- Raporlama için çalışma alanı (Power BI)
- Paylaşılan videolar için bir alan (Microsoft Stream)
- Paylaşılan formlar için bir alan (Formlar)

Farklı Microsoft 365, diğer hizmetler grup üyelerine ek işlevsellik ve Microsoft 365 sağlamak için grup üyeleriyle etkileşim kurabilirsiniz.
Bunun örnekleri şunlardır:

- Power Apps için uygulamanın sonları
- Power Automate için iş akışları oluşturma
- Project tabanlı proje yönetimi için Web'de Yol Haritası ve
- Teams tabanlı konuşmalar için video
- Yammer toplulukları için topluluklar

## <a name="user-interactions-with-groups"></a>Gruplarla kullanıcı etkileşimleri

Microsoft 365 Grupları hem yöneticiler hem de son kullanıcılar tarafından çeşitli arabirimlerden oluşturulabilir ve yönetilebilir. 

### <a name="administrative-experiences"></a>Yönetim deneyimleri

Yöneticiler, komut dosyası desteği olan komut satırı arabirimlerinin yanı sıra Microsoft 365 API'si ile etkileşim halindeki özel yerleşik uygulamalar gibi iş yükü yönetim merkezlerinden Graph yönetebilir. Bunun tek istisnası, Yammer web arabiriminin içinde oluşturulacak grup Yammer olmasıdır.

**İlgili ayarlar**

Grup ayarlarını yöneten çeşitli yönetim arabirimleri arasında farkında olmak istediğiniz bazı çakışmalar vardır.

**Microsoft 365 yönetici merkezi**

Grup Microsoft 365 yönetim merkezi, sahiplerin konuk eklemesine izin verme özelliği gibi Gruplara konuk erişimi varsayılan olarak etkindir. Bu yönetim merkezinden Gruplar için başka kuruluş düzeyi denetimi yoktur.

**Azure AD yönetim merkezi**

Azure AD yönetim merkezi, kullanıcıların Azure portallarında grup oluştur hem de sahip ata hem de süre sonu ve adlandırma ilkesi ayarlarıyla ilgili denetimler sunar.

Yönetim merkezi, toplantının ötesine geçecek çeşitli konuk daveti denetimi önlemleri de sağlar. Örneğin, Microsoft 365 yönetim merkezi olmayanların da konukları davet edip etmeyebilmelerini sınırlayabilirler

**SharePoint**

SharePoint site, Sahip, Üye ve Ziyaretçi güvenlik gruplarıyla oluşturulur ve ilk iki grup eşleri Sahip Microsoft 365 eşleşmesi olur. SharePoint Online siteleri için üyelik genel olarak ilişkili grup Microsoft 365 yönetiliyorsa, bu iki yönlü bir ilişki değildir. Microsoft 365 grup düzeyinde üyelikte yapılan tüm değişiklikler SharePoint'e yansır; bununla birlikte, SharePoint grubunda üyelik değiştirilirse bu Microsoft 365 yansıtlanmaz.

### <a name="user-experiences"></a>Kullanıcı deneyimleri

Son kullanıcılar grup içindeki bazı hizmetlerden gruplar Microsoft 365, diğerlerinde yalnızca bir grupla paylaşabilirler.

Aşağıdaki hizmetler son kullanıcılar tarafından grup oluşturulmasına olanak sağlar:

- Outlook
- Planner
- Project için web'de arama
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Grup oluşturma kısıtlaması

Ekiplerin tek bir ekibi kontrol etmek için en yaygın yaklaşım, hangi kullanıcıların ekip oluştur sınırlaması yapmaktır. Bu yalnızca grup oluşturma işlemi sınırlandırarak yapılabilir. Bunu yapmak, diğer hizmetlerden son kullanıcı için gerekli olacak grupları oluşturabilme becerisini etkiler. Microsoft 365 Grupları, bazı uygulama veya hizmetlerden grup oluşturulmasını kısıtlama becerisini desteklerken, diğer kullanıcılardan da grup oluşturulmasına izin vermemektedir.

Grup oluşturma kısıtlaması deneyimi, uygulamalar ve hizmetler arasında değişir:

|Uygulama veya hizmet|Deneyim|
|---|---|
|Outlook|**Yeni grup** seçeneği Kişiler sayfasındaki Yeni menüsünden kaldırılmıştır|
|Planner|**Yeni plan** , grup oluşturmanın kapatılma olduğunu açıklar ve planı var olan bir gruba ekleme teklifi sunar|
|Project için Web'de Yol Haritası|**Grup oluştur** menüsü, grup oluşturmanın kısıtlanmış olduğunu açıklar ve varolan bir grubu kullanmayı önerir.|
|SharePoint|Yine de bir gruba bağlı değilken ekip sitesi oluşturabilirsiniz.|
|Stream|**Oluştur** menüsü altında Grup seçeneği **görünmüyor**.|
|Teams|Kullanıcı yeni bir grupla ekip oluşturamaz, ancak mevcut bir grubu kullanan bir ekip oluşturabilir.<br><br>**Ekip oluştur düğmesi** , Gruptan ekip **oluştur ile değiştirilir**.|
|Yammer|**Grup oluştur seçeneği** ana Gruplar/Topluluklar gezintilerinden kaldırılır.|

## <a name="services-interactions-with-groups"></a>Gruplarla hizmet etkileşimleri

Farklı grup türleri, bunların Microsoft 365 yönetilişi ve nasıl yönetilleri hakkında bilgi ve birkaç yönetim önerisi için Microsoft 365 Grupları posteri'ne bakın.

[![Gruplar bilgi grafiği için başparmak resmi.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf)

[PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx)

Aşağıdaki tablo, çeşitli hizmetlerle Microsoft 365 Grupları etkileşimlerine genel bir bakış sağlar:

|Ürün|Özellikler|Hizmet bir grup olmadan var mı?|Hizmet bir grup oluşturabilir mi?|Örneği silmek grubu siler mi?|
|---|---|---|---|---|
|Azure AD|Üyelik, Grup denetimleri, Konuklar|Evet|Evet|Evet|
|Exchange|Takvim, posta kutusu|Evet|Evet|Evet|
|Formlar|Form|Evet|Hayır|Hayır|
|OneNote|Not Defteri|Evet|Hayır|Hayır|
|Planner|Görev panosu|Hayır|Evet|Evet|
|Power Apps uygulaması|Uygulama|Evet|Hayır|Hayır|
|Power Automate|İş Akışı|Evet|Hayır|Hayır|
|Power BI (klasik)|Workspace|Hayır|Evet|Evet|
|Power BI (yeni)|Workspace|Evet|Hayır|Evet|
|Project için web'de arama|Project planı|Evet|Evet|Hayır|
|Yol Haritası|Yol Haritası|Evet|Evet|Hayır|
|SharePoint|Site|Evet|Evet|Evet|
|Stream|Kanal, video|Evet|Evet|Evet|
|Teams|Ekip|Hayır|Evet|Evet|
|Yammer|Grup|Evet|Evet|Evet|

Yukarıdaki tablo Microsoft 365 hizmetleriyle grup etkileşimleri hakkında üst düzey bir genel bakış sağlarken, anlamalısınız bazı nüanslar ve matrisler vardır. Aşağıdaki bölümlerde, belirli iş yüklerine ve gruplarla etkileşimlerine daha ayrıntılı bir bakış yer almaktadır.

## <a name="azure-ad"></a>Azure AD

Azure AD, tüm kullanıcılar genelinde temel kimlik yönetimi Microsoft 365.

**Gruplara sağlanan önemli özellikler**

- Grup üyeliği
- Adlandırma ilkesi
- Süre sonu ilkesi
- Konuklar
- Grup oluşturma kısıtlaması

**Azure AD bir Grup oluşturabilir mi?**

Evet Microsoft 365 Gruplar Azure AD'den yönetim web portalı, PowerShell veya Graph API aracılığıyla oluşturulabilir.

**Azure AD'de grup olmadan var mı?**

Evet, Azure AD, Gruplarla ilişkisiz çok sayıda Microsoft 365 gerçekleştirir. Her Microsoft 365 grubu Azure AD'de bir nesne olarak temsil eder.

**Grup başına birden çok Azure AD örneği olabilir mi?**

Hayır, Azure AD'nin yalnızca bir örneği vardır.

**Azure AD birden çok Grupla ilişkilendiril markalı olabilir mi?**

Evet, çünkü Azure AD grup üyeliği hizmetini sağlayan temel platformdur.

**Azure AD'nin bir grup değişikliğiyle ilişkilendirmesi olabilir mi?**

Hayır, Azure AD grupların bulunduğu temel platformdur.

**Örneği silmek Grubu siler mi?**

Azure AD'de grubun silinmesi, grupla ilişkili ilgili hizmetleri ve içeriği siler.

## <a name="teams"></a>Teams

Teams, çeşitli Microsoft ve üçüncü taraf hizmetleriyle etkileşim kurmak için tek bir arabirim sağlayarak işbirliğini geliştirme amaçlı, sohbet ortalı bir çalışma alanıdır.

Ekip oluşturulduğunda varsayılan olarak, Microsoft 365 grubuyla ilişkilendirilmiş posta kutusu ve takvim hem Exchange'daki Genel Adres Listesi'ne hem de Başka bir Outlook. Kullanıcı aynı grup üzerinde hem kullanıcı adını hem de son kullanıcı adını Outlook Teams bu Microsoft 365 geçersiz kılabilir.

**Gruplara sağlanan önemli özellikler**

- Konuşmalar
- Kanallar & sekmeler
- Toplantılar

**Grup Teams oluştursun mu?**

Evet, yeni ekip oluşturmak yeni bir ekip grubu Microsoft 365 olur. Ayrıca, henüz bir grubu yok olan bir grup için de ekip oluşturabilirsiniz.

**Ekipler grupsuz var mı?**

Hayır, bir ekibin Grup olmadan var olamaz.

**Grup başına birden çok ekip olabilir mi?**

Hayır, ekiple grup arasındaki ilişki 1:1'dir.

**Bir ekip birden çok grupla ilişkilendirilsin mi?**

Hayır, ekibin kendisi yalnızca tek bir grupla ilişkilendiriliyor.

**Ekibin bir grup değişikliğiyle bir ilişkilendirmesi olabilir mi?**

Hayır, ekip yalnızca başlangıçta ilişkilendirilen grupla ilişkilendiril olabilir.

**Ekip silin silinecek mi?**

Evet, ekip sitesi Microsoft Teams grubu, grupla ilişkili hizmetleri ve içeriği siler.

## <a name="exchange"></a>Exchange

Exchange Online, takvim, kişi ve ilişkili işlevler sağlar. Grup bağlamında, hizmet örneğinin tamamı yerine yalnızca tek bir kaynak ilişkilendirildi.

**Gruplara sağlanan önemli özellikler**

- Posta kutusu ve takvim
- Tüm Grup üyelerine e-posta gönderebilme
- Depolama Bulma Teams ilgili kanal konuşmalarının bir açıklaması, Planner yorumları

**Grup Exchange neden olabilir?**

Evet, hem genel yönetim merkezinden hem de Exchange Online bir grup Outlook. Ayrıca, tüm dağıtım Exchange kendi gruplarına Microsoft 365.

**Grup Exchange var mı?**

Evet, Exchange Online posta kutuları ve takvimler dahil herhangi bir grup ilişkilendirmesi olmadan çeşitli hizmetler sağlar.

**Her grup için birden çok Exchange kutusu veya takvim örneği olabilir mi?**

Hayır, bir grup için yalnızca tek Exchange Online posta kutusu ve takvim olabilir.

**Posta Exchange ve takvimlerin birden çok grupla ilişkilendiril mi?**

Hayır, posta kutusu ve takvimin grupla bire bir ilişkisi vardır. Posta kutusunu başka kullanıcılarla veya gruplarla paylaşmak mümkündür, ancak bu herhangi bir hizmet ilişkilendirmesi oluşturmaz.

**Posta Exchange veya takvimin bir grup değişikliğiyle ilişkilendirmesini sağlandı mı?**

Hayır, posta kutusu ve takvim farklı bir grupla değiştirilemez. Bununla birlikte, içerik bir posta kutusundan diğerine Outlook bir üçüncü taraf aracı kullanılarak da kullanılabilir.

**Posta kutusu silin silinecek mi?**

Evet, Posta Kutusu'nda Exchange kutusunun silinmesi, hem grubu hem de grupla ilişkili hizmetleri ve içeriği siler.

## <a name="forms"></a>Formlar

Forms, web tabanlı anketler ve testler sağlar.

**Gruplara sağlanan önemli özellikler**

- Formlara sahiplik

**Forms grup oluşturabilir mi?**

Hayır, Forms grup oluşturamaz.

**Formlar grup olmadan var mı?**

Evet, anketler ve testler doğrudan son kullanıcının hesabında oluşturulabilir.

**Her grup için birden çok form olabilir mi?**

Evet, bir grupla ilişkilendirilmiş birden çok form olabilir.

**Formlar birden çok grupla ilişkilendirilsin mi?**

Hayır, form yalnızca tek bir grupla ilişkilendirilebilirsiniz.

**Formun bir grup değişikliğiyle ilişkilendirmesi olabilir mi?**

Hayır, bir grupla ilişkilendirilmiş bir form (doğrudan içinde oluşturulduktan veya bireyden aktarılan sahiplik) başka bir gruba taşınamaz.

**Formu silmek grubu silebilir mi?**

Hayır, bir grubu Forms arabiriminden silmek mümkün değildir; yalnızca tek tek formlar vardır.

## <a name="onenote"></a>OneNote

OneNote, dijital bir not defteri uygulamasıdır. Grupla OneNote not defteri, grup bağlantılı bir hizmet SharePoint ilgili sitenin dosyasında yer alan bir dosyadır.

**Gruplara sağlanan önemli özellikler**

- Paylaşılan not defteri (Grupla ilişkilendirilmiş dosya SharePoint depolanır)

**Grup OneNote neden olabilir?**

Hayır, OneNote uygulaması grup oluşturamaz.

**Not OneNote grup olmadan var mı?**

Evet, not defterleri doğrudan aynı konumda OneDrive paylaşılan konumlarda oluşturulabilir.

**Her grup için birden OneNote not defteri olabilir mi?**

Evet, not defteri varsayılan olarak oluşturulur ve başkalarını da eklenebilir; bununla birlikte, grupla OneNote hizmetlerden not defteri bağlantısı her zaman varsayılan not defterine gider.

**Not OneNote birden çok grupla ilişkilendirilsin mi?**

Hayır, not defteri grupla ilişkilendirilmiş site kitaplığında SharePoint çeşitli arabirimlerden bağlantılıdır. Bununla birlikte, aynı tek tek bireylerle paylaşılır gibi diğer Gruplarla da paylaşılamaz.

**Not defterinin bir grup değişikliğiyle ilişkilendirmesi var mı?**

Hayır, not defterinin kendisi grupla ilişkilendirililir ve diğer grup bağlantılı hizmetlerden doğrudan erişilebilir, ancak içerik bir not defterinde bir not defterinden diğerine OneNote.

**Not defteri silinecek mi?**

Hayır, ancak OneNote defteri silinirse grupla ilişkilendirilmiş hizmetlerin bazılarında bozuk bağlantılar olabilir.

## <a name="planner"></a>Planner

Planner basit bir grup görevi yönetim hizmetidir.

**Gruplara sağlanan önemli özellikler**

- Grup görevlerini yönetmek için yönetim panosu

**Planner bir grup oluşturabilir mi?**

Evet, plan oluşturma işlemi yeni bir grup oluşturacak.

**Planner panosunda grup yok mu?**

Hayır, bir plan bir grupla ilişkilendirilmiş olmalı.

**Grup başına birden çok plan olabilir mi?**

Evet, grup başına birden çok plan olabilir.

**Bir plan birden çok grupla ilişkilendirilsin mi?**

Hayır, bir plan yalnızca erişimin belirlenmesi için grup üyeliğine dayandır.

**Bir planın grup değişikliğiyle bir ilişkilendirmesi olabilir mi?**

Hayır, ancak planı kopyalama yeni bir grup oluşturur.

> [!NOTE]
> Başka herhangi bir uygulama tarafından oluşturulan bir Grup, Planner'da kullanıcıya otomatik olarak gösterlanmaz. Başlangıçta board'a erişmek için onu Grup tabanlı başka bir arabirimden (örneğin, Grup) Outlook.

**Planı silmek grubu siler mi?**

Evet, planın silinmesi grupla ve grupla ilişkilendirilmiş hizmetleri ve içeriği siler.

## <a name="power-apps"></a>Power Apps

Power Apps kodu olmayan bir uygulama geliştirme tuvali sağlar.

**Gruplara sağlanan önemli özellikler**

- Uygulamalar çalıştırılacak ve değiştirilecek bir grupla paylaşılıyor olabilir

**Grup Power Apps neden olabilir?**

Hayır, Power Apps grup Microsoft 365 oluşturamaz.

**Grup Power Apps var mı?**

Evet, uygulamalar Power Apps içinde oluşturulabilir ve paylaşılana veya yayımlanana kadar creators hesabı içinde yer alır.

**Grup başına birden çok uygulama olabilir mi?**

Evet, bir grupla paylaşılan birden çok uygulama olabilir.

**Uygulamalar birden çok grupla ilişkilendirilsin mi?**

Evet, bir uygulama birden çok grupla paylaşabilirsiniz.

**Bir uygulamanın grup değişikliğiyle bir ilişkilendirmesi olabilir mi?**

Evet, Power Apps grupla Microsoft 365 ilişki olarak uygulama hala oluşturucuyla paylaştır.

> [!IMPORTANT]
> [Uygulamaların onlarla paylaşılamadan önce grupların güvenliğin etkinleştirilmesi gerekir](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Uygulama silinecek mi?**

Hayır, uygulamalar grupla paylaşılma dışında bir gruba bağlı değildir.

## <a name="power-automate"></a>Power Automate

Power Automate (eski adı Microsoft Flow) iş akışları ve otomasyon hizmetleri sağlar.

**Gruplara sağlanan önemli özellikler**

- İş akışları çalıştırılacak ve değiştirilecek bir grupla paylaşılır.

**Grup Power Automate oluştursun mu?**

Hayır, Power Automate bir Microsoft 365 ilişkilendirilen bir grup oluşturamaz.

Bununla birlikte, Azure AD güvenlik grubu oluşturma veya bir Güvenlik Grubu üyeliğini güncelleştirme gibi çeşitli işlemler gerçekleştiren bir akış Microsoft 365 mümkündür.

**Akışlar grup olmadan var mı?**

Evet, akışlar Power Automate oluşturulabilir ve paylaşılana veya yayımlanana kadar Creators hesabında yer alır.

**Grup başına birden çok akış olabilir mi?**

Evet, bir grupla paylaşılan birden çok akış olabilir.

**Bir akış birden çok grupla ilişkilendiril mi?**

Evet, akış birden çok grupla paylaşılamaz.

**Bir akışın grup değişikliğiyle bir ilişkilendirmesi olabilir mi?**

Evet, akış Power Automate bir Microsoft 365 grubu yalnızca paylaştır; akış yine oluşturucuyla birlikte yer alır.

**Bir akışı silmek grubu siler mi?**

Hayır, Power Apps gibi, akışlar grupla paylaşılma dışında bir gruba bağlı değildir.

## <a name="power-bi-classic"></a>Power BI (klasik)

Power BI veri odaklı panolar ve raporlar sağlar.

**Gruplara sağlanan önemli özellikler**

- Veri raporlama

**Grup Power BI oluştursun mu?**

Evet, klasik çalışma alanı oluşturmak yeni bir çalışma Microsoft 365 oluşturmanızı sağlar.

**Klasik Power BI alanı bir grup olmadan var mı?**

Hayır, [Çalışma Alanı'Power BI klasik çalışma alanı bir grupla ilişkilendirilmiş olması gerekir](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Her grup için birden Power BI çalışma alanı olabilir mi?**

Hayır, klasik çalışma alanıyla grup arasındaki ilişki 1:1'tir.

**Çalışma alanı birden çok grupla ilişkilendirilsin mi?**

Teknik olarak hayır, klasik çalışma alanı grupla birlikte oluşturulurken, içerik Grup dışında kullanıcılar ve güvenlik gruplarıyla paylaşılır.

**Çalışma alanı bir grup değişikliğiyle ilişkilendirmeyi var mı?**

Hayır, klasik çalışma alanının kendisi Grup'la ilişkilendirildi, ancak içerik Power BI arabirimi içinde bir çalışma alanından diğerine veya içeriği yerel olarak dışarı aktararak taşınır.

**Çalışma alanı silinecek mi?**

Evet, Çalışma Alanı alanı Power BI ve grupla ilişkilendirilmiş hizmetleri ve içeriği siler.

## <a name="power-bi-new"></a>Power BI (yeni)

Power BI veri odaklı panolar ve raporlar sağlar.

Power BI'ta yeni çalışma alanı oluşturulurken Microsoft 365 grubu oluşturmaz, ancak başka bir şekilde grup oluşturmak, çalışma alanında yeni (klasik değil) bir çalışma Power BI.

**Gruplara sağlanan önemli özellikler**

- Veri raporlama

**Grup Power BI oluştursun mu?**

Hayır, yeni Power BI arabiriminden Microsoft 365 grup oluşturmak Power BI değildir.

**Yeni Power BI alanı bir grup olmadan var mı?**

Evet, farklı gruplarla ilişkili Power BI içinde raporların ve çalışma alanlarının Microsoft 365 olabilir.

**Her grup için birden çok çalışma alanı olabilir mi?**

Evet, [çalışma alanı tarafından oluşturulan Power BI çalışma alanları tek bir grupla paylaşılamaz](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Çalışma alanı birden çok grupla ilişkilendirilsin mi?**

Hayır, Çalışma Alanı Power BI tek bir grupla ilişkilendiril kullanılabilir.

**Çalışma alanı bir grup değişikliğiyle ilişkilendirmeyi sağlar mı?**

Evet ve hayır. Çalışma alanı Power BI bir defada tek bir grupla ilişkilendiril olabilir, ancak ilişkilendirmeyi istediğiniz zaman değiştirebilir. Bir grup tarafından Power BI çalışma alanı bu grupla kalıcı olarak ilişkilendirildi.

**Çalışma alanı silinecek mi?**

Evet, Çalışma Alanı alanı Power BI grubu ve grupla ilişkilendirilmiş hizmetleri ve içeriği siler.

## <a name="project-for-the-web"></a>Project için web'de arama

Project web için özellik, proje planları, Gantt grafikleri ve yol haritaları oluşturma olanağı sunar.
Gruplara sağlanan önemli özellikler.

- Project planları

**Web Project grup oluştursun mu?**

Evet, doğrudan Web için Web için Microsoft 365 bir Project grubu oluşturmak mümkündür.

**Projeler bir grup olmadan var mı?**

Evet, projeler tek bir grupla ilişkilendirilmeden Microsoft 365, ancak görevlerin ataması grup ilişkilendirmesi gerektirir.

**Her grup için birden çok proje olabilir mi?**

Evet, tek bir grupta birden çok proje bağlamak mümkündür.

**Proje birden çok grupla ilişkilendirilsin mi?**

Hayır, bir proje yalnızca tek bir grupla ilişkilendiril olabilir.

**Projenin bir grup değişikliğiyle ilişkilendirmesi var mı?**

Hayır, bir grupla ilişki kurulduktan sonra bu ilişki değiştiremez.

**Proje silin silinecek mi?**

Hayır, web için Project'de projeyi silmek grubu silemez.

## <a name="roadmap"></a>Yol Haritası

Yol Haritası, web ve diğer web için yol Project yol haritaları oluşturabilme Project Online.

**Gruplara sağlanan önemli özellikler**

- Project yol haritaları

**Yol Haritası grup oluşturabilir mi?**

Evet, doğrudan yol haritasından yeni bir Microsoft 365 grup oluşturmak mümkündür.

**Yol Haritası bir grup olmadan var mı?**

Evet, yol haritaları bir grupla ilişkilendirilmeden Microsoft 365, yol haritasının paylaşımı grup ilişkilendirmesi gerektirir.

**Grup başına birden çok yol haritası olabilir mi?**

Evet, birden çok yol haritasını tek bir gruba bağlamak mümkündür.

**Yol haritası birden çok grupla ilişkilendirilsin mi?**

Hayır, yol haritası yalnızca tek bir grupla ilişkilendiril olabilir.

**Yol haritası bir grup değişikliğiyle ilişkilendirmeyi mümkün mü?**

Hayır, bir grupla ilişki kurulduktan sonra bu ilişki değiştiremez.

**Yol haritası silinecek mi?**

Hayır, yol haritasını silmek grubu silemez.

## <a name="sharepoint"></a>SharePoint

SharePoint, başka şeylerin arasında, çeşitli posta hizmetleri için depolama hizmetleri sağlayan web tabanlı bir Microsoft 365 platformudur.

**Gruplara sağlanan önemli özellikler**

- Belge kitaplığı
- Not defteri depolama OneNote kitaplığı
- Depolama wiki Teams içeriği

**Grup SharePoint neden olabilir?**

Evet, ekip sitesinde ekip sitesi SharePoint varsayılan olarak Microsoft 365 bir ekip grubu oluşturulur. Grup ve isteğe bağlı olarak mevcut bir site için ekip oluşturmak da mümkündür.

**Sitelerin SharePoint grup olmadan var mı?**

Evet, SharePoint grupla ilişkilendirilmiş olmayan çeşitli hizmetler ve iletişim ve merkez siteleri gibi siteler sunar. 

**Grup başına birden çok site olabilir mi?**

Hayır, grup başına yalnızca tek bir site olabilir. Aşağıdaki özel Teams gruba bağlı olan diğer siteleri kullanabilirsiniz.

**Siteler birden çok grupla ilişkilendirilsin mi?**

Teknik olarak hayır, ancak site bir grupla oluşturulsa da, içerik diğer gruplarla paylaşılır.

**Sitenin grup değişikliğiyle bir ilişkilendirmesi olabilir mi?**

Hayır, sitenin kendisi grupla ilişkilendirildi, ancak içerik SharePoint arabirimi içinde bir siteden diğerine, yerel olarak dışarı aktararak veya bir üçüncü taraf aracı kullanılarak taşınabiliyor.

**Site silinecek mi?**

Evet, site sitenin SharePoint ve grupla ilişkilendirilmiş hizmetleri ve içeriği siler.

## <a name="stream"></a>Stream

Microsoft Stream, bir video barındırma ve paylaşma platformudur.

**Gruplara sağlanan önemli özellikler**

- Video depolama
- Teams kaydını kaydetme
- Video kanalları

**Akış bir grup oluşturabilir mi?**

Evet, doğrudan Stream'den yeni bir Microsoft 365 grup oluşturmak mümkündür.

**Stream bir grup olmadan var mı?**

Evet, video kanalları ve videolar bir grupla ilişkilendirilmeden Stream'de yer almaktadır.

**Grup başına birden çok video ve kanal olabilir mi?**

Evet, her grupta birden çok video ve kanal olabilir.

**Bir video veya kanal birden çok grupla ilişkilendirilsin mi?**

Evet, bir grupla video veya kanal oluşturulduğunda, bu video veya kanal diğer gruplarla paylaşılır.

**Bir Grup değişikliğiyle ilişkilendirmeyi var mı?**

Evet ve hayır; Stream'daki videolar orijinal karşıya yükleyiciye veya toplantı kaydediciye aittir ve bu nedenle herhangi bir grupla ilişkilendirilebilirsiniz, ancak video kanalları yalnızca başlangıçta oluşturulduları grupla ilişkilendirilebilirsiniz.

**Videoları veya kanalları silmek grubu siler mi?**

Hayır, videoları veya kanalları silmek grubu silemez. Bununla birlikte, grubun kendisini Stream'de silmek, gerçek videolar dışında grupla ilişkilendirilmiş hizmetleri ve içeriği siler.

## <a name="yammer"></a>Yammer

Yammer, kuruluşlar arasında ve içinde topluluk katılımını teşvik etmek için tasarlanmış kurumsal bir sosyal platformdur.

Bir topluluk (daha önce "grup" olarak bilinirdi) Yammer bir posta kutusu oluşturur, ancak şu anda bu kutu kullanılamaz.

Microsoft 365 ekibiyle ilişkilendirilmiş Yammer grup, başka bir ekiple Microsoft Teams.

**Gruplara sağlanan önemli özellikler**

- Konuşma alanı

**Grup Yammer oluştur Microsoft 365 var mı?**

Evet, platformlar bağlı Yammer kullanıcının grup oluşturma özelliği varsa Microsoft 365 yeni bir Grup Oluştur grubu oluşturulur.

İlişkili Yammer grupla Microsoft 365, kendisinde değil, hiçbir arabirim veya hizmette Yammer oluşturulamaz.

**Yammer grubu olmayan bir Microsoft 365 var mı?**

Evet, grup oluşturmadan Yammer grup Microsoft 365 mümkündür.

Yammer platformu Microsoft 365 gruplarına bağlı değilse veya kullanıcıların Microsoft 365 grubu oluşturma özelliği yoksa, Yammer grupları Microsoft 365 ilişki olmadan oluşturulur.

**Her grup için Yammer grup Microsoft 365 olabilir mi?**

Hayır, grup ve Yammer arasındaki ilişki Microsoft 365:1'tir.

**Bir Yammer birden fazla grupla ilişkilendirilen bir Microsoft 365 olabilir mi?**

Hayır, Yammer grubu yalnızca tek bir grupla Microsoft 365 olabilir. Gönderilerin diğer gruplarla paylaşılıyor veya diğer gruplarla Yammer mümkündür.

**Bir grup Yammer bir grup değişikliğiyle Microsoft 365 olabilir mi?**

Hayır, Yammer grubu ancak başlangıçta ilişkilendirilmiş Microsoft 365 grupla ilişkilendiril olabilir.

**Bu grup Yammer, ilk grubu Microsoft 365 siler mi?**

Evet, Microsoft'ta grup Yammer ilgili Microsoft grubu ve grupla ilişkili hizmetler ve içeriği siler.

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)
