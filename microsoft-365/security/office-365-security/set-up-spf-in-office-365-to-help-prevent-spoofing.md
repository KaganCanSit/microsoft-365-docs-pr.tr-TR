---
title: Kimlik sahtekarlığını önlemeye yardımcı olmak için SPF'yi ayarlama
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Bir Etki Alanı Adı Hizmeti (DNS) kaydını, Office 365'daki özel etki alanınızla Sender Policy Framework (SPF) kullanacak şekilde nasıl güncelleştireceğinizi öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d29175c471e076b1f69e1edb6da3c005d3857f8f
ms.sourcegitcommit: c4924bcad6648fae279076cafa505fae1194924a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2022
ms.locfileid: "65626051"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Kimlik sahtekarlığını önlemeye yardımcı olmak için SPF'yi ayarlama

- [Önkoşullar](#prerequisites)
- [SPF TXT kaydınızı oluşturma veya güncelleştirme](#create-or-update-your-spf-txt-record)
- [Alt etki alanları nasıl işlenir?](#how-to-handle-subdomains)
- [SPF sorunlarını giderme](#troubleshooting-spf)

<!--
[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

Bu makalede, Office 365'da özel etki alanınızla Sender Policy Framework (SPF) e-posta kimlik doğrulamasını kullanabilmeniz için bir Etki Alanı Adı Hizmeti (DNS) kaydının nasıl güncelleştirildiği açıklanır.

SPF, özel etki alanınızdan gönderilen giden e-postanın *doğrulanmasında* yardımcı olur (bu e-postanın kimden geldiğini söylüyor). SPF, [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC'nin](use-dmarc-to-validate-email.md) tam olarak önerilen e-posta kimlik doğrulama yöntemlerini ayarlamanın ilk adımıdır.

- [Önkoşullar](#prerequisites)
- [SPF TXT kaydınızı oluşturma veya güncelleştirme](#create-or-update-your-spf-txt-record)
  - [Alt etki alanları nasıl işlenir?](#how-to-handle-subdomains)
- [SPF e-posta kimlik doğrulaması gerçekte ne yapar?](#what-does-spf-email-authentication-actually-do)
  - [SPF sorunlarını giderme](#troubleshooting-spf)
- [SPF hakkında daha fazla bilgi](#more-information-about-spf)

## <a name="prerequisites"></a>Önkoşullar

> [!IMPORTANT]
> **Küçük bir işletmeyseniz** veya IP adreslerini veya DNS yapılandırmasını bilmiyorsanız İnternet etki alanı kayıt şirketinizi (ör. GoDaddy, Bluehost, web.com) & *SPF'nin DNS yapılandırması* (ve diğer e-posta kimlik doğrulama yöntemleri) ile ilgili yardım ister. <p> **Özel bir URL kullanmıyorsanız** (ve Office 365 için kullanılan URL **onmicrosoft.com** ile bitiyorsa), SPF sizin için Office 365 hizmetinde zaten ayarlanmıştır.

Haydi başlayalım.

Office 365 için SPF TXT kaydı, tüm özel etki alanları veya alt etki alanları için dış DNS'te yapılır. Kaydı yapmak için bazı bilgilere ihtiyacınız var. Bu bilgileri toplayın:

- Varsa, özel etki alanınız için SPF TXT kaydı. Yönergeler için bkz. [Office 365 DNS kayıtları oluşturmak için ihtiyacınız olan bilgileri toplama](../../admin/get-help-with-domains/information-for-dns-records.md).

- Mesajlaşma sunucularınıza gidin ve Dış IP adreslerini (tüm şirket içi mesajlaşma sunucularından gereklidir) öğrenin. Örneğin, **131.107.2.200**.

- SPF TXT kaydınıza eklemeniz gereken tüm üçüncü taraf etki alanları için kullanılacak etki alanı adları. Bazı toplu posta sağlayıcıları, müşterileri için kullanılacak alt etki alanları ayarlamışlardır. Örneğin, MailChimp şirketi **servers.mcsv.net** ayarladı.

- SPF TXT kaydınız için hangi zorlama kuralını kullanmak istediğinizi öğrenin. **-all** kuralı önerilir. Diğer söz dizimi seçenekleri hakkında ayrıntılı bilgi için bkz. [Office 365 için SPF TXT kaydı söz dizimi](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Özel etki alanı kullanmak için, Office 365 kimlik sahtekarlıklarını önlemeye yardımcı olmak için DNS kaydınıza bir Sender Policy Framework (SPF) TXT kaydı eklemeniz gerekir.

## <a name="create-or-update-your-spf-txt-record"></a>SPF TXT kaydınızı oluşturma veya güncelleştirme

1. Aşağıdaki tabloda yer alan SPF söz dizimini bildiğinizden emin olun.

    |Öğe|Kullanıyorsanız...|Müşteriler için ortak mı?|Bunu ekle...|
    |---|---|---|---|
    |1|Herhangi bir e-posta sistemi (gerekli)|Ortak. Tüm SPF TXT kayıtları bu değerle başlar|`v=spf1`|
    |2|Exchange Online|Ortak|`include:spf.protection.outlook.com`|
    |3|Yalnızca ayrılmış Exchange Online|Yaygın değil|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Almanya, yalnızca Microsoft Bulut Almanya|Yaygın değil|`include:spf.protection.outlook.de`|
    |5|Üçüncü taraf e-posta sistemi|Yaygın değil|`include:<domain_name>` <p> \<domain_name\> üçüncü taraf e-posta sisteminin etki alanıdır.|
    |6|Şirket içi e-posta sistemi. Örneğin, Exchange Online Protection artı başka bir e-posta sistemi|Yaygın değil|Her ek posta sistemi için aşağıdakilerden birini kullanın: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> ve \<domain_name\> etki alanınız adına posta gönderen diğer e-posta sisteminin IP adresi ve etki alanıdır.|
    |7|Herhangi bir e-posta sistemi (gerekli)|Ortak. Tüm SPF TXT kayıtları bu değerle biter|`<enforcement rule>` <p> Bu, çeşitli değerlerden biri olabilir. değerini `-all`öneririz.|

2. Henüz yapmadıysanız, tablodan söz dizimini kullanarak SPF TXT kaydınızı oluşturun.

   Örneğin, tamamen Office 365 barındırılıyorsanız, yani şirket içi posta sunucularınız yoksa, SPF TXT kaydınız 1, 2 ve 7. satırları içerir ve şöyle görünür:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **Yukarıdaki örnek en yaygın SPF TXT kaydıdır**. Bu kayıt, Microsoft veri merkezinizin Birleşik Devletler veya Avrupa'da (Almanya dahil) veya başka bir konumda bulunması fark etmeksizin hemen hemen herkes için çalışır.

   Ancak Microsoft Cloud Germany'nin bir parçası olan Office 365 Germany satın aldıysanız 2. satır yerine 4. satırdaki include deyimini kullanmanız gerekir. Örneğin, tamamen Office 365 Almanya'da barındırılıyorsanız, yani şirket içi posta sunucularınız yoksa, SPF TXT kaydınız 1, 4 ve 7. satırları içerir ve şöyle görünür:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Office 365'de zaten dağıtıldıysanız ve özel etki alanınız için SPF TXT kayıtlarınızı ayarladıysanız ve Office 365 Almanya'ya geçiriyorsanız SPF TXT kaydınızı güncelleştirmeniz gerekir. Bunu yapmak için olarak değiştirin `include:spf.protection.outlook.com` `include:spf.protection.outlook.de`.

3. SPF TXT kaydınızı oluşturduktan sonra DNS'de kaydı güncelleştirmeniz gerekir. **Bir etki alanı için yalnızca bir SPF TXT kaydınız olabilir.** Bir SPF TXT kaydı varsa, yeni kayıt eklemek yerine var olan kaydı güncelleştirmeniz gerekir. [Office 365 için DNS kayıtları oluşturma'ya](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) gidin ve DNS barındırma sağlayıcınızın bağlantısını seçin.

4. SPF TXT kaydınızı test edin.

## <a name="how-to-handle-subdomains"></a>Alt etki alanları nasıl işlenir?

Alt etki alanları *üst düzey etki alanının SPF kaydını devralmadığı için her alt etki alanı için ayrı bir kayıt oluşturmanız gerektiğini* unutmayın.

Saldırganların varolmayan alt etki alanından olduğunu iddia eden e-posta göndermesini önlemek için her etki alanı ve alt etki alanı için bir joker karakter SPF kaydı (`*.`) gereklidir. Örneğin:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>SPF sorunlarını giderme

SPF TXT kaydınızla ilgili sorun mu yaşıyorsunuz? Sorun [Giderme: Office 365'da SPF için en iyi yöntemler makalesini](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot) okuyun.

## <a name="what-does-spf-email-authentication-actually-do"></a>SPF e-posta kimlik doğrulaması gerçekte ne yapar?

SPF, sizin adınıza posta göndermesine izin verilen posta sunucularını tanımlar. Temel olarak SPF, DKIM, DMARC ve Office 365 tarafından desteklenen diğer teknolojilerle birlikte kimlik sahtekarlığı ve kimlik avının önlenmesine yardımcı olur. SPF, DNS tarafından özel etki alanınız adına hangi posta sunucularının posta gönderebileceğini belirlemek için kullanılan bir TXT kaydı olarak eklenir. Alıcı posta sistemleri, özel etki alanınızdan gelen bir iletinin yetkili bir mesajlaşma sunucusundan gelip alınmadığını belirlemek için SPF TXT kaydına başvurur.

Örneğin, özel etki alanı contoso.com Office 365 kullandığını düşünelim. Office 365 mesajlaşma sunucularını etki alanınız için geçerli posta sunucuları olarak listeleyen bir SPF TXT kaydı eklersiniz. Alıcı mesajlaşma sunucusu joe@contoso.com bir ileti aldığında, sunucu contoso.com için SPF TXT kaydını arar ve iletinin geçerli olup olmadığını bulur. Alıcı sunucu, iletinin SPF kaydında listelenen Office 365 mesajlaşma sunucuları dışında bir sunucudan geldiğini öğrenirse, alıcı posta sunucusu iletiyi istenmeyen posta olarak reddetmeyi seçebilir.

Ayrıca, özel etki alanınızın SPF TXT kaydı yoksa, bazı alıcı sunucular iletiyi doğrudan reddedebilir. Bunun nedeni, alıcı sunucunun iletinin yetkili bir mesajlaşma sunucusundan geldiğini doğrulayamıyor olmasıdır.

Office 365 için postayı zaten ayarladıysanız, Microsoft'un mesajlaşma sunucularını ZATEN BIR SPF TXT kaydı olarak DNS'ye eklemişsinizdir. Ancak, DNS'de SPF TXT kaydınızı güncelleştirmeniz gerekebilecek bazı durumlar vardır. Örneğin:

- Daha önce, SharePoint Online kullanıyorsanız özel etki alanınıza farklı bir SPF TXT kaydı eklemeniz gerekiyordu. Bu artık gerekli değildir. Bu değişiklik, SharePoint Çevrimiçi bildirim iletilerinin Gereksiz E-posta klasörüne düşmesi riskini azaltmalıdır. 10 arama sınırına ulaşıyorsanız ve "arama sınırını aştı" ve "çok fazla atlama" gibi hatalar alıyorsanız SPF TXT kaydınızı güncelleştirin.

- Office 365 ve şirket içinde Exchange karma bir ortamınız varsa.

- DKIM ve DMARC'yi ayarlamayı planlıyorsunuz (önerilir).

## <a name="more-information-about-spf"></a>SPF hakkında daha fazla bilgi

Gelişmiş örnekler için desteklenen SPF söz dizimi, kimlik sahtekarlığı, sorun giderme ve Office 365 SPF'yi nasıl desteklediği hakkında daha ayrıntılı bir tartışma için bkz. [Office 365 kimlik sahtekarlığı ve kimlik avının önlenmesi için SPF nasıl çalışır](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks)?

## <a name="next-steps-dkim-and-dmarc"></a>Sonraki Adımlar: DKIM ve DMARC

 SPF, kimlik sahtekarlıklarını önlemeye yardımcı olmak için tasarlanmıştır, ancak SPF'nin koruyabileceği kimlik sahtekarlık teknikleri vardır. Bunlara karşı savunmak için SPF'yi ayarladıktan sonra DKIM ve DMARC'yi Office 365 için yapılandırmanız gerekir.

[**DKIM**](use-dkim-to-validate-outbound-email.md) e-posta kimlik doğrulamasının amacı, posta içeriğinin değiştirilmediğini kanıtlamaktır.

[**DMARC**](use-dmarc-to-validate-email.md) e-posta kimlik doğrulamasının amacı, SPF ve DKIM bilgilerinin Kimden adresiyle eşleştiğinden emin olmaktır.

 Gelişmiş örnekler ve desteklenen SPF söz dizimi hakkında daha ayrıntılı bir tartışma için bkz. [Office 365 kimlik sahtekarlığı ve kimlik avının önlenmesi için SPF nasıl çalışır](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks)?

*Bu belgelerle ilgili geri bildiriminiz varsa 'Geri Bildirim' bölümünden 'Bu sayfa' öğesini seçin.*
