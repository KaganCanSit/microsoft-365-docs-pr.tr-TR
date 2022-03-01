---
title: Aracı durumu sorunlarını araştırma
description: mdatp health komutunu çalıştırarak döndürülen değerler hakkında bilgi
keywords: mdatp health, command, health, status, command, onboarding status
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
ms.technology: mde
ms.openlocfilehash: 13407c78f89058efe15ed0f5d8f23272716e0237
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028442"
---
# <a name="investigate-agent-health-issues"></a>Aracı durumu sorunlarını araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Aşağıdaki tablo, komutu ve bunların ilgili açıklamalarını çalıştırarak döndürülen `mdatp health` değerler hakkında bilgi sağlar.

<br>

****

|Değer|Açıklama|
|---|---|
|automatic_definition_update_enabled|Otomatik virüsten koruma tanım güncelleştirmeleri etkinleştirildiyse True, aksi takdirde yanlış olur.|
|cloud_automatic_sample_submission_consent|Geçerli örnek gönderme düzeyi. Aşağıdaki değerlerden biri olabilir: <ul><li>**Yok**: Microsoft'a hiçbir şüpheli örnek gönderilmez.</li><li>**Kasa**: Yalnızca kişisel kimliği belirlenebilir bilgi (PII) içeren şüpheli örnekler otomatik olarak yüklenir. Bu, bu ayarın varsayılan değeridir.</li><li>**Hepsi**: Tüm şüpheli örnekler Microsoft'a gönderilir.</li></ul>|
|cloud_diagnostic_enabled|İsteğe bağlı tanılama veri toplama etkinleştirildiyse Doğru, aksi takdirde yanlış olur. Uç nokta için Defender ile ve Microsoft Defender Virüsten Koruma ve Windows gibi diğer ürün ve hizmetlerle ilgili daha fazla bilgi Windows [bkz. Microsoft Gizlilik Bildirimi](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|Bulut teslimi koruma etkinleştirildiyse true, aksi takdirde false olur.|
|conflicting_applications|Uç Nokta için Microsoft Defender ile çakışması olası uygulamaların listesi. Bu liste, uyumluluk sorunlarına neden olduğu bilinen diğer güvenlik ürünlerini ve diğer uygulamaları içerir ancak bunlarla sınırlı değildir.|
|definitions_status|Virüsten koruma tanımlarının durumu.|
|definitions_updated|Son virüsten koruma tanım güncelleştirmesini tarih ve saati.|
|definitions_updated_minutes_ago|Son virüsten koruma tanımı güncelleştirmeden bu yana geçen dakika sayısı.|
|definitions_version|Virüsten koruma tanım sürümü.|
|edr_client_version|Cihazda EDR istemci sürümü.|
|edr_configuration_version|EDR sürümünü kullanın.|
|edr_device_tags|Cihazla ilişkilendirilmiş etiketlerin listesi.|
|edr_group_ids|Cihazın ilişkilendirilen grup kimliği.|
|edr_machine_id|Ad'da kullanılan cihaz Microsoft 365 Defender.|
|engine_version|Virüsten koruma altyapısının sürümü.|
|sağlıklı|Ürün iyi durumdaysa doğru, aksi takdirde yanlıştır.|
|lisanslı|Cihaz bir kiracıya alındıysa doğru; aksi takdirde yanlıştır.|
|log_level|Ürün için geçerli günlük düzeyi.|
|machine_guid|Virüsten koruma bileşeni tarafından kullanılan benzersiz makine tanımlayıcısı.|
|network_protection_status|Ağ koruma bileşeninin durumu (yalnızca macOS). Aşağıdaki değerlerden biri olabilir: <ul><li>**başlatma** - Ağ koruması başlat başlıyor</li><li>**failed_to_start** - Bir hatadan dolayı ağ koruması başlatılamdı</li><li>**başlatıldı** - Ağ koruması şu anda cihazda çalışıyor</li><li>**Yeniden başlatma** - Ağ koruması şu anda yeniden başlatıyor</li><li>**durduruluyor** - Ağ koruması durduruluyor</li><li>**durduruldu** - Ağ koruması çalışmıyor</li></ul>|
|org_id|Cihazın yerleşik olduğu kuruluş. Cihaz henüz herhangi bir kuruluşa eklememişse yazdırılır. Ekleme hakkında daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender'a Ekleme](onboarding.md).|
|passive_mode_enabled|Virüsten koruma bileşeni pasif modunda çalıştıracak şekilde ayarlanırsa True, aksi takdirde yanlış olur.|
|product_expiration|Geçerli ürün sürümünün destek sonuna ulaştığı tarih ve saat.|
|real_time_protection_available|Gerçek zamanlı koruma bileşeni iyi durumdaysa doğru, aksi takdirde yanlıştır.|
|real_time_protection_enabled|Gerçek zamanlı virüsten koruma etkinse true, aksi takdirde yanlış olur.|
|real_time_protection_subsystem|Gerçek zamanlı korumayı hizmet etmek için kullanılan alt sistem. Gerçek zamanlı koruma beklendiği gibilenmiyorsa, yazdırılır.|
|release_ring|Sürüm halkası. Daha fazla bilgi için bkz. [Dağıtım halkaları](deployment-rings.md).|
|
