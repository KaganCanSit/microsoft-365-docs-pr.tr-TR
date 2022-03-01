---
title: '3. Aşama için Microsoft Defender Office 365 na geçiş: Ekleme'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Üçüncü taraf koruma hizmetlerinden veya cihazdan Microsoft Defender'a üçüncü taraf korumasından Microsoft Defender'a Office 365 tamamlayın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3798bdb28bb44b5148574b4c09a372ff564e47e5
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010183"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Geçiş için Microsoft Defender'Office 365 - Aşama 3: Ekleme

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

<br>

|[![Aşama 1: Hazırlık.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Aşama 1: Hazırlama](migrate-to-defender-for-office-365-prepare.md)|[![Aşama 2: Ayarlama.](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Aşama 2: Ayarlama](migrate-to-defender-for-office-365-setup.md)|![Aşama 3: Ekleme.](../../media/phase-diagrams/onboard.png) <br> Aşama 3: Ekleme|
|---|---|---|
|||*Buradasınız!*|

Aşama **3'e hoş geldiniz: Üçüncü** yıl için **[Microsoft Defender'a Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Güvenlik önlemlerini eklemeye Teams](#step-1-begin-onboarding-security-teams)
2. [(İsteğe bağlı) Pilot kullanıcıların var olan koruma hizmetiniz tarafından filtre uygulamanın dışında tutulacak](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Akıllı ifadeyi ayarlama](#step-3-tune-spoof-intelligence)
4. [Kimliğe bürünme koruması ve posta kutusu zekası ayarlama](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Ölçmek ve ayarlamak için kullanıcı gönderimlerinden veri kullanma](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(İsteğe bağlı) Pilot uygulamanıza daha fazla kullanıcı ekleyin ve daha fazla kullanıcı ekleyin](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [SCL=Microsoft 365-1 posta akış kuralını tüm kullanıcılara genişletme ve kapatma](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [MX kayıtlarınızı değiştirme](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>1. Adım: Eklemeye başlama Güvenlik Teams

Kuruluşta bir güvenlik müdahale ekibi varsa, şimdi sizin için Microsoft Defender'ı bilet sistemleri Office 365 yanıt süreçlerinize tümleştirmeye başlamanın tam zamanı. Bu kendi başına bir konu başlığıdır, ancak bazen gözden kaçırabilirsiniz. Güvenlik yanıtı ekibinin erkenden dahil olmasını sağlamak, MX kayıtlarınızı değiştirişte, kuruluşlarının tehditlerle başa çıkmaya hazır olmasını sağlar. Olay müdahalesi, aşağıdaki görevleri yerine idare etmek için iyi bir şekilde sahip olmak gerekir:

- Yeni araçları öğrenin ve bunları mevcut akışlara tümleştirin. Örneğin:
  - Karantinaya alınmış iletilerin yönetici yönetimi önemlidir. Yönergeler için bkz [. Karantinaya alınmış iletileri ve dosyaları yönetici olarak yönetme](manage-quarantined-messages-and-files.md).
  - İleti izleme, iletiler siz girdiler veya ayrıldıklarına ne olduğunu Microsoft 365. Daha fazla bilgi için [bkz. Yönetim merkezinde modern Exchange ileti izleme Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Kuruluşa izin ver gereken riskleri belirleme.
- Kurumsal işlemler için [uyarıları](../../compliance/alert-policies.md) ayarlama ve özelleştirme.
- Olay kuyruğun yönetin ve olası riskleri düzeltmek.

If your organization has purchased Microsoft Defender for Office 365 Plan 2, they should familiarizing themselves and using features such as Threat Explorer, Advanced Hunting, and Incidents. İlgili eğitimler için bkz.<https://aka.ms/mdoninja>

Güvenlik yanıtı ekipleriniz filtrelenmemiş iletileri toplar ve çözümlerse, bu filtrelenmemiş iletileri almak için SecOps posta kutusunu yapılandırabilirsiniz. Yönergeler için bkz. [Gelişmiş teslim ilkesinde SecOps posta kutularını yapılandırma](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

SIEM/SOAR ile tümleştirme hakkında daha fazla bilgi için, aşağıdaki makalelere bakın:

- [API'lere Microsoft 365 Defender genel bakış](/microsoft-365/security/defender/api-overview)
- [Akış API'si](/microsoft-365/security/defender/streaming-api)
- [Gelişmiş Av API'si](/microsoft-365/security/defender/api-advanced-hunting)
- [Olay API'leri](/microsoft-365/security/defender/api-incident)

Eğer kuruluşta güvenlik müdahale ekibi yoksa veya mevcut süreç akışları hakkında bilgi edinebilirsiniz. Bu zamanı, destek için Defender'daki temel av ve yanıt özelliklerini Office 365. Daha fazla bilgi için bkz [. Tehdit soruşturması ve yanıtı](office-365-ti.md).

### <a name="rbac-roles"></a>RBAC rolleri

Office 365 için Defender'daki izinler rol tabanlı erişim denetimine (RBAC) dayalıdır ve Microsoft 365 Defender [portalında açıklanmıştır](permissions-microsoft-365-security-center.md). Bunlar, gözlerde tutmanız gereken önemli noktalardır:

- Azure AD rolleri, iş **yüklerinin tüm** iş yüklerine Microsoft 365. Örneğin, Azure portalda Güvenlik Yöneticisi'ne kullanıcı eklerseniz, bu kullanıcının her yerde Güvenlik Yöneticisi izinleri olur.
- & portalında e-posta ve işbirliği rolleri Microsoft 365 Defender Portalına, Microsoft 365 Defender Portalı'Microsoft 365 uyumluluk merkezi ve daha eski olan Güvenlik ve Uyumluluk Merkezi'ne & verin. Örneğin, Microsoft 365 Defender portalında Güvenlik Yöneticisi'ne kullanıcı eklerseniz, bu kullanıcının yalnızca Microsoft 365 Defender Portalı' Microsoft 365 uyumluluk merkezi ve Güvenlik &  erişimi olur.
- Microsoft 365 Defender portalında birçok özellik Exchange Online PowerShell cmdlet'lerini temel almıştır ve bu nedenle Exchange Online'de ilgili rollerde (teknik olarak, rol grupları) rol grubu üyeliği gerekir (özellikle, ilgili özel olarak ilgili rollere erişim için Exchange Online  PowerShell cmdlet'leri).
- Microsoft 365 Defender portalında & Azure AD rollerinin eşdeğeri olan ve güvenlik işlemleri için önemli olan E-posta özellikleri işbirliği rolleri vardır (örneğin, Önizleme rolü ve Arama ve Temizleme rolü).

Normalde, yalnızca güvenlik personelinin alt kümesinin kullanıcı posta kutularından iletileri doğrudan indirmesi için ek haklara ihtiyacı olur. Bunun için, Güvenlik Okuyucusu'nın varsayılan olarak sahip olmadığını ek bir izin gerekir.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>2. Adım: (İsteğe bağlı) Muaf pilot kullanıcıların var olan koruma hizmetiniz tarafından filtre uygulamasını geri alın

Bu adım gerekli değildir, ancak pilot kullanıcılarınızı var olan koruma hizmetiniz tarafından filtrelemeyi at edecek şekilde yapılandırmayı düşünebilirsiniz. Bu eylem, Office 365 için Defender'ın pilot kullanıcıların tüm  filtreleme ve koruma görevlerini işlemesini sağlar. Pilot kullanıcılarınızı mevcut koruma hizmetiniz için muaf değilsanız, Office 365 için Defender yalnızca diğer hizmetten gelen (zaten filtrelenmiş olan iletileri filtreleme) tarafından etkin bir şekilde çalışır.

> [!NOTE]
> Geçerli koruma hizmetiniz bağlantı kaydırma özelliği sağladığı ancak Bağlantı işlevselliğiyle ilgili pilot Kasa gerekir. Bağlantıların çift kaydırma özelliği desteklanmaz.

## <a name="step-3-tune-spoof-intelligence"></a>3. Adım: Akıllı ifadeyi ayarlama

İzin verilen [veya](learn-about-spoof-intelligence.md) engellenen ifadeyi (yanıltı) görmek ve ifadeyi geçersiz kılmak için sistem kararlarını geçersiz kılmaya gerek olup olmadığını belirlemek için Bilgi Bloğu içgörüsine bakın. İş açısından kritik e-posta kaynaklarından bazıları DNS'de (SPF, DKIM ve DMARC) yanlış yapılandırılmış e-posta kimlik doğrulama kayıtlarına sahip olabilir ve etki alanı sorunlarını maskelerken mevcut koruma hizmetiniz içinde geçersiz kılmalar kullanıyor olabilirsiniz.

Kimliksız kimlik doğrulaması, DNS'de düzgün e-posta kimlik doğrulaması kayıtları olmadan etki alanlarından e-postaları kurtarabilirsiniz, ancak özellik bazen hatalı kimlik doğrulamasından iyi kimlik doğrulamayı ayırt etmek için yardıma ihtiyaç alır. Aşağıdaki ileti kaynağı türlerine odaklanın:

- Bağlayıcılar için Gelişmiş Filtreleme'de tanımlanan IP adresi [aralıklarının dışında olan ileti kaynakları](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- En fazla ileti sayısına sahip ileti kaynakları.
- Organizasyon üzerinde en yüksek etkiyi alan ileti kaynakları.

Kimlik hesabı zekası, kullanıcı gönderimlerini yapılandırdıktan sonra sonunda kendisini ayar gerektirecek, bu nedenle herhangi bir neden yoktur.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>4. Adım: Kimliğe bürünme koruması ve posta kutusu zekası ayarlama

Hiçbir eylem modu uygulama altında kimliğe bürünme korumasının sonuçlarını gözlemlemek için yeterli  zaman elde ettikten sonra, kimlik avı önleme ilkelerinde her kimliğe bürünme koruma eylemlerini tek tek açabilirsiniz:

- Kullanıcı kimliğe bürünme koruması: **hem Standart hem de Katı** için iletiyi karantinaya alın.
- Etki alanı kimliğe bürünme koruması: **İletiyi hem** Standart hem de Katı için karantinaya alın.
- Posta kutusu zekası **koruması: standart için iletiyi alıcıların Gereksiz E-posta klasörlerine** taşıma; **Katı için iletiyi** karantinaya alın.

İletilere herhangi bir işlem yapmadan kimliğe bürünme koruma sonuçlarını ne kadar uzun süre izlersiniz? Ne kadar çok veriye ihtiyaç olacağını belirlemek için izinler veya engellemeler gerekir. Gözlem ve ayarlamaya olanak tanıyacak kadar önemli olan her korumayı açma arasında gecikmeler kullanmayı göz önünde bulundurarak.

> [!NOTE]
> Bu korumaları sık sık ve sürekli izlemek ve ayarlamak önemlidir. Hatalı pozitif sonuçlardan şüpheleniyorsanız nedenini araştırarak geçersiz kılmaları yalnızca gerekli olduğu şekilde ve yalnızca gerekli algılama özelliği için kullanın.

### <a name="tune-mailbox-intelligence"></a>Posta kutusu zekası ayarlama

Posta kutusu zekası, kimliğe bürünme girişimleri olarak belirlenen iletilerde herhangi bir işlem yapmak üzere yapılandırılmış olsa [da, pilot](impersonation-insight.md) kullanıcıların e-posta gönderme ve alma desenlerini öğrenmeye devam ediyor ve bunu öğreniyor. Bir dış kullanıcı pilot kullanıcılarından biri ile bağlantıda olursa, bu dış kullanıcıdan gelen iletiler posta kutusu zekası tarafından kimliğe bürünme girişimleri olarak tanımsızlamaz (dolayısıyla hatalı pozitif sonuçlar azaltıldı).

Hazırsanız, posta kutusu zekası diğer bir kimliğe bürünme girişimleri olarak algılanan iletiler üzerinde hareket etmeye izin vermek için aşağıdaki adımları izleyin:

- Standart koruma ayarlarına sahip kimlik avı önleme ilkesinde, Posta kutusu zekası kimliğine  bürünülen bir kullanıcı algılarsa iletiyi alıcıların Gereksiz E-posta klasörlerine taşımak için değerini **değiştirin**.

- Katı koruma ayarlarının olduğu Kimlik avı önleme ilkesinde, Posta kutusu zekası, kimliğine bürünülen bir kullanıcı algılar ve bu kullanıcının değerini İletiyi karantinaya **alın olarak değiştirin**.

İlkeleri değiştirmek için bkz. [Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemledikten ve tüm ayarlamaları yaptıktan sonra, kullanıcı kimliğe bürünülerek algılanan iletileri karantinaya almak için bir sonraki bölüme ilerleyin.

### <a name="tune-user-impersonation-protection"></a>Kullanıcı kimliğe bürünme korumasını ayarlama

Standart ve Katı ayarları temel alan kimlik avı önleme ilkelerinizin her ikisinde de, Eğer iletisi kimliğine  bürünülen bir kullanıcı olarak algılanırsa değerini iletiyi **Karantina'ya alın olarak değiştirin**.

Kullanıcı [kimliğe bürünme girişimleriyle](impersonation-insight.md) nelerin engellenmiş olduğunu görmek için kimliğe bürünme içgörüne bakın.

İlkeleri değiştirmek için bkz. [Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemledikten ve tüm ayarlamaları yapıldıktan sonra, etki alanı kimliğine bürünülerek algılanan iletileri karantinaya almak için sonraki bölüme ilerleyin.

### <a name="tune-domain-impersonation-protection"></a>Etki alanı kimliğe bürünme korumasını ayarlama

Standart ve Katı ayarları temel alan kimlik avı önleme ilkelerinizin her ikisinde de, Eğer iletisi kimliğine  bürünülen bir etki alanı olarak algılanırsa değerini iletiyi karantinaya **alın olarak değiştirin**.

Etki alanı [kimliğe bürünme](impersonation-insight.md) girişimleriyle nelerin engellenmiş olduğunu görmek için kimliğe bürünme içgörüne bakın.

İlkeleri değiştirmek için bkz. [Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemlemek ve gerekli ayarlamaları yapmak.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>5. Adım: Ölçmek ve ayarlamak için kullanıcı gönderimlerinden verileri kullanma

Pilot kullanıcılarınız hatalı pozitif ve yanlış negatif sonuçlar bildirseler, iletiler portalında [Gönderiler sayfasında Microsoft 365 Defender görüntülenir](admin-submission.md). Yanlış tanımlanamayan iletileri çözümleme için Microsoft'a bildirebilirsiniz ve pilot uygulama ayarlarınıza ilişkin ayarları ve özel durumları gereken şekilde ayarlamak için bilgileri kullanabilirsiniz.

Aşağıdaki özellikleri kullanarak, aşağıdaki özellikler için Defender'daki koruma ayarlarını izleyebilir ve Office 365:

- [Karantina](manage-quarantined-messages-and-files.md)
- [Tehdit Gezgini](email-security-in-microsoft-defender.md)
- [E-posta güvenlik raporları](view-email-security-reports.md)
- [Office 365 raporları için Defender](view-reports-for-mdo.md)
- [Posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Organizasyonunız kullanıcı raporları için üçüncü taraf bir hizmet kullanıyorsa, bu verileri geri bildirim döngüyle tümleştirebilirsiniz.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>6. Adım: (İsteğe bağlı) Pilot uygulamanıza daha fazla kullanıcı ekleme ve adımı uygulama

Sorunları bulup düzeltirken pilot gruplara daha fazla kullanıcı  eklersiniz (ve bu yeni pilot kullanıcıların uygun şekilde var olan koruma hizmetiniz tarafından taramasını muaftabilirsiniz). Şu anda ne kadar çok test yapar, daha sonra o kadar az kullanıcı sorunuyla uğraşabilirsiniz. Bu "Şelale" yaklaşımı kuruluşun daha büyük bölümlerine göre ayara izin verir ve güvenlik ekiplerinize yeni araçlar ve işlemlere ayar yapmak için zaman verir.

- Microsoft 365, kurumsal ilkelere yüksek güven kimlik avı iletilerine izin veri olduğunda uyarı verir. Bu iletileri tanımlamak için aşağıdaki seçenekleri kullanabilirsiniz:
  - Tehdit koruması durumu [raporunda geçersiz kılmalar](view-email-security-reports.md#threat-protection-status-report).
  - İletileri tanımlamak için Tehdit Gezgini'nde filtreleyin.
  - İletileri tanımlamak için Gelişmiş Arama'da filtre uygulama.

  Yönetici gönderimleri aracılığıyla tüm hatalı pozitif sonuçlar için mümkün olan en erken zamanda Microsoft'a rapor edin, bu hatalı pozitif sonuçlar için güvenli geçersiz kılmaları yapılandırmak için Kiracı İzin Ver [/](tenant-allow-block-list.md) Engelleme Listesi özelliğini kullanın.

- Gereksiz geçersiz kılmaları incelemek de iyi bir fikirdir. Başka bir deyişle, iletiler üzerinde Microsoft 365 kararlara bakın. Microsoft365 doğru karar düzeltmeyi işlese, geçersiz kılma ihtiyacı büyük ölçüde azalır veya ortadan kalkmış olur.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>7. Adım: Microsoft 365 korumasını genişletme ve SCL=-1 posta akış kuralını kapatma

MX kayıtlarınızı başka bir kayıtla işaret etmeye hazır olduğunda, bu bölümdeki Microsoft 365.

1. Pilot ilkeleri tüm kuruluşa genişletin. Temelde, bunu yapmanın farklı yolları vardır:
   - Önceden [belirlenmiş güvenlik ilkelerini](preset-security-policies.md) kullanın ve kullanıcılarınızı Standart koruma profiliyle Katı koruma profili (herkesin kapsa olduğundan emin olun) arasında bölün. Önceden belirlenmiş güvenlik ilkeleri, oluşturduğunuz özel ilkeler veya varsayılan ilkeler önce uygulanır. Tek tek pilot ilkelerinizi silmeden kapatabilirsiniz.

     Önceden belirlenmiş güvenlik ilkelerinin dezavantajı, güvenlik ilkelerini oluşturduktan sonra birçok önemli ayarı değiştirememenizi sağlar.

   - Pilot uygulama sırasında oluşturduğunuz ve ayar oluşturduğunuz ilkelerin kapsamını tüm kullanıcıları (örneğin, tüm etki alanlarındaki tüm alıcılar) içerecek şekilde değiştirebilirsiniz. Unutmayın; aynı türde birden çok ilke (örneğin, kimlik avı önleme ilkeleri) aynı kullanıcıya uygulanırsa (tek tek, grup üyeliği veya e-posta etki alanına göre), yalnızca en yüksek önceliğe sahip ilke ayarları (en düşük öncelik numarası) uygulanır ve bu tür ilkeler için işlem durakları uygulanır.

2. SCL=-1 posta akış kuralını kapatın (silmeden kapatabilirsiniz).

3. Önceki değişikliklerin geçerli olduğunu ve kullanıcı için Defender'ın Office 365 tüm kullanıcılar için düzgün etkinleştirildiğinden emin olun. Bu noktada, Office 365 için Defender'ın tüm koruma özellikleri, artık tüm alıcıların posta üzerinde eyleme girmesine izin veriliyor, ancak bu posta zaten var olan koruma hizmetiniz tarafından taranmış.

Daha büyük ölçekli veri kaydı ve ayarlamaları için bu aşamada duraklatabilirsiniz.

## <a name="step-8-switch-your-mx-records"></a>8. Adım: MX kayıtlarınızı değiştirme

> [!NOTE]
>
> - Etki alanınız için MX kaydını değiştirişte, değişikliklerin İnternet'te yayılması 48 saat kadar sürebilir.
>
> - Daha hızlı yanıt ve gerekirse geri alma sağlamak için DNS kayıtlarınızı TTL değerini düşürmenizi öneririz. Geçiş tamamlandıktan ve doğrulandıktan sonra özgün TTL değerine geri dönseniz bile.
>
> - Daha az sık kullanılan etki alanlarını değiştirmekle başlamayı düşünebilirsiniz. Daha büyük etki alanlarına gitmeden önce duraklatabilir ve izleyebilirsiniz. Öte yandan, bunu yapsanız bile tüm kullanıcıların ve etki alanlarının ilkeler kapsamında olduğundan emin olun, çünkü ikincil SMTP etki alanları ilke uygulamasından önceki birincil etki alanlarıyla çözümlenir.
>   
> - Tek bir etki alanı için birden çok MX kaydı teknik olarak çalışır ve bu teknik çalışma, bu makaledeki tüm yönlendirmeleri takip etmiş olmak kaydıyla bölünmüş yönlendirmeye sahip çalışmanıza olanak sağlar. Özel olarak, ilkelerin tüm kullanıcılara uygulandığından emin olun; SCL=-1 posta akış kuralı yalnızca var olan koruma hizmetiniz üzerinden geçen postaya [uygulanır.3. Adım: SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule) posta akış kuralını koruma veya oluşturma. Bununla birlikte, bu yapılandırma sorun gidermeyi çok daha zorlaştıracak bir davranışa neden olur ve dolayısıyla bunu özellikle de uzun süreler için önerilmez.
>
> - MX kayıtlarınızı değiştirmeden önce, gelen bağlayıcısı üzerinde koruma hizmetlerinden Gelen Bağlayıcısı'nın etkin olmadığını doğru Microsoft 365. Normalde, bağlayıcıda aşağıdaki ayarlardan biri veya daha fazlası yapılandırılmış olur:
>
>   - **ve iş ortağının Office 365** ile kimlik doğrulaması yapmak için kullandığı sertifikada konu adının bu etki alanı adıyla (*RestrictDomainsToCertificate) eşleşmesi gerekir*
>   - **Bu IP adresi aralığı içinden gönderilmezse e-posta** iletilerini reddetme (*RestrictDomainsToIPAddresses*)
>
>   Bağlayıcı türü **İş Ortağı ise** ve bu ayarlardan biri açıksa, MX kayıtlarınızı değiştirdikten sonra etki alanlarınıza tüm posta teslimi başarısız olur. Devam etmek için önce bu ayarları devre dışı bırakmanız gerekir. Bağlayıcı, karma için kullanılan bir şirket içi bağlayıcı ise, şirket içi bağlayıcıyı değiştirmenize gerek yok. Ancak yine de, bir İş ortağı bağlayıcısı olup varlıklarını **kontrol** edin.
>   
> - Geçerli posta ağ geçidiniz de alıcı doğrulaması sağlıyorsa, etki alanının Adres Mektup birleştirmede Yetkili olarak [yapılandırıldığından](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) emin Microsoft 365. Bu, gereksiz geri dönen iletileri önlenebilir.

Hazır olduğunda, etki alanlarınız için MX kaydını değiştirme. Tüm etki alanlarınızı aynı anda geçirebilirsiniz. Ya da, daha az sık kullanılan etki alanlarını önce ve sonra kalanları daha sonra geçirebilirsiniz.

Herhangi bir noktada burada duraklatabilir ve değerlendire durabilirsiniz. Ama unutmayın: SCL=-1 posta akış kuralını kapattıktan sonra, kullanıcıların hatalı pozitif sonuçlarını denetlemeyle ilgili iki farklı deneyimi olabilir. Ne kadar kısa sürede tek ve tutarlı bir deneyim sımsık olursanız, kullanıcılarınızı ve yardım masası ekiplerini, eksik iletilerde sorun gidermeleri ne kadar mutlu edecekse o kadar mutlu olur.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler! İş için [Microsoft Defender'a geçiş işleminizi Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Bu geçiş kılavuzunda adımları takip etmiş olacağınız için, postanın doğrudan Posta'ya teslim Microsoft 365 çok daha sorunsuz olması gerekir.

Şimdi siz, diğer iki işlem için Defender'ın normal çalışmasına ve bakımına Office 365. Pilot çalışma sırasında ancak daha büyük ölçekli olarak deneyimle ilgili sorunları izleyin ve izleyin. Kimlik [sahtesi içgörü ve](learn-about-spoof-intelligence.md) kimliğe bürünme içgörüleri çok yararlı olacaktır, ancak aşağıdaki etkinlikleri normal bir oluşum olarak değerlendirin:[](impersonation-insight.md)

- Kullanıcı gönderimlerini ve özellikle de kullanıcı [tarafından bildirilen kimlik avı iletilerini gözden geçirme](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office)
- Tehdit koruması durumu raporunda [geçersiz kılmaları gözden geçirebilirsiniz](view-email-security-reports.md#threat-protection-status-report).
- Fırsatları [ve riskli](/microsoft-365/security/defender/advanced-hunting-example) iletileri ayarlamak için Gelişmiş Arama sorgularını kullanın.
