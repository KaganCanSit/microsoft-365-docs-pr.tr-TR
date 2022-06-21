---
title: Microsoft Defender Virüsten Koruma diğer güvenlik ürünleriyle uyumluluk
description: Diğer güvenlik ürünleri ve işletim sistemleriyle Microsoft Defender Virüsten Koruma hakkında bilgi edinin.
keywords: windows defender, uç nokta için defender, yeni nesil, virüsten koruma, uyumluluk, pasif mod
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 424d1974c16c5205052bec19b1235df28db2e2e3
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185794"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Virüsten Koruma diğer güvenlik ürünleriyle uyumluluk

**Şunlar için geçerlidir:**

- Microsoft Defender Virüsten Koruma
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platform**
- Windows

Microsoft Defender Virüsten Koruma aşağıdaki Windows sürümlerini çalıştıran uç noktalara otomatik olarak yüklenir:

- Windows 10 veya daha yenisi
- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya üzeri
- Windows Server 2016

Microsoft dışı başka bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü kullanıldığında ne olur? Microsoft Defender Virüsten Koruma başka bir virüsten koruma ürünüyle birlikte çalıştırabilir misiniz? Yanıtlar, işletim sisteminiz ve virüsten korumanızla birlikte [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) kullanıp kullanmadığınız gibi çeşitli faktörlere bağlıdır.

Bu makalede, Uç Nokta için Defender ile ve Uç Nokta için Defender olmadan Microsoft Defender Virüsten Koruma ve Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü ile neler olduğu açıklanmaktadır.

> [!IMPORTANT]
> - Microsoft Defender Virüsten Koruma Windows 10 ve 11, Windows Server 2022, Windows Server 2019, Windows Server, sürüm 1803 veya üzeri ve Windows Server 2016 çalıştıran cihazlarda kullanılabilir. 
> - Microsoft Defender Virüsten Koruma, [modern, birleşik çözüm](/microsoft-365/security/defender-endpoint/configure-server-endpoints) kullanılarak eklendiğinde Windows Server 2012 R2'de de kullanılabilir.
> - Windows 8.1'da, Microsoft Endpoint Configuration Manager aracılığıyla yönetilen [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)) olarak kurumsal düzeyde uç nokta virüsten koruma sunulur.
> - Windows Defender kurumsal düzeyde yönetim sağlamasa da [Windows Defender Windows 8.1 üzerindeki tüketici cihazları](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) için de sunulur.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Uç Nokta için Defender olmadan virüsten koruma

Bu bölümde, Uç Nokta için Defender'a eklenmemiş uç noktalarda Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma ürünlerinin yanı sıra Microsoft Defender Virüsten Koruma kullandığınızda ne olacağı açıklanmaktadır. 

> [!NOTE]
> Genel olarak, uç nokta için Defender'a eklenmemiş cihazlarda Microsoft Defender Virüsten Koruma pasif modda çalışmaz.

Aşağıdaki tabloda neler bekleyebileceğiniz özetlenmiştir:

|Windows sürümü|Birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Microsoft Defender Virüsten Koruma durumu|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Microsoft Defender Virüsten Koruma|Etkin mod|
|Windows 10 <br/> Windows 11|Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Devre dışı modu (otomatik olarak gerçekleşir)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, sürüm 1803 veya üzeri <br/> Windows Server 2016 <br/> Windows Server 2012 R2 |Microsoft Defender Virüsten Koruma|Etkin mod|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, sürüm 1803 veya üzeri <br/> Windows Server 2016 |Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Devre dışı (el ile ayarlama) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Windows Server'da, Microsoft dışı bir virüsten koruma ürünü çalıştırıyorsanız, çakışmayı önlemek için Microsoft Defender Virüsten Koruma kaldırabilirsiniz. Cihaz Uç Nokta için Microsoft Defender ekliyse pasif modda Microsoft Defender Virüsten Koruma kullanabilirsiniz (aşağıya bakın).

> [!TIP]
> Windows Server 2016 Microsoft Defender Virüsten Koruma yerine *Windows Defender Virüsten Koruma* görebilirsiniz.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender Virüsten Koruma ve Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma çözümleri

> [!NOTE]
> Genel olarak, Microsoft Defender Virüsten Koruma yalnızca Uç Nokta için Defender'a eklenen uç noktalarda pasif moda ayarlanabilir.

Microsoft Defender Virüsten Koruma etkin modda mı, pasif modda mı yoksa devre dışı mı çalıştırıldığında aşağıdakiler gibi çeşitli faktörlere bağlıdır:

- Uç noktaya hangi Windows sürümü yüklü
- uç noktada birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü Microsoft Defender Virüsten Koruma olup olmadığı
- Uç noktanın Uç Nokta için Defender'a eklenip eklenmediği

Aşağıdaki tabloda çeşitli senaryolarda Microsoft Defender Virüsten Koruma durumu özetlemektedir. 

| Windows sürümü   | Virüsten koruma/kötü amaçlı yazılımdan koruma çözümü  | Ekleme tarihi: <br/> Uç Nokta için Defender mı? | Microsoft Defender Virüsten Koruma durumu     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Microsoft Defender Virüsten Koruma | Evet  | Etkin mod | 
| Windows 10 <br/> Windows 11 | Microsoft Defender Virüsten Koruma | Hayır   | Etkin mod |
| Windows 10 <br/> Windows 11  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet  | Pasif mod (otomatik olarak) |
| Windows 10 <br/> Windows 11  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır   | Devre dışı modu (otomatik olarak)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, sürüm 1803 veya üzeri  | Microsoft Defender Virüsten Koruma  | Evet |         Etkin mod  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, sürüm 1803 veya üzeri   | Microsoft Defender Virüsten Koruma | Hayır  | Etkin mod |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, sürüm 1803 veya üzeri  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet  | Microsoft Defender Virüsten Koruma pasif moda ayarlanmalıdır (el ile) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, sürüm 1803 veya üzeri  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır  | Microsoft Defender Virüsten Koruma devre dışı bırakılmalıdır (el ile) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Microsoft Defender Virüsten Koruma | Evet | Etkin mod |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft Defender Virüsten Koruma | Hayır | Etkin mod |
| Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet | Microsoft Defender Virüsten Koruma pasif moda ayarlanmalıdır (el ile) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır | Microsoft Defender Virüsten Koruma devre dışı bırakılmalıdır (el ile) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Windows Server 2019'da Windows Server, sürüm 1803 veya üzeri, Windows Server 2016 veya R2 Windows Server 2012 Microsoft Defender Virüsten Koruma  Microsoft dışı bir virüsten koruma ürünü yüklediğinizde pasif moda otomatik olarak girmez. Bu gibi durumlarda, bir sunucuda birden çok virüsten koruma ürününün yüklü olmasından kaynaklanan sorunları önlemek için Microsoft Defender Virüsten Koruma pasif moda ayarlayın. PowerShell, grup ilkesi veya kayıt defteri anahtarı kullanarak Microsoft Defender Virüsten Koruma pasif moda ayarlayabilirsiniz. 

**Kayıt Defteri Anahtarı Yöntemi**

  Aşağıdaki kayıt defteri anahtarını ayarlayarak Microsoft Defender Virüsten Koruma pasif moda ayarlayabilirsiniz:
- Yolu: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Ad: `ForceDefenderPassiveMode`
- Türü: `REG_DWORD`
- Değer: `1`

**GPO Yöntemi**

- **Bilgisayar Yapılandırması** > **Yönetim Şablonları** >  **Windows Bileşenleri** >  Microsoft Defender Virüsten Koruma > grup ilkesi Yönetim **Düzenleyicisi'ni** açın.
- **Microsoft Defender Virüsten Koruma Kapat'ı** seçin.
- GPO'yı **Etkin** olarak ayarlayın.

"Get-MpComputerStatus" komutu ve "AMRunningMode" anahtarıyla PowerShell'de Koruma durumunu görüntüleyebilirsiniz.

## SYNTAX

```
PS C:\Users\tommaso> Get-MpComputerStatus


AMEngineVersion                  : 0.0.0.0
AMProductVersion                 : 4.18.2205.4
AMRunningMode                    : Not running
AMServiceEnabled                 : False
AMServiceVersion                 : 0.0.0.0
AntispywareEnabled               : False
AntispywareSignatureAge          : 4294967295
AntispywareSignatureLastUpdated  :
AntispywareSignatureVersion      : 0.0.0.0
AntivirusEnabled                 : False
AntivirusSignatureAge            : 4294967295
AntivirusSignatureLastUpdated    :
AntivirusSignatureVersion        : 0.0.0.0
BehaviorMonitorEnabled           : False
ComputerID                       : 5CF99D95-BF09-4B2E-9911-8E01C55642E5
ComputerState                    : 0
DefenderSignaturesOutOfDate      : False
DeviceControlDefaultEnforcement  : N/A
DeviceControlPoliciesLastUpdated : 01/01/1601 00:00:00
DeviceControlState               : N/A
FullScanAge                      : 4294967295
FullScanEndTime                  :
FullScanOverdue                  : False
FullScanRequired                 : False
FullScanSignatureVersion         :
FullScanStartTime                :
IoavProtectionEnabled            : False
IsTamperProtected                : False
IsVirtualMachine                 : True
LastFullScanSource               : 0
LastQuickScanSource              : 0
NISEnabled                       : False
NISEngineVersion                 : 0.0.0.0
NISSignatureAge                  : 4294967295
NISSignatureLastUpdated          :
NISSignatureVersion              : 0.0.0.0
OnAccessProtectionEnabled        : False
ProductStatus                    : 1
QuickScanAge                     : 4294967295
QuickScanEndTime                 :
QuickScanOverdue                 : False
QuickScanSignatureVersion        :
QuickScanStartTime               :
RealTimeProtectionEnabled        : False
RealTimeScanDirection            : 0
RebootRequired                   : False
TamperProtectionSource           : Signatures
TDTMode                          : N/A
TDTStatus                        : N/A
TDTTelemetry                     : N/A
TroubleShootingDailyMaxQuota     :
TroubleShootingDailyQuotaLeft    :
TroubleShootingEndTime           :
TroubleShootingExpirationLeft    :
TroubleShootingMode              :
TroubleShootingModeSource        :
TroubleShootingQuotaResetTime    :
TroubleShootingStartTime         :
PSComputerName                   :
```

Aşağıdaki örnekte, Defender durumu **Çalışmıyor** şeklindedir.

 > [!NOTE]
 > Pasif modun Windows Server 2016 ve Windows Server 2012 R2 çalıştıran uç noktalarda çalışması için bu uç noktaların[, Ekleme Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) açıklanan modern, birleşik çözümle birlikte eklenmelidir. 

(<a id="fn3">3</a>) Windows Server 2016, Windows Server 2012 R2, Windows Server sürüm 1803 veya üzeri, Windows Server 2019 ve Windows Server 2022'de, *eklenmeyen* bir uç noktada Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız Uç Nokta için Microsoft Defender, bir sunucuda birden çok virüsten koruma ürününün yüklü olmasından kaynaklanan sorunları önlemek için Microsoft Defender Virüsten Koruma el ile devre dışı bırakın/kaldırın.

> [!TIP]
> Windows Server 2016 Microsoft Defender Virüsten Koruma yerine *Windows Defender Virüsten Koruma* görebilirsiniz.

> [!IMPORTANT]
> - Microsoft Defender Virüsten Koruma yalnızca Windows 10 ve 11, Windows Server 2022, Windows Server 2019, Windows Server, sürüm 1803 veya üzeri, Windows Server 2016 ve çalıştıran cihazlarda kullanılabilir ve R2 Windows Server 2012.
> - Windows 8.1'da kurumsal düzeyde uç nokta virüsten koruma, Microsoft Endpoint Configuration Manager aracılığıyla yönetilen [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)) olarak sunulur.
> - Windows Defender kurumsal düzeyde yönetim sağlamasa da [Windows Defender Windows 8.1 üzerindeki tüketici cihazları](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) için de sunulur.

Uç Nokta için Defender, uç noktanıza yüklenen virüsten korumayı daha da genişleten özellikler içerir. Başka bir virüsten koruma çözümünün yanı sıra Microsoft Defender Virüsten Koruma çalıştırma avantajından yararlanabilirsiniz.

Örneğin, [blok modunda uç nokta algılama ve yanıt (EDR),](edr-in-block-mode.md) Microsoft Defender Virüsten Koruma birincil virüsten koruma ürünü olmasa bile kötü amaçlı yapıtlara karşı ek koruma sağlar. Bu tür özellikler, pasif modda veya etkin modda Microsoft Defender Virüsten Koruma yüklenmesini ve çalıştırılmasını gerektirir.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Microsoft Defender Virüsten Koruma pasif modda çalışması için gereksinimler

Microsoft Defender Virüsten Koruma pasif modda çalışması için uç noktaların aşağıdaki gereksinimleri karşılaması gerekir:

- İşletim sistemi: Windows 10 veya daha yenisi; Windows Server 2022, Windows Server 2019 veya Windows Server, sürüm 1803 veya üzeri
- Microsoft Defender Virüsten Koruma yüklü olmalıdır
- Microsoft dışı başka bir virüsten koruma/kötü amaçlı yazılımdan koruma ürünü yüklenmeli ve birincil virüsten koruma çözümü olarak kullanılmalıdır
- Uç noktalar Uç Nokta için Defender'a eklenmelidir

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Microsoft Defender Virüsten Koruma Uç Nokta için Defender işlevselliğini nasıl etkiler?

Uç Nokta için Defender, Microsoft Defender Virüsten Koruma pasif modda çalışıp çalışmayacağını etkiler. Ayrıca, Microsoft Defender Virüsten Koruma durumu Uç Nokta için Defender'daki belirli özellikleri etkileyebilir. Örneğin, Microsoft Defender Virüsten Koruma etkin veya pasif moddayken gerçek zamanlı koruma çalışır, ancak Microsoft Defender Virüsten Koruma devre dışı bırakıldığında veya kaldırıldığında çalışmaz.

> [!IMPORTANT]
> Bu bölümdeki tabloda, Microsoft Defender Virüsten Koruma etkin modda mı, pasif modda mı yoksa devre dışı mı yoksa kaldırılmış mı olduğuna göre etkin olarak çalışan veya çalışmayan özellikler ve özellikler özetlenir. Bu tablo yalnızca bilgilendirici olacak şekilde tasarlanmıştır. 
> Pasif modda Microsoft Defender Virüsten Koruma kullanıyorsanız veya engelleme [modunda](edr-in-block-mode.md) EDR kullanıyorsanız, ihlal sonrasında algılanan kötü amaçlı yapıtları algılamak ve düzeltmek için arka planda çalışan gerçek zamanlı koruma, bulut tabanlı koruma veya sınırlı düzenli tarama gibi **özellikleri kapatmayın**.

| Koruma | Microsoft Defender Virüsten Koruma <br/>(*Etkin mod*) | Microsoft Defender Virüsten Koruma <br/>(*Pasif mod*) | Microsoft Defender Virüsten Koruma <br/>(*Devre dışı veya kaldırıldı*) | [Engelleme modunda EDR ](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Gerçek zamanlı koruma](configure-real-time-protection-microsoft-defender-antivirus.md) | Evet | Bkz. not <sup>[[4](#fn4)]</sup> | Hayır | Hayır | 
| [Bulut tabanlı koruma](enable-cloud-protection-microsoft-defender-antivirus.md) | Evet | Hayır  | Hayır | Hayır | 
| [Ağ koruması](network-protection.md)  | Evet | Hayır | Hayır | Hayır | 
| [Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md)  | Evet | Hayır | Hayır  | Hayır | 
| [Sınırlı düzenli tarama kullanılabilirliği](limited-periodic-scanning-microsoft-defender-antivirus.md) | Hayır | Hayır | Evet | Hayır | 
| [Dosya tarama ve algılama bilgileri](review-scan-results-microsoft-defender-antivirus.md) | Evet | Evet<sup>[[5](#fn5)]</sup> | Hayır | Evet | 
| [Tehdit düzeltme](configure-remediation-microsoft-defender-antivirus.md) | Evet | Bkz. not <sup>[[6](#fn6)]</sup> | Hayır | Evet | 
| [Güvenlik bilgileri güncelleştirmeleri](manage-updates-baselines-microsoft-defender-antivirus.md) | Evet | Evet <sup>[[7](#fn7)]</sup> | Hayır | Evet <sup>[[7](#fn7)]</sup> | 
| [Veri Kaybı Önleme](../../compliance/endpoint-dlp-learn-about.md) | Evet | Evet | Hayır | Hayır |
| [Denetimli klasör erişimi](controlled-folders.md) | Evet |Hayır | Hayır | Hayır |
| [Web içeriği filtreleme](web-content-filtering.md) | Evet | Bkz. not <sup>[[8](#fn8)]</sup> | Hayır | Hayır |
| [Cihaz denetimi](device-control-report.md) | Evet | Evet | Hayır | Hayır |
| [PUA koruması](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Evet | Hayır | Hayır | Hayır |

(<a id="fn4">4</a>) Genel olarak, Microsoft Defender Virüsten Koruma pasif moddayken, gerçek zamanlı koruma etkin ve pasif modda olsa bile herhangi bir engelleme veya zorlama sağlamaz.

(<a id="fn5">5</a>) Microsoft Defender Virüsten Koruma pasif moddayken taramalar zamanlanmaz.

(<a id="fn6">6</a>) Microsoft Defender Virüsten Koruma pasif moddayken tehditleri düzeltmez. Ancak tehditler[, blok modunda uç nokta algılama ve yanıt (EDR)](edr-in-block-mode.md) ile düzeltilebilir. Bu durumda, Microsoft Defender Virüsten Koruma pasif modda olsa bile kaynak olarak Microsoft Defender Virüsten Koruma gösteren uyarılar görebilirsiniz.

(<a id="fn7">7</a>) Güvenlik bilgileri güncelleştirme temposu yalnızca Windows Update ayarları tarafından denetlenilir. Defender'a özgü güncelleştirme zamanlayıcıları (belirli bir zamanda günlük/haftalık, aralık tabanlı) ayarları yalnızca Microsoft Defender Virüsten Koruma etkin modda olduğunda çalışır. Pasif modda yoksayılırlar.

(<a id="fn8">8</a>) Microsoft Defender Virüsten Koruma pasif moddayken, web içeriği filtreleme yalnızca Microsoft Edge tarayıcı ile çalışır. 

> [!NOTE]
> [Uç nokta veri kaybı önleme](/microsoft-365/compliance/endpoint-dlp-learn-about) koruması, Microsoft Defender Virüsten Koruma etkin veya pasif modda olduğunda normal çalışmaya devam eder.

## <a name="important-notes"></a>Önemli notlar

- Microsoft Defender Virüsten Koruma, Uç Nokta için Defender veya Windows Güvenliği uygulaması tarafından kullanılan ilişkili hizmetlerden hiçbirini devre dışı bırakmayın, durdurmayın veya değiştirmeyin. Bu öneri *wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* veya *MsMpEng* hizmet ve işlemlerini içerir. Bu hizmetleri el ile değiştirmek cihazlarınızda ciddi kararsızlıklara neden olabilir ve ağınızı savunmasız hale getirebilir. Bu hizmetlerin devre dışı bırakılması, durdurulması veya değiştirilmesi, Microsoft dışı virüsten koruma çözümleri kullanılırken ve bilgilerinin [Windows Güvenliği uygulamasında](microsoft-defender-security-center-antivirus.md) nasıl görüntülendiği konusunda da sorunlara neden olabilir.

- Uç Nokta için Defender'da Microsoft Defender Virüsten Koruma birincil virüsten koruma çözümünüz olmasa bile EDR blok modunda açın. blok modunda EDR, cihazda bulunan kötü amaçlı öğeleri algılar ve düzelter (ihlal sonrası). Daha fazla bilgi için bkz. [blok modunda EDR](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma durumunu onaylama

Aşağıdaki tabloda açıklandığı gibi, Microsoft Defender Virüsten Koruma durumunu onaylamak için çeşitli yöntemlerden birini kullanabilirsiniz:

 | Yöntem | Yordam | 
 |:---|:---| 
 | Windows Güvenliği uygulaması | <ol><li>Windows cihazda Windows Güvenliği uygulamasını açın.</li><li>**Virüs ve tehdit koruması**’nı seçin.</li><li>**Who beni koruyor?** bölümünde **Sağlayıcıları yönet'i** seçin.</li><li>**Güvenlik sağlayıcıları** sayfasındaki **Virüsten Koruma'nın** altında **Microsoft Defender Virüsten Koruma açık olduğunu** görmeniz gerekir.</li></ol> | 
 | Görev Yöneticisi | <ol><li>Windows cihazda Görev Yöneticisi uygulamasını açın.</li><li>**Ayrıntılar** sekmesini seçin.</li><li>Listede **MsMpEng.exe** arayın.</li></ol> | 
 | Windows PowerShell <br/> (Microsoft Defender Virüsten Koruma çalıştığını onaylamak için) | <ol><li>Windows cihazda Windows PowerShell açın. </li><li>Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Get-Process`.</li><li>Sonuçları gözden geçirin. **Microsoft Defender Virüsten Koruma** etkinseMsMpEng.exegörmeniz gerekir.</li></ol> | 
 | Windows PowerShell <br/>(Virüsten korumanın yerinde olduğunu onaylamak için) |  [Get-MpComputerStatus PowerShell cmdlet'ini](/powershell/module/defender/get-mpcomputerstatus) kullanabilirsiniz.<ol><li>Windows cihazda Windows PowerShell açın.</li><li>Aşağıdaki PowerShell cmdlet'ini çalıştırın:<br/>`Get-MpComputerStatus | select AMRunningMode`.</li><li>Sonuçları gözden geçirin. Uç noktada Microsoft Defender Virüsten Koruma etkinse **Normal**, **Pasif** veya **EDR Blok Modu'nu** görmeniz gerekir. </li></ol> | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Microsoft Defender Virüsten Koruma durumları hakkında daha fazla ayrıntı

Bu bölümdeki tabloda, Microsoft Defender Virüsten Koruma ile görebileceğiniz çeşitli durumlar açıklanmaktadır.

 |  Durum  |  Neler olur?  | 
 |:---|:---| 
 |  Etkin mod  |  Etkin modda Microsoft Defender Virüsten Koruma makinede virüsten koruma uygulaması olarak kullanılır. Configuration Manager, grup ilkesi, Microsoft Intune veya diğer yönetim ürünleri kullanılarak yapılandırılan Ayarlar uygulanır. Dosyalar taranır, tehditler giderilir ve algılama bilgileri yapılandırma aracınızda (uç noktanın kendisindeki Configuration Manager veya Microsoft Defender Virüsten Koruma uygulaması gibi) bildirilir.  | 
 |  Pasif mod veya EDR Blok modu |  Pasif modda, virüsten koruma uygulaması olarak Microsoft Defender Virüsten Koruma kullanılmaz ve tehditler Microsoft Defender Virüsten Koruma tarafından *düzeltılmaz*. <p>Bununla birlikte, EDR [Blok Modunda çalışırken tehditler, blok modunda uç nokta algılama ve yanıt (EDR)](edr-in-block-mode.md) ile düzeltilebilir. <p> Dosyalar EDR tarafından taranır ve Uç Nokta için Defender hizmetiyle paylaşılan tehdit algılamaları için raporlar sağlanır. Microsoft Defender Virüsten Koruma pasif modda olsa bile kaynak olarak Microsoft Defender Virüsten Koruma gösteren uyarılar görebilirsiniz. <p> Microsoft Defender Virüsten Koruma pasif moddayken Microsoft Defender Virüsten Koruma [güncelleştirmelerini yönetmeye](manage-updates-baselines-microsoft-defender-antivirus.md) devam edebilirsiniz; ancak Microsoft Defender Virüsten Koruma  cihazlarınızın kötü amaçlı yazılımlara karşı gerçek zamanlı koruma sağlayan Microsoft dışı bir virüsten koruma ürünü varsa etkin moda geçin. <p> En iyi güvenlik katmanlı savunma ve algılama etkinliği için, Microsoft Defender Virüsten Koruma pasif modda çalışıyor olsa bile virüsten koruma ve kötü amaçlı yazılımdan koruma güncelleştirmelerinizi aldığınızdan emin olun. Bkz. [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md). <p> Pasif modun yalnızca makine [modern, birleşik çözüm](/microsoft-365/security/defender-endpoint/configure-server-endpoints) kullanılarak eklendiğinde Windows Server 2012 R2 & 2016'da desteklendiğini unutmayın.  | 
 |  Devre Dışı veya Kaldırıldı  |  Devre dışı bırakıldığında veya kaldırıldığında, virüsten koruma uygulaması olarak Microsoft Defender Virüsten Koruma kullanılmaz. Dosyalar taranmıyor ve tehditler düzeltilmiyor. <p> Microsoft Defender Virüsten Koruma devre dışı bırakmak veya kaldırmak genel olarak önerilmez; mümkünse, Microsoft dışı bir kötü amaçlı yazılımdan koruma/virüsten koruma çözümü kullanıyorsanız Microsoft Defender Virüsten Koruma pasif modda tutun. <p> Microsoft Defender Virüsten Koruma otomatik olarak devre dışı bırakıldığı durumlarda, Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma ürününün süresi dolarsa veya virüslere, kötü amaçlı yazılımlara veya diğer tehditlere karşı gerçek zamanlı koruma sağlamayı durdurursa otomatik olarak yeniden etkinleştirilebilir. Microsoft Defender Virüsten Koruma otomatik olarak yeniden etkinleştirilmesi, uç noktalarınızda virüsten korumanın korunmasına yardımcı olur. <p> Microsoft dışı bir virüsten koruma uygulaması kullanıyorsanız tehditleri düzenli aralıklarla denetlemek için Microsoft Defender Virüsten Koruma altyapısıyla birlikte çalışan [sınırlı düzenli tarama](limited-periodic-scanning-microsoft-defender-antivirus.md) da kullanabilirsiniz.  | 

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows istemcilerinde Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Engelleme modunda EDR ](edr-in-block-mode.md)
- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](/microsoft-365/compliance/endpoint-dlp-learn-about)
