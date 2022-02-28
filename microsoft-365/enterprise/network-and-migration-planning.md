---
title: Ağ ve geçiş planlama Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makale, ağ planlaması, test etme ve diğer kaynak geçiş bilgilerine Office 365.
ms.openlocfilehash: 21bd36395f6ceb6a13b3180a26f8dbf7f197f134
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984460"
---
# <a name="network-and-migration-planning-for-office-365"></a>Ağ ve geçiş planlama Office 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Bu makalede, ağ planlama ve test etme ve test etme hakkında bilgilerin bağlantıları ve Office 365.
  
Office 365'i ilk kez dağıtmadan veya Office 365'a geçiş için dağıtmadan önce, size gereken bant genişliğini tahmin etmek için bu konu başlıkları altında yer alan bilgileri kullanabilir ve Office 365'te dağıtmak veya geçiş yapmak için yeterli bant genişliğiniz olup olmadığını test Office 365.

Bu makale, proje ayarları [için ağ planlaması ve performans Office 365](./network-planning-and-performance.md).

Hem microsoft hem de diğer Microsoft bulut Microsoft 365 hizmetleri için ağına en iyi duruma getirme adımları için, [Enterprise Architects için Microsoft Bulut Ağı posteri'ne](../solutions/cloud-architecture-models.md) bakın.
   
## <a name="estimate-network-bandwidth-requirements"></a>Ağ bant genişliği gereksinimlerini tahmin edin
<a name="EstimateBandwidthRequirements"> </a>

İnternet Office 365 kullanılması, kuruluşun İnternet bağlantı hattı kullanımını artırabilir. Şu anda var olan bant genişliğinin, Office 365 tam olarak dağıtıldıktan sonra tahmini artışı işlemek için yeterli olup olmadığını belirlemek ve günün en yoğun saatlerini idare edecek en az %20 kapasite bırakmak önemlidir.
  
Bant genişliğini tahmin etmek için aşağıdaki adımları kullanın:
  
1. Her İnternet çıkıştıracak istemcilerin sayısını değerlendirin. Çok terabitli ağlarımızın mümkün olduğunca fazla bağlantıyı işlemesine izin verme. 
    
2. İstemcilerin Office 365 kullanabileceği diğer hizmet ve özellikleri belirleme. Büyük olasılıkla, farklı hizmetlere veya kullanım profillerine sahip kişi gruplarına sahipsinizdir.
    
3. Pilot bir istemci grubu için ağ kullanımını ölçün. Pilot istemcilerin hem kuruluşta farklı kişi profillerini hem de farklı coğrafi konumları temsil olduğundan emin olmak. Sonuçlarınızı eski hesaplayıcılarımıza veya kendi [ağ üzerinde Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) Microsoft Teams [çalışmamıza](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) göre çapraz kontrol edebilirsiniz[](/microsoftteams/prepare-network). 
    
4. Pilot gruptaki ölçüleri kullanarak tüm kuruluşun ihtiyaçları için tahminler yapın ve ağ üzerinde herhangi bir değişiklik yapmadan önce tahminlerin doğrulanması için yeniden test yapın.
    
## <a name="test-your-existing-network"></a>Var olan anızı test etmek
<a name="calculators"> </a>

 **Ağ araçları.** İndirme, karşıya yükleme ve gecikme kısıtlamalarını belirlemek için İnternet bant genişliğinizi test edin ve doğrulayın. Bu araçlar, geçiş için ağ becerilerinizin yanı sıra dağıtıldıktan sonra da size yardımcı olur. 
    
- [Microsoft Uzak Bağlantı Çözümleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=517243): Kendi ortamınıza yönelik Exchange Online test eder.
    
- Sorunları gidermek [Destek ve Kurtarma Yardımcısı sorunları Office 365 için Microsoft](https://diagnostics.office.com/#/Download?env=SOC) Outlook Office 365 kullanın. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Ağ planlaması ve geçiş performansını iyileştirmek için en iyi Office 365
<a name="BestPractices"> </a>

Office 365 deneyiminizi geliştirme konusunda daha fazla bilgi için, bu en iyi Office 365 daha derine bakın.
  
1. Kullanıcılarınıza hemen yardımcı olmak mı istiyor musunuz? [Ağınız henüz doğru değilken Office 365](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) Online, Exchange Online ve Lync Online gibi SharePoint Office 365'i kullanma hakkında ipuçları için bkz. Yavaş bir Office 365 ağın kullanımıyla ilgili en iyi yöntemler. Bu makalede, Office 365 deneyiminizi en iyi duruma getirmeniz için TechNet ve Support.office.com'daki içeriğin yüklemeleri açıklanmıştır ve web sayfalarınızı özelleştirmenin kolay yolları ve en iyi internet deneyimi için Internet Explorer ayarlarınızı nasıl Office 365 içerir. 
    
2. Trafiği [Office 365 bir şekilde yönetmeyi ve](./microsoft-365-network-connectivity-principles.md) mümkün olan en iyi performansı elde etmek için Office 365 ilkelerini anlamak için Ağ Bağlantısı İlkeleri makalesinde okuyabilirsiniz. Bu makale, ağ bağlantısını güvenli bir şekilde en iyi duruma getirme konusunda Office 365 yardımcı olacaktır. 
    
3. Güncelleştirmelerin zamanlamayı dikkatle yöneterek posta geçişi Windows geliştirin. Ağ bant genişliği kullanımını düzenlemek üzere istemci bilgisayarlarınızı toplu olarak güncelleştirebilir ve istemci bilgisayarlarınızı başka bir Office 365 başlamadan önce tüm istemci bilgisayarların güncelleştiril olduğundan emin olun. Daha fazla bilgi için bkz[. Masaüstü bilgisayarlarını el ile güncelleştirme ve Office 365 güncelleştirmeleri için yapılandırma](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 trafiğin en iyi performansı, güvenilir bir İnternet hizmeti olarak kabul edilirse ve bazı kuruluşların güvenilmeyen İnternet hizmetleriyle ağ trafiğine yer alan geleneksel filtreleme ve taramanın büyük bir yerini atlayarak gerçekleştirebilirsiniz. Bu normal olarak, ara sunucu kullanıcı kimlik doğrulaması ve paket incelemesi gibi giden işlemleri kaldırmanın yanı sıra doğru Ağ Adresi Çevirisi (NAT) ve artırılmış ağ isteklerini işlemek için yeterli bant genişliği kapasitesiyle İnternet'e yerel çıkış sağlamayı içerir. Ağ Office 365 [bir](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) İnternet hizmeti olarak işlerinizi yönetmek için ek yol gösterici bilgiler Office 365 uç noktalarını yönetme'ye bakın.
    
1. Uç [noktaların Office 365 emin olun](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Giden ek trafik Office 365 TLS/SSL üzerinden güvenli trafikte artışın yanı sıra giden ara sunucu bağlantılarında da artışa neden olur.
    
2. Giden sunucu sunucularınızı kullanıcı kimlik doğrulaması gerektirirse, yavaş bağlantı veya işlev kaybı ile karşınıza çıkabilirsiniz. Etki alanlarında kimlik doğrulaması gereksinimini Office 365 yükü azaltabilirsiniz.
    
3. Çok fazla sayıda paylaşılan takviminiz ve posta kutunuz varsa, takvimden posta kutusuna gelen bağlantı sayısında Outlook Exchange. Örneğin, Outlook istemci, kullanımda olan her paylaşılan takvim için iki ek bağlantı açabilir. Bu durumda, çıkış ara sunucusunun bağlantıları işleyene olduğundan emin olur veya iş için Office 365 bağlantılarda ara Outlook.
    
4. Genel bir IP adresi için en fazla desteklenen cihaz sayısını ve birden çok IP adresi arasında yük dengelemeyi belirleme. Daha fazla bilgi için [bkz. Ağ desteğiyle NAT Office 365](nat-support-with-microsoft-365.md).
    
5. Ağınızdaki bilgisayarlardan giden bağlantıları incelerken, bu filtreyi Office 365 etki alanlarına atlayarak bağlantı ve performansı iyileştirebilirsiniz. Buna ek olarak, giden denetlemeyi atlayarak genellikle tek bir İnternet çıkış ihtiyacı ortadan kaldırır ve belirli bir Office 365 için yerel İnternet çıkışlarını sağlar.
    
6. Bazı müşterilerin iç ağ ayarları, performansı etkileyebilir. Ayarlar iletim birimi (MTU) boyutu, ağ otomatik görüşmeler veya otomatik algılama gibi en iyi yönlendirmeler ve İnternet'e yönelik en iyi rotalar, bakulacak yaygın yerlerdir.
    
## <a name="network-planning-reference-for-office-365"></a>Ağ planlama başvurusu Office 365
<a name="NetReference"> </a>

Bu konular, ağ Office 365 ayrıntılı bilgiler içerir.
  
- [Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [İçerik teslim ağları](content-delivery-networks.md)
    
- [Etki Alanı için Dış Etki Alanı Adı Sistemi Office 365](external-domain-name-system-records.md)
    
- [Office 365 hizmetlerde IPv6 desteği](ipv6-support.md)
    
- [Office 365 Bağlantısı İlkeleri](./microsoft-365-network-connectivity-principles.md)
    
- [Office 365 hizmetlerine bağlanan ağ cihazlarını planlama](plan-for-network-devices.md)
    
- [Kurulum kılavuzları Office 365 hizmetleri](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)