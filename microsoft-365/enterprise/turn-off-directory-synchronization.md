---
title: Etki alanı için dizin eşitlemesini Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, powershell kullanarak bu makalede dizin eşitlemesini kapatma hakkında bilgi Microsoft 365.
ms.openlocfilehash: 83a3d66493994800a71a1910332a5eb2cdb003cd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988727"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Etki alanı için dizin eşitlemesini Microsoft 365
Dizin eşitlemeyi kapatmak ve eşitlenmiş kullanıcılarınızı yalnızca buluta dönüştürmek için PowerShell kullanabilirsiniz. Ancak, dizin eşitlemesini kapatmanın bir sorun giderme adımı olarak kullanılması önerilmez. Dizin eşitlemesi sorunlarını gidermek için yardıma ihtiyacınız varsa, Dizin [eşitlemesi sorunlarını giderme makalesine Microsoft 365](fix-problems-with-directory-synchronization.md) bakın. 
  
[Gerekirse iş](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) ürünleri için destek ile iletişime geçin.
  
## <a name="turn-off-directory-synchronization"></a>Dizin eşitlemesini kapatma  
Dizin eşitlemesini kapatmak için:
  
1. İlk olarak, gerekli yazılımı yükleyin ve Microsoft 365 bağlanin. Yönergeler için bkz[. Bağlan için Microsoft Azure Active Directory Modülü ile Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Dizin [eşitlemesini devre dışı bırakmak için Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) kullanın: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Bu komutu kullanırsanız, dizin eşitlemesini yeniden açmak için 72 saat beklemeniz gerekir.
>
