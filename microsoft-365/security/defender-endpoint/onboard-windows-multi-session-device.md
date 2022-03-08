---
title: Azure Windows Masaüstü'ne çok oturumlu cihazları ekleme
description: Azure Sanal Masaüstü'de birden çok oturum Windows ekleme hakkında bu makaledeki diğer yazıları okuyun.
keywords: Azure Sanal Masaüstü, WVD, microsoft defender, uç nokta, ekleme
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: d97326987af49b9bac44b3578884c72d756d5595
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324067"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Azure Windows Masaüstü'ne çok oturumlu cihazları ekleme

Okuma için 6 dakika

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows Sanal Masaüstü'de (AVD) çalışan birden çok oturum vardır

Uç Nokta için Microsoft Defender hem VDI hem de Azure Sanal Masaüstü oturumlarını izlemeyi destekler. Kuruluş gereksinimlerine bağlı olarak, çalışanlarının şirket verilerine ve uygulamalarına yönetimi olmayan bir cihazdan, uzak konumdan veya benzer bir senaryodan erişmelerine yardımcı olmak için VDI veya Azure Sanal Masaüstü oturumları gerçekleştirebilirsiniz. Uç Nokta için Microsoft Defender ile bu sanal makineleri anormal etkinlikler için izleyebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Kalıcı olmayan [VDI hakkında dikkate alınacak noktalara aşinalık sahibi olursunuz](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). [Azure Sanal Masaüstü](/azure/virtual-desktop/overview) kalıcı olmayan seçenekler sağlamasa da, yeni ana bilgisayar ve yeniden depolama makinelerini sağlamak için Windows altın rengi resim kullanmak için yollar sağlar. Bu da ortamdaki vola uygunluğu artırır ve dolayısıyla Uç Nokta için Microsoft Defender portalında oluşturulan ve bakımını yapan girdileri etkiler ve bu da güvenlik analistlerinin görünürlüğünü azalttı.

> [!NOTE]
> Ekleme yöntemi seçiminize bağlı olarak cihazlar, Uç nokta portalı için Microsoft Defender'da şu şekilde  görünebilir:
>
> - Her sanal masaüstü için tek giriş
> - Her sanal masaüstü için birden çok giriş

Microsoft, sanal masaüstü başına tek bir giriş olarak Azure Sanal Masaüstü'ne giriş önerilen bir uygulamadır. Bu, uç nokta için Microsoft Defender portalında inceleme deneyiminin, makine adını temel alan tek bir cihaz bağlamında olduğunu garanti eder. WVD ana bilgisayarlarını sık sık silebilir ve yeniden yer alan kuruluşlar, aynı makine için Uç nokta portalı Microsoft Defender'da birden çok nesne oluşturmasını engelley bir yandan da bu yöntemi kullanmayı kesinlikle göz önünde bulundurlar. Bu durum, olayları araştırırken karışıklığa yol açabilir. Test veya geçici olmayan ortamlar için farklı bir tercih seçebilirsiniz.

Microsoft, WVD altın resim görüntüsüne Uç nokta ekleme için Microsoft Defender'ı eklemeyi önertir. Bu şekilde, bu ekleme betiği hemen ilk önyüklemede çalıştırılmalıdır. WVD golden image'den sağlanan tüm WVD makinelerde ilk önyüklemede başlangıç betiği olarak yürütülür. Öte yandan, galeri resimlerinden birini değiştirmeden kullanıyorsanız, betiği paylaşılan bir konuma yer paylaşımlı bir konuma yer paylaşımlı olarak arayın ve yerel veya etki alanı grup ilkesinden arayın.

> [!NOTE]
> WVD altın resim üzerindeki VDI ekleme başlangıç betiği yerleşimi ve yapılandırması, bunu WVD başlatıldığında çalışan bir başlangıç betiği olarak yapılandırr. Gerçek WVD altın resmi ekleme önerilmez. Betiği çalıştırmak için kullanılan yöntem diğer bir önemli noktadır. Makinede oturum almaya uygun olan makineyle hizmete cihaz ekleme arasındaki sürenin azaltılması için, başlangıç/hazırlama işleminin mümkün olduğunca erken bir sürede çalışması gerekir. 1. ve 2. senaryoların altındaki senaryolar bunu hesaba alır.

### <a name="scenarios"></a>Senaryolar

WVD ana bilgisayar makinesi eklemenin çeşitli yolları vardır:

- Başlatma sırasında betiği altın resimde (veya paylaşılan bir konumdan) çalıştırın.
- Betiği çalıştırmak için bir yönetim aracı kullanın.
- Bulut [için Microsoft Defender ile Tümleştirme Aracılığıyla](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*1. Senaryo: Yerel grup ilkesi kullanma*

Bu senaryo, betiğin altın bir görüntüye yerleştirilmesini gerektirir ve başlatma işleminin başlarında çalıştırmak için yerel grup ilkesi kullanır.

Kalıcı olmayan sanal masaüstü [altyapısı (VDI) cihazlarını ekleme yönergelerini kullanın](configure-endpoints-vdi.md).

Her cihaz için tek bir giriş yönergelerini izleyin.

#### <a name="scenario-2-using-domain-group-policy"></a>*Senaryo 2: Etki alanı grup ilkesi kullanma*

Bu senaryo merkezi olarak bulunan bir betik kullanır ve bunu etki alanı tabanlı bir grup ilkesi kullanarak çalıştırır. Ayrıca betiği altın görüntüye yer ve aynı şekilde çalıştırabilirsiniz.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Windows 365 Defender portaldan WindowsDefenderATPOnboardingPackage.zip dosya indirme

1. VDI yapılandırma paketi dosya .zip açma (WindowsDefenderATPOnboardingPackage.zip)

    1. Mobil Microsoft 365 Defender bölmesinde  Uç Noktaları **Ekleme'yi Ayarlar** \> \> **(Cihaz Yönetimi'nin** **altında) öğesini seçin**.
    1. İşletim Windows 10 veya Windows 11 olarak seçin.
    1. Dağıtım yöntemi **alanında** , kalıcı olmayan uç noktalar için VDI ekleme betikleri'ne seçin.
    1. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. .zip dosyasının içeriğini cihaz tarafından erişilebilen, salt okunur bir konuma ayıklar. **optionalParamsPolicy** adlı bir klasörünüz ve **WindowsDefenderATPOnboardingScript.cmd** ve **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Sanal makine başlatıldığında betiği çalıştırmak için Grup İlkesi yönetim konsolunu kullanın

1. Grup İlkesi Yönetim Konsolu'nu (GPMC) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi Yönetim Düzenleyicisi'nde Bilgisayar yapılandırması **Tercihleri Denetim** \> **masası** \> **ayarlarına gidin**.

3. Zamanlanmış **görevler'e sağ** tıklayın, **Yeni'ye** tıklayın ve sonra da **Acil Görev (** En Az 7 Windows tıklayın.

4. Açılan Görev penceresinde Genel **sekmesine** gidin. Güvenlik **seçenekleri'nin altında** Kullanıcı **veya Grubu Değiştir'e tıklayın** ve SYSTEM yazın. Adları **Denetimi'ne ve** sonra da Tamam'a tıklayın. NT AUTHORITY\SYSTEM, görevin çalıştıracak olduğu kullanıcı hesabı olarak görünür.

5. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

6. Eylemler sekmesine **gidin** ve Yeni'yi **tıklatın**. Eylem alanında **Program başlat'ın** seçili olduğundan emin olun. Şunları girin:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Ardından **Tamam'ı** seçin ve tüm açık GPMC pencerelerini kapatın.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Senaryo 3: Yönetim araçlarını kullanarak ekleme*

Bir yönetim aracı kullanarak makinelerinizi yönetmeyi planlıyorsanız, başka cihazlarla birlikte cihazları Microsoft Endpoint Configuration Manager.

Daha fazla bilgi için bkz. [Configuration Manager Windows cihazları ekleme](configure-endpoints-sccm.md).

> [!WARNING]
> Saldırı yüzeyini azaltma kuralları başvurusunu kullanmayı planlıyorsanız[, "](attack-surface-reduction-rules-reference.md)[PSExec ve WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands) komutlarından kaynaklanan süreç oluşturmalarını engelle" kuralının kullanılmama gerektiğini, çünkü bu kuralın Site Yönetimi ile Microsoft Endpoint Configuration Manager. Kural, Configuration Manager istemcisinin düzgün çalışması için kullandığı WMI komutlarını engeller.

> [!TIP]
> Cihazı işe seçtikten sonra, cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta cihazı için Microsoft Defender'da algılama testi çalıştırma](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Altın resminizi inşa ediyorken makinelerinizi etiketleme

Eklemenizin bir parçası olarak, Microsoft Güvenlik Merkezi'nde WVD makinelerini daha kolay ayırt etmek için bir makine etiketi ayarlamayı düşünebilirsiniz. Daha fazla bilgi için bkz [. Kayıt defteri anahtarı değerini ayarerek cihaz etiketleri ekleme](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

Altın resminizi inşa etmek için başlangıç koruma ayarlarını da yapılandırmanız gerekebilir. Daha fazla bilgi için diğer [önerilen yapılandırma ayarları'ne bakın](configure-endpoints-gp.md#other-recommended-configuration-settings).

Ayrıca, FSlogix kullanıcı profillerini kullanıyorsanız, aşağıdaki dosyaları her zaman açık korumanın dışında tutabilirsiniz:

**Dosyaları Dışla:**

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**İşlemleri Dışla:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Lisans gereksinimleri

Lisanslama notu: Windows Enterprise çoklu oturum kullanırken, gereksinimlerinize bağlı olarak tüm kullanıcıların Uç Nokta için Microsoft Defender (kullanıcı başına), Windows Enterprise E5, Microsoft 365 Güvenliği veya Güvenlik lisansları aracılığıyla lisanslandır Microsoft 365 E5 ya da sanal makinenin Bulut için Microsoft Defender aracılığıyla lisansını edin.
Uç Nokta için Microsoft Defender Lisans gereksinimleri bağlantısında bulunabilir: [Lisans gereksinimleri](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Bilinen sorunlar ve sınırlamalar

Birden Microsoft Edge oturumda web filtrelemesi yalnızca Windows 10 için destek sağlar.

#### <a name="related-links"></a>İlgili Bağlantılar

[PowerShell aracılığıyla Uç Nokta için Defender'da dışlamalar ekleme](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
