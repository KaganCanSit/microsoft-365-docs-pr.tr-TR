---
title: Üçüncü taraf bir çözümden geçirirken Microsoft Defender Virüsten Koruma sorunlarını giderin
description: Microsoft Defender Virüsten Koruma'ya geçiş sırasında sık karşılaşılan hataları giderme
keywords: olay, hata kodu, günlüğe kaydetme, sorun giderme, microsoft defender virüsten koruma, windows defender virüsten koruma, geçiş
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: c1fe1713909395c1c30af8089664e70598e91721
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923178"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Üçüncü taraf bir çözümden geçirirken Microsoft Defender Virüsten Koruma sorunlarını giderin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Virüsten Koruma](https://www.microsoft.com/windows/comprehensive-security)

**Platform**
- Windows

Üçüncü taraf bir güvenlik çözümünden Microsoft Defender Virüsten Koruma'ya geçiş yaparken sorunlarla karşılaşırsanız burada yardım bulabilirsiniz.

## <a name="review-event-logs"></a>Olay günlüklerini gözden geçirme

1. Görev çubuğunda **Ara simgesini** seçip *olay görüntüleyicisini arayarak Olay görüntüleyicisi* uygulamasını açın.

    Microsoft Defender Virüsten Koruma hakkında bilgi, **Microsoft** \> **Windows Windows** \> **Defender'ın Uygulama ve Hizmet Günlükleri** \> altında bulunabilir.

1. Buradan **İşletim altında** **Aç'ı** seçin.

    Ayrıntılar bölmesinden bir olay seçildiğinde, alt bölmedeki **Genel** ve **Ayrıntılar sekmelerinin** altında bir olay hakkında daha fazla bilgi gösterilir.

## <a name="microsoft-defender-antivirus-wont-start"></a>Microsoft Defender Virüsten Koruma başlatılmıyor

Bu sorun, tümü aynı temel nedene sahip olan birkaç farklı olay kimlikleri biçiminde bildirimde bulunabilir.

### <a name="associated-event-ids"></a>İlişkili olay kimlikleri

Olay Kimliği|Günlük adı|Açıklama|Kaynak
---|---|---|---
15|Uygulama|Windows Defender durumu başarıyla SECURITY_PRODUCT_STATE_OFF güncelleştirildi.|Güvenlik Merkezi
5007|Microsoft-Windows-Windows Defender/Operasyonel|Windows Defender Virüsten Koruma Yapılandırması değişti. Bu beklenmeyen bir olaysa, kötü amaçlı yazılımların sonucu olabileceğinden ayarları gözden geçirmeniz gerekir. <p> **Eski değer:** Default\IsServiceRunning = 0x0 <p> **Yeni değer:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operasyonel|Casus yazılımlar ve istenmeyebilecek diğer yazılımlar için Windows Defender Virüsten Koruma taraması devre dışı bırakıldı.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Üçüncü taraf virüsten koruma yazılımı yüklü olduğundan Microsoft Defender Virüsten Koruma'nın başlatılıp başlatılmayacağını nasıl anlarız?

Bir Windows 10 veya Windows 11 cihazında, Uç Nokta için Microsoft Defender kullanmıyorsanız ve yüklü bir üçüncü taraf virüsten koruma yazılımınız varsa, Microsoft Defender Virüsten Koruma otomatik olarak kapatılır. Uç Nokta için Microsoft Defender'ı üçüncü taraf virüsten koruma yazılımı yüklü olarak kullanıyorsanız, Microsoft Defender Virüsten Koruma daha az işlevsellikle pasif modda başlar.

> [!TIP]
> Az önce açıklanan senaryo yalnızca Windows 10 ve Windows 11 için geçerlidir. Windows'un diğer sürümleri, üçüncü taraf güvenlik yazılımıyla birlikte çalıştırılan Microsoft Defender Virüsten Koruma'ya [farklı yanıtlara](microsoft-defender-antivirus-compatibility.md) sahiptir.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Microsoft Defender Virüsten Koruma'nın kapalı olup olmadığını denetlemek için Hizmetler uygulamasını kullanma

Hizmetler uygulamasını açmak için görev çubuğundan **Ara** simgesini seçin ve *hizmetleri* arayın. Uygulamayı *, services.msc* yazarak komut satırından da açabilirsiniz.

Microsoft Defender Virüsten Koruma hakkındaki bilgiler **, Hizmetler uygulamasında Windows Defender** \> **İşletimsel** altında listelenir. Virüsten koruma hizmetinin adı *Windows Defender Virüsten Koruma Hizmeti'dir*.

Uygulamayı denetlerken *Windows Defender Virüsten Koruma Hizmeti'nin* el ile olarak ayarlandığını görebilirsiniz, ancak bu hizmeti el ile başlatmayı denediğinizde *, Yerel Bilgisayardaki Windows Defender Virüsten Koruma Hizmeti'nin başlatıldığını ve durdurulduğunu belirten bir uyarı alırsınız. Bazı hizmetler diğer hizmetler veya programlar tarafından kullanılmadıysa otomatik olarak durduruluyor.*

Bu, üçüncü taraf virüsten koruma yazılımıyla uyumluluğu korumak için Microsoft Defender Virüsten Koruma'nın otomatik olarak kapatıldığını gösterir.

#### <a name="generate-a-detailed-report"></a>Ayrıntılı rapor oluşturma

Şu anda etkin olan grup ilkeleri hakkında ayrıntılı bir rapor oluşturmak için **Yönetici olarak çalıştır** modunda bir komut istemi açıp aşağıdaki komutu girebilirsiniz:

```console
GPresult.exe /h gpresult.html
```

Bu, *./gpresult.html* konumunda bulunan bir rapor oluşturur. Bu dosyayı açtığınızda, Microsoft Defender Virüsten Koruma'nın nasıl kapatıldığına bağlı olarak aşağıdaki sonuçları görebilirsiniz.

##### <a name="group-policy-results"></a>Grup ilkesi sonuçları

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Güvenlik ayarları etki alanı veya yerel düzeyde grup ilkesi (GPO) aracılığıyla uygulanıyorsa ya da System center configuration manager (SCCM)

GPResults raporunda, *Windows Bileşenleri/Windows Defender Virüsten Koruma* başlığı altında, Microsoft Defender Virüsten Koruma'nın kapalı olduğunu belirten aşağıdaki girişe benzer bir şey görebilirsiniz.

Ilkesi|Ayar|Kazanan GPO
---|---|---
Windows Defender Virüsten Koruma'nı kapatma|Etkin|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Güvenlik ayarları Grup ilkesi tercihi (GPP) aracılığıyla uygulanıyorsa

*Kayıt defteri öğesi (Anahtar yolu: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Değer adı: DisableAntiSpyware)* başlığı altında, Microsoft Defender Virüsten Koruma'nın kapalı olduğunu gösteren aşağıdaki girişe benzer bir şey görebilirsiniz.

DisableAntiSpyware|-
---|---
Kazanan GPO|Win10-Workstations
Sonuç: Başarılı|
**Genel**|
Eylem|Güncelleştirme
**Özellikler**|
Kovan|HKEY_LOCAL_MACHINE
Anahtar yolu|SOFTWARE\Policies\Microsoft\Windows Defender
Değer adı|DisableAntiSpyware
Değer türü|REG_DWORD
Değer verileri|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Güvenlik ayarları kayıt defteri anahtarı aracılığıyla uygulanıyorsa

Rapor, Microsoft Defender Virüsten Koruma'nın kapalı olduğunu belirten aşağıdaki metni içerebilir:

> Kayıt Defteri (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (onaltılık)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Windows'ta veya Windows Server görüntünüzde güvenlik ayarları ayarlandıysa

Hayal eden yöneticiniz, *GPEdit.exe*, *LGPO.exe* aracılığıyla veya görev dizisindeki kayıt defterini değiştirerek **[disableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** güvenlik ilkesini yerel olarak ayarlamış olabilir. Microsoft Defender Virüsten Koruma için [Güvenilir Görüntü Tanımlayıcısı yapılandırabilirsiniz](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) .

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Microsoft Defender Virüsten Koruma'nı yeniden açma

Şu anda etkin başka bir virüsten koruma yazılımı yoksa Microsoft Defender Virüsten Koruma otomatik olarak açılır. Microsoft Defender Virüsten Koruma'nın tam işlevsellikle çalışabilmesi için üçüncü taraf virüsten koruma yazılımını tamamen kapatmanız gerekir.

> [!WARNING]
> *HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services'da wdboot, wdfilter*, *wdnisdrv, wdnissvc* ve *windefend* için *Windows Defender* başlangıç değerlerini düzenlemenizi öneren çözümler desteklenmez ve sisteminizi yeniden görüntülemeye zorlayabilir. 

Uç Nokta için Microsoft Defender'ı ve üçüncü taraf virüsten koruma yazılımını Microsoft Defender Virüsten Koruma ile birlikte kullanmaya başlarsanız pasif mod kullanılabilir. Pasif mod, Microsoft Defender Virüsten Koruma'nın dosyaları taramasına ve kendisini güncelleştirmesine izin verir, ancak tehditleri düzeltmez. Ayrıca, [Uç nokta veri kaybı önleme (DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) dağıtılmadığı sürece [Gerçek Zamanlı Koruma](configure-real-time-protection-microsoft-defender-antivirus.md) aracılığıyla davranış izleme pasif modda kullanılamaz.

[Sınırlı düzenli tarama](limited-periodic-scanning-microsoft-defender-antivirus.md) olarak bilinen başka bir özellik, Microsoft Defender Virüsten Koruma otomatik olarak kapatacak şekilde ayarlandığında son kullanıcılar tarafından kullanılabilir. Bu özellik, Microsoft Defender Virüsten Koruma'nın sınırlı sayıda algılama kullanarak üçüncü taraf virüsten koruma yazılımıyla birlikte dosyaları düzenli aralıklarla taramasına olanak tanır.

> [!IMPORTANT]
> Kurumsal ortamlarda sınırlı düzenli tarama önerilmez. Microsoft Defender Virüsten Koruma'yı bu modda çalıştırırken kullanılabilen algılama, yönetim ve raporlama özellikleri, etkin moda göre azaltılır.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)


### <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma uyumluluğu](microsoft-defender-antivirus-compatibility.md)
- [Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma](microsoft-defender-security-center-antivirus.md)
