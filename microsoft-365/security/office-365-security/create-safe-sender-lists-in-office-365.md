---
title: Güvenilir gönderen listeleri oluşturma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) gelen iletilere izin vermek için kullanılabilen ve tercih Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c1aa754790ccf0787a7ee79b0add0d7f5e17ca7
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996463"
---
# <a name="create-safe-sender-lists-in-eop"></a>EOP'de güvenilir gönderen listeleri oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutuları olan bir Microsoft 365 müşterisi veya Exchange Online posta kutuları olmayan tek başına bir Exchange Online Protection (EOP) müşterisiysiniz, EOP kullanıcıların güvenilen gönderenlerden e-posta almalarını sağlamanın çeşitli yollarını sunar. Bu seçenekler posta Exchange kuralları (aktarım kuralları olarak da bilinir), Outlook Kasa Gönderenler, IP İzin Verilenler Listesi (bağlantı filtreleme) ve istenmeyen posta önleme ilkelerinde izin verilen gönderenler listelerini veya izin verilen etki alanı listelerini içerir. Toplu olarak, bu seçenekleri güvenilir gönderenler listeleri _olarak düşünebilirsiniz_.

Kullanılabilir güvenilir gönderen listeleri, en çok önerilenden en az önerilene doğru aşağıdaki listede açıklanmıştır:

1. Posta akış kuralları
2. Outlook Kasa Gönderenler
3. IP İzin Ver Listesi (bağlantı filtreleme)
4. İzin verilen gönderenler listeleri veya izin verilen etki alanı listeleri (istenmeyen posta önleme ilkeleri)

Posta akış kuralları, yalnızca doğru iletilere izin verilirken en fazla esnekliği sağlar. İstenmeyen posta önleme ilkelerinde izin verilen gönderenler ve izin verilen etki alanı listeleri IP İzin Verilenler Listesi kadar güvenli değildir, çünkü gönderenin e-posta etki alanı kolayca kimliklerini kullanır. Ancak IP İzin Listesi de risk sunar, çünkü bu IP adresinden gönderilen  herhangi bir etki alanındaki e-postalar istenmeyen posta filtrelemeyi atlar.

> [!IMPORTANT]
>
> - Kötü amaçlı yazılım veya yüksek güvenli kimlik avı olarak tanımlanan iletiler, güvenli gönderen listesi seçeneği ne olursa olsun her zaman karantinaya alınır.
>
> - Güvenilir gönderen listelerini kullanarak *istenmeyen posta* filtrelemeyle ilgili özel durumları yakından takip etmek için dikkatli olun.
>
> - Hatalı pozitif sonuçlarla (iyi e-posta kötü işaretlenmiştir) yardımcı olması için güvenilir gönderen listelerini kullanabilirsiniz, ancak mümkünse kaçınılması gereken geçici bir çözüm olarak güvenilir gönderen listelerini kullanmayı göz önünde bulundurabilirsiniz. Güvenilir gönderen listelerini kullanarak hatalı pozitif sonuçlar yönetimi önerilmez, çünkü istenmeyen posta filtreleme özel durumları nedeniyle kuruluş kimlik sahtesi ve diğer saldırılara açık olabilir. Hatalı pozitif sonuçlar yönetmek için güvenilir gönderen listelerini kullanmayı merak ediyorsanız, bu konuda bilgili olmalı ve İletileri ve dosyaları [Microsoft'a](report-junk-email-messages-to-microsoft.md) bildirme konusunu hazır tutmanız gerekir.
>
> - Etki alanının kimliği doğrulanmamış e-posta göndermesine izin vermek (kimlik kimlik doğrulaması korumasını atlama) ancak istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma denetimlerini atlamama [](learn-about-spoof-intelligence.md) izin vermek için kimliksiz kimlik doğrulaması içgörüsini ve Kiracı İzin Ver/Engelleme Listesi'ne göz [atabilirsiniz](tenant-allow-block-list.md).
>
> - EOP ve Outlook, iletinin göndereni belirlemek için farklı ileti özelliklerini inceler. Daha fazla bilgi için, bu [makalenin devam bölümündeki Toplu e-posta için](#considerations-for-bulk-email) dikkate alınacak noktalar bölümüne bakın.
>

Buna karşılık, engellenen gönderen listelerini kullanarak belirli kaynaklardan gelen e-postaları engellemek için _çeşitli seçenekleriniz de vardır_. Daha fazla bilgi için bkz [. EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>(Önerilen) Posta akış kurallarını kullanma

> [!NOTE]
> İç göndereni güvenilir gönderen olarak tasarlamak için ileti üst bilgilerini ve posta akış kurallarını kullanasınız. Bu bölümdeki yordamlar yalnızca dış gönderenler için çalışır.

Exchange Online tek başına EOP'daki posta akışı kuralları, iletileri tanımlamak için koşulları ve özel durumları ve bu iletilere ne yapılması gerektiğini belirten eylemleri kullanır. Daha fazla bilgi için, [aşağıdaki adreste posta akışı kuralları (aktarım kuralları) Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

Aşağıdaki örnekte, istenmeyen posta filtrelemeyi atlamak için e-contoso.com e-postaya ihtiyacınız olduğu varsay gelir. Bunu yapmak için aşağıdaki ayarları yapılandırabilirsiniz:

1. **Koşul**: **Gönderenin etki** \> **alanı contoso.com**\>.

2. Aşağıdaki ayarlardan birini yapılandırma:

   - **Posta akışı kuralı koşulu**: **İleti üst bilgisi şu** \> **sözcüklerden herhangi birini içerir**\>: **Üst bilgi** adı: `Authentication-Results` \> **Üst bilgi** değeri: `dmarc=pass` veya `dmarc=bestguesspass`.

     Bu koşul, gönderen etki alanının kimlik doğrulamasının doğrulanmaz olması için, gönderen e-posta etki alanının e-posta kimlik doğrulama durumunu denetler. E-posta kimlik doğrulaması hakkında daha fazla bilgi için [bkz. SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) [ve DMARC](use-dmarc-to-validate-email.md).

   - **IP İzin Listesi**: Bağlantı filtresi ilkesinde kaynak IP adresini veya adres aralığını belirtin.

     Gönderen etki alanı e-posta kimlik doğrulamasını kullanmazsanız bu ayarı kullanın. IP İzin Listesi'nin kaynak IP adresleri söz konusu olduğunda mümkün olduğunca kısıtlayıcı olun. /24 veya daha küçük bir IP adresi aralığı öneririz (daha az daha iyi). Tüketici hizmetleri (örneğin, genel ağ) veya paylaşılan altyapılara ait IP outlook.com aralıklarını kullanmayın.

   > [!IMPORTANT]
   >
   > - Hiçbir zaman posta akışı kurallarını, istenmeyen *posta* filtrelemeyi atlama koşulu olarak yalnızca gönderen etki alanıyla yapılandırma. Bunu yapmak *,* saldırganların gönderen etki alanını kimlik doğrulaması yapma (veya tam e-posta adresinin kimliğine bürünme), tüm istenmeyen posta filtrelemelerini atlama ve iletinin alıcının Gelen Kutusu'na ulaşabilmesi için gönderen kimlik doğrulamasını atlama olasılığını önemli ölçüde artırır.
   >
   > - Sahip olduğunuz etki alanlarını (kabul edilen etki alanları olarak da bilinir) veya popüler etki alanlarını (örneğin, microsoft.com) posta akış kurallarında koşullar olarak kullanmayın. Bunu yapmak yüksek risk kabul edilir çünkü saldırganların e-posta gönderme fırsatları oluşturur ve aksi halde filtrelenmiş olur.
   >
   > - Ağ adresi çevirisinin (NAT) ağ geçidinin arkasında yer alan bir IP adresine izin verirsiniz, IP İzin Listeniz'in kapsamını bilmek için NAT havuzuna katılan sunucuları bilebilirsiniz. IP adresleri ve NAT katılımcıları değişebilir. Standart bakım yordamlarının bir parçası olarak IP İzin Listesi girdilerinizi düzenli aralıklarla denetlemeniz gerekir.

3. **İsteğe bağlı koşullar**:
   -  \> Gönderen **iç/dış** \> **Kuruluş dışında**: Bu koşul örtülü bir koşuldur, ancak doğru yapılandırılmamış şirket içi e-posta sunucularını hesap etmek için bu koşulu kullanabilirsiniz.
   - **Konu veya gövde** \> **Konu veya gövde şu sözcüklerden herhangi birini içerir** \> \<keywords\>: İletileri konu satırı veya ileti gövdesine anahtar sözcükler veya tümceciklerle daha fazla sınırlandırabilirsiniz, bu sözcükleri bir koşul olarak kullanabilirsiniz.

4. **Eylem**: Kuralda bu eylemlerin ikisini de yapılandırabilirsiniz:
   1. **İleti özelliklerini değiştirme** \> **istenmeyen posta güven düzeyini (SCL) ayarlama** \> **İstenmeyen posta filtrelemeyi atlar**.
   2. **İleti özelliklerini değiştirme** \> **ileti üst bilgisi ayarlama**: **İleti üst bilgilerini değere** \<CustomHeaderName\> **ayarlayın**\<CustomHeaderValue\>.

      Örneğin, `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Kuralda birden çok etki alanınız varsa, üst bilgi metnini uygun şekilde özelleştirebilirsiniz.

      İleti bir posta akış kuralı nedeniyle istenmeyen posta filtrelemeyi atlasa, `SFV:SKN` **değer değeri X-Forefront-Antispam-Report üst bilgisinde damgalanır** . İleti IP İzin Listesi'nin içinde yer alan bir kaynaktansa, değer `IPV:CAL` de eklenir. Bu değerler sorun gidermede size yardımcı olabilir.

![EAC'de istenmeyen posta filtrelemeyi atlamak için posta akışı kuralı ayarları.](../../media/1-AllowList-SkipFilteringFromContoso.png)

## <a name="use-outlook-safe-senders"></a>Gönderenleri Outlook Kasa kullanma

> [!CAUTION]
> Bu yöntem, aksi halde filtrelenmiş olan e-postaları Gelen Kutusu'na başarıyla teslim etmekle karşı yüksek riskli bir yöntem oluşturur; öte yandan, kullanıcının kimlik Kasa gönderenler veya Kasa Etki Alanları listeleri kötü amaçlı yazılım veya yüksek güveni olan kimlik avı iletilerinin filtresini engellemez.

Kuruluş ayarı yerine, kullanıcılar veya yöneticiler gönderen e-posta adreslerini posta Kasa Gönderenler listesine ekleyebilir. Yönergeler için bkz. [Posta kutularında veya posta Exchange Online gereksiz e-posta Office 365](configure-junk-email-settings-on-exo-mailboxes.md). Gönderenler filtre yığınının parçalarını atlamayacaklarından çoğu durumda bu tercih edilmez. Gönderene güvenin, ancak gönderenin güvenliği ihlal edilmiş olabilir ve kötü amaçlı içerik gönderebilirsiniz. En iyisi filtrelerimizin tüm iletiyi kontrol etmek için gerekenleri yapmalarını ve ardından filtrelerimiz yanlış tarafından yanlış olması durumuna karşı [microsoft'a pozitif/](report-junk-email-messages-to-microsoft.md) negatif rapor vermenizi sağlar. Filtreleme yığınını atlamak [ZAP'la da karışıyor](zero-hour-auto-purge.md).

İletiler, kullanıcının Kasa Gönderenler listesi nedeniyle istenmeyen posta filtrelemesini atlasa, **X-Forefront-Antispam-Report** `SFV:SFE`üst bilgi alanı istenmeyen posta, kimlik sahtesi ve kimlik avına yönelik filtrelemenin atlan olduğunu belirten değeri içerir.

## <a name="use-the-ip-allow-list"></a>IP İzin Ver Listesini kullanma

Daha önce açıklandığı gibi posta akışı kurallarını kullanasanız, bir sonraki en iyi seçenek bağlantı filtresi ilkesinde kaynak e-posta sunucusunu veya sunucularını IP İzin Listesi'ne eklemektir. Ayrıntılar için bkz. [EOP'de bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).

**Notlar**:

- İzin verilen IP adresleri sayısını en az düzeyde tutmanız önemlidir, bu nedenle mümkün olduğunda IP adresi aralıklarının tamamını kullanmaktan kaçının.
- Tüketici hizmetleri (örneğin, genel ağ) veya paylaşılan altyapılara ait IP outlook.com aralıklarını kullanmayın.
- IP İzin Ver Listesi'ne düzenli olarak girdileri gözden geçirin ve artık ihtiyacınız yok girdileri kaldırın.

> [!CAUTION]
> Posta akış kuralları gibi ek doğrulama olmadan, IP İzin Listesi'nin kaynaklarından gelen e-postalar istenmeyen posta filtrelemeyi ve gönderen kimlik doğrulamasını (SPF, DKIM, DMARC) denetler. Bu, aksi halde filtrelenmiş olan e-postaları Gelen Kutusu'na başarıyla teslim etmekle karşı büyük risk oluşturur; ancak IP İzin Listesi kötü amaçlı yazılım veya yüksek güveni olan kimlik avı iletilerinin filtresini engellemez.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>İzin verilen gönderenler listelerini veya izin verilen etki alanı listelerini kullanma

İstenmeyen posta önleme ilkesinde izin verilen gönderenler listesini veya izin verilen etki alanı listesini kullanmak en az tercih edilen seçenektir. Gönderenler tüm *istenmeyen postayı* , kimlik sahtesini ve kimlik avı korumasını ve gönderen kimlik doğrulamasını (SPF, DKIM, DMARC) atlayarak mümkünse bu seçeneği engellemeniz gerekir. Bu yöntem, yalnızca geçici test için en iyi yöntemdir. Ayrıntılı adımlar, [EOP'de istenmeyen posta ilkelerini yapılandırma başlığında](configure-your-spam-filter-policies.md) bulunabilir.

Bu listeler için en yüksek sınır yaklaşık 1000 girdidir; Ancak portala yalnızca 30 giriş girebilirsiniz. PowerShell kullanarak 30'dan fazla giriş eklemeniz gerekir.

> [!CAUTION]
>
> - Bu yöntem, aksi halde filtrelenmiş olan e-postaları Gelen Kutusu'na başarıyla teslim etmekle karşı yüksek riskli bir yöntem oluşturur; öte yandan, izin verilen gönderenler veya izin verilen etki alanları listeleri kötü amaçlı yazılım veya yüksek güveni olan kimlik avı iletilerinin filtresini engellemez.
>
> - Sahip olduğunuz (kabul edilen etki alanları olarak da bilinir) veya izin verilen etki alanı listelerinde popüler etki alanlarını (örneğin, microsoft.com) kullanmayın.

## <a name="considerations-for-bulk-email"></a>Toplu e-posta için dikkate alınacak noktalar

Standart SMTP e-posta iletisi, ileti *zarfı ve ileti* içeriğilerinden oluşur. İleti zarfı, iletiyi SMTP sunucuları arasında ileterek teslim etmek için gereken bilgileri içerir. İleti içeriği, ileti üst bilgisi alanlarını (toplu olarak *ileti üst bilgisi* denir) ve ileti gövdeyi içerir. İleti zarfı RFC 5321'de ve ileti üst bilgisi de RFC 5322'de açıklanmıştır. alıcılar hiçbir zaman gerçek ileti zarfını görmez, çünkü ileti iletim süreci tarafından oluşturulur ve aslında iletinin bir parçası değildir.

- Adres `5321.MailFrom` (MAIL **FROM** adresi, P1 göndereni veya zarf gönderen olarak da bilinir), iletinin SMTP iletiminde kullanılan e-posta adresidir. Bu **e-posta** adresi normalde ileti üst bilgisinde Dönüş Yolu üst bilgi alanına kaydedilir (ancak gönderen farklı bir **Dönüş Yolu e-posta** adresi ataması mümkündür). İleti teslim edilene kadar teslim edileme raporunun (NDR veya geri dönen ileti olarak da bilinir) alıcısı olur.
- Gönderen `5322.From` adresi veya P2 göndereni olarak da bilinir), Gönderen üst bilgisi alanında yer alan e-posta adresidir ve e-posta istemcisinde görüntülenen gönderenin e-posta adresidir. 

Genellikle, adresler `5321.MailFrom` `5322.From` ve adresler aynıdır (kişiler arasında iletişim). Bununla birlikte, başka biri adına e-posta gönderi olduğunda, adresler farklı olabilir. Bu genellikle toplu e-posta iletilerde olur.

Örneğin, Blue Yonder Airlines'ın e-posta reklamını göndermek için Megie'nin Seyahatini işe tuttuğunu varsayalım. Gelen Kutunuzda size gelen iletide aşağıdaki özellikler vardır:

- Adres `5321.MailFrom` önemli blueyonder.airlines@margiestravel.com.
- Adres `5322.From` blueyonder@news.blueyonderairlines.com, bu adreste göreceğiz Outlook.

Kasa EOP'de `5322.From` istenmeyen posta önleme ilkelerinde yer alan gönderen listelerini ve güvenilir etki alanı listelerini incelerken, bu durum adresi kullanan gönderenlerin `5322.From` Outlook Kasa benzer.

Bu iletinin filtresini önlemek için aşağıdaki adımları gerçekleştirebilirsiniz:

- Gönderen blueyonder@news.blueyonderairlines.com olarak e-posta `5322.From` (adres) Outlook Kasa ekleyin.
- [Posta akış kuralı, bir](#recommended-use-mail-flow-rules) e-posta iletisinden ( `5322.From` adres, blueyonder@news.blueyonderairlines.com ) veya her blueyonder.airlines@margiestravel.com iletilerin için `5321.MailFrom`bir koşul kullanın.
