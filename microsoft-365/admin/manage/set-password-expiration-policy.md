---
title: Kuruluşunuzun parola süre sonu ilkesini belirleyin
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: Bir yöneticinin, iş, okul veya kar amacı gütmeyen kuruluş için parola süre sonu ilkesi ayarlamasını Microsoft 365 yönetim merkezi.
ms.openlocfilehash: 9ba871a166169a0125b68808c124b10802424dfd
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011829"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Kuruluşunuzun parola süre sonu ilkesini belirleyin

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale, bir işletme, okul veya kar amacı gütmeyen kuruluş için parola süre sonu ilkesi belirleyen kişilere yöneliktir. Bu adımları tamamlamak için yönetici hesabınızla oturum Microsoft 365 gerekir. [Yönetici hesabı nedir?](/microsoft-365/admin/add-users/about-admin-roles).

Yönetici olarak, kullanıcı parolalarının süresinin belirli sayıda gün sonunda dolmasını sağlayabilir veya parolaları süresi hiçbir zaman dolmayacak şekilde ayarlayabilirsiniz. Varsayılan olarak, parolaların süresi hiç dolmay olarak ayarlanmıştır.

Güncel araştırma, zorunlu parola değişikliklerinin kesinlikle yarardan çok zarara neden olduğunu göstermektedir. Bunlar, kullanıcıları daha zayıf parolalar kullanmaya, parolaları yeniden kullanmaya ya da saldırganlar tarafından kolayca tahmin edilebilecek şekilde güncellemeye itmektedir. Çok faktörlü kimlik [doğrulamasını etkinleştirmenizi öneririz](../security-and-compliance/set-up-multi-factor-authentication.md). Parola ilkesi hakkında daha fazla bilgi edinmek için Parola ilkesi [önerileri'ne göz atabilirsiniz](../misc/password-policy-recommendations.md).

Bu adımları gerçekleştirmek [için genel](../add-users/about-admin-roles.md) yönetici olmak gerekir.

Kullanıcıysanız, parolanızı süresi hiç dolmayacak şekilde ayarlamak için gereken izinleriniz yoktur. İş veya okulunuzun teknik desteğinden, bu makaledeki adımları sizin için uygulamalarını isteyin.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="set-password-expiration-policy"></a>Parola süre sonu ilkesini ayarlama

Belirli bir süre sonra kullanıcı parolalarının süresinin dolmasını ayarlamak istiyorsanız aşağıdaki adımları izleyin.

1. Kuruluş Microsoft 365 yönetim merkezi Altında Güvenlik ayarları <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**&** gizlilik</a> **sekmesine Ayarlar**.

    Genel yönetici değilseniz, Güvenlik ve gizlilik seçeneğini görmüyorsanız.
  
1. **Parola süre sonu ilkesini** seçin.
  
1. Kullanıcıların parolalarını değiştirmek zorunda açmalarını istemiyorsanız, Kullanıcı parolalarını süresi dolmak üzere birkaç gün sonra süresi dolacak şekilde **ayarla'nın yanındaki kutunun işaretini kaldırın**.

1. Parolaların ne sıklıkla süre sonunun geleceğini tuşlayın. 14 ile 730 arasında bir gün sayısı seçin.
  
1. İkinci kutuya, kullanıcılara parola süresinin dolacağının ne zaman bildirileceğini yazın ve sonra **Kaydet**’e tıklayın. 1 ile 30 arasında bir gün sayısı seçin.

> [!IMPORTANT]
> Parola süre sonu bildirimleri artık web uygulamaları veya Office yönetim merkezinde [desteklenmiyor](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Parola süre sonu özelliği hakkında bilmeniz gereken önemli noktalar
  
Yalnızca Outlook uygulamasını kullanan kişilerin, önbellekte süresi dolana kadar Microsoft 365 parolalarını sıfırlamaları zorunlu olmayacaktır. Bu, gerçek sona erme tarihinden sonra birkaç gün sürebilir. Bu durumun yönetici düzeyinde geçici çözümü yoktur.

## <a name="prevent-last-password-from-being-used-again"></a>Son parolanın yeniden kullanılmasını engelleme

Kullanıcılarının eski parolaları geri dönüşümlerini engellemek için şirket içi Active Directory'de (AD) parola geçmişini zorlayarak bunu yapmaya devam edin. Bkz [. Özel parola ilkesi oluşturma](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

Azure AD'de, kullanıcı bir parolayı değiştirse son parola yeniden kullanılamaz. Parola ilkesi, doğrudan Azure AD'de oluşturulan ve yönetilen tüm kullanıcı hesaplarına uygulanır. Bu parola ilkesi değiştirilemez. Bkz [. Azure AD parola ilkeleri](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Kullanıcı parola karmalarını şirket içi Active Directory'den Azure AD'ye (Kullanıcı Microsoft 365) eşitleme

Bu makale, yalnızca bulut kullanan kullanıcıların (Azure AD) süre sonu ilkesini ayarlamaya yöneliktir. Parola karması eşitlemesi, geçişli kimlik doğrulama veya ADFS gibi şirket içi federasyon kullanan karma kimlikli kullanıcılar için geçerli değildir.
  
Kullanıcı parola karmalarını şirket içi AD'den Azure AD'ye eşitlemeyi öğrenmek için bkz. [Azure AD Connect eşitlemesiyle parola karması eşitlemesi gerçekleştirme](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>E-postada parola ilkeleri ve hesap Azure Active Directory

Azure Active Directory'de daha fazla parola ilkeleri ve kısıtlaması kullanabilirsiniz. Daha fazla [bilgi için parola ilkeleri ve hesap kısıtlamaları Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) göz atabilirsiniz.

## <a name="update-password-policy"></a>Parolayı güncelleştirme İlkesi

Aşağıdaki Set-MsolPasswordPolicy cmdlet'i, belirtilen etki alanı veya kiracının parola ilkesine güncelleştirme sağlar ve parolanın değişmeden önce geçerli olduğu süresini belirtir.

Belirli bir etki alanı veya kiracı için parola ilkesi güncelleştirme hakkında bilgi edinmek için [bkz. Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>İlgili içerik

[Kullanıcıların kendi parolalarını sıfırlamasına izin verme](../add-users/let-users-reset-passwords.md) (makale)/

[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)
