---
title: Uç Nokta için Microsoft Defender Windows önceki sürümlerini ekleme
description: algılayıcı verilerini Uç Nokta için Microsoft Defender algılayıcıya gönderebilmeleri için Windows cihazlarının önceki sürümlerini ekleme desteği
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
ms.openlocfilehash: 0cd1e0aa999200814639f24401bf019774ca1d43
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825222"
---
# <a name="onboard-previous-versions-of-windows"></a>Windows'un önceki sürümlerini ekleyin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platform**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Uç Nokta için Defender desteği alt düzey işletim sistemlerini içerecek şekilde genişleterek desteklenen Windows sürümlerinde gelişmiş saldırı algılama ve araştırma özellikleri sağlar.

Uç Nokta için Defender'a alt düzey Windows istemci uç noktalarını eklemek için şunları yapmanız gerekir:

- [System Center Endpoint Protection istemcilerini yapılandırma ve güncelleştirme](#configure-and-update-system-center-endpoint-protection-clients)
- [Algılayıcı verilerini raporlamak için Microsoft Monitoring Agent (MMA) yükleme ve yapılandırma](#install-and-configure-microsoft-monitoring-agent-mma)

Windows Server 2008 R2 SP1 için [Bulut için Microsoft Defender ekleme](#onboard-windows-servers-through-microsoft-defender-for-cloud) seçeneğiniz vardır.

> [!NOTE]
> Microsoft Monitoring Agent aracılığıyla bir Windows sunucusu eklemek için düğüm başına Uç Nokta için Defender tek başına sunucu lisansı gereklidir (Seçenek 1). Alternatif olarak, Bulut için Microsoft Defender aracılığıyla bir Windows sunucusu eklemek için düğüm başına sunucular için Microsoft Defender lisansı gerekir (Seçenek 2), bkz. [Bulut için Microsoft Defender'de kullanılabilen desteklenen özellikler](/azure/security-center/security-center-services).

> [!TIP]
> Cihazı ekledikten sonra, hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Defender uç noktasında algılama testi çalıştırma](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>System Center Endpoint Protection istemcilerini yapılandırma ve güncelleştirme

> [!IMPORTANT]
> Bu adım yalnızca kuruluşunuz System Center Endpoint Protection (SCEP) kullanıyorsa gereklidir.

Uç Nokta için Defender, kötü amaçlı yazılım algılamalarına görünürlük sağlamak ve kötü amaçlı olabilecek dosyaları veya şüpheli kötü amaçlı yazılımları yasaklayarak kuruluşunuzdaki bir saldırının yayılmasını durdurmak için System Center Endpoint Protection ile tümleşir.

Bu tümleştirmeyi etkinleştirmek için aşağıdaki adımlar gereklidir:

- [Endpoint Protection istemcileri için Ocak 2017 kötü amaçlı yazılımdan koruma platformu güncelleştirmesini](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie) yükleme
- **SCEP** istemcisi Bulut Koruma Hizmeti üyeliğini Gelişmiş ayarına yapılandırma
- Ağınızı Microsoft Defender Virüsten Koruma buluta bağlantılara izin verecek şekilde yapılandırın. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma ağ bağlantılarını yapılandırma ve doğrulama](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Microsoft Monitoring Agent (MMA) yükleme ve yapılandırma

### <a name="before-you-begin"></a>Başlamadan önce

En düşük sistem gereksinimlerini doğrulamak için aşağıdaki ayrıntıları gözden geçirin:

- [Şubat 2018 aylık güncelleştirme paketini](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598) yükleme

  > [!NOTE]
  > Yalnızca Windows Server 2008 R2, Windows 7 SP1 Enterprise ve Windows 7 SP1 Pro için geçerlidir.

- [Müşteri deneyimi ve tanılama telemetrisi için Güncelleştirme'yi](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) yükleme

- [.NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (veya üzeri) veya [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework) yükleme

    > [!NOTE]
    > Yalnızca Windows Server 2008 R2, Windows 7 SP1 Enterprise ve Windows 7 SP1 Pro için geçerlidir.
    >
    > Yukarıdaki yüklemeyi .NET Framework 4.0.x'i yüklemeyin.
    >
    > .NET 4.5 yüklemesi, yüklemeden sonra bilgisayarınızı yeniden başlatmanızı gerektirebilir.

- Azure Log Analytics aracısı minimum sistem gereksinimlerini karşılayın. Daha fazla bilgi için bkz. [Log Analytics ile ortamınızdaki bilgisayarlardan veri toplama](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Yükleme adımları

1. Aracı kurulum dosyasını indirin: [Windows 64 bit aracı](https://go.microsoft.com/fwlink/?LinkId=828603) veya [Windows 32 bit aracı](https://go.microsoft.com/fwlink/?LinkId=828604).

    >[!NOTE]
    >[MMA aracısı tarafından SHA-1 desteğinin kullanımdan kaldırılması nedeniyle MMA aracısının](/azure/azure-monitor/agents/agent-windows#sha-2-code-signing-support-requirement) 10.20.18029 veya daha yeni bir sürümü olması gerekir.
    

2. Çalışma alanı kimliğini alın:
   - Uç Nokta için Defender gezinti bölmesinde **Ayarlar > Cihaz yönetimi > Ekleme'yi** seçin
   - İşletim sistemini seçin
   - Çalışma alanı kimliğini ve çalışma alanı anahtarını kopyalama

3. Çalışma Alanı Kimliği ve Çalışma Alanı anahtarını kullanarak aracıyı yüklemek için aşağıdaki yükleme yöntemlerinden birini seçin:
    - [Kurulumu kullanarak aracıyı el ile yükleyin](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      **Aracı Kurulum Seçenekleri** sayfasında **aracıyı Azure Log Analytics'e (OMS) Bağlan'ı** seçin

    - [Aracıyı komut satırını kullanarak yükleyin](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Aracıyı bir betik kullanarak yapılandırın](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > [ABD Kamu müşterisiyseniz](gov.md), "Azure Bulutu" altında kurulum sihirbazını kullanıyorsanız veya komut satırı veya betik kullanıyorsanız "Azure ABD Kamu" seçeneğini belirlemeniz gerekir. "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" parametresini 1 olarak ayarlayın.

4. İnternet'e bağlanmak için ara sunucu kullanıyorsanız Ara sunucu ve İnternet bağlantı ayarlarını yapılandırma bölümüne bakın.

Tamamlandıktan sonra, bir saat içinde portalda eklenen uç noktaları görmeniz gerekir.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Ara sunucu ve internet bağlantısı ayarlarını yapılandırın
Sunucularınızın Uç Nokta için Defender ile iletişim kurmak için ara sunucu kullanması gerekiyorsa, MMA'yı ara sunucuyu kullanacak şekilde yapılandırmak için aşağıdaki yöntemlerden birini kullanın:

- [MMA'yi ara sunucu kullanacak şekilde yapılandırma](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Windows tüm bağlantılar için ara sunucu kullanacak şekilde yapılandırma](configure-proxy-internet.md)

Bir ara sunucu veya güvenlik duvarı kullanılıyorsa, sunucuların tüm Uç Nokta için Microsoft Defender hizmet URL'lerine doğrudan ve SSL kesme olmadan erişebildiğinden emin olun. Daha fazla bilgi için bkz [. Uç Nokta için Defender hizmet URL'lerine erişimi etkinleştirme](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). SSL kesme özelliğinin kullanılması, sistemin Uç Nokta için Defender hizmetiyle iletişim kurmasını engeller.

Tamamlandıktan sonra, bir saat içinde portalda eklenen Windows sunucuları görmeniz gerekir.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Bulut için Microsoft Defender aracılığıyla Windows sunucuları ekleme

1. Microsoft 365 Defender gezinti bölmesinde **Ayarlar** >  **Cihaz** **yönetimiOnboarding'i** >  seçin.

2. İşletim sistemi olarak **Windows Server 2008 R2 SP1'i** seçin.

3. **Bulut için Microsoft Defender'de Sunucuları Ekle'ye** tıklayın.

4. [Bulut için Microsoft Defender ile Uç Nokta için Microsoft Defender'daki](/azure/security-center/security-center-wdatp) ekleme yönergelerini izleyin ve Azure ARC kullanıyorsanız, [Uç Nokta için Microsoft Defender etkinleştirme başlığı altında yer alan ekleme yönergelerini izleyin tümleştirmesi](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Ekleme adımlarını tamamladıktan sonra, [System Center Endpoint Protection istemcilerini yapılandırmanız ve güncelleştirmeniz](#configure-and-update-system-center-endpoint-protection-clients) gerekir.

> [!NOTE]
>
> - Sunucuların beklendiği gibi çalışması için Microsoft Defender aracılığıyla ekleme için, sunucunun Microsoft Monitoring Agent (MMA) ayarları içinde yapılandırılmış uygun bir çalışma alanı ve anahtara sahip olması gerekir.
> - Yapılandırıldıktan sonra makineye uygun bulut yönetim paketi dağıtılır ve algılayıcı işlemi (MsSenseS.exe) dağıtılır ve başlatılır.
> - Sunucu bir OMS Ağ Geçidi sunucusunu ara sunucu olarak kullanacak şekilde yapılandırılmışsa da bu gereklidir.



## <a name="verify-onboarding"></a>Eklemeyi doğrulama

Microsoft Defender AV ve Uç Nokta için Microsoft Defender çalıştığını doğrulayın. 

> [!NOTE]
> Microsoft Defender AV'nin çalıştırılması gerekli değildir, ancak önerilir. Birincil uç nokta koruma çözümü başka bir virüsten koruma satıcısı ürünüyse Defender Virüsten Koruma'yı Pasif modda çalıştırabilirsiniz. Pasif modun açık olduğunu yalnızca Uç Nokta için Microsoft Defender algılayıcının (SENSE) çalıştığını doğruladıktan sonra onaylayabilirsiniz. 

1. Microsoft Defender AV'nin yüklü olduğunu doğrulamak için aşağıdaki komutu çalıştırın:

   ```sc.exe query Windefend```

    Sonuç 'Belirtilen hizmet yüklü bir hizmet olarak yok' ise Microsoft Defender AV'yi yüklemeniz gerekir. Daha fazla bilgi için bkz. [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-windows.md).

    Windows sunucularınızdaki Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için grup ilkesi kullanma hakkında bilgi için bkz. [Yapılandırmak ve yönetmek için grup ilkesi ayarlarını kullanma Microsoft Defender Virüsten Koruma](use-group-policy-microsoft-defender-antivirus.md).


2. Uç Nokta için Microsoft Defender çalıştığını doğrulamak için aşağıdaki komutu çalıştırın:

    ```sc.exe query sense```
    
    Sonuç, çalıştığını göstermelidir. Ekleme ile ilgili sorunlarla karşılaşırsanız bkz. [Ekleme sorunlarını giderme](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma
Sunucunun Uç Nokta hizmeti için Defender'a rapor ettiğini doğrulamak için [Yeni eklenen bir cihazda algılama testi çalıştırma](run-detection-test.md) bölümündeki adımları izleyin.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Yönetim çözümü olmadan uç noktaları ekleme 

### <a name="using-group-policy"></a>grup ilkesi kullanma

**1. Adım: Uç noktanız için karşılık gelen udpat'ı indirin.**

1. c:\windows\sysvol\domain\scripts konumuna gidin (Etki alanı denetleyicilerinden birinde değişiklik denetimi gerekebilir.)
1. MMA adlı bir klasör oluşturun.
1. Aşağıdakileri indirin ve MMA klasörüne yerleştirin:
   
    - Müşteri deneyimi ve tanılama telemetrisi için güncelleştirme:
      - [Windows Server 2008 R2 x64 için](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Windows Server 2008 R2 SP1 için aşağıdaki güncelleştirmeler de gereklidir:

    Şubat 2018 Aylık Dağıtımı - KB4074598 (Windows Server 2008 R2)

    [Microsoft Update Kataloğu](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Windows Server 2008 R2 x64 güncelleştirmelerini indirme
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Windows Server 2008 R2 x64 için](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > Bu makalede x64 tabanlı sunucular kullandığınız varsayılır (MMA Aracısı .exe x64 Yeni SHA-2 uyumlu sürümü).


**2. Adım: DeployMMA.cmd dosya adı oluşturma (not defterini kullanarak)** Aşağıdaki satırları cmd dosyasına ekleyin. ÇALIŞMA ALANI KİmLİKİne ve ANAHTARA ihtiyacınız olduğunu unutmayın.

Aşağıdaki komut bir örnektir. Aşağıdaki değerleri değiştirin:
- KB - Eklediğiniz uç noktayla ilgili geçerli KB'yi kullanın
- Çalışma Alanı Kimliği ve ANAHTAR - Kimliğinizi ve anahtarınızı kullanın


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

Özellikle "Uç Nokta için Microsoft Defender Ekleme" gibi cihazları eklemeye yönelik yeni bir grup ilkesi oluşturun.

- "c:\windows\MMA" adlı bir grup ilkesi Klasörü oluşturun

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="Klasörlerin konumu" lightbox="images/grppolicyconfig1.png":::

    **Bu işlem, GPO'yu uygulayan her sunucuya MMA adlı yeni bir klasör ekler ve c:\windows içinde depolanır. Bu, MMA yükleme dosyalarını, önkoşulları ve yükleme betiğini içerir.**

- Net logon'da depolanan dosyaların her biri için bir grup ilkesi Dosyaları tercihi oluşturun.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="Grup ilkesi - 1" lightbox="images/grppolicyconfig2.png":::

Dosyaları ETKİALANI\NETLOGON\MMA\dosyaadı'ndan C:\windows\MMA\dosyaadı konumuna kopyalar; **bu nedenle yükleme dosyaları sunucuda yereldir**:

:::image type="content" source="images/deploymma.png" alt-text="Dağıtım mma cmd özellikleri" lightbox="images/deploymma.png":::

İşlemi yineleyin ancak COMMON sekmesinde öğe düzeyi hedeflemesi oluşturun; böylece dosya yalnızca kapsamda uygun platform/İşletim sistemi sürümüne kopyalanır:

:::image type="content" source="images/targeteditor.png" alt-text="Hedef düzenleyici" lightbox="images/targeteditor.png":::

Windows Server 2008 R2 için aşağıdakiler gerekir (ve yalnızca aşağı kopyalanır):
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Bu işlem tamamlandıktan sonra bir başlangıç betiği ilkesi oluşturmanız gerekir:

:::image type="content" source="images/startupprops.png" alt-text="Başlangıç özellikleri" lightbox="images/startupprops.png":::

Burada çalıştırılacak dosyanın adı c:\windows\MMA\DeployMMA.cmd şeklindedir.
Sunucu, başlatma işleminin bir parçası olarak yeniden başlatıldıktan sonra, Çalışma Alanı Kimliği ve Anahtarı ayarlanırken müşteri deneyimi ve tanılama telemetrisi için güncelleştirme KB'sini yükler ve ardından MMA Aracısı'nı yükler ve sunucu eklenir.

Tüm sunucuları yeniden başlatmak istemiyorsanız deployMMA.cmd dosyasını çalıştırmak için **de hemen bir görev** kullanabilirsiniz.

Bu işlem iki aşamada yapılabilir. İlk olarak **GPO'da dosyaları ve klasörü** oluşturun - GPO'nun uygulandığından ve tüm sunucularda yükleme dosyalarının bulunduğundan emin olmak için sisteme zaman verin. Ardından, hemen görevi ekleyin. Bu, yeniden başlatma gerektirmeden aynı sonucu elde eder.

Betik bir çıkış yöntemine sahip olduğundan ve MMA yüklüyse yeniden çalıştırılmıyorsa, aynı sonucu elde etmek için günlük zamanlanmış bir görev de kullanabilirsiniz. Configuration Manager uyumluluk ilkesine benzer şekilde, MMA'nın mevcut olduğundan emin olmak için her gün kontrol eder.

:::image type="content" source="images/schtask.png" alt-text="görev zamanlama" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="Yeni görev özellikleri" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="Mma indirme özelliklerini dağıtma" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="Görev zamanlayıcı" lightbox="images/tasksch.png":::

Özellikle Server 2008 R2 civarında sunucu ekleme belgelerinde belirtildiği gibi lütfen aşağıya bakın: Windows Server 2008 R2 SP1 için aşağıdaki gereksinimleri karşıladığınızdan emin olun:

- [Şubat 2018 aylık güncelleştirme paketini](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598) yükleme
- [.NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (veya üzeri) veya [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework) yükleme

Windows Server 2008 R2'yi eklemeden önce lütfen KB'lerin mevcut olup olmadığını denetleyin. Bu işlem, sunucuları yönetmeye Configuration Manager sahip değilseniz tüm sunucuları eklemenizi sağlar.


## <a name="offboard-endpoints"></a>Uç noktaları çıkarma

Hizmetten Windows uç noktalarını çıkarmak için iki seçeneğiniz vardır:

- MMA aracısını kaldırma
- Uç Nokta için Defender çalışma alanı yapılandırmasını kaldırma

> [!NOTE]
> Çıkarma, Windows uç noktasının portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere uç noktadan veriler 6 aya kadar saklanır.

### <a name="uninstall-the-mma-agent"></a>MMA aracısını kaldırma

Windows uç noktasını çıkarmak için MMA aracısını kaldırabilir veya Uç Nokta için Defender çalışma alanınıza raporlamadan ayırabilirsiniz. Aracı kullanıma eklendikten sonra uç nokta artık uç nokta için Defender'a algılayıcı verileri göndermez.
Daha fazla bilgi için bkz. [Aracıyı devre dışı bırakmak için](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Uç Nokta için Defender çalışma alanı yapılandırmasını kaldırma

Aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Uç Nokta için Defender çalışma alanı yapılandırmasını MMA aracısından kaldırma
- Yapılandırmayı kaldırmak için bir PowerShell komutu çalıştırma

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Uç Nokta için Defender çalışma alanı yapılandırmasını MMA aracısından kaldırma

1. **Microsoft Monitoring Agent Özellikleri'nde** **Azure Log Analytics (OMS)** sekmesini seçin.

2. Uç Nokta için Defender çalışma alanını seçin ve **Kaldır'a** tıklayın.

    :::image type="content" source="images/atp-mma.png" alt-text="Çalışma Alanları bölmesi" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Yapılandırmayı kaldırmak için bir PowerShell komutu çalıştırma

1. Çalışma Alanı Kimliğinizi alın:

   1. Gezinti bölmesinde **Ayarlar** >  **Onboarding'i** seçin.

   1. İlgili işletim sistemini seçin ve Çalışma Alanı Kimliğinizi alın.

    
2. Yükseltilmiş bir PowerShell açın ve aşağıdaki komutu çalıştırın. Aldığınız Çalışma Alanı Kimliğini kullanın ve öğesini değiştirerek `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
