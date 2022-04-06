---
title: Windows'un önceki sürümlerini Uç Nokta için Microsoft Defender
description: Algılayıcı verilerini algılayıcı algılayıcısına Windows için desteklenen önceki Uç Nokta için Microsoft Defender cihazları ekleme
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8fc3f86aa15a9fe54a410c869eb84b2b1ff79872
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474519"
---
# <a name="onboard-previous-versions-of-windows"></a>Windows'un önceki sürümlerini ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformlar**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Uç Nokta için Defender, destek süresini daha düşük işletim sistemleri içerecek şekilde genişletmiş ve desteklenen yeni sürümlerde gelişmiş saldırı algılama ve Windows sunar.

Uç nokta için Defender'Windows istemci uç noktalarını eklemeye devam etmek için şunları gerekir:

- [İstemcileri yapılandırma System Center Endpoint Protection güncelleştirme](#configure-and-update-system-center-endpoint-protection-clients)
- [Algılayıcı verilerini rapor etmek Microsoft Monitoring Agent (MMA) yükleme ve yapılandırma](#install-and-configure-microsoft-monitoring-agent-mma)

Windows Server 2008 R2 SP1'de, sunucu ve sunucu [arasında ekleme Bulut için Microsoft Defender](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Microsoft Monitoring Agent üzerinden bir Windows sunucusu almak için, düğüm başına Uç nokta tek Microsoft Monitoring Agent Defender gereklidir. Alternatif olarak, Bulut için Microsoft Defender (Seçenek 2) üzerinden bir Windows sunucusu almak için düğüm başına bir Microsoft Defender sunucu lisansı gereklidir, bkz[. Bulut için Microsoft Defender](/azure/security-center/security-center-services).

> [!TIP]
> Cihazı işe başladıktan sonra, hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta için Defender'da algılama testi çalıştırma](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>İstemcileri yapılandırma System Center Endpoint Protection güncelleştirme

> [!IMPORTANT]
> Bu adım yalnızca, kuruluşta System Center Endpoint Protection (SCEP) kullanıyorsa gereklidir.

Uç nokta için Defender, System Center Endpoint Protection amaçlı yazılım algılamaları için görünürlük sağlamak ve kötü amaçlı olabilecek dosyaları veya şüpheli kötü amaçlı yazılımdan şüphelenilenleri yasaklama nedeniyle kuruluşta bir saldırının yayılmasını durdurmak amacıyla System Center Endpoint Protection ile tümleştirilmiştir.

Bu tümleştirmeyi etkinleştirmek için aşağıdaki adımlar gereklidir:

- Endpoint Protection [istemcileri için Ocak 2017 kötü amaçlı yazılımdan koruma platform güncelleştirmesini yükleme](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- SCEP istemcisi Bulut Koruma Hizmeti üyeliğini Gelişmiş **ayarına göre** yapılandırma
- Aynı buluta bağlantılara izin vermek için a Microsoft Defender Virüsten Koruma yapılandırabilirsiniz. Daha fazla bilgi için bkz[. Ağ bağlantılarını Microsoft Defender Virüsten Koruma ve doğrulama](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>MMA (MMA) Microsoft Monitoring Agent ve yapılandırma

### <a name="before-you-begin"></a>Başlamadan önce

En düşük sistem gereksinimlerini doğrulamak için aşağıdaki ayrıntıları gözden geçirme:

- Şubat [2018 aylık güncelleştirme toplaması yükleme](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Yalnızca Windows Server 2008 R2, Windows 7 SP1 Enterprise ve 7 SP1 Windows için Pro.

- Müşteri deneyimi [ve tanılama telemetrisi için Güncelleştirmeyi yükleme](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- [.NET framework 4.5 (veya sonraki](https://www.microsoft.com/download/details.aspx?id=30653) bir sürümü) veya [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework) yükleme

    > [!NOTE]
    > Yalnızca Windows Server 2008 R2, Windows 7 SP1 Enterprise ve 7 SP1 Windows için Pro.
    >
    > Yukarıdaki yüklemenin .NET Framework, yani 4.0.x'i yükleyemesiniz.
    >
    > .NET 4.5'in yüklenmesi, yüklemeden sonra bilgisayarınızı yeniden başlatmanızı gerekli olabilir.

- Azure Log Analytics aracısı en düşük sistem gereksinimlerini karşılar. Daha fazla bilgi için bkz [. Log Analytics ile ortamıınızdaki bilgisayarlardan veri toplama](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Yükleme adımları

1. Aracı kurulum dosyasını indirin: [Windows 64 bit aracısı veya](https://go.microsoft.com/fwlink/?LinkId=828603) [Windows 32 bit aracısı](https://go.microsoft.com/fwlink/?LinkId=828604).

2. Çalışma alanı kimliğini alın:
   - Uç nokta gezinti bölmesi için Defender'da Cihaz **yönetimi Ayarlar >'ı > seçin**
   - İşletim sistemini seçin
   - Çalışma alanı kimliğini ve çalışma alanı anahtarını kopyalama

3. Çalışma Alanı Kimliği ve Çalışma Alanı anahtarının kullanımı aracıyı yüklemek için aşağıdaki yükleme yöntemlerden birini seçin:
    - [Kurulumu kullanarak aracıyı el ile yükleyin](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      Aracı **Kurulum Seçenekleri sayfasında,** **Aracıyı Azure Bağlan (OMS)** seçme

    - [Komut çizgilerini kullanarak aracıyı yükleyin](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Aracıyı bir betik kullanarak yapılandır.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation)

   > [!NOTE]
   > ABD Kamu müşterisiysiniz [, "](gov.md)Azure Bulut" altında, kurulum sihirbazını kullanıyorsanız veya komut satırı ya da betik kullanıyorsanız "Azure US Government"ı seçmeniz gerekir- "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" parametresini 1 olarak ayarlayın.

4. İnternet'e bağlanmak için proxy kullanıyorsanız, Proxy ve İnternet bağlantısı ayarlarını yapılandırma bölümüne bakın.

Tamamlandığında, portalda bir saat içinde yerleşik uç noktaları görmelisiniz.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Ara sunucu ve İnternet bağlantısı ayarlarını yapılandırma
Sunucularınızı Uç Nokta için Defender ile iletişim kurmak üzere bir proxy kullanmaları gerekirse, MMA'yı ara sunucuyu kullanmak üzere yapılandırmak için aşağıdaki yöntemlerden birini kullanın:

- [MMA'yı ara sunucuyu kullanmak üzere yapılandırma](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Tüm Windows için proxy sunucusu kullanmak üzere yapılandırma](configure-proxy-internet.md)

Bir ara sunucu veya güvenlik duvarı kullanıyorsa, lütfen sunucuların tüm UÇ NOKTA IÇIN MICROSOFT DEFENDER hizmeti URL'lerine doğrudan ve SSL kesişme noktası olmadan erişe olduğundan emin olun. Daha fazla bilgi için bkz. [Uç nokta hizmeti URL'leri için Defender erişimini etkinleştirme](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). SSL kesişme noktası kullanımı, sistemin Uç nokta için Defender hizmetiyle iletişim kurmasını engellemektedir.

Tamamlandığında, portalda bir saat Windows yerleşik sunucu olduğunu görmelisiniz.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Windows aracılığıyla sunucu ekleme Bulut için Microsoft Defender

1. Gezinti bölmesinde Microsoft 365 Defender **Device managementOnboarding'Ayarlar** >  >  **seçin**.

2. İşletim **Windows olarak Windows Server 2008 R2 SP1'i** seçin.

3. Erişim **Araçlarında Sunucuları Ekle'Bulut için Microsoft Defender**.

4. [Uç Nokta için Microsoft Defender'da](/azure/security-center/security-center-wdatp) Bulut için Microsoft Defender yönergelerini izleyin ve Azure ARC kullanıyorsanız Bu özelliği etkinleştirme konusunda verilen [ekleme Uç Nokta için Microsoft Defender tümleştirmeyi sağlar](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Ekleme adımlarını tamamladıktan sonra, istemcilerini yapılandırmalı [ve System Center Endpoint Protection.](#configure-and-update-system-center-endpoint-protection-clients)

> [!NOTE]
>
> - Sunucuların beklendiği gibi çalışması için Microsoft Defender aracılığıyla ekleme için, sunucunun uygun bir çalışma alanı ve Microsoft Monitoring Agent MMA) ayarları içinde yapılandırılmış olması gerekir.
> - Yapılandırıldıktan sonra makineye uygun bulut yönetim paketi dağıtılır ve algılayıcı işlemi (MsSenseS.exe) dağıtılacak ve başlatılacaktır.
> - Bu ayrıca, sunucu bir OMS Ağ Geçidi sunucusunu ara sunucu olarak kullanmak üzere yapılandırılmışsa da gereklidir.



## <a name="verify-onboarding"></a>Ekleme doğrulama

Microsoft Defender AV ve Uç Nokta için Microsoft Defender çalıştığını doğrulayın. 

> [!NOTE]
> Microsoft Defender AV'nin kullanılması gerekmez, ancak bu sürümün kullanılması önerilir. Birincil uç nokta koruma çözümü başka bir virüsten koruma satıcısı ürünü ise, Defender Virüsten Koruma'ı Pasif modunda çalıştırabilirsiniz. Pasif modunun, yalnızca algılayıcı (SENSE) Uç Nokta için Microsoft Defender sonra çalıştığını doğrulayabilir. 

1. Microsoft Defender AV'nin yüklü olduğunu doğrulamak için aşağıdaki komutu çalıştırın:

   ```sc.exe query Windefend```

    Sonuç 'Belirtilen hizmet, yüklü bir hizmet olarak yok' ise Microsoft Defender AV'i yüklemeniz gerekir. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma'de Windows 10](microsoft-defender-antivirus-windows.md).

    Windows sunucularında grup ilkesi ve yönetmek için Microsoft Defender Virüsten Koruma'i kullanma hakkında bilgi için bkz. grup ilkesi ve yönetmek için grup ilkesi [ayarlarını kullanma Microsoft Defender Virüsten Koruma](use-group-policy-microsoft-defender-antivirus.md).


2. Postanın çalıştığını doğrulamak için Uç Nokta için Microsoft Defender çalıştırın:

    ```sc.exe query sense```
    
    Sonuç çalışıyor olduğunu göster olmalı. Eklemeyle ilgili sorunlarla karşılaşırsanız bkz. [Ekleme sorunlarını giderme](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma
Sunucunun Uç nokta hizmeti [için Defender'a](run-detection-test.md) rapor çalıştığını doğrulamak için yeni eklenen bir cihazda algılama testi çalıştırma'daki adımları izleyin.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Yönetim çözümüne sahip ekleme uç noktaları 

### <a name="using-group-policy"></a>grup ilkesi'i kullanma

**1. Adım: Uç noktanız için ilgili udpate'yi indirin.**

1. c:\windows\sysvol\domain\scripts klasörüne gidin (Etki alanı denetleyicilerinde değişiklik denetimi gerekli olabilir.)
1. MMA adlı bir klasör oluşturun.
1. Aşağıdakini indirin ve MMA klasörüne yazın:
   
    - Müşteri deneyimi ve tanılama telemetrisi güncelleştirmesi:
      - [Windows Server 2008 R2 x64 için](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Windows Server 2008 R2 SP1 için aşağıdaki güncelleştirmeler de gereklidir:

    Şubat 2018 Aylık Yükleme - KB4074598 (Windows Server 2008 R2)

    [Microsoft Update Kataloğu](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Windows Server 2008 R2 x64 için güncelleştirmeleri indirme
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Windows Server 2008 R2 x64 için](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > Bu makalede, x64 tabanlı sunucuları (MMA Aracısı .exe x64 New SHA-2 uyumlu sürümü) varsayabilirsiniz.


**2. Adım: DeployMMA.cmd (not defteri kullanarak) dosya adı oluşturma** Cmd dosyasına aşağıdaki satırları ekleyin. ÇALıŞMA ALANı Kimliği ve ANAHTAR'a ihtiyacınız olduğunu unutmayın.

Aşağıdaki komut bir örnektir. Aşağıdaki değerleri değiştirin:
- KB - Eklemede olduğunuz uç noktayla ilgili geçerli KB'yi kullanın
- Çalışma alanı kimliği ve ANAHTAR - Kimliğinizi ve anahtarınızı kullanın


```dos
@echo off 
cd "C:"
IF EXIST "C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe" ( 
exit
) ELSE (

wusa.exe C:\Windows\MMA\Windows6.1-KB3080149-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB4074598-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB3154518-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows8.1-KB3080149-x64.msu /quiet /norestart
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t: "C:\Windows\MMA"c:\windows\MMA\ setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1
OPINSIGHTS_WORKSPACE_ID="<your workspace ID>"
OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1
)

)
```





### <a name="group-policy-configuration"></a>grup ilkesi Yapılandırması

"Kullanıcı Ekleme" gibi ekleme cihazlarına özel olarak yeni Uç Nokta için Microsoft Defender oluşturun.

- "grup ilkesi "c:\windows\MMA" adlı bir Klasör oluşturun

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="Klasörler konumu" lightbox="images/grppolicyconfig1.png":::

    **Bu, GPO'nun uygulandığı her sunucuya MMA adı verilen yeni bir klasör ekler ve c:\windows konumunda depolanır. Bu, MMA için yükleme dosyalarını, önkoşulları ve yükleme betiği içerir.**

- Net oturum grup ilkesi depolanan dosyaların her biri için ayrı bir Dosya tercihi oluşturun.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="Grup ilkesi - 1" lightbox="images/grppolicyconfig2.png":::

DOSYALARı DOMAIN\NETLOGON\MMA\dosyaadı konumundan C:\windows\MMA\dosyaadı dizinine kopyalar; dolayısıyla yükleme dosyaları sunucuya **yerel olur**:

:::image type="content" source="images/deploymma.png" alt-text="mma cmd özelliklerini dağıtma" lightbox="images/deploymma.png":::

Bu işlemi yineler ancak ORTAK sekmesinde öğe düzeyi hedeflemeyi oluşturun; böylelikle dosya yalnızca kapsam olarak uygun platforma/İşletim sistemi sürümüne kopyalanır:

:::image type="content" source="images/targeteditor.png" alt-text="Hedef düzenleyici" lightbox="images/targeteditor.png":::

Windows Server 2008 R2 için aşağıdakilere ihtiyacınız vardır (ve yalnızca bu kopyalayıp aşağı doğru gelecektir):
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Bu yapıldıktan sonra, bir başlangıç betiği ilkesi oluşturmanız gerekir:

:::image type="content" source="images/startupprops.png" alt-text="Başlangıç özellikleri" lightbox="images/startupprops.png":::

Burada çalıştıracak dosyanın adı c:\windows\MMA\DeployMMA.cmd'dir.
Sunucu, başlatma işleminin bir parçası olarak yeniden başlatıldıktan sonra, Müşteri deneyimi ve tanılama telemetrisi için güncelleştirme KB'sini ve ardından Çalışma Alanı Kimliği ve Anahtar'ı ayarlarken MMA Aracısı'ı yüklenir ve sunucu eklenir.

Tüm sunucuları yeniden **başlatmak istemiyorsanız** , deployMMA.cmd'yi çalıştırmak için de acil bir görev kullanabilirsiniz.

Bu iki aşamada yapılabilir. Önce dosyaları **ve** GPO'da klasörü oluşturun - GPO'nun uygulandığını ve tüm sunucuların yükleme dosyalarına sahip olduğundan emin olmak için sistemle ilgili zaman seçin. Ardından, acil görevi ekleyin. Bu yeniden başlatmaya gerek kalmadan aynı sonucu elde ettiy.

Betik'in bir çıkış yöntemi vardır ve MMA yüklenirse yeniden çalıştırılamayacaktan, aynı sonucu elde etmek için günlük olarak zamanlanmış bir görev de kullanabilirsiniz. Uyumluluk ilkesine Configuration Manager, MMA'nın var olduğundan emin olmak için günlük olarak denetimler.

:::image type="content" source="images/schtask.png" alt-text="görev zamanlama" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="Yeni görev özellikleri" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="Mma indirme özelliklerini dağıtma" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="Görev zamanlayıcı" lightbox="images/tasksch.png":::

Özellikle Server 2008 R2'nin çevresinde bulunan Server için ekleme belgelerinde belirtildiği gibi, lütfen aşağıya bakın: Windows Server 2008 R2 SP1 için, aşağıdaki gereksinimleri karşılarsınız:

- Şubat [2018 aylık güncelleştirme toplaması yükleme](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- [.NET framework 4.5 (veya sonraki](https://www.microsoft.com/download/details.aspx?id=30653) bir sürümü) veya [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework) yükleme

Windows Server 2008 R2'yi eklemeden önce lütfen KB'lerin mevcut olup olduğunu kontrol edin. Bu işlem, Sunucu yönetimiyle ilgili bir yönetimi olmadığınız tüm sunucuları Configuration Manager sağlar.


## <a name="offboard-endpoints"></a>Offboard uç noktaları

Hizmetten en fazla Windows çıkarabilirsiniz:

- MMA aracısı kaldırma
- Uç nokta çalışma alanı yapılandırması için Defender'ı kaldırma

> [!NOTE]
> Offboarding, Windows uç noktasının algılayıcı verilerini portala göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere uç nokta üzerinden alınan veriler 6 ay süreyle korunur.

### <a name="uninstall-the-mma-agent"></a>MMA aracısı kaldırma

Windows uç noktasını çıkararak, MMA aracısı kaldırabilir veya uç nokta için Defender çalışma alanınıza bildirmeden çıkarabilirsiniz. Aracıyla çıkartan sonra, uç nokta artık Uç Nokta için Defender'a algılayıcı verileri göndermez.
Daha fazla bilgi için bkz [. Aracıyı devre dışı bırakmak için](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Uç nokta çalışma alanı yapılandırması için Defender'ı kaldırma

Aşağıdaki yöntemlerden birini kullanabilirsiniz:

- MMA aracıdan Uç nokta çalışma alanı yapılandırması için Defender'ı kaldırma
- Yapılandırmayı kaldırmak için PowerShell komutunu çalıştırma

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>MMA aracıdan Uç nokta çalışma alanı yapılandırması için Defender'ı kaldırma

1. Veri **Microsoft Monitoring Agent,Azure** **Günlük Analizi (OMS) sekmesini** seçin.

2. Uç nokta için Defender çalışma alanını seçin ve Kaldır'a **tıklayın**.

    :::image type="content" source="images/atp-mma.png" alt-text="Çalışma Alanları bölmesi" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Yapılandırmayı kaldırmak için PowerShell komutunu çalıştırma

1. Çalışma Alanı Kimliği'nizi alırsınız:

   1. Gezinti bölmesinde Gezinti **Bölmesi'Ayarlar** >  **seçin**.

   1. uygun işletim sistemini seçin ve Çalışma Alanı Kimliği'nizi seçin.

    
2. Yükseltilmiş bir PowerShell açın ve aşağıdaki komutu çalıştırın. Edinilen ve değiştirerek edinilen Çalışma Alanı Kimliğini kullanın `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
