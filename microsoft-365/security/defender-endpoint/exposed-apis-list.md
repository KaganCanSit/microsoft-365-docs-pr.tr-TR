---
title: Desteklenen Uç Nokta için Microsoft Defender API'leri
ms.reviewer: ''
description: API çağrıları oluşturabileceğiniz desteklenen belirli Uç Nokta için Microsoft Defender varlıkları hakkında bilgi edinin.
keywords: api'ler, desteklenen API'ler, aktör, uyarılar, cihaz, kullanıcı, etki alanı, ip, dosya, gelişmiş sorgular, gelişmiş tehdit avcılığı
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
ms.openlocfilehash: fe43d4df71b0801ae89149797068873577c77c38
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174694"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Desteklenen Uç Nokta için Microsoft Defender API'leri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Uç nokta URI'sini ve sürüm oluşturma

### <a name="endpoint-uri"></a>Uç nokta URI'si

> Hizmet temeli URI'si: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> Sorgu tabanlı OData'da '/api' ön eki bulunur. Örneğin, Uyarıları almak için adresine GET isteği gönderebilirsiniz [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Sürüm

> API sürüm oluşturma işlemini destekler.
>
> Geçerli sürüm **V1.0'dır**.
>
> Belirli bir sürümü kullanmak için şu biçimi kullanın: `https://api.securitycenter.microsoft.com/api/{Version}`. Örneğin: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Herhangi bir sürüm (ör. `https://api.securitycenter.microsoft.com/api/alerts`) belirtmezseniz en son sürüme ulaşacaksınız.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

API çağrılarını çalıştırabileceğiniz desteklenen tek tek varlıklar ve HTTP isteği değerleri, istek üst bilgileri ve beklenen yanıtlar gibi ayrıntılar hakkında daha fazla bilgi edinin.

## <a name="in-this-section"></a>Bu bölümde

Konu | Açıklama
:---|:---
[Gelişmiş avcılık](run-advanced-query-api.md) | API'den sorgu çalıştırma.<p>*Gelişmiş avcılık özellikleri [İş için Defender'a](../defender-business/mdb-overview.md) dahil değildir*.
[Uyarı yöntemleri ve özellikleri](alerts.md) | Uyarı alma, uyarı oluşturma, uyarıyı güncelleştirme ve daha fazlası gibi \- API çağrılarını çalıştırın.
[Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma](get-assessment-methods-properties.md) | Cihaz başına güvenlik açığı değerlendirmelerini toplamak için API çağrılarını çalıştırın; örneğin: \- güvenli yapılandırma değerlendirmesini dışarı aktarma, yazılım envanteri değerlendirmesini dışarı aktarma, yazılım güvenlik açıklarını dışarı aktarma ve delta dışarı aktarma yazılım güvenlik açıkları değerlendirmesi.
[Otomatik Araştırma yöntemleri ve özellikleri](investigation.md) | Araştırma koleksiyonu alma gibi \- API çağrılarını çalıştırın.
[Etki alanıyla ilgili uyarıları al](get-domain-related-alerts.md) | Etki alanıyla ilgili cihazları, etki alanı istatistiklerini ve daha fazlasını alma gibi \- API çağrılarını çalıştırın.
[Dosya yöntemleri ve özellikleri](files.md) | Dosya bilgilerini alma, dosyayla ilgili uyarılar, dosyayla ilgili cihazlar ve dosya istatistikleri gibi \- API çağrılarını çalıştırın.
[Gösterge yöntemleri ve özellikleri](ti-indicator.md) | Göstergeleri alma, Gösterge oluşturma ve Göstergeleri silme gibi \- API çağrılarını çalıştırın.
[IP ile ilgili uyarıları al](get-ip-related-alerts.md) | IP ile ilgili uyarıları alma ve IP istatistikleri alma gibi \- API çağrılarını çalıştırın.
[Makine yöntemleri ve özellikleri](machine.md) | Cihazları alma, kimliğe göre cihaz alma, oturum açmış kullanıcılar hakkında bilgi alma, etiketleri düzenleme ve daha fazlası gibi \- API çağrılarını çalıştırın.
[Makine Eylemi yöntemleri ve özellikleri](machineaction.md) | Yalıtım, Virüsten koruma taraması çalıştırma ve daha fazlası gibi \- API çağrıları çalıştırın.
[Öneri yöntemleri ve özellikleri](recommendation.md) | Kimliğe göre öneri alma gibi \- API çağrılarını çalıştırın.
[Düzeltme etkinliği yöntemleri ve özellikleri](get-remediation-methods-properties.md) | Tüm düzeltme görevlerini alma, kullanıma sunulan cihazları düzeltme görevi alma ve kimliğe göre bir düzeltme görevi alma gibi \- API çağrısı çalıştırın.
[Puan yöntemleri ve özellikleri](score.md) | Maruz kalma puanı alma veya cihaz güvenli puanı alma gibi \- API çağrılarını çalıştırın.
[Yazılım yöntemleri ve özellikleri](software.md) | Yazılıma göre güvenlik açıklarını listeleme gibi \- API çağrılarını çalıştırın.
[Kullanıcı yöntemleri](user.md) | Kullanıcıyla ilgili uyarıları ve kullanıcıyla ilgili cihazları alma gibi \- API çağrılarını çalıştırın.
[Güvenlik açığı yöntemleri ve özellikleri](vulnerability.md) | Cihazları güvenlik açığına göre listeleme gibi \- API çağrılarını çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [api'leri Uç Nokta için Microsoft Defender](apis-intro.md)

- [api sürüm notlarını Uç Nokta için Microsoft Defender](api-release-notes.md)
