---
title: İstemci davranışı engelleme
description: İstemci davranışı engelleme, müşteriyi engelleme ve engellemenin bir Uç Nokta için Microsoft Defender
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
ms.openlocfilehash: 8da3f04af66568bbe79dd6a74c38b30a8a1ab891
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470229"
---
# <a name="client-behavioral-blocking"></a>İstemci davranışı engelleme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Genel bakış

İstemci davranışı engellemesi, Uç Nokta için [Defender'daki](behavioral-blocking-containment.md) davranış engelleme ve içerirlik yeteneklerinin bir bileşenidir. Cihazlarda (istemci veya uç nokta olarak da adlandırılan) şüpheli davranışlar algılandığından, yapılar (dosyalar veya uygulamalar gibi) engellenir, denetlenir ve otomatik olarak düzeltilir.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Bulut ve istemci koruması" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Virüsten koruma, bulut korumasıyla eşleştirilmiş olarak en iyi şekilde çalışır.

## <a name="how-client-behavioral-blocking-works"></a>İstemci davranışı engelleme nasıl çalışır?

[Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md) bir cihazda şüpheli davranışı, kötü amaçlı kodu, dosyasız ve bellek içinde saldırılarını ve daha fazlasını algılanabilir. Şüpheli davranışlar algılandığında, Microsoft Defender Virüsten Koruma bu şüpheli davranışları ve işlem ağaçlarını bulut koruma hizmetine izler ve gönderir. Makine öğrenimi, mili saniye cinsinden kötü amaçlı uygulamalarla iyi davranışlar arasında ayrım sağlar ve her yapıyı sınıflara böler. Yapı, zararlı olduğu bulunan yapı, neredeyse gerçek zamanlı olarak cihazda engellenir.

Şüpheli bir davranış algılandığında bir uyarı oluşturulur ve [](alerts-queue.md) Saldırı algılandığında ve durdurulurken "ilk erişim uyarısı" gibi uyarılar [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) (eski adı Microsoft 365 Defender) tetiklenir ve görünür.

İstemci davranış engellemesi, yalnızca bir saldırının başlamasını önlemeye yardımcı olmakla birlikte yürütmeye başlayan bir saldırıyı durdurmanıza da yardımcı olur. Geri bildirim [döngüsü engelleme ile](feedback-loop-blocking.md) de (davranışa yönelik engelleme ve içeren başka bir özellik) saldırılar, organizasyonlu diğer cihazlarda önlenebilir.

## <a name="behavior-based-detections"></a>Davranış tabanlı algılamalar

Davranış tabanlı algılamalar, bu algılamalar için [MITRE ATT&CK Matrisi'ne Enterprise](https://attack.mitre.org/matrices/enterprise). Adlandırma kuralı kötü amaçlı davranışın gözlemlenen saldırı aşamalarını belirlemeye yardımcı olur:

|Tactic|Algılama tehdit adı|
|---|---|
|Initial Access|`Behavior:Win32/InitialAccess.*!ml`|
|Yürütme|`Behavior:Win32/Execution.*!ml`|
|Kalıcılık|`Behavior:Win32/Persistence.*!ml`|
|Ayrıcalık Yükseltme|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Savunma Savunma|`Behavior:Win32/DefenseEvasion.*!ml`|
|Kimlik Bilgilerine Erişim|`Behavior:Win32/CredentialAccess.*!ml`|
|Keşif|`Behavior:Win32/Discovery.*!ml`|
|Lateral Movement|`Behavior:Win32/LateralMovement.*!ml`|
|Koleksiyon|`Behavior:Win32/Collection.*!ml`|
|Komut ve Denetim|`Behavior:Win32/CommandAndControl.*!ml`|
|Exfiltration|`Behavior:Win32/Exfiltration.*!ml`|
|Etki|`Behavior:Win32/Impact.*!ml`|
|Uncategorized|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Belirli tehditler hakkında daha fazla bilgi edinmek için son **[küresel tehdit etkinliklerine bakın](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>İstemci davranış engellemesini yapılandırma

Kuruluşta Uç Nokta için Defender kullanıyorsa, istemci davranışı engelleme varsayılan olarak etkindir. Öte yandan, davranış engelleme ve dahil olmak üzere Uç Nokta için Defender'ın tüm özelliklerinden yararlanmak [için, Uç](behavioral-blocking-containment.md) Nokta için Defender'ın etkinleştirildiğinden ve yapılandırıldığından emin olun:

- [Uç nokta taban çizgisi için Defender](configure-machines-security-baseline.md)
- [Uç Nokta için Defender'a yerleşik cihazlar](onboard-configure.md)
- [EDR modunda çalışma](edr-in-block-mode.md)
- [Saldırı yüzeyini azaltma](attack-surface-reduction.md)
- [Yeni nesil koruma](configure-microsoft-defender-antivirus-features.md) (virüsten koruma, kötü amaçlı yazılımdan koruma ve diğer tehdit koruması özellikleri)
