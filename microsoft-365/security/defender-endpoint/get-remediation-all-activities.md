---
title: Tüm düzeltme etkinliklerini listele
description: Tüm düzeltme etkinlikleri hakkında bilgi verir.
keywords: api'ler, düzeltme, düzeltme API'si, al, düzeltme görevleri, tüm düzeltme,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3e387c8fb6ca9f1aca756ef2ab0b4c0684033370
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014035"
---
# <a name="list-all-remediation-activities"></a>Tüm düzeltme etkinliklerini listele

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Tüm düzeltme etkinlikleri hakkında bilgi verir.

[Düzeltme etkinlikleri hakkında daha fazla bilgi öğrenin](tvm-remediation.md).

**URL:** GET: /api/remediationTasks
<br>[OData V4 sorgularını destekler](https://www.odata.org/documentation/).
<br>OData'da desteklenen işleçler:
<br>```$filter``` on:  ```createdon``` ve özellikler'i ```status``` seçin.
<br>```$top``` maksimum değeri 10.000' olur.
<br>```$skip```.
<br>Uç Nokta için [Microsoft Defender ile OData sorguları ile ilgili örneklere bakın](exposed-apis-odata-samples.md).

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|RemediationTasks.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı)|RemediationTask.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

## <a name="properties"></a>Özellikler

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Kategori|Dize|Düzeltme etkinliğinin kategorisi (Yazılım/Güvenlik yapılandırması)|Yazılım
completerEmail|Dize|Düzeltme etkinliği başka biri tarafından el ile tamamlandıktan sonra, bu sütunda o kişinin e-postası yer alır|Null
completerId|Dize|Düzeltme etkinliği başka biri tarafından el ile tamamlandıktan sonra, bu sütunda o kişinin nesne kimliği yer açılar|Null
tamamlanmaMethod|Dize|Düzeltme etkinliği, "tamamlandı olarak işaretle" seçeneğini seçen bir kişi tarafından "otomatik olarak" (tüm cihazlara yama varsa) veya "el ile" tamamılabilir|Otomatik
createdOn|DateTime|Bu düzeltme etkinliğinin oluşturulma zamanı|2021-01-12T18:54:11.5499478Z
Açıklama|Dize|Bu düzeltme etkinliğinin açıklaması|Cihazlarınızı etkileyen bilinen güvenlik açıklarını azaltmak için Microsoft Silverlight'ı sonraki bir sürüme güncelleştirin.
dueOn|DateTime|Bu düzeltme etkinliği için oluşturanın ayarlanacak son tarih|2021-01-13T00:00:00Z
fixedDevices|.|Düzeltilmiştir cihaz sayısı|2
Kimlik|Dize|Bu düzeltme etkinliğinin kimliği|097d9735-5479-4899-b1b7-77398899df92
adKimlik|Dize|İlgili ürün adı|Microsoft Silverlight
Öncelik|Dize|Bu düzeltme etkinliği için oluşturana öncelik (Yüksek\Orta\Düşük)|Yüksek
ürünkimlik|Dize|İlgili ürün kimliği|microsoft-_-silverlight
productivityImpactRemediationType|Dize|Yalnızca kullanıcıları etkilemeyen cihazlar için birkaç yapılandırma değişikliği talep edilebilir. Bu değer, "tüm ışıklı cihazlar" veya "yalnızca kullanıcı etkisi olan cihazlar" arasındaki seçimi gösterir.|AllAssets
rbacGroupNames|Dize|İlgili cihaz grubu adları|[ "Windows Servers", "Windows 11", "Windows 10" ]
recommendedProgram|Dize|Yükseltme için önerilen program|Null
önerilenVendor|Dize|Yükseltme için önerilen satıcı|Null
recommendedVersion|Dize|Güncelleştirme/yükseltme için önerilen sürüm|Null
relatedComponent|Dize|Bu düzeltme etkinliğinin ilgili bileşeni (güvenlik önerisi için ilgili bileşene benzer)|Microsoft Silverlight
requesterEmail|Dize|Oluşturucu e-posta adresi|globaladmin@UserName.contoso.com
requesterId|Dize|Oluşturan nesne kimliği|r647211f-2e16-43f2-a480-16ar3a2a796r
istekte bulunduran Notlar|Dize|Bu düzeltme etkinliği için oluşturan kişi tarafından eklenen notlar (ücretsiz metin)|Null
Scid|Dize|İlgili güvenlik önerisinin SCID'si|Null
Durum|Dize|Düzeltme etkinliği durumu (Etkin/Tamamlandı)|Etkin
statusLastModifiedOn|DateTime|Durum alanı güncelleştirilen tarih|2021-01-12T18:54:11.5499487Z
targetDevices|Long|Bu düzeltmenin uygulan uygulana uygun olduğu, açık cihaz sayısı|43
Başlık|Dize|Bu düzeltme etkinliğinin başlığı|Microsoft Silverlight'ı güncelleştirin
Tür|Dize|Düzeltme türü|Güncelleştirme
vendorId|Dize|İlgili satıcı adı|Microsoft

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/
```

### <a name="response-example"></a>Yanıt örneği

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks",
    "value": [
        {
            "id": "03942ef5-aewb-4w6e-b555-d6a97013844w",
            "title": "Update Microsoft Silverlight",
            "createdOn": "2021-02-10T13:20:36.4718166Z",
            "requesterId": "65548a1d-ef00-4a7a-8d19-1b967b5c36f4",
            "requesterEmail": "user1@contoso.com",
            "status": "Active",
            "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
            "description": "Update Silverlight to a later version  to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
            "relatedComponent": "Microsoft Silverlight",
            "targetDevices": 18511,
            "rbacGroupNames": [
                "UnassignedGroup",
                "hhh"
            ],
            "fixedDevices": 2866,
            "requesterNotes": "test",
            "dueOn": "2021-02-11T00:00:00Z",
            "category": "Software",
            "productivityImpactRemediationType": null,
            "priority": "Medium",
            "completionMethod": null,
            "completerId": null,
            "completerEmail": null,
            "scid": null,
            "type": "Update",
            "productId": "microsoft-_-silverlight",
            "vendorId": "microsoft",
            "nameId": "silverlight",
            "recommendedVersion": null,
            "recommendedVendor": null,
            "recommendedProgram": null
        }
    ]
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Düzeltme yöntemleri ve özellikleri](get-remediation-methods-properties.md)
- [Kimlikle bir düzeltme etkinliği elde](get-remediation-one-activity.md)
- [Bir düzeltme etkinliğinin açık cihazları listesi](get-remediation-exposed-devices-activities.md)
- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
