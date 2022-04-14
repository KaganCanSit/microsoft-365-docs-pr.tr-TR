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
description: Yöneticiler, Exchange Online posta kutuları olan veya olmayan Exchange Online Protection (EOP) kuruluşlarında kullanılabilen kimlik avı önleme ilkelerini oluşturmayı, değiştirmeyi ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f199cb3dbaddc47416c24a82b3066a2631641706
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847409"
---
# <a name="configure-anti-phishing-policies-in-eop"></a>EOP'de kimlik avı önleme ilkelerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, etkinleştirilmiş sınırlı sayıda kimlik sahtekarlığı önleme özelliği içeren varsayılan bir kimlik avı önleme ilkesi vardır varsayılan olarak. Daha fazla bilgi için bkz. [Kimlik avı önleme ilkelerindeki kimlik sahtekarlığı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

Yöneticiler varsayılan kimlik avı önleme ilkesini görüntüleyebilir, düzenleyebilir ve yapılandırabilir (ancak silemez). Daha fazla ayrıntı düzeyi için, kuruluşunuzdaki belirli kullanıcılar, gruplar veya etki alanları için geçerli olan özel kimlik avı önleme ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliklidir, ancak özel ilkelerinizin önceliğini (çalıştırma sırasını) değiştirebilirsiniz.

Exchange Online posta kutuları olan kuruluşlar, Microsoft 365 Defender portalında veya Exchange Online PowerShell'de kimlik avı önleme ilkeleri yapılandırabilir. Tek başına EOP kuruluşları yalnızca Microsoft 365 Defender portalını kullanabilir.

Office 365 için Microsoft Defender'de kullanılabilen daha gelişmiş kimlik avı önleme ilkelerini oluşturma ve değiştirme hakkında bilgi için bkz. [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

Kimlik avı önleme ilkesinin temel öğeleri şunlardır:

- **Kimlik avı önleme ilkesi**: Etkinleştirecek veya devre dışı bırakacağınız kimlik avı korumalarını ve seçeneklerin uygulanacağı eylemleri belirtir.
- **Kimlik avı önleme kuralı: Kimlik avı** önleme ilkesi için öncelik ve alıcı filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında kimlik avı önleme ilkelerini yönetirken bu iki öğe arasındaki fark belirgin değildir:

- Kimlik avı önleme ilkesi oluşturduğunuzda, her ikisi için de aynı adı kullanarak kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesini aynı anda oluşturursunuz.
- Kimlik avı önleme ilkesini değiştirdiğinizde ad, öncelik, etkin veya devre dışı ayarları ve alıcı filtreleri kimlik avı önleme kuralını değiştirir. Diğer tüm ayarlar ilişkili kimlik avı önleme ilkesini değiştirir.
- Bir kimlik avı önleme ilkesini kaldırdığınızda, kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesi kaldırılır.

Exchange Online PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için bu makalenin devamında yer alan [Kimlik avı önleme ilkelerini yapılandırmak için PowerShell Exchange Online kullanma](#use-exchange-online-powershell-to-configure-anti-phishing-policies) bölümüne bakın.

Her kuruluşun şu özelliklere sahip Office365 AntiPhish Default adlı yerleşik bir kimlik avı önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş kimlik avı önleme kuralı (alıcı filtreleri) olmasa bile ilke kuruluştaki tüm alıcılara uygulanır.
- İlke, değiştiremezseniz **en düşük** özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Oluşturduğunuz tüm özel ilkeler her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **IsDefault** özelliği değerine `True`sahiptir) ve varsayılan ilkeyi silemezsiniz.

Kimlik avı korumasının verimliliğini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha katı ayarlara sahip özel kimlik avı önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

  Tek başına EOP PowerShell'de kimlik avı önleme ilkelerini yönetemezsiniz.

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Kimlik avı önleme ilkelerini eklemek, değiştirmek ve silmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Kimlik avı önleme ilkelerine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'deki](/Exchange/permissions-exo/permissions-exo#role-groups) **Salt Okunur Kuruluş Yönetimi** rol grubu da özelliğe <sup>\*</sup> salt okunur erişim sağlar.

- Kimlik avı önleme ilkeleri için önerilen ayarlarımız için bkz. [EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

- Güncelleştirilmiş ilkenin uygulanması için 30 dakikaya kadar bekleyin.

- Filtreleme işlem hattında kimlik avı önleme ilkelerinin nereye uygulandığı hakkında bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Kimlik avı önleme ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel kimlik avı önleme ilkesi oluşturmak, her ikisi için de aynı adı kullanarak kimlik avı önleme kuralını ve ilişkili kimlik avı önleme ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Oluştur'u seçin**.

3. İlke sihirbazı açılır. **İlke adı** sayfasında şu ayarları yapılandırın:
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

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Görüntülenen **Kimlik avı eşiği & koruma** sayfasında, kimlik **sahtekarlığı zekasını açmak veya kapatmak için Kimlik sahtekarlığı zekasını etkinleştir** onay kutusunu kullanın. Varsayılan değer açık (seçili) ve açık bırakmanızı öneririz. Eylemi bir sonraki sayfada engellenen sahte iletilerde gerçekleştirecek şekilde yapılandıracaksınız.

   Kimlik sahtekarlık zekasını kapatmak için onay kutusunu temizleyin.

   > [!NOTE]
   > MX kaydınız Microsoft 365 işaret etmiyorsa kimlik sahtekarlığı önleme korumasını kapatmanız gerekmez; bunun yerine Bağlayıcılar için Gelişmiş Filtreleme'yi etkinleştirirsiniz. Yönergeler için bkz. [Exchange Online'da Bağlayıcılar için Gelişmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırın:
   - **İleti sahte olarak algılanırsa**: Bu ayar yalnızca önceki sayfada **Kimlik sahtekarlığına izin verin'i** seçtiğinizde kullanılabilir. Engellenen sahte gönderenlerden gelen iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
     - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
     - **İletiyi karantinaya alma**: Bu eylemi seçerseniz, **kimlik sahtekarlığına karşı koruma tarafından karantinaya** alınan iletilere uygulanan karantina ilkesini seçtiğiniz bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

       Boş **Bir Karantina ilkesi değeri uygula** , varsayılan karantina ilkesinin kullanıldığı anlamına gelir (kimlik sahtekarlığı zekası algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı önleme ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir. Desteklenen koruma filtreleme kararları için kullanılan varsayılan karantina ilkeleri hakkında daha fazla bilgi için [bu tabloya](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) bakın.

   - **Güvenlik ipuçları & göstergeler**:
     - **İlk kişi güvenlik ipucu göster**: Daha fazla bilgi için bkz. [İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - Kimlik **sahtekarlığına yönelik kimliği doğrulanmamış gönderenler**<sup>\*</sup> için göster (?) : İleti SPF veya DKIM denetimlerini geçmezse **ve** ileti DMARC veya [bileşik kimlik doğrulamasını](email-validation-and-authentication.md#composite-authentication) geçmezse Outlook Kimden kutusunda gönderenin fotoğrafına soru işareti (?) ekler.
     - **"via" etiketini**<sup>\*</sup> göster: DKIM imzasında etki alanından veya **MAIL FROM** adresinden farklıysa Kimden adresine bir via etiketi (fabrikam.com aracılığıyla chris@contoso.com) ekler.

     Bir ayarı açmak için onay kutusunu seçin. Kapatmak için onay kutusunu temizleyin.

     <sup>\*</sup> Bu ayar yalnızca önceki sayfada **Kimlik sahtekarı zekasını etkinleştir'i** seçtiğinizde kullanılabilir. Daha fazla bilgi için bkz. [Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).

   İşiniz bittiğinde **İleri'ye** tıklayın.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

8. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ilkeler listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Son değiştirme**

3. Ada tıklayarak bir ilke seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için bu [makalenin önceki bölümlerinde yer alan Microsoft 365 Defender portalını kullanarak kimlik avı önleme ilkeleri oluşturma](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) bölümüne bakın.

   Varsayılan kimlik avı önleme ilkesi için **Kullanıcılar, gruplar ve etki alanları** bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandıramazsınız.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırasını ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan kimlik avı önleme ilkesini devre dışı bırakamazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, kimlik avı önleme ilkelerine oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, kimlik avı önleme ilkesinin önceliğini yalnızca oluşturduktan sonra değiştirebilirsiniz. PowerShell'de, kimlik avı önleme kuralını oluştururken varsayılan önceliği geçersiz kılabilirsiniz (bu, mevcut kuralların önceliğini etkileyebilir).
- Kimlik avı önleme ilkeleri, görüntülendikleri sırayla işlenir (ilk **ilkenin Öncelik** değeri 0'dır). Varsayılan kimlik avı önleme ilkesi **En düşük** öncelik değerine sahiptir ve bunu değiştiremezsiniz.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve özel ilkelerin sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan ilkede yalnızca **Önceliği azalt** seçeneği kullanılabilir.
   - En düşük **Öncelik** değerine sahip ilke (örneğin, **3**) yalnızca **Önceliği artır** seçeneği kullanılabilir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelik değerleri arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

Özel bir kimlik avı önleme ilkesini kaldırmak için Microsoft 365 Defender portalını kullandığınızda, kimlik avı önleme kuralı ve buna karşılık gelen kimlik avı önleme ilkesi silinir. Varsayılan kimlik avı önleme ilkesini kaldıramazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

4. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini yapılandırmak için Exchange Online PowerShell kullanma

Daha önce açıklandığı gibi, kimlik avı önleme ilkesi bir kimlik avı önleme ilkesinden ve kimlik avından koruma kuralından oluşur.

Exchange Online PowerShell'de kimlik avı önleme ilkeleriyle kimlik avı önleme kuralları arasındaki fark belirgindir. **-AntiPhishPolicy cmdlet'lerini kullanarak\*** kimlik avı önleme ilkelerini yönetirsiniz ve **-AntiPhishRule cmdlet'lerini kullanarak\*** kimlik avı önleme kurallarını yönetirsiniz.

- PowerShell'de önce kimlik avı önleme ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan kimlik avı önleme kuralını oluşturursunuz.
- PowerShell'de, kimlik avı önleme ilkesindeki ayarları ve kimlik avı önleme kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den kimlik avı önleme ilkesini kaldırdığınızda, buna karşılık gelen kimlik avı önleme kuralı otomatik olarak kaldırılmaz ve tam tersi de geçerlidir.

> [!NOTE]
> Aşağıdaki PowerShell yordamları, Exchange Online Protection PowerShell kullanan tek başına EOP kuruluşlarında kullanılamaz.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Kimlik avı önleme ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de kimlik avı önleme ilkesi oluşturmak iki adımlı bir işlemdir:

1. Kimlik avı önleme ilkesini oluşturun.
2. Kuralın geçerli olduğu kimlik avı önleme ilkesini belirten kimlik avı önleme kuralını oluşturun.

 **Notlar**:

- Yeni bir kimlik avı önleme kuralı oluşturabilir ve bu kurala mevcut, ilişkilendirilmemiş bir kimlik avı önleme ilkesi atayabilirsiniz. Kimlik avı önleme kuralı birden fazla kimlik avı önleme ilkesiyle ilişkilendirilebilir.

- İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni kimlik avı önleme ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:

  - Yeni ilkeyi devre dışı olarak oluşturun (**New-AntiPhishRule** cmdlet'inde _etkindir_`$false`).
  - **New-AntiPhishRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ _\<Number\>_ ayarlayın (Öncelik ).

- PowerShell'de oluşturduğunuz yeni bir kimlik avı önleme ilkesi, ilkeyi bir kimlik avı önleme kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>1. Adım: Kimlik avı önleme ilkesi oluşturmak için PowerShell kullanma

Kimlik avı önleme ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSpoofIntelligence <$true | $false>] [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableUnauthenticatedSender <$true | $false>] [-EnableViaTag <$true | $false>] [-SpoofQuarantineTag <QuarantineTagName>]
```

Bu örnek, aşağıdaki ayarlarla Research Quarantine adlı bir kimlik avı önleme ilkesi oluşturur:

- Açıklama: Araştırma departmanı ilkesi.
- Kimlik sahtekarlığı algılamaları için varsayılan eylemi Karantina olarak değiştirir ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanır ( _SpoofQuarantineTag_ parametresini kullanmıyoruz).

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme [ilkesinde kullanılacak karantina ilkelerini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. Kimlik [avı önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>2. Adım: Kimlik avı önleme kuralı oluşturmak için PowerShell kullanma

Kimlik avı önleme kuralı oluşturmak için şu sözdizimini kullanın:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, aşağıdaki koşullara sahip Araştırma Bölümü adlı bir kimlik avı önleme kuralı oluşturur:

- Kural, Araştırma Karantinası adlı kimlik avı önleme ilkesiyle ilişkilendirilir.
- Kural, Araştırma Bölümü adlı grubun üyeleri için geçerlidir.
- _Priority_ parametresini kullanmadığımız için varsayılan öncelik kullanılır.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Kimlik avı önleme ilkelerini görüntülemek için PowerShell kullanma

Mevcut kimlik avı önleme ilkelerini görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı önleme ilkelerinin özet listesini döndürür.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Bu örnek, Yöneticiler adlı kimlik avı önleme ilkesinin tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Kimlik avı önleme kurallarını görüntülemek için PowerShell kullanma

Mevcut kimlik avı önleme kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı önleme kurallarının özet listesini döndürür.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Bu örnek, Contoso Executives adlı kimlik avı önleme kuralının tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Kimlik avı önleme ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de kimlik avı önleme ilkesini değiştirdiğinizde, [1. Adım: PowerShell'i kullanarak](#step-1-use-powershell-to-create-an-anti-phish-policy) bu makalenin önceki bölümlerinde açıklanan kimlik avı önleme ilkesi oluşturma başlığı altında açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır, her zaman **En düşük** önceliklidir ve bunu silemezsiniz) yalnızca PowerShell'de kimlik avı önleme ilkesini değiştirdiğinizde kullanılabilir.
- Kimlik avı önleme ilkesini yeniden adlandıramazsınız ( **Set-AntiPhishPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında bir kimlik avı önleme ilkesini yeniden adlandırdığınızda, yalnızca kimlik avı önleme _kuralını_ yeniden adlandırırsınız.

Kimlik avı önleme ilkesini değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme [ilkesinde kullanılacak karantina ilkesini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. Kimlik [avı önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Kimlik avı önleme kurallarını değiştirmek için PowerShell kullanma

PowerShell'de kimlik avı önleme kuralını değiştirdiğinizde kullanılamayan tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Enabled_ parametresidir. Mevcut kimlik avı önleme kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak kimlik avından koruma kuralı oluşturma](#step-2-use-powershell-to-create-an-anti-phish-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

Kimlik avı önleme kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Kimlik avı önleme kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de kimlik avı önleme kuralının etkinleştirilmesi veya devre dışı bırakılması, kimlik avı önleme ilkesinin tamamını (kimlik avı önleme kuralı ve atanan kimlik avı önleme ilkesi) etkinleştirir veya devre dışı bırakır. Varsayılan kimlik avı önleme ilkesini etkinleştiremez veya devre dışı bırakamazsınız (her zaman tüm alıcılara uygulanır).

PowerShell'de kimlik avı önleme kuralını etkinleştirmek veya devre dışı bırakmak için şu sözdizimini kullanın:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme kuralını devre dışı bırakır.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) ve [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Kimlik avı önleme kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de kimlik avı önleme kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-AntiPhishRule** cmdlet'indeki _Priority_ parametresini kullanın.
- Varsayılan kimlik avı önleme ilkesinin karşılık gelen bir kimlik avı önleme kuralı yoktur ve her zaman **değiştirilemez öncelik değeri En Düşük'e** sahiptir.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Kimlik avı önleme ilkelerini kaldırmak için PowerShell kullanma

Bir kimlik avı önleme ilkesini kaldırmak için PowerShell kullandığınızda, buna karşılık gelen kimlik avı önleme kuralı kaldırılmaz.

PowerShell'de kimlik avı önleme ilkesini kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme ilkesini kaldırır.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Kimlik avı önleme kurallarını kaldırmak için PowerShell kullanma

PowerShell kullanarak kimlik avı önleme kuralını kaldırdığınızda, ilgili kimlik avı önleme ilkesi kaldırılmaz.

PowerShell'de kimlik avı önleme kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme kuralını kaldırır.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

EOP'de kimlik avı önleme ilkelerini başarıyla yapılandırdığınızdan emin olmak için aşağıdaki adımlardan birini yapın:

- konumundaki Microsoft 365 Defender portalındaki <https://security.microsoft.com/antiphishing>**Kimlik Avı önleme** sayfasında ilkelerin listesini, **Durum** değerlerini ve **Öncelik** değerlerini doğrulayın. Daha fazla ayrıntı görüntülemek için, ada tıklayıp görüntülenen açılır listede ayrıntıları görüntüleyerek ilkeyi seçin.

- Exchange Online PowerShell'de değerini ilke veya kuralın adıyla değiştirin\<Name\>, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
