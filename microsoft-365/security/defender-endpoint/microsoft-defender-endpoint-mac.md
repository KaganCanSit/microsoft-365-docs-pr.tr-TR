---
title: Mac'te Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Mac'te Uç Nokta için Microsoft Defender yüklemeyi, yapılandırmayı, güncelleştirmeyi ve kullanmayı öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, monterey, big sur, catalina, mojave, mde for mac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d6438c7af3d3dbb8f4b2c19fdfdd04640cc8b4d2
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174960"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konuda Mac'te Uç Nokta için Defender'ı yükleme, yapılandırma, güncelleştirme ve kullanma işlemleri açıklanmaktadır.

> [!CAUTION]
> Mac'te Uç Nokta için Microsoft Defender birlikte diğer üçüncü taraf uç nokta koruma ürünlerini çalıştırmak, performans sorunlarına ve öngörülemeyen yan etkilere yol açabilir. Ortamınızda Microsoft dışı uç nokta koruması mutlak bir gereksinimse, virüsten koruma işlevini [Pasif modda](mac-preferences.md#enforcement-level-for-antivirus-engine) çalışacak şekilde yapılandırdıktan sonra Mac'te Uç Nokta için Defender EDR işlevselliğinden güvenle yararlanabilirsiniz.

## <a name="whats-new-in-the-latest-release"></a>En son sürümdeki yenilikler

[Uç Nokta için Microsoft Defender'deki yenilikler](whats-new-in-microsoft-defender-endpoint.md)

[Mac'te Uç Nokta için Microsoft Defender'deki yenilikler](mac-whatsnew.md)

> [!TIP]
> Paylaşmak istediğiniz herhangi bir geri bildiriminiz varsa, cihazınızda Mac'te Uç Nokta için Microsoft Defender açarak ve Geri bildirim **Göndermeye Yardımcı Olun** \> bölümüne giderek bu **geri bildirimi** gönderin.

Önizleme özellikleri (Mac cihazlarınız için uç noktada algılama ve yanıtlama gibi) dahil olmak üzere en son özellikleri almak için Uç Nokta için Microsoft Defender çalıştıran macOS cihazınızı "Insider" cihazı olacak şekilde yapılandırın.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Mac'e Uç Nokta için Microsoft Defender yükleme

### <a name="prerequisites"></a>Önkoşullar

- Uç Nokta için Defender aboneliği ve Microsoft 365 Defender portalına erişim
- macOS ve BASH betiği oluşturmada başlangıç düzeyinde deneyim
- Cihazdaki yönetim ayrıcalıkları (el ile dağıtım durumunda)

### <a name="installation-instructions"></a>Yükleme yönergeleri

Mac'te Uç Nokta için Defender'ı yüklemek ve yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

- Üçüncü taraf yönetim araçları:
    - [Microsoft Intune tabanlı dağıtım](mac-install-with-intune.md)
    - [JAMF tabanlı dağıtım](mac-install-with-jamf.md)
    - [Diğer MDM ürünleri](mac-install-with-other-mdm.md)

- Komut satırı aracı:
    - [El ile dağıtım](mac-install-manually.md)

### <a name="system-requirements"></a>Sistem gereksinimleri

macOS'un en son üç ana sürümü desteklenir.

> [!IMPORTANT]
> macOS 11 (Big Sur) ve üzeri sürümlerde Uç Nokta için Microsoft Defender ek yapılandırma profilleri gerektirir. macOS'un önceki sürümlerinden yükseltme yapıyorsanız, [macOS Catalina için yeni yapılandırma profilleri ve macOS'un daha yeni sürümlerinde listelenen ek yapılandırma profillerini](mac-sysext-policies.md) dağıttığınızdan emin olun.

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Disk alanı: 1 GB

macOS'un beta sürümleri desteklenmez.

M1 yonga tabanlı işlemcilere sahip macOS cihazları için destek, aracının 101.40.84 sürümünden bu yana resmi olarak desteklenmektedir.

Hizmeti etkinleştirdikten sonra, ağınızı veya güvenlik duvarınızı, bu hizmetle uç noktalarınız arasında giden bağlantılara izin verecek şekilde yapılandırmanız gerekebilir.

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Mac'te Uç Nokta için Microsoft Defender aşağıdaki Microsoft Toplu Lisanslama tekliflerinden birini gerektirir:

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Güvenlik
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Uç Nokta için Microsoft Defender

> [!NOTE]
> Uygun lisanslı kullanıcılar en fazla beş eşzamanlı cihazda Uç Nokta için Microsoft Defender kullanabilir.
> Uç Nokta için Microsoft Defender ayrıca bir Bulut Çözümü Sağlayıcısı (CSP) satın alınabilir. CSP aracılığıyla satın aldığınızda, listelenen Microsoft Toplu Lisanslama tekliflerini gerektirmez.

### <a name="configuring-exclusions"></a>Dışlamaları Yapılandırma

Dışlama eklerken, [Microsoft Defender Virüsten Koruma için yaygın dışlama hatalarına](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) dikkat edin.

### <a name="network-connections"></a>Ağ bağlantıları

Aşağıdaki indirilebilir elektronik tablo, ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddedecek bir güvenlik duvarı veya ağ filtreleme kuralı olmadığından emin olmalısınız veya bunlar için özel olarak bir *izin verme* kuralı oluşturmanız gerekebilir.


|Etki alanları listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta için Microsoft Defender URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD için Uç Nokta için Microsoft Defender URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Uç Nokta için Microsoft Defender aşağıdaki bulma yöntemlerini kullanarak bir proxy sunucusu bulabilir:

- Ara sunucu otomatik yapılandırması (PAC)
- Web Proxy Otomatik Bulma Protokolü (WPAD)
- El ile statik proxy yapılandırması

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, önceden listelenen URL'lerde anonim trafiğe izin verildiğinden emin olun.

> [!WARNING]
> Kimliği doğrulanmış proxy'ler desteklenmez. Yalnızca PAC, WPAD veya statik ara sunucu kullanıldığından emin olun.
>
> GÜVENLIK nedeniyle SSL denetimi ve ara sunucuları da desteklenmez. SSL denetimi ve ara sunucunuzun macOS'ta Uç Nokta için Microsoft Defender verileri kesmeden ilgili URL'lere doğrudan geçirmesi için bir özel durum yapılandırın. Kesme sertifikanızı genel depoya eklemek kesmeye izin vermez.

Bir bağlantının engellenmediğini <https://x.cp.wd.microsoft.com/api/report> test etmek için tarayıcıda açın ve <https://cdn.x.cp.wd.microsoft.com/ping> açın.

Komut satırını tercih ederseniz, Terminal'de aşağıdaki komutu çalıştırarak bağlantıyı de kontrol edebilirsiniz:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Bu komutun çıkışı aşağıdakine benzer olmalıdır:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> İstemci cihazlarda [Sistem Bütünlüğü Koruması'nın](https://support.apple.com/HT204899) (SIP) etkin kalmasını öneririz. SIP, işletim sistemiyle alt düzey kurcalamayı engelleyen yerleşik bir macOS güvenlik özelliğidir ve varsayılan olarak etkindir.

Uç Nokta için Microsoft Defender yüklendikten sonra Bağlantı, Terminal'de aşağıdaki komut çalıştırılarak doğrulanabilir:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender güncelleştirme

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar. Mac'te Uç Nokta için Microsoft Defender güncelleştirmek için Microsoft AutoUpdate (MAU) adlı bir program kullanılır. Daha fazla bilgi için bkz[. Mac'te Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender yapılandırma

Ürünü kurumsal ortamlarda yapılandırma yönergeleri[, Mac'te Uç Nokta için Microsoft Defender için tercihleri ayarlama](mac-preferences.md) bölümünde sağlanır.

## <a name="macos-kernel-and-system-extensions"></a>macOS çekirdek ve sistem uzantıları

macOS 11 'den (Big Sur) başlayarak, Uç Nokta için Microsoft Defender çekirdek uzantısından sistem uzantılarına tamamen geçirilmiştir. Çekirdek uzantısı macOS 10.15 (Catalina) üzerinde hala kullanılıyor.

## <a name="resources"></a>Kaynaklar

- Günlüğe kaydetme, kaldırma veya diğer konular hakkında daha fazla bilgi için bkz. [Mac'te Uç Nokta için Microsoft Defender kaynakları](mac-resources.md).
- [Mac'te Uç Nokta için Microsoft Defender için gizlilik](mac-privacy.md).
