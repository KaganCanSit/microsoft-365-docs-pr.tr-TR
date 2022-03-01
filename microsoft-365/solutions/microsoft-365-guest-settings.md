---
title: Microsoft 365 konuk paylaşımı ayarları başvurusu
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
f1.keywords: NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkTEAMS
ms.localizationpriority: high
recommendations: false
description: Kuruluş dışından kişilerle paylaşımı etkileyebilecek Microsoft 365 paylaşım ayarları hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: bf0a85f43733ac90d55dde9ded38efd273a9c485
ms.sourcegitcommit: d7cdbdda9b829c49caa3105eb47d3f26b88a5daf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2022
ms.locfileid: "63021583"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Microsoft 365 konuk paylaşımı ayarları başvurusu

Bu makalede, iş yükleri için kuruluş dışından kişilerle paylaşımı etkileyebilecek çeşitli ayarlara Microsoft 365: Teams, Microsoft 365 Grupları, SharePoint ve OneDrive. Bu ayarlar Azure Active Directory, Microsoft 365, Teams ve SharePoint yönetim merkezlerinde yer alır.

## <a name="azure-active-directory"></a>Azure Active Directory

**Yönetici rolü:** Genel yönetici

Azure Active Directory, dizin hizmetidir ve Microsoft 365. Kurumsal Azure Active Directory ayarları, gruplarda, Teams gruplarında, Microsoft 365 gruplarında ve SharePoint paylaşımı OneDrive.

> [!NOTE]
> Bu ayarlar yalnızca, SharePoint [Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) ile SharePoint ve OneDrive tümleştirmesi yapılandırıldığında yapılan ayarları etkiler. Aşağıdaki tabloda bunun yapılandırıldığından emin olduğu varsayıldı.

### <a name="external-collaboration-settings"></a>Dış işbirliği ayarları

**Gezinti:** [Azure Active Directory Merkezinde Dış](https://aad.portal.azure.com) kimlikler > Azure Active Directory > Dış > ayarlarına tıklayın

![Kurumsal İlişkiler Azure Active Directory sayfası Ayarlar ekran görüntüsü.](../media/azure-ad-organizational-relationships-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Konuk kullanıcı erişimi|Konuk kullanıcıların dizin nesnelerinin özelliklerine ve üyeliklerine erişimi sınırlıdır|Konukların çalışma [sayfalarında sahip olduğu izinleri Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions).|
|Konuk daveti ayarları|Kuruluşta herkes, konuk ve yönetici olmayan konuk kullanıcıları davet ediyor olabilir|Konukların, üyelerin ve yöneticilerin kuruluşa konuk davet edip etmeyeceklerini belirler. <p> Bu ayar, Microsoft 365 ve video paylaşım Teams deneyimi SharePoint.|
|Kullanıcı akışları aracılığıyla konuk self servis kaydolmasını etkinleştirme|Hayır|Birisinin sizin oluşturduğunuz bir uygulamaya kaydolmasına ve yeni bir konuk hesabı oluşturmasına olanak sağlayan kullanıcı akışları oluşturamıyorsanız bunu belirler.|
|İşbirliği kısıtlamaları|Davetlerin herhangi bir etki alanına gönderilmeye izin verme|Bu ayar paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak sağlar. İzin verilen etki alanları belirtilmişse paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtilirse, paylaşım davetleri bu etki alanlarına gönderilmez. <p> Bu ayar, Microsoft 365 ve video paylaşım Teams deneyimi SharePoint. Etki alanlarına daha ayrıntılı düzeyde izin vermek veya engellemek için etki alanı filtrelemesini SharePoint Teams.|

Bu ayarlar kullanıcıların dizine davet edilmelerini etkiler. Bu etki, zaten dizinde olan konuklarla paylaşımı etkilemez.

## <a name="microsoft-365"></a>Microsoft 365

**Yönetici rolü:** Genel yönetici

Grup Microsoft 365 yönetim merkezi paylaşmak ve grupları paylaşmak için kuruluş Microsoft 365 vardır.

### <a name="sharing"></a>Paylaşım

**Gezinti:** [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) >  **Ayarlar** >  **Org** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**ayarlarıGizlilik**</a> >  & **sekmesiSharing** > .

![Ekip sitesi güvenlik ve gizlilik konuk paylaşımı ayarının Microsoft 365 yönetim merkezi.](../media/sharepoint-security-privacy-sharing-setting.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Kullanıcıların kuruluşa yeni konuk eklemesine izin verme|On|Evet olarak **ayarlanırsa**, Azure AD üyeleri Azure AD aracılığıyla konukları davetlayabilir; hayır olarak **ayarlanırsa**, olamazlar. Evet **olarak ayarlanırsa**, Microsoft 365 Grubu üyeleri konukları sahip onayıyla davetlayabilir; Hayır olarak ayarlanırsa Microsoft 365 Grubu üyeleri sahip onayı olan konukları davetlayabilir, ancak sahiplerin onay için genel yönetici olması gerekir. <p> Üyeler davet **etme,** konuk yerine Azure AD'de bulunan üyelere başvurur ve davette yer alan site veya grup üyelerini Microsoft 365. <p> Bu, Kurumsal ilişkiler **ayarları içinde Üyeler davet** Azure Active Directory aynıdır.|

### <a name="microsoft-365-groups"></a>Microsoft 365 Grupları

**Gezinti:** [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) >  **Ayarlar** >  **Gizle ve Gruplar**> Microsoft 365 ayarları

![Grup Grup Microsoft 365 ayarlarının ekran Microsoft 365 yönetim merkezi.](../media/office-365-groups-guest-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Kuruluş dışındaki grup üyelerinin grup içeriğine erişmesine izin verme|On|Açık olarak ayar **konuklar** grup içeriğine erişebilirsiniz; bu ayar **Kapalı** olarak ayarlanırken hayır. Konukların grup **gruplarında veya** grup gruplarında etkileşim kurduğu tüm senaryolarda bu Microsoft 365 Açık Teams.|
|Grup sahiplerinin, kuruluş dışındaki kişilerin gruplara eklemesine izin verme|On|Açık **olduğunda**, Grup Microsoft 365 veya Teams gruplara yeni konuklar davet etmelerini sağlar. Kapalı **olduğunda**, bunu ifade etmeyer. Konukların gruplara **ekli** olduğu tüm senaryolarda bu ayar Açık olur.|

Bu ayarlar kuruluş düzeyindedir. [PowerShell kullanarak grup düzeyinde bu ayarları](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) değiştirme hakkında bilgi için bkz. Belirli bir grup için ayarlar oluşturma.

## <a name="teams"></a>Teams

Diğer Teams ayarlarının kullanılabilir olması için Ana konuk erişimine **izin ver** Teams ana konuk erişimine izin ver  anahtarının Açık olması gerekir.

**Yönetici rolü:** Teams yöneticisi

### <a name="guest-access"></a>Konuk erişimi

**Gezinti:** [Teams merkeziGökenden](https://admin.teams.microsoft.com) >  **ayarlarGizli** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**erişim**</a>

![Konuk erişimi Teams iki durumlu düğmenin ekran görüntüsü.](../media/teams-guest-access-toggle.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|E-postada konuk erişimine izin Teams|Kapalı|Konuk erişimini genel olarak erişim için Teams veya kapatın. Bu ayarın bir kez değiştirilene kadar yürürlüğe girecekleri 24 saat sürebilir.|

### <a name="guest-calling"></a>Konuk arama

**Gezinti:** [Teams merkeziGökenden](https://admin.teams.microsoft.com) >  **ayarlarGizli** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**erişim**</a>

![Konuk arama Teams ekran görüntüsü.](../media/teams-guest-calling-setting.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Özel arama yapma|On|Açık **olduğunda** konuklar Teams'da eşler arası aramalar **Teams Ise,** onu cevaplayabilir.|

### <a name="guest-meeting"></a>Konuk toplantısı

**Gezinti:** [Teams merkeziGökenden](https://admin.teams.microsoft.com) >  **ayarlarGizli** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**erişim**</a>

![Konuk toplantı Teams ekran görüntüsü.](../media/teams-guest-meeting-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|IP videosuna izin ver|On|Konuklar **Açık** olduğunda, aramalarında ve toplantılarında videoyu kullanabilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|Ekran paylaşım modu|Tüm ekran|Devre **Dışı** Bırak'a geldiğinde, konuklar bir gün içinde ekranlarını Teams. Tek uygulama **olarak ayar konuklar** ekranlarında yalnızca tek bir uygulamayı paylaşabilir. Tüm ekran **olarak ayar olduğunda**, konuklar bir uygulamayı veya tüm ekranlarını paylaşmayı seçebilir.|
|Şimdi Karşılamaya İzin Ver|On|Konuklar **Açık** olduğunda, Teams'te Şimdi Meet özelliğini kullanabilir; **Kapalı** olduğunda ise bunu göremz.|

### <a name="guest-messaging"></a>Konuk mesajlaşması

**Gezinti:** [Teams merkeziGökenden](https://admin.teams.microsoft.com) >  **ayarlarGizli** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**erişim**</a>

![Konuk ileti Teams ekran görüntüsü.](../media/teams-guest-messaging-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Gönderilen iletileri düzenleme|On|Açık **olduğunda** konuklar daha önce gönderdiği iletileri düzenleyebilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|Gönderilen iletileri silme|On|Açık **olduğunda**, konuklar daha önce gönderdiği iletileri silebilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|Sohbet|On|Açık **olduğunda** konuklar Teams'te **sohbeti kullanabilir; Kapalı** olduğunda ise sohbeti kullanamz.|
|Görüşmelerde Giphy kullanma|On|Açık **olduğunda**, konuklar görüşmelerde Giphy'leri kullanabilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|Giphy içerik derecelendirmesi|Orta|Tüm içeriğe **izin ver olarak ayarlanırsa**, konuklar içerik derecelendirmesine bakılmaksızın sohbetlere tüm Giphy'leri ekler. Orta konuklar **sohbetlere** Giphy eklediği zaman, ancak yetişkin içeriğine göre orta derecede kısıtlanır. Katı konuklar **sohbetlere** Giphy'ler eklensin, ancak yetişkin içeriği eklemesi kısıtlanır.|
|Görüşmelerde Mem kullanma|On|Konuklar **Konuşmalarda** Mem'leri Açık olarak kullanabilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|Konuşmalarda kullanıcı çıkartmaları|On|Açık **olduğunda** konuklar görüşmelerde çıkartmaları kullanabilir; Kapalı **olduğunda**, bunu onlar da göremz.|
|İletileri görüntülemek için tam ekran okuyucuya izin verme|On|Açık **olduğunda** konuklar e-posta Tam Ekran Okuyucu **, Kapalı** olduğunda ise görüntüden atlayabilir.|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint ve OneDrive (kuruluş düzeyi)

**Yönetici rolü:** SharePoint yönetici

Bu ayarlar, kuruluşta tüm siteleri etkiler. Bunlar doğrudan grup Microsoft 365 grupları veya Teams etkilemez, ancak kullanıcı deneyimi sorunlarından kaçınmak için bu ayarları Microsoft 365 Grupları ve Grupları ayarlarıyla Teams öneririz. (Örneğin, Teams'te konuk paylaşımına izin verilmiyorsa ancak SharePoint'te konuk Teams'ta konuk erişimi olmaz, çünkü Teams dosyaları SharePoint.)

### <a name="sharepoint-and-onedrive-sharing-settings"></a>SharePoint ve OneDrive ayarlarını değiştirme

OneDrive sitelerin hiyerarşisi bir SharePoint olduğundan, kuruluş düzeyindeki paylaşım ayarları aynı diğer sitelerde olduğu gibi OneDrive siteleri de SharePoint etkiler.

**Gezinti:** SharePoint merkezi > Paylaşımı

![Kuruluş düzeyi SharePoint ayarlarının ekran görüntüsü.](../media/external-sharing.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|SharePoint|Herkes|Siteler için izin verilen en izinli paylaşım SharePoint belirtir.|
|OneDrive|Herkes|Belirli siteler için izin verilen en izinli OneDrive belirtir. Bu ayar, izin verilen ayardan SharePoint olamaz.|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>SharePoint paylaşım OneDrive ayarlarına tıklayın ve tıklayın

**Gezinti:** SharePoint merkezi > Paylaşımı

![Kuruluş düzeyi SharePoint paylaşım ayarlarının ekran görüntüsü.](../media/external-sharing.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Dış paylaşımı etki alanına göre sınırlama|Kapalı|Bu ayar paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak sağlar. İzin verilen etki alanları belirtilmişse paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtilirse, paylaşım davetleri bu etki alanlarına gönderilmez. <p> Bu ayar, kuruluş SharePoint tüm OneDrive sitelerini etkiler.|
|Yalnızca belirli güvenlik gruplarında yer alan kullanıcıların dışarıdan paylaşımda  olmasına izin verme|Kapalı|SharePoint ve OneDrive'da kimlerin konuklarla paylaşım yapanı sınırlamak OneDrive, paylaşımı belirtilen güvenlik gruplarında yer alan kişiler ile sınırlayabilir. Bu ayarlar gruplarda veya gruplarda Microsoft 365 paylaşımı Teams. Belge ve klasör paylaşımı yalnızca belirtilen güvenlik gruplarında yer alan kişiler tarafından yapasa da, grup veya ekip aracılığıyla davet edilen konuklar da ilişkili siteye erişim sahibi olabilir. <p> Belirtilen her grup için, bu kullanıcılardan hangisinin Herkes bağlantılarıyla paylaşa birini seçebilirsiniz.|
|Konukların paylaşım davetleri gönderilirken aynı hesabı kullanarak oturum açması gerekir|Kapalı|Konukların davet gönderildiği adresten farklı bir e-posta adresi kullanarak site paylaşım davetlerini kullanmalarını engellemektedir. <p> [SharePoint ve OneDrive Azure AD B2B (Önizleme)](/sharepoint/sharepoint-azureb2b-integration-preview) ile tümleştirme bu ayarı kullanmaz, çünkü tüm konuklar davetin gönderildiği e-posta adresine bağlı olarak dizine eklenir. Siteye erişmek için alternatif e-posta adresleri kullanılamaz.|
|Konukların sahip olmadığını öğeleri paylaşmasına izin verme|On|Açık **olduğunda**, konuklar sahip olmadığınız öğeleri diğer kullanıcılarla veya konuklarla paylaşabilir; Kapalı **olduğunda** , bu iki tinlik (Kapalı) olarak kabul kullanılamaz. Konuklar her zaman tam denetimine sahip olduğu öğeleri paylaşabilir.|
|Doğrulama kodu kullanan kişilerin, birkaç gün sonra yeniden doğrulaması gerekiyor|Kapalı|Bu ayar, belirli sayıda gün sonra tek seferlik geçiş kodu ile kimlik doğrulaması kullanan kullanıcıların yeniden kimlik doğrulaması gerektirmeyi sağlar.|
|Bir siteye veya postaya konuk OneDrive, süresi bu kadar gün sonra otomatik olarak dolmaz|On|Yöneticiniz konuk erişimi için bir süre sonu ayarladısa, siteye davet etmiş veya tek tek dosyaları ve klasörleri kendileriyle paylaştığınız her konuk belirli sayıda gün boyunca erişime sahip olur. Daha fazla bilgi için, [Site için konuk süre sonu yönetme](https://support.microsoft.com/en-us/office/manage-guest-expiration-for-a-site-25bee24f-42ad-4ee8-8402-4186eed74dea)

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>SharePoint ve OneDrive bağlantısı ayarlarını değiştirme ve değiştirme

Dosya ve klasörler SharePoint ve OneDrive'de paylaşılırken, alıcılara dosya veya klasörün kendi kendilerine doğrudan erişim vermek yerine, dosya veya klasör üzerinde izinleri olan bir bağlantı gönderilir. Çeşitli türlerde bağlantılar vardır ve kullanıcılara sunulan dosya veya klasörü paylaştıklarına varsayılan bağlantı türünü seçebilirsiniz. Herkes bağlantıları için izinleri ve süre sonu *seçeneklerini de kullanabilirsiniz* .

**Gezinti:** SharePoint merkezi > Paylaşımı

![Kuruluş düzeyi SharePoint klasörleri paylaşma ayarlarının ekran görüntüsü.](../media/sharepoint-organization-files-folders-sharing-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Dosya ve klasör bağlantıları|Bağlantıya sahip herkes|Kullanıcı bir dosya veya klasörü paylaştığında, varsayılan olarak hangi paylaşım bağlantısının gösterl olduğunu belirtir. Kullanıcılar isterse paylaşmadan önce seçeneği değiştirebilirler. Varsayılan olarak Bağlantısı olan herkes ve  Bir site için Herkes paylaşımına izin verilmiyor olarak ayarlanırsa, bu sitenin  varsayılan ayarı Yalnızca sizinki olan kişiler gösterilir.|
|Bu bağlantıların süresi bu kadar gün içinde dolacak|Kapalı (son kullanma tarihi yok)|Herkes bağlantısı oluşturulduktan ve *bu bağlantının süresinin* dolması sonrasındaki gün sayısını belirtir. Süresi dolmuş bağlantılar yenilenmez. Sona erme tarihi geçen paylaşıma devam etmek için yeni bağlantı oluşturun.|
|Dosya izinleri|Görüntüleme ve düzenleme|Herkes bağlantısı oluştururken kullanıcıların dosya izin *düzeylerini belirtir.* Görünüm **seçiliyse** , kullanıcılar yalnızca görüntüleme izinleri olan *herkes* dosya bağlantıları oluşturabilir. Görüntüle **ve düzenle seçiliyse** , kullanıcılar bağlantıyı oluşturdukları zaman görüntüleme ve görüntüleme ve düzenleme izinleri arasında seçim oluşturabilir.|
|Klasör izinleri|Görüntüleme, düzenleme ve karşıya yükleme|Herkes bağlantısı oluştururken kullanıcıların klasör izin *düzeylerini belirtir.* Görünüm **seçiliyse** , kullanıcılar yalnızca görüntüleme izinlerine *sahip herkes* klasörü bağlantıları oluşturabilir. Görüntüle **, düzenle ve karşıya yükle** seçiliyse, kullanıcılar bağlantıyı yenilerken görüntüleme ve görüntüleme, düzenleme ve karşıya yükleme izinleri arasında seçim de seçebilir.|

## <a name="sharepoint-site-level"></a>SharePoint (site düzeyi)

**Yönetici rolü:** SharePoint yönetici

Bu ayarlar tüm site için kuruluş genelinde geçerli SharePoint olduğundan, kuruluş düzeyi ayarı değişirse sitenin etkili paylaşım ayarı değişebilir. Burada bir ayar seçerseniz ve kuruluş düzeyi daha sonra daha kısıtlayıcı bir değere ayarlanırsa, bu site daha kısıtlayıcı bir değerle çalışır. Örneğin, Herkes'i seçerseniz  ve kuruluş düzeyi ayarı daha sonra Yeni ve var olan konuklar olarak ayarlanırsa **, bu** site yalnızca yeni ve mevcut konuklara izin verecek. Kuruluş düzeyi ayarı Herkes olarak ayarlanmışsa bu site **yine** Herkes bağlantılarına *izin* verecek.

### <a name="site-sharing"></a>Site paylaşımı

Aynı dosyada yer alan her site için konuk paylaşım SharePoint. Bu ayar hem site paylaşımı hem de dosya ve klasör paylaşımı için geçerlidir. (*Herkes* paylaşımı site paylaşımı için kullanılamaz. **Herkes'i seçerseniz**, kullanıcılar Herkes bağlantılarını ve yeni ve mevcut konuklarla sitenin kendisini  kullanarak dosya ve klasör paylaşabilir.)

Sitenin duyarlılık etiketi uygulanmışsa, bu etiket dış paylaşım ayarlarını denetimine sahip olabilir. Daha fazla bilgi için bkz. Site site sitelerine, [gruplara ve sitelere Microsoft Teams Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

**Gezinti:** SharePoint siteleri > için Yönetim Merkezi'> Dış paylaşımı > İlkeler > siteyi seçin

![Site dış SharePoint ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Site içeriği ile paylaşabilirsiniz|Site türüne göre değişir (aşağıdaki tabloya bakın)|Bu site için izin verilen dış paylaşım türünü gösterir. Burada kullanılabilen seçenekler, ilgili kuruluş düzeyinde paylaşım ayarlarına SharePoint.|

### <a name="site-file-and-folder-link-settings"></a>Site dosyası ve klasör bağlantısı ayarları

Bağlantı türü ve izinleri için varsayılan ayarları ve her site için Herkes bağlantıları *için süre sonu* ayarlarını kullanabilirsiniz. Site düzeyinde ayar olduğunda, bu ayarlar kuruluş düzeyi ayarlarını geçersiz kılar. Herkes bağlantıları *kuruluş* düzeyinde devre dışı bırakılırsa *, Herkes* site düzeyinde kullanılabilir bir bağlantı türü olmayacaktır.

**Gezinti:** SharePoint siteleri > için Yönetim Merkezi'> Dış paylaşımı > İlkeler > siteyi seçin

![Site SharePoint bağlantı paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-site-link-sharing-settings.png)

| Ayar | Default | Açıklama |
|:-----|:-----|:-----|
|Etki alanına göre paylaşımı sınırlama|Kapalı|Bu ayar paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak sağlar. İzin verilen etki alanları belirtilmişse paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtilirse, paylaşım davetleri bu etki alanlarına gönderilmez. <p> Bu ayar, kuruluş veya Azure AD düzeyinde ayarlanmış etki alanı kısıtlamalarını geçersiz kılmak için kullanılamaz.|
|Varsayılan paylaşım bağlantı türü|Kuruluş düzeyi ayarıyla aynı|Bu ayar, bu site içinde kullanıcılara sunulan varsayılan paylaşım bağlantısını belirtmenize olanak sağlar. Kuruluş *düzeyi ayarıyla aynı seçenek* , kuruluş ve site paylaşımı ayarlarının bir birleşimiyle tanımlanır.|
|Herkes bağlantıları için gelişmiş ayarlar|Kuruluş düzeyi ayarıyla aynı|Bu sitede bir dosya için Süresi *dolan Herkes* bağlantısı oluşturulduktan sonra geçerli olan gün sayısını belirtir. Süresi dolmuş bağlantılar yenilenmez. Sona erme tarihi geçen paylaşıma devam etmek için yeni bağlantı oluşturun.|
|Varsayılan bağlantı izni|Kuruluş düzeyi ayarıyla aynı|Bu ayar, bu sitede dosyalar için oluşturulan bağlantı paylaşımı için varsayılan izni (Görüntüleme veya Düzenleme) belirtmenize olanak sağlar.|

### <a name="default-site-sharing-settings"></a>Varsayılan site paylaşım ayarları

Aşağıdaki tabloda her site türü için varsayılan paylaşım ayarı gösterilmiştir.

| Site türü | Varsayılan paylaşım ayarı |
|:-----|:-----|
|Klasik|**Yalnızca kuruluşta yer alan kişiler**|
|OneDrive|**Herkes**|
|Grup bağlantılı siteler (site Teams)|**Grup Grupları ayarı Grup sahiplerinin** kuruluş Microsoft 365 kişi eklemesine izin  ver ayarı Açık ise yeni ve mevcut konuklar **Açık** durumdadır; aksi takdirde Yalnızca mevcut **konuklar**|
|İletişim|**Yalnızca kuruluşta yer alan kişiler**|
|Grup (Ekip Sitesi yok) #STS3 modern siteler|**Yalnızca kuruluşta yer alan kişiler**|

> [!NOTE]
> Kök iletişim sitesinde (tenant-name.sharepoint.com) Herkes varsayılan paylaşım ayarı **vardır**.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint ve dış OneDrive paylaşımına genel bakış](/sharepoint/external-sharing-overview)

[Web'de konuk Microsoft Teams](/MicrosoftTeams/guest-access)

[Gruplara konuk Microsoft 365 ekleme](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
