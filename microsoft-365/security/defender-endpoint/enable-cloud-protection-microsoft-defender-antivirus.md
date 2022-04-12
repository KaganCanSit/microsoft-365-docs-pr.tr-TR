---
title: Microsoft Defender Virüsten Koruma'de bulut korumasını açma
description: Hızlı ve gelişmiş koruma özelliklerinden yararlanmak için bulut korumasını açın.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, bulut, ilk bakışta blok
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95269837e4ad26b4928a2ff82df65a259c707290
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790668"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma'de bulut korumasını açma

**Şunlar için geçerlidir:**

- Microsoft Defender Virüsten Koruma
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platform**
- Windows

[Microsoft Defender Virüsten Koruma'da bulut koruması](cloud-protection-microsoft-defender-antivirus.md) doğru, gerçek zamanlı ve akıllı koruma sağlar. Bulut koruması varsayılan olarak etkinleştirilmelidir; ancak bulut korumasını kuruluşunuzun gereksinimlerine uyacak şekilde yapılandırabilirsiniz.

## <a name="methods-to-configure-cloud-protection"></a>Bulut korumasını yapılandırma yöntemleri

Çeşitli yöntemlerden birini kullanarak Microsoft Defender Virüsten Koruma bulut korumasını açabilir veya kapatabilirsiniz:

- Microsoft Intune ve Configuration Manager içeren Microsoft Endpoint Manager
- Grup İlkesi
- PowerShell cmdlet'leri

Ayrıca Windows Güvenliği uygulamasını kullanarak tek tek uç noktalarda bulut korumasını açabilir veya kapatabilirsiniz. 

Uç noktalarınızın bulut koruma hizmetine bağlanamasını sağlamak için belirli ağ bağlantısı gereksinimleri hakkında daha fazla bilgi için bkz. [Ağ bağlantılarını yapılandırma ve doğrulama](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> Windows 10 ve Windows 11, bu makalede açıklanan **Temel** ve **Gelişmiş** raporlama seçenekleri arasında bir fark yoktur. Bu eski bir ayrımdır ve her iki ayarın seçilmesi de aynı bulut koruması düzeyine neden olur. Paylaşılan bilgilerin türü veya miktarında fark yoktur. Topladığımız bilgiler hakkında daha fazla bilgi için bkz. [Microsoft Gizlilik Bildirimi](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için Intune kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Giriş** bölmesinde **Cihaz yapılandırması > Profiller'i** seçin.

3. Yapılandırmak istediğiniz **Cihaz kısıtlamaları** profil türünü seçin. Yeni bir **Cihaz kısıtlamaları** profil türü oluşturmanız gerekiyorsa bkz. [Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure).

4. **Özellikler** \> **Yapılandırma ayarları: Microsoft Defender Virüsten Koruma düzenle'yi** \> seçin.

5. **Bulut tabanlı koruma** anahtarında **Etkinleştir'i** seçin.

6. **Kullanıcılara örnek göndermeden önce sor** açılan listesinde **Tüm verileri otomatik olarak gönder'i** seçin.

Ayarlarını oluşturma ve yapılandırma da dahil olmak üzere Intune cihaz profilleri hakkında daha fazla bilgi için bkz. [Microsoft Intune cihaz profilleri nedir?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için Microsoft Endpoint Manager kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Uç nokta güvenliği** \> **Virüsten Koruma'yı** seçin.

3. Bir virüsten koruma profili seçin. (Henüz bir profiliniz yoksa veya yeni bir profil oluşturmak istiyorsanız bkz[. Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure).

4. **Özellikler**'i seçin. Ardından **Yapılandırma ayarları'nın** yanındaki **Düzenle'yi** seçin.

5. **Bulut koruması'nı** genişletin ve bulut **tabanlı koruma düzeyi** listesinde aşağıdakilerden birini seçin:
   - **Yüksek**: Güçlü bir algılama düzeyi uygular.
   - **Yüksek artı**: **Yüksek** düzeyi kullanır ve daha fazla koruma önlemi uygular (istemci performansını etkileyebilir).
   - **Sıfır tolerans**: Tüm bilinmeyen yürütülebilir dosyaları engeller.

6. **Gözden Geçir ve kaydet'i** ve ardından **Kaydet'i** seçin.

Microsoft Endpoint Configuration Manager yapılandırma hakkında daha fazla bilgi için bkz. [Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için grup ilkesi kullanma

1. grup ilkesi yönetim cihazınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** seçin.

4. Ağacı **bileşenleri** >  Windows için genişletin **Microsoft Defender Virüsten Koruma > MAPS**

    > [!NOTE]
    > MAPS ayarları, bulut tabanlı korumaya eşittir.

5. **Microsoft MAPS'e Katıl'a** çift tıklayın. Seçeneğinin açık olduğundan ve **Temel HARITALAR** veya **Gelişmiş HARITALAR** olarak ayarlandığından emin olun. **Tamam**'ı seçin.

    Algılanan yazılım hakkında temel veya ek bilgiler göndermeyi seçebilirsiniz:

    - Temel MAPS: Temel üyelik, cihazınızda algılanan kötü amaçlı yazılımlar ve istenmeyebilecek yazılımlar hakkında Microsoft'a temel bilgiler gönderir. Bilgiler yazılımın nereden geldiğini (URL'ler ve kısmi yollar gibi), tehdidi çözmek için gerçekleştirilen eylemleri ve eylemlerin başarılı olup olmadığını içerir.

    - Gelişmiş HARITALAR: Gelişmiş üyelik, temel bilgilere ek olarak, yazılımın tam yolu ve yazılımın cihazınızı nasıl etkilediği hakkında ayrıntılı bilgiler de dahil olmak üzere kötü amaçlı yazılımlar ve istenmeyebilecek yazılımlar hakkında ayrıntılı bilgiler gönderir.

6. **Daha fazla analiz gerektiğinde Dosya örnekleri gönder'e** çift tıklayın. İlk seçeneğin **Etkin** olarak ayarlandığından ve diğer seçeneklerin şunlardan biri olarak ayarlandığından emin olun:

   - **Güvenli örnekler gönderme** (1)
   - **Tüm örnekleri gönder** (3)

   >[!NOTE]
   > **Güvenli örnekler gönder** (1) seçeneği, çoğu örneğin otomatik olarak gönderileceği anlamına gelir. Kişisel bilgiler içerme olasılığı olan dosyalar yine de sorulacaktır ve ek onay gerektirir.
   > **Seçeneğin Her Zaman İste** (0) olarak ayarlanması, cihazın koruma durumunu düşürür. **Bunu Hiçbir zaman gönderme** (2) olarak ayarlamak, Pertahanan Microsoft untuk Titik Akhir [İlk Bakışta Engelle](configure-block-at-first-sight-microsoft-defender-antivirus.md) özelliğinin çalışmaymayacağı anlamına gelir.

7. **Tamam**'ı seçin.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'ler bulut korumasını açabilir:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma ve Microsoft Defender Virüsten Koruma cmdlet'lerini yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlet'lerini](/powershell/module/defender/) kullanma . [İlke CSP - Defender](/windows/client-management/mdm/policy-csp-defender) özellikle [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) hakkında daha fazla bilgiye sahiptir.

> [!IMPORTANT]
> **-SubmitSamplesConsent** `SendSafeSamples` değerini (varsayılan, önerilen ayar) `NeverSend`veya `AlwaysPrompt`olarak ayarlayabilirsiniz. Bu `SendSafeSamples` ayar, çoğu örneğin otomatik olarak gönderileceği anlamına gelir. Kişisel bilgiler içerme olasılığı olan dosyalar devam etmek için bir istemle sonuçlanır ve onay gerektirir.
> `NeverSend` ve `AlwaysPrompt` ayarları cihazın koruma düzeyini düşürür. Ayrıca ayar, `NeverSend` Pertahanan Microsoft untuk Titik Akhir [İlk Bakışta Engelle](configure-block-at-first-sight-microsoft-defender-antivirus.md) özelliğinin çalışmaymayacağı anlamına gelir.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/defender/set-msft-mppreference) kullanın:

```WMI
MAPSReporting
SubmitSamplesConsent
```

İzin verilen parametreler hakkında daha fazla bilgi için bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Windows Güvenliği uygulamasıyla tek tek istemcilerde bulut korumasını açma

> [!NOTE]
> **Microsoft MAPS grup ilkesi raporlaması için yerel ayarı yapılandırma geçersiz kılma** ayarı **Devre Dışı** olarak ayarlanırsa, Windows Ayarlar'deki **Bulut tabanlı koruma** ayarı gri görünür ve kullanılamaz. grup ilkesi Nesnesi aracılığıyla yapılan değişikliklerin, ayarın Windows Ayarlar güncelleştirilmeden önce tek tek uç noktalara dağıtılması gerekir.

1. Görev çubuğunda kalkan simgesini seçerek veya başlangıç menüsünde **Windows Güvenliği arayarak Windows Güvenliği** uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin ve ardından **Ayarları yönet'in** altında **Virüs & tehdit koruması ayarları'nı** seçin.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Virüs & tehdit koruması ayarları" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. **Bulut Tabanlı Koruma** ve **Otomatik örnek gönderimlerinin** **Açık** olarak değiştirildiğini onaylayın.

   > [!NOTE]
   > Otomatik örnek gönderimi grup ilkesi ile yapılandırıldıysa ayar gri görünür ve kullanılamaz.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma'de Microsoft bulut korumasını kullanma](cloud-protection-microsoft-defender-antivirus.md)

- [Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Microsoft Defender Virüsten Koruma’yı yönetmek için PowerShell cmdlet'lerini kullanın](use-powershell-cmdlets-microsoft-defender-antivirus.md)
