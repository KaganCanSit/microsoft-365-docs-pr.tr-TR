---
title: Hizmet Microsoft 365 Kurumsal uygulamaları yapılandırma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 7cec08a5-97fd-4761-b23b-ef3d66519e30
f1.keywords:
- NOCSH
description: Posta Microsoft 365 Kurumsal, posta hizmetleri ve uygulamaları SharePoint, Exchange gibi Microsoft Teams.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 8375fe3b43c2671dd7134768610b4b99c683d740
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635075"
---
# <a name="configure-microsoft-365-enterprise-services-and-applications"></a>Hizmet Microsoft 365 Kurumsal uygulamaları yapılandırma

Temel [ayarlama yönergelerimiz,](../admin/setup/setup.md) kullanıcı hizmetlerinizi ve uygulamalarınızı Microsoft 365 en kısa sürede herkesin kullanımına alamanıza yardımcı olur. Bazen, bunları herkes kullanmaya başlamadan önce yapılandırmayı tercih edilir. Örneğin, posta yönlendirme, dosya depolama veya paylaşım ilkelerini yapılandırmak istiyorsanız. 
  
Kurulum sırasında yardım almak Microsoft 365, FastTrack hizmetleri ve hizmetleriyle ilgili kurulum **[](https://www.microsoft.com/fasttrack/microsoft-365)** Microsoft 365 [Office 365 kullanın](setup-guides-for-microsoft-365.md).
  
|**Hizmetler & uygulamaları**|**Kaynaklar**|
|:-----|:-----|
|**Microsoft 365 Paketi** |- [Oturum Açma Sayfasında Şirket Microsoft 365 ekleme](https://support.office.com/article/Add-your-company-branding-to-Office-365-Sign-In-Page-a1229cdb-ce19-4da5-90c7-2b9b146aef0a) <br> - [Yardım bölmesinde özelleştirilmiş yardım masası bilgilerini Microsoft 365 ekleme](https://support.office.com/article/Add-customized-help-desk-info-to-the-Office-365-help-pane-9dd9b104-68f7-4d49-9a30-82561c7d79a3) <br> - [Azure AD ve diğer uygulamalarla tümleştirme ekleyin](https://support.office.com/article/Integrated-Apps-and-Azure-AD-for-Office-365-administrators-cb2250e3-451e-416f-bf4e-363549652c2a).  <br> - [Mobil cihazda mobil cihaz yönetimini etkinleştirme ve Microsoft 365](https://support.office.microsoft.com/article/Manage-mobile-devices-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) <br> - [Ekran Microsoft 365 izleme](monitor-connectivity.md) |
|**E-posta** <br> (Exchange Online) | - Exchange [Deployment Assistant'ı kullanarak Exchange Karma ile Exchange hazır olun](https://technet.microsoft.com/exdeploy2013)  <br> - Özelleştirilmiş [kurulum Exchange için](https://aka.ms/office365setup) geçiş danışmanını kullanın  <br> - [Ayarlama Exchange Online Protection](/exchange/standalone-eop/set-up-your-eop-service) |
|**Siteler** <br> (SharePoint) | - [SharePoint Server için SharePoint yapılandırma](/SharePoint/hybrid/hybrid) <br> - Ek [özellikleri SharePoint planlamak ve](https://support.office.com/article/SharePoint-Online-Planning-Guide-for-Office-365-for-business-d5089cdf-3fd2-4230-acbd-20ecda2f9bb8) yapılandırmak [için SharePoint Planlama Kılavuzu'SharePoint](https://aka.ms/spoguidance) destek dağıtım danışmanını kullanın|
|**IM ve çevrimiçi toplantılar** <br> (Teams) | - [Microsoft Teams dağıtımına genel bakış](/microsoftteams/deploy-overview)<br> - [Toplantılar ve konferanslar Microsoft Teams](/microsoftteams/deploy-meetings-microsoft-teams-landing-page) <br> - [Sesli Teams planınızı planlama](/microsoftteams/cloud-voice-landing-page) |
| **Dosya depolama & paylaşımı** <br> (OneDrive ve SharePoint) | - [Dosya depolama Microsoft 365 paylaşımını ayarlama](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_WhatDif): Dosyaları depolamak için OneDrive kullanmalı ve ekip sitelerinden SharePoint zaman öğrenin <br> - Özelleştirilmiş [kurulum OneDrive için Kurulum](https://aka.ms/OD4Bguidance) Kılavuzu'nı kullanın |
|**Microsoft 365 uygulamaları** | - Microsoft 365 bir dağıtım veya yükseltme [Office planlamayla](/deployoffice) ilgili yardım almak için Kurumlar için Microsoft 365 Uygulamaları Kılavuzu'Kurumlar için Microsoft 365 Uygulamaları kullanmaları gerekir.  <br> - [Power BI için Microsoft 365 yönetim merkezi](https://support.office.com/article/Power-BI-for-Office-365-Admin-Center-Help-5e391ecb-500c-47a3-bd0f-a6173b541044) <br> - [Office Delve yöneticileri Microsoft 365 bilgi](https://support.office.com/article/Office-Delve-for-Office-365-admins-54f87a42-15a4-44b4-9df0-d36287d9531b) <br> - [Çalışma hakkında sık sorulan Sway](https://support.office.com/article/446380fa-25bf-47b2-996c-e12cb2f9d075) <br> - [Kullanmaya başlayın'Project Online](https://support.office.com/article/Get-started-with-Project-Online-e3e5f64f-ada5-4f9d-a578-130b2d4e5f11).  <br> - [Microsoft Intune dağıtım danışmanı](/mem/intune/) |
|**Enterprise Social** <br> (Yammer) | - [Yammer ile Microsoft 365](https://support.office.com/article/Plan-for-Yammer-integration-with-Office-365-4086681f-6de1-4d39-aa72-752b2af1cbd7)  <br> - Özelleştirilmiş [kurulum Yammer Enterprise için](https://aka.ms/yammerdeploy) Kurulum Kılavuzu'nı kullanın |
