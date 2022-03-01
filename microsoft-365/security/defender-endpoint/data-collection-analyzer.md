---
title: Windows'da gelişmiş sorun giderme için veri Windows
description: Karmaşık sorun giderme senaryolarında veri toplamak üzere istemci çözümleyicisini kullanmayı öğrenin
keywords: bilgi toplama, mdeclientanalyzer sorunlarını giderme, gelişmiş sorun giderme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 06d201d6f3604580ad9543616c48e526f63bac83
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016535"
---
# <a name="data-collection-for-advanced-troubleshooting-on-windows"></a>Windows'da gelişmiş sorun giderme için veri Windows

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft destek uzmanlarıyla işbirliği yapmak üzere daha karmaşık senaryolarda sorun giderme için veri toplamak üzere istemci çözümleyicisini kullanabilirsiniz. Çözümleyici betiği bu amaç için diğer parametreleri destekler ve araştırılması gereken gözlemlenen belirtilere dayalı olarak belirli bir günlük kümesi toplayabilirsiniz.

'**MDEClientAnalyzer.cmd /?**' çalıştırın kullanılabilir parametrelerin listesini ve onların açıklamasını görmek için:

![Komut satırda istemci çözümleyicisi parametrelerinin görüntüsü.](images/d89a1c04cf8441e4df72005879871bd0.png)

> [!NOTE]
> Herhangi bir gelişmiş sorun giderme parametresi kullanıldığında, çözümleyici ilgili destek [ günlükleriniMpCmdRun.exe](/microsoft-365/security/defender-endpoint/command-line-arguments-microsoft-defender-antivirus) için Microsoft Defender Virüsten Koruma aratır.

**-h** - Standart [Windows ek olarak](/windows-hardware/test/wpt/wpr-command-line-options) ayrıntılı bir genel performans izlemesi toplamak için Performans Kaydedicisi'ne çağrılar.

**-l** - Hafif bir perfmon [Windows](/windows-server/remote/remote-desktop-services/rds-rdsh-performance-counters) izlemek için yerleşik Performans İzleyicisi'ne çağrılar. Zaman içinde oluşan ancak isteğe bağlı olarak yeniden üreti güç performans düşüşü sorunlarının tanılaması sırasında bu yararlı olabilir.

**-c** - Gerçek [zamanlı dosya sisteminin,](/sysinternals/downloads/procmon) kayıt defterinin ve süreç/iş parçacığı etkinliğinin gelişmiş izlenmesi için süreç izlemesine çağrılar. Bu özellikle çeşitli uygulama uyumluluk senaryolarında sorun giderirken kullanışlıdır.

**-i** - Ağ ve Windowsnetsh.exeizlemesini başlatmak için, ağ ile ilgili çeşitli sorunları giderirken yararlı olan yerleşik Güvenlik Duvarı komutunu arar.[](/windows/win32/winsock/netsh-exe)

**-b** - '-c' ile aynıdır, ancak işlem izleme izlemesi bir sonraki başlatma sırasında başlatılır ve yalnızca -b yeniden kullanılırken durdurulur.

**-a** - Virüsten koruma [Windows](/windows-hardware/test/wpt/wpr-command-line-options) (MsMpEng.exe) ile ilgili yüksek CPU sorunlarını çözümlemeye özgü ayrıntılı bir performans izlemesi toplamak için Performans Kaydedicisi'ne MsMpEng.exe.

**-v** - En ayrıntılı [ -MpCmdRun.exe bayraklarıyla](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus) birlikte virüsten koruma yazılımı veya komut satırı bağımsız değişkenlerini kullanır.

**-t** - Uç Nokta DLP ile ilgili tüm istemci tarafı bileşenlerinin ayrıntılı izlemesini başlatır. Bu, dosyalarda [DLP eylemlerinin](/microsoft-365/compliance/endpoint-dlp-learn-about#endpoint-activities-you-can-monitor-and-take-action-on) beklendiği gibi olmadığının senaryoları için kullanışlıdır.

**-q** - Uç nokta DLPDiagnose.ps1 DLP için temel yapılandırmayı ve gereksinimleri doğrulayan çözümleyici 'Araçlar' dizininden gelen arama betiği kullanılır.

**-d** - **MsSenseS**.exe (Windows Server 2016 eski işletim sistemi) ve ilgili işlemlerin bellek dökümü toplar.

- \* Bu bayrak, yukarıda belirtilen bayraklarla birlikte kullanılabilir.
- \*\*[PPL korumalı işlemlerin](/windows-hardware/drivers/install/early-launch-antimalware) bellek dökümü yakalaması MsSense.exe MsMpEng.exe şu anda çözümleyici tarafından desteklenmiyor.

**-z** - CrashOnCtrlScroll aracılığıyla tam makine bellek dökümü koleksiyonu için hazırlamak üzere makinede [kayıt defteri anahtarlarını yapılandırr](/windows-hardware/drivers/debugger/forcing-a-system-crash-from-the-keyboard). Bu, bilgisayarı dondurma sorunlarını çözümlemek için yararlı olur.

\* En sağdaki CTRL tuşunu basılı tutun ve SCROLL LOCK tuşuna iki kez basın.

**-k** - [Sistemin kilitlenmeye ve bir](/sysinternals/downloads/notmyfault) makine bellek dökümü oluşturmasını zorlamak için NotMyFault aracını kullanır. Bu, çeşitli işletim sistemi kararlılığı sorunlarını çözümlemek için yararlı olur.

Çözümleyici ve yukarıdaki tüm senaryo bayrakları, çözümleyici araç kümesi içinde de birlikte gelen 'RemoteMDEClientAnalyzer.cmd' çalıştırarak uzaktan başlatabilirsiniz:

![Çözümleyici bilgilerine sahip komut çizgisinin resmi.](images/57cab9d82d08f672a92bf9e748ac9572.png)

> [!NOTE]
>
> - RemoteMDEClientAnalyzer.cmd kullanırken, yapılandırılan dosya paylaşımından aracı indirmek ve sonra yerel olarak çalıştırmak için psexec dosyasına PsExec.exe.
    CMD betiği, SİSTEM bağlamı içinde uzaktan çalıştır olmadığını belirtmek için '-r' bayrağını kullanır ve kullanıcıya sorulmayacaktır.
> - Aynı bayrak, kullanıcıdan veri toplama için dakika sayısını belirtme isteğinde kaçınmak için MDEClientAnalyzer.cmd ile de kullanılabilir. Örneğin:
>
>    **MDEClientAnalyzer.cmd -r -i -m 5**
>
>   - **-r** - Aracın uzaktan (veya etkileşimli olmayan bağlamdan) çalıştırı olduğunu gösterir
>   - **-i** - Diğer ilgili günlüklerle birlikte ağ izleme koleksiyonu için Senaryo bayrağı
>   - **-m** \# - Çalıştıracak dakika sayısı (yukarıdaki örnekte 5 dakika)
