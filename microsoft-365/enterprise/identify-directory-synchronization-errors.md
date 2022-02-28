---
title: Dizinde dizin eşitlemesi hatalarını Microsoft 365
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
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Dizin eşitleme hatalarını ve olası düzeltmeleri görüntülemeyi öğrenin ve Microsoft 365 yönetim merkezi.
ms.openlocfilehash: 2b832cff65aad0ae7327f440a565e12c7cba66f4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986718"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Dizinde dizin eşitlemesi hatalarını Microsoft 365

Dizin eşitlemesi hatalarını, aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi.</a> Yalnızca User nesnesi hataları görüntülenir. PowerShell ile hataları görüntülemek için bkz [. DirSyncProvisioningErrors ile nesneleri tanımlama](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Dizin eşitlemesi hatalarını Microsoft 365 yönetim merkezi

Hata varsa görüntülemek Microsoft 365 yönetim merkezi:
  
1. E-posta [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) genel yönetici hesabıyla oturum açın. 
    
2. Giriş **sayfasında** , Kullanıcı yönetimi **kartını görebilirsiniz** . 
    
    ![Kullanıcının kullanıcı yönetimi Microsoft 365 yönetim merkezi.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Kartta, Dizin **eşitleme hataları sayfasında** hataları görmek için **Azure AD Bağlan** hataları **eşitle'yi** seçin.   
    
    ![Dizin eşitleme hataları sayfasına bir örnek.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Hatayla ilgili bilgilerin ve düzeltme ipuçlarının olduğu ayrıntılar bölmesini görüntülemek için hatalardan birini seçin.

   ![Dizin eşitleme hatasının ayrıntıları örneği.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Görüntüden sonra, [tanımlanan sorunları düzeltmek için bkz. Microsoft 365](fix-problems-with-directory-synchronization.md) eşitleme sorunlarını giderme.