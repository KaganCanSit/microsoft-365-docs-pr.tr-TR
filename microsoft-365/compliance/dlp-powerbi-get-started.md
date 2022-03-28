---
title: Veriler için veri kaybı önlemeyi Power BI
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: DLP'yi PowerBI konumlarına hazırlama ve dağıtma.
ms.openlocfilehash: a1ea5321b77db1b4e7741f4d41cdd485adbd0b97
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717350"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>Yeni yönetim (önizleme) için Veri kaybı önleme Power BI ilkeleriyle çalışmaya başlama

Kuruluşların hassas verilerini algılamalarına ve korumalarına yardımcı olmak için veri [Microsoft 365 önleme (DLP) güvenlik güvenliklerini](/microsoft-365/compliance/dlp-learn-about-dlp) desteklemesini Power BI. PowerBI veri kümesi DLP ilkesinde yer alan ölçütle eşlendiğinde, hassas içeriğin doğasını açıklayan bir uyarı tetiklenir. Bu uyarı, yöneticiler tarafından izlenmesi ve yönetimi için Microsoft  uyumluluk portalında yer alan veri kaybı önleme Uyarılar sekmesine de kaydedilir. Ayrıca yöneticilere ve belirli kullanıcılara e-posta uyarıları gönderilebilir.

## <a name="considerations-and-limitations"></a>Dikkate alınacak noktalar ve sınırlamalar

- DLP ilkeleri çalışma alanları için geçerlidir. Yalnızca Nesil2'nin Premium alanında barındırılan çalışma alanları kullanılabilir.
- DLP veri kümesi değerlendirme iş yükleri kapasiteyi etkiler. DLP değerlendirme iş yüklerinin tarifesi desteklenmiyor.
- Hem klasik hem de yeni deneyim çalışma alanları, Yeni Nesil2'de farklı bir kapasitede barındırıldıklarında Premium destek sağlar.
- Bu çalışma için özel bir DLP özel ilkesi Power BI. DLP şablonları desteklenmiyor.
- DLP konumu destek duyarlılık etiketlerine ve hassas bilgi türlerine koşullar olarak uygulanan DLP İlkeleri. 
- Power BI için DLP ilkeleri, [DirectQuery](/power-bi/connect-data/desktop-use-directquery) veya canlı bağlantı yoluyla kendi veri kaynağına bağlanan örnek veri kümelerinde[, akış](/power-bi/connect-data/service-real-time-streaming) veri kümelerinde veya veri [kümelerinde desteklanmaz](/power-bi/connect-data/desktop-directquery-about#live-connections).
- Bağımsız bulutlarda Power BI DLP ilkeleri desteklanmaz.

## <a name="licensing-and-permissions"></a>Lisans ve izinler

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Power BI için DLP'ye başlamadan önce, Microsoft 365 [onaylamanız gerekir](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Tam lisanslama kılavuzu için, güvenlik [Microsoft 365 uyumluluğu için güvenlik & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>İzinler

Etkinlik gezgininde Power BI için [DLP'den veriler ekleyebilirsiniz](/microsoft-365/compliance/data-classification-activity-explorer). Etkinlik gezginine izin veren dört rol vardır; verilere erişim için kullanıyorsanız bu hesaplardan herhangi birinin üyesi olması gerekir.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

## <a name="how-dlp-policies-for-power-bi-work"></a>Yeni iş için DLP Power BI çalışma

Uyumluluk portalının veri kaybını önleme bölümünde bir DLP ilkesi tanımlarsınız. Bkz [. Veri kaybı önleme ilkesi tasarlama](dlp-policy-design.md#design-a-data-loss-prevention-policy). İlkede, algılamak istediğiniz duyarlılık etiketlerini belirtirsiniz. Ayrıca, ilke belirtilen duyarlılık etiketinin uygulandığı bir veri kümesi algılayana kadar gerçekleşecek eylemlerini de belirtirsiniz. DLP ilkeleri bu işlemler için iki Power BI:

- İlke ipuçları aracılığıyla kullanıcı bildirimi.
- Uyarılar. Uyarılar, yöneticilere ve kullanıcılara e-postayla gönderebilirsiniz. Ayrıca yöneticiler, uyumluluk merkezinin Uyarılar sekmesindeki **uyarıları** izleyebilir ve yönetebilir. 

Bir veri kümesi DLP tarafından değerlendirilip DLP ilkesi koşullarıyla eşlenince, ilkede tanımlanan eylemler uygulanır. Veri kümesi aşağıdaki gibi olduğunda, veri kümesi değerlendirilir:

- Yayımla
- Yeniden Yayımla
- isteğe bağlı yenileme
- Zamanlanan yenileme

>[!NOTE]
> Aşağıdakilerden biri doğruysa, veri kümesi DLP değerlendirmesini gerçekleştirin:
> - Olayın başlatıcısı hizmet sorumlusudır.
> - Veri kümesi sahibi bir hizmet sorumlusu veya B2B kullanıcısıdır.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>Veri kümesi bir DLP ilkesiyle eşleni olduğunda ne olur?

Veri kümesi bir DLP ilkesiyle eş olduğunda:

- İlkenin yapılandırılmış kullanıcı bildirimi varsa, kullanıcının DLP ilkesiyle eş Power BI için görev çubuğunda kalkan simgesiyle işaretlenir.

    ![Listelerde veri kümesinde ilke ipucu rozetinin ekran görüntüsü.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    İlkenin eşleşmesi ve algılanan hassas bilgi türünün nasıl iş açılması gerektiğini açıklayan bir ilke ipucu görmek için veri kümesi ayrıntıları sayfasını açın.

    ![Veri kümesi ayrıntıları sayfasında ilke ipucu ekran görüntüsü.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > İlke ipucu gizlendiğinde silinmez. Sayfayı bir sonraki ziyaretinde görünecektir.

- İlkede uyarılar etkinse, uyumluluk merkezinin **dlp Uyarıları** sekmesine bir uyarı kaydedilir ve (yapılandırıldısa) yöneticilere ve/veya belirtilen kullanıcılara bir e-posta gönderilir. Aşağıdaki resimde, uyumluluk **merkezinin** veri kaybı önleme bölümündeki Uyarılar sekmesi görüntülenir.

    ![Uyumluluk merkezinde Uyarılar sekmesinin ekran görüntüsü.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>DLP ilkesi yapılandırma Power BI

DLP ilkesi oluşturma [, test etme ve ayarlama'daki yordamları izleyin ve](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) özel şablonu kullanın.

> [!IMPORTANT]
> İlke için DLP ilkenizin konumlarını Power BI, yalnızca dış Power BI seçin. Başka konum seçme, bu yapılandırma desteklenmiyor. 

<!--1. Log into the [Microsoft 365 compliance portal](https://compliance.microsoft.com).

1. Choose the **Data loss prevention** solution in the navigation pane, select the **Policies** tab, choose **Create policy**.

    ![Screenshot of D L P create policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create.png)

1. Choose the **Custom** category and then the **Custom policy** template.
    
    >[!NOTE]
    >No other categories or templates are currently supported.

    ![Screenshot of D L P choose custom policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-custom.png)
 
    When done, click **Next**.

1. Name the policy and provide a meaningful description.

    ![Screenshot of D L P policy name description section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-name-description.png)
 
    When done, click **Next**.

1. Enable Power BI as a location for the DLP policy. **Disable all other locations**. Currently, DLP policies for Power BI must specify Power BI as the sole location.

    ![Screenshot of D L P choose location page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-location.png)

    By default the policy will apply to all workspaces. Alternatively, you can specify particular workspaces to include in the policy as well as workspaces to exclude from the policy.
    >[!NOTE]
    > DLP actions are supported only for workspaces hosted in Premium Gen2 capacities.

    If you select **Choose workspaces** or **Exclude workspaces**, a dialog will allow you to create a list of included (or excluded) workspaces. You must specify workspaces by workspace object ID. Click the info icon for information about how to find workspace object IDs.

    ![Screenshot of D L P choose workspaces dialog.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-workspaces.png)
 
    After enabling Power BI as a DLP location for the policy and choosing which workspaces the policy will apply to, click **Next**.

1. The **Define policy settings** page appears. Choose **Create or customize advanced DLP rules** to begin defining your policy.

    ![Screenshot of D L P create advanced rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-advanced-rule.png)
 
    When done, click **Next**.

1. On the **Customize advanced DLP rules** page, you can either start creating a new rule or choose an existing rule to edit. Click **Create rule**.

    ![Screenshot of D L P create rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule.png)


1. The **Create rule** page appears. On the create rule page, provide a name and description for the rule, and then configure the other sections, which are described following the image below.

    ![Screenshot of D L P create rule form.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule-form.png)
 
### Conditions

In the condition section, you define the conditions under which the policy will apply to a dataset. Conditions are created in groups. Groups make it possible to construct complex conditions.

1. Open the conditions section, choose **Add condition** and then **Content contains**.

    ![Screenshot of D L P add conditions content contains section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions-content-contains.png)
 
    This opens the first group (named Default – you can change this).

1. Choose **Add**, and then **Sensitivity labels**.
        
    >[!NOTE]
    > Sensitive info types are currently not supported.
    
    ![Screenshot of D L P add conditions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions.png)
 
    When you choose **Sensitivity labels**, you will be able to choose a particular sensitivity label from a list that will appear.

    You can add additional sensitivity labels to the group. To the right of the group name, you can specify **Any of these** or **All of these**. This determines whether matches on all or any of the labels is required for the condition to hold. Make sure **Any of these** is selected, since datasets can’t have more than one label applied.

    The image below shows a group (Default) that contains two sensitivity label conditions. The logic Any of these means that a match on any one of the sensitivity labels in the group constitutes “true” for that group.

    ![Screenshot of D L P conditions group section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-condition-group.png) 
 
    You can create more than one group, and you can control the logic between the groups with **AND** or **OR** logic. 

    The image below shows a rule containing two groups, joined by **OR** logic.

    ![Screenshot of rule with two groups.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-content-contains.png) 
 
### Exceptions

If the sensitivity label of the dataset matches any of the defined exceptions, the rule won’t be applied to the dataset. 

Exceptions are configured in the same way as conditions, described above.
    
![Screenshot of D L P exceptions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-exceptions-section.png)
 
### Actions

Protection actions are currently unavailable for Power BI DLP policies.

![Screenshot of D L P policy actions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-actions-section.png)


### User notifications

The user notifications section is where you configure your policy tip. Turn on the toggle, select the **Notify users in Office 365 service with a policy tip** and **Policy tips** checkboxes, and write your policy tip in the text box.

![Screenshot of D L P user notification section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-notification.png)
 
### User overrides
 
User overrides are currently unavailable for Power BI DLP policies.

![Screenshot of D L P user overrides section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-overrides-section.png) 
 
### Incident reports

Assign a severity level that will be shown in alerts generated from this policy. Enable (default) or disable email notification to admins, specify users or groups for email notification, and configure the details about when notification will occur.

![Screenshot of D L P incident report section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-incidence-report.png)
   
### Additional options

![Screenshot of D L P additional options section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-additional-options.png)
 
## Monitor and manage policy alerts

Log into the Microsoft 365 compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>Sonraki adımlar

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](/microsoft-365/compliance/dlp-learn-about-dlp)
- [Power BI'de duyarlılık etiketleri](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [Denetim şeması için duyarlılık etiketleri Power BI](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)