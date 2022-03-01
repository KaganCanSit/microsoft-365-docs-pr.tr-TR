---
title: SharePoint 2007 geçiş seçeneklerini ayarlama
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Bu makale, yükseltmelerini planlamalarına yardımcı SharePoint Server 2007 kullanan kullanıcılara ilişkin bilgileri içerir.
ms.openlocfilehash: 9c1c4c90443b632b490ac7a510394f367f688fca
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019457"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint 2007 geçiş seçeneklerini ayarlama

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft SharePoint 2007 ve SharePoint Server 2007 destek sonuna ulaştı. Yükseltme zamanı geldi! Bu makalede geçiş seçenekleriniz hakkında bilgi sunulmaktadır.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Daha fazla bilgi için yaygın yükseltme SharePoint

SharePoint Server ortamını yükseltmek için SharePoint vardır. Microsoft Office SharePoint Server 2007 sunucu grubu varsa, aşağıda yükseltme yöntemlerinin örneklerini verilmiştir:
  
- Veritabanı ekleme
    
- Yan yana yükseltme
    
- Yerinde yükseltme
    
- Karma yükseltme (yerinde ve ayrılmış veritabanları / ayrı veritabanı ekleme)
    
- SharePoint (şirket içi cihaza çevrimiçi bağlanma) SharePoint
    
- Verileri site koleksiyonları veya kitaplıklar arasında el ile taşıma
    
- FastTrack'e Yükseltme (Microsoft 365 [Çevrimiçi SharePoint danışmanı](https://aka.ms/spoguidance))
    
- Microsoft 365'de SharePoint Online'a (SPO) Geçiş API'si
    
Size en uygun olan nedir?
  
Yükseltme söz konusu olduğunda, grubun ne yaptığını ve ne için kullanıı olduğunu bilginiz size taktik bir güç verir. kişiler Grup Grubu'SharePoint seçeneklerinizi seçmenize yardımcı olur.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007'de de, burada ele almayacak aşamalı bir yükseltme vardır. Adıma özel yükseltme makalelerinin listesini görmek için bkz. [SharePoint Server 2007 destek sonu Yol Haritası](sharepoint-2007-end-of-support.md). 
  
Yükseltmede hangi [ürün sürümüne](https://support.microsoft.com/lifecycle/search) sahip olursanız olun, Ürün Yaşam SharePoint Sistem Gereksinimlerini denetlemeyi unutmayın. Bu şekilde bir sonraki yükseltmenin ne zaman gerekli olacağını bilirsiniz (örneğin, diğer yükseltmeleri planlamak için SharePoint Server 2010 gibi eski bir üründe duraklarsanız, destek bitiş tarihini biliyorsanız) ve planınızı destekleyen donanıma sahip olduğunu unutmayın. 
  
SharePoint sitelerinizi bulutta Microsoft 365'e Microsoft 365 veya bir şekilde geçiş yapmayı planlıyorsanız, şimdi Microsoft 365 ve Office 365 açıklamalarının bağlantısını yer [işaretlerine](/office365/servicedescriptions/office-365-service-descriptions-technet-library) eklemenin tam zamanıdır. Çevrimiçi özellikler hakkında bilgi edinmek ve bunların şirket içi SharePoint Sunucu'dan nasıl farklı olabileceğini öğrenmek için Hizmet SharePoint gerekir. İşlevsel Microsoft Office SharePoint Server 2007 sunucu sunucularını yükseltme. Yükleme sırasında bozuk siteler varsa, yükseltme öncesinde bunları düzeltin.
  
## <a name="a-note-about-managing-risk"></a>Riski yönetme hakkında bir not

'Yan yana' gibi yöntemler, yükseltme mantığının düzeni açısından önemlidir. Yan yana yükseltme sırasında, Microsoft Office SharePoint Server 2007 sunucu grubu korunur, ancak yeni donanıma onun bir sonraki sürümüyle (SharePoint Server 2010) bir sunucu grubu kurabilirsiniz. Bu, üç şekilde yardımcı olur:
  
1. Veritabanı ekleme kullanarak, Microsoft Office SharePoint Server 2007 veritabanlarınızı ayrı ayrı yükseltebilirsiniz.
    
2. Microsoft Office SharePoint Server 2007 sunucu grubu üzerinde yalnızca birkaç kritik belge kitaplığının ve diğer bilgilerin kullanılabilir olduğunu ansanız, verileri Microsoft Office SharePoint Server 2007'den başka bir sunucuya el ile taşımayı SharePoint  ya da yalnızca belirli siteleri ve web'leri bir sonraki sürüme alırsınız (bu, işlerinizi kolaylaştırabilirsiniz).
    
3. Doğrudan Microsoft Office SharePoint Server 2007 sunucu grubu için ne kadar az şey yaparsınız, siz yükseltme sırasında o sunucu grubu içinde yer alan veriler o kadar güvenli olur.
    
Yükseltme In-Place yöntemler doğrudan Microsoft Office SharePoint Server 2007 sunucu grubu üzerinde hareket eder ve eski ortamınızı kullanarak yol bırakmak ve yeniden başlamak için daha az kolay seçenek sağlar. Mümkün olduğunca, bazı güvenlik önlemleri alın (özgün ortamın yedeklerini alma ve test etme gibi). Örneğin, Microsoft Office SharePoint Server 2007 sunucu sunucunuz sanalsa ve yedekleme ve geri yükleme amacıyla çoğaltılmışsa, yükseltme işleminin hizmet penceresinden önce en güncel veritabanlarını yedekle ve geri yükleyin. Veritabanı yedeklerini geri yükleme seçeneğiniz olduğunu bilmek, daha güvende çalışmanızı sağlamakla da aynı şekilde rahat çalışmanızı sağlar.
  
> [!TIP]
> [Microsoft Office SharePoint Server 2007, SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2013](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)) ve [SharePoint Server 2016'da](/SharePoint/upgrade-and-update/best-practices-for-upgrade) yükseltme için en iyi yöntemler belgeleri vardır. [](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) Ayrıca, yükseltme ve yükseltme veya yükseltme deneyimi olan [Microsoft](https://partnercenter.microsoft.com/pcv/search) Microsoft 365 arayabilirsiniz. 
  
## <a name="make-your-plan"></a>Planınızı yapma

Yükseltmeniz gerekirse bir plana ihtiyacınız vardır ve her durumda tek boyut buna uymaz. Planınız 'SharePoint Microsoft 365 Online ile Microsoft 365 aboneliği oluştur, etki alanını kaydet ve insanları dosyalarını oraya kaydetmeleri için yönlendir' kadar basit olabilir. Ve belki de böyle olabilir. Bu karar size göredir ve hem sizin hem de kullanıcılarının gerçekten ihtiyaçte olduğu bir karardır.
  
> [!NOTE]
> Yaşam döngüsü sona eren bir yazılımda çalışma risklidir. Destek dışında olan ürünlerde sorun bulunurken artık düzeltme eki yoktur. Bu aynı zamanda, yeni güvenlik tehditleri ortaya çıktığında güvenlik yamaları veya düzeltmeleri olmayacaktır, çünkü yaşam döngüsünün sonuna kadar olan ürünler artık desteklenmiyor. Lütfen böyle bir durumdan kaçının! 
  
### <a name="first-know-your-farm"></a>İlk olarak, grubunızı tanıyor

Yükseltme yaparken, karar verme kararının sunucu grubu tarafından organizasyonunız için ne yaptığını temel alarak olması gerekir. Hangi ihtiyaçları karşılar? Rolü nedir? Şirketinizin her grubu için farklı bir rol olabilir. Gruplarınızı SharePoint, bazıları *güvenli* tutma için orada bulunan dosya arşivleri olabilir. Sunucu grubu aynı anda birçok rol doldurıyorsa, site koleksiyonlarının, web'lerin, hatta belge kitaplıklarının ne yaptığını, özelleştirmelerin ne kadar önemli olduğunu da bilmek de gerekir. Verilerinizi bu düzeyde çözümlemek çok fazla iş gibi görünebilir, ancak yükseltmeden veya geçirmeden önce etki alanınıza hakim olmak için zaman ve çabadan tasarruf sağlar. Tüm hareketli parçaları ve en önemli parçaları bir kez biliyor, neleri aştıktan ve geride bıraka bir şey olduğunu da bilirsiniz. Bu bilgi, ilerlerken size çok yarar. 
  
Peki, SharePoint Server sunucu grubum hakkında kullanıcıların SharePoint nedir?
  
- Yerleşik SharePoint özellikleri
    
- Büyük veri corpus (dosya arşivi gibi)
    
- Kullanılabilirlik
    
- Grup içinde kritik uygulamalar, web bölümleri veya belgeler (Görev açısından kritik grup)
    
- Uyumluluk standartlarının karşısı
    
- Özelleştirmeler
    
SharePoint sunucu grubundan işletmeniz için temel öneme sahip bir şeyler çalıştırıyorsanız, diyelim ki bu sunucu grubu istemci hizmeti gereksinimleriyle ilgili kritik verilerin büyük bir kataloğunu kullanıyorsa, 'Kritik uygulamalar' gibi 'Kullanılabilirlik' durumlarının yanına da işaret koyabilirsiniz; başka bir ifadeyle SharePoint'i bir süre kullanamasanız işletmeniz bundan etki edilir. Benzer biçimde, 'Özelleştirmeler'i de kontrol edebilirsiniz, çünkü grup tekliflerinizi kritik hizmetler özel kodu, site tanımlarını veya birlikte çalışacak birçok özelleştirmeyi temel almaktadır.
  
SharePoint'te yerleşik olarak bulunan yazılımlara katılımınız dışında katılımınız olmadan bu ihtiyaçları karşılarsanız ve bunu genel olarak güncelleştirin, normal yönetim ve bakım çalışmaları gerçekleştirin, "Yerleşik SharePoint"ı seçmiş de olabilirsiniz. SharePoint'un eski sürümünde kalmanın da nedeni de bu olabilir. Başka bir deyişle, zaten ihtiyacınız olan şeyi yapıyor ve şu ana kadar destek sonu olan Microsoft Office SharePoint Server 2007'de yükseltmeniz gerekmadı.
  
Bu madde işaretli listelerde, yükseltmeniz için ölçütler oluşturabilirsiniz. Başka bir deyişle, herhangi bir yükseltmenin dikkate alınmak üzere bu çıtaya karşılaması gerekir. Bu, şu anda sizin için gereklere uymaan yöntemleri edeylene kadar size bir yol sağlar.
  
### <a name="a-simple-sample-plan"></a>Basit bir plan örneği

Yükseltmenin benimsenecek yolda liderlerle ve diğer yöneticilerle daha kapsamlı bir fikir birliğine SharePoint olması gerekir. SharePoint Yöneticileri sıklıkla ağ yöneticileriyle Microsoft SQL Server, Ağ ve Güvenlik ekipleriyle ve daha birçok konuda işbirliği yapar. Birçok katılımcının olduğu yerde, yükseltme ve geçiş planınız için bir anlaşma ayarlamanız veya ayarlamalar yapmak zorundayabilirsiniz. Örneğin, verileri, şirketinizin bir bölümü tarafından Microsoft 365'te SharePoint Online'ın kullanımına geçirilirse, büyük olasılıkla ağ içinde performans ayarlaması veya testi yapmak gerekir. Etkilenen ekiplere, daha önce bilgi gerekir.
  
Basit örneğimde, bir yöneticinin SharePoint göstermek istiyorum ve ardından tüm paydaşların üzerinde anlaştığı planı listelsin. Netlik sağlamak için, anlaşmalarınızı ve kararlarınızı belgelenin.
  
Plan, bir grubu ayrıntılı bir çözümlemeyle başladıktan sonra başlar ve grubu rollerini, sorunları ve bazı yükseltme seçeneklerini daraltmaya yol açacak diğer önemli bilgileri tanımlamaya çalışır. Bundan sonra, yönetici yönetici tarafından bir yükseltme SharePoint yapılır ve proje katılımcıları eylem planı üzerinde onaylar.
  
'En önemli' madde işareti listem:
  
- Kullanılabilirlik, uyumluluk standartlarının SharePoint yerleşik özellikleri.
    
- Verilerin çoğu üç site koleksiyonunda yer alıyor. Geliştirme ekibi tarafından önemli kullanılan toplantı çalışma alanlarından biri ve dünya çapında birden fazla saat diliminde yoğun olarak kullanılıyor.
    
- Yaygın olarak kullanılan 17 site daha vardır.
    
- En büyükleri iki belge kitaplığı (kök site koleksiyonunda Toplantı Çalışma Alanı ve Belgeler) ve her biri 8000'den çok belge. Elektronik tablo ekleri olan çok fazla sayıda arşivlenmiş belgemiz ve listemiz var.
    
- Hassas verileri olan ve Uyumlu kalması gereken 14 kitaplık listesi vardır.
    
- Nerede olursa olsun, esnayı ve e-keşifleri yapma yeteneğine sahip OLASILIK OLASILIK.
    
- InfoSec kuralları nedeniyle, bu verilerin bir bazıları şirket içinde kalarak var olmalı.
    
 **Yükseltme ve geçiş seçimlerim:**
  
| Evet | Hayır |
|:-----|:-----|
|Veritabanı ekleme ile veritabanlarını yükseltme  <br/> |Yerinde yükseltme  <br/> |
|Gruplarla yan yana yükseltme  <br/> |Karma Yükseltme  <br/> |
|Microsoft 365'de SPO'ya Geçiş API'si (kişisel site verileri için)  <br/> |SharePoint Karma'ya sahip (henüz gerekli değil)  <br/> |
|Kritik veriler için SharePoint Online'a el ile yapılan bazı veri geçişleri  <br/> |FastTrack sihirbazına yükseltmeyi Microsoft 365  <br/> |
   
 **Önerilen planım:**
  
Şirket içinde, yan yana SharePoint sürümleriyle yükseltin, biraz sanallaştırın, böylece önce veritabanlarını yükseltebilirsiniz. SharePoint 2007'den SharePoint 2010'a gidin. Sonuçta elde edilen sunucu grubu Yöneticiler ve Geliştirmeler tarafından test edildi. Sonuçta elde edilen grubu kullanıcılar test ediyor. Bu süre boyunca gösteriyi durduran sorunları düzeltin. Yine yan yana, 2010 veritabanlarını SharePoint 2013'e SharePoint yükseltin. Test. Kullanıcı testi/pilot'ları. Bu süre boyunca gösteriyi durduran sorunları düzeltin.
  
- SPO ile Arama Federasyon Karma'nın sizin 2013'e uygun olup olduğunu düşünün.
    
- buradan [FastTrack](https://fasttrack.microsoft.com) Online'a yükseltmek SharePoint yardım alabilirsiniz. 
    
- Herhangi bir site koleksiyonunun Microsoft 365 Aboneliğine yük Microsoft 365. (Microsoft 365 Uyumluluk standartlarını [karşılar](/compliance/regulatory/offering-home). Microsoft 365 [eBulma'ya sahiptir ve](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) Uyumluluk [Merkezi aracılığıyla](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) Esnet'i kabul ediyor olabilir.) 
    
Aksi takdirde, SharePoint Server 2016'ya yan yana yükseltmeye devam edersiniz.
  
> [!NOTE]
> Yönetici tarafından yapılan öneriler arasında yükseltmeyi planlama ve gerçek süreç, yükseltmenin dayandır olduğu diğer paydaşlarla yapılan konuşmalardır. Örneğin, bazen ekonomik nedenler yöneticileri planlarını değiştirmeye zorlar. Son karar ne olursa olsun, çalışmadan önce, üzerinde anlaşmaya var olan planı belgelelisiniz. Şöyle bir şey olabilir: 
  
 **Eylem planım:**
  
Şirket içinde, server 2010 ve 2013'SharePoint varsayılan oluşturmak için sanal bir ortam kullanıyoruz. SharePoint Server 2016, 2016'nın sistem gereksinimlerini karşılayacak yeni donanım üzerine inşa edilecektir. Veritabanlarını 2007'den, SharePoint Server 2016 ile bu sürümler arasındaki tüm sürümlerden SharePoint için veritabanı eklemeleri yapacağız. Yerel özelliklerin ihtiyaçlarımızı karşılaması yoksa, şu anda SharePoint Server 2016 ortamı için temel özelleştirmeler yeniden oluşturmaktadır. Başarılı olursak, yeni donanım üzerinde yükseltilmiş veritabanları ve daha az özelleştirmeyle şirket içi bir sunucu grubum olacak. Yükseltilmiş içerik veritabanlarını SharePoint Server 2013'te yeni site koleksiyonlarına ekledikten sonra, canlı kullanım için yeni SharePoint Server 2016 ortamına DNS testi/denemesi yapacağız.
  
- Şu anda SharePoint Server 2016 ile SharePoint Online arasında bir Federasyon SharePoint dikkate alamayacak.
    
- Tahminen sitelerimizin %35'i ilgili etki alanlarıyla yeni SPO sitelerine  dönüştü veya sonunda en OneDrive İş haline gelir. Siteleri dönüştürmek veya yeni siteleri SPO'ya yönlendirmek için başka fırsatlar arıyoruz.
    
- Geçiş işleminin bu bölümü el ile, kişisel sitelere sürükleyip bırakarak ve bir bölümünü de geçiş API'si OneDrive İş ile olacak.
    
Planı takip etmek için daha ayrıntılı adımlar veya belirli yükseltme yönergelerine yönelik bir dizi bağlantı gerekir. MOSS 2007 bilgisayarı devre dışı bırakılmamış ve sanal ortamlar karşılaştırma adına korunarak; bununla birlikte, kullanıcılar SharePoint Server 2016'ya yeniden yönlendirildiklarında yükseltme tamamlanır.
  
Çoğunlukla yöntem seçiminde en önemli faktörler yükseltmenin toplam maliyeti ve zaman içinde ortaya maliyetidir (geçiş yol haritası makalesinde bu SharePoint daha fazla bilgi bulabilirsiniz). Öte yandan, ileri planlamanın beklentileri ayarlama, akıllı seçim ve nasıl bir başarı elde edebileceklerini çerçeveleme açısından size çok fayda sağlar.
  
## <a name="related-links"></a>İlgili bağlantılar

[Office 2007 sunucularından ve istemcilerinden yükseltmeye yardımcı olan kaynaklar](upgrade-from-office-2007-servers-and-products.md)
  
[Microsoft Yaşam Döngüsü İlkesi ve Yaşam Döngüsü araması](https://support.microsoft.com/lifecycle)
  
[Yükseltme veya geçişte yardımcı olacak Microsoft İş Ortaklarını arama](https://partnercenter.microsoft.com/pcv/search)
