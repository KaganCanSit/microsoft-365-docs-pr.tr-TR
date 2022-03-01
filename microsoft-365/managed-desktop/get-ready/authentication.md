---
title: Şirket içi kaynaklara erişimi Microsoft Yönetilen Masaüstü için hazırlama
description: Azure AD'nin kimlik doğrulama sağlamak için şirket içi AD ile iletişim kurasını sağlayacak önemli adımlar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 3db3d469f7b417035e6ae11507c54c6bad871a89
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027556"
---
# <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Şirket içi kaynaklara erişimi Microsoft Yönetilen Masaüstü için hazırlama

Microsoft Yönetilen Masaüstü'nden, cihazlar Azure Active Directory (Azure AD) sürümüne eklenir. Bu nedenle, şirket içi Active Directory kullanıyorsanız, Azure AD'ye katılmış cihazların şirket içi Active Directory'niz ile iletişim kurayalı olduğundan emin olun.

> [!NOTE]  
> *Karma* Azure AD'ye katılma, Microsoft Yönetilen Masaüstü tarafından desteklenmiyor.

Azure Active Directory, kullanıcılarının Tek Oturum'dan (SSO) Sign-On olanak sağlar. Çoklu Oturum açma, normalde kaynakları her kullanmaları için kimlik bilgileri sağlamak zorunda olmayacakları anlamına gelir.

Diğer e-Azure Active Directory için bkz. [Azure AD birleştirme uygulamanızı planlama](/azure/active-directory/devices/azureadjoin-plan). Azure AD'ye katılmış Sign-On Çoklu İş (SSO) hakkında arka plan bilgileri için bkz. SSO'dan şirket içi kaynaklara [yönelik Azure AD'ye katılan cihazlarda nasıl çalışır](/azure/active-directory/devices/azuread-join-sso#how-it-works).

Bu makalede, yerel Active Directory bağlantısına bağlı uygulamaların ve diğer kaynakların Microsoft Yönetilen Masaüstü ile sorunsuz şekilde çalışması için denetlemeniz gerekenler açıklanmıştır.

## <a name="single-sign-on-for-on-premises-resources"></a>Şirket Sign-On için tek veri kaynağı

UPN Sign-On parola kullanarak çoklu oturum (SSO) özelliği Microsoft Tarafından Yönetilen Masaüstü Cihazlarda varsayılan olarak etkinleştirilir. Ancak kullanıcılarınız bazı ek kurulum Windows Hello olan Windows Hello Kurumsal'i de kullanabilir.

### <a name="single-sign-on-by-using-upn-and-password"></a>UPN Sign-On parola kullanarak tek giriş

Çoğu kuruluşta, kullanıcılarınız Microsoft Tarafından Yönetilen Masaüstü Cihazlarında UPN ve parolayla kimlik doğrulaması yapmak için SSO'u kullanabilir. Bu işlevin çalışır durumda olduğundan emin olmak için, aşağıdaki şeyleri bir kez daha denetlemelisiniz:

- Azure AD aboneliğinin Bağlan onaylayın. Windows Server 2008 R2 veya sonraki bir Windows Şirket içi Active Directory sunucusu kullan olmalıdır.
- Azure AD Bağlan'nin desteklenen bir sürümü çalıştırarak çalıştır bu onaylayın. Bu üç özniteliği Azure AD ile eşitlerken ayar gerekir:
    - Şirket içi Active Directory'nin (kullanıcıların bulunduğu) DNS etki alanı adı.
    - Şirket içi Active Directory'niz (kullanıcıların bulunduğu yer) Net BU SÜRÜM.
    - Kullanıcının SAM hesap adı.

### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Sign-On İş'i kullanarak Windows Hello uygulama

Ayrıca Microsoft Yönetilen Masaüstü cihazları, İş için Microsoft iş işlerinizi kullanarak kullanıcılarınıza hızlı, Windows Hello deneyim sunar. Windows Hello Kurumsal'ın kullanıcılarınız ilgili UPN ve parolayı sağlamak zorunda kalmadan çalışması için, Şirket içi Single-Sign için [Azure AD'ye](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) bağlı cihazları yapılandırma Windows Hello Kurumsal'ı kullanarak gereksinimleri denetleme ve ardından orada sağlanan adımları izleyin.

## <a name="apps-and-resources-that-use-authentication"></a>Kimlik doğrulama kullanan uygulamalar ve kaynaklar

Uygulamaları uygulamalar [ve kaynaklar üzerinde çalışmak](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) için ayarlama konusunda yol gösterici tam yol bilgi için Azure içerik kümesinde uygulamalar ve kaynaklarla ilgili dikkate alınacak Azure Active Directory. Özet olarak:

| Uygulama veya hizmet | Görev |
| ------ | ------ |
| Bulut tabanlı uygulamalar | Azure AD **uygulama galerisine** eklenenler gibi bulut tabanlı uygulamaları kullanıyorsanız, çoğu için Microsoft Yönetilen Masaüstü ile çalışmak için başka hazırlık gerektirmez. Bununla birlikte, Web Hesabı Yöneticisi'ni (WAM) kullanmayan tüm Win32 uygulamaları yine de kullanıcılardan kimlik doğrulaması istendiğinde olabilir. |
| Şirket içinde barındırılan uygulamalar | Şirket içinde **barındırılan uygulamalar için, bu** uygulamaları tarayıcılar içinde güvenilen siteler listesine eklemeye emin olun. Bu adım, Windows kimlik bilgileri sorulmadan kullanıcı kimlik doğrulamasının sorunsuz çalışmasına olanak sağlar. Uygulama eklemek için, Yapılandırılabilir [ayarlar başvurusunda](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) [Güvenilen siteler'e bakın](../working-with-managed-desktop/config-setting-ref.md). |
| Active Directory Federasyon Hizmetleri | Active Directory Federasyon Hizmetleri kullanıyorsanız, AD FS ile çoklu oturum açma doğrulama ve yönetme'de yer alan adımları kullanarak SSO'nun [etkinleştirildiğinden emin olun](/previous-versions/azure/azure-services/jj151809(v=azure.100)). |
| Eski protokolleri kullanan şirket içi uygulamalar | Şirket **içi olan ve** eski protokolleri kullanan uygulamalarda, cihazların kimlik doğrulaması için şirket içi etki alanı denetleyicisine erişimi olduğu sürece ek kurulum gerekmez. Bununla birlikte, bu uygulamalara güvenli erişim sağlamak için Azure AD Uygulama Ara Sunucusu dağıtmanız gerekir. Daha fazla bilgi için bkz[. TT'nin Uygulama Ara Sunucusu Azure Active Directory şirket içi uygulamalara uzaktan erişim](/azure/active-directory/manage-apps/application-proxy). |
| Makine kimlik doğrulaması ile şirket içi uygulamalar | Şirket içinde **çalıştıran ve makine kimlik doğrulamasına** güvenen uygulamalar destek desteklemez; bu nedenle, bunları daha yeni sürümlerle değiştirebilirsiniz. |

### <a name="network-shares-that-use-authentication"></a>Kimlik doğrulama kullanan ağ paylaşımları

Cihazların bir UNC yolu kullanarak şirket içi etki alanı denetleyicisine erişimi olduğu sürece, kullanıcıların ağ paylaşımlarına erişimi için ek kurulum gerekmez.

### <a name="printers"></a>Yazıcılar

Karma Bulut Yazdırmayı yapılandırmadınız sürece, Microsoft Yönetilen Masaüstü cihazları şirket içi Active Directory'nize yayımlanmış [yazıcılara bağlanamıyor](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).

Yazıcılar yalnızca bulut ortamında otomatik olarak keşfedilelene kadar, aygıtlar şirket içi etki alanı denetleyicisine erişimi olduğu sürece, kullanıcılarınız yazıcı yolunu veya yazıcı kuyruğu yolunu kullanarak şirket içi yazıcıları kullanabilir.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. Verilere kullanıcı erişimini hazırlama (bu makale).
1. [Uygulamaları hazırlama](apps.md).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
