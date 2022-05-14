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
description: Yöneticiler, Exchange Online Protection(EOP) içindeki tüm kullanıcılar için karantinaya alınan iletileri görüntülemeyi ve yönetmeyi öğrenebilir. Office 365 için Microsoft Defender sahip kuruluşlardaki yöneticiler, karantinaya alınan dosyaları SharePoint Online, OneDrive İş ve Microsoft Teams de yönetebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: df123916f5f15a8651ba8ad8dcbae95598afbfa8
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418072"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda karantina, potansiyel olarak tehlikeli veya istenmeyen iletileri barındırıyor. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan e-posta iletileri](quarantine-email-messages.md).

Yöneticiler tüm kullanıcılar için tüm karantinaya alınmış iletileri görüntüleyebilir, yayımlayabilir ve silebilir. Yöneticiler hatalı pozitif sonuçları Microsoft'a da bildirebilir.

Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım, yüksek güvenilirlikli kimlik avı veya posta akışı kuralları (aktarım kuralları olarak da bilinir) nedeniyle karantinaya alınan iletileri yönetebilir. Ancak yöneticiler _, karantinaya_ alınan iletilerin neden karantinaya alındığına (desteklenen özellikler için) bağlı olarak kullanıcıların karantinaya alınan iletilere ne yapmalarına izin verildiğini tanımlamak için karantina ilkelerini kullanabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

Office 365 için Microsoft Defender sahip kuruluşlardaki yöneticiler SharePoint[, OneDrive ve Microsoft Teams için Kasa Ekleri](mdo-for-spo-odb-and-teams.md) tarafından karantinaya alınan dosyaları da yönetebilir.

Karantinaya alınan iletileri Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online Exchange Online'da posta kutuları olan Microsoft 365 kuruluşlar için PowerShell'de; tek başına EOP PowerShell'de ve olmayan kuruluşlar için tek başına EOP PowerShell'de görüntüleyip yönetirsiniz Exchange Online posta kutuları).

Karantinaya alınan iletileri yönetici olarak yönetmeyi öğrenmek için bu kısa videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGGPF]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açmak için adresine <https://security.microsoft.com>gidin. Doğrudan **Karantina** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantine>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Tüm kullanıcılar için karantinaya alınan iletilerde işlem yapmak için **Kuruluş Yönetimi**, **Güvenlik Yöneticisi** veya **Karantina Yöneticisi**<sup>\*</sup> rol gruplarının üyesi olmanız gerekir. Microsoft'a ileti göndermek için **Güvenlik Yöneticisi** rol grubunun üyesi olmanız gerekir.
  - Tüm kullanıcılar için karantinaya alınan iletilere salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.
  - <sup>\*</sup>Microsoft 365 Defender [portalındaki](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) **E-posta & işbirliği** rollerindeki **Karantina Yöneticisi** rol grubunun üyelerinin de Exchange Online PowerShell'de karantina yordamları gerçekleştirmek için **Exchange Online'da Hijyen Yönetimi** rol grubunun üyesi olması [](/Exchange/permissions-exo/permissions-exo#role-groups) gerekir.

- Karantinaya alınan iletiler, neden karantinaya alındıklarına bağlı olarak varsayılan bir süre boyunca saklanır. Bekletme süresi dolduktan sonra iletiler otomatik olarak silinir ve kurtarılamaz. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan e-posta iletileri ve Office 365 için Defender](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Karantinaya alınan e-posta iletilerini yönetmek için Microsoft 365 Defender portalını kullanma

### <a name="view-quarantined-email"></a>Karantinaya alınan e-postayı görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **Karantinayı Gözden Geçir'e** \> gidin. Doğrudan **Karantina** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantine>.

2. **Karantina** sayfasında **, E-posta** sekmesinin seçili olduğunu doğrulayın.

3. Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz. Gösterilen sütunları değiştirmek için **Sütunları özelleştir'e**  tıklayın. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):

   - **Alınan süre**<sup>\*</sup>
   - **Konu**<sup>\*</sup>
   - **Gönderen**<sup>\*</sup>
   - **Karantina nedeni**<sup>\*</sup>
   - **Sürüm durumu**<sup>\*</sup>
   - **İlke türü**<sup>\*</sup>
   - **Sona eri -yor**<sup>\*</sup>
   - **Alıcı**
   - **İleti Kimliği**
   - **İlke adı**
   - **İleti boyutu**
   - **Posta yönü**
   - **Alıcı etiketi**

   İşiniz bittiğinde **Uygula'ya** tıklayın.

4. Sonuçları filtrelemek için **Filtrele'ye** tıklayın. Görüntülenen **Filtreler** açılır listesinde aşağıdaki filtreler bulunur:
   - **İleti Kimliği**: İletinin genel olarak benzersiz tanımlayıcısı.

     Örneğin, kuruluşunuzdaki bir kullanıcıya gönderilen iletiyi aramak için [ileti izlemesini](message-trace-scc.md) kullandınız ve iletinin teslim etmek yerine karantinaya alındığını belirlediniz. Açılı ayraçlar (\<\>) içerebilecek tam ileti kimliği değerini eklediğinizden emin olun. Örneğin: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Gönderen adresi**
   - **Alıcı adresi**
   - **Konu**
   - **Alınan saat**: **Başlangıç saati** ve **Bitiş saati** (tarih) girin.
   - **Süre sonu: İletilerin** süresi karantinadan ne zaman dolacaklarına göre filtreleyin:
     - **Bugün**
     - **Sonraki 2 gün**
     - **Sonraki 7 gün**
     - **Özel**: **Başlangıç saati** ve **Bitiş saati** (tarih) girin.
   - **Alıcı etiketi**
   - **Karantina nedeni**:
     - **Aktarım kuralı** (posta akışı kuralı)
     - **Toplu**
     - **Spam**
     - **Kötü amaçlı yazılım**: EOP'de kötü amaçlı yazılımdan koruma ilkeleri veya Office 365 için Defender ekleri ilkelerini Kasa. **İlke Türü** değeri hangi özelliğin kullanıldığını gösterir.
     - **Kimlik avı**: İstenmeyen posta filtresinin kararı **,** iletiyi (kimlik [sahtekarlığı ayarları](set-up-anti-phishing-policies.md#spoof-settings) veya [kimliğe bürünme koruması](kimlik avı önleme ilkelerini ayarlama) karantinaya alan Kimlik Avı veya kimlik avı korumasıdır.
     - **Yüksek güvenilirlikli kimlik avı**
   - **Alıcı**: **Tüm kullanıcılar** veya **Yalnızca ben**. Son kullanıcılar yalnızca kendilerine gönderilen karantinaya alınmış iletileri yönetebilir.
   - **Sürüm durumu**: Aşağıdaki değerlerden herhangi biri:
     - **Gözden geçirilmesi gerekiyor**
     - **Onaylı**
     - **Redd -edildi**
     - **Sürüm istendi**
     - **Yayım -lanan**
   - **İlke Türü**: İletileri ilke türüne göre filtreleyin:
     - **Kötü amaçlı yazılımdan koruma ilkesi**
     - **Kasa Ekler ilkesi**
     - **Kimlik avı önleme ilkesi**
     - **İstenmeyen posta önleme ilkesi**
     - **Aktarım kuralı** (posta akışı kuralı)

   İşiniz bittiğinde **Uygula'ya** tıklayın. Filtreleri temizlemek için Filtreleri temizle simgesine tıklayın ![.](../../media/m365-cc-sc-clear-filters-icon.png) **Filtreleri temizleyin**.

5. Belirli iletileri bulmak için **Arama** kutusunu ve ilgili değeri kullanın. Joker karakterler desteklenmez. Aşağıdaki değerlere göre arama yapabilirsiniz:
   - Gönderen e-posta adresi
   - Konu. İletinin tüm konusunu kullanın. Arama büyük/küçük harfe duyarlı değildir.

   Arama ölçütlerini girdikten sonra sonuçları filtrelemek için ENTER tuşuna basın.

Karantinaya alınmış belirli bir iletiyi buldukktan sonra, iletinin ayrıntılarını görüntülemek ve bu ileti üzerinde işlem yapmak için iletiyi seçin (örneğin, iletiyi görüntüleme, yayınlama, indirme veya silme).

#### <a name="view-quarantined-message-details"></a>Karantinaya alınan ileti ayrıntılarını görüntüleme

Listeden karantinaya alınmış iletiyi seçtiğinizde, görüntülenen ayrıntılar açılır öğesinde aşağıdaki bilgiler bulunur.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Karantinaya alınan iletinin ayrıntılar açılır öğesi" lightbox="../../media/quarantine-message-details-flyout.png":::

- **İleti Kimliği: İletinin** genel olarak benzersiz tanımlayıcısı. İleti üst bilgisindeki **İleti Kimliği** üst bilgisi alanında kullanılabilir.
- **Gönderen adresi**
- **Alındı**: İletinin alındığı tarih/saat.
- **Konu**
- **Karantina nedeni**: bir iletinin **İstenmeyen Posta**, **Toplu**, **Kimlik Avı** olarak tanımlandığını, posta akışı kuralıyla (**Aktarım kuralı**) eşleşip eşleşmediğini veya **Kötü Amaçlı Yazılım** içerdiğinin belirlenip tanımlanmadığını gösterir.
- **İlke türü**
- **İlke adı**
- **Alıcı sayısı**
- **Alıcılar**: İleti birden çok alıcı içeriyorsa, alıcı listesinin tamamını görmek için **İletiyi önizleme** veya **İleti üst bilgisini görüntüle'ye** tıklamanız gerekir.
- **Alıcı etiketi**: Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender kullanıcı etiketleri](user-tags.md).
- **Süre sonu**: İletinin otomatik olarak silineceği ve karantinadan kalıcı olarak silineceği tarih/saat.
- **Yayın tarihi**: İletinin yayımlandığı tüm e-posta adresleri (varsa).
- **Henüz yayımlanmadı**: İletinin henüz yayımlanmadığı tüm e-posta adresleri (varsa).

İleti üzerinde işlem yapmak için sonraki bölüme bakın.

> [!NOTE]
> Ayrıntılar açılır öğesinde kalmak, ancak baktığınız karantinaya alınmış iletiyi değiştirmek için açılır listenin üst kısmındaki yukarı ve aşağı okları kullanın.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Karantinaya alınan iletinin ayrıntılar açılır öğesindeki yukarı ve aşağı oklar" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Karantinaya alınan e-postada işlem gerçekleştirme

Listeden karantinaya alınmış bir iletiyi seçtikten sonra, ayrıntılar açılır öğesinde aşağıdaki eylemler kullanılabilir:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="Karantinaya alınan iletinin ayrıntılar açılır öğesindeki Kullanılabilir eylemler" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![E-postayı serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın e-postası**<sup>\*</sup>: Görüntülenen açılır bölmede aşağıdaki seçenekleri yapılandırın:
  - **Kuruluşunuzun izin verme listesine gönderen ekleme**: Gönderenden gelen iletilerin karantinaya alınmasını önlemek için bu seçeneği belirleyin.
  - Aşağıdaki seçeneklerden birini belirleyin:
    - **Tüm alıcılara serbest bırakma**
    - **Belirli alıcılara bırakın**: Görüntülenen **Alıcılar kutusunda alıcıları** seçin
  - **Bu iletinin bir kopyasını diğer alıcılara gönder**: Bu seçeneği belirleyin ve görüntülenen **Alıcılar** kutusuna alıcı e-posta adreslerini girin.

    > [!NOTE]
    > İletinin bir kopyasını diğer alıcılara göndermek için, iletiyi özgün alıcılardan en az birini de serbest bırakmanız gerekir ( **Tüm alıcılara bırak** veya **Belirli alıcılara bırak'ı** seçin).

  - **Algılamayı geliştirmek için iletiyi Microsoft'a gönderin (hatalı pozitif)**: Bu seçenek varsayılan olarak seçilidir ve hatalı bir şekilde karantinaya alınan iletiyi Hatalı pozitif olarak Microsoft'a bildirir. İleti istenmeyen posta, toplu, kimlik avı veya kötü amaçlı yazılım içeren olarak karantinaya alındıysa, ileti Microsoft İstenmeyen Posta Çözümleme Ekibi'ne de bildirilir. Analiz sonuçlarına bağlı olarak, hizmet genelinde istenmeyen posta filtresi kuralları iletinin geçmesine izin verecek şekilde ayarlanabilir.

  - **Bunun gibi iletilere izin ver**: Bu seçenek varsayılan olarak kapalıdır (![İki durumlu düğme kapalıdır).](../../media/scc-toggle-off.png)) Benzer URL'lere, eklere ve diğer özelliklere sahip iletilerin karantinaya alınmasını geçici olarak önlemek için açın (![Açık konuma getirin](../../media/scc-toggle-on.png)). Bu seçeneği açtığınızda, aşağıdaki seçenekler kullanılabilir:
    - **Daha sonra kaldır**: Bu tür iletilere ne kadar süre izin vermek istediğinizi seçin. **1 gün** ile **30 gün** arasını seçin. Varsayılan değer 30'dur.
    - **İsteğe bağlı not**: İzin ver için yararlı bir açıklama girin.

  İşiniz bittiğinde **, İletiyi serbest bırak'a** tıklayın.

  İletileri yayımlama hakkında notlar:

  - İletiyi aynı alıcıya birden çok kez yayımlayamazsınız.
  - Olası alıcılar listesinde yalnızca iletiyi almayan alıcılar görüntülenir.
  - **Algılamayı geliştirmek için iletiyi Microsoft'a gönder (hatalı pozitif)** ve **Bu seçenekler gibi iletilere izin ver'i** yalnızca **Güvenlik Yöneticileri** rol grubunun üyeleri görebilir ve kullanabilir. 

- ![E-posta paylaş simgesi.](../../media/m365-cc-sc-share-email-icon.png) **E-posta paylaşma**: Görüntülenen açılır öğeye iletinin bir kopyasını almak için bir veya daha fazla alıcı ekleyin. İşiniz bittiğinde **Paylaş'a** tıklayın.

Diğer eylemler simgesine tıkladıktan ![sonra aşağıdaki eylemler kullanılabilir.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler**:

- ![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-view-message-headers-icon.png) **İleti üst bilgilerini görüntüle: İleti** üst bilgisi metnini görmek için bu bağlantıyı seçin. **İleti üst bilgisi** açılır öğesi aşağıdaki bağlantılarla görüntülenir:
  - **İleti üst bilgisini kopyala**: İleti üst bilgisini (tüm üst bilgi alanları) panonuza kopyalamak için bu bağlantıya tıklayın.
  - **Microsoft İleti Üst Bilgisi Çözümleyicisi**: Üst bilgi alanlarını ve değerlerini derinlemesine çözümlemek için bu bağlantıya tıklayarak İleti Üst Bilgisi Çözümleyicisi'ne gidin. çözümlemek **istediğiniz ileti üst bilgisini ekleme** bölümüne ileti üst bilgisini yapıştırın (CTRL+V veya sağ tıklayıp **Yapıştır'ı** seçin) ve ardından **Üst bilgileri çözümle'ye** tıklayın.

- ![önizleme iletisi simgesi.](../../media/m365-cc-sc-preview-message-icon.png) **Önizleme iletisi**: Görüntülenen açılır öğede aşağıdaki sekmelerden birini seçin:
  - **Kaynak**: tüm bağlantılar devre dışı bırakılmış olarak ileti gövdesinin HTML sürümünü gösterir.
  - **Düz metin**: İleti gövdesini düz metin olarak gösterir.

- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra, ileti özgün alıcılara gönderilmeden hemen silinir.

- ![E-posta simgesini indirin.](../../media/m365-cc-sc-download-icon.png) **E-postayı indir**: Görüntülenen açılır menüde **, Bu iletiyi indirmenin risklerini anlıyorum'ı** seçin ve ardından **İndir'e** tıklayarak iletinin yerel bir kopyasını .eml biçiminde kaydedin.

- ![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png) **Göndereni engelle**: Göndereni **posta** kutunuzdaki Engellenen Gönderenler listesine ekleyin. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png) **Yalnızca gönder**: İletiyi analiz için Microsoft'a bildirir. Görüntülenen açılır öğede aşağıdaki seçenekleri belirleyin:
  - **Gönderme türünü seçin**: **E-posta** (varsayılan), **URL** veya **Dosya**.
  - **Ağ iletisi kimliğini ekleyin veya e-posta dosyasını karşıya yükleyin**: Aşağıdaki seçeneklerden birini seçin:
    - **E-posta ağ ileti kimliğini ekleyin** (varsayılan olarak, kutuda karşılık gelen değer bulunur)
    - **E-posta dosyasını (.msg veya eml) Upload**: Göndermek üzere .msg veya .eml ileti dosyasını bulmak ve seçmek için **Dosyalara gözat'a** tıklayın.
  - **Sorun yaşayan bir alıcı seçin**: İletiye uygulanan ilkeleri analiz etmek için iletinin bir (tercih edilen) veya daha fazla özgün alıcısını seçin.
  - **Microsoft'a göndermek için bir neden seçin**: Aşağıdaki seçeneklerden birini belirleyin:
    - **Engellenmemesi gerekir (hatalı pozitif)** (varsayılan): Aşağıdaki seçenekler kullanılabilir:
      - **Bunun gibi iletilere izin ver**: Bu seçenek varsayılan olarak kapalıdır (![İki durumlu düğme kapalıdır).](../../media/scc-toggle-off.png)) Benzer URL'lere, eklere ve diğer özelliklere sahip iletilerin karantinaya alınmasını geçici olarak önlemek için açın (![Açık konuma getirin](../../media/scc-toggle-on.png)). Bu seçeneği açtığınızda, aşağıdaki seçenekler kullanılabilir:
        - **Daha sonra kaldır**: Bu tür iletilere ne kadar süre izin vermek istediğinizi seçin. **1 gün** ile **30 gün** arasını seçin. Varsayılan değer 30'dur.
        - **İsteğe bağlı not**: İzin ver için yararlı bir açıklama girin.
    - **Engellenmiş olmalıdır (hatalı negatif)**.

  İşiniz bittiğinde **Gönder'e** tıklayın.

<sup>\*</sup> Bu seçenek, daha önce yayımlanmış olan iletiler için kullanılamaz ( **Serbest bırakıldı durum** değeri **Serbest Bırakıldı'dır**).

İletiyi serbest bırakmaz veya kaldırmazsanız, varsayılan karantina bekletme süresi dolduktan sonra silinir ( **Süre sonu** sütununda gösterildiği gibi).

> [!NOTE]
> Mobil cihazda açıklama metni eylem simgelerinde kullanılamaz.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Kullanılabilir eylemlerin vurgulandığı karantinaya alınmış bir iletinin ayrıntıları" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Sırayla simgeler ve karşılık gelen açıklamaları aşağıdaki tabloda özetlenir:
>
> |Simge|Açıklama|
> |---:|---|
> |![E-postayı serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png)|**E-postayı serbest bırakma**|
> |![E-posta paylaş simgesi.](../../media/m365-cc-sc-share-email-icon.png)|**E-posta paylaşma**|
> |![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-view-message-headers-icon.png)|**İleti üst bilgilerini görüntüleme**|
> |![önizleme iletisi simgesi.](../../media/m365-cc-sc-preview-message-icon.png)|**önizleme iletisi**|
> |![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png)|**Karantinadan sil**|
> |![E-posta simgesini indirin.](../../media/m365-cc-sc-download-icon.png)|**E-postayı indirme**|
> |![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png)|**Göndereni engelle**|
> |![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png)|**Yalnızca gönder**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Karantinaya alınan birden çok e-posta iletisinde işlem gerçekleştirme

İlk sütunun solundaki boş alana tıklayarak listeden (en fazla 100) birden çok karantinaya alınmış ileti seçtiğinizde, aşağıdaki eylemleri gerçekleştirebileceğiniz **Toplu eylemler** açılan listesi görüntülenir:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Karantinadaki iletiler için Toplu eylemler açılan listesi" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![E-postayı serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın iletileri**: İletileri tüm alıcılara yayınlar. Görüntülenen açılır öğede, tek bir iletiyi serbest bıraktığınızda aynı olan aşağıdaki seçenekleri belirleyebilirsiniz:
  - **Kuruluşunuzun izin verme listesine gönderen ekleme**
  - **Bu iletinin bir kopyasını diğer alıcılara gönder**
  - **Algılamayı geliştirmek için iletiyi Microsoft'a gönderin (hatalı pozitif)**
  - **Aşağıdaki gibi iletilere izin ver**:
    - **Daha sonra kaldır**: **1 gün** ile **30 gün**
    - **İsteğe bağlı not**

  İşiniz bittiğinde **, İletiyi serbest bırak'a** tıklayın.

  > [!NOTE]
  > Aşağıdaki senaryoyu göz önünde bulundurun: john@gmail.com faith@contoso.com ve john@subsidiary.contoso.com bir ileti gönderir. Gmail bu iletiyi, Microsoft'ta kimlik avı olarak karantinaya yönlendirilen iki kopyaya ayırır. Yönetici bu iletilerin ikisini de admin@contoso.com yayınlar. Yönetici posta kutusuna ulaşan ilk yayımlanan ileti teslim edilir. yayımlanan ikinci ileti yinelenen teslim olarak tanımlanır ve atlanır. İleti, aynı ileti kimliğine ve alma zamanına sahipse yinelenenler olarak tanımlanır.

- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **İletileri silme**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra, iletiler özgün alıcılara gönderilmeden karantinadan hemen kaldırılır.
- ![E-posta simgesini indirin.](../../media/m365-cc-sc-download-icon.png) **İletileri indirme**
- ![Yalnızca gönder simgesi.](../../media/m365-cc-sc-create-icon.png) **Yalnızca gönder**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Office 365 için Defender'de karantinaya alınan dosyaları yönetmek için Microsoft 365 Defender portalını kullanma

> [!NOTE]
> Bu bölümdeki karantinaya alınan dosyalara yönelik yordamlar yalnızca Plan 1 veya Plan 2 abonelerine Office 365 için Microsoft Defender kullanılabilir.

Office 365 için Defender olan kuruluşlarda yöneticiler, SharePoint, OneDrive ve Microsoft Teams için Kasa Ekleri tarafından karantinaya alınan dosyaları yönetebilir. Bu dosyalar için korumayı etkinleştirmek için bkz[. SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açma](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Karantinaya alınan dosyaları görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **Karantinayı Gözden Geçir'e** \> gidin. Doğrudan **Karantina** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantine>.

2. **Karantina** sayfasında **Dosyalar** sekmesini seçin (**E-posta** varsayılan sekmedir).

3. Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz. Gösterilen sütunları değiştirmek için **Sütunları özelleştir'e** tıklayın. Varsayılan sütunlar yıldız işaretiyle (<sup>\*</sup>):
   - **Kullanıcı**<sup>\*</sup>
   - **Konum**<sup>\*</sup>
   - **Ek dosya adı**<sup>\*</sup>
   - **Dosya URL'si**<sup>\*</sup>
   - **Dosya Boyutu**
   - **Sürüm durumu**<sup>\*</sup>
   - **Sona eri -yor**<sup>\*</sup>
   - **Algılanan:**
   - **Zamana göre değiştirildi**

   İşiniz bittiğinde **Uygula** veya **İptal'e** tıklayın.

4. Sonuçları filtrelemek için **Filtrele'ye** tıklayın. Görüntülenen **Filtreler** açılır listesinde aşağıdaki filtreler bulunur:
   - **Alınan süre**: **Başlangıç saati** ve **Bitiş saati** (tarih).
   - **Süre sonu**: **Başlangıç saati** ve **Bitiş saati** (tarih).
   - **Karantina nedeni**: Kullanılabilir tek değer **Kötü Amaçlı Yazılımdır**.
   - **İlke türü**

   İşiniz bittiğinde **Uygula** veya **İptal'e** tıklayın.

Belirli bir karantinaya alınmış dosyayı buldukktan sonra, dosyayla ilgili ayrıntıları görüntülemek ve üzerinde işlem yapmak için dosyayı seçin (örneğin, dosyayı görüntüleme, bırakma, indirme veya silme).

#### <a name="view-quarantined-file-details"></a>Karantinaya alınan dosya ayrıntılarını görüntüleme

Listeden karantinaya alınmış bir dosya seçtiğinizde, açılan ayrıntılar açılır öğesinde aşağıdaki bilgiler bulunur:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Karantinaya alınan bir dosyanın ayrıntılar açılır öğesi" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Dosya Adı**
- **Dosya URL'si**: Dosyanın konumunu tanımlayan URL (örneğin, SharePoint Online).
- **Üzerinde kötü amaçlı içerik algılandı** Dosyanın karantinaya alındığı tarih/saat.
- **Süre sonu**: Dosyanın karantinadan silineceği tarih.
- **Algılanan:**
- **Yayım -lanan?**
- **Kötü Amaçlı Yazılım Adı**
- **Belge Kimliği: Belge** için benzersiz bir tanımlayıcı.
- **Dosya Boyutu**: Kilobayt (KB) cinsinden.
- **Organizasyon** Kuruluşunuzun benzersiz kimliği.
- **Son değiştirme**
- **Değiştiren**: Dosyayı son değiştiren kullanıcı.
- **Güvenli Karma Algoritması 256 bit (SHA-256) değeri**: Bu karma değeri kullanarak dosyayı diğer saygınlık depolarında veya ortamınızdaki diğer konumlarda tanımlayabilirsiniz.

Dosya üzerinde işlem yapmak için sonraki bölüme bakın.

> [!NOTE]
> Ayrıntılar açılır öğesinde kalmak, ancak baktığınız karantinaya alınmış dosyayı değiştirmek için açılır listenin üst kısmındaki yukarı ve aşağı okları kullanın.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Karantinaya alınan dosyaların ayrıntılar açılır öğesindeki yukarı ve aşağı oklar" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Karantinaya alınan dosyalarda işlem gerçekleştirme

Listeden karantinaya alınmış bir dosyayı seçtikten sonra ayrıntılar açılır listesinde aşağıdaki eylemler kullanılabilir:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Karantinaya alınmış bir dosyanın ayrıntılar açılır öğesindeki eylemler" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Dosya serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın dosyası**<sup>\*</sup>: Görüntülenen açılır bölmede, **Analiz için Rapor dosyalarını Microsoft'a** açın veya kapatın ve ardından **Serbest Bırak'a** tıklayın.
- ![Dosya serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Dosya indir simgesi.](../../media/m365-cc-sc-download-icon.png) **Dosyayı indir**: Görüntülenen açılır menüde **, Bu dosyayı indirmenin risklerini anlıyorum'ı** seçin ve dosyanın yerel bir kopyasını kaydetmek için **İndir'e** tıklayın.
- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra dosya hemen silinir.
- ![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png) **Göndereni engelle**: Göndereni **posta** kutunuzdaki Engellenen Gönderenler listesine ekleyin. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Bu seçenek, daha önce yayımlanmış olan dosyalar için kullanılamaz ( **Yayımlanan durum** değeri **Yayınlandı'dır**).

Dosyayı serbest bırakmaz veya kaldırmazsanız, varsayılan karantina bekletme süresi dolduktan sonra silinir ( **Süre sonu** sütununda gösterildiği gibi).

#### <a name="take-action-on-multiple-quarantined-files"></a>Karantinaya alınan birden çok dosya üzerinde eylem gerçekleştirme

**Konu** sütununun solundaki boş alana tıklayarak listeden (en fazla 100) karantinaya alınmış birden çok dosya seçtiğinizde, aşağıdaki eylemleri gerçekleştirebileceğiniz **Toplu eylemler** açılan listesi görüntülenir:

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Karantinadaki dosyalar için Toplu eylemler açılan listesi" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Dosya serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın dosyası**: Görüntülenen açılır bölmede, **Analiz için Rapor dosyalarını Microsoft'a** açın veya kapatın ve ardından **Serbest Bırak'a** tıklayın.
- ![Karantinadan sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan sil**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra dosya hemen silinir.
- ![Dosya indir simgesi.](../../media/m365-cc-sc-download-icon.png) **Dosyayı indir**: Görüntülenen açılır menüde **, Bu dosyayı indirmenin risklerini anlıyorum'ı** seçin ve dosyanın yerel bir kopyasını kaydetmek için **İndir'e** tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Karantinaya alınan iletileri ve dosyaları görüntülemek ve yönetmek için Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Karantinadaki iletileri ve dosyaları görüntülemek ve yönetmek için kullandığınız cmdlet'ler aşağıdaki listede açıklanmıştır:

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): Bu cmdlet'in yalnızca iletiler için olduğunu, SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerindeki karantinaya alınmış dosyalara yönelik olmadığını unutmayın.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Daha fazla bilgi için

[Karantinaya alınan iletiler hakkında SSS](quarantine-faq.yml)
