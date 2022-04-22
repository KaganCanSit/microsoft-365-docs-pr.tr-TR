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
description: Bir yöneticinin Microsoft 365 yönetim merkezi'da işletmeniz, okuluniz veya kar amacı gütmeyen kuruluşunuz için parola süre sonu ilkesi ayarlamayı öğrenin.
ms.openlocfilehash: ed94cb8bc3bdcc1c1f30c6cb9bf56907c83de41e
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022349"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Kuruluşunuzun parola süre sonu ilkesini belirleyin

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale, bir işletme, okul veya kar amacı gütmeyen kuruluş için parola süre sonu ilkesi belirleyen kişilere yöneliktir. Bu adımları tamamlamak için Microsoft 365 yönetici hesabınızla oturum açmanız gerekir. [Yönetici hesabı nedir?](/microsoft-365/admin/add-users/about-admin-roles).

Yönetici olarak, kullanıcı parolalarının süresinin belirli sayıda gün sonunda dolmasını sağlayabilir veya parolaları süresi hiçbir zaman dolmayacak şekilde ayarlayabilirsiniz. Varsayılan olarak, kuruluşunuz için parolaların süresi hiçbir zaman dolmaz olarak ayarlanır.

Güncel araştırma, zorunlu parola değişikliklerinin kesinlikle yarardan çok zarara neden olduğunu göstermektedir. Bunlar, kullanıcıları daha zayıf parolalar kullanmaya, parolaları yeniden kullanmaya ya da saldırganlar tarafından kolayca tahmin edilebilecek şekilde güncellemeye itmektedir. [Çok faktörlü kimlik doğrulamasını](../security-and-compliance/set-up-multi-factor-authentication.md) etkinleştirmenizi öneririz. Parola ilkesi hakkında daha fazla bilgi edinmek için [Bkz. Parola ilkesi önerileri](../misc/password-policy-recommendations.md).

Bu adımları gerçekleştirmek için [genel yönetici](../add-users/about-admin-roles.md) olmanız gerekir.

Kullanıcıysanız, parolanızı süresi hiç dolmayacak şekilde ayarlamak için gereken izinleriniz yoktur. İş veya okulunuzun teknik desteğinden, bu makaledeki adımları sizin için uygulamalarını isteyin.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken işe alımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="set-password-expiration-policy"></a>Parola süre sonu ilkesini ayarlama

Belirli bir süre sonra kullanıcı parolalarının süresinin dolmasını ayarlamak istiyorsanız aşağıdaki adımları izleyin.

1. Microsoft 365 yönetim merkezi Kuruluş <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Ayarlar altındaki Güvenlik & gizlilik** sekmesine</a> gidin.

    Genel yönetici veya güvenlik yöneticisi değilseniz Güvenlik ve gizlilik seçeneğini görmezsiniz.
  
1. **Parola süre sonu ilkesini** seçin.
  
1. Kullanıcıların parolaları değiştirmesini istemiyorsanız, **Kullanıcı parolalarını birkaç gün sonra sona erecek şekilde ayarla'nın** yanındaki kutunun işaretini kaldırın.

1. Parolaların ne sıklıkla süre sonunun geleceğini tuşlayın. 14 ile 730 arasında bir gün sayısı seçin.
  
1. İkinci kutuya, kullanıcılara parola süresinin dolacağının ne zaman bildirileceğini yazın ve sonra **Kaydet**’e tıklayın. 1 ile 30 arasında bir gün sayısı seçin.

> [!IMPORTANT]
> Parola süre sonu bildirimleri artık Office web uygulamalarında veya [yönetim merkezinde desteklenmemektedir](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Parola süre sonu özelliği hakkında bilmeniz gereken önemli noktalar
  
Yalnızca Outlook uygulamasını kullanan kişiler, önbellekte süresi dolana kadar Microsoft 365 parolalarını sıfırlamak zorunda kalmaz. Bu, gerçek sona erme tarihinden sonra birkaç gün sürebilir. Bu durumun yönetici düzeyinde geçici çözümü yoktur.

## <a name="prevent-last-password-from-being-used-again"></a>Son parolanın yeniden kullanılmasını engelleme

Kullanıcılarınızın eski parolaları geri dönüştürmesini engellemek istiyorsanız, şirket içi Active Directory (AD) içinde parola geçmişini zorunlu kılarak bunu yapabilirsiniz. Bkz. [Özel parola ilkesi oluşturma](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

Azure AD'de, kullanıcı parolayı değiştirdiğinde son parola yeniden kullanılamaz. Parola ilkesi, doğrudan Azure AD'de oluşturulan ve yönetilen tüm kullanıcı hesaplarına uygulanır. Bu parola ilkesi değiştirilemez. Bkz. [Azure AD parola ilkeleri](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Kullanıcı parola karmalarını bir şirket içi Active Directory Azure AD(Microsoft 365) ile eşitleme

Bu makale, yalnızca bulut kullanan kullanıcıların (Azure AD) süre sonu ilkesini ayarlamaya yöneliktir. Parola karması eşitleme, doğrudan kimlik doğrulaması veya ADFS gibi şirket içi federasyon kullanan karma kimlik kullanıcıları için geçerli değildir.
  
Kullanıcı parola karmalarını şirket içi AD'den Azure AD'ye eşitlemeyi öğrenmek için bkz. [Azure AD Connect eşitlemesiyle parola karması eşitlemesi gerçekleştirme](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Azure Active Directory'da parola ilkeleri ve hesap kısıtlamaları

Azure Active Directory'de daha fazla parola ilkesi ve kısıtlama ayarlayabilirsiniz. Daha fazla bilgi için [Azure Active Directory'daki Parola ilkeleri ve hesap kısıtlamaları'ne](/azure/active-directory/authentication/concept-sspr-policy) göz atın.

## <a name="update-password-policy"></a>Parola İlkesini güncelleştirme

Set-MsolPasswordPolicy cmdlet'i, belirtilen etki alanı veya kiracının parola ilkesini güncelleştirir ve parolanın değiştirilmesi gerekmeden önce geçerli kaldığı süreyi gösterir.

Belirli bir etki alanı veya kiracı için parola ilkesinin nasıl güncelleştirildiğini öğrenmek için bkz [. Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>İlgili içerik

[Kullanıcıların kendi parolalarını sıfırlamasına izin ver](../add-users/let-users-reset-passwords.md) (makale)/

[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)
