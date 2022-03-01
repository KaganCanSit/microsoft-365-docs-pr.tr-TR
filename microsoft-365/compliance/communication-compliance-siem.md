---
title: SIEM çözümleriyle iletişim uyumluluğu
description: SIEM çözümleriyle iletişim uyumluluğu tümleştirmesi hakkında bilgi edinin.
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
ms.openlocfilehash: d957b5fec4341cd7335f5c5a49b6654ffaf51f68
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006757"
---
# <a name="communication-compliance-with-siem-solutions"></a>SIEM çözümleriyle iletişim uyumluluğu

[İletişim uyumluluğu,](communication-compliance.md) kuruluşta uygunsuz iletileri algılamanıza Microsoft 365 yakalamanıza ve üzerinde işlemnize yardımcı olarak iletişim risklerini en aza indirmeye yardımcı olan bir Insider risk çözümüdür. Microsoft [Sentinel](https://azure.microsoft.com/services/azure-sentinel) veya [Splunk](https://www.splunk.com/) gibi güvenlik bilgileri ve olay yönetimi (SIEM) çözümleri, kuruluş içindeki tehditleri toplamak ve izlemek için yaygın olarak kullanılır.

Kuruluşların yaygın bir ihtiyacı, iletişim uyumluluk uyarılarını ve bu SIEM çözümlerini tümleştirin. Bu tümleştirmeyle, kuruluşlar SIEM çözümlerinde iletişim uyumluluk uyarılarını  bakarak, iletişim uyumluluk iş akışı ve kullanıcı deneyimi içinde uyarıları düzeltmek için bu uyarıları düzeltmeye devam ediyor. Örneğin, çalışan başka bir çalışana rahatsız edici bir ileti gönderir ve bu ileti uygunsuz içeriği iletişim uyumluluk ilkesi izlemesi tarafından algılanır. Bu olaylar, iletişim uyumluluk Microsoft 365 tarafından denetim günlüğü olarak da bilinen "birleşik denetim günlüğü" içinde ve SIEM çözümüne aktarılır. Daha sonra SIEM çözümünde, iletişim uyumluluk uyarılarıyla ilişkilendirilmiş SIEM Denetimi Microsoft 365 olaylara yönelik bir uyarı tetiklenir. İlkeler SIEM çözümlerine yönelik uyarıya bu şekilde bildirilecek ve sonra iletişim uyumluluk çözümünde uyarıyı araştıracak ve düzeltmek için uyarılacaklar.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>DenetimDe iletişim Microsoft 365 uyarıları

Tüm iletişim uyumluluk ilkesi eşleşmeleri Denetim'de Microsoft 365 yakalanır. Aşağıdaki örneklerde, seçilen iletişim uyumluluğu ilkesi eşleşme etkinlikleri için kullanılabilir ayrıntılar gösterilmelidir:

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

**Özel anahtar sözcük Microsoft 365 (özel duyarlı bilgi türü) olan bir ilke için Denetim günlüğü girdisi örneği:**

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
> Şu anda, Microsoft 365 Denetimi'nde ilke eşleşmesi kaydediliyorsa ve ilke eşleşmelerini iletişim uyumluluğunu araştırmanız için gereken süre arasında 24 saatlik bir gecikme olabilir.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>İletişim uyumluluğunu ve Microsoft Sentinel tümleştirmeyi yapılandırma

İletişim uyumluluk ilkesi eşleşmelerini toplamak için Microsoft Sentinel'i kullanırken, Sentinel veri kaynağı olarak Microsoft 365 Denetim'i kullanır. İletişim uyumluluk uyarılarını Sentinel ile tümleştirin, aşağıdaki adımları tamamlayın:

1. [Microsoft Sentinel'e ekleme](/azure/sentinel/quickstart-onboard). Ekleme işleminin bir parçası olarak, veri kaynaklarınızı yapılandırabilirsiniz.
2. Veri bağlayıcısı için Microsoft Sentinel [Microsoft Office 365 yapılandırın ve bağlayıcı](/azure/sentinel/data-connectors-reference#microsoft-office-365) yapılandırması altında *Gönder'i Exchange*.
3. İletişim uyumluluk uyarılarını almak için arama sorgusunu yapılandırabilirsiniz. Örneğin:

    *| OfficeActivity | burada OfficeWorkload == "Exchange" ve Operation == "YönekRuleMatch" | TimeGenerated'e göre sıralama*

    Belirli bir kullanıcıya filtre yapmak için aşağıdaki sorgu biçimini kullanırsiniz:

    *| OfficeActivity | burada OfficeWorkload == "Exchange" ve Operation == "BuDeğişken" ve UserId == "User1@Contoso.com" | TimeGenerated'e göre sıralama*

Microsoft Sentinel tarafından toplanan Microsoft 365 günlükleri Office 365 hakkında daha fazla bilgi için bkz. [Azure İzleme Günlükleri başvurusu](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>İletişim uyumluluğunu ve Splunk tümleştirmeyi yapılandırma

İletişim uyumluluk uyarılarını Splunk ile tümleştirin, aşağıdaki adımları tamamlayın:

1. Web [için Splunk Eklenti'lerini Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Windows için Splunk Eklentileri için Azure AD'de bir tümleştirme uygulaması Microsoft Office 365
3. Splunk çözümünüzde arama sorgularını yapılandırarak. Tüm iletişim uyumluluk uyarılarını tanımlamak için aşağıdaki arama örneğini kullanın:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=WorkloadRuleMatch*

Belirli bir iletişim uyumluluk ilkesine yönelik sonuçları filtrelemek için *, SRPolicyMatchDetails.SRPolicyName parametresini kullanabilirsiniz* .

Örneğin, aşağıdaki arama örneğinde Uygunsuz içerik adlı iletişim uyumluluğu ilkesine eşleşmelerle ilgili *uyarılar ve yoll olabilir*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=WorkloadRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

Aşağıdaki tabloda, farklı ilke türleri için örnek arama sonuçları yer alır:

| İlke türleri | Örnek arama sonuçları |
| :------------------ | :--------------------------------------- |
| Özel hassas bilgi türü anahtar sözcük listesini algılama ilkesi | { <br> CreationTime: 2021-09-17T16:29:57 <br> Kimlik: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyShi: true <br> ObjectId: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Operation: YalıtlıkRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. Not","BilgiSiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey:StoreDeliveryAgent <br> UserType: 0 <br> Sürüm: 1 <br> İş Yükü: Exchange <br> } |
| Uygunsuz dili algılayan ilke | { <br> CreationTime: 2021-09-17T23:44:35 <br> Kimlik: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyShi: true <br> ObjectId: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Operation: YalıtlıkRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. İleti","BilgiSiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey:StoreDeliveryAgent <br> UserType: 0 <br> Sürüm: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Diğer SIEM çözümleriyle iletişim uyumluluğunu yapılandırma

Denetim Merkezi'nde iletişim uyumluluk Microsoft 365 eşleşmeleri almak için, PowerShell'i veya Office 365 [API'sini kullanabilirsiniz](/office/office-365-management-api/office-365-management-activity-api-reference).

PowerShell kullanırken, iletişim uyumluluk etkinlikleri için denetim günlüğü olaylarını filtrelemek üzere **Search-UnifiedAuditLog** cmdlet'iyle bu parametrelerden birini kullanabilirsiniz.

| Denetim günlüğü parametresi | İletişim uyumluluğu parametre değeri |
| :------------------ | :--------------------------------------- |
| Operasyonlar          | UzleMatch                     |
| RecordType          | ComplianceSupervisionExchange            |

Örneğin, Operations parametresi ve *YallıkRuleMatch* değerini kullanan örnek bir arama şöyledir:

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Aşağıda **, RecordsType** parametresini ve *ComplianceSupervisionExchange değerini kullanan örnek bir arama ve aşağıdakiler* yer alınarak değiştirilebilir:

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Kaynaklar

- [İletişim uyumluluğu denetimi](communication-compliance-reports-audits.md#audit)
- [Gelişmiş Denetim Microsoft 365](advanced-audit.md)
- [Office 365 Yönetimi Etkinliği API başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference)
