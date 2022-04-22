---
title: Microsoft 365 Lighthouse'de self servis parola sıfırlamayı yönetme
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için self servis parola sıfırlamayı yönetmeyi öğrenin.
ms.openlocfilehash: 4d618eb80dfd4a37ad5548de997b3d551bcbbf85
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022371"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'de self servis parola sıfırlamayı yönetme

Microsoft 365 Lighthouse, iş ortaklarının Azure Active Directory (Azure AD) self servis parola sıfırlamayı (SSPR) yönetmesini sağlar. SSPR, kullanıcılara yönetici veya yardım masası katılımı olmadan parolalarını değiştirme veya sıfırlama olanağı sağlar. Kullanıcının hesabı kilitliyse veya parolasını unutursa, engellemesini kaldırmak ve işe geri dönmek için istemleri izleyebilir. Bu özellik, kullanıcı cihazında veya uygulamada oturum açamazsa yardım masası çağrılarını ve üretkenlik kaybını azaltır.

## <a name="before-you-begin"></a>Başlamadan önce

Kiracı listede görünmeden önce aşağıdaki koşulların karşılanması gerekir:

- Müşteri kiracısının her kullanıcı için bir Azure AD Premium lisansı olmalıdır. Hangi lisansların SSPR'yi desteklediği hakkında daha fazla bilgi için bkz. [Self servis parola sıfırlama Azure Active Directory için lisans gereksinimleri](/azure/active-directory/authentication/concept-sspr-licensing).

- Müşteri kiracısının Lighthouse içinde etkin olması gerekir. Kiracının etkin olup olmadığını belirlemeyi öğrenmek için [Microsoft 365 Lighthouse'daki Windows 365 (Bulut Bilgisayarlar) sayfasına genel bakış bölümüne](m365-lighthouse-tenants-page-overview.md) bakın.

## <a name="view-sspr-tenant-status"></a>SSPR kiracı durumunu görüntüleme

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Parola sıfırlama** sekmesini seçin.

Parola sıfırlama sekmesi, önerilen ayarlar, SSPR'ye kaydolmamış kullanıcı sayısı ve yönettiğiniz kuruluşlar genelinde SSPR dağıtım ilerleme durumunun kiracıya göre ayrıntılı dökümü aracılığıyla SSPR'yi etkinleştiren kiracılara genel bir bakış sağlar.

## <a name="enable-sspr-for-a-tenant"></a>Kiracı için SSPR'yi etkinleştirme

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Parola sıfırlama** sekmesini seçin.

3. Kiracı listesinden bir kiracı seçerek ayrıntılar bölmesini açın.

4. Azure Active Directory 'a (Azure AD) gitmek için **Azure Active Directory SSPR ayarlarını düzenle'yi** seçin.

5. Azure AD'de tüm veya seçili kullanıcılar için SSPR'yi etkinleştirin. Daha fazla bilgi edinmek için bkz[. Öğretici: Kullanıcıların self servis parola sıfırlama Azure Active Directory kullanarak hesap kilidini açmalarını veya parolaları sıfırlamalarını sağlama](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Kullanıcılara SSPR'ye kaydolmalarını bildirme

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Parola sıfırlama** sekmesini seçin.

3. Kiracı listesinden bir kiracı seçerek ayrıntılar bölmesini açın.

4. Bildirmek istediğiniz kullanıcıları seçin.

5. **E-posta oluştur'u** seçin.

Lighthouse varsayılan e-posta istemcinizi açar ve E-posta iletisini SSPR'ye kaydolma yönergeleriyle önceden doldurulur. Seçilen tüm kullanıcılar Gizli satırına eklenir. Kullanıcılara tek tek e-posta göndermeyi tercih ederseniz, kullanıcı adının yanındaki e-posta simgesini seçebilirsiniz.

Farklı bir e-posta hesabı kullanmak istiyorsanız, kullanıcı listesini bir dosyaya aktarabilirsiniz. Ayrıca, şirketinizin markasıyla özelleştirebileceğiniz örnek e-posta şablonlarını da indirebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Azure Active Directory self servis parola sıfırlama dağıtımı planlama](/azure/active-directory/authentication/howto-sspr-deployment) (makale)\
[Öğretici: Kullanıcıların Azure Active Directory self servis parola sıfırlama (makale)\ kullanarak hesap kilidini açmalarını veya parolaları sıfırlamalarını sağlama](/azure/active-directory/authentication/tutorial-enable-sspr)
[Azure AD'de SSPR'yi etkinleştirme ve yapılandırma](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (video)\
[Microsoft 365 Lighthouse'de çok faktörlü kimlik doğrulamasını yönetme](m365-lighthouse-manage-mfa.md) (makale)
