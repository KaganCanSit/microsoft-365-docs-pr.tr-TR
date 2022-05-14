---
title: Geri bildirim döngüsü engelleme
description: Hızlı koruma olarak da adlandırılan geri bildirim döngüsü engelleme, Uç Nokta için Microsoft Defender
keywords: davranış engelleme, hızlı koruma, geri bildirim engelleme, Uç Nokta için Microsoft Defender
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: da3f16837b8715fe791fbd8abf48acb657fd4963
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416782"
---
# <a name="feedback-loop-blocking"></a>Geri bildirim döngüsü engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

## <a name="overview"></a>Genel bakış

Hızlı koruma olarak da adlandırılan geri bildirim döngüsü engelleme, [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/) [davranış engelleme ve kapsama özelliklerinin](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) bir bileşenidir. Geri bildirim döngüsü engelleme sayesinde kuruluşunuz genelindeki cihazlar saldırılara karşı daha iyi korunur. 

## <a name="how-feedback-loop-blocking-works"></a>Geri bildirim döngüsü engelleme nasıl çalışır?

[Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) gibi şüpheli bir davranış veya dosya algılandığında, bu yapıt hakkındaki bilgiler birden çok sınıflandırıcıya gönderilir. Hızlı koruma döngüsü altyapısı, bir dosyanın engellenip engellenmeyeceğine ilişkin bir karara varmak için bilgileri inceler ve diğer sinyallerle ilişkilendirır. Yapıtları denetleme ve sınıflandırma işlemi hızlı bir şekilde gerçekleşir. Onaylanan kötü amaçlı yazılımların hızlı bir şekilde engellenmesine neden olur ve tüm ekosistem genelinde korumayı destekler. 

Hızlı koruma uygulandığında saldırı, bir cihazda, kuruluştaki diğer cihazlarda ve diğer kuruluşlardaki cihazlarda durdurulabilir ve saldırı, koruma alanını genişletmeye çalışır.


## <a name="configuring-feedback-loop-blocking"></a>Geri bildirim döngüsünü engellemeyi yapılandırma

Kuruluşunuz Uç Nokta için Defender kullanıyorsa, geri bildirim döngüsü engellemesi varsayılan olarak etkindir. Ancak hızlı koruma, Uç Nokta için Defender özellikleri, makine öğrenmesi koruma özellikleri ve Microsoft güvenlik hizmetleri arasında sinyal paylaşımının bir birleşimiyle gerçekleşir. Uç Nokta için Defender'ın aşağıdaki özelliklerinin etkinleştirildiğinden ve yapılandırıldığından emin olun:

- [temelleri Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Uç Nokta için Microsoft Defender eklenen cihazlar](/microsoft-365/security/defender-endpoint/onboard-configure)

- [Engelleme modunda EDR ](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Saldırı yüzeyini azaltma](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Yeni nesil koruma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (virüsten koruma)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Davranışsal engelleme ve kapsama](behavioral-blocking-containment.md)

- [(Blog) Davranışsal engelleme ve kapsama: Optikleri korumaya dönüştürme](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Yararlı Uç Nokta için Microsoft Defender kaynakları](/microsoft-365/security/defender-endpoint/helpful-resources)
