---
title: Microsoft Defender Virüsten Koruma dağıtma, yönetme ve raporlama
description: Intune, Microsoft Endpoint Configuration Manager, grup ilkesi, PowerShell veya WMI ile Microsoft Defender Virüsten Koruma dağıtabilir ve yönetebilirsiniz
keywords: dağıtma, yönetme, güncelleştirme, koruma Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 778b12e1096c5ecfdb960955b52624c65b492d54
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872687"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma dağıtma, yönetme ve raporlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma 

**Platform**
- Windows

Microsoft Defender Virüsten Koruma çeşitli yollarla dağıtabilir, yönetebilir ve raporlayabilirsiniz.

Microsoft Defender Virüsten Koruma istemcisi Windows 10 ve Windows 11 temel bir parçası olarak yüklendiğinden, istemcinin uç noktalarınıza geleneksel dağıtımı geçerli değildir.

Ancak çoğu durumda Microsoft Intune, Microsoft Endpoint Configuration Manager, Bulut için Microsoft Defender veya grup ilkesi ile uç noktalarınızda koruma hizmetini etkinleştirmeniz gerekir  Aşağıdaki tabloda açıklanan nesneler.

Ayrıca şunların ek bağlantılarını da görürsünüz:

- Ürün ve koruma güncelleştirmelerini yönetme de dahil olmak üzere Microsoft Defender Virüsten Koruma korumayı yönetme
- Microsoft Defender Virüsten Koruma koruma hakkında raporlama

> [!IMPORTANT]
> Çoğu durumda, Windows 10 veya Windows 11, çalışan ve güncel olan başka bir virüsten koruma ürünü bulursa Microsoft Defender Virüsten Koruma devre dışı bırakır. Microsoft Defender Virüsten Koruma çalışmadan önce üçüncü taraf virüsten koruma ürünlerini devre dışı bırakmanız veya kaldırmanız gerekir. Üçüncü taraf virüsten koruma ürünlerini yeniden etkinleştirir veya yüklerseniz Windows 10 veya Windows 11 Microsoft Defender Virüsten Koruma otomatik olarak devre dışı bırakır.

Araç|Dağıtım seçenekleri (<a href="#fn2" id="ref2">2</a>)|Yönetim seçenekleri (ağ genelinde yapılandırma ve ilke veya temel dağıtım) ([3](#fn3))|Raporlama seçenekleri
---|---|---|---
Microsoft Intune|[Intune'de uç nokta koruma ayarları ekleme](/intune/endpoint-protection-configure)|[Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure)| [Cihazları yönetmek için Intune konsolunu kullanma](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|[Endpoint Protection noktası site sistemi rolünü][] ve [özel istemci ayarlarıyla Endpoint Protection etkinleştir][] kullanın|[varsayılan ve özelleştirilmiş kötü amaçlı yazılımdan koruma ilkeleri][] ve [istemci yönetimi][] ile|Varsayılan [Configuration Manager İzleme çalışma alanı][] ve [e-posta uyarıları][] ile
grup ilkesi ve Active Directory (etki alanına katılmış)|Yapılandırma değişikliklerini dağıtmak ve Microsoft Defender Virüsten Koruma etkinleştirildiğinden emin olmak için grup ilkesi Nesnesi kullanın.|[Microsoft Defender Virüsten Koruma için güncelleştirme seçeneklerini yapılandırma][] ve [Windows Defender özelliklerini yapılandırma][] için grup ilkesi Nesnelerini (GPO' lar) kullanın|Uç nokta raporlaması grup ilkesi ile kullanılamaz. Herhangi bir ayar veya ilkenin uygulanmadığını belirlemek için [Grup İlkeleri] listesini oluşturabilirsiniz][]
PowerShell|tek tek uç noktalarda grup ilkesi, Microsoft Endpoint Configuration Manager veya el ile dağıtın.|Defender modülünde bulunan [Set-MpPreference] ve [Update-MpSignature] cmdlet'lerini kullanın.|Uygun [Defender modülünde kullanılabilen Get- cmdlet'lerini kullanın][]
Windows Yönetim Araçları|tek tek uç noktalarda grup ilkesi, Microsoft Endpoint Configuration Manager veya el ile dağıtın.|[MSFT_MpPreference sınıfının set yöntemini][] ve [MSFT_MpSignature sınıfının güncelleştirme yöntemini][] kullanın|[MSFT_MpComputerStatus][] sınıfını ve [Windows Defender WMIv2 Sağlayıcısında ilişkili sınıfların get yöntemini kullanın][]
Microsoft Azure|Azure portal [Visual Studio sanal makine yapılandırmasını veya Azure PowerShell cmdlet'lerini kullanarak Azure için Microsoft Antimalware dağıtın](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). [Uç nokta korumasını Bulut için Microsoft Defender* içinde de yükleyebilirsiniz](/azure/defender-for-cloud/endpoint-protection-recommendations-technical)|[Azure PowerShell cmdlet'leri ile Sanal Makineler ve Cloud Services için Microsoft Antimalware](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) yapılandırma veya [kod örnekleri kullanma](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|İzlemeyi etkinleştirmek [için Sanal Makineler için Microsoft Antimalware ve Azure PowerShell cmdlet'leri olan Bulut Hizmetleri'ni](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) kullanın. Ayrıca Azure Active Directory'daki kullanım raporlarını gözden geçirerek [Muhtemelen bulaşmış cihazlar][] raporu da dahil olmak üzere şüpheli etkinlikleri belirleyebilir ve bir SIEM aracını [Microsoft Defender Virüsten Koruma olayları][] hakkında rapor vermek üzere yapılandırabilir ve bu aracı AAD'ye uygulama olarak ekleyebilirsiniz.

1. <span id="fn1" />Özellikle bulut tabanlı korumayla ilgili bazı işlevlerin ve özelliklerin kullanılabilirliği, Microsoft Endpoint Manager (Geçerli Dal) ile System Center 2012 Configuration Manager arasında farklılık gösterir. Bu kitaplıkta Windows 10, Windows 11, Windows Server 2016 ve Microsoft Endpoint Manager (Geçerli Dal) üzerine odaklandık. Önemli farklılıkları açıklayan bir tablo için bkz. [Microsoft Defender Virüsten Koruma'de Microsoft bulut tarafından sağlanan korumayı kullanma](cloud-protection-microsoft-defender-antivirus.md). [(Tabloya dön)](#ref2)

2. <span id="fn2" />Windows 10 ve Windows 11 Microsoft Defender Virüsten Koruma, ek bir istemci veya hizmet yüklemeden veya dağıtmadan kullanılabilen bir bileşendir. Üçüncü taraf virüsten koruma ürünleri kaldırıldığında veya güncel olmadığında (Windows Server 2016 hariç) otomatik olarak etkinleştirilir. Bu nedenle geleneksel dağıtım gerekli değildir. Burada dağıtım, uç noktalarda veya sunucularda Microsoft Defender Virüsten Koruma bileşeninin kullanılabilir ve etkin olduğundan emin olmak anlamına gelir. [(Tabloya dön)](#ref2)

3. <span id="fn3" />Ürün ve koruma güncelleştirmelerini yapılandırma da dahil olmak üzere özelliklerin ve korumanın yapılandırması, bu kitaplığın [Microsoft Defender Virüsten Koruma özelliklerini yapılandırma](configure-notifications-microsoft-defender-antivirus.md) bölümünde daha ayrıntılı olarak açıklanmıştır. [(Tabloya dön)](#ref2)

## <a name="in-this-section"></a>Bu bölümde

Makale | Açıklama
---|---
[Microsoft Defender Virüsten Koruma korumasını dağıtma ve etkinleştirme](deploy-microsoft-defender-antivirus.md) | İstemci Windows 10 veya Windows 11 temel bir parçası olarak yüklenmiş olsa da ve geleneksel dağıtım geçerli olmasa da, istemciyi uç noktalarınızda Microsoft Endpoint Configuration Manager, Microsoft Intune veya nesneleri grup ilkesi.
[Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md) | Microsoft Defender Virüsten Koruma güncelleştirilmesinin iki bölümü vardır: uç noktalarda istemciyi güncelleştirme (ürün güncelleştirmeleri) ve Güvenlik bilgilerini güncelleştirme (koruma güncelleştirmeleri). Microsoft Endpoint Configuration Manager, grup ilkesi, PowerShell ve WMI kullanarak Güvenlik bilgilerini çeşitli yollarla güncelleştirebilirsiniz.
[Microsoft Defender Virüsten Koruma korumayı izleme ve raporlama](report-monitor-microsoft-defender-antivirus.md) | Koruma durumunu izlemek ve uç nokta koruması hakkında raporlar oluşturmak için Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Operations Management Suite için Güncelleştirme Uyumluluğu eklentisini veya üçüncü taraf bir SIEM ürününü (Windows olay günlüklerini kullanarak) kullanabilirsiniz.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
    
