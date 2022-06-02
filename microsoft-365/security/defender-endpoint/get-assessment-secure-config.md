---
title: Cihaz başına güvenli yapılandırma değerlendirmelerini dışarı aktarma
description: DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir girdi döndürür.
keywords: api, API'ler, dışarı aktarma değerlendirmesi, cihaz başına değerlendirme, güvenlik açığı değerlendirme raporu, cihaz güvenlik açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım güvenlik açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6d706dc8552490b7705cc23fca4751f810211d47
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839316"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Cihaz başına güvenli yapılandırma değerlendirmelerini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Tüm yapılandırmaları ve bunların durumunu cihaz başına temel alarak döndürür.

Farklı veri türlerini almak için farklı API çağrıları vardır. Veri miktarı büyük olabileceğinden, alınabilmesinin iki yolu vardır:

- [Güvenli yapılandırma değerlendirmesi **JSON yanıtını** dışarı aktarma](#1-export-secure-configuration-assessment-json-response): API, kuruluşunuzdaki tüm verileri Json yanıtları olarak çeker. Bu yöntem, _100 K'den az cihazı olan küçük kuruluşlar_ için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan \@odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

- [**Dosyalar aracılığıyla** güvenli yapılandırma değerlendirmesini dışarı aktarma](#2-export-secure-configuration-assessment-via-files): Bu API çözümü, daha büyük miktarlardaki verilerin daha hızlı ve daha güvenilir bir şekilde çekilmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar:

  - Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.

  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.

Toplanan veriler ( _JSON yanıtı_ veya _dosyalar aracılığıyla_) geçerli durum anlık görüntüsüdür ve geçmiş verileri içermez. Geçmiş verileri toplamak için müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri **_tam dışarı aktarma_** ve **_cihaza göredir_** ( **_cihaz başına_** olarak da adlandırılır).

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. Güvenli yapılandırma değerlendirmeyi dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı, kullanıma sunulan cihazlarınızda Güvenli Yapılandırma Değerlendirmesi'ni içerir ve DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir giriş döndürür.

#### <a name="111-limitations"></a>1.1.1 Sınırlamaları

- En büyük sayfa boyutu 200.000'dir.

- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek için ayrıntılar için bkz. [Uç Nokta için Microsoft Defender API'lerini kullanma](apis-intro.md).

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Vulnerability.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Vulnerability.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize \(default = 50.000\): Yanıt olarak sonuç sayısı.
- \$top: Döndürülecek \(sonuç sayısı odata.nextLink döndürmez \@ve bu nedenle tüm verileri\) çekmez.

### <a name="15-properties"></a>1.5 Özellikleri

> [!NOTE]
>
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.
> - Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
---|---|---|---
ConfigurationCategory|Dize|Yapılandırmanın ait olduğu kategori veya gruplandırma: Uygulama, İşletim Sistemi, Ağ, Hesaplar, Güvenlik denetimleri|Güvenlik denetimleri
ConfigurationId|Dize|Belirli bir yapılandırma için benzersiz tanımlayıcı|scid-10000
ConfigurationImpact|Dize|Yapılandırmanın genel yapılandırma puanına etkisi derecelendirilmiştir (1-10)|9
Configurationname|Dize|Yapılandırmanın görünen adı|Cihazları Uç Nokta için Microsoft Defender ekleme
ConfigurationSubcategory|Dize|Yapılandırmanın ait olduğu alt kategori veya alt gruplama. Çoğu durumda bu, belirli özellikleri veya özellikleri açıklar.|Cihazları Ekleme
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com
IsApplicable|Bool|Yapılandırmanın veya ilkenin geçerli olup olmadığını gösterir|True
IsCompliant|Bool|Yapılandırmanın veya ilkenin düzgün yapılandırılıp yapılandırılmadığını gösterir|False
IsExpectedUserImpact|Bool|Yapılandırmanın uygulanıp uygulanmayacağının kullanıcı tarafından etkilenip etkilenmeyeceğini gösterir|True
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Bu, aynı ailedeki Windows 10 ve Windows 11 gibi varyasyonlar da dahil olmak üzere belirli işletim sistemlerini gösterir. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.|Windows10 ve Windows 11
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.|Sunucular
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.|sca-_-scid-20000
Zaman damgası|Dize|Yapılandırmanın cihazda son görüldüğü zaman|2020-11-03 10:13:34.8476880
|

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
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Güvenli yapılandırma değerlendirmelerini dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı, kullanıma sunulan cihazlarınızda Güvenli Yapılandırma Değerlendirmesi'ni içerir ve DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir giriş döndürür.

#### <a name="212-limitations"></a>2.1.2 Sınırlamaları

Bu API için hız sınırlamaları dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma.](apis-intro.md)

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Vulnerability.Read.All|\'"Tehdit ve Güvenlik Açığı Yönetimi" güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Vulnerability.Read|\'"Tehdit ve Güvenlik Açığı Yönetimi" güvenlik açığı bilgilerini okuyun\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parametre

- sasValidHours: İndirme URL'lerinin geçerli olacağı saat sayısı (En fazla 24 saat).

### <a name="25-properties"></a>2.5 Özellikleri

> [!NOTE]
>
> - Dosyalar çok satırlı Json biçiminde gzip sıkıştırılmış &.
> - İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametresini kullanabilirsiniz.
> - Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirme yaptığınızdan emin olabilirsiniz.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
---|---|---|---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi|["Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.|2021-05-20T08:00:00Z
|

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

- [Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessment-methods-properties.md)
- [Cihaz başına yazılım envanteri değerlendirmeyi dışarı aktarma](get-assessment-software-inventory.md)
- [Cihaz başına yazılım güvenlik açıkları değerlendirmesi dışarı aktarma](get-assessment-software-vulnerabilities.md)

Diğer ilgililer

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Kuruluşunuzdaki güvenlik açıkları](tvm-weaknesses.md)
