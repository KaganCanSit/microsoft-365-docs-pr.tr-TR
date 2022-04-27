---
title: Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama
description: Microsoft Defender Virüsten Koruma koruma ve ürün güncelleştirmelerini nasıl alacağını yönetin.
keywords: güncelleştirmeler, güvenlik temelleri, koruma, güncelleştirmeleri zamanlama, güncelleştirmeleri zorlama, mobil güncelleştirmeler, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 6822f736cae73d7d4654f8b4310e0e397cffa677
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077486"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama

> [!IMPORTANT]
> Mart 2022 Microsoft Defender altyapı güncelleştirmesini (**1.1.19100.5**) uygulayan müşteriler yüksek kaynak kullanımıyla (CPU ve/veya bellek) karşılaşmış olabilir. Microsoft, önceki sürümde sunulan hataları gideren bir güncelleştirme (**1.1.19200.5**) yayımladı. Müşterilerin Virüsten Koruma Altyapısı'nın bu yeni altyapı derlemesine (**1.1.19200.5**) güncelleştirmeleri önerilir. Performans sorunlarının tamamen düzeltildiğinden emin olmak için, güncelleştirme uygulandıktan sonra makinelerin yeniden başlatılması önerilir. [Bkz. Aylık platform ve altyapı sürümleri](#monthly-platform-and-engine-versions) (bu makalede).

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planları 1 ve 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma güncel tutmak, cihazlarınızın yeni kötü amaçlı yazılımlara ve saldırı tekniklerine karşı korunmak için gereken en son teknolojiye ve özelliklere sahip olduğundan emin olmak için kritik öneme sahiptir. Microsoft Defender Virüsten Koruma [pasif modda](microsoft-defender-antivirus-compatibility.md) çalışıyor olsa bile virüsten korumanızı güncelleştirin. Microsoft Defender Virüsten Koruma güncel tutmayla ilgili iki tür güncelleştirme vardır:

- [Güvenlik bilgileri güncelleştirmeleri](#security-intelligence-updates)
- [Ürün güncelleştirmeleri](#product-updates)

> [!TIP]
> En güncel altyapı, platform ve imza tarihini görmek [için Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma yazılımlarına yönelik güvenlik bilgileri güncelleştirmelerini ziyaret edin](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Güvenlik bilgileri güncelleştirmeleri

Microsoft Defender Virüsten Koruma [bulut tabanlı koruma](cloud-protection-microsoft-defender-antivirus.md) kullanır (Microsoft Gelişmiş Koruma Hizmeti veya MAPS olarak da adlandırılır) ve ek koruma sağlamak için dinamik güvenlik bilgileri güncelleştirmelerini düzenli aralıklarla indirir. Bu dinamik güncelleştirmeler, KB2267602 güvenlik bilgileri güncelleştirmesi aracılığıyla düzenli güvenlik bilgileri güncelleştirmelerinin yerini almaz.

> [!NOTE]
> Güncelleştirmeler aşağıdaki KB'ler altında yayımlanıyor:
> - Microsoft Defender Virüsten Koruma: KB2267602
> - System Center Endpoint Protection: KB2461484

Bulut tabanlı koruma her zaman açıktır ve çalışması için İnternet'e etkin bir bağlantı gerektirir. Güvenlik bilgileri güncelleştirmeleri zamanlanmış bir tempoda gerçekleşir (ilke aracılığıyla yapılandırılabilir). Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma'de Microsoft bulut tarafından sağlanan korumayı kullanma](cloud-protection-microsoft-defender-antivirus.md).

Son güvenlik bilgileri güncelleştirmelerinin listesi için bkz[. Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma yazılımları için güvenlik bilgileri güncelleştirmeleri](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Altyapı güncelleştirmeleri güvenlik bilgileri güncelleştirmelerine dahil edilir ve aylık düzende yayımlar.

## <a name="product-updates"></a>Ürün güncelleştirmeleri

Microsoft Defender Virüsten Koruma *platform* güncelleştirmeleri olarak bilinen [aylık güncelleştirmeler (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) gerektirir.

Güncelleştirmelerin dağıtımını aşağıdaki yöntemlerden biriyle yönetebilirsiniz:

- [Windows Sunucusu Güncelleştirme Hizmeti (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/sum/understand/software-updates-introduction)
- Microsoft'u dağıtmak ve güncelleştirmeleri ağınızdaki uç noktalara Windows için kullandığınız olağan yöntem.

Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma koruma güncelleştirmeleri için kaynakları yönetme](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Aylık güncelleştirmeler aşamalar halinde yayımlanır ve [bu da Window Server Update Services'nizde](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) birden çok paketin görünmesine neden olarak ortaya çıkar.
> - Bu makalede, geniş sürüm kanalında yer alan değişiklikler listelenmiştir. [En son geniş kanal sürümüne buradan bakın](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Aşamalı dağıtım işlemi hakkında daha fazla bilgi edinmek ve sonraki sürüm hakkında daha fazla bilgi edinmek için bkz. [Microsoft Defender güncelleştirmeleri için aşamalı dağıtım işlemini yönetme](manage-gradual-rollout.md).
> - Güvenlik bilgileri güncelleştirmeleri hakkında daha fazla bilgi edinmek için bkz[. Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma yazılımlarına yönelik güvenlik bilgileri güncelleştirmeleri](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Microsoft Defender işlemlerinin listesini arıyorsanız **[mde-urls çalışma kitabını indirin](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)** ve **ardından Microsoft Defender İşlemleri** çalışma sayfasını seçin. mde-urls çalışma kitabı, [ara sunucudaki Uç Nokta için Microsoft Defender hizmet URL'lerine erişimi etkinleştirme](configure-proxy-internet.md) bölümünde açıklandığı gibi ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini de listeler.

## <a name="monthly-platform-and-engine-versions"></a>Aylık platform ve altyapı sürümleri

Platform güncelleştirmesini güncelleştirme veya yükleme hakkında bilgi için bkz. [Windows Defender kötü amaçlı yazılımdan koruma platformu için güncelleştirme](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Tüm güncelleştirmelerimiz

- Performans geliştirmeleri
- Hizmet verilebilirlik iyileştirmeleri
- Tümleştirme geliştirmeleri (Bulut, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Mart-2022 *UPDATE* (Platform: 4.18.2203.5 | Motor: 1.1.19200.5)</summary>

*Mart 2022 Microsoft Defender altyapı güncelleştirmesini (**1.1.19100.5**) uygulayan müşteriler yüksek kaynak kullanımıyla (CPU ve/veya bellek) karşılaşmış olabilir. Microsoft, önceki sürümde sunulan hataları gideren bir güncelleştirme (**1.1.19200.5**) yayımladı. Müşterilerin Virüsten Koruma Altyapısı'nın bu yeni altyapı derlemesine (**1.1.19200.5**) güncelleştirmeleri önerilir. Performans sorunlarının tamamen düzeltildiğinden emin olmak için, güncelleştirme uygulandıktan sonra makinelerin yeniden başlatılması önerilir.*

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.363.817.0**<br/>
&ensp;Yayın tarihi: **22 Nisan 2022**<br/>
&ensp;Platform: **4.18.2203.5**<br/>
&ensp;Motor: **1.1.19200.5**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.19200.5 <br/>
Güvenlik bilgileri güncelleştirme sürümü: 1.363.817.0<br/>

### <a name="whats-new"></a>Yenilikler

- Önceki Mart 2022 Microsoft Defender altyapı güncelleştirmesi (1.1.19100.5) ile ilgili yüksek kaynak kullanımı (CPU ve/veya bellek) ile ilgili sorunları giderir

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details><details>
<summary>Mart-2022 (Platform: 4.18.2203.5 | Motor: 1.1.19100.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.361.1449.0**<br/>
&ensp;Yayın tarihi: **7 Nisan 2022**<br/>
&ensp;Platform: **4.18.2203.5**<br/>
&ensp;Motor: **1.1.19100.5**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.19100.5 <br/>
Güvenlik bilgileri güncelleştirme sürümü: 1.361.1449.0<br/>

### <a name="whats-new"></a>Yenilikler

- Outlook eklentisini engelleyen [saldırı yüzeyi azaltma kuralı](attack-surface-reduction.md) için düzeltme eklendi 
- Kısa süreli işlemlerle ilgili [davranış izleme](configure-protection-features-microsoft-defender-antivirus.md) performansı sorununa yönelik düzeltme eklendi 
- [AMSI](/windows/win32/amsi/antimalware-scan-interface-portal) dışlaması için düzeltme eklendi 
- Geliştirilmiş [kurcalama koruması](prevent-changes-to-security-settings-with-tamper-protection.md) özellikleri 
- Yapılandırma kullanılırken `SharedSignaturesPath` bazı durumlarda [gerçek zamanlı korumanın](configure-protection-features-microsoft-defender-antivirus.md) devre dışı bırakılmasına yönelik bir düzeltme eklendi (Parametre hakkında `SharedSignaturesPath` daha fazla ayrıntı için bkz[. Set-MpPreference](/powershell/module/defender/set-mppreference))

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details><details>
<summary>Şubat-2022 (Platform: 4.18.2202.4 | Motor: 1.1.19000.8)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.361.14.0**<br/>
&ensp;Yayın tarihi: **14 Mart 2022**<br/>
&ensp;Platform: **4.18.2202.4**<br/>
&ensp;Motor: **1.1.19000.8**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.19000.8 <br/>
Güvenlik bilgileri güncelleştirme sürümü: 1.361.14.0 <br/>

### <a name="whats-new"></a>Yenilikler

- Algılama ve davranış izleme mantığında iyileştirmeler
- Hatalı pozitif tetikleme saldırı yüzeyi azaltma algılamaları düzeltildi
- EDR ve Gelişmiş Tehdit Avcılığı algılama uyarılarının daha iyi aslına uygunluğuna neden olan düzeltme eklendi
- Defender artık bildirim açılır pencerelerinde özel bildirimleri desteklemez. GPO/Intune/SCCM ve belgeler bu değişikliği yansıtacak şekilde değiştirildi.
- Çıkarılabilir depolama birimine yazılan dosyaların hem bilgilerini hem de kopyalarını yakalamaya yönelik geliştirmeler. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control, çıkarılabilir depolama medyası](device-control-removable-storage-access-control.md).
- SmartScreen hizmetine ulaşılamıyorsa geliştirilmiş trafik çıkışı 
- Kimlik doğrulama gereksinimleri olan ara sunucuları kullanan müşteriler için bağlantı geliştirmeleri
- Ağ FileShares için VDI cihaz güncelleştirme hatası düzeltildi 
- Blok modunda EDR artık yeni CSP'lerle ayrıntılı cihaz hedeflemeyi destekliyor. Bkz[. Blok modunda uç nokta algılama ve yanıt (EDR).](edr-in-block-mode.md)

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details><details>
<summary>Ocak-2022 (Platform: 4.18.2201.10 | Motor: 1.1.18900.2)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.357.8.0**<br/>
&ensp;Yayın tarihi: **9 Şubat 2022**<br/>
&ensp;Platform: **4.18.2201.10**<br/>
&ensp;Motor: **1.1.18900.2**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.18900.2 <br/>
Güvenlik bilgileri güncelleştirme sürümü: 1.357.8.0 <br/>

### <a name="whats-new"></a>Yenilikler

- Filtreleme performansında davranış izleme geliştirmeleri
- TrustedInstaller'a Sağlamlaştırma
- Kurcalama koruması geliştirmeleri
- `ScanScheduleTime` [Yerine Set-MpPreference](/powershell/module/defender/set-mppreference) içindeki yeni `ScanScheduleOffest` cmdlet'i eklendi. Bu ilke, zamanlanmış tarama gerçekleştirmek için gece yarısından sonraki dakika sayısını yapılandırıyor.
- `-ServiceHealthReportInterval` [Set-MpPreference](/powershell/module/defender/set-mppreference) ayarı eklendi. Bu ilke zamanlanmış tarama gerçekleştirmek için zaman aralığını (dakika cinsinden) yapılandırıyor.
- `AllowSwitchToAsyncInspection` [Set-MpPreference](/powershell/module/defender/set-mppreference) ayarı eklendi. Bu ilke, zaman uyumlu olarak denetlenen ağ akışlarının denetlenip doğrulandıktan sonra zaman uyumsuz denetime geçmesine olanak tanıyan bir performans iyileştirmesi sağlar.
- v2 güncelleştirmelerini Performans Analizi: Uzak PowerShell ve PowerShell 7.x desteği eklendi. [Microsoft Defender Virüsten Koruma için bkz. Performans çözümleyicisi](tune-performance-defender-antivirus.md).
- Microsoft Defender Virüsten Koruma ağ inceleme sistemi sürücüsündeki olası yinelenen paket hatası düzeltildi.

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Önceki sürüm güncelleştirmeleri: Yalnızca teknik yükseltme desteği

Yeni bir paket sürümü yayımlandıktan sonra, önceki iki sürüme yönelik destek yalnızca teknik desteğe indirgener. Bu bölümde listelenen sürümlerden eski sürümler ve yalnızca teknik yükseltme desteği için sağlanır.<br/><br/>

<details>
<summary>Kasım-2021 (Platform: 4.18.2111.5 | Motor: 1.1.18800.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.355.2.0**<br/>
&ensp;Yayın tarihi: **9 Aralık 2021**<br/>
&ensp;Platform: **4.18.2111.5**<br/>
&ensp;Motor: **1.1.18800.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

Altyapı sürümü: 1.1.18800.4 Güvenlik bilgileri güncelleştirme sürümü: 1.355.2.0

### <a name="whats-new"></a>Yenilikler

- Exchange sunucularda belirli yoğun senaryoların CPU kullanım verimliliği iyileştirildi
- Defender PowerShell modülünde Get-MpComputerStatus altına yeni cihaz denetimi durum alanları eklendi. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control](device-control-removable-storage-access-control.md).
- PowerShell ile ayarlandığında değerin kaldırılamamasına neden olan `SharedSignatureRoot` hata düzeltildi
- Uç Nokta için Microsoft Defender [kurcalama korumasının](prevent-changes-to-security-settings-with-tamper-protection.md) açık olduğunu belirtmesine rağmen kurcalama korumasının etkinleştirilemediği hata düzeltildi
- Microsoft Defender Virüsten Koruma aracı için performans çözümleyicisine desteklenebilirlik ve hata düzeltmeleri eklendi. Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma için performans çözümleyicisi](tune-performance-defender-antivirus.md).   
   - için PowerShell ISE desteği eklendi `New-MpPerformanceRecording`
   - için hata hataları düzeltildi `Get-MpPerformanceReport -TopFilesPerProcess`
   - PowerShell 7.x, uzak oturumlar ve PowerShell ISE'de kullanırken `New-MpPerformanceRecording` performans kaydı oturum sızıntısı düzeltildi


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ekim-2021 (Platform: 4.18.2110.6 | Motor: 1.1.18700.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.353.3.0**<br/>
&ensp;Yayın tarihi: **28 Ekim 2021**<br/>
&ensp;Platform: **4.18.2110.6**<br/>
&ensp;Motor: **1.1.18700.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

Altyapı sürümü: 1.1.18700.4 Güvenlik bilgileri güncelleştirme sürümü: 1.353.3.0

### <a name="whats-new"></a>Yenilikler

- Dosya aktarım protokolü (FTP) ağ trafiği kapsamı iyileştirmeleri
- Windows Server 2016 üzerinde çalışan Exchange Server Microsoft Defender CPU kullanımını azaltmaya yönelik düzeltme
- Tarama kesintileri için düzeltme
- Engellenen kurcalama girişimlerinin Güvenlik Merkezi'nde görünmemesiyle ilgili uyarılar için düzeltme
- Microsoft Defender hizmetinde kurcalama dayanıklılığı iyileştirmeleri

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Eylül-2021 (Platform: 4.18.2109.6 | Motor: 1.1.18600.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.351.7.0**<br/>
&ensp;Yayın tarihi: **7 Ekim 2021**<br/>
&ensp;Platform: **4.18.2109.6**<br/>
&ensp;Motor: **1.1.18600.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

Altyapı sürümü: 1.1.18600.4 Güvenlik bilgileri güncelleştirme sürümü: 1.351.7.0

### <a name="whats-new"></a>Yenilikler
- Microsoft Defender Virüsten Koruma altyapısı ve platform güncelleştirmeleri için yeni gecikme halkası. Bu halkayı tercih eden cihazlar, güncelleştirmeleri 48 saatlik bir gecikmeyle alır. Yeni gecikme halkası yalnızca kritik ortamlar için önerilir. Bkz. [Microsoft Defender güncelleştirmeleri için aşamalı dağıtım işlemini yönetme](manage-gradual-rollout.md).
- Microsoft Defender güncelleştirme aşamalı dağıtım işleminde iyileştirmeler

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ağustos-2021 (Platform: 4.18.2108.7 | Motor: 1.1.18500.10)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.349.22.0**<br/>
&ensp;Yayın tarihi: **2 Eylül 2021**<br/>
&ensp;Platform: **4.18.2108.7**<br/>
&ensp;Motor: **1.1.18500.10**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Davranış izleme altyapısında iyileştirmeler
- [Microsoft Defender Virüsten Koruma için yeni performans çözümleyicisi](tune-performance-defender-antivirus.md) yayımlandı
- kötü amaçlı DLL'leri yüklemeye karşı sağlamlaştırılmış Microsoft Defender Virüsten Koruma
- Microsoft Defender Virüsten Koruma TrustedInstaller atlamaya karşı sağlamlaştırılmış
- Dosya değişikliği bildirimlerini Human-Operated Ransomware (HumOR) için daha fazla veri içerecek şekilde genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Temmuz-2021 (Platform: 4.18.2107.4 | Motor: 1.1.18400.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.345.13.0**<br/>
&ensp;Yayın tarihi: **5 Ağustos 2021**<br/>
&ensp;Platform: **4.18.2107.4**<br/>
&ensp;Motor: **1.1.18400.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Windows Taşınabilir Cihazlar için cihaz denetimi desteği eklendi
- İstenmeyebilecek uygulamalar (PUA) koruması tüketiciler için varsayılan olarak açıktır (Bkz. [İstenmeyebilecek uygulamalar varsayılan olarak engellenir](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- grup ilkesi Nesne tarafından yönetilen sistemler için zamanlanmış taramalar, kullanıcı tarafından yapılandırılan tarama süresine uygun olacaktır
- Davranış izleme altyapısında iyileştirmeler

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok

<br/>
</details><details>
<summary> Haziran-2021 (Platform: 4.18.2106.5 | Motor: 1.1.18300.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.343.17.0**<br/>
&ensp;Yayın tarihi: **28 Haziran 2021**<br/>
&ensp;Platform: **4.18.2106.5**<br/>
&ensp;Motor: **1.1.18300.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Microsoft Defender güncelleştirmelerinin aşamalı dağıtım sürecini yönetmek için yeni denetimler. Bkz. [Microsoft Defender güncelleştirmeleri için aşamalı dağıtım işlemini yönetme](manage-gradual-rollout.md).
- Davranış izleme altyapısında iyileştirme
- Kötü amaçlı yazılımdan koruma tanımlarının dağıtımında iyileştirmeler
- Genişletilmiş Edge ağ olay incelemeleri

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Mayıs 2021 (Platform: 4.18.2105.4 | Motor: 1.1.18200.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.341.8.0**<br/>
&ensp;Yayın tarihi: **3 Haziran 2021**<br/>
&ensp;Platform: **4.18.2105.4**<br/>
&ensp;Motor: **1.1.18200.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- [Davranış izlemede iyileştirmeler](client-behavioral-blocking.md)
- [Ağ koruma](network-protection.md) bildirimi filtreleme özelliği düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Nisan-2021 (Platform: 4.18.2104.14 | Motor: 1.1.18100.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.337.2.0**<br/>
&ensp;Yayın tarihi: **26 Nisan 2021**  (Motor: 1.1.18100.6 yayın tarihi: 5 Mayıs 2021)<br/>
&ensp;Platform: **4.18.2104.14**<br/>
&ensp;Motor: **1.1.18100.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Daha fazla davranış izleme mantığı
- Geliştirilmiş çekirdek modu anahtar günlükçü algılaması
- [Microsoft Defender güncelleştirmeleri](manage-gradual-rollout.md) için aşamalı dağıtım işlemini yönetmek için yeni denetimler eklendi


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Mart-2021 (Platform: 4.18.2103.7 | Motor: 1.1.18000.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.335.36.0**<br/>
&ensp;Yayın tarihi: **2 Nisan 2021**<br/>
&ensp;Platform: **4.18.2103.7**<br/>
&ensp;Motor: **1.1.18000.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Davranış İzleme altyapısında iyileştirme
- Genişletilmiş ağ deneme yanılma saldırısı risk azaltmaları
- [Kurcalama Koruması](prevent-changes-to-security-settings-with-tamper-protection.md) etkinleştirildiğinde daha fazla başarısız kurcalama girişimi olay oluşturma

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Şubat-2021 (Platform: 4.18.2102.3 | Motor: 1.1.17900.7)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.333.7.0**<br/>
&ensp;Yayın tarihi: **9 Mart 2021**<br/>
&ensp;Platform: **4.18.2102.3**<br/>
&ensp;Motor: **1.1.17900.7**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- [Kurcalama koruması](prevent-changes-to-security-settings-with-tamper-protection.md) aracılığıyla iyileştirilmiş hizmet kurtarma
- Kurcalama koruma kapsamını genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ocak-2021 (Platform: 4.18.2101.9 | Motor: 1.1.17800.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.327.1854.0**<br/>
&ensp;Yayın tarihi: **2 Şubat 2021**<br/>
&ensp;Platform: **4.18.2101.9**<br/>
&ensp;Motor: **1.1.17800.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Kabuk kodu açıklarını algılama geliştirmeleri
- Kimlik bilgisi çalma girişimleri için daha fazla görünürlük
- Microsoft Defender Virüsten Koruma hizmetlerinde antitampering özelliklerinde iyileştirmeler
- ARM x64 öykünmesi için geliştirilmiş destek
- Düzeltme: EDR Engelle bildirimi, gerçek zamanlı koruma ilk algılamayı gerçekleştirdikten sonra tehdit geçmişinde kalıyor

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Kasım-2020 (Platform: 4.18.2011.6 | Motor: 1.1.17700.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.327.1854.0**<br/>
&ensp;Yayın tarihi: **03 Aralık 2020**<br/>
&ensp;Platform: **4.18.2011.6**<br/>
&ensp;Motor: **1.1.17700.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- [SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) durum desteği günlüğü iyileştirildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ekim-2020 (Platform: 4.18.2010.7 | Motor: 1.1.17600.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.327.7.0**<br/>
&ensp;Yayın tarihi: **29 Ekim 2020**<br/>
&ensp;Platform: **4.18.2010.7**<br/>
&ensp;Motor: **1.1.17600.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Özel tehdit kategorileri için yeni açıklamalar
- Geliştirilmiş öykünme özellikleri
- Geliştirilmiş ana bilgisayar adresi izin verme/engelleme özellikleri
- Defender CSP'de yerel kullanıcı dışlamalarının birleştirilmesini yoksaymak için yeni seçenek

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok
<br/>
</details><details>
<summary> Eylül-2020 (Platform: 4.18.2009.7 | Motor: 1.1.17500.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.325.10.0**<br/>
&ensp;Yayın tarihi: **01 Ekim 2020**<br/>
&ensp;Platform: **4.18.2009.7**<br/>
&ensp;Motor: **1.1.17500.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Karantinadaki dosyaları geri yüklemek için yönetici izinleri gereklidir
- XML biçimlendirilmiş olaylar artık destekleniyor
- Dışlama birleştirmelerini yoksaymak için CSP desteği
- Yeni yönetim arabirimleri:
   - UDP İncelemesi
   - Server 2019'da Ağ Koruması
   - Ağ Koruması için IP Adresi dışlamaları
- TPM ölçümlerine daha iyi görünürlük
- VBA modülü taraması Office iyileştirildi

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok
<br/>
</details>
<details>
<summary> Ağustos-2020 (Platform: 4.18.2008.9 | Motor: 1.1.17400.5)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.323.9.0**<br/>
&ensp;Yayın tarihi: **27 Ağustos 2020**<br/>
&ensp;Platform: **4.18.2008.9**<br/>
&ensp;Motor: **1.1.17400.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Daha fazla telemetri olayı ekleme
- Geliştirilmiş tarama olayı telemetrisi
- Bellek taramaları için geliştirilmiş davranış izleme
- Geliştirilmiş makro akışları taraması
- Get-MpComputerStatus PowerShell cmdlet'ine eklendi `AMRunningMode`
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) yoksayılır. Microsoft Defender Virüsten Koruma, başka bir virüsten koruma programı algıladığında otomatik olarak kapanır.


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Temmuz-2020 (Platform: 4.18.2007.8 | Motor: 1.1.17300.4)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.321.30.0**<br/>
&ensp;Yayın tarihi: **28 Temmuz 2020**<br/>
&ensp;Platform: **4.18.2007.8**<br/>
&ensp;Motor: **1.1.17300.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- BITS için geliştirilmiş telemetri
- Geliştirilmiş Authenticode kod imzalama sertifikası doğrulaması

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Haziran-2020 (Platform: 4.18.2006.10 | Motor: 1.1.17200.2)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.319.20.0**<br/>
&ensp;Yayın tarihi: **22 Haziran 2020**<br/>
&ensp;Platform: **4.18.2006.10**<br/>
&ensp;Motor: **1.1.17200.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- [Destek günlüklerinin konumunu](./collect-diagnostic-data.md) belirtme olanağı
- Pasif modda agresif yakalama taraması atlanıyor.
- Defender'ın tarifeli bağlantılarda güncelleştirmesine izin ver
- Önbelleğe alma devre dışı bırakıldığında performans ayarlaması düzeltildi
- Kayıt defteri sorgusu düzeltildi
- ADMX'te tarama süresi rastgele kullanımı düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Mayıs 2020 (Platform: 4.18.2005.4 | Motor: 1.1.17100.2)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.317.20.0**<br/>
&ensp;Yayın tarihi: **26 Mayıs 2020**<br/>
&ensp;Platform: **4.18.2005.4**<br/>
&ensp;Motor: **1.1.17100.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Tarama olayları için geliştirilmiş günlük kaydı
- Geliştirilmiş kullanıcı modu kilitlenme işlemesi.
- Kurcalama koruması için olay izleme eklendi
- AMSI Örneği gönderimi düzeltildi
- AMSI Bulut engellemesi düzeltildi
- Güvenlik güncelleştirmesi yükleme günlüğü düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Nisan-2020 (Platform: 4.18.2004.6 | Motor: 1.1.17000.2)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.315.12.0**<br/>
&ensp;Yayın tarihi: **30 Nisan 2020**<br/>
&ensp;Platform: **4.18.2004.6**<br/>
&ensp;Motor: **1.1.17000.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- WDfilter geliştirmeleri
- Saldırı yüzeyi azaltma algılama olaylarına daha fazla eyleme dönüştürülebilir olay verileri ekleme
- Tanılama verileri ve WMI'deki sürüm bilgileri düzeltildi
- Platform güncelleştirmesinin ardından kullanıcı arabirimindeki yanlış platform sürümü düzeltildi
- Dosyasız tehdit koruması için dinamik URL intel'i
- UEFI tarama özelliği
- Güncelleştirmeler için günlüğü genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Mart-2020 (Platform: 4.18.2003.8 | Motor: 1.1.16900.2)</summary>

&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.313.8.0**<br/>
&ensp;Yayın tarihi: **24 Mart 2020**<br/>
&ensp;Platform: **4.18.2003.8**<br/>
&ensp;Motor: **1.1.16900.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- [MpCmdRun'a](./command-line-arguments-microsoft-defender-antivirus.md) CPU Azaltma seçeneği eklendi
- Tanılama özelliğini geliştirme
- güvenlik zekası zaman aşımını azaltma (5 dk)
- AMSI altyapısı iç günlük özelliğini genişletme
- İşlem engelleme bildirimini iyileştirme

### <a name="known-issues"></a>Bilinen Sorunlar
[**Düzeltildi**] Microsoft Defender Virüsten Koruma tarama çalıştırırken dosyaları atlar.

<br/>
</details>

<details>

<summary> Şubat-2020 (Platform: - | Motor: 1.1.16800.2)</summary>


&ensp;Güvenlik bilgileri güncelleştirme sürümü: **1.311.4.0**<br/>
&ensp;Yayın tarihi: **25 Şubat 2020**<br/>
&ensp;Platform/İstemci: **-**<br/>
&ensp;Motor: **1.1.16800.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Ocak-2020 (Platform: 4.18.2001.10 | Motor: 1.1.16700.2)</summary>


Güvenlik bilgileri güncelleştirme sürümü: **1.309.32.0**<br/>
Yayın tarihi: **30 Ocak 2020**<br/>
Platform/İstemci: **4.18.2001.10**<br/>
Motor: **1.1.16700.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Exchange ile WS2016'da BSOD düzeltildi
- TMP ağ yoluna yeniden yönlendirildiğinde platform güncelleştirmelerini destekleme
- Platform ve altyapı sürümleri [WDSI'ye](https://www.microsoft.com/en-us/wdsi/defenderupdates) eklenir <!-- The preceding URL must include "/en-us" -->
- Acil durum imza güncelleştirmesini [pasif moda](./microsoft-defender-antivirus-compatibility.md) genişletme
- 4.18.1911.3 askıda kalma sorununu düzeltme

### <a name="known-issues"></a>Bilinen Sorunlar

[**Düzeltildi**] [Modern bekleme modunu](/windows-hardware/design/device-experiences/modern-standby) kullanan cihazlar, koruma boşluğuna neden olan Windows Defender filtre sürücüsünde askıda kalmayla karşılaşabilir.  Etkilenen makineler müşteriye en son kötü amaçlı yazılımdan koruma platformuna güncelleştirilmemiş gibi görünür.
<br/>
> [!IMPORTANT]
> Bu güncelleştirme:
> - SHA2'yi desteklemek için platformun daha düşük sürümünü çalıştıran RS1 cihazları tarafından gereklidir;
> - asılı sorunları olan sistemler için yeniden başlatma bayrağı vardır;
> - Nisan 2020'de yeniden yayımlanır ve gelecekteki kullanılabilirliği korumak için daha yeni güncelleştirmelerle yenilenmez;
> - yeniden başlatma gereksinimi nedeniyle bir güncelleştirme olarak kategorilere ayrılmıştır; Ve
> - yalnızca [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update) ile sunulur.
<br/>
</details>

<details>
<summary> Kasım-2019 (Platform: 4.18.1911.3 | Motor: 1.1.16600.7)</summary>

Güvenlik bilgileri güncelleştirme sürümü: **1.307.13.0**<br/>
Yayın tarihi: **7 Aralık 2019**<br/>
Platform: **4.18.1911.3**<br/>
Motor: **1.1.17000.7**<br/>
Destek aşaması: **Destek yok**<br/>

### <a name="whats-new"></a>Yenilikler

- MpCmdRun izleme düzeyi düzeltildi
- WDFilter sürüm bilgileri düzeltildi
- Bildirimleri geliştirme (PUA)
- destek dosyalarına MRT günlükleri ekleme

### <a name="known-issues"></a>Bilinen Sorunlar
Bu güncelleştirme yüklendiğinde, cihazın en son platform sürümüne güncelleştirilebilmesi için 4.18.2001.10 atlama paketi gerekir.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>Microsoft Defender Virüsten Koruma platform desteği

Platform ve altyapı güncelleştirmeleri aylık tempoda sağlanır. Tam olarak desteklenmek için en son platform güncelleştirmelerini güncel tutun. Destek yapımız dinamiktir ve en son platform sürümünün kullanılabilirliğine bağlı olarak iki aşamaya dönüşmektedir:

- **Güvenlik ve Kritik Güncelleştirmeler hizmet aşaması** - En son platform sürümünü çalıştırırken kötü amaçlı yazılımdan koruma platformunda hem Güvenlik hem de Kritik güncelleştirmeleri almaya uygun olacaksınız.

- **Teknik Destek (Yalnızca) aşaması** - Yeni bir platform sürümü yayımlandıktan sonra, eski sürümler (N-2) desteği yalnızca teknik desteğe indirgenecektir. N-2'den eski platform sürümleri artık desteklenmeyecektir.*

\*Windows 10 sürümden (bkz. Windows 10 [sürümlerine dahil edilen platform sürümü](#platform-version-included-with-windows-10-releases)) en son platform sürümüne yükseltmeler için teknik destek sunulmaya devam edecektir.

Teknik destek (yalnızca) aşamasında, ticari olarak makul destek olayları Microsoft Müşteri Hizmetleri & Desteği ve Microsoft'un yönetilen destek teklifleri (Premier Destek gibi) aracılığıyla sağlanacaktır. Destek olayı daha fazla rehberlik için geliştirmeye yükseltme gerektiriyorsa, güvenlikle ilgili olmayan bir güncelleştirme gerektiriyorsa veya bir güvenlik güncelleştirmesi gerektiriyorsa, müşterilerin en son platform sürümüne veya ara güncelleştirmeye (*) yükseltmesi istenir.

> [!NOTE]
> Microsoft Defender Virüsten Koruma Platform Güncelleştirmesi'ni el ile dağıtıyorsanız veya Microsoft Defender Virüsten Koruma Platform Update'i dağıtmak için bir betik veya Microsoft dışı bir yönetim ürünü kullanıyorsanız, sürümün `4.18.2001.10` [Microsoft Update Kataloğu'ndan](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10) yüklendiğinden emin olun  platform güncelleştirmesinin (N-2) en son sürümü yüklenmeden önce.

### <a name="platform-version-included-with-windows-10-releases"></a>Windows 10 sürümlerine dahil edilen platform sürümü

Aşağıdaki tabloda, en son Windows 10 sürümleriyle birlikte gönderilen Microsoft Defender Virüsten Koruma platform ve altyapı sürümleri sağlanır:<br/><br/>

|Windows 10 sürümü  |Platform sürümü  |Altyapı sürümü |Destek aşaması |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Teknik yükseltme desteği (yalnızca) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Teknik yükseltme desteği (yalnızca) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Teknik yükseltme desteği (yalnızca) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Teknik yükseltme desteği (yalnızca) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Teknik yükseltme desteği (yalnızca) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Teknik yükseltme desteği (yalnızca) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Teknik yükseltme desteği (yalnızca) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Teknik yükseltme desteği (yalnızca) |

Windows 10 sürüm bilgileri için [Windows yaşam döngüsü bilgi sayfasına bakın](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) güncelleştirmeleri

Windows 10 (Enterprise, Pro ve Home sürümleri), Windows Server 2019, Windows Server 2022 ve Windows Server 2016 işletim sistemi yükleme görüntülerinizi en son virüsten koruma ve kötü amaçlı yazılımdan koruma güncelleştirmeleriyle güncelleştirmenizi öneririz. İşletim sistemi yükleme görüntülerinizi güncel tutmak, koruma boşluğu oluşmasını önlemeye yardımcı olur.

Daha fazla bilgi için bkz. [Windows işletim sistemi yükleme görüntüleri için Microsoft Defender güncelleştirmesi](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20220321.1</summary>

&ensp;Paket sürümü: **20220321.1**<br/>
&ensp;Platform sürümü: **4.18.2202.4**<br/>
&ensp;Altyapı sürümü: **1.1.19000.8**<br/>
&ensp;İmza sürümü: **1.351.337.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok

<br/>
</details><details>
<summary>20220305.1</summary>

&ensp;Paket sürümü: **20220305.1**<br/>
&ensp;Platform sürümü: **4.18.2201.10**<br/>
&ensp;Altyapı sürümü: **1.1.18900.3**<br/>
&ensp;İmza sürümü: **1.359.1405.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok

<br/>
</details><details>
<summary>20220203.1</summary>

&ensp;Paket sürümü: **20220203.1**<br/>
&ensp;Platform sürümü: **4.18.2111.5**<br/>
&ensp;Altyapı sürümü: **1.1.18900.2**<br/>
&ensp;İmza sürümü: **1.357.32.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>20220105.1</summary>

&ensp;Paket sürümü: **20220105.1**<br/>
&ensp;Platform sürümü: **4.18.2111.5**<br/>
&ensp;Altyapı sürümü: **1.1.18800.4**<br/>
&ensp;İmza sürümü: **1.355.1482.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2112.01</summary>

&ensp;Paket sürümü: **1.1.2112.01**<br/>
&ensp;Platform sürümü: **4.18.2110.6**<br/>
&ensp;Altyapı sürümü: **1.1.18700.4**<br/>
&ensp;İmza sürümü: **1.353.2283.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2111.02</summary>

&ensp;Paket sürümü: **1.1.2111.02**<br/>
&ensp;Platform sürümü: **4.18.2110.6**<br/>
&ensp;Altyapı sürümü: **1.1.18700.4**<br/>
&ensp;İmza sürümü: **1.353.613.0**<br/>

### <a name="fixes"></a>Giderir
- Yerelleştirme dosyalarıyla ilgili bir sorun düzeltildi

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Paket sürümü: **1.1.2110.01**<br/>
&ensp;Platform sürümü: **4.18.2109.6**<br/>
&ensp;Altyapı sürümü: **1.1.18500.10**<br/>
&ensp;İmza sürümü: **1.349.2103.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2109.01</summary>

&ensp;Paket sürümü: **1.1.2109.01**<br/>
&ensp;Platform sürümü: **4.18.2107.4**<br/>
&ensp;Altyapı sürümü: **1.1.18400.5**<br/>
&ensp;İmza sürümü: **1.347.891.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2108.01</summary>

&ensp;Paket sürümü: **1.1.2108.01**<br/>
&ensp;Platform sürümü: **4.18.2107.4**<br/>
&ensp;Altyapı sürümü: **1.1.18300.4**<br/>
&ensp;İmza sürümü: **1.343.2244.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2107.02</summary>

&ensp;Paket sürümü: **1.1.2107.02**<br/>
&ensp;Platform sürümü: **4.18.2105.5**<br/>
&ensp;Altyapı sürümü: **1.1.18300.4**<br/>
&ensp;İmza sürümü: **1.343.658.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2106.01</summary>

&ensp;Paket sürümü: **1.1.2106.01**<br/>
&ensp;Platform sürümü: **4.18.2104.14**<br/>
&ensp;Altyapı sürümü: **1.1.18100.6**<br/>
&ensp;İmza sürümü: **1.339.1923.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2105.01</summary>

&ensp;Paket sürümü: **1.1.2105.01**<br/>
&ensp;Platform sürümü: **4.18.2103.7**<br/>
&ensp;Altyapı sürümü: **1.1.18100.6**<br/>
&ensp;İmza sürümü: **1.339.42.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Paket sürümü: **1.1.2104.01**<br/>
&ensp;Platform sürümü: **4.18.2102.4**<br/>
&ensp;Altyapı sürümü: **1.1.18000.5**<br/>
&ensp;İmza sürümü: **1.335.232.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Paket sürümü: **1.1.2103.01**<br/>
&ensp;Platform sürümü: **4.18.2101.9**<br/>
&ensp;Altyapı sürümü: **1.1.17800.5**<br/>
&ensp;İmza sürümü: **1.331.2302.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Paket sürümü: **1.1.2102.03**<br/>
&ensp;Platform sürümü: **4.18.2011.6**<br/>
&ensp;Altyapı sürümü: **1.1.17800.5**<br/>
&ensp;İmza sürümü: **1.331.174.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Paket sürümü: **1.1.2101.02**<br/>
&ensp;Platform sürümü: **4.18.2011.6**<br/>
&ensp;Altyapı sürümü: **1.1.17700.4**<br/>
&ensp;İmza sürümü: **1.329.1796.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Paket sürümü: **1.1.2012.01**<br/>
&ensp;Platform sürümü: **4.18.2010.7**<br/>
&ensp;Altyapı sürümü: **1.1.17600.5**<br/>
&ensp;İmza sürümü: **1.327.1991.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Paket sürümü: **1.1.2011.02**<br/>
&ensp;Platform sürümü: **4.18.2010.7**<br/>
&ensp;Altyapı sürümü: **1.1.17600.5**<br/>
&ensp;İmza sürümü: **1.327.658.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yenilenen Microsoft Defender Virüsten Koruma imzaları
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Paket sürümü: **1.1.2011.01**<br/>
&ensp;Platform sürümü: **4.18.2009.7**<br/>
&ensp;Altyapı sürümü: **1.1.17600.5**<br/>
&ensp;İmza sürümü: **1.327.344.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Yok
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Paket sürümü: **1.1.2011.01**<br/>
&ensp;Platform sürümü: **4.18.2008.9**<br/>
&ensp;Altyapı sürümü: **1.1.17400.5**<br/>
&ensp;İmza sürümü: **1.327.2216.0**<br/>

### <a name="fixes"></a>Giderir
- Yok

### <a name="additional-information"></a>Ek bilgiler
- Windows 10 RS1 veya üzeri işletim sistemi yükleme görüntüleri için destek eklendi.
<br/>
</details>

## <a name="more-resources"></a>Diğer kaynaklar

| Makale | Açıklama  |
|:---|:---|
|[Windows işletim sistemi yükleme görüntüleri için Microsoft Defender güncelleştirmesi](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | İşletim sistemi yükleme görüntüleriniz (WIM ve VHD dosyaları) için kötü amaçlı yazılımdan koruma güncelleştirme paketlerini gözden geçirin. Windows 10 (Enterprise, Pro ve Home sürümleri), Windows Server 2019, Windows Server 2022 ve Windows Server 2016 için Microsoft Defender Virüsten Koruma güncelleştirmeleri alın yükleme görüntüleri.  |
|[Koruma güncelleştirmelerinin nasıl indirileceğini ve uygulanacağını yönetme](manage-protection-updates-microsoft-defender-antivirus.md) | Koruma güncelleştirmeleri birçok kaynak üzerinden teslim edilebilir. |
|[Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Koruma güncelleştirmelerinin ne zaman indirilmesi gerektiğini zamanlayabilirsiniz. |
|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Uç nokta bir güncelleştirmeyi veya zamanlanmış taramayı kaçırırsa, kullanıcı bir sonraki oturum açtığında güncelleştirmeyi zorlayabilir veya tarama yapabilirsiniz. |
|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md) | Koruma güncelleştirmelerini başlangıçta veya belirli bulut tabanlı koruma olaylarının ardından indirilecek şekilde ayarlayabilirsiniz. |
|[Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Güncelleştirmelerin pil gücünde gerçekleşip gerçekleşmeyeceği gibi, özellikle mobil cihazlar ve sanal makineler için yararlı olan ayarları belirtebilirsiniz. |
| [EDR Algılayıcısı için Uç Nokta için Microsoft Defender güncelleştirme](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | 2021'de yayımlanan yeni Uç Nokta için Microsoft Defender birleşik çözüm paketinde bulunan EDR algılayıcısını (MsSense.exe) güncelleştirebilirsiniz.   |

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgi edinmek isterseniz, bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
