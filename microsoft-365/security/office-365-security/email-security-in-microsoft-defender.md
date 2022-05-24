---
title: Office 365 için Microsoft Defender'de Tehdit Gezgini ile e-posta güvenliği
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
description: Kötü amaçlı yazılım kimlik avı girişimlerini görüntüleyin ve araştırın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 637e387ca457c9795892791a1a6d9326107fc6fb
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648205"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'de Tehdit Gezgini ile e-posta güvenliği

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Şunlar için geçerlidir:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu makalede:

- [E-postada algılanan kötü amaçlı yazılımları görüntüleme](#view-malware-detected-in-email)
- [Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın](#view-phishing-url-and-click-verdict-data)
- [Otomatik araştırma ve yanıt başlatma](#start-automated-investigation-and-response)

> [!NOTE]
> Bu, **Tehdit Gezgini (Gezgin)**, **e-posta güvenliği**, **Gezgin ve Gerçek zamanlı algılamalar** (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) ile ilgili **3 makalelik bir serinin** parçasıdır. Bu serideki diğer iki makale, [Tehdit Gezgini ve Tehdit Gezgini'nde Tehdit avcılığı](threat-hunting-in-threat-explorer.md) [ve Gerçek zamanlı algılamalardır](real-time-detections.md).

Bu makalede, Microsoft 365 güvenlik özellikleri tarafından e-postada algılanan kötü amaçlı yazılımları ve kimlik avı girişimlerini görüntüleme ve araştırma işlemleri açıklanmaktadır.

## <a name="view-malware-detected-in-email"></a>E-postada algılanan kötü amaçlı yazılımları görüntüleme

E-postada kötü amaçlı yazılımların Microsoft 365 teknolojisine göre sıralanmış olduğunu görmek için Explorer'ın [**E-posta \> Kötü Amaçlı Yazılım**](threat-explorer-views.md#email--malware) görünümünü (veya Gerçek zamanlı algılamaları) kullanın. Kötü amaçlı yazılım varsayılan görünümdür, bu nedenle Gezgin'i açar açmaz seçilebilir.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği'ne** gidin ve **Ardından Gezgin** veya **Gerçek zamanlı algılamalar'ı** seçin. Doğrudan sayfaya gitmek için veya <https://security.microsoft.com/realtimereports>kullanın<https://security.microsoft.com/threatexplorer>.

   Bu örnekte **Gezgin** kullanılır.

   Buradan Görünüm'den başlayın, araştırmak için belirli bir zaman dilimi seçin (gerekirse) ve [Gezgin kılavuzuna](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through) göre filtrelerinizi odaklayın.

2. **Görünüm** açılan listesinde **E-posta** \> **Kötü Amaçlı Yazılım'ın** seçili olduğunu doğrulayın.

3. **Gönderen'e** tıklayın ve açılan listede **Temel** \> **Algılama teknolojisi'ni** seçin.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="Kötü amaçlı yazılım algılama teknolojisi" lightbox="../../media/exploreremailmalwaredetectiontech-newimg.png":::

   Algılama teknolojileriniz artık rapor için filtre olarak kullanılabilir.

4. Bir seçenek belirleyin ve ardından **yenile'ye** tıklayarak bu filtreyi uygulayın (tarayıcı pencerenizi yenilemeyin).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="seçilen algılama teknolojisi" lightbox="../../media/exploreremailmalwaredetectiontech2-new.png":::

   Rapor, seçtiğiniz teknoloji seçeneğini kullanarak kötü amaçlı yazılımların e-postada algıladığınız sonuçları gösterecek şekilde yenilenir. Buradan daha fazla analiz gerçekleştirebilirsiniz.

### <a name="report-a-message-as-clean-in-explorer"></a>Gezgin'de iletiyi temiz olarak bildirme

Bir iletiyi hatalı pozitif olarak bildirmek için Gezgin'de **Temiz** raporla seçeneğini kullanabilirsiniz. 

1. Microsoft 365 Defender portalında **E-posta & işbirliği** \> **Gezgini'ne** gidin ve **Görünüm** açılan listesinde **Kimlik Avı'nın** seçili olduğunu doğrulayın.

2. **E-posta** sekmesinde olduğunuzu doğrulayın ve bildirilen iletiler listesinden temiz olarak bildirmek istediğiniz iletileri seçin. 

3. Seçenekler listesini genişletmek için **Eylemler'e** tıklayın.

4. **Yeni gönderimi başlat** bölümüne gitmek için seçenekler listesini aşağı kaydırın ve ardından **Temiz raporla'yı** seçin. Açılır öğe görüntülenir.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/report-clean-option-explorer.png" alt-text="Gezgin'de Rapor temizleme seçeneği" lightbox="../../media/report-clean-option-explorer.png":::

5. Kaydırıcıyı **Açık** konuma getirin. Açılan listeden, iletinin kaldırılmasını istediğiniz gün sayısını belirtin, gerekirse bir not ekleyin ve **gönder'i** seçin. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın

İzin verilen, engellenen ve geçersiz kılınan URL'lerin listesi de dahil olmak üzere, e-postadaki URL'ler aracılığıyla kimlik avı girişimlerini görüntüleyebilirsiniz. Tıklanan URL'leri tanımlamak için [Kasa Bağlantıların](safe-links.md) yapılandırılması gerekir. [Kasa Bağlantıları ilkelerini](set-up-safe-links-policies.md) tıklama zamanı koruması ve Kasa Bağlantıları ile tıklama kararlarının günlüğe kaydedilmesi için ayarladığınızdan emin olun.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği'ne** gidin ve **Ardından Gezgin** veya **Gerçek zamanlı algılamalar'ı** seçin. Doğrudan sayfaya gitmek için veya <https://security.microsoft.com/realtimereports>kullanın<https://security.microsoft.com/threatexplorer>.

   Bu örnekte **Gezgin** kullanılır.

2. **Görünüm** açılan listesinde **E-posta** \> **Kimlik Avı'nı** seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Kimlik avı bağlamında Gezgin için Görünüm menüsü" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. **Gönderen'e** tıklayın ve **URL'ler** \> Açılan **listeden karara tıklayın'ı** seçin.

4. Görüntülenen seçeneklerde **Engellendi** ve **Engelle geçersiz kılındı** gibi bir veya daha fazla seçenek belirleyin ve ardından **Yenile'ye** tıklayın (tarayıcı pencerenizi yenilemeyin).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="URL'ler ve tıklama kararları" lightbox="../../media/threatexploreremailphishclickverdict-new.png":::

   Rapor, raporun altındaki **URL'ler** sekmesinde iki farklı URL tablosu gösterecek şekilde yenilenir:

   - **En çok kullanılan URL'ler** , filtrelediğiniz iletilerdeki URL'ler ve her URL için e-posta teslim eylemi sayısıdır. Kimlik avı e-posta görünümünde bu liste genellikle geçerli URL'ler içerir. Saldırganlar, teslim etmeye çalışmak için iletilerine iyi ve kötü URL'lerin bir karışımını ekler, ancak kötü amaçlı bağlantıların daha ilginç görünmesini sağlar. URL tablosu toplam e-posta sayısına göre sıralanır, ancak görünümü basitleştirmek için bu sütun gizlenir.

   - **En üstteki tıklamalar**, tıklanan ve toplam tıklama sayımına göre sıralanmış Kasa Bağlantılar sarmalanmış URL'leridir. Görünümü basitleştirmek için bu sütun da görüntülenmez. Sütuna göre toplam sayımlar, tıklanan her URL için Kasa Bağlantıları tıklama kararı sayısını gösterir. Kimlik avı e-posta görünümünde bunlar genellikle şüpheli veya kötü amaçlı URL'lerdir. Ancak görünümde tehdit olmayan ancak kimlik avı iletilerinde bulunan URL'ler yer alabilir. Açılmamış bağlantılarda URL tıklamaları burada gösterilmez.

   İki URL tablosu, teslim eylemine ve konuma göre kimlik avı e-posta iletilerindeki en iyi URL'leri gösterir. Tablolar, uyarıya rağmen engellenen veya ziyaret edilen URL tıklamalarını gösterir, böylece kullanıcılara hangi olası hatalı bağlantıların sunulduğunu ve kullanıcıların tıkladığını görebilirsiniz. Buradan daha fazla analiz gerçekleştirebilirsiniz. Örneğin, grafiğin altında, kuruluşunuzun ortamında engellenen e-posta iletilerinde en çok kullanılan URL'leri görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="Engellenen Gezgin URL'leri" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Daha ayrıntılı bilgileri görüntülemek için bir URL seçin.

   > [!NOTE]
   > URL açılır öğesi iletişim kutusunda, e-posta iletilerindeki filtreleme kaldırılarak URL'nin ortamınızda gösterilmesinin tam görünümü gösterilir. Bu, Gezgin'de ilgilendiğiniz e-posta iletilerini filtrelemenize, olası tehditler olan belirli URL'leri bulmanıza ve ardından Gezgin görünümünün kendisine URL filtreleri eklemek zorunda kalmadan ortamınızdaki URL'nin açığa çıkma durumunu (URL ayrıntıları iletişim kutusu aracılığıyla) genişletmenize olanak tanır.

### <a name="interpretation-of-click-verdicts"></a>Tıklama kararlarının yorumlanması

E-posta veya URL açılır listelerinde, İlk Tıklamalar'da ve filtreleme deneyimlerimizde farklı tıklama kararı değerleri görürsünüz:

- **Hiçbiri:** URL için karar alınamadı. Kullanıcı URL'ye tıklaymış olabilir.
- **Izin verilen:** Kullanıcının URL'ye gitmesine izin verildi.
- **Engellenen:** Kullanıcının URL'ye gezinmesi engellendi.
- **Bekleyen karar:** Kullanıcıya patlama bekleniyor sayfası sunuldu.
- **Geçersiz kılınarak engellendi:** Kullanıcının doğrudan URL'ye gezinmesi engellendi. Ancak kullanıcı URL'ye gitmek için bloğun üzerine geçti.
- **Bekleyen karar atlandı:** Kullanıcıya patlama sayfası sunuldu. Ancak kullanıcı URL'ye erişmek için iletinin üzerine geçti.
- **Hata:** Kullanıcıya hata sayfası sunuldu veya karar yakalanırken bir hata oluştu.
- **Başarısızlık:** Karar yakalanırken bilinmeyen bir özel durum oluştu. Kullanıcı URL'ye tıklaymış olabilir.

## <a name="start-automated-investigation-and-response"></a>Otomatik araştırma ve yanıt başlatma

> [!NOTE]
> Otomatik araştırma ve yanıt özellikleri *Office 365 için Microsoft Defender Plan 2* ve *Office 365 E5'da* kullanılabilir.

[Otomatik araştırma ve yanıt](automated-investigation-response-office.md) , güvenlik operasyonları ekibinize siber saldırıları araştırmak ve azaltmak için harcanan zamandan ve çabadan tasarruf edebilir. Güvenlik playbook'larını tetikleyebilecek uyarıları yapılandırmaya ek olarak, Gezgin'deki bir görünümden otomatik araştırma ve yanıt işlemi başlatabilirsiniz. Ayrıntılar için bkz [. Örnek: Güvenlik yöneticisi Gezgin'den araştırma tetikler](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Diğer makaleler

[E-posta Varlık Sayfası ile e-postaları araştırma](mdo-email-entity-page.md)
