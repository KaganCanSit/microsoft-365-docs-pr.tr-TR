---
title: Microsoft 365 kaynak planlama - Güvenlik mimarisi
description: Microsoft'ta Teknik Sorumlu Mimar Alex Shteynberg'Enterprise Microsoft'un en önemli tasarım stratejileri hakkında bilgi öğrenin.
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
ms.openlocfilehash: 8e24242639362bddca7540cd8dfb390b0edb5e8c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996126"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>Kimlik ve ötesine, Bir mimarın görünüm noktası

Microsoft'un Sorumlu Teknik Mimarı [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/) bu makalede, Microsoft'u ve diğer Microsoft bulut hizmetlerini benimseyen kurumsal kuruluşlar için Microsoft 365 stratejilerini ele almaktadır.

## <a name="about-the-author"></a>Yazar hakkında

![Alex Shteynberg'in fotoğrafı.](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

New York Microsoft Technology Center'da Teknik Mimar [olarak çalışıyorum](https://www.microsoft.com/mtc?rtc=1). Çoğunlukla büyük müşterilerle ve karmaşık gereksinimlerle çalışıyoruz. Görünüm noktam ve yorumlarım bu etkileşimleri temel aldı ve her durum için geçerli değildir. Ancak, benim deneyimimde, en karmaşık güçlükleri olan müşterilere yardımcı olabiliriz, tüm müşterilere yardımcı olabiliriz.

Normalde her yıl 100'den fazla müşteriyle çalışıyoruz. Her kuruluşun benzersiz özellikleri vardır, ancak eğilimleri ve yaygınlıkları görmek ilginçtir. Örneğin, bir eğilim birçok müşteri için sektörler arası ilgidir. Sonuçta, bir banka dalı bir kafe ve bir topluluk merkezi olabilir.

Rolümde, müşterilerin benzersiz iş hedefleri kümesine çözüm bulmak için en iyi teknik çözüme ulaşlarına yardımcı olmak istiyorum. Resmi olarak Kimlik, Güvenlik, Gizlilik ve Uyumluluk'a odaklan istiyorum. Bu dokunmatik ekranların tüm işlere dokunması beni çok güzeldir. Bana çoğu projeyle ilgili olarak bir fırsat sunuyor. Bu, beni çok meşgul ediyor ve bu rolün keyfini çıkar ediyor.

New York City'de (en iyi!) yaşıyorum ve kültürü, yiyecek ve insanlarının (trafik değil) farklı yerlerinin keyfini çıkarıyor. Dünyanın büyük bir tarafından yaşamımı takip etmek için seyahat etmek istiyorum. Şu anda vahşi yaşam hakkında bilgi edinmek için Afrika'ya bir seyahatte bulunuyorum.

## <a name="guiding-principles"></a>Yol gösteren ilkeler

- **Basit çoğunlukla daha iyidir**: Teknolojiyle hemen hemen her şeyi yapasiniz, ancak bunu yapmak gerektiği anlamına da değildir. Özellikle güvenlik alanı içinde, birçok müşteri aşırıya yönelik çözümler sunar. [Google'ın](https://www.youtube.com/watch?v=SOQgABDSYZE) Şerit konferansında bu videoyu takip ediyor ve bu noktaya vurgu yapmak istiyorum.
- **Kişiler, süreç, teknoloji**: [Önce teknolojinin değil](https://en.wikipedia.org/wiki/Human-centered_design) , insanların süreci geliştirmesi için tasarım. "Mükemmel" bir çözüm yoktur. Çeşitli risk faktörlerini dengelememiz gerekiyor ve kararlar her işletme için farklı olacak. Çok fazla müşteri, daha sonra kullanıcılarının kaçınılması için bir yaklaşım tasarlar.
- **Önce 'neden' ve sonra da 'nasıl'** üzerine odaklanın: Milyon soru sormak için 7 yaşında, can sıkıcı bir çocuk ola. Soracak doğru soruları bilmiyorsanız doğru yanıta ulaşaa biliyoruz. Birçok müşteri, iş sorununu tanımlamak yerine nasıl çalışması gerekir? üzerine varsayımlar sunar. Her zaman, alınan birden çok yol vardır.
- **Geçmiş en iyi yöntemleri uzun süre takip edin**: En iyi uygulamaların ışık hızında değişmektedir. Azure AD'ye üç aydan daha uzun bir süre önce baktıysanız, büyük olasılıkla güncelsinizdir. Buradaki her şey yayından sonra  değişiklik olabilir. Bugün için "En iyi" seçenek şu andan itibaren altı ay ile aynı olmayacak.

## <a name="baseline-concepts"></a>Temel kavramlar

Bu bölümü atlamayın. Uzun zamandır bulut hizmetlerini kullanan müşteriler için bile bu konulara bir adım geri dönmem gerektiğini biliyorum.
Ne yazık ki dil hassas bir araç değil. Aynı sözcüğü, farklı kavramları veya aynı kavramı farklı sözcüklerle ifade etmek için sıklıkla kullanıyoruz. Bazı taban çizgisi terminolojisi ve "hiyerarşi modeli" kurmak için bu diyagramı çoğunlukla aşağıdan kullanırız.
<br><br>

![Kiracı, abonelik, hizmet ve veriler çizimi.](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Yüzüyorken, okyanusta değil de havuza başlamanın daha iyi olduğunu öğrenirsiniz. Bu diyagramda teknik olarak doğru olmaya çalışmam. Bazı temel kavramları tartışmak bir modeldir.

Diyagramda:

- Kiracı = bir Azure AD örneği. Bir hiyerarşinin "en üstünde" veya diyagramda Düzey 1'dedir. Bunun, diğer her şeyin bulunduğu "[sınır](/azure/active-directory/users-groups-roles/licensing-directory-independence)" olduğunu düşünebiliyoruz ([Azure AD B2B dışında](/azure/active-directory/b2b/what-is-b2b) ). Tüm Microsoft kurumsal bulut hizmetleri bu kiracılardan birinin parçası. Tüketici hizmetleri birbirinden ayrıdır. Belgelerde kiracı, Azure Office 365, WVD kiracısı gibi farklı "Kiracı" görünür. Bu çeşitlemelerin çoğunlukla müşteriler için karışıklığa neden olduğunu fark ediyoruz.
- Diyagramda Düzey 2 olan Hizmetler/abonelikler, bir ve yalnızca bir kiracıya aittir. SaaS hizmetlerinin çoğu 1:1'tir ve geçiş yapmadan hareket ettir kullanılamaz. Azure farklıdır, faturalandırmayı [ve/veya](/azure/cost-management-billing/manage/billing-subscription-transfer) aboneliği başka [bir kiracıya](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) taşıabilirsiniz. Azure aboneliklerini taşıması gereken birçok müşteri vardır. Bunun çeşitli etkileri vardır. Aboneliğin dışında olan nesneler taşınmaz (örneğin, rol tabanlı erişim denetimi veya Azure RBAC ve gruplar, uygulamalar, ilkeler gibi Azure AD nesneleri). Ayrıca, bazı hizmetler de (Azure Anahtar Kasası, Veri Kasaları, vb.). İyi bir iş ihtiyacınız olmadan hizmetleri geçirmeyin. Geçiş için yararlı olacak bazı betikler bu [dosyalarda GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- Verilen hizmette genellikle bir tür "alt düzey" sınırı veya Düzey 3 (L3) vardır. Bu, güvenliğin, ilkelerin, yönetimin ve diğer ayrımların nasıl iş yarar olduğunu anlamak için kullanışlıdır. Ne yazık ki, tekdüz bir ad yok. L3 için bazı örnekler: Azure Aboneliği = [kaynak](/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [örnek](/dynamics365/admin/new-instance-management); Power BI = [çalışma alanı](/power-bi/service-create-the-new-workspaces); Power Apps = [ortam](/power-platform/admin/environments-overview), bu şekilde devam eder.
- Düzey 4, gerçek verilerin yaşadığı yerdir. Bu 'veri uçağını' karmaşık bir konu. Bazı hizmetler RBAC için Azure AD'yi kullanırken, bazıları kullanmaz. Temsilci seçme konularıyla ilgili konulara gidip bu konuyu biraz tartışacağız.

Çok sayıda müşteri (ve Microsoft çalışanı) bulamıyorum, bazı ek kavramlar kafayı karıştırılır veya aşağıdakiler hakkında sorularım olabilir:

- Herkesin hiçbir [maliyeti](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) yoktur ve çok [sayıda kiracı oluşturabilir](https://azure.microsoft.com/pricing/details/active-directory/). Bunun içinde bir hizmet sağlanmasına gerek yok. Onlarcası var. Her Kiracı adı Microsoft'un dünya çapında bulut hizmetinin benzersizdir (başka bir deyişle, iki kiracı aynı adıya sahip olabilir). Bunların hepsi tarih biçiminde TenantName.onmicrosoft.com. Kiracıları otomatik olarak (sahip olmayan kiracılar[) oluşturma işlemleri de vardır](/azure/active-directory/users-groups-roles/directory-self-service-signup). Örneğin, kullanıcı başka hiçbir kiracıda yer olmayan e-posta etki alanı olan bir kurumsal hizmete kayıt olduğunda, bu durum ortaya çıkabilir.
- Yönetilen bir kiracıda, birçok [DNS etki](/azure/active-directory/fundamentals/add-custom-domain) alanı buna kaydediliyor olabilir. Bu, özgün kiracı adını değiştirmez. Şu anda bir kiracıyı yeniden adlandırmanın (geçiş dışında) kolay bir yolu yoktur. Kiracı adı teknik olarak bu günlerde kritik öneme sahip olsa da, bazıları bunun sınırlayıcı olduğunu bulabilir.
- Henüz herhangi bir hizmeti dağıtmayı planlamamış bilesanız, organizasyon için bir kiracı adı rezerve edelesiniz. Aksi takdirde, biri onu sizin geri almak için basit bir işlem yoktur (DNS adlarından aynı sorun). Bunu müşterilerden çok sık duyuyorum. Kiracı adınız ne olmalı? konusu da tartışılan bir konudur.
- DNS ad alanlarınız varsa, bunların hepsini kiracınıza eklemeniz gerekir. Aksi takdirde, bu [adla yönetilemeyen](/azure/active-directory/users-groups-roles/directory-self-service-signup) bir kiracı oluşturabilir ve bu da yönetimin kesintiye [neden olduğunu sağlar](/azure/active-directory/users-groups-roles/domains-admin-takeover).
- DNS ad alanı (örneğin contoso.com) bir ve yalnızca bir Kiracı'ya ait olabilir. Bunun çeşitli senaryolarda (örneğin, bir birleşme veya alım sırasında e-posta etki alanı paylaşımı vb.) bir anlamı vardır. DNS alt listesini (örneğin, div.contoso.com) başka bir kiracıya kaydetmenin bir yolu var, ancak bu kayıttan kaçınılmalıdır. En üst düzey etki alanı adı kaydederek, tüm alt etki alanları aynı kiracıya ait olduğu varsayılır. Çok kiracılı senaryolarda (aşağıya bakın) Normalde başka bir üst düzey etki alanı adı (etki alanı adı veya etki alanı contoso.ch) ch-contoso.com.
- Who "sahibi" mi olmalı? Kiracılarının şu anda kimin sahibi olduğunu çoğu zaman bilmiyorum. Bu, büyük bir kırmızı bayrak. Microsoft desteğini en kısa sürede arayın. Hizmet sahibinin (genellikle kiracıyı yönetmek için Exchange yönetici olarak belirlensi), sorun olduğunda olduğu gibi. Kiracı, gelecekte istediğiniz tüm hizmetleri içerir. Kiracı sahibinin, kuruluşta tüm bulut hizmetlerinin etkinleştirilene karar verecek bir grup olması gerekir. Bir diğer sorun, kiracı sahibi grubundan tüm hizmetleri yönetmesi istenecek. Bu, büyük kuruluşlar için ölçeklendirmez.
- Alt/süper kiracı diye bir kavram yoktur. Bazı durumlarda, bu mit yine kendini gösteriyor. Bu, [Azure AD B2C kiracıları](/azure/active-directory-b2c/) için de geçerlidir. Çok fazla "B2C ortamım XYZ Kiracımda" veya "Azure kiracımı Office 365 kiracıma nasıl taşımam gerekir?"
- Çoğu müşteri bu belgeyi kullanırkenn bu belge çoğunlukla ticari dünya bulutuna odaklanır. Hakim bulutlar hakkında bilgili olmak [bazen yararlı olabilir](/azure/active-directory/develop/authentication-national-cloud). Hakim bulutların, bu tartışmanın kapsamı dışında olan konuları tartışmanın başka bir anlamı vardır.

## <a name="baseline-identity-topics"></a>Temel kimlik konuları

Microsoft'un kimlik platformu (Azure AD) hakkında Azure Active Directory belge vardır. Yeni başlayanlar için genellikle bunaltıcı bir durum olur. Bunu öğrendikten sonra bile sürekli yeniliği ve değişikliği takip etmek zor olabilir. Müşteri etkileşimlerimde çoğunlukla iş hedefleri arasında "çevirmen" olarak görev aldım ve bu konulara ilişkin "İyi, İyi, En İyi" yaklaşımları (ve insan "falez notları"). Nadiren mükemmel bir yanıt vardır ve "doğru" kararı çeşitli risk etmenlerinin dengesidir. Aşağıda, müşterilerle tartışma eğiliminde ihtiyacım olan bazı yaygın sorular ve karışıklığa neden olan sorular verilmiştir.

### <a name="provisioning"></a>Sağlama

Azure AD, kimlik dünyanız için yönetim eksikliklerini çözemmektedir! [Kimlik yönetimi](/azure/active-directory/governance/identity-governance-overview) , bulut kararlarının birbirinden bağımsız kritik bir öğesi olacaktır. Yönetim gereksinimleri zaman içinde değişir ve bu nedenle bir araç değil bir programdır.

[Azure AD Bağlan](/azure/active-directory/hybrid/whatis-azure-ad-connect) başka bir [Microsoft Identity Manager](/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) ile başka bir şey (üçüncü taraf veya özel) karşılaştırması? Gelecekte çok sorundan tasarruf edin ve Azure AD ile Bağlan. Bu araçta, müşteri yapılandırmalarını ve sürekli yapılan yenilikleri ele alan her türlü akıllı özellik vardır.

Daha karmaşık bir mimariye doğru yol alanın bazı uç örnekleri:

- Bunlar arasında ağ bağlantısı olmayan birden çok AD ormanım var. Bulut Hazırlama adlı yeni [bir seçenek vardır](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Active Directory'm yok ve yüklemek de istemiyorum. Azure AD Bağlan LDAP'den [eşitlemek üzere yapılandırabilirsiniz](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (iş ortağı gerekebilir).
- Aynı nesneleri birden çok kiracıya sağlamam gerekiyor. Bu teknik olarak desteklenen bir durum değildir, ancak "aynı" tanımına bağlıdır.

Varsayılan eşitleme kurallarını (nesneleri filtreleme, [öznitelikleri değiştirme](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering), [diğer](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized) oturum açma kimliği gibi [)](/azure/active-directory/hybrid/plan-connect-userprincipalname) özelleştirmeli miyim? Kaçının! Kimlik platformu ancak onu kullanan hizmetler kadar değerlidir. Her türlü sonda yapılandırmayı yapsanız da, uygulamaları üzerindeki etkisine bakmak için bu soruyu yanıtlayın. Posta özelliği etkin nesneleri filtrelersanız çevrimiçi hizmetler için GAL eksik olur; Uygulama belirli özniteliklere dayanıyorsa, bunlara filtre uygulamanın öngörülemez bir etkisi olur; gibi diğer tüm ifadeleri de okur. Bu bir kimlik ekibi kararı değildir.

XYZ SaaS, Just-in-Time (JIT) hazırlamayı destekler; neden eşitlememi gerekli kıyorsunuz? Yukarıya bakınız. Birçok uygulamanın işlevler için "profil" bilgilerine ihtiyacı vardır. Posta özelliği etkin tüm nesneler kullanılamıyorsa GAL'niz kullanılamaz. Aynı durum, Azure AD [ile tümleştirilmiş](/azure/active-directory/app-provisioning/user-provisioning) uygulamalarda kullanıcı hazırlama için de geçerlidir.

### <a name="authentication"></a>Kimlik Doğrulama

[Parola karması eşitlemesi](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (PHS) ile [federasyon karşılaştırması](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) ve geçişli kimlik [doğrulaması](/azure/active-directory/hybrid/how-to-connect-fed-compatibility) (PTA)

Genellikle federasyon konusunda tutkulu [bir tartışma](/azure/active-directory/hybrid/choose-ad-authn) var. Basit çoğunlukla daha iyidir ve dolayısıyla bunu yapmak için iyi bir nedenniz yoksa PHS kullanın. Ayrıca, aynı kiracıda yer alan farklı DNS etki alanları için farklı kimlik doğrulama yöntemleri yapılandırabilirsiniz.

Bazı müşteriler federasyon + PHS'yi temel olarak şu türler için etkinleştirir:

- Federasyon hizmeti [kullanılamıyorsa](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) geri dönme (olağanüstü durum kurtarma için) seçeneği.
- Ek özellikler (örneğin: [Azure AD DS](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) ve güvenlik hizmetleri (sızdırılmış [kimlik bilgileri](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Federasyon kimlik doğrulamasını anlamayan Azure hizmetleri için destek (örneğin, [Azure Dosyaları](/azure/storage/files/storage-files-active-directory-overview)).

Bazı yanlışlıkları netleştirmek için müşterilere genellikle istemci kimlik doğrulaması akışında yol sunarum. Sonuç aşağıdaki resim gibi görünüyor, bu da etkileşimli oraya varma işlemi kadar iyi değil.

![Örnek beyaz tahta görüşmesi.](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Bu tür beyaz tahta çizimleri, kimlik doğrulama isteği akışı içinde güvenlik ilkelerinin nereye uygulandığını belirtir. Bu örnekte, Active Directory Federasyon Hizmeti (AD FS) aracılığıyla zorunlu kılınan ilkeler ilk hizmet isteğine uygulanır, ancak izleyen hizmet isteklerine uygulanmaz. Bu, güvenlik denetimlerini mümkün olduğunca fazla buluta taşımanın en az bir nedenidir.

Anımsayladığım kadar uzun [süredir çoklu oturum açma](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) hayali için hayalimiz devam ediyor. Bazı müşteriler, "doğru" federasyon (STS) sağlayıcısını seçerek bunu başaracaklarını inanıyorlar. Azure AD, [SSO özelliklerini etkinleştirmeye önemli](/azure/active-directory/manage-apps/plan-sso-deployment) ölçüde yardımcı olabilir ama STS'nin hiçbir şey harika olmadığını sağlar. Kritik uygulamalarda hala kullanılan çok fazla "eski" kimlik doğrulama yöntemi vardır. Azure AD'nin iş [ortağı çözümleriyle genişlet](/azure/active-directory/saas-apps/tutorial-list) süresinin genişlet çözümü, bu senaryoların birçoğuna yönelik olabilir. SSO bir strateji ve bir yolculuktur. Uygulama standartlarına uygun hareket etmeden buraya [varaasiniz](/azure/active-directory/develop/v2-app-types). Bu konu ile ilgili olarak, parolasız kimlik [doğrulamaya](/azure/active-directory/authentication/concept-authentication-passwordless) yönelik bir seyahat vardır ve bu da sihirli bir yanıtı yok.

[Multi factor authentication](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) bugün çok önemlidir ([daha fazlası](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) için burada). Kullanıcı davranışı [analizine ekleyin;](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) en yaygın siber saldırıları engelleyen bir çözümünüz olur. Tüketici hizmetleri bile MFA gerektirmeye neden oluyor. Yine de modern kimlik doğrulama yaklaşımlarını taşımak istemeyen birçok [müşteriyle tanışmaya](../enterprise/hybrid-modern-auth-overview.md) devam ediyoruz. En büyük bağımsız değişken, bunun kullanıcıları ve eski uygulamaları etkilemesidir. Bazen iyi bir harekete geç de olabilir ve duyurulanın değişiklikler Exchange Online [olabilir](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282). Müşterilere bu [geçişte](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) yardımcı olmak için çok sayıda Azure AD raporu sunulmaktadır.

### <a name="authorization"></a>Yetkilendirme

[Wikipedia başına](https://en.wikipedia.org/wiki/Authorization), "yetki vermek" bir erişim ilkesi tanımlamaktır. Buna, birçok kişi nesne (dosya, hizmet vb.) için erişim denetimlerini tanımlayabilme özelliği olarak bakar. Siber tehditlere karşı geçerli dünyada, bu kavram hızla çeşitli tehdit vektörlerine tepki ve bunlara yanıt olarak erişim denetimlerini ayarlay bir dinamik ilkeye geliştiriyor. Örneğin, banka hesabıma olağandışı bir konumdan erişerim, ek onay adımları alırsınız. Bu yaklaşım için, sadece ilkenin kendisini değil tehdit algılama ve sinyal korelasyon metodolojilerinin ekosistemini de göz önünde bulunduracağız.

Azure AD'nin ilke altyapısı Koşullu Erişim ilkeleri [kullanılarak uygulanır](/azure/active-directory/conditional-access/overview). Bu sistem, dinamik kararlar almak için çeşitli diğer tehdit algılama sistemlerinden gelen bilgilere bağlıdır. Basit bir görünüm aşağıdaki çizime benzer:

![Azure AD'de ilke altyapısı.](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

Tüm bu sinyalleri bir araya getiren bu tür dinamik ilkeler, şöyle dinamik ilkelere olanak sağlar:

- Aygıtınızda bir tehdit algılanırsa, verilere erişiminiz yalnızca indirme özelliği olmadan web'e azaltıldı.
- Olağandışı bir yüksek hacimde veri indirirken indiren her şey şifrelenir ve kısıtlanır.
- Bir hizmete unmanageed bir cihazdan erişinse çok hassas veriler engellenir, ancak başka bir konuma kopyalama olanağı olmadan kısıtlanmamış verilere erişme izni verilir.

Bu genişletilmiş yetkilendirme tanımını kabul ediyorsanız, ek çözümler uygulamalı gerekir. Hangi çözümlerin uygulanmasını istediğiniz, ilkenin ne kadar dinamik olması istediğinize ve hangi tehditleri önceliklendirmek istediğinize bağlıdır. Bu tür sistemlere bazı örnekler:

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Kimlik için Microsoft Defender](/azure-advanced-threat-protection/)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Office 365 için Microsoft Defender](../security/office-365-security/defender-for-office-365.md)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/) (Bulut Uygulamaları için Defender)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Microsoft Bilgi Koruması](../compliance/information-protection.md) (MIP)
- [Microsoft Sentinel](/azure/sentinel/)

Kuşkusuz, Azure AD'nin yanı sıra, çeşitli hizmet ve uygulamaların da kendi özel yetkilendirme modelleri vardır. Bunların bazıları daha sonra temsilci bölümünde ele alınmıştır.

### <a name="audit"></a>Denetim

Azure AD'nin [ayrıntılı denetim ve raporlama](/azure/active-directory/reports-monitoring/) özellikleri vardır. Ancak, güvenlik kararları almak için gereken tek bilgi kaynağı çoğunlukla bu değildir. Bu konu hakkında daha fazla tartışmaya temsilci bölümünde bakın.

## <a name="theres-no-exchange"></a>Herhangi bir Exchange

Paniğe kapma! Bu, Exchange veya kullanımdan SharePoint anlamına değildir. Hala temel bir hizmettir. Bir süredir teknoloji sağlayıcıları, birden çok hizmet bileşenlerini kapsayacak şekilde kullanıcı deneyimlerinden (UX) geçiş yaptı. Modern Microsoft 365 örneğin, e-posta ekleri SharePoint[](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC) Online'da veya başka bir OneDrive İş.

![E-postaya dosya ekleme.](../media/solutions-architecture-center/modern-attachments.png)

Outlook istemcisine bakarak, bu deneyimin bir parçası olarak "bağlı" olan birçok hizmeti görebilir, yalnızca Exchange. Bu gruplar Azure AD, Microsoft Arama, Uygulamalar, Profil, uyumluluk ve diğer Office 365 içerir.

![Outlook ile çağrı arabirimi.](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

Yaklaşan [Microsoft Akıcı Çerçeve](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) önizlemesi hakkında bilgi okuyun. Şu anda önizlemede, konuşmaları doğrudan doğrudan Teams ve yanıt Outlook. Aslında, Teams [istemcisi](https://products.office.com/microsoft-teams/download-app) bu stratejinin en göze çarpan örneklerindendir.

Genel olarak, Microsoft bulutlarında yer alan diğer hizmetlerle Office 365 net bir çizgi çizmek zorlaşır. Tek bir bileşen kullansalar bile, tüm bizlerde yapılan tüm yeniliklerden yararlanamalarını sağlamak için bu bilgileri müşteriler için büyük bir avantaj olarak görmek istiyorum. Oldukça harika ve birçok müşteri için çok fazla şey var.

Bugün, birçok müşteri IT gruplarının "ürünler" çevresinde yapılandırılmış olduğunu gördüm. Belirli her ürün için bir uzmana ihtiyacınız olduğu için şirket içi dünya için mantıklıdır. Ancak, bu hizmetler buluta taşındığında bir Active Directory veya veri Exchange hata ayıklamak zorunda değilim. Otomasyon (bulutun ne tür olduğu), bazı yinelenen el ile işleri kaldırır (bkz. tamam. Bununla birlikte, hizmetler arası etkileşimi, etkiyi, iş gereksinimlerini ve daha fazlasını anlamak için bunlar daha karmaşık gereksinimlerle değiştirilir. Öğrenmek için hazırsanız [,](/learn/) bulut dönüşümü tarafından etkinleştirilen harika fırsatlar vardır. Teknolojiye atlamadan önce, müşterilerle genellikle, IT becerileri ve ekip yapılarında yapılan değişikliği yönetme hakkında konuşuyoruz.

Tüm diğer SharePoint ve geliştiriciler için lütfen "SharePoint'de çevrimiçi olarak XYZ'i nasıl yapabilirim?" SharePoint durdurun. İş [Power Automate](/power-automate/) (veya Flow) kullanın, çok daha güçlü bir platformdur. 500 K öğe listeniz için daha iyi bir UX oluşturmak üzere [Azure Bot Framework](/azure/bot-service/) kullanın. CSOM [yerine Microsoft Graph'i](https://developer.microsoft.com/graph/) kullanmaya başlama. [Microsoft Teams](/MicrosoftTeams/Teams-overview) dünya SharePoint başkalarını da içerir. Liste başka örnekler de var. Orada muazzam ve olağanüstü bir evren var. Kapıyı açın [ve keşfetmeye başlayabilirler]().

Diğer yaygın etki uyumluluk alanındadır. Bu hizmet arası yaklaşım birçok uyumluluk ilkelerinin tamamen kafanızı karıştırıyor gibi görünüyor. "Bir eBulma sistemiyle tüm e-posta iletişimlerini günlüğü tutmam gerekiyor" ifadesinin yer alan kuruluşlara sürekli olarak bak görüyorum. E-posta artık yalnızca e-posta değil diğer hizmetlere açık bir pencere olduğunda, bu durum gerçekten ne anlama geliyor? Office 365 bir uyumluluk yaklaşımı [benimser](../compliance/index.yml), ancak kişiler ve süreçleri değiştirmek çoğunlukla teknolojiden çok daha zordur.

Başka birçok kişi vardır ve sürecin bir anlamı vardır. Bana göre bu kritik ve tartışılan bir alandır. Belki başka bir makalede daha fazla bilgi bulabilirsiniz.

## <a name="tenant-structure-options"></a>Kiracı yapısı seçenekleri

### <a name="single-tenant-vs-multi-tenant"></a>Tek kiracı ve birden çok kiracı

Genel olarak, çoğu müşteride tek bir üretim kiracısı olması gerekir. Birden çok kiracının zor olduğu (zor bir arama [Bing) veya](https://www.bing.com/search?q=office%20365%20multiple%20tenants) bu teknik [yazıyı okumanın birçok nedeni vardır](https://aka.ms/multi-tenant-user). Aynı zamanda, birlikte İşletmem olan birçok kurumsal müşteri, öğrenme, test ve denemeler için başka bir (küçük) kiracıya sahip. Azure Lighthouse ile kiracılar arasında Azure erişimi [daha kolay olur](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 SaaS hizmetlerinin ve diğer birçok hizmetin kiracılar arası senaryolar için sınırları vardır. [Azure AD B2B senaryolarında göz önünde bulundurabilirsiniz](/azure/active-directory/b2b/what-is-b2b).

Birçok müşteri bir birleşme ve alımdan (M&A) sonra birden çok üretim kiracısına sahip olur ve birleştirme yapmak ister. Bugün basit değil ve Microsoft Consulting Services (MCS) ya da bir iş ortağı ve üçüncü taraf yazılımı gerektirir. Gelecekte çok kiracılı müşterilerle ilgili çeşitli senaryoları ele alan sürekli mühendislik çalışmaları devam ediyor.

Bazı müşteriler birden fazla kiracıyla devam etmek ister. Bu çok dikkatli bir karar ve neredeyse her zaman iş nedeni odaklı olmalıdır! Bazı örnekler şunlardır:

- Farklı varlıklar arasında kolay işbirliğinin gerekli olmadığını ve güçlü bir yönetim ve başka bir yalıtım ihtiyacının bulunduğu, holding türünde bir şirket yapısı.
- Bir alımdan sonra, iki varlığı ayrı tutmak için bir iş kararı alınması gerekir.
- Müşterinin üretim ortamını değiştirmeyen bir ortamın benzetimi.
- Müşteriler için yazılım geliştirme.

Bu çok kiracılı senaryolarda, müşteriler çoğunlukla kiracılar genelinde bazı yapılandırmaları aynı tutmak veya yapılandırma değişiklikleriyle borçları rapor etmek ister. Bu çoğunlukla el ile yapılan değişikliklerden kod olarak yapılandırmaya ilerlemek anlamına gelir. Microsoft Premiere desteği, şu genel IP: temel alarak bu tür gereksinimler için bir atölye sunar. <https://Microsoft365dsc.com>

### <a name="multi-geo"></a>Multi-Geo

[Multi-Geo'ya](../enterprise/microsoft-365-multi-geo.md) veya Multi-Geo'ya değil, bu kadarı yeterli olabilir. Birden Office 365 Multi-Geo ile, veri yerleşim gereksinimlerini karşılamayı seçtiğiniz coğrafi konumlarda verilerin orada sağlanmasını ve [depolansını sabilirsiniz](../enterprise/o365-data-locations.md). Bu özellik hakkında birçok yanlış anlama vardır. Şunları unutmayın:

- Performans avantajlarını sağlamak için değildir. Ağ tasarımı doğru değilken performansı [kötüleştirmeye](https://aka.ms/office365networking) neden olabilir. Cihazları Microsoft ağına "kapat" edin (verileriniz için gerekli olmayabilir).
- GDPR uyumluluğu için çözüm [değildir](https://www.microsoft.com/trust-center/privacy/gdpr-overview). GDPR, veri bağımsızlığı veya depolama konumlarına odaklanmaz. Bunun için başka uyumluluk çerçeveleri de vardır.
- Yönetim temsilcilerini (aşağıya bakın) veya bilgi [engellerini çözmez](../compliance/information-barriers.md).
- Çok kiracılı ile aynı değildir ve ek kullanıcı [sağlama iş akışları](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) gerektirir.
- Kiracınız [(Azure](../enterprise/moving-data-to-new-datacenter-geos.md) AD) başka bir coğrafyaya taşınmaz.

## <a name="delegation-of-administration"></a>Yönetim temsilcisi seçme

Büyük kuruluşların çoğunda, görevlerin ve rol tabanlı erişim denetimlerinin ayrımı (RBAC) gerekli bir gerçekliktir. Daha önce özür dileriz. Bu, bazı müşterilerin yapmak istemesi kadar basit değildir. Müşteri, yasal, uyumluluk ve diğer gereksinimler farklı ve bazen dünyanın her yerine çakışıyor. Basitlik ve esneklik çoğunlukla birbirinin karşı taraflarındadır. Yanlış bir şey yapma, bu işte daha iyi bir iş yapabiliriz. Zaman içinde önemli geliştirmeler oldu (ve olacak). 379230 belgeleri okumadan iş gereksinimlerinize uygun modelin çalışması için yerel [Microsoft](https://www.microsoft.com/mtc) Teknoloji Merkezi'nizi ziyaret edin! Burada, bunun neden bu şekilde değil de, ne üzerinde düşünmem gerektiğine odaklanın. Aşağıda plan yapmak için beş farklı alan ve karşılaştığım yaygın sorulardan bazıları yer almaktadır.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>Azure AD ve Microsoft 365 merkezleri

Uzun ve büyüyen yerleşik roller [listesi vardır](/azure/active-directory/roles/permissions-reference). Her rol, belirli eylemlerin gerçekleştirile izin vermek için birlikte gruplandı olan rol izinleri listesinden oluşur. Bu izinleri her rolün içindeki "Açıklama" sekmesinde görebilirsiniz. Alternatif olarak, Merkezi'nde bunların daha insan okunabilir sürümünü Microsoft 365 Yönetici. Yerleşik rollerin tanımları değiştirilemez. Genel olarak, bunları üç kategori olarak gruplayın:

- **Genel yönetici**: Bu "tüm güçlü" rol, aynı [diğer sistemlerde](../enterprise/protect-your-global-administrator-accounts.md) olduğu gibi yüksek düzeyde korumalıdır. Tipik öneriler şunlardır: kalıcı atama yok ve Azure AD Privileged Identity Management (PIM), güçlü kimlik doğrulaması gibi bilgileri kullanma. İlginçtir ki, bu rol varsayılan olarak her şeye erişim vermez. Genellikle, daha sonra tartışılan uyumluluk erişimi ve Azure erişimi konusunda karışıklığa neden olur. Bununla birlikte, bu rol her zaman kiracının diğer hizmetlere erişim atamaktadır.
- **Belirli hizmet yöneticileri**: Bazı hizmetler (Exchange, SharePoint, Power BI gibi) Azure AD'den üst düzey yönetim rollerini tüketir. Bu tüm hizmetlerde tutarlı değildir ve daha sonra ele alınacak, hizmete özgü daha çok rol vardır.
- **İşlevsel**: Belirli işlemlere (konuk davetlisi, vb.) odaklanan uzun (ve büyüyen) bir roller listesi vardır. Düzenli aralıklarla, müşteri ihtiyaçlarına bağlı olarak bunların daha fazlası eklenir.

Her şeyi temsil etmek mümkün değildir (boşluk kısalsa da), bu da Genel yönetici rolünün bazen kullanılmalıdır anlamına gelir. Kişiler bu rolün üyeliği yerine kod ve otomasyon yapılandırması dikkate alınmalıdır.

**Not**: Microsoft 365 yönetim merkezi kullanıcı dostu bir arabirime sahiptir, ancak Azure AD yönetici deneyimine göre özellikler alt kümesine sahiptir. Her iki portal da aynı Azure AD rollerini kullanır, dolayısıyla değişiklikler aynı yerde ortaya çıkana kadar devam eder. İpucu: Azure dağınıklığı olmaksızın kimlik yönetimi odaklı bir yönetici arabirimi kullanmak için kullanıcı arabirimini kullanın <https://aad.portal.azure.com>.

Adın içinde ne var? Rolün adıyla varsayımlar yapma. Dil çok hassas bir araç değildir. Amaç, hangi rollerin gerektiğine bakmadan önce temsilci seçileri olması gereken işlemleri tanımlamaktır. "Güvenlik Okuyucu" rolüne birisini eklemek, her şeyin güvenlik ayarlarını görmelerine neden olmaz.

Özel roller [oluşturabilme özelliği yaygın](/azure/active-directory/users-groups-roles/roles-custom-overview) bir soru olabilir. Bu, bugün Azure AD'de sınırlıdır (aşağıya bakın) ancak zamanla yetenekleriniz artacak. Bunların Azure AD'nin işlevleri için geçerli olduğunu düşünüyorum ve hiyerarşi modelini "aşağı" ya da "aşağı" yaymayabilirsiniz (yukarıda ele alınmıştır). "Özel" ile her başa çıksam, "basit olan daha iyidir" anaparama geri dönme eğiliminde olurum.

Bir dizinin alt kümesinde rollerin kapsamını belirleyebilirsiniz. Örneğin, "Yalnızca AB'de kullanıcılar için yardım masası Yöneticisi"ne benzer. [Yönetim Birimleri](/azure/active-directory/users-groups-roles/directory-administrative-units) (AU) bunu ele almayı amaçlar. Yukarıda olduğu gibi, bunların Azure AD'nin işlevleri için geçerli olduğunu düşünüyorum ve "aşağı" yayılmayabilirsiniz. Elbette bazı rollerin kapsamları anlamlı değildir (genel yöneticiler, hizmet yöneticileri vb.).

Bugün, tüm bu roller doğrudan üyelik (veya [Azure AD PIM](/azure/active-directory/privileged-identity-management/) kullanıyorsanız dinamik atama) gerektirir. Bu da, müşterilerin bunları doğrudan Azure AD'de yönetmesi ve güvenlik grubu üyeliğine dayalı olamazları anlamına gelir. Bunları yönetmek için yükseltilmiş haklarla çalışması gereken betikler oluşturmanın bir fanı değilim. Genel olarak ServiceNow gibi süreç sistemleriyle API tümleştirmesini veya Saviynt gibi iş ortağı yönetim araçlarını kullanmalarını öneriyorum. Bu iş için zamanla ilgili mühendislik çalışmaları devam ediyor.

[Azure AD PIM'den birkaç](/azure/active-directory/privileged-identity-management/) kez bahsedildi. Şirket içi denetimler Microsoft Identity Manager (MIM) [Privileged Access Management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) (PAM) çözümü ile ilgili bir çözüm vardır. Ayrıca Ayrıcalıklı Erişim İş Istasyonu ( [PAWs](/windows-server/identity/securing-privileged-access/privileged-access-workstations) ) ve [Azure AD Kimlik Yönetimi'ne de bakabilirsiniz](/azure/active-directory/governance/identity-governance-overview). Aynı zamanda, tam zamanında, yeterli sayıda dinamik rol yükseltmesine olanak sağlayan çeşitli üçüncü taraf araçları da vardır. Bu genellikle, ortamın güvenliğini sağlamak için yapılan daha büyük tartışmaların bir parçası olur.

Bazen senaryolar, bir role dış kullanıcı eklemeyi çağrır (yukarıdaki çok kiracılı bölüme bakın). Bu da tamam. [Azure AD B2B](/azure/active-directory/b2b/) , belki de başka bir makalede, müşterilere yol tavsiye etmek için büyük ve eğlenceli bir konudur.

### <a name="security-and-compliance-center-scc"></a>Güvenlik ve Uyumluluk Merkezi (SCC)

[Güvenlik ve Uyumluluk Office 365'& Office 365 İzinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md), Azure AD rollerinden ayrı ve ayrı olan bir "rol grupları" koleksiyonudur. Bu rol gruplardan bazıları Azure AD rollerinden (örneğin, Güvenlik Okuyucu) aynı adıya sahip olduğu için kafa karıştırıcı olabilir, ancak farklı üyelikleri de olabilir. Azure AD rollerinin kullanımını tercih ederim. Her rol grubu bir veya birden çok "rolden" (aynı sözcüğü yeniden kullanmanın ne anlama gelir? ifadesine bakın) ve üyeleriniz azure AD'den (e-posta özelliği etkin nesneler) oluşur. Ayrıca, rolle aynı adı alan ve bu rolü içere bir rol de içere bir rol grubu oluşturabilirsiniz (bu karışıklıktan kaçının).

Bir bakıma, bunlar en iyi rol Exchange bir gelişmedir. Bununla birlikte, Exchange Online kendi [rol grubu yönetim arabirimi](/exchange/permissions-exo) vardır. Exchange Online'daki bazı rol grupları kilitlenir ve Azure AD'den veya Güvenlik & Uyumluluk Merkezi'nden yönetilir, ancak diğerleri de aynı veya benzer adlara sahip olabilir ve Exchange Online (karışıklığa neden olarak) yönetilebilir. Kullanıcı yönetimiyle ilgili kapsamlara Exchange Online yoksa, kullanıcı arabirimini Exchange öneririz.

Özel roller oluşturayaasiniz. Roller Microsoft tarafından oluşturulan hizmetlere göre tanımlanır ve yeni hizmetler geldikçe büyür. Bu, kavram olarak Azure [AD'de uygulamalar tarafından tanımlanan rollere](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) benzer. Yeni hizmetler etkinleştirildiğinde, bu hizmetlere erişim vermek veya temsilci temsilciliği vermek için çoğunlukla yeni rol gruplarının oluşturulmuş olması gerekir (örneğin, [Insider risk yönetimi](../compliance/insider-risk-management-configure.md)).

Bu rol grupları doğrudan üyelik de gerektirir ve Azure AD gruplarını içeramaz. Ne yazık ki, bugün bu rol grupları Azure AD PIM tarafından desteklenmiyor. Azure AD rolleri gibi, BEN de API'ler veya Saviynt gibi bir iş ortağı yönetim ürünü aracılığıyla bunların yönetimini öner ediyorum.

Güvenlik & Uyumluluk Merkezi rolleri Microsoft 365 etki alanınız vardır ve bu rol gruplarının kapsamını ortamın bir alt kümesini (Azure AD'de yönetim birimleriyle vb.) kapsamında bulunduramazsınız. Birçok müşteri, nasıl alt izin alıkattır olduklarını sorar. Örneğin, "yalnızca AB kullanıcıları için bir DLP ilkesi oluşturun." Bugün, Güvenlik ve Uyumluluk Merkezi'nde belirli bir işlevin & varsa, kiracıda bu işlevin kapsaladığı her şeye haklara sahipsinizdir. Bununla birlikte, birçok ilkenin ortamın bir alt kümesini hedef alan özellikleri vardır (örneğin, "bu [etiketlerin yalnızca](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) bu kullanıcılar tarafından kullanılabilir durumda olmalıdır") Düzgün yönetim ve iletişim, çakışmaları önlemenin önemli bir bileşenidir. Bazı müşteriler, Güvenlik ve Uyumluluk Merkezi'nde alt teslime karşı "kod olarak yapılandırma" & tercih eder. Bazı hizmetler alt teslimi destekler (aşağıya bakın).

Şu anda Güvenlik & Uyumluluk Merkezi (protection.office.com) aracılığıyla yönetilen denetimlerin iki ayrı yönetim portalına geçirilirken olduğunu security.microsoft.com compliance.microsoft.com. Değişiklik, tek sabittir!

### <a name="service-specific"></a>Hizmete Özgü

Daha önce de belirtildiği gibi, birçok müşteri daha ayrıntılı bir temsilci modeli elde etmek için arıyor. Yaygın bir örnek: "Yalnızca Bölüm X kullanıcıları ve konumları için XYZ hizmetini yönetin" (veya başka bir boyut). Bunu yapabilme özelliği her hizmete bağlıdır ve hizmetler ve özellikler arasında tutarlı değildir. Buna ek olarak, her hizmetin ayrı ve benzersiz bir RBAC modeli olabilir. Bunların hepsini tartışmak yerine (sonsuza kadar sürer), her hizmet için ilgili bağlantılar ekliyorum. Bu tam bir liste değildir, ancak hemen çalışmaya başlamanız gerekir.

- **Exchange Online** - (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** - (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **eBulma** - (.. /compliance/index.yml)
  - **İzin Filtreleme** - (.. /compliance/index.yml)
  - **Uyumluluk Sınırları** - (.. /compliance/set-up-compliance-boundaries.md)
  - **Advanced eDiscovery** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multi-geo** - (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** – (/dynamics365/)

  Not: Bu bağlantı, belge kökünün bağlantısıdır. Yönetici/temsilci modelinde çeşitlemeler içeren birçok hizmet türü vardır.

- **Power Platform** - (/power-platform/admin/admin-documentation)
  - **Power Apps** - (/power-platform/admin/wp-security)

    Not: Yönetici/temsilci modellerinde çeşitleme içeren birden çok tür vardır.

  - **Power Automate** - (/power-automate/environments-overview-admin)
  - **Power BI** - (/power-bi/service-admin-governance)

    Not: Veri platformu güvenliği ve temsilcisi (Power BI bileşenidir) karmaşık bir alandır.

- **MEM/Intune** - (/mem/intune/fundamentals/role-based-access-control)
- **Uç Nokta için Microsoft Defender** - (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Bulut Uygulamaları için Microsoft Defender** - (/cloud-app-security/manage-admins)
- **Stream** - (/stream/assign-administrator-user-role)
- **Bilgi engelleri** - (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Etkinlik Günlükleri

Office 365 bir denetim [günlüğü var](../compliance/search-the-audit-log-in-security-and-compliance.md). Bu çok ayrıntılı [bir günlüktir](/office/office-365-management-api/office-365-management-activity-api-schema), ancak adını fazla okumayın. Güvenlik ve uyumluluk 2013 için istediğiniz veya gereken her şeyi içerene kadar içerebilir. Ayrıca, bazı müşteriler Gelişmiş Denetim ile [gerçekten ilgileniyor](../compliance/advanced-audit.md).

Diğer API'Microsoft 365 erişilen günlüklere örnek olarak şunlar yer içerir:

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (diğer adlarla ilgili Office 365)
- [Exchange İzleme](/powershell/module/exchange/get-messagetrace)
- Yukarıda adı geçen Tehdit/UEBA Sistemleri (örneğin, Azure AD Kimlik Koruması, Bulut Uygulamaları için Microsoft Defender, Uç Nokta için Microsoft Defender, gibi)
- [Microsoft bilgi koruması](../compliance/data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Öncelikle, bir güvenlik ve uyumluluk programı için gereken tüm günlük kaynaklarını tanımlamak önemlidir. Ayrıca, farklı günlüklerin farklı satır üzerinde bekletme sınırları olduğunu unutmayın.

Yönetici temsilcisi açısından bakıldığında, Microsoft 365 günlüklerinin çoğunda yerleşik bir RBAC modeli yoktur. Bir günlüğü görme izniniz varsa, günlüğün içinde yer alan her şeyi görme iznine sahipsinizdir. Müşteri gereksiniminin yaygın bir örneği: "Yalnızca AB kullanıcıları için etkinliği sorgulay bilmek istiyorum" (veya başka bir boyut). Bu gereksinimi karşılamak için günlükleri başka bir hizmete aktarmamız gerekir. Microsoft bulutunda, bu aracı [Microsoft Sentinel](/azure/sentinel/overview) veya [Log Analytics'e aktarmanızı öneririz](/azure/azure-monitor/learn/quick-create-workspace).

Üst düzey diyagram:

![güvenlik ve uyumluluk programı için günlük kaynaklarının diyagramı.](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Yukarıdaki diyagram, Etkinlik Merkezi'ne ve/veya Azure Günlük Çözümlemesi'ne ve/veya Azure Depolama günlükleri göndermeye yönelik yerleşik özellikleri temsil eder. Tüm sistemler bu ilk önce dahil değildir. Ancak bu günlükleri aynı depoya göndermek için başka yaklaşımlar da vardır. Örneğin, Microsoft [Sentinel ile Teams koruma makalenize bakın](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

Tüm günlükleri tek bir depolama konumda birleştirerek çapraz korelasyonlar, özel bekletme süreleri, RBAC modelini desteklemek için gereken verilerle birleştirme gibi ek avantaj da vardır. Veriler bu depolama sistemine olduktan sonra, uygun bir RBAC Power BI görsel öğe (veya başka bir görsel öğe türü) ile bir pano oluşturabilirsiniz.

Günlükler yalnızca tek bir yere yönlendirilenler değildir. Ayrıca bu günlükleri, Office 365'de Bulut Uygulamaları [için Microsoft Defender ile veya](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) özel bir RBAC modeliyle tümleştirin [Power BI](../admin/usage-analytics/usage-analytics.md). Farklı depoların farklı avantajları ve izleyicileri vardır.

Güvenlik, tehdit, güvenlik açıkları gibi çok zengin bir yerleşik çözümleme sistemi olduğunu ve Microsoft 365 Defender adlı bir hizmette olduğunu [da Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

Birçok büyük müşteri bu günlük verilerini bir üçüncü taraf sisteme (örneğin, SIEM) aktarmayı istiyor. Bunun için farklı yaklaşımlar vardır, ancak genel olarak Azure Etkinlik [Merkezi](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) [ve](/graph/security-integration) Graph iyi başlangıç noktalarıdır.

### <a name="azure"></a>Azure

Azure AD, Azure ve SaaS arasında yüksek ayrıcalık rollerini ayırmanın bir yolu olup olmadığını sıkça sorulan bir soru vardır (örneğin: Office 365 için Genel Yönetici ancak Azure değil).  Aslında değil.  Yönetimde tam bir ayırma gerekirse çok kiracılı mimari gerekir, ancak bu önemli bir [karmaşıklık sağlar](https://aka.ms/multi-tenant-user) (yukarı bakın). Tüm bu hizmetler aynı güvenlik/kimlik sınırının bir parçası (yukarıdaki hiyerarşi modeline bakın).

Aynı kiracıda yer alan çeşitli hizmetler arasındaki ilişkilerin anlamak önemlidir. Azure, Office 365 ve Power Platform'a (ve çoğunlukla şirket içi ve üçüncü taraf bulut hizmetlerine) yayılan iş çözümleri geliştiriyor olan birçok müşteriyle çalışıyorum. Yaygın bir örnek:

1. Bir dizi belge/resim/vb. üzerinde işbirliği yapmak istiyorum (Office 365)
2. Her birini bir onay işlemi aracılığıyla gönderme (Power Platform)
3. Tüm bileşenler onaylandıktan sonra bunları birleşik bir teslim edilebilir(ler) (Azure) [Microsoft Graph API'sinde](/azure/active-directory/develop/microsoft-graph-intro) bir araya Graph bunlar için en iyi dostunuz olur.  Olanaksız değil, ancak birden çok kiracıya yayılan bir çözüm tasarlamak çok daha [karmaşıktır](/azure/active-directory/develop/single-and-multi-tenant-apps).

Azure Role-Based Erişim Denetimi (RBAC) Azure için daha ince erişim yönetimi sağlar. RBAC kullanarak, kullanıcılara işlerini yapmak için gereken en az izin vererek kaynaklara erişimi yönetebilirsiniz. Bu belgenin ayrıntıları bu belgenin kapsamı dışındadır, ancak RBAC hakkında daha fazla bilgi için bkz. Azure'da rol tabanlı erişim denetimi [(RBAC) nedir?](/azure/role-based-access-control/overview) RBAC önemlidir, ancak Azure için yönetimle ilgili dikkate alınacak konuların yalnızca bir kısmıdır. [Bulut Benimseme Çerçevesi,](/azure/cloud-adoption-framework/govern/) daha fazla bilgi edinmek için harika bir başlangıç noktasıdır. Arkadaşımın [Andres Gerçekteninet'in, müşterilere](https://www.linkedin.com/in/andres-ravinet/) adım adım yol adım yol vermelerini istiyorum, ancak çeşitli bileşenlere göre yaklaşıma karar verme. Çeşitli öğeler için üst düzey görünüm (gerçek müşteri modeline kadar iyi değildir) şöyledir:

![Temsili yönetim için Azure bileşenlerinin üst düzey görünümü.](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Yukarıdaki resimde de gördüğünüz gibi, diğer birçok hizmet tasarımın bir parçası olarak düşünülmelidir (örneğin: [Azure](/azure/governance/policy/overview) İlkeleri, [Azure](/azure/governance/blueprints/overview) Şemaları, [Yönetim](/azure/governance/management-groups/) Grupları, vb.).

## <a name="conclusion"></a>Sonuç

Kısa bir özet olarak başladı ve beklendiğinden daha uzun sona erdi.  Şimdi, organizasyonunız için temsilci modeli oluşturmayı derinden incelemeye hazır olduğunu umarız.  Bu konuşma müşterilerle çok yaygındır. Herkese uygun tek bir model yoktur. Müşteriler arasında gördüğünüz ortak düzenleri belgeden önce, Microsoft mühendislik tarafından planlanan birkaç geliştirme için bekleme. Bu arada, en yakın Microsoft Teknoloji Merkezi'ne bir ziyaret düzenlemek için [Microsoft hesabı ekibiyle birlikte çalışabilirsiniz](https://www.microsoft.com/mtc).  Sizi orada görebilirler!
