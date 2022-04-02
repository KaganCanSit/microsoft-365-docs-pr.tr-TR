---
title: Gelişmiş av şemasında Microsoft 365 Defender tabloları
description: Tehdit arama sorgularını çalıştırabilirsiniz verileri anlamak için gelişmiş av şemasında yer alan tablolar hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, veriler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a496e0e293e72821016d6efa5fbd9622f669ab0b
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755547"
---
# <a name="understand-the-advanced-hunting-schema"></a>Gelişmiş arama şemasını anlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Gelişmiş [av şeması](advanced-hunting-overview.md) ; cihazlar, uyarılar, kimlikler ve diğer varlık türleri hakkında etkinlik bilgileri veya bilgi sağlayan birden çok tablodan oluşturulur. Birden çok tabloya yayılan sorguları etkili bir şekilde oluşturmak için gelişmiş av şemasında yer alan tabloları ve sütunları anlamalısınız.

<a name="get-schema-information-in-the-security-center"></a>

## <a name="get-schema-information"></a>Şema bilgilerini al

Sorguları oluşturmakla birlikte, yerleşik şema başvurularını kullanarak şemadaki her tablo hakkında hızla aşağıdaki bilgileri edinebilirsiniz:

- **Tablolar açıklaması**: Tabloda yer alan verilerin türü ve bu verilerin kaynağı.
- **Sütunlar**: Tablodaki tüm sütunlar.
- **Eylem türleri**— tablo tarafından desteklenen `ActionType` olay türlerini temsil eden sütundaki olası değerler. Bu bilgiler yalnızca olay bilgileri içeren tablolar için sağlanır.
- **Örnek sorgu**: Tablonun nasıl kullanılay olacağını özellikte olan örnek sorgular.

### <a name="access-the-schema-reference"></a>Şema başvurusuna erişme
Şema başvurusuna hızla erişmek için, şema **gösteriminde** tablo adının yanındaki Başvuruyu görüntüle eylemini seçin. Tablo aramak için **Şema başvurusu** da öğesini de seçin.

:::image type="content" source="../../media/understand-schema-1.png" alt-text="Microsoft 365 Defender portalında Gelişmiş Av sayfasındaki Şema Başvurusu sayfası" lightbox="../../media/understand-schema-1.png":::

## <a name="learn-the-schema-tables"></a>Şema tablolarını öğrenme
Aşağıdaki başvuru, şemadaki tüm tabloları listeler. Her tablo adı, o tablonun sütun adlarını açıklayan sayfaya bağlantı sağlar. Tablo ve sütun adları, gelişmiş av ekranındaki şema gösteriminin bir parçası olarak Bulut için Defender'da da listelenir.

| Tablo adı | Açıklama |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Uyarılarla ilişkilendirilmiş dosyalar, IP adresleri, URL'ler, kullanıcılar veya cihazlar |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Önem derecesi bilgileri ve tehdit sınıflandırması dahil olmak üzere Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender uyarıları  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Diğer bulut uygulamaları ve hizmetlerde Office 365 ve nesneleri içeren etkinlikler |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Güvenlik denetimleri tarafından tetiklenen olaylar (örneğin, Güvenlik koruması ve Windows Defender Virüsten Koruma türler) |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Uç noktalarda sertifika doğrulama olaylarından alınan imzalı dosyaların sertifika bilgileri |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Dosya oluşturma, değiştirme ve diğer dosya sistemi olayları |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | DLL yükleme olayları |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Işletim sistemi bilgileri dahil olmak üzere makine bilgileri |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Cihazlarda oturum açma ve diğer kimlik doğrulama olayları |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Ağ bağlantısı ve ilgili olaylar |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Fiziksel bağdaştırıcılar, IP ve MAC adresleri ile bağlı ağlar ve etki alanları dahil olmak üzere cihazların ağ özellikleri |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Süreç oluşturma ve ilgili olaylar |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Kayıt defteri girdilerini oluşturma ve değiştirme |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Tehdit & Cihazlarla ilgili çeşitli güvenlik yapılandırmalarının durumunu gösteren Güvenlik Açığı Yönetimi değerlendirme etkinlikleri |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Threat & Güvenlik Açığı Yönetimi tarafından cihazları değerlendirmek için kullanılan çeşitli güvenlik yapılandırmaları hakkında bilgi tabanı; çeşitli standartlara ve karşılaştırmalara eşlemeler içerir  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Sürüm bilgileri ve destek sonu durumu da dahil olmak üzere cihazlarda yüklü yazılımların envanteri |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Cihazlarda bulunan yazılım açıkları ve her bir güvenlik açığını gideren kullanılabilir güvenlik güncelleştirmeleri listesi |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Exploit code'ın genel kullanıma açık olup olmadığı da dahil olmak üzere, herkese açık açık güvenlik açıkları için bilgi tabanı |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | E-postalara eklenen dosyalar hakkında bilgi |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Microsoft 365 teslimi ve engelleme etkinlikleri de dahil olmak üzere e-posta etkinliklerini engelleme |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | E-postalar alıcı posta kutusuna teslim Microsoft 365 sonra, teslim sonrası oluşan güvenlik olayları |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | E-postalarda yer alan URL'ler hakkında bilgiler |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Active Directory (AD) çalıştıran bir şirket içi etki alanı denetleyicisini içeren olaylar. Bu tablo, etki alanı denetleyicisinde kimlikle ilgili çeşitli olayları ve sistem olaylarını kapsar. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Hesap bilgileri de dahil olmak üzere çeşitli kaynaklardan Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Active Directory ve Microsoft çevrimiçi hizmetlerinde kimlik doğrulama olayları |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Kullanıcılar, gruplar, cihazlar ve etki alanları gibi Active Directory nesneleri için sorgular |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
