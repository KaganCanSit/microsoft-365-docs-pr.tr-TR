---
title: Posta üzerinde dağıtma, yönetme ve Microsoft Defender Virüsten Koruma
description: Intune, Microsoft Defender Virüsten Koruma, Grup İlkesi, PowerShell veya WMI Microsoft Endpoint Configuration Manager e-postayı dağıtabilirsiniz ve yönetabilirsiniz
keywords: dağıtma, yönetme, güncelleştirme, koruma, Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1ce212bf01b8c464760192a4bbd6355498d19c3c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998049"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Posta üzerinde dağıtma, yönetme ve Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Çeşitli yollarla bu uygulamaları dağıtabilirsiniz, Microsoft Defender Virüsten Koruma ve raporleyebilirsiniz.

Microsoft Defender Virüsten Koruma istemcisi Windows 10 ve Windows 11'in çekirdek parçası olarak yüklü olduğundan, istemcinin uç noktalarınıza geleneksel dağıtımı geçerli değildir.

Bununla birlikte, çoğu durumda aşağıdaki tabloda açıklanan Microsoft Intune, Microsoft Endpoint Configuration Manager, Bulut için Microsoft Defender veya Grup İlkesi Nesneleri ile uç noktalarınız üzerinde koruma hizmetini etkinleştirmeniz gerekir.

Ayrıca aşağıdakiler için ek bağlantılar da vardır:

- Ürün Microsoft Defender Virüsten Koruma koruma güncelleştirmeleri de içinde olmak üzere veri korumasını yönetme
- Veri korumasını Microsoft Defender Virüsten Koruma raporlama

> [!IMPORTANT]
> Çoğu durumda, Windows 10 veya Windows 11, çalışan ve güncel olan başka bir virüsten koruma ürünü bulursa Microsoft Defender Virüsten Koruma'i devre dışı bıraktır. Bu güncelleştirmenin çalışması için, önce üçüncü taraf virüsten koruma Microsoft Defender Virüsten Koruma devre dışı bırakmanız veya kaldırmanız gerekir. Üçüncü taraf virüsten koruma ürünlerini yeniden etkinleştirir veya yüklürsanız, Windows 10 veya Windows 11 otomatik olarak virüsten Microsoft Defender Virüsten Koruma.

Araç|Dağıtım seçenekleri (<a href="#fn2" id="ref2">2</a>)|Yönetim seçenekleri (ağ genelinde yapılandırma ve ilke veya temel dağıtım) ([3](#fn3))|Raporlama seçenekleri
---|---|---|---
Microsoft Intune|[Intune'da uç nokta koruma ayarları ekleme](/intune/endpoint-protection-configure)|[Intune'da cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure)| [Cihazları yönetmek için Intune konsolunu kullanma](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|[Özel Endpoint Protection site sistem rolü][] ve [Endpoint Protection siteyi özel istemci ayarlarıyla etkinleştirme][]|[Varsayılan ve özelleştirilmiş kötü amaçlı yazılımdan koruma ilkeleri][] ve [istemci yönetimi][] ile|Varsayılan [Yapılandırma Yöneticisi İzleme çalışma alanı][] ve [e-posta uyarıları][]
Grup İlkesi ve Active Directory (etki alanına katılmış)|Yapılandırma değişikliklerini dağıtmak ve ayarların etkinleştirildiğinden emin olmak için Grup Microsoft Defender Virüsten Koruma nesnesi kullanın.|[özellikleri yapılandırma][] ve [Özellikleri Microsoft Defender Virüsten Koruma yapılandırma][] için Grup İlkesi Nesneleri'Windows Defender kullanın][]|Uç nokta raporlaması Grup İlkesi ile kullanılamaz. [Grup İlkeleri listesi oluşturarak, herhangi bir ayarın veya ilkenin uygulanmadıyı belirlemek için][]
PowerShell|Tek tek uç noktalara Grup İlkesiyle, Microsoft Endpoint Configuration Manager veya el ile dağıtın.|Defender modülünde bulunan [Set-MpPreference] ve [Update-MpSignature] cmdlet'lerini kullanın.|Defender modülünde uygun [Get- cmdlet'leri kullanın][]
Windows Yönetimi Aracı|Tek tek uç noktalara Grup İlkesiyle, Microsoft Endpoint Configuration Manager veya el ile dağıtın.|[Sınıf için [Set MSFT_MpPreference][] ve [Sınıf için güncelleştirme MSFT_MpSignature][]|[MSFT_MpComputerStatus][] sınıfını ve [Windows Defender WMIv2 Sağlayıcı][]
Microsoft Azure|Azure portalında Microsoft Antimalware, sanal makine yapılandırmasını veya [Visual Studio cmdlet'lerini kullanarak Azure için Azure PowerShell dağıtın](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Ayrıca Bulut için [Microsoft Defender'da Uç Nokta Korumasını Yükleyebilirsiniz*](/azure/security-center/security-center-install-endpoint-protection)|Microsoft Antimalware [Cmdlet'leriyle Sanal](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) Makineler ve Bulut Hizmetleri Azure PowerShell yapılandırma veya [kod örnekleri kullanma](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|[İzlemeyi Microsoft Antimalware için Sanal Makineler ve Bulut Hizmetleri Azure PowerShell Cmdlet'leri](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) ile birlikte kullanın. Ayrıca, [Muhtemelen virüs bulaşabilir cihazlar][] raporu dahil olmak üzere şüpheli etkinlikleri belirlemek için Azure Active Directory'daki kullanım raporlarını gözden geçirebilirsiniz ve [Microsoft Defender Virüsten Koruma olayları][] hakkında rapor yapmak ve bu aracı AAD'te bir uygulama olarak eklemek için bir SIEM aracı yapılandırabilirsiniz.

1. <span id="fn1" />Özellikle buluta teslim edilen korumayla ilgili bazı işlev ve özelliklerin kullanılabilirliği, Microsoft Endpoint Manager (Geçerli Dalı) ile System Center Yapılandırma Yöneticisi arasında farklılık gösterir. Bu kitaplıkta 11, Windows 10, Windows ve Windows Server 2016 (Güncel Dalı) Microsoft Endpoint Manager odaklandı. En [önemli farkları açıklayan tablo için bkz. Microsoft Defender Virüsten Koruma'de Microsoft](cloud-protection-microsoft-defender-antivirus.md) bulutla korumayı kullanma. [(Tabloya dön)](#ref2)

2. <span id="fn2" />Windows 10 ve Windows 11'de, Microsoft Defender Virüsten Koruma bileşeni ek istemci veya hizmetin yüklenmesi veya dağıtımı olmadan kullanılabilir. Üçüncü taraf virüsten koruma ürünleri kaldırildiğinde veya güncel değilken otomatik olarak etkinleştirilir (üçüncü taraf virüsten koruma ürünleri Windows Server 2016. Bu nedenle geleneksel dağıtım gerekmez. Burada dağıtım, en son bileşenin Microsoft Defender Virüsten Koruma uç noktalar veya sunucularda etkinleştirildiğinden ve etkinleştirildiğinden emin olmak anlamına gelir. [(Tabloya dön)](#ref2)

3. <span id="fn3" />Ürün ve koruma güncelleştirmelerini yapılandırma da içinde olmak üzere özelliklerin ve korumanın yapılandırması, bu kitaplığın [Microsoft Defender Virüsten Koruma yapılandırma](configure-notifications-microsoft-defender-antivirus.md) bölümünde daha ayrıntılı olarak açıklanmıştır. [(Tabloya dön)](#ref2)

## <a name="in-this-section"></a>Bu bölümde

Konu | Açıklama
---|---
[Korumayı dağıtma Microsoft Defender Virüsten Koruma etkinleştirme](deploy-microsoft-defender-antivirus.md) | İstemci Windows 10 veya Windows 11'in temel bir parçası olarak yüklenirken ve geleneksel dağıtım geçerli olmazken, istemciyi Microsoft Endpoint Configuration Manager, Microsoft Intune veya Grup İlkesi Nesneleriyle uç noktalarında etkinleştirmeniz gerekir.
[Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md) | İçerik güncelleştirmenin iki Microsoft Defender Virüsten Koruma vardır: uç noktalarda istemciyi güncelleştirme (ürün güncelleştirmeleri) ve Güvenlik zekası güncelleştirmeleri (koruma güncelleştirmeleri). Güvenlik zekası güncelleştirmesini, Güvenlik Zekası'Microsoft Endpoint Configuration Manager, PowerShell ve WMI'ı kullanarak çeşitli yollarla güncelleştirebilirsiniz.
[Korumayı izleme ve Microsoft Defender Virüsten Koruma bildirme](report-monitor-microsoft-defender-antivirus.md) | Koruma durumunu izlemek ve uç nokta koruması hakkında raporlar oluşturmak için Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Operations Management Suite için Güncelleştirme Uyumluluğu eklentisini veya üçüncü taraf SIEM ürününü kullanabilirsiniz (Windows olay günlüklerini tüketerek).
