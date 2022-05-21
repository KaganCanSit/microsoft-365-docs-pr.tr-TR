---
title: Office 365 hizmetlerine bağlanan ağ cihazlarını planlama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Özet: Office 365 bağlanmak için kullanılan ağ kapasitesi, WAN hızlandırıcıları ve yük dengeleme cihazlarıyla ilgili dikkat edilmesi gereken noktaları açıklar.'
ms.openlocfilehash: 3b79e73f292ecf1db38a90364db3d2e475723158
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622821"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 hizmetlerine bağlanan ağ cihazlarını planlama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*
  
Bazı ağ donanımlarının desteklenen eşzamanlı oturum sayısıyla ilgili sınırlamaları olabilir. 2.000'den fazla kullanıcısı olan kuruluşlar için ek Office 365 hizmet trafiğini işleyebilmelerini sağlamak için ağ cihazlarını izlemelerini öneririz. Basit Ağ Yönetimi Protokolü (SNMP) izleme yazılımı bunu yapmanıza yardımcı olabilir.

Bu makale, [Office 365 için ağ planlama ve performans ayarlamanın](./network-planning-and-performance.md) bir parçasıdır.

Şirket içi giden İnternet proxy ayarları, istemci uygulamalarınız için Office 365 hizmetlerine bağlantıyı da etkiler. Ayrıca, ağ proxy cihazlarınızı Microsoft bulut hizmetleri URL'leri ve uygulamaları için bağlantılara izin verecek şekilde yapılandırmanız gerekir. Her kuruluş farklıdır. Microsoft'un bu süreci nasıl yönettiği ve sağladığımız bant genişliği miktarı hakkında fikir edinmek için [örnek olay incelemesini okuyun](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Aşağıdaki Skype Kurumsal Yardım makalelerinin Skype Kurumsal ayarları hakkında daha fazla bilgi vardır:
  
- [Yöneticiler için Skype Kurumsal Çevrimiçi oturum açma hatalarını giderme](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Şirket içi güvenlik duvarı bağlantıyı engellediğinden Skype Kurumsal bağlanamazsınız veya bazı özellikler çalışmaz](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Bu ayarların çoğu Skype Kurumsal özgü olsa da, ağ yapılandırmasıyla ilgili genel yönergeler tüm Office 365 hizmetleri için yararlıdır.
  
## <a name="determining-network-capacity"></a>Ağ Kapasitesini Belirleme

Bir bağlantıda bulunan her ağ cihazının kapasite sınırı vardır. Bu cihazlar arasında birbirine bağlanan istemci ve sunucu ağ bağdaştırıcıları, yönlendiriciler, anahtarlar ve hub'lar bulunur. Yeterli ağ kapasitesi, hiçbirinin doygun olmadığını gösterir. Ağ etkinliğinin izlenmesi, tüm ağ cihazlarında gerçek yüklerin maksimum kapasiteden daha az olduğundan emin olmak için gereklidir. Ağ kapasitesi ara sunucu cihazı performansını etkiler.
  
Çoğu durumda, İnternet bağlantısı bant genişliği trafik miktarının sınırını ayarlar. Yoğun trafik saatlerinde zayıf performans, büyük olasılıkla İnternet bağlantısının aşırı kullanımından kaynaklanır. Bu durum, şube ofisi ara sunucu bilgisayarlarının şubenin genel merkezindeki ara sunucu cihazına yavaş bir Geniş Alan Ağı (WAN) bağlantısı üzerinden bağlandığı bir şube ofisi senaryosu için de geçerlidir.
  
Ağ kapasitesini test etmek için ara sunucu ağ arabirimindeki ağ etkinliğini izleyin. Herhangi bir ağ arabiriminin bant genişliği üst sınırının yüzde 75'inden fazlaysa, yetersiz olan ağ altyapısının bant genişliğini artırmayı göz önünde bulundurun. Alternatif olarak, HTTP sıkıştırma gibi gelişmiş özellikleri de kullanmayı göz önünde bulundurun.
  
## <a name="wan-accelerators"></a>WAN Hızlandırıcıları

Kuruluşunuz geniş alan ağı (WAN) hızlandırma proxy gereçleri kullanıyorsa, Office 365 hizmetlerine eriştiğinizde sorunlarla karşılaşabilirsiniz. Kullanıcılarınızın Office 365 erişirken tutarlı bir deneyime sahip olduğundan emin olmak için ağ cihazınızı veya cihazlarınızı iyileştirmeniz gerekebilir. Örneğin, Office 365 hizmetler bazı Office 365 içeriğini ve TCP üst bilgisini şifreler. Cihazınız bu tür trafiği işleyemeyebilir.
  
[OFFICE 365 ile WAN İyileştirme Denetleyicisi veya Trafik/İnceleme cihazlarını kullanma hakkındaki](https://support.microsoft.com/kb/2690045) destek bildirimimizi okuyun.
  
## <a name="hardware-and-software-load-balancing-devices"></a>Donanım ve Yazılım Yük Dengeleme Cihazları

Kuruluşunuzun, istekleri Active Directory Federasyon Hizmetleri (AD FS) (AD FS) sunucularınıza ve/veya Exchange karma sunucularınıza dağıtmak için bir donanım yük dengeleyici (HLB) veya Ağ Yükü Dengeleme (NLB) çözümü kullanması gerekir. Yük dengeleme cihazları, şirket içi sunuculara yönelik ağ trafiğini denetler. Bu sunucular, çoklu oturum açma ve karma dağıtım Exchange kullanılabilirliğini sağlamaya yardımcı olması açısından çok önemlidir.
  
Windows Server'da yerleşik olarak bulunan yazılım tabanlı bir NLB çözümü sunuyoruz. Office 365, yük dengeleme gerçekleştirmek için bu çözümü destekler.
  
## <a name="firewalls-and-proxies"></a>Güvenlik duvarları ve proxy'ler

güvenlik duvarlarını ve proxy'leri Office 365 bağlanacak şekilde yapılandırma hakkında daha fazla bilgi için cihazlar ve bağlantı hattı seçimi hakkında daha fazla bilgi edinmek için [Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md) ve [Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) bölümünü okuyun.
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 hizmetleri için kurulum kılavuzları](setup-guides-for-microsoft-365.md)

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)