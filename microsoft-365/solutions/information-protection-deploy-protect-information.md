---
title: Veri gizliliği düzenlemeye tabi bilgileri koruma
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
description: Güvenlik Microsoft 365 uyumluluk özelliklerini dağıtın ve kişisel bilgilerinizi koruyun.
ms.openlocfilehash: 2739da0b5e9c4896b65751c63d9b2e5f3b026a2e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012820"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemeye tabi bilgileri koruma

Aboneliğinize, veri gizliliği uyumluluğu  ihtiyaçlarını ve düzenlemelerini karşılamak için bir dizi bilgi koruma denetimi kullanılabilir. Bunlar Genel Veri Koruma Yönetmeliği (GDPR), HIPAA-HITECH (ABD sağlık hizmetleri gizlilik yasası), California Tüketici Koruma Yasası (CCPA) ve Brezilya Veri Koruma Yasası (LGPD)dır.

Bu denetimler aşağıdaki çözüm alanları içindedir:

- Duyarlılık etiketleri
- Veri kaybı önleme (DLP)
- Office şifreleme (OME)
- Teams ve sitelere erişim denetimleri

![Kişisel bilgileri korumak için veri gizlilik düzenlemesi konularını temel alan hizmetler.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Bu çözüm, veri gizliliği düzenlemelerine tabi bilgileri korumaya ilişkin güvenlik ve uyumluluk özelliklerini açıklar. Güvenlik özelliklerinin tam listesi için Microsoft 365 belgelerine Microsoft 365 [bakın](../security/index.yml). Uyumluluk belgelerinin uyumluluk özelliklerinin tam listesi Microsoft 365 için uyumluluk [Microsoft 365 bakın](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Bilgi koruma denetimlerini etkileyen veri gizliliği düzenlemeleri

Aşağıda, bilgi koruma denetimleriyle ilişkili olacak veri gizliliği düzenlemelerinin örnek bir listesi ve gösterilmiştir:

- GDPR Makale 5(1)(f))
- GDPR Makalesi (32)(1)(a)
- LGPD Makale 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Yukarıdakilerin [her biri hakkında daha fazla bilgi için veri gizliliği](information-protection-deploy-assess.md) risklerini değerlendirme ve hassas öğeleri belirleme makalesine bakın.

Bilgi koruması için veri gizliliğiyle ilgili düzenlemeler önerilir:

- Kayıp veya yetkisiz erişim, kullanım ve/veya iletimlere karşı koruma.
- Koruyucu mekanizmalar için risk tabanlı uygulama.
- Uygun olduğunda şifrelemenin kullanımı.

Ayrıca, organizasyonunız diğer uyumluluk Microsoft 365 veya ticari nedenlerle bu içeriği korumak da istiyor olabilir. Veri gizliliği için bilgi koruma düzeninizi oluşturma, genel bilgi koruma planlaması, uygulama ve yönetiminin bir parçası olarak yapılabilir.

Web'de bilgi koruma düzenini Microsoft 365 yardımcı olmak için, aşağıdaki bölümde ilgili becerilerin kısa bir listesi ve bu özelliklere yönelik iyileştirme Microsoft 365. Bu liste, veri gizliliği düzenlemeleri için geçerli olan özellikler ve geliştirme eylemleri içerir. Ancak, daha eski olandan daha eski olandan daha yeni bir özellik varsa, bu liste eski teknolojileri içermemektedir. Örneğin, daha fazla bilgi ve SharePoint IRM için Bilgi Hakları Yönetimi OneDrive, ancak duyarlılık etiketleri listeye dahil değildir.

## <a name="managing-information-protection-in-microsoft-365"></a>Web'de bilgi korumasını Microsoft 365

Microsoft [bilgi koruma çözümleri](../compliance/information-protection.md) yazılım, güvenlik özellikleri ve Microsoft Microsoft 365 Microsoft Azure bir dizi tümleşik Windows. Bu Microsoft 365, bilgi koruma çözümleri şunlardır:

- [Hassas bilgi türleri](../compliance/sensitive-information-type-entity-definitions.md) (veri gizliliği [risklerini değerlendirme ve hassas öğeleri tanımlama makalesinde açıklanmıştır)](information-protection-deploy-assess.md)
- [Duyarlılık etiketleri](../compliance/sensitivity-labels.md)
  - Hizmet/kapsayıcı düzeyi
  - İstemci tarafı/içerik düzeyi
  - Veri kaynağında ve veri kaynağında SharePoint otomatik OneDrive
- Veri Kaybı Önleme (DLP)
- [Microsoft 365 uç noktası veri kaybını önleme](../compliance/endpoint-dlp-learn-about.md)
- [Office 365 İleti Şifrelemesi özellikleri (OME) ve OME Gelişmiş](../compliance/ome.md) İleti [Şifrelemesi'ne sahip olun](../compliance/ome-advanced-message-encryption.md)

Buna ek olarak, site ve kitaplık düzeyinde koruma, herhangi bir koruma düzenine dahil etmek için önemli mekanizmalardır.

Dış veri koruma özellikleri hakkında daha fazla bilgi Microsoft 365 bkz:

- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Windows Koruma](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Microsoft Bilgi Koruması çerçevesine gelen duyarlılık etiketleri, kullanıcıların üretkenliğini ve işbirliği yapma yeteneğini engellemeden kuruluş verilerinizi sınıflandırmanıza ve korumanıza olanak sağlar.

> [!div class="mx-imgBorder"]
> ![Metindeki duyarlılık Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Duyarlılık etiketlerinin önkoşulları

Aşağıda vurgulanan duyarlılık etiket tabanlı özelliklerden herhangi birini uygulamadan önce bu etkinlikleri gerçekleştirin:

1. Aşağıdaki bilgileri anlıyoruz:
   - **İş gereksinimleri.** Kuruluşta duyarlılık etiketleri uygulamak için iş nedenlerini oluşturma. Örneğin, bilgi koruması için veri gizliliği gereksinimleriniz olabilir.
   - **Duyarlılık etiketi özellikleri.** Duyarlılık etiketleme karmaşık olabilir, bu nedenle başlamadan önce duyarlılık etiketleri [belgelerini okuduğundan](../compliance/sensitivity-labels.md) emin olun.
   - **Anımsayacak önemli şeyler** Duyarlılık etiketleri Microsoft Uyumluluk yönetim merkezinden yönetilir, ancak hedef ve uygulama seçenekleri önemli ölçüde değişiklik gösterir.
      - Siteler, gruplar ve kapsayıcı düzeyinde Teams duyarlılık etiketleri vardır (ayarlar kapsayıcının içindeki içeriğe geçerli değildir). Bunlar, bir site, grup veya Ekip sağlandıklarında bunları uygulayan kullanıcılara ve gruplara yayımlanır.
      - Etkin içerik için duyarlılık etiketleri var. Bunlar ayrıca el ile uygulanan veya şu olduğunda otomatik olarak uygulanan kullanıcılara veya gruplara da yayımlanır:
        - Dosya kullanıcının masaüstünde veya SharePoint sitesinde açılır/SharePoint.
        - Bir e-posta taslak olarak taslağı hazırlar ve gönderilir.
      - Belirli bir süre içinde kalan dosyalara otomatik uygulama için duyarlılık SharePoint OneDrive e-postaların yanı sıra Exchange. Bunlar tüm sitelere veya belirli sitelere hedeflenir ve bu ortamlardaki dosyalara otomatik olarak uygulanır.

2. Geçerli duyarlılık etiketlemeyi eski yöntemlerle veya alternatif yöntemlerle rasyonelleştirin

   - Azure Information Protection

      Geçerli duyarlılık etiketleme şemasının mevcut Azure Information Protection etiketleme uygulamasıyla bir araya [geçirilmesi](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) gerekiyor olabilir.
   - OME

      E-posta koruması için modern duyarlılık etiketlemeyi ve OME gibi mevcut e-posta şifreleme yöntemlerini kullanmayı planlıyorsanız bu yöntemler birlikte kullanılabilir, ancak bu yöntemlerden hangisinin uygulanmalıdır senaryolarını anlanız gerekir. Modern Office 365 İleti Şifrelemesi etiket türü korumasını OME tabanlı koruma ile karşılaştıran bir tablo içeren yeni özelliklere [(OME)](#office-365-message-encryption-ome-new-capabilities) bakın.

3. Daha geniş bir bilgi koruma düzeniyle tümleştirmeyi plan edin. OME ile birlikte kullanılabilirlik özelliğinde, duyarlılık etiketleri Microsoft 365 kaybı önleme (DLP) ve Bulut Uygulamaları için Microsoft Defender gibi özelliklerle birlikte kullanılabilir. Veri [Microsoft Bilgi Koruması koruma Microsoft 365](../compliance/information-protection.md) ulaşmak için aşağıdaki diğer bilgilere bakın.

4. Duyarlılık etiketi sınıflandırma ve denetim düzeni geliştirin. Bkz [. Veri Sınıflandırma ve Duyarlılık Etiketi Taksonomisi](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Genel rehber

1. **Şema tanımı.** Etiket ve koruma uygulamak üzere teknik özellikleri kullanmadan önce, bir sınıflandırma şeması tanımlamak için tüm kuruluşlarıyla birlikte çalışabilirsiniz. Zaten kişisel verileri eklemenizi kolaylaştıran bir sınıflandırma şemanız olabilir.
2. **Başlarken.** uygulanacak etiketlerin sayısına ve adlarına karar vererek başlayabilirsiniz. Bu etkinliği, hangi teknolojiyi ve etiketlerin nasıl uygulanacakları konusunda kaygılanmadan kullanın. Bu şemayı, şirket içinde ve diğer bulut hizmetlerde bulunan veriler de dahil olmak üzere, genel olarak tüm kuruluş genelinde uygulayabilirsiniz.
3. **Ek öneriler** İlkeleri, etiketleri ve koşulları tasarlar ve sunarken, aşağıdaki önerileri dikkate a göz önünde bulundurabilirsiniz:

   - **Varolan sınıflandırma şemasını (varsa) kullanın.** Birçok kuruluş zaten bazı formlarda veri sınıflandırması kullanıyor. Varolan etiket şemasını dikkatle değerlendirin ve mümkünse, bunu olduğu gibi kullanın. Son kullanıcılarınız tarafından tanınabilir tanıdık etiketlerin kullanımı benimsemeyi zorlar.
   - **Küçük başlat'a.** Oluşturabilirsiniz etiket sayısında hemen hiçbir sınırlama yoktur. Ancak, çok fazla sayıda etiket ve alt etiket benimsemeyi yavaşlatabilirsiniz.
   - **Senaryoları ve kullanım durumlarını kullanın.** Organizasyonuz içinde yaygın kullanım durumlarını tanımlama ve konu a kapsamındaki veri gizliliği düzenlemelerinden türetilen kullanım senaryolarını belirleme. Sınıflandırılmış etiket ve sınıflandırma yapılandırmasının uygulamada çalışsa da çalışmadığnı doğrulayın.
   - **Her yeni etiket isteğini sorun.** Her senaryo veya kullanım durumu için gerçekten yeni bir etiket gerekiyor mu yoksa sahip olduğunuz etiketi kullanabilir misiniz? Etiketlerin sayısını en düşük düzeyde tutmak benimsemeyi geliştirin.
   - **Önemli departmanlar için alt etiketler kullanın.** Bazı departmanların belirli etiketler gerektiren belirli ihtiyaçları olur. Bu etiketleri var olan bir etiket için alt etiket olarak tanımlayın ve genel olarak değil de kullanıcı gruplarına atanan kapsamı olan ilkeleri kullanmayı göz önünde bulundurabilirsiniz.
   - **Kapsamları göz önünde bulundurarak ilkeleri göz önünde bulundurarak.** Kullanıcıların alt kümeleri tarafından hedeflenen ilkeler etiket aşırı yükü önlemektedir. Kapsamı olan bir ilke, yalnızca ilgili bölüm için çalışan çalışanlara rol veya departmana özgü etiketler ya da alt etiketler atamayı sağlar.
   - **Anlamlı etiket adları kullanın.** Jargon, standartlar veya kısaltmaları etiket adı olarak kullanmamaya çalış. Benimsemeyi geliştirmek için son kullanıcıyla aynı adı kullanmaya çalış. PII, PCI, HIPAA, LBI, MBI ve HBI gibi etiketler kullanmak yerine, İş Dışı, Genel, Genel, Gizli ve Çok Gizli gibi adları dikkate alın.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Siteler, gruplar ve ekipler için duyarlılık etiketleri oluşturma ve dağıtma

İçerik [İçerikleri'sinde](../compliance/sensitivity-labels-teams-groups-sites.md) duyarlılık <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>, şimdi bunları şu kapsayıcılara uygulayabilirsiniz:

- Microsoft Teams siteleri
- Microsoft 365 grupları (eski adı Office 365 grupları)
- SharePoint siteleri

Bu kapsayıcıların içeriğinin korunmasına yardımcı olmak için aşağıdaki etiket ayarlarını kullanın:

- Grup bağlantılı web sitelerinin Microsoft 365 (genel veya özel) Teams
- Dış kullanıcı erişimi
- Unmanaged cihazlarından erişim

Veri gizliliği için, hassas kişisel verilerin depolanmasında kullanılacak kapsayıcılarda dış paylaşımı önlemek için verileri içeren dosyaları özel olarak ve yönetilen cihazlar gerektirmeyi seçin.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>İçerik için duyarlılık etiketleri oluşturma ve dağıtma

Dosyalara uygulanan duyarlılık etiketleri, bu etiketlerin içeriğini şifrelemenizi, içeriği filigranla filigran oluşturmanizi ve Office uygulamaları içeriği için Outlook ve Web üzerinde Office.

Kuruluş verilerinizi duyarlılık etiketleriyle korumaya başlamaya hazır olduğunda:

1. **Etiketleri oluşturun.** Duyarlılık etiketlerinizi oluşturmak ve farklı içerik duyarlılık düzeyleri için kuruluş sınıflandırma taksonomisi'ne göre adlar oluşturun. Sınıflandırma taksonomisi geliştirme hakkında daha fazla bilgi için Veri [Sınıflandırması ve Duyarlılık Etiketi Taksonomisi teknik belgesine bakın](https://aka.ms/dataclassificationwhitepaper).
2. **Her etiketin neler yapalını tanımlayın.** Her etiketle ilişkili olarak istediğiniz koruma ayarlarını yapılandırabilirsiniz. Örneğin, daha düşük duyarlılık içeriğinin (örneğin "Genel" etiketi) yalnızca bir üst bilgi veya alt bilgi uygulanması gerekirken, daha yüksek duyarlılık içeriğinin (örneğin, "Gizli" etiketi) bir filigranı olması ve şifrelemenin etkinleştirilmesi gerekir.
3. **Etiketleri yayımlama.** Duyarlılık etiketleriniz yapılandırıldıktan sonra, bunları bir etiket ilkesi kullanarak yayımlayın. Etiketlere sahip olması gereken kullanıcı ve gruplara ve hangi ilke ayarlarının gerektiğine karar verin. Tek bir etiket yeniden kullanılabilir. Bir kez tanımlar ve ardından bunu farklı kullanıcılara atanmış çeşitli etiket ilkelerine  dahilebilirsiniz.

Duyarlılık etiketlerini Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">sonra, kullanıcılar</a> içerik [oluşturulurken veya düzenlensin diye sınıflandırmak](../compliance/sensitivity-labels-office-apps.md) ve korumak için Office uygulamaları içinde görünmeye başlar.

![Microsoft 365'da duyarlılık Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Veri gizliliği için, hassas kişisel bilgileri içeren e-postaya veya içeriğe şifreleme ve diğer kuralların bulunduğu bir duyarlılık etiketini el ile uygulayabilirsiniz.

> [!NOTE]
> E-postaya şifreleme uygulanmış duyarlılık etiketleri, OME ile bazı örtüşen işlevlere sahip olur. Bkz [. OME ve duyarlılık etiketleriyle güvenli e-posta senaryoları karşılaştırması](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Kullanıcılar belgeleri düzenlerken veya e-posta düzenlerken istemci tarafı otomatik etiketleme

Duyarlılık etiketi oluşturmanız, [belirttiğiniz koşullarla](../compliance/apply-sensitivity-label-automatically.md) eşleşmesi için e-posta dahil olmak üzere bu etiketi otomatik olarak içeriğe atabilirsiniz.

İçeriklere otomatik olarak duyarlılık etiketleri uygulayabilme özelliği önemlidir, çünkü:

- Sınıflandırmalardan her biri için kullanıcılarınızı ne zaman kullanılamayacaklarını eğitmek zorunda değilsiniz.
- Tüm içeriği doğru şekilde sınıflandırmak için kullanıcılara güvenmeniz gerek değildir.
- Kullanıcıların artık ilkelerinizi malıdır; onlar da çalışmalarına odaklanabilirsiniz.

Otomatik etiket, hem kullanıcılara etiket önerilerini hem de otomatik olarak etiket uygulamayı destekler. Ancak her iki durumda da, içeriği doğru etiketlemeye yardımcı olmak için kullanıcı etiketi kabul etmeye veya reddetmeye karar verir.

Belge kaydedmeden önce bile etiketin uygulanama süresi nedeniyle, istemci tarafı etiketlemesi belgelerde çok az gecikmeye neden olur. Bununla birlikte, tüm istemci uygulamaları otomatik etiketlemeyi desteklemez. Bu özellik, Azure Information Protection birleşik etiketleme istemcisi ve azure uygulamalarının [bazı Office destekler](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Yapılandırma yönergeleri için bkz[. Belirli uygulamalar için otomatik Office yapılandırma](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Veri gizliliği için, hassas kişisel bilgiler içeren içeriklere otomatik olarak duyarlılık etiketleri uygulayabilirsiniz.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>İçerik zaten kayded olduğunda hizmet tarafındaki otomatik etiketleme

Bu yöntem, duyarlılık etiketleriyle otomatik sınıflandırma olarak adlandırılır. Ayrıca, geri kalan veriler için otomatik etiketleme (SharePoint ve OneDrive'daki belgeler için) ve geçişteki veriler (Exchange tarafından gönderilen veya alınan e-posta için) olarak da ifade edilenleri duyabilirsiniz. Örneğin Exchange, posta kutularında kalan e-postaları içermez.

Bu etiket, kullanıcı uygulaması yerine hizmetin kendisi tarafından uygulandığından, kullanıcıların hangi uygulamalara sahip olduğu ve hangi sürüme sahip olduğu konusunda kaygılanmanız yoktur. Sonuç olarak bu özellik, kurum genelinde hemen kullanılabilir ve ölçekte etiketlemeye uygundur. Otomatik etiket ilkeleri etiketlemeyi desteklemez, çünkü kullanıcı etiket işlemiyle etkileşimde bulunmakla etkileşimde bulunmakla ilgili bilgi desteklemez. Bunun yerine, yönetici, etiketi gerçekten uygulamadan önce içeriğin doğru etikete sahip olduğundan emin olmak için benzetim modunda ilkeleri çalıştırır.

Yapılandırma yönergeleri için bkz. Otomatik etiketleme ilkeleri için SharePoint[, OneDrive yapılandırma Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Önemli olan sitelerde veri gizliliği için hassas kişisel bilgileri içeren içeriğin otomatik olarak şifrelen için anında duyarlılık etiketleri bulunmaktadır.

## <a name="data-loss-prevention"></a>Veri kaybını önleme

Microsoft 365'te, hem şirket içinde hem de dışında kişisel bilgi içeren verilerin paylaşımı gibi riskli, yanlışlıkla veya uygunsuz paylaşımı tespit etmek, uyarmak ve engellemek için veri kaybı önleme [(DLP) önlemeyi (DLP)](../compliance/dlp-learn-about-dlp.md) kullanabilirsiniz.

DLP şunları şunları sağlar:

- Riskli paylaşım etkinliklerini tanımlama ve izleme.
- Kullanıcıları doğru kararlar vermek için bağlam içinde yol gösterici rehberlikle eğitin.
- İçeriğin üretkenliğini artırmadan veri kullanımı ilkelerini zorunlu kılın.
- Verileri paylaşılan zaman algılamak ve korumak için sınıflandırma ve etiketlemeyle tümleştirin.

### <a name="supported-workloads-for-dlp"></a>DLP için desteklenen iş yükleri

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi'daki</a> bir DLP ilkesiyle, Microsoft 365, Exchange Online, SharePoint, OneDrive ve OneDrive gibi birçok konumda yer alan hassas öğeleri tanımlayabilir, izleyebilir ve otomatik olarak koruyabilirsiniz. Microsoft Teams.

Örneğin, herhangi bir posta sitesinde depolanan kredi kartı numarası içeren herhangi bir OneDrive tanımlayabilir veya yalnızca belirli OneDrive sitelerini izleyebilirsiniz.

Ayrıca, hassas öğeleri tanımlama ve DLP ilkeleri uygulama olanağı içeren Excel, PowerPoint ve Word'un yerel olarak yüklenmiş sürümlerinde de hassas öğeleri izleyebilir ve koruyabilirsiniz. DLP, bu kullanıcılar bu uygulamalardan içerik paylaştığında sürekli Office sağlar.

> [!div class="mx-imgBorder"]
> ![DLP için desteklenen iş yükleri.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Bu şekil, kişisel verileri koruyan bir DLP örneği gösterir.

> [!div class="mx-imgBorder"]
> ![DLP kullanarak kişisel verileri koruma örneği.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP, sistem durumu kaydı içeren bir belgeyi veya e-postayı tanımlamak için kullanılır ve sonra bu belgeye erişimi otomatik olarak engeller veya e-postanın gönderilmelerini engeller. Ardından DLP, alıcıyı bir ilke ipucuyla bilgili olarak son kullanıcıya ve yöneticiye bir uyarı gönderir.

### <a name="planning-for-dlp"></a>DLP planlama

DLP ilkelerinizi planlama:

- İş gereksinimleriniz.

- Kuruluşun, veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama [makalesinde açıklandığı gibi risk tabanlı bir değerlendirme](information-protection-deploy-assess.md).

- Yerinde başka bilgi koruma ve yönetim mekanizmaları veya veri gizliliğini planlama.

- Veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama makalesinde açıklandığı gibi, değerlendirme çalışmalarınızı temel alarak kişisel veriler için tanımmış olduğunuz [hassas bilgi türleri](information-protection-deploy-assess.md). DLP ilkesi koşulları, hem hassas bilgi türlerine hem de bekletme etiketlerine dayandırabilirsiniz.

- DLP koşullarını belirtmeniz gereken bekletme etiketleri. Daha fazla [bilgi için, kuruluş makalesinde veri gizlilik düzenlemesine tabi olan](information-protection-deploy-govern.md) geçerli bilgilere bakın.

- Kuruluşta birinin hassas bilgi türlerinde, bekletme etiketlerinde, yasal düzenlemelerde ve uyumluluk ilkelerinde yer alan değişikliklere yönelik ilkeleri işletmesi ve ayarlaması gereken sürekli DLP ilkesi yönetimi.

Duyarlılık etiketleri DLP ilkesi koşullarında kullanılamaz, ancak erişimi engellemeye yönelik bazı koruma senaryoları yalnızca hassas bilgi türlerine göre otomatik olarak uygulanan duyarlılık etiketleriyle gerçekleştirilebilir. Güçlü bir duyarlılık etiketi kullanılıyorsa, koruma korumasını korumak için DLP'nin kullanıp kullanılmaması gerektiğini düşünün, çünkü:

  - DLP, dosyaların paylaşımını önlenebilir. Duyarlılık etiketleri yalnızca erişimi önlenebilir.

  - DLP'nin kurallar, koşullar ve eylemler açısından daha ayrıntılı denetim düzeyleri vardır.

  - DLP ilkeleri sohbet Teams mesajlarına uygulanabilir. Duyarlılık etiketleri yalnızca belgelere ve e-postalara uygulanabilir.


### <a name="dlp-policies"></a>DLP ilkeleri

DLP ilkeleri Microsoft Uyumluluk yönetim merkezinde yapılandırılır ve koruma düzeyini, ilkenin hassas bilgi türünü ve hedef iş yüklerini belirtir. Bunun temel bileşenleri korumayı ve veri türlerini belirlemektir.

> [!div class="mx-imgBorder"]
> ![DLP ilkesi yapılandırması Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

GDPR farkındalığı için örnek bir DLP ilkesi aşağıdaki gibidir.

![GDPR farkındalığı için örnek DLP ilkesi.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

DLP [ilkeleri oluşturma](../compliance/create-test-tune-dlp-policy.md) ve uygulama hakkında daha fazla bilgi için bu makaleye bakın.

### <a name="protection-levels-for-data-privacy"></a>Veri gizliliği için koruma düzeyleri

Aşağıdaki tabloda, DLP kullanarak korumayı artırmaya yönelik üç yapılandırma listelemaktadır.

![DLP ile veri gizliliği koruma düzeyleri.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

İlk yapılandırma olan Farkındalık, veri gizliliği düzenlemelerine yönelik uyumluluk yapılandırmasını karşılamak için başlangıç noktası ve minimum koruma düzeyi olarak kullanılabilir.

> [!NOTE]
> Koruma düzeyleri artarak, kullanıcıların bilgileri paylaşma ve bilgilere erişme yetenekleri bazı durumlarda azalır ve bu durum kullanıcıların üretkenliğini veya günlük görevleri tamamlama yeteneğini etkileyebilir.

Koruma düzeylerini artıran çalışanlarınızı daha güvenli bir ortamda üretken olmaya devam etmek için zaman kendinizi yeni güvenlik ilkeleri ve yordamlar konusunda eğitip eğitin.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>DLP ile duyarlılık etiketleri kullanma örneği

Duyarlılık etiketleri, son derece düzenlemeye tabi bir ortamda veri gizliliği sağlamak için DLP ile birlikte kullanılabilir. Tümleşik dağıtımın temel adımları:

1. Veri gizliliği için mevzuat ve başka türlü iş gereksinimleri belge belge belgelemektedir.
2. Hedef veri kaynakları, türler ve sahiplik, veri gizliliği kaygıları ile nitelene olarak niteler.
3. Veri gizliliği etkin noktaları için gereksinimleri karşılamaya ve yönetmeye genel bir strateji oluşturulmaktadır.
4. Veri gizlilik denetim stratejisini ele alan aşamalı bir eylem planı hazırlar.

Bu öğeler belirlendiktan sonra hassas bilgi türlerini, duyarlılık etiketleme taksonomisini ve DLP ilkelerini birlikte kullanabilirsiniz. Bu şekilde bir örnek ve sayı 365'tir.

> [!div class="mx-imgBorder"]
> ![DLP ile çalışan duyarlılık etiketleri örneği.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Bu resmin daha büyük bir sürümüne bakın](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Aşağıda, şekilde gösterildiği gibi DLP ve duyarlılık etiketlerini birlikte kullanan bazı veri koruma senaryoları ve bunlar yer almaktadır.

| Senaryo | İşlem |
|:-------|:-----|
| A | <ol><li>İçerik için duyarlılık etiketleri yönetici tarafından, içeriğe ve e-postaya el ile veya otomatik olarak uygulama için gruplar halinde yayımlanır. </li><li>Kullanıcı A, şifreleme veya uygulanan diğer ayarlarla içerikle etkileşim kurduğunda etiketleri el ile veya otomatik olarak uygular. </li><li>Kullanıcı A, konuk kullanıcı olan Kullanıcı B'ye korumalı bir e-posta veya dosya gönderir. </li></ol> |
| B | Yönetici tarafından A Kullanıcısı'na yayımlanan DLP ilkesi A Kullanıcısı'nın e-postayı ve/veya dosyayı Kullanıcı B'ye göndermelerini engeller. |
| C |  "Sahip konukları davet etmeyecek" ayarının yer alan duyarlılık etiketi, ekip üyelerine veya site için bir ekip veya Teams veren A SharePoint yayımlanır. Sitenin başka bir kullanıcısı seçmeli olarak dosya paylaşımını Kullanıcı B ile denemesi, ancak DLP'nin dosyayı engellemesi. |
| D | Site içeriğine otomatik olarak uygulamanın duyarlılık etiketi bir veya birden çok sitede yayımlanır ve bu da bir koruma katmanı daha sağlar ve sonuçta korumalı bir site elde eder. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Office 365 İleti Şifrelemesi (OME) yeni özellikleri

Kişiler hasta durumu bilgileri veya müşteri ve çalışan bilgileri gibi hassas öğeleri almak için çoğunlukla e-posta kullanır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyemelerini sağlamaya yardımcı olur.

[OME ile](../compliance/ome.md), kurum içindeki ve dışındaki kişiler arasında şifrelenmiş iletiler gönderebilir ve alabilirsiniz. OME; Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. OME, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyemelerini sağlamaya yardımcı olur.

Veri gizliliği için, hassas öğeler içeren iç iletileri korumak için OME kullanırsınız. Office 365 İleti Şifrelemesi, Azure Information Protection'ın bir parçası olan Microsoft Azure Hak Yönetimi'ne (Azure RMS) bağlı bir çevrimiçi hizmettir. Bu, e-postanızı güvenlik altına almak için şifreleme, kimlik ve yetkilendirme ilkelerini içerir. Hak yönetimi şablonlarını, İletileri Iletme seçeneğini ve yalnızca şifrele seçeneğini kullanarak iletileri şifreebilirsiniz.

Ayrıca, bu korumayı uygulamak için posta akışı kuralları da tanımlayabilirsiniz. Örneğin, belirli bir alıcıya adreslenen tüm iletilerin şifrelenirken şifrelenirken gerekli olduğu veya konu satırda belirli anahtar sözcükler içeren bir kural oluşturabilir ve ayrıca alıcıların iletinin içeriğini kopyalayıp yazdıramayacaklarını belirtebilirsiniz.

Buna ek olarak, OME [Gelişmiş](../compliance/ome-advanced-message-encryption.md) İleti Şifrelemesi dış alıcılar ve şifreli e-postalara erişimleri üzerinde daha esnek denetimler gerektiren uyumluluk yükümlülüklerini karşılamanıza da yardımcı olur. Microsoft 365'da OME Gelişmiş İleti Şifrelemesi ile, kuruluş dışında paylaşılan hassas e-postaları hassas bilgi türlerini algılayan otomatik ilkelerle denetim altına alabilirsiniz.

Veri gizliliği için, e-postayı bir dış tarafla paylaşmanız gerekirse son kullanma tarihi belirtebilirsiniz ve iletileri iptal edersiniz. Dış alıcılara gönderilen iletiler için yalnızca bir son kullanma tarihi iptal edilebilir ve bu tarihin son kullanma tarihini ayarlayın.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>OME ve duyarlılık etiketleriyle güvenli e-posta senaryoları karşılaştırması

Şifreleme içeren e-postaya uygulanan OME ve duyarlılık etiketlerinin bazı çakışmaları vardır, bu nedenle bu tabloda gösterildiği gibi hangi senaryoların uygulanabilecek olduğunu anlamanız önemlidir.

| Senaryo | Duyarlılık Etiketleri | OME |
|:-------|:-----|:-------|
| İç + iş ortakları <br> İç kullanıcılarla güvenilir iş ortakları arasında güvenli bir şekilde iletişim kurma ve işbirliği yapma | Öner – tamamen özelleştirilmiş sınıflandırma ve koruma içeren etiketler | Evet – Yalnızca şifreleme veya Sınıflandırmaya sahip korumayı iletme |
| Dış taraflar <br> Tüm dış/tüketici kullanıcılarıyla güvenli bir şekilde iletişim kurma ve işbirliği yapma | Evet – etikette önceden tanım alıcıları | Öner – alıcılara göre tam zamanlı koruma |
| Sona erme/iptali olan şirket içi + iş ortakları <br> Süre sonu ve iptal ile iç kullanıcılarla ve güvenilir iş ortaklarıyla posta ve içerik erişimini denetleme | Öner - Erişim süresiyle tamamen özelleştirilmiş koruma, kullanıcı dosyaları el ile izleyebilir ve iptal eder | Hayır – iç posta için iptal veya son kullanma tarihi yoktur |
| Süre sonu/iptali olan dış taraflar <br> Süre sonu ve iptali olan dış/tüketici kullanıcılarının posta ve içerik erişimini denetleme | Evet, kullanıcı dosyaları el ile izleyebilir | Öner (E5) – yönetici Güvenlik ve Uyumluluk Merkezi'& postayı iptal ettirebilirsiniz |
| Otomatik etiketleme <br> Kuruluş, belirli hassas içerikle ve/veya belirli alıcılarla posta/ekleri otomatik olarak korumak istiyor | Öner (E5) - İstemcileri otomatik olarak etiketleme Exchange Outlook, posta akış kurallarını ve DLP İlkesini geliştirmektedir | Evet - Yalnızca şifrele veya İleri iletme korumalı posta akış kuralları ve DLP ilkesi |
||||

Bu iki yöntem arasında son kullanıcı ve yönetici deneyimlerinden de farklar olur.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams hassas veriler için korumayla çalışma

Kişisel verileri gizlilik düzenlemelerine uygun olarak depolamayı planlamış Teams için bkz. Aşağıdakiler için ayrıntılı rehberlik [](secure-teams-security-isolation.md)ve yapılandırma adımları sağlayan güvenlik yalıtımlı bir ekip yapılandırma:

- Kimlik ve cihaz erişimi
- Özel ekip oluşturma
- Temel ekip sitesi izinlerinin kilitlenmesi
- Şifrelemeli grup tabanlı duyarlılık etiketi
