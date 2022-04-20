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
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection (EOP) içinde gelen iletilere izin vermek için kullanılabilir ve tercih edilen seçenekler hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 898f04826f89e3a33c0cfcca01b717523e7c6122
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974223"
---
# <a name="create-safe-sender-lists-in-eop"></a>EOP'de güvenilir gönderen listeleri oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

posta kutuları Exchange Online veya Exchange Online posta kutuları olmayan tek başına Exchange Online Protection (EOP) müşterisi olan bir Microsoft 365 müşterisiyseniz, EOP kullanıcıların güvenilir gönderenlerden e-posta almasını sağlamanın birden çok yolunu sunar. Bu seçenekler arasında Exchange posta akışı kuralları (aktarım kuralları olarak da bilinir), gönderenler Outlook Kasa, IP İzin Verilenler Listesi (bağlantı filtreleme) ve istenmeyen posta önleme ilkelerinde izin verilen gönderen listeleri veya izin verilen etki alanı listeleri bulunur. Toplu olarak, bu seçenekleri _güvenilir gönderen listeleri_ olarak düşünebilirsiniz.

Kullanılabilir güvenilir gönderen listeleri, en çok önerilenden en az önerilene kadar aşağıdaki listede açıklanmıştır:

1. Posta akışı kuralları
2. Outlook Kasa Gönderenler
3. IP İzin Ver Listesi (bağlantı filtreleme)
4. İzin verilen gönderen listeleri veya izin verilen etki alanı listeleri (istenmeyen posta önleme ilkeleri)

Posta akışı kuralları, yalnızca doğru iletilere izin verildiğinden emin olmak için en fazla esnekliği sağlar. İstenmeyen postadan koruma ilkelerindeki izin verilen gönderen ve izin verilen etki alanı listeleri IP İzin Verilenler Listesi kadar güvenli değildir çünkü gönderenin e-posta etki alanı kolayca sahtedir. Ancak IP adresinden gönderilen _herhangi_ bir etki alanından gelen e-postalar istenmeyen posta filtrelemesini atladığı için IP İzin Verme Listesi de bir risk oluşturur.

> [!IMPORTANT]
>
> - Kötü amaçlı yazılım veya yüksek güvenilirlikli kimlik avı olarak tanımlanan iletiler, kullandığınız güvenilir gönderen listesi seçeneğine bakılmaksızın her zaman karantinaya alınır. Daha fazla bilgi için bkz[. Office 365'de varsayılan olarak güvenlidir](secure-by-default.md).
>
> - Güvenilir gönderen listelerini kullanarak istenmeyen posta filtrelemesinde _yaptığınız özel durumları_ yakından izlemeye dikkat edin.
>
> - Hatalı pozitif (iyi e-posta kötü olarak işaretlenmiş) konusunda yardımcı olmak için güvenilir gönderen listelerini kullanabilirsiniz ancak mümkünse kaçınılması gereken geçici bir çözüm olarak güvenilir gönderen listelerinin kullanımını göz önünde bulundurmalısınız. İstenmeyen posta filtreleme özel durumları kuruluşunuzu kimlik sahtekarlığına ve diğer saldırılara açabileceğinden, güvenilir gönderen listelerini kullanarak hatalı pozitif sonuçları yönetmenizi önermeyiz. Hatalı pozitif sonuçları yönetmek için güvenilir gönderen listelerini kullanmakta ısrar ediyorsanız dikkatli olmanız ve [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md) konusunu hazır tutmanız gerekir.
>
> - Etki alanının kimliği doğrulanmamış e-posta göndermesine (kimlik sahtekarlığına karşı korumayı atlama) ancak istenmeyen posta önleme ve diğer korumaları atlamamasına izin vermek için kimlik [sahtekarlığı zekası içgörülerini](learn-about-spoof-intelligence.md) ve [Kiracı İzin Ver/Engelle Listesi'ni](tenant-allow-block-list.md) kullanabilirsiniz.
>
> - EOP ve Outlook, iletinin gönderenini belirlemek için farklı ileti özelliklerini inceleyin. Daha fazla bilgi için bu makalenin devamında yer [alan Toplu e-posta ile ilgili dikkat edilmesi gerekenler](#considerations-for-bulk-email) bölümüne bakın.
>

Buna karşılık, _engellenen gönderen listelerini_ kullanarak belirli kaynaklardan gelen e-postaları engellemek için çeşitli seçenekleriniz de vardır. Daha fazla bilgi için bkz. [EOP'de engelleyici gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>(Önerilen) Posta akışı kurallarını kullanma

> [!NOTE]
> bir iç göndereni güvenilir gönderen olarak belirtmek için ileti üst bilgilerini ve posta akışı kurallarını kullanamazsınız. Bu bölümdeki yordamlar yalnızca dış gönderenler için geçerlidir.

Exchange Online ve tek başına EOP'deki posta akışı kuralları, iletileri tanımlamak için koşulları ve özel durumları ve bu iletilere ne yapılması gerektiğini belirten eylemleri kullanır. Daha fazla bilgi için bkz. [Exchange Online'de Posta akışı kuralları (aktarım kuralları).](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

Aşağıdaki örnekte, istenmeyen posta filtrelemeyi atlamak için contoso.com e-postasına ihtiyacınız olduğu varsayılır. Bunu yapmak için aşağıdaki ayarları yapılandırın:

1. **Koşul**: **Gönderen** \> **etki alanı** \> contoso.com.

2. Aşağıdaki ayarlardan birini yapılandırın:

   - **Posta akışı kuralı koşulu**: **İleti üst bilgisi** \> **şu sözcüklerden** \> herhangi birini içerir **Üst bilgi adı**: `Authentication-Results` \> **Üst bilgi değeri**: `dmarc=pass` veya `dmarc=bestguesspass`.

     Bu koşul, gönderen etki alanının sahte olmadığından emin olmak için gönderen e-posta etki alanının e-posta kimlik doğrulama durumunu denetler. E-posta kimlik doğrulaması hakkında daha fazla bilgi için bkz. [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC](use-dmarc-to-validate-email.md).

   - **IP İzin Verme Listesi**: Bağlantı filtresi ilkesinde kaynak IP adresini veya adres aralığını belirtin.

     Gönderen etki alanı e-posta kimlik doğrulaması kullanmıyorsa bu ayarı kullanın. IP İzin Ver Listesindeki kaynak IP adresleri söz konusu olduğunda mümkün olduğunca kısıtlayıcı olun. /24 veya daha az BIR IP adresi aralığı öneririz (daha azı daha iyidir). Tüketici hizmetlerine (örneğin, outlook.com) veya paylaşılan altyapılara ait IP adresi aralıklarını kullanmayın.

   > [!IMPORTANT]
   >
   > - İstenmeyen posta filtrelemeyi atlamak için koşul olarak posta akışı kurallarını _hiçbir zaman yalnızca_ gönderen etki alanıyla yapılandırmayın. Bunun yapılması, saldırganların gönderen etki alanını taklit etme (veya tam e-posta adresinin kimliğine bürünme), tüm istenmeyen posta filtrelemesini atlama ve iletinin alıcının Gelen Kutusu'na ulaşması için gönderen kimlik doğrulama denetimlerini atlama olasılığını _önemli ölçüde_ artırır.
   >
   > - Sahip olduğunuz etki alanlarını (kabul edilen etki alanları olarak da bilinir) veya popüler etki alanlarını (örneğin, microsoft.com) posta akışı kurallarında koşul olarak kullanmayın. Bunu yapmak, saldırganların başka türlü filtrelenecek e-posta gönderme fırsatları oluşturması nedeniyle yüksek risk olarak kabul edilir.
   >
   > - Ağ adresi çevirisi (NAT) ağ geçidinin arkasındaki bir IP adresine izin verirseniz, IP İzin Verme Listenizin kapsamını bilmek için NAT havuzuna dahil olan sunucuları bilmeniz gerekir. IP adresleri ve NAT katılımcıları değişebilir. Standart bakım yordamlarınızın bir parçası olarak IP İzin Ver Listesi girdilerinizi düzenli aralıklarla denetlemeniz gerekir.

3. **İsteğe bağlı koşullar**:
   - **Gönderen** \> **iç/dış** \> **Kuruluş dışında**: Bu koşul örtülüdür, ancak doğru yapılandırılmamış olabilecek şirket içi e-posta sunucularını hesaba eklemek için bu koşulu kullanabilirsiniz.
   - **Konu veya gövde** \> **konu veya gövde bu sözcüklerden** \> herhangi birini içerir \<keywords\>: İletileri konu satırında veya ileti gövdesinde anahtar sözcüklere veya tümceciklere göre daha fazla kısıtlayabilirseniz, bu sözcükleri bir koşul olarak kullanabilirsiniz.

4. **Eylem**: Kuralda bu eylemlerin ikisini de yapılandırın:
   1. **İleti özelliklerini** \> değiştirme **istenmeyen posta güvenilirlik düzeyini (SCL)** \> ayarlama **İstenmeyen posta filtrelemeyi atla**.
   2. **İleti özelliklerini** \> değiştirme **ileti üst bilgisi ayarlama**: **İleti üst bilgisini** \<CustomHeaderName\> **değerine** \<CustomHeaderValue\>ayarlayın.

      Örneğin, `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Kuralda birden fazla etki alanınız varsa, üst bilgi metnini uygun şekilde özelleştirebilirsiniz.

      Bir ileti posta akışı kuralı nedeniyle istenmeyen posta filtrelemeyi atladığında, değer `SFV:SKN` değeri **X-Forefront-Antispam-Report** üst bilgisinde damgalanır. İleti IP İzin Verme Listesi'nde bulunan bir kaynaktan geliyorsa, değer `IPV:CAL` de eklenir. Bu değerler sorun giderme konusunda size yardımcı olabilir.

      :::image type="content" source="../../media/1-AllowList-SkipFilteringFromContoso.png" alt-text="İstenmeyen posta filtrelemesini atlamak için EAC'deki Posta akışı kuralı ayarları" lightbox="../../media/1-AllowList-SkipFilteringFromContoso.png":::

## <a name="use-outlook-safe-senders"></a>Outlook Kasa Gönderenleri kullanma

> [!CAUTION]
> Bu yöntem, saldırganların Gelen Kutusu'na e-postayı başarıyla teslim etme riski oluşturur ve aksi takdirde filtrelenebilir; ancak kullanıcının Kasa Gönderenler veya Kasa Etki Alanları listeleri kötü amaçlı yazılımların veya yüksek güvenilirlikli kimlik avı iletilerinin filtrelenmesini engellemez.

Kuruluş ayarı yerine, kullanıcılar veya yöneticiler gönderen e-posta adreslerini posta kutusunun Kasa Gönderenler listesine ekleyebilir. Yönergeler için bkz[. Office 365 Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md). Çoğu durumda, gönderenler filtreleme yığınının bölümlerini atlayacağı için bu tercih edilmez. Gönderene güvenseniz de, gönderenin güvenliği tehlikeye girebilir ve kötü amaçlı içerik gönderebilir. Filtrelerimizin her iletiyi denetlemek için gerekenleri yapmasına izin vermeniz ve filtrelerimizin yanlış olması durumunda [hatalı pozitif/negatif değerini Microsoft'a bildirmeniz](report-junk-email-messages-to-microsoft.md) en iyisidir. Filtreleme yığınının atlanması DA [ZAP'a](zero-hour-auto-purge.md) müdahale eder.

bir kullanıcının Kasa Gönderenler listesi nedeniyle iletiler istenmeyen posta filtrelemeyi atladığında, **X-Forefront-Antispam-Report** üst bilgi alanı, istenmeyen posta, kimlik sahtekarlığı ve kimlik avı filtrelemesinin atlandığını gösteren değerini `SFV:SFE`içerir.

## <a name="use-the-ip-allow-list"></a>IP İzin Ver Listesini Kullanma

Daha önce açıklandığı gibi posta akışı kurallarını kullanamıyorsanız, bir sonraki en iyi seçenek kaynak e-posta sunucusunu veya sunucuları bağlantı filtresi ilkesindeki IP İzin Verme Listesi'ne eklemektir. Ayrıntılar için bkz [. EOP'de bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).

**Notlar**:

- İzin verilen IP adreslerinin sayısını en az düzeyde tutmanız önemlidir, bu nedenle mümkün olduğunda tüm IP adresi aralıklarını kullanmaktan kaçının.
- Tüketici hizmetlerine (örneğin, outlook.com) veya paylaşılan altyapılara ait IP adresi aralıklarını kullanmayın.
- IP İzin Ver Listesindeki girdileri düzenli olarak gözden geçirin ve artık ihtiyacınız olmayan girdileri kaldırın.

> [!CAUTION]
> Posta akışı kuralları gibi ek doğrulama olmadan, IP İzin Ver Listesindeki kaynaklardan gelen e-postalar istenmeyen posta filtreleme ve gönderen kimlik doğrulaması (SPF, DKIM, DMARC) denetimlerini atlar. Bu, saldırganların Gelen Kutusu'na e-postayı başarıyla teslim etme riski oluşturur ve aksi takdirde filtrelenebilir; ancak IP İzin Ver Listesi kötü amaçlı yazılım veya yüksek güvenilirlikli kimlik avı iletilerinin filtrelenmesini engellemez.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>İzin verilen gönderen listelerini veya izin verilen etki alanı listelerini kullanma

İstenmeyen en az seçenek, istenmeyen posta önleme ilkelerinde izin verilen gönderen listesini veya izin verilen etki alanı listesini kullanmaktır. Gönderenler tüm istenmeyen posta, kimlik sahtekarlığı ve kimlik avı korumasını ve gönderen kimlik doğrulamasını (SPF, DKIM, DMARC) atladığından _mümkünse_ bu seçenekten kaçınmalısınız. Bu yöntem yalnızca geçici test için en iyi şekilde kullanılır. Ayrıntılı adımlar [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md) konusunda bulunabilir.

Bu listeler için en yüksek sınır yaklaşık 1000 giriştir; ancak portala yalnızca 30 giriş girebilirsiniz. 30'dan fazla girdi eklemek için PowerShell'i kullanmanız gerekir.

> [!CAUTION]
>
> - Bu yöntem, saldırganların Gelen Kutusu'na e-postayı başarıyla teslim etme riski oluşturur ve aksi takdirde filtrelenebilir; ancak, izin verilen gönderenler veya izin verilen etki alanları listeleri kötü amaçlı yazılımların veya yüksek güvenilirlikli kimlik avı iletilerinin filtrelenmesini engellemez.
>
> - İzin verilen etki alanı listelerinde sahip olduğunuz etki alanlarını (kabul edilen etki alanları olarak da bilinir) veya popüler etki alanlarını (örneğin, microsoft.com) kullanmayın.

## <a name="considerations-for-bulk-email"></a>Toplu e-posta ile ilgili dikkat edilmesi gerekenler

Standart smtp e-posta iletisi, _ileti zarfı ve ileti_ içeriğinden oluşur. İleti zarfı, iletiyi SMTP sunucuları arasında iletmek ve teslim etmek için gereken bilgileri içerir. İleti içeriği, ileti üst bilgisi alanlarını (topluca _ileti üst bilgisi_ olarak adlandırılır) ve ileti gövdesini içerir. İleti zarfı RFC 5321'de ve ileti üst bilgisi RFC 5322'de açıklanmıştır. İleti iletim işlemi tarafından oluşturulduğundan ve iletinin bir parçası olmadığından alıcılar gerçek ileti zarfını asla görmez.

- Adres `5321.MailFrom` ( **POSTA KIMDEN** adresi, P1 gönderen veya zarf gönderen olarak da bilinir), iletinin SMTP iletiminde kullanılan e-posta adresidir. Bu **e-posta** adresi genellikle ileti üst bilgisindeki Dönüş Yolu üst bilgisi alanına kaydedilir (ancak gönderenin farklı bir **Dönüş Yolu e-posta** adresi belirlemesi mümkündür). İleti teslim edilemiyorsa, teslim edilemedi raporunun alıcısıdır (NDR veya geri dönen ileti olarak da bilinir).
- `5322.From` (**Kimden** adresi veya P2 göndereni olarak da bilinir) **Kimden** üst bilgisi alanındaki e-posta adresidir ve gönderenin e-posta istemcilerinde görüntülenen e-posta adresidir.

Ve adresleri sıklıkla `5321.MailFrom` `5322.From` aynıdır (kişiden kişiye iletişim). Ancak, başka biri adına e-posta gönderildiğinde, adresler farklı olabilir. Bu durum en sık toplu e-posta iletileri için gerçekleşir.

Örneğin, Blue Yonder Airlines'ın e-posta reklamlarını göndermek için Margie'nin Seyahatini kiraladığını varsayalım. Gelen Kutunuzda aldığınız ileti aşağıdaki özelliklere sahiptir:

- Adres `5321.MailFrom` blueyonder.airlines@margiestravel.com.
- Adres `5322.From` blueyonder@news.blueyonderairlines.com, Outlook'da göreceğiniz adrestir.

EOP'deki istenmeyen posta önleme ilkelerinde gönderen listelerini ve güvenli etki alanı listelerini Kasa `5322.From` yalnızca adresleri inceler; bu, adresi kullanan `5322.From` Outlook Kasa Gönderenlere benzer.

Bu iletinin filtrelenmesini önlemek için aşağıdaki adımları uygulayabilirsiniz:

- blueyonder@news.blueyonderairlines.com (`5322.From`adres) Outlook Kasa Gönderen olarak ekleyin.
- blueyonder@news.blueyonderairlines.com (adres, blueyonder.airlines@margiestravel.com `5322.From` (), `5321.MailFrom`veya her ikisinden gelen iletilerin aranması koşuluyla bir [posta akışı kuralı kullanın](#recommended-use-mail-flow-rules).
