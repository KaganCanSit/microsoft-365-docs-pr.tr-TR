---
title: Office 365 için Microsoft Defender değerlendirme
description: Değerlendirme modundaki Office 365 için Defender, kötü amaçlı yazılım gibi kararların günlüğe kaydedildiği ancak iletilerde işlem yapmaması için Office 365 için Defender e-posta ilkeleri oluşturur.
keywords: Office 365, Office 365 için Microsoft Defender, office 365 değerlendirmesini değerlendirin, office 365, Microsoft Defender'ı deneyin Uç Nokta için Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f5d82e9baaca7209f8a91a7f1984aa38e3102e6
ms.sourcegitcommit: 74518b920b4166adccc10ea1581a62c44bb14edb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738759"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender değerlendirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Office 365 için Microsoft Defender değerlendirme genel önizleme aşamasındadır. Bu önizleme sürümü hizmet düzeyi sözleşmesi olmadan sağlanır. Bazı özellikler desteklenmeyebilir veya sınırlı özelliklere sahip olabilir.

Kapsamlı bir güvenlik ürünü değerlendirmesi yapmak, yükseltmeler ve satın almalar hakkında bilinçli kararlar vermenize yardımcı olabilir. Güvenlik operasyon ekibinizin günlük görevlerinde nasıl yardımcı olabileceğini değerlendirmek için güvenlik ürününün özelliklerini denemenize yardımcı olur.

[Office 365 için Microsoft Defender](defender-for-office-365.md) değerlendirme deneyimi, Office 365 için Microsoft Defender özelliklerini değerlendirmeye odaklanabilmeniz için cihaz ve ortam yapılandırmasının karmaşıklıklarını ortadan kaldıracak şekilde tasarlanmıştır. Değerlendirme modunda, Exchange Online posta kutularına gönderilen tüm iletiler MX kayıtlarını Microsoft'a işaret etmeden değerlendirilebilir. Bu özellik yalnızca e-posta koruması için geçerlidir ve Word, SharePoint veya Teams gibi İstemcileri Office için geçerli değildir.

Office 365 için Microsoft Defender destekleyen bir lisansınız yoksa, [30 günlük ücretsiz bir değerlendirme](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) başlatabilir ve Microsoft 365 Defender portalındaki özellikleri adresinden <https://security.microsoft.com>test edebilirsiniz. Hızlı kurulumdan keyif alırsınız ve gerekirse kolayca kapatabilirsiniz.

> [!NOTE]
> adresinde Microsoft 365 Defender portalındaysanız<https://security.microsoft.com>, burada bir Office 365 için Defender değerlendirmesi başlatabilirsiniz: **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Değerlendirme modu**. Veya doğrudan **Değerlendirme modu** sayfasına gitmek için kullanın <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Değerlendirme nasıl çalışır?

Değerlendirme modundaki Office 365 için Defender, kötü amaçlı yazılım gibi kararların günlüğe kaydedildiği ancak iletilerde işlem yapmaması için Office 365 için Defender e-posta ilkeleri oluşturur. MX kaydı yapılandırmanızı değiştirmeniz gerekmez.

Değerlendirme moduyla, [Kasa Ekler](safe-attachments.md), [Kasa Bağlantıları](safe-links.md) ve [hazırlamayı önleme ilkelerindeki posta kutusu zekası](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) sizin adınıza ayarlanır. Tüm Office 365 için Defender ilkeleri arka planda zorlama modunda oluşturulur ve sizin için görünmez.

Kurulumun bir parçası olarak, değerlendirme modu [Bağlayıcılar için Gelişmiş Filtreleme'yi de yapılandırıyor](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) ( _atlama listesi_ olarak da bilinir). Bu yapılandırma, IP adresini ve gönderen bilgilerini koruyarak filtreleme doğruluğunu artırır. Bu bilgiler, posta Office 365 için Defender önünden bir e-posta güvenlik ağ geçidinden (ESG) geçtiğinde kaybolur. Bağlayıcılar için Gelişmiş Filtreleme, mevcut Exchange Online Protection (EOP) istenmeyen posta önleme ve kimlik avı önleme ilkelerinizin filtreleme doğruluğunu da artırır.

Bağlayıcılar için Gelişmiş Filtreleme, filtreleme doğruluğunu artırır ancak Office 365 için Defender önünde bir ESG'niz varsa ve şu anda EOP filtrelemesini atlamıyorsanız belirli iletiler için teslim edilebilirliği değiştirebilir. Etki EOP ilkeleriyle sınırlıdır; Değerlendirmenin bir parçası olarak ayarlanan Office 365 için Defender ilkeleri, zorlama modunda oluşturulur. Olası üretim etkisini en aza indirmek için, iletilerin istenmeyen posta güvenilirlik düzeyini (SCL) -1 olarak ayarlamak üzere bir posta akışı kuralı (aktarım kuralı olarak da bilinir) oluşturarak çoğu EOP filtrelemesini atlayabilirsiniz. Ayrıntılar için bkz. [Exchange Online iletilerde istenmeyen posta güvenilirlik düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Değerlendirme modu ayarlandığında, ilkeler uygulandığında engellenecek iletileri (örneğin silme, gereksiz postaya gönderme, karantina) belirten 90 güne kadar veri içeren günlük bir raporunuz olur. Tüm Office 365 için Defender ve EOP algılamaları için raporlar oluşturulur. Raporlar algılama teknolojisi başına toplanır (örneğin, kimliğe bürünme) ve zaman aralığına göre filtrelenebilir. Ayrıca, özel özetler oluşturmak veya Gezgin'i kullanarak iletileri ayrıntılı olarak incelemek için isteğe bağlı olarak ileti raporları oluşturulabilir.

Basitleştirilmiş kurulum deneyimiyle aşağıdakilere odaklanabilirsiniz:

- Değerlendirmeyi çalıştırma
- Ayrıntılı rapor alma
- Raporu eylem için analiz etme
- Değerlendirme sonucunu sunma

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="licensing"></a>Lisanslama

Değerlendirmeye erişmek için lisans gereksinimlerini karşılamanız gerekir. Aşağıdaki lisanslardan herhangi biri çalışır:

- Office 365 için Microsoft Defender Plan 1
- Office 365 için Microsoft Defender Plan 2
- Microsoft 365 E5, Microsoft 365 E5 Güvenlik
- Office 365 E5

Bu lisanslardan birine sahip değilseniz deneme lisansı almanız gerekir.

#### <a name="trial"></a>Deneme

Office 365 için Microsoft Defender için deneme lisansı almak için **Faturalama yöneticisi rolüne** veya **Genel yönetici rolüne** sahip olmanız gerekir. Genel yönetici rolüne sahip birinden izin isteyin. [Abonelikler ve lisanslar hakkında bilgi edinin](../../commerce/licenses/subscriptions-and-licenses.md)

Uygun role sahip olduktan sonra, önerilen yol konumundaki Microsoft 365 yönetim merkezi Office 365 için Microsoft Defender (Plan 2) <https://admin.microsoft.com> için bir deneme lisansı almak ve ardından **Faturalama** \> **Satın Alma hizmetleri'ne** gidip Office 365 için Microsoft Defender (Plan 2) deneme sürümü. Ya da doğrudan deneme sayfasına gitmek için Deneme sürümü 25 lisans için 30 günlük ücretsiz deneme sürümünü içerir'i kullanın <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> .

Gelişmiş tehditleri izlemek ve raporlamak için değerlendirmeyi içeren 30 günlük bir süreniz olacak. Tam Office 365 için Defender özellikleri istiyorsanız ücretli abonelik satın alma seçeneğiniz de vardır.

### <a name="roles"></a>Rolleri

**değerlendirme modunda Office 365 için Defender** ayarlamak için Exchange Online rolleri gereklidir. Microsoft 365 uyumluluk veya güvenlik yöneticisi rolü atamak işe yaramaz.

- [Exchange Online'de izinler hakkında bilgi edinin](/exchange/permissions-exo/permissions-exo)
- [Yönetici rolleri atama hakkında bilgi edinin](../../admin/add-users/assign-admin-roles.md)

Aşağıdaki roller gereklidir:

|Görev|Rol (Exchange Online)|
|---|---|
|Ücretsiz deneme sürümü edinin veya Office 365 için Microsoft Defender satın alın (Plan 2)|Faturalama yöneticisi rolü VEYA Genel yönetici rolü|
|Değerlendirme ilkesi oluşturma|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü|
|Değerlendirme ilkesini düzenleme|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü|
|Değerlendirme ilkesini silme|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü |
|Değerlendirme raporunu görüntüleme|Güvenlik yöneticisi rolü VEYA Güvenlik okuyucusu rolü|

### <a name="enhanced-filtering-for-connectors"></a>Bağlayıcılar için Gelişmiş Filtreleme

Toplu ve istenmeyen posta koruması gibi Exchange Online Protection ilkeleriniz aynı kalır. Ancak, değerlendirme Bağlayıcılar için Gelişmiş Filtreleme özelliğini açar ve bu da atlanmadığı sürece posta akışınızı ve Exchange Online Protection ilkelerinizi etkileyebilir.

Bağlayıcılar için Gelişmiş Filtreleme, kiracıların kimlik sahtekarlığı önleme koruması kullanmasına olanak tanır. Bağlayıcılar için Gelişmiş Filtreleme'yi açmadan bir e-posta güvenlik ağ geçidi (ESG) kullanıyorsanız kimlik sahtekarlığı önleme desteklenmez.

### <a name="urls"></a>Url 'leri

URL'ler posta akışı sırasında patlatılır. Belirli URL'lerin açılmasını istemiyorsanız, izin verilen URL'ler listenizi uygun şekilde yönetin. Ayrıntılar için bkz. [Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md) .

E-posta iletisi gövdelerindeki URL bağlantıları, müşteri etkisini azaltmak için sarmalamaz.

### <a name="email-routing"></a>E-posta yönlendirme

E-postanızı yönlendiren gelen bağlayıcının adı da dahil olmak üzere, e-postanızın şu anda nasıl yönlendirildiğini ayarlamanız için gereken ilgili ayrıntıları hazırlayın. Yalnızca Exchange Online Protection kullanıyorsanız bağlayıcınız olmaz. [Posta akışı ve e-posta yönlendirme hakkında bilgi edinin](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Desteklenen e-posta yönlendirme senaryoları şunlardır:

- **Üçüncü taraf iş ortağı ve/veya şirket içi hizmet sağlayıcısı**: Değerlendirmek istediğiniz gelen bağlayıcı bir üçüncü taraf sağlayıcı kullanır ve/veya şirket içi e-posta güvenliği için bir çözüm kullanıyorsunuz.
- **Yalnızca Microsoft Exchange Online Koruması**: Değerlendirmek istediğiniz kiracı, e-posta güvenliği için Office 365 kullanır ve Posta Exchange (MX) kaydı Microsoft'u gösterir.

### <a name="email-security-gateway"></a>E-posta güvenlik ağ geçidi

Üçüncü taraf e-posta güvenlik ağ geçidi (ESG) kullanıyorsanız sağlayıcının adını bilmeniz gerekir. Şirket içi ESG veya desteklenmeyen satıcılar kullanıyorsanız, cihazların genel IP adreslerini bilmeniz gerekir.

Desteklenen üçüncü taraf iş ortakları şunlardır:

- Barracuda
- IronPort
- Mimecast
- Yazım Denetleme Noktası
- Sophos
- Symantec
- Trend Micro

### <a name="scoping"></a>Kapsam

Değerlendirmenin kapsamını bir gelen bağlayıcıya göre ayarlayabileceksiniz. Yapılandırılmış bağlayıcı yoksa, değerlendirme kapsamı yöneticilerin Office 365 için Defender değerlendirmek için kiracınızdaki herhangi bir kullanıcıdan veri toplamasına olanak tanır.

## <a name="get-started-with-the-evaluation"></a>Değerlendirmeyle Kullanmaya başlayın

Microsoft 365 Defender portalında aşağıdaki erişim noktalarından Office 365 için Microsoft Defender değerlendirme kurulum kartını bulun:

- **Bitiş noktası** \> **Güvenlik Açığı Yönetimi** \> **Pano** (<https://security.microsoft.com/tvm_dashboard>)
- **E-posta & işbirliği** \> **İlkeler & kuralları** \> **Tehdit ilkeleri** (<https://security.microsoft.com/threatpolicy>)
- **Rapor** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Değerlendirmeyi ayarlama

Değerlendirmeniz için kurulum akışını başlattıktan sonra iki yönlendirme seçeneği sunulur. Kuruluşunuzun posta yönlendirme kurulumuna ve değerlendirme gereksinimlerine bağlı olarak, üçüncü taraf ve/veya şirket içi hizmet sağlayıcısı mı kullandığınızı yoksa yalnızca Microsoft Exchange Online mi kullandığınızı seçebilirsiniz.

- Üçüncü taraf bir iş ortağı ve/veya şirket içi hizmet sağlayıcısı kullanıyorsanız, açılan menüden satıcının adını seçmeniz gerekir. Bağlayıcıyla ilgili diğer ayrıntıları sağlayın.

- MX kaydı Microsoft'u işaret ederse ve bir **Exchange Online** posta kutunuz varsa Microsoft Exchange Online'ı seçin.

Ayarlarınızı gözden geçirin ve gerekirse düzenleyin. Ardından **Değerlendirme oluştur'u** seçin. Kurulumunuzun tamamlandığını belirten bir onay iletisi almalısınız.

Office 365 için Microsoft Defender değerlendirme raporunuz günde bir kez oluşturulur. Verilerin doldurulmaları 24 saat kadar sürebilir.

### <a name="exchange-mail-flow-rules-optional"></a>posta akışı kurallarını Exchange (isteğe bağlı)

Mevcut bir ağ geçidiniz varsa, değerlendirme modunun etkinleştirilmesi Bağlayıcılar için Gelişmiş Filtreleme'yi etkinleştirir. Bu özellik, gelen gönderen IP adresini değiştirerek filtreleme doğruluğunu artırır. Bu özellik filtre kararlarını değiştirebilir ve Exchange Online Protection atlamıyorsanız bu, belirli iletiler için teslim edilebilirliği değiştirebilir. Bu durumda, etkiyi analiz etmek için filtrelemeyi geçici olarak atlamak isteyebilirsiniz. Filtrelemeyi atlamak için, Exchange yönetim merkezinde (EAC) ileti SCL'sini -1 olarak ayarlayan bir posta akışı kuralı (aktarım kuralı olarak da bilinir) <https://admin.exchange.microsoft.com/#/transportrules> oluşturun (henüz yoksa). Yönergeler için bkz. [Exchange Online iletilerde istenmeyen posta güvenilirlik düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Özellikleri değerlendirin

Değerlendirme raporu oluşturulduktan sonra, kuruluşunuzdaki e-postalarda ve işbirliği çalışma alanlarında kaç gelişmiş tehdit bağlantısı, gelişmiş tehdit eki ve olası kimliğe bürünme tanımlandığını görün.

Deneme süresi dolduktan sonra rapora 90 gün boyunca erişmeye devam edebilirsiniz. Ancak, daha fazla bilgi toplamaz. Deneme süreniz dolduktan sonra Office 365 için Microsoft Defender kullanmaya devam etmek istiyorsanız, [Office 365 için Microsoft Defender (Plan 2) için ücretli bir abonelik satın](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) almayı unutmayın.

yönlendirmenizi güncelleştirmek veya değerlendirmenizi istediğiniz zaman kapatmak için **Ayarlar** gidebilirsiniz. Ancak, değerlendirmenizi kapattıktan sonra devam etmeye karar vermeniz durumunda aynı kurulum işlemini yeniden gerçekleştirmeniz gerekir.

## <a name="provide-feedback"></a>Geri bildirim gönderin

Geri bildiriminiz, ortamınızı gelişmiş saldırılara karşı koruma konusunda daha iyi olmamıza yardımcı olur. Ürün özellikleri ve değerlendirme sonuçlarıyla ilgili deneyiminizi ve izlenimlerinizi paylaşın.

Düşüncelerinizi bize bildirmek için **Geri bildirim gönder'i** seçin.
