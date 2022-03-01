---
title: Dosya kaynak türü
description: Dosyalarla ilgili uç nokta uyarıları için son Microsoft Defender'ı alın.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 7fef64136e27b8b9a85163fe9e25fdf59ab6d2aa
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997162"
---
# <a name="file-resource-type"></a>Dosya kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Uç Nokta için Defender'da bir dosya varlığı temsil etme.

## <a name="methods"></a>Yöntemler

Yöntem|İade Türü |Açıklama
:---|:---|:---
[Dosya al](get-file-information.md) | [dosya](files.md) | Tek bir dosya al 
[Dosyayla ilgili uyarıları listele](get-file-related-alerts.md) | [uyarı](alerts.md) koleksiyonu | Dosyayla [](alerts.md) ilişkilendirilmiş uyarı varlıklarını almak.
[Dosyayla ilgili makineler listele](get-file-related-machines.md) | [makine](machine.md) koleksiyonu | Uyarıyla [ilişkilendirilmiş](machine.md) makine varlıklarını al.
[dosya istatistikleri](get-file-statistics.md) | İstatistik özeti | Verilen dosya için yaygın bilgileri sağlar.


## <a name="properties"></a>Özellikler

|Özellik | Tür | Açıklama |
|:---|:---|:---|
|sha1 | Dize | Dosya içeriğinin Sha1 karması |
|sha256 | Dize | Dosya içeriğinin Sha256 karması |
|globalPrevalence | Nullable long | Kuruluş genelinde yaygın dosya kullanımı |
|globalFirstObserved | DateTimeOffset | Dosya ilk kez gözlemlenirken |
|globalLastObserved | DateTimeOffset | Dosyanın en son ne zaman gözlemlenmesi |
|boyut | Nullable long | Dosya boyutu |
|fileType | Dize | Dosyanın türü |
|isPeFile | Boole | doğru ise (örneğin, "DLL", "EXE" vb.) |
|filePublisher | Dize | Dosya yayıncısı |
|fileProductName | Dize | Ürün adı |
|imzacı | Dize | Dosya imzacı |
|issuer | Dize | Dosyayı iletir |
|signerHash | Dize | İmzalama sertifikasının karması |
|isValidCertificate | Boole | Sertifikayı imzalama, Uç nokta aracısı için Microsoft Defender tarafından başarıyla doğrulandı |
|determinationType | Dize | Dosyanın karartma türü |
|determinationValue | Dize | Karar değeri |

## <a name="json-representation"></a>Json gösterimi

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
