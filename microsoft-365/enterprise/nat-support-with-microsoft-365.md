---
title: Nat desteği ve Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: Bu makalede, NAT kullanarak kuruluşta IP adresi başına kullanabileceğiniz istemci sayısını yaklaşık olarak nasıl kullanabileceğiniz hakkında ayrıntılar sunulmaktadır.
ms.openlocfilehash: 5335ac87bb579b6cb00e1387da97dd5a1d4f6c7f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984462"
---
# <a name="nat-support-with-office-365"></a>Nat desteği ve Office 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Daha önce kılavuzda, Office 365 bağlantı noktasına bağlanmak için IP adresi başına Exchange istemci sayısı üst sayısının yaklaşık 2.000 istemci olması önerildi.
  
## <a name="why-use-nat"></a>Neden NAT kullanasınız?

NAT kullanarak şirket ağı kullanan binlerce kişi, genel olarak yönlendirilebilir birkaç IP adresini "paylaşabilir".
  
Çoğu şirket ağı özel (RFC1918) IP adresi alanı kullanır. Özel adres alanı İnternet Atanmış Numaralar Yetkilisi (IANA) tarafından atanır ve yalnızca genel İnternet'e veya İnternet'e doğrudan yönlendir yapmayan ağlara yöneliktir.
  
Özel bir IP adresi alanı içinde yer alan cihazlara İnternet erişimi sağlamak için kuruluşlar, ağ adresi çevirisi (NAT) veya bağlantı noktası adresi çevirisi (PAT) hizmetleri sağlayan güvenlik duvarları ve ara sunucu gibi ağ geçidi teknolojileri kullanır. Bu ağ geçitleri, iç cihazlardan İnternet'e gelen trafiğin (Office 365 dahil) bir veya birden çok genel olarak yönlendirilebilir IP adreslerinden geliyor gibi görünmesini sağlar. Bir iç cihazdan giden her bağlantı, genel IP adresi üzerinde farklı bir kaynak TCP bağlantı noktasına çevrilir. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Aynı anda neden çok sayıda bağlantının aynı anda Office 365 olması gerekiyor?

Outlook veya daha fazla bağlantı açabilirsiniz (eklentilerin, paylaşılan takvimlerin, posta kutularının vb. olduğu durumlar). Windows tabanlı NAT aygıtında kullanılabilen en çok 64.000 bağlantı noktası olduğundan, bağlantı noktaları tüketmeden önce IP adresinin arkasında en çok 8.000 kullanıcı olabilir. Müşterilerin NAT için işletim sistemi Windows tabanlı olmayan cihazlar kullandığında, kullanılabilir toplam bağlantı noktalarının kullanılan NAT cihazına veya yazılımına bağımlı olduğunu unutmayın. Bu senaryoda, en fazla bağlantı noktası sayısı 64.000'den az olabilir. Bağlantı noktalarının kullanılabilirliği, Windows 4.000 bağlantı noktasını kendi kullanımı için kısıtlama gibi diğer faktörlerden de etkilenir ve bu da kullanılabilir bağlantı noktalarının toplam sayısını 60.000'e düşürer. Aynı anda bağlanan ve ek bağlantı noktaları gerektiren Internet Explorer gibi başka uygulamalar da olabilir.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Tek bir genel IP adresinin arkasındaki en fazla desteklenen cihaz ve Office 365

Tek bir genel IP adresi arkasında en fazla cihaz sayısını belirlemek için istemci başına tepe bağlantı noktası tüketimini belirlemek üzere ağ trafiğini izlemelisiniz. Ayrıca bağlantı noktası kullanımı için tepe faktörü kullanılabilir (en az 4). 
  
 **IP adresi başına desteklenen cihaz sayısını hesaplamak için aşağıdaki formülü kullanın:**
  
Tek bir genel IP adresi arkasında desteklenen en fazla cihaz sayısı = (64.000 - kısıtlanmış bağlantı noktaları)/(Tepe bağlantı noktası tüketimi + tepe faktörü)
  
 **Örneğin, aşağıdakiler doğruysa:**
  
- **Kısıtlı bağlantı noktaları:** İşletim sistemi için 4.000

- **Tepe bağlantı noktası tüketimi:** Cihaz başına 6

- **Tepe faktörü:** 4

Ardından, tek bir genel IP adresinin arkasındaki en fazla desteklenen cihaz sayısı = (64.000 - 4.000)/(6 + 4) = 6.000
  
Office 365 barındırma paketinin yayım tarihi, Microsoft Office Outlook 2007'ye yönelik Eylül 2011 veya Microsoft Outlook 2010 için Kasım 2011 güncelleştirmelerine veya daha sonraki bir güncelleştirmeye dahil edilen sürümlerde, Outlook'tan gelen bağlantı sayısı (her ikisi de Office Outlook 2007 Service Pack 2 ve Outlook 2010) Exchange kadar 2 olabilir. Ağ bağlantı noktasının tepede gereksinecek en düşük ve en fazla bağlantı noktası sayısını belirlemek için farklı işletim sistemlerinde, kullanıcı davranışlarında, bu gibi çeşitli işlemlerde faktöre ihtiyacınız vardır.
  
Tek bir genel IP adresi arkasında daha fazla cihazı desteklemek için desteklenecek en fazla cihaz sayısını değerlendirmek için verilen adımları izleyin:
  
İstemci başına tepe bağlantı noktası tüketimini belirlemek üzere ağ trafiğinin izlenmesi. Bu verileri toplamalısiniz:
  
- Birden fazla konumdan
    
- Birden fazla cihaza
    
- Birden çok kez
    
Ortamında desteklanacak IP adresi başına en fazla kullanıcı sayısı hesaplamak için yukarıdaki formülü kullanın.
  
Ek genel IP adreslerinde istemci yükünü dağıtmak için çeşitli yöntemler vardır. Kullanılabilir stratejiler şirket ağ geçidi çözümünün özelliklerine bağlıdır. En basit çözüm, kullanıcı adresi alanınızı bölümlemeniz ve her ağ geçidine statik olarak çok sayıda IP adresi "atamaktır". Çok sayıda ağ geçidi cihazı için bir diğer alternatif de bir IP adresi havuzu kullanma olanağıdır. Adres havuzun avantajı, çok daha dinamik olması ve kullanıcı tabanınız arttıkça daha az düzeltme gerektirmesidir.
  
## <a name="see-also"></a>Ayrıca bkz.

[Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
