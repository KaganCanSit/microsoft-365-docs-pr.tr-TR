---
title: Temel güvenlik Uç Nokta için Microsoft Defender uyumluluğu artırma
description: Temel Uç Nokta için Microsoft Defender, en iyi korumayı sağlamak için güvenlik denetimlerini ayarlar.
keywords: Intune yönetimi, Uç Nokta için Microsoft Defender, Microsoft Defender, Uç Nokta için Microsoft Defender ASR, güvenlik temeli
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1980567c93364f35923a9a7f2433733e05878e61
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467983"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Temel güvenlik Uç Nokta için Microsoft Defender uyumluluğu artırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Güvenlik taban çizgisi, güvenlik özelliklerinin hem güvenlik uzmanlarının hem de uzman ve sistem yöneticilerinin kılavuzlarına Windows emin olur. Dağıtıldığında, en iyi korumayı sağlamak için Uç nokta güvenlik temeli için Defender, Uç nokta güvenlik denetimleri için Defender'ı ayarlar.

Güvenlik taban çizgilerini ve bunların yapılandırma profillerini kullanarak nasıl Intune için bu SSS [bölümünü okuyun](/intune/security-baselines#q--a).

Güvenlik taban çizgilerine uyumluluğu dağıtmadan ve izlemeden önce:

- [Cihazlarınızı okul yönetimine Intune kaydetme](configure-machines.md#enroll-devices-to-intune-management)
- [Gerekli izinlere sahip olduğundan emin olun](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Güvenlik Uç Nokta için Microsoft Defender temelleri Windows Intune karşılaştırma

Windows Intune güvenlik temeli, tarayıcı ayarları, PowerShell ayarları ve Microsoft Defender Virüsten Koruma gibi bazı güvenlik özellikleri için ayarlar da dahil olmak üzere, Windows çalıştıran cihazları güvenli bir şekilde yapılandırmak için gereken kapsamlı bir önerilen ayarlar Microsoft Defender Virüsten Koruma. Buna karşılık, Uç nokta için Defender taban çizgisi, uç noktada algılama ve yanıtlama (EDR) ayarları ile aynı zamanda Windows Intune güvenlik temeli içinde bulunan ayarlar da dahil olmak üzere Uç nokta için Defender yığınında tüm güvenlik denetimlerini en iyi duruma Windows Intune ayarlar sağlar. Her taban çizgisi hakkında daha fazla bilgi için bkz:

- [Windows için güvenlik temeli ayarlarını Intune](/intune/security-baseline-settings-windows)
- [Uç Nokta için Microsoft Defender için temel Intune](/intune/security-baseline-settings-defender-atp)

İdeal olarak, Uç nokta için Defender'a ekli cihazlar, başlangıçta Windows'in güvenliğini sağlamak için Windows Intune güvenlik temeli ve uç nokta güvenlik denetimleri için Defender'ı en iyi şekilde yapılandırmak üzere en üstteki uç nokta güvenlik temeli için Defender.) dağıtılır. Riskler ve tehditlerle ilgili en son verilerden faydalanmek ve taban çizgisi geliştikçe çakışmaları en aza indirmek için, piyasaya çıktıları yayımlanan tüm ürünlerde taban çizgilerinin en son sürümlerini her zaman kullanın.

> [!NOTE]
> Uç nokta güvenlik temeli için Defender fiziksel cihazlar için iyileştirilmiştir ve şu anda sanal makine (VMs) veya VDI uç noktalarında kullanmak için önerilmez. Bazı taban çizgisi ayarları, sanallaştırılmış ortamlardaki uzak etkileşimli oturumları etkileyenin.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Uç nokta güvenlik temeli için Defender'a uyumluluğu izleme

Cihaz **yapılandırma yönetimine** [ilişkin güvenlik](configure-machines.md) taban çizgisi kartı, uç nokta güvenlik Windows 10 Için Defender Windows 11 atanmış cihazlar genelinde uyumlulukla ilgili genel bir bakış sağlar.

:::image type="content" source="images/secconmgmt_baseline_card.png" alt-text="Güvenlik taban çizgisi kartı" lightbox="images/secconmgmt_baseline_card.png":::

*Uç nokta güvenlik temeli için Defender'a uyumluluğu gösteren kart*

Her cihaza aşağıdaki durum türlerinden biri verilir:

- **Taban çizgisiyle** eşler: Cihaz ayarları, taban çizgisinin tüm ayarlarıyla eşler.
- **Taban çizgisi eşleşmez**: En az bir cihaz ayarı taban çizgisiyle eş değildir.
- **Yanlış Yapılandırılmış: En** az bir temel ayarı cihazda düzgün yapılandırılmamış ve çakışma, hata veya bekleme durumuna göredir.
- **Uygulanamaz**: Cihazda en az bir taban çizgisi ayarı geçerli değildir.

Belirli cihazları gözden geçirmek için kart **üzerinde Güvenlik temeli yapılandır'ı** seçin. Bu sizi cihaz yönetimine Intune alır. Buradan, cihazların **adları ve** durumları için Cihaz durumu'seçin.

> [!NOTE]
> Cihaz yapılandırma yönetimi sayfasında görüntülenen toplanan verilerde ve cihaz yapılandırma yönetim sayfasında genel bakış ekranlarında görüntülenen verilerde farklılıklar Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Temel güvenlik Uç Nokta için Microsoft Defender gözden geçirme ve atama

Cihaz yapılandırma yönetimi, yalnızca güvenlik Windows 10 temel Windows 11 atanmış olan tüm cihaz ve cihaz Uç Nokta için Microsoft Defender izler. Temeli rahatça gözden geçirebilirsiniz ve uygun bir şekilde cihaz yönetimiyle Intune atabilirsiniz.

1. Cihaz **yönetimiyle ilgili daha** fazla **bilgi için Güvenlik temeli** kartında Güvenlik temeli Intune seçin. Temel uyumluluğuna benzer bir genel bakış görüntülenir.

   > [!TIP]
   > Alternatif olarak, Tüm hizmetler ve Cihaz güvenliği > Microsoft Defender ATP temeli için, Microsoft Azure portalında Uç nokta güvenlik temeli için Defender> Intune > Uç nokta **güvenlik > > Defender'a gidin**.

2. Yeni profil oluşturma.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile1.png" alt-text="Web siteniz için güvenlik Uç Nokta için Microsoft Defender temele genel bakış altında Profil Intune" lightbox="images/secconmgmt_baseline_intuneprofile1.png":::<br>
   *Uç Nokta için Microsoft Defender temele genel bakış Intune*

3. Profil oluşturma sırasında, temel üzerinde belirli ayarları gözden geçirebilirsiniz ve ayarlayabilirsiniz.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile2.png" alt-text="Temel çalışma sırasında profil oluşturma sırasında güvenlik temeli Intune" lightbox="images/secconmgmt_baseline_intuneprofile2.png":::<br>
   *E-Intune'de profil oluşturma sırasında güvenlik temeli Intune*

4. Profili uygun cihaz grubuna attayabilirsiniz.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile3.png" alt-text="Temel güvenlik taban çizgisi Intune" lightbox="images/secconmgmt_baseline_intuneprofile3.png":::<br>
   *Temel çalışma alanına güvenlik temeli profili Intune*

5. Profili oluşturmak için kaydedin ve atanan cihaz grubuna dağıtın.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile4.png" alt-text="Temel güvenlik temeli atama Intune" lightbox="images/secconmgmt_baseline_intuneprofile4.png":::<br>
   *Temel veride güvenlik temeli profili Intune*

> [!TIP]
> Temel güvenlik Intune cihazlarınızı kapsamlı olarak korumak ve korumak için kullanışlı bir yol sağlar. [Temel güvenlik taban çizgisi hakkında daha fazla bilgi Intune](/intune/security-baselines).

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
- [Cihaz ekleme ve Uç Nokta için Microsoft Defender](configure-machines-onboarding.md)
- [ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme](configure-machines-asr.md)
