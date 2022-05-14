---
title: İstemci davranışsal engelleme
description: İstemci davranış engellemesi, Uç Nokta için Microsoft Defender davranış engelleme ve kapsama özelliklerinin bir parçasıdır
keywords: davranış engelleme, hızlı koruma, istemci davranışı, Uç Nokta için Microsoft Defender
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
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 95c138b6613d610520a4e6870ae7a59b46159f5d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418750"
---
# <a name="client-behavioral-blocking"></a>İstemci davranışsal engelleme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Ortam**
- Windows

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Genel bakış

İstemci davranış engellemesi, Uç Nokta için Defender'daki [davranış engelleme ve kapsama özelliklerinin](behavioral-blocking-containment.md) bir bileşenidir. Cihazlarda şüpheli davranışlar algılandığından (istemciler veya uç noktalar olarak da adlandırılır), yapıtlar (dosyalar veya uygulamalar gibi) engellenir, denetlenir ve otomatik olarak düzeltilir.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Bulut ve istemci koruması" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Virüsten koruma, bulut korumasıyla eşleştirildiğinde en iyi şekilde çalışır.

## <a name="how-client-behavioral-blocking-works"></a>İstemci davranış engellemesi nasıl çalışır?

[Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md) bir cihazda şüpheli davranışı, kötü amaçlı kodu, dosyasız ve bellek içi saldırıları ve daha fazlasını algılayabilir. Şüpheli davranışlar algılandığında, Microsoft Defender Virüsten Koruma bu şüpheli davranışları ve işlem ağaçlarını izler ve bulut koruma hizmetine gönderir. Makine öğrenmesi, kötü amaçlı uygulamalarla iyi davranışları milisaniyeler içinde ayırt eder ve her yapıtı sınıflandırır. Neredeyse gerçek zamanlı olarak, bir yapıt kötü amaçlı olarak bulunduğunda cihazda engellenir.

Şüpheli bir davranış algılandığında bir [uyarı](alerts-queue.md) oluşturulur ve saldırı algılanıp durdurulurken görünür; gibi uyarılar tetiklenir ve [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) (eski adıyla Microsoft 365 Defender) görüntülenir.

İstemci davranış engellemesi, bir saldırının başlatılmasını önlemeye yardımcı olmakla kalmaz, yürütülmeye başlayan bir saldırının durdurulmasını da sağlayabilir. Geri [bildirim döngüsü engellemesi](feedback-loop-blocking.md) (davranış engelleme ve kapsama özelliğinin başka bir özelliği) sayesinde, kuruluşunuzdaki diğer cihazlarda saldırılar engellenir.

## <a name="behavior-based-detections"></a>Davranış tabanlı algılamalar

Davranış tabanlı algılamalar, [Enterprise için MITRE ATT&CK Matrisine](https://attack.mitre.org/matrices/enterprise) göre adlandırılır. Adlandırma kuralı, kötü amaçlı davranışın gözlemlendiği saldırı aşamasını belirlemeye yardımcı olur:

|Taktik|Algılama tehdidi adı|
|---|---|
|İlk Erişim|`Behavior:Win32/InitialAccess.*!ml`|
|Yürütme|`Behavior:Win32/Execution.*!ml`|
|Kalıcılık|`Behavior:Win32/Persistence.*!ml`|
|Ayrıcalık Yükseltme|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Savunma Kaçamak|`Behavior:Win32/DefenseEvasion.*!ml`|
|Kimlik Bilgisi Erişimi|`Behavior:Win32/CredentialAccess.*!ml`|
|Keşif|`Behavior:Win32/Discovery.*!ml`|
|YanAl Hareket|`Behavior:Win32/LateralMovement.*!ml`|
|Koleksiyon|`Behavior:Win32/Collection.*!ml`|
|Komut ve Denetim|`Behavior:Win32/CommandAndControl.*!ml`|
|Sızdırma|`Behavior:Win32/Exfiltration.*!ml`|
|Etki|`Behavior:Win32/Impact.*!ml`|
|Kategorilenmemiş|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Belirli tehditler hakkında daha fazla bilgi edinmek için bkz. **[son küresel tehdit etkinliği](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>İstemci davranış engellemesini yapılandırma

Kuruluşunuz Uç Nokta için Defender kullanıyorsa istemci davranış engellemesi varsayılan olarak etkindir. Ancak davranış [engelleme ve kapsama](behavioral-blocking-containment.md) dahil olmak üzere tüm Uç Nokta için Defender özelliklerinden yararlanmak için Uç Nokta için Defender'ın aşağıdaki özellik ve özelliklerinin etkinleştirildiğinden ve yapılandırıldığından emin olun:

- [Uç Nokta için Defender temelleri](configure-machines-security-baseline.md)
- [Uç Nokta için Defender'a eklenen cihazlar](onboard-configure.md)
- [Engelleme modunda EDR ](edr-in-block-mode.md)
- [Saldırı yüzeyini azaltma](attack-surface-reduction.md)
- [Yeni nesil koruma](configure-microsoft-defender-antivirus-features.md) (virüsten koruma, kötü amaçlı yazılımdan koruma ve diğer tehdit koruması özellikleri)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
