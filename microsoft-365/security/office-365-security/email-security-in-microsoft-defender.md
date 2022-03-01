---
title: Microsoft Defender'da Threat Explorer ile e-posta güvenliği Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Kötü amaçlı yazılım kimlik avı girişimlerini  görüntüp araştırabilirsiniz.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ee97c54174fc7aaa2cd6d653dcd9fdd8298376d
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021630"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Microsoft Defender'da Threat Explorer ile e-posta güvenliği Office 365

Bu makalede:

- [E-postada algılanan kötü amaçlı yazılımı görüntüleme](#view-malware-detected-in-email)
- [Kimlik avı URL'sini görüntüleme ve karar verilerine tıklama](#view-phishing-url-and-click-verdict-data)
- [Otomatik araştırma ve yanıt başlatma](#start-automated-investigation-and-response)

> [!NOTE]
> Bu, **Threat Explorer (Explorer)****,** **e-posta** güvenliği ve Explorer ile Gerçek zamanlı algılamalar (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) hakkında **3** makalelik bir serinin bir bölümüdir. Bu dizide yer alan diğer iki makale de Tehdit Gezgini'nde [tehdit](threat-hunting-in-threat-explorer.md) avı, [Tehdit Gezgini ve Gerçek zamanlı algılamalar'dır](real-time-detections.md).

Bu makalede, güvenlik özellikleri tarafından e-postayla algılanan kötü amaçlı yazılım ve kimlik avı girişimlerini görüntüleme ve Microsoft 365 açıklanmıştır.

**Aşağıdakiler için geçerlidir:**

- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="view-malware-detected-in-email"></a>E-postada algılanan kötü amaçlı yazılımı görüntüleme

Microsoft 365 teknolojisine göre sıralanmış e-postada kötü amaçlı yazılım algılanmış olarak görmek için, [**\>**](threat-explorer-views.md#email--malware) Explorer'ın E-posta Kötü Amaçlı E-posta görünümünü kullanın (veya Gerçek zamanlı algılamalar). Kötü amaçlı yazılım varsayılan görünüm olduğu için Gezgin'i açar açmaz seçili olabilir.

1. Aşağıdaki Microsoft 365 Defender portalında E-posta ve <https://security.microsoft.com>**& gidin** ve **Gezgin'i** veya **Gerçek zamanlı algılamalar'ı seçin**. Doğrudan sayfaya gitmek için veya kullanın <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

   Bu örnekte Explorer **2007 2013 201**

   Buradan Görünüm'den başlatın, araştırmanız için gereken belirli bir zaman dilimini seçin (gerekirse) ve Gezgin'de olduğu gibi [filtrelerinizi odak noktası olarak kullanın](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Görünüm açılan **listesinde** , Kötü Amaçlı E-posta Kötü Amaçlı **E-posta'nın** \> **seçili** olduğunu doğrulayın.

3. **Gönderen'e** tıklayın **ve açılan** \> **listede Temel** Algılama teknolojisi'ne tıklayın.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="kötü amaçlı yazılım algılama teknolojisi.":::

   Algılama teknolojileriniz artık rapor için filtre olarak kullanılabilir.

4. Bir seçenek belirtin ve ardından bu **filtreyi uygulamak** için Yenile'ye tıklayın (tarayıcı pencerenizi yenilemenin gerektir).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="algılama teknolojisi seçilmiştir.":::

   Rapor, seçtiğiniz teknoloji seçeneği kullanılarak, kötü amaçlı yazılımın e-postada algıladık sonuçları gösterecek şekilde yenilenir. Buradan daha fazla analiz yürütesiniz.

### <a name="report-a-message-as-clean-in-explorer"></a>Gezgin'de iletiyi temiz olarak bildirme

Bir iletiyi **hatalı pozitif sonuç** olarak rapor etmek için Explorer'daki Rapor temizleme seçeneğini kullanabilirsiniz. 

1. Microsoft 365 Defender portalında  **E-posta &-posta** \> işbirliği **Gezgini'ne** gidin ve Görünüm açılan listesinde Kimlik Avı'nın **seçili olduğunu** doğrulayın.

2. E-posta **sekmesindeysiniz** ve bildirilen iletiler listesinden, temiz olarak rapor etmek istediğiniz iletileri seçin. 

3. Seçenek **listesini** genişletmek için Eylemler'e tıklayın.

4. Seçenek listesini aşağı kaydırarak Yeni gönderimi başlat **bölümüne gidin ve** ardından Rapor **temizleme'yi seçin**. Bir açılır çıktı görüntülenir.

   > [!div class="mx-imgBorder"]
   > ![Explorer'da rapor temizleme seçeneği.](../../media/report-clean-option-explorer.png) 

5. Kaydırıcıyı Açık olarak **ayarlayın**. Açılan listeden iletinin kaldırılmasını istediğiniz gün sayısını belirtin, gerekirse bir not ekleyin ve sonra Gönder'i **seçin**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Kimlik avı URL'sini görüntüleme ve karar verilerine tıklama

İzin verilen, engellenmiş ve geçersiz kılınmış URL'lerin listesi de içinde olmak üzere, e-posta url'leri aracılığıyla kimlik avı girişimlerini görüntüebilirsiniz. Tıkılan URL'leri tanımlamak için, [Kasa yapılandırılması](safe-links.md) gerekir. Yeni Bağlantılar'ın [tıklama Kasa](set-up-safe-links-policies.md) ve tıklama kararlarının günlüğü tutma için Bağlantılar ilkelerini ayarlamayı Kasa.

1. Aşağıdaki Microsoft 365 Defender portalında E-posta ve <https://security.microsoft.com>**& gidin** ve **Gezgin'i** veya **Gerçek zamanlı algılamalar'ı seçin**. Doğrudan sayfaya gitmek için veya kullanın <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

   Bu örnekte Explorer **2007 2013 201**

2. Görünüm açılan **listesinde E-posta** Kimlik **Avını** \> **seçin**.

   > [!div class="mx-imgBorder"]
   > ![Kimlik avı bağlamında Gezgin için Görünüm menüsü.](../../media/ExplorerViewEmailPhishMenu.png)

3. **Gönderen'e** tıklayın ve ardından **URL'leri seçin** \> **Açılan** listede karara tıklayın.

4. Görünen seçeneklerde, Engellendi ve Geçersiz kılınma öğesini engelle gibi bir  veya birden çok seçeneği belirleyin ve yenile'ye **tıklayın (** tarayıcı pencerenizi yenilemeyin).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="URL'ler ve kararlara tıklayın.":::

   Rapor, raporun altındaki URL'ler sekmesinde iki farklı **URL tablosu gösterecek** şekilde yenilenir:

   - **En üst URL'ler** , filtreleyilen iletilerde yer alan URL'ler ve her URL için e-posta teslim eylemi sayılarıdır. Kimlik avı e-posta görünümünde, bu liste normalde geçerli URL'leri içerir. Saldırganlar, iletilerinde iyi ve kötü URL'lerin bir karışımını bulundurarak bunların teslim  kurtarmaya çalışsa da kötü amaçlı bağlantıların daha ilginç bir görünüme sahip olduğunu fark ediyor. URL'ler tablosu toplam e-posta sayısına göre sıralanmış, ancak görünümü basitleştirmek için bu sütun gizlenir.

   - **En çok** tıklamalar, Kasa tıklama sayısına göre sıralanmış, Bağlantıların kaydırılmış URL'leridir. Görünümü basitleştirmek için bu sütun da görüntülenmez. Sütuna göre toplam sayı sayısı, tık Kasa URL için karara tıklama sayısını gösterir. Kimlik avı e-posta görünümünde, bunlar çoğunlukla şüpheli veya kötü amaçlı URL'lerdir. Ancak görünüm, tehdit olmayan ancak kimlik avı iletisinde yer alan URL'leri içerebilir. Kaydırılmış bağlantılarda URL tıklamaları burada göster şey değil.

   İki URL tablosu kimlik avı e-posta iletisinde teslim eylemine ve konuma göre en önemli URL'leri gösterir. Tablolarda, uyarıya rağmen engellenmiş veya ziyaret edilen URL tıklamaları gösterir; böylelikle kullanıcılara hangi olası hatalı bağlantıların sunlarak ve kullanıcılara tıklanarak gösternebilirsiniz. Buradan daha fazla analiz yürütesiniz. Örneğin, grafiğin altında, kuruluşun ortamında engellenmiş e-posta iletilerinde en üst URL'leri görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > ![Engellenmiş olan Gezgin URL'leri.](../../media/ExplorerPhishClickVerdictURLs.png)

   Daha ayrıntılı bilgi görüntülemek için bir URL seçin.

   > [!NOTE]
   > URL uçarak çıkış iletişim kutusunda, e-posta iletilerine filtre uygulama, URL'nin ortamınıza maruz kalma sürenizin tam görünümünü göstermek için kaldırılır. Bu, Gezgin'de kaygı ayarlarınız olan e-posta iletilerine filtre uygulamanıza, olası tehditlere neden olan belirli URL'leri bulmanızı ve ardından Gezgin görünümünün kendisine URL filtreleri eklemek zorunda kalmadan ortamınıza URL'nin açık kalma süresini anlamanızı (URL ayrıntıları iletişim kutusu yoluyla) anlamanızı sağlar.

### <a name="interpretation-of-click-verdicts"></a>Tıklama kararlarının yorumlanması

E-posta veya URL çıkışlarında, Üst Tıklamalar'da ve filtreleme deneyimlerimiz arasında farklı tıklama karar değerleri görüyorsunuz:

- **Yok:** URL için karar yakalanamıyor. Kullanıcı URL'ye tıklamış olabilir.
- **İzin verildi:** Kullanıcının URL'ye girmesine izin verili.
- **Engellendi:** Kullanıcının URL'ye gezinmesi engellendi.
- **Bekleyen karar:** Kullanıcıya detonation-pending sayfası sunuldu.
- **Geçersiz kılınan engelleme:** Kullanıcının doğrudan URL'ye gezinmesi engellendi. Ancak kullanıcı URL'ye gitmek için bloğun üzerine atlar.
- **Bekleyen beklemede olan beklemede atlandı:** Kullanıcıya detonation sayfası sunuldu. Ancak kullanıcı URL'ye erişmek için iletinin üzerine atlar.
- **Hata:** Kullanıcıya hata sayfası sunuldu veya karara karar verirken bir hata oluştu.
- **Hata:** Karar yakalama sırasında bilinmeyen bir özel durum oluştu. Kullanıcı URL'ye tıklamış olabilir.

## <a name="start-automated-investigation-and-response"></a>Otomatik araştırma ve yanıt başlatma

> [!NOTE]
> Plan 2 ve 2'nin son güncelleştirmeleri için *Microsoft Defender'Office 365 otomatik soruşturma* ve *Office 365 E5*.

[Otomatik araştırma ve yanıt,](automated-investigation-response-office.md) güvenlik işlemleri ekip sürenizi ve siber saldırıları araştırma ve azaltma için harcanan çabadan tasarruf sağlar. Güvenlik çalışma kitabını tetikleyen uyarılar yapılandırmaya ek olarak, Gezgin'de görünümden otomatik bir araştırma ve yanıt işlemi de başlatabilirsiniz. Ayrıntılar için bkz [. Örnek: Güvenlik yöneticisi Explorer'dan gelen bir soruşturmayı tetikler](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Diğer makaleler

[E-posta Varlık Sayfası içeren e-postaları araştırma](mdo-email-entity-page.md)
