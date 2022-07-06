---
title: SIEM çözümleri ile iletişim uyumluluğu
description: SIEM çözümleriyle iletişim uyumluluğu tümleştirmesi hakkında bilgi edinin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, iletişim uyumluluğu
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 4d9ee561e033e98919063d1f344aa3207a6bb6cd
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626545"
---
# <a name="communication-compliance-with-siem-solutions"></a>SIEM çözümleri ile iletişim uyumluluğu

[İletişim uyumluluğu](communication-compliance.md) , Microsoft Purview'da kuruluşunuzdaki uygunsuz iletileri algılamanıza, yakalamanıza ve üzerinde işlem yapmanıza yardımcı olarak iletişim risklerini en aza indirmeye yardımcı olan bir iç risk çözümüdür. [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) veya [Splunk](https://www.splunk.com/) gibi güvenlik bilgileri ve olay yönetimi (SIEM) çözümleri genellikle kuruluş içindeki tehditleri toplamak ve izlemek için kullanılır.

Kuruluşların yaygın ihtiyaçlarından biri, iletişim uyumluluk uyarılarını ve bu SIEM çözümlerini tümleştirmektir. Bu tümleştirme sayesinde kuruluşlar, iletişim uyumluluk uyarılarını SIEM çözümlerinde görüntüleyebilir ve ardından iletişim uyumluluğu iş akışı ve kullanıcı deneyimi içindeki uyarıları düzeltebilir. Örneğin, bir çalışan başka bir çalışana rahatsız edici bir ileti gönderir ve bu ileti uygunsuz içerik için bir iletişim uyumluluk ilkesi izlemesi tarafından algılanır. Bu olaylar, iletişim uyumluluk çözümü tarafından Microsoft 365 Denetiminde ("birleşik denetim günlüğü" olarak da bilinir) izlenir ve SIEM çözümüne aktarılır. Daha sonra, Microsoft 365 Denetimi'nde izlenen ve iletişim uyumluluk uyarılarıyla ilişkili olaylardan kuruluş için SIEM çözümünde bir uyarı tetiklenir. Araştırmacılara SIEM çözümlerinde uyarı bildirilir ve ardından iletişim uyumluluk çözümünde uyarıyı araştırır ve düzelterler.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Microsoft 365 Denetimi'nde iletişim uyumluluğu uyarıları

Tüm iletişim uyumluluk ilkesi eşleşmeleri Microsoft 365 Denetimi'nde yakalanır. Aşağıdaki örneklerde, seçili iletişim uyumluluk ilkesi eşleştirme etkinlikleri için kullanılabilen ayrıntılar gösterilir:

**Uygunsuz İçerik ilkesi şablonu eşleşmesi için denetim günlüğü girdisi örneği:**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/7/2021 5:30:11 AM
UserIds: user1@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-07T05:30:11","Id":"44e98a7e-57fd-4f89-79b8-08d941084a35","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<HE1P190MB04600526C0524C75E5750C5AC61A9@HE1P190MB0460.EURP190.PROD.OUTLOOK.COM\>","UserId":"user1@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"53be0bf4-75ee-4315-b65d-17d63bdd53ae","SRPolicyName":"Adult images","SRRuleMatchDetails":\[\]}}
ResultIndex: 24
ResultCount: 48
Identity: 44e98a7e-57fd-4f89-79b8-08d941084a35
IsValid: True
ObjectState: Unchanged
```

**Özel anahtar sözcük eşleşmesi olan bir ilke için Microsoft 365 Denetim günlüğü girdisi örneği (özel hassas bilgi türü):**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/6/2021 9:50:12 PM
UserIds: user2@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-06T21:50:12","Id":"5c61aae5-26fc-4c8e-0791-08d940c8086f","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"public\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<20210706174831.24375086.807067@sailthru.com\>","UserId":"user2@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"a97cf128-c0fc-42a1-88e3-fd3b88af9941","SRPolicyName":"Insiders","SRRuleMatchDetails":\[{"SRCategoryName":"New insiders lexicon"}\]}}
ResultIndex: 46
ResultCount: 48
Identity: 5c61aae5-26fc-4c8e-0791-08d940c8086f
IsValid: True
ObjectState: Unchanged
```

> [!NOTE]
> Şu anda, ilke eşleşmesinin Microsoft 365 Denetimi'nde kaydedildiği süre ile iletişim uyumluluğunda ilke eşleşmelerini araştırabileceğiniz süre arasında 24 saate kadar gecikme olabilir.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>İletişim uyumluluğunu ve Microsoft Sentinel tümleştirmesini yapılandırma

İletişim uyumluluk ilkesi eşleşmelerini toplamak için Microsoft Sentinel'i kullanırken, Sentinel veri kaynağı olarak Microsoft 365 Denetimi'ni kullanır. İletişim uyumluluk uyarılarını Sentinel ile tümleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Sentinel'e ekleme](/azure/sentinel/quickstart-onboard). Ekleme işleminin bir parçası olarak veri kaynaklarınızı yapılandıracaksınız.
2. Microsoft Sentinel [Microsoft Office 365 veri bağlayıcısını](/azure/sentinel/data-connectors-reference#microsoft-office-365) yapılandırın ve bağlayıcı yapılandırması altında *Exchange'i* seçin.
3. İletişim uyumluluk uyarılarını almak için arama sorgusunu yapılandırın. Örneğin:

    *| OfficeActivity | burada OfficeWorkload == "Exchange" ve Operation == "SupervisionRuleMatch" | TimeGenerated'a göre sıralama*

    Belirli bir kullanıcıya filtre uygulamak için aşağıdaki sorgu biçimini kullanabilirsiniz:

    *| OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" and UserId == "User1@Contoso.com" | TimeGenerated'a göre sıralama*

Microsoft Sentinel tarafından toplanan Office 365 için Microsoft 365 Denetim günlükleri hakkında daha fazla bilgi için bkz. [Azure İzleyici Günlükleri başvurusu](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>İletişim uyumluluğunu ve Splunk tümleştirmeyi yapılandırma

İletişim uyumluluk uyarılarını Splunk ile tümleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Office 365 için Splunk Eklentisini](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI) yükleme
2. Microsoft Office 365 için Splunk Eklentisi için Azure AD'de bir tümleştirme uygulaması yapılandırma
3. Splunk çözümünüzde arama sorgularını yapılandırın. Tüm iletişim uyumluluk uyarılarını tanımlamak için aşağıdaki arama örneğini kullanın:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=SupervisionRuleMatch*

Belirli bir iletişim uyumluluk ilkesinin sonuçlarını filtrelemek için *SRPolicyMatchDetails.SRPolicyName* parametresini kullanabilirsiniz.

Örneğin, aşağıdaki arama örneği *Uygunsuz içerik* adlı bir iletişim uyumluluk ilkesiyle eşleşmeler için uyarılar döndürür:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

Aşağıdaki tabloda farklı ilke türleri için örnek arama sonuçları gösterilmektedir:

| İlke türleri | Örnek arama sonuçları |
| :------------------ | :--------------------------------------- |
| Özel hassas bilgi türü anahtar sözcük listesini algılama ilkesi | { <br> CreationTime: 2021-09-17T16:29:57 <br> Kimlik: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> Objectıd: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> İşlem: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> Kayıt Türü: 68 <br> ResultStatus: {"ItemClass":"IPM. Not","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Sürüm: 1 <br> İş Yükü: Exchange <br> } |
| Uygunsuz dili algılama ilkesi | { <br> CreationTime: 2021-09-17T23:44:35 <br> Kimlik: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> Objectıd: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> İşlem: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> Kayıt Türü: 68 <br> ResultStatus: {"ItemClass":"IPM. Yammer.Message","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Sürüm: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Diğer SIEM çözümleriyle iletişim uyumluluğunu yapılandırma

Microsoft 365 Denetimi'nden iletişim uyumluluk ilkesi eşleşmelerini almak için PowerShell'i veya [Office 365 Yönetim API'sini](/office/office-365-management-api/office-365-management-activity-api-reference) kullanabilirsiniz.

PowerShell kullanırken, iletişim uyumluluk etkinlikleri için denetim günlüğü olaylarını filtrelemek için **Search-UnifiedAuditLog** cmdlet'iyle bu parametrelerden birini kullanabilirsiniz.

| Denetim günlüğü parametresi | İletişim uyumluluğu parametre değeri |
| :------------------ | :--------------------------------------- |
| Operasyonlar          | SupervisionRuleMatch                     |
| Kayıt Türü          | ComplianceSupervisionExchange            |

Örneğin, **Operations** parametresini ve *SupervisionRuleMatch* değerini kullanan örnek bir arama aşağıda verilmiştir:

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Aşağıda **RecordsType** parametresini ve *ComplianceSupervisionExchange* değerini kullanan örnek bir arama verilmiştir:

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Kaynaklar

- [İletişim uyumluluğu denetimi](communication-compliance-reports-audits.md#audit)
- [Microsoft Purview Denetim (Premium)](advanced-audit.md)
- [Office 365 Yönetim Etkinliği API’si referansı](/office/office-365-management-api/office-365-management-activity-api-reference)
