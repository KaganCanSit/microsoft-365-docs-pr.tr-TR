---
title: Microsoft Yönetilen Masaüstü'nden Uygulamalar
description: Uygulamaların nasıl iş işlemekte olduğunu açıklar; bunları paketle, dağıtın ve destekle birlikte.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ce43080c284c4c15be5a8799f70a43de611ff9ba
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027553"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'nden Uygulamalar

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->

## <a name="apps-generally"></a>Uygulamalar genel olarak

Microsoft, Microsoft Yönetilen Masaüstü'ne katılmak Microsoft 365 E3 E5 lisansının yanı sıra bazı önemli uygulamaları da içerir. Bununla birlikte, bu uygulamaları sağlamız halde tamamlamanız gereken bazı sorumluluklar ve işlemler vardır.

Ayrıca, Microsoft Intune'un dağıtım potansiyel satışını kullanarak self servis aracılığıyla Şirket Portalı veya gerekli bir arka plan yüklemesi aracılığıyla kullanıcılarınıza Microsoft olmayan başka uygulamalar da dağıtabilirsiniz.

## <a name="apps-provided-by-microsoft"></a>Microsoft tarafından sağlanan uygulamalar

Microsoft Yönetilen Masaüstü lisansınıza dahil edilen uygulamalar, Enterprise için Microsoft 365 Uygulamaları Standart Paketi'ne (Word, Excel, PowerPoint, Outlook, Publisher, Access, Teams ve OneNote.)

Microsoft Project ve Visio Tıkla-Çalıştır sürümleri varsayılan olarak dahil değildir, ancak bu sürümlerin eklenmelerini de talepebilirsiniz.  Bu uygulamalar hakkında daha fazla bilgi için bkz[. Microsoft yönetilen Microsoft Project cihazlarına Microsoft Visio Yükleme](../get-started/project-visio.md).

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Microsoft'un sağlamamız uygulamaları desteklemek için yaptığı iş

Microsoft, dahil edilen uygulama dağıtım, güncelleştirme ve destek için tam Kurumlar için Microsoft 365 Uygulamaları sağlayacaktır. Microsoft Project ve Visio *Tıkla-Çalıştır sürümleri varsayılan* olarak dahil değildir. Bununla birlikte, Microsoft Yönetilen Masaüstü, DAĞıTıM yöneticinizin lisansları yönetmesine ve bu uygulamaları organizasyonunıza uygun şekilde dağıtmasına olanak sağlayan dağıtım grupları sağlar. Microsoft, Microsoft Yönetilen Masaüstü destek kanalları aracılığıyla bu uygulamaların kullanıcılarını destekleyecektir.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Sağlamamız uygulamaları desteklemek için ne yapmak gerekir?

Yine de bu uygulamalarla bazı şeyler yapmak gerekir:

| Görev | Açıklama |
| ------ | ------ |
| LisansLarı Ata | Kullanıcı lisansı için uygun lisansları almak ve kullanıcılara atamak sizin Kurumlar için Microsoft 365 Uygulamaları. |
| Güvenlik gruplarına kullanıcı ekleme | Microsoft Project veya Visio kullanıyorsanız, BU kullanıcıları uygun dağıtım gruplarına eklemesi gerekir. Bu kullanıcılar şirketten ayrılmaları durumuyla ilgili olarak, bu kullanıcılardan lisansları geri almak, IT yöneticilerinden de sorumlu olur. |
| Eklenti Microsoft 365 dağıtma | Bu uygulamalardan herhangi biri için herhangi bir Eklentiye ihtiyacınız Kurumlar için Microsoft 365 Uygulamaları, bunları 32 Windows gibi merkezi olarak dağıtın.

## <a name="apps-you-provide"></a>Sağlamakta olduğunuz uygulamalar

büyük olasılıkla iş işlemleriniz için ihtiyacınız olan başka uygulamalarınız vardır. Bu uygulamalar yalnızca Microsoft Intune dağıtım potansiyel sürümü kullanılarak Microsoft Yönetilen Masaüstü cihazlarına dağıtılabilir. Uygulama dağıtımı hakkında daha fazla bilgi için, Uygulamaları Microsoft Yönetilen Masaüstü [cihazlarına dağıtma makalesinde yer alan adımları izleyin](../get-started/deploy-apps.md).

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'ne eklenmek için kendi uygulamalarınızı hazırlama

Uygulamalarınızı gözden geçirme, denetleme:

- Microsoft Yönetilen Masaüstü uygulaması gereksinimlerinde açıklandığı gibi, uygulamaların hiçbiri [yasaklanmaz veya kısıtlanmış davranışa sahip değildir](../service-description/mmd-app-requirements.md).
- Uygulamaların, diğer uygulamalar tarafından yönetimaya hazır Microsoft Intune. Daha fazla bilgi için bkz[. Windows 10'i kullanarak uygulama Microsoft Intune](/intune/apps-windows-10-app-deploy) [dağıtımı ve](/intune/apps-add) Microsoft Intune.
- Lisans anahtarları sağlama, lisans koşullarıyla anlaşma sağlama ve sunucu bağlantılarını önceden ayarlama gibi diğer paketleme öncesi gereksinimler.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. Uygulamaları hazırlama (bu makale).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
