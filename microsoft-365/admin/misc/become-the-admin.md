---
title: Şirket içi yöneticiyi teslim alma gerçekleştirme
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
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
description: Kendi kendine kullanıcı Microsoft 365'de self servis kayıt tarafından oluşturulan, yöneticisi olmayan bir hesabın hesabını almak için e-posta ve etki alanı sahipliğinizi doğrulamayı Microsoft 365.
ms.openlocfilehash: 1201ea967fb829e43433cb5ed49f073b1d862728
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019471"
---
# <a name="perform-an-internal-admin-takeover"></a>Şirket içi yöneticiyi teslim alma gerçekleştirme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

Yöneticiyseniz ve self servis kullanıcı kaydolan tarafından oluşturulan yönetilanmamış bir hesabın hesabını almak için, bu makaledeki adımları takip edinerek bir iç yöneticiyi kullanımdan çıkarabilirsiniz.

> [!NOTE]
> Azure AD kullanan herhangi bir bulut hizmetine self servis kayıt, kullanıcıya yönelik olmayan veya "gölgeli" bir Azure AD dizinine ekler ve unmanaged bir hesap oluşturur. Yönetimi olmayan hesap, genel yönetici olmayan bir dizindir. Bir hesabın yönetilip yönetilil olmadığını belirlemek için bkz. [Kiracı Türünü Belirleme](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Başlamadan önce

Bir kullanıcı e-posta Microsoft 365 hizmetleri için oturum aya ise, o kullanıcı için otomatik olarak bir hesap oluşturulur. Yönetici, hesapta kullanıcıları yönetmek veya başka Microsoft 365 hizmetleri satın almak istiyorsa, yöneticinin yönetimini devretmek için aşağıdaki adımları takip eden yönetici olması gerekir.

## <a name="step-1-verify-your-email-address"></a>1. Adım: E-posta adresinizi doğrulama

> [!NOTE]
> If self servis is enabled in your account, users can subscribe to free services such as Power BI, on their own. Bu hizmetler özel olarak, self servis kullanıcı aboneliğinin yönetici olarak almak istediğiniz yöneti olmayan hesabı oluşturduğu durumlarda kullanım için hazırlar. 1. Adımda, yöneticiyi kaldırma sihirbazını başlatmak için Power BI'i kullanarak kaldırmak istediğiniz etki alanının kullanıcı hesabını oluşturabilir ve böylelikle yönetnemeyen etki alanı hesabının yöneticisi siz olursiniz.

1. Ücretsiz deneme sürümüne Power BI için Power BI [sitesine](https://powerbi.com) gidin ve **Ücretsiz** >  denemeyi **başlat'ı** seçin (Diğerleriyle paylaş kutusunda Power BI Pro seçin. 

2. Kurum adının (örneğin) etki alanı adını kullanan bir kullanıcı hesabıyla kaydolabilirsiniz `powerbiadmin@contoso.com`. Hesabınız zaten kullanıyorsa geçerli parolanızı kullanarak oturum açın.

3. E-postanızı doğrulama **kodunu kontrol edin** ve e-posta adresinizi doğrulamak için kodu girin.

## <a name="step-2-create-a-new-account-for-admin-access"></a>2. Adım: Yönetici erişimi için yeni bir hesap oluşturma

1. Doğrulama kodunu girerken yeni bir hesap oluşturabilirsiniz bir sayfaya getirisiniz.

2. Kullanıcı adı ve parola alanlarını kullanmak istediğiniz hesap ile doldurun ve sonra hesabı oluşturma adımlarını tamamlayın.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>3. Adım: Etki alanı sahipliğini doğrulama ve yönetici olma

1. 2. Adımı tamamlandıktan sonra, sol gezinti bölmesindeki yönetim merkezi simgesini seçin (alternatif olarak, bir tarayıcıya gidin ve buraya yazın `https://admin.microsoft.com`).

    Yöneticiyi teslim alma sihirbazına yönlendirildiniz.

2. **Sonraki'yi** seçin ve etki alanı kayıt şirketine bir TXT kaydı ekleyerek, sahip olmak istediğiniz etki alanının sahibi olduğunu doğrulayın.

    Sihirbaz, hem eklemeniz için TXT kaydını hem de kayıt şirketinizin web sitesine bir bağlantı ve adım adım yönergelere ulaşacak bir bağlantı sağlar.

3. Şimdi **yöneticisiniz sayfasında, Yönetim** merkezine **git'i seçin**.

    Hesabı yönetim merkezinde yönetmek için gereken yönetici ayrıcalıklarına sahipsiniz. Örneğin, hesap kullanıcılarını ve gruplarını yönetebilir, yeni abonelik satın alabilirsiniz, kullanıcı atamaları yapabilecek ve hesap etki alanlarını yönetebilirsiniz.

    Etki alanınızı başka bir hesaba eklemek için bu hesaptan kaldırmak için bkz [. Başka bir hesaptan etki alanı kaldırma](remove-a-domain-from-another-account.md).
  
## <a name="related-content"></a>İlgili içerik

YouTube: [Power BI ve Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk)(video)\
[Azure AD'de yöneticiyi devretme](/azure/active-directory/users-groups-roles/domains-admin-takeover) (makale)\
[Kurumda self servis kaydolmayı kullanma](self-service-sign-up.md) (makale)\
[Hizmet Power BI rolünü anlama](/power-bi/service-admin-role) (makale)