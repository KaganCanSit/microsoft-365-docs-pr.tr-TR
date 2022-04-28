---
title: Office 365 ile NAT desteği
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, NAT kullanarak kuruluşunuzda IP adresi başına kullanabileceğiniz istemci sayısına yaklaşık olarak nasıl bağlanabileceğiniz hakkında ayrıntılar sağlanır.
ms.openlocfilehash: 71c9d54ddf88d9b69c890609fea7ece8cac0de33
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097392"
---
# <a name="nat-support-with-office-365"></a>Office 365 ile NAT desteği

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Daha önce kılavuz, Office 365 bağlanmak için IP adresi başına kullanmanız gereken en fazla Exchange istemcisi sayısının ağ bağlantı noktası başına yaklaşık 2.000 istemci olduğunu belirtmişti.
  
## <a name="why-use-nat"></a>NAT neden kullanılır?

NAT kullanarak, şirket ağındaki binlerce kişi genel olarak yönlendirilebilen birkaç IP adresini "paylaşabilir".
  
Çoğu kurumsal ağ özel (RFC1918) IP adresi alanı kullanır. Özel adres alanı, İnternet Atanan Numaralar Yetkilisi (IANA) tarafından ayrılır ve yalnızca doğrudan genel İnternet'e ve İnternet'ten yönlendirilmeyen ağlara yöneliktir.
  
Kuruluşlar, özel IP adresi alanındaki cihazlara İnternet erişimi sağlamak için ağ adresi çevirisi (NAT) veya bağlantı noktası adresi çevirisi (PAT) hizmetleri sağlayan güvenlik duvarları ve proxy'ler gibi ağ geçidi teknolojilerini kullanır. Bu ağ geçitleri iç cihazlardan İnternet'e giden trafiğin (Office 365 dahil) bir veya daha fazla genel olarak yönlendirilebilir IP adreslerinden geldiğini gösterir. Bir iç cihazdan giden her bağlantı, genel IP adresinde farklı bir kaynak TCP bağlantı noktasına çevrilir. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Office 365 için aynı anda neden bu kadar çok bağlantı açmanız gerekiyor?

Outlook sekiz veya daha fazla bağlantı açabilir (eklentilerin, paylaşılan takvimlerin, posta kutularının vb. olduğu durumlarda). Windows tabanlı bir NAT cihazında en fazla 64.000 bağlantı noktası olduğundan, bağlantı noktaları tükenmeden önce IP adresinin arkasında en fazla 8.000 kullanıcı olabilir. Müşteriler NAT için Windows işletim sistemi tabanlı olmayan cihazlar kullanıyorsa, kullanılabilir toplam bağlantı noktalarının hangi NAT cihazının veya yazılımının kullanıldığına bağlı olduğunu unutmayın. Bu senaryoda maksimum bağlantı noktası sayısı 64.000'den az olabilir. Bağlantı noktalarının kullanılabilirliği, 4.000 bağlantı noktasını kendi kullanımı için kısıtlamak Windows gibi diğer faktörlerden de etkilenir ve bu da toplam kullanılabilir bağlantı noktası sayısını 60.000'e düşürür. Internet Explorer gibi aynı anda bağlanabilen ve ek bağlantı noktaları gerektiren başka uygulamalar da olabilir.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Office 365 ile tek bir genel IP adresinin arkasında desteklenen en fazla cihazı hesaplama

Tek bir genel IP adresinin arkasındaki en fazla cihaz sayısını belirlemek için, istemci başına en yüksek bağlantı noktası tüketimini belirlemek için ağ trafiğini izlemeniz gerekir. Ayrıca, bağlantı noktası kullanımı için en yüksek faktör (en az 4) kullanılmalıdır. 
  
 **IP adresi başına desteklenen cihaz sayısını hesaplamak için aşağıdaki formülü kullanın:**
  
Tek bir genel IP adresi arkasında desteklenen en yüksek cihaz sayısı = (64.000 - kısıtlı bağlantı noktaları)/(Tepe bağlantı noktası tüketimi + tepe faktörü)
  
 **Örneğin, aşağıdakiler doğruysa:**
  
- **Kısıtlı bağlantı noktaları:** İşletim sistemi için 4.000

- **En yüksek bağlantı noktası tüketimi:** Cihaz başına 6

- **Tepe faktörü:** 4

Ardından, tek bir genel IP adresi = (64.000 - 4.000)/(6 + 4) = 6.000'in arkasında desteklenen en fazla cihaz
  
Microsoft Office Outlook 2007 için Eylül 2011 veya Microsoft Outlook 2010 için Kasım 2011 güncelleştirmelerinde yer alan Office 365 barındırma paketinin yayımlanmasıyla birlikte, Outlook bağlantı sayısı (her ikisi de Office Outlook 2007 Service Pack 2 ve Outlook 2010) Exchange 2'ye kadar olabilir. Ağınızın en yüksek düzeyde ihtiyaç duyacağı en düşük ve en fazla bağlantı noktası sayısını belirlemek için farklı işletim sistemlerini, kullanıcı davranışlarını vb. dikkate almanız gerekir.
  
Tek bir genel IP adresinin arkasında daha fazla cihaz desteklemek istiyorsanız, desteklenebilen en fazla cihaz sayısını değerlendirmek için ana hatlarıyla verilen adımları izleyin:
  
İstemci başına en yüksek bağlantı noktası tüketimini belirlemek için ağ trafiğini izleyin. Bu verileri toplamanız gerekir:
  
- Birden çok konumdan
    
- Birden çok cihazdan
    
- Birden çok kez
    
Ortamlarında desteklenecek IP adresi başına en fazla kullanıcı sayısını hesaplamak için yukarıdaki formülü kullanın.
  
İstemci yükünü ek genel IP adresleri arasında dağıtmak için çeşitli yöntemler vardır. Kullanılabilir stratejiler, kurumsal ağ geçidi çözümünün özelliklerine bağlıdır. En basit çözüm, kullanıcı adresi alanınızı segmentlere ayırmak ve her ağ geçidine statik olarak bir dizi IP adresi atamaktır. Birçok ağ geçidi cihazının sunduğu bir diğer alternatif de IP adresleri havuzunu kullanabilmektir. Adres havuzunun avantajı, kullanıcı tabanınız büyüdükçe çok daha dinamik ve ayarlama gerektirme olasılığının daha düşük olmasıdır.
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
