---
title: Geri bildirim döngüsü engelleme
description: Hızlı koruma olarak da adlandırılan geri bildirim döngüsü engelleme, Uç Nokta için Microsoft Defender'daki davranış engelleme ve koruma yeteneklerinin bir bölümü mü
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
ms.openlocfilehash: 82d5fb32a9535a5b341bca8e5bee989d88ad8232
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997460"
---
# <a name="feedback-loop-blocking"></a>Geri bildirim döngüsü engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

## <a name="overview"></a>Genel bakış

Hızlı koruma olarak da adlandırılan geri bildirim döngüsü engelleme, Uç Nokta için Microsoft [Defender'da](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) davranış engelleme ve koruma yeteneklerine yönelik [bir bileşendir](/windows/security/threat-protection/). Geri bildirim döngüsü engellemeyle, organizasyonu genelindeki cihazlar saldırılardan daha iyi korunur. 

## <a name="how-feedback-loop-blocking-works"></a>Geri bildirim döngüsü engelleme nasıl çalışır?

Başka herhangi bir kişi tarafından olduğu gibi şüpheli bir davranış veya [dosya Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), bu yapıyla ilgili bilgiler birden çok sınıflandırıcıya gönderilir. Hızlı koruma döngü altyapısı, dosyanın engellenmiş olup olmadığı konusunda karar almak için bilgileri diğer sinyallerle inceler ve birbiriyle bağlantılı sağlar. Yapıları denetleme ve sınıflendirme hızlı şekilde gerçekleşir. Bu, onaylanan kötü amaçlı yazılımlara hızlı bir şekilde engel verir ve tüm ekosistem boyunca koruma sağlar. 

Hızlı bir korumayla bir cihaz, kuruluşta diğer cihazlar ve diğer kuruluşlara yönelik bir saldırı, alt yerini genişletmeye çalışıyor.


## <a name="configuring-feedback-loop-blocking"></a>Geri bildirim döngüsü engellemeyi yapılandırma

Kuruluşta Uç Nokta için Defender kullanıyorsa, geri bildirim döngüsü engelleme varsayılan olarak etkindir. Bununla birlikte, hızlı koruma, Defender'ın Uç Nokta özellikleri, makine öğrenme koruma özellikleri ve Microsoft güvenlik hizmetleri genelinde sinyal paylaşımı ile bir arada gerçekleşir. Uç nokta için Defender'ın aşağıdaki özelliklerinin etkinleştirildiğinden ve yapılandırıldığından emin olun:

- [Uç nokta taban çizgisi için Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Uç Nokta için Microsoft Defender'a ekli cihazlar](/microsoft-365/security/defender-endpoint/onboard-configure)

- [EDR modunda çalışma](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Saldırı yüzeyini azaltma](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Yeni nesil koruma (virüsten](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) koruma)

## <a name="related-articles"></a>İlgili makaleler

- [Davranışsal engelleme ve engelleme](behavioral-blocking-containment.md)

- [(Blog) Davranışsal engelleme ve engelleme: Optikleri korumaya dönüştürme](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Uç nokta kaynakları için yararlı Microsoft Defender](/microsoft-365/security/defender-endpoint/helpful-resources)
