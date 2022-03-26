---
title: Saldırı yüzeyini azaltma kuralları başvurusu
description: Saldırı yüzeyini azaltma kuralları ile ilgili ayrıntıları kural temelinde listeler.
keywords: Saldırı yüzeyini azaltma kuralları, ASR, asr kuralları, hip'ler, izinsiz giriş önleme sistemi, koruma kuralları, exploit kuralları, izinsiz giriş önleme kuralları, hastalık önleme kuralları, bulaşma önleme kuralları, Uç nokta için Microsoft Defender, ASR kurallarını yapılandırma, ASR kural açıklaması
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.date: 02/04/2022
ms.openlocfilehash: 77edaa3d71911bd0594e707996c320285dddabc5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754108"
---
# <a name="attack-surface-reduction-rules-reference"></a>Saldırı yüzeyini azaltma kuralları başvurusu

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Bu makalede saldırı azaltma kuralları hakkında bilgi sağlar:

- [Desteklenen işletim sistemi sürümleri](#supported-operating-systems)
- [Desteklenen yapılandırma yönetim sistemleri](#supported-configuration-management-systems)
- [Kural başına uyarı ve bildirim ayrıntıları](#per-rule-alert-and-notification-details)
- [Kural başına açıklamalar](#per-rule-descriptions)
  - Kural açıklamaları
  - GUID'ler
  - Yapılandırma yönetimi sistemi kural adları

## <a name="public-preview-supported-operating-systems"></a>Genel önizleme: Desteklenen işletim sistemleri

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Aşağıdaki tabloda, şu anda ön kullanım öncesi olarak satışa devam eden saldırı yüzeyini azaltma kuralları için desteklenen işletim sistemleri listelemektedir. Kurallar alfabetik düzende listelenir. Aksi belirtilmedikçe, en düşük Windows&nbsp; 10 derlemesi sürüm 1709 (RS3, derleme 16299) veya sonrasıdır; en düşük Windows&nbsp; Server derlemesi 1809 veya daha yeni bir sürümdür.

> [!NOTE]
> Windows&nbsp; Server2012R2&nbsp;&nbsp; ve Windows&nbsp; Server2016'daki&nbsp; saldırı alanı azaltma kuralları, modern birleşik çözüm paketi kullanılarak ekli cihazlar için kullanılabilir. Daha fazla bilgi için bkz[. R2 ve 2016 Preview'da kullanmak için modern birleşik Windows Server 2012 yeni işlevler](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).
>

| Kural adı | &nbsp;Windows Server 2016 <sup>[[1](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup> |
|---|:---:|:---:|
|[Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme](#block-abuse-of-exploited-vulnerable-signed-drivers) | E | E |
|[Adobe Reader'ın alt işlemleri oluşturmalarını engelleme](#block-adobe-reader-from-creating-child-processes) | E | E |
|[Tüm Office alt işlemleri oluşturmalarını engelleme](#block-all-office-applications-from-creating-child-processes) | E | E |
|[Yerel güvenlik yetkilisi alt sisteminden (Windows) kimlik bilgilerinin çalmasını lsass.exe](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | E | E |
|[E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme](#block-executable-content-from-email-client-and-webmail) | E | E |
|[Yürütülebilir dosyaların yaygın bir yaş veya güvenilir liste ölçütüne uygun olmadıkça çalıştırmalarını engelleme](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | E | E |
|[Kapatılaabilecek betikleri yürütmeyi engelleme](#block-execution-of-potentially-obfuscated-scripts) | E | E |
|[JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | N | N |
|[Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme](#block-office-applications-from-creating-executable-content) | E | E |
|[Diğer Office başka işlemlere kod eklemelerini engelleme](#block-office-applications-from-injecting-code-into-other-processes)  | E | E |
|[Alt Office, iletişim uygulamasının oluşturulmasını engelleme](#block-office-communication-application-from-creating-child-processes) | E | E |
|[WMI olay aboneliği aracılığıyla kalıcılığı engelleme](#block-persistence-through-wmi-event-subscription) \* _Dosya ve klasör dışlamaları desteklenmiyor._ | N | N |
|[PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme](#block-process-creations-originating-from-psexec-and-wmi-commands) | E | E |
|[USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme](#block-untrusted-and-unsigned-processes-that-run-from-usb) | E | E |
|[Makrolar arasında Win32 API Office engelleme](#block-win32-api-calls-from-office-macros) | N | N |
|[Fidye yazılımlarına karşı gelişmiş koruma kullanın](#use-advanced-protection-against-ransomware) | E | E |
|  |  |  |

(<a id="fn1">1</a>) Windows Server 2012 2016 için modern, birleşik çözümü ifade eder. Daha fazla bilgi için bkz. [Uç nokta Windows Defender'a Sunucu Ekleme](configure-server-endpoints.md).

_Genel Önizlemeyi Bitir: Desteklenen işletim sistemleri_

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

Aşağıdaki tabloda, şu anda genel kullanılabilirlik için yayımlanan kurallar için desteklenen işletim sistemleri liste edilmektedir. Kurallar alfabetik düzende listelenir.

> [!Note]
>
> Aksi belirtilmedikçe, en düşük Windows&nbsp; 10 derlemesi sürüm 1709 (RS3, derleme 16299) veya sonrasıdır; en düşük Windows&nbsp; Server derlemesi 1809 veya daha yeni bir sürümdür.
>

|Kural adı|&nbsp;Windows 10|&nbsp;Windows Server 2019|&nbsp;Windows Server|
|---|:---:|:---:|:---:|
|[Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme](#block-abuse-of-exploited-vulnerable-signed-drivers) | E | E | E <br><br> sürüm 1803 (Yarı Yıllık Kanal) veya sonrası |
|[Adobe Reader'ın alt işlemleri oluşturmalarını engelleme](#block-adobe-reader-from-creating-child-processes) | Y sürümü 1809 veya sonrası | E | E  <br><br> |
|[Tüm Office alt işlemleri oluşturmalarını engelleme](#block-all-office-applications-from-creating-child-processes) | E | E | E <br><br> |
|[Yerel güvenlik yetkilisi alt sisteminden (Windows) kimlik bilgilerinin çalmasını lsass.exe](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y sürüm 1803 veya sonrası | E <br><br> | E <br><br> |
|[E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme](#block-executable-content-from-email-client-and-webmail) | E | E <br><br> | E <br><br> |
|[Yürütülebilir dosyaların yaygın bir yaş veya güvenilir liste ölçütüne uygun olmadıkça çalıştırmalarını engelleme](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y sürüm 1803 veya sonrası | E <br><br> | E <br><br> |
|[Kapatılaabilecek betikleri yürütmeyi engelleme](#block-execution-of-potentially-obfuscated-scripts) | E | E <br><br> | E <br><br> |
|[JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | E | E <br><br> | E <br><br> |
|[Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme](#block-office-applications-from-creating-executable-content) | E | E <br><br> | E <br><br> |
|[Diğer Office başka işlemlere kod eklemelerini engelleme](#block-office-applications-from-injecting-code-into-other-processes)  | E | E <br><br> | E <br><br> |
|[Alt Office, iletişim uygulamasının oluşturulmasını engelleme](#block-office-communication-application-from-creating-child-processes) | E | E <br><br> | E <br><br> |
|[WMI olay aboneliği aracılığıyla kalıcılığı engelleme](#block-persistence-through-wmi-event-subscription) <br><br> \*_Dosya ve klasör dışlamaları desteklenmiyor._ | Y sürüm 1903 (derleme 18362) veya sonrası| E | E <br><br> sürüm 1903 (derleme 18362) veya sonrası |
|[PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y sürüm 1803 veya sonrası | E <br><br> | E <br><br>  |
|[USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme](#block-untrusted-and-unsigned-processes-that-run-from-usb) | E | E <br><br> | E <br><br> |
|[Makrolar arasında Win32 API Office engelleme](#block-win32-api-calls-from-office-macros) | E | E <br><br> | E <br><br> |
|[Fidye yazılımlarına karşı gelişmiş koruma kullanın](#use-advanced-protection-against-ransomware) | Y sürüm 1803 veya sonrası | E <br><br> | E <br><br> |
|  |  |  |  |

## <a name="supported-configuration-management-systems"></a>Desteklenen yapılandırma yönetim sistemleri

Bu tabloda başvurulan yapılandırma yönetim sistemi sürümleriyle ilgili bilgilere bağlantılar bu tablonun altında listelenmiştir.

|Kural adı | Intune | Microsoft Endpoint Manager |Microsoft Uç Noktası Yapılandırma Yöneticisi |Grup İlkesi<sup>[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme](#block-abuse-of-exploited-vulnerable-signed-drivers) | E  | Y MEM OMA-URI |   | E  |  E  |
|[Adobe Reader'ın alt işlemleri oluşturmalarını engelleme](#block-adobe-reader-from-creating-child-processes) | E |   | E | E  | E  |
|[Tüm Office alt işlemleri oluşturmalarını engelleme](#block-all-office-applications-from-creating-child-processes) | E |   |E <br><br> CB 1710 | E  | E  |
|[Yerel güvenlik yetkilisi alt sisteminden (Windows) kimlik bilgilerinin çalmasını lsass.exe](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | E  |   | E <br><br>CB 1802 | E  | E  |
|[E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme](#block-executable-content-from-email-client-and-webmail) | E |  |E <br><br> CB 1710 | E | E  |
|[Yürütülebilir dosyaların yaygın bir yaş veya güvenilir liste ölçütüne uygun olmadıkça çalıştırmalarını engelleme](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | E |   | E <br><br> CB 1802 |  E |  E |
|[Kapatılaabilecek betikleri yürütmeyi engelleme](#block-execution-of-potentially-obfuscated-scripts) | E |   |  E  <br><br> CB 1710 | E  | E  |
|[JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | E |   | E <br><br> CB 1710 | E  | E  |
|[Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme](#block-office-applications-from-creating-executable-content) | E |  |E <br><br> CB 1710 | E  | E  |
|[Diğer Office başka işlemlere kod eklemelerini engelleme](#block-office-applications-from-injecting-code-into-other-processes) | E |  | E <br><br> CB 1710 | E  | E  |
|[Alt Office, iletişim uygulamasının oluşturulmasını engelleme](#block-office-communication-application-from-creating-child-processes) | E |  |E <br><br> CB 1710 | E  | E  |
|[WMI olay aboneliği aracılığıyla kalıcılığı engelleme](#block-persistence-through-wmi-event-subscription) |  |  |  |E   | E  |
|[PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme](#block-process-creations-originating-from-psexec-and-wmi-commands) | E |   |   |  E | E  |
|[USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme](#block-untrusted-and-unsigned-processes-that-run-from-usb) | E |   |E <br><br> CB 1802  | E  | E  |
|[Makrolar arasında Win32 API Office engelleme](#block-win32-api-calls-from-office-macros) | E |   | E <br><br> CB 1710  | E  |  E |
|[Fidye yazılımlarına karşı gelişmiş koruma kullanın](#use-advanced-protection-against-ransomware) | E |   | E <br><br> CB 1802 | E  | E  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) Herhangi bir kuralın GUID'lerini kullanarak saldırı yüzeyi azaltma kurallarını kural temelinde yapılandırabilirsiniz.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM artık Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Kural başına uyarı ve bildirim ayrıntıları

Engelleme modunda tüm kurallar için bildirim bildirimleri oluşturulur. Diğer modlardan herhangi bir kural bildirim oluşturmaz

"Kural Durumu" belirtilen kurallar için:

- Birleşimler ile \<ASR Rule, Rule State\> ASR kuralları yalnızca yüksek bulut bloğu düzeyindeki cihazlar için Uç Nokta için Microsoft Defender'da uyarıların (uyarı bildirimleri) ortaya çıkarilmesi için kullanılır. Yüksek bulut engelleme düzeyinde yer alan cihazlar herhangi bir ASR Kuralı, <Durum veya> uyarı oluşturmaz
- EDR, ancak yalnızca yüksek bulut bloğu düzeyindeki cihazlarda ASR kuralları için uyarı oluşturulur.

| Kural adı: | Kural durumu: | Posta'da uyarılar EDR? <br> (Evet&nbsp;\|&nbsp;Hayır) | Uyarı bildirimleri mi oluştursunuz? <br> (Evet&nbsp;\|&nbsp;Hayır) |
|---|:---:|:---:|:---:|
|   |   |  _Yalnızca yüksek bulut bloğu düzeyindeki cihazlar için_ | _Yalnızca Engelleme modunda_ |
|[Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | E |
|[Adobe Reader'ın alt işlemleri oluşturmalarını engelleme](#block-adobe-reader-from-creating-child-processes) | Engelle  | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[Tüm Office alt işlemleri oluşturmalarını engelleme](#block-all-office-applications-from-creating-child-processes) |   | N | E |
|[Yerel güvenlik yetkilisi alt sisteminden (Windows) kimlik bilgilerinin çalmasını lsass.exe](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | E |
|[E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme](#block-executable-content-from-email-client-and-webmail) |   | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[Yürütülebilir dosyaların yaygın bir yaş veya güvenilir liste ölçütüne uygun olmadıkça çalıştırmalarını engelleme](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | E |
|[Kapatılaabilecek betikleri yürütmeyi engelleme](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | N \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Engelle | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | E <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme](#block-office-applications-from-creating-executable-content) |   | N | E |
|[Diğer Office başka işlemlere kod eklemelerini engelleme](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | E |
|[Alt Office, iletişim uygulamasının oluşturulmasını engelleme](#block-office-communication-application-from-creating-child-processes) |  |  N | E |
|[WMI olay aboneliği aracılığıyla kalıcılığı engelleme](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | N \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | E |
|[USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | N \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|[Makrolar arasında Win32 API Office engelleme](#block-win32-api-calls-from-office-macros) |   | N | E |
|[Fidye yazılımlarına karşı gelişmiş koruma kullanın](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir  | N \| Y <br> Cihazın yüksek bulut blok düzeyinde olması gerekir |
|   |   |   |   |
  
## <a name="asr-rule-modes"></a>ASR kuralı modları

- **Yapılandırılmadı veya** **Devre** Dışı Bırak: Bu, ASR kuralının etkinleştirilmemiş veya devre dışı bırakılmıştır. Bu eyaletin kodu = 0.
- **Engelle**: Bu, ASR kuralının etkinleştiril olduğu durumduz. Bu eyaletin kodu 1'dir.
- **Denetim**: Bu, ASR kuralının dağıtıldı kuruluşa veya ortama karşı etkili davranışı için değerlendiri olduğu durumdur. Bu eyaletin kodu 2'dir.
- **Uyar** Bu, ASR kuralının etkin olduğu durum olup son kullanıcıya bir bildirim sunar, ancak son kullanıcının engeli atlayarak buna izin vermesini sağlar. Bu eyaletin kodu 6'dır.

_Uyarı modu_ , kullanıcıları olası riskli eylemler hakkında uyaran bir engelleme modu t t modudur. Kullanıcılar engelleme uyarı mesajını atlayarak temel eyleme izin vermeyi seçebilir. Kullanıcılar **Bloğu zorunlu** kılınacak şekilde Tamam'ı seçerek veya bloğun zamanında oluşturulan son kullanıcı açılır bildirimiyle atlama **seçeneğini -** Engellemeyi Kaldır seçeneğini belirleyin. Uyarının engellemesi kaldırktan sonra, uyarı iletisi bir sonraki kez ortaya geçene kadar işleme izin verilir ve bu sırada son kullanıcının eylemin yenidenpertesi gerekir.

İzin Ver düğmesine tıklırsanız engelleme 24 saat boyunca engellenir. 24 saat sonra, son kullanıcının engellemeye yeniden izin vermesi gerekir. ASR kuralları için uyarı modu yalnızca RS5+ (1809+) cihazlarında destekler. Eski sürümlere sahip cihazlarda ASR kurallarına atla atanırsa kural engellenmiş modda çalışır.

Ayrıca, yalnızca uyarı modunu "Uyar" olarak belirterek PowerShell aracılığıyla uyarı AttackSurfaceReductionRules_Actions bir kural da belirtebilirsiniz. Örneğin:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Kural açıklamaları başına

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme

Bu kural, uygulamanın korumasız imzalı bir sürücüyü diske yazmasını engellemektedir. Joker karakterli, korumasız sürücüler \-  \-, çekirdeke erişim kazanmak için yeterli ayrıcalıklara sahip yerel uygulamalar tarafından kullanılabilir. Zayıf imzalı sürücüler, saldırganların güvenlik çözümlerini devre dışı bırakmasına veya tehlikeye atabilmesine olanak sağlar ve sonunda sistem güvenliğinin tehlikeye atabilmesine neden olur.

**Açıklardan yararlanan ve korumasız imzalı** sürücülerin kötüye kullanımına engelle kuralı, sistemde zaten var olan bir sürücünün yüklenmesini engellemez.

> [!NOTE]
>
> Bu kuralı MEM OMA-URI kullanarak yapılandırsanız. Özel [kuralları yapılandırmak için bkz. MEM OMA-URI](enable-attack-surface-reduction.md#mem) .
>
> Ayrıca, Bu kuralı [PowerShell kullanarak da yapılandırabilirsiniz](enable-attack-surface-reduction.md#powershell).
>
> Sürücüyü incelemek için, çözümleme için bir sürücü göndermek üzere bu Web [sitesini kullanın](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

Intune Adı: `Block abuse of exploited vulnerable signed drivers` (henüz kullanılamıyor)

Yapılandırma Yöneticisi adı: Henüz kullanılamıyor
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies:
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Adobe Reader'ın alt işlemleri oluşturmalarını engelleme

Bu kural Adobe Reader'ın süreç oluşturmasını engelleyerek saldırılar önler.

Sosyal mühendislik veya açıklardan yararlanan kötü amaçlı yazılımlar yüklerini indirip başlatarak Adobe Reader'ı yok etmeye devam ediyor. Çocuk işlemlerinin Adobe Reader tarafından oluşturulmasını engelleyerek, kötü amaçlı yazılımla vektör olarak kullanmayı denemeniz engellenebilir.

Intune adı: `Process creation from Adobe Reader (beta)`

Yapılandırma Yöneticisi adı: Henüz kullanılamıyor

GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Gelişmiş av eylem türü:

- AsrAdobeReaderProcessAudited
- AsrAdobeReaderProcessBlocked

Bağımlılıklar: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Tüm Office alt işlemleri oluşturmalarını engelleme

Bu kural, Office işlemleri oluşturmalarını engeller. Office word, Excel, PowerPoint, OneNote ve Access'i içerir.

Kötü amaçlı alt işlemler oluşturmak, yaygın bir kötü amaçlı yazılım stratejisidir. Bir vektör olarak kullanan Office kötü amaçlı yazılım, çoğunlukla daha fazla yük indirmek ve çalıştırmak için VBA makroları ve açıklarından yararlanma kodu çalıştırır. Bununla birlikte, bazı yasal iş hattı uygulamaları da amacına yönelik alt süreçler oluştursa da; örneğin, bir komut istemini ya da Kayıt Defteri ayarlarını yapılandırmak için PowerShell'i kullanmak gibi.

Intune adı: `Office apps launching child processes`

Yapılandırma Yöneticisi adı: `Block Office application from creating child processes`

GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Gelişmiş av eylem türü:

- AsrOfficeProcessAudited
- AsrOfficeProcessBlocked

Bağımlılıklar: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Yerel güvenlik yetkilisi alt sisteminden Windows çalmak için kimlik bilgilerini engelleme

Bu kural, Yerel Güvenlik Yetkilisi Alt Sistemi Hizmetini (LSASS) kilitleyerek kimlik bilgilerinin çalınmalarını önlemeye yardımcı olur.

LSASS, aynı bilgisayarda oturum alan kullanıcıların kimliğini Windows sağlar. Microsoft Defender Credential Guard Windows, LSASS'den kimlik bilgileri ayıklamaya yönelik denemeleri normalde engellemaktadır. Bununla birlikte, bazı kuruluşlar özel akıllı kart sürücüleriyle veya Yerel Güvenlik Yetkilisi'ne (LSA) yüklene diğer programlarla ilgili uyumluluk sorunları nedeniyle tüm bilgisayarlarında Credential Guard'i etkinleştiremmektedir. Bu gibi durumlarda, saldırganlar LSASS'den net metin parolalarını ve NTLM karmalarını karalayık için Mimikatz gibi korsanlar araçlarını kullanabilir.

> [!NOTE]
> Bazı uygulamalarda, kod tüm çalışan işlemleri numaralaraer ve çok kapsamlı izinlerle bunları açmaya çalışır. Bu kural uygulamanın işlem açma eylemlerini geriler ve ayrıntıları güvenlik olay günlüğüne kaydeder. Bu kural çok fazla gürültüye neden olabilir. Yalnızca LSASS'yi numaralandıran ancak işlevselliği gerçekten etkilemeyen bir uygulama varsa, bunu dışlama listesine eklemenize gerek yoktur. Tek başına, bu olay günlüğü girdisi kötü amaçlı bir tehdit olduğu anlamına gelmez.
  
> [!IMPORTANT]
> Saldırı Yüzeyini Azaltma (ASR) kuralı için "Windows yerel güvenlik yetkilisi alt sisteminden (lsass.exe)" kimlik bilgilerini engelleme kuralı için varsayılan durum Yapılandırılmadı olarak değişir ve varsayılan mod Engellendi olarak **ayarlanır**.  Diğer tüm ASR kuralları varsayılan durumda kalır: **Yapılandırılmadı**. Son kullanıcı bildirimlerini azaltmak için ek filtreleme mantığı kurala zaten dahil edildi. Müşteriler kuralı Denetim, Uyar veya **Devre** Dışı **Modları** **olarak yapılandırabilir** ve varsayılan modu geçersiz kılar. Bu kuralın işlevselliği aynıdır; kuralın varsayılan olarak modunda yapılandırılması veya Engelleme modunu el ile etkinleştirmeniz gerekir.  

Intune adı: `Flag credential stealing from the Windows local security authority subsystem`

Yapılandırma Yöneticisi adı: `Block credential stealing from the Windows local security authority subsystem`

GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Gelişmiş av eylem türü:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Bağımlılıklar: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme

Bu kural, aşağıdaki dosya türlerinin Microsoft Outlook uygulamasında veya Outlook.com'da ve diğer popüler web posta sağlayıcılarının içinde açılan e-postalardan başlatılmasını engeller:

- Yürütülebilir dosyalar (.exe, .dll veya .scr gibi)
- Betik dosyaları (PowerShell .ps, Visual Basic .vbs veya JavaScript .js)

Intune adı: `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager adı:`Block executable content from email client and webmail`

GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Gelişmiş av eylem türü:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Bağımlılıklar: MDAV

> [!NOTE]
> Kullandığınız uygulamaya **bağlı olarak, e-posta istemci ve web postalarından** yürütülebilir içeriği engelleme kuralı, aşağıdaki alternatif açıklamalara sahip olur:
>
> - Intune (Yapılandırma Profilleri): Yürütülebilir içerik (exe, dll, ps, js, vbs, vb.) e-postadan (web postası/posta istemcisi) atılır (özel durum yoktur).
> - Endpoint Manager: E-posta ve web posta istemcilerinden yürütülebilir içerik indirmesini engelin.
> - Grup İlkesi: E-posta istemcisi ve web postası için yürütülebilir içeriği engelin.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Yürütülebilir dosyaların yaygın bir yaş veya güvenilir liste ölçütüne uygun olmadıkça çalıştırmalarını engelleme

Bu kural yürütülebilir dosyaları (.exe, .dll veya .scr gibi) başlatmalarını engeller. Dolayısıyla, güvenilmeyen veya bilinmeyen yürütülebilir dosyaları başlatmak riskli olabilir, çünkü dosyalar kötü amaçlı dosyalar ise başlangıçta açık değildir.

> [!IMPORTANT]
> Bu kuralı [kullanmak için bulut teslimi korumasını](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) etkinleştirmeniz gerekir.
>
> **Yürütülebilir dosyaların**, GUID ile birlikte bir yaygınlık, `01443614-cd74-433a-b99e-2ecdc07bfc25` yaş veya güvenilir liste ölçütüne uygun olmadığı sürece çalıştırmasını engelle kuralı Microsoft'a aittir ve yöneticiler tarafından belirtilmez. Bu kural, güvenilir listesini düzenli olarak güncelleştirmek için bulut teslimi koruması kullanır.
>
> Tek tek dosyaları veya klasörleri (klasör yollarını veya tam kaynak adlarını kullanarak) belirtebilirsiniz, ancak hangi kuralların veya dışlamaların geçerli olduğunu belirtemezseniz.

Intune adı: `Executables that don't meet a prevalence, age, or trusted list criteria`

Yapılandırma Yöneticisi adı: `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

Gelişmiş av eylem türü:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Bağımlılıklar: MDAV, Bulut Koruması

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Kapatılaabilecek betikleri yürütmeyi engelleme

Bu kural, sahipsiz bir betiğin içinde şüpheli özellikler algılar.

Betik gizleme, hem kötü amaçlı yazılım yazarlarının hem de yasal uygulamaların fikri mülkiyeti gizlemek veya betik yükleme sürelerini azaltmak için kullanabileceği yaygın bir tekniktir. Kötü amaçlı yazılım yazarları, kötü amaçlı kodun okunmalarını zorlaştıracak şekilde kapatmayı da kullanır ve bu da insanların ve güvenlik yazılımlarının yakın incelemesini engeller.

Intune adı: `Obfuscated js/vbs/ps/macro code`

Yapılandırma Yöneticisi adı: `Block execution of potentially obfuscated scripts`

GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Gelişmiş av eylem türü:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Bağımlılıklar: MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme

Bu kural, betiklerin kötü amaçlı olarak indirilmiş olabilecek içeriği başlatmasını önler. JavaScript veya VBScript'te yazılmış kötü amaçlı yazılım, çoğunlukla İnternet'te başka bir kötü amaçlı yazılımı getirmek ve başlatmak için bir indirmeci gibi davranır.

Yaygın olsa da, iş dizisi uygulamaları bazen yükleyicileri indirmek ve başlatmak için betikler kullanır.

Intune adı: `js/vbs executing payload downloaded from Internet (no exceptions)`

Yapılandırma Yöneticisi adı: `Block JavaScript or VBScript from launching downloaded executable content`

GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

Gelişmiş av eylem türü:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Bağımlılıklar: MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme

Bu kural, Office kodların diske yaz Excel engelleyerek Word, Excel ve PowerPoint gibi birçok uygulamanın kötü amaçlı olabilecek yürütülebilir içerik oluşturmasını engellemesini sağlar.

Vektör olarak ihlal eden Office kötü amaçlı yazılım, kötü amaçlı bileşenleri diske Office kötü amaçlı bileşenleri parçalara ayrılmaya veya kaydetmeye çalışabilirsiniz. Bu kötü amaçlı bileşenler, bilgisayarın yeniden başlatılmasını ve sistem üzerinde kalıcı halede kalmalarını sağlar. Bu nedenle, bu kural yaygın bir kalıcılık tekniğini savunur.

Intune adı: `Office apps/macros creating executable content`

SCCM adı: `Block Office applications from creating executable content`

GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

Gelişmiş av eylem türü:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Bağımlılıklar: MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Diğer Office başka işlemlere kod eklemelerini engelleme

Bu kural, uygulama ekleme Office diğer işlemlere ekleme girişimlerini engeller.

Saldırganlar, kod ekleme Office uygulamalar kullanarak kötü amaçlı uygulamaları başka işlemlere geçirmeyi sınayabilir, böylece kod temiz bir işlem olarak maskeli olabilir.

Kod eklemenin bilinen yasal iş amacı yoktur.

Bu kural Word, Excel ve PowerPoint.

Intune adı: `Office apps injecting code into other processes (no exceptions)`

Yapılandırma Yöneticisi adı: `Block Office applications from injecting code into other processes`

GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Gelişmiş av eylem türü:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Bağımlılıklar: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Alt Office, iletişim uygulamasının oluşturulmasını engelleme

Bu kural, diğer Outlook işlemleri oluşturmasını engelle birlikte yasal veya yasal Outlook olanak sağlar.

Bu kural sosyal mühendislik saldırılarını korur ve koddan yararlanmayı bu uygulamanın güvenlik açıklarından yararlanmasını Outlook. Ayrıca, kullanıcı kimlik [Outlook güvenliği](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) ihlal edildiklerde saldırganların kullanabileceği kural ve form açıklarından yararlanmaya karşı da koruma sağlar.

> [!NOTE]
> Bu kural, diğer tüm işlerde DLP ilkesi ipuçlarını ve Araç Outlook. Bu kural yalnızca Outlook.com Outlook.com için geçerlidir.

Intune adı: `Process creation from Office communication products (beta)`

Yapılandırma Yöneticisi adı: Kullanılamıyor

GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

Gelişmiş av eylem türü:

- AsrOfficeCommAppProcessAudited
- AsrOfficeCommAppProcessBlocked

Bağımlılıklar: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>WMI olay aboneliği aracılığıyla kalıcılığı engelleme

Bu kural, bir cihazda kalıcılığı ulaşmak için kötü amaçlı yazılımların WMI'ya kötü amaçlı yazılım engellemesini engeller.

> [!IMPORTANT]
> Dosya ve klasör dışlamaları bu saldırı yüzeyini azaltma kuralı için geçerli değildir.

Dosyasız tehditlerle gizli kalmak, dosya sisteminde görülmemek ve düzenli olarak yürütme denetimi kazanmak için çeşitli taktikler kullanır. Bazı tehditlere karşı, GIZLI kalmak için WMI deposunu ve olay modelini kötüye kullanabilir.

Intune adı: Kullanılamaz

Yapılandırma Yöneticisi adı: Kullanılamıyor

GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Gelişmiş av eylem türü:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Bağımlılıklar: MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme

Bu kural [PsExec](/sysinternals/downloads/psexec) ve WMI aracılığıyla oluşturulan [işlemlerin çalışmalarını](/windows/win32/wmisdk/about-wmi) engeller. Hem PsExec hem de WMI kodu uzaktan çalıştırabilir, dolayısıyla bu işlevselliği komut ve denetim amacıyla kötü amaçlı yazılımlar tarafından kötü amaçlı olarak kullanmak veya kuruluş ağının her yerine bulaşma riski vardır.

> [!WARNING]
> Bu kuralı yalnızca cihazlarınızı [Intune](/intune) veya başka bir MDM çözümüyle yönetiyorsanız kullanın. Bu kural, Configuration Manager istemcisinin [doğru Microsoft Endpoint Configuration Manager](/configmgr) IÇIN KULLANDıĞı WMI komutlarını engeller.

Intune adı: `Process creation from PSExec and WMI commands`

Yapılandırma Yöneticisi adı: Geçerli değil

GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Gelişmiş av eylem türü:

- AsrPsexecWmiProcessAudited
- AsrPsexecWmiProcessBlocked

Bağımlılıklar: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme

Bu kuralla, yöneticiler SD kartları da dahil olmak üzere USB çıkarılabilir sürücülerden imzalanmamış veya güvenilmeyen yürütülebilir dosyaları çalıştırmayı önlenebilir. Engellenen dosya türleri yürütülebilir dosyalar içerir (.exe, .dll veya .scr gibi)

Intune adı: `Untrusted and unsigned processes that run from USB`

Yapılandırma Yöneticisi adı: `Block untrusted and unsigned processes that run from USB`

GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Gelişmiş av eylem türü:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Bağımlılıklar: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Makrolar arasında Win32 API Office engelleme

Bu kural VBA makrolarının Win32 API'lerini aramasını önler.

Office VBA, Win32 API çağrılarını sağlar. Kötü amaçlı yazılım, doğrudan diske bir şey yazmadan [Win32 API'lerini](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) çağırarak kötü amaçlı kabukkodu başlatma gibi bu özelliği kötüye kullanımına neden olabilir. Çoğu kuruluş, makroları başka şekillerde kullanıyor olsalar bile, günlük işlevlerinde Win32 API'lerini arama özelliğine güvenmez.

Desteklenen işletim sistemleri:

- [Windows 10, sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, sürüm 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Intune adı: `Win32 imports from Office macro code`

Yapılandırma Yöneticisi adı: `Block Win32 API calls from Office macros`

GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Gelişmiş av eylem türü:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Bağımlılıklar: MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Fidye yazılımlarına karşı gelişmiş koruma kullanın

Bu kural fidye yazılımlarına karşı ek bir koruma katmanı sağlar. Dosyanın fidye yazılımına benzeip benzeme olmadığını belirlemek için hem istemci hem de bulut gericiliği kullanır. Bu kural, aşağıdaki özelliklerden birini veya birden fazlasını bulunduran dosyaları engellemez:

- Dosyanın Microsoft bulutunda zaten iş dışı olduğu bulundu.
- Dosya geçerli bir imzalanmış dosyadır.
- Dosya, fidye yazılımı olarak dikkate alınmayacak kadar yaygındır.

Kural, fidye yazılımlarını önlemek için dikkatli bir kenarda hataya neden olur.

> [!NOTE]
> Bu kuralı [kullanmak için bulut teslimi korumasını](enable-cloud-protection-microsoft-defender-antivirus.md) etkinleştirmeniz gerekir.

Intune adı: `Advanced ransomware protection`

Yapılandırma Yöneticisi adı: `Use advanced protection against ransomware`

GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

Gelişmiş av eylem türü:

- AsrRansomwareAudited
- AsrRansomwareBlocked

Bağımlılıklar: MDAV, Bulut Koruması
