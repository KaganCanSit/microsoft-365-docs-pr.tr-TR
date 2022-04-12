---
title: yeni Pertahanan Microsoft untuk Titik Akhir sürümü için sunucu geçişi senaryoları
description: Sunucularınızı önceki MMA tabanlı çözümden geçerli Uç Nokta için Defender birleşik çözüm paketine geçirme hakkında genel bir bakış edinmek için bu makaleyi okuyun.
keywords: sunucuyu geçirme, sunucu, 2012r2, 2016, sunucu geçişi, cihaz yönetimi, Pertahanan Microsoft untuk Titik Akhir sunucuları yapılandırma, Pertahanan Microsoft untuk Titik Akhir sunucuları ekleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ed31a629f6cde18af03c3c6102b821cb6a04dd96
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782687"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Önceki MMA tabanlı Pertahanan Microsoft untuk Titik Akhir çözümünden sunucu geçişi senaryoları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Windows Server 2012 R2
- Windows Server 2016
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Yükleme veya yükseltme işlemine devam etmeden önce her zaman işletim sisteminin ve Windows Server 2016 Microsoft Defender Virüsten Koruma tam olarak güncelleştirildiğinden emin olun. EDR Algılayıcı bileşenine yönelik düzenli ürün iyileştirmeleri ve düzeltmeleri almak için[, Windows Update KB5005292'nin](https://go.microsoft.com/fwlink/?linkid=2168277) yüklendiğinden veya yüklendikten sonra onay aldığından emin olun. Ayrıca, koruma bileşenlerinin güncel kalmasını sağlamak için lütfen [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama makalesine](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) başvurun.

Bu yönergeler, Windows Server 2012 R2 ve Windows Server 2016 için Pertahanan Microsoft untuk Titik Akhir yeni birleşik çözüm ve yükleyici (MSI) paketi için geçerlidir. Bu makale, öncekinden geçerli çözüme çeşitli olası geçiş senaryoları için üst düzey yönergeler içerir. Bu üst düzey adımlar, ortamınızda bulunan dağıtım ve yapılandırma araçlarına ayarlanacak yönergeler olarak tasarlanmıştır.

> [!NOTE]
> Pertahanan Microsoft untuk Titik Akhir yüklü işletim sistemi yükseltmeleri desteklenmez. Yükseltmeye devam etmeden önce lütfen uygulamayı kapatın ve kaldırın.

> [!NOTE]
> Otomatik yükseltme gerçekleştirmek için tam Microsoft Endpoint Configuration Manager otomasyonu ve tümleştirmesi, MECM'nin sonraki bir sürümünde kullanıma sunulacaktır. En son düzeltme paketiyle birlikte 2107 sürümünden yapılandırmanın yanı sıra grup ilkesi, PowerShell, Microsoft Endpoint Manager kiracı ekleme veya yerel yapılandırma için Endpoint Protection düğümünü kullanabilirsiniz. Ayrıca, el ile yükseltme adımlarını otomatikleştirmek için Microsoft Endpoint Configuration Manager'deki mevcut işlevlerden yararlanabilirsiniz; yöntemleri aşağıda açıklanmıştır.


## <a name="installer-script"></a>Yükleyici betiği

Microsoft Endpoint Configuration Manager veya Bulut için Microsoft Defender kullanılmadığında veya yükseltmeyi gerçekleştirmek için henüz kullanılabilir olmadığında yükseltmeleri kolaylaştırmak için bu [yükseltme betiğini](https://github.com/microsoft/mdefordownlevelserver) kullanabilirsiniz. Aşağıdaki gerekli adımları otomatikleştirmeye yardımcı olabilir:

1. Pertahanan Microsoft untuk Titik Akhir için OMS çalışma alanını kaldırın (İsteğE BAĞLI).
2. Yüklüyse System Center Endpoint Protection (SCEP) istemcisini kaldırın.
3. Gerekirse (R2 Windows Server 2012) [önkoşullarını](configure-server-endpoints.md#prerequisites) indirin ve yükleyin.
4. Pertahanan Microsoft untuk Titik Akhir yükleyin.
5. [Microsoft 365 Defender'dan indirilen](https://security.microsoft.com) **grup ilkesi kullanmak için** ekleme betiğini uygulayın.

Betiği kullanmak için, yükleme ve ekleme paketlerini de yerleştirdiğiniz bir yükleme dizinine indirin (bkz. [Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).

ÖRNEK: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>geçiş senaryolarını Microsoft Endpoint Configuration Manager 

>[!NOTE]
>Microsoft Endpoint Configuration Manager, sürüm 2107 veya üzeri gerekir.

Geçiş adımları: 

1. Microsoft Defender Virüsten Koruma (Windows Server 2016) dahil olmak üzere makineyi tam olarak güncelleştirin.
2. Geçirilecek makineleri dahil etmek için üyelik kurallarıyla yeni bir koleksiyon oluşturun.
3. Aşağıdaki görevleri gerçekleştirmek için [bir uygulama oluşturun](/mem/configmgr/apps/deploy-use/create-applications): 
   1. SCEP'i kaldırın.
   2. [Önkoşulları](configure-server-endpoints.md#prerequisites) uygun olduğunda yükleyin.
   3. Pertahanan Microsoft untuk Titik Akhir yükleme (bkz. [Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).
   4. [Microsoft 365 Defender'dan indirilen](https://security.microsoft.com) **grup ilkesi kullanmak için** ekleme betiğini uygulayın. 
   > [!TIP]
   > Yukarıdaki adımları otomatikleştirmek için [yükleyici betiğini](server-migration.md#installer-script) uygulamanızın bir parçası olarak kullanabilirsiniz.
4. Uygulamayı yeni koleksiyona dağıtın.
5. Koleksiyona Endpoint Protection ilkeleri oluşturun ve/veya atayın.
6. Güncelleştirmeleri uygulama.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Şu anda sunucularınızı yönetmek için Microsoft Endpoint Configuration Manager kullanıyorsunuz, Microsoft dışı bir virüsten koruma çözümü ve MMA tabanlı algılayıcı çalıştırıyorsunuz. Yeni Pertahanan Microsoft untuk Titik Akhir yükseltmek istiyorsunuz.

Geçiş adımları:

1. Microsoft Defender Virüsten Koruma (Windows Server 2016) dahil olmak üzere makineyi tam olarak güncelleştirin.
2. Geçirilecek makineleri dahil etmek için üyelik kurallarıyla yeni bir koleksiyon oluşturun. 
3. Üçüncü taraf virüsten koruma yönetiminin artık bu makinelere virüsten koruma göndermediğinden emin olun.*
4. İlkelerinizi MECM'nin Endpoint Protection düğümünde yazın ve yeni oluşturulan koleksiyonu hedefleyin.*
5. Aşağıdaki görevleri gerçekleştirmek için bir uygulama oluşturun:
   1. Pertahanan Microsoft untuk Titik Akhir için MMA çalışma alanı yapılandırmasını kaldırın. Bkz. [PowerShell kullanarak çalışma alanını kaldırma](/azure/azure-monitor/agents/agent-manage). Bu adım isteğe bağlıdır; önceki EDR algılayıcısı, yenisi etkin hale geldikten sonra çalışmayı durdurur.
   2. [Önkoşulları](configure-server-endpoints.md#prerequisites) uygun olduğunda yükleyin.
   3. Windows Server 2012 R2 ve 2016 paketi için Pertahanan Microsoft untuk Titik Akhir yükleyin ve **pasif modu etkinleştirin**. Bkz[. Komut satırını kullanarak Microsoft Defender Virüsten Koruma yükleme](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. [Microsoft 365 Defender'dan indirilen](https://security.microsoft.com) **grup ilkesi kullanmak için** ekleme betiğini uygulayın.
6. Güncelleştirmeleri uygulama.
7. Microsoft dışı virüsten koruma yazılımınızı Microsoft dışı virüsten koruma konsolunu veya uygun Microsoft Endpoint Configuration Manager kullanarak kaldırın. Pasif mod yapılandırmasını kaldırdığınızdan emin olun.*

> [!TIP]
> Yukarıdaki adımları otomatikleştirmek için [yükleyici betiğini](server-migration.md#installer script) uygulamanızın bir parçası olarak kullanabilirsiniz. Pasif modu etkinleştirmek için -Passive bayrağını uygulayın. Örneğin, .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*Bu adımlar yalnızca Microsoft dışı virüsten koruma çözümünüzü değiştirmek istiyorsanız geçerlidir. [Bkz. Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Pertahanan Microsoft untuk Titik Akhir](why-use-microsoft-defender-antivirus.md).

Bir makineyi pasif moddan çıkarmak için aşağıdaki anahtarı 0 olarak ayarlayın:

Yol: HKLM\SOFTWARE\Policies\Microsoft\Windows Gelişmiş Tehdit Koruması Adı: ForceDefenderPassiveMode Türü: REG_DWORD Değer: 0


## <a name="other-migration-scenarios"></a>Diğer geçiş senaryoları

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>MMA tabanlı Pertahanan Microsoft untuk Titik Akhir kullanılarak eklenmiş bir sunucunuz var. SCEP yüklü (Windows Server 2012 R2) veya Microsoft Defender Virüsten Koruma (Windows Server 2016). Bu makine Bulut için Microsoft Defender, Microsoft Endpoint Manager veya Microsoft Endpoint Configuration Manager aracılığıyla **yönetilmiyor**.

1. Microsoft Defender Virüsten Koruma (Windows Server 2016) dahil olmak üzere makineyi tam olarak güncelleştirin.
2. Pertahanan Microsoft untuk Titik Akhir için MMA çalışma alanı yapılandırmasını kaldırın. Bkz. [PowerShell kullanarak çalışma alanını kaldırma](/azure/azure-monitor/agents/agent-manage).
3. System Center Endpoint Protection kaldırın (R2 Windows Server 2012).
4. [Önkoşulları](configure-server-endpoints.md#prerequisites) uygun olduğunda yükleyin. 
5. Pertahanan Microsoft untuk Titik Akhir yükleme (bkz[. Sunucu uç noktalarını yapılandırma](configure-server-endpoints.md).)
6. [Microsoft 365 Defender'dan indirilen](https://security.microsoft.com) **grup ilkesi kullanmak için** ekleme betiğini uygulayın. 
7. Güncelleştirmeleri uygulama.
8. grup ilkesi, PowerShell veya üçüncü taraf bir yönetim çözümü kullanarak ilkeler oluşturun ve uygulayın.

> [!TIP]
> Yukarıdaki adımları otomatikleştirmek için yükleyici betiğini kullanabilirsiniz.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Pertahanan Microsoft untuk Titik Akhir yüklemek istediğiniz bir sunucunuz var. Microsoft olmayan bir uç nokta koruması veya uç noktada algılama ve yanıtlama çözümü yüklüdür. Microsoft Endpoint Configuration Manager veya Bulut için Microsoft Defender kullanmayı amaçlamayın. Kendi dağıtım mekanizmanızı kullanırsınız. 

1. Microsoft Defender Virüsten Koruma (Windows Server 2016) dahil olmak üzere makineyi tam olarak güncelleştirin.
2. Windows Server 2012 R2 & 2016 paketi için Pertahanan Microsoft untuk Titik Akhir yükleyin ve **pasif modu etkinleştirin**. Bkz[. Komut satırını kullanarak Microsoft Defender Virüsten Koruma yükleme](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. [Microsoft 365 Defender'den](https://security.microsoft.com) indirilen, ortamınıza uygun ekleme betiğini uygulayın. 
4. Microsoft dışı uç nokta korumasını veya uç noktada algılama ve yanıtlama çözümünü kaldırın ve pasif modu kaldırın.*
5. Güncelleştirmeleri uygulama.
6. grup ilkesi, PowerShell veya üçüncü taraf bir yönetim çözümü kullanarak ilkeler oluşturun ve uygulayın.

> [!TIP]
> 1 ile 4 arasında adımları otomatikleştirmeye yardımcı olması için [yükleyici betiğini](server-migration.md#installer-script) kullanabilirsiniz. Pasif modu etkinleştirmek için Defender Virüsten Koruma'nın eklemeden önce pasif moda geçmesini ve Microsoft dışı kötü amaçlı yazılımdan koruma çözümünü engellememesini sağlayacak -Passive bayrağını uygulayın. Ardından, EDR Block gibi EDR özellikleri desteklemek üzere eklendikten sonra Defender Virüsten Koruma'nın pasif modda kalmasını sağlamak için "ForceDefenderPassiveMode" kayıt defteri anahtarını ayarladığınızdan emin olun. ÖRNEK: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Bu adım yalnızca Microsoft dışı virüsten koruma çözümünüzü değiştirmek istiyorsanız geçerlidir. Tüm özellikleri sağlamak için Pertahanan Microsoft untuk Titik Akhir dahil Microsoft Defender Virüsten Koruma kullanmanızı öneririz. [Bkz. Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Pertahanan Microsoft untuk Titik Akhir](why-use-microsoft-defender-antivirus.md).

Bir makineyi pasif moddan çıkarmak için aşağıdaki anahtarı 0 olarak ayarlayın:

Yol: HKLM\SOFTWARE\Policies\Microsoft\Windows Gelişmiş Tehdit Koruması Adı: ForceDefenderPassiveMode Türü: REG_DWORD Değer: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Bulut için Microsoft Defender senaryoları

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Bulut için Microsoft Defender kullanıyorsunuz. Azure için Microsoft Monitoring Agent (MMA) ve/veya Microsoft Antimalware (SCEP) yüklüdür ve yükseltmek istiyorsunuz.
Bulut için Microsoft Defender kullanıyorsanız otomatik yükseltme işleminden yararlanabilirsiniz. Bkz. [Bulut için Defender tümleşik EDR çözümüyle uç noktalarınızı koruma: Pertahanan Microsoft untuk Titik Akhir](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>grup ilkesi yapılandırması
grup ilkesi kullanarak yapılandırma için, doğru Uç Nokta için Defender ilke seçeneklerine erişmek için merkezi deponuzdaki en son ADMX dosyalarını kullandığınızdan emin olun. Lütfen [Windows'da yönetim şablonları grup ilkesi için Merkezi Mağaza oluşturma ve yönetme](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) makalesine başvurun ve **Windows 10 ile kullanmak üzere** en son dosyaları indirin.
