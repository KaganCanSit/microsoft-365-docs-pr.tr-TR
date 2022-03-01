---
title: Cihazlarınızı doğru yapılandırıldığından emin olun
description: Cihazları uygun şekilde yapılandırarak tehditlere karşı genel güvenliğinizi geliştirin ve saldırılara algıla ve yanıt verme yeteneğinizi geliştirin.
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 61b275e5e42a10743eee744ab44bce48a25fa2eb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998243"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Cihazlarınızı doğru yapılandırıldığından emin olun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Uygun şekilde yapılandırılan cihazlarla, tehditlere karşı genel güvenliği artırarak saldırılar tespit etme ve yanıt verme yeteneğinizi geliştirebilirsiniz. Güvenlik yapılandırması yönetimi cihazlarınızı şu şekilde sağlamaya yardımcı olur:

- Uç Nokta için Microsoft Defender'a Ekleme
- Uç nokta güvenlik taban çizgisi yapılandırması için Defender'ı karşılama veya aşma
- Stratejik saldırı yüzeyini azaltmaları yerleştirin

Cihaz **yapılandırma yönetimi** sayfasını açmak için, gezinti menüsünde Yapılandırma yönetimi'ne tıklayın.

![Güvenlik yapılandırması yönetimi sayfası.](images/secconmgmt_main.png)

*Cihaz yapılandırma yönetim sayfası*

Kuruluş düzeyinde yapılandırma durumunu izleyebilir ve işe alım kapsamı kötü, uyumluluk sorunları ve iyileştirilmiş saldırı alanı risk azaltmalarına doğrudan, Microsoft Intune ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> cihaz yönetimi sayfalarına yönelik derin bağlantılar aracılığıyla hızlı bir şekilde harekete geçebilirsiniz.

Bunu yaparken, şunları yapma avantajından faydalan oluruz:

- Cihazlarınız üzerinde etkinliklerin kapsamlı görünürlüğü
- Ham etkinlikleri işlemeye, ihlal etkinliğini ve tehdit göstergelerini belirlemeye yönelik güçlü tehdit zekası ve güçlü cihaz öğrenme teknolojileri
- Kötü amaçlı dosyaların yüklemesini, sistem dosyalarını ve işlemlerini ele geçirerek, veri sızıntısını ve diğer tehdit etkinliklerini etkili bir şekilde durdurmak üzere yapılandırılan tam güvenlik özellikleri yığını
- Saldırı yüzeyini azaltmayı en iyi duruma getirmek, tehdit etkinliklerine karşı stratejik savunmayı en üst düzeye çıkarma ve üretkenliği en aza indirme

## <a name="enroll-devices-to-intune-management"></a>Cihazları Intune yönetimine kaydetme

Cihaz yapılandırma yönetimi, intune cihaz yönetimiyle birlikte, kuruluş cihazları ve temel güvenlik yapılandırmasının envanterini oluşturur. Intune tarafından yönetilen cihazlarda yapılandırma sorunlarını izleyebilir ve Windows yönetebilirsiniz.

Cihazlarınızı düzgün yapılandırıldığından emin olmadan önce bunları Intune yönetimine kaydettirin. Intune kaydı güçlü bir kayıttır ve bu kayıt cihazları için Windows vardır. Intune kayıt seçenekleri hakkında daha fazla bilgi için, Diğer cihazlarda [kayıt Windows okuyun](/intune/windows-enroll).

> [!NOTE]
> Cihazları Windows Intune'a kaydetmek için, yöneticilere zaten lisans atanmış olması gerekir. [Cihaz kaydı için lisans atama hakkında bilgi alın](/intune/licenses-assign).

> [!TIP]
> Intune aracılığıyla cihaz yönetimini en iyi duruma getirmek için [Intune'a Uç Nokta için Defender'a bağlanin](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Gerekli izinleri alma

Varsayılan olarak, yalnızca Azure AD'de Genel Yönetici veya Intune Hizmet Yöneticisi rolüne atanmış kullanıcılar, ekleme cihazları için gereken cihaz yapılandırma profillerini yönetebilir ve ataabilir ve güvenlik temeli dağıtabilir.

Size başka roller atanmışsa gerekli izinlere sahip olduğunuzdan emin olun:

- Cihaz yapılandırmaları için tam izinler
- Güvenlik taban çizgilerine tam izinler
- Cihaz uyumluluk ilkeleri için okuma izinleri
- Kuruluş izinlerini okuma

![Intune üzerinde gerekli izinler.](images/secconmgmt_intune_permissions.png)

*Intune'da cihaz yapılandırma izinleri*

> [!TIP]
> Intune'da izin atama hakkında daha fazla bilgi edinmek [için özel roller oluşturma hakkında bilgi okuyun](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>Bu bölümde

Konu|Açıklama
:---|:---
[Cihazları Uç Nokta için Defender'a ekleme](configure-machines-onboarding.md)|Intune tarafından yönetilen cihazların ekleme durumunu takip edin ve Intune aracılığıyla daha fazla cihaz ekleme. 
[Uç nokta güvenlik temeli için Defender'a uyumluluğu artırma](configure-machines-security-baseline.md)|Taban çizgisi uyumluluğunu ve uyumluluğunu takip edin. Güvenlik taban çizgisini daha fazla Intune tarafından yönetilen cihaza dağıtın.
[ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme](configure-machines-asr.md)|Microsoft 365 Defender portalında etki çözümleme araçlarını kullanarak kural dağıtımını ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">ince Microsoft 365 Defender gözden geçirebilirsiniz</a>.

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
