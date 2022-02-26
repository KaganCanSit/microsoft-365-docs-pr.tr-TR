---
title: Office 365 hizmetlerine bağlanan ağ cihazlarını planlama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Ağ kapasitesi, WAN hızlandırıcıları ve yük dengeleme cihazlarına bağlanmak için dikkate alınması gereken noktalar Office 365.'
ms.openlocfilehash: 38df9a64610c4b4d44014a142bf7d255aa0a0f46
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973717"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 hizmetlerine bağlanan ağ cihazlarını planlama

*Bu makale hem diğer Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*
  
Bazı ağ donanımlarında, desteklenen eş zamanlı oturum sayısında sınırlandırma olabilir. Kullanıcı sayısı 2.000'i geçen kuruluşlarda, ek kullanıcı hizmeti trafiğiyle başaabileceklerinden emin olmak için ağ cihazlarını izlemelerini Office 365 öneririz. Basit Ağ Yönetimi Protokolü (SNMP) izleme yazılımı bunu yapmaya yardımcı olabilir.

Bu makale, proje ayarları [için ağ planlaması ve performans Office 365](./network-planning-and-performance.md).

Şirket içi giden İnternet ara sunucu ayarları, istemci uygulamalarınız için Office 365 bağlantınızı da etkiler. Ayrıca, ağ ara sunucu cihazlarınızı Microsoft bulut hizmetleri URL'leri ve uygulamalarına bağlantılara izin verecek şekilde yapılandırmanız gerekir. Her kuruluş farklıdır. Microsoft'un bu süreci nasıl yönet olduğu ve ne kadar bant genişliği sağlar? hakkında fikir almak için, [örnek olay incelemeyi okuyun](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Aşağıdaki Yardım Skype Kurumsal, güvenlik ayarları hakkında daha fazla Skype Kurumsal içerir:
  
- [Yöneticiler Skype Kurumsal Çevrimiçi oturum açma hatalarında sorun giderme](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Şirket içi güvenlik Skype Kurumsal bağlantıyı engellemesi nedeniyle, Skype Kurumsal'e bağlanamazsanız veya bazı özellikler işe yaramadı](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Bu ayarların birçoğu özel Skype Kurumsal, ağ yapılandırmasıyla ilgili genel kılavuz, diğer hizmetlerde Office 365 yarar.
  
## <a name="determining-network-capacity"></a>Ağ Kapasitesi Belirleme

Bağlantıda olan her ağ aygıtının kendi kapasite sınırı vardır. Bu cihazlar istemci ve sunucu ağ bağdaştırıcıları, yönlendiriciler, anahtarlar ve bunları birbirine bağlı hub'lardan içerir. Yeterli ağ kapasitesi, hiçbirinin fazla doymamış olması anlamına gelir. Tüm ağ cihazlarına gerçek yüklerin maksimum kapasitenin altında olduğundan emin olmak için ağ etkinliğini izlemek çok önemlidir. Ağ kapasitesi ara sunucu cihaz performansını etkiler.
  
Çoğu durumda, trafik miktarının sınırını İnternet bağlantısı bant genişliği ayarlar. Trafiğin en yoğun olduğu saatlerinde performansın düşük nedeni büyük olasılıkla İnternet bağlantısının aşırı kullanımıdır. Bu durum, şube ara sunucu bilgisayarlarına şubenin merkezinde yavaş bir Geniş Alan Ağı (WAN) üzerinden ara sunucu cihazına bağlı olan şube senaryoları için de geçerlidir.
  
Ağ kapasitesi test etmek için, ara sunucu ağ arabiriminde ağ etkinliğini takip eder. Bu, herhangi bir ağ arabiriminin en yüksek bant genişliğinin yüzde 75'inden fazla ise, yeterli olmayan ağ altyapısının bant genişliğini artırmayı göz önünde bulundurabilirsiniz. Http sıkıştırma gibi gelişmiş özellikleri kullanmayı da düşünebilirsiniz.
  
## <a name="wan-accelerators"></a>WAN Hızlandırıcıları

Kuruluşta geniş alan ağı (WAN) hızlandırma ara sunucu cihazları kullanıyorsa, veritabanına veya hizmetlere erişen Office 365 karşılaşabilirsiniz. Kullanıcılarının posta dosyalarına erişirken tutarlı bir deneyimden emin olmak için ağ cihazınızı veya cihazlarınızı en Office 365. Örneğin, Office 365 hizmetleri bazı önemli Office 365 TCP üst bilgilerini şifreler. Cihazınız bu tür bir trafiği işlemeye devam edeyemebilir.
  
WAN İyileştirme Denetleyicisi veya Trafik/İnceleme cihazlarını farklı cihazlarla [kullanma ile ilgili destek Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Donanım ve Yazılım Yük Dengeleme Cihazları

Kuruluş, istekleri Active Directory Federasyon Hizmetleri (AD FS) sunucularınıza ve/veya karma sunucularınıza dağıtmak için bir donanım yük dengeleyicisi (HLB) veya Ağ Yükü Dengeleme (NLB) çözümü Exchange gerekir. Yük dengeleme cihazları, şirket içi sunuculara ağ trafiğini kontrol ediyor. Bu sunucular, çoklu oturum açma kullanılabilirliğini sağlamaya yardımcı olmak ve karma dağıtımı Exchange çok önemlidir.
  
Windows Server'da yerleşik olarak yazılım tabanlı bir NLB çözümü sağlaruz. Office 365 dengelemeyi başarmak için bu çözümü destekler.
  
## <a name="firewalls-and-proxies"></a>Güvenlik duvarları vexies

Office 365'a bağlanırken güvenlik duvarlarını ve aracıları yapılandırma hakkında daha fazla ayrıntı için, cihazlar ve devre seçimi hakkında daha fazla bilgi edinmek için [Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) uç noktalarını yönetme, [Office 365](assessing-network-connectivity.md) ağ bağlantısını değerlendirme ve Office 365 uç noktaları [SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) bölümünü okuyun.
  
## <a name="see-also"></a>Ayrıca bkz.

[Kurulum kılavuzları Office 365 hizmetleri](setup-guides-for-microsoft-365.md)

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)