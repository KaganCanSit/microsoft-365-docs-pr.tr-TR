---
title: "Office 365 için Microsoft Defender Aşama 2'ye geçiş: Kurulum"
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
description: Üçüncü taraf koruma hizmetinden veya cihazından Office 365 için Microsoft Defender korumasına geçişe başlamak için adımları uygulayın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 34e975be9a937177706fd7db6605d2ef25edcad3
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043555"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Office 365 için Microsoft Defender Geçiş - 2. Aşama: Kurulum

**Şunlar için geçerlidir:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

<br>

|[![1. Aşama: Hazırlanın.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Aşama 1: Hazırlık](migrate-to-defender-for-office-365-prepare.md)|![2. Aşama: Ayarlama.](../../media/phase-diagrams/setup.png) <br> Aşama 2: Kurulum|[![3. Aşama: Ekleme.](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Aşama 3: Katılım](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Buradasınız!*||

**2. Aşama:** **[Office 365 için Microsoft Defender'a geçiş](migrate-to-defender-for-office-365.md#the-migration-process)** kurulumunuza hoş geldiniz! Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Pilot kullanıcılar için dağıtım grupları oluşturma](#step-1-create-distribution-groups-for-pilot-users)
2. [Kullanıcı ileti raporlaması için kullanıcı gönderimini yapılandırma](#step-2-configure-user-submission-for-user-message-reporting)
3. [SCL=-1 posta akışı kuralını koruma veya oluşturma](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Bağlayıcılar için Gelişmiş Filtrelemeyi Yapılandırma](#step-4-configure-enhanced-filtering-for-connectors)
5. [Pilot koruma ilkeleri oluşturma](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>1. Adım: Pilot kullanıcılar için dağıtım grupları oluşturma

Geçişinizin aşağıdaki yönleri için dağıtım grupları Microsoft 365 gereklidir:

- **SCL=-1 posta akışı kuralı için özel durumlar**: Pilot kullanıcıların Office 365 için Defender korumanın tüm etkisini elde etmelerini istiyorsunuz, bu nedenle gelen iletilerinin Office 365 için Defender tarafından taranması gerekir. Bunu yapmak için pilot kullanıcılarınızı Microsoft 365'deki uygun dağıtım gruplarında tanımlayıp bu grupları SCL=-1 posta akışı kuralına özel durumlar olarak yapılandırabilirsiniz.

  [Ekleme 2. Adım: (İsteğe bağlı) Pilot kullanıcıları mevcut koruma hizmetinize göre filtrelemeden](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service) muaf tutma bölümünde açıklandığı gibi, aynı pilot kullanıcıları mevcut koruma hizmetiniz tarafından taramaktan muaf tutmanız gerekir. Mevcut koruma hizmetinize göre filtreleme olasılığını ortadan kaldırmak ve yalnızca Office 365 için Defender güvenmek, geçişiniz tamamlandıktan sonra gerçekleşeceklerin en iyi ve en yakın gösterimidir.

- **Belirli Office 365 için Defender koruma özelliklerini test** etme: Pilot kullanıcılar için bile her şeyi aynı anda açmak istemezsiniz. Pilot kullanıcılarınız için geçerli olan koruma özellikleri için aşamalı bir yaklaşım kullanmak sorun gidermeyi ve ayarlamayı çok daha kolay hale getirir. Bu yaklaşımı göz önünde bulundurarak aşağıdaki dağıtım gruplarını öneririz:
  - **Kasa Ekler pilot grubu**: Örneğin, **MDOPilot\_SafeAttachments**
  - **Kasa Bağlantıları pilot grubu**: Örneğin, **MDOPilot\_SafeLinks**
  - **Standart istenmeyen posta önleme ve kimlik avı önleme ilkesi ayarları için bir pilot grup**: Örneğin, **MDOPilot\_İstenmeyen PostaPhish\_Standard**
  - **Katı istenmeyen posta önleme ve kimlik avı önleme ilkesi ayarları için bir pilot grup**: Örneğin, **MDOPilot\_İstenmeyen Posta Katı\_**

Netlik sağlamak için bu makalenin tamamında bu belirli grup adlarını kullanacağız, ancak kendi adlandırma kuralınızı kullanabilirsiniz.

Test etmeye hazır olduğunuzda, bu grupları [SCL=-1 posta akışı kuralına](#step-3-maintain-or-create-the-scl-1-mail-flow-rule) özel durumlar olarak ekleyin. Office 365 için Defender'deki çeşitli koruma özellikleri için ilkeler oluştururken, ilkenin kime uygulanacağını tanımlayan koşullar olarak bu grupları kullanacaksınız.

**Notlar**:

- Standart ve Katı terimleri, [önceden belirlenmiş güvenlik ilkelerinde](preset-security-policies.md) de kullanılan [önerilen güvenlik ayarlarımızdan](recommended-settings-for-eop-and-office365.md) gelir. İdeal olarak, pilot kullanıcılarınızı Standart ve Katı önceden ayarlanmış güvenlik ilkeleri içinde tanımlamanızı söyleyebiliriz, ancak bunu yapamayız. Neden mi? Önceden ayarlanmış güvenlik ilkelerindeki (özellikle iletilerde gerçekleştirilen eylemler) ayarları özelleştiremediğiniz için. Geçiş testi sırasında, Office 365 için Defender iletilere ne yapacağını görmek, bunun olmasını istediğinizi doğrulamak ve bu sonuçlara izin vermek veya bunları önlemek için ilke yapılandırmalarını ayarlamak isteyebilirsiniz.

  Bu nedenle, önceden ayarlanmış güvenlik ilkelerini kullanmak yerine, ayarlara çok benzeyen ancak bazı durumlarda Standart ve Katı ön ayarlı güvenlik ilkeleri ayarlarından farklı olan özel ilkeleri el ile oluşturacaksınız.

- Standart veya Katı önerilen değerlerimizden **önemli ölçüde** farklı ayarlarla denemeler yapmak istiyorsanız, bu senaryolarda pilot kullanıcılar için ek ve belirli dağıtım grupları oluşturmayı ve kullanmayı göz önünde bulundurmalısınız. Ayarlarınızın ne kadar güvenli olduğunu görmek için Yapılandırma Çözümleyicisi'ni kullanabilirsiniz. Yönergeler için bkz[. EOP ve Office 365 için Microsoft Defender koruma ilkeleri için yapılandırma çözümleyicisi](configuration-analyzer-for-security-policies.md).

  Çoğu kuruluş için en iyi yaklaşım, önerilen Standart ayarlarımızla yakından uyumlu ilkelerle başlamaktır. Kullanılabilir zaman diliminizde yapabileceğiniz kadar fazla gözlem ve geri bildirimden sonra, daha sonra daha agresif ayarlara geçebilirsiniz. Kimliğe bürünme koruması ve Gereksiz E-posta klasörüne teslim ile karantinaya teslim için özelleştirme gerekebilir.

  Özelleştirilmiş ilkeler kullanıyorsanız, geçiş için önerilen ayarları içeren ilkeler _öncesinde_ uygulandığından emin olmanız yeterlidir. Bir kullanıcı aynı türdeki birden çok ilkede (örneğin, kimlik avından koruma) tanımlanırsa, kullanıcıya yalnızca bir ilke uygulanır (ilkenin öncelik değerine göre). Daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>2. Adım: Kullanıcı iletisi raporlaması için kullanıcı gönderimini yapılandırma

Kullanıcıların Office 365 için Defender hatalı pozitifleri veya hatalı negatifleri tanımlama özelliği geçişin önemli bir parçasıdır.

Kullanıcıların kötü amaçlı veya kötü amaçlı olarak bildirdiği iletileri almak için bir Exchange Online posta kutusu belirtebilirsiniz. Daha fazla yönerge için bkz. [Kullanıcı tarafından bildirilen ileti ayarları](user-submission.md). Bu posta kutusu, kullanıcılarınızın Microsoft'a gönderdiği iletilerin kopyalarını alabilir veya posta kutusu iletileri Microsoft'a bildirmeden kesebilir (güvenlik ekibiniz iletileri el ile analiz edebilir ve gönderebilir). Ancak, bu kesme yaklaşımı hizmetin otomatik olarak ayarlayıp öğrenmesine izin vermez.

Ayrıca pilottaki tüm kullanıcıların, kullanıcı gönderimiyle uyumlu Outlook'da desteklenen bir ileti raporlama uygulaması yüklü olduğunu da onaylamanız gerekir. Bu uygulamalar şunlardır:

- [Rapor İletisi eklentisi](enable-the-report-message-add-in.md)
- [Rapor Kimlik Avı eklentisi](enable-the-report-phish-add-in.md)
- [Burada](user-submission.md#third-party-reporting-tools) açıklandığı gibi desteklenen üçüncü taraf raporlama araçları.

Bu adımın önemini hafife almayın. Kullanıcı gönderimlerinden alınan veriler, geçiş öncesinde ve sonrasında iyi ve tutarlı bir son kullanıcı deneyimini doğrulamanız için gereken geri bildirim döngüsünü sağlar. Bu geri bildirim, bilinçli ilke yapılandırma kararları vermenize ve yönetiminize geçişin sorunsuz bir şekilde gittiğine ilişkin veri destekli raporlar sağlamanıza yardımcı olur.

Tüm kuruluşun deneyimi tarafından yedeklenen verilere güvenmek yerine birden fazla geçiş, tek bir olumsuz kullanıcı deneyimine dayalı duygusal spekülasyonlara neden oldu. Ayrıca, kimlik avı simülasyonları çalıştırıyorsanız, araştırma gerektirebilecek riskli bir şey gördüklerinde sizi bilgilendirmek için kullanıcılarınızdan gelen geri bildirimleri kullanabilirsiniz.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>3. Adım: SCL=-1 posta akışı kuralını koruma veya oluşturma

Gelen e-postanız Microsoft 365 önünde duran başka bir koruma hizmeti aracılığıyla yönlendirildiğinden, Exchange Online tüm gelen postaların istenmeyen posta güvenilirlik düzeyini (SCL) -1 değerine ayarlayan (istenmeyen posta filtrelemeyi atla) bir posta akışı kuralınız (aktarım kuralı olarak da bilinir) büyük olasılıkla vardır. Üçüncü taraf koruma hizmetlerinin çoğu, hizmetlerini kullanmak isteyen Microsoft 365 müşteriler için bu SCL=-1 posta akışı kuralını teşvik edin.

Microsoft filtreleme yığınını geçersiz kılmak için başka bir mekanizma (örneğin, ip izin listesi) kullanıyorsanız, Microsoft 365 gelen tüm internet postaları üçüncü taraf koruma hizmetinden geldiği **sürece** (doğrudan İnternet'ten Microsoft 365'a posta akışı yapılmaz) SCL=-1 posta akışı kuralına geçmenizi öneririz.

Geçiş sırasında SCL=-1 posta akışı kuralı aşağıdaki nedenlerle önemlidir:

- Microsoft *yığınındaki* hangi özelliklerin mevcut koruma hizmetinizin sonuçlarını etkilemeden iletiler üzerinde işlem yapacağını görmek için [Tehdit Gezgini'ni](email-security-in-microsoft-defender.md) kullanabilirsiniz.
- SCL=-1 posta akışı kuralına özel durumlar yapılandırarak kimlerin Microsoft 365 filtreleme yığını tarafından korunduğunu aşamalı olarak ayarlayabilirsiniz. Özel durumlar, bu makalenin ilerleyen bölümlerinde önerdiğimiz pilot dağıtım gruplarının üyeleri olacaktır.

  MX kaydınızın Microsoft 365 tam geçişi öncesinde veya sırasında, kuruluşunuzdaki tüm alıcılar için Microsoft 365 koruma yığınının tam korumasını açmak için bu kuralı devre dışı bırakacaksınız.

Daha fazla bilgi için bkz. [Exchange Online iletilerde istenmeyen posta güvenilirlik düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Notlar**:

- İnternet postasının mevcut koruma hizmetiniz üzerinden **ve** doğrudan Microsoft 365 aynı anda akmasına izin vermek istiyorsanız, SCL=-1 posta akışı kuralını (istenmeyen posta filtrelemeyi atlayan posta) yalnızca mevcut koruma hizmetinizden geçen postalarla kısıtlamanız gerekir. Microsoft 365'da kullanıcı posta kutularına filtrelenmemiş internet postası girişini istemezsiniz.

  Mevcut koruma hizmetiniz tarafından zaten taranmış postaları doğru şekilde tanımlamak için, SCL=-1 posta akışı kuralına bir koşul ekleyebilirsiniz. Örneğin:

  - **Bulut tabanlı koruma hizmetleri için**: Kuruluşunuza özgü bir üst bilgi ve üst bilgi değeri kullanabilirsiniz. Üst bilgi içeren iletiler Microsoft 365 tarafından taranmıyor. Üst bilgi içermeyen iletiler Microsoft 365 tarafından taranır
  - **Şirket içi koruma hizmetleri veya cihazları için**: Kaynak IP adreslerini kullanabilirsiniz. Kaynak IP adreslerinden gelen iletiler Microsoft 365 tarafından taranmıyor. Kaynak IP adreslerinden olmayan iletiler Microsoft 365 tarafından taranır.

- Postanın filtrelenip filtrelenmediğini denetlemek için yalnızca MX kayıtlarına güvenmeyin. Gönderenler MX kaydını kolayca yoksayabilir ve doğrudan Microsoft 365 e-posta gönderebilir.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>4. Adım: Bağlayıcılar için Gelişmiş Filtrelemeyi Yapılandırma

İlk yapmanız gereken, var olan koruma hizmetinizden Microsoft 365'a posta akışı için kullanılan bağlayıcıda [Bağlayıcılar için Gelişmiş Filtreleme](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) 'yi (*listelemeyi atlama* olarak da bilinir) yapılandırmaktır. Bağlayıcıyı tanımlamaya yardımcı olması için [Gelen iletiler raporunu](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) kullanabilirsiniz.

Office 365 için Defender tarafından İnternet iletilerinin nereden geldiğini görmek için Bağlayıcılar için Gelişmiş Filtreleme gereklidir. Bağlayıcılar için İyileştirilmiş Filtreleme, Microsoft filtreleme yığınının (özellikle [kimlik sahtekarlığı zekasının](anti-spoofing-protection.md) yanı sıra [Tehdit Gezgini](threat-explorer.md) ve [Otomatik Araştırma & Yanıtı (AIR)](automated-investigation-response-office.md)'daki ihlal sonrası özelliklerin doğruluğunu büyük ölçüde artırır.

Bağlayıcılar için Gelişmiş Filtreleme'yi doğru bir şekilde etkinleştirmek için, gelen postaları \*\* Microsoft 365 yönlendiren **tüm\*\*** üçüncü taraf hizmetlerin ve/veya şirket içi e-posta sistemi konaklarının **genel** IP adreslerini eklemeniz gerekir.

Bağlayıcılar için Gelişmiş Filtreleme'nin çalıştığını onaylamak için, gelen iletilerin aşağıdaki üst bilgilerden birini veya her ikisini birden içerdiğini doğrulayın:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>5. Adım: Pilot koruma ilkeleri oluşturma

Tüm kullanıcılara uygulanmamış olsalar bile üretim ilkeleri oluşturarak [Tehdit Gezgini](threat-explorer.md) gibi ihlal sonrası özellikleri test edebilir ve Office 365 için Defender güvenlik yanıtı ekibinizin süreçleriyle tümleştirmeyi test edebilirsiniz.

> [!IMPORTANT]
> İlkelerin kapsamı kullanıcılar, gruplar veya etki alanları olabilir. Yalnızca üçüyle eşleşen kullanıcılar ilkenin kapsamına gireceği için üçünün de tek bir ilkede karıştırılması önerilmez. Pilot ilkeler için grupları veya kullanıcıları kullanmanızı öneririz. Üretim ilkeleri için etki alanlarını kullanmanızı öneririz. Kullanıcının ilke kapsamında olup olmadığını **yalnızca** kullanıcının birincil e-posta etki alanının belirlediğini anlamak son derece önemlidir. Bu nedenle, kullanıcının ikincil etki alanı için MX kaydını değiştirirseniz, birincil etki alanının da bir ilke kapsamında olduğundan emin olun.

### <a name="create-pilot-safe-attachments-policies"></a>Pilot Kasa Ekler ilkeleri oluşturma

[Kasa Ekler](safe-attachments.md), MX kaydınızı değiştirmeden önce etkinleştirmek ve test etmek için en kolay Office 365 için Defender özelliktir. Kasa Ekler aşağıdaki avantajlara sahiptir:

- Minimum yapılandırma.
- Hatalı pozitiflerin son derece düşük olma olasılığı.
- Her zaman açık olan ve SCL=-1 posta akışı kuralından etkilenmeyen kötü amaçlı yazılımdan koruma davranışına benzer.

Pilot kullanıcılarınız için bir Kasa Ekler ilkesi oluşturun.

Önerilen ayarlar için bkz. [Önerilen Kasa Ekler ilkesi ayarları](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Standart ve Katı önerilerin aynı olduğunu unutmayın. İlkeyi oluşturmak için bkz. [Kasa Ekler ilkelerini ayarlama](set-up-safe-attachments-policies.md). İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SafeAttachments** grubunu kullandığınızdan emin olun.

> [!IMPORTANT]
> Bugün, Varsayılan Kasa Ekler ilkesi yoktur. MX kayıtlarını değiştirmeden önce, kuruluşun tamamını koruyan bir Kasa Ekleri ilkeniz olmasını öneririz.

### <a name="create-pilot-safe-links-policies"></a>Pilot Kasa Bağlantıları ilkeleri oluşturma

> [!NOTE]
> Zaten sarmalanmış veya yeniden yazılmış bağlantıları sarmalama veya yeniden yazma desteğimiz yok. Geçerli koruma hizmetiniz e-posta iletilerindeki bağlantıları zaten sarmalar veya yeniden yazarsa, pilot kullanıcılarınız için bu özelliği kapatmanız gerekir. Bunun olmamasını sağlamanın bir yolu, Kasa Bağlantıları ilkesinde diğer hizmetin URL etki alanını dışlamaktır.
>
> Kasa Desteklenen Office uygulamaları için bağlantı koruması, tüm lisanslı kullanıcılar için geçerli olan genel bir ayardır. Belirli kullanıcılar için değil, genel olarak açabilir veya kapatabilirsiniz. Daha fazla bilgi için bkz[. Office 365 uygulamalar için Kasa Bağlantıları korumasını yapılandırma](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Pilot kullanıcılarınız için bir Kasa Bağlantıları ilkesi oluşturun. Kasa Bağlantılarında hatalı pozitif sonuç olasılığı da oldukça düşüktür, ancak özelliği Kasa Ekler'e göre daha az sayıda pilot kullanıcıda test etmeyi düşünmelisiniz. Özellik kullanıcı deneyimini etkilediğinden, kullanıcıları eğitmek için bir plan düşünmelisiniz.

Önerilen ayarlar için bkz. [Önerilen Kasa Bağlantılar ilke ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings). Standart ve Katı önerilerin aynı olduğunu unutmayın. İlkeyi oluşturmak için bkz. [Kasa Bağlantıları ilkelerini ayarlama](set-up-safe-links-policies.md). İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SafeLinks** grubunu kullandığınızdan emin olun.

> [!IMPORTANT]
> Bugün, Varsayılan Kasa Bağlantıları ilkesi yoktur. MX kayıtlarını değiştirmeden önce, kuruluşun tamamını koruyan bir Kasa Bağlantıları ilkeniz olmasını öneririz.

### <a name="create-pilot-anti-spam-policies"></a>Pilot istenmeyen posta önleme ilkeleri oluşturma

Pilot kullanıcılar için iki istenmeyen posta önleme ilkesi oluşturun:

- Standart ayarları kullanan bir ilke. İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SpamPhish\_Standard** grubunu kullanın.
- Katı ayarları kullanan bir ilke. İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SpamPhish\_Strict** grubunu kullanın. Bu ilke, Standart ayarlara sahip ilkeden daha yüksek önceliğe (daha düşük sayıya) sahip olmalıdır.

Önerilen Standart ve Katı ayarlar için bkz. [Önerilen istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). İlkeleri oluşturmak için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Pilot kimlik avı önleme ilkeleri oluşturma

Pilot kullanıcılar için iki kimlik avı önleme ilkesi oluşturun:

- Aşağıda açıklandığı gibi kimliğe bürünme algılama eylemleri dışında Standart ayarları kullanan bir ilke. İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SpamPhish\_Standard** grubunu kullanın.
- Aşağıda açıklandığı gibi kimliğe bürünme algılama eylemleri dışında Katı ayarları kullanan bir ilke. İlkenin koşulu olarak (ilkenin uygulandığı kişiler) **MDOPilot\_SpamPhish\_Strict** grubunu kullanın. Bu ilke, Standart ayarlara sahip ilkeden daha yüksek önceliğe (daha düşük sayıya) sahip olmalıdır.

Sahtekarlık algılamaları için önerilen Standart eylem, **İletiyi alıcıların Gereksiz E-posta klasörlerine taşı** eylemidir ve önerilen Katı eylem **iletiyi karantinaya al'dır**. Sonuçları gözlemlemek için sahte zeka içgörülerini kullanın. Geçersiz kılmalar sonraki bölümde açıklanmıştır. Daha fazla bilgi için bkz [. EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md).

Kimliğe bürünme algılamaları için pilot ilkeler için önerilen Standart ve Katı eylemleri yoksayın. Bunun yerine, aşağıdaki ayarlar için **Hiçbir eylem uygulama** değerini kullanın:

- **İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa**
- **İleti kimliğine bürünülen etki alanı olarak algılanırsa**
- **Posta kutusu zekası kimliğine bürünülen bir kullanıcı algılarsa**

Sonuçları gözlemlemek için kimliğe bürünme içgörülerini kullanın. Daha fazla bilgi için bkz[. Office 365 için Defender'de Kimliğe Bürünme içgörüleri](impersonation-insight.md).

Kimlik sahtekarlığı korumasını ayarlayacak (izin ve blokları ayarla) ve iletileri karantinaya almak veya Gereksiz E-posta klasörüne taşımak için her kimliğe bürünme koruma eylemini açacaksınız (Standart veya Katı önerilere göre). Sonuçları gözlemleyebilir ve ayarlarını gerektiği gibi ayarlayabilirsiniz.

Daha fazla bilgi için, aşağıdaki konulara bakın:

- [Kimlik sahtekarlığına karşı koruma](anti-spoofing-protection.md)
- [Kimlik avı önleme ilkelerinde kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırın](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! [Office 365 için Microsoft Defender'a geçişinizin Kurulum aşamasını](migrate-to-defender-for-office-365.md#the-migration-process) tamamladınız!

- 3. [Aşama: Ekleme'ye](migrate-to-defender-for-office-365-onboard.md) geçin.
