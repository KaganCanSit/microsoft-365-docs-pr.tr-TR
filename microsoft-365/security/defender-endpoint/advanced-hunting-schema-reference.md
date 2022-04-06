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
ms.openlocfilehash: 2e45a4ae78d0beb9bc57b72a59b9cf1376ac7da7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468357"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da gelişmiş arama şemasını anlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Gelişmiş [av şeması](advanced-hunting-overview.md) , cihazlar ve diğer varlıklar hakkında etkinlik bilgileri ya da bilgi sağlayan birden çok tablodan yapılır. Birden çok tabloya yayılan sorguları etkili bir şekilde oluşturmak için gelişmiş av şemasında yer alan tabloları ve sütunları anlamalısınız.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>Şema bilgilerini çalışma Bulut için Defender

Sorguları oluşturmakla birlikte, yerleşik şema başvurularını kullanarak şemadaki her tablo hakkında hızla aşağıdaki bilgileri edinebilirsiniz:

- **Tablolar açıklaması**: Tabloda yer alan verilerin türü ve bu verilerin kaynağı.
- **Sütunlar**: Tablodaki tüm sütunlar.
- **Eylem türleri**: Sütunda, tablo `ActionType` tarafından desteklenen olay türlerini temsil eden olası değerler. Bu değerler yalnızca olay bilgileri içeren tablolar için sağlanmıştır.
- **Örnek sorgu**: Tablonun nasıl kullanılay olacağını özellikte olan örnek sorgular.

### <a name="access-the-schema-reference"></a>Şema başvurusuna erişme

Şema başvurusuna hızla erişmek için, şema **gösteriminde** tablo adının yanındaki Başvuruyu görüntüle eylemini seçin. Tablo aramak için **Şema başvurusu** da öğesini de seçin.

:::image type="content" source="images/ah-reference.png" alt-text="Gelişmiş av sayfası" lightbox="images/ah-reference.png":::

## <a name="learn-the-schema-tables"></a>Şema tablolarını öğrenme

Aşağıdaki başvuru, gelişmiş av şemasında yer alan tüm tabloları listeler. Her tablo adı, o tablonun sütun adlarını açıklayan sayfaya bağlantı sağlar.

Tablo ve sütun adları, gelişmiş av Microsoft 365 Defender şema temsili içinde, tablo ve sütun adları da listelenmiştir.

<br>

****

|Tablo adı|Açıklama|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Alanla ilgili Microsoft 365 Defender |
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|Işletim sistemi bilgileri dahil olmak üzere cihaz bilgileri|
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
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Cihazlarda bulunan yazılım açıkları ve her bir güvenlik açığını gideren kullanılabilir güvenlik güncelleştirmeleri listesi|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Exploit code'ın genel kullanıma açık olup olmadığı da dahil olmak üzere, herkese açık açık güvenlik açıkları için bilgi tabanı|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Tehdit & Cihazlarla ilgili çeşitli güvenlik yapılandırmalarının durumunu gösteren Güvenlik Açığı Yönetimi değerlendirme etkinlikleri|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Threat & Güvenlik Açığı Yönetimi tarafından cihazları değerlendirmek için kullanılan çeşitli güvenlik yapılandırmaları hakkında bilgi tabanı; çeşitli standartlara ve karşılaştırmalara eşlemeler içerir|
|

> [!TIP]
> Uç [nokta, Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview), Microsoft Defender for Cloud Apps için Defender'dan gelen verileri kullanarak tehdit avına Office 365 için Microsoft Defender gelişmiş Microsoft Defender for Cloud Apps kullanın Kimlik için Microsoft Defender. [Aç'Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

Gelişmiş av iş akışlarınızı e-postanıza taşıma hakkında daha fazla bilgi Uç Nokta için Microsoft Defender Microsoft 365 Defender Gelişmiş arama sorgularını buradan [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](overview-custom-detections.md)
- [Gelişmiş av veri şeması değişiklikleri](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
