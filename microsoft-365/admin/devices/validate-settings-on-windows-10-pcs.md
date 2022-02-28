---
title: Bilgisayarlar için uygulama koruma Windows 10 doğrulama
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: İşletmeler için Microsoft 365 koruma ayarlarının kullanıcılarınızı ve cihazlarınızı etkileyeni doğrulamayı Windows 10 öğrenin.
ms.openlocfilehash: 311da3efec8cd3ad57e722aea5a8c3888d1af7b0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983842"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Bilgisayarlar için cihaz koruma Windows 10 doğrulama

## <a name="verify-that-windows-10-device-policies-are-set"></a>Cihaz ilkelerinin Windows 10 ayar olduğunu doğrulama

Cihaz [ilkelerini ayarladikten](protection-settings-for-windows-10-pcs.md) sonra, ilkenin kullanıcıların cihazlarında etkiliksi birkaç saat sürebilir. İlkelerin, kullanıcıların cihazlarında çeşitli ekranlara Windows Ayarlar ilkelerin etkili olduğunu onaylayın. Kullanıcılar mobil cihazlarında Güncelleştirme Windows ve Windows Defender Virüsten Koruma ayarlarını değiştire Windows 10, birçok seçenek gri görünür.
  
1. Şu **ayarlara Ayarlar** \> **Update &amp; Windows** \> **Yeniden** \> **Başlatma seçenekleri'ne** gidin ve tüm ayarların gri renkte görüntü olduğunu onaylayın. 
    
    ![Yeniden başlatma seçeneklerinin tüm seçenekleri gri gösterilir.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Gelişmiş seçenekleri  **Ayarlar'e &amp;** \> **Windows'e** \> \> **gidin** ve tüm ayarların gri renkte görüntü olduğunu onaylayın. 
    
    ![Windows güncelleştirme seçeneklerinin hepsi gri gösterilir.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Güncelleştirme **Ayarlar-Posta** \> **Windows &amp;** \> **Güncelleştirme Gelişmiş seçenekleri** \> **Güncelleştirmelerin** \> **nasıl teslim edileceklerini seçin**.
    
    Bazı ayarların kuruluş tarafından gizlenmiş veya yönetilen bir ileti (kırmızı renkle) olduğunu ve tüm seçeneklerin gri renkte olduğunu onaylayın.
    
    ![Güncelleştirmelerin nasıl teslim edileceklerini seçin sayfası ayarların kuruluş tarafından gizlendi veya yönetiliyor olduğunu gösterir.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Güvenlik Merkezi'Windows Defender açmak için güvenlik **Ayarlar** \> **&amp;** \> Güncelleştirme'ye **Windows Defender** \> **Windows Defender** \> **&amp;** \> **&amp;** Virüsten Koruma Virüs tehdit koruması ayarlarını aç'a tıklayın. 
    
5. Tüm seçeneklerin gri renkte olduğunu doğrulayın. 
    
    ![Virüs ve tehdit koruması ayarları gri görünür.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>İlgili içerik

[Microsoft 365 belgeleri ve kaynakları için belgeler](/admin)\
[Windows 10 bilgisayarlarında cihaz yapılandırmalarını ayarlama](protection-settings-for-windows-10-pcs.md)
