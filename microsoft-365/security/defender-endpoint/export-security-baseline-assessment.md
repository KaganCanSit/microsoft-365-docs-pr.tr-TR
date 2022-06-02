---
title: Cihaz başına güvenlik temeli değerlendirme yöntemleri ve özellikleri
description: "\"Tehdit ve Güvenlik Açığı Yönetimi\" verileri çeken güvenlik temelleri API'leri hakkında bilgi sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir."
keywords: api, API'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirmesi başına, makine değerlendirmesi başına, güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım güvenlik açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 5fd673f37dd35a83a714c0f3dd1c6ac3b0a049ca
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840080"
---
# <a name="export-security-baselines-assessment-per-device"></a>Cihaz başına güvenlik temelleri değerlendirmesini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender Güvenlik Açığı Yönetimi mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.- Güncelleştirme](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir.

- **JSON yanıtı**  API, kuruluşunuzdaki tüm verileri JSON yanıtları olarak çeker. Bu yöntem, _100 K'den az cihazı olan küçük kuruluşlar_ için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan \@odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

- **dosyalar aracılığıyla** Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Azure Depolama'dan verileri aşağıdaki gibi indirebilirsiniz:
  - Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.
  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.

'_JSON yanıtı_ veya _dosyalar aracılığıyla_' kullanılarak toplanan veriler, geçerli durumu gösteren geçerli anlık görüntüdür. Geçmiş verileri içermez. Geçmiş verileri toplamak için müşterilerin verileri kendi veri depolamalarına kaydetmesi gerekir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma güvenlik temeli değerlendirme yöntemleri **_tam dışarı aktarma_** ve **_cihaza göredir_** ( **_cihaz başına_** olarak da adlandırılır)

## <a name="1-export-security-baselines-assessment-json-response"></a>1. Güvenlik temelleri değerlendirmesini dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Cihaz başına tüm cihazlar için tüm güvenlik temeli değerlendirmelerini döndürür. DeviceId, ProfileId, ConfigurationId'nin her benzersiz bileşimi için ayrı bir giriş içeren bir tablo döndürür.

### <a name="12-permissions"></a>1.2 İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek için ayrıntılar için bkz. [Uç Nokta için Microsoft Defender API'lerini kullanma](apis-intro.md).

İzin türü|Izni|İzin görünen adı
:---|:---|:---
Uygulama|SecurityBaselinesAssessment.Read.All |'Tüm güvenlik temelleri değerlendirme bilgilerini oku'
Temsilci (iş veya okul hesabı)|SecurityBaselinesAssessment.Read|'Güvenlik temelleri değerlendirme bilgilerini oku'

### <a name="13-limitations"></a>1.3 Sınırlamalar

- En büyük sayfa boyutu 200.000'dir.
- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="14-parameters"></a>1.4 Parametreler

- pageSize (varsayılan = 50.000): Yanıt olarak sonuç sayısı.
- $top: Döndürülecek sonuç sayısı (@odata.nextLink döndürmez ve bu nedenle tüm verileri çekmez).

### <a name="15-http-request"></a>1.5 HTTP isteği

```http
GET /api/machines/baselineComplianceAssessmentByMachine
```

### <a name="16-properties-json-response"></a>1.6 Özellikleri (JSON yanıtı)

> [!NOTE]
> Her kayıt yaklaşık 1 KB veridir. Doğru pageSize parametresini seçerken bunu dikkate almanız gerekir.
>
> Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir. Yalnızca belgelenmiş sütunları kullanın.
>
> Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
|configurationId|Dize|Temel karşılaştırmadaki belirli bir yapılandırma için benzersiz tanımlayıcı.
|profileId|Dize|Değerlendirilen profil için benzersiz tanımlayıcı.
|Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
|deviceName|Dize|Cihazın tam etki alanı adı (FQDN).
|isApplicable|Boole|Yapılandırmanın bu cihaz için geçerli olup olmadığını gösterir.
|isCompliant|Boole|Cihazın yapılandırmayla uyumlu olup olmadığını gösterir.
|Kimliği|Dize|DeviceId, ProfileId ve ConfigurationId'nin birleşimi olan kayıt için benzersiz tanımlayıcı.
|osVersion|Dize|Cihazda çalışan işletim sisteminin belirli bir sürümü.
|osPlatform|Dize|Cihazda çalışan işletim sistemi platformu. Windows 10 ve Windows 11 gibi aynı aile içinde varyasyonları olan belirli işletim sistemleri. Ayrıntılar için bkz. [TVM tarafından desteklenen işletim sistemleri ve platformlar](tvm-supported-os.md) .
|rbacGroupId|Int|Rol tabanlı erişim denetimi (RBAC) grup kimliği. Cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
|rbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
|DataCollectionTimeOffset|Datetime|Verilerin cihazdan toplandığı zaman. Veri toplanmadıysa bu alan görünmeyebilir.
|ComplianceCalculationTimeOffset|Datetime|Değerlendirme hesaplamasının yapıldığı zaman.
|RecommendedValue|Dize|Geçerli cihaz ayarının şikayet olması için beklenen değerler kümesi.
|Currentvalue|Dize|Cihazda bulunan algılanan değerler kümesi.
|Kaynak|Dize|Geçerli cihaz ayarını belirlemek için kullanılan kayıt defteri yolu veya başka bir konum.

## <a name="17-example"></a>1.7 Örneği

### <a name="171-request-example"></a>1.7.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="172-response-example"></a>1.7.2 Yanıt örneği

```json
{
"@odata.context": " https://api.securitycenter.microsoft.com /api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetBaselineAssessment)",
"value": [
{
    "id": "0000682575d5d473e82ed4d8680425d152411251_9e1b90be-e83e-485b-a5ec-4a429412e734_1.1.1",
    "configurationId": "1.1.1",
    "deviceId": "0000682575d5d473242222425d152411251",
    "deviceName": " ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596 ",
    "profileId": "9e1b90be-e83e-485b-a5ec-4a429412e734",
    "osPlatform": "WindowsServer2019",
    "osVersion": "10.0.17763.2330",
    "rbacGroupId": 86,
    "rbacGroupName": "UnassignedGroup",
    "isApplicable": true,
    "isCompliant": false,
    "dataCollectionTimeOffset": "2021-12-22T00:08:02.478Z",
    "recommendedValue": [
                    "Greater than or equal '24'"
                ],
                "currentValue": [
                    "24"
                ],
                "source": [
                    "password_hist_len"
                ],
}
```

## <a name="2-export-security-baselines-assessment-via-files"></a>2. Güvenlik temelleri değerlendirmesini dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Cihaz başına tüm cihazlar için tüm güvenlik temeli değerlendirmelerini döndürür. DeviceId, ProfileId, ConfigurationId'nin her benzersiz bileşimi için ayrı bir giriş içeren bir tablo döndürür.

### <a name="22-limitations"></a>2.2 Sınırlamaları

- Bu API için hız sınırlamaları dakikada 5 çağrı ve saatte 20 çağrıdır.

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/BaselineComplianceAssessmentExport
```

### <a name="24-parameters"></a>2.4 Parametreler

- sasValidHours: İndirme URL'lerinin geçerli olacağı saat sayısı (En fazla 24 saat).

### <a name="25-properties-via-files"></a>2.5 Özellikleri (dosyalar aracılığıyla)

> [!NOTE]
> Dosyalar çok satırlı Json biçiminde gzip sıkıştırılmış &.
>
>İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametresini kullanabilirsiniz.
>
>İndirme hızlarını en üst düzeye çıkarmak için, verileri verilerinizin bulunduğu Azure bölgesinden indirdiğinizden emin olun.
>
>Her kayıt yaklaşık 1 KB veridir. Sizin için uygun pageSize parametresini seçerken bunu dikkate almanız gerekir.
>
>Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir. Yalnızca belgelenmiş sütunları kullanın.

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
|Dosyaları dışarı aktarma|array[string]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.
|GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.

## <a name="26-example"></a>2.6 Örneği

### <a name="261-request-example"></a>2.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Yanıt örneği

```json
{
    "@odata.context": "https://api.securitycenter. contoso.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": 
    [
    "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId= OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00000-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv=ABCD",
   "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00001-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv= ABCD",
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik temelleri değerlendirme profillerini alma](get-security-baselines-assessment-profiles.md)
- [Güvenlik temelleri değerlendirme yapılandırmalarını alma](get-security-baselines-assessment-configurations.md)
