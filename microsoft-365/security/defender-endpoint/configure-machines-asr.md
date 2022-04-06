---
title: ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme
description: Tipik kötü amaçlı yazılım açıklarını tanımlamak ve önlemek için saldırı alanı azaltma (ASR) kurallarınızı en iyi duruma getirme.
keywords: onboard, Intune yönetimi, Uç Nokta için Microsoft Defender, Microsoft Defender, Windows Defender, saldırı yüzeyini azaltma, ASR, güvenlik temeli
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d2bf9a6fa1f874e7d550d0d0f7a42742a07665eb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468269"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Saldırı yüzeyini azaltma (ASR) kuralları, tipik](./attack-surface-reduction.md) kötü amaçlı yazılım açıklarını tespit eder ve engeller. Kötü amaçlı olabilecek kodun ne zaman ve nasıl çalıştırılayabileceklerini kontrol etmek için bu kodlar gerekir. Örneğin, JavaScript veya VBScript'in indirilen yürütülebilir dosyayı başlatmasını engelleyebilir, Office makrolarından Win32 API aramalarını engelleyebilir ve USB sürücülerinden çalıştırilen işlemleri engelleyebilirler.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Saldırı yüzeyi yönetim kartı" lightbox="../../media/attack-surface-mgmt.png":::
<br>
*Saldırı yüzeyi yönetim kartı*

*Attack surface yönetim kartı*, aşağıdakiler için kullanabileceğiniz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">araçlara</a> bir giriş noktasıdır:

* ASR kurallarının şu anda kuruluşta nasıl dağıtıldıklarını anlıyoruz.
* ASR algılamalarını gözden geçirme ve olası yanlış algılamaları belirleme.
* Dışlamaların etkisini çözümle ve dışlamak için dosya yollarının listesini oluştur.

Saldırı **yüzeyi yönetimi Raporları Saldırı yüzeyini azaltma** \> **kuralları Dışlama** \> **ekle'yi** \> **seçin**. Orada, portalda diğer bölümlere Microsoft 365 Defender.

:::image type="content" source="images/secconmgmt_asr_m365exlusions.png" alt-text="Microsoft 365 Defender portalında yer alan Saldırı yüzeyini azaltma kuralları sayfasındaki Dışlama ekle sekmesi" lightbox="images/secconmgmt_asr_m365exlusions.png":::<br>
Microsoft 365 Defender *portalında Saldırı yüzeyini azaltma kuralları sayfasındaki Özel Microsoft 365 Defender sekmesi*

> [!NOTE]
> Bir portala Microsoft 365 Defender için bir Microsoft 365 E3 E5 lisansınız ve Azure Active Directory'de belirli rolleri olan bir Azure Active Directory. [Gerekli lisanslar ve izinler hakkında bilgi alın](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Bir portalda ASR kuralı dağıtımı hakkında daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">fazla Microsoft 365 Defender</a> için bkz. [ASR kuralı dağıtımını ve algılamalarını izleme ve yönetme](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**İlgili konular**

* [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
* [Cihaz ekleme ve Uç Nokta için Microsoft Defender](configure-machines-onboarding.md)
* [Temel güvenlik Uç Nokta için Microsoft Defender uyumluluğu izleme](configure-machines-security-baseline.md)
