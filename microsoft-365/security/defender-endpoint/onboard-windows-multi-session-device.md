---
title: Azure Sanal Masaüstü'nde çok oturumlu Windows cihazları ekleme
description: Azure Sanal Masaüstü'nde çok oturumlu cihazlar Windows ekleme hakkında bu makalede daha fazla bilgi edinin
keywords: Azure Sanal Masaüstü, AVD, microsoft defender, uç nokta, ekleme
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
ms.openlocfilehash: 7a093a3b50d7153c71eecb9707ff8ab0dbef0d20
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013298"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Azure Sanal Masaüstü'nde çok oturumlu Windows cihazları ekleme

Okunmasının 6 dakikası

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Sanal Masaüstü(AVD) üzerinde çalışan çok oturumlu Windows

Uç Nokta için Microsoft Defender hem VDI hem de Azure Sanal Masaüstü oturumlarını izlemeyi destekler. Kuruluşunuzun gereksinimlerine bağlı olarak, çalışanlarınızın yönetilmeyen bir cihazdan, uzak konumdan veya benzer bir senaryodan şirket verilerine ve uygulamalarına erişmesine yardımcı olmak için VDI veya Azure Sanal Masaüstü oturumları uygulamanız gerekebilir. Uç Nokta için Microsoft Defender ile bu sanal makineleri anormal etkinlik için izleyebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

[Kalıcı olmayan VDI ile ilgili dikkat edilmesi gerekenler](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1) hakkında bilgi sahibi olun. [Azure Sanal Masaüstü](/azure/virtual-desktop/overview) kalıcılık dışı seçenekler sağlamasa da, yeni konaklar sağlamak ve makineleri yeniden dağıtmak için kullanılabilecek altın Windows görüntüsü kullanmanın yollarını sağlar. Bu, ortamdaki volatiliteyi artırır ve böylece Uç Nokta için Microsoft Defender portalında oluşturulan ve tutulan girişleri etkileyerek güvenlik analistlerinizin görünürlüğünü azaltabilir.

> [!NOTE]
> Seçtiğiniz ekleme yöntemine bağlı olarak cihazlar Uç Nokta için Microsoft Defender portalda şu şekilde görünebilir:
>
> - Her sanal masaüstü için tek giriş
> - Her sanal masaüstü için birden çok giriş

Microsoft, Azure Sanal Masaüstü'nü sanal masaüstü başına tek bir giriş olarak eklemenizi önerir. Bu, Uç Nokta için Microsoft Defender portalındaki araştırma deneyiminin makine adına göre bir cihaz bağlamında olmasını sağlar. AVD konaklarını sık sık silen ve yeniden dağıtan kuruluşlar, aynı makine için birden çok nesnenin Uç Nokta için Microsoft Defender portalında oluşturulmasını önlediği için bu yöntemi kullanmayı kesinlikle göz önünde bulundurmalıdır. Bu, olayları araştırırken kafa karışıklığına neden olabilir. Test veya geçici olmayan ortamlar için farklı bir seçim yapmayı tercih edebilirsiniz.

Microsoft, AVD altın görüntüsüne Uç Nokta için Microsoft Defender ekleme betiğinin eklenmesini önerir. Bu şekilde, bu ekleme betiğinin ilk önyüklemede hemen çalıştığından emin olabilirsiniz. AVD altın görüntüsünden sağlanan tüm AVD makinelerinde ilk önyüklemede başlangıç betiği olarak yürütülür. Ancak galeri görüntülerinden birini değiştirmeden kullanıyorsanız, betiği paylaşılan bir konuma yerleştirin ve yerel veya etki alanı grup ilkesinden çağırın.

> [!NOTE]
> VDI ekleme başlangıç betiğinin AVD altın görüntüsüne yerleştirilmesi ve yapılandırması, onu AVD başlatıldığında çalışan bir başlangıç betiği olarak yapılandırıyor. Gerçek AVD altın görüntüsünü **eklemek önerilmez.** Dikkat edilmesi gereken bir diğer nokta da betiği çalıştırmak için kullanılan yöntemdir. Oturumları almak için kullanılabilen makine ile hizmete cihaz ekleme arasındaki süreyi azaltmak için başlatma/sağlama işleminin olabildiğince erken bir aşamasında çalıştırılmalıdır. Aşağıdaki 1 ve 2 senaryoları bunu dikkate alır.

### <a name="scenarios"></a>Senaryo

AVD konak makinesini eklemenin birkaç yolu vardır:

- Başlatma sırasında betiği altın görüntüde (veya paylaşılan bir konumdan) çalıştırın.
- Betiği çalıştırmak için bir yönetim aracı kullanın.
- [Bulut için Microsoft Defender ile Tümleştirme aracılığıyla](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Senaryo 1: Yerel grup ilkesini kullanma*

Bu senaryo, betiğin altın bir görüntüye yerleştirilmesini gerektirir ve önyükleme işleminin erken aşamalarında çalıştırmak için yerel grup ilkesini kullanır.

[Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme başlığındaki](configure-endpoints-vdi.md) yönergeleri kullanın.

Her cihaz için tek bir giriş için yönergeleri izleyin.

#### <a name="scenario-2-using-domain-group-policy"></a>*Senaryo 2: Etki alanı grup ilkesini kullanma*

Bu senaryo merkezi olarak bulunan bir betik kullanır ve bunu etki alanı tabanlı bir grup ilkesi kullanarak çalıştırır. Ayrıca betiği altın görüntüye yerleştirebilir ve aynı şekilde çalıştırabilirsiniz.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Windows 365 Defender portalından WindowsDefenderATPOnboardingPackage.zip dosyasını indirme

1. VDI yapılandırma paketini .zip dosyasını açın (WindowsDefenderATPOnboardingPackage.zip)

    1. Microsoft 365 Defender portalı  gezinti bölmesinde **uç noktaları** \> ekleme **(Cihaz Yönetimi** altında) **Ayarlar**\> seçin.
    1. İşletim sistemi olarak Windows 10 veya Windows 11 seçin.
    1. **Dağıtım yöntemi** alanında, kalıcı olmayan uç noktalar için VDI ekleme betikleri'ni seçin.
    1. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

2. .zip dosyasının içeriğini, cihaz tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. **OptionalParamsPolicy** adlı bir klasörünüz ve **WindowsDefenderATPOnboardingScript.cmd** ve **Onboard-NonPersistentMachine.ps1** dosyalarına sahip olmanız gerekir.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Sanal makine başlatıldığında betiği çalıştırmak için grup ilkesi yönetim konsolunu kullanma

1. grup ilkesi Yönetim Konsolu'nu (GPMC) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve **Düzenle'ye** tıklayın.

2. grup ilkesi Yönetim Düzenleyicisi'nde **Bilgisayar yapılandırması** \> **Tercihleri** \> **Denetim masası ayarları'na** gidin.

3. **Zamanlanmış görevler'e** sağ tıklayın, **Yeni'ye** tıklayın ve ardından **Anında Görev'e** (En az Windows 7) tıklayın.

4. Açılan Görev penceresinde **Genel** sekmesine gidin. **Güvenlik seçenekleri'nin** altında **Kullanıcıyı veya Grubu Değiştir'e** tıklayın ve SYSTEM yazın. **Adları Denetle'ye** ve ardından Tamam'a tıklayın. NT AUTHORITY\SYSTEM, görevin çalıştırılacağı kullanıcı hesabı olarak görünür.

5. **Kullanıcının oturum açıp açmadığını çalıştır'ı** seçin ve **En yüksek ayrıcalıklarla çalıştır** onay kutusunu işaretleyin.

6. **Eylemler** sekmesine gidin ve **Yeni'ye** tıklayın. Eylem alanında **Program başlat'ın** seçili olduğundan emin olun. Aşağıdakileri girin:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Ardından **Tamam'ı** seçin ve açık GPMC pencerelerini kapatın.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Senaryo 3: Yönetim araçlarını kullanarak ekleme*

Makinelerinizi bir yönetim aracı kullanarak yönetmeyi planlıyorsanız, cihazları Microsoft Endpoint Configuration Manager ile ekleyebilirsiniz.

Daha fazla bilgi için bkz. [Configuration Manager kullanarak Windows cihazları ekleme](configure-endpoints-sccm.md).

> [!WARNING]
> [Saldırı yüzeyi azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md) kullanmayı planlıyorsanız, "[PSExec ve WMI komutlarından kaynaklanan işlem oluşturmalarını engelle](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)" kuralının kullanılmaması gerektiğini unutmayın çünkü bu kural Microsoft Endpoint Configuration Manager aracılığıyla yönetimle uyumsuzdur. Kural, Configuration Manager istemcisinin düzgün çalışması için kullandığı WMI komutlarını engeller.

> [!TIP]
> Cihazı ekledikten sonra, cihazın hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Altın resminizi oluştururken makinelerinizi etiketleme

Ekleme işleminizin bir parçası olarak, Microsoft Güvenlik Merkezi'nde AVD makinelerini daha kolay ayırt etmek için bir makine etiketi ayarlamayı düşünebilirsiniz. Daha fazla bilgi için bkz. [Kayıt defteri anahtarı değeri ayarlayarak cihaz etiketleri ekleme](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

Altın görüntünüzü oluştururken ilk koruma ayarlarını da yapılandırmak isteyebilirsiniz. Daha fazla bilgi için bkz. [Önerilen diğer yapılandırma ayarları](configure-endpoints-gp.md#other-recommended-configuration-settings).

Ayrıca, FSlogix kullanıcı profillerini kullanıyorsanız, aşağıdaki dosyaları her zaman açık korumanın dışında tutmanızı öneririz:

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

**Dışlama İşlemleri:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Lisans gereksinimleri

Lisanslamayla ilgili not: Gereksinimlerinize bağlı olarak çok oturumlu Windows Enterprise kullanırken, tüm kullanıcıların Uç Nokta için Microsoft Defender (kullanıcı başına), Windows Enterprise E5 üzerinden lisansa sahip olmasını seçebilirsiniz Microsoft 365  Güvenlik veya Microsoft 365 E5 ya da VM'nin Bulut için Microsoft Defender aracılığıyla lisansa sahip olması.
Uç Nokta için Microsoft Defender için lisanslama gereksinimleri şu konumda bulunabilir: [Lisans gereksinimleri](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Bilinen sorunlar ve sınırlamalar

Çok oturumlu Windows 10 web filtrelemesi için yalnızca Microsoft Edge desteklenir.

#### <a name="related-links"></a>İlgili Bağlantılar

[PowerShell aracılığıyla Uç Nokta için Defender dışlamaları ekleme](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
