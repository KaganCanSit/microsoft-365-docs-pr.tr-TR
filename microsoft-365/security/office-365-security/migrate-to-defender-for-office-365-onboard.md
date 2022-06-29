---
title: "Office 365 için Microsoft Defender Aşama 3'e geçiş: Ekleme"
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
description: Üçüncü taraf koruma hizmetinden veya cihazından Office 365 için Microsoft Defender korumasına geçiş adımlarını tamamlayın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b2358103b3ab6bfee34e88d23f4b3de0d774e34e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492136"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Office 365 için Microsoft Defender Geçiş - 3. Aşama: Ekleme

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

<br>

|[![1. Aşama: Hazırlanın.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Aşama 1: Hazırlık](migrate-to-defender-for-office-365-prepare.md)|[![2. Aşama: Ayarlama.](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Aşama 2: Kurulum](migrate-to-defender-for-office-365-setup.md)|![3. Aşama: Ekleme.](../../media/phase-diagrams/onboard.png) <br> Aşama 3: Katılım|
|---|---|---|
|||*Buradasınız!*|

**3. Aşama:** **[geçişinizi Office 365 için Microsoft Defender eklemeye](migrate-to-defender-for-office-365.md#the-migration-process)** hoş geldiniz! Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Güvenlik Ekiplerini eklemeye başlama](#step-1-begin-onboarding-security-teams)
2. [(İsteğe bağlı) Pilot kullanıcıların mevcut koruma hizmetinize göre filtrelemesini muaf tutma](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Sahte zekayı ayarlama](#step-3-tune-spoof-intelligence)
4. [Kimliğe bürünme koruması ve posta kutusu zekasını ayarlama](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Ölçmek ve ayarlamak için kullanıcı gönderimlerindeki verileri kullanma](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(İsteğe bağlı) Pilotunuza daha fazla kullanıcı ekleme ve yineleme](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Microsoft 365 korumasını tüm kullanıcılara genişletme ve SCL=-1 posta akışı kuralını kapatma](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [MX kayıtlarınızı değiştirme](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>1. Adım: Güvenlik Ekiplerini eklemeye başlama

Kuruluşunuzun bir güvenlik yanıt ekibi varsa, şimdi Office 365 için Microsoft Defender bilet sistemleri de dahil olmak üzere yanıt süreçlerinizle tümleştirmeye başlamanın tam zamanıdır. Bu tamamen kendi başına bir konudur, ancak bazen göz ardı edilir. Güvenlik yanıtı ekibini erken devreye almak, MX kayıtlarınızı değiştirdiğinizde kuruluşunuzun tehditlerle başa çıkmak için hazır olmasını sağlar. Olay yanıtının aşağıdaki görevleri yerine getirmek için iyi bir donanıma sahip olması gerekir:

- Yeni araçları öğrenin ve mevcut akışlarla tümleştirin. Örneğin:
  - Karantinaya alınan iletilerin Yönetici yönetimi önemlidir. Yönergeler için bkz. [Karantinaya alınan iletileri ve dosyaları yönetici olarak yönetme](manage-quarantined-messages-and-files.md).
  - İleti izleme, Microsoft 365'e girerken veya microsoft 365'den ayrılırken iletilere ne olduğunu görmenizi sağlar. Daha fazla bilgi için bkz. [Exchange Online'deki modern Exchange yönetim merkezinde ileti izleme](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Kuruluşa verilmiş olabilecek riskleri belirleyin.
- Kurumsal işlemler için [uyarıları](../../compliance/alert-policies.md) ayarlayın ve özelleştirin.
- Olay sırasını yönetin ve olası riskleri düzeltin.

Kuruluşunuz Plan 2 Office 365 için Microsoft Defender satın aldıysa Tehdit Gezgini, Gelişmiş Tehdit Avcılığı ve Olaylar gibi özellikleri tanımaya ve kullanmaya başlamalıdır. İlgili eğitimler için bkz <https://aka.ms/mdoninja>. .

Güvenlik yanıtı ekibiniz filtrelenmemiş iletileri toplar ve çözümlerse, bu filtrelenmemiş iletileri almak için bir SecOps posta kutusu yapılandırabilirsiniz. Yönergeler için bkz. [Gelişmiş teslim ilkesinde SecOps posta kutularını yapılandırma](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

SIEM/SOAR ile tümleştirme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Microsoft 365 Defender API'lerine genel bakış](/microsoft-365/security/defender/api-overview)
- [Akış API'si](/microsoft-365/security/defender/streaming-api)
- [Gelişmiş Avcılık API'si](/microsoft-365/security/defender/api-advanced-hunting)
- [Olay API'leri](/microsoft-365/security/defender/api-incident)

Kuruluşunuzun bir güvenlik yanıt ekibi veya mevcut işlem akışları yoksa, Office 365 için Defender'daki temel tehdit avcılığı ve yanıt özellikleri hakkında bilgi edinmek için bu zamanı kullanabilirsiniz. Daha fazla bilgi için bkz [. Tehdit araştırması ve yanıtı](office-365-ti.md).

### <a name="rbac-roles"></a>RBAC rolleri

Office 365 için Defender'deki izinler rol tabanlı erişim denetimini (RBAC) temel alır ve [Microsoft 365 Defender portalındaki](permissions-microsoft-365-security-center.md) İzinler bölümünde açıklanmıştır. Göz önünde bulundurulması gereken önemli noktalar şunlardır:

- Azure AD rolleri, Microsoft 365'teki **tüm** iş yüklerine izin verir. Örneğin, Azure portal Güvenlik Yöneticisi'ne bir kullanıcı eklerseniz, her yerde Güvenlik Yöneticisi izinleri olur.
- Microsoft 365 Defender portalındaki e-posta & işbirliği rolleri, Microsoft 365 Defender Portalı, Microsoft Purview uyumluluk portalı ve eski Güvenlik & Uyumluluk Merkezi'ne izin verir. Örneğin, Microsoft 365 Defender portalında Güvenlik Yöneticisi'ne bir kullanıcı eklerseniz, bu kullanıcının **yalnızca** Microsoft 365 Defender Portalı, Microsoft Purview uyumluluk portalı ve Güvenlik & Uyumluluk Merkezi'nde Güvenlik Yöneticisi erişimi olur.
- Microsoft 365 Defender portalındaki birçok özellik Exchange Online PowerShell cmdlet'lerini temel alır ve bu nedenle Exchange Online karşılık gelen rollerde (teknik olarak rol grupları) rol grubu üyeliği gerektirir (özellikle ilgili Exchange Online  PowerShell cmdlet'leri).
- Microsoft 365 Defender portalında Azure AD rolleriyle eşdeğer olmayan ve güvenlik işlemleri için önemli olan E-posta & işbirliği rolleri vardır (örneğin Önizleme rolü ve Arama ve Temizleme rolü).

Genellikle yalnızca bir güvenlik personeli alt kümesi, iletileri doğrudan kullanıcı posta kutularından indirmek için ek haklara ihtiyaç duyar. Bu, Güvenlik Okuyucusu'nın varsayılan olarak sahip olmadığı ek bir izin gerektirir.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>2. Adım: (İsteğe bağlı) Pilot kullanıcıların mevcut koruma hizmetinize göre filtrelemesini muaf tutma

Bu adım gerekli olmasa da, pilot kullanıcılarınızı mevcut koruma hizmetinize göre filtrelemeyi atlayacak şekilde yapılandırmayı düşünmelisiniz. Bu eylem, Office 365 için Defender pilot kullanıcılar için **tüm** filtreleme ve koruma görevlerini işlemesini sağlar. Pilot kullanıcılarınızı mevcut koruma hizmetinizden muaf tutmazsanız, Office 365 için Defender yalnızca diğer hizmetten gelen yanıtsızlıklarda (filtrelenmiş iletileri filtreleme) etkili bir şekilde çalışır.

> [!NOTE]
> Geçerli koruma hizmetiniz bağlantı sarmalama sağlıyorsa ancak Güvenli Bağlantılar işlevselliğini pilot olarak kullanmak istiyorsanız bu adım açıkça gereklidir. Bağlantıların çift kaydırması desteklenmez.

## <a name="step-3-tune-spoof-intelligence"></a>3. Adım: Sahte zekayı ayarlama

Kimlik sahtekarlığına izin verilen veya engellenen özellikleri görmek ve kimlik sahtekarlığına yönelik sistem kararını geçersiz kılmanız gerekip gerekmediğini belirlemek için Kimlik Sahtekarlığına ilişkin bilgi sahtekarlığına ilişkin [içgörüleri](learn-about-spoof-intelligence.md) gözden geçirin. İş açısından kritik e-postanızın bazı kaynakları DNS'de (SPF, DKIM ve DMARC) e-posta kimlik doğrulama kayıtlarını yanlış yapılandırmış olabilir ve etki alanı sorunlarını maskelemek için mevcut koruma hizmetinizde geçersiz kılmalar kullanıyor olabilirsiniz.

Kimlik sahtekarı zekası, DNS'de düzgün e-posta kimlik doğrulaması kayıtları olmadan etki alanlarından e-postayı kurtarabilir, ancak özellik bazen iyi sahtekarlık ile hatalı kimlik sahtekarlıklarını ayırt etme konusunda yardıma ihtiyaç duyar. Aşağıdaki ileti kaynağı türlerine odaklanın:

- [Bağlayıcılar için Gelişmiş Filtreleme'de](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) tanımlanan IP adresi aralıklarının dışında olan ileti kaynakları.
- İleti sayısı en yüksek olan ileti kaynakları.
- Kuruluşunuz üzerinde en yüksek etkiye sahip ileti kaynakları.

Kimlik sahtekarlığı zekası, kullanıcı gönderimlerini yapılandırdıktan sonra sonunda kendini ayarlar, bu nedenle mükemmellik gerekmez.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>4. Adım: Kimliğe bürünme korumasını ve posta kutusu zekasını ayarlama

Herhangi **bir eylem modu uygulama** bölümünde kimliğe bürünme korumasının sonuçlarını gözlemlemek için yeterli süreniz olduktan sonra kimlik avı önleme ilkelerindeki her kimliğe bürünme koruması eylemini tek tek açabilirsiniz:

- Kullanıcı kimliğe bürünme koruması: İletiyi hem Standart hem de Katı için **karantinaya alın** .
- Etki alanı kimliğe bürünme koruması: İletiyi hem Standart hem de Katı için **karantinaya alın** .
- Posta kutusu yönetim bilgileri koruması: **İletiyi Standart için alıcıların Gereksiz E-posta klasörlerine taşıyın** ; **İletiyi Strict için karantinaya alın** .

İletiler üzerinde işlem yapmadan kimliğe bürünme koruması sonuçlarını ne kadar uzun süre izlerseniz, gerekli olabilecek izinler veya bloklar için o kadar fazla veri tanımlamanız gerekir. Gözlem ve ayarlamaya izin verecek kadar önemli olan her korumayı açmak arasında bir gecikme kullanmayı göz önünde bulundurun.

> [!NOTE]
> Bu korumaların sık ve sürekli izlenmesi ve ayarlanması önemlidir. Hatalı pozitif olduğundan şüpheleniyorsanız, nedenini araştırın ve geçersiz kılmaları yalnızca gerektiği gibi ve yalnızca bunu gerektiren algılama özelliği için kullanın.

### <a name="tune-mailbox-intelligence"></a>Posta kutusu zekası ayarlama

Posta kutusu zekası [kimliğe bürünme girişimleri olduğu belirlenen iletilerde](impersonation-insight.md) hiçbir işlem gerçekleştirecek şekilde yapılandırılmış olsa da, pilot kullanıcıların e-posta gönderme ve alma düzenlerini öğrenmiştir. Dış kullanıcı pilot kullanıcılarınızdan biriyle iletişim halindeyse, bu dış kullanıcıdan gelen iletiler posta kutusu zekası tarafından kimliğe bürünme girişimleri olarak tanımlanmaz (böylece hatalı pozitif sonuçları azaltır).

Hazır olduğunuzda, posta kutusu zekasının kimliğe bürünme girişimi olarak algılanan iletiler üzerinde işlem gerçekleştirmesine izin vermek için aşağıdaki adımları uygulayın:

- Standart koruma ayarlarıyla kimlik avı önleme ilkesinde, **Posta kutusu zekası kimliğine bürünülen bir kullanıcı algılarsa** iletisini **alıcıların Gereksiz E-posta klasörlerine taşı** olarak değerini değiştirin.

- Katı koruma ayarlarıyla kimlik avı önleme ilkesinde, **Posta kutusu zekası tarafından algılanan ve kimliğine bürünülen kullanıcıyı algılarsa** değerini **Karantinaya** al olarak değiştirin.

İlkeleri değiştirmek için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemleyip herhangi bir ayarlama yaptıktan sonra, kullanıcı kimliğine bürünme tarafından algılanan iletileri karantinaya almak için sonraki bölüme geçin.

### <a name="tune-user-impersonation-protection"></a>Kullanıcı kimliğe bürünme korumasını ayarlama

Standart ve Katı ayarları temel alan kimlik avı önleme ilkelerinizin her ikisinde de, **kimliğine bürünülen bir kullanıcı olarak algılanan iletinin** değerini **değiştirerek iletiyi karantinaya alın**.

Kullanıcı kimliğe bürünme girişimi olarak neyin engellendiğini görmek için kimliğe bürünme [içgörüsüsüne](impersonation-insight.md) bakın.

İlkeleri değiştirmek için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemleyip herhangi bir ayarlama yaptıktan sonra, etki alanı kimliğe bürünme tarafından algılanan iletileri karantinaya almak için sonraki bölüme geçin.

### <a name="tune-domain-impersonation-protection"></a>Etki alanı kimliğe bürünme korumasını ayarlama

Standart ve Katı ayarları temel alan kimlik avı önleme ilkelerinizin her ikisinde de, **kimliğine bürünülen bir etki alanı olarak algılanan iletinin** değerini **değiştirerek iletiyi karantinaya alın**.

Etki alanı kimliğe bürünme girişimi olarak engellenenleri görmek için kimliğe bürünme [içgörüsüsüne](impersonation-insight.md) bakın.

İlkeleri değiştirmek için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

Sonuçları gözlemleyin ve gerekli ayarlamaları yapın.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>5. Adım: Ölçmek ve ayarlamak için kullanıcı gönderimlerindeki verileri kullanma

Pilot kullanıcılarınız hatalı pozitif sonuçları ve hatalı negatifleri rapor ettikçe, iletiler [Microsoft 365 Defender portalındaki Gönderimler sayfasında](admin-submission.md) görünür. Yanlış tanımlanan iletileri analiz için Microsoft'a bildirebilir ve bilgileri kullanarak pilot ilkelerinizdeki ayarları ve özel durumları gerektiği gibi ayarlayabilirsiniz.

Office 365 için Defender koruma ayarlarını izlemek ve yinelemek için aşağıdaki özellikleri kullanın:

- [Karantina](manage-quarantined-messages-and-files.md)
- [Tehdit Gezgini](email-security-in-microsoft-defender.md)
- [E-posta güvenlik raporları](view-email-security-reports.md)
- [raporları Office 365 için Defender](view-reports-for-mdo.md)
- [Posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Kuruluşunuz kullanıcı raporları için üçüncü taraf bir hizmet kullanıyorsa bu verileri geri bildirim döngünüzle tümleştirebilirsiniz.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>6. Adım: (İsteğe bağlı) Pilotunuza daha fazla kullanıcı ekleme ve yineleme

Sorunları bulup düzeltirken pilot gruplara daha fazla kullanıcı ekleyebilirsiniz (ve buna karşılık olarak bu yeni pilot kullanıcıları mevcut koruma hizmetiniz tarafından taramadan muaf tutabilirsiniz). Şimdi ne kadar çok test yaparsanız, daha sonra ilgilenmeniz gereken kullanıcı sorunları o kadar az olur. Bu "şelale" yaklaşımı kuruluşun daha büyük bölümlerine göre ayarlamaya olanak tanır ve güvenlik ekiplerinize yeni araçlara ve süreçlere uyum sağlaması için zaman verir.

- Microsoft 365, kuruluş ilkeleri tarafından yüksek güvenilirlikli kimlik avı iletilerine izin verildiğinde uyarılar oluşturur. Bu iletileri tanımlamak için aşağıdaki seçeneklere sahipsiniz:
  - [Tehdit koruması durum raporundaki](view-email-security-reports.md#threat-protection-status-report) geçersiz kılmalar.
  - İletileri tanımlamak için Tehdit Gezgini'nde filtreleyin.
  - İletileri tanımlamak için Gelişmiş Tehdit Avcılığı'nda filtreleyin.

  Yönetici gönderimleri aracılığıyla microsoft'a mümkün olan en erken şekilde hatalı pozitif sonuçları bildirin, bu hatalı pozitif sonuçların güvenli geçersiz kılmalarını yapılandırmak için [Kiracı İzin Ver/Engelle Listesi](tenant-allow-block-list.md) özelliğini kullanın.

- Gereksiz geçersiz kılmaları incelemek de iyi bir fikirdir. Başka bir deyişle, Microsoft 365'in iletilerde verdiği kararlara bakın. Microsoft365 doğru kararı verdiyse geçersiz kılma gereksinimi büyük ölçüde azalır veya ortadan kalkar.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>7. Adım: Microsoft 365 korumasını tüm kullanıcılara genişletme ve SCL=-1 posta akışı kuralını kapatma

MX kayıtlarınızı Microsoft 365'e işaret etmeye hazır olduğunuzda bu bölümdeki adımları uygulayın.

1. Pilot ilkeleri kuruluşun tamamına genişletme. Temel olarak, bunu yapmanın farklı yolları vardır:
   - [Önceden ayarlanmış güvenlik](preset-security-policies.md) ilkelerini kullanın ve kullanıcılarınızı Standart koruma profili ile Katı koruma profili arasında bölün (herkesin kapsandığından emin olun). Önceden ayarlanmış güvenlik ilkeleri, oluşturduğunuz özel ilkelerden veya varsayılan ilkelerden önce uygulanır. Tek tek pilot ilkelerinizi silmeden kapatabilirsiniz.

     Önceden ayarlanmış güvenlik ilkelerinin dezavantajı, önemli ayarları oluşturduktan sonra çoğu ayarı değiştirememenizdir.

   - Pilot sırasında oluşturduğunuz ve ayarladığınız ilkelerin kapsamını tüm kullanıcıları (örneğin, tüm etki alanlarındaki tüm alıcıları) içerecek şekilde değiştirin. Aynı türdeki birden çok ilkenin (örneğin, kimlik avı önleme ilkeleri) aynı kullanıcıya (tek tek, grup üyeliğine veya e-posta etki alanına göre) uygulanıp uygulanmadığını, yalnızca en yüksek önceliğe (en düşük öncelik numarasına) sahip ilke ayarlarının uygulandığını ve bu ilke türü için işlemenin durdurulduğunu unutmayın.

2. SCL=-1 posta akışı kuralını kapatın (silmeden kapatabilirsiniz).

3. Önceki değişikliklerin geçerli olduğunu ve Office 365 için Defender artık tüm kullanıcılar için düzgün bir şekilde etkinleştirildiğini doğrulayın. Bu noktada, Office 365 için Defender tüm koruma özelliklerinin artık tüm alıcılar için posta üzerinde işlem yapmalarına izin verilir, ancak bu posta zaten mevcut koruma hizmetiniz tarafından taranmıştır.

Daha büyük ölçekli veri kaydı ve ayarlama için bu aşamada duraklatabilirsiniz.

## <a name="step-8-switch-your-mx-records"></a>8. Adım: MX kayıtlarınızı değiştirme

> [!NOTE]
>
> - Etki alanınız için MX kaydını değiştirdiğinizde değişikliklerin İnternet'e yayılması 48 saate kadar sürebilir.
> - Daha hızlı yanıt ve olası geri alma (gerekirse) için DNS kayıtlarınızın TTL değerini düşürmenizi öneririz. Geçiş tamamlandıktan ve doğrulandıktan sonra özgün TTL değerine geri dönebilirsiniz.
> - Daha az sıklıkta kullanılan etki alanlarını değiştirmekle başlamayı düşünmelisiniz. Daha büyük etki alanlarına geçmeden önce duraklatabilir ve izleyebilirsiniz. Ancak, bunu yapsanız bile, ikincil SMTP etki alanları ilke uygulamasından önceki birincil etki alanlarına çözümlendiğinden, tüm kullanıcıların ve etki alanlarının ilkeler kapsamında olduğundan emin olmanız gerekir.
> - Tek bir etki alanı için birden çok MX kaydı teknik olarak çalışır ve bu makaledeki tüm yönergeleri izlemiş olmanız koşuluyla bölünmüş yönlendirmeye sahip olmanıza olanak sağlar. Özellikle, ilkelerin tüm kullanıcılara uygulandığından, SCL=-1 posta akışı kuralının yalnızca [Kurulum Adım 3: SCL=-1 posta akışı kuralını koruma veya oluşturma](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule) bölümünde açıklandığı gibi var olan koruma hizmetinizden geçen postalara uygulandığından emin olmanız gerekir. Ancak, bu yapılandırma sorun gidermeyi çok daha zor hale getiren bir davranış ortaya çıkarır ve bu nedenle, özellikle uzun süreler için genellikle bunu önermeyiz.
> - MX kayıtlarınızı değiştirmeden önce, koruma hizmetinden Microsoft 365'e gelen bağlayıcıda aşağıdaki ayarların etkinleştirilmediğini doğrulayın. Bağlayıcıda genellikle aşağıdaki ayarlardan biri veya daha fazlası yapılandırılır:
>   - **ve iş ortağının Office 365 ile kimlik doğrulaması yapmak için kullandığı sertifikadaki konu adının bu etki alanı adıyla** (*RestrictDomainsToCertificate) eşleşmesini* gerektirir
>   - **Bu IP adresi aralığından gönderilmeyen e-posta iletilerini reddet** (*RestrictDomainsToIPAddresses*) Bağlayıcı türü **İş Ortağı** ise ve bu ayarlardan biri açıksa, MX kayıtlarınızı değiştirdikten sonra etki alanlarınıza tüm posta teslimi başarısız olur. Devam etmeden önce bu ayarları devre dışı bırakmanız gerekir. Bağlayıcı karma için kullanılan bir şirket içi bağlayıcıysa, şirket içi bağlayıcıyı değiştirmeniz gerekmez. Ancak yine de **bir İş Ortağı** bağlayıcısının olup olmadığını de kontrol edebilirsiniz.
> - Geçerli posta ağ geçidiniz de alıcı doğrulaması sağlıyorsa, etki alanının Microsoft 365'te [Yetkili](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) olarak yapılandırılıp yapılandırılmadığını denetlemek isteyebilirsiniz. Bu, gereksiz geri dönen iletileri önleyebilir.

Hazır olduğunuzda, etki alanlarınız için MX kaydını değiştirin. Tüm etki alanlarınızı aynı anda geçirebilirsiniz. İsterseniz, önce daha az sık kullanılan etki alanlarını ve ardından geri kalanları daha sonra geçirebilirsiniz.

Herhangi bir noktada burada duraklama ve değerlendirme yapmaktan çekinmeyin. Ancak unutmayın: SCL=-1 posta akışı kuralını kapattığınızda, kullanıcıların hatalı pozitif sonuçları denetlemek için iki farklı deneyimi olabilir. Tek ve tutarlı bir deneyimi ne kadar çabuk sağlayabilirseniz, eksik bir iletiyle ilgili sorunları gidermek zorunda olan kullanıcılarınız ve yardım masası ekipleriniz o kadar mutlu olur.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler! [Office 365 için Microsoft Defender geçişinizi](migrate-to-defender-for-office-365.md#the-migration-process) tamamladınız! Bu geçiş kılavuzundaki adımları izlediğiniz için, postanın doğrudan Microsoft 365'e teslim edildiği ilk birkaç gün çok daha sorunsuz olmalıdır.

Şimdi Office 365 için Defender normal çalışmasına ve bakımına başlarsınız. Pilot sırasında karşılaştığınıza benzer ancak daha büyük ölçekte sorunları izleyin ve izleyin. Sahte [zeka içgörüleri](learn-about-spoof-intelligence.md) ve [kimliğe bürünme içgörüleri](impersonation-insight.md) en yararlı olacaktır, ancak aşağıdaki etkinlikleri normal bir durum haline getirebilirsiniz:

- Kullanıcı gönderimlerini, özellikle [de kullanıcı tarafından bildirilen kimlik avı iletilerini](automated-investigation-response-office.md) gözden geçirin
- [Tehdit koruması durum raporundaki](view-email-security-reports.md#threat-protection-status-report) geçersiz kılmaları gözden geçirin.
- Fırsatları ve riskli iletileri ayarlamak için [Gelişmiş Tehdit Avcılığı](/microsoft-365/security/defender/advanced-hunting-example) sorgularını kullanın.
