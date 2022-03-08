---
title: Denetim günlüğünde arama Microsoft 365 uyumluluk merkezi
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
description: Bu Microsoft 365 uyumluluk merkezi, birleşik denetim günlüğünde arama yapmak ve kurumda kullanıcı ve yönetici etkinliğini görüntülemek için kullanın.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: 71b7bb5d5588f19ff4134c133377b3e9ca83c780
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319357"
---
# <a name="search-the-audit-log-in-the-compliance-center"></a>Uyumluluk merkezinde denetim günlüğünde arama yapın

Kullanıcının belirli bir belgeyi görüntüp görüntülemediğni veya posta kutusundan bir öğeyi temiz olup bulamadığnı bulmanız mı gerekiyor? Öyleyse, birleştirilmiş denetim günlüğünde arama yapmak için Microsoft 365 uyumluluk merkezi günlüğünde arama yapmak ve kuruluşta kullanıcı ve yönetici etkinliğini görüntülemek için Denetim Günlüğü arama aracını kullanabilirsiniz. Onlarca farklı hizmet ve Microsoft 365 gerçekleştirilen binlerce kullanıcı ve yönetici işlemi, kuruluşun birleşik denetim günlüğünde yakalanır, kaydedilir ve korunur. Bu işlemlerin denetim kayıtlarını aramak, görüntülemek ve dışarı aktararak (CSV dosyasına) aramak, görüntülemek ve dışarı aktarmak için, organizasyonu kullanan kullanıcılar denetim günlüğü arama aracını kullanabilir.

## <a name="microsoft-365-services-that-support-auditing"></a>Microsoft 365 desteği olan diğer hizmetler

Neden birleşik denetim günlüğü? Denetim günlüğünde, farklı hizmetlerde gerçekleştirilen etkinlikler için Microsoft 365 vardır. Aşağıdaki tabloda, birleşik Microsoft 365 tarafından desteklenen hizmet ve özellikler (alfabetik sırada) listelemektedir.

| Microsoft 365 hizmeti veya özelliği | Kayıt türleri|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| İletişim uyumluluğu|ComplianceSuperVisionExchange|
| İçerik gezgini|LabelContentExplorer|
| Veri kaybı önleme (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| eKbulma|Keşif, AeD|
| Tam Veri Eşleşmesi|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Formlar|MicrosoftForms|
| Bilgi engelleri|InformationBarrierPolicyApplication|
| Microsoft 365 Defender|AirInvestigation, AirManualInvestigation, AirAdminActionInvestigation, MS365DCustomDetection|
| Microsoft Teams|MicrosoftTeams|
| MyAnalytics|MyAnalyticsSettings|
| OneDrive İş|OneDrive|
| Power Apps|PowerAppsApp, PowerAppsPlan|
| Power Automate|MicrosoftFlow|
| Power BI|PowerBIAudit|
| Karantina|Karantina|
| Bekletme ilkeleri ve bekletme etiketleri|MIPLabel, MipAutoLabelExchangeItem, MipAutoLabelSharePointItem, MipAutoLabelSharePointPolicyLocation|
| Hassas bilgi türleri|DlpSensitiveInformationType|
| Duyarlılık etiketleri|MIPLabel, SensitivityLabelAction, SensitivityLabeledFileAction, SensitivityLabelPolicyMatch|
| SharePoint Online|SharePoint, SharePointFileOperation,SharePointSharingOperation, SharePointListOperation, SharePointCommentOperation |
| Stream|MicrosoftStream|
| Tehdit İstihbaratı|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|
|||

Önceki tabloda listelenen hizmetlerin her biri üzerinde denetlenen işlemler hakkında daha fazla bilgi için, bu makalenin Denetlenen [etkinlikler bölümüne](#audited-activities) bakın.

Önceki tabloda, Exchange Online PowerShell'de **Search-UnifiedAuditLog** cmdlet'ini kullanarak veya bir PowerShell betiği kullanarak ilgili hizmette etkinlikler için denetim günlüğünde arama yapmak için kullanmak üzere kayıt türü değeri de tanımlandı. Bazı hizmetlerin, aynı hizmet kapsamındaki farklı etkinlik türleri için birden çok kayıt türü vardır. Denetim kayıt türlerinin daha eksiksiz bir listesi için bkz. Office 365 [Yönetim Etkinliği API'si şeması](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Denetim günlüğünde arama yapmak için PowerShell kullanma hakkında daha fazla bilgi için bkz:

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Denetim günlüğünde arama yapmak için PowerShell betiği kullanma](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Denetim günlüğünde aramadan önce

Denetim günlüğünde arama yapmaya başlamadan önce aşağıdaki öğeleri okuduğundan emin olun.

- Denetim günlüğü araması, kurumsal kuruluşlar tarafından denetlenen Microsoft 365 Office 365 açıktır. Denetim günlüğü aramanın açık olduğunu doğrulamak için, PowerShell'de aşağıdaki Exchange Online çalıştırabilirsiniz:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  `True` *UnifiedAuditLogIngestionEnabled* özelliğinin değeri, denetim günlüğü aramasında izinlerin açık olduğunu gösterir. Daha fazla bilgi için bkz [. Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md).

- Denetim günlüğünde arama View-Only için Exchange Online Günlükleri veya Denetim Günlükleri rolüne atanmış Exchange Online gerekir. Varsayılan olarak, bu roller yönetim merkezinin İzinler sayfasında yer alan Uyumluluk Yönetimi ve Kuruluş Exchange atanır. Office 365 ve Microsoft 365 genel yöneticiler otomatik olarak Kuruluş Yönetimi rol grubuna üye olarak Exchange Online. Kullanıcıya denetim günlüğünde en düşük düzeydeki ayrıcalıklarla arama yapma olanağı vermek için, Exchange Online'de özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve sonra da kullanıcıyı yeni rol grubunun üyesi olarak ebilirsiniz. Daha fazla bilgi için bkz[. Gruptaki rol gruplarını Exchange Online](/Exchange/permissions-exo/role-groups).

  > [!IMPORTANT]
  > Kullanıcıya denetim View-Only İzinler sayfasındaki Denetim Günlükleri veya Denetim Günlükleri Microsoft 365 uyumluluk merkezi atarsanız,  denetim günlüğünde arama yapmak mümkün olmayacaktır. İzinleri aynı dosyanın Exchange Online. Çünkü, denetim günlüğünde arama yapmak için kullanılan temel cmdlet, bir Exchange Online cmdlet'tir.

- Kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirilen, bir denetim kaydı oluşturulur ve kuruluşun denetim günlüğünde depolanır. Denetim kaydının korunma süresi (denetim günlüğünde aranabilir) süresi Office 365 veya Microsoft 365 Kurumsal aboneliğinize ve özel olarak belirli kullanıcılara atanan lisansın türüne bağlıdır.

  - Office 365 E5 veya Microsoft 365 E5 lisansı atanmış kullanıcılar için (ya da Microsoft 365 E5 Uyumluluk veya Microsoft 365 E5 eBulma ve Denetim eklenti lisansına sahip kullanıcılar), Azure Active Directory, Exchange ve SharePoint etkinlikleri varsayılan olarak bir yıl süreyle korunur. Kuruluşlar ayrıca, diğer hizmetlerde bir yıla kadar olan etkinliklerle ilgili denetim kayıtlarını tutmak için denetim günlüğü bekletme ilkeleri oluşturabilir. Daha fazla bilgi için bkz [. Denetim günlüğü bekletme ilkelerini yönetme](audit-log-retention-policies.md).

    > [!NOTE]
    > Bir yıllık denetim kayıtlarının elde tutulması için özel önizleme programına organizasyonunız katıldısa, genel kullanılabilirlik sürümü tarihi önce oluşturulan denetim kayıtlarının bekletme süresi sıfırlanmaz.

  - E5 dışında bir lisansa veya başka bir Office 365 Microsoft 365 atanmış kullanıcılar için, denetim kayıtları 90 gün boyunca korunur. Birleşik denetim günlüğünü destekleyen Office 365 Microsoft 365 aboneliklerin listesi için, güvenlik [ve uyumluluk merkezi hizmet açıklamasına bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Posta kutusu denetimi varsayılan olarak açık olduğunda bile, bazı kullanıcılar için posta kutusu denetim olaylarının Microsoft 365 uyumluluk merkezi'ta veya Office 365 Yönetim Etkinliği API'si aracılığıyla yer olmadığını farkebilirsiniz. Daha fazla bilgi için bkz [. Posta kutusu denetim günlüğü hakkında daha fazla bilgi](enable-mailbox-auditing.md#more-information).

- Kuruluşlarınız için denetim günlüğü aramalarını kapatmak için, aşağıdaki komutu Exchange Online bağlı uzak PowerShell'de çalıştırabilirsiniz:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Denetim aramanızı yeniden açmak için, PowerShell'de aşağıdaki Exchange Online çalıştırabilirsiniz:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Daha fazla bilgi için bkz [. Denetim günlüğü aramalarını kapatma](turn-audit-log-search-on-or-off.md).

- Daha önce de belirtildiği gibi, denetim günlüğünde arama yapmak için kullanılan temel cmdlet, **Search-UnifiedAuditLog** olan bir Exchange Online cmdlet'tir. Başka bir ifadeyle, bu cmdlet'i kullanarak denetim günlüğünde arama yapmak için denetim sayfasındaki arama **aracını Microsoft 365 uyumluluk merkezi.** Bu cmdlet'i Exchange Online PowerShell'de çalıştırabilirsiniz. Daha fazla bilgi için bkz. [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  **Search-UnifiedAuditLog** cmdlet'i tarafından döndürülen arama sonuçlarını bir CSV dosyasına aktarma hakkında bilgi için, Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme konusunda yer alan "İpuçları denetim günlüğünü dışarı aktarma ve görüntüleme" bölümüne [bakın](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Denetim günlüğünden verileri programlı olarak indirmek için, PowerShell betiği kullanmak yerine Office 365 Yönetim Etkinliği API'sini öneririz. En Office 365 Yönetimi Etkinlik API'si, işletme, güvenlik ve uyumluluk izleme çözümleri geliştirmek için kullanabileceğiniz bir REST web hizmetidir. Daha fazla bilgi için bkz[. Office 365 API başvurusu.](/office/office-365-management-api/office-365-management-activity-api-reference)

- Azure Active Directory (Azure AD), etki alanınız için dizin Microsoft 365. Birleşik denetim günlüğü, yönetim portalında veya Azure yönetim portalında gerçekleştirilen kullanıcı, Microsoft 365 yönetim merkezi, uygulama, etki <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> alanı ve dizin etkinliklerini içerir. Azure AD olaylarının tam listesi için bkz. [Denetim Azure Active Directory Olaylarını denetleme](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Bir olay gerçekleşirken ilgili denetim günlüğü kaydının bir denetim günlüğü araması sonucunda döndürül olması 30 dakika veya 24 saate kadar sürebilir. Aşağıdaki tabloda, iş yer alan farklı hizmetler için gereken Microsoft 365.

  |Microsoft 365 hizmeti veya özelliği|30 dakika|24 saat|
  |---|:---:|:---:|
  |Güvenlik ve Tehdit Microsoft 365 için Defender|![Onay işareti.](../media/checkmark.png)||
  |Azure Active Directory (kullanıcı oturum açma olayları)||![Onay işareti.](../media/checkmark.png)|
  |Azure Active Directory (yönetici olayları)||![Onay işareti.](../media/checkmark.png)|
  |Veri Kaybını Önleme|![Onay işareti.](../media/checkmark.png)||
  |Dynamics 365 CRM||![Onay işareti.](../media/checkmark.png)|
  |eKbulma|![Onay işareti.](../media/checkmark.png)||
  |Exchange Online|![Onay işareti.](../media/checkmark.png)||
  |Microsoft Power Automate||![Onay işareti.](../media/checkmark.png)|
  |Microsoft Stream|![Onay işareti.](../media/checkmark.png)||
  |Microsoft Teams|![Onay işareti.](../media/checkmark.png)||
  |Power Apps||![Onay işareti.](../media/checkmark.png)|
  |Power BI|![Onay işareti.](../media/checkmark.png)||
  |Microsoft 365 uyumluluk merkezi|![Onay işareti.](../media/checkmark.png)||
  |Duyarlılık etiketleri||![Onay işareti.](../media/checkmark.png)|
  |SharePoint Online ve OneDrive İş|![Onay işareti.](../media/checkmark.png)||
  |Workplace Analytics|![Onay işareti.](../media/checkmark.png)||
  |Yammer||![Onay işareti.](../media/checkmark.png)|
  |Microsoft Forms|![Onay işareti.](../media/checkmark.png)||
  ||||

- Denetim günlüğü Power BI varsayılan olarak etkin değildir. Denetim günlüğünde Power BI etkinlikleri aramak için bu yönetim portalında denetimi Power BI gerekir. Yönergeler için, yönetim portalında yer alan "Denetim günlükleri" [Power BI bakın](/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Denetim günlüğünde arama

Denetim günlüğünde arama ve arama Microsoft 365.

[1. Adım: Denetim günlüğü araması çalıştırma](#step-1-run-an-audit-log-search)

[2. Adım: Arama sonuçlarını görüntüleme](#step-2-view-the-search-results)

[3. Adım: Arama sonuçlarını dosyaya aktarma](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>1. Adım: Denetim günlüğü araması çalıştırma

1. Gidin ve <https://compliance.microsoft.com> oturum açma.

    > [!TIP]
    > Oturum açma bilgilerine erişmek için gizli gözatma oturumu (normal oturum Microsoft 365 uyumluluk merkezi) kullanın, çünkü bu oturum açmış durumdaki oturum açma bilgilerinizin kullanımını engellez. Google Chrome'da (gizli pencere olarak adlandırılan) Microsoft Edge'da veya gizli gözatma oturumunda InPrivate Gözatma oturumu açmak için **CTRL+SHIFT+N** tuşlarına basın.

2. Denetim bölmesinin sol Microsoft 365 uyumluluk merkezi'a **tıklayın**.

    **Denetim sayfası** görüntülenir.

    ![Ölçütleri yapılandırarak raporu çalıştırmak için Ara'ya tıklayın.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > Kullanıcı **ve yönetici etkinliği kaydını başlat bağlantısı** görüntüleniyorsa, denetimi açmak için bu bağlantıya tıklayın. Bu bağlantıyı görmüyorsanız, organizasyonunız için denetim açıktır.

3. Arama **sekmesinde** , aşağıdaki arama ölçütlerini yapılandırabilirsiniz:

   1. **Başlangıç tarihi** ve **Bitiş tarihi**: Varsayılan olarak son yedi gün seçilidir. Bir tarih ve saat aralığında 2013 olayları görüntülemek için, o tarih ve saat aralığını seçin. Tarih ve saat, yerel saatle birlikte sunulacaktır. Belirtmezseniz, en uzun tarih aralığı 90 gündür. Seçilen tarih aralığı 90'dan fazla gün ise, bir hata görüntülenir.

    > [!TIP]
    > En uzun tarih aralığı olan 90 gün kullanıyorsanız, Başlangıç tarihi için geçerli **saati seçin**. Aksi takdirde, başlangıç tarihini bitiş tarihinden önce olduğunu söyleyen bir hata alırsınız. Denetimi son 90 gün içinde tekrar kullandıysanız, en uzun tarih aralığı denetimin açık olduğu tarihten önce baş yürümez.

   2. **Etkinlikler**: Arayabilirsiniz etkinlikleri görüntülemek için açılan listeye tıklayın. Kullanıcı ve yönetici etkinlikleri, ilgili etkinlik grupları halinde düzenlenmiştir. Belirli etkinlikleri seçerek veya etkinlik grubu adına tıklar ve gruptaki tüm etkinlikleri seçersiniz. Ayrıca, seçimi temizlemek için seçili bir etkinliği de tıklarsiniz. Siz arama çalıştırdikten sonra, yalnızca seçili etkinliklere ait denetim günlüğü girdileri görüntülenir. Tüm etkinlikler **için sonuçları göster seçildiğinde** , seçilen kullanıcı veya kullanıcı grubu tarafından gerçekleştirilen tüm etkinliklere yönelik sonuçlar görüntülenir.<br/><br/>Denetim günlüğüne 100'den fazla kullanıcı ve yönetici etkinlikleri kaydedilir. Farklı **hizmetlerin her bir** etkinliğine ilişkin açıklamaları görmek için, bu makalenin konu başlığı altında Denetlenen etkinlikler sekmesine tıklayın.

   3. **Kullanıcılar**: Bu kutuya tıklayın ve arama sonuçlarını görüntülemek için bir veya birden çok kullanıcı seçin. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliğin denetim günlüğü girdileri, sonuç listesinde görüntülenir. Tüm kullanıcılara (ve hizmet hesaplarına) ait girdilerin kuruma geri dönmesi için bu kutuyu boş bırakın.

   4. **Dosya, klasör veya site**: Belirtilen anahtar sözcüğü içeren klasör dosyasıyla ilgili etkinliği aramak için dosya veya klasör adının bir veya hepsini yazın. Dosya veya klasörün URL'sini de belirtebilirsiniz. URL kullanıyorsanız, tam URL yolunun yaz olduğundan emin olun veya URL'nin bir bölümünü yazın; özel karakter ya da boşluk içerme (bununla birlikte, joker karakter ()\* kullanımı destekler).<br/><br/>Kuruma ait tüm dosya ve klasörlere ait girdilerin geri dönmesi için bu kutuyu boş bırakın.

    > [!TIP]
    >
    > - Bir **siteyle** ilgili tüm etkinlikleri arıyorsanız, URL'den sonra bir siteye ilişkin tüm girdileri vermek için joker karakteri (\*) ekleyin; örneğin, `"https://contoso-my.sharepoint.com/personal*"`.
    >
    > - Bir dosyayla ilgili tüm etkinlikleri arıyorsanız **, bu** dosyayla ilgili tüm girdilerin geri dönmesi için dosya adının önünde joker karakteri (\*) ekleyin; örneğin, `"*Customer_Profitability_Sample.csv"`.

4. Arama **ölçütlerinizi** kullanarak arama çalıştırmak için Ara'ya tıklayın.

   Arama sonuçları yüklenir ve birkaç dakika sonra yeni bir sayfada görüntülenir. Arama tamamlandığında, bulunan sonuç sayısı görüntülenir. 150 olaylık artışlarla en çok 50.000 olay görüntülenir.

   ![Arama tamamlendikten sonra sonuç sayısı görüntülenir.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>İpuçları günlüğünde arama aramanın nasıl iş olduğunu denetleme

- Etkinlik adına tıklayarak aramak istediğiniz belirli etkinlikleri seçin. Veya grup adına tıklayarak bir gruptaki (Dosya ve klasör etkinlikleri **gibi) tüm** etkinlikler için arama da gerçekleştirebilirsiniz. Bir etkinlik seçiliyse, bu etkinliği tıklar ve seçimi iptal edebilirsiniz. Ayrıca, anahtar sözcüğü içeren etkinlikleri görüntülemek için arama kutusunu da kullanabilirsiniz.

  ![Tüm etkinlikleri seçmek için etkinlik grup adına tıklayın.](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Yönetici denetim **günlüğünde yer alan olayları görüntülemek için**, Etkinlikler listesinde  Tüm etkinlikler için Exchange seçmeniz gerekir. Bu denetim günlüğünden gelen olaylar için sonuçların Etkinlik sütununda bir cmdlet adı (örneğin, **Set-Mailbox**) görüntülenir. Daha fazla bilgi için, **bu konunun Denetlenen** etkinlikler sekmesine tıklayın ve sonra da Exchange **etkinliklerine tıklayın**.

  Benzer şekilde, Etkinlikler listesinde karşılık gelen bir öğesi olmayan bazı **denetim etkinlikleri de** vardır. Bu etkinlikler için yapılan işlemlerin adını biliyorsanız, tüm etkinlikler için arama yapmak ve ardından arama sonuçlarını CSV dosyasına aktardikten sonra işlemleri filtrelemek için bu işlemlere filtre uygulamanız gerekir.

- Geçerli **arama ölçütlerini** temizlemek için Temizle'ye tıklayın. Tarih aralığı, varsayılan değer olan son yedi gün değerine döner. Ayrıca, tüm seçili **etkinlikleri iptal etmek için Tüm etkinliklerin sonuçlarını göstermek için** de Tüm temizle'yi tıklatın.

- 50.000 sonuç bulunursa, büyük olasılıkla arama ölçütlerine uyan 50.000'den çok olay olduğunu varsayabilirsiniz. Daha az sonuç elde etmek için arama  \> ölçütlerini daraltarak aramaya yeniden çalıştırabilirsiniz veya Sonuçları dışarı aktar Tüm sonuçları indir'i seçerek tüm arama sonuçlarını dışarı **aktarabilirsiniz**.

### <a name="step-2-view-the-search-results"></a>2. Adım: Arama sonuçlarını görüntüleme

Denetim günlüğü aramanın sonuçları Denetim günlüğü **araması sayfasındaki** **Sonuçlar'ın altında** görüntülenir. Daha önce de belirtildiği gibi, 150 olaylık artışlarla en çok 50.000 (en yeni) olay görüntülenir. Sonraki 150 olayları **görüntülemek için kaydırma çubuğunu kullanın veya Shift + End** tuşlarına basın.

Sonuçlar, arama tarafından döndürülen her olay hakkında aşağıdaki bilgileri içerir:

- **Tarih**: Olayın yaşandığı tarih ve saat (yerel saatinize göre).

- **IP adresi**: Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi, IPv4 veya IPv6 adres biçiminde görüntülenir.

   > [!NOTE]
  > Bazı hizmetlerde, bu alanda görüntülenen değer etkinliği yapan kişi tarafından kullanılan cihazın IP adresi değil, kullanıcı adına hizmeti çağıran güvenilen bir uygulamanın IP adresi (örneğin, Web üzerinde Office uygulamaları) olabilir. Ayrıca, ilgili etkinlikler için yönetici etkinliği (veya sistem hesabı tarafından gerçekleştirilen Azure Active Directory), IP adresi günlüğe kaydedilmez ve bu alanda görüntülenen değerdir`null`.

- **Kullanıcı**: Olayı tetikleyen eylemi gerçekleştiren kullanıcı (veya hizmet hesabı).

- **Etkinlik**: Kullanıcı tarafından gerçekleştirilen etkinlik. Bu değer, Etkinlikler açılan listesinde seçtiğiniz **etkinliklere** karşılık gelen bir değerdir. Yönetici denetim günlüğünden Exchange için, bu sütundaki değer bir Exchange cmdlet'tir.

- **Öğe**: İlgili etkinliğin sonucunda oluşturulan veya değiştirilen nesne. Örneğin, görüntülenen veya değiştirilen dosya ya da güncelleştirilen kullanıcı hesabı. Tüm etkinliklerin bu sütunda değeri yoktur.

- **Ayrıntı**: Etkinlik hakkında ek bilgiler. Bir kez daha, tüm etkinliklerin değeri yoktur.

> [!TIP]
> Sonuçları sıralamak için **Sonuçlar'ın altındaki** sütun başlığına tıklayın. Sonuçları A'dan Z'ye veya Z'den A'ya sıralayın. Sonuçları en eskiden en yeniye veya en yeniden en eskiye doğru sıralamak için Tarih üst bilginize tıklayın.

#### <a name="view-the-details-for-a-specific-event"></a>Belirli bir olayın ayrıntılarını görüntüleme

Arama sonuçları listesinde olay kaydına tıklayarak, olayla ilgili daha fazla ayrıntı görüntüebilirsiniz. Olay kaydından ayrıntılı özellikleri içeren bir çıkış sayfası görüntülenir. Görüntülenen özellikler, olayın oluştuğu hizmete bağlıdır. 

### <a name="step-3-export-the-search-results-to-a-file"></a>3. Adım: Arama sonuçlarını dosyaya aktarma

Denetim günlüğü aramalarının sonuçlarını yerel bilgisayarınızdan bir virgülle ayrılmış değer (CSV) dosyasına aktarabilirsiniz. Bu dosyayı başka bir dosyada Microsoft Excel arama, sıralama, filtreleme ve tek sütunu (birden çok özellik içeren) birden çok sütuna bölme gibi özellikleri kullanabilirsiniz.

1. Denetim günlüğü arama çalıştırın ve ardından istediğiniz sonuçları elde inceye kadar arama ölçütlerini düzeltin.

2. Arama sonuçları sayfasında Dışarı Aktar Tüm **sonuçları** **yükle'ye** >  tıklayın.

   Denetim günlüğünden arama ölçütlerine uyan tüm girdiler BIR CSV dosyasına dışarı aktarıldı. Denetim günlüğünden alınan ham veriler CSV dosyasına kaydedilir. Denetim günlüğü girdisine ilişkin ek bilgiler, CSV'de **Denetim Verileri adlı** sütuna ek olarak yer almaktadır.

     > [!IMPORTANT]
     > Tek bir denetim günlüğü aramalarından CSV dosyasına en çok 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den çok olay olduğunu varsayabilirsiniz. Bu sınırdan fazlasını dışarı aktarmayı deneyin ve denetim günlüğü girdilerinin sayısını azaltmak için bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girdiyi dışarı aktaracak şekilde, daha küçük tarih aralıklarında birden çok arama çalıştırmaya gerek kullanabilirsiniz.

3. Dışarı aktarma işlemi tamamlandıktan sonra, pencerenin en üstünde CSV dosyasını açmanızı ve yerel bilgisayarınıza kaydetmenizi istediğiniz bir ileti görüntülenir. Csv dosyasına, İndirmeler klasöründen de erişebilirsiniz.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Denetim günlüğü arama sonuçlarını dışarı aktarma ve görüntüleme hakkında daha fazla bilgi

- Tüm arama sonuçlarını indirmişken, CSV dosyası Oluşturma **Tarihi**, **Kullanıcı** Kimlikleri, İşlemler **ve Denetim** Verileri **sütunlarını içerir**. **Denetim Verileri sütunu** her olay hakkında ek bilgi içerir (uyumluluk merkezinde arama sonuçlarını görüntülendiğinde görüntülenen ayrıntılı bilgilere benzer). Bu sütundaki veriler, denetim günlüğü kaydından birden çok özelliği içeren JSON nesnelerinden oluşur. JSON *nesnesinde* her özellik:değer çifti virgülle ayrılır. denetim verileri sütununu birden çok sütuna bölmek için Excel'de Power Query Düzenleyicisi'nde JSON dönüştürme aracını kullanabilirsiniz; böylece JSON nesnesinde her özelliğin kendi sütunu olur. Bu özellik, bu özelliklerden birini veya birden fazlasını sıralama ve filtrelemenizi sağlar. Power Query Düzenleyicisi'ni kullanarak JSON nesnesini dönüştürmeye ilişkin adım adım yönergeler için bkz. Denetim günlüğü kayıtlarını dışarı aktarma [, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

  Denetim Verileri sütununu **böldikten** sonra, belirli bir etkinlik türünün ayrıntılı  özelliklerini görüntülemek için İşlemler sütununa göre filtre kullanabilirsiniz.

- Farklı hizmetlerden olaylar içeren bir arama sorgusunun tüm sonuçlarını indirerek, eylemin gerçekleştir  olduğu hizmete bağlı olarak CSV dosyasındaki Denetim Verileri sütununda farklı özellikler bulunur. Örneğin, Exchange Azure AD denetim günlüklerinden gelen girdiler, eylemin başarılı olup olmadığını gösteren **ResultStatus** adlı bir özellik içerir. Bu özellik diğer olaylara SharePoint. Benzer şekilde SharePoint etkinliklerin de dosya ve klasörle ilgili etkinlikler için site URL'sini tanımlayan bir özelliği vardır. Bu davranışı azaltmak için, tek bir hizmetten gelen etkinliklere yönelik sonuçları dışarı aktarmada farklı aramalar kullanmayı göz önünde bulundurabilirsiniz.

  Tüm sonuçları indir uygulandığında CSV dosyasındaki **Denetim** Verileri sütununda listelenen özelliklerin birçoğuna ve her birinin uygulandığı hizmete ilişkin açıklama için bkz. Denetim günlüğünde ayrıntılı [özellikler](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Denetlenen etkinlikler

Bu bölümdeki tablolarda, bu bölümdeki tablolarda denetlenen Microsoft 365. Bu olayları aramak için güvenlik ve uyumluluk merkezinde denetim günlüğünde arama yapın.

Bu tablolar, ilgili etkinlikleri veya belirli bir hizmetten gelen etkinlikleri gruplar. Tablolarda, Etkinlikler açılan listesinde görüntülenen kolay ad ve arama sonuçlarını  dışarı aktarsanız bir denetim kaydının ayrıntılı bilgisinde ve CSV dosyasında görüntülenen ilgili işlemi içeren işlem adı yer almaktadır. Ayrıntılı bilgilerin açıklamaları için bkz. [Denetim günlüğünde ayrıntılı özellikler](detailed-properties-in-the-office-365-audit-log.md).

Belirli bir tabloya gitmek için aşağıdaki bağlantılardan birini tıklatın.

:::row:::
    :::column:::
        [Dosya ve sayfa etkinlikleri](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Klasör etkinlikleri](#folder-activities)
    :::column-end:::
    :::column:::
        [SharePoint etkinlikleri ekleme](#sharepoint-list-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Paylaşım ve erişim isteği etkinlikleri](#sharing-and-access-request-activities)
    :::column-end:::
    :::column:::
        [Eşitleme etkinlikleri](#synchronization-activities)
    :::column-end:::
    :::column:::
        [Site izinleri etkinlikleri](#site-permissions-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Site yönetimi etkinlikleri](#site-administration-activities)
    :::column-end:::
    :::column:::
        [Exchange kutusu etkinliklerini geri alın](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Kullanıcı yönetimi etkinlikleri](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Azure AD grup yönetimi etkinlikleri](#azure-ad-group-administration-activities)
    :::column-end:::
    :::column:::
        [Uygulama yönetimi etkinlikleri](#application-administration-activities)
    :::column-end:::
    :::column:::
        [Rol yönetimi etkinlikleri](#role-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Dizin yönetimi etkinlikleri](#directory-administration-activities)
    :::column-end:::
    :::column:::
        [eBulma etkinlikleri](#ediscovery-activities)
    :::column-end:::
    :::column:::
        [Advanced eDiscovery etkinlikleri](#advanced-ediscovery-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Power BI etkinlikleri](#power-bi-activities)
    :::column-end:::
    :::column:::
        [Microsoft Workplace Analytics](#workplace-analytics-activities)
    :::column-end:::
    :::column:::
        [Microsoft Teams etkinlikleri](#microsoft-teams-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Microsoft Teams Sağlık etkinlikleri](#microsoft-teams-healthcare-activities)
    :::column-end:::
    :::column:::
        [Microsoft Teams Vardiyalar etkinlikleri](#microsoft-teams-shifts-activities)
    :::column-end:::
    :::column:::
        [Yammer etkinlikleri](#yammer-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Microsoft Power Automate etkinlikleri](#microsoft-power-automate-activities)
    :::column-end:::
    :::column:::
        [Microsoft Power Apps etkinlikleri](#microsoft-power-apps-activities)
    :::column-end:::
    :::column:::
        [Microsoft Stream etkinlikleri](#microsoft-stream-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [İçerik gezgini etkinlikleri](#content-explorer-activities)
    :::column-end:::
    :::column:::
        [Etkinlikleri karantinaya alın](#quarantine-activities)
    :::column-end:::
    :::column:::
        [Microsoft Forms etkinlikleri](#microsoft-forms-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Duyarlılık etiketi etkinlikleri](#sensitivity-label-activities)
    :::column-end:::
    :::column:::
        [Bekletme ilkesi ve bekletme etiketi etkinlikleri](#retention-policy-and-retention-label-activities)
    :::column-end:::
    :::column:::
        [E-posta etkinliklerini brifing](#briefing-email-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [MyAnalytics etkinlikleri](#myanalytics-activities)
    :::column-end:::
    :::column:::
        [Bilgi engelleri etkinlikleri](#information-barriers-activities)
    :::column-end:::
    :::column:::
        [Disposition review activities](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [İletişim uyumluluğu etkinlikleri](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Etkinlikleri bildirme](#report-activities)
    :::column-end:::
    :::column:::
        [Exchange etkinliklerini yönet](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Dosya ve sayfa etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş'de dosya ve sayfa etkinlikleri açık OneDrive İş.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Dosyaya erişildi|FileAccessed|Kullanıcı veya sistem hesabı bir dosyaya erişmektedir. Kullanıcı bir dosyaya eriştirilsin mi, fileAccessed olayı sonraki beş dakika boyunca aynı kullanıcı için yeniden aynı dosya için günlüğe kaydedilmez.|
|(yok)|FileAccessedExtended|Bu durum, "Dosyaya erişildi" (FileAccessed) etkinliğiyle ilgilidir. Aynı kişi bir dosyaya uzun bir süre boyunca (3 saate kadar) sürekli olarak erişenin FileAccessedExtended etkinliği günlüğe kaydedilir. <br/><br/> FileAccessedExtended etkinliklerinin günlüğe kaydediliş amacı, bir dosyaya sürekli olarak erişilirken günlüğe kaydedilen FileAccessed etkinlikleri sayısını azaltmaktır. Bu, aynı kullanıcı etkinliğine karşı birden çok FileAccessed kaydı gürültünün azaltılmasına ve başlangıçtaki (ve daha önemli olan) FileAccessed etkinliğine odaklanmanıza yardımcı olur.|
|Dosyanın bekletme etiketi değiştirildi|ComplianceSettingChanged|Belgeye uygulanmış veya belgeden kaldırılmış bir bekletme etiketi. Bir bekletme etiketi el ile veya otomatik olarak iletiye uygulandığında bu olay tetiklenir.|
|Kayıt durumu kilitli olarak değiştirildi|LockRecord|Belgeyi kayıt kilitli olarak sınıflara alan bir bekletme etiketinin kayıt durumu. Bu, belgenin değiştirilile veya silinemez olduğu anlamına gelir. Yalnızca site için katılımcı izni atanan kullanıcılar belgenin kayıt durumunu değiştirebilir.|
|Kayıt durumu kilidi açık olarak değiştirildi|UnlockRecord|Belgeyi kayıt kilidinin açık olduğu şekilde sınıflandı olarak sınıflandına sahip bir bekletme etiketinin kayıt durumu. Bu, belgenin değiştirilil geri silinebilir veya silinebilir olduğu anlamına gelir. Yalnızca site için katılımcı izni atanan kullanıcılar belgenin kayıt durumunu değiştirebilir.|
|Dosya iade edildi|FileCheckedIn|Kullanıcı belge kitaplığından kullanıma alınmış bir belgeyi iade etti.|
|Dosya kullanıma alınmış|FileCheckedOut|Kullanıcı belge kitaplığında bulunan bir belgeyi kontrol etti. Kullanıcılar, kendileriyle paylaşılan belgeleri iade etmek ve bu belgelerde değişiklik yapmak için kullanılabilir.|
|Dosya kopyalandı|FileCopied|Kullanıcı siteden bir belge kopyalatır. Kopyalanan dosya sitede başka bir klasöre kaydedilebilir.|
|Dosya silindi|FileDeleted|Kullanıcı siteden bir belge sildi.|
|Dosya geri dönüşüm kutusu'dan silindi|FileDeletedFirstStageRecycleBin|Kullanıcı sitenin geri dönüşüm kutusunu kullanarak dosyayı sildi.|
|Dosya ikinci aşama geri dönüşüm kutusu'dan silindi|FileDeletedSecondStageRecycleBin|Kullanıcı sitenin ikinci aşama geri dönüşüm kutusunu kullanarak dosyayı sildi.|
|Kayıt olarak işaretlenen dosya silindi|RecordDelete|Kayıt olarak işaretlenmiş bir belge veya e-posta silinmiştir. Öğelere kayıt olarak işaret alan bir bekletme etiketi uygulandığında, öğe kayıt olarak kabul edilir.|
|Algılanan belge duyarlılık eşleşmesi|DocumentSensitivityMismatchDetected|Kullanıcı bir belgeyi bir duyarlılık etiketiyle korunan bir siteye yükledi ve belgenin siteye uygulanan duyarlılık etiketinden daha yüksek öncelikli bir duyarlılık etiketi var. Örneğin, Gizli etiketli bir belge Genel etiketli bir siteye karşıya karşıya yüklenen bir belgedir. <br/><br/> Belgenin siteye uygulanan duyarlılık etiketinden daha düşük öncelikli bir duyarlılık etiketi varsa bu olay tetikli değildir. Örneğin, Genel etiketli bir belge Gizli etiketli bir siteye karşıya karşıya yük olur. Duyarlılık etiketi önceliği hakkında daha fazla bilgi için bkz. [Etiket önceliği (sipariş konuları)](sensitivity-labels.md#label-priority-order-matters).|
|Dosyada kötü amaçlı yazılım algılandı|FileMalwareDetected|SharePoint virüsten koruma altyapısı bir dosyada kötü amaçlı yazılım algılar.|
|Dosya kullanıma alındı|FileCheckOutDiscarded|Kullanıcı kullanıma alınmış bir dosyayı atmış (veya geri almış) . Bu, kullanıma alındıklarında dosya üzerinde yaptığı tüm değişikliklerin atılmış olduğu ve belgenin belge kitaplığında sürümüne kaydedilene kadar geçerli olduğu anlamına gelir.|
|İndirilen dosya|FileDownloaded|Kullanıcı siteden bir belge indirildi.|
|Dosya değiştirildi|FileModified|Kullanıcı veya sistem hesabı, siteden bir belgenin içeriği veya özellikleri üzerinde değişiklik gösterir. Aynı kullanıcı aynı belgenin içeriğinde veya özelliklerinde değişiklik olduğunda sistem, başka bir FileModified olayı için günlük oluşturmadan önce beş dakika bekler.|
|(yok)|FileModifiedExtended|Bu durum, "Değiştirilmiş dosya" (FileModified) etkinliğiyle ilgilidir. Aynı kişi bir dosyayı uzun bir süre boyunca (3 saate kadar) sürekli olarak değiştiren FileModifiedExtended etkinliği günlüğe kaydedilir. <br/><br/> FileModifiedExtended etkinliklerinin günlüğe kaydedilme amacı, bir dosya sürekli olarak değiştirildiğinde günlüğe kaydedilen FileModified etkinlikleri sayısını azaltmaktır. Bu, aynı kullanıcı etkinliğine uygun olması için birden fazla FileModified kaydı gürültünün azaltılmasına ve başlangıçtaki (ve daha önemli olan) FileModified etkinliğine odaklanmanıza yardımcı olur.|
|Dosya taşındı|FileMoved|Kullanıcı bir belgeyi sitenin geçerli bulunduğu konumdan yeni bir konuma taşır.|
|(yok)|FilePreviewed|Kullanıcı site sitesinde veya site SharePoint önizlemede OneDrive İş görüntüdedir. Bu olaylar genellikle, resim galerisini görüntüleme gibi tek bir etkinliği temel alan yüksek hacimlerde gerçekleşir.|
|Gerçekleştirilen arama sorgusu|SearchQueryPerformed|Kullanıcı veya sistem hesabı, e-posta SharePoint içinde bir OneDrive İş. Hizmet hesabının arama sorgusu gerçekleştirdiği bazı yaygın senaryolar arasında sitelere ve OneDrive hesaplarına eBulma bekletmesi ve bekletme ilkesi uygulama ve site içeriğine otomatik bekletme veya duyarlılık etiketleri uygulama yer almaktadır.|
|Dosya geri dönüştürüldi | FileRecycled | Kullanıcı dosyayı Geri Dönüşüm Kutusu'na SharePoint taşır. |
|Klasör geri dönüştürüldi | FolderRecycled | Kullanıcı klasörü Geri Dönüşüm Kutusu'SharePoint taşır. |
|Dosyanın tüm ikincil sürümleri geri dönüştürüldi|FileVersionsAllMinorsRecycled|Kullanıcı dosyanın sürüm geçmişinden tüm ikincil sürümleri sildi. Silinen sürümler sitenin geri dönüşüm kutusuna taşınır.|
|Dosyanın tüm sürümleri geri dönüştürüldi|FileVersionsAllRecycled|Kullanıcı dosyanın sürüm geçmişinden tüm sürümleri sildi. Silinen sürümler sitenin geri dönüşüm kutusuna taşınır.|
|Dosyanın sürümü geri dönüştürüldi|FileVersionRecycled|Kullanıcı dosyanın sürüm geçmişinden bir sürümü sildi. Silinen sürüm sitenin geri dönüşüm kutusu'na taşınır.|
|Dosya yeniden adlandırıldı|FileRenamed|Kullanıcı siteden bir belgeyi yeniden adlandırdı.|
|Dosya geri yüklendi|FileRestored|Kullanıcı sitenin geri dönüşüm kutusunu kullanarak bir belgeyi geri yükledi.|
|Dosya karşıya yüklendi|FileUploaded|Kullanıcı sitedeki bir klasöre belge yükledi.|
|Sayfa görüntülandı|PageViewed|Kullanıcı sitede bir sayfayı görüntüler. Bu, Web tarayıcısı kullanarak belge kitaplığında yer alan dosyaları görüntülemeyi içermez. Kullanıcı sayfayı görüntülenin, sonraki beş dakika boyunca aynı sayfa için aynı kullanıcı için PageViewed olayı yeniden günlüğe kaydedilmez.|
|(yok)|PageViewedExtended|Bu durum, "Sayfa görüntü edildi" (PageViewed) etkinliğiyle ilgilidir. Aynı kişi bir web sayfasını uzun bir süre boyunca (3 saate kadar) sürekli olarak görüntülerken PageViewedExtended etkinliği günlüğe kaydedilir. <br/><br/> PageViewedExtended etkinliklerinin günlüğe kaydedilme amacı, bir sayfa sürekli olarak görüntü olduğunda günlüğe kaydedilen PageViewed etkinlikleri sayısını azaltmaktır. Bu, aynı kullanıcı etkinliğine yönelik birden fazla PageViewed kaydı gürültünün azaltılmasına ve başlangıçtaki (ve daha önemli olan) PageViewed etkinliğine odaklanmanıza yardımcı olur.|
|İstemci tarafından sinyal gelen görünümü|ClientViewSignaled|Kullanıcının istemcisi (web sitesi veya mobil uygulama gibi) belirtilen sayfanın kullanıcı tarafından görüntümüş olduğunu sinyalini verdi. Bu etkinlik genellikle bir sayfa için PagePrefetched etkinliği takip eden günlüğe kaydedilir. <br/><br/>**NOT**: ClientViewSignaled olayları sunucu tarafından değil istemci tarafından sinyallenenin olması nedeniyle, olayın sunucu tarafından günlüğe kaydedilmeyebilir ve dolayısıyla denetim günlüğünde görünmeyebilirsiniz. Ayrıca denetim kaydında yer alan bilgilerin güvenilir olması da mümkün olabilir. Bununla birlikte, kullanıcının kimliği sinyali oluşturmak için kullanılan belirteç tarafından doğrulanmış olduğundan, ilgili denetim kaydında listelenen kullanıcının kimliği doğrudur. Sistem, aynı kullanıcının istemcisi sayfanın kullanıcı tarafından yeniden görüntülmüş olduğunu işaret ediyorken, aynı olayın günlüğe kaydedilemeden önce beş dakika bekler.|
|(yok)|PagePrefetched|Kullanıcının istemcisi (web sitesi veya mobil uygulama gibi), kullanıcının göz atarak performansı iyileştirmesine yardımcı olmak için belirtilen sayfayı talep etmiştir. Bu olay, sayfa içeriğine kullanıcının istemcisine hizmet olduğunu göstermek için günlüğe kaydedilir. Bu olay kullanıcının sayfaya gezinen tam bir göstergesi değildir. <br/><br/> Sayfa içeriği istemci tarafından işlenen zaman (kullanıcının isteğine göre) ClientViewSignaled olayı oluşturul etmelidir. İstemcilerin bazıları önceden getiri olduğunu gösterirken bazıları önceden getirileri desteklemez ve bu nedenle bazı önceden getirileri PageViewed etkinlikleri olarak günlüğe kaydedilebilirsiniz.|
||||

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>FileAccessed ve FilePreviewed etkinlikleri hakkında sık sorulan sorular

**Kullanıcı dışı etkinlikler FilePreviewed audit records that contain a user agent like "OneDriveMpc-Transform_Thumbnail"?**

Kullanıcıya özel eylemlerin bunlar gibi olaylar oluşturması senaryoların farkındayız. Kullanıcı profili kartı açma gibi kullanıcı eylemleri (Web üzerinde Outlook'ta bir iletide adına veya e-posta adresine tıklarsanız) benzer olaylara neden olabilir.

**Kullanıcı her OneDriveMpc-Transform_Thumbnail bilerek tetiklenir mi?**

Hayır. Ancak benzer olaylar, tarayıcının önceden getirme sonucu olarak günlüğe kaydedilebilirsiniz.

**Microsoft tarafından kaydedilmiş bir IP adresi üzerinden bir FilePreviewed etkinliği geliyorsa, bu önizlemenin kullanıcının cihazı ekranında görüntüleniyor olduğu anlamına mı gelir?**

Hayır. Olay, tarayıcının önceden getirme sonucu günlüğe kaydedilmiş olabilir.

**Belgenin önizlemesini oluşturan bir kullanıcının FileAccessed olayları oluşturması senaryoları var mı?**

Hem FilePreviewed hem de FileAccessed olayları kullanıcının aramasını dosyanın okundu veya küçük resim işlemede bir okuma sonucunda olduğunu gösterir. Bu olaylar, erişim hedefine göre önizlemeyle uyumlu olacak şekilde tasarlanmış olmalarına karşılık, olay ayrımı kullanıcının amacına uygun değildir.

#### <a name="the-appsharepoint-user-in-audit-records"></a>Denetim kayıtlarında\@ appsharepoint kullanıcısı

Bazı dosya etkinliklerinin (ve diğer SharePoint ilgili etkinliklerin denetim kayıtlarında), etkinliği gerçekleştiren kullanıcının (Kullanıcı ve KullanıcıKimliği alanlarında tanımlanan) başarılı olduğunu app@sharepoint. Bu, etkinliği gerçekleştiren "kullanıcı"nın bir uygulama olduğunu gösterir. Bu durumda uygulamaya, SharePoint'de kullanıcı, yönetici veya hizmet adına kuruluş genelinde eylemler (SharePoint sitesi veya OneDrive hesabı arama gibi) gerçekleştirme izinleri ve verildi. Bir uygulamaya izin verme süreci yalnızca Uygulama erişimi *SharePoint olarak da çağrılır*. Bu, kullanıcı yerine bir SharePoint gerçekleştirmek üzere kullanıcılara sunulan kimlik doğrulamasının uygulama tarafından gerçekleştirilene kadar olduğunu gösterir. Bu nedenle, app@sharepoint kayıtlarda bu kullanıcı tanımlanır. Daha fazla bilgi için bkz[. Yalnızca SharePoint kullanarak erişim izni.](/sharepoint/dev/solution-guidance/security-apponly-azureacs)

Örneğin, app@sharepoint " Arama sorgusu" ve "Erişilen dosya" olaylarına kullanıcı olarak sık sık tanımlanır. Bunun nedeni, kuruluşlarda erişim izni SharePoint App-Only olan bir uygulama, sitelere ve site hesaplarına bekletme ilkeleri uygularken arama sorguları gerçekleştirir ve dosyalara OneDrive olur.

Bir denetim kaydında etkinlik gerçekleştirilen app@sharepoint olarak bu kayıtta yer alan diğer senaryolar:

- Microsoft 365 Gruplar'a. Kullanıcı veya yönetici yeni bir grup oluşturduğunda, site koleksiyonu oluşturmak, listeleri güncelleştirmek ve site grubuna üye eklemek için denetim SharePoint oluşturulur. Bu görevler grubu oluşturan kullanıcı adına bir uygulama gerçekleştirilir.

- Microsoft Teams. Grupların Microsoft 365 gibi, site koleksiyonu oluşturmak, listeleri güncelleştirmek ve ekip oluşturulduğunda bir SharePoint grubuna üye eklemek için denetim kayıtları oluşturulur.

- Uyumluluk özellikleri. Yönetici bekletme ilkeleri, eBulma bekletmeleri ve otomatik olarak duyarlılık etiketleri uygulama gibi uyumluluk özelliklerini uygularken.

Bu ve diğer senaryolarda, belirtilen kullanıcı kısa bir zaman diliminde ve genellikle birbirinin birkaç saniye içinde app@sharepoint'i içeren birden çok denetim kaydı olduğunu da fark etmezsiniz. Bu ayrıca, büyük olasılıkla aynı kullanıcı tarafından başlatılan görev tarafından tetiklanıldığını da gösterir. Ayrıca, denetim kaydında ApplicationDisplayName ve EventData alanları olayı tetikleyen senaryoyu veya uygulamayı tanımlamanıza yardımcı olabilir.

### <a name="folder-activities"></a>Klasör etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş. Daha önce de açıkıldığı gibi, bazı SharePoint denetim kayıtları, eylemi başlatan kullanıcı veya app@sharepoint kullanıcı adına etkinlik gerçekleştirilen kullanıcıya gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarında appsharepoint\@ kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Klasör kopyalandı|FolderCopied|Kullanıcı sitedeki bir klasörü siteden başka bir konuma SharePoint OneDrive İş.|
|Klasör oluşturuldu|FolderCreated|Kullanıcı sitede bir klasör oluşturur.|
|Klasör silindi|FolderDeleted|Kullanıcı siteden klasör sildi.|
|Klasör geri dönüşüm kutusu'dan silindi|FolderDeletedFirstStageRecycleBin|Kullanıcı sitedeki geri dönüşüm kutusunu bir klasörü sildi.|
|Klasör ikinci aşama geri dönüşüm kutusu'dan silindi|FolderDeletedSecondStageRecycleBin|Kullanıcı sitedeki ikinci aşama geri dönüşüm kutusu'na klasörü sildi.|
|Klasör değiştirildi|FolderModified|Kullanıcı sitedeki bir klasörde değişiklik yaptı. Bu, klasörün meta verilerini değiştirmeyi (etiketleri ve özellikleri değiştirme gibi) içerir.|
|Klasör taşındı|FolderMoved|Kullanıcı klasörü sitede farklı bir konuma taşır.|
|Klasör yeniden adlandırıldı|FolderRenamed|Kullanıcı sitedeki bir klasörü yeniden adlandırdı.|
|Klasör geri yüklendi|FolderRestored|Kullanıcı sitedeki geri dönüşüm kutusu tarafından silinmiş bir klasörü geri yüklemiş.|
||||

### <a name="sharepoint-list-activities"></a>SharePoint etkinlikleri ekleme

Aşağıdaki tabloda, kullanıcıların SharePoint Online'da listeler ve liste öğeleriyle etkileşim kurması ile ilgili etkinlikler açık almaktadır. Daha önce de açıkıldığı gibi, bazı SharePoint denetim kayıtları, eylemi başlatan kullanıcı veya app@sharepoint kullanıcı adına etkinlik gerçekleştirilen kullanıcıya gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarında appsharepoint\@ kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Liste oluşturuldu|ListCreated|Kullanıcı özel bir liste SharePoint oluşturdu.|
|Liste sütunu oluşturuldu|ListColumnCreated|Kullanıcı yeni bir SharePoint sütunu oluşturdu. Liste sütunu, bir veya birden çok liste sütununa eklenmiş SharePoint dir.|
|Oluşturulan liste içerik türü|ListContentTypeCreated|Bir kullanıcı liste içerik türü oluşturdu. Liste içerik türü, bir veya birden çok içerik listesine eklenen içerik SharePoint olur.|
|Liste öğesi oluşturuldu|ListItemCreated|Bir kullanıcı mevcut dosya listesinde bir SharePoint oluşturdu.|
|Site sütunu oluşturuldu|SiteColumnCreated|Kullanıcı site sütununu SharePoint oluşturdu. Site sütunu, listeye ekli olmayan bir sütun olabilir. Site sütunu aynı zamanda belirli bir web'de herhangi bir liste tarafından  kullanılan bir meta veri yapısıdır.|
|Site içerik türü oluşturuldu|Oluşturulan Site İçerik Türü|Bir kullanıcı site içerik türü oluşturdu. Site içerik türü, üst siteye eklenen bir içerik t type'tır.|
|Liste silindi|ListDeleted|Bir kullanıcı silinmiş SharePoint sildi.|
|Silinmiş liste sütunu|Silinmiş Liste Sütunu|Kullanıcı bir liste SharePoint sildi.|
|Silinmiş liste içerik türü|ListContentTypeDeleted|Bir kullanıcı liste içerik türünü sildi.|
|Silinmiş liste öğesi|Liste Öğesi Silindi|Kullanıcı bir liste SharePoint sildi.|
|Site sütunu silindi|SiteColumnDeleted|Bir kullanıcı site SharePoint sildi.|
|Site içerik türü silindi|SiteContentTypeDeleted|Kullanıcı site içerik türünü sildi.|
|Geri dönüştürülen liste öğesi|ListItemRecycled|Kullanıcı, bir SharePoint öğesini Geri Dönüşüm Kutusu'na taşıdı.|
|Liste geri yüklendi|ListRestored|Kullanıcı Geri Dönüşüm Kutusu'SharePoint bir liste geri yüklendi.|
|Liste öğesi geri yüklendi|ListItemRestored|Kullanıcı Geri Dönüşüm Kutusu'SharePoint bir öğe geri yüklendi.|
|Liste güncelleştirildi|ListUpdated|Kullanıcı bir veya SharePoint değiştirerek posta listesini güncellemiştir.|
|Güncelleştirilmiş liste sütunu|ListColumnUpdated|Kullanıcı bir veya SharePoint değiştirerek liste sütununu güncellemiştir.|
|Güncelleştirilmiş liste içerik türü|ListContentTypeUpdated|Kullanıcı bir veya birden çok özelliği değiştirerek liste içerik türünü güncellemiştir.|
|Güncelleştirilmiş liste öğesi|ListItemUpdated|Kullanıcı bir veya SharePoint değiştirerek bir liste öğesini güncellemiştir.|
|Site sütunu güncelleştirildi|SiteColumnUpdated|Kullanıcı bir veya SharePoint değiştirerek site sütununu güncellemiştir.|
|Güncelleştirilmiş site içerik türü|SiteContentTypeUpdated|Kullanıcı bir veya birden çok özelliği değiştirerek site içerik türünü güncellemiştir.|
|Görüntülenen liste öğesi|ListItemViewed|Bir kullanıcı bir liste SharePoint görüntüledi. Kullanıcı liste öğesini görüntülenin, sonraki beş dakika boyunca aynı liste öğesi için aynı kullanıcı için ListItemViewed olayı yeniden günlüğe kaydedilmez.|
||||

### <a name="sharing-and-access-request-activities"></a>Paylaşım ve erişim isteği etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş'de kullanıcı paylaşımı ve erişim isteği etkinlikleri açık OneDrive İş. Paylaşım olayları için, Sonuçlar'ın altındaki  Ayrıntı sütunu öğenin paylaşıldı olduğu kullanıcının veya grubun adını tanımlar ve bu kullanıcının mı yoksa grubun kuruluşta mı üye mi yoksa konuk mu olduğunu tanımlar. Daha fazla bilgi için [bkz. Denetim günlüğünde paylaşım denetimini kullanma](use-sharing-auditing.md).

> [!NOTE]
> Kullanıcılar, kullanıcı *nesnesinin* UserType özelliğine bağlı olarak üye veya konuk olabilir. Bir üye genellikle çalışandır ve konuklar da genellikle kuruluş dışından işbirliği yapan bir konuk olur. Kullanıcı paylaşım davetini kabul eder (ve henüz kuruluşun bir parçası değilse), kuruluş dizinde onun için bir konuk hesabı oluşturulur. Konuk kullanıcının dizininize hesabı olduktan sonra, kaynaklar o kullanıcıyla doğrudan paylaşılıyor olabilir (davet gerektirmeden).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Site koleksiyonuna izin düzeyi eklendi|PermissionLevelAdded|Site koleksiyonuna bir izin düzeyi eklenmiştir.|
|Erişim isteği kabul edildi|AccessRequestAccepted|Siteye, klasöre veya belgeye erişim isteği kabul edildi ve istekte bulunan kullanıcıya erişim verildi.|
|Paylaşım daveti kabul edildi|SharingInvitationAccepted|Kullanıcı (üye veya konuk) bir paylaşım davetini kabul etmiş ve kaynağa erişim ve verisi verii. Bu olay, davet edilen kullanıcı ve daveti kabul etmek için kullanılan e-posta adresi hakkında bilgi içerir (bunlar farklı olabilir). Bu etkinliğe çoğunlukla, kullanıcıya kaynak için nasıl erişim verilmesini (örneğin, kullanıcı kaynağına erişimi olan bir gruba ekleme gibi) açıklayan ikinci bir olay eşlik ediyor.|
|Paylaşım daveti engellendi|SharingInvitationBlocked|Kuruluşta yer alan bir kullanıcı tarafından gönderilen paylaşım daveti, hedef kullanıcının etki alanı temel alarak dış paylaşıma izin veren veya dış paylaşımı engellenmiş olan bir dış paylaşım ilkesi nedeniyle engellendi. Bu durumda, paylaşım daveti engellenmiş çünkü: <br/> Hedef kullanıcının etki alanı, izin verilen etki alanları listesine dahil değildir. <br/> Veya <br/> Hedef kullanıcının etki alanı, engellenen etki alanları listesine eklenir. <br/> Etki alanları temel alınarak dış paylaşıma izin verme veya engelleme hakkında daha fazla bilgi için bkz. [SharePoint Online'da kısıtlı etki alanları paylaşımı ve OneDrive İş](/sharepoint/restricted-domains-sharing).|
|Erişim isteği oluşturuldu|AccessRequestCreated|Kullanıcı, erişim iznine sahip olduğu bir site, klasör veya belgeye erişim isteğinda ekleyebilirsiniz.|
|Şirkette paylaşılabilir bağlantı oluşturuldu|CompanyLinkCreated|Kullanıcı kaynağa şirket genelinde bir bağlantı oluşturdu. Şirket genelindeki bağlantılar yalnızca kuruluş üyeleri tarafından kullanılabilir. Konuklar tarafından kullanılamaz.|
|Anonim bağlantı oluşturuldu|AnonymousLinkCreated|Kullanıcı kaynağa bir anonim bağlantı oluşturdu. Bu bağlantıya sahip olan herkes kimlik doğrulaması yapmak zorunda kalmadan kaynağa erişebilirsiniz.|
|Güvenli bağlantı oluşturuldu|SecureLinkCreated|Bu öğeye bir güvenli paylaşım bağlantısı oluşturulmuş.|
|Paylaşım daveti oluşturuldu|SharingInvitationCreated|Kullanıcı SharePoint Online'da veya OneDrive İş dizininde yer alan bir kullanıcıyla kaynak paylaştırdı.|
|Silinmiş güvenli bağlantı|SecureLinkDeleted|Güvenli paylaşım bağlantısı silindi.|
|Erişim isteği reddedildi|AccessRequestDenied|Site, klasör veya belgeye erişim isteği reddedilmiştir.|
|Şirkette paylaşılabilir bağlantı kaldırıldı|CompanyLinkRemoved|Kullanıcı kaynağın şirket genelindeki bağlantısını kaldırdı. Artık bu bağlantı kaynağa erişmek için kullanılamaz.|
|Anonim bağlantı kaldırıldı|AnonymousLinkRemoved|Kullanıcı kaynağa olan anonim bağlantıyı kaldırdı. Artık bu bağlantı kaynağa erişmek için kullanılamaz.|
|Dosya, klasör veya site paylaşıldı|SharingSet|Kullanıcı (üye veya konuk) dosya, klasör veya siteyi SharePoint OneDrive İş dizinindeki bir kullanıcıyla paylaştırdı. Bu etkinliğin **Ayrıntı** sütunundaki değer, kaynağın paylaşıldı olduğu kullanıcının adını tanımlar ve bu kullanıcının üye mi yoksa konuk mu olduğunu tanımlar. <br/><br/> Bu etkinliğe çoğunlukla, kullanıcıya kaynak için nasıl erişim verilmesini açıklayan ikinci bir olay eşlik ediyor. Örneğin, kullanıcı kaynağına erişimi olan bir gruba ekleme.|
|Güncelleştirilmiş erişim isteği|AccessRequestUpdated|Öğeye erişim isteği güncelleştirildi.|
|Anonim bağlantı güncelleştirildi|AnonymousLinkUpdated|Kullanıcı kaynağa olan anonim bağlantıyı güncellemiştir. Arama sonuçlarını dışarı aktararak, güncelleştirilen alan EventData özelliğine dahil edilir.|
|Güncelleştirilmiş paylaşım daveti|SharingInvitationUpdated|Dış paylaşım daveti güncelleştirildi.|
|Anonim bağlantı kullanıldı|AnonymousLinkUsed|Anonim bir kullanıcı, anonim bağlantı kullanarak bir kaynağa erişdi. Kullanıcının kimliği bilinmiyor olabilir, ancak kullanıcının IP adresi gibi diğer ayrıntıları da öğrenebilirsiniz.|
|Dosya, klasör veya sitenin paylaşılmayan adı|SharingRevoked|Kullanıcı (üye veya konuk) daha önce başka bir kullanıcıyla paylaşılmış olan dosya, klasör veya sitenin paylaşımını sildi.|
|Şirkette paylaşılabilir bağlantı kullanıldı|CompanyLinkUsed|Kullanıcı şirket çapında bir bağlantı kullanarak bir kaynağa erişti.|
|Kullanılan güvenli bağlantı|SecureLinkUsed|Bir kullanıcı güvenli bağlantı kullandı.|
|Kullanıcı güvenli bağlantıya eklendi|AddedToSecureLink|Bir kullanıcı, güvenli paylaşım bağlantısını kullanabileceği varlıklar listesine eklendi.|
|Kullanıcı güvenli bağlantıdan kaldırıldı|RemovedFromSecureLink|Bir kullanıcı güvenli paylaşım bağlantısı kullanabileceği varlıklar listesinden çıkarıldı.|
|Paylaşım davetini geri kaldırıldı|SharingInvitationRevoked|Kullanıcı bir kaynağın paylaşım davetini geri çekildi.|
||||

### <a name="synchronization-activities"></a>Eşitleme etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş'de dosya eşitleme etkinlikleri liste OneDrive İş.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Bilgisayarın dosyaları eşitlemesine izin verildi|ManagedSyncClientAllowed|Kullanıcı siteyle başarılı bir eşitleme ilişkisi kurmıştır. Eşitleme ilişkisinin başarılı olması için, kullanıcının bilgisayarının kuruluşta belge kitaplıklarına erişen etki alanları listesine (güvenilir alıcılar *listesi olarak adlandırılan*) eklenmiş bir etki alanına üye olmasıdır. <br/><br/> Bu özellik hakkında daha fazla bilgi için bkz. Windows PowerShell alıcılar listesinde yer alan etki OneDrive eşitleme etki alanlarını etkinleştirmek için [cmdlet'leri kullanma](/powershell/module/sharepoint-online/).|
|Bilgisayarın dosyaları eşitlemesi engellendi|UnmanagedSyncClientBlocked|Kullanıcı, kuruluş etki alanına üye olmayan veya kuruluşun belge kitaplıklarına erişen etki alanları listesine (güvenilir alıcılar listesi olarak adlandırılan  *)*  eklenmiştir. Eşitleme ilişkisine izin verilmez ve kullanıcının bilgisayarının belge kitaplığına dosya eşitlemesi, indirmesi veya karşıya yüklemesi engellenir. <br/><br/> Bu özellik hakkında bilgi için bkz. Windows PowerShell alıcılar listesinde yer alan etki OneDrive eşitleme etki alanlarını etkinleştirmek için [cmdlet'leri kullanma](/powershell/module/sharepoint-online/).|
|Dosyalar bilgisayara indirildi|FileSyncDownloadedFull|Kullanıcı bir dosyayı SharePoint belge kitaplığından veya OneDrive eşitleme uygulamasını (OneDrive.exe) kullanarak OneDrive İş bilgisayarınıza indirmiştir.|
|Dosya değişiklikleri bilgisayara indirildi|FileSyncDownloadedPartial|Bu olay, eski OneDrive İş eşitleme uygulaması (eşitleme) ile birlikte Groove.exe.|
|Dosyalar belge kitaplığına yüklendi|FileSyncUploadedFull|Kullanıcı belge kitaplığı SharePoint nda veya OneDrive eşitleme uygulamasını (OneDrive.exe) kullanarak belge kitaplığında yeni bir dosya OneDrive İş dosyada değişiklikler OneDrive.exe.|
|Dosya değişiklikleri belge kitaplığına yüklendi|FileSyncUploadedPartial|Bu olay, eski OneDrive İş eşitleme uygulaması (eşitleme) ile birlikte Groove.exe.|
||||

### <a name="site-permissions-activities"></a>Site izinleri etkinlikleri

Aşağıdaki tabloda, sitelere erişim vermek (ve iptal etmek) için SharePoint izin atama ve grupları kullanma ile ilgili olaylar listelemektedir. Daha önce de açıkıldığı gibi, bazı SharePoint denetim kayıtları, eylemi başlatan kullanıcı veya app@sharepoint kullanıcı adına etkinlik gerçekleştirilen kullanıcıya gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarında appsharepoint\@ kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Site koleksiyonu yöneticisi eklendi|SiteCollectionAdminAdded|Site koleksiyonu yöneticisi veya sahibi, bir kişiyi site için site koleksiyonu yöneticisi olarak eklemektedir. Site koleksiyonu yöneticilerinin site koleksiyonu ve tüm alt siteler üzerinde tam denetim izinleri vardır. Bu etkinlik, yönetici bir kullanıcının OneDrive hesabına erişme izni verdiği zaman da (SharePoint yönetim merkezinde kullanıcı profilini düzenleyerek veya kullanıcı hesabını [Microsoft 365 yönetim merkezi.](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)|
|Grup grubuna kullanıcı veya SharePoint eklendi|AddedToGroup|Kullanıcı grup grubuna bir üye veya SharePoint ekledi. Bu, bilerek yapılan bir eylem olabileceği gibi paylaşım olayı gibi başka bir etkinliğin sonucu da olabilir.|
|İzin düzeyi devralması bozuldu|PermissionLevelsInheritanceBroken|Öğe değiştirildi, böylece artık üst öğesinden izin düzeylerini devralmaz.|
|Paylaşım devralması bozuldu|SharingInheritanceBroken|Öğe değiştirildi, böylece artık üst öğesinden paylaşım izinlerini devralmaz.|
|Grup oluşturuldu|GroupAdded|Site yöneticisi veya sahibi, site için bir grup oluşturur veya bir grubun oluşturularak sonuç olarak bir görev gerçekleştirir. Örneğin, kullanıcı ilk kez bir dosyanın paylaşımına bağlantı oluşturduğunda, kullanıcının kendi sitelerine bir sistem OneDrive İş eklenir. Bu olay, kullanıcının paylaşılan bir dosyaya düzenleme izinleri içeren bir bağlantı oluşturması sonucu da olabilir.|
|Grup silindi|GroupRemoved|Kullanıcı siteden bir grubu sildi.|
|Değiştirilmiş erişim isteği ayarı|WebRequestAccessModified|Erişim isteği ayarları sitede değiştirildi.|
|Değiştirilmiş 'Üyeler Paylaşabilir' ayarı|WebMembersCanShareModified|**Paylaşabilirsiniz Üyeleri** ayarı sitede değiştirildi.|
|Site koleksiyonunda izin düzeyi değiştirildi|PermissionLevelModified|Site koleksiyonunda bir izin düzeyi değiştirilmiştir.|
|Site izinleri değiştirildi|SitePermissionsModified|Site yöneticisi veya sahibi (veya sistem hesabı), siteden bir gruba atanan izin düzeyini değiştirir. Gruptan tüm izinler kaldırılmışsa da bu etkinlik günlüğe kaydedilir. <br/><br/> **NOT**: Bu işlem SharePoint Online'da SharePoint. İlgili olayları bulmak için, **Site** koleksiyonu yöneticisi eklendi, Grup için kullanıcı veya grup eklendi, **SharePoint Kullanıcıya** grup oluşturma izni **verildi, Grup** oluşturuldu ve Grup silindi gibi diğer izin etkinliklerini **arayabilirsiniz.** |
|Site koleksiyonundan izin düzeyi kaldırıldı|PermissionLevelRemoved|Site koleksiyonundan bir izin düzeyi kaldırılmıştır.|
|Site koleksiyonu yöneticisi kaldırıldı|SiteCollectionAdminRemoved|Site koleksiyonu yöneticisi veya sahibi, bir kişiyi sitenin koleksiyon yöneticisi olarak kaldırır. Bu etkinlik, yöneticinin kendi kullanıcı hesabı için site koleksiyonu yöneticileri listesinden (kullanıcı profilini OneDrive yönetim merkezinde düzenleyerek) kendilerini site koleksiyonu yöneticileri listesinden kaldırıyor SharePoint kaydedilir.  Denetim günlüğü arama sonuçlarında bu etkinliğin sonuç olarak dönmesi için, tüm etkinlikleri aramanız gerekir.|
|Kullanıcı veya grup grup SharePoint kaldırıldı|RemovedFromGroup|Kullanıcı grup grubundan bir üyeyi veya SharePoint kaldırılmıştır. Bu, bilerek yapılan bir eylem olabileceği gibi, unsharing olayı gibi başka bir etkinliğin sonucu da olabilir.|
|Site yöneticisi izinleri istenen|SiteAdminChangeRequest|Kullanıcı, bir site koleksiyonunda site koleksiyonu yöneticisi olarak eklenme isteğinda lenmiştir. Site koleksiyonu yöneticilerinin site koleksiyonu ve tüm alt siteler üzerinde tam denetim izinleri vardır.|
|Paylaşım devralma geri yüklendi|SharingInheritanceReset|Öğenin üst öğesinden paylaşım izinlerini devralmasını sağlarken değişiklik yapıldı.|
|Grup güncelleştirildi|GroupUpdated|Site yöneticisi veya sahibi, site için bir grubun ayarlarını değiştirmektedir. Bu, grubun adını, grup üyeliğini kimlerin görüntüleyemez veya düzenleyemez? ve üyelik isteklerinin nasıl işlenemez? içerebilir.|
||||

### <a name="site-administration-activities"></a>Site yönetimi etkinlikleri

Aşağıdaki tabloda, SharePoint Online'da site yönetimi görevlerinin sonucunda SharePoint liste vardır. Daha önce de açıkıldığı gibi, bazı SharePoint denetim kayıtları, eylemi başlatan kullanıcı veya app@sharepoint kullanıcı adına etkinlik gerçekleştirilen kullanıcıya gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarında appsharepoint\@ kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|İzin verilen veri konumu eklendi|AllowedDataLocationAdded|Bir SharePoint yöneticisi veya genel yönetici çok coğrafi bir ortamda izin verilen bir veri konumu ekledi.|
|Muaf kullanıcı aracısı eklendi|ExemptUserAgentSet|Bir SharePoint yöneticisi veya genel yönetici, yönetim merkezinde muaf kullanıcı aracıları listesine bir kullanıcı SharePoint ekledi.|
|Coğrafi konum yöneticisi eklendi|GeoAdminAdded|Bir SharePoint yöneticisi veya genel yönetici bir kullanıcıyı bir konumun coğrafi yöneticisi olarak ekledi.|
|Kullanıcının grup oluşturmasına izin verildi|AllowGroupCreationSet|Site yöneticisi veya sahibi, siteye bir izin düzeyi ekler ve bu izin atanan kullanıcının o site için bir grup oluşturma izni verir.|
|Sitenin coğrafi olarak taşınması iptal edildi|SiteGeoMoveCancelled|Bir SharePoint yöneticisi veya genel yönetici sitenin coğrafi olarak SharePoint veya OneDrive başarılı bir şekilde iptal etmiştir. Multi-Geo özelliği, bir kuruluşun birden çok Microsoft veri merkezi coğrafyasına (geo) yayılmasına olanak sağlar. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Paylaşım ilkesi değiştirildi|SharingPolicyChanged|Bir SharePoint yöneticisi veya genel yönetici SharePoint Yönetim Merkezi'ni veya Microsoft 365 yönetim merkezi, SharePoint Yönetim Kabuğu'SharePoint değiştirmiştir. Kurum içinde paylaşım ilkesinde ayarlarda yapılan her değişiklik günlüğe kaydedilir. Değiştirilen ilke, olay kaydının ayrıntılı özelliklerinde **ModifiedProperties** alanında tanımlanır.|
|Cihaz erişim ilkesi değiştirildi|DeviceAccessPolicyChanged|Bir SharePoint yöneticisi veya genel yönetici, kurum için yönetim dışı cihazlar ilkesi değiştirmiştir. Bu ilke, SharePoint bir OneDrive olmayan cihazlardan Microsoft 365 OneDrive ve posta cihazlarına erişimi kontrol eder. Bu ilkenin yapılandırılması için Enterprise Mobility + Security gerekir. Daha fazla bilgi için bkz. [Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices).|
|Muaf kullanıcı aracıları değiştirildi|CustomizeExemptUsers|Bir SharePoint yöneticisi veya genel yönetici, yönetim merkezinde muaf kullanıcı aracıları SharePoint özelleştirdi. Hangi kullanıcı aracılarının dizine almak için bir web sayfasının tamamını almaktan muaf tutulacaklarını belirtebilirsiniz. Bu, muaf olduğunu belirttiğiniz kullanıcı aracısı bir InfoPath formuyla karşılaştığında, formun tüm web sayfası yerine XML dosyası olarak döndürülecektir. Bu InfoPath formlarında dizin oluşturmayı daha hızlı sağlar.|
|Ağ erişim ilkesi değiştirildi|NetworkAccessPolicyChanged|Bir SharePoint yöneticisi veya genel yönetici, SharePoint Online PowerShell kullanarak veya SharePoint Online PowerShell kullanarak konum tabanlı erişim ilkesi (güvenilir ağ sınırı olarak da denir) SharePoint değiştirmiştir. Bu tür ilkeler, sizin belirttiğiniz yetkili IP SharePoint ve OneDrive kaynakları için kimlerin erişeni kontrol eder. Daha fazla bilgi için bkz[. SharePoint Online'a erişimi denetleme ve OneDrive konuma göre verileri denetleme](/sharepoint/control-access-based-on-network-location).|
|Sitenin coğrafi olarak taşınması tamamlandı|SiteGeoMoveCompleted|Genel yönetici tarafından zamanlanan bir siteyi coğrafi olarak taşıma başarılı bir şekilde tamamlanmıştır. Multi-Geo özelliği, bir kuruluşun birden çok Microsoft veri merkezi coğrafyasına (geo) yayılmasına olanak sağlar. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Gönderilen bağlantısı oluşturuldu|SendToConnectionAdded|Genel SharePoint yöneticisi veya genel yönetici, yönetim merkezinin Kayıt yönetimi sayfasında yeni bir SharePoint oluşturur. Gönder bağlantısı, belge deposunun veya kayıt merkezinin ayarlarını belirtir. Gönder bağlantısı seniz, İçerik Düzenleyicisi belgeleri belirtilen konuma gönderebilir.|
|Site koleksiyonu oluşturuldu|SiteCollectionCreated|Bir SharePoint yöneticisi veya genel yönetici SharePoint Online kuruluşunda bir site koleksiyonu oluşturur veya bir kullanıcı kendi OneDrive İş sağlar.|
|Sahipsiz merkez sitesi silindi|HubSiteOrphanHubDeleted|Bir SharePoint yöneticisi veya genel yönetici, ilişkili sitesi olmayan bir merkez sitesi olan artık bir merkez sitesini sildi. Sahipsiz bir hub, büyük olasılıkla özgün hub sitenin silinmesi nedeniyle kaynaklandı.|
|Gönder bağlantısı silindi|SendToConnectionRemoved|Bir SharePoint yöneticisi veya genel yönetici, yönetim merkezinin Kayıt yönetimi sayfasındaki Gönder SharePoint silebilir.|
|Site silindi|SiteDeleted|Site yöneticisi siteyi siler.|
|Belge önizleme etkinleştirildi|PreviewModeEnabledSet|Site yöneticisi, site için belge önizlemesini sağlar.|
|Eski iş akışı etkinleştirildi|LegacyWorkflowEnabledSet|Site yöneticisi veya sahibi siteye SharePoint 2013 İş Akışı Görevi içerik türünü eklemektedir. Ayrıca genel yöneticiler aynı zamanda genel yönetim merkezinde kuruluşun tamamı için SharePoint etkinleştir olabilir.|
|Enabled Office on Demand|OfficeOnDemandSet|Site yöneticisi, Office masaüstü uygulamalarının en son sürümüne erişmelerine olanak sağlayan Office izin verdi. Office Özel Istekler, SharePoint yönetim merkezinde etkinleştirilir ve tam, yüklü Microsoft 365 uygulamalarını içeren bir Office gerektirir.|
|Kişi Aramaları için etkin sonuç kaynağı|PeopleResultsScopeSet|Site yöneticisi, bir site için Kişi Aramaları için sonuç kaynağını oluşturur.|
|RSS akışları etkinleştirildi|NewsFeedEnabledSet|Site yöneticisi veya sahibi site için RSS akışlarını etkindir. Genel yöneticiler, genel yönetim merkezinde kuruluşun tamamı için RSS SharePoint etkinleştir olabilir.|
|Merkez sitesine katılmış site|HubSiteJoined|Site sahibi kendi sitesini bir merkez sitesiyle ilişkilendirdi.|
|Site koleksiyonu kotası değiştirildi|SiteCollectionQuotaModified|Site yöneticisi, site koleksiyonunda kotada değişiklik yaptı.|
|Kayıtlı merkez sitesi|HubSiteRegistered|Bir SharePoint yöneticisi veya genel yönetici bir merkez sitesi oluşturur. Sonuçlar, sitenin bir merkez sitesi olarak kaydedilir.|
|İzin verilen veri konumu kaldırıldı|AllowedDataLocationDeleted|Bir SharePoint yöneticisi veya genel yönetici çok coğrafi bir ortamda izin verilen veri konumunu kaldırılmış olabilir.|
|Coğrafi konum yöneticisi kaldırıldı|GeoAdminDeleted|Bir SharePoint yöneticisi veya genel yönetici bir konumun coğrafi yöneticisi olarak bir kullanıcı kaldırılmıştır.|
|Site yeniden adlandırıldı|SiteRenamed|Site yöneticisi veya sahibi siteyi yeniden adlandırıyor|
|Sitenin coğrafi olarak taşınması zamanlandı|SiteGeoMoveScheduled|Bir SharePoint yöneticisi veya genel yönetici sitenin coğrafi olarak SharePoint veya OneDrive başarılı bir şekilde zamanmıştır. Multi-Geo özelliği, bir kuruluşun birden çok Microsoft veri merkezi coğrafyasına (geo) yayılmasına olanak sağlar. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Ana bilgisayar sitesini ayarlama|HostSiteSet|Bir SharePoint yöneticisi veya genel yönetici, kişisel siteleri veya diğer siteleri barındırmak için OneDrive İş değiştirir.|
|Coğrafi konum için depolama kotasını ayarlama|GeoQuotaAllocated|Bir SharePoint yöneticisi veya genel yönetici, çok coğrafi bir ortamda coğrafi konum için depolama kotasını yapılandırmış olabilir.|
|Merkez sitesinden katılmamış site|HubSiteUnjoined|Site sahibi merkez sitesinden kendi sitesini aşiyar.|
|Kaydı olmayan merkez sitesi|HubSiteUnregistered|Bir SharePoint yöneticisi veya genel yönetici, siteyi merkez sitesi olarak değiştirmemiş olabilir. Bir merkez sitesi kaydısız olduğunda, artık merkez sitesi olarak işlevsizdir.|
||||

### <a name="exchange-mailbox-activities"></a>Exchange kutusu etkinliklerini geri alın

Aşağıdaki tabloda, posta kutusu denetim günlüğü tarafından günlüğe kaydedilebilir etkinlikler listelene. Posta kutusu sahibi, temsilci kullanıcı veya yönetici tarafından gerçekleştirilen posta kutusu etkinlikleri, 90 gün boyunca denetim günlüğüne otomatik olarak kaydedilir. Yöneticinin, tüm kullanıcılarınız için posta kutusu denetim günlüğünü kapatması mümkündür. Bu durumda, hiçbir kullanıcının posta kutusu eylemi günlüğe kaydedilmez. Daha fazla bilgi için bkz. [Posta kutusu denetimini yönetme](enable-mailbox-auditing.md).

 Ayrıca, Exchange Online PowerShell'de [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) cmdlet'ini kullanarak posta kutusu Exchange Online arayabilirsiniz.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Erişilen posta kutusu öğeleri|MailItemsAccessed|İletiler posta kutusunda okundu veya erişildi. Bu etkinliğin denetim kayıtları iki şekilde tetiklenir: posta istemcisi (Outlook gibi) iletiler üzerinde bir bağlama işlemi gerçekleştirirken veya posta protokolleri (Exchange ActiveSync veya IMAP gibi) öğeleri bir posta klasöründe eşitlesin. Bu etkinlik yalnızca lisans veya lisans Office 365 kullanıcılar için Microsoft 365 E5 kaydedilir. Güvenliği ihlal edilmiş e-posta hesabını incelerken, bu etkinliğin denetim kayıtlarını çözümlemek yararlı olur. Daha fazla bilgi için, Gelişmiş Denetim'in "Gelişmiş Denetim olayları" [bölümüne bakın](advanced-audit.md#advanced-audit-events). |
|Temsilci posta kutusu izinleri eklendi|Add-MailboxPermission|Yönetici, kullanıcıya (temsilci olarak bilinir) başka bir kişinin posta kutusu için FullAccess posta kutusu izni atadı. FullAccess izni, temsilciye diğer kişinin posta kutusunu açma ve posta kutusunun içeriğini okuma ve yönetme izni verir. Bu etkinliğin denetim kaydı, hizmette yer alan bir sistem hesabı Microsoft 365 düzenli aralıklarla kuruluş adına bakım görevlerini gerçekleştirirken de oluşturulur. Sistem hesabı tarafından gerçekleştirilen yaygın bir görev, sistem posta kutularının izinlerini güncelleştirmektir. Daha fazla bilgi için bkz[. Posta kutusu denetim Exchange hesapları](#system-accounts-in-exchange-mailbox-audit-records).|
|Takvim klasörüne temsilci erişimi olan kullanıcı eklendi veya kaldırıldı|UpdateCalendarDelegation|Bir kullanıcı başka bir kullanıcının posta kutusunun takvimine temsilci olarak eklenmiştir veya kaldırılmıştır. Takvim temsilcisi, aynı kuruluşta yer alan başka birine posta kutusu sahibinin takvimini yönetme izni verir.|
|Klasöre izinler eklendi|AddFolderPermissions|Bir klasör izni eklendi. Klasör izinleri, bir posta kutusu içinde yer alan klasörlere ve bu klasörlerde yer alan iletilere, kuruluşta hangi kullanıcıların eriş erişeni kontrol edin.|
|İletiler başka bir klasöre kopyalandı|Kopyala|İleti başka bir klasöre kopyalandı.|
|Oluşturulan posta kutusu öğesi|Oluştur|Posta kutusunun Takvim, Kişiler, Notlar veya Görevler klasöründe bir öğe oluşturulur. Örneğin, yeni bir toplantı isteği oluşturulur. İleti oluşturma, gönderme veya alma denetlenz. Ayrıca, posta kutusu klasörü oluşturma denetlenz.|
|Web uygulamasında yeni gelen Outlook kuralı oluşturuldu|New-InboxRule|Posta kutusu sahibi veya posta kutusuna erişimi olan başka bir kullanıcı, web uygulamasında bir Outlook kuralı oluşturdu.|
|Silinmiş Öğeler klasöründen silinmiş iletiler|SoftDelete|İleti kalıcı olarak silinmiştir veya Silinmiş Öğeler klasöründen silinmiştir. Bu öğeler Kurtarılabilir Öğeler klasörüne taşınır. Kullanıcı bir tirtir ve Shift+Delete tuşlarına basarak kurtarılabilir Öğeler **klasörüne de taşınır**.|
|İletiyi kayıt olarak etiketleme|ApplyRecordLabel|İleti bir kayıt olarak sınıflandırılmış. Bu durum, içeriği kayıt olarak sınıflanan bir bekletme etiketi iletiye el ile veya otomatik olarak uygulandığında ortaya çıkar.|
|İletiler başka bir klasöre taşındı|Taşıma|İleti başka bir klasöre taşınmış.|
|İletiler Silinmiş Öğeler klasörüne taşındı|MoveToDeletedItems|İleti silinmiştir ve Silinmiş Öğeler klasörüne taşınmış.|
|Klasör izni değiştirildi|UpdateFolderPermissions|Klasör izni değiştirildi. Klasör izinleri, kuruluşta hangi kullanıcıların posta kutusu klasörlerine ve klasördeki iletilere erişe bir denetimde bulunur.|
|Web uygulamasından gelen Outlook kuralı|Set-InboxRule|Posta kutusu sahibi veya posta kutusuna erişimi olan başka bir kullanıcı, Outlook web uygulamasını kullanarak gelen kutusu kuralını değiştirdi.|
|İletiler posta kutusundan temizildi|HardDelete|İleti Kurtarılabilir Öğeler klasöründen temiz edildi (posta kutusundan kalıcı olarak silindi).|
|Temsilci posta kutusu izinleri kaldırıldı|Remove-MailboxPermission|Yönetici, kişinin posta kutusundan Tam Erişim iznini (temsilciye atanmış olan izin) kaldırılmıştır. FullAccess izni kaldırıldıktan sonra, temsilci diğer kişinin posta kutusunu açamaz veya kişinin posta kutusuyla ilgili hiçbir içeriğe erişamaz.|
|Klasörden izinler kaldırıldı|RemoveFolderPermissions|Klasör izni kaldırılmıştır. Klasör izinleri, bir posta kutusu içinde yer alan klasörlere ve bu klasörlerde yer alan iletilere, kuruluşta hangi kullanıcıların eriş erişeni kontrol edin.|
|İleti gönderildi|Gönderin|İleti gönderildi, yanıtlandı veya iletildi. Bu etkinlik yalnızca lisans veya lisans Office 365 kullanıcılar için Microsoft 365 E5 kaydedilir. Daha fazla bilgi için, Gelişmiş Denetim'in "Gelişmiş Denetim olayları" [bölümüne bakın](advanced-audit.md#advanced-audit-events).|
|İleti Farklı Gönder izinleri kullanılarak gönderildi|SendAs|Farklı Gönder izni kullanılarak bir ileti gönderilmiştir. Bu, başka bir kullanıcının iletiyi, posta kutusu sahibinden geliyor gibi gönderdiği anlamına gelir.|
|İleti Adına Gönder izinleri kullanılarak gönderildi|SendOnBehalf|SendOnBehalf izni kullanılarak bir ileti gönderilmiştir. Bu, başka bir kullanıcının iletiyi posta kutusu sahibi adına gönderdiği anlamına gelir. İleti, iletinin kimin adına gönderildiğini ve aslında kim tarafından gönderildiğini alıcıya gösterir.|
|Outlook istemcisinde güncelleştirilmiş gelen Outlook kuralları|UpdateInboxRules|Posta kutusu sahibi veya posta kutusu kuralı oluşturulan, değiştirilen veya kaldırılan posta kutusuna erişimi olan başka bir kullanıcı, Outlook.|
|İleti güncelleştirildi|Güncelleştirme|İleti veya özellikleri değiştirilmiştir.|
|Kullanıcı posta kutusunda oturum etti|MailboxLogin|Kullanıcı posta kutusunda oturum alaştırdı.|
|İletiyi kayıt olarak etiketleme||Kullanıcı e-posta iletisine bir bekletme etiketi uyguladı ve bu etiket öğeyi kayıt olarak işaretlemek üzere yapılandırıldı. |
||||

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Posta kutusu denetim Exchange kayıtlarına sistem hesapları

Bazı posta kutusu etkinliklerinin (özellikle **Add-MailboxPermissions**) denetim kayıtlarında, etkinliği yapan (ve Kullanıcı ve KullanıcıKimliği alanlarında tanımlananları) NT AUTHORITY\SYSTEM veya NT AUTHORITY\SYSTEM(Microsoft.Exchange) olduğunu farkebilirsiniz. Servicehost). Bu, etkinliği gerçekleştiren "kullanıcı"nın Microsoft bulut Exchange bir sistem hesabı olduğunu gösterir. Bu sistem hesabı genellikle, kuruluş adına zamanlanmış bakım görevleri gerçekleştirir. Örneğin, NT AUTHORITY\SYSTEM(Microsoft.Exchange. ServiceHost) hesabı, sistem posta kutusu olan DiscoverySearchMailbox'ın izinlerini güncelleştirmektir. Bu güncelleştirmenin amacı, DiscoverySearchMailbox için Keşif Yönetimi rol grubuna FullAccess izninin (varsayılan olan) atandığı doğrulamaktır. Bu, eBulma yöneticilerinin kuruluşlarında gerekli görevleri gerçekleştireceklerini sağlar.

**Add-MailboxPermission** için bir denetim kaydında belirlenebilir başka bir sistem kullanıcı Administrator@apcprd03.prod.outlook.com. Bu hizmet hesabı, DiscoverySearchMailbox sistem posta kutusunun Keşif Yönetimi rol grubuna atanan FullAccess iznini doğrulama ve güncelleştirmeyle ilgili posta kutusu denetim kayıtlarına da dahildir. Özel olarak, Microsoft destek personeli Administrator@apcprd03.prod.outlook.com bir RBAC rolü tanılama aracı çalıştır çalıştırıyorsa, söz konusu hesapta yer alan denetim kayıtlarının tetiklenir.

### <a name="user-administration-activities"></a>Kullanıcı yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici hesabı Azure yönetim portalını kullanarak bir kullanıcı hesabını ekleyenin veya değiştirirken günlüğe kaydedilen kullanıcı Microsoft 365 yönetim merkezi etkinlikleri [](https://go.microsoft.com/fwlink/p/?linkid=2024339) listelemektedir.

> [!NOTE]
> Aşağıdaki tabloda bulunan İşlem **sütununda listelenen** işlem adları nokta ( ) içerir `.` . Denetim günlüğünde arama sırasında bir PowerShell komutunda işlemi belirtirken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi belirtirse, bu dönemi işlem adına dahil etmek gerekir. Ayrıca, işlem adını içeren çift tırnak işareti (`" "`) kullanmaya da dikkat etmek gerekir.

|Etkinlik|Operation|Açıklama|
|:-----|:-----|:-----|
|Kullanıcı eklendi|seçin.|Bir kullanıcı hesabı oluşturulmuş.|
|Kullanıcı lisansı değiştirildi|Kullanıcı lisansını değiştir'i seçin.|Kullanıcıya atanan lisans değiştirilmiştir. Hangi lisansların değişikliklerin olduğunu görmek için, ilgili Kullanıcı **güncelleştirildi etkinliğine** bakın.|
|Kullanıcı parolası değiştirildi|Kullanıcı parolasını değiştir'i seçin.|Kullanıcı parolasını değiştirir. Kullanıcıların kendi parolalarını sıfırlamasına izin vermek için, kendi kendine parola sıfırlamanın kurumda (tüm kullanıcılar veya seçili kullanıcılar için) etkinleştirilmesi gerekir. Ayrıca, kendi kendine parola sıfırlama etkinliğini aynı zamanda kendi Azure Active Directory. Daha fazla bilgi için bkz [. Azure AD parola yönetimi için raporlama seçenekleri](/azure/active-directory/authentication/howto-sspr-reporting).
|Kullanıcı silindi|Kullanıcı silme.|Bir kullanıcı hesabı silinmiştir.|
|Kullanıcı parolasını sıfırlama|Kullanıcı parolasını sıfırlayın.|Yönetici kullanıcının parolasını sıfırlar.|
|Kullanıcıya parola değiştirmesini gereken özellik ayarla|Kullanıcı parolasını değiştirmeye zorlar ayarlayın.|Yönetici, kullanıcının bir sonraki oturumda parolasını değiştirmesini gereken özelliği Microsoft 365.|
|Lisans özelliklerini ayarlama|Lisans özelliklerini ayarlama.|Yönetici, bir kullanıcıya atanan lisansın özellikleri üzerinde değişiklik yaptı.|
|Kullanıcı güncelleştirildi|Kullanıcı güncelleştirme.|Yönetici, kullanıcı hesabının bir veya birden çok özelliklerini değiştirir. Güncelleştirilebilir kullanıcı özelliklerinin listesi için, Denetim Raporu Olayları'nın "Kullanıcı özniteliklerini güncelleştirme" [Azure Active Directory bakın](/azure/active-directory/reports-monitoring/concept-audit-logs).|
||||

### <a name="azure-ad-group-administration-activities"></a>Azure AD grup yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici veya kullanıcı bir Microsoft 365 Grubu oluşturduğunda veya değiştirirken ya da yönetici Microsoft 365 yönetim merkezi veya Azure yönetim portalını kullanarak güvenlik grubu oluşturduğunda günlüğe kaydedilen grup yönetimi etkinlikleri listelemektedir.[](https://go.microsoft.com/fwlink/p/?linkid=2024339) Çalışma sayfalarındaki gruplar hakkında daha fazla Microsoft 365 için bkz. Çalışma sayfalarında [Grupları görüntüleme, Microsoft 365 yönetim merkezi](../admin/create-groups/create-groups.md).

> [!NOTE]
> Aşağıdaki tabloda bulunan İşlem **sütununda listelenen** işlem adları nokta ( ) içerir `.` . Denetim günlüğünde arama sırasında bir PowerShell komutunda işlemi belirtirken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi belirtirse, bu dönemi işlem adına dahil etmek gerekir. Ayrıca, işlem adını içeren çift tırnak işareti (`" "`) kullanmaya da dikkat etmek gerekir.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Grup eklendi|Grup ekle'yi seçin.|Bir grup oluşturulmuş.|
|Gruba üye eklendi|Gruba üye ekleme.|Gruba bir üye eklendi.|
|Grup silindi|Grubu sil'i seçin.|Bir grup silinmiştir.|
|Gruptan üye kaldırıldı|Gruptan üye kaldırma.|Gruptan bir üye kaldırılmıştır.|
|Grup güncelleştirildi|Grubu güncelleştir'i seçin.|Grubun özelliği değiştirilmiştir.|
||||

### <a name="application-administration-activities"></a>Uygulama yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici Azure AD'de kayıtlı bir uygulamayı ekleyenin veya bir uygulamayı değiştirirken günlüğe kaydedilen uygulama yöneticisi etkinlikleri listelemektedir. Kimlik doğrulaması için Azure AD'ye güvenen tüm uygulamanın dizine kaydedilmiş olması gerekir.

> [!NOTE]
> Aşağıdaki tabloda bulunan İşlem **sütununda listelenen** işlem adları nokta ( ) içerir `.` . Denetim günlüğünde arama sırasında bir PowerShell komutunda işlemi belirtirken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi belirtirse, bu dönemi işlem adına dahil etmek gerekir. Ayrıca, işlem adını içeren çift tırnak işareti (`" "`) kullanmaya da dikkat etmek gerekir.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Temsilci girdisi eklendi|Temsilci girdisi ekleme.|Azure AD'de bir uygulamaya kimlik doğrulama izni oluşturulmuş veya ve verilmiş.|
|Hizmet sorumlusu eklendi|Hizmet sorumlusu ekleme.|Uygulama Azure AD'ye kaydedilmiştir. Uygulama, dizinde bir hizmet sorumlusuyla temsil edildi.|
|Hizmet sorumlusuna kimlik bilgileri eklendi|Hizmet sorumlusu kimlik bilgilerini ekleyin.|Azure AD'de hizmet sorumlusuna kimlik bilgileri eklenmiştir. Hizmet ilkesi dizinde bir uygulamayı temsil eder.|
|Temsilci girdisi kaldırıldı|Temsilci girdisini kaldırma.|Azure AD'de bir uygulamada kimlik doğrulama izni kaldırılmıştır.|
|Dizinden hizmet sorumlusu kaldırıldı|Hizmet sorumlusu kaldırma.|Azure AD'den bir uygulama silinmiştir/kaydı silinmiştir. Uygulama, dizinde bir hizmet sorumlusuyla temsil edildi.|
|Hizmet sorumlusundan kimlik bilgileri kaldırıldı|Hizmet sorumlusu kimlik bilgilerini kaldırın.|Azure AD'de hizmet sorumlusundan kimlik bilgileri kaldırılmıştır. Hizmet ilkesi dizinde bir uygulamayı temsil eder.|
|Temsilci girdisini ayarlama|Temsilci girdisini ayarlama.|Azure AD'de bir uygulama için kimlik doğrulama izni güncelleştirilmiştir.|
||||

### <a name="role-administration-activities"></a>Rol yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici iş sayfasında veya Azure yönetim portalında yönetici rollerini yönetirken günlüğe kaydedilen Azure AD [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) etkinlikleri listelemektedir.

> [!NOTE]
> Aşağıdaki tabloda bulunan İşlem **sütununda listelenen** işlem adları nokta ( ) içerir `.` . Denetim günlüğünde arama sırasında bir PowerShell komutunda işlemi belirtirken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi belirtirse, bu dönemi işlem adına dahil etmek gerekir. Ayrıca, işlem adını içeren çift tırnak işareti (`" "`) kullanmaya da dikkat etmek gerekir.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Role üye ekleme|Role üye ekleme.|Grup yöneticisi rolüne bir kullanıcı Microsoft 365.|
|Kullanıcı dizin rolünden kaldırıldı|Üyeyi rolden kaldır.|Bir kullanıcı izinde yönetici rolünden Microsoft 365.|
|Şirket iletişim bilgilerini ayarlama|Şirket iletişim bilgilerini ayarlama.|Organizasyonunız için şirket düzeyinde iletişim tercihleri güncelleştirilmiştir. Bu, abonelikle ilgili olarak E-posta tarafından gönderilen e-posta Microsoft 365 ve hizmetlerle ilgili teknik bildirimleri içerir.|
||||

### <a name="directory-administration-activities"></a>Dizin yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici azure ad dizininde veya Azure yönetim portalında kuruluşunı yönetirken günlüğe kaydedilen[,](https://go.microsoft.com/fwlink/p/?linkid=2024339) Azure AD Microsoft 365 yönetim merkezi etkinlikleri listelemektedir.

> [!NOTE]
> Aşağıdaki tabloda bulunan İşlem **sütununda listelenen** işlem adları nokta ( ) içerir `.` . Denetim günlüğünde arama sırasında bir PowerShell komutunda işlemi belirtirken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi belirtirse, bu dönemi işlem adına dahil etmek gerekir. Ayrıca, işlem adını içeren çift tırnak işareti (`" "`) kullanmaya da dikkat etmek gerekir.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Şirkete etki alanı eklendi|Şirkete etki alanı ekleyin.|Organizasyona etki alanı eklendi.|
|Dizine iş ortağı eklendi|Şirkete iş ortağı ekleyin.|Kuruluşa iş ortağı (yönetici temsilcisi) eklendi.|
|Şirketten etki alanı kaldırıldı|Şirketten etki alanı kaldırma.|Etki alanı, kuruluştan kaldırıldı.|
|Dizinden iş ortağı kaldırıldı|Şirketten iş ortağı kaldırma.|Kuruluştan iş ortağı (yönetici temsilcisi) kaldırıldı.|
|Şirket bilgilerini ayarlama|Şirket bilgilerini ayarlama.|Kuruluşun şirket bilgileri güncelleştirilmiştir. Bu, abonelikle ilgili olarak E-posta hizmeti tarafından gönderilen Microsoft 365 e-posta adreslerini ve bu hizmetlerle ilgili teknik Microsoft 365 içerir.|
|Etki alanı kimlik doğrulamasını ayarlama|Etki alanı kimlik doğrulamasını ayarlayın.|Kurum için etki alanı kimlik doğrulama ayarı değiştirildi.|
|Etki alanı için federasyon ayarları güncelleştirildi|Etki alanında federasyon ayarlarını yapın.|Kuruluş için federasyon (dış paylaşım) ayarları değiştirildi.|
|Parola ilkesi ayarlama|Parola ilkesi ayarlama.|Kuruluşta kullanıcı parolalarının uzunluk ve karakter kısıtlamaları değiştirilmiştir.|
|Azure AD eşitlemesi açık|DirSyncEnabled bayrağını ayarlayın.|Dizin için etki alanı için bir dizini Azure AD Eşitleme.|
|Etki alanı güncelleştirildi|Etki alanını güncelleştir'i seçin.|Kuruluşta bir etki alanının ayarları güncelleştirildi.|
|Doğrulanmış etki alanı|Etki alanını doğrulama.|Kuruluşta bir etki alanının sahibi olduğu doğrulanmıştır.|
|Doğrulanmış e-postayla etki alanı doğrulandı|Doğrulanmış e-postayla etki alanını doğrulayın.|E-posta doğrulaması, kuruluşta bir etki alanının sahibi olduğunu doğrulamak için kullanılır.|
||||

### <a name="ediscovery-activities"></a>eBulma etkinlikleri

Güvenlik ve uyumluluk merkezinde veya ilgili PowerShell cmdlet'leri çalıştırarak gerçekleştirilen İçerik Arama ve eBulma ile ilgili etkinlikler denetim günlüğüne kaydedilir. Bu, aşağıdaki etkinlikleri içerir:

- eBulma servis durumlarını oluşturma ve yönetme

- İçerik Aramalarını oluşturma, başlatma ve düzenleme

- Arama sonuçlarını önizleme, dışarı aktarma ve silme gibi İçerik Arama eylemleri gerçekleştirme

- İçerik Arama için izin filtrelemeyi yapılandırma

- eBulma Yönetici rolünü yönetme

Günlüğe kaydedilen eBulma etkinliklerinin listesi ve ayrıntılı açıklaması için bkz. Denetim günlüğünde [eBulma etkinliklerini arama](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> **eBulma** etkinlikleri altında listelenen etkinliklerden ve Etkinlikler açılan listesinde **yer alan Advanced eDiscovery** etkinliklerinin arama sonuçlarında görüntülenebilir olması 30 dakika kadar sürer. Buna karşılık, eBulma cmdlet etkinliklerinden gelen ilgili olayların arama sonuçlarında görünmesi 24 saat kadar sürebilir.

### <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery etkinlikleri

Denetim günlüğünde, çalışma sayfalarındaki etkinlikler için Advanced eDiscovery. Bu etkinliklerin açıklaması için, denetim günlüğünde [eKbulma](search-for-ediscovery-activities-in-the-audit-log.md#advanced-ediscovery-activities) etkinliklerini arama Advanced eDiscovery" bölümüne bakın.

### <a name="power-bi-activities"></a>Power BI etkinlikleri

Denetim günlüğünde, çalışma sayfalarındaki etkinlikler için Power BI. Proje etkinliklerini Power BI için, "Power BI tarafından denetlenen etkinlikler" bölümüne ([Kurum içinde denetimi kullanma) bakın](/power-bi/service-admin-auditing#activities-audited-by-power-bi).

Denetim günlüğü Power BI varsayılan olarak etkin değildir. Denetim günlüğünde Power BI etkinlikleri aramak için bu yönetim portalında denetimi Power BI gerekir. Yönergeler için, yönetim portalında yer alan "Denetim günlükleri" [Power BI bakın](/power-bi/service-admin-portal#audit-logs).

### <a name="workplace-analytics-activities"></a>Workplace Analytics etkinlikleri

Workplace Analytics, grupların organizasyonunız genelinde nasıl işbirliği  olduğuyla ilgili içgörü sağlar. Aşağıdaki tabloda, workplace Analytics'te Yönetici rolüne veya Analist rollerine atanmış kullanıcılar tarafından gerçekleştirilen etkinlikler listelemektedir. Analist rolüne atanan kullanıcılar tüm hizmet özelliklerine tam erişime sahiptir ve çözümleme yapmak için ürünü kullanırlar. Yönetici rolüne atanan kullanıcılar gizlilik ayarlarını ve sistem varsayılanlarını yapılandırabilir ve workplace Analytics'te kurumsal verileri hazırlar, karşıya yükleyebilir ve doğrular. Daha fazla bilgi için bkz. [Workplace Analytics](/workplace-analytics/index-orig).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Erişilen OData bağlantısı|AccessedOdataLink|Analist sorgu için OData bağlantısına erişdi.|
|Sorgu iptal edildi|CanceledQuery|Analist çalışan sorguyu iptal etti.|
|Toplantı dışlaması oluşturuldu|MeetingExclusionCreated|Analist toplantı dışlama kuralı oluşturdu.|
|Silinen sonuç|DeletedResult|Analist sorgu sonuçlarını sildi.|
|Rapor indirildi|DownloadedReport|Analist sorgu sonuç dosyasını indirdi.|
|Yürütülür sorgu|ExecutedQuery|Analist bir sorgu çalıştırdı.|
|Güncelleştirilmiş veri erişimi ayarı|UpdatedDataAccessSetting|Yönetici veri erişim ayarlarını güncellemiştir.|
|Güncelleştirilmiş gizlilik ayarı|UpdatedPrivacySetting|Yönetici tarafından güncelleştirilmiş gizlilik ayarları; örneğin, en küçük grup boyutu.|
|Kuruluş verileri karşıya yüklendi|UploadedOrgData|Yönetici kuruluş veri dosyasını yükledi.|
|Kullanıcı oturum açtı<sup>*</sup>| UserLoggedIn |Bir kullanıcı kendi hesabıyla Microsoft 365 oturum açın.|
|Kullanıcı oturumu kapatıldı<sup>*</sup>| UserLoggedOff |Bir kullanıcı hesabıyla oturum Microsoft 365 oturumları.
|Araştırıldı|ViewedExplore|Bir veya birden çok Sayfa sekmesinde analist görünümü olan görsel öğeler.|
||||

> [!NOTE]
> <sup>*</sup>Bunlar, Azure Active Directory açma ve kapatma etkinlikleridir. Bu etkinlikler, kurumda Workplace Analytics'i açmasanız bile günlüğe kaydedilir. Kullanıcı oturum açma etkinlikleri hakkında daha fazla bilgi için bkz. Oturum [açma günlüklerinde Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>Microsoft Teams etkinlikleri

Denetim günlüğünde, kullanıcı ve yönetici etkinlikleri için arama Microsoft Teams. Teams, çalışma sayfalarındaki sohbet merkezi çalışma Microsoft 365. Ekibin konuşmalarını, toplantılarını, dosyalarını ve notlarını tek bir yerde bir araya getirir. Denetlenen en Teams açıklamaları için bkz. Denetim günlüğünde [denetlenen olayları Microsoft Teams](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Microsoft Teams Sağlık etkinlikleri

If your organization is using the [Patients application](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) in Microsoft Teams, you can search the audit log for activities for the using the Patients app. Ortamınız Hastalar uygulamasını destekleyecek şekilde yapılandırılmışsa Etkinlikler seçici listesinde bu etkinlikler için ek **bir etkinlik** grubu vardır.

![Microsoft Teams seçici listesinde Sağlık etkinlikleri'ne tıklayın.](../media/TeamsHealthcareAuditActivities.png)

Hastalar uygulaması etkinliklerinin açıklaması için bkz. Hastalar [uygulaması için denetim günlükleri](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Microsoft Teams Vardiyalar etkinlikleri

If your organization is usings app in Microsoft Teams, you can search the audit log for activities for the using the Shifts app. Ortamınız Vardiyalar uygulamalarını destekleyecek şekilde yapılandırılmışsa, Etkinlikler seçici listesinde bu etkinlikler için ek **bir etkinlik** grubu vardır.

Vardiyalar uygulama etkinliklerinin açıklaması için bkz. Denetim günlüğünde [Vardiyalar'daki olayları Microsoft Teams](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Yammer etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen Yammer ve yönetici etkinlikleri listele. Denetim Yammer ilgili etkinlikleri geri dönmek için, Etkinlikler listesinde Tüm etkinlikler için sonuçları **göster'i** **seçmeniz** gerekir. Arama sonuçlarını daraltmak için tarih **aralığı kutularını** ve Kullanıcılar listesini kullanın.

> [!NOTE]
> Bazı Yammer etkinlikleri yalnızca Gelişmiş Denetim'de kullanılabilir. Bu da, kullanıcıların denetim günlüğüne kaydedilmeden önce uygun lisansa atanmaları gerekir. Yalnızca Gelişmiş Denetim'de bulunan etkinlikler hakkında daha fazla bilgi için bkz. Gelişmiş [Microsoft 365](advanced-audit.md#advanced-audit-events). Gelişmiş Denetim lisans gereksinimleri için bkz[. Aşağıdaki Denetim çözümleri Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Aşağıdaki tabloda, Gelişmiş Denetim etkinlikleri yıldız (*) ile vurgulanır.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Veri bekletme ilkesi değiştirildi|SoftDeleteSettingsUpdated|Doğrulanmış yönetici ağ verileri bekletme ilkesi ayarını Kalıcı Olarak Sil veya Otomatik Olarak Sil olarak günceller. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirin.|
|Ağ yapılandırması değiştirildi|NetworkConfigurationUpdated|Ağ yöneticisi veya doğrulanmış yönetici Yammer yapılandırmasını değiştirir. Bu, verileri dışarı aktarma ve sohbeti etkinleştirme aralığını ayarlamayı içerir.|
|Ağ profili ayarları değiştirildi|ProcessProfileFields|Ağ yöneticisi veya doğrulanmış yönetici, ağ kullanıcıları için üye profillerde görünen bilgileri değiştirir.|
|Özel içerik modu değiştirildi|SupervisorAdminToggled|Doğrulanmış yönetici,  *Özel İçerik Modu'ni*  çalışır veya kapatmış olur. Bu mod, yöneticinin özel gruplarda yer alan gönderileri ve bireysel kullanıcılar (veya kullanıcı grupları) arasındaki özel iletileri görüntüleyebiliyor. Yalnızca doğrulanmış yöneticiler bu işlemi gerçekleştirin.|
|Güvenlik yapılandırması değiştirildi|NetworkSecurityConfigurationUpdated|Doğrulanmış yönetici, Yammer yapılandırmasını günceller. Bu, parola süre sonu ilkelerini ve IP adreslerinde kısıtlamaları ayarlamayı içerir. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirin.|
|Dosya oluşturuldu|FileCreated|Kullanıcı dosyayı karşıya yükler.|
|Grup oluşturuldu|GroupCreation|Kullanıcı bir grup oluşturur.|
|İleti oluşturuldu<sup>*</sup>|MessageCreated|Kullanıcı bir ileti oluşturur.|
|Grup silindi|GroupDeletion|Gruptan bir grup Yammer.|
|İleti silindi|MessageDeleted|Kullanıcı iletiyi sildi.|
|İndirilen dosya|FileDownloaded|Kullanıcı dosyayı indirir.|
|Dışarı aktarıldı veriler|DataExport|Doğrulanmış yönetici, Yammer verilerini dışarı aktarıyor. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirin.|
|Topluluk erişimi başarısız oldu<sup>*</sup>|CommunityAccessFailure|Kullanıcı bir topluluka erişemedi.|
|Dosyaya erişim başarısız oldu<sup>*</sup>|FileAccessFailure|Kullanıcı bir dosyaya erişemedi.|
|İletiye erişemedi<sup>*</sup>|MessageAccessFailure|Kullanıcı bir iletiye erişemedi.|
|Dosya paylaşıldı|FileShared|Kullanıcı bir dosyayı başka bir kullanıcıyla paylaştığında.|
|Ağ kullanıcısı askıya alındı|NetworkUserSuspended|Ağ yöneticisi veya doğrulanmış yönetici kullanıcının askıya alınmasına (devre dışı bırak) Yammer.|
|Kullanıcı askıya alındı|UserSuspension|Kullanıcı hesabı askıya alındı (devre dışı bırakıldı).|
|Dosya açıklaması güncelleştirildi|FileUpdateDescription|Kullanıcı dosyanın açıklamasını değiştirir.|
|Dosya adı güncelleştirildi|FileUpdateName|Kullanıcı dosyanın adını değiştirir.|
|İleti güncelleştirildi<sup>*</sup>|MessageUpdated|Kullanıcı iletiyi günceller.|
|Dosya görüntülandı|FileVisited|Kullanıcı dosyayı görüntüler.|
|İleti görüntü alındı<sup>*</sup>|MessageViewed|Kullanıcı iletiyi görüntüler.|
||||

### <a name="microsoft-power-automate-activities"></a>Microsoft Power Automate etkinlikleri

Denetim günlüğünde, bir günlükte (eski adı Power Automate etkinlik) için Microsoft Flow. Bu etkinlikler, akışları oluşturma, düzenleme ve silmeyi ve akış izinlerini değiştirmeyi içerir. Etkinlik etkinliklerini denetleme hakkında Power Automate için, web günlüğünde Power Automate [denetim etkinliklerinin kullanılabilir olduğu bloga Microsoft 365 uyumluluk merkezi](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Microsoft Power Apps etkinlikleri

Denetim günlüğünde, herhangi bir uygulamada uygulamayla ilgili etkinlikler için Power Apps. Bu etkinlikler bir uygulama oluşturmayı, başlatmayı ve yayımlamayı içerir. Uygulamalara izin atama da denetlenebilir. Tüm etkinlik etkinliklerini Power Apps için bkz. Günlük [Power Apps](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Microsoft Stream etkinlikleri

Microsoft Stream'de etkinlikler için denetim günlüğünde arama yapın. Bu etkinlikler, kullanıcılar tarafından gerçekleştirilen video etkinliklerini, grup kanalı etkinliklerini ve kullanıcıları yönetme, kuruluş ayarlarını yönetme ve raporları dışarı aktarma gibi yönetici etkinliklerini içerir. Bu etkinliklerin açıklaması için Microsoft Stream'de Denetim Günlükleri'nin "Stream'de günlüğe kaydedilen [eylemler" bölümüne bakın](/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>İçerik gezgini etkinlikleri

Aşağıdaki tabloda, içerik gezgininde denetim günlüğüne kaydedilen etkinlikler listeledir. Aşağıdaki kaynakta yer alan Veri sınıflandırmaları aracında erişilen içerik Microsoft 365 uyumluluk merkezi. Daha fazla bilgi için bkz [. Veri sınıflandırma içerik gezginini kullanma](data-classification-content-explorer.md).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Öğeye erişildi|LabelContentExplorerAccessedItem|Yönetici (veya İçerik Gezgini İçerik Görüntüleyicisi rol grubunun üyesi olan bir kullanıcı) e-posta iletisi veya belgeyi görüntülemek için içerik SharePoint/OneDrive kullanır.|
||||

### <a name="quarantine-activities"></a>Etkinlikleri karantinaya alın

Aşağıdaki tabloda, denetim günlüğünde arayabilirsiniz karantina etkinlikleri liste almaktadır. Karantina hakkında daha fazla bilgi için bkz. [E-posta iletilerini karantinaya alındı](../security/office-365-security/quarantine-email-messages.md).

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Karantina iletisi silindi|KarantinaDelete|Bir kullanıcı zararlı olduğu kabulilen bir e-posta iletisi sildi.|
|Karantina iletisi dışarı aktarıldı|QuarantineExport|Bir kullanıcı zararlı olduğu kabulilen bir e-posta iletisi dışarı aktardı.|
|Önizlemeli karantina iletisi|KarantinaPreview|Bir kullanıcı zararlı olduğu kabulilen bir e-posta iletisi önizlemesi yaptı.|
|İleti karantinaya alındı|KarantinaRelease|Bir kullanıcı karantinadan alınan ve zararlı olduğu kabulilen bir e-posta iletisi yayımladı.|
|Karantina iletisi üst bilgisi görüntü alındı|QuarantineViewHeader|Bir kullanıcı üst bilgide, zararlı olduğu kabul edildi bir e-posta iletisi görüntüledi.|
||||

### <a name="microsoft-forms-activities"></a>Microsoft Forms etkinlikleri

Bu bölümdeki tablolarda, Microsoft Forms'da denetim günlüğüne kaydedilen kullanıcı ve yönetici etkinlikleri yer almaktadır. Microsoft Forms analiz için veri toplamak için kullanılan bir form/test/anket aracıdır. Açıklamalarda aşağıda belirtilenin, bazı işlemler ek etkinlik parametreleri içerir.

Bir Forms etkinliği ortak yazar veya anonim yanıtlayan tarafından gerçekleştirilse, biraz daha farklı bir şekilde günlüğe kaydedilir. Daha fazla bilgi için ortak [yazarlar ve anonim yanıtlayanlar tarafından gerçekleştirilen Forms etkinlikleri bölümüne](#forms-activities-performed-by-coauthors-and-anonymous-responders) bakın.

> [!NOTE]
> Bazı Forms denetim etkinlikleri yalnızca Gelişmiş Denetim'de kullanılabilir. Bu da, kullanıcıların denetim günlüğüne kaydedilmeden önce uygun lisansa atanmaları gerekir. Yalnızca Gelişmiş Denetim'de bulunan etkinlikler hakkında daha fazla bilgi için bkz. Gelişmiş [Microsoft 365](advanced-audit.md#advanced-audit-events). Gelişmiş Denetim lisans gereksinimleri için bkz[. Aşağıdaki Denetim çözümleri Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Aşağıdaki tabloda, Gelişmiş Denetim etkinlikleri yıldız (*) ile vurgulanır.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Açıklama oluşturuldu|CreateComment|Form sahibi teste yorum veya puan ekler.|
|Form oluşturuldu|CreateForm|Form sahibi yeni bir form oluşturur. <br><br>Property DataMode:string, geçerli formun yeni veya var olan bir Excel değeri DataSync'e eşitlene kadar ayar olduğunu gösterir. Özelliği ExcelWorkbookLink:string geçerli formun Excel çalışma kitabı kimliğini gösterir.|
|Düzenlenen form|Formu Düzenle|Form sahibi soru oluşturma, kaldırma veya düzenleme gibi bir formu düzenler. *EditOperation:string özelliği*, düzenleme işlemi adını gösterir. Olası işlemler:<br/>- CreateQuestion<br/>- CreateQuestionChoice <br/>- DeleteQuestion <br/>- DeleteQuestionChoice <br/>- DeleteFormImage <br/>- DeleteQuestionImage <br/>- UpdateQuestion <br/>- UpdateQuestionChoice <br/>- UploadFormImage/Bing/OneDrive <br/>- UploadQuestionImage <br/>- ChangeTheme <br><br>FormImage, Forms'da kullanıcının bir sorgu veya arka plan teması gibi bir resim yükleyage tüm yerlerini içerir.|
|Form taşındı|MoveForm|Form sahibi formu taşır. <br><br>Property DestinationUserId:string, formu hareket eden kişinin kullanıcı kimliğini gösterir. Property NewFormId:string, yeni kopyalanan formun yeni kimliğidir. Property IsDelegateAccess:boolean, geçerli form taşıma eyleminin yönetici temsilci sayfası üzerinden gerçekleştirileni gösterir.|
|Form silindi|DeleteForm|Form sahibi formu siler. Buna SoftDelete (kullanılan silme seçeneği ve geri dönüşüm kutusu'na taşınan form) ve HardDelete (Geri dönüşüm kutusu boşaltıldı) dahildir.|
|Görüntülenen form (tasarım süresi)|Görünüm Formu|Form sahibi mevcut bir formu düzenleme için açar. <br><br>Özellik Erişimi Reddedildi:boolean, izin denetimi nedeniyle geçerli formun erişiminin reddedilmiş olduğunu gösterir. Özellik FromSummaryLink:boolean özet bağlantı sayfasından geçerli isteğin olduğunu gösterir.|
|Önizlemesi yapılan form|Önizleme Formu|Form sahibi, Preview işlevini kullanarak formun önizlemesini gösterir.|
|Form dışarı aktarıldı|Dışarı Aktarma Formu|Form sahibi sonuçları başka bir Excel. <br><br>Özellik Dışarı Aktarma Biçimi:dize, Excel İndir veya Çevrimiçi olduğunu gösterir.|
|Kopyalama için izin verilen paylaşım formu|AllowShareFormForCopy|Form sahibi formu diğer kullanıcılarla paylaşmak için bir şablon bağlantısı oluşturur. Form sahibi şablon URL'sini oluşturmak için tıkladığında bu olay günlüğe kaydedilir.|
|Kopyalama için izin verilmeyen paylaşım formu|DisallowShareFormForCopy|Form sahibi şablon bağlantısını siler.|
|Form birlikte yazar eklendi|AddFormCoauthor|Kullanıcı, yanıtların tasarımına/görünümüne yardımcı olmak için işbirliği bağlantısı kullanır. Bu olay, kullanıcı bir collab URL'si kullandığında günlüğe kaydedilir (collab URL'si ilk kez oluşturulmaz).|
|Form birlikte yazar kaldırıldı|RemoveFormCoauthor|Form sahibi işbirliği bağlantısını siler.|
|Yanıt sayfası görüntü alındı|ViewRuntimeForm|Kullanıcı görüntülemek için bir yanıt sayfası açtı. Kullanıcı yanıt gönderip göndermese de göndermese de bu olay günlüğe kaydedilir.|
|Yanıt oluşturuldu|CreateResponse|Yeni yanıt almaya benzer.  Bir kullanıcı forma yanıt gönderttirdi. <br><br>Property ResponseId:string and Property ResponderId:string hangi sonucun görüntü görüntülemekte olduğunu gösterir. <br><br>Anonim bir yanıtlayan için, ResponderId özelliği null olur.|
|Yanıt güncelleştirildi|UpdateResponse|Form sahibi testte bir açıklamayı veya puanı güncellemiştir. <br><br>Property ResponseId:string and Property ResponderId:string hangi sonucun görüntü görüntülemekte olduğunu gösterir. <br><br>Anonim bir yanıtlayan için, ResponderId özelliği null olur.|
|Tüm yanıtlar silindi|DeleteAllResponses|Form sahibi tüm yanıt verilerini siler.|
|Yanıt silindi|DeleteResponse|Form sahibi bir yanıtı siler. <br><br>Property ResponseId:string, silinen yanıtı gösterir.|
|Yanıtlar görüntü edildi|ViewResponses|Form sahibi toplanan yanıtların listesini görüntüler. <br><br>Özellik Görünüm Türü:dize, form sahibinin Ayrıntı'nın mı yoksa Toplama'nın mı görüntüleyle ilgili olduğunu gösterir|
|Yanıt görüntü alındı|ViewResponse|Form sahibi belirli bir yanıtı görüntüler. <br><br>Property ResponseId:string and Property ResponderId:string hangi sonucun görüntü görüntülemekte olduğunu gösterir. <br><br>Anonim bir yanıtlayan için, ResponderId özelliği null olur.|
|Özet bağlantısı oluşturuldu|GetSummaryLink|Form sahibi sonuçları paylaşmak için özet sonuçları bağlantısı oluşturur.|
|Silinen özet bağlantısı|DeleteSummaryLink|Form sahibi özet sonuçları bağlantısını siler.|
|Güncelleştirilmiş form kimlik avı durumu|UpdatePhishingStatus|Son güvenlik durumunun değişip değişmemiş olup olmadığı önemli değildir (örneğin, form artık Kapalı veya Açık durumda olsa da, iç güvenlik durumu için ayrıntılı değer her değiştirnişinde bu olay günlüğe kaydedilir). Bu, yinelenen olayları son bir güvenlik durumu değişikliği olmadan da göreceğinizi anlamına gelir. Bu olayın olası durum değerleri şöyledir:<br/>- Take Down <br/>- Yönetici tarafından Aşağı Al <br/>- Yönetici Engeli Kaldırıldı <br/>- Otomatik Engellendi <br/>- Otomatik Engellemesi Kaldır <br/>- Müşteri Bildirildi <br/>- MüşteriYi Sıfırla Bildirdi|
|Kullanıcı kimlik avı durumu güncelleştirildi|UpdateUserPhishingStatus|Kullanıcı güvenliği durumuna göre değeri her değiştirişte bu olay günlüğe kaydedilir. Kullanıcı Microsoft Online güvenlik ekibi tarafından ele alınan bir kimlik avı  formu oluşturduğunda denetim kaydında kullanıcı durumunun Değeri Kimlik AvıCı Olarak Onaylanır. Yönetici kullanıcının engellemesini kaldırırsa, kullanıcının durumu değeri Normal Kullanıcı Olarak Sıfırla **olarak ayarlanır**.|
|Gönderilmiş Formlar Pro daveti|ProInvitation|Kullanıcı bir denemeyi etkinleştirmek Pro tıkladığında.|
|Form ayarı güncelleştirildi<sup>*</sup> |UpdateFormSetting|Form sahibi bir veya birden çok form ayarlarını günceller. <br><br>Özellik FormSettingName:string güncelleştirilmiş hassas ayarların adını gösterir. Property NewFormSettings:string, güncelleştirilmiş ayarların adını ve yeni değerini gösterir. Özellik thankYouMessageContainsLink:boolean, güncelleştirilmiş teşekkür iletisinde URL bağlantısı olduğunu belirtir.|
|Kullanıcı ayarı güncelleştirildi|UpdateUserSetting|Form sahibi kullanıcı ayarını günceller. <br><br>Özellik UserSettingName:string ayarın adını ve yeni değerini gösterir|
|Listelenen formlar<sup>*</sup>|Liste Formları|Form sahibi formların listesini görüntü alıyor. <br><br>Özellik Görünüm Türü:dize, form sahibinin hangi görünümde olduğunu gösterir: Tüm Formlar, Benimle Paylaşılan veya Grup Formları|
|Yanıt gönderildi|SubmitResponse|Kullanıcı forma bir yanıt gönderdi. <br><br>IsInternalForm:boolean özelliği, yanıtlayan, form sahibiyle aynı kuruluş içinde ise bunu gösterir.|
|Etkinleştirildi herkes yanıtla ayarı<sup>*</sup>|AllowAnonymousResponse|Form sahibi, herhangi birinin formu yanıtlamasına izin veren ayarı etkinleştirir.|
|Devre dışı bırakılmış herkes yanıtla ayarı<sup>*</sup>|DisallowAnonymousResponse|Form sahibi, herhangi birinin formu yanıtlamasına izin veren ayarı devre dışı bırakır.|
|Belirli kişiler yanıt yanıtla ayarını etkinleştirdi<sup>*</sup>|EnableSpecificResponse|Form sahibi, yalnızca geçerli kuruluşta yer alan belirli kişilerin veya belirli grupların formu yanıtlamasına izin veren ayarı etkinleştirir.|
|Devre dışı bırakılmış belirli kişiler yanıt olabilir ayarı<sup>*</sup>|DisableSpecificResponse|Form sahibi, yalnızca geçerli kuruluşta yer alan belirli kişilerin veya belirli grupların formu yanıtlamasına izin veren ayarı devre dışı bırakır.|
|Belirli bir yanıtlayan eklendi<sup>*</sup>|AddSpecificResponder|Form sahibi, belirli yanıtlayanlar listesine yeni bir kullanıcı veya grup ekler.|
|Belirli bir yanıtlayan kaldırıldı<sup>*</sup>|RemoveSpecificResponder|Form sahibi belirli yanıtlayanlar listesinden bir kullanıcı veya grubu kaldırır.|
|Devre dışı bırakılmış işbirliği<sup>*</sup>|DisableCollaboration|Form sahibi, formda işbirliği ayarını devre dışı bırakır.|
|İş Office 365 veya okul hesabı işbirliği için etkinleştirildi<sup>*</sup>|EnableWorkOrSchoolCollaboration|Form sahibi, iş veya okul hesabı olan Microsoft 365 form görüntülemelerine ve düzenlemelerine izin veren ayarı etkinleştirir.|
|Kuruluşumda birlikte çalışan kişiler etkinleştirildi<sup>*</sup>|EnableSameOrgCollaboration|Form sahibi, geçerli kuruluşta yer alan kullanıcıların formu görüntülemelerine ve düzenlemelerine izin veren ayarı etkinleştirir.|
|Belirli kişiler işbirliği etkinleştirildi<sup>*</sup>|EnableSpecificCollaboaration|Form sahibi, yalnızca geçerli kuruluşta yer alan belirli kişilerin veya belirli grupların formu görüntüleme ve düzenlemelerine izin veren ayarı etkinleştirir.|
|Çalışma kitabına Excel bağlandı<sup>*</sup>|ConnectToExcelWorkbook|Formu bir çalışma kitabına Excel. <br><br>Özelliği ExcelWorkbookLink:string geçerli formun Excel çalışma kitabı kimliğini gösterir.|
|Koleksiyon oluşturuldu|CollectionCreated|Form sahibi bir koleksiyon oluşturdu.|
|Koleksiyon güncelleştirildi|CollectionUpdated|Form sahibi koleksiyon özelliğini günceller.|
|Geri Dönüşüm Kutusu'dan koleksiyonu silindi|Collection Biraçıkla|Form sahibi Geri Dönüşüm Kutusu'dan bir koleksiyonu kalıcı olarak sildi.|
|Koleksiyonu Geri Dönüşüm Kutusu'na taşındı|CollectionSoftDeleted|Form sahibi koleksiyonu Geri Dönüşüm Kutusu'na taşıdı.|
|Koleksiyonu yeniden adlandırıldı|CollectionRenamed|Form sahibi koleksiyonun adını değiştirdi.|
|Formu koleksiyona taşıdı|MovedFormIntoCollection|Form sahibi formu koleksiyona taşıdı.|
|Formu koleksiyonun dışarı taşındı|MovedFormOutofCollection|Form sahibi formu koleksiyonun dışarı taşıdı.|
||||

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Ortak yazarlar ve anonim yanıtlayanlar tarafından gerçekleştirilen form etkinlikleri

Formlar tasar olduğunda ve yanıtları çözümlerken işbirliğini destekler. Form işbirliği yapan, ortak yazar *olarak bilinir*. Birlikte yazar olarak, formu silme veya taşıma dışında, form sahibinin yapanın her şeyi birlikte yazar. Formlar, anonim olarak yanıt ver kullanıcılara yanıt ver veren bir form oluşturmanıza da olanak sağlar. Bu, yanıtlayanların bir formu yanıtlamak için kuruluşta oturumlarının olması gerek olmadığını anlamına gelir.

Aşağıdaki tabloda, ortak yazarlarla anonim yanıtlayanlar tarafından gerçekleştirilen etkinlikler için denetim kaydında yer alan denetim etkinlikleri ve bilgileri açık almaktadır.

|Etkinlik türü|İç veya dış kullanıcı|Günlüğe kaydedilen kullanıcı kimliği|Oturum açan kuruluş|Forms kullanıcı türü|
|:-----|:-----|:-----|:-----|:-----|
|Birlikte yazar etkinlikleri|İç|UPN|Form sahibinin kuruluş|Birlikte yazar|
|Birlikte yazar etkinlikleri|Dış|UPN<br>|Birlikte yazarla kuruluş<br>|Birlikte yazar|
|Birlikte yazar etkinlikleri|Dış|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(Kimliğin ikinci bölümü karmadır ve farklı kullanıcılar için farklıdır)|Form sahibinin kuruluş<br>|Birlikte yazar|
|Yanıt etkinlikleri|Dış|UPN<br>|Yanıtlayan'ın kuruluş şeması<br>|Yanıtlayan|
|Yanıt etkinlikleri|Dış|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(Kullanıcı Kimliğinin ikinci bölümü karmadır ve farklı kullanıcılar için farklıdır)|Form sahibinin kuruluş|Yanıtlayan|
|Yanıt etkinlikleri|Anonim|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(Kullanıcı Kimliğinin ikinci bölümü karmadır ve farklı kullanıcılar için farklıdır)|Form sahibinin kuruluş|Yanıtlayan|
||||

### <a name="sensitivity-label-activities"></a>Duyarlılık etiketi etkinlikleri

Aşağıdaki tabloda duyarlılık etiketlerinin kullanımından sonuç olan [olaylar listele.](sensitivity-labels.md)

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
|Siteye duyarlılık etiketi uygulandı|SensitivityLabelApplied|Bir siteye veya siteye SharePoint Teams.|
|Duyarlılık etiketi siteden kaldırıldı|SensitivityLabelRemoved|Bir siteden veya siteden SharePoint Teams kaldırıldı.|
|Dosyaya duyarlılık etiketi uygulandı|FileSensitivityLabelApplied|Belgeye, Microsoft 365 uygulamaları kullanılarak bir duyarlılık Web üzerinde Office. veya otomatik etiketleme ilkesi gibi bir ilkeye de neden olabilir.|
|Dosyaya uygulanan duyarlılık etiketi değiştirildi|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|Bir belgeye farklı bir duyarlılık etiketi uygulanmış. <br /><br>Bu etkinliğin işlemleri, etiketin nasıl değiştirildiklarına bağlı olarak değişir:<br /> - Web üzerinde Office etiketleme ilkesi (FileSensitivityLabelChanged) <br /> - Microsoft 365 uygulamaları (SensitivityLabelUpdated)|
|Sitenin duyarlılık etiketi değiştirildi|SensitivityLabelChanged|Bir siteye veya siteye farklı bir duyarlılık SharePoint Teams.|
|Duyarlılık etiketi dosyadan kaldırıldı|FileSensitivityLabelRemoved|Duyarlılık etiketi, Microsoft 365 uygulamaları, Web üzerinde Office, otomatik etiket ilkesi veya [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'i kullanılarak belgeden kaldırılmıştır.|
||||

### <a name="retention-policy-and-retention-label-activities"></a>Bekletme ilkesi ve bekletme etiketi etkinlikleri

Aşağıdaki tabloda, oluşturulan, [yeniden yapılandırılan](retention.md) veya silinen bekletme ilkeleri ve bekletme etiketlerine yönelik yapılandırma etkinlikleri açıklandı.

|Kolay ad|Operation|Açıklama|
|:-----|:-----|:-----|
| Uyarlanabilir kapsam üyeliği değiştirildi |ApplicableAdaptiveScopeChange |Kullanıcılar, siteler veya gruplar uyarlanabilir kapsama eklenmiştir veya bu kapsamdan kaldırılmıştır. Bu değişiklikler, kapsamın sorgusunu çalıştırmanın sonuçlarıdır. Değişiklikler sistem tarafından başlatıldıklarından, bildirilen kullanıcı kullanıcı hesabı yerine GUID olarak görüntülenir.|
| Bekletme ilkesi için yapılandırılmış ayarlar |NewRetentionComplianceRule |Yönetici, yeni bir bekletme ilkesi için bekletme ayarlarını yapılandırdı. Bekletme ayarları, öğelerin ne kadar korunacaklarını ve bekletme süresi dolduğunda öğelere ne olacağını (öğeleri silme, öğeleri tutma veya saklama ve sonra da silme gibi) içerir. Bu etkinlik, [New-RetentionComplianceRule cmdlet'ini çalıştırmaya](/powershell/module/exchange/new-retentioncompliancerule) da karşılık gelir.|
| Uyarlanabilir kapsam oluşturuldu |NewAdaptiveScope |Yönetici uyarlanabilir bir kapsam oluşturdu.|
| Bekletme etiketi oluşturuldu |NewComplianceTag |Yönetici yeni bir bekletme etiketi oluşturdu.|
| Bekletme ilkesi oluşturuldu |NewRetentionCompliancePolicy|Yönetici yeni bir bekletme ilkesi oluşturdu.|
| Silinmiş uyarlanabilir kapsam | RemoveAdaptiveScope| Yönetici uyarlanabilir kapsamı sildi.|
| Bekletme ilkesinden silinen ayarlar| RemoveRetentionComplianceRule<br/>| Yönetici, bekletme ilkesi yapılandırma ayarlarını sildi. Yönetici bir bekletme ilkesi silebilir veya [Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule) cmdlet'ini çalıştırıyorsa, büyük olasılıkla bu etkinlik günlüğe kaydedilir.|
| Silinmiş bekletme etiketi |RemoveComplianceTag | Yönetici bir bekletme etiketini sildi.|
| Silinmiş bekletme ilkesi |RemoveRetentionCompliancePolicy<br/> |Yönetici bir bekletme ilkesi sildi. |
| Bekletme etiketleri için mevzuat kaydı seçeneği etkinleştirildi<br/> |SetRestrictiveRetentionUI |Yönetici, [Set-RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) cmdlet'ini son olarak, bir yöneticinin bekletme etiketi için kullanıcı arabirimi yapılandırma seçeneğini seçerek içeriği yasal düzenleme kaydı olarak işaretlemesi için kullandı.|
| Güncelleştirilmiş uyarlanabilir kapsam | SetAdaptiveScope | Yönetici, var olan bir uyarlanabilir kapsam için açıklamayı veya sorguyu değiştirdi. |
| Bekletme ilkesi için güncelleştirilmiş ayarlar | SetRetentionComplianceRule | Yönetici, var olan bir bekletme ilkesi için bekletme ayarlarını değiştirmiştir. Bekletme ayarları, öğelerin ne kadar korunacaklarını ve bekletme süresi dolduğunda öğelere ne olacağını (öğeleri silme, öğeleri tutma veya saklama ve sonra da silme gibi) içerir. Bu etkinlik, [Set-RetentionComplianceRule cmdlet'ini çalıştırmaya](/powershell/module/exchange/set-retentioncompliancerule) da karşılık gelir. |
| Güncelleştirilmiş bekletme etiketi |SetComplianceTag  | Yönetici, var olan bir bekletme etiketini güncellemiştir.|
| Güncelleştirilmiş bekletme ilkesi |SetRetentionCompliancePolicy |Yönetici var olan bir bekletme ilkesi güncellemiştir. Bu olayı tetikleyen güncelleştirmeler, bekletme ilkesine uygulanan içerik konumlarını eklemeyi veya hariç tutmayı içerir.|
||||

### <a name="briefing-email-activities"></a>E-posta etkinliklerini brifing

Aşağıdaki tabloda, Brifing e-postası içinde yer alan ve denetim günlüğüne Microsoft 365 liste vardır. Brifing e-postası hakkında daha fazla bilgi için bkz:

- [Brifing e-postası'ne genel bakış](/Briefing/be-overview)

- [Brifing e-postası yapılandırma](/Briefing/be-admin)

|**Kolay ad**|**Operation**|**Açıklama**|
|:----|:-----|:-----|
|Güncelleştirilmiş kuruluş gizlilik ayarları|UpdatedOrganizationBriefingSettings|Yönetici, Brifing e-postası için kuruluş gizlilik ayarlarını günceller. |
|Güncelleştirilmiş kullanıcı gizlilik ayarları|UpdatedUserBriefingSettings|Yönetici, Brifing e-postası için kullanıcı gizlilik ayarlarını günceller.
||||

### <a name="myanalytics-activities"></a>MyAnalytics etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen MyAnalytics etkinlikleri Microsoft 365 listele. MyAnalytics hakkında daha fazla bilgi için bkz. [Yöneticiler için MyAnalytics](/workplace-analytics/myanalytics/overview/mya-for-admins).

|**Kolay ad**|**Operation**|**Açıklama**|
|:-----|:-----|:-----|
|Güncelleştirilmiş kuruluş MyAnalytics ayarları|UpdatedOrganizationMyAnalyticsSettings|Yönetici MyAnalytics için kuruluş düzeyinde ayarları günceller. |
|Güncelleştirilmiş kullanıcı MyAnalytics ayarları|UpdatedUserMyAnalyticsSettings|Yönetici MyAnalytics için kullanıcı ayarlarını günceller.|
||||

### <a name="information-barriers-activities"></a>Bilgi engelleri etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen bilgi engellerinin etkinlikleri Microsoft 365. Bilgi engelleri hakkında daha fazla bilgi için bkz. Engelin ortadan [kaldıran bilgi Microsoft 365](information-barriers.md).

|**Kolay ad**|**Operation**|**Açıklama**|
|:----------------|:------------|:--------------|
| Siteye kesimler eklendi | SegmentsAdded | Bir SharePoint yöneticisi, genel yönetici veya site sahibi site için bir veya birden çok bilgi engeli ekledi. |
| Sitenin kesimleri değiştirildi | SegmentsChanged | Bir SharePoint yöneticisi veya genel yönetici sitenin bir veya daha fazla bilgi kesiminin kesimlerini değiştirmiştir. |
| Siteden kesimler kaldırıldı | SegmentsRemoved | Bir SharePoint yöneticisi veya genel yönetici sitenin bir veya daha fazla bilgi engelini kaldırılmıştır. |
||||

### <a name="disposition-review-activities"></a>Disposition review activities

Aşağıdaki tabloda, bir öğe yapılandırılmış bekletme döneminin sonuna geldiğinde gözden geçirenin edatını inceleyen etkinlikleri listelemektedir. Daha fazla bilgi için bkz [. İçeriği görüntüleme ve görüntüleme](disposition.md#viewing-and-disposing-of-content).

|**Kolay ad**|**Operation**|**Açıklama**|
|:-----|:-----|:-----|
|Onayın onayı|OnaylamaSeski|Disposition gözden geçiren biri, öğeyi bir sonraki konumlandırma aşamasına taşımak için öğenin yok olduğunu onaylar. Öğe, disposition gözden geçirmenin tek veya son aşamasında ise, disposition onayı öğeyi kalıcı silme için uygun olarak işaretledi.|
|Uzatılmış bekletme süresi|ExtendRetention|Disposition gözden geçiren öğenin bekletme süresi uzatıldı.|
|Yeniden etiketli öğe|RelabelItem|A disposition reviewer relabeled the retention label.|
|Gözden geçirenler eklendi|AddReviewer|Bir disposition gözden geçiren geçerli disposition gözden geçirme aşamasına bir veya daha fazla kullanıcı ekledi.|
||||

### <a name="communication-compliance-activities"></a>İletişim uyumluluğu etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen iletişim uyumluluk Microsoft 365 listele. Daha fazla bilgi için bkz[. Web'de iletişim Microsoft 365](communication-compliance.md).

|**Kolay ad**|**Operation**|**Açıklama**|
|:-----|:-----|:-----|
|İlke güncelleştirmesi|SupervisionPolicyCreated, VeliSaatPolicyUpdated, VeliSaat|İletişim uyumluluk yöneticisi bir ilke güncelleştirmesi gerçekleştirdi.|
|İlke eşleşmesi|UzleMatch|Kullanıcı bir ilkenin koşuluna eşleşen bir ileti gönderdi.|
|İletilere uygulanan etiket|SupervisoryReviewTag|Etiketler iletilere veya iletilere uygulanır; çözülür.|
||||

### <a name="report-activities"></a>Etkinlikleri bildirme

Aşağıdaki tabloda, denetim günlüğüne kaydedilen kullanım raporlarına Microsoft 365 listele.

|**Kolay ad**|**Operation**|**Açıklama**|
|:-----|:-----|:-----|
|Güncelleştirilmiş kullanım raporu gizlilik ayarları|UpdateUsageReportsPrivacySetting|Yönetici tarafından kullanım raporları için gizlilik ayarları güncelleştirildi. |
||||

### <a name="exchange-admin-audit-log"></a>Exchange denetim günlüğü

Exchange yöneticisi denetim günlüğü (Microsoft 365'ta varsayılan olarak etkindir) yönetici (veya yönetim izinleri atanmış bir kullanıcı) Exchange Online kuruluşunda bir değişiklik yaptıktan sonra denetim günlüğünde bir olayı günlüğe kaydeder. Exchange yönetim merkezi kullanılarak veya Exchange Online'de cmdlet çalıştırarak yapılan değişiklikler, Exchange yönetici denetim günlüğüne kaydedilir. **Get-**, **Search** veya **Test** fiilleriyle başlayan cmdlet'ler denetim günlüğüne kaydedilmez. Oturum açmada yönetici denetim günlüğüyle ilgili daha ayrıntılı Exchange için bkz. [Yönetici denetim günlüğü](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Yönetici Exchange Online günlüğüne (veya denetim günlüğüne) oturum Exchange bazı yeni cmdlet'ler vardır. Bu cmdlet'lerin birçoğu müşteri hizmetleriyle Exchange Online ve Microsoft veri merkezi personeli veya hizmet hesapları tarafından çalıştırıldı. Bu cmdlet'ler, çok sayıda "gürültülü" denetim olaylarının ortaya çıkarılamay olduğundan günlüğe kaydedilmez. Denetlenen bir Exchange Online cmdlet'i varsa, lütfen Microsoft Desteği'ne bir tasarım değişikliği isteği (DCR) gönderin.

Burada, denetim günlüğünde arama Exchange yönetici etkinliklerini aramak için bazı ipuçları ve almaktadırsınız:

- Yönetici denetim günlüğünden girdilerin Exchange için, Etkinlikler listesinde Tüm etkinlikler için sonuçları  **göster'i seçmeniz** gerekir. Arama sonuçlarını, Exchange belirli bir tarih  aralığında belirli bir tarih aralığında belirli bir yönetici tarafından çalıştıracak şekilde daraltmak için, tarih aralığı kutularını ve Kullanıcılar listesini kullanın.

- Yönetici denetim günlüğünden olayları Exchange için, Etkinlik sütununa tıklar ve  cmdlet adlarını alfabetik düzende sıralar.

- Hangi cmdlet'in çalıştırıldısı, hangi parametrelerin ve parametre değerlerinin kullanılmış olduğu ve hangi nesnelerin etkilendiği hakkında bilgi almak için Tüm sonuçları indir seçeneğini belirterek arama **sonuçlarını dışarı aktarabilirsiniz** . Daha fazla bilgi için bkz [. Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

- Ayrıca, Exchange Online `Search-UnifiedAuditLog -RecordType ExchangeAdmin` PowerShell'de bu komutu kullanarak yalnızca yönetici denetim günlüğünden Exchange getirebilirsiniz. Arama sonuçlarında ilgili denetim günlüğü girdisi için bir Exchange cmdlet'i çalıştırıldıktan sonra 30 dakika kadar sürebilir. Daha fazla bilgi için bkz. [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). **Search-UnifiedAuditLog** cmdlet'i tarafından döndürülen arama sonuçlarını bir CSV dosyasına aktarma hakkında bilgi için, Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme konusunda yer alan "İpuçları denetim günlüğünü dışarı aktarma ve görüntüleme" bölümüne [bakın](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Ayrıca, Exchange Exchange yönetim merkezini kullanarak veya Exchange Online PowerShell'de **Search-AdminAuditLog'u** çalıştırarak da Exchange Online görüntüabilirsiniz. Bu, özellikle yöneticiler tarafından gerçekleştirilen etkinlikleri aramak için iyi bir Exchange Online olur. Yönergeler için bkz:

  - [Yönetici denetim günlüğünü görüntüleme](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Aynı yönetici etkinliklerinin aynı Exchange hem yönetici denetim günlüğüne hem de denetim Exchange günlüğe kaydedileceğini unutmayın.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Şu anda Microsoft 365 olan hizmetler arasında ne fark vardır?**

Exchange Online, SharePoint Online, OneDrive İş, Azure Active Directory, Microsoft Teams, Dynamics 365, Office 365 için Defender gibi en çok kullanılan hizmetler ve Power BI denetime alındı. Denetlenen [hizmetlerin listesi için](search-the-audit-log-in-security-and-compliance.md) bu makalenin başına bakın.

**Microsoft 365'te denetim hizmeti tarafından hangi etkinlikler Microsoft 365?**

Denetlenen [etkinliklerin listesi](#audited-activities) ve açıklaması için bu makaledeki Denetlenen etkinlikler bölümüne bakın.

**Denetim kaydının bir olay gerçekleştikten sonra kullanılabilir olması ne kadar zaman alır?**

Çoğu denetim verisi 30 dakika içinde kullanılabilir ancak ilgili denetim günlüğü girişinin arama sonuçlarında görüntülensi için bir olayın gerçekleşmesi 24 saat kadar sürebilir. Farklı hizmetlerde yer [alan olayların](#before-you-search-the-audit-log) ne kadar süreyle kullanılabilir olacağını gösteren, bu makalenin Denetim günlüğünde aramadan önce bölümündeki tabloya bakın.

**Denetim kayıtları ne kadar süreyle korunur?**

Daha önce de belirtildiği gibi, microsoft e5 lisansı atanmış kullanıcılar (Office 365 E5 veya Microsoft 365 E5 eklenti lisansına sahip kullanıcılar) tarafından gerçekleştirilen etkinlikler için denetim kayıtları bir yıl süreyle korunur. Birleşik denetim günlüğünü destekleyen diğer tüm aboneliklerde, denetim kayıtları 90 gün boyunca korunur.

**Denetim verilerine programatik olarak erişebilir miyim?**

Evet. Denetim Office 365 api'si, denetim günlüklerini programatik olarak getirmek için kullanılır.  Çalışmaya başlama için bkz[. Yönetim API'lerini Office 365 başlama](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Güvenlik ve uyumluluk merkezini veya Office 365 Yönetim Etkinliği API'sini kullanma dışında denetim günlükleri Office 365 var mı?**

Hayır. Denetim hizmetlerinden veri almak için tek yol bunlardır.

**Denetim günlüklerini yakalamak istediğim her hizmette denetimi tek tek etkinleştirmem gerekir mi?**

Hizmetlerin çoğunda, siz başlangıçta organizasyonunız için denetimi etkinleştirdikten sonra denetim varsayılan olarak etkinleştirilir (bu makaledeki Denetim günlüğünde aramadan [](#before-you-search-the-audit-log) önce bölümünde açıklanmıştır).

**Denetim hizmeti kayıtların yeniden çoğaltılmasında destek var mı?**

Hayır. Denetim hizmeti pipeline is near real time, and therefore can't support de-duplication.

**Denetim verileri nerede depolanır?**

Şu anda NA (Kuzey Amerika), EMEA (Avrupa, Orta Doğu ve Afrika) ve APAC (Asya Pasifik) bölgelerinde potansiyel dağıtımları denetlemektedir. Bu bölgelerde yer alan kiracıların denetim verileri bu bölgede depolanır. Çok coğrafi kiracılı kiracılarda, kiracının tüm bölgelerinden toplanan denetim verileri yalnızca kiracının giriş bölgesinde depolanır. Bununla birlikte, verileri yük dengeleme için ve yalnızca canlı site sorunları sırasında bu bölgeler arasında akışla akariz. Bu etkinlikleri gerçekleştir verileri gerçekleştirdir, iletilim verileri şifrelenir. 

**Verileri denetleme şifrelenmiş mi?**

Denetim verileri, birleşik denetim Exchange dağıtıldığında aynı bölgede yer alan posta kutularında (saklanan veriler) depolanır. Posta kutusu verileri, posta kutusu tarafından şifrelenmez Exchange. Bununla birlikte, Microsoft veri merkezlerindeki veri sunucularının sayısı BitLocker Exchange, hizmet düzeyinde şifreleme tüm posta kutusu verilerini şifreler. Daha fazla bilgi için bkz[. Microsoft 365 Encryption for Skype Kurumsal, OneDrive İş, SharePoint Online, and Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Geçişte olan posta verileri her zaman şifrelenir.
