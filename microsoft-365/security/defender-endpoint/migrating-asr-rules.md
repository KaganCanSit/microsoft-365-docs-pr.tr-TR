---
title: Üçüncü taraf HIPS'den ASR kurallarınama
description: Üçüncü taraf bir Ana Bilgisayar Engelleme Sistemi (HIPS) çözümünden ASR kurallarına geçişe nasıl yaklaş yaklaşın açıklaması vardır.
keywords: Saldırı yüzeyini azaltma kuralları, asr, asr kuralları, hip'ler, izinsiz giriş önleme sistemi, koruma kuralları, exploit önleme, izinsiz giriş önleme, exploit, bulaşma önleme, Uç nokta için Microsoft Defender
ms.topic: article
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 2530f38bdcfdbb74bdd9a80c59c53c9e273e1449
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2021
ms.locfileid: "63019091"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>Üçüncü taraf HIPS'den ASR kurallarınama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makale, genel kuralları Uç Nokta için Microsoft Defender ile eşlemenizi sağlar.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>Üçüncü taraf HIPS üründen ASR kurallarına nasıl başlandı?

### <a name="block-creation-of-specific-files"></a>Belirli dosyaların oluşturulmasını engelleme

- **Şu işlemler** için geçerlidir: Tüm işlemler
- **İşlem**- Dosya Oluşturma
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerler, İşlemler, Hizmetler**- *.zeole, *.odin, *.locky, *.jaff, *.lukitus, *.wnry, *.krab
- **Saldırı Surface Azaltma kuralları** - ASR kuralları Güvenlik (IOC) Göstergelerini değil saldırı tekniklerini engellemektedir. Belirli bir dosya uzantısını engellemek, cihazın güvenliğinin tehlikeye atsını önlemey sürece her zaman yararlı olur. Saldırılar yalnızca yük için yeni bir dahili telefon türü oluşturana kadar kısmen saldırıya neden olur.
- **Diğer önerilen özellikler**: Bulut Koruma ve Davranış Çözümlemesi ile birlikte Microsoft Defender AV'nin etkin olması kesinlikle önerilir. ASR kuralı "Fidye yazılımlarına karşı gelişmiş koruma kullan" gibi diğer önlemeleri kullanmalarını öneririz. Bu, fidye yazılımı saldırılarına karşı daha yüksek koruma düzeyi sağlar. Ayrıca bu kayıt defteri anahtarlarının birçoğu, ASEP teknikleri gibi Uç Nokta için Microsoft Defender tarafından izlenir ve bu da belirli uyarıları tetikler. Kullanılan kayıt defteri anahtarları en az Yerel Yönetici veya Güvenilen Yükleyici ayrıcalıklarının değiştirilebilir olması gerekir. En düşük yönetim hesapları veya haklarıyla birlikte, kilitli bir ortam kullanılması önerilir. Daha geniş güvenlik önerilerimizin bir parçası olan "Gerekilmeyen roller için Hata Ayıklamayı Devre Dışı Bırak" gibi diğer sistem yapılandırmaları etkinleştirilebilir.

### <a name="block-creation-of-specific-registry-keys"></a>Belirli kayıt defteri anahtarları oluşturulmasını engelleme

- **Şu işlemler** için geçerlidir: Tüm İşlemler
- **İşlemler** - Yok
- **Operation**- Registry Modifications
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler**-  *\* Software,HKCU\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess
- **Saldırı Surface Azaltma kuralları** - ASR kuralları Güvenlik (IOC) Göstergelerini değil saldırı tekniklerini engellemektedir. Belirli bir dosya uzantısını engellemek her zaman yararlı olur, çünkü cihazın güvenliğini engellemez. Saldırılar yalnızca yük için yeni bir dahili telefon türü oluşturana kadar kısmen saldırıya neden olur.
- **Diğer önerilen özellikler**: Bulut Koruma ve Davranış Çözümlemesi ile birlikte Microsoft Defender AV'nin etkin olması kesinlikle önerilir. ASR kuralı "Fidye yazılımlarına karşı gelişmiş koruma kullanın" gibi ek önleme özellikleri öneririz. Bu, fidye yazılımı saldırılarına karşı daha yüksek koruma düzeyi sağlar. Ayrıca, BU kayıt defteri anahtarlarının birkaçı da, ASEP teknikleri gibi Uç Nokta için Microsoft Defender tarafından izlenir ve bu da belirli uyarıları tetikler. Buna ek olarak, kullanılan kayıt defteri anahtarları en az Yerel Yönetici veya Güvenilen Yükleyici ayrıcalıkları gerektirir. En düşük yönetim hesapları veya haklarıyla birlikte, kilitli bir ortam kullanılması önerilir. Daha geniş güvenlik önerilerimizin bir parçası olan "Gerekilmeyen roller için Hata Ayıklamayı Devre Dışı Bırak" gibi diğer sistem yapılandırmaları etkinleştirilebilir.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>Güvenilmeyen programların çıkarılabilir sürücülerden çalıştırmalarını engelleme

- **USB'den** Güvenilmeyen Programlar için geçerlidir
- **İşlemler**- *
- **Operation**- Process Execution
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler:-*
- **Saldırı Surface** Azaltma kuralları- ASR kuralları, çıkarılabilir sürücülerde güvenilmeyen ve imzalanmamış programların başlatılmasını önlemeye yönelik yerleşik bir kurala sahiptir: "USB'den çalıştırılabilen güvenilmeyen ve imzasız işlemleri engelle", GUID "b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4".
- **Diğer önerilen özellikler**- Lütfen Uç Nokta için Microsoft Defender'ı kullanarak USB cihazları ve diğer çıkarılabilir medyalar için ek denetimleri keşfedin:Uç Nokta için [Microsoft Defender'ı kullanarak USB](/windows/security/threat-protection/device-control/control-usb-devices-using-intune) cihazları ve diğer çıkarılabilir medyaları denetleme.

### <a name="block-mshta-from-launching-certain-child-processes"></a>Mshta'nın bazı alt işlemleri başlatmalarını engelleme

- **Şu için geçerlidir**: Mshta
- **İşlemler**- mshta.exe
- **Operation**- Process Execution
- **Dosya/Klasör, Kayıt Defteri Anahtarları/Değerleri, İşlemler,** Hizmetler- powershell.exe, cmd.exe, regsvr32.exe
- **Saldırı Surface Azaltma kuralları**- ASR kuralları, alt işlemlerin "Saldırı" olarak engellemesini önleyen belirli bir mshta.exe. Bu denetim Exploit Protection veya Windows Defender Application Control kapsamındadır.
- **Diğer önerilen özellikler**: Windows Defender'nin tamamen mshta.exe için Uygulama Denetimi'ne etkinleştirin. Organizasyon, iş hattı uygulamaları için "mshta.exe" gerektiriyorsa, bu kuralın alt işlemleri başlatmasını önlemek için belirli bir Windows Defender Exploit Protection mshta.exe bir kural yapılandırabilirsiniz.

### <a name="block-outlook-from-launching-child-processes"></a>Outlook işlemleri başlatmalarını engelleme

- **Şu için geçerlidir**: Outlook
- **İşlemler**- outlook.exe
- **Operation**- Process Execution
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler**- powershell.exe
- **Saldırı Surface** Azaltma kuralları- ASR kuralları, Office iletişim uygulamalarının (Outlook, Skype ve Teams) alt işlemleri başlatmasını önlemeye yönelik yerleşik bir kurala sahiptir: "Office iletişim uygulamasının alt işlemleri oluşturmasını engelle", GUID "26190899-1602-49e8-8b27-eb1d0a1ce869".
- **Diğer önerilen özellikler**- PowerShell'den saldırı yüzeyini en aza indirmek için PowerShell kısıtlanmış dil modunu etkinleştirmenizi öneririz.

### <a name="block-office-apps-from-launching-child-processes"></a>Office uygulamalarının alt işlemleri başlatmalarını engelleme

- **Şu için geçerlidir**: Office
- **İşlemler**- winword.exe, powerpnt.exe, excel.exe
- **Operation**- Process Execution
- **Dosya/Klasörler,** Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler powershell.exe, cmd.exe, wscript.exe, mshta.exe, EQNEDT32.EXE, regsrv32.exe
- **Saldırı Surface** Azaltma kuralları- ASR kuralları, Office uygulamalarının alt işlemleri başlatmasını önlemeye yönelik yerleşik bir kurala sahiptir: "Tüm Office uygulamalarının alt işlemleri oluşturmasını engelle", GUID "d4f940ab-401b-4efc-aadc-ad5f3c50688a".
- **Diğer önerilen özellikler** - Yok

### <a name="block-office-apps-from-creating-executable-content"></a>Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme

- **Şu için geçerlidir**: Office
- **İşlemler**- winword.exe, powerpnt.exe, excel.exe
- **İşlem**- Dosya Oluşturma
- **Dosya/Klasör Örnekleri** Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler- C:\Users *\AppData **.exe, C:\ProgramData**.exe, C:\ProgramData**.com, C:\UsersAppData*\Local\**Temp.com, C:\Users*\Downloads**.exe, C:\Users *\AppData.scf **, C:\ProgramData.scf**, C:\Users\Public*.exe, C:\Users*\Desktop***.exe
- **Saldırı Yüzeyini Azaltma kuralları** - Yok.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>Wscript'in belirli dosya türlerini okumalarını engelleme

- **Için geçerlidir**- Wscript
- **İşlemler**- wscript.exe
- **operation**- file read
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler**- C:\Users *\AppData**.js, C:\Users\* Downloads**.js
- **Saldırı Surface Azaltma kuralları**- Güvenilirlik ve performans sorunlarından dolayı ASR kuralları, belirli bir betik dosya türünü belirli bir sürecin okumasını engelleme özelliğine sahip değildir. Bu senaryolardan kaynaklanan saldırı vektörlerini önlemeye yönelik bir kuralımız var. Kural adı: "JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatmalarını engelleme" (GUID "d3e037e1-3eb8-44c8-a917-57927947596 ve "Gizli olabilecek betiklerin yürütülmesini engelle" (GUID " 5beb7efe-fd9a-4556-801d-275e5ffc04cc").
- Diğer önerilen **özellikler- Bu** senaryolarda belirli saldırı vektörlerini azaltmak için belirli ASR kuralları olsa da, AV'nin varsayılan olarak Kötü Amaçlı Yazılımdan Koruma Tarama Arabirimi (AMSI) aracılığıyla betikleri (PowerShell, Windows Betik Ana Bilgisayarı, JavaScript, VBScript ve daha birçok özelliği) gerçek zamanlı olarak inceleyebiliyor olduğu bahsetmeniz önemlidir. Daha fazla bilgiyi burada edinebilirsiniz: [Kötü amaçlı yazılımdan Koruma Tarama Arabirimi (AMSI)](/windows/win32/amsi/antimalware-scan-interface-portal).

### <a name="block-launch-of-child-processes"></a>Alt işlemlerin başlatılmasını engelle

- **Adobe** Acrobat için geçerlidir
- **İşlemler**- AcroRd32.exe, Acrobat.exe
- **Operation**- Process Execution
- **Dosya/Klasör, Kayıt Defteri Anahtarları/Değerleri, İşlemler,** Hizmetler- cmd.exe, powershell.exe, wscript.exe
- **Saldırı Surface Azaltma kuralları**- ASR kuralları Adobe Reader'ın alt işlemleri başlatmalarını engellemeye olanak sağlar. Kural adı, "Adobe Reader'ın alt işlemleri oluşturmalarını engelle", GUID "7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c" şeklindedir.
- **Diğer önerilen özellikler** - Yok

### <a name="block-download-or-creation-of-executable-content"></a>Yürütülebilir içerik indirmeyi veya oluşturulmasını engelleme

- **-** CertUtil için geçerlidir: Yürütülebilir dosya indirmeyi veya oluşturulmasını engelleme
- **İşlemler**- certutil.exe
- **İşlem**- Dosya Oluşturma
- **Dosya/Klasör Örnekleri, Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler**- *.exe
- **Saldırı Surface Azaltma kuralları**- ASR kuralları bu senaryoları desteklemez çünkü bunlar Koruma koruma Microsoft Defender Virüsten Koruma vardır.
- **Önerilen diğer özellikler**- Microsoft Defender AV CertUtil'in yürütülebilir içerik oluşturmasını veya indirmesini engeller.

### <a name="block-processes-from-stopping-critical-system-components"></a>İşlemlerin kritik Sistem bileşenlerini durdurmalarını engelleme

- **Şu işlemler** için geçerlidir: Tüm İşlemler
- **İşlemler**- *
- **İşlem**- Süreç Sonlandırma
- **Dosyalar/Klasörler,** Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler- MsSense.exe, MsMpEng.exe, NisSrv.exe, svchost.exe*, services.exe, csrss.exe, smss.exe, wininit.exe ve daha birçok örnek.
- **Saldırı Surface Azaltma kuralları**- ASR kuralları bu senaryoları desteklemez, çünkü bunlar yerleşik güvenlik Windows koruma ile korunurlar.
- **Diğer önerilen özellikler:** ELAM (Erken Başlatma Kötü Amaçlı Yazılımdan Koruma), PPL (Koruma Süreci Işığı), PPL Kötü Amaçlı Yazılımdan Koruma Işığı ve System Guard.

### <a name="block-specific-launch-process-attempt"></a>Belirli başlatma İşlem Denemelerini engelle

- **Özel İşlemler** için geçerlidir
- **İşlemler**- "Sürecinizi Adla"
- **Operation**- Process Execution
- **Dosya/Klasörler, Kayıt Defteri Anahtarları/Değerleri,** İşlemler, Hizmetler ve diğer tor.exe, bittorrent.exe, cmd.exe, powershell.exe ve daha birçok örnek
- **Saldırı Surface Azaltma kuralları** - Genel, ASR kuralları Uygulama yöneticisi olarak işlevecek şekilde tasarlanmadı.
- **Diğer önerilen özellikler**: Kullanıcıların belirli işlemleri veya programları başlatmasını önlemek için, Uygulama Denetimi'Windows Defender kullanılması önerilir. Uç Nokta Dosyası için Microsoft Defender ve Sertifika göstergeleri, Bir Olay Yanıtı senaryosunda kullanılabilir (uygulama denetim mekanizması olarak görülmeleri gerekir).

### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>İzin yapılandırmalarında yetkisiz Microsoft Defender Virüsten Koruma engelleme

- **Şu işlemler** için geçerlidir: Tüm İşlemler
- **İşlemler**- *
- **Operation**- Registry Modifications
- **Dosya/Klasörler,** Kayıt Defteri Anahtarları/Değerleri, İşlemler, Hizmetler- HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiCcaware, HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowGerTimeMonitoring, buna örnek.
- **Saldırı Surface Azaltma kuralları**- ASR kuralları bu senaryoları kapsıyor çünkü bunlar yerleşik Uç Nokta koruma için Microsoft Defender'ın bir parçası.
- Diğer **önerilen** özellikler- Tamper Protection (kabul et, Intune'dan yönetilme), DisableAntiVirus, DisableAntiVirware, DisableGertimeMonitoring, DisableOnAccessProtection, DisableBehaviorMonitoring ve DisableIOAVProtection kayıt defteri anahtarlarında (ve daha birçok) yetkisiz değişiklikleri önlemek.

Ayrıca bkz.

- [Saldırı yüzeyini azaltma hakkında SSS](attack-surface-reduction-faq.yml)
- [Saldırı yüzeyini azaltma kurallarını etkinleştirin](enable-attack-surface-reduction.md)
- [Saldırı yüzeyini azaltma kurallarını değerlendirin](evaluate-attack-surface-reduction.md)
