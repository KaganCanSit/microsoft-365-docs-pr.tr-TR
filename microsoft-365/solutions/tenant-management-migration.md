---
title: Adım 4. Kurumsal kiracılar Microsoft 365 kiracınız için geçiş
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Kiracınız Windows cihazlarınızı, Office uygulamalarını ve Office sunucularınızı Microsoft 365 geçirebilirsiniz.
ms.openlocfilehash: 1892ae3da900f1c940866a2b2a3c70c1d6cb5db3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011788"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>Adım 4. Kurumsal kiracılar Microsoft 365 kiracınız için geçiş

Çoğu kuruluşta, birden çok işletim sistemi, istemci yazılımı ve sunucu yazılımı sürümü içeren heterojen bir ortam vardır. Microsoft 365 sürümleri, IT altyapının önemli bileşenlerinin en güvenli sürümlerini içerir. Ayrıca bulut teknolojilerinden yararlanmak için tasarlanmış üretkenlik özelliklerini de içerir.

Kurumsal tümleşik ürünler paketinin Microsoft 365 değerini en üst düzeye çıkarmak için, bu sürümü geçirmek üzere bir strateji planlamaya ve uygulamaya başlayabilirsiniz:

| Kaynak | Hedef |
|:-------|:-----|
| Windows 7 ve Windows 8.1 | Windows 10 Enterprise |
| Office cihazlarına yüklenmiş istemci ürünleri | Microsoft 365 Kurumsal Uygulamaları |
| Office sunucu ürünlerinde şirket içi sunucularda yüklü | Microsoft 365'daki eşdeğer bulut tabanlı Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>Windows 10'a Windows 10

Kurumsal Microsoft 365 lisans için her kullanıcı bir lisans Windows 10 Enterprise. 7 veya daha fazla Windows cihazlarınızı geçirmek Windows 8.1 yerinde yükseltme işlemiyle devam edin. *14 Ocak 2020 Windows 7 destek sona erdi*. 

Bir uygulamayı yerinde yükseltmenin Windows 10 Enterprise başka yükleme yöntemleri için bkz. [Windows 10 senaryolarında önerilir](/windows/deployment/windows-10-deployment-scenarios). Ayrıca, kendi [başına Windows 10 dağıtımı da](/windows/deployment/planning/) planabilirsiniz.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>Kurumlar için Microsoft 365 Uygulamaları'a Kurumlar için Microsoft 365 Uygulamaları

Microsoft 365 için Kurumlar için Microsoft 365 Uygulamaları, Microsoft bulutundan yüklenmiş ve güncelleştirilir Office istemci ürünlerinin (Word, PowerPoint, Excel ve Outlook) bir sürümüdür. Daha fazla bilgi için bkz[. Kurumlar için Microsoft 365 Uygulamaları](/deployoffice/about-microsoft-365-apps).

2019 veya daha eski sürümlerde bilgisayarlarınızı Office tutmak yerine aşağıdaki adımları izleyin:

1. Kullanıcılarınız için Microsoft 365 lisansı alın ve attayabilirsiniz.
2. Bilgisayarlarında Office 2013 veya Office 2016 yüklemelerini kaldırın.
3. Tek Kurumlar için Microsoft 365 Uygulamaları veya bir IT sürümü sırasında yükleme. Daha fazla bilgi için bkz[. Dağıtım dağıtım Microsoft 365 Uygulamaları](/deployoffice/deployment-guide-microsoft-365-apps).

Kurumlar için Microsoft 365 Uygulamaları güncelleştirmeleri ve yeni özellik güncelleştirmelerini otomatik olarak yükleyebilir ve gelişmiş güvenlik ve üretkenlik için Microsoft 365 bulut tabanlı hizmetlerden faydalanabilirsiniz.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>Şirket içi sunucuları ve verileri başka sunuculara Microsoft 365

Microsoft 365 kurumsal, web tarayıcıları ve Outlook istemcisi gibi Office sunucu yazılımının şirket içi sürümleriyle aynı araçlardan bazılarını kullanan Office sunucu hizmetlerinin bulut tabanlı sürümlerini içerir. Bulut tabanlı bu hizmetler, güvenlik ve yeni özellikler için otomatik olarak güncelleştirilir. Geçiş sonrasında, IT departmanınız şirket içi sunucuları korumak ve güncelleştirmek için gereken zamandan tasarruf sağlar.

Belirli kullanıcı ve iş yükleri için kullanıcıları ve verileri Microsoft 365 kullanın:

- [Posta kutularını şirket içi posta kutusundan Exchange Server posta kutusuna Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [SharePoint Server'dan SharePoint Online'a veri SharePoint geçirme](/sharepointmigration/migrate-to-sharepoint-online)
- [Skype Kurumsal Online'dan Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>Tüm kuruluşa geçiş

Tüm organizasyon ürünlerinizi Kurumsal Kurumsal'daki ürünler ve hizmetlere taşıma hakkında daha iyi bir resim Microsoft 365 için bu geçiş posterini indirin:

[![Postere geçiş posterini Microsoft 365 görüntüsü.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Bu iki sayfalık poster, var olan altyapının envanterini inimini yapmak için hızlı bir yol sağlar. Kurumsal hizmetlere yönelik web'de ürün veya hizmete taşıma ile ilgili Microsoft 365 için kullanın. Ürün ve Windows Office, cihaz yönetimi, kimlik ve tehdit koruması, bilgi koruma ve uyumluluk gibi diğer altyapı ve güvenlik öğelerini gösterir.

## <a name="results-of-step-4"></a>Adım 4'in sonuçları

Kiracınız için geçiş Microsoft 365, belirlediniz:

- 7 veya Windows çalıştıran Windows 8.1 cihazlar ve bunları güncelleştirme planınız Windows 10 Enterprise.
- Hangi cihazların istemci uygulamalarını Office ve bunları kurumsal uygulamalara uygun Microsoft 365 planla.
- Hangi şirket içi Office sunucu hizmetlerinin, sunucu hizmetlerinin Microsoft 365 ve verilerini geçirme planına geçir olması gerekir.

İşte, şirket içi sunucuların geçişi tamamlanmış bir kiracı örneği.

![Şirket içi sunucuların tamamlanmış geçişiyle bir kiracı örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

Bu çizimde, kuruluşun sahip olduğu kuruluşlar:

- Şirket içi posta kutuları, Exchange Server posta kutularına Exchange Online.
- Şirket içi SharePoint Sunucusu siteleri ve verileri, şirket içinde SharePoint'a Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>Geçiş için sürekli bakım

Sürekli olarak şunları yapmak zorundayabilirsiniz:

- Posta kutunuzu geçirme işleminin durumuna Exchange, geçiş işlemini Exchange Online geçişe yapmaya devam edin.
- Şirket içi geçiş işleminizin durumuna bağlı SharePoint, geçiş işlemini SharePoint için Microsoft 365 geçişe devam edin.

## <a name="next-step"></a>Sonraki adım

[![5. Adım. Cihaz ve uygulama yönetimini dağıtın.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

Cihaz ve [uygulama yönetimini dağıtmak için cihaz](tenant-management-device-management.md) ve uygulama yönetimiyle devam edin.