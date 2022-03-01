---
title: '1. Aşama için Microsoft Defender Office 365 ya geçiş: Hazırlanma'
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
description: Üçüncü taraf koruma hizmeti veya cihazından Üçüncü taraf koruma hizmeti veya cihazından Microsoft Defender'a Office 365 adımları.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f8a35fa7e8ac469a87861d25f45e7078eb4be940
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015352"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-1-prepare"></a>Geçiş için Microsoft Defender'a Office 365 - Aşama 1: Hazırlık

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

<br>

|![Aşama 1: Hazırlık.](../../media/phase-diagrams/prepare.png) <br> Aşama 1: Hazırlama|[![Aşama 2: Ayarlama](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Aşama 2: Ayarlama](migrate-to-defender-for-office-365-setup.md)|[![Aşama 3: Ekleme](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Aşama 3: Ekleme](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
|*Buradasınız!*|||

Aşama **1'e Hoş Geldiniz: Microsoft** **[Defender'a geçiş işleminin Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Bu geçiş aşaması aşağıdaki adımları içerir. Herhangi bir değişiklik öncesinde, öncelikle mevcut koruma hizmetinizin ayarlarının envanterini alınız. Aksi takdirde, kalan adımları herhangi bir sırada atabilirsiniz:

1. [Mevcut koruma hizmetinizin ayarlarının envanterini alın](#inventory-the-settings-at-your-existing-protection-service)
2. [Microsoft 365'te mevcut koruma yapılandırmanızı denetleme](#check-your-existing-protection-configuration-in-microsoft-365)
3. [Posta yönlendirme yapılandırmanızı denetleme](#check-your-mail-routing-configuration)
4. [İletileri farklı bir yere Microsoft 365](#move-features-that-modify-messages-into-microsoft-365)
5. [İstenmeyen posta ve toplu kullanıcı deneyimlerini tanımlama](#define-spam-and-bulk-user-experiences)
6. [Öncelik hesaplarını tanımlama ve belirleme](#identify-and-designate-priority-accounts)

## <a name="inventory-the-settings-at-your-existing-protection-service"></a>Mevcut koruma hizmetinizin ayarlarının envanterini alın

Var olan koruma hizmetinizin ayarları, kuralları, özel durumları, vb. eksiksiz bir envanterini almak iyi bir fikirdir çünkü aboneliğinizi iptal etmenizden sonra büyük olasılıkla bilgilere erişemeyebilirsiniz.

**Ancak, yeni ve gelişmiş bir hizmet için Defender'da var olan tüm özelleştirmelerinizi otomatik olarak veya rastgele yeniden Office 365.** En iyi şekilde, artık gerekli, ilgili veya işlevsel olmayan ayarlar tanıtabilirsiniz. En kötüsü, önceki özelleştirmelerden bazıları bu özelleştirmeler için Defender'da güvenlik sorunları Office 365.

Defender for Office 365'un yerel yetenekleri ve davranışınız sizin sınamanız ve gözlemniz sonunda size gereken geçersiz kılmaları ve ayarları belirler. Var olan koruma hizmetinizin ayarlarını aşağıdaki kategorilere ayırmayı yararlı bulabilirsiniz:

- **Bağlantı veya içerik filtreleme**: Büyük olasılıkla bu özelleştirmelerin büyük olasılıkla Sizin için Defender'da pek bir Office 365.
- **İşletme yönlendirme**: Yeniden oluşturmanız gereken özelleştirmelerin büyük olasılıkla bu kategoriye girer. Örneğin, posta akış kuralları (aktarım kuralları olarak da Microsoft 365 olarak Exchange), bağlayıcıları ve özel durumları birlikte kullanarak bu ayarları yeniden oluşturabilirsiniz.

Eski ayarları görme engelli bir şekilde Microsoft 365 yerine, sürekli artan kullanıcı üyeliğinin olduğu bir pilot aşama ve kurumsal iş ihtiyaçlarıyla ilgili güvenlik hususlarını dengelemeye dayalı gözlem tabanlı ayarlama içeren bir Şelale yaklaşımı öneririz.

## <a name="check-your-existing-protection-configuration-in-microsoft-365"></a>Microsoft 365'te mevcut koruma yapılandırmanızı denetleme

Daha önce de belirtildiği gibi, üçüncü taraf koruma hizmeti kullansa bile, Microsoft 365'e teslim edilen posta için tüm koruma özelliklerini tamamen kapatmanız mümkün değildir. Dolayısıyla, bir kuruluşun en azından bazı e-Microsoft 365 özellikleri yapılandırılmış olması sıra dışı değildir. Örneğin:

- Geçmişte, üçüncü taraf koruma hizmetini üçüncü taraf koruma hizmetiyle birlikte Microsoft 365. Bu bağlantıda, şu anda yok sayılan bazı koruma Microsoft 365 ve yapılandırmış olabileceğiniz gibi. Ancak bu ayarlar, siz aramada koruma özelliklerini etkinleştirmek için "aramayı çevir" Microsoft 365.
- Mevcut koruma hizmetiniz aracılığıyla yapılan hatalı pozitif Microsoft 365 (iyi posta kötü işaretlenmiş iyi posta) veya hatalı negatif (izin verilen kötü posta) için konaklama hizmetiniz olabilir.

Mevcut koruma özelliklerinizi gözden Microsoft 365 artık gerekli olan ayarları kaldırmayı veya basitleştirmeyi göz önünde bulundurabilirsiniz. Yıllar önce gerekli olan bir kural veya ilke ayarı, kuruluşun risk altında olması ve koruması için gerekli boşluklar oluşturmasını sağlar.

## <a name="check-your-mail-routing-configuration"></a>Posta yönlendirme yapılandırmanızı denetleme

- Herhangi bir tür karmaşık yönlendirme kullanıyorsanız (örneğin, Merkezi Posta [Aktarım),](/exchange/transport-options) yönlendirmenizi basitleştirmeyi ve kapsamlı bir şekilde belgeleyebilirsiniz. Dış atlamalar, özellikle de Microsoft 365 ileti alındıktan sonra, yapılandırmayı ve sorun gidermeyi karmaşıklaştırabilirsiniz.

- Giden ve geçiş posta akışı bu makalenin kapsamı dışındadır. Bununla birlikte, aşağıdaki adımlardan birini veya birkaçı da yapmak zorundayabilirsiniz:
  - E-posta gönderirken kullanmakta istediğiniz tüm etki alanlarının doğru SPF kayıtlarına sahip olduğunu doğrulayın. Daha fazla bilgi için bkz [. SPF'yi spooflun önlenmesine yardımcı olacak şekilde ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  - DkIM oturum açma kurulumunu, belirli bir Microsoft 365. Daha fazla bilgi için bkz. [Giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md).
  - Postayı doğrudan bir postadan yönlendirmiyorsanız, Microsoft 365 bağlayıcıyı kaldırarak veya değiştirerek bu yönlendirmeyi değiştirebilirsiniz.

- Şirket Microsoft 365 e-posta sunucularından e-posta geçişi yapmak, kendi başına karmaşık bir proje olabilir. Basit bir örnek olarak, iletilerin çoğunu iç alıcılara gönderen ve toplu postalarda olmayan az sayıda uygulama veya cihaz kullanılabilir. Ayrıntılar [için bu](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365) kılavuza bakın. Daha kapsamlı ortamların daha iyi düşün olması gerekir. Pazarlama e-postasına ve alıcılar tarafından istenmeyen posta olarak görülen iletilere izin verilmez.

- Office 365 için Defender'ın DMARC raporlarını toplamaya bir özelliği yok. Microsoft Akıllı [Güvenlik Birliği (MISA) kataloğunu ziyaret](https://www.microsoft.com/misapartnercatalog) edin ve daha fazla bilgi için DMARC raporlaması sunan üçüncü taraf satıcıları Microsoft 365.

## <a name="move-features-that-modify-messages-into-microsoft-365"></a>İletileri farklı bir yere Microsoft 365

İletileri herhangi bir yolla değiştirerek tüm özelleştirmeleri veya özellikleri başka bir Microsoft 365. Örneğin, var olan koruma hizmetiniz dış **gönderenlerden** gelen iletilerin konu veya ileti gövdesine bir Dış etiket ekler. Bağlantı kaydırma özelliği, bazı iletilerde sorunlara da neden olur. Bugün böyle bir özellik kullanıyorsanız, sorunları en aza indirmek için alternatif olarak Bağlantıların Kasa önceliklerini belirlemelisiniz.

Var olan koruma hizmetinizin ileti değiştirme özelliklerini kapatmıyorsanız, aşağıdaki negatif sonuçların yanıtlarını Microsoft 365:

- DKIM bozacak. Tüm gönderenler DKIM'ye güvenmez, ancak bunu yapanlar kimlik doğrulamayı başarısız olur.
- [Bu kılavuzun sonraki](anti-spoofing-protection.md) sayfalarındaki akıllı ifade ve ayar adımı düzgün çalışmaz.
- Büyük olasılıkla çok sayıda yanlış pozitif sonuç alırsınız (iyi posta kötü olarak işaretlenir).

E-postada dış Microsoft 365 yeniden oluşturmak için aşağıdaki seçeneklere sahipsiniz:

- İlk [Outlook ipucuyla birlikte, dış gönderenin](https://techcommunity.microsoft.com/t5/exchange-team-blog/native-external-sender-callouts-on-email-in-outlook/ba-p/2250098) arama [özelliğini de kullanabilirsiniz](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- Posta akış kuralları (aktarım kuralları olarak da bilinir). Daha fazla bilgi için bkz. Kuruluş genelindeki ileti uyarılarını, imzaları, alt bilgileri veya [üst bilgileri Exchange Online](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

Microsoft, yakın gelecekte Kimliği Doğrulanmış Alınan Zincir (ARC) standardını desteklemek için sektörle birlikte çalışıyor. Geçerli posta ağ geçidi sağlayıcınızda etkinleştirilmiş ileti değiştirme özelliklerini bırakmak isterseniz, bu standarda destek olmak için planlarıyla ilgili olarak onlarla bağlantı kurmanızı öneririz.

## <a name="account-for-any-active-phishing-simulations"></a>Etkin kimlik avı benzetimleri için hesap

Etkin üçüncü taraf kimlik avı benzetimleri varsa iletilerin, bağlantıların ve eklerin, kimlik avı için Defender tarafından kimlik avı olarak tanımlardan birini Office 365. Daha fazla bilgi için bkz [. Gelişmiş teslim ilkesinde üçüncü taraf kimlik avı benzetimlerini yapılandırma](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).

## <a name="define-spam-and-bulk-user-experiences"></a>İstenmeyen posta ve toplu kullanıcı deneyimlerini tanımlama

- **Karantina veya Gereksiz E-posta klasörüne** teslim edin: Kötü amaçlı ve kesinlikle riskli iletiler için doğal ve önerilen yanıt, iletileri karantinaya almaktır. Ancak, kullanıcılarının istenmeyen posta ve toplu posta (gri posta olarak da bilinir) gibi daha az zararlı iletileri işlemelerini *nasıl sağlarsınız*? Bu tür iletiler kullanıcı Gereksiz E-posta klasörlerine teslim edilecek mi?

  Standart güvenlik ayarlarımız ile, bu daha az riskli iletileri genellikle Gereksiz E-posta klasörüne teslim etmiş oluruz. Bu davranış, kullanıcıların Gereksiz E-posta klasörlerinde eksik iletileri denetlemelerine ve bu iletilerin kendilerinin kurtarılmalarına neden olan birçok tüketici e-posta teklifine benzer. Ya da kullanıcı bilerek bir bülten veya pazarlama postası için kayıt oldusa, aboneliği iptal etmek veya göndereni kendi posta kutusu için engellemeyi seçebilir.

  Bununla birlikte, birçok kurumsal kullanıcı Gereksiz E-posta klasörlerinde çok az posta (varsa) posta almak için kullanılır. Bunun yerine, bu kurumsal kullanıcılar eksik iletileri için karantinayı denetlemeye kullanılır. Karantinada karantina bildirimleri, bildirim sıklığı ve iletileri görüntülemek ve serbest bırakmak için gereken izinler ile ilgili sorunlar ortaya çıkar.

  - Etki Alanı Anahtarları Tanımlanan Posta (DKIM) bozacak.
  - [Akıllı ifade doğru](anti-spoofing-protection.md) çalışmaz.
  - Büyük olasılıkla çok sayıda yanlış pozitif sonuç alırsınız (iyi posta kötü olarak işaretlenir).

  Sonuçta, e-postanın Gereksiz E-posta klasörüne teslimini karantinaya almak istemeniz sizin kararınızdır. Ancak, bu önemli bir sorundur: Office 365 için Defender deneyimi kullanıcılarınızı eskiden kullandığından farklı olursa, bunları bilgilendirmeniz ve temel eğitim sağlamanız gerekir. Pilot uygulamayla edinen eğitimleri bir hale dahil edin ve kullanıcıların e-posta teslimi için her yeni davranışa hazır olduğundan emin olun.

- **İstenilen toplu posta ve istenmeyen toplu posta: Birçok** koruma sistemi kullanıcıların kendileri için toplu e-postaya izin vermelerini veya engellemelerini sağlar. Bu ayarlar Microsoft 365'a kolayca geçirilmez, bu nedenle VIP'ler ve personeliyle birlikte çalışarak, Microsoft 365.

  Bugün Microsoft 365, bazı toplu postaları (örneğin, bültenler) ileti kaynağına bağlı olarak güvenli olarak düşünebilirsiniz. Bu "güvenli" kaynaklardan gelen postalar şu anda toplu olarak işaretli değil (toplu şikayet düzeyi veya BCL 0 veya 1'tir), bu nedenle bu kaynaklardan gelen postaları genel olarak engellemek zordur. Çoğu kullanıcı için çözüm, onlardan bu toplu iletilerin aboneliğini tek tek iptallerini istemek veya Outlook'i kullanarak göndereni engellemektir. Ancak bazı kullanıcılar toplu iletileri engellemeyi veya toplu mesaj aboneliklerini iptal eder.

  TOPLU e-postayı filtreleyene posta akış kuralları, VIP kullanıcılar bunu kendileri yönetmek isteyene kadar yararlı olabilir. Daha fazla bilgi için bkz [. Toplu e-postaları filtrelemek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-filter-bulk-mail).

## <a name="identify-and-designate-priority-accounts"></a>Öncelik hesaplarını tanımlama ve belirleme

Özellik sizin için kullanılabilirse, **öncelik hesapları** ve **kullanıcı etiketleri** önemli kullanıcılarınızı tanımlamanıza yardımcı Microsoft 365 şekilde raporlarda dikkati ortaya çıkarlar. Daha fazla bilgi için bkz[. Windows için Microsoft Defender'da Office 365](user-tags.md) [ve öncelik hesaplarını yönetme ve izleme](/microsoft-365/admin/setup/priority-accounts).

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! Microsoft **Defender'a geçiş** [işleminin Hazırlık aşamasını tamamladınız ve Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Aşama [2: Kurulum'a devam edin](migrate-to-defender-for-office-365-setup.md).
