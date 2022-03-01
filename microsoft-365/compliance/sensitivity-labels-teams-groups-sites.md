---
title: Site oluşturma, Microsoft Teams grupları Microsoft 365 duyarlılık SharePoint kullanma
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
search.appverid:
- MOE150
- MET150
description: Farklı sitelerde ve farklı gruplarda yer alan SharePoint Microsoft Teams korumak için duyarlılık Microsoft 365 kullanın.
ms.openlocfilehash: d7d5ae1dfea2179c698922c4ddb045de0cd20ce5
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014365"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Aynı sitelerde, gruplarda ve Microsoft Teams sitelerde Microsoft 365 için duyarlılık SharePoint kullanma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Belgeleri ve e-postaları sınıflandırmak ve korumak için duyarlılık etiketleri kullanmanın yanı sıra, içeriği şu kapsayıcılarda korumak için de duyarlılık etiketlerini kullanabilirsiniz: Microsoft Teams siteleri, Microsoft 365 grupları (eski adı [Office 365 grupları](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) ve diğer SharePoint.[](sensitivity-labels.md) Bu kapsayıcı düzeyinde sınıflandırma ve koruma için aşağıdaki etiket ayarlarını kullanın:

- Ekip sitelerinin ve özel grupların gizliliği (genel Microsoft 365)
- Dış kullanıcı erişimi
- Sitelerden dış SharePoint paylaşma
- Unmanaged cihazlarından erişim
- Kimlik doğrulama bağlamları (önizlemede)
- SharePoint sitesi için varsayılan paylaşım bağlantısı (yalnızca PowerShell yapılandırması)

> [!IMPORTANT]
> Kuralın belirlenemeyen cihaz ayarları ve kimlik doğrulama bağlamları, Koşullu Erişim'Azure Active Directory birlikte çalışır. Bu ayarlar için bir duyarlılık etiketi kullanmak istemeniz gerekirse, bu bağımlı özelliği yapılandırabilirsiniz. Aşağıdaki yönergelere ek bilgiler dahil edilir.

Bu duyarlılık etiketini desteklenen bir kapsayıcıya uygularken, etiket sınıflandırma ve yapılandırılmış koruma ayarlarını site veya gruba otomatik olarak uygular.

Öte yandan bu kapsayıcıların içeriği, görsel işaretler ve şifreleme gibi dosyaların ve e-postaların sınıflandırma veya ayarlarının etiketlerini devralmaz. Kullanıcıların belgelerini SharePoint sitelerinde veya ekip sitelerinde etiketleysin diye, SharePoint ve Office dosyaları için duyarlılık etiketlerini [etkinleştirmiş OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

> [!NOTE]
> Kapsayıcılar için duyarlılık etiketleri İçerik Teslim Ağlarında (CDN Office 365 desteklenmiyor.

## <a name="using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Daha fazla site için Microsoft Teams, Microsoft 365 ve sitelerde duyarlılık SharePoint kullanma

Kapsayıcılar için duyarlılık etiketlerini etkinleştirmeden ve yeni ayarlar için duyarlılık etiketlerini yapılandırmadan önce, kullanıcılar uygulamalarına duyarlılık etiketlerini görebilir ve uygulayabilirler. Örneğin, Word'den:

![Word masaüstü uygulamasında görüntülenen bir duyarlılık etiketi.](../media/sensitivity-label-word.png)

Kapsayıcılar için duyarlılık etiketlerini etkinleştirdikten ve yapılandırdikten sonra, kullanıcılar bunlara ek olarak Microsoft ekip sitelerine, site gruplarına ve sitelere duyarlılık Microsoft 365 ve SharePoint uygulayabilirler. Örneğin, ekip sitesinden yeni bir ekip sitesi SharePoint:

![Ekip sitesinden ekip sitesi oluştururken bir duyarlılık SharePoint.](../media/sensitivity-labels-new-team-site.png)

## <a name="how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels"></a>Kapsayıcılar için duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme

Kapsayıcılar için duyarlılık etiketlerini henüz etkinleştirmediyseniz, tek seferlik bir yordam olarak aşağıdaki adım kümelerini uygulayın:

1. Bu özellik Azure AD [işlevini](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels) kullandığından, duyarlılık etiketi desteğini etkinleştirmek için Azure AD belgelerinde verilen yönergeleri izleyin: Duyarlılık etiketleri Microsoft 365 gruplarına Azure Active Directory.

2. Artık duyarlılık etiketlerinizi Azure AD'ye eşitlemeniz gerekiyor. İlk olarak, [Güvenlik ve Uyumluluk & PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Örneğin, yönetici olarak çalıştırdınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın.

3. Ardından, duyarlılık etiketlerinizin farklı gruplarda kullanılabilir olduğundan emin olmak için Microsoft 365 çalıştırın:

    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-groups-and-site-settings"></a>Grupları ve site ayarlarını yapılandırma

Duyarlılık etiketleri önceki bölümde açıklandığı gibi kapsayıcılar için etkinleştirildikten sonra, duyarlılık etiketleme yapılandırmasında gruplar ve siteler için koruma ayarlarını yapılandırabilirsiniz. Duyarlılık etiketleri kapsayıcılar için etkinleştirilinceye kadar, ayarlar görünür ancak yapılandıramaz.

1. Duyarlılık etiketi oluşturmak veya [düzenlemek için genel](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) yönergeleri izleyin ve etiketin kapsamı için Gruplar **& grupları'nın** seçili olduğundan emin olun: 
    
    ![Dosyalar ve e-postalar için duyarlılık etiketi kapsamı seçenekleri.](../media/groupsandsites-scope-options-sensitivity-label.png)
    
    Etiket için yalnızca bu kapsam seçildiğinde, etiket duyarlılık etiketlerini destekleyen Office ve dosyalarla e-postalara uygulanmayacak şekilde Office uygulamalarda görüntülenmez. Bu etiket ayrımını eklemek hem kullanıcılar hem de yöneticiler için yararlı olabilir, ancak etiket dağıtımının karmaşıklığını da ekleyebilir.
    
    Örneğin, etiketli bir belge etiketli bir [](sensitivity-labels.md#label-priority-order-matters) siteye SharePoint olduğunu algılayama nedeniyle etiket sıralamanızı dikkatle gözden geçirmeniz gerekiyor. Bu senaryoda, belgenin sitenin etiketinden daha yüksek öncelikli bir duyarlılık etiketi olduğunda denetim olayı ve e-posta otomatik olarak oluşturulur. Daha fazla bilgi için bu [sayfanın Denetim duyarlılığı etiket etkinlikleri](#auditing-sensitivity-label-activities) bölümüne bakın. 

2. Ardından, Gruplar **ve siteler için koruma ayarlarını tanımla** sayfasında, kullanılabilir seçeneklerden birini veya her ikisini de seçin:
    
    - **Gizlilik ve Dış kullanıcılar erişim ayarlarını** yapılandırmak için **gizlilik ve** **dış kullanıcı erişimi** ayarları. 
    - **Dış paylaşım ve Koşullu Erişim** ayarları, belirli sitelerde etiketli sitelerde dış **paylaşımı SharePoint** ve Site ayarlarıyla etiketlenmiş şekilde korumak için **Azure AD Koşullu SharePoint** kullanın.

3. Gizlilik ve **dış kullanıcı erişimi ayarlarını seçtiysanız**, şimdi aşağıdaki ayarları yapılandırabilirsiniz:
    
    - **Gizlilik**: Kuruluşta herkesin **bu** etiketin uygulandığı ekip sitesine veya gruba erişmesi için varsayılan olarak Genel'i kullanın.
        
        **Erişime** yalnızca organizasyonda onaylanmış üyelerle kısıtlanıyorsa Özel'i seçin.
        
        **Kapsayıcıda** içeriği duyarlılık etiketini kullanarak korumak ancak yine de kullanıcıların gizlilik ayarını kendilerini yapılandırmalarına izin ver seçeneğine sahip olmak için Yok'a seçin.
        
        Ortak veya **Özel** **ayarının ayarları** ve bu etiketi kapsayıcıya uygulayan gizlilik ayarını kilitler. Seçtiğiniz ayar, ekip veya grup için yapılandırılan önceki gizlilik ayarının yerini değiştirir ve gizlilik değerini kilitler; böylelikle önce duyarlılık etiketini kapsayıcıdan kaldırarak bunu değiştirebilirsiniz. Duyarlılık etiketini kaldırdikten sonra, etiketten gelen gizlilik ayarı kalır ve kullanıcılar artık bu ayarı yeniden değiştirebilir.
    
    - **Dış kullanıcı erişimi**: Grup sahibinin gruba konuk [ekp eklemey denetleme.](/office365/admin/create-groups/manage-guest-access-in-groups)

4. Dış paylaşım ve **Koşullu Erişim ayarlarını seçtiysanız**, şimdi aşağıdaki ayarları yapılandırabilirsiniz:
    
    - **Belirli sitelerden dış SharePoint denetimi**: Herkes, yeni ve var olan konuklar, var olan konuklar veya yalnızca kuruluşta yer alan kişiler için dış paylaşımı seçmek için bu seçeneği belirleyin. Bu yapılandırma ve ayarlar hakkında daha fazla bilgi için, aşağıdaki SharePoint [bkz. Site için dış paylaşımı açma veya kapatma](/sharepoint/change-external-sharing-site).
    
    - **Etki alanlarıyla etiketlenmiş siteleri korumak için Azure AD koşullu SharePoint kullanın**: Bu seçeneği yalnızca, kuruluş yapılandırılmışsa ve Koşullu Erişim Azure Active Directory [kullanıyorsa belirleyin](/azure/active-directory/conditional-access/overview). Daha sonra aşağıdaki ayarlardan birini seçin:
    
        - **Kullanıcıların,** SharePoint olmayan cihazlardan SharePoint sitelerine erişip erişeyemeyenleri belirleme: Bu seçenek, SharePoint ve OneDrive içeriğine erişimi engellemek veya sınırlamak için Azure AD Koşullu Erişimi kullanan SharePoint özelliğini kullanır. Daha fazla bilgi için [bkz. Aşağıdaki belgelere bakarak, kontrol SharePoint](/sharepoint/control-access-from-unmanaged-devices). Bu etiket ayarı için belirttiğiniz seçenek, site için PowerShell komutunu çalıştırmayla eşdeğerdir. Bu komutun yönergelerinde, Erişimi engelleme veya sınırlandırma bölümündeki 3-5 SharePoint sitesi veya [OneDrive](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive) bölümüne SharePoint.
            
            Ek yapılandırma bilgileri için, [bu bölümün sonundaki Unmanaged devices seçeneğine](#more-information-about-the-dependencies-for-the-unmanaged-devices-option) bağımlılıklar hakkında daha fazla bilgi bölümüne bakın.
            
        - **Var olan kimlik doğrulama bağlamını** seçme: Şu anda önizlemede olan bu seçenek, kullanıcılar bu etiketin uygulandığı sitelere erişene SharePoint daha sıkı erişim koşulları zorunlu kılınmanıza olanak sağlar. Bu koşullar, kuruluşun Koşullu Erişim dağıtımı için oluşturulmuş ve yayımlanmış var olan bir kimlik doğrulama bağlamını seçmeniz sırasında uygulanır. Kullanıcılar yapılandırılmış koşulları karşılamazsa veya kimlik doğrulama bağlamlarını desteklemezse, erişimleri reddedilir.
            
            Ek yapılandırma bilgileri için, [bu bölümün sonundaki Kimlik doğrulama bağlam seçeneğine bağımlılıklar](#more-information-about-the-dependencies-for-the-authentication-context-option) hakkında daha fazla bilgi bölümüne bakın.
            
            Bu etiket yapılandırmasına örnekler:
            
             - Çok faktörlü kimlik doğrulaması [(MFA) gerektirecek şekilde yapılandırılmış bir kimlik doğrulama bağlamı seçersiniz](/azure/active-directory/conditional-access/untrusted-networks). Bu etiket daha sonra çok gizli SharePoint içeren bir site sitesine uygulanır. Sonuç olarak, güvenilmeyen bir ağdan gelen kullanıcılar bu siteden bir belgeye erişmeye çalışırken, belgeye erişmek için önce tamamlamaları gereken MFA istemini görebilirler.
             
             - Kullanım koşulları [(ToU) ilkeleri için yapılandırılmış bir kimlik doğrulama bağlamı seçersiniz](/azure/active-directory/conditional-access/terms-of-use). Bu etiket daha sonra, SharePoint veya uyumluluk nedenleriyle kullanım kabulünü gerektiren öğelerin yer almalı olduğu web sitelerine uygulanır. Sonuç olarak, kullanıcılar bu siteden bir belgeye erişmeye çalışırken, özgün belgeye erişmek için önce kabul etmeleri gereken bir kullanım belgesi koşulları görüyorlar.

> [!IMPORTANT]
> Etiketi bir ekip, grup veya siteye uygulayan yalnızca bu site ve grup ayarları geçerli olur. Etiketin [kapsamı dosyalar ve](sensitivity-labels.md#label-scopes) e-postalar içerirse, şifreleme ve içerik işaretleme gibi diğer etiket ayarları ekip, grup veya site içindeki içeriğe uygulanmaz.

Duyarlılık etiketiniz daha önce yayımlanmış değilse, şimdi bunu bir [duyarlılık etiketi ilkesine ekleyerek yayımlayın](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy). Bu etiketi içeren bir duyarlılık etiketi ilkesi atanan kullanıcılar site ve gruplar için bu ilkeyi seçecek.

##### <a name="more-information-about-the-dependencies-for-the-unmanaged-devices-option"></a>Unmanaged devices option için bağımlılıklar hakkında daha fazla bilgi

Zorunlu kısıtlamaları kullanma altında belirtilen şekilde SharePoint koşullu erişim ilkesi yapılandırmazsanız[, burada](/sharepoint/app-enforced-restrictions) belirttiğiniz seçeneğin hiçbir etkisi olmaz. Buna ek olarak, kiracı düzeyinde yapılandırılmış bir ayara göre daha az kısıtlayıcı olursa, hiçbir etkisi olmaz. Kurum genelindeki bir ayarı, aynı veya daha kısıtlayıcı olan bir cihaz için yapılandırdınız

Örneğin, kiracınız Sınırlı **, yalnızca web** erişimine izin ver için yapılandırılmışsa, tam erişime izin veren etiket ayarının hiçbir etkisi olmaz çünkü daha az kısıtlayıcıdır. Bu kiracı düzeyi ayarı için, erişimi engelecek etiket ayarını (daha kısıtlayıcı) veya sınırlı erişim için etiket ayarını (kiracı ayarıyla aynı) seçin.

Kimlik ayarlarını etiket SharePoint ayrı yapılandırasınız, çünkü bağımlılıkların var olduğu duyarlılık etiketi yapılandırmasını denetlemez. Bu bağımlılıklar, etiket oluşturulduktan ve yayımlandıktan sonra, etiket uygulandıktan sonra bile yalıtıldı. Bununla birlikte, etiket zaten uygulandıktan sonra kullanıcı bir sonraki kimlik doğrulaması yapılana kadar etiket ayarı etkili olmaz.

##### <a name="more-information-about-the-dependencies-for-the-authentication-context-option"></a>Kimlik doğrulama bağlam seçeneğine bağımlılıklar hakkında daha fazla bilgi

Seçim için açılan listede görüntülenmek üzere, kimlik doğrulama bağlamlarının Erişim Koşulu yapılandırmanız kapsamında oluşturularak, yapılandırıldığında ve Azure Active Directory gerekir. Daha fazla bilgi ve yönergeler için Azure AD [Koşullu Erişim belgelerinden](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts) Kimlik doğrulama bağlamlarını yapılandırma bölümüne bakın.

Tüm uygulamalar kimlik doğrulama bağlamlarını desteklemez. Desteklenmeyen uygulamaya sahip bir kullanıcı, kimlik doğrulama bağlamı için yapılandırılmış siteye bağlanırsa, erişim reddedildi iletisiyle veya kimlik doğrulaması istenir ancak reddedilir. Şu anda kimlik doğrulama bağlamlarını destekleyen uygulamalar:

- Web için Office Web için Outlook içeren web sitesi

- Microsoft Teams macOS Windows için web sayfaları (web Teams hariç)

- Microsoft Planner

- Microsoft 365 Uygulamaları, word, Excel ve PowerPoint sürümleri için sürüm:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 2.48.303
    - Android: 16.0.13924.10000

- Microsoft 365 Uygulamaları için Outlook; en düşük sürümler:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 4.2109.0
    - Android: 4.2025.1

- OneDrive eşitleme uygulama, minimum sürümler:
    - Windows: 21.002
    - macOS: 21.002
    - iOS: 12.30'da geliyor
    - Android: Henüz desteklenmiyor

Bu önizlemenin bilinen sınırlamaları:

- Yalnızca OneDrive eşitleme için desteklenen uygulama, OneDrive siteler için değil.

- Aşağıdaki özellikler ve uygulamalar kimlik doğrulama bağlamları ile uyumsuz olabilir, bu nedenle kullanıcı kimlik doğrulama bağlamı kullanarak siteye başarıyla erişdikten sonra bunların çalışmaya devam edeceğini denetlemeniz teşvik edilir:
    
    - Power Apps veya Power Automate
    - Üçüncü taraf uygulamalar

### <a name="configure-settings-for-the-default-sharing-link-for-a-site-by-using-powershell-advanced-settings"></a>PowerShell gelişmiş ayarlarını kullanarak bir sitenin varsayılan paylaşım bağlantısının ayarlarını yapılandırma

Uyumluluk merkezinden yapılandırabilirsiniz sitelerin ve grupların etiket ayarlarına ek olarak, site için varsayılan paylaşım bağlantı türünü ve paylaşım bağlantısı izinlerini de yapılandırabilirsiniz.

Bu ayarların nasıl olduğu hakkında daha fazla bilgi edinmek için [bkz. Site için varsayılan bağlantı türünü değiştirme](/sharepoint/change-default-sharing-link).

Paylaşım bağlantısı için bu ek etiket ayarları şu anda yalnızca PowerShell *AdvancedSettings* parametresi olarak ve Güvenlik ve Uyumluluk Merkezi [PowerShell'den](/powershell/exchange/scc-powershell) [Set-Label](/powershell/module/exchange/set-label) ve [New-Label](/powershell/module/exchange/new-labelpolicy) cmdlet'leri & kullanılabilir:

- **DefaultSharingScope**: Kullanılabilir değerler:
    - **SpecificPeople**: Sitenin varsayılan paylaşım bağlantısını "Belirli kişiler" bağlantısına ayarlar
    - **Kuruluş**: Sitenin varsayılan paylaşım bağlantısını "kuruluş" bağlantısına veya şirket paylaşılabilir bağlantısına ayarlar
    - **Herkes**: Sitenin varsayılan paylaşım bağlantısını Anonim Erişim veya Herkes bağlantısına ayarlar

- **DefaultShareLinkPermission**: Kullanılabilir değerler:
    - **Görüntüleme**: Sitenin varsayılan bağlantı iznini "görüntüleme" izinlerine ayarlar
    - **Düzenle**: Sitenin varsayılan bağlantı iznini "düzenleme" izinlerine ayarlar

Bu iki ayar ve değer, [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) cmdlet'inden *DefaultSharingScope* ve *DefaultShareLinkPermission* parametrelerinin eşdeğeridir.

Duyarlılık etiketi GUID'nin **8faca7b8-8d20-48a3-8ea2-0f96310a848e** olduğu PowerShell örnekleri:

- Paylaşım bağlantı türünü SpecificPeople olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Paylaşım bağlantısı izinlerini Düzenle olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

#### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Gelişmiş ayarları belirtmek için PowerShell ipuçları

Duyarlılık etiketini adına göre belirtesiniz, ancak etiket adını veya görünen adı belirtme konusunda olası karışıklıkları önlemek için etiket GUID'sini kullanmayı öneririz. GUID'i bulmak için:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
````

Bu gelişmiş ayarlardan birini duyarlılık etiketinden kaldırmak için aynı AdvancedSettings parametre söz dizimini kullanın, ancak bir null dize değeri belirtin. Örneğin:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

## <a name="sensitivity-label-management"></a>Duyarlılık etiketi yönetimi

Siteler ve gruplar için yapılandırılmış duyarlılık etiketleri oluşturmak, değiştirmek veya silmek için aşağıdaki kılavuzu kullanın.

### <a name="creating-and-publishing-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış etiketler oluşturma ve yayımlama

Yeni bir duyarlılık etiketi oluşturulduğunda ve yayımlanır ve bir saat içinde ekip, grup ve sitelerde kullanıcılar tarafından görülebilir. Bununla birlikte, mevcut bir etiketi değiştirirsanız, 24 saate kadar izin kullanın. Site ve grup ayarları için yapılandırılan etiket kullanıcılarınız için bir etiket yayımlamak üzere aşağıdaki kılavuzu kullanın:

1. Duyarlılık etiketini oluşturduktan ve yapılandırdikten sonra, yalnızca birkaç test kullanıcısına uygulanan bir etiket ilkesine bu etiketi ekleyin.

2. Değişikliğin çoğaltılması için bekleyin:

   - Yeni etiket: Bir saat bekleyin.
   - Mevcut etiket: 24 saat bekleyin.

3. Bu bekleme süresinde, 1. adımda oluşturduğunuz etiketle bir ekip, Microsoft 365 grubu veya SharePoint sitesi oluşturmak için test kullanıcı hesaplarından birini kullanın.

4. Bu oluşturma işlemi sırasında hata yoksa, etiketi kiracılı tüm kullanıcılara yayımlamanın güvenli olduğunu bilirsiniz.

### <a name="modifying-published-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış olarak yayımlanan etiketleri değiştirme

En iyi yöntem olarak, etiket ekiplere, gruplara veya sitelere uygulandıktan sonra bir duyarlılık etiketi için site ve grup ayarlarını değiştirmezsiniz. Bunu yapmak için, değişikliklerin etiket uygulanmış olan tüm kapsayıcılara çoğaltılması için 24 saat beklemeyi unutmayın.

Buna ek olarak, değişiklikleriniz Dış **kullanıcılara erişim ayarını da içerecekse** :

- Yeni ayar yeni kullanıcılar için geçerlidir, ancak var olan kullanıcılar için geçerli değildir. Örneğin, bu ayar daha önce seçilmişse ve bunun sonucunda konuk kullanıcılar siteye erişmişse, etiket yapılandırmasında bu ayar temizlendikten sonra bu konuk kullanıcılar siteye yine de erişebilirsiniz.

- Grup özellikleri gizliMembership ve roleEnabled ile ilgili gizlilik ayarları güncelleştirilmez.

### <a name="deleting-published-labels-that-are-configured-for-sites-and-groups"></a>Siteler ve gruplar için yapılandırılmış yayımlanmış etiketleri silme

Site ve grup ayarlarının etkin olduğu bir duyarlılık etiketini siler ve bu etiket bir veya birden çok etiket ilkelerine dahil edilirse, bu eylem yeni ekipler, gruplar ve siteler için oluşturma hataları oluşturulmasına yol açabilir. Bu durumdan kaçınmak için aşağıdaki kılavuzu kullanın:

1. Duyarlılık etiketini, etiketin olduğu tüm etiket ilkelerinden kaldırın.

2. Bir saat bekleyin.

3. Bu bekleme süresinden sonra bir ekip, grup veya site oluşturmayı deneyin ve etiketin artık görünür olmadığını onaylayın.

4. Duyarlılık etiketi görünür durumda değilse artık etiketi güvenle silebilirsiniz.

## <a name="how-to-apply-sensitivity-labels-to-containers"></a>Duyarlılık etiketleri kapsayıcılara nasıl uygulanır

Artık duyarlılık etiketini veya etiketlerini aşağıdaki kapsayıcılara uygulayabilirsiniz:

- [Microsoft 365 Ad'de Grup Grubu](#apply-sensitivity-labels-to-microsoft-365-groups)
- [Microsoft Teams sitesini ziyaret edin](#apply-a-sensitivity-label-to-a-new-team)
- [Microsoft 365'da grup Web üzerinde Outlook](#apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web)
- [SharePoint sitesi](#apply-a-sensitivity-label-to-a-new-site)

Birden çok siteye duyarlılık etiketi [uygulamaniz gerekirse PowerShell'i kullanabilirsiniz](#use-powershell-to-apply-a-sensitivity-label-to-multiple-sites).

### <a name="apply-sensitivity-labels-to-microsoft-365-groups"></a>Gruplara duyarlılık Microsoft 365 uygulama

Artık duyarlılık etiketini veya etiketlerini gruplara veya gruplara Microsoft 365 hazır mısınız? Yönergeler için Azure AD belgelerine geri dönme:

- [Azure portalda yeni bir gruba etiket atama](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

- [Azure portalda mevcut bir gruba etiket atama](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

- [Azure portalda var olan bir gruptan etiket kaldırın](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

### <a name="apply-a-sensitivity-label-to-a-new-team"></a>Yeni bir ekipe duyarlılık etiketi uygulama

Kullanıcılar, ekiplerde yeni ekipler oluşturduklarında duyarlılık Microsoft Teams. Duyarlılık açılan listesinden etiket **seçenler** , gizlilik ayarı etiket yapılandırmasını yansıtacak şekilde değişebilir. Dış kullanıcıların etiket için seçtiğiniz erişim ayarına bağlı olarak, kullanıcılar kuruluş dışından kişi ek bilgilere ek bilgilere sahip olabilir veya ekynek eknez.

[E-Teams için duyarlılık etiketleri hakkında daha fazla Teams](/microsoftteams/sensitivity-labels)

![Yeni ekip oluştururken gizlilik ayarı.](../media/privacy-setting-new-team.png)

Ekibi oluşturduktan sonra duyarlılık etiketi tüm kanalların sağ üst köşesinde görünür.

![Duyarlılık etiketi ekipte görünür.](../media/privacy-setting-teams.png)

Hizmet aynı duyarlılık etiketini ekip grubuna ve ekip sitesine Microsoft 365 şekilde SharePoint uygular.

### <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Yeni bir gruba duyarlılık etiketi Web üzerinde Outlook

İçerik Web üzerinde Outlook yeni bir grup sanız, yayımlanan etiketler için **Duyarlılık seçeneğini belirtin** veya değiştirebilirsiniz:

![Grup oluşturma ve Duyarlılık'ın altında bir seçenek seçme.](../media/sensitivity-label-new-group.png)

### <a name="apply-a-sensitivity-label-to-a-new-site"></a>Yeni bir siteye duyarlılık etiketi uygulama

Yöneticiler ve son kullanıcılar modern ekip siteleri ve iletişim siteleri oluşturduklarında duyarlılık etiketlerini seçerek [Gelişmiş](/sharepoint/create-site-collection) **ayarlar'ı genişleter**:

![Site oluşturma ve Duyarlılık'ın altında bir seçenek seçme.](../media/sensitivity-label-new-communication-site.png)

Açılan kutuda seçimin etiket adları görüntülenir ve yardım simgesi, kullanıcıların uygulanacak doğru etiketi belirlemesine yardımcı olan araç ipucuyla birlikte tüm etiket adlarını görüntüler.

Etiket uygulandığında ve kullanıcılar siteye göz atarak etiketin adını ve uygulanan ilkeleri görebilir. Örneğin, bu site Gizli olarak **etiketlenmiş** ve gizlilik ayarı Özel olarak **ayarlanmıştır**:

![Duyarlılık etiketi uygulanmış bir site.](../media/sensitivity-label-site.png)

### <a name="use-powershell-to-apply-a-sensitivity-label-to-multiple-sites"></a>Birden çok siteye duyarlılık etiketi uygulamak için PowerShell kullanma

Birçok siteye duyarlılık etiketi uygulamak için [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) ve [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini geçerli [SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) Yönetim Kabuğu'nun *sensitivityLabel* parametresiyle kullanabilirsiniz. Siteler herhangi bir SharePoint site koleksiyonu veya OneDrive olabilir.

SharePoint Online Yönetim Kabuğu'nın 16.0.19418.12000 veya sonraki bir sürümünün yüklü olduğundan emin olun.

1. Yönetici Olarak Çalıştır seçeneğini kullanarak bir PowerShell **oturumu** açın.

2. Etiketinizin GUID'sini [bilmiyorsanız: güvenlik Bağlan Uyumluluk & PowerShell'e](/powershell/exchange/connect-to-scc-powershell) yönlendirin ve duyarlılık etiketleriyle GUID'lerinin listesini elde edin.

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Şimdi [SharePoint Online PowerShell'e](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) bağlanın ve etiket GUID'nizi değişken olarak depolar. Örneğin:

   ```powershell
   $Id = [GUID]("e48058ea-98e8-4940-8db0-ba1310fd955e")
   ```

4. URL'lerinde tanımlayıcı dizenin ortak olduğu birden çok siteyi tanımlayan yeni bir değişken oluşturun. Örneğin:

   ```powershell
   $sites = Get-SPOSite -IncludePersonalSite $true -Limit all -Filter "Url -like 'documents"
   ```

5. Etiketi bu sitelere uygulamak için aşağıdaki komutu çalıştırın. Örneklerimizi kullanarak:

   ```powershell
   $sites | ForEach-Object {Set-SPOTenant $_.url -SensitivityLabel $Id}
   ```

Bu komut dizisi kiracınız genelinde birden çok siteyi aynı duyarlılık etiketiyle etiketlemenize olanak sağlar ve bu nedenle site başına yapılandırmaya uygun Set-SPOTenant cmdlet'ini değil Set-SPOSite cmdlet'ini kullanırsınız. Bununla birlikte, Set-SPOSite sitelerin her biri için aşağıdaki komutu yinelayarak belirli sitelere farklı bir etiket uygulamaniz gerekirken Set-SPOSite cmdlet'ini kullanın: `Set-SPOSite -Identity <URL> -SensitivityLabel "<labelguid>"`

## <a name="view-and-manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>Duyarlılık etiketlerini yönetim merkezinde görüntüleme SharePoint yönetme

Uygulanan duyarlılık etiketlerini görüntülemek, sıralamak ve aramak için yeni Yönetim **Merkezi'nde** bulunan Etkin siteler SharePoint kullanın. Önce Duyarlılık sütununu **eklemeniz** gerekiyor olabilir:

![Etkin siteler sayfasında duyarlılık sütunu.](../media/manage-site-sensitivity-labels.png)

Etkin siteler sayfasından siteleri yönetme hakkında daha fazla bilgi ve sütun ekleme hakkında daha fazla bilgi için bkz. Yeni Yönetim [Merkezi'nde SharePoint yönetme](/sharepoint/manage-sites-in-new-admin-center).

Ayrıca, bu sayfadan bir etiket değiştirebilir ve uygulayabilirsiniz:

1. Ayrıntılar bölmesini açmak için site adını seçin.

2. **İlkeler** sekmesini ve ardından Duyarlılık **ayarı** için **Düzenle'yi** seçin.

3. Duyarlılık **ayarını düzenle bölmesinde** siteye uygulamak istediğiniz duyarlılık etiketini seçin. Duyarlılık etiketlerinin belirli kullanıcılara atandığı kullanıcı uygulamalarının aksine yönetim merkezi kiracınız için tüm duyarlılık etiketlerini görüntüler. Bir etiket seçtikten sonra Kaydet'i **seçin**.

## <a name="support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteği

Duyarlılık etiketlerini destekleyen yönetim merkezleri kullanırken kiracınız için tüm duyarlılık etiketlerini görüyorsunuz. Karşılaştırmada, yayımlama ilkelerine göre duyarlılık etiketlerini filtreleyene kullanıcı uygulamaları ve hizmetler bu etiketlerin bir alt kümesini görmenizi neden olabilir.

Aşağıdaki uygulamalar ve hizmetler, siteler ve grup ayarları için yapılandırılmış duyarlılık etiketlerini destekler:

- Yönetim merkezleri:

  - SharePoint merkezi
  - Teams merkezi
  - Azure Active Directory portalı
  - Microsoft 365 yönetici merkezi
  - Microsoft 365 uyumluluk merkezi

- Kullanıcı uygulamaları ve hizmetleri:

  - SharePoint
  - Teams
  - Web üzerinde Outlook, macOS, Windows Android için ve
  - Formlar
  - Stream
  - Planner 

Aşağıdaki uygulama ve hizmetler şu anda siteler ve grup ayarları için yapılandırılmış duyarlılık etiketlerini desteklememektedir:

- Yönetim merkezleri:

  - Exchange merkezi

- Kullanıcı uygulamaları ve hizmetleri:

  - Dynamics 365
  - Yammer
  - Project
  - Power BI

## <a name="classic-azure-ad-group-classification"></a>Klasik Azure AD grup sınıflandırması

Kapsayıcılar için duyarlılık etiketlerini etkinleştirdikten sonra Azure AD'nin grup sınıflandırmaları artık Microsoft 365 tarafından destekleniyor ve duyarlılık etiketlerini destekleyen sitelerde görüntülenmez. Bununla birlikte, eski sınıflandırmalarınızı duyarlılık etiketlerine dönüştürabilirsiniz.

Eski grup sınıflandırmayı eski grup sınıflandırması olarak nasıl kullandıklarına bir örnek SharePoint[" site SharePoint sınıflandırmayı değerlendirmeye bakın](/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Bu sınıflandırmalar, Azure AD PowerShell veya PnP Core kitaplığı kullanılarak ve ayar için değerler tanımlayarak yapılandırılmıştır `ClassificationList` . Kiracınız sınıflandırma değerleri tanımlanmışsa, [AzureADPreview PowerShell modülünde aşağıdaki komutu çalıştırabilirsiniz](https://www.powershellgallery.com/packages/AzureADPreview):

```powershell
($setting["ClassificationList"])
```

Eski sınıflandırmalarınızı duyarlılık etiketlerine dönüştürmek için, birini yapın:

- Varolan etiketleri kullanma: Zaten yayımlanmış olan mevcut duyarlılık etiketlerini düzenleyerek siteler ve gruplar için istediğiniz etiket ayarlarını belirtin.

- Yeni etiket oluşturma: Var olan sınıflandırmalarla aynı adlara sahip yeni duyarlılık etiketleri oluşturarak ve yayımarak, siteler ve gruplar için istediğiniz etiket ayarlarını belirtin.

Ardından:

1. Mevcut kullanıcı gruplarına ve sitelere ad eşlemesi Microsoft 365 duyarlılık SharePoint için PowerShell kullanın. Yönergeler için sonraki bölüme bakın.

2. Mevcut grup ve sitelerden eski sınıflandırmaları kaldırın.

Kullanıcıların henüz duyarlılık etiketlerini desteklememiş uygulama ve hizmetlerde yeni gruplar oluşturmasını engelleyesiniz, ancak kullanıcıların eski sınıflandırmalarla oluşturduğu yeni grupları bakmak için yinelenen bir PowerShell betiği çalıştırabilirsiniz ve bunları duyarlılık etiketlerini kullanmak üzere dönüştürebilirsiniz.

Siteler ve gruplar için duyarlılık etiketlerinin ve Azure AD sınıflandırmalarının birlikte çıtalarını yönetmenize yardımcı olması için bkz. Azure Active Directory grupları için sınıflandırma ve [duyarlılık Microsoft 365 bkz](migrate-aad-classification-sensitivity-labels.md).

### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Farklı kullanıcı gruplarının sınıflandırmalarını duyarlılık etiketlerine Microsoft 365 için PowerShell kullanma

1. İlk olarak, [Güvenlik ve Uyumluluk & PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Örneğin, yönetici olarak çalıştırdınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın:

2. Get-Label cmdlet'ini kullanarak duyarlılık etiketlerinin ve [GUID'lerinin](/powershell/module/exchange/get-label) listesini elde edin:

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Kullanıcı gruplarınıza uygulamak istediğiniz duyarlılık etiketlerinin GUID'lerini Microsoft 365 kullanın.

4. Şimdi [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) ayrı bir Windows PowerShell bağlanın.

5. Şu anda "Genel" sınıflandırması olan grupların listesini almak için örnek olarak aşağıdaki komutu kullanın:

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Her grup için yeni duyarlılık etiketi GUID'lerini ekleyin. Örneğin:

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Kalan grup sınıflandırmaları için 5. ve 6. adımları yinelayın.

## <a name="auditing-sensitivity-label-activities"></a>Duyarlılık etiketi etkinliklerini denetleme

> [!IMPORTANT]
> Kapsayıcıları koruyan etiketler için yalnızca Gruplar & siteleri kapsamını seçerek etiket ayrımını kullanıyorsanız: Bu bölümde açıklanan Algılanan belge duyarlılığı  eşleşmesi denetim olayı ve e-posta nedeniyle, Dosyalar **&** e-postaları kapsamında olan etiketlerden [](sensitivity-labels.md#label-priority-order-matters) önce etiketlere sıralamayı göz önünde bulundurabilirsiniz **.** 

Birisi bir belgeyi duyarlılık etiketiyle korunan bir siteye yüklese ve belgesinde siteye uygulanan duyarlılık etiketinden daha yüksek öncelikli [](sensitivity-labels.md#label-priority-order-matters) bir duyarlılık etiketi varsa, bu eylem engellenmiş değildir. Örneğin, genel etiketini bir sitenin SharePoint  ve birisi bu siteye Gizli etiketli bir belge **yükledi**. Daha yüksek önceliğe sahip bir duyarlılık etiketi daha düşük öncelik sırasına sahip içerikten daha fazla duyarlılık olan içeriği tanım olduğundan, bu durum bir güvenlik sorunu olabilir.

Eylem engellenmiş olsa da, denetlenr ve varsayılan olarak, belgeyi karşıya yük eden kişiye ve site yöneticisine otomatik olarak bir e-posta oluşturulur. Sonuç olarak, hem kullanıcı hem de yöneticiler etiket önceliğini bu şekilde yanlış hizaya sahip olan belgeleri tanımlayabilir ve gerekirse harekete geçebilirsiniz. Örneğin, karşıya yüklenen belgeyi siteden silin veya taşıyın.

Belgenin siteye uygulanan duyarlılık etiketinden daha düşük öncelikli bir duyarlılık etiketi olması güvenlik sorununa neden olmaz. Örneğin, Genel etiketli bir **belge** Gizli etiketli bir siteye **karşıya karşıya yük olur**. Bu senaryoda, denetim olayı ve e-posta oluşturulmaz.

> [!NOTE]
> Aynı kullanıcıların bir etiketi daha düşük bir sınıflandırmaya düşürmek için gerekçe sağlamasını gerektiren ilke seçeneğinde olduğu gibi, aynı üst etiketin alt etiketlerinin de aynı önceliğe sahip olduğu kabul edilir.

Bu olayın denetim günlüğünde arama yapmak için, Dosya ve  sayfa etkinlikleri kategorisindeki Algılanan belge **duyarlılığı uygunluğu yok mu? hatalarına** bakın.

Otomatik olarak oluşturulan e-postada konu  Uyumlu olmayan duyarlılık etiketi algılandı ve e-posta iletisi, karşıya yüklenen belge ve sitenin bağlantısıyla etiket uyumsuzluğuna açıklama ekler. Ayrıca, kullanıcıların duyarlılık etiketini nasıl değiştir bağlantıya sahip olduğunu açıklayan bir belge bağlantısı da içerir. Bu otomatik e-postalar özelleştir kullanılamaz, ancak [Set-SPOTenant'ın aşağıdaki PowerShell komutunu kullanarak bu e-postaların gönderilmelerini önebilirsiniz](/powershell/module/sharepoint-online/set-spotenant):

```PowerShell
Set-SPOTenant -BlockSendLabelMismatchEmail $True
```

Birisi bir site veya gruptan duyarlılık etiketi eklesin veya kaldırıyorsa, bu etkinlikler de denetlenmektedir, ancak otomatik olarak bir e-posta oluşturmadan yapılır.

Tüm bu denetim olayları Duyarlılık etiketi [etkinlikleri kategorisinde](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) bulunabilir. Denetim günlüğünde arama yapmak için yönergeler için bkz. [Güvenlik ve Uyumluluk Merkezi'nde denetim & arama](search-the-audit-log-in-security-and-compliance.md).

## <a name="how-to-disable-sensitivity-labels-for-containers"></a>Kapsayıcılar için duyarlılık etiketlerini devre dışı bırakma

[PowerShell'de](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell) duyarlılık Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri için duyarlılık etiketlerini kapatabilirsiniz. Bununla birlikte, özelliği devre dışı bırakmak için 5. adımda bunu belirtin `$setting["EnableMIPLabels"] = "False"`.

Duyarlılık etiketleri  oluşturma veya düzenleme yaparken grup ve sitelerin tüm ayarlarını kullanılamaz duruma döndürmeye ek olarak, bu eylem kapsayıcıların yapılandırmasında hangi özelliği kullanabileceğinizi de geri getirir. Site siteleri, Microsoft Teams, Microsoft 365 için duyarlılık etiketlerinin etkinleştirilmesi, **sınıflandırma (**[Azure AD](#classic-azure-ad-group-classification) grup sınıflandırması için SharePoint) özelliğini Duyarlılık olarak **değiştirmektedir**. Kapsayıcılar için duyarlılık etiketlerini devre dışı bırakarak duyarlılık özelliğini yoksayın ve Sınıflandırma özelliğini yeniden kullanın.

Bu, daha önce kapsayıcılara uygulanmış olan site ve gruplardan gelen hiçbir etiket ayarlarının zorunlu kılınmayacak ve kapsayıcıların artık etiketleri görüntüleymeyecek olması anlamına gelir.

Bu kapsayıcılara Azure AD sınıflandırma değerleri uygulanmışsa, kapsayıcılar sınıflandırmaları yeniden kullanmaya döner. Özelliği etkinleştirdikten sonra oluşturulan yeni sitelerin veya grupların etiket veya sınıflandırması görüntülenmez. Bu kapsayıcılar ve her yeni kapsayıcı için artık sınıflandırma değerleri uygulayabilirsiniz. Daha fazla bilgi için bkz[. "modern" siteler](/sharepoint/dev/solution-guidance/modern-experience-site-classification) sınıflandırması SharePoint sınıflandırma ve Office [grupları için sınıflandırmalar oluşturma](../enterprise/manage-microsoft-365-groups-with-powershell.md).

## <a name="additional-resources"></a>Ek kaynaklar

Microsoft Teams, O365 Grupları ve SharePoint Online siteleriyle Webinar kaydına bakın ve Duyarlılık [etiketlerini kullanma SharePoint yanıtlandı](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380).

Bu web tarayıcısı, özellik hala önizlemede olduğunda kaydedilmiştir, dolayısıyla kullanıcı arabiriminde bazı farklılıklar fark etmişsinizdir. Bununla birlikte, bu sayfada belgelenmiş yeni özelliklere sahip bilgiler yine doğrudur.

Bağlı siteleri ve kanal sitelerini Teams hakkında daha fazla bilgi için bkz. Bağlı [siteleri Teams kanal sitelerini yönetme](/SharePoint/teams-connected-sites).
