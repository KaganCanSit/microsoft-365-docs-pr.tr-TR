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
ms.openlocfilehash: 64de83690edb96e3bf7a889309c262a92f8e8193
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286351"
---
# <a name="groups-services-interactions"></a>Grup hizmetleri etkileşimleri

Microsoft 365 Grupları, son kullanıcılara bağlı bir deneyim sunmak üzere Microsoft 365 platformundaki çeşitli hizmetler ve iş yükleri için ortak bir doku sağlar. Temel olarak, aşağıdakileri sağlamak için bir Microsoft 365 grubu vardır:

- Üyeliği yönetmenin bir yolu (Azure AD)
- Mesajlaşma ve konuşmalar için bir yer (posta kutusu, Microsoft Teams Yammer Exchange)
- Dosyaların depolandığı bir yer (SharePoint)
- Zamanlama için bir takvim (Exchange)
- Notları yakalamak için bir not defteri (OneNote)

Grup oluşturma noktasında, diğer birkaç kaynak da sağlanır, ancak hizmetten ilk kez erişilene kadar bunlar görünmez:

- Grup görevlerini yönetmek için bir pano (Planner)
- Raporlama için çalışma alanı (Power BI)
- Paylaşılan videolar için bir alan (Microsoft Stream)
- Paylaşılan formlar için bir alan (Formlar)

Microsoft 365 genelinde, diğer hizmetler grup üyelerine ek işlevler ve yetenekler sunmak için Microsoft 365 gruplarla etkileşim kurabiliyor.
Buna örnek olarak şunlar verilebilir:

- Uygulamalar için Power Apps
- İş akışları için Power Automate
- Şelale tabanlı proje yönetimi için web'de Project ve Yol Haritası
- Kanal tabanlı konuşmalar için Teams
- İlgi alanları için Yammer

## <a name="user-interactions-with-groups"></a>Gruplarla kullanıcı etkileşimleri

Microsoft 365 Grupları hem yöneticiler hem de son kullanıcılar tarafından çeşitli arabirimlerden oluşturulabilir ve yönetilebilir. 

### <a name="administrative-experiences"></a>Yönetim deneyimleri

Yöneticiler çeşitli iş yükü yönetim merkezlerinden Microsoft 365 grupları, betiği destekleyen komut satırı arabirimlerinin yanı sıra Graph API ile etkileşim kuran özel olarak oluşturulmuş uygulamalar oluşturabilir ve yönetebilir. Bunun tek istisnası, Yammer web arabiriminden oluşturulması gereken Yammer gruplarıdır.

**İlgili ayarlar**

Grup ayarlarını yönetebilen çeşitli yönetim arabirimleri arasında, bilmeniz gereken birkaç çakışma vardır.

**Microsoft 365 yönetici merkezi**

Microsoft 365 yönetim merkezi, sahiplerin konuk eklemesine izin verme özelliği de varsayılan olarak Gruplar'a konuk erişimi etkindir. Bu yönetim merkezinden Gruplar için başka kuruluş düzeyinde denetim yoktur.

**Azure AD yönetim merkezi**

Azure AD yönetim merkezi, kullanıcıların Azure portallarında Grup oluşturup oluşturamayacağı veya sahip atayabileceğine ilişkin denetimlerin yanı sıra süre sonu ve adlandırma ilkesi ayarları sunar.

Yönetim merkezi ayrıca, sahip olmayanların da konuk davet edip edemeyeceğini sınırlama gibi Microsoft 365 yönetim merkezi ötesinde birkaç konuk daveti denetimi önlemi sağlar

**SharePoint**

SharePoint siteler Sahip, Üye ve Ziyaretçi güvenlik gruplarıyla oluşturulur ve ilk ikisi Microsoft 365 grup karşılıklarıyla eşleşmektedir. SharePoint Online sitelerinin üyeliği genellikle ilişkili Microsoft 365 grubu tarafından yönetilse de, çift yönlü bir ilişki değildir. Microsoft 365 grup düzeyindeki üyelik değişiklikleri SharePoint yansıtılır, ancak üyelik SharePoint grubunda değiştirilirse, bu Microsoft 365 grubuna yansıtılmaz.

### <a name="user-experiences"></a>Kullanıcı deneyimleri

Son kullanıcılar Microsoft 365 içindeki çeşitli hizmetlerden gruplar oluşturabilir ve bazılarında yalnızca bir grupla paylaşabilir.

Aşağıdaki hizmetler, son kullanıcılar tarafından grup oluşturulmasına olanak sağlar:

- Outlook
- Planner
- Web için Project
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Grup oluşturma kısıtlaması

Ekiplerin yayılmasını denetlemenin yaygın bir yaklaşımı, hangi kullanıcıların bunları oluşturabileceğini sınırlamaktır. Bu yalnızca grupların oluşturulmasını sınırlayarak yapılabilir. Bunu yapmak, son kullanıcı için gerekli olabilecek diğer hizmetlerden grup oluşturma özelliğini etkiler. Microsoft 365 Grupları, bazı uygulamalardan veya hizmetlerden grup oluşturmayı kısıtlamayı ve diğer uygulamalardan izin verme özelliğini desteklemez.

Grup oluşturma kısıtlaması deneyimi uygulamalar ve hizmetler arasında farklılık gösterir:

|Uygulama veya hizmet|Deneyim|
|---|---|
|Outlook|**Yeni grup** seçeneği Kişiler sayfasındaki Yeni menüden kaldırıldı|
|Planner|**Yeni plan** , grup oluşturmanın kapatıldığını ve planı mevcut bir gruba eklemeyi teklif ettiğini açıklar|
|Web ve Yol Haritası için Project|**Grup oluştur menüsü,** grup oluşturmanın kısıtlandığını açıklar ve mevcut bir grubu kullanmayı önerir.|
|SharePoint|Yine de bir gruba bağlı olmayan bir ekip sitesi oluşturabiliyor.|
|Stream|**Grup** seçeneği **Oluştur menüsünün** altında görünmez.|
|Teams|Kullanıcı yeni bir grupla ekip oluşturamaz, ancak yine de mevcut bir grubu kullanan bir ekip oluşturabilir.<br><br>**Ekip oluştur** düğmesi, **Gruptan ekip oluştur** ile değiştirilir.|
|Yammer|**Grup oluştur** seçeneği ana Gruplar/Topluluklar gezintisinden kaldırılır.|

## <a name="services-interactions-with-groups"></a>Gruplarla hizmet etkileşimleri

Farklı grup türleri, bunların nasıl oluşturulduğu ve yönetilme şekli ve birkaç idare önerisi hakkında bilgi için Microsoft 365'deki Gruplar posterini inceleyin.

[![Gruplar için başparmak görüntüsü bilgi grafiği.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf)

[PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx)

Aşağıdaki tabloda çeşitli hizmetlerle Microsoft 365 Grupları etkileşimlerine genel bir bakış sağlanır:

|Ürün|Özellik|Hizmet bir grup olmadan mı var?|Hizmet bir grup oluşturabilir mi?|Örnek silindiğinde grup silinir mi?|
|---|---|---|---|---|
|Azure AD|Üyelik, Grup denetimleri, Konuklar|Evet|Evet|Evet|
|Exchange|Takvim, posta kutusu|Evet|Evet|Evet|
|Forms|Form|Evet|Hayır|Hayır|
|OneNote|Dizüstü|Evet|Hayır|Hayır|
|Planner|Görev panosu|Hayır|Evet|Evet|
|Power Apps uygulaması|Uygulama|Evet|Hayır|Hayır|
|Power Automate|Iş akışı|Evet|Hayır|Hayır|
|Power BI (klasik)|Workspace|Hayır|Evet|Evet|
|Power BI (yeni)|Workspace|Evet|Hayır|Evet|
|Web için Project|Project planı|Evet|Evet|Hayır|
|Yol Haritası|Yol Haritası|Evet|Evet|Hayır|
|SharePoint|Site|Evet|Evet|Evet|
|Stream|Kanal, video|Evet|Evet|Evet|
|Teams|Takım|Hayır|Evet|Evet|
|Yammer|Grup|Evet|Evet|Evet|

Yukarıdaki tabloda Microsoft 365 hizmetleriyle grup etkileşimlerine üst düzey bir genel bakış sağlansa da, anlamanız gereken çeşitli nüanslar ve incelik vardır. Aşağıdaki bölümlerde belirli iş yüklerine ve gruplarla etkileşimlerine daha ayrıntılı bir bakış sağlanır.

## <a name="azure-ad"></a>Azure AD

Azure AD, Microsoft 365 genelinde temel alınan kimlik yönetimi özelliklerini sağlar.

**Gruplara sağlanan temel özellikler**

- Grup üyeliği
- Adlandırma ilkesi
- Süre sonu ilkesi
- Konuklar
- Grup oluşturma kısıtlaması

**Grup oluşturabilir Azure AD?**

Evet, Microsoft 365 Grupları yönetim web portalı, PowerShell veya Graph API aracılığıyla Azure AD oluşturulabilir.

**Grup olmadan Azure AD var mı?**

Evet, Azure AD Microsoft 365 Grupları ilişkisi olmayan çok sayıda hizmet gerçekleştirir. Her Microsoft 365 grubu, Azure AD bir nesne olarak temsil edilir.

**Grup başına birden çok Azure AD örneği olabilir mi?**

Hayır, Azure AD yalnızca bir örneği vardır.

**Azure AD birden çok Grupla ilişkilendirilebilir mi?**

Evet, çünkü grup üyeliği hizmetini sağlayan temel platform Azure AD.

**Azure AD'nin grupla ilişkisi değişebilir mi?**

Hayır, Azure AD grupların bulunduğu temel platformdur.

**Örnek silindiğinde Grup silinir mi?**

Azure AD'da grubun silinmesi, grupla ilişkili ilgili hizmetleri ve içeriği siler.

## <a name="teams"></a>Teams

Teams, çeşitli Microsoft ve üçüncü taraf hizmetleriyle etkileşime geçmek için tekil bir arabirim sağlayarak işbirliğini geliştirmeyi amaçlayan sohbet merkezli bir çalışma alanıdır.

Varsayılan olarak, bir ekip oluşturulduğunda, Microsoft 365 grubuyla ilişkilendirilmiş posta kutusu ve takvim hem Exchange'deki Genel Adres Listesi'nden hem de Outlook gizlenir. Bu, kullanıcı aynı Microsoft 365 grubunda hem Outlook hem de Teams kullanmak isterse yönetici tarafından el ile geçersiz kılınabilir.

**Gruplara sağlanan temel özellikler**

- Konuşma
- Kanallar & sekmeler
- Toplantılar

**Teams grup oluşturabilir misiniz?**

Evet, yeni bir ekip oluşturmak yeni bir Microsoft 365 grubu oluşturur. Şu anda bir grubu olmayan mevcut bir grup için ekip oluşturmak da mümkündür.

**Ekipler grup olmadan var mı?**

Hayır, bir ekibin Grup olmadan var olması mümkün değildir.

**Grup başına birden çok ekip olabilir mi?**

Hayır, bir ekiple grup arasındaki ilişki 1:1'dir.

**Bir ekip birden çok grupla ilişkilendirilebilir mi?**

Hayır, takımın kendisi yalnızca tek bir grupla ilişkilendirilebilir.

**Bir ekibin grupla ilişkisi değişebilir mi?**

Hayır, ekip yalnızca ilk ilişkilendirildiği grupla ilişkilendirilebilir.

**Ekip silindiğinde grup silinir mi?**

Evet, ekibin Microsoft Teams silinmesi grubu, grupla ilişkili hizmetleri ve içeriği siler.

## <a name="exchange"></a>Exchange

Exchange Online mesajlaşma, takvim, kişi ve ilişkili işlevler sağlar. Bir Grup bağlamında, tüm hizmet örneğinin aksine yalnızca tek bir kaynak ilişkilendirilir.

**Gruplara sağlanan temel özellikler**

- Posta kutusu ve takvim
- Tüm Grup üyelerine e-posta gönderebilme
- eBulma amacıyla Teams kanal konuşmalarının Depolama, Planner açıklamaları

**Exchange grup oluşturabilir misiniz?**

Evet, Exchange Online yönetim merkezinden ve Outlook bir grup oluşturmak mümkündür. Ayrıca Exchange dağıtım listelerini Microsoft 365 gruplara dönüştürebilirsiniz.

**Grup olmadan Exchange var mı?**

Evet, Exchange Online paylaşılan posta kutuları ve takvimler dahil olmak üzere grup ilişkilendirmesi olmadan çeşitli hizmetler sağlar.

**Grup başına birden çok Exchange posta kutusu veya takvim örneği olabilir mi?**

Hayır, bir grup için yalnızca tek bir Exchange Online posta kutusu ve takvim olabilir.

**Exchange posta kutuları ve takvimler birden çok grupla ilişkilendirilebilir mi?**

Hayır, posta kutusu ve takvim grupla 1:1 ilişkisine sahiptir. Posta kutusunu diğer kullanıcılar veya gruplarla paylaşmak mümkündür, ancak bu herhangi bir hizmet ilişkisi biçimi oluşturmaz.

**Exchange posta kutusunun veya takvimin grupla ilişkisi değişebilir mi?**

Hayır, posta kutusu ve takvim farklı bir gruba değiştirilemez. Ancak içerik, Outlook içinde veya üçüncü taraf bir araç kullanılarak bir posta kutusundan diğerine taşınabilir.

**Posta kutusu silindiğinde grup silinir mi?**

Evet, Exchange'deki posta kutusu silindiğinde grupla ilişkili hizmetlerin ve içeriğin yanı sıra grup silinir.

## <a name="forms"></a>Forms

Formlar web tabanlı anketler ve testler sağlar.

**Gruplara sağlanan temel özellikler**

- Formların sahipliği

**Formlar grup oluşturabilir mi?**

Hayır, Formlar grup oluşturamaz.

**Formlar grup olmadan var mı?**

Evet, anketler ve testler doğrudan son kullanıcının hesabında oluşturulabilir.

**Grup başına birden çok form olabilir mi?**

Evet, bir grupla ilişkilendirilmiş birden çok form olabilir.

**Formlar birden çok grupla ilişkilendirilebilir mi?**

Hayır, form yalnızca tek bir grupla ilişkilendirilebilir.

**Formun grupla ilişkisi değişebilir mi?**

Hayır, bir form bir grupla ilişkilendirildikten (doğrudan içinde oluşturulduktan veya bir bireyden aktarılan sahiplik) başka bir gruba taşınamaz.

**Form silindiğinde grup silinir mi?**

Hayır, Bir grubu Formlar arabiriminden silmek mümkün değildir, yalnızca tek tek formlar.

## <a name="onenote"></a>OneNote

OneNote dijital bir not defteri uygulamasıdır. Grupla oluşturulan OneNote not defteri, grup bağlantılı hizmet yerine ilişkili SharePoint sitesinde bulunan bir dosyadır.

**Gruplara sağlanan temel özellikler**

- Paylaşılan not defteri (Grupla ilişkili SharePoint kitaplığında depolanır)

**OneNote grup oluşturabilir misiniz?**

Hayır, OneNote uygulaması grup oluşturamaz.

**OneNote not defterleri grup olmadan var mı?**

Evet, not defterleri doğrudan OneDrive veya diğer paylaşılan konumlarda oluşturulabilir.

**Grup başına birden çok OneNote not defteri olabilir mi?**

Evet, varsayılan olarak bir not defteri oluşturulur ve diğerleri eklenebilir, ancak grupla ilişkili hizmetlerden OneNote bağlantısı her zaman varsayılan not defterine gider.

**OneNote not defteri birden çok grupla ilişkilendirilebilir mi?**

Hayır, not defteri grupla ilişkili SharePoint site kitaplığında depolanır ve çeşitli arabirimlerden bağlanır. Öte yandan diğer Gruplarla da aynı şekilde paylaşılabilir.

**Not defterinin grupla ilişkisi değişebilir mi?**

Hayır, not defterinin kendisi grupla ilişkilendirilir ve gruba bağlı diğer hizmetlerden doğrudan erişilebilir, ancak içerik OneNote uygulamasında bir not defterinden diğerine taşınabilir.

**Not defteri silindiğinde grup silinir mi?**

Hayır, ancak OneNote not defteri silinirse grupla ilişkili bazı hizmetlerde bozuk bağlantılar olabilir.

## <a name="planner"></a>Planner

Planner basit bir grup görev yönetimi hizmetidir.

**Gruplara sağlanan temel özellikler**

- Grup görevlerini yönetmek için pano

**Planner bir grup oluşturabilir mi?**

Evet, plan oluşturmak yeni bir grup oluşturur.

**Planner panosu bir grup olmadan var mı?**

Hayır, bir plan bir grupla ilişkilendirilmelidir.

**Grup başına birden çok plan olabilir mi?**

Evet, grup başına birden çok plan olabilir.

**Bir plan birden çok grupla ilişkilendirilebilir mi?**

Hayır, bir plan erişimi belirlemek için yalnızca grup üyeliğine dayanır.

**Bir planın grupla ilişkisi değişebilir mi?**

Hayır, ancak planı kopyalamak yeni bir grup oluşturur.

> [!NOTE]
> Başka bir uygulama tarafından oluşturulan bir Grup, Planner'da bir kullanıcı için otomatik olarak gösterilmez. Panoya başlangıçta erişmek için panoyu Outlook gibi başka bir Grup tabanlı arabirimden açmaları gerekir.

**Plan silindiğinde grup silinir mi?**

Evet, planı sildiğinizde grup ve grupla ilişkili hizmetler ve içerik silinir.

## <a name="power-apps"></a>Power Apps

Power Apps, kod olmadan uygulama geliştirme için bir tuval sağlar.

**Gruplara sağlanan temel özellikler**

- Uygulamalar çalıştırılacak ve değiştirilecek bir grupla paylaşılabilir

**Power Apps grup oluşturabilir misiniz?**

Hayır, Power Apps Microsoft 365 grubu oluşturamaz.

**Grup olmadan Power Apps var mı?**

Evet, uygulamalar Power Apps içinde oluşturulabilir ve paylaşılana veya yayımlanana kadar oluşturucu hesabında bulunabilir.

**Grup başına birden çok uygulama olabilir mi?**

Evet, bir grupla paylaşılan birden çok uygulama olabilir.

**Uygulamalar birden çok grupla ilişkilendirilebilir mi?**

Evet, bir uygulama birden çok grupla paylaşılabilir.

**Bir uygulamanın grupla ilişkisi değişebilir mi?**

Evet, Power Apps ile bir Microsoft 365 grubu arasındaki ilişki yalnızca paylaşımda olduğundan uygulama yine de oluşturucuda yer alır.

> [!IMPORTANT]
> [Uygulamaların onlarla paylaşılabilmesi için önce grupların güvenlik etkin olması gerekir](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Uygulama silindiğinde grup silinir mi?**

Hayır, uygulamalar onlarla paylaşılmak dışında gruba bağlı değildir.

## <a name="power-automate"></a>Power Automate

Power Automate (eski adıyla Microsoft Flow) iş akışları ve otomasyon hizmetleri sağlar.

**Gruplara sağlanan temel özellikler**

- İş akışları, çalıştırılacak ve değiştirilecek bir grupla paylaşılabilir.

**Grup oluşturabilir Power Automate?**

Hayır, Power Automate bir grupla ilişkilendirilen bağlamda bir Microsoft 365 grubu oluşturamaz.

Ancak, Azure AD güvenlik grubu oluşturma veya bir Microsoft 365 grubunun üyeliğini güncelleştirme gibi çeşitli işlemler gerçekleştiren bir akış oluşturmak mümkündür.

**Akışlar grup olmadan var mı?**

Evet, akışlar Power Automate içinde oluşturulabilir ve paylaşılana veya yayımlanana kadar oluşturucu hesabında bulunabilir.

**Grup başına birden çok akış olabilir mi?**

Evet, bir grupla paylaşılan birden çok akış olabilir.

**Bir akış birden çok grupla ilişkilendirilebilir mi?**

Evet, bir akış birden çok grupla paylaşılabilir.

**Bir akışın grupla ilişkisi değişebilir mi?**

Evet, Power Automate ve Microsoft 365 grubu arasındaki ilişki yalnızca paylaşımda olduğundan akış yine de oluşturucuyla birlikte kalır.

**Akış silindiğinde grup silinir mi?**

Hayır, Power Apps gibi akışlar da onlarla paylaşılmak dışında gruba bağlı değildir.

## <a name="power-bi-classic"></a>Power BI (klasik)

Power BI, etkileşimli veri temelli panolar ve raporlar sağlar.

**Gruplara sağlanan temel özellikler**

- Veri raporlama

**Power BI grup oluşturabilir misiniz?**

Evet, klasik çalışma alanı oluşturmak bir Microsoft 365 grubu oluşturur.

**Power BI klasik çalışma alanı grup olmadan mı var?**

Hayır, [Power BI'deki klasik bir çalışma alanı bir grupla ilişkilendirilmelidir](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Grup başına birden çok Power BI çalışma alanı olabilir mi?**

Hayır, klasik çalışma alanıyla grup arasındaki ilişki 1:1'dir.

**Çalışma alanı birden çok grupla ilişkilendirilebilir mi?**

Teknik olarak hayır, klasik çalışma alanı grupla birlikte oluşturulurken, içerik kullanıcılar ve güvenlik gruplarıyla Grubun dışında paylaşılabilir.

**Çalışma alanının grupla ilişkisi değişebilir mi?**

Hayır, klasik çalışma alanının kendisi Grupla ilişkilendirilir, ancak içerik Power BI arabiriminde veya içeriği yerel olarak dışarı aktarılarak bir çalışma alanından diğerine taşınabilir.

**Çalışma alanı silindiğinde grup silinir mi?**

Evet, Power BI'deki çalışma alanı silindiğinde grup ve grupla ilişkili hizmetler ve içerik silinir.

## <a name="power-bi-new"></a>Power BI (yeni)

Power BI, etkileşimli veri temelli panolar ve raporlar sağlar.

Power BI'da yeni bir çalışma alanı oluşturmak Microsoft 365 grubu oluşturmazken, başka herhangi bir yolla grup oluşturmak Power BI'da yeni (klasik olmayan) bir çalışma alanı oluşturur.

**Gruplara sağlanan temel özellikler**

- Veri raporlama

**Power BI grup oluşturabilir misiniz?**

Hayır, yeni Power BI arabiriminden bir Microsoft 365 grubu oluşturmak mümkün değildir.

**Yeni Power BI çalışma alanı bir grup olmadan var mı?**

Evet, Microsoft 365 gruplarla ilişkilendirilmemiş raporların ve çalışma alanlarının Power BI oluşturulması mümkündür.

**Grup başına birden çok çalışma alanı olabilir mi?**

Evet, [Power BI tarafından oluşturulan birden çok çalışma alanı tek bir grupla paylaşılabilir](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Çalışma alanı birden çok grupla ilişkilendirilebilir mi?**

Hayır, Power BI tarafından oluşturulan bir çalışma alanı yalnızca tek bir grupla ilişkilendirilebilir.

**Bir çalışma alanının grupla ilişkisi değişebilir mi?**

Evet ve hayır. Power BI tarafından oluşturulan bir çalışma alanı aynı anda yalnızca tek bir grupla ilişkilendirilebilir, ancak herhangi bir zamanda ilişkilendirmeyi değiştirebilir. Bir grup tarafından Power BI oluşturulan çalışma alanı, bu grupla kalıcı olarak ilişkilendirilir.

**Çalışma alanı silindiğinde grup silinir mi?**

Evet, Power BI'deki çalışma alanı silindiğinde grup ve grupla ilişkili hizmetler ve içerik silinir.

## <a name="project-for-the-web"></a>Web için Project

Web için Project proje planları, Gantt grafikleri ve yol haritaları oluşturma olanağı sunar.
Gruplara sağlanan temel özellikler.

- planları Project

**Web için Project grup oluşturabilir mi?**

Evet, doğrudan web için Project yeni bir Microsoft 365 grubu oluşturmak mümkündür.

**Projeler grup olmadan var mı?**

Evet, projeler bir Microsoft 365 grubuyla ilişkilendirilmeden var olabilir, ancak görevlerin atanması için grup ilişkilendirmesi gerekir.

**Grup başına birden çok proje olabilir mi?**

Evet, tek bir grupta birden çok proje bağlamak mümkündür.

**Proje birden çok grupla ilişkilendirilebilir mi?**

Hayır, bir proje yalnızca tek bir grupla ilişkilendirilebilir.

**Bir projenin grupla ilişkisi değişebilir mi?**

Hayır, bir grupla ilişki kurulduktan sonra değiştirilemez.

**Proje silindiğinde grup silinir mi?**

Hayır, web için Project proje silindiğinde grup silinmez.

## <a name="roadmap"></a>Yol Haritası

Yol haritası, web ve Project Online için Project ile proje yol haritaları oluşturma olanağı sağlar.

**Gruplara sağlanan temel özellikler**

- Project yol haritaları

**Yol Haritası bir grup oluşturabilir mi?**

Evet, doğrudan yol haritasından yeni bir Microsoft 365 grubu oluşturmak mümkündür.

**Yol haritası bir grup olmadan var mı?**

Evet, yol haritaları bir Microsoft 365 grubuyla ilişkilendirilmeden mevcut olabilir, ancak yol haritasının paylaşılması için grup ilişkilendirmesi gerekir.

**Grup başına birden çok yol haritası olabilir mi?**

Evet, birden çok yol haritasını tek bir gruba bağlamak mümkündür.

**Yol haritası birden çok grupla ilişkilendirilebilir mi?**

Hayır, yol haritası yalnızca tek bir grupla ilişkilendirilebilir.

**Yol haritasının grupla ilişkisi değişebilir mi?**

Hayır, bir grupla ilişki kurulduktan sonra değiştirilemez.

**Yol haritası silindiğinde grup silinir mi?**

Hayır, yol haritası silindiğinde grup silinmez.

## <a name="sharepoint"></a>SharePoint

SharePoint, çeşitli Microsoft 365 hizmetleri için depolama hizmetleri gibi diğer özellikleri de sağlayan web tabanlı bir içerik yönetimi platformudur.

**Gruplara sağlanan temel özellikler**

- Belge kitaplığı
- OneNote not defterini depolama kitaplığı
- Teams wiki dosyalarının Depolama

**SharePoint grup oluşturabilir misiniz?**

Evet, SharePoint'da ekip sitesi oluşturmak varsayılan olarak bir Microsoft 365 grubu oluşturur. Ayrıca, mevcut bir site için bir grup ve isteğe bağlı olarak bir ekip oluşturmak da mümkündür.

**Grup olmadan SharePoint site var mı?**

Evet, SharePoint iletişim ve merkez siteleri gibi grupla ilişkili olmayan birkaç hizmet ve site sunar. 

**Grup başına birden çok site olabilir mi?**

Hayır, grup başına yalnızca tek bir site olabilir. Teams'daki özel ve paylaşılan kanallar, gruba bağlı olmayan ek siteler kullanır.

**Siteler birden çok grupla ilişkilendirilebilir mi?**

Teknik olarak hayır, ancak site bir grupla oluşturulurken içerik diğer gruplarla paylaşılabilir.

**Bir sitenin grupla ilişkisi değişebilir mi?**

Hayır, sitenin kendisi grupla ilişkilendirilir, ancak içerik, içeriği yerel olarak dışarı aktararak veya üçüncü taraf bir araç kullanarak SharePoint arabiriminde bir siteden diğerine taşınabilir.

**Site silindiğinde grup silinir mi?**

Evet, site SharePoint silindiğinde grup ve grupla ilişkili hizmetler ve içerik silinir.

## <a name="stream"></a>Stream

Microsoft Stream bir video barındırma ve paylaşma platformudur.

**Gruplara sağlanan temel özellikler**

- Video depolama
- Toplantı kaydını Teams
- Video kanalları

**Stream grup oluşturabilir mi?**

Evet, doğrudan Stream'den yeni bir Microsoft 365 grubu oluşturmak mümkündür.

**Stream bir grup olmadan var mı?**

Evet, video kanalları ve videolar bir grupla ilişkilendirilmeden Stream'de bulunabilir.

**Grup başına birden çok video ve kanal olabilir mi?**

Evet, her grupta birden çok video ve kanal olabilir.

**Bir video veya kanal birden çok grupla ilişkilendirilebilir mi?**

Evet, bir grupla bir video veya kanal oluşturulurken, diğer gruplarla paylaşılabilir.

**Grupla ilişkisi değişebilir mi?**

Evet ve hayır; Stream'deki videolar özgün yükleyiciye veya toplantı kaydedicisine aittir ve bu nedenle herhangi bir grupla ilişkilendirilebilir, ancak video kanalları yalnızca başlangıçta oluşturuldukları grupla ilişkilendirilebilir.

**Videoları veya kanalları silmek grubu siler mi?**

Hayır, videoları veya kanalları silmek grubu silmez. Ancak Stream'de grubun kendisini silmek, gerçek videolar dışında grupla ilişkili hizmetleri ve içeriği siler.

## <a name="yammer"></a>Yammer

Yammer, kuruluşlar içinde ve arasında topluluk katılımını teşvik etmek için tasarlanmış kurumsal bir sosyal platformdur.

Yammer'da bir topluluk (eski adıyla "grup") oluşturmak bir posta kutusu oluşturur, ancak şu anda bu kullanılmaz.

Yammer ile ilişkilendirilmiş bir Microsoft 365 grubu Microsoft Teams bir ekiple kullanılamaz.

**Gruplara sağlanan temel özellikler**

- Konuşma alanı

**Microsoft 365 grubu Yammer oluşturabilir misiniz?**

Evet, Yammer'de yeni bir grup oluşturmak, platformlar bağlıysa ve kullanıcının grup oluşturma yeteneğine sahipse yeni bir Microsoft 365 grubu oluşturur.

İlişkili Microsoft 365 grubuna sahip bir Yammer grubu, Yammer dışında hiçbir arabirimde veya hizmette oluşturulamaz.

**Microsoft 365 grubu olmayan bir Yammer grubu var mı?**

Evet, Microsoft 365 grubu olmayan bir Yammer grubu oluşturmak mümkündür.

Yammer platformu Microsoft 365 gruplarına bağlı değilse veya kullanıcılar Microsoft 365 grubu oluşturma yeteneğine sahip değilse, Microsoft 365 grup ilişkilendirmesi olmadan Yammer gruplar oluşturulur.

**Microsoft 365 grubu başına birden çok Yammer grubu olabilir mi?**

Hayır, bir Yammer grubu ile Microsoft 365 grubu arasındaki ilişki 1:1'dir.

**Bir Yammer grubu birden çok Microsoft 365 grubuyla ilişkilendirilebilir mi?**

Hayır, Yammer grubu yalnızca tek bir Microsoft 365 grubuyla ilişkilendirilebilir. Gönderilerin diğer Yammer gruplarıyla paylaşılması veya bu gruplara taşınması mümkündür.

**bir Yammer grubunun bir Microsoft 365 grubuyla ilişkisi değişebilir mi?**

Hayır, Yammer grubu yalnızca ilk ilişkilendirildiği Microsoft 365 grubuyla ilişkilendirilebilir.

**Yammer grubu silindiğinde Microsoft 365 grubu silinir mi?**

Evet, Yammer'da grubu silmek ilgili Microsoft grubunu ve grupla ilişkili hizmetleri ve içeriği siler.

## <a name="related-topics"></a>İlgili konular

[İşbirliği idaresi planlama önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği idare planınızı oluşturma](collaboration-governance-first.md)
