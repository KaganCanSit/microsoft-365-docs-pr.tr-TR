---
title: ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme
description: Tipik kötü amaçlı yazılım açıklarını tanımlamak ve önlemek için saldırı alanı azaltma (ASR) kurallarınızı en iyi duruma getirme.
keywords: onboard, Intune yönetimi, Endpoint için Microsoft Defender, Microsoft Defender, Windows Defender, saldırı yüzeyini azaltma, ASR, güvenlik temeli
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
ms.openlocfilehash: bd5b88c5d43f2ec20c200ee55458e2ef204775ae
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998050"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Saldırı yüzeyini azaltma (ASR) kuralları, tipik](./attack-surface-reduction.md) kötü amaçlı yazılım açıklarını tespit eder ve engeller. Kötü amaçlı olabilecek kodun ne zaman ve nasıl çalıştırılayabileceklerini kontrol etmek için bu kodlar gerekir. Örneğin, JavaScript veya VBScript'in indirilen yürütülebilir dosyayı başlatmasını engelleyebilir, Office makrolarından Win32 API aramalarını engelleyebilir ve USB sürücülerinden çalıştırilen işlemleri engelleyebilirler.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Saldırı yüzeyi yönetim kartı.":::
<br>
*Saldırı yüzeyi yönetim kartı*

*Attack surface yönetim kartı*, aşağıdakiler için kullanabileceğiniz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">araçlara</a> bir giriş noktasıdır:

* ASR kurallarının şu anda kuruluşta nasıl dağıtıldıklarını anlıyoruz.
* ASR algılamalarını gözden geçirme ve olası yanlış algılamaları belirleme.
* Dışlamaların etkisini çözümle ve dışlamak için dosya yollarının listesini oluştur.

Saldırı **yüzeyi yönetimi Raporları Saldırı yüzeyini azaltma** \> **kuralları Dışlama** \> **ekle'yi** \> **seçin**. Orada, portalda diğer bölümlere Microsoft 365 Defender.

![Microsoft 365 Defender portalında Saldırı yüzeyini azaltma kuralları sayfasındaki Dışlama ekle sekmesi.](images/secconmgmt_asr_m365exlusions.png)<br>
Microsoft 365 Defender *portalında Saldırı yüzeyini azaltma kuralları sayfasındaki Özel Microsoft 365 Defender sekmesi*

> [!NOTE]
> Bir portala Microsoft 365 Defender için bir Microsoft 365 E3 E5 lisansınız ve Azure Active Directory'de belirli rolleri olan bir Azure Active Directory. [Gerekli lisanslar ve izinler hakkında bilgi alın](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Bir portalda ASR kuralı dağıtımı hakkında daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">fazla Microsoft 365 Defender</a> için bkz. [ASR kuralı dağıtımını ve algılamalarını izleme ve yönetme](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**İlgili konular**

* [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
* [Uç nokta için Microsoft Defender'a cihaz ekleme](configure-machines-onboarding.md)
* [Uç nokta güvenlik temeli için Microsoft Defender'a uyumluluğu izleme](configure-machines-security-baseline.md)
