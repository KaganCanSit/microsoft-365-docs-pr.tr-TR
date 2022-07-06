---
title: Microsoft Teams, Microsoft 365 Grupları ve SharePoint siteleriyle duyarlılık etiketlerini kullanma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkSPO
search.appverid:
- MOE150
- MET150
description: SharePoint ve Microsoft Teams sitelerindeki ve Microsoft 365 gruplarındaki içeriği korumak için duyarlılık etiketlerini kullanın.
ms.openlocfilehash: 17b1a2aab1da0e2c901aac14b3bf675cbbabe740
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628693"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Belge ve e-postaları sınıflandırmak ve korumak için [duyarlılık etiketlerini](sensitivity-labels.md) kullanmanın yanı sıra, şu kapsayıcılardaki içeriği korumak için duyarlılık etiketlerini de kullanabilirsiniz: Microsoft Teams siteleri, Microsoft 365 grupları ([eski adıyla Office 365 grupları](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) ve SharePoint siteleri. Bu kapsayıcı düzeyinde sınıflandırma ve koruma için aşağıdaki etiket ayarlarını kullanın:

- Ekip sitelerinin ve Microsoft 365 gruplarının gizliliği (genel veya özel)
- Dış kullanıcı erişimi
- SharePoint sitelerinden dış paylaşım
- Yönetilmeyen cihazlardan erişim
- Kimlik doğrulama bağlamları (önizlemede)
- SharePoint sitesi için varsayılan paylaşım bağlantısı (Yalnızca PowerShell yapılandırması)
- Önizlemede: Site paylaşım ayarları (Yalnızca PowerShell yapılandırması)

> [!IMPORTANT]
> Yönetilmeyen cihazlar ve kimlik doğrulama bağlamları için ayarlar, Azure Active Directory Koşullu Erişim ile birlikte çalışır. Bu ayarlar için duyarlılık etiketi kullanmak istiyorsanız bu bağımlı özelliği yapılandırmanız gerekir. Aşağıdaki yönergelere ek bilgiler eklenmiştir.

Bu duyarlılık etiketini desteklenen bir kapsayıcıya uyguladığınızda, etiket otomatik olarak site veya gruba sınıflandırma ve yapılandırılmış koruma ayarlarını uygular.

Ancak bu kapsayıcılardaki içerik, görsel işaretler ve şifreleme gibi dosya ve e-postalar için sınıflandırma veya ayarların etiketlerini devralmaz. Kullanıcıların belgelerini SharePoint sitelerinde veya ekip sitelerinde etiketleyebilmesi [için, SharePoint ve OneDrive'da Office dosyaları için duyarlılık etiketlerini etkinleştirdiğinizden](sensitivity-labels-sharepoint-onedrive-files.md) emin olun.

## <a name="using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri için duyarlılık etiketlerini kullanma

Kapsayıcılar için duyarlılık etiketlerini etkinleştirmeden ve yeni ayarlar için duyarlılık etiketlerini yapılandırmadan önce, kullanıcılar kendi uygulamalarında duyarlılık etiketlerini görebilir ve uygulayabilir. Örneğin, Word'den:

![Word masaüstü uygulamasında görüntülenen duyarlılık etiketi.](../media/sensitivity-label-word.png)

Kapsayıcılar için duyarlılık etiketlerini etkinleştirip yapılandırdıktan sonra, kullanıcılar ayrıca Microsoft ekip sitelerine, Microsoft 365 gruplarına ve SharePoint sitelerine duyarlılık etiketlerini görebilir ve uygulayabilir. Örneğin, SharePoint'ten yeni bir ekip sitesi oluşturduğunuzda:

![SharePoint'ten ekip sitesi oluştururken duyarlılık etiketi.](../media/sensitivity-labels-new-team-site.png)

> [!NOTE]
> Kapsayıcılar için duyarlılık etiketleri, şu anda önizleme aşamasında olan [Teams paylaşılan kanallarını](/MicrosoftTeams/shared-channels) destekler. Bir ekibin paylaşılan kanalları varsa, duyarlılık etiketi ayarlarını üst ekibinden otomatik olarak devralır ve bu etiket kaldırılamaz veya başka bir etiketle değiştirilemez.

## <a name="how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels"></a>Kapsayıcılar için duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme

Kapsayıcılar için duyarlılık etiketlerini henüz etkinleştirmediyseniz, aşağıdaki adım kümesini tek seferlik bir yordam olarak uygulayın:

1. Bu özellik Azure AD işlevselliği kullandığından, duyarlılık etiketi desteğini etkinleştirmek için Azure AD belgelerindeki yönergeleri izleyin: [Azure Active Directory'de Microsoft 365 gruplarına duyarlılık etiketleri atama](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels).

2. Şimdi duyarlılık etiketlerinizi Azure AD eşitlemeniz gerekir. İlk olarak [Güvenlik & Uyumluluk PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Örneğin, yönetici olarak çalıştırdığınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın.

3. Ardından duyarlılık etiketlerinizin Microsoft 365 gruplarıyla kullanılabildiğinden emin olmak için aşağıdaki komutu çalıştırın:

    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-groups-and-site-settings"></a>Grupları ve site ayarlarını yapılandırma

Önceki bölümde açıklandığı gibi kapsayıcılar için duyarlılık etiketleri etkinleştirildikten sonra, duyarlılık etiketleme yapılandırmasında gruplar ve siteler için koruma ayarlarını yapılandırabilirsiniz. Kapsayıcılar için duyarlılık etiketleri etkinleştirilene kadar ayarlar görünür ancak bunları yapılandıramazsınız.

1. [Duyarlılık etiketi oluşturmak veya düzenlemek](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) için genel yönergeleri izleyin ve etiketin kapsamı için **Gruplar & sitelerini** seçtiğinizden emin olun: 
    
    ![Dosyalar ve e-postalar için duyarlılık etiketi kapsam seçenekleri.](../media/groupsandsites-scope-options-sensitivity-label.png)
    
    Etiket için yalnızca bu kapsam seçildiğinde, etiket duyarlılık etiketlerini destekleyen Office uygulamalarında görüntülenmez ve dosyalara ve e-postalara uygulanamaz. Etiketlerin bu ayrımının olması hem kullanıcılar hem de yöneticiler için yararlı olabilir, ancak etiket dağıtımınızın karmaşıklığını da ekleyebilir.
    
    Örneğin, SharePoint [etiketlenmiş bir belgenin etiketli](sensitivity-labels.md#label-priority-order-matters) bir siteye ne zaman yüklendiğini algıladığından, etiket sıralamanızı dikkatle gözden geçirmeniz gerekir. Bu senaryoda, belge sitenin etiketinden daha yüksek öncelikli duyarlılık etiketine sahip olduğunda bir denetim olayı ve e-posta otomatik olarak oluşturulur. Daha fazla bilgi için bu sayfadaki [Duyarlılık etiketi etkinliklerini denetleme](#auditing-sensitivity-label-activities) bölümüne bakın. 

2. Ardından, **Gruplar ve siteler için koruma ayarlarını tanımla** sayfasında, kullanılabilir seçeneklerden birini veya her ikisini birden seçin:
    
    - **Gizlilik ve Dış kullanıcılar erişim ayarlarını** yapılandırmak için **gizlilik** ve **dış kullanıcı erişim** ayarları. 
    - **Dış paylaşım ve Koşullu Erişim ayarları**, **Etiketli SharePoint sitelerinden dış paylaşımı denetle ve Etiketli SharePoint sitelerini** **korumak için Koşullu Erişim Azure AD kullan** ayarını yapılandırmak için.

3. **Gizlilik ve dış kullanıcı erişim ayarlarını** seçtiyseniz, şimdi aşağıdaki ayarları yapılandırın:
    
    - **Gizlilik**: Kuruluşunuzdaki herkesin bu etiketin uygulandığı ekip sitesine veya gruba erişmesini istiyorsanız Varsayılan **Genel'i** koruyun.
        
        Erişimin yalnızca kuruluşunuzdaki onaylanan üyelerle sınırlandırılmasını istiyorsanız **Özel'i** seçin.
        
        Duyarlılık etiketini kullanarak kapsayıcıdaki içeriği korumak ancak yine de kullanıcıların gizlilik ayarını kendilerinin yapılandırmasına izin vermek istediğinizde **Hiçbiri'ni** seçin.
        
        **Genel** veya **Özel** ayarının ayarları ve bu etiketi kapsayıcıya uyguladığınızda gizlilik ayarını kilitleyin. Seçtiğiniz ayar, ekip veya grup için yapılandırılabilir önceki gizlilik ayarlarının yerini alır ve gizlilik değerini kilitleyerek yalnızca önce kapsayıcıdan duyarlılık etiketi kaldırılarak değiştirilebilir. Duyarlılık etiketini kaldırdıktan sonra, etiketten gizlilik ayarı kalır ve kullanıcılar artık etiketi yeniden değiştirebilir.
    
    - **Dış kullanıcı erişimi**: Grup sahibinin [gruba konuk ekleyip ekleyemeyeceğini](/office365/admin/create-groups/manage-guest-access-in-groups) denetler.

4. **Dış paylaşım ve Koşullu Erişim ayarlarını** seçtiyseniz, şimdi aşağıdaki ayarları yapılandırın:
    
    - **Etiketli SharePoint sitelerinden dış paylaşımı denetleme**: Bu seçeneği belirleyerek herkes, yeni ve mevcut konuklar, mevcut konuklar veya yalnızca kuruluşunuzdaki kişiler için dış paylaşımı seçin. Bu yapılandırma ve ayarlar hakkında daha fazla bilgi için SharePoint belgelerine bakın. [Site için dış paylaşımı açma veya kapatma](/sharepoint/change-external-sharing-site).
    
    - **Etiketli SharePoint sitelerini korumak için koşullu erişim Azure AD kullanın**: Bu seçeneği yalnızca kuruluşunuz yapılandırdıysa ve [Azure Active Directory Koşullu Erişim](/azure/active-directory/conditional-access/overview) kullanıyorsa seçin. Ardından aşağıdaki ayarlardan birini seçin:
    
        - **Kullanıcıların yönetilmeyen cihazlardan SharePoint sitelerine erişip erişemeyeceğini belirleyin**: Bu seçenek, yönetilmeyen cihazlardan SharePoint ve OneDrive içeriğine erişimi engellemek veya sınırlamak için Azure AD Koşullu Erişim kullanan SharePoint özelliğini kullanır. Daha fazla bilgi için SharePoint [belgelerinden Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices) bölümüne bakın. Bu etiket ayarı için belirttiğiniz seçenek, [SharePoint yönergelerindeki Belirli bir SharePoint sitesine veya OneDrive'a erişimi engelleme veya sınırlama](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive) bölümünde 3-5 arası adımlarda açıklandığı gibi, site için PowerShell komutunu çalıştırmaya eşdeğerdir.
            
            Ek yapılandırma bilgileri [için bu bölümün sonundaki yönetilmeyen cihazlara yönelik bağımlılıklar seçeneği hakkında daha fazla bilgi](#more-information-about-the-dependencies-for-the-unmanaged-devices-option) bölümüne bakın.
            
        - **Mevcut kimlik doğrulama bağlamını seçin**: Şu anda önizleme aşamasında olan bu seçenek, kullanıcılar bu etiketin uygulandığı SharePoint sitelerine eriştiğinde daha sıkı erişim koşulları uygulamanıza olanak tanır. Bu koşullar, kuruluşunuzun Koşullu Erişim dağıtımı için oluşturulmuş ve yayımlanmış mevcut bir kimlik doğrulama bağlamını seçtiğinizde uygulanır. Kullanıcılar yapılandırılmış koşulları karşılamıyorsa veya kimlik doğrulama bağlamlarını desteklemeyen uygulamalar kullanıyorlarsa erişimleri reddedilir.
            
            Ek yapılandırma bilgileri [için bu bölümün sonundaki kimlik doğrulama bağlamı seçeneğine yönelik bağımlılıklar hakkında daha fazla bilgi](#more-information-about-the-dependencies-for-the-authentication-context-option) bölümüne bakın.
            
            Bu etiket yapılandırması için örnekler:
            
             - [Çok faktörlü kimlik doğrulaması (MFA)](/azure/active-directory/conditional-access/untrusted-networks) gerektirecek şekilde yapılandırılmış bir kimlik doğrulama bağlamı seçersiniz. Bu etiket daha sonra çok gizli öğeler içeren bir SharePoint sitesine uygulanır. Sonuç olarak, güvenilmeyen bir ağdan gelen kullanıcılar bu sitedeki bir belgeye erişmeye çalıştığında, belgeye erişebilmeleri için önce tamamlamaları gereken MFA istemini görürler.
             
             - [Kullanım koşulları (ToU) ilkeleri](/azure/active-directory/conditional-access/terms-of-use) için yapılandırılmış bir kimlik doğrulama bağlamı seçersiniz. Bu etiket daha sonra, yasal veya uyumluluk nedenleriyle kullanım koşulları kabulü gerektiren öğeler içeren bir SharePoint sitesine uygulanır. Sonuç olarak, kullanıcılar bu sitedeki bir belgeye erişmeye çalıştığında, özgün belgeye erişebilmeleri için kabul etmesi gereken bir kullanım koşulları belgesi görürler.

> [!IMPORTANT]
> Etiketi bir ekip, grup veya siteye uyguladığınızda yalnızca bu site ve grup ayarları etkinleşir. [Etiketin kapsamı](sensitivity-labels.md#label-scopes) dosya ve e-posta içeriyorsa, şifreleme ve içerik işaretleme gibi diğer etiket ayarları ekip, grup veya site içindeki içeriğe uygulanmaz.

Duyarlılık etiketiniz henüz yayımlanmadıysa, şimdi duyarlılık [etiketi ilkesine ekleyerek](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) yayımlayın. Bu etiketi içeren bir duyarlılık etiketi ilkesi atanan kullanıcılar, bu ilkeyi siteler ve gruplar için seçebilir.

##### <a name="more-information-about-the-dependencies-for-the-unmanaged-devices-option"></a>Yönetilmeyen cihazlar seçeneği için bağımlılıklar hakkında daha fazla bilgi

SharePoint için bağımlı koşullu erişim ilkesini [Uygulama tarafından zorlanan kısıtlamaları kullanma](/sharepoint/app-enforced-restrictions) bölümünde belirtildiği gibi yapılandırmazsanız, burada belirttiğiniz seçeneğin hiçbir etkisi olmaz. Buna ek olarak, kiracı düzeyinde yapılandırılmış bir ayardan daha az kısıtlayıcıysa hiçbir etkisi olmaz. Yönetilmeyen cihazlar için kuruluş genelinde bir ayar yapılandırdıysanız, aynı veya daha kısıtlayıcı bir etiket ayarı seçin

Örneğin, kiracınız **Sınırlı, yalnızca web erişimine izin ver** için yapılandırılmışsa, tam erişime izin veren etiket ayarının etkisi olmaz çünkü daha az kısıtlayıcıdır. Bu kiracı düzeyi ayarı için erişimi engellemek için etiket ayarını (daha kısıtlayıcı) veya sınırlı erişim için etiket ayarını (kiracı ayarıyla aynı) seçin.

SharePoint ayarlarını etiket yapılandırmasından ayrı olarak yapılandırabildiğiniz için, duyarlılık etiketi yapılandırmasında bağımlılıkların mevcut olup olmadığı denetlenemez. Bu bağımlılıklar, etiket oluşturulduktan ve yayımlandıktan ve hatta etiket uygulandıktan sonra bile yapılandırılabilir. Ancak etiket zaten uygulanmışsa, etiket ayarı kullanıcı bir sonraki kimlik doğrulamasından sonra geçerli olmaz.

##### <a name="more-information-about-the-dependencies-for-the-authentication-context-option"></a>Kimlik doğrulama bağlamı seçeneği için bağımlılıklar hakkında daha fazla bilgi

Seçim açılan listesinde görüntülemek için, kimlik doğrulama bağlamlarının Azure Active Directory Koşul Erişimi yapılandırmanızın bir parçası olarak oluşturulması, yapılandırılması ve yayımlanması gerekir. Daha fazla bilgi ve yönergeler için, Azure AD Koşullu Erişim belgelerindeki [Kimlik doğrulama bağlamlarını yapılandırma](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts) bölümüne bakın.

Tüm uygulamalar kimlik doğrulama bağlamlarını desteklemez. Desteklenmeyen bir uygulamaya sahip bir kullanıcı bir kimlik doğrulama bağlamı için yapılandırılmış siteye bağlanırsa, erişim reddedildi iletisini görür veya kimlik doğrulamasından geçmek isteyip istemediğiniz sorulur. Şu anda kimlik doğrulama bağlamlarını destekleyen uygulamalar:

- Web için Outlook'u içeren Web için Office

- Windows ve macOS için Microsoft Teams (Teams web uygulamasını hariç tutar)

- Microsoft Planner

- Word, Excel ve PowerPoint için Microsoft 365 Uygulamaları; en düşük sürümler:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 2.48.303
    - Android: 16.0.13924.10000

- Outlook için Microsoft 365 Uygulamaları; en düşük sürümler:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 4.2109.0
    - Android: 4.2025.1

- OneDrive eşitleme uygulaması, en düşük sürümler:
    - Windows: 21.002
    - macOS: 21.002
    - iOS: 12.30'da kullanıma sunulacak
    - Android: Henüz desteklenmiyor

Bu önizleme için bilinen sınırlamalar:

- OneDrive eşitleme uygulaması için, diğer siteler için değil, yalnızca OneDrive için desteklenir.

- Aşağıdaki özellikler ve uygulamalar kimlik doğrulama bağlamlarıyla uyumsuz olabilir, bu nedenle bir kullanıcı bir kimlik doğrulama bağlamını kullanarak bir siteye başarıyla eriştiğinde bunların çalışmaya devam edip etmediğini denetlemenizi öneririz:
    
    - Power Apps veya Power Automate kullanan iş akışları
    - Üçüncü taraf uygulamaları

### <a name="configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings"></a>PowerShell gelişmiş ayarlarını kullanarak site için varsayılan paylaşım bağlantı türü ayarlarını yapılandırma

Microsoft Purview uyumluluk portalı yapılandırabileceğiniz sitelerin ve grupların etiket ayarlarına ek olarak, site için varsayılan paylaşım bağlantı türünü de yapılandırabilirsiniz. Belgeler için duyarlılık etiketleri, varsayılan paylaşım bağlantı türü için de yapılandırılabilir. Kullanıcılar Office uygulamalarında **Paylaş** düğmesini seçtiğinde, fazla paylaşımı önlemeye yardımcı olan bu ayarlar otomatik olarak seçilir. 

Daha fazla bilgi ve yönergeler için bkz. [SharePoint ve OneDrive'da siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanma](sensitivity-labels-default-sharing-link.md).

### <a name="configure-site-sharing-permissions-by-using-powershell-advanced-settings"></a>PowerShell gelişmiş ayarlarını kullanarak site paylaşım izinlerini yapılandırma

> [!NOTE]
> Bu etiket ayarı şu anda önizleme aşamasındadır.

SharePoint sitesine uygulanacak duyarlılık etiketi için yapılandırabileceğiniz bir diğer PowerShell gelişmiş ayarı da **MembersCanShare** ayarıdır. Bu ayar, SharePoint yönetim merkezinden ayarlayabileceğiniz eşdeğer yapılandırmadır > **Site izinleri** > **Site Paylaşımı Üyelerin** > **Paylaşım izinlerini** **paylaşma** >  şeklini değiştirme. 

Üç seçenek, **MembersCanShare** PowerShell gelişmiş ayarı için eşdeğer değerlerle listelenir:

|SharePoint yönetim merkezinden seçenek |MembersCanShare için eşdeğer PowerShell değeri |
|----------------------------------------|------------------------------------------------|
|**Site sahipleri ve üyeleri dosyaları, klasörleri ve siteyi paylaşabilir. Düzenleme izinlerine sahip kişiler dosya ve klasörleri paylaşabilir.**| MemberShareAll|
|**Site sahipleri ve üyeleri ile Düzenleme izinlerine sahip kişiler dosya ve klasörleri paylaşabilir, ancak siteyi yalnızca site sahipleri paylaşabilir.**|MemberShareFileAndFolder|
|**Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir.**|MemberShareNone|

Bu yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. SharePoint topluluk belgelerinden [üyelerin paylaşım şeklini değiştirme](/microsoft-365/community/sharepoint-security-a-team-effort#change-how-members-can-share) .

Duyarlılık etiketi GUID'sinin **8faca7b8-8d20-48a3-8ea2-0f96310a848e** olduğu örnek:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{MembersCanShare="MemberShareNone"}
````

PowerShell gelişmiş ayarlarını belirtme konusunda daha fazla yardım için bkz. [Gelişmiş ayarları belirtmek için PowerShell ipuçları](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="sensitivity-label-management"></a>Duyarlılık etiketi yönetimi

Siteler ve gruplar için yapılandırılan duyarlılık etiketlerini oluştururken, değiştirirken veya silerken aşağıdaki kılavuzu kullanın.

### <a name="creating-and-publishing-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış etiketler oluşturma ve yayımlama

Bu etiket site ve grup ayarları için yapılandırıldığında kullanıcılarınız için bir etiket yayımlamak için aşağıdaki kılavuzu kullanın:

1. Duyarlılık etiketini oluşturup yapılandırdıktan sonra, bu etiketi yalnızca birkaç test kullanıcısı için geçerli olan bir etiket ilkesine ekleyin.

2. Değişikliğin çoğaltılması için bekleyin:
    
   - Yeni etiket: En az bir saat bekleyin.
   - Mevcut etiket: En az 24 saat bekleyin.
    
    Etiketlerin zamanlaması hakkında daha fazla bilgi için bkz. [Yeni etiketlerin ve değişikliklerin etkin hale gelmesini bekleme](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect) zamanı.

3. Bu bekleme süresinden sonra test kullanıcı hesaplarından birini kullanarak 1. adımda oluşturduğunuz etiketle bir ekip, Microsoft 365 grubu veya SharePoint sitesi oluşturun.

4. Bu oluşturma işlemi sırasında hata yoksa, etiketi kiracınızdaki tüm kullanıcılara yayımlamanın güvenli olduğunu biliyorsunuz.

### <a name="modifying-published-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış yayımlanmış etiketleri değiştirme

En iyi uygulama olarak, etiket ekiplere, gruplara veya sitelere uygulandıktan sonra duyarlılık etiketi için site ve grup ayarlarını değiştirmeyin. Bunu yaparsanız, değişikliklerin etiketi uygulanmış olan tüm kapsayıcılara çoğaltılması için en az 24 saat beklemeyi unutmayın.

Ayrıca, değişiklikleriniz **Dış kullanıcılar erişim** ayarını da içeriyorsa:

- Yeni ayar yeni kullanıcılar için geçerlidir ancak mevcut kullanıcılar için geçerli değildir. Örneğin, bu ayar daha önce seçilmişse ve sonuç olarak, konuk kullanıcılar siteye eriştiyse, etiket yapılandırmasında bu ayar temizlendikten sonra bu konuk kullanıcılar siteye erişmeye devam edebilir.

- hiddenMembership ve roleEnabled grup özelliklerinin gizlilik ayarları güncelleştirilmez.

### <a name="deleting-published-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış yayımlanmış etiketleri silme

Site ve grup ayarlarının etkinleştirildiği bir duyarlılık etiketini silerseniz ve bu etiket bir veya daha fazla etiket ilkesine dahil edilirse, bu eylem yeni ekipler, gruplar ve siteler için oluşturma hatalarına neden olabilir. Bu durumu önlemek için aşağıdaki kılavuzu kullanın:

1. Duyarlılık etiketini, etiketi içeren tüm etiket ilkelerinden kaldırın.

2. En az bir saat bekleyin.

3. Bu bekleme süresinden sonra bir ekip, grup veya site oluşturmayı deneyin ve etiketin artık görünür olmadığını onaylayın.

4. Duyarlılık etiketi görünmüyorsa, artık etiketi güvenle silebilirsiniz.

## <a name="how-to-apply-sensitivity-labels-to-containers"></a>Kapsayıcılara duyarlılık etiketleri uygulama

Artık duyarlılık etiketini veya etiketlerini aşağıdaki kapsayıcılara uygulamaya hazırsınız:

- [Azure AD'de Microsoft 365 grubu](#apply-sensitivity-labels-to-microsoft-365-groups)
- [Microsoft Teams ekip sitesi](#apply-a-sensitivity-label-to-a-new-team)
- [Web üzerinde Outlook'de Microsoft 365 grubu](#apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web)
- [SharePoint sitesi](#apply-a-sensitivity-label-to-a-new-site)

[Birden çok siteye duyarlılık etiketi uygulamanız](#use-powershell-to-apply-a-sensitivity-label-to-multiple-sites) gerekiyorsa PowerShell'i kullanabilirsiniz.

### <a name="apply-sensitivity-labels-to-microsoft-365-groups"></a>Microsoft 365 gruplarına duyarlılık etiketleri uygulama

Artık duyarlılık etiketini veya etiketlerini Microsoft 365 gruplarına uygulamaya hazırsınız. Yönergeler için Azure AD belgelerine dönün:

- [Azure portal'da yeni bir gruba etiket atama](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

- [Azure portal'de var olan bir gruba etiket atama](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

- [Azure portal'da var olan bir gruptan etiket kaldırma](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

### <a name="apply-a-sensitivity-label-to-a-new-team"></a>Yeni bir takıma duyarlılık etiketi uygulama

Kullanıcılar Microsoft Teams'de yeni ekipler oluştururken duyarlılık etiketlerini seçebilir. **Duyarlılık** açılan listesinden etiketi seçtiklerinde, gizlilik ayarı etiket yapılandırmasını yansıtacak şekilde değişebilir. Etiket için seçtiğiniz dış kullanıcılar erişim ayarına bağlı olarak, kullanıcılar kuruluş dışındaki kişileri ekise ekleyebilir veya ekleyemez.

[Teams için duyarlılık etiketleri hakkında daha fazla bilgi edinin](/microsoftteams/sensitivity-labels)

![Yeni bir ekip oluştururken gizlilik ayarı.](../media/privacy-setting-new-team.png)

Ekibi oluşturduktan sonra duyarlılık etiketi tüm kanalların sağ üst köşesinde görünür.

![Duyarlılık etiketi ekipte görünür.](../media/privacy-setting-teams.png)

Hizmet, microsoft 365 grubuna ve bağlı SharePoint ekip sitesine otomatik olarak aynı duyarlılık etiketini uygular.

### <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Web üzerinde Outlook'da yeni bir gruba duyarlılık etiketi uygulama

Web üzerinde Outlook'da, yeni bir grup oluşturduğunuzda yayımlanan etiketler için **Duyarlılık** seçeneğini belirleyebilir veya değiştirebilirsiniz:

![Grup oluşturma ve Duyarlılık altında bir seçenek belirleme.](../media/sensitivity-label-new-group.png)

### <a name="apply-a-sensitivity-label-to-a-new-site"></a>Yeni siteye duyarlılık etiketi uygulama

Yöneticiler ve son kullanıcılar [modern ekip siteleri ve iletişim siteleri oluştururken](/sharepoint/create-site-collection) duyarlılık etiketlerini seçebilir ve **Gelişmiş ayarlar'ı** genişletebilir:

![Bir site oluşturma ve Duyarlılık altında bir seçenek belirleme.](../media/sensitivity-label-new-communication-site.png)

Açılan kutuda seçimin etiket adları görüntülenir ve yardım simgesi tüm etiket adlarını araç ipucuyla birlikte görüntüler ve bu da kullanıcıların uygulanacak doğru etiketi belirlemesine yardımcı olabilir.

Etiket uygulandığında ve kullanıcılar siteye göz attığında, etiketin adını ve uygulanan ilkeleri görürler. Örneğin, bu site **Gizli** olarak etiketlenmiş ve gizlilik ayarı **Özel** olarak ayarlanmıştır:

![Duyarlılık etiketi uygulanmış bir site.](../media/sensitivity-label-site.png)

### <a name="use-powershell-to-apply-a-sensitivity-label-to-multiple-sites"></a>Birden çok siteye duyarlılık etiketi uygulamak için PowerShell kullanma

Birçok siteye duyarlılık etiketi uygulamak için geçerli [SharePoint Online Yönetim Kabuğu'ndan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) *DuyarlılıkLabel* parametresiyle [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) ve [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanabilirsiniz. Siteler herhangi bir SharePoint site koleksiyonu veya OneDrive sitesi olabilir.

SharePoint Online Yönetim Kabuğu'nun 16.0.19418.12000 veya sonraki bir sürümüne sahip olduğunuzdan emin olun.

1. **Yönetici Olarak Çalıştır** seçeneğiyle bir PowerShell oturumu açın.

2. Etiket GUID'nizi bilmiyorsanız: [Güvenlik & Uyumluluk PowerShell'e bağlanın](/powershell/exchange/connect-to-scc-powershell) ve duyarlılık etiketlerinin ve guid'lerinin listesini alın.

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Şimdi [SharePoint Online PowerShell'e bağlanın](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) ve etiket GUID'nizi değişken olarak depolayın. Örneğin:

   ```powershell
   $Id = [GUID]("e48058ea-98e8-4940-8db0-ba1310fd955e")
   ```

4. URL'lerinde ortak bir tanımlayıcı dizesi olan birden çok siteyi tanımlayan yeni bir değişken oluşturun. Örneğin:

   ```powershell
   $sites = Get-SPOSite -IncludePersonalSite $true -Limit all -Filter "Url -like 'documents"
   ```

5. Etiketi bu sitelere uygulamak için aşağıdaki komutu çalıştırın. Örneklerimizi kullanarak:

   ```powershell
   $sites | ForEach-Object {Set-SPOTenant $_.url -SensitivityLabel $Id}
   ```

Bu komut serisi, kiracınızdaki birden çok siteyi aynı duyarlılık etiketiyle etiketlemenize olanak tanır. Bu nedenle, site başına yapılandırmaya yönelik Set-SPOSite cmdlet'i yerine Set-SPOTenant cmdlet'ini kullanırsınız. Ancak, bu sitelerin her biri için aşağıdaki komutu yineleyerek belirli sitelere farklı bir etiket uygulamanız gerektiğinde Set-SPOSite cmdlet'ini kullanın: `Set-SPOSite -Identity <URL> -SensitivityLabel "<labelguid>"`

## <a name="view-and-manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>SharePoint yönetim merkezinde duyarlılık etiketlerini görüntüleme ve yönetme

Uygulanan duyarlılık etiketlerini görüntülemek, sıralamak ve aramak için yeni SharePoint yönetim merkezinde <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteleri**</a> kullanın. Önce **Duyarlılık** sütununu eklemeniz gerekebilir:

![Etkin siteler sayfasındaki Duyarlılık sütunu.](../media/manage-site-sensitivity-labels.png)

Etkin siteler sayfasından siteleri yönetme hakkında daha fazla bilgi ve sütun ekleme hakkında daha fazla bilgi için bkz. [Yeni SharePoint yönetim merkezinde siteleri yönetme](/sharepoint/manage-sites-in-new-admin-center).

Ayrıca bu sayfadan bir etiketi değiştirebilir ve uygulayabilirsiniz:

1. Ayrıntılar bölmesini açmak için site adını seçin.

2. **İlkeler** sekmesini ve ardından **Duyarlılık** ayarı için **Düzenle'yi** seçin.

3. **Duyarlılığı düzenle ayarı** bölmesinden, siteye uygulamak istediğiniz duyarlılık etiketini seçin. Belirli kullanıcılara duyarlılık etiketlerinin atanabildiği kullanıcı uygulamalarından farklı olarak, yönetim merkezi kiracınız için tüm duyarlılık etiketlerini görüntüler. Bir etiket seçtikten sonra **Kaydet'i** seçin.

## <a name="support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteği

Duyarlılık etiketlerini destekleyen yönetim merkezlerini kullandığınızda, Azure Active Directory portalı dışında kiracınız için tüm duyarlılık etiketlerini görürsünüz. Buna karşılık, duyarlılık etiketlerini yayımlama ilkelerine göre filtreleyen kullanıcı uygulamaları ve hizmetleri, bu etiketlerin bir alt kümesini görmenizi sağlayabilir. Azure Active Directory portalı etiketleri yayımlama ilkelerine göre de filtreler.

Aşağıdaki uygulamalar ve hizmetler, siteler ve grup ayarları için yapılandırılan duyarlılık etiketlerini destekler:

- Yönetici merkezleri:

  - SharePoint yönetim merkezi
  - Teams yönetim merkezi
  - Microsoft 365 yönetici merkezi
  - Microsoft Purview uyumluluk portalı

- Kullanıcı uygulamaları ve hizmetleri:

  - SharePoint
  - Teams
  - Web üzerinde Outlook ve Windows, macOS, iOS ve Android için
  - Forms
  - Stream
  - Planner 

Aşağıdaki uygulamalar ve hizmetler şu anda siteler ve grup ayarları için yapılandırılmış duyarlılık etiketlerini desteklemez:

- Yönetici merkezleri:

  - Exchange yönetim merkezi

- Kullanıcı uygulamaları ve hizmetleri:

  - Dynamics 365
  - Yammer
  - Project
  - Power BI
  - Uygulamalarım portalı

## <a name="classic-azure-ad-group-classification"></a>Klasik Azure AD grup sınıflandırması

Kapsayıcılar için duyarlılık etiketlerini etkinleştirdikten sonra, Azure AD grup sınıflandırmaları artık Microsoft 365 tarafından desteklenmez ve duyarlılık etiketlerini destekleyen sitelerde görüntülenmez. Ancak eski sınıflandırmalarınızı duyarlılık etiketlerine dönüştürebilirsiniz.

SharePoint için eski grup sınıflandırmasını nasıl kullanmış olabileceğiniz bir örnek olarak bkz. [SharePoint "modern" siteler sınıflandırması](/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Bu sınıflandırmalar, Azure AD PowerShell veya PnP Core kitaplığı kullanılarak yapılandırıldı ve ayar için `ClassificationList` değerler tanımlandı. Kiracınızda tanımlanmış sınıflandırma değerleri varsa, [AzureADPreview PowerShell modülünden](https://www.powershellgallery.com/packages/AzureADPreview) aşağıdaki komutu çalıştırdığınızda bunlar gösterilir:

```powershell
($setting["ClassificationList"])
```

Eski sınıflandırmalarınızı duyarlılık etiketlerine dönüştürmek için aşağıdakilerden birini yapın:

- Mevcut etiketleri kullan: Zaten yayımlanmış olan duyarlılık etiketlerini düzenleyerek siteler ve gruplar için istediğiniz etiket ayarlarını belirtin.

- Yeni etiketler oluşturma: Mevcut sınıflandırmalarınızla aynı adlara sahip yeni duyarlılık etiketleri oluşturup yayımlayarak siteler ve gruplar için istediğiniz etiket ayarlarını belirtin.

Sonra:

1. PowerShell'i kullanarak, ad eşlemesini kullanarak duyarlılık etiketlerini mevcut Microsoft 365 gruplarına ve SharePoint sitelerine uygulayın. Yönergeler için sonraki bölüme bakın.

2. Mevcut gruplardan ve sitelerden eski sınıflandırmaları kaldırın.

Kullanıcıların uygulama ve hizmetlerde henüz duyarlılık etiketlerini desteklemeyen yeni gruplar oluşturmasını engelleyemezsiniz ancak kullanıcıların eski sınıflandırmalarla oluşturduğu yeni grupları aramak için yinelenen bir PowerShell betiği çalıştırabilir ve bunları duyarlılık etiketlerini kullanacak şekilde dönüştürebilirsiniz.

Siteler ve gruplar için duyarlılık etiketlerinin ve Azure AD sınıflandırmalarının bir arada bulunmalarını yönetmenize yardımcı olmak için bkz. [Microsoft 365 grupları için Azure Active Directory sınıflandırması ve duyarlılık etiketleri](migrate-aad-classification-sensitivity-labels.md).

### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Microsoft 365 gruplarının sınıflandırmalarını duyarlılık etiketlerine dönüştürmek için PowerShell kullanma

1. İlk olarak [Güvenlik & Uyumluluk PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Örneğin, yönetici olarak çalıştırdığınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın:

2. [Get-Label](/powershell/module/exchange/get-label) cmdlet'ini kullanarak duyarlılık etiketlerinin ve GUID'lerin listesini alın:

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Microsoft 365 gruplarınıza uygulamak istediğiniz duyarlılık etiketlerinin GUID'lerini not edin.

4. Şimdi [ayrı bir Windows PowerShell penceresinde Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

5. Şu anda "Genel" sınıflandırmasına sahip grupların listesini almak için örnek olarak aşağıdaki komutu kullanın:

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Her grup için yeni duyarlılık etiketi GUID'sini ekleyin. Örneğin:

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Kalan grup sınıflandırmalarınız için 5. ve 6. adımları yineleyin.

## <a name="auditing-sensitivity-label-activities"></a>Duyarlılık etiketi etkinliklerini denetleme

> [!IMPORTANT]
> Kapsayıcıları koruyan etiketler için yalnızca **Gruplar & siteleri** kapsamını seçerek etiket ayrımı kullanıyorsanız: Bu bölümde açıklanan **Algılanan belge duyarlılığı uyuşmazlığı** denetim olayı ve e-posta nedeniyle, **etiketlerden önce Dosyalar & e-postaları** kapsamına sahip etiketlerden önce [sıralamayı](sensitivity-labels.md#label-priority-order-matters) göz önünde bulundurun. 

Birisi duyarlılık etiketiyle korunan bir siteye belge yüklerse ve belgenin öncelik duyarlılık etiketi siteye uygulanan duyarlılık etiketinden [daha yüksekse](sensitivity-labels.md#label-priority-order-matters) , bu eylem engellenmez. Örneğin, Bir SharePoint sitesine **Genel** etiketini uyguladınız ve birisi bu siteye **Gizli** etiketli bir belge yükler. Daha yüksek önceliğe sahip bir duyarlılık etiketi, daha düşük öncelik sırasına sahip içerikten daha duyarlı içeriği tanımladığından, bu durum bir güvenlik sorunu olabilir.

Eylem engellenmese de denetlenip varsayılan olarak belgeyi karşıya yükleyen kişiye ve site yöneticisine otomatik olarak bir e-posta oluşturur. Sonuç olarak, hem kullanıcı hem de yöneticiler etiket önceliğini yanlış hizalayan belgeleri tanımlayabilir ve gerekirse eylem gerçekleştirebilir. Örneğin, karşıya yüklenen belgeyi siteden silin veya taşıyın.

Belgenin, siteye uygulanan duyarlılık etiketinden daha düşük öncelikli duyarlılık etiketine sahip olması güvenlikle ilgili bir sorun oluşturmaz. Örneğin, **Genel** etiketli bir belge **Gizli** etiketli bir siteye yüklenir. Bu senaryoda, bir denetim olayı ve e-posta oluşturulmaz.

> [!NOTE]
> Kullanıcıların etiketi daha düşük bir sınıflandırmaya değiştirmek için gerekçe sağlamasını gerektiren ilke seçeneğinde olduğu gibi, aynı üst etikete ait alt etiketlerin de aynı önceliğe sahip olduğu kabul edilir.

Bu olayın denetim günlüğünde arama yapmak için **Dosya ve sayfa etkinlikleri** kategorisinde **Algılanan belge duyarlılığı uyuşmazlığı'nı** arayın.

Otomatik olarak oluşturulan e-postada konu **Uyumsuz duyarlılık etiketi algılandı** ve e-posta iletisinde, karşıya yüklenen belge ve sitenin bağlantısıyla etiketleme uyuşmazlığı açıklanmaktadır. Ayrıca, kullanıcıların duyarlılık etiketini nasıl değiştirebileceğini açıklayan bir belge bağlantısı içerir. Bu otomatik e-postalar özelleştirilemez, ancak [Set-SPOTenant'tan](/powershell/module/sharepoint-online/set-spotenant) aşağıdaki PowerShell komutunu kullandığınızda bunların gönderilmesini engelleyebilirsiniz:

```PowerShell
Set-SPOTenant -BlockSendLabelMismatchEmail $True
```

Birisi bir siteye veya gruba duyarlılık etiketi eklediğinde veya kaldırdığında, bu etkinlikler de denetlenir ancak otomatik olarak e-posta oluşturmaz.

Tüm bu denetim olayları [Duyarlılık etiketi etkinlikleri](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) kategorisinde bulunabilir. Denetim günlüğünde arama yapma yönergeleri için bkz [. Güvenlik & Uyumluluk Merkezi'nde denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.

## <a name="how-to-disable-sensitivity-labels-for-containers"></a>Kapsayıcılar için duyarlılık etiketlerini devre dışı bırakma

[PowerShell'de duyarlılık etiketi desteğini etkinleştirme](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell) başlığı altında yer alan yönergeleri kullanarak Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri için duyarlılık etiketlerini kapatabilirsiniz. Ancak, özelliği devre dışı bırakmak için 5. adımda öğesini belirtin `$setting["EnableMIPLabels"] = "False"`.

Duyarlılık etiketleri oluşturduğunuzda veya düzenlediğinizde tüm ayarları gruplar ve siteler için kullanılamaz hale getirmenin yanı sıra, bu eylem kapsayıcıların yapılandırması için hangi özelliği kullandığını geri alır. Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri için duyarlılık etiketlerini etkinleştirmek, kullanılan özelliği **Sınıflandırmadan** ([Azure AD grup sınıflandırması](#classic-azure-ad-group-classification) için kullanılır) **Duyarlılık'a** değiştirir. Kapsayıcılar için duyarlılık etiketlerini devre dışı bırakırsanız kapsayıcılar Duyarlılık özelliğini yoksayar ve Sınıflandırma özelliğini yeniden kullanır.

Bu, daha önce kapsayıcılara uygulanan sitelerden ve gruplardan gelen etiket ayarlarının zorunlu tutulmayacağı ve kapsayıcıların artık etiketleri görüntülemeyacağı anlamına gelir.

Bu kapsayıcılara Azure AD sınıflandırma değerleri uygulanmışsa, kapsayıcılar sınıflandırmaları yeniden kullanmaya geri döner. Özelliği etkinleştirdikten sonra oluşturulan yeni sitelerin veya grupların etiket görüntülemeyeceğini veya sınıflandırmaya sahip olmadığını unutmayın. Bu kapsayıcılar ve yeni kapsayıcılar için artık sınıflandırma değerleri uygulayabilirsiniz. Daha fazla bilgi için bkz. [SharePoint "modern" site sınıflandırması](/sharepoint/dev/solution-guidance/modern-experience-site-classification) ve [Kuruluşunuzdaki Office grupları için sınıflandırmalar oluşturma](../enterprise/manage-microsoft-365-groups-with-powershell.md).

## <a name="additional-resources"></a>Ek kaynaklar

[Microsoft Teams, O365 Grupları ve SharePoint Online siteleriyle Duyarlılık etiketlerini kullanma ile](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380) ilgili web semineri kaydına ve yanıtlanmış sorulara bakın.

Bu web semineri, özellik önizleme aşamasındayken kaydedilmiştir, bu nedenle kullanıcı arabiriminde bazı tutarsızlıklar fark edebilirsiniz. Ancak bu özelliğin bilgileri, bu sayfada belgelenen tüm yeni özelliklerle doğru olmaya devam eder.

Teams bağlantılı siteleri ve kanal sitelerini yönetme hakkında daha fazla bilgi için bkz. [Teams bağlı sitelerini ve kanal sitelerini yönetme](/SharePoint/teams-connected-sites).
