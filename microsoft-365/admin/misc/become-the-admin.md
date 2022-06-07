---
title: İç yönetici devralma işlemi gerçekleştirme
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Microsoft 365'te self servis kullanıcı kaydı tarafından oluşturulan yönetilmeyen bir hesabı devralmak için e-postanızı ve etki alanı sahipliğini doğrulamayı öğrenin.
ms.openlocfilehash: b930e9d4774dc9271d4bcbd93ffb9e5ced577dab
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922141"
---
# <a name="internal-admin-takeover"></a>İç yönetici devralma

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

Yöneticiyseniz ve self servis kullanıcı kaydı tarafından oluşturulan yönetilmeyen bir hesabı devralmak istiyorsanız, bu makaledeki adımları izleyerek iç yönetici devralma işlemi gerçekleştirebilirsiniz.

> [!NOTE]
> Azure AD kullanan herhangi bir bulut hizmetine self servis kaydolma, kullanıcıyı yönetilmeyen veya "gölge" bir Azure AD dizinine ekler ve yönetilmeyen bir hesap oluşturur. Yönetilmeyen hesap, genel yönetici olmayan bir dizindir. Bir hesabın yönetilip yönetilmediğini belirlemek için bkz. [Kiracı Türünü Belirleme](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Başlamadan önce

Bir kullanıcı e-posta adresi kullanarak Microsoft 365 hizmetlerine kaydolduğunda, bu kullanıcılar için otomatik olarak bir hesap oluşturulur. Yönetici hesapta kullanıcıları yönetmek veya ek Microsoft 365 hizmetleri satın almak istiyorsa, yönetici devralma işlemini gerçekleştirmek için bu adımları izleyerek hesapta yönetici olması gerekir.

## <a name="step-1-verify-your-email-address"></a>1. Adım: E-posta adresinizi doğrulama

> [!NOTE]
> Hesabınızda self servis etkinleştirildiyse, kullanıcılar Power BI gibi ücretsiz hizmetlere kendi başlarına abone olabilir. Bu hizmetler özellikle bir self servis kullanıcı aboneliğinin yönetici olarak devralmak istediğiniz yönetilmeyen hesabı oluşturduğu durumlarda kullanılır. 1. Adımda, yönetilmeyen etki alanı hesabının yöneticisi olabilmeniz için Power BI kullanarak yönetici devralma sihirbazını başlatarak kaldırmak istediğiniz etki alanı için bir kullanıcı hesabı oluşturursunuz.

1. Power BI'a kaydolmak için [Power BI sitesine](https://powerbi.com) gidin ve Ücretsiz  > **Başlangıç ücretsiz deneme sürümünü** **başlat'ı** seçin (Power BI Pro ile paylaş kutusunda). 

2. Kuruluşunuzun etki alanı adını (gibi `powerbiadmin@contoso.com`) kullanan bir kullanıcı hesabıyla kaydolun. Hesabınız zaten kullanılıyorsa geçerli parolanızı kullanarak oturum açın.

3. **Doğrulama kodu** için e-postanızı denetleyin ve e-posta adresinizi doğrulamak için kodu girin.

## <a name="step-2-create-a-new-account-for-admin-access"></a>2. Adım: Yönetici erişimi için yeni bir hesap oluşturma

1. Doğrulama kodunu girdiğinizde, yeni bir hesap oluşturabileceğiniz bir sayfaya getirilirsiniz.

2. Kullanıcı adı ve parola alanlarını kullanmak istediğiniz hesapla doldurun ve ardından hesabı oluşturma adımlarını tamamlayın.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>3. Adım: Etki alanı sahipliğini doğrulama ve yönetici olma

1. 2. Adımı tamamladıktan sonra sol gezinti bölmesindeki yönetim merkezi simgesini seçin (alternatif olarak, bir tarayıcıya gidin ve yazın `https://admin.microsoft.com`).

    Yönetici devralma sihirbazına yönlendirilirsiniz.

2. **İleri'yi** seçin ve etki alanı kayıt şirketinize bir TXT kaydı ekleyerek devralmak istediğiniz etki alanının sahibi olduğunuzu doğrulayın.

    Sihirbaz size eklenecek TXT kaydının yanı sıra kayıt şirketinizin web sitesine bir bağlantı ve adım adım yönergelerin bağlantısını sağlar.

3. **Artık yöneticisiniz** sayfasında Yönetim **merkezine git'i** seçin.

    Yönetim merkezinde hesabı yönetmek için gereken yönetici ayrıcalıklarına sahipsiniz. Örneğin, hesap kullanıcılarını ve gruplarını yönetebilir, yeni abonelikler satın alabilir, kullanıcı atamaları yapabilir ve hesap etki alanlarını yönetebilirsiniz.

    Etki alanınızı başka bir hesaba ekleyebilmek için bu hesaptan kaldırmak istiyorsanız bkz. Etki [alanını başka bir hesaptan kaldırma](remove-a-domain-from-another-account.md).
  
## <a name="related-content"></a>İlgili içerik

YouTube: [Power BI ve Microsoft 365 için BT Yöneticisi Devralma işlemini gerçekleştirmenin üç adımı](https://www.youtube.com/watch?v=xt5EsrQBZZk) (video)\
[Azure AD'de yönetici devralma](/azure/active-directory/users-groups-roles/domains-admin-takeover) (makale)\
[Kuruluşunuzda self servis kaydolmayı kullanma](self-service-sign-up.md) (makale)\
[Power BI hizmet yöneticisi rolünü anlama](/power-bi/service-admin-role) (makale)