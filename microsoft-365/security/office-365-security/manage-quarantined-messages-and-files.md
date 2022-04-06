---
title: Karantinaya alınan iletileri ve dosyaları yönetici olarak yönetme
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection'da (EOP) kullanıcılar için karantinaya alınmış iletileri görüntülemeyi ve yönetmeyi öğrenebilir. Office 365 için Microsoft Defender olan kuruluşlarda yöneticiler SharePoint Online, OneDrive İş ve Microsoft Teams'te karantinaya alınmış dosyaları yönetebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 449886f6272c81f9947fd3e7ea869e565326578f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469657"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online ya da tek başına Exchange Online Protection Exchange Online Protection EOP Exchange Online) kuruluşlarında, karantinada tehlikeli veya istenmeyen iletiler karantinaya alın. Daha fazla bilgi için bkz. [EOP'de e-posta iletileri karantinaya alınmış](quarantine-email-messages.md).

Yöneticiler tüm kullanıcılar için karantinaya alınmış ileti türlerini  görüntüleme, bırakma ve silme. Yöneticiler hatalı pozitif sonuçlar da Microsoft'a bildirebilirsiniz.

Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım olarak karantinaya alınmış iletileri, yüksek güven kimlik avı veya posta akış kuralları (aktarım kuralları olarak da bilinir) sonucunda yönetebilir. Ancak yöneticiler, iletinin _neden_ karantinaya alındığına (desteklenen özellikler için) göre karantinaya alınmış iletilerde kullanıcılara izin verilenleri tanımlamak için karantina ilkelerini kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

Office 365 için Microsoft Defender [Kasa'a](mdo-for-spo-odb-and-teams.md) sahip olan kuruluşlarda yöneticiler, SharePoint, OneDrive ve klasörlerin ekleri SharePoint tarafından karantinaya Microsoft Teams.

karantinaya alınmış iletileri Microsoft 365 Defender portalında veya PowerShell'de Exchange Online (Microsoft 365 posta kutuları olan Microsoft 365 için PowerShell'de; Exchange Online'de ise tek başına EOP PowerShell ile yönetirsiniz Exchange Online kutularını da) kullanın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Oturum açma Microsoft 365 Defender için, ' gidin<https://security.microsoft.com>. Doğrudan Karantina sayfasına **gitmek için** , kullanın <https://security.microsoft.com/quarantine>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Tüm kullanıcılar için karantinaya alınmış iletilerde eylem yapmak için, Kuruluş **Yönetimi, Güvenlik** Yöneticisi veya Karantina Yöneticisi rol gruplarının **üyesi olmak**<sup>\*</sup> gerekir.  Microsoft'a ileti göndermek için Güvenlik Yöneticisi rol grubunun **üyesi olmak** gerekir.
  - Tüm kullanıcılar için karantinaya alınmış iletilere salt okunur erişim için, Genel Okuyucu veya Güvenlik **Okuyucu rol** **gruplarının üyesi** olmak gerekir.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.
  - <sup>\*</sup>[Microsoft 365 Defender portalında](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) **E-posta &** işbirliği rollerinde yer alan Karantina Yöneticisi rol grubunun üyelerinin, Exchange Online PowerShell'de karantina yordamları gerçekleştirmek için [Exchange Online'te](/Exchange/permissions-exo/permissions-exo#role-groups) Skrya Yönetimi rol grubunun üyesi Exchange Online gerekir. 

- Karantinaya alınan iletiler, karantinaya alındıklarına bağlı olarak varsayılan bir süre boyunca korunur. Bekletme süresi dolduğunda, iletiler otomatik olarak silinir ve kurtarılamaz. Daha fazla bilgi için bkz. [EOP'de karantinaya alınmış e-posta iletileri Office 365 için Defender](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Karantinaya alınmış Microsoft 365 Defender iletilerini yönetmek için kullanıcı portalını kullanma

### <a name="view-quarantined-email"></a>Karantinaya alınmış e-postayı görüntüleme

1. Aşağıdaki Microsoft 365 Defender portalında E-posta Gönder <https://security.microsoft.com>ve işbirliğini **& Karantina'ya** \>  \> **gidin**. Doğrudan Karantina sayfasına **gitmek için** , kullanın <https://security.microsoft.com/quarantine>.

2. Karantina sayfasında **,** E-posta sekmesinin **seçili** olduğunu doğrulayın.

3. Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz. Gösterilen **sütunları değiştirmek**  için Sütunları özelleştir'e tıklayın. Varsayılan değerler yıldız işaretiyle () işaretlenir<sup>\*</sup>:

   - **Alınan saat**<sup>\*</sup>
   - **Konu**<sup>\*</sup>
   - **Gönderen**<sup>\*</sup>
   - **Karantina nedeni**<sup>\*</sup>
   - **Sürüm durumu**<sup>\*</sup>
   - **İlke türü**<sup>\*</sup>
   - **Son kullanma tarihi**<sup>\*</sup>
   - **Alıcı**
   - **İleti Kimliği**
   - **İlke adı**
   - **İleti boyutu**
   - **Posta yönü**
   - **Alıcı etiketi**

   Bitirdikten sonra Uygula'ya **tıklayın**.

4. Sonuçları filtrelemek için Filtre'ye **tıklayın**. Görüntülenen Filtreler açılır yapısında **aşağıdaki** filtreler kullanılabilir:
   - **İleti Kimliği**: İletinin genel benzersiz tanımlayıcısıdır.

     Örneğin, ileti [izlemeyi,](message-trace-scc.md) kuruluşta bir kullanıcıya gönderilmiş bir iletiyi bakmak için kullandınız ve ileti teslim etmek yerine karantinaya alındı. Tüm ileti kimliği değerini de dahil etmek gerekir; bu değer köşeli ayraçları () içerebilir\<\>. Örneğin: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Gönderen adresi**
   - **Alıcı adresi**
   - **Konu**
   - **Alınan saat**: Başlangıç **saati ve Bitiş** **saati (tarih** ) girin.
   - **Son kullanma** tarihi: İletileri karantinadan kullanım süresi dolana kadar filtrelerini uygulama:
     - **Bugün**
     - **Sonraki 2 gün**
     - **Sonraki 7 gün**
     - **Özel**: Başlangıç **saati ve Bitiş** **saati (tarih** ) girin.
   - **Alıcı etiketi**
   - **Karantina nedeni**:
     - **Aktarım kuralı** (posta akışı kuralı)
     - **Toplu**
     - **İstenmeyen posta**
     - **Kötü** amaçlı yazılım: EOP'de kötü amaçlı yazılımdan koruma ilkeleri Kasa EOP'de ek ilkeleri Office 365 için Defender. **İlke Türü** değeri, hangi özelliğin kullanılmış olduğunu gösterir.
     - **Kimlik avı**: İstenmeyen posta filtresi  kararı, Kimlik avı veya kimlik avı korumasını karantinaya [aldı (kimlik](set-up-anti-phishing-policies.md#spoof-settings) avı ayarları veya [kimliğe bürünme koruması](set-up-anti-phishing-policies).
     - **Yüksek güven kimlik avı**
   - **Alıcı**: **Tüm kullanıcılar veya** Yalnızca **ben**. Son kullanıcılar yalnızca kullanıcılara gönderilen karantinaya alınmış iletileri yönetebilir.
   - **Sürüm durumu**: Aşağıdaki değerlerden herhangi biri:
     - **Gözden geçirme gerekiyor**
     - **Onaylandı**
     - **Reddedildi**
     - **Sürüm isteği alındı**
     - **Yayımlanan**
   - **İlke Türü**: İletileri ilke türüne göre filtreleme:
     - **Kötü amaçlı yazılımdan koruma ilkesi**
     - **Kasa ekleri ilkesi**
     - **Kimlik avı önleme ilkesi**
     - **İstenmeyen posta önleme ilkesi**
     - **Aktarım kuralı** (posta akışı kuralı)

   Bitirdikten sonra Uygula'ya **tıklayın**. Filtreleri temizlemek için Filtreleri temizle simgesine ![tıklayın.](../../media/m365-cc-sc-clear-filters-icon.png) **Filtreleri temizleme**.

5. Belirli iletileri **bulmak** için Arama kutusunu ve karşılık gelen değeri kullanın. Joker karakterler desteklenmiyor. Aşağıdaki değerlere göre arama yapabilirsiniz:
   - Gönderen e-posta adresi
   - Konu. İletinin konusunun tamamını kullanın. Arama büyük/harfe duyarlı değildir.

   Arama ölçütlerini girdikten sonra, sonuçları filtrelemek için ENTER tuşuna basın.

Belirli bir karantinaya alınmış iletiyi bu olduktan sonra, ayrıntılarını görüntülemek ve iletiyle ilgili bir işlem yapmak için (örneğin, iletiyi görüntüleme, bırakma, indirme veya silme) iletiyi seçin.

#### <a name="view-quarantined-message-details"></a>Karantinaya alınan ileti ayrıntılarını görüntüleme

Listeden karantinaya alınmış iletiyi seçin, görüntülenen ayrıntılar açılır iletisinde aşağıdaki bilgiler kullanılabilir.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Karantinaya alınmış iletinin ayrıntılar uçarak çıkış" lightbox="../../media/quarantine-message-details-flyout.png":::

- **İleti Kimliği**: İletinin genel benzersiz tanımlayıcısıdır. İleti üst **bilgisinde İleti** Kimliği üst bilgisi alanında kullanılabilir.
- **Gönderen adresi**
- **Alındı**: İletinin alın aldığı tarih/saat.
- **Konu**
- **Karantina nedeni**: Bir iletinin İstenmeyen **Posta, Toplu**, Kimlik Avı, bir posta akış **kuralıyla (** Aktarım kuralı) eş olup olmadığını veya Kötü Amaçlı Yazılım içeren olarak tanım gösterip tanım olmadığını **gösterir**.
- **İlke türü**
- **İlke adı**
- **Alıcı sayısı**
- **Alıcılar**: İleti birden çok alıcı içeriyorsa, alıcıların tam listesini görmek için  İletiyi önizleme'yi veya İleti üst bilgilerini görüntüle'yi tıklatmanız gerekir.
- **Alıcı etiketi**: Daha fazla bilgi için bkz [. Alıcı etiketleri Office 365 için Microsoft Defender](user-tags.md).
- **Son kullanma** tarihi: İletinin karantinadan otomatik olarak ve kalıcı olarak silinecek olduğu tarih/saat.
- **Yayım tarihi**: İletinin yayım tarihi olan tüm e-posta adresleri (varsa).
- **Henüz yayınlanma tarihi:** İletinin henüz yayınlanmamış olduğu tüm e-posta adresleri (varsa).

İleti üzerinde işlem yapmak için sonraki bölüme bakın.

> [!NOTE]
> Ayrıntılar uç iletisinde kalmak, ancak üzerinde karantinaya alınmış iletiyi değiştirmek için, uç ilişkinin üst kısmında bulunan yukarı ve aşağı okları kullanın.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Karantinaya alınmış iletinin ayrıntılar iletisinde yukarı ve aşağı oklar" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Karantinaya alınmış e-postada eyleme geç

Listeden karantinaya alınmış bir ileti belirttikten sonra, ayrıntılar iletisinde aşağıdaki eylemler kullanılabilir:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="Karantinaya alınmış iletinin ayrıntılar iletisinde Kullanılabilir eylemler" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Sürüm e-postası simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Sürüm e-postası**<sup>\*</sup>: Görüntülenen açılır bölmede aşağıdaki seçenekleri yapılandırabilirsiniz:
  - **Göndereni kurum izin listesine ekleme: Gönderenden** gelen iletilerin karantinaya alınmasını önlemek için bu seçeneği belirtin.
  - Aşağıdaki seçeneklerden birini belirleyin:
    - **Tüm alıcılara sürüm**
    - **Belirli alıcılara sürüm**: Görüntülenen Alıcılar **kutusunda alıcıları** seçin
  - **Bu iletinin bir kopyasını diğer alıcılara gönderme**: Bu seçeneği belirtin ve görüntülenen Alıcılar kutusuna alıcının **e-posta** adreslerini girin.

    > [!NOTE]
    > İletinin bir kopyasını diğer alıcılara göndermek için, iletiyi özgün alıcılardan en az biri olarak bırakmanız gerekir (Tüm alıcıların için serbest bırak'ı veya Belirli  alıcılara **bırak'ı seçin**).

  - **algılamayı geliştirmek için iletiyi Microsoft'a gönderin (** hatalı pozitif): Varsayılan olarak bu seçenek seçilidir ve hatalı karantinaya alınmış iletiyi hatalı pozitif olarak Microsoft'a raporlar. İleti istenmeyen posta, toplu kimlik avı veya kötü amaçlı yazılım içeren olarak karantinaya alınmışsa, ileti Microsoft İstenmeyen Posta Çözümleme Ekibi'ne de bildiriliyor. Çözümlemelerinin sonuçlarına bağlı olarak, hizmet genelinde istenmeyen posta filtresi kuralları, iletiyi izin verecek şekilde ayarlanabilir.

  - **İletilere şu şekilde izin** ver: Bu seçenek varsayılan olarak kapalıdır (![Kapalı olarak geçiş).](../../media/scc-toggle-off.png) Benzer URL'lere, eklere](../../media/scc-toggle-on.png) ve diğer özelliklere sahip iletilerin karantinaya alınmasını geçici olarak önlemek için bu özelliği açın (![Aç/Aç). Bu seçeneği açık durumdayken aşağıdaki seçenekler kullanılabilir:
    - **Sonra kaldır**: Bunun gibi iletilere ne kadar süre izin vermek istediğiniz seçin. **1 gün ile** **30 gün arasında bir gün seçin**. Varsayılan değer 30'dır.
    - **İsteğe bağlı** not: İzin vermek için yararlı bir açıklama girin.

  Bitirdikten sonra İletiyi **bırak'a tıklayın**.

  Mesaj bırakmayla ilgili notlar:

  - Aynı alıcıya birden çok kez ileti bırakasınız.
  - Yalnızca iletiyi henüz teslim etmeen alıcılar olası alıcılar listesinde görünür.
  - Algılamayı geliştirmek **için (****hatalı** pozitif) ve Bu gibi iletilere izin ver seçeneklerini yalnızca Güvenlik Yöneticileri rol grubunun üyeleri iletiyi **Microsoft'a gönder'i görebilir ve** kullanabilir. 

- ![E-postayı paylaş simgesi.](../../media/m365-cc-sc-share-email-icon.png) **E-postayı** paylaşma: Görüntülenen açılır iletide, iletinin bir kopyasını almak için bir veya birden çok alıcı ekleyin. Bitirdikten sonra Paylaş'a **tıklayın**.

Diğer eylemler simgesine tıklarsanız aşağıdaki ![eylemler kullanılabilir.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler**:

- ![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-view-message-headers-icon.png) **İleti üst bilgilerini görüntüleme**: İleti üst bilgisi metnini görmek için bu bağlantıyı seçin. İleti **üst bilgisi** açılır başlığı, aşağıdaki bağlantılarla birlikte görüntülenir:
  - **İleti üst bilginizi** kopyalayın: İleti üst bilgilerini (tüm üst bilgi alanları) panoya kopyalamak için bu bağlantıya tıklayın.
  - **Microsoft İleti Üst Bilgisi Çözümleyicisi**: Üstbilgi alanlarını ve değerlerini derinlemesine çözümlemek için, bu bağlantıya tıklayarak İleti Üst Bilgisi Çözümleyicisi'ne gidin. İleti üst bilgilerini Çözümlemek istediğiniz  ileti üst bilgilerini ekleme bölümüne yapıştırın (CTRL+V veya sağ tıklayın ve Yapıştır'ı **seçin) ve** ardından Üst bilgileri **çözümle'ye tıklayın**.

- ![İletiyi önizleme simgesi.](../../media/m365-cc-sc-preview-message-icon.png) **Önizleme iletisi**: Görüntülenen açılır listede, aşağıdaki sekmelerden birini seçin:
  - **Kaynak**: Tüm bağlantılar devre dışı bırakılmıştır ve ileti gövdesinin HTML sürümünü gösterir.
  - **Düz metin**: İleti gövdesini düz metin olarak gösterir.

- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen **uyarıda Evet'e** tıklarsanız, ileti özgün alıcılara gönderilmeden hemen silinir.

- ![İndir e-posta simgesi.](../../media/m365-cc-sc-download-icon.png) **E-postayı** indir: Görüntülenen açılır iletide, Bu iletiyi indirmenin risklerini anlıyorum öğesini seçin ve sonra da indir'e tıklayıp iletinin yerel bir kopyasını .eml biçiminde kaydedin.

- ![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png) **Göndereni** engelleme: Göndereni posta kutunuzda Engellenen Gönderenler **listesine** ekleyin. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png) **Yalnızca gönderin**: İletiyi çözümleme için Microsoft'a raporlar. Görüntülenen açılır listede aşağıdaki seçenekleri belirleyin:
  - **Gönderme türünü seçin**: **E-posta** (varsayılan), **URL** veya **Dosya**.
  - **Ağ iletisi kimliğini ekleyin veya e-posta dosyasını karşıya yükleyin**: Aşağıdaki seçeneklerden birini belirleyin:
    - **E-posta ağ iletisi kimliğini** ekleyin (varsayılan, kutuya karşılık gelen değerle birlikte)
    - **Upload-posta dosyasını (.msg veya eml)** kaydedin: Dosyaları bulmak  ve göndermek için .msg veya .eml ileti dosyasını seçmek için Dosyalara gözat'a tıklayın.
  - **Sorunu olan bir alıcı seçin**: Uygulanmış olan ilkeleri çözümlemek için iletinin bir (tercih edilen) veya daha fazla özgün alıcısı seçin.
  - **Microsoft'a gönderme için bir neden seçin**: Aşağıdaki seçeneklerden birini belirleyin:
    - **Engellenmiş olmalıdır (hatalı pozitif)** (varsayılan): Aşağıdaki seçenekler kullanılabilir:
      - **İletilere şu şekilde izin** ver: Bu seçenek varsayılan olarak kapalıdır (![Kapalı olarak geçiş).](../../media/scc-toggle-off.png) Benzer URL'lere, eklere](../../media/scc-toggle-on.png) ve diğer özelliklere sahip iletilerin karantinaya alınmasını geçici olarak önlemek için bu özelliği açın (![Aç/Aç). Bu seçeneği açık durumdayken aşağıdaki seçenekler kullanılabilir:
        - **Sonra kaldır**: Bunun gibi iletilere ne kadar süre izin vermek istediğiniz seçin. **1 gün ile** **30 gün arasında bir gün seçin**. Varsayılan değer 30'dır.
        - **İsteğe bağlı** not: İzin vermek için yararlı bir açıklama girin.
    - **Engellenmiş olması gerekir (yanlış negatif)**.

  Bitirdikten sonra Gönder'e **tıklayın**.

<sup>\*</sup> Bu seçenek, daha önce yayımlanan iletiler için kullanılamaz (Yayımlanan **durum** değeri Sürüm **tarihidir**).

İletiyi çıkartır veya kaldırsanız bile, varsayılan karantina bekletme süresinin süresi dolsa bile (Süre aşımına varıldı sütununda gösterildiği gibi) bu **ileti** silinir.

> [!NOTE]
> Mobil cihazda, eylem simgelerini açıklama metni kullanılamaz.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Kullanılabilir eylemler vurgulanmış olarak karantinaya alınmış iletinin ayrıntıları" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Simgeler ve bunların karşılık gelen açıklamaları aşağıdaki tabloda özetlenmiştir:
>
> |Simge|Açıklama|
> |---:|---|
> |![Sürüm e-postası simgesi.](../../media/m365-cc-sc-check-mark-icon.png)|**Sürüm e-postası**|
> |![E-postayı paylaş simgesi.](../../media/m365-cc-sc-share-email-icon.png)|**E-posta paylaşma**|
> |![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-view-message-headers-icon.png)|**İleti üst bilgilerini görüntüleme**|
> |![İletiyi önizleme simgesi.](../../media/m365-cc-sc-preview-message-icon.png)|**İletiyi önizleme**|
> |![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png)|**Karantinadan silme**|
> |![İndir e-posta simgesi.](../../media/m365-cc-sc-download-icon.png)|**İndirme e-postası**|
> |![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png)|**Göndereni engelle**|
> |![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png)|**Yalnızca gönder**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Birden çok karantinaya alınmış e-posta iletide eyleme geç

İlk sütunun sol tarafından boş bir alana tıklayarak listede birden çok karantinaya alınmış ileti (en çok 100) seçin; burada, aşağıdaki eylemleri gerçekleştirebilirsiniz:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Karantinada yer alan iletiler için Toplu eylemler açılan listesi" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Sürüm e-postası simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Sürüm iletileri**: İletileri tüm alıcılara yayımlar. Görüntülenen açılır listede, aşağıdaki seçenekleri kullanabilirsiniz; bu, tek bir iletiyi sürümle aynı olur:
  - **Göndereni kuruluşun izin listesine ekleme**
  - **Bu iletinin bir kopyasını diğer alıcılara gönder**
  - **Algılamayı geliştirmek için iletiyi Microsoft'a gönderin (hatalı pozitif)**
  - **Şöyle iletilere izin ver**:
    - **Sonra kaldır**: **1 gün** **- 30 gün**
    - **İsteğe bağlı not**

  Bitirdikten sonra İletiyi **bırak'a tıklayın**.

  > [!NOTE]
  > Aşağıdaki senaryoyu göz önünde john@gmail.com: Faith@contoso.com ve john@subsidiary.contoso.com. Gmail iki iletiyi, Microsoft'ta kimlik avı olarak karantinaya yönlendirilen iki kopyaya kopyalar. Yönetici, bu iletilerin her ikisini de admin@contoso.com. Yönetici posta kutusuna ulaşan ilk yayımlanan ileti teslim edilir. Yayımlanan ikinci ileti yinelenen teslim olarak tanımlanır ve atlanır. Aynı ileti kimliğine ve alınan süreye sahipse, ileti yinelenen ileti olarak tanımlanır.

- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **İletileri** silme: Görüntülenen **uyarıda Evet'e** tıklarsanız, iletiler özgün alıcılara gönderilmeden hemen karantinadan kaldırılır.
- ![İndir e-posta simgesi.](../../media/m365-cc-sc-download-icon.png) **İletileri indirme**
- ![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png) **Yalnızca gönder**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Microsoft 365 Defender portalında karantinaya alınmış dosyaları yönetmek için Office 365 için Defender

> [!NOTE]
> Bu bölümdeki karantinaya alınmış dosyalar için yordamlar yalnızca Plan 1 Office 365 için Microsoft Defender Plan 2 aboneleri tarafından kullanılabilir.

Office 365 için Defender'Office 365 için Defender olan kuruluşlarda, yöneticiler Kasa, SharePoint, OneDrive ve klasörlerin ekleri tarafından karantinaya Microsoft Teams. Bu dosyalar için korumayı etkinleştirmek için bkz. Kasa, [SharePoint, OneDrive ve](turn-on-mdo-for-spo-odb-and-teams.md) Microsoft Teams.

### <a name="view-quarantined-files"></a>Karantinaya alınmış dosyaları görüntüleme

1. Aşağıdaki Microsoft 365 Defender portalında E-posta Gönder <https://security.microsoft.com>ve işbirliğini **& Karantina'ya** \>  \> **gidin**. Doğrudan Karantina sayfasına **gitmek için** , kullanın <https://security.microsoft.com/quarantine>.

2. Karantina sayfasında **Dosyalar** sekmesini seçin **(****E-posta** varsayılan sekmedir).

3. Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz. Gösterilen **sütunları değiştirmek** için Sütunları özelleştir'e tıklayın. Varsayılan sütunlar bir yıldız işaretiyle () işaretlenir<sup>\*</sup>:
   - **Kullanıcı**<sup>\*</sup>
   - **Konum**<sup>\*</sup>
   - **Ek dosya adı**<sup>\*</sup>
   - **Dosya URL'si**<sup>\*</sup>
   - **Dosya Boyutu**
   - **Sürüm durumu**<sup>\*</sup>
   - **Son kullanma tarihi**<sup>\*</sup>
   - **Algılandı**
   - **Saate göre değiştirildi**

   Bitirdikten sonra Uygula'ya veya **İptal'e** **tıklayın**.

4. Sonuçları filtrelemek için Filtre'ye **tıklayın**. Görüntülenen Filtreler açılır yapısında **aşağıdaki** filtreler kullanılabilir:
   - **Alınan saat**: **Başlangıç saati** ve **Bitiş saati** (tarih).
   - **Son kullanma** tarihi: **Başlangıç saati** ve **Bitiş saati** (tarih).
   - **Karantina nedeni**: Kullanılabilir tek değer Kötü Amaçlı **Yazılım'dır**.
   - **İlke türü**

   Bitirdikten sonra Uygula'ya veya **İptal'e** **tıklayın**.

Belirli bir karantinaya alınmış dosyayı buktan sonra, dosyayla ilgili ayrıntıları görüntülemek ve bu dosya üzerinde işlem yapmak (örneğin, dosyayı görüntüleme, bırakma, indirme veya silme) için dosyayı seçin.

#### <a name="view-quarantined-file-details"></a>Karantinaya alınmış dosya ayrıntılarını görüntüleme

Listeden karantinaya alınmış bir dosya seçin, açılan ayrıntılar açılır listesinde aşağıdaki bilgiler kullanılabilir:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Karantinaya alınmış dosyanın ayrıntılar uçarak çıkış" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Dosya Adı**
- **Dosya URL'si**: Dosyanın konumunu tanımlayan URL (örneğin, SharePoint Online).
- **Algılandığında kötü amaçlı içerik** Dosyanın karantinaya alındığı tarih/saat.
- **Son kullanma** tarihi: Dosyanın karantinadan silinecektir.
- **Algılandı**
- **Yayımlanan?**
- **Kötü Amaçlı Yazılım Adı**
- **Belge Kimliği**: Belge için benzersiz bir tanımlayıcı.
- **Dosya Boyutu**: Kilobayt (KB) cinsinden.
- **Kuruluş** Kuruluş benzersiz kimliğidir.
- **Son değiştirme**
- **Değiştiren**: Dosyayı son değiştiren kullanıcı.
- **Güvenli Karma Algoritması 256 bit (SHA-256)** değeri: Bu karma değerini, dosyayı diğer itibarı depolarında veya ortamınız içinde başka konumlarda tanımlamak için kullanabilirsiniz.

Dosya üzerinde işlem yapmak için sonraki bölüme bakın.

> [!NOTE]
> Ayrıntılar bölmesinde kalmak, ancak üzerinde karantinaya alınmış dosyayı değiştirmek için, uç ilişkinin üst kısmında bulunan yukarı ve aşağı okları kullanın.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Karantinaya alınmış dosyaların ayrıntılarında yukarı ve aşağı oklar" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Karantinaya alınmış dosyalarda eyleme geç

Listeden karantinaya alınmış bir dosya seçdikten sonra, ayrıntılar ayrıntılarında şu eylemler kullanılabilir:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Karantinaya alınmış dosyanın ayrıntılarlarında yer alan eylemler" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Sürüm dosyası simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Sürüm dosyası**<sup>\*</sup>: Görüntülenen açılır bölmede Çözümleme için Dosyaları **Microsoft'a** bildir'i açın veya kapatın, ardından Sürüm'e **tıklayın**.
- ![Sürüm dosyası simgesi.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Dosya indir simgesi.](../../media/m365-cc-sc-download-icon.png) **Dosya indirme**: Görüntülenen açılır dosyada, Bu dosyayı indirmenin risklerini anlıyorum öğesini seçin ve ardından dosyanın yerel bir kopyasını  kaydetmek için İndir'e tıklayın.
- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen **uyarıda Evet'e** tıklarsanız, dosya hemen silinir.
- ![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png) **Göndereni** engelleme: Göndereni posta kutunuzda Engellenen Gönderenler **listesine** ekleyin. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Bu seçenek, daha önce yayımlanan dosyalarda kullanılamaz (Yayımlanan **durum** değeri Sürüm **tarihidir**).

Dosyayı çıkartır veya kaldırsanız bile, varsayılan karantina bekletme süresinin süresi dolsa bile (Süre aşımına varma sütununda gösterildiği gibi) bu **dosya** silinir.

#### <a name="take-action-on-multiple-quarantined-files"></a>Birden çok karantinaya alınmış dosyada eyleme geç

Konu sütununu sol boş alana tıklayarak listede birden çok karantinaya alınmış dosya (en çok 100) seçerek, aşağıdaki eylemleri gerçekleştirebilirsiniz Toplu  eylemler açılan listesi görüntülenir:

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Karantinada yer alan dosyalar için Toplu eylemler açılan listesi" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Sürüm dosyası simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Sürüm dosyası**: Görüntülenen açılır bölmede Çözümleme için Dosyaları **Microsoft'a** bildir'i açın veya kapatın, ardından Sürüm'e **tıklayın**.
- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen **uyarıda Evet'e** tıklarsanız, dosya hemen silinir.
- ![Dosya indir simgesi.](../../media/m365-cc-sc-download-icon.png) **Dosya indirme**: Görüntülenen açılır dosyada, Bu dosyayı indirmenin risklerini anlıyorum öğesini seçin ve ardından dosyanın yerel bir kopyasını  kaydetmek için İndir'e tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Karantinaya Exchange Online ve dosyaları görüntülemek ve yönetmek için PowerShell veya tek başına EOP PowerShell kullanma

Karantinada iletileri ve dosyaları görüntülemek ve yönetmek için kullanabileceğiniz cmdlet'ler aşağıdaki listede açıklanmıştır:

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): Bu cmdlet'in yalnızca iletilere ait olduğunu, Kasa, SharePoint, OneDrive ve klasörlerin eklerinden karantinaya Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Daha fazla bilgi için

[Karantinaya alınmış iletiler hakkında SSS](quarantine-faq.yml)
