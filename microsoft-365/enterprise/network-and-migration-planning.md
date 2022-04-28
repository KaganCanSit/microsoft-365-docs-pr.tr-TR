---
title: Office 365 için ağ ve geçiş planlaması
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Bu makale ağ planlama, test etme ve Office 365 geçiş hakkındaki bilgilerin bağlantılarını içerir.
ms.openlocfilehash: 6288c9afae66206b7284f751f8a63381ab8451e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077469"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365 için ağ ve geçiş planlaması

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Bu makale, ağ planlama ve test etme ve Office 365 geçiş hakkındaki bilgilerin bağlantılarını içerir.
  
İlk kez dağıtmadan veya Office 365 geçirmeden önce, ihtiyacınız olan bant genişliğini tahmin etmek ve ardından Office 365 dağıtmak veya geçiş yapmak için yeterli bant genişliğine sahip olduğunuzu test etmek ve doğrulamak için bu konulardaki bilgileri kullanabilirsiniz.

Bu makale, [Office 365 için ağ planlama ve performans ayarlamanın](./network-planning-and-performance.md) bir parçasıdır.

Ağınızı Microsoft 365 ve diğer Microsoft bulut platformları ve hizmetleri için iyileştirme adımları [için Enterprise Architects için Microsoft Bulut Ağı](../solutions/cloud-architecture-models.md) posterine bakın.
   
## <a name="estimate-network-bandwidth-requirements"></a>Ağ bant genişliği gereksinimlerini tahmin
<a name="EstimateBandwidthRequirements"> </a>

Office 365 kullanmak kuruluşunuzun internet bağlantı hattının kullanımını artırabilir. Şu anda kullanılabilir bant genişliği miktarının, Office 365 tam olarak dağıtıldıktan sonra tahmini artışı işlemek için yeterli olup olmadığını belirlemek ve en yoğun gün sayısını işlemek için en az %20 kapasite bırakmak önemlidir.
  
Bant genişliğini tahmin etmek için aşağıdaki adımları kullanın:
  
1. Her İnternet çıkışını kullanacak istemci sayısını değerlendirin. Çok terabitli ağımızın mümkün olduğunca çok bağlantıyı işlemesine izin verin. 
    
2. İstemcilerin hangi Office 365 hizmetlerini ve özelliklerini kullanabileceklerini belirleyin. Büyük olasılıkla farklı hizmetlere veya kullanım profillerine sahip kişi gruplarınız olacaktır.
    
3. Bir pilot istemci grubu için ağ kullanımını ölçün. Pilot istemcilerin hem kuruluştaki farklı kişi profillerini hem de farklı coğrafi konumları temsil ettiğinden emin olun. Exchange [ve](/microsoftteams/prepare-network) [Microsoft Teams](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) ya da kendi ağımızda gerçekleştirdiğimiz [örnek olay incelemesi](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) için sonuçlarınızı eski hesaplayıcılarımızla karşılaştırabilirsiniz. 
    
4. Tüm kuruluşun gereksinimlerini tahmin etmek için pilot gruptaki ölçümleri kullanın ve ağınızda herhangi bir değişiklik yapmadan önce tahminleri doğrulamak için yeniden test edin.
    
## <a name="test-your-existing-network"></a>Mevcut ağınızı test edin
<a name="calculators"> </a>

 **Ağ araçları.** İndirme, karşıya yükleme ve gecikme kısıtlamalarını belirlemek için İnternet bant genişliğinizi test edin ve doğrulayın. Bu araçlar, hem geçiş için ağınızın özelliklerini hem de tamamen dağıtıldıktan sonra belirlemenize yardımcı olur. 
    
- [Microsoft Uzaktan Bağlantı Çözümleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online ortamınızda bağlantıyı test edin.
    
- [Outlook ve Office 365 sorunlarını gidermek için Office 365 için Microsoft Desteği ve Kurtarma Yardımcısı'nı](https://diagnostics.office.com/#/Download?env=SOC) kullanın. 

- [Microsoft 365 ağ bağlantısı test aracı: Ağ bağlantısı](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool) Microsoft 365 testler.
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Office 365 için ağ planlaması ve geçiş performansını iyileştirmeye yönelik en iyi yöntemler
<a name="BestPractices"> </a>

Office 365 deneyiminizi geliştirme hakkında daha fazla bilgi için bu en iyi yöntemlere biraz daha yakından bakın.
  
1. Kullanıcılarınıza hemen yardım etmeye başlamak mı istiyorsunuz? Ağınız işbirliği yapmadığında SharePoint Online, Exchange Online ve Lync Online gibi Office 365 kullanmayla ilgili ipuçları için bkz. Yavaş ağda Office 365 kullanmaya yönelik [en iyi yöntemler](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Bu makale, TechNet'te içerik yüklerine ve Office 365 deneyiminizi iyileştirmeye yönelik Support.office.com bağlantı verir ve web sayfalarınızı özelleştirmenin kolay yolları ve internet explorer ayarlarınızı en iyi Office 365 deneyimi için ayarlama hakkında bilgi içerir. 
    
2. Office 365 trafiğini güvenli bir şekilde yönetmeye ve mümkün olan en iyi performansı elde etmeye yönelik bağlantı ilkelerini anlamak için [Ağ Bağlantısı İlkeleri'ni](./microsoft-365-network-connectivity-principles.md) Office 365 okuyun. Bu makale, Office 365 ağ bağlantısını güvenli bir şekilde iyileştirmeye yönelik en son yönergeleri anlamanıza yardımcı olur. 
    
3. Windows Güncelleştirmeleri zamanlamasını dikkatle yöneterek posta geçiş performansını geliştirin. İstemci bilgisayarlarınızı toplu olarak güncelleştirebilir ve ağ bant genişliğinin kullanımını düzenlemek için Office 365 geçmeden önce tüm istemci bilgisayarların güncelleştirildiğinden emin olabilirsiniz. Daha fazla bilgi için bkz. [En son güncelleştirmeler için masaüstlerini Office 365 için el ile güncelleştirme ve yapılandırma](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 ağ trafiği, güvenilir bir İnternet hizmeti olarak kabul edildiğinde ve bazı kuruluşların güvenilmeyen İnternet hizmetlerine ağ trafiğine yerleştirdiği geleneksel filtreleme ve tarama işlemlerinin çoğunu atlamasına izin verildiğinde en iyi performansı gösterir. Bu genellikle ara sunucu kullanıcı kimlik doğrulaması ve paket denetimi gibi giden işlemleri kaldırmanın yanı sıra doğru Ağ Adresi Çevirisi (NAT) ve artan ağ isteklerini işlemek için yeterli bant genişliği kapasitesi ile İnternet'e yerel çıkış sağlamayı içerir. Ağınızı Office 365 ağınızda güvenilir bir İnternet hizmeti olarak işleyecek şekilde yapılandırma konusunda ek yönergeler için bkz. Office 365 [uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
    
1. [Office 365 uç noktalarını yönetmeyi sağlayın](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Office 365 ek trafik, giden ara sunucu bağlantılarının artmasına ve TLS/SSL üzerinden güvenli trafiğin artmasına neden olur.
    
2. Giden proxy'leriniz kullanıcı kimlik doğrulaması gerektiriyorsa yavaş bağlantı veya işlev kaybıyla karşılaşabilirsiniz. Office 365 etki alanları için kimlik doğrulama gereksiniminin atlanması bu yükü azaltabilir.
    
3. Çok sayıda paylaşılan takviminiz ve posta kutunuz varsa, Outlook ile Exchange arasındaki bağlantı sayısında bir artış görebilirsiniz. Örneğin, Outlook istemcisi kullanımdaki her paylaşılan takvim için en fazla iki ek bağlantı açabilir. Bu durumda, çıkış ara sunucusunun bağlantıları işleyebileceğinden emin olun veya Outlook için Office 365 bağlantıları için ara sunucuyu atlayabilirsiniz.
    
4. Genel IP adresi için desteklenen en fazla cihaz sayısını ve birden çok IP adresi arasında yük dengelemeyi belirleme. Daha fazla bilgi için bkz. [Office 365 ile NAT desteği](nat-support-with-microsoft-365.md).
    
5. Ağınızdaki bilgisayarlardan giden bağlantıları inceliyorsanız, bu filtrelemeyi Office 365 etki alanlarına atlamak bağlantıyı ve performansı geliştirir. Ayrıca, giden incelemenin atlanması genellikle tek bir İnternet çıkışı gereksinimini ortadan kaldırır ve hedeflenen Office 365 ağ istekleri için yerel İnternet çıkışını etkinleştirir.
    
6. Bazı müşteriler iç ağ ayarlarının performansı etkileyebileceğini tespit etti. Maksimum iletim birimi (MTU) boyutu, ağ otomatik anlaşması veya otomatik algılama gibi Ayarlar ve İnternet'e en uygun alt rotalar, bakılması gereken yaygın yerlerdir.
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 için ağ planlama başvurusu
<a name="NetReference"> </a>

Bu konular ayrıntılı Office 365 ağ başvuru bilgilerini içerir.
  
- [Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [İçerik teslim ağları](content-delivery-networks.md)
    
- [Office 365 için Dış Etki Alanı Adı Sistemi kayıtları](external-domain-name-system-records.md)
    
- [Office 365 hizmetlerinde IPv6 desteği](ipv6-support.md)
    
- [Office 365 Ağ Bağlantı İlkeleri](./microsoft-365-network-connectivity-principles.md)
    
- [Office 365 hizmetlerine bağlanan ağ cihazlarını planlama](plan-for-network-devices.md)
    
- [Office 365 hizmetleri için kurulum kılavuzları](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)
