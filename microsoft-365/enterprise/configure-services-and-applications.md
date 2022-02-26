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
description: Posta Microsoft 365 Kurumsal, posta hizmetleri ve uygulamaları SharePoint, Exchange gibi Skype Kurumsal.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: d9e756ccdab188cf34228989a58e174f0fc2cfbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973728"
---
# <a name="configure-microsoft-365-enterprise-services-and-applications"></a>Hizmet Microsoft 365 Kurumsal uygulamaları yapılandırma

Temel [ayarlama yönergelerimiz,](../admin/setup/setup.md) kullanıcı hizmetlerinizi ve uygulamalarınızı Microsoft 365 en kısa sürede herkesin kullanımına alamanıza yardımcı olur. Bazen, bunları herkes kullanmaya başlamadan önce yapılandırmayı tercih edilir. Örneğin, posta yönlendirmeyi, dosya depolama alanını veya paylaşım ilkelerini yapılandırmak istiyorsanız. 
  
Kurulum sırasında yardım almak Microsoft 365, FastTrack hizmetleri ve hizmetleri için Kurulum **[](https://www.microsoft.com/fasttrack/microsoft-365)** [Microsoft 365'Office 365 kullanın](setup-guides-for-microsoft-365.md).
  
|**Hizmetler & uygulamaları**|**Kaynaklar**|
|:-----|:-----|
|**Microsoft 365 Paketi** |- [Oturum Açma Sayfası'Microsoft 365 şirket markanızı ekleme](https://support.office.com/article/Add-your-company-branding-to-Office-365-Sign-In-Page-a1229cdb-ce19-4da5-90c7-2b9b146aef0a) <br> - [Yardım bölmesinde özelleştirilmiş yardım masası bilgilerini Microsoft 365 ekleme](https://support.office.com/article/Add-customized-help-desk-info-to-the-Office-365-help-pane-9dd9b104-68f7-4d49-9a30-82561c7d79a3) <br> - [Azure AD ve diğer uygulamalarla tümleştirme ekleyin](https://support.office.com/article/Integrated-Apps-and-Azure-AD-for-Office-365-administrators-cb2250e3-451e-416f-bf4e-363549652c2a).  <br> - [E-posta, takvim, belgeler](https://support.office.com/Article/Learn-more-about-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2) ve sohbetle işbirliği yapmak için grupları kullanma hakkında daha fazla bilgi <br> - [Mobil cihaz yönetimini mobil cihazda etkinleştirme ve Microsoft 365](https://support.office.microsoft.com/article/Manage-mobile-devices-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) <br> - [Ekran Microsoft 365 izleme](monitor-connectivity.md) |
|**E-posta** <br> (Exchange Online) | - Exchange [Deployment Assistant'ı kullanarak Exchange Karma ile Exchange hazır olun](https://technet.microsoft.com/exdeploy2013)  <br> - Özelleştirilmiş [Exchange için](https://aka.ms/office365setup) geçiş danışmanını kullanın  <br> - [Ayarlama Exchange Online Protection](/exchange/standalone-eop/set-up-your-eop-service) |
|**Siteler** <br> (SharePoint Online) | [SharePoint Server 2013 için -Karma işlevselliğini yapılandırma](/SharePoint/hybrid/hybrid)<br> - [SharePoint Online'da site](https://support.office.com/article/Create-and-use-site-templates-60371B0F-00E0-4C49-A844-34759EBDD989) şablonları oluşturma ve kullanma <br> - Ek özellikleri [SharePoint ve yapılandırmak için](https://support.office.com/article/SharePoint-Online-Planning-Guide-for-Office-365-for-business-d5089cdf-3fd2-4230-acbd-20ecda2f9bb8) [SharePoint Çevrimiçi Planlama Kılavuzu'SharePoint](https://aka.ms/spoguidance) çevrimiçi dağıtım danışmanını kullanın <br> - [Video portalınızı yönetme](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da) |
|**IM ve çevrimiçi toplantılar** <br> (Skype Kurumsal Online) | - [Lync Server 2013 veya Skype Kurumsal](/previous-versions/office/lync-server-2013/lync-server-2013-lync-server-2013-hybrid) [2015 için karma işlevselliğini yapılandırma](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)<br> - [Skype Kurumsal Online'ı ayarlama](https://support.office.com/article/Set-up-Skype-for-Business-Online-40296968-e779-4259-980b-c2de1c044c6e) ve arama yönlendirme, konferans çağrısı ve paylaşım gibi sık kullanılan özellikleri yapılandırma  <br> - Özelleştirilmiş [Skype Kurumsal için](/MicrosoftTeams/faq-journey) dağıtım danışmanını kullanın |
| **Dosya depolama & paylaşımı** <br> (OneDrive İş ve SharePoint Online) | - [Dosya depolama Microsoft 365 paylaşımını ayarlama](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_WhatDif): Dosyaları depolamak için OneDrive İş ve SharePoint Online ekip sitelerini ne zaman saklamanız gerektiğini öğrenin <br> - [Dosya depolamayı ve paylaşımı ayarlama](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_MoveDocsVideo): Dosyaları OneDrive İş ekip sitenize SharePoint kolay olduğunu görme <br> - [Dosya depolamayı ve paylaşımı ayarlama](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_Store): Dosyaları bilgisayarınıza ve ekip sitenize OneDrive İş için tüm adımları izleyin. Dosya paylaşımı için ipuçlarını öğrenin <br> - Özelleştirilmiş [OneDrive İş için Kurulum](https://aka.ms/OD4Bguidance) Kılavuzu'nı kullanın |
|**Microsoft 365 uygulamaları** | - Microsoft 365 bir dağıtım veya yükseltme [Office](/deployoffice) planlamayla ilgili yardım almak için Kurumlar için Microsoft 365 Uygulamaları Kılavuzu'Kurumlar için Microsoft 365 Uygulamaları kullanmaları gerekir.  <br> - [Power BI için Microsoft 365 yönetim merkezi](https://support.office.com/article/Power-BI-for-Office-365-Admin-Center-Help-5e391ecb-500c-47a3-bd0f-a6173b541044) <br> - [Office Delve yöneticileri Microsoft 365 bilgi](https://support.office.com/article/Office-Delve-for-Office-365-admins-54f87a42-15a4-44b4-9df0-d36287d9531b) <br> - [Sway hakkında sık sorulan sorular](https://support.office.com/article/446380fa-25bf-47b2-996c-e12cb2f9d075) <br> - [Yeni bir e-Project Online](https://support.office.com/article/Get-started-with-Project-Online-e3e5f64f-ada5-4f9d-a578-130b2d4e5f11).  <br> - [Microsoft Intune dağıtım danışmanı](/mem/intune/) |
|**Enterprise Social** <br> (Yammer) | - [E-Yammer'i Microsoft 365](https://support.office.com/article/Plan-for-Yammer-integration-with-Office-365-4086681f-6de1-4d39-aa72-752b2af1cbd7)  <br> - Özelleştirilmiş [Yammer Enterprise için Kurulum](https://aka.ms/yammerdeploy) Kılavuzu'nı kullanın |