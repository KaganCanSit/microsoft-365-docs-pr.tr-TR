---
title: Makine kaynak türü
description: Uç Nokta için Microsoft Defender'da Makine kaynak türünün yöntemleri ve özellikleri hakkında bilgi öğrenin.
keywords: api'ler, desteklenen api'ler, get, makineler
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
ms.openlocfilehash: 80ac3e9ed43de98d32fd14063261452cfd5b1372
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996449"
---
# <a name="machine-resource-type"></a>Makine kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Yöntemler

<br>

****

|Yöntem|İade Türü|Açıklama|
|---|---|---|
|[Liste makineleri](get-machines.md)|[makine](machine.md) koleksiyonu|Kuruluşta [makine](machine.md) varlıklarını listele.|
|[Makine al](get-machine-by-id.md)|[makine](machine.md)|Bir makinenin [kimliğini](machine.md) kullanarak almak.|
|[Oturum açan kullanıcılara oturum açma](get-machine-log-on-users.md)|[kullanıcı](user.md) koleksiyonu|Makinede [oturum](user.md) açan Kullanıcı kümesine [sahip olur.](machine.md)|
|[İlgili uyarıları al](get-machine-related-alerts.md)|[uyarı](alerts.md) koleksiyonu|Makinede [yükseltilmiş uyarı](alerts.md) varlıkları [kümesine yükseltin](machine.md).|
|[Yüklü yazılımı al](get-installed-software.md)|[yazılım](software.md) koleksiyonu|Verilen bir makine kimliğiyle ilgili yüklü yazılım koleksiyonunu sağlar.|
|[Bulunan güvenlik açıklarını elde eder](get-discovered-vulnerabilities.md)|[güvenlik açığı koleksiyonu](vulnerability.md)|Verilen bir makine kimliğiyle ilgili bulunan güvenlik açıkları koleksiyonunu sağlar.|
|[Güvenlik önerileri al](get-security-recommendations.md)|[öneri](recommendation.md) koleksiyonu|Verilen bir makine kimliğiyle ilgili güvenlik önerileri koleksiyonunu sağlar.|
|[Makine etiketleri ekleme veya kaldırma](add-or-remove-machine-tags.md)|[makine](machine.md)|Belirli bir makineye etiket ekleyin veya etiketi kaldırın.|
|[IP'ye göre makineler bulma](find-machines-by-ip.md)|[makine](machine.md) koleksiyonu|IP ile görülen makineleri bulun.|
|[Makinelerini etikete göre bulma](find-machines-by-tag.md)|[makine](machine.md) koleksiyonu|Makine etikete göre [bulun](machine-tags.md).|
|[Eksik KB'leri al](get-missing-kbs-machine.md)|KB koleksiyonu|Makine kimliğiyle ilişkilendirilmiş eksik KB'lerin listesini al|
|[Cihaz değerini ayarlama](set-device-value.md)|[makine](machine.md) koleksiyonu|Cihazın [değerini ayarlayın](tvm-assign-device-value.md).|
|[Makine güncelleştirme](update-machine-method.md)|[makine](machine.md) koleksiyonu|Makinenin güncelleştirme durumunu al.|
|

## <a name="properties"></a>Özellikler

<br>

****

|Özellik|Tür|Açıklama|
|---|---|---|
|id|Dize|[makine kimliğini doğrulamayı](machine.md) sağlar.|
|computerDnsName|Dize|[makinede](machine.md) tam ad.|
|firstSeen|DateTimeOffset|Makinede Uç Nokta için Microsoft [Defender tarafından](machine.md) gözlemlenen ilk tarih ve saat.|
|lastSeen|DateTimeOffset|Son alınan tam cihaz raporunun saati ve tarihi. Bir cihaz normalde her 24 saatte bir tam rapor gönderir.|
|osPlatform|Dize|İşletim sistemi platformu.|
|onboardingstatus|Dize|Makine ekleme durumu. Olası değerler şöyledir: "eklemeli" ve "çıkarıldı".|
|osProcessor|Dize|İşletim sistemi işlemcisi. Bunun yerine osArchitecture özelliğini kullanın.|
|Sürüm|Dize|İşletim sistemi sürümü.|
|osBuild|Nullable long|İşletim sistemi derleme numarası.|
|lastIpAddress|Dize|Makinede yerel NIC'nin son [IP'sini.](machine.md)|
|lastExternalIpAddress|Dize|Makinenin İnternet'e [eriştiği](machine.md) son IP.|
|healthStatus|Enum|[makine](machine.md) durumu'. Olası değerlerdir: "Etkin", "Etkin Değil", "EngelliKullanıcı", "NoSensorData", "NoSensorDataImpairedCommunication" ve "Bilinmiyor".|
|rbacGroupName|Dize|Makine grubu Adı.|
|rbacGroupId|Dize|Makine grubu kimliği.|
|riskScore|Nullable Enum|Uç Nokta için Microsoft Defender tarafından değerlendirilen risk puanı. Olası değerler şöyledir: 'Yok', 'Bilgilendirme', 'Düşük', 'Orta' ve 'Yüksek'.|
|aadDeviceId|Nullable representation Guid|AAD Kimliğini (makine bağlı [olduğunda](machine.md)) AAD alır.|
|makine Etiketleri|Dize koleksiyonu|Makine [etiketleri](machine.md) kümesi.|
|exposureLevel|Nullable Enum|Uç Nokta için Microsoft Defender tarafından değerlendirilen pozlama düzeyi. Olası değerler: 'Yok', 'Düşük', 'Orta' ve 'Yüksek'.|
|deviceValue|Nullable Enum|Cihazın [değeridir](tvm-assign-device-value.md). Olası değerler şöyledir: 'Normal', 'Düşük' ve 'Yüksek'.|
|ipAddresses|IpAddress koleksiyonu|***IpAddress nesneleri*** kümesi. Bkz [. Makine API'sini al](get-machines.md).|
|osArchitecture|Dize|İşletim sistemi mimarisi. Olası değerler şöyledir: "32 bit", "64 bit". osProcessor yerine bu özelliği kullanın.|
|
