---
title: Uç Nokta API'leri için desteklenen Microsoft Defender
ms.reviewer: ''
description: API çağrıları oluşturabilirsiniz. Uç nokta varlıkları için desteklenen belirli Microsoft Defender varlıkları hakkında bilgi edinin.
keywords: api'ler, desteklenen api'ler, Actor, alerts, device, user, domain, ip, dosya, gelişmiş sorgular, gelişmiş av
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
ms.openlocfilehash: 94c5698845f556936373ee4548d9aa137f03867b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997125"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Uç Nokta API'leri için desteklenen Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Uç nokta URI'si ve sürüm

### <a name="endpoint-uri"></a>Uç nokta URI'si

> Hizmet temel URI'si: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> OData tabanlı sorguların '/api' ön eki vardır. Örneğin, GET isteği gönderenin Uyarıları almak için [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Sürüm

> API, sürümleri destekler.
>
> Geçerli sürüm **V1.0'dır**.
>
> Belirli bir sürümü kullanmak için şu biçimi kullanın: `https://api.securitycenter.microsoft.com/api/{Version}`. Örneğin: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Herhangi bir sürüm belirtmezseniz (örn. `https://api.securitycenter.microsoft.com/api/alerts`) en son sürüme sahip olacaksiniz.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

API çağrılarını çalıştırabilirsiniz tek tek desteklenen varlıklar ve HTTP isteği değerleri, istek üst bilgileri ve beklenen yanıtlar gibi ayrıntılar hakkında daha fazla bilgi edinin.

## <a name="in-this-section"></a>Bu bölümde

Konu | Açıklama
:---|:---
[Gelişmiş Av](run-advanced-query-api.md) | API'den sorguları çalıştırın.
[Uyarı yöntemleri ve özellikleri](alerts.md) | Uyarı al, uyarı oluştur \- , uyarı güncelleştir ve daha fazlası gibi API çağrılarını çalıştırın.
[Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessment-methods-properties.md) | API aramalarını çalıştırarak cihaz başına güvenlik açığı değerlendirmeleri toplayın. Örneğin: \- güvenli yapılandırma değerlendirmesini dışarı aktarma, yazılım envanteri değerlendirmesini dışarı aktarma, yazılım güvenlik açıkları değerlendirmesini dışarı aktarma ve yazılım açıkları farklı dışarı aktarma güvenlik açıkları değerlendirmesi.
[Otomatik Araştırma yöntemleri ve özellikleri](investigation.md) | Araştırma koleksiyonu gibi Run \- API aramaları.
[Etki alanıyla ilgili uyarıları al](get-domain-related-alerts.md) | Etki alanıyla ilgili cihazlar, \- etki alanı istatistikleri ve daha fazlası gibi API çağrılarını çalıştırın.
[Dosya yöntemleri ve özellikleri](files.md) | Dosya bilgilerini, dosyayla \- ilgili uyarıları, dosyayla ilgili cihazları ve dosya istatistiklerini almak gibi API çağrılarını çalıştırın.
[Gösterge yöntemleri ve özellikleri](ti-indicator.md) | Gösterge Al, Gösterge Oluştur \- ve Göstergeleri Sil gibi API çağrılarını çalıştırın.
[IP ile ilgili uyarıları al](get-ip-related-alerts.md) | IP ile ilgili uyarılar almak \- ve IP istatistikleri almak gibi API çağrılarını çalıştırın.
[Makine yöntemleri ve özellikleri](machine.md) | Cihazları al, cihazları \- kimlikle al, oturum açan kullanıcılarla ilgili bilgiler, etiketleri düzenleme gibi API çağrılarını çalıştır.
[Makine Eylemi yöntemleri ve özellikleri](machineaction.md) | Isolation, Run anti-virus \- scan ve daha fazlası gibi API çağrılarını çalıştırın.
[Öneri yöntemleri ve özellikleri](recommendation.md) | Kimlikle öneri almak gibi \- API çağrılarını çalıştırın.
[Düzeltme etkinliği yöntemleri ve özellikleri](get-remediation-methods-properties.md) | Tüm düzeltme görevlerini almak \- , açık cihazlar düzeltme görevini almak ve kimlikle tek bir düzeltme görevi almak gibi API çağrılarını çalıştırın.
[Puan yöntemleri ve özellikleri](score.md) | Pozlama puanı almak veya cihazın \- güvenli puanını almak gibi API çağrılarını çalıştırın.
[Yazılım yöntemleri ve özellikleri](software.md) | Yazılıma göre liste açıkları \- gibi API aramalarını çalıştırın.
[Kullanıcı yöntemleri](user.md) | Kullanıcıyla ilgili uyarılar ve \- kullanıcıyla ilgili cihazlar gibi API çağrılarını çalıştırın.
[Güvenlik açığı yöntemleri ve özellikleri](vulnerability.md) | Liste cihazları gibi API çağrılarını \- güvenlik açığına bağlı olarak çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta API'leri için Microsoft Defender](apis-intro.md)

- [Uç Nokta API sürüm notları için Microsoft Defender](api-release-notes.md)
