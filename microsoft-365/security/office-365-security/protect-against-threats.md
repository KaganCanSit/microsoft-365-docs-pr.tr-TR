---
title: Office 365 için Microsoft Defender'da tehditlere karşı koruma, Kötü amaçlı yazılımdan koruma, Kimlik avı önleme, İstenmeyen posta önleme, Kasa bağlantıları, Kasa ekleri, Sıfır saatlik otomatik temizleme (ZAP), MDO güvenlik yapılandırması
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
description: Yöneticiler tehdit koruması hakkında daha fazla bilgi Microsoft 365 ve bunun nasıl organizasyon için kullanıla birlikte yapılandırıldığından emin olabilir.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 280cbd310742ecfe31ac8b565d285f7b464d3e24
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683855"
---
# <a name="protect-against-threats"></a>Tehditlere karşı koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Burada, uygulamanın öbeklere dönüş için Defender yapılandırmasını kesmeye Office 365 kılavuzu ve almaktadır. Office 365'de tehdit koruması özellikleri konusunda yeniysiniz, nereden başlayacağından emin değil veya en iyi şekilde bilgi edinmek *için bu kılavuzu* bir denetim listesi ve başlangıç noktası olarak kullanın.

> [!IMPORTANT]
> **İlk başta önerilen ayarlar her** ilke için dahil edilir; bununla birlikte, birçok seçenek vardır ve ayarlarınızı belirli kuruluşun ihtiyaçlarını karşılayacak şekilde değiştirebilirsiniz. İlkelerinizi veya değişikliklerinizin veri merkeziniz üzerinden çalışması için yaklaşık 30 dakika bekleyin.
>
> Office 365 için Defender'da çoğu ilkenin el ile yapılandırmasını atlamak için, önceden ayarlanmış güvenlik ilkelerini Standart veya Katı düzeyinde kullanabilirsiniz. Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).

## <a name="requirements"></a>Gereksinimler

### <a name="subscriptions"></a>Abonelikler

Tehdit koruması özellikleri tüm Microsoft veya *Office 365* dahil edilir; bununla birlikte, bazı aboneliklerin gelişmiş özellikleri vardır. Aşağıdaki tabloda, bu makalede yer alan koruma özellikleri ve en düşük abonelik gereksinimleri listelenmiştir.

> [!TIP]
> Denetimi açma yönergelerinin *ötesinde, adımlar* kötü amaçlı yazılımdan korunmaya, kimlik avından korunmaya ve istenmeyen posta önlemeye başlar. Bu adımlar, Office 365 Exchange Online Protection bir parçası olarak **işaretlenir**. Bu, (Office 365 için Defender) EOP'de yer alan ve bir araya gelene kadar Office 365 için **Defender** makalesinde garip görünebilir.

|Koruma türü|Abonelik gereksinimi|
|---|---|
|Denetim günlüğü (raporlama amacıyla)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Kötü amaçlı yazılımdan koruma|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Kimlik avı koruması|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|İstenmeyen posta önleme koruması|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|E-posta ve belgelerin diğer dosyalarında kötü amaçlı URL'lere ve Office karşı koruma (bağlantılar Kasa Ekleri Kasa koruma)|[Office 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Roller ve izinler

Yeni ilkeler için Defender Office 365'ı yapılandırmak için, size uygun bir rol atanmalıdır. Bu eylemleri gerçekleştiren roller için aşağıdaki tabloya bakın.

|Rol veya rol grubu|Daha fazla bilgi için|
|---|---|
|genel yönetici|[Yönetici Microsoft 365 hakkında](../../admin/add-users/about-admin-roles.md)|
|Güvenlik Yöneticisi|[Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference#security-administrator)
|Exchange Online Yönetimi|[Web'de Exchange Online](/exchange/permissions-exo/permissions-exo)|

Daha fazla bilgi edinmek için [Portalda izinler Microsoft 365 Defender bakın](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Raporlama ve soruşturma için denetim günlüğünü açma

- Denetim günlüğünizi erken başlatma. Aşağıdaki adımlardan bazıları için **denetimin AÇıK** olması gerekir. Denetim günlüğü, günlük kaydının dahil olduğu [aboneliklerde Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Tehdit koruması raporları, e-posta güvenlik raporları ve [Gezgin'de](view-email-security-reports.md) verileri görüntülemek [için denetim](threat-explorer.md) günlüğünün Açık olması *gerekir*. Daha fazla bilgi edinmek için [bkz. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Bölüm 1 - EOP'de kötü amaçlı yazılımdan koruma

Kötü amaçlı yazılımdan koruma için önerilen ayarlar hakkında daha fazla bilgi için bkz. [EOP kötü amaçlı yazılımdan koruma ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Kötü amaçlı **yazılımdan koruma sayfasını** Microsoft 365 Defender açın<https://security.microsoft.com/antimalwarev2>.

2. Kötü amaçlı **yazılımdan koruma** sayfasında, adına tıklayarak **Varsayılan (Varsayılan)** adlı ilkeyi seçin.

3. Açılan ilke ayrıntıları açılır sayfasında Koruma ayarlarını **düzenle'ye tıklayın** ve sonra aşağıdaki ayarları yapılandırabilirsiniz:
   - **Koruma ayarları** bölümü:
     - **Yaygın ekler filtresini etkinleştirme: Seç** (aç). Daha **fazla dosya türü eklemek için** Dosya türlerini özelleştir'e tıklayın.
     - **Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştir**: Bu ayarın seçili olduğunu doğrulayın. Kötü amaçlı yazılım için ZAP hakkında daha fazla bilgi için bkz. Kötü amaçlı yazılım için Sıfır saatlik [otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware)
   - **Karantina ilkesi**: Varsayılan AdminOnlyAccessPolicy değerini seçili bırakın. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).
   - **Bildirim** bölümü: Bildirim ayarlarından hiçbirinin seçilmemiş olduğunu doğrulayın.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İlke ayrıntıları ayrıntılarına dönüp Kapat'a **tıklayın**.

Kötü amaçlı yazılımdan koruma ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Bölüm 2 - EOP'de kimlik avı koruması ve Kimlik avı koruması Office 365

[Kimlik avı koruması,](anti-phishing-protection.md) [EOP içeren aboneliklerde kullanılabilir](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Gelişmiş kimlik avı koruması, windows için [Defender'da Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Kimlik avına karşı koruma ilkeleri için önerilen ayarlar hakkında daha fazla bilgi için bkz. Kimlik avı için [Microsoft Defender'da](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365) [EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) kimlik avı koruma ilkesi ayarları ve Kimlik avıyla mücadele ilkesi Office 365.

Aşağıdaki yordam, varsayılan kimlik avı önleme ilkesi yapılandırmayı açıklar. Ayarlar için Defender'da bulunan Office 365 açıkça işaretlenir.

1. kimlik **avıyla mücadele sayfasını** Microsoft 365 Defender açın<https://security.microsoft.com/antiphishing>.

2. Kimlik **avından korunma sayfasında** , adına tıklayarak **Office365 AntiPhish Default (Varsayılan)** adlı ilkeyi seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Kimlik avı eşiği & koruma** bölümü: Koruma **ayarlarını düzenle'ye** tıklayın ve açılan açılır listede aşağıdaki ayarları yapılandırın:
     - **Kimlik avı e-posta eşiği**<sup>\*</sup>: **2 - Katı** (Standart) veya **3 - Daha Katı (Katı** ) seçin.
     - **Kimliğe Bürünme**<sup>\*</sup> bölümü: Aşağıdaki değerleri yapılandırma:
       - Kullanıcıların **korunmasını** etkinleştir'i seçin, görüntülenen Yönet **(nn)** gönderenler bağlantısına tıklayın ve kimliğe bürünmeye karşı korumak için iç ve dış gönderenleri ekleyin (örneğin, kuruluşun yönetim kurulu üyeleri, CEO'nız, CFO'nız ve diğer üst düzey liderler).
       - Korumak **için etki alanlarını etkinleştir'i** seçin ve sonra aşağıdaki ayarları yapılandırarak görünür:
         - Kabul **edilen etki alanlarınıza (Etki** alanlarımı görüntüle'ye tıklayarak **görünür)** kimliğe bürünülme tarafından korunması için Sahibim etki alanlarını ekle'yi seçin.
         - Diğer etki alanlarındaki gönderenleri korumak için Özel etki alanlarını ekle'yi **seçin, görüntülenen** Yönet **(nn)** özel etki alanları bağlantısını tıklatın ve kimliğe bürünmelerden korumak için diğer etki alanlarını ekleyin.
     - **Güvenilen gönderenler ve**<sup>\*</sup> etki alanları ekleme bölümü: Gönderen ve gönderen etki alanı özel durumlarını gerekirse kimliğe bürünme koruması olarak yapılandırmak için Yönet **(nn)** güvenilen gönderenler ve etki alanları'ya tıklayın.
     - Posta kutusu zekası <sup>\*</sup> ayarları: Posta **kutusu zekasını etkinleştir ve** Kimliğe **bürünme koruması için zekayı etkinleştir'in seçili** olduğunu doğrulayın.
     - **Kimlik bilgileri bölümü** : Kimlik doğrulama **akıllı telefonlarını etkinleştir'in seçili** olduğunu doğrulayın.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Eylemler** bölümü: Eylemleri **düzenle'ye** tıklayın ve açılan açılır listede aşağıdaki ayarları yapılandırabilirsiniz:
     - **İleti eylemleri** bölümü: Aşağıdaki ayarları yapılandırma:
       - **İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa**<sup>\*</sup>: İletiyi **karantinaya alın'ı seçin**. Kullanıcı **kimliğe bürünme** koruması tarafından [karantinaya alınmış](quarantine-policies.md) iletilere uygulanan karantina ilkesi seçen bir Karantina ilkesi uygula kutusu görüntülenir.
       - **İleti kimliğine bürünülen bir etki alanı olarak algılanırsa**<sup>\*</sup>: İletiyi **karantinaya alın'ı seçin**. Etki **alanı kimliğe** bürünme koruması tarafından karantinaya [](quarantine-policies.md) alınmış iletilere uygulanan karantina ilkesi seçen bir Karantina ilkesi uygula kutusu görüntülenir.
       - **Posta kutusu zekası kimliğine** bürünülen bir kullanıcı <sup>\*</sup>algılarsa **: İletiyi** alıcıların Gereksiz E-posta klasörlerine taşı (Standart) veya İletiyi **karantinaya alın** (Katı) seçin. İletiyi **karantinaya alın'ı** seçerseniz, burada posta kutusu zekası koruması tarafından [](quarantine-policies.md) karantinaya alınmış iletilere uygulanan karantina ilkesine tıklayın.
       - **İletinin e-posta adresi olarak algılanırsa**: İletiyi alıcıların Gereksiz E-posta klasörlerine **taşı (Standart** ) veya İletiyi karantinaya **alın (Katı** ) seçeneğini seçin.  İletiyi **karantinaya alın'ı** seçerseniz, burada karantina ilkesi ilkesi seçerek, [](quarantine-policies.md) akıllı ifade koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesi görüntülenir.
     - **Güvenlik ipuçları & bölümü** : Aşağıdaki ayarları yapılandırma:
       - **İlk kişi güvenlik ipucu**: Seçin (aç).
       - **Kullanıcı kimliğine bürünme güvenlik ipucu**<sup>\*</sup>: Seçin (aç).
       - **Etki alanı kimliğe bürünme güvenlik ipucu**<sup>\*</sup> göster: Seçin (aç).
       - **Kullanıcı kimliğe bürünme alışılmadık güvenlik ipucu**<sup>\*</sup> göster: Seçin (aç).
       - **Kimlik doğrulaması olmayan gönderenler için kimlik doğrulaması (?) göster**: Seçin (aç).
       - **"Aracılığıyla" etiketini göster**: Seçin (aç).

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   <sup>\*</sup>Bu ayar yalnızca Windows için Defender'da Office 365.

4. **Kaydet'e ve** ardından Kapat'a **tıklayın**

Kimlik avı koruma ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de](configure-anti-phishing-policies-eop.md) kimlik avı koruma ilkelerini yapılandırma ve Kimlik avı için [Microsoft Defender'da](configure-mdo-anti-phishing-policies.md) kimlik avı ilkelerini yapılandırma Office 365.

## <a name="part-3---anti-spam-protection-in-eop"></a>Bölüm 3 - EOP'de istenmeyen posta önleme koruması

İstenmeyen posta önleme için önerilen ayarlar hakkında daha fazla bilgi için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Microsoft 365 Defender **portalında** İstenmeyen posta önleme ilkeleri sayfasını açın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden İstenmeyen postayla mücadele gelen ilkesi **(Varsayılan)** adlı ilkeyi seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **İstenmeyen posta & toplu e-posta** eşiği bölümü: **İstenmeyen posta eşiğini ve özelliklerini düzenle'ye tıklayın**. Görüntülenen açılır listede aşağıdaki ayarları yapılandırabilirsiniz:
     - **Toplu e-posta** eşiği: Bu değeri 5 (Katı) veya 6 (Standart) olarak ayarlayın.
     - Diğer ayarları varsayılan değerlerinde bırakın (**Kapalı veya** **Yok**).

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Eylemler** bölümü: Eylemleri **düzenle'ye tıklayın**. Görüntülenen açılır listede aşağıdaki ayarları yapılandırabilirsiniz:
     - **İleti eylemleri** bölümü:
       - **İstenmeyen** posta: **İletiyi Gereksiz E-posta klasörüne taşı'nın** seçili olduğunu doğrulayın (Standart) veya İletiyi karantinaya **alın (Katı** ) seçeneğini seçin.
       - **Yüksek güven içeren istenmeyen posta**: İletiyi **karantinaya alın'ı seçin**.
       - **Kimlik avı**: İletiyi **karantinaya alın'ı seçin**.
       - **Yüksek güvenlikli kimlik avı**: **İletileri karantinaya alın'ın** seçili olduğunu doğrulayın.
       - **Toplu**: İletiyi **Gereksiz E-posta klasörüne taşı'nın seçili** olduğunu doğrulayın (Standart) veya İletiyi karantinaya **alın (Katı** ) seçeneğini seçin.

       İletiyi  karantinaya **alın'ı** seçen her eylem için, burada gereksiz posta önleme korumasıyla [](quarantine-policies.md) karantinaya alınan iletilere uygulanan karantina ilkesi seçen bir Karantina ilkesi seçin kutusu görüntülenir.

     - **İstenmeyen postayı şu kadar gün karantinada** tutma: **Değeri 30 gün doğrulama** .
     - **İstenmeyen posta güvenliği ipuçlarını** etkinleştirme: Bu ayarın seçili olduğunu doğrulayın (açık).
     - **Sıfır saatlik otomatik temizlemeyi etkinleştir (ZAP)**: Bu ayarın seçili olduğunu doğrulayın (açık).
       - **Kimlik avı iletileri için etkinleştir**: Bu ayarın seçili olduğunu (açık) doğrulayın. Daha fazla bilgi için bkz[. Kimlik avı için Sıfır saatlik otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing)
       - **İstenmeyen posta iletilerini etkinleştirme**: Bu ayarın seçili olduğunu (açık) doğrulayın. Daha fazla bilgi için bkz[. İstenmeyen posta için Sıfır saatlik otomatik temizleme (ZAP).](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam)

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **İzin verilen ve engellenen** gönderenler ve etki alanları bölümü: [EOP'de](create-block-sender-lists-in-office-365.md) engellenen gönderenler listeleri oluşturma veya [EOP'de](create-safe-sender-lists-in-office-365.md) güvenilir gönderen listeleri oluşturma konusunda açıklandığı gibi izin verilen gönderenleri ve izin verilen etki alanlarını gözden geçirme veya düzenleme.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İşlemi tamamladığınızda, **Kapat**'a tıklayın.

İstenmeyen posta önleme ilkelerini yapılandırmaya yönelik ayrıntılı yönergeler için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Bölüm 4 - Kötü amaçlı URL'lere ve dosyalara karşı koruma (Kasa Için Defender'da Kasa Bağlantılara ve Bağlantılara Office 365)

Kötü amaçlı URL'lere ve dosyalara karşı tıklama süresi koruması, Microsoft [Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Tüm Ekler ve Bağlantılar [Kasa aracılığıyla](safe-attachments.md) [Kasa](safe-links.md) ayarlanır.

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Kasa için Microsoft Defender'da Ekleri Office 365

Ekler hakkında önerilen ayarlar hakkında daha fazla bilgi Kasa bkz.[ Kasa ayarlarına tıklayın](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Microsoft 365 Defender **portalında**, 'da Kasa ekleri sayfasını açın<https://security.microsoft.com/safeattachmentv2>.

2. Ekler **Kasa, Genel** **ayarlar'a** tıklayın ve beliren açılır sayfada aşağıdaki ayarları yapılandırabilirsiniz:
   - **SharePoint, OneDrive için Office 365** Defender'ı Microsoft Teams: Bu ayarı aç (![Aç/kapat).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **E-posta Kasa, SharePoint, OneDrive** ve Microsoft Teams için Ekleri açmadan önce, denetim günlüğünün kuruluşta açık olduğunu doğrulayın. Bu eylem normalde, bir hesapta Denetim Günlükleri rolü atanmış olan biri Exchange Online. Daha fazla bilgi için bkz [. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md)!

   - **Belgeler Kasa istemcileri için Office açma**: Bu ayarı açma (![Aç/kapat).](../../media/scc-toggle-on.png) Bu özelliğin yalnızca gerekli lisans türlerinde kullanılabilir ve anlamlı olduğunu unutmayın. Daha fazla bilgi için bkz[. Kasa Belge Belgeleri'Microsoft 365 E5](safe-docs.md).
   - **Belgelerin dosyayı kötü amaçlı olarak tanımlasa bile Kasa** Korumalı Görünüm'e tıklamasına izin ver: Bu ayarın kapalı olduğunu doğrulama (![Kapalı olarak değiştir).](../../media/scc-toggle-off.png).

   Bitirdikten sonra Kaydet'e **tıklayın.**

3. Ekler sayfasında **Kasa** oluştur'a ![tıklayın](../../media/m365-cc-sc-create-icon.png).

4. Açılan **Kasa Ekleri Oluştur ilke** sihirbazında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **İlke sayfanıza bir ad** girin:
     - **Ad**: Benzersiz ve açıklayıcı bir ad girin.
     - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Kullanıcılar ve etki alanları** sayfası: Bu ilk ilkeniz olduğundan ve büyük olasılıkla kapsamı en üst düzeye çıkarmak istediğinizden, [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) kabul edilen etki alanlarınızı Etki Alanları kutusuna **girmeyi** düşünebilirsiniz. Aksi takdirde, daha ayrıntılı **denetim için** **Kullanıcılar ve** Gruplar kutularını kullanabilirsiniz. Özel durumları belirtmek için Bu kullanıcıları, grupları ve etki **alanlarını dışla'ı seçerek ve** değerleri girebilirsiniz.
   - **Ayarlar** sayfa:
     - **Kasa bilinmeyen kötü amaçlı yazılım yanıtı: Engelle'yi** **seçin**.
     - **Karantina ilkesi**: Varsayılan değer boştur ve bu da AdminOnlyAccessPolicy ilkesi olduğu anlamına gelir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).
     - **Algılanan ekleri olan eki yeniden yönlendirme** **: Yeniden** yönlendirmeyi etkinleştir: Bu ayarı açın (seçin) ve algılanan iletileri almak için bir e-posta adresi girin.
     - **Varsayılan ayarı Kasa Tarama** tamamlanmadı ise Ekler algılama yanıtı uygulama (zaman aşımı veya hatalar): Bu ayarın seçili olduğunu doğrulayın.

5. Bitirdikten sonra Gönder'e **ve** ardından Bitti'ye **tıklayın**.

6. (Önerilen) Genel yönetici veya SharePoint Online yöneticisi olarak, SharePoint Online PowerShell'de **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** cmdlet'ini _DisallowInfectedFileDownload_ `$true` parametresiyle çalıştırın.
   - `$true` algılanan dosyalar için tüm eylemleri engeller (Sil dışında). Kişiler algılanan dosyaları açz, taşıya, kopyalayıp paylaşsalar.
   - `$false` Sil ve İndir dışındaki tüm eylemleri engeller. Kişiler riski kabul etme ve algılanan dosyayı indirmeyi seçebilir.

7. Değişikliklerinizin tüm veri merkezlerine yayılması için 30 dakika Microsoft 365 bekleyin.

Ekleri Yapılandırma hakkında ayrıntılı Kasa Ekleri İlkeleri ve Ekleri Kasa genel ayarları için aşağıdaki konulara bakın:

- [Kasa Office 365 için Microsoft Defender'da Ekleri Ayarlama Office 365](set-up-safe-attachments-policies.md)
- [E-Kasa, E-posta SharePoint, OneDrive için Ekleri Açma Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Kasa için Microsoft Defender'da Bağlantılar Office 365

Bağlantılar'ın önerilen ayarları hakkında daha fazla Kasa için bkz. [Kasa bağlantı ayarlarını değiştirme](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Kasa **portalında** Yer alan Microsoft 365 Defender sayfasını açın<https://security.microsoft.com/safelinksv2>.

2. Bağlantılar **Kasa Genel** **ayarlar'a** tıklayın ve beliren açılır sayfada aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ayarlar uygulamalar bölümündeki içeriğe Office 365 tıklayın**:
     - **Office 365 Kasa'da Bağlantıları kullanma**: Bu ayarın açık olduğunu doğrulama (![Açık.](../../media/scc-toggle-on.png))
     - **Kullanıcılar Office 365 korumalı bağlantılara** tıklayma ayarını izleme: Bu ayarı kapatın (![Kapalı olarak kapatın.](../../media/scc-toggle-off.png))
     - **Kullanıcıların Office 365 uygulamaları içinde özgün URL'ye** tıklamalarına izin verme: Bu ayarın açık olduğunu doğrulayın (![Iki durumlu düğme).](../../media/scc-toggle-on.png)

   Bitirdikten sonra Kaydet'e **tıklayın.**

3. Yeni Bağlantılar **sayfasına Kasa** simgesine ![tıklayın](../../media/m365-cc-sc-create-icon.png).

4. Açılan **Yeni Kasa Bağlantıları ilke** sihirbazında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **İlke sayfanıza bir ad** girin:
     - **Ad**: Benzersiz ve açıklayıcı bir ad girin.
     - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Kullanıcılar ve etki alanları** sayfası: Bu ilk ilkeniz olduğundan ve büyük olasılıkla kapsamı en üst düzeye çıkarmak istediğinizden, [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) kabul edilen etki alanlarınızı Etki Alanları kutusuna **girmeyi** düşünebilirsiniz. Aksi takdirde, daha ayrıntılı **denetim için** **Kullanıcılar ve** Gruplar kutularını kullanabilirsiniz. Özel durumları belirtmek için Bu kullanıcıları, grupları ve etki **alanlarını dışla'ı seçerek ve** değerleri girebilirsiniz.
   - **Koruma ayarları** sayfası:
     - **İletilerde kötü amaçlı olabilecek bilinmeyen URL'lerin eylemlerini seçin**: Bu ayarı **Aç**.
     - **Program içinde bilinmeyen veya kötü amaçlı olabilecek URL'ler Microsoft Teams** seçin: Bu ayarı **Aç**. Mart 2020'den sonra, bu ayar Önizleme'dedir ve yalnızca Microsoft Teams Teknolojisini Benimseme Programı (TAP) üyeleri tarafından kullanılabilir veya işlevseldir.
     - **Dosyaları işaret edecek şüpheli bağlantılar ve bağlantılar için gerçek zamanlı URL tarama uygulama**: Bu ayarı seçin (aç).
       - **İletiyi teslim etmek için URL tarama işleminin tamam bekleyin**: Bu ayarı seçin (aç).
     - **Farklı Kasa Kuruluş içinde gönderilen e-posta iletilerine bağlantılar**: Bu ayarı seçin (aç).
     - **Kullanıcı tıklatmalarını izleme**: Bu ayarın seçilmemiş olduğunu doğrulayın (kapalı).
     - **Kullanıcıların özgün URL'ye tıklamalarına izin verme**: Bu ayarın açık olduğunu doğrulayın (seçili).
     - Bildirim ve **uyarı** sayfalarında kuruluşun markasını görüntüleme: Bu ayarı seçmek (açma) yalnızca Şirket logonuzu yüklemek için [Microsoft 365](../../admin/setup/customize-your-organization-theme.md) temasını özelleştirme'daki yönergeleri izledikten sonra anlamlıdır.
     - **Aşağıdaki URL'leri yeniden yazma:** Bu ayar için özel bir önerimiz yok. Daha fazla bilgi için, [Bağlantılar ilkeleri altında "Aşağıdaki URL'leri yeniden yazma" Kasa bakın](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).
   - **Bildirim** sayfası:
     - **Kullanıcılara nasıl bildirim yapmak gerekir?** bölüm: İsteğe bağlı olarak, Özelleştirilmiş bildirim **metnini girmek için** Özel bildirim metni kullan'ı seçin. Özel bildirim metnini **Microsoft Çeviri diline çevirmek üzere** Otomatik olarak yerelleştirme için Kullanıcı Arabirimini kullan'ı da kullanabilirsiniz. Aksi takdirde Varsayılan **bildirim metnini kullan'ın seçili olduğu bırakın** .

5. Bitirdikten sonra Gönder'e **ve** ardından Bitti'ye **tıklayın**.

Yeni bağlantılar için Bağlantılar Kasa genel ayarlarını yapılandırmaya yönelik ayrıntılı Kasa, aşağıdaki konulara bakın:

- [Destek için Microsoft Defender Kasa da Bağlantılar ilkelerini Office 365](set-up-safe-links-policies.md)
- [Web için Microsoft Defender'Kasa Bağlantılar için genel ayarları Office 365](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Şimdi SharePoint Online'da veya başka bir OneDrive İş'de algılanan dosyalar için uyarılar ayarlayın

SharePoint Online'daki veya OneDrive İş'daki bir dosya kötü amaçlı olarak tanım geldiğinde bildirim almak için, bu bölümde açıklandığı gibi bir uyarı kurabilirsiniz.

1. aşağıdaki Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>ve **işbirliği &** \> **Ilkeler'e & ilkesi'ne** \> **gidin**.

2. Uyarı ilkesi **sayfasında Yeni** uyarı **ilkesi'ne tıklayın**.

3. Yeni **uyarı ilkesi sihirbazı** açılır. Ad **sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ad**: Benzersiz ve açıklayıcı bir ad girin. Örneğin, Kitaplıklar'a Kötü Amaçlı Dosyalar yazabilirsiniz.
   - **Açıklama**: İsteğe bağlı bir açıklama girin.
   - **Önem Derecesi****: Düşük,** Orta **veya Yüksek'i** **seçin**.
   - **Kategori**: Tehdit **yönetimi'ne seçin**.

   Bitirdikten sonra, Sonraki'ne **tıklayın.**

4. Uyarı **ayarları oluştur sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ne hakkında uyarı almaksınız?** bölüm: **Etkinlik Dosyada** \> **kötü amaçlı yazılım algılandı**.
   - **Uyarının tetiklenirken nasıl tetiklenir** ? Bölüm: Bir **etkinlik kuralla her eşleşmesi olduğunda doğrula** seçilir.

   Bitirdikten sonra, Sonraki'ne **tıklayın.**

5. Alıcılarınızı **ayarlayın sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **E-posta bildirimleri gönderme**: Bu ayarın seçili olduğunu doğrulayın.
   - **E-posta** alıcıları: Kötü amaçlı bir dosya algılandığında bildirim alacak bir veya birden çok genel yönetici, güvenlik yöneticisi veya güvenlik okuyucusu seçin.
   - **Günlük bildirim sınırı**: Sınır **yok'ın seçili** olduğunu doğrulayın.

   Bitirdikten sonra, Sonraki'ne **tıklayın.**

6. Ayarlarınızı **gözden geçirme sayfasında** ayarlarınızı gözden geçirip Evet **,** hemen aç'ın seçili olduğunu doğrulayın ve ardından Son'a **tıklayın**

Uyarı ilkeleri hakkında daha fazla bilgi edinmek için bkz[. İlke Microsoft 365 uyumluluk merkezi](../../compliance/alert-policies.md).

> [!NOTE]
> Yapılandırmayı bitirdikten sonra, iş yükü soruşturmalarını başlatmak için bu bağlantıları kullanın:
>
> - [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
> - [Office 365 için Defender Microsoft 365 Defender da karantinaya alınmış dosyaları yönetmek için Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [SharePoint Online'da kötü amaçlı dosya bulunursa, OneDrive ne Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Karantinaya alınan iletileri ve dosyaları bir yönetici olarak e-posta Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Kurulum sonrası görevleri ve sonraki adımlar

Tehdit koruması özelliklerini yapılandırdikten sonra, bu özelliklerin nasıl çalıştığını izledikten emin olun! İlkelerinizi gözden geçirin ve gözden geçirin; böylece, gerekenleri yapmaları için bunları düzeltin. Ayrıca, değer katan yeni özellikleri ve hizmet güncelleştirmelerini izleyin.

|Ne yapmalı?|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|Raporları görüntüerek tehdit koruması özelliklerinin organizasyonunız için nasıl çalıştığını görme|[E-posta güvenlik raporları](view-email-security-reports.md) <p> [Microsoft Defender Güvenlik raporları Office 365](view-reports-for-mdo.md) <p> [Tehdit Gezgini](threat-explorer.md)|
|Tehdit koruması ilkelerinizi gereken şekilde düzenli aralıklarla gözden geçirme ve düzeltme|[Güvenli Puan](../defender/microsoft-secure-score.md) <p> [Microsoft 365 soruşturma ve yanıt özelliklerini inceleme](./office-365-ti.md)|
|Yeni özellikleri ve hizmet güncelleştirmelerini izleyin|[Standart ve Hedefli sürüm seçenekleri](../../admin/manage/release-options-in-office-365.md) <p> [İleti Merkezi](../../admin/manage/message-center.md) <p> [Microsoft 365 Yol Haritası](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Hizmet Açıklamaları](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
