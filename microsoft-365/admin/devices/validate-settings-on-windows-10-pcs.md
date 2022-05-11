---
title: Windows 10 bilgisayarlar için uygulama koruma ayarlarını doğrulama
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
description: İş için Microsoft 365 uygulama koruma ayarlarının kullanıcılarınızın Windows 10 cihazları üzerinde etkili olduğunu doğrulamayı öğrenin.
ms.openlocfilehash: cbb26461da9fcc73f57d219c36ef04d97e7fc209
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317563"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Windows 10 bilgisayarlar için cihaz koruma ayarlarını doğrulama

> [!NOTE]
> İş için Microsoft Defender, 1 Mart 2022'de başlayarak Microsoft 365 İş Ekstra müşterilerine dağıtılıyor. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi edinin](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Windows 10 cihaz ilkelerinin ayarlandığını doğrulayın

[Cihaz ilkelerini ayarladıktan](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md) sonra, ilkenin kullanıcıların cihazlarında etkili olması birkaç saat kadar sürebilir. Kullanıcıların cihazlarında çeşitli Windows Ayarlar ekranlarına bakarak ilkelerin geçerli olduğunu onaylayabilirsiniz. Kullanıcılar Windows 10 cihazlarında Windows Update ve Microsoft Defender Virüsten Koruma ayarlarını değiştiremeyeceğinden, birçok seçenek gri görünür.
  
1. **Ayarlar** \> Güvenliği \> **güncelleştir &amp;** **Windows Update** \> **Yeniden başlatma seçenekleri'ne** gidin ve tüm ayarların gri olduğunu onaylayın.

    ![Tüm Yeniden Başlatma seçenekleri gri görünür.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. **Ayarlar** \> Güvenliği \> **güncelleştir &amp;** **Windows Update** \> **Gelişmiş seçenekler'e** gidin ve tüm ayarların gri olduğunu onaylayın.

    ![Windows Gelişmiş güncelleştirme seçeneklerinin tümü gri görünür.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. **Ayarlar** \> **Güncelleştirme &amp; güvenliği** \> **Windows Update** \> **Gelişmiş seçenekler** \> **Güncelleştirmelerin nasıl teslim edilir seçin** bölümüne gidin.

    Bazı ayarların kuruluşunuz tarafından gizlendiğini veya yönetildiğini ve tüm seçeneklerin gri olduğunu belirten iletiyi (kırmızı) görebildiğinizi onaylayın.

    ![Güncelleştirmelerin nasıl teslimileceğini seçin sayfası, ayarların kuruluşunuz tarafından gizlendiğini veya yönetildiğini gösterir.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Windows Defender Güvenlik Merkezi'ni açmak için **Ayarlar** \> **Güvenliği güncelleştir'e &amp;** \> gidin **Windows Defender** \> **Windows Defender Güvenlik Merkezi** \> **Virüs iş parçacığı koruması Virüs &amp;** **&amp; tehdit koruması**\> ayarlarını aç'a tıklayın.

5. Tüm seçeneklerin gri renkte olduğunu doğrulayın.

    ![Virüs ve tehdit koruması ayarları gri görünür.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>İlgili içerik

[İş belgeleri ve kaynakları için Microsoft 365](/admin)

[Windows 10 pc'ler](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 için cihaz yapılandırmalarını ayarlama İş [planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](../../admin/security-and-compliance/secure-your-business-data.md)
