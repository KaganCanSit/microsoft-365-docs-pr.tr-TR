---
title: kiracı hizmetinin durumunu Microsoft 365 Lighthouse görüntüleme
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için kiracı hizmet durumunu görüntülemeyi öğrenin.
ms.openlocfilehash: c5cfed4449fbdbb6cb63bc80dfd8e23ca4d5c4bb
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023623"
---
# <a name="view-tenant-service-health-in-microsoft-365-lighthouse"></a>kiracı hizmetinin durumunu Microsoft 365 Lighthouse görüntüleme

Microsoft 365 Lighthouse'de yönettiğiniz kiracıların hizmet durumunu görüntüleyebilirsiniz. Hizmet durumu Microsoft Intune, Azure Active Directory (Azure AD) kimlik hizmetleri ve mobil cihaz yönetimi (MDM) bulut hizmetleri gibi çeşitli hizmetler için olaylar ve öneriler içerir. Yönetilen kiracılarınızdan kaçının olaylardan etkilendiğini de görebilirsiniz. Örneğin, kiracılarınızdan biri sorun yaşıyorsa, Hizmet durumu sayfasını denetleyebilir ve bunun devam eden bir çözümle ilgili bilinen bir sorun olup olmadığını veya son bir değişikliğin bunları etkileyip etkilemediğini belirleyebilirsiniz. Bu, sorun giderme ve destek çağrılarını azaltma konusunda size zaman kazandırabilir.

Lighthouse'da oturum açamıyorsanız, iş ortağı kiracınızda oturum açmanızı engelleyen bilinen sorunları denetlemek için [Microsoft 365 hizmet durumu sayfasını](https://status.office365.com/) kullanabilirsiniz. Ayrıca, belirli hizmet olaylarıyla ilgili bilgileri görmek için Twitter'da [@MSFT365status](https://twitter.com/MSFT365Status) takip etmek için kaydolun.

## <a name="before-you-begin"></a>Başlamadan önce

Hizmet durumunu görüntülemek için iş ortağı kiracısında şu özellik kümesine sahip bir Azure AD rolüne sahip olmanız gerekir: **microsoft.office365.serviceHealth/allEntities/allTasks**. Azure AD rollerinin listesi için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Tüm kiracılar için hizmet durumunu görüntüleme

1. Lighthouse'un sol gezinti bölmesinde **Hizmet durumu'ı** seçin.

2. **Hizmet durumu** sayfasında, aşağıdakiler de dahil olmak üzere geçerli hizmet durumunu gözden geçirin:

   - Toplam olay sayısı
   - Yönetilen kiracılardan herhangi birini etkileyen toplam öneri sayısı
   - Etkin olay içeren hizmet sayısı.

3. **Tüm hizmetler** sekmesinde hizmete göre sorunları gözden geçirin.

4. **Tüm sorunlar** sekmesinde tüm geçerli sorunları gözden geçirin.

## <a name="review-issue-details"></a>Sorun ayrıntılarını gözden geçirme

1. Lighthouse'un sol gezinti bölmesinde **Hizmet durumu'ı** seçin.

2. **Hizmet durumu** sayfasında **Tüm hizmetler** veya **Tüm sorunlar** sekmesini seçin.

3. Listeden bir sorun seçin.

4. Sorun ayrıntıları bölmesinde sorun türü, etkilenen kiracılar, kullanıcı etkisi ve sorun geçmişi gibi ayrıntılı bilgileri gözden geçirin.

**Etkilenen kiracılar** sekmesinde, etkilenen kiracıların listesini virgülle ayrılmış değerler (.csv) dosyasına aktararak bunu destek ekiplerinizle paylaşabilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 hizmet durumunu denetleme](/microsoft-365/enterprise/view-service-health) (makale)\
[Microsoft 365 Lighthouse ile ilgili bilinen sorunlar](m365-lighthouse-known-issues.md) (makale)
