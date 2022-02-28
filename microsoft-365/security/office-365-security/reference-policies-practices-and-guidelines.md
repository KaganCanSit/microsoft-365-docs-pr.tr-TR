---
title: Başvuru İlkeleri, yöntemler ve yönergeler
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
- MET150
ms.assetid: ff3f140b-b005-445f-bfe0-7bc3f328aaf0
ms.collection:
- M365-security-compliance
description: Microsoft, kullanıcılarımızı kötü amaçlı, istenmeyen veya kötü amaçlı e-postalara karşı korumaya yardımcı olmak için çeşitli ilkeler, yordamlar ve çeşitli endüstri en iyi yöntemleri benimsedi.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 21b1918155755d7786f7b797ae7c705ca8c0ec39
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988765"
---
# <a name="reference-policies-practices-and-guidelines"></a>Başvuru: İlkeler, yöntemler ve yönergeler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft, web'de en güvenilir kullanıcı deneyimini sağlama konusunda yardımcı olmak için ayrılmıştır. Bu nedenle, Microsoft kullanıcılarımızı kötü amaçlı, istenmeyen veya kötü amaçlı e-postalara karşı korumaya yardımcı olmak için çeşitli endüstri en iyi yöntemleri benimseyen çeşitli ilkeler, yordamlar ve benimsenmiş oldu. Kullanıcılara e-posta göndermeye çalışan gönderenler, bu çabaya yardımcı olmak ve olası teslim sorunlarını önlemeye yardımcı olmak için bu makaledeki rehberleri tam olarak anlarından ve takiplarından emin olmalı.

Bu ilke ve yönergelere uygun değilsanız, destek ekibimiz size yardımcı olabilir. Bu makalede sunulan yönergelere, uygulamalara ve ilkelere bağlı olarak kalıyorsanız ve gönderen IP adresinize bağlı olarak teslim sorunlarıyla hala yaşıyorsanız, lütfen kayıt isteği göndermek için adımları izleyin. Yönergeler için bkz [. Kendinizi engellenen gönderenler listesinden kaldırmak için liste portalını kullanma](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="general-microsoft-policies"></a>Genel Microsoft ilkeleri

Kullanıcılara gönderilen Microsoft 365, e-posta iletimi ve kullanıcı e-postanın kullanımıyla ilgili tüm Microsoft ilkelerine uygun Microsoft 365.

- Web sitelerine uygulanan Microsoft 365 Koşulları; özellikle de hizmeti istenmeyen posta olarak kullanmak veya kötü amaçlı yazılım dağıtmak için yasaklama.

- [Microsoft Hizmet Sözleşmesi](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Resmi düzenlemeler

Kullanıcılara gönderilen Microsoft 365 ilgili yargı yetkisine sahip e-posta iletişimlerini yöneten tüm geçerli yasalara ve yasal düzenlemelere uyması gerekir.

- [CAN-SPAM Act: A Compliance Guide for Business](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- ["Beni Kaldır" Yanıtları ve Sorumlulukları: E-posta Pazarlamacıları "Abonelikten Çıkma" İddialarını Yerine Getirmeli](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Teknik yönergeler

E-Microsoft 365 gönderilen e-postanın aşağıdaki belgelerde listelenen uygulanabilir önerilere uygun olması gerekir (bazı bağlantılar yalnızca İngilizce dilinde kullanılabilir).

- [RFC 2505: SMTP MTA'lar Öneriler İstenmeyen Posta Önleme bilgileri](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: Komut Aktarma için SMTP Hizmet Uzantısı](https://www.ietf.org/rfc/rfc2920.txt)

Buna ek olarak, E-posta'ya Microsoft 365 e-posta sunucularının aşağıdaki gereksinimlere uyması gerekir:

- Gönderenin, RFC 5321, RFC 5322 ve diğer İnternet Internet Mühendislik Görev Gücü'nde (IETF) yayımladığı üzere, İnternet e-postası iletimiyle ilgili tüm teknik standartlara uyması bekleniyor.

- 500 ile 599 arasında (kalıcı teslim edilemedi yanıtı veya NDR olarak da bilinir) sayısal SMTP hata yanıt kodu verilidikten sonra, gönderenin bu iletiyi o alıcıya yeniden aktarmayı denemesi gerekir.

- Birden fazla teslim yanıtın ardından, gönderenin bu alıcıya e-posta gönderme denemelerini durdurması gerekir.

- İletilerin güvenli olmayan e-posta geçişi veya ara sunucular aracılığıyla iletilenemleri.

- Tek tek listelerden veya gönderen tarafından barındırılan tüm listelerden abonelikten çıkma mekanizması, alıcıların kolayca belgelenmiş ve kolayca bulunsun ve kullansın.

- Dinamik IP boşluğundan bağlantılar kabul edilemey.

- E-posta sunucularının geçerli geçerli ters DNS kayıtlarına sahip olması gerekir.

## <a name="reputation-management"></a>İtibaren yönetimi

Gönderenler, ISS'ler ve diğer hizmet sağlayıcıları, giden IP adreslerinin itibarını etkin bir şekilde yönetmeleri gerekir.

## <a name="microsoft-365-limits"></a>Microsoft 365 sınırları

Gönderenlerin, Sınırlarda Microsoft 365 sınırlara [Exchange Online Protection gerekir](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>E-posta teslim kaynakları ve kuruluşlar

Microsoft, İnternet ve e-posta ekosistemini geliştirmek için sektör gövdeleri ve hizmet sağlayıcılarıyla etkin bir şekilde çalışır. Bu kuruluşlar, destekleyen ve gönderenlerin bağlı kalmalarını öneren en iyi uygulama belgelerini yayımlar. Bu, dünyanın her bir yerine gelen çeşitli e-posta servis sağlayıcıları arasında e-posta teslim etme olanağınızı geliştirmektedir.

- [Malware Mobile Kötü Amaçlı Yazılımdan Korunma Çalışma Grubu](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [E-posta & Sağlayıcı Sağlayıcı Sağlayıcı](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Kötüye kullanım ve istenmeyen posta bildirimi

Yasa dışı, kötü amaçlı, istenmeyen veya kötü amaçlı e-postaları rapor etmek için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md). Bu tür iletişimleri göndermek Microsoft'un ilkelerini ihlal etmiş olur ve onaylandı raporlarında uygun önlemleri alınır.

## <a name="law-enforcement"></a>Yasa yaptırımı

Bir hukuk yaptırımı üyesiyseniz ve Office 365 ile ilgili yasal belgelerle Microsoft Corporation'a hizmet vermek isterseniz veya Microsoft'a gönderilen yasal belgelerle ilgili sorularınız varsa lütfen (1) (425) 722-1299'u arayın.