---
title: makineAction kaynak türü
description: Uç nokta için Microsoft Defender'da MakineAction kaynak türünün yöntemleri ve özellikleri hakkında bilgi öğrenin.
keywords: api'ler, desteklenen api'ler, get, makineaction, son
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
ms.technology: mde
ms.openlocfilehash: 625170f0e589ece6f6277dc8445f3af7bef11837
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996557"
---
# <a name="machineaction-resource-type"></a>MakineAction kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Daha fazla bilgi için bkz. [Yanıt Eylemleri](respond-machine-alerts.md).

|Yöntem|İade Türü|Açıklama|
|---|---|---|
|[List MachineActions](get-machineactions-collection.md)|[Makine Eylemi](machineaction.md)|Makine [Eylemi varlıklarını](machineaction.md) listele.|
|[MakineAction'larını al](get-machineaction-object.md)|[Makine Eylemi](machineaction.md)|Tek bir Makine [Eylemi varlığı](machineaction.md) elde edersiniz.|
|[Soruşturma paketini topla](collect-investigation-package.md)|[Makine Eylemi](machineaction.md)|Makineden araştırma paketi [toplayın](machine.md).|
|[Araştırma paketi SAS URI'lerini al](get-package-sas-uri.md)|[Makine Eylemi](machineaction.md)|Araştırma paketini indirmek için URI'yi elde edin.|
|[Makinesi yalıt](isolate-machine.md)|[Makine Eylemi](machineaction.md)|Makinenin [ağı kullanarak](machine.md) yalıtmak.|
|[Makineye yalıtımdan çıkış](unisolate-machine.md)|[Makine Eylemi](machineaction.md)|[Yalıtım'tan](machine.md) çıkar makinesi.|
|[Uygulama yürütmeyi kısıtla](restrict-code-execution.md)|[Makine Eylemi](machineaction.md)|Uygulama yürütmeyi kısıtla.|
|[Uygulama kısıtlamalarını kaldırma](unrestrict-code-execution.md)|[Makine Eylemi](machineaction.md)|Uygulama yürütme kısıtlamalarını kaldırın.|
|[Virüsten koruma taraması çalıştırma](run-av-scan.md)|[Makine Eylemi](machineaction.md)|Av taramasını, uygun Windows Defender kullanarak çalıştırın.|
|[Offboard makinesi](offboard-machine-api.md)|[Makine Eylemi](machineaction.md)|Uç Nokta [için](machine.md) Microsoft Defender'ın offboard makinesi.|
|[Dosyayı durdurma ve karantinaya alın](stop-and-quarantine-file.md)|[Makine Eylemi](machineaction.md)|Makinede dosyanın yürütülmesini durdurun ve silin.|
|[Canlı yanıt çalıştır](run-live-response.md)|[Makine Eylemi](machineaction.md)|Bir cihazda bir dizi canlı yanıt komutu çalıştırır|
|[Canlı yanıt sonucu al](get-live-response-result.md)|URL varlığı|Belirli canlı yanıt komutu sonuç indirme bağlantısını dizinine göre indirir.|
|[Makine eylemini iptal etme](cancel-machine-action.md)|[Makine Eylemi](machineaction.md)|Etkin makine eylemini iptal etme.|

<br>

## <a name="properties"></a>Özellikler

|Özellik|Tür|Açıklama|
|---|---|---|
|Kimlik|Guid|Makine Eylemi [varlıklarının](machineaction.md) kimliği.|
|tür|Enum|Eylemin türü. Olası değerler şöyledir: "RunAntiVirusScan", "Offboard", "Canlı Yanıt", "CollectInvestigationPackage", "Isolate", "Unisolate", "StopAndQuarantineFile", "RestrictCodeExecution" ve "UnstrictCodeExecution".|
|kapsam|dize|Eylemin kapsamı. "Full" or "Selective" for Isolation, "Quick" or "Full" for Anti-Virus scan.|
|istekteyen|Dize|Eylemi yürüten kişinin kimliği.|
|externalID|Dize|Müşterinin özel korelasyon isteğiyle gönderebn olduğu kimlik.|
|requestSource|dize|Eylemi gönderilen kullanıcının/uygulamanın adı.|
|komutlar|dizi|Çalıştıracak komutlar. İzin verilen değerler PutFile, RunScript, GetFile değerleridir.|
|cancellationRequestor|Dize|Eylemi iptal edilen kişinin kimliği.|
|requestorComment|Dize|Eylem paylaşıldığı zaman yazılan açıklama.|
|cancellationComment|Dize|Eylem iptal edilirken yazılan açıklama.|
|durum|Enum|Komutun geçerli durumu. Olası değerler şöyledir: "Beklemede", "Çıkış", "Başarılı Oldu", "Başarısız", "Zaman Aşımı" ve "İptal Edildi".|
|machineId|Dize|[Eylemin yürütül](machine.md) olduğu makinenin kimliği.|
|computerDnsName|Dize|[Eylemin](machine.md) yürütül olduğu makinenin adı.|
|creationDateTimeUtc|DateTimeOffset|Eylemin oluşturulduğunda olduğu tarih ve saat.|
|cancellationDateTimeUtc|DateTimeOffset|Eylemin iptal edildiği tarih ve saat.|
|lastUpdateDateTimeUtc|DateTimeOffset|Eylem durumunun güncelleştirilmiş olduğu son tarih ve saat.|
|başlık|Dize|Makine eylem başlığı.|
|relatedFileInfo|Sınıf|İki Özellik içerir. dize `fileIdentifier`, Olası değerleri içeren Enum `fileIdentifierType` : "Sha1", "Sha256" ve "Md5".|

## <a name="json-representation"></a>Json gösterimi

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
