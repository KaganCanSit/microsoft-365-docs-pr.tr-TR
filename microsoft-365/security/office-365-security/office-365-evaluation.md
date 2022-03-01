---
title: Microsoft Defender'ı Office 365
description: Değerlendirme modunda Office 365 için Defender, kötü amaçlı yazılım gibi kararları günlüğe alan ancak iletilere yönelik Office 365 ilkeler için Defender'ı oluşturur.
keywords: değerlendirme Office 365, Office 365 için Microsoft Defender, Office 365 değerlendirme, Office 365, Microsoft Defender, Uç Nokta için Microsoft Defender'ı deneyin
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
ms.openlocfilehash: 7a00dc92383e71d105faf0975468e47bc38ed60e
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2022
ms.locfileid: "63016301"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Microsoft Defender'ı Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Değerlendirme için Microsoft Defender Office 365 genel önizlemede. Bu önizleme sürümü, hizmet düzeyi sözleşmesi olmadan sağlanır. Bazı özellikler desteklenmiyor veya kısıtlı özelliklere sahip olabilir.

Kapsamlı bir güvenlik ürünü değerlendirmesini yapmak, yükseltmeler ve satın almalar hakkında bilinçli kararlar adedi verebilirsiniz. Güvenlik ürünü özelliklerini denemek, güvenlik işlemleri takımınıza günlük görevlerinde nasıl yardımcı olduğunu değerlendirmek için yardımcı olur.

Office 365 [için Microsoft Defender](defender-for-office-365.md) değerlendirme deneyimi, cihaz ve ortam yapılandırmasının karmaşıklıklarını ortadan kaldıracak şekilde tasarlanmıştır; böylece siz de bu deneyimin için Microsoft Defender'ın özelliklerini Office 365. Değerlendirme moduyla, posta kutularına Exchange Online tüm iletiler MX kayıtları Microsoft'a işaret etmeden değerlendirilir. Bu özellik yalnızca e-posta koruması için geçerlidir; Word Office, SharePoint veya Teams.

Henüz Office 365 için Microsoft Defender'ı destekleyen bir lisansınız yoksa, [ücretsiz bir 30](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) günlük değerlendirme başlatabilirsiniz ve Microsoft 365 Defender portalında özellikleri test edebilirsiniz<https://security.microsoft.com>. Hızlı ayarlamanın keyfini çıkarabilirsiniz ve gerekirse kolayca kapatabilirsiniz.

> [!NOTE]
> Microsoft 365 Defender portalında <https://security.microsoft.com>isanız, Office 365 için Defender değerlendirmesini buradan başlatabilirsiniz: E-posta **&** \> İşbirliği İlkeleri **ve** \>  \> Diğer & bölümünde Kuralları Tehdit İlkeleri **Değerlendirme modu.**  Veya doğrudan Değerlendirme modu **sayfasına gitmek için** kullanın <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Değerlendirme nasıl çalışır?

Değerlendirme modunda Office 365 için Defender, kötü amaçlı yazılım gibi kararları günlüğe alan ancak iletilere yönelik Office 365 ilkeler için Defender'ı oluşturur. MX kaydı yapılandırmanızı değiştirmeniz gerekmez.

Değerlendirme moduyla, [Kasa](safe-attachments.md), [Posta Kasa'ne](safe-links.md) tıklayın ve posta kutusu zekası ile koruma [](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ilkeleri sizin adına ayarlanır. Uygulama için Office 365 Defender ilkeleri arka planda zorlama olmayan modda oluşturulur ve sizin için görünmez.

Kurulum kapsamında, değerlendirme modu Bağlayıcılar için Geliştirilmiş Filtreleme'yi [de](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) yapılandırarak (liste atlama olarak da _bilinir_). Bu yapılandırma, posta güvenlik ağ geçidinde (ESG) bir e-posta güvenlik ağ geçididen (ESG) geçtiğinde kaybolan IP adresi ve gönderen bilgilerini koruyarak filtreleme doğruluğunu Office 365. Bağlayıcılar için İyileştirilmiş Filtreleme, mevcut istenmeyen posta (EOP) istenmeyen posta önleme ve kimlik avı ilkeleriniz için Exchange Online Protection doğruluk oranı da geliştirmektedir.

Bağlayıcılar için İyileştirilmiş Filtreleme, filtreleme doğruluğunu geliştirse de, Office 365 için Defender'ın önünde bir ESG'niz varsa ve şu anda EOP filtrelemesini atladıysanız, bazı iletiler için teslim edilebilirliği değiştirebilir. Bu etki EOP ilkeleriyle sınırlıdır; Değerlendirmenin Office 365 için Defender uygulaması, zorlama olmayan modda oluşturulur. Olası üretim etkisini en aza indirmek için, iletilerin istenmeyen posta güven düzeyini (SCL) -1 olarak ayarlamak üzere bir posta akış kuralı (aktarım kuralı olarak da bilinir) oluşturarak EOP filtrelemelerinin çoğunu atabilirsiniz. Ayrıntılar [için bkz. E-posta iletilerinde istenmeyen posta güven düzeyini (SCL) ayarlamak Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) kuralları kullanma.

Değerlendirme modu ayarlanıyorsa, ilkeler uygulanırsa engellenmiş iletilerin nicelik ölçülerini belirten 90 günlük veri (örneğin, sil, gereksize gönder, karantinaya gönder) günlük bir raporunuz olur. Tüm Defender for Office 365 EOP algılamaları için raporlar oluşturulur. Raporlar algılama teknolojisine göre (örneğin kimliğe bürünme) göre toplanır ve zaman aralığına göre filtre uygulama. Buna ek olarak, ileti raporları özel özetler oluşturmak veya Explorer'ı kullanarak iletileri derinden daldıracak şekilde isteğe bağlı olarak oluşturulabilir.

Basitleştirilmiş ayarlama deneyimiyle, aşağıdakilere odaklanabilirsiniz:

- Değerlendirmeyi çalıştırma
- Ayrıntılı rapor alma
- Raporu eylem için çözümleme
- Değerlendirme sonucunu sunumlama

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="licensing"></a>Lisanslama

Değerlendirmeye erişmek için lisans gereksinimlerini karşılamanız gerekir. Aşağıdaki lisanslardan herhangi biri çalışır:

- Office 365 için Microsoft Defender Plan 1
- Office 365 için Microsoft Defender Plan 2
- Microsoft 365 E5, Microsoft 365 E5 Güvenlik
- Office 365 E5

Bu lisanslardan biri yoksa deneme lisansı alınız gerekir.

#### <a name="trial"></a>Deneme

Office 365 için Microsoft Defender'ın deneme lisansı almak için Faturalama yöneticisi rolüne veya **Genel** yönetici **rolüne sahip olmak gerekir**. Genel yönetici rolüne sahip bir kişiden izin isteğinde bulundur. [Abonelikler ve lisanslar hakkında bilgi edinin](../../commerce/licenses/subscriptions-and-licenses.md)

Uygun role sahip olduktan sonra önerilen yol, Microsoft 365 yönetim merkezi'ta Office 365 için Microsoft Defender (Plan 2) <https://admin.microsoft.com>  \> deneme lisansı almak ve ardından Fatura Satın Alma hizmetleri'ne gidip Office 365 (Plan 2) için Microsoft Defender denemesini bulup seçmektir. Doğrudan deneme sayfasına gitmek için de Bu deneme, <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> 25 lisans için 30 günlük ücretsiz bir deneme içerir.

30 günlük bir pencerede gelişmiş tehditlere karşı izleme ve raporu değerlendirme gerekir. Ayrıca, ücretli abonelik satın alma seçeneğiniz de vardır. Bu özellikler için Defender'ın tamamını Office 365 edinebilirsiniz.

### <a name="roles"></a>Roller

**Exchange Online için** Defender'ı değerlendirme modunda Office 365 için farklı roller gereklidir. Uyumluluk Microsoft 365 güvenlik yöneticisi rolü atama işe yaramadı.

- [E-Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Yönetici rollerini atama hakkında bilgi](../../admin/add-users/assign-admin-roles.md)

Aşağıdaki roller gereklidir:

<br>

****

|Görev|Rol (Exchange Online)|
|---|---|
|Ücretsiz denemeyi alın veya Office 365 için Microsoft Defender'ı (Plan 2) satın alın|Faturalama yöneticisi rolü VEYA Genel yönetici rolü|
|Değerlendirme ilkesi oluşturma|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü|
|Değerlendirme ilkesi düzenleme|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü|
|Değerlendirme ilkesi silme|Uzak ve Kabul Edilen Etki Alanları rolü; Güvenlik yöneticisi rolü |
|Değerlendirme raporunu görüntüleme|Güvenlik yöneticisi rolü VEYA Güvenlik okuyucusu rolü|
|

### <a name="enhanced-filtering-for-connectors"></a>Bağlayıcılar için Geliştirilmiş Filtreleme

Toplu Exchange Online Protection istenmeyen posta koruması gibi önemli ilkeleriniz aynı kalacaktır. Ancak değerlendirme, posta akışınızı ve posta ilkelerinizi etkileyebilirsiniz ve bu da at atlamadıkça Exchange Online Protection sağlar.

Bağlayıcılar için İyileştirilmiş Filtreleme, kiracılarınpoing korumasını kullanmasına olanak sağlar. Bağlayıcılar için Geliştirilmiş Filtreleme'yi açık yapmadan e-posta güvenliği ağ geçidi (ESG) kullanıyorsanız, izinsiz giriş önleme kullanılamaz.

### <a name="urls"></a>URL'ler

Posta akışı sırasında URL'ler detone olur. Belirli URL'lerin detonlu olması istemiyorsanız, izin verilen URL'ler listenizi doğru yönetin. Ayrıntılar [için bkz. Kiracı İzin Verme/Engelleme](tenant-allow-block-list.md) Listesini Yönetme.

E-posta ileti gövdesinde yer alan URL bağlantıları, müşterinin etkisini daha az etkiler.

### <a name="email-routing"></a>E-posta yönlendirme

Postanızı yönlendiren gelen bağlayıcının adı da içinde olmak üzere, e-postanıza ilişkin geçerli rotayı ayarlamak için gereken ilgili ayrıntıları hazırlayın. Yalnızca Başka bir Exchange Online Protection kullanıyorsanız, bağlayıcıya sahip olmayacaksanız. [Posta akışı ve e-posta yönlendirme hakkında bilgi alın](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Desteklenen e-posta yönlendirme senaryoları şunlardır:

- **Üçüncü taraf iş** ortağı ve/veya şirket içi hizmet sağlayıcısı: Değerlendirmek istediğiniz gelen bağlayıcısı üçüncü taraf bir sağlayıcı kullanır ve/veya şirket içi e-posta güvenliği için bir çözüm kullanıyorsanız.
- **Microsoft Exchange Online Posta** Koruması: Değerlendirmek istediğiniz kiracı E-posta güvenliği için Office 365 kullanır ve Posta Exchange (MX) kaydı Microsoft'a puanları sağlar.

### <a name="email-security-gateway"></a>E-posta güvenliği ağ geçidi

Üçüncü taraf bir e-posta güvenlik ağ geçidi (ESG) kullanıyorsanız, sağlayıcının adını bilmek gerekir. Şirket içi ESG veya desteklenen olmayan satıcılar kullanıyorsanız, cihazlara yönelik genel IP adreslerini bilgilisiniz.

Desteklenen üçüncü taraf iş ortakları şunlardır:

- Barracuda
- IronPort
- Mimecast
- Proofpoint
- İkinci sınıf
- Bursa
- Eğilim Mikro

### <a name="scoping"></a>Coping

Değerlendirmenin kapsamını bir gelen bağlayıcısı olarak kullanabilirsiniz. Yapılandırılmış bağlayıcı yoksa, değerlendirme kapsamı yöneticilerin kiracınız içinde yer alan herhangi bir kullanıcıdan veri topladığı ve Defender'ı varsayılan Office 365.

## <a name="get-started-with-the-evaluation"></a>Değerlendirmeyle çalışmaya başlama

Aşağıdaki erişim noktalarından Office 365 portalında değerlendirme Microsoft 365 Defender için Microsoft Defender'ı bulun:

- **Uç noktalar** \> **Güvenlik Açığı Yönetimi** \> **Pano** (<https://security.microsoft.com/tvm_dashboard>)
- **E-& ve işbirliği** \> **İlkeler & kuralları** \> **Tehdit ilkeleri** (<https://security.microsoft.com/threatpolicy>)
- **Raporlar** \> **E-& işbirliği** \> **E-& işbirliği raporları** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Değerlendirmeyi ayarlama

Değerlendirmeniz için ayarlama akışına başladıktan sonra size iki yönlendirme seçeneği verilir. Kuruluş posta yönlendirme kurulumu ve değerlendirme gereksinimlerine bağlı olarak, üçüncü taraf hizmet sağlayıcı mı, yoksa şirket içi hizmet sağlayıcısı mı yoksa yalnızca şirket içi hizmet sağlayıcısı mı Microsoft Exchange Online.

- Üçüncü taraf bir iş ortağı ve/veya şirket içi hizmet sağlayıcısı kullanıyorsanız, açılan menüden satıcının adını seçmeniz gerekir. Bağlayıcıyla ilgili diğer ayrıntıları sağlama.

- **MX Microsoft Exchange Online** Microsoft'a gidip bir posta kutunuz varsa, O'Exchange Online seçin.

Ayarlarınızı gözden geçirme ve gerekirse düzenleme. Ardından Değerlendirme **oluştur'a seçin**. Ayarlamanın tamam olduğunu belirten bir onay iletisi alırsınız.

Değerlendirme için Microsoft Defender Office 365 değerlendirme raporunuz günde bir kez oluşturulur. Verilerin doldurmak 24 saat kadar sürebilir.

### <a name="exchange-mail-flow-rules-optional"></a>Exchange akış kurallarını güncelleştirme (isteğe bağlı)

Mevcut bir ağ geçidiniz varsa değerlendirme modunu etkinleştirmek, Bağlayıcılar için Geliştirilmiş Filtreleme özelliğini etkinleştirir. Bu özellik, gelen gönderen IP adresini değiştirerek filtreleme doğruluğunu geliştirmektedir. Bu özellik filtre kararlarını değiştirebilir ve bazı iletileri atlamiyorsanız Exchange Online Protection, teslim edilebilirliği değiştirebilir. Bu durumda etkiyi çözümlemek için filtreyi geçici olarak atlamak iyi bir yol olabilir. Filtrelemeyi atlamak için, iletilerin SCL'sini -1 olarak ayarlayan (yoksa) Exchange yönetim merkezinde (EAC) bir posta akışı kuralı (aktarım kuralı olarak da bilinir) <https://admin.exchange.microsoft.com/#/transportrules> oluşturun. Yönergeler için bkz[. Posta akış kurallarını kullanarak e-posta iletilerinde istenmeyen posta güven düzeyini (SCL) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Özellikleri değerlendirme

Değerlendirme raporu oluşturulduktan sonra, e-postalarda ve işbirliği çalışma alanlarında kaç gelişmiş tehdit bağlantısı, gelişmiş tehdit eki ve kimliğe bürünülme kimliğine bürünülen kişi olduğunu bakın.

Deneme süresinin süresi dolduğunda, rapora 90 gün boyunca erişmeye devam edersiniz. Bununla birlikte, daha fazla bilgi toplamaz. Deneme süreniz sona erdikten sonra Office 365 için Microsoft Defender'ı kullanmaya devam etmek için Office 365 [(Plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) için ücretli bir abonelik satın almayı öğrenin.

Yönlendirmenizi güncelleştirmek **Ayarlar** veya değerlendirmenizi herhangi bir zamanda kapatmak için Ayarlar'ye gidebilirsiniz. Ancak, değerlendirmenizi kapattıktan sonra da değerlendirmeye devam etmek için aynı ayarlama işlemini tekrar değerlendirmeniz gerekir.

## <a name="provide-feedback"></a>Geri bildirim sağlama

Geri bildiriminiz, ortamınızı gelişmiş saldırılardan koruma konusunda daha iyi bir şekilde çalışmamıza yardımcı olur. Deneyimlerinizi ve ürün becerilerinizi ve değerlendirme sonuçlarını genel olarak paylaşın.

**Görüşlerinizi bize haber** vermek için Geri bildirim ver'i seçin.
