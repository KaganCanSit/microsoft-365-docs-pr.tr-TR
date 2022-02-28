---
title: Ağ Microsoft 365 değerlendirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
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
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365, dünyanın her yerine gelen müşterilerin İnternet bağlantısı kullanarak hizmete bağlanmalarını sağlamak için tasarlanmıştır. Hizmet geliştikçe, hizmetin güvenliği, Microsoft 365 güvenilirliği, hizmete bağlantı kurmak için İnternet'i kullanan müşterilere dayalı olarak geliştir gelir.
ms.openlocfilehash: 2f982bbce4786c69034560276e5aceebaa575a00
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985555"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Ağ Microsoft 365 değerlendirme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365, dünyanın her yerine gelen müşterilerin İnternet bağlantısı kullanarak hizmete bağlanmalarını sağlamak için tasarlanmıştır. Hizmet geliştikçe, hizmetin güvenliği, Microsoft 365 güvenilirliği, hizmete bağlantı kurmak için İnternet'i kullanan müşterilere dayalı olarak geliştir gelir.
  
İnternet bağlantısını kullanmayı plan Microsoft 365 müşteriler, mevcut ve tahmin edildi internet bağlantısı müşterilerimizin dağıtım projesinin bir parçası olarak değerlendirmeleri gerekir. Güvenilir ve uygun boyuttaki İnternet bağlantısı, kurumsal sınıf dağıtımlarda çeşitli özellik ve senaryoları Microsoft 365 önemli bir kısmıdır.
  
Ağ değerlendirmeleri, boyutunuz ve tercihlerinize bağlı olarak birçok farklı kişi ve kuruluş tarafından yapılabilir. Değerlendirmenin ağ kapsamı, dağıtım işlemi sırasında bulunduğunuz yere bağlı olarak değişiklik gösterebilir. Ağ değerlendirmesini gerçekleştirmek için gerekenleri daha iyi anlamanıza yardımcı olmak için, size uygun seçenekleri anlamanıza yardımcı olacak bir ağ değerlendirmesi kılavuzu hazırlıyoruz. Bu değerlendirme, başarılı bir şekilde dağıtım projesine benimsemek için dağıtım projesine hangi adımların ve kaynakların ek gerek olacağını Microsoft 365.
  
Kapsamlı bir ağ değerlendirmesi, uygulama ayrıntılarıyla birlikte ağ tasarımı güçlükleri için olası çözümler sağlar. Bazı ağ değerlendirmeleri, var olan ağ ve İnternet çıkış Microsoft 365 küçük yapılandırma veya tasarım değişiklikleriyle en iyi ağ bağlantısının karşılayabileceğini gösterir.

Bazı değerlendirmeler, ağ bileşenlerine ağ Microsoft 365 için ek yatırımlar gerektirecek. Örneğin, şubeleri ve birden çok coğrafi bölgeyi kapsayan kurumsal ağlar, SD-WAN çözümlerine yatırım yapmak veya İnternet bağlantısının İnternet bağlantısını destekleyecek şekilde iyileştirilmiş yönlendirme altyapısına Microsoft 365. Zaman zaman bir değerlendirme, Microsoft 365 Çevrimiçi medya kalitesi gibi senaryoların düzenleme veya performans gereksinimleri tarafından etkilenin [ağ Skype Kurumsal gösterir](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Bu ek gereksinimler, İnternet bağlantısı altyapısına, yönlendirme iyileştirmeye ve özel doğrudan bağlantıya yatırımlara neden olabilir.

Anızı değerlendirmenize yardımcı olacak bazı kaynaklar:

- Ağ [Microsoft 365 hakkında kavramsal bilgiler için](microsoft-365-networking-overview.md) bkz. Ağ bağlantısına Microsoft 365 genel bakış.
- Trafiği [Microsoft 365 bir şekilde yönetmeyi ve](./microsoft-365-network-connectivity-principles.md) mümkün olan en iyi performansı elde Microsoft 365 bağlantı ilkelerini anlamak için bkz. Ağ Bağlantısı İlkeleri.
- Planlama, tasarım FastTrack dağıtımla ilgili rehber yardım Microsoft 365 [Microsoft Microsoft 365](https://www.microsoft.com/fasttrack) için kaydolabilirsiniz. 
- Belirli [Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) konumuyla başka bir kullanıcı konumu arasında yapılacak ağ bağlantısı iyileştirmeleri hakkında özel rehberlik sağlayan temel bağlantı testlerini çalıştırmak için aşağıdaki bağlantı testi Microsoft 365.

> [!NOTE]
> Kimlik bilgileri için ExpressRoute'u kullanmak için Microsoft Office 365. Microsoft her müşteri isteğini gözden kullanır ve yalnızca müşterinin yasal düzenleme gereksinimi velisi doğrudan bağlantı Office 365, ExpressRoute'u kullanım için yetkilendirer. Bu tür gereksinimleriniz varsa, Microsoft incelemesine başlamak için lütfen düzenlemeye yönelik metin alıntısı ve web bağlantısını, Office 365 için [ExpressRoute'ta](https://aka.ms/O365ERReview) doğrudan bağlantının gerekli olduğu anlamına gelen metni girin. Yeni e-posta için rota filtreleri oluşturmaya Office 365 yetkisiz abonelikler bir [hata iletisi alır](https://support.microsoft.com/kb/3181709).
  
Ağ değerlendirmenizi daha iyi planlamanız için dikkat gereken Microsoft 365:
  
- Microsoft 365, ortak İnternet üzerinde çalışan, güvenli, güvenilir ve yüksek performanslı bir hizmettir. Hizmetin bu yönlerini geliştirmek için yatırım yapmaya devam edeceğiz. Tüm Microsoft 365 hizmetleri İnternet bağlantısı aracılığıyla kullanılabilir.

- kullanılabilirlik, küresel erişim ve İnternet tabanlı Microsoft 365 performansı gibi her iki yönü de iyileştirmeye devam ediyor. Örneğin, birçok Microsoft 365 hizmet, İnternet'e yönelik, genişleyen bir uç düğümü kümesiden faydalanr. Bu kenar ağı, İnternet üzerinden gelen bağlantılarda en iyi yakınlığı ve performansı sunar.

- Microsoft 365'i Teams ya da Skype Kurumsal Online ses, görüntü veya toplantı özellikleri gibi hizmetler için kullanmayı düşünen müşterilerin, gereksinimlerini gereksinimlerini karşılamak için [Microsoft FastTrack'i](https://www.microsoft.com/fasttrack) kullanmaları gerekir.

Bunu değerlendirmeye devam ediyorsanız Microsoft 365 ağ değerlendirmenize nereden başlayacağınızı bileamıyorsanız veya aş konusunda yardıma ihtiyaç ihtiyaçnız olan ağ tasarımı güçlükleri bulduysanız, lütfen Microsoft hesabı ekibiyle birlikte çalışmanız gerekir.

## <a name="the-microsoft-365-connectivity-test"></a>Microsoft 365 bağlantı testi

Microsoft 365 [bağlantı testi](https://aka.ms/netonboard), Microsoft 365 kiracınıza yönelik temel bağlantı testleri yapan ve en iyi performans için belirli ağ tasarımı önerileri sağlayan bir kavram kanıtı (POC) ağ Microsoft 365 aracıdır. Araç, İnternet'e göz atmada kullanışlı olan ancak genel olarak yüksek SaaS uygulamalarının performansını etkileyen büyük kurumsal ağ çevre tasarımı seçimlerini Microsoft 365.

Ağ Ekleme aracı şunları yapar:

- Konumu algılar veya test etmek için bir konum belirtebilirsiniz
- Ağ çıkış bağlantınız konumunu denetler
- En yakın ön Microsoft 365 olan ağ yolunu test ediyor
- Ara sunucularla, güvenlik duvarlarına Windows 10 DNS ile ilgili çevre ağı tasarımı önerileri sağlayan indirilebilir bir güvenlik duvarı uygulaması kullanarak gelişmiş testler sağlar. Araç ayrıca, Skype Kurumsal Online, Microsoft Teams Online ve SharePoint performans testleri Exchange Online.

Aracın iki bileşeni vardır: temel bağlantı bilgilerini toplayan tarayıcı tabanlı bir kullanıcı arabirimi ve gelişmiş testler Windows 10 ek değerlendirme verileri döndüren indirilebilir bir kullanıcı arabirimi.

Tarayıcı tabanlı araç aşağıdaki bilgileri görüntüler:

- Sonuçlar ve etki sekmesi
  - Kullanım için hizmet ön kapı haritasında konum
  - En iyi bağlantı sağlayacak diğer hizmet ön kapılarının haritasında yer
  - Yakın gelecekte bulunan diğer müşterilerle Microsoft 365 göre göre performans
- Ayrıntılar ve çözümler sekmesi
  - Şehre ve ülkeye göre kullanıcı konumu
  - Şehre, bölgeye ve ülkeye göre ağ çıkış konumu
  - Kullanıcıdan ağ çıkış uzaklığına
  - Microsoft 365 Exchange Online ön kapı konumu
  - Kullanıcı Microsoft 365 Exchange Online en iyi ön kapı
  - Metro alanınıza gelen ve daha iyi performansa sahip müşteriler

Gelişmiş Testler indirilebilir uygulama aşağıdaki ek bilgileri sağlar:

- Ayrıntılar ve çözümler sekmesi (eklenen)
  - Kullanıcının varsayılan ağ geçidi
  - İstemci DNS Sunucusu
  - İstemci DNS Yeniden Doğrulayıcı Çözümleyicisi
  - Exchange Online DNS sunucusu
  - SharePoint Online DNS sunucusu
  - Proxy sunucu kimliği
  - Medya bağlantı denetimi
  - Medya kalitesi paket kaybı
  - Medya kalitesi gecikme süresi
  - Medya kalitesi değişimi
  - Medya kalitesi paketi yeniden sıralama
- Özel özel birden çok uç noktayla bağlantı testleri
- İnternet, SharePoint Online ve Teams hizmetleri için izleme Exchange Online ve gecikme süresi verilerini içeren ağ yolu tanılamaları

Yeni ağ tasarımı önerileri blog gönderisi ile Microsoft 365 bağlantı testini okuyabilir ve geri Microsoft 365 Güncelleştirme Özellikleri bağlantı [testi POC'da](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) bulabilirsiniz. Bu araç için gelecek güncelleştirmeler ve Microsoft 365 ağ güncelleştirmeleri hakkında bilgiler Office 365 [blog'a](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) postalanmıştır.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Bağlantısına Genel Bakış](microsoft-365-networking-overview.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](./microsoft-365-network-connectivity-principles.md)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)