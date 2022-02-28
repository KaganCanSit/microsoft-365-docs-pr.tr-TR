---
title: Contoso Kurumlar için Microsoft 365 Uygulamaları dağıtımı
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'ya dağıtım yapmak Microsoft Endpoint Configuration Manager Contoso'Kurumlar için Microsoft 365 Uygulamaları.
ms.openlocfilehash: 6442deb0c6b7dce83a997bab28aa1c9cc85e8564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983506"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Contoso Kurumlar için Microsoft 365 Uygulamaları dağıtımı

Contoso, daha etkili bir işbirliği Windows 10 Enterprise daha iyi güvenlik Kurumlar için Microsoft 365 Uygulamaları daha modern bir masaüstü deneyimi sağlamak için bilgisayarlarını Daha Yüksek ve Gelişmiş Sürüm'e yükseltti. Contoso, altyapı ve iş gereksinimlerini değerlendirdikten sonra dağıtım için şu önemli gereksinimleri belirledi:

- Tüm bilgisayarlar tek bir Kurumlar için Microsoft 365 Uygulamaları.
- Dağıtım mümkün olduğunda mevcut yönetim araçlarını ve altyapısını kullanmalısınız.
- Dağıtım, kullanıcıların cihazlerinde birden çok dili ve mevcut mimariyi desteklemesi gerekir.
- Bilgisayarlar, en düşük IT yönetim maliyeti ve kullanıcılar üzerinde çok az etki ile güncel ve güvenli kalsın.

## <a name="deployment-tools"></a>Dağıtım araçları

Contoso, gereksinimlerine bağlı olarak dağıtım tercih etti ve Windows 10 Enterprise (Geçerli Kurumlar için Microsoft 365 Uygulamaları) aracılığıyla dağıtıldı. Configuration Manager, büyük ortamlar için ölçekler ve yükleme, güncelleştirmeler ve ayarlar üzerinde kapsamlı denetim sağlar. Ayrıca, e-posta postalarınızı dağıtmayı ve yönetmeyi daha kolay ve verimli hale getirir, ayrıca Office özellikleri vardır:

- Uzak konumlarda cihazlara dağıtımda sınırlı ağ kapasitesine yardımcı olan eş önbelleği.
- Güncelleştirmelerin Office ve izlenmesini kolaylaştıran ve yöneticilere en son dağıtım ve yönetim özelliklerine erişim veren Office Yönetimi panosu.
- İşletim sistemiyle aynı dili otomatik olarak dağıtma da dahil olmak üzere akıllı dil paketi dağıtımı.
- Tam olarak desteklenen ve kullanımı kolay bir yöntem olan ve dağıtım sırasında bir istemciden Office sürümlerini kaldırma.

Contoso, Yapılandırma Yöneticisi'ne ek olarak, Microsoft'un ücretsiz bir aracı olan Office eklentileri ve [VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps) için Hazırlık Araç Seti'ni kullanarak makrolarında ve eklentilerinde Office sorunları değerlendirdi.

## <a name="managing-deployment-and-updates"></a>Dağıtım ve güncelleştirmeleri yönetme

Kurumlar için Microsoft 365 Uygulamaları bir sürüm modeli vardır: Office olarak kullanın. Hizmet modeli, yeni özelliklerle güncel kalmayı kolaylaştırır. Ancak, çoğunlukla, IT departmanların yeni sürümlerde dağıtım ve test çalışmalarını değiştirmesi gerektirmektedir. Uyumluluk sorunlarını en aza indirmek ve bilgisayarlarının güncel kalmasını sağlamak için Contoso dağıtıldı ve Windows iki Office dağıtıldı:

- İlk olarak, Kurumlar için Microsoft 365 Uygulamaları küçük bir temsili cihaz kümesine dağıtıldılar. Bu pilot grup uygulamaları, eklentileri ve donanımı test etmek için kullanılan bir uygulama Kurumlar için Microsoft 365 Uygulamaları.
- Dört ay sonra pilot gruptaki uygulamalar, eklentiler ve donanımla ilgili tüm kritik sorunları eledikten sonra, Contoso Kurumlar için Microsoft 365 Uygulamaları'i kuruluşun diğer cihazlarına (geniş grup) dağıttı.

Contoso, Yapılandırma Yöneticisi'Office güncelleştirmeleri yönetmek yerine buluttan otomatik güncelleştirmeleri etkinleştirdi. Bulut tabanlı güncelleştirmeler, yönetim yükünü azaltırken cihazların güncel kalmasını da sağlar.

Contoso, özellik güncelleştirmeleri için Office'in dağıtımında kullandığı iki aşamalı yaklaşımı izledi: Pilot gruptaki cihazlar, kuruluşun geri kalanından (geniş grup) dört ay önce özellik güncelleştirmeleri aldı. Bu seçeneği etkinleştirmek için, Contoso Office iki önerilen güncelleştirme [kanalı kullandı](/DeployOffice/overview-update-channels):

- Semi-Annual Enterprise grubu güncelleştirmeleri için Kanal Önizlemesi (Önizleme)
- Semi-Annual Enterprise grup güncelleştirmeleri için Kanal Kanalı

Altı Semi-Annual Enterprise (Önizleme) kanalı, Altı Aylık Kanal'dan Kurumlar için Microsoft 365 Uygulamaları Semi-Annual Enterprise dört ay önce bir sürüm yayımlayalır, Contoso'da güncelleştirmeleri yönetmek zorunda kalmadan doğrulamaya zaman vardır.

## <a name="deployment-process"></a>Dağıtım işlemi

Contoso, posta kutusu dağıtımını Office Microsoft'un en iyi uygulama önerilerini içeren aşağıdaki süreci uygulamaya başladı:

1. Dağıtımdan önce, Contoso Office ve VBA için Hazırlık Araç Seti'ni kullanarak uygulamalarını test etti ve Office Eklentileri ile uyumluluklarını değerlendirmek için Kurumlar için Microsoft 365 Uygulamaları.
1. Configuration Manager'da, istemci cihazlarında eş önbelleği etkinleştirdi. Bu, uzak konumlarda istemci cihazlarına dağıtım için sınırlı ağ kapasitesine yardımcı olur. 
1. Contoso, Configuration Manager'da cihaz koleksiyonları olarak iki dağıtım grubu tanımladı: pilot grup ve geniş bir grup. Kuruluş genelinde küçük bir temsili cihaz kümesi de dahil olan pilot grup, uygulama, eklenti ve donanımla ilgili ek test için Windows 10 Enterprise ve Kurumlar için Microsoft 365 Uygulamaları.
1. Her ikisi de Configuration Manager Office parçası olan Office İstemci Yönetimi panosu ve Office 365 Yükleyici sihirbazını kullanarak Office için dağıtım paketleri oluşturdular. Bu grup, Kurumlar için Microsoft 365 Uygulamaları Kanal'da pilot grup (Önizleme) Semi-Annual Enterprise bir tane de Kanal'da geniş grup için olmak Semi-Annual Enterprise hazırlar.
2. Her Office paketi İngilizce, Fransızca ve Almanca Dil paketleri içerir. Cihaz, Office paketinde yer alan bir dile gerek Office, bu dil paketi otomatik olarak paketten Office Content Delivery Network (CDN).
3. Kullanıcılar, bu özellikleri yüklemeden önce Office paketinin var olan tüm MSI sürümlerini otomatik olarak kaldırmak için Office yerleşik özelliğini Kurumlar için Microsoft 365 Uygulamaları.
4. Configuration Manager'da, dağıtım Windows ve Office dağıtım noktalarına paketler dağıtıldı. Ardından, pilot uygulama paketini pilot gruba dağıtmak için Configuration Manager dağıtım Kurumlar için Microsoft 365 Uygulamaları sıralarını kullandılar.
5. Pilot gruptaki uyumluluk sorunlarını çözümledikten sonra, Contoso görev sıralarını hazır paket paketini Kurumlar için Microsoft 365 Uygulamaları grubuna dağıttı.

Contoso cihazları buluttan otomatik olarak güncelleştirmeyi seçtiğinden, işlemi Configuration Manager'da yönetmenize gerek yoktu. Cihazları, ilk dağıtımda tanımlanan güncelleştirme kanalına göre doğrudan buluttan otomatik olarak güncelleştirilir.

Burada Contoso 2013 yükleme Kurumlar için Microsoft 365 Uygulamaları devam eden güncelleştirmelerin dağıtım mimarisini nasıl güncellemektedir.

![E-posta için Contoso dağıtım Kurumlar için Microsoft 365 Uygulamaları.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Sonraki adım

Contoso'ya[, Microsoft Intune](contoso-mdm.md) cihazlarını ve kuruluş genelinde çalıştıracakları uygulamaları yönetmek için Microsoft 365 Kurumsal'da Contoso'ya nasıl yardımcı olduğunu öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal Uygulamaları](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)