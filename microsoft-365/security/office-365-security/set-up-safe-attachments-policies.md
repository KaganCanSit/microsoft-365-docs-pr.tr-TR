---
title: Office 365 için Microsoft Defender Kasa Ekler ilkelerini ayarlama
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
description: Kuruluşunuzu e-postadaki kötü amaçlı dosyalardan korumak için Kasa Ekler ilkelerini tanımlama hakkında bilgi edinin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 46b69c1bea0f967fe22c031397a8887f3399c99b
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115575"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender Kasa Ekler ilkelerini ayarlama

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, [Office 365 için Microsoft Defender](whats-new-in-defender-for-office-365.md) sahip iş müşterilerine yöneliktir. Outlook'da ek taraması hakkında bilgi arayan bir ev kullanıcısıysanız bkz. [Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Kasa Ekler[, Exchange Online Protection'da](whats-new-in-defender-for-office-365.md) [(EOP) kötü amaçlı yazılımdan koruma](anti-malware-protection.md) tarafından tarandıktan sonra gelen e-posta iletilerindeki ekleri denetlemek için, ancak alıcılara teslim etmeden önce sanal bir ortam kullanan Office 365 için Microsoft Defender bir özelliktir. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Kasa Ekler](safe-attachments.md).

Varsayılan Kasa Ekler ilkesi olmasa **da, Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tüm alıcılara Kasa Ekler koruması sağlar (özel Kasa Ekler ilkelerinde tanımlanmayan kullanıcılar). Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md). Belirli kullanıcılar, gruplar veya etki alanları için geçerli Kasa Ekler ilkeleri oluşturmak için bu makaledeki yordamları da kullanabilirsiniz.

Kasa Ekler ilkelerini Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online Exchange Online'de posta kutuları olan uygun Microsoft 365 kuruluşlar için PowerShell' de yapılandırabilirsiniz; tek başına EOP PowerShell posta kutularını Exchange Online, ancak Office 365 için Defender eklenti abonelikleriyle).

Kasa Ekler ilkesinin temel öğeleri şunlardır:

- **Güvenli ek ilkesi**: Bilinmeyen kötü amaçlı yazılım algılamaları için eylemleri, belirli bir e-posta adresine kötü amaçlı yazılım ekleri içeren iletilerin gönderilip gönderilmeyebileceğini ve Kasa Ekler taraması tamamlanamadıysa iletilerin teslim edilip edilmeyeceğini belirtir.
- **Güvenli ek kuralı**: Öncelik ve alıcı filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında Kasa Ekler ilkelerini yönetirken bu iki öğe arasındaki fark belirgin değildir:

- Kasa Ekler ilkesi oluşturduğunuzda, her ikisi için de aynı adı kullanarak aynı anda güvenli bir ek kuralı ve ilişkili güvenli ek ilkesi oluşturursunuz.
- Kasa Ekler ilkesini değiştirdiğinizde ad, öncelik, etkin veya devre dışı ile ilgili ayarlar ve alıcı filtreleri güvenli ek kuralını değiştirir. Diğer tüm ayarlar ilişkili güvenli ek ilkesini değiştirir.
- Kasa Ekler ilkesini kaldırdığınızda, güvenli ek kuralı ve ilişkili güvenli ek ilkesi kaldırılır.

Exchange Online PowerShell veya tek başına EOP PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin [devamında yer alan Kasa Ekler ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell Exchange Online kullanma](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) bölümüne bakın.

> [!NOTE]
> Kasa Ekler ayarlarının genel ayarlar alanında, Kasa Ekler ilkelerine bağımlı olmayan özellikleri yapılandırabilirsiniz. Yönergeler için bkz[. Microsoft 365 E5'da SharePoint, OneDrive, Microsoft Teams ve Kasa Belgeleri için](turn-on-mdo-for-spo-odb-and-teams.md) [Kasa Eklerini](safe-docs.md) Açma.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirmeden önce izinlere ihtiyacınız vardır:
  - Kasa Ekler ilkelerini oluşturmak, değiştirmek ve silmek için, Microsoft 365 Defender portalında **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi **ve** **Exchange Online'da Kuruluş Yönetimi** rol grubunun üyesi olmanız gerekir.
  - Kasa Ekler ilkelerine salt okunur erişim için, Microsoft 365 Defender portalında **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalındaki İzinler](permissions-microsoft-365-security-center.md) ve [Exchange Online'deki İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365'deki diğer özellikler için izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Kasa Ekler ilkeleri için önerilen ayarlarımız için bkz. [Ek ayarları Kasa](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Yeni veya güncelleştirilmiş bir ilkenin uygulanması için 30 dakikaya kadar bekleyin.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Kasa Ek ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel Kasa Ekleri ilkesi oluşturmak, her ikisi için de aynı adı kullanarak güvenli ek kuralını ve ilişkili güvenli ek ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Oluştur'u seçin**.

3. İlke sihirbazı açılır. **İlkenizi adlandırın** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. Görüntülenen **Kullanıcılar ve etki alanları** sayfasında, ilkenin geçerli olduğu iç alıcıları tanımlayın (alıcı koşulları):
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

5. **Ayarlar** sayfasında aşağıdaki ayarları yapılandırın:

   - **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı**: Aşağıdaki değerlerden birini seçin:
     - **Kapalı**: Genellikle bu değeri önermeyiz.
     - **Monitör**
     - **Engelle**: Bu varsayılan değerdir ve Standart ve Katı [önceden ayarlanmış güvenlik ilkelerinde](preset-security-policies.md) önerilen değerdir.
     - **Değiştirmek**
     - **Dinamik Teslim (Önizleme özelliği)**

     Bu değerler [Kasa Ekler ilke ayarlarında](safe-attachments.md#safe-attachments-policy-settings) açıklanmıştır.

   - **Karantina ilkesi**: Kasa Ekleri (**Engelle**, **Değiştir** veya **Dinamik Teslim**) tarafından karantinaya alınan iletilere uygulanan karantina ilkesini seçin. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

     Boş değer, varsayılan karantina ilkesinin kullanıldığı anlamına gelir (Kasa Ekler tarafından e-posta algılamaları için AdminOnlyAccessPolicy). Daha sonra Kasa Ekler ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir.

   - **Algılanan ekleri olan iletileri yeniden yönlendirme**: **Yeniden yönlendirmeyi etkinleştir'i** seçerseniz, Analiz ve araştırma amacıyla kötü amaçlı yazılım **ekleri içeren iletiler göndermek üzere Belirtilen e-posta adresine engellenen, izlenen veya değiştirilen ekler içeren iletileri gönder kutusunda bir e-posta** adresi belirtebilirsiniz.

     Standart ve Katı ilke ayarları için öneri, yeniden yönlendirmeyi etkinleştirmektir. Daha fazla bilgi için bkz. [Kasa Ekler ayarları](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - **Tarama tamamlanamadıysa Kasa Ekler algılama yanıtını uygulayın (zaman aşımı veya hatalar)**: **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı** tarafından belirtilen eylem, Kasa Ekler taraması tamamlanamadıklarında bile iletilerde gerçekleştirilen işlemdir. Bu seçeneği belirlediyseniz, her zaman **Yeniden yönlendirmeyi etkinleştir'i** seçin ve kötü amaçlı yazılım ekleri içeren iletiler göndermek için bir e-posta adresi belirtin. Aksi takdirde iletiler kaybolabilir.

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

7. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Kasa Ekler ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında, ilke listesinde aşağıdaki özellikler görüntülenir:
   - **Ad**
   - **Durum**
   - **Öncelik**

3. Ada tıklayarak bir ilke seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Kasa Ekler ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde** **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için, bu [makalenin önceki bölümlerinde yer alan Kasa Ekler ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) bölümüne bakın.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırasını ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-safe-attachments-policies"></a>Kasa Ek ilkelerini etkinleştirme veya devre dışı bırakma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Kasa Ek ilkelerinin önceliğini ayarlama

Varsayılan olarak, Kasa Ekler ilkelerine oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

Öncelik sırası ve birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

Kasa Ekler ilkeleri işlendikleri sırayla görüntülenir (ilk **ilkenin Öncelik** değeri 0'dır).

**Not**: Microsoft 365 Defender portalında, Kasa Ekler ilkesini oluşturduktan sonra önceliğini değiştirebilirsiniz. PowerShell'de, güvenli ek kuralını oluştururken varsayılan önceliği geçersiz kılabilirsiniz (bu, mevcut kuralların önceliğini etkileyebilir).

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

1. Microsoft 365 Defender portalında, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin.

2. **Kasa Ekler** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve ilke sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan ilkede yalnızca **Önceliği azalt** seçeneği kullanılabilir.
   - En düşük **Öncelik** değerine sahip ilke (örneğin, **3**) yalnızca **Önceliği artır** seçeneği kullanılabilir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelik değerleri arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Kasa Ekler ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Ekler'e** gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında, ilkenin adına tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

4. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Exchange Online PowerShell veya tek başına EOP PowerShell kullanarak Kasa Ekler ilkelerini yapılandırma

Daha önce açıklandığı gibi, Kasa Ekler ilkesi güvenli bir ek ilkesinden ve güvenli bir ek kuralından oluşur.

PowerShell'de, güvenli ek ilkeleriyle güvenli ek kuralları arasındaki fark belirgindir. Güvenli ek ilkelerini **-SafeAttachmentPolicy cmdlet'lerini kullanarak\*** yönetirsiniz ve **-SafeAttachmentRule cmdlet'lerini kullanarak\*** güvenli ek kurallarını yönetirsiniz.

- PowerShell'de önce güvenli ek ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan güvenli ek kuralını oluşturursunuz.
- PowerShell'de, güvenli ek ilkesindeki ayarları ve güvenli ek kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den güvenli bir ek ilkesini kaldırdığınızda, buna karşılık gelen güvenli ek kuralı otomatik olarak kaldırılmaz ve tam tersi de geçerlidir.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Kasa Ek ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de Kasa Ekleri ilkesi oluşturmak iki adımlı bir işlemdir:

1. Güvenli ek ilkesini oluşturun.
2. Kuralın geçerli olduğu güvenli ek ilkesini belirten güvenli ek kuralını oluşturun.

 **Notlar**:

- Yeni bir güvenli ek kuralı oluşturabilir ve var olan ve ilişkilendirilmemiş bir güvenli ek ilkesi atayabilirsiniz. Güvenli bir ek kuralı birden fazla güvenli ek ilkesiyle ilişkilendirilebilir.

- İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni güvenli ek ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı olarak oluşturun (**New-SafeAttachmentRule** cmdlet'inde _etkin_`$false`).
  - **New-SafeAttachmentRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ ayarlayın (Öncelik _\<Number\>_).

- PowerShell'de oluşturduğunuz yeni bir güvenli ek ilkesi, ilkeyi güvenli bir ek kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>1. Adım: Güvenli bir ek ilkesi oluşturmak için PowerShell kullanma

Güvenli bir ek ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

Bu örnek, aşağıdaki değerlerle Contoso All adlı güvenli bir ek ilkesi oluşturur:

- Kasa Belgeler taramasıyla kötü amaçlı yazılım içerdiği belirlenen iletileri engelleyin (_Eylem_ parametresini kullanmıyoruz ve varsayılan değer ).`Block`
- _QuarantineTag_ parametresini kullanmadığımız için varsayılan [karantina ilkesi](quarantine-policies.md) kullanılır (AdminOnlyAccessPolicy).
- Yeniden yönlendirme etkinleştirilir ve kötü amaçlı yazılım içerdiği bulunan iletiler analiz ve araştırma için sec-ops@contoso.com gönderilir.
- Kasa Ekler taraması kullanılamıyorsa veya hatalarla karşılaşıyorsa, iletiyi teslim etmeyin (_ActionOnError_ parametresini kullanmıyoruz ve varsayılan değer olur`$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Güvenli bir ek [ilkesinde kullanılacak karantina ilkesini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. [Kasa Ekler ilkeleri'nde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>2. Adım: Güvenli bir ek kuralı oluşturmak için PowerShell kullanma

Güvenli bir ek kuralı oluşturmak için şu sözdizimini kullanın:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Bu örnek, aşağıdaki koşullara sahip Contoso All adlı güvenli bir ek kuralı oluşturur:

- Kural, Contoso All adlı güvenli ek ilkesiyle ilişkilendirilir.
- Kural, contoso.com etki alanındaki tüm alıcılar için geçerlidir.
- _Priority_ parametresini kullanmadığımız için varsayılan öncelik kullanılır.
- Kural etkindir ( _Enabled_ parametresini kullanmıyoruz ve varsayılan değerdir `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Güvenli ek ilkelerini görüntülemek için PowerShell kullanma

Mevcut güvenli ek ilkelerini görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli ek ilkelerinin özet listesini döndürür.

```PowerShell
Get-SafeAttachmentPolicy
```

Bu örnek, Contoso Executives adlı güvenli ek ilkesine ilişkin ayrıntılı bilgileri döndürür.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Güvenli ek kurallarını görüntülemek için PowerShell kullanma

Mevcut güvenli ek kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli ek kurallarının özet listesini döndürür.

```PowerShell
Get-SafeAttachmentRule
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

Bu örnek, Contoso Executives adlı güvenli ek kuralına ilişkin ayrıntılı bilgileri döndürür.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Güvenli ek ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de güvenli bir ek ilkesini yeniden adlandıramazsınız ( **Set-SafeAttachmentPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında Kasa Ekler ilkesini yeniden adlandırdığınızda, yalnızca güvenli ek _kuralını_ yeniden adlandırırsınız.

Aksi takdirde, bu makalenin önceki bölümlerinde yer alan [1. Adım: PowerShell kullanarak güvenli ek ilkesi oluşturma bölümünde açıklandığı gibi güvenli bir ek ilkesi](#step-1-use-powershell-to-create-a-safe-attachment-policy) oluşturduğunuzda da aynı ayarlar kullanılabilir.

Güvenli bir ek ilkesini değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Güvenli bir ek [ilkesinde kullanılacak karantina ilkesini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. [Kasa Ekler ilkeleri'nde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Güvenli ek kurallarını değiştirmek için PowerShell kullanma

PowerShell'de güvenli bir ek kuralını değiştirdiğinizde kullanılamayan tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Enabled_ parametresidir. Mevcut güvenli ek kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak güvenli ek kuralı oluşturma](#step-2-use-powershell-to-create-a-safe-attachment-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

Güvenli bir ek kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Güvenli ek kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de güvenli bir ek kuralının etkinleştirilmesi veya devre dışı bırakılması, Kasa Ekler ilkesinin tamamını (güvenli ek kuralı ve atanan güvenli ek ilkesi) etkinleştirir veya devre dışı bırakır.

PowerShell'de güvenli bir ek kuralını etkinleştirmek veya devre dışı bırakmak için şu sözdizimini kullanın:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli ek kuralını devre dışı bırakır.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) ve [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Güvenli ek kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de güvenli bir ek kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Not**: Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-SafeAttachmentRule** cmdlet'indeki _Priority_ parametresini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Güvenli ek ilkelerini kaldırmak için PowerShell kullanma

Güvenli bir ek ilkesini kaldırmak için PowerShell kullandığınızda, ilgili güvenli ek kuralı kaldırılmaz.

PowerShell'de güvenli bir ek ilkesini kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli ek ilkesini kaldırır.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Güvenli ek kurallarını kaldırmak için PowerShell kullanma

Güvenli bir ek kuralını kaldırmak için PowerShell kullandığınızda, ilgili güvenli ek ilkesi kaldırılmaz.

PowerShell'de güvenli bir ek kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli ek kuralını kaldırır.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Kasa Ekler ilkelerini başarıyla oluşturduğunuzu, değiştirdiğinizde veya kaldırdığınızdan emin olmak için aşağıdaki adımlardan herhangi birini yapın:

- konumundaki **Microsoft 365 Defender** portalının <https://security.microsoft.com/safeattachmentv2>Kasa Ekler sayfasında, ilkelerin listesini, **Durum** değerlerini ve **Öncelik** değerlerini doğrulayın. Daha fazla ayrıntı görüntülemek için, ada tıklayarak listeden ilkeyi seçin ve açılır listede ayrıntıları görüntüleyin.

- Exchange Online PowerShell'de veya PowerShell'Exchange Online Protection değerini ilkenin veya kuralın adıyla değiştirin\<Name\>, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Kasa Eklerinin iletileri taradığını doğrulamak için kullanılabilir Office 365 için Defender raporlarını denetleyin. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında Office 365 için Defender](threat-explorer.md) [için raporları görüntüleme](view-reports-for-mdo.md) ve Gezgini Kullanma.
