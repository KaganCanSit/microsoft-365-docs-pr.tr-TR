---
title: Mac'te Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Mac'te e-posta yükleme, yapılandırma, güncelleştirme ve Uç Nokta için Microsoft Defender öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, monterey, big sur, catalina, mojave, mac için mde
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
ms.openlocfilehash: 2e982a32826906feb65b05837506ff2f513eb27e
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507311"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konu başlığında, Mac'te Uç Nokta için Defender'ı yükleme, yapılandırma, güncelleştirme ve kullanma açıklanmıştır.

> [!CAUTION]
> Mac'te diğer üçüncü taraf uç nokta koruma ürünlerinin Uç Nokta için Microsoft Defender birlikte çalıştırmanın performans sorunlarına ve öngörülemeyen yan etkilere neden olması olasıdır. Microsoft dışı uç nokta koruması ortamınızın mutlak bir gereksinimi ise, virüsten koruma işlevini Pasif modunda çalıştıracak şekilde yapılandırdikten sonra Mac EDR Uç Nokta için Defender'ın avantajını güvenle [kullanabilirsiniz](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>En son sürümde yapılan güncelleştirmeler

[Uç Nokta için Microsoft Defender’daki yenilikler](whats-new-in-microsoft-defender-endpoint.md)

[Mac'te Uç Nokta için Microsoft Defender'](mac-whatsnew.md)

> [!TIP]
> Paylaşmak isteğiniz herhangi bir geri bildiriminiz varsa, aygıtınızda Mac'te Uç Nokta için Microsoft Defender'ı açarak ve Geri bildirim Göndermeye Yardım **Edin'e** \> giderek **gönderin**.

Önizleme özellikleri (Örneğin, Mac cihazlarınız için uç noktada algılama ve yanıtlama) en son özellikleri almak için, Uç Nokta için Microsoft Defender çalıştıran macOS cihazınızı "Insider" cihazı olacak şekilde yapılandırabilirsiniz.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Uç Nokta için Microsoft Defender Mac'e yükleme

### <a name="prerequisites"></a>Önkoşullar

- Uç nokta aboneliği ve Microsoft 365 Defender portalına erişim için Defender
- macOS ve BASH betikleri için başlangıç düzeyi deneyimi
- Cihaz üzerinde yönetim ayrıcalıkları (el ile dağıtım durumunda)

### <a name="installation-instructions"></a>Yükleme yönergeleri

Mac'te Uç Nokta için Defender'ı yüklemek ve yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

- Üçüncü taraf yönetim araçları:
    - [Microsoft Intune tabanlı dağıtım](mac-install-with-intune.md)
    - [JAMF tabanlı dağıtım](mac-install-with-jamf.md)
    - [Diğer MDM ürünleri](mac-install-with-other-mdm.md)

- Komut satırı aracı:
    - [El ile dağıtım](mac-install-manually.md)

### <a name="system-requirements"></a>Sistem gereksinimleri

MacOS'un en son üç ana sürümü de destekle devam ediyor.

> [!IMPORTANT]
> macOS 11 (Big Sur) ve üstünde, Uç Nokta için Microsoft Defender yapılandırma profilleri gerekir. önceki macOS sürümlerinden yükseltme yapılan mevcut bir müşteriysiniz, [macOS Catalina](mac-sysext-policies.md) için yeni yapılandırma profilleri ve macOS'un daha yeni sürümleri konusunda listelenen ek yapılandırma profillerini dağıtın.

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Disk alanı: 1 GB

macOS'un beta sürümleri desteklenmiyor.

M1 yonga tabanlı işlemcilere sahip macOS cihazlar desteği, temsilcinin 101.40.84 sürümünden itibaren resmi olarak destek almaktadır.

Hizmeti etkinleştirdikten sonra, ağ veya güvenlik duvarınızı bu bağlantıyla uç noktalarınız arasında giden bağlantılara izin verecek şekilde yapılandırmanız gerekebilir.

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Uç Nokta için Microsoft Defender lisanslama için aşağıdaki Microsoft Toplu Lisans tekliflerinden biri gerekir:

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Güvenlik
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Uç Nokta için Microsoft Defender

> [!NOTE]
> Uygun lisanslı kullanıcılar en fazla Uç Nokta için Microsoft Defender eş zamanlı cihazlarda Kullanıcı Lisansı kullanabilir.
> Uç Nokta için Microsoft Defender, bir aydan (CSP) Bulut Çözümü Sağlayıcısı de satın alınabilir. BIR CSP ile satın alınsa, listelenen Microsoft Toplu Lisanslama teklifleri gerektirmez.

### <a name="configuring-exclusions"></a>Dışlamaları Yapılandırma

Dışlamalar eklerken, dışlama [hatalarının yaygın olarak Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Ağ bağlantıları

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kurabilirsiniz ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralları olmadığını veya bunlar için özel olarak bir izin *kuralı oluşturmanız gerekebilir* .


|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
|Uç Nokta için Microsoft Defender müşteriler için bir URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Uç Nokta için Microsoft Defender Gov/GCC/DoD için URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Uç Nokta için Microsoft Defender bulma yöntemleri kullanarak bir proxy sunucusu bu olabilir:

- Proxy otomatik yapılandırması (PAC)
- Web Proxy Otomatik Bulma Protokolü (WPAD)
- El ile statik ara sunucu yapılandırması

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, anonim trafiğin daha önce listelenen URL'lerde izin verildiğindan emin olun.

> [!WARNING]
> Kimliği doğrulanmışxler desteklanmaz. Yalnızca PAC, WPAD veya statik ara sunucu kullanılırken emin olma.
>
> SSL incelemesi ve kesişme prox'leri güvenlik nedenleriyle de desteklanmaz. macOS'ta SSL incelemeleri ve proxy sunucunuz için, macOS'ta Uç Nokta için Microsoft Defender kesişme olmadan ilgili URL'lere doğrudan geçecek bir özel durum yapılandırın. Kesme noktası sertifikanızı genel mağazaya eklemek kesme noktası engellemesine izin vermez.

Bağlantının engel olmadığını test etmek için tarayıcıyı <https://x.cp.wd.microsoft.com/api/report> <https://cdn.x.cp.wd.microsoft.com/ping> açın ve açın.

Komut çizgilerini tercih ediyorsanız Terminal'de aşağıdaki komutu çalıştırarak da bağlantıyı kontrol edin:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Bu komutun çıkışı aşağıdakine benzer olması gerekir:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> İstemci cihazlarda Sistem Bütünlüğü [Koruması'nın](https://support.apple.com/HT204899) (SIP) etkin durumda tutmasını öneririz. SIP, işletim sistemiyle düşük düzeyde oynanmasını önleyen ve varsayılan olarak etkinleştiren yerleşik bir macOS güvenlik özelliğidir.

Bağlantı Uç Nokta için Microsoft Defender, Terminal'de aşağıdaki komut çalıştırarak bağlantı doğrulanabilir:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender güncelleştirme

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar. Mac'Uç Nokta için Microsoft Defender güncelleştirme yapmak için Microsoft AutoUpdate (MAU) adlı bir program kullanılır. Daha fazla bilgi edinmek için bkz[. Mac'te Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender yapılandırma

Ürünü kurumsal ortamlarda yapılandırma kılavuzuna [Mac'te Kurumsal ortamlar için tercihleri ayarlama Uç Nokta için Microsoft Defender kılavuzu yer almaktadır](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>macOS çekirdek ve sistem uzantıları

macOS gelişimle hizalama olarak, Mac'te çekirdek uzantıları yerine sistem uzantılarını yararlanan bir Uç Nokta için Microsoft Defender güncelleştirmesi için hazırlanmaya devam ediyoruz. İlgili ayrıntılar için bkz[. Mac'te Uç Nokta için Microsoft Defender.](mac-whatsnew.md)

## <a name="resources"></a>Kaynaklar

- Günlüğe kaydetme, kaldırma veya diğer konular hakkında daha fazla bilgi için bkz. [Mac'te Uç Nokta için Microsoft Defender kaynakları](mac-resources.md).
- [Mac'Uç Nokta için Microsoft Defender gizlilik](mac-privacy.md).
