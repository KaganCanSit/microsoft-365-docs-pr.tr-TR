---
title: Office 2007 veya 2010 sunucu ve istemcilerinden yükseltmenizi planlama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
ms.assetid: b2acaeca-4986-40f4-92b7-a1bdd06e549d
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Bu makale, yükseltmelerini planlamalarına yardımcı olmak için Office 2007 veya Office 2010 kullanan kullanıcılara yönelik kaynaklar içerir.
ms.openlocfilehash: ba57eb9f6f1b3c0d573b19b63da1fdd2c1a2b879
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100269"
---
# <a name="plan-your-upgrade-from-office-2007-or-office-2010-servers-and-clients"></a>Office 2007 veya Office 2010 sunucu ve istemcilerinden yükseltmenizi planlama

*Bu makale hem Enterprise için Microsoft 365 hem de Enterprise için Office 365 için geçerlidir.*

Kuruluşunuz Office ürünlerinin ve sunucularının eski sürümlerini kullanıyorsa şimdi yükseltmenizi planlamaya başlamak için harika bir zaman. Office 2007 ürün ve hizmetleri [destek sonuna](upgrade-from-office-2007-servers-and-products.md) ulaşmıştır. Office 2010 ürün ve hizmetleri için:

- Office 2010 ve Exchange 2010 *, 13 Ekim 2020'de* destek sonuna ulaştı. 
- SharePoint 2010 ve Project Server 2010 *, 13 Nisan 2021'de* destek sonuna ulaşacaktır. 

Daha fazla bilgi için bkz[. Office 2010 sunucularından ve istemcilerinden yükseltme](upgrade-from-office-2010-servers-and-products.md).

Yükseltmenize başlamak için bu makaledeki kaynakları kullanın.

## <a name="what-is-microsoft-365"></a>Microsoft 365 nedir?

[Microsoft 365](https://www.microsoft.com/microsoft-365), daha fazlasını başarmanıza yardımcı olmak için tasarlanmış yenilikçi Office uygulamaları, akıllı bulut hizmetleri ve birinci sınıf güvenliğin bir birleşimidir.

Microsoft 365, kuruluşunuzun en son Windows işletim sistemi üzerinde çalıştığından emin olmak için lisansları ve özellikleri içerir. Ayrıca Windows, iOS ve Android cihazlarınızın kimlik doğrulaması ve veri koruması gerektiren ilkelerle kaydedilmesini ve güvenliğinin sağlanmasını sağlar. Ayrıca, Windows 10 ve Enterprise (eski adıyla Office 365 ProPlus) istemci yazılımı için Microsoft 365 Uygulamaları en son özellikleri ve güvenlik güncelleştirmelerini içerecek şekilde sürekli olarak güncelleştirilir.
  
Microsoft 365, Microsoft bulutu tarafından etkinleştirilen ve güvenliği sağlanan cihazları ve üretkenlik deneyimlerini sürekli geliştirerek işletmenizi dijital olarak dönüştürmenin yoludur.
 
|Kaynak|Açıklama|
|---|---|
|[Microsoft 365](https://www.microsoft.com/microsoft-365)|Microsoft 365 sürümleri hakkında bilgi edinin.|
|[İş için Microsoft 365 belgeleri](../admin/index.yml)|Küçük ve orta ölçekli işletmeler için Microsoft 365 sürümü hakkında ayrıntılı bilgi edinin.|
|[Eğitim için Microsoft 365 belgeleri](/microsoft-365/education/)|Eğitim kuruluşları için Microsoft 365 sürümü hakkında ayrıntılı bilgi edinin.|
|[Enterprise belgeleri için Microsoft 365](./index.yml)|Kurumsal kuruluşlar için Microsoft 365 sürümü hakkında ayrıntılı bilgi edinin.|
|||

## <a name="what-happens-if-i-dont-upgrade"></a>Yükseltme yapmazsam ne olur?

Şu anda yükseltmemeyi seçebilirsiniz. Şirket içi sunucularınız ve uygulamalarınız çalışmaya devam eder. Ancak artık güvenlik güncelleştirmeleri veya destek seçenekleri almadığınızda, kuruluşunuz güvenlik ihlallerine karşı savunmasız olabilir. Yükseltmenizi yakında planlamanızı kesinlikle öneririz. şirket içi sunucularınızın ve uygulamalarınızın Microsoft 365 veya daha yeni sürümlerine yükseltebilirsiniz.

## <a name="what-upgrade-options-are-available"></a>Hangi yükseltme seçenekleri kullanılabilir?      

Kuruluşlar çeşitli yükseltme seçeneklerini dikkate almalıdır:

- **Şirket içi sunucularınızı ve uygulamalarınızı yükseltin.** şirket içinde Office ürünleri ve sunucu uygulamalarını kullanıyorsanız aşağıdaki planlama içeriğine bakın:<br/> 

  |Office 2007 ürün ve hizmetleri|Office 2010 ürün ve hizmetleri|
  |---|---|
  |[Office 2007](/DeployOffice/office-2007-end-support-roadmap) (Masaüstü)|[Office 2010](/DeployOffice/office-2010-end-support-roadmap) (Masaüstü)|
  |[Exchange 2007](exchange-2007-end-of-support.md)|[Exchange 2010](exchange-2010-end-of-support.md)|
  |[SharePoint 2007](sharepoint-2007-end-of-support.md)|[SharePoint 2010](upgrade-from-sharepoint-2010.md)|
  |[Office İletişim Sunucusu](/skypeforbusiness/plan-your-deployment/upgrade)|[Lync Server 2010](/skypeforbusiness/plan-your-deployment/upgrade)|
  |[Project Server 2007](project-server-2007-end-of-support.md)|[Project Server 2010](project-server-2010-end-of-support.md)|
  |[PerformancePoint Server 2007](pps-2007-end-of-support.md)||
 
- **Microsoft 365 veya Office 365 ile karma bir çözüm uygulayın.** Karma çözüm, şirket içi sunucularınızı ve uygulamalarınızı ve bunların bulut eşdeğerlerini kullanır. Buluta aşamalı olarak taşınıyorsanız veya bazı sunucu ve uygulamaları şirket içinde tutmanız gerekiyorsa, karma bir çözüm kuruluşunuz için uygun olabilir. Daha fazla bilgi için bkz. [Microsoft bulut mimarisi modelleri](../solutions/cloud-architecture-models.md). 
    
- **Microsoft 365 veya Office 365 ile buluta gitme.** Birçok müşteri için buluta geçmek verimli ve uygun maliyetli bir çözümdür. Buluta eksiksiz bir şekilde geçmek kurulumu ve sürekli yönetimi kolaylaştırır. Bu seçenek tüm en son özellikleri ve güvenlik güncelleştirmelerini sorunsuz bir şekilde sağlar. Daha fazla bilgi için bu makalenin [Microsoft 365 nedir?](#what-is-microsoft-365) bölümüne bakın.
    
## <a name="can-i-get-help-for-my-organization"></a>Kuruluşum için yardım alabilir miyim?

Yükseltmenizi planlama konusunda yardım istiyorsanız aşağıdaki seçeneklerden birini veya daha fazlasını göz önünde bulundurun:

- Bir iş ortağı veya toplu lisanslama uzmanıyla çalışın. [Microsoft 365 iş ortağınızı veya kurumsal bayinizi bulun](https://support.office.com/article/b6c18a9b-2aed-4c84-9d75-af709160258c.aspx). 

- Kuruluşunuz uygun sayıda Microsoft 365 lisansı satın alırsa, FastTrack ekibimiz kurulum sürecinde size yardımcı olabilir. Daha fazla bilgi için bkz. [Microsoft 365 için FastTrack](https://www.microsoft.com/fasttrack/microsoft-365).

- Küçük bir kuruluşun parçasıysanız veya kuruluşunuzun Office yükseltmesini kendiniz halletmeyi tercih ediyorsanız bkz. [Microsoft 365 İş kullanıcılarınızı en son Office istemcisine yükseltme](/office365/admin/setup/upgrade-users-to-latest-office-client). 
  
## <a name="im-a-home-user-what-do-i-do"></a>Ev kullanıcısıyım. Ne yapacağım?

Evde Office 2007 veya Office 2010 kullanıyorsanız aşağıdaki yükseltme seçeneklerini göz önünde bulundurun:

- **tarayıcıda ücretsiz olarak Office kullanın.** Tarayıcınızda Office dosyaları oluşturun, görüntüleyin ve düzenleyin. İnternet erişimi olan herhangi bir cihazdan bu dosyalara erişim elde edin. 

  [Web üzerinde Office](https://products.office.com/office-online/documents-spreadsheets-presentations-office-online) [Web için Word](https://go.microsoft.com/fwlink/p/?linkid=746664), [Web için Excel](https://go.microsoft.com/fwlink/p/?linkid=746665), [Web için PowerPoint, Web için OneNote](https://go.microsoft.com/fwlink/p/?linkid=746666), [Sway](https://go.microsoft.com/fwlink/p/?linkid=746674), [E-posta](https://go.microsoft.com/fwlink/p/?linkid=746676), [](https://go.microsoft.com/fwlink/p/?linkid=746675) [Takvim](https://go.microsoft.com/fwlink/p/?linkid=746678) ve [OneDrive](https://go.microsoft.com/fwlink/p/?linkid=746679). Başlamak için [Office.com](https://office.com) adresini ziyaret edin ve [Microsoft hesabınızı](https://account.microsoft.com/account) kullanarak oturum açın. Microsoft hesabınız yoksa [Office.com](https://office.com) adresinden bir hesap oluşturabilirsiniz.

- **Microsoft 365 Aile deneyin.** Sizin için nasıl çalıştığını görmek için [bir Microsoft 365 Aile](https://www.microsoft.com/microsoft-365/p/microsoft-365-family/cfq7ttc0k5dm?rtc=2&activetab=pivot:overviewtab) deneme sürümü başlatın. Microsoft 365 Aile ile OneDrive ile bulut depolamanın keyfini çıkaracaksınız.

  Windows 7 desteği [14 Ocak 2020'de sona erdi](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support). Office 365 Ev veya Office 365 Personal ile sağlanan ve Windows 7 cihazda çalışan Word, Excel, PowerPoint, Outlook, Publisher ve Access sürümleri güvenlik güncelleştirmeleri alır ancak özellik güncelleştirmelerini almaz. Bu uygulamaların özellik güncelleştirmelerini almaya devam etmek için [Windows 7 cihazlarınızı Windows 10 yükseltin](https://support.microsoft.com/help/12435/windows-10-upgrade-faq).
    
- **Ev &amp; öğrenci Office satın alın.** Bu seçeneği belirlerseniz, tek seferlik satın alma işlemi yapar ve Windows PC veya Mac bilgisayarınıza Office yüklersiniz. Bu satın alma bir abonelik değil; bir bilgisayar için tek seferlik, kalıcı kullanım lisansıdır. [Gereksinimleri](https://office.com/systemrequirements) görüntüleyin ve bir sürüm seçin.

  - Windows bilgisayarınız Windows 10 çalıştırıyorsa, [Office Ev & Öğrenci 2019'u](https://www.microsoft.com/p/office-home-student-2019/cfq7ttc0k7c8) almayı göz önünde bulundurun.

  - Windows bilgisayarınız Windows 7, 8 veya 8.1 çalıştırıyorsa ve şu anda Windows 10 yükseltmiyorsanız, Office Home & Student 2016'yı veya başka bir Microsoft Office sürümünü almayı göz önünde bulundurun. Yetkili bir satıcıdan alabilirsiniz.
     
    Windows 7 desteği [14 Ocak 2020'de sona erdi](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support). Microsoft artık bunun için güvenlik güncelleştirmeleri sağlamaz. Windows 7 cihazlarınızı sürekli güvenlik, özellik güncelleştirmeleri ve sürekli destek için Windows 10 yükseltin.

Şimdi yükseltmemeyi seçerseniz, Office uygulamalarınız [zaman çizelgelerine](https://support.microsoft.com/lifecycle/search/13615) göre çalışmaya devam eder. Ancak, güvenlik güncelleştirmelerini veya yeni ve geliştirilmiş özellikleri almak için yükseltmeniz gerekir.
   
## <a name="next-steps"></a>Sonraki adımlar

- [Office 2007 sunucuları ve istemcilerinden yükseltme](upgrade-from-office-2007-servers-and-products.md)
- [Office 2010 sunucuları ve istemcilerinden yükseltme](upgrade-from-office-2010-servers-and-products.md)
   
## <a name="related-topics"></a>İlgili konular
  
[Microsoft Yaşam Döngüsü İlkesi](/lifecycle/)