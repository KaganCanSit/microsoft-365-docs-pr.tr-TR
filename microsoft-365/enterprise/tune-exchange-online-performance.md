---
title: Performans Exchange Online ayarlama
ms.author: krowley
author: tracyp
manager: laurawi
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
description: Bu makale, çalışma performanslarını iyileştirmeyle ilgili genel ipuçları ve diğer Exchange Online.
ms.openlocfilehash: 5feb704a1da83ef93ebc3bbe72fb12c7f0c54574
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988121"
---
# <a name="tune-exchange-online-performance"></a>Performans Exchange Online ayarlama

Bu makale, özellikle de geçiş işleminin önünde performans iyileştirmeyle ilgili genel ipuçları Exchange Online bağlantılar içerir. Bu makale, Projeniz için [ağ planlaması ve performans ayarı Office 365](./network-planning-and-performance.md) bölümüyle hazırlanmıştır.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Performans iyileştirme için dikkat Exchange Online.

Geçiş hızını artırmak ve işlerinizi geliştirmek için, aşağıdakilere dikkat Exchange Online:
  
- **Posta kutusu boyutlarını azaltma.** Posta kutusunun daha küçük boyutlu olması, geçiş hızını iyiler. 
    
- **Karma bir dağıtımda posta kutusu taşıma Exchange kullanın.** Karma Exchange, çevrimdışı posta (of. OST dosyaları) dosya başka bir klasöre Exchange Online. Bu, indirme bant genişliği gereksinimlerini önemli ölçüde azaltır. 
    
- **Posta kutusu hareketlerini, İnternet trafiğinin az olduğu ve şirket içi veya iş yerinde kullanımın düşük olduğu dönemlere Exchange zamanlamayın.** Taşımaları zamanlaması sırasında geçiş istekleri, posta kutusu çoğaltma ara sunucusuna gönderilen ve hemen yer almayan bir durumla karşıtlik sağlar. 
    
- **E-posta için yalın açılır Web üzerinde Outlook.** Yalın açılan menüler, sunucu üzerinde bazı bileşenleri işerek Microsoft Edge Internet Explorer'da bazı e-posta iletilerinin daha küçük, daha az yoğun bellek kullanımına yönelik sürümlerini sağlar. Daha fazla bilgi için bkz [. E-posta iletilerini okurken kullanılan belleği azaltmak için yalın açılır pencereleri kullanma](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Genel öneriler

- KONUMUZ için DNS arama outlook.office.com MS-datacenterne konumunuz için mantıksal bir giriş konumu girebilirsiniz.

- Posta kutusunu önbelleğe alma ve uygun seçenekleri (re. önbelleğe alma süresi, paylaşılan posta kutusu önbelleğe alma, vb.

- İnternet Outlook gitmeden önce ağ bağlantılarınızı VPN bağlantılarından (merkezi bir ofislere) geçirmenizi sağlar.

- Posta kutusu verilerinizin klasör ve öğe miktarları ile ilgili sınırlamalara bağlı olduğundan emin olun.
    
Geçiş performansını yükseltme hakkında Exchange için bkz. [Geçiş Office 365 ve en iyi yöntemler](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
