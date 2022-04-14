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
ms.openlocfilehash: 2a74fce0242f0206218d6f7f2f13e61d9f0a3b6f
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847125"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik ilkeleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

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

- **Yerleşik koruma** (yalnızca Office 365 için Defender): Yalnızca Kasa Bağlantıları ve Kasa Ekleri korumasını etkinleştiren bir profil. Bu profil, hiçbir zaman varsayılan ilkeleri olmayan Kasa Bağlantıları ve Kasa Ekleri için varsayılan ilkeler sağlar.

  **Yerleşik koruma** için, tüm Office 365 için Defender müşteriler için önceden ayarlanmış güvenlik ilkesi varsayılan olarak açıktır. Bunu önermesek de, korumanın belirli kullanıcılara uygulanmaması için **Kullanıcılar**, **Gruplar** ve **Etki Alanları** temelinde özel durumlar da yapılandırabilirsiniz.

İlkeleri kullanıcılara atayana kadar **, Standart** ve **Katı** önceden ayarlanmış güvenlik ilkeleri kimseye atanamaz. Buna karşılık, **yerleşik koruma** önceden ayarlanmış güvenlik ilkesi varsayılan olarak tüm alıcılara atanır, ancak özel durumları yapılandırabilirsiniz.

### <a name="policies-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerindeki ilkeler

Önceden ayarlanmış güvenlik ilkeleri, EOP ve Office 365 için Microsoft Defender'deki çeşitli koruma özelliklerine karşılık gelen ilkeleri kullanır. Bu ilkeler, kullanıcılara **Standart koruma** veya **Katı koruma** önayarlı güvenlik ilkeleri _atandıktan sonra_ oluşturulur. Bu ilkelerdeki ayarları değiştiremezsiniz.

- **Exchange Online Protection (EOP) ilkeleri**: Bu, Exchange Online posta kutularına sahip Microsoft 365 kuruluşları ve Exchange Online posta kutusu olmayan tek başına EOP kuruluşlarını içerir:

  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Önceden Ayarlanmış Güvenlik İlkesi** adlı [istenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md).
  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Ön Ayarlı Güvenlik İlkesi** adlı [kötü amaçlı yazılımdan koruma ilkeleri](configure-anti-malware-policies.md).
  - **Standart Önceden Ayarlanmış Güvenlik İlkesi** ve **Katı Ön Ayarlı Güvenlik İlkesi** (kimlik sahtekarlığı ayarları) adlı [EOP Kimlik Avı önleme ilkeleri](set-up-anti-phishing-policies.md#spoof-settings).

- **Office 365 için Microsoft Defender ilkeleri**: Bu, Microsoft 365 E5 veya Office 365 için Defender eklenti abonelikleri olan kuruluşları içerir:
  - Office 365 için Microsoft Defender'da **Standart Ön AyarLı Güvenlik İlkesi** ve **Katı Ön Ayarlı Güvenlik İlkesi** adlı kimlik avı önleme ilkeleri şunlardır:
    - EOP kimlik avı önleme ilkelerinde kullanılabilen kimlik sahtekarlığı [ayarlarının](set-up-anti-phishing-policies.md#spoof-settings) aynısı.
    - [Kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Kasa](set-up-safe-links-policies.md) **Standart Önceden Ayarlanmış Güvenlik İlkesi**, **Katı Önceden Ayarlanmış Güvenlik İlkesi** ve **Yerleşik Koruma İlkesi** adlı bağlantılar ilkeleri.
  - Kasa **Standart Önceden Ayarlanmış Güvenlik İlkesi, Katı Önceden Ayarlanmış Güvenlik İlkesi** ve **Yerleşik Koruma İlkesi** adlı [Ekler ilkeleri](set-up-safe-attachments-policies.md).

EOP korumalarını Office 365 için Microsoft Defender korumalardan farklı kullanıcılara uygulayabilirsiniz.

### <a name="policy-settings-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerindeki ilke ayarları

Koruma profillerindeki ilke ayarlarını değiştiremezsiniz. **Standart**, **Katı** ve **Yerleşik koruma** ilkesi ayarı değerleri [, EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar](recommended-settings-for-eop-and-office365.md) bölümünde açıklanmıştır.

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

3. **Standart koruma uygulama** veya **Katı koruma uygulama** sihirbazı açılır öğede başlar. **EOP korumaları için geçerlidir** sayfasında, [EOP korumalarının uygulandığı iç alıcıları](#policies-in-preset-security-policies) tanımlayın (alıcı koşulları):
   - **Kullanıcılar**
   - **Gruplar**
   - **Etki alanları**

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   - **Bu kullanıcıları, grupları ve etki alanlarını dışlayın**: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları), bu seçeneği belirleyin ve özel durumları yapılandırın. Ayarlar ve davranış, koşullara tam olarak benzer.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. Office 365 için Microsoft Defender kuruluşlarda, **Office 365 için Microsoft Defender korumalarının geçerli olduğu iç alıcıları** tanımlamak için [Office 365 için Defender korumaların](#policies-in-preset-security-policies) uygulandığı sayfaya yönlendirilirsiniz to (alıcı koşulları).

   Ayarlar ve davranış, önceki adımda **EOP korumalarının uygulandığı sayfaya** tam olarak benzer.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Değişikliklerinizi gözden geçirin ve onaylayın** sayfasında, seçimlerinizi doğrulayın ve **onayla'ya** tıklayın.

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

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Kullanıcıya **Standart koruma** veya **Katı koruma** güvenlik ilkesini başarıyla atadığınızdan emin olmak için, varsayılan değerin **Standart koruma** ayarından farklı olduğu ve **Katı koruma** ayarından farklı olduğu bir koruma ayarı kullanın.

Örneğin, istenmeyen posta (yüksek güvenilir istenmeyen posta değil) olarak algılanan e-postalar için, iletinin **Standart koruma** kullanıcıları için Gereksiz E-posta klasörüne teslim edilmiş ve **Katı koruma** kullanıcıları için karantinaya alınmış olduğunu doğrulayın.

Ya da [toplu posta](bulk-complaint-level-values.md) için, BCL değerinin 6 veya üzerinin iletiyi **Standart koruma** kullanıcıları için Gereksiz E-posta klasörüne teslim ettiğini ve BCL değerinin 4 veya üzerinin iletiyi **Katı koruma** kullanıcıları için karantinaya alındığını doğrulayın.
