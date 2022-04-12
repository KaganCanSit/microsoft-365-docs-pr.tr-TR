---
title: Microsoft Defender Virüsten Koruma için bulut koruma düzeyini belirtin
description: Microsoft Defender Virüsten Koruma için bulut koruma düzeyinizi ayarlayın.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, saldırganlık, koruma düzeyi
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 6e24be40b4ff9e57d896cf53769b578c482a2c6e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787544"
---
# <a name="specify-the-cloud-protection-level"></a>Bulut koruma düzeyini belirleyin

**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Bulut koruması, geleneksel güvenlik bilgileri güncelleştirmelerinden çok daha hızlı bir şekilde uç noktalarınıza koruma sağlamak için Microsoft Defender Virüsten Koruma ile birlikte çalışır. Microsoft Endpoint Manager (önerilen) veya grup ilkesi kullanarak bulut koruma düzeyinizi yapılandırabilirsiniz.

> [!NOTE]
> **Yüksek**, **Yüksek +** veya **Sıfır toleransı** seçildiğinde bazı meşru dosyalar algılanabilir. Böyle bir durumda, algılanan dosyanın engelini kaldırabilirsiniz veya Microsoft 365 Defender portalında bu algılamaya itiraz edebilirsiniz.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Bulut koruma düzeyini belirtmek için Microsoft Endpoint Manager kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Uç nokta güvenliği** \> **Virüsten Koruma'yı** seçin.

3. Bir virüsten koruma profili seçin. (Henüz bir profiliniz yoksa veya yeni bir profil oluşturmak istiyorsanız bkz[. Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure).

4. **Özellikler**'i seçin. Ardından **Yapılandırma ayarları'nın** yanındaki **Düzenle'yi** seçin.

5. **Bulut koruması'nı** genişletin ve bulut **tabanlı koruma düzeyi** listesinde aşağıdakilerden birini seçin:

    - **Yapılandırılmadı**: Varsayılan durum.
    - **Yüksek**: Güçlü bir algılama düzeyi uygular.
    - **Yüksek artı**: **Yüksek** düzeyi kullanır ve ek koruma önlemleri uygular (istemci performansını etkileyebilir).
    - **Sıfır tolerans**: Tüm bilinmeyen yürütülebilir dosyaları engeller.

6. **Gözden Geçir + kaydet'i** ve ardından **Kaydet'i** seçin.

> [!TIP]
> Yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:
>
> - [Endpoint Protection yapılandırma](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Intune'de uç nokta koruma ayarları ekleme](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Bulut koruma düzeyini belirtmek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar Yapılandırması** \> **Yönetim şablonları'na** gidin.

4. **MpEngine** **Microsoft Defender Virüsten Koruma Bileşenleri** \> **Windows** \> ağacı genişletin.

5. **Bulut koruma düzeyini seçin** ayarına çift tıklayın ve **Etkin** olarak ayarlayın. Koruma düzeyini seçin:

    - **Yapılandırılmadı**: Varsayılan durum.
    - **Varsayılan engelleme düzeyi** , meşru dosyaları algılama riskini artırmadan güçlü algılama sağlar.
    - **Orta engelleme düzeyi** yalnızca yüksek güvenilirlik algılamaları için orta düzey sağlar
    - **Yüksek engelleme düzeyi** , istemci performansını iyileştirirken güçlü bir algılama düzeyi uygular (ancak hatalı pozitifler için size daha fazla şans da verebilir).
    - **Yüksek + engelleme düzeyi** ek koruma önlemleri uygular (istemci performansını etkileyebilir ve hatalı pozitif sonuç alma şansınızı artırabilir).
    - **Sıfır tolerans engelleme düzeyi** tüm bilinmeyen yürütülebilir dosyaları engeller.

6. **Tamam**'ı seçin.

7. Güncelleştirilmiş grup ilkesi Nesnenizi dağıtın. Bkz. [grup ilkesi Yönetim Konsolu](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Şirket içinde grup ilkesi Nesneleri mi kullanıyorsunuz? Bulutta nasıl çeviri yaptıklarını görün. [Microsoft Endpoint Manager - Önizleme'de grup ilkesi analiz kullanarak şirket içi grup ilkesi nesnelerinizi analiz](/mem/intune/configuration/group-policy-analytics) edin.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)
  
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft Defender Virüsten Koruma için bulut korumasının neden etkinleştirilmesi gerekir?](why-cloud-protection-should-be-on-mdav.md)
