---
title: Office 365 için Defender raporlarını görüntüleme
f1.keywords:
- CSH
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
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler, Microsoft 365 Defender portalında bulunan Office 365 için Defender raporlarını bulmayı ve kullanmayı öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 551d2f0f2da872ff24da2bd0d691eea775894c08
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102580"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Office 365 için Defender raporları görüntüleme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Office 365 için Microsoft Defender kuruluşlar (örneğin, Microsoft 365 E5 abonelikler veya Office 365 için Microsoft Defender Plan 1 veya Office 365 için Microsoft Defender Plan 2 eklentileri) güvenlikle ilgili çeşitli raporlar içerir. [Gerekli izinlere](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports) sahipseniz bu raporları Microsoft 365 Defender portalında görüntüleyebilir ve indirebilirsiniz.

## <a name="view-and-download-reports"></a>Raporları görüntüleme ve indirme

### <a name="view-reports"></a>Raporları görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **Doğrudan E-posta & işbirliği raporları** sayfasına gitmek için kullanın<https://security.microsoft.com/emailandcollabreport>.

1. Görüntülemek istediğiniz raporu seçin ve ardından **Ayrıntıları görüntüle'yi** seçin.

### <a name="download-reports"></a>Raporları indirme

konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, İndirmek için** **Raporlar** > **E-posta & işbirliği** \> Raporları'na gidin. İndirme raporları sayfasına doğrudan gitmek **için** kullanın <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="Microsoft 365 Defender portalındaki E-posta & işbirliği raporları sayfası" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> Office 365 için Defender gerektirmeyen [e-posta güvenlik raporları, Microsoft 365 Defender portalında e-posta güvenlik raporlarını görüntüleme bölümünde](view-email-security-reports.md) açıklanmıştır.
>
> Posta akışıyla ilgili raporlar artık Exchange yönetim merkezindedir (EAC). Bu raporlar hakkında daha fazla bilgi için [bkz. Yeni Exchange yönetim merkezinde posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>Kasa Ekler dosya türleri raporu

> [!NOTE]
> Bu rapor kullanım dışı bırakıldı. Aynı bilgiler [Tehdit koruması durum raporunda](#threat-protection-status-report) da mevcuttur.

## <a name="safe-attachments-message-disposition-report"></a>Kasa Ekler ileti bırakma raporu

> [!NOTE]
> Bu rapor kullanım dışı bırakıldı. Aynı bilgiler [Tehdit koruması durum raporunda](#threat-protection-status-report) da mevcuttur.

## <a name="mail-latency-report"></a>Posta gecikme süresi raporu

**Posta gecikme süresi raporu**, kuruluşunuzda yaşanan posta teslimi ve patlama gecikmesinin toplam görünümünü gösterir. Hizmetteki posta teslim süreleri bir dizi faktörden etkilenir ve saniyelerdeki mutlak teslim süresi genellikle başarının veya sorunun iyi bir göstergesi değildir. Bir günde yavaş teslim süresi, başka bir günde ortalama teslim süresi olarak kabul edilebilir veya tam tersi olabilir. Bu, diğer iletilerin gözlemlenen teslim süreleri hakkındaki istatistiksel verilere göre ileti teslimini nitelemeye çalışır.

İstemci tarafı ve ağ gecikme süresi dahil değildir.

Raporu görüntülemek için adresinden Microsoft 365 Defender portalını <https://security.microsoft.com>açın. **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları** bölümüne gidin. **Doğrudan E-posta & işbirliği raporları** sayfasına gitmek için kullanın<https://security.microsoft.com/emailandcollabreport>.

**E-posta & işbirliği raporları** sayfasında **Posta gecikmesi raporunu** bulun ve **Ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için kullanın <https://security.microsoft.com/mailLatencyReport>.

:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki Posta gecikmesi raporu pencere öğesi" lightbox="../../media/mail-latency-report-widget.png":::

**Posta gecikmesi raporu** sayfasında, **Posta gecikmesi raporu** sayfasında aşağıdaki sekmeler bulunur:

- **50. yüzdebirlik** dilim: İleti teslim sürelerinin ortası budur. Bu değeri ortalama teslim süresi olarak düşünebilirsiniz. Bu sekme varsayılan olarak seçilidir.
- **90. yüzdebirlik** dilim: Bu, ileti teslimi için yüksek gecikme süresi olduğunu gösterir. İletilerin yalnızca %10'unun teslimi bu değerden uzun sürdü.
- **99. yüzdebirlik** dilim: Bu, ileti teslimi için en yüksek gecikme süresini gösterir.

Seçtiğiniz sekmeden bağımsız olarak grafik, iletileri aşağıdaki kategorilere göre düzenlenmiş olarak gösterir:

- **Genel**
- **Patlama**

Grafikte bir kategorinin üzerine geldiğinizde, her kategorideki gecikme süresinin dökümünü görebilirsiniz.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="Posta gecikme süresi raporunun 50. yüzdebirlik dilimler görünümü" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

**Filtre'ye** tıklarsanız, hem grafiği hem de ayrıntılar tablosunu aşağıdaki değerlere göre filtreleyebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **İleti görünümü**: Aşağıdaki değerlerden biri:
  - **Tüm iletiler**
  - **Patlatılan iletiler**: Aşağıdaki değerlerden biri:
    - **Satır içi patlama**: Teslimden önce tamamen test edilen iletileri içerir.
    - **Zaman uyumsuz patlama**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler bulunur:

- **Tarih (UTC)**
- **Gecikme**
- **İleti sayısı**
- **50. yüzdebirlik**
- **90. yüzdebirlik**
- **99. yüzdebirlik**

Ana rapor sayfasında Dışarı ![Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktar](view-email-security-reports.md#export-report)** düğmesi kullanılabilir.

## <a name="threat-protection-status-report"></a>Tehdit koruması durum raporu

**Tehdit koruması durum** raporu, Exchange Online Protection (EOP) ve [Office 365 için Microsoft Defender](exchange-online-protection-overview.md) tarafından algılanan ve engellenen kötü amaçlı içerik ve kötü amaçlı e-posta hakkındaki bilgileri bir araya getiren tek bir görünümdür. Daha fazla bilgi için bkz [. Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>En çok gönderenler ve alıcılar raporu

**En çok gönderenler ve alıcılar** raporu, EOP ve Office 365 için Defender koruma özellikleri için en çok kullanılan alıcıları gösterir. Daha fazla bilgi için bkz [. En çok gönderenler ve alıcılar raporu](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>URL koruma raporu

**URL koruma raporu**, Kasa [Bağlantıları'nın](safe-links.md) bir parçası olarak algılanan tehditler ve URL tıklamalarında gerçekleştirilen eylemler için özet ve eğilim görünümleri sağlar. Bu rapor, **Kullanıcı tıklamalarını izle** seçeneği belirlenmediğinde Kasa Bağlantıları ilkesinin uygulandığı kullanıcılardan gelen tıklama verilerine sahip olmayacaktır.

Raporu görüntülemek için [Microsoft 365 Defender portalını](https://security.microsoft.com) açın, **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları'na** gidin. **E-posta & işbirliği raporları** **sayfasında URL koruma sayfasını** bulun ve **ayrıntıları görüntüle'ye** tıklayın. Doğrudan rapora gitmek için dosyasını açın <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="E-posta & işbirliği raporları sayfasındaki URL koruma raporu pencere öğesi" lightbox="../../media/url-protection-report-widget.png":::

**URL koruma** raporu sayfasındaki kullanılabilir görünümler aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Bu bir *koruma eğilimi raporudur*, yani veriler daha büyük bir veri kümesindeki eğilimleri temsil eder. Sonuç olarak, grafiklerdeki veriler burada gerçek zamanlı olarak kullanılamaz, ancak ayrıntılar tablosundaki verilerdir, bu nedenle ikisi arasında küçük bir tutarsızlık görebilirsiniz. Grafikler dört saatte bir yenilenir ve son 90 güne ilişkin verileri içerir.

### <a name="view-data-by-url-click-protection-action"></a>URL tıklama koruması eylemine göre verileri görüntüleme

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="URL koruma raporunda URL tıklama koruma eylemi olarak görünen görünüm" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

**Verileri URL tıklaması ile görüntüle koruma eylem** görünümü, kuruluştaki kullanıcıların URL tıklamalarının sayısını ve tıklamanın sonuçlarını gösterir:

- **İzin verildi**: Tıklamalara izin verilir.
- **Kiracı yöneticisi tarafından izin verilir**: Kasa Bağlantıları ilkelerinde izin verilen tıklamalar.
- **Engellendi: Engellendi'ye** tıklayın.
- **Kiracı yöneticisi tarafından engellendi**: Kasa Bağlantıları ilkelerinde engellenen tıklamalar.
- **Engellendi ve tıklandı**: Kullanıcıların engellenen URL'ye tıkladığı engellenen tıklamalar.
- **Kiracı yöneticisi tarafından engellendi ve şu bağlantıya tıklandı**: Yönetici bağlantıyı engelledi, ancak kullanıcı bağlantıyı tıklatmış.
- **Tarama sırasında tıklanan**: Kullanıcıların URL'ye yönelik bekleyen tarama sayfasına tıkladığı yeri tıklar.
- **Bekleyen tarama**: Tarama kararını bekleyen URL'lere tıklar.

Tıklama, kullanıcının engelleme sayfasından kötü amaçlı web sitesine tıkladığını gösterir (yöneticiler Kasa Bağlantılar ilkeleri'nde tıklamayı devre dışı bırakabilir).

**Filtreler'e** tıklarsanız, görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek raporu ve ayrıntılar tablosunu değiştirebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **Eylem**:
  - **Izin verilen**
  - **Engellenen**
  - **Kiracı yöneticisi tarafından izin verilir**
  - **Engellendi ve tıklandı**
  - **Kiracı yöneticisi tarafından engellendi ve**
  - **Tarama sırasında tıklanan**
  - **Bekleyen tarama**
- **Etki alanları**: Rapor sonuçlarında listelenen URL etki alanları.
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Grafiğin altındaki ayrıntılar tablosu, kuruluş içinde son 7 gün boyunca gerçekleşen tüm tıklamaların neredeyse gerçek zamanlı görünümünü sağlar:

- **Tıklama zamanı**
- **Kullanıcı**
- **URL**
- **Eylem**
- **Uygulama**

Ana rapor sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](view-email-security-reports.md#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](view-email-security-reports.md#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](view-email-security-reports.md#export-report)** düğmeleri kullanılabilir.

### <a name="view-data-by-url-click-by-application"></a>Uygulamaya göre URL'ye tıklayarak verileri görüntüleme

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="URL koruma raporundaki URL tıklama koruması eylem görünümü" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

Verileri **URL'ye göre görüntüle görünümü,** Kasa Bağlantıları destekleyen uygulamalara göre URL tıklamalarının sayısını gösterir:

- **E-posta istemcisi**
- **Belgeyi Office**
- **Teams**

**Filtreler'e** tıklarsanız, görüntülenen açılır öğede aşağıdaki değerlerden birini veya daha fazlasını seçerek raporu ve ayrıntılar tablosunu değiştirebilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: Grafikten kullanılabilir uygulamalar.
- **Etki alanları**: Rapor sonuçlarında listelenen URL etki alanları.
- **Alıcı**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Grafiğin altındaki ayrıntılar tablosu, kuruluş içinde son 7 gün boyunca gerçekleşen tüm tıklamaların neredeyse gerçek zamanlı görünümünü sağlar:

- **Tıklama zamanı**
- **Kullanıcı**
- **URL**
- **Eylem**
- **Uygulama**

Ana rapor sayfasında Zamanlama ![oluştur simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](view-email-security-reports.md#schedule-report)**, ![Rapor iste simgesi.](../../media/m365-cc-sc-download-icon.png) **[İstek raporu](view-email-security-reports.md#request-report)** ve ![Dışarı Aktar simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı aktarma](view-email-security-reports.md#export-report)** düğmeleri kullanılabilir.

## <a name="additional-reports-to-view"></a>Görüntülemek için ek raporlar

Bu makalede açıklanan raporlara ek olarak, aşağıdaki tabloda açıklandığı gibi birkaç rapor daha mevcuttur:

|Rapor|Konu|
|---|---|
|**Explorer** (Office 365 için Microsoft Defender Plan 2) veya **gerçek zamanlı algılamalar** (Office 365 için Microsoft Defender Plan 1)|[Tehdit Gezgini (ve gerçek zamanlı algılamalar)](threat-explorer.md)|
|Office 365 için Defender gerektirmeyen e-posta güvenlik raporları|[Microsoft 365 Defender portalında e-posta güvenlik raporlarını görüntüleme](view-email-security-reports.md)|
|Exchange yönetim merkezinde (EAC) posta akışı raporları|[Yeni Exchange yönetim merkezinde posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

PowerShell raporlama cmdlet'leri:

|Rapor|Konu|
|---|---|
|En çok gönderenler ve alıcılar|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|En iyi kötü amaçlı yazılım|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Posta trafiği|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Güvenli Bağlantılar|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Güvenliği aşılmış kullanıcılar|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|Posta akışı durumu|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|Kimlik sahtekarlığına neden olan kullanıcılar|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Office 365 için Defender raporlarını görüntülemek için hangi izinler gereklidir?

Bu makalede açıklanan raporları görüntülemek ve kullanmak için Microsoft 365 Defender portalında aşağıdaki rol gruplarından birinin üyesi olmanız gerekir:

- **Kuruluş Yönetimi**
- **Güvenlik Yöneticisi**
- **Güvenlik Okuyucusu**
- **Genel Okuyucu**

Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

**Not**: kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Raporlarda veri gösterilmiyorsa ne olur?

Office 365 için Defender raporlarınızda veri görmüyorsanız ilkelerinizin doğru ayarlandığını bir kez daha denetleyin. Office 365 için Defender korumasının geçerli olması için kuruluşunuzun [Kasa Bağlantıları ilkeleri](set-up-safe-links-policies.md) ve Kasa [Ekleri ilkeleri](set-up-safe-attachments-policies.md) tanımlanmış olmalıdır. Ayrıca bkz [. istenmeyen posta önleme](anti-spam-protection.md) ve [kötü amaçlı yazılımdan koruma](anti-malware-protection.md).

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Defender portalında akıllı raporlar ve içgörüler](reports-and-insights-in-security-and-compliance.md)

[Yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference)
