---
title: Sender Policy Framework (SPF) kimliği doğrunlamayı nasıl önlez?
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 12/15/2016
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3aff33c5-1416-4867-a23b-e0c0c5b4d2be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Hedef e Microsoft 365 sistemlerinin özel etki alanınız üzerinden gönderilen iletilere güven güvensin diye DNS'deki Sender Policy Framework (SPF) TXT kaydını nasıl kullandığını öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 76bc783dc624487b438ca41dcd9fc38bd9bce911
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006807"
---
# <a name="how-microsoft-365-uses-sender-policy-framework-spf-to-prevent-spoofing"></a>How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 **Özet:** Bu makalede, hedef e-Microsoft 365 sistemlerinin özel etki alanınız tarafından gönderilen iletilere güveni sağlamak için, DNS'deki Sender Policy Framework (SPF) TXT kaydını nasıl kullandığı açıklanmıştır. Bu durum, bir postadan gönderilen giden Microsoft 365. E-postadan Microsoft 365 alıcıya gönderilen Microsoft 365 her zaman SPF'yi geçecektir.

SPF TXT kaydı, e-posta iletilerinin gönderildiği etki alanı adını doğrularsanız kimlik sahtesini ve kimlik avını önlemeye yardımcı olan bir DNS kaydıdır. SPF, gönderenin IP adresini gönderen etki alanının iddia edilen sahibiyle doğruarak e-posta iletilerinin kaynağını doğrular.

> [!NOTE]
> SPF kayıt türleri, İnternet Mühendislik Görev Gücü (IETF) tarafından 2014'te kullanım dışıdır. Bunun yerine, SPF bilginizi yayımlamak için DNS'de TXT kayıtlarını kullanmaya devam edin. Bu makalenin kalan bölümü netlik için SPF TXT kaydı terimini kullanır.

Etki alanı yöneticileri DNS'de TXT kayıtlarında SPF bilgilerini yayımlar. SPF bilgileri, yetkili giden e-posta sunucularını tanımlar. Hedef e-posta sistemleri iletilerin yetkili giden e-posta sunucularından geldiğini doğrular. SPF'yi zaten biliyorsanız veya basit bir dağıtımınız varsa ve yalnızca Microsoft 365 için DNS'e SPF TXT kaydınıza neleri ekleyileceğini biliyorsanız, spooflamayı önlemeye yardımcı olmak için [Microsoft 365'de SPF'yi](set-up-spf-in-office-365-to-help-prevent-spoofing.md) ayarlama'ya gidebilirsiniz. Microsoft 365'te tümüyle barındırılan bir dağıtımınız yoksa veya SPF'nin nasıl çalıştığını veya SPF için SPF sorunlarının nasıl giderilir hakkında daha fazla bilgi Microsoft 365 okumaya devam edin.

> [!NOTE]
> Daha önce, SharePoint Online'da da kullandıysanız, özel etki alanınıza farklı bir SPF TXT kaydı SharePoint vardı. Bu artık gerekli değildir. Bu değişiklik, Çevrimiçi bildirim SharePoint Gereksiz E-posta klasörüne kadar olan iletilerden çalışma riskini azaltmalı. Hemen hiçbir değişiklik yapmak zorunda değilsiniz, ancak "çok fazla arama" hatası alırsanız, SPF TXT kaydınızı, spoofingi önlemeye yardımcı olmak için [Microsoft 365'de SPF'yi ayarlama konusunda açıklandığı gibi değiştirebilirsiniz](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

## <a name="how-spf-works-to-prevent-spoofing-and-phishing-in-microsoft-365"></a>SPF, kimlik avından ve kimlik avından korunmak için Microsoft 365
<a name="HowSPFWorks"> </a>

SPF, gönderenin bir etki alanı adına göndermesine izin veriip verilmediğini belirler. Gönderenin bunu yapmalarına izin verilmezse, yani e-posta alıcı sunucuda SPF denetimine başarısız olursa, iletiyle ne yapacaklarını bu sunucuda yapılandırılan istenmeyen posta ilkesi belirler.

Her SPF TXT kaydı üç parça içerir: SPF TXT kaydı olduğu bildirimi, etki alanınız ve etki alanınız adına gönderabilecek dış etki alanlarıyla birlikte bir zorlama kuralı göndermesine izin verilen IP adresleri. Geçerli bir SPF TXT kaydında bu üçüne de ihtiyacınız var. Bu makalede, SPF TXT kaydınızı nasıl formunuz açıklanmıştır ve bu kaydın çalışmasında en iyi Microsoft 365. Kaydınızı DNS'de yayımlamak için etki alanı kayıt şirketiyle çalışma yönergelerinin bağlantıları da sağlanır.

### <a name="spf-basics-ip-addresses-allowed-to-send-from-your-custom-domain"></a>SPF hakkında temel bilgiler: Özel etki alanınız üzerinden göndern izin verilen IP adresleri
<a name="SPFBasicsIPaddresses"> </a>

SPF kuralının temel söz dizimi'ne bakın:

v=spf1 \<IP\> \<enforcement rule\>

Örneğin, aşağıdaki SPF kuralının bu kural için var olduğunu contoso.com:

v=spf1 \<IP address #1\> \<IP address #2\> \<IP address #3\> \<enforcement rule\>

Bu örnekte SPF kuralı, alıcı e-posta sunucusuna yalnızca etki alanı için bu IP adreslerinden posta kabul etmelerini contoso.com:

- IP adresi #1

- IP adresi 2

- IP adresi #3

Bu SPF kuralı, alıcı e-posta sunucusuna bu üç IP adresinden bir ileti contoso.com ancak bu üç IP adresi arasında değil de, alıcı sunucunun zorlama kuralını iletiye uygulaması gerektiğini söyler. Zorlama kuralı genellikle şu seçeneklerden biri olur:

- **Zor başarısız.** İleti zarfını 'zor başarısız' olarak işaretlenin ve sonra da alıcı sunucunun bu tür ileti için yapılandırılmış istenmeyen posta ilkesine uygun olarak izleyin.

- **Yumuşak başarısız.** İleti zarfta 'yumuşak başarısız' olarak iletiyi işaretleme. Normalde, e-posta sunucuları yine de bu iletileri teslim edecek şekilde yapılandırılır. Son kullanıcıların çoğu bu işareti görmüyor.

- **Nötr.** Hiçbir şey yapma, başka bir şey yapma, ileti zarfını işaretleme. Bu genellikle test amacıyla ayrılmıştır ve nadiren kullanılır.

Aşağıdaki örnekler, SPF'nin farklı durumlarda nasıl çalıştığını gösterir. Bu örneklerde, contoso.com gönderendir ve woodgrovebank.com alıcıdır.

### <a name="example-1-email-authentication-of-a-message-sent-directly-from-sender-to-receiver"></a>Örnek 1: Doğrudan gönderenden alıcıya gönderilen iletinin e-posta kimlik doğrulaması
<a name="spfExample1"> </a>

SPF, gönderenden alıcıya giden yol doğrudan olduğunda en iyi şekilde çalışır; örneğin:

![SPF'nin doğrudan sunucudan sunucuya gönderilirken e-postayı nasıl kimlik doğrulamasını gösteren diyagram.](../../media/835c20a7-ed4c-49c4-91fe-b8ebb3e452a1.jpg)

Bu woodgrovebank.com ileti aldığında, IP adresi #1 contoso.com için SPF TXT kaydında yer alıyorsa, ileti SPF onay kutusunu geçer ve kimliği doğrulanır.

### <a name="example-2-spoofed-sender-address-fails-the-spf-check"></a>Örnek 2: Kimliği doğruamayan gönderen adresi SPF denetimi başarısız olur
<a name="spfExample2"> </a>

Bir kimlik avının kimlik sahtecisi tarafından kimlik contoso.com:

![SPF'nin kimlik doğrulaması yapılan bir sunucudan gönderilirken e-postanın nasıl kimlik doğrulamasını gösteren diyagram.](../../media/235dac3d-cdc5-466e-86e0-37b5979de198.jpg)

IP adresi #12, contoso.com'un SPF TXT kaydında yer almamıştır, ancak ileti SPF denetiminde başarısız olur ve alıcı bunu istenmeyen posta olarak işaretlemeyi seçebilir.

### <a name="example-3-spf-and-forwarded-messages"></a>Örnek 3: SPF ve iletili iletiler
<a name="spfExample3"> </a>

SPF'nin bir dezavantajı, e-posta iletildiklerinden sonra çalışmay olmasıdır. Örneğin, e-postanın woodgrovebank.com bir hesapta tüm e-postayı gönderecek bir iletme kuralı ayarla olduğunu outlook.com düşünün:

![İleti iletilirken SPF'nin e-posta kimliğini nasıl doğrulayamadı gösteren diyagram.](../../media/6e92acd6-463e-4a1b-8327-fb1cf861f356.jpg)

İleti başlangıçta woodgrovebank.com'de SPF denetimi geçer ancak IP #25, contoso.com'un SPF TXT kaydında yer almay olduğundan outlook.com'deki SPF denetiminde başarısız olur. Outlook.com bu şekilde iletiyi istenmeyen posta olarak işaretlebilirsiniz. Bu sorunu geçici olarak çözmek için, SPF'yi DKIM ve DMARC gibi diğer e-posta kimlik doğrulama yöntemleriyle birlikte kullanın.

### <a name="spf-basics-including-third-party-domains-that-can-send-mail-on-behalf-of-your-domain"></a>SPF hakkında temel bilgiler: Etki alanınız adına posta gönderen üçüncü taraf etki alanlarını ekleme
<a name="SPFBasicsIncludes"> </a>

IP adreslerine ek olarak, SPF TXT kaydınızı etki alanlarını gönderen olarak içerecek şekilde de yapılandırabilirsiniz. Bunlar SPF TXT kaydına "include" deyimleri olarak eklenir. Örneğin, contoso.com, sahip olduğu Posta ve Posta contoso.net posta contoso.org TÜM IP adreslerini eklemek istiyor olabilir. Bunu yapmak için, contoso.com şöyle bir SPF TXT kaydı yayımlar:

```text
v=spf1 include:contoso.net include:contoso.org -all
```

Alıcı sunucu DNS'de bu kaydı bulduğunda, aynı zamanda DNS için SPF TXT kaydında ve sonra bu kayıt için contoso.net DNS contoso.org. Kayıtlarda ek bir include deyimi bulursa contoso.net contoso.org ifade de bu ifadeden sonra gelecektir. Hizmet reddi saldırılarını önlemeye yardımcı olmak için, tek bir e-posta iletisi için DNS araması sayısı üst sayısı 10'dır. Her include deyimi, ek bir DNS aramasını temsil eder. Bir ileti 10 sınırı aşarsa, ileti SPF'de başarısız olur. İleti bu sınıra ulaştığında, alıcı sunucunun yapılandırma türüne bağlı olarak, gönderen iletinin "çok fazla arama" üretmiş olduğunu veya "ileti için maksimum atlama sayısı aşıldı" (bu durum, aramalar döngüye alınıp DNS zaman aşımını aşıldığında meydana gelir) iletisi alabilirsiniz. Bunu önlemeye yönelik ipuçları için bkz. Sorun [Giderme: SPF için en iyi Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="requirements-for-your-spf-txt-record-and-microsoft-365"></a>SPF TXT kaydınız ve kaydınız için Microsoft 365
<a name="SPFReqsinO365"> </a>

Postayı kendi etki alanınız için Microsoft 365 ayarsanız, Microsoft mesajlaşma sunucularını etki alanınız için yasal bir posta kaynağı olarak tanımlayan bir SPF TXT kaydı zaten oluşturdunız. Bu kayıt büyük olasılıkla şöyledir:

```text
v=spf1 include:spf.protection.outlook.com -all
```

Tam barındırılan bir müşteriysiniz, başka bir ifadeyle giden posta gönderen şirket içi posta sunucularınız yoksa, bu sunucu için yayımlamanız gereken tek SPF TXT kaydı Office 365.

Karma bir dağıtımınız varsa (başka bir ifadeyle, bazı posta kutularınız şirket içinde ve bazıları da Microsoft 365'te barındırıldı) veya Exchange Online Protection (EOP) tek başına müşterisiysiniz (başka bir ifadeyle, şirket içi posta kutularınızı korumak için EOP kullanıyorsa), şirket içi uç posta sunucularınızın her biri için giden IP adresini DNS'deki SPF TXT kaydına eklemalısınız.

## <a name="form-your-spf-txt-record-for-microsoft-365"></a>Daha fazla bilgi için SPF TXT Microsoft 365
<a name="FormYourSPF"> </a>

Özel etki alanınız için SPF TXT kaydını oluşturmak üzere bu makaledeki söz dizimi bilgilerini kullanın. Burada bahsed yer alsa da en sık kullanılan seçenekler söz dizimi seçenekleridir. Kaydınızı kurduktan sonra, etki alanı kayıt şirketinizin kaydını güncelleştirmeniz gerekir.

Etki alanlarıyla ilgili olarak bu etki alanlarını dahil etmek Microsoft 365 bkz. [SPF için gereken dış DNS kayıtları](../../enterprise/external-domain-name-system-records.md). Etki [alanı kayıt şirketinizin](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) SPF (TXT) kayıtlarını güncelleştirmek için adım adım yönergeleri kullanın.

### <a name="spf-txt-record-syntax-for-microsoft-365"></a>Microsoft 365 için SPF TXT kaydı söz Microsoft 365
<a name="SPFSyntaxO365"> </a>

Aşağıdaki söz dizimlerini kullanarak, Microsoft 365 bir SPF TXT kaydı vardır:

```text
v=spf1 [<ip4>|<ip6>:<IP address>] [include:<domain name>] <enforcement rule>
```

Örneğin:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 include:spf.protection.outlook.com -all
```

burada:

- **v=spf1** gereklidir. Bu, TXT kaydını SPF TXT kaydı olarak tanımlar.

- **ip4** , IP sürüm 4 adreslerini kullanmakta olduğunu gösterir. **ip6** , IP sürüm 6 adreslerini kullanmakta olduğunu gösterir. IPv6 IP adresleri kullanıyorsanız, bu makaledeki **örneklerde yer alan ip4'ü** **ip6** ile değiştirin. Ayrıca CIDR notasyonu kullanarak IP adresi aralıklarını da belirtebilirsiniz; örneğin **ip4:192.168.0.1/26**.

- _IP adresi_ , SPF TXT kaydına eklemek istediğiniz IP adresidir. Genelde, bu IP adresi, kuruluşun giden posta sunucusunun IP adresidir. Birden çok giden posta sunucusu listeabilirsiniz. Daha fazla bilgi için bkz. Örnek: Birden çok giden şirket içi posta sunucusu için [SPF TXT kaydı ve şu Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#ExampleSPFMultipleMailServerO365).

- _etki alanı_ adı, yasal bir gönderen olarak eklemek istediğiniz etki alanıdır. Etki alanı adları listesine bu adlar için Microsoft 365 bkz. [SPF için gereken dış DNS kayıtları](../../enterprise/external-domain-name-system-records.md).

- Zorlama kuralı genellikle aşağıdaki kurallardan biridir:

  - -all

    Zor başarısız olduğunu gösterir. Etki alanınız için tüm yetkili IP adreslerini biliyorsanız, bunları SPF TXT kaydında listelenin ve -all (sabit başarısız) niteleyicisini kullanın. Ayrıca, yalnızca SPF kullanıyorsanız, yani DMARC veya DKIM kullanmıyorsanız, -all niteleyicisi kullan gerekir. Her zaman bu niteleyiciyi öneririz.

  - ~all

    Yumuşak başarısız olduğunu gösterir. IP adreslerinin tam listesine sahip olup olmadığınız konusunda emin değilsiniz, ~all (yumuşak başarısız) niteleyicisini kullansanız iyi olur. Ayrıca, DMARC'ı p=karantina veya p=reddet ile kullanıyorsanız, ~all kullanabilirsiniz. Aksi takdirde,-all kullanın.

  - ?all

    Nötr değeri gösterir. Bu, SPF'yi test etmek için kullanılır. Canlı dağıtımda bu niteleyiciyi kullanmamanızı öneririz.

### <a name="example-spf-txt-record-to-use-when-all-of-your-mail-is-sent-by-microsoft-365"></a>Örnek: Postanın hepsi postanız bir posta tarafından gönder) için SPF TXT Microsoft 365
<a name="ExampleSPFNoSP"> </a>

Postanın hepsi postanız Posta Microsoft 365, bunu SPF TXT kaydında kullanın:

```text
v=spf1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-a-hybrid-scenario-with-one-on-premises-exchange-server-and-microsoft-365"></a>Örnek: Tek bir şirket içi posta ve posta modeliyle karma bir senaryo için SPF TXT Exchange Server Microsoft 365
<a name="ExampleSPFHybridOneExchangeServer"> </a>

Karma bir ortamda, şirket içi Exchange Server IP adresi 192.168.0.1 ise, SPF zorlama kuralını zor başarısız olacak şekilde ayarlamak için SPF TXT kaydını aşağıdaki gibi yapın:

```text
v=spf1 ip4:192.168.0.1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-multiple-outbound-on-premises-mail-servers-and-microsoft-365"></a>Örnek: Birden çok giden şirket içi posta sunucusu ve posta sunucusu için SPF TXT Microsoft 365
<a name="ExampleSPFMultipleMailServerO365"> </a>

Birden çok giden posta sunucunuz varsa, her posta sunucusunun IP adresini SPF TXT kaydına dahil edin ve her IP adresini bir boşlukla ve ardından bir "ip4:" deyimiyle birbirinden ayırın. Örneğin:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 ip4:192.168.0.3 include:spf.protection.outlook.com -all
```

## <a name="next-steps-set-up-spf-for-microsoft-365"></a>Sonraki adımlar: SPF'yi iş için Microsoft 365
<a name="SPFNextSteps"> </a>

SPF TXT kaydınızı formüle ettiyken, bu kaydı etki alanınıza eklemek için [Microsoft 365'de SPF'yi](set-up-spf-in-office-365-to-help-prevent-spoofing.md) ayarlama'daki adımları izleyin.

SPF, her ne kadar spooflamayı önlemeye yardımcı olmak için tasarlanmış olsa da, SPF'nin karşı koruyamaz olduğu başka yöntemler de vardır. Bunlara karşı korunmak için, SPF'yi ayarlamış olduktan sonra DKIM ve DMARC'yi de SPF için Microsoft 365. Kullanmaya başlamak için bkz. DkIM kullanarak belirli bir yıl içinde özel [etki alanınıza gönderilen giden e-postayı Microsoft 365](use-dkim-to-validate-outbound-email.md). Ardından, bkz. [DMARC kullanarak e-postayı doğrulamak için Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="troubleshooting-best-practices-for-spf-in-microsoft-365"></a>Sorun giderme: SPF için en iyi Microsoft 365
<a name="SPFTroubleshoot"> </a>

Özel etki alanınız için yalnızca bir SPF TXT kaydı oluşturabilirsiniz. Birden çok kayıt oluşturmak tek durumuna neden olur ve SPF başarısız olur. Bunu önlemek için, her alt etki alanı için ayrı kayıtlar oluşturabilirsiniz. Örneğin, bu kayıt için bir kayıt contoso.com kaydı ve kayıt için de başka bir bulkmail.contoso.com.

E-posta iletisi teslime başlamadan önce 10'dan fazla DNS aramasına neden oluyorsa, alıcı posta sunucusu kalıcı bir hatayla (  _permerror_ olarak da adlandırılan) yanıt verir ve iletinin SPF denetimi başarısız olmasına neden olur. Alıcı sunucu, aşağıdakine benzer bir hata içeren bir teslim edilemedi raporuyla (NDR) de yanıt verir:

- İleti atlama sayısını aştı.

- İletide çok fazla arama gerekiyor.

## <a name="avoiding-the-too-many-lookups-error-when-you-use-third-party-domains-with-microsoft-365"></a>Birden çok aramayla üçüncü taraf etki alanlarını kullanırken "çok fazla arama" Microsoft 365
<a name="SPFTroubleshoot"> </a>

Bazı üçüncü taraf etki alanları için SPF TXT kayıtları, alıcı sunucuyu çok fazla sayıda DNS araması yapmak üzere yönlendirin. Örneğin, bu yazma zamanında, Salesforce.com kaydına 5 deyim içerir:

```text
v=spf1 include:_spf.google.com
include:_spfblock.salesforce.com
include:_qa.salesforce.com
include:_spfblock1.salesforce.com
include:spf.mandrillapp.com mx ~all
```

Hatadan kaçınmak için, herkesin toplu e-posta gönderdiği bir ilkeyi (örneğin, bu amaçla) özel olarak bir alt etki alanı kullanması gerekir. Ardından, toplu e-postayı içeren alt etki alanı için farklı bir SPF TXT kaydı tanımlarsınız.

 Örneğin, salesforce.com gibi bazı durumlarda, SPF TXT kaydında etki alanını kullanasınız, ancak bazı durumlarda üçüncü taraf bu amaçla kullanmak üzere bir alt etki alanı oluşturdu olabilir. Örneğin, exacttarget.com SPF TXT kaydınız için kullanmak üzere bir alt etki alanı oluşturdu:

```text
cust-spf.exacttarget.com
```

SPF TXT kaydınıza üçüncü taraf etki alanlarını dahil ederken, 10 arama sınırına ulaşmayacak şekilde üçüncü taraf hangi etki alanını veya alt etki alanını kullanacaktır? ile doğrulamanız gerekir.

## <a name="how-to-view-your-current-spf-txt-record-and-determine-the-number-of-lookups-that-it-requires"></a>Geçerli SPF TXT kaydınızı görüntüleme ve gereken arama sayısını belirleme
<a name="SPFTroubleshoot"> </a>

SPF TXT kaydınız da dahil olmak üzere DNS kayıtlarınızı görüntülemek için nslookup kullanabilirsiniz. SPF TXT kaydınızı içeriğini görüntülemek için kullanabileceğiniz bir dizi ücretsiz çevrimiçi araç vardır. SPF TXT kaydınıza bakarak ve deyimler ve yeniden yönlendirmeler zincirini takiperek, kaydın kaç DNS araması gerektirdiğini bulabilirsiniz. Bazı çevrimiçi araçlar bu aramaları sizin için bile sayar ve görüntüler. Bu numarayı izlemek, kuruluştan gelen iletilerin alıcı sunucudan gelen perm hatası olarak adlandırılan kalıcı bir hatayı tetiklemesini önlemeye yardımcı olur.

## <a name="for-more-information"></a>Daha fazla bilgi için
<a name="SPFTroubleshoot"> </a>

SPF TXT kaydını eklemek için yardıma mı ihtiyacınız var? Microsoft 365'te özel etki alanınız ile Sender Policy Framework kullanımı hakkında ayrıntılı bilgi için Microsoft 365 için herhangi bir DNS barındırma sağlayıcısında [DNS](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) kayıtları oluşturma makalesini Microsoft 365. [İstenmeyen posta önleme ileti üst bilgileri](anti-spam-message-headers.md), SPF denetimleri için posta Microsoft 365 kullanılan söz dizimi ve üst bilgi alanlarını içerir.
