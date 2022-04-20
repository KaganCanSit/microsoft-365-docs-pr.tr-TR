---
title: ABD bankacılık ve sermaye piyasaları için temel uyumluluk ve güvenlik konuları
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
ms.prod: microsoft-365-enterprise
ms.custom: seo-marvel-jun2020
ms.localizationpriority: high
description: Finansal hizmet kurumlarının Microsoft 365 ve Teams kullanarak finansal güvenlik uyumluluğunu nasıl koruyabileceğini ve etkili bir şekilde işbirliği yapabileceklerini öğrenin.
f1.keywords: NOCSH
ms.openlocfilehash: ed00d120d00253c1abbb6d0c0109fdce0b7ff863
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948275"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>ABD bankacılık ve sermaye piyasaları için temel uyumluluk ve güvenlik konuları

## <a name="introduction"></a>Giriş
Finansal hizmet kurumları sıkı güvenlik, uyumluluk ve idare denetimleri taleplerinde neredeyse tüm ticari işletmeleri aşıyor. Verilerin, kimliklerin, cihazların ve uygulamaların korunması yalnızca işletmeleri için kritik öneme sahip değildir, ABD Menkul Kıymetler ve Exchange Komisyonu (SEC), Finansal Endüstri Düzenleme Kurumu (FINRA), Federal Finansal Kurumlar Sınav Konseyi (FFIEC) ve Emtia Vadeli İşlemler Ticaret Komisyonu (CFTC) gibi düzenleyici kurumların uyumluluk gereksinimlerine ve yönergelerine tabidir. Ayrıca, finansal kurumlar Dodd-Frank ve 2002 Sarbanes-Oxley Yasası gibi yasalara tabidir.

Günümüzün artan güvenlik ihtiyat, içeriden risk endişeleri ve kamu veri ihlalleri ikliminde müşteriler, kişisel verileri ve bankacılık varlıkları konusunda onlara güvenmek için finans kuruluşlarından yüksek düzeyde güvenlik de talep ediyor.

Tarihsel olarak, kapsamlı denetimlere duyulan ihtiyaç, finans kurumlarının iç ve dış işbirliği sağlamak için kullandığı BT sistemlerini ve platformlarını doğrudan etkileyip kısıtlamıştı. Günümüzde finansal hizmetler çalışanlarının benimsemesi ve kullanımı kolay modern bir işbirliği platformuna ihtiyacı vardır. Ancak finansal hizmetler, kullanıcıları ve BT sistemlerini tehditlere karşı korumak için ilkeler uygulayan güvenlik ve uyumluluk denetimleriyle kullanıcılar, ekipler ve departmanlar arasında işbirliği yapma esnekliğini dengeleyemez.

Finansal hizmetler sektöründe aşağıdakiler dahil olmak üzere işbirliği araçlarının ve güvenlik denetimlerinin yapılandırılması ve dağıtımı için dikkatli bir şekilde dikkat edilmesi gerekir:
- Ortak kurumsal işbirliği ve iş süreci senaryolarının risk değerlendirmesi
- Bilgi koruma ve veri idaresi gereksinimleri
- Siber güvenlik ve içeriden tehditler
- Mevzuat uyumluluğu gereksinimleri
- Diğer operasyonel riskler

**Microsoft 365, finansal hizmetler kuruluşlarının karşılaştığı çağdaş zorlukları giderebilen modern bir çalışma alanı bulut ortamıdır. Kuruluş genelinde güvenli ve esnek işbirliği, sıkı mevzuat uyumluluğu çerçevelerine uymak için denetimler ve ilke uygulama ile birleştirilir.** Bu makalede, Microsoft 365 platformunun finansal hizmetlerin modern bir işbirliği platformuna geçmesine nasıl yardımcı olduğu açıklanırken, verilerin ve sistemlerin güvenli ve yönetmeliklerle uyumlu kalmasına nasıl yardımcı olur:

* Microsoft 365 ve Microsoft Teams kullanarak kuruluş ve çalışan üretkenliğini etkinleştirme
* Microsoft 365 kullanarak modern işbirliğini koruma 
* Hassas verileri tanımlama ve veri kaybını önleme
* Kaleyi savun
* Kayıtları etkili bir şekilde yöneterek verileri idare etme ve düzenlemelere uyma
* Bilgi engelleri olan etik duvarlar oluşturma
* Veri sızdırma ve şirket içi risklere karşı koruma

Bir Microsoft iş ortağı olarak Protiviti bu makaleye katkıda bulundu ve bu makaleye önemli geri bildirimler sağladı.

Aşağıdaki indirilebilir çizimler bu makaleyi tamamlar. Woodgrove Bank ve Contoso, bu makalede açıklanan özelliklerin finansal hizmetlerin genel mevzuat gereksinimlerini karşılamak için nasıl uygulanabileceğini göstermek için kullanılır. Bu çizimleri kendi kullanımınız için uyarlamaktan çekinmeyin. 

**Microsoft 365 bilgi koruma ve uyumluluk çizimleri**

| Öğe | Açıklama |
|:-----|:-----|
|[![Model posteri: bilgi koruma ve uyumluluk özelliklerini Microsoft 365.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>İngilizce: [pdf](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| olarak [indirme Visio olarak indirme](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japonca: [pdf](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| olarak [indirme Visio olarak indirme](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)  <br/> Kasım 2020'de güncelleştirildi|Içerir: <ul><li>  Microsoft Purview Information Protection ve Microsoft Purview veri kaybı önleme</li><li>Bekletme ilkeleri ve bekletme etiketleri </li><li>Bilgi engelleri</li><li>İletişim uyumluluğu</li><li>Insider riski</li><li>Üçüncü taraf veri alımı</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Microsoft 365 ve Teams kullanarak kurumsal ve çalışan üretkenliğini güçlendirme

İşbirliği genellikle çeşitli iletişim biçimlerini, belgeleri/verileri depolamayı ve bu verilere erişmeyi ve gerektiğinde diğer uygulamaları tümleştirmeyi gerektirir. Finansal hizmetlerdeki çalışanların genellikle diğer departmanların veya ekiplerin üyeleriyle ve bazen de dış varlıklarla işbirliği yapıp iletişim kurmaları gerekir. Bu nedenle silo oluşturan veya bilgi paylaşımını zorlaştıran sistemlerin kullanılması istenmeyen bir durumdur. Bunun yerine, çalışanların güvenli bir şekilde ve şirket ilkesine göre iletişim kurmasını, işbirliği yapmasını ve bilgi paylaşmasını sağlayan platformlar ve uygulamalardan yararlanmak tercih edilir.

Çalışanlara modern, bulut tabanlı bir işbirliği platformu sağlamak, daha üretken olmalarını sağlayan araçları seçmelerine ve tümleştirmelerine ve çevik çalışma yolları bulmalarını sağlamalarına olanak tanır. Teams,güvenlik denetimleri ve kuruluşu koruyan bilgi idare ilkeleriyle birlikte kullanmak, iş gücünüzün etkili bir şekilde iletişim kurmasını ve işbirliği yapmasına yardımcı olabilir.

Teams kuruluş için bir işbirliği merkezi sağlar. Ortak girişimler ve projeler üzerinde verimli bir şekilde çalışmak için insanların bir araya getirilmesine yardımcı olur. Teams, ekip üyelerinin 1:1 ve çok taraflı sohbet konuşmaları yürütmelerine, birlikte çalışmalarına ve belgeleri birlikte yazmalarına ve dosyaları depolamalarına ve paylaşmalarına olanak tanır. Teams ayrıca tümleşik kurumsal ses ve video aracılığıyla çevrimiçi toplantıları kolaylaştırır. Teams Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI ve üçüncü taraf iş kolu uygulamaları gibi Microsoft uygulamalarıyla da özelleştirilebilir. Teams hem iç ekip üyeleri hem de ekip kanallarına katılabilen, sohbet konuşmalarına katılabilen, depolanan dosyalara erişebilen ve diğer uygulamalardan yararlanabilen izin verilen dış kullanıcılar tarafından kullanılmak üzere tasarlanmıştır

Her Microsoft Ekibi bir Microsoft 365 grubu tarafından yedeklenmiştir. Bu grup, Teams dahil olmak üzere çok sayıda Office 365 hizmet için üyelik hizmeti olarak kabul edilir. Microsoft 365 grupları, "sahipler" ile "üyeler" arasında güvenli bir şekilde ayrım yapmak ve Teams içindeki çeşitli özelliklere erişimi denetlemek için kullanılır. Uygun idare denetimleri ve düzenli olarak yönetilen erişim gözden geçirmeleriyle birleştiğinde, Teams yalnızca üyelerin ve sahiplerin yetkili kanalları ve özellikleri kullanmasına izin verir.

Teams finansal hizmetlerden yararlandığı yaygın bir senaryo, iç projeleri veya programları çalıştırırken geçerlidir. Örneğin bankalar, zenginlik yönetimi firmaları, kredi sendikaları ve sigorta sağlayıcıları gibi birçok finans kurumunun kara para aklama ve diğer uyumluluk programlarına sahip olması gerekir. BT'nin, perakende ve zenginlik yönetimi gibi iş hatlarının ve mali suç biriminin birbiriyle veri paylaşması ve program veya belirli soruşturmalar hakkında iletişim kurması için işlevsel bir ekip gerekebilir. Geleneksel olarak, bu programlar paylaşılan ağ sürücülerini kullanır, ancak bu yaklaşım aşağıdakiler de dahil olmak üzere çok sayıda zorluk sunabilir:
* Belgeyi aynı anda yalnızca bir kişi düzenleyebilir.
* Kişilerin eklenmesi/kaldırılması genellikle BT'yi içerdiği için güvenliği yönetmek zaman alır.
* Veriler, paylaşılan ağ sürücülerinde gerekenden veya istenenden çok daha uzun süre yerleşik olarak kalır.

Teams hassas istemci verilerini güvenli bir şekilde depolamak ve ekip üyeleri arasında hassas konuların ele alınabileceği konuşmalar yürütmek için bir işbirliği alanı sağlayabilir. Ekibin birden çok üyesi aynı anda tek bir belgeyi düzenleyebilir veya üzerinde işbirliği yapabilir. Program sahibi veya koordinatör, ekip sahibi olarak yapılandırılabilir ve ardından gerektiğinde üye ekleyip kaldırabilir.

Bir diğer yaygın senaryo, belgeleri depolama ve yönetme de dahil olmak üzere güvenli bir şekilde işbirliği yapmak için Teams "sanal veri odası" olarak kullanmaktır. Yatırım bankacılığı, varlık yönetimi veya özel sermaye firmaları içindeki ekip üyeleri ve sendikalar, bir anlaşma veya yatırım üzerinde güvenli bir şekilde işbirliği yapabilir. İşlevler arası ekipler genellikle bu tür anlaşmaların planlanması ve yerine getirilmesinde görev alır ve verileri güvenli bir şekilde paylaşma ve konuşma yürütme özelliği temel bir gereksinimdir. İlgili belgeleri dış yatırımcılarla güvenli bir şekilde paylaşmak da önemli bir gereksinimdir. Teams, yatırım verilerini merkezi olarak depolamak, korumak ve paylaşmak için güvenli ve tam olarak denetlenebilir bir konum sağlar.

![Bir toplantıdaki bir grup ofis çalışanı, büyük bir kararnamedeki görüntüleri tartışır.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: İşbirliğini geliştirme ve uyumluluk riskini azaltma

Microsoft 365, temel üyelik hizmeti olarak Microsoft 365 grupları kullanarak Teams için diğer ortak ilke özelliklerini sağlar. Bu ilkeler işbirliğini iyileştirmeye ve uyumluluk gereksinimlerini karşılamaya yardımcı olabilir.

**Microsoft 365 grup adlandırma ilkeleri**, Microsoft 365 grupların ve dolayısıyla ekiplerin şirket ilkesine göre adlandırılmasını sağlamaya yardımcı olur. Adlar uygun değilse sorunlu olabilir. Örneğin, adlar uygun şekilde uygulanmadıysa çalışanlar hangi ekiplerle çalışacaklarını veya hangi ekiplerle bilgi paylaşacaklarını bilmeyebilir. Grup adlandırma ilkeleri (ön ek/sonek tabanlı ilkeler ve özel engellenen sözcükler için destek dahil) iyi bir "hijyen" uygulayabilir ve ayrılmış sözcükler veya uygunsuz terminoloji gibi belirli sözcüklerin kullanımını engelleyebilir.
  
**Microsoft 365 grup süre sonu ilkeleri**, Microsoft 365 grupların ve dolayısıyla ekiplerin kuruluşun istediği veya ihtiyaç duyduğundan daha uzun süre saklanmamasını sağlamaya yardımcı olur. Bu özellik, iki önemli bilgi yönetimi sorununu önlemeye yardımcı olur:

* Gerekli olmayan veya kullanılmayan ekiplerin çoğaltılması.
* Artık gerekli olmayan veya kuruluş tarafından kullanılmayan verilerin fazla tutulması (yasal saklama/koruma durumları hariç).

Yöneticiler Microsoft 365 grupları için 90, 180 veya 365 gün gibi bir süre sonu süresi belirtebilir. bir Microsoft 365 grubu tarafından yedeklenen bir hizmet süre sonu boyunca etkin değilse, grup sahiplerine bildirim gönderilir. Hiçbir işlem yapılmazsa, Microsoft 365 grubu ve Teams dahil olmak üzere ilgili tüm hizmetleri silinir.
  
Teams ve diğer grup tabanlı hizmetlerde depolanan verilerin fazla tutulması finansal hizmet kuruluşları için risk oluşturabilir. Microsoft 365 grup süre sonu ilkeleri, artık gerekli olmayan verilerin saklanmasını önlemeye yardımcı olmak için önerilen bir yoldur. Yerleşik saklama etiketleri ve ilkeleriyle birlikte Microsoft 365, kuruluşların yalnızca kurumsal ilkeleri ve mevzuat uyumluluğu yükümlülüklerini karşılamak için gereken verileri saklamasına yardımcı olur.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Özel gereksinimleri kolayca tümleştirme

Teams, varsayılan olarak ekiplerin self servis oluşturulmasını sağlar. Ancak, düzenlemeye tabi olan birçok kuruluş, çalışanları tarafından şu anda hangi işbirliği kanallarının kullanıldığını, hangi kanalların hassas veriler içerebileceğini ve kuruluş kanallarının sahipliğini denetlemek ve anlamak ister. bu idare denetimlerini kolaylaştırmak için Microsoft 365 kuruluşun self servis ekip oluşturmayı devre dışı bırakmasına olanak tanır. Kuruluşlar, Microsoft Power Apps ve Power Automate gibi iş süreci otomasyon araçlarını kullanarak çalışanların yeni bir ekip oluşturma isteğinde bulunmaları için basit formlar ve onay süreçleri oluşturup dağıtabilir. Onaylandığında ekip otomatik olarak sağlanabilir ve istekte bulunana bir bağlantı gönderilebilir. Bu şekilde kuruluşlar uyumluluk denetimlerini ve özel gereksinimlerini ekip oluşturma süreciyle tasarlayabilir ve tümleştirebilir.
 
### <a name="acceptable-digital-communication-channels"></a>Kabul edilebilir dijital iletişim kanalları

FINRA, [düzenlemeye tabi firmaların dijital iletişimlerinin Exchange Yasası 17a-3 ve 17a-4'ün yanı sıra FINRA Kural Serisi 4510'un kayıt tutma gereksinimlerini karşıladığını vurgular](https://www.finra.org/rules-guidance/key-topics/books-records). FINRA, kuruluşların uyumluluk ve risk yönetimini geliştirmesine yardımcı olmak için önemli bulguları, gözlemleri ve etkili uygulamaları içeren yıllık bir rapor yayınlar. [FINRA, 2019 Sınav Bulguları ve Gözlemleri Raporu'nda](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) dijital iletişimi firmaların denetim ve kayıt tutma gereksinimleriyle uyumlu zorluklarla karşılaştıkları önemli bir alan olarak tanımladı.

Bir kuruluş çalışanlarının uygulama tabanlı mesajlaşma hizmeti veya işbirliği platformu gibi belirli bir uygulamayı kullanmasına izin verirse, firmanın iş kayıtlarını arşivlemesi ve söz konusu uygulamadaki çalışanların etkinliklerini ve iletişimlerini denetlemesi gerekir. Kuruluşlar, FINRA kurallarına ve menkul kıymet yasalarına uymak ve çalışanların bu uygulamaların kullanımıyla ilgili bu kuralların olası ihlallerini takip etmek için durum tespiti yürütmekle sorumludur.
  
FINRA tarafından önerilen etkili uygulamalar şunlardır:
* Dijital iletişim kanalları için kapsamlı bir idare programı oluşturun. Kuruluşun hangi dijital iletişim kanallarına izin verildiğine ilişkin kararlarını yönetin ve her dijital kanal için uyumluluk süreçlerini tanımlayın. Dijital iletişim kanallarının hızla değişen ortamını yakından izleyin ve uyumluluk süreçlerini güncel tutun.
* İzin verilen dijital kanalları net bir şekilde tanımlayın ve kontrol edin. Hem onaylanan hem de yasaklanan dijital kanalları tanımlayın. Kuruluşun kayıt yönetimi ve denetim gereksinimlerine uyma becerisini sınırlayan, dijital kanallarda yasaklanmış dijital kanalların veya yasaklanmış özelliklerin kullanımını engelleyin veya kısıtlayın.
* Dijital iletişimler için eğitim sağlayın. Kayıtlı temsilcilere onaylı dijital kanallara erişim vermeden önce zorunlu eğitim programları uygulayın. Eğitim, bir kuruluşun iş ve kişisel dijital iletişim beklentilerinin netleştirilmesine yardımcı olur ve her kanalın izin verilen özelliklerini uyumlu bir şekilde kullanmada personele yol gösterir.

FINRA'nın Dijital İletişim bulguları ve gözlemleri doğrudan bir kuruluşun işle ilgili tüm iletişimleri korumak için [SEC Kural 17a-4'e](https://www.law.cornell.edu/cfr/text/17/240.17a-4) , iletişimlerin denetlenip gözden geçirilmesi için FINRA kuralları [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) ve [3120'ye](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) ve kayıt tutma için Kural Serisi [4510'a](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) uyma becerisiyle ilgilidir. Emtia Vadeli İşlemLer Ticaret Komisyonu (CFTC), 17 CFR 131'in altında benzer gereksinimleri ilan eder. Bu düzenlemeler bu makalenin ilerleyen bölümlerinde ayrıntılı olarak ele alınmaktadır.

***Teams, kapsamlı Microsoft 365 güvenlik ve uyumluluk tekliflerinin yanı sıra, finansal hizmet kurumlarının etkin bir şekilde iş yürütmesi ve düzenlemelere uyması için kurumsal bir dijital iletişim kanalı sağlar.*** Bu makalenin geri kalanında kayıt yönetimi, bilgi koruması, bilgi engelleri ve denetim denetimi için yerleşik Microsoft 365 özelliklerin Teams bu yasal yükümlülükleri karşılamaya yardımcı olacak güçlü bir araç takımı sağladığı açıklanmaktadır.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Microsoft 365 ile modern işbirliğini koruma

### <a name="secure-user-identities-and-control-access"></a>Kullanıcı kimliklerinin güvenliğini sağlama ve erişimi denetleme

***Müşteri bilgilerine, finansal belgelere ve uygulamalara erişimi koruma, kullanıcı kimliklerinin güvenliğini güçlü bir şekilde sağlamakla başlar.*** Bu, kuruluşun kimlikleri depolaması ve yönetmesi, güvenilir bir kimlik doğrulama aracı sağlaması ve bu uygulamalara erişimi dinamik olarak denetlemesi için güvenli bir platform gerektirir.

Çalışanlar çalışırken, uygulamadan uygulamaya veya birden çok konum ve cihaz arasında geçiş yapabilir. Yol boyunca her adımda verilere erişimin kimliği doğrulanmalıdır. Kimlik doğrulama işleminin kimliklerin tehlikeye atılmasını sağlamak için güçlü bir protokolü ve birden çok kimlik doğrulama faktörünün (tek seferlik SMS geçiş kodu, kimlik doğrulayıcı uygulaması ve sertifika gibi) desteklemesi gerekir. Risk tabanlı erişim ilkelerini zorunlu tutma, finansal verileri ve uygulamaları içeriden gelen tehditlere, yanlışlıkla veri sızıntılarına ve veri sızdırmaya karşı korumak için kritik öneme sahiptir.

Microsoft 365, kimliklerin merkezi olarak depolandığı ve güvenli bir şekilde yönetildiği [Azure Active Directory (Azure AD)](/azure/active-directory/) içinde güvenli bir kimlik platformu sağlar. Azure AD, bir çok ilgili Microsoft 365 güvenlik hizmetiyle birlikte, çalışanlara güvenli bir şekilde çalışması için gereken erişimi sağlamanın yanı sıra kuruluşu tehditlere karşı korumanın temelini oluşturur.

[Azure AD Multi-Factor Authentication (MFA),](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) platformda yerleşiktir ve hassas finansal verilere ve uygulamalara erişirken kullanıcı kimliğini onaylamaya yardımcı olmak için ek bir kimlik doğrulaması kanıtı sağlar. Azure MFA için parola ve bilinen mobil cihaz gibi en az iki kimlik doğrulaması biçimi gerekir. Aşağıdakiler dahil olmak üzere birkaç ikinci faktörlü kimlik doğrulama seçeneğini destekler:

- Microsoft Authenticator uygulaması
- SMS ile teslim edilen tek seferlik geçiş kodu
- Kullanıcının PIN girmesi gereken telefon araması

Parola bir şekilde ele geçirilirse, potansiyel bir bilgisayar korsanı kuruluş verilerine erişmek için kullanıcının telefonuna ihtiyaç duymaya devam eder. Buna ek olarak, Microsoft 365 Modern Kimlik Doğrulama'yı önemli bir protokol olarak kullanır ve bu protokol, microsoft Outlook ve diğer Microsoft Office uygulamaları da dahil olmak üzere çalışanların her gün kullandığı işbirliği araçlarına web tarayıcılarından aynı güçlü ve zengin kimlik doğrulama deneyimini getirir.

#### <a name="passwordless"></a>Parolasız

Parolalar, güvenlik zincirindeki en zayıf bağlantıdır. Ek doğrulama yapılmazsa tek bir hata noktası olabilir. Microsoft, finans kurumlarının gereksinimlerine uygun çok çeşitli kimlik doğrulama seçeneklerini destekler.

*Parolasız* yöntemler, MFA'nın kullanıcılar için daha kullanışlı hale getirmesini sağlar. Tüm MFA parolasız olmasa da, parolasız teknolojiler çok faktörlü kimlik doğrulamasını devreye alır. Microsoft, Google ve diğer sektör liderleri, Fast IDentity Online (FIDO) adlı bir grupta web ve mobil cihazlarda daha basit, daha güçlü bir kimlik doğrulama deneyimi sağlamak için standartlar geliştirmiştir. Yakın zamanda geliştirilen FIDO2 standardı, kullanıcıların kimlik avının ortadan kaldırılması için parola gerektirmeden kolayca ve güvenli bir şekilde kimlik doğrulamasına olanak tanır.

Parolasız Microsoft MFA yöntemleri şunlardır:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): Esneklik, kolaylık ve maliyet için Microsoft Authenticator mobil uygulamasını kullanmanızı öneririz. Microsoft Authenticator, Azure AD'ye bağlı tüm uygulamalar için biyometriyi, anında iletme bildirimlerini ve tek seferlik geçiş kodlarını destekler. Apple ve Android uygulama mağazalarından edinilebilir.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): Bilgisayarda yerleşik bir deneyim için Windows Hello kullanmanızı öneririz. Otomatik olarak oturum açmak için biyometrik bilgileri (yüz veya parmak izi gibi) kullanır.  
* [FIDO2 Güvenlik anahtarları](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) artık birkaç Microsoft iş ortağı tarafından kullanılabilir: USB, NFC özellikli rozet veya biyometrik anahtarda Yubico, Feitian Technologies ve HID Global.

[Azure AD Koşullu Erişim](/azure/active-directory/conditional-access/) , erişim denetimi kararlarını otomatikleştirmek ve şirket varlıklarını korumak için kuruluş ilkelerini zorlamak için sağlam bir çözüm sağlar. Klasik bir örnek, finansal planlayıcının hassas müşteri verilerine sahip bir uygulamaya erişmek istemesidir. Bu uygulamalara özel olarak erişmek için çok faktörlü kimlik doğrulaması gerçekleştirmek için otomatik olarak gereklidir ve erişimin şirket tarafından yönetilen bir cihazdan yapılması gerekir. Azure Koşullu Erişim, kullanıcının erişim isteği hakkında kullanıcı, cihaz, konum ve ağ özellikleri ve kullanıcının erişmeye çalıştığı uygulama gibi sinyalleri bir araya getirir. Yapılandırılan ilkelere göre uygulamaya erişme girişimlerini dinamik olarak değerlendirir. Kullanıcı veya cihaz riski yükseltilmişse veya başka koşullar karşılanmazsa, Azure AD MFA gerektirme, güvenli parola sıfırlaması gerektirme veya erişimi kısıtlama veya engelleme gibi ilkeleri otomatik olarak zorunlu kılabilir. Bu, hassas kuruluş varlıklarının dinamik olarak değişen ortamlarda korunmasına yardımcı olur.
 
Azure AD ve ilgili Microsoft 365 güvenlik hizmetleri, verilere ve uygulamalara erişimin güvence altına alınabilmesi ve mevzuat uyumluluğu yükümlülüklerinin karşılanabilmesi için modern bir bulut işbirliği platformunun finansal kurumlara dağıtılabildiği temeli sağlar. Bu araçlar aşağıdaki temel özellikleri sağlar:

* Kullanıcı kimliklerini merkezi olarak depolayın ve güvenli bir şekilde yönetin.
* Erişim isteklerinde kullanıcıların kimliğini doğrulamak ve tüm uygulamalarda tutarlı ve sağlam bir kimlik doğrulaması deneyimi sağlamak için çok faktörlü kimlik doğrulaması da dahil olmak üzere güçlü bir kimlik doğrulama protokolü kullanın.
* Kimlik, kullanıcı/grup üyeliği, uygulama, cihaz, ağ, konum ve gerçek zamanlı risk puanı dahil olmak üzere ilke karar alma sürecine birden çok sinyal ekleyerek tüm erişim isteklerinde ilkeleri dinamik olarak doğrulayın.
* Kullanıcı davranışına ve dosya özelliklerine göre ayrıntılı ilkeleri doğrulayın ve gerektiğinde ek güvenlik önlemlerini dinamik olarak zorunlu kılın.
* Kuruluştaki "gölge BT"yi belirleyin ve InfoSec ekiplerinin bulut uygulamalarını tasdik etmelerine veya engellemelerine izin verin.
* Microsoft ve Microsoft dışı bulut uygulamalarına erişimi izleme ve denetleme.
* E-posta kimlik avı ve fidye yazılımı saldırılarına karşı proaktif olarak koruma.

#### <a name="azure-ad-identity-protection"></a>Azure AD Kimlik Koruması
Koşullu Erişim kaynakları şüpheli isteklerden korurken, Kimlik Koruması şüpheli kullanıcı hesaplarının sürekli risk algılama ve düzeltmesini sağlayarak daha da ileri gider. Kimlik Koruması, ortamınızdaki şüpheli kullanıcı ve oturum açma davranışı hakkında 24 saat bilgi sahibi olmanıza neden olur. Otomatik yanıtı, güvenliği aşılmış kimliklerin kötüye kullanılmasına proaktif olarak engel olur.
 
Kimlik Koruması, kuruluşların üç temel görevi yerine getirmesine olanak tanıyan bir araçtır:

* Kimlik tabanlı risklerin algılanması ve düzeltilmesi için otomatikleştirme.
* Portaldaki verileri kullanarak riskleri araştırın.
* Daha fazla analiz için risk algılama verilerini üçüncü taraf yardımcı programlara aktarın.

Kimlik Koruması, Kullanıcılarınızı korumak için Microsoft'un Azure AD'ye sahip kuruluşlardaki, Microsoft Hesapları ile tüketici alanında ve Xbox ile oyun oynamadaki konumundan edindiği bilgileri kullanır. Microsoft, müşterileri belirlemek ve tehditlere karşı korumak için günde 65 trilyon sinyal analiz eder. Tarafından oluşturulan ve Kimlik Koruması'na beslenen sinyaller, erişim kararları almak için Koşullu Erişim gibi araçlara daha fazla aktarılabilir. Ayrıca kuruluşunuzun zorlanan ilkelerine göre daha fazla araştırma yapmak için bir güvenlik bilgileri ve olay yönetimi (SIEM) aracına geri beslenebilirler.

Kimlik Koruması, kuruluşların Microsoft ekosistemi genelinde buluşsal yöntemler, kullanıcı ve varlık davranış analizi (UEBA) ve makine öğrenmesi (ML) temelinde gelişmiş algılama ile desteklenen bulut zekası avantajlarından yararlanarak kimlik güvenliğinin aşılmasına karşı otomatik olarak korunmasına yardımcı olur.

![Beş bilgi çalışanı bir diğerini izlerken sunum yapıyor.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Hassas verileri tanımlama ve veri kaybını önleme
Microsoft 365, aşağıdakiler dahil olmak üzere güçlü özelliklerin bir birleşimiyle tüm kuruluşların kuruluş içindeki hassas verileri tanımlamasına olanak tanır:

* **Microsoft Purview,** hem kullanıcı tabanlı sınıflandırma hem de hassas verilerin otomatik sınıflandırması için Information Protection.
* Hassas veri türlerini (başka bir deyişle, normal ifadeler) ve anahtar sözcükleri ve ilke zorlamayı kullanarak hassas verilerin otomatik olarak tanımlanması için **Microsoft Purview Veri Kaybı Önleme (DLP**).

**[Microsoft Purview Information Protection](../compliance/information-protection.md)** kuruluşların duyarlılık etiketlerini kullanarak belgeleri ve e-postaları akıllı bir şekilde sınıflandırmasına olanak tanır. Duyarlılık etiketleri kullanıcılar tarafından Microsoft Office uygulamalarındaki belgelere ve Outlook'daki e-postalara el ile uygulanabilir. Etiketler belge işaretlerini, şifreleme yoluyla korumayı ve hak yönetimi zorlamasını otomatik olarak uygulayabilir. Hassas verileri otomatik olarak bulmak ve sınıflandırmak için anahtar sözcükleri ve hassas veri türlerini (kredi kartı numaraları, sosyal sigorta numaraları ve kimlik numaraları gibi) kullanan ilkeler yapılandırılarak duyarlılık etiketleri de otomatik olarak uygulanabilir.

Ayrıca Microsoft, yalnızca desen eşleştirmesi veya içerik içindeki öğelerle değil, içeriğe dayalı hassas verileri tanımlamak için makine öğrenmesi modellerini kullanan "eğitilebilir sınıflandırıcılar" sağlar. Sınıflandırıcı, sınıflandırılacak içeriğin çok sayıda örneğine bakarak bir içerik türünü tanımlamayı öğrenir. Sınıflandırıcıyı eğitin, belirli bir kategorideki içerik örnekleri vererek başlar. Bu örneklerden öğrendikten sonra model, eşleşen ve eşleşmeyen örneklerin bir karışımı verilerek test edilir. Sınıflandırıcı, belirli bir örneğin kategoriye girip girmediğini tahmin eder. Ardından bir kişi sonuçları doğrular, sınıflandırıcının tahminlerinin doğruluğunu artırmaya yardımcı olmak için pozitifleri, negatifleri, hatalı pozitifleri ve hatalı negatifleri sıralar. Eğitilen sınıflandırıcı yayımlandığında içeriği Microsoft Office SharePoint Online, Exchange Online ve OneDrive İş işler ve içeriği otomatik olarak sınıflandırır.

Belgelere ve e-postalara duyarlılık etiketleri uygulamak, nesne içinde seçilen duyarlılığı tanımlayan meta verileri ekler. Duyarlılık daha sonra verilerle birlikte hareket eder. Bu nedenle, etiketli bir belge kullanıcının masaüstünde veya şirket içi bir sistemde depolanmış olsa bile, yine de korunur. Bu işlevsellik, Microsoft Defender for Cloud Apps veya ağ uç cihazları gibi diğer Microsoft 365 çözümlerinin hassas verileri tanımlamasını ve güvenlik denetimlerini otomatik olarak zorunlu kılmasını sağlar. Duyarlılık etiketleri, çalışanları bir kuruluştaki hangi verilerin hassas olarak kabul edildiği ve verileri aldığında nasıl işleyecekleri konusunda eğitmek için ek avantaj sağlar.

**[Microsoft Purview Veri Kaybı Önleme (DLP),](../compliance/dlp-learn-about-dlp.md)** hassas veriler içeren belgeleri, e-postaları ve konuşmaları hassas veriler için tarayarak ve ardından bu nesneler üzerinde ilkeyi zorunlu kılarak otomatik olarak tanımlar. İlkeler, SharePoint ve OneDrive İş belgelerde uygulanır. Kullanıcılar e-posta gönderdiğinde ve Teams sohbetlerde ve kanal konuşmalarında da uygulanır. İlkeler anahtar sözcükleri, hassas veri türlerini, bekletme etiketlerini ve verilerin kuruluş içinde mi yoksa dışarıdan mı paylaşıldığını aramak için yapılandırılabilir. Kuruluşların hatalı pozitif sonuçları azaltmak için DLP ilkelerine ince ayar yapmalarına yardımcı olmak için denetimler sağlanır. Hassas veriler bulunduğunda, Microsoft 365 uygulamalarındaki kullanıcılara içeriklerinin hassas veriler içerdiğini bildirmek ve ardından düzeltici eylemler önermek için özelleştirilebilir ilke ipuçları görüntülenebilir. İlkeler ayrıca kullanıcıların belgelere erişmesini, belgeleri paylaşmasını veya belirli türde hassas veri içeren e-postalar göndermesini engelleyebilir. Microsoft 365 100'den fazla yerleşik hassas veri türünü destekler. Kuruluşlar özel hassas veri türlerini ilkelerine uyacak şekilde yapılandırabilir.

Microsoft Purview Information Protection ve DLP ilkelerinin kuruluşlara dağıtılması, çalışanların kuruluşun veri sınıflandırma şemasını ve hangi veri türlerinin hassas kabul edildiğini anlaması için dikkatli bir planlama ve kullanıcı eğitim programı gerektirir. Çalışanlara hassas verileri tanımlamalarına ve bunların nasıl işlendiğini anlamalarına yardımcı olacak araçlar ve eğitim programları sağlamak, onları bilgi güvenliği risklerini azaltmaya yönelik çözümün bir parçası haline getirir.

Tarafından oluşturulan ve Kimlik Koruması'na beslenen sinyaller, erişim kararları almak için Koşullu Erişim gibi araçlara veya kuruluşun zorunlu ilkelerine göre araştırma için bir güvenlik bilgileri ve olay yönetimi (SIEM) aracına da beslenebilir.

Kimlik Koruması, kuruluşların buluşsal yöntemler, kullanıcı ve varlık davranışı analizi ve Microsoft ekosistemi genelinde makine öğrenmesi tabanlı gelişmiş algılamalar tarafından desteklenen bulut zekasının avantajlarından yararlanarak kimlik güvenliğinin aşılmasına karşı otomatik olarak korunmasına yardımcı olur.

![Bir bilgi çalışanı, çok sayıda izleyicinin önünde resmedilir.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Kaleyi savun

Microsoft kısa süre önce modern kuruluşun gelişen tehdit ortamına karşı güvenliğini sağlamak için tasarlanan Microsoft 365 Defender çözümünü kullanıma sundu. Tehdit Koruması çözümü, Akıllı Güvenlik Graph yararlanarak birden çok saldırı vektörlerine karşı kapsamlı, tümleşik güvenlik sunar.

### <a name="the-intelligent-security-graph"></a>[Akıllı Güvenlik Graph](https://www.microsoft.com/security/business/intelligence) 
Microsoft 365 güvenlik hizmetleri, Akıllı Güvenlik Graph tarafından desteklenir. Akıllı Güvenlik Graph, siber tehditlerle mücadele etmek için Microsoft ve iş ortaklarından gelen tehdit bilgilerini ve güvenlik sinyallerini bağlamak için gelişmiş analiz kullanır. Microsoft, yığın genelinde güç koruma katmanları oluşturan trilyonlarca güvenlik sinyali toplayarak büyük ölçekte küresel hizmetler yürütmektedir. Makine öğrenmesi modelleri bu zekayı değerlendirir ve sinyal ve tehdit içgörüleri ürünlerimiz ve hizmetlerimiz arasında yaygın olarak paylaşılır. Bu, tehditleri hızla algılayıp yanıtlamamıza ve müşterilere düzeltme için eyleme dönüştürülebilir uyarılar ve bilgiler getirmemize olanak tanır. Makine öğrenmesi modellerimiz sürekli olarak eğitilir ve yeni içgörülerle güncelleştirilerek daha güvenli ürünler oluşturmamıza ve daha proaktif güvenlik sağlamamıza yardımcı olur.

[Office 365 için Microsoft Defender](../security/office-365-security/defender-for-office-365.md), kuruluşları e-posta ve Office belgeleri aracılığıyla gönderilen kötü amaçlı bağlantılara ve kötü amaçlı yazılımlara karşı koruyan tümleşik bir Microsoft 365 hizmeti sağlar. Kullanıcıları etkileyen en yaygın saldırı vektörlerinden biri e-posta kimlik avı saldırılarıdır. Bu saldırılar belirli kullanıcıları hedef alabilir ve kullanıcıdan kötü amaçlı bir bağlantıya tıklamasını veya kötü amaçlı yazılım içeren bir eki açmasını isteyen bir eylem çağrısı ile çok ikna edici olabilir. Bilgisayara bulaştıktan sonra, saldırgan kullanıcının kimlik bilgilerini çalabilir ve kuruluş genelinde ya da hassas bilgileri aramak için e-postaları ve verileri dışarı çıkarabilir. Office 365 için Defender, kötü amaçlı olabilecek belgeler ve bağlantıları tıklayarak değerlendirerek güvenli ekleri ve güvenli bağlantıları destekler ve erişimi engeller. E-posta ekleri, kullanıcının posta kutusuna teslim etmeden önce korumalı bir korumalı alanda açılır. Ayrıca, Office belgelerdeki bağlantıları kötü amaçlı URL'ler için değerlendirir. Office 365 için Defender ayrıca SharePoint Online, OneDrive İş ve Teams'daki bağlantıları ve dosyaları korur. Kötü amaçlı bir dosya algılanırsa, Office 365 için Defender olası hasarı azaltmak için bu dosyayı otomatik olarak kilitler.

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) önleyici koruma, ihlal sonrası algılama ve otomatik araştırma ve yanıt için birleşik bir uç nokta güvenlik platformudur. Uç Nokta için Defender, kurumsal uç noktalarda hassas verilerin bulunması ve korunması için yerleşik özellikler sağlar.

[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security), kuruluşların ilkeleri ayrıntılı düzeyde zorlamasına ve makine öğrenmesi kullanılarak otomatik olarak tanımlanan bireysel kullanıcı profillerine dayalı davranış anomalilerini algılamasına olanak tanır. Bulut için Defender Uygulamaları ilkeleri, erişilen belgelerin kullanıcı davranışı ve özellikleriyle ilgili ek sinyalleri değerlendirerek hassas şirket varlıklarını korumak için Azure Koşullu Erişim ilkeleri oluşturabilir. Zaman içinde Bulut için Defender Uygulamaları, erişen veriler ve kullandıkları uygulamalarla ilgili olarak her çalışan için tipik davranışı öğrenir. Öğrenilen davranış desenlerine bağlı olarak, bir çalışan bu davranış profilinin dışında hareket ederse ilkeler güvenlik denetimlerini otomatik olarak zorunlu kılabilir. Örneğin, bir çalışan genellikle pazartesiden cumaya kadar 09:00 ile 17:00 arasında bir muhasebe uygulamasına erişiyorsa ancak pazar akşamı bu uygulamaya yoğun bir şekilde erişmeye başlarsa, Bulut için Defender Uygulamalar kullanıcının yeniden kimlik doğrulamasını zorunlu kılmak için ilkeleri dinamik olarak zorunlu kılabilir. Bu, kullanıcının kimlik bilgilerinin gizliliğinin tehlikeye atılmasını sağlamaya yardımcı olur. Bulut için Defender Uygulamaları ayrıca kuruluştaki "gölge BT"nin tanımlanmasına yardımcı olabilir ve bu da bilgi güvenliği ekiplerinin çalışanların hassas verilerle çalışırken tasdikli araçlar kullanmasını sağlamasına yardımcı olur. Son olarak Bulut için Defender Uygulamalar, Microsoft 365 platformunun dışında bile Bulut'un herhangi bir yerinde hassas verileri koruyabilir. Kuruluşların erişimi denetleyerek ve kullanımı izleyerek belirli dış Bulut uygulamalarını tasdik etmesine (veya tasdikini kaldırmasına) olanak tanır.
 
[Kimlik için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) gelişmiş tehditleri, güvenliği aşılmış kimlikleri ve kuruluşunuza yönelik kötü amaçlı insider eylemlerini tanımlamak, algılamak ve araştırmak için şirket içi Active Directory sinyallerinizden yararlanan bulut tabanlı bir güvenlik çözümüdür. AATP, SecOp analistlerinin ve güvenlik uzmanlarının hibrit ortamlardaki gelişmiş saldırıları algılamasını sağlar:
* Öğrenme tabanlı analiz kullanarak kullanıcıları, varlık davranışını ve etkinlikleri izleyin.
* Active Directory'de depolanan kullanıcı kimliklerini ve kimlik bilgilerini koruma.
* Sonlandırma zinciri boyunca şüpheli kullanıcı etkinliklerini ve gelişmiş saldırıları belirleyin ve araştırın.
* Hızlı önceliklendirme için basit bir zaman çizelgesinde net olay bilgileri sağlayın.

![Ofis çalışanları küçük bir konferans odasında buluşur. Biri sunum yapıyor.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Verileri yönetme ve kayıtları yönetme

Finansal kurumlar, kurumsal saklama zamanlamalarında temsil edilen mevzuat, yasal ve iş yükümlülüklerine göre kayıt ve bilgilerini saklamalıdır. Örneğin SEC, kayıt türüne göre ilk iki yıl için hemen erişilebilir olacak şekilde üç ile altı yıllık [saklama sürelerini zorunlu tutun](https://www.sec.gov/rules/interp/34-47806.htm) . Kuruluşlar, veriler yetersiz tutulursa (çok erken atılırsa) yasal ve mevzuat uyumluluğu riskleriyle karşı karşıya kalır ve artık bilgi gerekmediğinde bertaraf edilmesini zorunlu hale getiren düzenlemeleri de yönetir. Etkili kayıt yönetimi stratejileri pratik ve tutarlı bir yaklaşımı vurgular, böylece bilgiler uygun şekilde atılırken kuruluş için maliyet ve risk en aza indirilir.
 
Buna ek olarak, New York Dışişleri Mali Hizmetler Bakanlığı'ndan gelen yasal düzenlemeler, kapsanan varlıkların, nonpublic olmayan bilgilerin elden çıkarılmasına yönelik politika ve yordamları sürdürmesini gerektirir. 23 NYCRR 500, Bölüm 500.13, Veri Saklamaya İlişkin Sınırlamalar, "Siber güvenlik programının bir parçası olarak, kapsanan her Varlık, iş operasyonları için veya Kapsanan Varlığın diğer meşru iş amaçları için artık gerekli olmayan bu Bölümün 500.01(g)(2)-(3) bölümünde tanımlanan herhangi bir Abonelik Dışı Bilgi temelinde düzenli aralıklarla güvenli elden çıkarma ilkeleri ve yordamları içermelidir,  aksi takdirde bu bilgilerin yasa veya düzenlemeyle saklanması gerekmesi dışında."
 
Finansal kurumlar büyük miktarlarda veriyi yönetir. Ayrıca sözleşmenin süresi dolan veya kuruluştan ayrılan bir çalışan gibi bazı saklama süreleri olaylar tarafından tetiklenir. Bu atmosferde kayıt saklama ilkelerini uygulamak zor olabilir. Kuruluş belgeleri arasında kayıt saklama dönemlerini doğru bir şekilde atama yaklaşımları farklılık gösterebilir. Bazıları saklama ilkelerini geniş bir şekilde uygular veya otomatik sınıflandırma ve makine öğrenmesi tekniklerinden yararlanabilir. Diğerleri, tek tek belgelere benzersiz olarak saklama dönemleri atayan daha ayrıntılı bir işlem gerektiren bir yaklaşımı tanımlar.

***Microsoft 365, kayıt yönetimi gereksinimlerini akıllı bir şekilde uygulamak için bekletme etiketleri ve ilkeleri tanımlamak için esnek özellikler sağlar.*** Kayıt yöneticisi, geleneksel bekletme zamanlamasında "kayıt türünü" temsil eden bir bekletme etiketi tanımlar. Bekletme etiketi şu ayrıntıları tanımlayan ayarları içerir:

- Kaydın ne kadar süreyle tutuldu
- Saklama süresi dolduğunda ne olur (belgeyi silin, bir değerlendirme gözden geçirmesi başlatın veya hiçbir işlem gerçekleştirmeyin)
-  Bekletme süresinin başlatılmasını tetikleyen (oluşturulma tarihi, son değiştirme tarihi, etiketli tarih veya olay) ve belgeyi veya e-postayı kayıt olarak işaretler (yani düzenlenemez veya silinemez)

Bekletme etiketleri daha sonra SharePoint veya OneDrive sitelerinde, Exchange posta kutularında ve Microsoft 365 gruplarında yayımlanır. Kullanıcılar bekletme etiketlerini belgelere ve e-postalara el ile uygulayabilir. Kayıt yöneticileri, etiketleri otomatik olarak uygulamak için zekayı kullanabilir. Akıllı özellikler [doksan artı yerleşik hassas bilgi türlerini](../compliance/content-search.md) (ABA çıkış numarası, ABD banka hesap numarası veya ABD Sosyal Güvenlik Numarası gibi) temel alabilir. Ayrıca, kredi kartı numaraları veya diğer kişisel bilgiler gibi belgelerde veya e-postalarda bulunan anahtar sözcüklere veya hassas verilere ya da SharePoint meta verilerine göre özelleştirilebilir. El ile veya otomatik desen eşleştirme yoluyla kolayca tanımlanamayan veriler için eğitilebilir sınıflandırıcılar, belgeleri makine öğrenmesi tekniklerine göre akıllı bir şekilde sınıflandırmak için kullanılabilir.
 
**Menkul Kıymetler ve Exchange Komisyonu (SEC),** aracı satıcıların ve diğer düzenlenmiş finansal kurumların işle ilgili tüm iletişimleri tutmasını gerektirir. Bu gereksinimler e-postalar, belgeler, anlık iletiler, fakslar ve daha fazlası gibi birçok iletişim ve veri türü için geçerlidir. **SEC kuralı 17a-4** , bu kuruluşların kayıtları elektronik veri depolama sisteminde depolamak için karşılaması gereken ölçütleri tanımlar. 2003 yılında SEC, bu gereksinimleri açıklığa kavuşturan bir yayın yayınladı. Aşağıdaki ölçütleri içeriyor:

* Elektronik depolama sistemi tarafından korunan veriler yeniden yazılamaz ve silinemez olmalıdır. Bu, WORM gereksinimi olarak adlandırılır (bir kez yazın, birçoğunu okuyun).
* Depolama sistemi, bir celp veya başka bir yasal emir olması durumunda verileri kuralın gerektirdiği saklama süresinin ötesinde depolayabilmelidir.
* Bir kuruluş, tümleşik donanım ve yazılım denetim kodlarını kullanarak gerekli saklama süresi boyunca kaydın üzerine yazılmasını, silinmesini veya başka bir şekilde değiştirilmesini engelleyen bir elektronik depolama sistemi kullandıysa kuralın (f)(2)(ii)(A) paragrafında yer alan gereksinimi ihlal etmez.
* Bir kaydın üzerine yazılması veya silinmesi riskini yalnızca "azaltan" elektronik depolama sistemleri, örneğin erişim denetimine bağlı olarak kuralın gereksinimlerini karşılamaz.

Finans kurumlarının SEC kuralı 17a-4'ün gereksinimlerini karşılamasına yardımcı olmak için Microsoft 365 verilerin nasıl korunacakları, ilkelerin yapılandırılması ve verilerin hizmet içinde depolanmasıyla ilgili özelliklerin bir bileşimini sağlar. Şunlar dahildir:

* **Verilerin korunması (Kural 17a-4(a), (b)(4))** – Bekletme etiketleri ve ilkeleri kuruluş gereksinimlerini karşılayacak şekilde esnektir ve farklı veri, belge ve bilgi türlerine otomatik olarak veya el ile uygulanabilir. SharePoint ve OneDrive İş belgeleri, Exchange Online posta kutularındaki veriler ve Teams'daki veriler de dahil olmak üzere çok çeşitli veri türleri ve iletişimler desteklenir.  
* **Yeniden yazılamaz, silinemez biçim (Kural 17a-4(f)(2)(ii)(A))** – Saklama ilkeleri için Koruma Kilidi özelliği, kayıt yöneticilerinin ve yöneticilerin artık değiştirilemeyecekleri şekilde bekletme ilkelerini kısıtlayıcı olacak şekilde yapılandırmalarına olanak tanır. Bu, herkesin bekletme ilkesini herhangi bir şekilde kaldırmasını, devre dışı bırakmasını veya değiştirmesini engeller. Başka bir deyişle, Koruma Kilidi etkinleştirildikten sonra devre dışı bırakılamaz ve bekletme ilkesinin uygulandığı herhangi bir verinin saklama süresi boyunca üzerine yazılabilmesi, değiştirilebileceği veya silinebileceği bir yöntem yoktur. Ayrıca saklama süresi kısaltılamaz. Ancak, verilerin saklamaya devam etmesi için yasal bir gereksinim olduğunda saklama süresi uzatılabilir.<br/><br/>Saklama ilkesine Koruma Kilidi uygulandığında, aşağıdaki eylemler kısıtlanır:

  - İlkenin saklama süresi yalnızca artırılabilir. Kısaltılamaz.
  - Kullanıcılar ilkeye eklenebilir, ancak ilkede yapılandırılan mevcut kullanıcılar kaldırılamaz.
   - Bekletme ilkesi, kuruluştaki herhangi bir yönetici tarafından silinemez.
 
  Koruma Kilidi, en yüksek ayrıcalıklı erişim düzeyine sahip yöneticilerin bile hiçbir kullanıcının ayarları değiştirebilmesini, değiştirebilmesini, üzerine yazabilmesini veya silebilmesine yardımcı olur ve sec 2003 Sürümünde sağlanan yönergelere uygun olarak Microsoft 365 arşivleme özelliğini getirir.

* **Verilerin depolanması/seri hale getirilmesi ve dizinlenmesi (Kural 17a-4(f)(2) (ii)(B) ve (C))** – Office 365 iş yüklerinin her biri depolama ortamında veri kaydetme işleminin kalitesini ve doğruluğunu otomatik olarak doğrulamaya yönelik özellikler içerir. Ayrıca veriler, verilerin etkili bir şekilde aranmasına ve alınmasına olanak sağlamak için yeterli dizin oluşturmayı sağlamak için meta veriler ve zaman damgaları kullanılarak depolanır.
 
* **Yinelenen kopyalar için ayrı depolama alanı (Kural 17a-4(f)(3(iii))** – Office 365 bulut hizmeti, verilerin yinelenen kopyalarını yüksek kullanılabilirliğinin temel bir yönü olarak depolar. Bu, tüm sunucularda fiziksel düzeyde, veri merkezi içindeki sunucu düzeyinde ve coğrafi olarak dağınık veri merkezleri için hizmet düzeyinde de dahil olmak üzere hizmetin tüm düzeylerinde yedeklilik uygulanarak gerçekleştirilir.

* **İndirilebilir ve erişilebilir veriler (Kural 17a-4(f)(2)(ii)(D))** – Office 365 genellikle saklama için etiketlenmiş verilerin yerinde aranmalarına, erişilmesine ve indirilmesine izin verir. Ayrıca yerleşik eBulma özellikleri kullanılarak Exchange Online Arşivlerindeki verilerin aranabilir olmasını sağlar. Daha sonra veriler EDRML ve PST gibi standart biçimlerde gerektiğinde indirilebilir.
 
* **Denetim gereksinimleri (Kural 17a-4(f)(3)(v))** – Office 365 veri nesnelerini değiştiren, bekletme ilkelerini yapılandıran veya değiştiren, eBulma aramaları yapan veya erişim izinlerini değiştiren her yönetim ve kullanıcı eylemi için denetim günlüğü sağlar. Office 365, bir eylemi kimin gerçekleştirdiği, ne zaman gerçekleştirildiği, eylemle ilgili ayrıntılar ve gerçekleştirilen komutlar gibi kapsamlı bir denetim kaydı tutar. Denetim günlüğü daha sonra çıktı olarak kullanılabilir ve gerektiğinde resmi denetim işlemlerinin bir parçası olarak dahil edilebilir.

Son olarak Kural 17a-4, kuruluşların iki yıl boyunca hemen erişilebilir olmaları için birçok işlem türünün kayıtlarını tutmasını gerektirir. Kayıtlar, hemen erişim olmadan üç-altı yıl daha saklanmalıdır. Yinelenen kayıtlar da aynı süre boyunca site dışında bir konumda tutulmalıdır. Microsoft 365 kayıt yönetimi özellikleri, kayıtların değiştirilmeyecek veya silinmeyecek ancak kayıt yöneticisi tarafından denetlenen bir süre boyunca kolayca erişilebilecek şekilde korunmasını sağlar. Bu dönemler, kuruluşun mevzuat uyumluluğu yükümlülüklerine bağlı olarak gün, ay veya yıllara yayılabilir.
 
Talep üzerine Microsoft, bir kuruluş tarafından gerekirse SEC 17a-4 ile uyumluluk kanıtlama mektubu sağlayacaktır.

Buna ek olarak, bu özellikler Microsoft 365 **Finansal Endüstri Düzenleme Kurumu'ndan** ABD **Emtia Vadeli İşlemleri Ticaret Komisyonu** ve [FINRA Kural Serisi 4510'dan](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) [CFTC Kural 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) için depolama gereksinimlerini karşılamaya yardımcı olur. Bu kurallar, finansal kurumların kayıtları tutması için genel olarak en açıklayıcı rehberi temsil eder.

Microsoft 365 SEC kuralı 17a-4 ve diğer düzenlemelerle nasıl uyumlu olduğuna ilişkin ek [ayrıntılara Cohasset Associates'in Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d)](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers) değerlendirmesi bölümünden ulaşabilirsiniz.

## <a name="establish-ethical-walls-with-information-barriers"></a>Bilgi engelleri olan etik duvarlar oluşturma

Finansal kurumlar, belirli rollerdeki çalışanların bilgi alışverişinde veya diğer rollerle işbirliği yapmasını engelleyen düzenlemelere tabi olabilir. Örneğin, FINRA'nın 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) ve (b)(2)(H)(iii) kurallarını yayımlayarak üyelerin şunları zorunlu kıldığını varsayalım:

"(G) araştırma analistlerinin, yatırım bankacılığı hizmetleri faaliyetlerinde bulunan kişiler veya satış ve ticaret personeli dahil olmak üzere, kendi kararlarına veya denetimlerine yanlı olabilecek diğer kişiler tarafından gözden geçirme, baskı veya gözetimden yalıtılmasını sağlamak için makul bir şekilde tasarlanmış bilgi engelleri veya diğer kurumsal korumalar oluşturun;" ve "(H) borç araştırma analistlerinin yalıtılmasını sağlamak için makul bir şekilde tasarlanmış bilgi engelleri veya diğer kurumsal korumalar oluşturun  (i) yatırım bankacılığı hizmetlerinde faaliyette bulunan kişilerin gözden geçirmesi, baskısı veya gözetimi; (ii) ana ticaret veya satış ve ticaret faaliyetleri; ve (iii) kararlarında veya denetimlerinde yanlı olabilecek diğer kişiler;"

Sonuç olarak, bu kurallar kuruluşların politikalar oluşturmasını ve bankacılık hizmetleri, satış veya analistlerle bilgi ve iletişim alışverişinde bulunan roller arasında bilgi engelleri uygulamalarını gerektirir.

[Bilgi engelleri](../compliance/information-barriers.md), Office 365 ortamınızda etik duvarlar oluşturarak uyumluluk yöneticilerinin veya diğer yetkili yöneticilerin Teams kullanıcı grupları arasında iletişime izin veren veya engelleyen ilkeler tanımlamasına olanak tanır. Bilgi engelleri, yetkisiz iletişimi önlemek için belirli eylemler üzerinde denetimler gerçekleştirir. Bilgi engelleri ayrıca şirket içi ekiplerin birleştirmeler/devralmalar veya hassas anlaşmalar üzerinde çalıştığı ya da yoğun şekilde kısıtlanması gereken hassas iç bilgilerle çalıştığı senaryolarda iletişimi kısıtlayabilir.

Bilgi engelleri, Teams konuşmaları ve dosyaları destekler. FINRA düzenlemelerine uymaya yardımcı olmak için aşağıdaki iletişimle ilgili eylem türlerini önleyebilirler:

* Kullanıcı arama
* Ekiliğe üye ekleme veya ekipteki başka bir üyeyle katılmaya devam etme
* Sohbet oturumu başlatma veya devam edin
* Grup sohbeti başlatma veya devam edin
* Bir kişiyi toplantıya katılmaya davet etme
* Ekran paylaşma
* Arama gerçekleştirin

## <a name="implement-supervisory-control"></a>Denetim denetimi uygulama

Finansal kurumlar genellikle kuruluşların içinde çalışanların etkinliklerini izlemek ve ilgili menkul kıymet yasalarına uyum sağlamasına yardımcı olmak için bir denetim işlevi kurmak ve sürdürmek için gereklidir. Özellikle, FINRA şu denetim gereksinimlerini belirlemiştir:
 
* [FINRA Kural 3110 (Denetim),](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) firmaların çalışanlarının ve faaliyette bulunduğu işletme türlerinin faaliyetlerini denetlemek için yazılı denetim prosedürlerine (WSP) sahip olmasını gerektirir. Diğer gereksinimlere ek olarak, yordamlar şunları içermelidir:
   - Denetim personelinin denetimi
   - Bir firmanın yatırım bankacılığı, menkul kıymetler işletmesi, iç iletişim ve iç soruşturmalarının gözden geçirilmesi
   - Insider ticareti için işlemlerin gözden geçirilmesi
   - Yazışmaların ve şikayetlerin gözden geçirilmesi

   Yordamlar incelemelerden, her bir kişinin gerçekleştireceği denetim etkinliğinden, gözden geçirme sıklığından ve gözden geçirilecek belge veya iletişim türlerinden sorumlu olan bireyleri açıklamalıdır.
 
* [FINRA Kural 3120 (Gözetmen Denetim Sistemi),](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) firmaların, Kural 3110 tarafından tanımlanan yazılı denetim prosedürlerini doğrulayan bir denetim denetim ilkeleri ve prosedürleri sistemine (SCP) sahip olmasını gerektirir. Firmaların yalnızca WSP'lere sahip olmaları değil, aynı zamanda geçerli menkul kıymet yasalarına ve düzenlemelerine uyum sağlama becerilerini doğrulamak için bu prosedürleri yıllık olarak test eden politikalara sahip olmaları gerekir. Test kapsamını tanımlamak için risk tabanlı yöntemler ve örnekleme kullanılabilir. Diğer gereksinimlerin yanı sıra, bu kural firmaların üst yönetime test sonuçlarının özetini ve test sonuçlarına yanıt olarak önemli istisnaları veya değiştirilmiş yordamları içeren yıllık bir rapor sağlamasını gerektirir.

![Bir ofis çalışanı bir grafiği ve tabloları ekranda görüntülerken, diğerleri arka planda buluşur.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>İletişim uyumluluğu

İletişim uyumluluğu, kuruluşların yetkili gözetmenler tarafından izleme ve gözden geçirme amacıyla çalışan iletişimlerini yakalamak üzere ilkeleri önceden yapılandırmalarına olanak tanır. İletişim uyumluluğundaki ilkeler iç/dış e-posta ve ekleri, sohbet ve kanal iletişimlerini Teams ve Çevrimiçi sohbet iletişimlerini ve eklerini Skype Kurumsal. Ayrıca, iletişim uyumluluğu üçüncü taraf hizmetlerden (Bloomberg, Thomson Reuters, LinkedIn, Twitter, Facebook, Box ve Dropbox gibi) iletişim ve verileri alabilir.
Bir kuruluş içinde yakalanıp gözden geçirilebilen iletişimin kapsamlı yapısı ve ilkelerin yapılandırılabildiği kapsamlı koşullar, finans kurumlarının FINRA Kural 3110'a uymasına yardımcı olmak için iletişim uyumluluk ilkelerine olanak sağlar. İlkeler, kişilerin veya grupların iletişimlerini gözden geçirmek üzere yapılandırılabilir.  Atanan gözetmenler bireysel veya grup düzeyinde atanabilir. Gelen veya giden iletileri, etki alanlarını, bekletme etiketlerini, anahtar sözcükleri veya tümcecikleri, anahtar sözcük sözlüklerini, hassas veri türlerini, ekleri, ileti boyutunu veya ek boyutunu temel alan iletişimleri yakalamak için kapsamlı koşullar yapılandırılabilir. Gözden geçirenler, bayraklı iletişimleri gözden geçirebilecekleri, ilkeleri ihlal etme olasılığı olan iletişimler üzerinde işlem yapabilecekleri ve bayrak eklenmiş öğeleri çözümlendi olarak işaretleyebilecekleri bir pano alır. Ayrıca incelemelerin ve daha önce çözümlenmiş olan öğelerin sonuçlarını da gözden geçirebilirler.
  
İletişim uyumluluğu, ilke gözden geçirme etkinliklerinin ilkeye ve gözden geçirene göre denetlenebilmesini sağlayan raporlar sağlar. Raporlar, ilkelerin kuruluşun yazılı denetim ilkeleri tarafından tanımlandığı şekilde çalıştığını doğrulamak için kullanılabilir. Bunlar, gözden geçirme gerektiren ve şirket ilkesiyle uyumlu olmayan iletişimleri tanımlamak için de kullanılabilir. Son olarak, ilkeleri yapılandırma ve iletişimleri gözden geçirmeyle ilgili tüm etkinlikler birleşik Office 365 denetim günlüğünde denetlenir. Sonuç olarak, iletişim uyumluluğu finans kurumlarının FINRA Kural 3120'ye uymasına da yardımcı olur.

İletişim uyumluluğu, FINRA kurallarına uymanın yanı sıra kuruluşların diğer yasal gereksinimlere, şirket ilkelerine ve etik standartlara uyum için iletişimleri izlemesine olanak tanır. İletişim uyumluluğu, iletişimleri gözden geçirirken hatalı pozitif sonuçları azaltmaya yardımcı olan yerleşik tehdit, taciz ve küfür sınıflandırıcıları sağlar ve inceleme ve düzeltme işlemi sırasında gözden geçirenlere zaman kazandırır. Ayrıca kuruluşların birleşmeler, devralmalar veya liderlik değişiklikleri gibi hassas değişikliklere uğradıklarında iletişimleri izleyerek riski azaltmalarına da olanak tanır.

![Bilgi çalışanı ekrana odaklanır.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Veri sızdırma ve şirket içi risklere karşı koruma

Kuruluşlar için yaygın bir tehdit, veri sızdırma veya bir kuruluştan veri ayıklama eylemidir. Bu risk, her gün erişilebilen bilgilerin hassas doğası nedeniyle finansal kurumlar için önemli bir endişe kaynağı olabilir. Kullanılabilir iletişim kanalı sayısının artması ve verilerin taşınmasına yönelik araçların yaygınlaşmasıyla birlikte, veri sızıntıları, ilke ihlalleri ve iç risk risklerinin risklerini azaltmak için genellikle gelişmiş özellikler gerekir.

### <a name="insider-risk-management"></a>İçeriden risk yönetimi

Çalışanların doğası gereği her yerden erişilebilen çevrimiçi işbirliği araçlarıyla etkinleştirilmesi kuruluşa risk getirir. Çalışanlar yanlışlıkla veya kötü amaçlı olarak saldırganlara veya rakiplere veri sızdırabilir.  Alternatif olarak, kişisel kullanım için verileri dışarı aktarabilir veya verileri gelecekteki bir işverene götürebilirler. Bu senaryolar, finansal hizmet kurumları için hem güvenlik hem de uyumluluk açısından ciddi riskler sunar. Bu riskleri ortaya çıktığında belirlemek ve bunları hızla azaltmak için hem veri toplamaya yönelik akıllı araçlar hem de yasal, insan kaynakları ve bilgi güvenliği gibi departmanlar arasında işbirliği gerekir.

Microsoft 365 yakın zamanda, Microsoft 365 hizmetlerindeki sinyalleri ilişkilendiren ve gizli desenler ve iç risk işaretleri için kullanıcı davranışını analiz etmek için makine öğrenmesi modellerini kullanan bir insider risk yönetimi çözümü başlattı. Bu araç, önceden belirlenmiş iş akışlarına göre servis taleplerini kolayca düzeltebilmeleri için güvenlik operasyonları, dahili araştırmacılar ve İk arasında işbirliğine olanak tanır.  

Örneğin, insider risk yönetimi bir kullanıcının Windows 10 masaüstünden gelen, dosyaları USB sürücüsüne kopyalama veya kişisel e-posta hesabına e-posta gönderme gibi sinyalleri, Office 365 e-posta, SharePoint Online, Microsoft Teams veya çevrimiçi hizmetler etkinlikleriyle ilişkilendirebilir veri sızdırma desenlerini tanımlamak için OneDrive İş. Ayrıca bu etkinlikleri, ortak bir veri sızdırma düzeni olan bir kuruluşta çalışanlarla ilişkilendirebilir. Zaman içinde birden çok etkinliği ve davranışı izleyebilir. Yaygın desenler ortaya çıktığında uyarılar oluşturabilir ve araştırmacıların ilke ihlalini yüksek düzeyde güvenle doğrulamak için önemli etkinliklere odaklanmasına yardımcı olabilir. Insider risk yönetimi, veri gizliliği düzenlemelerini karşılamaya yardımcı olmak için araştırmacıların verilerini anonim hale getirirken, araştırmalarını verimli bir şekilde gerçekleştirmelerine yardımcı olan önemli etkinliklere de göz atabilir. Araştırmacıların önemli etkinlik verilerini İk ve hukuk departmanlarına paketlemesine ve güvenli bir şekilde göndermesine olanak tanır ve düzeltme eylemine yönelik vakaların oluşturulmasına yönelik yaygın yükseltme iş akışlarını takip eder.

Insider risk yönetimi, kuruluşların iç riskleri izleme ve araştırma özelliklerini önemli ölçüde artırırken, kuruluşların veri gizliliği düzenlemelerini karşılamasına ve vakalar daha üst düzey eylem gerektirdiğinde yerleşik yükseltme yollarını izlemesine olanak sağlar. Insider risk yönetimi hakkında daha fazla bilgi için bkz. [Modern risk sorun noktaları ve Insider risk yönetiminde iş akışı](../compliance/insider-risk-management.md).

![Bir ekranı görüntülerken bir bölme türündeki bir çağrı merkezi çalışanı.](../media/clo17-call-center-006.jpg)

### <a name="tenant-restrictions"></a>Kiracı kısıtlamaları

Hassas verilerle ilgilenen ve güvenliğe sıkı bir önem veren kuruluşlar genellikle kullanıcıların erişebileceği çevrimiçi kaynakları denetlemek ister. Aynı zamanda, Office 365 gibi çevrimiçi hizmetler aracılığıyla güvenli işbirliği sağlamak istiyorlar. Sonuç olarak, şirket dışındaki Office 365 ortamları şirket cihazlarından kötü amaçlı veya yanlışlıkla veri sızdırmak için kullanılabildiğinden, kullanıcıların erişebileceği Office 365 ortamlarını denetlemek zor bir durum haline gelir. Geleneksel olarak kuruluşlar, kullanıcıların kurumsal cihazlardan erişebileceği etki alanlarını veya IP adreslerini kısıtlar. Ancak bu, kullanıcıların Office 365 hizmetlerine yasal olarak erişmesi gereken bulut öncelikli bir dünyada çalışmaz.

Microsoft 365, kiracı [kısıtlamalarına](/azure/active-directory/manage-apps/tenant-restrictions) bu sınamayı giderme olanağı sağlar. Kiracı kısıtlamaları, dolandırıcı kimlikler (şirket dizininizin parçası olmayan kimlikler) kullanarak çalışanların dış Office 365 kurumsal kiracılara erişimini kısıtlamak için yapılandırılabilir. Bugün kiracı kısıtlamaları kiracı genelinde geçerli olur ve bu sayede yalnızca yapılandırdığınız listede görünen kiracılara erişim sağlanır. Microsoft, denetimin ayrıntı düzeyini artırmak ve sağladığı korumaları geliştirmek için bu çözümü geliştirmeye devam etmektedir.

![GRAFİK.](../media/clo1717-corporate-office-001.jpg)

## <a name="conclusion"></a>Sonuç

Microsoft 365 ve Teams, finansal hizmetler şirketleri için tümleşik ve kapsamlı bir çözüm sunarak kuruluş genelinde basit ama güçlü bulut tabanlı işbirliği ve iletişim özellikleri sağlar. Kurumlar, Microsoft 365 güvenlik ve uyumluluk teknolojilerini kullanarak verileri, kimlikleri, cihazları ve uygulamaları siber güvenlik ve iç riskler gibi çeşitli operasyonel risklerden korumak için sağlam güvenlik denetimleriyle daha güvenli ve uyumlu bir şekilde çalışabilir. Microsoft 365, finansal hizmet kuruluşlarının şirketlerini, çalışanlarını ve müşterilerini korurken daha fazlasını başarabileceği temelden güvenli bir platform sağlar.
