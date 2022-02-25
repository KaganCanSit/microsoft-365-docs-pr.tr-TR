---
title: Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma
description: DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir girdi döndürür.
keywords: api, api'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirme başına güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: ab33db7fb7acf1969973a7af8f80ea97ef3d378f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959655"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Cihaz başına tüm yapılandırmaları ve bunların durumunu verir.

Farklı türde veriler almak için farklı API çağrıları vardır. Veri miktarı büyük olduğundan, alınanın iki yolu vardır:

- [Güvenli yapılandırma değerlendirmesi **OData'sını**](#1-export-secure-configuration-assessment-odata) dışarı aktarma: API, OData protokolüne göre organizasyonu json yanıtları olarak tüm verileri çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

- [Dosyalar aracılığıyla güvenli yapılandırma **değerlendirmesini dışarı aktarma**](#2-export-secure-configuration-assessment-via-files): Bu API çözümü, daha fazla miktarda verinin daha hızlı ve güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Kaynağı'Depolama'den tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar:

  - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.

  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

Toplanan veriler ( _OData_ kullanılarak veya dosyalar _yoluyla) geçerli_ durumunun geçerli anlık görüntüsü olur ve tarihi verileri içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

> [!Note]
>
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

## <a name="1-export-secure-configuration-assessment-odata"></a>1. Güvenli yapılandırma değerlendirmesini (OData) dışarı aktarma

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı, belirtilen cihazlarınız için Güvenli Yapılandırma Değerlendirmesi'ne sahiptir ve DeviceId, ConfigurationId'nin her benzersiz bileşimine bir giriş döndürür.

#### <a name="111-limitations"></a>1.1.1 Sınırlamalar

- En büyük sayfa boyutu 200.000'tir.

- Bu API için fiyat sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı](apis-intro.md) kullanma.

İzin türü | İzin | İzin görünen adı
---|---|---
Uygulama | Güvenlik Açığı.Read.All | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı) | Güvenlik Açığı.Okuma | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize \(default = 50.000\) – yanıt olarak sonuç sayısı

- \$top – sonuç sayısı \(\@odata.nextLink olarak sonuç vermez ve bu nedenle tüm verileri çekmez\)

### <a name="15-properties"></a>1.5 Özellikler

>[!Note]
>
>- Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir.  Bu API'yi çalıştıracaksanız, sonuçta elde edilen çıktının bu tabloda listelenen sırada döndürülecek olması gerekmez.
>
>- Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.
>

Özellik (Kimlik) | Veri türü | Açıklama | Döndürülen değer örneği
:---|:---|:---|:---
ConfigurationCategory | dize | Yapılandırmanın ait olduğu kategori veya gruplama: Uygulama, işletim sistemi, Ağ, Hesaplar, Güvenlik denetimleri | Güvenlik denetimleri
ConfigurationId | dize | Belirli bir yapılandırma için benzersiz tanımlayıcı | scid-10000
ConfigurationImpact | dize | Yapılandırmanın etkisini genel yapılandırma puanına göre derecelendirildi (1-10) | 9
ConfigurationName | dize | Yapılandırmanın görünen adı | Cihazları Uç Nokta için Microsoft Defender'a ekleme
ConfigurationSubcategory | dize | Yapılandırmanın ait olduğu alt kategori veya alt grup. Bu özellik, birçok durumda belirli özellikleri veya özellikleri açıklar. | Cihazları Ekleme
DeviceId | dize | Hizmette cihaz için benzersiz tanımlayıcı. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | dize | Cihazın tam etki alanı adı (FQDN). | johnlaptop.europe.contoso.com
IsApplicable | bool | Yapılandırmanın veya ilkenin uygun olup olmadığını gösterir | true
IsCompliant | bool | Yapılandırmanın veya ilkenin düzgün yapılandırıldığından emin olun | false
IsExpectedUserImpact | bool | Yapılandırmanın uygulanması kullanıcı üzerinde etki olup olmadığını gösterir | true
OSPlatform | dize | Cihazda çalışan işletim sisteminin platformu. Bu, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın. | Windows10
RbacGroupName | dize | Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur. | Sunucular
RecommendationReference | dize | Bu yazılımla ilgili öneri kimliğine başvuru. | sca-_-scid-20000
Zaman damgası | dize | Yapılandırmanın cihazda en son ne zaman görüldü? | 2020-11-03 10:13:34.8476880

### <a name="16-examples"></a>1.6 Örnekler

#### <a name="161-request-example"></a>1.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5 
```

#### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-20000",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Onboard Devices",
            "configurationImpact": 9,
            "isCompliant": false,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Onboard devices to Microsoft Defender for Endpoint",
            "recommendationReference": "sca-_-scid-20000"
        },
        {
            "deviceId": "0002a1de123456a8c06de736785395d4ce7610",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-39",
            "configurationCategory": "OS",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Enable 'Domain member: Digitally sign secure channel data (when possible)'",
            "recommendationReference": "sca-_-scid-39"
        },
        {
            "deviceId": "00044f912345daf759462bde6bd733d6a9c56ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45612eeb224d2de2f5ea3142726e63f16a.DomainPII_21eed80d086e76dbfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-6093",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Antivirus",
            "configurationImpact": 5,
            "isCompliant": false,
            "isApplicable": false,
            "isExpectedUserImpact": false,
            "configurationName": "Enable Microsoft Defender Antivirus real-time behavior monitoring for Linux",
            "recommendationReference": "sca-_-scid-6093"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Güvenli yapılandırma değerlendirmesini dışarı aktarma (dosyalar yoluyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı, belirtilen cihazlarınız için Güvenli Yapılandırma Değerlendirmesi'ne sahiptir ve DeviceId, ConfigurationId'nin her benzersiz bileşimine bir giriş döndürür.

#### <a name="212-limitations"></a>2.1.2 Sınırlamalar

Bu API için fiyat sınırlamaları, dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü | İzin | İzin görünen adı
---|---|---
Uygulama | Güvenlik Açığı.Read.All | \'"Tehdit ve Güvenlik Açığı Yönetimi" güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı) | Güvenlik Açığı.Okuma | \'"Tehdit ve Güvenlik Açığı Yönetimi" güvenlik açığı bilgilerini okuma\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parametreler

- sasValidSatır – İndirme URL'lerinin geçerli olduğu saat sayısı (En fazla 24 saat).

### <a name="25-properties"></a>2.5 Özellikler

>[!Note]
>
>- Dosyalar çok satırlı Json & sıkıştırılmış sıkıştırılmış dosya biçimindedir.
>
>- İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametreyi kullanabilirsiniz.
>
>- Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirmeye emin olun.
>
Özellik (Kimlik) | Veri türü | Açıklama | Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma | arraystring\[\] | Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi | [  Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2” ]
GeneratedTime | dize | Dışarı aktarmanın oluşturulma zamanı. | 2021-05-20T08:00:00Z ]

### <a name="26-examples"></a>2.6 Örnekler

#### <a name="261-request-example"></a>2.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>2.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#contoso.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessmnt-1methods-properties.md)

- [Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma](get-assessmnt-software-inventory.md)

- [Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma](get-assessmnt-software-vulnerabilities.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)

- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
