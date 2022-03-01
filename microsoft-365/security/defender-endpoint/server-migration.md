---
title: Uç Nokta için Microsoft Defender'ın yeni sürümü için sunucu geçiş senaryoları
description: Önceki MMA tabanlı çözümden Uç nokta birleşik çözüm paketi için geçerli Defender'a sunucularınızı geçirmeyle ilgili genel bir bakış için bu makaleyi okuyun.
keywords: sunucu, sunucu, 2012r2, 2016, sunucu geçişi, cihaz yönetimi, Uç nokta sunucuları için Microsoft Defender'ı yapılandırma, Uç nokta sunucuları için Microsoft Defender'ı ekleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1a78d99650015aa0da92e35787a164b5c5a07b71
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014076"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Önceki, Uç nokta çözümü için MMA tabanlı Microsoft Defender'dan sunucu geçişi senaryoları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Windows Server 2012 R2
- Windows Server 2016
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Yükleme veya Microsoft Defender Virüsten Koruma devam etmeden önce, Windows Server 2016 her zaman güncelleştirmelerin tam olarak güncelleştiril olduğundan emin olun. EDR Windows Algılayıcı bileşenine yönelik düzenli ürün geliştirmeleri ve düzeltmeler almak için [KB5005292 Güncelleştirmesini kb5005292'in](https://go.microsoft.com/fwlink/?linkid=2168277) uygulandığını veya onaylandıktan emin olun. Buna ek olarak, koruma bileşenlerini güncel tutmak için güncelleştirmeleri yönetme [Microsoft Defender Virüsten Koruma temelleri uygulamanız gerekir](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Bu yönergeler, Windows Server 2012 R2 ve Windows Server 2016 için Uç Nokta için Microsoft Defender'ın yeni birleşik çözüm ve yükleyici paketi için Windows Server 2012 geçerlidir. Bu makale, öncekinden geçerli çözümüne kadar çeşitli olası geçiş senaryoları için üst düzey yönergeler içerir. Bu üst düzey adımlar, ortamınıza uygun dağıtım ve yapılandırma araçlarına yönelik yönergeler olarak tasarlanmıştır.

> [!NOTE]
> Microsoft Defender for Endpoint yüklü işletim sistemi yükseltmeleri desteklenmiyor. Yükseltme işlemiyle devam etmeden önce lütfen çıkar'ı kaldırın.

> [!NOTE]
> Önizleme sırasında, otomatik Microsoft Endpoint Configuration Manager gerçekleştirmek için tam otomasyon ve tümleştirme, MECM'nin sonraki bir sürümüyle kullanılabilir hale gelecektir. En son düzeltme toplaması ile 2107 sürümüne kadar, Endpoint Protection düğümünü yapılandırma için kullanabileceğiniz gibi, Grup İlkesi, PowerShell, Microsoft Endpoint Manager ekleme veya yerel yapılandırma da kullanabilirsiniz. Buna ek olarak, el ile yükseltme adımlarını otomatik Microsoft Endpoint Configuration Manager için Microsoft Endpoint Configuration Manager yöntemlerinde, aşağıda açıklanan yöntemlerden de kullanabilirsiniz.


## <a name="installer-script"></a>Yükleyici betiği

Bulut için Microsoft Defender Microsoft Endpoint Configuration Manager veya Yükseltmeyi gerçekleştirmek için henüz kullanılabilir durumda değilken yükseltmeleri kolaylaştırmak için, bu yükseltme [betiği kullanabilirsiniz](https://github.com/microsoft/mdefordownlevelserver). Aşağıdaki gerekli adımları otomatikleştirmeye yardımcı olabilir:

1. Uç Nokta için Microsoft Defender'ın OMS çalışma alanını kaldırın (İsteğE BAĞLı).
2. Yüklü System Center Endpoint Protection istemcisini kaldırın.
3. Gerekirse, önkoşulları Windows Server 2012 (R2) [indirip](configure-server-endpoints.md#prerequisites) yükleyin.
4. Uç Nokta için Microsoft Defender'ı yükleyin.
5. Kullanıcı grubundan indirilen **Grup İlkesi ile kullanmak üzere** ekleme [be Microsoft 365 Defender](https://security.microsoft.com).

Betiği kullanmak için, yükleme ve ekleme paketlerini de yerleştirerek bir yükleme dizinine indirin (bkz. [Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).

ÖRNEK: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager senaryolarını geçirme 

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-including-system-center-endpoint-protection-scep-and-are-running-the-microsoft-monitoring-agent-mma-based-sensor-you-want-to-upgrade-to-the-microsoft-defender-for-endpoint-unified-solution-preview"></a>Şu anda Microsoft Endpoint Configuration Manager System Center Endpoint Protection (SCEP) dahil olmak üzere sunucularınızı yönetmek için Microsoft Monitoring Agent (MMA) tabanlı algılayıcıyı çalıştırabilirsiniz. Uç nokta birleşik çözüm önizlemesi için Microsoft Defender'a yükseltmek **istiyor olun**.

>[!NOTE]
>2107 sürümünü Microsoft Endpoint Configuration Manager gerekir.


Geçiş adımları: 

1. Makineyi Tam Olarak Güncelleştir (Microsoft Defender Virüsten Koruma) Windows Server 2016.
2. Geçir taşınecek makineleri eklemek için üyelik kurallarıyla yeni bir koleksiyon oluşturun.
3. [Aşağıdaki görevleri gerçekleştirmek](/mem/configmgr/apps/deploy-use/create-applications) için bir uygulama oluşturun: 
   1. Uç nokta için Microsoft Defender'ın MMA çalışma alanı yapılandırmasını kaldırın. Bkz [. PowerShell kullanarak çalışma alanını kaldırma](/azure/azure-monitor/agents/agent-manage). Bu adım isteğe bağlıdır; önceki EDR algılayıcının daha yenisi etkin hale geldikten sonra çalışma durur (bunun birkaç saat sürebilir olduğunu unutmayın).
   2. SCEP'yi kaldırın.
   3. Uygun olduğunda [önkoşulları](configure-server-endpoints.md#prerequisites) yükleyin.
   4. Uç Nokta için Microsoft Defender'ı yükleyin ( [bkz. Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).
   5. Kullanıcı grubundan indirilen **Grup İlkesi ile kullanmak üzere** ekleme [be Microsoft 365 Defender](https://security.microsoft.com). 

   > [!TIP]
   > Yukarıdaki adımları [otomatikleştirmek için](server-migration.md#installer-script) uygulamanın bir parçası olarak yükleyici betiği kullanabilirsiniz.
4. Uygulamayı yeni koleksiyona dağıtın.
5. Koleksiyona kendi ilkeleri oluşturma ve/Endpoint Protection (var olan) ilkeleri attayarak.
6. Güncelleştirmeleri uygulama.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Şu anda sunucularınızı yönetmek Microsoft Endpoint Configuration Manager Microsoft dışı bir virüsten koruma çözümü ve MMA tabanlı bir algılayıcı kullanıyorsanız. Uç nokta için yeni Microsoft Defender'a yükseltmek istiyor olun.

Geçiş adımları:

1. Makineyi Tam Olarak Güncelleştir (Microsoft Defender Virüsten Koruma) Windows Server 2016.
2. Geçir taşınecek makineleri eklemek için üyelik kurallarıyla yeni bir koleksiyon oluşturun. 
3. Üçüncü taraf virüsten koruma yönetiminin artık bu makinelere virüsten koruma yazılımı basmaması.*
4. ILKELERInizi MECM'Endpoint Protection düğümde yazma ve yeni oluşturulan koleksiyonu hedefle.*
5. Aşağıdaki görevleri gerçekleştirmek için bir uygulama oluşturun:
   1. Uç nokta için Microsoft Defender'ın MMA çalışma alanı yapılandırmasını kaldırın. Bkz [. PowerShell kullanarak çalışma alanını kaldırma](/azure/azure-monitor/agents/agent-manage). Bu adım isteğe bağlıdır; önceki EDR algılayıcının daha yenisi etkin hale geldikten sonra çalışma durur (bunun birkaç saat sürebilir olduğunu unutmayın).
   2. Uygun olduğunda [önkoşulları](configure-server-endpoints.md#prerequisites) yükleyin.
   3. Windows Server 2012 R2 ve 2016 paketi için Uç Nokta için Microsoft Defender'ı yükleyin ve **pasif modunu etkinleştirin**. Bkz[. Komut Microsoft Defender Virüsten Koruma kullanarak yükleme](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Kullanıcı grubundan indirilen **Grup İlkesi ile kullanmak üzere** ekleme [be Microsoft 365 Defender](https://security.microsoft.com).
6. Güncelleştirmeleri uygulama.
7. Microsoft dışı virüsten koruma yazılımınızı, Microsoft dışı bir virüsten koruma konsolu kullanarak veya uygun bir Microsoft Endpoint Configuration Manager kullanarak kaldırın. Pasif modu yapılandırmasını kaldırmaya dikkat edin.*

> [!TIP]
> Yukarıdaki adımları [otomatikleştirmek için uygulamanın bir parçası olarak installer-script'i](server-migration.md#installer script) kullanabilirsiniz. Pasif modunu etkinleştirmek için, -Edilgen bayrağını uygulama. Örneğin, .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Edilgen

*Bu adımlar yalnızca Microsoft dışı virüsten koruma çözümlerinizi değiştirmek için geçerlidir. Birlikte [daha iyi: Microsoft Defender Virüsten Koruma uç nokta için Microsoft Defender'a bakın](why-use-microsoft-defender-antivirus.md).

Bir makine pasif modundan taşımak için aşağıdaki anahtarı 0 olarak ayarlayın:

Yol: HKLM\SOFTWARE\Policies\Microsoft\Windows Gelişmiş Tehdit Koruması Adı: ForceDefenderPassiveMode Tür: REG_DWORD Değer: 0


## <a name="other-migration-scenarios"></a>Diğer geçiş senaryoları

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Uç Nokta için MMA tabanlı Microsoft Defender kullanılarak ekli bir sunucunuz var. SCEP yüklü (Windows Server 2012 R2) veya Microsoft Defender Virüsten Koruma (Windows Server 2016). Bu makine Bulut **,** Windows için Microsoft Defender, Microsoft Endpoint Manager veya Microsoft Endpoint Configuration Manager.

1. Makineyi Tam Olarak Güncelleştir (Microsoft Defender Virüsten Koruma) Windows Server 2016.
2. Uç nokta için Microsoft Defender'ın MMA çalışma alanı yapılandırmasını kaldırın. Bkz [. PowerShell kullanarak çalışma alanını kaldırma](/azure/azure-monitor/agents/agent-manage).
3. S2 System Center Endpoint Protection (Windows Server 2012 R2) uygulamasını kaldırın.
4. Uygun olduğunda [önkoşulları](configure-server-endpoints.md#prerequisites) yükleyin. 
5. Uç Nokta için Microsoft Defender'ı yükleme ( [Bkz. Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).)
6. Kullanıcı grubundan indirilen **Grup İlkesi ile kullanmak üzere** ekleme [be Microsoft 365 Defender](https://security.microsoft.com). 
7. Güncelleştirmeleri uygulama.
8. Grup İlkesi, PowerShell veya üçüncü taraf bir yönetim çözümü kullanarak ilkeler oluşturun ve uygulayabilirsiniz.

> [!TIP]
> Yukarıdaki adımları otomatikleştirmek için yükleyici betiği kullanabilirsiniz.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Üzerinde Uç Nokta için Microsoft Defender'ı yüklemek istediğiniz bir sunucunuz var. Microsoft'a yönelik olmayan bir uç nokta koruması veya uç noktada algılama ve yanıtlama çözümü vardır. Bulut için Microsoft Defender veya Microsoft Endpoint Configuration Manager'i kullanmayız. Kendi dağıtım mekanizmanızı kullanırsiniz. 

1. Makineyi Tam Olarak Güncelleştir (Microsoft Defender Virüsten Koruma) Windows Server 2016.
2. Windows Server 2012 R2 2016 paketi için Uç & Microsoft Defender'ı yükleyin ve **pasif modunu etkinleştirin**. Bkz[. Komut Microsoft Defender Virüsten Koruma kullanarak yükleme](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Kendi ortamınıza uygun, bilgisayarınızdan indirilen ekleme betiği [Microsoft 365 Defender](https://security.microsoft.com). 
4. Microsoft olmayan uç nokta korumasını veya çözüm uç noktada algılama ve yanıtlama edilgen modunu kaldırın.*
5. Güncelleştirmeleri uygulama.
6. Grup İlkesi, PowerShell veya üçüncü taraf bir yönetim çözümü kullanarak ilkeler oluşturun ve uygulayabilirsiniz.

> [!TIP]
> 1 ile 4 [arasında olan adımları](server-migration.md#installer-script) otomatikleştirmeye yardımcı olmak için yükleyici betiği kullanabilirsiniz. Pasif modunu etkinleştirmek için, Defender Virüsten Koruma'nın ek işe alımdan önce pasif moduna girer ve Microsoft olmayan bir kötü amaçlı yazılımdan koruma çözümüyle engellemesini sağlayan -Edilgen bayrağını kullanın. Ardından, EDR EDR Engelle gibi güvenlik özelliklerini desteklemek amacıyla, Defender Virüsten Koruma'nın pasif modunda kalmasını sağlamak için "ForceDefenderPassiveMode" kayıt defteri anahtarının EDR emin olun. ÖRNEK: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Bu adım yalnızca Microsoft dışı virüsten koruma çözümlerinizi değiştirmek için geçerlidir. Tüm özellikleri Microsoft Defender Virüsten Koruma sağlamak için Uç Nokta için Microsoft Defender'a dahil olan Windows Defender'ı kullanmanız önerilir. Birlikte [daha iyi: Microsoft Defender Virüsten Koruma uç nokta için Microsoft Defender'a bakın](why-use-microsoft-defender-antivirus.md).

Bir makine pasif modundan taşımak için aşağıdaki anahtarı 0 olarak ayarlayın:

Yol: HKLM\SOFTWARE\Policies\Microsoft\Windows Gelişmiş Tehdit Koruması Adı: ForceDefenderPassiveMode Tür: REG_DWORD Değer: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Bulut için Microsoft Defender senaryoları

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Bulut için Microsoft Defender'ı kullanıyorsanız. Azure Microsoft Monitoring Agent (SCEP) için Microsoft Antimalware (MMA) ve/veya Başka Bir Sürüm yüklenir ve yükseltmek istiyor olun.
Bulut için Microsoft Defender'ı kullanıyorsanız, otomatik yükseltme işlemini kullanabilirsiniz. Bkz[. Bulut tümleşik uygulama çözümü için Defender ile uç EDR koruma: Uç nokta için Microsoft Defender](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>Grup İlkesi yapılandırması
Grup İlkesi kullanan yapılandırma için merkezi mağazanıza en son ADMX dosyalarını kullanarak uç nokta için doğru Defender ilke seçeneklerine erişmeye emin olun. Genel Web [Site'de](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Grup İlkesi Yönetim Şablonları için Merkezi Mağaza oluşturma ve yönetme Windows ve **Windows 10.**
