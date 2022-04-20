---
title: Office 365 için Microsoft Defender, Kötü Amaçlı Yazılımdan Koruma, Kimlik Avı önleme, İstenmeyen posta önleme, Kasa bağlantıları, Kasa ekleri, Sıfır saat otomatik temizleme (ZAP), MDO güvenlik yapılandırmasındaki tehditlere karşı koruma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
ms.date: 06/22/2021
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler Microsoft 365'de tehdit koruması hakkında bilgi edinebilir ve bunu kuruluşunuz için nasıl kullanacağınızı yapılandırabilir.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d067035d5eaf3c7a4febac6feeab0c56cd707728
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941445"
---
# <a name="protect-against-threats"></a>Tehditlere karşı korunun

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

aşağıda, Office 365 için Defender yapılandırmasını öbeklere bölen bir hızlı başlangıç kılavuzu verilmiştir. Office 365 tehdit koruması özelliklerini kullanmaya yeni başladıysanız, nereden başlayacağınızı bilmiyorum veya *bunu yaparak* en iyi şekilde öğreniyorsanız, bu kılavuzu bir denetim listesi ve başlangıç noktası olarak kullanın.

> [!IMPORTANT]
> **İlk önerilen ayarlar her ilke türü için dahil edilir; ancak birçok seçenek mevcuttur ve ayarlarınızı kuruluşunuzun gereksinimlerini karşılayacak şekilde ayarlayabilirsiniz**. İlkelerinizin veya değişikliklerinizin veri merkezinizde çalışmasını sağlamak için yaklaşık 30 dakika bekleyin.
>
> Office 365 için Defender'da çoğu ilkenin el ile yapılandırmasını atlamak için, Standart veya Katı düzeyde önceden ayarlanmış güvenlik ilkelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).

## <a name="requirements"></a>Gereksinimler

### <a name="subscriptions"></a>Abonelik

Tehdit koruması özellikleri *tüm* Microsoft veya Office 365 aboneliklerine dahildir; ancak bazı abonelikler gelişmiş özelliklere sahiptir. Aşağıdaki tabloda, en düşük abonelik gereksinimleriyle birlikte bu makalede yer alan koruma özellikleri listelenmiştir.

> [!TIP]
> Denetimi açma yönergelerinin ötesinde, *adımların* kötü amaçlı yazılımdan koruma, kimlik avı önleme ve Office 365 Exchange Online Protection (**EOP**) kapsamında işaretlenmiş istenmeyen posta önlemeyi başlattığına dikkat edin. EOP'nin (Office 365 için Defender) EOP içerdiğini ve derlediğinize kadar **bu, Office 365 için Defender** bir makalede garip görünebilir.

|Koruma türü|Abonelik gereksinimi|
|---|---|
|Denetim günlüğü (raporlama amacıyla)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Kötü amaçlı yazılımdan koruma|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Kimlik avından koruma|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|İstenmeyen posta önleme koruma|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|E-posta ve Office belgelerindeki kötü amaçlı URL'lere ve dosyalara karşı koruma (bağlantılar ve Kasa Ekleri Kasa)|[Office 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Roller ve izinler

Office 365 için Defender ilkelerini yapılandırmak için size uygun bir rol atanmalıdır. Bu eylemleri gerçekleştirebilecek roller için aşağıdaki tabloya göz atın.

|Rol veya rol grubu|Daha fazla bilgi nereden edinilir?|
|---|---|
|genel yönetici|[Microsoft 365 yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md)|
|Güvenlik Yöneticisi|[Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference#security-administrator)
|Exchange Online Kuruluş Yönetimi|[Exchange Online'de izinler](/exchange/permissions-exo/permissions-exo)|

Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Raporlama ve araştırma için denetim günlüğünü açma

- Denetim günlüğünüzü erken başlatın. Aşağıdaki adımlardan bazıları için denetimin **ON** olması gerekir. Denetim günlüğü[, Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) içeren aboneliklerde kullanılabilir. Tehdit koruma raporlarında, [e-posta güvenlik raporlarında](view-email-security-reports.md) ve [Gezgin'de](threat-explorer.md) verileri görüntülemek için denetim günlüğü *Açık* olmalıdır. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Bölüm 1 - EOP'de kötü amaçlı yazılımdan koruma

Kötü amaçlı yazılımdan koruma için önerilen ayarlar hakkında daha fazla bilgi için bkz. [EOP kötü amaçlı yazılımdan koruma ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Microsoft 365 Defender portalında <https://security.microsoft.com/antimalwarev2>**kötü amaçlı yazılımdan koruma** sayfasını açın.

2. **Kötü amaçlı yazılımdan koruma** sayfasında, ada tıklayarak **Varsayılan (Varsayılan)** adlı ilkeyi seçin.

3. Açılan ilke ayrıntıları açılır öğesinde **Koruma ayarlarını düzenle'ye** tıklayın ve aşağıdaki ayarları yapılandırın:
   - **Koruma ayarları** bölümü:
     - **Ortak ekler filtresini etkinleştirin**: Seçin (açın). **Daha fazla dosya türü eklemek için Dosya türlerini özelleştir'e** tıklayın.
     - **Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştir**: Bu ayarın seçili olduğunu doğrulayın. Kötü amaçlı yazılımlar için ZAP hakkında daha fazla bilgi için bkz. Kötü [amaçlı yazılım için sıfır saatlik otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware)
   - **Karantina ilkesi**: AdminOnlyAccessPolicy varsayılan değerini seçili bırakın. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).
   - **Bildirim** bölümü: Bildirim ayarlarından hiçbirinin seçilmediğini doğrulayın.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İlke ayrıntıları açılır menüsüne geri dönüp **Kapat'a** tıklayın.

Kötü amaçlı yazılımdan koruma ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Bölüm 2 - EOP ve Office 365 için Defender kimlik avı koruması

[Kimlik avı koruması](anti-phishing-protection.md)[, EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) içeren aboneliklerde kullanılabilir. Gelişmiş kimlik avı koruması[, Office 365 için Defender'de](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) kullanılabilir.

Kimlik avı önleme ilkeleri için önerilen ayarlar hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'da EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) ve [Kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

Aşağıdaki yordamda varsayılan kimlik avı önleme ilkesinin nasıl yapılandırıldığı açıklanmaktadır. Yalnızca Office 365 için Defender'de kullanılabilen Ayarlar açıkça işaretlenir.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com/antiphishing>**Kimlik avı önleme** sayfasını açın.

2. **Kimlik avına karşı koruma** sayfasında, ada tıklayarak **Office365 AntiPhish Default (Varsayılan)** adlı ilkeyi seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde aşağıdaki ayarları yapılandırın:
   - **Kimlik avı eşiği & koruma** bölümü: **Koruma ayarlarını düzenle'ye** tıklayın ve açılan açılır öğede aşağıdaki ayarları yapılandırın:
     - **Kimlik avı e-posta eşiği**<sup>\*</sup>: **2 - Agresif** (Standart) veya **3 - Daha Agresif** (Katı) seçeneğini belirleyin.
     - **Kimliğe Bürünme** bölümü <sup>\*</sup>: Aşağıdaki değerleri yapılandırın:
       - **Kullanıcıların korumasını etkinleştir'i** seçin, görüntülenen **Yönet (nn) gönderenler** bağlantısına tıklayın ve ardından kuruluşunuzun yönetim kurulu üyeleri, CEO'nuz, CFO'nuz ve diğer üst düzey liderler gibi kimliğe bürünmelere karşı korumak için iç ve dış gönderenler ekleyin.
       - **Etki alanlarını korumak için etkinleştir'i** seçin ve ardından görüntülenen aşağıdaki ayarları yapılandırın:
         - Kabul edilen **etki alanlarınızdaki** iç gönderenleri ( **Etki alanlarımı görüntüle'ye** tıklayarak görünür) kimliğe bürünmeye karşı korumak için Sahip olduğum etki alanlarını ekle'yi seçin.
         - Diğer etki alanlarındaki gönderenleri korumak için **Özel etki alanları ekle'yi** seçin, görüntülenen **Özel etki alanlarını yönet (nn)** bağlantısına tıklayın ve ardından kimliğe bürünmeye karşı korumak için başka etki alanları ekleyin.
     - **Güvenilen gönderenler ve etki alanları** bölümü <sup>\*</sup> ekleme: Gerekirse, gönderen ve gönderen etki alanı özel durumlarını kimliğe bürünme koruması için yapılandırmak için **Yönet (nn) güvenilen** gönderenleri ve etki alanlarını yönet'e tıklayın.
     - Posta kutusu yönetim bilgileri ayarları <sup>\*</sup>: **Kimliğe bürünme koruması için posta kutusu zekasını etkinleştir ve Zekayı etkinleştir'in** seçili olduğunu doğrulayın.
     - **Kimlik sahtekarı** bölümü: Kimlik **sahtekarlık zekasını etkinleştir'in** seçili olduğunu doğrulayın.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Eylemler** bölümü: **Eylemleri düzenle'ye** tıklayın ve açılan açılır öğede aşağıdaki ayarları yapılandırın:
     - **İleti eylemleri** bölümü: Aşağıdaki ayarları yapılandırın:
       - **İleti kimliğine bürünülen bir kullanıcı**<sup>\*</sup> olarak algılanırsa: **İletiyi karantinaya al'ı** seçin. Kullanıcı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan [karantina ilkesini](quarantine-policies.md) seçtiğiniz bir Karantina **ilkesi uygula** kutusu görüntülenir.
       - **İleti kimliğine bürünülen bir etki alanı**<sup>\*</sup> olarak algılanırsa: **İletiyi karantinaya al'ı** seçin. Etki alanı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan [karantina ilkesini](quarantine-policies.md) seçtiğiniz karantina **ilkesini uygula** kutusu görüntülenir.
       - **Posta kutusu zekası kimliğine bürünülen bir kullanıcı**<sup>\*</sup> algılarsa: **İletiyi alıcıların Gereksiz E-posta klasörlerine taşı** (Standart) veya **İletiyi karantinaya al** (Katı) seçeneğini belirleyin. **İletiyi karantinaya al'ı** seçerseniz, posta kutusu yönetim bilgileri koruması tarafından **karantinaya** alınan iletilere uygulanan [karantina ilkesini](quarantine-policies.md) seçtiğiniz bir Karantina ilkesi uygula kutusu görüntülenir.
       - **İleti sahte olarak algılanırsa**: **İletiyi alıcıların Gereksiz E-posta klasörlerine taşı** (Standart) veya **İletiyi karantinaya** al (Katı) seçeneğini belirleyin.  **İletiyi karantinaya al'ı** seçerseniz, **kimlik sahtekarlığına karşı koruma ile karantinaya** alınan iletilere uygulanan [karantina ilkesini](quarantine-policies.md) seçtiğiniz bir Karantina ilkesi uygula kutusu görüntülenir.
     - **Güvenlik ipuçları & göstergeler** bölümü: Aşağıdaki ayarları yapılandırın:
       - **İlk kişiyi göster güvenlik ipucu**: Seç (aç).
       - **Kullanıcı kimliğe bürünme güvenlik ipucu**<sup>\*</sup> göster: Seç (aç).
       - **Etki alanı kimliğe bürünme güvenlik ipucu**<sup>\*</sup> göster: Seç (aç).
       - **Kullanıcı kimliğine bürünme olağan dışı karakterleri güvenlik ipucu**<sup>\*</sup> göster: Seç (aç).
       - Kimlik **sahtekarlığına yönelik kimliği doğrulanmamış gönderenler için göster (?)** : Seç (aç).
       - **"via" etiketini göster**: Seçin (açın).

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   <sup>\*</sup>Bu ayar yalnızca Office 365 için Defender kullanılabilir.

4. **Kaydet'e** ve ardından **Kapat'a** tıklayın

Kimlik avı önleme ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md) ve [Office 365 için Microsoft Defender kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Bölüm 3 - EOP'de istenmeyen posta önleme koruması

İstenmeyen posta önleme için önerilen ayarlar hakkında daha fazla bilgi için bkz. [EOP istenmeyen posta önleme ilke ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Microsoft 365 Defender portalında <https://security.microsoft.com/antispam>**İstenmeyen posta önleme ilkeleri** sayfasını açın.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, adına tıklayarak listeden **İstenmeyen posta önleme gelen ilkesi (Varsayılan) adlı ilkeyi** seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde aşağıdaki ayarları yapılandırın:
   - **toplu e-posta eşiği & istenmeyen posta özellikleri** bölümü: **İstenmeyen posta eşiğini ve özelliklerini düzenle'ye** tıklayın. Görüntülenen açılır öğede aşağıdaki ayarları yapılandırın:
     - **Toplu e-posta eşiği**: Bu değeri 5 (Katı) veya 6 (Standart) olarak ayarlayın.
     - Diğer ayarları varsayılan değerlerinde bırakın (**Kapalı** veya **Yok**).

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Eylemler** bölümü: **Eylemleri düzenle'ye** tıklayın. Görüntülenen açılır öğede aşağıdaki ayarları yapılandırın:
     - **İleti eylemleri** bölümü:
       - **İstenmeyen posta**: **İletiyi Gereksiz E-posta klasörüne taşı'nın** seçili olduğunu doğrulayın (Standart) veya **İletiyi karantinaya al** (Katı) seçeneğini belirleyin.
       - **Yüksek güvenilirlikli istenmeyen posta**: **İletiyi karantinaya al'ı** seçin.
       - **Kimlik avı**: **İletiyi karantinaya al'ı** seçin.
       - **Yüksek güvenilirlikli kimlik avı**: **Karantina iletilerinin** seçili olduğunu doğrulayın.
       - **Toplu**: **İletiyi Gereksiz E-posta klasörüne taşı'nın** seçili olduğunu doğrulayın (Standart) veya **Karantina iletisi** (Katı) seçeneğini belirleyin.

       **İletiyi karantinaya al'ı** seçtiğiniz her eylem için, istenmeyen posta önleme koruması tarafından **karantinaya** alınan iletilere uygulanan [karantina ilkesini](quarantine-policies.md) seçtiğiniz karantina ilkesi seçin kutusu görüntülenir.

     - **İstenmeyen postaları şu kadar gün boyunca karantinada tutun**: **30** gün değerini doğrulayın.
     - **İstenmeyen posta güvenlik ipuçlarını etkinleştirme**: Bu ayarın seçili (açık) olduğunu doğrulayın.
     - **Sıfır saatlik otomatik temizlemeyi (ZAP) etkinleştir**: Bu ayarın seçili olduğunu (açık) doğrulayın.
       - **Kimlik avı iletileri için etkinleştir**: Bu ayarın seçili (açık) olduğunu doğrulayın. Daha fazla bilgi için bkz. [Kimlik avı için sıfır saat otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing)
       - **İstenmeyen posta iletileri için etkinleştir**: Bu ayarın seçili (açık) olduğunu doğrulayın. Daha fazla bilgi için bkz. [İstenmeyen postalar için sıfır saatlik otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam)

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **İzin verilen ve engellenen gönderenler ve etki alanları** bölümü: İzin verilen gönderenlerinizi ve izin verilen etki alanlarınızı [EOP'de engellenen gönderen listeleri oluşturma veya EOP'de](create-block-sender-lists-in-office-365.md) [güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md) başlığı altında açıklandığı gibi gözden geçirin veya düzenleyin.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İşlemi tamamladığınızda, **Kapat**'a tıklayın.

İstenmeyen posta önleme ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Bölüm 4 - Kötü amaçlı URL'lere ve dosyalara karşı koruma (Kasa Bağlantılar ve Kasa ekleri Office 365 için Defender)

Office 365 için Microsoft Defender [içeren](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) aboneliklerde kötü amaçlı URL'lerden ve dosyalardan tıklama zamanı koruması sağlanır. [Kasa Ekler](safe-attachments.md) ve [Kasa Bağlantıları](safe-links.md) ilkeleri aracılığıyla ayarlanır.

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da ek ilkelerini Kasa

Kasa Ekleri için önerilen ayarlar hakkında daha fazla bilgi için bkz. .[ Ekler ayarlarını Kasa](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. **Microsoft 365 Defender** portalında <https://security.microsoft.com/safeattachmentv2>Kasa Ekler sayfasını açın.

2. **Kasa Ekler** sayfasında **Genel ayarlar'a** tıklayın ve görüntülenen açılır listede aşağıdaki ayarları yapılandırın:
   - **SharePoint, OneDrive ve Microsoft Teams için Office 365 için Defender açın**: Bu ayarı açın (![Aç.](../../media/scc-toggle-on.png))

     > [!IMPORTANT]
     > **SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmadan önce, kuruluşunuzda denetim günlüğünün açık olduğunu doğrulayın**. Bu eylem genellikle Exchange Online'de Denetim Günlükleri rolü atanmış biri tarafından gerçekleştirilir. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md)!

   - **Office istemcileri için Kasa Belgeleri açın**: Bu ayarı açın (![Aç/kapat).](../../media/scc-toggle-on.png)). Bu özelliğin yalnızca gerekli lisans türleriyle kullanılabilir ve anlamlı olduğunu unutmayın. Daha fazla bilgi için bkz. [Microsoft 365 E5 belgeleri Kasa](safe-docs.md).
   - **Kasa Belgeler dosyayı kötü amaçlı olarak tanımlasa bile, kişilerin Korumalı Görünüm'e tıklamasına izin verin: Bu ayarın** kapalı olduğunu doğrulayın (![Kapat.](../../media/scc-toggle-off.png))

   İşiniz bittiğinde **Kaydet'e** tıklayın

3. **Kasa Ekler** sayfasına dönün, Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png).

4. Açılan **Kasa Ekleri Oluşturma ilkesi** sihirbazında aşağıdaki ayarları yapılandırın:
   - **İlke sayfanızı adlandır** :
     - **Ad**: Benzersiz ve açıklayıcı bir şey girin.
     - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Kullanıcılar ve etki alanları** sayfası: Bu ilk ilkeniz olduğundan ve kapsamı en üst düzeye çıkarmak istediğinizden, [Kabul edilen etki alanlarınızı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) **Etki Alanları** kutusuna girmeyi göz önünde bulundurun. Aksi takdirde, daha ayrıntılı denetim için **Kullanıcılar** ve **Gruplar** kutularını kullanabilirsiniz. **Bu kullanıcıları, grupları ve etki alanlarını dışla'yı** seçip değerler girerek özel durumlar belirtebilirsiniz.
   - **Ayarlar** sayfası:
     - **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı**: **Engelle'yi** seçin.
     - **Karantina ilkesi**: Varsayılan değer boş olduğundan AdminOnlyAccessPolicy ilkesi kullanılır. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).
     - **Algılanan eklerle eki yeniden yönlendirme** : **Yeniden yönlendirmeyi etkinleştir**: Bu ayarı açın (seçin) ve algılanan iletileri almak için bir e-posta adresi girin.
     - **Tarama tamamlanamadıysa Kasa Ekler algılama yanıtını uygulayın (zaman aşımı veya hatalar)**: Bu ayarın seçili olduğunu doğrulayın.

5. İşiniz bittiğinde **Gönder'e** ve ardından **Bitti'ye** tıklayın.

6. (Önerilen) Genel yönetici veya SharePoint Online yöneticisi olarak, SharePoint Online PowerShell'de _DisallowInfectedFileDownload_ parametresi olarak `$true` ayarlanmış **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** cmdlet'ini çalıştırın.
   - `$true` algılanan dosyalar için tüm eylemleri (Sil hariç) engeller. Kişiler algılanan dosyaları açamaz, taşıyamaz, kopyalayamaz veya paylaşamaz.
   - `$false` Sil ve İndir dışındaki tüm eylemleri engeller. Kişiler riski kabul etmeyi ve algılanan bir dosyayı indirmeyi seçebilir.

7. Değişikliklerinizin tüm Microsoft 365 veri merkezlerine yayılması için 30 dakikaya kadar bekleyin.

Kasa Ekleri için Kasa Ekler ilkelerini ve genel ayarları yapılandırmaya yönelik ayrıntılı yönergeler için aşağıdaki konulara bakın:

- [Office 365 için Microsoft Defender Kasa Ekler ilkelerini ayarlama](set-up-safe-attachments-policies.md)
- [SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekleri açma](turn-on-mdo-for-spo-odb-and-teams.md)
- [Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Kasa Bağlantıları ilkeleri

Kasa Bağlantıları için önerilen ayarlar hakkında daha fazla bilgi için bkz. [Kasa Bağlantılar ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. **Microsoft 365 Defender** portalında <https://security.microsoft.com/safelinksv2>Kasa Bağlantılar sayfasını açın.

2. **Kasa Bağlantılar** sayfasında **Genel ayarlar'a** tıklayın ve görüntülenen açılır listede aşağıdaki ayarları yapılandırın:
   - **Desteklenen Office 365 uygulamaları bölümündeki içeriğe uygulanan Ayarlar**:
     - **Office 365 uygulamalarında Kasa Bağlantıları kullan**: Bu ayarın açık olduğunu doğrulayın (![Açık.](../../media/scc-toggle-on.png))
     - **Kullanıcıların Office 365 uygulamalarda korumalı bağlantılara ne zaman tıkladığını izlemeyin**: Bu ayarı kapatın (![Kapat.](../../media/scc-toggle-off.png))
     - **Kullanıcıların Office 365 uygulamalarda özgün URL'ye tıklamasına izin vermeyin**: Bu ayarın açık olduğunu doğrulayın (![Açık.](../../media/scc-toggle-on.png)).

   İşiniz bittiğinde **Kaydet'e** tıklayın

3. **Kasa Bağlantılar** sayfasına dönün, Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png).

4. Açılan **Kasa Bağlantıları oluştur ilke** sihirbazında aşağıdaki ayarları yapılandırın:
   - **İlke sayfanızı adlandır** :
     - **Ad**: Benzersiz ve açıklayıcı bir şey girin.
     - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Kullanıcılar ve etki alanları** sayfası: Bu ilk ilkeniz olduğundan ve kapsamı en üst düzeye çıkarmak istediğinizden, [Kabul edilen etki alanlarınızı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) **Etki Alanları** kutusuna girmeyi göz önünde bulundurun. Aksi takdirde, daha ayrıntılı denetim için **Kullanıcılar** ve **Gruplar** kutularını kullanabilirsiniz. **Bu kullanıcıları, grupları ve etki alanlarını dışla'yı** seçip değerler girerek özel durumlar belirtebilirsiniz.
   - **Url & koruma ayarları sayfasına tıklayın** :
     - **E-postalar bölümündeki kötü amaçlı olabilecek URL'ler üzerinde eylem** :
       - **Açık: Kasa Bağlantılar, kullanıcılar e-postadaki bağlantılara tıkladığında bilinen, kötü amaçlı bağlantıların listesini denetler**: Ayarını seçin (açın).
       - **Kuruluş içinde gönderilen e-posta iletilerine Kasa Bağlantıları uygula**: Bu ayarı seçin (açın).
       - **Şüpheli bağlantılar ve dosyalara işaret eden bağlantılar için gerçek zamanlı URL taraması uygulayın**: Bu ayarı seçin (açın).
       - **İletiyi göndermeden önce URL taramasının tamamlanmasını bekleyin**: Bu ayarı seçin (açın).
       - **URL'leri yeniden yazmayın, yalnızca Kasa Bağlantılar API'si aracılığıyla denetimler yapın**: Bu ayarın seçili olmadığını doğrulayın (kapatın).
     - **E-postada aşağıdaki URL'leri yeniden yazmayın**: Bu ayar için belirli bir önerimiz yok. Daha fazla bilgi için Kasa [Bağlantıları ilkelerindeki "Aşağıdaki URL'leri yeniden yazmayın" listelerine](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) bakın.
     - **Microsoft Teams bölümde kötü amaçlı olabilecek URL'ler için eylem**:
       - ***Açık: Kasa Bağlantılar, kullanıcılar Microsoft Teams bağlantılara tıkladığında bilinen, kötü amaçlı bağlantıların listesini denetler**: Bu ayarı seçin (aç).
     - **Koruma ayarları bölümüne tıklayın** :
       - **Kullanıcı tıklamalarını izleme**: Bu ayarın seçili (açık) olduğunu doğrulayın.
       - **Kullanıcıların özgün URL'ye tıklamasına izin ver**: Bu ayarı kapat (seçili değil).
       - **Bildirim ve uyarı sayfalarında kuruluş markasını görüntüleme**: Bu ayarı seçmek (açmak) ancak kuruluşunuzun şirket logonuzu karşıya yüklemek [için Microsoft 365 temasını özelleştirme başlığı altındaki](../../admin/setup/customize-your-organization-theme.md) yönergeleri izledikten sonra anlamlıdır.
   - **Bildirim** sayfası:
     - **Kullanıcıları nasıl bilgilendirmek istiyorsunuz?** bölüm: İsteğe bağlı olarak, **kullanılacak özelleştirilmiş bildirim metnini girmek için Özel bildirim metnini kullan'ı** seçebilirsiniz. Özel bildirim metnini kullanıcının diline çevirmek **için Otomatik yerelleştirme için Microsoft Çeviri kullan'ı** da seçebilirsiniz. Aksi takdirde **Varsayılan bildirim metnini kullan'ı** seçili bırakın.

5. İşiniz bittiğinde **Gönder'e** ve ardından **Bitti'ye** tıklayın.

Kasa Bağlantıları için Kasa Bağlantıları ilkelerini ve genel ayarları yapılandırmaya yönelik ayrıntılı yönergeler için aşağıdaki konulara bakın:

- [Office 365 için Microsoft Defender'da Kasa Bağlantıları ilkelerini ayarlama](set-up-safe-links-policies.md)
- [Office 365 için Microsoft Defender'da Kasa Bağlantıları için genel ayarları yapılandırma](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Şimdi SharePoint Online veya OneDrive İş'da algılanan dosyalar için uyarılar ayarlayın

SharePoint Online veya OneDrive İş'daki bir dosya kötü amaçlı olarak tanımlandığında bildirim almak için, bu bölümde açıklandığı gibi bir uyarı ayarlayabilirsiniz.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **Ilkeleri & kuralları** \> **Uyarı ilkesi'ne** gidin.

2. **Uyarı ilkesi** sayfasında **Yeni uyarı ilkesi'ne** tıklayın.

3. **Yeni uyarı ilkesi** sihirbazı açılır. **Ad** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ad**: Benzersiz ve açıklayıcı bir ad girin. Örneğin, Kitaplıklara Kötü Amaçlı Dosyalar yazabilirsiniz.
   - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Önem derecesi**: **Düşük**, **Orta** veya **Yüksek'i** seçin.
   - **Kategori**: **Tehdit yönetimi'ne** tıklayın.

   İşiniz bittiğinde **İleri'ye** tıklayın

4. **Uyarı ayarları oluştur** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ne hakkında uyarı vermek istiyorsunuz?** section: **Etkinlik dosyada** \> **kötü amaçlı yazılım algılandı**.
   - **Uyarının nasıl tetiklenmiş olmasını istiyorsunuz** ? bölümü: **Bir etkinlik kuralla her eşleştiğinde** doğrulama seçilidir.

   İşiniz bittiğinde **İleri'ye** tıklayın

5. **Alıcılarınızı ayarlayın** sayfasında aşağıdaki ayarları yapılandırın:
   - **E-posta bildirimleri gönder**: Bu ayarın seçili olduğunu doğrulayın.
   - **E-posta alıcıları**: Kötü amaçlı bir dosya algılandığında bildirim alması gereken bir veya daha fazla genel yönetici, güvenlik yöneticisi veya güvenlik okuyucu seçin.
   - **Günlük bildirim sınırı**: **Sınır** seçilmedi öğesini doğrulayın.

   İşiniz bittiğinde **İleri'ye** tıklayın

6. **Ayarlarınızı gözden geçirin** sayfasında ayarlarınızı gözden geçirin, **Evet, hemen aç'ın** seçili olduğunu doğrulayın ve **son'a** tıklayın

Uyarı ilkeleri hakkında daha fazla bilgi edinmek için [Bkz. Microsoft Purview uyumluluk portalında uyarı ilkeleri](../../compliance/alert-policies.md).

> [!NOTE]
> Yapılandırmayı bitirdiğinizde iş yükü araştırmalarını başlatmak için şu bağlantıları kullanın:
>
> - [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
> - [Office 365 için Defender'de karantinaya alınan dosyaları yönetmek için Microsoft 365 Defender portalını kullanma](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [SharePoint Online, OneDrive veya Microsoft Teams'da kötü amaçlı bir dosya bulunduğunda yapılması gerekenler](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [karantinaya alınan iletileri ve dosyaları Microsoft 365'da yönetici olarak yönetme](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Kurulum sonrası görevler ve sonraki adımlar

Tehdit koruması özelliklerini yapılandırdıktan sonra bu özelliklerin nasıl çalıştığını izlediğinize emin olun! İlkelerinizi gözden geçirin ve gözden geçirin ve istediğiniz şeyi yapmalarını sağlayın. Ayrıca değer katabilecek yeni özellikleri ve hizmet güncelleştirmelerini izleyin.

|Yapılması gerekenler|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|Raporları görüntüleyerek tehdit koruması özelliklerinin kuruluşunuz için nasıl çalıştığını görün|[E-posta güvenlik raporları](view-email-security-reports.md) <p> [Office 365 için Microsoft Defender raporları](view-reports-for-mdo.md) <p> [Tehdit Gezgini](threat-explorer.md)|
|Tehdit koruma ilkelerinizi gerektiği gibi düzenli aralıklarla gözden geçirin ve düzeltin|[Güvenli Puan](../defender/microsoft-secure-score.md) <p> [Microsoft 365 tehdit araştırması ve yanıt özellikleri](./office-365-ti.md)|
|Yeni özellikleri ve hizmet güncelleştirmelerini izleyin|[Standart ve Hedefli sürüm seçenekleri](../../admin/manage/release-options-in-office-365.md) <p> [İleti Merkezi](../../admin/manage/message-center.md) <p> [Microsoft 365 Yol Haritası](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Hizmet Açıklamaları](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
