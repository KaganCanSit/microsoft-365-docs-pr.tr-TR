---
title: Üçüncü taraf bir çözümden geçirirken Microsoft Defender Virüsten Koruma sorunlarını giderin
description: Microsoft Defender Virüsten Koruma geçiş sırasında sık karşılaşılan hataları giderme
keywords: olay, hata kodu, günlüğe kaydetme, sorun giderme, microsoft defender virüsten koruma, windows defender virüsten koruma, geçiş
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 10/19/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 74843a71131ae8f10628dac96086e68e25acb2b0
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788446"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Üçüncü taraf bir çözümden geçirirken Microsoft Defender Virüsten Koruma sorunlarını giderin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Üçüncü taraf bir güvenlik çözümünden Microsoft Defender Virüsten Koruma geçiş yaparken sorunlarla karşılaşırsanız burada yardım bulabilirsiniz.

## <a name="review-event-logs"></a>Olay günlüklerini gözden geçirme

1. Görev çubuğunda **Ara simgesini** seçip *olay görüntüleyicisini arayarak Olay görüntüleyicisi* uygulamasını açın.

    Microsoft Defender Virüsten Koruma hakkındaki bilgileri **Microsoft** \> **Windows Windows Defender** \> **Uygulama ve Hizmet Günlükleri** \> altında **bulabilirsiniz.**

1. Buradan **İşletim altında** **Aç'ı** seçin.

    Ayrıntılar bölmesinden bir olay seçildiğinde, alt bölmedeki **Genel** ve **Ayrıntılar sekmelerinin** altında bir olay hakkında daha fazla bilgi gösterilir.

## <a name="microsoft-defender-antivirus-wont-start"></a>Microsoft Defender Virüsten Koruma başlatılamıyor

Bu sorun, tümü aynı temel nedene sahip olan birkaç farklı olay kimlikleri biçiminde bildirimde bulunabilir.

### <a name="associated-event-ids"></a>İlişkili olay kimlikleri

Olay Kimliği|Günlük adı|Açıklama|Kaynak
---|---|---|---
15|Uygulama|Windows Defender durumu başarıyla SECURITY_PRODUCT_STATE_OFF güncelleştirildi.|Güvenlik Merkezi
5007|Microsoft-Windows-Windows Defender/Operasyonel|Windows Defenderin virustentorjunta Yapılandırması değişti. Bu beklenmeyen bir olaysa, kötü amaçlı yazılımların sonucu olabileceğinden ayarları gözden geçirmeniz gerekir. <p> **Eski değer:** Default\IsServiceRunning = 0x0 <p> **Yeni değer:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operasyonel|casus yazılımlar ve istenmeyebilecek diğer yazılımlar için Windows Defenderin virustentorjunta tarama devre dışı bırakıldı.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Üçüncü taraf virüsten koruma yazılımı yüklü olduğundan Microsoft Defender Virüsten Koruma başlatılıp başlatılmayacağını nasıl anlarız?

Windows 10 veya Windows 11 bir cihazda, Pertahanan Microsoft untuk Titik Akhir kullanmıyorsanız ve üçüncü taraf virüsten koruma yazılımı yüklüyse Microsoft Defender Virüsten Koruma otomatik olarak kapatılır. Pertahanan Microsoft untuk Titik Akhir üçüncü taraf virüsten koruma yazılımı yüklü olarak kullanıyorsanız, Microsoft Defender Virüsten Koruma pasif modda başlar ve işlevselliği azaltılır.

> [!TIP]
> Az önce açıklanan senaryo yalnızca Windows 10 ve Windows 11 için geçerlidir. Windows diğer sürümleri, üçüncü taraf güvenlik yazılımıyla birlikte çalıştırılan Microsoft Defender Virüsten Koruma [farklı yanıtlara](microsoft-defender-antivirus-compatibility.md) sahiptir.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Microsoft Defender Virüsten Koruma kapalı olup olmadığını denetlemek için Hizmetler uygulamasını kullanma

Hizmetler uygulamasını açmak için görev çubuğundan **Ara** simgesini seçin ve *hizmetleri* arayın. Uygulamayı *, services.msc* yazarak komut satırından da açabilirsiniz.

Microsoft Defender Virüsten Koruma hakkındaki bilgiler Hizmetler uygulamasında **Windows Defender** \> **Operasyonel** altında listelenir. Virüsten koruma hizmetinin adı *Windows Defenderin virustentorjunta Hizmeti'dir*.

Uygulamayı denetlerken *Windows Defenderin virustentorjunta Hizmeti'nin* el ile olarak ayarlandığını görebilirsiniz, ancak bu hizmeti el Windows Defenderin virustentorjunta ile başlatmayı denediğinizde *Yerel Bilgisayarda hizmet hizmeti başlatıldı ve durduruldu. Bazı hizmetler diğer hizmetler veya programlar tarafından kullanılmadıysa otomatik olarak durduruluyor.*

Bu, üçüncü taraf virüsten koruma yazılımıyla uyumluluğu korumak için Microsoft Defender Virüsten Koruma otomatik olarak kapatıldığını gösterir.

#### <a name="generate-a-detailed-report"></a>Ayrıntılı rapor oluşturma

Şu anda etkin olan grup ilkeleri hakkında ayrıntılı bir rapor oluşturmak için **Yönetici olarak çalıştır** modunda bir komut istemi açıp aşağıdaki komutu girebilirsiniz:

```console
GPresult.exe /h gpresult.html
```

Bu, *./gpresult.html* konumunda bulunan bir rapor oluşturur. Bu dosyayı açtığınızda, Microsoft Defender Virüsten Koruma nasıl kapatıldığına bağlı olarak aşağıdaki sonuçları görebilirsiniz.

##### <a name="group-policy-results"></a>Grup ilkesi sonuçları

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Güvenlik ayarları etki alanı veya yerel düzeyde grup ilkesi (GPO) aracılığıyla uygulanıyorsa ya da System center configuration manager (SCCM)

GPResults raporundaki *bileşenler/Windows Defenderin virustentorjunta Windows* başlığı altında, Microsoft Defender Virüsten Koruma kapatıldığını gösteren aşağıdaki girişe benzer bir şey görebilirsiniz.

Ilkesi|Ayar|Kazanan GPO
---|---|---
Windows Defenderin virustentorjunta kapatma|Etkin|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Güvenlik ayarları Grup ilkesi tercihi (GPP) aracılığıyla uygulanıyorsa

*Kayıt defteri öğesi (Anahtar yolu: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Değer adı: DisableAntiSpyware)* başlığı altında, Microsoft Defender Virüsten Koruma kapatıldığını belirten aşağıdaki girişe benzer bir şey görebilirsiniz.

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

Rapor, Microsoft Defender Virüsten Koruma kapalı olduğunu belirten aşağıdaki metni içerebilir:

> Kayıt Defteri (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (onaltılık)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Güvenlik ayarları Windows veya Windows Server görüntünüzde ayarlandıysa

Hayal eden yöneticiniz, *GPEdit.exe*, *LGPO.exe* aracılığıyla veya görev dizisindeki kayıt defterini değiştirerek **[disableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** güvenlik ilkesini yerel olarak ayarlamış olabilir. Microsoft Defender Virüsten Koruma için [Güvenilen Görüntü Tanımlayıcısı yapılandırabilirsiniz](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender).

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Microsoft Defender Virüsten Koruma yeniden açma

Microsoft Defender Virüsten Koruma, şu anda etkin başka bir virüsten koruma yazılımı yoksa otomatik olarak açılır. Microsoft Defender Virüsten Koruma tam işlevsellikle çalıştığından emin olmak için üçüncü taraf virüsten koruma yazılımını tamamen kapatmanız gerekir.

> [!WARNING]
> *HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services'da wdboot, wdfilter*, *wdnisdrv*, *wdnissvc* ve *windefend* için *Windows Defender* başlangıç değerlerini düzenlemenizi öneren çözümler desteklenmez ve sisteminizi yeniden görüntülemeye zorlayabilir.

Pertahanan Microsoft untuk Titik Akhir ve üçüncü taraf virüsten koruma yazılımını Microsoft Defender Virüsten Koruma ile birlikte kullanmaya başlarsanız pasif mod kullanılabilir. Pasif mod, Microsoft Defender Virüsten Koruma dosyaları taramasını ve kendisini güncelleştirmesini sağlar, ancak tehditleri düzeltmez. Ayrıca, [Uç nokta veri kaybı önleme (DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) dağıtılmadığı sürece [Gerçek Zamanlı Koruma](configure-real-time-protection-microsoft-defender-antivirus.md) aracılığıyla davranış izleme pasif modda kullanılamaz.

[Sınırlı düzenli tarama](limited-periodic-scanning-microsoft-defender-antivirus.md) olarak bilinen başka bir özellik, Microsoft Defender Virüsten Koruma otomatik olarak kapatacak şekilde ayarlandığında son kullanıcılar tarafından kullanılabilir. Bu özellik, Microsoft Defender Virüsten Koruma sınırlı sayıda algılama kullanarak üçüncü taraf virüsten koruma ile birlikte dosyaları düzenli aralıklarla taramasını sağlar.

> [!IMPORTANT]
> Kurumsal ortamlarda sınırlı düzenli tarama önerilmez. Bu modda Microsoft Defender Virüsten Koruma çalıştırırken kullanılabilen algılama, yönetim ve raporlama özellikleri, etkin moda göre azaltılır.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)


### <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma uyumluluğu](microsoft-defender-antivirus-compatibility.md)
- [Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma](microsoft-defender-security-center-antivirus.md)
