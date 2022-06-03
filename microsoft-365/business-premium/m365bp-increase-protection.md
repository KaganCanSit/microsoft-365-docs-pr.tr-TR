---
title: Microsoft 365 İş Ekstra için tehdit korumasını artırma
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
- admindeeplinkSPO
search.appverid:
- BCS160
- MET150
description: Microsoft 365 İş Ekstra'de koruma düzeyini artırma konusunda yardım alın
ms.openlocfilehash: a442dcd399a1886f5f63bd17dc897d1547a0f579
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863618"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra için tehdit korumasını artırma

Bu hedefte, Microsoft 365 İş Ekstra ile tehdit korumanızı artırırsınız. İşletmenizi kimlik avına, kötü amaçlı yazılımlara ve diğer tehditlere karşı korumak çok önemlidir. Bu amaç aşağıdakiler hakkında bilgi içerir:

- Kurulum ve yapılandırmada çok zaman kazandırabilen [önceden ayarlanmış güvenlik ilkeleri](#review-and-apply-preset-security-policies)
- İş gereksinimlerinize uygun olarak tanımlayabileceğiniz [özel güvenlik ilkeleri](#create-custom-security-policies)
- [SharePoint ve OneDrive dosya ve klasörler için paylaşım ayarlarınızı ayarlama](#set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders)
- Belirli dosyaları ve bunların nasıl kullanıldığını izleyen [uyarı ilkeleri](#review-your-alert-policies). 

## <a name="review-and-apply-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkelerini gözden geçirme ve uygulama

Aboneliğiniz istenmeyen posta önleme, kötü amaçlı yazılımdan koruma ve kimlik avı koruması için önerilen ayarları kullanan [önceden ayarlanmış güvenlik ilkeleri](../security/office-365-security/preset-security-policies.md) içerir. Varsayılan olarak yerleşik koruma etkindir; ancak, daha fazla güvenlik için standart veya katı koruma uygulamayı göz önünde bulundurun. 

:::image type="content" source="media/m365bp-presetsecuritypolicies.png" alt-text="Önceden ayarlanmış güvenlik ilkelerinin ekran görüntüsü.":::

> [!NOTE]
> Önceden ayarlanmış güvenlik ilkeleri, [güvenlik varsayılanlarıyla](m365bp-conditional-access.md#security-defaults) aynı şey değildir. Genellikle *önce güvenlik* varsayılanlarını *veya* [Koşullu Erişim'i](m365bp-conditional-access.md#conditional-access) kullanırsınız ve ardından güvenlik ilkelerinizi eklersiniz. [Önceden ayarlanmış güvenlik ilkeleri,](#what-are-preset-security-policies) güvenlik ilkelerinizi ekleme işlemini basitleştirir. Kendi [özel ilkelerinizi de ekleyebilirsiniz](#create-custom-security-policies). 

### <a name="what-are-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkeleri nelerdir?

Önceden ayarlanmış güvenlik ilkeleri, e-posta ve işbirliği içeriğiniz için koruma sağlar. Bu ilkeler şunlardan oluşur:

- Koruma düzeyini belirleyen *profiller*
- *İlkeler* (istenmeyen posta önleme, kötü amaçlı yazılımdan koruma, kimlik avı önleme, kimlik sahtekarlığı ayarları, kimliğe bürünme, Kasa Ekler ve Kasa Bağlantıları gibi)
- *İlke ayarları* (ilkeleri ve özel durumları alacak gruplar, kullanıcılar veya etki alanları gibi)

Aşağıdaki tabloda koruma düzeyleri ve önceden ayarlanmış ilke türleri özetlenmiştir.

| Koruma düzeyi | Açıklama |
|:---|:---|
| **Standart koruma** <br/>(*çoğu işletme için önerilir*) | Standart koruma, çoğu kullanıcı için uygun bir temel profil kullanır. Standart koruma, istenmeyen posta önleme, kötü amaçlı yazılımdan koruma, kimlik avı önleme, kimlik sahtekarlığı ayarları, kimliğe bürünme ayarları, Kasa Bağlantıları ve Kasa Ekler ilkelerini içerir.  |
| **Katı koruma**  | Katı koruma, standart koruma ile aynı türde ilkeler içerir, ancak daha sıkı ayarlar içerir. İşletmenizin ek güvenlik gereksinimlerini veya düzenlemelerini karşılaması gerekiyorsa, en azından öncelikli kullanıcılarınıza veya yüksek değerli hedeflerinize katı koruma uygulamayı göz önünde bulundurun. |
| **Yerleşik koruma** | E-postadaki kötü amaçlı bağlantılara ve eklere karşı koruma sağlar. Yerleşik koruma etkindir ve varsayılan olarak tüm kullanıcılara uygulanır.  |

> [!TIP]
> Önceden ayarlanmış ilkeleri alacak kullanıcıları, grupları ve etki alanlarını belirtebilir ve belirli özel durumları tanımlayabilirsiniz, ancak önceden belirlenmiş ilkeleri değiştiremezsiniz. Güvenlik ilkeleriniz için farklı ayarlar kullanmak istiyorsanız, şirketinizin gereksinimlerine uygun kendi özel ilkelerinizi oluşturabilirsiniz.

### <a name="policy-order-of-priority"></a>İlke önceliği sırası

Kullanıcılara birden çok ilke atanırsa, ilkeleri uygulamak için bir öncelik sırası kullanılır. Öncelik sırası aşağıdaki gibi çalışır:

1. **Katı koruma** en yüksek önceliği alır ve diğer tüm ilkeleri geçersiz kılar.

2. **Standart koruma** 

3. **Özel güvenlik ilkeleri**

4. **Yerleşik koruma** en düşük önceliği alır ve katı koruma, standart koruma ve özel ilkeler tarafından geçersiz kılınabilir.

Katı koruma diğer tüm ilkeleri geçersiz kılar ve yerleşik koruma diğer ilkeler tarafından geçersiz kılınabilir. 

Önceden ayarlanmış güvenlik ilkeleri hakkında daha fazla bilgi edinmek için bkz [. Önceden ayarlanmış güvenlik ilkeleri nelerden yapılır](../security/office-365-security/preset-security-policies.md#what-preset-security-policies-are-made-of)?

### <a name="how-do-i-assign-preset-security-policies-to-users"></a>Kullanıcılara önceden ayarlanmış güvenlik ilkeleri atamak Nasıl yaparım??

> [!IMPORTANT]
> Başlamadan önce, Exchange Online 'de (aboneliğinize dahil olan) aşağıdaki rollerden birine sahip olduğunuzdan emin olun:
> 
> - Genel Yönetici
> - Kuruluş Yönetimi
> - Güvenlik Yöneticisi
> 
> Daha fazla bilgi için bkz. [Exchange Online İzinler](/exchange/permissions-exo/permissions-exo) ve [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md).

Önceden ayarlanmış güvenlik ilkeleri atamak için şu adımları izleyin:

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **Şablonlu ilkeler** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Önceden Ayarlanmış Güvenlik İlkeleri'ne** gidin. ( **Doğrudan Önceden Ayarlanmış güvenlik ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/presetSecurityPolicies>.)

2. **Önceden ayarlanmış güvenlik ilkeleri** sayfasındaki **Standart koruma** veya **Katı koruma** bölümünde Devre **dışı** olan iki durumlu düğmeyi **Etkin** olarak değiştirin ve **yönet'i** seçin.

3. **Standart koruma uygulama** veya **Katı koruma uygulama** sihirbazı açılır öğede başlar. **EOP korumaları için geçerlidir** sayfasında, ilkelerin geçerli olduğu iç alıcıları tanımlayın (alıcı koşulları):
   - **Kullanıcılar**
   - **Gruplar**
   - **Etki alanları**

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için değerin yanındaki **Kaldır** simgesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) yazın.

   Dışlama belirtmek için **Bu kullanıcıları, grupları ve etki alanlarını dışla** onay kutusunu seçin ve ardından dışlanması gereken kullanıcıları, grupları veya etki alanlarını belirtin.

   İşiniz bittiğinde **İleri'yi** seçin.

4. **İlkelerin geçerli olduğu iç alıcıları** (alıcı koşulları) tanımlamak için Office 365 için Defender korumalar sayfaya uygulanır. Önceki adımda yaptığınız gibi kullanıcıları, grupları ve etki alanlarını belirtin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Değişikliklerinizi gözden geçirin ve onaylayın** sayfasında seçimlerinizi doğrulayın ve ardından **Onayla'yı** seçin.

> [!TIP]
> Önceden ayarlanmış güvenlik ilkeleri atama hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın:
> - [Kullanıcılara önceden ayarlanmış güvenlik ilkeleri atama](../security/office-365-security/preset-security-policies.md#assign-preset-security-policies-to-users)
> - [E-posta ve işbirliği içeriği için önerilen ayarlar](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (Microsoft 365 İş Ekstra Exchange Online Protection ve Office 365 için Microsoft Defender Plan 1'i içerir)

## <a name="create-custom-security-policies"></a>Özel güvenlik ilkeleri oluşturma

Bu makalenin önceki bölümlerinde açıklanan [önceden ayarlanmış güvenlik ilkeleri](#what-are-preset-security-policies) çoğu işletme için güçlü koruma sağlar. Ancak, yalnızca önceden ayarlanmış güvenlik ilkelerini kullanmakla sınırlı değilsiniz. Şirketinizin gereksinimlerine uygun olarak kendi özel güvenlik ilkelerinizi tanımlayabilirsiniz. 

Kendi özel ilkelerinizi oluşturmaya başlamak için [tehditlere karşı koruma](../security/office-365-security/protect-against-threats.md) hızlı başlangıç kılavuzumuzu kullanın. Kılavuz, yalnızca kendi güvenlik ilkelerinizi ayarlama konusunda size yol göstermesiyle kalmaz, aşağıdakiler için başlangıç noktası olarak kullanılması önerilen ayarları da sağlar:

- [Kötü amaçlı yazılımdan koruma](../security/office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Gelişmiş antiphishing koruması](../security/office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Antispam koruması](../security/office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Kasa Bağlantıları ve Kasa Ekleri](../security/office-365-security/protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

## <a name="set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>SharePoint ve OneDrive dosya ve klasörler için paylaşım ayarlarını belirleme

Varsayılan olarak, paylaşım düzeyleri hem SharePoint hem de OneDrive için en uygun düzeye ayarlanır. İşletmenizi daha iyi korumak için varsayılan ayarları değiştirmenizi öneririz.

1. <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">SharePoint yönetim merkezinde **Paylaşım'a**</a> gidin ve [kuruluşunuz için yönetici izinlerine](/sharepoint/sharepoint-admin-role) sahip bir hesapla oturum açın.
 
2. **Dış paylaşım'ın** altında paylaşım düzeyini belirtin. (Dış paylaşımı önlemek için **En az izin verme** seçeneğini kullanmanızı öneririz.)

3. **Dosya ve klasör bağlantıları'nın** altında bir seçenek belirleyin (**örneğin, Belirli kişiler**). Ardından, paylaşılan bağlantılar **(Görünüm gibi**) için varsayılan olarak Görünüm veya Düzenleme izinlerinin verilip verilmeyeceğini seçin.

4. **Diğer ayarlar'ın** altında, kullanmak istediğiniz seçenekleri belirleyin.

5. Ardından **Kaydet'i** seçin.

> [!TIP]
> Bu ayarlar hakkında daha fazla bilgi edinmek için bkz. [Paylaşım ayarlarını yönetme](/sharepoint/turn-external-sharing-on-or-off).

## <a name="review-your-alert-policies"></a>Uyarı ilkelerinizi gözden geçirme

Uyarı ilkeleri, işletmenizdeki kullanıcı ve yönetici etkinliklerini, olası kötü amaçlı yazılım tehditlerini ve veri kaybı olaylarını izlemek için kullanışlıdır. Aboneliğiniz bir dizi varsayılan ilke içerir, ancak özel ilkeler de oluşturabilirsiniz. Örneğin, kimsenin harici olarak paylaşmasını istemediğiniz önemli bir dosyayı SharePoint depolarsanız, birisi paylaşırsa sizi uyaran bir bildirim oluşturabilirsiniz.

Aşağıdaki görüntüde, Microsoft 365 İş Ekstra dahil edilen bazı varsayılan ilkeler gösterilmektedir.

![Microsoft 365 ile birlikte gelen varsayılan uyarı ilkeleri.](../media/alertpolicies.png)

### <a name="view-your-alert-policies"></a>Uyarı ilkelerinizi görüntüleme

1. konumundaki Microsoft Purview uyumluluk portalı [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **İlkeler'i** ve ardından **Uyarı ilkeleri'ni** seçin.

3. Daha fazla ayrıntı görüntülemek veya ilkeyi düzenlemek için tek bir ilke seçin. Aşağıdaki görüntüde, bir ilkenin seçili olduğu uyarı ilkelerinin listesi gösterilmektedir:

   :::image type="content" source="media/selected-alert-policy.png" lightbox="media/selected-alert-policy.png" alt-text="Seçili uyarı ilkesinin ekran görüntüsü.":::

> [!TIP]
> Daha fazla bilgi için bkz. [uyarı ilkeleri](../compliance/alert-policies.md).

### <a name="how-to-view-alerts"></a>Uyarıları görüntüleme

Belirli bir uyarıya bağlı olarak, uyarılarınızı Microsoft 365 Defender portalında veya Microsoft Purview uyumluluk portalı görüntüleyebilirsiniz.

| Uyarı türü  | Yapılması gerekenler  |
|---------|---------|
| Kullanıcı kötü amaçlı bir bağlantıya tıkladığında, bir e-postanın kötü amaçlı yazılım veya kimlik avı olarak bildirilmesi veya bir cihazın kötü amaçlı yazılım içerdiği algılanması gibi güvenlik uyarısı     | <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve **E-posta & işbirliği** bölümünde **İlkeler & kuralları** > **Uyarı ilkesi'ni** seçin. Alternatif olarak doğrudan adresine <https://security.microsoft.com/alertpolicies>gidebilirsiniz. |
| Kullanıcının hassas veya gizli bilgileri paylaşması (veri kaybı önleme uyarısı) veya olağan dışı bir dış dosya paylaşımı hacmi (bilgi idaresi uyarısı) olması gibi uyumluluk uyarısı    | <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> gidin ve **İlkeler** > **Uyarı Uyarı** > **ilkeleri'ni** seçin.  |

Daha fazla bilgi için bkz. [Uyarıları görüntüleme](../compliance/alert-policies.md#view-alerts).

## <a name="disable-or-manage-calendar-sharing"></a>Takvim paylaşımını devre dışı bırakma veya yönetme

Kuruluşunuzdaki kişilerin takvimlerini paylaşmasını engelleyebilirsiniz. Paylaşabilecekleri ayrıntı düzeyini de yönetebilirsiniz. Örneğin, paylaşımı yalnızca serbest/meşgul zamanları ile kısıtlayabilirsiniz.

1. [Microsoft 365 yönetim merkezi Kuruluş ayarları'na](https://go.microsoft.com/fwlink/p/?linkid=2053743) gidin ve oturum açın.

2. **Takvim'i** seçin ve kuruluşunuzdaki kişilerin takvimlerini Office 365 veya Exchange sahip kişiler dışındaki kişilerle mi yoksa herkesle mi paylaşabileceğini seçin.

   **Dış paylaşım** seçeneğini temizlemenizi öneririz.

   Herkesle paylaş seçeneğini belirlerseniz, yalnızca serbest/meşgul bilgilerini de paylaşmaya karar vekleyebilirsiniz.

3. Sayfanın alt kısmındaki **Değişiklikleri kaydet'i** seçin.

   Aşağıdaki görüntüde takvim paylaşımına izin verilmediği gösterilmektedir.

   ![Dış takvim paylaşımına izin verilmediğini gösteren ekran görüntüsü.](../media/nocalendarsharing.png)

   Aşağıdaki görüntüde, takvim paylaşımına yalnızca serbest/meşgul bilgileri içeren bir e-posta bağlantısıyla izin verildiğinde ayarlar gösterilir.

   ![Herkesle takvim serbest/meşgul paylaşımının ekran görüntüsü.](../media/sharefreebusy.png)

Kullanıcılarınızın takvimlerini paylaşmasına izin veriliyorsa, Web üzerinde Outlook'dan nasıl paylaşacaklarına [ilişkin bu yönergelere](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Şimdi [**KCG cihazlarını ayarlama görevine başlayalım**](m365bp-devices-overview.md).
