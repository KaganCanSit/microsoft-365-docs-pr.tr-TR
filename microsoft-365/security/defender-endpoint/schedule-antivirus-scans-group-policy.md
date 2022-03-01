---
title: Grup İlkesini kullanarak virüsten koruma taramaları zamanlama
description: Virüsten koruma taramalarını ayarlamak için Grup İlkesi kullanma
keywords: hızlı tarama, tam tarama, zamanlama, grup ilkesi, virüsten koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/10/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 0e5e22b1c3f73f39ad65df39fd25e9b7b6e8a913
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008104"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Grup İlkesini kullanarak virüsten koruma taramaları zamanlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Bu makalede, Grup İlkesi kullanılarak zamanlanmış taramaların nasıl yapılandırlandığı açıklanmıştır. Taramaları zamanlama ve tarama türleri hakkında daha fazla bilgi edinmek için bkz. Zamanlanmış hızlı veya [tam tarama Microsoft Defender Virüsten Koruma yapılandırma](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Grup İlkesini kullanarak virüsten koruma taramalarını yapılandırma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Düzenleyicisi'nde Bilgisayar **yapılandırması** \>  \> Yönetim Şablonları ve Bileşenleri ve **Windows'Microsoft Defender Virüsten Koruma** \>  \> **gidin**.

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi Nesnesi için ayarları belirtin ve tamam'ı **seçin**. 

4. Yapılandırmak istediğiniz her ayar için 1-4 adımlarını yinelayın.

5. Grup İlkesi Nesnenizi her zaman olduğu gibi dağıtın. Grup İlkesi Nesneleri hakkında yardım gerekirse bkz. [Grup İlkesi Nesnesi oluşturma](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Zamanlanmış taramaları yapılandırken, Zamanlanmış taramayı yalnızca bilgisayar açık olduğunda ama bilgisayarda değilken başlat ayarı varsayılan olarak etkindir ve makine önce boşta durmasını gerekli bulundurarak beklenen zamanlanmış zamanı etkide bırakır.
>
> Haftalık taramalarda, Windows Server'da varsayılan davranış makine boşta olduğunda otomatik bakım dışında tarama yapmaktır. Varsayılan ayar ve Windows 10, makine boşta olduğunda otomatik bakım sırasında tarama yapmaktır. Bu davranışı değiştirmek için **ScanOnlyIfIdle'i devre dışı bırakarak** ayarları değiştirin ve ardından bir zamanlama tanımlayın.

Daha fazla bilgi için Bkz. [Koruma güncelleştirmelerinin ne zaman indirilecek](manage-protection-update-schedule-microsoft-defender-antivirus.md) ve uygulanmalıdır? ve Kullanıcıların ilke ayarları konularını yerel olarak değiştirmesini [engelleme veya bu konular](configure-local-policy-overrides-microsoft-defender-antivirus.md) üzerinde değişiklik olmasına izin verme.

## <a name="group-policy-settings-for-scheduling-scans"></a>Tarama zamanlaması için Grup İlkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmamışsa) |
|:---|:---|:---|:---|
| Tarama | Zamanlanmış taramada kullanmak üzere tarama türünü belirtme | Hızlı tarama |
| Tarama | Zamanlanmış taramayı çalıştırmak için haftanın günlerini belirtme | Taramayı çalıştıracak günü belirtin (veya hiç belirtme). | Hiçbir zaman |
| Tarama | Zamanlanmış taramayı çalıştırmak için günün saatlerini belirtme | Gece yarısından sonra kaç dakika sonra olduğunu belirtin (örneğin, **01:00 için 60** girin). | 02:00 |
| Kök | Zamanlanmış görev zamanlarını rastgeleleştirme |Başka Microsoft Defender Virüsten Koruma, taramanın başlangıç saatlerini 0 ile 23 saat arasında herhangi bir aralara rastgele sırayın. <p>[SCEP'de](/mem/intune/protect/certificates-scep-configure), herhangi bir ara aralığı artı veya eksi 30 dakikayı rastgele tarar. Bu, sanal makinelerde veya VDI dağıtımlarında yararlı olabilir. | Etkin |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>Uç nokta kullanım dışıyken taramaları zamanlamayı kullanan Grup İlkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmamışsa) |
|:---|:---|:---|:---|
| Tarama | Zamanlanmış taramayı yalnızca bilgisayar üzerindeyken ama kullanımda değilken başlatma | Bilgisayar üzerinde olmadığı ancak kullanımda olmadığı sürece, zamanlanmış taramalar çalışmaz | Etkin |

> [!NOTE]
> Uç noktaların kullanım içinde olmadığınız zamanlarda taramalar zamanlarken, taramalar CPU azaltma yapılandırmasına uygun değildir ve taramayı mümkün olan en hızlı şekilde tamamlamak için mevcut kaynaklardan tam olarak yararlanacak.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>Düzeltme için gereken taramaları zamanlama grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmamışsa) |
|---|---|---|---|
| Düzeltme | Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için haftanın günlerini belirtme | Taramayı çalıştıracak günü belirtin (veya hiç belirtme). | Hiçbir zaman |
| Düzeltme | Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için günün saatlerini belirtme | Gece yarısından sonra kaç dakika sonra olduğunu belirtme (örneğin, **01:00 için 60** girin) | 02:00 |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>Günlük taramaları zamanlamayı grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmamışsa) |
|:---|:---|:---|:---|
| Tarama | Günde hızlı taramalar çalıştırmak için aralığı belirtme | Bir sonraki hızlı taramadan önce kaç saat gerektir gerektiğini belirtin. Örneğin, her iki saatte bir çalıştırmak için **, 2** girin; günde bir kez **24 girin**. Günlük **hızlı taramayı** hiçbir zaman çalıştırmak için 0 girin. | Hiçbir zaman |
| Tarama | Günlük hızlı tarama için saati belirtme | Gece yarısından sonra kaç dakika sonra olduğunu belirtme (örneğin, **01:00 için 60** girin) | 02:00 |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>Koruma güncelleştirmeleri sonrasında taramaları zamanlamayı planlamak için Grup İlkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmamışsa)|
|:---|:---|:---|:---|
| İmza güncelleştirmeleri | Güvenlik zekası güncelleştirmesi sonrasında taramayı açma | Yeni bir koruma güncelleştirmesi indirildikten hemen sonra tarama işlemi gerçekleşir | Etkin |

