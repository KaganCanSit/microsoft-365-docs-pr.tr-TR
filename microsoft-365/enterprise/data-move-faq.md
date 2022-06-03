---
title: Veri taşıma genel SSS
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: ITPro
ms.topic: faq
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Çekirdek verileri yeni bir Office 365 veri merkezi coğrafi konumuna taşıma hakkında sık sorulan soruların (SSS) yanıtlarını bulun.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3164612238010e72eb02510e1264cca528b80f38
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874324"
---
# <a name="data-move-general-faq"></a>Veri taşıma genel SSS

Bekleyen temel müşteri verilerini yeni bir veri merkezi coğrafi konumuna taşıma hakkındaki genel soruların yanıtlarını burada bulabilirsiniz.

### <a name="what-customers-are-eligible-to-request-a-move"></a>Hangi müşteriler taşıma isteğinde bulunabilir?
<details><summary>Genişletmek için tıklayın</summary>

Yeni veri merkezi coğrafi bölgesi için uygun bir ülke seçen mevcut Microsoft 365 ticari müşteriler taşıma isteğinde bulunabilir. Program yalnızca uygun iş yükleri için bekleyen temel müşteri verilerini ilgili Microsoft 365 veri merkezi coğrafi konumuna geçirmek üzere Microsoft 365 kiracıya atanmış uygun ülke koduna sahip kiracılar için mevcuttur. Bkz. Ülke [uygunluğunuzu onaylamak için verilerinizin taşınmasını isteme](request-your-data-move.md) .

</details>

### <a name="how-do-we-define-core-customer-data"></a>Temel Müşteri Verilerini nasıl tanımlarız?
<details><summary>Genişletmek için tıklayın</summary>

Temel müşteri verileri, [Microsoft Online Services Koşulları'nda](https://aka.ms/ost) tanımlanan müşteri verilerinin bir alt kümesini ifade eden bir terimdir:

- posta kutusu içeriğini (e-posta gövdesi, takvim girdileri ve e-posta eklerinin içeriği) Exchange Online
- çevrimiçi site içeriğini ve bu sitede depolanan dosyaları SharePoint
- OneDrive İş karşıya yüklenen dosyalar

</details>

### <a name="what-is-in-scope-for-teams-migration"></a>Teams geçişinin kapsamı nedir?
<details><summary>Genişletmek için tıklayın</summary>

Exchange Online, SharePoint Online ve OneDrive İş ek olarak; Microsoft, Teams verileri yerel veri merkezine geçirir.

- Özel iletiler ve kanal iletileri dahil olmak üzere sohbet iletilerini Teams.
- Sohbetlerde kullanılan görüntüleri Teams.

Teams dosyaları SharePoint Online'da, Teams sohbet dosyaları da OneDrive İş depolanır. Sesli mesaj, takvim ve kişiler Exchange Online depolanır. Çoğu durumda, Exchange Online, SharePoint Online ve OneDrive İş yerel veri merkezi coğrafi alanında müşteri tarafından zaten kullanılır ve ayrıca uygun müşteri ülkeleri için Microsoft 365 geçiş programının bir parçasıdır.

</details>

### <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>Kiracımın temel müşteri verilerinin yeni coğrafi bölgemde bekleyen konumda depolanması için geçişim hangi noktada tamamlandı?
<details><summary>Genişletmek için tıklayın</summary>

Exchange Online ile SharePoint Online/OneDrive İş arasındaki paylaşılan bağımlılıklar nedeniyle, her iki hizmet de geçirilene kadar herhangi bir geçişin tamamlandığı düşünülemez. Exchange Online ve SharePoint Çevrimiçi/OneDrive İş genellikle ayrı zamanlarda ve birbirinden bağımsız olarak geçiriliyor. Müşteri kiracı yöneticileri, her hizmet geçişi tamamlandığında İleti Merkezi'nde onay alır ve her hizmet için bekleyen konumdaki temel müşteri verilerini onaylamak için Yönetici Merkezi'nde veri konumu kartını görüntüleyebilir.

</details>

### <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Taşıma sırasında müşteri verilerimin güvende olduğundan ve kapalı kalma süresi yaşamayacağımdan nasıl emin olursunuz?
<details><summary>Genişletmek için tıklayın</summary>

Veri taşıma, son kullanıcıları en az etkileyen bir arka uç hizmeti işlemidir. Etkilenebilen özellikler [, Verilerinizin taşınması sırasında ve sonrasında'da](during-and-after-your-data-move.md) listelenir. Kullanılabilirlik için [Microsoft Online Services Hizmet Düzeyi Sözleşmesi'ne (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) bağlıyız, dolayısıyla taşıma sırasında müşterilerin hazırlaması veya izlemesi gereken hiçbir şey yoktur.

Tüm Microsoft 365 hizmetleri veri merkezlerinde aynı sürümleri çalıştırdığından, tutarlı işlevlerden emin olabilirsiniz. Hizmetiniz işlem boyunca tam olarak desteklenir.

</details>

### <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Farklı coğrafi bölgelerde farklı hizmetlerin bulunmasının etkisi nedir?
<details><summary>Genişletmek için tıklayın</summary>

bazı Microsoft 365 hizmetleri, bazı mevcut müşteriler ve taşıma sürecinin ortasındaki müşteriler için farklı coğrafi bölgelerde bulunabilir. Hizmetlerimiz birbirinden bağımsız olarak çalışır ve böyle bir durumda kullanıcı deneyimi üzerinde hiçbir etkisi yoktur. Ancak, veri yerleşimi amacıyla, hem Exchange Online hem de SharePoint Çevrimiçi/OneDrive İş aynı veri merkezi coğrafi konumuna geçirilene kadar kiracı geçişi tamamlanmış olarak kabul edilemez.

</details>

### <a name="where-is-my-core-customer-data-located"></a>Temel müşteri verilerim nerede bulunur?
<details><summary>Genişletmek için tıklayın</summary>

Müşteri kiracı yöneticileri Yönetici Merkezi'nde veri konumu kartını istedikleri zaman görüntüleyebilir ve her hizmet için (özellikle kiracıları için) bekleyen konumdaki temel müşteri verilerini onaylayabilir. Ayrıca veri merkezi coğrafi alanlarının konumunu, veri merkezlerinin ve Office 365 müşteri verilerinin konumunu [Microsoft 365 etkileşimli veri merkezi haritalarında](https://office.com/datamaps) yeni kiracılar için bekleyen konumlardaki geçerli varsayılan çekirdek müşteri verilerine başvuru olarak yayımlarız. Bekleyen müşteri verilerinizin konumunu Microsoft 365 yönetim merkezi Kuruluş Profilinizin altındaki Veri Konumu bölümünden doğrulayabilirsiniz.

</details>

### <a name="when-will-i-be-able-to-request-a-move"></a>Ne zaman taşıma isteğinde bulunacağım?
<details><summary>Genişletmek için tıklayın</summary>

Veri merkezi coğrafi bölgeniz için desteklenen zaman çerçeveleri için verilerinizi [taşıma isteğinde](request-your-data-move.md) bulunma sayfasına bakın.

</details>

### <a name="how-can-i-request-to-be-moved"></a>Taşınmayı nasıl isteyebilirim?
<details><summary>Genişletmek için tıklayın</summary>

Uygun müşteriler [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) bir sayfa görür. Taşıma isteğinde bulunma yönergeleri için lütfen bkz. [Veri taşıma isteğinde](request-your-data-move.md) bulunma.

</details>

### <a name="can-i-change-my-selection-after-requesting-a-move"></a>Taşıma isteğinde bulunarak seçimimi değiştirebilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

İsteğinizi gönderdikten sonra sizi işlemden kaldırmamız mümkün değildir.

</details>

### <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Son tarihten önce bir taşıma isteğinde bulunmazsa ne olur?
<details><summary>Genişletmek için tıklayın</summary>

Açık kayıt döneminden sonra geçiş isteklerini kabul edemeyiz.

</details>

### <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Daha iyi bir ağ performansı elde etmek için verilerimi taşımak istersem ne olur?
<details><summary>Genişletmek için tıklayın</summary>

Microsoft 365 veri merkezine fiziksel yakınlık, daha iyi bir ağ performansı garantisi değildir. Son kullanıcı ile Microsoft 365 hizmeti arasındaki ağ performansını etkileyen birçok faktör ve bileşen vardır. Bu ve performans ayarlama hakkında daha fazla bilgi için bkz. [Microsoft 365 için ağ planlama ve performans ayarlama](network-planning-and-performance.md).

</details>

### <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Tüm hizmetler verilerini aynı günde mi taşır?
<details><summary>Genişletmek için tıklayın</summary>

Her hizmet bağımsız olarak taşınır ve büyük olasılıkla verilerini farklı zamanlarda taşır.

</details>

### <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Verilerimin ne zaman taşınmasını istediğimi seçebilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

Müşteriler belirli bir tarihi seçemezler, taşımalarını geciktiremezler ve taşımalar için belirli bir tarih veya saat çerçevesini paylaşamayız.

</details>

### <a name="can-you-share-when-my-data-will-be-moved"></a>Verilerim ne zaman taşınacak?
<details><summary>Genişletmek için tıklayın</summary>

Veri taşıma işlemleri, son kullanıcıları en az etkileyen arka uç işlemidir. Genel olarak çalıştırılan ve otomatikleştirilmiş bir ortamda veri taşıma gerçekleştirmemiz gereken karmaşıklık, duyarlık ve ölçek, kiracınız veya başka bir tek kiracı için bir veri taşıma işleminin tamamlanması beklendiğinde paylaşmamızı engeller. Müşteriler, veri taşıma işlemi tamamlandığında katılımcı hizmet başına İleti Merkezi'nde bir onay alır.

</details>

### <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Veriler taşınırken kullanıcılar hizmetlere erişirse ne olur?
<details><summary>Genişletmek için tıklayın</summary>

Her hizmet için verilerin taşınması sırasında sınırlı olabilecek özelliklerin tam listesi için bkz. [Verileriniz taşınırken ve sonrasında](during-and-after-your-data-move.md) .

</details>

### <a name="how-do-i-know-the-move-is-complete"></a>Taşıma işleminin tamam olduğunu Nasıl yaparım? biliyor musunuz?
<details><summary>Genişletmek için tıklayın</summary>

Her hizmetin verilerini taşıma işleminin tamamlandığını onaylayan Microsoft 365 İleti Merkezi'ni izleyin. Her hizmetin verileri taşındığında üç tamamlama bildirimi alırsınız: her biri Exchange Online, çevrimiçi SharePoint ve Çevrimiçi Skype Kurumsal. Müşteri verilerinizin bekleyen konumunu Microsoft 365 yönetim merkezi Kuruluş Profilinizin altındaki Veri Konumu bölümünden de doğrulayabilirsiniz.

</details>

### <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Yeni veri merkezi coğrafi bölgelerinden birinde Microsoft 365 müşterisiyim, ancak kaydolunca farklı bir ülke seçtim. Yeni veri merkezi coğrafi konumuna nasıl taşınabilirim?
<details><summary>Genişletmek için tıklayın</summary>

Kiracınızla ilişkili kayıt ülkesini değiştirmek mümkün değildir. Bunun yerine, yeni bir abonelikle yeni bir Microsoft 365 kiracı oluşturmanız ve kullanıcılarınızı ve verilerinizi yeni kiracıya el ile taşımanız gerekir.

</details>

### <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Exchange Online taşıma sırasında Microsoft 365 e-posta verilerinin Microsoft 365 geçiş işlemi devam ederse ne olur?
<details><summary>Genişletmek için tıklayın</summary>

Bu çok yaygın bir senaryodur ve tam olarak desteklenir. Veri merkezi coğrafi bölgeleri arasında bulut geçişi, şirket içi bulut posta kutusu geçişlerini engellemez.

</details>

### <a name="can-i-pilot-some-users"></a>Bazı kullanıcıları pilot olarak kullanabilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

Bağlantıyı test etmek için ayrı bir deneme kiracısı oluşturabilirsiniz, ancak deneme kiracısı mevcut kiracınızla hiçbir şekilde birleştirilemiyor.

</details>

### <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Microsoft'un verilerimi taşımasını beklemek istemiyorum. Yeni bir kiracı oluşturup kendi kiracımı taşıyabilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

Evet, ancak işlem Microsoft'un veri taşıma işlemini gerçekleştirmesi kadar sorunsuz olmayacaktır.

Yeni veri merkezi coğrafi alanı kullanılabilir olduktan sonra yeni bir kiracı oluşturursanız, yeni kiracı yeni coğrafi bölgede barındırılır. Bu yeni kiracı önceki kiracınızdan tamamen ayrıdır ve tüm kullanıcı posta kutularını, site içeriğini, etki alanı adlarını ve diğer tüm verileri taşımak sizin sorumluluğunuzdadır. Kiracı adını bir kiracıdan diğerine taşıyabileceğinizi unutmayın. Kullanıcılarınız için tüm ayarları, verileri ve abonelikleri taşımayla ilgileneceğimiz için Microsoft tarafından sağlanan taşıma programını beklemenizi öneririz.

</details>

### <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Müşteri verilerim zaten yeni bir veri merkezi coğrafi konumuna taşındı. Geri dönebilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

Hayır, bu mümkün değil. Yeni coğrafi veri merkezlerine taşınan müşteriler geri taşınamaz. Herhangi bir coğrafi bölgede müşteri olarak, daha önce yaşadığınız hizmet kalitesi, performans ve güvenlik denetimleriyle aynı deneyime sahip olacaksınız. [Microsoft 365 Multi Geo](https://aka.ms/multi-geo), bazı müşterilerin eklenti olarak kullanımına sunulur ve tek bir kiracının birden çok uydu coğrafi bölge oluşturmasına ve veri yerleşimi taahhütleriyle kullanıcı verilerini bu coğrafi bölgelere taşımasına olanak tanır.

</details>

### <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Yeni veri merkezlerinde barındırılan Microsoft 365 kiracılar ülke dışındaki kullanıcıların kullanımına sunulacak mı?
<details><summary>Genişletmek için tıklayın</summary>

Evet. Microsoft, 2.700'den fazla İnternet Servis Sağlayıcısı (ISS) ile eşleme anlaşmaları ile dünya çapında 35 ülkede 130'dan fazla konumda genel İnternet bağlantıları olan büyük bir küresel ağ sürdürmektedir. Kullanıcılar, İnternet'te bulundukları her yerden veri merkezlerine erişebilir.

</details>

### <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Kiracım Multi Geo eklentisini yapılandırdı. Varsayılan coğrafi konumumu değiştirmek ve uydu bölgesinde olmayan herhangi bir kullanıcıyı yeni varsayılan coğrafi bölgeye taşımak için Microsoft 365 Taşıma Programı'na kiracıma yine kaydolabilir miyim?
<details><summary>Genişletmek için tıklayın</summary>

Evet, kiracınız kaydolmaya uygun ancak [Multi-Geo'yı](https://aka.ms/multi-geo) yapılandıran müşteriler için kiracı düzeyinde taşıma tam olarak desteklenmediğinden önemli noktalar vardır.

SharePoint Online ve OneDrive İş bu program aracılığıyla kiracı düzeyinde yeni veri merkezi coğrafi konumuna geçemez. Müşteri yöneticisi OneDrive İş paylaşımlarını Multi-Geo kullanarak kullanılabilir herhangi bir bölgeye taşınacak şekilde yapılandırabilir, ancak kiracı için Multi-Geo yapılandırıldıktan sonra kiracının varsayılan konumu değiştirilemez.

Geçişi kabul eden müşteriler için, tüm Exchange Online posta kutularını geçerli varsayılan coğrafi bölgenizden yeni yerel veri merkezi coğrafi bölgenize taşıyacağız ve varsayılan Exchange Online bölgesini güncelleştireceğiz. Hedeflediğiniz gibi uydu bölgesi veri yerleşimine saygı duymaya devam etmek için Multi Geo uydu bölgelerinde yapılandırılmış exo posta kutularını taşımayacağız.  Multi Geo yapılandırmasına sahip müşteriler için sohbet hizmeti kiracı geçişlerini Teams Exchange Online benzer şekilde davranır.

</details>

### <a name="i-have-public-folders-deployed-in-my-tenant-what-will-be-the-impact-on-public-folder-access-during-or-after-the-move"></a>Kiracımda dağıtılan ortak klasörlerim var. Taşıma sırasında veya sonrasında ortak klasör erişimi üzerindeki etkisi ne olur?
<details><summary>Genişletmek için tıklayın</summary>

Ortak klasörlerin taşınması sırasında veya sonrasında ortak klasörlere erişen son kullanıcıların herhangi bir etkisi yoktur. Ancak, tüm ortak klasör posta kutuları aynı bölgeye taşına kadar ortak klasörler Exchange Yönetici Merkezi aracında yönetim için kullanılamayabilir. Daha fazla ayrıntı için [lütfen bu makaleye](https://aka.ms/pfxrf) bakın.

</details>

### <a name="related-topics"></a>İlgili konular

[Temel verileri yeni Microsoft 365 veri merkezi coğrafi bölgelerine taşıma](moving-data-to-new-datacenter-geos.md)

[Veri taşıma isteğinde bulunma](request-your-data-move.md)

[Microsoft 365 Multi Geo](https://aka.ms/multi-geo)

[etkileşimli veri merkezi haritası Microsoft 365](https://office.com/datamaps)

[Microsoft 365 Desteği](../admin/get-help-support.md)

[Microsoft Dynamics CRM Online için yeni veri merkezi coğrafi bölgeleri](/power-platform/admin/new-datacenter-regions)

[Bölgeye göre Azure hizmetleri](https://azure.microsoft.com/regions/)
