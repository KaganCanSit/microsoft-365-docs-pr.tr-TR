---
title: Üçüncü Microsoft Defender Virüsten Koruma çözümden ilerlerken sorun giderme
description: Hata gidermeye kadar yaygın hataları Microsoft Defender Virüsten Koruma
keywords: olay, hata kodu, günlüğe kaydetme, sorun giderme, microsoft Defender virüsten koruma, windows defender virüsten koruma, geçiş
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
ms.openlocfilehash: c1b60b66977c4f93591bce20a5cf6ace0b7fc567
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997521"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Üçüncü Microsoft Defender Virüsten Koruma çözümden ilerlerken sorun giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Üçüncü taraf bir güvenlik çözümünden başka bir çözümden başka bir çözüme veya başka bir çözüme veya başka bir Microsoft Defender Virüsten Koruma.

## <a name="review-event-logs"></a>Olay günlüklerini gözden geçirme

1. Görev çubuğunda Ara simgesini seçerek ve olay **görüntüleyicisini** arayarak Olay *görüntüleyicisi uygulamasını açın*.

    Daha fazla Microsoft Defender Virüsten Koruma, Microsoft **Günlüklerini Ve Uygulamaları ve Hizmet** **Günlüklerini** \> \> **Windows** \> Windows Defender.

1. Buradan İşlem'in  altında **Aç'ı seçin**.

    Ayrıntılar bölmesinden bir olay seçerek, alt bölmede Genel ve Ayrıntılar sekmelerinin altında etkinlik hakkında daha **fazla** **bilgi** gösterilir.

## <a name="microsoft-defender-antivirus-wont-start"></a>Microsoft Defender Virüsten Koruma başlamaz

Bu sorun, hepsinin temel nedeni aynı olan birkaç farklı olay kimlikleri şeklinde yeniden ortaya çıkar.

### <a name="associated-event-ids"></a>İlişkili olay kimlikleri

Olay Kimliği|Günlük adı|Açıklama|Kaynak
---|---|---|---
15|Uygulama|Güncelleştirme Windows Defender başarıyla güncelleştirildi ve SECURITY_PRODUCT_STATE_OFF.|Güvenlik Merkezi
5007|Microsoft-Windows-Windows Defender/İşlem|Windows Defender Virüsten Koruma Yapılandırması değişti. Bu beklenmeyen bir olaysa, kötü amaçlı yazılımdan etkilana neden olduğu için ayarları gözden geçirebilirsiniz. <p> **Eski değer:** Default\IsServiceRunning = 0x0 <p> **Yeni değer:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/İşlem|Windows Defender Virüsten Koruma yazılım tarama ve diğer istenmeyen yazılımlar devre dışı bırakılır.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Üçüncü taraf virüsten Microsoft Defender Virüsten Koruma yüklü olduğundan e-postanın başlatılamay nasıl olur?

Windows 10 veya Windows 11 cihazında, Uç Nokta için Microsoft Defender kullanmayacaksanız ve yüklü bir üçüncü taraf virüsten koruma varsa, Microsoft Defender Virüsten Koruma otomatik olarak kapatılır. Üçüncü taraf virüsten koruma yazılımının yüklü olduğu Uç Nokta için Microsoft Defender'ı kullanıyorsanız, Microsoft Defender Virüsten Koruma pasif modunda başlar ve işlev azalır.

> [!TIP]
> Az önce açıklanan senaryo yalnızca 11. Windows 10 ve Windows için geçerlidir. Uygulamanın diğer Windows, [üçüncü taraf](microsoft-defender-antivirus-compatibility.md) güvenlik Microsoft Defender Virüsten Koruma birlikte çalıştırıla ilgili farklı yanıtlara sahiptir.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Hizmet uygulamasını kullanarak kapalı olup Microsoft Defender Virüsten Koruma denetleme

Hizmetler uygulamasını açmak için görev **çubuğundan Ara** simgesini seçin ve hizmetleri *arayın*. Ayrıca, *services.msc* yazarak da komut satırdan uygulamayı açabilirsiniz.

Hizmet Microsoft Defender Virüsten Koruma, Hizmetler uygulamasında İşlem İşlemleri **altında Windows Defender** \> **listelenir**. Virüsten koruma hizmeti adı *Hizmet Windows Defender Virüsten Koruma adıdır*.

Uygulamayı kontrol ederken, *Windows Defender Virüsten Koruma* Hizmeti'nin el ile olarak ayar olduğunu görebilir, ancak bu hizmeti el ile başlatmayı denemelisiniz; Bu, Uygulama Başlatıcı Windows Defender Virüsten Koruma *Yerel Bilgisayarda hizmet hizmeti başlatıldı ve ardından durduruldu. Bazı hizmetler, başka hizmetler veya programlar tarafından kullannmayacaksa otomatik olarak durur.*

Bu, Microsoft Defender Virüsten Koruma virüsten koruma yazılımıyla uyumluluğu korumak için otomatik olarak kapatmış olduğunu gösterir.

#### <a name="generate-a-detailed-report"></a>Ayrıntılı rapor oluşturma

Şu anda etkin grup ilkeleri hakkında ayrıntılı bir rapor oluşturmak için, komut istemini Yönetici modunda  çalıştır'da açarak ve aşağıdaki komutu girerek yapabilirsiniz:

```console
GPresult.exe /h gpresult.html
```

Bu, *./gpresult.html.* Bu dosyayı açın; dosyanın nasıl kapatmış olduğuna bağlı olarak Microsoft Defender Virüsten Koruma sonuçlarıyla karşınıza çıkar.

##### <a name="group-policy-results"></a>Grup ilkesi sonuçları

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Güvenlik ayarları etki alanı veya yerel düzeyde grup ilkesi (GPO) aracılığıyla veya System Center Configuration Manager (SCCM) aracılığıyla uygulanırsa

GPResults raporu içinde, *Windows Bileşenleri/* Windows Defender Virüsten Koruma başlığı altında, aşağıdaki girişe benzer bir şey görebilir ve bu Microsoft Defender Virüsten Koruma kapalıdır.

İlke|Ayar|Kazanan GPO
---|---|---
E-Windows Defender Virüsten Koruma|Etkin|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Güvenlik ayarları Grup ilkesi tercihi (GPP) aracılığıyla uygulanırsa

Kayıt Defteri öğesi *(Anahtar yolu: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Değer adı: DisableAnti Öğe)* başlığı altında, aşağıdaki girişe benzer bir şey görebilir ve bunun Microsoft Defender Virüsten Koruma kapalı olduğunu gösterir.

DisableAntiCcaware|-
---|---
Kazanan GPO|Win10-Workstations
Sonuç: Başarılı|
**Genel**|
Eylem|Güncelleştirme
**Özellikler**|
Değilken|HKEY_LOCAL_MACHINE
Anahtar yolu|SOFTWARE\Policies\Microsoft\Windows Defender
Değer adı|DisableAntiCcaware
Değer türü|REG_DWORD
Value data|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Güvenlik ayarları kayıt defteri anahtarı aracılığıyla uygulanırsa

Rapor, aşağıdaki metni içerebilir ve bu metin Microsoft Defender Virüsten Koruma kapalı olabilir:

> Kayıt Defteri (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Bu sunucuda veya Windows Server resminde güvenlik Windows ayarları

Yanlışlayan yöneticiniz, güvenlik ilkesi **[DisableAntiCcaware'ı](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)***GPEdit.exe*, *LGPO.exe* aracılığıyla yerel olarak veya görev sırasında kayıt defterini değiştirerek ayarla etmiş olabilir. Bir kullanıcı [için Güvenilen Resim Tanımlayıcı'Microsoft Defender Virüsten Koruma](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender).

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Microsoft Defender Virüsten Koruma açma

Microsoft Defender Virüsten Koruma virüsten koruma yazılımı o anda etkin değilse otomatik olarak açılır. Virüsten koruma yazılımının tüm işlevlerle çalışması için üçüncü taraf virüsten Microsoft Defender Virüsten Koruma tamamen kapatmanız gerekir.

> [!WARNING]
> *HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services'te* *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* ve *windefend* için Windows Defender başlangıç değerlerini düzenlemenizi öneren çözümler desteklenmez ve sisteminizi yeniden görüntüleyemezsiniz.

Pasif modu, Uç Nokta için Microsoft Defender'ı ve birlikte bir üçüncü taraf virüsten koruma yazılımı kullanıyorsanız Microsoft Defender Virüsten Koruma. Pasif modu, Microsoft Defender Virüsten Koruma tarama ve güncelleştirme izinlerine izin verir, ancak tehditleri düzeltmez. Buna ek olarak, Uç nokta [veri](configure-real-time-protection-microsoft-defender-antivirus.md) kaybını önleme [(DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) dağıt olmadığı sürece gerçek Zamanlı Koruma yoluyla davranış izleme pasif modu altında kullanılamaz.

Sınırlı düzenli tarama olarak [bilinen bir başka](limited-periodic-scanning-microsoft-defender-antivirus.md) özellik de, dönemsel tarama Microsoft Defender Virüsten Koruma otomatik olarak kapatacak şekilde ayarlanmış olan son kullanıcılar tarafından kullanılabilir. Bu özellik, Microsoft Defender Virüsten Koruma bir dizi algılama kullanarak üçüncü taraf virüsten koruma yazılımıyla birlikte dosyaları düzenli aralıklarla taramanızı sağlar.

> [!IMPORTANT]
> Kurumsal ortamlarda sınırlı düzenli tarama önerilmez. Bu modda çalışan tüm özellikleri Microsoft Defender Virüsten Koruma algılama, yönetim ve raporlama özellikleri, etkin modla karşılaştırıldığında azaltıldı.

### <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma uyumluluğu](microsoft-defender-antivirus-compatibility.md)
- [Microsoft Defender Virüsten Koruma Windows Güvenliği seçin](microsoft-defender-security-center-antivirus.md)
