---
title: Microsoft Defender Virüsten Koruma Sanal Masaüstü Altyapısı dağıtım kılavuzu
description: Koruma ve performans arasında en iyi dengeyi sağlamak için sanal masaüstü ortamında Microsoft Defender Virüsten Koruma dağıtmayı öğrenin.
keywords: vdi, hyper-v, vm, sanal makine, windows defender, virüsten koruma, av, sanal masaüstü, rds, uzak masaüstü
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8cb3dcec3690ae3a4433bfffee53dc99842c0028
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872324"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Sanal Masaüstü Altyapısı (VDI) ortamında Microsoft Defender Virüsten Koruma için dağıtım klavuzu

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Standart şirket içi veya donanım yapılandırmalarına ek olarak, Microsoft Defender Virüsten Koruma uzak masaüstü (RDS) veya kalıcı olmayan sanal masaüstü altyapısı (VDI) ortamında da kullanabilirsiniz.

Microsoft Uzak Masaüstü Hizmetleri ve VDI desteği hakkında daha fazla bilgi için bkz. [Azure Sanal Masaüstü Belgeleri](/azure/virtual-desktop).

Azure tabanlı sanal makineler için bkz[. Bulut için Microsoft Defender'de Endpoint Protection yükleme](/azure/defender-for-cloud/endpoint-protection-recommendations-technical).

Güncelleştirmeleri VDI'lerde çalışan VM'lere kolayca dağıtabilme özelliği sayesinde, makinelerinizde güncelleştirmeleri hızlı ve kolay bir şekilde nasıl edinebileceğinize odaklanmak için bu kılavuzu kısaltdık. Güncelleştirmeler konak sunucusundaki bileşen bitlerine genişletildiğinden ve açıldığında doğrudan VM'ye indirildiğinden, artık düzenli aralıklarla altın renkli görüntüler oluşturmanız ve mühürlemeniz gerekmez.

Bu kılavuzda, aşağıdakiler de dahil olmak üzere VM'lerinizi en iyi koruma ve performans için yapılandırma işlemleri açıklanmaktadır:

- [Güvenlik bilgileri güncelleştirmeleri için ayrılmış bir VDI dosya paylaşımı ayarlama](#set-up-a-dedicated-vdi-file-share)
- [Zamanlanmış taramaları rastgele belirleme](#randomize-scheduled-scans)
- [Hızlı taramaları kullanma](#use-quick-scans)
- [Bildirimleri engelleme](#prevent-notifications)
- [Taramaların her güncelleştirmeden sonra gerçekleşmesini devre dışı bırakma](#disable-scans-after-an-update)
- [Bir süredir çevrimdışı olan eski makineleri veya makineleri tarama](#scan-vms-that-have-been-offline)
- [Dışlamaları uygulama](#exclusions)

Ayrıca, performans testi ve virüsten koruma performansını kendi VDI'nizde nasıl test edebileceğinize ilişkin yönergelerle birlikte yeni paylaşılan güvenlik zekası güncelleştirme özelliğine bakan [teknik inceleme Microsoft Defender Virüsten Koruma](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf) Sanal Masaüstü Altyapısı'a indirebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

> [!IMPORTANT]
> VDI Windows Server 2012 veya Windows Server 2016 üzerinde barındırılsa da, Windows önceki sürümlerinde kullanılamayan artan koruma teknolojileri ve özellikleri nedeniyle sanal makinelerin (VM) en az 1607 Windows 10 çalışıyor olması gerekir.
>
> Microsoft Defender AV'nin Windows 10 Insider Preview, derleme 18323 (ve üzeri) içinde sanal makinelerde çalışma yönteminde performans ve özellik iyileştirmeleri vardır. Insider Preview derlemesi kullanmanız gerekiyorsa bu kılavuzda bunu belirleyeceğiz; belirtilmezse, en iyi koruma ve performans için gereken en düşük sürüm 1607 Windows 10.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Ayrılmış bir VDI dosya paylaşımı ayarlama

Windows 10, sürüm 1903'te, indirilen güvenlik zekası güncelleştirmelerinin paketten çıkarılma işlemini bir konak makineye boşaltan ve böylece önceki CPU, disk ve bellek kaynaklarını tek tek makinelere kaydeden paylaşılan güvenlik zekası özelliğini kullanıma sunduk. Bu özellik geri aktarılmıştır ve artık Windows 10 sürüm 1703 ve üzeri sürümlerde çalışır. Bu özelliği bir grup ilkesi veya PowerShell ile ayarlayabilirsiniz.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Paylaşılan güvenlik bilgileri özelliğini etkinleştirmek için grup ilkesi kullanın:

1. grup ilkesi yönetim bilgisayarınızda grup ilkesi Yönetim Konsolu'nu açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve ardından **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** tıklatın.

4. **Güvenlik Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

5. **VDI istemcileri için güvenlik zekası konumunu tanımla'ya** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Otomatik olarak bir alan görüntülenir.

6. Girin `\\<sharedlocation\>\wdav-update` (bu değerle ilgili yardım için bkz [. İndirme ve paketi açma](#download-and-unpackage-the-latest-updates)).

7. **Tamam**'a tıklayın.

8. GPO'yi test etmek istediğiniz VM'lere dağıtın.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Paylaşılan güvenlik zekası özelliğini etkinleştirmek için PowerShell kullanma

Özelliği etkinleştirmek için aşağıdaki cmdlet'i kullanın. Daha sonra bunu göndermeniz gerekir çünkü normalde PowerShell tabanlı yapılandırma ilkelerini VM'lere gönderebilirsiniz:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

ne \<shared location\> olacağını öğrenmek için [İndirme ve paketi açma](#download-and-unpackage-the-latest-updates) bölümüne bakın.

## <a name="download-and-unpackage-the-latest-updates"></a>En son güncelleştirmeleri indirme ve paketten çıkarma

Artık yeni güncelleştirmeleri indirmeye ve yüklemeye başlayabilirsiniz. Aşağıda sizin için örnek bir PowerShell betiği oluşturduk. Bu betik, yeni güncelleştirmeleri indirmenin ve vm'leriniz için hazır hale getirmenin en kolay yoludur. Ardından, zamanlanmış bir görev kullanarak betiği yönetim makinesinde belirli bir zamanda çalışacak şekilde ayarlamanız gerekir (veya Azure, Intune veya SCCM'de PowerShell betiklerini kullanmayı biliyorsanız, bu betikleri de kullanabilirsiniz).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd /d $vdmpath & mpam-fe.exe /x"
```

Zamanlanmış bir görevi günde bir kez çalışacak şekilde ayarlayabilirsiniz, böylece paket indirildiğinde ve paketten her açıldığında VM'ler yeni güncelleştirmeyi alır.
Günde bir kez ile başlamanızı öneririz, ancak etkiyi anlamak için sıklığı artırma veya azaltma denemeleri yapmalısınız.

Güvenlik bilgileri paketleri genellikle her üç-dört saatte bir yayımlanır. Bir sıklığın dört saatten kısa ayarlanması önerilmiyor çünkü bu, yönetim makinenizdeki ağ ek yükünü hiçbir fayda sağlamadan artıracaktır.

Ayrıca tek sunucunuzu veya makinenizi vm'ler adına belirli bir aralıkta güncelleştirmeleri getirecek ve bunları kullanım için dosya paylaşımına yerleştirecek şekilde ayarlayabilirsiniz.
Bu, cihazların güncelleştirmeleri alabilmesi için paylaşıma okuma erişimi için paylaşıma ve NTFS izinlerine sahip olması durumunda mümkündür.

Bunu yapmak için:
 1. SMB/CIFS dosya paylaşımı oluşturun. 
 
 2. Aşağıdaki paylaşım izinlerine sahip bir dosya paylaşımı oluşturmak için aşağıdaki örneği kullanın.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > **Kimliği Doğrulanmış Kullanıcılar:Okuma:** için bir NTFS izni eklenir. 

    Bu örnekte dosya paylaşımı şu şekildedir:

    \\\fileserver.fqdn\mdatp$\wdav-update

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>PowerShell betiğini çalıştırmak için zamanlanmış görev ayarlama

1. Yönetim makinesinde Başlat menüsü açın ve **Görev Zamanlayıcı** yazın. Bunu açın ve yan panelde **Görev oluştur...** öğesini seçin.

2. Adı **Güvenlik bilgileri paketten çıkarıcı** olarak girin. **Tetikleyici** sekmesine gidin. **Yeni... öğesini seçin.** \> **Günlük'e** gidin ve **Tamam'ı** seçin.

3. **Eylemler** sekmesine gidin. **Yeni... öğesini seçin.** **Program/Betik** alanına **PowerShell** girin. **Bağımsız değişken ekle** alanına girin`-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1`. **Tamam**'ı seçin.

4. İsterseniz ek ayarları yapılandırmayı seçebilirsiniz.

5. Zamanlanmış görevi kaydetmek için **Tamam'ı** seçin.

Göreve sağ tıklayıp **Çalıştır'a** tıklayarak güncelleştirmeyi el ile başlatabilirsiniz.

### <a name="download-and-unpackage-manually"></a>El ile indirme ve paketlemeyi açma

Her şeyi el ile yapmayı tercih ederseniz betiğin davranışını çoğaltmak için yapmanız gerekenler şunlardır:

1. Sistem kökünde akıllı güncelleştirmeleri depolamak için adlı `wdav_update` yeni bir klasör oluşturun, örneğin klasörünü `c:\wdav_update`oluşturun.

2. *wdav_update* altında GUID adıyla alt klasör oluşturma, örneğin`{00000000-0000-0000-0000-000000000000}`

   İşte bir örnek: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > Betikte GUID'nin son 12 basamağını dosyanın indirildiği yıl, ay, gün ve saat olacak şekilde ayarlıyoruz, böylece her seferinde yeni bir klasör oluşturulur. Dosyayı her seferinde aynı klasöre indirecek şekilde bunu değiştirebilirsiniz.

3. adresinden [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  GUID klasörüne bir güvenlik zekası paketi indirin. Dosya olarak adlandırılmalıdır `mpam-fe.exe`.

4. Bir cmd istemi penceresi açın ve oluşturduğunuz GUID klasörüne gidin. Dosyaları ayıklamak için **/X** ayıklama komutunu kullanın, örneğin `mpam-fe.exe /X`.

   > [!NOTE]
   > Vm'ler, ayıklanmış bir güncelleştirme paketiyle yeni bir GUID klasörü oluşturulduğunda veya mevcut bir klasör yeni ayıklanmış paketle güncelleştirildiğinde güncelleştirilmiş paketi alır.

## <a name="randomize-scheduled-scans"></a>Zamanlanmış taramaları rastgele belirleme

Zamanlanmış taramalar [, gerçek zamanlı koruma ve taramaya](configure-real-time-protection-microsoft-defender-antivirus.md) ek olarak çalışır.

Taramanın başlangıç zamanı hala zamanlanmış tarama ilkesini (**ScheduleDay, ScheduleTime** ve **ScheduleQuickScanTime**) temel alır.  Rastgele belirleme, Microsoft Defender Virüsten Koruma zamanlanan tarama için ayarlanan süreden itibaren dört saatlik bir süre içinde her makinede tarama başlatmasına neden olur.

Bkz [. Zamanlanmış taramalar](scheduled-catch-up-scans-microsoft-defender-antivirus.md) için kullanılabilen diğer yapılandırma seçenekleri için taramaları zamanlama.

## <a name="use-quick-scans"></a>Hızlı taramaları kullanma

Zamanlanmış tarama sırasında gerçekleştirilecek tarama türünü belirtebilirsiniz. Hızlı taramalar, kötü amaçlı yazılımların etkin olması için bulunması gereken tüm yerlere bakmak üzere tasarlandıklarından tercih edilen yaklaşımdır. Aşağıdaki yordamda grup ilkesi kullanarak hızlı taramaların nasıl ayarlanacağı açıklanmaktadır.

1. grup ilkesi Düzenleyicinizde, **Tarama** Microsoft Defender Virüsten Koruma Yönetim **şablonları** \> **Windows bileşenleri'ne** \>  \> gidin.

2. **Zamanlanmış tarama için kullanılacak tarama türünü belirtin'i** seçin ve ilke ayarını düzenleyin.

3. İlkeyi **Etkin** olarak ayarlayın ve **Seçenekler'in** altında  **Hızlı tarama'yı** seçin.

4. **Tamam**'ı seçin.

5. grup ilkesi nesnenizi her zamanki gibi dağıtın.

## <a name="prevent-notifications"></a>Bildirimleri engelleme

Bazen Microsoft Defender Virüsten Koruma bildirimleri birden çok oturuma gönderilebilir veya kalıcı hale gelebilir. Bu sorunu en aza indirmek için Microsoft Defender Virüsten Koruma kullanıcı arabirimini kilitleyebilirsiniz. Aşağıdaki yordamda, grup ilkesi bildirimlerin nasıl gizlendiği açıklanır.

1. grup ilkesi Düzenleyicinizde **İstemci Arabirimi** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> gidin.

2. **Tüm bildirimleri gizle'yi** seçin ve ilke ayarlarını düzenleyin.

3. İlkeyi **Etkin** olarak ayarlayın ve **ardından Tamam'ı** seçin.

4. grup ilkesi nesnenizi her zamanki gibi dağıtın.

Bildirimlerin gizlenmesi, taramalar yapıldığında veya düzeltme eylemleri gerçekleştirildiğinde Microsoft Defender Virüsten Koruma bildirimlerin Windows 10 İşlem Merkezi'nde gösterilmesini önler. Ancak, güvenlik operasyonları ekibiniz saldırı algılanıp durdurulurken taramanın sonuçlarını görür; "İlk erişim uyarısı" gibi uyarılar tetiklenir ve [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) görüntülenir.

> [!TIP]
> İşlem Merkezi'ni Windows 10 veya Windows 11 açmak için aşağıdaki adımlardan birini uygulayın:
>
> - Görev çubuğunun sağ ucunda İşlem Merkezi simgesini seçin.
> - Windows logo tuşu düğmesi + A tuşlarına basın.
> - Dokunmatik ekranlı bir cihazda, ekranın sağ kenarından içeri doğru çekin.

## <a name="disable-scans-after-an-update"></a>Güncelleştirmeden sonra taramaları devre dışı bırakma

Güncelleştirmeden sonra taramanın devre dışı bırakılması, bir güncelleştirme alındıktan sonra taramanın oluşmasını engeller. Ayrıca hızlı bir tarama çalıştırdıysanız, temel görüntüyü oluştururken bu ayarı uygulayabilirsiniz. Bu şekilde, yeni güncelleştirilen VM'nin yeniden tarama gerçekleştirmesini engelleyebilirsiniz (temel görüntüyü oluştururken zaten taradığınız gibi).

> [!IMPORTANT]
> Güncelleştirmeden sonra taramaların çalıştırılması, VM'lerinizin en son Güvenlik bilgileri güncelleştirmeleriyle korunmasına yardımcı olur. Bu seçeneğin devre dışı bırakılması VM'lerinizin koruma düzeyini azaltır ve yalnızca temel görüntüyü ilk oluştururken veya dağıtırken kullanılmalıdır.

1. grup ilkesi Düzenleyicinizde **Güvenlik Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> gidin.

2. **Güvenlik bilgileri güncelleştirmesinin ardından taramayı aç'ı** seçin ve ilke ayarını düzenleyin.

3. İlkeyi **Devre Dışı** olarak ayarlayın.

4. **Tamam**'ı seçin.

5. grup ilkesi nesnenizi her zamanki gibi dağıtın.

Bu ilke, bir güncelleştirmeden hemen sonra taramanın çalışmasını engeller.

## <a name="scan-vms-that-have-been-offline"></a>Çevrimdışı olan VM'leri tarama

1. grup ilkesi Düzenleyicinizde **Tarama** Microsoft Defender Virüsten Koruma **Windows** \> **bileşenleri'ne** \> gidin.

2. **Yakalama hızlı taramasını aç'ı** seçin ve ilke ayarını düzenleyin.

3. İlkeyi **Etkin** olarak ayarlayın.

4. **Tamam**'ı seçin.

5. grup ilkesi Nesnenizi genellikle yaptığınız gibi dağıtın.

Vm ardışık olarak zamanlanmış iki veya daha fazla taramayı kaçırdıysa, bu ilke bir taramayı zorlar.

## <a name="enable-headless-ui-mode"></a>Başsız kullanıcı arabirimi modunu etkinleştirme

1. grup ilkesi Düzenleyicinizde **İstemci Arabirimi** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> gidin.

2. **Başsız kullanıcı arabirimi modunu etkinleştir'i** seçin ve ilkeyi düzenleyin.

3. İlkeyi **Etkin** olarak ayarlayın.

4. **Tamam**'a tıklayın.

5. grup ilkesi Nesnenizi genellikle yaptığınız gibi dağıtın.

Bu ilke, Microsoft Defender Virüsten Koruma kullanıcı arabiriminin tamamını kuruluşunuzdaki son kullanıcılardan gizler.

## <a name="exclusions"></a>Dışlamalar

Dışlamalar gereksinimlerinize uyacak şekilde eklenebilir, kaldırılabilir veya özelleştirilebilir.

Daha fazla bilgi için bkz[. Windows Server'da Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma](configure-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="additional-resources"></a>Ek kaynaklar

- [Teknik Community Blogu: Kalıcı olmayan VDI makineleri için Microsoft Defender Virüsten Koruma yapılandırma](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Uzak Masaüstü Hizmetleri ve VDI'de TechNet forumları](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask PowerShell betiği](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
