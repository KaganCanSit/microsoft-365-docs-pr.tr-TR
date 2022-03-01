---
title: Kasa Office 365 için Microsoft Defender'da Ekleri Ayarlama Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: E-postada kötü amaçlı Kasa için Ek ilkeleri tanımlamayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cc0f2e3e87c288383880ba5b69f3b6b5d303c40
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032511"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Kasa Office 365 için Microsoft Defender'da Ekleri Ayarlama Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, Microsoft [Defender'a sahip iş müşterileri için Office 365](whats-new-in-defender-for-office-365.md). E-postada ek taraması hakkında bilgi arayan bir ev kullanıcısı Outlook[, bkz. Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Kasa Ekler, [Exchange Online Protection'de (EOP)](anti-malware-protection.md) kötü amaçlı yazılımdan koruma tarafından tarantıktan sonra, ancak alıcılara teslim edildikten sonra gelen e-posta iletilerideki ekleri kontrol etmek için sanal bir ortam kullanan Office 365 için [Microsoft Defender'ın](whats-new-in-defender-for-office-365.md) bir özelliğidir. Daha fazla bilgi için bkz[. Kasa için Microsoft Defender'daki Ekler'Office 365](safe-attachments.md).

Varsayılan Kasa Ekler ilkesi her ne kadar da olsa, yerleşik koruma önceden ayarlanmış güvenlik  ilkesi tüm alıcılara Kasa Ekler koruması sağlar (özel Kasa Ek ilkeleri içinde tanımlanmamış kullanıcılar). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md). Ayrıca, bu makaledeki yordamları kullanarak belirli kullanıcılar, Kasa veya etki alanlarına yönelik ek ilkeleri oluşturabilirsiniz.

Microsoft 365 Defender portalında veya PowerShell'de Kasa Ekleri ilkelerini yapılandırabilirsiniz (Exchange Online PowerShell'de posta kutusu olan uygun Microsoft 365 kuruluşları için; Exchange Online'te posta kutusu olan kuruluşlar için tek başına EOP PowerShell Exchange Online kutularını ekleyin, ancak diğer eklenti abonelikleri Office 365 Defender'ı kullanın).

E-posta Ekleri Kasa temel öğeleri:

- **Güvenli** ek ilkesi: Bilinmeyen kötü amaçlı yazılım algılamaları için eylemleri, kötü amaçlı yazılım ekleri olan iletilerin belirli bir e-posta adresine gönderip gönderilmeme ve Eğer Kasa eğer ileti gönderip gönderilemeyenleri belirtir.
- **Güvenli ek kuralı**: Önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Bu iki öğe arasındaki fark, portalda ekleri Kasa yönetiyorken belirgin Microsoft 365 Defender değildir:

- Kasa Ekler ilkesi  oluştururken, aslında güvenli bir ek kuralı ve ilişkili güvenli ek ilkesi aynı anda her ikisi için de aynı adı kullanarak oluşturulur.
- Ekler ilkesi değiştirildiğinde Kasa, ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri güvenli ek kuralını değiştirir. Diğer tüm ayarlar ilişkili güvenli ek ilkesini değiştirir.
- Bir Ekleri Kaldırma Kasa ilkesi, güvenli ek kuralı ve ilişkili güvenli ek ilkesi kaldırılır.

PowerShell Exchange Online tek başına EOP PowerShell'de, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin devam Exchange Online Ek ilkeleri yapılandırmak için PowerShell veya tek Kasa [EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) kullanma bölümüne bakın.

> [!NOTE]
> Eklerin genel ayarlar alanında Kasa ayarlarına bağlı olmayan özellikleri Yapılandır'a Kasa gerekir. Yönergeler için bkz[. Kasa'de Belgeler için SharePoint, OneDrive,](turn-on-mdo-for-spo-odb-and-teams.md) Microsoft Teams ve Kasa [Ekleri Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirmek için önce izinlere ihtiyacınız vardır:
  - Kasa Ekleri ilkelerini oluşturmak, değiştirmek ve silmek için, **Microsoft 365 Defender portalında** Kuruluş Yönetimi veya Güvenlik Yöneticisi rol gruplarının üyesi  ve Exchange Online'te Kuruluş Yönetimi rol grubuna üye olmalıdır. 
  - Eklere salt okunur erişim Kasa için, Microsoft 365 Defender portalında Genel Okuyucu veya Güvenlik Okuyucusu rol gruplarının üyesi Microsoft 365 Defender  gerekir.

  Daha fazla bilgi için bkz. [Site portalında Microsoft 365 Defender ve](permissions-microsoft-365-security-center.md) [Site'deki Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Kullanıcı atamasında ilgili Azure Active Directory rolüne Microsoft 365 yönetim merkezi, kullanıcılara _Microsoft 365 Defender portalında_ gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Ekler ilkeleriniz hakkında önerilen Kasa için bkz. [Ek Kasa ayarları.](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)

- Yeni veya güncelleştirilmiş ilkenin uygulanması için 30 dakika kadar bekleyin.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Microsoft 365 Defender Ekleri ilkeleri oluşturmak Kasa kullanma

Microsoft 365 Defender portalında özel bir ek Kasa ilkesi oluşturmak, güvenli ek kuralını ve ilişkili güvenli ek ilkesi her ikisi için aynı adı kullanarak aynı anda oluşturur.

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri &** \>  \> Kuralları Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekler **Kasa Oluştur** simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Oluştur'a iki tablo da oluşturabilirsiniz**

3. İlke sihirbazı açılır. **İlkenizi adla** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
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

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar (geçerli özel durumlar) eklemek için, bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Sayfa **Ayarlar**, aşağıdaki ayarları yapılandırabilirsiniz:

   - **Kasa bilinmeyen kötü amaçlı yazılım yanıtı**: Aşağıdaki değerlerden birini seçin:
     - **Kapalı**: Normalde, bu değeri önerilmez.
     - **Monitör**
     - **Engelle**: Bu, varsayılan değerdir ve Standart ve Katı önceden tanımlı güvenlik ilkelerde [önerilen değerdir](preset-security-policies.md).
     - **Değiştir**
     - **Dinamik Teslim (Önizleme özelliği)**

     Bu değerler Ekler ilke [Kasa içinde açıklanmıştır](safe-attachments.md#safe-attachments-policy-settings).

   - **Karantina ilkesi**: Ekleri (Engelle, Değiştir veya Dinamik Teslim) Kasa iletilere uygulanan karantina **ilkesi seçin**. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

     Boş bir değer, varsayılan karantina ilkesi 'nin kullanılmış olduğu anlamına gelir (Ekler tarafından e-posta algılamaları için AdminOnlyAccessPolicy Kasa kullanılır). Daha sonra Ekleri Kasa ilkeyi düzenleyseniz veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir.

   - Algılanan **ekleri** olan iletileri yeniden yönlendirme: Yeniden yönlendirmeyi etkinleştir'i seçerse **çözümleme ve** soruşturma için kötü amaçlı yazılım ekleri içeren iletileri göndermek üzere, Engellenen **,** izlenen veya değiştirilmiş ekleri belirtilen e-posta adresi kutusuna gönder kutusunda bir e-posta adresi belirtebilirsiniz.

     Standart ve Katı ilke ayarları için öneri, yeniden yönlendirmeyi etkinleştirmektir. Daha fazla bilgi için Bkz[. Kasa ayarlarına bakın](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - Tarama **tamamlanmadı ise Kasa** Ekler algılama yanıtı uygulama (zaman aşımı veya hatalar): Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı tarafından belirtilen eylem, **Kasa** Ekler tarama tamamlanamasa bile iletilere alınır. Bu seçeneği belirttiğinizde her zaman Yeniden yönlendirmeyi **etkinleştir'i seçin** ve kötü amaçlı yazılım ekleri içeren iletileri göndermek için bir e-posta adresi belirtin. Aksi takdirde, iletiler kaybolabilir.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

7. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Ekleri Microsoft 365 Defender için Kasa portalını kullanma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri &** \>  \> Kuralları Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Kasa **Ekleri** sayfasında, ilkeler listesinde aşağıdaki özellikler görüntülenir:
   - **Ad**
   - **Durum**
   - **Öncelik**

3. Adına tıklayarak bir ilkeyi seçince, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Ekleri Microsoft 365 Defender ilkelerini değiştirmek Kasa portalını kullanma

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta** \> & İşbirliği **İlkeleri & Kuralları** \>  \> Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekleri **Kasa**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin önceki [Microsoft 365 Defender Ek ilkeleri oluşturmak Kasa](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) Portalını kullanma bölümüne bakın.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırası ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-safe-attachments-policies"></a>Ek İlkeleri Etkinleştirme Kasa devre dışı bırakma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri &** \>  \> Kuralları Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekleri **Kasa**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Eklerin önceliğini Kasa ilkeleri

Varsayılan olarak, Kasa ilkelerine oluşturulduklarına göre öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Öncelik sırası, birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

Kasa ek ilkeleri işlenme sırasına göre görüntülenir (ilk ilkenin **Öncelik** değeri 0'dır).

**Not**: Microsoft 365 Defender portalında, posta Ekleri Kasa önceliğini değiştirebilirsiniz. PowerShell'de, güvenli ek kuralı  oluşturmak (var olan kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

1. Microsoft 365 Defender portalında, İlkeler bölümünde **E-&** \> İşbirliği **İlkeleri &'ne** \>  \> Kasa Tehdit İlkeleri'ne gidin. 

2. Ekleri **Kasa**, adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, Geçerli öncelik değerine ve ilke sayısına göre Önceliği  artır veya Önceliği azalt'a bakın:
   - Öncelik değeri 0 **olan** ilke **yalnızca** Önceliğe azalt **seçeneğine** sahiptir.
   - En düşük Öncelik **değerine (** örneğin, 3) sahip **ilke** yalnızca Öncelik **artır seçeneğine** sahiptir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliğe **artır** hem de Öncelik azalt **seçeneklerine** sahiptir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Microsoft 365 Defender Attachments ilkelerini kaldırmak Kasa kullanma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri &** \>  \> Kuralları Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekleri **Kasa**, ilkenin adına tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

4. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Ek Exchange Online ilkelerini yapılandırmak için Exchange Online PowerShell veya tek başına EOP PowerShell Kasa kullanma

Daha önce açıklandığı gibi, Kasa Ekleri ilkesi, güvenli bir ek ilkesi ve güvenli bir ek kuralıdan oluşur.

PowerShell'de, güvenli ek ilkeleriyle güvenli ek kuralları arasındaki fark görünür. Güvenli ek **\*ilkelerini yönetmek için -SafeAttachmentPolicy** cmdlet'lerini **\*ve güvenilir ek kurallarını da -SafeAttachmentRule** cmdlet'lerini kullanarak yönetirsiniz.

- PowerShell'de önce güvenli ek ilkesi oluşturun, sonra da kuralın geçerli olduğu ilkeyi tanımlayan güvenli ek kuralını oluşturun.
- PowerShell'de, güvenli ek ilkesi ve güvenli ek kuralı ayarlarını ayrıca değiştirirsiniz.
- PowerShell'den güvenli bir ek ilkesi kaldırırken, buna karşılık gelen güvenli ek kuralı otomatik olarak kaldırılamaz ve tersi de geçerlidir.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Ek ilkeleri oluşturmak için PowerShell Kasa kullanma

PowerShell Kasa te Ekleri Oluşturma ilkesi iki adımlı bir işlemdir:

1. Güvenli ek ilkesi oluşturun.
2. Kuralın geçerli olduğu güvenli ek ilkesi belirten güvenli ek kuralı oluşturun.

 **Notlar**:

- Yeni bir güvenli ek kuralı oluşturabilir ve bu kurala varolan, ilişkilendirilmemiş bir güvenli ek ilkesi atabilirsiniz. Güvenli bir ek kuralı birden çok güvenli ek ilkesiyle ilişkilendirilz.

- İlkeyi oluşturmadan önce, PowerShell portalında kullanılabilen yeni güvenli ek Microsoft 365 Defender ilkelerde aşağıdaki ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı olarak _oluşturun (_ `$false` **New-SafeAttachmentRule cmdlet'inde** etkin).
  - Oluşturma sırasında ilkenin önceliğini _(__\<Number\>_ Öncelik ) **New-SafeAttachmentRule** cmdlet'inde ayarlayın.

- PowerShell'de yeni bir güvenli ek ilkesi oluşturmanız, siz ilkeyi güvenli bir ek kuralına atayana kadar Microsoft 365 Defender portalda görünmez.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>1. Adım: Güvenli bir ek ilkesi oluşturmak için PowerShell kullanma

Güvenli bir ek ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

Bu örnek, aşağıdaki değerleri içeren Contoso All adlı güvenli bir ek ilkesi oluşturur:

- Belgeler tarama (_Action_ parametresi kullanacağız ve varsayılan değer de Kasa) ile kötü amaçlı yazılım içermesi bulunan iletileri engel tutun`Block`.
- Varsayılan karantina [ilkesi kullanılır](quarantine-policies.md) (AdminOnlyAccessPolicy), çünkü _Karantina Etiketini parametresi kullanmayız_ .
- Yeniden yönlendirme etkinleştirilir ve kötü amaçlı yazılım içerdiği bulunan iletiler çözümleme ve soruşturma için sec-ops@contoso.com'e gönderilir.
- Başka Kasa Ekler tarama kullanılamıyorsa veya hatalarla karşılaşıyorsa iletiyi teslim etme (_ActionOnError_ parametresi kullanacağız ve varsayılan değer de ).`$true`

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Güvenli ek ilkesinde kullanmak [üzere karantina](quarantine-policies.md) ilkesi belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#safe-attachments-policies-in-powershell) Ekler ilkeleri içinde karantina Kasa kullanma.

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>2. Adım: Güvenli bir ek kuralı oluşturmak için PowerShell kullanma

Güvenli bir ek kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Bu örnek, aşağıdaki koşulları içeren Contoso All adlı güvenli bir ek kuralı oluşturur:

- Kural, Contoso All adlı güvenli ek ilkesiyle ilişkilendirildi.
- Kural, etki alanındaki tüm alıcılar için contoso.com geçerlidir.
- Öncelik parametresi kullanılmay _olduğundan,_ varsayılan öncelik kullanılır.
- Kural etkinleştirilir ( _Enabled_ parametresi bizim değil ve varsayılan değer: `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Güvenli ek ilkelerini görüntülemek için PowerShell kullanma

Varolan güvenli ek ilkelerini görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli ek ilkelerinin özet bir listesini döndürür.

```PowerShell
Get-SafeAttachmentPolicy
```

Bu örnek, Contoso Yöneticiler adlı güvenli ek ilkesi için ayrıntılı bilgi döndürür.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Güvenli ek kurallarını görüntülemek için PowerShell kullanma

Var olan güvenli ek kurallarını görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli ek kurallarının özet listesini döndürür.

```PowerShell
Get-SafeAttachmentRule
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

Bu örnek, Contoso Yöneticiler adlı güvenli ek kuralı için ayrıntılı bilgi döndürür.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Güvenli ek ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de güvenli ek ilkesi yeniden adlandırılamaz ( **Set-SafeAttachmentPolicy** cmdlet'in _Name_ parametresi yoktur). E-posta Kasa Ekleri Microsoft 365 Defender yeniden adlandırıyorken, yalnızca güvenli ek kuralını yeniden _adlandırıyor olursunuz_.

Bunun dışında, aynı ayarlar 1. Adım [: PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) kullanarak bu makalenin önceki kısımlarında güvenli bir ek ilkesi oluşturmak için kullanma bölümünde açıklandığı gibi kullanılabilir.

Güvenli ek ilkesi değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Güvenli ek ilkesinde kullanmak [üzere karantina](quarantine-policies.md) ilkesi belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#safe-attachments-policies-in-powershell) Ekler ilkeleri içinde karantina Kasa kullanma.

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Güvenli ek kurallarını değiştirmek için PowerShell kullanma

PowerShell'de güvenli ek kuralını değiştirirken kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza  olanak sağlayan Enabled parametresidir. Var olan güvenli ek kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, aynı ayarları 2. Adım [: PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) kullanarak bu makalenin başlarındaki Güvenli ek kuralı oluşturmak için kullanma bölümünde açıklanan kural 2.

Güvenli ek kuralını değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Güvenli ek kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de güvenli ek kuralının etkinleştirilmesi veya devre dışı bırakılması, Kasa Ek İlkesinin tamamını (güvenli ek kuralı ve atanmış güvenli ek ilkesi) etkinleştirir veya devre dışı açıklar.

PowerShell'de güvenli ek kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimi kullanın:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Bölümü adlı güvenli ek kuralı devre dışı bırak).

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Enable-SafeAttachmentRule ve](/powershell/module/exchange/enable-safeattachmentrule) [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Güvenli ek kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de güvenli ek kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Not**: Yeni kuralı irken önceliğini ayarlamak için, onun yerine **New-SafeAttachmentRule** cmdlet'inin Öncelik parametresini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Güvenli ek ilkelerini kaldırmak için PowerShell kullanma

Güvenli bir ek ilkesi kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen güvenli ek kuralı kaldırılamaz.

PowerShell'de güvenli ek ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı güvenli ek ilkesi kaldırabilirsiniz.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Güvenli ek kurallarını kaldırmak için PowerShell kullanma

Güvenli bir ek kuralını kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen güvenli ek ilkesi kaldırılamaz.

PowerShell'de güvenli ek kuralını kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Bölümü adlı güvenli ek kuralını kaldırır.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Ekler ilkelerini başarıyla oluşturduğunuz, değiştir doğrulamanız veya Kasa için, aşağıdaki adımlardan herhangi birini yapın:

- Microsoft 365 Defender **portalında**<https://security.microsoft.com/safeattachmentv2>, Kasa Ekleri sayfasında, ilkelerin listesini, Durum değerlerini ve  **Öncelik değerlerini doğrulayın**. Daha fazla ayrıntı görüntülemek için, adı tıklatarak listeden ilkeyi seçin ve ayrıntıları uçarak görüntüye geçin.

- PowerShell Exchange Online veya Exchange Online Protection PowerShell'de, \<Name\> ilke veya kuralın adıyla değiştirin, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Eklerin iletileri Kasa doğrulamak için, kullanılabilir Dosya için Defender'ı Office 365 kontrol edin. Daha fazla bilgi için bkz[. Office 365 için Defender raporlarını görüntüleme](view-reports-for-mdo.md) ve Microsoft 365 Defender [kullanın](threat-explorer.md).
