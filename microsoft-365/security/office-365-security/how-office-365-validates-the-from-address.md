---
title: EOP kimlik avının önlenmesi için Kimden adresini nasıl doğrular?
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
description: Yöneticiler, kimlik avının önlenmesine yardımcı olmak için Exchange Online Protection (EOP) ve Outlook.com tarafından kabul edilen veya reddedilen e-posta adresi türleri hakkında bilgi edinebilir.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c8b9fb5c9e2b67a656948684838b61b4a9c33a8d
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319560"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>EOP kimlik avının önlenmesi için Kimden adresini nasıl doğrular?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kimlik avı saldırıları, herhangi bir e-posta kuruluşu için sürekli bir tehdit oluşturur. Sahte [(sahte) gönderen e-posta adreslerini](anti-spoofing-protection.md) kullanmaya ek olarak, saldırganlar genellikle Kimden adresinde İnternet standartlarını ihlal eden değerler kullanır. Bu tür kimlik avının önlenmesine yardımcı olmak için, Exchange Online Protection (EOP) ve Outlook.com artık bu makalede açıklandığı gibi gelen iletilerin RFC uyumlu bir Kimden adresi içermesini gerektirir. Bu zorlama Kasım 2017'de etkinleştirildi.

**Notlar**:

- Bu makalede açıklandığı gibi Adreslerden yanlış biçimlendirilmiş kuruluşlardan düzenli olarak e-posta alıyorsanız, bu kuruluşların e-posta sunucularını modern güvenlik standartlarına uyacak şekilde güncelleştirmelerini teşvik edin.

- İlgili Gönderen alanı (Adına gönder ve posta listeleri tarafından kullanılır) bu gereksinimlerden etkilenmez. Daha fazla bilgi için şu blog gönderisine bakın: [E-postanın "göndereni" ne anlama gelir?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email)

## <a name="an-overview-of-email-message-standards"></a>E-posta iletisi standartlarına genel bakış

Standart smtp e-posta iletisi, *ileti zarfı ve ileti* içeriğinden oluşur. İleti zarfı, iletiyi SMTP sunucuları arasında iletmek ve teslim etmek için gereken bilgileri içerir. İleti içeriği, ileti üst bilgisi alanlarını (topluca *ileti üst bilgisi* olarak adlandırılır) ve ileti gövdesini içerir. İleti zarfı [RFC 5321'de](https://tools.ietf.org/html/rfc5321) ve ileti üst bilgisi [RFC 5322'de](https://tools.ietf.org/html/rfc5322) açıklanmıştır. İleti iletim işlemi tarafından oluşturulduğundan ve iletinin bir parçası olmadığından alıcılar gerçek ileti zarfını asla görmez.

- Adres `5321.MailFrom` ( **POSTA KIMDEN** adresi, P1 gönderen veya zarf gönderen olarak da bilinir), iletinin SMTP iletiminde kullanılan e-posta adresidir. Bu **e-posta** adresi genellikle ileti üst bilgisindeki Dönüş Yolu üst bilgisi alanına kaydedilir (ancak gönderenin farklı bir **Dönüş Yolu e-posta** adresi belirlemesi mümkündür).

- `5322.From` (Kimden adresi veya P2 göndereni olarak da bilinir) **Kimden** üst bilgisi alanındaki e-posta adresidir ve gönderenin e-posta istemcilerinde görüntülenen e-posta adresidir. Kimden adresi, bu makaledeki gereksinimlerin odak noktasıdır.

Kimden adresi çeşitli RFC'ler arasında ayrıntılı olarak tanımlanır (örneğin, RFC 5322 bölümleri 3.2.3, 3.4 ve 3.4.1 ve [RFC 3696](https://tools.ietf.org/html/rfc3696)). Adresleme ve geçerli veya geçersiz olarak kabul edilen birçok çeşitleme vardır. Basit tutmak için aşağıdaki biçim ve tanımları öneririz:

`From: "Display Name" <EmailAddress>`

- **Görünen Ad**: E-posta adresinin sahibini açıklayan isteğe bağlı bir tümcecik.

  - Görünen adı her zaman gösterildiği gibi çift tırnak işareti (") içine almanız önerilir. Görünen ad virgül içeriyorsa, dizeyi RFC 5322 başına çift tırnak içine _almanız gerekir_ .
  - Kimden adresi bir görünen ad içeriyorsa, EmailAddress değeri gösterildiği gibi açılı ayraçlar (< >) içine alınmalıdır.
  - Microsoft, görünen adla e-posta adresi arasına bir boşluk eklemenizi kesinlikle önerir.

- **EmailAddress**: E-posta adresi şu biçimi `local-part@domain`kullanır:

  - **local-part**: Adresle ilişkilendirilmiş posta kutusunu tanımlayan bir dize. Bu değer etki alanı içinde benzersizdir. Genellikle posta kutusu sahibinin kullanıcı adı veya GUID kullanılır.
  - **etki alanı**: E-posta adresinin yerel bölümü tarafından tanımlanan posta kutusunu barındıran e-posta sunucusunun tam etki alanı adı (FQDN).

  EmailAddress değeriyle ilgili dikkat edilmesi gereken bazı ek noktalar şunlardır:

  - Yalnızca bir e-posta adresi.
  - Açılı ayraçları boşluklarla ayırmamanızı öneririz.
  - E-posta adresinden sonra ek metin eklemeyin.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Geçerli ve geçersiz Kimden adresleri örnekleri

Aşağıdaki Kimden e-posta adresleri geçerlidir:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Köşeli ayraçlarla e-posta adresi arasında boşluklar olduğundan önerilmez.)

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Görünen ad çift tırnak içine alınmadığından önerilmez.)

Aşağıdaki Kimden e-posta adresleri geçersiz:

- **Kimden adresi yok**: Bazı otomatik iletiler Kimden adresi içermez. Geçmişte, Microsoft 365 veya Outlook.com Kimden adresi olmayan bir ileti aldığında, hizmet iletiyi teslim edilebilir hale getirmek için şu varsayılan Kimden: adresini eklemiştir:

  `From: <>`

  Artık, kimden adresi boş olan iletiler artık kabul edilir.

- `From: Microsoft 365 sender@contoso.com` (Görünen ad var, ancak e-posta adresi açılı ayraç içine alınmamış.)

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (E-posta adresinden sonraki metin.)

- `From: Sender, Example <sender.example@contoso.com>` (Görünen ad virgül içerir, ancak çift tırnak içine alınmaz.)

- `From: "Microsoft 365 <sender@contoso.com>"` (Tüm değer yanlış şekilde çift tırnak içine alınmış.)

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Görünen ad var, ancak e-posta adresi açılı ayraç içine alınmamış.)

- `From: Microsoft 365<sender@contoso.com>` (Görünen ad ile sol açılı köşeli ayraç arasında boşluk yoktur.)

- `From: "Microsoft 365"<sender@contoso.com>` (Kapanış çift tırnak işareti ile sol açılı köşeli ayraç arasında boşluk yoktur.)

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Özel etki alanınıza otomatik yanıtları gizleme

Otomatik yanıtları engellemek için değerini `From: <>` kullanamazsınız. Bunun yerine, özel etki alanınız için null bir MX kaydı ayarlamanız gerekir. Yanıtlayan sunucunun ileti gönderebileceği yayımlanmış bir adres olmadığından otomatik yanıtlar (ve tüm yanıtlar) doğal olarak gizlenir.

- E-posta almayacak bir e-posta etki alanı seçin. Örneğin, birincil etki alanınız contoso.com ise noreply.contoso.com seçebilirsiniz.

- Bu etki alanı için null MX kaydı tek bir dönemden oluşur.

Örneğin:

```text
noreply.contoso.com IN MX .
```

MX kayıtlarını ayarlama hakkında daha fazla bilgi için bkz. [Microsoft 365 için herhangi bir DNS barındırma sağlayıcısında DNS kayıtları oluşturma](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Null MX yayımlama hakkında daha fazla bilgi için bkz. [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Adres zorlamasından geçersiz kıl

Gelen e-postanın Kimden adresi gereksinimlerini atlamak için, [Microsoft 365'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md) başlığı altında açıklandığı gibi IP İzin Verme Listesi (bağlantı filtreleme) veya posta akışı kurallarını (aktarım kuralları olarak da bilinir) kullanabilirsiniz.

Microsoft 365 gönderdiğiniz giden e-posta için Kimden adresi gereksinimlerini geçersiz kılamazsınız. Ayrıca Outlook.com, destek aracılığıyla bile herhangi bir tür geçersiz kılmaya izin vermez.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Microsoft 365'da siber suçlardan korunmanın ve korunmanın diğer yolları

Kuruluşunuzu kimlik avına, istenmeyen postalara, veri ihlallerine ve diğer tehditlere karşı nasıl güçlendirebileceğiniz hakkında daha fazla bilgi için bkz. [İş planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](../../admin/security-and-compliance/secure-your-business-data.md).
