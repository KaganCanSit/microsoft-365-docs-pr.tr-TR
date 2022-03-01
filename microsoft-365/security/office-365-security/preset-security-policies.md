---
title: Önceden belirlenmiş güvenlik ilkeleri
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
description: Yöneticiler, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender'ın koruma özellikleri genelinde Standart ve Katı ilke ayarlarının nasıl uygulanabileceklerini Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ff81eea4232693662a907695ea0cef0d94941ac6
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015438"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Önceden belirlenmiş güvenlik ilkeleri, önerilen tüm istenmeyen posta, kötü amaçlı yazılım ve kimlik avı ilkelerinin kullanıcılara aynı anda uygulanması için merkezi bir konum sağlar. İlke ayarları yapılandırılabilir değildir. Bunun yerine, bunlar bizim tarafından ayarlanır ve zararlı içeriği kullanıcılardan uzak tutmak ile gereksiz kesintileri önlemek arasındaki denge için veri merkezlerimizde yer alan gözlemlerimize ve deneyimlerimize dayalıdır.

Bu makalenin kalan kalanında önceden ayarlanmış güvenlik ilkeleri ve bunları nasıl yapılandırılan açıklanmıştır.

## <a name="what-preset-security-policies-are-made-of"></a>Önceden belirlenmiş güvenlik ilkeleri

Önceden belirlenmiş güvenlik ilkeleri aşağıdaki öğelerden oluşur:

- Profiller
- İlkeler
- İlke ayarları

Ayrıca, önceden ayarlanmış birden çok güvenlik ilkelerinin ve diğer ilkelerin aynı kişi için geçerli olması, öncelik sırası önemlidir.

### <a name="profiles-in-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerde profiller

Profil, koruma düzeyini belirler. Aşağıdaki profiller kullanılabilir:

- **Standart koruma**: Çoğu kullanıcı için uygun olan taban çizgisi koruma profili.
- **Katı koruma**: Seçili kullanıcılar için daha katı bir koruma profili (yüksek değerli hedefler veya öncelikli kullanıcılar).

  Standart **koruma ve** **Katı koruma için**, kuralları, profillerin kimlere uygulansa veya uygulanmadısını belirleyen koşullar ve özel durumlar için kullanırsiniz.

  Kullanılabilir koşullar ve özel durumlar:

  - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya kuruluşta posta kişileri.
  - **Gruplar**: Belirtilen dağıtım grupları, posta etkin güvenlik grupları veya Microsoft 365 Grupları.
  - **Etki** alanları: Belirtilen kabul edilen etki [alanlarındaki tüm](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alıcılar.

  Bir koşulu veya özel durumu yalnızca bir kez kullanabilirsiniz, ancak koşul veya özel durum için birden çok değer belirtebilirsiniz. Aynı koşul veya özel durum kullanımı VEYA mantığının birden çok değeri (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar, AND mantığı kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

- **Yerleşik koruma (yalnızca** Office 365 için Defender): Bağlantıları ve Ekleri koruma Kasa sağlayan Kasa profil. Bu profil, varsayılan ilkelerin hiç Kasa bağlantılar Kasa ekleri için varsayılan ilkeler sağlar.

  Yerleşik **koruma için,** önceden ayarlanmış güvenlik ilkesi varsayılan olarak bu müşteriler için tüm Defender Office 365 açıktır. Bunu önermse de, özel durumları Kullanıcılar, Gruplar ve Etki Alanları'ne göre yapılandırarak korumanın  belirli kullanıcılara uygulanmasını da sebilirsiniz. 

İlkeleri kullanıcılara atayana kadar, **Standart** ve **Katı** önceden tanımlı güvenlik ilkeleri hiç kimseye atanmaz. Buna karşılık, **yerleşik koruma önceden** ayarlanmış güvenlik ilkesi tüm alıcılara varsayılan olarak atanır, ancak özel durumları yapılandırabilir.

### <a name="policies-in-preset-security-policies"></a>Önceden belirlenmiş güvenlik ilkelerde ilkeler

Önceden belirlenmiş güvenlik ilkeleri, EOP'nin çeşitli koruma özelliklerinden ve İlkeler için Microsoft Defender'dan Office 365. Bu ilkeler, _kullanıcılara_ Standart koruma veya **Katı koruma önceden** tanımlı **güvenlik** ilkelerini atadikten sonra oluşturulur. Bu ilkelerde ayarları değiştiremezsiniz.

- **Exchange Online Protection ilkeleri:** Bu, Microsoft 365 posta kutuları olan Exchange Online ve posta kutusu olmayan tek Exchange Online EOP kuruluşlarını içerir:

  - [Standart Önceden Belirlenmiş Güvenlik İlkesi](configure-your-spam-filter-policies.md) **ve Kesin Önceden Belirlenmiş Güvenlik** İlkesi adlı istenmeyen posta **önleme ilkeleri**.
  - [Standart Önceden Belirlenmiş Güvenlik İlkesi](configure-anti-malware-policies.md) **ve Kesin Önceden Belirlenmiş Güvenlik İlkesi** adlı kötü amaçlı **yazılımdan koruma ilkeleri**.
  - [Standart Önceden Belirlenmiş Güvenlik İlkesi ve Katı Önceden](set-up-anti-phishing-policies.md#spoof-settings) **Belirlenmiş Güvenlik İlkesi** **(kimlik** avı ayarları) adlı EOP Kimlik avından koruma ilkeleri.

- **İlkeler için Microsoft Defender Office 365 ilkeleri**: Bu, Microsoft 365 E5 veya Office 365 için Defender'a sahip olan kuruluşları içerir:
  - Standart Önceden Belirlenmiş Güvenlik İlkesi ve Kesin Önceden Belirlenmiş Güvenlik İlkesi Office 365 için Microsoft  Defender'da kimlik avıyla mücadele ilkeleri şunlardır:
    - EOP [kimlik avı önleme](set-up-anti-phishing-policies.md#spoof-settings) ilkelerde bulunan kimlik sahtesi ayarlarıyla aynıdır.
    - [Kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Kasa Önceden Belirlenmiş Güvenlik İlkesi](set-up-safe-links-policies.md)**, Kesin** **Önceden Belirlenmiş Güvenlik** İlkesi ve Yerleşik Koruma İlkesi **adlı Bağlantılar ilkeleri vardır**.
  - [Kasa Önceden Belirlenmiş Güvenlik İlkesi](set-up-safe-attachments-policies.md)**, Katı** **Önceden Belirlenmiş Güvenlik** İlkesi ve Yerleşik Koruma İlkesi **adlı Ek ilkeleri içerir**.

EOP korumalarını, kullanıcı koruması için Microsoft Defender'dan farklı Office 365 uygulayabilirsiniz.

### <a name="policy-settings-in-preset-security-policies"></a>Önceden belirlenmiş güvenlik ilkelerde ilke ayarları

Koruma profillerde ilke ayarlarını değiştiremezsiniz. **Standart,** **Katı** ve **Yerleşik** koruma ilkesi ayarı değerleri EOP için önerilen ayarlar ve [Güvenlik için Microsoft Defender'da Office 365 açıklanmıştır](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Önceden ayarlanmış güvenlik ilkeleri ve diğer ilkeler için öncelik sırası

Bir kullanıcıya birden çok ilke uygulandığında, en yüksek önceliğe en düşük önceliğe aşağıdaki sıra uygulanır:

1. **Kesin koruma önceden** ayarlanmış güvenlik ilkesi
2. **Standart koruma önceden** ayarlanmış güvenlik ilkesi
3. Özel güvenlik ilkeleri
4. **Yerleşik koruma önceden ayarlanmış** güvenlik ilkesi ve varsayılan güvenlik ilkeleri

Başka bir deyişle, Katı koruma ilkesi ayarları  **, Standart** koruma ilkesi ayarlarını geçersiz kılar ve bu da ayarları özel ilkeden geçersiz kılar ve bu da Yerleşik koruma önceden ayarlanmış güvenlik ilkesinden (Kasa Bağlantılar  ve Kasa Ekleri) ve varsayılan ilkeden (istenmeyen postadan koruma, kötü amaçlı yazılımdan koruma ve kimlik avı önleme) ayarları geçersiz kılar.

Örneğin, Standart korumada bir güvenlik ayarı varsa  ve yönetici kullanıcı için Standart korumayı etkinleştirdiyse, özel bir ilkede veya varsayılan ilkede (aynı kullanıcı için) bu ayar için yapılandırılmış olan yerine **Standart** koruma ayarı uygulanır. Belirli ihtiyaçları karşılamak üzere, özel bir ilke uygularken yalnızca **Standart** veya Katı koruma ilkesi uygulamak istediğiniz, kuruluşta bazı bölümlere sahip olabileceğinizi unutmayın.

**Yerleşik koruma,** var olan Bağlantıları ve Ekleri Kasa alıcıları Kasa etkilemez. Standart **korumayı,** Katı korumayı veya özel Kasa  Bağlantıları'nı veya Kasa Ekleri ilkelerini zaten yapılandırdıysanız, bu ilkeler her zaman Yerleşik korumadan önce  uygulanır; dolayısıyla, önceden ayarlanmış veya özel ilkelerde zaten tanımlanmış olan alıcıların hiçbir etkisi olmaz.

## <a name="assign-preset-security-policies-to-users"></a>Kullanıcılara önceden ayarlanmış güvenlik ilkeleri atama

### <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Önceden belirlenmiş güvenlik **ilkeleri sayfasına gitmek** için kullanın <https://security.microsoft.com/presetSecurityPolicies>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Önceden ayarlanmış güvenlik ilkelerini yapılandırmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi **rol gruplarının** **üyesi olun** .
  - Önceden ayarlanmış güvenlik ilkelerine salt okunur erişim için, Genel Okuyucu rol grubunun **üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Not**: Kullanıcı atama Azure Active Directory ilgili kullanıcı rolüne Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Kullanıcılara standart Microsoft 365 Defender Katı önceden tanımlı güvenlik ilkeleri atamak için İlke Portalı'nı kullanın

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, Şablon ilkeleri bölümündeki **&** \> İşbirliği İlkeleri'ne **&** \>  \> Kurallar Tehdit İlkeleri Önceden Belirlenmiş Güvenlik **İlkeleri'ne** gidin. Doğrudan Önceden belirlenmiş güvenlik **ilkeleri sayfasına gitmek** için kullanın <https://security.microsoft.com/presetSecurityPolicies>.

2. Önceden belirlenmiş **güvenlik ilkeleri sayfasında** , Standart koruma **veya Katı** koruma **bölümlerinde** **Yönet'e** tıklayın.

3. Standart **Koruma Uygula veya** **Katı koruma uygula** sihirbazı bir uç uçarak başlar. **EOP korumaları uygulanıyor** sayfasında, [EOP](#policies-in-preset-security-policies) korumalarının geçerli olduğu iç alıcıları (alıcı koşulları) seçin:
   - **Kullanıcılar**
   - **Gruplar**
   - **Etki alanları**

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları) bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Office 365 için Microsoft Defender'da, Office 365 korumaları için [Microsoft Defender](#policies-in-preset-security-policies) korumalarının geçerli olduğu iç alıcıları (alıcı koşulları) belirlemek üzere sayfaya Office 365 için **Defender'a** alınırsınız.

   Ayarlar ve davranış tam olarak **önceki adımda yer alan EOP korumaları** gibi sayfa için geçerlidir.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Değişikliklerinizi **gözden geçir ve onaylayın sayfasında** seçimlerinizi doğrulayın ve ardından Onayla'ya **tıklayın**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Standart Microsoft 365 Defender Katı önceden ayarlanmış güvenlik ilkelerinin atamalarını değiştirmek için güvenlik portalını kullanma

Standart koruma veya Katı koruma önceden ayarlanmış güvenlik  ilkesi atamasını  değiştirme adımları, ilk başta önceden ayarlanmış güvenlik ilkelerini kullanıcılara atamayla [aynıdır](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Var olan koşulları **ve özel** durumları  koruyarak Standart koruma veya Katı koruma önceden ayarlanmış güvenlik ilkelerini devre dışı bırakmak için, ![iki durumlu düğmeyi Devre Dışı **Durumuna Getir** Kapalı olarak kaydırın.](../../media/scc-toggle-off.png) İlkeleri etkinleştirmek için, iki durumlu düğmeyi **Etkin Geçiş Açık** ![olarak kaydırın](../../media/scc-toggle-on.png).

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Yerleşik Microsoft 365 Defender önceden ayarlanmış güvenlik ilkesi atamalarını değiştirmek için Güvenlik Portalı'nı kullanma

Yerleşik koruma önceden  ayarlanmış güvenlik ilkesi tüm alıcılara atanır ve **Standart** koruma veya Katı koruma önceden ayarlanmış güvenlik ilkeleri veya özel Kasa Bağlantıları veya Ekleri Kasa ilkeleri içinde tanımlanan alıcıları etkilemez.

Bu nedenle, yerleşik koruma önceden ayarlanmış güvenlik ilkesi için **genelde özel durumlar önerilmez** .

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, Şablon ilkeleri bölümündeki **&** \> İşbirliği İlkeleri'ne **&** \>  \> Kurallar Tehdit İlkeleri Önceden Belirlenmiş Güvenlik **İlkeleri'ne** gidin. Doğrudan Önceden belirlenmiş güvenlik **ilkeleri sayfasına gitmek** için kullanın <https://security.microsoft.com/presetSecurityPolicies>.

2. Önceden belirlenmiş **güvenlik ilkeleri sayfasında**, Yerleşik **koruma bölümünde Dışlama ekle (****önerilmez) öğesini** seçin.

3. Görüntülenen **Yerleşik korumadan** çıkar açılır iletisinde, yerleşik Dışlama Bağlantıları ve Ekleri Koruma'nın dışında Kasa iç alıcıları Kasa seçin:
   - **Kullanıcılar**
   - **Gruplar**
   - **Etki alanları**

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Kullanıcıya Standart koruma veya Katı koruma güvenlik ilkesi atamayı başarıyla  tamamladınız doğrulamak için, varsayılan değerin Katı koruma ayarından farklı olan Standart koruma ayarından farklı bir  koruma **ayarı** kullanın.

Örneğin, istenmeyen posta olarak algılandı (yüksek güvenle istenmeyen posta değil) e-posta için iletinin Standart koruma kullanıcıları için Gereksiz E-posta klasörüne  teslim edildiğinden ve Katı koruma kullanıcıları için karantinaya alınmış **olduğunu doğrulayın.**

Ya da toplu posta [için, 6](bulk-complaint-level-values.md) veya daha yüksek BCL değeri iletiyi Standart koruma kullanıcıları için Gereksiz E-posta klasörüne teslim eder  ve BCL değeri 4 veya daha yüksek olan ileti Katı koruma kullanıcıları için iletiyi **karantinaya** alır.
