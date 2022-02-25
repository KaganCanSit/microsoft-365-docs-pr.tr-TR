---
title: Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma
description: API yanıtı her cihaza göre çalışır ve açık cihazlarınıza yüklenmiş korumasız yazılımları ve bu yazılım ürünlerinde bilinen güvenlik açıklarını içerir. Bu tablo işletim sistemi bilgilerini, CD'leri ve güvenlik açığı önem düzeyi bilgilerini de içerir.
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
ms.openlocfilehash: 951f78ba361a12e404a5cce2071f931eab30c43f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959653"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Tüm cihazlara yönelik tüm bilinen yazılım güvenlik açıklarını ve ayrıntılarını, cihaz başına döndürür.

Farklı türde veriler almak için farklı API çağrıları vardır. Veri miktarı çok büyük olduğundan, alınanın iki yolu vardır:

- [OData yazılım açıkları değerlendirmesini dışarı aktarma](#1-export-software-vulnerabilities-assessment-odata)  API, OData protokolüne göre organizasyon verilerinize Json yanıtları olarak tüm verileri çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

- [Dosyalar aracılığıyla yazılım açıkları değerlendirmesini dışarı aktarma](#2-export-software-vulnerabilities-assessment-via-files) Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Kaynağı'Depolama'den tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar:

  - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.

  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

Toplanan veriler ( _OData_ kullanılarak veya dosyalar _yoluyla) geçerli_ durumunun geçerli anlık görüntüsü olur ve tarihi verileri içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

> [!Note]
>
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

## <a name="1-export-software-vulnerabilities-assessment-odata"></a>1. Yazılım açıkları değerlendirmesini (OData) dışarı aktarma

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı cihaz başına tüm yüklü yazılım verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, ASPID benzersiz her bileşimi için bir giriş ile bir tablo döndürür.

#### <a name="limitations"></a>Sınırlamalar

>- En büyük sayfa boyutu 200.000'tir.
>
>- Bu API için fiyat sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü | İzin | İzin görünen adı
---|---|---
Uygulama | Güvenlik Açığı.Read.All | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı) | Güvenlik Açığı.Okuma | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000) – yanıtta sonuç sayısı
- $top – sonuç sayısı (sonuç olarak @odata.nextLink vermez ve dolayısıyla tüm verileri çekmez)

### <a name="15-properties"></a>1.5 Özellikler
>
>[!Note]
>
>- Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate alasınız.
>
>- Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.
>
>- Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir.  Bu API'yi çalıştıracaksanız, sonuçta elde edilen çıktının bu tabloda listelenen sırada döndürülecek olması gerekmez.
>

Özellik (Kimlik) | Veri türü | Açıklama | Döndürülen değer örneği
:---|:---|:---|:---
YerkarakDiyaKimlik | dize | Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı. | CHATE-2020-15992
CvssScore | dize | DEMİ'nin CVSS puanı. | 6.2
DeviceId | dize | Hizmette cihaz için benzersiz tanımlayıcı. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | dize | Cihazın tam etki alanı adı (FQDN). | johnlaptop.europe.contoso.com
DiskPath'ler  | Arraystring\[\] | Ürünün cihaza yük olduğuna dair disk kanıtı. | [ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel | dize | Bu güvenlik açığının açıkları açıklığı düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit) | ExploitIsInKit
FirstSeenTimestamp | dize | Bu ürünün 1. TIR'ı cihazda ilk kez görüldü. | 2020-11-03 10:13:34.8476880
Kimlik | dize | Kayıt için benzersiz tanımlayıcı. | 123ABG55_573AG&mnp!
LastSeenTimestamp | dize | EN son YALNıZ BIRAYI cihaz üzerinde görüldü. | 2020-11-03 10:13:34.8476880
OSPlatform | dize | Cihazda çalışan işletim sisteminin platformu. Bu, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın. | Windows10
RbacGroupName  | dize | Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur. | Sunucular
RecommendationReference | dize | Bu yazılımla ilgili öneri kimliğine başvuru. | va-_-microsoft--_ silverlight
RecommendedSecurityUpdate (isteğe bağlı) | dize | Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması. | Nisan 2020 Güvenlik Güncelleştirmeleri
RecommendedSecurityUpdateId (isteğe bağlı) | dize | İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı | 4550961
RegistryPaths  | Arraystring\[\] | Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı. | [ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName | dize | Yazılım ürününün adı. | chrome
SoftwareVendor | dize | Yazılım satıcısının adı. | google
SoftwareVersion | dize | Yazılım ürününün sürüm numarası. | 81.0.4044.138
VulnerabilitySeverityLevel  | dize | CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi. | Orta

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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
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
            "recommendationReference": "va-_-microsoft-_-windows_10"
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

İzin türü | İzin | İzin görünen adı
---|---|---
Uygulama | Güvenlik Açığı.Read.All | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı) | Güvenlik Açığı.Okuma | \'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametreler

- sasValidSatır – İndirme URL'lerinin geçerli olduğu saat sayısı (En fazla 24 saat)

### <a name="25-properties"></a>2.5 Özellikler

>[!Note]
>
>- Dosyalar çok satırlı Json & sıkıştırılmış sıkıştırılmış dosya biçimindedir.
>
>- İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametreyi kullanabilirsiniz.
>
>- Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirmeye emin olun.
>

>[!Note]
>
>- Her kayıt yaklaşık 1 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate alasınız.
>
>- Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.
>

Özellik (Kimlik) | Veri türü | Açıklama | Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma | arraystring\[\]  | Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi. | [  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]
GeneratedTime | dize | Dışarı aktarmanın oluşturulma zamanı. | 2021-05-20T08:00:00Z

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

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessmnt-1methods-properties.md)

- [Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma](get-assessmnt-secure-cfg.md)

- [Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma](get-assessmnt-software-inventory.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)

- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
