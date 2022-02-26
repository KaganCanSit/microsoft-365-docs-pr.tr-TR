---
title: Organizasyonunız için İkincil özelliğini yapılandırma
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
description: 'Exchange PowerShell kullanarak, tüm ya da belirli kullanıcılar için İkincil özelliğini etkinleştirmeyi veya devre dışı bırakmayı öğrenin. '
ms.openlocfilehash: 5037e7cb6518ca90f3d12c183fcff3c838c29907
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973610"
---
# <a name="configure-clutter-for-your-organization"></a>Organizasyonunız için İkincil özelliğini yapılandırma

> [!TIP]
> [Odaklanmış Gelen](../setup/configure-focused-inbox.md) Kutusu, İkincil'in yerini alacak. Daha fazla bilgi: [Odaklanmış Gelen Kutusu'na ve İkincil için planlarımıza göre güncelleştirme](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Yönetici olarak, iş yeriz için İkincil özelliğini yönetmeniz Microsoft 365. İkincil özelliğini kurumdaki kullanıcılar için açmak/kapatmak için, Exchange PowerShell kullan gerekir. (Tek tek kişiler şu yönergeleri kullanarak özelliği açabilirsiniz/kapatabilirsiniz: İkincil [özelliğini iki](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) Outlook.
  
Exchange [PowerShell](/powershell/exchange/exchange-online-powershell) kullanma hakkında ayrıntılı bilgi için [Bağlan Exchange Online ve Exchange Online için PowerShell'i Exchange](/powershell/exchange/connect-to-exchange-online-powershell) göz atabilirsiniz. En az en az en Exchange Hizmet yöneticisi rolüne ve Exchange Online PowerShell'e bağlanabilme yeteneğine sahip bir hesabınız gerekir. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Exchange PowerShell kullanarak İkincil özelliğini açma

Set-Clutter cmdlet'ini çalıştırarak posta kutusu [için İkincil özelliğini el ile](/powershell/module/exchange/set-clutter) etkinleştirebilirsiniz. Ayrıca, Get-Clutter cmdlet'ini çalıştırarak da, kuruluşların posta [kutuları için İkincil ayarlarını](/powershell/module/exchange/get-clutter) görüntüebilirsiniz. 
  
Allie Bellew adlı tek bir kullanıcı için İkincil özelliğini açma
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Exchange PowerShell'i kullanarak İkincil özelliğini kapatma

Set-Clutter cmdlet'ini çalıştırarak posta kutusu için [İkincil'i el ile](/powershell/module/exchange/set-clutter) devre dışı ekleyebilirsiniz. Ayrıca, Get-Clutter cmdlet'ini çalıştırarak da, kuruluşların posta [kutuları için İkincil ayarlarını](/powershell/module/exchange/get-clutter) görüntüebilirsiniz. 
  
Allie Bellew adlı tek bir kullanıcı için İkincil özelliğini kapatın:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Kullanıcılarınızı toplu olarak oluşturmak için PowerShell kullanıyorsanız, İkincil'i yönetmek için her kullanıcının posta kutusunda [Set-Clutter'ı](/powershell/module/exchange/set-clutter) çalıştırmanız gerekir. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>İkincil özelliğini açma/kapatma anahtarı diğer kullanıcılara ne zaman Web üzerinde Outlook?
<a name="bkmk_onoff"> </a>

Yönetici olarak, Exchange PowerShell kullanarak İkincil özelliğini yeniden etkinleştirabilirsiniz. Bu yapıldıktan sonra, Odaklanmış Gelen Kutusu kapatacağız ve İkincil özelliği yeniden etkin hale gelecektir. 
  
 **Web üzerinde Outlook'i Microsoft 365 İş Ekstra kullanıyorsanız:**
  
- Kullanıcı şu anda İkincil özelliğini etkinleştirmişse: 
    
  - İkincil özelliğinin ayarları görüntülenir
    
- Kullanıcı şu anda Odaklanmış Gelen Kutusu'na etkinleştirmişse: 
    
  - İkincil özelliğinin ayarları görünmez
    
- İkincil veya Odaklanmış Gelen Kutusu etkin değilse: 
    
  - Hem İkincil hem de Odaklanmış Gelen Kutusu, kullanıcının Posta Kutusunda seçenekler olarak Ayarlar
    
 **Outlook.com kullanıyorsanız:**
  
- Kullanıcı şu anda İkincil özelliğini etkinleştirmişse: 
    
  - İkincil özelliğinin ayarları görüntülenir
    
- Kullanıcı şu anda Odaklanmış Gelen Kutusu'na etkinleştirmişse: 
    
  - İkincil özelliğinin ayarları görünmez
    
- İkincil veya Odaklanmış Gelen Kutusu etkin değilse: 
    
  - Hem İkincil hem de Odaklanmış Gelen Kutusu, kullanıcının Posta Kutusunda seçenekler olarak Ayarlar
    
- Kullanıcı Geçmişteki bir noktada Odaklanmış Gelen Kutusu'na etkinleştirildiyse:
    
  - İkincil özelliğinin ayarları hiçbir zaman görünmez
    
    Aksi takdirde, 
    
  - İkincil özelliğinin ayarları görüntülenir
    
## <a name="related-content"></a>İlgili içerik

[karışık e-postada düşük öncelikli iletileri sıralamak için karışık Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (makale)\
[OWA'da düşük öncelikli iletileri sıralamak için Karışık E-posta özelliğini kullanma](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (makale)\
[E-postada İkincil özelliğini Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (makale)
