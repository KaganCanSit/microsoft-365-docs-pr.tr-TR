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
description: Exchange Online Protection (EOP) uygulamasının tek başına ve karma ortamlarda şirket içi e-posta kuruluşunuzu korumaya nasıl yardımcı olabileceğini öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 19bf82a530cd61b253047261bb44893266a240d8
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941577"
---
# <a name="exchange-online-protection-overview"></a>Exchange Online Protection’a genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP), kuruluşunuzu istenmeyen postalara, kötü amaçlı yazılımlara ve diğer e-posta tehditlerine karşı koruyan bulut tabanlı filtreleme hizmetidir. EOP, Exchange Online posta kutularına sahip tüm Microsoft 365 kuruluşlara dahil edilir.

> [!NOTE]
> EOP, şirket içi posta kutularını korumak için tek başına ve şirket içi Exchange posta kutularını korumak için karma ortamlarda da kullanılabilir. Daha fazla bilgi için bkz. [Tek başına Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

EOP güvenlik özelliklerini ayarlama adımları ve Office 365 için Microsoft Defender elde ettiğiniz ek güvenlikle karşılaştırma için bkz. [Tehditlere karşı koruma](protect-against-threats.md). EOP özellikleri için önerilen ayarlar, [EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar](recommended-settings-for-eop-and-office365.md) bölümünde bulunur.

Bu makalenin geri kalanında EOP'nin nasıl çalıştığı ve EOP'de kullanılabilen özellikler açıklanmaktadır.

## <a name="how-eop-works"></a>EOP nasıl çalışır?

EOP'nin nasıl çalıştığını anlamak için gelen e-postayı nasıl işlediğini görmenize yardımcı olur:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Gereksiz posta veya karantina ya da son kullanıcı posta teslimi kararından önce İnternet'ten veya Müşteri geri bildiriminin EOP'ye ve Bağlantı, Kötü Amaçlı Yazılımdan Koruma, Posta Akışı Kuralları-Eğik Çizgi-İlke Filtreleme ve İçerik Filtreleme yoluyla iletilmesine ilişkin e-posta grafiği" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. Gelen bir ileti EOP'ye girdiğinde, başlangıçta gönderenin itibarını denetleyen bağlantı filtrelemesinden geçer. İstenmeyen postaların çoğu bu noktada durdurulur ve EOP tarafından reddedilir. Daha fazla bilgi için bkz. [Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).

2. Ardından ileti kötü amaçlı yazılım olup olmadığını denetler. İletide veya eklerde kötü amaçlı yazılım bulunursa, ileti karantinaya teslim edilir. Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım karantinaya alınan iletileri görüntüleyebilir ve bunlarla etkileşimde bulunabilir. Ancak, yöneticiler [kullanıcıların karantinaya](quarantine-policies.md) alınan iletilere ne yapmalarına izin verileceğini belirtmek için karantina ilkeleri oluşturabilir ve kullanabilir. Kötü amaçlı yazılım koruması hakkında daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma](anti-malware-protection.md).

3. İleti, oluşturduğunuz posta akışı kurallarına (aktarım kuralları olarak da bilinir) göre değerlendirildiği ilke filtrelemesi boyunca devam eder. Örneğin, bir kural belirli bir gönderenden bir ileti geldiğinde yöneticiye bildirim gönderebilir.

   Hizmet lisanslarına sahip Exchange Enterprise CAL ile şirket içi kuruluşta, EOP'deki [Microsoft Purview veri kaybı önleme (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) denetimleri de bu noktada gerçekleşir.

4. İleti, zararlı iletilerin istenmeyen posta, yüksek güvenilirlikli istenmeyen posta, kimlik avı, yüksek güvenilirlikli kimlik avı veya toplu (istenmeyen posta önleme ilkeleri) veya kimlik sahtekarlığı (kimlik avı önleme ilkelerindeki kimlik sahtekarlığı ayarları) olarak tanımlandığı içerik filtrelemesinden (istenmeyen posta önleme ve kimlik sahtekarlığı önleme) geçer. Filtreleme kararına (karantinaya alma, Gereksiz E-posta klasörüne gitme vb.) ve kullanıcıların karantinaya alınan iletilere [karantina ilkelerini](quarantine-policies.md) kullanarak yapabileceklerine bağlı olarak iletiyi gerçekleştirecek eylemi yapılandırabilirsiniz. Daha fazla bilgi için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md) ve [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

Bu koruma katmanlarının tümünü başarıyla geçiren bir ileti alıcılara teslim edilir.

Daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>EOP veri merkezleri

EOP, en iyi kullanılabilirliği sağlamak için tasarlanmış dünya çapındaki veri merkezlerinden oluşan bir ağda çalışır. Örneğin, bir veri merkezi kullanılamaz duruma gelirse, e-posta iletileri hizmette herhangi bir kesinti olmadan otomatik olarak başka bir veri merkezine yönlendirilir. Her veri merkezinde sunucular sizin adınıza iletileri kabul eder ve kuruluşunuzla İnternet arasında bir ayrım katmanı sağlayarak sunucularınızdaki yükü azaltır. Bu yüksek oranda kullanılabilir ağ aracılığıyla Microsoft, e-postanın kuruluşunuza zamanında ulaşmasını sağlayabilir.

EOP, veri merkezleri arasında ancak yalnızca bir bölge içinde yük dengeleme gerçekleştirir. Tek bir bölgede sağlandıysanız, tüm iletileriniz o bölge için posta yönlendirmesi kullanılarak işlenir.

### <a name="eop-features"></a>EOP özellikleri

Bu bölüm, EOP'de kullanılabilen ana özelliklere üst düzey bir genel bakış sağlar.

Tüm EOP abonelik planlarının gereksinimleri, önemli sınırları ve özellik kullanılabilirliği hakkında bilgi için [Exchange Online Protection hizmet açıklamasına](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) bakın.

**Notlar**:

- EOP, iletilerde bilinen kötü amaçlı bağlantıları algılamaya yardımcı olan çeşitli URL blok listeleri kullanır.
- EOP, istenmeyen posta gönderdiği bilinen etki alanlarının geniş bir listesini kullanır.
- EOP, müşterilerimizin her zaman otomatik olarak korunmasına yardımcı olan birden çok kötü amaçlı yazılımdan koruma altyapısı kullanır.
- EOP, ileti gövdesindeki etkin yükü ve kötü amaçlı yazılım için tüm ileti eklerini inceler.
- Koruma ilkeleri için önerilen değerler için bkz. [EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar](recommended-settings-for-eop-and-office365.md).
- Koruma ilkelerini yapılandırmaya yönelik hızlı yönergeler için bkz. [Tehditlere karşı koruma](protect-against-threats.md).

|Özellik|Açıklamalar|
|---|---|
|**Koruma**||
|Kötü amaçlı yazılımdan koruma|[EOP'de kötü amaçlı yazılımdan koruma](anti-malware-protection.md) <p> [Kötü amaçlı yazılımdan koruma SSS](anti-malware-protection-faq-eop.yml) <p> [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)|
|Gelen istenmeyen posta önleme|[EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md) <p> [İstenmeyen posta önleme SSS](anti-spam-protection-faq.yml) <p> [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
|Giden istenmeyen posta önleme|[EOP'de giden istenmeyen posta koruması](outbound-spam-controls.md) <p> [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md) <p> [Microsoft 365'de otomatik dış e-posta iletmeyi denetleme](external-email-forwarding.md)|
|Bağlantı filtreleme|[Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md)|
|Kimlik avına karşı koruma|[Microsoft 365'de kimlik avı önleme ilkeleri](set-up-anti-phishing-policies.md) <p> [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)|
|Kimlik sahtekarlığına karşı koruma|[EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md) <p> [Kiracı İzin Verilenler/Engellenenler Listesini Yönetme](tenant-allow-block-list.md)|
|Teslim edilen kötü amaçlı yazılım, istenmeyen posta ve kimlik avı iletileri için sıfır saatlik otomatik temizleme (ZAP)|[Exchange Online'de ZAP](zero-hour-auto-purge.md)|
|Önceden ayarlanmış güvenlik ilkeleri|[EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik ilkeleri](preset-security-policies.md) <p> [EOP ve Office 365 için Microsoft Defender koruma ilkeleri için yapılandırma çözümleyicisi](configuration-analyzer-for-security-policies.md)|
|Kiracı İzin Verilenler/Engellenenler Listesi|[Kiracı İzin Verilenler/Engellenenler Listesini Yönetme](tenant-allow-block-list.md)|
|İleti gönderenler için listeleri engelleme|[EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md)|
|İleti gönderenler için listelere izin ver|[EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md)|
|Dizin Tabanlı Kenar Engelleme (DBEB)|[Geçersiz alıcılara gönderilen iletileri reddetmek için Dizin Tabanlı Uç Engelleme'yi kullanma](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Karantina ve gönderimler**||
|Yönetici gönderimi|[Şüpheli istenmeyen postaları, kimlik avı, URL'leri ve dosyaları Microsoft'a göndermek için Yönetici gönderimini kullanma](admin-submission.md)|
|Kullanıcı gönderimleri (özel posta kutusu)|[Kullanıcı gönderimleri ilkesi](user-submission.md)|
|Karantina - yöneticiler|[Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme](manage-quarantined-messages-and-files.md) <p> [Karantinaya alınan iletiler hakkında SSS](quarantine-faq.yml) <p> [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md) <p> [Microsoft 365'da istenmeyen postadan koruma iletisi üst bilgileri](anti-spam-message-headers.md) <p> konumundaki [İleti Üst Bilgisi Çözümleyicisi'ni](https://mha.azurewebsites.net/) kullanarak karantinaya alınan iletilerin ileti üst bilgilerini analiz edebilirsiniz.|
|Karantina - son kullanıcılar|[Karantinaya alınan iletileri EOP'de kullanıcı olarak bulma ve bırakma](find-and-release-quarantined-messages-as-a-user.md) <p> [Karantinaya alınan iletileri serbest bırakmak ve bildirmek için karantina bildirimlerini kullanma](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Karantina ilkeleri](quarantine-policies.md)|
|**Posta akışı**||
|Posta akışı kuralları|[Exchange Online'da posta akışı kuralları (aktarım kuralları)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Exchange Online'da posta akışı kuralı koşulları ve özel durumlar (koşullar)](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Exchange Online'de posta akışı kuralı eylemleri](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Exchange Online'de posta akışı kurallarını yönetme](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Exchange Online'de posta akışı kuralı yordamları](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Kabul edilen etki alanları|[Exchange Online'de kabul edilen etki alanlarını yönetme](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Bağlayıcı|[Exchange Online'de bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Bağlayıcılar için Gelişmiş Filtreleme|[Exchange Online'de bağlayıcılar için gelişmiş filtreleme](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Izleme**||
|İleti izleme|[İleti izleme](message-trace-scc.md) <p> [Exchange yönetim merkezinde ileti izleme](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|E-posta & işbirliği raporları|[E-posta güvenlik raporlarını görüntüleme](view-email-security-reports.md)|
|Posta akışı raporları|[Posta akışı raporlarını görüntüleme](view-mail-flow-reports.md) <p> [Exchange yönetim merkezinde posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Posta akışı içgörüleri|[Posta akışı içgörüleri](mail-flow-insights-v2.md) <p> [Exchange yönetim merkezinde posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Denetim raporları|[Exchange yönetim merkezinde raporları denetleme](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Uyarı ilkeleri|[Uyarı ilkeleri](../../compliance/alert-policies.md)|
|**Hizmet Düzeyi Sözleşmeleri (SLA' lar) ve destek**||
|İstenmeyen posta etkinliği SLA'sı|\> 99%|
|Hatalı pozitif oran SLA'sı|\< 1:250,000|
|Virüs algılama ve engelleme SLA'sı|Bilinen virüslerin %100'ünün|
|Aylık çalışma süresi SLA'sı|99.999%|
|haftanın yedi günü, günde 24 saat Telefon ve web teknik desteği|[EOP için yardım ve destek](help-and-support-for-eop.md).|
|**Diğer özellikler**||
|Coğrafi olarak yedekli bir sunucu genel ağı|EOP, en iyi kullanılabilirliği sağlamaya yardımcı olmak için tasarlanmış dünya çapında bir veri merkezleri ağında çalışır. Daha fazla bilgi için bu makalenin önceki bölümlerinde yer alan [EOP veri merkezleri](#eop-datacenters) bölümüne bakın.|
|Şirket içi sunucu postayı kabul edemediğinde ileti kuyruğa alma|Ertelenmiş iletiler bir gün boyunca kuyruklarımızda kalır. İleti yeniden deneme girişimleri, alıcının posta sisteminden aldığımız hataya dayanır. İletiler ortalama olarak 5 dakikada bir yeniden deneniyor. Daha fazla bilgi için bkz. [EOP kuyruğa alındı, ertelendi ve geri dönen iletiler hakkında SSS](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 İleti Şifrelemesi eklenti olarak kullanılabilir|Daha fazla bilgi için bkz[. Office 365'de şifreleme](../../compliance/encryption.md).|
|||
