---
title: Adlandırılmış Varlıkların SMTP DNS Tabanlı Kimlik Doğrulaması (DANE) e-posta iletişimlerinin güvenliğini sağlamak için nasıl çalışır?
f1.keywords:
- NOCSH
ms.author: v-mathavale
author: v-mathavale
manager: dansimp
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Posta sunucuları arasındaki e-posta iletişiminin güvenliğini sağlamak için SMTP DNS Tabanlı Adlandırılmış Varlıkların Kimlik Doğrulamasının (DANE) nasıl çalıştığını öğrenin.
ms.openlocfilehash: b5f9337457556dda53b5b2f982480a4c2501fcc9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782863"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Adlandırılmış Varlıkların SMTP DNS Tabanlı Kimlik Doğrulaması (DANE) nasıl çalışır?

SMTP protokolü, iletileri posta sunucuları arasında aktarmak için kullanılan ana protokoldür ve varsayılan olarak güvenli değildir. İletilerin SMTP üzerinden şifrelenmiş iletimini desteklemek için Aktarım Katmanı Güvenliği (TLS) protokolü yıllar önce kullanıma sunulmuştur. Bu, bir gereksinim olarak değil, genellikle fırsatçı olarak kullanılır ve çok fazla e-posta trafiğinin net metin halinde bırakılması, kötü aktörlerin müdahalesine karşı savunmasız olmasıdır. Ayrıca SMTP, kimlik sahtekarlığına ve OrtaDaki Adam (MITM) saldırılarına duyarlı olan genel DNS altyapısı aracılığıyla hedef sunucuların IP adreslerini belirler. Bu, e-posta gönderme ve alma güvenliğini artırmak için birçok yeni standardın oluşturulmasına neden olmuştur. Bunlardan biri, Adlandırılmış Varlıkların DNS Tabanlı Kimlik Doğrulamasıdır (DANE).

SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) için DANE, etki alanının DNS kaydı kümesinde Aktarım Katmanı Güvenliği Kimlik Doğrulaması (TLSA) kaydının varlığını kullanarak bir etki alanına işaret eder ve posta sunucuları DANE'yi destekler. TLSA kaydı yoksa, posta akışı için DNS çözümlemesi, herhangi bir DANE denetimi denenmeden her zamanki gibi çalışır. TLSA kaydı TLS desteğine güvenli bir şekilde sinyal gönderir ve etki alanı için DANE ilkesini yayımlar. Bu nedenle, posta sunucularını göndermek, SMTP DANE kullanarak meşru alıcı posta sunucularının kimliğini başarıyla doğrulayabilir. Bu, eski sürüme düşürme ve MITM saldırılarına karşı dayanıklı olmasını sağlar. DANE' nin DNSSEC üzerinde doğrudan bağımlılıkları vardır. Bu, ortak anahtar şifrelemesi kullanarak DNS aramaları için kayıtları dijital olarak imzalayarak çalışır. DNSSEC denetimleri, istemciler için DNS sorguları oluşturan DNS sunucuları olan özyinelemeli DNS çözümleyicilerinde gerçekleşir. DNSSEC, DNS kayıtlarının değiştirilmemesini ve orijinal olmasını sağlar.

Bir etki alanının MX, A/AAAA ve DNSSEC ile ilgili kaynak kayıtları DNSSEC kimlik doğrulaması olarak DNS özyinelemeli çözümleyiciye döndürüldükten sonra, gönderen posta sunucusu MX ana bilgisayar girdisine veya girişlerine karşılık gelen TLSA kaydını ister. TLSA kaydı mevcutsa ve başka bir DNSSEC denetimi kullanılarak kimlik doğrulaması kanıtlanmışsa, DNS özyinelemeli çözümleyici TLSA kaydını gönderen posta sunucusuna döndürür.

Özgün TLSA kaydını aldıktan sonra, gönderen posta sunucusu özgün TLSA kaydıyla ilişkilendirilmiş MX konağına bir SMTP bağlantısı kurar. Gönderen posta sunucusu TLS'yi ayarlamayı ve sunucunun TLS sertifikasını TLSA kaydındaki verilerle karşılaştırmayı deneyerek gönderene bağlı hedef posta sunucusunun geçerli alıcı posta sunucusu olduğunu doğrular. Kimlik doğrulaması başarılı olursa ileti iletilir (TLS kullanılarak). Kimlik doğrulaması başarısız olduğunda veya TLS hedef sunucu tarafından desteklenmiyorsa, Exchange Online 15 dakika sonra aynı hedef etki alanı için bir DNS sorgusuyla başlayan doğrulama işleminin tamamını yeniden dener ve bundan sonra 15 dakika sonra sonraki 24 saat boyunca her saat çalışır. Kimlik doğrulaması 24 saat yeniden denendikten sonra başarısız olmaya devam ederse, iletinin süresi dolar ve hata ayrıntılarını içeren bir NDR oluşturulur ve gönderene gönderilir.

## <a name="what-are-the-components-of-dane"></a>DANE bileşenleri nelerdir?

### <a name="tlsa-resource-record"></a>TLSA Kaynak Kaydı

TLS Kimlik Doğrulaması (TLSA) kaydı, bir sunucunun X.509 sertifikasını veya ortak anahtar değerini kaydı içeren etki alanı adıyla ilişkilendirmek için kullanılır. TLSA kayıtlarına yalnızca etki alanınızda DNSSEC etkinse güvenilebilir. Etki alanınızı barındırmak için bir DNS sağlayıcısı kullanıyorsanız, bu, etki alanını onlarla yapılandırırken sunulan bir ayar olabilir. DNSSEC bölge imzalama hakkında daha fazla bilgi edinmek için şu bağlantıyı ziyaret edin: [DNSSEC | genel bakış Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)).

Örnek TLSA kaydı:

:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Örnek TLSA kaydı" lightbox="../media/compliance-trial/example-TLSA-record.png":::

TLSA kayıt türüne özgü dört yapılandırılabilir alan vardır:

**Sertifika Kullanım Alanı**: Gönderen e-posta sunucusunun hedef e-posta sunucusunun sertifikasını nasıl doğrulayacaklarını belirtir.

|Değer|Kısaltma|Açıklama|
|---|---|---|
|01<sup></sup>|PKIX-TA|Kullanılan sertifika, X.509 güven zincirinden güven bağlayıcısı Genel CA'dır.|
|11<sup></sup>|PKIX-EE|Sertifika işaretlendi hedef sunucudur; DNSSEC denetimleri orijinalliğini doğrulamalıdır.|
|2|DANE-TA|Sunucunun X.509 ağacından gelen ve güven zincirindeki bir güven bağlantısı tarafından doğrulanması gereken özel anahtarını kullanın. TLSA kaydı, etki alanı için TLS sertifikalarını doğrulamak için kullanılacak güven bağlayıcısını belirtir.|
|3|DANE-EE|Yalnızca hedef sunucunun sertifikasıyla eşleşir.|

<sup>1</sup> Exchange Online, DANE SMTP ile uygulandığında 0 veya 1 Sertifika Kullanım Alanı değerlerinin kullanılmaması gerektiğine dair RFC uygulama yönergelerini izler. Sertifika Kullanımı alan değeri 0 veya 1 olan bir TLSA kaydı Exchange Online döndürülürse, Exchange Online bunu kullanılamaz olarak değerlendirir. Tüm TLSA kayıtları kullanılamaz durumda bulunursa, Exchange Online e-posta gönderilirken 0 veya 1 için DANE doğrulama adımlarını gerçekleştirmez. Bunun yerine, bir TLSA kaydının bulunması nedeniyle, Exchange Online e-postayı göndermek, hedef e-posta sunucusu TLS'yi destekliyorsa e-postayı göndermek veya hedef e-posta sunucusu TLS'yi desteklemiyorsa e-postayı bırakıp ndr oluşturmak için TLS kullanımını zorunlu kılacaktır.

Örnek TLSA kaydında Sertifika Kullanım Alanı '3' olarak ayarlandığından Sertifika İlişkilendirme Verileri ('abc123... xyz789') yalnızca hedef sunucunun sertifikasıyla eşleşir.

**Seçici alanı**: Hedef sunucu sertifikasının hangi bölümlerinin denetlenmesi gerektiğini gösterir.

|Değer|Kısaltma|Açıklama|
|---|---|---|
|0|Cert|Tam sertifika kullanın.|
|1|SPKI (Konu Ortak Anahtar Bilgileri)|Sertifikanın ortak anahtarını ve ortak anahtarın kullanılacağı belirlenen algoritmayı kullanın.|

Örnek TLSA kaydında Seçici Alanı '1' olarak ayarlanmıştır, bu nedenle Sertifika İlişkilendirme Verileri hedef sunucu sertifikasının ortak anahtarı ve ortak anahtarın kullanmak üzere tanımlandığı algoritma kullanılarak eşleştirilir.

**Eşleşen Tür Alanı**: Sertifikanın TLSA kaydında gösterileceği biçimi gösterir.

|Değer|Kısaltma|Açıklama|
|---|---|---|
|0|Tam|TSLA kaydındaki veriler tam sertifika veya SPKI'dir.|
|1|SHA-256|TSLA kaydındaki veriler, sertifikanın veya SPKI'nin SHA-256 karmasıdır.|
|2|SHA-512|TSLA kaydındaki veriler, sertifikanın veya SPKI'nin SHA-512 karmasıdır.|

Örnek TLSA kaydında, Eşleşen Tür Alanı '1' olarak ayarlanmıştır, bu nedenle Sertifika İlişkilendirme Verileri hedef sunucu sertifikasındaki Konu Ortak Anahtar Bilgilerinin SHA-256 karmasıdır

**Sertifika İlişkilendirme Verileri**: Hedef sunucu sertifikasıyla eşleştirmek için kullanılan sertifika verilerini belirtir. Bu veriler Seçici Alanı değerine ve Eşleşen Tür Değerine bağlıdır.

Örnek TLSA kaydında Sertifika İlişkilendirme verileri 'abc123.. xyz789'. Örnekteki Seçici Alanı değeri '1' olarak ayarlandığından, hedef sunucu sertifikasının ortak anahtarına ve onunla kullanılmak üzere tanımlanan algoritmaya başvurur. Örnekteki Eşleşen Tür alan değeri '1' olarak ayarlandığından hedef sunucu sertifikasındaki Konu Ortak Anahtar Bilgisi'nin SHA-256 karması başvuruda bulunur.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Exchange Online müşterileri SMTP DANE Giden'i nasıl kullanabilir?

Exchange Online müşterisi olarak, giden e-postanız için bu gelişmiş e-posta güvenliğini yapılandırmak için yapmanız gereken hiçbir şey yoktur. Bu sizin için oluşturduğumuz bir şeydir ve tüm Exchange Online müşterileri için varsayılan olarak açıktır ve hedef etki alanı DANE desteğini tanıttığında kullanılır. DNSSEC ve DANE denetimleriyle e-posta göndermenin avantajlarından yararlanmak için, e-posta alışverişi yaptığınız iş ortaklarınıza, bu standartları kullanarak e-posta alabilmeleri için DNSSEC ve DANE uygulaması gerektiğini iletin.

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Exchange Online müşteriler SMTP DANE gelen hizmetini nasıl kullanabilir?

Şu anda Exchange Online için gelen SMTP DANE desteklenmez. Desteğin 2022'nin sonunda piyasaya sürülmesi bekleniyor.

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Önerilen TLSA kayıt yapılandırması nedir?

Sertifika Kullanımı alanından oluşan bir TLSA kaydı olan SMTP DANE için RFC uygulama kılavuzu başına 3, Seçici alanı 1 olarak ayarlanmış ve Eşleşen Tür alanı 1 olarak ayarlanmış olmalıdır.

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>SMTP DANE ile Posta Flow Exchange Online

Aşağıdaki akış grafiğinde gösterilen SMTP DANE ile Exchange Online için posta akışı işlemi, DNSSEC aracılığıyla etki alanı ve kaynak kaydı güvenliğini, hedef posta sunucusunda TLS desteğini ve hedef posta sunucusunun sertifikasının ilişkili TLSA kaydına göre beklenenle eşleşdiğini doğrular.

SMTP DANE hatasının e-postanın engellenmesine neden olacağı yalnızca iki senaryo vardır:

- Hedef etki alanı DNSSEC desteğine işaret etti, ancak bir veya daha fazla kayıt kimliği doğrulanmamış olarak döndürüldü.

- Hedef etki alanı için tüm MX kayıtlarının TLSA kayıtları vardır ve hedef sunucunun sertifikalarından hiçbiri TSLA kayıt verilerine göre beklenenle eşleşmez veya hedef sunucu tarafından TLS bağlantısı desteklenmez.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="SMTP DANE ile çevrimiçi posta akışını Exchange" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>İlgili Teknolojiler

|Teknoloji|Ek Bilgiler|
|---|---|
|**Posta Aktarım Aracısı - Katı Aktarım Güvenliği (MTA-STS),** hedef e-posta sunucusunun TLS'yi destekleyip desteklemediğini ve TLS üzerinde anlaşmaya varılamadığında yapılması gerekenleri belirten etki alanı ilkelerini ayarlamaya yönelik bir mekanizma sağlayarak (örneğin, iletimi durdurma) devre dışı bırakma ve OrtaDaki Adam saldırılarını önlemeye yardımcı olur.|Exchange Online'in gelecek gelen ve giden MTA-STS desteği hakkında daha fazla bilgi bu yılın sonlarında yayımlanacaktır. <br/><br/> [Exchange Online Transport News from Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699) <br/><br/> [rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)|
|**Sender Policy Framework (SPF),** hedef e-posta sistemlerinin özel etki alanınızdan gönderilen iletilere güvenmesini sağlamak için IP bilgilerini kullanır.|[Sender Policy Framework (SPF) kimlik sahtekarlığına nasıl engel oluyor - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)|
|**DomainKeys Identified Mail (DKIM),** hedef e-posta sistemlerinin özel etki alanınızdan giden iletilere güvenmesini sağlamak için X.509 sertifika bilgilerini kullanır.|[Özel etki alanınızda e-posta için DKIM kullanma - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)|
|**Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC),** gönderenlerin kimliğini doğrulamak ve hedef e-posta sistemlerinin etki alanınızdan gönderilen iletilere güvenmesini sağlamak için Sender Policy Framework ve DomainKeys Identified Mail ile birlikte çalışır.|[E-postayı doğrulamak için DMARC kullanma, kurulum adımları - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)|

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>SMTP DANE ile E-posta Gönderme Sorunlarını Giderme

Şu anda, Exchange Online ile e-posta gönderirken DANE için dört hata kodu vardır. Microsoft bu hata kodu listesini etkin bir şekilde güncelleştiriyor. Hatalar şu şekilde görünür:

1. İleti İzleme Ayrıntıları görünümü aracılığıyla Exchange Yönetim Merkezi portalı.
2. DANE veya DNSSEC hatası nedeniyle ileti gönderilmediğinde oluşturulan NDR'ler.
3. Uzak Bağlantı Çözümleyicisi aracı [Microsoft Uzaktan Bağlantı Çözümleyicisi](https://testconnectivity.microsoft.com/tests/o365).

|NDR Kodu|Açıklama|
|---|---|
|5.7.321|starttls-desteklenmiyor: Hedef posta sunucusunun posta almak için TLS'yi desteklemesi gerekir.|
|5.7.322|sertifikanın süresi doldu: Hedef posta sunucusunun sertifikasının süresi doldu.|
|5.7.323|tlsa-invalid: Etki alanı DANE doğrulamasında başarısız oldu.|
|5.7.324|dnssec-invalid: Hedef etki alanı geçersiz DNSSEC kayıtları döndürdü.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>5.7.321 starttls-desteklenmiyor sorunlarını giderme

Bu genellikle hedef posta sunucusuyla ilgili bir sorunu gösterir. İletiyi aldıktan sonra:

1. Hedef e-posta adresinin doğru girildiğini denetleyin.
2. Hedef sunucunun TLS kullanarak iletileri alacak şekilde doğru yapılandırılıp yapılandırılmadığını belirleyebilmesi için hedef e-posta yöneticisini bu hata kodunu aldığınıza dair uyarın.
3. E-postayı göndermeyi yeniden deneyin ve Exchange Yönetim Merkezi portalındaki ileti için İleti İzleme Ayrıntıları'nı gözden geçirin.

### <a name="troubleshooting-57322-certificate-expired"></a>5.7.322 sertifikasının süresi doldu sorunlarını giderme

Süresi dolmamış geçerli bir X.509 sertifikasının gönderen e-posta sunucusuna sunulması gerekir. X.509 sertifikaları genellikle yıllık olarak sona erdikten sonra yenilenmelidir. İletiyi aldıktan sonra:

1. Hedef e-posta yöneticisini bu hata kodunu aldığınız konusunda uyarın ve hata kodu dizesini sağlayın.
2. Hedef sunucu sertifikasının yenilenmesi ve TLSA kaydının yeni sertifikaya başvurmak üzere güncelleştirilebilmesi için zaman tanıyın. Ardından, e-postayı göndermeyi yeniden deneyin ve Exchange Yönetim Merkezi portalındaki ileti için İleti İzleme Ayrıntıları'nı gözden geçirin.

### <a name="troubleshooting-57323-tlsa-invalid"></a>5.7.323 tlsa-invalid sorunlarını giderme

Bu hata kodu TLSA kaydının yanlış yapılandırılması ile ilgilidir ve yalnızca DNSSEC-authentic TLSA kaydı döndürüldükten sonra oluşturulabilir. DANE doğrulaması sırasında kayıt döndürüldükten sonra gerçekleşen ve kodun oluşturulmasına neden olabilecek birçok senaryo vardır. Microsoft, her senaryonun belirli bir koda sahip olması için bu hata kodunun kapsadığı senaryolar üzerinde etkin bir şekilde çalışmaktadır. Şu anda, bu senaryolardan biri veya daha fazlası hata kodunun oluşturulmasına neden olabilir:

1. Hedef posta sunucusunun sertifikası, özgün TLSA kaydı başına beklenen sertifikayla eşleşmiyor.
2. Orijinal TLSA kaydı yanlış yapılandırılmış.
3. Hedef etki alanına saldırı yapılıyor.
4. Diğer DANE hataları.

İletiyi aldıktan sonra:

1. Hedef e-posta yöneticisini bu hata kodunu aldığınız konusunda uyarın ve hata kodu dizesini sağlayın.
2. Hedef e-posta yöneticisinin DANE yapılandırmasını ve e-posta sunucusu sertifikası geçerliliğini gözden geçirmesine izin verin. Ardından, e-postayı göndermeyi yeniden deneyin ve Exchange Yönetim Merkezi portalındaki ileti için İleti İzleme Ayrıntıları'nı gözden geçirin.

### <a name="troubleshooting-57324-dnssec-invalid"></a>5.7.324 dnssec-invalid sorunlarını giderme

Hedef etki alanı DNSSEC-authentic olduğunu belirttiğinde ancak Exchange Online DNSSEC-authentic olarak doğrulayamadığında bu hata kodu oluşturulur.

İletiyi aldıktan sonra:

1. Hedef e-posta yöneticisini bu hata kodunu aldığınız konusunda uyarın ve hata kodu dizesini sağlayın.
2. Hedef e-posta yöneticisinin etki alanının DNSSEC yapılandırmasını gözden geçirmesi için zaman tanıyın. Ardından, e-postayı göndermeyi yeniden deneyin ve Exchange Yönetim Merkezi portalındaki ileti için İleti İzleme Ayrıntıları'nı gözden geçirin.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>SMTP DANE ile E-posta Alma Sorunlarını Giderme

Şu anda, alıcı etki alanının yöneticisinin dnssec ve DANE yapılandırmasını doğrulamak ve bu standartları kullanarak Exchange Online e-posta almak için sorunlarını gidermek için kullanabileceği iki yöntem vardır.

1. [RFC8460'ta](https://datatracker.ietf.org/doc/html/rfc8460) tanıtılan SMTP TLS-RPT'yi (Aktarım Katmanı Güvenlik Raporlaması) benimseme
2. Uzak Bağlantı Çözümleyicisi aracını [kullanma Microsoft Uzaktan Bağlantı Çözümleyicisi](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) , gönderenlerin hedef etki alanı yöneticilerine DANE ve MTA-STS başarıları ve ilgili hedef etki alanlarıyla ilgili hatalar hakkında ayrıntılı bilgi sağlaması için bir raporlama mekanizmasıdır. TLS-RPT raporlarını almak için, etki alanınızın DNS kayıtlarına yalnızca raporların gönderilmesini istediğiniz e-posta adresini veya URI'yi içeren bir TXT kaydı eklemeniz gerekir. Exchange Online, JSON biçiminde TLS-RPT raporları gönderir.

Örnek kayıt:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Örnek kayıt" lightbox="../media/compliance-trial/example-record.png":::

İkinci yöntem, Exchange Online hizmet dışında e-posta gönderirken dns yapılandırmanızda aynı DNSSEC ve DANE denetimlerini yapabilen Uzak [Bağlantı Çözümleyicisi Microsoft Uzaktan Bağlantı Çözümleyicisi'ni](https://testconnectivity.microsoft.com/tests/o365) kullanmaktır. Bu, bu standartları kullanarak Exchange Online'dan e-posta almak için yapılandırmanızdaki hataları gidermenin en doğrudan yoludur.

Sorun giderme sırasında aşağıdaki hata kodları oluşturulabilir:

|NDR Kodu|Açıklama|
|---|---|
|4/5.7.321|starttls-desteklenmiyor: Hedef posta sunucusunun posta almak için TLS'yi desteklemesi gerekir.|
|4/5.7.322|sertifikanın süresi doldu: Hedef posta sunucusunun sertifikasının süresi doldu.|
|4/5.7.323|tlsa-invalid: Etki alanı DANE doğrulamasında başarısız oldu.|
|4/5.7.324|dnssec-invalid: Hedef etki alanı geçersiz DNSSEC kayıtları döndürdü.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>5.7.321 starttls-desteklenmiyor sorunlarını giderme

> [!NOTE]
> Bu adımlar, SMTP DANE kullanarak Exchange Online e-posta alma sorunlarını gideren e-posta yöneticilerine yöneliktir.

Bu genellikle hedef posta sunucusuyla ilgili bir sorunu gösterir. Uzak Bağlantı Çözümleyicisi'nin bağlanma testi yaptığı posta sunucusu. Genellikle bu kodu oluşturan iki senaryo vardır:

1. Hedef posta sunucusu güvenli iletişimi hiç desteklemez ve düz, şifrelenmemiş iletişim kullanılmalıdır.
2. Hedef sunucu yanlış yapılandırılmış ve STARTTLS komutunu yoksayar.

İletiyi aldıktan sonra:

1. E-posta adresini denetleyin.
2. Deyimin ilişkili olduğu posta sunucusunu tanımlayabilmeniz için hata deyimiyle ilişkili IP adresini bulun.
3. POSTA sunucunuzun ayarını denetleyip SMTP trafiğini dinleyecek şekilde yapılandırıldığından emin olun (genellikle 25 ve 587 bağlantı noktaları).
4. Birkaç dakika bekleyin, ardından Uzaktan Bağlantı Çözümleyicisi aracıyla testi yeniden deneyin.
5. Yine de başarısız olursa TLSA kaydını kaldırmayı deneyin ve Uzaktan Bağlantı Çözümleyicisi aracıyla testi yeniden çalıştırın.
6. Hata yoksa, bu durum posta almak için kullandığınız posta sunucusunun STARTTLS'yi desteklemediğini gösterebilir ve DANE kullanmak için bunu destekleyen bir sunucuya yükseltmeniz gerekebilir.

### <a name="troubleshooting-57322-certificate-expired"></a>5.7.322 sertifikasının süresi doldu sorunlarını giderme

> [!NOTE]
> Bu adımlar, SMTP DANE kullanarak Exchange Online e-posta alma sorunlarını gideren e-posta yöneticilerine yöneliktir.

Süresi dolmamış geçerli bir X.509 sertifikasının gönderen e-posta sunucusuna sunulması gerekir. X.509 sertifikaları genellikle yıllık olarak sona erdikten sonra yenilenmelidir. İletiyi aldıktan sonra:

1. İlişkili olduğu posta sunucusunu tanımlayabilmeniz için hata deyimiyle ilişkili IP'yi denetleyin. Belirttiğiniz e-posta sunucusunda süresi dolan sertifikayı bulun.
2. Sertifika sağlayıcınızın web sitesinde oturum açın.
3. Süresi dolan sertifikayı seçin ve yenileme ve yenileme için ödeme yapmak için yönergeleri izleyin.
4. Sağlayıcınız satın alma işlemini doğruladıktan sonra yeni bir sertifika indirebilirsiniz.
5. Yenilenen sertifikayı ilişkili posta sunucusuna yükleyin.
6. Posta sunucusunun ilişkili TLSA kaydını yeni sertifikanın verileriyle güncelleştirin.
7. Uygun bir süre bekledikten sonra, Uzaktan Bağlantı Çözümleyicisi aracıyla testi yeniden deneyin.

### <a name="troubleshooting-57323-tlsa-invalid"></a>5.7.323 tlsa-invalid sorunlarını giderme

> [!NOTE]
> Bu adımlar, SMTP DANE kullanarak Exchange Online e-posta alma sorunlarını gideren e-posta yöneticilerine yöneliktir.

Bu hata kodu TLSA kaydının yanlış yapılandırılması ile ilgilidir ve yalnızca DNSSEC-authentic TSLA kaydı döndürüldükten sonra oluşturulabilir. Ancak, DANE doğrulaması sırasında kayıt döndürüldükten sonra kodun oluşturulmasına neden olabilecek birçok senaryo vardır. Microsoft, her senaryonun belirli bir koda sahip olması için bu hata kodunun kapsadığı senaryolar üzerinde etkin bir şekilde çalışmaktadır. Şu anda, bu senaryolardan biri veya daha fazlası hata kodunun oluşturulmasına neden olabilir:

1. Orijinal TLSA kaydı yanlış yapılandırılmış.
2. Sertifika henüz geçerli bir zaman değil/gelecek bir zaman penceresi için yapılandırılmadı.
3. Hedef etki alanına saldırı yapılıyor.
4. Diğer DANE hataları.

İletiyi aldıktan sonra:

1. İlişkili olduğu posta sunucusunu tanımlamak için hata deyimiyle ilişkili IP'yi denetleyin.
2. Tanımlanan posta sunucusuyla ilişkili TLSA kaydını tanımlayın.
3. Gönderene tercih edilen DANE denetimlerini gerçekleştirmesi için sinyal gönderdiğinden ve TLSA kaydına doğru sertifika verilerinin eklendiğinden emin olmak için TLSA kaydının yapılandırmasını doğrulayın.
    1. Kayıtta tutarsızlıklar için herhangi bir güncelleştirme yapmanız gerekiyorsa, birkaç dakika bekleyin ve ardından Uzaktan Bağlantı Çözümleyicisi aracıyla testi yeniden çalıştırın.
4. Tanımlanan posta sunucusunda sertifikayı bulun.
5. Sertifikanın geçerli olduğu zaman penceresini denetleyin. Geçerliliği gelecekteki bir tarihte başlatacak şekilde ayarlandıysa geçerli tarih için yenilenmesi gerekir.
    1. Sertifika sağlayıcınızın web sitesinde oturum açın.
    2. Süresi dolan sertifikayı seçin ve yenileme ve yenileme için ödeme yapmak için yönergeleri izleyin.
    3. Sağlayıcınız satın alma işlemini doğruladıktan sonra yeni bir sertifika indirebilirsiniz.
    4. Yenilenen sertifikayı ilişkili posta sunucusuna yükleyin.

### <a name="troubleshooting-57324-dnssec-invalid"></a>5.7.324 dnssec-invalid sorunlarını giderme

> [!NOTE]
> Bu adımlar, SMTP DANE kullanarak Exchange Online e-posta alma sorunlarını gideren e-posta yöneticilerine yöneliktir.

Bu hata kodu, hedef etki alanı DNSSEC-authentic olduğunu belirttiğinde ancak Exchange Online DNSSEC-authentic olarak doğrulayamadığında oluşturulur. Bu bölüm DNSSEC sorunlarını gidermek için kapsamlı olmayacaktır ve etki alanlarının daha önce DNSSEC kimlik doğrulamasını geçtiği ancak şimdi geçmediği senaryolara odaklanmaktadır.

İletiyi aldıktan sonra:

1. GoDaddy gibi bir DNS sağlayıcısı kullanıyorsanız, sorun giderme ve yapılandırma değişikliği üzerinde çalışabilmesi için DNS sağlayıcınıza hatayı uyarın.
2. Kendi DNSSEC altyapınızı yönetiyorsanız, bu hata iletisini oluşturabilecek birçok DNSSEC yanlış yapılandırması vardır. Bölgenizin daha önce DNSSEC kimlik doğrulamasını geçirip geçirmediğini denetlemeniz gereken bazı yaygın sorunlar:
    1. Üst bölge, alt bölgede olmayan bir öğeye işaret eden bir dizi DS kaydı barındırdığında, bozuk güven zinciri. Bu, çözümleyicileri doğrulayarak alt bölgenin sahte olarak işaretlenmesine neden olur.
        - Alt etki alanları RRSIG anahtar kimliklerini gözden geçirerek ve bunların üst bölgede yayımlanan DS kayıtlarındaki anahtar kimliklerle eşleştiğinden emin olarak çözümleyebilirsiniz.
    2. Etki alanı için RRSIG kaynak kaydı geçerli zaman değil, süresi doldu veya geçerlilik süresi başlamadı.
        - Geçerli zaman dilimlerini kullanarak etki alanı için yeni imzalar oluşturarak sorunu çözebilirsiniz.

## <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Exchange Online müşterisi olarak DNSSEC ve/veya DANE kullanmayı geri çevirebilir miyim?

DNSSEC ve DANE'nin hizmetimizin güvenlik konumunu önemli ölçüde artıracağına ve tüm müşterilerimize fayda sağlayacağına kesinlikle inanıyoruz. Bu dağıtımın M365 müşterileri için yaratabileceği olası etkinin riskini ve önem derecesini azaltmak için geçen yıl boyunca özenle çalıştık. Olumsuz etkinin ortaya çıktıktan sonra en aza indirildiğinden emin olmak için dağıtımı etkin bir şekilde izleyip izleyeceğiz. Bu nedenle kiracı düzeyinde özel durumlar veya geri çevirme kullanılamaz.
DNSSEC ve/veya DANE'nin etkinleştirilmesi ile ilgili herhangi bir sorunla karşılaşırsanız, bu belgede belirtilen hataları araştırmak için farklı yöntemler hatanın kaynağını belirlemenize yardımcı olur. Çoğu durumda sorun dış hedef tarafla ilgili olacaktır ve bu iş ortaklarına, bu standartları kullanarak Exchange Online e-posta almak için DNSSEC ve DANE'yi doğru yapılandırmaları gerektiğini bildirmeniz gerekir.

### <a name="how-does-dnssec-relate-to-dane"></a>DNSSEC ile DANE arasındaki ilişki nedir?

DNSSEC, DNS sorgusuna yanıt olarak döndürülen kayıtların orijinal olduğundan emin olmak için ortak anahtar altyapısından yararlanarak DNS çözümlemesine bir güven katmanı ekler. DANE, alıcı posta sunucusunun özgün MX kaydı için geçerli ve beklenen posta sunucusu olmasını sağlar.

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>SMTP için MTA-STS ile DANE arasındaki fark nedir?

DANE ve MTA-STS aynı amaca hizmet eder, ancak DANE, DNS kimlik doğrulaması için DNSSEC gerektirirken, MTA-STS sertifika yetkililerine dayanır.

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Fırsatçı TLS neden yeterli değildir?

Fırsatçı TLS, her ikisi de desteklemeyi kabul ederse iki uç nokta arasındaki iletişimi şifreler. Ancak, TLS iletimi şifrelese bile, DNS çözümlemesi sırasında etki alanı için gerçek uç nokta yerine kötü amaçlı bir aktörün uç noktasına işaret eden bir etki alanı yanıltılabilir. Bu, DNSSEC ile MTA-STS ve/veya SMTP DANE uygulanarak giderilen bir e-posta güvenliği açığıdır.

### <a name="why-isnt-dnssec-sufficient"></a>DNSSEC neden yeterli değildir?

DNSSEC, posta akışı senaryoları için OrtaDaki Adam saldırılarına ve eski sürüme düşürme (TLS'den metin temizlemeye) saldırılarına karşı tam olarak dayanıklı değildir. DNSSEC ile birlikte MTA-STS ve DANE eklenmesi, hem MITM hem de eski sürüme düşürme saldırılarını engellemek için kapsamlı bir güvenlik yöntemi sağlar.

## <a name="additional-links"></a>Ek Bağlantılar

[Kendi etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[DNSSEC | genel bakış Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[E-postayı doğrulamak için DMARC kullanma, kurulum adımları - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Özel etki alanınızda e-posta için DKIM kullanma - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Sender Policy Framework (SPF) kimlik sahtekarlığına nasıl engel oluyor - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online Transport News from Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)
