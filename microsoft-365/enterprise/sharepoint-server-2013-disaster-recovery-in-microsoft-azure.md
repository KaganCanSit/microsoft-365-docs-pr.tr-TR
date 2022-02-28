---
title: SharePoint Server 2013 Olağanüstü Durum Kurtarma Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
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
description: Bu makalede, şirket içi kurtarma ortamınız için olağanüstü durum kurtarma ortamı oluşturmak üzere Azure'ın nasıl SharePoint açıklanmıştır.
ms.openlocfilehash: 80b85aeb602cadf3fb2306c5ef929acbe35d3762
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988783"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>SharePoint Server 2013 Olağanüstü Durum Kurtarma Microsoft Azure

 Azure'ı kullanarak, şirket içi acil durum kurtarma ortamınız için bir acil durum SharePoint oluşturabilirsiniz. Bu makalede, bu çözümün nasıl tasarlan ve uygulandığını açıklanmıştır.

 **Acil durum kurtarma SharePoint Server 2013'e genel bakış videosunu izleyin**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 Şirket içi ortamınız olağanüstü SharePoint olduğunda, önceliğiniz sistemin yeniden hızlı bir şekilde yeniden kullanılabilirliğe sahip olmaktır. Acil durum kurtarma SharePoint içinde zaten çalışan bir yedek ortamınız olduğunda daha hızlı ve daha Microsoft Azure. Bu videoda, açık bir yük devretme SharePoint ana kavramlar açıklanmıştır ve bu makaledeki tüm ayrıntılar tamamlanmıştır.
  
Bu makaleyi aşağıdaki çözüm modeliyle kullanın: Acil **SharePoint Kurtarma'ya Microsoft Azure**.
  
[![SharePoint kurtarma işlemini Azure'a  gerektir.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Olağanüstü durum kurtarma için Azure Altyapı Hizmetlerini kullanma

Birçok kuruluş, şirket içi derleme ve bakım bakımları SharePoint olağanüstü durumlara neden olan bir kurtarma ortamına sahip değildir. Azure Altyapı Hizmetleri, olağanüstü durum kurtarma ortamları için, şirket içi alternatiflerden daha esnek ve daha ucuz olan etkileyici seçenekler sağlar.
  
Azure Altyapı Hizmetleri'nin kullanımıyla ilgili avantajlar şunlardır:
  
- **Daha az maliyetli kaynak** Şirket içi olağanüstü durum kurtarma ortamlarının bakımını ve ödemesini şirket içi durumlara göre daha az kaynak için kullanın. Kaynakların sayısı, hangi olağanüstü durum kurtarma ortamını seçtiğinize bağlıdır: soğuk bekleme, sıcak bekleme veya sıcak bekleme.
    
- **Daha iyi kaynak esnekliği** Bir facia durumunda, yükleme gereksinimlerini karşılamak için kurtarma SharePoint ölçeğini kolayca ölçeklendirin. Artık kaynaklara ihtiyacınız kalmadan ölçeklendirin.
    
- **Daha düşük veri merkezi taahhüdü** Farklı bir bölgeye ikincil veri merkezi yatırım yapmak yerine Azure Altyapı Hizmetleri'nde kullanın.
    
Olağanüstü durum kurtarma ile yeni başlayan kuruluşlar için daha az karmaşık seçenekler ve yüksek güvenlik gereksinimlerine sahip kuruluşlar için gelişmiş seçenekler vardır. Soğuk, sıcak ve sıcak bekleme ortamlarının tanımları, ortam bir bulut platformunda barındırıldıyken biraz farklıdır. Aşağıdaki tabloda, Azure'da bir kurtarma grubu SharePoint için bu ortamlar açık almaktadır.
  
**Tablo: Kurtarma ortamları**

|**Kurtarma ortamı türü**|**Açıklama**|
|:-----|:-----|
|Sıcak  <br/> |Tam boyutlu bir grup sağlandı, güncelleştirildi ve bekleme modunda çalışıyor.  <br/> |
|Isınma  <br/> |Sunucu grubu yerleşiktir ve sanal makineler de çalışıyor ve güncelleştirilir.  <br/> Kurtarma işlemi, içerik veritabanlarını iliştirme, hizmet uygulamaları sağlama ve içerikte gezinmeyi içerir.  <br/> Grup, üretim grubu daha küçük bir sürümü olabilir ve tam kullanıcı tabanına hizmet edecek şekilde ölçeklendirildi.  <br/> |
|Soğuk  <br/> |Sunucu grubu tümüyle yerleşiktir, ancak sanal makineler durdurulur.  <br/> Ortamın korunması, sanal makineleri zaman zaman başlatmayı, ortamı düzeltme eki uygulama, güncelleştirme ve doğrulamayı içerir.  <br/> Bir facia durumunda ortamın tamamını başlatma.  <br/> |
   
Kuruluş kurtarma süresi hedeflerini (RTOS) ve Kurtarma Noktası Hedeflerini (RRP) değerlendirmek önemlidir. Bu gereksinimler, hangi ortamın organizasyonunıza en uygun yatırım olduğunu belirler.
  
Bu makaledeki kılavuzda, sıcak bir bekleme ortamının nasıl uygulanıyor olduğu açıklanmıştır. Bu tür bir ortamı desteklemek için ek yordamları takip etmek zorunda da olsalar, bunu soğuk bekleme ortamına uyarlanabilir. Bu makalede, bekleme modundaki bir ortamın nasıl uygulanıyor olduğu açık değildir.
  
Olağanüstü durum kurtarma çözümleri hakkında daha fazla bilgi için bkz. [SharePoint 2013'te](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) yüksek kullanılabilirlik ve olağanüstü durum kurtarma kavramları ve [SharePoint 2013](/SharePoint/administration/plan-for-disaster-recovery) için bir olağanüstü durum kurtarma stratejisi seçme.
  
## <a name="solution-description"></a>Çözüm açıklaması

Acil durum kurtarma için sıcak bekleme çözümü aşağıdaki ortamı gerektirir:
  
- Şirket içi bir SharePoint üretim grubu
    
- Azure'SharePoint kurtarma grubu
    
- İki ortam arasında siteden siteye VPN bağlantısı
    
Aşağıdaki resimde bu üç öğenin gösterildiği yer almaktadır.
  
**Şekil: Azure'daki bir sıcak bekleme çözümünün öğeleri**

![Azure'da SharePoint bekleme çözümünün öğeleri.](../media/AZarch-AZWarmStndby.png)
  
SQL Server Yedeklemeleri ve işlem günlüklerini Azure'daki kurtarma sunucu grubuna kopyalamak için Dağıtılmış Dosya Sistemi Çoğaltması (ANDR) ile günlük gönderimi işlemi kullanılır: 
  
- BUDTİr, günlükleri üretim ortamından kurtarma ortamına iletir. WAN senaryosunda, BULIR, günlükleri doğrudan Azure'daki ikincil sunucuya teslim etmekten daha verimlidir.
    
- Günlükler, Azure'SQL Server ortamındaki sistemlere yeniden oynatıldı.
    
- Kurtarma alıştırması yapılana kadar, SharePoint gönderilen günlük dosyasını, kurtarma ortamındaki içerik veritabanlarına eklemezsiniz.
    
Grubu kurtarmak için aşağıdaki adımları uygulayın:
  
1. Günlük gönderimi durdurun.
    
2. Birincil grup için trafik kabul etmeyi durdurun.
    
3. Son işlem günlüklerini yeniden yürütme.
    
4. İçerik veritabanlarını sunucu grubuyla birlikte ekleme.
    
5. Çoğaltılmış hizmet veritabanlarından hizmet uygulamalarını geri yükleme.
    
6. Kurtarma sunucu alanına işaret etmek için Etki Alanı Adı Sistemi (DNS) kayıtlarını güncelleştirin.
    
7. Tam gezinmeye başlama.
    
Canlı kurtarmanın sorunsuzca çalışmasını sağlamak için bu adımları düzenli olarak provanızı ve bunları belgelenizi öneririz. İçerik veritabanlarını eklemek ve hizmet uygulamalarını geri yüklemek biraz zaman alır ve genellikle bazı el ile yapılandırmalar gerektirir.
  
Kurtarma işlemi gerçekleştirildikten sonra, bu çözüm aşağıdaki tabloda listelenen öğeleri sağlar.
  
**Tablo: Çözüm kurtarma hedefleri**

|**Öğe**|**Açıklama**|
|:-----|:-----|
|Siteler ve içerik  <br/> |Siteler ve içerik kurtarma ortamında kullanılabilir.  <br/> |
|Yeni bir arama örneği  <br/> |Bu sıcak bekleme çözümünde, arama veritabanlarından arama geri yüklendi değildir. Kurtarma grubu içinde yer alan arama bileşenleri, üretim grubuyla mümkün olduğunca benzer şekilde yapılandırılır. Siteler ve içerik geri yüklendikten sonra, arama dizinini yeniden oluşturma için tam gezinmeye başlandı. Sitelerin ve içeriğin kullanılabilir hale tamamlanması için gezinmeyi beklemeniz gerekmemektedir.  <br/> |
|Hizmetler  <br/> | Veritabanlarında veri depolana hizmetler, günlük olarak gönderilen veritabanlarından geri yüklenir. Veritabanlarında veri depolamayan hizmetler basit bir şekilde çalışmaya başlamıştır. <br/>  Veritabanlarına sahip tüm hizmetlerin geri yüklenebilir olması gerekir. Aşağıdaki hizmetlerin veritabanlarından geri yüklenemez ve yük devretme sonrasında başlatabilirsiniz: <br/>  Kullanım ve Durum VeriSi Toplama <br/>  Eyalet hizmeti <br/>  Word otomasyonu <br/>  Veritabanı kullanmayan diğer hizmetler <br/> |
   
Daha karmaşık kurtarma hedefleri için Microsoft Consulting Services (MCS) ile veya bir iş ortağıyla çalışabilirsiniz. Bunlar aşağıdaki tabloda özetlenmiştir.
  
**Tablo: MCS veya bir iş ortağı tarafından adreslenen diğer öğeler**

|**Öğe**|**Açıklama**|
|:-----|:-----|
|Özel grup çözümlerini eşitleme  <br/> |İdeal olarak, kurtarma grubu yapılandırması üretim grubuyla aynıdır. Özel sunucu grubu çözümlerinin çoğaltılmış olup olmadığını ve iki ortamları eşitlenmiş durumda tutmak için bu işlemde olup olmadığını değerlendirmek üzere bir danışman veya iş ortağıyla çalışabilirsiniz.  <br/> |
|Şirket içi veri kaynaklarına bağlantılar  <br/> |Yedek etki alanı denetleyicisi (İVB) bağlantıları ve arama içerik kaynakları gibi arka uç veri sistemlerine bağlantıları çoğaltmak pratik olmaz.  <br/> |
|Arama geri yükleme senaryoları  <br/> |Kurumsal arama dağıtımları oldukça benzersiz ve karmaşık olduğundan, arama veritabanlarından geri yüklemek için daha fazla yatırım gerekir. Bir danışman veya iş ortağıyla birlikte, kuruma gereksinsin arama geri yükleme senaryolarını belirlemek ve uygulamak için çalış çalışıyoruz.  <br/> |
   
Bu makalede sağlanan kılavuzda, şirket içi grubu zaten tasarlanmış ve dağıtılmış olduğu varsayılacaktır.
  
## <a name="detailed-architecture"></a>Ayrıntılı mimari

İdeal olarak, Azure'daki kurtarma grubu yapılandırması aşağıdakiler de dahil olmak üzere şirket içi üretim grubuyla aynıdır:
  
- Sunucu rollerinin aynı gösterimi
    
- Özelleştirmelerin aynı yapılandırması
    
- Arama bileşenlerinin aynı yapılandırması
    
Azure'daki ortam, üretim grubu için daha küçük bir sürüm olabilir. Yük devretme sonrasında kurtarma sunucu grubu ölçeğini ölçeklendirmeyi planlıyorsanız, başlangıçta her sunucu rolü türünün temsil olması önemlidir.
  
Bazı yapılandırmalar yük devretme ortamında çoğaltmak pratik olmaz. Yük devretme grubu beklenen hizmet düzeyini sağladığından emin olmak için yük devretme yordamlarını ve ortamı test etmeye emin olun.
  
Bu çözüm, bir veri grubu için belirli bir topoloji SharePoint değildir. Bu çözümün odak noktası, yük devretme grubu için Azure'i kullanmak ve iki ortam arasında günlük gönderimi ile DEPOLA'ya uygulamaktır.
  
### <a name="warm-standby-environments"></a>Sıcak bekleme ortamları

Sıcak bir bekleme ortamında, Azure ortamındaki tüm sanal makineler çalışıyor. Ortam yük devretme alıştırması veya olayı için hazır.
  
Aşağıdaki resimde, şirket içi bir SharePoint sunucu grubuyla, sıcak bekleme ortamı olarak yapılandırılan Azure tabanlı bir SharePoint sunucu grubuyla olağanüstü durum kurtarma çözümü yer almaktadır.
  
**Şekil: Üretim grubu için topoloji ve önemli öğeler ve sıcak bir bekleme kurtarma grubu**

![SharePoint grubu ve sıcak bir bekleme kurtarma grubu topolojisi.](../media/AZarch-AZWarmStndby.png)
  
Bu diyagramda:
  
- İki ortam yan yana resim göstermektedir: şirket içi depolama SharePoint ve Azure'daki sıcak bekleme grubu.
    
- Her ortamda bir dosya paylaşımı vardır.
    
- Her grup dört katman içerir. Yüksek kullanılabilirlik elde etmek için, her katman ön uç hizmetleri, dağıtılmış önbellek, arka uç hizmetleri ve veritabanları gibi belirli bir rol için aynı şekilde yapılandırılmış iki sunucu veya sanal makine içerir. Bu çizimde belirli bileşenlerin çağrılsı çok önemli değil. İki grup da aynı şekilde yapılandırılmıştır.
    
- Dördüncü katman, veritabanı katmanıdır. Günlük gönderimi, şirket içi ortamdaki ikincil veritabanı sunucusundaki günlükleri aynı ortamdaki dosya paylaşımına kopyalamak için kullanılır.
    
- BELGEYİ, şirket içi ortamdaki dosya paylaşımından Azure ortamında dosya paylaşımına dosyaları kopyalar.
    
- Günlük gönderimi, Azure ortamındaki dosya paylaşımından günlükleri kurtarma ortamındaki SQL Server AlwaysOn kullanılabilirlik grubunda birincil kopyaya yeniden oynatır.
    
### <a name="cold-standby-environments"></a>Soğuk bekleme ortamları

Soğuk bekleme ortamında, SharePoint sunucu grubu sanal makineleri kapatabilirsiniz. (Her sanal makinenin etki alanıyla eşitleymesi için, bazen sanal makinelere her iki haftada bir veya ayda bir gibi başlamalarını öneririz.) Günlük gönderimi ve LOGR'ya sürekli işlemlerin sağlanmasına yardımcı olmak için, Azure kurtarma ortamında aşağıdaki sanal makineler çalışıyor kalmalıdır:
  
- Dosya paylaşımı
    
- Birincil veritabanı sunucusu
    
- Etki Alanı Hizmetleri ve DNS'Windows Server Active Directory en az bir sanal makine
    
Aşağıdaki resimde, dosyanın sanal makinesi ve birincil veritabanı sanal makinesi'nin çalıştır SharePoint bir Azure yük devretme ortamı yer alır. Diğer tüm SharePoint makineleri durdurulur. Otomatik olarak çalışan sanal makine Windows Server Active Directory DNS gösterilmez.
  
**Şekil: Çalışan sanal makinelerle soğuk bekleme kurtarma grubu**

![Azure'daki SharePoint bekleme modundaki çözümün öğeleri.](../media/AZarch-AZColdStndby.png)
  
Soğuk bekleme ortamına yük devretmeden sonra, tüm sanal makineler başlatıldı ve veritabanı sunucularının yüksek kullanılabilirliğini elde etmek için kullanılan yöntem SQL Server AlwaysOn kullanılabilirlik grupları gibi yapılandırmalıdır.
  
Birden çok depolama grubu uygulanırsa (veritabanları birden çok veritabanına SQL Server yüksek kullanılabilirlik kümesine yayılmışsa), depolama grubuyla ilişkilendirilmiş günlükleri kabul etmek için her depolama grubunun birincil veritabanı çalışıyor olmalıdır.
  
### <a name="skills-and-experience"></a>Beceriler ve deneyim

Bu olağanüstü kurtarma çözümünde birden fazla teknoloji kullanılır. Bu teknolojilerin beklendiği gibi etkileşimli çalışmanıza yardımcı olmak için, şirket içi ve Azure ortamındaki her bileşenin doğru bir şekilde yüklenmiş ve yapılandırılmış olması gerekir. Bu çözümü ayarleyen kişi veya ekibin, aşağıdaki makalelerde açıklanan teknolojilerle ilgili güçlü çalışma bilgilerine ve el altında becerilere sahip olması önerilir:
  
- [Dağıtılmış Dosya Sistemi (BUMS) Çoğaltma Hizmetleri](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))
    
- [Windows Sunucu Yük Devretme Kümesi 'ni (WSFC) SQL Server](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)
    
- [AlwaysOn Kullanılabilirlik Grupları (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)
    
- [Veritabanı Veritabanlarını Yedekleme ve SQL Server Geri Yükleme](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)
    
- [SharePoint Server 2013 yükleme ve grup dağıtımı](/SharePoint/install/installation-and-configuration-overview)
    
- [Microsoft Azure](/azure/)
    
Son olarak, bu teknolojilerle ilişkili görevleri otomatikleştirmek için kullanabileceğiniz komut dosyası becerilerini öneririz. Bu çözümde açıklanan tüm görevleri tamamlamak için kullanılabilir kullanıcı arabirimlerini kullanabilirsiniz. Bununla birlikte, el ile yapılan bir yaklaşım zaman alıcı ve hataya neden olabilir ve tutarsız sonuçlar verir.
  
Azure, Windows PowerShell, Windows PowerShell Server ve Azure SQL Server SharePoint için Windows PowerShell kitaplıkları da vardır. Bu, olağanüstü durum kurtarma SQL yapılandırma ve koruma sürenizi azaltmaya yardımcı olan Güvenlik Güvenlik 365'i unutmayın.
  
## <a name="disaster-recovery-roadmap"></a>Olağanüstü durum kurtarma yol haritası

![Olağanüstü bir kurtarma yol SharePoint için görsel temsil.](../media/Azure-DRroadmap.png)
  
Bu yol haritasında, üretimde dağıtılan bir SharePoint Server 2013 sunucu grubu zaten olduğu varsayıldı.
  
**Tablo: Olağanüstü durum kurtarma yol haritası**

|**Aşama**|**Açıklama**|
|:-----|:-----|
|Aşama 1  <br/> |Olağanüstü durum kurtarma ortamını tasarlar.  <br/> |
|Aşama 2  <br/> |Azure sanal ağı ve VPN bağlantısını oluşturun.  <br/> |
|Aşama 3  <br/> |Active Directory Windows Etki Alanı Adı Hizmetlerini Azure sanal ağına dağıtın.  <br/> |
|Aşama 4  <br/> |Azure'SharePoint kurtarma sunucu grubu dağıtımı.  <br/> |
|Aşama 5  <br/> |Kümeler arasında DEPOLA'yi ayarlayın.  <br/> |
|Aşama 6  <br/> |Kurtarma grubu için günlük gönderimi ayarlama.  <br/> |
|Aşama 7  <br/> | Yük devretme ve kurtarma çözümlerini doğrulama. Bu, aşağıdaki yordamları ve teknolojileri içerir: <br/>  Günlük gönderimi durdurun. <br/>  Yedekleri geri yükleyin. <br/>  İçerikte gezinme. <br/>  Hizmetleri kurtarabilirsiniz. <br/>  DNS kayıtlarını yönetin. <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Aşama 1: Olağanüstü durum kurtarma ortamını tasarlama

SharePoint [2013 için Microsoft Azure](microsoft-azure-architectures-for-sharepoint-2013.md) Mimarileri'ne bakarak, acil durum kurtarma ortamı da içinde olmak üzere acil durum kurtarma ortamını SharePoint kullanın. Tasarım işlemini başlatmak için [Azure Visio'SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=392554) Acil Durum Kurtarma Çözümü dosyasındaki grafikleri kullanabilirsiniz. Azure ortamında herhangi bir çalışmaya başlamadan önce ortamın tamamını tasarlamanız önerilir.
  
[SharePoint 2013 için Microsoft Azure Architectures'da sağlanan sanal](microsoft-azure-architectures-for-sharepoint-2013.md) ağ, VPN bağlantısı, Active Directory ve SharePoint sunucu grubu tasarımında sağlanan kılavuzun yanı sıra, Azure ortamına dosya paylaşımı rolü eklemeye de emin olun.
  
Bir olağanüstü durum kurtarma çözümünde günlük gönderimi desteklemek için, veritabanı rollerinin bulunduğu alt ağa bir dosya paylaşım sanal makinesi eklenir. Dosya paylaşımı, SQL Server AlwaysOn kullanılabilirlik grubunda Düğüm Çoğunluğu'SQL Server düğümünü de sağlar. Bu, AlwaysOn kullanılabilirlik gruplarında SharePoint standart bir SQL Server grubu için önerilen yapılandırmadır. 
  
> [!NOTE]
> bir SQL Server AlwaysOn kullanılabilirlik grubuna katılmak için veritabanının önkoşullarını gözden geçirmek önemlidir. Daha fazla bilgi için Bkz[. AlwaysOn Kullanılabilirlik Grupları için Öneriler, Kısıtlamalar ve Önkoşullar](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability). 
  
**Şekil: Olağanüstü durum kurtarma çözümü için kullanılan dosya sunucusunun yerleşimi**

![Veritabanı sunucu rollerini içeren aynı bulut hizmetine eklenmiş bir dosya SharePoint sanal makine gösterir.](../media/AZenv-FSforDFSRandWSFC.png)
  
Bu diyagramda, dosya paylaşımı sanal makinesi, veritabanı sunucu rollerini içeren Azure'da aynı alt ağa eklenir. Dosya paylaşımı sanal makinesi, kullanıcı rolleri gibi diğer sunucu rolleriyle bir kullanılabilirlik kümesine SQL Server.
  
Günlüklerin yüksek kullanılabilirliği konusunda endişeleriniz varsa Azure Blob Depolama Hizmeti ile SQL Server ve geri yükleme'yi kullanarak farklı bir [Depolama yaklaşım benimseyebilirsiniz](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service). Bu, Azure'da günlükleri doğrudan bir blob depolama URL'sinde kaydeden yeni bir özelliktir. Bu çözüm, bu özelliğin kullanımıyla ilgili rehberlik içermez.
  
Kurtarma grubu tasarlarken, başarılı bir olağanüstü durum kurtarma ortamının kurtarmak istediğiniz üretim ortamını doğru bir şekilde yansıtdığını unutmayın. Kurtarma grubu tasarımı, dağıtımı ve testi için, kurtarma grubu boyutu en önemli şey değildir. Grup ölçeği, iş gereksinimlerine göre kuruluştan kuruluşa değişiklik sağlar. Kısa bir kesinti için veya performans ve kapasite talepleri grubu ölçeklendirmeniz gerekene kadar, ölçeği aşağı doğru bir grup kullanmak mümkün olabilir.
  
Kurtarma sunucu çiftini, hizmet düzeyi sözleşmeniz (SLA) gereksinimlerinizi karşılayacak ve işletmenizi desteklemek için gereken işlevleri sağlamak üzere üretim grubuyla mümkün olduğunca aynı şekilde yapılandırabilirsiniz. Olağanüstü durum kurtarma ortamı tasarlarken, üretim ortamınız için değişiklik yönetim sürecinize de bakın. Kurtarma ortamını üretim ortamıyla aynı zaman aralığında güncelleştirerek, değişiklik yönetim sürecini kurtarma ortamına genişletmenizi öneririz. Değişiklik yönetimi işleminin bir parçası olarak, grup yapılandırmanız, uygulamalarınız ve kullanıcılarınız için ayrıntılı envanteri korumanızı öneririz. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Aşama 2: Azure sanal ağ ve VPN bağlantısı oluşturma

[Bağlan ağdan bir Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) ağına bağlanıyorsanız, Azure'da sanal ağı planlama ve dağıtma ve VPN bağlantısını oluşturma hakkında bilgi gösterir. Aşağıdaki yordamları tamamlamak için konu başlığında yer alan yönergeleri izleyin:
  
- Sanal Ağın özel IP adresi alanı planlama.
    
- Sanal Ağ için yönlendirme altyapısı değişikliklerini plan yapın.
    
- Şirket içi VPN cihazından gelen ve bu cihazdan gelen trafik için güvenlik duvarı kurallarını plan edin.
    
- Azure'da şirket içi sanal ağı oluşturun.
    
- Şirket içi ağınız ve Sanal Ağ arasında yönlendirmeyi yapılandırın.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Aşama 3: Active Directory ve Etki Alanı Adı Hizmetlerini Azure sanal ağına dağıtma

Bu aşama, [SharePoint 2013 için Microsoft Azure](microsoft-azure-architectures-for-sharepoint-2013.md) Mimarileri'de açıklandığı ve aşağıdaki şekilde gösterildiği gibi karma bir senaryoda hem Windows Server Active Directory hem de DNS'yi Sanal Ağa dağıtmayı içerir.
  
**Şekil: Karma Active Directory etki alanı yapılandırması**

![Azure sanal ağına dağıtılan iki sanal makine ve SharePoint Grubu alt ağ, çoğaltma etki alanı denetleyicileri ve DNS sunucularıdır.](../media/AZarch-HyADdomainConfig.png)
  
Çizimde, aynı alt ağ için iki sanal makine dağıtılır. Bu sanal makinelerde her biri iki rol barındırabilirsiniz: Active Directory ve DNS.
  
Azure'da Active Directory'yi dağıtmadan önce, Azure [Sanal Makinelerinde Windows Server Active Directory için yönergeler'i okuyun](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Bu yönergeler, çözümünüz için farklı bir mimariye mi yoksa farklı yapılandırma ayarlarına mı ihtiyacınız olduğunu belirlemenize yardımcı olur.
  
Azure'da etki alanı denetleyicisini ayarlama hakkında ayrıntılı kılavuz için bkz. [Azure Sanal Ağlarında Bir Çoğaltılabilir Active Directory Etki Alanı Denetleyicisi Yükleme](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).
  
Bu aşamadan önce, Sanal Ağ'a sanal makineler dağıtmamıştınız. Active Directory ve DNS'yi barındırmak için sanal makineler büyük olasılıkla çözüm için ihtiyacınız olan en büyük sanal makine değildir. Bu sanal makineleri dağıtmadan önce, Sanal Ağınız'da kullanmayı planlasanız en büyük sanal makinenini oluşturun. Bu, çözüme ihtiyacınız olan en büyük boyutu sağlayan Azure'daki bir etiketin üzerinde olmasını sağlamaya yardımcı olur. Şu anda bu sanal makinesi yapılandırmaya gerek yok. Bunu oluşturun ve bir yana bırakın. Bunu yapmak zorunda değilsanız, daha sonra daha büyük sanal makineler oluşturmada bir sınırlamayla çalışabilirsiniz; bu, makalenin yazıldığı sırada soruna neden olur. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Aşama 4: Azure'SharePoint kurtarma sunucu grubu dağıtma

Tasarım SharePoint göre Sanal Ağınız'da SharePoint sunucu grubu dağıtın. Azure'da daha fazla rol [dağıtmadan önce SharePoint 2013 Azure Altyapı](/previous-versions/azure/dn275958(v=azure.100)) Hizmetleri'SharePoint planlamayı gözden geçirmek yararlı olabilir.
  
Kavram kanıtı ortamımızı inşaarak öğrendiklerimizi aşağıdaki uygulamaları göz önünde bulundurabilirsiniz:
  
- Azure portalını veya PowerShell'i kullanarak sanal makineler oluşturun.
    
- Azure ve Hyper-V dinamik belleği desteklemez. Bunun performans ve kapasite planlarınızı faktöre dönüştür olduğundan emin olun.
    
- Sanal makineleri, sanal makine oturum açmanın kendi üzerinden değil, Azure arabirimi üzerinden yeniden başlatın. Azure arabirimini kullanmak daha iyi çalışır ve daha öngörülebilirdir.
    
- Maliyetleri kaydetmek için sanal bir makineyi kapatmak için Azure arabirimini kullanın. Sanal makine oturum açma sesini kapatırsanız, ücretler tahakkuk edene kadar devam eder.
    
- Sanal makineler için bir adlandırma kuralı kullanın.
    
- Sanal makinelerin dağıtıldı olduğu veri merkezi konumuyla ilgili dikkat seçin.
    
- Azure'daki otomatik ölçeklendirme özelliği, bu roller için SharePoint desteklenmiyor.
    
- Geri yüklenecek sunucu grubu içinde bulunan site koleksiyonları gibi öğeleri yapılandırmayın. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Aşama 5: KÜMELER arasında DEPOLA'yi ayarlama

MMCR kullanarak dosya çoğaltmasını ayarlamak için DNS Yönetimi ek bileşenini kullanın. Bununla birlikte, AŞAĞıDAKILER GIBI) ÖNCE, ŞIRKET içi dosya sunucunuzda ve Azure dosya sunucunuzda oturum açın ve HIZMETI WINDOWS Windows.
  
Sunucu Yöneticisi Panosunda aşağıdaki adımları tamamlayın:
  
- Yerel sunucuyu yapılandırma.
    
- Rol ve **Özellik Ekleme Sihirbazı'nı başlatın**.
    
- Dosya ve **Depolama düğümünü** açın.
    
- **YERKİ Ad Alanları ve** **DEPO çoğaltması'ni seçin**.
    
- **Sihirbazın** adımlarını tamamlamak için Sonraki'ne tıklayın.
    
Aşağıdaki tablo, YALNıZ12 başvuru makalelerinin ve blog gönderilerinin bağlantılarını sağlar.
  
**Tablo: BUR için başvuru makaleleri**

|**Başlık**|**Açıklama**|
|:-----|:-----|
|[Çoğaltma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11)) <br/> |Çoğaltma bağlantıları içeren BIRMYA Yönetim TechNet konusu  <br/> |
|[HID Çoğaltması: Sağ Kalma Kılavuzu](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |EDNİ bilgilerine bağlantılar içeren wiki  <br/> |
|[YINELEME Çoğaltması: Sık Sorulan Sorular](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10)) <br/> |HIÇ YINELEME Çoğaltması TechNet konusu  <br/> |
|[Her iki postayı da aynı şekilde ifade edebilirsiniz.](/archive/blogs/josebda/) <br/> |Microsoft'ta Dosya Sunucusu ekibinde Program Yöneticisi tarafından yazılan blog  <br/> |
|[Microsoft Depolama - Dosya Dolabı Blogu'nda En Iyi Ekip](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Windows Server'da dosya hizmetleri ve depolama özellikleri hakkında blog  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Aşama 6: Kurtarma grubu için günlük gönderimi ayarlama

Günlük gönderimi, bu ortamda olağanüstü durum kurtarmayı ayarlamanın kritik bileşenidir. Birincil veritabanı sunucu örneğinden ikinci bir veritabanı sunucu örneğine veritabanları için işlem günlüğü dosyalarını otomatik olarak göndermek üzere günlük gönderimini kullanabilirsiniz. Günlük gönderimi ayarlamak için bkz. [SharePoint 2013'te günlük gönderimi yapılandırma](/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> SharePoint Server'da günlük gönderim desteği belirli veritabanlarıyla sınırlıdır. Daha fazla bilgi için bkz. Veritabanları için desteklenen yüksek kullanılabilirlik ve olağanüstü durum [SharePoint seçenekleri (SharePoint 2013)](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Aşama 7: Yük devretme ve kurtarmayı doğrulama

Bu son aşama, olağanüstü durum kurtarma çözümünün planlandığı gibi çalıştığını doğrulamaktır. Bunu yapmak için, üretim grubu kapatan ve kurtarma grubu'nu yeni bir grup olarak başlatan bir yük devretme olayı oluşturun. Yük devretme senaryosunu el ile veya betikleri kullanarak başlatabilirsiniz.
  
İlk adım, grup hizmetleri veya içerik için gelen kullanıcı isteklerini durdurmaktır. DNS girdilerini devre dışı bırakarak veya ön uç web sunucularını kapatarak bunu kullanabilirsiniz. Grup "aşağı" olduktan sonra, kurtarma grubu için başarısız olabilir.
  
### <a name="stop-log-shipping"></a>Günlük gönderimi durdurma

Grup kurtarma işlemi öncesinde günlük gönderimi durdurmanız gerekir. Önce Azure'da ikincil sunucuda günlük gönderimini durdurun ve ardından bunu şirket içi birincil sunucuda durdurun. önce ikincil sunucuda ve sonra da birincil sunucuda günlük gönderimini durdurmak için aşağıdaki betiği kullanın. Betikte yer alan veritabanı adları, ortamınıza bağlı olarak farklı olabilir.
  
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

### <a name="restore-the-backups"></a>Yedekleri geri yükleme

Yedeklerin oluşturulduk sırayla geri yüklemeleri gerekir. Belirli bir işlem günlüğü yedeklemesini geri yükleymeden önce, atlanmamış işlemleri geri almadan (yani,  `WITH NORECOVERY`):
  
- Tam veritabanı yedeklemesi ve son farklılık yedeklemesi - Herhangi biri varsa, söz konusu işlem günlüğü yedeğine alınan bu yedekleri geri yükleyin. En yeni tam veya farklılık veritabanı yedeklemesi oluşturulmadan önce, veritabanı tam kurtarma modeli veya toplu olarak kaydedilmiş kurtarma modeli kullanmıştı.
    
- Tüm işlem günlüğü yedeklemeleri - Tam veritabanı yedeklemeden veya farklılıklı yedeklemeden (birini geri yükledikten sonra) ve belirli işlem günlüğü yedeklemeden önce alınan işlem günlüğü yedeklemelerini geri yükleyin. Günlük yedekleri, oluşturulduk sırayla ve günlük zincirinde boşluklar olmadan uygulanmalıdır.
    
İkincil sunucuya, sitelerin işlen böyle bir şekilde içerik veritabanını kurtarmak için, kurtarma öncesinde tüm veritabanı bağlantılarını kaldırın. Veritabanını geri yüklemek için aşağıdaki son SQL çalıştırın.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> T-SQL kullanıyorken, belirsizlik ortadan kaldırmak için her RESTORE deyiminde **WITH NORECOVERY** veya **WITH RECOVERY** belirtin; betikler yazarken bu çok önemlidir. Tam ve farklı yedeklemeler geri yüklendikten sonra, işlem günlükleri farklı bir SQL Server Management Studio. Ayrıca, günlük gönderimi zaten durdurulurken içerik veritabanı bekleme durumunda olduğundan, durumu tam erişime geçirmeniz gerekir.
  
Başka SQL Server Management Studio veritabanına sağ tıklayın,  > **WSS_Content** SevlerSyaları'nın üzerine gelin ve ardından İşlem Günlüğü'ne **tıklayın (tam** yedeklemeyi geri yüklemedıysanız, bu kullanılamaz). Daha fazla bilgi için bkz[. İşlem Günlüğü Yedeğini (Yedekle) SQL Server](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).
  
### <a name="crawl-the-content-source"></a>İçerik kaynağında gezinme

Arama Hizmeti'ne geri yüklemek için her içerik kaynağında tam gezinmeye başlamalıdır. Şirket içi grupla ilgili arama önerileri gibi bazı çözümleme bilgilerini kaybettiğimizi unutmayın. Tam gezinmelere başlamadan önce, Windows PowerShell **restore-SPEnterpriseSearchServiceApplication** cmdlet'ini kullanın ve günlükte sevk edilen ve çoğaltılmış Arama Yönetimi veritabanını (varsayılan) **Search_Service__DB_<GUID>**. Bu cmdlet arama yapılandırması, şema, yönetilen özellikler, kurallar ve kaynaklar verir ve diğer bileşenlerin varsayılan bir kümesi oluşturur.
  
Tam gezinmeye başlamak için aşağıdaki adımları tamamlayın:
  
1. SharePoint 2013 Yönetim Merkezi'nde **Application ManagementService** >  **ApplicationsManage** >  hizmet uygulamaları'na gidin ve gezinmek istediğiniz Search Service uygulamasına tıklayın.
    
2. Arama Yönetimi **sayfasında İçerik** **Kaynakları'ne** tıklayın, istediğiniz içerik kaynağının üzerine gelin, oka tıklayın ve sonra da Tam Gezinmeyi **Başlat'a tıklayın**.
    
### <a name="recover-farm-services"></a>Grup hizmetlerini kurtarma

Aşağıdaki tabloda, günlük olarak sevk edilen veritabanları olan hizmetlerin, veritabanlarının olduğu, ancak günlük gönderimi ile geri yüklemenin önerilmez olduğu hizmetler ve veritabanları olmayan hizmetlerin nasıl kurtarılmaları önerilir.
  
> [!IMPORTANT]
> Şirket içi veritabanı SharePoint Azure ortamına geri yükleniyorsa, Azure'a henüz SharePoint olmayan hiçbir hizmet kurtarılamaz. 
  
**Tablo: Hizmet uygulaması veritabanı başvurusu**

|**Bu hizmetleri günlük olarak gönderilen veritabanlarından geri yükleme**|**Bu hizmetlerin veritabanları vardır, ancak veritabanlarını geri yüklemeden bu hizmetleri başlatmanızı öneririz**|**Bu hizmetler veritabanlarında veri depolamaz; yük devretme sonrasında bu hizmetleri başlatma**|
|:-----|:-----|:-----|
| Makine Çevirisi Hizmeti <br/>  Yönetilen Meta Veri Hizmeti <br/>  Güvenli Depolama Hizmeti <br/>  Kullanıcı Profili. (Yalnızca Profil ve Sosyal Etiketleme veritabanlarını destekler. Eşitleme veritabanı desteklenmiyor.) <br/>  Microsoft SharePoint Foundation Abonelik Ayarlar Hizmeti <br/> | Kullanım ve Durum VeriSi Toplama <br/>  Eyalet hizmeti <br/>  Word otomasyonu <br/> | Excel Services <br/>  PerformancePoint Hizmetleri <br/>  PowerPoint Dönüştürme <br/>  Visio Grafik Hizmeti <br/>  Çalışma Yönetimi <br/> |
   
Aşağıdaki örnekte, Yönetilen Meta Veri hizmetinin bir veritabanından nasıl geri yük kaynağı olduğu gösterir.
  
Bu, var olan Managed_Metadata_DB kullanır. Bu veritabanı günlük gönderildi, ancak ikincil grup üzerinde etkin bir hizmet uygulaması yok, bu nedenle hizmet uygulaması yerine gerçekleştikten sonra bağlı olması gerekir.
  
İlk olarak ,  `New-SPMetadataServiceApplication`kullanın ve geri  `DatabaseName` yüklenen veritabanının adıyla anahtarı belirtin.
  
Ardından, ikincil sunucuda yeni Yönetilen Meta Veri Hizmeti Uygulaması'nda aşağıdaki gibi yapılandırabilirsiniz:
  
- Ad: Yönetilen Meta Veri Hizmeti
    
- Veritabanı sunucusu: Sevk edilen işlem günlüğünden gelen veritabanı adı
    
- Veritabanı adı: Managed_Metadata_DB
    
- Uygulama havuzu: SharePoint Uygulamaları 
    
### <a name="manage-dns-records"></a>DNS kayıtlarını yönetme

KENDI sunucu grubunıza işaret etmek için DNS kayıtlarını el SharePoint gerekir.
  
Birden çok ön uç web sunucularının olduğu çoğu durumda, istekleri sunucu grubu önündeki web ön uç sunucuları arasında dağıtmak için, Windows Server 2012'te Ağ Yükü Dengeleme özelliğiden veya bir donanım yük dengeleyiciden yararlanmak anlamlıdır. Ağ yükü dengeleme, web ön uç sunucularından biri başarısız olduğunda istekleri diğer sunuculara dağıtarak riski azaltmaya da yardımcı olabilir. 
  
Normalde, ağ yük dengelemeyi ayarsanız, kümenize tek bir IP adresi atanır. Ardından, ağınız için kümeyi alan DNS sağlayıcısında bir DNS ana bilgisayar kaydı oluşturun. (Bu proje için, şirket içi veri merkezi hatası durumunda azure'a bir DNS sunucusu veririz.) Örneğin, Active Directory'de DNS Yöneticisi'nde yük  `https://sharepoint.contoso.com`dengelemeli kümenizin IP adresini ifade etmek için bir DNS kaydı oluşturabilirsiniz.
  
SharePoint sunucu grubunıza dış erişim için, istemcilerin intranet'te kullanan URL'sini (örneğin, `https://sharepoint.contoso.com`) güvenlik duvarınıza bağlı bir dış IP adresini kullanan bir dış DNS sunucusunda ana bilgisayar kaydı oluşturabilirsiniz. (Bu örneği kullanarak en iyi yöntem, bölünmüş DNS'yi ayararak iç DNS `contoso.com` sunucusunun yetkili olduğunu ve DNS isteklerini dış DNS sunucunuza yönlendirmek yerine istekleri doğrudan SharePoint grup kümesine yönlendirecek şekilde ayarlamaktır.) Daha sonra dış IP adresini şirket içi kümenizin iç IP adresiyle eşleyenin, böylece istemciler araylıklarının kaynaklarını bulur.
  
Buradan, bir kaç farklı olağanüstü durum kurtarma senaryosuyla yüz yüzersiniz:
  
 **Örnek senaryo: Şirket içi SharePoint, şirket içi sunucu grubu donanım hatası nedeniyle SharePoint kullanılamaz.** Bu durumda, Azure SharePoint sunucu grubu üzerinde yük devretme adımlarını tamamlandıktan sonra, aynı şirket içi sunucu grubu için olduğu gibi, kurtarma SharePoint sunucu grubu web-ön uç sunucularında ağ yükü dengelemeyi yapılandırabilirsiniz. Ardından, iç DNS sağlayıcınızda ana bilgisayar kaydını kurtarma grubu küme IP adresine işaret edecek şekilde yönlendirebilirsiniz. İstemcilerde önbelleğe alınan DNS kayıtlarının yenilenmesi ve kurtarma sunucu grubu üzerine işaretlenmesi biraz zaman al götürebilirsiniz.
  
 **Örnek senaryo: Şirket içi veri merkezi tamamen kaybolur.** Bu senaryo, fire veya sel gibi doğal bir olağanüstü durum nedeniyle oluşabilir. Bu durumda, bir kuruluş için, büyük olasılıkla başka bir bölgede ve Kendi dizin hizmetleri ve DNS'i olan Azure alt ağlarında barındırılan ikincil bir veri merkeziniz olabilir. Önceki olağanüstü durum senaryolarında olduğu gibi, iç ve dış DNS kayıtlarınızı Azure SharePoint sunucu SharePoint yönlendirin. BIR kez daha, DNS kaydı yayılmasının biraz zaman al etki alanı olduğunu unutmayın.
  
Ana bilgisayar adı alan site koleksiyonu mimarisi ve dağıtımında [(SharePoint 2013)](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) önerilen şekilde ana bilgisayar adı alan site koleksiyonları kullanıyorsanız, benzersiz DNS adlarla (örneğin, `https://sales.contoso.com` `https://marketing.contoso.com`ve ) SharePoint sunucu grubu içinde aynı web uygulaması tarafından barındırılan birkaç site koleksiyonunuz olabilir. Bu durumda, küme IP adresinize işaret her site koleksiyonu için DNS kayıtları oluşturabilirsiniz. Bir istek web SharePoint ön uç sunucularına ulaştığında, her bir isteği uygun site koleksiyonuna yönlendirmeyi ele alıyor.
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft kavram kanıtı ortamı

Bu çözüm için bir kavram kanıtı ortamı tasarladık ve test ettik. Test ortamımızın tasarım hedefi, müşteri ortamında SharePoint bir grup grubu dağıtmak ve kurtarmaktır. Birkaç varsayım yaptık, ancak hiçbir özelleştirme yapmadan, grup için ilk kullanımdan önce tüm işlevlerin sağlan gerektiğini biliyorum. Topoloji, alan ve ürün grubundan gelen en iyi uygulama kılavuzu kullanılarak yüksek kullanılabilirlik için tasarlanmıştır.
  
Aşağıdaki tabloda, şirket içi test ortamı için oluşturduğumız ve yapılandırılan Hyper-V sanal makineleri açıklandı.
  
**Tablo: Şirket içi test için sanal makineler**

|**Sunucu adı**|**Rol**|**Yapılandırma**|
|:-----|:-----|:-----|
|DC1  <br/> |Active Directory ile etki alanı denetleyicisi.  <br/> |İki işlemci  <br/> 512 MB ile 4 GB RAM arasında  <br/> 1 x 127 GB sabit disk  <br/> |
|RRAS  <br/> |Yönlendirme ve Uzaktan Erişim Hizmeti (RRAS) rolüyle yapılandırılmış sunucu.  <br/> |İki işlemci  <br/> 2-8 GB RAM  <br/> 1 x 127 GB sabit disk  <br/> |
|FS1  <br/> |Yedekler için paylaşımların ve BUR'nin bitiş noktasının olduğu dosya sunucusu.  <br/> |Dört işlemci  <br/> 2-12 GB RAM  <br/> 1 x 127 GB sabit disk  <br/> 1 x 1 TB sabit disk (SAN)  <br/> 1 x 750 GB sabit disk  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Ön uç web sunucuları.  <br/> |Dört işlemci  <br/> 16 GB RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Uygulama sunucuları.  <br/> |Dört işlemci  <br/> 2-16 GB RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |SQL Server 2012 AlwaysOn kullanılabilirlik gruplarıyla yapılandırılan veritabanı sunucuları. Bu yapılandırmada birincil ve ikincil SQL olarak SP-SQL-HA1 ve SP-SQL-HA2 kullanılabilir.  <br/> |Dört işlemci  <br/> 2-16 GB RAM  <br/> |
   
Aşağıdaki tabloda, şirket içi test ortamı için ön uç web ve uygulama sunucuları için oluşturduğumız ve yapılandırmışmız Hyper-V sanal makinelerinin sürücü yapılandırmaları açık almaktadır.
  
**Tablo: Şirket içi test için Ön Uç Web ve Uygulama sunucuları için sanal makine sürücüsü gereksinimleri**

|**Sürücü harfi**|**Boyut**|**Dizin adı**|**Yol**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Sistem sürücüsü  <br/> |<DriveLetter>:\\Program Dosyaları\\ Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Günlük sürücü (40 GB)  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\  <br/> |
|F  <br/> |80  <br/> |Sayfa (36 GB)  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQLDATA\\  <br/> |
   
Aşağıdaki tabloda, oluşturulan ve şirket içi veritabanı sunucuları olarak hizmet verecek şekilde yapılandırılan Hyper-V sanal makinelerinin sürücü yapılandırmaları açık almaktadır. Veritabanı **Altyapısı Yapılandırması sayfasında** , aşağıdaki tabloda **gösterilen ayarları** ayarlamak ve onaylamak için Veri Dizinleri sekmesine erişin.
  
**Tablo: Şirket içi test için veritabanı sunucusu için sanal makine sürücüsü gereksinimleri**

|**Sürücü harfi**|**Boyut**|**Dizin adı**|**Yol**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Veri kök dizini  <br/> |<DriveLetter>:\\Program Dosyaları\\ Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Kullanıcı veritabanı dizini  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\  <br/> |
|F  <br/> |500  <br/> |Kullanıcı veritabanı günlük dizini  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\  <br/> |
|G  <br/> |500  <br/> |Temp DB dizini  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\  <br/> |
|H  <br/> |500  <br/> |Temp DB günlük dizini  <br/> |<DriveLetter>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Test ortamını ayarlama

Farklı dağıtım aşamaları sırasında, test ekibi normalde önce şirket içi mimari üzerinde, sonra da ilgili Azure ortamında çalıştı. Bu, ev için üretim gruplarının zaten çalışan olduğu genel gerçek dünya durumlarını yansıtıyor. Daha da önemlisi, geçerli üretim iş yükünü, kapasiteyi ve tipik performansı biliyor olmasıdır. İş gereksinimlerini karşıy acil durum kurtarma modeli yapılandırmaya ek olarak, en düşük hizmet düzeyini sunmak için kurtarma grubu sunucularını da boyutla karşılamanız gerekir. Soğuk veya sıcak bir bekleme ortamında, kurtarma grubu normalde üretim grubundan daha küçüktür. Kurtarma grubu kararlı ve üretimde olduktan sonra, grup iş yükü gereksinimlerini karşılamak için ölçeklendirildi ve ölçeklendirildi.
  
Test ortamımızı şu üç aşamada dağıttık:
  
- Karma altyapıyı ayarlama
    
- Sunucuları sağlama
    
- Grup SharePoint dağıtma
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Karma altyapıyı ayarlama

Bu aşama, şirket içi grup için ve Azure'daki kurtarma grubu için bir etki alanı ortamı ayarlamayı da dahil eder. Test ekibi, Active Directory'i yapılandırmayla ilişkilendirilmiş normal görevlere ek olarak, iki ortam arasında bir yönlendirme çözümü ve bir VPN bağlantısı uygulamaya başladı.
  
#### <a name="provision-the-servers"></a>Sunucuları sağlama

Sunucu grubu sunucularına ek olarak, etki alanı denetleyicileri için sunucu sağlanması ve hem RRAS'yi hem de siteden siteye VPN'yi işlemek üzere bir sunucuyu yapılandırmanız gerekmektedir. BUR hizmeti için iki dosya sunucusu sağlandı ve test etmek için birkaç istemci bilgisayar sağlandı.
  
#### <a name="deploy-the-sharepoint-farms"></a>Grup SharePoint dağıtma

Ana SharePoint, gerektiğinde ortamı sabitlemeyi ve sorun gidermeyi basitleştirmek için iki aşamalı olarak dağıtılmıştır. İlk aşama sırasında, her sunucu grubu gerekli işlevselliği desteklemek için topolojinin her katmanında en az sayıda sunucuya dağıtılmıştır.
  
SQL Server 2013 sunucularını oluşturmadan önce, SharePoint sunucularını oluşturduk. Bu yeni bir dağıtım olduğundan, dağıtım öncesinde kullanılabilirlik gruplarını SharePoint. MCS en iyi uygulama kılavuzuna dayalı üç grup oluşturduk. 
  
> [!NOTE]
> Yüklemeden önce kullanılabilirlik grupları oluştur oluşturmak için yer tutucu SharePoint oluşturun. Daha fazla bilgi için bkz. [SQL Server 2013 için AlwaysOn](/SharePoint/administration/configure-an-alwayson-availability-group) Kullanılabilirlik Gruplarını yapılandırma SharePoint
  
Sunucu grubu ve ek sunucuları aşağıdaki sırada oluşturduk:
  
- SP-SQL-HA1 ve SP-SQL-HA2 sağlama.
    
- AlwaysOn'un yapılandırılması ve sunucu grubu için üç kullanılabilirlik grubu oluşturma. 
    
- Merkezi Yönetim'i barındırmak için SP-APP1 sağlama.
    
- Dağıtılmış önbelleği barındırmak için SP-WFE1 ve SP-WFE2 sağlama. 
    
Komut satırına başka bir ad kullandık ve  _skipRegisterAsDistributedCache_ **psconfig.exe** host parametresini kullandık. Daha fazla bilgi için bkz. [SharePoint Server 2013'te akışlar ve Dağıtılmış Önbellek hizmetini planlama](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Kurtarma ortamında aşağıdaki adımları tekrarlarız:
  
- Az-SQL-HA1 ve AZ-SQL-HA2 hazırlama.
    
- AlwaysOn'un yapılandırılması ve sunucu grubu için üç kullanılabilirlik grubu oluşturma.
    
- Merkezi Yönetim'i barındırmak için AZ-APP1 sağlama.
    
- Dağıtılmış önbelleği barındırmak için AZ-WFE1 ve AZ-WFE2 sağlama.
    
Dağıtılmış önbelleği yapılandırdikten ve test kullanıcılarını ekledikten ve içeriği test ettikten sonra dağıtımın ikinci aşamasına başladık. Bu, sunucu grubu mimarisinde açıklanan yüksek kullanılabilirlik topolojilerini destekleyecek şekilde katmanları ölçeklendirme ve sunucu grubu sunucularını yapılandırmayı gerektirmektedir.
  
Aşağıdaki tabloda, kurtarma grubumuz için ayarlarımız sanal makine, alt ağ ve kullanılabilirlik kümeleri açık almaktadır.
  
**Tablo: Kurtarma grubu altyapısı**

|**Sunucu adı**|**Rol**|**Yapılandırma**|**Alt Ağ**|**Kullanılabilirlik kümesi**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Active Directory ile etki alanı denetleyicisi  <br/> |İki işlemci  <br/> 512 MB ile 4 GB RAM arasında  <br/> 1 x 127 GB sabit disk  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Yedekler için paylaşımların ve ANDR için uç noktası olan dosya sunucusu  <br/> | A5 yapılandırması: <br/>  İki işlemci <br/>  14 GB RAM <br/>  1 x 127 GB sabit disk <br/>  1 x 135 GB sabit disk <br/>  1 x 127 GB sabit disk <br/>  1 x 150 GB sabit disk <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Ön Uç Web sunucuları  <br/> | A5 yapılandırması: <br/>  İki işlemci <br/>  14 GB RAM <br/>  1 x 127 GB sabit disk <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Uygulama sunucuları  <br/> | A5 yapılandırması: <br/>  İki işlemci <br/>  14 GB RAM <br/>  1 x 127 GB sabit disk <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |AlwaysOn kullanılabilirlik grupları için veritabanı sunucuları ve birincil ve ikincil çoğaltmalar  <br/> | A5 yapılandırması: <br/>  İki işlemci <br/>  14 GB RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Operasyonlar

Test ekibi sunucu grubu ortamlarını yapılandırdikten ve işlevsel testi tamamlandıktan sonra, şirket içi kurtarma ortamını yapılandırmak için gereken aşağıdaki işlemler görevlerini başlatmışlardır:
  
- Yedekleri tam ve farklılıkla yapılandırma.
    
- Şirket içi ortamla Azure ortamı arasında işlem günlüklerini aktaran dosya sunucularında BUR'yi yapılandırabilirsiniz.
    
- Birincil veritabanı sunucusunda günlük gönderimini yapılandırma.
    
- Gerekli olduğu şekilde günlük gönderimi ile ilgili sorunları giderin, doğrulama yapın ve sorun giderin. Bu, ağ gecikme süresi gibi soruna neden olacak her türlü davranışı belirleme ve belgele birlikte, günlük gönderimi veya BULANİS dosya eşitleme hatalarının neden olduğu bilgileri içerir.
    
### <a name="databases"></a>Veritabanları

Yük devretme testlerimiz aşağıdaki veritabanlarını içerir: 
  
- WSS_Content
    
- ManagedMetadata
    
- Profil DB
    
- Eşitleme DB
    
- Sosyal DB
    
- İçerik Türü Merkezi (adanmış bir İçerik Türü Dağıtım Merkezi için bir veritabanı)
    
## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

Bu bölümde test sırasında karşılaştığımız sorunlar ve bunların çözümleri açıklandı. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Terim Deposu Yönetim Aracı'nın kullanımı "Yönetilen Meta Veri Deposu veya Bağlantı şu anda kullanılamıyor" hatasına neden oldu.

Web uygulaması tarafından kullanılan uygulama havuzu hesabının Terim Deposuna Okuma iznine sahip olduğundan emin olun.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Özel terim kümeleri site koleksiyonunda kullanılamaz

İçerik site koleksiyonunuzla içerik türü hub'nız arasındaki hizmet uygulaması ilişkilendirmesi eksik mi? Buna ek olarak, **Yönetilen Meta Veri - <site collection name>** Bağlantı özellikleri ekranında, şu seçeneğin etkinleştirildiğinden emin olun: Bu hizmet uygulaması sütuna özgü terim kümeleri için **varsayılan depolama konumutur.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Get-ADForest Windows PowerShell komutu "'Get-ADForest' terimi cmdlet, işlev, betik dosyası veya işlenen programın adı olarak tanınmıyor" hatasını üretir.

Kullanıcı profillerini ayarlarken, Active Directory ormanı adına ihtiyacınız vardır. Rol ve Özellik Ekleme Sihirbazı'nda, Windows PowerShell için Active Directory Modülü'dür (Uzak Sunucu Yönetim Araçları>Rol Yönetimi Araçları **>AD DS ve AD LDS Araçları** bölümünde). Buna ek olarak, yazılım bağımlılıklarının yüklendiğinden emin olmak için **Get-ADForest'i** kullanmadan önce aşağıdaki komutları çalıştırın.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>'' üzerinde 'AlwaysOn_health' XEvent oturumu başlatma sırasında kullanılabilirlik grubu oluşturma başarısız<server name> oluyor

Yük devretme kümenizin her iki düğümünün de "Duraklatıldı" veya "Durduruldu" değil Durum "Yukarı" durumunda olduğundan emin olun. 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server günlüğü gönderim işi dosya paylaşımına bağlanmaya çalışırken erişim reddedildi hatasıyla başarısız oluyor

Varsayılan kimlik SQL Server, ağ kimlik bilgileri altında çalışan Kullanıcı Aracısı'nız olduğundan emin olun.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server sevkiyat işi başarıyı gösterir, ancak hiçbir dosya kopyalanmaz

Bunun nedeni, kullanılabilirlik grubu için varsayılan yedekleme tercihi İkincil Tercih **İkincil'indir**. Kullanılabilirlik grubu için birincil yerine ikincil sunucudan günlük gönderimi işini çalıştır grubuna; Aksi takdirde, iş sessizce başarısız olur. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Yönetilen Meta Veri hizmeti (veya SharePoint hizmet) yüklemeden sonra otomatik olarak başlatılam

Hizmetlerin başlaması, SharePoint Server performansınız ve geçerli yüküne bağlı olarak SharePoint sürebilir. Hizmet için **başlat'ı** el ile tıklatın ve durumu izlemek için Sunucu'da Hizmetler ekranında zaman zaman yenileme yaparken yeterli başlangıç süresi sağlamalısınız. Hizmet durdurulursa, tanı günlüğünü SharePoint, hizmeti yeniden başlatmayı deneyin ve sonra günlükte hataları denetleyin. Daha fazla bilgi için bkz[. SharePoint 2013'te tanılama günlüğünü yapılandırma](/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>DNS'yi Azure yük devretme ortamına değiştirdikten sonra, istemci tarayıcıları site için eski IP SharePoint kullanmaya devam eder

DNS değişikliğiniz hemen tüm istemciler tarafından görülemeyebilir. Test istemciinde, yükseltilmiş komut isteminden aşağıdaki komutu gerçekleştirin ve siteye yeniden erişmeyi deneyin.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Ek kaynaklar

[Veritabanları için desteklenen yüksek kullanılabilirlik ve olağanüstü durum SharePoint seçenekleri](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[SQL Server 2013 için AlwaysOn Kullanılabilirlik Gruplarında SharePoint yapılandırma](/SharePoint/administration/configure-an-alwayson-availability-group)
  
## <a name="see-also"></a>Ayrıca Bkz

[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)