---
title: Microsoft 365'a gönderilen postanın sorunlarını giderme
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
description: Bu makalede, e-postanın gelen kutularına gönderilmesiyle ilgili sorunlar için sorun giderme bilgileri Microsoft 365 &, müşterilere toplu posta Microsoft 365 sağlar.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f5fe128989b66f110899e6af08180e830319b739
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006801"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Microsoft 365'a gönderilen postanın sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

Bu makalede, aynı makaledeki gelen kutularına e-posta göndermeye çalışırken sorun yaşayan gönderenler için sorun giderme bilgileri ve Microsoft 365 toplu postayla ilgili en iyi yöntemler sunulmaktadır.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>IP'nizin ve etki alanının gönderme itibarını mı yönetiyorsunuz?

EOP filtreleme teknolojileri, kullanıcılara ve diğer Microsoft ürünlerine (örneğin Microsoft 365 istenmeyen posta önleme koruması sağlamak Exchange Server. Ayrıca SPF, DKIM ve DMARC kullanıyoruz; e-posta gönderen etki alanının bu yetkiye sahip olduğunu doğruarak kimlik avı ve kimlik avı sorununa çözüm olarak bu sorunu çözmeye yardımcı olan e-posta kimlik doğrulama teknolojileri. EOP filtrelemesi, gönderen IP, etki alanı, kimlik doğrulama, liste doğruluğu, şikayet oranları, içerik ve daha birçok faktör tarafından etkilenir. Bunlar arasında, gönderenin itibarını ve e-posta teslim etme becerisini etkileyen faktörlerden biri de gereksiz e-posta şikayet oranıdır.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Yeni IP adreslerinden e-posta mı gönderiyorsunuz?

Daha önce e-posta göndermek için kullanılmamış IP adresleri normalde sistemlerde yerleşik olarak bir saygınlığı olmaz. Sonuç olarak, yeni IP'lerden gelen e-postalarda teslim sorunları yaşama olasılığı daha yüksek olur. IP, istenmeyen posta göndermemeyle ilgili bir üne sahip olduktan sonra, EOP normalde daha iyi bir e-posta teslim deneyimi sağlar.

Var olan SPF kayıtları altında kimliği doğrulanan etki alanları için eklenen yeni IP'ler normalde etki alanının gönderme itibarının bir avantajdır. Etki alanınız iyi bir gönderme itibarına sahipse yeni IP'ler daha hızlı bir up up süresiyle karşınıza çıkabilecektir. Yeni IP'nin ses düzeyi, liste doğruluğu ve gereksiz e-posta şikayet oranlarına bağlı olarak, birkaç hafta içinde ya da daha kısa sürede tam olarak artışlı olması beklebilir.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>DNS'nizin doğru ayar olduğunu onaylayın

Posta yönlendirme için gereken MX kaydı da dahil olmak üzere DNS kayıtlarını oluşturma ve koruma yönergeleri için, DNS barındırma sağlayıcınıza başvurun.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Kendinizi yönlendirilebilir olmayan bir IP olarak tanıtmama

Ters DNS araması başarısız olan gönderenlerden gelen e-postayı kabul e-postası kabul e-postası kabul e-postası kabul edilemebilir. Bazı durumlarda, EOP bağlantısını açmaya çalışırken, geçerli gönderenler kendilerini yanlış şekilde İnternet'e yönlendirilebilir olmayan bir IP olarak tanıtıyor. Özel (yönlendirilebilir olmayan) ağ için ayrılmış IP adresleri şunlardır:

- 192.168.0.0/16 (veya 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (veya 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (veya 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>NdR' de bir kullanıcıya e-posta gönderirken teslim edile değil raporu (NDR) Office 365

Bazı teslim sorunları, gönderenin IP adresinin Microsoft tarafından engellenmiş olması veya önceki istenmeyen posta etkinliği nedeniyle kullanıcı hesabının yasaklı gönderen olarak tanımlanması nedeniyle ortaya çıkan bir sorundır. NDR'yi hatayla aldıklarını inanıyorsanız, sorunu çözmek için öncelikle NDR iletisinde verilen yönergeleri izleyin.

Hatayı aldığınız hata hakkında daha fazla bilgi için, bu raporlarda yer alan E-posta teslimi olmayan raporlar [konusunda yer alan hata kodlarının Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Örneğin, aşağıdaki NDR'yi alırsanız, gönderen IP adresinin Microsoft tarafından engellenmiş olduğunu gösterir:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Bu listeden kaldırma isteği kullanmak için, liste portalını kullanarak kendinizi [engellenen gönderenler listesinden kaldırabilirsiniz](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>E-postam alıcının Gereksiz E-posta klasörüne geldi

Bir ileti EOP tarafından yanlışlıkla istenmeyen posta olarak tanımlanmışsa, alıcıyla birlikte çalışarak bu hatalı pozitif iletiyi değerlendirip çözümleyecek Microsoft İstenmeyen Posta Çözümleme Ekibi'ne gönderebilirsiniz. Daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>IP adresimin trafiği EOP tarafından kısıtlandı

EOP'den IP adresinizin EOP tarafından kısıt olduğunu belirten bir NDR alırsanız, örneğin:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

IP adresi üzerinden şüpheli etkinlikler algılandığından ve IP adresi değerlendirilirken geçici olarak kısıtlandığından NDR'yi aldınız. Şüphe değerlendirme yoluyla temize kavuşturıldı olursa, bu kısıtlama kısa süre içinde kaldıracağız.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>E-posta adresine gönderenlerden e-posta Microsoft 365

 Kullanıcılarımıza ileti almak için, ağ bağlantılarının EOP'nin veri merkezlerimizde kullandığı IP adreslerinden bağlantılara izin verilerinde izin olduğundan emin olun. Daha fazla bilgi için BKZ[. EXCHANGE ONLINE PROTECTION IP adresleri](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Kullanıcıları toplu e-postayla göndermek için Microsoft 365 yöntemleri

Kullanıcılarınıza sıklıkla toplu e-posta kampanyaları Microsoft 365 ve e-postaların güvenli ve zamanında ulaşını sağlamak istiyorsanız, bu bölümdeki ipuçlarını izleyin.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Gönderen adının iletiyi göndereni yansıtmaya

Konu, iletinin ne hakkında olduğunu kısaca açıklamalı ve ileti gövdesi teklif, hizmet veya ürünün neyle ilgili olduğunu kısa bir şekilde belirtmektedir. Örneğin:

Doğru:

> Buradan: marketing@shoppershandbag.com <br> Konu: Noel mevsimi için katalog güncelleştirildi!

Yanlış:

> Someone@outlook.com <br> Konu: Kataloglar

Kişilerin kim olduğunu ve ne yaptığını daha kolay fark edesiniz, istenmeyen posta filtrelerinin çoğunu kullanarak teslim etmek o kadar zor olur.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Kampanya e-postalarında aboneliği kaldır seçeneğini her zaman dahil edin

Pazarlama e-postaları, özellikle de bültenler, her zaman gelecekteki e-postalardan bir abonelikten çıkma yolu içerir. Örneğin:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Bazı gönderenler, alıcıların konu altında "Aboneliği Kaldır" olan belirli bir diğer adla e-posta göndermelerini gerekli bulundurarak bu seçeneği içerir. Bu, yukarıdaki tek tıklamalı örnekten daha iyi değildir. Alıcıların posta göndermelerini zorunlu seçmeyi tercih ediyorsanız, bağlantıya tıklayana kadar tüm gerekli alanların önceden doldurulmuş olduğundan emin olur.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Pazarlama e-postası veya bülten kaydı için çift kabul seçeneği kullanma

Bu endüstrinin en iyi uygulaması, şirketin ürün veya hizmetlerinize erişmek için kullanıcıların iletişim bilgilerini kaydetmelerini gerekli veya teşvik ediyorsa önerilir. Bazı şirketler kayıt işlemi sırasında kullanıcılarını pazarlama e-postalarına veya e-bültenlere otomatik olarak kaydolmayı bir uygulama olarak kabul eder, ancak bu, e-posta filtreleme dünyasında sorgulanabilir bir pazarlama uygulaması olarak kabul edilir.

Kayıt işlemi sırasında, varsayılan olarak "Evet, lütfen bülteninizi bana gönderin" veya "Evet, lütfen özel teklifler gönderin" onay kutusu seçiliyse, yakından ilgisini ödemeyen kullanıcılar istemeden pazarlama e-postası veya almak istemedileri bültenlere kaydolabilirsiniz.

 Microsoft bunun yerine çift kabul seçeneği önerir; bu da, pazarlama e-postaları veya bültenler için onay kutusunun varsayılan olarak işaretsiz olduğu anlamına gelir. Ayrıca kayıt formu gönderildikten sonra kullanıcıya pazarlama e-postaları alma kararı almalarını sağlayan bir URL ile bir doğrulama e-postası gönderilir.

 Bu, pazarlama e-postalarını yalnızca almak isteyen kullanıcıların e-postalara uygun olarak, gönderen şirketten şüpheli e-posta pazarlama uygulamalarından birini temizlemeye yardımcı olur.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>E-posta iletisi içeriğinin saydam ve izlenebilir olduğundan emin olun

E-postaların gönderilme yolu da içeriği açısından da önemlidir. E-posta içeriği oluştururken, e-posta filtreleme hizmetleriyle e-postalarınızı bayrakla işaretlenmeyecek şekilde en iyi yöntemleri kullanın:

- E-posta iletisi alıcıların göndereni adres defterine eklemesini isteği gönderirken, bu eylemin bir teslim garantisi olmadığını açıkça ifade etmek gerekir.

- İletinin gövdesine dahil edilen yeniden yönlendirmeler benzer ve tutarlı olmalı, birden fazla ve değişken olmalıdır. Bu bağlamda yeniden yönlendirme, bağlantı ve belgeler gibi iletiden uzak olan her şeyi belirtir. Çok fazla reklam varsa veya Aboneliği Kaldır bağlantılarınız varsa ya da Profil bağlantılarını güncelleştirin, hepsi aynı etki alanına işaret olmalıdır. Örneğin:

  Doğru (tüm etki alanları aynıdır):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Yanlış (tüm etki alanları farklıdır):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Büyük resim ve ekleri olan içerik ya da yalnızca resimden oluşan iletilere sahip içerikten kaçının.

- Genel gizliliğiniz veya P3P ayarlarınız, pikselleri izleme (web hataları veya işaretleri) olduğunu açıkça ifademelidir.

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Veritabanlarından yanlış e-posta diğer adlarını kaldırma

Veritabanınıza geri dönen e-posta oluşturan tüm e-posta diğer adları gereksizdir ve e-posta filtreleme hizmetleriyle giden e-postalarınızı daha fazla incelemeniz risk altında olur. E-posta veritabanınızı güncel olduğundan emin olun.