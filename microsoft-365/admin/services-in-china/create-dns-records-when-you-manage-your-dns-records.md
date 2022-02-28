---
title: DNS kayıtlarınızı yönetirken Office 365 IÇIN DNS kayıtları oluşturma
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEA150
ms.assetid: 0669bf14-414d-4f51-8231-6b710ce7980b
ROBOTS: NOINDEX
description: 'DNS kayıtlarınızı yönetirken 21Vianet tarafından Office 365 DNS kayıtları oluşturma hakkında bilgi öğrenin. '
monikerRange: o365-21vianet
ms.openlocfilehash: 0b84926dbedf90752c994e76695c2d18d92fb9c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985012"
---
# <a name="create-dns-records-for-office-365-when-you-manage-your-dns-records"></a>DNS kayıtlarınızı yönetirken Office 365 IÇIN DNS kayıtları oluşturma

Posta yönlendirme için gereken MX kaydı da dahil olmak üzere 21Vianet tarafından çalıştırılan Office 365 için DNS kayıtlarını oluşturma hakkında ayrıntılı yönergeler için bkz. herhangi bir DNS barındırma sağlayıcısında [DNS Office 365](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). 
  
  
Diğer seçenekler ve dikkat gereken bazı şeyler:
      
-  Etki alanınızın DNS barındırma sağlayıcısını veya etki alanı kayıt şirketini bilmiyorsanız, bkz. [Etki alanı kayıt yetkilinizi veya DNS barındırma hizmet sağlayıcınızı bulma](../get-help-with-domains/find-your-domain-registrar.md) DNS kayıtlarının ne yaptığının açıklamaları için bkz. [DNS ile ilgili temel bilgiler](../get-help-with-domains/dns-basics.md).
    
-  Bazı DNS barındırma sağlayıcıları gereken tüm kayıt türlerini oluşturmanıza izin vermemektedir ve bu durum barındırma sağlayıcınız [SRV, CNAME, TXT](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77) veya yeniden yönlendirmeyi desteklemezken Hizmet sınırlandırmalarına neden olur. Sağlayıcınız SRV, TXT veya CNAME kayıtlarını desteklenmiyorsa, tüm gerekli kayıt türlerini destekleyen bir sağlayıcıya etki [](../get-help-with-domains/buy-a-domain-name.md) alanı [aktarmanızı öneririz](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). 
    
- Hangi DNS kayıtlarının gerekli olduğunu görmek ve e-posta için MX kaydı da dahil olmak üzere her kayıtta kullanmak üzere değerleri bulmak için bkz. DNS kayıtlarında oluşturmak için [Office 365 toplama](../get-help-with-domains/information-for-dns-records.md). DNS kayıtlarının ne yaptığının açıklamaları için bkz. [DNS ile ilgili temel bilgiler](../get-help-with-domains/dns-basics.md).
