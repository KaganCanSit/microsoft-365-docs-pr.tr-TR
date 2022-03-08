---
title: Contoso'nun COVID-19 yanıtı ve karma çalışma desteği
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso Corporation'ın COVID-19 çalışmalarına nasıl yanıt verdiğni ve karma çalışma için yazılım yükleme ve güncelleştirme altyapısına nasıl mühendislik işlemi başlattıklarını anlıyoruz.
ms.openlocfilehash: 8b3829b7d3361c3a29ee495dd5a335a28a08c0b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325733"
---
# <a name="contosos-covid-19-response-and-support-for-hybrid-work"></a>Contoso'nun COVID-19 yanıtı ve karma çalışma desteği

Contoso her zaman, Paris merkezinde merkezi bir VPN sunucusu üzerinden şirket içi kaynaklara erişen uzak çalışanlarını destekliyormuştur. Contoso, tüm uzak çalışanlarına yönetilen bir dizüstü bilgisayar verdi. Şirket içi çalışanların masaüstü bilgisayarlarla dizüstü bilgisayarları bir karışımı vardı.

## <a name="contosos-response-to-covid-19"></a>Contoso'nun COVID-19 yanıtı

COVID-19 kaydırmak 19'un başlangıcıyla, aniden temel çalışanlar değil de uzaktan çalışanlar oldu. Contoso, iş gücünün evden çalışmaya geçişini gerçekleştirerek ve şirket içi kaynaklara uzaktan erişim yoluyla ve Microsoft 365 bulut hizmetlerini kullanarak çevrimiçi olarak birincil etkinliklerini gerçekleştirerek yanıt verdi.

Contoso'nun Paris genel merkezinde, zaten uzaktan iş gücünün %25'ini desteklemek için uzak erişim VPN sunucuları vardı, ancak iş gücünün %90'ını desteklemek için uzaktan erişim kapasitesini ölçeklendirmek için hızla taşındı. Contoso, her uydu ofisinin uzak erişim VPN sunucularını, uzak çalışanların Contoso intranet'e erişim için bölgesel olarak yakın bir giriş noktası kullanmalarını sağlıyor.

Contoso ayrıca, Office 365 uç noktaları kümesi için trafiğin VPN bağlantısını atlayarak doğrudan İnternet üzerinden gönderilmesini sağlamak üzere bölünmüş bölme için dizüstü bilgisayar, tablet ve akıllı telefonlara yüklenmiş VPN istemcilerinin yapılandırmasını da güncelledi. Daha fazla bilgi için bkz. [VPN bölünmüş Office 365 kullanan uzak kullanıcılar için bağlantı sorunlarını en iyi duruma getirme](../enterprise/microsoft-365-vpn-split-tunnel.md).

Burada, Paris merkezinde ve uydu ofislerinin her birsinde yüklü VPN cihazlarının yer alan sonuç yapılandırması ve yer almaktadır. 

![Contoso'nun VPN altyapısı.](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

Yüklü VPN istemcisine sahip bir uzaktan çalışan bölgesel olarak en yakın ofisi bulmak için DNS kullanır ve orada yüklü olan VPN cihazına bağlanır. Bölünmüş trafiğin olmasıyla, Microsoft 365 en iyi duruma getirme trafiği doğrudan bölgesel olarak en yakın ağ Microsoft 365 gönderilir. Diğer tüm trafikler VPN cihazına VPN bağlantısı üzerinden gönderilir.

## <a name="contosos-support-for-hybrid-work"></a>Contoso'nun karma çalışma desteği

bölgesel kilitlemeler sırasında çoğunlukla uzak çalışanları desteklemek üzere ilk değişiklikler yapıldıktan sonra, Contoso karma çalışmaları desteklemek için altyapı değişiklikleri yaptı ve çalışan:

- Her zaman uzak.
- Her zaman yerinde.
- Site içi ve uzak birleşimi.

Microsoft 365, güvenlik ve uyumluluk özellikleri Sıfır Güven için tasarlanmıştır ve kullanıcının ve cihazına bakılmaksızın çalışır. Daha fazla bilgi için bkz. [Sıfır Güven](https://www.microsoft.com/security/business/zero-trust).

Bununla birlikte, yazılım için yeni yüklemelerin ve güncelleştirmelerin yönetilmesi cihazın bulunduğu konuma bağlıdır, çünkü yazılım şirket içi bir kaynaktan veya İnternet kaynağından gelebilir. Contoso IT Mimarları yeni yükleme ve güncelleştirme altyapılarını çalışan yerine cihazın konumu temel alarak tasarlar.

İki tür cihaz belirlenmiştir: şirket içi ve dolaşım.

### <a name="dedicated-on-premises"></a>Adanmış şirket içi

Ayrılmış bir şirket içi cihaz, Contoso intranet'inden hiç ayrı olmayan ve yüklü bir VPN istemcisi olmayan bir masaüstü veya sunucu bilgisayardır. Bu şirket içi cihazlar, Microsoft Endpoint Configuration Manager, Kurumlar için Microsoft 365 Uygulamaları ve Edge tarayıcısı yüklemeleri ve güncelleştirmeleri için Windows 10 ve dağıtım noktalarını kullanmaya devam eder.

### <a name="roaming"></a>Dolaşım

Bir dolaşım cihazı Contoso intranet'inden ayrılarak, contoso VPN istemcisinin yüklü olduğu birçok ofis çalışanlarına ve tüm uzak çalışanların ve diğer kuruluşa ait akıllı telefonlar ve tabletler gibi diğer cihazlara verilen dizüstü bilgisayarları içerir. 

Bu cihazlar herhangi bir anda İnternet'e bağlanamalarından dolayı, Windows 10, Kurumlar için Microsoft 365 Uygulamaları ve Edge yüklemeleri ve güncelleştirmeleri için Intune'ı veya diğer bulut tabanlı hizmetleri kullanırlar. Var olan şirket içi Configuration Manager dağıtım noktalarını kullanmazlar.

Bu, dolaşım cihazı yüklemelerinden ve güncelleştirmelerinden bazılarının şirket içinde ve intranet'e bağlıyken İnternet üzerinden yapılması anlamına gelir. Ancak Contoso IT Mimarları, özellikle de uzaktaki çalışanların çoğu intranet'e çok az bağlandığında, yapılandırmanın basitliğini İnternet'te intranet bant genişliğinin iyileştirmeden daha önemli olduğunu karar verdi.

Sonuçta elde edilen altyapı şu şekildedir.

![Contoso'nun yüklemeleri ve güncelleştirmeleri altyapısı.](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Yükleme ve güncelleştirme davranışı, cihazları şu gruplardan birinin üyesi yaparak belirlenir:

- OnPremDevices

  Cihazki Configuration Manager istemcisi, yüklemeler ve güncelleştirmeler için dağıtım noktalarını kullanır.

- RoamingDevices

  Intune ve cihazki diğer ayarlar, yüklemeler ve güncelleştirmeler için Microsoft 365 kullanımını belirtir.

## <a name="new-onboarding-process"></a>Yeni ekleme işlemi

Yeni bir çalışana veya veri merkezinde yeni bir sunucuya verilen yeni ayrılmış bir şirket içi cihaz için, çalışan imza geldiğinde, Cihazın OnPremDevices grubunda üyeliğine bağlı olarak Configuration Manager istemcisi Windows 10, Kurumlar için Microsoft 365 Uygulamaları için en son güncelleştirmeleri indirir ve Kurumlar için Microsoft 365 Uygulamaları ve şirket içi Configuration Manager dağıtım noktalarından Edge. Tamamlandığında, ayrılmış şirket içi cihaz kullanıma hazır olur ve devam eden güncelleştirmeler için bu dağıtım noktalarını kullanır.

Yeni bir çalışana verilen yeni bir uzaktan cihaz için, çalışan oturum a açınca cihaz, RoamingDevices grubunda üyeliğine bağlı olarak Intune bulut hizmetiyle ve diğer hizmetlerle bağlantı kurarak Windows 10, Kurumlar için Microsoft 365 Uygulamaları ve Edge'in en son güncelleştirmelerini indirir ve yükleyin. Tamamlandığında, uzak cihaz kullanıma hazır olur ve şirket içi kaynaklara ve sürekli güncelleştirmeler için Microsoft 365 ağ bağlantısına erişmek için yüklü VPN istemcisini kullanır.

## <a name="next-step"></a>Sonraki adım

[Kurum içinde karma çalışma için altyapınızı](empower-people-to-work-remotely.md) ayarlayın.
