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
description: Yöneticiler, Exchange Online Protection (EOP) içinde istenmeyen posta önleme ilkelerini görüntülemeyi, oluşturmayı, değiştirmeyi ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d72b99b73a7c399147360364fc2de0a6cee6435b
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128733"
---
# <a name="configure-anti-spam-policies-in-eop"></a>EOP'de istenmeyen posta önleme ilkelerini yapılandırma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları Exchange Online olmayan Microsoft 365 kuruluşlarda, gelen e-posta iletileri EOP tarafından istenmeyen postalara karşı otomatik olarak korunur. EOP, kuruluşunuzun istenmeyen postalara karşı genel savunmasının bir parçası olarak istenmeyen posta önleme ilkelerini (istenmeyen posta filtresi ilkeleri veya içerik filtresi ilkeleri olarak da bilinir) kullanır. Daha fazla bilgi için bkz [. İstenmeyen posta önleme koruması](anti-spam-protection.md).

Yöneticiler varsayılan istenmeyen posta önleme ilkesini görüntüleyebilir, düzenleyebilir ve yapılandırabilir (ancak silemez). Daha fazla ayrıntı düzeyi için, kuruluşunuzdaki belirli kullanıcılar, gruplar veya etki alanları için geçerli olan özel istenmeyen posta önleme ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliklidir, ancak özel ilkelerinizin önceliğini (çalıştırma sırasını) değiştirebilirsiniz.

İstenmeyen posta önleme ilkelerini Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell Exchange Online de yapılandırabilirsiniz; Exchange Online olmayan kuruluşlar için tek başına EOP PowerShell  posta kutuları).

İstenmeyen posta önleme ilkesinin temel öğeleri şunlardır:

- **İstenmeyen posta filtresi ilkesi**: İstenmeyen posta filtreleme kararlarının eylemlerini ve bildirim seçeneklerini belirtir.
- **İstenmeyen posta filtresi kuralı: İstenmeyen posta filtresi** ilkesi için öncelik ve alıcı filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında istenmeyen posta önleme ilkelerini yönettiğinizde bu iki öğe arasındaki fark belirgin değildir:

- İstenmeyen postadan koruma ilkesi oluşturduğunuzda, aslında her ikisi için de aynı adı kullanarak bir istenmeyen posta filtresi kuralı ve ilişkili istenmeyen posta filtresi ilkesi oluşturursunuz.
- İstenmeyen posta önleme ilkesini değiştirdiğinizde ad, öncelik, etkin veya devre dışı ile ilgili ayarlar ve alıcı filtreleri istenmeyen posta filtresi kuralını değiştirir. Diğer tüm ayarlar ilişkili istenmeyen posta filtresi ilkesini değiştirir.
- İstenmeyen postadan koruma ilkesini kaldırdığınızda, istenmeyen posta filtresi kuralı ve ilişkili istenmeyen posta filtresi ilkesi kaldırılır.

Exchange Online PowerShell veya tek başına EOP PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin devamında yer alan [İstenmeyen posta önleme ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell Exchange Online kullanma](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) bölümüne bakın.

Her kuruluşun Şu özelliklere sahip Varsayılan adlı yerleşik bir istenmeyen posta önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş istenmeyen posta filtresi kuralı (alıcı filtreleri) olmasa bile ilke kuruluştaki tüm alıcılara uygulanır.
- İlke, değiştiremezseniz **en düşük** özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Oluşturduğunuz tüm özel ilkeler her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **IsDefault** özelliği değerine `True`sahiptir) ve varsayılan ilkeyi silemezsiniz.

İstenmeyen posta filtrelemenin verimliliğini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha katı ayarlara sahip özel istenmeyen posta önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - İstenmeyen posta önleme ilkelerini eklemek, değiştirmek ve silmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - İstenmeyen posta önleme ilkelerine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- İstenmeyen posta önleme ilkeleri için önerilen ayarlarımız için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- İstenmeyen posta filtrelemeyi tamamen kapatamazsınız, ancak gelen iletideki çoğu istenmeyen posta filtrelemesini atlamak için bir posta akışı kuralı (aktarım kuralı olarak da bilinir) kullanabilirsiniz (örneğin, e-postayı Microsoft 365 teslim etmeden önce üçüncü taraf koruma hizmeti veya cihazı üzerinden yönlendiriyorsanız). Daha fazla bilgi için bkz. [İletilerde istenmeyen posta güvenilirlik düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Yüksek güvenilirlikli kimlik avı iletileri hala filtrelenir. EOP'deki diğer özellikler etkilenmez (örneğin, iletiler her zaman kötü amaçlı yazılım için taranır).
  - SecOps posta kutuları veya kimlik avı simülasyonları için istenmeyen posta filtrelemeyi atlamanız gerekiyorsa, posta akışı kurallarını kullanmayın. Daha fazla bilgi için bkz. [Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>İstenmeyen posta önleme ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel bir istenmeyen posta önleme ilkesi oluşturmak, her ikisi için de aynı adı kullanarak istenmeyen posta filtresi kuralını ve ilişkili istenmeyen posta filtresi ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **İlke oluşturun** ve açılan listeden **Gelen'i** seçin.

3. İlke sihirbazı açılır. **İlkenizi adlandırın sayfasında** şu ayarları yapılandırın:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. Görüntülenen **Kullanıcılar, gruplar ve etki alanları sayfasında,** ilkenin geçerli olduğu iç alıcıları tanımlayın (alıcı koşulları):
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya posta kişileri.
   - **Gruplar**:
     - Belirtilen dağıtım gruplarının veya posta özellikli güvenlik gruplarının üyeleri.
     - Belirtilen Microsoft 365 Grupları.
   - **Etki alanları**: Kuruluşunuzda belirtilen [kabul edilen etki alanlarındaki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) tüm alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşuldaki birden çok değer OR mantığını kullanır (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar AND mantığını kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

   - **Bu kullanıcıları, grupları ve etki alanlarını dışlayın**: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları), bu seçeneği belirleyin ve özel durumları yapılandırın. Ayarlar ve davranış, koşullara tam olarak benzer.

   > [!IMPORTANT]
   > Birden çok farklı koşul veya özel durum ek değildir; Onlar kapsayıcı. İlke _yalnızca_ belirtilen alıcı filtrelerinin _tümüyle_ eşleşen alıcılara uygulanır. Örneğin, ilkede aşağıdaki değerlerle bir alıcı filtresi koşulu yapılandırabilirsiniz:
   >
   > - Alıcı: romain@contoso.com
   > - Alıcı şu üyelerin üyesidir: Yöneticiler
   >
   > İlke, _romain@contoso.com yalnızca_ Yönetici gruplarının da üyesiyse uygulanır. Grubun üyesi değilse ilke ona uygulanmaz.
   >
   > Benzer şekilde, ilkenin özel durumu olarak aynı alıcı filtresini kullanırsanız, ilke _romain@contoso.com yalnızca_ Yöneticiler gruplarının da üyesiyse uygulanmaz. Grubun üyesi değilse, ilke hala onun için geçerlidir.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Görüntülenen Toplu e-posta eşiği & istenmeyen posta özellikleri** sayfasında aşağıdaki ayarları yapılandırın:

   - **Toplu e-posta eşiği**: Sonraki sayfada yapılandırdığınız **Toplu** istenmeyen posta filtreleme kararı için belirtilen eylemi tetikleyen iletinin toplu şikayet düzeyini (BCL) belirtir. Daha yüksek bir değer, iletinin daha az istendiğini gösterir (istenmeyen postaya benzemesi daha olasıdır). Varsayılan değer 7'dir. Daha fazla bilgi için bkz [. EOP'de toplu şikayet düzeyi (BCL)](bulk-complaint-level-values.md) ve [Gereksiz e-posta ile toplu e-posta arasındaki fark nedir?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Varsayılan olarak, PowerShell yalnızca _MarkAsSpamBulkMail_ ayarı istenmeyen posta önleme ilkelerindedir `On` . Bu ayar **Toplu** filtreleme kararının sonuçlarını önemli ölçüde etkiler:

     - **_MarkAsSpamBulkMail_ Açık:** Eşiğe eşit veya daha büyük bir BCL, **İstenmeyen Posta'nın** filtreleme kararına karşılık gelen bir SCL 6'ya dönüştürülür ve iletide **Toplu** filtreleme kararına yönelik eylem alınır.
     - **_MarkAsSpamBulkMail_ Kapalı:** İleti BCL ile damgalanır, ancak **Toplu** filtreleme kararı için _hiçbir işlem_ yapılmaz. Aslında, BCL eşiği ve **Toplu** filtreleme kararı eylemi ilgisizdir.

   - **İstenmeyen posta puanını** artırın, **İstenmeyen posta**<sup>\*</sup> olarak işaretle ve **Test modu**: Varsayılan olarak kapatılan Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları.

     Bu ayarlar hakkında ayrıntılı bilgi için bkz. [EOP'de Gelişmiş İstenmeyen Posta Filtresi ayarları](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup>**Belirli dilleri ve** **bu ülkelerden gelenleri** içerir ayarları ASF'nin bir parçası değildir.

   - **Belirli dilleri içerir**: Kutuya tıklayın ve açılan listeden **Açık** veya **Kapalı'yı** seçin. Bu özelliği açarsanız bir kutu görüntülenir. Kutuya bir dilin adını yazmaya başlayın. Desteklenen dillerin filtrelenmiş bir listesi görüntülenir. Aradığınız dili bulduğunuzda seçin. Bu adımı gerektiği kadar tekrarlayın. Varolan bir değeri kaldırmak için Kaldır ![simgesine tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   - **Bu ülkelerden** _: Kutuya tıklayın ve açılan listeden _ *Açık** veya **Kapalı'yı** seçin. Bu özelliği açarsanız bir kutu görüntülenir. Kutuya bir ülkenin adını yazmaya başlayın. Desteklenen ülkelerin filtrelenmiş listesi görüntülenir. Aradığınız ülkeyi bulduğunuzda seçin. Bu adımı gerektiği kadar tekrarlayın. Varolan bir değeri kaldırmak için Kaldır ![simgesine tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırın:

   - **İleti eylemleri**: İletiler üzerinde aşağıdaki istenmeyen posta filtreleme kararlarına göre gerçekleştirecek eylemi seçin veya gözden geçirin:
     - **Spam**
     - **Yüksek güvenilirlikli istenmeyen posta**
     - **Kimlik Avı**
     - **Yüksek güvenilirlikli kimlik avı**
     - **Toplu**

     İstenmeyen posta filtreleme kararlarına yönelik kullanılabilir eylemler aşağıdaki tabloda açıklanmıştır.

     - Onay işareti ( ![Onay işareti.](../../media/checkmark.png)) eylemin kullanılabilir olduğunu gösterir (tüm eylemler tüm kararlarda kullanılamaz).
     - Onay işaretinden sonraki yıldız işareti ( <sup>\*</sup> ) istenmeyen posta filtreleme kararı için varsayılan eylemi gösterir.

     |Eylem|Spam|Yüksek<br>Güven<br>istenmeyen posta|Kimlik Avı|Yüksek<br>Güven<br>Kimlik avı|Toplu|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**İletiyi Gereksiz E-posta klasörüne taşıma**: İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. <sup>1</sup>|![Onay işareti.](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|
     |**X üst bilgisi ekle**: İleti üst bilgisine bir X üst bilgisi ekler ve iletiyi posta kutusuna teslim eder. <p> Bu X üst bilgisini ekle metin kutusuna daha sonra **X üst bilgisi** alan adını (değeri değil) girersiniz. <p> **İstenmeyen posta** ve **Yüksek güvenilirlikli istenmeyen posta** kararları için ileti Gereksiz E-posta klasörüne taşınır. <sup>1,2</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**Metinle önceden eklenen konu satırı**: İletinin konu satırının başına metin ekler. İleti posta kutusuna teslim edilir ve Gereksiz e-posta klasörüne taşınır. <sup>1,2</sup> <p> Metni daha sonra **Konu ön eki satırına bu metin kutusuyla** girersiniz.|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**İletiyi e-posta adresine yeniden yönlendirme**: İletiyi hedeflenen alıcılar yerine diğer alıcılara gönderir. <p> Alıcıları daha sonra **Bu e-posta adresine yeniden yönlendir** kutusunda belirtirsiniz.|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
     |**İletiyi sil**: Tüm ekler dahil olmak üzere iletinin tamamını sessizce siler.|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)||![Onay işareti](../../media/checkmark.png)|
     |**Karantina iletisi**: İletiyi hedeflenen alıcılar yerine karantinaya gönderir. <p> İletinin ne kadar süreyle karantinada tutulacağını **Daha sonra Karantina** kutusunda belirtirsiniz. <p> Görüntülenen [İlke](quarantine-policies.md) seçin kutusunda istenmeyen posta filtresi kararı için karantinaya alınan iletilere uygulanan karantina **ilkesini belirtirsiniz** . Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md). <sup>3</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../../media/checkmark.png)|
     |**Eylem yok**|||||![Onay işareti](../../media/checkmark.png)|

     > <sup>1</sup> EOP artık gereksiz e-posta kuralını kullanmak yerine iletileri Gereksiz E-posta klasörüne yönlendirmek için kendi posta akışı teslim aracısını kullanıyor. **Set-MailboxJunkEmailConfiguration** cmdlet'indeki _Enabled_ parametresinin artık posta akışı üzerinde hiçbir etkisi yoktur. Daha fazla bilgi için bkz[. Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > EOP'nin şirket içi Exchange posta kutularını koruduğu karma ortamlarda, şirket içi Exchange posta akışı kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız gerekir. Bu posta akışı kuralları, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşıyabilmesi için EOP istenmeyen posta filtreleme kararını çevirir. Ayrıntılar için bkz. [Karma ortamlarda Gereksiz E-posta klasörüne istenmeyen posta göndermek için EOP'yi yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Bu değeri, iletiyi filtrelemek veya yönlendirmek için posta akışı kurallarında koşul olarak kullanabilirsiniz.
     >
     > <sup>3</sup> Boş **bir İlke değeri seçin** , söz konusu karar için varsayılan karantina ilkesinin kullanıldığı anlamına gelir. İstenmeyen posta önleme ilkesini daha sonra düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir. İstenmeyen posta filtresi kararları için kullanılan varsayılan karantina ilkeleri hakkında daha fazla bilgi için [bu tabloya](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) bakın.
     >
     > Kullanıcılar, yüksek güvenilirlikli kimlik avı olarak karantinaya alınan kendi iletilerini yayınlayamaz. Yöneticiler en iyi durumda karantina ilkesini yapılandırarak kullanıcıların karantinaya alınan yüksek güvenilirlikli kimlik avı iletilerinin yayınlanmasını isteyebilir.

   - **İstenmeyen postaları şu kadar gün boyunca karantinada tutun**: İstenmeyen posta filtreleme kararı için eylem olarak **İletiyi karantinaya al** seçeneğini belirlediyseniz iletiyi ne kadar süreyle karantinada tutabileceğinizi belirtir. Süre dolduktan sonra ileti silinir ve kurtarılamaz. Geçerli bir değer 1 ila 30 gündür.

     > [!NOTE]
     > Varsayılan değer, varsayılan istenmeyen posta önleme ilkesinde ve PowerShell'de oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde 15 gündür. varsayılan değer, Microsoft 365 Defender portalında oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde 30 gündür.
     >
     > Bu ayar, **kimlik avı** önleme ilkeleri tarafından karantinaya alınan iletilerin ne kadar süreyle tutulduğunu da denetler. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan iletiler ve Office 365 için Defender](quarantine-email-messages.md).

   - **Bu X üst bilgisi metnini ekle**: Bu kutu gereklidir ve yalnızca istenmeyen posta filtreleme kararı için eylem olarak **X üst bilgisi ekle'yi** seçtiyseniz kullanılabilir. Belirttiğiniz değer, ileti üst bilgisine eklenen üst bilgi alanı *adıdır* . Üst bilgi alanı *değeri* her zaman `This message appears to be spam`şeklindedir.

     Uzunluk üst sınırı 255 karakterdir ve değer boşluk veya iki nokta üst üste (:)) içeremez.

     Örneğin, değerini `X-This-is-my-custom-header`girerseniz, iletiye eklenen X üst bilgisi şu şekildedir: `X-This-is-my-custom-header: This message appears to be spam.`

     Boşluk veya iki nokta üst üste içeren bir değer girerseniz (:), girdiğiniz değer yoksayılır ve varsayılan X üst bilgisi (`X-This-Is-Spam: This message appears to be spam.` ) iletisine eklenir.

   - **Bu metinle önceden eklenen konu satırı**: Bu kutu gereklidir ve yalnızca istenmeyen posta filtreleme kararı için eylem olarak **metin içeren Önceden eklenen konu satırını** seçtiyseniz kullanılabilir. İletinin konu satırının başına eklenecek metni girin.

   - **Bu e-posta adresine yeniden yönlendir**: Bu kutu gereklidir ve yalnızca istenmeyen posta filtreleme kararı için eylem olarak **E-posta adresine yeniden yönlendirme iletisini** seçtiyseniz kullanılabilir. İletiyi iletmek istediğiniz e-posta adresini girin. Noktalı virgülle ayrılmış birden çok değer girebilirsiniz (;).

   - **Güvenlik İpuçları etkinleştir**: Güvenlik İpuçları varsayılan olarak etkindir, ancak onay kutusunu temizleyerek bunları devre dışı bırakabilirsiniz.

   - **Sıfır saatlik otomatik temizlemeyi (ZAP) etkinleştirme**: ZAP, Exchange Online posta kutularına zaten teslim edilmiş iletileri algılar ve üzerinde işlem uygular. Daha fazla bilgi için bkz. [Sıfır saatlik otomatik temizleme - istenmeyen postalara ve kötü amaçlı yazılımlara karşı koruma](zero-hour-auto-purge.md).

     ZAP varsayılan olarak açıktır. ZAP açıldığında aşağıdaki ayarlar kullanılabilir:

     - **Kimlik avı iletileri için ZAP'ı etkinleştirme**: Varsayılan olarak, ZAP kimlik avı algılamaları için etkinleştirilir, ancak onay kutusunu temizleyerek devre dışı bırakabilirsiniz.
     - **İstenmeyen posta iletileri için ZAP'ı etkinleştirme**: Varsayılan olarak, ZAP istenmeyen posta algılamaları için etkinleştirilir, ancak onay kutusunu temizleyerek devre dışı bırakabilirsiniz.

   > [!NOTE]
   > Son kullanıcı istenmeyen posta bildirimlerinin yerini karantina ilkelerindeki _karantina bildirimleri_ almıştır. Karantina bildirimleri, tüm desteklenen koruma özellikleri (yalnızca istenmeyen posta önleme ilkesi ve kimlik avı önleme ilkesi kararları) için karantinaya alınan iletiler hakkında bilgi içerir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

   İşiniz bittiğinde **İleri'ye** tıklayın.

7. Görüntülenen **& engelleme listesi açılır öğesinde** , ileti gönderenlerini istenmeyen posta filtrelemeyi atlayabilmeleri için izin verilen e-posta adresine veya e-posta etki alanına göre yapılandırabilirsiniz.

   **İzin verilenler** bölümünde, izin verilen gönderenleri ve izin verilen etki alanlarını yapılandırabilirsiniz. **Engellenen** bölümünde engellenen gönderenler ve engellenen etki alanları ekleyebilirsiniz.

   > [!IMPORTANT]
   >
   > İzin verilen etki alanları listesine etki alanları eklemeden önce çok dikkatli düşünün. Daha fazla bilgi için bkz. [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md)
   >
   > İzin verilen etki alanları listesine hiçbir zaman kendi [kabul edilen etki alanlarınızı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) veya ortak etki alanlarınızı (örneğin, microsoft.com veya office.com) eklemeyin. Bu etki alanlarının istenmeyen posta filtrelemesini atlamasına izin verilirse, saldırganlar bu güvenilen etki alanlarını sahtekarlık yapan iletileri kuruluşunuza kolayca gönderebilir.
   >
   > Engellenen etki alanları listesine etki alanlarını ekleyerek etki alanlarını el ile engellemek tehlikeli değildir, ancak yönetim iş yükünüzü artırabilir. Daha fazla bilgi için bkz. [EOP'de engelleyici gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).
   >
   > Filtrelerimizin bir iletiyi kaçıracağı, filtreleme kararına katılmadığınız veya sistemlerimizin bu iletiyi yakalaması zaman alan zamanlar olacaktır. Bu gibi durumlarda, geçerli filtreleme kararlarını geçersiz kılmak için izin verilenler listesi ve blok listesi kullanılabilir. Ancak, bu listeleri düzenli ve geçici olarak kullanmanız gerekir: longs listeleri yönetilemez hale gelebilir ve filtreleme yığınımız yapması gereken şeyi yapmalıdır. İzin verilen bir etki alanını uzun süre tutacaksanız, gönderene etki alanının kimliğinin doğrulandığını doğrulamasını ve değilse DMARC reddetme olarak ayarlanmasını söylemeniz gerekir.

   Listelerden herhangi birine girdi ekleme adımları aynıdır:

   1. Yapılandırmak istediğiniz listenin bağlantısına tıklayın:
      - **Izin verilen** \> **Gönderenler**: **Yönet (nn) gönderenler'e** tıklayın.
      - **Izin verilen** \> **Etki alanları**: **Etki alanlarına izin ver'e** tıklayın.
      - **Engellenen** \> **Gönderenler**: **Yönet (nn) gönderenler'e** tıklayın.
      - **Engellenen** \> **Etki alanları**: **Etki alanlarını engelle'ye** tıklayın.

   2. Görüntülenen açılır öğede aşağıdaki adımları uygulayın:
      1. Oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Gönderenleri veya** **Etki alanı ekle'yi seçin**.
      2. Görüntülenen **Gönderen ekle** veya **Etki alanı ekle** açılır öğesinde, **Gönderen** kutusuna gönderenin e-posta adresini veya **Etki Alanı** kutusuna etki alanını girin. Siz yazarken, değer kutunun altında görünür. E-posta adresini veya etki alanını yazmayı bitirdiğinizde kutunun altındaki değeri seçin.
      3. Önceki adımı gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

      İşiniz bittiğinde **, Gönderen ekle'ye** veya **Etki alanı ekle'ye** tıklayın.

      Ana açılır öğeye döndüğünüzde, eklediğiniz gönderenler veya etki alanları sayfada listelenir. Bu sayfadan bir girdiyi kaldırmak için aşağıdaki adımları uygulayın:

      1. Listeden bir veya daha fazla girdi seçin. Listedeki değerleri bulmak için **Arama** kutusunu da kullanabilirsiniz.
      2. En az bir girdiyi seçtikten sonra sil simgesi ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png) Görünür.
      3. Sil simgesine tıklayın ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png) öğesini seçin.

      İşiniz bittiğinde **Bitti'ye** tıklayın.

      **& engelleme listesine izin ver** sayfasına geri dönün, devam etmek için okunduğunuzda **İleri'ye** tıklayın.

8. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Oluştur'a** tıklayın.

9. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında aşağıdaki değerlerden birini arayın:
   - **Tür** değeri **Özel istenmeyen posta önleme ilkesidir**
   - **Ad** değeri **İstenmeyen postadan koruma gelen ilkesidir (Varsayılan)**

   İstenmeyen posta önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Tür**

3. Ada tıklayarak istenmeyen posta önleme ilkesi seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden bir istenmeyen posta önleme ilkesi seçin:
   - **Tür** sütunundaki değerin **Özel istenmeyen posta önleme ilkesi** olduğu, oluşturduğunuz özel bir ilkedir.
   - **İstenmeyen posta önleme gelen ilkesi (Varsayılan)** adlı varsayılan ilke.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için bu [makalenin önceki İstenmeyen posta önleme ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) bölümüne bakın.

   Varsayılan istenmeyen posta önleme ilkesi **için Uygulanan** bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandıramazsınız.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırasını ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan istenmeyen posta önleme ilkesini devre dışı bırakamazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden Tür **değeri** **Özel istenmeyen posta önleme ilkesi** olan bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Özel istenmeyen posta önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, istenmeyen posta önleme ilkelerine oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelere göre daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, istenmeyen posta önleme ilkesinin önceliğini yalnızca oluşturduktan sonra değiştirebilirsiniz. PowerShell'de, istenmeyen posta filtresi kuralını oluştururken varsayılan önceliği geçersiz kılabilirsiniz (bu, mevcut kuralların önceliğini etkileyebilir).
- İstenmeyen posta önleme ilkeleri, görüntülenme sırasına göre işlenir (ilk **ilkenin Öncelik** değeri 0'dır). Varsayılan istenmeyen posta önleme ilkesi **En düşük** öncelik değerine sahiptir ve bunu değiştiremezsiniz.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden **Özel istenmeyen posta önleme ilkesi** **Tür değerine** sahip bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve özel ilkelerin sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan istenmeyen posta önleme ilkesi yalnızca **Önceliği azalt** seçeneğine sahiptir.
   - En düşük **Öncelik** değerine (örneğin, **3**) sahip istenmeyen posta önleme ilkesi yalnızca **Önceliği artır** seçeneğine sahiptir.
   - Üç veya daha fazla istenmeyen posta önleme ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Özel istenmeyen posta önleme ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

Özel bir istenmeyen posta önleme ilkesini kaldırmak için Microsoft 365 Defender portalını kullandığınızda, istenmeyen posta filtresi kuralı ve ilgili istenmeyen posta filtresi ilkesi silinir. Varsayılan istenmeyen posta önleme ilkesini kaldıramazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden Tür **değeri** **Özel istenmeyen posta önleme ilkesi** olan bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

3. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerini yapılandırmak için Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Daha önce açıklandığı gibi, istenmeyen posta önleme ilkesi bir istenmeyen posta filtresi ilkesi ve bir istenmeyen posta filtresi kuralından oluşur.

Exchange Online PowerShell veya tek başına EOP PowerShell'de, istenmeyen posta filtresi ilkeleriyle istenmeyen posta filtresi kuralları arasındaki fark belirgindir. İstenmeyen posta filtresi ilkelerini -HostedContentFilterPolicy cmdlet'lerini kullanarak yönetirsiniz ve **-HostedContentFilterRule cmdlet'lerini kullanarak\*** istenmeyen posta filtre kurallarını yönetirsiniz.**\***

- PowerShell'de önce istenmeyen posta filtresi ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan istenmeyen posta filtresi kuralını oluşturursunuz.
- PowerShell'de, istenmeyen posta filtresi ilkesindeki ayarları ve istenmeyen posta filtresi kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den bir istenmeyen posta filtresi ilkesini kaldırdığınızda, ilgili istenmeyen posta filtresi kuralı otomatik olarak kaldırılmaz ve tam tersi de geçerlidir.

Aşağıdaki istenmeyen posta önleme ilkesi ayarları yalnızca PowerShell'de kullanılabilir:

- Varsayılan olarak _MarkAsSpamBulkMail_ parametresidir `On` . Bu ayarın etkileri, bu makalenin önceki bölümlerinde [yer alan İstenmeyen posta önleme ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) bölümünde açıklanmıştır.
- Son kullanıcı istenmeyen posta karantina bildirimleri için aşağıdaki ayarlar:
  - Outlook için Gereksiz E-posta Raporlama Aracı bağlantısını gösteren veya gizleyen _DownloadLink_ parametresi.
  - Bildirimin konu satırını özelleştirmek için kullanabileceğiniz _EndUserSpamNotificationCustomSubject_ parametresi.

### <a name="use-powershell-to-create-anti-spam-policies"></a>İstenmeyen posta önleme ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de istenmeyen posta önleme ilkesi oluşturmak iki adımlı bir işlemdir:

1. İstenmeyen posta filtresi ilkesini oluşturun.
2. Kuralın geçerli olduğu istenmeyen posta filtresi ilkesini belirten istenmeyen posta filtresi kuralını oluşturun.

 **Notlar**:

- Yeni bir istenmeyen posta filtresi kuralı oluşturabilir ve mevcut, ilişkilendirilmemiş istenmeyen posta filtresi ilkesini atayabilirsiniz. İstenmeyen posta filtresi kuralı birden fazla istenmeyen posta filtresi ilkesiyle ilişkilendirilemiyor.
- İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni istenmeyen posta filtresi ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı olarak oluşturun (**New-HostedContentFilterRule** cmdlet'inde _etkin_`$false`).
  - **New-HostedContentFilterRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ ayarlayın (Öncelik _\<Number\>_).

- PowerShell'de oluşturduğunuz yeni bir istenmeyen posta filtresi ilkesi, ilkeyi bir istenmeyen posta filtresi kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>1. Adım: İstenmeyen posta filtresi ilkesi oluşturmak için PowerShell kullanma

İstenmeyen posta filtresi ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarlarla Contoso Executives adlı bir istenmeyen posta filtresi ilkesi oluşturur:

- İstenmeyen posta filtreleme kararı istenmeyen posta veya yüksek güvenilirlikli istenmeyen posta olduğunda iletileri karantinaya alın ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanın ( _SpamQuarantineTag_ veya _HighConfidenceSpamQuarantineTag_ parametrelerini kullanmıyoruz).
- BCL 7, 8 veya 9, toplu e-posta istenmeyen posta filtreleme kararı için eylemi tetikler.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> İstenmeyen posta filtresi [ilkesinde kullanılacak karantina ilkesini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. [İstenmeyen posta önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-spam-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>2. Adım: İstenmeyen posta filtresi kuralı oluşturmak için PowerShell kullanma

İstenmeyen posta filtresi kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, şu ayarlarla Contoso Executives adlı yeni bir istenmeyen posta filtresi kuralı oluşturur:

- Contoso Executives adlı istenmeyen posta filtresi ilkesi kuralla ilişkilendirilir.
- Kural, Contoso Executives Group adlı grubun üyeleri için geçerlidir.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini görüntülemek için PowerShell kullanma

Tüm istenmeyen posta filtresi ilkelerinin özet listesini döndürmek için şu komutu çalıştırın:

```PowerShell
Get-HostedContentFilterPolicy
```

Belirli bir istenmeyen posta filtresi ilkesi hakkında ayrıntılı bilgi döndürmek için şu söz dizimini kullanın:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Yöneticiler adlı istenmeyen posta filtresi ilkesinin tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını görüntülemek için PowerShell kullanma

Mevcut istenmeyen posta filtresi kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Tüm istenmeyen posta filtresi kurallarının özet listesini döndürmek için şu komutu çalıştırın:

```PowerShell
Get-HostedContentFilterRule
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Belirli bir istenmeyen posta filtresi kuralı hakkında ayrıntılı bilgi döndürmek için şu sözdizimini kullanın:

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Contoso Executives adlı istenmeyen posta filtresi kuralının tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de bir istenmeyen posta filtresi ilkesini değiştirdiğinizde, ilkeyi [1. Adım: PowerShell'i kullanarak](#step-1-use-powershell-to-create-a-spam-filter-policy) bu makalenin önceki bölümlerinde açıklanan istenmeyen posta filtresi ilkesi oluşturma bölümünde açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır, her zaman **En düşük** önceliklidir ve bunu silemezsiniz) yalnızca PowerShell'de istenmeyen posta filtresi ilkesini değiştirdiğinizde kullanılabilir.
- İstenmeyen posta filtresi ilkesini yeniden adlandıramazsınız ( **Set-HostedContentFilterPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında istenmeyen posta önleme ilkesini yeniden adlandırdığınızda, yalnızca istenmeyen posta filtresi _kuralını_ yeniden adlandırırsınız.

İstenmeyen posta filtresi ilkesini değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> İstenmeyen posta filtresi [ilkesinde kullanılacak karantina ilkesini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. [İstenmeyen posta önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-spam-policies-in-powershell).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını değiştirmek için PowerShell kullanma

PowerShell'de istenmeyen posta filtresi kuralını değiştirdiğinizde kullanılamayabilecek tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Enabled_ parametresidir. Mevcut istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, PowerShell'de istenmeyen posta filtresi kuralını değiştirdiğinizde ek ayar kullanılamaz. Bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak istenmeyen posta filtresi kuralı oluşturma](#step-2-use-powershell-to-create-a-spam-filter-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

İstenmeyen posta filtresi kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

Bu örnek, adlı `{Fabrikam Spam Filter}`mevcut istenmeyen posta filtresi kuralını yeniden adlandırır.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de istenmeyen posta filtresi kuralının etkinleştirilmesi veya devre dışı bırakılması, istenmeyen posta önleme ilkesinin tamamını (istenmeyen posta filtresi kuralı ve atanan istenmeyen posta filtresi ilkesi) etkinleştirir veya devre dışı bırakır. Varsayılan istenmeyen posta önleme ilkesini etkinleştiremez veya devre dışı bırakamazsınız (her zaman tüm alıcılara uygulanır).

PowerShell'de istenmeyen posta filtresi kuralını etkinleştirmek veya devre dışı bırakmak için şu sözdizimini kullanın:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı istenmeyen posta filtresi kuralını devre dışı bırakır.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) ve [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de istenmeyen posta filtresi kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-HostedContentFilterRule** cmdlet'indeki _Priority_ parametresini kullanın.
- Varsayılan istenmeyen posta filtresi ilkesinin karşılık gelen bir istenmeyen posta filtresi kuralı yoktur ve her zaman **değiştirilemez öncelik değeri En Düşük'e** sahiptir.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>İstenmeyen posta filtresi ilkelerini kaldırmak için PowerShell kullanma

Bir istenmeyen posta filtresi ilkesini kaldırmak için PowerShell kullandığınızda, ilgili istenmeyen posta filtresi kuralı kaldırılmaz.

PowerShell'de istenmeyen posta filtresi ilkesini kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı istenmeyen posta filtresi ilkesini kaldırır.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>İstenmeyen posta filtresi kurallarını kaldırmak için PowerShell kullanma

Bir istenmeyen posta filtresi kuralını kaldırmak için PowerShell kullandığınızda, ilgili istenmeyen posta filtresi ilkesi kaldırılmaz.

PowerShell'de istenmeyen posta filtresi kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı istenmeyen posta filtresi kuralını kaldırır.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>İstenmeyen posta ilkesi ayarlarınızı test etmek için GTUBE iletisi gönderme

> [!NOTE]
> Bu adımlar yalnızca GTUBE iletisini gönderdiğiniz e-posta kuruluşu giden istenmeyen postaları taramazsa çalışır. Varsa, test iletisini gönderemezsiniz.

İstenmeyen Toplu E-posta için Genel Test (GTUBE), kuruluşunuzun istenmeyen posta önleme ayarlarını doğrulamak için bir test iletisine eklediğiniz bir metin dizesidir. GTUBE iletisi, kötü amaçlı yazılım ayarlarını test etmek için Avrupa Bilgisayar Virüsten Koruma Araştırma Enstitüsü (EICAR) metin dosyasına benzer.

E-posta iletisine boşluk veya satır sonu olmadan aşağıdaki GTUBE metnini tek bir satıra ekleyin:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
