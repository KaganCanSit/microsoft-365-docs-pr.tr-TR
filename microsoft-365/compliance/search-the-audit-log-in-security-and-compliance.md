---
title: Microsoft Purview uyumluluk portalı denetim günlüğünde arama yapma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Kuruluşunuzdaki kullanıcı ve yönetici etkinliğini görüntülemek üzere birleşik denetim günlüğünde arama yapmak için Microsoft Purview uyumluluk portalı kullanın.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: 9d556facba3fa1a9c1dbafbfe2b2cb519f1b362d
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810976"
---
# <a name="search-the-audit-log-in-the-compliance-portal"></a>Uyumluluk portalında denetim günlüğünde arama yapma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kullanıcının belirli bir belgeyi görüntüleyip görüntülemediğini veya bir öğeyi posta kutusundan temizleyip temizlemediğini bulmanız mı gerekiyor? Öyleyse, kuruluşunuzdaki kullanıcı ve yönetici etkinliğini görüntülemek üzere birleşik denetim günlüğünde arama yapmak için Microsoft Purview uyumluluk portalı'deki denetim günlüğü arama aracını kullanabilirsiniz. Onlarca Microsoft 365 hizmeti ve çözümünde gerçekleştirilen binlerce kullanıcı ve yönetici işlemi, kuruluşunuzun birleşik denetim günlüğünde yakalanır, kaydedilir ve saklanır. Kuruluşunuzdaki kullanıcılar, bu işlemlerin denetim kayıtlarını aramak, görüntülemek ve dışarı aktarmak (CSV dosyasına) için denetim günlüğü arama aracını kullanabilir.

## <a name="microsoft-365-services-that-support-auditing"></a>Denetimi destekleyen Microsoft 365 hizmetleri

Neden birleşik denetim günlüğü? Çünkü denetim günlüğünde farklı Microsoft 365 hizmetlerinde gerçekleştirilen etkinlikleri arayabilirsiniz. Aşağıdaki tabloda, birleşik denetim günlüğü tarafından desteklenen Microsoft 365 hizmetleri ve özellikleri (alfabetik sırada) listelenmektedir.

| Microsoft 365 hizmeti veya özelliği | Kayıt türleri|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| İletişim uyumluluğu|ComplianceSuperVisionExchange|
| İçerik gezgini|LabelContentExplorer|
| Veri bağlayıcıları|ComplianceConnector|
| Veri kaybı önleme (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| Ediscovery|Bulma, AeD|
| Tam Veri Eşleşmesi|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Forms|MicrosoftForms|
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
| Tehdit Analizi|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|

Önceki tabloda listelenen hizmetlerin her birinde denetlenen işlemler hakkında daha fazla bilgi için bu makaledeki [Denetlenen etkinlikler](#audited-activities) bölümüne bakın.

Önceki tabloda, Exchange Online PowerShell'de **Search-UnifiedAuditLog** cmdlet'ini kullanarak veya bir PowerShell betiği kullanarak ilgili hizmetteki etkinlikler için denetim günlüğünde arama yapmak için kullanılacak kayıt türü değeri de tanımlanır. Bazı hizmetlerin aynı hizmet içindeki farklı etkinlik türleri için birden çok kayıt türü vardır. Denetim kaydı türlerinin daha eksiksiz bir listesi için bkz. [Office 365 Yönetim Etkinliği API'si şeması](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Denetim günlüğünde arama yapmak için PowerShell kullanma hakkında daha fazla bilgi için bkz:

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Denetim günlüğünü aramak için PowerShell betiği kullanma](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Denetim günlüğünde arama yapmadan önce

Denetim günlüğünde arama yapmaya başlamadan önce aşağıdaki öğeleri okuduğunuzdan emin olun.

- Microsoft 365 ve Office 365 kuruluşlarında denetim günlüğü araması varsayılan olarak açıktır. Denetim günlüğü aramasının açık olduğunu doğrulamak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  *UnifiedAuditLogIngestionEnabled* özelliğinin değeri`True`, denetim günlüğü aramasının açık olduğunu gösterir. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md).

- Denetim günlüğünde arama yapmak için Exchange Online'da View-Only Denetim Günlükleri veya Denetim Günlükleri rolüne atanmış olmanız gerekir. Varsayılan olarak, bu roller Exchange yönetim merkezindeki **İzinler** sayfasındaki Uyumluluk Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Office 365 ve Microsoft 365'deki genel yöneticiler otomatik olarak Exchange Online'da Kuruluş Yönetimi rol grubunun üyeleri olarak eklenir. Kullanıcıya en düşük ayrıcalık düzeyiyle denetim günlüğünde arama yapma olanağı vermek için, Exchange Online'da özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve kullanıcıyı yeni rol grubunun bir üyesi olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [Exchange Online rol gruplarını yönetme](/Exchange/permissions-exo/role-groups).

  > Kullanıcıya uyumluluk portalındaki İzinler sayfasında View-Only Denetim **Günlükleri veya Denetim Günlükleri** rolü atarsanız, denetim günlüğünde arama yapamaz. İzinleri Exchange Online atamanız gerekir. Bunun nedeni, denetim günlüğünde arama yapmak için kullanılan temel cmdlet'in Exchange Online bir cmdlet olmasıdır.

- Bir kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirildiğinde, bir denetim kaydı oluşturulur ve kuruluşunuz için denetim günlüğünde depolanır. Denetim kaydının tutulacak süresi (ve denetim günlüğünde aranabilir) Office 365 veya Microsoft 365 Kurumsal aboneliğinize ve özellikle belirli kullanıcılara atanan lisansın türüne bağlıdır.

  - Office 365 E5 veya Microsoft 365 E5 lisansı (veya Microsoft 365 E5 Uyumluluk veya Microsoft 365 E5 eBulma ve Denetim eklentisi lisansına sahip kullanıcılar) atanan kullanıcılar için, Azure Active Directory, Exchange ve SharePoint etkinliği varsayılan olarak bir yıl boyunca saklanır. Kuruluşlar ayrıca diğer hizmetlerdeki etkinliklerin denetim kayıtlarını bir yıla kadar saklamak için denetim günlüğü saklama ilkeleri oluşturabilir. Daha fazla bilgi için bkz. [Denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md).

    > [!NOTE]
    > Kuruluşunuz denetim kayıtlarının bir yıllık saklaması için özel önizleme programına katıldıysa, genel kullanılabilirlik dağıtım tarihinden önce oluşturulan denetim kayıtlarının saklama süresi sıfırlanmaz.

  - Başka herhangi bir (E5 olmayan) Office 365 veya Microsoft 365 lisansı atanmış kullanıcılar için denetim kayıtları 90 gün boyunca saklanır. Birleşik denetim günlüğünü destekleyen Office 365 ve Microsoft 365 aboneliklerinin listesi için [güvenlik ve uyumluluk portalı hizmet açıklamasına](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center) bakın.

    > [!NOTE]
    > Posta kutusu denetimi varsayılan olarak açık olsa bile, uyumluluk portalında veya Office 365 Yönetim Etkinliği API'sinde bazı kullanıcılar için posta kutusu denetim olaylarının denetim günlüğü aramalarında bulunmadığını fark edebilirsiniz. Daha fazla bilgi için bkz. [Posta kutusu denetim günlüğü hakkında daha fazla bilgi](enable-mailbox-auditing.md#more-information).

- Kuruluşunuz için denetim günlüğü aramasını kapatmak istiyorsanız, Exchange Online kuruluşunuza bağlı uzak PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Denetim aramasını yeniden açmak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Daha fazla bilgi için bkz. [Denetim günlüğü aramasını kapatma](turn-audit-log-search-on-or-off.md).

- Daha önce belirtildiği gibi, denetim günlüğünde arama yapmak için kullanılan temel alınan cmdlet, **Search-UnifiedAuditLog** olan bir Exchange Online cmdlet'idir. Bu, uyumluluk portalındaki **Denetim** sayfasındaki arama aracını kullanmak yerine denetim günlüğünde arama yapmak için bu cmdlet'i kullanabileceğiniz anlamına gelir. Bu cmdlet'i Exchange Online PowerShell'de çalıştırmanız gerekir. Daha fazla bilgi için bkz [. Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  **Search-UnifiedAuditLog** cmdlet'i tarafından döndürülen arama sonuçlarını csv dosyasına dışarı aktarma hakkında bilgi için, Denetim [günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log) bölümündeki "Denetim günlüğünü dışarı aktarma ve görüntüleme İpuçları" bölümüne bakın.

- Denetim günlüğünden program aracılığıyla veri indirmek istiyorsanız, PowerShell betiği kullanmak yerine Office 365 Yönetim Etkinliği API'sini kullanmanızı öneririz. Office 365 Yönetim Etkinliği API'si, kuruluşunuz için işlemler, güvenlik ve uyumluluk izleme çözümleri geliştirmek için kullanabileceğiniz bir REST web hizmetidir. Daha fazla bilgi için bkz. [Office 365 Yönetim Etkinliği API başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference).

- Azure Active Directory (Azure AD), Microsoft 365 için dizin hizmetidir. Birleşik denetim günlüğü, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> veya Azure yönetim portalında gerçekleştirilen kullanıcı, grup, uygulama, etki alanı ve dizin etkinliklerini içerir. Azure AD olaylarının tam listesi için bkz. [Denetim Raporu Olayları Azure Active Directory](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Microsoft, ilgili denetim kaydının bir denetim günlüğü aramasının sonuçlarında döndürülmesi için bir olay gerçekleştikten sonra belirli bir süreyi garanti etmez. Temel hizmetler (Exchange, SharePoint, OneDrive ve Teams gibi) için denetim kaydı kullanılabilirliği genellikle bir olay gerçekleştikten sonra 60 ile 90 dakika arasındadır. Diğer hizmetler için denetim kaydı kullanılabilirliği daha uzun olabilir. Ancak, kaçınılmaz olan bazı sorunlar (sunucu kesintisi gibi) denetim kayıtlarının kullanılabilirliğini geciktiren denetim hizmetinin dışında oluşabilir. Bu nedenle, Microsoft belirli bir zamana bağlanmaz.

- Power BI için denetim günlüğü varsayılan olarak etkin değildir. Denetim günlüğünde Power BI etkinlik aramak için, Power BI yönetici portalında denetimi etkinleştirmeniz gerekir. Yönergeler için Power BI [yönetici portalındaki](/power-bi/service-admin-portal#audit-logs) "Denetim günlükleri" bölümüne bakın.

## <a name="search-the-audit-log"></a>Denetim günlüğünde arama yapma

Microsoft 365'da denetim günlüğünde arama yapma işlemi aşağıdadır.

[1. Adım: Denetim günlüğü araması çalıştırma](#step-1-run-an-audit-log-search)

[2. Adım: Arama sonuçlarını görüntüleme](#step-2-view-the-search-results)

[3. Adım: Arama sonuçlarını bir dosyaya aktarma](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>1. Adım: Denetim günlüğü araması çalıştırma

1. <https://compliance.microsoft.com> adresine gidin ve oturum açın.

    > [!TIP]
    > Uyumluluk portalına erişmek için özel gözatma oturumu (normal oturum değil) kullanın çünkü bu, şu anda oturum açtığınız kimlik bilgilerinin kullanılmasını engeller. Microsoft Edge'da InPrivate Gözatma oturumu veya Google Chrome'da özel gözatma oturumu (gizli pencere olarak adlandırılır) açmak için **CTRL+SHIFT+N** tuşlarına basın.

2. Uyumluluk portalının sol bölmesinde **Denetim'e** tıklayın.

    **Denetim** sayfası görüntülenir.

    ![Ölçütleri yapılandırın ve ardından raporu çalıştırmak için Ara'ya tıklayın.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > **Kullanıcı ve yönetici etkinliği kaydını başlat** bağlantısı görüntüleniyorsa, denetimi açmak için bu bağlantıya tıklayın. Bu bağlantıyı görmüyorsanız, kuruluşunuz için denetim açıktır.

3. **Arama** sekmesinde aşağıdaki arama ölçütlerini yapılandırın:

   1. **Başlangıç tarihi** ve **Bitiş tarihi**: Son yedi gün varsayılan olarak seçilidir. Bu dönemde gerçekleşen olayları görüntülemek için bir tarih ve saat aralığı seçin. Tarih ve saat yerel saatte gösterilir. Belirtebileceğiniz maksimum tarih aralığı 90 gündür. Seçilen tarih aralığı 90 günden büyükse bir hata görüntülenir.

    > [!TIP]
    > En fazla 90 gün tarih aralığı kullanıyorsanız **Başlangıç tarihi** için geçerli saati seçin. Aksi takdirde, başlangıç tarihinin bitiş tarihinden önce olduğunu belirten bir hata alırsınız. Son 90 gün içinde denetimi açtıysanız, maksimum tarih aralığı denetimin açıldığı tarihten önce başlayamaz.

   2. **Etkinlikler**: Arayabileceğiniz etkinlikleri görüntülemek için açılan listeye tıklayın. Kullanıcı ve yönetici etkinlikleri ilgili etkinlik grupları halinde düzenlenir. Belirli etkinlikleri seçebilir veya etkinlik grubu adına tıklayarak gruptaki tüm etkinlikleri seçebilirsiniz. Seçimi temizlemek için seçili bir etkinliğe de tıklayabilirsiniz. Aramayı çalıştırdıktan sonra, yalnızca seçili etkinlikler için denetim günlüğü girişleri görüntülenir. **Tüm etkinlikler için sonuçları göster** seçildiğinde, seçilen kullanıcı veya kullanıcı grubu tarafından gerçekleştirilen tüm etkinliklerin sonuçları görüntülenir.<br/><br/>Denetim günlüğüne 100'den fazla kullanıcı ve yönetici etkinliği kaydedilir. Farklı hizmetlerin her birindeki her etkinliğin açıklamalarını görmek için bu makalenin konu başlığındaki **Denetlenen etkinlikler** sekmesine tıklayın.

   3. **Kullanıcılar**: Bu kutuya tıklayın ve arama sonuçlarını görüntülemek üzere bir veya daha fazla kullanıcı seçin. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliğin denetim günlüğü girişleri, sonuç listesinde görüntülenir. Kuruluşunuzdaki tüm kullanıcıların (ve hizmet hesaplarının) girdilerini döndürmek için bu kutuyu boş bırakın.

   4. **Dosya, klasör veya site**: Belirtilen anahtar sözcüğü içeren klasör dosyasıyla ilgili etkinliği aramak için bir dosya veya klasör adının bir kısmını veya tümünü yazın. Ayrıca bir dosya veya klasörün URL'sini de belirtebilirsiniz. URL kullanıyorsanız, tam URL yolunu yazdığınızdan veya URL'nin bir bölümünü yazdığınızdan emin olun, özel karakter veya boşluk eklemeyin (ancak joker karakter (\*) kullanılması desteklenir).<br/><br/>Kuruluşunuzdaki tüm dosya ve klasörlerin girdilerini döndürmek için bu kutuyu boş bırakın.

    > [!TIP]
    >
    > - **Bir siteyle** ilgili tüm etkinlikleri arıyorsanız, url'nin arkasına joker karakteri (\*) ekleyerek bu sitenin tüm girdilerini döndürebilirsiniz; örneğin, `"https://contoso-my.sharepoint.com/personal*"`.
    >
    > - Bir **dosyayla** ilgili tüm etkinlikleri arıyorsanız, dosya adının önüne joker karakteri (\*) ekleyerek bu dosyanın tüm girdilerini (örneğin, `"*Customer_Profitability_Sample.csv"`) döndürebilirsiniz.

4. Arama ölçütlerinizi kullanarak aramayı çalıştırmak için **Ara'ya** tıklayın.

   Arama sonuçları yüklenir ve birkaç dakika sonra yeni bir sayfada görüntülenir. Arama tamamlandığında, bulunan sonuç sayısı görüntülenir. 150 olaylık artışlarla en fazla 50.000 olay görüntülenir. Arama ölçütlerini karşılayan 50.000'den fazla olay varsa, yalnızca döndürülen 50.000 sıralanmamış olay görüntülenir.

   ![Arama tamamlandıktan sonra sonuç sayısı görüntülenir.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Denetim günlüğünde arama için İpuçları

- Etkinlik adına tıklayarak aranacak belirli etkinlikleri seçebilirsiniz. Ya da grup adına tıklayarak bir gruptaki tüm etkinlikleri ( **Dosya ve klasör etkinlikleri** gibi) arayabilirsiniz. Bir etkinlik seçiliyse, seçimi iptal etmek için bu etkinliğe tıklayabilirsiniz. Yazdığınız anahtar sözcüğü içeren etkinlikleri görüntülemek için arama kutusunu da kullanabilirsiniz.

  ![Tüm etkinlikleri seçmek için etkinlik grubu adına tıklayın.](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Exchange yönetici denetim günlüğündeki olayları görüntülemek için **Etkinlikler** listesindeki **tüm etkinlikler için sonuçları göster'i** seçmeniz gerekir. Bu denetim günlüğündeki olaylar, sonuçlardaki **Etkinlik** sütununda bir cmdlet adı (örneğin, **Set-Mailbox**) görüntüler. Daha fazla bilgi için bu **konudaki Denetlenen etkinlikler** sekmesine tıklayın ve ardından **yönetici etkinlikleri Exchange** tıklayın.

  Benzer şekilde, **Etkinlikler** listesinde karşılık gelen bir öğeye sahip olmayan bazı denetim etkinlikleri vardır. Bu etkinlikler için işlemin adını biliyorsanız, tüm etkinlikleri arayabilir ve arama sonuçlarını bir CSV dosyasına aktardıktan sonra işlemleri filtreleyebilirsiniz.

- Geçerli arama ölçütlerini temizlemek için **Temizle'ye** tıklayın. Tarih aralığı, son yedi günün varsayılan değerini döndürür. Tüm seçili etkinlikleri iptal **etmek üzere tüm etkinliklerin sonuçlarını göstermek için Tümünü temizle'ye** de tıklayabilirsiniz.

- 50.000 sonuç bulunursa, büyük olasılıkla arama ölçütlerine uyan 50.000'den fazla olay olduğunu varsayabilirsiniz. Arama ölçütlerini daraltabilir ve daha az sonuç döndürmek için aramayı yeniden çalıştırabilir veya Sonuçları \> **dışarı aktar** **Tüm sonuçları indir'i** seçerek arama sonuçlarının tümünü dışarı aktarabilirsiniz.

### <a name="step-2-view-the-search-results"></a>2. Adım: Arama sonuçlarını görüntüleme

Denetim günlüğü aramasının sonuçları Denetim **günlüğü arama** sayfasındaki **Sonuçlar** altında görüntülenir. Daha önce belirtildiği gibi, en fazla 50.000 (en yeni) olay 150 olaylık artışlarla görüntülenir. Sonraki 150 olayı görüntülemek için kaydırma çubuğunu kullanın veya **Shift + End** tuşlarına basın.

Sonuçlar, arama tarafından döndürülen her olay hakkında aşağıdaki bilgileri içerir:

- **Tarih**: Olayın gerçekleştiği tarih ve saat (yerel saatinizde).

- **IP adresi**: Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi IPv4 veya IPv6 adres biçiminde görüntülenir.

   > [!NOTE]
  > Bazı hizmetler için, bu alanda görüntülenen değer, etkinliği gerçekleştiren kişinin kullandığı cihazın IP adresi değil, kullanıcı adına hizmete çağrı yapan güvenilir bir uygulamanın IP adresi (örneğin, Web üzerinde Office uygulamalar) olabilir. Ayrıca, Azure Active Directory ile ilgili olaylar için yönetici etkinliği (veya bir sistem hesabı tarafından gerçekleştirilen etkinlik) için IP adresi günlüğe kaydedilmez ve bu alanda görüntülenen değer olur`null`.

- **Kullanıcı**: Olayı tetikleyen eylemi gerçekleştiren kullanıcı (veya hizmet hesabı).

- **Etkinlik**: Kullanıcı tarafından gerçekleştirilen etkinlik. Bu değer **, Etkinlikler** açılan listesinde seçtiğiniz etkinliklere karşılık gelir. Exchange yönetici denetim günlüğündeki bir olay için bu sütundaki değer bir Exchange cmdlet'idir.

- **Öğe**: İlgili etkinliğin sonucu olarak oluşturulan veya değiştirilen nesne. Örneğin, görüntülenen veya değiştirilen dosya veya güncelleştirilen kullanıcı hesabı. Tüm etkinliklerin bu sütunda değeri yoktur.

- **Ayrıntı**: Etkinlik hakkında ek bilgiler. Yine, tüm etkinliklerin bir değeri yoktur.

> [!TIP]
> Sonuçları sıralamak için **Sonuçlar'ın** altında bir sütun başlığına tıklayın. Sonuçları A'dan Z'ye veya Z'den A'ya sıralayabilirsiniz. Sonuçları en eskiden en yeniye veya en yeniden en eskiye sıralamak için **Tarih** üst bilgisine tıklayın.

#### <a name="view-the-details-for-a-specific-event"></a>Belirli bir olayın ayrıntılarını görüntüleme

Arama sonuçları listesinde olay kaydına tıklayarak bir olay hakkında daha fazla ayrıntı görüntüleyebilirsiniz. Olay kaydındaki ayrıntılı özellikleri içeren bir açılır sayfa görüntülenir. Görüntülenen özellikler, olayın gerçekleştiği hizmete bağlıdır. 

### <a name="step-3-export-the-search-results-to-a-file"></a>3. Adım: Arama sonuçlarını bir dosyaya aktarma

Denetim günlüğü aramasının sonuçlarını yerel bilgisayarınızdaki virgülle ayrılmış değer (CSV) dosyasına aktarabilirsiniz. Bu dosyayı Microsoft Excel açabilir ve arama, sıralama, filtreleme ve tek bir sütunu (birden çok özellik içeren) birden çok sütuna bölme gibi özellikleri kullanabilirsiniz.

1. Bir denetim günlüğü araması çalıştırın ve istediğiniz sonuçları elde edene kadar arama ölçütlerini düzeltin.

2. Arama sonuçları sayfasında Dışarı **Aktar** > **Tüm sonuçları indir'e** tıklayın.

   Denetim günlüğünden arama ölçütlerine uyan tüm girdiler CSV dosyasına aktarılır. Denetim günlüğündeki ham veriler bir CSV dosyasına kaydedilir. Denetim günlüğü girdisindeki ek bilgiler CSV'de **AuditData** adlı bir sütuna eklenir.

     > [!IMPORTANT]
     > Tek bir denetim günlüğü aramasından CSV dosyasına en fazla 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den fazla olay olduğunu varsayabilirsiniz. Bu sınırdan daha fazlasını dışarı aktarmak için, denetim günlüğü girdilerinin sayısını azaltmak için bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girişi dışarı aktarmak için daha küçük tarih aralıklarıyla birden çok arama çalıştırmanız gerekebilir.

3. Dışarı aktarma işlemi tamamlandıktan sonra pencerenin üst kısmında CSV dosyasını açmanızı ve yerel bilgisayarınıza kaydetmenizi isteyen bir ileti görüntülenir. CSV dosyasına İndirmeler klasöründen de erişebilirsiniz.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Denetim günlüğü arama sonuçlarını dışarı aktarma ve görüntüleme hakkında daha fazla bilgi

- Tüm arama sonuçlarını indirdiğinizde CSV dosyası **CreationDate**, **UserIds**, **Operations** ve **AuditData** sütunlarını içerir. **AuditData** sütunu her olay hakkında ek bilgiler içerir (uyumluluk portalında arama sonuçlarını görüntülediğinizde açılır sayfada görüntülenen ayrıntılı bilgilere benzer). Bu sütundaki veriler, denetim günlüğü kaydından birden çok özellik içeren bir JSON nesnesinden oluşur. JSON nesnesindeki her *özellik:değer* çifti virgülle ayrılır. **AuditData** sütununu birden çok sütuna bölerek JSON nesnesindeki her özelliğin kendi sütununa sahip olması için Excel'daki Power Query Düzenleyicisi JSON dönüştürme aracını kullanabilirsiniz. Bu, bu özelliklerden birini veya daha fazlasını sıralamanıza ve filtrelemenize olanak tanır. JSON nesnesini dönüştürmek için Power Query Düzenleyicisi kullanarak adım adım yönergeler için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

  **AuditData** sütununu böldükten sonra, belirli bir etkinlik türünün ayrıntılı özelliklerini görüntülemek için **İşlemler** sütununu filtreleyebilirsiniz.

- Farklı hizmetlerden olaylar içeren bir arama sorgusundan tüm sonuçları indirdiğinizde, CSV dosyasındaki **AuditData** sütunu eylemin hangi hizmette gerçekleştirildiğine bağlı olarak farklı özellikler içerir. Örneğin, Exchange ve Azure AD denetim günlüklerindeki girdiler, eylemin başarılı olup olmadığını gösteren **ResultStatus** adlı bir özellik içerir. Bu özellik SharePoint'daki olaylara dahil değildir. Benzer şekilde, SharePoint olayları, dosya ve klasörle ilgili etkinlikler için site URL'sini tanımlayan bir özelliğe sahiptir. Bu davranışı azaltmak için, etkinliklerin sonuçlarını tek bir hizmetten dışarı aktarmak için farklı aramalar kullanmayı göz önünde bulundurun.

  Tüm sonuçları ve her birinin geçerli olduğu hizmeti indirdiğinizde CSV dosyasındaki **AuditData** sütununda listelenen özelliklerin birçoğunun açıklaması için bkz. [Denetim günlüğündeki Ayrıntılı özellikler](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Denetlenen etkinlikler

Bu bölümdeki tablolarda, Microsoft 365 denetlenen etkinlikler açıklanmaktadır. Güvenlik ve uyumluluk portalındaki denetim günlüğünde arama yaparak bu olayları arayabilirsiniz.

Bu tablolar ilgili etkinlikleri veya belirli bir hizmetten gelen etkinlikleri gruplandırır. Tablolar, **Etkinlikler** açılan listesinde görüntülenen kolay adı ve bir denetim kaydının ayrıntılı bilgilerinde ve arama sonuçlarını dışarı aktardığınızda CSV dosyasında görünen ilgili işlemin adını içerir. Ayrıntılı bilgilerin açıklamaları için [denetim günlüğündeki Ayrıntılı özellikler bölümüne](detailed-properties-in-the-office-365-audit-log.md) bakın.

Belirli bir tabloya gitmek için aşağıdaki bağlantılardan birine tıklayın.

:::row:::
    :::column:::
        [Dosya ve sayfa etkinlikleri](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Klasör etkinlikleri](#folder-activities)
    :::column-end:::
    :::column:::
        [Liste etkinliklerini SharePoint](#sharepoint-list-activities)
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
        [Posta kutusu etkinliklerini Exchange](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Kullanıcı yönetimi etkinlikleri](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Grup yönetimi etkinliklerini Azure AD](#azure-ad-group-administration-activities)
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
        [eBulma (Premium) etkinlikleri](#ediscovery-premium-activities)
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
        [Microsoft Teams Healthcare etkinlikleri](#microsoft-teams-healthcare-activities)
    :::column-end:::
    :::column:::
        [Microsoft Teams Vardiyaları etkinlikleri](#microsoft-teams-shifts-activities)
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
        [Karantina etkinlikleri](#quarantine-activities)
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
        [E-posta etkinliklerini bilgilendirme](#briefing-email-activities)
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
        [Gözden geçirme etkinliklerini değerlendirme](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [İletişim uyumluluk etkinlikleri](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Rapor etkinlikleri](#report-activities)
    :::column-end:::
    :::column:::
        [yönetici etkinliklerini Exchange](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Şifrelenmiş ileti portalı etkinlikleri](#encrypted-message-portal-activities)
    :::column-end:::
    :::column:::
        
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Dosya ve sayfa etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş'daki dosya ve sayfa etkinlikleri açıklanmaktadır.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Erişilen dosya|FileAccessed|Kullanıcı veya sistem hesabı bir dosyaya erişir. Kullanıcı bir dosyaya eriştiğinde, FileAccessed olayı aynı kullanıcı için sonraki beş dakika boyunca aynı dosya için yeniden günlüğe kaydedilmez.|
|(yok)|FileAccessedExtended|Bu, "Erişilen dosya" (FileAccessed) etkinliğiyle ilgilidir. Bir FileAccessedExtended olayı, aynı kişi uzun bir süre boyunca (3 saate kadar) bir dosyaya sürekli eriştiğinde günlüğe kaydedilir. <br/><br/> FileAccessedExtended olaylarının günlüğe kaydedilmesinin amacı, bir dosyaya sürekli erişildiğinde günlüğe kaydedilen FileAccessed olaylarının sayısını azaltmaktır. Bu, temelde aynı kullanıcı etkinliği için birden çok FileAccessed kaydının gürültüsünü azaltmaya yardımcı olur ve ilk (ve daha önemli) FileAccessed olayına odaklanmanızı sağlar.|
|Dosya için bekletme etiketi değiştirildi|ComplianceSettingChanged|Belgeye bekletme etiketi uygulandı veya belgeden kaldırıldı. Bekletme etiketi el ile veya otomatik olarak iletiye uygulandığında bu olay tetikleniyor.|
|Kayıt durumu kilitli olarak değiştirildi|LockRecord|Belgeyi kayıt olarak sınıflandırır bekletme etiketinin kayıt durumu kilitlendi. Başka bir deyişle, belge değiştirilemez veya silinemez. Yalnızca site için en az katkıda bulunan izni atanmış kullanıcılar belgenin kayıt durumunu değiştirebilir.|
|Kayıt durumu kilidi açık olarak değiştirildi|UnlockRecord|Belgeyi kayıt kilidi açılmış olarak sınıflandıran bekletme etiketinin kayıt durumu. Bu, belgenin değiştirilebileceği veya silinebileceği anlamına gelir. Yalnızca site için en az katkıda bulunan izni atanmış kullanıcılar belgenin kayıt durumunu değiştirebilir.|
|İade edilmiş dosya|FileCheckedIn|Kullanıcı, belge kitaplığından kullanıma aldıkları bir belgeyi iade etti.|
|Kullanıma alınan dosya|FileCheckedOut|Kullanıcı, belge kitaplığında bulunan bir belgeyi kullanıma alır. Kullanıcılar, kendileriyle paylaşılan belgeleri kullanıma alabilir ve belgelerde değişiklik yapabilir.|
|Kopyalanan dosya|FileCopied|Kullanıcı bir siteden belge kopyalar. Kopyalanan dosya sitedeki başka bir klasöre kaydedilebilir.|
|Dosya silindi|FileDeleted|Kullanıcı siteden bir belgeyi siler.|
|Geri dönüşüm kutusundan dosya silindi|FileDeletedFirstStageRecycleBin|Kullanıcı sitenin geri dönüşüm kutusundan bir dosyayı siler.|
|İkinci aşama geri dönüşüm kutusundan dosya silindi|FileDeletedSecondStageRecycleBin|Kullanıcı sitenin ikinci aşama geri dönüşüm kutusundan bir dosyayı siler.|
|Kayıt olarak işaretlenmiş dosya silindi|RecordDelete|Kayıt olarak işaretlenmiş bir belge veya e-posta silindi. Öğelere kayıt olarak işaretleyen bir bekletme etiketi içeriğe uygulandığında, öğe kayıt olarak kabul edilir.|
|Belge duyarlılığı uyuşmazlığı algılandı|DocumentSensitivityMismatch Algılandı|Kullanıcı bir belgeyi duyarlılık etiketiyle korunan bir siteye yükler ve belge, siteye uygulanan duyarlılık etiketinden daha yüksek öncelikli duyarlılık etiketine sahiptir. Örneğin, Gizli etiketli bir belge Genel etiketli bir siteye yüklenir. <br/><br/> Belge, siteye uygulanan duyarlılık etiketinden daha düşük öncelikli duyarlılık etiketine sahipse bu olay tetiklenmiyor. Örneğin, Genel etiketli bir belge Gizli etiketli bir siteye yüklenir. Duyarlılık etiketi önceliği hakkında daha fazla bilgi için bkz. [Etiket önceliği (sipariş önemlidir)](sensitivity-labels.md#label-priority-order-matters).|
|Dosyada kötü amaçlı yazılım algılandı|FileMalware Algılandı|SharePoint virüsten koruma altyapısı bir dosyadaki kötü amaçlı yazılımları algılar.|
|Atılan dosya kullanıma alma|FileCheckOutDiscarded|Kullanıcı kullanıma alınmış bir dosyayı atar (veya geri alır). Bu, kullanıma alındığı sırada dosyada yaptıkları değişikliklerin atıldığı ve belge kitaplığındaki belge sürümüne kaydedilmediği anlamına gelir.|
|İndirilen dosya|FileDownloaded|Kullanıcı siteden bir belge indirir.|
|Değiştirilen dosya|FileModified|Kullanıcı veya sistem hesabı, sitedeki bir belgenin içeriğini veya özelliklerini değiştirir. Sistem, aynı kullanıcı aynı belgenin içeriğini veya özelliklerini değiştirdiğinde başka bir FileModified olayını günlüğe kaydedebilmesi için beş dakika bekler.|
|(yok)|FileModifiedExtended|Bu, "Değiştirilmiş dosya" (FileModified) etkinliğiyle ilgilidir. Aynı kişi bir dosyayı uzun bir süre (3 saate kadar) sürekli değiştirdiğinde FileModifiedExtended olayı günlüğe kaydedilir. <br/><br/> FileModifiedExtended olaylarının günlüğe kaydedilmesinin amacı, bir dosya sürekli değiştirildiğinde günlüğe kaydedilen FileModified olaylarının sayısını azaltmaktır. Bu, temelde aynı kullanıcı etkinliği için birden çok FileModified kaydının gürültüsünü azaltmaya yardımcı olur ve ilk (ve daha önemli) FileModified olayına odaklanmanızı sağlar.|
|Dosya taşındı|FileMoved|Kullanıcı bir belgeyi sitedeki geçerli konumundan yeni bir konuma taşır.|
|(yok)|FilePreviewed|Kullanıcı, bir SharePoint veya OneDrive İş sitesinde dosyaların önizlemesini gösterir. Bu olaylar genellikle görüntü galerisini görüntüleme gibi tek bir etkinliğe bağlı olarak yüksek hacimlerde gerçekleşir.|
|Gerçekleştirilen arama sorgusu|SearchQueryPerformed|Kullanıcı veya sistem hesabı SharePoint veya OneDrive İş arama gerçekleştirir. Hizmet hesabının arama sorgusu gerçekleştirdiği bazı yaygın senaryolar arasında sitelere ve OneDrive hesaplarına eBulma saklama ve bekletme ilkesi uygulama ve site içeriğine bekletme veya duyarlılık etiketlerini otomatik uygulama yer alır.|
|Dosyayı geri dönüştüren | FileRecycled | Kullanıcı bir dosyayı SharePoint Geri Dönüşüm Kutusu'na taşır. |
|Klasörü geri dönüştüren | FolderRecycled | Kullanıcı bir klasörü SharePoint Geri Dönüşüm Kutusu'na taşır. |
|Dosyanın tüm ikincil sürümleri geri dönüştürüldi|FileVersionsAllMinorsRecycled|Kullanıcı, dosyanın sürüm geçmişinden tüm ikincil sürümleri siler. Silinen sürümler sitenin geri dönüşüm kutusuna taşınır.|
|Dosyanın tüm sürümleri geri dönüştürüldi|FileVersionsAllRecycled|Kullanıcı dosyanın sürüm geçmişinden tüm sürümleri siler. Silinen sürümler sitenin geri dönüşüm kutusuna taşınır.|
|Dosyanın geri dönüştürülmüş sürümü|FileVersionRecycled|Kullanıcı bir dosyanın sürüm geçmişinden bir sürümü siler. Silinen sürüm sitenin geri dönüşüm kutusuna taşınır.|
|Dosya yeniden adlandırıldı|FileRenamed|Kullanıcı sitedeki bir belgeyi yeniden adlandırır.|
|Geri yüklenen dosya|FileRestored|Kullanıcı sitenin geri dönüşüm kutusundan bir belgeyi geri yükler.|
|Karşıya yüklenen dosya|FileUploaded|Kullanıcı sitedeki bir klasöre belge yükler.|
|Görüntülenen sayfa|PageViewed|Kullanıcı sitedeki bir sayfayı görüntüler. Bu, belge kitaplığında bulunan dosyaları görüntülemek için Web tarayıcısı kullanmayı içermez. Kullanıcı bir sayfayı görüntüledikten sonra, PageViewed olayı sonraki beş dakika boyunca aynı kullanıcı için aynı sayfa için yeniden günlüğe kaydedilmez.|
|(yok)|PageViewedExtended|Bu, "Görüntülenen sayfa" (PageViewed) etkinliğiyle ilgilidir. Bir PageViewedExtended olayı, aynı kişi uzun bir süre boyunca (3 saate kadar) sürekli olarak bir web sayfasını görüntülediğinde günlüğe kaydedilir. <br/><br/> PageViewedExtended olaylarının günlüğe kaydedilmesinin amacı, bir sayfa sürekli görüntülendiğinde günlüğe kaydedilen PageViewed olaylarının sayısını azaltmaktır. Bu, temelde aynı kullanıcı etkinliği için birden çok PageViewed kaydının gürültüsünü azaltmaya yardımcı olur ve ilk (ve daha önemli) PageViewed olayına odaklanmanızı sağlar.|
|İstemci tarafından sinyallenenleri görüntüleme|ClientViewSignaled|Kullanıcının istemcisi (web sitesi veya mobil uygulama gibi) belirtilen sayfanın kullanıcı tarafından görüntülendiğinin sinyalini verdi. Bu etkinlik genellikle bir sayfa için PagePrefetched olayından sonra günlüğe kaydedilir. <br/><br/>**NOT**: ClientViewSignaled olayları sunucu yerine istemci tarafından sinyallendirildiğinden, olay sunucu tarafından günlüğe kaydedilmemiş olabilir ve bu nedenle denetim günlüğünde görünmeyebilir. Denetim kaydındaki bilgilerin güvenilir olmayabileceği de mümkündür. Ancak, kullanıcının kimliği sinyali oluşturmak için kullanılan belirteç tarafından doğrulandığından, ilgili denetim kaydında listelenen kullanıcının kimliği doğrudur. Sistem, aynı kullanıcının istemcisi sayfanın kullanıcı tarafından yeniden görüntülendiğini bildirirken aynı olayı günlüğe kaydedebilmesi için beş dakika bekler.|
|(yok)|PagePrefetched|Kullanıcının istemcisi (web sitesi veya mobil uygulama gibi), kullanıcı göz atarsa performansı iyileştirmeye yardımcı olmak için belirtilen sayfayı istedi. Bu olay, sayfa içeriğinin kullanıcının istemcisine sunulduğuna işaret etmek için günlüğe kaydedilir. Bu olay, kullanıcının sayfaya gidip gitmediğinin kesin bir göstergesi değildir. <br/><br/> Sayfa içeriği istemci tarafından işlendiğinde (kullanıcının isteğine göre) bir ClientViewSignaled olayı oluşturulmalıdır. Tüm istemciler önceden getirme işlemini belirtmeyi desteklemez ve bu nedenle bazı önceden getirilen etkinlikler bunun yerine PageViewed olayları olarak günlüğe kaydedilebilir.|

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>FileAccessed ve FilePreviewed olayları hakkında sık sorulan sorular

**Kullanıcı olmayan etkinlikler"OneDriveMpc-Transform_Thumbnail" gibi bir kullanıcı aracısı içeren FilePreviewed denetim kayıtlarını tetikleyebilir mi?**

Kullanıcı dışı eylemlerin bunlara benzer olaylar oluşturduğu senaryoların farkında değildir. Kullanıcı profili kartını açma gibi kullanıcı eylemleri (Web üzerinde Outlook bir iletideki adına veya e-posta adresine tıklayarak) benzer olaylar oluşturabilir.

**OneDriveMpc-Transform_Thumbnail çağrıları her zaman kullanıcı tarafından kasıtlı olarak tetikleniyor mu?**

Hayır. Ancak tarayıcı ön getirme işleminin sonucu olarak benzer olaylar günlüğe kaydedilebilir.

**Microsoft tarafından kayıtlı bir IP adresinden filePreviewed olayının geldiğini görürsek, bu önizlemenin kullanıcının cihazının ekranında görüntülendiği anlamına mı gelir?**

Hayır. Olay, tarayıcı ön getirme işleminin sonucu olarak günlüğe kaydedilmiş olabilir.

**Belge önizlemesi kullanan bir kullanıcının FileAccessed olayları oluşturduğu senaryolar var mı?**

Hem FilePreviewed hem de FileAccessed olayları, kullanıcının çağrısının dosyanın okunmasını (veya dosyanın küçük resim işlemesinin okunmasını) gösterdiğini gösterir. Bu olaylar önizleme ve erişim amacına uygun olarak tasarlanırken, olay ayrımı kullanıcının amacının garantisi değildir.

#### <a name="the-appsharepoint-user-in-audit-records"></a>Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı

Bazı dosya etkinliklerinin (ve diğer SharePoint ilgili etkinliklerin) denetim kayıtlarında, etkinliği gerçekleştiren kullanıcının (User ve UserId alanlarında tanımlanan) app@sharepoint olduğunu fark edebilirsiniz. Bu, etkinliği gerçekleştiren "kullanıcının" bir uygulama olduğunu gösterir. Bu durumda uygulamaya kullanıcı, yönetici veya hizmet adına kuruluş genelinde eylemler (SharePoint site veya OneDrive hesabı arama gibi) gerçekleştirmek için SharePoint izinleri verilmiştir. Bir uygulamaya izin verme işlemi, *Yalnızca Uygulama erişimi SharePoint* olarak adlandırılır. Bu, bir eylem gerçekleştirmek için SharePoint sunulan kimlik doğrulamasının kullanıcı yerine bir uygulama tarafından yapıldığını gösterir. bu nedenle app@sharepoint kullanıcı belirli denetim kayıtlarında tanımlanır. Daha fazla bilgi için bkz. [Yalnızca Uygulama SharePoint kullanarak erişim izni verme](/sharepoint/dev/solution-guidance/security-apponly-azureacs).

Örneğin, app@sharepoint genellikle "Gerçekleştirilen arama sorgusu" ve "Erişilen dosya" olayları için kullanıcı olarak tanımlanır. Bunun nedeni, kuruluşunuzda SharePoint App-Only erişimi olan bir uygulamanın sitelere ve OneDrive hesaplarına bekletme ilkeleri uygularken arama sorguları gerçekleştirmesi ve dosyalara erişmesidir.

Bir denetim kaydında etkinlik gerçekleştiren kullanıcı olarak app@sharepoint tanımlanabileceği diğer birkaç senaryo aşağıdadır:

- Microsoft 365 Grupları. Kullanıcı veya yönetici yeni bir grup oluşturduğunda, site koleksiyonu oluşturmak, listeleri güncelleştirmek ve bir SharePoint grubuna üye eklemek için denetim kayıtları oluşturulur. Bu görevler, grubu oluşturan kullanıcı adına bir uygulama gerçekleştirilir.

- Microsoft Teams. Microsoft 365 Grupları benzer şekilde, bir ekip oluşturulduğunda site koleksiyonu oluşturmak, listeleri güncelleştirmek ve bir SharePoint grubuna üye eklemek için denetim kayıtları oluşturulur.

- Uyumluluk özellikleri. Bir yönetici bekletme ilkeleri, eBulma tutmaları ve duyarlılık etiketlerini otomatik uygulama gibi uyumluluk özelliklerini uyguladığında.

Bu ve diğer senaryolarda, belirtilen kullanıcı olarak app@sharepoint birden çok denetim kaydının kısa bir zaman dilimi içinde (genellikle birkaç saniye içinde) oluşturulduğunu da fark edeceksiniz. Bu, büyük olasılıkla aynı kullanıcı tarafından başlatılan görev tarafından tetiklendiklerini de gösterir. Ayrıca, denetim kaydındaki ApplicationDisplayName ve EventData alanları, olayı tetikleyen senaryoyu veya uygulamayı belirlemenize yardımcı olabilir.

### <a name="folder-activities"></a>Klasör etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş klasör etkinlikleri açıklanmaktadır. Daha önce açıklandığı gibi, bazı SharePoint etkinliklerinin denetim kayıtları, app@sharepoint kullanıcının eylemi başlatan kullanıcı veya yönetici adına etkinlik gerçekleştirdiğini gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Kopyalanan klasör|KlasörKopied|Kullanıcı siteden bir klasörü SharePoint veya OneDrive İş başka bir konuma kopyalar.|
|Klasör oluşturuldu|KlasörOluştur|Kullanıcı sitede bir klasör oluşturur.|
|Klasör silindi|KlasörDeleted|Kullanıcı siteden bir klasörü siler.|
|Klasör geri dönüşüm kutusundan silindi|FolderDeletedFirstStageRecycleBin|Kullanıcı sitedeki geri dönüşüm kutusundan bir klasörü siler.|
|İkinci aşama geri dönüşüm kutusundan klasör silindi|FolderDeletedSecondStageRecycleBin|Kullanıcı sitedeki ikinci aşama geri dönüşüm kutusundan bir klasörü siler.|
|Değiştirilen klasör|FolderModified|Kullanıcı sitedeki bir klasörü değiştirir. Bu, etiketleri ve özellikleri değiştirme gibi klasör meta verilerini değiştirmeyi içerir.|
|Taşınan klasör|Klasör Taşınan|Kullanıcı bir klasörü sitedeki farklı bir konuma taşır.|
|Klasör yeniden adlandırıldı|FolderRenamed|Kullanıcı sitedeki bir klasörü yeniden adlandırır.|
|Geri yüklenen klasör|FolderRestored|Kullanıcı silinen bir klasörü sitedeki geri dönüşüm kutusundan geri yükler.|

### <a name="sharepoint-list-activities"></a>Liste etkinliklerini SharePoint

Aşağıdaki tabloda, kullanıcıların SharePoint Online'daki liste ve liste öğeleriyle ne zaman etkileşime geçtiğiyle ilgili etkinlikler açıklanmaktadır. Daha önce açıklandığı gibi, bazı SharePoint etkinliklerinin denetim kayıtları, app@sharepoint kullanıcının eylemi başlatan kullanıcı veya yönetici adına etkinlik gerçekleştirdiğini gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Oluşturulan liste|ListCreated|Kullanıcı bir SharePoint listesi oluşturdu.|
|Liste sütunu oluşturuldu|ListColumnCreated|Kullanıcı bir SharePoint listesi sütunu oluşturdu. Liste sütunu, bir veya daha fazla SharePoint listesine eklenmiş bir sütundur.|
|Oluşturulan liste içerik türü|ListContentTypeCreated|Kullanıcı bir liste içerik türü oluşturdu. Liste içerik türü, bir veya daha fazla SharePoint listesine eklenmiş bir içerik türüdür.|
|Liste öğesi oluşturuldu|ListItemCreated|Kullanıcı var olan bir SharePoint listesinde öğe oluşturdu.|
|Site sütunu oluşturuldu|SiteColumnCreated|Kullanıcı bir SharePoint site sütunu oluşturdu. Site sütunu, listeye eklenmemiş bir sütundur. Site sütunu aynı zamanda belirli bir web'deki herhangi bir liste tarafından kullanılabilecek bir meta veri yapısıdır.|
|Site içerik türü oluşturuldu|Site ContentType Oluşturuldu|Kullanıcı bir site içerik türü oluşturdu. Site içerik türü, üst siteye eklenmiş bir içerik türüdür.|
|Silinen liste|ListDeleted|Kullanıcı bir SharePoint listesini sildi.|
|Silinen liste sütunu|Liste Sütunu Silindi|Kullanıcı bir SharePoint listesi sütununu sildi.|
|Silinen liste içerik türü|ListContentTypeDeleted|Kullanıcı liste içerik türünü sildi.|
|Liste öğesi silindi|Liste Öğesi Silindi|Kullanıcı bir SharePoint liste öğesini sildi.|
|Site sütunu silindi|SiteColumnDeleted|Kullanıcı bir SharePoint site sütununu sildi.|
|Site içerik türü silindi|SiteContentTypeDeleted|Kullanıcı site içerik türünü sildi.|
|Geri dönüştürülen liste öğesi|ListItemRecycled|Kullanıcı bir SharePoint liste öğesini Geri Dönüşüm Kutusu'na taşıdı.|
|Geri yüklenen liste|ListRestored|Kullanıcı Geri Dönüşüm Kutusu'ndan bir SharePoint listesini geri yükledi.|
|Geri yüklenen liste öğesi|ListItemRestored|Kullanıcı Geri Dönüşüm Kutusu'ndan bir SharePoint listesi öğesini geri yükledi.|
|Güncelleştirilmiş liste|ListUpdated|Kullanıcı bir veya daha fazla özelliği değiştirerek bir SharePoint listesini güncelleştirdi.|
|Güncelleştirilmiş liste sütunu|ListColumnUpdated|Kullanıcı bir veya daha fazla özelliği değiştirerek bir SharePoint listesi sütununu güncelleştirdi.|
|Güncelleştirilmiş liste içerik türü|ListContentTypeUpdated|Kullanıcı bir veya daha fazla özelliği değiştirerek liste içerik türünü güncelleştirdi.|
|Güncelleştirilmiş liste öğesi|ListItemUpdated|Bir kullanıcı, bir veya daha fazla özelliği değiştirerek bir SharePoint liste öğesini güncelleştirdi.|
|Site sütunu güncelleştirildi|SiteColumnUpdated|Kullanıcı bir veya daha fazla özelliği değiştirerek bir SharePoint site sütununu güncelleştirdi.|
|Güncelleştirilmiş site içerik türü|SiteContentTypeUpdated|Kullanıcı, bir veya daha fazla özelliği değiştirerek site içerik türünü güncelleştirdi.|

### <a name="sharing-and-access-request-activities"></a>Paylaşım ve erişim isteği etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş'da kullanıcı paylaşım ve erişim isteği etkinlikleri açıklanmaktadır. Olayları paylaşmak için **, Sonuçlar** altındaki **Ayrıntı** sütunu öğenin paylaşıldığı kullanıcının veya grubun adını ve söz konusu kullanıcının veya grubun kuruluşunuzdaki bir üye veya konuk olup olmadığını tanımlar. Daha fazla bilgi için bkz. [Denetim günlüğünde paylaşım denetimini kullanma](use-sharing-auditing.md).

> [!NOTE]
> Kullanıcılar, kullanıcı nesnesinin UserType özelliğine göre  *üye*  veya  *konuk*  olabilir. Üye genellikle bir çalışandır ve konuk genellikle kuruluşunuzun dışında bir ortak çalışandır. Bir kullanıcı paylaşım davetini kabul ettiğinde (ve henüz kuruluşunuzun bir parçası değilse), kuruluşunuzun dizininde onun için bir konuk hesabı oluşturulur. Konuk kullanıcının dizininizde bir hesabı olduğunda kaynaklar doğrudan onlarla paylaşılabilir (davet gerektirmeden).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Site koleksiyonuna izin düzeyi eklendi|PermissionLevelAdded|Site koleksiyonuna izin düzeyi eklendi.|
|Kabul edilen erişim isteği|AccessRequestAccepted|Site, klasör veya belgeye erişim isteği kabul edildi ve istekte bulunan kullanıcıya erişim verildi.|
|Kabul edilen paylaşım daveti|SharingInvitationAccepted|Kullanıcı (üye veya konuk) paylaşım davetini kabul etti ve bir kaynağa erişim izni verildi. Bu olay, davet edilen kullanıcı ve daveti kabul etmek için kullanılan e-posta adresi hakkında bilgiler içerir (farklı olabilir). Bu etkinliğe genellikle kullanıcıya kaynağa nasıl erişim verildiğini açıklayan ikinci bir olay eşlik eder. Örneğin, kullanıcıyı kaynağa erişimi olan bir gruba ekler.|
|Engellenen paylaşım daveti|SharingInvitationBlocked|Kuruluşunuzdaki bir kullanıcı tarafından gönderilen paylaşım daveti, hedef kullanıcının etki alanına göre dış paylaşıma izin veren veya reddeden bir dış paylaşım ilkesi nedeniyle engellenir. Bu durumda paylaşım daveti engellendi çünkü: <br/> Hedef kullanıcının etki alanı izin verilen etki alanları listesine dahil değildir. <br/> Veya <br/> Hedef kullanıcının etki alanı engellenen etki alanları listesine eklenir. <br/> Etki alanları temelinde dış paylaşıma izin verme veya bunları engelleme hakkında daha fazla bilgi için bkz. [SharePoint Online'da kısıtlı etki alanları paylaşımı ve OneDrive İş](/sharepoint/restricted-domains-sharing).|
|Erişim isteği oluşturuldu|AccessRequestCreated|Kullanıcı erişim izni olmayan bir siteye, klasöre veya belgeye erişim ister.|
|Şirket tarafından paylaşılabilir bağlantı oluşturuldu|CompanyLinkCreated|Kullanıcı bir kaynağa şirket genelinde bir bağlantı oluşturmuştur. şirket genelinde bağlantılar yalnızca kuruluşunuzdaki üyeler tarafından kullanılabilir. Konuklar tarafından kullanılamazlar.|
|Anonim bağlantı oluşturuldu|AnonymousLinkCreated|Kullanıcı bir kaynağa anonim bağlantı oluşturdu. Bu bağlantıya sahip olan herkes kimliğinin doğrulanması gerekmeden kaynağa erişebilir.|
|Güvenli bağlantı oluşturuldu|SecureLinkCreated|Bu öğeye güvenli bir paylaşım bağlantısı oluşturuldu.|
|Paylaşım daveti oluşturuldu|SharingInvitationCreated|Kullanıcı SharePoint Online'da bir kaynak paylaştı veya kuruluşunuzun dizininde olmayan bir kullanıcıyla OneDrive İş.|
|Güvenli bağlantı silindi|SecureLinkDeleted|Güvenli paylaşım bağlantısı silindi.|
|Erişim isteği reddedildi|AccessRequestDenied|Site, klasör veya belgeye erişim isteği reddedildi.|
|Şirket tarafından paylaşılabilir bağlantı kaldırıldı|ŞirketLinkRemoved|Kullanıcı bir kaynağa şirket genelindeki bağlantıyı kaldırdı. Bağlantı artık kaynağa erişmek için kullanılamaz.|
|Anonim bağlantı kaldırıldı|AnonymousLinkRemoved|Kullanıcı bir kaynağa anonim bağlantı kaldırdı. Bağlantı artık kaynağa erişmek için kullanılamaz.|
|Paylaşılan dosya, klasör veya site|SharingSet|Kullanıcı (üye veya konuk), SharePoint veya OneDrive İş içindeki bir dosyayı, klasörü veya siteyi kuruluşunuzun dizinindeki bir kullanıcıyla paylaştı. Bu etkinliğin **Ayrıntı** sütunundaki değer, kaynağın paylaşıldığı kullanıcının adını ve bu kullanıcının üye mi yoksa konuk mu olduğunu tanımlar. <br/><br/> Bu etkinliğe genellikle kullanıcıya kaynağa nasıl erişim verildiğini açıklayan ikinci bir olay eşlik eder. Örneğin, kullanıcıyı kaynağa erişimi olan bir gruba ekleme.|
|Güncelleştirilmiş erişim isteği|AccessRequestUpdated|Bir öğeye erişim isteği güncelleştirildi.|
|Anonim bağlantı güncelleştirildi|AnonymousLinkUpdated|Kullanıcı bir kaynağa anonim bağlantı güncelleştirdi. Güncelleştirilmiş alan, arama sonuçlarını dışarı aktardığınızda EventData özelliğine eklenir.|
|Paylaşım daveti güncelleştirildi|SharingInvitationUpdated|Dış paylaşım daveti güncelleştirildi.|
|Anonim bağlantı kullanıldı|AnonymousLinkUsed|Anonim bir kullanıcı, bir kaynağa anonim bağlantı kullanarak erişmiş. Kullanıcının kimliği bilinmiyor olabilir, ancak kullanıcının IP adresi gibi diğer ayrıntıları alabilirsiniz.|
|Paylaşılmayan dosya, klasör veya site|SharingRevoked|Kullanıcı (üye veya konuk), daha önce başka bir kullanıcıyla paylaşılan bir dosya, klasör veya sitenin paylaşımını kaldırmıştı.|
|Şirket tarafından paylaşılabilir bağlantı kullanıldı|CompanyLinkUsed|Kullanıcı şirket genelinde bir bağlantı kullanarak bir kaynağa erişti.|
|Kullanılan güvenli bağlantı|SecureLinkUsed|Kullanıcı güvenli bir bağlantı kullandı.|
|Kullanıcı güvenli bağlantıya eklendi|AddedToSecureLink|Güvenli paylaşım bağlantısı kullanabilen varlıklar listesine bir kullanıcı eklendi.|
|Kullanıcı güvenli bağlantıdan kaldırıldı|RemovedFromSecureLink|Bir kullanıcı, güvenli paylaşım bağlantısı kullanabilen varlıklar listesinden kaldırıldı.|
|Paylaşım daveti geri çekildi|SharingInvitationRevoked|Kullanıcı bir kaynağa paylaşım daveti çekti.|

### <a name="synchronization-activities"></a>Eşitleme etkinlikleri

Aşağıdaki tabloda, SharePoint Online ve OneDrive İş dosya eşitleme etkinlikleri listelenir.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Bilgisayarın dosyaları eşitlemesine izin verildi|ManagedSyncClientAllowed|Kullanıcı bir siteyle başarıyla eşitleme ilişkisi kurar. Kullanıcının bilgisayarı, kuruluşunuzdaki belge kitaplıklarına erişebilen etki alanları listesine ( *güvenli alıcılar listesi* olarak adlandırılır) eklenmiş bir etki alanının üyesi olduğundan eşitleme ilişkisi başarılı olur. <br/><br/> Bu özellik hakkında daha fazla bilgi için bkz[. Güvenli alıcılar listesindeki etki alanları için OneDrive eşitleme etkinleştirmek için Windows PowerShell cmdlet'leri kullanma](/powershell/module/sharepoint-online/).|
|Bilgisayarın dosyaları eşitlemesi engellendi|UnmanagedSyncClientBlocked|Kullanıcı, kuruluşunuzun etki alanının üyesi olmayan veya kuruluşunuzdaki belge kitaplıklarına erişebilen etki alanları listesine (  *güvenilir alıcılar listesi*  olarak adlandırılır) eklenmemiş bir etki alanının üyesi olan bir bilgisayardan siteyle eşitleme ilişkisi kurmaya çalışır. Eşitleme ilişkisine izin verilmez ve kullanıcının bilgisayarının dosyaları bir belge kitaplığına eşitlemesi, indirmesi veya karşıya yüklemesi engellenir. <br/><br/> Bu özellik hakkında bilgi için bkz. [Güvenli alıcılar listesindeki etki alanları için OneDrive eşitleme etkinleştirmek için Windows PowerShell cmdlet'lerini kullanma](/powershell/module/sharepoint-online/).|
|Bilgisayara indirilen dosyalar|FileSyncDownloadedFull|Kullanıcı SharePoint belge kitaplığından veya OneDrive eşitleme uygulamasını (OneDrive.exe) kullanarak OneDrive İş bilgisayarına dosya indirir.|
|Bilgisayara indirilen dosya değişiklikleri|FileSyncDownloadedPartial|Bu olay, eski OneDrive İş eşitleme uygulaması (Groove.exe) ile birlikte kullanım dışı bırakıldı.|
|Belge kitaplığına dosya yüklendi|FileSyncUploadedFull|Kullanıcı, OneDrive eşitleme uygulamasını (OneDrive.exe) kullanarak yeni bir dosyayı veya değişiklikleri SharePoint belge kitaplığına veya OneDrive İş bir dosyaya yükler.|
|Belge kitaplığına yüklenen dosya değişiklikleri|FileSyncUploadedPartial|Bu olay, eski OneDrive İş eşitleme uygulaması (Groove.exe) ile birlikte kullanım dışı bırakıldı.|

### <a name="site-permissions-activities"></a>Site izinleri etkinlikleri

Aşağıdaki tabloda, SharePoint izin atama ve sitelere erişim vermek (ve iptal etmek) için grupları kullanma ile ilgili olaylar listeleniyor. Daha önce açıklandığı gibi, bazı SharePoint etkinliklerinin denetim kayıtları, app@sharepoint kullanıcının eylemi başlatan kullanıcı veya yönetici adına etkinlik gerçekleştirdiğini gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Site koleksiyonu yöneticisi eklendi|SiteCollectionAdminAdded|Site koleksiyonu yöneticisi veya sahibi, site için bir kişiyi site koleksiyonu yöneticisi olarak ekler. Site koleksiyonu yöneticileri, site koleksiyonu ve tüm alt siteler için tam denetim izinlerine sahiptir. Bu etkinlik, yönetici kullanıcının OneDrive hesabına (SharePoint yönetim merkezinde kullanıcı profilini düzenleyerek veya Microsoft 365 yönetim merkezi kullanarak) erişim verdiğinde de [günlüğe](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data) kaydedilir.|
|SharePoint grubuna kullanıcı veya grup eklendi|AddedToGroup|Kullanıcı bir SharePoint grubuna üye veya konuk ekledi. Bu kasıtlı bir eylem veya paylaşım olayı gibi başka bir etkinliğin sonucu olabilir.|
|İzin düzeyi devralmayı bozdu|PermissionLevelsInheritanceBroken|Bir öğe, artık üst öğesinden izin düzeylerini devralmaması için değiştirildi.|
|Paylaşım devralmayı bozdu|SharingInheritanceBroken|Öğe artık üst öğesinden paylaşım izinlerini devralmaması için değiştirildi.|
|Grup oluşturuldu|GroupAdded|Site yöneticisi veya sahibi site için bir grup oluşturur veya bir grubun oluşturulmasına neden olan bir görev gerçekleştirir. Örneğin, bir kullanıcı dosyayı paylaşmak için ilk kez bir bağlantı oluşturduğunda, kullanıcının OneDrive İş sitesine bir sistem grubu eklenir. Bu olay, kullanıcının paylaşılan bir dosyaya yönelik düzenleme izinlerine sahip bir bağlantı oluşturmasının bir sonucu da olabilir.|
|Grup silindi|GroupRemoved|Kullanıcı siteden bir grubu siler.|
|Değiştirilmiş erişim isteği ayarı|WebRequestAccessModified|Erişim isteği ayarları bir sitede değiştirildi.|
|'Üyeler Paylaşabilir' ayarı değiştirildi|WebMembersCanShareModified|**Üyeler Paylaşabilir** ayarı sitede değiştirildi.|
|Site koleksiyonunda değiştirilmiş izin düzeyi|PermissionLevelModified|Site koleksiyonunda izin düzeyi değiştirildi.|
|Değiştirilen site izinleri|SitePermissionsModified|Site yöneticisi veya sahibi (veya sistem hesabı), sitedeki bir gruba atanan izin düzeyini değiştirir. Tüm izinler bir gruptan kaldırılırsa bu etkinlik de günlüğe kaydedilir. <br/><br/> **NOT**: Bu işlem SharePoint Online'da kullanım dışı bırakılmıştır. İlgili olayları bulmak için **Site koleksiyonu yöneticisi eklendi, SharePoint** **grubuna kullanıcı veya grup eklendi**, Grup **oluşturmasına izin verilen kullanıcı**, **Oluşturulan grup** ve **Silinmiş grup** gibi izinle ilgili diğer etkinlikleri arayabilirsiniz.|
|Site koleksiyonundan izin düzeyi kaldırıldı|PermissionLevelRemoved|Site koleksiyonundan izin düzeyi kaldırıldı.|
|Site koleksiyonu yöneticisi kaldırıldı|SiteCollectionAdminRemoved|Site koleksiyonu yöneticisi veya sahibi, sitenin site koleksiyonu yöneticisi olarak bir kişiyi kaldırır. Bu etkinlik, yönetici bir kullanıcının OneDrive hesabının site koleksiyonu yöneticileri listesinden (SharePoint yönetim merkezinde kullanıcı profilini düzenleyerek) kendisini kaldırdığında da günlüğe kaydedilir.  Bu etkinliği denetim günlüğü arama sonuçlarında döndürmek için tüm etkinlikleri aramanız gerekir.|
|SharePoint grubundan kullanıcı veya grup kaldırıldı|RemovedFromGroup|Kullanıcı bir üyeyi veya konuğu SharePoint grubundan kaldırdı. Bu kasıtlı bir eylem veya paylaşılmayan olay gibi başka bir etkinliğin sonucu olabilir.|
|İstenen site yöneticisi izinleri|SiteAdminChangeRequest|Kullanıcı, site koleksiyonu için site koleksiyonu yöneticisi olarak eklenmesini istemektedir. Site koleksiyonu yöneticileri, site koleksiyonu ve tüm alt siteler için tam denetim izinlerine sahiptir.|
|Paylaşım devralma geri yüklendi|SharingInheritanceReset|Öğenin paylaşım izinlerini üst öğesinden devralması için bir değişiklik yapıldı.|
|Güncelleştirilmiş grup|GroupUpdated|Site yöneticisi veya sahibi, bir site için grubun ayarlarını değiştirir. Bu, grubun adını değiştirmeyi, grup üyeliğini kimlerin görüntüleyebileceğini veya düzenleyebileceğini ve üyelik isteklerinin nasıl işlenme şeklini içerebilir.|

### <a name="site-administration-activities"></a>Site yönetimi etkinlikleri

Aşağıdaki tabloda, SharePoint Online'da site yönetimi görevlerinden kaynaklanan olaylar listelendir. Daha önce açıklandığı gibi, bazı SharePoint etkinliklerinin denetim kayıtları, app@sharepoint kullanıcının eylemi başlatan kullanıcı veya yönetici adına etkinlik gerçekleştirdiğini gösterir. Daha fazla bilgi için bkz [. Denetim kayıtlarındaki uygulama\@sharepoint kullanıcısı](#the-appsharepoint-user-in-audit-records).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|İzin verilen veri konumu eklendi|AllowedDataLocationAdded|bir SharePoint veya genel yönetici, çok coğrafi bir ortamda izin verilen bir veri konumu ekledi.|
|Muaf kullanıcı aracısı eklendi|ExemptUserAgentSet|SharePoint veya genel yönetici, SharePoint yönetim merkezindeki muaf kullanıcı aracıları listesine bir kullanıcı aracısı ekledi.|
|Coğrafi konum yöneticisi eklendi|GeoAdminAdded|SharePoint veya genel yönetici, bir kullanıcıyı konumun coğrafi yöneticisi olarak ekledi.|
|Kullanıcının grup oluşturmasına izin verildi|AllowGroupCreationSet|Site yöneticisi veya sahibi bir siteye izin düzeyi ekler ve bu izin atanmış bir kullanıcının bu site için grup oluşturmasına izin verir.|
|site coğrafi taşıma iptal edildi|SiteGeoMoveCancelled|SharePoint veya genel yönetici bir SharePoint veya OneDrive site coğrafi taşıma işlemini başarıyla iptal eder. Multi-Geo özelliği, bir kuruluşun coğrafi bölge olarak adlandırılan birden çok Microsoft veri merkezi coğrafyasına yayılmasına olanak tanır. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Paylaşım ilkesi değiştirildi|SharingPolicyChanged|SharePoint veya genel yönetici, Microsoft 365 yönetim merkezi, SharePoint yönetim merkezini veya Çevrimiçi Yönetim Kabuğu'SharePoint kullanarak SharePoint paylaşım ilkesini değiştirdi. Kuruluşunuzdaki paylaşım ilkesindeki ayarlarda yapılan tüm değişiklikler günlüğe kaydedilir. Değiştirilen ilke, olay kaydının ayrıntılı özelliklerindeki **ModifiedProperties** alanında tanımlanır.|
|Cihaz erişim ilkesi değiştirildi|DeviceAccessPolicyChanged|SharePoint veya genel yönetici, kuruluşunuz için yönetilmeyen cihazlar ilkesini değiştirdi. Bu ilke, kuruluşunuza katılmış olmayan cihazlardan SharePoint, OneDrive ve Microsoft 365 erişimini denetler. Bu ilkenin yapılandırılması için bir Enterprise Mobility + Security aboneliği gerekir. Daha fazla bilgi için bkz. [Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices).|
|Muaf kullanıcı aracıları değiştirildi|CustomizeExemptUsers|SharePoint veya genel yönetici, SharePoint yönetim merkezinde muaf kullanıcı aracılarının listesini özelleştirdi. Dizine eklenecek web sayfasının tamamını almaktan muaf tutulacak kullanıcı aracılarını belirtebilirsiniz. Bu, muaf olarak belirttiğiniz bir kullanıcı aracısı bir InfoPath formuyla karşılaştığında formun web sayfasının tamamı yerine XML dosyası olarak döndürüleceği anlamına gelir. Bu, InfoPath formlarının dizinini oluşturmayı hızlandırır.|
|Ağ erişim ilkesi değiştirildi|NetworkAccessPolicyChanged|SharePoint veya genel yönetici, SharePoint yönetim merkezinde veya SharePoint Online PowerShell kullanarak konum tabanlı erişim ilkesini (güvenilen ağ sınırı olarak da adlandırılır) değiştirdi. Bu ilke türü, belirttiğiniz yetkili IP adresi aralıklarına göre kuruluşunuzdaki SharePoint ve OneDrive kaynaklara kimlerin erişebileceğini denetler. Daha fazla bilgi için bkz. [SharePoint Online'a erişimi denetleme ve ağ konumuna göre verileri OneDrive](/sharepoint/control-access-based-on-network-location).|
|Tamamlanan site coğrafi taşıma|SiteGeoMoveCompleted|Kuruluşunuzdaki bir genel yönetici tarafından zamanlanan site coğrafi taşıma işlemi başarıyla tamamlandı. Multi-Geo özelliği, bir kuruluşun coğrafi bölge olarak adlandırılan birden çok Microsoft veri merkezi coğrafyasına yayılmasına olanak tanır. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Gönderilen bağlantı oluşturuldu|SendToConnectionAdded|SharePoint veya genel yönetici, SharePoint yönetim merkezindeki Kayıtlar yönetim sayfasında yeni bir Gönder bağlantısı oluşturur. Gönder bağlantısı, belge deposunun veya kayıt merkezinin ayarlarını belirtir. Gönder bağlantısı oluşturduğunuzda, İçerik Düzenleyicisi belgeleri belirtilen konuma gönderebilir.|
|Site koleksiyonu oluşturuldu|SiteCollectionCreated|SharePoint veya genel yönetici, SharePoint Online kuruluşunuzda bir site koleksiyonu oluşturur veya bir kullanıcı OneDrive İş sitesini sağlar.|
|Yalnız bırakılmış hub sitesi silindi|HubSiteOrphanHubDeleted|bir SharePoint veya genel yönetici, kendisiyle ilişkilendirilmiş sitesi olmayan bir merkez sitesi olan yalnız bırakılmış hub sitesini sildi. Yalnız bırakılmış hub'ın nedeni büyük olasılıkla özgün hub sitesinin silinmesidir.|
|Gönderilen bağlantı silindi|SendToConnectionRemoved|SharePoint veya genel yönetici, SharePoint yönetim merkezindeki Kayıtlar yönetim sayfasındaki Gönder bağlantısını siler.|
|Site silindi|SiteDeleted|Site yöneticisi siteyi siler.|
|Etkin belge önizlemesi|PreviewModeEnabledSet|Site yöneticisi bir site için belge önizlemesini etkinleştirir.|
|Etkin eski iş akışı|LegacyWorkflowEnabledSet|Site yöneticisi veya sahibi SharePoint 2013 İş Akışı Görevi içerik türünü siteye ekler. Genel yöneticiler, SharePoint yönetim merkezinde kuruluşun tamamı için iş akışlarını da etkinleştirebilir.|
|İsteğe Bağlı Office Etkinleştirildi|OfficeOnDemandSet|Site yöneticisi, kullanıcıların Office masaüstü uygulamalarının en son sürümüne erişmesini sağlayan İsteğe Bağlı Office etkinleştirir. İsteğe Bağlı Office SharePoint yönetim merkezinde etkinleştirilir ve tam, yüklü Office uygulamaları içeren bir Microsoft 365 aboneliği gerektirir.|
|Kişi Aramaları için etkin sonuç kaynağı|PeopleResultsScopeSet|Site yöneticisi, site için Kişi Aramaları için sonuç kaynağını oluşturur.|
|Etkin RSS akışları|NewsFeedEnabledSet|Site yöneticisi veya sahibi bir site için RSS akışlarını etkinleştirir. Genel yöneticiler, SharePoint yönetim merkezinde kuruluşun tamamı için RSS akışlarını etkinleştirebilir.|
|Hub sitesine katılmış site|HubSiteJoined|Site sahibi, sitesini bir hub sitesiyle ilişkilendirir.|
|Değiştirilen site koleksiyonu kotası|SiteCollectionQuotaModified|Site yöneticisi, site koleksiyonu kotasını değiştirir.|
|Kayıtlı hub sitesi|HubSiteRegistered|SharePoint veya genel yönetici bir merkez sitesi oluşturur. Sonuçlar, sitenin bir hub sitesi olarak kayıtlı olmasıdır.|
|İzin verilen veri konumu kaldırıldı|AllowedDataLocationDeleted|SharePoint veya genel yönetici, çok coğrafi bir ortamda izin verilen bir veri konumunu kaldırdı.|
|Coğrafi konum yöneticisi kaldırıldı|GeoAdminDeleted|SharePoint veya genel yönetici, bir kullanıcıyı konumun coğrafi yöneticisi olarak kaldırdı.|
|Site yeniden adlandırıldı|SiteRenamed|Site yöneticisi veya sahibi siteyi yeniden adlandırır|
|Zamanlanmış site coğrafi taşıma|SiteGeoMoveScheduled|SharePoint veya genel yönetici bir SharePoint veya OneDrive site coğrafi taşımayı başarıyla zamanlar. Multi-Geo özelliği, bir kuruluşun coğrafi bölge olarak adlandırılan birden çok Microsoft veri merkezi coğrafyasına yayılmasına olanak tanır. Daha fazla bilgi için bkz[. OneDrive ve SharePoint Online'da Multi-Geo Özellikleri](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Konak sitesini ayarlama|HostSiteSet|SharePoint veya genel yönetici, belirlenen siteyi kişisel veya OneDrive İş siteleri barındıracak şekilde değiştirir.|
|Coğrafi konum için depolama kotası ayarlama|GeoQuotaAllocated|SharePoint veya genel yönetici, çok coğrafi ortamdaki bir coğrafi konum için depolama kotasını yapılandırdı.|
|Merkez sitesinden ayrılmamış site|HubSiteUnjoined|Site sahibi, sitenin merkez sitesinden ayrılmasını sağlar.|
|Kayıtlı olmayan hub sitesi|HubSiteUnregistered|SharePoint veya genel yönetici sitenin kaydını merkez sitesi olarak kaldırıyor. Bir hub sitesinin kaydı kaldırıldığında, artık hub sitesi olarak çalışmaz.|

### <a name="exchange-mailbox-activities"></a>Posta kutusu etkinliklerini Exchange

Aşağıdaki tabloda, posta kutusu denetim günlüğü tarafından günlüğe kaydedilebilecek etkinlikler listelenir. Posta kutusu sahibi, temsilci kullanıcı veya yönetici tarafından gerçekleştirilen posta kutusu etkinlikleri, denetim günlüğüne otomatik olarak 90 güne kadar günlüğe kaydedilir. Bir yöneticinin kuruluşunuzdaki tüm kullanıcılar için posta kutusu denetim günlüğünü kapatması mümkündür. Bu durumda, hiçbir kullanıcı için hiçbir posta kutusu eylemi günlüğe kaydedilmez. Daha fazla bilgi için bkz. [Posta kutusu denetimini yönetme](enable-mailbox-auditing.md).

 Exchange Online PowerShell'de [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) cmdlet'ini kullanarak da posta kutusu etkinliklerini arayabilirsiniz.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Erişilen posta kutusu öğeleri|MailItemsAccessed|İletiler posta kutusunda okundu veya bu iletilere erişildi. Bu etkinliğin denetim kayıtları iki yoldan biriyle tetiklenir: posta istemcisi (Outlook gibi) iletilerde bağlama işlemi gerçekleştirdiğinde veya posta protokolleri (Exchange ActiveSync veya IMAP gibi) posta klasöründeki öğeleri eşitlediğinde. Bu etkinlik yalnızca Office 365 veya Microsoft 365 E5 lisansı olan kullanıcılar için günlüğe kaydedilir. Bu etkinlik için denetim kayıtlarını analiz etmek, güvenliği aşılmış e-posta hesabı araştırılırken yararlıdır. Daha fazla bilgi için Denetim (Premium) bölümündeki "[Denetim (Premium](advanced-audit.md#audit-premium-events)) olayları" bölümüne bakın. |
|Temsilci posta kutusu izinleri eklendi|Add-MailboxPermission|Yönetici, kullanıcıya (temsilci olarak bilinir) FullAccess posta kutusu iznini başka bir kişinin posta kutusuna atadı. FullAccess izni, temsilcinin diğer kişinin posta kutusunu açmasına ve posta kutusunun içeriğini okumasına ve yönetmesine olanak tanır. Bu etkinliğin denetim kaydı, Microsoft 365 hizmetindeki bir sistem hesabı kuruluşunuz adına düzenli aralıklarla bakım görevleri gerçekleştirdiğinde de oluşturulur. Sistem hesabı tarafından gerçekleştirilen yaygın bir görev, sistem posta kutuları için izinleri güncelleştirmektir. Daha fazla bilgi için bkz. [posta kutusu denetim kayıtları Exchange sistem hesapları](#system-accounts-in-exchange-mailbox-audit-records).|
|Takvim klasörüne temsilci erişimi olan kullanıcı eklendi veya kaldırıldı|UpdateCalendarDelegation|Kullanıcı, başka bir kullanıcının posta kutusunun takvimine temsilci olarak eklendi veya kaldırıldı. Takvim temsilcisi, aynı kuruluştaki başka birine posta kutusu sahibinin takvimini yönetme izni verir.|
|Klasöre izinler eklendi|AddFolderPermissions|Klasör izni eklendi. Klasör izinleri, kuruluşunuzdaki hangi kullanıcıların bir posta kutusundaki klasörlere ve bu klasörlerde bulunan iletilere erişebileceğini denetler.|
|İletileri başka bir klasöre kopyalandı|Kopya|İleti başka bir klasöre kopyalandı.|
|Posta kutusu öğesi oluşturuldu|Oluşturma|Posta kutusunun Takvim, Kişiler, Notlar veya Görevler klasöründe bir öğe oluşturulur. Örneğin, yeni bir toplantı isteği oluşturulur. İleti oluşturma, gönderme veya alma denetlenmiyor. Ayrıca, posta kutusu klasörü oluşturma işlemi denetlenmiyor.|
|Outlook web uygulamasında yeni gelen kutusu kuralı oluşturuldu|New-InboxRule|Posta kutusu sahibi veya posta kutusuna erişimi olan başka bir kullanıcı, Outlook web uygulamasında bir gelen kutusu kuralı oluşturdu.|
|Silinmiş Öğeler klasöründen silinen iletiler|SoftDelete|İleti kalıcı olarak silinmiş veya Silinmiş Öğeler klasöründen silinmiş. Bu öğeler Kurtarılabilir Öğeler klasörüne taşınır. İletiler, kullanıcı tarafından seçildiğinde ve **Shift+Delete** tuşlarına basıldığında kurtarılabilir Öğeler klasörüne de taşınır.|
|İleti kayıt olarak etiketlendi|ApplyRecordLabel|İleti kayıt olarak sınıflandırıldı. Bu durum, içeriği kayıt olarak sınıflandırır bir bekletme etiketi el ile veya iletiye otomatik olarak uygulandığında oluşur.|
|İletiler başka bir klasöre taşındı|Hareket|İleti başka bir klasöre taşındı.|
|İletiler Silinmiş Öğeler klasörüne taşındı|MoveToDeletedItems|Bir ileti silindi ve Silinmiş Öğeler klasörüne taşındı.|
|Değiştirilen klasör izni|UpdateFolderPermissions|Klasör izni değiştirildi. Klasör izinleri, kuruluşunuzdaki hangi kullanıcıların posta kutusu klasörlerine ve klasördeki iletilere erişebileceğini denetler.|
|Outlook web uygulamasından değiştirilen gelen kutusu kuralı|Set-InboxRule|Posta kutusu sahibi veya posta kutusuna erişimi olan başka bir kullanıcı, Outlook web uygulamasını kullanarak gelen kutusu kuralını değiştirdi.|
|İletileri posta kutusundan temizleme|HardDelete|Kurtarılabilir Öğeler klasöründen bir ileti temizlendi (posta kutusundan kalıcı olarak silindi).|
|Temsilci posta kutusu izinleri kaldırıldı|Remove-MailboxPermission|Yönetici, bir kişinin posta kutusundan FullAccess iznini (temsilciye atanmış olan) kaldırdı. FullAccess izni kaldırıldıktan sonra, temsilci diğer kişinin posta kutusunu açamaz veya içindeki herhangi bir içeriğe erişemez.|
|Klasörden izinler kaldırıldı|RemoveFolderPermissions|Klasör izni kaldırıldı. Klasör izinleri, kuruluşunuzdaki hangi kullanıcıların bir posta kutusundaki klasörlere ve bu klasörlerde bulunan iletilere erişebileceğini denetler.|
|İleti gönderildi|Gönderin|Bir ileti gönderildi, yanıtlandı veya iletildi. Bu etkinlik yalnızca Office 365 veya Microsoft 365 E5 lisansı olan kullanıcılar için günlüğe kaydedilir. Daha fazla bilgi için Denetim (Premium) bölümündeki "[Denetim (Premium](advanced-audit.md#audit-premium-events)) olayları" bölümüne bakın.|
|Farklı Gönder izinleri kullanılarak gönderilen ileti|GöndermeLer|SendAs izni kullanılarak bir ileti gönderildi. Bu, başka bir kullanıcının iletiyi posta kutusu sahibinden gelmiş gibi gönderdiği anlamına gelir.|
|Adına Gönder izinleri kullanılarak gönderilen ileti|SendOnBehalf|SendOnBehalf izni kullanılarak bir ileti gönderildi. Bu, başka bir kullanıcının iletiyi posta kutusu sahibi adına gönderdiği anlamına gelir. İleti, iletinin adına gönderildiği alıcıyı ve iletiyi gerçekten göndereni belirtir.|
|Outlook istemcisinden gelen kutusu kuralları güncelleştirildi|UpdateInboxRules|Posta kutusu sahibi veya Outlook istemcisini kullanarak gelen kutusu kuralı oluşturulan, değiştirilen veya kaldırılan posta kutusuna erişimi olan başka bir kullanıcı.|
|İleti güncelleştirildi|Güncelleştirme|İleti veya özellikleri değiştirildi.|
|Kullanıcı posta kutusunda oturum açtı|MailboxLogin|Kullanıcı posta kutusunda oturum açtı.|
|İletiyi kayıt olarak etiketleme||Kullanıcı bir e-posta iletisine bekletme etiketi uyguladı ve bu etiket öğeyi kayıt olarak işaretlemek için yapılandırıldı. |

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Exchange posta kutusu denetim kayıtlarındaki sistem hesapları

Bazı posta kutusu etkinliklerinin denetim kayıtlarında (özellikle **Add-MailboxPermissions**), etkinliği gerçekleştiren kullanıcının (ve User ve UserId alanlarında tanımlanan) NT AUTHORITY\SYSTEM veya NT AUTHORITY\SYSTEM(Microsoft.Exchange) olduğunu fark edebilirsiniz. Servicehost). Bu, etkinliği gerçekleştiren "kullanıcının" Microsoft bulutundaki Exchange hizmetindeki bir sistem hesabı olduğunu gösterir. Bu sistem hesabı genellikle kuruluşunuz adına zamanlanmış bakım görevleri gerçekleştirir. Örneğin, NT AUTHORITY\SYSTEM(Microsoft.Exchange) tarafından gerçekleştirilen yaygın bir denetim etkinliği. ServiceHost) hesabı, bir sistem posta kutusu olan DiscoverySearchMailbox üzerindeki izinleri güncelleştirmektir. Bu güncelleştirmenin amacı, DiscoverySearchMailbox için Bulma Yönetimi rol grubuna FullAccess izninin (varsayılandır) atandığını doğrulamaktır. Bu, eBulma yöneticilerinin kuruluşlarında gerekli görevleri gerçekleştirebilmesini sağlar.

**Add-MailboxPermission** için bir denetim kaydında tanımlanabilir başka bir sistem kullanıcı hesabı Administrator@apcprd03.prod.outlook.com. Bu hizmet hesabı, DiscoverySearchMailbox sistem posta kutusu için Bulma Yönetimi rol grubuna FullAccess izninin atandığını doğrulama ve güncelleştirmeyle ilgili posta kutusu denetim kayıtlarına da eklenir. Özellikle, Administrator@apcprd03.prod.outlook.com hesabını tanımlayan denetim kayıtları genellikle Microsoft destek personeli kuruluşunuz adına bir RBAC rol tanılama aracı çalıştırdığında tetiklenir.

### <a name="user-administration-activities"></a>Kullanıcı yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) veya Azure yönetim portalını kullanarak kullanıcı hesabı eklediğinde veya değiştirdiğinde günlüğe kaydedilen kullanıcı yönetimi etkinlikleri listelenmektedir.

> [!NOTE]
> Aşağıdaki tablodaki **İşlem** sütununda listelenen işlem adları bir nokta ( `.` ) içerir. Denetim günlüğünde arama yaparken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi bir PowerShell komutunda belirtirseniz, işlemi adına nokta eklemeniz gerekir. İşlem adını içermek için çift tırnak işareti (`" "`) kullandığınızdan da emin olun.

|Etkinlik|Işlem|Açıklama|
|:-----|:-----|:-----|
|Kullanıcı eklendi|Kullanıcı ekle'yi seçin.|Bir kullanıcı hesabı oluşturuldu.|
|Kullanıcı lisansı değiştirildi|Kullanıcı lisansını değiştirin.|Kullanıcıya atanan lisans değişti. Hangi lisansların değişiklik olduğunu görmek için ilgili **Güncelleştirilmiş kullanıcı** etkinliğine bakın.|
|Kullanıcı parolası değiştirildi|Kullanıcı parolasını değiştirin.|Kullanıcı parolasını değiştirir. Kullanıcıların parolalarını sıfırlamasına izin vermek için kuruluşunuzda self servis parola sıfırlamanın (tüm veya seçili kullanıcılar için) etkinleştirilmesi gerekir. Azure Active Directory'de self servis parola sıfırlama etkinliğini de izleyebilirsiniz. Daha fazla bilgi için bkz[. Azure AD parola yönetimi için raporlama seçenekleri](/azure/active-directory/authentication/howto-sspr-reporting).
|Silinen kullanıcı|Kullanıcıyı silin.|Bir kullanıcı hesabı silindi.|
|Kullanıcı parolasını sıfırlama|Kullanıcı parolasını sıfırlayın.|Yönetici, bir kullanıcının parolasını sıfırlar.|
|Kullanıcıyı parolayı değiştirmeye zorlayan özelliği ayarlama|Zorla kullanıcı parolasını değiştir'i ayarlayın.|Yönetici, kullanıcının Microsoft 365 bir sonraki oturum açmasında kullanıcıyı parolasını değiştirmeye zorlayan özelliği ayarlar.|
|Lisans özelliklerini ayarlama|Lisans özelliklerini ayarlayın.|Yönetici, kullanıcıya atanan lisanslı bir kullanıcının özelliklerini değiştirir.|
|Güncelleştirilmiş kullanıcı|Kullanıcıyı güncelleştirin.|Yönetici, bir kullanıcı hesabının bir veya daha fazla özelliğini değiştirir. Güncelleştirilebilecek kullanıcı özelliklerinin listesi için [Denetim Raporu Olaylarını Azure Active Directory](/azure/active-directory/reports-monitoring/concept-audit-logs) "Kullanıcı özniteliklerini güncelleştirme" bölümüne bakın.|

### <a name="azure-ad-group-administration-activities"></a>Grup yönetimi etkinliklerini Azure AD

Aşağıdaki tabloda, bir yönetici veya kullanıcı bir Microsoft 365 Grubu oluşturduğunda veya değiştirdiğinde ya da yönetici [Microsoft 365 yönetim merkezi veya Azure](https://go.microsoft.com/fwlink/p/?linkid=2024339) yönetim portalını kullanarak bir güvenlik grubu oluşturduğunda günlüğe kaydedilen grup yönetimi etkinlikleri listelenmektedir. Microsoft 365 grupları hakkında daha fazla bilgi için bkz. [Microsoft 365 yönetim merkezi Grupları görüntüleme, oluşturma ve silme](../admin/create-groups/create-groups.md).

> [!NOTE]
> Aşağıdaki tablodaki **İşlem** sütununda listelenen işlem adları bir nokta ( `.` ) içerir. Denetim günlüğünde arama yaparken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi bir PowerShell komutunda belirtirseniz, işlemi adına nokta eklemeniz gerekir. İşlem adını içermek için çift tırnak işareti (`" "`) kullandığınızdan da emin olun.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Grup eklendi|Grup ekle'yi seçin.|Bir grup oluşturuldu.|
|Gruba üye eklendi|Gruba üye ekleyin.|Gruba bir üye eklendi.|
|Grup silindi|Grubu sil'i seçin.|Bir grup silindi.|
|Gruptan üye kaldırıldı|Gruptan üyeyi kaldırın.|Gruptan bir üye kaldırıldı.|
|Güncelleştirilmiş grup|Grubu güncelleştirin.|Bir grubun özelliği değiştirildi.|

### <a name="application-administration-activities"></a>Uygulama yönetimi etkinlikleri

Aşağıdaki tabloda, bir yönetici Azure AD kayıtlı bir uygulamayı eklediğinde veya değiştirdiğinde günlüğe kaydedilen uygulama yöneticisi etkinlikleri listelenir. Kimlik doğrulaması için Azure AD kullanan tüm uygulamalar dizine kaydedilmelidir.

> [!NOTE]
> Aşağıdaki tablodaki **İşlem** sütununda listelenen işlem adları bir nokta ( `.` ) içerir. Denetim günlüğünde arama yaparken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi bir PowerShell komutunda belirtirseniz, işlemi adına nokta eklemeniz gerekir. İşlem adını içermek için çift tırnak işareti (`" "`) kullandığınızdan da emin olun.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Temsilci girdisi eklendi|Temsilci girdisi ekleyin.|Azure AD'da bir uygulamaya kimlik doğrulama izni oluşturuldu/verildi.|
|Hizmet sorumlusu eklendi|Hizmet sorumlusu ekleyin.|Azure AD'de bir uygulama kaydedildi. Bir uygulama, dizindeki bir hizmet sorumlusu tarafından temsil edilir.|
|Hizmet sorumlusuna kimlik bilgileri eklendi|Hizmet sorumlusu kimlik bilgileri ekleyin.|Kimlik bilgileri Azure AD'daki bir hizmet sorumlusuna eklendi. Hizmet ilkesi, dizindeki bir uygulamayı temsil eder.|
|Temsilci girdisi kaldırıldı|Temsilci girdisini kaldırın.|Azure AD'daki bir uygulamadan kimlik doğrulama izni kaldırıldı.|
|Dizinden hizmet sorumlusu kaldırıldı|Hizmet sorumlusunu kaldırın.|Bir uygulama Azure AD silindi/kaydı silindi. Bir uygulama, dizindeki bir hizmet sorumlusu tarafından temsil edilir.|
|Hizmet sorumlusundan kimlik bilgileri kaldırıldı|Hizmet sorumlusu kimlik bilgilerini kaldırın.|Kimlik bilgileri Azure AD bir hizmet sorumlusundan kaldırıldı. Hizmet ilkesi, dizindeki bir uygulamayı temsil eder.|
|Temsilci girişini ayarlama|Temsilci girişini ayarlayın.|Azure AD'daki bir uygulama için kimlik doğrulama izni güncelleştirildi.|

### <a name="role-administration-activities"></a>Rol yönetimi etkinlikleri

Aşağıdaki tabloda, yönetici Microsoft 365 yönetim merkezi veya Azure yönetim portalında yönetici rollerini yönettiğinde günlüğe kaydedilen [Azure AD](https://go.microsoft.com/fwlink/p/?linkid=2024339) rol yönetimi etkinlikleri listelenmektedir.

> [!NOTE]
> Aşağıdaki tablodaki **İşlem** sütununda listelenen işlem adları bir nokta ( `.` ) içerir. Denetim günlüğünde arama yaparken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi bir PowerShell komutunda belirtirseniz, işlemi adına nokta eklemeniz gerekir. İşlem adını içermek için çift tırnak işareti (`" "`) kullandığınızdan da emin olun.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Role üye ekleme|Role üye ekleyin.|Microsoft 365'da yönetici rolüne bir kullanıcı eklendi.|
|Dizin rolünden kullanıcı kaldırıldı|Üyeyi rolden kaldırın.|Microsoft 365'daki yönetici rolünden kullanıcı kaldırıldı.|
|Şirket iletişim bilgilerini ayarlama|Şirket iletişim bilgilerini ayarlayın.|Kuruluşunuz için şirket düzeyinde iletişim tercihleri güncelleştirildi. Bu, Microsoft 365 tarafından gönderilen abonelikle ilgili e-posta adreslerini ve hizmetlerle ilgili teknik bildirimleri içerir.|

### <a name="directory-administration-activities"></a>Dizin yönetimi etkinlikleri

Aşağıdaki tabloda, bir yönetici kuruluşunu Microsoft 365 yönetim merkezi veya Azure yönetim portalında yönettiğinde günlüğe kaydedilen [Azure AD](https://go.microsoft.com/fwlink/p/?linkid=2024339) dizin ve etki alanıyla ilgili etkinlikler listelenmektedir.

> [!NOTE]
> Aşağıdaki tablodaki **İşlem** sütununda listelenen işlem adları bir nokta ( `.` ) içerir. Denetim günlüğünde arama yaparken, denetim bekletme ilkeleri oluştururken, uyarı ilkeleri oluştururken veya etkinlik uyarıları oluştururken işlemi bir PowerShell komutunda belirtirseniz, işlemi adına nokta eklemeniz gerekir. İşlem adını içermek için çift tırnak işareti (`" "`) kullandığınızdan da emin olun.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Şirkete etki alanı eklendi|Şirkete etki alanı ekleyin.|Kuruluşunuza bir etki alanı eklendi.|
|Dizine bir iş ortağı eklendi|Şirkete iş ortağı ekleyin.|Kuruluşunuza bir iş ortağı (yönetici temsilcisi) eklendi.|
|Şirketten etki alanı kaldırıldı|Şirketten etki alanını kaldırın.|Kuruluşunuzdan bir etki alanı kaldırıldı.|
|Dizinden bir iş ortağı kaldırıldı|İş ortağını şirketten kaldırın.|Kuruluşunuzdan bir iş ortağı (yönetici temsilcisi) kaldırıldı.|
|Şirket bilgilerini ayarlama|Şirket bilgilerini ayarlayın.|Kuruluşunuz için şirket bilgileri güncelleştirildi. Bu, Microsoft 365 tarafından gönderilen abonelikle ilgili e-posta adreslerini ve Microsoft 365 hizmetleriyle ilgili teknik bildirimleri içerir.|
|Etki alanı kimlik doğrulamayı ayarlama|Etki alanı kimlik doğrulamayı ayarlayın.|Kuruluşunuz için etki alanı kimlik doğrulaması ayarı değiştirildi.|
|Etki alanı için federasyon ayarları güncelleştirildi|Etki alanında federasyon ayarlarını yapın.|Kuruluşunuz için federasyon (dış paylaşım) ayarları değiştirildi.|
|Parola ilkesini ayarlama|Parola ilkesini ayarlayın.|Kuruluşunuzdaki kullanıcı parolalarının uzunluk ve karakter kısıtlamaları değiştirildi.|
|Azure AD eşitlemeyi açtı|DirSyncEnabled bayrağını ayarlayın.|Azure AD Eşitleme için bir dizini etkinleştiren özelliği ayarlayın.|
|Güncelleştirilmiş etki alanı|Etki alanını güncelleştirin.|Kuruluşunuzdaki bir etki alanının ayarları güncelleştirildi.|
|Doğrulanmış etki alanı|Etki alanını doğrulayın.|Kuruluşunuzun bir etki alanının sahibi olduğu doğrulandı.|
|Doğrulanmış e-posta doğrulanmış etki alanı|Doğrulanmış e-posta etki alanını doğrulayın.|Kuruluşunuzun bir etki alanının sahibi olduğunu doğrulamak için e-posta doğrulamasını kullandınız.|

### <a name="ediscovery-activities"></a>eBulma etkinlikleri

Güvenlik ve uyumluluk portalında veya ilgili PowerShell cmdlet'leri çalıştırılarak gerçekleştirilen İçerik Arama ve eBulma ile ilgili etkinlikler denetim günlüğüne kaydedilir. Bu, aşağıdaki etkinlikleri içerir:

- eBulma servis taleplerini oluşturma ve yönetme

- İçerik Aramalarını oluşturma, başlatma ve düzenleme

- Arama sonuçlarını önizleme, dışarı aktarma ve silme gibi İçerik Arama eylemleri gerçekleştirme

- İçerik Arama için izin filtrelemeyi yapılandırma

- eBulma Yöneticisi rolünü yönetme

Günlüğe kaydedilen eBulma etkinliklerinin listesi ve ayrıntılı açıklaması için bkz. [Denetim günlüğünde eBulma etkinliklerini arama](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Etkinlikler **açılan listesinde** **eBulma etkinlikleri** ve **eBulma (Premium) etkinlikleri altında listelenen etkinliklerden kaynaklanan olayların** arama sonuçlarında görüntülenmesi 30 dakikaya kadar sürer. Buna karşılık, eBulma cmdlet etkinliklerinden gelen olayların arama sonuçlarında görünmesi 24 saate kadar sürer.

### <a name="ediscovery-premium-activities"></a>eBulma (Premium) etkinlikleri

Microsoft Purview eBulma (Premium) içindeki etkinlikler için denetim günlüğünde de arama yapabilirsiniz. Bu etkinliklerin açıklaması [için denetim günlüğünde eBulma](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-premium-activities) etkinliklerini arama bölümündeki "eBulma (Premium) etkinlikleri" bölümüne bakın.

### <a name="power-bi-activities"></a>Power BI etkinlikleri

denetim günlüğünde Power BI etkinlikleri arayabilirsiniz. Power BI etkinlikleri hakkında bilgi için, [Kuruluşunuzda denetimi kullanma](/power-bi/service-admin-auditing#activities-audited-by-power-bi) bölümündeki "Power BI tarafından denetlenen etkinlikler" bölümüne bakın.

Power BI için denetim günlüğü varsayılan olarak etkin değildir. Denetim günlüğünde Power BI etkinlik aramak için, Power BI yönetici portalında denetimi etkinleştirmeniz gerekir. Yönergeler için Power BI [yönetici portalındaki](/power-bi/service-admin-portal#audit-logs) "Denetim günlükleri" bölümüne bakın.

### <a name="workplace-analytics-activities"></a>Workplace Analytics etkinlikleri

Workplace Analytics, grupların kuruluşunuz genelinde nasıl işbirliği yaptığını gösteren içgörüler sağlar. Aşağıdaki tabloda, Workplace Analytics'te Yönetici rolüne veya Analist rollerine atanmış kullanıcılar tarafından gerçekleştirilen etkinlikler listelenmiştir. Analist rolüne atanan kullanıcılar tüm hizmet özelliklerine tam erişime sahiptir ve analiz yapmak için ürünü kullanır. Yönetici rolüne atanan kullanıcılar gizlilik ayarlarını ve sistem varsayılanlarını yapılandırabilir ve Workplace Analytics'te kuruluş verilerini hazırlayabilir, karşıya yükleyebilir ve doğrulayabilir. Daha fazla bilgi için bkz [. Workplace Analytics](/workplace-analytics/index-orig).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Erişilen OData bağlantısı|AccessedOdataLink|Analist bir sorgunun OData bağlantısına erişmiş.|
|sorgu iptal edildi|CanceledQuery|Analist çalışan sorguyu iptal etti.|
|Toplantı dışlaması oluşturuldu|MeetingExclusionCreated|Analist bir toplantı dışlama kuralı oluşturdu.|
|Silinen sonuç|DeletedResult|Analist bir sorgu sonucunu sildi.|
|İndirilen rapor|İndirilen Rapor|Analist bir sorgu sonuç dosyası indirdi.|
|Yürütülen sorgu|ExecutedQuery|Analist bir sorgu çalıştırmıştı.|
|Güncelleştirilmiş veri erişimi ayarı|UpdatedDataAccessSetting|Yönetici güncelleştirilmiş veri erişim ayarları.|
|Güncelleştirilmiş gizlilik ayarı|UpdatedPrivacySetting|Yönetici güncelleştirilmiş gizlilik ayarları; örneğin, en düşük grup boyutu.|
|Karşıya yüklenen kuruluş verileri|UploadedOrgData|Yönetici kurumsal veri dosyası.|
|Oturum açan kullanıcı<sup>*</sup>| UserLoggedIn |Microsoft 365 kullanıcı hesabında oturum açan bir kullanıcı.|
|Kullanıcı oturumu kapattı<sup>*</sup>| UserLoggedOff |Bir kullanıcı, Microsoft 365 kullanıcı hesabında oturumu kapatmış.
|Araştırıldı|ViewedExplore|Analist görselleştirmeleri bir veya daha fazla Araştır sayfası sekmesinde görüntüledi.|

> [!NOTE]
> <sup>*</sup>Bunlar Azure Active Directory oturum açma ve kapatma etkinlikleridir. Kuruluşunuzda Workplace Analytics açık olmasa bile bu etkinlikler günlüğe kaydedilir. Kullanıcı oturum açma etkinlikleri hakkında daha fazla bilgi için bkz. [Azure Active Directory oturum açma günlükleri](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>Microsoft Teams etkinlikleri

Microsoft Teams'de kullanıcı ve yönetici etkinlikleri için denetim günlüğünde arama yapabilirsiniz. Teams, Microsoft 365'da sohbet merkezli bir çalışma alanıdır. Bir ekibin konuşmalarını, toplantılarını, dosyalarını ve notlarını tek bir yerde bir araya getirir. Denetlenen Teams etkinliklerinin açıklamaları için bkz[. denetim günlüğünde Microsoft Teams olayları arama](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Microsoft Teams Healthcare etkinlikleri

Kuruluşunuz Microsoft Teams'de [Hastalar uygulamasını](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) kullanıyorsa, Denetim günlüğünde Hastalar uygulamasını kullanarak ilgili etkinlikler için arama yapabilirsiniz. Ortamınız Hastalar uygulamasını destekleyecek şekilde yapılandırılmışsa, **Etkinlikler seçici listesinde** bu etkinlikler için ek bir etkinlik grubu sağlanır.

![Etkinlikler seçici listesinde Healthcare etkinliklerini Microsoft Teams.](../media/TeamsHealthcareAuditActivities.png)

Hastalar uygulaması etkinliklerinin açıklaması için bkz. [Hastalar uygulaması için denetim günlükleri](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Microsoft Teams Vardiyaları etkinlikleri

Kuruluşunuz Microsoft Teams'da Vardiyalar uygulamasını kullanıyorsa, Denetim günlüğünde Vardiyalar uygulamasını kullanarak ile ilgili etkinlikler için arama yapabilirsiniz. Ortamınız Vardiyalar uygulamalarını destekleyecek şekilde yapılandırılmışsa, **Etkinlikler seçici listesinde** bu etkinlikler için ek bir etkinlik grubu kullanılabilir.

Vardiyalar uygulama etkinliklerinin açıklaması için bkz[. denetim günlüğünde Microsoft Teams olayları arama](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Yammer etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen Yammer kullanıcı ve yönetici etkinlikleri listelenir. Denetim günlüğünden Yammer ilgili etkinlikleri döndürmek için **Etkinlikler** listesindeki **Tüm etkinlikler için sonuçları göster'i** seçmeniz gerekir. Arama sonuçlarını daraltmak için tarih aralığı kutularını ve **Kullanıcılar** listesini kullanın.

> [!NOTE]
> Bazı Yammer denetim etkinlikleri yalnızca Denetim (Premium) içinde kullanılabilir. Bu, bu etkinlikler denetim günlüğüne kaydedilmeden önce kullanıcılara uygun lisansın atanması gerektiği anlamına gelir. Yalnızca Denetim (Premium) içinde kullanılabilen etkinlikler hakkında daha fazla bilgi için bkz. [Microsoft 365'de Denetim (Premium).](advanced-audit.md#audit-premium-events) Denetim (Premium) lisans gereksinimleri için bkz. [Microsoft 365'de çözümleri denetleme](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Aşağıdaki tabloda, Denetim (Premium) etkinlikleri yıldız (*) ile vurgulanır.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Veri saklama ilkesi değiştirildi|SoftDeleteSettingsUpdated|Doğrulanmış yönetici, ağ veri saklama ilkesi ayarını Sabit Silme veya Geçici Silme olarak güncelleştirir. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirebilir.|
|Ağ yapılandırması değiştirildi|NetworkConfigurationUpdated|Ağ veya doğrulanmış yönetici Yammer ağının yapılandırmasını değiştirir. Bu, verileri dışarı aktarma aralığını ayarlamayı ve sohbeti etkinleştirmeyi içerir.|
|Ağ profili ayarları değiştirildi|ProcessProfileFields|Ağ veya doğrulanmış yönetici, ağ kullanıcıları ağı için üye profillerinde görünen bilgileri değiştirir.|
|Özel içerik modu değiştirildi|SupervisorAdminToggled|Doğrulanmış yönetici  *Özel İçerik Modu'nu*  açar veya kapatır. Bu mod, bir yöneticinin gönderileri özel gruplar halinde görüntülemesine ve tek tek kullanıcılar (veya kullanıcı grupları) arasındaki özel iletileri görüntülemesine olanak tanır. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirebilir.|
|Değiştirilen güvenlik yapılandırması|NetworkSecurityConfigurationUpdated|Doğrulanmış yönetici, Yammer ağının güvenlik yapılandırmasını güncelleştirir. Bu, parola süre sonu ilkelerini ve IP adreslerinde kısıtlamaları ayarlamayı içerir. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirebilir.|
|Dosya oluşturuldu|FileCreated|Kullanıcı bir dosyayı karşıya yükler.|
|Grup oluşturuldu|GroupCreation|Kullanıcı bir grup oluşturur.|
|İleti oluşturuldu<sup>*</sup>|İletiOluştur|Kullanıcı bir ileti oluşturur.|
|Grup silindi|GroupDeletion|Bir grup Yammer silinir.|
|İleti silindi|MessageDeleted|Kullanıcı bir iletiyi siler.|
|İndirilen dosya|FileDownloaded|Kullanıcı bir dosya indirir.|
|Dışarı aktarılan veriler|DataExport|Doğrulanmış yönetici Yammer ağ verilerini dışarı aktarır. Bu işlemi yalnızca doğrulanmış yöneticiler gerçekleştirebilir.|
|Topluluğa erişilemedi<sup>*</sup>|CommunityAccessFailure|Kullanıcı bir topluluğa erişemedi.|
|Dosyaya erişilemedi<sup>*</sup>|FileAccessFailure|Kullanıcı bir dosyaya erişemedi.|
|İletiye erişemedi<sup>*</sup>|MessageAccessFailure|Kullanıcı bir iletiye erişemedi.|
|Paylaşılan dosya|FileShared|Kullanıcı başka bir kullanıcıyla dosya paylaşır.|
|Askıya alınan ağ kullanıcısı|NetworkUserSuspended|Ağ veya doğrulanmış yönetici, kullanıcıyı Yammer askıya alır (devre dışı bırakır).|
|Askıya alınan kullanıcı|UserSuspension|Kullanıcı hesabı askıya alındı (devre dışı bırakıldı).|
|Güncelleştirilmiş dosya açıklaması|FileUpdateDescription|Kullanıcı dosyanın açıklamasını değiştirir.|
|Güncelleştirilmiş dosya adı|FileUpdateName|Kullanıcı dosyanın adını değiştirir.|
|İleti güncelleştirildi<sup>*</sup>|MessageUpdated|Kullanıcı bir iletiyi güncelleştirir.|
|Görüntülenen dosya|FileVisited|Kullanıcı bir dosyayı görüntüler.|
|görüntülenen ileti<sup>*</sup>|MessageViewed|Kullanıcı bir iletiyi görüntüler.|

### <a name="microsoft-power-automate-activities"></a>Microsoft Power Automate etkinlikleri

denetim günlüğünde Power Automate(eski adıyla Microsoft Flow) etkinlikler için arama yapabilirsiniz. Bu etkinlikler arasında akış oluşturma, düzenleme ve silme ve akış izinlerini değiştirme yer alır. Power Automate etkinlikleri için denetim hakkında bilgi için uyumluluk [portalında kullanıma sunulan denetim olayları Power Automate](https://flow.microsoft.com/blog/security-and-compliance-center) bloga bakın.

### <a name="microsoft-power-apps-activities"></a>Microsoft Power Apps etkinlikleri

Power Apps'da uygulamayla ilgili etkinlikler için denetim günlüğünde arama yapabilirsiniz. Bu etkinlikler arasında uygulama oluşturma, başlatma ve yayımlama yer alır. Uygulamalara izin atama işlemi de denetlenmektedir. Tüm Power Apps etkinliklerin açıklaması için bkz. [Power Apps için etkinlik günlüğü](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Microsoft Stream etkinlikleri

denetim günlüğünde Microsoft Stream etkinlikleri arayabilirsiniz. Bu etkinlikler kullanıcılar tarafından gerçekleştirilen video etkinliklerini, grup kanalı etkinliklerini ve kullanıcıları yönetme, kuruluş ayarlarını yönetme ve raporları dışarı aktarma gibi yönetici etkinliklerini içerir. Bu etkinliklerin açıklaması için Microsoft Stream Denetim [Günlükleri'ndeki "Stream'de günlüğe](/stream/audit-logs#actions-logged-in-stream) kaydedilen eylemler" bölümüne bakın.

### <a name="content-explorer-activities"></a>İçerik gezgini etkinlikleri

Aşağıdaki tabloda, içerik gezgininde denetim günlüğüne kaydedilen etkinlikler listelenmektedir. Uyumluluk portalındaki Veri sınıflandırmaları aracından erişilen içerik gezgini. Daha fazla bilgi için bkz. [Veri sınıflandırması içerik gezginini kullanma](data-classification-content-explorer.md).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Erişilen öğe|LabelContentExplorerAccessedItem|Yönetici (veya İçerik Gezgini İçerik Görüntüleyicisi rol grubunun üyesi olan bir kullanıcı), e-posta iletisini veya SharePoint/OneDrive belgesini görüntülemek için içerik gezginini kullanır.|

### <a name="quarantine-activities"></a>Karantina etkinlikleri

Aşağıdaki tabloda, denetim günlüğünde arayabileceğiniz karantina etkinlikleri listelenir. Karantina hakkında daha fazla bilgi için bkz. [E-posta iletilerini karantinaya alma](../security/office-365-security/quarantine-email-messages.md).

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Karantina iletisi silindi|QuarantineDelete|Bir kullanıcı, zararlı olduğu düşünülen bir e-posta iletisini sildi.|
|Dışarı aktarılan karantina iletisi|QuarantineExport|Kullanıcı, zararlı olduğu düşünülen bir e-posta iletisini dışarı aktardı.|
|Önizlemeli karantina iletisi|QuarantinePreview|Bir kullanıcı, zararlı olduğu düşünülen bir e-posta iletisinin önizlemesini görüntüledi.|
|Karantina iletisi yayımlandı|QuarantineRelease|Bir kullanıcı karantinadan zararlı olduğu düşünülen bir e-posta iletisi yayımladı.|
|Karantina iletisinin üst bilgisi görüntülendi|QuarantineViewHeader|Kullanıcı üst bilgiyi, zararlı olduğu düşünülen bir e-posta iletisiyle görüntüledi.|

### <a name="microsoft-forms-activities"></a>Microsoft Forms etkinlikleri

Bu bölümdeki tablolar, denetim günlüğüne kaydedilen Microsoft Forms kullanıcı ve yönetici etkinlikleridir. Microsoft Forms, analiz için veri toplamak için kullanılan bir form/test/anket aracıdır. Açıklamalarda aşağıda belirtilen durumlarda, bazı işlemler ek etkinlik parametreleri içerir.

Bir Forms etkinliği bir ortak yazar veya anonim yanıtlayıcı tarafından gerçekleştiriliyorsa, biraz farklı günlüğe kaydedilir. Daha fazla bilgi için [, birlikte yazanlar ve anonim yanıtlayanlar tarafından gerçekleştirilen Formlar etkinlikleri](#forms-activities-performed-by-coauthors-and-anonymous-responders) bölümüne bakın.

> [!NOTE]
> Bazı Forms denetim etkinlikleri yalnızca Denetim (Premium) içinde kullanılabilir. Bu, bu etkinlikler denetim günlüğüne kaydedilmeden önce kullanıcılara uygun lisansın atanması gerektiği anlamına gelir. Yalnızca Denetim (Premium) içinde kullanılabilen etkinlikler hakkında daha fazla bilgi için bkz. [Microsoft 365'de Denetim (Premium).](advanced-audit.md#audit-premium-events) Denetim (Premium) lisans gereksinimleri için bkz. [Microsoft 365'de çözümleri denetleme](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Aşağıdaki tabloda, Denetim (Premium) etkinlikleri yıldız (*) ile vurgulanır.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Açıklama oluşturuldu|CreateComment|Form sahibi teste açıklama veya puan ekler.|
|Form oluşturuldu|CreateForm|Form sahibi yeni bir form oluşturur. <br><br>Property DataMode:string, özellik değeri DataSync'e eşitse geçerli formun yeni veya mevcut bir Excel çalışma kitabıyla eşitlenecek şekilde ayarlandığını gösterir. ExcelWorkbookLink:string özelliği, geçerli formun ilişkili Excel çalışma kitabı kimliğini gösterir.|
|Düzenlenen form|EditForm|Form sahibi soru oluşturma, kaldırma veya düzenleme gibi bir formu düzenler. *EditOperation:string* özelliği, düzenleme işleminin adını gösterir. Olası işlemler şunlardır:<br/>- CreateQuestion<br/>- CreateQuestionChoice <br/>- DeleteQuestion <br/>- DeleteQuestionChoice <br/>- DeleteFormImage <br/>- DeleteQuestionImage <br/>- UpdateQuestion <br/>- UpdateQuestionChoice <br/>- UploadFormImage/Bing/Onedrive <br/>- UploadQuestionImage <br/>- ChangeTheme <br><br>FormImage, Formlar'da kullanıcının sorgu veya arka plan teması gibi bir görüntüyü karşıya yükleyebileceği herhangi bir yer içerir.|
|Taşınan form|MoveForm|Form sahibi formu taşır. <br><br>DestinationUserId:string özelliği, formu taşıyan kişinin kullanıcı kimliğini gösterir. NewFormId:string özelliği, yeni kopyalanan formun yeni kimliğidir. IsDelegateAccess:boolean özelliği, geçerli form taşıma eyleminin yönetici temsilcisi sayfası üzerinden gerçekleştirildiğini gösterir.|
|Silinen form|DeleteForm|Form sahibi formu siler. Buna SoftDelete (kullanılan silme seçeneği ve geri dönüşüm kutusuna taşınan form) ve HardDelete (Geri dönüşüm kutusu boşaltıldı) dahildir.|
|Görüntülenen form (tasarım zamanı)|Görünüm Formu|Form sahibi, düzenlemek üzere var olan bir formu açar. <br><br>AccessDenied:boolean özelliği, izin denetimi nedeniyle geçerli formun erişiminin reddedilmiş olduğunu gösterir. FromSummaryLink:boolean özelliği, geçerli isteğin özet bağlantı sayfasından geldiğini gösterir.|
|Ön izleme formu|PreviewForm|Form sahibi, Preview işlevini kullanarak formun önizlemesini gösterir.|
|Dışarı aktarılan form|ExportForm|Form sahibi sonuçları Excel dışarı aktarır. <br><br>ExportFormat:string Özelliği, Excel dosyasının İndir veya Çevrimiçi olduğunu gösterir.|
|Kopyalama için izin verilen paylaşım formu|AllowShareFormForCopy|Form sahibi, formu diğer kullanıcılarla paylaşmak için bir şablon bağlantısı oluşturur. Form sahibi şablon URL'sini oluşturmak için tıkladığında bu olay günlüğe kaydedilir.|
|Kopya için izin verilmeyen paylaşım formu|DisallowShareFormForCopy|Form sahibi şablon bağlantısını siler.|
|Form birlikte yazma eklendi|AddFormCoauthor|Kullanıcı, yanıtları tasarlamaya/görüntülemeye yardımcı olmak için bir işbirliği bağlantısı kullanır. Bu olay, kullanıcı bir harmanlama URL'si kullandığında günlüğe kaydedilir (harmanlama URL'si ilk oluşturulduğunda günlüğe kaydedilmez).|
|Form birlikte yazması kaldırıldı|RemoveFormCoauthor|Form sahibi işbirliği bağlantısını siler.|
|Görüntülenen yanıt sayfası|ViewRuntimeForm|Kullanıcı görüntülemek için bir yanıt sayfası açtı. Bu olay, kullanıcının yanıt gönderip göndermediğine bakılmaksızın günlüğe kaydedilir.|
|Yanıt oluşturuldu|CreateResponse|Yeni yanıt almaya benzer.  Kullanıcı bir forma yanıt gönderdi. <br><br>Property ResponseId:string ve Property ResponderId:string hangi sonucun görüntülendiğini gösterir. <br><br>Anonim yanıtlayıcı için ResponderId özelliği null olur.|
|Güncelleştirilmiş yanıt|UpdateResponse|Form sahibi, testte bir açıklamayı veya puanı güncelleştirdi. <br><br>Property ResponseId:string ve Property ResponderId:string hangi sonucun görüntülendiğini gösterir. <br><br>Anonim yanıtlayıcı için ResponderId özelliği null olur.|
|Tüm yanıtlar silindi|DeleteAllResponses|Form sahibi tüm yanıt verilerini siler.|
|Yanıt Silindi|Deleteresponse|Form sahibi bir yanıtı siler. <br><br>Property ResponseId:string, yanıtın silindiğini gösterir.|
|Görüntülenen yanıtlar|ViewResponses|Form sahibi, toplanan yanıt listesini görüntüler. <br><br>ViewType:string Özelliği, form sahibinin Ayrıntı mı yoksa Toplama mı görüntülediğini gösterir|
|Görüntülenen yanıt|ViewResponse|Form sahibi belirli bir yanıtı görüntüler. <br><br>Property ResponseId:string ve Property ResponderId:string hangi sonucun görüntülendiğini gösterir. <br><br>Anonim yanıtlayıcı için ResponderId özelliği null olur.|
|Özet bağlantısı oluşturuldu|GetSummaryLink|Form sahibi, sonuçları paylaşmak için özet sonuçlar bağlantısı oluşturur.|
|Silinen özet bağlantısı|DeleteSummaryLink|Form sahibi özet sonuçları bağlantısını siler.|
|Form kimlik avı durumu güncelleştirildi|UpdatePhishingStatus|Bu olay, iç güvenlik durumunun ayrıntılı değeri değiştirildiğinde, bunun son güvenlik durumunu değiştirip değiştirmediğine bakılmaksızın günlüğe kaydedilir (örneğin, form artık Kapalı veya Açık durumdadır). Bu, son güvenlik durumu değişikliği olmadan yinelenen olaylar görebileceğiniz anlamına gelir. Bu olayın olası durum değerleri şunlardır:<br/>- Aşağı Al <br/>- Yönetici <br/>- Yönetici Engeli Kaldırıldı <br/>- Otomatik Engellendi <br/>- Otomatik Engeli Kaldırıldı <br/>- Müşteri Tarafından Bildirilen <br/>- Bildirilen Müşteriyi Sıfırla|
|Kullanıcı kimlik avı durumu güncelleştirildi|UpdateUserPhishingStatus|Bu olay, kullanıcı güvenlik durumu değeri her değiştirildiğinde günlüğe kaydedilir. Denetim kaydındaki kullanıcı durumunun değeri, Kullanıcı Microsoft Online güvenlik ekibi tarafından indirilmiş bir kimlik avı formu oluşturduğunda **Kimlik Avı Olarak Onaylandı şeklindedir** . Yönetici kullanıcının engellemesini kaldırırsa, kullanıcının durumunun değeri **Normal Kullanıcı Olarak Sıfırla olarak** ayarlanır.|
|Gönderilmiş Formlar Pro daveti|ProInvitation|Kullanıcı bir Pro deneme sürümünü etkinleştirmek için tıklar.|
|Güncelleştirilmiş form ayarı<sup>*</sup> |UpdateFormSetting|Form sahibi bir veya birden çok form ayarlarını güncelleştirir. <br><br>FormSettingName:string özelliği, güncelleştirilmiş hassas ayarların adını gösterir. NewFormSettings:string özelliği, güncelleştirilmiş ayarların adını ve yeni değerini gösterir. thankYouMessageContainsLink:boolean özelliği, güncelleştirilmiş teşekkür iletisinin bir URL bağlantısı içerdiğini gösterir.|
|Kullanıcı ayarı güncelleştirildi|UpdateUserSetting|Form sahibi bir kullanıcı ayarını güncelleştirir. <br><br>UserSettingName:string Özelliği ayarın adını ve yeni değerini gösterir|
|Listelenen formlar<sup>*</sup>|ListForms|Form sahibi form listesini görüntülüyor. <br><br>ViewType:string Özelliği, form sahibinin hangi görünüme baktığını gösterir: Tüm Formlar, Benimle Paylaşılan veya Grup Formları|
|Gönderilen yanıt|SubmitResponse|Kullanıcı bir forma yanıt gönderir. <br><br>IsInternalForm:boolean özelliği, yanıtlayanın form sahibiyle aynı kuruluş içinde olup olmadığını gösterir.|
|Herkes yanıt verebilir ayarını etkinleştirdi<sup>*</sup>|AllowAnonymousResponse|Form sahibi, herhangi birinin forma yanıt vermesini sağlayan ayarı açar.|
|Devre dışı bırakılan herkes yanıt verebilir ayarı<sup>*</sup>|DisallowAnonymousResponse|Form sahibi ayarı kapatarak herhangi birinin forma yanıt vermesini sağlar.|
|Etkin belirli kişiler yanıt verebilir ayarı<sup>*</sup>|EnableSpecificResponse|Form sahibi ayarı açar ve yalnızca geçerli kuruluştaki belirli kişilerin veya belirli grupların forma yanıt vermesine izin verir.|
|Devre dışı bırakılan belirli kişiler yanıt verebilir ayarı<sup>*</sup>|DisableSpecificResponse|Form sahibi ayarı kapatarak yalnızca geçerli kuruluştaki belirli kişilerin veya belirli grupların forma yanıt vermesini sağlar.|
|Belirli bir yanıtlayıcı eklendi<sup>*</sup>|AddSpecificResponder|Form sahibi, belirli yanıtlayıcılar listesine yeni bir kullanıcı veya grup ekler.|
|Belirli yanıtlayıcı kaldırıldı<sup>*</sup>|RemoveSpecificResponder|Form sahibi, bir kullanıcıyı veya grubu belirli yanıtlayıcılar listesinden kaldırır.|
|Devre dışı bırakılmış işbirliği<sup>*</sup>|DisableCollaboration|Form sahibi, formda işbirliği ayarını kapatır.|
|İş veya okul hesabı işbirliği Office 365 etkinleştirildi<sup>*</sup>|EnableWorkOrSchoolCollaboration|Form sahibi, Microsoft 365 iş veya okul hesabı olan kullanıcıların formu görüntülemesine ve düzenlemesine izin veren ayarı açar.|
|Kuruluşumdaki kişilerin işbirliğine olanak sağladı<sup>*</sup>|EnableSameOrgCollaboration|Form sahibi, geçerli kuruluştaki kullanıcıların formu görüntülemesine ve düzenlemesine izin veren ayarı açar.|
|Belirli kişilerin işbirliğini etkinleştirdi<sup>*</sup>|EnableSpecificCollaboaration|Form sahibi, yalnızca geçerli kuruluştaki belirli kişilerin veya belirli grupların formu görüntülemesine ve düzenlemesine izin veren ayarı açar.|
|Excel çalışma kitabına bağlı<sup>*</sup>|ConnectToExcelWorkbook|Formu bir Excel çalışma kitabına bağladı. <br><br>ExcelWorkbookLink:string özelliği, geçerli formun ilişkili Excel çalışma kitabı kimliğini gösterir.|
|Koleksiyon oluşturma|KoleksiyonOluştur|Form sahibi bir koleksiyon oluşturdu.|
|Koleksiyon güncelleştirildi|CollectionUpdated|Form sahibi bir koleksiyon özelliğini güncelleştirdi.|
|Geri Dönüşüm Kutusu'ndan silinen koleksiyon|CollectionHardDeleted|Form sahibi Geri Dönüşüm Kutusu'ndan bir koleksiyonu sabit olarak sildi.|
|Koleksiyon Geri Dönüşüm Kutusu'na taşındı|CollectionSoftDeleted|Form sahibi bir koleksiyonu Geri Dönüşüm Kutusu'na taşıdı.|
|Koleksiyon yeniden adlandırıldı|CollectionRenamed|Form sahibi koleksiyonun adını değiştirdi.|
|Formu koleksiyona taşıma|MovedFormIntoCollection|Form sahibi formu koleksiyona taşıdı.|
|Formu koleksiyon dışına taşıma|MovedFormOutofCollection|Form sahibi formu koleksiyon dışına taşıdı.|

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Birlikte yazanlar ve anonim yanıtlayanlar tarafından gerçekleştirilen form etkinlikleri

Formlar tasarlanırken ve yanıtlar çözümlenirken formlar işbirliğini destekler. Form ortak çalışanı *ortak yazar* olarak bilinir. Birlikte yazanlar, formu silmek veya taşımak dışında form sahibinin yapabilecekleri her şeyi yapabilir. Formlar ayrıca anonim olarak yanıt verilebilen bir form oluşturmanıza da olanak tanır. Bu, yanıtlayanın bir forma yanıt verebilmek için kuruluşunuzda oturum açması gerek olmadığı anlamına gelir.

Aşağıdaki tabloda, birlikte yazanlar ve anonim yanıtlayanlar tarafından gerçekleştirilen etkinliklere ilişkin denetim etkinlikleri ve denetim kaydındaki bilgiler açıklanmaktadır.

|Etkinlik türü|İç veya dış kullanıcı|Günlüğe kaydedilen kullanıcı kimliği|Oturum açan kuruluş|Form kullanıcı türü|
|:-----|:-----|:-----|:-----|:-----|
|Ortak yazarlık etkinlikleri|Iç|UPN|Form sahibinin kuruluşu|Birlikte yazma|
|Ortak yazarlık etkinlikleri|Dış|UPN<br>|Coauthor'ın kuruluşu<br>|Birlikte yazma|
|Ortak yazarlık etkinlikleri|Dış|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(Kimliğin ikinci bölümü, farklı kullanıcılar için farklı olacak bir karmadır)|Form sahibinin kuruluşu<br>|Birlikte yazma|
|Yanıt etkinlikleri|Dış|UPN<br>|Yanıtlayıcının kuruluşu<br>|Yanıtlayıcı|
|Yanıt etkinlikleri|Dış|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(Kullanıcı Kimliğinin ikinci bölümü, farklı kullanıcılar için farklı olacak bir karmadır)|Form sahibinin kuruluşu|Yanıtlayıcı|
|Yanıt etkinlikleri|Anonim|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(Kullanıcı Kimliğinin ikinci bölümü, farklı kullanıcılar için farklı olacak bir karmadır)|Form sahibinin kuruluşu|Yanıtlayıcı|

### <a name="sensitivity-label-activities"></a>Duyarlılık etiketi etkinlikleri

Aşağıdaki tabloda [duyarlılık etiketlerinin](sensitivity-labels.md) kullanılmasından kaynaklanan olaylar listelenir.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
|Siteye duyarlılık etiketi uygulandı|SensitivityLabelApplied|bir SharePoint veya Teams sitesine duyarlılık etiketi uygulandı.|
|Duyarlılık etiketi siteden kaldırıldı|SensitivityLabelRemoved|Bir SharePoint veya Teams sitesinden duyarlılık etiketi kaldırıldı.|
|Dosyaya duyarlılık etiketi uygulandı|FileSensitivityLabelApplied|Microsoft 365 uygulamaları Web üzerinde Office kullanılarak belgeye duyarlılık etiketi uygulandı. veya otomatik etiketleme ilkesi.|
|Dosyaya uygulanan duyarlılık etiketi değiştirildi|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|Belgeye farklı bir duyarlılık etiketi uygulandı. <br /><br>Bu etkinliğin işlemleri, etiketin nasıl değiştirildiğine bağlı olarak farklıdır:<br /> - Web üzerinde Office veya otomatik etiketleme ilkesi (FileSensitivityLabelChanged) <br /> - Microsoft 365 uygulamaları (SensitivityLabelUpdated)|
|Sitede duyarlılık etiketi değiştirildi|SensitivityLabelChanged|bir SharePoint veya Teams sitesine farklı bir duyarlılık etiketi uygulandı.|
|Dosyadan duyarlılık etiketi kaldırıldı|FileSensitivityLabelRemoved|Microsoft 365 uygulamaları, Web üzerinde Office, otomatik etiketleme ilkesi veya [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'i kullanılarak belgeden duyarlılık etiketi kaldırıldı.|

### <a name="retention-policy-and-retention-label-activities"></a>Bekletme ilkesi ve bekletme etiketi etkinlikleri

Aşağıdaki tabloda [, bekletme ilkeleri ve bekletme etiketleri](retention.md) oluşturulduğunda, yeniden yapılandırıldığında veya silindiğinde yapılandırmasını açıklar.

|Kolay ad|Işlem|Açıklama|
|:-----|:-----|:-----|
| Uyarlamalı kapsam üyeliği değiştirildi |ApplicableAdaptiveScopeChange |Kullanıcılar, siteler veya gruplar uyarlamalı kapsama eklendi veya bu kapsamdan kaldırıldı. Bu değişiklikler, kapsamın sorgusunu çalıştırmanın sonuçlarıdır. Değişiklikler sistem tarafından başlatıldığından, bildirilen kullanıcı kullanıcı hesabı yerine GUID olarak görüntülenir.|
| Bekletme ilkesi için yapılandırılmış ayarlar |NewRetentionComplianceRule |Yönetici, yeni bir bekletme ilkesi için bekletme ayarlarını yapılandırdı. Bekletme ayarları, öğelerin ne kadar süreyle tutulacaklarını ve bekletme süresi dolduğunda öğelere ne olacağını (öğeleri silme, öğeleri saklama veya saklama ve sonra silme gibi) içerir. Bu etkinlik, [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) cmdlet'ini çalıştırmaya da karşılık gelir.|
| Uyarlamalı kapsam oluşturuldu |NewAdaptiveScope |Yönetici uyarlamalı bir kapsam oluşturdu.|
| Bekletme etiketi oluşturuldu |NewComplianceTag |Yönetici yeni bir bekletme etiketi oluşturdu.|
| Bekletme ilkesi oluşturuldu |NewRetentionCompliancePolicy|Yönetici yeni bir bekletme ilkesi oluşturdu.|
| Uyarlamalı kapsam silindi | RemoveAdaptiveScope| Yönetici uyarlamalı bir kapsamı sildi.|
| Bekletme ilkesinden silinen ayarlar| RemoveRetentionComplianceRule<br/>| Yönetici bir bekletme ilkesinin yapılandırma ayarlarını sildi. Büyük olasılıkla, bir yönetici bir bekletme ilkesini sildiğinde veya [Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule) cmdlet'ini çalıştırdığında bu etkinlik günlüğe kaydedilir.|
| Silinen bekletme etiketi |RemoveComplianceTag | Yönetici bir bekletme etiketini sildi.|
| Bekletme ilkesi silindi |RemoveRetentionCompliancePolicy<br/> |Yönetici bir bekletme ilkesini sildi. |
| Bekletme etiketleri için düzenleme kaydı seçeneği etkinleştirildi<br/> |SetRestrictiveRetentionUI |Yönetici [Set-RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) cmdlet'ini çalıştırarak bir yöneticinin içeriği düzenleyici kayıt olarak işaretlemek üzere bekletme etiketi için kullanıcı arabirimi yapılandırma seçeneğini belirleyebilmesini sağlar.|
| Uyarlamalı kapsam güncelleştirildi | SetAdaptiveScope | Yönetici, mevcut uyarlamalı kapsamın açıklamasını veya sorgusunu değiştirdi. |
| Bekletme ilkesi için güncelleştirilmiş ayarlar | SetRetentionComplianceRule | Yönetici, mevcut bir bekletme ilkesinin bekletme ayarlarını değiştirdi. Bekletme ayarları, öğelerin ne kadar süreyle tutulacaklarını ve bekletme süresi dolduğunda öğelere ne olacağını (öğeleri silme, öğeleri saklama veya saklama ve sonra silme gibi) içerir. Bu etkinlik, [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) cmdlet'ini çalıştırmaya da karşılık gelir. |
| Bekletme etiketi güncelleştirildi |SetComplianceTag  | Yönetici mevcut bir bekletme etiketini güncelleştirdi.|
| Bekletme ilkesi güncelleştirildi |SetRetentionCompliancePolicy |Yönetici mevcut bir bekletme ilkesini güncelleştirdi. Bu olayı tetikleyen güncelleştirmeler, bekletme ilkesinin uygulandığı içerik konumlarını eklemeyi veya dışlamayı içerir.|

### <a name="briefing-email-activities"></a>E-posta etkinliklerini bilgilendirme

Aşağıdaki tabloda, Microsoft 365 denetim günlüğüne kaydedilen Brifing e-postası etkinlikleri listelenir. Brifing e-postası hakkında daha fazla bilgi için bkz:

- [Brifing e-postaya genel bakış](/Briefing/be-overview)

- [Brifing e-postasını yapılandırma](/Briefing/be-admin)

|**Kolay ad**|**Işlem**|**Açıklama**|
|:----|:-----|:-----|
|Kuruluş gizlilik ayarları güncelleştirildi|UpdatedOrganizationBriefingSettings|Yönetici, Brifing e-postası için kuruluşun gizlilik ayarlarını güncelleştirir. |
|Güncelleştirilmiş kullanıcı gizlilik ayarları|UpdatedUserBriefingSettings|Yönetici, Brifing e-postası için kullanıcı gizlilik ayarlarını güncelleştirir.

### <a name="myanalytics-activities"></a>MyAnalytics etkinlikleri

Aşağıdaki tabloda, myAnalytics'teki Microsoft 365 denetim günlüğüne kaydedilen etkinlikler listelenir. MyAnalytics hakkında daha fazla bilgi için bkz. [Yöneticiler için MyAnalytics](/workplace-analytics/myanalytics/overview/mya-for-admins).

|**Kolay ad**|**Işlem**|**Açıklama**|
|:-----|:-----|:-----|
|Kuruluş MyAnalytics ayarları güncelleştirildi|UpdatedOrganizationMyAnalyticsSettings|Yönetici MyAnalytics için kuruluş düzeyi ayarlarını güncelleştirir. |
|Kullanıcı MyAnalytics ayarları güncelleştirildi|UpdatedUserMyAnalyticsSettings|Yönetici MyAnalytics için kullanıcı ayarlarını güncelleştirir.|

### <a name="information-barriers-activities"></a>Bilgi engelleri etkinlikleri

Aşağıdaki tabloda, Microsoft 365 denetim günlüğüne kaydedilen bilgi engellerindeki etkinlikler listelenir. Bilgi engelleri hakkında daha fazla bilgi için bkz. [Microsoft 365 bilgi engelleri hakkında bilgi edinin](information-barriers.md).

|**Kolay ad**|**Işlem**|**Açıklama**|
|:----------------|:------------|:--------------|
| Siteye segmentler eklendi | SegmentlerEkli | bir SharePoint, genel yönetici veya site sahibi siteye bir veya daha fazla bilgi engeli ekledi. |
| Sitenin segmentleri değiştirildi | SegmentlerDeğiştirildi | SharePoint veya genel yönetici, sitenin bir veya daha fazla bilgi engelini değiştirdi. |
| Bir siteden segmentler kaldırıldı | SegmentlerRemoved | SharePoint veya genel yönetici, siteden bir veya daha fazla bilgi engeli segmentini kaldırdı. |

### <a name="disposition-review-activities"></a>Gözden geçirme etkinliklerini değerlendirme

Aşağıdaki tabloda, bir öğe yapılandırılan saklama süresinin sonuna ulaştığında gözden geçirenin yaptığı etkinlikler listelenir. Daha fazla bilgi için bkz [. İçeriği görüntüleme ve yok etme](disposition.md#viewing-and-disposing-of-content).

|**Kolay ad**|**Işlem**|**Açıklama**|
|:-----|:-----|:-----|
|Onaylanan elden çıkarma|ApproveDisposal|Bir değerlendirme gözden geçireni, öğenin bir sonraki değerlendirme aşamasına taşımak için elden geçirmesini onayladı. Öğe, değerlendirme gözden geçirmesinin tek veya son aşamasındaysa, değerlendirme onayı öğeyi kalıcı silme için uygun olarak işaretledi.|
|Genişletilmiş saklama süresi|ExtendRetention|Değerlendirme gözden geçiren, öğenin saklama süresini uzattı.|
|Yeniden etiketlenmiş öğe|RelabelItem|Bir değerlendirme gözden geçireni bekletme etiketini yeniden etiketledi.|
|Gözden geçirenler eklendi|AddReviewer|Bir değerlendirme gözden geçireni, geçerli değerlendirme gözden geçirme aşamasına bir veya daha fazla kullanıcı ekledi.|

### <a name="communication-compliance-activities"></a>İletişim uyumluluk etkinlikleri

Aşağıdaki tabloda, Microsoft 365 denetim günlüğüne kaydedilen iletişim uyumluluk etkinlikleri listelenir. Daha fazla bilgi için bkz. [Microsoft 365'de iletişim uyumluluğu hakkında bilgi edinin](communication-compliance.md).

|**Kolay ad**|**Işlem**|**Açıklama**|
|:-----|:-----|:-----|
|İlke güncelleştirmesi|SupervisionPolicyCreated, SupervisionPolicyUpdated, SupervisionPolicyDeleted|İletişim uyumluluk yöneticisi bir ilke güncelleştirmesi gerçekleştirmiştir.|
|İlke eşleşmesi|SupervisionRuleMatch|Kullanıcı bir ilkenin koşuluyla eşleşen bir ileti gönderdi.|
|İletilere uygulanan etiket|SupervisoryReviewTag|etiketler iletilere uygulanır veya iletiler çözümlenir.|

### <a name="report-activities"></a>Rapor etkinlikleri

Aşağıdaki tabloda, Microsoft 365 denetim günlüğüne kaydedilen kullanım raporlarına yönelik etkinlikler listelenir.

|**Kolay ad**|**Işlem**|**Açıklama**|
|:-----|:-----|:-----|
|Kullanım raporu gizlilik ayarları güncelleştirildi|UpdateUsageReportsPrivacySetting|Yönetici kullanım raporları için güncelleştirilmiş gizlilik ayarları. |

### <a name="exchange-admin-audit-log"></a>yönetici denetim günlüğünü Exchange

Exchange yönetici denetim günlüğü (Microsoft 365 varsayılan olarak etkindir) bir yönetici (veya yönetici izinleri atanmış bir kullanıcı) Exchange Online kuruluşunuzda değişiklik yaptığında denetim günlüğüne bir olay kaydeder. Exchange yönetim merkezi kullanılarak veya Exchange Online PowerShell'de bir cmdlet çalıştırılarak yapılan değişiklikler Exchange yönetici denetim günlüğüne kaydedilir. **Get-**, **Search** veya **Test** fiilleriyle başlayan cmdlet'ler denetim günlüğüne kaydedilmez. Exchange yönetici denetim günlüğü hakkında daha ayrıntılı bilgi için bkz. [Yönetici denetim günlüğü](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Exchange yönetici denetim günlüğüne (veya denetim günlüğüne) kaydedilmemiş bazı Exchange Online cmdlet'leri. Bu cmdlet'lerin çoğu Exchange Online hizmetinin bakımıyla ilgilidir ve Microsoft veri merkezi personeli veya hizmet hesapları tarafından çalıştırılır. Bu cmdlet'ler çok sayıda "gürültülü" denetim olayına neden olacağından günlüğe kaydedilmez. Denetlenmeyen bir Exchange Online cmdlet'i varsa, lütfen Microsoft Desteği bir tasarım değişikliği isteği (DCR) gönderin.

Denetim günlüğünde arama yaparken Exchange yönetici etkinliklerini aramak için bazı ipuçları şunlardır:

- Exchange yönetici denetim günlüğündeki girdileri döndürmek için **Etkinlikler** listesindeki **Tüm etkinlikler için sonuçları göster'i** seçmeniz gerekir. Belirli bir tarih aralığında belirli bir Exchange yöneticisi tarafından çalıştırılan cmdlet'lerin arama sonuçlarını daraltmak için tarih aralığı kutularını ve **Kullanıcılar** listesini kullanın.

- Exchange yönetici denetim günlüğündeki olayları görüntülemek için, cmdlet adlarını alfabetik sırada sıralamak için **Etkinlik** sütununa tıklayın.

- Hangi cmdlet'in çalıştırıldığı, hangi parametrelerin ve parametre değerlerinin kullanıldığı ve hangi nesnelerin etkilendiği hakkında bilgi almak için **Tüm sonuçları indir** seçeneğini belirleyerek arama sonuçlarını dışarı aktarabilirsiniz. Daha fazla bilgi için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

- Exchange yönetici denetim günlüğünden yalnızca denetim kayıtlarını döndürmek için PowerShell'Exchange Online komutunu da kullanabilirsiniz`Search-UnifiedAuditLog -RecordType ExchangeAdmin`. İlgili denetim günlüğü girişinin arama sonuçlarında döndürülürken bir Exchange cmdlet'inin çalıştırılması 30 dakika kadar sürebilir. Daha fazla bilgi için bkz [. Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). **Search-UnifiedAuditLog** cmdlet'i tarafından döndürülen arama sonuçlarını csv dosyasına dışarı aktarma hakkında bilgi için, Denetim [günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log) bölümündeki "Denetim günlüğünü dışarı aktarma ve görüntüleme İpuçları" bölümüne bakın.

- Ayrıca, Exchange yönetim merkezini kullanarak veya Exchange Online PowerShell'de **Search-AdminAuditLog** komutunu çalıştırarak olayları Exchange yönetici denetim günlüğünde görüntüleyebilirsiniz. Bu, Exchange Online yöneticileri tarafından gerçekleştirilen etkinliği özel olarak aramanın iyi bir yoludur. Yönergeler için bkz:

  - [Yönetici denetim günlüğünü görüntüleme](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Aynı Exchange yönetici etkinliklerinin hem Exchange yönetici denetim günlüğüne hem de denetim günlüğüne kaydedildiğini unutmayın.

### <a name="encrypted-message-portal-activities"></a>Şifrelenmiş ileti portalı etkinlikleri

Erişim günlükleri, kuruluşunuzun iletilerin ne zaman okunduğunu ve dış alıcılarınız tarafından iletileceğini belirlemesini sağlayan şifrelenmiş ileti portalı aracılığıyla şifrelenmiş iletiler için kullanılabilir. Şifrelenmiş ileti portalı etkinlik günlüklerini etkinleştirme ve kullanma hakkında daha fazla bilgi için bkz [. Şifrelenmiş ileti portalı etkinlik günlüğü](ome-message-access-logs.md).

İzlenen ileti için her denetim girdisi aşağıdaki alanları içerir:

- MessageID - İzlenen iletinin kimliğini içerir. Bu, sistem üzerinden bir iletiyi izlemek için kullanılan anahtar tanımlayıcıdır.
- Alıcı - Tüm alıcı e-posta adreslerinin listesi.
- Gönderen - Kaynak e-posta adresi.
- AuthenticationMethod - İletiye erişmek için OTP, Yahoo, Gmail veya Microsoft gibi kimlik doğrulama yöntemini açıklar.
- AuthenticationStatus - Kimlik doğrulamasının başarılı veya başarısız olduğunu belirten bir değer içerir.
- OperationStatus - Belirtilen işlemin başarılı mı yoksa başarısız mı olduğunu gösterir.
- AttachmentName - Ekin adı.
- OperationProperties - gönderilen OTP geçiş kodu sayısı veya e-posta konusu gibi isteğe bağlı özelliklerin listesi.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Şu anda denetlenen farklı Microsoft 365 hizmetleri nelerdir?**

Exchange Online, SharePoint Online, OneDrive İş, Azure Active Directory, Microsoft Teams, Dynamics 365, Office 365 için Defender, ve Power BI denetleniyor. Denetlenen hizmetlerin listesi için [bu makalenin başlangıcına](search-the-audit-log-in-security-and-compliance.md) bakın.

**Microsoft 365'da hangi etkinlikler denetim hizmeti tarafından denetlenir?**

[Denetlenen etkinliklerin](#audited-activities) listesi ve açıklaması için bu makaledeki Denetlenen etkinlikler bölümüne bakın.

**Bir olay gerçekleştikten sonra denetim kaydının kullanılabilir olması ne kadar sürer?**

Denetim verilerinin çoğu 30 dakika içinde kullanılabilir ancak ilgili denetim günlüğü girişinin arama sonuçlarında görüntülenmesi bir olay gerçekleştikten sonra 24 saat kadar sürebilir. Bu makalenin [Denetim günlüğünde arama yapmadan önce](#before-you-search-the-audit-log) bölümünde yer alan ve farklı hizmetlerdeki olayların kullanılabilir olması için gereken süreyi gösteren tabloya bakın.

**Denetim kayıtları ne kadar süreyle saklanır?**

Daha önce açıklandığı gibi, Office 365 E5 veya Microsoft E5 lisansına (veya Microsoft 365 E5 eklenti lisansına sahip kullanıcılara) atanan kullanıcılar tarafından gerçekleştirilen etkinliklerin denetim kayıtları bir yıl boyunca saklanır. Birleşik denetim günlüğünü destekleyen diğer tüm abonelikler için denetim kayıtları 90 gün boyunca saklanır.

**Denetim verilerine program aracılığıyla erişebilir miyim?**

Evet. Office 365 Yönetim Etkinliği API'si, denetim günlüklerini program aracılığıyla getirmek için kullanılır.  Başlamak için bkz. [Office 365 Yönetim API'leriyle Kullanmaya başlayın](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Güvenlik ve uyumluluk portalını veya Office 365 Yönetim Etkinliği API'sini kullanmak dışında denetim günlüklerini almanın başka yolları var mı?**

Evet, aşağıdaki yöntemleri kullanarak denetim günlüklerini alabilirsiniz:

- [Office 365 Yönetim Etkinliği API'si](/office/office-365-management-api/office-365-management-activity-api-reference).

- Microsoft Purview uyumluluk portalı [denetim günlüğü arama aracı](search-the-audit-log-in-security-and-compliance.md).

- Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'i.

**Denetim günlüklerini yakalamak istediğim her hizmette denetimi tek tek etkinleştirmem gerekiyor mu?**

Çoğu hizmette, kuruluşunuz için denetimi ilk kez açtıktan sonra denetim varsayılan olarak etkinleştirilir (bu [makalenin Denetim günlüğünde arama yapmadan önce](#before-you-search-the-audit-log) bölümünde açıklandığı gibi).

**Denetim hizmeti kayıtların yinelenenleri kaldırmayı destekliyor mu?**

Hayır. Denetim hizmeti işlem hattı neredeyse gerçek zamanlıdır ve bu nedenle yinelenenleri kaldırmayı destekleyemez.

**Denetim verileri nerede depolanır?**

Şu anda NA (Kuzey Amerika), EMEA (Avrupa, Orta Doğu ve Afrika) ve APAC (Asya Pasifik) bölgelerinde denetim işlem hattı dağıtımlarımız var. Bu bölgelerde barındırılan kiracıların denetim verileri bölgede depolanır. Çok coğrafi kiracılı kiracılar için, kiracının tüm bölgelerinden toplanan denetim verileri yalnızca kiracının ana bölgesinde depolanır. Ancak, verileri yük dengeleme için ve yalnızca canlı site sorunları sırasında bu bölgelere akabiliriz. Bu etkinlikleri gerçekleştirdiğimizde aktarımdaki veriler şifrelenir. 

**Denetim verileri şifrelenir mi?**

Denetim verileri, birleşik denetim işlem hattının dağıtıldığı bölgedeki Exchange posta kutularında (bekleyen veriler) depolanır. Bekleyen posta kutusu verileri Exchange tarafından şifrelenmez. Ancak Microsoft veri merkezlerindeki Exchange sunucular BitLocker aracılığıyla şifrelenmediğinden hizmet düzeyinde şifreleme tüm posta kutusu verilerini şifreler. Daha fazla bilgi için bkz[. Skype Kurumsal, OneDrive İş, SharePoint Online ve Exchange Online için Microsoft 365 Şifreleme](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Aktarımdaki posta verileri her zaman şifrelenir.
