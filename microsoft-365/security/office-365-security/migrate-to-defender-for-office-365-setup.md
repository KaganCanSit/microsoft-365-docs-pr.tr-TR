---
title: "Geçiş için Microsoft Defender'Office 365 Aşama 2: Kurulum"
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
description: Üçüncü taraf koruma hizmetlerinden veya cihazdan Microsoft Defender'a üçüncü taraf koruma hizmetinden Microsoft Defender'a Office 365 uygulayın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc16da76f4b863800bb4f1e7573bbe2fa106b4cf
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014060"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Geçiş için Microsoft Defender'a Office 365 - Aşama 2: Kurulum

**Aşağıdakiler için geçerlidir:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

<br>

|[![Aşama 1: Hazırlık.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Aşama 1: Hazırlama](migrate-to-defender-for-office-365-prepare.md)|![Aşama 2: Ayarlama.](../../media/phase-diagrams/setup.png) <br> Aşama 2: Ayarlama|[![Aşama 3: Ekleme.](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Aşama 3: Ekleme](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Buradasınız!*||

Aşama **2'ye hoş geldiniz: Üçüncü** aşama **[için Microsoft Defender'a Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Pilot kullanıcılar için dağıtım grupları oluşturma](#step-1-create-distribution-groups-for-pilot-users)
2. [Kullanıcı iletisi raporlaması için kullanıcı gönderimi yapılandırma](#step-2-configure-user-submission-for-user-message-reporting)
3. [SCL=-1 posta akış kuralını koruma veya oluşturma](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Bağlayıcılar için Geliştirilmiş Filtrelemeyi Yapılandırma](#step-4-configure-enhanced-filtering-for-connectors)
5. [Pilot koruma ilkeleri oluşturma](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>1. Adım: Pilot kullanıcılar için dağıtım grupları oluşturma

Geçiş işleminizin aşağıdaki Microsoft 365 için dağıtım grupları gereklidir:

- **SCL=-1** posta akış kuralı özel durumları: Pilot kullanıcıların Office 365 koruması için Defender'ı tam olarak etkileysin, bu nedenle gelen iletilerinin Office 365 için Defender tarafından taranmış olması gerekir. Bu, pilot kullanıcılarınızı Microsoft 365'de uygun dağıtım gruplarında tanımlayarak ve bu grupları SCL=-1 posta akış kuralı için özel durumlar olarak yapılandırarak yapar.

  2. Adım'da açıklandığı gibi [: (](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)İsteğe Bağlı) Muaf pilot kullanıcıların var olan koruma hizmetiniz tarafından filtre uygulamasını geri alamanız gerekir. Bu pilot kullanıcıları var olan koruma hizmetiniz ile taramaktan muaf tutulabilirsiniz. Mevcut koruma hizmetiniz tarafından filtreleme olanağını ortadan kaldırmak ve geçiş işleminiz tamamlandıktan sonra olacakların en iyi ve en yakın gösterimi olan Office 365 için Defender'a özel olarak güvenmektir.

- **Belirli Defender for Office 365 protection özellikleri** testi: Pilot kullanıcılar için bile her şeyi bir kerede açmak istemiyoruz. Pilot kullanıcılarınız için etkili olan koruma özellikleri için aşamalı bir yaklaşım kullanmak sorun gidermeyi ve ayarlamayı çok daha kolay hale getirir. Bu yaklaşımın bizim için aşağıdaki dağıtım gruplarını öneririz:
  - **Bir Kasa Ekleri pilot grubu**: Örneğin, **MDOPilotSafeAttachments\_**
  - **Bir Kasa Bağlantılar pilot grubu**: Örneğin, **MDOPilotSafeLinks\_**
  - **Standart istenmeyen posta önleme ve kimlik** avından koruma ilkesi ayarları için pilot grup: Örneğin, **MDOPilotSpamPhishStandard\_\_**
  - **Katı istenmeyen posta önleme ve kimlik** avından koruma ilkesi ayarları için pilot grup: Örneğin, **MDOPilotSpamPhishStrict\_\_**

Netlik sağlamak için, bu makale boyunca bu belirli grup adlarını kullanacaktır, ancak kendi adlandırma kuralınızı kullanmakta özgür oluruz.

Test etmeye hazır olduğunda, bu grupları [SCL=-1 posta akışı kuralına özel durum olarak ekleyin](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Office 365 için Defender'daki çeşitli koruma özellikleri için ilkeler  oluşturdukken, bu grupları ilkenin kimlere geçerli olduğunu tanımlayan koşullar olarak kullanırsunuz.

**Notlar**:

- Standard ve Katı terimleri, önceden ayarlanmış güvenlik ilkelerde [de](recommended-settings-for-eop-and-office365.md) kullanılan önerilen güvenlik [ayarlarımız'dan gelir](preset-security-policies.md). İdeal olan, pilot kullanıcılarınızı Standart ve Katı önceden ayarlanmış güvenlik ilkelerde tanımlamanızı söyleriz, ancak bunu uygulayalarız. Neden mi? Önceden ayarlanmış güvenlik ilkelerinde (özellikle, iletilerde  alınan eylemler veya kimliğe bürünme koruma ayarlarının ayarlanması) ayarları özelleştiremeyebilirsiniz. Geçiş testniz sırasında, Office 365 için Defender'ın iletilerde ne yaptığını görmek, yapmak istediğinizin bu olduğunu doğrulamak ve bu sonuçlara izin vermek veya engellemek için ilke yapılandırmalarını ayarlamanız iyi olabilir.

  Dolayısıyla, önceden ayarlanmış güvenlik ilkelerini kullanmak yerine el ile çok benzeyen, ancak bazı durumlarda Standart ve Katı önceden ayarlanmış güvenlik ilkelerinin ayarlarından farklı olan özel ilkeler oluşturmalısınız.

- Standart veya Katı önerilen değerlerden önemli ölçüde  farklı olan ayarlarla denemeler yapmak için bu senaryolarda pilot kullanıcılar için ek ve belirli dağıtım grupları oluşturmayı ve kullanmayı göz önünde bulundurabilirsiniz. Ayarlarınızın ne kadar güvenli olduğunu görmek için Yapılandırma Çözümleyicisi'ne kullanabilirsiniz. Yönergeler için bkz. [EOP'de koruma ilkeleri için yapılandırma çözümleyicisi ve](configuration-analyzer-for-security-policies.md) Office 365.

  Çoğu kuruluş için en iyi yaklaşım, önerilen Standart ayarlarımıza yakından uygun ilkelerle başlamaktır. Kullanılabilir zaman diliminde mümkün olduğu kadar gözlem ve geri bildirimden sonra, daha sonra daha saldırgan ayarlara geçebilirsiniz. Kimliğe bürünme koruması ve Gereksiz E-posta klasörüne teslim ile karantinaya teslim arasında özelleştirme gerekli olabilir.

  Özelleştirilmiş ilkeler kullanıyorsanız, geçiş için önerilen ayarlarımızı içeren ilkeler önce  bu ilkelerin uygulandığından emin olun. Kullanıcı aynı türde birden çok ilkede tanımlanırsa (örneğin, kimlik avından koruma), kullanıcıya bu türden yalnızca bir ilke uygulanır (ilkenin öncelik değerine bağlı olarak). Daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>2. Adım: Kullanıcı gönderimi için kullanıcı gönderimi raporlaması yapılandırma

Kullanıcılar, geçişin önemli bir bölümü olan Windows için Defender'dan Office 365 pozitif veya yanlış negatifleri belirleme olanağına sahip olur.

Kullanıcıların kötü amaçlı Exchange Online kötü amaçlı değil olarak rapor iletileri alacak yeni bir posta kutusu belirtebilirsiniz. Diğer yönergeler için bkz. [Kullanıcı tarafından bildirilen ileti ayarları](user-submission.md). Bu posta kutusu, kullanıcılarının Microsoft'a gönderdiğiniz iletilerin kopyalarını almak veya posta kutusunun iletileri Microsoft'a bildirmeden engellemesini silebilir (güvenlik ekibiniz iletileri el ile analiz edip gönderebilirsiniz). Ancak, bu kesme noktası yaklaşımı hizmetin otomatik olarak ayarlamasına ve öğrenmesine izin vermez.

Ayrıca pilot uygulamanın tüm kullanıcılarının, kullanıcı gönderimi ile uyumlu bir Outlook ileti raporlama uygulamasının yüklü olduğunu da onaylamanız gerekir. Bu uygulamalar şunlardır:

- [Rapor İletisi eklentisinde](enable-the-report-message-add-in.md)
- [Rapor Kimlik Avı eklentisi](enable-the-report-phish-add-in.md)
- Burada açıklandığı gibi desteklenen üçüncü taraf raporlama [araçları](user-submission.md#third-party-reporting-tools).

Bu adımın önemini vurgulamayın. Kullanıcı gönderimlerinden gelen veriler, geçiş öncesinde ve sonrasında iyi, tutarlı bir son kullanıcı deneyimini doğrulamanız gereken geri bildirim döngüsü sağlar. Bu geri bildirim, bilgili ilke yapılandırma kararlarını amanıza ve geçişin sorunsuz şekilde gittiğini yönetiminize veriyle ilgili raporlar sağlamanıza yardımcı olur.

Tüm kuruluşun deneyiminde arkanıza alınan verilere güvenmek yerine, birden çok geçiş, tek bir negatif kullanıcı deneyimine bağlı olarak duygusal bağlı bir geçişe neden olur. Ayrıca kimlik avı benzetimlerini çalıştırdısanız, araştırma gerektirecek bir riskle karşı karşı aldıklarında sizi bilgilendirmek için kullanıcılarından gelen geri bildirimleri kullanabilirsiniz.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>3. Adım: SCL=-1 posta akış kuralını koruma veya oluşturma

Gelen e-postanız Microsoft 365'in önünde bulunan başka bir koruma hizmeti aracılığıyla yönlendirildi olduğundan, büyük olasılıkla Exchange Online'te tüm gelen postaların istenmeyen posta güven düzeyini (SCL) -1 değerine (istenmeyen posta filtrelemeyi atla) ayarlayan bir posta akış kuralınız (aktarım kuralı olarak da bilinir) vardır. Çoğu üçüncü taraf koruma hizmeti, hizmetlerini kullanmak isteyen müşteriler için bu SCL=-1 posta Microsoft 365 kuralını teşvik eder.

Microsoft filtreleme yığınını (örneğin, IP izin listesine) geçersiz kılmak için başka bir mekanizma kullanıyorsanız, Microsoft 365'a gelen tüm gelen İnternet postası üçüncü taraf koruma hizmetlerinden geldiği sürece (örneğin, IP izin  listesi) SCL=-1 posta akış kuralına geçmenizi öneririz (posta akışı doğrudan Microsoft 365'a değil).

SCL=-1 posta akışı kuralı, geçiş sırasında aşağıdaki nedenlerden dolayı önemlidir:

- Threat [Explorer'ı](email-security-in-microsoft-defender.md) kullanarak, Microsoft yığınında bulunan koruma hizmetinizin  sonuçlarını etkilemeden iletiler üzerinde hangi özelliklerin üzerinde eyleme geçyeceğini gösterebilirsiniz.
- SCL=-1 posta akışı kuralına özel durumlar yapılandırarak, Microsoft 365 filtre yığını tarafından korunanları aşamalı olarak ayarlayabilirsiniz. Özel durumlar, bu makalenin devamlarında önereceğimiz pilot dağıtım gruplarının üyeleridir.

  MX kaydınızı başka bir kuruluşa devre dışı bırakmadan önce veya bu Microsoft 365 sırasında, bu kuralı devre dışı bırakarak, Microsoft 365 tüm alıcıları için koruma yığınını tam olarak etkinleştirmeniz gerekir.

Daha fazla bilgi için bkz. Kendi iletilerin içinde istenmeyen posta güven düzeyini [(SCL) ayarlamak için posta Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Notlar**:

- İnternet postalarının var olan koruma hizmetiniz üzerinden ve doğrudan Microsoft 365'e  aynı anda aksına izin vermeyi planlıyorsanız, SCL=-1 posta akış kuralını yalnızca varolan koruma hizmetinizin üzerinden geçen postayla (istenmeyen posta filtrelemeyi atlayan posta) kısıtlamanız gerekir. Filtrelenmemiş internet postanın posta kutusunun posta kutusundan kullanıcı posta kutularına iner Microsoft 365.

  Var olan koruma hizmetiniz tarafından zaten taranmış olan postayı doğru şekilde tanımlamak için SCL=-1 posta akış kuralına bir koşul  eklersiniz. Örneğin:

  - **Bulut tabanlı koruma hizmetleri için**: Üst bilgi ve üst bilgi değerini, özel olarak kullanabilirsiniz. Üst bilgisi olan iletiler, diğer Microsoft 365. Üst bilgisi olmayan iletiler göndererek Microsoft 365
  - **Şirket içi koruma hizmetleri veya cihazları için**: Kaynak IP adreslerini kullanabilirsiniz. Kaynak IP adreslerinden gelen iletiler ip adresleri tarafından Microsoft 365. Kaynak IP adreslerinden olmayan iletiler IP adresleri tarafından Microsoft 365.

- Postanın filtrelenmiş olup olmadığını kontrol etmek için özel olarak MX kayıtlarına güvenme. Gönderenler MX kaydını kolayca yoksayabilir ve doğrudan MX'e e-posta Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>4. Adım: Bağlayıcılar için Geliştirilmiş Filtrelemeyi Yapılandırma

İlk olarak, var olan koruma hizmetinizin posta akışı için kullanılan bağlayıcıda Bağlayıcılar için Gelişmiş Filtreleme'yi [(liste](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) atlama olarak da *bilinir)* yapılandırabilirsiniz ve bu, Microsoft 365. Bağlayıcıyı tanımlamak [için Gelen iletiler](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) raporunu kullanabilirsiniz.

İnternet iletilerinin aslında nereden geldiğini görmek için Bağlayıcılar Office 365 için Defender tarafından Geliştirilmiş Filtreleme gereklidir. Bağlayıcılar için İyileştirilmiş Filtreleme, Microsoft filtreleme yığınının (özellikle de tehdit Gezgini ve Otomatik Soruşturma'daki [](anti-spoofing-protection.md)[& (AIR)](automated-investigation-response-office.md) ihlal sonrası özellikleriyle birlikte doğruluğunu büyük ölçüde iyileştirilmiştir.[](threat-explorer.md)

Bağlayıcılar için Gelişmiş Filtreleme'yi doğru etkinleştirmek için, gelen postayı Microsoft 365'e yönlendiren tüm üçüncü taraf hizmetleri ve/veya şirket içi e-posta sistemi barındırıcılarının **genel IP** \***\*\***\* adreslerini eklemeniz gerekir.

Bağlayıcılar için İyileştirilmiş Filtreleme'nin çalıştığını onaylamak için, gelen iletilerin aşağıdaki üst bilgilerden birini veya her ikisini birden içerdiğini doğrulayın:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>5. Adım: Pilot koruma ilkeleri oluşturma

Üretim ilkeleri oluşturarak, tüm kullanıcılara uygulanmasa bile Threat [Explorer](threat-explorer.md) gibi ihlal sonrası özellikleri test etmek ve Office 365 için Defender'ı güvenlik yanıtı ekibinin süreçleriyle tümleştirmeyi test etmek için bu özellikleri ekleyebilirsiniz.

> [!IMPORTANT]
> İlkeler, kullanıcılar, gruplar veya etki alanları kapsamında olabilir. Bu üç ilkeyi tek bir ilkede karma olarak karıştırmanız önerilmez, çünkü yalnızca bu üç ilkeyi de karıştıran kullanıcılar ilkenin kapsamına girilir. Pilot ilkeler için grupları veya kullanıcıları kullanmalarını öneririz. Üretim ilkeleri için etki alanlarını kullanmalarını öneririz. Yalnızca kullanıcının birincil e-posta **etki alanının** , kullanıcının ilke kapsamına girip gir olmadığını belirlemesi son derece önemlidir. Dolayısıyla, kullanıcının ikincil etki alanının MX kaydını değiştirerek, birincil etki alanının da bir ilke kapsamında olduğundan emin olun.

### <a name="create-pilot-safe-attachments-policies"></a>Ekler Kasa için pilot uygulama ilkeleri oluşturma

[Kasa,](safe-attachments.md) MX kaydınızı değiştirmeden önce Office 365 ve test etmenin en kolay olduğu Dosya Için Defender özelliğidir. Kasa aşağıdaki avantajlara sahip:

- En düşük yapılandırma.
- Hatalı pozitif sonuçlar için son derece düşük bir fırsattır.
- Kötü amaçlı yazılımdan korumayla ilgili davranışa benzer, SCL=-1 posta akış kuralı her zaman açık olur ve bundan etkilenmez.

Pilot kullanıcılarınız Kasa Ekler ilkesi oluşturun.

Önerilen ayarlar için bkz. [Ekler ilke Kasa önerilen ayarlar](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Standart ve Katı önerilerinin aynı olduğunu unutmayın. İlkeyi oluşturmak için bkz[. Ekleri Kasa ayarlama](set-up-safe-attachments-policies.md). Grubun **MDOPilotSafeAttachments\_** grubunu ilke koşulu olarak (ilkenin geçerli olduğu kişi) kullanmaya dikkat olun.

> [!IMPORTANT]
> Bugün, Ekler ilkesi için Kasa yoktur. Tüm MX kayıtlarını değiştirmeden önce, tüm kuruluşu koruyan Kasa Ekleri ilkesine sahipnizi öneririz.

### <a name="create-pilot-safe-links-policies"></a>Pilot bağlantılar Kasa oluşturma

> [!NOTE]
> Zaten kaydırılmış veya yeniden yazılmış bağlantıları kaydırmayı veya yeniden yazmayı desteklemeyiz. Geçerli koruma hizmetiniz e-posta iletilerine bağlantıları zaten kaydırıyor veya yeniden yazıyorsa, pilot kullanıcılarınız için bu özelliği kapatmanız gerekir. Bunun olmasını sağlamanın bir yolu, Bağlantılar ilkesinde diğer hizmetin URL etki alanını Kasa etmektir.
>
> Kasa bağlantılar koruması, Office kullanıcılar için geçerli olan genel bir ayardır. Belirli kullanıcılar için değil, genel olarak bu özellikleri açabilirsiniz veya kapatabilirsiniz. Daha fazla bilgi için bkz[. Kasa uygulamaları için Bağlantılar korumasını Office 365.](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal)

Pilot kullanıcılarınız Kasa Bağlantılar ilkesi oluşturun. Kasa Bağlantılarında hatalı pozitif sonuçlar için de oldukça düşüktür, ancak bu özelliği Eklere göre daha az sayıda pilot kullanıcıda test Kasa düşünebilirsiniz. Bu özellik kullanıcı deneyimini etkileye olduğundan, kullanıcıları eğitme planı yapmayı düşünebilirsiniz.

Önerilen ayarlar için bkz. Önerilen [Bağlantılar Kasa ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings). Standart ve Katı önerilerinin aynı olduğunu unutmayın. İlkeyi oluşturmak için bkz[. Bağlantı Kasa ayarlama](set-up-safe-links-policies.md). Grup **MDOPilotSafeLinks'i\_** ilke koşulu olarak (ilkenin geçerli olduğu kişi) kullanmaya dikkat olun.

> [!IMPORTANT]
> Bugün, bağlantılar ilkesi için Kasa yoktur. MX kayıtlarını değiştirmeden önce, tüm kuruluşu koruyan bir Kasa Bağlantılar ilkesine sahipnizi öneririz.

### <a name="create-pilot-anti-spam-policies"></a>Pilot istenmeyen posta önleme ilkeleri oluşturma

Pilot kullanıcılar için iki istenmeyen posta önleme ilkeleri oluşturun:

- Standart ayarları kullanan ilke. Grup **MDOPilotSpamPhishStandard\_\_** grubunu ilkenin koşulu olarak kullanın (ilkenin geçerli olduğu kişi).
- Katı ayarlarını kullanan ilke. Grup **MDOPilotSpamPhishStrict'i\_\_** ilkenin koşulu olarak kullanın (ilkenin geçerli olduğu kişi). Bu ilke, Standart ayarlara sahip ilkeden daha yüksek önceliğe (daha düşük bir sayı) sahip olmalıdır.

Önerilen Standart ve Katı ayarları için bkz[. İstenmeyen posta önleme ilkesi ayarları.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings) İlkeleri oluşturmak için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Pilot kimlik avı önleme ilkeleri oluşturma

Pilot kullanıcılar için iki kimlik avı önleme ilkeleri oluşturun:

- Aşağıda açıklanan kimliğe bürünme algılama eylemleri dışında, Standart ayarları kullanan bir ilke. Grup **MDOPilotSpamPhishStandard\_\_** grubunu ilkenin koşulu olarak kullanın (ilkenin geçerli olduğu kişi).
- Aşağıda açıklandığı gibi kimliğe bürünme algılama eylemleri dışında Katı ayarlarını kullanan bir ilke. Grup **MDOPilotSpamPhishStrict'i\_\_** ilkenin koşulu olarak kullanın (ilkenin geçerli olduğu kişi). Bu ilke, Standart ayarlara sahip ilkeden daha yüksek önceliğe (daha düşük bir sayı) sahip olmalıdır.

Hesap tanıma algılamaları için önerilen Standart eylem İletiyi alıcıların Gereksiz E-posta klasörlerine taşı'dır ve önerilen Katı eylemi de iletiyi **karantinaya almaktır**. Sonuçları gözlemlemek için akıllı ifade içgörülerini kullanın. Geçersiz kılmalar bir sonraki bölümde açıklanmıştır. Daha fazla bilgi için bkz [. EOP'de Spoof Intelligence içgörü](learn-about-spoof-intelligence.md).

Kimliğe bürünme algılamaları için, pilot ilkeler için önerilen Standart ve Katı eylemleri yoksayın. Bunun yerine, Bu **değeri kullanın Aşağıdaki ayarlar için** hiçbir eylem uygulama:

- **İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa**
- **İleti kimliğine bürünülen etki alanı olarak algılanırsa**
- **Posta kutusu zekası kimliğine bürünülen bir kullanıcı algılarsa**

Sonuçları gözlemlemek için kimliğe bürünme içgörülerini kullanın. Daha fazla bilgi için, Office 365 [için Defender'daki Kimliğe Bürünme Office 365](impersonation-insight.md).

Kimlik sahteciliğe karşı korumayı (izinler ve engellemeleri ayarlama) ayarlar ve her kimliğe bürünme koruma eylemlerini, iletileri karantinaya almak veya Gereksiz E-posta klasörüne taşımak için (Standart veya Katı önerilerine göre) açabilirsiniz. Sonuçları gözlemlemek ve ayarlarını gerekli şekilde ayarlayabilirsiniz.

Daha fazla bilgi için, aşağıdaki konulara bakın:

- [Anti-spoing protection](anti-spoofing-protection.md)
- [Kimlik avı önleme ilkelerinde kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Kimlik avı önleme ilkelerini, kimlik avı için Defender'da Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! İş için Microsoft **Defender'a** [geçiş işleminin Kurulum aşamasını Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Aşama [3: Ekleme'ye devam edin](migrate-to-defender-for-office-365-onboard.md).
