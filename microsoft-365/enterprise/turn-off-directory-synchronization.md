---
title: Microsoft 365 için dizin eşitlemeyi kapatma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Bu makalede, Microsoft 365 için dizin eşitlemesini kapatmak için PowerShell kullanma hakkında bilgi bulabilirsiniz.
ms.openlocfilehash: 5082f89032c17e549f11f8397126f6d059937c48
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077344"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Microsoft 365 için dizin eşitlemeyi kapatma
Dizin eşitlemesini kapatmak ve eşitlenen kullanıcılarınızı yalnızca buluta dönüştürmek için PowerShell'i kullanabilirsiniz. Ancak, sorun giderme adımı olarak dizin eşitlemesini kapatmanız önerilmez. Dizin eşitleme sorunlarını giderme konusunda yardıma ihtiyacınız varsa, [Microsoft 365 için dizin eşitleme sorunlarını giderme](fix-problems-with-directory-synchronization.md) makalesine bakın. 
  
Gerekirse iş ürünleri için [desteğe başvurun](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
  
## <a name="turn-off-directory-synchronization"></a>Dizin eşitlemeyi kapatma  
Dizin eşitlemesini kapatmak için:
  
1. İlk olarak gerekli yazılımı yükleyin ve Microsoft 365 aboneliğinize bağlanın. Yönergeler için bkz[. Windows PowerShell için Microsoft Azure Active Directory Modülü ile Bağlan](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Dizin eşitlemesini devre dışı bırakmak için [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) kullanın: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Bu komutu kullanırsanız, dizin eşitlemesini yeniden açabilmeniz için 72 saat beklemeniz gerekir.
>
