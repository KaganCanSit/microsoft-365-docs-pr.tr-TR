---
title: Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma
description: Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür.
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
ms.openlocfilehash: 4c3464a3aec242bd098503ac5bca997943ac2a4a
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014048"
---
# <a name="export-software-inventory-assessment-per-device"></a>Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Farklı API çağrıları farklı türde veriler elde edin. Veri miktarı büyük olduğundan, alınanın iki yolu vardır:

- [Yazılım envanteri değerlendirme **JSON yanıtı dışarı aktarma**](#1-export-software-inventory-assessment-json-response) API, Json yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

- [Dosyalar aracılığıyla yazılım envanteri **değerlendirmesini dışarı aktarma**](#2-export-software-inventory-assessment-via-files)  Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar:
  - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.
  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

Toplanan veriler ( _Json yanıtı kullanılarak_ veya dosyalar _yoluyla_), geçerli durumunun geçerli anlık görüntüsü olur. Tarihi veriler içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Yazılım stok değerlendirmesini dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı cihaz başına tüm yüklü yazılım verilerini içerir. Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür.

#### <a name="limitations"></a>Sınırlamalar

- En büyük sayfa boyutu 200.000'tir.
- Bu API için fiyat sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Software.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı)|Software.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000): Yanıtta sonuç sayısı.
- $top: Sonuç sayısı (sonuç olarak @odata.nextLink ile sonuç vermez ve dolayısıyla tüm verileri çekmez)

### <a name="15-properties"></a>1.5 Özellikler

> [!NOTE]
>
> - Her kayıt yaklaşık 0,5 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate alasınız.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştıracaksanız, sonuçta elde edilen çıktının bu tabloda listelenen sırada döndürülecek olması gerekmez.
> - Yanıtta bazı ek sütunlar döndürülebilirsiniz. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
DeviceId|dize|Hizmette cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com
DiskPath'ler|Dizi[dize]|Ürünün cihaza yük olduğuna dair disk kanıtı.|[ "C:\\ Program Dosyaları (x86)\\MicrosoftSilverlightApplication\\\\\\silverlight.exe" ]
EndOfSupportDate|dize|Bu yazılım için desteğin destek tarihi vardır veya sona erer.|2020-12-30
EndOfSupportStatus|dize|Destek durumu sonu. Şu olası değerleri içerebilir: Yok, EOS Sürümü, Yaklaşan EOS Sürümü, EOS Yazılımı, Yaklaşan EOS Yazılımı.|Yaklaşan EOS
Kimlik|dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!
NumberOfWeaknesses|int|Bu cihaz üzerinde bu yazılıma olan zayıf sayı|3
OSPlatform|dize|Cihazda çalışan işletim sisteminin platformu. Bunlar, Windows 10 11 gibi, aynı aile içindeki çeşitlemelere sahip Windows 10 Windows sistemleridir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.|Windows10 ve Windows 11
RbacGroupName|dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.|Sunucular
RegistryPaths|Dizi[dize]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\\ SOFTWAREWOW6432NodeMicrosoft Windows CurrentVersionUninstallMicrosoft\\\\ Silverlight" ]\\\\\\\\
SoftwareFirstSeenTimestamp|dize|Bu yazılım ilk kez cihazda görüldü.|2019-04-07 02:06:47
SoftwareName|dize|Yazılım ürününün adı.|Silverlight
SoftwareVendor|dize|Yazılım satıcısının adı.|microsoft
SoftwareVersion|dize|Yazılım ürününün sürüm numarası.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 Örnekler

#### <a name="161-request-example"></a>1.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "numberOfWeaknesses": 58,
            "diskPaths": [],
            "registryPaths": [],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "Upcoming EOS Version",
            "endOfSupportDate": "2021-05-11T00:00:00+00:00"
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eed80d086e79bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.7.214.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765ddaf71234bde6bd733d6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178aedfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "configuration_manager",
            "softwareVersion": "5.0.8634.1000",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{B7D3A842-E826-4542-B39B-1D883264B279}"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f38765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-inventory-assessment-via-files"></a>2. Yazılım envanteri değerlendirmesini dışarı aktarma (dosyalar yoluyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı cihaz başına tüm yüklü yazılım verilerini içerir. Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür.

#### <a name="211-limitations"></a>2.1.1 Sınırlamalar

Bu API için fiyat sınırlamaları, dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı kullanma.](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Software.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'
Temsilcili (iş veya okul hesabı)|Software.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuma\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametreler

- sasValidSatır: İndirme URL'lerinin geçerli olduğu saat sayısı (En fazla 24 saat)

### <a name="25-properties"></a>2.5 Özellikler

> [!NOTE]
>
> - Dosyalar çok satırlı JSON & sıkıştırılmış dosya sıkıştırmalı biçimdedir.
> - İndirme URL'leri yalnızca 3 saat geçerlidir. Aksi takdirde parametreyi kullanabilirsiniz.
> - Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirmeye emin olun.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma|arraystring\[\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|dize|Dışarı aktarmanın oluşturulma zamanı.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Örnekler

#### <a name="261-request-example"></a>2.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>2.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessment-methods-properties.md)
- [Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma](get-assessment-software-vulnerabilities.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
