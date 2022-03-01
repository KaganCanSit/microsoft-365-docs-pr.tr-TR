---
title: EOP'de kimlik avı önleme ilkelerini yapılandırma
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
description: Yöneticiler, Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan veya olmayan kuruluşlarda bulunan kimlik avı önleme ilkelerinin nasıl oluşturulsa, değiştiriliyor ve Exchange Online öğrenilebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6321dcb41e276ccd03d048033e063572506a3c0f
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010917"
---
# <a name="configure-anti-phishing-policies-in-eop"></a>EOP'de kimlik avı önleme ilkelerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu olan Exchange Online kuruluşlarda, sınırlı sayıda kimlik sahtesi önleme özelliği içeren, varsayılan kimlik avı önleme ilkesi vardır. varsayılan olarak ayarlar. Daha fazla bilgi için bkz [. Kimlik avı önleme ilkelerde kimlik avı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

Yöneticiler varsayılan kimlik avı önleme ilkesi  görüntüleyemez, düzenleyebilir ve yapılandırsa da (ancak silemez). Daha ayrıntılı bilgi için, aynı zamanda, kurumlu belirli kullanıcılara, gruplara veya etki alanlarına uygulanacak özel kimlik avı ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliğe sahiptir, ancak özel ilkelerinizin önceliğini (çalışma sırası) değiştirebilirsiniz.

Posta kutuları Exchange Online kuruluşlar, Microsoft 365 Defender portalında veya Exchange Online PowerShell'de kimlik avı önleme ilkelerini yapılandırabilirsiniz. Tek başına EOP kuruluşları yalnızca Microsoft 365 Defender kullanabilir.

Office 365 için Microsoft Defender'da bulunan daha gelişmiş kimlik avı önleme ilkelerini oluşturma ve değiştirme hakkında bilgi için bkz. Office 365 için [Microsoft Defender'da](configure-mdo-anti-phishing-policies.md) kimlik avı koruma ilkelerini yapılandırma.

Kimlik avı önleme ilkesi için temel öğeler:

- **Kimlik avı koruma ilkesi**: Etkinleştirmek veya devre dışı bırakmak için kimlik avı korumalarını ve seçeneklerin uygulanacak eylemlerini belirtir.
- **Kimlik avı koruma kuralı**: Kimlik avı önleme ilkesi için önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Bu iki öğe arasındaki fark, kimlik avı önleme ilkelerini aşağıdaki portalda yönetirken Microsoft 365 Defender değildir:

- Kimlik avı önleme ilkesi  oluştururken, aslında bir kimlik avı önleme kuralı ve her ikisi için de aynı adı kullanarak ilişkili kimlik avı önleme ilkesi oluştur etmiş olursunuz.
- Kimlik avı koruma ilkesi değiştirildiğinde ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri kimlik avı koruma kuralını değiştirir. Diğer tüm ayarlar, ilişkili kimlik avı önleme ilkesine değişiklik sağlar.
- Kimlik avı önleme ilkesi kaldırılmışsa, kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesi kaldırılır.

PowerShell Exchange Online, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu [makalenin devam Exchange Online kimlik](#use-exchange-online-powershell-to-configure-anti-phishing-policies) avı ilkelerini yapılandırmak için PowerShell kullanma bölümüne bakın.

Her kuruluşun, şu özelliklere sahip Office365 AntiPhish Default adlı yerleşik kimlik avı önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş kimlik avı koruma kuralı (alıcı filtreleri) her ne kadar ilke kuruluşta yer alan tüm alıcılara uygulanır.
- İlke, değiştiriy **olmadığınız** en düşük özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Sizin kendi özel ilkeleriniz her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **değeri IsDefault** özelliğine `True`sahip) ve varsayılan ilkeyi silemezsiniz.

Kimlik avı korumasının etkisini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha sıkı ayarlarla özel kimlik avı önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

  Tek başına EOP PowerShell'de kimlik avı önleme ilkelerini yönetesiniz.

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Kimlik avı önleme ilkeleri eklemek, değiştirmek ve silmek için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olun**.
  - Kimlik avı önleme ilkelerine salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel özellik için salt okunur erişim de sağlar <sup>\*</sup>.

- Kimlik avı önleme ilkeleri için önerilen ayarlarımız için bkz. [EOP kimlik avı koruma ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

- Güncelleştirilmiş ilkenin uygulanması için 30 dakika kadar bekleyin.

- Kimlik avı önleme ilkelerinin filtre potansiyelinde nereye uygulandığı hakkında bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkeleri oluşturmak için kimlik avı portalını kullanma

Microsoft 365 Defender portalında özel bir kimlik avı önleme ilkesi oluşturmak, hem kimlik avı önleme kuralını hem de her ikisi için aynı adı kullanarak ilişkili kimlik avı önleme ilkesi oluşturur.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik avı **önleme sayfasında, Oluştur** simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Oluştur'a iki tablo da oluşturabilirsiniz**

3. İlke sihirbazı açılır. İlke **adı sayfasında** şu ayarları yapılandırabilirsiniz:
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

5. Görüntülenen **Kimlik avı & koruma** sayfasında Kimlik sahtesi zekasını etkinleştir onay kutusunu kullanarak kimlik  sahtesi zekasını açın veya kapatın. Varsayılan değer açık (seçili) ve bu değeri açık bırakmanız önerilir. Bir sonraki sayfada engellenen kimlik e-postalarını alacak eylemi yapılandırabilirsiniz.

   Akıllı ifadeyi kapatmak için onay kutusunu temizleyin.

   > [!NOTE]
   > MX kaydınız Ilkeler'e işaret Microsoft 365, bunun yerine Bağlayıcılar için Geliştirilmiş Filtreleme'yi etkinleştirirsiniz. Yönergeler için bkz. [Exchange Online'ta Bağlayıcılar için İyileştirilmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **İleti, ifade olarak algılanırsa**: Bu ayar yalnızca önceki sayfada Bilgi yok olarak etkinleştir'i **seçtiyseniz** kullanılabilir. Engellenen engellenen gönderenlerden gelen iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
     - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
     - **İletiyi karantinaya** alın: Bu eylemi seçerseniz,  akıllı durum korumasıyla karantinaya alınan iletilere uygulanan karantina ilkesi seçen bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

       Boş karantina **ilkesi değeri uygula** değeri, varsayılan karantina ilkesi'nin kullanıldı olduğu anlamına gelir (akıllı ifade algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı koruma ilkesi düzenlense veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir. Desteklenen koruma filtreleme kararlarında kullanılan varsayılan karantina ilkeleri hakkında daha fazla bilgi için bu tabloya [bakın](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Güvenlik ipuçları & göstergeleri**:
     - **İlk kişi bilgilerini güvenlik ipucu**: Daha fazla bilgi için bkz. [İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - Kimlik bilgisi için kimliği doğrulanmamış gönderenler için **göster (?**<sup>\*</sup>) : İleti SPF veya DKIM denetimlerini geçese ve ileti DMARC veya bileşik kimlik doğrulamasını geçese, Outlook'deki Gönderen kutusunda gönderenin fotoğrafına  bir soru işareti (?) [ekler.](email-validation-and-authentication.md#composite-authentication)
     - **"Aracılığıyla"**<sup>\*</sup> etiketini göster: DKIM imzası veya **MAIL FROM** adresi etki alanı farklı ise, Gönderen adresine aracılığıyla etiketi (chris@contoso.com aracılığıyla fabrikam.com) ekler.

     Ayarı açmak için onay kutusunu seçin. Kapatmak için onay kutusunu temizleyin.

     <sup>\*</sup> Bu ayar yalnızca önceki sayfada Akıllı **ifadeyi etkinleştir'i** seçtiyseniz kullanılabilir. Daha fazla bilgi için bkz [. Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

8. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkelerini görüntülemek için kimlik avı portalını kullanma

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , ilkeler listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Son değiştirme**

3. Adına tıklayarak bir ilkeyi seçince, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkelerini değiştirmek için Kimlik avı portalını kullanma

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı koruması sayfasında** , adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin önceki [Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) kimlik avı ilkeleri oluşturmak için Kimlik avı portalını kullanma bölümüne bakın.

   Varsayılan kimlik avı önleme ilkesi için, **Kullanıcılar,** gruplar ve etki alanları bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandırılamaz.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırası ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan kimlik avı önleme ilkesi devre dışı bırakılamaz.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , adı tıklatarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, kimlik avı önleme ilkelerine, oluşturulduklarına dayalı olarak öncelik verilir (daha yeni ilkeler, eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, kimlik avı önleme ilkesi önceliğini, oluşturduklardan sonra değiştirebilirsiniz. PowerShell'de, kimlik avı önleme kuralı 2007'de 00.000'de (mevcut kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- Kimlik avı önleme ilkeleri, görüntülenme sırasına göre işlenir (ilk ilkenin Öncelik değeri 0'dır). Varsayılan kimlik avı önleme ilkesi En düşük **öncelik değerine** sahiptir ve bunu değiştiremezsiniz.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , adı tıklatarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, geçerli öncelik değerine ve özel ilke  sayısına göre  Önceliği artır veya Önceliği azalt'a bakın:
   - Öncelik değeri 0 **olan** ilke **yalnızca** Önceliğe azalt **seçeneğine** sahiptir.
   - En düşük Öncelik **değerine (** örneğin, 3) sahip **ilke** yalnızca Öncelik **artır seçeneğine** sahiptir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliğe **artır** hem de Öncelik azalt **seçeneklerine** sahiptir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Özel kimlik Microsoft 365 Defender ilkelerini kaldırmak için Kimlik avı portalını kullanma

Özel bir kimlik Microsoft 365 Defender ilkeyi kaldırmak için Kimlik avı önleme portalını kullanırken, kimlik avı önleme kuralı ve buna karşılık gelen kimlik avı önleme ilkesi de silinir. Varsayılan kimlik avı önleme ilkesi kaldıramayr.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , adı tıklatarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

4. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Kimlik Exchange Online ilkelerini yapılandırmak için PowerShell'i kullanma

Daha önce açıklandığı gibi, kimlik avı önleme ilkesi bir kimlik avı önleme ilkesi ve kimlik avı önleme kuralıdan oluşur.

Bir Exchange Online PowerShell'de, kimlik avı koruma ilkeleriyle kimlik avı koruma kuralları arasındaki fark görünür. Kimlik avı önleme **\*ilkelerini, -AntiPhishPolicy** cmdlet'lerini ve kimlik avı önleme kurallarını **da -AntiPhishRule cmdlet'lerini\*** kullanarak yönetirsiniz.

- PowerShell'de önce kimlik avı önleme ilkesi oluşturun, sonra da kuralın geçerli olduğu ilkeyi tanımlayan kimlik avı önleme kuralını oluşturun.
- PowerShell'de, kimlik avı önleme ilkesi ve kimlik avı koruma kuralı ayarlarını ayrı ayrı değiştirirsiniz.
- PowerShell'den bir kimlik avı koruma ilkesi kaldırılmışsa, buna karşılık gelen kimlik avı önleme kuralı otomatik olarak kaldırılamaz ve bunun tersi de geçerlidir.

> [!NOTE]
> Aşağıdaki PowerShell yordamları, Exchange Online Protection PowerShell kullanan tek başına EOP Exchange Online Protection değildir.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>PowerShell kullanarak kimlik avı önleme ilkeleri oluşturma

PowerShell'de kimlik avına karşı koruma ilkesi oluşturmak iki adımlı bir işlemdir:

1. Kimlik avı önleme ilkesi oluşturun.
2. Kuralın geçerli olduğu kimlik avı önleme ilkesine yönelik kimlik avı önleme kuralını oluşturun.

 **Notlar**:

- Yeni bir kimlik avı önleme kuralı oluşturabilir ve bu kurala var olan, ilişkilendirilmemiş bir kimlik avı koruma ilkesi atfingingniz olabilir. Kimlik avı koruma kuralı birden çok kimlik avı önleme ilkesiyle ilişkilendirilz.

- İlkeyi oluşturmadan önce, PowerShell'de Microsoft 365 Defender portalında olmayan yeni kimlik avı önleme ilkelerde aşağıdaki ayarları yapılandırabilirsiniz:

  - Yeni ilkeyi devre dışı olarak _oluşturun (_ `$false` **New-AntiPhishRule cmdlet'inde** etkin).
  - Yeni-AntiPhishRule cmdlet'inde oluşturma sırasında **ilkenin önceliğini** _ayarlayın (__\<Number\>_ Öncelik).

- PowerShell'de yeni bir kimlik avı koruma ilkesi, siz bu ilkeyi bir kimlik avı koruma kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>1. Adım: Kimlik avı önleme ilkesi oluşturmak için PowerShell kullanma

Kimlik avı önleme ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSpoofIntelligence <$true | $false>] [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableUnauthenticatedSender <$true | $false>] [-EnableViaTag <$true | $false>] [-SpoofQuarantineTag <QuarantineTagName>]
```

Bu örnek, aşağıdaki ayarlarla Araştırma Karantinası adlı bir kimlik avı koruma ilkesi oluşturur:

- Açıklama şöyledir: Araştırma bölümü ilkesi.
- Kullanıcı adı kullanma algılamaları için varsayılan eylemi Karantina olarak değiştirir ve karantinaya alınmış iletiler için [](quarantine-policies.md) varsayılan karantina ilkesi kullanır (_SpoofQuarantineTag parametresi_ kullanacağız).

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme ilkesinde [kullanmak üzere](quarantine-policies.md) karantina ilkelerini belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#anti-phishing-policies) kimlik avı koruma ilkesinde karantina ilkesi belirtme.

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>2. Adım: PowerShell kullanarak kimlik avına karşı koruma kuralı oluşturma

Kimlik avı önleme kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, aşağıdaki koşulların yer alan Araştırma Bölümü adlı bir kimlik avına karşı koruma kuralı oluşturur:

- Kural, Araştırma Karantinası adlı kimlik avı koruma ilkesiyle ilişkilendirildi.
- Kural, Araştırma Bölümü adlı grubun üyeleri için geçerlidir.
- Öncelik parametresi kullanılmay _olduğundan,_ varsayılan öncelik kullanılır.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Kimlik avı koruma ilkelerini görüntülemek için PowerShell kullanma

Var olan kimlik avı koruma ilkelerini görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı koruma ilkelerinin özet bir listesini döndürür.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Bu örnek, Yöneticiler adlı kimlik avı önleme ilkesi için tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Kimlik avı koruma kurallarını görüntülemek için PowerShell kullanma

Var olan kimlik avı koruma kurallarını görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı kurallarının özet bir listesini döndürür.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Bu örnekte, Contoso Yöneticiler adlı kimlik avı koruma kuralı için tüm özellik değerleri döndürür.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Kimlik avı koruma ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de kimlik avı önleme ilkesinde değişiklik yapmak için 1. Adım: Bu makalenin başlarındaki Kimlik avı önleme ilkesi oluşturmak için [PowerShell'i](#step-1-use-powershell-to-create-an-anti-phish-policy) kullanma konusunda açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır **, her zaman** En düşük öncelikli ve bunu silemezsiniz) yalnızca PowerShell'de kimlik avı önleme ilkesinde değişiklik yapmak için kullanılabilir.
- Kimlik avı koruma ilkesi yeniden adlandırılamaz ( **Set-AntiPhishPolicy** cmdlet'in _Name_ parametresi yoktur). Bu portalda kimlik avı önleme ilkesine Microsoft 365 Defender, yalnızca kimlik avı koruma kuralını yeniden _adlandırıyor olursunuz_.

Kimlik avı önleme ilkesi değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishPolicy Ayarlama](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme ilkesinde [kullanmak üzere karantina](quarantine-policies.md) ilkesi belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#anti-phishing-policies) kimlik avı koruma ilkesinde karantina ilkesi belirtme.

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Kimlik avı koruma kurallarını değiştirmek için PowerShell kullanma

PowerShell'de kimlik avı koruma kuralını değiştirirken kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza  olanak sağlayan Enabled parametresidir. Kimlik avı koruma kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, aynı ayarları 2. Adım [: PowerShell](#step-2-use-powershell-to-create-an-anti-phish-rule) kullanarak bu makalenin başlarındaki Kimlik avı önleme kuralı bölümünde açıklandığı gibi bir kural oluşturmak için de kullanabilirsiniz.

Kimlik avı önleme kuralını değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishRule Ayarlama](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Kimlik avı koruma kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de kimlik avı koruma kuralının etkinleştirilmesi veya devre dışı bırakılması, tüm kimlik avı koruma ilkesi (kimlik avı koruma kuralı ve atanmış kimlik avı önleme ilkesi) etkinleştir veya devre dışı bırak. Varsayılan kimlik avı önleme ilkesi (her zaman tüm alıcılara uygulanır) etkinleştir veya devre dışı bırakasınız.

PowerShell'de kimlik avı önleme kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimlerini kullanın:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme kuralı devre dışı bırak).

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishRule'yi etkinleştirme ve](/powershell/module/exchange/enable-antiphishrule) [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Kimlik avı önleme kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de kimlik avı önleme kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı irken önceliğini ayarlamak için, bunun yerine **New-AntiPhishRule** cmdlet'inin Öncelik parametresini kullanın.
- Varsayılan kimlik avı önleme ilkesine karşılık gelen kimlik avı önleme kuralı yoktur ve her zaman En Düşük değiştirilmez öncelik **değerine sahiptir**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Kimlik avı önleme ilkelerini kaldırmak için PowerShell kullanma

Kimlik avı önleme ilkesi kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen kimlik avı önleme kuralı kaldırılamaz.

PowerShell'de kimlik avı önleme ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme ilkesi kaldır).

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Kimlik avı koruma kurallarını kaldırmak için PowerShell kullanma

Kimlik avı koruma kuralını kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen kimlik avı önleme ilkesi kaldırılamaz.

PowerShell'de kimlik avı önleme kuralını kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme kuralı kaldır).

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. AntiPhishRule'i kaldırma](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

EOP'de kimlik avı koruma ilkelerini başarıyla yapılandırıldığından emin olmak için, aşağıdaki adımlardan birini uygulayın:

- Microsoft 365 Defender portalında kimlik avıyla mücadele sayfasında, ilkelerin listesini, Durum değerlerini ve **Öncelik değerlerini doğrulayın**.  <https://security.microsoft.com/antiphishing> Daha fazla ayrıntı görüntülemek için, adı tıklatarak ve beliren açılır listede ayrıntıları görüntüerek listeden ilkeyi seçin.

- PowerShell Exchange Online, ilke \<Name\> veya kuralın adıyla değiştirin, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
