---
title: Cihaz başına yazılım envanteri değerlendirmeyi dışarı aktarma
description: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.
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
ms.openlocfilehash: 296b977452802d8e1ed8949cf6a8871cac171f3a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840004"
---
# <a name="export-software-inventory-assessment-per-device"></a>Cihaz başına yazılım envanteri değerlendirmeyi dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Farklı API çağrıları farklı veri türleri alır. Veri miktarı büyük olabileceğinden, alınabilmesinin iki yolu vardır:

- [Yazılım envanteri değerlendirmesi **JSON yanıtlarını** dışarı aktarma](#1-export-software-inventory-assessment-json-response) API, kuruluşunuzdaki tüm verileri Json yanıtları olarak çeker. Bu yöntem, _100 K'den az cihazı olan küçük kuruluşlar_ için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan \@odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

- [**Dosyalar aracılığıyla** yazılım envanteri değerlendirmeyi dışarı aktarma](#2-export-software-inventory-assessment-via-files)  Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar:
  - Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.
  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.

Toplanan veriler ( _Json yanıtı_ veya _dosyalar aracılığıyla_) geçerli durum anlık görüntüsüdür. Geçmiş verileri içermez. Geçmiş verileri toplamak için müşterilerin verileri kendi veri depolamalarına kaydetmesi gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri **_tam dışarı aktarma_** ve **_cihaza göredir_** ( **_cihaz başına_** olarak da adlandırılır).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Yazılım envanteri değerlendirmeyi dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Bu API yanıtı, cihaz başına yüklü yazılımların tüm verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.

#### <a name="limitations"></a>Sınırlamalar

- En büyük sayfa boyutu 200.000'dir.
- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma.](apis-intro.md)

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Software.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Software.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000): Yanıt olarak sonuç sayısı.
- $top: Döndürülecek sonuç sayısı (@odata.nextLink döndürmez ve bu nedenle tüm verileri çekmez)

### <a name="15-properties"></a>1.5 Özellikleri

> [!NOTE]
>
> - Her kayıt yaklaşık 0,5 KB veridir. Sizin için doğru pageSize parametresini seçerken bunu dikkate almanız gerekir.
> - Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.
> - Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir, lütfen yalnızca belgelenmiş sütunları kullanın.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).|johnlaptop.europe.contoso.com
DiskPath'ler|Dizi[dize]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.|[ "C:\\ Program Files (x86)\\Microsoft\\Silverlight\\Application\\silverlight.exe" ]
EndOfSupportDate|Dize|Bu yazılım için desteğin sona ereceği veya sona ereceği tarih.|2020-12-30
EndOfSupportStatus|Dize|Destek sonu durumu. Şu olası değerleri içerebilir: Yok, EOS Sürümü, Yaklaşan EOS Sürümü, EOS Yazılımı, Yaklaşan EOS Yazılımı.|Yaklaşan EOS
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.|123ABG55_573AG&mnp!
NumberOfWeaknesses|Int|Bu cihazdaki bu yazılımdaki zayıflıkların sayısı|3
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Bunlar, Windows 10 ve Windows 11 gibi aynı aile içinde varyasyonları olan belirli işletim sistemleridir. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.|Windows10 ve Windows 11
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.|Sunucular
RegistryPaths|Dizi[dize]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.|[ "HKEY_LOCAL_MACHINE\\ SOFTWARE\\WOW6432Node\\Microsoft\\ Windows\\ CurrentVersion\\Uninstall\\Microsoft Silverlight" ]
SoftwareFirstSeenTimestamp|Dize|Bu yazılım cihazda ilk kez görüldü.|2019-04-07 02:06:47
SoftwareName|Dize|Yazılım ürününün adı.|Silverlight
SoftwareVendor|Dize|Yazılım satıcısının adı.|Microsoft
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.|81.0.4044.138
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

## <a name="2-export-software-inventory-assessment-via-files"></a>2. Yazılım envanteri değerlendirmeyi dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Bu API yanıtı, cihaz başına yüklü yazılımların tüm verilerini içerir. DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür.

#### <a name="211-limitations"></a>2.1.1 Sınırlamaları

Bu API için hız sınırlamaları dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="22-permissions"></a>2.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek [için ayrıntılar için bkz. Uç Nokta için Microsoft Defender API'lerini kullanma.](apis-intro.md)

İzin türü|Izni|İzin görünen adı
---|---|---
Uygulama|Software.Read.All|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'
Temsilci (iş veya okul hesabı)|Software.Read|\'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgilerini okuyun\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametre

- sasValidHours: İndirme URL'lerinin geçerli olacağı saat sayısı (En fazla 24 saat)

### <a name="25-properties"></a>2.5 Özellikleri

> [!NOTE]
>
> - Dosyalar çok satırlı JSON biçiminde gzip sıkıştırılmış &.
> - İndirme URL'leri yalnızca 3 saat geçerlidir. Aksi takdirde parametresini kullanabilirsiniz.
> - Verilerinizin en yüksek indirme hızı için, verilerinizin bulunduğu Azure bölgesinden indirme yaptığınızdan emin olabilirsiniz.

<br>

****

Özellik (Kimlik)|Veri türü|Açıklama|Döndürülen değer örneği
:---|:---|:---|:---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.|2021-05-20T08:00:00Z
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
- [Cihaz başına güvenli yapılandırma değerlendirmelerini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım güvenlik açıkları değerlendirmesi dışarı aktarma](get-assessment-software-vulnerabilities.md)

Diğer ilgililer

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Kuruluşunuzdaki güvenlik açıkları](tvm-weaknesses.md)
