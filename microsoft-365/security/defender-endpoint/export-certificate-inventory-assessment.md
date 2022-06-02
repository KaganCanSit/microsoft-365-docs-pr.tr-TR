---
title: Cihaz başına sertifika değerlendirme yöntemleri ve özellikleri
description: "\"Tehdit ve Güvenlik Açığı Yönetimi\" verileri çeken sertifika API'leri hakkında bilgi sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir."
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
ms.openlocfilehash: c5f89d92e754648dcaffb134de70516c7274625d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838952"
---
# <a name="export-certificate-inventory-per-device"></a>Cihaz başına sertifika envanteri dışarı aktarma

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

## <a name="1-export-certificate-assessment-json-response"></a>1. Sertifika değerlendirmeyi dışarı aktarma (JSON yanıtı)

### <a name="11-api-method-description"></a>1.1 API yöntemi açıklaması

Cihaz başına tüm cihazlar için tüm sertifika değerlendirmelerini döndürür. DeviceId, Parmak İzi ve Yol'un her benzersiz bileşimi için ayrı bir giriş içeren bir tablo döndürür.

#### <a name="12-limitations"></a>1.2 Sınırlamaları

- En büyük sayfa boyutu 200.000'dir.
- Bu API için hız sınırlamaları dakikada 30 çağrı ve saatte 1000 çağrıdır.

### <a name="13-parameters"></a>1.3 Parametreler

- pageSize (varsayılan = 50.000): Yanıt olarak sonuç sayısı.
- $top: Döndürülecek sonuç sayısı (@odata.nextLink döndürmez ve bu nedenle tüm verileri çekmez).

### <a name="14-http-request"></a>1.4 HTTP isteği

```http
GET /api/machines/certificateAssessmentByMachine
```

### <a name="15-properties-json-response"></a>1.5 Özellikleri (JSON yanıtı)

> [!NOTE]
> Her kayıt yaklaşık 1 KB veridir. Doğru pageSize parametresini seçerken bunu dikkate almanız gerekir.
>
> Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir. Yalnızca belgelenmiş sütunları kullanın.
>
> Aşağıdaki tabloda tanımlanan özellikler, özellik kimliğine göre alfabetik olarak listelenir. Bu API'yi çalıştırırken, sonuçta elde edilen çıktının bu tabloda listelenen sırayla döndürülmesi gerekmez.

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
|Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
|DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
|Parmak izi|Boole|Sertifikanın benzersiz tanımlayıcısı.
|Yol|Dize|Sertifikanın konumu.
|SignatureAlgorithm|Dize|Karma algoritması ve kullanılan şifreleme algoritması.
|KeySize|Dize|İmza algoritmasında kullanılan anahtarın boyutu.
|ExpirationDate|Dize|Sertifikanın artık geçerli olmadığı tarih ve saat.
|Issuedate|Dize|Sertifikanın geçerli olduğu en erken tarih ve saat.
|SubjectType|Dize|Sertifikanın sahibinin bir CA veya son varlık olup olmadığını gösterir.
|Serialnumber|Dize|Sertifika yetkilisinin sistemlerindeki sertifikanın benzersiz tanımlayıcısı.
|Verilen|Nesne|Bir sertifikanın ait olduğu varlık; bir cihaz, birey veya kuruluş olabilir.
|VerilenAyrı|Nesne|Bilgileri doğrulayan ve sertifikayı imzalayan varlık.
|KeyUsage|Dize|Sertifikanın ortak anahtarının geçerli şifreleme kullanımları.
|ExtendedKeyUsage|Dize|Sertifika için diğer geçerli kullanımlar.
|RbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
|RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.

## <a name="16-example"></a>1.6 Örnek

### <a name="161-request-example"></a>1.6.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json

  {
     "@odata.context":"https://127.0.0.1/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetCertificateAssessment)",
      "value":[
        {
        "deviceId":"49126b9e4a5473b5229c73799e9e55c48668101b",
        "deviceName":"testmachine5",
        "thumbprint":"A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "path":"LocalMachine\\TestSignRoot\\A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "signatureAlgorithm":"sha384ECDSA",
        "keyLength":0,"notAfter":"0001-01-01T00:00:00Z",
        "notBefore":"0001-01-01T00:00:00Z",
        "subjectType":"CA",
        "serialNumber":"6086A185EAFA2B9943B4671603F40323",
        "subjectObject":null,
        "issuerObject":null,
        "keyUsageArray":null,
        "extendedKeyUsageArray":null,
        "isSelfSigned":false,
        "rbacGroupId":4226,
        "rbacGroupName":"testO6343398Gq31"}],
        "@odata.nextLink":"https://127.0.0.1/api/machines/CertificateAssessmentByMachine?pagesize=1&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wMy0yMS8wNTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjF9"
  }
```

## <a name="2-export-certificate-assessment-via-files"></a>2. Sertifika değerlendirmeyi dışarı aktarma (dosyalar aracılığıyla)

### <a name="21-api-method-description"></a>2.1 API yöntemi açıklaması

Cihaz başına tüm cihazlar için tüm sertifika değerlendirmelerini döndürür. DeviceId, Parmak İzi ve Yol'un her benzersiz bileşimi için ayrı bir giriş içeren bir tablo döndürür.

#### <a name="22-limitations"></a>2.2 Sınırlamaları

- Bu API için hız sınırlamaları dakikada 5 çağrı ve saatte 20 çağrıdır. 

### <a name="23-parameters"></a>2.3 Parametreler

- sasValidHours: İndirme URL'lerinin geçerli olacağı saat sayısı (En fazla 24 saat).

### <a name="24-http-request"></a>2.4 HTTP isteği

```http
GET /api/machines/certificateAssessmentExport
```

### <a name="25-properties-json-response"></a>2.5 Özellikleri (JSON yanıtı)

> [!NOTE]
> Dosyalar çok satırlı Json biçiminde gzip sıkıştırılmış &.
>
> İndirme URL'leri yalnızca 3 saat geçerlidir; aksi takdirde parametresini kullanabilirsiniz.
>
> İndirme hızlarını en üst düzeye çıkarmak için, verileri verilerinizin bulunduğu Azure bölgesinden indirdiğinizden emin olun.
>
> Her kayıt yaklaşık 1 KB veridir. Sizin için uygun pageSize parametresini seçerken bunu dikkate almanız gerekir.
>
> Yanıtta bazı ek sütunlar döndürülebilir. Bu sütunlar geçicidir ve kaldırılabilir. Yalnızca belgelenmiş sütunları kullanın.

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
|Dosyaları dışarı aktarma|Dize[dizi]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.
|GeneratedTime|Datetime|Dışarı aktarmanın oluşturulduğu saat.


## <a name="26-example"></a>2.6 Örneği

### <a name="261-request-example"></a>2.6.1 İstek örneği

```http
GET https://api.securitycenter.contoso.com/api/machines/certificateAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Yanıt örneği

```json
    {
        "@odata.context":"https://127.0.0.1/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
        "exportFiles":["https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4226/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=IMmwTOYmGvU0ei5AHLNAxnFCmZkE2jvBHzRmuAu9xaA%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4414/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=2r0y74WZsATa0DjQTwfBxNqL5vN2Wl0AZKHMNrxuJ30%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=75/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=uVdY4%2BBpMdPMwaD3G0RJTZkS4R9J8oN8I3tu%2FOcG35c%3D"],
        "generatedTime":"2022-03-20T13:18:00Z"
   }
```
