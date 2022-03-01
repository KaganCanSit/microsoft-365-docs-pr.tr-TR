---
title: Destek için Microsoft Defender Kasa da Bağlantılar ilkelerini Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, İş için Microsoft Defender'daki Bağlantılar ilkelerini ve Kasa Bağlantıları Kasa görüntülemeyi, oluşturmayı, değiştirmeyi ve Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2b4435dc8cf7cb560d565e6457f18b7f00e38bd0
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021590"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Destek için Microsoft Defender Kasa da Bağlantılar ilkelerini Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, Microsoft [Defender'a sahip iş müşterileri için Office 365](defender-for-office-365.md). Bu bağlantılarda Safelink'ler hakkında bilgi arayan bir ev kullanıcısı Outlook[, bkz. Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

[Kasa için Microsoft Defender'daki bağlantılar Office 365](defender-for-office-365.md) posta akışında gelen e-posta iletilerinin URL'sini tarama ve e-posta iletisinde ve diğer konumlarda URL'leri ve bağlantıları tıklatma zamanı sağlar. Daha fazla bilgi için bkz. [Kasa için Microsoft Defender'daki Office 365](safe-links.md).

Varsayılan Bağlantı ilkesi Kasa, yerleşik koruma önceden ayarlanmış güvenlik ilkesi tüm alıcılara  Kasa Bağlantıları koruması sağlar (özel Bağlantılar ilkeleri içinde tanımlanmamış kullanıcılar Kasa). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).

Ayrıca, bu makaledeki yordamları kullanarak belirli kullanıcılar, Kasa veya etki alanlarına uygun bağlantılar ilkeleri oluşturabilirsiniz.

> [!NOTE]
>
> Bağlantılar koruması için, bağlantılar Kasa dışında **genel Kasa** yapılandırabilirsiniz. Yönergeler için bkz. [İş için Microsoft Defender'da Kasa Bağlantılar için genel Office 365](configure-global-settings-for-safe-links.md).
>
> Yöneticiler, Bağlantılar'ın farklı yapılandırma ayarlarını dikkate Kasa gerekir. Kullanılabilir seçeneklerden biri, Kişisel Bağlantılar'a kullanıcı kimliği Kasa. Bu özellik, *Güvenlik Ekibi ekiplerinin olası kullanıcı* güvenliğini araştırmalarına, düzeltme önlemleri almalarına ve yüksek ihlalleri sınırlandırmalarına olanak sağlar.

Microsoft 365 Defender portalında veya PowerShell'de Kasa Bağlantıları ilkelerini yapılandırabilirsiniz (Exchange Online'te posta kutusu olan uygun Microsoft 365 kuruluşları için Exchange Online PowerShell; Exchange Online kutularını ekleyebilir, ancak diğer eklentiler için Microsoft Defender Office 365 abonelikleri kullanabilirsiniz).

Bağlantılar ilkesinin temel Kasa şöyledir:

- Güvenli bağlantılar **ilkesi: Kasa** Bağlantılar korumasını açma, gerçek zamanlı URL taramayı açma, iletiyi teslim etmek için gerçek zamanlı taramanın tamamlandıktan önce tamamlanacak şekilde beklemesini belirtme, iç iletileri taramayı açma, URL'lere kullanıcı tıklamalarını izleyip izley vermeyeceğinizi ve kullanıcıların özgün URL'ye tıklaymalarına izin verip vermeyeceğinizi belirtme.
- **Güvenli bağlantı kuralı**: Önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Aşağıdaki iki öğe arasındaki fark, portalda yer alan Kasa Bağlantıları ilkelerini yönetirken Microsoft 365 Defender değildir:

- Bağlantılar ilkesi Kasa, aslında güvenli bağlantı kuralı ve ilişkili güvenli bağlantılar ilkesi aynı anda her ikisi için de aynı adı kullanarak oluşturulur.
- Bağlantılar ilkesi değiştirdikten Kasa, ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri güvenli bağlantılar kuralını değiştirir. Diğer tüm ayarlar ilişkili güvenli bağlantılar ilkesine göre değişiklik sağlar.
- Bağlantılar ilkesi kaldır Kasa, güvenli bağlantılar kuralı ve ilişkili güvenli bağlantılar ilkesi kaldırılır.

PowerShell Exchange Online tek başına EOP PowerShell'de, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin devam Exchange Online Bağlantılar ilkelerini yapılandırmak için [PowerShell veya tek Kasa EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) kullanma bölümüne bakın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirmek için önce izinlerin atanmamış olması gerekir:
  - Kasa Bağlantıları ilkeleri oluşturmak, değiştirmek ve silmek için, **Microsoft 365 Defender portalında** Kuruluş Yönetimi veya Güvenlik Yöneticisi rol gruplarının üyesi  ve Exchange Online'te Kuruluş Yönetimi rol grubunun üyesi Exchange Online. 
  - Genel Bağlantılar ilkelerine salt Kasa için, Genel Okuyucu veya Güvenlik Okuyucusu **rol** **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Site portalında Microsoft 365 Defender ve](permissions-microsoft-365-security-center.md) [Site'deki Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Kullanıcı atamasında ilgili Azure Active Directory rolüne Microsoft 365 yönetim merkezi, kullanıcılara _Microsoft 365 Defender portalında_ gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  . - Aynı **zamanda Kuruluş Yönetimi'nin** Yalnızca Görüntüleme rol [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups), özel özellikle salt okunur erişim de sağlar.

- Bağlantılar ilkeleri hakkında önerilen ayarlarımız Kasa, bağlantı [ilkesi Kasa'ne bakın](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Yeni veya güncelleştirilmiş ilkenin uygulanması için 30 dakika kadar bekleyin.

- [İş için Microsoft Defender'a sürekli yeni özellikler Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Yeni özellikler eklendiklerine göre, mevcut Özellikler ve Bağlantılar ilkeleriniz için Kasa gerekir.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Yeni Microsoft 365 Defender ilkeleri oluşturmak için Kasa kullanma

Web Kasa portalında özel bağlantı bağlantıları ilkesi Microsoft 365 Defender, güvenli bağlantılar kuralı ve ilişkili güvenli bağlantılar ilkesi her ikisi için de aynı adı kullanarak aynı anda oluşturur.

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Bağlantılar Kasa **Oluştur** simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Oluştur'a iki tablo da oluşturabilirsiniz**

3. Yeni **Bağlantılar Kasa ilkesi sihirbazı** açılır. **İlkenizi adla** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:

   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Görüntülenen **Kullanıcılar ve etki** alanları sayfasında, ilkenin geçerli olduğu iç alıcıları (alıcı koşulları) bulun:
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya kuruluşta posta kişileri.
   - **Gruplar**: Belirtilen dağıtım grupları, posta etkin güvenlik grupları veya Microsoft 365 Grupları.
   - **Etki** alanları: Belirtilen kabul edilen etki [alanlarındaki tüm](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşulda birden çok değer IÇIN VEYA mantığını kullanın (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar, AND mantığını (örneğin, _\<recipient1\>_ ve ) kullanır _\<member of group 1\>_.

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (alıcı özel durumları) bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Görüntülenen **Koruma ayarları** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **İletilerde kötü amaçlı olabilecek bilinmeyen URL'ler için eylemi seçin**:  E-posta iletileri Kasa bağlantılar için Bağlantı korumasını etkinleştirmek için Etkin'i seçin. Bu ayarı etkinleştirirseniz, aşağıdaki ayarlar kullanılabilir:
     - **Dosyaları işaret alan şüpheli bağlantılar ve bağlantılar için** gerçek zamanlı URL tarama uygulama: E-posta iletisinde bağlantıları gerçek zamanlı taramayı etkinleştirmek için bu seçeneği belirtin. Bu ayarı şu şekilde etkinleştirirseniz kullanılabilir:
       - **İletiyi teslimmeden önce URL tarama işleminin tamamlandıktan** sonra tamamlanacak şekilde bekleme: Gerçek zamanlı URL tarama işleminin iletiyi teslim etmek için tamamlanacak şekilde beklemesini bekleyin.
     - **Posta Kasa Kuruluş** içinde gönderilen e-posta iletilerine bağlantılar: E-posta iletilerini, Kasa Gönderenler ve iç alıcılar arasındaki iletilere uygulamak için bu seçeneği belirtin.
   - **E-posta içinde bilinmeyen veya kötü** amaçlı olabilecek URL'lere yönelik eylemi seçin:  Microsoft Teams'daki bağlantılar için Kasa Bağlantıları korumasını etkinleştirmek için Teams. Bu ayarın etkili bir şekilde 24 saate kadar sürebilir.
   - **Kullanıcı tıklatmalarını izleme**: Kullanıcının e-posta iletilerde URL'lere tıklamalarını izleme seçeneğini etkinleştirmek için bu ayarın seçimini kaldırın.
   - **Kullanıcıların özgün URL'ye tıklamalarına izin verme**: Kullanıcıların uyarı sayfalarındaki özgün URL'ye tıklamalarını engellemek için bu [seçeneği belirtin](safe-links.md#warning-pages-from-safe-links).
   - **Aşağıdaki URL'leri yeniden** yazma: Belirtilen URL'lere, aksi takdirde Üçüncü Sayfa Bağlantıları tarafından engellenmiş Kasa verir.

     Kutuya istediğiniz URL'yi veya değeri yazın ve Ekle'ye **tıklayın**. Bu adımı gereken sayıda yinelayın.

     Var olan bir girdiyi kaldırmak için, ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

     Girdi söz dizimi [için, "Aşağıdaki URL'leri yeniden yazma" listesi için Giriş söz dizimi'ne bakın](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Bu ayarlar hakkında ayrıntılı bilgi için bkz. [Kasa iletileri için bağlantılar ayarları'Kasa](safe-links.md#safe-links-settings-for-email-messages) [Bağlantı ayarları'Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Standart ve Katı ilke ayarları için önerilen değerler hakkında daha fazla bilgi için bkz. [Kasa ilke ayarları](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Bildirim** sayfasında, Kullanıcılarınıza nasıl bildirim almak istediğinize **göre aşağıdaki değerlerden birini seçin**:
   - **Varsayılan bildirim metnini kullanma**
   - **Özel bildirim metni kullanma**: Bu değeri seçersiniz (uzunluk 200 karakteri geçemez), aşağıdaki ayarlar görüntülenir:
     - **Otomatik Microsoft Çeviri için E-yapılandırmayı kullanma**
     - **Özel bildirim metni**: Bu kutuya özel bildirim metnini girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

8. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Bağlantılar Microsoft 365 Defender görüntülemek için Kasa kullanma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Bağlantılar **Kasa**, aşağıdaki özellikler Bağlantılar ilkeleri listesinde Kasa görüntülenir:
   - **Ad**
   - **Durum**
   - **Öncelik**

3. Adına tıklayarak bir ilkeyi seçince, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Bağlantılar Microsoft 365 Defender değiştirmek için Kasa kullanma

1. Microsoft 365 Defender portalında, İlkeler ve **kurallar & Yönelik** \> **Tehdit İlkeleri bölümüne gidin** \> ve  \> **Kasa gidin**.

2. Yeni **Kasa sayfasında**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin [Microsoft 365 Defender için Kasa Portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) bölümüne bakın.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırası ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-safe-links-policies"></a>Bağlantılar ilkelerini etkinleştirme Kasa devre dışı bırakma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Yeni **Kasa sayfasında**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-safe-links-policies"></a>Bağlantılar ilkelerinin Kasa ayarlama

Varsayılan olarak Kasa Bağlantılara, oluşturulduklarının sırasına göre bir öncelik verilir (daha yeni ilkeler, eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

**Not**:

- Microsoft 365 Defender portalında, ilk bağlantıların önceliğini ancak Kasa sonra değiştirebilirsiniz. PowerShell'de, güvenli bağlantılar kuralı  oluşturmak (var olan kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- Kasa Bağlantıları ilkeleri görüntülenme sırasına göre işlenir (ilk ilkenin **Öncelik** değeri 0'dır). Öncelik sırası, birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Yeni **Kasa sayfasında**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, geçerli öncelik değerine ve özel ilke  sayısına göre  Önceliği artır veya Önceliği azalt'a bakın:
   - Öncelik değeri 0 **olan** ilke **yalnızca** Önceliğe azalt **seçeneğine** sahiptir.
   - En düşük Öncelik **değerine (** örneğin, 3) sahip **ilke** yalnızca Öncelik **artır seçeneğine** sahiptir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliğe **artır** hem de Öncelik azalt **seçeneklerine** sahiptir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Bağlantılar Microsoft 365 Defender kaldırmak için Kasa kullanma

1. Microsoft 365 Defender portalında, İlkeler bölümündeki **&** \> İşbirliği **İlkeleri ve & için** \>  \> Kurallar Tehdit **Kasa'e** gidin.

2. Yeni **Kasa sayfasında**, adı tıklatarak listeden bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

3. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Yeni Exchange Online ilkeleri yapılandırmak için powershell veya tek başına EOP PowerShell Kasa kullanma

Daha önce açıklandığı gibi, Kasa Bağlantıları ilkesi, güvenli bağlantı ilkesi ve güvenli bağlantı kuralıdan oluşur.

PowerShell'de, güvenli bağlantı ilkeleriyle güvenli bağlantı kuralları arasındaki fark görünür. Güvenli bağlantı ilkelerini **\*yönetmek için -SafeLinksPolicy** cmdlet'lerini ve **\*güvenli bağlantı kurallarını da -SafeLinksRule** cmdlet'lerini kullanarak yönetirsiniz.

- PowerShell'de önce güvenli bağlantı ilkesi, sonra da kuralın geçerli olduğu ilkeyi tanımlayan güvenli bağlantı kuralı oluşturun.
- PowerShell'de, güvenli bağlantılar ilkesi ve güvenli bağlantılar kuralıyla ilgili ayarları ayrıca değiştirirsiniz.
- PowerShell'den güvenli bağlantılar ilkesi kaldırılmışsa, buna karşılık gelen güvenli bağlantılar kuralı otomatik olarak kaldırılamaz ve bunun tersi de geçerlidir.

### <a name="use-powershell-to-create-safe-links-policies"></a>Yeni bağlantılar ilkeleri oluşturmak Kasa PowerShell kullanma

PowerShell'Kasa Bağlantılar ilkesi oluşturmak iki adımlı bir işlemdir:

1. Güvenli bağlantılar ilkesi oluşturun.
2. Kuralın geçerli olduğu güvenli bağlantılar ilkesi belirten güvenli bağlantılar kuralı oluşturun.

> [!NOTE]
>
> - Yeni bir güvenli bağlantı kuralı oluşturabilir ve bu kurala varolan, ilişkilendirilmemiş bir güvenli bağlantı ilkesi atabilirsiniz. Güvenli bağlantılar kuralı birden çok güvenli bağlantı ilkesiyle ilişkilendirilz.
>
> - İlkeyi oluşturmadan önce, PowerShell'de Microsoft 365 Defender portalda olmayan yeni güvenli bağlantı ilkelerde aşağıdaki ayarları yapılandırabilirsiniz:
>   - Yeni ilkeyi devre dışı olarak _oluşturun (_ `$false` **New-SafeLinksRule cmdlet'inde** etkin).
>   - **New-SafeLinksRule** _cmdlet'inde_ _\<Number\>_ oluşturma sırasında ilkenin önceliğini ayarlayın (Öncelik).
>
> - PowerShell'de yeni bir güvenli bağlantı ilkesi, siz güvenilir bağlantılar kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>1. Adım: PowerShell kullanarak güvenli bağlantılar ilkesi oluşturma

Güvenli bağlantılar ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - _DoNotRewriteUrls_ parametresinde kullanmak üzere girdi söz dizimi hakkında ayrıntılar için bkz. "Aşağıdaki URL'leri yeniden yazma" listesi için [giriş söz dizimi](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).
>
> - **Set-SafeLinksPolicy** cmdlet'ini kullanarak varolan güvenli bağlantı ilkelerini değiştirirken _DoNotRewriteUrls_ parametresinde kullanabileceğiniz ek söz dizimi için, bu makalenin devamdaki Güvenli bağlantı ilkelerini değiştirmek için [PowerShell](#use-powershell-to-modify-safe-links-policies) kullanma bölümüne bakın.

Bu örnek, aşağıdaki değerleri içeren Contoso All adlı bir güvenli bağlantı ilkesi oluşturur:

- E-posta iletisinde URL tarama ve yeniden yazma'ya tıklayın.
- Tarayıcıda URL taramayı Teams.
- Dosyaları işaret alan tıklı bağlantılar da dahil olmak üzere, tıklı URL'ler için gerçek zamanlı taramayı açma.
- İletiyi teslim etmek için URL tarama işleminin tamamlandıktan sonra tamamlanacaklarını bekleyin.
- İç iletiler için URL tarama ve yeniden yazma'ya tıklayın.
- Kasa Links korumasıyla ilgili kullanıcı tıklamalarını izleme (_DoNotTrackUserClicks_ parametresi kullanacağız) ve varsayılan değer de $false tıklamaların iz iz olduğu anlamına gelir.
- Kullanıcıların özgün URL'ye tıklamalarına izin verme.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>2. Adım: PowerShell kullanarak güvenli bağlantılar kuralı oluşturma

Güvenli bağlantılar kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Bu örnek, aşağıdaki koşulları içeren Contoso All adlı güvenli bağlantı kuralı oluşturur:

- Kural, Contoso All adlı güvenli bağlantılar ilkesiyle ilişkilendirildi.
- Kural, etki alanındaki tüm alıcılar için contoso.com geçerlidir.
- Öncelik parametresi kullanılmay _olduğundan,_ varsayılan öncelik kullanılır.
- Kural etkinleştirilir ( _Enabled_ parametresi bizim değil ve varsayılan değer: `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Güvenli bağlantı ilkelerini görüntülemek için PowerShell kullanma

Varolan güvenli bağlantı ilkelerini görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli bağlantı ilkelerinin özet bir listesini döndürür.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

Bu örnek, Contoso Yöneticiler adlı güvenli bağlantılar ilkesi için ayrıntılı bilgi döndürür.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Güvenli bağlantı kurallarını görüntülemek için PowerShell kullanma

Varolan güvenli bağlantı kurallarını görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli bağlantı kurallarının özet listesini döndürür.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

Bu örnekte, Contoso Yöneticiler adlı güvenli bağlantılar kuralıyla ilgili ayrıntılı bilgiler döndürür.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Güvenli bağlantı ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de güvenli bağlantı ilkesi yeniden adlandırılamaz ( **Set-SafeLinksPolicy** cmdlet'in _Name_ parametresi yoktur). Yeni portalda Kasa Bağlantılar Microsoft 365 Defender yeniden adlandırıyor, yalnızca güvenli bağlantılar kuralını yeniden _adlandırıyor olursunuz_.

PowerShell'de güvenli bağlantı ilkelerini değiştirmek için tek dikkat edilmesi gereken ek nokta _, DoNotRewriteUrls_ parametresi için kullanılabilir söz dizimidir ("Aşağıdaki URL'leri yeniden yazma [" listesi](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)):

- Var olan tüm girdilerin yerini alacak değerleri eklemek için, aşağıdaki söz dizimi kullanın: `"Entry1","Entry2,..."EntryN"`.
- Var olan diğer girdileri etkilemeden değer eklemek veya kaldırmak için, aşağıdaki söz dizimi kullanın: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Bunun dışında, 1. Adım [: PowerShell](#step-1-use-powershell-to-create-a-safe-links-policy) kullanarak güvenli bağlantılar ilkesi oluşturma makalesinde açıklandığı gibi aynı ayarlara bu makalenin başlarındaki Güvenli bağlantı ilkesi oluşturmak için de kullanabilirsiniz.

Güvenli bağlantılar ilkesi değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Güvenli bağlantı kurallarını değiştirmek için PowerShell kullanma

PowerShell'de güvenli bağlantı kuralı değiştirildiğinde kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza  olanak sağlayan Enabled parametresidir. Varolan güvenli bağlantı kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, 2. Adım [: PowerShell](#step-2-use-powershell-to-create-a-safe-links-rule) kullanarak bu makalenin başlarındaki Güvenli bağlantılar kuralı bölümünde açıklandığı gibi bir kural oluşturmak için de aynı ayarları kullanabilirsiniz.

Güvenli bağlantılar kuralını değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Güvenli bağlantı kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de güvenli bağlantı kuralının etkinleştirilmesi veya devre dışı bırakılması, tüm Bağlantıları Kasa ilkesini (güvenli bağlantılar kuralı ve atanmış güvenli bağlantılar ilkesi) etkinleştirir veya devre dışı bıraktır.

PowerShell'de güvenli bağlantılar kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimi kullanın:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Bölümü adlı güvenli bağlantılar kuralı devre dışı bırak).

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Enable-SafeLinksRule ve](/powershell/module/exchange/enable-safelinksrule) [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Güvenli bağlantı kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de güvenli bağlantılar kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Yeni kuralı irken önceliğini ayarlamak için, onun yerine **New-SafeLinksRule** cmdlet'inde Öncelik parametresini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Güvenli bağlantı ilkelerini kaldırmak için PowerShell kullanma

Güvenli bağlantılar ilkesi kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen güvenli bağlantılar kuralı kaldırılamaz.

PowerShell'de güvenli bağlantılar ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı güvenli bağlantılar ilkesi kaldırabilirsiniz.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Güvenli bağlantı kurallarını kaldırmak için PowerShell kullanma

PowerShell kullanarak güvenli bağlantılar kuralını kaldırabilirsiniz, buna karşılık gelen güvenli bağlantılar ilkesi kaldırılamaz.

PowerShell'de güvenli bağlantılar kuralını kaldırmak için şu söz dizimi kullanın:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı güvenli bağlantılar kuralı kaldırabilirsiniz.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Bağlantıların iletileri Kasa olduğunu doğrulamak için, bu raporlar için kullanılabilir Microsoft Defender Office 365 kontrol edin. Daha fazla bilgi için bkz[. Office 365 için Defender raporlarını görüntüleme](view-reports-for-mdo.md) ve Microsoft 365 Defender [kullanın](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Bağlantılar ilkelerini başarıyla oluşturduğunuzdan, değiştirildiğinden veya kaldırıldığı Kasa için, aşağıdaki adımlardan herhangi birini yapın:

- Microsoft 365 Defender'daki Kasa Bağlantılar sayfasında, ilkelerin listesini, Durum değerlerini ve **Öncelik değerlerini doğrulayın**.  <https://security.microsoft.com/safelinksv2> Daha fazla ayrıntı görüntülemek için, listeden ilkeyi seçin ve ayrıntıları dışarı doğru uçarak bakın.

- PowerShell Exchange Online veya Exchange Online Protection PowerShell'de, \<Name\> ilke veya kuralın adıyla değiştirin, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
