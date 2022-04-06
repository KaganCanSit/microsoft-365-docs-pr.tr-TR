---
title: Mimari gereksinimlerini ve planlama kavramlarını gözden Office 365 için Microsoft Defender
description: Microsoft 365 Defender'daki Office 365 için Microsoft Defender diyagramı, deneme laboratuvarınızı veya pilot ortamınızı oluşturmadan Microsoft 365 anda kimliğinizi anlamanıza yardımcı olur.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0ce03f919d3a4012952ab7d2056b33f2eeb71926
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569479"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>Temel Office 365 için Microsoft Defender gereksinimlerini ve temel kavramları gözden geçirin


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, [değerlendirme ortamını ayarlama](eval-defender-office-365-overview.md) işleminin 1/ 3. adımıdır ve Office 365 için Microsoft Defender. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-office-365-overview.md).

Yapıyı etkinleştirmeden Office 365 için Defender mimariyi anlıyoruz ve gereksinimleri karşılayana kadar emin olun. Bu makalede, bu ortamın karşılaması gereken mimari, temel kavramlar ve Exchange Online önkoşullar açıklanmıştır.

## <a name="understand-the-architecture"></a>Mimariyi anlama

Aşağıdaki diyagramda, üçüncü taraf SMTP ağ geçidini veya şirket içi tümleştirmeyi de içermesi Office için Microsoft Defender temel mimarisini gösterir. Karma birlikte çalışma senaryoları (başka bir ifadeyle, üretim posta kutuları hem şirket içi hem de çevrimiçidir) daha karmaşık yapılandırmalar gerektirir ve bu makale veya değerlendirme kılavuzunda ele alınmayacaktır.

:::image type="content" source="../../media/defender/m365-defender-office-architecture.png" alt-text="Mimariye uygun Office 365 için Microsoft Defender" lightbox="../../media/defender/m365-defender-office-architecture.png":::

Aşağıdaki tabloda bu çizim açık gösterilmiştir.

|Çağrıdan çıkma  |Açıklama  |
|---------|---------|
|1     | Dış gönderenin ana bilgisayar sunucusu normalde MX kaydı için genel bir DNS araması yapar ve bu da iletiyi geçişi için hedef sunucunun sağlar.  Bu başvuru doğrudan Exchange Online (EXO) veya EXO'ye geçiş için yapılandırılmış bir SMTP ağ geçidi olabilir.  |
|2     | Exchange Online Protection fazla ilkeler, etiketleme veya işlemenin gerekli olduğunu belirlemek için ileti üst bilgileriyle içeriğini inceler ve gelen bağlantısının görüşmelerini ve doğrulamalarını sağlar.  |
|3     | Exchange Online gelişmiş tehdit Office 365 için Microsoft Defender, azaltma ve düzeltme sunmak için güvenlik özellikleriyle tümleştirilmiştir. |
|4     | Kötü amaçlı, engellenmemiş veya karantinaya alınmış bir ileti işlenir ve EXO'de alıcıya teslim edilir; burada gereksiz postayla, posta kutusu kurallarıyla veya diğer ayarlarla ilgili kullanıcı tercihleri değerlendirilir ve tetiklenir. |
|5     | Posta özellikli şirket içi Active Directory ve hesapları eşitlemek ve en sonunda en üst düzeye Bağlan için eşitlemek ve sağlanması için Azure AD Azure Active Directory ile tümleştirme Exchange Online. |
|6     | Şirket içi ortamı tümleştirinken, postayla ilgili özniteliklerin, ayarların ve yapılandırmaların desteklenen yönetimi ve yönetimi için Exchange sunucusu kullanmaya teşvik edilebilir |
|7     | Office 365 için Microsoft Defender algılama ve yanıt Microsoft 365 Defender (XDR) için sinyal paylaşımı sağlar.|

Şirket içi tümleştirme yaygındır, ancak isteğe bağlıdır. Ortamınız yalnızca bulut tabanlı ise, bu kılavuz size de yardımcı olur.

## <a name="understand-key-concepts"></a>Önemli kavramları anlama

Aşağıdaki tabloda, MDO'yu değerlendirme, yapılandırma ve dağıtmada anlamanın önemli olduğu önemli kavramlar tanımlandı.


|Kavram  |Açıklama |Daha fazla bilgi  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP), organizasyonlarınızı istenmeyen postalara ve kötü amaçlı yazılım e-postalarına karşı korumaya yardımcı olan bulut tabanlı filtreleme hizmetidir. EOP, yeni Microsoft 365 lisansların tüm lisanslarında Exchange Online.     |   [Exchange Online Protection’a genel bakış](../office-365-security/exchange-online-protection-overview.md)      |
|Kötü amaçlı yazılımdan koruma     |    EXO'da posta kutuları olan kuruluşlar, kötü amaçlı yazılımlara karşı otomatik olarak korunur.     |  [EOP'de kötü amaçlı yazılımdan koruma](../office-365-security/anti-malware-protection.md)       |
|İstenmeyen posta önleme koruması     |   EXO'da posta kutuları olan kuruluşlar, gereksiz posta ve istenmeyen posta ilkelerine karşı otomatik olarak korunur.      |  [EOP'de istenmeyen posta önleme koruması](../office-365-security/anti-spam-protection.md)       |
|Kimlik avı koruması |  MDO, kimlik avı, veri avı, fidye yazılımı ve diğer zararlı etkinliklerle ilgili daha gelişmiş kimlik avı koruması sunar.   | [E-posta'da ek kimlik avı koruması Office 365 için Microsoft Defender](../office-365-security/anti-phishing-protection.md)   |
|Anti-spoing protection     |   EOP, kurumlarınızı sahte (sahte) gönderenlerden korumaya yardımcı olan özellikler içerir.      |   [EOP'de anti-poing protection](../office-365-security/anti-spoofing-protection.md)      |
|Kasa ekleme     |   Kasa Ekler, e-posta iletilerine teslim edilene kadar ekleri kontrol etmek ve "detonate" etmek için sanal bir ortam kullanarak ek bir koruma katmanı sağlar.      |   [Kasa'de Ekleri Office 365 için Microsoft Defender](../office-365-security/safe-attachments.md)      |
|Kasa, dosya SharePoint OneDrive için ekleri Microsoft Teams     |    Ayrıca, Kasa, SharePoint OneDrive ve Microsoft Teams ekleri, bulut depolama depolarında karşıya yüklenen dosyalar için ek bir koruma katmanı sunar.     |  [Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|Güvenli Bağlantılar     | Kasa Bağlantılar, gelen e-posta iletileri içinde URL taraması ve yeniden yazma özellikleri sağlar ve teslim veya tıklamadan önce bu bağlantıların doğrulamasını sağlar.        |   [Kasa'daki Bağlantıları Office 365 için Microsoft Defender](../office-365-security/safe-links.md)      |
|    |         |         |

İş için Microsoft Defender'da bulunan özellikler hakkında daha fazla bilgi Office bkz. [Office 365 için Microsoft Defender açıklama.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)

## <a name="review-architecture-requirements"></a>Mimari gereksinimleri gözden geçirin
Başarılı bir MDO değerlendirmesi veya üretim pilotları aşağıdaki önkulları varsayıyor:
- Tüm alıcı posta kutularınız şu anda posta Exchange Online.
- Genel MX kaydınız doğrudan EOP'ye veya üçüncü taraf SMTP ağ geçidine çözüm gelir ve bu ağ geçidi gelen dış e-postayı doğrudan EOP'ye iletir.
- Birincil e-posta etki alanınız *e-posta adresinizde* yetkili Exchange Online.
- Dizin Tabanlı Uç Engelleme'yi (DBEB) uygun *şekilde* başarıyla dağıttınız ve yapılandırdınız. Daha fazla bilgi için bkz [. Geçersiz Directory-Based iletileri reddetmek için Edge Engelleme'nin kullanımını engelleme](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> Bu gereksinimler geçerli yoksa veya hala karma bir birlikte çalışma senaryosundasanız, Office 365 için Microsoft Defender değerlendirme bu kılavuzda tam olarak kapsamına uymayan daha karmaşık veya gelişmiş yapılandırmalar gerekli olabilir.

## <a name="siem-integration"></a>SIEM tümleştirmesi

Etkili ve Office 365 için Microsoft Defender yanıt için, tüm organizasyon genelindeki güvenlik olaylarını daha kapsamlı olarak çözümlemek ve çalışma kitapları oluşturmak için bu uygulamaları Microsoft Sentinel ile tümleştirin. Daha fazla bilgi için bkz[. Bağlan uyarılarını Office 365 için Microsoft Defender](/azure/sentinel/connect-office-365-advanced-threat-protection).

Office 365 için Microsoft Defender Bilgileri ve Etkinlik Yönetimi API'si kullanılarak diğer Güvenlik Bilgileri ve Olay Yönetimi (SIEM) [çözümleriyle Office 365 da olabilir](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>Sonraki adımlar

Adım 2 / 3: [Değerlendirme ortamını etkinleştirme Office 365 için Microsoft Defender](eval-defender-office-365-enable-eval.md)

Değerlendirme görünümüne genel [bakış Office 365 için Microsoft Defender](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md) 
