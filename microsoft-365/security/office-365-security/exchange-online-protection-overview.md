---
title: Exchange Online Protection (EOP) genel bakış
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Bu posta Exchange Online Protection (EOP) tek başına ve karma ortamlarda şirket içi e-posta kuruluşlarınızı korumaya nasıl yardımcı olduğunu öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 319b20d548ad83cbf57043909a8dc2ce840db5cd
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682669"
---
# <a name="exchange-online-protection-overview"></a>Exchange Online Protection genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP), organizasyonlarınızı istenmeyen postalara, kötü amaçlı yazılımlara ve diğer e-posta tehditlerine karşı koruyan bulut tabanlı filtreleme hizmetidir. EOP, EOP'Microsoft 365 posta kutuları olan tüm Exchange Online vardır.

> [!NOTE]
> EOP, şirket içi posta kutularını ve karma ortamlarda korumak için kendi kendine de kullanılabilir ve şirket içi posta kutularını ve karma Exchange sağlar. Daha fazla bilgi için bkz. [Tek Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

EOP güvenlik özelliklerini ayarlama adımları ve güvenlikle ilgili karşılaştırması, EOP için Microsoft Defender'da Office 365 [tehditlere karşı koruma makalesinde yer almaktadır](protect-against-threats.md). EOP özellikleri için önerilen ayarlarAOP için önerilen ayarlar ve [Güvenlik için Microsoft Defender'da Office 365 vardır](recommended-settings-for-eop-and-office365.md).

Bu makalenin kalan bölümü EOP'nin nasıl çalıştığını ve EOP'de kullanılabilen özellikleri açıklar.

## <a name="how-eop-works"></a>EOP nasıl çalışır?

EOP'nin nasıl çalıştığını anlamak için, gelen e-postayı nasıl işle çalıştığını görmek yardımcı olur:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="EOP'ye geçen ve Gereksiz posta veya karantinaya veya son kullanıcı posta teslimi kararlarından önce EOP'ye geçen ve Bağlantı, Kötü amaçlı yazılımdan koruma, Posta Akışı Kuralları eğik çizgi İlkesi Filtreleme ve İçerik Filtreleme aracılığıyla gelen e-postanın grafiği.":::

1. EOP'ye gelen bir ileti EOP geldiğinde, ilk olarak gönderenin itibarını kontrolen bağlantı filtrelemeden geçer. İstenmeyen postanın çoğunluğu bu noktada durdurulur ve EOP tarafından reddedilir. Daha fazla bilgi için bkz [. Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).

2. Ardından ileti kötü amaçlı yazılımdan denetleniyor. İletide kötü amaçlı yazılım bulunursa veya ekleri varsa, ileti karantinaya teslim edilir. Varsayılan olarak, kötü amaçlı yazılım karantinaya alınmış iletileri yalnızca yöneticiler  görüntülemeli ve bu iletilerle etkileşimde bulunabilirsiniz. Ancak yöneticiler, kullanıcılara karantinaya alınmış [iletilerde](quarantine-policies.md) ne yapma izni verilmiyor belirtmek için karantina ilkeleri oluşturabilir ve kullanabilir. Kötü amaçlı yazılıma karşı koruma hakkında daha fazla bilgi edinmek için bkz. [EOP'de kötü amaçlı yazılımdan koruma](anti-malware-protection.md).

3. İleti, ilke filtreleme aracılığıyla devam eder ve oluşturduğunuz tüm posta akış kurallarına (aktarım kuralları olarak da bilinir) göre değerlendirilir. Örneğin, belirli bir gönderenden ileti geldiğinde kural yöneticiye bildirim gönderebilir.

   Hizmetler lisansları ile Exchange Enterprise CAL'ye sahip şirket içi kuruluşta, EOP'de veri kaybı önleme [(DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) denetimleri de bu noktada ortaya konur.

4. İleti, zararlı iletilerin istenmeyen posta, yüksek güven istenmeyen posta, kimlik avı, yüksek güven kimlik avı veya toplu (istenmeyen posta önleme ilkeleri) veya kimlik avı ilkeleri olarak tanım bulunduğu içerik filtrelemeden (istenmeyen posta önleme ve kimlik sahtesini önleme) geçer. İletiye yönelik eylemi, filtreleme kararını (karantina, Gereksiz E-posta klasörüne taşıma, vb.) ve kullanıcıların karantina ilkeleri kullanarak karantinaya alınmış iletilere neler yapacılarını [yapılandırabilirsiniz](quarantine-policies.md). Daha fazla bilgi için bkz [. EOP'de İstenmeyen](configure-your-spam-filter-policies.md) posta önleme ilkelerini yapılandırma ve Kimlik [avı ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

Tüm bu koruma katmanlarını başarıyla ilene bir ileti alıcılara teslim edilir.

Daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>EOP veri merkezleri

EOP, en iyi kullanılabilirliği sağlamak üzere tasarlanmış dünya çapında bir veri merkezleri ağına çalışır. Örneğin, veri merkezi kullanılamaz hale gelirse, e-posta iletileri hizmette kesinti olmadan otomatik olarak başka bir veri merkezine yönlendirilir. Her veri merkezinde sunucular sizin adına iletileri kabul eder ve böylece sunucularınız üzerindeki yükü azaltarak, organizasyonuzla İnternet arasında bir ayrım katmanı sağlarlar. Microsoft, bu yüksek kullanılabilir ağ aracılığıyla e-postanın kuruma zamanında ulaşmasına yardımcı olabilir.

EOP, veri merkezleri arasında ancak yalnızca bölge içinde yük dengelemesi yapar. Tek bir bölgede sağlandıysanız, tüm iletileriniz o bölgenin posta yönlendirmesi kullanılarak işlenir.

### <a name="eop-features"></a>EOP özellikleri

Bu bölümde EOP'de kullanılabilen ana özelliklere üst düzey bir genel bakış sağlanmaktadır.

Tüm EOP abonelik planları genelinde gereksinimler, önemli sınırlar ve özellik kullanılabilirliği hakkında bilgi için, aşağıdaki [Exchange Online Protection bakın](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Notlar**:

- EOP, iletilerde bilinen kötü amaçlı bağlantıları algılamaya yardımcı olan çeşitli URL engelleme listeleri kullanır.
- EOP, istenmeyen posta göndermesi bilinen çok geniş bir etki alanı listesi kullanır.
- EOP, birçok kötü amaçlı yazılımdan koruma altyapısı müşterilerimizin her zaman otomatik olarak korunmasına yardımcı olur.
- EOP, ileti gövdesinde etkin yükü ve kötü amaçlı yazılım için tüm ileti eklerini inceler.
- Koruma ilkeleri için önerilen değerler için bkz. [EOP ve Microsoft Defender için önerilen güvenlik Office 365.](recommended-settings-for-eop-and-office365.md)
- Koruma ilkelerini yapılandırmaya yönelik hızlı yönergeler için bkz. [Tehditlere karşı koruma](protect-against-threats.md).

|Özellik|Açıklamalar|
|---|---|
|**Koruma**||
|Kötü amaçlı yazılımdan koruma|[EOP'de kötü amaçlı yazılımdan koruma](anti-malware-protection.md) <p> [Kötü amaçlı yazılımdan koruma hakkında SSS](anti-malware-protection-faq-eop.yml) <p> [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)|
|Gelen istenmeyen posta önleme|[EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md) <p> [İstenmeyen posta koruması hakkında SSS](anti-spam-protection-faq.yml) <p> [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
|Giden İstenmeyen posta önleme|[EOP'de giden istenmeyen posta koruması](outbound-spam-controls.md) <p> [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md) <p> [E-postalarda otomatik dış e-posta iletmeyi Microsoft 365](external-email-forwarding.md)|
|Bağlantı filtreleme|[Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md)|
|Kimlik avı önleme|[E-postada kimlik avı önleme Microsoft 365](set-up-anti-phishing-policies.md) <p> [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)|
|Anti-spoing protection|[EOP'de akıllı Spoof Intelligence içgörü](learn-about-spoof-intelligence.md) <p> [Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md)|
|Teslim edilen kötü amaçlı yazılım, istenmeyen posta ve kimlik avı iletileri için sıfır saatlik otomatik temizleme (ZAP)|[Zap in Exchange Online](zero-hour-auto-purge.md)|
|Önceden belirlenmiş güvenlik ilkeleri|[EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik Office 365](preset-security-policies.md) <p> [EOP'de ve Office 365 için Microsoft Defender'da koruma ilkeleri için yapılandırma çözümleyicisi](configuration-analyzer-for-security-policies.md)|
|Kiracı İzin Ver/Engelleme Listesi|[Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md)|
|İleti gönderenleri için listeleri engelleme|[EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md)|
|İleti gönderenler için listelere izin verme|[EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md)|
|Dizin Tabanlı Kenar Engelleme (DBEB)|[Geçersiz alıcılara gönderilen iletileri reddetmek için Dizin Tabanlı Edge Engellemesi kullanma](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Karantina ve gönderiler**||
|Yönetici gönderimi|[Şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyaları Microsoft'a göndermek için Yönetici gönderimi kullanma](admin-submission.md)|
|Kullanıcı gönderimleri (özel posta kutusu)|[Kullanıcı gönderimleri ilkesi](user-submission.md)|
|Karantina - yöneticiler|[EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme](manage-quarantined-messages-and-files.md) <p> [Karantinaya alınmış iletiler hakkında SSS](quarantine-faq.yml) <p> [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md) <p> [İletide istenmeyen posta önleme ileti Microsoft 365](anti-spam-message-headers.md) <p> İleti Üst Bilgisi Çözümleyicisi'nde karantinaya alınmış iletilerin [ileti üst bilgilerini çözümebilirsiniz](https://mha.azurewebsites.net/).|
|Karantina - son kullanıcılar|[EOP'de kullanıcı olarak karantinaya alınmış iletileri bulma ve serbest bırakma](find-and-release-quarantined-messages-as-a-user.md) <p> [Karantinaya alınmış iletileri serbest bırakmak ve rapor etmek için karantina bildirimlerini kullanma](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Karantina ilkeleri](quarantine-policies.md)|
|**Posta akışı**||
|Posta akış kuralları|[posta akışı kuralları (aktarım kuralları) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [E-postada posta akışı kuralı koşulları ve özel durumları (koşullar) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [E-postada posta akışı Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Posta akış kurallarını aynı adreste Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [E-postada posta akışı kuralı Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Kabul edilen etki alanları|[Etki alanlarında kabul edilen etki alanlarını Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Bağlayıcılar|[E-postada bağlayıcıları kullanarak posta Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Bağlayıcılar için Geliştirilmiş Filtreleme|[E-postada bağlayıcılar için gelişmiş Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**İzleme**||
|İleti izleme|[İleti izleme](message-trace-scc.md) <p> [Exchange yönetim merkezinde ileti izleme](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|E-& işbirliği raporları|[E-posta güvenlik raporlarını görüntüleme](view-email-security-reports.md)|
|Posta akışı raporları|[Posta akışı raporlarını görüntüleme](view-mail-flow-reports.md) <p> [Exchange yönetim merkezinde posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Posta akışı içgörüleri|[Posta akışı içgörüleri](mail-flow-insights-v2.md) <p> [Exchange yönetim merkezinde posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Raporları denetleme|[Exchange yönetim merkezinde raporları denetleme](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Uyarı ilkeleri|[Uyarı ilkeleri](../../compliance/alert-policies.md)|
|**Hizmet Düzeyi Sözleşmeleri (SLA) ve destek**||
|İstenmeyen postaların etkililiği SLA|\> 99%|
|Yanlış pozitif oranı SLA|\< 1:250,000|
|Virüs algılama ve SLA'yı engelleme|Bilinen virüslerin %100'leri|
|Aylık çalışma süresi SLA|99.999%|
|Telefon, web teknik desteği haftanın yedi günü, günde 24 saat|[EOP için yardım ve destek](help-and-support-for-eop.md).|
|**Diğer özellikler**||
|Coğrafi olarak yedekli bir genel sunucu ağı|EOP, en iyi kullanılabilirliği sağlamak için tasarlanmış dünya çapında bir veri merkezleri ağına çalışır. Daha fazla bilgi için, bu [makalenin önceki kısımlarında yer alan EOP](#eop-datacenters) veri merkezleri bölümüne bakın.|
|Şirket içi sunucu posta kabul edilemezken ileti kuyruğa alma|Ertelenen mesajlar bir gün boyunca kuyruklarımızda kalır. İleti yeniden deneme deneme denemeleri, alıcının posta sisteminden geri alınan hataya dayalıdır. İletiler, ortalama olarak her 5 dakikada bir yeniden denenr. Daha fazla bilgi için [EOP sıraya alınan, ertelenmiş ve geri dönen iletiler hakkında SSS bölümüne bakın](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 İleti Şifrelemesi olarak kullanılabilen eklentiler|Daha fazla bilgi için bkz[. Şifreleme Office 365](../../compliance/encryption.md).|
|||
