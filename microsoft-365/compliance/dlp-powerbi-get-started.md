---
title: Power BI için DLP kullanmaya başlama
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
description: DLP için hazırlanma ve PowerBI konumlarına dağıtma.
ms.openlocfilehash: f831d42898e491258a53423c1d59b9f50c0b289d
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66616940"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>Power BI için Veri kaybını önleme ilkelerini kullanmaya başlama (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşların hassas verilerini algılamalarına ve korumalarına yardımcı olmak için [Microsoft Purview veri kaybı önleme (DLP) ilkeleri](/microsoft-365/compliance/dlp-learn-about-dlp) Power BI'ı destekler. Bir PowerBI veri kümesi bir DLP ilkesindeki ölçütle eşleştiğinde, hassas içeriğin doğasını açıklayan bir uyarı tetiklenebilir. Bu uyarı, yöneticiler tarafından izlenmesi ve yönetilmesi için Microsoft uyumluluk portalındaki veri kaybı önleme **Uyarıları** sekmesine de kaydedilir. Ayrıca, yöneticilere ve belirtilen kullanıcılara e-posta uyarıları gönderilebilir.

## <a name="considerations-and-limitations"></a>Dikkat edilmesi gerekenler ve sınırlamalar

- DLP ilkeleri çalışma alanları için geçerlidir. Yalnızca Premium 2. Nesil kapasitelerinde barındırılan çalışma alanları desteklenir. Daha fazla bilgi için bkz. [Power BI Premium 2. Nesil nedir?](/power-bi/enterprise/service-premium-gen2-what-is).
- DLP veri kümesi değerlendirme iş yükleri kapasiteyi etkiler. DLP değerlendirme iş yükleri için ölçüm desteklenmez.
- Hem klasik hem de yeni deneyim çalışma alanları, Premium 2. Nesil kapasitelerinde barındırılıyorsa desteklenir.
- Power BI için özel bir DLP özel ilkesi oluşturmanız gerekir. DLP şablonları desteklenmez.
- DLP konumuna uygulanan DLP ilkeleri, duyarlılık etiketlerini ve hassas bilgi türlerini koşul olarak destekler. 
- Power BI için DLP ilkeleri, [DirectQuery](/power-bi/connect-data/desktop-use-directquery) veya [canlı bağlantı](/power-bi/connect-data/desktop-directquery-about#live-connections) aracılığıyla veri kaynaklarına bağlanan örnek veri kümeleri, [akış veri kümeleri](/power-bi/connect-data/service-real-time-streaming) veya veri kümeleri için desteklenmez.
- Power BI için DLP ilkeleri bağımsız bulutlarda desteklenmez.

## <a name="licensing-and-permissions"></a>Lisanslama ve izinler

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

Power BI için DLP'yi kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) onaylamanız gerekir. Tam lisanslama yönergeleri için bkz. [Güvenlik & uyumluluğu için Microsoft 365 kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>İzinler

Power BI için DLP verileri [Etkinlik gezgininde](/microsoft-365/compliance/data-classification-activity-explorer) görüntülenebilir. Etkinlik gezginine izin veren dört rol vardır; verilere erişmek için kullandığınız hesap bunlardan herhangi birinin üyesi olmalıdır.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

## <a name="how-dlp-policies-for-power-bi-work"></a>Power BI için DLP ilkeleri nasıl çalışır?

Uyumluluk portalının veri kaybı önleme bölümünde bir DLP ilkesi tanımlarsınız. Bkz. [Veri kaybı önleme ilkesi tasarlama](dlp-policy-design.md#design-a-data-loss-prevention-policy). İlkede, algılamak istediğiniz duyarlılık etiketlerini belirtirsiniz. Ayrıca, ilke belirtilen duyarlılık etiketi uygulanmış bir veri kümesi algıladığında gerçekleşecek eylemleri de belirtirsiniz. DLP ilkeleri Power BI için iki eylemi destekler:

- İlke ipuçları aracılığıyla kullanıcı bildirimi.
- Uyarı. Uyarılar, yöneticilere ve kullanıcılara e-posta ile gönderilebilir. Ayrıca, yöneticiler uyumluluk merkezindeki **Uyarılar** sekmesinde uyarıları izleyebilir ve yönetebilir. 

Bir veri kümesi DLP tarafından değerlendirildiğinde ve bir DLP ilkesindeki koşullarla eşleştiğinde, ilkede tanımlanan eylemler uygulanır. Bir veri kümesi aşağıdaki durumlarda değerlendirilir:

- Yayımlamak
- Yeniden Yayımla
- İsteğe bağlı yenileme
- Zamanlanmış yenileme

>[!NOTE]
> Aşağıdakilerden biri doğruysa veri kümesinin DLP değerlendirmesi gerçekleşmez:
> - Olayın başlatıcısı bir hizmet sorumlusudur.
> - Veri kümesi sahibi bir hizmet sorumlusu veya B2B kullanıcısıdır.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>Veri kümesi DLP ilkesiyle eşleştiğinde ne olur?

Bir veri kümesi DLP ilkesiyle eşleştiğinde:

- İlkenin yapılandırılmış kullanıcı bildirimi varsa, Power BI hizmeti bir DLP ilkesiyle eşleşeceğini belirtmek için bir kalkan simgesiyle işaretlenir.

    ![Listelerdeki veri kümesinde ilke ipucu rozetinin ekran görüntüsü.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    İlke eşleşmesini ve algılanan hassas bilgi türünün nasıl işlenmesi gerektiğini açıklayan bir ilke ipucu görmek için veri kümesi ayrıntıları sayfasını açın.

    ![Veri kümesi ayrıntıları sayfasındaki ilke ipucunun ekran görüntüsü.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > İlke ipucunu gizlerseniz silinmez. Sayfayı bir sonraki ziyaret ışınızda görüntülenir.

- İlkede uyarılar etkinleştirilirse, uyumluluk merkezindeki dlp **Uyarıları** sekmesine bir uyarı kaydedilir ve (yapılandırıldıysa) yöneticilere ve/veya belirtilen kullanıcılara bir e-posta gönderilir. Aşağıdaki görüntüde, Microsoft Purview uyumluluk portalı veri kaybı önleme bölümündeki **Uyarılar** sekmesi gösterilmektedir.

    ![Uyumluluk merkezindeki Uyarılar sekmesinin ekran görüntüsü.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>Power BI için DLP ilkesi yapılandırma

[DLP ilkesi oluşturma, test edin ve ayarlayın ve](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) özel şablonu kullanın.

> [!IMPORTANT]
> Power BI için DLP ilkenizin konumlarını seçtiğinizde yalnızca Power BI konumunu seçin. Başka bir konum seçmeyin, bu yapılandırma desteklenmez. 

<!--1. Log into the [Microsoft Purview compliance portal](https://compliance.microsoft.com).

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

Log into the Microsoft Purview compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>Sonraki adımlar

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](/microsoft-365/compliance/dlp-learn-about-dlp)
- [Power BI'da duyarlılık etiketleri](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [Power BI'da duyarlılık etiketleri için şemayı denetleme](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)
