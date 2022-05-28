---
title: Office 365 için Microsoft Defender'da Kasa Bağlantıları ilkelerini ayarlama
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
description: Yöneticiler, Office 365 için Microsoft Defender Kasa Bağlantılar ilkelerini ve genel Kasa Bağlantıları ayarlarını görüntülemeyi, oluşturmayı, değiştirmeyi ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 969e3f3bb3b139a21cd2d84b4a0bd698a74b5107
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772456"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Kasa Bağlantıları ilkelerini ayarlama

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, [Office 365 için Microsoft Defender](defender-for-office-365.md) sahip iş müşterilerine yöneliktir. Outlook'da Safelink'ler hakkında bilgi arayan bir ev kullanıcısıysanız bkz. [Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Kasa [Office 365 için Microsoft Defender'deki](defender-for-office-365.md) bağlantılar, gelen e-posta iletilerinin posta akışında URL taramasına ve e-posta iletilerindeki ve diğer konumlardaki URL'lerin ve bağlantıların tıklama zamanının doğrulanmasını sağlar. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Kasa Bağlantılar](safe-links.md).

Varsayılan Kasa Bağlantıları ilkesi olmasa **da, yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tüm alıcılara Kasa Bağlantılar koruması sağlar (özel Kasa Bağlantıları ilkelerinde tanımlanmayan kullanıcılar). Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).

Bu makaledeki yordamları kullanarak belirli kullanıcılara, gruplara veya etki alanlarına uygulanan Kasa Bağlantıları ilkeleri de oluşturabilirsiniz.

> [!NOTE]
>
> Kasa Bağlantıları ilkelerinin **dışında** Kasa Bağlantıları koruması için genel ayarları yapılandırabilirsiniz. Yönergeler için bkz[. Office 365 için Microsoft Defender Kasa Bağlantıları için genel ayarları yapılandırma](configure-global-settings-for-safe-links.md).
>
> Yöneticiler, Kasa Bağlantıları için farklı yapılandırma ayarlarını dikkate almalıdır. Kullanılabilir seçeneklerden biri, Kasa Bağlantıları'na kullanıcı tarafından tanımlanabilir bilgiler eklemektir. Bu özellik, güvenlik operasyonları (SecOps) ekiplerinin olası kullanıcı güvenliğinin aşılmasını araştırmasına, düzeltici eylem gerçekleştirmesine ve yüksek maliyetli ihlalleri sınırlamasına olanak tanır.

Kasa Bağlantıları ilkelerini Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online PowerShell'de Exchange Online posta kutuları olan uygun Microsoft 365 kuruluşlar için PowerShell' de yapılandırabilirsiniz; tek başına EOP PowerShell posta kutularını Exchange Online, ancak Office 365 için Microsoft Defender eklenti abonelikleriyle).

Kasa Bağlantıları ilkesinin temel öğeleri şunlardır:

- **Güvenli bağlantılar ilkesi**: Kasa Bağlantılar korumasını açın, gerçek zamanlı URL taramasını açın, iletiyi teslim etmeden önce gerçek zamanlı taramanın tamamlanmasını bekleyip beklemeyeceğini belirtin, iç iletiler için taramayı açın, kullanıcının URL'lere tıklamalarını izlenip izlenmeyeceğini belirtin ve kullanıcıların özgün URL'ye oluk tıklamasına izin verilip verilmeyeceğini belirtin.
- **Güvenli bağlantılar kuralı**: Öncelik ve alıcı filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında Kasa Bağlantıları ilkelerini yönetirken bu iki öğe arasındaki fark belirgin değildir:

- bir Kasa Bağlantıları ilkesi oluşturduğunuzda, her ikisi için de aynı adı kullanarak aynı anda bir güvenli bağlantılar kuralı ve ilişkili güvenli bağlantılar ilkesi oluşturursunuz.
- Kasa Bağlantıları ilkesini değiştirdiğinizde ad, öncelik, etkin veya devre dışı ile ilgili ayarlar ve alıcı filtreleri güvenli bağlantılar kuralını değiştirir. Diğer tüm ayarlar ilişkili güvenli bağlantılar ilkesini değiştirir.
- Kasa Bağlantıları ilkesini kaldırdığınızda, güvenli bağlantılar kuralı ve ilişkili güvenli bağlantılar ilkesi kaldırılır.

Exchange Online PowerShell veya tek başına EOP PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin [devamında yer alan Kasa Bağlantıları ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell Exchange Online kullanma](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) bölümüne bakın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Kasa Bağlantıları** sayfasına gitmek için kullanın<https://security.microsoft.com/safelinksv2>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirmeden önce size izinler atanmalıdır:
  - Kasa Bağlantıları ilkelerini oluşturmak, değiştirmek ve silmek için, Microsoft 365 Defender portalında **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi **ve** Exchange Online **Kuruluş Yönetimi** rol grubunun üyesi olmanız gerekir.
  - Kasa Bağlantıları ilkelerine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalındaki İzinler](permissions-microsoft-365-security-center.md) ve [Exchange Online'deki İzinler](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365'deki diğer özellikler için izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  . - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Kasa Bağlantıları ilkeleri için önerilen ayarlarımız için bkz. [Bağlantılar ilke ayarları Kasa](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Yeni veya güncelleştirilmiş bir ilkenin uygulanması için 6 saate kadar izin verin.

- [Office 365 için Microsoft Defender sürekli olarak yeni özellikler ekleniyor](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Yeni özellikler eklendikçe, mevcut Kasa Bağlantıları ilkelerinizde ayarlamalar yapmanız gerekebilir.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Kasa Bağlantıları ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel bir Kasa Bağlantıları ilkesi oluşturmak, her ikisi için de aynı adı kullanarak güvenli bağlantılar kuralını ve ilişkili güvenli bağlantılar ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Bağlantılar'a** gidin. **Doğrudan Kasa Bağlantıları** sayfasına gitmek için kullanın<https://security.microsoft.com/safelinksv2>.

2. **Kasa Bağlantılar** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Oluştur'u seçin**.

3. **Yeni Kasa Bağlantıları ilke** sihirbazı açılır. **İlkenizi adlandırın** sayfasında aşağıdaki ayarları yapılandırın:

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

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Görüntülenen **Koruma ayarları** sayfasında aşağıdaki ayarları yapılandırın:
   - **İletilerdeki bilinmeyen kötü amaçlı URL'ler için eylemi seçin**: E-posta iletilerindeki bağlantılar için Kasa Bağlantılar korumasını etkinleştirmek için **Açık'ı** seçin. Bu ayarı açarsanız aşağıdaki ayarlar kullanılabilir:
     - **Şüpheli bağlantılar ve dosyalara işaret eden bağlantılar için gerçek zamanlı URL taraması uygulayın**: E-posta iletilerindeki bağlantıların gerçek zamanlı olarak taranmasını etkinleştirmek için bu seçeneği belirleyin. Bu ayarı açarsanız aşağıdaki ayar kullanılabilir:
       - **İletiyi teslim etmeden önce URL taramasının tamamlanmasını bekleyin: İletiyi teslim** etmeden önce gerçek zamanlı URL taramasının tamamlanmasını beklemek için bu seçeneği belirleyin.
     - **Kuruluş içinde gönderilen e-posta iletilerine Kasa Bağlantıları uygula**: İç gönderenler ve iç alıcılar arasındaki iletilere Kasa Bağlantıları ilkesini uygulamak için bu seçeneği belirleyin.
   - **Microsoft Teams içinde bilinmeyen veya kötü amaçlı olabilecek URL'ler için eylemi seçin: Teams** bağlantıları için Kasa Bağlantılar korumasını etkinleştirmek için **Açık'ı** seçin. Bu ayarın etkili olması 24 saat kadar sürebilir.

     > [!NOTE]
     > Şu anda Microsoft Teams için Kasa Bağlantıları koruması Microsoft 365 GCC High veya Microsoft 365 DoD'da kullanılamaz.

   - **Kullanıcı tıklamalarını izleme**: Kullanıcının e-posta iletilerindeki URL'leri izlemesini sağlamak için bu seçeneği seçili bırakın.
   - **Kullanıcıların özgün URL'ye tıklamasına izin ver**: Kullanıcıların [uyarı sayfalarında](safe-links.md#warning-pages-from-safe-links) özgün URL'ye tıklamasını engellemek için bu seçeneği temizleyin.
   - **Aşağıdaki URL'leri yeniden yazmayın**: aksi takdirde Kasa Bağlantıları tarafından engellenecek belirtilen URL'lere erişime izin verir.

     Kutuya, istediğiniz URL'yi veya değeri yazın ve **Ekle'ye** tıklayın. Bu adımı gerektiği kadar tekrarlayın.

     Var olan bir girdiyi kaldırmak için ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

     Giriş söz dizimi için bkz. ["Aşağıdaki URL'leri yeniden yazma" listesi için giriş söz dizimi](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Bu ayarlar hakkında ayrıntılı bilgi için bkz[. e-posta iletileri için bağlantılar ayarları Kasa](safe-links.md#safe-links-settings-for-email-messages) [ve Microsoft Teams için bağlantılar ayarları Kasa](safe-links.md#safe-links-settings-for-microsoft-teams).

   Standart ve Katı ilke ayarları için önerilen değerler hakkında daha fazla bilgi için bkz[. Bağlantılar ilke ayarları Kasa](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Bildirim** sayfasında **, kullanıcılarınıza nasıl bildirim göndermek istersiniz?** için aşağıdaki değerlerden birini seçin:
   - **Varsayılan bildirim metnini kullanma**
   - **Özel bildirim metni kullan**: Bu değeri seçerseniz (uzunluk 200 karakteri aşamaz), aşağıdaki ayarlar görüntülenir:
     - **Otomatik yerelleştirme için Microsoft Çeviri kullanma**
     - **Özel bildirim metni**: Bu kutuya özel bildirim metnini girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

8. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Kasa Bağlantıları ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Bağlantılar'a** gidin. **Doğrudan Kasa Bağlantıları** sayfasına gitmek için kullanın<https://security.microsoft.com/safelinksv2>.

2. **Kasa Bağlantılar** sayfasında, Kasa Bağlantıları ilkeleri listesinde aşağıdaki özellikler görüntülenir:
   - **Ad**
   - **Durum**
   - **Öncelik**

3. Ada tıklayarak bir ilke seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Kasa Bağlantıları ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. Microsoft 365 Defender portalında, **bağlantılar** **Kasa İlkeler & kuralları** \> **Tehdit İlkeleri** \> bölümüne  \> gidin.

2. **Kasa Bağlantılar** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için, bu [makaledeki Kasa Bağlantıları ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) bölümüne bakın.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırasını ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-safe-links-policies"></a>Kasa Bağlantıları ilkelerini etkinleştirme veya devre dışı bırakma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Bağlantılar'a** gidin. **Doğrudan Kasa Bağlantıları** sayfasına gitmek için kullanın<https://security.microsoft.com/safelinksv2>.

2. **Kasa Bağlantılar** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-safe-links-policies"></a>Kasa Bağlantıları ilkelerinin önceliğini ayarlama

Varsayılan olarak, Kasa Bağlantıları'na oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

**Not**:

- Microsoft 365 Defender portalında, Kasa Bağlantıları ilkesini oluşturduktan sonra önceliğini değiştirebilirsiniz. PowerShell'de, güvenli bağlantılar kuralı oluşturduğunuzda (mevcut kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- Kasa Bağlantılar ilkeleri, görüntülenme sırasına göre işlenir (ilk **ilkenin Öncelik** değeri 0'dır). Öncelik sırası ve birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Bağlantılar'a** gidin. **Doğrudan Kasa Bağlantıları** sayfasına gitmek için kullanın<https://security.microsoft.com/safelinksv2>.

2. **Kasa Bağlantılar** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve özel ilkelerin sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan ilkede yalnızca **Önceliği azalt** seçeneği kullanılabilir.
   - En düşük **Öncelik** değerine sahip ilke (örneğin, **3**) yalnızca **Önceliği artır** seçeneği kullanılabilir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelik değerleri arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Kasa Bağlantıları ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

1. Microsoft 365 Defender portalında, İlkeler **bölümündeki** **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kasa Bağlantılar** bölümüne gidin.

2. **Kasa Bağlantılar** sayfasında, ada tıklayarak listeden bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

3. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Kasa Bağlantıları ilkelerini yapılandırmak için Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Daha önce açıklandığı gibi, Kasa Bağlantılar ilkesi güvenli bağlantılar ilkesinden ve güvenli bağlantılar kuralından oluşur.

PowerShell'de, güvenli bağlantı ilkeleriyle güvenli bağlantı kuralları arasındaki fark belirgindir. Güvenli bağlantı ilkelerini **-SafeLinksPolicy cmdlet'lerini kullanarak\*** yönetirsiniz ve **-SafeLinksRule cmdlet'lerini kullanarak\*** güvenli bağlantı kurallarını yönetirsiniz.

- PowerShell'de önce güvenli bağlantılar ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan güvenli bağlantılar kuralını oluşturursunuz.
- PowerShell'de, güvenli bağlantılar ilkesindeki ayarları ve güvenli bağlantılar kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den güvenli bağlantılar ilkesini kaldırdığınızda, ilgili güvenli bağlantılar kuralı otomatik olarak kaldırılmaz ve bunun tersi de geçerlidir.

### <a name="use-powershell-to-create-safe-links-policies"></a>Kasa Bağlantıları ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de Kasa Bağlantıları ilkesi oluşturmak iki adımlı bir işlemdir:

1. Güvenli bağlantılar ilkesini oluşturun.
2. Kuralın geçerli olduğu güvenli bağlantılar ilkesini belirten güvenli bağlantılar kuralını oluşturun.

> [!NOTE]
>
> - Yeni bir güvenli bağlantılar kuralı oluşturabilir ve mevcut, ilişkilendirilmemiş güvenli bağlantılar ilkesini atayabilirsiniz. Güvenli bağlantılar kuralı birden fazla güvenli bağlantı ilkesiyle ilişkilendirilemiyor.
>
> - İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni güvenli bağlantılar ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:
>   - Yeni ilkeyi devre dışı olarak oluşturun (**New-SafeLinksRule** cmdlet'inde _etkin_`$false`).
>   - **New-SafeLinksRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ ayarlayın (Öncelik _\<Number\>_).
>
> - PowerShell'de oluşturduğunuz yeni bir güvenli bağlantılar ilkesi, ilkeyi güvenli bağlantılar kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>1. Adım: Güvenli bağlantılar ilkesi oluşturmak için PowerShell kullanma

Güvenli bağlantılar ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - _DoNotRewriteUrls_ parametresi için kullanılacak giriş söz dizimi hakkında ayrıntılı bilgi için, ["Aşağıdaki URL'leri yeniden yazmayın" listesi için giriş söz dizimine](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list) bakın.
>
> - **Set-SafeLinksPolicy** cmdlet'ini kullanarak mevcut güvenli bağlantı ilkelerini değiştirirken _DoNotRewriteUrls_ parametresi için kullanabileceğiniz ek söz dizimi için, bu makalenin devamında [yer alan Güvenli bağlantıları değiştirmek için PowerShell kullanma](#use-powershell-to-modify-safe-links-policies) bölümüne bakın.

Bu örnek, aşağıdaki değerlerle Contoso All adlı bir güvenli bağlantı ilkesi oluşturur:

- E-posta iletilerinde URL taramasını ve yeniden yazmayı açın.
- Teams'de URL taramayı açın.
- Dosyalara işaret eden tıklanan bağlantılar da dahil olmak üzere tıklanan URL'lerin gerçek zamanlı taramasını açın.
- İletiyi teslim etmeden önce URL taramasının tamamlanmasını bekleyin.
- İç iletiler için URL taramasını ve yeniden yazmayı açın.
- Kasa Bağlantıları korumasıyla ilgili kullanıcı tıklamalarını izleyin (_TrackUserClicks_ parametresini kullanmıyoruz ve varsayılan değer $true).
- Kullanıcıların özgün URL'ye tıklamasına izin verme.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>2. Adım: Güvenli bağlantılar kuralı oluşturmak için PowerShell kullanma

Güvenli bağlantılar kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Bu örnek, aşağıdaki koşullara sahip Contoso All adlı güvenli bağlantılar kuralı oluşturur:

- Kural, Contoso All adlı güvenli bağlantılar ilkesiyle ilişkilendirilir.
- Kural, contoso.com etki alanındaki tüm alıcılar için geçerlidir.
- _Priority_ parametresini kullanmadığımız için varsayılan öncelik kullanılır.
- Kural etkindir ( _Enabled_ parametresini kullanmıyoruz ve varsayılan değerdir `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Bu örnek, önceki örneğe benzer bir güvenli bağlantılar kuralı oluşturur, ancak bu örnekte kural kuruluştaki tüm kabul edilen etki alanlarındaki alıcılar için geçerlidir.

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

Bu örnek, önceki örneklere benzer bir güvenli bağlantılar kuralı oluşturur, ancak bu örnekte kural, .csv dosyasında belirtilen etki alanlarındaki alıcılar için geçerlidir.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs $SLDomains
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Güvenli bağlantı ilkelerini görüntülemek için PowerShell kullanma

Mevcut güvenli bağlantı ilkelerini görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli bağlantı ilkelerinin özet listesini döndürür.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

Bu örnek, Contoso Executives adlı güvenli bağlantılar ilkesine ilişkin ayrıntılı bilgileri döndürür.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Güvenli bağlantı kurallarını görüntülemek için PowerShell kullanma

Mevcut güvenli bağlantı kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, tüm güvenli bağlantı kurallarının özet listesini döndürür.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

Bu örnek, Contoso Yöneticileri adlı güvenli bağlantılar kuralına ilişkin ayrıntılı bilgileri döndürür.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Güvenli bağlantı ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de güvenli bağlantılar ilkesini yeniden adlandıramazsınız ( **Set-SafeLinksPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında bir Kasa Bağlantıları ilkesini yeniden adlandırdığınızda, yalnızca güvenli bağlantılar _kuralını_ yeniden adlandırırsınız.

PowerShell'de güvenli bağlantı ilkelerini değiştirmek için dikkat edilmesi gereken tek ek nokta _, DoNotRewriteUrls_ parametresinin kullanılabilir söz dizimidir ( ["Aşağıdaki URL'leri yeniden yazmayın" listesi](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)):

- Varolan girişlerin yerini alacak değerler eklemek için aşağıdaki söz dizimini kullanın: `"Entry1","Entry2,..."EntryN"`.
- Diğer mevcut girişleri etkilemeden değer eklemek veya kaldırmak için aşağıdaki söz dizimini kullanın: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Aksi takdirde, bu makalenin önceki bölümlerinde yer alan [1. Adım: PowerShell kullanarak güvenli bağlantılar ilkesi oluşturma](#step-1-use-powershell-to-create-a-safe-links-policy) bölümünde açıklandığı gibi güvenli bağlantılar ilkesi oluşturduğunuzda da aynı ayarlar kullanılabilir.

Güvenli bağlantılar ilkesini değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Güvenli bağlantı kurallarını değiştirmek için PowerShell kullanma

PowerShell'de güvenli bağlantılar kuralını değiştirdiğinizde kullanılamayan tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Enabled_ parametresidir. Mevcut güvenli bağlantılar kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak güvenli bağlantılar kuralı oluşturma](#step-2-use-powershell-to-create-a-safe-links-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

Güvenli bağlantılar kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Bu örnek, kuruluştaki kabul edilen tüm etki alanlarını Contoso All adlı güvenli bağlantılar kuralına koşul olarak ekler.

```powershell
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

Bu örnek, belirtilen .csv etki alanlarını Contoso All adlı güvenli bağlantılar kuralına koşul olarak ekler.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs $SLDomains
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Güvenli bağlantı kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de güvenli bağlantılar kuralının etkinleştirilmesi veya devre dışı bırakılması, Kasa Bağlantıları ilkesinin tamamını (güvenli bağlantılar kuralı ve atanan güvenli bağlantılar ilkesi) etkinleştirir veya devre dışı bırakır.

PowerShell'de güvenli bağlantılar kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimlerini kullanın:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli bağlantılar kuralını devre dışı bırakır.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) ve [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Güvenli bağlantı kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de güvenli bağlantılar kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-SafeLinksRule** cmdlet'indeki _Priority_ parametresini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Güvenli bağlantı ilkelerini kaldırmak için PowerShell kullanma

Güvenli bağlantılar ilkesini kaldırmak için PowerShell kullandığınızda, ilgili güvenli bağlantılar kuralı kaldırılmaz.

PowerShell'de güvenli bağlantılar ilkesini kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli bağlantılar ilkesini kaldırır.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Güvenli bağlantı kurallarını kaldırmak için PowerShell kullanma

Güvenli bağlantılar kuralını kaldırmak için PowerShell kullandığınızda, ilgili güvenli bağlantılar ilkesi kaldırılmaz.

PowerShell'de güvenli bağlantılar kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı güvenli bağlantılar kuralını kaldırır.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Kasa Bağlantıların iletileri taradığını doğrulamak için, kullanılabilir Office 365 için Microsoft Defender raporlarına bakın. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında Office 365 için Defender](threat-explorer.md) [için raporları görüntüleme](view-reports-for-mdo.md) ve Gezgini Kullanma.

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Bağlantılar ilkeleri Kasa başarıyla oluşturduğunuzu, değiştirdiğinizde veya kaldırdığınızdan emin olmak için aşağıdaki adımlardan herhangi birini yapın:

- konumundaki **Microsoft 365 Defender** portalının <https://security.microsoft.com/safelinksv2>Kasa Bağlantılar sayfasında, ilkelerin listesini, **Durum** değerlerini ve **Öncelik** değerlerini doğrulayın. Daha fazla ayrıntı görüntülemek için listeden ilkeyi seçin ve açılır menüde ayrıntıları görüntüleyin.

- Exchange Online PowerShell'de veya PowerShell'Exchange Online Protection değerini ilkenin veya kuralın adıyla değiştirin\<Name\>, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
