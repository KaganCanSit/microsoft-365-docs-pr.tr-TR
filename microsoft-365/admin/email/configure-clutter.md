---
title: Kuruluşunuz için İkincil'i yapılandırma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'Exchange PowerShell kullanarak kuruluşunuzdaki tüm veya belirli kullanıcılar için İkincil özelliğini etkinleştirmeyi veya devre dışı bırakmayı öğrenin. '
ms.openlocfilehash: 64c11b2a8bbce3747727c458a4427f5c0e1b135b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437205"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>Kuruluşunuz için Microsoft 365 İkincil'i yapılandırma

> [!TIP]
> [Odaklanmış Gelen Kutusu](../setup/configure-focused-inbox.md) İkincil'in yerini alacak. Daha fazla bilgi edinin: [Odaklanmış Gelen Kutusu'nu ve İkincil planlarımızı güncelleştirme](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Yönetici olarak, Microsoft 365 İkincil özelliğini yönetmeniz gerekebilir. Kuruluşunuzdaki kullanıcılar için İkincil özelliğini açmak/kapatmak için PowerShell'Exchange kullanmanız gerekir. (Kişiler şu yönergeleri kullanarak bu özelliği açabilir/kapatabilir: [Outlook İkincil özelliğini kapatın/açın](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
[PowerShell'i Exchange kullanma hakkında](/powershell/exchange/exchange-online-powershell) ayrıntılı bilgi [için PowerShell'i Exchange Online için PowerShell'i Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) ve Bağlan ile kullanma bölümüne bakın. En azından Exchange Hizmet yöneticisi rolüne ve PowerShell ile Exchange Online bağlanabilen bir hesabınız olmalıdır. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Exchange PowerShell kullanarak İkincil özelliğini açma

[Set-Clutter](/powershell/module/exchange/set-clutter) cmdlet'ini çalıştırarak bir posta kutusu için İkincil'i el ile etkinleştirebilirsiniz. Get-Clutter cmdlet'ini çalıştırarak kuruluşunuzdaki posta kutuları için [İkincil](/powershell/module/exchange/get-clutter) ayarlarını da görüntüleyebilirsiniz. 
  
Allie Bellew adlı tek bir kullanıcı için İkincil özelliğini açma
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Exchange PowerShell kullanarak İkincil özelliğini kapatma

[Set-Clutter](/powershell/module/exchange/set-clutter) cmdlet'ini çalıştırarak bir posta kutusu için İkincil özelliğini el ile devre dışı bırakabilirsiniz. **Get-Clutter** cmdlet'ini çalıştırarak kuruluşunuzdaki posta kutuları için [İkincil](/powershell/module/exchange/get-clutter) ayarlarını da görüntüleyebilirsiniz. 
  
Allie Bellew adlı tek bir kullanıcı için İkincil özelliğini kapatın:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Kullanıcılarınızı toplu olarak oluşturmak için PowerShell kullanıyorsanız, İkincil'i yönetmek için her kullanıcının posta kutusunda [Set-Clutter](/powershell/module/exchange/set-clutter) çalıştırmanız gerekir. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>İkincil açma/kapatma düğmesi Web üzerinde Outlook kullanıcılara ne zaman görünür?
<a name="bkmk_onoff"> </a>

Yönetici olarak, Exchange PowerShell kullanarak İkincil özelliğini yeniden etkinleştirebilirsiniz. Bu işlem tamamlandıktan sonra Odaklanmış Gelen Kutusu kapatılır ve İkincil özelliği yeniden etkin olur. 
  
 **Microsoft 365 İş Ekstra aboneliğiyle Web üzerinde Outlook kullanıyorsanız:**
  
- Kullanıcı şu anda İkincil özelliğini etkinleştirmişse: 
    
  - İkincil ayarları görünür
    
- Kullanıcının şu anda Odaklanmış Gelen Kutusu etkinse: 
    
  - İkincil ayarları görünmez
    
- İkincil veya Odaklanmış Gelen Kutusu etkin değilse: 
    
  - Kullanıcının Posta Ayarlar hem İkincil hem de Odaklanmış Gelen Kutusu seçenekler olarak görünür
    
 **Outlook.com kullanıyorsanız:**
  
- Kullanıcı şu anda İkincil özelliğini etkinleştirmişse: 
    
  - İkincil ayarları görünür
    
- Kullanıcının şu anda Odaklanmış Gelen Kutusu etkinse: 
    
  - İkincil ayarları görünmez
    
- İkincil veya Odaklanmış Gelen Kutusu etkin değilse: 
    
  - Kullanıcının Posta Ayarlar hem İkincil hem de Odaklanmış Gelen Kutusu seçenekler olarak görünür
    
- Kullanıcı geçmişte bir noktada Odaklanmış Gelen Kutusu'nu etkinleştirdiyse:
    
  - İkincil ayarları hiçbir zaman görünmez
    
    Aksi takdir -de 
    
  - İkincil ayarları görüntülenir
    
## <a name="related-content"></a>İlgili içerik

[Outlook düşük öncelikli iletileri sıralamak için İkincil özelliğini kullanma](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (makale)\
[OWA'da düşük öncelikli iletileri sıralamak için İkincil özelliğini kullanma](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (makale)\
[Outlook İkincil özelliğini kapatma](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (makale)
