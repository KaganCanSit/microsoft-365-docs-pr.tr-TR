---
title: Microsoft 365 Kurumsal planlama - Siber güvenlik mimarisi
description: Microsoft'ta, Cybersecurity Architect Enterprise Microsoft'un bu mimaride güvenlik güçlüklerini aşmayı öğrenin.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: c580b6529a3467a08befdb07c1b0b8d516208183
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005447"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>One Architect'in görünüm noktası üzerinden tekneyle açabilirsiniz güvenlik engelleri

Microsoft'un Siber Güvenlik Mimarı olan Bu makalede, Enterprise kuruluşlarda karşılaştığı en önemli güvenlik güçlüklerini açıklayan ve bu engeli aşacak yaklaşımlar öneren, [Sık](https://www.linkedin.com/in/kozeta-garrett-53013a6/) karşılaşılan güvenlik sorunlarına karşı yaklaşımlar önerildi.

## <a name="about-the-author"></a>Yazar hakkında

![HerletaTis fotoğrafını ekleyin.](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

Bir Bulut Güvenlik Mimarı olarak birçok kuruluşla birlikte çalışarak, Microsoft 365 ve Azure'a geçerek müşteriler için güvenlik mimarisini tasarlama ve uygulamaya odaklanan stratejik ve teknik rehberlik sunmak, kurumsal güvenlik çözümleri geliştirmek ve iş güvenliği mimarisiyle kültürün dönüşümüne yardımcı olmak için birçok kuruluşla birlikte çalıştım. Deneyimim olay algılama ve yanıt, kötü amaçlı yazılım çözümlemesi, test etme, ayrıca IT güvenliği ve savunma sonrası için geliştirmeler öner gibi bilgi içerir. Modernleştirme çabaları da içinde olmak üzere, işletme için güvenliği etkinleştiren bir sonuç olarak ortaya çıkan dönüşümler konusunda çok tutkuluum.

Son birkaç yıl boyunca güvenlik modernleştirmeyi benimseyen kuruluşların, son COVID-19 durumuna rağmen güvenli bir şekilde uzaktan çalışmaya devam eden harika bir konumda nasıl olduğunu görmek EN çok memnun kaldı. Ne yazık ki bu durumlar, bu acil ihtiyaç için hazır olmayan bazı müşterilerin çağrılarını geri çağırma çağrısı olarak da karşı çıktı. Birçok kuruluş hızlı bir şekilde modernleştirmeleri, birikimli IT güvenlik güvenlik nedenlerini devre dışı bıraktıktan sonra gece boyunca güvenlik durumlarını geliştirmeleri gerektiğini fark ediyor; böylece son derece alışılmışın dışında böyle durumlarda çalışamıyorlar.

Ancak Iyi haber, Microsoft'un kuruluşların güvenlik mezralarını hızlı bir şekilde yukarıya doğru hareketle göstermelerine yardımcı olmak için bazı harika kaynaklar kurdu. Bu kaynaklara ek olarak, her gün bu engeli aşarak tekneyle binen müşterilerle karşılaştığım en büyük güçlükleri paylaşmak istiyorum.

Şu anda Kuzey Virginia'da, ülkemizin Capital, Washington DC'sinde yaşıyorum. Yürüyüş, yürüyüş, yürüyüş ve yüzme gibi dış mekan etkinliklerinin ve egzersizlerin her türlüsine bayılacakm. Bunları yemek yapmak, gurme yemek yapmak ve seyahat etmek için tadını çıkariyorum.

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Bulut benimsemenin başlamasından itibaren Güvenlik ekibiyle iş ortağı olun

Başlangıç olarak, organizasyonu bulunduracak ekiplerin en baştan koordine etmelerinin ne kadar önemli olduğunu vurguy istemiyorum. Güvenlik ekipleri, bulutun benimsenmesi ve tasarımının ilk aşamalarında kritik iş ortakları olarak tanınıyor olmalı. Bu, güvenlik ekiplerinin yalnızca iş için ek özellikler (güvenli mobil cihazlardan gelen harika bir kullanıcı deneyimi, tam işlevsellik uygulamaları gibi) için değil, sınırlı işlevsellik e-posta ve üretkenlik uygulamalarının ötesinde şirket verileri üzerinde değer oluşturması için, aynı zamanda yeni ve eski güvenlik sorunlarını çözmeye yardımcı olan depolama, AI ve bilgi işlem analizi özelliklerini kullanmak anlamına gelir. Başarılı olmak için güvenlik ekiplerinin kişiler (kültür), süreçler (eğitim) ve teknoloji de içinde olmak üzere bu vardiyanın tüm yönlerini yönetmeye dahil olması gerekir. Ayrıca, Güvenlik İşlemleri Merkezi'nin (SOC) modernleştirme ve sürekli iyileştirmeye yatırım yapmak anlamına da gelir. Dijital dönüştürmenin güvenli bir şekilde gerçekleştir olduğundan emin olmak için, güvenlik stratejinizi iş stratejiniz ve ortam eğilimleriyle hizalamak için birlikte çalışma. Bu iyi bir iş olduğunda, kuruluşlar iş, IT ve güvenlik değişiklikleri dahil olmak üzere değişikliklere daha hızlı uyum sağlama özelliğini geliştirir.

Müşterilerin en çok engeli aşarak geçiş yaptığı zaman, işlemlerle SOC ekipleri arasında gerçek bir ortaklık olmadığını görüyorum. Operasyon ekibi, bulutu benimsemek için sıkı son tarihlerle baskıya geçirilmiş ve veklet edilmiş durumdayken, güvenlik ekipleri kapsamlı bir güvenlik stratejisini gözden geçirmek ve planlamak için her zaman erken süreçlere dahil değildir. Bu, şirket içinde farklı bulut bileşenlerini ve bileşenlerini tümleştirmeyi içerir. Bu ortaklığın olmaması, silolarda belirli bileşenlerine yönelik denetimler uygulamak için çalışıyor gibi görünen farklı ekiplere destek olmakta, uygulama, sorun giderme ve tümleştirmenin daha karmaşık hale getirmesini sağlar.

Bu engeli aşarak çalışan müşterilerin, karma bulut iş yüklerini korumak için güvenlik stratejisini ve gereksinimlerini yenilemek için İşlemler ve Yönetim ile Güvenlik ve Risk yönetim ekipleri arasında iyi bir ortaklık vardır. Siber güvenlik yönetimi, risk ve uyumluluk gereksinimlerine uygun olarak veri koruması ve sistemleri ve hizmetlerin kullanılabilirliği gibi en üst düzey güvenlik hedeflerine ve sonuçlarına lazerle odaklanmaktadırlar. Bu kuruluşlar, Operasyon ve Yönetim ekibiyle SOC arasında güvenlik tasarımı yaklaşımı açısından kritik öneme sahip ve yatırımlarının değerini en üst düzeye çıkaracak olan erken aşama ortaklıklar geliştirir.

## <a name="build-a-modern-identity-based-security-perimeter"></a>Modern (kimlik tabanlı) bir güvenlik çevresi oluşturma

Ardından, Sıfır Güven mimarisi yaklaşımı benimser. Bu, modern, kimlik tabanlı bir güvenlik çevresi inşa ile başlar. İster yerel ister bulut olsun, her erişim girişiminin doğrulanana kadar güvenilmeyen olarak kabul edildiği ("asla güvenme, her zaman doğrula" güvenlik mimarisini tasarla. Bu tasarım yaklaşımı güvenliği ve üretkenliği artırmakla birlikte, kullanıcıların her cihaz türüyle her yerden çalışmalarını da sağlar. Denetimlere dahil edilen gelişmiş bulut denetimleri Microsoft 365 risk düzeyine göre değerli kaynaklara erişimi denetleyirken kullanıcı kimliklerini korumaya yardımcı olur.

Önerilen yapılandırma için bkz. [Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="transition-security-controls-to-the-cloud"></a>Buluta güvenlik denetimlerini geçiş

Birçok güvenlik ekibi, "ağ çevre güvenliği" koruma ve şirket içi güvenlik araçlarını ve denetimlerini bulut çözümlerine "zorlama" dahil olmak üzere tüm şirket içi dünya için yerleşik geleneksel en iyi yöntemleri kullanmaya devam ediyor. Bu tür denetimler bulut için tasarlanmadı, etkili değildir ve modern bulut özelliklerini benimsemeyi engeller. Ağ çevre güvenliği yaklaşımı için kullanılan süreçlerin ve araçların verimsiz, bulut özelliklerine bağlı olduğu kanıtlandı ve modern ve otomatik güvenlik özelliklerinden yararlanmaya izin vermiyor.

Savunma stratejilerini bulut tarafından yönetilen koruma, otomatik araştırma ve düzeltme, otomatik kalem testi, Geçiş için Office 365 Defender ve olay çözümlemelerine kaydırarak bu engeli aşarak bu engeli aşabilirsiniz. Modern cihaz yönetim çözümlerini kullanan müşteriler, tüm cihazlar genelinde (akıllı telefon, kişisel bilgisayar, dizüstü bilgisayar veya tablet) otomatik yönetim, standart düzeltme eki, virüsten koruma, ilke zorlama ve uygulama koruması uygulamaya başladı. Bu şekilde VPN, Microsoft System Center Configuration Manager (SCCM) ve Active Directory grup ilkeleri ortadan kalkmış olur. Bu, koşullu erişim ilkeleriyle birlikte, güçlü denetim ve görünürlük sağlar ve ayrıca kullanıcılarının nereden işletim sisteminden bağımsız olarak kaynaklara kolay erişim sağlar.

## <a name="strive-for-best-together-security-tools"></a>'Birlikte en iyi şekilde' güvenlik araçları için çabayın

Müşterileri yanlışlıkla güvenlik araçlarına "cins" yaklaşımını benimser diğer bir engel. Ortaya çıkan güvenlik  ihtiyaçlarını karşılamak için sürekli "cinsin en iyileri" puan çözümlerini katmanlama, kurumsal güvenliğin bozlarak ortaya konulmalarına neden olur. En iyi yaklaşımlara sahip olsalar bile, çoğu ortamdaki araçlar fazla pahalı ve karmaşık hale gelir, çünkü tümleşik değildir. Bu da, ekibin karşılayak işleyenene göre daha fazla uyarı olduğu için görünürlükte boşluklar oluşturur. SecOps ekibini yeni araçlarla yeniden sınırlamak da sürekli bir zorluk haline gelir.

"Basit bir yaklaşımdır" yaklaşımı da güvenlik için işe yarar. "Cins en iyi" araçlardan sonra yola çıktıktan sonra, varsayılan olarak birlikte çalışan araçlarla "birlikte en iyi birlikte" bir strateji benimseerek bu engelin üzerinde binin. Microsoft güvenlik özellikleri, uygulamalara, kullanıcılara ve bulutlara yayılan tümleşik tehdit korumasıyla tüm kuruluşu korur. Tümleştirme, bir kuruluşun girişte saldırganlar bulundurarak ve hızlı bir şekilde düzelterek daha iyi ve riski azaltabilmesini sağlar.

## <a name="balance-security-with-functionality"></a>Güvenliği işlevsellikle dengeleme

Uzun bir siber güvenlik arka planından ve deneyiminden sonra, ilk olarak en güvenli yapılandırmaya hemen başlamayı ve kuruluşların faaliyet ve güvenlik ihtiyaçlarına göre güvenlik yapılandırmalarını rahatlatmalarını sağlamayı tercih ederim. Bununla birlikte, bu fiyat kayıp işlevsellik ve düşük kullanıcı deneyimi fiyatla gelebilir. Birçok kuruluş öğrendiklerini gibi, kullanıcılar için güvenlik çok zorsa, sizin dışınız üzerinde çalışmak için, unmand bulut hizmetlerini kullanma da dahil, bir yol bulurlar. Benim kabul etmek ne kadar zorsa, bu işlev-güvenlik bakiyesi elde edilmenin gerektiğini fark ettim.

Kullanıcıların işlerini yapmak için gerekenleri yapacaklarını fark eden kuruluşlar, "Shadow IT kullanıcının" ile mücadele etmeye değ olmadığının farkındadır. Shadow IT ve onaysız SaaS uygulamalarının işlerinde kullanımı konusunda, IT çalışanlarının en çok soruna neden olduğunu fark ediyor. Bu stratejilerini, kullanımını teşvik etmek için (gizleme yerine) ve oluştur oluşturılabileceği riskleri azaltmaya odaklanmak için kaydırmıştır. Bu kuruluşun güvenlik ekipleri her şeyin engellenmiş, günlüğe kaydedilip ters proxy veya VPN aracılığıyla gönderildiğini kabul etmez. Bunun yerine, bu güvenlik ekipleri değerli ve hassas verileri yanlış taraflara veya kötü amaçlı uygulamalara maruz kalmalarını koruma çabalarını bir kez daha ortaya çıkarlar. Bunlar, verilerin bütünlüğünü korumak için çalışır. Şifreleme, güvenli çok faktörlü kimlik doğrulaması, otomatik risk ve uyumluluk ve bulut erişimi güvenlik aracı (CASB) özellikleri de dahil olmak üzere daha gelişmiş bulut bilgi koruma yeteneklerine tam erişim sağlarken, hatta birden çok platformda korumalı paylaşımı teşvik etmek için izin verir ve hatta teşvik etmektedir. Bu kullanıcılar, işlerinin rekabetçi kenarda kalmasını sağlayan ilham verici yaratıcılığa, verimlilike ve işbirliğine gölge veriyor.

## <a name="adopt-a-methodical-approach"></a>Yöntemsel bir yaklaşımı benimseme

Sektör ne olursa olsun, farklı kuruluşlarda bulut güvenliği uygulama konusunda karşılaştığım güçlüklerin çoğu birbirine çok benzer. Her ne kadar belirli özellikler ve özelliklerle ilgili birçok harika belge varken, kuruluş düzeyinde nelerin geçerli olduğu, güvenlik özelliklerinin nerede çakışacağı ve becerilerin nasıl entegre olması gerektiğiyle ilgili bir düzeyde karışıklık vardır. Ayrıca hangi güvenlik özelliklerinin kutusundan önceden yapılandırıldığından ve kuruluşun yapılandırmasının gerekli olduğu konusunda bir belirsizlik düzeyi de vardır. Buna ek olarak, SOC ekipleri ne yazık ki hızla bulutun benimsenmesi ve dijital dönüşüme hazırlanmak için gereken bütçe ayırma, tam maruz kalma, eğitim ve bütçe ayırma durumlarına sahip değildirler.

Microsoft, bu engelleri temizlemenize yardımcı olmak için, güvenlik stratejinize ve uygulamanıza yöntemsel bir yaklaşım benimsersiniz ve bu kaynaklar için tasarlanmış çeşitli kaynaklar bağışlar.

|Kaynak   |Daha fazla bilgi  |
|---------|---------|
|[Evden çalışmayı desteklemek için güvenlik ekiplerine en önemli görevler](../security/top-security-tasks-for-remote-work.md)      | Kendinizi aniden iş yerinde çalışan iş gücü gibi büyük bir iş gücüne destek olarak bulursanız, bu makale güvenliği hızla yukarıya alamanıza yardımcı olur. Lisans planınıza dayalı olarak önerilen en önemli görevleri içerir.    |
|[Microsoft 365 Karar Verenler için Güvenlik](../security/Microsoft-365-security-for-bdm.md)    | Daha kapsamlı bir plan için zaman olduğunda, bu makale saldırı yüzeyine göre Microsoft 365 kapsayan öneriler içerir. Lisans ve alana göre sıralamak için (kimlik, tehdit koruması ve izleme gibi) kullanabileceğiniz bir elektronik tablo bile vardır.  |
|[Microsoft güvenlik mimarisi önerileri](/security/compass/compass)    | Bir güvenlik mimarıysanız, kimlik, ağ ve güvenlik işlemleri de dahil olmak üzere, disipline göre düzenlenmiş güvenlik önerilerini gördüğünüzden emin olun.   |
|[Microsoft Güvenlik İşlemleri önerileri](/security/compass/security-operations-videos-and-decks)|Güvenlik İşlemleri Merkezi'nde (SOC) ayarlama ve çalıştırmaya yönelik Microsoft önerilerini öğrenin |
|[Baş Bilgi Güvenlik Görevlisi (CISO) Atölye Eğitimi](/security/ciso-workshop/ciso-workshop)   | Bulut güvenliğinde yeniysiniz, bu video dizilerini kaçırmayın.        |
|[docs.security.com/security](/security/)    | Güvenlik stratejisi ve mimarisi için Microsoft genelinden teknik kılavuz.        |
| | |

Bu kaynakların hepsi başlangıç noktası olarak kullanılmaya ve kuruluş  ihtiyaçlarına göre uyarlanmış olarak tasarlanmıştır.
