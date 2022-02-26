---
title: Uyarı API'sini edinin
description: Uç Nokta için Microsoft Defender'da Uyarı kaynak türünün yöntemleri ve özellikleri hakkında bilgi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3344bb13d785739f7957c3b0d000b04ae7fea95b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62974111"
---
# <a name="alert-resource-type"></a>Uyarı kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="methods"></a>Yöntemler

<br>

****

|Yöntem|İade Türü|Açıklama|
|---|---|---|
|[Uyarı al](get-alert-info-by-id.md)|[Uyarı](alerts.md)|Tek bir uyarı [nesnesine](alerts.md) sahip olun.|
|[Liste uyarıları](get-alerts.md)|[Uyarı](alerts.md) koleksiyonu|Liste [uyarısı](alerts.md) koleksiyonu.|
|[Uyarıyı güncelleştir](update-alert.md)|[Uyarı](alerts.md)|Belirli bir [uyarıyı güncelleştirin](alerts.md).|
|[Toplu güncelleştirme uyarıları](batch-update-alerts.md)||Bir grup [uyarıyı güncelleştirme](alerts.md).|
|[Uyarı oluştur](create-alert-by-reference.md)|[Uyarı](alerts.md)|Gelişmiş Av'dan alınan olay verilerine dayalı olarak [uyarı oluşturun](run-advanced-query-api.md).|
|[İlgili etki alanlarını listele](get-alert-related-domain-info.md)|Etki alanı koleksiyonu|Uyarıyla ilişkilendirilmiş URL'leri listele.|
|[İlgili dosyaları listele](get-alert-related-files-info.md)|[Dosya](files.md) koleksiyonu|Uyarıyla [](files.md) ilişkilendirilmiş dosya varlıklarını [listele](alerts.md).|
|[İlgili IP'leri listele](get-alert-related-ip-info.md)|IP koleksiyonu|Uyarıyla ilişkilendirilmiş liste IP'leri.|
|[İlgili makineler al](get-alert-related-machine-info.md)|[Makine](machine.md)|[Uyarıyla](machine.md) ilişkilendirilmiş [makine](alerts.md).|
|[İlgili kullanıcıları al](get-alert-related-user-info.md)|[Kullanıcı](user.md)|[Uyarıyla](user.md) ilişkilendirilmiş [kullanıcı](alerts.md).|
|

## <a name="properties"></a>Özellikler

<br>

****

|Özellik|Tür|Açıklama|
|---|---|---|
|id|Dize|Uyarı Kimliği.|
|başlık|Dize|Uyarı başlığı.|
|açıklama|Dize|Uyarı açıklaması.|
|alertCreationTime|Nullable DateTimeOffset|Uyarının oluşturulmuş olduğu tarih ve saat (UTC).|
|lastEventTime|Nullable DateTimeOffset|Aynı cihazda uyarıyı tetikleyen etkinliğin son oluşumu.|
|firstEventTime|Nullable DateTimeOffset|Bu cihazda uyarıyı tetikleyen ilk olay.|
|lastUpdateTime|Nullable DateTimeOffset|Uyarının son güncelleştirme tarihi ve saati (UTC).|
|resolvedTime|Nullable DateTimeOffset|Uyarının durumunun 'Çözümlendi' olarak değiştir bitiş tarihi ve saati.|
|olaykimlikkim|Nullable Long|[Uyarının](view-incidents-queue.md) Olay Kimliği.|
|investigationId|Nullable Long|[Uyarıyla](automated-investigations.md) ilgili Araştırma Kimliği.|
|investigationState|Nullable Enum|Araştırma'nın geçerli [durumu](automated-investigations.md). Olası değerler şöyledir: 'Bilinmiyor', 'Sonlandırıldı', 'Başarıyla Gönderildi', 'Silindi', 'Başarısız', 'Kısmen Kuyruğa Alındı', 'Çalışıyor', 'PendingApproval', 'PendingResource', 'PartialLyInvestigated', 'TerminatedByUser', 'TerminatedBySystem', 'Kuyruğa Alındı', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.|
|atanan|Dize|Uyarının sahibi.|
|rbacGroupName|Dize|RBAC cihaz grup adı.|
|mitreTechniques|Dize|Geri Enterprise teknik kimliği.|
|relatedUser|Dize|Belirli bir uyarıyla ilgili kullanıcı ayrıntıları.|
|önem derecesi|Enum|Uyarının önem derecesi. Olası değerler şöyledir: 'Belirtilmemiş', 'Bilgilendirme', 'Düşük', 'Orta' ve 'Yüksek'.|
|durum|Enum|Uyarının geçerli durumunu belirtir. Olası değerler şöyledir: 'Bilinmiyor', 'Yeni', 'Çıkış' ve 'Çözümlendi'.|
|sınıflandırma|Nullable Enum|Uyarının belirtimi. Olası değerler şöyledir: 'Bilinmiyor', 'YanlışPositive', 'DoğruPositive'.|
|karartma|Nullable Enum|Uyarıyı belirlemeyi belirtir. Olası değerler şöyledir: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'.|
|kategori|Dize|Uyarının kategorisi.|
|algılamaKaynağı|Dize|Algılama kaynağı.|
|threatFamilyName|Dize|Tehdit ailesi.|
|threatName|Dize|Tehdit adı.|
|machineId|Dize|Uyarıyla [ilişkilendirilmiş](machine.md) makine varlığının kimliği.|
|computerDnsName|Dize|[makinede](machine.md) tam ad.|
|aadTenantId|Dize|Kimlik Azure Active Directory.|
|12013'e|Dize|Uyarıyı tetikleyen uyarının kimliği.|
|açıklamalar|Uyarı açıklamalarının listesi|Uyarı Açıklaması nesnesi şunları içerir: açıklama dizesi, createdBy dizesi ve createTime tarih saati.|
|Kanıt|Uyarı kanıtı listesi|Uyarıyla ilgili kanıt. Aşağıdaki örneğine bakın.|
|

### <a name="response-example-for-getting-single-alert"></a>Tek uyarı almak için yanıt örneği:

```http
GET https://api.securitycenter.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
{
    "id": "da637472900382838869_1364969609",
    "incidentId": 1126093,
    "investigationId": null,
    "assignedTo": null,
    "severity": "Low",
    "status": "New",
    "classification": null,
    "determination": null,
    "investigationState": "Queued",
    "detectionSource": "WindowsDefenderAtp",
    "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
    "category": "Execution",
    "threatFamilyName": null,
    "title": "Low-reputation arbitrary code executed by signed executable",
    "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
    "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
    "firstEventTime": "2021-01-26T20:31:32.9562661Z",
    "lastEventTime": "2021-01-26T20:31:33.0577322Z",
    "lastUpdateTime": "2021-01-26T20:33:59.2Z",
    "resolvedTime": null,
    "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
    "computerDnsName": "temp123.middleeast.corp.microsoft.com",
    "rbacGroupName": "A",
    "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
    "threatName": null,
    "mitreTechniques": [
        "T1064",
        "T1085",
        "T1220"
    ],
    "relatedUser": {
        "userName": "temp123",
        "domainName": "DOMAIN"
    },
    "comments": [
        {
            "comment": "test comment for docs",
            "createdBy": "secop123@contoso.com",
            "createdTime": "2021-01-26T01:00:37.8404534Z"
        }
    ],
    "evidence": [
        {
            "entityType": "User",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": null,
            "sha256": null,
            "fileName": null,
            "filePath": null,
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": "name",
            "domainName": "DOMAIN",
            "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
            "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
            "userPrincipalName": "temp123@microsoft.com",
            "detectionStatus": null
        },
        {
            "entityType": "Process",
            "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
            "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
            "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
            "fileName": "rundll32.exe",
            "filePath": "C:\\Windows\\SysWOW64",
            "processId": 3276,
            "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
            "processCreationTime": "2021-01-26T20:31:32.9581596Z",
            "parentProcessId": 8420,
            "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
            "parentProcessFileName": "rundll32.exe",
            "parentProcessFilePath": "C:\\Windows\\System32",
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        },
        {
            "entityType": "File",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
            "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
            "fileName": "suspicious.dll",
            "filePath": "c:\\temp",
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        }
    ]
}
```
