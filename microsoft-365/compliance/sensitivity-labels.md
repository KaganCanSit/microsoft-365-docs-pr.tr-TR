---
title: Duyarlılık etiketleri hakkında bilgi edinin
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Hassas içeriği sınıflandırmak ve korumak için Microsoft Purview Information Protection duyarlılık etiketlerini kullanın.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 088e84c492fe142471799139743f29be32513206
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287210"
---
# <a name="learn-about-sensitivity-labels"></a>Duyarlılık etiketleri hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Office uygulamalarınızda gördüğünüz duyarlılık etiketleri hakkında bilgi arıyorsanız bkz. [Office'de dosyalarınıza ve e-postanıza duyarlılık etiketleri uygulama](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).
>
> Bu sayfadaki bilgiler, bu etiketleri oluşturabilen ve yapılandırabilen BT yöneticilerine yöneliktir.

Kuruluşunuzdaki kişiler işlerini yapmak için hem kuruluş içindeki hem de dışındaki kişilerle işbirliği yapabilir. Bu, içeriğin artık bir güvenlik duvarının arkasında kalmayabileceği anlamına gelir; cihazlar, uygulamalar ve hizmetler arasında her yerde gezinebilir. Dolaşımdayken, bunu kuruluşunuzun iş ve uyumluluk ilkelerine uygun güvenli ve korumalı bir şekilde gerçekleştirmesini istersiniz.

Microsoft Purview'un duyarlılık etiketleri Information Protection kuruluşunuzun verilerini sınıflandırmanıza ve korumanıza olanak tanırken, kullanıcı üretkenliğinin ve işbirliği yapma becerilerinin engellenmediğinden emin olmanıza olanak tanır.

şeritteki **Giriş** sekmesinden Excel kullanılabilir duyarlılık etiketlerini gösteren örnek. Bu örnekte, uygulanan etiket durum çubuğunda görüntülenir:

![Excel şeridinde ve durum çubuğunda duyarlılık etiketi.](../media/Sensitivity-label-in-Excel.png)

Duyarlılık etiketlerini uygulamak için kullanıcıların Microsoft 365 iş veya okul hesaplarıyla oturum açması gerekir.

> [!NOTE]
> ABD Kamu kiracıları için duyarlılık etiketleri tüm platformlar için desteklenir.
>
> Azure Information Protection birleşik etiketleme istemcisini ve tarayıcısını kullanıyorsanız bkz. [Azure Information Protection Premium Kamu Hizmeti Açıklaması](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Duyarlılık etiketlerini şu amaçlarla kullanabilirsiniz:
  
- **Şifreleme ve içerik işaretlerini içeren koruma ayarları sağlayın.** Örneğin, bir belgeye veya e-postaya "Gizli" etiketi uygulayın; bu etiket içeriği şifreler ve "Gizli" filigranı uygular. İçerik işaretleri üst bilgi ve alt bilgilerin yanı sıra filigranları da içerir ve şifreleme, yetkili kişilerin içerik üzerinde gerçekleştirebileceği eylemleri de kısıtlayabilir.

- **Farklı platformlarda ve cihazlarda Office uygulamalarındaki içeriği korumak.** Office masaüstü uygulamaları ve Web üzerinde Office Word, Excel, PowerPoint ve Outlook tarafından desteklenir. Windows, macOS, iOS ve Android'de desteklenir.

- Microsoft Defender for Cloud Apps kullanarak **üçüncü taraf uygulama ve hizmetlerdeki içeriği koruyun**. Bulut için Defender Uygulamaları ile, üçüncü taraf uygulama veya hizmet duyarlılık etiketlerini okumasa veya desteklemese bile SalesForce, Box veya DropBox gibi üçüncü taraf uygulama ve hizmetlerdeki içeriği algılayabilir, sınıflandırabilir, etiketleyebilir ve koruyabilirsiniz.

- Teams, Microsoft 365 Grupları ve SharePoint siteleri içeren **kapsayıcıları koruyun**. Örneğin, gizlilik ayarlarını, dış kullanıcı erişimini ve dış paylaşımı ve yönetilmeyen cihazlardan erişimi ayarlayın.

- **Duyarlılık etiketlerini Power BI genişletme**: Bu özelliği açtığınızda, etiketleri Power BI uygulayabilir ve görüntüleyebilir ve hizmet dışına kaydedildiğinde verileri koruyabilirsiniz.

- **Duyarlılık etiketlerini Microsoft Purview Veri Haritası'ndaki varlıklara genişletme**: Şu anda önizleme aşamasında olan bu özelliği açtığınızda, duyarlılık etiketlerinizi Microsoft Purview Veri Eşlemesi'ndeki dosyalara ve şemalaştırılmış veri varlıklarına uygulayabilirsiniz. Şemaya ayrılmış veri varlıkları SQL, Azure SQL, Azure Synapse, Azure Cosmos ve AWS RDS'yi içerir.

- **Duyarlılık etiketlerini üçüncü taraf uygulamalarında ve hizmetlerinde kullanıma sunmak.** Üçüncü taraf uygulamalar, Microsoft Bilgi Koruması SDK'yı kullanarak duyarlılık etiketlerini okuyabilir ve koruma ayarları uygulayabilir.

- **Herhangi bir koruma ayarı kullanmadan içeriği sınıflandırmak.** Ayrıca, içeriği sınıflandırmanın bir sonucu olarak bir etiket atayabilirsiniz. Bu, kullanıcılara kuruluşunuzun etiket adlarıyla sınıflandırmanın görsel bir eşlemesini sağlar ve etiketleri kullanarak kullanım raporları oluşturabilir ve hassas içeriğiniz için etkinlik verilerini görebilir. Bu bilgilere bağlı olarak, koruma ayarlarını daha sonra uygulamayı istediğiniz zaman seçebilirsiniz.

Tüm bu durumlarda, Microsoft 365 duyarlılık etiketleri doğru içerik üzerinde doğru eylemleri gerçekleştirmenize yardımcı olabilir. Duyarlılık etiketleriyle, kuruluşunuz genelinde verileri sınıflandırabilir ve bu sınıflandırmaya göre koruma ayarlarını zorunlu kılabilirsiniz.

Bunlar ve duyarlılık etiketleri tarafından desteklenen diğer senaryolar hakkında daha fazla bilgi için bkz. [Duyarlılık etiketleri için yaygın senaryolar](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Duyarlılık etiketlerini destekleyen her zaman yeni özellikler geliştiriliyor, bu nedenle [Microsoft 365 yol haritasına](https://aka.ms/MIPC/Roadmap) başvurmayı da yararlı bulabilirsiniz.

## <a name="what-a-sensitivity-label-is"></a>Duyarlılık etiketi nedir?

İçeriğe duyarlılık etiketi atadığınızda, bu, uygulanmış ve şöyle bir damga gibidir:

- **Özelleştirilebilir.** Kuruluşunuza ve iş gereksinimlerinize özel olarak, kuruluşunuzda farklı hassas içerik düzeyleri için kategoriler oluşturabilirsiniz. Örneğin, Kişisel, Genel, Genel, Gizli ve Çok Gizli.

- **Metni temizleyin.** Bir etiket, dosyalar ve e-postalar için meta verilerde düz metinde depolandığından, üçüncü taraf uygulamalar ve hizmetler bunu okuyabilir ve gerekirse kendi koruyucu eylemlerini uygulayabilir.

- **Kalıcı.** Etiket dosyalar ve e-postalar için meta verilerde depolandığından, etiket nerede kaydedilir veya depolanırsa depolansın içerikle birlikte dolaşır. Benzersiz etiket tanımlaması, yapılandırdığınız ilkeleri uygulamak ve zorunlu tutmanın temeli haline gelir.

Kullanıcılar tarafından görüntülendiğinde duyarlılık etiketi, kullandıkları uygulamalardaki bir etiket gibi görünür ve mevcut iş akışlarıyla kolayca tümleştirilebilir.

Duyarlılık etiketlerini destekleyen her öğeye tek bir duyarlılık etiketi uygulanabilir. Belgelerde ve e-postalarda hem duyarlılık etiketi hem de [bekletme etiketi](retention.md#retention-labels) uygulanabilir.

> [!div class="mx-imgBorder"]
> ![E-postaya uygulanan duyarlılık etiketi.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Duyarlılık etiketlerinin yapabilecekleri

Bir e-postaya veya belgeye duyarlılık etiketi uygulandıktan sonra, söz konusu etiket için yapılandırılmış tüm koruma ayarları içeriğe uygulanır. Duyarlılık etiketini şu şekilde yapılandırabilirsiniz:

- Yetkisiz kişilerin bu verilere erişmesini önlemek için e-postaları ve belgeleri **şifreleyin**. Ayrıca, hangi kullanıcıların veya grubun hangi eylemleri ve ne kadar süre boyunca gerçekleştirme izinlerine sahip olduğunu seçebilirsiniz. Örneğin, kuruluşunuzdaki tüm kullanıcıların belgeyi değiştirmesine izin vermeyi seçebilirsiniz ancak başka bir kuruluştaki belirli bir grup belgeyi yalnızca görüntüleyebilir. Alternatif olarak, yönetici tanımlı izinler yerine, kullanıcılarınızın etiketi uyguladığında içeriğe izin atamasına izin vekleyebilirsiniz. 
    
    Duyarlılık etiketi oluştururken veya düzenlerken **şifreleme** ayarları hakkında daha fazla bilgi için bkz. [Duyarlılık etiketlerinde şifreleme kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md).

- Office uygulamaları kullanırken e-postaya veya etiket uygulanmış belgelere filigran, üst bilgi veya alt bilgi ekleyerek **içeriği işaretleyin**. Filigranlar belgelere uygulanabilir, ancak e-postaya uygulanamayabilir. Örnek üst bilgi ve filigran:
    
    ![Belgeye filigran ve üst bilgi uygulandı.](../media/Sensitivity-label-watermark-header.png)
    
    Dinamik işaretler, değişkenler kullanılarak da desteklenir. Örneğin, etiket adını veya belge adını üst bilgi, alt bilgi veya filigrana ekleyin. Daha fazla bilgi için bkz [. Değişkenlerle dinamik işaretler](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    İçerik işaretlerinin ne zaman uygulandığını denetlemeye mi ihtiyacınız var? Bkz. [Office uygulamalar içerik işaretleme ve şifreleme uyguladığında](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Belirli belgeleri temel alan şablonlarınız veya iş akışlarınız varsa, etiketi kullanıcılar için kullanılabilir hale getirmeden önce bu belgeleri seçtiğiniz içerik işaretleriyle test edin. Dikkat edilmesi gereken bazı dize uzunluğu kısıtlamaları:
    
    Filigranlar 255 karakterle sınırlıdır. Üst bilgiler ve alt bilgiler, Excel dışında 1024 karakterle sınırlıdır. Excel üst bilgiler ve alt bilgiler için toplam 255 karakter sınırı vardır, ancak bu sınır biçimlendirme kodları gibi görünür olmayan karakterleri içerir. Bu sınıra ulaşılırsa, girdiğiniz dize Excel görüntülenmez.

- [Duyarlılık etiketlerini Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerle kullanma özelliğini etkinleştirdiğinizde, siteler ve gruplar](sensitivity-labels-teams-groups-sites.md) **gibi kapsayıcılardaki içeriği koruyun**.
    
    Bu özelliği etkinleştirene kadar gruplar ve siteler için koruma ayarlarını yapılandıramazsınız. Bu etiket yapılandırması, belgelerin veya e-postaların otomatik olarak etiketlenmesine neden olmaz, ancak bunun yerine etiket ayarları içeriğin depolanabileceği kapsayıcıya erişimi denetleyerek içeriği korur. Bu ayarlar gizlilik ayarlarını, dış kullanıcı erişimini ve dış paylaşımı ve yönetilmeyen cihazlardan erişimi içerir.

- **Etiketi dosyalara ve e-postalara otomatik olarak uygulayın veya bir etiket önerin.** Etiketlemesini istediğiniz hassas bilgilerin nasıl tanımlandığını seçin ve etiket otomatik olarak uygulanabilir veya kullanıcılardan önerdiğiniz etiketi uygulamalarını isteyebilirsiniz. Bir etiket önerirseniz, istem seçtiğiniz metni görüntüler. Örneğin:
    
    ![Gerekli bir etiket atama istemi.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Duyarlılık etiketi oluştururken veya düzenlerken **dosyalar ve e-postalar için otomatik etiketleme** ayarları hakkında daha fazla bilgi için bkz. Office uygulamalar için [içeriğe otomatik olarak duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md) ve [Microsoft Purview Veri Haritası'nda Etiketleme](/azure/purview/create-sensitivity-label).

- SharePoint siteler ve tek tek belgeler için **varsayılan paylaşım bağlantı türünü ayarlayın**. Kullanıcıların fazla paylaşımını önlemeye yardımcı olmak için, kullanıcıların SharePoint ve OneDrive belgeleri paylaştığında [varsayılan kapsamı ve izinleri](sensitivity-labels-default-sharing-link.md) ayarlayın.

### <a name="label-scopes"></a>Etiket kapsamları

Duyarlılık etiketi oluşturduğunuzda, iki şeyi belirleyen etiketin kapsamını yapılandırmanız istenir:
- Bu etiket için yapılandırabileceğiniz etiket ayarları
- Etiketin kullanıcılar tarafından görüleceği yer

Bu kapsam yapılandırması, yalnızca belgeler ve e-postalar için olan ve kapsayıcılar için seçilmeyecek duyarlılık etiketlerine sahip olmanıza olanak tanır. Benzer şekilde, yalnızca kapsayıcılara yönelik olan ve belgeler ve e-postalar için seçilebilen duyarlılık etiketleri. Microsoft Purview Veri Eşlemesi varlıklarının kapsamını da seçebilirsiniz:

![Duyarlılık etiketleri için kapsam seçenekleri.](../media/sensitivity-labels-scopes.png)

Varsayılan olarak, **Dosyalar & e-posta** kapsamı her zaman seçilidir. Kiracınız için özellikler etkinleştirildiğinde diğer kapsamlar varsayılan olarak seçilir:

- **Gruplar & siteleri**: [Kapsayıcılar için duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Şema haline getirilmiş veri varlıkları**: [Microsoft Purview Veri Eşlemesi'nde içeriğinizi otomatik olarak etiketleme](/azure/purview/create-sensitivity-label)

Tüm kapsamların seçilmemesi için varsayılanları değiştirirseniz, seçmediğiniz kapsamlar için yapılandırma ayarlarının ilk sayfasını görürsünüz, ancak ayarları yapılandıramazsınız. Örneğin, dosyaların ve e-postaların kapsamı seçili değilse, sonraki sayfadaki seçenekleri belirleyemezsiniz:

![Duyarlılık etiketleri için kullanılamayan seçenekler.](../media/sensitivity-labels-unavailable-settings.png)

Kullanılamayan seçeneklere sahip bu sayfalar için devam etmek için **İleri'yi** seçin. Ya da etiketin kapsamını değiştirmek için **Geri'yi** seçin.

### <a name="label-priority-order-matters"></a>Etiket önceliği (sıralamanın önemi)

Yönetim merkezinizde duyarlılık etiketlerinizi oluşturduğunuzda, bunlar **Etiketler** sayfasındaki **Duyarlılık** sekmesindeki bir listede görünür. Bu listede etiketlerin sırası, önceliklerini yansıttığı için önemlidir. Listenin **en altında** Çok Gizli gibi en kısıtlayıcı duyarlılık etiketinizin ve Genel gibi en az kısıtlayıcı duyarlılık etiketinizin **en üstte** görünmesini istiyorsunuz.

Belge, e-posta veya kapsayıcı gibi bir öğeye yalnızca bir duyarlılık etiketi uygulayabilirsiniz. Kullanıcılarınızın bir etiketin sınıflandırmasını düşürürken bunun nedenini belirtmesini gerektiren bir seçenek ayarlarsanız bu listedeki sıra daha düşük sınıflandırmaları tanımlar. Ancak bu seçenek, üst etiketlerinin önceliğini paylaşan alt etiketler için geçerli değildir.

Ancak alt etiketlerin sırası [otomatik etiketleme](apply-sensitivity-label-automatically.md) ile birlikte kullanılır. Etiketleri otomatik olarak veya öneri olarak uygulanmak üzere yapılandırdığınızda birden fazla eşleşme birden fazla etiketle sonuçlanabilir. Uygulanacak veya önerilecek etiketi belirlemek için etiket sıralama kullanılır: Son hassas etiket seçilir ve varsa son alt etiket seçilir.

![Alt etiket oluşturma seçeneği.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Alt etiketler (gruplandırma etiketleri)

Alt etiketleri kullanarak, bir veya daha fazla etiketi, kullanıcının bir Office uygulamasında gördüğü bir üst etiket altında gruplandırabilirsiniz. Örneğin, kuruluşunuz gizli sınıflandırmasının belirli türlerine uygun birkaç farklı etiketi Gizli üst etiketi altında kullanabilir. Bu örnekte, Gizli üst etiketi yalnızca koruma ayarı olmayan bir metin etiketidir ve alt etiketleri olduğundan içeriğe uygulanamaz. Bunun yerine, kullanıcıların alt etiketlerini görüntülemek için Gizli'yi seçmesi gerekir ve ardından içeriğe uygulanacak bir alt etiket seçebilirler.

Alt etiketler, etiketleri kullanıcılara mantıksal gruplar altında sunmanın basit bir yoludur. Alt etiketler bağlı oldukları üst etiketteki ayarları devralmaz. Bir kullanıcı için alt etiket yayımladığınızda, bu kullanıcı ilgili alt etiketi içeriğe uygulayabilir ancak yalnızca üst etikete uygulayamaz.

Varsayılan etiket olarak bir üst etiket seçmeyin veya bir üst etiketi otomatik olarak uygulanacak (veya önerilen) şekilde yapılandırmayın. Bunu yaparsanız, üst etiket içeriğe uygulanmaz.

Alt etiketlemelerin kullanıcılar için nasıl görüntülendiğine ilişkin örnek:

![Şeritte gruplandırılmış alt etiket.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Duyarlılık etiketini düzenleme veya silme

Bir duyarlılık etiketini yönetim merkezinizden silerseniz, etiket içerikten otomatik olarak kaldırılmaz ve bu etiketin uygulandığı içerikte tüm koruma ayarları uygulanmaya devam eder.

Duyarlılık etiketini düzenlerseniz, söz konusu içerikte uygulanan etiketin sürümüdür.

## <a name="what-label-policies-can-do"></a>Etiket ilkelerinin yapabilecekleri

Duyarlılık etiketlerinizi oluşturduktan sonra, kuruluşunuzdaki kişilerin ve hizmetlerin kullanımına açmak için bunları yayımlamanız gerekir. Duyarlılık etiketleri daha sonra Office belgelere ve e-postalara ve duyarlılık etiketlerini destekleyen diğer öğelere uygulanabilir. 

Tüm Exchange posta kutuları gibi konumlarda yayımlanan bekletme etiketlerinden farklı olarak, duyarlılık etiketleri kullanıcılara veya gruplara yayımlanır. Duyarlılık etiketlerini destekleyen uygulamalar daha sonra bunları bu kullanıcılara ve gruplara uygulanan etiketler veya uygulayabilecekleri etiketler olarak görüntüleyebilir.

Bir etiket ilkesi yapılandırırken şunları yapabilirsiniz:

- **Etiketleri hangi kullanıcıların ve grupların göreceğini seçin.** Etiketler, Azure AD belirli bir kullanıcı veya e-posta özellikli güvenlik grubuna, dağıtım grubuna veya Microsoft 365 grubuna ([dinamik üyeliğe](/azure/active-directory/users-groups-roles/groups-create-rule) sahip olabilir) yayımlanabilir.

- Etiketlenmemiş belgeler ve e-postalar, yeni kapsayıcılar ([Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri için duyarlılık etiketlerini etkinleştirdiğinizde](sensitivity-labels-teams-groups-sites.md) ve şimdi [de Power BI içerik](/power-bi/admin/service-security-sensitivity-label-default-label-policy) için varsayılan etiket olarak **belirtin**. Dört öğe türü için de aynı etiketi veya farklı etiketleri belirtebilirsiniz. Kullanıcılar, uygulanan varsayılan duyarlılık etiketini içeriklerinin veya kapsayıcılarının duyarlılığıyla daha iyi eşleşecek şekilde değiştirebilir.
    
    > [!NOTE]
    > Yerleşik etiketler kullanan Office uygulamalar için önizlemede: Bu ayar artık kullanıcılar tarafından açıldığında var olan belgeleri ve yeni belgeleri destekliyor. Davranıştaki bu değişiklik, Azure Information Protection birleşik etiketleme istemcisiyle eşlik sağlar. Uygulama başına dağıtım ve en düşük sürümler hakkında daha fazla bilgi için Word, Excel ve PowerPoint [için yetenekler tablosuna](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) bakın.
    
    Tüm içeriğinize uygulanmasını istediğiniz temel koruma ayarlarını ayarlamak için varsayılan bir etiket kullanmayı göz önünde bulundurun. Ancak, kullanıcı eğitimi ve diğer denetimler olmadan bu ayar yanlış etiketlemeye de neden olabilir. Belgelere varsayılan etiket olarak şifreleme uygulayan bir etiket seçmek genellikle iyi bir fikir değildir. Örneğin, birçok kuruluşun şifrelemeyi destekleyen uygulamaları olmayan veya yetkilendirilebilen bir hesap kullanamayan dış kullanıcılarla belge göndermesi ve paylaşması gerekir. Bu senaryo hakkında daha fazla bilgi için bkz. [Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > [Alt etiketleriniz](#sublabels-grouping-labels) olduğunda, üst etiketi varsayılan etiket olarak yapılandırmamaya dikkat edin.

- **Etiketi değiştirmek için gerekçe gerektir.** Bir kullanıcı etiketi kaldırmaya veya daha düşük sıralı bir numaraya sahip bir etiketle değiştirmeyi denerse, kullanıcının bu eylemi gerçekleştirmek için bir gerekçe sağlaması gerekebilir. Örneğin, kullanıcı Gizli (sipariş numarası 3) etiketli bir belge açar ve bu etiketi Ortak (sipariş numarası 1) adlı bir belgeyle değiştirir. Office uygulamalar için bu gerekçe istemi yerleşik etiketleme kullandığınızda uygulama oturumu başına bir kez ve Azure Information Protection birleşik etiketleme istemcisini kullandığınızda dosya başına tetiklenir. Yöneticiler gerekçe nedenini ve [etkinlik gezginindeki](data-classification-activity-explorer.md) etiket değişikliğini okuyabilir.

    ![Kullanıcıların gerekçe girmelerini iste.](../media/Sensitivity-label-justification-required.png)

- Kullanıcıların belgeler ve e-postalar, yalnızca belgeler, kapsayıcılar ve Power BI içeriği için **etiket uygulamasını zorunlu kılar**. Zorunlu etiketleme olarak da bilinen bu seçenekler, kullanıcıların belgeleri kaydedip e-posta gönderebilmesi, yeni gruplar veya siteler oluşturabilmesi ve Power BI için etiketlenmemiş içerik kullandıklarında önce bir etiketin uygulanması gerektiğini güvence altına alır.
    
    Belgeler ve e-postalar için, bir etiket kullanıcı tarafından el ile, yapılandırdığınız bir koşulun sonucu olarak otomatik olarak atanabilir veya varsayılan olarak atanabilir (daha önce açıklanan varsayılan etiket seçeneği). Bir kullanıcının etiket ataması gerektiğinde örnek bir istem:

    ![Outlook kullanıcıdan gerekli etiketi uygulamasını isteme istemi.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Belgeler ve e-postalar için zorunlu etiketleme hakkında daha fazla bilgi için bkz. [Kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektirme](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    Kapsayıcılar için, grup veya site oluşturulurken bir etiket atanmalıdır.
    
    Power BI için zorunlu etiketleme hakkında daha fazla bilgi için bkz[. Power BI için zorunlu etiket ilkesi](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).
    
    Etiketleme kapsamınızı artırmanıza yardımcı olması için bu seçeneği kullanmayı göz önünde bulundurun. Ancak, kullanıcı eğitimi olmadan bu ayarlar yanlış etiketlemeye neden olabilir. Ayrıca, karşılık gelen bir varsayılan etiket ayarlamadığınız sürece, zorunlu etiketleme sık sorulan istemlerle kullanıcılarınızı rahatsız edebilir.

- **Özel bir yardım sayfasına yardım bağlantısı sağlayın.** Kullanıcılarınız duyarlılık etiketlerinizin ne anlama geldiğini veya nasıl kullanılmaları gerektiğini bilmiyorsa, Office uygulamalarında **Duyarlılık etiketi** menüsünün en altında görünen Daha Fazla Bilgi URL'si sağlayabilirsiniz:

    ![Şeritteki Duyarlılık düğmesinde daha fazla bilgi edinin bağlantısı.](../media/Sensitivity-label-learn-more.png)

Kullanıcılara ve gruplara yeni duyarlılık etiketleri atayan bir etiket ilkesi oluşturduktan sonra, kullanıcılar bu etiketleri Office uygulamalarında görmeye başlar. En son değişikliklerin kuruluşunuz genelinde çoğaltılması için 24 saate kadar izin verin.

Oluşturabileceğiniz ve yayımlayabileceğiniz duyarlılık etiketlerinin sayısıyla ilgili bir sınır yoktur. Tek bir istisna vardır: Etiket, kullanıcıları ve izinleri belirten bir şifreleme uygularsa, bu yapılandırmada desteklenen en fazla 500 etiket vardır. Ancak, kullanıcılarınız için yönetici ek yüklerini azaltmak ve karmaşıklığı azaltmak için en iyi yöntem olarak etiket sayısını en düşük düzeyde tutmaya çalışın. Gerçek dünya dağıtımları, kullanıcıların ana etiket başına beşten fazla ana etiketi veya beşten fazla alt etiketi olduğunda etkinliğin belirgin bir şekilde azaltıldığını kanıtlamıştır.

### <a name="label-policy-priority-order-matters"></a>Etiket ilkesi önceliği (sipariş önemlidir)

Duyarlılık etiketlerinizi, **Etiket** **ilkeleri sayfasındaki Duyarlılık ilkeleri** sekmesindeki bir listede görünen duyarlılık etiketi ilkesinde yayımlayarak kullanıcıların kullanımına sunabilirsiniz. Duyarlılık etiketleri gibi (bkz [. Etiket önceliği (sıra önemlidir)](#label-priority-order-matters)), duyarlılık etiketi ilkelerinin sırası da önceliklerini yansıttığı için önemlidir. En düşük önceliğe sahip etiket ilkesi **en üstte**, en yüksek önceliğe sahip etiket ilkesi ise **en altta** gösterilir.

Etiket ilkesi şunlardan oluşur:

- Bir etiket kümesi.
- İlkeye etiketlerle atanacak kullanıcılar ve gruplar.
- Bu kapsamın ilke ve ilke ayarlarının kapsamı (dosyalar ve e-postalar için varsayılan etiket gibi).

Bir kullanıcıyı birden çok etiket ilkesine dahil edebilirsiniz ve kullanıcı bu ilkelerden tüm duyarlılık etiketlerini ve ayarlarını alır. Birden çok ilkenin ayarlarında çakışma varsa, ilkenin en yüksek öncelikli (en düşük konum) ayarları uygulanır. Başka bir deyişle, en yüksek öncelik her ayar için kazanır.

Bir kullanıcı veya grup için beklediğiniz etiket veya etiket ilkesi ayarı davranışını görmüyorsanız duyarlılık etiketi ilkelerinin sırasını denetleyin. İlkeyi aşağı taşımanız gerekebilir. Etiket ilkelerini yeniden sıralamak için bir duyarlılık etiketi ilkesi seçin > sağ taraftaki üç noktayı > **Aşağı taşı** veya **Yukarı taşı'yı** seçin.

![Duyarlılık etiketi ilkeleri için sayfadaki taşıma seçeneği.](../media/sensitivity-label-policy-priority.png)

> [!NOTE]
> Unutmayın: Birden çok ilke atanmış bir kullanıcı için ayarlar çakışması olduğunda, ilkeden en yüksek önceliğe (en düşük konuma) sahip ayar uygulanır.

## <a name="sensitivity-labels-and-azure-information-protection"></a>Duyarlılık etiketleri ve Azure Information Protection

Windows, macOS, iOS ve Android'de Microsoft 365 Uygulamaları yerleşik olarak bulunan duyarlılık etiketleri, kullanıcılara tutarlı bir etiketleme deneyimi sağlamak için bu cihazlarda çok benzer şekilde görünür ve davranır. Ancak Windows bilgisayarlarda [Azure Information Protection (AIP) istemcisini](/azure/information-protection/rms-client/aip-clientv2) de kullanabilirsiniz. Bu istemci artık [bakım modunda](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613).

AIP istemcisini kullanıyorsanız, Windows bilgisayarlar için etiketleme seçeneklerinizi anlamak ve yönetmek [üzere Office uygulamalar için AIP eklentisi yerine yerleşik etiketlemeyi seçme](sensitivity-labels-aip.md) nedenine bakın.

### <a name="azure-information-protection-labels"></a>Azure Information Protection etiketleri

> [!NOTE]
> Azure portal Azure Information Protection etiketleri için etiket yönetimi **31 Mart 2021'de** kullanım dışı bırakılmıştır. Resmi [kullanımdan kaldırma bildiriminden](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179) daha fazla bilgi edinin.

Kiracınız henüz [birleşik etiketleme platformunda](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform) değilse duyarlılık etiketlerini kullanabilmek için önce birleşik etiketlemeyi etkinleştirmeniz gerekir. Yönergeler için bkz. [Azure Information Protection etiketlerini birleşik duyarlılık etiketlerine geçirme](/azure/information-protection/configure-policy-migrate-labels).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Duyarlılık etiketleri ve Microsoft Bilgi Koruması SDK'sı

Bir duyarlılık etiketi belgenin meta verilerinde depolandığından, üçüncü taraf uygulamalar ve hizmetler etiketleme dağıtımınızı tamamlamak için bu etiketleme meta verilerini okuyabilir ve bunlara yazabilir. Buna ek olarak, yazılım geliştiricileri birden çok platformda etiketleme ve şifreleme özelliklerini tam olarak desteklemek için [Microsoft Bilgi Koruması SDK'sını](/information-protection/develop/overview#microsoft-information-protection-sdk) kullanabilir. Daha fazla bilgi edinmek için [Tech Community blogundaki Genel Kullanılabilirlik duyurusunu okuyun](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

[Microsoft Purview Information Protection ile tümleştirilmiş iş ortağı çözümleri](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657) hakkında da bilgi edinebilirsiniz.

## <a name="deployment-guidance"></a>Dağıtım kılavuzu

Lisans bilgilerini, izinleri, dağıtım stratejisini, desteklenen senaryoların listesini ve son kullanıcı belgelerini içeren dağıtım planlaması ve yönergeleri için bkz. [duyarlılık etiketleriyle Kullanmaya başlayın](get-started-with-sensitivity-labels.md).

Veri gizliliği düzenlemelerine uymak için duyarlılık etiketlerini kullanmayı öğrenmek için bkz. [Microsoft 365 (aka.ms/m365dataprivacy) ile veri gizliliği düzenlemeleri için bilgi koruması dağıtma](../solutions/information-protection-deploy.md).
