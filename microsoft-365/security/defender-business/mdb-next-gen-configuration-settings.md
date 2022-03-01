---
title: İş için Microsoft Defender'da (önizleme) yeni nesil koruma yapılandırma ayarlarını anlama
description: İş için Microsoft Defender'da (önizleme) yeni nesil koruma için yapılandırma ayarlarını anlama
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a4fd47c04e063e049265f037568a768eb05b6cc7
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016703"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da (önizleme) yeni nesil yapılandırma ayarlarını anlama

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Defender'daki yeni nesil koruma (önizleme), güçlü virüsten koruma ve kötü amaçlı yazılımlardan koruma içerir. Varsayılan ilkeleriniz, üretkenliği engellemeden cihazlarınızı ve kullanıcılarınızı korumak üzere tasarlanmıştır; bununla birlikte, ilkelerinizi iş gereksinimlerinize uygun olarak özelleştirebilirsiniz. Microsoft Endpoint Manager kullanıyorsanız, güvenlik ilkelerinizi yönetmek için de bu bilgileri kullanabilirsiniz.

**Bu makalede şu açıklanmıştır**:

- [Yeni nesil koruma ayarları ve seçenekleri](#next-generation-protection-settings-and-options)
- [Defender For Business 'daki diğer önceden yapılandırılmış ayarlar (önizleme)](#other-preconfigured-settings-in-defender-for-business) 
- [İş için Defender varsayılan ayarları ve Microsoft Endpoint Manager](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Yeni nesil koruma ayarları ve seçenekleri

Aşağıdaki tabloda ayarlarınız ve seçenekleriniz listeledir:<br/><br/>

| Ayar | Açıklama |
|:---|:---|
| **Gerçek zamanlı koruma**  |  |
| **Gerçek zamanlı korumayı açma** | Varsayılan olarak etkinleştirildiğinde gerçek zamanlı koruma, kötü amaçlı yazılımları bulup cihazlarda çalıştırmayı durdurur. *Gerçek zamanlı korumanın açık tutmasını öneririz.*<br/><br/>Gerçek zamanlı koruma açık olduğunda aşağıdaki ayarları yapılandırr:<br/>- Davranış izleme açık ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- İndirilen tüm dosyalar ve ekler taranır ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Microsoft tarayıcılarında kullanılan betikler taranır ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **İlk görüşte engelle** | Varsayılan olarak etkin olan birinci görüşte engelle, algılama süresi içinde kötü amaçlı yazılımları engeller, çözümleme için örnek dosyaları gönderme sürenizi artırır (saniye olarak) ve algılama düzeyinizi Yüksek olarak ayarlar. *Blok'ları ilk görüşte açık tutmayı öneririz.*<br/><br/>İlk görüşte bloklar açık olduğunda, ilk kez görüntü için aşağıdaki Microsoft Defender Virüsten Koruma: <br/>- Şüpheli dosyaları engelleme ve tarama, Yüksek engelleme düzeyine ([CloudBlockLevel) ayarlanır](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)<br/>- Bir dosyanın engelleneceği ve denetleneceği saniye sayısı 50 saniye olarak ayarlanır ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**ÖNEMLİ**: İlk görüşte blok kapalı ise bu, görme engeli `CloudBlockLevel` `CloudExtendedTimeout` Microsoft Defender Virüsten Koruma.  |
| **Ağ korumasını açma** | Ağ koruması açık olduğunda, kimlik avı dolandırıcılığı, açıkları kullanan barındırma siteleri ve İnternet'e yönelik kötü amaçlı içeriğe karşı korunmaya yardımcı olur. Ayrıca, kullanıcıların ağ korumasını kapatmasını da sağlar.<br/><br/>Ağ koruması aşağıdaki modlardan biri olarak ayarlanabiliyor:<br/>- **Engelleme modu** (varsayılan ayardır) kullanıcıların güvenli değil olarak kabul edilen siteleri ziyaretlerini sağlar. *Ağ korumasını Engelleme modu olarak ayarlamayı öneririz.*<br/>- **Kullanıcıların güvenli** olmayan siteleri ziyaretlerine ve bu tür sitelerden ağ etkinliğini takiplerine olanak sağlayan Denetim modu <br/>- **Devre dışı modu**, kullanıcıların güvenli olmayan siteleri ziyaret veya bu tür sitelerden ağ etkinliğini takip eden siteleri ziyaretlerini engelleyen devre dışı modu |
| **Düzeltme**  |  |
| **İstenmeyen olabilecek uygulamaları (PUA) önlem alma** | PUA, güvenlik özelliklerinden kurtulmaya çalışan diğer, imzasız yazılımları ve yazılımdan kurtulmayı teklif eden reklam yazılımı, iş amaçlı yazılım yazılımlarını içerebilir. PUA bir virüs, kötü amaçlı yazılım veya başka tehdit türü gibi bir durumla karşı karşıya olmayabilir, ancak PUA cihaz performansını etkileyebilir.<br/><br/>PUA koruması, PUA olarak algılanan öğeleri engeller. PUA korumasını aşağıdaki ayarlardan biri olarak değiştirebilirsiniz: <br/>- **Enabled** (bu ayar varsayılandır) ve cihazlarda PUA olarak algılanan öğeleri engeller. *PUA korumasının etkin durumda tutmasını öneririz.*<br/>- **PUA** olarak algılanan öğeler üzerinde hiçbir eylem alan denetim modu <br/>- **Devre** dışı, PUA olabileceğini algılamaz veya bu öğeler üzerinde eyleme son |
| **Tarama**   |  |
| **Zamanlanmış tarama türü** | Cihazlarınıza haftalık virüsten koruma taraması çalıştırmayı göz önünde bulundurabilirsiniz. Aşağıdaki tarama türü seçeneklerinden birini seçebilirsiniz: <br/>- **Quickscan** , kayıt defteri anahtarları ve başlangıç klasörleri gibi, kötü amaçlı yazılımların bir cihazla başlamak üzere kaydedil olduğu konumları denetler. *Hızlı erişim seçeneğini öneririz.* <br/>- **Fullscan** bir cihazla ilgili tüm dosya ve klasörleri denetler <br/>- **Devre dışı** bırakıldı ise zamanlanmış taramalar olmaz. Kullanıcılar kendi cihazlarında taramaları yine çalıştırabilirsiniz. (Genelde zamanlanmış taramalarınızı devre dışı bırakmanızı önerilmez.) <br/><br/> [Tarama türleri hakkında daha fazla bilgi.](../defender-endpoint/schedule-antivirus-scans.md) |
| **Zamanlanmış taramayı çalıştırmak için haftanın günü** | Düzenli, haftalık virüsten koruma taramalarını çalıştırmak için bir gün seçin. |
| **Zamanlanmış taramayı çalıştırmak için günün saati** | Çalıştırmak için düzenli aralıklarla zamanlanmış virüsten koruma taramalarınızı çalıştırmak için bir zaman seçin. |
| **Düşük performans kullanma** | Bu ayar varsayılan olarak kapalıdır. *Bu ayarın kapalı durumda tutmalarını öneririz.* Bununla birlikte, zamanlanmış taramalarda kullanılan cihaz belleğini ve kaynakları sınırlamak için bu ayarı açabilirsiniz. <br/><br/>**ÖNEMLİ** Düşük performans **kullan'a** ayarlarsanız, aşağıdaki ayarları Yapılandırarak Performans Microsoft Defender Virüsten Koruma: <br/>- Arşiv dosyaları taranmadı ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- Taramalara düşük CPU önceliği atanır ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Tam virüsten koruma taraması atlandı ise herhangi bir yakalama taraması çalıştırmayacak ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Hızlı bir virüsten koruma taraması atlandı ise herhangi bir yakalama taraması çalıştırmayacak ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Virüsten koruma taraması sırasında ortalama CPU yük faktörü sayısını %50'den %20'ye indiren ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Kullanıcı deneyimi**   |  |
| **Kullanıcıların Windows Güvenliği izin verme** | Kullanıcıların Windows Güvenliği'i kendi cihazlarında açmalarını sağlamak için bu ayarı açın. Kullanıcılar, İş için Microsoft Defender'da (önizleme) yapılandırılan ayarları geçersiz kılabilecektir, ancak gerekirse hızlı tarama çalıştırabilecek veya algılanan tehditlere göz atabilecektir. |
| **Virüsten koruma dışlamaları** | Dışlamalar, taramalar tarafından atlanan süreçler, dosyalar veya Microsoft Defender Virüsten Koruma olur. *Genelde dışlamalar tanımlamanız gerekmer.* Microsoft Defender Virüsten Koruma işletim sistemi davranışları ve tipik yönetim dosyalarını temel alan birçok otomatik dışlama vardır.<br/><br/>[Dışlamalar hakkında daha fazla bilgi](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **İşlem dışlamaları** | İşlem dışlamaları, belirli işlemler tarafından açılan dosyaların başka bir Microsoft Defender Virüsten Koruma. <br/><br/>[İşlem dışlamaları hakkında daha fazla bilgi](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Dosya uzantısı dışlamaları** | Dosya uzantısı dışlamaları, belirli uzantılara sahip dosyaların başka uzantılar tarafından taran Microsoft Defender Virüsten Koruma.<br/><br/>[Dosya uzantısı dışlamaları hakkında daha fazla bilgi](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Dosya ve klasör dışlamaları** | Dosya ve klasör dışlamaları, belirli klasörlerdeki dosyaların başka klasörler tarafından taran Microsoft Defender Virüsten Koruma. <br/><br/>[Dosya ve klasör dışlamaları hakkında daha fazla bilgi](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>İş için Defender'daki diğer önceden yapılandırılmış ayarlar

Aşağıdaki güvenlik ayarları Defender İş (önizleme) içinde önceden yapılandırılmıştır:

- Çıkarılabilir sürücüleri tarama açık ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))
- Günlük hızlı taramalarda önceden ayarlanmış bir zaman yok ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))
- Virüsten koruma taraması çalıştırmadan önce güvenlik zekası güncelleştirmeleri denetlenir ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))
- Güvenlik zekası denetimleri her dört saatte bir gerçekleşir ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>İş için Defender varsayılan ayarları ve Microsoft Endpoint Manager

Aşağıdaki tabloda, İş için Defender (önizleme) için önceden yapılandırılmış ayarlar ve bu ayarların Microsoft Endpoint Manager'de gördüğünüze nasıl karşılık Microsoft Intune. Defender Kurumsal'da (önizleme [)](mdb-simplified-configuration.md) basitleştirilmiş yapılandırma işlemini kullanıyorsanız, bu ayarları düzenlemeniz gerekmektedir.
<br/><br/>

| Ayar  | Açıklama  |
|---------|---------|
| [Bulut koruması](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Bazen buluta teslim edilen koruma veya Microsoft Gelişmiş Koruma Hizmeti (HARITALAR) olarak da adlandırılan bulut koruması, bazen tek bir cihaz etkilenmeden önce Microsoft Defender Virüsten Koruma ve Microsoft bulutuyla birlikte çalışır. Varsayılan olarak [, AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) açıktır. <br/><br/>[Bulut koruması hakkında daha fazla bilgi edinin](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Gelen ve giden dosyaları izleme](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Gelen ve giden dosyaları izlemek için [, RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) tüm dosyaları izlemek için ayarlanmıştır.         |
| [Ağ dosyalarını tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Varsayılan olarak [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) etkinleştirilmez ve ağ dosyaları taranmaz. |
| [E-posta iletilerini tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Varsayılan olarak [, AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) etkin değildir ve e-posta iletileri taranmaz. |
| [Karantinaya alınmış kötü amaçlı yazılımı tutmak için gün sayısı (0-90)](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Varsayılan olarak, [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) bu ayar sıfır (0) gün olarak ayarlanır. Artifacts karantinada olan hiçbir şey otomatik olarak kaldırılmasız.  |
| [Örnek gönder izni](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Varsayılan olarak, [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) güvenli örnekleri otomatik olarak göndermek için et'tir. Güvenli örneklere örnek olarak `.bat`, `.scr`, `.dll``.exe` ve kişisel bilgileri (PII) içermeen dosyalar örnek olarak verilmiştir. Bir dosya PII içeriyorsa, kullanıcıya örnek gönderimin devam  olmasına izin verme isteği alır.<br/><br/>[Bulut koruması ve örnek gönderim hakkında daha fazla bilgi](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Çıkarılabilir sürücüleri tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Varsayılan olarak [, AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) , USB flash sürücüler gibi çıkarılabilir sürücüleri cihazlarda taramak için yapılandırılır.<br/><br/>[Kötü amaçlı yazılımdan koruma ilkesi ayarları hakkında daha fazla bilgi](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Günlük hızlı tarama zamanı çalıştırma](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Varsayılan olarak, [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) 02:00 olarak ayarlanır.<br/><br/>[Tarama ayarları hakkında daha fazla bilgi edinebilirsiniz](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Taramayı çalıştırmadan önce imza güncelleştirmelerini denetleme](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Varsayılan olarak, virüsten koruma/kötü amaçlı yazılım önleme taramalarını çalıştırmadan önce güvenlik zekası güncelleştirmelerini denetlemesi için [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) yapılandırılmıştır.<br/><br/>[Tarama ayarları ve Güvenlik zekası güncelleştirmeleri](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [hakkında daha fazla bilgi alın](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Güvenlik zekası güncelleştirmelerini denetleme sıklıkları (0-24 saat)](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Varsayılan olarak, [SignatureUpdateInterval güvenlik](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) zekası güncelleştirmelerini her dört saatte bir kontrol etmek üzere yapılandırılır.<br/><br/>[Tarama ayarları ve Güvenlik zekası güncelleştirmeleri](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [hakkında daha fazla bilgi alın](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender portalını ziyaret edin](mdb-get-started.md)

- [İş için Microsoft Defender'da (önizleme) güvenlik duvarı ayarlarını yönetme](mdb-custom-rules-firewall.md)

- [İlke CSP - Defender](/windows/client-management/mdm/policy-csp-defender)
