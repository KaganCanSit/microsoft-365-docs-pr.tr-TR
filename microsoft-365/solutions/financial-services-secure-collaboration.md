---
title: ABD bankacılık ve büyük pazarları için uyumluluk ve güvenlikle ilgili önemli noktalar
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
description: Finansal hizmet kuruluşlarının güvenlik uyumluluğunu koruma ve güvenlik uyumluluğu koruma ile birlikte çalışma hakkında bilgi Microsoft 365 birlikte Teams.
f1.keywords: NOCSH
ms.openlocfilehash: e94ad0e1f7b6f0c8b76f40b6492f69b23655855c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015225"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>ABD bankacılık ve büyük pazarları için uyumluluk ve güvenlikle ilgili önemli noktalar

## <a name="introduction"></a>Giriş
Finansal hizmetler kuruluşları sıkı güvenlik, uyumluluk ve yönetim denetimleri taleplerine bağlı olarak neredeyse tüm ticari işletmeleri aşacaktır. Veriler, kimlikler, cihazlar ve uygulamaların korunması yalnızca işletmeleri için kritik önem sağlamakla birlikte, ABD Menkul Değer Ve Exchange Komisyonu (SEC), Mali Sektör Düzenleyici Dairesi (FINRA), Federal Mali Kurumlar Genel Kurulu (FFIEC) ve Commodity Futures Ticaret Komisyonu (CFTC) gibi yasal düzenlemelere bağlılık gereksinimlerine ve yönergelerine de tabi olur. Buna ek olarak, mali kurumlar 2002 Mali Dodd-Frank ve Sarbanes-Oxley yasalarına tabidir.

Günümüzde daha yüksek güvenlik endişesi, insider risk kaygıları ve genel veri ihlalleri konusunda müşteriler de kişisel verilerine ve banka varlıklarına güven içinde olmak için finansal kuruluşlarından yüksek güvenlik düzeyleri talep ediyor.

Geçmişten bu kadar süre sonra, mali kuruluşların şirket içinde ve dışında işbirliğini etkinleştirmek için kullanabileceği IT sistemleri ve platformlarını doğrudan etkileyen ve kısıtlanmış kapsamlı denetimlere gerek vardır. Finansal hizmetler çalışanları, günümüzde kolayca benimsenen ve kullanımı kolay bir modern işbirliği platformuna ihtiyaç ihtiyaçmektedir. Ancak finansal hizmetler, kullanıcıları, ekipleri ve departmanları tehditlerden korumak için ilkeleri zorunlu alan güvenlik ve uyumluluk denetimleriyle kullanıcılar, ekipler ve departmanlar arasında işbirliği yapma esnekliğine sahip değildir.

Finansal hizmet sektöründe, işbirliği araçlarının ve güvenlik denetimlerinin yapılandırması ve dağıtımı konusunda dikkatli bir şekilde göz önünde bulundurulması gerekir:
- Ortak kurumsal işbirliği ve iş süreci senaryolarının risk değerlendirmesi
- Bilgi koruması ve veri idaresi gereksinimleri
- Siber güvenlik ve insider tehditleri
- Yasal düzenlemelere uyumluluk gereksinimleri
- Diğer işlem riskleri

**Microsoft 365, finansal hizmet kuruluşlarının karşı karşıya kaldığı sorunları aşacak modern bir çalışma alanı bulut ortamıdır. Kuruluş genelinde güvenli ve esnek işbirliği, denetimler ve ilke zorlaması ile bir araya yasal uyumluluk çerçevelerine bağlı kalın.** Bu makalede, Microsoft 365 platformu finansal hizmetlerin modern bir işbirliği platformuna taşınarak verilerin ve sistemlerin güvenli ve yasal düzenlemelere uyumlu durumda tutmaya nasıl yardımcı olduğu açıklanmıştır:

* Yönetim yönetim ve eğitim olanaklarını kullanarak kuruluş ve Microsoft 365 üretkenliğini Microsoft Teams
* Destek'i kullanarak modern işbirliğini Microsoft 365 
* Hassas verileri tanımlama ve veri kaybını önleme
* Hisarları savunma
* Kayıtları etkili bir şekilde yöneterek verileri yönetme ve düzenlemelere uyma
* Bilgi engelleriyle duvarlara evriz olma
* Veri sızıntılarına ve insider risklerine karşı koruma

Bir Microsoft iş ortağı olarak Protiviti bu makaleye katkıda bulundu ve bu makaleye önemli geri bildirimler sağladı.

Aşağıdaki indirilebilir çizimler bu makaleyi tamamlar. Woodgrove Bank ve Contoso, bu makalede açıklanan becerilerin finansal hizmetlerin genel yasal düzenleme gereksinimlerini karşılamak için nasıl uygulan uygulanalık olduğunu göstermek için kullanılır. Bu çizimleri kendi kullanımınız için uyarlamak sizin için özgürce olur. 

**Microsoft 365 koruma ve uyumluluk çizimlerini gösterir**

| Öğe | Açıklama |
|:-----|:-----|
|[![Model posteri: Microsoft 365 koruma ve uyumluluk özelliklerini içerir.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>İngilizce: [PDF olarak indirin](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [Dosya olarak Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japonca: [PDF olarak](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf) [Visio indirme](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)\|  <br/> Kasım 2020 güncelleştirildi|Şunları içerir: <ul><li>  Microsoft bilgi koruması ve veri kaybını önleme</li><li>Bekletme ilkeleri ve bekletme etiketleri </li><li>Bilgi engelleri</li><li>İletişim uyumluluğu</li><li>Insider riski</li><li>Üçüncü taraf veri alımı</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Kurumsal ve çalışan üretkenliğini, yönetim ve eğitim Microsoft 365 kullanarak Teams

İşbirliği normalde çeşitli iletişim biçimlerini, belgeleri/verileri depolayabilme ve bu verilere erişmeyi ve diğer uygulamaları gerektiğinde tümleştirebilmeyi gerektirir. Finansal hizmetlerde çalışan çalışanların normalde diğer departman veya ekiplerin üyeleriyle ve kimi zaman da dış varlıklarla işbirliği yapmaları ve iletişim kurmaları gerekir. Bu nedenle, silolar veya bilgi paylaşımını zorlaştıran sistemler kullanmak istenmeyen bir tercihtir. Bunun yerine, çalışanların güvenli bir şekilde ve kurumsal ilkeye göre bilgileri iletişim kurmasına, işbirliği kurmasına ve paylaşmasına olanak sağlayan platform ve uygulamalardan faydalanma tercih edilir.

Çalışanlara modern, bulut tabanlı bir işbirliği platformu sağlama, çalışanlara daha üretken hale getirin ve çevik yollarla çalışma yollarını bulmalarını sağlayan araçları seçerek tümleştirin. İş Teams denetimleri ve bilgi yönetimi ilkeleriyle birlikte kullanmak, iş gücünüzün etkili bir şekilde iletişim kurmasına ve işbirliği kurmasına yardımcı olabilir.

Teams bir işbirliği merkezi sağlar. Ortak girişimler ve projeler üzerinde verimli bir şekilde çalışmak için insanları bir araya getirmeye yardımcı olur. Teams, ekip üyelerinin bire bir ve çok taraflı sohbet konuşmaları yapmalarına, belgeler üzerinde işbirliği yapmalarına ve belgeleri birlikte kullanmalarına, dosyaları depolamalarına ve paylaşmalarına olanak sağlar. Teams ayrıca tümleşik kurumsal ses ve görüntü ile çevrimiçi toplantıları da kolaylaştırır. Teams ayrıca Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI ve üçüncü taraf iş hattı uygulamaları gibi Microsoft uygulamalarıyla da özelleştirilebilir. Teams ekip üyeleri ve ekip kanallarına katılarak sohbet konuşmalarına katılan, depolanan dosyalara erişen ve diğer uygulamalardan yararlanan izin verilen dış kullanıcıların kullanımına uygun şekilde tasarlanmıştır

Her Microsoft Team bir grup Microsoft 365 destekleni. Bu grup, çeşitli hizmetler ve hizmetler (örneğin, Office 365 hizmet) için üyelik Teams. Microsoft 365 grupları, "sahipler" ve "üyeler" arasında güvenli bir şekilde ayırt etmek ve grup içindeki çeşitli özelliklere erişimi Teams. Uygun yönetim denetimleriyle ve düzenli olarak yönetilen erişim incelemeleri ile Teams, yalnızca üyelerin ve sahiplerin yetkili kanallardan ve özelliklerden yararlanmasını sağlar.

Finansal hizmetlerin yararlarından yararlanan yaygın Teams, iç projeleri veya programları çalıştırmadır. Örneğin, bankalar, varlık yönetimi şirketleri, kredi birliği ve sigorta sağlayıcıları gibi birçok mali kurumun, bir başka uyumluluk programlarını ve para koruma programlarını zorunlu bulundurabilirsiniz. İşletmeden oluşan, perakende ve zengin yönetim gibi iş satırlarını ve mali olay birimini oluşturan işlevsel bir ekip, verileri birbirleriyle paylaşmak ve program veya belirli soruşturmalar hakkında iletişim kurmak için gerekli olabilir. Geleneksel olarak bu programlar paylaşılan ağ sürücülerini kullanıyor, ancak bu yaklaşım çeşitli zorluklara neden olabilir:
* Bir belgeyi aynı anda yalnızca bir kişi düzenleyebilir.
* Bireyleri eklemek/kaldırmak genellikle IT içerdiği için güvenliği yönetmek zaman alıcıdır.
* Veriler, gerekenden veya gerekenden çok daha uzun bir süre paylaşılan ağ sürücülerinde yerleşik olarak kalır.

Teams hassas istemci verilerini güvenli bir şekilde depolamak ve hassas konuların tartışılır olduğu ekip üyeleri arasında konuşmalar yapmak için işbirliği alanı s sağlar. Ekibin birden çok üyesi aynı anda tek bir belgeyi düzenleyebilir veya üzerinde işbirliği düzenleyebilir. Program sahibi veya özel kişi, ekip sahibi olarak yatıl olabilir ve gerektiğinde üye ekleyebilir ve kaldırabilir.

Bir diğer yaygın senaryo da Teams depolama ve yönetme gibi güvenli bir şekilde işbirliği yapmak için bu alanı "sanal veri odası" olarak kullanmaktır. Ekip üyeleri ve dağıtımları yatırım bankaları, varlık yönetimi veya özel öz varlık firmalarının bir anlaşma veya yatırım üzerinde güvenli bir şekilde işbirliği yapmalarını sağlar. İşlevsel ekipler, bu tür anlaşmaları planlama ve gerçekleştirmeye çoğunlukla dahil olur ve verileri güvenli bir şekilde paylaşabilme ve konuşma yapma olanağı temel gereksinimdir. İlgili belgeleri dış yatırımcılarla güvenli bir şekilde paylaşmak da önemli bir gereksinimdir. Teams verileri merkezi olarak depolamak, korumak ve paylaşmak için gereken güvenli ve tam olarak denetlenebilir bir konum sağlar.

![Bir toplantı çalışanlarının grubu büyük bir scree üzerinde görüntüler hakkında konuştular.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: İşbirliğini geliştirme ve uyumluluk riskini azaltma

Microsoft 365, temel üyelik hizmeti olarak Teams grupların kullanımı yoluyla, Microsoft 365 ilke özellikleri sağlar. Bu ilkeler işbirliğini geliştirmeye ve uyumluluk  ihtiyaçlarını karşılamaya yardımcı olabilir.

**Microsoft 365 adlandırma ilkeleri,** grup gruplarında Microsoft 365 dolayısıyla ekiplerin kurumsal ilkeye göre adlandırıldıklarının sağlanmasına yardımcı olur. Uygun olmayan adlar sorun yaratabilir. Örneğin, adlar uygun şekilde uygulanmazsa, çalışanlar hangi ekiplerle çalış çalışsa veya bilgilerle bilgi paylaşsalar bile, bunu bilmiyor olabilir. Grup adlandırma ilkeleri (önek/son ek tabanlı ilkeler ve özel engellenen sözcükler için destek dahil) iyi bir "ednın" zorunlu kılınması ve özel olarak ayrılmış sözcükler veya uygunsuz terminoloji gibi belirli sözcüklerin kullanımını engelleyebilir.
  
**Microsoft 365 süre sonu** ilkeleri, gruplarda Microsoft 365 ve dolayısıyla ekiplerin kuruluşun istediği veya gerekenden daha uzun süre tutulmaması sağlamaya yardımcı olur. Bu özellik, iki önemli bilgi yönetimi sorunlarını önlemeye yardımcı olur:

* Gerekli veya kullanılmaması gereken ekiplerin yayılması.
* Kuruluş tarafından artık gerekli olmayan veya kullanılan veriler için fazla saklama (yasal saklama/saklama durumlar dışında).

Yöneticiler, gruplarda 90, 180 veya 365 gün gibi Microsoft 365 bir süre sonu belirtmektedir. Bir grup tarafından desteklene hizmet Microsoft 365 süre sonu için etkin değilse, grup sahiplerine bildirim gelir. Hiçbir işlem Microsoft 365, Grup Teams de dahil olmak üzere ilgili tüm hizmetleri silinir.
  
Tek bir veritabanında ve diğer grup tabanlı hizmetlerde depolanan verilerin fazla Teams, finansal hizmet kuruluşlarına riskler neden olabilir. Microsoft 365 süre sonu ilkeleri, artık gerekli olan verilerin bekletmesini önlemeye yardımcı olmak için önerilen bir yoldur. Microsoft 365, yerleşik bekletme etiketleri ve ilkeleriyle bir araya getirerek kuruluşların yalnızca şirket ilkelerini ve yasal düzenlemelere uyumluluk yükümlülüklerini yerine getirmesi için gerekli olan verileri alıkoymalarına yardımcı olur.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Özel gereksinimleri kolaylıkla tümleştirin

Teams, varsayılan olarak ekiplerin self servis oluşturulmasına olanak sağlar. Ancak, düzenlemeye tabi olan birçok kuruluş çalışanları tarafından şu anda hangi işbirliği kanallarının geçerli olduğunu, hangi kanalların hassas veriler içer içerenin ve kuruluş kanallarının sahipliğini kontrol etmek ve anlamak ister. Bu yönetim denetimlerini kolaylaştırmak için, Microsoft 365 self servis ekip oluşturma özelliğini devre dışı bırakmasını sağlar. Kuruluşlar, Microsoft Power Apps ve Power Automate gibi iş süreci otomasyon araçlarını kullanarak, çalışanların yeni ekip oluşturması için basit formlar ve onay işlemleri hazırlayabilir ve dağıtabilirsiniz. Onaylandıktan sonra ekip otomatik olarak sağlandıktan sonra istek sahibine bir bağlantı gönderebilirsiniz. Bu şekilde, kuruluşlar uyumluluk denetimlerini ve özel gereksinimlerini ekip oluşturma işlemiyle tasarlar ve tümleştirin.
 
### <a name="acceptable-digital-communication-channels"></a>Kabul edilebilir dijital iletişim kanalları

FINRA, düzenlemeye tabi firmalardan gelen dijital iletişimlerin [Exchange Act rules 17a-3 ve 17a-4 ile FINRA Rule Series 4510'un](https://www.finra.org/rules-guidance/key-topics/books-records) kayıt tutma gereksinimlerini karşılamaktadır. FINRA, kuruluşların uyumluluk ve risk yönetimini geliştirmelerine yardımcı olmak için önemli bulguları, gözlemleri ve etkili uygulamaları içeren yıllık bir rapor yayımlar. FinRA [, 2019'daki](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) Gizli Bulguları ve Gözlemler Raporu'nda, dijital iletişimi gözetim ve kayıt tutma gerekliliklerine uymanın güçlükleriyle karşılaştıkları önemli bir alan olarak belirledi.

Bir kuruluş çalışanlarının uygulama tabanlı bir mesajlaşma hizmeti veya işbirliği platformu gibi belirli bir uygulamayı kullanmalarına izin verirseniz, firmanın söz konusu uygulamanın çalışanlarının etkinliklerini ve iletişimlerini denetlemesi için iş kayıtlarını arşivlemesi ve denetlemesi gerekir. Kuruluşlar, FINRA kuralları ve menkul değer yasalarına uymak için due dili kullanmak ve söz konusu uygulamaların çalışan kullanımıyla ilgili söz konusu kuralların olası ihlallerini takip etmekle sorumludur.
  
FINRA tarafından önerilen etkili uygulamalar şunlardır:
* Dijital iletişim kanalları için kapsamlı bir yönetim programı kurma. Kuruluşun hangi dijital iletişim kanallarına izin verildiğine ilişkin kararlarını yönetin ve her dijital kanal için uyumluluk süreçleri tanımlayın. Dijital iletişim kanallarının hızlı bir şekilde değişen ortamını yakından izleyin ve uyumluluk işlemlerini güncel tutabilirsiniz.
* Izin verilen dijital kanalları açık bir şekilde tanımlayın ve kontrol altında bulundurabilirsiniz. Onaylanmış ve yasaklanan dijital kanalları tanımlayın. Kuruluşun kayıt yönetimi ve gözetmen gereksinimlerine uyma becerisini sınırlayan, yasaklanan dijital kanalların veya dijital kanallarda yasaklanan özelliklerin kullanımını engelin veya kısıtlar.
* Dijital iletişimler için eğitim sağlama. Kayıtlı temsilcilere onaylı dijital kanallara erişim vermeden önce zorunlu eğitim programlarını hayata geçirebilirsiniz. Eğitim, kuruluşun ticari ve kişisel dijital iletişimlere olan beklentilerini netleştirmeye yardımcı olur ve personelin her kanalın izin verilen özelliklerini uyumlu bir şekilde kullanmalarına yardımcı olur.

Dijital İletişim için FINRA'nın bulguları ve gözlemleri, bir kuruluşun işle ilgili tüm iletişimleri korumak için [SEC Kuralı 17a-4'e](https://www.law.cornell.edu/cfr/text/17/240.17a-4) uyum, iletişimi gözetim ve gözden geçirme için FINRA kuralları [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) ve [3120](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) ve kayıt tutmak için Kural [Serileri 4510'a](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) uyum elde etme özelliğiyle doğrudan ilgilidir. Commodity Futures Ticaret Komisyonu (CFTC) 17 CFR 131'in altında benzer gereksinimleri ortaya almaktadır. Bu düzenlemeler bu makalenin ilerleyen sayfalarında ayrıntılı olarak ele alınmıştır.

***Teams güvenlik ve uyumluluk tekliflerini kapsamlı bir Microsoft 365 paketiyle birlikte, finansal hizmetler kuruluşlarının işleri etkili bir şekilde yürütecek ve yasal düzenlemelere uyması için kurumsal bir dijital iletişim kanalı sunar.*** Bu makalenin kalan kısmında, Microsoft 365 yönetimi, bilgi koruması, bilgi engelleri ve gözetmen denetimi gibi yerleşik becerilerin Teams bu mevzuat yükümlülüklerini karşılamaya yardımcı olacak güçlü bir araç kümesi verdiği açıklanmıştır.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Destekle modern işbirliğini Microsoft 365

### <a name="secure-user-identities-and-control-access"></a>Kullanıcı kimliklerinin güvenliğini sağlama ve erişimi denetleme

***Müşteri bilgilerine, finansal belgelere ve uygulamalara erişimi koruma, kullanıcı kimliklerinin kesinlikle güvenliğini sağlamadan başlar.*** Bu, kuruluş için kimlikleri depolamak ve yönetmek, güvenilir bir kimlik doğrulama aracı sağlamak ve bu uygulamalara erişimi dinamik olarak denetlemek için güvenli bir platform gerektirir.

Çalışanlar çalışıyorken bir uygulamadan uygulamaya veya birden fazla konum ile cihaz arasında geçişebilirler. Yol boyunca her adımda verilere erişimin doğrulanmış olması gerekir. Kimlik doğrulama işleminin, kimliklerin güvenliğinin ihlal edilmiş olmasını sağlamak için güçlü bir protokolü ve birden çok kimlik doğrulama faktörünü (tek seferlik SMS geçiş kodu, doğrulayıcı uygulaması ve sertifika gibi) desteklemesi gerekir. Risk tabanlı erişim ilkelerinin zorması, finansal verileri ve uygulamaları insider tehditlerine, yanlışlıkla veri sızıntılarına ve veri sızıntılarına karşı korumak için çok önemlidir.

Microsoft 365, kimliklerin merkezi olarak depolandığı ve güvenli bir şekilde yönetillerin bulunduğu Azure Active Directory ([Azure AD)](/azure/active-directory/) içinde güvenli bir kimlik platformu sağlar. Azure AD ile bir çok ilişkili Microsoft 365 güvenlik hizmeti, çalışanlara güvenli bir şekilde çalışması için gereken erişimi sağlamanın temelini oluşturur ve aynı zamanda kuruluşu tehditlerden de korur.

[Azure AD Multi-Factor Authentication (MFA),](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) platformda yerleşik olarak yer alır ve hassas finansal verilere ve uygulamalara erişen kullanıcı kimliğini onaylamaya yardımcı olmak için ek bir kimlik doğrulama kanıtı sağlar. Azure MFA, parola ve bilinen bir mobil cihaz gibi en az iki kimlik doğrulama yöntemi gerektirir. Aşağıdakiler gibi çeşitli ikinci faktörlü kimlik doğrulama seçeneklerini destekler:

- Microsoft Authenticator uygulaması
- SMS ile tek seferlik geçiş kodu teslim edildi
- Kullanıcının PIN'i girmesi gereken telefon görüşmesi

Parola bir şekilde tehlikeye girerse, kurumsal verilere erişim elde etmek için olası bir korsanın yine de kullanıcının telefonuna ihtiyacı olur. Buna ek olarak Microsoft 365, web tarayıcılarından Microsoft Outlook ve diğer Microsoft Office uygulamaları da dahil olmak üzere çalışanların gün boyunca kullandığı işbirliği araçlarına güçlü ve zengin kimlik doğrulama deneyimini getiren önemli bir protokol olarak Modern Kimlik Doğrulama'Microsoft Office kullanır.

#### <a name="passwordless"></a>Parolasız

Parolalar, güvenlik zincirinin en zayıf bağlantısıdır. Başka doğrulama yoksa, tek bir hata noktası olabilir. Microsoft, finansal kuruluşların ihtiyaçlarına uygun olarak çok çeşitli kimlik doğrulama seçeneklerini destekler.

*Parolasız* yöntemler, MFA'nın kullanıcılar için daha kolay hale getirir. Tüm MFA parolasız değildir ama parolasız teknolojiler çok faktörlü kimlik doğrulamasını kullanır. Microsoft, Google ve diğer endüstri öncüleri, Hızlı IDentity Online (FIDO) adı verilen bir grupta web ve mobil cihazlarda daha basit, daha güçlü bir kimlik doğrulama deneyimi sağlamak için standartlar geliştirmiştir. Yakın zamanda geliştirilen FIDO2 standardı, kullanıcıların kimlik avını ortadan kaldırmak için parolaya gerek kalmadan kolayca ve güvenli bir şekilde kimlik doğrulaması yapmalarına olanak sağlar.

Parolasız Microsoft MFA yöntemleri şunlardır:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): Esneklik, kolaylık ve maliyet için mobil uygulamayı Microsoft Authenticator öneririz. Microsoft Authenticator Azure AD bağlantılı herhangi bir uygulama için biyometrik, anında bildirimler ve tek kullanımlık geçiş kodlarını destekler. Apple ve Android uygulama mağazalarından edinebilirsiniz.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): PC'de yerleşik bir deneyim için Windows Hello. Otomatik olarak oturum açmak için biyometrik bilgileri (yüz veya parmak izi gibi) kullanır.  
* [FIDO2 Güvenlik](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) anahtarları şimdi birkaç Microsoft iş ortağından kullanılabilir: Yubico, Feitian Technologies ve HID Global USB, NFC özellikli rozet veya biyometrik anahtar.

[Azure AD Koşullu Erişim](/azure/active-directory/conditional-access/) , erişim denetim kararlarını otomatik olarak almak ve şirket varlıklarını korumak için kuruluş ilkelerini zorlamak için güçlü bir çözüm sağlar. Klasik bir örnek, finansal planlayıcının hassas müşteri verilerine sahip bir uygulamaya erişmek istediği zamandır. Özellikle bu uygulamaya erişmek için çok faktörlü kimlik doğrulamasının gerçekleştiriliyor olması için otomatik olarak gerekmektedir ve erişim şirket tarafından yönetilen bir cihazdan gerçekleştirilsin. Azure Koşullu Erişim, kullanıcının erişim isteğiyle ilgili olarak kullanıcı, cihaz, konum ve ağ ile kullanıcının erişmeye çalıştığı uygulama gibi sinyaller getirir. Yapılandırılmış ilkelere karşı uygulamaya erişim denemelerini dinamik olarak değerlendirir. Kullanıcı veya cihaz riski yükseltilmişse veya diğer koşullar karşılanmazsa, Azure AD, MFA gerektirme, güvenli parola sıfırlaması gerektirme, erişimi kısıtlama veya engelleme gibi ilkeleri otomatik olarak zorunlu tutabilirsiniz. Bu, hassas kurumsal varlıkların dinamik olarak değişen ortamlarda korunmasına yardımcı olur.
 
Azure AD ve ilgili Microsoft 365 güvenlik hizmetleri, veri ve uygulamalara erişimin güvence altına alınama ve uyumluluk uyumluluk yükümlülüklerinin karşılandırılay olması için, modern bir bulut işbirliği platformunun mali kurumlara aktarılamayacak temeli sağlar. Bu araçlar aşağıdaki temel özellikleri sağlar:

* Kullanıcı kimliklerini merkezi olarak depolar ve güvenli bir şekilde yönetir.
* Erişim isteklerinde kullanıcıların kimliğini doğrulamak ve tüm uygulamalarda tutarlı ve güçlü bir kimlik doğrulama deneyimi sağlamak için çok faktörlü kimlik doğrulaması da dahil olmak üzere güçlü bir kimlik doğrulama protokolü kullanın.
* Kimlik, kullanıcı/grup üyeliği, uygulama, cihaz, ağ, konum ve gerçek zamanlı risk puanı da içinde olmak üzere birden çok sinyalleri ilke karar verme sürecine dahil ederek tüm erişim isteklerine dinamik olarak ilkeleri doğrular.
* Kullanıcı davranışı ve dosya özelliklerine dayalı olarak ayrıntılı ilkeleri doğrular ve gerektiğinde ek güvenlik önlemlerini dinamik olarak zorunlu kılın.
* Kuruluşta "gölge IT" tanımlama ve InfoSec ekiplerinin bulut uygulamalarını güvenlikle ilgili olarak engellemesine izin verme.
* Microsoft'a ve Microsoft'a özel bulut uygulamalarına erişimi izleme ve denetleme.
* E-posta kimlik avı ve fidye yazılımı saldırılarına önceden koruma.

#### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection
Koşullu Erişim şüpheli isteklerden kaynakları korurken, Kimlik Koruması devam eden risk algılama ve şüpheli kullanıcı hesaplarının düzeltmesi ile daha da ilerler. Kimlik Koruması, ortamınız içinde saat içinde şüpheli kullanıcı ve oturum açma davranışı hakkında sizi bilgi tutar. Bu özelliğin otomatik yanıtı güvenliği tehlikeye atılmış kimliklerin kötüye 15 gün içinde ihlal 112 gün içinde ihlal 1 gün içinde 15 gün içinde karşıdan yüksek bir şekilde ihlal 15 gün içinde 1
 
Kimlik Koruması, kuruluşların üç önemli görevi gerçekleştirmelerini sağlayan bir araçtır:

* Kimlik tabanlı riskleri algılamayı ve düzeltmeyi otomatikleştirin.
* Portalda verileri kullanarak riskleri araştırabilirsiniz.
* Daha fazla çözümleme yapmak için risk algılama verilerini üçüncü taraf yardımcı programlara dışarı aktarın.

Kimlik Koruması, Microsoft'un Azure AD'ye sahip kuruluşlarda, Microsoft Hesapları ile tüketici alanı içinde ve xbox ile oyun oynama konusunda kullanıcılarınızı korumak için kendi konumundan edin yaptığı bilgileri kullanır. Microsoft, müşterileri tehditlerden korumak için günde 65 tr bir sinyal analiz eder. Kimlik Koruması tarafından oluşturulan ve Kimlik Koruması'ndan besilen sinyaller, erişim kararları almak için Koşullu Erişim gibi araçlara daha fazla beslenir. Ayrıca, bir güvenlik bilgileri ve olay yönetimi (SIEM) aracına geri beslenirler ve bu araç, kuruluşun zorunlu ilkelerine bağlı olarak daha fazla araştırma yapmak için hazırlar.

Kimlik Koruması, Microsoft ekosistemi üzerinde gelişmiş algılama, kullanıcı ve varlık davranışı analizi (UEBA) ve makine öğrenimi (ML) ile desteklenen bulut zekası özelliğinden yararlanarak kuruluşların kimlik güvenliğinden otomatik olarak korunmasına yardımcı olur.

![Bir sunuda, başka bir bilgi çalışanlarının başka biri olarak izlemesi gerekir.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Hassas verileri tanımlama ve veri kaybını önleme
Microsoft 365, tüm kuruluşların aşağıdakiler gibi güçlü özelliklerden bir birleşimiyle kuruluş içindeki hassas verileri tanımlamalarını sağlar:

* **Microsoft Bilgi Koruması tabanlı sınıflandırma ve** hassas verilerin otomatik sınıflandırması için genel bir sınıflandırma (MIP) sağlar.
* Office 365 veri türleri (başka bir deyişle normal ifadeler) ve anahtar sözcükler kullanarak hassas verilerin otomatik olarak tanımlanması ve ilke zorlaması için Veri Kaybı Önleme **(DLP)** önlemeyi sağlar.

**[Microsoft Bilgi Koruması (MIP),](../compliance/information-protection.md)** kuruluşların belgeleri ve e-postaları duyarlılık etiketlerini kullanarak akıllı bir şekilde sınıflandırmalarını sağlar. Duyarlılık etiketleri kullanıcılar tarafından Microsoft Office uygulamalarında belgelere ve Outlook e-postalara el ile Outlook. Etiketler otomatik olarak belge işaretleri, şifreleme yoluyla koruma ve hak yönetimi zorlaması uygulayabilir. Duyarlılık etiketleri, hassas verileri otomatik olarak bulmak ve sınıflandırmak için anahtar sözcükleri ve hassas veri türlerini (kredi kartı numaraları, sosyal sigorta numaraları ve kimlik numaraları gibi) kullanan ilkeler yapılandırarak da otomatik olarak uygulanabilir.

Buna ek olarak, Microsoft yalnızca desen eşleştirmesi veya içerik içindeki öğeler yerine, içeriğe dayalı hassas verileri tanımlamak için makine öğrenme modellerini kullanan "eğitilebilir sınıflayıcılar" sağlar. Sınıflandırıcı, sınıflandırılabilir içerikle ilgili çok sayıda örneke bakarak bir içerik türünü belirlemeyi öğrenir. Sınıflandırıcı eğitim, belirli bir kategorideki içeriğe örnekler vererek başlar. Bu örneklerden öğrendikten sonra, model eşleşen ve eşleşmeyen örnekler karma olarak test edilir. Sınıflandırıcı, verilen örneğin kategoriye gir olup olmadığını tahmin ediyor. Ardından bir kişi, sınıflandırıcının tahminlerinin doğruluğunu artırmaya yardımcı olmak için sonuçları onaylar; pozitifleri, negatifleri, yanlış pozitifleri ve yanlış negatifleri sıralar. Eğitimli sınıflandırıcı yayım olduğunda, içeriği otomatik olarak Microsoft Office SharePoint Online, Exchange Online ve OneDrive İş olarak sınıflanır.

Belgelere ve e-postalara duyarlılık etiketlerinin uygulanması, nesne içinde seçilen duyarlılığı tanımlayan meta verileri içerir. Daha sonra duyarlılık verilerle birlikte seyahat ediyor. Etiketli bir belge kullanıcının masaüstünde veya şirket içi bir sistem içinde depolanıyor olsa bile, korunmaktadır. Bu işlevsellik, Microsoft 365 ve güvenlik denetimlerini otomatik olarak zorunlu tutulacak şekilde bulut uygulamaları veya ağ uç cihazları için Microsoft Defender gibi diğer çözümlerde olanak tanır. Duyarlılık etiketleri çalışanlara kuruluş içinde hangi verilerin hassas olarak kabul edilir ve bu verileri alınca nasıl işleniyorları konusunda eğitimci olma avantajını da sağlar.

**[Office 365 Kaybı Önleme (DLP)](../compliance/dlp-learn-about-dlp.md)** özelliği, hassas verileri taratarak ve ardından bu nesneler üzerinde ilkeyi zorlayarak hassas veriler içeren belgeleri, e-postaları ve konuşmaları otomatik olarak tanımlar. İlkeler, belge ve SharePoint belgeler üzerinde OneDrive İş. Ayrıca, kullanıcılar e-posta gönderirken ve aynı zamanda Teams ve kanal konuşmalarında uygulanır. İlkeler anahtar sözcükleri, hassas veri türlerini, bekletme etiketlerini ve verilerin kuruluş içinde mi yoksa dışında mı paylaşılıyorsa onu araması için ya da kullanılabilir. Kuruluşların hatalı pozitif sonuçlarını azaltmak için DLP ilkelerine ince ayarda yardımcı olması için denetimler sağlanır. Hassas veriler bulunduysa, Microsoft 365 uygulamaları içindeki kullanıcılara özelleştirilebilir ilke ipuçları görüntülenebilir ve böylece içerikleri hassas veriler içerdiği konusunda bilgi edinebilir ve doğrulayıcı eylemler önerebilir. İlkeler kullanıcıların belgelere erişmesini, belge paylaşmasını veya belirli türlerde hassas veriler içeren e-postalar göndermesini de önleyebilirsiniz. Microsoft 365 100'den fazla yerleşik hassas veri türü destekler. Kuruluşlar, ilkelerine uygun olarak özel duyarlı veri türlerini yapılandırabilirsiniz.

MIP ve DLP ilkelerini kuruluşlara yapmak için dikkatli bir planlama ve kullanıcı eğitim programı gerekir; böylece çalışanlar kuruluşun veri sınıflandırma şemasını anlar ve hangi veri türlerinin hassas kabul edilir. Çalışanlara hassas verileri tanımlamalarına ve bu verilerin nasıl işle ilgili olduğunu anlamalarına yardımcı olan araçlar ve eğitim programları sağlama, bilgi güvenliği risklerini azaltmaya yönelik çözümün bir parçası olur.

Kimlik Koruması tarafından oluşturulan ve Kimlik Koruması'ne besilen sinyaller, erişim kararları almak için Koşullu Erişim gibi araçlara veya kuruluşun zorunlu ilkelerine dayalı olarak soruşturma için bir güvenlik bilgisi ve olay yönetimi (SIEM) aracına da beslenir.

Kimlik Koruması, gelişmiş algılamalar, kullanıcı ve varlık davranış çözümlemeleri ve Microsoft ekosistemi genelinde makine öğrenimi gibi gelişmiş algılamalarla desteklenen bulut zekası özelliğinden yararlanarak kuruluşların kimlik güvenliğinden otomatik olarak korunmasına yardımcı olur.

![Bilgi çalışanı, büyük bir monitör dizisinin önünde resim resmedildi.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Hisarları savunma

Microsoft, modern kuruluşun Microsoft 365 Defender tehdit ortamına karşı güvenliğini sağlamak için tasarlanan yeni çözüme kısa süre önce bir çözüm sunmaktadır. Akıllı Güvenlik özelliğiden yararlanarak Graph Koruma çözümü, birden çok saldırı vektörlerine karşı kapsamlı, tümleşik güvenlik sunar.

### <a name="the-intelligent-security-graph"></a>[Akıllı Güvenlik Graph](https://www.microsoft.com/security/business/intelligence) 
Farklı güvenlik Microsoft 365 hizmetleri Akıllı Güvenlik hizmetleri tarafından Graph. Siber tehditlerle mücadele etmek için, Akıllı Güvenlik Graph Microsoft'un ve ortaklarının tehdit zekasını ve güvenlik sinyallerini bağlantı kurmak için gelişmiş çözümleme kullanır. Microsoft, genel hizmetleri muazzam bir ölçekte çalışır ve yığın genelinde güç koruma katmanlarını bu güvenlik işaretlerini topluyor. Makine öğrenme modelleri bu zekayı değerlendirir ve sinyal ve tehdit öngörüleri ürün ve hizmetlerimiz genelinde yaygın olarak paylaşılır. Bu, tehditleri hızla algılaymıza ve yanıtlamamıza, düzeltme için de müşterilere işlemlebilir uyarılar ve bilgiler getirmemizi sağlar. Makine öğrenme modellerimiz, yeni içgörülerle sürekli olarak eğitildi ve güncelleştirildi, daha güvenli ürünler oluşturmamıza ve daha öngörülü bir güvenlik sağlamamıza yardımcı oluyor.

[Microsoft Defender for Office 365](../security/office-365-security/defender-for-office-365.md) provides an integrated Microsoft 365 service that protects organizations from malicious links and malware delivered through email and Office documents. Bugün kullanıcıları etkileyen en yaygın saldırı vektörlerinden biri e-posta kimlik avı saldırılarıdır. Bu saldırılar belirli kullanıcılara hedef olabilir ve kullanıcıdan kötü amaçlı yazılım içeren bir bağlantıya tıklamasını veya bir eki açmasını istenten bir eylem çağrısında çok ikna edici olabilir. Bilgisayara virüs bulaştırıldıktan sonra, saldırgan kullanıcının kimlik bilgilerini çalmak ve daha sonra kuruluş genelinde çalmak ya da e-postaları ve verileri çalarak hassas bilgileri arayabilmesini sağlar. Güvenlik için Defender Office 365 kötü amaçlı olabilecekler için belgeleri ve bağlantıları tıklama zamanında değerlendirerek ve erişimi engelleyen güvenli ekleri ve güvenli bağlantıları destekler. E-posta ekleri, kullanıcının posta kutusuna teslim edildiklerine kadar korumalı korumalı alanda açılır. Ayrıca, belgelerde kötü amaçlı URL'ler Office bağlantıları da değerlendirir. Defender for Office 365 ayrıca SharePoint Online, OneDrive İş ve Teams'da bağlantıları ve dosyaları korur. Kötü amaçlı bir dosya algılanırsa, olası Office 365 için Defender bu dosyayı otomatik olarak kilitler.

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) , koruma, ihlal sonrası algılama ve otomatik soruşturma ve yanıt için birleşik bir uç nokta güvenlik platformudur. Uç Nokta için Defender, kurumsal uç noktalarda hassas verilerin bulunması ve korunması için yerleşik özellikler sağlar.

[Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security) , kuruluşların ilkeleri ayrıntılı bir düzeyde zorunlu kullanmalarına ve makine öğrenimi kullanılarak otomatik olarak tanımlanan tek tek kullanıcı profillerine dayalı davranışsal hataları algılamalarına olanak sağlar. Bulut Uygulamaları için Defender ilkeleri, hassas şirket varlıklarını korumak için Azure Koşullu Erişim ilkeleri oluşturmak için, erişilen belgelerin kullanıcı davranışı ve özellikleriyle ilgili ek sinyalleri değerlendirebilirsiniz. Zaman içinde Bulut Uygulamaları için Defender, her çalışana, erişeceği verilerle ve bu uygulamalarla ilgili olarak nelerin tipik bir davranış olduğunu öğrenir. Öğrenilen davranış düzenlerine bağlı olarak, bir çalışan bu davranış profili dışında bir eylemde olursa ilkeler otomatik olarak güvenlik denetimlerini zorunlu kılınacaktır. Örneğin, bir çalışan normalde Pazartesi ile Cuma arası 09:00 ile 17:00 arası bir uygulamaya erişiyor ancak aniden o uygulamaya yoğun bir şekilde erişiyorsa, Bulut Uygulamaları için Defender dinamik olarak ilkeleri zorunlu kıldığında kullanıcının yeniden kimlik doğrulamasına gereksin. Bu, kullanıcının kimlik bilgilerinin güvenliğinin ihlal edilmiş olmasını sağlamaya yardımcı olur. Bulut Uygulamaları için Defender, kuruluşta "gölge IT"sini belirlemeye de yardımcı olabilir ve bu da bilgi güvenliği ekiplerinin, çalışanların hassas verilerle çalışırken güvenlik araçlarını kullanmalarını sağlamaya yardımcı olur. Son olarak, Bulut Uygulamaları için Defender hassas verileri buluttaki her yerde, platform dışında bile Microsoft 365 koruyabilirsiniz. Kuruluşların erişimi denetleyen ve kullanımı izlemesi için belirli dış Bulut uygulamalarını kullanmalarına (veya onaylarını kullanmamalarına) olanak sağlar.
 
[Identity için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) , şirket içi Active Directory sinyallerinizi kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini belirlemek, algılamak ve araştırmak için yararlanan bulut tabanlı bir güvenlik çözümüdür. AATP, snOp analistlerinin ve güvenlik uzmanlarının karma ortamlardaki gelişmiş saldırılar algılayan şu özellikleri sağlar:
* Öğrenme tabanlı çözümlemeleri kullanarak kullanıcıları, varlık davranışını ve etkinlikleri izleyebilirsiniz.
* Active Directory'de depolanan kullanıcı kimliklerini ve kimlik bilgilerini koruyun.
* Kill zinciri boyunca şüpheli kullanıcı etkinliklerini ve gelişmiş saldırılarını belirleyin ve araştırnın.
* Hızlı bir üç ay için basit bir zaman çizelgesi üzerinde net olay bilgileri sağlar.

![Ofis çalışanları küçük bir konferans odasında bir araya geldi. Biri sunu verir.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Verileri yönetme ve kayıtları yönetme

Finansal kuruluşlar, şirket bekletme zamanlamalarında temsil edilen yasal ve ticari yükümlülüklerine göre kayıt ve bilgilerini korumaları gerekir. Örneğin SEC, [kayıt](https://www.sec.gov/rules/interp/34-47806.htm) türüne göre üç ile altı yıllık bekletme dönemlerini vek. İlk iki yıl için anında erişilebilirlik sağlar. Veriler az korunursa (çok erken atılırsa) yasal ve mevzuat uyumluluğu risklerle karşılaşan kuruluşlar, ayrıca bilgilerin artık gerekli olmadığı zaman vekli düzenlemelerini de yönetir. Etkili kayıt yönetimi stratejileri, bilgilerin uygun şekilde atılması ve kuruluşa maliyeti ve riski en aza indirilmesi için pratik ve tutarlı bir yaklaşımı vurgular.
 
Buna ek olarak, New York State Department of Financial Services'ta yer alan düzenlemeler için, yayın dışı bilgilerin imhası için ilkeleri ve yordamları korumaları gerekir. 23 NYCRR 500, Bölüm 500.13, Veri Bekletme Sınırlamaları "Siber güvenlik programlarının bir parçası olarak, ele alınan her Bir Varlık, bölüm 500.01(g)(2)-(3) bölümünde tanımlanan ve artık ticari işlemlere veya Kapsayan Tüzel kişinin diğer yasal iş amaçlarına yönelik olarak güvenli bir şekilde sağlamak için ilkeler ve yordamlar içermesini gerektirir.  hariç, bu bilgilerin yasalar veya düzenlemeyle muhafazası zorunludur."
 
Finansal kurumlar çok büyük miktarda veri yönetir. Bazı bekletme süreleri de, sözleşmenin sona erdiği veya kuruluştan ayrılmakta olan bir çalışan gibi olaylar tarafından tetiklenir. Bu atmosferde, kayıt bekletme ilkeleri uygulamak zor olabilir. Kuruluş belgeleri genelinde kayıt bekletme dönemlerini doğru bir şekilde atama yaklaşımları değişiklik gösterebilir. Bazıları kapsamlı olarak bekletme ilkelerini kullanır veya otomatik sınıflama ve makine öğrenme tekniklerini kullanır. Diğerleri, benzersiz olarak tek tek belgelere bekletme dönemleri ataan daha ayrıntılı bir işlem gerektiren bir yaklaşım benimser.

***Microsoft 365, kayıt yönetimi gereksinimlerini akıllı bir şekilde uygulamak için bekletme etiketlerini ve ilkelerini tanımlamak için esnek özellikler sağlar.*** Kayıt yöneticisi, geleneksel bekletme zamanlamada "kayıt türünü" temsil eden bir bekletme etiketi tanımlar. Bekletme etiketi, şu ayrıntıları tanımlayan ayarları içerir:

- Kaydın ne kadar süreyle korundu
- Bekletme süresinin süresi dolduğunda neler olur (belgeyi silin, incelemeyi başlatma veya hiçbir işlem yapmaya izin alma)
-  Bekletme döneminin başlangıcını tetikleyen (oluşturma tarihi, son değiştirme tarihi, etiketli tarih veya olay) ve belgeyi veya e-postayı kayıt olarak işaretler (düzenlenemez veya silinemez)

Bekletme etiketleri daha sonra başka sitelerde SharePoint OneDrive, posta Exchange ve gruplarda Microsoft 365 yayımlanır. Kullanıcılar bekletme etiketlerini belgelere ve e-postalara el ile uygulayabilir. Kayıt yöneticileri etiketleri otomatik olarak uygulamak için zekayı kullanabilir. Akıllı özellikler, [doksan artı](../compliance/content-search.md) olarak yerleşik hassas bilgi türlerine (ABA outing numarası, ABD banka hesap numarası veya ABD Sosyal Güvenlik Numarası gibi) dayandırabilirsiniz. Ayrıca, kredi kartı numaraları veya diğer kişisel bilgiler gibi belgelerde veya e-postalarda bulunan anahtar sözcüklere veya hassas verilere göre ya da meta verilere dayalı olarak SharePoint. El ile veya otomatik desen eşleştirmesi ile kolayca tanımlanemeyen veriler için, eğitilebilir sınıflayıcılar belgeleri makine öğrenme tekniklerine göre akıllı bir şekilde sınıflandırmak için kullanılabilir.
 
**Securities and Exchange Commission (SEC)** işle ilgili tüm iletişimleri korumak için aracılı kuruluş veya başka düzenlemeye tabi mali kurumlar gerektirir. Bu gereksinimler; e-postalar, belgeler, anlık iletiler, fakslar ve çok daha fazlası gibi çok çeşitli iletişim ve veri türleri için geçerlidir. **SEC kuralı 17a-4** , bu kuruluşların kayıtları bir elektronik veri depolama sisteminde depolamak için karşılamaları gereken ölçütleri tanımlar. 2003'te SEC, bu gereksinimlerin açık olduğu bir sürüm yayınlamaktadır. Aşağıdaki ölçütleri içerir:

* Elektronik depolama sistemi tarafından korunan veriler yeniden yazılamaz ve silinebilir değildir. Buna BIR KURDUN gereksinimi denir (bir kez yazma, çok okuma).
* Depolama sisteminin, mahkeme kararı veya başka bir yasal sipariş olması durumunda kural tarafından gereken bekletme süresi dışında veri depolayabiliyor olması gerekir.
* Bir kuruluş, tümleşik donanım ve yazılım denetim kodlarının kullanımı yoluyla gerekli bekletme süresi boyunca bir kaydın üzerine yaz yazsını, sikini veya başka bir şekilde değiştirilmesini engelleyen bir elektronik depolama sistemi kullanıyorsa kuralın paragraf (f)(2)(a)(A) gereksinimini ihlal edilemez.
* Yalnızca "azalt" olan elektronik depolama sistemleri bir kaydın üzerine yazılma veya silinmesi riskini (örneğin, erişim denetimine bağlı olarak) kuralın gereksinimlerini karşılamaz.

Mali kuruluşların SEC kuralı 17a-4 gereksinimlerini karşılamasını yardımcı olmak için, Microsoft 365 verilerin nasıl korundurlandığı, ilkelerin yapılandırıldığında ve verilerin hizmet içinde depolandığıyla ilgili bir özellik birleşimi sağlar. Şunlar dahildir:

* Verilerin korunması **(Kural 17a-4(a), (b)(4))** – Bekletme etiketleri ve ilkeleri kurumsal ihtiyaçları karşılamak için esnektir ve farklı veri, belge ve bilgi türlerine otomatik olarak veya el ile uygulanabilir. SharePoint ve OneDrive İş'daki belgeler, posta kutuları içindeki veriler ve Exchange Online içindeki veriler gibi çok çeşitli veri türleri ve iletişim Teams.  
* Yeniden yazılamaz, silinebilir olmayan biçim **(Kural 17a-4(f)(2)(ii)(A))** – Bekletme ilkeleri için Saklama Kilidi özelliği, kayıt yöneticilerinin ve yöneticilerinin bekletme ilkelerini kısıtlayıcı olacak şekilde yapılandırarak artık değiştirilmeyecekleri şekilde yapılandırmalarını sağlar. Bu, bekletme ilkesini herhangi bir şekilde kaldırmasını, devre dışı bırakmasını veya değiştirmesini yasaklar. Bu, Saklama Kilidi etkinleştirildikten sonra devre dışı bırakılamayacakları ve bekletme süresi boyunca bekletme ilkesi uygulanmış olan verilerin üzerine yazılabilir, değiştirilebilir veya silinecek bir yöntem yoktur. Buna ek olarak, bekletme süresi de kısaltılmasız. Bununla birlikte, veri bekletmeye devam etmek için yasal bir zorunluluk söz konusu olduğunda bekletme süresi uzatabilirsiniz.<br/><br/>Bir bekletme ilkesine Koruma Kilidi uygulandığında, aşağıdaki eylemler kısıtlanır:

  - İlkenin bekletme süresi yalnızca artırılabilir. Kısaltılmasız.
  - Kullanıcılar ilkeye eklenebilir, ancak ilkede yapılandırılmış olan kullanıcılar kaldırılamaz.
   - Bekletme ilkesi kuruluş içindeki hiçbir yönetici tarafından silinemez.
 
  Koruma Kilidi, en yüksek ayrıcalıklı erişim düzeyine sahip yöneticiler bile kullanıcıların bile depolanmış olan ayarları değiştiremelerini, değiştirmelerini, üzerine yazmalarını veya silmelerini sağlar ve SEC 2003 Sürümünde sağlanan kılavuzla Office 365'de arşivlemeyi sağlar.

* Verilerin depolama/seri hale getirme ve dizine alma kalitesi, doğruluğu ve doğrulaması **(Kural 17a-4(f)(2) (ii)(B) ve (C))** – Office 365 iş yüklerinin her biri, depolama medyası üzerinde veri kaydetme işleminin kalitesini ve doğruluğunu otomatik olarak doğrulamak için özellikler içerir. Ayrıca veriler, verilerin etkin bir şekilde aranması ve alınması için yeterli dizin oluşturmanın sağlanması amacıyla meta veriler ve zaman damgasılar kullanılarak saklanır.
 
* Yinelenen kopyalar için ayrı depolama **alanı (Kural 17a-4(f)(3(iii))** – Office 365 bulut hizmeti, yüksek kullanılabilirliğini temel alan verilerin yinelenen kopyalarını depolar. Bu, tüm sunucularda fiziksel düzeyde, veri merkezi içindeki sunucu düzeyinde ve coğrafi olarak dağınık veri merkezlerinin hizmet düzeyinde de dahil olmak üzere hizmetin tüm düzeylerinde yedekli çalışma uygulanarak  uygulanır.

* İndirilebilir ve erişilebilir veriler **(Kural 17a-4(f)(2)(ii)(D))** – Office 365 genellikle bekletme için etiketlenmiş verilerin aranmalarına, erişildikten sonra indirilmalarına izin vermez. Ayrıca, Exchange Online eKbulma özellikleri kullanılarak Arşiv'de bulunan verilerin aranabilir olmasına da olanak sağlar. Daha sonra veriler EDRML ve PST dahil olmak üzere standart biçimlerde indirilebilir.
 
* **Denetim gereksinimleri (Kural 17a-4(f)(3)(v))** – Office 365 veri nesnelerini değiştiren, bekletme ilkelerini yapılandıran veya değiştiren, eBulma aramaları yapan veya erişim izinlerini değiştiren her yönetim ve kullanıcı eylemi için denetim günlüğü sağlar. Office 365 kimlerin eylem gerçekleştirilen, ne zaman gerçekleştirilen, eylemle ilgili ayrıntılar ve gerçekleştirilen komutlar gibi kapsamlı bir denetim izi vardır. Bundan sonra denetim günlüğü çıktısı olabilir ve gerekirse resmi denetim işlemlerinin bir parçası olarak yer almaktadır.

Son olarak, Kural 17a-4, kuruluşların birçok işlem türü için kayıt tutmalarını, böylelikle iki yıl süreyle hemen erişilebilir olmasını gerektirir. Kayıtlarda, acil olmayan erişimle birlikte üç ile altı yıl süreyle korunabilirsiniz. Yinelenen kayıtlar, site dışı bir konumda da aynı süre için tutulmalıdır. Office 365 yönetiminin bir özelliği, kayıtların değiştirilemez veya silinemez şekilde, ancak kayıt yöneticisi tarafından denetlenen bir süre kolayca erişilebiliyor olması için, kayıtların silinmesine olanak sağlar. Bu dönemler, kuruluşun mevzuata uygunluk yükümlülüklerine bağlı olarak günler, aylar veya yıllar olabilir.
 
İsteğiniz üzerine Microsoft, kuruluş tarafından gerekli olduğu şekilde SEC 17a-4 ile uyumlu olduğunu doğrulatır.

Buna ek olarak bu özellikler, Microsoft 365 Düzenleme Yetkisinde yer alan [CFTC Kuralı 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) için DEPOLAMA gereksinimlerini KARŞıLAMAnıza da yardımcı olur [](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) **.**  Bu kurallar, toplu olarak, finansal kuruluşların kayıtları tutması için global olarak en simgesel kılavuzu temsil ediyor.

Microsoft 365'nin SEC kuralı 17a-4 ile nasıl uyumlu olduğunu ve diğer yasal düzenlemelere [Cohasset Associates tarafından Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d)](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers) değerlendirme konusunda ek ayrıntılar sağlanmaktadır.

## <a name="establish-ethical-walls-with-information-barriers"></a>Bilgi engelleriyle duvarlara evriz olma

Finansal kurumlar, belirli rollerdeki çalışanların bilgi alışverişinde veya diğer rollerle işbirliği içinde yer paylaşmasını önleyen düzenlemelere tabi olabilir. Örneğin, FINRA'da üyelerin şunları gerektiren 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) ve (b)(2)(H)(iii) kurallarını yayımlanmıştır:

"(G) araştırma analistlerinin, yatırım banka hizmetleri etkinlikleriyle veya satış ve alım satım personeli dahil olmak üzere diğer kişiler tarafından gözden geçirme, baskı veya gözetimden yalıtılmış olmasını sağlamak için makul olarak tasarlanmış bilgi engellerini veya diğer kurumsal korumaları kurma ve "(H) bilgi engellerini veya diğer kurumsal korumaları makul bir şekilde tasarlar ve bu kişilerin araştırma analistlerinden yalıtılmış olmasını sağlamak için  ilgili kişilerin incelemesi, baskısı veya gözetimi: (i) yatırım banka hizmetleri; (ii) ana alım satım veya satış ve ticaret etkinlikleri; ve (iii) karar veya gözetimlerinden sapmaları olan diğer kişiler;"

Sonuçta, bu kurallar kuruluşların, analistlerle bilgi ve iletişim alışverişinde bankacılık hizmetleri, satış veya alım satım gibi roller arasında ilkeler kurmalarını ve bilgi engellerini uygulamalarını gerektirir.

[Bilgi engelleri](../compliance/information-barriers.md), Office 365 ortamınız içinde güvenli duvarlar kurabilme olanağını sağlar, uyumluluk yöneticilerinin veya diğer yetkili yöneticilerin Teams'te kullanıcı grupları arasında iletişime izin veren veya bunu engelleyen ilkeler tanımlamasına olanak sağlar. Bilgi engelleri, yetkisiz iletişimi önlemek için belirli eylemler üzerinde denetimler gerçekleştirin. Bilgi engelleri, iç ekiplerin şirket birleşmeleri/alımları veya hassas anlaşmalar üzerinde çalıştığı veya yoğun olarak kısıtlanmış olması gereken hassas iç bilgilerle çalıştığı senaryolarda da iletişimi kısıtlanabilir.

Web sayfalarında konuşmaları Microsoft 365 dosyaları desteklemeye ilişkin bilgi Teams. FinRA düzenlemelerine uymaya yardımcı olmak için aşağıdaki iletişimle ilgili işlem türlerini engellenebilir:

* Kullanıcı arama
* Ek ekipte bir üye ekleme veya ekipte başka bir üyeyle katılmaya devam
* Sohbet oturumu başlatma veya oturuma devam edin
* Grup sohbeti başlatma veya sohbete devam edin
* Birini toplantıya katılmaya davet etme
* Ekran paylaşma
* Arama yeri

## <a name="implement-supervisory-control"></a>Gözetmen denetimi uygulama

Finansal kuruluşların genellikle, çalışanların etkinliklerini izlemek ve ilgili menkul değerlerle uyumluluğu elde etmeye yardımcı olmak için kuruluşları içinde bir gözetmen işlevi kurması ve bu işlevi sürdürmesi gerekir. Özellikle, FINRA şu gözetim gereksinimlerini kurmaktadır:
 
* [FINRA Rule 3110 (Gözetim),](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) firmalardan çalışanlarının ve dahil olduğu iş türlerinin etkinliklerini denetlemeye yönelik yazılı gözetmen yordamları (WSP) gerektirir. Diğer gereksinimlere ek olarak, yordamlar şunları da içerebilir:
   - Gözetmen personelinin gözetimi
   - Firmanın yatırım bankacılığı, menkul değer işletmesi, iç iletişimleri ve iç soruşturmalarının gözden geçirme
   - Insider alım satım işlemleri için inceleme
   - Yazışma ve şikayetleri gözden geçirme

   Yordamlar incelemelerden sorumlu olan bireyleri, kişilerin gerçekleştirecekleri gözetmen etkinliğini, sıklıkları ve inceleme altındaki belge veya iletişim türlerini açıklamalı.
 
* [FINRA Rule 3120 (](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) Gözetmen Denetim Sistemi) firmanın, Kural 3110'da tanımlandığı şekilde yazılı gözetmen yordamlarını doğrulayan bir gözetmen ilkeleri ve yordamları (SCP) sistemi olmalıdır. Firmaların yalnızca WSP'lere sahip olması değil, aynı zamanda ilgili menkul değer yasalarına ve düzenlemelerine uyumluluğunu garanti etme yeteneğini doğrulamak için bu yordamları yıllık olarak test etme ilkelerine sahip olması gerekir. Test kapsamını tanımlamak için risk tabanlı metodolojiler ve örnekleme kullanılabilir. Diğer gereksinimlerin dışında, bu kural, firmalardan test sonuçlarının özetini ve test sonuçlarına yanıt olarak düzeltilen yordamları ve test sonuçlarının özetini içeren üst düzey yönetime yıllık bir rapor sağlamalarını gerektirir.

![Ofis çalışanı ekran üzerinde bir grafik ve tablolar görüntülerken, diğerleri arka planda bunu karşılar.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>İletişim uyumluluğu

Standart iletişim Microsoft 365, kuruluşların yetkili gözetmenlerin izlemesi ve gözden geçirmesi için çalışan iletişimlerini yakalamak üzere ilkeleri önceden yapılandırmalarına olanak sağlar. İletişim uyumluluğunun ilkeleri, iç/dış e-posta ve ekleri yakalamak, Teams sohbet ve kanal iletişimlerini yakalamak ve çevrimiçi Skype Kurumsal sohbet iletişimleri ve ekleri oluşturabilir. Buna ek olarak, iletişim uyumluluğu üçüncü taraf hizmetlerinden (Bloomberg, Thomson Reuters, LinkedIn, Twitter, Facebook, Box ve diğer hizmetler) iletişim ve Dropbox.
Bir kuruluş içinde yakalanması ve gözden geçirilemesi gereken iletişimlerin kapsamlı doğası ve ilkelerin yapılandırıldığı kapsamlı koşullar, finansal kuruluşların FINRA Kuralı 3110 ile uyumlu olmasına yardımcı olmak için iletişim uyumluluk ilkelerine izin verme. İlkeler, tek tek kişilerin veya grupların iletişimlerini gözden geçirmek üzere yalıtıldı.  Belirlenen gözetmenler bireysel veya grup düzeyinde atanabilir. Gelen veya giden iletiler, etki alanları, bekletme etiketleri, anahtar sözcükler veya tümcecikler, anahtar sözcük sözlükleri, hassas veri türleri, ekler, ileti boyutu veya ek boyutuna göre iletişim yakalamak üzere kapsamlı koşullar yapılandırabilirsiniz. Gözden geçirenler, bayraklı iletişimleri gözden geçirebilecekleri, ilkeleri ihlalabilecek iletişimler üzerinde eylemde olabilecek ve bayraklı öğeleri çözümlendi olarak işaretleyebilecekleri bir panoya sahip olur. Ayrıca daha önce çözümlenmiş incelemelerin ve öğelerin sonuçlarını da gözden geçirebilirler.
  
İletişim uyumluluğu, ilke gözden geçirme etkinliklerinin, ilkeye ve gözden geçirene göre denetlenesini sağlayan raporlar sağlar. Raporlar, ilkelerin kuruluşun yazılı gözetim ilkeleri tarafından tanımlandığı şekilde çalıştığını doğrulamak için kullanılabilir. Ayrıca gözden geçirme gerektiren ve şirket ilkesiyle uyumlu olmayan iletişimleri tanımlamak için de kullanılabilir. Son olarak, ilkeleri yapılandırma ve iletişimleri gözden geçirme ile ilgili tüm etkinlikler, birleşik denetim Office 365 içinde denetlenmektedir. Sonuç olarak, mali kuruluşların FINRA Kuralı 3120 Microsoft 365 e uymalarına da yardımcı olur.

FINRA kurallarına uymanın yanı sıra, iletişim uyumluluğu kuruluşların diğer yasal gereksinimlerle, kurumsal ilkelerle ve standartlarla uyumluluğunu sağlayan iletişimleri izlemelerine de olanak sağlar. İletişim uyumluluğu, iletişimleri gözden geçirme sırasında hatalı pozitif sonuç azaltmaya yardımcı olan yerleşik tehdit, taciz ve küfür sınıflayıcıları sağlar ve inceleme ve düzeltme sürecinde gözden geçirenlerin zamanlarını azaltır. Ayrıca, kuruluşların şirket birleşmeleri ve alımlar veya liderlik değişiklikleri gibi hassas değişikliklere tabi olduğunda iletişimleri izlemesi yoluyla riski azaltmasını da sağlar.

![Bir bilgi çalışanı ekrana odaklanıyor.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Veri sızıntılarına ve insider risklerine karşı koruma

Kuruluşlar için en yaygın tehdit, veri sızıntıları veya kuruluştan verileri ayıklama eylemidir. Her gün erişilebilen bilgilerin hassas yapısı nedeniyle, bu risk mali kurumlar açısından önemli bir risk olabilir. Kullanılabilir iletişim kanallarının sayısının artması ve verileri taşıma araçlarının çoğalmasıyla, veri sızıntıları, ilke ihlalleri ve insider riskini azaltmak için genellikle gelişmiş özellikler gereklidir.

### <a name="insider-risk-management"></a>Insider risk yönetimi

Her yerden erişilebilir çevrimiçi işbirliği araçlarına sahip çalışanların etkinleştirilmesi, kuruluşa yapısal olarak risk getirir. Çalışanlar saldırganlara veya rakiplere yanlışlıkla veya kötü amaçlı olarak veri sızdırıyor olabilir.  Alternatif olarak, verileri kişisel kullanım için kullanabilir veya gelecekteki işvereninizle birlikte bu veriye sahip olacak bir işverene götürebilirsiniz. Bu senaryolar, finansal hizmet kuruluşlarının hem güvenlik hem de uyumluluk açısından önemli riskler ortaya konur. Bu riskleri ne zaman oluşursa belirlemek ve onları hızla risk altında oluşturmak için, hem veri toplamaya yönelik akıllı araçlar hem de hukuk, insan kaynakları ve bilgi güvenliği gibi departmanlar arasında işbirliği gerekir.

Microsoft 365 yakın zamanda, Microsoft 365 hizmetleri genelinde sinyalleri birbiriyle ilişkili olan ve kullanıcı davranışını gizli kalıplara ve insider risk işaretlerine karşı çözümlemek için makine öğrenme modellerini kullanan bir Insider risk yönetimi çözümü başlattı. Bu araç, önceden belirlenen iş akışlarına dayalı vakaları kolayca düzeltmek için güvenlik işlemleri, şirket içi ve İk arasında işbirliğini sağlar.  

Örneğin, Microsoft 365'ta Insider risk yönetimi, bir kullanıcının Windows 10 masaüstünden gelen, usb sürücüsüne dosya kopyalama veya kişisel e-posta hesabına e-posta gönderme gibi sinyalleri Office 365 e-posta, SharePoint Online, Microsoft Teams veya OneDrive İş, filtreleme desenlerini tanımlamak için kullanın. Ayrıca bu etkinlikleri, yaygın bir veri sızıntı düzeni olan kuruluşdan ayrılmakta olan çalışanlarla da ilişkili olabilir. Zaman içinde birden çok etkinlik ve davranışı izleyebilir. Yaygın desenler ortaya çıkarsa, uyarılarda ortaya çıkabilir ve güvenlik nedeniyle ilke ihlalini doğrulamak için önemli etkinliklere odaklanmaya yardımcı olabilir. Insider risk yönetimi, veri gizliliği düzenlemelerini karşılamaya yardımcı olmak için güvenlik nedenlerinden sahte kimliksiz veriler elde edebilir ve bu yandan da incelemeleri verimli bir şekilde gerçekleştirmelerine yardımcı olan önemli etkinliklerin gizliliğini korumaya devam eder. Düzeltme eylemi durumlarını yükseltmeye yardımcı olmak için genel yükseltme iş akışlarını takip eden, İk ve hukuk departmanına önemli etkinlik verilerini paketleyen ve güvenli bir şekilde göndermek için izin verir.

Microsoft 365'de Insider risk yönetimi, kuruluşların insider risklerini izlemesi ve araştırma yeteneklerine büyük katkı sağlarken, kuruluşların veri gizliliği düzenlemelerini yine de karşılamasına ve vakaların daha üst düzey bir işlem gerektirmesi sırasında artan yolları izlemelerine olanak sağlar. Microsoft 365'ta Insider risk yönetimi hakkında daha fazla bilgi için bkz. [Modern risk noktaları ve insider risk yönetiminde iş akışı Microsoft 365](../compliance/insider-risk-management.md).

![Bir ekranı görüntülerken, küp türlerinde olan çağrı merkezi çalışanı.](../media/clo17-call-center-006.jpg)
 
### <a name="tenant-restrictions"></a>Kiracı kısıtlamaları
Hassas verilerle uğraşan ve güvenliği sıkı bir şekilde vurgu isteyen kuruluşlar normalde kullanıcıların eriş erişebilirsiniz çevrimiçi kaynakları kontrol etmek ister. Aynı zamanda, iş birliği gibi çevrimiçi hizmetler aracılığıyla güvenli bir işbirliğine de Office 365. Sonuç olarak, şirket Office 365 olmayan ortamlar kötü amaçlı veya istemeden şirket cihazlarından veri imha etmek için kullanalica olduğundan, kullanıcıların erişeb Office 365 Office 365 ortamlarını denetlemek zor olabilir. Kuruluşlar, geleneksel olarak, kullanıcıların şirket cihazlarından eriş erişeliklerini etki alanlarını veya IP adreslerini kısıtlar. Ancak bu, kullanıcıların bulut tabanlı hizmetlere yasal olarak erişmesi gereken ve dünyanın her bir Office 365 değildir.

Microsoft 365 bu [zorlukla mücadele](/azure/active-directory/manage-apps/tenant-restrictions) etme özelliği kiracı kısıtlamaları sağlar. Kiracı kısıtlamaları, çalışanlara dış veya kurumsal kiracılara erişimini kısıtlayan Office 365 kimlikler (şirket dizininizin bir parçası olmayan kimlikler) kullanarak ya da bu kiracılara yöneliktir. Bugün, kiracı genelinde geçerli olan kısıtlamalar yalnızca yapılandırılan listede görünen kiracılara erişim sağlar. Microsoft, denetim ayrıntısını artırmak ve sağladığı korumaları geliştirmek için bu çözümü geliştirmeye devam ediyor.

![GRAFIK.](../media/clo1717-corporate-office-001.jpg)
 
## <a name="conclusion"></a>Sonuç

Microsoft 365 kurumsal Teams kurumsal genelinde basit ancak güçlü bulut tabanlı işbirliği ve iletişim özelliklerini etkinleştiren finansal hizmet şirketleri için tümleşik ve kapsamlı bir çözüm sağlar. kuruluşlar Microsoft 365'tan gelen güvenlik ve uyumluluk teknolojilerini kullanarak, verileri, kimlikleri, cihazları ve uygulamaları siber güvenlik ve insider riskleri de dahil olmak üzere çeşitli faaliyet risklerinden korumak için güçlü güvenlik denetimleriyle daha güvenli ve uyumlu bir şekilde çalışabilirsiniz. Microsoft 365, finansal hizmetlerin kuruluşların şirketlerini, çalışanlarını ve müşterilerini korurken daha fazlasını başarmalarına yönelik temelden güvenli bir platform sağlar.
