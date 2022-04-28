---
title: Contoso için Kurumlar için Microsoft 365 Uygulamaları dağıtımı
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'un Kurumlar için Microsoft 365 Uygulamaları dağıtmak için Microsoft Endpoint Configuration Manager nasıl kullandığını anlama.
ms.openlocfilehash: 8b6fb639083145c728870156d848b75897483d25
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096556"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Contoso için Kurumlar için Microsoft 365 Uygulamaları dağıtımı

Contoso daha etkili işbirliği, daha iyi güvenlik ve daha modern bir masaüstü deneyimi sağlamak için bilgisayarlarını Windows 10 Enterprise ve Kurumlar için Microsoft 365 Uygulamaları yükseltti. Contoso, altyapı ve iş gereksinimlerini değerlendirdikten sonra dağıtım için şu önemli gereksinimleri tanımladı:

- Tüm bilgisayarlar Kurumlar için Microsoft 365 Uygulamaları çalıştırılmalıdır.
- Dağıtım mümkün olduğunda mevcut yönetim araçlarını ve altyapısını kullanmalıdır.
- Dağıtımın kullanıcıların cihazlarında birden çok dili ve mevcut mimarileri desteklemesi gerekir.
- Bilgisayarlar en düşük BT yönetim maliyetleriyle ve kullanıcılara minimum etkiyle güncel ve güvenli kalmalıdır.

## <a name="deployment-tools"></a>Dağıtım araçları

Contoso, gereksinimlerine göre Configuration Manager (Geçerli Dal) aracılığıyla Windows 10 Enterprise ve Kurumlar için Microsoft 365 Uygulamaları dağıtmayı seçti. Configuration Manager büyük ortamlar için ölçeklendirilir ve yükleme, güncelleştirmeler ve ayarlar üzerinde kapsamlı denetim sağlar. Ayrıca, Office dağıtmayı ve yönetmeyi kolaylaştırmak ve daha verimli hale getirmek için yerleşik özelliklere sahiptir:

- Eş önbelleği, uzak konumlardaki cihazlara dağıtılırken sınırlı ağ kapasitesine yardımcı olabilir.
- Office dağıtmayı ve güncelleştirmeleri izlemeyi kolaylaştıran ve yöneticilere en son dağıtım ve yönetim özelliklerine erişim sağlayan Office İstemci Yönetimi panosu.
- İşletim sistemiyle aynı dili otomatik olarak dağıtma dahil olmak üzere akıllı dil paketi dağıtımı.
- Dağıtım sırasında istemciden mevcut Office sürümlerini kaldırmaya yönelik, tam olarak desteklenen ve kullanımı kolay bir yöntem.

Contoso, Configuration Manager ek olarak[, Office makroları ve eklentileriyle uyumluluk sorunlarını değerlendirmek için Office Eklentileri için Hazırlık Araç Seti'ni](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps) ve Microsoft'un ücretsiz bir aracı olan VBA'yı kullandı.

## <a name="managing-deployment-and-updates"></a>Dağıtım ve güncelleştirmeleri yönetme

Kurumlar için Microsoft 365 Uygulamaları yeni bir sürüm modeline sahiptir: hizmet olarak Office. Hizmet modeli, yeni özelliklerle güncel kalmayı kolaylaştırır. Ancak genellikle BT departmanlarının yeni sürümleri dağıtma ve test etme şeklini değiştirmesini gerektirir. Uyumluluk sorunlarını en aza indirmek ve bilgisayarlarının güncel kalmasını sağlamak için Contoso, Windows ve Office iki aşamada dağıttı:

- İlk olarak, Kurumlar için Microsoft 365 Uygulamaları kuruluş genelinde küçük bir temsilci cihaz kümesine dağıttılar. Bu pilot grup uygulamaları, eklentileri ve donanımları Kurumlar için Microsoft 365 Uygulamaları ile test etmek için kullanılmıştır.
- Dört ay sonra, pilot gruptaki uygulamalar, eklentiler ve donanımlarla ilgili tüm kritik sorunları ele aldıktan sonra Contoso, kuruluştaki diğer cihazlara (geniş grup) Kurumlar için Microsoft 365 Uygulamaları dağıttı.

Contoso, Configuration Manager kullanarak Office güncelleştirmelerini yönetmek yerine buluttan otomatik güncelleştirmeleri etkinleştirdi. Bulut tabanlı güncelleştirmeler, yönetim yükünü azaltırken cihazların güncel kalmasını sağlar.

Contoso, özellik güncelleştirmeleri için Office dağıtmak için kullandıkları iki aşamalı yaklaşımı takip etti: Pilot gruptaki cihazlar, kuruluşun geri kalanındaki cihazlardan (geniş grup) dört ay önce özellik güncelleştirmeleri aldı. Contoso, bunu Office etkinleştirmek için önerilen iki [güncelleştirme kanalını](/DeployOffice/overview-update-channels) kullandı:

- Pilot grup güncelleştirmeleri için Semi-Annual Enterprise Kanalı (Önizleme)
- Geniş grup güncelleştirmeleri için kanal Semi-Annual Enterprise

Semi-Annual Enterprise Kanalı (Önizleme) Semi-Annual Enterprise Kanalından dört ay önce Kurumlar için Microsoft 365 Uygulamaları sürümünü yayımladığından, Contoso'nun güncelleştirmeleri yönetmek zorunda kalmadan doğrulamak için zamanı vardır.

## <a name="deployment-process"></a>Dağıtım işlemi

Contoso, Office dağıtımını tamamlamak için Microsoft'un en iyi uygulama önerilerini içeren aşağıdaki işlemi uyguladı:

1. Contoso dağıtımdan önce Office Eklentisi ve VBA için Hazırlık Araç Seti'ni kullanarak uygulamalarını test etti ve Kurumlar için Microsoft 365 Uygulamaları uyumluluğunu değerlendirmek için eklentileri Office.
1. Configuration Manager'da istemci cihazlarında eş önbelleği etkinleştirerek uzak konumlardaki istemci cihazlara dağıtım yaparken sınırlı ağ kapasitesine yardımcı olur. 
1. Contoso, Configuration Manager cihaz koleksiyonu olarak iki dağıtım grubu tanımlamıştı: pilot grup ve geniş bir grup. Kuruluş genelinde küçük bir temsili cihaz kümesini içeren pilot grup, Windows 10 Enterprise ve Kurumlar için Microsoft 365 Uygulamaları ile uygulamaların, eklentilerin ve donanımların ek testinde kullanıldı.
1. her ikisi de Configuration Manager konsolunun parçası olan Office İstemci Yönetimi panosunu ve Office 365 Yükleyicisi sihirbazını kullanarak Office için dağıtım paketleri oluşturdular. Biri Semi-Annual Enterprise Kanalındaki pilot grup (Önizleme) ve diğeri de Semi-Annual Enterprise Kanalındaki geniş grup için iki Kurumlar için Microsoft 365 Uygulamaları paketi oluşturmşlardır.
2. Her Office paketi İngilizce, Fransızca ve Almanca Dil paketlerini içerir. Bir cihaz Office paketine dahil olmayan bir dil gerektiriyorsa, bu dil paketi otomatik olarak Office Content Delivery Network (CDN) içinden indirilir.
3. Kurumlar için Microsoft 365 Uygulamaları yüklemeden önce Office tüm mevcut MSI sürümlerini otomatik olarak kaldırmak için Office paketindeki yerleşik özelliği kullandılar.
4. Configuration Manager'da Windows ve Office paketlerini ağlarındaki dağıtım noktalarına dağıttılar. Ardından pilot Kurumlar için Microsoft 365 Uygulamaları paketini pilot gruba dağıtmak için Configuration Manager dağıtım görev dizilerini çalıştırdılar.
5. Pilot grupla ilgili uyumluluk sorunlarını giderdikten sonra Contoso, Kurumlar için Microsoft 365 Uygulamaları paketini geniş gruba dağıtmak için görev dizilerini çalıştırdı.

Contoso cihazları buluttan otomatik olarak güncelleştirmeyi seçtiğinden, işlemi Configuration Manager'da yönetmeye gerek yoktu. Cihazları, ilk dağıtımda tanımlanan güncelleştirme kanalına bağlı olarak doğrudan buluttan otomatik olarak güncelleştirilir.

Contoso Kurumlar için Microsoft 365 Uygulamaları yüklemesi ve devam eden güncelleştirmeler dağıtım mimarisi aşağıdadır.

![Kurumlar için Microsoft 365 Uygulamaları için Contoso dağıtım altyapısı.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Sonraki adım

Contoso'un kuruluş genelinde çalıştırdıkları cihazları ve uygulamaları yönetmek için Microsoft 365'da Microsoft Intune nasıl [kullandığını](contoso-mdm.md) öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal Uygulamaları](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)