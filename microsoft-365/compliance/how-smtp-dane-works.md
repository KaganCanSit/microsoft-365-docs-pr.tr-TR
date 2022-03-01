---
title: E-posta iletişimlerinin güvenliğini sağlamak için Adlandırılmış Varlıkları SMTP DNS Tabanlı Kimlik Doğrulaması (DANE) nasıl çalışır?
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
description: Posta sunucuları arasındaki e-posta iletişimlerinin güvenliğini sağlamak için, SMTP DNS Tabanlı Adlandırılmış Varlıklar Kimlik Doğrulaması'nın (DANE) nasıl çalıştığını öğrenin.
ms.openlocfilehash: 32c39859d9bfdf292fd9c7a315a0ee1ee08eae2e
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010077"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Adlandırılmış Varlıkları (DANE) SMTP DNS Tabanlı Kimlik Doğrulaması (DANE) nasıl çalışır?

SMTP protokolü, posta sunucuları arasında ileti aktarımı için kullanılan ana protokoldür ve varsayılan olarak güvenli değildir. Aktarım Katmanı Güvenliği (TLS) protokolü, iletilerin SMTP üzerinden şifreli iletimini desteklemek için yıllar önce başlatıldı. Yaygın olarak, bir gereksinim olarak değil, fırsat olarak kullanılır ve çok fazla e-posta trafiğinin net bir metinde, olumsuz bir aksatan müdahaleye açık kalır. Ayrıca SMTP, hedef sunucuların IP adreslerini genel DNS altyapısı üzerinden belirler ve bu kimlik doğrulaması ve Ortadaki Adam (MITM) saldırılarına karşı duyarlıdır. Bu, e-posta gönderme ve alma güvenliğini artırmak için oluşturulan birçok yeni standarda yol açtı. Bunlardan biri Adlandırılmış Varlıkları (DANE) DNS Tabanlı Kimlik Doğrulaması'dır.
  
SMTP için DANE [RFC 7672](https://tools.ietf.org/html/rfc7672) , etki alanının DNS kaydı kümesinde bir Aktarım Katmanı Güvenliği Kimlik Doğrulaması (TLSA) kaydının varlığını bir etki alanına sinyal olarak verir ve posta sunucuları DANE'yi destekler. Mevcut TLSA kaydı yoksa, herhangi bir DANE denetimi denenmeden posta akışı için DNS çözümleme her zamanki gibi çalışır. TLSA kaydı TLS desteğine güvenli bir şekilde işaret eder ve etki alanı için DANE ilkesi yayımlar. Dolayısıyla, posta sunucularını gönderme, SMTP DANE kullanarak yasal alıcı posta sunucularının kimliğini doğrular. Bu, azaltma ve MITM saldırılarına karşı dayanıklı hale geldi. DANE'nin DNSSEC'e doğrudan bağımlılıkları vardır ve bu, genel anahtar şifrelemesini kullanarak DNS aramaları kayıtlarını dijital olarak imzalayarak çalışır. DNSSEC denetimleri, istemciler için DNS sorguları hazırlayan DNS sunucuları olan, yenidenlayan DNS çözümleyicilerde  gerçekleşir. DNSSEC, DNS kayıtlarının değiştirilmemasını ve kimlik doğrulamasını sağlar.  

Bir etki alanının MX, A/AAAA ve DNSSEC ile ilgili kaynak kayıtları DNSSEC kimlikli olarak DNS yineleyici çözümleyicisi'ne döndürülmezse, gönderen posta sunucusu, MX ana bilgisayar girdilerine veya girişlerine karşılık gelen TLSA kaydını ister. Başka bir DNSSEC denetimi kullanılarak TLSA kaydı mevcut ve kanıtlanmış doğrulanmışsa, DNS yineleyici çözümleyici TLSA kaydını gönderen posta sunucusuna geri gönderir. 

Özgün TLSA kaydını aldıktan sonra, gönderen posta sunucusu authentic TLSA kaydıyla ilişkilendirilmiş MX ana bilgisayarına bir SMTP bağlantısı kurabilirsiniz. Gönderen posta sunucusu TLS'yi ayarlamayı dener ve gönderene bağlı hedef posta sunucusunun yasal alıcı posta sunucusu olduğunu doğrulamak için sunucunun TLS sertifikasını TLSA kaydında yer alan verilerle karşılaştırmayı dener. Kimlik doğrulaması başarılı olursa ileti ilet (TLS kullanarak). Kimlik doğrulaması başarısız olduğunda veya hedef sunucu tarafından TLS desteklenmiyorsa, Exchange Online 15 dakika sonra aynı hedef etki alanı için bir DNS sorgusuyla başlayan doğrulama işleminin tamamını, bundan 15 dakika sonra ve bundan sonra da her saat 24 saatte bir yeniden denecek. 24 saat yeniden denemenin ardından kimlik doğrulaması başarısız olursa, iletinin süresi dolar ve hata ayrıntılarının yer olduğu bir NDR oluşturulur ve gönderene gönderilir. 

## <a name="what-are-the-components-of-dane"></a>DANE'nin bileşenleri nedir?

### <a name="tlsa-resource-record"></a>TLSA Kaynak Kaydı

TLS Authentication (TLSA) kaydı, sunucunun X.509 sertifikası veya ortak anahtar değerini kaydı içeren etki alanı adıyla ilişkilendirmek için kullanılır. TLSA kayıtlarına, yalnızca etki alanınız üzerinde DNSSEC etkinleştirildiğinde güvenilebilir. Etki alanınızı barındırmak için bir DNS sağlayıcısı kullanıyorsanız, bu sağlayıcıyla etki alanı yapılandırılamazken bu ayar sunabilirsiniz. DNSSEC bölge imzalama hakkında daha fazla bilgi edinmek için şu bağlantıyı ziyaret edin: [DNSSEC bölge yapısına genel | Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)). 
  
Örnek TLSA kaydı:
  
:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Örnek TLSA kaydı" lightbox="../media/compliance-trial/example-TLSA-record.png":::

TLSA kayıt türüne özgü dört yapılandırılabilir alan vardır: 

**Sertifika Kullanım Alanı**: Gönderen e-posta sunucusunun hedef e-posta sunucusunun sertifikasını nasıl doğrulası gerektiğini belirtir.

|Değer  |Kısaltma  |Açıklama |
|---------|---------|---------|
|01<sup></sup>     |PKIX-TA          |Kullanılan sertifika, X.509 güven zincirinden güven bağlantısı Genel CA'dır.          |
|11<sup></sup>     |PKIX-EE         |Hedef sunucu sertifika denetlenir; DNSSEC denetimlerinin orijinalliğini doğrulaması gerekir.          |
|2     |DANE-TA         |Güven zincirinin bir güven bağlantısı tarafından doğrulanması gereken X.509 ağacından sunucunun özel anahtarını kullanın. TLSA kaydı, etki alanı için TLS sertifikalarını doğrularken kullanılacak güven bağlayıcısını belirtir.         |
|3     |DANE-EE         |Yalnızca hedef sunucunun sertifikasıyla eşler.           |

<sup>1</sup> Exchange Online RFC uygulama kılavuzuna göre, DANE SMTP ile uygulanırken 0 veya 1 sertifika Kullanım Alanı değerlerinin kullanılmaması gerektiğini gösterir.   Sertifika Kullanımı alan değeri 0 veya 1 olan bir TLSA kaydı Exchange Online, Exchange Online olarak kabul edilir. Tüm TLSA kayıtları kullanılamaz bulunursa, Exchange Online e-posta gönderirken 0 veya 1 için DANE doğrulama adımlarını gerçekleştirmez. Bunun yerine, bir TLSA kaydının varlığı nedeniyle, Exchange Online e-posta göndermek için TLS kullanımını zorunlu tutan, hedef e-posta sunucusu TLS'yi destekliyorsa e-postayı gönderir veya e-postayı bırakarak ve hedef e-posta sunucusu TLS'yi desteklemezse NDR oluşturmada zorlar.     

Örnek TLSA kaydında, Sertifika Kullanım Alanı '3' olarak ayarlanmıştır; dolayısıyla Sertifika İlişki verileri ('abc123... xyz789') ile yalnızca hedef sunucunun sertifikasıyla eş kullanılabilir.

**Seçici alanı**: Hedef sunucu sertifikasının hangi bölümlerinin denetlen gerektiğini belirtir. 

|Değer  |Kısaltma  |Açıklama  |
|---------|---------|---------|
|0     |Sertifika         |Tam sertifika kullanın.         |
|1     |SPKI (Konu Ortak Anahtar Bilgileri)          |Sertifikanın ortak anahtarını kullanın ve ortak anahtarın hangi algoritmayla kullanacağız?          |

Örnek TLSA kaydında, Seçici Alanı '1' olarak ayarlanmıştır, böylece Sertifika İlişki İlişkisi Verileri hedef sunucu sertifikasının ortak anahtarı ve ortak anahtarın hangi algoritmayla tanımlanırsa algoritmayla eş kullanılabilir.

**Eşleşen Tür Alanı**: Sertifikanın TLSA kaydında temsil edilen biçimi gösterir. 

|Değer  |Kısaltma  |Açıklama  |
|---------|---------|---------|
|0     |Tam         |TSLA kaydında veriler tam sertifikadır veya SPKI'dir.          |
|1     |SHA-256         |TSLA kaydında veriler, sertifika veya SPKI'ye sahip bir SHA-256 karmasıdır.          |
|2     |SHA-512         |TSLA kaydında veriler, sertifika veya SPKI'ye sahip bir SHA-512 karmasıdır.         |

Örnek TLSA kaydında, Eşleşen Tür Alanı '1' olarak ayarlanır, dolayısıyla Sertifika İlişki İlişkisi Verileri hedef sunucu sertifikasından konu Ortak Anahtar Bilgisi'nin SHA-256 karması olur

**Sertifika İlişkili** Verileri: Hedef sunucu sertifikasıyla eşleştirmek için kullanılan sertifika verilerini belirtir. Bu veriler Seçici Alanı değerine ve Eşleşen Tür Değeri'ne bağlıdır.

Örnek TLSA kaydında, Sertifika İlişkisi verileri 'abc123... xyz789'. Örnekteki Seçici Alanı değeri '1' olarak ayarlı olduğu için, hedef sunucu sertifikasının ortak anahtarına ve bu sertifikayla birlikte kullanılacak algoritmaya başvurur. Ayrıca örnekteki Eşleşen Tür alan değeri '1' olarak ayarlarından, hedef sunucu sertifikasından Konu Ortak Anahtar Bilgisi'nin SHA-256 karma değerine de başvurulur.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Hangi müşterilerin Exchange Online SMTP DANE Giden Bağlantı'sı kullanabilir?

Müşteri Exchange Online olarak, giden e-postanız için bu gelişmiş e-posta güvenliğini yapılandırmak üzere bir şey yapmaya gerek yok. Bu sizin için bizim için inşa edilen ve tüm müşteriler için varsayılan olarak Exchange Online olan bir üründir ve hedef etki alanı DANE desteğinin tanıtımını yapmak için kullanılır. DNSSEC ve DANE denetimleriyle e-posta göndermenin avantajlarını yeniden elde etmek için, e-posta alışverişi gerçekleştirerek DNSSEC ve DANE'yi kullanmaları gereken iş ortaklarınızı bu standartları kullanarak e-posta almaları için bu iş ortaklarına ileti gönderin. 

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Müşterilerin gelen Exchange Online SMTP DANE'i nasıl kullanabilir?

Şu anda, gelen SMTP DANE bu konu için Exchange Online. Desteğin 2022'nin sonunda yayım bekleniyor. 

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Önerilen TLSA kayıt yapılandırması nedir?

Sertifika Kullanımı alanından 3 olarak ayarlanmış bir TLSA kaydı, 1 olarak ayarlanmış Seçici alanı ve 1 olarak ayarlanmış Eşleşen Tür alanı olan SMTP DANE için RFC uygulama kılavuzu başına önerilir. 

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online Posta Flow SMTP DANE ile birleştirme 

Aşağıdaki akış çizelgesinde gösterilen SMTP DANE ile Exchange Online için posta akış işlemi, DNSSEC aracılığıyla etki alanı ve kaynak kaydı güvenliğini, hedef posta sunucusunda TLS desteğini ve hedef posta sunucusunun sertifikasının ilişkili TLSA kaydına bağlı olarak beklenenle eşleşmesini doğrular. 

SMTP DANE hatasının e-postanın engellenmiş olması yalnızca iki senaryo vardır:

- Hedef etki alanı DNSSEC desteğine sinyal verdi ancak bir veya birden çok kayıt inauthentic olarak geri döndürüldü. 

- Hedef etki alanı için tüm MX kayıtları TLSA kayıtlarına sahip olup, hedef sunucunun sertifikalarının hiçbiri TSLA kayıt verilerinde beklenenle eşlenmiyor veya TLS bağlantısı hedef sunucu tarafından desteklenmiyor.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange DANE ile çevrimiçi posta akışı oluşturma" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>İlgili Teknolojiler 

|Teknoloji  |Ek Bilgiler  |
|---------|---------|
|Posta Aktarım Aracısı – Katı Aktarım Güvenliği **(MTA-STS), hedef e-posta sunucusunun TLS'yi** destekleyip destekleme olmadığını ve TLS'de görüşme yapılamasa da ne olacağını belirten etki alanı ilkelerini ayarlamaya yönelik bir mekanizma sağlayarak trtrt'nin indirilme ve Ortadaki Adam saldırılarını durdurmanıza yardımcı olur, örneğin iletimi durdurun.     |Gelen ve Exchange Online MTA-STS için yaklaşan desteği hakkında daha fazla bilgi bu yılın sonlarında yayımlanacak.     [Exchange Online Ignite 2020'den Aktarım Haberleri - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)<br /><br />[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461) |
|**Sender Policy Framework (SPF),** hedef e-posta sistemlerinin özel etki alanınız üzerinden gönderilen iletilere güven olduğundan emin olmak için IP bilgilerini kullanır.    |   [Sender Policy Framework (SPF) kimliği doğrunlamayı nasıl Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)      |
|**DomainKeys Tanımlanan Posta (DKIM),** hedef e-posta sistemlerinin özel etki alanınız üzerinden giden iletilere güven güveni sağlamak için X.509 sertifika bilgilerini kullanır.      | [DkIM'i özel etki alanınız içinde e-posta için kullanma - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)        |
|Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve **Uyumluluk (DMARC),** posta gönderenlerin kimliğini doğrulamak ve hedef e-posta sistemlerinin etki alanınız üzerinden gönderilen iletilere güven olduğundan emin olmak için Sender Policy Framework ve DomainKeys Tanımlanan Posta ile birlikte çalışır.      |  [E-postayı doğrulamak için DMARC kullanma, kurulum adımları - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)       |

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>SMTP DANE ile E-posta Gönderme sorunlarını giderme

Şu anda, E-posta ve Posta ile E-posta gönderirken DANE'Exchange Online. Microsoft bu hata kodu listesini etkin bir şekilde güncelleştiriyor. Hatalar şu şekilde görünür:
1.  İleti Exchange Görünümü aracılığıyla Yönetim Merkezi portalına gidin.
2.  BIR DANE veya DNSSEC hatası nedeniyle ileti gönderilmey olduğunda oluşturulan NDR'ler.
3.  Uzak Bağlantı Çözümleyicisi [aracı Microsoft Uzak Bağlantı Çözümleyicisi](https://testconnectivity.microsoft.com/tests/o365).

|NDR Kodu  |Açıklama  |
|---------|---------|
|5.7.321     |starttls-not-supported: Hedef posta sunucusu posta almak için TLS'yi desteklemeli.          |
|5.7.322     |sertifikanın süresi doldu: Hedef posta sunucusunun sertifikasının süresi doldu.          |
|5.7.323     |tlsa-invalid: Etki alanı DANE doğrulaması başarısız oldu.          |
|5.7.324     |dnssec-invalid: Hedef etki alanı geçersiz DNSSEC kayıtları döndürüldü.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>5.7.321 starttls-not-supported sorunlarını giderme

Bu genellikle hedef posta sunucusunda bir sorun olduğunu gösterir. İletiyi aldıktan sonra:
1.  Hedef e-posta adresinin doğru girilmiş olup olmadığını denetleyin.
2.  Hedef e-posta yöneticisini, bu hata kodunu aldıklarını ve böylece hedef sunucunun TLS kullanarak ileti alacak şekilde doğru yapılandırıp yapılandırılmadılarını belirleyeceklerini uyarın. 
3.  E-postayı göndermeyi yeniden deneyin ve Yönetim Merkezi portalında İleti İzleme Exchange gözden geçin.

### <a name="troubleshooting-57322-certificate-expired"></a>Sertifikanın süresi dolmuş 5.7.322 sorunlarını giderme

Gönderen e-posta sunucusuna süresi dolmamış geçerli bir X.509 sertifikası sun olmalıdır. X.509 sertifikaları yaygın olarak yıllık olarak sona erdikten sonra yenilenmesi gerekir. İletiyi aldıktan sonra:

1.  Hedef e-posta yöneticisine bu hata kodunu aldığınızı uyarın ve hata kodu dizesini girin.
2.  Hedef sunucu sertifikasının yenilenmesine ve TLSA kaydının yeni sertifikaya başvurulacak şekilde güncelleştirilsine izin verme. Ardından, e-postayı göndermeyi yeniden deneyin ve Yönetim Merkezi portalında iletinin İleti İzleme Exchange gözden geçin.

### <a name="troubleshooting-57323-tlsa-invalid"></a>5.7.323 tlsa-invalid sorunlarını giderme

Bu hata kodu BIR TLSA kaydının yanlış yapılandırılması ile ilgilidir ve ancak bir DNSSEC-authentic TLSA kaydı döndürüldikten sonra oluşturabilir. DANE doğrulaması sırasında, kayıt döndürüldikten sonra oluşan ve kodun oluşturulmalarına neden olan birçok senaryo vardır. Microsoft, bu hata kodu kapsamındaki senaryolar üzerinde etkin bir şekilde çalışarak her senaryonun belirli bir kodu olmasını sağlar. Şu anda, bu senaryolardan biri veya birden fazlası hata kodunun yeniltir 1.

1.  Hedef posta sunucusunun sertifikası orijinal TLSA kaydı başına beklenenle eşlenmiyor.
2.  Authentic TLSA kaydı yanlış yapılandırılmış.
3.  Hedef etki alanı saldırıya uğradığında.
4.  Diğer DANE hataları.

İletiyi aldıktan sonra:

1. Hedef e-posta yöneticisine bu hata kodunu aldığınızı uyarın ve onlara hata kodu dizesini girin.
2. Hedef e-posta yöneticisinin DANE yapılandırmasını ve e-posta sunucusu sertifikasının geçerliliğini gözden geçirmesi için zaman ver. Ardından, e-postayı göndermeyi yeniden deneyin ve Yönetim Merkezi portalında iletinin İleti İzleme Exchange gözden geçin.

### <a name="troubleshooting-57324-dnssec-invalid"></a>5.7.324 dnssec-invalid sorunlarını giderme

Bu hata kodu, hedef etki alanının DNSSEC-authentic olduğunu belirtti ancak Exchange Online DNSSEC-authentic olarak doğrulayamadı. 

İletiyi aldıktan sonra:

1. Hedef e-posta yöneticisine bu hata kodunu aldığınızı uyarın ve onlara hata kodu dizesini girin.
2. Hedef e-posta yöneticisinin etki alanının DNSSEC yapılandırmasını gözden geçirmesine izin ver. Ardından, e-postayı göndermeyi yeniden deneyin ve Yönetim Merkezi portalında iletinin İleti İzleme Exchange gözden geçin.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>SMTP DANE ile E-posta Alma Sorunlarını Giderme

Şu anda, alıcı etki alanının yöneticisinin bu standartları kullanarak kendi DNSSEC ve DANE yapılandırmalarından e-posta almak için Exchange Online kullanabileceği iki yöntem vardır. 

1. [RFC8460'ta](https://datatracker.ietf.org/doc/html/rfc8460) ilk kez sunuluyor SMTP TLS-RPT (Aktarım Katmanı Güvenlik Bildirimi) 
2. Uzak Bağlantı Çözümleyicisi aracını [Microsoft Uzak Bağlantı Çözümleyicisi aracını kullanma](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) , gönderenlerin, hedef etki alanı yöneticilerine, ilgili hedef etki alanlarındaki DANE ve MTA-STS başarıları ve hataları hakkında ayrıntılı bilgi sağlamaları için bir raporlama mekanizmasıdır. TLS-RPT raporları almak için, yalnızca raporlarınızı göndermek istediğiniz e-posta adresini veya URI'yi içeren etki alanı DNS kayıtlarına bir TXT kaydı eklemeniz gerekir. Exchange Online, TLS-RPT raporlarını JSON biçiminde gönderir. 

Örnek kayıt:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Örnek kayıt" lightbox="../media/compliance-trial/example-record.png":::

İkinci yöntem, hizmetin dışında e-posta gönderirken Exchange Online'in dns yapılandırmanız için de aynı DNSSEC ve DANE denetimlerini yapanın Uzak Bağlantı Çözümleyicisi [Microsoft](https://testconnectivity.microsoft.com/tests/o365) Uzak Bağlantı Çözümleyicisi'ni kullanmaktır. Bu, bu standartları kullanarak e-postayı yapılandırmadan almak için Exchange Online doğrudan yoludur. 

Sorun giderme sırasında aşağıdaki hata kodları oluşturulmuş olabilir:

|NDR Kodu  |Açıklama |
|---------|---------|
|4/5.7.321     |starttls-not-supported: Hedef posta sunucusu posta almak için TLS'yi desteklemeli.          |
|4/5.7.322     |sertifikanın süresi doldu: Hedef posta sunucusunun sertifikasının süresi doldu.          |
|4/5.7.323    |tlsa-invalid: Etki alanı DANE doğrulaması başarısız oldu.         |
|4/5.7.324     |dnssec-invalid: Hedef etki alanı geçersiz DNSSEC kayıtları döndürüldü.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>5.7.321 starttls-not-supported sorunlarını giderme

> [!NOTE]
> Bu adımlar, E-posta yöneticilerinin SMTP DANE kullanarak e-Exchange Online sorunlarını gidermeye yardımcı olur.

Bu genellikle hedef posta sunucusunda bir sorun olduğunu gösterir. Uzak Bağlantı Çözümleyicisi'nin bağlanmayı test etmekte olduğu posta sunucusu. Genellikle bu kodu oluşturan iki senaryo vardır: 

1.  Hedef posta sunucusu güvenli iletişimi hiç desteklemez ve düz, şifrelenmiş olmayan iletişim kullanılmalıdır. 
2.  Hedef sunucu yanlış yapılandırılmıştır ve STARTTLS komutunu yoksayar.
    
İletiyi aldıktan sonra:

1. E-posta adresini kontrol edin.
2. Deyimin ilişkilendirilen posta sunucusunu tanımlamak için hata deyimiyle ilişkilendirilmiş IP adresini bulun.
3. Posta sunucunuzun ayarını kontrol edin ve SMTP trafiğini (yaygın olarak 25 ve 587 bağlantı noktaları) dinlemek üzere yapılandırıldığından emin olun.
4. Birkaç dakika bekleyin, sonra Uzak Bağlantı Çözümleyicisi aracıyla sınamayı yeniden deneyin.
5. Yine de başarısız olursa, TLSA kaydını kaldırmayı deneyin ve sınamayı Uzak Bağlantı Çözümleyicisi aracıyla yeniden çalıştırın.
6. Hata yoksa, bu durum posta almak için kullanmakta olduğunuz posta sunucusunun STARTTLS'i destekleme olmadığını ve DANE'ı kullanmak için bunu destekleyen bir sunucuya yükseltmeniz gerek kullanabileceğinizi gösteriyor olabilir. 

### <a name="troubleshooting-57322-certificate-expired"></a>Sertifikanın süresi dolmuş 5.7.322 sorunlarını giderme

> [!NOTE]
> Bu adımlar, E-posta yöneticilerinin SMTP DANE kullanarak e-Exchange Online sorunlarını gidermeye yardımcı olur.

Gönderen e-posta sunucusuna süresi dolmamış geçerli bir X.509 sertifikası sun olmalıdır. X.509 sertifikaları yaygın olarak yıllık olarak sona erdikten sonra yenilenmesi gerekir. İletiyi aldıktan sonra:

1. Hata deyimiyle ilişkilendirilmiş IP'yi kontrol edin, böylece ilişkili posta sunucusunu tanımlayabilirsiniz. Tanım istediğiniz e-posta sunucusunda süresi dolan sertifikayı bulun.
2. Sertifika sağlayıcınızın web sitesinde oturum açma.
3. Süresi dolan sertifikayı seçin ve yenileme yönergelerini izleyin ve yenileme için ödeme uygulayın.
4. Sağlayıcınız satın alma işlemi doğruladıktan sonra yeni bir sertifika indirebilirsiniz.
5. Yenilenen sertifikayı ilişkili posta sunucusuna yükleyin.
6. Posta sunucusunun ilişkili TLSA kaydını yeni sertifikanın verileriyle güncelleştirin. 
7. Uygun bir süre bekledikten sonra, Uzak Bağlantı Çözümleyicisi aracıyla sınamayı yeniden deneyin.

### <a name="troubleshooting-57323-tlsa-invalid"></a>5.7.323 tlsa-invalid sorunlarını giderme

> [!NOTE]
> Bu adımlar, E-posta yöneticilerinin SMTP DANE kullanarak e-Exchange Online sorunlarını gidermeye yardımcı olur.

Bu hata kodu TLSA kaydının yanlış yapılandırılması ile ilgilidir ve yalnızca bir DNSSEC-authentic TSLA kaydı döndürüldikten sonra oluşturabilir. Ancak DANE doğrulaması sırasında, kayıt döndürüldikten sonra oluşan ve kodun oluşturulmalarına neden olan birçok senaryo vardır. Microsoft, bu hata kodu kapsamındaki senaryolar üzerinde etkin bir şekilde çalışarak her senaryonun belirli bir kodu olmasını sağlar. Şu anda, bu senaryolardan biri veya birden fazlası hata kodunun yeniltir 1.

1. Authentic TLSA kaydı yanlış yapılandırılmış.
2. Sertifika, gelecek bir zaman penceresi için henüz geçerli/yapılandırılmış zamanı değil. 
3. Hedef etki alanı saldırıya uğradı.
4. Diğer DANE hataları.

İletiyi aldıktan sonra:

1. İlişkili posta sunucusunu tanımlamak için hata deyimiyle ilişkilendirilmiş IP'yi kontrol edin. 
2. Tanımlanan posta sunucusuyla ilişkilendirilmiş TLSA kaydını tanımlama. 
3. Gönderene tercih edilen DANE denetimlerini gerçekleştirmesini ve doğru sertifika verilerini TLSA kaydına dahil ettiğine işaret edene emin olmak için, TLSA kaydının yapılandırmasını doğrulayın. 
    1. Tutarsızlıklar için kayıtta herhangi bir güncelleştirme yapmak zorunda kaldısanız, birkaç dakika bekleyin ve sonra Uzak Bağlantı Çözümleyicisi aracıyla testi yeniden çalıştırın. 
4. Tanımlanan posta sunucusunda sertifikayı bulun.
5. Sertifikanın geçerli olduğu zaman penceresini kontrol edin. Geçerliliği gelecekte bir tarihte başlatacak şekilde ayarlanırsa geçerli tarih için yenilenmesi gerekir.
    1. Sertifika sağlayıcınızın web sitesinde oturum açma.
    2. Süresi dolan sertifikayı seçin ve yenileme yönergelerini izleyin ve yenileme için ödeme uygulayın.
    3. Sağlayıcınız satın alma işlemi doğruladıktan sonra yeni bir sertifika indirebilirsiniz.
    4. Yenilenen sertifikayı ilişkili posta sunucusuna yükleyin.

### <a name="troubleshooting-57324-dnssec-invalid"></a>5.7.324 dnssec-invalid sorunlarını giderme

> [!NOTE]
> Bu adımlar, E-posta yöneticilerinin SMTP DANE kullanarak e-Exchange Online sorunlarını gidermeye yardımcı olur.

Bu hata kodu, hedef etki alanı bunun DNSSEC-authentic olduğunu belirtti ancak DNSSEC Exchange Online olarak doğrulayama geldiğinde oluşturulur. Bu bölüm DNSSEC sorunlarını gidermek için kapsamlı bir bölüm olmayacaktır ve etki alanlarının daha önce DNSSEC kimlik doğrulaması kullandı ancak şimdi değil, bu senaryolara odaklanır. 

İletiyi aldıktan sonra:

1. GoDaddy gibi bir DNS sağlayıcısı kullanıyorsanız, DNS sağlayıcınızı hataya karşı uyararak sorun giderme ve yapılandırma değişikliği üzerinde çalışmalarını sağlar. 
2. Kendi DNSSEC altyapınızı yönetiyorsanız, bu hata iletisini oluşturan birçok DNSSEC yanlış yapılandırması vardır. Bölgenizin daha önce DNSSEC kimlik doğrulamasını geçerek geçişte olup denetlemeniz gereken bazı yaygın sorunlar:
    1. Üst bölge alt bölgede olmayan bir şeye işaret ediyor bir dizi DS kaydına sahip olduğunda, bozuk güven zinciri. Bunun sonucunda alt bölge çözümleyiciler doğrulandı ve alt bölge geçersiz olarak işaretlenir. 
        - Alt etki alanları RRSIG anahtar kimliklerini gözden geçirerek ve üst bölgede yayımlanan DS kayıtlarında yer alan anahtar kimlikleriyle eşk sağlamayı sağlayarak bu sorunu giderin. 
    2. Etki alanının RRSIG kaynak kaydı için zaman geçerli değildir, süresi dolmuş veya geçerlilik dönemi henüz dolmamış olabilir. 
        - Geçerli zamanpanları kullanarak etki alanı için yeni imzalar oluşturarak bu sorunu çözebilirsiniz. 

## <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Müşteri Exchange Online, DNSSEC ve/veya DANE kullanmamayı tercih  miyim?

DNSSEC ve DANE'nin hizmetimizin güvenlik konumunu önemli ölçüde artıracaktır ve tüm müşterilerimizin bundan yararlanacaktır. Bu dağıtımın M365 müşterileri üzerindeki olası etki riskini ve önem derecesini azaltmak için geçen yıl boyunca titiz bir şekilde çalıştık. Dağıtım sırasında olumsuz etkinin en aza indirilmesi için dağıtımı etkin bir şekilde izlemeye ve izlemeye devam ediyoruz. Bu nedenle, kiracı düzeyinde özel durumlar veya geri vazgeçme seçeneği kullanılamaz.
DNSSEC ve/veya DANE'nin etkin olmasıyla ilgili herhangi bir sorun yaşamanız durumunda, bu belgede not alınan hataları araştırmanın farklı yöntemleri hatanın kaynağını tanımlamanıza yardımcı olur. Çoğu durumda, sorun dış hedef tarafla ilgili olur ve bu iş ortaklarına, bu standartları kullanarak Exchange Online'tan e-posta almak için DNSSEC ve DANE'yi doğru yapılandırmaları için bu iş ortaklarına haber göndermeniz gerekir.

### <a name="how-does-dnssec-relate-to-dane"></a>DNSSEC'in DANE ile nasıl ilişkili olduğunu nasıl sağlar?

DNSSEC, DNS sorgusuna yanıt olarak döndürülen kayıtların kimlik doğru olduğundan emin olmak için ortak anahtar altyapısından yararlanarak DNS çözümlemesine bir güven katmanı ekler. DANE, alıcı posta sunucusunun orijinal MX kaydı için geçerli ve beklenen posta sunucusu olduğunu garantiler. 

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>SMTP için MTA-STS ile DANE arasında ne fark vardır?

DANE ve MTA-STS aynı amaca hizmet verir, ama MTA-STS sertifika yetkililerine dayandırırken DANE, DNS kimlik doğrulaması için DNSSEC gerektirir. 

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Fırsatçı TLS neden yeterli değil?

Fırsatçı TLS, her ikisi de bunu desteklemeyi kabul ettiyse, iki uç nokta arasındaki iletişimi şifreler. Bununla birlikte, TLS iletimi şifrelese bile, DNS çözümlemesi sırasında etki alanı, etki alanının gerçek uç noktası yerine kötü niyetli bir actor'un uç noktasını görüntüde olacak şekilde kimlik aktarımına neden olabilir. Bu, E-posta güvenliğinde, DNSSEC ile MTA-STS ve/veya SMTP DANE'yi uygulayarak ele alınması gereken bir boşluktır.  

### <a name="why-isnt-dnssec-sufficient"></a>DNSSEC neden yeterli değil?

DNSSEC, posta akışı senaryoları için Ortadaki Adam saldırılarına tümüyle karşı karşı dayanıklı değildir ve posta akışı senaryoları için (TLS'den metni temizlemeye yönelik) saldırılara karşı tam karşıtlık sağlar. DNSSEC ile birlikte MTA-STS ve DANE'nin yanı sıra, HEM MITM'yi hem de azaltma saldırılarını trtrt etmek için kapsamlı bir güvenlik yöntemi sağlar.

## <a name="additional-links"></a>Ek Bağlantılar 

[Kendi etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[DNSSEC istemcisine genel | Microsoft Docs ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[E-postayı doğrulamak için DMARC kullanma, kurulum adımları - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[DkIM'i özel etki alanınıza gelen e-posta için kullanma - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Sender Policy Framework (SPF) kimliği doğrunlamayı nasıl Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online Ignite 2020'den Aktarım Haberleri - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)