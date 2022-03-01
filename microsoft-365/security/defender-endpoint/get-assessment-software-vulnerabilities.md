---
title: Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma
description: API yanıtı her cihaza göre çalışır ve açık cihazlarınıza yüklenmiş korumasız yazılımlar ve bu yazılım ürünlerine yönelik bilinen güvenlik açıkları içerir. Bu tablo işletim sistemi bilgilerini, CD'leri ve güvenlik açığı önem düzeyi bilgilerini de içerir.
keywords: api, api'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirme başına güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
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
ms.openlocfilehash: 5d10b96e1d5abfe1c9e9a87b9800dafba081c961
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014037"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Tüm cihazlara yönelik tüm bilinen yazılım güvenlik açıklarını ve ayrıntılarını, cihaz başına döndürür.

Farklı API çağrıları farklı türde veriler elde edin. Veri miktarı büyük olduğundan, alınanın iki yolu vardır:

1. [Yazılım açıkları değerlendirme **JSON yanıtı dışarı aktarma**](#1-export-software-vulnerabilities-assessment-json-response)  API, Json yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

2. [Dosyalar aracılığıyla yazılım açıkları **değerlendirmesini dışarı aktarma**](#2-export-software-vulnerabilities-assessment-via-files) Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Via-files, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar:
   - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.
   - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

3. [Delta dışarı aktarma yazılım güvenlik açıkları değerlendirme **JSON yanıtı**](#3-delta-export-software-vulnerabilities-assessment-json-response)  Her benzersiz bileşimi için bir girdiyle birlikte bir tablo döndürür: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,DorId ve EventTimestamp.
API, Json yanıtları olarak organizasyon verilerinize veri çeker. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.

   Tüm "yazılım güvenlik açıkları değerlendirmesi (JSON yanıtı)" tüm bu "yazılım açıkları değerlendirmesi", cihaza göre kuruma göre yazılım güvenlik açıkları değerlendirmesinin tüm anlık görüntüsünü elde etmek için kullanılır. Bununla birlikte, değişiklik dışarı aktarma API'si çağrısı yalnızca seçili tarih ile geçerli tarih (değişiklik"API çağrısı) arasında olan değişiklikleri getirmek için kullanılır. Her zaman büyük miktarda veriyle tam dışarı aktarma yapmak yerine, yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıkları hakkında belirli bilgiler edinebilirsiniz. Delta dışarı aktarma JSON yanıt API çağrısı, "kaç güvenlik açıkı düzeltildi?" gibi farklı KP'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açık eklendi?" gibi yeni güvenlik açıkları eklendi

   Yazılım güvenlik açıkları için Delta dışarı aktarma JSON yanıt API çağrısı yalnızca hedefli tarih aralığı için veri döndür olduğundan, tam dışarı aktarma olarak _kabul edilir_.

Toplanan veriler ( _Json yanıtı kullanılarak_ veya dosyalar _yoluyla_), geçerli durumunun geçerli anlık görüntüsü olur. Tarihi veriler içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Yazılım açıkları değerlendirmesini dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı cihaz başına tüm yüklü yazılım verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, ASPID benzersiz her bileşimi için bir giriş ile bir tablo döndürür.

#### <a name="111-limitations"></a>1.1.1 Sınırlamalar

- En büyük sayfa boyutu 200.000'tir.
- Bu API için fiyat sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Güvenlik Açığı.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı)|Güvenlik Açığı.Okuma|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000): Yanıtta sonuç sayısı.
- $top: Sonuç sayısı (sonuç @odata.nextLink ile sonuç vermez ve bu nedenle tüm verileri çekmez).

### <a name="15-properties"></a>1.5 Özellikler

> [!NOTE]
>
> - Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate alasınız.
> - Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştıracaksanız, sonuçta elde edilen çıktının bu tabloda listelenen sırada döndürülecek olması gerekmez.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
YerkarakDiyaKimlik|Dize|Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı.|CHATE-2020-15992
CvssScore|Dize|DEMİ'nin CVSS puanı.|6.2
DeviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com
DiskPath'ler|Arraystring\[\]|Ürünün cihaza yük olduğuna dair disk kanıtı.|[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel|Dize|Bu güvenlik açığının açıkları açıklığı düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|Dize|Bu ürünün 1. TIR'ı cihazda ilk kez görüldü.|2020-11-03 10:13:34.8476880
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!
LastSeenTimestamp|Dize|EN son YALNıZ BIRAYI cihaz üzerinde görüldü.|2020-11-03 10:13:34.8476880
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Bu özellik, Windows 10 11 gibi, aynı aile içindeki çeşitlemelere sahip belirli işletim Windows 10 Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.|Windows10 ve Windows 11
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.|Sunucular
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.|va-_-microsoft--_ silverlight
RecommendedSecurityUpdate (isteğe bağlı)|Dize|Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması.|Nisan 2020 Güvenlik Güncelleştirmeleri
RecommendedSecurityUpdateId (isteğe bağlı)|Dize|İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı|4550961
RegistryPaths|Arraystring\[\]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName|Dize|Yazılım ürününün adı.|Chrome
SoftwareVendor|Dize|Yazılım satıcısının adı.|Google
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.|81.0.4044.138
VulnerabilitySeverityLevel|Dize|CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi.|Orta
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

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Yazılım açıkları değerlendirmesini dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı cihaz başına tüm yüklü yazılım verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, ASPID benzersiz her bileşimi için bir giriş ile bir tablo döndürür.

#### <a name="212-limitations"></a>2.1.2 Sınırlamalar

Bu API için fiyat sınırlamaları, dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma](apis-intro.md).

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Güvenlik Açığı.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı)|Güvenlik Açığı.Okuma|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametreler

- sasValidSatır: İndirme URL'lerinin geçerli olduğu saat sayısı (En fazla 24 saat).

### <a name="25-properties"></a>2.5 Özellikler

> [!NOTE]
>
> - Dosyalar çok satırlı Json & sıkıştırılmış sıkıştırılmış dosya biçimindedir.
> - İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametreyi kullanabilirsiniz.
> - Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirmeye emin olun.
>
> - Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate alasınız.
> - Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma|arraystring\[\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Dize|Dışarı aktarmanın oluşturulma zamanı.|2021-05-20T08:00:00Z
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

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Delta dışarı aktarma yazılım açıkları değerlendirmesi (JSON yanıtı)

### <a name="31-api-method-description"></a>3.1 API yöntemi açıklaması

DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,ArdId gibi her benzersiz bileşimi için bir giriş olan bir tablo döndürür. API, Json yanıtları olarak organizasyon verilerinize veri çeker. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz. Tam yazılım açıkları değerlendirmesinin (JSON yanıtı) (cihazınızın yazılım güvenlik açıkları değerlendirmesinin tüm anlık görüntüsünü elde etmek için kullanılır) değişiklikli dışarı aktarma JSON yanıt API çağrısı, yalnızca seçili tarihle geçerli tarih (değişiklik" API çağrısı) arasında olan değişiklikleri getirmek için kullanılır. Her zaman büyük miktarda veriyle tam dışarı aktarma yapmak yerine, yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıkları hakkında belirli bilgiler edinebilirsiniz. Delta dışarı aktarma JSON yanıt API çağrısı, "kaç güvenlik açıkı düzeltildi?" gibi farklı KP'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açık eklendi?" gibi yeni güvenlik açıkları eklendi

> [!NOTE]
> Cihaz API çağrısına göre en az haftada bir kez tam dışarı aktarma yazılım açıkları değerlendirmesini ve bu ek dışarı aktarma yazılım açıkları için cihaz (değişiklikli) API çağrısına göre haftanın tüm diğer günlerini kullanmanız kesinlikle önerilir. Diğer JSON yanıt API'leri gibi "delta dışarı aktarma" tam dışarı aktarma değildir. Değişiklik dışarı aktarma, yalnızca seçilen tarih ile geçerli tarih (değişiklik" API çağrısı) arasında olan değişiklikleri içerir.

#### <a name="311-limitations"></a>3.1.1 Sınırlamalar

- En büyük sayfa boyutu 200.000'tir.
- Bu yanaTime parametresi en çok 14 gündür.
- Bu API için fiyat sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="32-permissions"></a>3.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Güvenlik Açığı.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgileri'
Temsilcili (iş veya okul hesabı)|Güvenlik Açığı.Okuma|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgileri'

### <a name="33-url"></a>3.3 URL

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametreler

- sinceTime (gerekli): Seçilen saat ile bugün arasındaki veriler.
- pageSize (varsayılan = 50.000): yanıtta sonuç sayısı.
- $top: sonuç sayısı (sonuç @odata.nextLink ile sonuç vermez ve bu nedenle tüm verileri çekmez).

### <a name="35-properties"></a>3.5 Özellikler

Döndürülen her kayıt, cihaz API'si tarafından yapılan tam dışarı aktarma yazılım açıkları değerlendirmesinde yer alan tüm verilerin yanı sıra iki alan daha içerir:  _**EventTimestamp**_ ve _**Durum**_.

> [!NOTE]
>
> - Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir; dolayısıyla lütfen yalnızca belgelenmiş sütunları kullanın.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştıracaksanız, sonuçta elde edilen çıktının bu tabloda listelenen sırada döndürülecek olması gerekmez.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
YerkarakDiyaKimlik |Dize|Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı.|CHATE-2020-15992  
CvssScore|Dize|DEMİ'nin CVSS puanı.|6.2  
DeviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com  
DiskPath'ler|Dizi[dize]|Ürünün cihaza yük olduğuna dair disk kanıtı.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|Dize|Bu delta olayı bulunduğu zaman.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|Dize|Bu güvenlik açığının açıkları açıklığı düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|Dize|Bu ürünün 1. TIR'ı cihazda ilk kez görüldü.|2020-11-03 10:13:34.8476880  
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!  
LastSeenTimestamp|Dize|EN son YALNıZ BIRAYI cihaz üzerinde görüldü.|2020-11-03 10:13:34.8476880  
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi, aynı aile içindeki çeşitlemelere sahip belirli Windows. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.|Windows10 ve Windows 11 
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.|Sunucular  
RecommendationReference|dize|Bu yazılımla ilgili öneri kimliğine başvuru.|va--microsoft--silverlight  
RecommendedSecurityUpdate |Dize|Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması.|Nisan 2020 Güvenlik Güncelleştirmeleri  
RecommendedSecurityUpdateId |Dize|İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı|4550961  
RegistryPaths |Dizi[dize]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
SoftwareName|Dize|Yazılım ürününün adı.|Chrome  
SoftwareVendor|Dize|Yazılım satıcısının adı.|Google  
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.|81.0.4044.138  
Durum|Dize|**Yeni** (bir cihazda yeni bir güvenlik açığı **için) (** 1) Düzeltildi (bu güvenlik açığı artık cihazda mevcut yoksa, bu durum düzeltilmiştir). (2) **Güncel** (bir cihaz'da bir güvenlik açığı değişmişse). Olası değişiklikler şunları içerir: CVSS puanı, exploitability level, önem düzeyi, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Düzeltildi
VulnerabilitySeverityLevel|Dize|Güvenlik açığına atanan önem düzeyi. Bu, CVSS puanına ve tehdit sahnesini etkileyen dinamik etmenlere dayalıdır.|Orta
|

#### <a name="clarifications"></a>Netleştirmeler

- Yazılım 1.0 sürümünden sürüm 2.0'a güncelleştirilmişse ve her iki sürüm de YERİPİ-A'ya açıksa, iki ayrı olay alırsınız:
   1. Düzeltildi: 1.0 sürümündeKI YERİNASLA-A düzeltildi.
   1. Yeni: 2.0 sürümüyle birlikte TIR-A eklendi.

- Belirli bir güvenlik açığı (örneğin, AİSYET) ilk olarak 1.0 sürümüne sahip yazılımda belirli bir zamanda (örneğin, 10 Ocak) görülürse ve birkaç gün sonra yazılım aynı ZAMAN-A sürümüne de açık olan 2.0 sürümüne güncelleştirilmişse, bu iki ayrı olay alırsınız:
   1. Düzeltildi: DEFA-X, FirstSeenTimestamp 10 Ocak sürüm 1,0.
   1. Yeni: CHA-X, FirstSeenTimestamp 10 Ocak sürüm 2.0.

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
- [Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma](get-assessment-software-inventory.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
