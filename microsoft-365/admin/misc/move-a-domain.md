---
title: Yöneticisi olmayan bir hesapta doğrulanmış bir etki alanını taşıma
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
description: Etki alanını hesaptan kaldırmak ve etki alanını hesabınıza eklemek için, yöneticisi olmayan bir hesaba katılmayı öğrenin.
ms.openlocfilehash: 7b7befdae4279b4b08ff076b88ed552b2bc411c3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326350"
---
# <a name="move-a-domain-verified-in-an-unmanaged-account"></a>Yöneticisi olmayan bir hesapta doğrulanmış bir etki alanını taşıma

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

Yöneticiyseniz ve Microsoft 365 hesabınıza etki alanı eklemeye çalıştınız, ancak etki alanı yönetnemeyen bir hesap için doğrulandığından engellendiyseniz, etki alanını kaldırmak ve hesabınıza eklemek için yöneti olmayan hesabın yöneticisi siz olursanız.

> [!NOTE]
> Azure AD kullanan herhangi bir bulut hizmetine self servis kayıt, kullanıcıya yönelik olmayan veya "gölgeli" bir Azure AD dizinine ekler ve unmanaged bir hesap oluşturur. Yönetimi olmayan hesap, genel yönetici olmayan bir dizindir. Bir hesabın yönetilip yönetilil olmadığını belirlemek için bkz. [Kiracı Türünü Belirleme](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type).
  
## <a name="before-you-begin"></a>Başlamadan önce

Bazı durumlarda, başka biri bu etki alanı adıyla ilişkilendirilmiş bir e-posta adresini kullanarak e-postanıza zaten Microsoft 365 etki alanı ekleyesiniz. Ancak, etki alanını diğer, yöneticisi olmayan hesaptan kaldırabilir ve kuruluş hesabınıza  eklersiniz.

İlk olarak, yönetnemeyen hesaba katılmanız ve bu hesabın yöneticisi olmanız gerekir (1. Adım - 3). Daha sonra etki alanını hesaptan kaldırabilir (4. Adım), kuruluş hesabınızla yeniden oturum açın ve etki alanını hesabınıza ekleyin (5. Adım).

## <a name="step-1-get-an-invitation-to-join-the-unmanaged-account"></a>1. Adım: Unmanaged hesabına katılma daveti al

Hesabınıza etki alanı eklemeye başladıktan sonra, birinin e-posta adresini kullanarak etki alanınıza zaten Microsoft 365 iletisi alabilirsiniz. 1. adım, diğer hesaba katılmak için bir davet talep etmek ve yöneticiyi teslim alma işleminin başlamasını sağlar.

1. Etki Alanı Ekle Microsoft 365 yönetim merkezi > **Ayarlar** >  **Domains** > **+ Etki** alanı ekle'ye gidin ve etki alanı adını ekleyin.

1. Başka kişiler etki alanı için bir e-posta adresi kullanarak zaten kayıt olduğundan etki alanını ekley parolanızın bir iletiyle karşınıza olduğunu görüyorsanız, hesap kullanıcı adınızı girin ve Daveti bana **gönder'i seçin**.

1. Geçerli hesabınızla, unmanaged hesapta oturum açın.

    E-postanıza bakarak, unmanaged hesabınıza katılmanıza yardımcı olacak daveti kontrol edin ve e-postada sağlanan bağlantıyı seçin.

    **E-posta adresinizi doğrulamak** için e-postadan doğrulama kodunu girin.

## <a name="step-2-complete-signup-with-email-instructions"></a>2. Adım: E-posta yönergeleriyle kaydolmayı tamamlama

1. Doğrulama kodunu girerken yeni bir hesap oluşturabilirsiniz bir sayfaya getirisiniz.

2. Kullanmak istediğiniz hesap ile kullanıcı adı ve parola alanlarını doldurun ve sonra hesabı oluşturma adımlarını tamamlayın.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>3. Adım: Etki alanı sahipliğini doğrulama ve yönetici olma

1. 2. Adımı tamamlandıktan sonra, sol gezinti bölmesindeki yönetim merkezi simgesini seçin (alternatif olarak, bir tarayıcıya gidin ve buraya yazın `https://admin.microsoft.com`).

    Yöneticiyi teslim alma sihirbazına yönlendirildiniz.

1. **Sonraki'yi** seçin ve etki alanı kayıt şirketine bir TXT kaydı ekleyerek, sahip olmak istediğiniz etki alanının sahibi olduğunu doğrulayın.

    Sihirbaz, hem eklemeniz için TXT kaydını hem de kayıt şirketinizin web sitesine bir bağlantı ve adım adım yönergelere ulaşacak bir bağlantı sağlar.

1. Şimdi **yöneticisiniz sayfasında, Yönetim** merkezine **git'i seçin**.

    Artık, etki alanını eski yönetemeyen hesaptan kaldırmak için gereken yönetici ayrıcalıklarına sahipsiniz.

## <a name="step-4-remove-a-domain-from-the-unmanaged-account"></a>4. Adım: Unmanaged hesabından etki alanı kaldırma

1.  >  2 **. Adımda** katıldığınız hesabın UsersActive users seçeneğine gidin ve oturum açtığınız kullanıcı adının Görünen adı'ı seçin.

1. Kullanıcı **adı'nın** **altında Kullanıcı** adını yönet'i seçin ve açılan listeden kullanıcı onmicrosoft.com seçerek o kullanıcıyı onmicrosoft etki alanına taşıma.

1. Hesabın oturumlarını ve yeni 'ı kullanarak yeniden oturum açın `username@account.onmicrosoft.com`.

1. Etki **Ayarlar** >  **Etki Alanları'ı** seçin, diğer hesaba eklemek istediğiniz etki alanını bulun ve Etki alanını **kaldır'ı seçin**.

    Varsayılan olarak başka bir etki alanı seçmeniz istenecekse, varsayılan etki onmicrosoft.com seçin.

    Etki alanını diğer kullanıcılar kullanıyorsa, onları kaldırmanız gerekir. Kullanıcıları otomatik olarak kaldırma, **etki alanınıza** el ile taşıma veya kullanıcıları tamamen kaldırma seçeneklerinden birini belirleyin.

   > [!NOTE]
   > Etki alanının hesaptan kaldırılması biraz zaman al etki alanı olarak yeniden kontrol edin. Etki alanı hesaptan kaybolursa, kaldırma işlemi tamamlanır.

1. Hesabın oturumlarını açın.

## <a name="step-5-add-the-domain-to-your-account"></a>5. Adım: Etki alanını hesabınıza ekleme

1. Etki alanını eklemek istediğiniz hesapta oturum açın.

1. Bu **hesapta etki alanı** >  sahipliğini doğrulamak ve etki alanını hesabınıza eklemeyi tamamlamak için sihirbaz adımlarıyla devam etmek için Ayarlar **Domains** > **+ Etki** Alanı Ekle'yi seçin ve ardından etki alanı adını girin.
  
## <a name="related-content"></a>İlgili içerik

[Şirket içi yöneticiyi teslim alma gerçekleştirme](become-the-admin.md) (makale)
