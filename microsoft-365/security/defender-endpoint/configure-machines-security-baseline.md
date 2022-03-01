---
title: Uç nokta güvenlik temeli için Microsoft Defender'a uyumluluğu artırma
description: Uç Nokta güvenlik temeli için Microsoft Defender, en iyi korumayı sağlayacak güvenlik denetimlerini ayarlar.
keywords: Intune yönetimi, Uç Nokta için Microsoft Defender, Microsoft Defender, Endpoint ASR için Microsoft Defender, güvenlik temeli
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
ms.openlocfilehash: 95790626461d7db02f3837321e0d9075e0597515
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998242"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Uç nokta güvenlik temeli için Microsoft Defender'a uyumluluğu artırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Güvenlik taban çizgisi, güvenlik özelliklerinin hem güvenlik uzmanlarının hem de uzman ve sistem yöneticilerinin kılavuzlarına Windows emin olur. Dağıtıldığında, en iyi korumayı sağlamak için Uç nokta güvenlik temeli için Defender, Uç nokta güvenlik denetimleri için Defender'ı ayarlar.

Güvenlik taban çizgilerini ve bunların Intune'da yapılandırma profilleri kullanılarak nasıl atanacaklarını anlamak için, [bu SSS bölümünü okuyun](/intune/security-baselines#q--a).

Güvenlik taban çizgilerine uyumluluğu dağıtmadan ve izlemeden önce:

- [Cihazlarınızı Intune yönetimine kaydetme](configure-machines.md#enroll-devices-to-intune-management)
- [Gerekli izinlere sahip olduğundan emin olun](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Uç Nokta için Microsoft Defender ile Intune güvenlik Windows için karşılaştırma

Intune güvenlik Windows, tarayıcı ayarları, PowerShell ayarları ve Microsoft Defender Virüsten Koruma gibi bazı güvenlik özellikleri ayarları da dahil olmak üzere, Windows çalıştıran cihazları güvenli bir şekilde yapılandırmak için gereken kapsamlı bir önerilen ayarlar Microsoft Defender Virüsten Koruma. Buna karşılık, Uç nokta için Defender taban çizgisi, uç noktada algılama ve yanıtlama (EDR) ayarları ile birlikte Windows Intune güvenlik temeli içinde bulunan ayarlar da dahil olmak üzere Uç nokta için Defender yığınında tüm güvenlik denetimlerini en iyi duruma Windows ayarlar sağlar. Her taban çizgisi hakkında daha fazla bilgi için bkz:

- [Windows temel güvenlik temeli ayarlarını değiştirme](/intune/security-baseline-settings-windows)
- [Intune için Uç nokta taban çizgisi ayarları için Microsoft Defender](/intune/security-baseline-settings-defender-atp)

İdeal olarak, Uç nokta için Defender'a ekli cihazlar, başlangıçta Windows'in güvenliğini sağlamak için Windows Intune güvenlik temeli ve Uç nokta güvenlik denetimleri için Defender'ı en iyi şekilde yapılandırmak üzere en üstteki Uç nokta güvenlik temeli için Defender.) dağıtılır. Riskler ve tehditlerle ilgili en son verilerden faydalanmek ve taban çizgisi geliştikçe çakışmaları en aza indirmek için, piyasaya çıktıları yayımlanan tüm ürünlerde taban çizgilerinin en son sürümlerini her zaman kullanın.

> [!NOTE]
> Uç nokta güvenlik temeli için Defender fiziksel cihazlar için iyileştirilmiştir ve şu anda sanal makine (VMs) veya VDI uç noktalarında kullanmak için önerilmez. Bazı taban çizgisi ayarları, sanallaştırılmış ortamlardaki uzak etkileşimli oturumları etkileyenin.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Uç nokta güvenlik temeli için Defender'a uyumluluğu izleme

Cihaz **yapılandırma yönetiminin** güvenlik [](configure-machines.md) taban çizgisi kartı, Uç nokta güvenlik temeli için Defender'ya atanmış Windows 10 Windows ve 11 cihaz genelinde uyumlulukla ilgili genel bir bakış sağlar.

![Güvenlik taban çizgisi kartı.](images/secconmgmt_baseline_card.png)

*Uç nokta güvenlik temeli için Defender'a uyumluluğu gösteren kart*

Her cihaza aşağıdaki durum türlerinden biri verilir:

- **Taban çizgisiyle** eşler: Cihaz ayarları, taban çizgisinin tüm ayarlarıyla eşler.
- **Taban çizgisi eşleşmez**: En az bir cihaz ayarı taban çizgisiyle eş değildir.
- **Yanlış Yapılandırılmış: En** az bir temel ayarı cihazda düzgün yapılandırılmamış ve çakışma, hata veya bekleme durumuna göredir.
- **Uygulanamaz**: Cihazda en az bir taban çizgisi ayarı geçerli değildir.

Belirli cihazları gözden geçirmek için kart **üzerinde Güvenlik temeli yapılandır'ı** seçin. Bu sizi Intune cihaz yönetimine alır. Buradan, cihazların **adları ve** durumları için Cihaz durumu'seçin.

> [!NOTE]
> Cihaz yapılandırma yönetimi sayfasında görüntülenen toplanan verilerde ve Intune'da genel bakış ekranlarında görüntülenen verilerde farklılıklarla görebilirsiniz.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Uç nokta güvenlik temeli için Microsoft Defender'ı gözden geçirme ve atama

Cihaz yapılandırma yönetimi yalnızca Uç nokta güvenlik Windows 10 için Microsoft Defender Windows 11 cihazın temel uyumluluğunu izler. Taban çizgisini rahatça gözden geçirebilirsiniz ve Intune cihaz yönetiminde cihazlara atabilirsiniz.

1. Intune **cihaz** **yönetimine gitmek için Güvenlik** taban çizgisi kartında Güvenlik temeli yapılandır'ı seçin. Temel uyumluluğuna benzer bir genel bakış görüntülenir.

   > [!TIP]
   > Alternatif olarak, Tüm hizmetler > **Intune > Cihaz güvenliği > Microsoft Defender ATP** temeli için güvenlik taban çizgisi üzerinden Microsoft Azure portalında Uç nokta için Defender güvenlik >'ne gidin.

2. Yeni profil oluşturma.

   ![Intune'da Uç nokta güvenlik temeli için Microsoft Defender'a genel bakış.](images/secconmgmt_baseline_intuneprofile1.png)<br>
   *Intune'da Uç Nokta güvenlik temeli için Microsoft Defender'a genel bakış*

3. Profil oluşturma sırasında, temel üzerinde belirli ayarları gözden geçirebilirsiniz ve ayarlayabilirsiniz.

   ![Intune'da profil oluşturma sırasında güvenlik temeli seçenekleri.](images/secconmgmt_baseline_intuneprofile2.png)<br>
   *Intune'da profil oluşturma sırasında güvenlik temeli seçenekleri*

4. Profili uygun cihaz grubuna attayabilirsiniz.

   ![Intune'daki güvenlik temeli profilleri.](images/secconmgmt_baseline_intuneprofile3.png)<br>
   *Intune'da güvenlik temeli profili atama*

5. Profili oluşturmak için kaydedin ve atanan cihaz grubuna dağıtın.

   ![Intune'da güvenlik temeli atama.](images/secconmgmt_baseline_intuneprofile4.png)<br>
   *Intune'da güvenlik temeli profili oluşturma*

> [!TIP]
> Intune'daki güvenlik taban çizgisi, cihazlarınızı kapsamlı olarak korumak ve korumak için kullanışlı bir yol sağlar. [Intune'daki güvenlik taban çizgilerini öğrenin](/intune/security-baselines).

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Cihazlarınızı doğru yapılandırıldığından emin olun](configure-machines.md)
- [Uç nokta için Microsoft Defender'a cihaz ekleme](configure-machines-onboarding.md)
- [ASR kuralı dağıtımını ve algılamalarını en iyi duruma getirme](configure-machines-asr.md)
