---
title: Kendi kendine parola sıfırlamayı yönetme
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
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse kendi kendine parola sıfırlamayı yönetmeyi öğrenin.
ms.openlocfilehash: b8367d2ed2c088d56425b08c6da5dfd55fcd84b8
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007236"
---
# <a name="manage-self-service-password-reset"></a>Kendi kendine parola sıfırlamayı yönetme

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, iş ortaklarının kendi kendine Azure Active Directory (Azure AD) parola sıfırlamayı (SSPR) yönetmelerini sağlar. SSPR, kullanıcılara yönetici veya yardım masası katılımı olmazken parolalarını değiştirme veya sıfırlama olanağı verir. Kullanıcının hesabı kilitliyse veya parolasını unutursa, kendi engellemesini kaldırmak ve işe dönmek için istemleri takip eder. Bu özellik, kullanıcı cihazında veya bir uygulamada oturum alayama geldiğinde yardım masası aramalarını ve üretkenlik kaybını azaltır.

## <a name="before-you-begin"></a>Başlamadan önce

Kiracının listede görünmesi için aşağıdaki koşulların karşı görünmesi gerekir:

- Müşteri kiracısı, her kullanıcı Azure AD Premium lisansına sahip olması gerekir. Hangi lisansların SSPR'yı desteklemesi hakkında daha fazla bilgi için bkz. Kendi [kendine parola sıfırlama Azure Active Directory gereksinimleri](/azure/active-directory/authentication/concept-sspr-licensing).

- Müşteri kiracısı, Deniz Feneri'nin içinde etkin olmalı. Kiracının etkin olup olmadığını belirlemeyi öğrenmek için Kiracılar sayfasına [Microsoft 365 Lighthouse genel bakış sayfasına bakın](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>SSPR kiracı durumunu görüntüleme

1. Deniz Feneri'nin sol gezinti bölmesinde Kullanıcılar'ı **seçin**.

2. Parola sıfırlama **sekmesini** seçin.

Parola sıfırlama sekmesi önerilen ayarlar aracılığıyla SSPR'i etkinleştiren kiracılara, SSPR için kayıtlı olmadığınız kullanıcıların sayısına ve yönetmek istediğiniz kuruluşlar genelinde SSPR dağıtımının ilerleme durumu kiracısına göre ayrıntılı çözümleme sağlar.

## <a name="enable-sspr-for-a-tenant"></a>Kiracı için SSPR'yi etkinleştirme

1. Deniz Feneri'nin sol gezinti bölmesinde Kullanıcılar'ı **seçin**.

2. Parola sıfırlama **sekmesini** seçin.

3. Kiracı listesinden, ayrıntılar bölmesini açmak için bir kiracı seçin.

4. **SSPR ayarlarını düzenle'yi Azure Active Directory** (Azure AD) Azure Active Directory için SSPR ayarlarını düzenle'yi seçin.

5. Azure AD'de, tüm veya seçili kullanıcılar için SSPR'yi etkinleştirin. Daha fazla bilgi için bkz. Öğretici: Kullanıcıların kendi kendine parola sıfırlama kullanarak hesaplarının kilidini açmalarını veya [Azure Active Directory parolalarını sıfırlamalarını etkinleştirme](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Kullanıcıları SSPR için kaydolmalarını bildirme

1. Deniz Feneri'nin sol gezinti bölmesinde Kullanıcılar'ı **seçin**.

2. Parola sıfırlama **sekmesini** seçin.

3. Kiracı listesinden, ayrıntılar bölmesini açmak için bir kiracı seçin.

4. Bildirmek istediğiniz kullanıcıları seçin.

5. **E-posta oluştur'a seçin**.

Deniz Feneri varsayılan e-posta istemcinizi açar ve E-posta iletisiyle SSPR için kaydolma yönergelerini önceden doldurmaya devam ediyor. Seçilen tüm kullanıcılar Gizli satırına dahil edilir. Tek tek kullanıcılara e-posta göndermeyi tercih ediyorsanız, kullanıcı adı'nın yanındaki e-posta simgesini seçin.

Farklı bir e-posta hesabı kullanmak için, kullanıcı listesini bir dosyaya aktarabilirsiniz. Ayrıca, şirketi markalamayla özelleştirebileceğiniz örnek e-posta şablonları da indirebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Kendi kendine Azure Active Directory sıfırlama dağıtımını planlama](/azure/active-directory/authentication/howto-sspr-deployment) (makale)\
[Öğretici: Kullanıcıların kendi kendine parola sıfırlama kullanarak hesaplarının kilidini açmalarını veya Azure Active Directory parolalarını](/azure/active-directory/authentication/tutorial-enable-sspr) sıfırlamalarını etkinleştirme (makale)\
[Azure AD'de SSPR'yi etkinleştirme ve](https://www.youtube.com/watch?v=rA8TvhNcCvQ) yapılandırma (video)\
[Çok faktörlü kimlik doğrulamasını](m365-lighthouse-manage-mfa.md) yönetme (makale)
