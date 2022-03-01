---
title: Komut çizgilerini yönetmek için komut Microsoft Defender Virüsten Koruma
description: Özel Microsoft Defender Virüsten Koruma komut satırı yardımcı programıyla yeni nesil korumayı taramaları ve yapılandırmaları için çalıştırın.
keywords: windows Defender Scan'ı çalıştırma, komut satırdan virüsten koruma taramasını çalıştırma, komut hattından windows defender taramasını, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: f7ae9c9d0986463b6d6368edd0dac050600e3373
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997071"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Komut satırı Microsoft Defender Virüsten Koruma ile mpcmdrun.exe ve yönetme

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Görev görevlerinde, Microsoft Defender Virüsten Koruma komut satırı aracını kullanarak **çeşitlimpcmdrun.exe.** Bu yardımcı program, görevleri otomatik hale Microsoft Defender Virüsten Koruma yarar. Yardımcı programı 'da bulabilirsiniz `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Komut isteminden çalıştırın.

> [!TIP]
> Komut isteminin yönetici düzeyinde bir sürümünü açmanız gerekir. Arama sonuçlarında Komut **İstemi'Başlat menüsü** Yönetici olarak **çalıştır'ı seçin**. Güncelleştirilmiş bir Microsoft Defender kötü amaçlı yazılımdan koruma platform sürümünü çalıştırıyorsanız, şu `MpCmdRun` konumdan çalıştırın: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Kötü amaçlı yazılımdan koruma platformu hakkında daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma ve taban çizgilerini güncelleştirme.](manage-updates-baselines-microsoft-defender-antivirus.md)

MpCmdRun yardımcı programı aşağıdaki söz dizimi kullanır:

```console
MpCmdRun.exe [command] [-options]
```

İşte bir örnek:

```console
MpCmdRun.exe -Scan -ScanType 2
```

Örneğimizde, MpCmdRun yardımcı programı cihazda tam virüsten koruma taraması başlatır.

## <a name="commands"></a>Komutlar

|Komut|Açıklama|
|---|---|
|`-?` **veya** `-h`|MpCmdRun aracı için kullanılabilir tüm seçenekleri görüntüler|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Kötü amaçlı yazılımları tarar. **ScanType değerleri**:<p>**0** Varsayılan, yapılandırmanıza göre<p>**1** Hızlı tarama<p>**2** Tam tarama<p>**3 Dosya** ve dizin özel taraması.<p>Cpu Azaltma, ilke yapılandırmaları göre çalışır|
|`-Trace [-Grouping #] [-Level #]`|Tanılama izlemeyi başlatır|
|`-GetFiles [-SupportLogLocation <path>]`|Destek bilgilerini toplar. Bkz[. 'tanılama verilerini toplama](collect-diagnostic-data.md)'|
|`-GetFilesDiagTrack`|ile aynıdır `-GetFiles`, ancak geçici DiagTrack klasörüne çıkış sağlar|
|`-RemoveDefinitions [-All]`|Yüklü Güvenlik Zekası'nın önceki bir yedek kopyasını veya özgün varsayılan kümeyi geri yükleme|
|`-RemoveDefinitions [-DynamicSignatures]`|Yalnızca dinamik olarak indirilen Security Intelligence'i kaldırır|
|`-RemoveDefinitions [-Engine]`|Önceki yüklü altyapısını geri yükleme|
|`-SignatureUpdate [-UNC \|-MMPC]`|Yeni Güvenlik zekası güncelleştirmelerini denetler|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Karantinaya alınmış öğeyi geriler veya listeler|
|`-AddDynamicSignature [-Path]`|Dinamik Güvenlik zekası yükler|
|`-ListAllDynamicSignatures`|Yüklenen dinamik Security Intelligence'i listeler|
|`-RemoveDynamicSignature [-SignatureSetID]`|Dinamik Güvenlik zekası kaldırır|
|`-CheckExclusion -path <path>`|Yol dışlanmış olup olmadığını denetler|
|`-ValidateMapsConnection`|Ağ bağlantınız, bulut hizmetiyle Microsoft Defender Virüsten Koruma doğrular. Bu komut yalnızca 1703 Windows 10 veya daha yeni sürümlerde çalışır.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Komutlar aracılığıyla komutları çalıştırmayla ilgili sık mpcmdrun.exe

Aşağıdaki tabloda MpCmdRun aracı kullanırken meydana gelebilir yaygın hatalar listeledir.

|Hata iletisi|Olası neden|
|---|---|
|**ValidateMapsConnection başarısız oldu (800106BA)** veya **0x800106BA**|Yeni Microsoft Defender Virüsten Koruma devre dışı bırakılır. Hizmeti etkinleştirin ve yeniden deneyin. Postalarınızı yeniden etkinleştirmeyle ilgili yardıma Microsoft Defender Virüsten Koruma, bkz[. Uç noktalarınıza Microsoft Defender Virüsten Koruma yeniden yükleme/etkinleştirme](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **İpucu**: Windows 10 1909 veya daha eski bir Windows Server 2019 veya daha eski bir modelde, hizmet eski adı *Windows Defender Virüsten Koruma.*|
|**0x80070667**|Komutu, `-ValidateMapsConnection` 1607 veya daha eski Windows 10 veya daha eski bir Windows Server 2016 çalıştırabilirsiniz. Komutu, 1703 veya Windows 10 veya daha yeni bir sürümü olan bir makineden ya da Windows Server 2019 veya daha yeni bir sürümden çalıştırın.|
|**MpCmdRun iç veya dış komut, işlenen program veya toplu iş dosyası olarak tanınmıyor.**|Araç, platform güncelleştirmelerinin Mart hariç `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` aylık olması `2012.4-0` gerekir veya araçtan çalıştır bağlı olabilir (platform güncelleştirmeleri burada farklılık gösterebilir)|
|**ValidateMapsConnection, HARITALAR'a bağlantı kuramadı (hr=80070005 httpcode=450)**|Komut yetersiz ayrıcalıkları kullanmaya çalışıldı. Yönetici olarak komut istemini (cmd.exe) kullanın.|
|**ValidateMapsConnection, HARITALAR'a bağlantı kuramadı (hr=80070006 httpcode=451)**|Güvenlik duvarı bağlantıyı engelliyor veya SSL incelemesi gerçekleştirıyor.|
|**ValidateMapsConnection, HARITALAR'a bağlantı kuramadı (hr=80004005 httpcode=450)**|Ad çözümleme sorunları gibi ağ ile ilgili olası sorunlar|
|**ValidateMapsConnection HARITALAR bağlantısı kuramadı (hr=0x80508015**|Güvenlik duvarı bağlantıyı engelliyor veya SSL incelemesi gerçekleştirıyor.|
|**ValidateMapsConnection, HARITALAR'a bağlantı kuramadı (hr=800722F0D)**|Güvenlik duvarı bağlantıyı engelliyor veya SSL incelemesi gerçekleştirıyor.|
|**ValidateMapsConnection HARITALAR'a bağlantı kuramadı (hr=80072EE7 httpcode=451)**|Güvenlik duvarı bağlantıyı engelliyor veya SSL incelemesi gerçekleştirıyor.|

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma yapılandırma](configure-microsoft-defender-antivirus-features.md)
- [Ağ bağlantılarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-network-connections-microsoft-defender-antivirus.md)
- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
