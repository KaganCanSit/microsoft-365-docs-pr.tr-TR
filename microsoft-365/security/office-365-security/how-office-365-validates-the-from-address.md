---
title: EOP, kimlik avını önlemek için From adresini nasıl doğrular?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Yöneticiler kimlik avını önlemeye yardımcı olmak için Exchange Online Protection (EOP) ve Outlook.com tarafından kabul edilen veya reddedilen e-posta adresleri türleri hakkında bilgi edinebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 412b6eb7045051c21a88c8b4b2ba5e80a06832dd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986515"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>EOP, kimlik avını önlemek için From adresini nasıl doğrular?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kimlik avı saldırıları, tüm e-posta kuruluşları için sürekli bir tehdittir. Sahte adresli [(sahte) gönderen e-posta](anti-spoofing-protection.md) adresleri kullanmanın yanı sıra, saldırganlar çoğunlukla Kaynak adreslerinde İnternet standartlarını ihlal eden değerler kullanır. Bu tür bir kimlik avının önlenmesine yardımcı olmak için, Exchange Online Protection (EOP) ve Outlook.com'a artık bu makalede açıklandığı gibi RFC uyumlu bir Kaynak adresi eklemek için gelen iletilerin dahil olması gerekir. Bu zorlama Kasım 2017'de etkinleştirildi.

**Notlar**:

- Düzenli aralıklarla, bu makalede açıklandığı gibi Kaynak adreslerinde yanlış formlara sahip kuruluşlardan e-posta alırsanız, bu kuruluşların modern güvenlik standartlarına uyması için e-posta sunucularını güncelleştirmelerini teşvik edin.

- İlgili Gönderen alanı (Adına Gönder ve posta listeleri tarafından kullanılır), bu gereksinimlerden etkilenmez. Daha fazla bilgi için aşağıdaki blog gönderisi'ne bakın: [E-postanın 'gönderen'ine başvurarak ne anlama geliyor?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email)

## <a name="an-overview-of-email-message-standards"></a>E-posta iletisi standartlarına genel bakış

Standart SMTP e-posta iletisi, ileti *zarfı ve ileti* içeriğilerinden oluşur. İleti zarfı, iletiyi SMTP sunucuları arasında ileterek teslim etmek için gereken bilgileri içerir. İleti içeriği, ileti üst bilgisi alanlarını (toplu olarak *ileti üst bilgisi* denir) ve ileti gövdeyi içerir. İleti zarfı [RFC 5321'de](https://tools.ietf.org/html/rfc5321) ve ileti üst bilgisi [de RFC 5322'de açıklanmıştır](https://tools.ietf.org/html/rfc5322). alıcılar hiçbir zaman gerçek ileti zarfını görmez, çünkü ileti iletim süreci tarafından oluşturulur ve aslında iletinin bir parçası değildir.

- Adres `5321.MailFrom` (MAIL **FROM** adresi, P1 göndereni veya zarf gönderen olarak da bilinir), iletinin SMTP iletiminde kullanılan e-posta adresidir. Bu **e-posta** adresi normalde ileti üst bilgisinde Dönüş Yolu üst bilgi alanına kaydedilir (ancak gönderen farklı bir **Dönüş Yolu e-posta** adresi ataması mümkündür).

- Gönderen `5322.From` adresi veya P2 göndereni olarak da bilinir), Gönderen üst bilgisi alanında yer alan e-posta adresidir ve e-posta istemcisinde görüntülenen gönderenin e-posta adresidir. Kaynak adresi, bu makaledeki gereksinimlerin odağıdır.

From adresi çeşitli RFC'ler genelinde ayrıntılı olarak tanımlanmıştır (örneğin, RFC 5322 bölüm 3.2.3, 3.4 ve 3.4.1 ve [RFC 3696](https://tools.ietf.org/html/rfc3696)). Adreslemenin birçok çeşitleni vardır ve bunlar geçerli veya geçersiz olarak kabul edilir. Basit tutmak için aşağıdaki biçimi ve tanımları öneririz:

`From: "Display Name" <EmailAddress>`

- **Görünen Ad**: E-posta adresinin sahibini tanımlayan isteğe bağlı bir tümcecik.

  - Görünen adı her zaman, gösterildiği gibi çift tırnak (") içine almanız önerilir. Görünen ad virgül içeriyorsa, RFC 5322 başına dizeyi çift tırnak içine almanız gerekir.
  - From adresi bir görünen ad içerirse, EmailAddress değeri gösterildiği gibi köşeli ayraç (< >) içine alınarak gönder gerekir.
  - Microsoft görünen ad ile e-posta adresi arasına boşluk eklemenizi kesinlikle öneririz.

- **EmailAddress**: Bir e-posta adresi şu biçimini kullanır `local-part@domain`:

  - **yerel bölüm**: Adresle ilişkilendirilmiş posta kutusunu tanımlayan dize. Bu değer etki alanı içinde benzersizdir. Çoğunlukla, posta kutusu sahibinin kullanıcı adı veya GUID'si kullanılır.
  - **etki** alanı: E-posta adresinin yerel bölümü tarafından tanımlanan posta kutusunu barındıran e-posta sunucusunun tam etki alanı adı (FQDN).

  EmailAddress değeriyle ilgili dikkate alınması gereken bazı ek noktalar:

  - Yalnızca bir e-posta adresi.
  - Açılı ayraçları boşlukla ayırmamanizi öneririz.
  - E-posta adresine bundan sonra başka metin eklemeyebilirsiniz.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Geçerli ve geçersiz Adreslerden örnekler

Aşağıdaki E-posta adreslerinden geçerlidir:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Açılı ayraçlar ile e-posta adresi arasında boşluklar olduğundan bu önerilmez.)

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Görünen ad çift tırnak içine alınmamış olduğundan bu önerilmez.)

Aşağıdaki E-posta adreslerinden geçersiz:

- **No From address**: Bazı otomatik iletilerde From adresi yoktur. Geçmişte, Microsoft 365 veya Outlook.com Kaynak adresi olmayan bir ileti geldiğinde, hizmet iletinin teslim edilebilir hale geldiği şu varsayılan Kaynak: adresini ekledi: adresi:

  `From: <>`

  Artık, boş Olan adresi olan iletiler artık kabul edilmeyecektir.

- `From: Microsoft 365 sender@contoso.com` (Görünen ad mevcut, ancak e-posta adresi köşeli ayraç içine alınmış değildir.)

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (E-posta adresinin sonrasındaki metin.)

- `From: Sender, Example <sender.example@contoso.com>` (Görünen ad virgül içerir, ancak çift tırnak içine alınmaz.)

- `From: "Microsoft 365 <sender@contoso.com>"` (Değerin tamamı yanlışlıkla çift tırnak içine alınır.)

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Görünen ad mevcut, ancak e-posta adresi köşeli ayraç içine alınmış değildir.)

- `From: Microsoft 365<sender@contoso.com>` (Görünen ad ile sol açılı ayraç arasında boşluk yoktur.)

- `From: "Microsoft 365"<sender@contoso.com>` (Kapanış çift tırnak işareti ile sol açılı ayraç arasında boşluk yoktur.)

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Özel etki alanınıza otomatik yanıtların gizlenme

Otomatik yanıtların göstermelerini `From: <>` devrederken bu değeri kullanaasiniz. Bunun yerine, özel etki alanınız için boş bir MX kaydı ayarlamanız gerekir. Otomatik yanıtlar (ve tüm yanıtlar) doğal olarak bastırılır çünkü yanıtlayan sunucunun ileti gönderladığı yayımlanmış bir adres yoktur.

- E-posta alın almayan bir e-posta etki alanı seçin. Örneğin, birincil etki alanınız etki contoso.com, etki alanınız birincil noreply.contoso.com.

- Bu etki alanının null MX kaydı tek bir noktadan oluşur.

Örneğin:

```text
noreply.contoso.com IN MX .
```

MX kayıtlarını ayarlama hakkında daha fazla bilgi için bkz. Etki alanı için herhangi bir [DNS barındırma sağlayıcısında DNS Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Null MX yayımlama hakkında daha fazla bilgi için bkz. [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Adres zorlamadan geçersiz kıl

Gelen e-postanın Gönderen adresi gereksinimlerini atlamak için, Microsoft 365'de güvenilir gönderen listeleri oluşturma konusunda açıklandığı gibi IP İzin Listesine (bağlantı filtreleme) veya posta akış kurallarını (aktarım kuralları olarak da bilinir) [kullanabilirsiniz](create-safe-sender-lists-in-office-365.md).

Bir posta Microsoft 365'den göndermek istediğiniz giden e-posta için From adresi gereksinimlerini geçersiz Microsoft 365. Buna ek olarak, Outlook.com destek aracılığıyla bile herhangi bir tür geçersiz kılmaya izin vermez.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>E-Microsoft 365'de siber suçları önlemenin ve bu suçlara karşı korunmanın diğer Microsoft 365

Organizasyonlarınızı kimlik avına, istenmeyen postalara, veri ihlallerine ve diğer tehditlere karşı nasıl güçlendirebilirsiniz hakkında daha fazla bilgi için bkz. İş planları için Microsoft 365 [10 güvenlik yolu](../../admin/security-and-compliance/secure-your-business-data.md).