---
title: Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama
description: Güvenlik ve Microsoft Defender Virüsten Koruma güncelleştirmelerini nasıl aldığını yönetin.
keywords: güncelleştirmeler, güvenlik taban çizgilerini, koruma, güncelleştirmeleri zamanlama, güncelleştirmeleri zorlama, mobil güncelleştirmeler, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.date: 03/16/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: c6454704c6cabfd5136eeec565c3c57dca044250
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526902"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planları 1 ve 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Cihazlarınızı Microsoft Defender Virüsten Koruma kötü amaçlı yazılımlara ve saldırı tekniklerine karşı korumak için gereken en yeni teknoloji ve özelliklere sahip olmak için, güncel tutmak çok önemlidir. Pasif modunda çalışan bir virüsten koruma olsa bile, Microsoft Defender Virüsten Koruma korumanızı [güncelleştirin](microsoft-defender-antivirus-compatibility.md). Güncelleştirmelerin güncel tutmayla ilgili iki tür Microsoft Defender Virüsten Koruma vardır:

- Güvenlik zekası güncelleştirmeleri
- Ürün güncelleştirmeleri

> [!TIP]
> En güncel altyapıyı, platformu ve imza tarihini görmek için Güvenlik zekası güncelleştirmelerini ve Microsoft'Microsoft Defender Virüsten Koruma diğer kötü amaçlı [yazılımlardan koruma güncelleştirmelerini ziyaret edin](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Güvenlik zekası güncelleştirmeleri

Microsoft Defender Virüsten Koruma [koruma (](cloud-protection-microsoft-defender-antivirus.md)Microsoft Gelişmiş Koruma Hizmeti veya HARITALAR olarak da adlandırılan) kullanır ve düzenli aralıklarla ek koruma sağlamak için dinamik güvenlik zekası güncelleştirmelerini indirir. Bu dinamik güncelleştirmeler, güvenlik zekası güncelleştirmesi KB2267602 aracılığıyla düzenli güvenlik zekası güncelleştirmeleri yerine almaz.

> [!NOTE]
> Güncelleştirmeler, aşağıdaki KB'ler altında yayımlar:
> - Microsoft Defender Virüsten Koruma: KB2267602
> - System Center Endpoint Protection: KB2461484

Bulut teslimi koruması her zaman açık olur ve etkin bir Internet bağlantısı gerektirir. Güvenlik zekası güncelleştirmeleri zamanlanmış bir tempoda (ilke üzerinden yapılandırılabilir) gerçekleşir. Daha fazla bilgi için bkz[. Microsoft'un bulut tarafından sağlanan korumasını Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md).

En son güvenlik zekası güncelleştirmelerinin listesi için bkz. Güvenlik zekası [güncelleştirmeleri Microsoft Defender Virüsten Koruma Microsoft kötü amaçlı yazılımlardan koruma](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Güvenlik zekası güncelleştirmeleriyle birlikte alınan altyapı güncelleştirmeleri, aylık düzenli olarak yayın almaktadır.

## <a name="product-updates"></a>Ürün güncelleştirmeleri

Microsoft Defender Virüsten Koruma platform [güncelleştirmeleri olarak bilinen aylık güncelleştirmeler (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) *gerektirir*.

Güncelleştirmelerin dağıtımını aşağıdaki yöntemlerden biri aracılığıyla yönetebilirsiniz:

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/sum/understand/software-updates-introduction)
- Microsoft'u dağıtmak ve ağ bağlantı noktalarında Windows güncelleştirmelerini dağıtmak için alışılmış yönteminizdir.

Daha fazla bilgi için bkz[. Koruma güncelleştirmeleri Microsoft Defender Virüsten Koruma yönetme](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Aylık güncelleştirmeler aşamalar içinde yayımlar ve bunun sonucunda [Window Server Update Services'sınız birden çok paket görülebilir.](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
> - Bu makalede, geniş sürüm kanalında yer alan değişiklikler listelanmıştır. [Burada en son geniş kanal sürümüne bakın](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Aşamalı kademeli kademeli kademeli geçiş işlemi hakkında daha fazla bilgi edinmek ve sonraki sürüm hakkında daha fazla bilgi edinmek için bkz. Microsoft Defender güncelleştirmeleri için aşamalı yayınlanma [işlemini yönetme](manage-gradual-rollout.md).
> - Güvenlik zekası güncelleştirmeleri hakkında daha fazla bilgi edinmek için bkz. Güvenlik zekası [güncelleştirmeleri Microsoft Defender Virüsten Koruma Microsoft kötü amaçlı yazılımlardan koruma](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Microsoft Defender işlemlerinin listesini arıyorsanız **[mde-urls](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)** çalışma kitabını indirin ve **Microsoft Defender İşlemleri çalışma sayfasını** seçin. mde-urls çalışma kitabı ayrıca, proxy sunucusunda Uç Nokta için Microsoft Defender hizmet URL'lerine erişimi etkinleştirme konusunda açıklandığı gibi, ağ bağlantınız olması gereken hizmetleri ve bu hizmetlerle ilişkilendirilmiş [URL'leri de listeler](configure-proxy-internet.md).

## <a name="monthly-platform-and-engine-versions"></a>Aylık platform ve altyapı sürümleri

Platform güncelleştirmesini güncelleştirme veya yükleme hakkında bilgi için bkz. Kötü [amaçlı yazılımlardan koruma platformu Windows Defender güncelleştirme](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Tüm güncelleştirmelerimiz

- Performans iyileştirmeleri
- Hizmet kullanılabilirliği geliştirmeleri
- Tümleştirme geliştirmeleri (Bulut, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Şubat-2022 (Platform: 4.18.2202.4 | Altyapı: 1.1.19000.8)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.361.14.0**<br/>
&ensp;Yayınlanma tarihi: **14 Mart 2022**<br/>
&ensp;Platform: **4.18.2202.4**<br/>
&ensp;Altyapı: **1.1.19000.8**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.19000.8 <br/>
Güvenlik zekası güncelleştirme sürümü: 1.361.14.0 <br/>

### <a name="whats-new"></a>Yenilikler

- Algılama ve davranış izleme mantığında geliştirmeler
- Hatalı pozitif tetikleyen saldırı yüzeyini azaltma algılamaları düzeltildi
- Gelişmiş Sakslama ve Gelişmiş Saksı algılama uyarılarının EDR ilgili düzeltme eklendi
- Defender artık bildirim açılan pencerelerde özel bildirimleri desteklemez. Bu değişikliği yansıtacak şekilde değiştirilmiş GPO/Intune/SCCM ve belgeler.
- Çıkarılabilir depolama alanına yazılan dosyaların hem bilgilerini hem de kopyasını yakalamak için yapılan geliştirmeler. Daha fazla bilgi için bkz. Uç Nokta Cihaz Denetimi Çıkarılabilir için [Microsoft Defender Depolama Erişim Denetimi, çıkarılabilir depolama medyası](device-control-removable-storage-access-control.md).
- SmartScreen hizmeti ulaşılamaz durumdayken geliştirilmiş trafik çıkışı 
- Kimlik doğrulama gereksinimleri olan sunuculara sahip müşterilere yapılan bağlantı iyileştirmeleri
- Ağ FileShares için VDI cihaz güncelleştirme hatası düzeltildi 
- EDR modundaki çalışma artık yeni CSP'lerle ayrıntılı cihaz hedeflemeyi destekliyor. Bkz[. Uç nokta algılama ve yanıt (EDR) engelleme modunda](edr-in-block-mode.md).

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details><details>
<summary>Ocak-2022 (Platform: 4.18.2201.10 | Altyapı: 1.1.18900.2)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.357.8.0**<br/>
&ensp;Yayınlanma Tarihi: **9 Şubat 2022**<br/>
&ensp;Platform: **4.18.2201.10**<br/>
&ensp;Altyapı: **1.1.18900.2**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.18900.2 <br/>
Güvenlik zekası güncelleştirme sürümü: 1.357.8.0 <br/>

### <a name="whats-new"></a>Yenilikler

- Filtreleme performansında davranış izleme geliştirmeleri
- TrustedInstaller'a güvenme
- Tamper protection geliştirmeleri
- `ScanScheduleTime` `ScanScheduleOffest` [Set-MpPreference'in yeni cmdlet'iyle değiştirildi](/powershell/module/defender/set-mppreference). Bu ilke, zamanlanmış bir tarama yapmak için gece yarısından sonra olan dakika sayısını yapılandırıyor.
- Bu ayar `-ServiceHealthReportInterval` [Set-MpPreference olarak eklendi](/powershell/module/defender/set-mppreference). Bu ilke, zamanlanmış bir tarama yapmak için zaman aralığını yapılandırarak (dakika içinde).
- Bu ayar `AllowSwitchToAsyncInspection` [Set-MpPreference olarak eklendi](/powershell/module/defender/set-mppreference). Bu ilke, eşitlenen ağ akışları denetlenen bir eşitleme denetimine geçerek, denetlenen ve doğrulandıktan sonra bir eşitleme denetimine geçişe olanak sağlayan bir performans iyileştirmesi sağlar.
- Performans Çözümleyicisi v2 güncelleştirmeleri: Uzak PowerShell ve PowerShell 7.x desteği eklendi. Bkz[. Sistem için performans çözümleyicisi Microsoft Defender Virüsten Koruma](tune-performance-defender-antivirus.md).
- Ağ denetleme sistemi sürücüsünde olası Microsoft Defender Virüsten Koruma paket hatası düzeltildi.

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok

<br/><br/>
</details><details>
<summary>Kasım-2021 (Platform: 4.18.2111.5 | Altyapı: 1.1.18800.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.355.2.0**<br/>
&ensp;Yayınlanma tarihi: **9 Aralık 2021**<br/>
&ensp;Platform: **4.18.2111.5**<br/>
&ensp;Altyapı: **1.1.18800.4**<br/>
&ensp;Destek aşaması: **Güvenlik ve Kritik Güncelleştirmeler**<br/>

Altyapı sürümü: 1.1.18800.4 Güvenlik zekası güncelleştirme sürümü: 1.355.2.0

### <a name="whats-new"></a>Yenilikler

- Exchange sunucularında yoğun bazı senaryoların CPU kullanım Exchange iyileştirildi
- Defender PowerShell modülünde, Cihaz Get-MpComputerStatus altında yeni cihaz denetimi durumu alanları eklendi. Daha fazla bilgi için bkz. [Uç Nokta Cihaz Denetimi Çıkarılabilir için Microsoft Defender Depolama Erişimi Denetimi](device-control-removable-storage-access-control.md).
- PowerShell ile `SharedSignatureRoot` ayarlanırken değerin kaldırılmasına neden olan hata düzeltildi
- Microsoft Defender for [Endpoint,tamper protection'ın](prevent-changes-to-security-settings-with-tamper-protection.md) açık olduğunu belirtse bile, değişiklik korumasının etkinleştirilmesi hatası düzeltildi
- Çözümleyicisi aracına yönelik performans çözümleyicisi için destek Microsoft Defender Virüsten Koruma düzeltmeleri eklendi. Daha fazla bilgi için bkz. [Performans çözümleyicisi Microsoft Defender Virüsten Koruma](tune-performance-defender-antivirus.md).   
   - için PowerShell ISE desteği eklendi `New-MpPerformanceRecording`
   - Hataların hataları giderildi `Get-MpPerformanceReport -TopFilesPerProcess`
   - PowerShell 7.x, uzak `New-MpPerformanceRecording` oturumlar ve PowerShell ISE kullanırken performans kaydı oturumu sızıntı düzeltildi


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Önceki sürüm güncelleştirmeleri: Yalnızca teknik yükseltme desteği

Yeni bir paket sürümü yayınlandıktan sonra, önceki iki sürümün desteği yalnızca teknik destekle azaltıldı. Bu bölümde listelenenden daha eski sürümler ve yalnızca teknik yükseltme desteği için sağlanmıştır.<br/><br/>

<details>
<summary> Ekim-2021 (Platform: 4.18.2110.6 | Altyapı: 1.1.18700.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.353.3.0**<br/>
&ensp;Yayınlanma tarihi: **28 Ekim 2021**<br/>
&ensp;Platform: **4.18.2110.6**<br/>
&ensp;Altyapı: **1.1.18700.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

Altyapı sürümü: 1.1.18700.4 Güvenlik zekası güncelleştirme sürümü: 1.353.3.0

### <a name="whats-new"></a>Yenilikler

- Dosya aktarım protokolü (FTP) ağ trafiği kapsamına yapılan iyileştirmeler
- Windows'da çalışan bir kullanıcıda Microsoft Defender CPU Exchange Server kullanımını azaltmak için Windows Server 2016
- Tarama kesintilerini düzeltme
- Güvenlik Merkezi'nde görünmeye engellenmiş değiştirilme girişimleriyle ilgili uyarılar için düzeltme
- Microsoft Defender hizmetlerinde oynanma dayanıklılığı ile ilgili iyileştirmeler

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Eylül-2021 (Platform: 4.18.2109.6 | Altyapı: 1.1.18600.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.351.7.0**<br/>
&ensp;Yayınlanma tarihi: **7 Ekim 2021**<br/>
&ensp;Platform: **4.18.2109.6**<br/>
&ensp;Altyapı: **1.1.18600.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

Altyapı sürümü: 1.1.18600.4 Güvenlik zekası güncelleştirme sürümü: 1.351.7.0

### <a name="whats-new"></a>Yenilikler
- Yeni altyapı ve platform güncelleştirmeleri Microsoft Defender Virüsten Koruma gecikme halkası. Bu halkaya kabul olan cihazlar, 48 saatlik bir gecikmeyle güncelleştirmeler alır. Yeni gecikme halkası yalnızca kritik ortamlar için önerilir. Bkz [. Microsoft Defender güncelleştirmeleri için aşamalı geçiş işlemini yönetme](manage-gradual-rollout.md).
- Microsoft Defender güncelleştirmesine aşamalı olarak geçiş işlemi ile ilgili iyileştirmeler

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ağustos-2021 (Platform: 4.18.2108.7 | Altyapı: 1.1.18500.10)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.349.22.0**<br/>
&ensp;Yayınlanma Tarihi: **2 Eylül 2021**<br/>
&ensp;Platform: **4.18.2108.7**<br/>
&ensp;Altyapı: **1.1.18500.10**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Davranış izleme altyapısında geliştirmeler
- Çözümleyici için [yeni performans çözümleyicisi Microsoft Defender Virüsten Koruma](tune-performance-defender-antivirus.md)
- Microsoft Defender Virüsten Koruma kötü amaçlı URL'lerin yüklenmesine karşı koruma
- Microsoft Defender Virüsten Koruma Installer atlamalarına karşı uzaklaştırılmış site
- Fidye yazılımları (HumOR) için daha fazla veri Human-Operated için dosya değişikliği bildirimlerini genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Temmuz-2021 (Platform: 4.18.2107.4 | Altyapı: 1.1.18400.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.345.13.0**<br/>
&ensp;Yayınlanma tarihi: **5 Ağustos 2021**<br/>
&ensp;Platform: **4.18.2107.4**<br/>
&ensp;Altyapı: **1.1.18400.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Taşınabilir Cihazlar için cihaz denetimi Windows desteği eklendi
- İstenmeyen olabilecek uygulamalar (PUA) koruması tüketiciler için varsayılan olarak açıktır (Bkz. İstenmeyen uygulamalar [varsayılan olarak engellenir](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Grup İlkesi Nesnesi yönetilen sistemleri için zamanlanmış taramalar, kullanıcının yapılandırılan tarama süresine uymaya devam eder
- Davranış izleme altyapısında geliştirmeler

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok

<br/>
</details><details>
<summary> Haziran-2021 (Platform: 4.18.2106.5 | Altyapı: 1.1.18300.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.343.17.0**<br/>
&ensp;Yayınlanma tarihi: **28 Haziran 2021**<br/>
&ensp;Platform: **4.18.2106.5**<br/>
&ensp;Altyapı: **1.1.18300.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Microsoft Defender güncelleştirmelerinin aşamalı olarak uygulama işlemini yönetmek için yeni denetimler. Bkz [. Microsoft Defender güncelleştirmeleri için aşamalı geçiş işlemini yönetme](manage-gradual-rollout.md).
- Davranış izleme altyapısında geliştirme
- Kötü amaçlı yazılımdan koruma tanımlarının geliştirilmesi
- Genişletilmiş Edge ağ olayı denetimleri

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Mayıs-2021 (Platform: 4.18.2105.4 | Altyapı: 1.1.18200.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.341.8.0**<br/>
&ensp;Yayınlanma tarihi: **3 Haziran 2021**<br/>
&ensp;Platform: **4.18.2105.4**<br/>
&ensp;Altyapı: **1.1.18200.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Davranış [izlemede geliştirmeler](client-behavioral-blocking.md)
- Ağ [koruması bildirim](network-protection.md) filtreleme özelliği düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Nisan-2021 (Platform: 4.18.2104.14 | Altyapı: 1.1.18100.5)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.337.2.0**<br/>
&ensp;Yayımlanan: **26 Nisan 2021**  (Altyapı: 5 Mayıs 2021'de yayımlanan 1.1.18100.6)<br/>
&ensp;Platform: **4.18.2104.14**<br/>
&ensp;Altyapı: **1.1.18100.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- Daha fazla davranış izleme mantığı
- Geliştirilmiş çekirdek modu anahtar günlüğe kaydeden algılama
- Microsoft Defender güncelleştirmeleri için aşamalı olarak geçiş işlemini yönetmek için [yeni denetimler eklendi](manage-gradual-rollout.md)


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Mart-2021 (Platform: 4.18.2103.7 | Altyapı: 1.1.18000.5)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.335.36.0**<br/>
&ensp;Yayınlanma Tarihi: **2 Nisan 2021**<br/>
&ensp;Platform: **4.18.2103.7**<br/>
&ensp;Altyapı: **1.1.18000.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Davranış İzleme altyapısına geliştirme
- Genişletilmiş ağ force-force-attack risk azaltmaları
- Tamper [Protection](prevent-changes-to-security-settings-with-tamper-protection.md) etkinleştirildiğinde daha fazla değiştirilme girişimi (olay oluşturma) başarısız oldu

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Şubat-2021 (Platform: 4.18.2102.3 | Altyapı: 1.1.17900.7)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.333.7.0**<br/>
&ensp;Yayınlanma tarihi: **9 Mart 2021**<br/>
&ensp;Platform: **4.18.2102.3**<br/>
&ensp;Altyapı: **1.1.17900.7**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Tamper protection aracılığıyla geliştirilmiş [hizmet kurtarma](prevent-changes-to-security-settings-with-tamper-protection.md)
- Değişiklik koruma kapsamını genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ocak-2021 (Platform: 4.18.2101.9 | Altyapı: 1.1.17800.5)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.327.1854.0**<br/>
&ensp;Yayınlanma Tarihi: **2 Şubat 2021**<br/>
&ensp;Platform: **4.18.2101.9**<br/>
&ensp;Altyapı: **1.1.17800.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Kabukkodu açıkları kullanma algılama geliştirmeleri
- Kimlik bilgisi çalma girişimleri için daha fazla görünürlük
- Microsoft Defender Virüsten Koruma hizmetlerde antitaperpering özelliklerinde iyileştirmeler
- x64 emulation ARM geliştirilmiş destek
- Düzeltme: EDR koruma ilk algılaması yapıldıktan sonra tehdit geçmişinde kalır

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Kasım-2020 (Platform: 4.18.2011.6 | Altyapı: 1.1.17700.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.327.1854.0**<br/>
&ensp;Yayınlanma tarihi: **3 Aralık 2020**<br/>
&ensp;Platform: **4.18.2011.6**<br/>
&ensp;Altyapı: **1.1.17700.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- geliştirilmiş [SmartScreen durumu](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) desteği günlüğü

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details><details>
<summary> Ekim-2020 (Platform: 4.18.2010.7 | Altyapı: 1.1.17600.5)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.327.7.0**<br/>
&ensp;Yayınlanma tarihi: **29 Ekim 2020**<br/>
&ensp;Platform: **4.18.2010.7**<br/>
&ensp;Altyapı: **1.1.17600.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Özel tehdit kategorileri için yeni açıklamalar
- Geliştirilmiş emulation capabilities
- Geliştirilmiş ana bilgisayar adresi izin verme/engelleme özellikleri
- Defender CSP'de yerel kullanıcı dışlamalarını birleştirmeyi yoksaymak için yeni seçenek

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok
<br/>
</details><details>
<summary> Eylül-2020 (Platform: 4.18.2009.7 | Altyapı: 1.1.17500.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.325.10.0**<br/>
&ensp;Yayınlanma tarihi: **01 Ekim 2020**<br/>
&ensp;Platform: **4.18.2009.7**<br/>
&ensp;Altyapı: **1.1.17500.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Dosyaları karantinada geri yüklemek için yönetici izinleri gereklidir
- XML biçimli olaylar artık de desteklemektedir
- Dışlama birleştirmelerini yoksayma için CSP desteği
- Yeni yönetim arabirimleri:
   - UDP İncelemesi
   - Server 2019'da Ağ Koruması
   - Ağ Koruması için IP Adresi dışlamaları
- TPM ölçüleri için geliştirilmiş görünürlük
- VBA modülü Office tarama ile geliştirilmiş

### <a name="known-issues"></a>Bilinen Sorunlar

Bilinen sorun yok
<br/>
</details>
<details>
<summary> Ağustos-2020 (Platform: 4.18.2008.9 | Altyapı: 1.1.17400.5)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.323.9.0**<br/>
&ensp;Yayınlanma tarihi: **27 Ağustos 2020**<br/>
&ensp;Platform: **4.18.2008.9**<br/>
&ensp;Altyapı: **1.1.17400.5**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Daha fazla telemetri olayları ekleme
- Geliştirilmiş tarama olayı telemetrisi
- Bellek taramaları için geliştirilmiş davranış izleme
- Geliştirilmiş makro akışları tarama
- `AMRunningMode`Get-MpComputerStatus PowerShell cmdlet'ine eklendi
- [DisableAntiCcaware yoksayılır](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) . Microsoft Defender Virüsten Koruma bir virüsten koruma programı algılayana kadar otomatik olarak kapanır.


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Temmuz-2020 (Platform: 4.18.2007.8 | Altyapı: 1.1.17300.4)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.321.30.0**<br/>
&ensp;Yayınlanma tarihi: **28 Temmuz 2020**<br/>
&ensp;Platform: **4.18.2007.8**<br/>
&ensp;Altyapı: **1.1.17300.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- BITS için geliştirilmiş telemetri
- Geliştirilmiş Authenticode kod imzalama sertifika doğrulaması

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Haziran-2020 (Platform: 4.18.2006.10 | Altyapı: 1.1.17200.2)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.319.20.0**<br/>
&ensp;Yayınlanma tarihi: **22 Haziran 2020**<br/>
&ensp;Platform: **4.18.2006.10**<br/>
&ensp;Altyapı: **1.1.17200.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Destek günlüklerinin [konumunu belirtme olasılığı](./collect-diagnostic-data.md)
- Pasif modunda agresif yakalama taraması atlar.
- Defender'ın tarifeli bağlantılarda güncelleştirmesine izin ver
- Önbelleğe alma devre dışı bırakılabilirken performans ayarı düzeltildi
- Kayıt defteri sorgusu düzeltildi
- ADMX'te tarama süresi rastgeleliği düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Mayıs-2020 (Platform: 4.18.2005.4 | Altyapı: 1.1.17100.2)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.317.20.0**<br/>
&ensp;Yayınlanma tarihi: **26 Mayıs 2020**<br/>
&ensp;Platform: **4.18.2005.4**<br/>
&ensp;Altyapı: **1.1.17100.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- Tarama olayları için geliştirilmiş günlük
- Geliştirilmiş kullanıcı modu kilitlenme işleme.
- Tamper protection için olay izleme eklendi
- AMSI Örnek gönderimi düzeltildi
- AMSI Bulut engellemesi düzeltildi
- Güvenlik güncelleştirmesi yükleme günlüğü düzeltildi

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Nisan-2020 (Platform: 4.18.2004.6 | Altyapı: 1.1.17000.2)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.315.12.0**<br/>
&ensp;Yayınlanma Tarihi: **30 Nisan 2020**<br/>
&ensp;Platform: **4.18.2004.6**<br/>
&ensp;Altyapı: **1.1.17000.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler
- WDfilter geliştirmeleri
- Saldırı yüzeyini azaltma algılama etkinliklerine daha fazla işlem özelliği olan etkinlik verileri ekleyin
- Tanılama verilarında ve WMI'da sürüm bilgileri düzeltildi
- Platform güncelleştirmesinden sonra kullanıcı arabiriminde yanlış platform sürümü düzeltildi
- Dosyasız tehdit koruması için dinamik URL intel
- UEFI tarama özelliği
- Güncelleştirmeler için günlüğü genişletme

### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Mart-2020 (Platform: 4.18.2003.8 | Altyapı: 1.1.16900.2)</summary>

&ensp;Güvenlik zekası güncelleştirme sürümü: **1.313.8.0**<br/>
&ensp;Yayınlanma tarihi: **24 Mart 2020**<br/>
&ensp;Platform: **4.18.2003.8**<br/>
&ensp;Altyapı: **1.1.16900.4**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- [MPCmdRun'a eklenen CPU Azaltma seçeneği](./command-line-arguments-microsoft-defender-antivirus.md)
- Tanılama özelliğini geliştirme
- güvenlik zekası zaman aşımını azaltma (5 dk)
- AMSI altyapısı iç günlük özelliğini genişletme
- süreç engelleme bildirimini geliştirin

### <a name="known-issues"></a>Bilinen Sorunlar
[**Düzeltildi**] Microsoft Defender Virüsten Koruma çalıştırma bu dosyaları atlar.

<br/>
</details>

<details>

<summary> Şubat-2020 (Platform: - | Altyapı: 1.1.16800.2)</summary>


&ensp;Güvenlik zekası güncelleştirme sürümü: **1.311.4.0**<br/>
&ensp;Yayınlanma Tarihi: **25 Şubat 2020**<br/>
&ensp;Platform/İstemci: **-**<br/>
&ensp;Altyapı: **1.1.16800.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler


### <a name="known-issues"></a>Bilinen Sorunlar
Bilinen sorun yok
<br/>
</details>

<details>
<summary> Ocak-2020 (Platform: 4.18.2001.10 | Altyapı: 1.1.16700.2)</summary>


Güvenlik zekası güncelleştirme sürümü: **1.309.32.0**<br/>
Yayınlanma Tarihi: **30 Ocak 2020**<br/>
Platform/İstemci: **4.18.2001.10**<br/>
Altyapı: **1.1.16700.2**<br/>
&ensp;Destek aşaması: **Teknik yükseltme desteği (yalnızca)**<br/>

### <a name="whats-new"></a>Yenilikler

- WS2016'da BSOD ve Exchange
- TMP ağ yoluna yönlendir geldiğinde destek platformu güncelleştirmeleri
- Platform ve altyapı sürümleri [WDSI'ye eklenmiştir](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- Acil durum imza güncelleştirmesini [pasif moduna genişletme](./microsoft-defender-antivirus-compatibility.md)
- Düzeltme 4.18.1911.3 askıda kalma

### <a name="known-issues"></a>Bilinen Sorunlar

[**Düzeltildi**] [Modern bekleme](/windows-hardware/design/device-experiences/modern-standby) modunu kullanan cihazlar, koruma Windows Defender bir boşlukla sonuçlanan filtre sürücüsünde askıda kalmayla karşıtlık ile karşıtlık yaşanıyor.  Etkilenen makineler müşteriye, kötü amaçlı yazılımdan koruma platformuna güncelleştirilmemiş gibi görünür.
<br/>
> [!IMPORTANT]
> Bu güncelleştirme:
> - SHA2'yi desteklemek için platformun alt sürümünü çalıştıran RS1 cihazları için gerekli;
> - asılı sorunları olan sistemler için yeniden başlatma bayrağı vardır;
> - Nisan 2020'de yeniden yayınlanacak ve gelecekte kullanılabilirliği devam edecek yeni güncelleştirmelerle kullanımdan çıkarımayacak;
> - yeniden başlatma gereksinimi nedeniyle güncelleştirme olarak kategorilere ayrılmıştır; ve
> - yalnızca Güncelleştirme ile Windows [sunulur](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Kasım-2019 (Platform: 4.18.1911.3 | Altyapı: 1.1.16600.7)</summary>

Güvenlik zekası güncelleştirme sürümü: **1.307.13.0**<br/>
Yayınlanma tarihi: **7 Aralık 2019**<br/>
Platform: **4.18.1911.3**<br/>
Altyapı: **1.1.17000.7**<br/>
Destek aşaması: **Destek yok**<br/>

### <a name="whats-new"></a>Yenilikler

- MpCmdRun izleme düzeyi düzeltildi
- WDFilter sürüm bilgileri düzeltildi
- Bildirimleri geliştirme (PUA)
- destek dosyalarına MRT günlükleri ekleme

### <a name="known-issues"></a>Bilinen Sorunlar
Bu güncelleştirme yüklendikten sonra, cihazın en son platform sürümüne güncelleştirileblir olması için atlama paketi 4.18.2001.10'a ihtiyaç vardır.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>Microsoft Defender Virüsten Koruma platformu desteği

Platform ve altyapı güncelleştirmeleri aylık düzenli olarak sağlanır. Tamamen destek olmak için en son platform güncelleştirmelerini takip edin. Destek yapımız dinamiktir ve en son platform sürümünün kullanılabilirliğine bağlı olarak iki aşamalı olarak geliştirmektedir:

- **Güvenlik ve Kritik Güncelleştirmeler hizmet aşaması** - En son platform sürümünü çalıştıracaksanız kötü amaçlı yazılımdan koruma platformuna hem Güvenlik hem de Kritik güncelleştirmeleri almaya uygun olursınız.

- **Teknik Destek (Yalnızca) aşaması** - Yeni bir platform sürümü yayınlandıktan sonra, eski sürümler (N-2) için destek yalnızca teknik destekle azaltlanacak. N-2'den daha eski platform sürümleri artık destek desteklemez.*

\*Windows 10 sürümüne (bkz. Windows 10 platform sürümüne dahil edilen platform sürümü) en [son platform](#platform-version-included-with-windows-10-releases) sürümüne yükseltmeler için teknik destek sağlanacaktır.

Teknik destek (yalnızca) aşamasında, ticari olarak makul destek olayları Microsoft Müşteri Hizmetleri & Desteği ve Microsoft'un yönetilen destek teklifleri (Premier Destek gibi) aracılığıyla sağlanacaktır. Destek olayı daha ileri bir kılavuz için geliştirmenin geliştirilmesini gerektiriyorsa, güvenlikle ilgili olmayan bir güncelleştirme veya güvenlik güncelleştirmesi gerektiriyorsa, müşterilerden en son platform sürümüne veya ara güncelleştirmeye (*) yükseltmeleri istenecek.

> [!NOTE]
> Microsoft Defender Virüsten Koruma Platform Update'i el ile dağıtıyorsanız ya da Microsoft Defender Virüsten Koruma Platform Update'i dağıtmak için betik veya Microsoft dışı bir yönetim ürünü kullanıyorsanız, `4.18.2001.10` sürümün [Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10) Kataloğu'na yüklenmiş olduğundan emin olun  Platform Güncelleştirmesi'nin (N-2) en son sürümü yüklenmeden önce.

### <a name="platform-version-included-with-windows-10-releases"></a>Windows 10 sürümlerine dahil edilen platform sürümü

Aşağıdaki tabloda, en Microsoft Defender Virüsten Koruma sürümleriyle birlikte gelen platform ve Windows 10 sürümleri yer almaktadır:<br/><br/>

|Windows 10 sürümü  |Platform sürümü  |Engine sürümü |Destek aşaması |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Teknik yükseltme desteği (yalnızca) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Teknik yükseltme desteği (yalnızca) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Teknik yükseltme desteği (yalnızca) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Teknik yükseltme desteği (yalnızca) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Teknik yükseltme desteği (yalnızca) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Teknik yükseltme desteği (yalnızca) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Teknik yükseltme desteği (yalnızca) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Teknik yükseltme desteği (yalnızca) |

Yayın Windows 10 fazla bilgi için yaşam [Windows bilgi sayfası'ne bakın](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Dağıtım Resmi Servis ve Yönetimi (DISM) güncelleştirmeleri

En son virüsten koruma ve kötü amaçlı yazılımdan koruma güncelleştirmeleriyle Windows 10 (Enterprise, Pro ve Ev sürümleri), Windows Server 2019, Windows Server 2022 ve Windows Server 2016 işletim sistemi yükleme resimlerinizi güncelleştirmenizi öneririz. Işletim sistemi yükleme resimlerinizin güncel tutmanız, korumada boşluklardan kaçınmanıza yardımcı olur.

Daha fazla bilgi için bkz. [İşletim sisteminin yükleme Windows için Microsoft Defender güncelleştirmesi](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20220305.1</summary>

&ensp;Paket sürümü: **20220305.1**<br/>
&ensp;Platform sürümü: **4.18.2201.10**<br/>
&ensp;Altyapı sürümü: **1.1.18900.3**<br/>
&ensp;İmza sürümü: **1.359.1405.0**<br/>

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
- Yok

### <a name="additional-information"></a>Ek bilgiler
- İmzalar Microsoft Defender Virüsten Koruma yenilendi
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Paket sürümü: **1.1.2011.01**<br/>
&ensp;Platform sürümü: **4.18.2009.7**<br/>
&ensp;Altyapı sürümü: **1.1.17600.5**<br/>
&ensp;İmza sürümü: **1.327.344.0**<br/>

### <a name="fixes"></a>Düzeltmeler
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

### <a name="fixes"></a>Düzeltmeler
- Yok

### <a name="additional-information"></a>Ek bilgiler
- RS1 veya daha Windows 10 işletim sistemi yükleme resimleri için destek eklendi.
<br/>
</details>

## <a name="more-resources"></a>Diğer kaynaklar

| Makale | Açıklama  |
|:---|:---|
|[İşletim sisteminin yükleme görüntüleri Windows için Microsoft Defender güncelleştirmesi](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | OS yükleme resimleriniz (WIM ve VHD dosyaları) için kötü amaçlı yazılımdan koruma güncelleştirme paketlerini gözden geçirebilirsiniz. Microsoft Defender Virüsten Koruma (Windows 10 Enterprise, Pro ve Ev sürümleri), Windows Server 2019, Windows Server 2022 ve diğer sürümler için Windows Server 2016 yükleme resimleri.  |
|[Koruma güncelleştirmelerinin nasıl indirildikten ve uygulandığını yönetme](manage-protection-updates-microsoft-defender-antivirus.md) | Koruma güncelleştirmeleri birçok kaynak aracılığıyla teslim edilir. |
|[Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Koruma güncelleştirmelerinin ne zaman indirilleri gerektiğini zamanabilirsiniz. |
|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Uç nokta bir güncelleştirmeyi veya zamanlanmış taramayı kaçırırsa, kullanıcı bir sonraki oturum a oturum adedesinde güncelleştirmeyi zorlar veya taramayı zorlarsanız. |
|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md) | Koruma güncelleştirmelerini başlangıçta veya belirli bulut teslimi koruma olaylarını yükledikten sonra indirilecek şekilde kurabilirsiniz. |
|[Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Pil gücünde güncelleştirmelerin olup olmadığı gibi, özellikle mobil cihazlar ve sanal makinelerde yararlı olacak ayarları belirtebilirsiniz. |
| [EDR Algılayıcısı için Uç Nokta Güncelleştirmesi için Microsoft Defender](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | 2021'de EDR uç nokta için Microsoft Defender birleşik çözüm paketine dahil olan algılayıcı (MsSense.exe) algılayıcısı (MsSense.exe) algılayıcıyı güncelleştirebilirsiniz.   |
