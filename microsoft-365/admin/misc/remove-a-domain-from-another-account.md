---
title: Başka bir hesaptan etki alanı kaldırma
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
description: Kendi kendine kullanıcı oturum açma ve oturum açma ile oluşturulan, unmanaged Microsoft 365.
ms.openlocfilehash: 0a7cf07a70e241c0b40f28159f31b0c86766bc1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325677"
---
# <a name="perform-an-internal-admin-takeover"></a>Şirket içi yöneticiyi teslim alma gerçekleştirme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

Yöneticiyseniz ve self servis kullanıcı kaydolan tarafından oluşturulan yönetnemeyen bir hesabın hesabını almaksanız, bunu şirket içi yöneticiyi teslim alma gerçekleştirerek gerçekleştirebilirsiniz.

> [!NOTE]
> Azure AD kullanan herhangi bir bulut hizmetine self servis kayıt, kullanıcıya yönelik olmayan veya "gölgeli" bir Azure AD dizinine ekler ve unmanaged bir hesap oluşturur. Yönetimi olmayan hesap, genel yönetici olmayan bir dizindir. Bir hesabın yönetilip yönetilil olmadığını belirlemek için bkz. [Kiracı Türünü Belirleme](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Başlamadan önce

Bazı durumlarda, başka biri bu etki alanı adıyla ilişkilendirilmiş bir e-posta adresini kullanarak e-postanıza zaten Microsoft 365 etki alanı ekleyesiniz. Ancak, etki alanını yönetilemeyen diğer hesaptan kaldırabilir ve bunu kuruluş tarafından yönetilen hesabınıza  eklersiniz.

Etki alanını diğer hesaptan kaldırmadan ve hesabınıza eklemeden önce yöneti olmayan hesaba katılmanız ve o hesabın yöneticisi olmanız gerekir. Ardından, etki alanını yönetilemeyen hesaptan kaldırır, hesabınızla yeniden oturum kaldırır ve etki alanını yönetilen hesabınıza eklersiniz.

Bu makaledeki adımlar yalnızca diğer hesaba katılmayı (1. ve 2. Adım) ana hatlarıyla açıklar ve yöneticiyi alma sihirbazında verilen adımları takip eder ve yönetnemeyen hesapta yönetici olur (3. Adım).

Yönetilen hesabın yöneticisi olduktan sonra, etki alanını yönetimiş hesaptan kaldırabilir ve hesabınıza ebilirsiniz. 

## <a name="step-1-verify-your-email-address"></a>1. Adım: E-posta adresinizi doğrulama

> [!NOTE]
> If self servis is enabled in your account, users can subscribe to free services such as Power BI, on their own. Bu hizmetler özel olarak, self servis kullanıcı aboneliğinin yönetici olarak almak istediğiniz yöneti olmayan hesabı oluşturduğu durumlarda kullanım için hazırlar. 1. Adımda, yöneticiyi kaldırma sihirbazını başlatmak için Power BI'i kullanarak kaldırmak istediğiniz etki alanının kullanıcı hesabını oluşturabilir ve böylelikle yönetnemeyen etki alanı hesabının yöneticisi siz olursiniz.

1. Ücretsiz deneme sürümüne Power BI için Power BI [sitesine](https://powerbi.com) gidin ve **Ücretsiz** >  denemeyi **başlat'ı** seçin (Diğerleriyle paylaş kutusunda Power BI Pro seçin. 

2. Kurum adının (örneğin) etki alanı adını kullanan bir kullanıcı hesabıyla kaydolabilirsiniz `powerbiadmin@contoso.com`. Hesabınız zaten kullanıyorsa geçerli parolanızı kullanarak oturum açın.

3. E-postanızı doğrulama **kodunu kontrol edin** ve e-posta adresinizi doğrulamak için kodu girin.

## <a name="step-2-create-a-new-account-for-admin-access"></a>2. Adım: Yönetici erişimi için yeni bir hesap oluşturma

1. Doğrulama kodunu girerken yeni bir hesap oluşturabilirsiniz bir sayfaya getirisiniz.

2. Kullanıcı adı ve parola alanlarını kullanmak istediğiniz hesap ile doldurun, ardından Başlat'ı **seçin**.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>3. Adım: Etki alanı sahipliğini doğrulama ve yönetici olma

1. 2. Adımı tamamlandıktan sonra, sol gezinti bölmesindeki yönetim merkezi simgesini seçin (alternatif olarak, bir tarayıcıya gidin ve buraya yazın `https://admin.microsoft.com`).

    Yöneticiyi teslim alma sihirbazına yönlendirildiniz.

1. **Sonraki'yi** seçin ve etki alanı kayıt şirketine bir TXT kaydı ekleyerek, sahip olmak istediğiniz etki alanının sahibi olduğunu doğrulayın. 

    Sihirbaz, hem eklemeniz için TXT kaydını hem de kayıt şirketinizin web sitesine bir bağlantı ve adım adım yönergelere ulaşacak bir bağlantı sağlar.

1. Şimdi **yöneticisiniz sayfasında, Yönetim** merkezine **git'i seçin**.

    Artık, etki alanını diğer hesaptan kaldırmak için gereken yönetici ayrıcalıklarına sahipsiniz. 
## <a name="related-content"></a>İlgili içerik

YouTube: Power BI ve Video)\ için IT Yöneticilerini [Power BI Microsoft 365 3](https://www.youtube.com/watch?v=xt5EsrQBZZk) adım
[Azure AD'de yöneticiyi devretme](/azure/active-directory/users-groups-roles/domains-admin-takeover) (makale)\
[Kurumda self servis kaydolmayı kullanma](self-service-sign-up.md) (makale)\
[Hizmet Power BI rolünü anlama](/power-bi/service-admin-role) (makale)
