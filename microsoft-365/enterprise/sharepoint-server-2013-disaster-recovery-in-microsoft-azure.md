---
title: Microsoft Azure'da SharePoint Server 2013 Olağanüstü Durum Kurtarma
ms.author: bcarter
author: brendacarter
manager: scotv
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Deployment
- seo-marvel-apr2020
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: Bu makalede, şirket içi SharePoint grubunuz için olağanüstü durum kurtarma ortamı oluşturmak üzere Azure'ın nasıl kullanılacağı açıklanmaktadır.
ms.openlocfilehash: 1b1951e70cfbecc0f6586e68d7142bc26fb6252f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077406"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Microsoft Azure'da SharePoint Server 2013 Olağanüstü Durum Kurtarma

 Azure'ı kullanarak, şirket içi SharePoint grubunuz için bir olağanüstü durum kurtarma ortamı oluşturabilirsiniz. Bu makalede, bu çözümün nasıl tasarlandığı ve uygulandığı açıklanmaktadır.

 **SharePoint Server 2013 olağanüstü durum kurtarmaya genel bakış videosunu izleyin**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]

 SharePoint şirket içi ortamınıza olağanüstü durum geldiğinde, en yüksek önceliğiniz sistemin hızla yeniden çalışmasını sağlamaktır. SharePoint ile olağanüstü durum kurtarma, zaten Microsoft Azure çalışan bir yedekleme ortamınız olduğunda daha hızlı ve kolaydır. Bu videoda, SharePoint sıcak yük devretme ortamının ana kavramları açıklanmaktadır ve bu makaledeki tüm ayrıntılar tamamlanmaktadır.

Bu makaleyi aşağıdaki çözüm modeliyle kullanın: **Microsoft Azure'da Olağanüstü Durum Kurtarma'yı SharePoint**.

[![Olağanüstü durum kurtarma işlemini Azure'a SharePoint.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)

 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) | [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)

## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Olağanüstü durum kurtarma için Azure Altyapı Hizmetleri'ni kullanma

Birçok kuruluşun SharePoint için olağanüstü durum kurtarma ortamı yoktur ve bu ortam şirket içinde derlemek ve bakımını yapmak pahalı olabilir. Azure Altyapı Hizmetleri, şirket içi alternatiflerden daha esnek ve daha ucuz olağanüstü durum kurtarma ortamları için cazip seçenekler sağlar.

Azure Altyapı Hizmetleri'ni kullanmanın avantajları şunlardır:

- **Daha az maliyetli kaynak** Şirket içi olağanüstü durum kurtarma ortamlarından daha az kaynak için bakım ve ödeme. Kaynak sayısı hangi olağanüstü durum kurtarma ortamını seçtiğinize bağlıdır: soğuk bekleme, sıcak bekleme veya etkin bekleme.

- **Daha iyi kaynak esnekliği** Olağanüstü bir durumda, yük gereksinimlerini karşılamak için kurtarma SharePoint grubunuzun ölçeğini kolayca genişletin. Kaynaklara artık ihtiyacınız kalmadığında ölçeği daraltın.

- **Daha düşük veri merkezi taahhüdü** Farklı bir bölgedeki ikincil veri merkezine yatırım yapmak yerine Azure Altyapı Hizmetleri'ni kullanın.

Olağanüstü durum kurtarmayı kullanmaya yeni başlayan kuruluşlar için daha az karmaşık seçenekler ve yüksek dayanıklılık gereksinimleri olan kuruluşlar için gelişmiş seçenekler vardır. Ortam bir bulut platformunda barındırıldığında soğuk, sıcak ve sıcak bekleme ortamlarının tanımları biraz farklıdır. Aşağıdaki tabloda, Azure'da bir SharePoint kurtarma grubu oluşturmak için bu ortamlar açıklanmaktadır.

**Tablo: Kurtarma ortamları**

|Kurtarma ortamı türü|Açıklama|
|---|---|
|Sıcak|Tam boyutlu bir grup sağlanır, güncelleştirilir ve beklemede çalışır.|
|Sıcak|Grup oluşturulur ve sanal makineler çalışır ve güncelleştirilir. <br/> Kurtarma, içerik veritabanlarını eklemeyi, hizmet uygulamalarını sağlamayı ve içeriği gezinmeyi içerir. <br/> Grup, üretim grubunun daha küçük bir sürümü olabilir ve ardından tam kullanıcı tabanına hizmet vermek için ölçeği genişletilebilir.|
|Soğuk|Grup tamamen oluşturulmuş, ancak sanal makineler durdurulmuş. <br/> Ortamın bakımı, sanal makineleri zaman zaman başlatmayı, düzeltme eki uygulama, güncelleştirme ve doğrulamayı içerir. <br/> Olağanüstü bir durumda ortamın tamamını başlatın.|

Kuruluşunuzun Kurtarma Süresi Hedeflerini (RTO' lar) ve Kurtarma Noktası Hedeflerini (RPO' lar) değerlendirmek önemlidir. Bu gereksinimler, kuruluşunuz için en uygun yatırımın hangi ortam olduğunu belirler.

Bu makaledeki kılavuzda, sıcak bir bekleme ortamının nasıl uygulandığı açıklanmaktadır. Bu tür bir ortamı desteklemek için ek yordamları izlemeniz gerekse de, bunu soğuk bekleme ortamına da uyarlayabilirsiniz. Bu makalede, etkin bekleme ortamının nasıl uygulandığı açıklanmaz.

Olağanüstü durum kurtarma çözümleri hakkında daha fazla bilgi için bkz. [SharePoint 2013'te yüksek kullanılabilirlik ve olağanüstü durum kurtarma kavramları](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) ve [SharePoint 2013 için olağanüstü durum kurtarma stratejisi seçme](/SharePoint/administration/plan-for-disaster-recovery).

## <a name="solution-description"></a>Çözüm açıklaması

Hazır bekleyen olağanüstü durum kurtarma çözümü aşağıdaki ortamı gerektirir:

- Şirket içi SharePoint üretim grubu

- Azure'da kurtarma SharePoint grubu

- İki ortam arasında siteden siteye VPN bağlantısı

Aşağıdaki şekilde bu üç öğe gösterilmektedir.

**Şekil: Azure'da sıcak bekleme çözümünün öğeleri**

![Azure'da SharePoint sıcak bekleme çözümünün öğeleri.](../media/AZarch-AZWarmStndby.png)

Dağıtılmış Dosya Sistemi Çoğaltması (DFSR) ile SQL Server günlük gönderimi, veritabanı yedeklemelerini ve işlem günlüklerini Azure'daki kurtarma grubuna kopyalamak için kullanılır:

- DFSR günlükleri üretim ortamından kurtarma ortamına aktarır. WAN senaryosunda DFSR, günlükleri doğrudan Azure'daki ikincil sunucuya göndermekten daha verimlidir.

- Günlükler Azure'daki kurtarma ortamındaki SQL Server yeniden oynatılır.

- Bir kurtarma alıştırması gerçekleştirilene kadar günlükle gönderilen SharePoint içerik veritabanlarını kurtarma ortamına ekleyemezsiniz.

Grubu kurtarmak için aşağıdaki adımları gerçekleştirin:

1. Günlük gönderimi durdurulsun.

2. Birincil sunucu grubuna gelen trafiği kabul etmeyi durdurun.

3. Son işlem günlüklerini yeniden yürütme.

4. İçerik veritabanlarını grubuna ekleyin.

5. Çoğaltılan hizmet veritabanlarından hizmet uygulamalarını geri yükleyin.

6. Etki Alanı Adı Sistemi (DNS) kayıtlarını kurtarma grubuna işaret etmek için güncelleştirin.

7. Tam gezinme başlatın.

Canlı kurtarmanızın sorunsuz bir şekilde çalıştığından emin olmak için bu adımları düzenli olarak provanızı ve belgelenizi öneririz. İçerik veritabanlarını eklemek ve hizmet uygulamalarını geri yüklemek biraz zaman alabilir ve genellikle el ile yapılandırma gerektirir.

Bir kurtarma gerçekleştirildikten sonra, bu çözüm aşağıdaki tabloda listelenen öğeleri sağlar.

**Tablo: Çözüm kurtarma hedefleri**

|Öğe|Açıklama|
|---|---|
|Siteler ve içerik|Siteler ve içerik kurtarma ortamında kullanılabilir.|
|Yeni bir arama örneği|Bu sıcak bekleme çözümünde arama, arama veritabanlarından geri yüklenmez. Kurtarma grubundaki arama bileşenleri, üretim grubuna mümkün olduğunca benzer şekilde yapılandırılır. Siteler ve içerik geri yüklendikten sonra, arama dizinini yeniden oluşturmak için tam gezinme başlatılır. Siteleri ve içeriği kullanılabilir hale getirmek için gezinmenin tamamlanmasını beklemeniz gerekmez.|
|Hizmetleri|Verileri veritabanlarında depolayan hizmetler, günlükle gönderilen veritabanlarından geri yüklenir. Veritabanlarında veri depolamayan hizmetler basitçe başlatılır. <br/> Veritabanlarına sahip tüm hizmetlerin geri yüklenmesi gerekmez. Aşağıdaki hizmetlerin veritabanlarından geri yüklenmesi gerekmez ve yük devretmeden sonra başlatılabilir: <br/> Kullanım ve Sistem Durumu Veri Toplama <br/> Durum hizmeti <br/> Word otomasyonu <br/> Veritabanı kullanmayan diğer tüm hizmetler|

Daha karmaşık kurtarma hedeflerini ele almak için Microsoft Danışmanlık Hizmetleri (MCS) veya bir iş ortağıyla çalışabilirsiniz. Bunlar aşağıdaki tabloda özetlenir.

**Tablo: MCS veya iş ortağı tarafından ele alınabilecek diğer öğeler**

|Öğe|Açıklama|
|---|---|
|Özel grup çözümlerini eşitleme|İdeal olarak, kurtarma grubu yapılandırması üretim grubuyla aynıdır. Özel grup çözümlerinin çoğaltılıp çoğaltılmadığını ve iki ortamı eşitlenmiş durumda tutma işleminin uygulanıp gerçekleştirilmediğini değerlendirmek için bir danışman veya iş ortağıyla çalışabilirsiniz.|
|Şirket içi veri kaynaklarına bağlantılar|Yedekleme etki alanı denetleyicisi (İVB) bağlantıları ve arama içeriği kaynakları gibi arka uç veri sistemlerine bağlantıları çoğaltmak pratik olmayabilir.|
|Geri yükleme senaryolarında arama|Kurumsal arama dağıtımları oldukça benzersiz ve karmaşık olma eğiliminde olduğundan, veritabanlarından aramayı geri yüklemek için daha fazla yatırım gerekir. Kuruluşunuzun gerektirebileceği arama geri yükleme senaryolarını belirlemek ve uygulamak için bir danışman veya iş ortağıyla çalışabilirsiniz.|

Bu makalede sağlanan kılavuzda, şirket içi grubu zaten tasarlanmış ve dağıtılmış olduğu varsayılmaktadır.

## <a name="detailed-architecture"></a>Ayrıntılı mimari

İdeal olarak, Azure'daki kurtarma grubu yapılandırması, aşağıdakiler de dahil olmak üzere şirket içi üretim grubuyla aynıdır:

- Sunucu rollerinin aynı gösterimi

- Özelleştirmelerin aynı yapılandırması

- Arama bileşenlerinin aynı yapılandırması

Azure'daki ortam, üretim grubunun daha küçük bir sürümü olabilir. Yük devretmeden sonra kurtarma grubunun ölçeğini genişletmeyi planlıyorsanız, her sunucu rolü türünün başlangıçta temsil edilmesi önemlidir.

Bazı yapılandırmaların yük devretme ortamında çoğaltılması pratik olmayabilir. Yük devretme kümesinin beklenen hizmet düzeyini sağladığından emin olmak için yük devretme yordamlarını ve ortamını test etmeye özen gösterin.

Bu çözüm, SharePoint grubu için belirli bir topolojiyi reçete etmez. Bu çözümün odak noktası, yük devretme grubu için Azure'ı kullanmak ve iki ortam arasında günlük gönderimi ve DFSR uygulamaktır.

### <a name="warm-standby-environments"></a>Sıcak bekleme ortamları

Sıcak bir bekleme ortamında, Azure ortamındaki tüm sanal makineler çalışır durumdadır. Ortam, yük devretme alıştırması veya olayı için hazırdır.

Aşağıdaki şekilde, şirket içi SharePoint grubundan sıcak bekleme ortamı olarak yapılandırılmış Azure tabanlı SharePoint grubuna olağanüstü durum kurtarma çözümü gösterilmektedir.

**Şekil: Bir üretim grubunun ve sıcak bekleme kurtarma grubunun topolojisi ve temel öğeleri**

![bir SharePoint grubunun topolojisi ve sıcak bir bekleme kurtarma grubu.](../media/AZarch-AZWarmStndby.png)

Bu diyagramda:

- İki ortam yan yana gösterilir: şirket içi SharePoint grubu ve Azure'daki sıcak bekleme grubu.

- Her ortam bir dosya paylaşımı içerir.

- Her grup dört katman içerir. Yüksek kullanılabilirlik elde etmek için her katman ön uç hizmetleri, dağıtılmış önbellek, arka uç hizmetleri ve veritabanları gibi belirli bir rol için aynı şekilde yapılandırılmış iki sunucu veya sanal makine içerir. Bu çizimde belirli bileşenleri çağırmak önemli değildir. İki grup aynı şekilde yapılandırılır.

- Dördüncü katman, veritabanı katmanıdır. Günlük gönderimi, günlükleri şirket içi ortamdaki ikincil veritabanı sunucusundan aynı ortamdaki dosya paylaşımına kopyalamak için kullanılır.

- DFSR, şirket içi ortamdaki dosya paylaşımındaki dosyaları Azure ortamındaki dosya paylaşımına kopyalar.

- Günlük gönderimi, günlükleri Azure ortamındaki dosya paylaşımından kurtarma ortamındaki SQL Server AlwaysOn kullanılabilirlik grubundaki birincil çoğaltmaya yeniden yürüter.

### <a name="cold-standby-environments"></a>Soğuk bekleme ortamları

Soğuk bekleme ortamında, SharePoint grubu sanal makinelerinin çoğu kapatılabilir. (Her sanal makinenin etki alanıyla eşitlenebilmesi için sanal makineleri zaman zaman başlatmanızı (örneğin, iki haftada bir veya ayda bir) öneririz.) Günlük gönderme ve DFSR işlemlerinin sürekli olarak gerçekleştirilmesini sağlamak için Azure kurtarma ortamında aşağıdaki sanal makinelerin çalışır durumda kalması gerekir:

- Dosya paylaşımı

- Birincil veritabanı sunucusu

- Etki Alanı Hizmetleri ve DNS Windows Server Active Directory çalıştıran en az bir sanal makine

Aşağıdaki şekilde, dosya paylaşımı sanal makinesinin ve birincil SharePoint veritabanı sanal makinesinin çalıştığı bir Azure yük devretme ortamı gösterilmektedir. Diğer tüm SharePoint sanal makineler durdurulur. Windows Server Active Directory ve DNS çalıştıran sanal makine gösterilmez.

**Şekil: Çalışan sanal makineler ile soğuk bekleme kurtarma grubu**

![Azure'da SharePoint soğuk bekleme çözümünün öğeleri.](../media/AZarch-AZColdStndby.png)

Soğuk bekleme ortamına yük devretme işleminden sonra tüm sanal makineler başlatılır ve veritabanı sunucularının yüksek kullanılabilirliğini elde etme yöntemi, SQL Server AlwaysOn kullanılabilirlik grupları gibi yapılandırılmalıdır.

Birden çok depolama grubu uygulanırsa (veritabanları birden fazla SQL Server yüksek kullanılabilirlik kümesine yayılır), depolama grubuyla ilişkili günlükleri kabul etmek için her depolama grubu için birincil veritabanının çalışıyor olması gerekir.

### <a name="skills-and-experience"></a>Beceriler ve deneyim

Bu olağanüstü durum kurtarma çözümünde birden çok teknoloji kullanılır. Bu teknolojilerin beklendiği gibi etkileşimde bulunmasına yardımcı olmak için şirket içi ve Azure ortamındaki her bileşenin doğru şekilde yüklenmesi ve yapılandırılması gerekir. Bu çözümü ayarlayan kişi veya ekibin, aşağıdaki makalelerde açıklanan teknolojilerle ilgili güçlü bir çalışma bilgisi ve uygulamalı becerilere sahip olması önerilir:

- [Dağıtılmış Dosya Sistemi (DFS) Çoğaltma Hizmetleri](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))

- [SQL Server ile sunucu yük devretme kümelemesi (WSFC) Windows](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)

- [AlwaysOn Kullanılabilirlik Grupları (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)

- [SQL Server Veritabanlarını Yedekleme ve Geri Yükleme](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)

- [SharePoint Server 2013 yükleme ve grup dağıtımı](/SharePoint/install/installation-and-configuration-overview)

- [Microsoft Azure](/azure/)

Son olarak, bu teknolojilerle ilişkili görevleri otomatikleştirmek için kullanabileceğiniz betik oluşturma becerilerini öneririz. Bu çözümde açıklanan tüm görevleri tamamlamak için kullanılabilir kullanıcı arabirimlerini kullanmak mümkündür. Ancak el ile uygulanan bir yaklaşım zaman alıcı ve hataya yatkın olabilir ve tutarsız sonuçlar verir.

Windows PowerShell ek olarak, SQL Server, SharePoint Server ve Azure için Windows PowerShell kitaplıklar da vardır. Olağanüstü durum kurtarma ortamınızı yapılandırma ve koruma süresini azaltmaya yardımcı olabilecek T-SQL'ı unutmayın.

## <a name="disaster-recovery-roadmap"></a>Olağanüstü durum kurtarma yol haritası

![SharePoint olağanüstü durum kurtarma yol haritasının görsel gösterimi.](../media/Azure-DRroadmap.png)

Bu yol haritası, üretimde dağıtılmış bir SharePoint Server 2013 grubuna sahip olduğunuzu varsayar.

**Tablo: Olağanüstü durum kurtarma yol haritası**

|Aşama|Açıklama|
|---|---|
|1. Aşama|Olağanüstü durum kurtarma ortamını tasarlayın.|
|2. Aşama|Azure sanal ağını ve VPN bağlantısını oluşturun.|
|3. Aşama|Windows Active Directory ve Etki Alanı Ad Hizmetleri'ni Azure sanal ağına dağıtın.|
|4. Aşama|Azure'da SharePoint kurtarma grubu dağıtın.|
|5. Aşama|Grupların arasında DFSR'yi ayarlayın.|
|6. Aşama|Kurtarma grubuna günlük gönderimini ayarlayın.|
|7. Aşama|Yük devretme ve kurtarma çözümlerini doğrulayın. Bu, aşağıdaki yordamları ve teknolojileri içerir: <br/> Günlük gönderimi durdurulsun. <br/> Yedekleri geri yükleyin. <br/> Gezinme içeriği. <br/> Hizmetleri kurtarma. <br/> DNS kayıtlarını yönetme.|

## <a name="phase-1-design-the-disaster-recovery-environment"></a>1. Aşama: Olağanüstü durum kurtarma ortamını tasarlama

SharePoint kurtarma grubu da dahil olmak üzere olağanüstü durum kurtarma ortamını tasarlamak [için SharePoint 2013 için Microsoft Azure Mimarileri'ndeki](microsoft-azure-architectures-for-sharepoint-2013.md) yönergeleri kullanın. Tasarım işlemini başlatmak için [Azure Visio dosyasındaki SharePoint Olağanüstü Durum Kurtarma Çözümü'ndeki](https://go.microsoft.com/fwlink/p/?LinkId=392554) grafikleri kullanabilirsiniz. Azure ortamında herhangi bir çalışmaya başlamadan önce ortamın tamamını tasarlamanızı öneririz.

[SharePoint 2013 için Microsoft Azure Mimarileri'nde](microsoft-azure-architectures-for-sharepoint-2013.md) sanal ağı, VPN bağlantısını, Active Directory'yi ve SharePoint grubunu tasarlama yönergelerine ek olarak, Azure ortamına bir dosya paylaşımı rolü eklediğinizden emin olun.

Olağanüstü durum kurtarma çözümünde günlük gönderimini desteklemek için veritabanı rollerinin bulunduğu alt ağa bir dosya paylaşımı sanal makinesi eklenir. Dosya paylaşımı, SQL Server AlwaysOn kullanılabilirlik grubu için düğüm çoğunluğunun üçüncü düğümü olarak da görev alır. Bu, SQL Server AlwaysOn kullanılabilirlik gruplarını kullanan standart bir SharePoint grubu için önerilen yapılandırmadır.

> [!NOTE]
> Veritabanının SQL Server AlwaysOn kullanılabilirlik grubuna katılması için önkoşulları gözden geçirmek önemlidir. Daha fazla bilgi için bkz. [AlwaysOn Kullanılabilirlik Grupları için Önkoşullar, Kısıtlamalar ve Öneriler](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability).

**Şekil: Olağanüstü durum kurtarma çözümü için kullanılan dosya sunucusunun yerleşimi**

![SharePoint veritabanı sunucusu rollerini içeren aynı bulut hizmetine eklenen bir dosya paylaşımı VM'sini gösterir.](../media/AZenv-FSforDFSRandWSFC.png)

Bu diyagramda, Azure'da veritabanı sunucusu rollerini içeren aynı alt ağa bir dosya paylaşımı sanal makinesi eklenir. Dosya paylaşımı sanal makinesini SQL Server rolleri gibi diğer sunucu rolleriyle bir kullanılabilirlik kümesine eklemeyin.

Günlüklerin yüksek kullanılabilirliği konusunda endişe duyuyorsanız, [Azure Blob Depolama Hizmeti ile SQL Server yedekleme ve geri yükleme](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service) kullanarak farklı bir yaklaşım benimsemeyi göz önünde bulundurun. Bu, Azure'da günlükleri doğrudan blob depolama URL'sine kaydeden yeni bir özelliktir. Bu çözüm, bu özelliği kullanma hakkında rehberlik içermez.

Kurtarma grubu tasarlarken, başarılı bir olağanüstü durum kurtarma ortamının kurtarmak istediğiniz üretim grubuna doğru yansıttığını unutmayın. Kurtarma grubunun boyutu, kurtarma grubunun tasarımında, dağıtımında ve testinde en önemli şey değildir. Grup ölçeği, iş gereksinimlerine göre kuruluştan kuruluşa değişir. Ölçeği azaltılmış bir grubu kısa bir kesinti için veya performans ve kapasite talepleri grubu ölçeklendirmenizi gerektirene kadar kullanmak mümkün olabilir.

Kurtarma grubu, hizmet düzeyi sözleşmesi (SLA) gereksinimlerinizi karşılayacak ve işinizi desteklemek için ihtiyacınız olan işlevselliği sağlayacak şekilde üretim grubuyla mümkün olduğunca aynı şekilde yapılandırın. Olağanüstü durum kurtarma ortamını tasarlarken, üretim ortamınız için değişiklik yönetimi sürecinize de bakın. Üretim ortamıyla aynı aralıkta kurtarma ortamını güncelleştirerek değişiklik yönetimi işlemini kurtarma ortamına genişletmenizi öneririz. Değişiklik yönetimi sürecinin bir parçası olarak grup yapılandırmanızın, uygulamalarınızın ve kullanıcılarınızın ayrıntılı envanterini korumanızı öneririz.

## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>2. Aşama: Azure sanal ağını ve VPN bağlantısını oluşturma

[Microsoft Azure bir sanal ağa şirket içi ağ Bağlan](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md), sanal ağı Azure'da nasıl planlayıp dağıtabileceğinizi ve VPN bağlantısını nasıl oluşturabileceğinizi gösterir. Aşağıdaki yordamları tamamlamak için konudaki yönergeleri izleyin:

- Sanal Ağ özel IP adresi alanını planlayın.

- Sanal Ağ için yönlendirme altyapısı değişikliklerini planlayın.

- Şirket içi VPN cihazına gelen ve bu cihazdan gelen trafik için güvenlik duvarı kuralları planlayın.

- Azure'da şirket içi sanal ağı oluşturun.

- Şirket içi ağınız ile Sanal Ağ arasında yönlendirmeyi yapılandırın.

## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>3. Aşama: Active Directory ve Etki Alanı Ad Hizmetleri'ni Azure sanal ağına dağıtma

Bu aşama, SharePoint [2013 için Microsoft Azure Mimarileri'nde](microsoft-azure-architectures-for-sharepoint-2013.md) açıklandığı gibi ve aşağıdaki şekilde gösterildiği gibi karma bir senaryoda Sanal Ağ hem Windows Server Active Directory hem de DNS dağıtmayı içerir.

**Şekil: Karma Active Directory etki alanı yapılandırması**

![Azure sanal ağına dağıtılan iki sanal makine ve SharePoint Grubu alt ağı çoğaltma etki alanı denetleyicileri ve DNS sunucularıdır.](../media/AZarch-HyADdomainConfig.png)

Çizimde, aynı alt ağa iki sanal makine dağıtılır. Bu sanal makinelerin her ikisi de iki rol barındırmaktadır: Active Directory ve DNS.

Azure'da Active Directory'yi dağıtmadan önce [Azure Sanal Makineler'da Windows Server Active Directory Dağıtma Yönergeleri'ne](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100) bakın. Bu yönergeler, çözümünüz için farklı bir mimariye mi yoksa farklı yapılandırma ayarlarına mı ihtiyacınız olduğunu belirlemenize yardımcı olur.

Azure'da etki alanı denetleyicisi ayarlama hakkında ayrıntılı yönergeler için bkz. [Azure Sanal Ağlarında Çoğaltma Active Directory Etki Alanı Denetleyicisi Yükleme](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).

Bu aşamadan önce sanal makineleri Sanal Ağ dağıtmadınız. Active Directory ve DNS barındırmak için sanal makineler büyük olasılıkla çözüm için ihtiyacınız olan en büyük sanal makineler değildir. Bu sanal makineleri dağıtmadan önce, önce Sanal Ağ kullanmayı planladığınız en büyük sanal makineyi oluşturun. Bu, çözümünüzün Azure'da ihtiyacınız olan en büyük boyuta izin veren bir etikete sahip olmasını sağlamaya yardımcı olur. Şu anda bu sanal makineyi yapılandırmanız gerekmez. Sadece oluşturun ve bir kenara bırakın. Bunu yapmazsanız, daha sonra daha büyük sanal makineler oluşturmaya çalıştığınızda bir sınırlamayla karşılaşabilirsiniz. Bu, bu makalenin yazıldığı sırada bir sorundu.

## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>4. Aşama: Azure'da SharePoint kurtarma grubu dağıtma

SharePoint grubu tasarım planlarınıza göre Sanal Ağ dağıtın. Azure'da SharePoint rolleri dağıtmadan önce [Azure Altyapı Hizmetleri'nde SharePoint 2013 planlama'nın](/previous-versions/azure/dn275958(v=azure.100)) gözden geçirilmesi yararlı olabilir.

Kavram kanıtı ortamımızı oluşturarak öğrendiğimiz aşağıdaki uygulamaları göz önünde bulundurun:

- Azure portal veya PowerShell kullanarak sanal makineler oluşturun.

- Azure ve Hyper-V dinamik belleği desteklemez. Bunun performans ve kapasite planlarınıza dahil olduğundan emin olun.

- Sanal makineleri, sanal makinenin oturum açma işleminden değil Azure arabiriminden yeniden başlatın. Azure arabirimini kullanmak daha iyi çalışır ve daha tahmin edilebilirdir.

- Maliyetlerden tasarruf etmek için bir sanal makineyi kapatmak istiyorsanız Azure arabirimini kullanın. Sanal makine oturum açma işlemini kapatırsanız ücretler tahakkuk etmeye devam eder.

- Sanal makineler için bir adlandırma kuralı kullanın.

- Sanal makinelerin dağıtıldığı veri merkezi konumuna dikkat edin.

- Azure'daki otomatik ölçeklendirme özelliği SharePoint rolleri için desteklenmez.

- Site koleksiyonları gibi geri yüklenecek öğeleri grup içinde yapılandırmayın.

## <a name="phase-5-set-up-dfsr-between-the-farms"></a>5. Aşama: Gruplarda DFSR'yi ayarlama

DFSR kullanarak dosya çoğaltmayı ayarlamak için DNS Yönetimi ek bileşenini kullanın. Ancak DFSR kurulumundan önce şirket içi dosya sunucunuzda ve Azure dosya sunucunuzda oturum açın ve hizmeti Windows'de etkinleştirin.

Sunucu Yöneticisi Panosu'ndan aşağıdaki adımları tamamlayın:

- Yerel sunucuyu yapılandırın.

- **Rol ve Özellik Ekleme Sihirbazı'nı** başlatın.

- **Dosya ve Depolama Hizmetleri** düğümünü açın.

- **DFS Ad Alanları** ve **DFS çoğaltma'ya** tıklayın.

- Sihirbaz adımlarını tamamlamak için **İleri'ye** tıklayın.

Aşağıdaki tabloda DFSR başvuru makalelerine ve blog gönderilerine bağlantılar sağlanmaktadır.

**Tablo: DFSR için başvuru makaleleri**

|Başlık|Açıklama|
|---|---|
|[Çoğaltma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))|Çoğaltma bağlantıları içeren DFS Yönetimi TechNet konusu|
|[DFS Çoğaltma: Hayatta Kalma Kılavuzu](https://go.microsoft.com/fwlink/p/?LinkId=392737)|DFS bilgilerine bağlantılar içeren wiki|
|[DFS Çoğaltma: Sık Sorulan Sorular](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10))|DFS Çoğaltma TechNet konusu|
|[Jose Barreto'nun Blogu](/archive/blogs/josebda/)|Microsoft'taki Dosya Sunucusu ekibinde Sorumlu Program Yöneticisi tarafından yazılan blog|
|[Microsoft'taki Depolama Ekibi - Dosya Dolabı Blogu](https://go.microsoft.com/fwlink/p/?LinkId=392740)|Windows Server'daki dosya hizmetleri ve depolama özellikleri hakkında blog|

## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>6. Aşama: Kurtarma grubuna günlük gönderimini ayarlama

Günlük gönderimi, bu ortamda olağanüstü durum kurtarmayı ayarlamak için kritik bir bileşendir. Birincil veritabanı sunucusu örneğinden ikincil veritabanı sunucusu örneğine veritabanları için işlem günlüğü dosyalarını otomatik olarak göndermek için günlük gönderimi kullanabilirsiniz. Günlük gönderimini ayarlamak için bkz. [SharePoint 2013'te günlük gönderimini yapılandırma](/sharepoint/administration/configure-log-shipping).

> [!IMPORTANT]
> SharePoint Server'da günlük gönderim desteği belirli veritabanlarıyla sınırlıdır. Daha fazla bilgi için bkz[. SharePoint veritabanları için desteklenen yüksek kullanılabilirlik ve olağanüstü durum kurtarma seçenekleri (SharePoint 2013)](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas).

## <a name="phase-7-validate-failover-and-recovery"></a>7. Aşama: Yük devretmeyi ve kurtarmayı doğrulama

Bu son aşamanın amacı olağanüstü durum kurtarma çözümünün planlandığı gibi çalıştığını doğrulamaktır. Bunu yapmak için üretim grubu kapatan ve kurtarma grubu yerine başlatan bir yük devretme olayı oluşturun. Yük devretme senaryolarını el ile veya betikleri kullanarak başlatabilirsiniz.

İlk adım, grup hizmetleri veya içerik için gelen kullanıcı isteklerini durdurmaktır. Bunu, DNS girdilerini devre dışı bırakarak veya ön uç web sunucularını kapatarak yapabilirsiniz. Grup "devre dışı" olduktan sonra kurtarma grubuna yük devredebilirsiniz.

### <a name="stop-log-shipping"></a>Günlük gönderimi durdurulsun

Grup kurtarmadan önce günlük gönderimi durdurmanız gerekir. Önce Azure'daki ikincil sunucuda günlük gönderimini durdurun ve ardından şirket içi birincil sunucuda durdurun. Önce ikincil sunucuda, ardından birincil sunucuda günlük gönderimini durdurmak için aşağıdaki betiği kullanın. Betikteki veritabanı adları ortamınıza bağlı olarak farklı olabilir.

```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')
```

### <a name="restore-the-backups"></a>Yedeklemeleri geri yükleme

Yedeklemeler oluşturuldukları sırayla geri yüklenmelidir. Belirli bir işlem günlüğü yedeklemesini geri yükleyebilmeniz için önce kaydedilmemiş işlemleri (yani kullanarak  `WITH NORECOVERY`) geri almadan aşağıdaki önceki yedeklemeleri geri yüklemeniz gerekir:

- Tam veritabanı yedeklemesi ve son değişiklik yedeklemesi - Varsa, belirli bir işlem günlüğü yedeğinden önce alınan bu yedeklemeleri geri yükleyin. En son tam veya değişiklik veritabanı yedeklemesi oluşturulmadan önce veritabanı tam kurtarma modelini veya toplu günlüğe kaydedilen kurtarma modelini kullanıyordu.

- Tüm işlem günlüğü yedeklemeleri - Tam veritabanı yedeklemesi veya değişiklik yedeğinden sonra (geri yüklerseniz) ve belirli bir işlem günlüğü yedeğinden önce alınan tüm işlem günlüğü yedeklemelerini geri yükleyin. Günlük yedeklemeleri, günlük zincirinde herhangi bir boşluk olmadan oluşturuldukları sırada uygulanmalıdır.

sitelerin işlenmesi için ikincil sunucudaki içerik veritabanını kurtarmak için kurtarmadan önce tüm veritabanı bağlantılarını kaldırın. Veritabanını geri yüklemek için aşağıdaki SQL deyimini çalıştırın.

```SQL
restore database WSS_Content with recovery
```

> [!IMPORTANT]
> T-SQL'ı açıkça kullandığınızda, belirsizliği ortadan kaldırmak için her RESTORE deyiminde **WITH NORECOVERY** veya **WITH RECOVERY** belirtin; betikler yazılırken bu çok önemlidir. Tam ve değişiklik yedeklemeleri geri yüklendikten sonra işlem günlükleri SQL Server Management Studio geri yüklenebilir. Ayrıca günlük gönderimi zaten durdurulduğu için içerik veritabanı bekleme durumunda olduğundan, durumu tam erişim olarak değiştirmeniz gerekir.

SQL Server Management Studio **WSS_Content veritabanına sağ** tıklayın, **TasksRestore'un** >  üzerine gelin ve **İşlem Günlüğü'ne** tıklayın (tam yedeklemeyi geri yüklemediyseniz bu kullanılamaz). Daha fazla bilgi için bkz[. İşlem Günlüğü Yedeklemesini (SQL Server) kaydetme](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).

### <a name="crawl-the-content-source"></a>İçerik kaynağında gezinme

Arama Hizmetini geri yüklemek için her içerik kaynağı için tam gezinme başlatmanız gerekir. Şirket içi grubundan arama önerileri gibi bazı analiz bilgilerini kaybettiğinizi unutmayın. Tüm gezinmeleri başlatmadan önce **Restore-SPEnterpriseSearchServiceApplication** Windows PowerShell cmdlet'ini kullanın ve Search_Service__DB_ günlük tarafından gönderilen ve çoğaltılan Arama Yönetimi veritabanını **\<GUID\>belirtin.** Bu cmdlet arama yapılandırması, şema, yönetilen özellikler, kurallar ve kaynaklar sağlar ve diğer bileşenlerin varsayılan kümesini oluşturur.

Tam gezinme başlatmak için aşağıdaki adımları tamamlayın:

1. SharePoint 2013 Yönetim Merkezi'nde **, Uygulama** **YönetimiHizmet** >  uygulamalarını  > **yönet'e** gidin ve gezinmek istediğiniz Arama Hizmeti uygulamasına tıklayın.

2. **Arama Yönetimi** sayfasında **İçerik Kaynakları'na** tıklayın, istediğiniz içerik kaynağının üzerine gelin, oka tıklayın ve ardından **Tam Gezinmeyi Başlat'a** tıklayın.

### <a name="recover-farm-services"></a>Grup hizmetlerini kurtarma

Aşağıdaki tabloda, günlükle gönderilen veritabanlarına sahip hizmetlerin, veritabanları olan ancak günlük gönderimi ile geri yüklenmesi önerilmeyen hizmetlerin ve veritabanı olmayan hizmetlerin nasıl kurtarılması gösterilmektedir.

> [!IMPORTANT]
> Şirket içi SharePoint veritabanını Azure ortamına geri yüklemek, Azure'a el ile yüklemediğiniz SharePoint hizmetlerini kurtarmaz.

**Tablo: Hizmet uygulaması veritabanı başvurusu**

|Bu hizmetleri günlükle gönderilen veritabanlarından geri yükleme|Bu hizmetlerin veritabanları vardır, ancak veritabanlarını geri yüklemeden bu hizmetleri başlatmanızı öneririz|Bu hizmetler verileri veritabanlarında depolamaz; yük devretmeden sonra bu hizmetleri başlatın|
|---|---|---|
|Makine Çevirisi Hizmeti <br/> Yönetilen Meta Veri Hizmeti <br/> Güvenli Depolama Hizmeti <br/> Kullanıcı Profili. (Yalnızca Profil ve Sosyal Etiketleme veritabanları desteklenir. Eşitleme veritabanı desteklenmiyor.) <br/> Microsoft SharePoint Foundation Aboneliği Ayarlar Hizmeti|Kullanım ve Sistem Durumu Veri Toplama <br/> Durum hizmeti <br/> Word otomasyonu|Excel Services <br/> PerformancePoint Hizmetleri <br/> PowerPoint Dönüştürme <br/> Visio Grafik Hizmeti <br/> İş Yönetimi|

Aşağıdaki örnekte, Yönetilen Meta Veri hizmetinin veritabanından nasıl geri yükleneceği gösterilmektedir.

Bu, mevcut Managed_Metadata_DB veritabanını kullanır. Bu veritabanı günlük olarak gönderilir, ancak ikincil grup üzerinde etkin bir hizmet uygulaması yoktur, bu nedenle hizmet uygulaması uygulandıktan sonra bağlanması gerekir.

İlk olarak kullanın  `New-SPMetadataServiceApplication`ve geri yüklenen veritabanının  `DatabaseName` adıyla anahtarı belirtin.

Ardından, ikincil sunucuda yeni Yönetilen Meta Veri Hizmeti Uygulamasını aşağıdaki gibi yapılandırın:

- Ad: Yönetilen Meta Veri Hizmeti

- Veritabanı sunucusu: Gönderilen işlem günlüğünden veritabanı adı

- Veritabanı adı: Managed_Metadata_DB

- Uygulama havuzu: hizmet uygulamalarını SharePoint

### <a name="manage-dns-records"></a>DNS kayıtlarını yönetme

SharePoint grubunuzu işaret etmek için DNS kayıtlarını el ile oluşturmanız gerekir.

Birden çok ön uç web sunucunuzun olduğu çoğu durumda, Windows Server 2012 ağ yükü dengeleme özelliğinden veya istekleri grubunuzdaki web ön uç sunucuları arasında dağıtmak için bir donanım yük dengeleyiciden yararlanmak mantıklıdır. Ağ yükü dengeleme, web ön uç sunucularınızdan biri başarısız olursa istekleri diğer sunuculara dağıtarak riski azaltmaya da yardımcı olabilir.

Genellikle, ağ yükü dengelemeyi ayarladığınızda kümenize tek bir IP adresi atanır. Ardından, ağınız için DNS sağlayıcısında kümeye işaret eden bir DNS ana bilgisayar kaydı oluşturursunuz. (Bu proje için, şirket içi veri merkezi hatası durumunda dayanıklılık için Azure'a bir DNS sunucusu yerleştireceğiz.) Örneğin, Active Directory'deki DNS Yöneticisi'nde, örneğin adlı  `https://sharepoint.contoso.com`, yük dengeli kümenizin IP adresine işaret eden bir DNS kaydı oluşturabilirsiniz.

SharePoint grubunuza dış erişim için, istemcilerin intranetinizde kullandığı URL'ye (örneğin, `https://sharepoint.contoso.com`) sahip bir dış DNS sunucusunda güvenlik duvarınızdaki bir dış IP adresine işaret eden bir konak kaydı oluşturabilirsiniz. (Bu örneği kullanarak en iyi yöntem, iç DNS sunucusunun dns isteklerini dış DNS sunucunuza yönlendirmek yerine doğrudan SharePoint grubu kümesi için yetkili olması ve istekleri doğrudan yönlendirmesi için `contoso.com` bölünmüş DNS ayarlamaktır.) Ardından, istemcilerin aradıkları kaynakları bulması için dış IP adresini şirket içi kümenizin iç IP adresiyle eşleyebilirsiniz.

Buradan birkaç farklı olağanüstü durum kurtarma senaryosuyla karşılaşabilirsiniz:

 **Örnek senaryo: Şirket içi SharePoint grubu, şirket içi SharePoint grubunda donanım hatası nedeniyle kullanılamıyor.** Bu durumda, Azure SharePoint grubuna yük devretme adımlarını tamamladıktan sonra, şirket içi grupta yaptığınız gibi kurtarma SharePoint grubundaki web ön uç sunucularında ağ yükü dengelemeyi yapılandırabilirsiniz. Ardından, iç DNS sağlayıcınızdaki konak kaydını kurtarma grubu küme IP adresine işaret etmek için yeniden yönlendirebilirsiniz. İstemcilerde önbelleğe alınmış DNS kayıtlarının yenilenmesi ve kurtarma grubuna işaret etmelerinin biraz zaman alabileceğini unutmayın.

 **Örnek senaryo: Şirket içi veri merkezi tamamen kaybolur.** Bu senaryo, yangın veya sel gibi doğal bir afet nedeniyle ortaya çıkabilir. Bu durumda, bir kuruluş için büyük olasılıkla başka bir bölgede barındırılan ikincil bir veri merkezinizin yanı sıra kendi dizin hizmetleri ve DNS'sine sahip Azure alt ağınız olacaktır. Önceki olağanüstü durum senaryosunda olduğu gibi, iç ve dış DNS kayıtlarınızı Azure SharePoint grubuna yönlendirecek şekilde yeniden yönlendirebilirsiniz. Dns kaydı yayma işleminin biraz zaman alabileceğini de unutmayın.

Konak adlı site [koleksiyonu mimarisi ve dağıtımında (SharePoint 2013)](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) önerilen ana bilgisayar adlı site koleksiyonları kullanıyorsanız, SharePoint grubunuzda aynı web uygulaması tarafından barındırılan ve benzersiz DNS adlarıyla (örneğin, `https://sales.contoso.com` ve `https://marketing.contoso.com`) birkaç site koleksiyonunuz olabilir. Bu durumda, küme IP adresinize işaret eden her site koleksiyonu için DNS kayıtları oluşturabilirsiniz. bir istek SharePoint web ön uç sunucularınıza ulaştıktan sonra, her isteği uygun site koleksiyonuna yönlendirmeyi işler.

## <a name="microsoft-proof-of-concept-environment"></a>Microsoft kavram kanıtı ortamı

Bu çözüm için kavram kanıtı ortamı tasarladık ve test ettik. Test ortamımızın tasarım hedefi, müşteri ortamında bulabileceğimiz bir SharePoint grubu dağıtmak ve kurtarmaktı. Birkaç varsayımda bulunduk, ancak çiftliğin herhangi bir özelleştirme olmadan kullanıma hazır tüm işlevleri sağlaması gerektiğini biliyorduk. Topoloji, alandan ve ürün grubundan en iyi yöntem kılavuzu kullanılarak yüksek kullanılabilirlik için tasarlanmıştır.

Aşağıdaki tabloda, şirket içi test ortamı için oluşturduğumuz ve yapılandırdığımız Hyper-V sanal makineleri açıklanmaktadır.

**Tablo: Şirket içi test için sanal makineler**

|Sunucu adı|Rol|Yapılandırma|
|---|---|---|
|DC1|Active Directory ile etki alanı denetleyicisi.|İki işlemci <br/> 512 MB ile 4 GB RAM arasında <br/> 1 x 127 GB sabit disk|
|RRAS|Yönlendirme ve Uzaktan Erişim Hizmeti (RRAS) rolüyle yapılandırılmış sunucu.|İki işlemci <br/> 2-8 GB RAM <br/> 1 x 127 GB sabit disk|
|FS1|Yedekler için paylaşımları ve DFSR için bir bitiş noktası olan dosya sunucusu.|Dört işlemci <br/> 2-12 GB RAM <br/> 1 x 127 GB sabit disk <br/> 1 x 1 TB sabit disk (SAN) <br/> 1 x 750 GB sabit disk|
|SP-WFE1, SP-WFE2|Ön uç web sunucuları.|Dört işlemci <br/> 16 GB RAM|
|SP-APP1, SP-APP2, SP-APP3|Uygulama sunucuları.|Dört işlemci <br/> 2-16 GB RAM|
|SP-SQL-HA1, SP-SQL-HA2|Yüksek kullanılabilirlik sağlamak için SQL Server 2012 AlwaysOn kullanılabilirlik gruplarıyla yapılandırılmış veritabanı sunucuları. Bu yapılandırmada birincil ve ikincil çoğaltmalar olarak SP-SQL-HA1 ve SP-SQL-HA2 kullanılır.|Dört işlemci <br/> 2-16 GB RAM|

Aşağıdaki tabloda, şirket içi test ortamı için ön uç web ve uygulama sunucuları için oluşturduğumuz ve yapılandırdığımız Hyper-V sanal makineleri için sürücü yapılandırmaları açıklanmaktadır.

**Tablo: Şirket içi test için Ön Uç Web ve Uygulama sunucuları için sanal makine sürücüsü gereksinimleri**

|Sürücü harfi|Boyutu|Dizin adı|Yol|
|---|---|---|---|
|C|80|Sistem sürücüsü|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|80|Günlük sürücüsü (40 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|80|Sayfa (36 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQLDATA\\|

Aşağıdaki tabloda, şirket içi veritabanı sunucuları olarak kullanılmak üzere oluşturulan ve yapılandırılan Hyper-V sanal makineleri için sürücü yapılandırmaları açıklanmaktadır. **Veritabanı Altyapısı Yapılandırması** sayfasında, aşağıdaki tabloda gösterilen ayarları ayarlamak ve onaylamak için **Veri Dizinleri** sekmesine erişin.

**Tablo: Şirket içi test için veritabanı sunucusu için sanal makine sürücüsü gereksinimleri**

|Sürücü harfi|Boyutu|Dizin adı|Yol|
|---|---|---|---|
|C|80|Veri kök dizini|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\|
|E|500|Kullanıcı veritabanı dizini|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|500|Kullanıcı veritabanı günlük dizini|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|G|500|Temp DB dizini|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|H|500|Temp DB günlük dizini|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|

### <a name="setting-up-the-test-environment"></a>Test ortamını ayarlama

Farklı dağıtım aşamaları sırasında, test ekibi genellikle önce şirket içi mimaride, ardından ilgili Azure ortamında çalışırdı. Bu, şirket içi üretim çiftliklerinin zaten çalışmakta olduğu genel gerçek dünya durumlarını yansıtır. Daha da önemlisi, geçerli üretim iş yükünü, kapasitesini ve tipik performansı bilmeniz gerekir. İş gereksinimlerini karşılayabilen bir olağanüstü durum kurtarma modeli oluşturmaya ek olarak, kurtarma grubu sunucularını minimum hizmet düzeyi sunmak için boyutlandırmanız gerekir. Soğuk veya sıcak bekleme ortamında kurtarma grubu genellikle bir üretim grubundan daha küçüktür. Kurtarma grubu kararlı ve üretimde olduktan sonra, iş yükü gereksinimlerini karşılamak için grup ölçeği artırılabilir ve genişletilebilir.

Test ortamımızı aşağıdaki üç aşamada dağıttık:

- Karma altyapıyı ayarlama

- Sunucuları sağlama

- SharePoint gruplarını dağıtma

#### <a name="set-up-the-hybrid-infrastructure"></a>Karma altyapıyı ayarlama

Bu aşama, şirket içi grubu ve Azure'daki kurtarma grubu için bir etki alanı ortamı ayarlamayı içerir. Test ekibi, Active Directory'yi yapılandırmayla ilişkili normal görevlere ek olarak bir yönlendirme çözümü ve iki ortam arasında vpn bağlantısı uyguladı.

#### <a name="provision-the-servers"></a>Sunucuları sağlama

Grup sunucularına ek olarak, etki alanı denetleyicileri için sunucuların sağlanması ve bir sunucunun RRAS'nin yanı sıra siteden siteye VPN'yi işleyecek şekilde yapılandırılması gerekiyordu. DFSR hizmeti için iki dosya sunucusu sağlandı ve test ediciler için birkaç istemci bilgisayar sağlandı.

#### <a name="deploy-the-sharepoint-farms"></a>SharePoint gruplarını dağıtma

SharePoint grupları, gerekirse ortam sabitlemeyi ve sorun gidermeyi basitleştirmek için iki aşamada dağıtıldı. İlk aşamada her grup, gerekli işlevselliği desteklemek üzere topolojinin her katmanı için en az sunucu sayısına dağıtıldı.

SharePoint 2013 sunucularını oluşturmadan önce SQL Server yüklü veritabanı sunucularını oluşturduk. Bu yeni bir dağıtım olduğundan, SharePoint dağıtmadan önce kullanılabilirlik gruplarını oluşturduk. MCS en iyi uygulama kılavuzlarını temel alan üç grup oluşturduk.

> [!NOTE]
> SharePoint yüklemeden önce kullanılabilirlik grupları oluşturabilmek için yer tutucu veritabanları oluşturun. Daha fazla bilgi için bkz. [SharePoint 2013 için SQL Server 2012 AlwaysOn Kullanılabilirlik Gruplarını Yapılandırma](/SharePoint/administration/configure-an-alwayson-availability-group)

Grubu oluşturduk ve aşağıdaki sırayla ek sunuculara katıldık:

- SP-SQL-HA1 ve SP-SQL-HA2 sağlama.

- AlwaysOn'u yapılandırın ve grup için üç kullanılabilirlik grubu oluşturun.

- Merkezi Yönetim'i barındırmak için SP-APP1 sağlama.

- Dağıtılmış önbelleği barındırmak için SP-WFE1 ve SP-WFE2 sağlayın.

Komut satırında **psconfig.exe** çalıştırdığınızda _skipRegisterAsDistributedCachehost_ parametresini kullandık. Daha fazla bilgi için bkz. [SharePoint Server 2013'te akışları ve Dağıtılmış Önbellek hizmetini planlama](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).

Kurtarma ortamında aşağıdaki adımları yineledik:

- AZ-SQL-HA1 ve AZ-SQL-HA2'yi sağlayın.

- AlwaysOn'u yapılandırın ve grup için üç kullanılabilirlik grubu oluşturun.

- Merkezi Yönetim'i barındırmak için AZ-APP1 sağlayın.

- Dağıtılmış önbelleği barındırmak için AZ-WFE1 ve AZ-WFE2 sağlayın.

Dağıtılmış önbelleği yapılandırıp test kullanıcıları ve test içeriği ekledikten sonra dağıtımın ikinci aşamasını başlattık. Bunun için katmanların ölçeği genişletildi ve grup sunucularında grup mimarisinde açıklanan yüksek kullanılabilirlik topolojisini destekleyecek şekilde yapılandırıldı.

Aşağıdaki tabloda kurtarma grubumuz için ayarladığımız sanal makineler, alt ağlar ve kullanılabilirlik kümeleri açıklanmaktadır.

**Tablo: Kurtarma grubu altyapısı**

|Sunucu adı|Rol|Yapılandırma|Alt ağ|Kullanılabilirlik kümesi|
|---|---|---|---|---|
|spDRAD|Active Directory ile etki alanı denetleyicisi|İki işlemci <br/> 512 MB ile 4 GB RAM arasında <br/> 1 x 127 GB sabit disk|sp-ADservers||
|AZ-SP-FS|Yedekler için paylaşımları olan dosya sunucusu ve DFSR için bir uç nokta|A5 yapılandırması: <br/> İki işlemci <br/> 14 GB RAM <br/> 1 x 127 GB sabit disk <br/> 1 x 135 GB sabit disk <br/> 1 x 127 GB sabit disk <br/> 1 x 150 GB sabit disk|sp-databaseservers|DATA_SET|
|AZ-WFE1, AZ -WFE2|Ön Uç Web sunucuları|A5 yapılandırması: <br/> İki işlemci <br/> 14 GB RAM <br/> 1 x 127 GB sabit disk|sp-webservers|WFE_SET|
|AZ -APP1, AZ -APP2, AZ -APP3|Uygulama sunucuları|A5 yapılandırması: <br/> İki işlemci <br/> 14 GB RAM <br/> 1 x 127 GB sabit disk|sp-applicationservers|APP_SET|
|AZ -SQL-HA1, AZ -SQL-HA2|AlwaysOn kullanılabilirlik grupları için veritabanı sunucuları ve birincil ve ikincil çoğaltmalar|A5 yapılandırması: <br/> İki işlemci <br/> 14 GB RAM|sp-databaseservers|DATA_SET|

### <a name="operations"></a>Operasyonlar

Test ekibi grup ortamlarını dengeleyip işlevsel testi tamamladıktan sonra, şirket içi kurtarma ortamını yapılandırmak için gereken aşağıdaki işlem görevlerini başlattı:

- Tam ve değişiklik yedeklemelerini yapılandırın.

- İşlem günlüklerini şirket içi ortamıyla Azure ortamı arasında aktaran dosya sunucularında DFSR'yi yapılandırın.

- Birincil veritabanı sunucusunda günlük gönderimini yapılandırın.

- Gerektiğinde günlük gönderimi durumunu dengeleyebilir, doğrulayabilir ve sorun giderebilirsiniz. Bu, günlük gönderimi veya DFSR dosya eşitleme hatalarına neden olabilecek ağ gecikmesi gibi sorunlara neden olabilecek tüm davranışları tanımlamayı ve belgelemesini içerir.

### <a name="databases"></a>Veritaban -ları

Yük devretme testlerimiz aşağıdaki veritabanlarını içerir:

- Wss_content

- ManagedMetadata

- Profil VERITABANı

- Db'yi eşitleme

- Sosyal Veritabanı

- İçerik Türü Hub'ı (ayrılmış İçerik Türü Dağıtım Hub'ı için bir veritabanı)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

bölümünde, testimiz sırasında karşılaştığımız sorunlar ve çözümleri açıklanmaktadır.

### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Terim Deposu Yönetim Aracı'nın kullanılması "Yönetilen Meta Veri Deposu veya Bağlantı şu anda kullanılamıyor" hatasına neden oldu.

Web uygulaması tarafından kullanılan uygulama havuzu hesabının Terim Deposuna Okuma Erişimi iznine sahip olduğundan emin olun.

### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Özel terim kümeleri site koleksiyonunda kullanılamaz

İçerik site koleksiyonunuz ile içerik türü hub'ınız arasında eksik bir hizmet uygulaması ilişkisi olup olmadığını denetleyin. Ayrıca, **Yönetilen Meta Veriler - \<site collection name\> Bağlantı** özellikleri ekranının altında bu seçeneğin etkinleştirildiğinden emin olun: **Bu hizmet uygulaması, sütuna özgü terim kümeleri için varsayılan depolama konumudur.**

### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Get-ADForest Windows PowerShell komutu şu hatayı oluşturur: "'Get-ADForest' terimi cmdlet, işlev, betik dosyası veya çalıştırılabilir programın adı olarak tanınmıyor."

Kullanıcı profillerini ayarlarken Active Directory orman adına ihtiyacınız vardır. Rol ve Özellik Ekleme Sihirbazı'nda, Windows PowerShell için Active Directory Modülü'nü etkinleştirdiğinizden emin olun (**Ad DS ve AD LDS Araçları bölümü>Rol Yönetim Araçları>Uzak Sunucu Yönetim Araçları'nın** altında). Ayrıca, yazılım bağımlılıklarınızın yüklendiğinden emin olmak için **Get-ADForest** kullanmadan önce aşağıdaki komutları çalıştırın.

```powershell
Import-Module ServerManager
Import-Module ActiveDirectory
```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Kullanılabilirlik grubu oluşturma işlemi '' üzerinde 'AlwaysOn_health' XEvent oturumunu başlatma sırasında\<server name\> başarısız oluyor

Yük devretme kümenizin her iki düğümünün de "Duraklatıldı" veya "Durduruldu" durumunda olmadığından emin olun.

### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server günlük gönderme işi, dosya paylaşımına bağlanmaya çalışırken erişim reddedildi hatasıyla başarısız oluyor

SQL Server Agent varsayılan kimlik bilgileri yerine ağ kimlik bilgileri altında çalıştığından emin olun.

### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server günlük gönderim işi başarılı olduğunu gösterir, ancak hiçbir dosya kopyalanır

Bunun nedeni, bir kullanılabilirlik grubu için varsayılan yedekleme tercihinin **İkincil'i Tercih Et** olmasıdır. Günlük gönderim işini birincil sunucu yerine kullanılabilirlik grubu için ikincil sunucudan çalıştırdığınızdan emin olun; aksi takdirde iş sessizce başarısız olur.

### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Yönetilen Meta Veri hizmeti (veya diğer SharePoint hizmeti) yüklemeden sonra otomatik olarak başlatılamıyor

SharePoint Sunucunuzun performansına ve geçerli yüküne bağlı olarak hizmetlerin başlatılması birkaç dakika sürebilir. Hizmet için **El ile Başlat'a** tıklayın ve zaman zaman Sunucudaki Hizmetler ekranını yenileyerek hizmetin durumunu izlemek için başlangıç için yeterli zaman sağlayın. Hizmetin durdurulmuş durumda kalması durumunda tanılama günlüğü SharePoint etkinleştirin, hizmeti yeniden başlatmayı deneyin ve ardından günlükte hatalar olup olmadığını denetleyin. Daha fazla bilgi için bkz[. SharePoint 2013'te tanılama günlüğünü yapılandırma](/sharepoint/administration/configure-diagnostic-logging)

### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>DNS'yi Azure yük devretme ortamına değiştirdikten sonra istemci tarayıcıları SharePoint sitesi için eski IP adresini kullanmaya devam eder

DNS değişikliğiniz tüm istemciler tarafından hemen görülemeyebilir. Test istemcisinde, yükseltilmiş bir komut isteminden aşağıdaki komutu gerçekleştirin ve siteye yeniden erişmeyi deneyin.

```DOS
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Ek kaynaklar

[SharePoint veritabanları için desteklenen yüksek kullanılabilirlik ve olağanüstü durum kurtarma seçenekleri](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

[SharePoint 2013 için SQL Server 2012 AlwaysOn Kullanılabilirlik Gruplarını Yapılandırma](/SharePoint/administration/configure-an-alwayson-availability-group)

## <a name="see-also"></a>Ayrıca Bkz

[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)
