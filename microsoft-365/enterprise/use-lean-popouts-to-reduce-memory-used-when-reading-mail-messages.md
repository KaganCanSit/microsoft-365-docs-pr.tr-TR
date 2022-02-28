---
title: Posta iletilerini okurken kullanılan belleği azaltmak için yalın açılır pencereleri kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Bu makale, bu makalede ileti indirme performansını geliştirmek için yalın açılır pencereleri kullanma Web üzerinde Outlook.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaacacc0c1db418181690a5a4691bd251180d97c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985143"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Posta iletilerini okurken kullanılan belleği azaltmak için yalın açılır pencereleri kullanma

Bu makale, çalışma sayfalarında ileti indirme performansını iyileştirme Web üzerinde Outlook. Bu makale, Projeniz için [ağ planlaması ve performans ayarı Office 365](./network-planning-and-performance.md) bölümüyle hazırlanmıştır.
  
Office 365 **Uygulama** **Yöneticisi, Genel** yönetici veya Kullanıcı Yöneticisi **olarak, Web üzerinde Outlook** Microsoft Edge veya Internet Explorer'da belirli e-posta iletilerinin daha _küçük, daha_ az yoğun bellek kullanımlı sürümü gibi bilgili açılır iletiler sunmak için Microsoft Edge'ı yapılandırabilirsiniz. Açılan menüler daha iyi Web üzerinde Outlook, sunucu tarafı işlenmiş bileşenleri en iyi duruma getirmek için yüklenir.
  
> [!NOTE]
> Mart 2018'den sonra, kullanım hakları kısıtlamaları belirten, Bilgi Hakları Yönetimi (IRM) gibi iletilerde yalın açılan menüler kullanılamaz.
  
Bu özellikler ana pencerede çalışmaya devam eder ancak yalın açılır pencerelerde kullanılamaz:
  
- Outlook eklentileri
  
- Skype Kurumsal durumu
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Kuruluş kapsamındaki tüm kullanıcılar için yalın açılır pencereleri Office 365 için
  
1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) cmdlet'ini Aşağıdaki gibi LeanPopoutEnabled parametresiyle çalıştırın:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Örneğin, kuruluşun tüm kullanıcıları için yalın açılır pencereleri etkinleştirmek için:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Kuruluş 2013'te açılan pencereleri devre dışı bırakmak için:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
