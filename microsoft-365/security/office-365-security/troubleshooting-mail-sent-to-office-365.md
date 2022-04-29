---
title: Microsoft 365'e gönderilen posta sorunlarını giderme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, Microsoft 365 müşterilere toplu posta göndermeye yönelik en iyi yöntemler Microsoft 365 & gelen kutularına e-posta göndermeyle ilgili sorun giderme bilgileri sağlanır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 37703ccb0ffb37163033bb2fdca24566a33bb275
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128444"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Microsoft 365'e gönderilen posta sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

Bu makalede, Microsoft 365 gelen kutularına e-posta göndermeye çalışırken sorun yaşayan gönderenler için sorun giderme bilgileri ve müşterilere toplu posta göndermeye yönelik en iyi yöntemler sağlanır.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>IP'nizin ve etki alanınızın gönderen itibarını yönetiyor musunuz?

EOP filtreleme teknolojileri, Microsoft 365 ve Exchange Server gibi diğer Microsoft ürünleri için istenmeyen posta önleme koruması sağlamak üzere tasarlanmıştır. SpF, DKIM ve DMARC'yi de kullanırız; E-postayı gönderen etki alanının bunu yapma yetkisi olduğunu doğrulayarak kimlik sahtekarlığı ve kimlik avı sorununu gidermeye yardımcı olan e-posta kimlik doğrulama teknolojileri. EOP filtrelemesi, gönderen IP, etki alanı, kimlik doğrulaması, liste doğruluğu, şikayet oranları, içerik ve daha fazlası ile ilgili birçok faktörden etkilenir. Bunlardan biri, gönderenin itibarını ve e-posta teslim etme becerisini azaltmadaki temel faktörlerden biri gereksiz e-posta şikayet oranıdır.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Yeni IP adreslerinden e-posta mı gönderiyorsunuz?

Daha önce e-posta göndermek için kullanılmayan IP adreslerinin sistemlerimizde yerleşik olarak herhangi bir saygınlığı yoktur. Sonuç olarak, yeni IP'lerden gelen e-postaların teslim sorunlarıyla karşılaşma olasılığı daha yüksektir. IP, istenmeyen posta göndermeme ününü edindikten sonra, EOP genellikle daha iyi bir e-posta teslim deneyimi sağlar.

Mevcut SPF kayıtları altında kimliği doğrulanmış etki alanları için eklenen yeni IP'ler genellikle etki alanının gönderen saygınlığının bir kısmını devralma avantajından yararlanır. Etki alanınızın iyi bir gönderen saygınlığı varsa yeni IP'ler daha hızlı bir artış süresiyle karşılaşabilir. Hacmine, liste doğruluğuna ve gereksiz e-posta şikayet oranlarına bağlı olarak, yeni bir IP'nin birkaç hafta içinde veya daha erken bir sürede tamamen artması beklenebilir.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>DNS'nizin doğru ayarlandığını onaylayın

Posta yönlendirme için gereken MX kaydı da dahil olmak üzere DNS kayıtlarını oluşturma ve koruma yönergeleri için DNS barındırma sağlayıcınıza başvurmanız gerekir.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Kendinizi yönlendirilemeyen bir IP olarak tanıtmadığınızdan emin olun

Ters DNS araması başarısız olan gönderenlerden gelen e-postaları kabul etmeyebiliriz. Bazı durumlarda, yasal gönderenler EOP bağlantısını açmaya çalışırken kendilerini yanlış bir şekilde İnternet'e yönlendirilebilir IP olarak tanıtır. Özel (yönlendirilemeyen) ağ için ayrılmış IP adresleri şunlardır:

- 192.168.0.0/16 (veya 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (veya 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (veya 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Office 365'da kullanıcıya e-posta gönderirken teslim edilmedi raporu (NDR) aldınız

Bazı teslim sorunları, gönderenin IP adresinin Microsoft tarafından engellenmesinin veya kullanıcı hesabının önceki istenmeyen posta etkinliği nedeniyle yasaklanmış gönderen olarak tanımlanmasının sonucudur. NDR'yi hatayla aldığınıza inanıyorsanız, sorunu çözmek için önce NDR iletisindeki yönergeleri izleyin.

Aldığınız hata hakkında daha fazla bilgi için Exchange Online'da [E-posta teslim edilmedi raporlarındaki](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online) hata kodlarının listesine bakın.

 Örneğin, aşağıdaki NDR'yi alırsanız, gönderen IP adresinin Microsoft tarafından engellendiğini gösterir:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Bu listeden kaldırma isteğinde bulunmak için [Listeden kaldırma portalını kullanarak kendinizi engellenen gönderenler listesinden kaldırabilirsiniz](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>E-postam alıcının Gereksiz E-posta klasörüne geldi

EOP tarafından hatalı bir şekilde istenmeyen posta olarak tanımlanan bir ileti varsa, alıcıyla birlikte çalışarak bu hatalı pozitif iletiyi Microsoft İstenmeyen Posta Çözümleme Ekibi'ne gönderebilirsiniz. Bu ileti, iletiyi değerlendirir ve analiz eder. Daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>IP adresimden gelen trafik EOP tarafından kısıtlandı

EOP'den IP adresinizin EOP tarafından kısıtlandığını belirten bir NDR alırsanız, örneğin:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

IP adresinden şüpheli etkinlik algılandığından ve daha fazla değerlendirilirken geçici olarak kısıtlandığından NDR'yi aldınız. Değerlendirme yoluyla şüphe giderilirse, bu kısıtlama kısa süre sonra kaldırılacaktır.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Microsoft 365'da gönderenlerden e-posta alamıyorum

 Kullanıcılarımızdan ileti almak için ağınızın EOP'nin veri merkezlerimizde kullandığı IP adreslerinden bağlantılara izin verdiğinden emin olun. Daha fazla bilgi için bkz. [IP adreslerini Exchange Online Protection](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Microsoft 365 kullanıcılara toplu e-posta göndermek için en iyi yöntemler

Kullanıcıları Microsoft 365 için sık sık toplu e-posta kampanyaları yürütüyorsanız ve e-postalarınızın güvenli ve zamanında ulaştığından emin olmak istiyorsanız, bu bölümdeki ipuçlarını izleyin.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Kimden adının iletiyi gönderen kişiyi yansıtdığından emin olun

Konu, iletinin ne hakkında olduğuna ilişkin kısa bir özet olmalıdır ve ileti gövdesi teklifin, hizmetin veya ürünün ne hakkında olduğunu açıkça ve kısaca belirtmelidir. Örneğin:

Doğru:

> Kimden: marketing@shoppershandbag.com <br> Konu: Noel sezonu için katalog güncelleştirildi!

Yanlış:

> Kimden: someone@outlook.com <br> Konu: Kataloglar

İnsanların kim olduğunuzu ve ne yaptığınızı bilmelerini ne kadar kolay hale getirirseniz, çoğu istenmeyen posta filtresi aracılığıyla teslim etmede o kadar az zorluk yaşarsınız.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Kampanya e-postalarına her zaman abonelikten çıkma seçeneği ekleyin

Pazarlama e-postaları, özellikle de bültenler, her zaman gelecekteki e-postalardan abonelikten çıkmak için bir yol içermelidir. Örneğin:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Bazı gönderenler, alıcıların konu başlığında "Aboneliği kaldır" olan belirli bir diğer adla e-posta göndermesini gerektirerek bu seçeneği içerir. Bu, yukarıdaki tek tıklamalı örnek için tercih edilemez. Alıcıların posta göndermesini zorunlu kılarsanız, bağlantıya tıkladığında tüm gerekli alanların önceden doldurulduğundan emin olun.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Pazarlama e-postası veya bülten kaydı için çift kabul etme seçeneğini kullanın

Şirketiniz ürün veya hizmetlerinize erişmek için kullanıcıları iletişim bilgilerini kaydetmeye ihtiyaç duyuyorsa veya teşvik ederse bu sektördeki en iyi uygulama önerilir. Bazı şirketler, kayıt işlemi sırasında pazarlama e-postaları veya e-bültenleri için kullanıcılarını otomatik olarak kaydetmeyi bir uygulama haline getirir, ancak bu, e-posta filtreleme dünyasında şüpheli bir pazarlama uygulaması olarak kabul edilir.

Kayıt işlemi sırasında varsayılan olarak "Evet, lütfen bülteninizi gönderin" veya "Evet, lütfen bana özel teklifler gönderin" onay kutusu seçiliyse, çok dikkat etmeyen kullanıcılar istemeden almak istemedikleri pazarlama e-postalarına veya bültenlerine kaydolabilir.

 Microsoft bunun yerine çift kabul etme seçeneğini önerir; bu da pazarlama e-postaları veya bültenleri için onay kutusunun varsayılan olarak işaretsiz olduğu anlamına gelir. Ayrıca, kayıt formu gönderildikten sonra, kullanıcıya pazarlama e-postaları alma kararını onaylamasına olanak tanıyan bir URL ile bir doğrulama e-postası gönderilir.

 Bu, yalnızca pazarlama e-postası almak isteyen kullanıcıların e-postalara kaydolmasını sağlamaya yardımcı olur ve daha sonra gönderen şirketi şüpheli e-posta pazarlama uygulamalarından temizler.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>E-posta iletisi içeriğinin saydam ve izlenebilir olduğundan emin olun

E-postaların gönderilme şekli, içerdikleri içerik kadar önemlidir. E-posta içeriği oluştururken, e-postalarınızın e-posta filtreleme hizmetleri tarafından işaretlenmemesini sağlamak için aşağıdaki en iyi yöntemleri kullanın:

- E-posta iletisi alıcıların göndereni adres defterine eklemesini istediğinde, bu tür bir eylemin teslim garantisi olmadığını açıkça belirtmelidir.

- İletinin gövdesine dahil edilen yeniden yönlendirmeler, birden çok ve çeşitli değil, benzer ve tutarlı olmalıdır. Bu bağlamdaki bir yeniden yönlendirme, bağlantı ve belgeler gibi iletiden uzak olan herhangi bir şeydir. Çok fazla reklam veya Abonelikten Çıkma bağlantınız varsa veya Profil bağlantılarını güncelleştirdiyseniz, hepsi aynı etki alanına işaret etmelidir. Örneğin:

  Doğru (tüm etki alanları aynıdır):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Yanlış (tüm etki alanları farklıdır):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Büyük resim ve ekleri olan içeriklerden veya yalnızca bir görüntüden oluşan iletilerden kaçının.

- Genel gizlilik veya P3P ayarlarınız, izleme piksellerinin (web hataları veya işaretleri) varlığını açıkça belirtmelidir.

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Veritabanlarınızdan yanlış e-posta diğer adlarını kaldırma

Veritabanınızda geri dönüş oluşturan tüm e-posta diğer adları gereksizdir ve e-posta filtreleme hizmetleri tarafından daha fazla inceleme için giden e-postalarınızı riske atar. E-posta veritabanınızın güncel olduğundan emin olun.
