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
description: Hassas içeriği sınıflandırmak ve korumak Microsoft Bilgi Koruması(MIP) etiketlerini kullanın.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 9c1eb0e7ba8f1c9388dd61f5e3433e47f9cd0cf4
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033336"
---
# <a name="learn-about-sensitivity-labels"></a>Duyarlılık etiketleri hakkında bilgi edinin

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Office uygulamalarında gördüğünüz duyarlılık etiketleri hakkında bilgi arıyorsanız, bkz. Office'te dosyalarınıza ve [e-postanıza duyarlılık Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).
>
> Bu sayfada yer alan bilgiler, bu etiketleri oluşturan ve yapılandıran IT yöneticilerine göredir.

İşlerini yapmak için, kuruluşların içindeki ve dışındaki diğer kişiler ile işbirliği yapın. Bu, içeriğin artık güvenlik duvarının arkasında kalma anlamına gelir; her yerde, cihazlar, uygulamalar ve hizmetler arasında dolaşabilirsiniz. E-ticaret ne zaman dolsa, bunu, kurumnizin iş ve uyumluluk ilkelerine uygun, güvenli ve korumalı bir şekilde yapmak istersiniz.

Microsoft Bilgi Koruması çözümünün duyarlılık etiketleri, kullanıcı üretkenliğinin ve işbirliği yapma becerilerinin engelli olmadığından emin olmak için, kuruluş verilerinizi sınıflandırmanıza ve korumanıza olanak sağlar.

Şeritteki Giriş sekmesinden Excel duyarlılık **etiketlerini** gösteren örnek. Bu örnekte, uygulanan etiket durum çubuğunda görüntülenir:

![Şeritte ve durum Excel duyarlılık etiketi.](../media/Sensitivity-label-in-Excel.png)

Duyarlılık etiketleri uygulamak için, kullanıcıların iş veya okul hesaplarıyla Microsoft 365 oturumları olması gerekir.

> [!NOTE]
> ABD Kamu kiracıları için duyarlılık etiketleri tüm platformlar için desteklemektedir.
>
> Azure Information Protection birleşik etiketleme istemcisini ve tarayıcısını kullanıyorsanız, [Bkz. Azure Information Protection Premium Açıklama](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Duyarlılık etiketlerini şu amaçlarla kullanabilirsiniz:
  
- **Şifreleme ve içerik işaretleri içeren koruma ayarları sağlar.** Örneğin, bir belgeye veya e-postaya "Gizli" etiketi ekleyin; bu etiket içeriği şifreler ve "Gizli" filigranı uygular. İçerik işaretlemeleri, filigranların yanı sıra üst bilgi ve alt bilgileri de içerir ve şifreleme, yetkili kişilerin içerik üzerinde gerçekleştir eylemlerine kısıtlama da neden olabilir.

- **Farklı platformlarda ve cihazlarda Office uygulamalarındaki içeriği korumak.** Word, Excel, PowerPoint ve Outlook masaüstü Office uygulamaları ve Web üzerinde Office. Windows, macOS, iOS ve Android'de de desteklenen.

- **Bulut Uygulamaları için Microsoft Defender'ı kullanarak üçüncü** taraf uygulama ve hizmetlerde yer alan içeriği koruyun. Bulut Uygulamaları için Defender'la, üçüncü taraf uygulama veya hizmet duyarlılık etiketlerini okumasa veya desteklemese bile SalesForce, Box veya DropBox gibi üçüncü taraf uygulama ve hizmetlerde içeriği algılanabilir, sınıflandıramaz, etiketli ve koruyabilirsiniz.

- **Özel gruplar**, gruplar Teams Microsoft 365 içeren kapsayıcıları SharePoint koruyun. Örneğin, gizlilik ayarlarını, dış kullanıcı erişimini ve dış paylaşımı ve unmanaged cihazlarından erişim ayarlarını yapın.

- **Duyarlılık etiketlerini Power BI**: Bu özelliği açık durumdayken, Power BI'de etiket uygulayabilir ve bakabilirsiniz ve verileri hizmetin dışına kaydedilene kadar koruyabilirsiniz.

- **Azure Purview'daki** varlıklara duyarlılık etiketlerini genişletme: Şu anda önizlemede olan bu özelliği etkin hale gelirken, Azure Purview'da dosyalara ve şemalı veri varlıklarına duyarlılık etiketlerinizi uygulayabilirsiniz. Şematize veri varlıkları arasında SQL, Azure SQL, Azure Synapse, Azure Cosoms ve AWS RDS yer alır.

- **Duyarlılık etiketlerini üçüncü taraf uygulamalarında ve hizmetlerinde kullanıma sunmak.** Microsoft Bilgi Koruması SDK'yı kullanarak, üçüncü taraf uygulamalar duyarlılık etiketlerini okuyabilir ve koruma ayarları uygulayabilir.

- **Herhangi bir koruma ayarı kullanmadan içeriği sınıflandırmak.** ayrıca, içeriği sınıflandırma sonucu yalnızca bir etiket de atabilirsiniz. Bu, kullanıcılara sınıflandırmanın kuruluş etiket adlarına görsel bir eşlemesini sağlar ve kullanım raporları oluşturmak ve hassas içeriğinizin etkinlik verilerini görmek için etiketleri kullanabilir. Bu bilgilere bağlı olarak, koruma ayarlarını daha sonra istediğiniz zaman uygulayabilirsiniz.

Tüm bu durumlarda, Microsoft 365'daki duyarlılık etiketleri doğru içerik üzerinde doğru eylemleri gerçekleştirebilirsiniz. Duyarlılık etiketleriyle, verileri kuruluş genelinde sınıflandırabilirsiniz ve koruma ayarlarını bu sınıflandırmaya göre zorunlu  edebilirsiniz.

Duyarlılık etiketleri tarafından desteklenen bu senaryolar ve diğer senaryolar hakkında daha fazla bilgi için bkz [. Duyarlılık etiketleri için genel senaryolar](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Duyarlılık etiketlerini destekleyen yeni özellikler her zaman geliştiriliyor. Bu nedenle, yol haritasına başvurulması konusunda Microsoft 365 [bulabilirsiniz](https://aka.ms/MIPC/Roadmap).

## <a name="what-a-sensitivity-label-is"></a>Duyarlılık etiketi nedir?

Bir duyarlılık etiketini içeriğe atadığınız zaman, uygulanan bir damga gibi olur ve şu şekilde olur:

- **Özelleştirilebilir.** Kendi kuruluş ve iş ihtiyaçlarına özel olarak, kurumuz için farklı düzeyde hassas içerik kategorileri oluşturabilirsiniz. Örneğin, Kişisel, Genel, Genel, Gizli ve Çok Gizli.

- **Metni temizleme.** Dosyalar ve e-postaların meta verilerinde bir etiket net metin olarak depolandığı için üçüncü taraf uygulamalar ve hizmetler bu etiketi okuyabilir ve gerekirse kendi koruyucu eylemlerini uygulayabilir.

- **Kalıcı.** Etiket, dosyaların ve e-postaların meta verilerinde depolandığı için, nereye kaydedilir veya depolandığı fark etmez; etiket içerikle birlikte dolaştır. Benzersiz etiket kimliği, yapılandırılan ilkelerin uygulanması ve zorlanmaları için temel haline gelir.

Kullanıcılar tarafından görüntülendiğinde, duyarlılık etiketi kullanıcıların uygulamalarına eklen bir etiket gibi görünür ve var olan iş akışlarıyla kolayca tümleşebilir.

Duyarlılık etiketlerini destekleyen her öğeye tek bir duyarlılık etiketi uygulanabilir. Belgelere ve e-postalara hem duyarlılık etiketi hem [de bekletme](retention.md#retention-labels) etiketi uygulanmış olabilir.

> [!div class="mx-imgBorder"]
> ![E-postaya uygulanan duyarlılık etiketi.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Duyarlılık etiketlerinin neler yapabilirim?

Bir e-postaya veya belgeye duyarlılık etiketi uygulandıktan sonra, bu etiket için tüm yapılandırılmış koruma ayarları içerikte zorunlu kılındı. Duyarlılık etiketini şu şekilde yapılandırarak:

- **Yetkisiz** kişilerin bu verilere erişmesini önlemek için e-postaları ve belgeleri şifrele. Ayrıca, hangi kullanıcıların veya grubun hangi eylemleri ne kadar süreyle gerçekleştirme iznine sahip olduğunu da seçebilirsiniz. Örneğin, başka bir kuruluşta belirli bir grup belgeyi yalnızca görüntüley varken, kuruluşta yer alan tüm kullanıcıların bir belgeyi değiştirmesine izin vermeyi seçebilirsiniz. Alternatif olarak, yönetici tanımlı izinler yerine kullanıcılarınızı etikete uygulayabilecekleri içerik izinleri atamalarına izin veebilirsiniz. 
    
    Duyarlılık etiketi **2007'yi** 2013'te 2007'yi kullanırken şifreleme ayarları hakkında daha fazla bilgi için bkz. Duyarlılık etiketlerini şifreleme kullanarak [içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md).

- **E-postaya** veya Office uygulanan belgelere filigran, üst bilgi veya alt bilgi ekleyerek, bu uygulamaları kullanarak içeriği işaretlerini alın. Filigranlar belgelere uygulanabilir, ancak e-posta uygulanmalıdır. Örnek üstbilgi ve filigran:
    
    ![Belgeye uygulanan filigran ve üst bilgi.](../media/Sensitivity-label-watermark-header.png)
    
    İçerik işaretleri uygulandığında denetlemeniz mi gerekiyor? Bkz[. Office uygulamaları içerik işaretleme ve şifreleme uygulamaz](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Tüm uygulamalar, değişkenler kullanarak dinamik işaretlemeleri destekler, ancak bazıları desteklemez. Örneğin, üst bilgi, alt bilgi veya filigrana etiket adını veya belge adını ekleyin. Daha fazla bilgi için bkz [. Değişkenlerle dinamik işaretler](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Dize uzunluğu: Filigranlar 255 karakterle sınırlıdır. Üstbilgi ve altbilgiler, üstbilgiler ve altbilgiler hariç 1024 Excel. Excel üst bilgi ve alt bilgiler için toplam 255 karakter sınırlaması vardır, ancak bu sınır, biçimlendirme kodları gibi görünür olmayan karakterleri içerir. Sınıra ulaşıldısa, bu sınıra girersiniz dizesi Excel.

- **Duyarlılık etiketlerini Microsoft Teams**, site grupları ve diğer sitelerle kullanma özelliğini etkinleştirirken, Microsoft 365 ve grup gibi [SharePoint koruyun](sensitivity-labels-teams-groups-sites.md).
    
    Bu özelliği etkinleştirene kadar gruplar ve siteler için koruma ayarlarını yapılandırılamaz. Bu etiket yapılandırması belgelerin veya e-postaların otomatik olarak etiketlenirken sonuç olarak değil, bunun yerine etiket ayarları içeriğin depolanlandığı kapsayıcıya erişimi denetleyerek içeriği korur. Bu ayarlar gizlilik ayarlarını, dış kullanıcı erişimini ve dış paylaşımı ve unmanaged cihazlarından erişimleri içerir.

- **Etiketi dosyalara ve e-postalara otomatik olarak uygulayabilir veya bir etiket önerebilirsiniz.** Etiket olmasını istediğiniz hassas bilgilerin nasıl tanım olacağını ve etiketin otomatik olarak nasıl uygulanabileceklerini seçin veya kullanıcılardan önerdiğiniz etiketi uygulamalarını istenebilirsiniz. Etiket önerin, bilgi isteminde seçtiğiniz metin görüntülenir. Örneğin:
    
    ![Gerekli etiketin atanma istemi.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Bir duyarlılık etiketi 2012 veya daha fazla duyarlılık etiketi 2012'yi düzenlerken dosya ve **e-posta** ayarlarını otomatik olarak etiketleme hakkında daha fazla bilgi için bkz. Office için içeriğe otomatik olarak duyarlılık etiketi uygulama ve [Azure Purview'da](/azure/purview/create-sensitivity-label) etiketleme.[](apply-sensitivity-label-automatically.md)

### <a name="label-scopes"></a>Etiket kapsamları

Duyarlılık etiketi  oluşturmak için, etiketin kapsamını iki şeyi belirleyen yapılandırman istensin:
- Bu etiket için yapılandırabilirsiniz etiket ayarları
- Etiketin kullanıcılar tarafından görülebilecekleri yer

Bu kapsam yapılandırması, yalnızca belgeler ve e-postalar için olan ve kapsayıcılar için seçilenene kadar duyarlılık etiketlerine sahip olasınız. Ve benzer şekilde, yalnızca kapsayıcılar için olan ve belgeler ve e-postalar için seçileylene duyarlılık etiketleri. Azure Purview varlıklarının kapsamını da kullanabilirsiniz:

![Duyarlılık etiketleri için kapsam seçenekleri.](../media/sensitivity-labels-scopes.png)

Varsayılan olarak, Dosyalar **ve & kapsamı** her zaman seçilidir. Kiracınız için özellikler etkinleştirildiğinde diğer kapsamlar varsayılan olarak seçilir:

- **Gruplar &:** [Kapsayıcılar için duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Şemalı veri varlıkları**: [Azure Purview'da içeriğinizi otomatik olarak etiketleme](/azure/purview/create-sensitivity-label)

Varsayılanları değiştirir ve tüm kapsamlar seçilmezse, henüz seçilmemiş kapsamlar için yapılandırma ayarlarının ilk sayfasını görüntülersiniz, ancak ayarları yapılandıramazsanız. Örneğin, dosya ve e-posta kapsamı seçilmemişse, sonraki sayfada şu seçenekleri seçeyesiniz:

![Duyarlılık etiketleri için kullanılamaz seçenekler.](../media/sensitivity-labels-unavailable-settings.png)

Kullanılamayan bu sayfalar için, devam etmek için **Sonraki'yi** seçin. Veya **Geri'yi** seçerek etiketin kapsamını değiştirebilirsiniz.

### <a name="label-priority-order-matters"></a>Etiket önceliği (sıralamanın önemi)

Yönetim merkezinize duyarlılık etiketlerinizi ekleyebilirsiniz, bu etiketler, Etiketler sayfasının **Duyarlılık** sekmesindeki bir **listede** görüntülenir. Bu listede, etiketlerin sırası önemlidir çünkü önceliklerini yansıtacaktır. Çok Gizli gibi en kısıtlayıcı duyarlılık etiketinizin listenin en altında ve en kısıtlayıcı duyarlılık etiketinizin  de (Genel gibi) en üstte görünmesini **istiyorsunuz**.

Belge, e-posta veya kapsayıcı gibi bir öğeye yalnızca bir duyarlılık etiketi uygulayabilirsiniz. Kullanıcılarınızın bir etiketin sınıflandırmasını düşürürken bunun nedenini belirtmesini gerektiren bir seçenek ayarlarsanız bu listedeki sıra daha düşük sınıflandırmaları tanımlar. Bununla birlikte, bu seçenek üst etiketlerinin önceliğini paylaşan altbelbeller için geçerli değildir.

Yine de alt etiketlerin sırası otomatik [etiketle](apply-sensitivity-label-automatically.md) birlikte kullanılır. Etiketleri otomatik olarak veya öneri olarak uygulanmak üzere yapılandırdığınızda birden fazla eşleşme birden fazla etiketle sonuçlanabilir. Uygulanacak veya önerilecek etiketi belirlemek için etiket sırası kullanılır: Son hassas etiket seçilir ve uygulanıyorsa son alt etiket olur.

![Alt etiket oluşturma seçeneği.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Alt etiketler (gruplandırma etiketleri)

Alt etiketleri kullanarak, bir veya daha fazla etiketi, kullanıcının bir Office uygulamasında gördüğü bir üst etiket altında gruplandırabilirsiniz. Örneğin, kuruluşunuz gizli sınıflandırmasının belirli türlerine uygun birkaç farklı etiketi Gizli üst etiketi altında kullanabilir. Bu örnekte Gizli üst etiketi, koruma ayarları eklemeden yalnızca bir metin etiketidir ve alt etiketleri olduğundan içeriğe uygulanamamaktadır. Bunun yerine, kullanıcıların altları görüntülemek için Gizli'yi seçmeleri gerekir ve bundan sonra içeriğe uygulamak için bir alt etiket seçebilirler.

Alt etiketler, etiketleri kullanıcılara mantıksal gruplar altında sunmanın basit bir yoludur. Alt etiketler bağlı oldukları üst etiketteki ayarları devralmaz. Bir kullanıcı için alt etiket yayımladığınızda, bu kullanıcı ilgili alt etiketi içeriğe uygulayabilir ancak yalnızca üst etikete uygulayamaz.

Varsayılan etiket olarak üst etiket seçmenin yanı sıra, otomatik olarak uygulanacak (veya önerilen) bir üst etiket yapılandırabilirsiniz. Bunu yaparsanız, üst etiket içeriğe uygulanmaz.

Altbelbellerin kullanıcılar için nasıl görüntüleniyor olduğunu örneği:

![Şeritte gruplara bağlı altbelbeller.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Duyarlılık etiketini düzenleme veya silme

Yönetim merkeziniz'den bir duyarlılık etiketini silerseniz etiket otomatik olarak içerikten kaldırılamaz ve koruma ayarları bu etiketin uygulandığı içerikte uygulanmaya devam eder.

Duyarlılık etiketini düzenlersanız, bu içerikte uygulanan etiketin sürümü uygulanır.

## <a name="what-label-policies-can-do"></a>Etiket ilkeleri neleri yapar?

Duyarlılık etiketlerinizi oluşturduktan sonra, bunları yayımlamanız ve bunları organizasyonlu kişiler ve hizmetler için kullanılabilir hale oluşturmanız gerekir. Daha sonra duyarlılık etiketleri belge ve Office ve duyarlılık etiketlerini destekleyen diğer öğelere de uygulanabilir. 

Paylaşılan tüm posta kutuları gibi konumlarda yayımlanan bekletme Exchange, duyarlılık etiketleri kullanıcılara veya gruplara yayımlanır. Daha sonra duyarlılık etiketlerini destekleyen uygulamalar bu kullanıcılara ve gruplara, uygulanan etiketler veya uygulanabilecek etiketler olarak  gösterebilirsiniz.

Bir etiket ilkesi yapılandırıldığında şunları da s yapılandırmaya devam etmiş sayılır:

- **Etiketleri hangi kullanıcıların ve grupların göreceğini seçin.** Etiketler, Azure AD'de belirli bir kullanıcıya veya e-posta özelliği etkin güvenlik grubuna, dağıtım grubuna Microsoft 365 grup (dinamik üyeliği [olabilir) için](/azure/active-directory/users-groups-roles/groups-create-rule) yayımlanır.

- **Etiketsiz belgeler** ve e-postalar, yeni kapsayıcılar ([Microsoft Teams, Microsoft 365](sensitivity-labels-teams-groups-sites.md) grupları ve SharePoint siteleri için duyarlılık etiketlerini etkinleştirdikten sonra, artık içerik için varsayılan Power BI [belirtin](/power-bi/admin/service-security-sensitivity-label-default-label-policy). Dört öğe türü için aynı etiketi veya farklı etiketleri belirtebilirsiniz. Kullanıcılar kendi içeriklerinin veya kapsayıcılarının duyarlılıklarıyla daha iyi eşleşmesi için, uygulanmış olan varsayılan duyarlılık etiketini değiştirebilir.
    
    > [!NOTE]
    > Yerleşik etiketlerin Office uygulamaların önizlemesinde: Bu ayar artık kullanıcılar tarafından açıldığında hem varolan belgeleri hem de yeni belgeleri destekler. Bu davranış değişikliği, Azure Information Protection birleşik etiketleme istemcisinde eşlik sağlar. Uygulama başına ve en düşük sürümler için uygulama başına uygulama sürümü hakkında daha fazla [](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) bilgi için Word, Excel özellikleri tablosuna PowerPoint.
    
    Tüm içeriğinize uygulanmasını istediğiniz temel koruma ayarları düzeyini ayarlamak için varsayılan bir etiket kullanmayı göz önünde bulundurabilirsiniz. Bununla birlikte, kullanıcı eğitimi ve diğer denetimler olmadan bu ayar yanlış etiketlemeye neden olabilir. Belgelere varsayılan etiket olarak şifreleme uygulanan bir etiket seçmek genellikle iyi bir fikir değildir. Örneğin, birçok kuruluşun şifrelemeyi destekleyen uygulamaları olmayan veya yetkilendirilen bir hesap kullanmay isteyen dış kullanıcılara belge göndermesi ve bu kullanıcılarla belge paylaşması gerekir. Bu senaryo hakkında daha fazla bilgi için bkz [. Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > Alt etiketleri [olduğunda, üst](#sublabels-grouping-labels) etiketi varsayılan etiket olarak yapılandırmama konusunda dikkatli olun.

- **Etiketi değiştirmek için gerekçelendirme gerektirme.** Kullanıcı bir etiketi kaldırmayı veya daha düşük sipariş numarası olan bir etiketle değiştirirse, kullanıcının bu eylemi gerçekleştirmek için bir gerekçelendirmesi gerektirmeyiniz gerekir. Örneğin, bir kullanıcı Gizli (sipariş numarası 3) etiketli bir belge açar ve bu etiketi Genel adlı bir belgeyle (sipariş numarası 1) değiştirir. Tüm Office için, yerleşik etiketlemeyi ve Azure Information Protection birleşik etiketleme istemcisini kullanarak dosya başına bir kez uygulama oturumu başına bu gerekçelendirme istemini tetikler. Yöneticiler gerekçelendirme nedenini etkinlik gezgininde etiket değişikliğiyle birlikte [okuyabilir](data-classification-activity-explorer.md).

    ![Kullanıcıların bir gerekçe girmelerini istemi.](../media/Sensitivity-label-justification-required.png)

- **Kullanıcıların belgelere ve e-postalara**, yalnızca belgelere, kapsayıcılara ve diğer belgelere etiket Power BI gerektir. Zorunlu etiketleme olarak da bilinen bu seçenekler, kullanıcıların belgeleri kaydederek e-posta gönderemeden, yeni gruplar veya siteler oluşturmadan, bu gruplarda etiketsiz içerik kullanmadan önce bir etiket uygulanması Power BI.
    
    Belgeler ve e-postalar için, yapılandırılan bir koşul sonucunda kullanıcı tarafından el ile bir etiket atanabilir veya varsayılan olarak atanabilir (önceden tanımlanan varsayılan etiket seçeneği). Kullanıcının etiket ataması gerektiğinde örnek bir istem:

    ![Kullanıcıdan Outlook etiketini uygulamalarını isteme.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Belgeler ve e-postalar için zorunlu etiketleme hakkında daha fazla bilgi için bkz. Kullanıcıların e-postalarına ve belgelerine [etiket uygulamalarını gerektirme](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    Kapsayıcılar için, grup veya site oluşturulduğunda bu etikete bir etiket atanmalıdır.
    
    E-Power BI için zorunlu etiketleme hakkında daha fazla bilgi için bkz[.](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy) Power BI.
    
    Etiket kapsamınızı artırmaya yardımcı olmak için bu seçeneği kullanmayı düşünebilirsiniz. Bununla birlikte, kullanıcı eğitimi olmadan bu ayarlar yanlış etiketlemeye neden olabilir. Buna ek olarak, karşılık gelen bir varsayılan etiket ayarlamadıysanız, zorunlu etiketleme kullanıcılarınızı sık sorulan istemlere karşı hayal kırıklığına uğratabilirsiniz.

- **Özel yardım sayfasına yardım bağlantısı sağlama.** Kullanıcılarınız duyarlılık etiketlerinin ne anlama olduğundan veya nasıl kullanılmaları gerektiğine emin değilse, Office uygulamaları altındaki Duyarlılık etiketi menüsünün altında görünen daha fazla bilgi URL'si sebilirsiniz:

    ![Şeritteki Duyarlılık düğmesi hakkında daha fazla bilgi bağlantısı.](../media/Sensitivity-label-learn-more.png)

Kullanıcılara ve gruplara yeni duyarlılık etiketleri ataan bir etiket ilkesi oluşturduktan sonra, kullanıcılar bu etiketleri kendi kullanıcılarının veya Office başlar. En son değişikliklerin tüm kuruluş genelinde çoğaltılması için 24 saate kadar izin verme.

Tek bir istisnayla, oluştur hem de yayımlayabilirsiniz duyarlılık etiketlerinin sayısında bir sınırlama yoktur: Etiket, kullanıcıları ve izinleri belirten şifrelemeyi uygularsa, bu yapılandırmada desteklenen en çok 500 etiket vardır. Bununla birlikte, yönetici yükünü azaltmak ve kullanıcılarınız için karmaşıklığı azaltmak için en iyi uygulama olarak, etiket sayısını en az düzeyde tutmaya çalışabilirsiniz. Gerçek dağıtımlar, kullanıcıların beşten fazla ana etiketi veya ana etiket başına beşten fazla alt etiketi olduğunda, bu dağıtımların fark edildiklerinden emin olunmalarını sağlar.

### <a name="label-policy-priority-order-matters"></a>Etiket ilkesi önceliği (sipariş konuları)

Duyarlılık etiketlerinizi, Etiket ilkeleri sayfasının Duyarlılık ilkeleri sekmesindeki bir listede görüntülenen bir duyarlılık etiketi ilkesinde yayımarak kullanıcılarına **gösterebilirsiniz**. Duyarlılık etiketleri gibi (bkz [. Etiket önceliği (sipariş konuları)](#label-priority-order-matters)), duyarlılık etiketi ilkelerinin sırası önemlidir çünkü bu ilkelerin önceliğini yansıtması gerekir. En düşük önceliğe sahip etiket ilkesi en üstte **,** en yüksek önceliğe sahip etiket ilkesi ise en altta **gösterilir**.

Etiket ilkesi şunları sağlar:

- Bir etiket kümesi.
- Etiketlerle ilkeye atanacak kullanıcılar ve gruplar.
- Bu kapsam için ilke ve ilke ayarlarının kapsamı (dosyalar ve e-postalar için varsayılan etiket gibi).

Bir kullanıcıyı birden çok etiket ilkelerine  dahil edebilirsiniz ve kullanıcı bu ilkelerden tüm duyarlılık etiketlerini ve ayarlarını alır. Birden çok ilkenin ayarlarında çakışma olursa, en yüksek önceliğe (en düşük konum) sahip ilkeye yönelik ayarlar uygulanır. Başka bir deyişle, her ayar için en yüksek öncelik kazanır.

Kullanıcı veya grup için beklediğiniz etiket veya etiket ilkesi ayar davranışını görmüyorsanız, duyarlılık etiketi ilkelerinin sırasına dikkat edin. İlkeyi aşağı taşımamız gerekiyor olabilir. Etiket ilkelerini yeniden sıralamak için, sağ üst köşedeki > veya Yukarı taşı'ya > duyarlılık etiketi **ilkesi seçin**.

![Duyarlılık etiketi ilkeleri için sayfada Taşı seçeneği.](../media/sensitivity-label-policy-priority.png)

> [!NOTE]
> Unutmayın: Birden çok ilke atanmış bir kullanıcının ayarları arasında çakışma olduğunda, en yüksek önceliğe (en düşük konum) sahip ilkeden gelen ayar uygulanır.

## <a name="sensitivity-labels-and-azure-information-protection"></a>Duyarlılık etiketleri ve Azure Information Protection

Windows bilgisayarlarında Microsoft 365 Uygulamaları etiketlerini kullanırken, Office uygulamalarına veya [Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2) istemcisine yerleşik olarak yer alan etiketlemeyi kullanabilirsiniz.

Yerleşik etiketler Azure Information Protection istemcisi tarafından Office bir eklenti kullanmamalarının nedeni, daha fazla kararlılık ve daha iyi performanstan yararlanmalarıdır. Ayrıca, gelişmiş sınıflayıcılar gibi en son özellikleri de desteklerler.

Varsayılan olarak, Azure Information Protection istemcisi yüklü olduğunda bu uygulamalarda yerleşik etiketleme kapalıdır. Bu varsayılan davranışı değiştirmek ve Office uygulamalarınız için yerleşik etiketleri kullanmak için bkz. Office Yerleşik etiketleme istemcisini ve [Azure Information Protection istemcisini kullanma](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-the-azure-information-protection-client).

Azure Information Protection istemcisini Office uygulamalarına bağlı ancak devre dışı bırakarak Azure Information Protection istemcisini duyarlılık etiketleriyle kullanma avantajından yararlanabilirsiniz:

- Şirket içinde depolanan hassas bilgileri keşfeden ve isteğe bağlı olarak bu içeriği etiketleyen bir tarayıcı

- Kullanıcıların tüm dosya türlerine etiket uygulayabilecekleri Dosya Gezgini'nde sağ tıklatma seçenekleri

- Metin, resim veya PDF belgelerinin şifrelenmiş dosyalarını görüntüleyen bir görüntüleyici

- Şirket içi dosyalarda hassas bilgileri bulmak ve bu dosyalarda etiketler ve şifrelemeler uygulamak veya kaldırmak için bir PowerShell modülü.

Azure Information Protection'ı yeni başladıysanız bkz[. Azure Information Protection belgelerinden](/azure/information-protection/rms-client/use-client#choose-your-windows-labeling-solution) Windows etiketlerin etiket çözümünü seçme.

### <a name="azure-information-protection-labels"></a>Azure Information Protection etiketleri

> [!NOTE]
> Azure portalında Azure Information Protection etiketleri için etiket yönetimi **31 Mart 2021'de kullanım dışıdır**. Resmi kullanımdan kullanımdan [kullanımdan kullanımdandan daha fazla bilgi için:](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179)

Kiracınız henüz birleşik etiketleme platformunda [değilse, duyarlılık](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform) etiketlerini kullanamadan önce birleşik etiketlemeyi etkinleştirmeniz gerekir. Yönergeler için bkz [. Azure Information Protection etiketlerini birleştirilmiş duyarlılık etiketlerine geçirme](/azure/information-protection/configure-policy-migrate-labels). 

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Duyarlılık etiketleri ve Microsoft Bilgi Koruması SDK

Duyarlılık etiketi bir belgenin meta verilerinde depolandığı için, üçüncü taraf uygulamalar ve hizmetler etiket dağıtımınıza destek olarak bu etiket meta verilerini okuyabilir ve yazabilir. Buna ek olarak, yazılım geliştiricileri [Microsoft Bilgi Koruması ve şifreleme](/information-protection/develop/overview#microsoft-information-protection-sdk) özelliklerini birden çok platformda tam olarak desteklemek için MICROSOFT BILGI KORUMASı SDK'yı kullanabilir. Daha fazla bilgi edinmek için Teknik [Posta Gönderisi blog'sinde Genel Community bakın](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Ayrıca, iş ortağı [çözümleriyle tümleştirilmiş olan iş ortağı çözümleri hakkında Microsoft Bilgi Koruması](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Dağıtım kılavuzu

Lisans bilgilerini, izinleri, dağıtım stratejisini, desteklenen senaryoların listesini ve son kullanıcı belgelerini içeren dağıtım planlama ve rehberlik için bkz. Duyarlılık [etiketleriyle çalışmaya başlama](get-started-with-sensitivity-labels.md).

Duyarlılık etiketlerini veri gizliliği düzenlemelerine uygun şekilde nasıl kullanabileceğinizi öğrenmek için bkz. Gizlilikle ilgili veri gizliliği düzenlemelerine uygun bilgi [Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).
