---
title: Microsoft Defender Virüsten Koruma Sanal Masaüstü Altyapısı kılavuzu
description: Koruma ve performans Microsoft Defender Virüsten Koruma en iyi dengeyi oluşturmak için sanal masaüstü ortamında mobil cihaz dağıtımı yapmayı öğrenin.
keywords: vdi, hyper-v, vm, sanal makine, windows defender, virüsten koruma, av, sanal masaüstü, rds, uzak masaüstü
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/11/2022
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 9ff523e55efa872002e53f74a631def4c65b9929
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015245"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Sanal masaüstü Microsoft Defender Virüsten Koruma (VDI) ortamında dağıtım kılavuzu

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Standart şirket içi veya donanım yapılandırmalarına ek olarak, Microsoft Defender Virüsten Koruma'i uzak masaüstü (RDS) veya kalıcı olmayan bir sanal masaüstü altyapısı (VDI) ortamında da kullanabilirsiniz.

Hizmetler ve VDI desteği Microsoft Uzak Masaüstü daha fazla bilgi için bkz. [Azure Sanal Masaüstü Belgeleri](/azure/virtual-desktop).

Azure tabanlı sanal makineler için bkz. [Bulut için Microsoft Defender Endpoint Protection'da kullanıcı yükleme](/azure/security-center/security-center-install-endpoint-protection).

VDA'larda çalışan VDY'lerde güncelleştirmeleri kolayca dağıtabilme özelliğiyle, makinelerde güncelleştirmeleri hızla ve kolayca nasıl edinebilirsinize odaklanmak için bu kılavuzu kısaltıldı. Güncelleştirmeler ana bilgisayar sunucusunda bileşen bitlerine genişletilir ve açık olduğunda doğrudan sanal makineye indirilirken, artık altın rengi resimleri düzenli aralıklarla oluşturmanız ve kapatmanız gerekmeyecektir.

Bu kılavuzda, sanal bilgisayarlarınızı en iyi koruma ve performans için yapılandırma ve aşağıdakiler de dahil:

- [Güvenlik zekası güncelleştirmeleri için ayrılmış bir VDI dosya paylaşımı ayarlama](#set-up-a-dedicated-vdi-file-share)
- [Zamanlanmış taramaları rastgele rastgeleleştirme](#randomize-scheduled-scans)
- [Hızlı taramaları kullanma](#use-quick-scans)
- [Bildirimleri engelleme](#prevent-notifications)
- [Her güncelleştirmeden sonra taramaların devamsını devre dışı bırak](#disable-scans-after-an-update)
- [Bir süredir çevrimdışı olan güncel olmayan makineleri veya makineleri tarama](#scan-vms-that-have-been-offline)
- [Dışlama uygula](#exclusions)

Ayrıca, yeni paylaşılan güvenlik zekası güncelleştirme özelliğine bakarak Microsoft Defender Virüsten Koruma'de, virüsten koruma performansını kendi VDI'niz üzerinde test etmeyle ilgili performans testi ve yol gösterici bilgileri de olan teknik teknik bilgileri [Sanal Masaüstü Altyapısı'e](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf) indirebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

> [!IMPORTANT]
> VDI Windows Server 2012 veya Windows Server 2016'te barındırılabilir ama Windows'in önceki sürümlerinde kullanılamayan artırılmış koruma teknolojileri ve özellikler nedeniyle, sanal makineler (SANAL MAKINELERI) en az 1607 Windows 10'te çalışıyor Windows.
>
> Microsoft Defender AV'nin Windows 10 Insider Preview, derleme 18323 (ve sonraki) derlemelerde sanal makinelerde çalışma yolunun performans ve özellik geliştirmeleri vardır. Insider Preview derlemesini kullanıyorsanız, bu kılavuzda tanımlaymız: Belirtilmezse, en iyi koruma ve performans için gereken en düşük sürüm 1607'Windows 10 sürümüdür.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Adanmış bir VDI dosya paylaşımı ayarlama

Windows 10 sürüm 1903'te indirilen güvenlik zekası güncelleştirmelerinin ana makineye boşalt boşaltılmış olan paylaşılan güvenlik zekası özelliğini kullanarak önceki CPU, disk ve bellek kaynaklarını tek tek makinelere kaydetmeyi sağlayan paylaşılan güvenlik zekası özelliğini kullandık. Bu özellik backported olarak alındı ve artık 1703 Windows 10 ve üzeri sürümlerde çalışıyor. Bu özelliği bir Grup İlkesi veya PowerShell ile ayarlayın.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Paylaşılan güvenlik zekası özelliğini etkinleştirmek için Grup İlkesi kullanma:

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim Konsolu'nu açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. Security Intelligence **Güncelleştirmeleri'Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin**.

5. **VDI istemcileri için güvenlik zekası konumunu tanımla'ya çift** tıklayın ve ardından Seçeneği Etkin olarak **ayarlayın**. Alan otomatik olarak görüntülenir.

6. Enter `\\<sharedlocation\>\wdav-update` (bu değerle ilgili yardım için bkz. [İndirme ve paketi açma](#download-and-unpackage-the-latest-updates)).

7. **Tamam**'a tıklayın.

8. GPO'nun, test etmek istediğiniz sanal sanal ağlarda dağıtın.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Paylaşılan güvenlik zekası özelliğini etkinleştirmek için PowerShell kullanma

Özelliği etkinleştirmek için aşağıdaki cmdlet'i kullanın. Daha sonra, bunu da normalde PowerShell tabanlı yapılandırma ilkelerini sanal bilgisayarlara iter gibi itmelisiniz:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

İndir [ve paketten](#download-and-unpackage-the-latest-updates) \<shared location\> çıkar bölümüne bakın.

## <a name="download-and-unpackage-the-latest-updates"></a>En son güncelleştirmeleri indirme ve paketten çıkarma

Artık yeni güncelleştirmeleri indirmeye ve yüklemeye başlatabilirsiniz. Aşağıda sizin için örnek bir PowerShell betiği oluşturduk. Bu betik, yeni güncelleştirmeleri indirmenin ve vm'lerinize hazır hale almanın en kolay yoludır. Ardından betiği, zamanlanmış bir görev kullanarak yönetim makinesi üzerinde belirli bir zamanda çalıştıracak şekilde ayarlasanız (veya Azure, Intune veya SCCM'de PowerShell betiklerini kullanmayı biliyorsanız, bu betikleri de kullanabilirsiniz).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd $vdmpath & c: & mpam-fe.exe /x"
```

Zamanlanmış bir görevi günde bir kez çalıştıracak şekilde ayarlanıyor, böylece paket her indirildikten ve paketten çıkarıldıktan sonra SANAL'lar yeni güncelleştirmeyi alır.
Günde bir kez başlamanızı öneririz, ancak etkisini anlamak için sıklığı artırmayı veya azaltmayı denemeniz gerekir.

Güvenlik zekası paketleri normalde her üç ile dört saatte bir yayımlanır. Dört saatten kısa bir sıklık ayarlamanın hiçbir yararı olmaz çünkü yönetim makinenizin ağ yükünü artıracaktır.

Ayrıca, vm'ler adına güncelleştirmeleri bir aralıkta getirmek ve bunları tüketim için dosya paylaşımına getirmek için tek sunucu veya makinenizi de kurabilirsiniz.
Bu durum, cihazların güncelleştirmeleri allarını almak için paylaşıma ve NTFS izinlerine sahip olduğu zaman paylaşıma erişim iznine sahip olabilir.

Bunu yapmak için:
 1. Bir SMB/CIFS dosya paylaşımı oluşturun. 
 
 2. Aşağıdaki paylaşım izinleriyle bir dosya paylaşımı oluşturmak için aşağıdaki örneği kullanın.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Kimliği Doğrulanmış Kullanıcılar:Okundu **: için bir NTFS izni eklendi**. 

    Örneğin, dosya paylaşımı:

    \\\fileserver.fqdn\mdatp$\wdav-update

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>PowerShell betiği çalıştırmak için zamanlanmış görev ayarlama

1. Yönetim makinesine görev Başlat menüsü Zamanlayıcı **yazın**. Görev açın ve yan **panelde Görev oluştur...** öğesini seçin.

2. Adı Güvenlik zekası **paketi aç olarak girin**. Tetikleyici **sekmesine gidin** . Yeni **...'yi seçin.** \> **Günlük olarak** ve Tamam'ı **seçin**.

3. Eylemler sekmesine **gidin**. **Yeni'yi seçin...** **Program/****Betik alanına PowerShell** girin. Bağımsız `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` değişken **ekle alanına girin** . **Tamam**'ı seçin.

4. 2010'da isterseniz ek ayarları yapılandırabilirsiniz.

5. **Zamanlanmış görevi** kaydetmek için Tamam'ı seçin.

Görevi sağ tıklatıp Çalıştır'ı tıklatarak güncelleştirmeyi el ile **başlatabilirsiniz**.

### <a name="download-and-unpackage-manually"></a>El ile indirme ve paketten çıkarma

Her şeyi el ile yapmak isterseniz, betiğin davranışını çoğaltmak için şunları yapabilirsiniz:

1. Sistem kökünde, zeka güncelleştirmelerini depolamak `wdav_update` için adlandırılan yeni bir klasör oluşturun, örneğin klasörü oluşturun `c:\wdav_update`.

2. Klasör altında, *GUID wdav_update* gibi bir alt klasör oluşturma `{00000000-0000-0000-0000-000000000000}`

   İşte bir örnek: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > Betikte, GUID'nin son 12 basamadı dosyanın indirildikten yıl, ay, gün ve saat olacak şekilde ayarlanır; böylece her sefer yeni bir klasör oluşturulur. Bunu değiştirebilirsiniz, böylece dosya her sefer aynı klasöre indirilir.

3. Guid klasörüne bir güvenlik zekası [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  paketi indirin. Dosyanın adı gerekir `mpam-fe.exe`.

4. Bir cmd istemi penceresi açın ve oluşturduğunuz GUID klasörüne gidin. Dosyaları **ayıklamak için /X** ayıklama komutunu kullanın, örneğin `mpam-fe.exe /X`.

   > [!NOTE]
   > Ayıklanan bir güncelleştirme paketiyle yeni bir GUID klasörü oluşturulduğunda veya var olan bir klasör yeni ayıklanan paketle her güncelleştirildiğinde, vmler güncelleştirilmiş paketi alır.

## <a name="randomize-scheduled-scans"></a>Zamanlanmış taramaları rastgele rastgeleleştirme

Zamanlanmış taramalar, gerçek zamanlı [koruma ve taramanın yanı sıra çalıştırın](configure-real-time-protection-microsoft-defender-antivirus.md).

Taramanın başlangıç zamanı hala zamanlanmış tarama ilkesine (**ScheduleDay**, **ScheduleTime** ve **ScheduleQuickScanTime) dayalıdır**. Rastgele başlatma, Microsoft Defender Virüsten Koruma tarama için ayarlanmış olan zaman penceresinden dört saatlik bir süre içinde her makinede bir tarama başlatmaya neden olur.

[Zamanlanmış taramalarda](scheduled-catch-up-scans-microsoft-defender-antivirus.md) kullanılabilen diğer yapılandırma seçeneklerini görmek için Taramaları zamanlama'ya bakın.

## <a name="use-quick-scans"></a>Hızlı taramaları kullanma

Zamanlanmış bir tarama sırasında gerçekleştirilecek tarama türünü belirtsiniz. Hızlı taramalar, kötü amaçlı yazılımın etkin olması gereken her yere bakacak şekilde tasarlanarak tercih edilen yaklaşımdır. Aşağıdaki yordamda, Grup İlkesi kullanılarak hızlı taramaların nasıl ayar kullanımı açık almaktadır.

1. Grup İlkesi Düzenleyicisi'nizin Yönetim şablonları ve  **Windows'Microsoft Defender Virüsten Koruma** \>  \> \> **gidin**.

2. **Zamanlanmış taramada kullanmak üzere tarama türünü belirtin'i** seçin ve ilke ayarını düzenleyin.

3. İlkeyi Etkin olarak **ayarlayın** ve **Seçenekler'in altında Hızlı**  **tarama'ya tıklayın**.

4. **Tamam**'ı seçin.

5. Grup İlkesi nesnenizi her zaman olduğu gibi dağıtın.

## <a name="prevent-notifications"></a>Bildirimleri engelleme

Bazen Microsoft Defender Virüsten Koruma oturumlarda bildirim gönderilmesine veya kalıcı olmasına neden olabilir. Bu sorunu en aza indirmek için kullanıcı arabirimini Microsoft Defender Virüsten Koruma kilitebilirsiniz. Aşağıdaki yordam, Grup İlkesi ile bildirimlerin nasıl gizlenmelerini açıklar.

1. Grup İlkesi Düzenleyicisi'nizin İstemci Arabirimi **Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **gidin**.

2. Tüm **bildirimlerin bastır öğesini seçin** ve ardından ilke ayarlarını düzenleyin.

3. İlkeyi Etkin olarak **ayarlayın** ve tamam'ı **seçin**.

4. Grup İlkesi nesnenizi her zaman olduğu gibi dağıtın.

Bildirimlerin bastırılması, tarama Microsoft Defender Virüsten Koruma düzeltme eylemleri gerçekleştirilmesi Windows 10 İşlem Merkezi'nde bildirimlerin 24.01.2013'te  gösterilene kadar göstermesini engelleme. Ancak güvenlik işlemleri ekipleri taramanın sonuçlarını Saldırı algılandığında ve durdurulurken "ilk erişim uyarısı" gibi uyarılar tetiklendi ve [Microsoft 365 Defender portalında görüldü](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Windows 10 11'de Windows Merkezini açmak için, aşağıdaki adımlardan birini uygulayın:
>
> - Görev çubuğunun sağ ucunda İşlem Merkezi simgesini seçin.
> - Logo tuşu Windows + A tuşlarına basın.
> - Dokunmatik ekranlı bir cihazda, ekranın sağ kenarından çekin.

## <a name="disable-scans-after-an-update"></a>Güncelleştirme sonrasında taramaları devre dışı bırakma

Güncelleştirme sonrasında taramayı devre dışı bırakmak, güncelleştirme aldıktan sonra taramanın devamsını engeller. Hızlı tarama da çalıştırdıysanız, temel görüntüyü oluştururken bu ayarı uygulayabilirsiniz. Bu şekilde, yeni güncelleştirilen VM'nin yeniden tarama gerçekleştirmesini önebilirsiniz (temel görüntüyü oluşturulduğunda zaten taramış olurken).

> [!IMPORTANT]
> Güncelleştirmeden sonra taramaları çalıştırmanız, sanal güncelleştirmeyi en son Güvenlik zekası güncelleştirmeleriyle korumanıza yardımcı olur. Bu seçeneği devre dışı bırakmak, sanal bilgisayarlarının koruma düzeyini azaltır ve yalnızca temel resmi oluştururken veya dağıtırken kullanılır.

1. Grup İlkesi Düzenleyicisi'nizin Güvenlik Zekası **Güncelleştirmeleri Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **gidin**.

2. Güvenlik **zekası güncelleştirmesi sonrasında taramayı aç'ı** seçin ve ilke ayarını düzenleyin.

3. İlkeyi Devre Dışı olarak **ayarlayın**.

4. **Tamam**'ı seçin.

5. Grup İlkesi nesnenizi her zaman olduğu gibi dağıtın.

Bu ilke, güncelleştirme sonrasında taramanın hemen çalışan bir durumla karşıltır.

## <a name="scan-vms-that-have-been-offline"></a>Çevrimdışı olan VM'leri tarama

1. Grup İlkesi Düzenleyicisi'nizin Sistem Bileşenleri **Windows Tarama'Microsoft Defender Virüsten Koruma** \>  \> **gidin**.

2. Hızlı **taramayı aç'ı seçin ve** ilke ayarını düzenleyin.

3. İlkeyi Etkin olarak **ayarlayın**.

4. **Tamam**'ı seçin.

5. Grup İlkesi Nesnenizi her zaman olduğu gibi dağıtın.

Bu ilke, VM birbirini takip eden iki veya daha fazla zamanlanmış taramayı kaçırdı ise taramayı güçler.

## <a name="enable-headless-ui-mode"></a>Başsız kullanıcı arabirimi modunu etkinleştirme

1. Grup İlkesi Düzenleyicisi'nizin İstemci Arabirimi **Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **gidin**.

2. **Başsız kullanıcı arabirimi modunu etkinleştir'i** seçin ve ilkeyi düzenleyin.

3. İlkeyi Etkin olarak **ayarlayın**.

4. **Tamam**'a tıklayın.

5. Grup İlkesi Nesnenizi her zaman olduğu gibi dağıtın.

Bu ilke tüm kullanıcı arabirimini Microsoft Defender Virüsten Koruma son kullanıcılardan gizler.

## <a name="exclusions"></a>Dışlamalar

Dışlamalar ihtiyaçlarınıza uyacak şekilde eklenebilir, kaldırılabilir veya özelleştirilebilir.

Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma sunucusunda dışlamaları yapılandırma Windows.](configure-exclusions-microsoft-defender-antivirus.md)

## <a name="additional-resources"></a>Ek kaynaklar

- [Teknik Community Blogu: Kalıcı Microsoft Defender Virüsten Koruma VDI makinelerini yapılandırma](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Uzak Masaüstü Hizmetleri ve VDI'de TechNet forumları](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask PowerShell betiği](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
