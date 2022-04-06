---
title: SPF'yi, sanallık engellemeye yardımcı olacak şekilde ayarlama
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
description: Bir etki alanı içinde Sender Policy Framework'i (SPF) özel etki alanınız ile kullanmak için Etki Alanı Adı Hizmeti (DNS) kaydını nasıl Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a25efbce5b9f8141575a88baa3fdd85b099dfbd6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682977"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>SPF'yi, sanallık engellemeye yardımcı olacak şekilde ayarlama

- [Önkoşullar](#prerequisites)
- [SPF TXT kaydınızı oluşturma veya güncelleştirme](#create-or-update-your-spf-txt-record)
- [Alt etki alanları nasıl iş olur?](#how-to-handle-subdomains)
- [SPF sorunlarını giderme](#troubleshooting-spf)

<!--
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

Bu makalede, özel etki alanınız ile Sender Policy Framework (SPF) e-posta kimlik doğrulamasını kullanmak için Etki Alanı Adı Hizmeti (DNS) kaydını nasıl güncelleştirileceğini Office 365.

SPF, *özel etki* alanınıza gönderilen giden e-postayı doğrulamaya yardımcı olur (bu e-postanın olduğunu söyleyen kişiden gelir). SPF, [DKIM](use-dkim-to-validate-outbound-email.md) ve DMARC için tam önerilen e-posta kimlik doğrulama yöntemlerini ayarlamanın [ilk adımıdır](use-dmarc-to-validate-email.md).

- [Önkoşullar](#prerequisites)
- [SPF TXT kaydınızı oluşturma veya güncelleştirme](#create-or-update-your-spf-txt-record)
  - [Alt etki alanları nasıl iş olur?](#how-to-handle-subdomains)
- [SPF e-posta kimlik doğrulaması aslında ne yapar?](#what-does-spf-email-authentication-actually-do)
  - [SPF sorunlarını giderme](#troubleshooting-spf)
- [SPF hakkında daha fazla bilgi](#more-information-about-spf)

## <a name="prerequisites"></a>Önkoşullar

> [!IMPORTANT]
> Küçük bir **işletmeysanız ya** da IP adresleri veya DNS yapılandırması hakkında bilginiz yoksa İnternet etki alanı kayıt şirketinizi arayın (örneğin. GoDaddy, Bluehost, web.com) *& SPF'nin DNS* yapılandırması (ve diğer herhangi bir e-posta kimlik doğrulaması yöntemi) ile ilgili yardım almak için yardım istemeniz gerekir. <p> **Özel BIR URL kullanamıyorsanız** (ve URL için kullanılan URL Office 365 onmicrosoft.com ile bitiyorsa **),** SPF sizin için Office 365 önceden ayarlanmıştır.

Haydi işe bakalım.

Etki alanları için SPF TXT Office 365 özel etki alanları veya alt etki alanları için dış DNS'de yapılır. Kaydı yapmak için bazı bilgilere ihtiyacınız var. Bu bilgileri toplayın:

- Özel etki alanınız için (varsa) SPF TXT kaydı. Yönergeler için bkz[. DNS kayıtlarında oluşturmak için Office 365 toplama](../../admin/get-help-with-domains/information-for-dns-records.md).

- Mesajlaşma sunucularınıza gidin ve Dış IP adreslerini (tüm şirket içi ileti sunucularından gerekli) bulun. Örneğin **131.107.2.200**.

- SPF TXT kaydınıza eklemek istediğiniz tüm üçüncü taraf etki alanlarında kullanmak üzere etki alanı adları. Bazı toplu posta sağlayıcıları, müşterileri için kullanmak üzere alt etki alanları ayarlamaktadır. Örneğin, MailChimp şirketi **posta servers.mcsv.net.**

- SPF TXT kaydınız için kullanmak istediğiniz zorlama kuralını bulun. **-all** kuralı önerilir. Diğer söz dizimi seçenekleri hakkında ayrıntılı bilgi için bkz. [SPF TXT kaydı söz dizimi Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Özel bir etki alanı kullanmak için, Office 365 kimlik doğrularının önlenmesine yardımcı olmak için DNS kaydınıza Bir Sender Policy Framework (SPF) TXT kaydı eklemeniz gerekir.

## <a name="create-or-update-your-spf-txt-record"></a>SPF TXT kaydınızı oluşturma veya güncelleştirme

1. Aşağıdaki tabloda, SPF söz dizimi hakkında bilgi sahibi olduğunu denetleyin.

    |Element|Eğer kullanıyorsanız...|Müşteriler arasında sık karşılaşılan bir durum mu var?|Bunu ekleyin...|
    |---|---|---|---|
    |1|Herhangi bir e-posta sistemi (gerekli)|Ortak. Tüm SPF TXT kayıtları bu değerle başlar|`v=spf1`|
    |2|Exchange Online|Ortak|`include:spf.protection.outlook.com`|
    |3|Exchange Online özel|Yaygın değil|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Almanya, yalnızca Microsoft Bulut Germany|Yaygın değil|`include:spf.protection.outlook.de`|
    |5|Üçüncü taraf e-posta sistemi|Yaygın değil|`include:<domain_name>` <p> \<domain_name\> üçüncü taraf e-posta sisteminin etki alanıdır.|
    |6|Şirket içi e-posta sistemi. Örneğin, Exchange Online Protection başka bir e-posta sistemi|Yaygın değil|Her ek posta sistemi için bunlardan birini kullanın: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> ve \<domain_name\> etki alanınız adına posta gönderen diğer e-posta sisteminin IP adresi ve etki alanıdır.|
    |7|Herhangi bir e-posta sistemi (gerekli)|Ortak. Tüm SPF TXT kayıtları bu değerle sona erer|`<enforcement rule>` <p> Bu birkaç değerden biri olabilir. Değerini öneririz `-all`.|

2. Henüz bunu yapmadıysanız, tablonun söz dizimini kullanarak SPF TXT kaydınızı form açın.

   Örneğin, tamamen Office 365'de barındırıldıysanız, başka bir ifadeyle şirket içi posta sunucularınız yoksa, SPF TXT kaydınız 1, 2 ve 7 satırlarını içerebilir ve aşağıdakine benzer olur:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **Yukarıdaki örnek en yaygın SPF TXT kaydıdır**. Microsoft veri merkezinizin AMERIKA Birleşik Devletleri'nde mi, Avrupa'da mı (Almanya dahil) yoksa başka bir konumda mı bulunduğuna bakılmaksızın, bu kayıt hemen herkes için çalışır.

   Bununla birlikte, Microsoft Bulut Office 365 bir parçası olan Almanya'yı satın aldıysanız, satır 2 yerine 4. satırdan include deyimini kullanabilirsiniz. Örneğin, tamamen Office 365 Germany'de barındırıldıysanız, yani şirket içi posta sunucularınız yoksa, SPF TXT kaydınız 1, 4 ve 7. satırları içerebilir ve aşağıdakine benzer olur:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Office 365'de zaten dağıtıldınız ve özel etki alanınız için SPF TXT kayıtlarınızı ayardıysanız ve Office 365 Germany'ye geçtiysiniz, SPF TXT kaydınızı güncelleştirmeniz gerekir. Bunu yapmak için olarak değiştirebilirsiniz `include:spf.protection.outlook.com` `include:spf.protection.outlook.de`.

3. SPF TXT kaydınızı kurduktan sonra, DNS'deki kaydı güncelleştirmeniz gerekir. **Etki alanı için yalnızca bir SPF TXT kaydınız olabilir.** SPF TXT kaydı varsa, yeni kayıt eklemek yerine var olan kaydı güncelleştirmeniz gerekir. Dns barındırma [hizmeti için DNS Office 365'e](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) gidin ve DNS barındırması için bağlantıyı seçin.

4. SPF TXT kaydınızı test etmek için.

## <a name="how-to-handle-subdomains"></a>Alt etki alanları nasıl iş olur?

Alt etki alanları en üst düzey etki alanının *SPF* kaydını devralmaz, çünkü her alt etki alanı için ayrı bir kayıt oluşturmanız gerekir.

Saldırganların var olmayan alt etki alanları olduğunu iddia eden e-posta göndermelerini önlemek için, her etki alanı ve alt etki alanı için joker karakterli SPF kaydı (`*.`) gerekir. Örneğin:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>SPF sorunlarını giderme

SPF TXT kaydıyla ilgili sorun mu var? Sorun [Giderme: En iyi SPF için en iyi Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>SPF e-posta kimlik doğrulaması aslında ne yapar?

SPF, sizin adına posta göndermesine izin verilen posta sunucularını tanımlar. Temelde, SPF, DKIM, DMARC ve diğer teknolojilerin Office 365 kimlik sahteciliği ve kimlik avını önlemeye yardımcı olur. SPF, özel etki alanınız adına hangi posta sunucularının posta gönderileceğini belirlemek için DNS tarafından kullanılan bir TXT kaydı olarak eklenir. Alıcı posta sistemleri, özel etki alanınıza gelen bir iletinin yetkili bir ileti sunucusundan gelip gelip olmadığını belirlemek için SPF TXT kaydına başvurur.

Örneğin, kendi özel etki alanı etki contoso.com etki Office 365. Etki alanınız için geçerli posta sunucuları olarak en iyi Office 365 posta sunucularını listeen bir SPF TXT kaydı eklersiniz. Alıcı ileti sunucusu joe@contoso.com'tan bir ileti geldiğinde, sunucu SPF TXT kaydını contoso.com ve iletinin geçerli olup olmadığını bulur. Alıcı sunucu iletinin SPF kaydında listelenen ileti sunucularından Office 365 bir sunucudan geldiğinde, alıcı posta sunucusu iletiyi istenmeyen posta olarak reddetmeyi seçebilir.

Ayrıca, özel etki alanınız SPF TXT kaydına sahip değilse, bazı alıcı sunucular iletiyi geri reddedebilirsiniz. Bunun nedeni, alıcı sunucunun iletinin yetkili bir ileti sunucusundan gelip almadı iletiyi doğrulayamalanmasıdır.

Office 365 için postayı zaten ayarladıysanız, Microsoft'un mesajlaşma sunucularını DNS'ye zaten bir SPF TXT kaydı olarak ekleyebilirsiniz. Bununla birlikte, DNS'de SPF TXT kaydınızı güncelleştirmeniz gereken bazı durumlar olabilir. Örneğin:

- SharePoint Online kullanıyorsanız, özel etki alanınıza daha önce farklı bir SPF TXT kaydı SharePoint vardı. Bu artık gerekli değildir. Bu değişiklik, Çevrimiçi bildirim SharePoint Gereksiz E-posta klasörüne kadar olan iletilerden çalışma riskini azaltmalı. "Arama sınırını aştı" ve "çok fazla atlama" gibi 10 arama sınırına ulaşıyorsanız ve hata alıyorsanız SPF TXT kaydınızı güncelleştirin.

- Karma ve karma bir ortamınız Office 365 şirket Exchange olabilir.

- DKIM ve DMARC'ı ayarlamayı hedeflisiniz (önerilir).

## <a name="more-information-about-spf"></a>SPF hakkında daha fazla bilgi

Gelişmiş örnekler için, desteklenen SPF söz dizimi, kimlik avı, sorun giderme ve Office 365'in SPF'yi nasıl desteklediği hakkında daha ayrıntılı bir açıklama için bkz. SPF, kimlik avını ve kimlik avını [önlemek için Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Sonraki Adımlar: DKIM ve DMARC

 SPF,poing'i önlemeye yardımcı olmak için tasarlanmıştır ancak SPF'nin koruyamay olduğu sanallık tekniklerini vardır. Bunlara karşı savunma yapmak için, SPF'yi ayarlamış olduktan sonra DKIM ve DMARC'yi daha büyük bir Office 365.

[**DKIM**](use-dkim-to-validate-outbound-email.md) e-posta kimlik doğrulamasının amacı posta içeriğinin değiştirilmediğini kanıtlamaktır.

[**DMARC**](use-dmarc-to-validate-email.md) e-posta kimlik doğrulamasında amaç, SPF ve DKIM bilgilerinin From adresiyle eş olduğundan emin olmaktır.

 Gelişmiş örnekler ve desteklenen SPF söz dizimi hakkında daha ayrıntılı bir açıklama için bkz. [SPF](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks) kimlik avı ve kimlik avını önlemek için Office 365.

*Bu belgelerde geri bildirimleriniz varsa 'Geri Bildirim' altında 'Bu sayfa' öğesini seçin.*
