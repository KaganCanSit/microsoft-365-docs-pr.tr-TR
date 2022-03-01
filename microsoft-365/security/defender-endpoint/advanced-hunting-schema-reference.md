---
title: Gelişmiş av şeması başvurusu
description: Tehdit arama sorgularını çalıştırabilirsiniz verileri anlamak için gelişmiş av şemasında yer alan tablolar hakkında bilgi öğrenin.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, mdatp, microsoft defender atp, uç nokta için Microsoft Defender, wdatp arama, sorgu, telemetri, şema başvurusu, kusto, tablo, veriler
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 290d302f815de38c4cd84f417118205ed6504fe2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021766"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da gelişmiş av şemasını anlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Gelişmiş [av şeması](advanced-hunting-overview.md) , cihazlar ve diğer varlıklar hakkında etkinlik bilgileri ya da bilgi sağlayan birden çok tablodan yapılır. Birden çok tabloya yayılan sorguları etkili bir şekilde oluşturmak için gelişmiş av şemasında yer alan tabloları ve sütunları anlamalısınız.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>Bulut için Defender'da şema bilgilerini al

Sorguları oluşturmakla birlikte, yerleşik şema başvurularını kullanarak şemadaki her tablo hakkında hızla aşağıdaki bilgileri edinebilirsiniz:

- **Tablolar açıklaması**: Tabloda yer alan verilerin türü ve bu verilerin kaynağı.
- **Sütunlar**: Tablodaki tüm sütunlar.
- **Eylem türleri**: Sütunda, tablo `ActionType` tarafından desteklenen olay türlerini temsil eden olası değerler. Bu yalnızca olay bilgileri içeren tablolar için sağlanmıştır.
- **Örnek sorgu**: Tablonun nasıl kullanılay olacağını özellikte olan örnek sorgular.

### <a name="access-the-schema-reference"></a>Şema başvurusuna erişme

Şema başvurusuna hızla erişmek için, şema **gösteriminde** tablo adının yanındaki Başvuruyu görüntüle eylemini seçin. Tablo aramak için **Şema başvurusu** da öğesini de seçin.

![Portal şeması başvurusuna nasıl erişileni gösteren resim.](images/ah-reference.png)

## <a name="learn-the-schema-tables"></a>Şema tablolarını öğrenme

Aşağıdaki başvuru, gelişmiş av şemasında yer alan tüm tabloları listeler. Her tablo adı, o tablonun sütun adlarını açıklayan sayfaya bağlantı sağlar.

Tablo ve sütun adları, gelişmiş av Microsoft 365 Defender şema temsili içinde, tablo ve sütun adları da listelenmiştir.

<br>

****

|Tablo adı|Açıklama|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Alanla ilgili Microsoft 365 Defender |
|**[CihazBilgileri](advanced-hunting-deviceinfo-table.md)**|Işletim sistemi bilgileri dahil olmak üzere cihaz bilgileri|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|Bağdaştırıcılar, IP ve MAC adresleri, ayrıca bağlı ağlar ve etki alanları dahil olmak üzere cihazların ağ özellikleri|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|Süreç oluşturma ve ilgili olaylar|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|Ağ bağlantısı ve ilgili olaylar|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|Dosya oluşturma, değiştirme ve diğer dosya sistemi olayları|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|Kayıt defteri girdilerini oluşturma ve değiştirme|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|Oturum açma bilgileri ve diğer kimlik doğrulama olayları|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|DLL yükleme olayları|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|Güvenlik denetimleri tarafından tetiklenen olaylar (güvenlik nedeniyle koruma ve açıklardan yararlanma koruması gibi) Microsoft Defender Virüsten Koruma türler|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|Uç noktalarda sertifika doğrulama olaylarından alınan imzalı dosyaların sertifika bilgileri|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|Sürüm bilgileri ve destek sonu durumu da dahil olmak üzere cihazlarda yüklü yazılımların envanteri|
|**[DeviceTvmSoftwareErabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Cihazlarda bulunan yazılım açıkları ve her bir güvenlik açığını gideren kullanılabilir güvenlik güncelleştirmeleri listesi|
|**[DeviceTvmSoftware BirikabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Exploit code'ın genel kullanıma açık olup olmadığı da dahil olmak üzere, herkese açık açık güvenlik açıkları için bilgi tabanı|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Tehdit & Cihazlarla ilgili çeşitli güvenlik yapılandırmalarının durumunu gösteren Güvenlik Açığı Yönetimi değerlendirme etkinlikleri|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Threat & Güvenlik Açığı Yönetimi tarafından cihazları değerlendirmek için kullanılan çeşitli güvenlik yapılandırmaları hakkında bilgi tabanı; çeşitli standartlara ve karşılaştırmalara eşlemeler içerir|
|

> [!TIP]
> Gelişmiş [av için Microsoft 365 Defender Uç nokta](/microsoft-365/security/defender/advanced-hunting-overview) için Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender'dan gelen verileri kullanarak tehdit avına kullanın. [Aç'Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

Uç nokta için Microsoft Defender'dan gelişmiş av iş akışlarınızı Gelişmiş av sorgularını Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender'e taşıma [hakkında daha fazla bilgi edinmek için.](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde)

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](overview-custom-detections.md)
- [Gelişmiş av veri şeması değişiklikleri](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
