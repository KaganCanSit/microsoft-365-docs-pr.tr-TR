---
title: Gelişmiş avla fidye yazılımı bulun
description: Fidye yazılımlarının etkilendiği cihazları bulmak için gelişmiş av kullanın.
keywords: gelişmiş av, fidye yazılımı, tehdit avı, siber tehdit araması, arama, sorgu, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-ransomware
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e90661932880ee146b8b1b81f8412e97d674749d
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755754"
---
# <a name="hunt-for-ransomware"></a>Fidye yazılımı avlayın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Fidye yazılımları, tek tek bilgisayar kullanıcılarını endüstrileri ve kamu kuruluşlarını ciddi etkileyen kurumsal bir tehditle karşı karşıya olan basit ürünlerden oluşan kötü amaçlı yazılımdan hızlı bir şekilde gelişti. Microsoft 365 Defender[,](microsoft-365-defender.md) fidye yazılımlarını ve ilişkili izinsiz giriş etkinliklerini algılayan ve engellayan pek çok özellik sağlarken, güvenlik işaretleri için proaktif denetimler gerçekleştirerek ağlarınızı korumanıza yardımcı olabilir.

> [İnsan tarafından işletilen fidye yazılımları hakkında bilgi](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

[E-postada](advanced-hunting-overview.md) gelişmiş Microsoft 365 Defender, fidye yazılımı etkinliğiyle ilişkilendirilmiş tek tek yapıları buen sorgular oluşturabilirsiniz. Ayrıca, etkinlik işaretlerine bakabilen ve acil dikkat gerektiren cihazları bulmak için bu işaretleri işaretlerini görene kadar göz atabilen daha gelişmiş sorgular çalıştırabilirsiniz.

## <a name="signs-of-ransomware-activity"></a>Fidye yazılımı etkinliğinin işaretleri
Microsoft güvenlik araştırmacısı, karmaşık izinsiz girişler tarafından başlatılan birçok fidye yazılımı kampanyalarında yaygın olarak kullanılan ancak bazı dikkatsiz yapıları gözlemledi. Bu işaretler çoğunlukla şifrelemeye hazırlanmak, algılamayı önlemek ve kanıt kanıtlarını temizlemek için sistem araçlarının kullanımını içerir.

| Fidye yazılımı etkinliği | Ortak araçlar | Amaç |
|--|--|--|
| İşlemleri durdurma | _taskkill.exe_, _net durak_ | Şifreleme için hedeflenmiş dosyaların çeşitli uygulamalar tarafından kilitlenmey olduğundan emin olun. |
| Hizmetleri kapatma | _sc.exe_ | - Şifreleme için hedeflenmiş dosyaların çeşitli uygulamalar tarafından kilitlenmey olduğundan emin olun.<br>- Güvenlik yazılımının şifrelemeyi ve diğer fidye yazılımı etkinliklerini kesintiye sevk etmelerini önle.<br>- Yedek yazılımın kurtarılabilir kopyalar oluşturmasını durdurun.  |
| Günlükleri ve dosyaları silme | _cipher.exe_, _wevtutil_, _fsutil.exe_ | Kanıt kanıtlarını kaldırın. |
| Gölge kopyaları silme  | _vsadmin.exe_, _wmic.exe_ | Şifreli dosyaları kurtarmak için  kullanılan sürücü gölge kopyalarını kaldırın. |
| Yedekleri silme ve durdurma | _wbadmin.exe_ | Şifreleme sonrasında kurtarmayı önleyen mevcut yedekleri silin ve zamanlanmış yedekleme görevlerini durdurun. |
| Önyükleme ayarlarını değiştir | _bcdedit.exe_ | Şifreleme işleminin neden olduğu başlatma hatalarının ardından uyarıları ve otomatik onarımları kapatın. |
| Kurtarma araçlarını kapatma | _schtasks.exe_, _regedit.exe_, | Sistem Geri Yükleme ve diğer sistem kurtarma seçeneklerini kapatın. |

## <a name="check-for-individual-signs-of-ransomware-activity"></a>Fidye yazılımı etkinliğinin tek tek işaretlerini denetleme
Önceki bölümde açıklanan etkinlikler de dahil olmak üzere fidye yazılımı davranışını oluşturan birçok etkinlik gerçek olabilir. Fidye yazılımlarını bulmak için aşağıdaki sorguları kullanırken, aynı cihazların çeşitli olası fidye yazılımı etkinliklerini sergip sergileye olmadığını kontrol etmek için birden fazla sorgu çalıştırın.

### <a name="stopping-multiple-processes-using-_taskkillexe_"></a>Birden çok işlemi tek tek _taskkill.exe_
Bu sorgu,taskkill.exeyardımcı programını kullanarak en az 10 ayrı _işlemi durdurma denemelerini_ denetler. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RS2vCUBCFz7rgfwiuIkit3eumVSgtpYvuS9SLDTY2eLUvxN_eb8YHKlFkyNzJzDkn505aailRX7mmGlFlmhNBhUrOSGeuT3L0s6QqNaMagolEcMyCbApjx2e8TYhcH8Q1mB-emq50z_lF39gvBzo9-gEF-6Yhlyh9653ejCfRK6zCsaZfuJOu-x2jkqqN-0Yls-8-gp6dZ52OVuT6Sad1plulyN0KIkMt15_zt7zHDe8OBwv3btoJToa7Tnp0T8Ou9WzfT761gPOm3_FQ16Zxp2qcCdg33_rlyokG-iXv7_4BRNMnhkortmvTW6rqnZ7bgP2Vtm70D3d9wcFaAgAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using taskkill.exe
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10
```
  
### <a name="stopping-processes-using-_net-stop_"></a>Net durağı kullanarak _işlemleri durdurma_
Bu sorgu, net dur komutunu kullanarak en az 10 ayrı işlemi durdurma _denemelerini_ denetler. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RQUvDUBCE5yz0P4ScUijWereXVkGQIti7aA1pqakhL7VVxN_ebzc1NBChPLJv2Z2ZN5sdaqhId1ppozeyF1WcVLkK7kCl0gcx-F2QFSrJFmACJ3XMlmgKGfmGWnXC6OlCU2qfIIz12OLfUk_h2FuG_IG505JayRdpDit3bIW33B2M3WeGSqIRrvudTJvpnWzmPKvc6JcYHx1eEvd8savV07e9TchzTt198AlNZ0kluNLfjHHjIPAvak4J_tvx9XtPR6ypbn1icxShvGgqyVkO-hrAm7VUrRcaTWOs6T_7hs7XjfSqL-Lpvu5BDLxjqKRjI9a9Juvew__T2x5HutIB3T1qt4QCAAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using net stop
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10
```
### <a name="deletion-of-data-on-multiple-drives-using-_cipherexe_"></a>Birden çok sürücüde birden çok sürücüde verilerin _silinmesinicipher.exe_
Bu sorgu,cipher.exekullanarak birden çok sürücüde _veri silmecipher.exe_. Bu etkinlik normalde fidye yazılımı tarafından şifreleme sonrasında verilerin kurtar 12'sini önlemek için yapılır. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI1SXUvDQBCcZ8H_cOQpgWLoD7AvVUEo4oPvElO1pblUcmn9QPztzk6TEuEsIdzdZndndm73cuRwWGDLb0PrhWfDs8Qab1jhmX8X3D-4HJbcK66W0Rqv8hT8K4RsiPW0PHbMasVQdbiGf3vaAec4wxWtPT0lz3vhSsUCrpVVE33I_Cb6vdNhTA9EeeVaVc8KDjOugmq2SDFlrSyKvCHS1NwJZ55L_HBPondNGDGWXP2JdyMnv927UnXHWwf6l4MunupXTOPfXszVT8_smriFOCxrRU-QclOQDLgCNRwQ1u8vZc8H2o1xp-7a7U1NefSko6pnmKjakNVi4chpiA39j-rGeF6HJ3xyH76NW2ZMFLGsNDJ9i05pZSPmVdDfq-jncfqtOuU5zSuQz6Zq92w7Hfbm-9cUm-d_vZ9J9S81O2KIfAMAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for cipher.exe deleting data from multiple drives
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine),
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1
```

### <a name="clearing-of-forensic-evidence-from-event-logs-using-_wevtutil_"></a>_Wevtutil_ kullanarak olay günlüklerinden kanıt temizleme
Bu sorgu, _wevtutil_ kullanarak olay günlüklerinden en az 10 günlük girdisi temizleme denemelerini denetler. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWRTU_CQBCG37OJ_2HDqSQkwMGjXgoHEg4cUI-m2hUaqGu6BaPxx_vsEFCTxmA225nOvB_tzFBDOc0VOBuyZ2JD3CnKEwMVpzfyPbVWlba8t9Sdnsi9CsPXdLfWf7Wq4xm0QuVSF5oYv4LhtQAfLIucKXWvF5gH5Ke5rak1prKEVRu2xalG3emGW6AdlGmsUv1O5m-fnLzmFHiV_G9FTKg1lUjs6Z5vucPvljsD0TOXhP6_Vm7841dFZnPAN2A_DDu36eSnCSbNnc3B6Zpb4nasZGf59zWA963orZdcEiKelBNvQ_fBNny-utOj3nn-3OUMxMA6CZV1bCt1r8i6d_TXFNKWxxrpC48hm8miAgAA&runQuery=true&timeRangeId=week)

```kusto
// Look for use of wevtutil to clear multiple logs
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10
```

### <a name="turning-off-services-using-_scexe_"></a>sc.exekullanarak _hizmetlerisc.exe_
Bu sorgu, var olan en az 10 hizmeti _sc.exe._ [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAKWST2vCQBDF31nodwg5RZCqhx7bi3ooeCjovaQxraIxxfU_fvj-ZoiiEIqlhM3Ozrz3ZnZm22or0lAl3xzrk33FHpTpUbn2rEgTzfCk-tACa6kvR-Qgt5wzrKAHNdTHOnveiJZVLGiAP4e5rpAnFHaauoZlGMMqHLsmT6FvfC-slFylEnWpoVnLvM3Twy74UnJNuJdVa6gpnsAe-81iVzbE3_kZiCV9mlHZf3Sue5pzii-3C9pU3BWYo_NGKPdvGJZh4x2N9Owzyi6e5K5qmmrVKg_9dNY11hzvu0_8fu0ItQP_6zfxCqLlEUMlNVO36BNW_ax_74K9l646-gFts39I1AIAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for sc.exe disabling services
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10
```

### <a name="turning-off-system-restore"></a>Sistem Geri Yükleme'yi Kapatma
Bu sorgu, Sistem Geri Yükleme'yi durdurma denemelerini ve sistemin fidye yazılımı tarafından şifrelenmiş verileri kurtarmak için kullanılmaktadır ve geri yükleme noktaları oluşturmasını engellemeye yönelik girişimler tanımlar. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAK2S3UrDQBCFz7XgO6y9id4o6HWvrIVCkaJPENOYFNumZGO1ID673w4xJA1isbJMZnZ-zpzM7EiptlooQc9UqjDLc-7wp1qrwj7Via44MzK35FTotTI5PXMr0aVe8cy15NzoGo-zqg_0m3KQSsRpQtbC6uMGpdt3jHeJfU_GymqG-uQb9XpcEn1HIuvmGpZT0Aq99Dim4G3ousNO8K04sSE6EEN22kL6jvzO-LaDNW2QzqxLmGBsPo9vUMt_oA8Na3DQv3vwcmPiifpmds48jkhut8T2FLikxm_T4bI_m_6uQt-wrXO28lPPSBcdziOqPFlP9RYy47tDKtuZM07hVtSvaJ_HYRPL63-NyMgtmtWv5684jy2WDx2O0ZEM562ZBLQvURxur6gDAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
//Pivoting for rundll32  
| where InitiatingProcessFileName =~ 'rundll32.exe'   
//Looking for empty command line   
and InitiatingProcessCommandLine !contains " " and InitiatingProcessCommandLine != ""  
//Looking for schtasks.exe as the created process  
and FileName in~ ('schtasks.exe')  
//Disabling system restore   
and ProcessCommandLine has 'Change' and ProcessCommandLine has 'SystemRestore' 
and ProcessCommandLine has 'disable'
```

### <a name="backup-deletion"></a>Yedekleme silme
Bu sorgu, şifreleme öncesinde _wmic.exe_ anlık görüntüleri silmek için gölge anlık görüntülerinin kullanımını tanımlar. [Sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWS2wqCQBCG_-ugd5CupTfoqgMIEV70AqFLGp5QyYLo2fsavEjxwlhWZ7-df2Z2dndyuitVxD9UrdKshrGHOxVqsZda6CVPnRJYzfR0QJVhnXRRbmSjN98VXrlFXEMfzNWkfphti50zLmSMdURfmFcCaSxqY3aMX4eqVKUn1OsV_8eLWX_rbwcVVhblBovY8bT76U-AxoedWeeWp7WzV0YDMqSQFNZavuuopnHH_Iku-lbJnLPMyxnYDTp4bZ5P9M5uNpsZIWSn7l_CuNoPSggb4z4CAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
| where FileName =~ "wmic.exe"
| where ProcessCommandLine has "shadowcopy" and ProcessCommandLine has "delete"
| project DeviceId, Timestamp, InitiatingProcessFileName, FileName,
ProcessCommandLine, InitiatingProcessIntegrityLevel, InitiatingProcessParentFileName
```

## <a name="check-for-multiple-signs-of-ransomware-activity"></a>Fidye yazılımı etkinliğinin çeşitli işaretlerini denetleme
Birkaç sorguyu ayrı olarak kullanmak yerine, etkilenen cihazları tanımlamak için fidye yazılımı etkinliğinin birden çok işaretlerini kontrol etmek için kapsamlı bir sorgu da kullanabilirsiniz. Aşağıdaki birleştirilmiş sorgu:
- Fidye yazılımı etkinliğinin hem görece daha beton hem de hafif işaretlerine bakarak
- Bu işaretlerin varlığını İşaretler
- Fidye yazılımı hedefi olma ihtimali daha yüksek olan cihazları tanımlar 

Bu birleştirilmiş sorgu, çalıştırıldıklarının birden çok işaretine sergilenen cihazların listesini döndürür. Fidye yazılımı etkinlik türlerinin sayısı da gösterilir. Bu birleştirilmiş sorguyu çalıştırmak için doğrudan gelişmiş arama sorgusu [düzenleyicisine kopyalayın](https://security.microsoft.com/advanced-hunting). 

```kusto
// Find attempts to stop processes using taskkill.exe
let taskKill = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10;
// Find attempts to stop processes using net stop
let netStop = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10;
// Look for cipher.exe deleting data from multiple drives
let cipher = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine), 
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1;
// Look for use of wevtutil to clear multiple logs
let wevtutilClear = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10;
// Look for sc.exe disabling services
let scDisable = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10;
// Main query for counting and aggregating evidence
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "vssadmin.exe" and ProcessCommandLine has_any("list shadows", "delete shadows")
or FileName =~ "fsutil.exe" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal"
or ProcessCommandLine has("bcdedit") and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures")
or ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup")
or (ProcessCommandLine has "wevtutil" and ProcessCommandLine has "cl") 
or (ProcessCommandLine has "wmic" and ProcessCommandLine has "shadowcopy delete")
or (ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled")
| extend Bcdedit = iff(ProcessCommandLine has "bcdedit" and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures"), 1, 0)
| extend ShadowCopyDelete = iff (ProcessCommandLine has "shadowcopy delete", 1, 0)
| extend VssAdminShadows = iff(ProcessCommandLine has "vssadmin" and ProcessCommandLine has_any("list shadows", "delete shadows"), 1, 0)
| extend Wbadmin = iff(ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup"), 1,0)
| extend Fsutil = iff(ProcessCommandLine has "fsutil" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal", 1, 0)
| summarize FirstActivity = min(Timestamp), ReportId = any(ReportId), Commands = make_set(ProcessCommandLine) by DeviceId, Fsutil, Wbadmin, ShadowCopyDelete, Bcdedit, VssAdminShadows, bin(Timestamp, 6h)
// Joining extra evidence
| join kind=leftouter (wevtutilClear) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (cipher) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (netStop) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (taskKill) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (scDisable) on $left.DeviceId == $right.DeviceId
| extend WevtutilUse = iff(LogClearCount > 10, 1, 0)
| extend CipherUse = iff(CipherCount > 1, 1, 0)
| extend NetStopUse = iff(netStopCount > 10, 1, 0)
| extend TaskkillUse = iff(taskKillCount > 10, 1, 0)
| extend ScDisableUse = iff(ScDisableCount > 10, 1, 0)
// Adding up all evidence
| mv-expand CommandList = NetStopList, TaskKillList, ClearedLogList, CipherList, Commands, ScDisableList
// Format results
| summarize BcdEdit = iff(make_set(Bcdedit) contains "1" , 1, 0), NetStop10PlusCommands = iff(make_set(NetStopUse) contains "1", 1, 0), Wevtutil10PlusLogsCleared = iff(make_set(WevtutilUse) contains "1", 1, 0),
CipherMultipleDrives = iff(make_set(CipherUse) contains "1", 1, 0), Fsutil = iff(make_set(Fsutil) contains "1", 1, 0), ShadowCopyDelete = iff(make_set(ShadowCopyDelete) contains "1", 1, 0),
Wbadmin = iff(make_set(Wbadmin) contains "1", 1, 0), TaskKill10PlusCommand = iff(make_set(TaskkillUse) contains "1", 1, 0), VssAdminShadow = iff(make_set(VssAdminShadows) contains "1", 1, 0), 
ScDisable = iff(make_set(ScDisableUse) contains "1", 1, 0), TotalEvidenceCount = count(CommandList), EvidenceList = make_set(Commands), StartofBehavior = min(FirstActivity) by DeviceId, bin(Timestamp, 1d)
| extend UniqueEvidenceCount = BcdEdit + NetStop10PlusCommands + Wevtutil10PlusLogsCleared + CipherMultipleDrives + Wbadmin + Fsutil + TaskKill10PlusCommand + VssAdminShadow + ScDisable + ShadowCopyDelete
| where UniqueEvidenceCount > 2
```
### <a name="understand-and-tweak-the-query-results"></a>Sorgu sonuçlarını anlama ve ayarlama
Birleştirilmiş sorgu aşağıdaki sonuçları döndürür:

- **DeviceId**— etkilenen cihazı tanımlar 
- **TimeStamp**: cihazda ilk kez fidye yazılımı etkinliği işareti gözlemlendi
- **Belirli etkinlik işaretleri;** _bcdEdit_ veya _FsUtil_ gibi birden çok sütunda gösterilen her bir işaretin sayısı
- **TotalEvidenceCount**—gözlemlenen işaret sayısı
- **UniqueEvidenceCount**— gözlemlenen işaret türlerinin sayısı

:::image type="content" source="../../media/advanced-hunting-ransomware-query.png" alt-text="Microsoft 365 Defender portalında fidye yazılımı etkinliği için birleştirilmiş bir Microsoft 365 Defender örneği" lightbox="../../media/advanced-hunting-ransomware-query.png":::

*Etkilenen cihazları ve fidye yazılımı etkinliğinin çeşitli işaretlerini gösteren sorgu sonuçları*

Varsayılan olarak, sorgu sonucunda yalnızca ikiden fazla fidye yazılımı etkinliği türü olan cihazlar liste vardır. Fidye yazılımı etkinliğinin herhangi bir işaretine sahip tüm cihazları görmek için aşağıdaki `where` işleci değiştirerek s sayısını sıfır (0) olarak ayarlayın. Daha az cihaz görmek için daha yüksek bir sayı ayarlayın. 

```kusto
| where UniqueEvidenceCount > 2
```

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)

## <a name="more-ransomware-resources"></a>Diğer fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Giderek büyüyen fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/) olan Microsoft 20 Temmuz 2021'de Sorunlar blog gönderisi
- [İnsan tarafından işletilen fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımlarına ve ekstörlere karşı hızlı bir şekilde koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (sayfa 10-19'a bakın)
- [Fidye yazılımı: Microsoft 365 Defender portalında periveive](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) ve sürekli tehdit Microsoft 365 Defender raporu

Microsoft 365:

- [Yazılım kiracınız için fidye yazılımı Microsoft 365 dağıtın](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımı saldırılarından kurtar](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Kötü amaçlı yazılım ve fidye yazılımına karşı koruma](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Bilgisayarınızı fidye yazılımlarından Windows koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Yazılım portalında fidye yazılımı](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) için tehdit Microsoft 365 Defender raporları

Microsoft Azure:

- [Fidye Yazılımı Saldırısını Azure Savunma](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı korunmak için planı yedekleme ve geri yükleme](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Yedekleme ile fidye yazılımlarından korunmaya](https://www.youtube.com/watch?v=VhLOr2_1MCg) yardımcı olun (26 dakikalık video)
- [Sistemsel kimlik güvenliğinden ödün verme](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok amaçlı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fidye Yazılımı Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Bulut Uygulamaları için Microsoft Defender:

-  [Bulut Uygulamaları için Defender'da anormal algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önlemeye ve fidye yazılımlarından korunmaya yönelik üç adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından işletilen fidye yazılımlarla mücadeleye yardımcı bir kılavuz: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (YERMİ) fidye yazılımı olayı soruşturmalarını nasıl yönetecekleri ile ilgili önemli adımlar.

- [İnsan tarafından işletilen fidye yazılımıyla mücadeleye kılavuz: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayan giderek daha iyi hale geliyor: Bölüm 4: mevcut tehditlerle gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Fidye yazılımı **bölümüne** bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırılar için saldırı zinciri çözümlemeleri içerir.

- [Fidye yazılımına yanıt— ödeme yapmak veya ödeme yapmak değil mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk 365 Fidye yazılımı saldırılarına saydamlık saldırısıyla yanıt verdi (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
