---
title: Evet veya Hayır veren bir formüle dayalı koşullu biçimlendirme
ms.author: krowley
author: tracyp
manager: scotv
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Bu makale, Exchange Online performansını nasıl artırabileceğinizi gösteren genel ipuçları ve diğer kaynaklara bağlantılar içerir.
ms.openlocfilehash: 3b048db5e3ea5090ce5ed2391269f8167c459538
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092039"
---
# <a name="tune-exchange-online-performance"></a>Evet veya Hayır veren bir formüle dayalı koşullu biçimlendirme

Bu makale, özellikle geçişin önünde Exchange Online performansını nasıl artırabileceğinizi gösteren genel ipuçları ve diğer kaynaklara bağlantılar içerir. Bu makale, [Office 365 projesi için ağ planlama ve performans ayarlamanın](./network-planning-and-performance.md) bir parçasıdır.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Exchange Online performansını geliştirmek için dikkat edilmesi gerekenler

Geçiş hızını artırmak ve kuruluşunuzun Exchange Online bant genişliği kısıtlamalarını azaltmak için aşağıdakileri göz önünde bulundurun:
  
- **Posta kutusu boyutlarını küçültün.** Daha küçük posta kutusu boyutu, geçiş hızını artırır. 
    
- **Exchange karma dağıtımıyla posta kutusu taşıma özelliklerini kullanın.** karma Exchange dağıtımıyla, çevrimdışı posta (biçiminde). OST dosyaları) Exchange Online geçirilirken yeniden indirme gerektirmez. Bu, indirme bant genişliği gereksinimlerinizi önemli ölçüde azaltır. 
    
- **Posta kutusu taşımalarını, düşük İnternet trafiği ve düşük şirket içi Exchange kullanım dönemlerinde gerçekleşecek şekilde zamanlayın.** Taşımalar zamanlandığında, geçiş istekleri posta kutusu çoğaltma ara sunucusuna gönderilir ve hemen gerçekleşmeyebilir. 
    
- **Web üzerinde Outlook için yalın açılır pencereleri kullanın.** Yalın açılır pencereler, sunucudaki bazı bileşenleri işleyerek Microsoft Edge veya Internet Explorer'da belirli e-posta iletilerinin daha küçük, daha az bellek kullanan sürümlerini sağlar. Daha fazla bilgi için bkz. [Posta iletilerini okurken kullanılan belleği azaltmak için yalın açılır pencereleri kullanma](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Genel öneri

- outlook.office.com için DNS aramasının, konumunuz için mantıksal bir giriş konumunda MS-veri merkezine girdiğinden emin olun.

- Posta kutusunun önbelleğe alınmasını araştırın ve uygun seçenekleri belirleyin (yeniden. önbelleğe alma süresi, paylaşılan posta kutusu önbelleğe alma, vb. ).

- İnternet üzerinden geçmeden önce Outlook verilerinizin VPN bağlantıları üzerinden (merkezi bir ofise) geçmesini engelin.

- Posta kutusu verilerinizin klasör ve öğe tutarlarıyla ilgili sınırlamalara bağlı olduğundan emin olun.
    
Exchange geçiş performansı hakkında daha fazla bilgi için bkz. [geçiş performansı ve en iyi yöntemler Office 365](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
