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
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Microsoft 365'da bulunan ve kuruluşunuz dışındaki kişilerle paylaşımı etkileyebilecek konuk paylaşım ayarları hakkında bilgi edinin.
ms.openlocfilehash: 4c472fb20a85c0f00f7623cc63c4d33556b511e2
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687264"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Microsoft 365 konuk paylaşımı ayarları başvurusu

Bu makalede, Microsoft 365 iş yükleri için kuruluşunuzun dışındaki kişilerle paylaşımı etkileyebilecek çeşitli ayarlar için başvuru sağlanır: Teams, Microsoft 365 Grupları, SharePoint ve OneDrive. Bu ayarlar Azure Active Directory, Microsoft 365, Teams ve SharePoint yönetim merkezlerinde yer alır.

## <a name="azure-active-directory"></a>Azure Active Directory

**Yönetici rolü:** Genel yönetici

Azure Active Directory, Microsoft 365 tarafından kullanılan dizin hizmetidir. Azure Active Directory Kuruluş ilişkileri ayarları Teams, Microsoft 365 Grupları, SharePoint ve OneDrive paylaşımı doğrudan etkiler.

> [!NOTE]
> Bu ayarlar yalnızca [Azure AD B2B ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview) yapılandırıldığında SharePoint etkiler. Aşağıdaki tabloda bunun yapılandırıldığı varsayılmaktadır.

### <a name="external-collaboration-settings"></a>Dış işbirliği ayarları

**Gezinti:** [Dış Kimlikler >](https://aad.portal.azure.com) Dış işbirliği ayarları > Azure Active Directory > yönetim merkezi Azure Active Directory

![Azure Active Directory Kuruluş İlişkileri Ayarlar sayfasının ekran görüntüsü.](../media/azure-ad-organizational-relationships-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Konuk kullanıcı erişimi|Konuk kullanıcıların dizin nesnelerinin özelliklerine ve üyeliklerine sınırlı erişimi vardır|[Konukların Azure Active Directory izinlerini](/azure/active-directory/fundamentals/users-default-permissions) belirler.|
|Konuk daveti ayarları|Kuruluştaki herkes konuklar ve yönetici olmayanlar da dahil olmak üzere konuk kullanıcıları davet edebilir|Konukların, üyelerin ve yöneticilerin kuruluşa konuk davet edip edemeyeceğini belirler. <p> Bu ayar, Teams ve SharePoint gibi Microsoft 365 paylaşım deneyimlerini etkiler.|
|Kullanıcı akışları aracılığıyla konuk self servis kaydolmayı etkinleştirme|Hayır|Birinin oluşturduğunuz bir uygulamaya kaydolmasına ve yeni bir konuk hesabı oluşturmasına izin veren kullanıcı akışları oluşturup oluşturamadığını belirler.|
|İşbirliği kısıtlamaları|Davetlerin herhangi bir etki alanına gönderilmesine izin ver|Bu ayar, paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak tanır. İzin verilen etki alanları belirtildiğinde, paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtildiğinde, paylaşım davetleri bu etki alanlarına gönderilemez. <p> Bu ayar, Teams ve SharePoint gibi Microsoft 365 paylaşım deneyimlerini etkiler. etki alanı filtrelemesini SharePoint veya Teams kullanarak etki alanlarına daha ayrıntılı bir düzeyde izin verebilir veya bunları engelleyebilirsiniz.|

Bu ayarlar, kullanıcıların dizine davet etme şeklini etkiler. Bunlar, zaten dizinde olan konuklarla paylaşımı etkilemez.

### <a name="cross-tenant-access-settings"></a>Kiracılar arası erişim ayarları

**Gezinti:** [Azure Active Directory yönetim merkezi](https://aad.portal.azure.com) > Azure Active Directory > Dış Kimlikler > Kiracılar arası erişim ayarları > Varsayılan ayarlar sekmesi

Varsayılan ayarlar, kuruluşa özgü ayarları olanlar dışında tüm dış Azure AD kuruluşları için geçerlidir. Belirli bir kuruluş için Ayarlar **Kuruluş ayarları** sekmesinde yapılandırılabilir. Konuklar (B2B işbirliği) ve [Azure AD B2B doğrudan bağlantı](/azure/active-directory/external-identities/b2b-direct-connect-overview) kullanıcıları için ayrı ayarlar vardır.

![Azure Active Directory Kiracılar arası erişim ayarları sayfasının ekran görüntüsü.](../media/azure-ad-cross-tenant-default-settings.png)

**Gelen erişim ayarları**

Gelen erişim ayarları, dış Azure AD kuruluşlarından kullanıcıların kuruluşunuzdaki kaynaklara erişip erişemeyeceğini denetler.

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|B2B işbirliği - dış kullanıcılar ve gruplar|Tümüne İzin Verildi|Diğer Azure AD kuruluşlarındaki kişilere kuruluşunuzdaki kaynaklara konuk olarak erişim izni verileceğini belirler.|
|B2B işbirliği - uygulamalar|Tümüne izin verilir|Kuruluşunuzdaki konuklara erişim izni verilebilen uygulamaları belirler.|
|B2B doğrudan bağlantı - dış kullanıcılar ve gruplar|Tümü engellendi|Diğer Azure AD kuruluşlarındaki kişilere B2B doğrudan bağlantı aracılığıyla kuruluşunuzdaki kaynaklara erişim izni verilip verilebileceğini belirler.|
|B2B doğrudan bağlantı - uygulamalar|Tümü engellendi|Kuruluşunuzdaki B2B doğrudan bağlantı kullanıcılarına hangi uygulamalara erişim verilebileceğini belirler.|
|Güven ayarları|Devre dışı|Koşullu erişim ilkelerinizin, bu kuruluşlardan kişiler kaynaklarınıza eriştiğinde diğer Azure AD kuruluşlarından gelen talepleri kabullenip kabul etmeyeceklerini belirler.|

**Giden erişim ayarları**

Giden erişim ayarları, kullanıcılarınızın dış kuruluştaki kaynaklara erişip erişemeyeceğini denetler.

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|B2B işbirliği - dış kullanıcılar ve gruplar|Tümüne İzin Verildi|Kuruluşunuzdaki hangi kullanıcılara diğer Azure AD kuruluşlarındaki kaynaklara konuk olarak erişim verilebileceğini belirler.|
|B2B işbirliği - uygulamalar|Tümüne izin verilir|Diğer Azure AD kuruluşlarında kullanıcılarınızın konuk olarak hangi uygulamalara erişim verebileceğini belirler.|
|B2B doğrudan bağlantı - dış kullanıcılar ve gruplar|Tümü engellendi|Kuruluşunuzdaki hangi kullanıcılara B2B doğrudan bağlantı aracılığıyla diğer Azure AD kuruluşlarındaki kaynaklara erişim verilebileceğini belirler.|
|B2B doğrudan bağlantı - uygulamalar|Tümü engellendi|Kullanıcılarınızın B2B doğrudan bağlantı aracılığıyla diğer Azure AD kuruluşlarında hangi uygulamalara erişim verileceğini belirler.|

## <a name="microsoft-365"></a>Microsoft 365

**Yönetici rolü:** Genel yönetici

Microsoft 365 yönetim merkezi, paylaşım ve Microsoft 365 Grupları için kuruluş düzeyinde ayarlara sahiptir.

### <a name="sharing"></a>Paylaşım

**Gezinti:** [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) >  **Ayarlar** >  **Org** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**ayarlarıGüvenlik**</a> >  & gizlilik **sekmesiHatalama** > .

![Microsoft 365 yönetim merkezi güvenlik ve gizlilik konuk paylaşımı ayarının ekran görüntüsü.](../media/sharepoint-security-privacy-sharing-setting.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Kullanıcıların kuruluşa yeni konuklar eklemesine izin verme|-Inı|**Evet** olarak ayarlandığında, Azure AD üyeleri Azure AD aracılığıyla konuk davet edebilir; **Hayır** olarak ayarlandığında yapamazlar. **Evet** olarak ayarlandığında, Microsoft 365 grup üyeleri konukları sahip onayıyla davet edebilir; **Hayır** olarak ayarlandığında, Microsoft 365 grup üyeleri sahip onayı olan konukları davet edebilir, ancak sahiplerin onaylaması için genel yönetici olması gerekir. <p> **Üyeler davet edebilir** seçeneğinin Azure AD'deki üyeleri (konuklardan farklı olarak) ifade ettiğini ve Microsoft 365'da site veya grup üyelerini ifade etmediğini unutmayın. <p> Bu, Azure Active Directory Kuruluş ilişkileri ayarlarındaki **Üyeler davet edebilir** ayarıyla aynıdır.|

### <a name="microsoft-365-groups"></a>Microsoft 365 Grupları

**Gezinti:** [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) >  **Ayarlar** >  **Org ayarları** > Microsoft 365 Grupları

![Microsoft 365 yönetim merkezi Microsoft 365 Grupları konuk ayarlarının ekran görüntüsü.](../media/office-365-groups-guest-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Kuruluşunuzun dışındaki grup üyelerinin grup içeriğine erişmesine izin verme|-Inı|**Açık** olarak ayarlandığında, konuklar grup içeriğine erişebilir; **Kapalı** olarak ayarlandığında, bunu yapamazlar. Konukların Microsoft 365 Grupları veya Teams ile etkileşime geçtiği tüm senaryolarda bu ayar **Açık** olmalıdır.|
|Grup sahiplerinin kuruluşunuz dışındaki kişileri gruplara eklemesine izin verme|-Inı|**Açık olduğunda**, Microsoft 365 Grupları veya Teams sahipleri gruba yeni konuklar davet edebilir. **Kapalıyken**, yapamazlar. Konukların gruplara eklendiği tüm senaryolarda bu ayar **Açık** olmalıdır.|

Bu ayarlar kuruluş düzeyindedir. PowerShell kullanarak bu ayarları grup düzeyinde değiştirme hakkında bilgi için bkz. [Belirli bir grup için ayarlar oluşturma](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) .

## <a name="teams"></a>Teams

Diğer konuk ayarlarının kullanılabilmesi için **Teams'da konuk erişimine izin ver Teams** ana konuk erişimi anahtarı **Açık** olmalıdır.

**Yönetici rolü:** hizmet yöneticisi Teams

### <a name="guest-access"></a>Konuk erişimi

**Gezinti:** [Teams yönetim merkeziG](https://admin.teams.microsoft.com) >  **genelinde** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**ayarlarGerekli**</a> >  erişim

![Teams konuk erişimi iki durumlu düğmesinin ekran görüntüsü.](../media/teams-guest-access-toggle.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Teams'da konuk erişimine izin ver|-Inı|Teams için konuk erişimini açar veya kapatır. Bu ayarın değiştirilmesi 24 saat sürebilir.|

### <a name="guest-calling"></a>Konuk arama

**Gezinti:** [Teams yönetim merkeziG](https://admin.teams.microsoft.com) >  **genelinde** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**ayarlarGerekli**</a> >  erişim

![Teams konuk arama seçeneklerinin ekran görüntüsü.](../media/teams-guest-calling-setting.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Özel aramalar yapma|-Inı|**Açık olduğunda**, konuklar Teams'da eşler arası aramalar yapabilir; **Kapalı** olduğunda bunu yapamazlar.|

### <a name="guest-meeting"></a>Konuk toplantısı

**Gezinti:** [Teams yönetim merkeziG](https://admin.teams.microsoft.com) >  **genelinde** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**ayarlarGerekli**</a> >  erişim

![Teams konuk toplantısı ayarlarının ekran görüntüsü.](../media/teams-guest-meeting-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|IP videosuna izin ver|-Inı|**Açık olduğunda**, konuklar aramalarında ve toplantılarında video kullanabilir; **Kapalı** olduğunda, yapamazlar.|
|Ekran paylaşım modu|Tüm ekran|**Devre Dışı bırakıldığında**, konuklar Teams ekranlarını paylaşamaz. **Tek uygulama** olarak ayarlandığında, konuklar ekranlarında yalnızca tek bir uygulamayı paylaşabilir. **Tüm ekran** olarak ayarlandığında, konuklar bir uygulamayı veya tüm ekranlarını paylaşmayı seçebilir.|
|Şimdi Buluşmaya İzin Ver|-Inı|**Açık olduğunda**, konuklar Teams'daki Şimdi Toplantı Yap özelliğini kullanabilir; **Kapalı** olduğunda kullanamazlar.|

### <a name="guest-messaging"></a>Konuk mesajlaşması

**Gezinti:** [Teams yönetim merkeziG](https://admin.teams.microsoft.com) >  **genelinde** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**ayarlarGerekli**</a> >  erişim

![Teams konuk mesajlaşma ayarlarının ekran görüntüsü.](../media/teams-guest-messaging-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Gönderilen iletileri düzenleme|-Inı|**Açık olduğunda**, konuklar daha önce gönderdikleri iletileri düzenleyebilir; **Kapalı** olduğunda, yapamazlar.|
|Gönderilen iletileri silme|-Inı|**Açık olduğunda**, konuklar daha önce gönderdikleri iletileri silebilir; **Kapalı** olduğunda, yapamazlar.|
|Sohbet|-Inı|**Açık olduğunda**, konuklar Teams sohbeti kullanabilir; **Kapalı** olduğunda kullanamazlar.|
|Konuşmalarda Giphys kullanma|-Inı|**Açık olduğunda**, konuklar konuşmalarda Giphys'i kullanabilir; **Kapalı** olduğunda, yapamazlar.|
|Giphy içerik derecelendirmesi|Orta|**Tüm içeriğe izin ver** olarak ayarlandığında, konuklar içerik derecelendirmesine bakılmaksızın tüm Giphy'leri sohbetlere ekleyebilir. **Orta** düzey olarak ayarlandığında konuklar sohbetlere Giphys ekleyebilir, ancak yetişkinlere yönelik içerikle sınırlı olacaktır. **Katı** konuklar sohbetlere Giphys ekleyebilir, ancak yetişkinlere yönelik içerik eklemeleri kısıtlanır.|
|Konuşmalarda Mem'leri kullanma|-Inı|**Açık olduğunda**, konuklar konuşmalarda memleri kullanabilir; **Kapalı** olduğunda, yapamazlar.|
|Konuşmalardaki kullanıcı çıkartmaları|-Inı|**Açık olduğunda**, konuklar konuşmalarda çıkartmaları kullanabilir; **Kapalı** olduğunda, yapamazlar.|
|İletileri görüntülemek için tam ekran okuyucuya izin ver|-Inı|**Açık olduğunda**, konuklar iletileri Tam Ekran Okuyucu'da görüntüleyebilir; **Kapalı** olduğunda görüntüleyemezler.|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint ve OneDrive (kuruluş düzeyinde)

**Yönetici rolü:** yönetici SharePoint

Bu ayarlar kuruluştaki tüm siteleri etkiler. Bunlar Microsoft 365 Grupları veya Teams doğrudan etkilemez, ancak kullanıcı deneyimi sorunlarını önlemek için bu ayarları Microsoft 365 Grupları ve Teams ayarlarıyla hizalamanızı öneririz. (Örneğin, konuk paylaşımına Teams izin veriliyorsa ancak SharePoint izin verilmiyorsa, Teams dosyalar SharePoint depolandığından Teams'deki konuklar Dosyalar sekmesine erişemeyebilir.)

### <a name="sharepoint-and-onedrive-sharing-settings"></a>paylaşım ayarlarını SharePoint ve OneDrive

OneDrive SharePoint içindeki sitelerin hiyerarşisi olduğundan, kuruluş düzeyinde paylaşım ayarları OneDrive diğer SharePoint siteleri gibi doğrudan etkiler.

**Gezinti:** SharePoint yönetim merkezi > **İlkeleri** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Paylaşma**</a>

![Kuruluş düzeyinde paylaşım ayarlarını SharePoint ekran görüntüsü.](../media/external-sharing.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|SharePoint|Kimse|SharePoint siteleri için izin verilen en izin verilen paylaşım izinlerini belirtir.|
|OneDrive|Kimse|OneDrive siteler için izin verilen en izin verilen paylaşım izinlerini belirtir. Bu ayar, SharePoint ayarından daha izin veremez.|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>Gelişmiş paylaşım ayarlarını SharePoint ve OneDrive

**Gezinti:** SharePoint yönetim merkezi > **İlkeleri** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Paylaşma**</a>

![Kuruluş düzeyinde SharePoint ek paylaşım ayarlarının ekran görüntüsü.](../media/external-sharing.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Dış paylaşımı etki alanına göre sınırlama|Kapalı|Bu ayar, paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak tanır. İzin verilen etki alanları belirtildiğinde, paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtildiğinde, paylaşım davetleri bu etki alanlarına gönderilemez. <p> Bu ayar, kuruluştaki tüm SharePoint ve OneDrive sitelerini etkiler.|
|Yalnızca belirli güvenlik gruplarındaki kullanıcıların harici olarak paylaşmasına izin ver|Kapalı|SharePoint ve OneDrive'da konuklarla kimlerin paylaşabileceğini sınırlamak istiyorsanız, paylaşımı belirtilen güvenlik gruplarındaki kişilerle sınırlayarak bunu yapabilirsiniz. Bu ayarlar Microsoft 365 Grupları veya Teams aracılığıyla paylaşımı etkilemez. Bir grup veya ekip aracılığıyla davet edilen konuklar da ilişkili siteye erişebilir, ancak belge ve klasör paylaşımı yalnızca belirtilen güvenlik gruplarındaki kişiler tarafından yapılabilir. <p> Belirtilen her grup için, bu kullanıcılardan hangilerinin Herkes bağlantılarıyla paylaşabileceğini seçebilirsiniz.|
|Konuklar, paylaşım davetlerinin gönderildiği hesabı kullanarak oturum açmalıdır|Kapalı|Konukların, davetin gönderildiğinden farklı bir e-posta adresi kullanarak site paylaşım davetlerini kullanmasını engeller. <p> Tüm konuklar davetin gönderildiği e-posta adresine göre dizine eklendiğinden [Azure AD B2B (Önizleme) ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview) bu ayarı kullanmaz. Siteye erişmek için alternatif e-posta adresleri kullanılamaz.|
|Konukların sahip olmadığı öğeleri paylaşmasına izin ver|-Inı|**Açık olduğunda**, konuklar sahip olmadığı öğeleri diğer kullanıcılarla veya konuklarla paylaşabilir; **Kapalıyken** yapamazlar. Konuklar her zaman tam denetime sahip oldukları ürünleri paylaşabilirler.|
|Doğrulama kodu kullanan kişilerin bu kadar gün sonra yeniden kimlik doğrulaması yapması gerekir|Kapalı|Bu ayar, tek seferlik geçiş koduyla kimlik doğrulayan kullanıcıların belirli sayıda gün sonra yeniden kimlik doğrulaması yapmasını zorunlu kılmanızı sağlar.|
|Bir siteye veya OneDrive konuk erişiminin süresi bu kadar gün sonra otomatik olarak dolacak|-Inı|Yöneticiniz konuk erişimi için bir süre sonu süresi ayarladıysa, siteye davet ettiğiniz veya tek tek dosya ve klasörleri paylaştığınız her konuk için belirli sayıda gün boyunca erişim verilir. Daha fazla bilgi [için, Bir site için konuk süre sonunu yönetme](https://support.microsoft.com/en-us/office/manage-guest-expiration-for-a-site-25bee24f-42ad-4ee8-8402-4186eed74dea) sayfasını ziyaret edin

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>dosya ve klasör bağlantısı ayarlarını SharePoint ve OneDrive

Dosya ve klasörler SharePoint ve OneDrive paylaşıldığında, paylaşım alıcılarına dosya veya klasöre doğrudan erişim vermek yerine dosya veya klasör izinleri olan bir bağlantı gönderilir. Çeşitli bağlantı türleri kullanılabilir ve kullanıcılara dosya veya klasör paylaştıklarında sunulan varsayılan bağlantı türünü seçebilirsiniz. *Ayrıca Herkes* bağlantıları için izinleri ve süre sonu seçeneklerini de ayarlayabilirsiniz.

**Gezinti:** SharePoint yönetim merkezi > **İlkeleri** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Paylaşma**</a>

![Kuruluş düzeyinde dosya ve klasör paylaşımı ayarlarını SharePoint ekran görüntüsü.](../media/sharepoint-organization-files-folders-sharing-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Dosya ve klasör bağlantıları|Bağlantıya sahip herkes|Kullanıcı bir dosya veya klasör paylaştığında varsayılan olarak hangi paylaşım bağlantısının gösterileceğini belirtir. Kullanıcılar isterse paylaşmadan önce seçeneği değiştirebilir. Varsayılan değer **Bağlantıya sahip herkes** olarak ayarlanırsa ve Belirli bir site için *Herhangi* bir paylaşıma izin verilmiyorsa, yalnızca **kuruluşunuzdaki kişiler** bu site için varsayılan olarak gösterilir.|
|Bu bağlantıların süresi bu kadar gün içinde dolmalıdır|Kapalı (süre sonu yok)|*Bir Herkes* bağlantısı oluşturulduktan sonra süresinin dolmasına neden olan gün sayısını belirtir. Süresi dolan bağlantılar yenilenemez. Süre sonunu geçtikten sonra paylaşmaya devam etmeniz gerekiyorsa yeni bir bağlantı oluşturun.|
|Dosya izinleri|Görüntüleme ve düzenleme|*Herkes* bağlantısı oluştururken kullanıcıların kullanabileceği dosya izin düzeylerini belirtir. **Görünüm** seçiliyse, kullanıcılar yalnızca görüntüleme izinlerine sahip *Herkes* dosya bağlantıları oluşturabilir. **Görünüm ve düzenleme** seçiliyse, kullanıcılar bağlantıyı oluştururken görüntüleme ve görüntüleme ve düzenleme izinleri arasında seçim yapabilir.|
|Klasör izinleri|Görüntüleme, düzenleme ve karşıya yükleme|*Herkes* bağlantısı oluştururken kullanıcıların kullanabileceği klasör izin düzeylerini belirtir. **Görünüm** seçiliyse, kullanıcılar yalnızca görüntüleme izinlerine sahip *Herkes* klasör bağlantıları oluşturabilir. **Görüntüle, düzenle ve karşıya yükle** seçiliyse, kullanıcılar bağlantıyı oluşturduklarında görüntüleme ve görüntüleme, düzenleme ve karşıya yükleme izinleri arasında seçim yapabilir.|

## <a name="sharepoint-site-level"></a>SharePoint (site düzeyi)

**Yönetici rolü:** yönetici SharePoint

Bu ayarlar SharePoint kuruluş genelindeki ayarlara tabi olduğundan, kuruluş düzeyi ayarı değişirse sitenin etkin paylaşım ayarı değişebilir. Burada bir ayar seçerseniz ve kuruluş düzeyi daha sonra daha kısıtlayıcı bir değere ayarlanırsa, bu site bu daha kısıtlayıcı değerde çalışır. Örneğin **, Herkes'i** seçerseniz ve kuruluş düzeyi ayarı daha sonra **Yeni ve mevcut konuklar** olarak ayarlanırsa, bu site yalnızca yeni ve mevcut konuklara izin verir. Kuruluş düzeyi ayarı daha sonra **Herkes** olarak ayarlanırsa, bu site yine *Herkes* bağlantılarına izin verir.

### <a name="site-sharing"></a>Site paylaşımı

SharePoint'da her site için konuk paylaşım izinleri ayarlayabilirsiniz. Bu ayar hem site paylaşımı hem de dosya ve klasör paylaşımı için geçerlidir. (Site paylaşımı için *herhangi bir* paylaşım kullanılamaz. **Herkes'i** seçerseniz, kullanıcılar *Herkes* bağlantılarını ve sitenin kendisini yeni ve mevcut konuklarla kullanarak dosya ve klasörleri paylaşabilir.)

Sitede bir duyarlılık etiketi uygulanmışsa, bu etiket dış paylaşım ayarlarını denetleyebilir. Daha fazla bilgi için bkz. [Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Kanal sitelerinin paylaşım ayarları yalnızca [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell cmdlet'i kullanılarak değiştirilebilir.

**Gezinti:** SharePoint yönetim merkezi > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler**</a> > **Dış paylaşımı düzenle** > site > **İlkeler** sekmesini seçin

![site dış paylaşım ayarlarını SharePoint ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Site içeriği ile paylaşılabilir|Site türüne göre değişir (aşağıdaki tabloya bakın)|Bu site için izin verilen dış paylaşımın türünü gösterir. Burada sağlanan seçenekler, SharePoint için kuruluş düzeyinde paylaşım ayarlarına tabidir.|

### <a name="site-file-and-folder-link-settings"></a>Site dosyası ve klasör bağlantısı ayarları

Bağlantı türü ve izinler için varsayılanları ve her site için *Herkes* bağlantıları için süre sonu ayarlarını ayarlayabilirsiniz. Site düzeyinde ayarlandığında, bu ayarlar kuruluş düzeyi ayarlarını geçersiz kılar. *Kuruluş düzeyinde Herkes* bağlantıları devre dışı bırakılırsa *, Herkes* site düzeyinde kullanılabilir bir bağlantı türü olmayacaktır.

**Gezinti:** SharePoint yönetim merkezi > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler**</a> > **Dış paylaşımı düzenle** > site > **İlkeler** sekmesini seçin

![SharePoint site düzeyi bağlantı paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-site-link-sharing-settings.png)

| Ayar | Varsayılan | Açıklama |
|:-----|:-----|:-----|
|Etki alanına göre paylaşımı sınırlama|Kapalı|Bu ayar, paylaşım için izin verilen veya engellenen etki alanlarının listesini belirtmenize olanak tanır. İzin verilen etki alanları belirtildiğinde, paylaşım davetleri yalnızca bu etki alanlarına gönderilebilir. Reddedilen etki alanları belirtildiğinde, paylaşım davetleri bu etki alanlarına gönderilemez. <p> Bu ayar, kuruluş veya Azure AD düzeyinde ayarlanan etki alanı kısıtlamalarını geçersiz kılmak için kullanılamaz.|
|Varsayılan paylaşım bağlantı türü|Kuruluş düzeyi ayarıyla aynı|Bu ayar, bu sitedeki kullanıcılara sunulan varsayılan paylaşım bağlantısını belirtmenize olanak tanır. *Kuruluş düzeyi ayarıyla aynı seçeneği*, kuruluş ve site paylaşım ayarlarının bir birleşimiyle tanımlanır.|
|Herkes bağlantıları için gelişmiş ayarlar|Kuruluş düzeyi ayarıyla aynı|Bu sitedeki bir dosya için *Bir Herkes* bağlantısı oluşturulduktan sonra süresi dolan gün sayısını belirtir. Süresi dolan bağlantılar yenilenemez. Süre sonunu geçtikten sonra paylaşmaya devam etmeniz gerekiyorsa yeni bir bağlantı oluşturun.|
|Varsayılan bağlantı izni|Kuruluş düzeyi ayarıyla aynı|Bu ayar, bu sitedeki dosyalar için oluşturulan paylaşım bağlantıları için varsayılan izni (Görüntüleme veya Düzenleme) belirtmenize olanak tanır.|

### <a name="default-site-sharing-settings"></a>Varsayılan site paylaşım ayarları

Aşağıdaki tabloda her site türü için varsayılan paylaşım ayarı gösterilmektedir.

| Site türü | Varsayılan paylaşım ayarı |
|:-----|:-----|
|Klasik|**Yalnızca kuruluşunuzdaki kişiler**|
|OneDrive|**Kimse**|
|Gruba bağlı siteler (Teams dahil)|Grup **sahiplerinin kuruluş dışındaki kişileri gruplara eklemesine izin ver** Microsoft 365 Grupları ayarı **Açıksa** **yeni ve mevcut konuklar**; aksi takdirde **yalnızca Mevcut konuklar**|
|İletişim|**Yalnızca kuruluşunuzdaki kişiler**|
|Grubu olmayan modern siteler (#STS3 TeamSite)|**Yalnızca kuruluşunuzdaki kişiler**|

> [!NOTE]
> Kök iletişim sitesinin (tenant-name.sharepoint.com) varsayılan paylaşım ayarı **Herkes'tır**.

## <a name="see-also"></a>Ayrıca bkz.

[dış paylaşıma genel bakış SharePoint ve OneDrive](/sharepoint/external-sharing-overview)

[Microsoft Teams'de konuk erişimi](/MicrosoftTeams/guest-access)

[Microsoft 365 Grupları konuk ekleme](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
