---
title: Diğer yöneticiler için tümleşik uygulamalar ve Azure MICROSOFT 365.
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Azure AD'de tümleşik Office 365 kaydetmeyi ve yönetmeyi, **Azure AD DC** yöneticisi veya Genel yönetici düzeyinde uygulama yetkilendirmelerine izin **vermeyi** öğrenin.
ms.openlocfilehash: ddb22c6e1be3d337fe7b54f27cae6a197f823c71
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681270"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Diğer yöneticiler için tümleşik uygulamalar ve Azure MICROSOFT 365.

Tümleşik uygulamaları yönetmek, uygulamaların kullanıcı iznini [yönetmekten daha fazlasıdır](../admin/misc/user-consent.md). Microsoft 365 REST API'lerinin ortaya çıktısı ile, kullanıcılar uygulamalara posta, takvimler, kişiler, kullanıcılar, gruplar, dosyalar ve klasörler gibi Microsoft 365 verilerine erişim izni ve zaman içinde kullanılabilir. Varsayılan olarak, kullanıcıların her uygulamaya tek tek izinler ataması gerekir. 

Ancak Azure **AD DC** yöneticisi veya Genel yönetici düzeyinde bir uygulamayı bir kez yetkilendirmek ve uygulamayı uygulama başlatıcı aracılığıyla tüm kuruluşa yetkilendirmek için bu ölçeği iyi değerlendirmez. Bunu yapmak için uygulamayı Azure Active Directory (Azure AD) olarak kaydetmeniz gerekir. Azure AD'de bir uygulamayı kaydettirmeden önce atılması gereken bazı adımlar ve bu adımların, uygulamayı kuruluş içinde yönetmenize yardımcı olduğunu biliyor Microsoft 365 vardır.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Yöneticiler için Azure AD Microsoft 365 kaynakları

Azure AD'de iş uygulamalarınızı yönetemeden önce Microsoft 365 bu iki görevi gerçekleştirmeniz gerekir.
  
|Önkoşullar|Açıklamalar|
|:-----|:-----|
|[Ücretsiz Azure AD aboneliğinizi kullanma](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Microsoft 365 abonelikleri, ücretsiz bir Azure AD aboneliğiyle birlikte gelir. Uygulamalarınızı yönetmek, kullanıcı ve grup hesaplarını oluşturmak ve yönetmek için Azure AD'i kullanabilirsiniz. Azure AD'i kullanmak için Azure portala gidip [https://portal.azure.com](https://portal.azure.com) iş veya hizmet Microsoft 365 açın.  <br/> |
|[Uygulamalar için kullanıcı iznini yönetme](../admin/misc/user-consent.md) <br/> |Üçüncü taraf uygulamaların kullanıcı bilgilerine erişmesine izin vermek ve sizin için Azure AD'de Microsoft 365 için uygulamalara yönelik kullanıcı iznini yönetmeniz gerekir. Örneğin, bir kullanıcı üçüncü taraf bir uygulama kullandığında, uygulama, kullanıcının takvimlerine erişme ve bir OneDrive klasöründeki dosyaları düzenleme izni isteyebilir.  <br/> |
   
Uygulama Microsoft 365 yönetimi, Azure AD'de uygulamaların bilgisine sahip olmak gerektirir. Size ihtiyacınız olan arka planı vermek için bu makaleleri kullanın.
  
|Makale|Açıklamalar|
|:-----|:-----|
|[Microsoft 365 uygulama başlatıcıyla tanışma](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Uygulama başlatıcıyı yeni kullanmaya devam ediyorsanız, bunun ne olduğunu ve nasıl kullanıla olduğunu merak ediyor olabilir. Uygulama başlatıcı, uygulamalarınızı uygulamalarınızı her yerden ve her yerden Microsoft 365.  <br/> |
|[Office 365 yönetimi API'leri için genel bakış](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Microsoft 365 yönetimi API'leri, en çok önem Microsoft 365 şeyleri (posta, takvimler, kişiler, kullanıcılar ve gruplar, dosyalar ve klasörler) sizin için erişim sağlar. <br/> |
|[Azure AD'de uygulamaları tümleştirme](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure AD ile tümleşik uygulamalar ve uygulamanızı kaydetme, kayıtlı bir uygulamanın ardındaki kavramları anlama ve çok kiracılı uygulamalara yönelik markalama yönergeleri hakkında bilgi edinin.  <br/> |
|[Uygulama başlatıcıya özel kutucuklar ekleme](/office365/admin/manage/customize-the-app-launcher)  <br/> |Masaüstü'Microsoft 365 başlatıcı kullanıcıların uygulamalarını bulmasını ve bu uygulamalarına erişmesini kolaylaştırır. Bu makalede, bir geliştirici olarak sizin, uygulamalarınızı kullanıcıların uygulama başlatıcısında nasıl görüntüleyebilirsiniz? Ayrıca bu kullanıcılara kullanıcı kimlik bilgilerini kullanarak çoklu oturum açma (SSO) deneyimi Microsoft 365 gerekir.  <br/> |
|[Azure AD tümleştirme öğreticileri](/azure/active-directory/saas-apps/tutorial-list) <br/> |Bu öğreticilerin amacı, üçüncü taraf SaaS uygulamaları için Azure AD SSO'nun nasıl yapılandırıldığından emin olmaktır.  <br/> |
|[Azure AD için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Azure AD, hizmet olarak kimlik sağlayarak geliştiriciler için kimlik doğrulamasını basitleştirerek, OAuth 2.0 ve OpenID Bağlan gibi endüstri standardı protokollerin yanı sıra, farklı platformlara yönelik açık kaynak kitaplıklarını da destekler ve kodlamaya hızlı bir şekilde başlamanıza yardımcı olur. Bu belge, Azure AD'nin desteklediği çeşitli senaryoları anlamanıza yardımcı olur ve nasıl başlamanız için olduğunu gösterir.  <br/> |
|[Uygulama erişimi](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD, günümüzün popüler hizmet olarak yazılım (SaaS) uygulamalarının birçoğuna kolay tümleştirme sağlar. Kimlik ve erişim yönetimi sağlar ve kullanıcıların hangi uygulama erişimine sahip olduklarını ve uygulamalarına erişmek için SSO'yı nerede kullanabileceğini keşfeden bir Erişim Paneli sunar. Bu makalede, Azure AD'ye yönelik uygulama erişimi geliştirmeleri hakkında daha fazla bilgi edinme ve onlara nasıl katkıda bulunabilirsiniz konusunda daha fazla bilgi edinmenıza olanak sağlayan ilgili kaynakların bağlantıları sağlanmıştır.  <br/> |
|[Office 365 deneyiminizi kişiselleştirme](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Her gün kullanıyorsanız uygulamaları Uygulama Başlatıcı'ya ekleyerek veya kaldırarak Microsoft 365 erişebilirsiniz.  <br/> |
