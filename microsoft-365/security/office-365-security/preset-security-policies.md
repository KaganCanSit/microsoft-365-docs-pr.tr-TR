---
title: Önceden ayarlanmış güvenlik ilkeleri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender koruma özellikleri arasında Standart ve Katı ilke ayarlarının nasıl uygulanacağını öğrenebilir
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eb9eb8c3f45b0047922be854972d1f96123342cb
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115531"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik ilkeleri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Önceden ayarlanmış güvenlik ilkeleri, önerilen tüm istenmeyen posta, kötü amaçlı yazılım ve kimlik avı ilkelerini kullanıcılara aynı anda uygulamak için merkezi bir konum sağlar. İlke ayarları yapılandırılamaz. Bunun yerine, bunlar bizim tarafımızda ayarlanır ve zararlı içerikleri kullanıcılardan uzak tutmak ve gereksiz kesintilerden kaçınmak arasında bir denge sağlamak için veri merkezlerindeki gözlemlerimize ve deneyimlerimize dayanır.

Bu makalenin geri kalanında önceden ayarlanmış güvenlik ilkeleri ve bunların nasıl yapılandırıldığı açıklanmaktadır.

## <a name="what-preset-security-policies-are-made-of"></a>Önceden ayarlanmış güvenlik ilkelerinin hangilerinden yapıldığı

Önceden ayarlanmış güvenlik ilkeleri aşağıdaki öğelerden oluşur:

- Profil
- İlkeler
- İlke ayarları

Ayrıca, önceden ayarlanmış birden çok güvenlik ilkesi ve diğer ilkeler aynı kişi için geçerliyse öncelik sırası önemlidir.

### <a name="profiles-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerindeki profiller

Profil, koruma düzeyini belirler. Aşağıdaki profiller kullanılabilir:

- **Standart koruma**: Çoğu kullanıcı için uygun bir temel koruma profili.
- **Katı koruma**: Seçili kullanıcılar için daha agresif bir koruma profili (yüksek değer hedefleri veya öncelikli kullanıcılar).

  **Standart koruma** ve **Katı koruma** için, ilkenin geçerli olduğu iç alıcıları (alıcı koşulları) belirlemek için koşullar ve özel durumlar içeren kurallar kullanırsınız.

  Kullanılabilir koşullar ve özel durumlar şunlardır:

  - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya posta kişileri.
  - **Gruplar**:
    - Belirtilen dağıtım gruplarının veya posta özellikli güvenlik gruplarının üyeleri.
    - Belirtilen Microsoft 365 Grupları.
  - **Etki alanları**: Kuruluşunuzda belirtilen [kabul edilen etki alanlarındaki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) tüm alıcılar.

  Bir koşulu veya özel durumu yalnızca bir kez kullanabilirsiniz, ancak koşul veya özel durum için birden çok değer belirtebilirsiniz. Aynı koşula veya özel duruma ait birden çok değer OR mantığını kullanır (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar AND mantığını kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

  > [!IMPORTANT]
  > Birden çok farklı koşul veya özel durum ek değildir; Onlar kapsayıcı. İlke _yalnızca_ belirtilen alıcı filtrelerinin _tümüyle_ eşleşen alıcılara uygulanır. Örneğin, ilkede aşağıdaki değerlerle bir alıcı filtresi koşulu yapılandırabilirsiniz:
  >
  > - Alıcı: romain@contoso.com
  > - Alıcı şu üyelerin üyesidir: Yöneticiler
  >
  > İlke, _romain@contoso.com yalnızca_ Yönetici gruplarının da üyesiyse uygulanır. Grubun üyesi değilse ilke ona uygulanmaz.
  >
  > Benzer şekilde, ilkenin özel durumu olarak aynı alıcı filtresini kullanırsanız, ilke _romain@contoso.com yalnızca_ Yöneticiler gruplarının da üyesiyse uygulanmaz. Grubun üyesi değilse, ilke hala onun için geçerlidir.

- **Yerleşik koruma** (yalnızca Office 365 için Defender): Yalnızca Kasa Bağlantıları ve Kasa Ekleri korumasını etkinleştiren bir profil. Bu profil, hiçbir zaman varsayılan ilkeleri olmayan Kasa Bağlantıları ve Kasa Ekleri için varsayılan ilkeler sağlar.

  **Yerleşik koruma** için, tüm Office 365 için Defender müşteriler için önceden ayarlanmış güvenlik ilkesi varsayılan olarak açıktır. Bunu önermesek de, korumanın belirli kullanıcılara uygulanmaması için **Kullanıcılar**, **Gruplar** ve **Etki Alanları** temelinde özel durumlar da yapılandırabilirsiniz.

İlkeleri kullanıcılara atayana kadar **, Standart** ve **Katı** önceden ayarlanmış güvenlik ilkeleri kimseye atanamaz. Buna karşılık, **yerleşik koruma** önceden ayarlanmış güvenlik ilkesi varsayılan olarak tüm alıcılara atanır, ancak özel durumları yapılandırabilirsiniz.

### <a name="policies-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerindeki ilkeler

Önceden ayarlanmış güvenlik ilkeleri, EOP ve Office 365 için Microsoft Defender'deki çeşitli koruma özelliklerine karşılık gelen ilkeleri kullanır. Bu ilkeler, kullanıcılara **Standart koruma** veya **Katı koruma** önayarlı güvenlik ilkeleri _atandıktan sonra_ oluşturulur. Bu ilkelerdeki ayarları değiştiremezsiniz.

- **Exchange Online Protection (EOP) ilkeleri**: Bu, Exchange Online posta kutularına sahip Microsoft 365 kuruluşları ve Exchange Online posta kutusu olmayan tek başına EOP kuruluşlarını içerir:

  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Önceden Ayarlanmış Güvenlik İlkesi** adlı [istenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md).
  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Ön Ayarlı Güvenlik İlkesi** adlı [kötü amaçlı yazılımdan koruma ilkeleri](configure-anti-malware-policies.md).
  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Ön Ayarlı Güvenlik İlkesi** (kimlik sahtekarlığı ayarları) adlı [EOP Kimlik Avı önleme ilkeleri](set-up-anti-phishing-policies.md#spoof-settings).

  > [!NOTE]
  > Giden istenmeyen posta ilkeleri önceden ayarlanmış güvenlik ilkelerinin bir parçası değildir. Varsayılan giden istenmeyen posta ilkesi, önceden ayarlanmış güvenlik ilkelerinin üyelerini otomatik olarak korur. Alternatif olarak, önceden ayarlanmış güvenlik ilkelerinin üyeleri için korumayı özelleştirmek için özel giden istenmeyen posta ilkeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md).

- **Office 365 için Microsoft Defender ilkeleri**: Bu, Microsoft 365 E5 veya Office 365 için Defender eklenti abonelikleri olan kuruluşları içerir:
  - standart **önayar güvenlik ilkesi** ve **katı önceden ayarlanmış güvenlik** ilkesi adlı Office 365 için Defender kimlik avı önleme ilkeleri, şunlardır:
    - EOP kimlik avı önleme ilkelerinde kullanılabilen kimlik sahtekarlığı [ayarlarının](set-up-anti-phishing-policies.md#spoof-settings) aynısı.
    - [Kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Kasa](set-up-safe-links-policies.md) **Standart Önceden Ayarlanmış Güvenlik İlkesi**, **Katı Önceden Ayarlanmış Güvenlik İlkesi** ve **Yerleşik Koruma İlkesi** adlı bağlantılar ilkeleri.
  - Kasa **Standart Önceden Ayarlanmış Güvenlik İlkesi, Katı Önceden Ayarlanmış Güvenlik İlkesi** ve **Yerleşik Koruma İlkesi** adlı [Ekler ilkeleri](set-up-safe-attachments-policies.md).

EOP korumalarını Office 365 için Defender korumalardan farklı kullanıcılara uygulayabilir veya aynı alıcılara EOP ve Office 365 için Defender uygulayabilirsiniz.

### <a name="policy-settings-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerindeki ilke ayarları

Koruma profillerindeki ilke ayarlarını değiştiremezsiniz. **Standart**, **Katı** ve **Yerleşik koruma** ilkesi ayarı değerleri [, EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar](recommended-settings-for-eop-and-office365.md) bölümünde açıklanmıştır.

> [!NOTE]
> Office 365 için Defender korumalarında, [kullanıcı kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) için gönderenleri ve [etki alanı kimliğe bürünme](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) koruması için iç veya dış etki alanlarını tanımlamanız gerekir.
>
> Sahip olduğunuz tüm etki alanları ([kabul edilen etki alanları](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), önceden ayarlanmış güvenlik ilkelerinde etki alanı kimliğe bürünme korumasını otomatik olarak alır.
>
> Tüm alıcılar, önceden ayarlanmış güvenlik ilkelerinde [posta kutusu zekasından](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) otomatik olarak kimliğe bürünme koruması alır.

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Önceden ayarlanmış güvenlik ilkeleri ve diğer ilkeler için öncelik sırası

Kullanıcıya birden çok ilke uygulandığında, aşağıdaki sıra en yüksek öncelikliden en düşük önceliğe uygulanır:

1. **Katı koruma** önceden ayarlanmış güvenlik ilkesi
2. **Standart koruma** önceden ayarlanmış güvenlik ilkesi
3. Özel güvenlik ilkeleri
4. **Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi ve varsayılan güvenlik ilkeleri

Başka bir deyişle, **Katı koruma** ilkesinin ayarları Standart **koruma** ilkesinin ayarlarını geçersiz kılar. Bu, özel bir ilkedeki ayarları geçersiz kılar ve bu da **Yerleşik koruma** ön ayarı güvenlik ilkesindeki (Kasa Bağlantılar ve Kasa Ekler) ve varsayılan ilkeden (istenmeyen posta önleme, kötü amaçlı yazılımdan koruma ve kimlik avı önleme) ayarları geçersiz kılar.

Örneğin, **Standart korumada** bir güvenlik ayarı varsa ve yönetici bir kullanıcı için **Standart korumayı** etkinleştirmişse, bu ayar için özel ilkede veya varsayılan ilkede (aynı kullanıcı için) yapılandırılan ayar yerine **Standart koruma** ayarı uygulanır. Belirli gereksinimleri karşılamak için kuruluşunuzdaki diğer kullanıcılara özel bir ilke uygularken yalnızca **Standart** veya **Katı koruma** ilkesini uygulamak istediğiniz kuruluşunuzun bir bölümüne sahip olabileceğini unutmayın.

**Yerleşik koruma**, mevcut Kasa Bağlantıları veya Kasa Ekleri ilkelerindeki alıcıları etkilemez. **Standart koruma**, **Katı koruma** veya özel Kasa Bağlantıları veya Kasa Ekler ilkelerini zaten yapılandırdıysanız, bu ilkeler _her zaman_ **Yerleşik korumadan** _önce_ uygulanır, bu nedenle bu önceden ayarlanmış veya özel ilkelerde zaten tanımlanmış olan alıcıları etkilemez.

## <a name="assign-preset-security-policies-to-users"></a>Kullanıcılara önceden ayarlanmış güvenlik ilkeleri atama

### <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Önceden ayarlanmış güvenlik ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/presetSecurityPolicies>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Önceden ayarlanmış güvenlik ilkelerini yapılandırmak için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Önceden ayarlanmış güvenlik ilkelerine salt okunur erişim için **Genel Okuyucu** rol grubunun üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Not**: kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'daki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Kullanıcılara Standart ve Katı önceden ayarlanmış güvenlik ilkeleri atamak için Microsoft 365 Defender portalını kullanın

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, Şablonlu ilkeler** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Önceden Ayarlanmış Güvenlik İlkeleri'ne** gidin. **Önceden ayarlanmış güvenlik ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/presetSecurityPolicies>.

2. **Önceden ayarlanmış güvenlik ilkeleri** sayfasında **, Standart koruma** veya **Katı koruma** bölümlerinde **Yönet'e** tıklayın.

3. **Standart koruma uygulama** veya **Katı koruma uygulama** sihirbazı açılır öğede başlar.

   **Exchange Online Protection Uygula** sayfasında, [EOP korumalarının uygulandığı iç alıcıları](#policies-in-preset-security-policies) tanımlayın (alıcı koşulları):
   - **Tüm alıcılar**
   - **Belirli alıcılar**:
     - **Kullanıcılar**
     - **Gruplar**
     - **Etki alanları**

     Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

     Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   - **Hiçbiri**

   - **Bu alıcıları dışla**: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları), bu seçeneği belirleyin ve özel durumları yapılandırın. Ayarlar ve davranış, koşullara tam olarak benzer.

   İşiniz bittiğinde **İleri'ye** tıklayın.

   > [!NOTE]
   > Office 365 için Defender olmayan kuruluşlarda **İleri'ye** tıklamak sizi **Gözden Geçir** sayfasına götürür. **Gözden Geçir** sayfasından önceki kalan adımlar/sayfalar yalnızca Office 365 için Defender sahip kuruluşlarda kullanılabilir.

4. **Office 365 için Defender korumasını uygula** sayfasında, [Office 365 için Defender korumalarının](#policies-in-preset-security-policies) geçerli olduğu iç alıcıları (alıcı koşulları) tanımlayın.

   Ayarlar ve davranış, önceki adımda **EOP korumalarının uygulandığı sayfaya** tam olarak benzer.

   Önceki sayfada EOP koruması için seçtiğiniz **alıcıları** kullanmak için Önceden seçilen alıcılar'ı da seçebilirsiniz.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Kimliğe Bürünme koruması** sayfasında **İleri'ye** tıklayın.

6. **Saldırganlar tarafından kimliğe bürünüldiğinde bayrak eklemek için e-posta adresleri ekleyin** sayfasında, [kullanıcı kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) tarafından korunan iç ve dış gönderenleri ekleyin.

   > [!NOTE]
   > Tüm alıcılar, önceden ayarlanmış güvenlik ilkelerinde [posta kutusu zekasından](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) otomatik olarak kimliğe bürünme koruması alır.

   Her giriş bir görünen ad ve bir e-posta adresinden oluşur. Kutulara her değeri girin ve **Ekle'ye** tıklayın. Bu adımı gerektiği kadar tekrarlayın.

   En fazla 350 kullanıcı belirtebilir ve birden çok ilkedeki kullanıcı kimliğe bürünme koruması ayarlarında aynı kullanıcıyı belirtemezsiniz.

   Listeden var olan bir girdiyi kaldırmak için ![Kullanıcıyı kimliğe bürünme koruması simgesinden kaldırın.](../../media/m365-cc-sc-remove.png).

   İşiniz bittiğinde **İleri'ye** tıklayın.

7. **Saldırganlar tarafından kimliğe bürünüldiğinde bayrak eklemek için etki alanları ekle** sayfasında, [etki alanı kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) tarafından korunan iç ve dış etki alanları ekleyin.

   > [!NOTE]
   > Sahip olduğunuz tüm etki alanları ([kabul edilen etki alanları](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), önceden ayarlanmış güvenlik ilkelerinde etki alanı kimliğe bürünme korumasını otomatik olarak alır.

   Belirtilen etki alanlarındaki tüm gönderenler etki alanı kimliğe bürünme koruması tarafından korunur.

   Kutuya etki alanını girin ve **Ekle'ye** tıklayın. Bu adımı gerektiği kadar tekrarlayın.

   Listeden var olan bir girdiyi kaldırmak için girdiyi seçin ve ardından ![Kimliğe bürünme koruması simgesinden etki alanını kaldırın.](../../media/m365-cc-sc-remove.png).

   Tüm kimlik avı önleme ilkelerinde etki alanı kimliğe bürünme koruması için belirtebileceğiniz en fazla etki alanı sayısı 50'dir.

   İşiniz bittiğinde **İleri'ye** tıklayın.

8. **Kimliğe bürünme olarak işaretlememek için güvenilen e-posta adresleri ve etki alanları ekle sayfasında, kimliğe bürünme** korumasının dışında tutmak istediğiniz gönderen e-posta adreslerini ve etki alanlarını girin. Bu gönderenlerden gelen iletiler hiçbir zaman kimliğe bürünme saldırısı olarak işaretlenmez, ancak gönderenler EOP ve Office 365 için Defender'deki diğer filtreler tarafından taramaya devam eder.

   Kutuya e-posta adresini veya etki alanını girin ve **Ekle'ye** tıklayın. Bu adımı gerektiği kadar tekrarlayın.

   Listeden var olan bir girdiyi kaldırmak için girdiyi seçin ve ardından ![Kimliğe bürünme koruması simgesinin özel durumlarını kaldırın.](../../media/m365-cc-sc-remove.png).

   İşiniz bittiğinde **İleri'ye** tıklayın.

9. **Bu ilkeyi gözden geçir ve onayla** sayfasında seçimlerinizi doğrulayın ve **onayla'ya** tıklayın.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Standart ve Katı önceden ayarlanmış güvenlik ilkelerinin atamalarını değiştirmek için Microsoft 365 Defender portalını kullanın

**Standart koruma** veya **Katı koruma** önayarlı güvenlik ilkesinin atamasını değiştirme adımları, [kullanıcılara önceden ayarlanmış güvenlik ilkelerini ilk atadığınız](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users) zamanki adımlarla aynıdır.

Mevcut koşulları ve özel durumları korurken **Standart koruma** veya **Katı koruma** önayarlı güvenlik ilkelerini devre dışı bırakmak için iki **durumlu düğmeyi Devre Dışı** ![Geçiş Kapalı.](../../media/scc-toggle-off.png). İlkeleri etkinleştirmek için iki **durumlu düğmeyi Etkin İki Durumlu** ![Düğme Açık](../../media/scc-toggle-on.png) olarak kaydırın.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Yerleşik koruma önceden ayarlanmış güvenlik ilkesinin atamalarını değiştirmek için Microsoft 365 Defender portalını kullanın

**Yerleşik koruma** önayarlı güvenlik ilkesinin tüm alıcılara atandığını ve **Standart koruma** veya **Katı** koruma önayarlı güvenlik ilkeleri ya da özel Kasa Bağlantıları veya Kasa Ekleri ilkelerinde tanımlanan alıcıları etkilemediği unutmayın.

Bu nedenle, **genellikle Yerleşik koruma** önayarlı güvenlik ilkesi için özel durumlar önermeyiz.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, Şablonlu ilkeler** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Önceden Ayarlanmış Güvenlik İlkeleri'ne** gidin. **Önceden ayarlanmış güvenlik ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/presetSecurityPolicies>.

2. **Önceden ayarlanmış güvenlik ilkeleri** sayfasında **Yerleşik koruma** bölümünde **Dışlama ekle (önerilmez)** seçeneğini belirleyin.

3. Görüntülenen **Yerleşik korumanın dışında bırak** açılır penceresinde, yerleşik Kasa Bağlantıları ve Kasa Ekler korumasının dışında tutulan iç alıcıları tanımlayın:
   - **Kullanıcılar**
   - **Gruplar**
   - **Etki alanları**

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Yerleşik koruma simgesinden dışlamaları kaldırın.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Kullanıcıya **Standart koruma** veya **Katı koruma** güvenlik ilkesini başarıyla atadığınızdan emin olmak için, varsayılan değerin **Standart koruma** ayarından farklı olduğu ve **Katı koruma** ayarından farklı olduğu bir koruma ayarı kullanın.

Örneğin, istenmeyen posta (yüksek güvenilir istenmeyen posta değil) olarak algılanan e-postalar için, iletinin **Standart koruma** kullanıcıları için Gereksiz E-posta klasörüne teslim edilmiş ve **Katı koruma** kullanıcıları için karantinaya alınmış olduğunu doğrulayın.

Ya da [toplu posta](bulk-complaint-level-values.md) için, BCL değerinin 6 veya üzerinin iletiyi **Standart koruma** kullanıcıları için Gereksiz E-posta klasörüne teslim ettiğini ve BCL değerinin 4 veya üzerinin iletiyi **Katı koruma** kullanıcıları için karantinaya alındığını doğrulayın.
