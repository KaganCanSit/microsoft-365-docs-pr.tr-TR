---
title: Cihazda canlı yanıt komutlarını çalıştırma
description: Bir cihazda bir dizi canlı yanıt komutu çalıştırmayı öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, kitaplı kitaplara yükleme
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6e8146a5e73cb056f6e22ec975f909c281d0890a
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996519"
---
# <a name="run-live-response-commands-on-a-device"></a>Cihazda canlı yanıt komutlarını çalıştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)


[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Bir cihazda bir dizi canlı yanıt komutu çalıştırır

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları dakikada 10 çağrıdır (ek istekler HTTP 429 ile yanıt verir).

2. Eş zamanlı olarak 25 oturum (azaltma sınırını aşan istekler "429 - Çok fazla istek" yanıtı alır).

3. Makine kullanılamıyorsa, oturum 3 gün boyunca kuyruğa alır.

4. 10 dakika sonra RunScript komutu zaman aşımına neden olur.

5. Canlı yanıt komutları sıraya alınmaz ve bir defada yalnızca bir komut yürütül olabilir.

6. Bu API çağrısını çalıştırmaya çalışan makine, buna otomatik bir düzeltme düzeyi atanmamış bir RBAC cihaz grubunda ise, belirli bir Cihaz Grubu için en azından en düşük Düzeltme Düzeyini etkinleştirmeniz gerekir.

7. Tek bir API çağrısında birden çok canlı yanıt komutu  çalıştırabilirsiniz. Bununla birlikte, canlı yanıt komutu başarısız olduğunda sonraki tüm eylemler yürütülmez.

## <a name="minimum-requirements"></a>En Düşük Gereksinimler

Cihazda oturumu başlatamadan önce, aşağıdaki gereksinimleri karşılayın:

- **Dosyanın desteklenen bir sürümünü çalıştırarak Windows**.

  Cihazlar, aşağıdaki Windows sürümlerinden birini çalıştırabiliyor Windows

  - **Windows 11**
  
  - **Windows 10**
    - [Sürüm 1909](/windows/whats-new/whats-new-windows-10-version-1909) veya sonrası
    - [KB4515384 ile](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) Sürüm [1903](/windows/whats-new/whats-new-windows-10-version-1903)
    - [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) [ile Sürüm 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809)
    - [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795) [ile Sürüm 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803)
    - [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816) [ile Sürüm 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709)

  - **Windows Server 2019 - Yalnızca Genel önizleme için geçerlidir**
    - Sürüm 1903 veya ( [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) ile) daha sonraki sürümler
    - Sürüm 1809 ( [KB4537818 ile](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md).

|İzin türü|İzin|İzin görünen adı|
|---|---|---|
|Uygulama|Machine.LiveResponse|Belirli bir makinede canlı yanıt çalıştırma|
|Temsilcili (iş veya okul hesabı)|Machine.LiveResponse|Belirli bir makinede canlı yanıt çalıştırma|

## <a name="http-request"></a>HTTP isteği

```HTTP
POST https://api.securitycenter.microsoft.com/API/machines/{machine_id}/runliveresponse
```

## <a name="request-headers"></a>Üstbilgi isteği

|Name|Tür|Açıklama|
|---|---|---|
|Yetkilendirme|Dize|Taşıyıcı\<token>\. Gerekli.|
|İçerik Türü|dize|application/json. Gerekli.|

## <a name="request-body"></a>İstek gövdesi

|Parametre|Tür|Açıklama|
|---|---|---|
|Açıklama ekleme|Dize|Eylemle ilişkilendirmek için açıklama.|
|Komutlar|Dizi|Çalıştıracak komutlar. İzin verilen değerler PutFile, RunScript, GetFile değerleridir.|

## <a name="commands"></a>Komutlar

|Komut Türü|Parametreler|Açıklama|
|---|---|---|
|PutFile|Anahtar: FileName <p> Değer: \<file name\>|Kitaplıktan cihaza bir dosya koyar. Dosyalar çalışma klasörüne kaydedilir ve cihaz varsayılan olarak yeniden başlatıldığında silinir.
|RunScript|Anahtar: ScriptName <br> Değer: \<Script from library\> <p> Anahtar: Args <br> Değer: \<Script arguments\>|Cihazda kitaplıktan bir betik çalıştırır. <p>  Args parametresi betiğinize geçirildi. <p> 10 dakika sonra zaman aşımı.|
|GetFile|Anahtar: Yol <br> Değer: \<File path\>|Cihazdan dosya toplayın. NOT: Yol içinde geri tireler gerekir.|

## <a name="response"></a>Yanıt

- Başarılı olursa, bu yöntem 201 Oluşturuldu hata döner.

  Eylem varlığı. Belirtilen kimliğin bulunduğu makine bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```HTTP
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runliveresponse

```JSON
{
   "Commands":[
      {
         "type":"RunScript",
         "params":[
            {
               "key":"ScriptName",
               "value":"minidump.ps1"
            },
            {
               "key":"Args",
               "value":"OfficeClickToRun"
            }

         ]
      },
      {
         "type":"GetFile",
         "params":[
            {
               "key":"Path",
               "value":"C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
            }
         ]
      }
   ],
   "Comment":"Testing Live Response API"
}
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```HTTP
HTTP/1.1 200 Ok
```

İçerik türü: application/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "{machine_action_id}",
    "type": "LiveResponse",
    "requestor": "analyst@microsoft.com",
    "requestorComment": "Testing Live Response API",
    "status": "Pending",
    "machineId": "{machine_id}",
    "computerDnsName": "hostname",
    "creationDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "lastUpdateDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "errorHResult": 0,
    "commands": [
        {
            "index": 0,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "RunScript",
                "params": [
                    {
                        "key": "ScriptName",
                        "value": "minidump.ps1"
                    },{
                        "key": "Args",
                        "value": "OfficeClickToRun"
                    }
                ]
            }
        }, {
            "index": 1,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "GetFile",
                "params": [{
                        "key": "Path", "value": "C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
                    }
                ]
            }
        }
    ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Makine eylem API'sini edinin](get-machineaction-object.md)
- [Canlı yanıt sonucu al](get-live-response-result.md)
- [Makine eylemini iptal etme](cancel-machine-action.md)
