---
title: Microsoft Defender Virüsten Koruma güvenlik ürünleriyle uyumluluk sorunları
description: Diğer güvenlik Microsoft Defender Virüsten Koruma ve işletim sistemleriyle nasıl ilgili bilgi edinmek gerekir.
keywords: windows defender, uç nokta için Defender, yeni nesil, virüsten koruma, uyumluluk, pasif modu
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
ms.date: 03/14/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 25d01c597da0f3a3e108eeee27d3a0dfe5b58eb7
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512538"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Virüsten Koruma güvenlik ürünleriyle uyumluluk sorunları

**Aşağıdakiler için geçerlidir:**

- Microsoft Defender Virüsten Koruma
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

Microsoft Defender Virüsten Koruma, aşağıdaki sürümlerini çalıştıran uç noktalara otomatik olarak yüklenir Windows:

- Windows 10 veya daha yeni
- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya daha yenisi
- Windows Server 2016

Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü kullanılıyorsa ne olur? Başka bir virüsten Microsoft Defender Virüsten Koruma birlikte bu uygulamaları da çalıştırabilirsiniz mi? Yanıtlar, işletim sisteminiz gibi çeşitli faktörlere ve virüsten koruma yazılımınız ile birlikte Uç Nokta için [Microsoft Defender'ı](microsoft-defender-endpoint.md) kullanarak mı kullandığınıza bağlıdır.

Bu makalede, uç nokta için Defender Microsoft Defender Virüsten Koruma birlikte ve Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü ile neler olduğu açıklanmıştır.

> [!IMPORTANT]
> - Microsoft Defender Virüsten Koruma Windows 10 ve 11, Windows Server 2022, Windows Server 2019, Windows Server, sürüm 1803 veya daha yeni sürümleri ve Windows Server 2016. 
> - Microsoft Defender Virüsten Koruma, modern, birleşik Windows Server 2012 çözümü kullanılarak ekli olduğunda [R2'de de kullanılabilir](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - Windows 8.1'te, aracılığıyla yönetilen [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10) olarak kurumsal düzeyde uç nokta virüsten koruma sunulur Microsoft Endpoint Configuration Manager.
> - Windows Defender, mobil cihazlarda [tüketici cihazlar](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) için de Windows 8.1, ancak Windows Defender kurumsal düzeyde yönetim sağlamaz.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Uç nokta için Defender olmadan virüsten koruma

Bu bölümde, Uç nokta için Defender Microsoft Defender Virüsten Koruma a ekli olmayan uç noktalarda Microsoft virüsten koruma/kötü amaçlı yazılımdan koruma ürünleriyle birlikte ne olduğu açıklandı. 

> [!NOTE]
> Genel olarak Microsoft Defender Virüsten Koruma, Uç Nokta için Defender'a eklemeilen cihazlarda pasif modunda çalışmaz.

Aşağıdaki tabloda nelerin beklemesi gerekenler özetlenmiştir:

|Windows sürümü|Birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Microsoft Defender Virüsten Koruma durumu|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Microsoft Defender Virüsten Koruma|Etkin mod|
|Windows 10 <br/> Windows 11|Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Devre dışı modu (otomatik olarak gerçekleşir)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, sürüm 1803 veya daha yenisi <br/> Windows Server 2016 |Microsoft Defender Virüsten Koruma|Etkin mod|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, sürüm 1803 veya daha yenisi <br/> Windows Server 2016  |Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü|Devre dışı (el ile ayarlanmış) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Windows Server'da Microsoft olmayan bir virüsten koruma ürünü çalıştırıyorsanız, çakışmayı önlemek Microsoft Defender Virüsten Koruma virüsten koruma yazılımını kaldırabilirsiniz. Cihaz Uç Nokta için Microsoft Defender'a ekli ise pasif Microsoft Defender Virüsten Koruma kullanabilirsiniz (aşağıya bakın).

> [!TIP]
> Diğer Windows Server 2016, *geri Windows Defender Virüsten Koruma başka* *bir Microsoft Defender Virüsten Koruma*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender Virüsten Koruma Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma çözümleri

> [!NOTE]
> Genelde, Microsoft Defender Virüsten Koruma için Defender'a kabul edildi uç noktalarda pasif moduna ayarlanabilirsiniz.

Edil Microsoft Defender Virüsten Koruma modda mı, pasif modda mı yoksa devre dışı bırakılabilir mi gibi çeşitli faktörlere bağlıdır:

- Uç nokta üzerinde Windows sürümü yüklü
- Uç Microsoft Defender Virüsten Koruma birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü olup olmadığı
- Uç nokta için Defender'a uç noktanın eklemesi

Aşağıdaki tabloda, çeşitli senaryolarda Microsoft Defender Virüsten Koruma durum özetlenmiştir. 

| Windows sürümü   | Virüsten koruma/kötü amaçlı yazılımdan koruma çözümü  | Başlangıç <br/> Uç Nokta için Defender? | Microsoft Defender Virüsten Koruma durumu     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Microsoft Defender Virüsten Koruma | Evet  | Etkin mod | 
| Windows 10 <br/> Windows 11 | Microsoft Defender Virüsten Koruma | Hayır   | Etkin mod |
| Windows 10 <br/> Windows 11  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet  | Pasif modu (otomatik olarak) |
| Windows 10 <br/> Windows 11  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır   | Devre dışı modu (otomatik olarak)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows, sürüm 1803 veya daha yenisi  | Microsoft Defender Virüsten Koruma  | Evet |         Etkin mod  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows, sürüm 1803 veya daha yenisi   | Microsoft Defender Virüsten Koruma | Hayır  | Etkin mod |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows, sürüm 1803 veya daha yenisi  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet  | Microsoft Defender Virüsten Koruma pasif moduna (el ile) ayar olmalı <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows, sürüm 1803 veya daha yenisi  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır  | Microsoft Defender Virüsten Koruma devre dışı bırakmalısınız (el ile) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Microsoft Defender Virüsten Koruma | Evet | Etkin mod |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft Defender Virüsten Koruma | Hayır | Etkin mod |
| Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Evet | Microsoft Defender Virüsten Koruma pasif moduna (el ile) ayar olmalı <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü | Hayır | Microsoft Defender Virüsten Koruma devre dışı bırakmalısınız (el ile) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Windows Server 2019, Windows Server, sürüm 1803 veya daha yenisi, Windows Server 2016 veya Windows Server 2012 R2, Microsoft Defender Virüsten Koruma  Microsoft dışı bir virüsten koruma ürünü yükleytükten sonra pasif moduna otomatik olarak girmez. Böyle durumlarda, sunucuda Microsoft Defender Virüsten Koruma çok virüsten koruma ürünü olması nedeniyle oluşan sorunları önlemek için pasif moduna ayarlayın. PowerShell, Microsoft Defender Virüsten Koruma İlkesi veya kayıt defteri anahtarı kullanarak pasif moduna Microsoft Defender Virüsten Koruma. 

  Aşağıdaki kayıt Microsoft Defender Virüsten Koruma edilgen moduna geçer ve bunu pasif moduna:
- Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Ad: `ForceDefenderPassiveMode`
- Tür: `REG_DWORD`
- Değer: `1`

 > [!NOTE]
 > Pasif modunun Windows Server 2016 ve R2 Windows Server 2012 uç noktalarında çalışması için, bu uç noktaların Onboard Windows sunucularında açıklanan modern, birleşik [çözümle birlikte Windows gerekir](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) Windows Server 2016 veya Windows Server 2012 R2'de, Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız ve bu uç nokta Uç Nokta için Microsoft Defender'a ekli olarak yoksa, bu uç noktayı devre dışı Microsoft Defender Virüsten Koruma  ve birden çok virüsten koruma ürünü yüklü olması nedeniyle oluşan sorunları el ile engelleyebilirsiniz.

> [!TIP]
> Diğer Windows Server 2016, *geri Windows Defender Virüsten Koruma başka* *bir Microsoft Defender Virüsten Koruma*.

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma yalnızca Windows 10 ve 11, Windows Server 2022, Windows Server 2019, Windows Server, sürüm 1803 veya daha yenisi, Windows Server 2016 çalıştıran cihazlarda kullanılabilir ve Windows Server 2012 R2.
>
> Genel Windows 8.1, virüsten koruma yazılımı tarafından yönetilen kurumsal düzeyde [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)) virüsten koruma hizmeti Microsoft Endpoint Configuration Manager.
>
> Windows Defender, mobil cihazlarda [tüketici cihazlar](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) için de Windows 8.1, ancak Windows Defender kurumsal düzeyde yönetim sağlamaz.

Uç nokta için Defender, uç noktanıza yüklenmiş olan virüsten korumayı daha da genişleten özellikler içerir. Başka bir virüsten koruma çözümüyle birlikte Microsoft Defender Virüsten Koruma çalıştırmanın avantajından yararlanabilirsiniz.

Örneğin, Engelleme [modunda Uç nokta algılama ve EDR (Microsoft Defender Virüsten Koruma),](edr-in-block-mode.md) birincil virüsten koruma ürünü değilken bile kötü amaçlı yapıtlara karşı ek koruma sağlar. Bu tür becerilerin Microsoft Defender Virüsten Koruma edilgen modda veya etkin modda yüklenmeleri ve çalıştırılamalarını gerektirir.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Edilgen Microsoft Defender Virüsten Koruma modunda çalıştıracak sistem gereksinimleri

Uç noktaların Microsoft Defender Virüsten Koruma edilgen modda çalıştırıla çalışması için, uç noktaların aşağıdaki gereksinimleri karşılaması gerekir:

- İşletim sistemi: Windows 10 veya daha yenisi; Windows Server 2022, Windows Server 2019 veya Windows Server, sürüm 1803 veya daha yenisi
- Microsoft Defender Virüsten Koruma yüklü olması gerekir
- Microsoft dışı başka bir virüsten koruma/kötü amaçlı yazılımdan koruma ürünü, birincil virüsten koruma çözümü olarak yük olmalı ve kullanılmalıdır.
- Uç noktalar, Uç Nokta için Defender'a eklemeli

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Bu Microsoft Defender Virüsten Koruma, Uç nokta işlevi için Defender'ı nasıl etkiler?

Uç Nokta için Defender, Microsoft Defender Virüsten Koruma edilgen modda çalıştırıp çalıştırıılamay noktasını etkiler. Microsoft Defender Virüsten Koruma için Defender'daki bazı özellikleri de etkileyebilir. Örneğin, gerçek zamanlı koruma Microsoft Defender Virüsten Koruma veya pasif modundayken çalışır, ancak devre dışı Microsoft Defender Virüsten Koruma kaldırılamaz.

Bu bölümdeki tabloda, "Etkin modda mı, pasif modda mı, yoksa devre dışı mı/kaldırılamaz Microsoft Defender Virüsten Koruma etkin çalışıp çalışmadığınıza bağlı olarak etkin olarak çalışan özellik ve yetenekleri özetlenmiştir.

> [!IMPORTANT]
> Aşağıdaki tablo yalnızca bilgilendirmeyi yapmak üzere tasarlanmıştır. **Gerçek zamanlı** koruma, bulut teslimi koruması veya Microsoft Defender Virüsten Koruma'i pasif modunda kullanıyorsanız sınırlı düzenli tarama gibi özellikleri ya da ihlal sonrası algılayan kötü amaçlı yapıları saptamak ve düzeltmek için perde arkasında çalışan [EDR'i](edr-in-block-mode.md) engelleme modunda kapatmayın.

 | Koruma | Microsoft Defender Virüsten Koruma <br/>(*Etkin mod*) | Microsoft Defender Virüsten Koruma <br/>(*Pasif modu*) | Microsoft Defender Virüsten Koruma <br/>(*Devre dışı bırakıldı veya kaldırıldı*) | [EDR modunda çalışma](edr-in-block-mode.md) | 
 |:---|:---|:---|:---|:---| 
 | [Gerçek zamanlı koruma](configure-real-time-protection-microsoft-defender-antivirus.md) | Evet | Nota bakın <sup>[[4](#fn4)]</sup> | Hayır | Hayır | 
 | [Bulut teslimi koruma](enable-cloud-protection-microsoft-defender-antivirus.md) | Evet | Hayır  | Hayır | Hayır | 
 | [Ağ koruması](network-protection.md)  | Evet | Hayır | Hayır | Hayır | 
 | [Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md)  | Evet | Hayır | Hayır  | Hayır | 
 | [Sınırlı düzenli tarama kullanılabilirliği](limited-periodic-scanning-microsoft-defender-antivirus.md) | Hayır | Hayır | Evet | Hayır | 
 | [Dosya tarama ve algılama bilgileri](review-scan-results-microsoft-defender-antivirus.md) | Evet | Evet<sup>[[5](#fn5)]</sup> | Hayır | Evet | 
 | [Tehdit düzeltmesi](configure-remediation-microsoft-defender-antivirus.md) | Evet | Evet | Hayır | Evet | 
 | [Güvenlik zekası güncelleştirmeleri](manage-updates-baselines-microsoft-defender-antivirus.md) | Evet | Evet | Hayır | Evet | 

(<a id="fn4">4</a>) Genel olarak, Microsoft Defender Virüsten Koruma pasif modundayken, gerçek zamanlı koruma etkin ve pasif modunda olsa bile, hiçbir engelleme veya zorlama sağlamaz.

(<a id="fn5">5</a>) Microsoft Defender Virüsten Koruma pasif modundayken, taramalar zamanlanmaz.

> [!NOTE]
> [Microsoft 365 uç nokta veri kaybı önleme](/microsoft-365/compliance/endpoint-dlp-learn-about) koruması etkin veya pasif modunda Microsoft Defender Virüsten Koruma şekilde normal çalışmaya devam eder.

## <a name="important-notes"></a>Önemli notlar

- Microsoft Defender Virüsten Koruma, Endpoint için Defender veya Windows Güvenliği uygulaması tarafından kullanılan ilişkili hizmetleri devre dışı bırakmayın, durdurmayı veya Windows Güvenliği. Bu öneri *wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* veya *MsMpEng* hizmetlerini ve işlemlerini içerir. Bu hizmetlerin el ile değiştirilmesi, cihazlarınız üzerinde ciddi bir soruna neden olabilir ve ağın korunmasına neden olabilir. Bu hizmetlerin devre dışı bırakılması, durdurulması veya değiştirilmesi, Microsoft dışı virüsten koruma çözümlerini kullanırken ve bunların bilgilerin Windows Güvenliği [neden olabilir](microsoft-defender-security-center-antivirus.md).

- Uç nokta için Defender'EDR, birincil virüsten koruma çözümünüz Microsoft Defender Virüsten Koruma engelleme modunda açabilirsiniz. EDR modundayken düzeltme, cihazda bulunan kötü amaçlı öğeleri algılar ve düzeltmek (ihlal sonrası). Daha fazla bilgi için bkz[. EDR modunda çalışma](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Posta durumunu doğrulama Microsoft Defender Virüsten Koruma

Aşağıdaki tabloda açıklandığı gibi, posta iletisinin durumunu onaylamak Microsoft Defender Virüsten Koruma yöntemlerden birini kullanabilirsiniz:

 | Yöntem | Yordam | 
 |:---|:---| 
 | Windows Güvenliği uygulaması |  1. Windows cihazda, Windows Güvenliği açın.<br/>2. Virüs koruması **için &'i seçin**.<br/>3. **Sağlayıcılar Who koruma altında Sağlayıcılar'ı** **yönet'i seçin**.<br/>4. Güvenlik **sağlayıcıları sayfasındaki** Virüsten **Koruma'nın** altında Microsoft Defender Virüsten Koruma **olduğunu görebilirsiniz**. | 
 | Görev Yöneticisi |  1. Windows Yöneticisi uygulamasını açın.<br/>2. Ayrıntılar **sekmesini** seçin.<br/>3. Listede **MsMpEng.exe** bir liste seçin. | 
 | Windows PowerShell <br/> (Çalıştır bu Microsoft Defender Virüsten Koruma onaylamak için) |  1. Windows cihazda, Tamam'Windows PowerShell. <br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Get-Process`.<br/>3. Sonuçları gözden geçirin. Etkinse **MsMpEng.exe** diğer Microsoft Defender Virüsten Koruma görüyor olun. | 
 | Windows PowerShell <br/>(Virüsten korumanın var olduğunu onaylamak için) |  [Get-MpCompstatus PowerShell cmdlet'ini kullanabilirsiniz](/powershell/module/defender/get-mpcomputerstatus).<br/>1. Windows cihazda, Tamam'Windows PowerShell.<br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın:<br/> \|Get-MpComputerStatus AMRunningMode öğesini seçin <br/>3. Sonuçları gözden geçirin. Uç noktada Etkin **değilken Normal** Microsoft Defender Virüsten Koruma Edilgen'i görüyor olun.  | 
 | Komut İstemi |  1. Bir Windows Komut İstemi'ne açın.<br/>2. yazın ve `sc query windefend`Enter tuşuna basın.<br/>3. Pasif modunda çalışma Microsoft Defender Virüsten Koruma için sonuçları gözden geçirebilirsiniz.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Önemli eyaletler hakkında daha Microsoft Defender Virüsten Koruma bilgi

Bu bölümdeki tabloda, bu makalede gördüğünüz çeşitli eyaletler Microsoft Defender Virüsten Koruma.

 |  Durum  |  Ne olur?  | 
 |:---|:---| 
 |  Etkin mod  |  Etkin modda, Microsoft Defender Virüsten Koruma makinede virüsten koruma uygulaması olarak kullanılabilir. Ayarlar Yöneticisi, Grup İlkesi, Grup İlkesi, Microsoft Intune veya diğer yönetim ürünleri kullanılarak yapılandırılan diğer ürünler uygulanır. Dosyalar taranır, tehditlere düzeltmeler yapıldı ve algılama bilgileri yapılandırma aracınıza bildiriliyor (Configuration Manager veya uç noktanın kendi Microsoft Defender Virüsten Koruma uygulama gibi).  | 
 |  Pasif modu  |  Pasif modunda, Microsoft Defender Virüsten Koruma virüsten koruma uygulaması olarak kullanılamaz ve güvenlik duvarı tarafından düzeltme Microsoft Defender Virüsten Koruma. Öte yandan, tehditlerin düzeltmesi için [Uç nokta algılama ve EDR) engelleme modunda düzeltebilirsiniz](edr-in-block-mode.md). <br/><br/> Dosyalar başka bir EDR tarafından taranır ve uç nokta için Defender hizmetiyle paylaşılan tehdit algılamaları için raporlar sağlanır. Pasif modundayken bile Microsoft Defender Virüsten Koruma olarak e-postaların kaynak olarak Microsoft Defender Virüsten Koruma uyarılar görebilirler. <br/><br/> Microsoft Defender Virüsten Koruma edilgen moddayken, örneğin örneğin Microsoft Defender Virüsten Koruma güncelleştirmelerini yine de [yönetebilirsiniz; bununla](manage-updates-baselines-microsoft-defender-antivirus.md) birlikte, pasif Microsoft Defender Virüsten Koruma  etkin moda girer. Cihazlarınızı, Microsoft virüsten koruma ürünü olmayan ve kötü amaçlı yazılımlara karşı gerçek zamanlı koruma sağlayan bir virüsten koruma yazılımına sahipse etkin moda dönüştürebilirsiniz. <br/><br/> En iyi güvenlik katmanlı savunma ve algılama için, koruma yazılımınız ve kötü amaçlı yazılımlardan koruma güncelleştirmelerinizi edin edinin (Microsoft Defender Virüsten Koruma edilgen modda çalışıyor olsa bile). Bkz[. Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> Makine modern, birleşik çözüm kullanılarak işe Windows Server 2012 R2 & 2016'da pasif modunun yalnızca destek [olara destek olduğunu unutmayın](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  Devre dışı <br/><br/> veya <br/><br/> Kaldırıldı  |  Virüsten koruma uygulaması Microsoft Defender Virüsten Koruma devre dışı bırakılmıştır veya kaldırılmıştır. Dosyalar taranmaz ve tehditlere düzeltme olmaz. <br/><br/> Posta hizmet Microsoft Defender Virüsten Koruma devre dışı bırakma veya kaldırma genel olarak önerilmez; mümkünse, Microsoft dışı bir kötü amaçlı yazılım/virüsten koruma çözümü kullanıyorsanız Microsoft Defender Virüsten Koruma edilgen modda kullanın. <br/><br/> Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma ürününün süresi dolduğunda veya başka bir şekilde virüslere, kötü amaçlı yazılımlara ve diğer tehditlere karşı gerçek zamanlı koruma sağlamayı durdurursa, Microsoft Defender Virüsten Koruma otomatik olarak yeniden etkinleştirilebilir. Virüsten korumanın otomatik olarak Microsoft Defender Virüsten Koruma yeniden etkinleştirilmesi, virüsten korumanın uç noktalarınız üzerinde korunmasına yardımcı olur. <br/><br/> Ayrıca, Microsoft dışı [bir virüsten](limited-periodic-scanning-microsoft-defender-antivirus.md) koruma uygulaması kullanıyorsanız tehditleri düzenli olarak denetlemeniz için Microsoft Defender Virüsten Koruma altyapısıyla birlikte çalışan sınırlı düzenli tarama da kullanabilirsiniz.  | 


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma istemci Windows'i](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Virüsten Koruma Server'da Windows'i seçin](microsoft-defender-antivirus-on-windows-server.md)
- [EDR modunda çalışma](edr-in-block-mode.md)
- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](/microsoft-365/compliance/endpoint-dlp-learn-about)
