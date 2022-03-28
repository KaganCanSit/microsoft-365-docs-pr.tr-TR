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
description: Yöneticiler, portalda yer alan Office 365 için Defender'ı nasıl bulup kullanabileceğini Microsoft 365 Defender.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7532d5be8febda1b4dc4dfc0a0860516188ecfc5
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775630"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>yeni portalda Office 365 raporları için Defender'Microsoft 365 Defender görüntüleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Office 365 için Microsoft Defender (örneğin, Microsoft 365 E5 abonelikleri veya Office 365 için Microsoft Defender Plan 1 veya Office 365 Plan 2 eklentileri için Microsoft Defender) güvenlikle ilgili çeşitli raporlar içerir. Gerekli izinlere [sahipsiniz,](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports) bu raporları web portalında Microsoft 365 Defender.

## <a name="view-and-download-reports"></a>Raporları görüntüleme ve indirme

### <a name="view-reports"></a>Raporları görüntüleme

1. Aşağıdaki Microsoft 365 Defender portalında Raporlar E-postası <https://security.microsoft.com>**ve** \> **işbirliği & E-posta** \> **ve & raporları'ne gidin**. Doğrudan E-posta Ve **İşbirliği & sayfasına gitmek** için, kullanın <https://security.microsoft.com/emailandcollabreport>.

1. Görüntülemek istediğiniz raporu ve sonra Ayrıntıları **görüntüle'yi seçin**.  

### <a name="download-reports"></a>Raporları indirme

1. Aşağıdaki Microsoft 365 Defender portalında **RaporlarEmail** <https://security.microsoft.com>**ve** >  işbirliği & **Raporları**\> indirme'ye gidin. Doğrudan İndirme raporları **sayfasına gitmek için** kullanın <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

![Web & e-posta ve işbirliği Microsoft 365 Defender sayfası.](../../media/email-collaboration-download-reports.png)

> [!NOTE]
>
> Office 365 için Defender gerektirmeyen e-posta güvenlik raporları, Microsoft 365 Defender portalında [e-posta güvenlik raporlarını görüntüleme makalesinde açıklanmıştır](view-email-security-reports.md).
>
> Posta akışıyla ilgili raporlar artık genel yönetim Exchange (EAC) yer alır. Bu raporlar hakkında daha fazla bilgi için bkz[. Yeni Yönetim Merkezi'nde Exchange raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>Kasa Ekleri dosya türleri raporu

> [!NOTE]
> Bu rapor kullanımdan silindi. Aynı bilgiler Tehdit koruması durumu [raporunda da mevcuttur](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>Kasa Ekleri ileti yok durumu raporu

> [!NOTE]
> Bu rapor kullanımdan silindi. Aynı bilgiler Tehdit koruması durumu [raporunda da mevcuttur](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Posta gecikme süresi raporu

Posta **gecikme süresi raporu** size, kurum içinde yaşanan posta teslim ve detonasyonu gecikme süresinin toplu bir görünümünü gösterir. Hizmette posta teslim süreleri bir dizi etmen tarafından etkilenir ve saniyeler içinde mutlak teslim süresi bir başarının veya sorunun göstergesi değildir. Bir gün içinde yavaş teslim süresi, başka bir gün için ortalama bir teslim süresi veya tersi olarak kabul olabilir. Bu, diğer iletilerin gözlemlenen teslim süreleri hakkında istatistiksel verilere dayalı olarak ileti teslimlerini nitelendirmaya çalışır.

İstemci tarafı ve ağ gecikme süresi dahil değildir.

Raporu görüntülemek için Rapor Portalı'Microsoft 365 Defender '<https://security.microsoft.com>da açın, Raporlar  \> E-postası ve **işbirliği &-posta** \> **& gidin**. Doğrudan E-posta Ve **İşbirliği & sayfasına gitmek** için, kullanın <https://security.microsoft.com/emailandcollabreport>.

**E-posta & raporları sayfasında** Posta gecikme süresi **raporunu bulun ve Ayrıntıları** **görüntüle'ye tıklayın**. Doğrudan rapora gitmek için kullanın <https://security.microsoft.com/mailLatencyReport>.

![E-posta ve işbirliği raporları sayfasındaki posta & raporu widget'ı.](../../media/mail-latency-report-widget.png)

Posta **gecikme süresi raporu sayfasında** , Posta gecikme süresi raporu **sayfasında aşağıdaki sekmeler** bulunur:

- **50. yüzdebirlik**: Bu, ileti teslim zamanları için orta değerdir. Bu değeri, ortalama bir teslim süresi olarak düşünabilirsiniz. Bu sekme varsayılan olarak seçilidir.
- **90. yüzdebirlik**: Bu, ileti teslimi için yüksek gecikme süresini gösterir. İletilerin yalnızca %10'larının teslimi bu değerden uzun sürebilir.
- **99. yüzdebirlik**: Bu, ileti teslimi için en yüksek gecikme süresini gösterir.

Hangi sekmeyi seç olursa olsun, grafik iletileri aşağıdaki kategorilerde düzenlenmiş olarak gösterir:

- **Genel**
- **Detonation**

Grafikte bir kategorinin üzerine gelindiğinde, her kategorideki gecikme süresinin dökümünü görüntüebilirsiniz.

![Posta gecikme süresi raporunun 50. yüzdebirlik görünümü.](../../media/mail-latency-report-50th-percentile-view.png)

Filtre'ye **tıklarsanız**, aşağıdaki değerlere göre hem grafiği hem de ayrıntılar tablosuna filtre yapabilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **İleti görünümü**: Aşağıdaki değerlerden biri:
  - **Tüm iletiler**
  - **Detonated messages**: One of the following values:
    - **Satır içi detonasyonu**: Teslimden önce tümüyle test edilmiş iletileri içerir.
    - **Zaman uyumsuz detonasyonu**

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Grafiğin altındaki ayrıntılar tablosunda aşağıdaki bilgiler kullanılabilir:

- **Tarih (UTC)**
- **Gecikme süresi**
- **İleti sayısı**
- **50. yüzdebirlik**
- **90. yüzdebirlik**
- **99. yüzdebirlik**

Ana rapor sayfasında Dışarı Aktar ![simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı](view-email-security-reports.md#export-report)** Aktar düğmesi kullanılabilir.

## <a name="threat-protection-status-report"></a>Tehdit koruması durum raporu

Tehdit **koruması durum raporu**, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) ve Office 365 için Microsoft Defender tarafından algılanan ve engellenen kötü amaçlı içerik ve kötü amaçlı e-postalarla ilgili bilgileri bir araya getiren tek bir Office 365. Daha fazla bilgi için tehdit [koruması durum raporuna bakın](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>En çok gönderenler ve alıcılar raporu

En **çok gönderenler ve alıcılar raporu**, EOP için en yüksek alıcıları ve EOP koruma özellikleri Office 365 gösterir. Daha fazla bilgi için bkz [. İlk gönderenler ve alıcılar raporu](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>URL koruma raporu

**URL koruma raporu, algılanan** tehditlere ve URL tıklamalarına yönelik işlemlere yönelik özet ve eğilim görünümleri sağlar. Bu bağlantılar, [Kasa sağlar](safe-links.md). Bu raporda, Uygulanan Bağlantılar ilkesine göre Kasa **tıklamaları izleme seçeneği seçili olan kullanıcılardan gelen verilere tıklanmayacak**.

Raporu görüntülemek için Rapor Portalı'Microsoft 365 Defender açın,  \> Raporlar E-postası ve **işbirliği & E-posta** \> **& raporlarına gidin**.[](https://security.microsoft.com) **E-posta & raporları sayfasında** **URL koruma sayfasını bulun ve Ayrıntıları** **görüntüle'ye tıklayın**. Doğrudan rapora gitmek için ' i açın <https://security.microsoft.com/reports/URLProtectionActionReport>.

![E-posta ve işbirliği raporları sayfasındaki URL & raporu widget'ı.](../../media/url-protection-report-widget.png)

URL koruma raporu **sayfasındaki kullanılabilir** görünümler aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Bu bir koruma *eğilimi raporudur, yani* veriler daha büyük bir veri kümesinde eğilimleri temsil eder. Sonuç olarak, grafiklerde yer alan veriler burada gerçek zamanlı olarak kullanılamaz, ancak ayrıntılar tablosunda veriler yer alır, dolayısıyla ikisi arasında küçük bir uyuşmazlık olduğunu farkebilirsiniz. Grafikler her dört saatte bir yenilenir ve son 90 günlük verileri içerir.

### <a name="view-data-by-url-click-protection-action"></a>Verileri URL'ye göre görüntüleme tıklatma koruması eylemi

![URL'de koruma eylem görünümüne tıklayın URL koruma raporu.](../../media/url-threat-protection-report-url-click-protection-action-view.png)

Verileri **URL'ye göre görüntüle tıklama** koruması eylem görünümü, kuruluşta kullanıcılar tarafından yapılan URL tıklamalarının sayısını ve şu tıklatmaların sonuçlarını gösterir:

- **İzin verildi**: İzin verilen tıklamalar.
- **Kiracı yöneticisi tarafından izin verildi**: Bağlantılar ilkelerde izin Kasa tıklamalar.
- **Engellendi**: Engellendi'ye tıklayın.
- **Kiracı yöneticisi tarafından engellendi**: Bu bağlantılar ilkelerde Kasa.
- **Engellenmiş ve tıklanma tarihi**: Kullanıcıların engellenen URL'ye tıklaması için engellenen tıklamalar.
- **Kiracı yöneticisi tarafından engellenmiş ve şu şekilde** tıklandı: Yönetici bağlantıyı engelledi, ancak kullanıcı bağlantıyı tıkladı.
- **Tarama sırasında tıklayma**: Kullanıcıların URL'ye kadar bekleyen tarama sayfasında tıklaymalarını sağlar.
- **Bekleyen tarama**: Tarama kararını bekleyen URL'lere tıklama.

Tıklar, kullanıcının kötü amaçlı web sitesine yönelik engelleme sayfasına tıklamış olduğunu gösterir (yöneticiler Kasa Bağlantıları ilkelerde tıklamayı devre dışı bırakabilirsiniz).

**Filtreler'e** tıklarsanız, görüntülenen açılır listede aşağıdaki değerlerden birini veya birden fazlasını seçerek raporu ve ayrıntılar tablosunda değişiklik yapabilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **Eylem**:
  - **İzin verildi**
  - **Engellendi**
  - **Kiracı yöneticisi tarafından izin verildi**
  - **Engellendi ve boyunca tıklandı**
  - **Kiracı yöneticisi tarafından engellenmiş ve**
  - **Tarama sırasında tıklatma**
  - **Bekleyen tarama**
- **Etki** alanları: Rapor sonuçlarında listelenen URL etki alanları.
- **Alıcılar**

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Grafiğin altındaki ayrıntılar tablosu, son 7 gün boyunca kuruluş içinde yapılan tüm tıklamaların neredeyse gerçek zamanlı görünümünü sağlar:

- **Saat'e tıklayın**
- **Kullanıcı**
- **URL**
- **Eylem**
- **Uygulama**

Ana rapor sayfasında Zamanlama oluştur ![simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](view-email-security-reports.md#schedule-report)**, ![Rapor isteği simgesi.](../../media/m365-cc-sc-download-icon.png) **[Rapor isteği](view-email-security-reports.md#request-report)** ve Dışarı Aktar ![simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı](view-email-security-reports.md#export-report)** aktar düğmeleri kullanılabilir.

### <a name="view-data-by-url-click-by-application"></a>Uygulamaya göre verileri URL'ye göre görüntüleme

![URL'de, URL koruma raporunda uygulama görünümüne göre tıklayın.](../../media/url-threat-protection-report-url-click-by-application-view.png)

Verileri **URL'ye göre görüntüle'ye tıklarken uygulama** görünümü, Veri Bağlantılarını destekleyen uygulamaların URL Kasa gösterir:

- **E-posta istemcisi**
- **Office belgeyi ekleme**
- **Teams**

**Filtreler'e** tıklarsanız, görüntülenen açılır listede aşağıdaki değerlerden birini veya birden fazlasını seçerek raporu ve ayrıntılar tablosunda değişiklik yapabilirsiniz:

- **Tarih (UTC)**: **Başlangıç tarihi** ve **Bitiş tarihi**
- **Algılama**: Grafikten kullanılabilir uygulamalar.
- **Etki** alanları: Rapor sonuçlarında listelenen URL etki alanları.
- **Alıcılar**

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Grafiğin altındaki ayrıntılar tablosu, son 7 gün boyunca kuruluş içinde yapılan tüm tıklamaların neredeyse gerçek zamanlı görünümünü sağlar:

- **Saat'e tıklayın**
- **Kullanıcı**
- **URL**
- **Eylem**
- **Uygulama**

Ana rapor sayfasında Zamanlama oluştur ![simgesi.](../../media/m365-cc-sc-create-icon.png) **[Zamanlama oluştur](view-email-security-reports.md#schedule-report)**, ![Rapor isteği simgesi.](../../media/m365-cc-sc-download-icon.png) **[Rapor isteği](view-email-security-reports.md#request-report)** ve Dışarı Aktar ![simgesi.](../../media/m365-cc-sc-download-icon.png) **[Dışarı](view-email-security-reports.md#export-report)** aktar düğmeleri kullanılabilir.

## <a name="additional-reports-to-view"></a>Görüntülemek için ek raporlar

Bu makalede açıklanan raporlara ek olarak, aşağıdaki tabloda açıklandığı gibi başka birkaç rapor da kullanılabilir:

|Rapor|Konu|
|---|---|
|**Explorer** (Plan 2 Office 365 için Microsoft Defender) veya gerçek **zamanlı** algılamalar (Plan 1 Office 365 için Microsoft Defender)|[Tehdit Gezgini (ve gerçek zamanlı algılamalar)](threat-explorer.md)|
|Office 365 için Defender gerektirmeyen e-posta güvenlik Office 365|[Portalda e-posta Microsoft 365 Defender görüntüleme](view-email-security-reports.md)|
|Yönetim merkezinde (EAC) Exchange akışı raporları|[Yeni Yönetim Merkezi'nde posta Exchange raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

PowerShell raporlama cmdlet'leri:

|Rapor|Konu|
|---|---|
|En çok gönderenler ve alıcılar|[Get-MailTrafficTopReport](/powershell/module/exchange/get-mailtraffictopreport) <p> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|En iyi kötü amaçlı yazılım|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Posta trafiği|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Güvenli Bağlantılar|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Güvenliği ihlal edilmiş kullanıcılar|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|Posta akışı durumu|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|Spoofed kullanıcılar|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Yeni raporlar için Defender'ı görüntülemek için Office 365 gereklidir?

Bu makalede açıklanan raporları görüntülemek ve kullanmak için, Microsoft 365 Defender portalında aşağıdaki rol gruplarından birinin üyesi Microsoft 365 Defender gerekir:

- **Kuruluş Yönetimi**
- **Güvenlik Yöneticisi**
- **Güvenlik Okuyucu**
- **Genel Okuyucu**

Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

**Not**: Kullanıcı atama Azure Active Directory ilgili kullanıcı rolüne Microsoft 365 yönetim merkezi, kullanıcılara _Microsoft 365 Defender portalında_ gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Raporlar veri göster görünmüyorsa ne olacak?

Yeni raporlar için Defender'da Office 365 görmüyorsanız, ilkelerinizin doğru ayarlanmış olup olmadığını bir kez daha denetleyin. Defender'ın koruma [Kasa için](set-up-safe-links-policies.md)[, Kasa](set-up-safe-attachments-policies.md) Bağlantılar ilkeleri ve Office 365 Kasa Ekleri ilkeleri tanımlanmalıdır. Ayrıca bkz [. İstenmeyen postadan ve kötü amaçlı yazılımlardan koruma](anti-spam-and-anti-malware-protection.md).

## <a name="related-topics"></a>İlgili konular

[Web portalında akıllı raporlar Microsoft 365 Defender öngörüler](reports-and-insights-in-security-and-compliance.md)

[Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference)
