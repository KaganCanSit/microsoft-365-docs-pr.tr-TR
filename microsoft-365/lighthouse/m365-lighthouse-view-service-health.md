---
title: Kiracı hizmet durumunu görüntüleme
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Hizmet Sağlayıcıları (MSP) için Microsoft 365 Lighthouse hizmet durumunu görüntülemeyi öğrenin.
ms.openlocfilehash: 21315d0ea616fcd2865879d9d8aec66b17830208
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324613"
---
# <a name="view-tenant-service-health"></a>Kiracı hizmet durumunu görüntüleme

Aynı kiracıda, yönetmekte olduğu kiracıların hizmet durumunu Microsoft 365 Lighthouse. Hizmet durumu; Microsoft Intune, Azure Active Directory (Azure AD) kimlik hizmetleri ve mobil cihaz yönetimi (MDM) bulut hizmetleri gibi çeşitli hizmetlere yönelik olayları ve tavsiyeleri içerir. Ayrıca, yönetilen kiracılardan kaç tanenizin olaylardan etkilendiğini de görebilirsiniz. Örneğin, kiracılardan biri sorun yaşıyorsa, Hizmet durumu sayfasını kontrol edip bunun çözüm için devam eden bilinen bir sorun mu yoksa yakın zamanda yapılan bir değişikliğin onları etki edip e-postayla ilgili bir sorun olup olmadığını öğrenebilirsiniz. Bu, sorun giderme ve destek aramalarını azaltma zamandan tasarruf sağlar.

Deniz Feneri'nde oturum aasanız, [Microsoft 365](https://status.office365.com/) hizmet durumu sayfasını kullanarak iş ortağı kiracınıza oturum açmanızı engelleyen bilinen sorunları kontrol edebilirsiniz. Ayrıca, belirli hizmet olayları [@MSFT365status](https://twitter.com/MSFT365Status) görmek için Twitter'da takip etmek için oturum açma.

## <a name="before-you-begin"></a>Başlamadan önce

Hizmet durumunu görüntülemek için, iş ortağı kiracısında şu özellik kümesine sahip bir Azure AD rolüne ihtiyacınız vardır: **microsoft.office365.serviceHealth/allEntities/allTasks**. Azure AD rollerinin listesi için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Tüm kiracıların hizmet durumunu görüntüleme

1. Deniz Feneri'nin sol gezinti bölmesinde Hizmet **durumu'ni seçin**.

2. Hizmet **durumu sayfasında** , geçerli hizmet durumunu gözden geçirin; şöyle:

   -   Olay sayısı toplamı
   -   Yönetilen kiracılardan herhangi birini etkileyen tavsiyelerin toplam sayısı
   -   Etkin olayları olan hizmetlerin sayısı.

3. Tüm hizmetler **sekmesinde,** hizmetlere göre sorunları gözden geçirebilirsiniz.

4. Tüm sorunlar **sekmesinde,** tüm geçerli sorunları gözden geçirebilirsiniz.

## <a name="review-issue-details"></a>Sorun ayrıntılarını gözden geçirme

1. Deniz Feneri'nin sol gezinti bölmesinde Hizmet **durumu'ni seçin**.

2. Hizmet durumu **sayfasında Tüm** hizmetler veya **Tüm sorunlar** **sekmesini** seçin.

3. Listeden bir sorun seçin.

4. Sorun ayrıntıları bölmesinde, sorun türü, etkilenen kiracılar, kullanıcı etkisi ve sorun geçmişi gibi ayrıntılı bilgileri gözden geçirebilirsiniz.

Kiracı **etkilenenler sekmesinde** , etkilenen kiracıların listesini bir virgülle ayrılmış değerler (.csv) dosyasına aktarabilir ve böylelikle bu dosyayı destek ekipleriyle paylaşabilirsiniz.

## <a name="related-content"></a>İlgili içerik
[Hizmet durumunu denetleme Microsoft 365](/microsoft-365/enterprise/view-service-health) (makale)\
[E-Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) bilinen sorunlar (makale)