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
ms.openlocfilehash: be25acb8414705c48a8763a0530ec2a70565de83
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313601"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Bilgisayarlar için cihaz koruma Windows 10 doğrulama

> [!NOTE]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Cihaz ilkelerinin Windows 10 ayar olduğunu doğrulama

Cihaz [ilkelerini ayarladikten](protection-settings-for-windows-10-pcs.md) sonra, ilkenin kullanıcıların cihazlarında etkiliksi birkaç saat sürebilir. İlkelerin, kullanıcıların cihazlarında çeşitli ekranlara Windows Ayarlar ilkelerin etkili olduğunu onaylayın. Kullanıcılar mobil cihazlarında Windows Update Microsoft Defender Virüsten Koruma ayarlarını değiştire Windows 10, çoğu seçenek gri görünür.
  
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
[PC'lerde cihaz Windows 10 yapılandırmalarını ayarlamaİsneden](protection-settings-for-windows-10-pcs.md)
 [iş planları için güvenlik Microsoft 365 10 yolu](../security-and-compliance/secure-your-business-data.md)