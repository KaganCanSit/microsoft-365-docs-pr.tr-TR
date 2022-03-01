---
title: İstenmeyen posta filtresi ilkelerini yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 316544cb-db1d-4c25-a5b9-c73bbcf53047
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, EOP'de (EOP) istenmeyen posta önleme ilkelerini görüntülemeyi, oluşturma Exchange Online Protection ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1ac240f402d230362cb33ea818e62c1e0629eb39
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015569"
---
# <a name="configure-anti-spam-policies-in-eop"></a>EOP'de istenmeyen posta önleme ilkelerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection Exchange Online Protection EOP (EOP) kuruluşlarına gelen Exchange Online e-posta iletileri, EOP tarafından istenmeyen postalara karşı otomatik olarak korunur. EOP, istenmeyen postalara karşı genel savunmanın bir parçası olarak istenmeyen posta önleme ilkelerini (istenmeyen posta filtresi ilkeleri veya içerik filtresi ilkeleri olarak da bilinir) kullanır. Daha fazla bilgi için bkz. [İstenmeyen posta koruması](anti-spam-protection.md).

Yöneticiler, varsayılan istenmeyen posta önleme ilkesi  görüntüleyemez, düzenleyebilir ve yapılandırabilirsiniz (ancak silemezler). Daha ayrıntılı bilgi için, aynı zamanda organizasyonu kullanan belirli kullanıcılara, gruplara veya etki alanlarına uygulanacak özel istenmeyen posta önleme ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliğe sahiptir, ancak özel ilkelerinizin önceliğini (çalışma sırası) değiştirebilirsiniz.

Microsoft 365 Defender portalında veya PowerShell'de (Microsoft 365 posta kutuları olan Microsoft 365 kuruluşları için Exchange Online Exchange Online PowerShell'de; istenmeyen posta önlemeye gerek kalmadan kuruluşlar için tek başına EOP PowerShell Exchange Online  posta kutuları).

İstenmeyen posta önleme ilkesi temel öğeleri:

- **İstenmeyen posta** filtresi ilkesi: İstenmeyen posta filtreleme kararlarını ve bildirim seçeneklerinin eylemlerini belirtir.
- **İstenmeyen posta** filtresi kuralı: İstenmeyen posta filtresi ilkesi için önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Bu iki öğe arasındaki fark, portalda istenmeyen posta önleme İlkelerini yönetirken belirgin Microsoft 365 Defender değildir:

- İstenmeyen posta önleme ilkesi  oluştururken, aslında bir istenmeyen posta filtresi kuralı ve ilişkili istenmeyen posta filtresi ilkesi aynı anda her ikisi için de aynı adı kullanır.
- İstenmeyen posta önleme ilkesi değiştirildiğinde, ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri istenmeyen posta filtresi kuralını değiştirir. Diğer tüm ayarlar ilişkili istenmeyen posta filtresi ilkesini değiştirir.
- İstenmeyen posta önleme ilkesi kaldırılan, istenmeyen posta filtresi kuralı ve ilişkili istenmeyen posta filtresi ilkesi kaldırılır.

PowerShell Exchange Online tek başına EOP PowerShell'de, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu [makalenin devam Exchange Online PowerShell veya tek başına EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) kullanarak istenmeyen posta önleme ilkelerini yapılandırmak için kullanma bölümüne bakın.

Her kuruluşun, şu özelliklere sahip Varsayılan adlı yerleşik istenmeyen posta önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş istenmeyen posta filtresi kuralı (alıcı filtreleri) her ne kadar ilke kuruluşta yer alan tüm alıcılara uygulanır.
- İlke, değiştiriy **olmadığınız** en düşük özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Sizin kendi özel ilkeleriniz her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **değeri IsDefault** özelliğine `True`sahip) ve varsayılan ilkeyi silemezsiniz.

İstenmeyen posta filtrelemenin etkisini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha sıkı ayarlarla, özel istenmeyen posta önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - İstenmeyen posta önleme ilkeleri eklemek, değiştirmek ve silmek için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olun**.
  - İstenmeyen posta önleme ilkelerine salt okunur erişim için, Genel Okuyucu veya Güvenlik **Okuyucusu** rol **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- İstenmeyen posta önleme ilkeleri için önerilen ayarlarımız için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- İstenmeyen posta filtrelemeyi tamamen kapatabilirsiniz, ancak gelen iletide istenmeyen posta filtrelemenin çoğunu atlamak için (örneğin, e-postayı üçüncü taraf koruma hizmeti veya cihaz üzerinden Microsoft 365'a teslim etmek için) bir posta akış kuralı (aktarım kuralı olarak da bilinir) kullanabilirsiniz. Daha fazla bilgi için bkz [. İletilerde istenmeyen posta güven düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Yüksek güven kimlik avı iletilerine filtre uygulanmış olarak devam ediyor. EOP'nin diğer özellikleri etkilenmez (örneğin, iletiler her zaman kötü amaçlı yazılım için taranır).
  - SecOps posta kutuları veya kimlik avı benzetimleri için istenmeyen posta filtrelemeyi atlamanız gerekirse, posta akış kurallarını kullanmayın. Daha fazla bilgi için bkz. Kullanıcılara üçüncü taraf kimlik avı benzetimlerinin ve filtrelenmemiş [iletilerin SecOps posta kutularına teslimi yapılandırma](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Microsoft 365 Defender istenmeyen posta önleme ilkeleri oluşturmak için bu portalı kullanma

Microsoft 365 Defender portalında özel bir istenmeyen posta önleme ilkesi oluşturmak, istenmeyen posta filtresi kuralını ve ilişkili istenmeyen posta filtresi ilkesi aynı anda her ikisi için de aynı adı kullanarak oluşturur.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri sayfasında** Simge oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **İlke** oluşturun ve **sonra açılan listeden** Gelen'i seçin.

3. İlke sihirbazı açılır. **İlkenizi adla sayfasında** şu ayarları yapılandırabilirsiniz:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Görüntülenen **Kullanıcılar, gruplar ve etki** alanları sayfasında, ilkenin geçerli olduğu iç alıcıları (alıcı koşulları) bulun:
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya kuruluşta posta kişileri.
   - **Gruplar**: Belirtilen dağıtım grupları, posta etkin güvenlik grupları veya Microsoft 365 Grupları.
   - **Etki** alanları: Belirtilen kabul edilen etki [alanlarındaki tüm](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşulda birden çok değer IÇIN VEYA mantığını kullanın (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar, AND mantığını (örneğin, _\<recipient1\>_ ve ) kullanır _\<member of group 1\>_.

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları) bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Görüntülenen istenmeyen **posta özellikleri & toplu e-posta** eşiği üzerinde aşağıdaki ayarları yapılandırın:

   - **Toplu e-posta** eşiği: Bir sonraki sayfada yapılandırılan Toplu istenmeyen posta filtreleme kararı için belirtilen eylemi tetikleyen iletinin toplu şikayet  düzeyini (BCL) belirtir. Daha yüksek bir değer iletinin daha az tercih edilen bir değer olduğunu (istenmeyen postaya benzeme olasılığı daha yüksek) gösterir. Varsayılan değer 7'dir. Daha fazla bilgi için [bkz. EOP'de toplu şikayet düzeyi (BCL)](bulk-complaint-level-values.md) ve Gereksiz e-posta ile toplu e-posta [arasındaki fark nedir?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Varsayılan olarak, PowerShell yalnızca _MarkAsSpamBulkMail_ ayarının istenmeyen posta `On` önleme ilkeleri içinde yer almaktadır. Bu ayar Toplu filtreleme kararının **sonuçlarını önemli** ölçüde etkiler:

     - **_MarkAsSpamBulkMail_** Açık durumdadır: Eşikten büyük veya ona eşit olan bir BCL, İstenmeyen posta filtreleme kararına karşılık gelen SCL 6'ya dönüştürülür ve Toplu filtreleme kararının eylemi iletiye alınır.
     - **_MarkAsSpamBulkMail_** Kapalı: İletiye BCL damgalı olarak işaret uygulanmıştır, ancak  Toplu filtreleme kararı için **hiçbir işlem** alınmaz. Sonuç olarak, BCL eşiği ve **Toplu** filtreleme karar eylemi önemli değildir.

   - **İstenmeyen posta** sayısını **artırma, İstenmeyen**<sup>\*</sup> posta olarak işaretle ve **Test modu**: Varsayılan olarak kapalı olan Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları.

     Bu ayarlar hakkında ayrıntılı bilgi için bkz. [EOP'de Gelişmiş İstenmeyen Posta Filtresi ayarları](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup> Belirli **diller içerir ve** bu **ülkelerden gelen ayarlar** ASF'nin bir parçası değildir.

   - **Belirli diller içerir**: Kutuya tıklayın ve açılan **listeden Açık** **veya** Kapalı'yı seçin. Bu kutu açılırsa, bir kutu görüntülenir. Kutuya bir dilin adını yazmaya başlayın. Desteklenen diller için filtrelenmiş bir liste görüntülenir. İstediğiniz dili bulunca seçin. Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için Kaldır simgesine ![tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   - **Şu ülkelerde** _: Kutuya tıklayın ve açılan listeden _ *On** veya **Kapalı'yı** seçin. Bu kutu açılırsa, bir kutu görüntülenir. Kutuya bir ülkenin adını yazmaya başlayın. Desteklenen ülkelerin filtre uygulanmış listesi görüntülenir. İstediğiniz ülkeyi bulunca seçin. Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için Kaldır simgesine ![tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:

   - **İleti eylemleri**: Aşağıdaki istenmeyen posta filtreleme kararlarına dayalı olarak iletilere yönelik eylemi seçin veya gözden geçirme:
     - **İstenmeyen posta**
     - **Yüksek güven istenmeyen posta**
     - **Kimlik avı**
     - **Yüksek güven kimlik avı**
     - **Toplu**

     İstenmeyen posta filtreleme kararlarında  kullanılabilen eylemler aşağıdaki tabloda açıklanmıştır.

     - Onay işareti ( ![Onay işareti.](../../media/checkmark.png)) eylemin kullanılabilir olduğunu gösterir (tüm eylemler tüm kararlarda kullanılamaz).
     - Onay işareti sonrasındaki yıldız işareti ( <sup>\*</sup> ), istenmeyen posta filtreleme kararının varsayılan eylemlerini gösterir.

     <br>

     ****

     |Eylem|İstenmeyen posta|Yüksek<br>güven<br>istenmeyen posta|Kimlik avı|Yüksek<br>güven<br>kimlik avı|Toplu|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**İletiyi Gereksiz E-posta klasörüne** taşı: İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. <sup>1</sup>|![Onay işareti.](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|
     |**X üstbilgisi** ekle: İleti üst bilginize bir X üstbilgisi ekler ve iletiyi posta kutusuna teslim ediyor. <p> Daha sonra Bu X üstbilgisini ekle metin kutusuna X üstbilgisi alan adını ( **değer değil) girersiniz** . <p> **İstenmeyen** Posta **ve Yüksek güven istenmeyen** posta kararları için, ileti Gereksiz E-posta klasörüne taşınır. <sup>1,2</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**Konu satırına metin ekle**: İletinin konu satırına metin ekler. İleti posta kutusuna teslim edilir ve Gereksiz e-posta klasörüne taşınır. <sup>1,2</sup> <p> Metni daha sonra Bu metinle **önek konu satırına girersiniz** .|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**İletiyi e-posta adresine** yeniden yönlendir: İletiyi, hedeflenen alıcılar yerine diğer alıcılara gönderir. <p> Alıcıları daha sonra Bu e-posta **adresine yeniden yönlendir kutusunda belirtirsiniz** .|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
     |**İletiyi** silme: Tüm ekler dahil olmak üzere iletinin tamamını sessiz bir şekilde siler.|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**İletiyi** karantinaya alın: İletiyi, hedeflenen alıcılar yerine karantinaya gönderir. <p> İletinin daha sonra Karantina kutusunda karantinada tutulacak ne kadar süreyle **tutulacaklarını** belirtirsiniz. <p> Görüntülenen İlke [seçin kutusunda](quarantine-policies.md) , istenmeyen posta filtresi kararının karantinaya alınmış iletilerine uygulanan karantina **ilkesi** belirtirsiniz. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md). <sup>3</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../../media/checkmark.png)|
     |**Eylem yok**|||||![Onay işareti](../../media/checkmark.png)|
     |

     > <sup>1</sup> EOP, artık iletileri gereksiz e-posta kuralı yerine Gereksiz E-posta klasörüne yönlendirecek şekilde kendi posta akışı teslim aracısını kullanıyor. **Set-MailboxJokEmailConfiguration** cmdlet'inde _Enabled_ parametresi artık posta akışını hiçbir şekilde etkilemeyecektir. Daha fazla bilgi için bkz[. Posta kutuları üzerinde gereksiz Exchange Online yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > EOP'nin şirket içi veya posta kutularını Exchange karma ortamlarda, şirket içi posta kutularında posta akış kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız Exchange. Bu posta akış kuralları EOP istenmeyen posta filtreleme kararını çevirerek, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşımasini sağlar. Ayrıntılar için bkz. [EOP'yi karma ortamlarda gereksiz E-posta klasörüne istenmeyen posta teslim edecek şekilde yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Bu değeri, posta akışı kurallarında iletiyi filtrelemek veya yönlendirmek için bir koşul olarak kullanabilirsiniz.
     >
     > <sup>3</sup> Boş bir **İlke değeri seçin,** belirli bir karar için varsayılan karantina ilkesi kullanılacak anlamına gelir. Daha sonra istenmeyen posta önleme ilkenizi düzenleyseniz veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir. İstenmeyen posta filtresi kararlarında kullanılan varsayılan karantina ilkeleri hakkında daha fazla bilgi için bu [tabloya bakın](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **İstenmeyen postayı şu** kadar gün karantinada tutma: İstenmeyen posta filtreleme kararının eylemi olarak İletiyi karantinaya alın'ı seçtiysanız, iletiyi ne kadar süre karantinada tutacaklarını belirtir. Süre sona erdikten sonra, ileti silinir ve kurtarılamaz. Geçerli bir değer 1 ile 30 gün arasında olur.

     > [!NOTE]
     > Varsayılan değer, varsayılan istenmeyen posta önleme ilkesinde ve PowerShell'de oluştur ilkelerin yeni istenmeyen posta önleme ilkelerde 15 gündür. Varsayılan değer, yeni istenmeyen posta önleme ilkelerde varsayılan değer olarak 30 gündür ve Microsoft 365 Defender vardır.
     >
     > Bu ayar aynı zamanda kimlik avı önleme ilkeleri tarafından karantinaya alınan iletilerin ne kadar **süreyle** korun koruna bir durumda olduğunu da ayarlar. Daha fazla bilgi için bkz. [EOP'de karantinaya alınmış iletiler ve Office 365](quarantine-email-messages.md).

   - **Şu X üstbilgi metnini ekleyin**: Bu kutu gereklidir ve yalnızca istenmeyen posta filtreleme kararının eylemi olarak **X** üstbilgisi Ekle'yi seçtiysanız kullanılabilir. Belirttiğiniz değer, ileti üst *bilgisinde* eklenen üst bilgi alanı adıdır. Üst bilgi alanı *değeri her* zamandır `This message appears to be spam`.

     Uzunluk üst üste 255 karakterdir ve değer boşluk veya iki nokta üst üste (iki nokta üst üste) :).

     Örneğin, değerini girersiniz `X-This-is-my-custom-header`ve iletiye eklenen X üstbilgisi aşağıdaki gibi olur: `X-This-is-my-custom-header: This message appears to be spam.`

     Boşluk veya iki nokta üst üste (tarih) içeren bir değer :), girersiniz değer yoksayılır ve varsayılan X üstbilgisi iletiye () eklenir`X-This-Is-Spam: This message appears to be spam.`.

   - **Konu satırına bu** metni hazırlayın: Bu kutu gereklidir ve yalnızca istenmeyen posta filtreleme kararının eylemi  olarak Konu satırına metin ekle'i seçtiysanız kullanılabilir. İletinin konu satırına eklemek istediğiniz metni girin.

   - **Bu e-posta adresine** yeniden yönlendir: Bu kutu gereklidir ve ancak istenmeyen posta filtreleme  kararının eylemi olarak iletiyi e-posta adresine yeniden yönlendir'i seçtiysanız kullanılabilir. İletiyi teslim etmek istediğiniz e-posta adresini girin. Noktalı virgülle (birden çok değer) ayırarak birden çok değer ;).

   - **Güvenlik ayarlarını İpuçları**: Varsayılan olarak Güvenlik İpuçları etkinleştirilir, ancak onay kutusunu temizerek bunları devre dışı edebilirsiniz.

   - **Sıfır saatlik otomatik temizlemeyi etkinleştir (ZAP): ZAP**, önceden bu posta kutularına teslim edilen iletileri algılar ve Exchange Online alır. Daha fazla bilgi için bkz [. Sıfır saatlik otomatik temizleme - istenmeyen postaya ve kötü amaçlı yazılıma karşı koruma](zero-hour-auto-purge.md).

     ZAP varsayılan olarak açıktır. ZAP açıkken aşağıdaki ayarlar kullanılabilir:

     - **Kimlik avı iletileri için ZAP'yi** etkinleştirme: Varsayılan olarak, kimlik avı algılamaları için ZAP etkinleştirilir, ancak onay kutusunu temizerek devre dışı abilirsiniz.
     - **İstenmeyen posta iletileri için ZAP'yi** etkinleştirme: Varsayılan olarak, ZAP istenmeyen posta algılamaları için etkinleştirilir, ancak onay kutusunu temizerek devre dışı abilirsiniz.

   > [!NOTE]
   > Son kullanıcı istenmeyen posta bildirimleri karantina ilkeleri içinde _karantina bildirimleriyle_ değiştirilmiştir. Karantina bildirimleri, tüm desteklenen koruma özellikleri için karantinaya alınmış iletiler hakkında bilgi içerir (yalnızca istenmeyen posta önleme ilkesi ve kimlik avıyla mücadele ilkesi kararları değil). Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

7. Görüntülenen İzin **ver &** engellenenler listesi açılır listesinde, ileti gönderenlerini istenmeyen posta filtresini atlamalarına izin verilen e-posta adresine veya e-posta etki alanına göre yapılandırabilirsiniz.

   İzin Verilen **bölümünde** , izin verilen gönderenleri ve izin verilen etki alanlarını yapılandırabilirsiniz. Engellenen **bölümünde,** engellenen gönderenler ve engellenen etki alanları eklersiniz.

   > [!IMPORTANT]
   >
   > Etki alanlarını izin verilen etki alanları listesine eklemeden önce çok dikkatli olun. Daha fazla bilgi için bkz [. EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md)
   >
   > Kendi kabul edilen etki [alanlarınızı veya ortak etki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alanlarınızı (örneğin, microsoft.com veya office.com) hiçbir zaman izin verilen etki alanları listesine ekleyin. Bu etki alanlarının istenmeyen posta filtresini atlayarak atabilmesine izin verilirse, saldırganlar kolayca bu güvenilir etki alanlarına kimlik gönderen iletiler gönderebilir.
   >
   > Etki alanlarını engellenen etki alanları listesine ekleyerek el ile engellemek tehlikeli değildir, ancak yönetim iş yükünü artırır. Daha fazla bilgi için bkz [. EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).
   >
   > Filtrelerimizin bir iletiyi kaçırması, filtreleme kararını kabul etmeyebilirsiniz veya sistemlerimizin bunu takip etmeleri zaman alır. Bu gibi durumlarda, izin verilenler listesi ve engelleme listesi geçerli filtreleme kararlarını geçersiz kılmak için kullanılabilir. Ancak, bu listeleri kısa süreyle ve geçici olarak kullan çünkü uzun listeler kolay kolay gerçekleştirilebilir ve filtreleme yığınımız olması gereken şekilde yapılacak şekildedir. İzin verilen bir etki alanını uzun süre saklayacaksanız, gönderenden etki alanının doğrulanmış olduğunu doğrulamasını ve doğrulanmamışsa DMARC reddetmesi olarak ayarlamasını söylemeniz gerekir.

   Listelerden herhangi birini girdi ekleme adımları aynıdır:

   1. Yapılandırmak istediğiniz listenin bağlantısına tıklayın:
      - **İzin verildi** \> **Gönderenler**: Yönet **(nn) gönderenler'e tıklayın**.
      - **İzin verildi** \> **Etki alanları**: Etki alanlarına **izin ver'e tıklayın**.
      -  \> Engellendi **Gönderenler**: Yönet **(nn) gönderenler'e tıklayın**.
      -  \> Engellendi **Etki alanları**: Etki alanlarını **engelle'ye tıklayın**.

   2. Görüntülenen açılır listede aşağıdaki adımları uygulayın:
      1. Oluştur simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Gönderenleri ekleyin veya** Etki **alanı ekleyin**.
      2. Görüntülenen **Gönderenleri ekle veya** Etki  alanı ekle açılır kutusunda, Gönderen kutusuna gönderenin e-posta adresini veya Etki Alanı  kutusuna etki **alanını** girin. Siz yazarken, değer kutunun altında görüntülenir. E-posta adresini veya etki alanını yazmayı bitirdikten sonra, kutunun altındaki değeri seçin.
      3. Önceki adımı gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

      Bitirdikten sonra Gönderenleri **ekle'ye veya Etki alanı ekle'ye** **tıklayın**.

      Ana uça geri dönüp, eklemişsiniz olan gönderenler veya etki alanları sayfada listelenir. Bu sayfadan girdiyi kaldırmak için aşağıdaki adımları izleyin:

      1. Listeden bir veya daha fazla girdi seçin. Ayrıca, listede değerleri **bulmak** için Arama kutusunu da kullanabilirsiniz.
      2. En az bir girdiyi seçdikten sonra, sil simgesi ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png) görüntülenir.
      3. Sil simgesine tıklayın ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png) seçin.

      Bitirdikten sonra Bitti'ye **tıklayın**.

      İzin Ver & **sayfasına geri dönüp** **okumaya devam** etmek için Sonraki'ne tıklayın.

8. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Oluştur'a **tıklayın**.

9. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>İstenmeyen Microsoft 365 Defender ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, aşağıdaki değerlerden birini bulun:
   - Tür **değeri** Özel istenmeyen **posta önleme ilkesidir**
   - Ad **değeri** **İstenmeyen posta önleme gelen ilkesidir (Varsayılan)**

   İstenmeyen posta önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Tür**

3. Adına tıklayarak istenmeyen posta önleme ilkesi işaretlendiğinde, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>İstenmeyen Microsoft 365 Defender ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, adına tıklayarak listeden bir istenmeyen posta önleme ilkesi seçin:
   - Tür sütunundaki değerin Özel istenmeyen posta önleme ilkesi **olduğu****, oluşturduğunuz özel ilke**.
   - İstenmeyen postayla **mücadele gelen ilkesi (Varsayılan) adlı varsayılan ilke**.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin Microsoft 365 Defender önleme ilkeleri oluşturmak için [E-posta](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) portalını kullanma bölümüne bakın.

   Varsayılan istenmeyen posta önleme ilkesi için, Uygulanan bölümü  kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandırılamaz.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırası ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan istenmeyen posta önleme ilkesi devre dışı bırakamaz.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel istenmeyen posta önleme ilkesi Tür değerine sahip bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Özel istenmeyen posta önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, istenmeyen posta önleme ilkelerine, oluşturulduklarına dayalı olarak öncelik verilir (daha yeni ilkeler, eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, istenmeyen posta önleme ilkesi önceliğini ancak oluşturduklardan sonra değiştirebilirsiniz. PowerShell'de, istenmeyen posta filtresi kuralı  oluşturmak (var olan kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- İstenmeyen posta önleme ilkeleri görüntülenme sırasına göre işlenir (ilk ilkenin **Öncelik** değeri 0'dır). Varsayılan istenmeyen posta önleme ilkesi En düşük **öncelik değerine** sahiptir ve bunu değiştiremezsiniz.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel istenmeyen posta önleme ilkesi Tür değerine sahip bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, geçerli öncelik değerine ve özel ilke  sayısına göre  Önceliği artır veya Önceliği azalt'a bakın:
   - Öncelik değeri **0** **olan istenmeyen posta** önleme ilkesi yalnızca Öncelik azalt **seçeneğine** sahiptir.
   - En düşük Öncelik değerine (örneğin,  **3**) sahip istenmeyen posta önleme ilkesi yalnızca Öncelik artır **seçeneğine** sahiptir.
   - Üç veya daha fazla istenmeyen posta önleme ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliği  artır hem de Öncelik azalt **seçenekleri** kullanılabilir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Microsoft 365 Defender istenmeyen posta önleme ilkelerini kaldırmak için bu portalı kullanın

Özel bir istenmeyen posta Microsoft 365 Defender için Posta Önleme portalını kullanırken, istenmeyen posta filtresi kuralı ve buna karşılık gelen istenmeyen posta filtresi ilkesi de silinir. Varsayılan istenmeyen posta önleme ilkesi kaldıramayr.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel istenmeyen posta önleme ilkesi Tür değerine sahip bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

3. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>İstenmeyen Exchange Online ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell kullanma

Daha önce açıklandığı gibi, istenmeyen posta önleme ilkesi istenmeyen posta filtresi ilkesi ve istenmeyen posta filtresi kuralıdan oluşur.

Aynı Exchange Online tek başına EOP PowerShell'de, istenmeyen posta filtresi ilkeleriyle istenmeyen posta filtresi kuralları arasındaki fark görünür hale gelir. **\*-HostedContentFilterPolicy** cmdlet'lerini kullanarak istenmeyen posta filtresi ilkelerini yönetirsiniz ve **-HostedContentFilterRule cmdlet'lerini\*** kullanarak istenmeyen posta filtresi kurallarını yönetirsiniz.

- PowerShell'de, önce istenmeyen posta filtresi ilkesi, ardından da kuralın geçerli olduğu ilkeyi tanımlayan istenmeyen posta filtresi kuralını oluşturun.
- PowerShell'de, istenmeyen posta filtresi ilkesi ve istenmeyen posta filtresi kuralı ayarlarını ayrıca değiştirirsiniz.
- PowerShell'den istenmeyen posta filtresi ilkesi kaldırılmışsa, buna karşılık gelen istenmeyen posta filtresi kuralı otomatik olarak kaldırılamaz ve bunun tersi de geçerlidir.

Aşağıdaki istenmeyen posta önleme ilkesi ayarları yalnızca PowerShell'de kullanılabilir:

- Varsayılan _olarak MarkAsSpamBulkMail_ `On` parametresidir. Bu ayarın etkileri, bu makalenin önceki Microsoft 365 Defender İstenmeyen posta ilkeleri oluşturmak için [E-posta](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) portalını kullanma bölümünde açıklanmıştır.
- Son kullanıcı istenmeyen posta karantina bildirimleri için aşağıdaki ayarlar:
  - Daha _fazla bilgi_ için Gereksiz E-posta Raporlama Aracı'nın bağlantısını gösteren veya gizleen DownloadLink Outlook.
  - _Bildirimin konu satırı özelleştirmek için kullanabileceğiniz EndUserSpamNotificationCustomSubject_ parametresi.

### <a name="use-powershell-to-create-anti-spam-policies"></a>İstenmeyen posta önleme ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de istenmeyen posta önleme ilkesi oluşturmak iki adımlık bir işlemdir:

1. İstenmeyen posta filtresi ilkesi oluşturun.
2. Kuralın geçerli olduğu istenmeyen posta filtresi ilkesi belirten istenmeyen posta filtresi kuralını oluşturun.

 **Notlar**:

- Yeni bir istenmeyen posta filtresi kuralı oluşturabilir ve bu kurala var olan, ilişkilendirilmemiş bir istenmeyen posta filtresi ilkesi attaysanız. İstenmeyen posta filtresi kuralı birden fazla istenmeyen posta filtresi ilkesiyle ilişkilendirilz.
- İlkeyi oluşturmadan önce, PowerShell'de yeni istenmeyen posta filtresi ilkelerde Microsoft 365 Defender ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı _olarak oluşturun (_ `$false` **New-HostedContentFilterRule cmdlet'inde** Etkin).
  - **New-HostedContentFilterRule** cmdlet'inde oluşturma sırasında ilkenin önceliğini _ayarlayın (__\<Number\>_ Öncelik).

- PowerShell'de yeni bir istenmeyen posta filtresi ilkesi, siz bu ilkeyi istenmeyen posta filtresi kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>1. Adım: PowerShell'i kullanarak istenmeyen posta filtresi ilkesi oluşturma

İstenmeyen posta filtresi ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarları içeren Contoso Yöneticiler adında bir istenmeyen posta filtresi ilkesi oluşturur:

- İstenmeyen posta filtreleme kararı istenmeyen posta veya yüksek güven içeren istenmeyen posta olduğunda iletileri karantinaya alın [](quarantine-policies.md) ve karantinaya alınmış iletiler için varsayılan karantina ilkesi kullanın (_SpamQuarantineTag_ veya _HighConfidenceSpamQuarantineTag_ parametrelerini kullanacağız).
- BCL 7, 8 veya 9, toplu e-posta istenmeyen posta filtreleme kararının eylemlerini tetikler.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> İstenmeyen posta filtresi [ilkesinde kullanmak](quarantine-policies.md) üzere karantina ilkesi belirtme hakkında ayrıntılı yönergeler için bkz. PowerShell kullanarak istenmeyen posta önleme ilkesinde karantina [ilkesi belirtme](quarantine-policies.md#anti-spam-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>2. Adım: PowerShell kullanarak istenmeyen posta filtresi kuralı oluşturma

İstenmeyen posta filtresi kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, şu ayarları içeren Contoso Yöneticiler adında yeni bir istenmeyen posta filtresi kuralı oluşturur:

- Contoso Executives adlı istenmeyen posta filtresi ilkesi kuralla ilişkilendirildi.
- Kural, Contoso Executives Group adlı grubun üyeleri için geçerlidir.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini görüntülemek için PowerShell kullanma

Tüm istenmeyen posta filtresi ilkelerinin özet listesini geri dönmek için şu komutu çalıştırın:

```PowerShell
Get-HostedContentFilterPolicy
```

Belirli bir istenmeyen posta filtresi ilkesi hakkında ayrıntılı bilgi dönmek için şu söz dizimsini kullanın:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Yöneticiler adlı istenmeyen posta filtresi ilkesi için tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını görüntülemek için PowerShell kullanma

Var olan istenmeyen posta filtresi kurallarını görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Tüm istenmeyen posta filtresi kurallarının özet listesini geri dönmek için şu komutu çalıştırın:

```PowerShell
Get-HostedContentFilterRule
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Belirli bir istenmeyen posta filtresi kuralı hakkında ayrıntılı bilgi almak için şu söz dizimi kullanın:

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Contoso Yöneticiler adlı istenmeyen posta filtresi kuralı için tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de istenmeyen posta filtresi ilkesinde değişiklik yapmak için 1. Adım: Bu makalenin başlarındaki İstenmeyen posta filtresi ilkesi oluşturmak için [PowerShell](#step-1-use-powershell-to-create-a-spam-filter-policy) kullanma bölümünde açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır **, her zaman** En düşük öncelikli ve bunu silemezsiniz) yalnızca PowerShell'de istenmeyen posta filtresi ilkesinde değişiklik yapmak için kullanılabilir.
- İstenmeyen posta filtresi ilkesi yeniden _adlandırılamaz_ (**Set-HostedContentFilterPolicy** cmdlet'in Name parametresi yoktur). İlke portalında istenmeyen posta önleme Microsoft 365 Defender yeniden adlandırıyorken, yalnızca istenmeyen posta filtresi kuralını yeniden _adlandırıyor olursunuz_.

İstenmeyen posta filtresi ilkesinde değişiklik yapmak için şu söz dizimlerini kullanın:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> İstenmeyen posta filtresi [ilkesinde kullanmak](quarantine-policies.md) üzere karantina ilkesi belirtme hakkında ayrıntılı yönergeler için bkz. PowerShell kullanarak istenmeyen posta önleme ilkesinde karantina [ilkesi belirtme](quarantine-policies.md#anti-spam-policies-in-powershell).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını değiştirmek için PowerShell kullanma

PowerShell'de istenmeyen posta filtresi kuralını değiştirirken kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak sağlayan Enabled parametresidir. Var olan istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için bir sonraki bölüme bakın.

Aksi takdirde, PowerShell'de istenmeyen posta filtresi kuralını değiştirerek ek ayarlar kullanılamaz. 2. Adım: Bu makalenin başlarındaki İstenmeyen posta filtresi kuralı oluşturmak için [PowerShell](#step-2-use-powershell-to-create-a-spam-filter-rule) kullanma bölümünde açıklandığı gibi, aynı ayarlara da sahip olursiniz.

İstenmeyen posta filtresi kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

Bu örnekte, adlı mevcut istenmeyen posta filtresi kuralı yeniden adlandırılır `{Fabrikam Spam Filter}`.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de istenmeyen posta filtresi kuralının etkinleştirilmesi veya devre dışı bırakılması, tüm istenmeyen posta önleme ilkesi (istenmeyen posta filtresi kuralı ve atanmış istenmeyen posta filtresi ilkesi) için etkinleştirme veya devre dışı bırakma. Varsayılan istenmeyen posta önleme ilkesi (her zaman tüm alıcılara uygulanır) etkinleştir veya devre dışı bırakasınız.

PowerShell'de istenmeyen posta filtresi kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimi kullanın:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Bölümü adlı istenmeyen posta filtresi kuralı devre dışıdır.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Enable-HostedContentFilterRule ve](/powershell/module/exchange/enable-hostedcontentfilterrule) [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de istenmeyen posta filtresi kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı irken önceliğini ayarlamak için, onun yerine **New-HostedContentFilterRule** cmdlet'inde Öncelik parametresini kullanın.
- Varsayılan istenmeyen posta filtresi ilkesine karşılık gelen bir istenmeyen posta filtresi kuralı yoktur ve her zaman En Düşük değiştirilmez öncelik **değerine sahiptir**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini kaldırmak için PowerShell kullanma

PowerShell kullanarak istenmeyen posta filtresi ilkesi kaldırabilirsiniz, buna karşılık gelen istenmeyen posta filtresi kuralı kaldırılamaz.

PowerShell'de istenmeyen posta filtresi ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı istenmeyen posta filtresi ilkesi kaldırır.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını kaldırmak için PowerShell kullanma

PowerShell kullanarak istenmeyen posta filtresi kuralını kaldırabilirsiniz, buna karşılık gelen istenmeyen posta filtresi ilkesi kaldırılamaz.

PowerShell'de istenmeyen posta filtresi kuralını kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı istenmeyen posta filtresi kuralı kaldır).

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>İstenmeyen posta ilkesi ayarlarınızı test etmek için GTUBE iletisi gönderme

> [!NOTE]
> Bu adımlar yalnızca, GTUBE iletisi göndermekte olduğunuz e-posta kuruluşu giden istenmeyen postaları taramazsa çalışır. Varsa, test mesajını gönderesiniz.

İstenmeyen Toplu E-posta için Genel Test (GTUBE), test iletisine ek olarak, kuruluşlarının istenmeyen posta önleme ayarlarını doğrulamak için bir metin dizesidir. GTUBE iletisi, kötü amaçlı yazılım ayarlarını test etmek için Avrupa Virüsten Koruma Enstitüsü (EICAR) metin dosyasına benzer.

Boşluk veya satır sonu olmadan, e-posta iletisine aşağıdaki GTUBE metnini tek satıra dahil edin:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
