---
title: Kullanıcı olarak karantinaya alınan iletileri bulma ve serbest bırakma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Consumer/IW
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Kullanıcılar, kendilerine teslim edilmesi gereken Exchange Online Protection (EOP) içinde karantinaya alınan iletileri görüntülemeyi ve yönetmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
adobe-target: true
ms.openlocfilehash: 845e72f2cf3eeb97d7d5f90224967a4fe5068cf1
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607685"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Karantinaya alınan iletileri EOP'de kullanıcı olarak bulma ve bırakma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

posta kutuları olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları Exchange Online olan Microsoft 365 kuruluşlarında karantina, potansiyel olarak tehlikeli veya istenmeyen iletileri barındırıyor. Daha fazla bilgi için bkz. [EOP'de karantinaya alma](quarantine-email-messages.md).

Normal bir kullanıcı (yönetici değil) olarak, karantinaya alınmış bir iletinin alıcısı olarak kullanabileceğiniz **varsayılan** özellikler aşağıdaki tabloda açıklanmıştır:

|Karantina nedeni|Görünüm|Sürüm|Silme|
|---|:---:|:---:|:---:|
|**İstenmeyen posta önleme ilkeleri**||||
|Toplu|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Spam|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Yüksek güvenilirlikli istenmeyen posta|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Kimlik Avı|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Yüksek güvenilirlikli kimlik avı||||
|**Kimlik avından koruma ilkeleri**||||
|EOP'de kimlik sahtekarlığına karşı koruma|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Office 365 için Defender'de kimliğine bürünülen kullanıcı koruması|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Office 365 için Defender'de kimliğine bürünülen etki alanı koruması|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Office 365 için Defender'da posta kutusu zekası koruması|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Kötü amaçlı yazılımdan koruma ilkeleri**||||
|Kötü amaçlı yazılım olarak karantinaya alınan ekleri içeren e-posta iletileri.||||
|**Office 365 için Defender'da Güvenli Ekler**||||
|Kötü amaçlı ekler içeren e-posta iletilerini kötü amaçlı yazılım olarak karantinaya veren Güvenli Ekler ilkeleri.||||
|Kötü amaçlı dosyaları kötü amaçlı yazılım olarak karantinaya alan SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekler.||||
|**Posta akışı kuralları (aktarım kuralları)**||||
|E-posta iletilerini karantinaya veren posta akışı kuralları.||||

_Karantina ilkeleri_ , kullanıcıların [, iletinin desteklenen özelliklerde](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) neden karantinaya alındığına bağlı olarak karantinaya alınan iletilere ne yapmalarına izin verildiğini tanımlar. Varsayılan karantina ilkeleri, önceki tabloda açıklandığı gibi geçmiş özellikleri zorunlu kılmaktadır. Yöneticiler, desteklenen özelliklerdeki kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve uygulayabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

Karantinaya alınan iletilerinizi Microsoft 365 Defender portalında veya (yönetici bunu ayarladıysa) karantina ilkelerinden karantina bildirimlerini görüntüleyip yönetirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açmak için adresine <https://security.microsoft.com>gidin. Doğrudan **Karantina** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantine>.

- Yöneticiler, iletilerin istenmeyen posta önleme ilkelerinde kalıcı olarak silinmeden önce ne kadar süreyle karantinada tutulabileceğini yapılandırabilir. Karantina süresi dolan iletiler kurtarılamaz. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

- Varsayılan olarak, yüksek güvenilirlikli kimlik avı, kötü amaçlı yazılım veya posta akışı kurallarıyla karantinaya alınan iletiler yalnızca yöneticiler tarafından kullanılabilir ve kullanıcılar tarafından görünmez. Daha fazla bilgi için bkz. [Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme](manage-quarantined-messages-and-files.md).

## <a name="view-your-quarantined-messages"></a>Karantinaya alınan iletilerinizi görüntüleme

> [!NOTE]
> Karantinaya alınan iletileri görüntüleme olanağınız [, karantinaya](quarantine-policies.md) alınan ileti türüne (karantina [nedeniyle varsayılan karantina ilkesi](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) olabilir) uygulanan karantina ilkesi tarafından denetlenmektedir.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **Karantinayı Gözden Geçir'e** \> gidin. Doğrudan **Karantina** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantine>.

2. **Karantina** sayfasında, kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz. Gösterilen sütunları değiştirmek için **Sütunları özelleştir'e**  tıklayın. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):

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

   İşiniz bittiğinde **Uygula'ya** tıklayın.

3. Sonuçları filtrelemek için **Filtrele'ye** tıklayın. Görüntülenen **Filtreler** açılır listesinde aşağıdaki filtreler bulunur:
   - **İleti Kimliği**: İletinin genel olarak benzersiz tanımlayıcısı.
   - **Gönderen adresi**
   - **Alıcı adresi**
   - **Konu**
   - **Alınan saat**: **Başlangıç saati** ve **Bitiş saati** (tarih) girin.
   - **Süre sonu: İletilerin** süresi karantinadan ne zaman dolacaklarına göre filtreleyin:
     - **Bugün**
     - **Sonraki 2 gün**
     - **Sonraki 7 gün**
     - **Özel**: **Başlangıç saati** ve **Bitiş saati** (tarih) girin.
   - **Karantina nedeni**:
     - **Toplu**
     - **Spam**
     - **Kimlik avı**: İstenmeyen posta filtresi kararı **Kimlik avı** veya kimlik avı önleme koruması iletiyi karantinaya aldı ([kimlik sahtekarlığı ayarları](set-up-anti-phishing-policies.md#spoof-settings) veya [kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Yüksek güvenilirlikli kimlik avı**
   - **Sürüm durumu**: Aşağıdaki değerlerden herhangi biri:
     - **Gözden geçirilmesi gerekiyor**
     - **Onaylı**
     - **Redd -edildi**
     - **Sürüm istendi**
     - **Yayım -lanan**
   - **İlke Türü**: İletileri ilke türüne göre filtreleyin:
     - **Kötü amaçlı yazılımdan koruma ilkesi**
     - **Güvenli Ekler ilkesi**
     - **Kimlik avı önleme ilkesi**
     - **İstenmeyen posta önleme ilkesi**

   İşiniz bittiğinde **Uygula'ya** tıklayın. Filtreleri temizlemek için Filtreleri temizle simgesine tıklayın ![.](../../media/m365-cc-sc-clear-filters-icon.png) **Filtreleri temizleyin**.

4. Belirli iletileri bulmak için **Arama** kutusunu ve ilgili değeri kullanın. Joker karakterler desteklenmez. Aşağıdaki değerlere göre arama yapabilirsiniz:
   - İleti Kimliği
   - Gönderen e-posta adresi
   - Alıcı e-posta adresi
   - Konu. İletinin tüm konusunu kullanın. Arama büyük/küçük harfe duyarlı değildir.
   - İlke adı. İlke adının tamamını kullanın. Arama büyük/küçük harfe duyarlı değildir.

   Arama ölçütlerini girdikten sonra sonuçları filtrelemek için ENTER tuşuna basın.

   > [!NOTE]
   > Ana **Karantina** sayfasındaki **Arama** kutusu yalnızca geçerli görünümde karantinaya alınan öğeleri arar, karantinanın tamamını aramaz. Karantinaya alınan tüm öğeleri aramak için **Filtre'yi** ve sonuçta elde edilen **Filtreler** açılır öğesini kullanın.

Karantinaya alınmış belirli bir iletiyi buldukktan sonra, iletinin ayrıntılarını görüntülemek ve bu ileti üzerinde işlem yapmak için iletiyi seçin (örneğin, iletiyi görüntüleme, yayınlama, indirme veya silme).


### <a name="view-quarantined-message-details"></a>Karantinaya alınan ileti ayrıntılarını görüntüleme

Listeden karantinaya alınmış iletiyi seçtiğinizde, görüntülenen ayrıntılar açılır öğesinde aşağıdaki bilgiler bulunur.

:::image type="content" source="../../media/quarantine-user-message-details.png" alt-text="Karantinaya alınan iletinin ayrıntılar açılır öğesi" lightbox="../../media/quarantine-user-message-details.png":::

Listeden bir e-posta iletisi seçtiğinizde, **Ayrıntılar** açılır bölmesinde aşağıdaki ileti ayrıntıları görüntülenir:

- **İleti Kimliği: İletinin** genel olarak benzersiz tanımlayıcısı.
- **Gönderen adresi**
- **Alındı**: İletinin alındığı tarih/saat.
- **Konu**
- **Karantina nedeni**
- **İlke türü**: İlke türü. Örneğin, **İstenmeyen posta önleme ilkesi**.
- **Alıcı sayısı**
- **Alıcılar**: İleti birden çok alıcı içeriyorsa, alıcı listesinin tamamını görmek için **İletiyi önizleme** veya **İleti üst bilgisini görüntüle'ye** tıklamanız gerekir.
- **Süre sonu**: İletinin otomatik olarak silineceği ve karantinadan kalıcı olarak silineceği tarih/saat.

İleti üzerinde işlem yapmak için sonraki bölüme bakın.

> [!NOTE]
> Ayrıntılar açılır öğesinde kalmak, ancak baktığınız karantinaya alınmış iletiyi değiştirmek için açılır listenin üst kısmındaki yukarı ve aşağı okları kullanın.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Karantinaya alınan iletinin ayrıntılar açılır öğesindeki yukarı ve aşağı oklar" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Karantinaya alınan e-postada işlem gerçekleştirme

> [!NOTE]
> Karantinaya alınan iletilerde eylem gerçekleştirme olanağınız, [karantinaya](quarantine-policies.md) alınan ileti türüne (karantina [nedeniyle varsayılan karantina ilkesi](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) olabilir) uygulanan karantina ilkesi tarafından denetlenmektedir. Bu bölümde tüm kullanılabilir eylemler açıklanmaktadır.

Listeden karantinaya alınmış bir iletiyi seçtikten sonra, ayrıntılar açılır öğesinde aşağıdaki eylemler kullanılabilir:

:::image type="content" source="../../media/quarantine-user-message-details-flyout-actions.png" alt-text="Karantinaya alınmış bir iletinin ayrıntılar açılır öğesindeki kullanılabilir eylemler" lightbox="../../media/quarantine-user-message-details-flyout-actions.png":::

- ![E-postayı serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın e-postası**<sup>\*</sup>: İletiyi Gelen Kutunuza teslim eder.

- ![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-eye-icon.png) **İleti üst bilgilerini görüntüle: İleti** üst bilgisi metnini görmek için bu bağlantıyı seçin. **İleti üst bilgisi** açılır öğesi aşağıdaki bağlantılarla görüntülenir:
- **İleti üst bilgisini kopyala**: İleti üst bilgisini (tüm üst bilgi alanları) panonuza kopyalamak için bu bağlantıya tıklayın.
- **Microsoft İleti Üst Bilgisi Çözümleyicisi**: Üst bilgi alanlarını ve değerlerini derinlemesine çözümlemek için bu bağlantıya tıklayarak İleti Üst Bilgisi Çözümleyicisi'ne gidin. çözümlemek **istediğiniz ileti üst bilgisini ekleme** bölümüne ileti üst bilgisini yapıştırın (CTRL+V veya sağ tıklayıp **Yapıştır'ı** seçin) ve ardından **Üst bilgileri çözümle'ye** tıklayın.

Diğer eylemler simgesine tıkladıktan ![sonra aşağıdaki eylemler kullanılabilir.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler**:

- ![önizleme iletisi simgesi.](../../media/m365-cc-sc-eye-icon.png) **Önizleme iletisi**: Görüntülenen açılır öğede aşağıdaki sekmelerden birini seçin:
  - **Kaynak**: tüm bağlantılar devre dışı bırakılmış olarak ileti gövdesinin HTML sürümünü gösterir.
  - **Düz metin**: İleti gövdesini düz metin olarak gösterir.

- ![Karantinadan kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png) **Karantinadan kaldır**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra, ileti özgün alıcılara gönderilmeden hemen silinir.

- ![E-posta simgesini indirin.](../../media/m365-cc-sc-download-icon.png) **E-postayı indir**: Görüntülenen açılır menüde **, Bu iletiyi indirmenin risklerini anlıyorum'ı** seçin ve ardından **İndir'e** tıklayarak iletinin yerel bir kopyasını .eml biçiminde kaydedin.

- ![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png) **Göndereni engelle**: Göndereni **posta** kutunuzdaki Engellenen Gönderenler listesine ekleyin. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Bu seçenek, daha önce yayımlanmış olan iletiler için kullanılamaz ( **Serbest bırakıldı durum** değeri **Serbest Bırakıldı'dır**).

İletiyi serbest bırakmaz veya kaldırmazsanız, varsayılan karantina bekletme süresi dolduktan sonra silinir ( **Süre sonu** sütununda gösterildiği gibi).

> [!NOTE]
> Mobil cihazda açıklama metni eylem simgelerinde kullanılamaz.
>
> :::image type="content" source="../../media/quarantine-user-message-details-flyout-mobile-actions.png" alt-text="Karantinaya alınan ve kullanılabilir eylemlerin vurgulandığı iletinin ayrıntıları" lightbox="../../media/quarantine-user-message-details-flyout-mobile-actions.png":::

>
> Sırayla simgeler ve karşılık gelen açıklamaları aşağıdaki tabloda özetlenir:
>
> |Simge|Açıklama|
> |---:|---|
> |![E-postayı serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png)|**E-postayı serbest bırakma**|
> |![İleti üst bilgilerini görüntüle simgesi.](../../media/m365-cc-sc-eye-icon.png)|**İleti üst bilgilerini görüntüleme**|
> |![önizleme iletisi simgesi.](../../media/m365-cc-sc-eye-icon.png)|**önizleme iletisi**|
> |![Karantinadan kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png)|**Karantinadan kaldır**|
> |![Göndereni engelle simgesi.](../../media/m365-cc-sc-block-sender-icon.png)|**Göndereni engelle**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Karantinaya alınan birden çok e-posta iletisinde işlem gerçekleştirme

İlk sütunun solundaki boş alana tıklayarak listeden (en fazla 100) birden çok karantinaya alınmış ileti seçtiğinizde, aşağıdaki eylemleri gerçekleştirebileceğiniz **Toplu eylemler** açılan listesi görüntülenir:

:::image type="content" source="../../media/quarantine-user-message-bulk-actions.png" alt-text="Karantinadaki iletiler için toplu eylemler açılan listesi" lightbox="../../media/quarantine-user-message-bulk-actions.png":::

- ![İletileri serbest bırak simgesi.](../../media/m365-cc-sc-check-mark-icon.png) **Yayın iletileri**: İletileri Gelen Kutunuza teslim eder.
- ![Karantinadan kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png) **İletileri silme**: Görüntülenen uyarıda **Evet'e** tıkladıktan sonra, iletiler özgün alıcılara gönderilmeden karantinadan hemen kaldırılır.
