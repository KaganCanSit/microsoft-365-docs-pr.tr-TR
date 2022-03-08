---
title: Microsoft 365 ServiceNow yapılandırmasıyla tümleştirmeye genel bakış
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: ServiceNow için Kapsam Sertifikalı uygulama yükleme ve yapılandırma kılavuzu.
ms.openlocfilehash: dc69f6210eda4ba04dfd0aecf9795bfcba2efe22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324333"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Microsoft 365 ServiceNow yapılandırmasıyla tümleştirmeye genel bakış

Aşağıdaki içerik en düşük **1 Microsoft 365.7** sürümüne sahip destek tümleştirme uygulaması için geçerlidir.

**Microsoft 365 desteği tümleştirmesi,** yardım, Microsoft 365 ve hizmet durumunu ServiceNow örnekleriyle tümleştirmenize olanak sağlar. Microsoft'un bilinen ve bildirilen sorunlarını araştırebilir, Olayları çözebilir, Microsoft'un önerilen çözümlerini kullanarak görevleri tamamlar ve gerekirse Microsoft insan destekli destek ekibine bildirebilirsiniz.

ServiceNow **Microsoft 365 destek tümleştirme** uygulaması için, [ServiceNow Mağazası'ne gidin](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Temel özellikler

Bunlar, ServiceNow örneğinde Microsoft 365 destek tümleştirme uygulamasıyla elde edecekleri temel özelliklerdir:

- Hizmet Durumu Olayları: Kullanıcı etkisi, kapsamı, geçerli durum ve sonraki beklenen güncelleştirme gibi bilinen Microsoft hizmet durumu olayları hakkında bilgiler. Makine öğrenimi kullanılarak, ServiceNow olayları, kısa açıklama alanı temel alarak Microsoft hizmet durumu olaylarıyla eş almaktadır.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Hizmet Durumu Olayları açıklama alanı.":::

- Önerilen çözümler: Makine öğrenimi tarafından desteklenen Microsoft'un hassas hedefli çözümlerini ve ilgili makaleleri öneren görev ve olay açıklamaları kullanılır. Ayrıca, gerekirse başka çözümler bulmak için Arama'ya da kullanabilirsiniz.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Önerilen çözümler açıklama alanı.":::

- Microsoft hizmet isteği: Sorunları Microsoft destek aracıları ile iletişime alın ve durumunuzla ilgili durum güncelleştirmeleri alın.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Servis isteği formu.":::

## <a name="prerequisites"></a>Önkoşullar

### <a name="permissions-requirements"></a>İzin gereksinimleri

Bu kılavuza devam etmek için, tüm süreç boyunca aşağıdaki izinlerin kullanılabilir ve yapılandırılmış olduğundan emin olun:

- Azure Active Directory AD AAD oluşturan bir yönetici (yönetici)

- ServiceNow yöneticisi

- Microsoft 365 kiracı yöneticisi

### <a name="configuration-highlights"></a>Yapılandırma vurguları

Destek **tümleştirmesi Microsoft 365 için**:

- Hem giden hem de Microsoft Azure Active Directory AAD API çağrılarının kimlik doğrulaması için uygulamaları Microsoft Azure Active Directory(AAD) uygulamasına kaydettirin.

- Hem giden hem de gelen Microsoft Azure AD için ServiceNow varlıkları oluşturun.

- ServiceNow örneğini bu yönetim portalı aracılığıyla Microsoft Microsoft 365 tümleştirin.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="ServiceNow tümleştirme diyagramı.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>ServiceNow ortamlarında uygulama bağımlılıkları

İzinler gerekli:

- oauthentity\_

- oauthentityprofile\_\_

Uygulama Microsoft 365 Tümleştirme uygulaması yüklendikten sonra, iki Uygulama Çapraz Kapsamı erişimi oluşturulur. Başarılı bir şekilde oluşturulmazsa, bunları el ile oluşturun.

## <a name="setup-the-integration"></a>Tümleştirmeyi ayarlama

Uygulamayı indirdikten sonra, kar ortamınıza Microsoft 365 kurulum sihirbazına gidin ve kurulum işlemini tamamlayın.
:::image type="content" source="../../media/154124985-76e13e7d-b32e-4741-830b-bbb110d3ecbf.png" alt-text="Kar kurulum sihirbazı":::

Aşağıdaki sayfaları ziyaret ederek adımlar hakkında daha fazla bilgi edinebilirsiniz:
- ServiceNow ortamınız gelen web hizmeti çağrıları için Temel Kimlik Doğrulama'ya (ServiceNow kullanıcı kimlik bilgileriyle erişim) izin verdiyse, [ServiceNow Basic Authentication](servicenow-basic-authentication.md) ile destek Microsoft 365 ayarlama konusunda verilen yönergeleri izleyin.
- ServiceNow ortamınız gelen web hizmeti aramalarında Temel Kimlik Doğrulamasına (ServiceNow kullanıcı kimlik bilgileriyle erişim) izin vermiyorsa, [Azure AD Kimlik](servicenow-aad-oauth-token.md) Doğrulaması Belirteci ile destek Microsoft 365 ayarlama konusunda verilen yönergeleri izleyin.
  - Kimlik Doğrulama Belirteci'nin doğru çalışması için bu yapılandırma AAD SSO kiracısı gerekir.

Her özelliği anlamak için bkz. [Microsoft 365 tümleştirmeyi destekleme](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> Bu uygulama düzenlemeye tabi veya kısıtlanmış ortamlarda desteklenmiyor.
