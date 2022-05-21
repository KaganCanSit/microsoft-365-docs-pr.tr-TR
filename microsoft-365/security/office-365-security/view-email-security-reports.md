---
title: E-posta güvenlik raporlarını görüntüleme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 3a137e28-1174-42d5-99af-f18868b43e86
ms.collection:
- M365-security-compliance
description: Yöneticiler, Microsoft 365 Defender portalında bulunan e-posta güvenlik raporlarını bulmayı ve kullanmayı öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6e57b797ab0b5d5eee90315ae9c3459fcba0a02c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621680"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında e-posta güvenlik raporlarını görüntüleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 Defender portalında<https://security.microsoft.com>, Microsoft 365'daki istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma özellikleri gibi e-posta güvenlik özelliklerinin kuruluşunuzu nasıl korudiğini görmenize yardımcı olmak için çeşitli raporlar sağlanır. [Gerekli izinlere](#what-permissions-are-needed-to-view-these-reports) sahipseniz bu raporları bu makalede açıklandığı gibi görüntüleyebilir ve indirebilirsiniz.

> [!NOTE]
>
> **E-posta & işbirliği raporları sayfasındaki raporlardan** bazıları Office 365 için Microsoft Defender gerektirir. Bu raporlar hakkında bilgi için bkz. [Microsoft 365 Defender portalında Office 365 için Defender raporları görüntüleme](view-reports-for-mdo.md).
>
> Posta akışıyla ilgili raporlar artık Exchange yönetim merkezindedir. Bu raporlar hakkında daha fazla bilgi için [bkz. Yeni Exchange yönetim merkezinde posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

Kuruluşunuzdaki Office 365 için Defender etkinliğini anlamak için raporları nasıl kullanabileceğinizi öğrenmek için bu kısa videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBkxB]

## <a name="email-security-report-changes-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında e-posta güvenlik raporu değişiklikleri

Microsoft 365 Defender portalında değiştirilen, taşınan veya kullanım dışı bırakılan Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender raporları aşağıdaki tabloda açıklanmıştır.

|Kullanım dışı bırakılan rapor ve cmdlet'ler|Yeni rapor ve cmdlet'ler|İleti Merkezi Kimliği|Tarih|
|---|---|:---:|:---:|
|**URL izleme** <br/><br/> Get-URLTrace|[URL koruma raporu](view-reports-for-mdo.md#url-protection-report) <br/><br/> [Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <br> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|MC239999|Haziran 2021|
|**Gönderilen ve alınan e-posta raporu** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailReport|[Tehdit koruması durum raporu](#threat-protection-status-report) <br> [Posta akışı durum raporu](#mailflow-status-report) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <br> [Get-MailFlowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|MC236025|Haziran 2021|
|**Raporu iletme** <br/><br/> cmdlet yok|[EAC'de otomatik iletilen iletiler raporu](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) <br/><br/> cmdlet yok|MC250533|Haziran 2021|
|**Kasa Ekler dosya türleri raporu** <br/><br/> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Tehdit koruması durum raporu: Verileri E-posta \> Kötü Amaçlı Yazılımlarına göre görüntüleme](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250532|Haziran 2021|
|**Kasa Ekler ileti bırakma raporu** <br/><br/> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Tehdit koruması durum raporu: Verileri E-posta \> Kötü Amaçlı Yazılımlarına göre görüntüleme](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250531|Haziran 2021|
|**E-posta raporunda kötü amaçlı yazılım algılandı** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailMalwareReport|[Tehdit koruması durum raporu: Verileri E-posta \> Kötü Amaçlı Yazılımlarına göre görüntüleme](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250530|Haziran 2021|
|**İstenmeyen posta algılama raporu** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailSpamReport|[Tehdit koruma durum raporu: E-posta İstenmeyen Posta \> ile verileri görüntüleme](#view-data-by-email--spam-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250529|Ekim 2021|
|Get-AdvancedThreatProtectionDocumentReport <br/><br/> Get-AdvancedThreatProtectionDocumentDetail|[Get-ContentMalwareMdoAggregateReport](/powershell/module/exchange/get-contentmalwaremdoaggregatereport) <br/><br/> [Get-ContentMalwareMdoDetailReport](/powershell/module/exchange/get-contentmalwaremdodetailreport)|MC343433|Mayıs 2022|
|**aktarım kuralı raporunu Exchange** <br/><br/> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|[EAC'de aktarım kuralı raporunu Exchange](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report) <br/><br/> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|MC316157|Nisan 2022|
|Get-MailTrafficTopReport|[En çok gönderenler ve alıcı raporu](view-email-security-reports.md#top-senders-and-recipients-report) <br/><br/> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport) <br/><br/> **Not**: Get-MailTrafficTopReport'taki şifreleme raporlama özelliklerinin yerini alamaz.|MC315742|Nisan 2022|

## <a name="compromised-users-report"></a>Güvenliği aşılmış kullanıcılar raporu

> [!NOTE]
> Bu rapor, Exchange Online posta kutularına sahip Microsoft 365 kuruluşlarda kullanılabilir. Tek başına Exchange Online Protection (EOP) kuruluşlarında kullanılamaz.

**Güvenliği Aşılmış kullanıcılar** raporu, son 7 gün içinde **Şüpheli** veya **Kısıtlı** olarak işaretlenmiş kullanıcı hesaplarının sayısını gösterir. Bu durumlardan herhangi birindeki hesaplar sorunlu ve hatta güvenliği aşılmış durumdadır. Sık kullanımda, şüpheli veya kısıtlanmış hesaplarda ani artışları ve hatta eğilimleri tespit etmek için raporu kullanabilirsiniz. Güvenliği aşılmış kullanıcılar hakkında daha fazla bilgi için bkz. [Güvenliği aşılmış bir e-posta hesabını yanıtlama](responding-to-a-compromised-email-account.md).

:::image type="content" source="../../media/compromised-users-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Güvenliği aşılmış kullanıcılar pencere öğesi" lightbox="../../media/compromised-users-report-widget.png":::

Toplama görünümü son 90 güne ilişkin verileri, ayrıntı görünümü ise son 30 güne ilişkin verileri gösterir.

Raporu adresinden Microsoft 365 Defender portalında <https://security.microsoft.com>görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **Güvenliği aşılmış kullanıcıları** bulun ve **ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/CompromisedUsers>.

**Güvenliği aşılmış kullanıcılar** sayfasında, grafik belirtilen tarih aralığı için aşağıdaki bilgileri gösterir:

- **Kısıtlı**: Son derece şüpheli desenler nedeniyle kullanıcı hesabının e-posta göndermesi kısıtlandı.
- **Şüpheli**: Kullanıcı hesabı şüpheli e-posta gönderdi ve e-posta gönderme riski altında.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Oluşturma zamanı**
- **Kullanıcı Kimliği**
- **Eylem**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Etkinlik**: **Kısıtlı** veya **Şüpheli**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Güvenliği aşılmış kullanıcılar** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

:::image type="content" source="../../media/compromised-users-report-activity-view.png" alt-text="Güvenliği aşılmış kullanıcılar raporundaki Rapor görünümü" lightbox="../../media/compromised-users-report-activity-view.png":::

## <a name="exchange-transport-rule-report"></a>aktarım kuralı raporunu Exchange

**Exchange aktarım kuralı** raporu, posta akışı kurallarının (taşıma kuralları olarak da bilinir) kuruluşunuzdaki gelen ve giden iletiler üzerindeki etkisini gösterir.

Raporu Microsoft 365 Defender portalında görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **Exchange aktarım kuralını** bulun ve **ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/transport-rule-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Exchange aktarım kuralı pencere öğesi" lightbox="../../media/transport-rule-report-widget.png":::

**Exchange aktarım kuralı raporu** sayfasında, kullanılabilir grafikler ve veriler aşağıdaki bölümlerde açıklanmıştır.
> [!NOTE]
> **Exchange aktarım kuralı raporu** artık EAC'de kullanılabilir. Daha fazla bilgi için bkz. [yeni EAC Exchange taşıma kuralı raporu](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

### <a name="chart-breakdown-by-direction"></a>Yöne göre grafik dökümü

:::image type="content" source="../../media/transport-rule-report-etr-direction-view.png" alt-text="Exchange taşıma kuralı raporundaki Exchange Taşıma kuralları için Yön görünümü" lightbox="../../media/transport-rule-report-etr-direction-view.png":::

**Yöne göre Grafik dökümü'nü** seçerseniz aşağıdaki grafikler kullanılabilir:

- **Exchange aktarım kurallarına göre verileri görüntüleme**: Posta akışı kurallarından etkilenen **Gelen** ve **Giden** iletilerin sayısı.
- **Verileri DLP Exchange aktarım kurallarına göre görüntüleme**: Veri kaybı önleme (DLP) posta akışı kurallarından etkilenen **Gelen** ve **Giden** iletilerin sayısı.

Aşağıdaki bilgiler grafiğin altındaki ayrıntılar tablosunda gösterilmiştir:

- **Tarih**
- **DLP ilkesi** (**Verileri yalnızca DLP Exchange aktarım kurallarına göre görüntüleme**)
- **Taşıma kuralı**
- **Konu**
- **Gönderen adresi**
- **Alıcı adresi**
- **Önem derecesi**
- **Yön**

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Yön**: **Giden** ve **Gelen**.
- **Önem Derecesi**: **Yüksek önem derecesi**, **Orta önem derecesi** ve **Düşük önem derecesi**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Exchange aktarım kuralı rapor** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="chart-breakdown-by-severity"></a>Önem Derecesine göre grafik dökümü

:::image type="content" source="../../media/transport-rule-report-etr-severity-view.png" alt-text="Exchange aktarım kuralı raporundaki Exchange Aktarım kuralları için Önem Derecesi görünümü" lightbox="../../media/transport-rule-report-etr-severity-view.png":::

**Önem Derecesine göre Grafik dökümü'ni** seçerseniz aşağıdaki grafikler kullanılabilir:

- **Exchange aktarım kurallarına göre verileri görüntüleme**: **Yüksek önem derecesi**, **Orta önem derecesi** ve **Düşük önem derecesi iletilerinin** sayısı. Önem derecesi düzeyini kuralda bir eylem olarak ayarlarsınız (**Bu kuralı önem düzeyi veya** _SetAuditSeverity_ ile denetleyin). Daha fazla bilgi için bkz. [Exchange Online posta akışı kuralı eylemleri](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **DLP Exchange aktarım kurallarına göre verileri görüntüleme**: DLP posta akışı kurallarından etkilenen **Yüksek önem derecesi**, **Orta önem derecesi** ve **Düşük önem derecesi** iletilerinin sayısı.

Aşağıdaki bilgiler grafiğin altındaki ayrıntılar tablosunda gösterilmiştir:

- **Tarih**
- **DLP ilkesi** (**Verileri yalnızca DLP Exchange aktarım kurallarına göre görüntüleme**)
- **Taşıma kuralı**
- **Konu**
- **Gönderen adresi**
- **Alıcı adresi**
- **Önem derecesi**
- **Yön**

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Yön**: **Giden** ve **Gelen**
- **Önem Derecesi**: **Yüksek önem derecesi**, **Orta önem derecesi** ve **Düşük önem derecesi**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Exchange aktarım kuralı rapor** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

## <a name="forwarding-report"></a>Raporu iletme

> [!NOTE]
> Bu rapor artık EAC'de kullanılabilir. Daha fazla bilgi için bkz. [Yeni EAC'de otomatik iletilen iletiler raporu](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Posta akışı durum raporu

**Posta akışı durum raporu**, gelen ve giden e-postalar, istenmeyen posta algılamaları, kötü amaçlı yazılımlar, "iyi" olarak tanımlanan e-postalar ve uçta izin verilen veya engellenen e-postalarla ilgili bilgileri gösteren akıllı bir rapordur. Bu, uç koruma bilgilerini içeren tek rapordur ve hizmete Exchange Online Protection (EOP) tarafından değerlendirilmek üzere izin verilmeden önce ne kadar e-postanın engellendiğini gösterir. Bir ileti beş alıcıya gönderiliyorsa bunu bir ileti değil beş farklı ileti olarak saymamızı anlamak önemlidir.

Raporu adresinden Microsoft 365 Defender portalında <https://security.microsoft.com>görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **Posta akışı durum özetini** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/mail-flow-status-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Posta akışı durum özeti pencere öğesi" lightbox="../../media/mail-flow-status-report-widget.png":::

### <a name="type-view-for-the-mailflow-status-report"></a>Posta akışı durum raporu için tür görünümü

:::image type="content" source="../../media/mail-flow-status-report-type-view.png" alt-text="Posta akışı durum raporundaki Tür görünümü" lightbox="../../media/mail-flow-status-report-type-view.png":::

**Posta Akışı durum raporu** sayfasında, **Tür** sekmesi varsayılan olarak seçilidir. Grafik, belirtilen tarih aralığı için aşağıdaki bilgileri gösterir:

- **İyi posta**: İstenmeyen posta olmadığı belirlenen veya kullanıcı ya da kuruluş ilkeleri tarafından izin verilen e-posta.
- **Toplam**
- **Kötü amaçlı yazılım**: Çeşitli filtreler tarafından kötü amaçlı yazılım olarak engellenen e-posta.
- **Kimlik avı e-postası**: Çeşitli filtreler tarafından kimlik avı olarak engellenen e-posta.
- **İstenmeyen posta**: Çeşitli filtreler tarafından istenmeyen posta olarak engellenen e-posta.
- **Kenar koruması**: EOP veya Office 365 için Defender tarafından değerlendirilmeden önce kenarda/çevrede reddedilen e-posta.
- **Kural iletileri**: Posta akışı kuralları (taşıma kuralları olarak da bilinir) tarafından üzerinde işlem yapılan e-posta iletileri.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Yön**
- **Tür**
- **24 saat**
- **3 gün**
- **7 gün**
- **15 gün**
- **30 gün**

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Posta yönü**: **Gelen** ve **Giden**.
- **Tür**:
  - **İyi posta**
  - **Malware**
  - **Spam**
  - **Kenar koruması**
  - **Kural iletileri**
  - **Kimlik avı postası**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Posta akışı durum raporu** sayfasına dönün, **daha fazla ayrıntı için Kategori seçin'e** tıklarsanız, aşağıdaki değerlerden birini seçebilirsiniz:

- **Kimlik avı e-postası**: Bu seçim sizi [Tehdit koruması durum raporuna](view-email-security-reports.md#threat-protection-status-report) götürür.
- **E-postadaki kötü amaçlı yazılım**: Bu seçim sizi [Tehdit koruması durum raporuna](view-email-security-reports.md#threat-protection-status-report) götürür.
- **İstenmeyen posta algılamaları**: Bu seçim sizi [İstenmeyen Posta Algılamaları raporuna](view-email-security-reports.md#spam-detections-report) götürür.
- **Edge istenmeyen postayı engelledi**: Bu seçim sizi [İstenmeyen Posta Algılamaları raporuna](view-email-security-reports.md#spam-detections-report) götürür.

**Posta akışı durum raporu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama ve](#schedule-report)** ![Dışarı Aktar simgesi oluşturun.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="direction-view-for-the-mailflow-status-report"></a>Posta akışı durum raporu için yön görünümü

:::image type="content" source="../../media/mail-flow-status-report-direction-view.png" alt-text="Posta Akışı durum raporundaki Yön görünümü" lightbox="../../media/mail-flow-status-report-direction-view.png":::

**Yön** sekmesine tıklarsanız grafikte belirtilen tarih aralığı için aşağıdaki bilgiler gösterilir:

- **Gelen**
- **Giden**

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Posta yönü**: **Gelen** ve **Giden**.
- **Tür**:
  - **İyi posta**
  - **Malware**
  - **Spam**
  - **Kenar koruması**
  - **Kural iletileri**
  - **Kimlik avı postası**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Posta akışı durum raporu** sayfasına dönün, **daha fazla ayrıntı için Kategori seçin'e** tıklarsanız, aşağıdaki değerlerden birini seçebilirsiniz:

- **Kimlik avı e-postası**: Bu seçim sizi [Tehdit koruması durum raporuna](view-email-security-reports.md#threat-protection-status-report) götürür.
- **E-postadaki kötü amaçlı yazılım**: Bu seçim sizi [Tehdit koruması durum raporuna](view-email-security-reports.md#threat-protection-status-report) götürür.
- **İstenmeyen posta algılamaları**: Bu seçim sizi [İstenmeyen Posta Algılamaları raporuna](view-email-security-reports.md#spam-detections-report) götürür.
- **Edge istenmeyen postayı engelledi**: Bu seçim sizi [İstenmeyen Posta Algılamaları raporuna](view-email-security-reports.md#spam-detections-report) götürür.

**Posta akışı durum raporu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **Zamanlama ve** ![Dışarı Aktar simgesi oluşturun.](../../media/m365-cc-sc-download-icon.png) **Dışarı aktarma** düğmeleri kullanılabilir.

### <a name="mailflow-view-for-the-mailflow-status-report"></a>Posta akışı durum raporu için posta akışı görünümü

**Posta Akışı** görünümünde, Microsoft'un e-posta tehdit koruması özelliklerinin kuruluşunuzdaki gelen ve giden e-postaları nasıl filtrelediğiniz gösterilir. Bu görünümde, toplam e-posta sayısıyla ilgili ayrıntıları ve kenar koruması, kötü amaçlı yazılımdan koruma, kimlik avı önleme, istenmeyen posta önleme ve kimlik sahtekarlığı gibi yapılandırılmış tehdit koruması özelliklerinin bu sayıyı nasıl etkilediği hakkında ayrıntılı bilgi sağlamak için yatay akış diyagramı ( _Sankey_ diyagramı olarak bilinir) kullanılır.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view.png" alt-text="Posta akışı durum raporundaki Posta Akışı görünümü" lightbox="../../media/mail-flow-status-report-mailflow-view.png":::

Toplama görünümü ve ayrıntılar tablosu görünümü 90 günlük filtrelemeye olanak tanır.

Diyagramdaki bilgiler **EOP** veya **Office 365 için Defender** teknolojileri tarafından renk kodlanmıştır.

Diyagram aşağıdaki yatay şeritler halinde düzenlenmiştir:

- **Toplam e-posta** bandı: Bu değer her zaman önce gösterilir.
- **Edge bloğu** ve **İşlenmiş** bant:
  - **Kenar bloğu: Uçta** filtrelenen ve Edge Koruması olarak tanımlanan iletiler.
  - **İşlendi**: Filtreleme yığını tarafından işlenen iletiler.
- Sonuç bandı:
  - **Kural Bloğu**: Exchange posta akışı kuralları (aktarım kuralları) tarafından işlenen iletiler.
  - **Kötü amaçlı yazılım bloğu**: Çeşitli filtreler tarafından kötü amaçlı yazılım olarak tanımlanan iletiler.<sup>\*</sup>
  - **Kimlik avı bloğu**: Çeşitli filtreler tarafından işlenirken kimlik avı olarak tanımlanan iletiler.<sup>\*</sup>
  - **İstenmeyen posta bloğu**: Çeşitli filtreler tarafından işlenirken istenmeyen posta olarak tanımlanan iletiler.<sup>\*</sup>
  - **Kimliğe bürünme bloğu**: Office 365 için Defender kullanıcı kimliğe bürünme veya etki alanı kimliğe bürünme olarak algılanan iletiler.<sup>\*</sup>
  - **Patlama bloğu**: Kasa Ekler ilkeleri veya Office 365 için Defender Kasa Bağlantılar ilkeleri tarafından dosya veya URL'nin patlatılması sırasında algılanan iletiler.<sup>\*</sup>
  - **ZAP kaldırıldı**: Sıfır saatlik otomatik temizleme (ZAP) tarafından kaldırılan iletiler.<sup>\*</sup>
  - **Teslim edildi**: İzin verme nedeniyle kullanıcılara ileti teslim edildi.<sup>\*</sup>

Diyagramda yatay bir bandın üzerine geldiğinizde ilgili ileti sayısını görürsünüz.

<sup>\*</sup> Bu öğeye tıklarsanız, diyagram daha fazla ayrıntı gösterecek şekilde genişletilir. Genişletilmiş düğümlerdeki her öğenin açıklaması için bkz [. Algılama teknolojileri](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-details.png" alt-text="Posta akışı durum raporundaki Posta Akışı görünümünde kimlik avı bloğu ayrıntıları" lightbox="../../media/mail-flow-status-report-mailflow-view-details.png":::

Diyagramın altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Tarih**
- **Toplam e-posta**
- **Kenar filtrelenmiş**
- **Kural iletileri**
- **Kötü amaçlı yazılımdan koruma altyapısı, Kasa Ekler, filtrelenmiş kural**
- **DMARC kimliğe bürünme, kimlik sahtekarlığı, kimlik avı filtresi**
- **Patlama algılama**
- **İstenmeyen postadan koruma filtresi**
- **ZAP kaldırıldı**
- **Tehditlerin algılanmadığı iletiler**

Ayrıntılar tablosunda bir satır seçerseniz, görüntülenen ayrıntılar açılır öğesinde e-posta sayılarının daha ayrıntılı dökümü gösterilir.

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Yön**: **Giden** ve **Gelen**.

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Posta akışı durumu rapor** sayfasına geri dönüp **Eğilimleri göster'e** tıklayarak görüntülenen **Posta akışı eğilimleri** açılır öğesinde eğilim grafiklerini görebilirsiniz.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-show-trends.png" alt-text="Posta akışı durum raporundaki Posta Akışı görünümünde Posta akışı eğilimleri açılır öğesi" lightbox="../../media/mail-flow-status-report-mailflow-view-show-trends.png":::

**Posta akışı durum raporu** sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **Dışarı aktar** düğmesi kullanılabilir.

## <a name="malware-detections-report"></a>Kötü amaçlı yazılım algılama raporu

> [!NOTE]
> Bu rapor kullanım dışı bırakıldı. Aynı bilgiler [Tehdit koruması durum raporunda](#threat-protection-status-report) da mevcuttur.

## <a name="mail-latency-report"></a>Posta gecikme süresi raporu

Office 365 için Defender'daki **Posta gecikme süresi raporu**, kuruluşunuzda yaşanan posta teslimi ve patlama gecikmesi hakkında bilgi içerir. Daha fazla bilgi için bkz. [Posta gecikme süresi raporu](view-reports-for-mdo.md#mail-latency-report).

## <a name="spam-detections-report"></a>İstenmeyen posta algılama raporu

> [!NOTE]
> Bu rapor kullanım dışı bırakıldı. Aynı bilgiler [Tehdit koruması durum raporunda](#threat-protection-status-report) da mevcuttur.

## <a name="spoof-detections-report"></a>Kimlik sahtekarlık algılamaları raporu

**Kimlik sahtekarlık algılamaları** raporu, sahtekarlık nedeniyle engellenen veya izin verilen iletiler hakkındaki bilgileri gösterir. Kimlik sahtekarlığı hakkında daha fazla bilgi için bkz. [EOP'de kimlik sahtekarlığı önleme koruması](anti-spoofing-protection.md).

Raporun toplam görünümü 90 günlük filtrelemeye izin verirken, ayrıntı görünümü yalnızca on günlük filtrelemeye izin verir.

Raporu Microsoft 365 Defender portalında görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında Kimlik **sahtekarı algılamalarını** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/SpoofMailReport>.

:::image type="content" source="../../media/spoof-detections-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Kimlik sahtekarlık algılamaları pencere öğesi" lightbox="../../media/spoof-detections-widget.png":::

Grafik aşağıdaki bilgileri gösterir:

- **Geçirmek**
- **Başarısız**
- **SoftPass**
- **Hiçbiri**
- **Diğer**

Grafikte bir günün (veri noktası) üzerine geldiğinizde, kaç sahte ileti algılandığını ve bunun nedenini görebilirsiniz.

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Sonuç**:
  - **Geçirmek**
  - **Başarısız**
  - **SoftPass**
  - **Yok**
  - **Diğer**
- **Kimlik sahtekarı türü**: **İç** ve **Dış**

:::image type="content" source="../../media/spoof-detections-report-page.png" alt-text="Microsoft 365 Defender portalındaki Kimlik Sahtekarı posta raporu sayfası" lightbox="../../media/spoof-detections-report-page.png":::

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Tarih**
- **Sahte kullanıcı**
- **Altyapı gönderme**
- **Kimlik sahtekarı türü**
- **Sonuç**
- **Sonuç kodu**
- **SPF**
- **DKIM**
- **DMARC**
- **İleti sayısı**

Bileşik kimlik doğrulama sonuç kodları hakkında daha fazla bilgi için bkz[. Microsoft 365'da istenmeyen postadan koruma iletisi üst bilgileri](anti-spam-message-headers.md).

**Kimlik sahtekarı algılamaları** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

## <a name="submissions-report"></a>Gönderimler raporu

**Gönderimler** raporu, yöneticilerin analiz için Microsoft'a bildirdiği öğeler hakkındaki bilgileri gösterir. Daha fazla bilgi için bkz. [Şüpheli istenmeyen postaları, kimlik avı, URL'leri ve dosyaları Microsoft'a göndermek için Yönetici Gönderimi'ni kullanma](admin-submission.md).

Raporu adresinden Microsoft 365 Defender portalında <https://security.microsoft.com>görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **Gönderimler'i** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/adminSubmissionReport>. [Microsoft 365 Defender portalında yönetici gönderimlerine](admin-submission.md) gitmek **için Gönderimlere Git'e** tıklayın. Yöneticiler raporu son 30 gün boyunca görüntüleyebilir.

:::image type="content" source="../../media/submissions-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Gönderimler pencere öğesi" lightbox="../../media/submissions-report-widget.png":::

Grafik aşağıdaki bilgileri gösterir:

- **Bekleyen**
- **Tamamlandı**

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Bildirilen tarih**: **Başlangıç saati** ve **Bitiş saati**
- **Gönderim türü**:
  - **E-posta**
  - **URL**
  - **Dosya**
- **Gönderim Kimliği**
- **Ağ İletisi Kimliği**
- **Gönderen**
- **Ad**
- **Gönderen**
- **Gönderme nedeni**:
  - **Gereksiz değil**
  - **Phish**
  - **Malware**
  - **Spam**
- **Yeniden tarama durumu**:
  - **Bekleyen**
  - **Tamamlandı**

Grafiğin altındaki ayrıntılar tablosu aynı bilgileri gösterir ve **E-posta & işbirliği** \> **Gönderimleri'ndeki** **Analiz için gönderildi** sekmesindeki **Grupla** veya **Sütunları özelleştir** seçenekleriyle aynıdır. Daha fazla bilgi için bkz. [Microsoft'a yönetici gönderimlerini görüntüleme](admin-submission.md#view-admin-submissions-to-microsoft).

**Gönderimler** sayfasında **[Dışarı Aktar](#export-report)** düğmesi kullanılabilir.

:::image type="content" source="../../media/submissions-report-page.png" alt-text="Microsoft 365 Defender portalındaki Gönderimler rapor sayfası" lightbox="../../media/submissions-report-page.png":::

## <a name="threat-protection-status-report"></a>Tehdit koruması durum raporu

**Tehdit koruması durum** raporu hem EOP hem de Office 365 için Defender kullanılabilir; ancak raporlar farklı veriler içerir. Örneğin, EOP müşterileri e-postada algılanan kötü amaçlı yazılımlarla ilgili bilgileri görüntüleyebilir, ancak [SharePoint, OneDrive ve Microsoft Teams için Kasa Ekleri](mdo-for-spo-odb-and-teams.md) tarafından algılanan kötü amaçlı dosyalar hakkındaki bilgileri görüntüleyebilir.

Rapor, kötü amaçlı yazılımdan koruma altyapısı tarafından engellenen dosyalar veya web sitesi adresleri (URL'ler), [sıfır saatlik otomatik temizleme (ZAP](zero-hour-auto-purge.md)) ve [Kasa Bağlantıları](safe-links.md), [Kasa Ekleri](safe-attachments.md) ve [kimlik avı önleme ilkelerindeki kimliğe bürünme koruması özellikleri gibi Office 365 için Defender özellikleri gibi kötü amaçlı içeriğe sahip e-posta iletilerinin](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) sayısını sağlar. Eğilimleri belirlemek veya kuruluş ilkelerinin ayarlanması gerekip gerekmediğini belirlemek için bu bilgileri kullanabilirsiniz.

**Not**: Bir ileti beş alıcıya gönderiliyorsa bunu tek bir ileti değil beş farklı ileti olarak saymamızı anlamak önemlidir.

Raporu Microsoft 365 Defender portalında görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **Tehdit koruması durumunu** bulun ve **ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için aşağıdaki URL'lerden birini açın:

- Office 365 için Defender:<https://security.microsoft.com/reports/TPSAggregateReportATP>
- EOP: <https://security.microsoft.com/reports/TPSAggregateReport>

:::image type="content" source="../../media/threat-protection-status-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Tehdit koruması durumu pencere öğesi" lightbox="../../media/threat-protection-status-report-widget.png":::

Grafik varsayılan olarak son 7 güne ilişkin verileri gösterir. **Tehdit koruması durumu raporu** sayfasında **Filtre'ye** tıklarsanız, 90 günlük bir tarih aralığı seçebilirsiniz (deneme abonelikleri 30 günle sınırlı olabilir). Ayrıntılar tablosu 30 gün boyunca filtrelemeye izin verir.

Kullanılabilir görünümler aşağıdaki bölümlerde açıklanmıştır.

### <a name="view-data-by-overview"></a>Genel Bakış'a göre verileri görüntüleme

:::image type="content" source="../../media/threat-protection-status-report-overview-view.png" alt-text="Tehdit koruması durum raporundaki Genel Bakış görünümü" lightbox="../../media/threat-protection-status-report-overview-view.png":::

**Verileri Genel Bakışa Göre Görüntüle** görünümünde, grafikte aşağıdaki algılama bilgileri gösterilir:

- **E-posta kötü amaçlı yazılımı**
- **E-posta kimlik avı**
- **İstenmeyen e-posta**
- **İçerik kötü amaçlı yazılımı**

Grafiğin altında hiçbir ayrıntı tablosu yoktur.

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**.
- **Algılama**:
  - **E-posta kötü amaçlı yazılımı**
  - **E-posta kimlik avı**
  - **İstenmeyen e-posta**
  - **İçerik kötü amaçlı yazılımı**
- **Korumalı:** **MDO** (Office 365 için Defender) ve **EOP**.
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil). Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

### <a name="view-data-by-email--phish-and-chart-breakdown-by-detection-technology"></a>Verileri Algılama Teknolojisine göre E-posta \> Kimlik Avı ve Grafik dökümü ile görüntüleme

:::image type="content" source="../../media/threat-protection-status-report-phishing-detection-tech-view.png" alt-text="Tehdit koruması durum raporundaki kimlik avı e-postası için Algılama teknolojisi görünümü" lightbox="../../media/threat-protection-status-report-phishing-detection-tech-view.png":::

> [!NOTE]
> Mayıs 2021'den itibaren e-postadaki kimlik avı algılamaları, kimlik avı **URL'leri içeren ileti eklerini** içerecek şekilde güncelleştirildi. Bu değişiklik algılama biriminin bir bölümünü **E-posta Kötü Amaçlı Yazılımlarına Göre Görüntüle görünümünden ve Verileri E-posta \>** **\> Kimlik Avı ile görüntüle** görünümüne kaydırabilir. Başka bir deyişle, geleneksel olarak kötü amaçlı yazılım olarak tanımlanan kimlik avı URL'lerine sahip ileti ekleri artık kimlik avı olarak tanımlanabilir.

Verileri **E-posta \> Kimlik Avına göre görüntüle** ve **Algılama Teknolojisine göre Grafik dökümü** görünümünde, grafikte aşağıdaki bilgiler gösterilir:

- **URL kötü amaçlı itibarı**<sup>\*</sup>: Diğer Microsoft 365 müşterilerinde Office 365 için Defender patlamalardan oluşturulan kötü amaçlı URL itibarı.
- **Gelişmiş filtre**: Makine öğrenmesini temel alan kimlik avı sinyalleri.
- **Genel filtre**: Analist kurallarına göre kimlik avı sinyalleri.
- **Kuruluş içi kimlik sahtekarı**: Gönderen, alıcı etki alanını sahtekarlık yapmaya çalışıyor.
- **Dış etki alanını sahtekarlık** etme: Gönderen başka bir etki alanı sahtekarlığına çalışıyor.
- **Kimlik sahtekarlığı DMARC**: İletilerde DMARC kimlik doğrulaması hatası.
- **Kimliğe bürünme markası**: Gönderenlere göre iyi bilinen markaların kimliğine bürünme.
- **Karma analiz algılama**
- **Dosya saygınlığı**
- **Parmak izi eşleştirme**
- **URL'nin patlatılmasıyla ilgili saygınlık**<sup>\*</sup>
- **URL patlama**<sup>\*</sup>
- **Kimliğe bürünme kullanıcısı**<sup>\*</sup>
- **Kimliğe bürünme etki alanı**<sup>\*</sup>: Müşterinin sahip olduğu veya tanımladığı etki alanlarının kimliğine bürünme.
- **Posta kutusu zekası**<sup>\*</sup> kimliğe bürünme: Yönetici tarafından tanımlanan veya posta kutusu zekası aracılığıyla öğrenilen kullanıcıların kimliğine bürünme.
- **Dosya patlama**<sup>\*</sup>
- **Dosya patlatıcının itibarı**<sup>\*</sup>
- **Kampanya**<sup>\*</sup>

<sup>\*</sup>Yalnızca Office 365 için Defender

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Algılama teknolojisi**
- **Teslim durumu**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: Grafiktekiyle aynı değerler.
- **Korumalı:** **MDO** (Office 365 için Defender) veya **EOP**
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü** veya belirtilen ilke.
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="view-data-by-email--spam-and-chart-breakdown-by-detection-technology"></a>Verileri Algılama Teknolojisine göre E-posta İstenmeyen Posta \> ve Grafik dökümüyle görüntüleme

:::image type="content" source="../../media/threat-protection-status-report-spam-detection-tech-view.png" alt-text="Tehdit koruması durum raporundaki istenmeyen postalar için algılama teknolojisi görünümü" lightbox="../../media/threat-protection-status-report-spam-detection-tech-view.png":::

Verileri **E-posta İstenmeyen Posta \> ile görüntüle** ve **Algılama Teknolojisine Göre Grafik dökümü** görünümünde, grafikte aşağıdaki bilgiler gösterilir:

- **URL kötü amaçlı itibarı**
- **Gelişmiş filtre**
- **Genel filtre**
- **Karma analiz algılama**: İletinin kararına birden çok filtre katkıda bulundu.
- **Parmak izi eşleştirme**: İleti, önceki iletiler nedeniyle kötü olarak işaretlendi.
- **Etki alanı itibarı**: Bu ileti, gönderenin etki alanı itibarına bağlı olarak istenmeyen posta olarak kabul edildi.
- **Toplu**: Kullanıcı için toplu ayarı aştığı algılanan öğeler.
- **IP saygınlığı**: İleti, gönderen IP adresi itibarına bağlı olarak istenmeyen posta olarak kabul edildi.

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Algılama teknolojisi**
- **Teslim durumu**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: Grafiktekiyle aynı değerler.
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü** veya belirtilen ilke.
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="view-data-by-email--malware-and-chart-breakdown-by-detection-technology"></a>Verileri Algılama Teknolojisine göre E-posta \> Kötü Amaçlı Yazılımlarına ve Grafik dökümlerine göre görüntüleme

:::image type="content" source="../../media/threat-protection-status-report-malware-detection-tech-view.png" alt-text="Tehdit koruması durum raporundaki kötü amaçlı yazılımlar için algılama teknolojisi görünümü" lightbox="../../media/threat-protection-status-report-malware-detection-tech-view.png":::

> [!NOTE]
> Mayıs 2021'den itibaren, e-postadaki kötü amaçlı yazılım algılamaları ileti eklerine **zararlı URL'ler** içerecek şekilde güncelleştirildi. Bu değişiklik, algılama biriminin bir bölümünü **Verileri E-posta Kimlik Avı görünümü dışında ve Verileri E-posta \>** **\> Kötü Amaçlı Yazılımlarına Göre Görüntüle** görünümüne kaydırabilir. Başka bir deyişle, artık geleneksel olarak kimlik avı olarak tanımlanan ileti eklerindeki zararlı URL'ler kötü amaçlı yazılım olarak tanımlanabilir.

Verileri **E-posta \> Kötü Amaçlı Yazılımlarına Göre Görüntüle** ve **Algılama Teknolojisine Göre Grafik dökümü** görünümünde, grafikte aşağıdaki bilgiler gösterilir:

- **Dosya patlama**<sup>\*</sup>: Kasa Eklerine göre algılama.
- **Dosya patlama itibarı**<sup>\*</sup>: Office 365 için Defender patlamalar tarafından oluşturulan tüm kötü amaçlı dosya itibarı.
- **Dosya saygınlığı**
- **Kötü amaçlı yazılımdan koruma altyapısı**<sup>\*</sup>: Kötü amaçlı yazılımdan koruma altyapılarından algılama.
- **Kötü amaçlı yazılımdan koruma ilkesi dosya türü bloğu**: Bunlar, iletide tanımlanan kötü amaçlı dosya türü nedeniyle filtrelenen e-posta iletileridir.
- **URL kötü amaçlı itibarı**<sup>\*</sup>
- **URL patlama**<sup>\*</sup>
- **URL'nin patlatılmasıyla ilgili saygınlık**<sup>\*</sup>
- **Kampanya**<sup>\*</sup>

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Algılama teknolojisi**
- **Teslim Durumu**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: Grafiktekiyle aynı değerler.
- **Korumalı:** **MDO** (Office 365 için Defender) veya **EOP**
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü** veya belirtilen ilke.
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Koruma durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="chart-breakdown-by-policy-type"></a>İlke türüne göre grafik dökümü

:::image type="content" source="../../media/threat-protection-status-report-phishing-policy-type-view.png" alt-text="Tehdit koruması durum raporundaki kimlik avı e-postası, istenmeyen e-posta veya kötü amaçlı yazılım e-postası için İlke türü görünümü" lightbox="../../media/threat-protection-status-report-phishing-policy-type-view.png":::

**Verileri E-posta \> Kimlik Avına Göre Görüntüle**, **E-posta İstenmeyen E-postaya \> Göre Görüntüle** veya **E-posta \> Kötü Amaçlı Yazılım görünümlerine göre verileri görüntüle** görünümlerinde, **İlke türüne göre Grafik dökümü'nü** seçtiğinizde grafikte aşağıdaki bilgiler gösterilir:

- **Kötü amaçlı yazılımdan koruma**
- **ekleri Kasa**<sup>\*</sup>
- **Kimlik avı önleme**
- **Antispam**
- **Posta akışı kuralı** (taşıma kuralı olarak da bilinir)
- **Diğer**

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Algılama teknolojisi**
- **Teslim durumu**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**:
  - **URL kötü amaçlı itibarı**<sup>\*</sup>: Diğer Microsoft 365 müşterilerinde Office 365 için Defender patlamalardan oluşturulan kötü amaçlı URL itibarı.
  - **Gelişmiş filtre**: Makine öğrenmesini temel alan kimlik avı sinyalleri.
  - **Genel filtre**: Analist kurallarına göre kimlik avı sinyalleri.
  - **Kuruluş içi kimlik sahtekarı**: Gönderen, alıcı etki alanını sahtekarlık yapmaya çalışıyor.
  - **Dış etki alanını sahtekarlık** etme: Gönderen başka bir etki alanı sahtekarlığına çalışıyor.
  - **Kimlik sahtekarlığı DMARC**: İletilerde DMARC kimlik doğrulaması hatası.
  - **Kimliğe bürünme markası**: Gönderenlere göre iyi bilinen markaların kimliğine bürünme.
  - **Karma analiz algılama**
  - **Dosya saygınlığı**
  - **Parmak izi eşleştirme**
  - **URL'nin patlatılmasıyla ilgili saygınlık**<sup>\*</sup>
  - **URL patlama**<sup>\*</sup>
  - **Kimliğe bürünme kullanıcısı**<sup>\*</sup>
  - **Kimliğe bürünme etki alanı**<sup>\*</sup>: Müşterinin sahip olduğu veya tanımladığı etki alanlarının kimliğine bürünme.
  - **Posta kutusu zekası**<sup>\*</sup> kimliğe bürünme: Yönetici tarafından tanımlanan veya posta kutusu zekası aracılığıyla öğrenilen kullanıcıların kimliğine bürünme.
  - **Dosya patlama**<sup>\*</sup>
  - **Dosya patlatıcının itibarı**<sup>\*</sup>
  - **Kampanya**<sup>\*</sup>
- **Korumalı:** **MDO** (Office 365 için Defender) veya **EOP**
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü** veya belirtilen ilke.
- **Alıcı**

<sup>\*</sup>Yalnızca Office 365 için Defender

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="chart-breakdown-by-delivery-status"></a>Teslimat durumuna göre grafik dökümü

:::image type="content" source="../../media/threat-protection-status-report-phishing-delivery-status-view.png" alt-text="Tehdit koruması durum raporundaki kimlik avı e-postası ve kötü amaçlı yazılım e-postası için Teslim durumu görünümü" lightbox="../../media/threat-protection-status-report-phishing-delivery-status-view.png":::

**Verileri E-posta \> Kimlik Avına Göre Görüntüle**, **Verileri E-posta İstenmeyen Postayla \> Görüntüle** veya **E-posta \> Kötü Amaçlı Yazılım görünümlerine göre görüntüle** görünümlerinde **, Teslim durumuna göre Grafik dökümü'nü** seçtiğinizde grafikte aşağıdaki bilgiler gösterilir:

- **Barındırılan posta kutusu: Gelen Kutusu**
- **Barındırılan posta kutusu: Gereksiz**
- **Barındırılan posta kutusu: Özel klasör**
- **Barındırılan posta kutusu: Silinmiş Öğeler**
- **Iletilen**
- **Şirket içi sunucu: Teslim edildi**
- **Karantina**
- **Teslim başarısız oldu**
- **Düştü**

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Algılama teknolojisi**
- **Teslim durumu**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**:
  - **URL kötü amaçlı itibarı**<sup>\*</sup>: Diğer Microsoft 365 müşterilerinde Office 365 için Defender patlamalardan oluşturulan kötü amaçlı URL itibarı.
  - **Gelişmiş filtre**: Makine öğrenmesini temel alan kimlik avı sinyalleri.
  - **Genel filtre**: Analist kurallarına göre kimlik avı sinyalleri.
  - **Kuruluş içi kimlik sahtekarı**: Gönderen, alıcı etki alanını sahtekarlık yapmaya çalışıyor.
  - **Dış etki alanını sahtekarlık** etme: Gönderen başka bir etki alanı sahtekarlığına çalışıyor.
  - **Kimlik sahtekarlığı DMARC**: İletilerde DMARC kimlik doğrulaması hatası.
  - **Kimliğe bürünme markası**: Gönderenlere göre iyi bilinen markaların kimliğine bürünme.
  - **Karma analiz algılama**
  - **Dosya saygınlığı**
  - **Parmak izi eşleştirme**
  - **URL'nin patlatılmasıyla ilgili saygınlık**<sup>\*</sup>
  - **URL patlama**<sup>\*</sup>
  - **Kimliğe bürünme kullanıcısı**<sup>\*</sup>
  - **Kimliğe bürünme etki alanı**<sup>\*</sup>: Müşterinin sahip olduğu veya tanımladığı etki alanlarının kimliğine bürünme.
  - **Posta kutusu zekası**<sup>\*</sup> kimliğe bürünme: Yönetici tarafından tanımlanan veya posta kutusu zekası aracılığıyla öğrenilen kullanıcıların kimliğine bürünme.
  - **Dosya patlama**<sup>\*</sup>
  - **Dosya patlatıcının itibarı**<sup>\*</sup>
  - **Kampanya**<sup>\*</sup>
- **Korumalı:** **MDO** (Office 365 için Defender) veya **EOP**
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **Güvenli Ekleri Kaydetme**
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü** veya belirtilen ilke.
- **Alıcı**

<sup>\*</sup>Yalnızca Office 365 için Defender

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="view-data-by-content--malware"></a>İçerik \> Kötü Amaçlı Yazılımlarına göre verileri görüntüleme

:::image type="content" source="../../media/threat-protection-status-report-content-malware-view.png" alt-text="Tehdit koruması durum raporundaki İçerik kötü amaçlı yazılım görünümü" lightbox="../../media/threat-protection-status-report-content-malware-view.png":::

**verileri İçerik \> Kötü Amaçlı Yazılımlarına Göre Görüntüle** görünümünde, Office 365 için Microsoft Defender kuruluşlara yönelik grafikte aşağıdaki bilgiler gösterilir:

- **Kötü amaçlı yazılımdan koruma altyapısı**: Microsoft 365 yerleşik [virüs algılaması](virus-detection-in-spo.md) tarafından SharePoint, OneDrive ve Microsoft Teams kötü amaçlı dosyalar algılandı.
- **MDO patlama**: [SharePoint, OneDrive ve Microsoft Teams için Kasa Ekleri](mdo-for-spo-odb-and-teams.md) tarafından algılanan kötü amaçlı dosyalar.
- **Dosya saygınlığı**

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih (UTC)**
- **Ek dosya adı**
- **Iş yük -ünü**
- **Algılama teknolojisi**
- **Dosya boyutu**
- **Son değiştirme kullanıcısı**

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: **Kötü amaçlı yazılımdan koruma altyapısı**, **MDO patlama** ve **Dosya patlama**
- **İş yükü**: **Teams**, **SharePoint** ve **OneDrive**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

### <a name="view-data-by-system-override-and-chart-breakdown-by-reason"></a>Verileri Sistem geçersiz kılmaya göre görüntüleme ve Nedene göre Grafik dökümü

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png" alt-text="Tehdit koruması durum raporundaki Neden görünümüne göre İleti geçersiz kılma ve Grafik dökümü" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png":::

**Sistem geçersiz kılmaya göre verileri görüntüle** ve **Nedene göre grafik dökümü** görünümünde, grafikte aşağıdaki geçersiz kılma nedeni bilgileri gösterilir:

- **Şirket içi atlama**
- **IP'ye izin ver**
- **Exchange aktarım kuralı** (posta akışı kuralı)
- **Kuruluşa izin verilen gönderenler**
- **Kuruluşa izin verilen etki alanları**
- **ZAP etkin değil**
- **Kullanıcı Kasa Göndereni**
- **Kullanıcı Kasa Etki Alanı**
- **Kimlik avı simülasyonu**: Daha fazla bilgi için bkz. [Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma](configure-advanced-delivery.md).
- **Üçüncü taraf filtresi**

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Sistem geçersiz kılma**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Neden**: Grafikle aynı değerler.
- **Teslim Konumu**: **Gereksiz Posta klasörü etkin değil** veya **SecOps posta kutusu**.
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**: **Tümü**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü**
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktar](#export-report)** düğmesi kullanılabilir.

### <a name="view-data-by-system-override-and-chart-breakdown-by-delivery-location"></a>Verileri Sistem geçersiz kılmaya göre görüntüleme ve Teslim konumuna göre Grafik dökümü

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png" alt-text="Tehdit koruması durum raporunda İleti geçersiz kılma ve Teslim Konumuna göre Grafik dökümü" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png":::

**Verileri Sistem geçersiz kılmaya göre görüntüle** ve **Teslim konumuna göre Grafik dökümü** görünümünde, grafikte aşağıdaki geçersiz kılma nedeni bilgileri gösterilir:

- **Gereksiz Posta klasörü etkin değil**
- **SecOps posta kutusu**: Daha fazla bilgi için bkz. [Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma](configure-advanced-delivery.md).

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih**
- **Konu**
- **Gönderen**
- **Alıcı**
- **Sistem geçersiz kılma**
- **Gönderen IP'i**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Tarih (UTC)** **Başlangıç tarihi** ve **Bitiş tarihi**
- **Neden**
  - **Şirket içi atlama**
  - **IP'ye izin ver**
  - **Exchange aktarım kuralı** (posta akışı kuralı)
  - **Kuruluşa izin verilen gönderenler**
  - **Kuruluşa izin verilen etki alanları**
  - **ZAP etkin değil**
  - **Kullanıcı Kasa Göndereni**
  - **Kullanıcı Kasa Etki Alanı**
  - **Kimlik avı simülasyonu**: Daha fazla bilgi için bkz. [Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma](configure-advanced-delivery.md).
  - **Üçüncü taraf filtresi**
- **Teslim Konumu**: **Gereksiz Posta klasörü etkin değil** veya **SecOps posta kutusu**.
- **Yön**:
  - **Tüm**
  - **Gelen**
  - **Giden**
- **Etiket**: **Tümü** veya belirtilen kullanıcı etiketi (öncelik hesapları dahil). Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).
- **Etki alanı**: **Tümü** veya [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **İlke türü**:
  - **Tüm**
  - **Kötü amaçlı yazılımdan koruma**
  - **ekleri Kasa**<sup>\*</sup>
  - **Kimlik avı önleme**
  - **Antispam**
  - **Posta akışı kuralı** (aktarım kuralı)
  - **Diğer**
- **İlke adı (yalnızca ayrıntılar tablo görünümü)**: **Tümü**
- **Alıcı**

<sup>\*</sup>Yalnızca Office 365 için Defender

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**Tehdit koruması durumu** sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktar](#export-report)** düğmesi kullanılabilir.

## <a name="top-malware-report"></a>En iyi kötü amaçlı yazılım raporu

**En iyi kötü amaçlı yazılım** raporu [, EOP'de kötü amaçlı](anti-malware-protection.md) yazılımdan koruma tarafından algılanan çeşitli kötü amaçlı yazılım türlerini gösterir.

Raporu Microsoft 365 Defender portalında görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **En iyi kötü amaçlı yazılım'ı** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/TopMalware>.

:::image type="content" source="../../media/top-malware-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki en iyi kötü amaçlı yazılım pencere öğesi" lightbox="../../media/top-malware-report-widget.png":::

Pasta grafikte bir kümenin üzerine geldiğinizde, bir tür kötü amaçlı yazılımın adını ve bu kötü amaçlı yazılıma sahip olarak algılanan ileti sayısını görebilirsiniz.

**En iyi kötü amaçlı yazılım raporu** sayfasında pasta grafiğin daha büyük bir sürümü görüntülenir. Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **En iyi kötü amaçlı yazılım**
- **Sayısı**

**Filtre'ye** tıklarsanız **Başlangıç tarihi** ve **Bitiş tarihi** içeren bir tarih aralığı belirtebilirsiniz.

**En iyi kötü amaçlı yazılım** sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama ve](#schedule-report)** ![Dışarı Aktar simgesi oluşturun.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](#export-report)** düğmeleri kullanılabilir.

:::image type="content" source="../../media/top-malware-report-view.png" alt-text="En iyi kötü amaçlı yazılım rapor görünümü" lightbox="../../media/top-malware-report-view.png":::

## <a name="top-senders-and-recipients-report"></a>En çok gönderenler ve alıcılar raporu

**En çok gönderenler ve alıcılar** raporu hem EOP hem de Office 365 için Defender kullanılabilir; ancak raporlar farklı veriler içerir. Örneğin, EOP müşterileri en çok kötü amaçlı yazılım, istenmeyen posta ve kimlik avı (kimlik sahtekarlığı) alıcılarıyla ilgili bilgileri görüntüleyebilir ancak [Kasa Ekler](safe-attachments.md) veya [kimlik avı koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) tarafından algılanan kötü amaçlı yazılımlarla ilgili bilgileri görüntüleyemez.

**En çok gönderenler ve alıcılar**, kuruluşunuzdaki en çok gönderenlerin yanı sıra EOP ve Office 365 için Defender koruma özellikleri tarafından algılanan iletiler için en çok kullanılan alıcıları gösterir. Varsayılan olarak, raporda geçen haftanın verileri gösterilir, ancak son 90 güne ilişkin veriler kullanılabilir.

Raporu adresinden Microsoft 365 Defender portalında <https://security.microsoft.com>görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **, En çok gönderenler ve alıcılar raporunu bulun ve** **ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için aşağıdaki URL'lerden birini açın:

- Office 365 için Defender:<https://security.microsoft.com/reports/TopSenderRecipientsATP>
- EOP: <https://security.microsoft.com/reports/TopSenderRecipient>

:::image type="content" source="../../media/top-senders-and-recipients-widget.png" alt-text="Raporlar panosundaki En çok gönderenler ve alıcılar pencere öğesi" lightbox="../../media/top-senders-and-recipients-widget.png":::

Pasta grafikte bir kamanın üzerine geldiğinizde, gönderenin veya alıcının ileti sayısını görebilirsiniz.

**En çok gönderenler ve alıcılar** sayfasında pasta grafiğin daha büyük bir sürümü görüntülenir. Aşağıdaki grafikler kullanılabilir:

- **En çok gönderenler için verileri göster** (bu varsayılan görünümdür)
- **En çok posta alıcıları için verileri gösterme**
- **En çok istenmeyen posta alıcıları için verileri gösterme**
- **En iyi kötü amaçlı yazılım alıcıları için verileri gösterme** (EOP)
- **En çok kimlik avı alıcıları için verileri gösterme**
- **En çok kötü amaçlı yazılım alıcıları için verileri gösterme (MDO)**
- **En çok kimlik avı alıcıları için verileri gösterme (MDO)**

Veriler seçiminize göre değişir.

Pasta grafikte bir kamanın üzerine geldiğinizde, ilgili gönderenin veya alıcının ileti sayısını görebilirsiniz.

Grafiğin altındaki ayrıntılar tablosu, seçtiğiniz görünüme göre gönderenleri veya alıcıları ve ileti sayılarını gösterir.

**Filtre'ye** tıklayıp **Başlangıç tarihi** ve **Bitiş tarihi'ni** seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz. Kullanıcılar ayrıca kullanıcı etiketlerine göre filtreleyebilir. 

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

**En çok gönderenler ve alıcılar** sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **Dışarı aktar** düğmesi kullanılabilir.

:::image type="content" source="../../media/top-senders-and-recipients-report-view.png" alt-text="En çok gönderenler ve alıcılar raporunda En çok gönderenler için verileri göster görünümü" lightbox="../../media/top-senders-and-recipients-report-view.png":::

## <a name="url-protection-report"></a>URL koruma raporu

**URL koruma raporu** yalnızca Office 365 için Microsoft Defender kullanılabilir. Daha fazla bilgi için bkz. [URL koruma raporu](view-reports-for-mdo.md#url-protection-report).

## <a name="user-reported-messages-report"></a>Kullanıcı tarafından bildirilen iletiler raporu

> [!IMPORTANT]
> **Kullanıcı tarafından bildirilen iletiler** raporunun düzgün çalışması için, Microsoft 365 ortamınızda **denetim günlüğünün açık olması gerekir**. Bu genellikle Exchange Online'de Denetim Günlükleri rolü atanmış biri tarafından gerçekleştirilir. Daha fazla bilgi için bkz[. Denetim günlüğü aramasını Microsoft 365 açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

**Kullanıcı tarafından bildirilen iletiler** raporu, kullanıcıların Gereksiz olarak bildirdiği e-posta iletileri, kimlik avı girişimleri veya [Rapor İletisi eklentisini veya Rapor](enable-the-report-message-add-in.md) [Kimlik Avı eklentisini](enable-the-report-phish-add-in.md) kullanarak iyi postalar hakkındaki bilgileri gösterir.

Raporu Microsoft 365 Defender portalında görüntülemek için **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** sayfasında **, Kullanıcı tarafından bildirilen iletileri** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/userSubmissionReport>. [Microsoft 365 Defender portalında yönetici gönderimlerine](admin-submission.md) gitmek **için Gönderimlere Git'e** tıklayın.

:::image type="content" source="../../media/user-reported-messages-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki kullanıcı tarafından bildirilen iletiler pencere öğesi" lightbox="../../media/user-reported-messages-widget.png":::

**Filtre'ye** tıklayıp görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek hem grafiği hem de ayrıntılar tablosunu filtreleyebilirsiniz:

- **Bildirilen tarih**: **Başlangıç saati** ve **Bitiş saati**
- **Rapor eden**
- **E-posta konusu**
- **İleti bildirilen kimlik**
- **Ağ İletisi Kimliği**
- **Gönderen**
- **Bildirilen neden**
  - **Gereksiz değil**
  - **Phish**
  - **Spam**
- **Kimlik avı benzetimi**: **Evet** veya **Hayır**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Girişleri gruplandırmak için **Gruplandır'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:

- **Hiçbiri**
- **Neden**
- **Gönderen**
- **Rapor eden**
- **Sonucu yeniden tara**
- **Kimlik avı benzetimi**

:::image type="content" source="../../media/user-reported-messages-report.png" alt-text="Kullanıcı tarafından bildirilen iletiler raporu" lightbox="../../media/user-reported-messages-report.png":::

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **E-posta konusu**
- **Rapor eden**
- **Bildirilen tarih**
- **Gönderen**
- **Bildirilen neden**
- **Sonucu yeniden tara**
- **Etiketler**: Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

Analiz için Microsoft'a ileti göndermek için tablodan ileti girişini seçin, **analiz için Microsoft'a gönder'e** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:

- **Rapor temizleme**
- **Kimlik avı bildirme**
- **Kötü amaçlı yazılımları bildirme**
- **İstenmeyen posta bildir**'
- **Araştırmayı tetikleme** (Office 365 için Defender)

**Kullanıcı tarafından bildirilen iletiler** sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktar](#export-report)** düğmesi kullanılabilir.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Bu raporları görüntülemek için hangi izinler gerekiyor?

Bu makalede açıklanan raporları görüntülemek ve kullanmak için Microsoft 365 Defender portalında aşağıdaki rol gruplarından birinin üyesi olmanız gerekir:

- **Kuruluş Yönetimi**
- **Güvenlik Yöneticisi**
- **Güvenlik Okuyucusu**
- **Genel Okuyucu**

Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

**Not**: kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Raporlarda veri gösterilmiyorsa ne olur?

Raporlarınızda veri görmüyorsanız, kullandığınız filtreleri denetleyin ve ilkelerinizin doğru ayarlanıp ayarlanmadığını bir kez daha denetleyin. Daha fazla bilgi edinmek için bkz [. Tehditlere karşı koruma](protect-against-threats.md).

## <a name="schedule-report"></a>Raporu zamanla

1. Belirli bir raporun ana sayfasında Zamanlama oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Zamanlama oluşturun**.
2. **Zamanlanmış rapor oluşturma** sihirbazı açılır. **Zamanlanan ad raporu** sayfasında **Ad** değerini gözden geçirin veya özelleştirin ve ardından **İleri'ye** tıklayın.
3. **Tercihleri ayarla** sayfasında aşağıdaki ayarları yapılandırın:
   - **Sıklık**: Aşağıdaki değerlerden birini seçin:
     - **Haftalık** (varsayılan)
     - **Aylık**
   - **Başlangıç tarihi**: Raporun oluşturulması başladığında. Varsayılan değer bugündür.
   - **Süre sonu tarihi**: Raporun oluşturulmasının sona ermesi. Varsayılan değer bugünden itibaren bir yıldır.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Alıcılar** sayfasında rapor için alıcıları seçin. Varsayılan değer e-posta adresinizdir, ancak başkalarını ekleyebilirsiniz.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Gözden Geçir** sayfasında seçimlerinizi gözden geçirin. Değişiklik yapmak için ilgili bölümlerde **Geri** düğmesine veya **Düzenle** bağlantısına tıklayabilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

### <a name="managed-existing-scheduled-reports"></a>Yönetilen mevcut zamanlanmış raporlar

Önceden oluşturduğunuz zamanlanmış raporları yönetmek için aşağıdaki adımları uygulayın:

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Raporlar'a** \> gidin **, E-posta'yı genişletin & işbirliği** \> **için Zamanlamaları yönet'i** seçin.

   Doğrudan **Zamanlamaları yönet** sayfasına gitmek için kullanın <https://security.microsoft.com/ManageSubscription>.

2. **Zamanlamaları yönet** sayfasında, zamanlanan her rapor için aşağıdaki bilgiler gösterilir:
   - **Başlangıç tarihini zamanlama**
   - **Zamanlama adı**
   - **Rapor türü**
   - **Frekans**
   - **Son gönderilen**

   Değiştirmek istediğiniz mevcut zamanlanmış raporu bulun.

3. Zamanlanmış raporu seçtikten sonra açılan ayrıntılar açılır öğesinde aşağıdaki eylemlerden birini yapın:
   - **Adı düzenle**: Bu düğmeye tıklayın, görüntülenen açılır öğede raporun adını değiştirin ve **kaydet'e** tıklayın.
   - **Zamanlamayı sil**: Bu düğmeye tıklayın, görüntülenen uyarıyı okuyun (önceki raporlar artık indirilemez) ve ardından **Kaydet'e** tıklayın.
   - **Zamanlama ayrıntıları** bölümü: Aşağıdaki ayarları değiştirmek için **Tercihleri düzenle'ye** tıklayın:
     - **Sıklık**: **Haftalık** veya **Aylık**
     - **Başlangıç tarihi**
     - **Süre sonu tarihi**

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Alıcılar** bölümü: Zamanlanmış rapora alıcı eklemek veya kaldırmak için Alıcıları **düzenle'ye** tıklayın. İşiniz bittiğinde **Kaydet'e** tıklayın

   İşlemi tamamladığınızda, **Kapat**'a tıklayın.

## <a name="request-report"></a>İstek raporu

1. Belirli bir raporun ana sayfasında Rapor iste simgesine tıklayın ![.](../../media/m365-cc-sc-download-icon.png) **Rapor iste**.
2. **İsteğe bağlı rapor oluşturma** sihirbazı açılır. **İsteğe bağlı ad raporu** sayfasında **Ad değerini gözden** geçirin veya özelleştirin ve ardından **İleri'ye** tıklayın.
3. **Tercihleri ayarla** sayfasında aşağıdaki ayarları gözden geçirin veya yapılandırın:
   - **Başlangıç tarihi**: Raporun oluşturulması başladığında. Varsayılan değer bir ay öncedir.
   - **Süre sonu tarihi**: Raporun oluşturulmasının sona ermesi. Varsayılan değer bugündür.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Alıcılar** sayfasında rapor için alıcıları seçin. Varsayılan değer e-posta adresinizdir, ancak başkalarını ekleyebilirsiniz.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Gözden Geçir** sayfasında seçimlerinizi gözden geçirin. Değişiklik yapmak için ilgili bölümlerde **Geri** düğmesine veya **Düzenle** bağlantısına tıklayabilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

6. Rapor başarıyla oluşturulduktan sonra Yeni **isteğe bağlı rapor oluşturuldu** sayfasına yönlendirilirsiniz. Burada **Başka bir rapor oluştur'a** veya **Bitti'ye** tıklayabilirsiniz.

   Rapor, sonraki bölümde açıklandığı gibi **İndirme raporları** sayfasında da kullanılabilir.

### <a name="download-reports"></a>Raporları indirme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Raporlar'a** \> gidin **, E-posta'yı genişletin & işbirliği** \> için **İndirme raporları'nı** seçin.

   İndirme raporları sayfasına doğrudan gitmek **için** kullanın <https://security.microsoft.com/ReportsForDownload>.

2. **İndirme raporları** sayfasında, kullanılabilir her rapor için aşağıdaki bilgiler gösterilir:
   - **Başlangıç tarihi**
   - **Ad**
   - **Rapor türü**
   - **Son gönderilen**
   - **Yön**

   İndirmek istediğiniz raporu bulun ve seçin.

## <a name="export-report"></a>Raporu dışarı aktarma

Belirli bir raporun ana sayfasında Dışarı Aktar simgesine tıklayın ![.](../../media/m365-cc-sc-download-icon.png) **Dışarı aktar** (bu bağlantı varsa). Aşağıdaki ayarları yapılandırabileceğiniz dışarı **aktarma koşulları** açılır öğesi görüntülenir:

- **Dışarı aktaracak bir görünüm seçin**: Aşağıdaki değerlerden birini seçin:
  - **Özet**: Son 90 gün için veriler kullanılabilir.
  - **Ayrıntılar**: Veriler son 30 gün için kullanılabilir.
- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**.

Filtreleri yapılandırmayı bitirdiğinizde **Dışarı Aktar'a** tıklayın. Açılan iletişim kutusunda, dosyayı açmayı, dosyayı kaydetmeyi veya seçimi anımsamayı seçebilirsiniz.

Dışarı aktarılan her .csv dosyası 150.000 satırla sınırlıdır. Veriler 150.000'den fazla satır içeriyorsa, birden çok .csv dosyası oluşturulur.

## <a name="related-topics"></a>İlgili konular

[EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md)

[EOP'de kötü amaçlı yazılımdan koruma](anti-malware-protection.md)

[Microsoft 365 Defender portalında akıllı raporlar ve içgörüler](reports-and-insights-in-security-and-compliance.md)

[Microsoft 365 Defender portalında posta akışı raporlarını görüntüleme](view-mail-flow-reports.md)

[Office 365 için Defender için raporları görüntüleme](view-reports-for-mdo.md)
