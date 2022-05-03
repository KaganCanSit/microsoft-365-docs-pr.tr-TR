---
title: İş için Microsoft Defender'da yeni nesil koruma yapılandırma ayarlarını anlama
description: küçük ve orta ölçekli işletmeler için uç nokta güvenliği olan İş için Defender'daki virüsten koruma ve yeni nesil koruma ayarlarını anlayın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 34cbd422cafe5c171f47e8e6470c4b12f9e1700d
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174458"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da yeni nesil yapılandırma ayarlarını anlama

İş için Defender'daki yeni nesil koruma, güçlü virüsten koruma ve kötü amaçlı yazılımdan koruma içerir. Varsayılan ilkeleriniz, üretkenliği engellemeden cihazlarınızı ve kullanıcılarınızı korumak için tasarlanmıştır; ancak, ilkelerinizi iş gereksinimlerinize uyacak şekilde de özelleştirebilirsiniz. Microsoft Intune kullanıyorsanız güvenlik ilkelerinizi yönetmek için Microsoft Endpoint Manager yönetim merkezini kullanabilirsiniz.

**Bu makalede şunlar açıklanmaktadır**:

- [Yeni nesil koruma ayarları ve seçenekleri](#next-generation-protection-settings-and-options)
- [İş için Defender'da önceden yapılandırılmış diğer ayarlar](#other-preconfigured-settings-in-defender-for-business) 
- [İş için Defender varsayılan ayarları ve Microsoft Intune](#defender-for-business-default-settings-and-microsoft-intune)

## <a name="next-generation-protection-settings-and-options"></a>Yeni nesil koruma ayarları ve seçenekleri

Aşağıdaki tabloda ayarlarınız ve seçenekleriniz listelenmiştir:

| Ayar | Açıklama |
|:---|:---|
| **Gerçek zamanlı koruma**  |  |
| **Gerçek zamanlı korumayı açma** | Varsayılan olarak etkin olan gerçek zamanlı koruma, cihazlarda kötü amaçlı yazılımları bulur ve çalışmasını durdurur. *Gerçek zamanlı korumayı açık tutmanızı öneririz.*<br/><br/>Gerçek zamanlı koruma açık olduğunda aşağıdaki ayarları yapılandırılır:<br/>- Davranış izleme açık ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- İndirilen tüm dosyalar ve ekler taranır ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Microsoft tarayıcılarında kullanılan betikler taranır ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **İlk görüşte engelle** | Varsayılan olarak etkindir, ilk bakışta engelle özelliği algılamadan sonra saniyeler içinde kötü amaçlı yazılımları engeller, analiz için örnek dosyaları göndermeye izin verilen süreyi (saniye olarak) artırır ve algılama düzeyinizi Yüksek olarak ayarlar. *İlk görüşte bloğu açık tutmanızı öneririz.*<br/><br/>İlk bakışta engelle özelliği açıldığında, Microsoft Defender Virüsten Koruma için aşağıdaki ayarları yapılandırılır: <br/>- Şüpheli dosyaların engellenmesi ve taranma düzeyi Yüksek engelleme düzeyine ayarlanır ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>- Bir dosyanın engellenip işaretlenmesi için saniye sayısı 50 saniye olarak ayarlanır ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**ÖNEMLİ**: İlk bakışta blok kapalıysa, Microsoft Defender Virüsten Koruma etkiler `CloudBlockLevel` `CloudExtendedTimeout`.  |
| **Ağ korumasını açın** | Ağ koruması açık olduğunda kimlik avı dolandırıcılığına, kötüye kullanım barındırma sitelerine ve İnternet'te kötü amaçlı içeriğe karşı korunmaya yardımcı olur. Ayrıca kullanıcıların ağ korumasını kapatmasını engeller.<br/><br/>Ağ koruması aşağıdaki modlardan birine ayarlanabilir:<br/>- Kullanıcıların güvenli olmayan siteleri ziyaret etmesini engelleyen **blok modu** (bu ayar varsayılan ayardır). *Ağ korumasını Engelle moduna ayarlamanızı öneririz.*<br/>- Kullanıcıların güvenli olmayabilecek siteleri ziyaret etmesine ve bu tür sitelerden ağ etkinliğini izlemesine olanak tanıyan **denetim modu** <br/>- **Devre dışı modu**, kullanıcıların güvenli olmayabilecek siteleri ziyaret etmelerini engelleyen veya ağ etkinliğini bu tür sitelerden/sitelerden izleyen devre dışı modu |
| **Düzeltme**  |  |
| **İstenmeyebilecek uygulamalarda (PUA) gerçekleştirme eylemi** | PUA, güvenlik özelliklerinden kaçınmaya çalışan diğer, imzalanmamış yazılımları ve kaçış yazılımlarını yüklemeyi teklif eden reklam yazılımları, paketleme yazılımları içerebilir. PUA mutlaka bir virüs, kötü amaçlı yazılım veya başka tür tehditler olmasa da, PUA cihaz performansını etkileyebilir.<br/><br/>PUA koruması, PUA olarak algılanan öğeleri engeller. PUA korumasını aşağıdaki ayarlardan birine ayarlayabilirsiniz: <br/>- **Etkin** (bu ayar varsayılan ayardır), cihazlarda PUA olarak algılanan öğeleri engeller. *PUA korumasını etkin tutmanızı öneririz.*<br/>- PUA olarak algılanan öğeler üzerinde hiçbir işlem gerçekleştirmeyen **denetim modu** <br/>- **Devre dışı**, PUA olabilecek öğeleri algılamaz veya üzerinde işlem yapmaz |
| **Tarama**   |  |
| **Zamanlanmış tarama türü** | Cihazlarınızda haftalık bir virüsten koruma taraması çalıştırmayı göz önünde bulundurun. Aşağıdaki tarama türü seçenekleri arasından seçim yapabilirsiniz: <br/>- **Quickscan** , kayıt defteri anahtarları ve başlangıç klasörleri gibi kötü amaçlı yazılımların bir cihazla başlamak üzere kaydedilebileceği konumları denetler. *Hızlı tarama seçeneğini kullanmanızı öneririz.* <br/>- **Fullscan** , bir cihazdaki tüm dosya ve klasörleri denetler <br/>- **Devre dışı,** zamanlanmış tarama yapılmayacağı anlamına gelir. Kullanıcılar yine de kendi cihazlarında tarama çalıştırabilir. (Genel olarak, zamanlanmış taramalarınızı devre dışı bırakmanızı önermeyiz.) <br/><br/> [Tarama türleri hakkında daha fazla bilgi edinin](../defender-endpoint/schedule-antivirus-scans.md). |
| **Zamanlanmış tarama çalıştırmak için haftanın günü** | Normal, haftalık virüsten koruma taramalarınızın çalıştırılacak bir gün seçin. |
| **Zamanlanmış taramanın çalıştırıldığı günün saati** | Düzenli olarak zamanlanmış virüsten koruma taramalarınızı çalıştırmak için bir zaman seçin. |
| **Düşük performans kullanma** | Bu ayar varsayılan olarak kapalıdır. *Bu ayarı kapalı tutmanızı öneririz.* Ancak, zamanlanmış taramalar sırasında kullanılan cihaz belleğini ve kaynakları sınırlamak için bu ayarı açabilirsiniz. <br/><br/>**ÖNEMLİ** **Düşük performans kullan'ı** açarsanız, Microsoft Defender Virüsten Koruma için aşağıdaki ayarları yapılandırılır: <br/>- Arşiv dosyaları taranmıyor ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- Taramalara düşük CPU önceliği atanır ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Tam virüsten koruma taraması kaçırılırsa, hiçbir yakalama taraması çalışmaz ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Hızlı bir virüsten koruma taraması kaçırılırsa, hiçbir yakalama taraması çalışmaz ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Virüsten koruma taraması sırasında ortalama CPU yük faktörünü %50'den %20'ye düşürür ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Kullanıcı deneyimi**   |  |
| **Kullanıcıların Windows Güvenliği uygulamasına erişmesine izin ver** | Kullanıcıların cihazlarında Windows Güvenliği uygulamasını açmasını sağlamak için bu ayarı açın. Kullanıcılar İş için Microsoft Defender'da yapılandırdığınız ayarları geçersiz kılamaz, ancak gerekirse hızlı bir tarama çalıştırabilir veya algılanan tehditleri görüntüleyebilir. |
| **Virüsten koruma dışlamaları** | Dışlamalar, Microsoft Defender Virüsten Koruma taramaları tarafından atlanan işlemler, dosyalar veya klasörlerdir. *Genel olarak, dışlamaları tanımlamanız gerekmez.* Microsoft Defender Virüsten Koruma, bilinen işletim sistemi davranışlarına ve tipik yönetim dosyalarına dayalı birçok otomatik dışlama içerir.<br/><br/>[Dışlamalar hakkında daha fazla bilgi edinin](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **İşlem dışlamaları** | İşlem dışlamaları, belirli işlemler tarafından açılan dosyaların Microsoft Defender Virüsten Koruma tarafından taranmasını önler. <br/><br/>[İşlem dışlamaları hakkında daha fazla bilgi edinin](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Dosya uzantısı dışlamaları** | Dosya uzantısı dışlamaları, belirli uzantılara sahip dosyaların Microsoft Defender Virüsten Koruma tarafından taranmasını engeller.<br/><br/>[Dosya uzantısı dışlamaları hakkında daha fazla bilgi edinin](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Dosya ve klasör dışlamaları** | Dosya ve klasör dışlamaları, belirli klasörlerdeki dosyaların Microsoft Defender Virüsten Koruma tarafından taranmasını engeller. <br/><br/>[Dosya ve klasör dışlamaları hakkında daha fazla bilgi edinin](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>İş için Defender'da önceden yapılandırılmış diğer ayarlar

İş için Defender'da aşağıdaki güvenlik ayarları önceden yapılandırılmış:

- Çıkarılabilir sürücülerin taranması açık ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))
- Günlük hızlı taramaların önceden ayarlanmış zamanı yoktur ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))
- Güvenlik bilgileri güncelleştirmeleri virüsten koruma taraması çalışmadan önce [denetleniyor (CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))
- Güvenlik bilgileri denetimleri dört saatte bir gerçekleşir ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-intune"></a>İş için Defender varsayılan ayarları ve Microsoft Intune

Aşağıdaki tabloda İş için Defender için önceden yapılandırılmış ayarlar ve bu ayarların Intune 'de görebileceğiniz ayarlara nasıl karşılık geldiğini (Microsoft Endpoint Manager yönetim merkezinde yönetilir) açıklar. [İş için Defender'da basitleştirilmiş yapılandırma işlemini](mdb-simplified-configuration.md) kullanıyorsanız, bu ayarları düzenlemeniz gerekmez.

| Ayar  | Açıklama  |
|---------|---------|
| [Bulut koruması](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Bulut koruması bazen bulut tabanlı koruma veya Microsoft Gelişmiş Koruma Hizmeti (MAPS) olarak da adlandırılır. Bulut koruması, bazen tek bir cihaz etkilenmeden önce bile yeni tehditleri belirlemek için Microsoft Defender Virüsten Koruma ve Microsoft bulutuyla birlikte çalışır. Varsayılan olarak [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) açıktır. <br/><br/>[Bulut koruması hakkında daha fazla bilgi edinin](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Gelen ve giden dosyalar için izleme](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Gelen ve giden dosyaları izlemek için [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) tüm dosyaları izleyecek şekilde ayarlanır.         |
| [Ağ dosyalarını tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Varsayılan olarak [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) etkin değildir ve ağ dosyaları taranmaz. |
| [E-posta iletilerini tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Varsayılan olarak [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) etkin değildir ve e-posta iletileri taranmaz. |
| [Karantinaya alınan kötü amaçlı yazılımların tutulacak gün sayısı (0-90)](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Varsayılan olarak, [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) bu ayar sıfır (0) gün olarak ayarlanır. Karantinadakilerin otomatik olarak kaldırılmadığını Artifacts.  |
| [Örnek onayı gönderme](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Varsayılan olarak [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) , güvenli örnekleri otomatik olarak gönderecek şekilde ayarlanır. Güvenli örneklere örnek olarak, , , ve `.exe` kişisel bilgiler (PII) içermeyen dosyalar verilebilir`.bat`. `.dll``.scr` Bir dosya PII içeriyorsa, kullanıcı örnek gönderimin devam etmesine izin vermek için bir istek alır.<br/><br/>[Bulut koruması ve örnek gönderim hakkında daha fazla bilgi edinin](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Çıkarılabilir sürücüleri tarama](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Varsayılan olarak [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) , cihazlarda USB başparmak sürücüleri gibi çıkarılabilir sürücüleri tarayacak şekilde yapılandırılır.<br/><br/>[Kötü amaçlı yazılımdan koruma ilkesi ayarları hakkında daha fazla bilgi edinin](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Günlük hızlı tarama süresini çalıştırma](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Varsayılan olarak [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) 02:00 olarak ayarlanır.<br/><br/>[Tarama ayarları hakkında daha fazla bilgi edinin](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Taramayı çalıştırmadan önce imza güncelleştirmelerini denetleme](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Varsayılan olarak [CheckForSignaturesBeforeRunningScan, virüsten](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) koruma/kötü amaçlı yazılımdan koruma taramaları çalıştırmadan önce güvenlik bilgileri güncelleştirmelerini denetlemek üzere yapılandırılır.<br/><br/>Tarama ayarları ve [Güvenlik bilgileri güncelleştirmeleri](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates) [hakkında daha fazla bilgi edinin](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Güvenlik bilgileri güncelleştirmelerini denetleme sıklıkları (0-24 saat)](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Varsayılan olarak [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) , güvenlik bilgileri güncelleştirmelerini dört saatte bir denetleyecek şekilde yapılandırılır.<br/><br/>Tarama ayarları ve [Güvenlik bilgileri güncelleştirmeleri](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates) [hakkında daha fazla bilgi edinin](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings). |


## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender portalını ziyaret edin](mdb-get-started.md)
- [İş için Microsoft Defender'de güvenlik duvarı ayarlarını yönetme](mdb-custom-rules-firewall.md)
- [İlke CSP - Defender](/windows/client-management/mdm/policy-csp-defender)
