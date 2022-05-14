---
title: grup ilkesi kullanarak virüsten koruma taramaları zamanlama
description: Virüsten koruma taramalarını ayarlamak için grup ilkesi kullanma
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
ms.openlocfilehash: 21b30bc9ce43c4d6a04e6e6e33f55f6d8e3d6d1b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415528"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>grup ilkesi kullanarak virüsten koruma taramaları zamanlama

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Bu makalede, grup ilkesi kullanarak zamanlanmış taramaların nasıl yapılandırıldığı açıklanır. Taramaları zamanlama ve tarama türleri hakkında daha fazla bilgi edinmek için bkz[. Zamanlanmış hızlı veya tam Microsoft Defender Virüsten Koruma taramalarını yapılandırma](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>grup ilkesi kullanarak virüsten koruma taramalarını yapılandırma

1. grup ilkesi yönetim makinenizdeki grup ilkesi Düzenleyicisi'nde **Bilgisayar yapılandırması** \> **Yönetim Şablonları** \> **Windows Bileşenleri** \> **Microsoft Defender Virüsten Koruma Tarama'ya** \> gidin.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. grup ilkesi Nesnesi için ayarları belirtin ve ardından **Tamam'ı** seçin. 

4. Yapılandırmak istediğiniz her ayar için 1-4 arası adımları yineleyin.

5. grup ilkesi Nesnenizi normal şekilde dağıtın. grup ilkesi Nesneleri ile ilgili yardıma ihtiyacınız varsa bkz. [grup ilkesi Nesnesi Oluşturma](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Zamanlanmış taramaları yapılandırırken, **Zamanlanmış taramayı yalnızca bilgisayar açıkken ancak kullanımda değilken başlat** ayarı varsayılan olarak etkindir, makinenin önce boşta olmasını gerektirerek beklenen zamanlanmış süreyi etkileyebilir.
>
> Haftalık taramalar için, Windows Sunucusu'nda varsayılan davranış, makine boştayken otomatik bakımın dışında tarama yapmaktır. Windows 10 ve sonraki sürümlerde varsayılan ayar, makine boştayken otomatik bakım sırasında tarama yapmaktır. Bu davranışı değiştirmek için **ScanOnlyIfIdle'ı** devre dışı bırakarak ayarları değiştirin ve ardından bir zamanlama tanımlayın.

Daha fazla bilgi için [Koruma güncelleştirmelerinin ne zaman indirilip uygulanacağını yönetme ve](manage-protection-update-schedule-microsoft-defender-antivirus.md) [Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya değiştirmesine izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md) konularına bakın.

## <a name="group-policy-settings-for-scheduling-scans"></a>Taramaları zamanlamak için grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmadıysa) |
|:---|:---|:---|:---|
| Tarama | Zamanlanmış tarama için kullanılacak tarama türünü belirtme | Hızlı tarama |
| Tarama | Zamanlanmış taramanın çalıştırıldığı haftanın gününü belirtme | Tarama çalıştırılacak günü (veya hiçbir zaman) belirtin. | Hiç |
| Tarama | Zamanlanmış taramanın çalıştırıldığı günün saatini belirtme | Gece yarısından sonraki dakika sayısını belirtin (örneğin, 01: **00 için 60** girin). | 2:00'de. |
| Kök | Zamanlanmış görev sürelerini rastgele belirleme |Microsoft Defender Virüsten Koruma, taramanın başlangıç saatini 0 ile 23 saat arasında herhangi bir zaman aralığına rastgele olarak ayarlayın. <p>[SCEP'te](/mem/intune/protect/certificates-scep-configure) taramaları herhangi bir aralık artı veya eksi 30 dakikaya rastgele ayarlayın. Bu, sanal makinelerde veya VDI dağıtımlarında yararlı olabilir. | Etkin |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>Uç nokta kullanımda olmadığında taramaları zamanlamak için grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmadıysa) |
|:---|:---|:---|:---|
| Tarama | Zamanlanmış taramayı yalnızca bilgisayar açıkken ancak kullanımda değilken başlatın | Bilgisayar açık ancak kullanımda olmadığı sürece zamanlanmış taramalar çalıştırılmaz | Etkin |

> [!NOTE]
> Uç noktaların kullanımda olmadığı zamanlar için taramalar zamanladığınızda, taramalar CPU azaltma yapılandırmasına uygun değildir ve taramayı mümkün olan en hızlı şekilde tamamlamak için kullanılabilir kaynaklardan tam olarak yararlanır.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>Düzeltme gerektiren taramaları zamanlamak için grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmadıysa) |
|---|---|---|---|
| Düzeltme | Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için haftanın gününü belirtin | Tarama çalıştırılacak günü (veya hiçbir zaman) belirtin. | Hiç |
| Düzeltme | Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için günün saatini belirtin | Gece yarısından sonraki dakika sayısını belirtin (örneğin, 1 için **60** girin.) | 2:00'de. |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>Günlük taramaları zamanlamak için grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmadıysa) |
|:---|:---|:---|:---|
| Tarama | Her gün hızlı tarama çalıştırmak için aralığı belirtin | Sonraki hızlı taramadan önce kaç saat geçmesi gerektiğini belirtin. Örneğin, iki saatte bir çalıştırmak için günde bir kez **olmak üzere 2** girin **, 24** girin. Günlük hızlı taramayı asla çalıştırmamak için **0** girin. | Hiç |
| Tarama | Günlük hızlı tarama süresini belirtme | Gece yarısından sonraki dakika sayısını belirtin (örneğin, 1 için **60** girin.) | 2:00'de. |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>Koruma güncelleştirmelerinden sonra taramaları zamanlamak için grup ilkesi ayarları

| Konum | Ayar | Açıklama | Varsayılan ayar (yapılandırılmadıysa)|
|:---|:---|:---|:---|
| İmza güncelleştirmeleri | Güvenlik bilgileri güncelleştirmesinin ardından taramayı açma | Yeni bir koruma güncelleştirmesi indirildikten hemen sonra tarama gerçekleşir | Etkin |

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)