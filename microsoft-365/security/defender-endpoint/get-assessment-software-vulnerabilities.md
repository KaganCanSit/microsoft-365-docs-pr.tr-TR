---
title: Cihaz başına yazılım güvenlik açıkları değerlendirmesi dışarı aktarma
description: API yanıtı cihaza göredir ve kullanıma sunulan cihazlarınızda yüklü güvenlik açığı bulunan yazılımları ve bu yazılım ürünlerinde bilinen güvenlik açıklarını içerir. Bu tabloda işletim sistemi bilgileri, CVE kimlikleri ve güvenlik açığı önem derecesi bilgileri de yer alır.
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
ms.openlocfilehash: 86d2b0b09748a83c9b73430c4c6e371ca2e37f31
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839003"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Cihaz başına yazılım güvenlik açıkları değerlendirmesi dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bilinen tüm yazılım güvenlik açıklarını ve bunların tüm cihazlara ilişkin ayrıntılarını cihaz başına temel alarak döndürür.

Farklı API çağrıları farklı veri türleri alır. Veri miktarı büyük olabileceğinden, alınabilmesinin iki yolu vardır:

1. [Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi **JSON yanıtı**](#1-export-software-vulnerabilities-assessment-json-response)  API, kuruluşunuzdaki tüm verileri Json yanıtları olarak çeker. Bu yöntem, _100 K'den az cihazı olan küçük kuruluşlar_ için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan \@odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

2. [**Dosyalar aracılığıyla** yazılım güvenlik açıkları değerlendirmelerini dışarı aktarma](#2-export-software-vulnerabilities-assessment-via-files) Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. 100 K'den fazla cihazı olan büyük kuruluşlar için via-files önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar:
   - Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.
   - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.

3. [Delta dışarı aktarma yazılımı güvenlik açıkları değerlendirmesi **JSON yanıtı**](#3-delta-export-software-vulnerabilities-assessment-json-response)  DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId ve EventTimestamp'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.
API, kuruluşunuzdaki verileri Json yanıtları olarak çeker. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

   Tam "yazılım güvenlik açıkları değerlendirmesi (JSON yanıtı)" kuruluşunuzun yazılım güvenlik açıkları değerlendirmesinin tüm anlık görüntüsünü cihaza göre almak için kullanılır. Ancak, delta dışarı aktarma API çağrısı yalnızca seçili tarih ile geçerli tarih ("delta" API çağrısı) arasında gerçekleşen değişiklikleri getirmek için kullanılır. Her seferinde büyük miktarda veriyle tam dışarı aktarma işlemi almak yerine yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıklarıyla ilgili belirli bilgileri alırsınız. Delta dışarı aktarma JSON yanıt API'si çağrısı, "kaç güvenlik açığı düzeltildi?" gibi farklı KPI'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açığı eklendi?"

   Yazılım güvenlik açıkları için Delta dışarı aktarma JSON yanıt API çağrısı yalnızca hedeflenen bir tarih aralığına ait verileri döndürdüğünden, _tam dışarı aktarma_ olarak kabul edilmez.

Toplanan veriler ( _Json yanıtı_ veya _dosyalar aracılığıyla_) geçerli durum anlık görüntüsüdür. Geçmiş verileri içermez. Geçmiş verileri toplamak için müşterilerin verileri kendi veri depolamalarına kaydetmesi gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri **_tam dışarı aktarma_** ve **_cihaza göredir_** ( **_cihaz başına_** olarak da adlandırılır).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı, cihaz başına yüklü yazılımların tüm verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.

#### <a name="111-limitations"></a>1.1.1 Sınırlamaları

- En büyük sayfa boyutu 200.000'dir.
- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma.](apis-intro.md)

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Vulnerability.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Vulnerability.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000): Yanıt olarak sonuç sayısı.
- $top: Döndürülecek sonuç sayısı (@odata.nextLink döndürmez ve bu nedenle tüm verileri çekmez).

### <a name="15-properties"></a>1.5 Özellikleri

> [!NOTE]
>
> - Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate almanız gerekir.
> - Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
CveId|Dize|Ortak Güvenlik Açıkları ve Etkilenmeler (CVE) sistemi altında güvenlik açığına atanan benzersiz tanımlayıcı.|CVE-2020-15992
CvssScore|Dize|CVE'nin CVSS puanı.|6.2
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com
DiskPath'ler|Dizi\[dizesi\]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.|[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel|Dize|Bu güvenlik açığının kötüye kullanılabilirlik düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|Dize|Bu ürünün CVE'i cihazda ilk kez görüldü.|2020-11-03 10:13:34.8476880
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!
LastSeenTimestamp|Dize|CVE'nin cihazda son görüldüğü zaman.|2020-11-03 10:13:34.8476880
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Bu özellik, Windows 10 ve Windows 11 gibi aynı aile içinde varyasyonları olan belirli işletim sistemlerini gösterir. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.|Windows10 ve Windows 11
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.|Sunucular
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.|_va-microsoft-silverlight_
RecommendedSecurityUpdate (isteğe bağlı)|Dize|Güvenlik açığını gidermek için yazılım satıcısı tarafından sağlanan güvenlik güncelleştirmesinin adı veya açıklaması.|Nisan 2020 Güvenlik Güncelleştirmeleri
RecommendedSecurityUpdateId (isteğe bağlı)|Dize|İlgili kılavuz veya bilgi bankası (KB) makaleleri için geçerli güvenlik güncelleştirmelerinin veya tanımlayıcısının tanımlayıcısı|4550961
RegistryPaths|Dizi\[dizesi\]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName|Dize|Yazılım ürününün adı.|Chrome
SoftwareVendor|Dize|Yazılım satıcısının adı.|Google
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.|81.0.4044.138
VulnerabilitySeverityLevel|Dize|CVSS puanına ve tehdit ortamının etkilediği dinamik faktörlere bağlı olarak güvenlik açığına atanan önem düzeyi.|Orta
|

### <a name="16-examples"></a>1.6 Örnekler

#### <a name="161-request-example"></a>1.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Yazılım güvenlik açıklarını değerlendirmeyi dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı, cihaz başına yüklü yazılımların tüm verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.

#### <a name="212-limitations"></a>2.1.2 Sınırlamaları

Bu API için hız sınırlamaları dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma](apis-intro.md).

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Vulnerability.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Vulnerability.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametreler

- sasValidHours: İndirme URL'lerinin geçerli olacağı saat sayısı (En fazla 24 saat).

### <a name="25-properties"></a>2.5 Özellikleri

> [!NOTE]
>
> - Dosyalar çok satırlı Json biçiminde gzip sıkıştırılmış &.
> - İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametresini kullanabilirsiniz.
> - Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirme yaptığınızdan emin olabilirsiniz.
>
> - Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate almanız gerekir.
> - Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Örnekler

#### <a name="261-request-example"></a>2.6.1 İstek örneği

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>2.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Delta dışarı aktarma yazılımı güvenlik açıkları değerlendirmesi (JSON yanıtı)

### <a name="31-api-method-description"></a>3.1 API yöntemi açıklaması

DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. API, kuruluşunuzdaki verileri Json yanıtları olarak çeker. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz. Tam yazılım güvenlik açıkları değerlendirmesinin (JSON yanıtı) (cihazınıza göre kuruluşunuzun yazılım güvenlik açıkları değerlendirmesinin tüm anlık görüntüsünü almak için kullanılır) aksine, delta dışarı aktarma JSON yanıt API çağrısı yalnızca seçili tarih ile geçerli tarih (delta" API çağrısı) arasında gerçekleşen değişiklikleri getirmek için kullanılır. Her seferinde büyük miktarda veriyle tam dışarı aktarma işlemi almak yerine yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıklarıyla ilgili belirli bilgileri alırsınız. Delta dışarı aktarma JSON yanıt API'si çağrısı, "kaç güvenlik açığı düzeltildi?" gibi farklı KPI'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açığı eklendi?"

> [!NOTE]
> Cihaz API çağrısı tarafından yapılan tam dışarı aktarma yazılımı güvenlik açıkları değerlendirmesini haftada en az bir kez kullanmanız kesinlikle önerilir ve bu ek dışarı aktarma yazılımı güvenlik açıkları cihaza göre değişir (delta) API çağrısı haftanın diğer günlerinde de yapılır. Diğer Değerlendirmeler JSON yanıt API'lerinden farklı olarak , "delta dışarı aktarma" tam dışarı aktarma değildir. Delta dışarı aktarma işlemi yalnızca seçili tarih ile geçerli tarih ("delta" API çağrısı) arasında gerçekleşen değişiklikleri içerir.

#### <a name="311-limitations"></a>3.1.1 Sınırlamaları

- En büyük sayfa boyutu 200.000'dir.
- sinceTime parametresi en fazla 14 güne sahiptir.
- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="32-permissions"></a>3.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma.](apis-intro.md)

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Vulnerability.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun'
Temsilci (iş veya okul hesabı)|Vulnerability.Read|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun'

### <a name="33-url"></a>3.3 URL

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametreler

- sinceTime (gerekli): Seçilen saat ile bugün arasındaki veriler.
- pageSize (varsayılan = 50.000): yanıt olarak sonuç sayısı.
- $top: döndürülecek sonuç sayısı (@odata.nextLink döndürmez ve bu nedenle tüm verileri çekmez).

### <a name="35-properties"></a>3.5 Özellikleri

Döndürülen her kayıt, cihaz API'sine göre tam dışarı aktarma yazılımı güvenlik açıkları değerlendirmesinin tüm verilerinin yanı sıra iki alan daha içerir:  _**EventTimestamp**_ ve _**Status**_.

> [!NOTE]
>
> - Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir, bu nedenle lütfen yalnızca belgelenmiş sütunları kullanın.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
CveId |Dize|Ortak Güvenlik Açıkları ve Etkilenmeler (CVE) sistemi altında güvenlik açığına atanan benzersiz tanımlayıcı.|CVE-2020-15992  
CvssScore|Dize|CVE'nin CVSS puanı.|6.2  
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com  
DiskPath'ler|Dizi[dize]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|Dize|Bu delta olayının bulunduğu saat.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|Dize|Bu güvenlik açığının kötüye kullanılabilirlik düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|Dize|Bu ürünün CVE'i cihazda ilk kez görüldü.|2020-11-03 10:13:34.8476880  
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!  
LastSeenTimestamp|Dize|CVE'nin cihazda son görüldüğü zaman.|2020-11-03 10:13:34.8476880  
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi aynı aile içindeki varyasyonlara sahip belirli işletim sistemleri. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.|Windows10 ve Windows 11 
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.|Sunucular  
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.|va--microsoft--silverlight  
RecommendedSecurityUpdate |Dize|Güvenlik açığını gidermek için yazılım satıcısı tarafından sağlanan güvenlik güncelleştirmesinin adı veya açıklaması.|Nisan 2020 Güvenlik Güncelleştirmeleri  
RecommendedSecurityUpdateId |Dize|İlgili kılavuz veya bilgi bankası (KB) makaleleri için geçerli güvenlik güncelleştirmelerinin veya tanımlayıcısının tanımlayıcısı|4550961  
RegistryPaths |Dizi[dize]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
SoftwareName|Dize|Yazılım ürününün adı.|Chrome  
SoftwareVendor|Dize|Yazılım satıcısının adı.|Google  
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.|81.0.4044.138  
Durum|Dize|**Yeni** (bir cihazda sunulan yeni bir güvenlik açığı için) (1) **Düzeltildi** (bu güvenlik açığı cihazda artık yoksa, bu da düzeltildiği anlamına gelir). (2) **Güncelleştirildi** (cihazdaki bir güvenlik açığı değiştiyse. Olası değişiklikler şunlardır: CVSS puanı, kötüye kullanılabilirlik düzeyi, önem düzeyi, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Sabit
VulnerabilitySeverityLevel|Dize|Güvenlik açığına atanan önem düzeyi. CVSS puanına ve tehdit ortamının etkilediği dinamik faktörlere dayanır.|Orta
|

#### <a name="clarifications"></a>Açıklamalar

- Yazılım sürüm 1.0'dan sürüm 2.0'a güncelleştirildiyse ve her iki sürüm de CVE-A'da kullanıma sunulduysa, iki ayrı olay alırsınız:
   1. Düzeltildi: Sürüm 1.0'da CVE-A düzeltildi.
   1. Yeni: Sürüm 2.0'da CVE-A eklendi.

- Belirli bir güvenlik açığı (örneğin CVE-A) sürüm 1.0'a sahip yazılımlarda ilk kez belirli bir zamanda (örneğin, 10 Ocak) görüldüyse ve birkaç gün sonra bu yazılım aynı CVE-A'ya da kullanıma sunulan sürüm 2.0'a güncelleştirildiyse, şu iki ayrı olayı alırsınız:
   1. Düzeltildi: CVE-X, FirstSeenTimestamp Ocak 10, sürüm 1,0.
   1. Yeni: CVE-X, FirstSeenTimestamp Ocak 10, sürüm 2.0.

### <a name="36-examples"></a>3.6 Örnekler

#### <a name="361-request-example"></a>3.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>3.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.DeltaAssetVulnerability)",
    "value": [
        {
            "id": "008198251234544f7dfa715e278d4cec0c16c171_chrome_87.0.4280.88__",
            "deviceId": "008198251234544f7dfa715e278b4cec0c19c171",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_1c8fee370690ca24b6a0d3f34d193b0424943a8b8.DomainPII_0dc1aee0fa366d175e514bd91a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "87.0.4280.88",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Google Chrome"
            ],
            "lastSeenTimestamp": "2021-01-04 00:29:42",
            "firstSeenTimestamp": "2020-11-06 03:12:44",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "00e59c61234533860738ecf488eec8abf296e41e_onedrive_20.64.329.3__",
            "deviceId": "00e56c91234533860738ecf488eec8abf296e41e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_82c13a8ad8cf3dbaf7bf34fada9fa3aebc124116.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.64.329.3",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2127521184-1604012920-1887927527-24918864\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-11 19:49:48",
            "firstSeenTimestamp": "2020-12-07 18:25:47",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "01aa8c73095bb12345918663f3f94ce322107d24_firefox_83.0.0.0_CVE-2020-26971_",
            "deviceId": "01aa8c73065bb12345918693f3f94ce322107d24",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_42684eb981bea2d670027e7ad2caafd3f2b381a3.DomainPII_21eed80b086e76dbfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "mozilla",
            "softwareName": "firefox",
            "softwareVersion": "83.0.0.0",
            "cveId": "CVE-2020-26971",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "193220",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Mozilla Firefox 83.0 (x86 en-US)"
            ],
            "lastSeenTimestamp": "2021-01-05 17:04:30",
            "firstSeenTimestamp": "2020-05-06 12:42:19",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-mozilla-_-firefox",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "026f0fcb12345fbd2decd1a339702131422d362e_project_16.0.13701.20000__",
            "deviceId": "029f0fcb13245fbd2decd1a336702131422d392e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_a5706750acba75f15d69cd17f4a7fcd268d6422c.DomainPII_f290e982685f7e8eee168b4332e0ae5d2a069cd6.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "project",
            "softwareVersion": "16.0.13701.20000",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\ProjectProRetail - en-us"
            ],
            "lastSeenTimestamp": "2021-01-03 23:38:03",
            "firstSeenTimestamp": "2019-08-01 22:56:12",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-project",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "038df381234510b357ac19d0113ef622e4e212b3_chrome_81.0.4044.138_CVE-2020-16011_",
            "deviceId": "038df381234510d357ac19b0113ef922e4e212b3",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596a43a2ef2bbfa00f6a16c0cb1d108bc63e32.DomainPII_3c5fefd2e6fda2f36257359404f6c1092aa6d4b8.net",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "81.0.4044.138",
            "cveId": "CVE-2020-16011",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "ADV 200002",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{C4EBFDFD-0C55-3E5F-A919-E3C54949024A}"
            ],
            "lastSeenTimestamp": "2020-12-10 22:45:41",
            "firstSeenTimestamp": "2020-07-26 02:13:43",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        }
    ],
    "@odata.nextLink": "https://wpatdadi-eus-stg.cloudapp.net/api/machines/SoftwareVulnerabilitiesTimeline?sincetime=2021-01-11&pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessment-methods-properties.md)
- [Cihaz başına güvenli yapılandırma değerlendirmelerini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım envanteri değerlendirmeyi dışarı aktarma](get-assessment-software-inventory.md)

Diğer ilgililer

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Kuruluşunuzdaki güvenlik açıkları](tvm-weaknesses.md)
