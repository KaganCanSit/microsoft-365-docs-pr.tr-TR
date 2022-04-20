---
title: Veri gizliliği düzenlemesine tabi bilgileri koruma
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Microsoft 365 güvenlik ve uyumluluk özelliklerini dağıtın ve kişisel bilgilerinizi koruyun.
ms.openlocfilehash: 0876cc1ff51b133e22d13b4c7fbc9a575db32d26
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943293"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemesine tabi bilgileri koruma

Veri gizliliği uyumluluk gereksinimlerini ve düzenlemelerini karşılamaya yardımcı olmak için aboneliğinizde bir dizi bilgi koruma denetimi kullanılabilir. Bunlar Arasında Genel Veri Koruma Yönetmeliği (GDPR), HIPAA-HITECH (Birleşik Devletler sağlık hizmetleri gizlilik yasası), California Tüketici Koruma Yasası (CCPA) ve Brezilya Veri Koruma Yasası (LGPD) bulunur.

Bu denetimler aşağıdaki çözüm alanlarındadır:

- Duyarlılık etiketleri
- Microsoft Purview Veri kaybı önleme (DLP)
- Microsoft Purview İleti Şifrelemesi
- Teams ve site erişim denetimleri

![Veri gizliliği düzenlemesine tabi kişisel bilgileri korumaya yönelik temel hizmetler.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Bu çözüm, veri gizliliği düzenlemelerine tabi bilgileri korumak için güvenlik ve uyumluluk özelliklerini açıklar. Microsoft 365 güvenlik özelliklerinin tam listesi için [Microsoft 365 güvenlik belgelerine bakın](../security/index.yml). Microsoft 365 uyumluluk özelliklerinin tam listesi için [bkz. Microsoft Purview belgeleri](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Bilgi koruma denetimlerini etkileyen veri gizliliği düzenlemeleri

Bilgi koruma denetimleriyle ilgili olabilecek veri gizliliği düzenlemelerinin örnek listesi aşağıda verilmiştir:

- GDPR Madde 5(1)(f))
- GDPR Makalesi (32)(1)(a)
- LGPD Makale 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Yukarıdakilerin her biri hakkında daha fazla bilgi için [veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama makalesine](information-protection-deploy-assess.md) bakın.

Bilgi koruması için veri gizliliği düzenlemeleri önerilir:

- Kayıplara veya yetkisiz erişime, kullanıma ve/veya iletimlere karşı koruma.
- Koruyucu mekanizmaların risk tabanlı uygulaması.
- Uygun yerlerde şifreleme kullanımı.

Kuruluşunuz, Microsoft 365 içeriği diğer uyumluluk gereksinimleri gibi başka amaçlarla veya iş nedenleriyle de korumak isteyebilir. Veri gizliliği için bilgi koruma şemanızı oluşturma işlemi genel bilgi koruma planlaması, uygulaması ve yönetimi kapsamında yapılmalıdır.

Microsoft 365'da bir bilgi koruma şemasını kullanmaya başlamanıza yardımcı olmak için, aşağıdaki bölümde Microsoft 365 ilgili özelliklerin ve iyileştirme eylemlerinin kısa bir listesi yer alır. Liste, veri gizliliği düzenlemeleri için geçerli olan özellikleri ve iyileştirme eylemlerini içerir. Ancak, eskisinin yerini büyük ölçüde alan daha yeni bir özellik varsa, listede eski teknolojiler yoktur. Örneğin, SharePoint ve OneDrive için Bilgi Hakları Yönetimi (IRM) listeye dahil değildir, ancak duyarlılık etiketleri dahil edilir.

## <a name="managing-information-protection-in-microsoft-365"></a>Microsoft 365'de bilgi korumasını yönetme

Microsoft [bilgi koruma çözümleri](../compliance/information-protection.md) Microsoft 365, Microsoft Azure ve Microsoft Windows genelinde bir dizi tümleşik özellik içerir. Microsoft 365 bilgi koruma çözümleri şunları içerir:

- [Hassas bilgi türleri](../compliance/sensitive-information-type-entity-definitions.md) ([veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama makalesinde](information-protection-deploy-assess.md) açıklanmıştır)
- [Duyarlılık etiketleri](../compliance/sensitivity-labels.md)
  - Hizmet/kapsayıcı düzeyi
  - İstemci tarafı/içerik düzeyi
  - SharePoint ve OneDrive bekleyen veriler için otomatikleştirilmiş
- Veri Kaybı Önleme (DLP)
- [Uç nokta veri kaybı önleme](../compliance/endpoint-dlp-learn-about.md)
- [Office 365 İleti Şifrelemesi yeni özellikleri (OME)](../compliance/ome.md) ve OME [Gelişmiş İleti Şifrelemesi](../compliance/ome-advanced-message-encryption.md)

Ayrıca, site ve kitaplık düzeyinde koruma, herhangi bir koruma şemasına dahil edilmesi gereken önemli mekanizmalardır.

Microsoft 365 dışındaki diğer bilgi koruma özellikleri hakkında bilgi için bkz:

- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Microsoft Purview Information Protection duyarlılık etiketleri, kullanıcıların üretkenliğini ve işbirliği yapma becerilerini engellemeden kuruluşunuzun verilerini sınıflandırmanıza ve korumanıza olanak sağlar.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 duyarlılık etiketleri.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Duyarlılık etiketleri için önkoşullar

Aşağıda vurgulanan duyarlılık etiketi tabanlı özelliklerden herhangi birini uygulamadan önce bu etkinlikleri tamamlayın:

1. Aşağıdakileri anlayın:
   - **İş gereksinimleri.** Kuruluşunuzda duyarlılık etiketleri uygulamak için iş nedenlerini belirleyin. Örneğin, bilgi koruması için veri gizliliği gereksinimleriniz.
   - **Duyarlılık etiketi özellikleri.** Duyarlılık etiketleme karmaşık hale gelebilir, bu nedenle başlamadan önce [duyarlılık etiketleri belgelerini](../compliance/sensitivity-labels.md) okuduğunuzdan emin olun.
   - **Hatırlamanız gereken önemli şeyler** Duyarlılık etiketleri Microsoft Purview uyumluluk portalında yönetilir, ancak hedefleme ve uygulama seçenekleri önemli ölçüde farklılık gösterir.
      - Siteler, gruplar ve Teams için kapsayıcı düzeyinde duyarlılık etiketleri vardır (ayarlar kapsayıcının içindeki içeriğe uygulanmaz). Bunlar bir site, grup veya Ekip sağlandığında bunları uygulayan kullanıcılara ve gruplara yayımlanır.
      - Etkin içerik için duyarlılık etiketleri vardır. Bunlar ayrıca, bunları el ile uygulayan veya aşağıdaki durumlarda otomatik olarak uygulanan kullanıcılara veya gruplara da yayımlanır:
        - Dosya, kullanıcının masaüstüne veya SharePoint sitesine açılır/düzenlenir/kaydedilir.
        - Bir e-posta taslağı oluşturulur ve gönderilir.
      - SharePoint ve OneDrive bekleyen dosyalara otomatik uygulama için duyarlılık etiketleri ve Exchange aracılığıyla aktarımda olan e-postalar vardır. Bunlar tüm siteleri veya belirli siteleri hedefler ve bu ortamlarda bekleyen dosyalara otomatik olarak uygulanır.

2. Geçmiş veya alternatif yöntemlerle geçerli duyarlılık etiketlemesini rasyonalize etme

   - Azure Information Protection

      Geçerli duyarlılık etiketleme düzeninin mevcut [azure Information Protection](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) etiketleme uygulamalarıyla mutabık kılınmış olması gerekebilir.
   - OME

      E-posta koruması için modern duyarlılık etiketlemesi kullanmayı planlıyorsanız ve OME gibi mevcut e-posta şifreleme yöntemleri mevcutsa, bunlar birlikte bulunabilir, ancak bunların uygulanması gereken senaryoları anlamanız gerekir. Modern duyarlılık etiket türü korumasını OME tabanlı korumayla karşılaştıran bir tablo içeren [Office 365 İleti Şifrelemesi yeni özelliklerine (](#office-365-message-encryption-ome-new-capabilities)OME) bakın.

3. Daha geniş bir bilgi koruma düzeniyle tümleştirmeyi planlayın. OME ile birlikte bulunmanın yanı sıra duyarlılık etiketleri, Microsoft Purview Veri Kaybı Önleme (DLP) ve Microsoft Defender for Cloud Apps gibi yan yana özellikler de kullanılabilir. Veri gizliliğiyle ilgili bilgi koruma hedeflerinize ulaşmak için bkz. [Verilerinizi Microsoft Purview ile](../compliance/information-protection.md) koruma.

4. Duyarlılık etiketi sınıflandırması ve denetim şeması geliştirme. Bkz. [Veri Sınıflandırma ve Duyarlılık Etiketi Taksonomisi](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Genel rehber

1. **Şema tanımı.** Etiketleri ve korumayı uygulamak için teknik özellikleri kullanmadan önce, bir sınıflandırma şeması tanımlamak için kuruluşunuz genelinde çalışın. Kişisel verilerin eklenmesini kolaylaştıran bir sınıflandırma şemanız zaten olabilir.
2. **Başlarken.** Uygulanacak etiketlerin sayısına ve adlarına karar vererek başlayın. Hangi teknolojinin kullanılacağı ve etiketlerin nasıl uygulanacağı konusunda endişelenmeden bu etkinliği gerçekleştirin. Bu şemayı şirket içinde ve diğer bulut hizmetlerinde bulunan veriler de dahil olmak üzere kuruluşunuz genelinde evrensel olarak uygulayın.
3. **Ek öneriler** İlkeleri, etiketleri ve koşulları tasarlarken ve uygularken şu önerileri göz önünde bulundurun:

   - **Mevcut sınıflandırma şemasını (varsa) kullanın.** Birçok kuruluş zaten veri sınıflandırmayı bir biçimde kullanıyor. Mevcut etiket şemasını dikkatle değerlendirin ve mümkünse olduğu gibi kullanın. Son kullanıcılarınız tarafından tanınabilen tanıdık etiketlerin kullanılması benimsemeyi yönlendirecektir.
   - **Küçük bir başlangıç.** Oluşturabileceğiniz etiket sayısıyla ilgili neredeyse hiçbir sınır yoktur. Ancak çok sayıda etiket ve alt etiket benimsemeyi yavaşlatabilir.
   - **Senaryoları ve kullanım örneklerini kullanın.** Kuruluşunuzdaki yaygın kullanım örneklerini belirleyin ve tabi olduğunuz veri gizliliği düzenlemelerinden türetilen senaryoları kullanın. Öngörülen etiket ve sınıflandırma yapılandırmasının pratikte çalışıp çalışmayacağını doğrulayın.
   - **Yeni bir etiket için her isteği sorgula.** Her senaryo veya kullanım örneğinin gerçekten yeni bir etikete ihtiyacı var mı yoksa zaten sahip olduğunuz etiketi kullanabilir misiniz? Etiket sayısını en düşük düzeyde tutmak benimsemeyi geliştirir.
   - **Anahtar departmanlar için alt etiketleri kullanın.** Bazı departmanların belirli etiketler gerektiren belirli gereksinimleri olacaktır. Bu etiketleri mevcut bir etikete alt etiketler olarak tanımlayın ve genel olarak değil, kullanıcı gruplarına atanan kapsamlı ilkeleri kullanmayı göz önünde bulundurun.
   - **Kapsamlı ilkeleri göz önünde bulundurun.** Kullanıcıların alt kümelerini hedefleyen ilkeler etiket aşırı yüklemesini engeller. Kapsamlı bir ilke, yalnızca ilgili departman için çalışan çalışanlara rol veya departmana özgü etiketler veya alt etiketler atamayı sağlar.
   - **Anlamlı etiket adları kullanın.** Etiket adları olarak jargon, standartlar veya kısaltmalar kullanmamaya çalışın. Benimsemeyi geliştirmek için son kullanıcıyla rezonansı olan adları kullanmayı deneyin. PII, PCI, HIPAA, LBI, MBI ve HBI gibi etiketleri kullanmak yerine İş Dışı, Genel, Genel, Gizli ve Çok Gizli gibi adları göz önünde bulundurun.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Siteler, gruplar ve ekipler için duyarlılık etiketleri oluşturma ve dağıtma

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalında</a> [duyarlılık etiketleri](../compliance/sensitivity-labels-teams-groups-sites.md) oluşturduğunuzda, artık bunları şu kapsayıcılara uygulayabilirsiniz:

- siteleri Microsoft Teams
- Microsoft 365 grupları (eski adıyla Office 365 grupları)
- siteleri SharePoint

Bu kapsayıcılardaki içeriğin korunmasına yardımcı olması için aşağıdaki etiket ayarlarını kullanın:

- Microsoft 365 grup bağlantılı Teams sitelerinin gizliliği (genel veya özel)
- Dış kullanıcı erişimi
- Yönetilmeyen cihazlardan erişim

Veri gizliliği için, hassas kişisel verilerle içerik depolamak için kullanılacak kapsayıcıların dış paylaşımını önlemek için, verileri içeren dosyaları özel olarak işaretleyin ve yönetilen cihazlar gerektirir.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>İçerik için duyarlılık etiketleri oluşturma ve dağıtma

Dosyalara uygulanan duyarlılık etiketleri, içeriklerini şifrelemenize, içeriği filigranlayıp Office uygulama içeriği için Outlook ve Web üzerinde Office gibi diğer denetimleri tanımlamanıza olanak tanır.

Kuruluşunuzun verilerini duyarlılık etiketleriyle korumaya başlamaya hazır olduğunuzda:

1. **Etiketleri oluşturun.** Farklı duyarlılık düzeyleri için duyarlılık etiketlerinizi kuruluşunuzun sınıflandırma taksonomisine göre oluşturun ve adlandırın. Sınıflandırma taksonomisi geliştirme hakkında daha fazla bilgi için [bkz. Veri Sınıflandırması ve Duyarlılık Etiketi Taksonomisi teknik incelemesi](https://aka.ms/dataclassificationwhitepaper).
2. **Her etiketin neler yapabileceğini tanımlayın.** Her etiketle ilişkilendirılmasını istediğiniz koruma ayarlarını yapılandırın. Örneğin, daha düşük duyarlılık içeriğinin (örneğin, "Genel" etiketi) yalnızca bir üst bilgi veya alt bilginin uygulanmasını, daha yüksek duyarlılık içeriğinin (örneğin , "Gizli" etiket) bir filigranı olması ve şifrelemenin etkinleştirilmesini isteyebilirsiniz.
3. **Etiketleri yayımlayın.** Duyarlılık etiketleriniz yapılandırıldıktan sonra bir etiket ilkesi kullanarak yayımlayın. Etiketlerin hangi kullanıcı ve gruplara sahip olması gerektiğine ve hangi ilke ayarlarının kullanılacağına karar verin. Tek bir etiket yeniden kullanılabilir. Bir kez tanımlarsınız ve ardından farklı kullanıcılara atanan çeşitli etiket ilkelerine ekleyebilirsiniz.

Duyarlılık etiketlerini <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalından</a> yayımladığınızda, kullanıcılar içeriği oluşturulduklarında veya düzenlendiklerinde sınıflandırmak ve korumak için [Office uygulamalarda](../compliance/sensitivity-labels-office-apps.md) görünmeye başlarlar.

![Microsoft 365'da duyarlılık etiketi dağıtım akışı.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Veri gizliliği için, e-postaya veya hassas kişisel bilgiler içeren içeriğe şifreleme ve diğer kuralları içeren bir duyarlılık etiketini el ile uygularsınız.

> [!NOTE]
> E-postaya şifreleme etkinleştirilmiş duyarlılık etiketlerinin OME ile çakışan bazı işlevleri vardır. Bkz [. OME ve duyarlılık etiketleriyle güvenli e-posta senaryoları karşılaştırması](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Kullanıcılar belgeleri düzenlerken veya e-posta oluştururken istemci tarafı otomatik etiketleme

Duyarlılık etiketi oluşturduğunuzda, belirttiğiniz koşullarla eşleştiğinde bu etiketi e-posta da dahil olmak üzere içeriğe [otomatik olarak atayabilirsiniz](../compliance/apply-sensitivity-label-automatically.md) .

İçeriklere duyarlılık etiketlerini otomatik olarak uygulayabilme özelliği önemlidir çünkü:

- Sınıflandırmalarınızın her birini kullanmak için kullanıcılarınızı eğitmek zorunda değilsiniz.
- Tüm içeriği doğru sınıflandırmak için kullanıcılara güvenmeniz gerekmez.
- Kullanıcıların artık ilkeleriniz hakkında bilgi sahibi olması gerekmez; bunun yerine çalışmalarına odaklanabilir.

Otomatik etiketleme, kullanıcılara etiket önermenin yanı sıra otomatik olarak etiket uygulamayı destekler. Ancak her iki durumda da kullanıcı, içeriğin doğru etiketlenmesine yardımcı olmak için etiketi kabul etmeye veya reddetmeye karar verir.

Belge kaydedilmeden önce bile etiket uygulanabileceğinden, bu istemci tarafı etiketlemesi belgeler için çok az gecikmeye neden olur. Ancak tüm istemci uygulamaları otomatik etiketlemeyi desteklemez. Bu özellik, Azure Information Protection birleşik etiketleme istemcisi ve [Office uygulamalarının bazı sürümleri](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) tarafından desteklenir.

Yapılandırma yönergeleri için bkz. [Office uygulamaları için otomatik etiketlemeyi yapılandırma](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Veri gizliliği için hassas kişisel bilgiler içeren içerik için duyarlılık etiketlerini otomatik olarak uygularsınız.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>İçerik zaten kaydedildiğinde hizmet tarafı otomatik etiketleme

Bu yöntem, duyarlılık etiketleriyle otomatik sınıflandırma olarak adlandırılır. Bekleyen veriler (SharePoint ve OneDrive belgeler için) ve aktarımdaki veriler (Exchange tarafından gönderilen veya alınan e-postalar için) için otomatik etiketleme olarak da anıldığını duyabilirsiniz. Exchange için bekleyen posta kutularına e-postalar dahil değildir.

Bu etiketleme kullanıcı uygulaması yerine hizmetin kendisi tarafından uygulandığından, kullanıcıların hangi uygulamalara ve hangi sürüme sahip olduğu konusunda endişelenmeniz gerekmez. Sonuç olarak, bu özellik kuruluşunuz genelinde hemen kullanılabilir ve büyük ölçekte etiketleme için uygundur. Kullanıcı etiketleme işlemiyle etkileşim kurmadığından otomatik etiketleme ilkeleri önerilen etiketlemeyi desteklemez. Bunun yerine yönetici, etiketi uygulamadan önce içeriğin doğru etiketlenmesine yardımcı olmak için ilkeleri simülasyon modunda çalıştırır.

Yapılandırma yönergeleri için bkz. [SharePoint, OneDrive ve Exchange için otomatik etiketleme ilkelerini yapılandırma](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

İlgi duyulan sitelerdeki veri gizliliği için hassas kişisel bilgiler içeren içeriğin otomatik olarak şifrelenmesi için duyarlılık etiketleri gönderebilirsiniz.

## <a name="data-loss-prevention"></a>Veri kaybı önleme

Hem şirket içinde hem de dışarıdan kişisel bilgiler içeren verilerin paylaşılması gibi riskli, yanlışlıkla veya uygunsuz paylaşımları algılamak, uyarmak ve engellemek için Microsoft 365 [veri kaybı önlemeyi (DLP)](../compliance/dlp-learn-about-dlp.md) kullanabilirsiniz.

DLP şunları yapmanızı sağlar:

- Riskli paylaşım etkinliklerini belirleme ve izleme.
- Doğru kararları almaları için bağlam içi rehberlikle kullanıcıları eğitin.
- Üretkenliği engellemeden içerik üzerinde veri kullanım ilkelerini zorunlu kılma.
- Verileri paylaşıldığında algılamak ve korumak için sınıflandırma ve etiketleme ile tümleştirin.

### <a name="supported-workloads-for-dlp"></a>DLP için desteklenen iş yükleri

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalındaki</a> bir DLP ilkesiyle Exchange Online, SharePoint, OneDrive ve Microsoft Teams gibi Microsoft 365 birçok konumdaki hassas öğeleri tanımlayabilir, izleyebilir ve otomatik olarak koruyabilirsiniz.

Örneğin, herhangi bir OneDrive sitesinde depolanan kredi kartı numarası içeren herhangi bir belgeyi tanımlayabilir veya yalnızca belirli kişilerin OneDrive sitelerini izleyebilirsiniz.

Ayrıca Excel, PowerPoint ve Word'ün yerel olarak yüklenmiş sürümlerinde hassas öğeleri izleyebilir ve koruyabilirsiniz. Bu, hassas öğeleri tanımlama ve DLP ilkeleri uygulama özelliğini içerir. DLP, kişiler bu Office uygulamalarından içerik paylaştığında sürekli izleme sağlar.

> [!div class="mx-imgBorder"]
> ![DLP için desteklenen iş yükleri.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Bu şekilde, kişisel verileri koruyan bir DLP örneği gösterilmektedir.

> [!div class="mx-imgBorder"]
> ![DLP kullanarak kişisel verileri koruma örneği.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP, sistem durumu kaydı içeren bir belgeyi veya e-postayı tanımlamak için kullanılır ve ardından bu belgeye erişimi otomatik olarak engeller veya e-postanın gönderilmesini engeller. DLP daha sonra alıcıya bir ilke ipucu bildirir ve son kullanıcıya ve yöneticiye bir uyarı gönderir.

### <a name="planning-for-dlp"></a>DLP planlama

DLP ilkelerinizi planlama:

- İş gereksinimleriniz.

- [Veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama makalesinde](information-protection-deploy-assess.md) açıklandığı gibi kuruluşun risk tabanlı değerlendirmesi.

- Veri gizliliğinin yerinde veya planlanmasında diğer bilgi koruma ve idare mekanizmaları.

- Değerlendirmenize bağlı olarak kişisel veriler için tanımladığınız hassas bilgi türleri [, veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama makalesinde](information-protection-deploy-assess.md) açıklandığı gibi çalışır. DLP ilkesi koşulları hem hassas bilgi türlerini hem de bekletme etiketlerini temel alabilir.

- Bekletme etiketleri, DLP koşullarını belirtmeniz gerekir. Daha fazla [bilgi için kuruluşunuzun veri gizliliği düzenlemesine tabi idare bilgileri](information-protection-deploy-govern.md) makalesine bakın.

- Kuruluştaki birinin hassas bilgi türlerindeki, bekletme etiketlerindeki, yönetmeliklerdeki ve uyumluluk ilkelerindeki değişiklikler için ilkeleri çalıştırmasını ve ayarlamasını gerektiren sürekli DLP ilke yönetimi.

Duyarlılık etiketleri DLP ilke koşullarında kullanılamasa da, erişimi önlemeye yönelik belirli koruma senaryolarına yalnızca hassas bilgi türlerine göre otomatik olarak uygulanabilen duyarlılık etiketleriyle ulaşılabilir. Sağlam duyarlılık etiketlemesi varsa, korumayı artırmak için DLP'nin kullanılıp kullanılmayacağını göz önünde bulundurun çünkü:

  - DLP, dosyaların paylaşılmasını engelleyebilir. Duyarlılık etiketleri yalnızca erişimi engelleyebilir.

  - DLP kurallar, koşullar ve eylemler açısından daha ayrıntılı denetim düzeylerine sahiptir.

  - DLP ilkeleri Teams sohbet ve kanal iletilerine uygulanabilir. Duyarlılık etiketleri yalnızca belgelere ve e-postalara uygulanabilir.


### <a name="dlp-policies"></a>DLP ilkeleri

DLP ilkeleri Microsoft Purview uyumluluk portalında yapılandırılır ve koruma düzeyini, ilkenin aradığı hassas bilgi türünü ve hedef iş yüklerini belirtir. Temel bileşenleri korumayı ve veri türlerini tanımlamaktır.

> [!div class="mx-imgBorder"]
> ![Microsoft 365'de DLP ilkesi yapılandırması.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

GDPR farkındalığı için örnek bir DLP ilkesi aşağıda verilmiştir.

![GDPR farkındalığı için örnek DLP ilkesi.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

DLP ilkeleri oluşturma ve uygulama hakkında daha fazla bilgi için [bu makaleye](../compliance/create-test-tune-dlp-policy.md) bakın.

### <a name="protection-levels-for-data-privacy"></a>Veri gizliliği için koruma düzeyleri

Aşağıdaki tabloda DLP kullanarak korumayı artırmaya yönelik üç yapılandırma listelemektedir.

![DLP ile veri gizliliği koruma düzeyleri.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

İlk yapılandırma olan Farkındalık, veri gizliliği düzenlemelerine yönelik uyumluluk gereksinimlerini karşılamak için başlangıç noktası ve minimum koruma düzeyi olarak kullanılabilir.

> [!NOTE]
> Koruma düzeyleri arttıkça, kullanıcıların bilgileri paylaşma ve bilgilere erişme yeteneği bazı durumlarda azalır ve üretkenliğini veya günlük görevleri tamamlama becerisini etkileyebilir.

Çalışanlarınızın koruma düzeylerini artırırken daha güvenli bir ortamda üretken olmaya devam etmelerine yardımcı olmak için, zaman ayırarak onları yeni güvenlik ilkeleri ve yordamları konusunda eğitin.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>DLP ile duyarlılık etiketleri kullanma örneği

Duyarlılık etiketleri, yüksek düzeyde düzenlenmiş bir ortamda veri gizliliği sağlamak için DLP ile birlikte çalışabilir. Tümleşik dağıtımın temel adımları şunlardır:

1. Veri gizliliği için mevzuat ve diğer iş gereksinimleri belgelenmiştir.
2. Hedef veri kaynakları, türleri ve sahipliği, veri gizliliği endişelerine göre karakterize edilir.
3. Gereksinimleri ele almak ve veri gizliliği etkin noktalarını korumak ve yönetmek için genel bir strateji oluşturulur.
4. Veri gizliliği denetim stratejisini ele almak için aşamalı bir eylem planı uygulanır.

Bu öğeler belirlendikten sonra hassas bilgi türlerini, duyarlılık etiketleme taksonominizi ve DLP ilkelerini birlikte kullanabilirsiniz. Bu şekilde bir örnek gösterilmektedir.

> [!div class="mx-imgBorder"]
> ![DLP ile çalışan duyarlılık etiketleri örneği.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Bu görüntünün daha büyük bir sürümünü görün](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Aşağıda, şekilde gösterildiği gibi DLP ve duyarlılık etiketlerini birlikte kullanan bazı veri koruma senaryoları yer alır.

| Senaryo | Işlem |
|:-------|:-----|
| A | <ol><li>İçeriğin duyarlılık etiketleri, yönetici tarafından el ile veya otomatik uygulamadan içeriğe ve e-postaya yönelik kullanıcılara ve gruplara yayımlanır. </li><li>A kullanıcısı, içerikle etkileşim kurarken etiketleri el ile veya otomatik olarak uygular; şifreleme veya diğer ayarlar uygulanır. </li><li>A kullanıcısı, konuk kullanıcı olan B Kullanıcısına korumalı bir e-posta veya dosya gönderir. </li></ol> |
| B | Yönetici tarafından A Kullanıcısına yayımlanan DLP ilkesi, A Kullanıcısının E-postayı ve/veya dosyayı B Kullanıcısına göndermesini engeller. |
| C |  "Sahip konukları davet edemiyor" ayarına sahip duyarlılık etiketi, Teams ekibi veya SharePoint sitesi sağlayan A Kullanıcısı'na yayımlanır. Sitenin başka bir kullanıcısı, B kullanıcısı ile bir dosyayı seçerek paylaşmayı dener, ancak DLP bunu engeller. |
| D | Otomatik uygulamadan siteye içerik için duyarlılık etiketi bir veya daha fazla sitede yayımlanarak başka bir koruma katmanı sağlanır ve bu da korumalı bir siteyle sonuçlanır. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Office 365 İleti Şifrelemesi (OME) yeni özellikleri

İnsanlar genellikle hasta sağlığı bilgileri veya müşteri ve çalışan bilgileri gibi hassas öğeleri değiştirmek için e-posta kullanır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyebilmesine yardımcı olur.

[OME](../compliance/ome.md) ile kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli iletiler gönderebilir ve alabilirsiniz. OME, Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. OME, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyebilmesine yardımcı olur.

Veri gizliliği için, hassas öğeler içeren iç iletileri korumak için OME kullanırsınız. Office 365 İleti Şifrelemesi, Azure Information Protection'nin bir parçası olan Microsoft Azure Rights Management (Azure RMS) üzerinde oluşturulmuş bir çevrimiçi hizmettir. Bu, e-postanızın güvenliğini sağlamaya yardımcı olmak için şifreleme, kimlik ve yetkilendirme ilkelerini içerir. İletileri, hak yönetimi şablonlarını, İletme seçeneğini ve yalnızca şifrele seçeneğini kullanarak şifreleyebilirsiniz.

Bu korumayı uygulamak için posta akışı kuralları da tanımlayabilirsiniz. Örneğin, belirli bir alıcıya gönderilen tüm iletilerin şifrelenmesini gerektiren veya konu satırında belirli anahtar sözcükler içeren bir kural oluşturabilir ve ayrıca alıcıların iletinin içeriğini kopyalayamaz veya yazdıramazsınız.

Ayrıca, OME [Gelişmiş İleti Şifrelemesi](../compliance/ome-advanced-message-encryption.md) , dış alıcılar ve şifrelenmiş e-postalara erişimleri üzerinde daha esnek denetimler gerektiren uyumluluk yükümlülüklerini karşılamanıza yardımcı olur. Microsoft 365'da OME Gelişmiş İleti Şifrelemesi ile, hassas bilgi türlerini algılayan otomatik ilkelerle kuruluş dışında paylaşılan hassas e-postaları denetleyebilirsiniz.

Veri gizliliği için, e-postayı bir dış tarafla paylaşmanız gerekiyorsa, son kullanma tarihi belirtebilir ve iletileri iptal edebilirsiniz. Yalnızca dış alıcılara gönderilen iletiler için iptal edebilir ve son kullanma tarihi ayarlayabilirsiniz.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>OME ve duyarlılık etiketleriyle güvenli e-posta senaryoları karşılaştırması

Şifreleme ile e-postaya uygulanan OME ve duyarlılık etiketlerinin bazı çakışmaları vardır, bu nedenle bu tabloda gösterildiği gibi hangi senaryolara uygulanabileceğini anlamak önemlidir.

| Senaryo | Duyarlılık Etiketleri | OME |
|:-------|:-----|:-------|
| dahili + iş ortakları <br> İç kullanıcılar ve güvenilir iş ortakları arasında güvenli iletişim kurma ve işbirliği yapma | Öneri – tamamen özelleştirilmiş sınıflandırma ve koruma özelliklerine sahip etiketler | Evet – Sınıflandırma olmadan yalnızca şifreleme veya İletme koruması |
| Dış taraflar <br> Tüm dış/tüketici kullanıcılarla güvenli iletişim kurma ve işbirliği yapma | Evet – etiketteki alıcıları önceden tanımla | Öneri – alıcıları temel alan tam zamanında koruma |
| Süre sonu/iptali olan dahili + iş ortakları <br> Süre sonu ve iptal ile iç kullanıcılar ve güvenilir iş ortaklarıyla posta ve içerik erişimini denetleme | Öneri - erişim süresiyle tamamen özelleştirilmiş koruma, kullanıcı dosyaları el ile izleyebilir ve iptal edebilir | Hayır – iç posta için iptal veya süre sonu yok |
| Süre sonu/iptali olan dış taraflar <br> Son kullanma tarihi ve iptali olan dış/tüketici kullanıcılarla posta ve içerik erişimini denetleme | Evet – kullanıcı dosyaları el ile izleyebilir | Öneri (E5) – yönetici Güvenlik & Uyumluluk Merkezi'nden gelen postaları iptal edebilir |
| Otomatik etiketleme <br> Kuruluş, belirli hassas içeriğe ve/veya belirli alıcılara sahip postaları/ekleri otomatik olarak korumak istiyor | Öneri (E5) - Exchange ve Outlook istemcilerinde otomatik etiketleme, posta akışı kurallarını ve DLP ilkesini genişletiyor | Evet - posta akışı kuralları ve DLP ilkesi ile Yalnızca şifrele veya İletme koruması |
||||

Bu iki yöntem arasında son kullanıcı ve yönetici deneyimlerinde de farklılıklar olacaktır.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Son derece hassas veriler için koruma ile Teams

kişisel verileri Teams'da veri gizliliği düzenlemelerine tabi olarak depolamayı planlayan kuruluşlar için bkz. Ayrıntılı yönergeler ve yapılandırma adımları sağlayan [bir ekibi güvenlik yalıtımıyla](secure-teams-security-isolation.md) yapılandırma:

- Kimlik ve cihaz erişimi
- Özel ekip oluşturma
- Temel alınan ekip sitesi izinlerinin kilitlenmesi
- Şifrelemeli grup tabanlı duyarlılık etiketi
